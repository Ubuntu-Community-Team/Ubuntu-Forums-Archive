---
title: "Boot Puppy Linux on Dell 1501"
date: 2008-12-03
forum: Other OS Talk
---

### Post by jpittack on 2008-12-03
I could use some help.  I just got a nice 8 GB flash drive (overkill) from Black Friday sales.  I was going to use DSL, but decided to try Puppy instead.  So far I like the default layout of Puppy better, but I can't get it to boot from my flash drive.  Heres all the problems I have had.

I have never gotten anything to boot from a usb flash drive before (on anything), and this is my first attempt on this laptop.  The BIOS does give the option.  There are two that might work.  USB storage and removable devices (SD card mabye?).  Both have a higher priority then the hard drive.

When I boot, the CD version will work, so long as I specify no acpi.  I have tried adding the nesscary lines to grub, but I know that I am doing that wrong.  The relevant lines from menu.lst

```
title		Puppy Linux
root		(sdb1,0)
kernel		/media/disk/vmlinuz
initrd		/media/disk/initrd.gz
```

I am mainly interested in using an OS from RAM.  I don't consider myself knowledgeable enough to try running Ubuntu from RAM.  I've tried it once before and it didn't turn out well.  I am using the flash drive because I would like to be able to move from computer to computer with it.

Thanks for looking folks!

---

### Post by Cenotaph on 2008-12-03
I suggest you try unetbootin available at unetbootin.sourceforge.net

it's a pretty good tool that will set up everything for you, so unless you want to learn how to do it yourself or need a more advanced configuration, you should give it a try. 

It even has some presets you can use including configuration of puppy linux and damn small linux, not sure its the latest versions of them, though. But you can use CD images and other options to create the bootable flash drive also, if you want.

its a good way to install ubuntu too, that's how ive been using it anyway ;)

---

### Post by jpittack on 2008-12-04
unetbootin works when I used the flash drive on my roommates laptop.  It will not boot from my laptop.  I have tried adding the mbr stuff.  I think that is supposed to add a floppy drive to the flash drive and use that to boot.  The laptop doesn't have a floppy drive, thus the BIOS doesn't boot from one.  Any other thoughts?

---

### Post by spcwingo on 2008-12-09
If it has a floppy try installing grub to a floppy and booting from it to the flash drive.  If I recall correctly the option to do that is under setup in the menu.

---

### Post by tuvw610 on 2008-12-09
We at [www.inwowgold.com](www.inwowgold.com) understand that casual gamers cannot make a life out of playing WoW. Some people may have the luxury of time and money to do whatever they please every single day, but for most of us, we need to work and support ourselves and our families. This is where the best [wow power leveling](http://www.inwowgold.com/power-leveling/) services of [http://www.inwowgold.com](http://www.inwowgold.com) can help you out! You can experience [World of Warcraft](http://www.google.com/search?hl=en&q=site%3Awww.inwowgold.com+World+of+Warcraft&aq=o&oq=) today without having to worry about grinding levels or wasting time earning [wow gold](http://www.inwowgold.com). Purchase these [cheapest wow gold](http://www.inwowgold.com) services from us and play the game as a game, rather than as a second job. Our [wow fast power leveling](http://www.inwowgold.com/power-leveling/) services are completely legitimate, ensuring that only human players will ever play your character. Our leveling services can get you to your desired level, with your desired faction and money all for competitive and low prices.

---

