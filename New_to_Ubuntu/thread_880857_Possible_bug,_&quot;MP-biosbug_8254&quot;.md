---
title: "Possible bug, &quot;MP-biosbug 8254&quot;"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by richie42 on 2008-08-05
Okay, I am using Windows on this computer. It is version 8.04. I checked the CD, there are no problems, it passed the test. Right when I was about to install the OS, it said this.

MP-biosbug 8254 timer ot connected to IO APIC.

Help, I don't want to install a Linux on a bad computer.

**I am not too good with computers (worse with working with Linux) so can you simplify your answer for me?**

---

### Post by bobnutfield on 2008-08-05
Don't Panic!  This is a common bug, normally related to laptops.  I have the same error  at the boot prompt from grub and it generally causes no issues at all.

---

### Post by dca on 2008-08-05
Does your motherboard allow you to go into BIOS and disable APIC???

---

### Post by dca on 2008-08-05
Also, someone may have to chime in and see if this is still relevant but when Dapper was released 2+ years ago a lot of others rec'd same message and simply added 'noapic' as an addendum to the kernel arguments
 
[http://ubuntuforums.org/showthread.php?t=191355](http://ubuntuforums.org/showthread.php?t=191355)

---

### Post by dca on 2008-08-05
> **bobnutfield said:**
> Don't Panic!  This is a common bug, normally related to laptops.  I have the same error  at the boot prompt from grub and it generally causes no issues at all.

I like this answer the best because it simply sounds like the motherboard and guts were config to work with an MS OS specifically, but not only...

---

### Post by bobnutfield on 2008-08-05
> **dca said:**
> I like this answer the best because it simply sounds like the motherboard and guts were config to work with an MS OS specifically, but not only...

This has actually been covered quite extensively, and you are correct, noapic at the boot prompt will *usually* eliminate the message, but sometimes things like frequency scaling will no longer work with noapic.

---

### Post by bobnutfield on 2008-08-05
Here is a thread from linuxquestions about this issue:

[http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/]("http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/")

---

### Post by richie42 on 2008-08-05
Okay, now when I got to the boot from CD point, I pressed F6 and a selection box came, "noapic" was one of the selections and I selected it. It looked all good when I selected the install point. However, it said this when I loaded the installer:
starting log daemon sk (there were other sets of ransom letters, I could not write them down all at once)

Also, when I restarted the computer, the box was ot selected that time. Do I eed to select "noapic" for the oe time that I install Ubuntu or is there a problem with what I got.

---

### Post by bobnutfield on 2008-08-05
Are you running the live cd or trying to install?  If you are running the live cd, then you will have to issue that command each time you boot from it.  But, I would suggest trying to boot without issuing noapic and see if it causes any issues.  I am betting it will not cause any problems.

---

### Post by richie42 on 2008-08-05
What's the Live CD? I would say I am trying to install the OS then.

---

### Post by bobnutfield on 2008-08-05
I see, I misunderstood your previous post.  Is this error message preventing you from installing?  If it is not, then you can proceed with the install and once installed, you can edit the boot line in your menu.lst file to include noapic.  Don't worry about what that means at this point.  This bug (MP BIOS 8254) does not usually prevent you from installing.

---

### Post by richie42 on 2008-08-05
> **bobnutfield said:**
> I see, I misunderstood your previous post.  Is this error message preventing you from installing?  If it is not, then you can proceed with the install and once installed, you can edit the boot line in your menu.lst file to include noapic.  Don't worry about what that means at this point.  This bug (MP BIOS 8254) does not usually prevent you from installing.

Okay, sorry if I am overcautious, I don't want to erase a hard drive and put on a bad OS (did that once).

---

### Post by bobnutfield on 2008-08-05
That is fine, you are very wise to be over-cautious while you are learning the system.

Are you dual booting with Windows on a separate partition?

---

### Post by richie42 on 2008-08-05
No, I am not dual booting. I got Ubuntu so I could swipe the hard drive so I could get rid of a virus. Anyways, I got a big monitor ad the 800 X 600 resolution is too small. Can I increase the screen resolution?

---

### Post by bobnutfield on 2008-08-05
Yes, you can, but you should consider what graphics card you are using.  If you are using nVidia or ATI, there are proprietory drivers available that will tremendous improve your graphics.  Once your system is installed, go System>Administration>Hardware Drivers to see if there are any drivers recommended.  If not, you can adjust your Display in the System menu as well.

---

### Post by richie42 on 2008-08-05
I am using NVidia!

It is just annoying that I had 1280 by 768, and I would like it high or closer to that resolution.

---

### Post by bobnutfield on 2008-08-05
OK, your easiest solution (has always been for me anyway), is to install a program called EnvyNG.  This program will determine your video care, select the correct driver for it, and install and configure your display automatically.  You can get EnvyNG from the Synaptics Package Manager, or just type in a terminal:

> sudo apt-get install envyng

---

### Post by richie42 on 2008-08-05
I copied and pasted, but I got this:

```

richard@theSelbys:~$ sudo apt-get install envyng 
[sudo] password for richard: 

Sorry, try again.
[sudo] password for richard: 
Sorry, try again.
[sudo] password for richard: 
sudo: 2 incorrect password attempts
richard@theSelbys:~$ sudo apt-get install envyng 
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng
richard@theSelbys:~$ 



```

---

### Post by bobnutfield on 2008-08-05
Sorry. try the command again, like this:

> sudo apt-get install envyng-core envyng-gtk

I forgot to add the -core.  This will install the program and also a GUI for it you can find after installation in Applications>System

Also, when you open the package manager, make sure the first four repositories are checked (Settings>Repositories)

---

### Post by richie42 on 2008-08-05
Okay, where is settings > repositories on Envy NG?

---

### Post by bobnutfield on 2008-08-05
No, no, the repositories are in the settings section of the Synaptic Package Manager, not EnvyNG.  If you have EnvyNG installed, just run it and follow the instructions.

---

### Post by richie42 on 2008-08-05
I installed it. I restarted the computer ad it looks beautiful.
Thaks, man.

---

### Post by bobnutfield on 2008-08-05
My pleasure.

---

### Post by richie42 on 2008-08-05
I am unsure if this is *really* a problem but it has been over 3 hours since I installed Google Toolbar for Firefox and I cannot get any of my bookmarks.

---

