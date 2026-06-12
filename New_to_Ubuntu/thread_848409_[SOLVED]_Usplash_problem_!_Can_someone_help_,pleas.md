---
title: "[SOLVED] Usplash problem ! Can someone help ,please?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by bhadotia on 2008-07-03
I wanted to try out Debian as I've never been able to take a good look at it. But unfortunately this time also a problem occured - the boot-loader did install (neither grub nor lilo). So I gave up the idea , booted Ubuntu and formated the partition on which Debian was installed (I did not want to go through all the pain of installing grub manually by myself). But now I have a problem , since this incident the usplash screen is not working properly - it comes up when the system is booting and when the bar has moved a little further it goes away and boot messages start showing (this has happened with me earlier also - either when I did something like this or when some other problem occured like hibernating problem). 
Now after several times reinstalling usplash and usplashscreenubuntu  the problem has worsened . At first when the usplash screen that showed up for some time was without any problem . Now that screen is also distorted and ofcourse it stays only for a few seconds and then goes away to make room for the boot messages.
Can someone help me solve this.
Many thanks

---

### Post by philinux on 2008-07-03
startupmanager might solve it.

It's in synaptic. You can choose to have splash or text or both.

Other than that change themes then reboot then change back to you're preferred.
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Fix_the_shutdown_.22Network_Error.22_display_.28restore_shutdown_splash_screen.29)
Similar problem

---

### Post by bhadotia on 2008-07-03
Tried changing the system theme, login window, boot splash and rebooted thrice , but still no luck. The debian boot splash screen (the other boot splash theme) is not even showing up - at least ubuntu theme shows up distorted for some time. 
Any other suggestions?

---

### Post by philinux on 2008-07-03
Have you tried startupmanager

---

### Post by bhadotia on 2008-07-03
Yes , I already have it - Just didn't get the idea of changing the bootsplash . 
The option that enables text in startupmanager gives beautiful orange texts during the stat-up but my problem is I'm shown the console with boot messages instead of splash screen or that text.

---

### Post by bhadotia on 2008-07-05
Anyone , please help.
I tried disabling the usplash theme rebooted and then reenabled and rebooted.
But still its showing the boot messages instead of boot-splash .

---

### Post by bhadotia on 2008-07-17
I found the solution [here]("http://ubuntuforums.org/showthread.php?t=857565").
> **coffeecat said:**
> You get this problem if the UUID of the swap partition has been changed since you installed Ubuntu. Sometimes something goes wrong in the installation - this happened to me. It's possible this is your problem.

Anyway, have a look at these two threads:

[http://ubuntuforums.org/showthread.php?t=746132&page=2](http://ubuntuforums.org/showthread.php?t=746132&page=2)

[http://ubuntuforums.org/showthread.php?t=782700](http://ubuntuforums.org/showthread.php?t=782700)

and also:

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990)

What you have to do is:

1 - Run 'sudo blkid -c /dev/null' (no quotes) from a terminal. Include the -c /dev/null bit. If you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.

2 - Check that the UUID for the swap partition in /etc/initramfs-tools/conf.d/resume is the same as the UUID you got from blkid. Edit the file if necessary.

3 - Run 'sudo update-initramfs -u' from a terminal (again, no quotes).

4 - Reboot.

5 - Enjoy usplash.

---

