---
title: "Can't boot into ubuntu"
date: 2024-11-01
forum: New to Ubuntu
---

### Post by javizuma on 2024-11-01
Hello! I’m new to Ubuntu and currently using it on my workstation. Recently, I’ve been experiencing some boot issues.


I ran Boot Repair and received the following message: [https://paste.ubuntu.com/p/HJXWGsGWpv/](https://paste.ubuntu.com/p/HJXWGsGWpv/) 


Could you please advise me on what steps I should take next? Thank you!

---

### Post by yancek on 2024-11-01
You forgot to post what those 'boot issues' are so all we can do is guess.  Post some specific information on exactly what happens when you select to boot Ubuntu.  Has it been booting successfully since the initial install?  I see you have it set to NOT show the boot menu, was that a choice you made?  Does your system boot?  Can you boot when you select Ubuntu from the BIOS boot options menu?

---

### Post by javizuma on 2024-11-01
The main issue is the inconsistency in booting up. Sometimes, it boots to the login screen, but after I enter my password, it gets stuck on a black screen. Other times, it doesn&#8217;t even make it that far. Occasionally, I can get it to boot by pressing F12 and selecting Ubuntu (but this doesn't always work and gets stuck in the login screen). 


Also, I&#8217;m curious about the boot menu. I don&#8217;t remember intentionally disabling it, but should it be showing up? I also tried booting selecting ubuntu from the BIOS, but that didn&#8217;t work either. On the bright side, I was able to boot from a USB with Ubuntu on it!

---

### Post by javizuma on 2024-11-01
I&#8217;m still having some trouble, but I did try using Boot Repair, and here&#8217;s the new report it generated: [https://paste.ubuntu.com/p/VnG78GvsH5/](https://paste.ubuntu.com/p/VnG78GvsH5/).

When I went through it, I noticed this message:
[INDENT]"Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.4 LTS entry (sda1/efi/ubuntu/grubx64.efi file)!"
[/INDENT]Could this be related to the issue I&#8217;m facing? And if so, would you have any advice on how I can go about fixing it? I already have ubuntu as my top priority for booting in the BIOS, but I don't know if that's exactly what this is referring to. Thanks!

Thank you so much for your help!

---

### Post by yancek on 2024-11-01
If you only have Ubuntu installed on the computer, the default is not to show the menu.  You can change this by editing as root (use sudo) the text file  /etc/default/grub and make sure there is a line like the one below there.  You need to run sudo update-grub after making the change to have it take effect.

> #GRUB_TIMEOUT_STYLE=menu 

>  Locked-NVram detected.


I've seen a number of threads recently with that error but no single solution so I would start by doing a search here for 'locked nvram detected', maybe include the manufacturer name of your computer.

---

