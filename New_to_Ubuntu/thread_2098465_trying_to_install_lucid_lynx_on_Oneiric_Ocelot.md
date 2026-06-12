---
title: "trying to install lucid lynx on Oneiric Ocelot?"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by xXselkiesXx on 2012-12-26
Having issues reverting to Lucid Lynx after installing Oneiric ocelot... is it because the ISO is intended for use with Windows based systems? I've put the ISO on an SD card just like I had initially done for both the initial install with 10.04 and 11.10, but for some reason my system refuses to boot from the SD card as before. Any ideas or tips for a newbie? 
Thanks,
Joshua

---

### Post by Bashing-om on 2012-12-26
xXselkiesXx; Hi !

I can think of two causes - both grub related.
1. What have you got set in bios for boot priorities and where is grub installed ?
 grub I expect is still installed on the hard disk, if you make the 1st boot priority as the hard disk, can you boot to either of your ubuntu's ?
2. Grub is not installed on the SD card (default install is sda). If you can boot up as in (1.) You can install grub onto the SD card.
```
sudo fdisk -l #to determine the ID of the card
 sudo grub-install /dev/<card's ID>
sudo update-grub #updates grub's config files, picking up all operating systems

```reset boot priority to the SD card in bios.

 I anticipate this should work <== BDQ

---

### Post by xXselkiesXx on 2012-12-26
Seems I must be having a bad string of luck. Ive also forgotten my password as root user after returning from a deployment and have been unable to successfully work around it by using recovery mode. I can boot 11.10 but am restricted as guest user. I am also unsure about where grub is located, I'm still learning as a newbie :-P I have been setting boot priority to USB/SD card but if I could get grub on there I would agree it should work. Any alternative ideas on getting grub on SD without sudo commands? I'll see if it will work root user authentication.

---

### Post by Bashing-om on 2012-12-26
xXselkiesXx;

Let's do this to get your "sudo" back.
Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[INDENT][INDENT]one step at a time gets us there <== BDQ

[/INDENT][/INDENT]

---

### Post by xXselkiesXx on 2012-12-27
Got sudo back but had to edit the kernel command line in grub prior to boot. Success of some sort finally! Calling it a night and trying the commands in terminal you gave me first thing tomorrow!

---

