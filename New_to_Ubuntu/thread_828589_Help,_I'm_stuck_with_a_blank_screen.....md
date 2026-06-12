---
title: "Help, I'm stuck with a blank screen...."
date: 2008-06-13
forum: New to Ubuntu
---

### Post by jkkmmck on 2008-06-13
I'm really going to have to rely on the kind souls here to help me to get to a working computer, hope someone takes pity on me!
Here's my story: I'm a long time Mac user who has never owned a piece of PC hardware, and has spent about ten minutes time total in front of Windows over the last 20 years. I'm very unfamiliar with PC hardware, but I really wanted to give Ubuntu a try, so I bought a used Thinkcentre and an older Dell LCD monitor (with VGA hookup only). 40 GB hard drive, 2.8 Ghz P4, 256 mb of ram, integrated graphics.
I plugged everything in and found that it booted up to Windows XP just fine, got on my home network and got on the internet. That being enough of Windows for me, I burned an Ubuntu Live CD on my Mac, then tried to boot the PC from it, but the installer told me I didn't have enough ram to do that. So I burned the "alternate" text based installer CD and somehow managed to figure out how to get the PC to boot up to the BIOS screen, start up from the CD, and after a while I actually got Hardy Heron running seemingly perfectly well on this old machine. I did notice that performance seemed sluggish, with lots of window artifacts and stuff. I opened up some programs, ran the set of software updates that Ubuntu wanted me to run, and shut down feeling pretty good about the whole thing.
In the morning, however, I got no video when I turned the machine back on. I did eventually get the strange bongo sound I had heard on startup the night before, and which I take to be the Ubuntu "welcome" chime. But, after a few white streaks of light across the monitor,it was nothing but pitch black. I tried booting up to the BIOS screen again and did get the horrible beeps, but no video. I switched out monitor and cable -- no dice. The other monitor is new enough that it sends a little square graphic bouncing around the screen that says something like "I'm not getting any signal."

So, I think the machine is still alive, but it doesn't seem to be sending out a video signal. I'm comfortable with the terminal on the Mac, but I somehow don't think on my DHCP home network I'm going to be able to telnet in to the PC to see if it's alive, or what the problem is. 

So I turn to you for suggestions about what I might try next.

Thanks for your time!

---

### Post by ibuclaw on 2008-06-13
Boot up the PC, when GRUB loads. Hold down the Escape button and a boot menu should show.

Select the "**Ubuntu Recovery Mode**" option. Then select "**Fix X**" Option in the Recovery Menu.

Once that has finished, choose the option to continue into Normal Boot. and fingers crossed. X should be back and working again.

Regards
Iain

---

### Post by jkkmmck on 2008-06-14
Many thanks. That worked! It turns out the first, used monitor is crapping out. The second monitor I attached to it just wasn't showing up for some reason, until I booted up holding the escape key. Not sure why this worked, but thanks again, and I can't wait for my *Ubuntu for Non-Geeks* to arrive!

---

### Post by ibuclaw on 2008-06-14
Lol... That **IS** the "Non-Geek" way to fix X, by the way... :)
Else I would of asked you to edit your "**/etc/X11/xorg.conf**" file!!! :lolflag:
Regards
Iain

[EDIT]
Oh! You mean the book... :-s

Not that I want to discourage you from it, because there **WILL** be alot of useful information in it.
But I find that the online documentation is far superior nowadays, and is constantly being updated with the times...

---

