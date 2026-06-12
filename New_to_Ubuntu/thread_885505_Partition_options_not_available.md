---
title: "Partition options not available"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by its_jon on 2008-08-10
Just downloaded the latest Ubuntu stable.

I am trying to overwrite an install of XP Pro......

When I get to the partition window the options are hashed out and I have nothing in the big white box (which I presume should show some partition graphs or someting)

In the prepare partitions box I only have the options
Cancel, back or forward.

Clicking forward throws up the error message (No root defined) as you would expect.....

any ideas ????

thanks

---

### Post by Elfy on 2008-08-10
Check the cd for defects.

Check md5sum of download.

Use the partition editor in sys - admin to do the partitioning before you get to install.

---

### Post by its_jon on 2008-08-10
Thanks.....

I checked the disk using the option to check on the install menu.

{Use the partition editor in sys - admin to do the partitioning before you get to install. }

sys - admin ? .... It that in xp ?

---

### Post by Elfy on 2008-08-10
> sys - admin on the livecd menus - gparted is called Partition Editor there.

---

### Post by its_jon on 2008-08-10
Found it.... gparted Reports "no devices detacted" ?

Something bios related ?

MoBo is foxconn A6VMX

---

### Post by Elfy on 2008-08-10
> Something bios related ?Perhaps it is something specific to your hardware but not sure obviously.

What are you trying to install it on?

---

### Post by its_jon on 2008-08-10
/Ok.... the full story...

My Mum 70 year old.... wanted me to get her a PC.

Most important bits I thought would be a nice big screen and a quality mouse and keyboard.

It arrived (I normally build my own but I needed a guarantee for this one) fully built. (exept OS)

I have an XP disk which has never let me down...... It let me down with this PC..... No Mouse .... Possibly a mobo jumper issue however plugging it into a USB eventually worked after 10 reboots or so.

However I have always experimented with Linux but never yet got a version to install properly..... As xp looks rubbish on a widescreen monitor.... and this PC will be going to someone who will have a learning curve weather its windows or xwindow then I think its a good thing to try.... Ubuntu certainly looks ace and user friendly/warm.

So..... its a new machine....

AM2+
Semperon LE-1200 2.1ghz AM2
512Mb DDR2 667Mhz PC5300
80 gig SATAI/II 2mb cash
450 psu

---

### Post by Elfy on 2008-08-10
I did have some problems a while back with the livecd partition editor onone for my mum funnily enough - I use a bootable part editor instead and all went ok, but maybe you'd be better of with the alternative.

Another thing you could try - I had to go into the bios on a hdd and make sure that the access mode was set right - I needed toset it to auto - slightly different problem there - it installed but grub didn't see it.

I use partedmagic which also has testdisk and photrec so it's a good tool to have -
[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads) - if you try it - burn as an iso/image so it can boot

---

### Post by its_jon on 2008-08-10
Bios appears to be right.....

ok enough to get xp up and running.

It appears that ubuntu has not detected a hard drive available to partition.

so maybe its the HD type ?

80 gb Maxtor DiamondMax SATAI/II 2mb cashe ?

IDE Master is CDROM slave not installed

HD is on SATA ch1 ....... anything to check out there ?

thanks

---

### Post by Elfy on 2008-08-10
Odd - I'd be interested to know if it get's recognised once xp is installed, but I can't think of any reason why it's not recognised by the livecd.

Did you try with a differerent editor?

Sorry I can't be of more help :(

---

### Post by its_jon on 2008-08-10
XP was installed prior to ubuntu.

:confused:

---

### Post by Elfy on 2008-08-10
sorry - long day :lol: - I did read that earlier, honest.

Still can't see why it isn't recognised.

---

### Post by its_jon on 2008-08-10
Well.... I installed the motherboard tools disk under XP.

Its made xp look and work better....

I then booted into the live Ubuntu CD in the hope that it may have collected some new info....but nope... still no HD in my pc.

Im sure its a simple fix 8-[ .....anyone ?

---

