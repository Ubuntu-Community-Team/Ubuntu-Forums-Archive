---
title: "Replacing Windows with Ubuntu and using Windows as a virtual machine"
date: 2018-01-22
forum: New to Ubuntu
---

### Post by bsodx on 2018-01-22
Hi there, it's a brand-new user.

I'm very new with Linux/Ubuntu, while I plan to learn to fly soon. My problem is: I recently saw an article about migrating Windows to Ubuntu and running Windows as a virtual machine for increased security. I decided to do this as well.What do I need to know is:

1.Is there a program that can be used instead of VmWare? It sounds like a business solution and it looks like it could betray a non-commercial user (Like they can remove the Player or something like that)

2.Is a 4 GB total RAM and 350 GB empty space enough? Disk would be, but I can't make sure that RAM would handle this.

Thanks in advance!

(Guide on article was: Convert Windows to a virtual machine instance with VmWare Converter -> Delete Windows and install Ubuntu -> Load Windows' virtual instance using VmWare Player)

---

### Post by tinylagarto on 2018-01-22
I personally do not use virtualization anymore but I know of and used Virtualbox. It is in the Ubuntu repositories.

---

### Post by ajgreeny on 2018-01-22
Which version of Windows do you have and was it the OS that came with the machine?

It is very likely that it is an OEM installation if it was on your computer when you purchased it and it will therefore be usable only on the original hardware, which a virtual machine, even if itself running on that same hardware, is not in Microsoft's eyes.

You would therefore have to purchase another license from Microsoft for your virtual installation no matter how unfair that seems to be; I am not even sure if you can get Windows 8 and above to install to unknown hardware, but I may be wrong about that as my last Windows use was XP.

---

### Post by QIII on 2018-01-22
^^  This (the license issue) will be the greatest hurdle.

---

### Post by bsodx on 2018-01-23
> **ajgreeny said:**
> Which version of Windows do you have and was it the OS that came with the machine?

It is very likely that it is an OEM installation if it was on your computer when you purchased it and it will therefore be usable only on the original hardware, which a virtual machine, even if itself running on that same hardware, is not in Microsoft's eyes.

You would therefore have to purchase another license from Microsoft for your virtual installation no matter how unfair that seems to be; I am not even sure if you can get Windows 8 and above to install to unknown hardware, but I may be wrong about that as my last Windows use was XP.

It is Windows 7 SP1, and I found that it's an OEM version.

In my opinion there's two legal options to evade the license trouble:

1.If Converter is taking a system image and it's deployed on same hardware, it should continue working in the same manner. I know that OEM licenses save themselves with processor info so they can't be installed on another computer, but can still be used on the same one.

2.Using a retail code: I should have a retail copy somewhere. I'll just activate it on this one, but finding that retail is another trouble.

Also thanks for replying that fast.

---

### Post by HermanAB on 2018-01-24
You can get a free copy of Windows 10 if you sign up as a MS Beta tester:

[http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html](http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html)

---

### Post by wrongusername2 on 2018-01-24
I have same setup as you. I run Ubuntu 16.04 on physical machine and Win7 runs as VM. I use Virtual box, it is free. You may need more than 4gb of RAM. 

In my case I built Win7 VM when I was still running Win7 on my laptop. I used Virtual box. I backed up the whole VM to an external hard drive.
Then I installed the Ubuntu, installed Virtualbox and imported the Win7 VM in to Virtual box.

---

### Post by chris53 on 2018-01-24
Following this thread...   I think I would like to do the same thing

---

### Post by bsodx on 2018-01-25
> **HermanAB said:**
> You can get a free copy of Windows 10 if you sign up as a MS Beta tester:

[http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html](http://www.aeronetworks.ca/2015/02/windows-10-on-virtualbox.html)

Insider program now requires a copy of Windows 10 to work.

Update: I virtualized Ubuntu a day ago and it's doing well, except some performance drops.

---

