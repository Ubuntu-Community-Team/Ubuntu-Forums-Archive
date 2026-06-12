---
title: "Graphics Resolution 640x480 only reconized Lubuntu 14.10 on dell inspiron 1100"
date: 2015-01-01
forum: New to Ubuntu
---

### Post by Christopher_Brown on 2015-01-01
Hey, I'm a completely new user of Linux, and having a very old laptop, specifically a Dell Inspiron 1100 that refused to run with Windows, i decided to go with linux, and naturally got Lubuntu 14.10, seeing as it's a distro of Linux designed for older systems. However, once i installed it, it would only run in 640x480 resolution, using only the top left corner of the screen. I've tried everything i can think of and find to get Lubuntu 14.10 to recognize different resolutions, but nothing is working. CAN ANYONE HELP ME FIX THIS PROBLEM??????????????PLEASE??????????????????

---

### Post by sudodus on 2015-01-01
Welcome to the Ubuntu Forums :-)

Please specify your computer

- Brand name and model (OK)
- CPU ?
- RAM (size) ?
- graphics chip/card ?
- wifi chip/card ?

it makes it possible to give relevant advice (I find several specifications for that model via the internet).

But it is an old computer, that might have problems running a current Lubuntu version. I think it might be worthwhile to try

- ***Lubuntu 14.04.1 LTS*** (long time support) and UXA acceleration if you have Intel graphics. See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Graphics_chip_.2BAC8_card](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Graphics_chip_.2BAC8_card)

or a light-weight community re-spin based on Ubuntu 12.04 LTS: ***Bento***, ***Bodhi*** or ***LXLE***

If still problems, please try an ultra-light linux distro, for example ***Wary Puppy*** or ***Tiny Core***.

See also this link : [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by Christopher_Brown on 2015-01-01
it's a dell inspiron 1100, 512 megs ram, only ethernet chip, and standard intel graphics chipset, and intel celeron 2.0ghz processor

---

### Post by sudodus on 2015-01-01
Good :-)

It is near the low limit of what works with Lubuntu, but should be possible. I suggest that you try UXA acceleration. It works for me with version 14.04 LTS in an old IBM ThinkCentre. I don't know about 14.10.

Also, 14.10 has only 9 months of support, while Lubuntu 14.04 has 3 years, until April 2017. So the advice in my previous post might work.

---

### Post by Christopher_Brown on 2015-01-01
so ho do i get uxa acceleration for my inspiron on lubuntu?

---

### Post by sudodus on 2015-01-01
Do it according to this link

