---
title: "Booting Problems"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by eagleclaw on 2012-01-27
Newly installed Ubuntu 11.04 from a purchased disk. Used whole drive for OS (no dual boot or sharing). Laptop boots up to the "Ubuntu" start screen then goes gray and non esponsive. Turn pwr off and restart. Not sure what triggers the screen, but after several tries I get the GNU Grub version 1.99-12 Ubuntu5 screen. Then I can choose Ubuntu with Linux 3.0.0-15 generic. Then the system boots up and I am in business and the system seems to work fine. 

How do I troubleshoot the boot hang up.

---

### Post by wolfen69 on 2012-01-27
Next time the system boots up to the desktop, try:
```
sudo update-grub
```
and reboot.

Btw, did you do any system updates?

---

### Post by eagleclaw on 2012-01-27
Thanks for the reply and tip, I assume I was supposed to type grub update in the terminal. Thats what I did and did get results back in the terminal window. Unfortunately it did not solve the problem. I am getting to where during boot up, if I do a contrl-Alt-S (which is how I get to bios setup) at just the right time I can get to the grub page. The other options are Memory Test, previous versions (which is generic 12 instead of 15). I am going to try the Memory test which takes a long time and see what the results of that is. 

Thanks again, any other tips in your bag of tricks?

---

### Post by wolfen69 on 2012-01-27
> **eagleclaw said:**
> 

Thanks again, any other tips in your bag of tricks?

To get grub manually every time, just hold the shift key during bootup. No need to go into bios first. But something definitely is not right.

---

### Post by nipunshakya on 2012-01-27
try running an update from synaptic package manager and restart your machine...maybe that can help you out....just make sure you mark all upgrades and apply those,....your system will download them and you need to restart yo complete your update...(make sure you select all available updates)

Regards,WinuxUser

---

### Post by eagleclaw on 2012-02-01
Okay, I have upgraded everything that is to upgrade. I still do not boot properly. 

What is Grub and why do I have to get to the Grub screen in order to to boot to Ubuntu? 

I there a way to get a line by line boot so I can see what the computer is doing during the boot process? 

How do I flash my BIOS to make sure it is not that causing the issue?

---

### Post by eagleclaw on 2012-02-01
Oh, I forgot to add that I was running Ubuntu 8.04 before and it booted fine. I did not use a Linux system until just recently getting serious about learning it and using it. I used the 8.04 in a dual boot and found I never used it. A few weeks ago I used the 8.04 image to re-partition the whole drive and go Linux all the way. This is an old P3-1000Hz-512M laptop and after installing the 8.04 which seemed to work fine, it was way out of date and I upgraded to 10.04 over the internet (took 4 hours). For some reason 10.04 was not co-operating so I ordered the 11.04 CD using mail. 

So.... is this computer not compatible for Ubuntu above 8.04 version?  I don't give up easy.  If I get past this booting issue then I can start exploring the world of open source computing.

---

### Post by nipunshakya on 2012-02-03
> **eagleclaw said:**
> Okay, I have upgraded everything that is to upgrade. I still do not boot properly. 

What is Grub and why do I have to get to the Grub screen in order to to boot to Ubuntu? 

I there a way to get a line by line boot so I can see what the computer is doing during the boot process? 

How do I flash my BIOS to make sure it is not that causing the issue?

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
To see your line by line boot, maybe its located somewhere in your /etc/default/grub (im on windows now so cant be specific...still, try there)
Regarding your BIOS, i dont know about that man...

Regards,WinuxUser

---

### Post by nipunshakya on 2012-02-03
Regarding your laptop specs, i guess u might want to look at a hardware compatibility list before plunging into grub 3.0 for a p III

[http://wiki.untangle.com/index.php/Hardware_Compatibility_List](http://wiki.untangle.com/index.php/Hardware_Compatibility_List)

---

### Post by oldfred on 2012-02-03
One of the more common issues is video related. I have had to use nomodeset on every first boot until I install the nVidia driver.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by elliotn on 2012-02-03
remove NVIDIA-common ```
sudo apt-get remove nvidia-common
```
90% it will work

---

