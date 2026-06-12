---
title: "Installing Ubuntu on Dell with No Linux Experience"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by pcfast on 2012-07-28
Hello Everyone,

I have a Dell Dimension 2350 that I would like to install Linux on.  I have no experience with Linux or messing around with computers too much.   

Dell Dimension 2350 Specs: 
256MB of RAM
2GHZ Intel Celeron 
Windows XP

[http://support.dell.com/support/edocs/systems/dim2350/specs.htm]("http://support.dell.com/support/edocs/systems/dim2350/specs.htm")

The HD has about 10GB being used out of 60GB.  I would like to do dual boot on this Dell, but I am not sure if this is possible.  If not, what is the best way to wipe the HD of Windows for installing Ubuntu?  Can I still keep Word, Excel, PowerPoint on Ubuntu?

I have seen a some people have had issues installing Ubuntu with this particular Dell.  I was wondering if it would be better to consider using an older Ubuntu version? 

Any advice or help is appreciated.

---

### Post by cortman on 2012-07-28
> **pcfast said:**
> Hello Everyone,

I have a Dell Dimension 2350 that I would like to install Linux on.  I have no experience with Linux or messing around with computers too much.   

Dell Dimension 2350 Specs: 
256MB of RAM
2GHZ Intel Celeron 
Windows XP

[http://support.dell.com/support/edocs/systems/dim2350/specs.htm](http://support.dell.com/support/edocs/systems/dim2350/specs.htm)

The HD has about 10GB being used out of 60GB.  I would like to do dual boot on this Dell, but I am not sure if this is possible.  If not, what is the best way to wipe the HD of Windows for installing Ubuntu?  Can I still keep Word, Excel, PowerPoint on Ubuntu?

I have seen a some people have had issues installing Ubuntu with this particular Dell.  I was wondering if it would be better to consider using an older Ubuntu version? 

Any advice or help is appreciated.

Windows programs will not run in Ubuntu, with a few exceptions. Office very likely will not. Ubuntu comes with a free alternative- LibreOffice- which is every bit as good IMHO.
Installing a dual boot is very easy. BUT- before you do anything:

**[SIZE=4]Back up your data.[/SIZE]**

I can't stress this enough- unless you are able to back up, you should not try to install Ubuntu.
First you should go into Windows and resize the partition- DON'T resize a Windows partition with Ubuntu- WIndows is very finicky about this. The tools to do this are in the Control Panel>Computer Management or something like that- a quick Google search will find you instructions on that.
When the partition is resized, boot from the Ubuntu disk and tell the installer to install "alongside" Windows XP. If you don't get this "install alongside" option, something isn't holding out; abort the installer and report back.
Good luck!

---

### Post by afixane on 2012-07-28
> **pcfast said:**
> Hello Everyone,

I have a Dell Dimension 2350 that I would like to install Linux on.  I have no experience with Linux or messing around with computers too much.   

Dell Dimension 2350 Specs: 
256MB of RAM
2GHZ Intel Celeron 
Windows XP

[http://support.dell.com/support/edocs/systems/dim2350/specs.htm](http://support.dell.com/support/edocs/systems/dim2350/specs.htm)

The HD has about 10GB being used out of 60GB.  I would like to do dual boot on this Dell, but I am not sure if this is possible.  If not, what is the best way to wipe the HD of Windows for installing Ubuntu?  Can I still keep Word, Excel, PowerPoint on Ubuntu?

I have seen a some people have had issues installing Ubuntu with this particular Dell.  I was wondering if it would be better to consider using an older Ubuntu version? 

Any advice or help is appreciated.

With your "tiny" RAM memory, IMO, it's better to don't install Ubuntu. Ubuntu require ~512 MB to run and ~1 GB for optimal experience. It's better to install Bodhi Linux (which based on Ubuntu) or Lubuntu.

---

### Post by pcfast on 2012-07-28
The computer was given to me and does not have any files that I care about.  So I don't need to worry about getting files off of it or backing it up really.  Perfect for playing around with a new OS in my opinion! 

I don't have MS Office on my current laptop (windows) and sort of refuse to buy it.  (I guess I don't like giving MS money!)  Having Word would be useful for when people send me files.  I usually will just use GoogleDocs now but sometimes that can be limiting for sending people files when they don't have a Google account. 

Can I dual boot Lubuntu or Bodhi Linux?  I was just reading about LinuxMint, could I make that run on this Dell?

---

### Post by pcfast on 2012-07-28
What about PuppyLinux?

---

### Post by cortman on 2012-07-28
Puppy is good.

I didn't pay attention to your RAM; you definitely want a lighter system than straight Ubuntu. I use Bodhi Linux on my netbook about every day and it's one of my favorite OS's- looks absolutely fantastic and is super lightweight. Definitely give Bodhi a whirl- they have a great support community as well.
Bodhi doesn't come with any programs beyond a web browser, text editor, and terminal- so you'll be able to put exactly what you want on it.

---

### Post by Kelvari on 2012-07-29
+1 for Lubuntu. I've got it running on an older system myself, and it seems pretty snappy.

As far as office suites go, you might be satisfied with LibreOffice ([http://www.libreoffice.org/](http://www.libreoffice.org/)). It's a free full office suite, forked off of OpenOffice.org back when Oracle bought out Sun.

It should be able to handle most day-to-day situations where you'd find yourself using MS Office, with a nice price tag (free).

Edit: I would also recommend throwing some more RAM in there if you can get your hands on there. There's no such thing as 'too much' RAM, so long as the computer still boots.

---

### Post by TheMTtakeover on 2012-07-29
> **pcfast said:**
> Hello Everyone,

I have a Dell Dimension 2350 that I would like to install Linux on.  I have no experience with Linux or messing around with computers too much.   

Dell Dimension 2350 Specs: 
256MB of RAM
2GHZ Intel Celeron 
Windows XP

[http://support.dell.com/support/edocs/systems/dim2350/specs.htm]("http://support.dell.com/support/edocs/systems/dim2350/specs.htm")

The HD has about 10GB being used out of 60GB.  I would like to do dual boot on this Dell, but I am not sure if this is possible.  If not, what is the best way to wipe the HD of Windows for installing Ubuntu?  Can I still keep Word, Excel, PowerPoint on Ubuntu?

I have seen a some people have had issues installing Ubuntu with this particular Dell.  I was wondering if it would be better to consider using an older Ubuntu version? 

Any advice or help is appreciated.

I'm gonna agree with everyone else and say Ubuntu is a no go with that amount of RAM. I've had good experiences with puppy linux on older dells.

---

### Post by mastablasta on 2012-07-29
there is libre office available. older versions of MS office work with wine. 

install in side by side dual boot is is preety much straight forward. you need to cretae an emtpy unformatted partition and during install just say to install to install into largest empy disk space. if you plan to format. it's even easier. just tell it to overwrite the disk.

you can test is firts using live CD/USB and boto form it and choose try it on boot screen. it will take long time to load since all OS loads into ram. also it won't work as fast as install (especially since you have low ram) but it gives you some idea what to expect.

a few easy to use and install light distributions :
Lubuntu
Bodhi linux
peppermint OS
mint LXDE
chrunchbang (based on debian stable)
puppy linux
slitaz

---

### Post by afixane on 2012-07-29
> **pcfast said:**
> The computer was given to me and does not have any files that I care about.  So I don't need to worry about getting files off of it or backing it up really.  Perfect for playing around with a new OS in my opinion! 

I don't have MS Office on my current laptop (windows) and sort of refuse to buy it.  (I guess I don't like giving MS money!)  Having Word would be useful for when people send me files.  I usually will just use GoogleDocs now but sometimes that can be limiting for sending people files when they don't have a Google account. 

Can I dual boot Lubuntu or Bodhi Linux?  I was just reading about LinuxMint, could I make that run on this Dell?

Bodhi And Lubuntu can dualboot too. It's basic feature on all Linux.

---

### Post by pcfast on 2012-07-29
> **mastablasta said:**
> a few easy to use and install light distributions :
Lubuntu
Bodhi linux
peppermint OS
mint LXDE
chrunchbang (based on debian stable)
puppy linux
slitaz

Thanks I will read up and look into these Linux versions and figure out what is best.  So many to choose from it's almost hard to decide! 

> **afixane said:**
> Bodhi And Lubuntu can dualboot too. It's basic feature on all Linux.

I was mainly wondering if it was feasible on this Dell?  Seems like the best thing to would be to just run 1 Linux Distribution on it?

---

### Post by waynefoutz on 2012-07-29
> **pcfast said:**
> Thanks I will read up and look into these Linux versions and figure out what is best.  So many to choose from it's almost hard to decide! 



I was mainly wondering if it was feasible on this Dell?  Seems like the best thing to would be to just run 1 Linux Distribution on it?

I think he meant dual-booting with Windows. 

I put my vote in for Bohdi. Either that or Lubuntu. Bohdi is a lot prettier and more fun to use.

---

### Post by levlaz on 2012-07-29
> **pcfast said:**
> Thanks I will read up and look into these Linux versions and figure out what is best.  So many to choose from it's almost hard to decide! 



I was mainly wondering if it was feasible on this Dell?  Seems like the best thing to would be to just run 1 Linux Distribution on it?

You can certainly dual boot, it will have no effect on the speed of the computer since by creating a new partition in the hard drive you essentially segregate windows and Linux - the only limitation will be the amount of Disk Space you have left (since you said XP was already using 10GB). Other then that dual booting will have no other effect on the speed or performance of the computer since you are not going to be running both OS's at the same time. 

I think that you should try Lubuntu - it is a great distribution which is very easy to install and will give you a good representation of a modern GNU/Linux setup. The other distros mentioned are great choices as well, but I think Lubuntu is very well polished. 

I would stay away from Puppy - although it runs quick on pretty much anything you put it on, I do not think it is for beginners - some things can get a little hairy once you start playing with it. 

But since this is not your main PC it does not really matter, install all of them (individually) if you feel like it -- that way you can see the differences and learn something new. 

As far as an office suite for your other computer, definitely look at LibreOffice I have been using it for years (before that OpenOffice) in the educational, business, and personal setting with no major compatibility issues. I have been able to accomplish every task that I have had with this fantastic piece of software.

---

### Post by pcfast on 2012-07-29
I have actually been using OpenOffice for a few years now..  It took some getting used to but now I like it.  

OpenOffice should work on most Linux Distros?

---

### Post by waynefoutz on 2012-07-29
> **pcfast said:**
> I have actually been using OpenOffice for a few years now..  It took some getting used to but now I like it.  

OpenOffice should work on most Linux Distros?

most of them have moved over to LibreOffice, which is a fork of OpenOffice. They are almost identical.

---

### Post by levlaz on 2012-07-29
> **pcfast said:**
> I have actually been using OpenOffice for a few years now..  It took some getting used to but now I like it.  

OpenOffice should work on most Linux Distros?

Yes it should, but it is a pretty big program that may use up all of your RAM. For a lighter alternative check out [Abiword]("http://abiword.com/") for word processing and [Gnumeric]("http://projects.gnome.org/gnumeric/") for spreadsheets.

---

### Post by pcfast on 2012-07-29
> **waynefoutz said:**
> most of them have moved over to LibreOffice, which is a fork of OpenOffice. They are almost identical.

Does that mean OpenOffice files are compatible with LibreOffice?

---

### Post by levlaz on 2012-07-29
> **pcfast said:**
> Does that mean OpenOffice files are compatible with LibreOffice?

Yes all of the files are compatible, same goes for Abiword and Gnumeric -- thats the beauty of[ open standards]("http://en.wikipedia.org/wiki/OpenDocument") it does not matter what you use it all works and looks the same.

---

### Post by critin on 2012-07-30
> **levlaz said:**
> 
I would stay away from Puppy - although it runs quick on pretty much anything you put it on, I do not think it is for beginners - some things can get a little hairy once you start playing with it. 



I agree.  Puppy isn't a simple system for beginners--it's just tiny.  Users need to know more than with other systems.

---

### Post by mastablasta on 2012-07-30
> **pcfast said:**
> Does that mean OpenOffice files are compatible with LibreOffice?
 
Libre Office is basicall Openoffice with some bugs fixed and soem new features added. It was forked, because the development on Openoffice stalled due to Oracle's policy.
 
edit: that's correct, Puppy is ment to be used live, and has a bit more complicated hard disk install.

---

### Post by reinisvs on 2012-07-30
> **pcfast said:**
> What about PuppyLinux?

PuppyLinux is an excellent Distro, I manged to get an ancient thinkpad working very smoothly (until the HD failed)

---

### Post by pcfast on 2012-07-30
> **levlaz said:**
> Yes all of the files are compatible, same goes for Abiword and Gnumeric -- thats the beauty of[ open standards]("http://en.wikipedia.org/wiki/OpenDocument") it does not matter what you use it all works and looks the same.

Open source rocks!

---

### Post by pcfast on 2012-08-12
I burned a Disc with Bodhi, but can't get Dell to boot off it.  Is there a way to check whether the files downloaded correctly and burned correctly?

---

### Post by pcfast on 2012-08-12
Here is what happens, I press F12 then select to boot from the Disc, it then goes to a black screen, then the Windows XP loads from the HD.  

Can anyone tell me what I am doing wrong or what I need to do?

-Thanks

---

### Post by Terl on 2012-08-12
Are you burning the disk as an image or as a set of files?  You need to burn the discs at a slow speed as an image.

---

### Post by pcfast on 2012-08-12
Yes I did it as an Image.  I also did a slow burn.

---

### Post by MoebusNet on 2012-08-12
One of the issues I've run into is that the default video card driver for Ubuntu 12.04 as well as other recent Linux distros doesn't support my antique Geforce4 4200 Go video card. To make things more interesting, Nvidia dropped support for their proprietary nvidia-96 driver for Ubuntu 12.04 & Linux. This isn't really a Linux issue, the video card manufacturers just are not very accomodating as far as releasing info to support their video cards.

Without knowing your video card, you may just have to try several different Linux distros - including some older ones like Ubuntu 11.10 or 11.04 to find support for your video card if that is an issue. That may be a reason you are not booting from Live-CD. 

Live-CD or Live-USB is your friend. I would attempt to make sure my hardware will boot the Live version before I attempt an install.

Once you find a Linux distro that will boot a Live-CD, then you can decide what works for you and what you want to install.

Of course take my advice as with all others with a grain of salt; YMMV.

---

### Post by pcfast on 2012-08-14
I don't think this old Dell can read DVD's.  I guess I will try installing with a USB drive.

---

### Post by MoebusNet on 2012-08-14
My 2002 Dell Latitude D800 notebook can read & write CD's but DVD's are read-only unless I use an external DVD burner. I had to update to a newer version of the BIOS to be able to boot from USB; the factory-supplied BIOS wasn't able to do that.

That may be an issue you'll run into.

---

### Post by tartalo on 2012-08-14
If you are going to test a lot of different Live distros from a pendrive, you might find this useful:

[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by ads2996 on 2012-08-14
1. Backup all ur data
2. Use Gparted to shrink ur c drive giving about 10-20gb of unallocated space.
3. Create an extended partation. Of 1gb swap and the rest ext4.
4. install ubuntu using advanced partation settings.
5. select the ext4 partation to install on.

---

### Post by Jay MC on 2012-08-14
If you're in the market for a lightweight Linux distro, Crunchbang might also be worth a look.  It's a really nice lightweight distro.  I can't say I've personally tried it with that amount of RAM, but I've heard it works fine.

---

