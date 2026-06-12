---
title: "Which OS to run on these servers?"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by thebigguyconnor on 2011-11-28
I've got a couple of boxes (old off-lease type dell optiplex boxes,  basic system specs, etc) that I'd like to use as home servers, running  either windows or linux, and I'd like to know what you guys would  recommend.  I am going to run the servers headless most of the time, so  I'd actually prefer that the OS I install not have pretty graphics,  because it would just take up pointless resources.
 
 I *would* like the option of going into a GUI when I need to hook  up a head because I am not totally comfortable with the CLI just yet  (especially on linux).
 
 ** Ok here's the two machines:**
 
 * Dell OptiPlex GX240 Tower*
 
 AGP Matrox Dual Head VGA Adapter
 4 or 5 PCI Slots, can't remember
 4 USB ports total (USB 1.1)
 100 MBPS Fast Ethernet
 40 GB IDE HDD
 1 GB PC133 RAM
 Pentium 4 - 1.8 GHz
 
 * Dell OptiPlex GX270 Small Form Factor PC (for its time - 2003)*
 
 Integrated VGA
 PCI Slot, and AGP 8X Slot, both unused (also they're both half-height expansion slots)
 8 USB ports total (USB 2.0)
 Gigabit Ethernet
 20 GB IDE HDD
 256 MB DDR RAM (may be able to 
 Pentium 4 - 2.4 GHz
 
 ** Here is what I'd like to run on these two:**
 
 *** Web Server*** (Apache or lighttpd)
 *** FTP File Server* **(FileZilla Server if on windows, I don't know which sort of FTP servers Linux has)
 *** Windows-Capable Networked Print Server*** (Both computers have  Parallel Ports to work with my ancient 1990s era LaserJet 4P, want a  print server that works with windows PCs, not just unix/linux)
 *** SSL Server* **(if it's a linux box, but if it's windows then I'll use RDP)
 *** Proxy Server*** (on windows I'd use Proxify, thru Hamachi, don't know of a linux alternative)
 *** Hamachi Server*** (I know how to set this up already on both)
 *** Video Game Server for a couple games*** (It wouldn't always be  running but easy to launch - I know how to set this up on both windows  and linux, but want to know which services I should run on which PCs  based on their specs)
 ***Music Server*** (don't know how to set this up - was hoping to learn  how and which software to use to accomplish that task - want to share  music from one hard drive to whole family so they can sync it to their  MP3 Players, etc)
 
 [SIZE=4]TL;DR:[/SIZE]
 
 I want to know your recommendations on **which above services in the list to assign to which computer**, and **which OS to run on each computer**  based on their specs.  Right now I'm leaning towards running Windows XP  on the first one and some sort of Linux for the second one.
 
 Hoping for some help,
 
 Connor McBrine-Ellis
 
 Thanks!

---

### Post by Corporation on 2011-11-28
I'm a fan of Gentoo Linux or OpenBSD on servers, would run fine on both of these.

Edit: Due to need for game servers, I'd err towards Gentoo as many blobs aren't compiled for BSD.

---

### Post by thebigguyconnor on 2011-11-28
> **Corporation said:**
> I'm a fan of Gentoo Linux or OpenBSD on servers, would run fine on both of these.

Edit: Due to need for game servers, I'd err towards Gentoo as many blobs aren't compiled for BSD.
Ok, thx.

I've heard good things about Gentoo.  Which package manager does it use, and how hard is it in every day basic use?  I've used APT and PACMAN in the past, but I wouldn't really have much of a problem learning another one, I guess.

Is Debian as good as Gentoo.  I was thinking of just going with Debian since it's most similar to Ubuntu which I'm used to,

Also, still wondering about the printer.  How do I set up a print server that works on windows XP/7 using the linux command line?

Thanks for any and all advice.

---

