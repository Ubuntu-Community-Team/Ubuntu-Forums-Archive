---
title: "Skype beta 2.0.0.68 + Creative Live Cam Vista = LFE"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by TeoBigusGeekus on 2008-05-14
At last, my long quest came to an and: I can officially declare that Creative Live Cam Vista works with the latest Skype coupled with the latest Ubuntu.
I just thought that sharing this information would be nice cause I've had my share of nagging at Ubuntu about this problem, I wouldn't wish others to share the same feelings about it.
Here goes:
Install build essential
```
sudo apt-get install build-essential
```
Then
```
cd ~
mkdir webcam-driver
svn co svn://rastageeks.org/svn/ov51x-jpeg/trunk webcam-driver
cd webcam-driver
sudo apt-get install linux-headers-`uname -r`
make
sudo make install
sudo gedit /etc/modprobe.d/ov51x-jpeg
```
Add this line to the empty file
```
options ov51x-jpeg forceblock=1 led=2
```
Finally
```
sudo modprobe ov51x-jpeg
```

Now open Skype and go to options, video devices and check the camera...
Voila!!!

:guitar:  :guitar:  :guitar:


P.S. Many of you will think "Hey, what's the big deal?", but those who know will rejoice!

---

### Post by kostkon on 2008-05-14
Nice how-to! I would like to point out two things:

1. You could put the [HOWTO] prefix in the beginning of the thread's title.

2. I think that Skype is not beta anymore!

---

### Post by TeoBigusGeekus on 2008-05-15
> **kostkon said:**
> 
1. You could put the [HOWTO] prefix in the beginning of the thread's title.


8-[ Ehhh, how do I do that? Sorry, it's my first thread ever...

---

### Post by Nattydread69 on 2008-09-27
I have the creative vista live webcam and I tried this  under Hardy 64 bit but it still doesn't work with skype. 
Although I can get a picture using Easycam 2.
Is there something I am doing wrong?

---

