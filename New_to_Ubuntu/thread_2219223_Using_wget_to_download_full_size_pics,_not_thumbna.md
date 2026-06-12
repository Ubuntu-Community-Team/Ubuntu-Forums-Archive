---
title: "Using wget to download full size pics, not thumbnails, from RSS feed"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Kamiya19 on 2014-04-23
Hi everyone,

I am trying to download all the pictures from a webpage, but  unfortunately my code only downloads the thumbnails. Anyone familiar  with wget, or how I can force it to follow links and automatically  download the full size images from their source?

The webpage is today.deviantart.com/dds

 	Code:

 	```
wget -nd -H -p -A jpg,jpeg,png,gif -e robots=off http://today.deviantart.com/dds
``` 
I know the -D command may come in use, as the -l1 (or higher  numbers) may be useful as well, but am not familiar enough to figure  this out for myself. 

Could someone lend a hand?

---

