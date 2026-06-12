---
title: "Logitech QuickCam Communicate STX"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by fossil112 on 2008-11-30
Hi.  I'm trying to install a webcam that I recently purchased.  I've read quite a few threads, but I'm getting a little confused.  
I've ran the following w/o errors

```

sudo apt-get install build-essential
```

and

```
sudo apt-get install linux-headers-386
```

What are my next steps?  (Ubuntu 8.10)

---

### Post by plucky on 2008-11-30
> What are my next steps? (Ubuntu 8.10) 


What guide are you using?


This [link](https://help.ubuntu.com/community/Webcam) might help

See this link for [Logitech webcams](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)


Your camera seems to have a [bug report and workaround for 8.10](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723)

Try installing webcam programs like camorama,cheese,skype,ekiga etc to test your webcam.

Good Luck
:)

---

### Post by forkandles on 2008-11-30
You can probably glean some useful information from the posts here.

[https://answers.launchpad.net/ubuntu/+source/gspca/+question/41434](https://answers.launchpad.net/ubuntu/+source/gspca/+question/41434)

---

### Post by fossil112 on 2008-11-30
Thanks guys, I'll dig into it today and keep you posted.

---

### Post by fossil112 on 2008-11-30
I installed Cheese 2.24.1 and I got good video, but no audio.  I followed [this guide]("https://answers.launchpad.net/ubuntu/+source/gspca/+question/41434") starting with marcobra's fist post about 1/3 of the say down the page.  I went got as far as
 ```
sudo tar -xjvf gspca-source.tar.bz2
```  
but received the following
```

vince@Vince:~$ sudo tar -xjvf gspca-source.tar.bz2
tar: gspca-source.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

So, Cheese was loaded fine, but I"m not sure how to fix this error.  Then, maybe I can follow the rest of the coding and get this bad boy working.

---

### Post by weose33 on 2008-11-30
According to Naif Sport, Cuthbertson gift "supervise GMG's intimate productive arrangement treat, working intimately with original visionaries Todd McFarlane and R.A. Salvatore to convey their unequaled and new modality to [maple story mesos](http://www.ugamegold.com/c_Maple-Story-Mesos/)   living" in his new personation. Gullible Mutant Games is now in pre-production on its perform denomination.

---

### Post by zachbb on 2008-11-30
From what I understand, it's because there is a conflict between the current driver and the driver needed by some aplications:

Look at this link on how to preload the driver. Preload it first with proycons instructions and then make it permenant:
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723)

Zach

---

### Post by zachbb on 2008-11-30
sorry double posted

---

### Post by spiderbatdad on 2008-11-30
> **fossil112 said:**
> I installed Cheese 2.24.1 and I got good video, but no audio.  I followed [this guide]("https://answers.launchpad.net/ubuntu/+source/gspca/+question/41434") starting with marcobra's fist post about 1/3 of the say down the page.  I went got as far as
 ```
sudo tar -xjvf gspca-source.tar.bz2
```  
but received the following
```

vince@Vince:~$ sudo tar -xjvf gspca-source.tar.bz2
tar: gspca-source.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

So, Cheese was loaded fine, but I"m not sure how to fix this error.  Then, maybe I can follow the rest of the coding and get this bad boy working.

The issue here is most likely, the package is on your desktop, but when you open a terminal, your pwd (present working directory) is /home/user_name. If you enter the command ```
cd Desktop
```with a capital D, you can now work with files in that directory. There is also a patch that has to be applied to that driver before you compile it. Have you seen this article? [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)

Get the patch in this thread [http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500](http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500)

And find the link with instructions for applying it to the package...now..I did all this and got my logitech and gigaware cams working (still had to use LD_PRELOAD with some apps) but after the latest kernel upgrade (2.6.27-9-generic) I no longer needed the gspca driver. Indeed it isnt included with the kernel. The uvcvideo driver worked fine, though still using LD_PRELOAD in some cases.
So ```
uname -r
```to see if you are running 2.6.27-9...if not I suggest sudo apt-get update && sudo apt-get upgrade.  When you are asked what to do about menu list, use the drop down arrow and select "Use the package maintainer's version."


If your cam works fine with LD_PRELOAD, i would recommend LD_PRELOAD=.....4vl2convert.so skype instead of v4l1compat.so, as v4l2 works better in skype.

---

### Post by fossil112 on 2008-12-01
thanks for your thorough explanation, spider...i'll dig into it once i get home (at work now).  very much appreciated

---

### Post by markbuntu on 2008-12-01
I have that same cam, it worked out of the box for me in Intrepid. In hardy all I had to do was use v4l instead of v4l2. I figured that out with Ekiga.

---

