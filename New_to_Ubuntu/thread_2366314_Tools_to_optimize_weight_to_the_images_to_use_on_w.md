---
title: "Tools to optimize weight to the images to use on website"
date: 2017-07-16
forum: New to Ubuntu
---

### Post by sed_faster on 2017-07-16
Hello folks,

I intend find a tools to use to optimize images to use on website. I finded this article: [https://www.tecmint.com/optimize-and-compress-jpeg-or-png-batch-images-linux-commandline/](https://www.tecmint.com/optimize-and-compress-jpeg-or-png-batch-images-linux-commandline/)
Which tools do you recommend use to do this job?

Thanks

---

### Post by TheFu on 2017-07-16
$ more ~/bin/img-opt.sh 
```
#!/bin/bash
QUAL=40

for img in "$@"; do
  NEW=${img/%.???/-opt.jpg}
  echo " Working on $img ..."
   convert -quality $QUAL  "$img"  "$NEW"

done

echo "rename 's/-opt.jpg/.jpg/g' "

```
is exactly how I do it.
* file names cannot have funny characters **or spaces**.  spaces in file or directory names definitely break this script.
* pass in the name of the files or a glob you want handled.  **img-opt.sh *jpg** is fine.
* A quality of 40 is a high compromise. Most images will compress more with few visual artifacts even at 20.
* convert is part of the imagemagick suite of tools. Install that package.

I like that this can be applied automatically from our version control as the images are deployed to different web sites.  Automate processing is key.

---

### Post by leunam12 on 2017-07-18
I use xnview

---

