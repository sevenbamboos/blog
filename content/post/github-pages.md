+++
author = "YuPing Wang"
date = "2016-06-01T16:05:27+08:00"
description = "publish static web pages on Github"
draft = false
tags = ["git-hub", "writing"]
title = "How to build personal blog via Github Pages"
type = "post"

+++

# Config Hugo
[Hugo](https://gohugo.io/) 
The configuration is straightforward and it lets you focus on the contents instead of web pages' style. It's worth noting to include the following in config.toml:
```
baseurl = "http://xxx.github.io/yyy"
publishdir = "public"
canonifyurls = true // ensure css can be loaded
```

# Choose a theme
Without a theme, hugo won't show anything but a blank page, which is definitely not welcome for novice. You can get a basic idea about what available themes look like from [**here**](http://themes.gohugo.io/). Then choose one from the [**list**](https://github.com/spf13/hugoThemes) and execute the following commands:
```
mkdir themes
cd themes
git clone git@github.com:mmrath/hugo-bootstrap.git // change the theme name if necessary
```
And don't forget to add the theme name to config file to save some time of typing later on:
```
theme = "hugo-bootstrap"
```
[**TODO**] add more information for theme customization

# Local testing
The next step is to add contents by:
```
hugo new post/new-blog-item.md
hugo server -wD // including draft during the content generating
```
Once satisfied with the result, you can mark the file as non-draft and generate the content by:
```
hugo // it's such a compact command without any unnecessary parameter
```

# Push to Github Pages 
Now the final step is to publish it to Github, which requires us to put the pages in a repository's "gh-pages" branch. A very easy way for git novice is to create a separate repository specific for the generated web pages (of course, we have to create gh-pages branch as well). I suggest to use the follow strategy:
```
cd hugo_content_folder/public
git init
git add .
git ci -m "comments xxx"
git remote add origin git@github.com:xxx/yyy.git
git push origin master
git co --orphan gh-pages
git add .
git ci -m "comments yyy"
git push origin gh-pages
``` 
[**XXX**] How to simplify the preceding commands? When following the Hugo's official document withe "git subtree" stuff, there is non-fast-forward error in my console!

