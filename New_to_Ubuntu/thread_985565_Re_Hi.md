---
title: "Re: Hi"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by manjunaathsiegen on 2008-11-17
Hi,
Recently I installed Ubuntu 8.10 in my laptop.  But inbuilt mic and web-camera are not supporting.  Mine is Sony viao VGN-FFZ18M series laptop.
What I suppose to do to work my web camera and mic. Please help me in this.
Thanking You,

---

### Post by halitech on 2008-11-17
if they truely aren;t supported at this time the only way to get them to work will be to write code to make them work. If you mean not working (as opposed to not supported) then we'll see what we can do to get them working.
Can you open a terminal and post the results of```
sudo lsusb
```

---

### Post by manjunaathsiegen on 2008-11-17
Hi, here is 
manjunath@manjunath-laptop:~$sudo lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ca:1837 Ricoh Co., Ltd
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And one more thing is I am new to Ubuntu and if I tried to copy the code from terminal usual copy method is not working.  How to do exactly.
Thaning you,

---

### Post by karlr42 on 2008-11-17
You have to use ctrl-shift-c to copy text from the terminal.

---

### Post by echo314 on 2008-11-17
You must highlight the text with your mouse, right click and select copy. The normal key shortcuts you are familiar with may not work. Once you get into Fx, you may hit control-V, or right click and Paste.

**EDIT: Learning something new everyday here!

---

### Post by halitech on 2008-11-17
for the terminal, the same commands will work but you need to press shift as well (ctrl-shift-c = copy, ctrl-shift-v = paste)

---

### Post by halitech on 2008-11-17
> **manjunaathsiegen said:**
> Hi, here is 
manjunath@manjunath-laptop:~$sudo lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ca:1837 Ricoh Co., Ltd
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

And one more thing is I am new to Ubuntu and if I tried to copy the code from terminal usual copy method is not working.  How to do exactly.
Thaning you,

with it not seeing the device as a webcam I don't think you can get it to work however this thread (post 86) says they got it working
[http://ubuntuforums.org/showthread.php?t=289836&page=9](http://ubuntuforums.org/showthread.php?t=289836&page=9)

---

### Post by manjunaathsiegen on 2008-11-17
Hi here is the output:
```
manjunath@manjunath-laptop:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ca:1837 Ricoh Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Please check how I can solve my web camera and mic to function.

And thanks for your help in copying from terminal. It worked very well.
Thanking you,


> **halitech said:**
> if they truely aren;t supported at this time the only way to get them to work will be to write code to make them work. If you mean not working (as opposed to not supported) then we'll see what we can do to get them working.
Can you open a terminal and post the results of```
sudo lsusb
```

---

### Post by manjunaathsiegen on 2008-11-17
Hi,
I tried accordingly as page 86 but nothing came out. I am getting below error !!

```
manjunath@manjunath-laptop:~$ sudo dpkg -i ~/Desktop/ricoh-webcam-r5u870-2.6.20-16-generic_0.10.0-2_i386.deb
dpkg: error processing /home/manjunath/Desktop/ricoh-webcam-r5u870-2.6.20-16-generic_0.10.0-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/manjunath/Desktop/ricoh-webcam-r5u870-2.6.20-16-generic_0.10.0-2_i386.deb

```


> **halitech said:**
> with it not seeing the device as a webcam I don't think you can get it to work however this thread (post 86) says they got it working
[http://ubuntuforums.org/showthread.php?t=289836&page=9](http://ubuntuforums.org/showthread.php?t=289836&page=9)

---

### Post by halitech on 2008-11-18
did you download the file and then change directory (cd Desktop) to where you saved the file to?

---

### Post by manjunaathsiegen on 2008-11-18
Hi,
Yes I did.  But still it is not working.

> **halitech said:**
> did you download the file and then change directory (cd Desktop) to where you saved the file to?

---

### Post by jpoRS on 2008-11-18
Is this a built in webcam or a USB one?  In my experience with built in cameras support is VERY patchy, and you may be out of luck for the time being.

Welcome to the community
jim

---

### Post by manjunaathsiegen on 2008-11-18
Hi,
Yes it is built in web camera.
So, how can I solve my problem.
Thanking you.

> **jpoRS said:**
> Is this a built in webcam or a USB one?  In my experience with built in cameras support is VERY patchy, and you may be out of luck for the time being.

Welcome to the community
jim

---

### Post by manjunaathsiegen on 2008-11-18
Hi all,
If any one know how to activate inbuilt blue tooth, web camera and mic in sony vaio note book under ubuntu 8.10 operating system. please help me.

---

### Post by jpoRS on 2008-11-18
If you have the programming experience, you should be able to program your way around this, with a little bit of work.  If this isn't an option, do you have access to a USB webcam?  Several of them are supported, and that may solve your problem until someone else gets your camera supported.

Sorry I can't be more help.
jim

---

