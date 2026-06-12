---
title: "Ubuntu installation stuck on loading screen"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by getswad on 2012-11-24
Hi,

I'm trying to install Ubuntu 12.10 on my Dell Studio 15 laptop.

It has an Intel Core i5 M 430 @2.27GHz processor
4.00 GB Ram 
Windows 7 64 bit OS installed.

I downloaded Ubuntu and used Universal Installer 1.9.1.6 to create a boot-able USB and tried to install.

But I couldn't go past the loading screen with 'Ubuntu' and . . . . .

I tried booting with ubuntu-12.10-desktop-amd64 and ubuntu-12.10-desktop-i386, but both would get stuck at the same point.

I'm trying to dual install Ubuntu 12.10 on an empty partition(E:/ 75GB available) in the HDD with Windows 7(C:/).

Please help.

Thanks,
Swad

Edit: Posted here because I'm new to Ubuntu.
Plz move to correct section([http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)) if it should be there

---

### Post by oldfred on 2012-11-24
Welcome to the forums.

Have you tried booting into the liveCD mode or just installer? Is it the 4 MBR partition limit and Windows has used all 4 primary partitions?

If you cannot get a screen:
What video do you have? Often video is an issue on booting. 

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by getswad on 2012-11-24
Thanks for the reply.

I tried both Run 'Ubuntu from USB' and 'Install into Harddisk'. Both gave out the same problem.

I have 3 Partitions. Where c:/ has 200GB and D:/ has 200GB and E:/ has remaining (~75Gb).
I'm trying to install Ubuntu into E:/ which is empty.

For Display I have ATI Mobility Radeon HD 5470.
And its a Full HD Display.

Thanks,
Swad

---

### Post by 2F4U on 2012-11-24
You could play with grub kernel parameters and see if this helps to bring up the GUI. Many people with similar problems has success using the nomodeset grub kernel parameter:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by vuarnet on 2012-11-25
how long did you wait before you abandoned the startup? booting from a live cd can take a loooong time sometimes... (well into the minutes)

i would think that if you can get to the loading screen, you should be able to get to the OS with enough time... then you could start the install process from there.

it's likely not the graphics card -- i've heard they're not super compatible but they are still usuable to get into the OS. I installed 12.10 on my fiancee's younger brother's computer and he had nvidia graphics and it took me like 5 hours to get past black and white lines... if that gives you any reference point lol

and fwiw the amd64 live iso would be the appropriate pkg, not i386.

---

### Post by getswad on 2012-11-25
Thanks for the suggestion guyz. 

Finally I was able to run Ubuntu installation.

I did not make any changes, but it was installed.
Not sure what the issue is.

Thanks everyone.

---

