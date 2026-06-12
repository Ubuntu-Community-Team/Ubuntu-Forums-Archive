---
title: "Old PC, but Ubuntu running very slowly"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by Kev Black on 2012-10-07
Hi,
got tired of XP on an old PC of mine, and thought it is time to leap to Linux.

I downloaded 12.04 and created a bootable usb stick and installed successfully.

However I am disappointed in how slow the machine is.

It has an AMD Athlon XP 2700 CPU, 120Gb free drive space, but only 1/2 Gb of RAM.
It has an MSI/ATI R350 /Radeon 9800 graphics card.

free - mem reports:

    total       used       free     shared    buffers     cached
Mem:           495        488          7          0          1         74
-/+ buffers/cache:        412         83
Swap:          509         75        434

I can see that the graphics card is not properly supported now and is using the basic open-source drivers.....

Additionally using firefox, embedded video (for example on BBC sites) is not playing...

I'm not sure where to go from here - I could upgrade RAM, as that looks tight (!) but not sure if that helps.
Not sure if the fact the graphics card is using non-specific drivers is the problem.
Expected embedded video to works.

A bit stuck, so any advice or options welcome.

Thanks in advance.

---

### Post by akoskm on 2012-10-07
Regarding to [Radeon Driver]("https://help.ubuntu.com/community/RadeonDriver") wiki page your radeon card has good 3D acceleration support.
I would start with installing video drivers. That will improve the overall performance.

Open **System Settings > Hardware > Additional drivers**. That will check are there any proprietary drivers available for your system, including your Radeon card.

---

### Post by NikTh on 2012-10-07
> **Kev Black said:**
> 

free - mem reports:

    total       used       free     shared    buffers     cached
Mem:           495        488          7          0          1         74
-/+ buffers/cache:        412         83
Swap:          509         75        434

Hi , 

this is poor RAM (512MB). 

Ubuntu 12.04 is a new O.S compared with windows xp (10-12 years old) and it needs more RAM than 512MB. 
However other Ubuntu Versions exists for low specs machines. 