[https://wiki.ubuntu.com/Lubuntu/Adva...ip_.2BAC8_card]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Graphics_chip_.2BAC8_card")

---

### Post by Christopher_Brown on 2015-01-01
UXA acceleration isn't working at all. what do i do? someone else told me it's just a bug in 14.10, and told me to downgrade to 14.04..since UXA acceleration isn't working, should i jsut try that?

---

### Post by sudodus on 2015-01-01
1. You can't downgrade, instead you get the 14.04.1 LTS Lubuntu 32-bit iso file and make a new installation. There you might have better luck with UXA.

2. If still no go, try one of the re-spins based on 12.04 LTS. See post #2. You find download links or torrent files at the websites of Bento, Bodhi and LXLE.

3. If still no go, try Wary Puppy and Tiny Core ...

---

### Post by mörgæs on 2015-01-02
Let's see the graphics card in details. Please run ```
lspci -nnk | grep -iA2 vga
``` and post the results in CODE tags.

---

### Post by DuckHook on 2015-01-03
I am familiar with this ugly little beast. Actually, I'm not being fair. It was tidy enough in its day, but at 7.5 lbs, it was like carrying around a brick, and in terms of horsepower, I'm afraid that the DE lifecycle has long since passed it by.

I agree with Sudodus: it's either Lubuntu 14.04 for this beastie or one of the super lightweight distros. I'm surprised you have 512 MB in it. You must have maxed out the RAM at some point. However, as you've discovered, it's the video subsystem that will be your choke-point. I finally sent mine to the big computer lab in the sky when it wouldn't even boot into BIOS, but if memory serves me, it had at most XGA graphics. Even native resolution won't improve it much from the VGA you've got now.

If I may be so bold, you may be better off installing a command-line on the thing and using it as a combo file/print/media/torrent server. It has USB 2.0, so attaching a cheap 1 TB USB drive to it should give you sufficient throughput to stream video or music. It would also act as a nice little backup server with rsync running as a daemon. You wouldn't even have to look at the screen if you ssh into it to do all of your configuration and maintenance. And if you are the type that goes in for such things, it would act as a perfectly adequate SOHO web server, mail server, secure gateway, TOR node, etc, but I realize that I'm now getting into serious Geek territory. What I'm trying to say is that sometimes it makes more sense to reposition old HW for uses that are easy to implement and within its power rather than wrestling with the thing for days only to be disappointed with the inevitable sluggishness and limitations of a machine no longer capable of providing a good laptop experience on modern graphical OSes. So rather than trying to make an old geezer lift pianos, consider putting him to work making fine furniture, if you get my drift.

---

### Post by Mike_Walsh on 2015-01-03
Hello, Christopher.

Welcome to the Forums.

I, too, possess one of these 'beasties', as DuckHook puts it. Had it 12 years, now. It's definitely no lightweight; 7.5 lbs is about right.....it's the type of thing those 'back-pack' laptop carriers were developed for.....'cos it'll put your shoulder joint out trying to carry it around for too long!! Most of the weight comes from that huge battery pack, because you'll find that YOUR machine is actually running a full desktop CPU; the 'mobile', low-power CPUs hadn't got off the ground in those days. It's got to provide the same power that would normally be supplied by a mains PSU (somewhere in the region of 16-18 volts).

That's the very reason it produces all that heat...!

It originally came with XP (used to run like molasses), a 2.2 GHz Celeron, 128 MB RAM, and a 20 GB hard drive. I've tweaked it somewhat over the years; maxed out the RAM to 1 GB; upgraded the Celeron to a 2.6 GHz P4, hard drive is now 40 GB.

sudodus is absolutely right about the Puppies. I tried Lubuntu 14.04 on it when I switched from XP last year, and had exactly the same problem you've got.....and nobody on here was able to help with it. So instead of trying to fix it, I looked around for a distro that WOULD work; and in early November, I found it. Puppy Linux 'Tahrpup' 6.0. Works perfectly, without ANY tweaking. If you're interested, you can get it from here:-

[http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/)

You'll need the 5th entry down; tahr-6.0-CE_PAE.iso. Download, burn, and boot in the normal way. It'll definitely fit on a CD; you won't need a DVD.

You can try it from a live session; you can then install, either to hard drive (not usual with the Puppies, but it's what I've done) or to flash drive (which is what the Puppies were originally designed for, and what most people use). Works a treat, too. It actually uses a more up-to-date kernel than the 'buntu 14.04 releases; 3.14, as opposed to 3.13.....could be the reason why the graphics are behaving themselves.

If you're wanting a wireless adapter for the Dell, this DOES work on the 1100:-

[http://uk.tp-link.com/products/details/?categoryid=243&model=TL-WN725N](http://uk.tp-link.com/products/details/?categoryid=243&model=TL-WN725N)

I'm using the TP-Link right this moment. Puppy will tell you which kernel module you need for it, and then install it for you. Only snag is, you have to manually re-start it every time...

Hope that helps. The 1100s are rarer than hen's teeth these days, but I'm always happy to help folk out with advice regarding them...I've had a wee bit of experience! But please remember; although the Puppies DO run fast, since they run entirely in RAM, DON'T expect fast performance; this is ancient 'tech' we're talking about here. It won't be quick, but it WILL do everything you want it to do.....as long as you're not a gamer, or into video editing, or stuff like that. If you browse the web, word process, do e-mails, play music, or edit photos, it'll work fine. ;)

It'll do everything XP used to do.....and it'll do it faster. If you want any help with it, just ask. Or try the Puppy Forums:-

[http://www.murga-linux.com/puppy/index.php?sid=c804c36020d273e83b2552666886fafd](http://www.murga-linux.com/puppy/index.php?sid=c804c36020d273e83b2552666886fafd)


Regards,

Mike.

---

### Post by Mike_Walsh on 2015-01-03
> **sudodus said:**
> Do it according to this link

[https://wiki.ubuntu.com/Lubuntu/Adva...ip_.2BAC8_card]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Graphics_chip_.2BAC8_card")

@sudodus:-

Just thought I'd let you know, for future reference. I've just created an xorg.conf file, and tried this in Lubuntu 14.04 LTS (32-bit); it doesn't work there, either.

So I'll stick with 'Tahrpup' on the Dell, I think. It all works perfectly.

I'm more than happy with it, actually; it interacts very nicely with Ubuntu 14.04.1 LTS on my big Compaq desktop, with regard to network printing, and file-sharing via SAMBA, so.....that'll do me! And she's definitely got more 'horsepower' since upgrading the 'Celery-stick' to the P4.

Thanks for the tip, though; it was certainly worth a try.

Cheers! ;)


Regards,

Mike.

---

### Post by sudodus on 2015-01-03
I'm glad to read that not only the old (but updated) Wary Puppy, but also the more modern ***Tahrpup*** works well with really old hardware.

UXA acceleration helps with my old Intel graphics, but obviously it does not help with the graphics in the old Dell Inspiron 1100.

Thanks for sharing your results :-)

---

### Post by Mike_Walsh on 2015-01-03
> **sudodus said:**
> I'm glad to read that not only the old (but updated) Wary Puppy, but also the more modern ***Tahrpup*** works well with really old hardware.

UXA acceleration helps with my old Intel graphics, but obviously it does not help with the graphics in the old Dell Inspiron 1100.

Thanks for sharing your results :-)

Well, I can confirm that Tahrpup definitely works with MY 1100, in its present configuration:-

Pentium 4 @2.6 Ghz
1 GB RAM
40 GB Hitachi 'TravelStar' HDD
Intel 'Extreme' graphics 82845 G/GL/GE/PE/GV graphics adapter.

Interestingly, when I had her stripped down for the P4 upgrade about a month ago, I took the opportunity to examine the graphics adapter more closely. It's a curious set-up. I know it's described as 'integrated' graphics, but upon closer examination it looks like a small daughter-board built on top of the motherboard, with the card itself PLUGGED into it...because you CAN remove it. However, the display cable plugs into the lower portion of this set-up, the daughter-board; so I don't quite know what this means for being able to replace it...

However, the OP said he tried it with 14.10.....and THAT has the 3.16 kernel; so maybe it's something the Puppy devs have done...I can't say. Whatever it is, it WORKS.

Dell themselves are less than forthcoming about ANY of their hardware, never mind stuff as old as this!

Regards,

Mike. ;)

---

