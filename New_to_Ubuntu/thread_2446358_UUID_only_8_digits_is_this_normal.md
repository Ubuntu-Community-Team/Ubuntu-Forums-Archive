---
title: "UUID only 8 digits? is this normal?"
date: 2020-06-29
forum: New to Ubuntu
---

### Post by siggigretars on 2020-06-29
Hello all. I am very new to Linux and not very computer literate, so please be kind :)

I have been trying to change my Steam library folder to my 2TB hard disk, but having all kinds of troubles. 

First of all, when I try to find my drive UUID, it is only 8 digits. I kind of understand that it has something to do with being a FAT type, but other than that I have no idea. I see that another drive (sda1) is also type VFAT but has the correct number of UUID digits. 
I also see that in front of my 2TB disk (sdb) it says "LABEL_FATBOOT". 

So I ask, is it normal that my disk only has an 8 digit UUID and if not, how can I change it to an acceptable UUID? 

[IMG]https://imgur.com/4XU4auu[/IMG][https://imgur.com/4XU4auu](https://imgur.com/4XU4auu)

Thank you. 

P.s. tried to insert an image on here, uploaded it up to imgur.com and pasted the url into the add image url field but it doesn't show here, any idea why?

Siggi

---

### Post by Dennis N on 2020-06-29
First, be clear that in Linux sda1 is a partition, not a disk (or drive). 
In the line for sda1:
UUID= is an identifier for the file system on that partition. 
PARTUUID= is an identifier for the actual partition sda1.

The identifier for disk sdb is for the filesystem on the disk. Apparently, it has no partitions. 8 digits is normal for that kind of file system. It's recommended you should partition that disk and format partitions to be used before using it with Linux. Your files and folders should be on partitions.

As to the image, I think you can only display an image uploaded to the forum.

---

### Post by siggigretars on 2020-06-29
Oh, I see. That explains a lot. 

I will try to partition and format the disk, thank you for your help :)

---

### Post by coffeecat on 2020-06-29
> **siggigretars said:**
> 

P.s. tried to insert an image on here, uploaded it up to imgur.com and pasted the url into the add image url field but it doesn't show here, any idea why?

Siggi

Very odd. I've had a look at the raw text in your post and the image ought to show. Perhaps imgur is doing something to prevent it displaying. That being said, clicking on the hyperlink in your post reveals the image.

A couple of points so that the information you are posting in the image can be more easily accessed by those helping. First, if you want to show terminal output, please do not post images. Simply copy and paste the relevant terminal output into your post - this means that others can easily quote your output when offering help. You can copy highlighted text in the terminal with ctrl-shift-c rather than ctrl-c, or right-click -> copy, and then paste into your post in the normal way. If you do that please enclose output between BBCode [noparse]```
 and 
```[/noparse] tags for clarity and to preserve columnar formatting. Link in my sig for the use of BBCode code tags if you need it. 

Second thing. If you do need to include image(s), you can use the inbuilt forum image uploader - much better than using an off-site image hosting site. From the quick reply message editor, click on the "go advanced" button for a fuller-feature message editor, and then use the paperclip icon in the toolbar to upload your image(s) to the forum. That way you get clickable thumbnails.

Welcome to the forum!

---

### Post by ActionParsnip on 2020-06-29
If your output is in a terminal, you don't need a screenshot. Just copy and paste the text. Its much quicker and the text can be inline. A screenshot of text on a forum.......?

---

### Post by siggigretars on 2020-06-29
Very true, a bit of overthinking (and quite a bit of stupidity) on my part there. Guess I'm too used to screenshotting error messages in Windows. 

Of course it makes much more sense to just copy and paste *slaps forehead*

Thanks for the help.

---

### Post by siggigretars on 2020-06-29
Thank you, of course it makes much more sense to just copy and paste the text. Stupid of me. 

I will try out the other options you mention regarding inserting an image on here, if I need to now that I realized the very simple copy/paste option... 

Thank you :)

---

### Post by TheFu on 2020-06-29
FAT32 and NTFS partitions have shorter UUiDs than Linux file systems. For example, a FAT32 efi partition has a UUID=E7E6-D023  While an ext2 /boot/ partition has a UUID=d62de6a2-5b69-4d3a-8a41-91040d274d9e and ext4 UUID=fcdd553f-1edf-4c07-9cf8-541f9c7cce44

UUIDs aren't some super secret thing.  They are just trying to be unique on a machine or subnet.

Same for LAN ips - nothing super secret about those either.
if we look under /dev/disk/ there are lots of other symbolic links back to the file systems for mount use.

---

