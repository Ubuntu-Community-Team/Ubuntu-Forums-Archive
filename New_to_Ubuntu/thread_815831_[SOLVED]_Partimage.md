---
title: "[SOLVED] Partimage"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-02
I want to restore my ubuntu and windows instalation in many computers or in other words i want to install windows and ubuntu in a set of computers [ around 10 computers in my hostel ] of my friends.

Is there any way to do this in a short time by using partimage like GHOST in windows.

---

### Post by HotShotDJ on 2008-06-02
> **rraj.be said:**
> I want to restore my ubuntu and windows instalation in many computers I respectfully suggest that you NOT attempt to manage 10 dual-boot systems until you become more familiar with Ubuntu.  Also, keep in mind that you may run into licensing issues if you try to install copies of Windows on 10 computers.  This is not, however, a problem for your Ubuntu partition.

---

### Post by logos34 on 2008-06-02
NTFS support in Partimage is still 'experimental', so you'd have to use something else like maybe CLonezilla.  Partimage would work for linux.

What about a customized installation CD/DVD of ubuntu? Installation on each machine only takes slightly longer than restoring an image. 
[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by rraj.be on 2008-06-02
I am staying in a hostel and i told about the features and advantages of ubuntu to them.

They all want to install ubuntu in their computer as a dual boot.

This is my main issue.

I am tiered of installing ubutu and then updating every thing and then providing them with required packages.

there is no need for e to  copy my windows too.

i am just asking that is it possible to copy my entire partition to my friends system using partimage.

---

### Post by HotShotDJ on 2008-06-02
> **rraj.be said:**
> i am just asking that is it possible to copy my entire partition to my friends system using partimage.Yes, it is possible.  However, I recommend that you follow logos34's advise instead.  And while you probably CAN use partimage copy your Windows partition (although I have no first hand knowledge of how to do it), the unauthorized copying of Windows is illegal, even in India.  My understanding of the rules of this forum is that we are not allowed to assist other members to break the law.

---

### Post by rraj.be on 2008-06-02
I tried remastersys and reconstructor too.

I created the custum live dvd 5 times and each time when i boot with that its taking me to 

```
initramfs

BUSY BOX SHELL
```

I dont know what went wrong.

I searched for help and trien in ubuntu forums too but no use.

could you help me in this.

---

### Post by rraj.be on 2008-06-02
I am too not intrested in breaking law or even with WINDOWS.

I am still having it in my system because i use to work some security stuffs in windows hacking and Tweeking.

further i use it because i dont know how to program java and C,C++ in ubuntu.

can you help me in this too.

---

### Post by logos34 on 2008-06-02
look through this thread:
[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

---

### Post by HotShotDJ on 2008-06-02
> **rraj.be said:**
> further i use it because i dont know how to program java and C,C++ in ubuntu.

can you help me in this too.I don't know how to program java, C, or C++ in either Ubuntu or Windows... I'm pretty sure that teaching those skills is well outside the scope of this forum. :)

---

### Post by rraj.be on 2008-06-02
Hey i am not asking to teach me programing.

I dont know what IDE to use for it.

I use NET BEANS in windows.

I use anjuta For my c c++ in ubuntu but not much familar.

K. what abt using remastersys and getting into initramfs BUSY BOX SHELL

---

### Post by rraj.be on 2008-06-02
> **logos34 said:**
> look through this thread:
[http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)



There is a lot of posts and all are about installing usind live cd and not with custom live cd.

Could you help me in some what in detail, please logos.

---

### Post by rraj.be on 2008-06-02
Is there any one please .

---

### Post by cjv8888 on 2008-07-18
Yes, you can image Windows and linux using Partimage.
I just succeeded in restoring WinXP on NTFS file system using an image made with Partimage completely error free.
To put the image of either Ubuntu or XP on another computer, easiest way would be to use a live CD.
I used the Knoppix CD which already contains Partimage. Then transfer the image from a USB HD,

---

