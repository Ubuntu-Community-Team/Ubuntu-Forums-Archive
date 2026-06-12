---
title: "So confused about Ubuntu/Windows 8 Dual Boot Partitions"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by cyan on 2012-12-27
Hi, everyone. I am *that* guy. I know just enough about Linux to get myself in trouble and then I run screaming for the hills when I do.

So here's my problem.

I have a PC on which I installed Windows 7 and Ubuntu. Recently I upgraded the Windows install to Windows 8 and Ubuntu to 12.10.

Windows kept saying there were problems and kept doing a bunch of blue screens saying it was resetting my machine and "refreshing" the install. 

Um. . .okay.

When all was said and done, I couldn't get into my Ubuntu install. Eventually, I decided to do a clean Ubuntu install and that seems to have worked. I can now access both my Windows 8 install and my Ubuntu 12.10 install. All is good.

However. . .

I now have a triple boot system (sort of). One install is Windows 8 and another is the first (borked) Ubuntu install. Both of these are handled by the Windows boot screen. If I try to access that Ubuntu install I can't. But Windows 8? No problem.

Then I have a SECOND Ubuntu install. The Grub screen that shows *that* install comes up first and allows me to select Ubuntu or Windows 8 (clicking on Windows 8 takes me to the Windows boot screen which offers Windows 8 or the original Ubuntu install).

Am I making any sense yet?

So basically I have the different partitions you see in the attached photo. I want to get rid of the first Ubuntu install and give that disk space to the working Ubuntu install.

How can I do that without going back to the problem I had with the original dual boot set up (where Ubuntu wouldn't load)?

Any guidance is appreciated. Thank you.

---

### Post by eternalnewbee on 2012-12-27
Delete all Ubuntu  partitions and reinstall again.

---

### Post by audiomick on 2012-12-27
No, that is a bit radical.

In your screenshot, there is only one partition that can be an Ubuntu install. That is sda5. If anything, there are two Windows installs there (two ntfs partitions), but I doubt if that is really the case.

I think you should go here
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

and either just run the boot repair, or generate a boot info and post it here so that people can see what is where on your system.

Actually, I am not that sure about how well the boot repair deals with Win 8, so maybe posting the boot info is a better idea.

---

### Post by oldfred on 2012-12-28
If you see Ubuntu from a Windows menu, it probably is wubi. Although EasyBCD may look somewhat similar.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

    

Best to post link to BootInfo as suggested by audiomick as then we can see all the details.

---

### Post by Bucky Ball on 2012-12-28
Yep, only seeing one EXT4 partition there so the other install must be a Wubi install, as oldfred suggests; Ubuntu inside Windows.

---

### Post by Yougo on 2012-12-28
...

---

### Post by chubble10 on 2012-12-28
> **audiomick said:**
> Actually, I am not that sure about how well the boot repair deals with Win 8.
It's works fine!
I erased 7 and installed 8 (which of course got rid of GRUB), and boot-repair picked everything up fine to get the boot menu back.

When you get it all sorted, remember to [disable fast boot]("http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8"), as otherwise [file issues]("http://ubuntuforums.org/showthread.php?t=1953674") could occur!

---

### Post by grahammechanical on 2012-12-28
Might I draw our attention to this?

[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

I have seen references to Secure Remix in a few posts. I have not needed to use this tool but I have downloaded it just in case I do need it.

It has something called OS-Uninstaller (tool to uninstall any Operating System from your PC). I do not know how well it works but it seems like a useful utility to have.

There is a 12.10 version

[http://sourceforge.net/projects/ubuntu-secured/]("http://sourceforge.net/projects/ubuntu-secured/")

Regards.

---

### Post by verzx on 2012-12-28
Start again, install Windows 8 again then install Ubuntu. The way you want it so if you want Windows 8 to be the main OS then install that first and install Ubuntu alongside windows 8.

---

### Post by verzx on 2012-12-28
Start fresh and install Windows 8 then Ubuntu alongside Windows 8.

---

