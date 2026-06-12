---
title: "&quot;Boot Error&quot; when running Ubunto from usb - while same usb worked in another computer"
date: 2016-09-02
forum: New to Ubuntu
---

### Post by Eliran on 2016-09-02
Hi Everyone,
I'm struggling full day with the next problem:



[LIST]
[*]There is a prepared disk on key with Ubuntu on it.  I've seen in my own eyes that it worked on another computer when this disk on key was given to me.
[/LIST]



[LIST]
[*]In my house, I changed the boot order as I've been told , for the first boot will be from USB-HDD (For the operating system will be launched from the disk on key, and not Windows which is in the Hard Disk). I made it through the bios, and tried also through boot menu (F12).
[/LIST]



[LIST]
[*]Every time I get the next message: "Boot Error". I do not get to the phase when I should chose between "Try Ubunto" and "Install ubunto". I mean this error of "Boot Error" shown very early - before any other message.
[/LIST]



[LIST]
[*]I tried download Ubunto to an other DOK I have. There the result was that I didn't get any message, and the computer ignored this DOK at all. I mean Windows started up and not Ubunto.
[/LIST]


Last thing that maybe is important -  My computer is 9 years old. I see in my bios only Legacy option and not UEFI.


I will really appreciate any help with this issue  
thank you,
     Eliran.

---

### Post by oldrocker99 on 2016-09-02
A 9 year old PC will have BIOS but not UEFI. 

You need to change the boot order to CD-ROM or USB appearing FIRST. Then change the order back to the HDD appearing first after installation on reboot. Or you can leave it as you changed it, and if there's no CD-ROM or USB available, the PC **should** start from the HDD.

If you can't start the installation with F12, you **may** have a defective installation medium. Try another disk or USB thumb drive and see if you get a boot.

---

### Post by jarvis3 on 2016-09-03
Heres how i install ubuntu and u should try this. I installed rufus [ a bootable drive thingy XD ] [https://rufus.akeo.ie/](https://rufus.akeo.ie/)  Then i installed the ubuntu iso image from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) . then open rufus and have a usb drive in the pc. you should do this all on an other computer btw! anyway add the iso image on to the desk top. on the top bar select the usb drive then gpt partition scheme for uefi then fat32, 8192 bytes. below you will dee and image on the left side of the words iso image. click on it and browse for the iso image u installed

---

### Post by yancek on 2016-09-03
Generally, you should see the name of the drive in the options since computers are capable of booting from different drive.  So look for the name of it, Sandisk, Toshiba or whatever it is.  Have you ever booted from a flash drive with this computer?  At that age, it may not be capable of booting from a flash drive.

---

### Post by Bucky Ball on 2016-09-03
> **jarvis3 said:**
> on the top bar select the usb drive then gpt partition scheme for uefi then fat32, 8192 bytes.

As has already been mentioned, this machine does not have UEFI. Please read other posts before posting as this detail is in the first line of the post above yours. Also see the last line of the first post in the thread. Thanks. :)

Also, your screenshot didn't make it. 'Adv Reply' or 'Go Adv' and use the paperclip icon in the toolbar there.

The USB is working fine, no problem there as it is working on other machines, just not the one in question, so knowing how to create the install media is not the issue here.

---

### Post by mook765 on 2016-09-03
I see only two possibilities why your machine is not able to boot from this pendrive.
a) The pendrive is only UEFI-capable
b) You have a 32 bit machine and try to boot a 64 bit operating system.
Find out the capabilities of your computer or provide information about your hardware, so we can find it out.
We can't know what is on your pendrive, and we don't know which hardware you use, so how can we help you solving the problem?

---

### Post by Geoffrey_Arndt on 2016-09-04
If your old PC has a CD or CD/DVD drive, then, . . . after downloading the iso - - use a good disk burning program and burn an iso-image file to either CD or DVD (Lubuntu may still fit on 1 CD, but Xubuntu likely requires DVD).    Your old PC will boot from that media if you set the boot priority order in BIOS so CD/DVD is listed first.    I would suggest to try Xubuntu or Lubuntu on that old machine.   The chance of success are much improved.

---

### Post by sudodus on 2016-09-05
The current Lubuntu iso files (for 16.04.1 LTS) are too big for CD, but the following iso file is small enough, 696 MiB,

**lubuntu-14.04.1-desktop-i386.iso** with 'live session' alias 'Try Lubuntu' and the 'graphical desktop installer' alias 'ubiquity' for Lubuntu 14.04.1 LTS 32-bit kernel.

---

