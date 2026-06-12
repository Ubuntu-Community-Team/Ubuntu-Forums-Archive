---
title: "Rescue files from Windows"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Zetetes on 2012-05-17
I have an older asus p4s8x with a p4 on which windows xp has become completely dysfunctional.  I have set up ubuntu as the only way to access the computer/hard drive.  So far, so good, but ubuntu has too little space to work with.  Can I directly delete the windows system folders and files and the old programs on that ntfs partition from inside unbuntu?  Windows can go, but I have lots of photos and documents on that partition that I don't want to lose or overwrite.   My goal is to free up lots of space that I can hopefully later sequester to ubuntu somehow (I'll be back to ask bout that later).

Has anyone ever gone through this primitive an operation before?  Again, windows is dead, unresponsive entirely.

---

### Post by josephmills on 2012-05-17
> **Zetetes said:**
> I have an older asus p4s8x with a p4 on which windows xp has become completely dysfunctional.  I have set up ubuntu as the only way to access the computer/hard drive.  So far, so good, but ubuntu has too little space to work with.  Can I directly delete the windows system folders and files and the old programs on that ntfs partition from inside unbuntu?  Windows can go, but I have lots of photos and documents on that partition that I don't want to lose or overwrite.   My goal is to free up lots of space that I can hopefully later sequester to ubuntu somehow (I'll be back to ask bout that later).

Has anyone ever gone through this primitive an operation before?  Again, windows is dead, unresponsive entirely.

I made a youtube video and am uploading it will post link when uploaded 

:)

---

### Post by Zetetes on 2012-05-17
> **josephmills said:**
> I made a youtube video and am uploading it will post link when uploaded 

:)
Looking forward to that. Thanks.

---

### Post by josephmills on 2012-05-17
Sorry about the poor sound sync
[http://www.youtube.com/watch?v=Ab4zEP8aIY0](http://www.youtube.com/watch?v=Ab4zEP8aIY0)
but here it is and I need too do myself :) 
Make sure you back UP 
and thanks again for choosing Ubuntu 

:)

---

### Post by Zetetes on 2012-05-17
> **josephmills said:**
> Sorry about the poor sound sync
[http://www.youtube.com/watch?v=Ab4zEP8aIY0](http://www.youtube.com/watch?v=Ab4zEP8aIY0)
but here it is and I need too do myself :) 
Make sure you back UP 
and thanks again for choosing Ubuntu 

:)
OK. Watched it. You seem to have answered my question(s) and I thank you. I appreciate your having taken the trouble to illustrate the procedure for me. Today is my first ever contact with linux\unbuntu, so I'm going to have to listen and watch it again a few times. Ubuntu looks very well done, but I still don't know a thing about it and I need to get familiar.

---

### Post by black veils on 2012-05-18
3 steps need to be done.

**1.  retrieve your personal files from Windows**

a.  boot into the Ubuntu live cd, choose the 'try' option, not 'install', so it will load the desktop environment.

b.  open the file manager and click the Windows partition from the left pane.

c.  find your personal files on Windows, and copy-paste them to a usb flash drive, that should work, (best to check these things).


**2.  remove Windows**

from the Ubuntu live cd desktop environment, open the application [COLOR=YellowGreen]*[COLOR=Black]gparted. [/COLOR]*[COLOR=Black]this is a partition manager, you will be able to delete Windows here.


**3.  sort bootloader (grub) after deleting Windows**
[/COLOR][/COLOR]
this part i am not sure on how to do. essentially you probably need to run  ```
sudo update-grub
```  but i dont think it works from the live desktop environment, as i have not been successful myself the one time i tried it. if it is *not* done, then your system will probably be *unbootable*. it is not a big issue though, a simple matter of a file needing to be updated about the operating systems on your computer. grub may even need reinstalling instead of merely updating.

someone else needs to help with step 3

---

### Post by black veils on 2012-05-19
my previous post and "step 3", you could do this:

1.  boot into your Ubuntu live cd/usb, choose to load the desktop environment.

2.  open the terminal and copy-paste the following commands individually (press the Enter key after each and wait).

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```
```
sudo apt-get update
```
```
sudo apt-get install boot-repair
```

3.  find and launch the app "boot-repair", then choose "recommended repair"

---

### Post by mörgæs on 2012-05-19
> **Zetetes said:**
> OK. Watched it. You seem to have answered my question(s) and I thank you. I appreciate your having taken the trouble to illustrate the procedure for me. Today is my first ever contact with linux\unbuntu, so I'm going to have to listen and watch it again a few times. Ubuntu looks very well done, but I still don't know a thing about it and I need to get familiar.

Good, then please mark the thread 'solved'.
Welcome to the fora.

---

