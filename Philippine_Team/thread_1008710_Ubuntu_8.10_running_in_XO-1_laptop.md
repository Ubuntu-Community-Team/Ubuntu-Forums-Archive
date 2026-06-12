---
title: "Ubuntu 8.10 running in XO-1 laptop"
date: 2008-12-11
forum: Philippine Team
---

### Post by jsgotangco on 2008-12-11
[IMG]http://farm4.static.flickr.com/3024/3099520492_b7f607f57f.jpg[/IMG]

Used a 4GB SDHC Class 6 card from CD-R King for P380. Laptop needs to have a developer key. The kernel is not stock Ubuntu but taken from the OLPC kernel so that the keybindings, camera and LCD functions will work. Since the laptop only has a measly 256MB of RAM, I created a swap file from the card of the same size. It's basically Xubuntu btw, just made it look more like GNOME which I'm more familiar with.

I blogged about this with more details at [http://engage.wordpress.com/2008/12/11/ubuntu-810-for-the-xo-1-laptop/](http://engage.wordpress.com/2008/12/11/ubuntu-810-for-the-xo-1-laptop/)

---

### Post by loell on 2008-12-11
ooh, looking pretty.. :)

but

> 
Kernel is from OLPC release 8.2.0. USB boot fix in ramdisk is the only change that was applied to OLPC-distributed files.

does this mean, you have to disable the update manager? so as to avoid ubuntu kernel updates?

---

### Post by jsgotangco on 2008-12-12
Nahh doesn't have to be. With some regex magic you can just avoid specific updates, say the kernel and stuff.

---

### Post by adredz on 2008-12-12
what a hellova touch pad! for Goliath? looks kiddy to me. it has a defense armor on its sides.:)

---

### Post by loell on 2008-12-12
> **adredz said:**
> looks kiddy to me. it has a defense armor on its sides.:)

well it wouldn't be an [educational laptop for children]("http://laptop.org/en/laptop/index.shtml") if it didn't look kiddy, you know.. ;)

---

### Post by jsgotangco on 2008-12-12
> **adredz said:**
> what a hellova touch pad! for Goliath? looks kiddy to me. it has a defense armor on its sides.:)

It is ruggedized by design and the touchpad is just in the middle. The sides are used for any stylus. The display itself has two modes, the colored one and a paper-white display similar to what e-ink devices use.

---

### Post by adredz on 2008-12-13
aw, at first glance kala ko touchpad lahat yan hehehe

---

### Post by jsgotangco on 2008-12-13
water resistant keyboard din yan ;-)

---

### Post by adredz on 2008-12-13
ows?hehehe. astig pala yan, pwede mong gamitin under the rain?:)

---

### Post by jsgotangco on 2008-12-13
Only the keyboard, not the display ;-)

---

