---
title: "Windows 8 dual boot questions/ bugs"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Eersfanpilot on 2013-04-07
I am experiencing two bugs.

1.  When in Ubuntu and close the screen ( sleep mode)  the computer does not wake.


2.  When in Ubuntu, I can not browse the Windows drive,  when I tried Ubuntu without installing I could. I keep getting an unable to mount error message that the drive is in hibernation.




 Advice?

---

### Post by dillonboardman on 2013-04-07
1. Click on the power button when you open it. It should brling you to the lock screen. Hopefully in a future version, users can just swipe the trackpad to wake it up.

2. I have the same problem. The only *solution* I have found was taking out the battery when you're booted into Windows. I don't encourage doing this as it could cause multiple other problems, but it does bypass the whole Windows 'shut down' process that causes it to go into hibernation. 

I hope that this helps you a bit.

---

### Post by oldfred on 2013-04-07
Windows 8 is always in hibernation. And the LInux NTFS driver will not mount hibernated file systems to prevent damage. Generally better to create a shared NTFS data partition and have any data you may want in both systems in that shared data partition.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Reboot/mount issues
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/1043149)

---

### Post by Eersfanpilot on 2013-04-07
> **dillonboardman said:**
> 1. Click on the power button when you open it. It should brling you to the lock screen. Hopefully in a future version, users can just swipe the trackpad to wake it up.

2. I have the same problem. The only *solution* I have found was taking out the battery when you're booted into Windows. I don't encourage doing this as it could cause multiple other problems, but it does bypass the whole Windows 'shut down' process that causes it to go into hibernation. 

I hope that this helps you a bit.

Thanks but the power button trick did not work for me when Ubuntu is in sleep mode.

---

### Post by slooksterpsv on 2013-04-07
When you boot Ubuntu, press e to edit the boot configuration and at the end of the line that looks similar to:

```

linux /boot/vmlinuz-3.8.0-12-generic root=#### ro quiet splash 

```

add NOACPI try that.

---

### Post by Eersfanpilot on 2013-04-09
> **dillonboardman said:**
> 1. Click on the power button when you open it. It should brling you to the lock screen. Hopefully in a future version, users can just swipe the trackpad to wake it up.

2. I have the same problem. The only *solution* I have found was taking out the battery when you're booted into Windows. I don't encourage doing this as it could cause multiple other problems, but it does bypass the whole Windows 'shut down' process that causes it to go into hibernation. 

I hope that this helps you a bit.

> **slooksterpsv said:**
> When you boot Ubuntu, press e to edit the boot configuration and at the end of the line that looks similar to:

```

linux /boot/vmlinuz-3.8.0-12-generic root=#### ro quiet splash 

```

add NOACPI try that.


I tried this but no luck. I have the same problem,  in sleep mode the computer's screen will not wake while in Ubuntu.  The lights come on on the keyboard but the screen will not come back. 

 On a side note regarding putting the code in,  once done it does not seem to stay. I put it in and booted,  then went to sleep to test and had to  hard reboot  due to  the screen not coming back.  Upon reboot I checked for the new code,  not there.  Line was back to normal.

---

### Post by oldfred on 2013-04-09
Editing the grub menu as you boot is a one time change. Usually you can find ways that resolve the issue, or you have to experiment with different settings. If you find the correct settings and have to make them permanent, you edit your grub file and update grub.

       gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

If multi-booting you should turn hibenation off in Windows 8.

---

### Post by Eersfanpilot on 2013-04-10
oldfred you came through again! After going into the windows settings I can now browse all the files on the computer in the Windows side of the HDD. 

Just to be clear, Are you saying by disabling fast boot in Windows it will help with the screen off issue coming out of sleep mode in Ubuntu or not? I'm still not clear on a lot of this GRUB2 stuff. I looked at that link you provided but I am a NOOB and some of that is like reading Greek to me still. 

I understand that putting the code in the way I was during the bootloader screen it was a one time code. However, how and where do I go to put it in permanently? I did notice that line of code had "ro" in it and (thinking in terms of my phone) sometimes I have to be in "rw" to write and make things take effect. Am I close in my thinking here? Were my changes only in read only? 


PROBLEM 2 SOLVED

---

### Post by oldfred on 2013-04-10
I do not really know about Windows hibernation. I never have used hibernation, but Windows now made it automatic to make it seem like it boots faster. See post #2 on details.

I posted above how to make permanent edits to grub menu's default settings which are in /etc/default/grub.

---

