---
title: "Two noob questions regarding Ubuntu 14.04"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by mikeyinid on 2014-05-27
Two things. First, is there a GUI app for changing folder paths/location. Been Googling for days and havent found anything. Second, my machine runs a 3rd gen i5, 8gb ballistix ram, and ssd and hdd. I have my / and /home taking up the entire ssd as I am compiling AOSP. I have 20gb swap on the hdd but everytime I check, none is being used. Is swap necessary with my setup?

---

### Post by Bucky Ball on 2014-05-27
A 20Gb swap isn't. You only need around 2Gb unless you do a lot of hibernation (and if you do you would go for 8Gb to match the amount of installed RAM). 

Not sure about your first question. Changing what folder paths/location? Do you mean when you open your file manager you want it to open to a specific folder?

---

### Post by papibe on 2014-05-28
Hi mikeyinid.

> **mikeyinid said:**
> is there a GUI app for changing folder paths/location.
Could you explain a little more? May be an example?
> **mikeyinid said:**
> Is swap necessary with my setup?
It all depends on how much RAM you use. In other words, how many apps you have open at a time. For most cases, 8Gb of RAM would allow you disable swap without much problems.

Regards.

---

### Post by mikeyinid on 2014-05-28
> **Bucky Ball said:**
> A 20Gb swap isn't. You only need around 2Gb unless you do a lot of hibernation (and if you do you would go for 8Gb to match the amount of installed RAM). 

Not sure about your first question. Changing what folder paths/location? Do you mean when you open your file manager you want it to open to a specific folder?

> **papibe said:**
> Hi mikeyinid.


Could you explain a little more? May be an example?

It all depends on how much RAM you use. In other words, how many apps you have open at a time. For most cases, 8Gb of RAM would allow you disable swap without much problems.

Regards.
See the attachment. Its an xposed module for Android but is exactly what I am talking about. You change the path of a folder then it gives you the option to move the contents of the old folder to the new folder or delete them. i would like something similar in Ubuntu.
[ATTACH=CONFIG]253522[/ATTACH]

---

### Post by nerdtron on 2014-05-28
You soon learn the hard way when you change the default target paths of you default folder paths. Is there a good reason why you want this? I think may be because of the small space on you ssd?
You can try creating symbolic links, more like shortcuts in windows, that points a folder to a different location on another drive.

---

### Post by mikeyinid on 2014-05-28
> **nerdtron said:**
> You soon learn the hard way when you change the default target paths of you default folder paths. Is there a good reason why you want this? I think may be because of the small space on you ssd?
You can try creating symbolic links, more like shortcuts in windows, that points a folder to a different location on another drive.

I figured out how to move the directories in places in Nautilus. I guess the only other thing I want to move to the HDD is Trash. I tried the symlink thing but I just get the items in both places taking up twice the space. I'm sure I did it wrong but I'd like to just be able to move it like I did downloads.

I moved /tmp to RAM to help speed up my builds. Is there a legit reason NOT to do that? Everything seems OK except right after a build finishes and all the RAM is used. A reboot fixes it so not a huge deal.

---

### Post by lukeiamyourfather on 2014-05-28
> **mikeyinid said:**
> 
I moved /tmp to RAM to help speed up my builds. Is there a legit reason NOT to do that? Everything seems OK except right after a build finishes and all the RAM is used. A reboot fixes it so not a huge deal.

Some applications will store a significant amount of data in /tmp for things like thumbnails, proxy videos, auto saves, and all that stuff can add up to quite a lot. I wouldn't leave /tmp as a RAM disk for day to day usage, but it makes sense to configure it that way for specific tasks like compiling AOSP. There might be a way to define a temporary directory for building AOSP that isn't /tmp which could be a safer option.

---

### Post by mikeyinid on 2014-05-28
> **lukeiamyourfather said:**
> Some applications will store a significant amount of data in /tmp for things like thumbnails, proxy videos, auto saves, and all that stuff can add up to quite a lot. I wouldn't leave /tmp as a RAM disk for day to day usage, but it makes sense to configure it that way for specific tasks like compiling AOSP. There might be a way to define a temporary directory for building AOSP that isn't /tmp which could be a safer option.

I literally only build AOSP and web browse on this machine. I dont do any media or photo stuff on it. I have a MBA for that stuff. Since moving /tmp to RAM I periodically check RAM usage, and unless I'm building usage is never more than 25%. I will look at alternatives because what you said does make sense. But moving /tmp almost cut my build times in half so I'm hesitant to change it haha.

---