### Post by nosillacast on 2009-01-17
I'm a noob with great faith so I've been following the instructions at [http://www.olpcnews.com/forum/index.php?topic=4053.0](http://www.olpcnews.com/forum/index.php?topic=4053.0) but I've hit a snag.

I believe I've got Ubuntu on the SD card via the thumb drive, and I did the whole developer key dance.  The issue is when I boot I get the error "sdhci card didn't power up after 1 second".  I've read threads with a theory that the cards are too big, so maybe partitioning an 8 GB card into two 4 GB partitions would help, but this is a stinkin' 2GB card to start with.

clues? helpful hints? tell me what to do?  Knightwise promised me you guys are gentle with noobs...I can help with OSX problems but not linux!

Allison
NosillaCast at [http://podfeet.com](http://podfeet.com)
A technology geek podcast with an EVER so slight Macintosh bias!

p.s. I've seen that updating to q2e24 helps but I can't get mine past q2d07.

---

### Post by wygee on 2009-01-18
> **adredz said:**
> ows?hehehe. astig pala yan, pwede mong gamitin under the rain?:)

pwede yan. just use an umbrella, ella, ella.. eh, eh. hehehe :lolflag:

---

### Post by jsgotangco on 2009-01-18
> **nosillacast said:**
> I'm a noob with great faith so I've been following the instructions at [http://www.olpcnews.com/forum/index.php?topic=4053.0](http://www.olpcnews.com/forum/index.php?topic=4053.0) but I've hit a snag.

I believe I've got Ubuntu on the SD card via the thumb drive, and I did the whole developer key dance.  The issue is when I boot I get the error "sdhci card didn't power up after 1 second".  I've read threads with a theory that the cards are too big, so maybe partitioning an 8 GB card into two 4 GB partitions would help, but this is a stinkin' 2GB card to start with.

clues? helpful hints? tell me what to do?  Knightwise promised me you guys are gentle with noobs...I can help with OSX problems but not linux!

Allison
NosillaCast at [http://podfeet.com](http://podfeet.com)
A technology geek podcast with an EVER so slight Macintosh bias!

p.s. I've seen that updating to q2e24 helps but I can't get mine past q2d07.

Some cards seem not to be able to power on from boot hence, even though you are able to write to the sd card, it still won't work. I've experienced it with brands like Sandisk (2GB) and Kingston (SDHC 4GB). This seems to happen with your card. You can confirm if it doesn't work at all with a warm reboot upon the first failure notice in Forth.

What I'm currently using now is a generic no-brand 4GB SDHC Class 6 and it works out of the box. I'm currently running Sugar Build 767 with firmware Q2E18. I suggest you install 767 first if you haven't yet and the firmware will update itself as well.

---

### Post by nosillacast on 2009-01-19
> **jsgotangco said:**
> Some cards seem not to be able to power on from boot hence, even though you are able to write to the sd card, it still won't work. I've experienced it with brands like Sandisk (2GB) and Kingston (SDHC 4GB). This seems to happen with your card. You can confirm if it doesn't work at all with a warm reboot upon the first failure notice in Forth.

What I'm currently using now is a generic no-brand 4GB SDHC Class 6 and it works out of the box. I'm currently running Sugar Build 767 with firmware Q2E18. I suggest you install 767 first if you haven't yet and the firmware will update itself as well.

hmmm...I just checked and it's actually a 4GB card, but it IS Sandisk.  so remember the noob part?  what does it mean to install 767?  is that a build number?  maybe a link on that?  and so I should buy a no-name brand SD card and I might have more success than Sandisk, how odd, but I believe you!

Allison
NosillaCast at [http://podfeet.com](http://podfeet.com)
A technology geek podcast with an EVER so slight Macintosh bias!

---

### Post by jsgotangco on 2009-01-19
I've tried it with 2 Sandisk cards and didn't get them to work at all, so I guess the logical choice is to try out another card (a 2GB will really suffice, but if you want to add more software, make sure to get at least 4GB).

When I said to update to build 767, I mean the default operating system of the XO laptop, the one running the Sugar interface. The detailed information about upgrading to build 767 can be read here: [http://wiki.laptop.org/go/Clean-install_procedure](http://wiki.laptop.org/go/Clean-install_procedure)

Post away in case you encounter difficulties!

---

### Post by nosillacast on 2009-01-28
> **jsgotangco said:**
> I've tried it with 2 Sandisk cards and didn't get them to work at all, so I guess the logical choice is to try out another card (a 2GB will really suffice, but if you want to add more software, make sure to get at least 4GB).

When I said to update to build 767, I mean the default operating system of the XO laptop, the one running the Sugar interface. The detailed information about upgrading to build 767 can be read here: [http://wiki.laptop.org/go/Clean-install_procedure](http://wiki.laptop.org/go/Clean-install_procedure)

Post away in case you encounter difficulties!

You were right Jerome, finally found a PNY 2GB SD card (wasn't SDHC in case that makes a diff) and the install worked!  It's working!

many thanks,
Allison
NosillaCast at [http://podfeet.com](http://podfeet.com)
A technology geek podcast with an EVER so slight Macintosh bias!

---

### Post by jsgotangco on 2009-01-29
Good to know that you were able to make it work!

OT: Allison - I didn't notice until I saw your signature, I'm actually subscribed to your podcast since last year. I'm also a mac user at work so it has been very helpful ;-) Thanks for what you've been doing!

---

### Post by nosillacast on 2009-01-30
> **jsgotangco said:**
> Good to know that you were able to make it work!

OT: Allison - I didn't notice until I saw your signature, I'm actually subscribed to your podcast since last year. I'm also a mac user at work so it has been very helpful ;-) Thanks for what you've been doing!

No WAY!  That's so awesome!  this world is getting smaller every day!

hey, since you didn't mock my earlier questions - can I ask a Dumb Question?  This version of Ubuntu doesn't appear to have a GUI-based sleep or hibernate or anything like that. I've been closing the lid, it makes a lovely chime.  I thought it was sleeping but every once in a while it makes the chime again so I suspect not.  Is there a sleep?  Or do I have to shut down with the command line?

thanks again for the  help,

Allison
NosillaCast at [http://podfeet.com](http://podfeet.com)
A technology geek podcast with an EVER so slight Macintosh bias!

---

### Post by creek23 on 2009-01-31
Kuya Jerome! Wow!

I chatted with Naz last week and he told me he's hacking his XO-1 to have Xubuntu as well. It's nice that you two are pulling stuff from the impossible. ;)

He was going to lend me Michael Angelo to me but I rather not -- you need them best in Manila to gain more OLPC PH volunteers.

---

### Post by jsgotangco on 2009-02-01
Thanks! We actually had a meeting yesterday at my office and how we're going to make this work for this year. You can check out the replay at [http://www.ustream.tv/recorded/1109274](http://www.ustream.tv/recorded/1109274)

---

### Post by jsgotangco on 2009-02-01
> **nosillacast said:**
> 
hey, since you didn't mock my earlier questions - can I ask a Dumb Question?  This version of Ubuntu doesn't appear to have a GUI-based sleep or hibernate or anything like that. I've been closing the lid, it makes a lovely chime.  I thought it was sleeping but every once in a while it makes the chime again so I suspect not.  Is there a sleep?  Or do I have to shut down with the command line?


I believe that this implementation, even though it uses the OLPC kernel, does not make much use of the aggressive power management modes in Sugar, hence it does not do hibernate/suspend. What I do is shutdown from the menu to turn it off, or you could probably do ```
sudo shutdown -h now
``` from the terminal.

The release is a great mashup of Ubuntu and OLPC kernel, but its not full featured which is understandable, given the limited resources the XO-1 machine has.

---

