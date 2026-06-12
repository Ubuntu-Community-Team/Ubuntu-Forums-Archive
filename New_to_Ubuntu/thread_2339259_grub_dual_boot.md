---
title: "grub dual boot"
date: 2016-10-06
forum: New to Ubuntu
---

### Post by grazen on 2016-10-06
Hello, 

I'm using grub to switch between windows 10 and ubuntu.
I haven't used ubuntu in months but suddenly the windows option didn't work in the grub menu.
And it got automatically removed afterwards, I've had this before so I started in ubuntu and tried to update grub2 with sudo apt-get update grub2.
Which seemed to be working fine, after that I used boot repair. But nothing worked so far and I really don't know what to do now.

This is the pastebin [http://paste.ubuntu.com/23285018/](http://paste.ubuntu.com/23285018/)

---

### Post by mook765 on 2016-10-06
The command to update grub is not  *sudo apt-get update grub2* it is
```
sudo update-grub
```
The boot-info-summary looks ok, but there is a problem within Windows, Grub cant even find Windows.
You will have to check with Windows-recovery-CD what is going on.

---

### Post by grazen on 2016-10-06
Yes I've tried that too, I got a recovery usb and tried some of the troubleshooting but it didn't seem like I could do much..

Does anyone else have any suggestions? I can't imagine that windows would just dissapear overnight? I really have no clue how I can fix this, or get my data back..

I have no clue what I did but I fixed it...

---

### Post by oldfred on 2016-10-06
Grub only boots working Windows.
Or Windows that is not hibernated nor needs chkdsk.
Windows NTFS needs chkdsk after any resize.
And Windows 8 or later is always hibernated with its fast start setting. And updates in Window may turn that back on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

You also are showing 3.19 kernel which as part of 14.04 is the enablement stack to allow newer systems to use newer kernel. But then you have to continue to update kernels.
       
 [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr) 
    
You may need to copy & paste the update command.

---