First I suggest Lubuntu 12.04 (lighter than Gnome 3.4 and Unity plugin) ==> [http://lubuntu.net/tags/lubuntu-1204](http://lubuntu.net/tags/lubuntu-1204)

Then I suggest an even more lighter Distro based in Ubuntu 12.04 , Bodhi Linux 2.0 => [http://www.bodhilinux.com/](http://www.bodhilinux.com/)

As for your graphics card you will need the ID and not only the model , so you can search better. 
Open a terminal and give this command ```
lspci -nnk | grep -iA2 vga
``` and you will see various info , ID included. 

Thanks

---

### Post by Peripheral Visionary on 2012-10-07
1/2 gig of RAM is insufficient for Ubuntu. I know the system requirements page doesn't say that, and Ubuntu does run on machines with the minimum required RAM, but some graphics cards borrow a lot too. 

Have you tried either of Ubuntu's younger siblings that are *designed for modest hardware*?  Check out [Xubuntu]("http://xubuntu.org") and [Lubuntu]("http://lubuntu.net")!  Give them a test drive. Either will run speedily on your machine.  

My computer also has only 512 of RAM and it runs Xubuntu nice 'n' fast.

Now by the time I clicked the Submit button someone else had already beat me to the same point. So just call me Ditto.

---

### Post by Kev Black on 2012-10-07
kev@kev-linux:~$ lspci -nnk | grep -iA2 vga
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI R350 AH [Radeon 9800] [1002:4148]
    Subsystem: Advanced Micro Devices [AMD] nee ATI Device [1002:4f72]
    Kernel driver in use: radeon

when I open
**System Settings > Hardware > Additional drivers**.
It tells me no proprietary drivers are in use.... 

So I think that means I'm using the only/best driver for the card? and although maybe not perfect I think it should mean it is not the card causing the pathetic performance???

I guess I could invest in another gig of RAM to see if that makes a difference.....

Any ideas why embedded video is not working?

Thanks for the help so far.

K

---

### Post by Peripheral Visionary on 2012-10-07
> **Kev Black said:**
> k
Any ideas why embedded video is not working?

Try installing the Ubuntu restricted extras package if you haven't already done so. It has the multimedia codecs and such.

---

### Post by ojdon on 2012-10-07
Like other people have stated, Ubuntu would definitely struggle with 512MB of RAM, but [Lubuntu]("http://lubuntu.net/") would be so much quicker. You should definitely consider making the move.

---

### Post by HermanAB on 2012-10-07
Fuhgedabout running regular Ubuntu on that machine. Lubuntu and Xubuntu will fly however.

---

### Post by gradinaruvasile on 2012-10-07
> **akoskm said:**
> Regarding to [Radeon Driver]("https://help.ubuntu.com/community/RadeonDriver") wiki page your radeon card has good 3D acceleration support.
I would start with installing video drivers. That will improve the overall performance.

Open **System Settings > Hardware > Additional drivers**. That will check are there any proprietary drivers available for your system, including your Radeon card.

Radeon 9800 is not supported anymore by proprietary drivers (thats really old news, since Ubuntu 8.10 old).
You can use ony the open source ones (the ones you already have). Make sure you have the firmware-linux-nonfree package installed and disable KMS.

I agree on installing Xfce (xubuntu). The default Unity desktop is demanding hardware-acceleration wise, its not suitable for older machines.

---

### Post by Kev Black on 2012-10-07
OK so xubuntu being installed tonight.....
 
thanks

---

### Post by mips on 2012-10-07
Get some more ram if you can as it really does help in linux.

---

### Post by ssulaco on 2012-10-07
> **Kev Black said:**
> 
However I am disappointed in how slow the machine is.
It has an AMD Athlon XP 2700 CPU, 120Gb free drive space, but only 1/2 Gb of RAM.
The AMD 2700 should be clocking between 2-2.5 gig..should be plenty for Ubuntu....Im guessing you can install more than 500mb of ram,probably up to 2 gig......I agree with mips....MAX it out,mem is cheap..try eBay 
> **Kev Black said:**
> OK so xubuntu being installed tonight.....
 thanks
Xubuntu,is a great choice,Im running the current LTS,Rock Solid,....I would still max out your mem.

> **mips said:**
> Get some more ram if you can as it really does help in linux.
big time

---

### Post by will1982 on 2012-10-07
> **Kev Black said:**
> OK so xubuntu being installed tonight.....
 
thanks

Lubuntu uses less ram then xubuntu

---

### Post by Peripheral Visionary on 2012-10-08
> **will1982 said:**
> Lubuntu uses less ram then xubuntu

LXDE may use less than Xfce, but I find **no measurable difference** between Xubu and Lubu on my 8-year-old Dell with the same RAM as the OP's.

Except that Xubu has more features available and is more configurable.  Lubuntu is beautiful and fast, though, and previews of the next release look awesome.  If future versions of Xubuntu prove to be too much for my old hardware, Lubuntu is the first alternative I'll check out.  I love the file manager (PCManFM) and use it in place of Xubu's Thunar. I also really like the customized Lubuntu Software Center and use it in place of the Ubuntu Software Center.  Lubu is an up-and-comer that certainly holds a lot of promise.

---

### Post by will1982 on 2012-10-08
> **Peripheral Visionary said:**
> LXDE may use less than Xfce, but I find **no measurable difference** between Xubu and Lubu on my 8-year-old Dell with the same RAM as the OP's.

Except that Xubu has more features available and is more configurable.  Lubuntu is beautiful and fast, though, and previews of the next release look awesome.  If future versions of Xubuntu prove to be too much for my old hardware, Lubuntu is the first alternative I'll check out.  I love the file manager (PCManFM) and use it in place of Xubu's Thunar. I also really like the customized Lubuntu Software Center and use it in place of the Ubuntu Software Center.  Lubu is an up-and-comer that certainly holds a lot of promise.

I've never used Xubuntu or Lubuntu, just repeating rumors.
I guess it boils down to personal preference then.

---

### Post by mr-woof on 2012-10-08
I'd recommend crunchbang for any old machines, i'm using it now on this netbook. Crunchbang running and connected to the wireless, uses 92 meg of ram. Openbox is a bit mad at first, but it's very good once you get the hang of it.

---

### Post by Pilot6 on 2012-10-08
Strange. I have 2 pcs with almost same specs. Both AthlonXP with 1.5 GB RAM.
1. With same Radeon card with free driver
2. With an old Nvidia with proprietary.
Both work quite well.

Oops. 500MB is not enough.

---

### Post by Kev Black on 2012-10-09
Well thanks, installed Xubuntu, and the difference is amazing. I'ts not super fast but it is an old PC, but VERY VERY usable, and Xubuntu for my basic needs looks fine....

Still no flash video tho.
 
Thanks for everyone's help, and I think I will buy a bit more RAM just for fun!
 
K

---

