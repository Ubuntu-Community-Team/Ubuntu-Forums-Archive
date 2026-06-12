---
title: "Problem installing Ubuntu 12.10 in an HP laptop"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by dohc97 on 2012-12-04
Absolutely a newbie in Ubuntu here.  I have an HP Envy 15 with 64 bit Windows 7 Pro installed in it.  Specs are i7-3610QM, 8 Gig of ram and 1 TB of hard drive space. My display adapters are an Intel HD Graphics 4000 and a Radeon HD 7750M. I tried installing Ubuntu 12.10 the other day but it just ejects the CD and leaves me at a black screen.

---

### Post by 2F4U on 2012-12-04
Does it boot from the CD? If yes, how far do you get in booting from the CD? Did you verify the checksum of the downloaded iso file? Did you burn at the lowest possible speed? Can you boot into the desktop environment of the liveCD?

---

### Post by arpanaut on 2012-12-04
12.10 iso's are way over CD size limits, could this be your problem?
Best try DVD or USB installation media.

---

### Post by dohc97 on 2012-12-04
I meant to say I burned it into a DVD, not a CD.

I just noticed that I used an iso for an amd64.  Should I use the iso for i386_32bit?  My HP runs on an intel and is a 64 bit machine.

---

### Post by arpanaut on 2012-12-04
AMD64 is for both intel and amd 64 bit processors, it's named that way because AMD implemented 64 bit first, confusing for some.

Might be a bad burn, or a bad download of the image.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the iso proves okay try another burn "as an image"

---

### Post by rutafid on 2012-12-04
I had to install 32 bit 12.4 instead of 12.10. After that everything works great

---

### Post by rutafid on 2012-12-04
at the maximum spee in the bur in the burn program

---

### Post by COMECON on 2012-12-04
> **dohc97 said:**
> I meant to say I burned it into a DVD, not a CD.

I just noticed that I used an iso for an amd64.  Should I use the iso for i386_32bit?  My HP runs on an intel and is a 64 bit machine.

As it has been said, amd64 architecture can be installed on Intel processors. As you have 8GB of RAM and a 64-bit processor, you should install it. If you have, say 3GB of RAM, it wouldn't matter to install 32 or 64 bit, as the mainly advantage of 64 bit is to manage more than 4GB of RAM. 
Catbuntu

---

### Post by dohc97 on 2012-12-04
So, I ran the md5sum and the iso that I downloaded turned out OK.  I burned the iso again using the slowest speed.  I rebooted the laptop and it went thru the splash screen.  It then ejected the DVD and asked me to hit OK.  Once I did that, the PC rebooted and started in windows 7. 

I might try the 12.4 version next.

---

### Post by leunam12 on 2012-12-04
Try installing from USB stick.

---

### Post by squakie on 2012-12-04
> **dohc97 said:**
> So, I ran the md5sum and the iso that I downloaded turned out OK.  I burned the iso again using the slowest speed.  I rebooted the laptop and it went thru the splash screen.  It then ejected the DVD and asked me to hit OK.  Once I did that, the PC rebooted and started in windows 7. 

I might try the 12.4 version next.

Do you mean it went through the entire install process or that it stopped right after the DVD got to it's splash screen?

---

### Post by mastablasta on 2012-12-05
> **COMECON said:**
>  If you have, say 3GB of RAM, it wouldn't matter to install 32 or 64 bit, as the mainly advantage of 64 bit is to manage more than 4GB of RAM. 
Catbuntu
 
that is not true!
 
the main advantage of using 64bit OS is to use the full power of 64 bit CPU. RAM is just a bonus. as 32bit with PAE kernel (now default) can recognise up to 64GB ram anyway...

---

### Post by verzx on 2012-12-05
I'm having a simular problem on my laptop but my laptop is a HP Pavillion G6 Version, for some reason something always corrupts the ubuntu installation. Ubuntu 12.04 / 12.10 I've tried them both.
 
This is with running wubi.exe to install ubuntu (could just be that)
 
 

Doing either of the following; 
[LIST]
[*]Boots in to a Black Screen
[*]Windows chckdsk finds errors and fixes them, then ubuntu boots into grub
[*]Really Slow
[*]Freezes and have to restart
[*]Running Really hot (with jupiter and power saving mode)
[/LIST]Not sure why but I think it could just be something to do with the later developed HP Laptops in general.

---

### Post by mastablasta on 2012-12-05
> **verzx said:**
> I' 
This is with running wubi.exe to install ubuntu (could just be that)
 .
wubi installs on a virtual drive inside windows. so if somehting is wrong in windows it could also be wrong in ubuntu.
 
another option is that disk drive is going bad.
 
 
you might also need to install correct GPU drivers.

---

