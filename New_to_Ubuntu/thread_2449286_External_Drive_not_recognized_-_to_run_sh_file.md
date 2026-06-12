---
title: "External Drive not recognized - to run sh file"
date: 2020-08-24
forum: New to Ubuntu
---

### Post by eopi on 2020-08-24
Hi, 

I need some help. 

I have a file, sh file that converts .HEIC files (pic files) to .jpg files.  But my external drive is not found.  (**Edit**: My SH file is placed in the External Drives folder awaiting execution ability or command.) I used Ctrl L in the Directory to get the direct link to the folder and I confirmed using df -h that my external is there.

In the Terminal the following is what I'm pasting for the purpose of executing. 

/media/zoaa/Seagate Backup Plus Drive/Family_Pictures/E IPhone yr 2017 thru 2020/100APPLE/rnpic.sh

The Error is the following:

bash: /media/zoaa/Seagate: No such file or directory

Any help will be appreciated.
Thanks,

---

### Post by deadflowr on 2020-08-24
Try encapsulating it in quotes like
```
"/media/zoaa/Seagate Backup Plus Drive/Family_Pictures/E IPhone yr 2017 thru 2020/100APPLE/rnpic.sh"
```
Otherwise it stops at the first break.

---

### Post by eopi on 2020-08-24
> **deadflowr said:**
> Try encapsulating it in quotes like
```
"/media/zoaa/Seagate Backup Plus Drive/Family_Pictures/E IPhone yr 2017 thru 2020/100APPLE/rnpic.sh"
```
Otherwise it stops at the first break.

This seems to get it going although a strange thing happened. 

When I ran my test trial on . or Home with 6 or 7 pictures being converted, I see that it converted those pictures.  But now Terminal is simply repeating that code:

Working on file IMG_8118.HEIC
File contains 1 images
Written to IMG_8118.HEIC.jpg
Working on file IMG_8119.HEIC
File contains 1 images
Written to IMG_8119.HEIC.jpg
Working on file IMG_8120.HEIC
File contains 1 images
Written to IMG_8120.HEIC.jpg
Working on file IMG_8121.HEIC
File contains 1 images
Written to IMG_8121.HEIC.jpg
Working on file IMG_8804.HEIC

Instead, it should be saying "Converting 6,000 pictures from the other location". So to speak ...

I created a new SH File with a new name, placed the new SH file in the distant folder. I moved away from . or Home. 

My SH file has the following commands:

#!/bin/bash
for f in *.HEIC
do
echo "Working on file $f"
heif-convert $f $f.jpg
done

Any ideas on how I can get it to break its dedication to the original Test Run? 
Should I reboot?

Thanks,

---

### Post by Impavidus on 2020-08-24
You use shell globbing (the *.HEIC in the script) to select the files. This means it will act on all non-hidden files in the current directory with a name ending in .HEIC. It doesn't matter where the script is located, it matters what your current working directory is when you call the script. So try changing directory first.

---

### Post by ActionParsnip on 2020-08-25
You aren't accommodating the spaces in the file names. They need escaping. You will also need to do similar in your script.

---

