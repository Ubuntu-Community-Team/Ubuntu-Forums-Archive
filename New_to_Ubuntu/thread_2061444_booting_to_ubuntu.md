---
title: "booting to ubuntu"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by eatingstick on 2012-09-22
Hello all, I am a complete beginner so please be patient.
I have just downloaded ubuntu-12.04.1-desktop-i386, installed it to my pendrive and installed it alongside my pre-existing windows 7. It worked fine but now, whenever the computer is off and I press the power button (or simply restart from either Ubuntu or Windows 7) it boots directly to Windows 7. If I press f5 during the boot it only gives me the Windows 7 option.
The only way I have to boot into ubuntu is by keeping the USB pendrive inserted.
When the pendrive is inserted I can choose to boot to Ubuntu or Windows 7, when I choose Ubuntu it loads with all the programs I put in during the previous session (so I guess it's not booting to the live version everytime).
I have no previous experience with any other operating system other than Microsoft Windows, I've never installed any other operating system on my computer which has all the default Windows 7 settings.
How can I choose the OS without having to boot from my pendrive?
Thanks in advance for any help you can give me.

---

### Post by kc1di on 2012-09-22
Hi eatingstick and welcome to Ubuntu and Linux,

There have been some problems reported on some installs where the Grub boot loader is installed to the usb drive instead of the machine's Master Boot Record (MBR)
you can go to this page and download and run boot repair which should fix the problem for you.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

If it does not fix the boot problem then there is an option to create a boot information file that you can post here and it will give us a better idea of what will need to be done.

---

### Post by eatingstick on 2012-09-22
Hi kc1di, thank you for answering.
I just booted back to ubuntu with the USB live pendrive to follow the instructions to install the boot-repair directly in Ubuntu using the "sudo apt..." and am not managing to connect to my wi-fi. During the last session I had installed some updates so I'm guessing that's what did it since it's been connecting to my wi-fi just fine.
How can I go back to before it installed the updates? Or is there anything else I should do?
Also... should this problem be posted as a new thread?
Thank you.

---

### Post by kc1di on 2012-09-22
> **eatingstick said:**
> Hi kc1di, thank you for answering.
I just booted back to ubuntu with the USB live pendrive to follow the instructions to install the boot-repair directly in Ubuntu using the "sudo apt..." and am not managing to connect to my wi-fi. During the last session I had installed some updates so I'm guessing that's what did it since it's been connecting to my wi-fi just fine.
How can I go back to before it installed the updates? Or is there anything else I should do?
Also... should this problem be posted as a new thread?
Thank you.

The wifi problem should be posted separately for a better chance of an answer.  My guess though is that you received a new kernel and not an update on the driver module. but that's just a guess. 
can you connect via LAN?  if so try to get the boot problem fixed first.

---

### Post by eatingstick on 2012-09-22
Ok, the problem seems to be solved now. 
Also the connection problem seems to be fine now.
Thank you kc1di.
next question is: how do I file this as "solved" ?

---

### Post by kc1di on 2012-09-22
click on edit and edit the subject line :)

---

