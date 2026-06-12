---
title: "If I switch to PCLinuxOS, what will be different from ubuntu?"
date: 2008-01-09
forum: Other OS Talk
---

### Post by Romanus81 on 2008-01-09
I just installed PCLinuxOS's Minime 2008 distro. I love it, mainly because it fixed a lot of annoying hardware related bugs I couldn't find a fix for in ubuntu (my pc wouldn't shut down, could never get the boot loader to work, etc.) 
My only question is that is PCLinuxOS too different from Ubuntu that I can't use Ubuntu howto's? Can I still add Ubuntu repo's to PCLinuxOS? What will I need to get used to, other than KDE?

---

### Post by savagenator on 2008-01-09
on the lowdown i think its the same, it won't have exactly the same problems and it might be setup differently in some areas, but everything else should be the same. When I used SUSE i found that a few things (like fstab) were completely different, but otherwise i could use and debug it normally.

---

### Post by SunnyRabbiera on 2008-01-09
well firstly, pclinux is rpm based not debian based so your ubuntu installer packages wont work.
also there is the matter that Pclinux has a smaller library then ubuntu.
if you are wet under the nose you may want to give mandriva 2008 a shot instead

---

### Post by original_jamingrit on 2008-01-09
It shouldn't be that much different.  It's just that when you follow ubuntu howtos, you just have to avoid downloading debs, and replace sudo apt-get with sudo <insert appropriate command>.

---

### Post by Kingsley on 2008-01-09
> **original_jamingrit said:**
> It shouldn't be that much different.  It's just that when you follow ubuntu howtos, you just have to avoid downloading debs, and replace sudo apt-get with sudo <insert appropriate command>.

I'm very sure PCLinuxOS uses apt-get also.

---

### Post by DarkOx on 2008-01-09
How far from the beaten path do you intend to stray?

I used PCLinuxOS for awhile, and I found for most things you didn't need any kind of tutorial. Compiz worked fine by default, and just about all of the popular packages you'd want are in PCLinuxOS's repos. You can sometimes loosely follow Ubuntu-based tutorials, but you must adapt them to PCLinuxOS -- such as using an rpm based command in place of dpkg, for example. I found the process hit-and-miss, but sometimes I got it to work.

Having said that, if there's some obscure or new program (like AWN, at least when I used it) you need to use, it's hard to find rpm's for it. Sometimes Mandriva rpms will work on PCLinuxOS, but not always -- compiling the program may be your only option to get it. Also remember in PCLinuxOS packages often aren't split up the way they are in Ubuntu (for example, to get kteatime I had to install the whole kde games package) and sometimes have different names (I think PCLinuxOS calls the msttcorefonts package 'webcore fonts' or something like that.)

The biggest change for PCLinuxOS is it's control center, which is quite frankly superb. I remember it setting up a samba share a lot easier than in other distros.

---

### Post by r4ik on 2008-01-09
Howto's can be found here,

[http://www.howtoforge.com/the_perfect_desktop_pclinuxos_2007](http://www.howtoforge.com/the_perfect_desktop_pclinuxos_2007)

and here,

[http://www.howtoforge.com/pclinuxos_gnome](http://www.howtoforge.com/pclinuxos_gnome)

Good luck !

---

### Post by loneowais on 2008-01-09
I would rather suggest you to switch to Linux Mint....Its better than PclinuxOS & is completely compatible with ubuntu.....its great/

Although i'm using gutsy gibon

---

### Post by SunnyRabbiera on 2008-01-09
> **original_jamingrit said:**
> It shouldn't be that much different.  It's just that when you follow ubuntu howtos, you just have to avoid downloading debs, and replace sudo apt-get with sudo <insert appropriate command>.

pclinux uses apt, and root

---

