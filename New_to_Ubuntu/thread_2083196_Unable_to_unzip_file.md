---
title: "Unable to unzip file"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by hansnn on 2012-11-11
I am trying to download this file, I'm not sure what format it is or anything, all I know is that it's a DVD.

And it's zipped.

When I try to unzip it, i get this error:



[I]
Archive:  /home/martinux/Downloads/SMFE-Community (1).zip.crdownload
[/home/martinux/Downloads/SMFE-Community (1).zip.crdownload]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/martinux/Downloads/SMFE-Community (1).zip.crdownload or
          /home/martinux/Downloads/SMFE-Community (1).zip.crdownload.zip, and cannot find /home/martinux/Downloads/SMFE-Community (1).zip.crdownload.ZIP, period.
[/I]


The file requires zip V1.0 and i have V3.0

I looked around but found no answers, so I'm thinking it got something to do with the fact that it's a DVD?
Maybe it's a windows file?

I found no answers online so i ask here before i try downloading semi-related software until i maybe find something that solve it.

Thank you

---

### Post by NikTh on 2012-11-11
Hi,
What Ubuntu version you have ? 
Have you tried right click and "extract here" ? 
Have installed the p7full-zip package ? 
```
sudo apt-get install p7zip-full
``` 

Thanks

---

### Post by mgngapyin on 2012-11-11
I think the download is not complete or may be corrupted for some reasons.

.crdownload is added to to the folder when you're dowloading something with Chrome/Chromium browser. 

Try completing the download & unzip again.

---

### Post by NikTh on 2012-11-11
> **mgngapyin said:**
> 
.crdownload is added to to the folder when you're dowloading something with Chrome/Chromium browser. 

Try completing the download & unzip again.

This is correct ! 

I didn't notice . 

Thanks

---

### Post by hansnn on 2012-11-12
Problem solved!

I use chromium but there is no .crdownload

To solve it i simply right clicked and pressed 'extract here'.

Thank you very much!

---