### Post by verzx on 2012-12-05
I installed the GPU drivers and neptune and put it on power saver and it was still hot. I'm going to try a USB installation tonight and i'll let you know how I get on, thanks anyway mastablasta. :)

---

### Post by Toriku on 2012-12-05
are you burning the image to disk, or burning an image of a disk as a file onto the disk?
its the most common mistake I've encountered for people trying to install a new OS for the first time, thought I should point it out

to be sure check the disk in windows, it should contain lots of files, if it contains just a ubuntu.iso or something then thats your problem...

I recommend IMGBURN as a burner rather than the windows default one... Its free and much more intuitive

---

### Post by mastablasta on 2012-12-05
> **verzx said:**
> I installed the GPU drivers and neptune and put it on power saver and it was still hot. I'm going to try a USB installation tonight and i'll let you know how I get on, thanks anyway mastablasta. :)
 
ah you have Intel GPU only. it's a different issue than OP. This intel GPU should work well out of the box. how did you install newer drivers? did you use the PPA?

---

### Post by COMECON on 2012-12-05
> **mastablasta said:**
> that is not true!
 
the main advantage of using 64bit OS is to use the full power of 64 bit CPU. RAM is just a bonus. as 32bit with PAE kernel (now default) can recognise up to 64GB ram anyway...

As far as I know it is, or at least it was. I have a 64-bit CPU but only 3GB of RAM, and all the people I asked told me that using a 64-bit system wouldn't have too much advantages, even it could be worse due to some applications' compatibility with 64-bit.
Also, Windows x86 was installed by default instead of x64, so I assumed that 64-bit would give me more problems that advantages.
Apologies if I'm wrong,
Catbuntu

---

### Post by dohc97 on 2012-12-05
> **Toriku said:**
> are you burning the image to disk, or burning an image of a disk as a file onto the disk?
its the most common mistake I've encountered for people trying to install a new OS for the first time, thought I should point it out

to be sure check the disk in windows, it should contain lots of files, if it contains just a ubuntu.iso or something then thats your problem...

I recommend IMGBURN as a burner rather than the windows default one... Its free and much more intuitive

I am using IMGBURN to burn the iso file to a DVD.

also, the file that I downloaded is just one iso file.  to be exact, it is called "ubuntu-12.10-desktop-amd64".  how do i get those other files?  did i download the wrong file?

---

### Post by verzx on 2012-12-05
> **mastablasta said:**
> ah you have Intel GPU only. it's a different issue than OP. This intel GPU should work well out of the box. how did you install newer drivers? did you use the PPA?

No. I have dual graphics, AMD APU Quad Core. HP Pavillion G6-1331ea Laptop. It prompted me with an update for the Graphics card after installing updates using the update manager.:)

---

### Post by mastablasta on 2012-12-05
windows 32bit (x86) has a max ram block built in by microsoft. mostly due to expected drivers issues. 
have a look: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
 
64bit linux is different as things work now. 32bit programmes simply use 32bit libraries as needed. 
 
it used to be like you describe, but things change. they change quite fast in IT.
 
plenty computers though still ship with windows home basic or similar with max ram at 4GB. i just got a laptop with windows 7 starter and 2GB ram (which is the max win7 starter hcan handle). the CPU is 64 bit and the max ram on the laptop can go up to 8GB. so i guess they expect me to upgrade the OS. and i plan to - to upgrade to Ubuntu 64bit :-)
 
 
it is also true that performance improvement might not be so big with less ram, but if you have 64bit CPU then why not use 64bit OS? and who knows maybe you would upgrade ram in near future and if you use LTS you wont' need a reinstall to go 64 bit.
 
anyway you can read a bit more here: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
> 
**Which is Better - 32 or 64 Bits?**
 
 
If you are doing heavy work where you have started to hit the 4GB memory barrier, then 64-bit is for you. Certain intensive tasks such as encoding video or audio also run significantly faster on 64-bit operating systems (NOTE: this is implementation specific). 
Phoronix has done some [testing]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1") (2009), comparing 32bit/PAE/64bit, and this seems to indicate that **64bit performs better than 32bit in almost all cases.** 
Early 64-bit adopters were plagued by incompatibility problems (most noticeably Java and Flash), however most issues have now been resolved. 
Some applications such as Flash do run slower in 64-bit mode, however work continues to improve on this. 
Other platforms which also come in 32 and 64-bit flavours may experience more problems especially due to a lack of 64-bit device drivers as incompatible user application. As Ubuntu is entirely open source, this is not the case as all hardware supported by Ubuntu works equally well in 32-bit and 64-bit environments. The same applies to open source user applications as well. 
 
**Which Should I Choose?**
 
Unless you have specific reasons to choose 32-bit, we recommend 64-bit to utilise the full capacity of your hardware. 

 
some people say even flash doesn't seem to be an issue anymore. but i guess ti still depends on hardware/drivers....

---

