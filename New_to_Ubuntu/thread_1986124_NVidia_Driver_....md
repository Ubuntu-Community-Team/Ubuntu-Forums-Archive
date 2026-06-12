---
title: "NVidia Driver ..."
date: 2012-05-24
forum: New to Ubuntu
---

### Post by wbslinux on 2012-05-24
ASUS G73Jw Quad i7(86 x64); Win7; NVidia GTX 460M 

I have been waiting until I could get enough of my "stuff" done on Linux while maintaining a Windows machine.  When I get far enough, I'll go full Linux and use a VM to run Windows for the online games I play.

I installed the WUBI on my machine and had no problem integrating the Firefox and Thunderbird to match those on the Windows side.  I converted to those two programs a few years back in anticipation of this move.

Having programmed since 1969, I am familiar with command prompt activities from the "Terminal" mode, and just need a reference to look up the command syntax.

All went well with this test except the NVidia driver.  The standard VGA operated both my notebook's screen and the external screen I use when home. (Note: do not attempt any configuration in VGA without the "Mirror" option checked, or soon your buttons will be on one screen and your mouse on another ;-)  I installed the NVidia driver from the additional driver section.  The driver worked well with the notebook screen, but I could not get the external screen to be recognized.  The driver did not install a control panel and the display "Refresh" option would never show the external screen.  So I downloaded the latest Linux64 .run (driver shell) from NVidia and did everything in my power to get it to run.  I changed file attributes, and used the "su" and "su root" commands without any success.  I have the administrator rights and when I tried to make a "root" account, there was no option.  For some reason, I do not know the root password, and cannot get the "sh drivershellfilename" to run without getting the error that it must be run by the root.  I read and tried everything I could find about running a shell with root permissions and finally gave up.

If I could get this video problem fixed, I would be set to transition to linux.  I would also add it to my ASUS TF300T android tablet as well.  I had no WiFi issues with the TP-LINK WN822N v2 Wireless USB Adapter.  It is an Atheros driver. The internal wifi is a type of Atheros as well and I am not expecting any problems there.

When booting into the OS, There was a long delay getting my usb keyboard and mouse to work through the hub.  So login took a bit of waiting and testing connections while gnashing teeth.  I am pleasantly surprised at how far the Wubi has come since I last tried it out.

If anyone has an idea for me, I would love any advice.  I may have missed something, and I am sure that a proprietary driver/control panel may come sometime in the future from NVidia.  Never got to try out the 295.53 driver.

---

### Post by ikt on 2012-05-24
> **wbslinux said:**
> For some reason, I do not know the root password, and cannot get the "sh drivershellfilename" to run without getting the error that it must be run by the root.

"sudo ./drivershellfilename.sh" most likely.

root password should be your current users password.

---

### Post by wbslinux on 2012-05-24
My password didn't work for anything except the admin account I was using, which by the way was different than the screen name of my account.  It somehow adopted the Win7 account name, though I installed it with a different name ... hmm?  I'll reinstall it when I have a min and see what I get.

---

### Post by ikt on 2012-05-24
> **wbslinux said:**
> My password didn't work for anything except the admin account I was using, which by the way was different than the screen name of my account.  It somehow adopted the Win7 account name, though I installed it with a different name ... hmm?  I'll reinstall it when I have a min and see what I get.

I think those sound like WUBI specific problems, I still recommend the best option is to dual boot, if you have an SSD you can come out of Win7 and into Ubuntu in under a minute. :D

---

### Post by Kayo Veloso Trigo on 2012-05-24
> **wbslinux said:**
> ASUS G73Jw Quad i7(86 x64); Win7; NVidia GTX 460M .

i have the same notebook that you have, but i just started to use ubuntu on my mothers notebook, and i don't know nothing about linux, just somethings i searched on the web and I'm using her notebook to test the ubuntu, and I'm liking it. Did you have problems with drivers except for the graphics? the keyboard works well? is it hard to configure the G73JW?

i have searched on the forums and found this two links that may help you with the nvidia drivers.
[http://ubuntuforums.org/showthread.php?t=1771806](http://ubuntuforums.org/showthread.php?t=1771806)
[http://ubuntuforums.org/showthread.php?t=1768551&page=7](http://ubuntuforums.org/showthread.php?t=1768551&page=7)

---

### Post by Frogs Hair on 2012-05-24
When the Nvidia current driver was installed from additional drivers did you look in the Nvidia X server settings GUI ? It should look as below .

---

