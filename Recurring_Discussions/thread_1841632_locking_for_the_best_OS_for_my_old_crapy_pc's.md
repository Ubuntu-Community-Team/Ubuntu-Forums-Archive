---
title: "locking for the best OS for my old crapy pc's"
date: 2011-09-09
forum: Recurring Discussions
---

### Post by uKEN on 2011-09-09
Hay well I have a few realy crapy pc: 

GatWay lap top.. 1200mh, 512mb ram
Dell desk top.. p4, 256mb ram

 Will thay run beader under puppy or Lbuntu or what
any sugestions would be great

---

### Post by TeoBigusGeekus on 2011-09-09
Lubuntu will be perfect for them.
If you feel adventurous, you could try an Arch linux installation with openbox as you DE.

---

### Post by Bachstelze on 2011-09-09
I wish people would stop saying over 1 GHz with 512 MB of RAM is "crappy". Hell, you can run Ubuntu on that, just disable RAM-heavy things like Compiz and maybe Firefox. When you're on 400 MHz with 128 MB of RAM you're talking crappy.

---

### Post by Chimes on 2011-09-09
Puppy, TinyCore, CrunchBang, Zenwalk, and Vector are going to be ones that people redirect you too. They will all run entirely fine on the specs you're talking about. In fact, you will swear you've never seen a computer go so fast from powered off to desktop in your life. I've run linux on a computer with 350 mhz and 58 mb ram. I am not kidding. This laptop was half as old as I was when I got it. PDFs took a while, and I never even tried video, but checking e-mail and editing documents (abiword was fastest) went as fine as one could want.

Anyway, I encourage you to try these non-ubuntu OSes: you will definitely learn new things about taking care of a linux systems.

However, a warning. The reason this is true is because these Operating Systems have not been designed (nor had enough developers and a big enough support community) to be encapsulatingly easy to use. So for example, normally the point-and-click installer modules will work, the software will work, etc. But at some point, you will probably run into some showstopper package that doesn't work, or isn't prepared for your OS, or some kind of bug you didn't expect.

Now, if you're ready to pull up your sleeves and do some really scary stuff (like type "configure" and "make" and then "make install" on a command line to install software manually :) ) you can usually fix most of these problems easily. It just takes a little learning if you're not well acquainted with the command line and the filesystem structure and operation of a linux system. So for example, when someone asks me how to start learning more about linux than they already know, I suggest O'Reilly's linux pocket guide and one of these barebone systems.

Now, the benefit of ubuntu is its easy. Apt-get takes care of everything package related, because there are all these people making sure there are no problems on the distribution level. It does often come with a lot of stuff you may not want right now (don't use bluetooth, for example?), but it will do the job. It is this ease of installing packages (and my constant need to do it) which is why I use ubuntu with enlightenment on my main system (2.0 gHz with enlightenment desktop = wicked fast. I don't remember the last time I waited for something to open.) I also uninstall a lot of programs I don't need, and prevent several services from beginning at startup. It maintains the simplicity and speed I am looking for.

But for example, on a server you very, very rarely have to install new packages. So for example, if these boxes are just going to be simple servers, say like, a jukebox for playing music (I know small servers is often a good use for old computers), ease of rapid anytime package-installation wouldn't come under consideration.

edit: btw the laptop was from 1997 or 98, I believe, so it was like 12 years old when I got it. I still have it in storage with a couple other keepsakes.

---

### Post by el_koraco on 2011-09-09
> **uKEN said:**
> 
 Will thay run beader under puppy or Lbuntu or what
any sugestions would be great

Lubuntu, Xubuntu, hell, you can even run Ubuntu on it if you use Metacity instead of Compiz. Or choose one of the lighter distros. Openbox can run on 40 MB if you do a Gentoo, Arch, Slackware, grml2hd or Debian netinstall, and there's a bunch of even lighter window managers. JVM (Puppy Linux uses it) goes beyond 40 MB and you get a panel and stuff. Any tiler will run on the Force alone. 

It's mostly the apps that will test the ram. I'd say go with CLI apps as much as you can - mutt for email, mc for file management, irssi/centerim/mcabber for IM and IRC, MOC, cmus or mpd for music, mplayer for video, rtorrent for torrenting, and leave the RAM for a browser. You can even trim down there, Midori is a fully featured browser that hardly ever eats more than 150 MB. It's even gonna be fun, I got 2 gigs of RAM, and only use Firefox and office software from the graphical apps.

---

### Post by ilovelinux33467 on 2011-09-09
You could try out FreeBSD and install a light window manager like icewm from the ports. Or even NetBSD.

---

### Post by LowSky on 2011-09-09
About Arch, make sure the processor is i686 compatible. Many of those older chips under the 1.5Ghz ranges can be i586 and not compatible with Arch. This is part of the reason many OSes are still written for 386 and 486 processors, so old PC's can still run.

---

### Post by Tibuda on 2011-09-09
do you want to lock an os? I suggest this:
[img]http://upload.wikimedia.org/wikipedia/commons/thumb/5/59/Padlock.svg/220px-Padlock.svg.png[/img]

---

### Post by walt.smith1960 on 2011-09-09
Another option for less powerful machines might be PCLinuxOS.  I have a ThinkPad R31 which is a 2002ish PIII w/ 512 Mb. RAM.  For whatever reason, Ubuntu and Lubuntu 11.04 would not install.  I think it might be due to a deprecated video driver though I'm not sure.  Ubuntu 10.10 would install and run, 11.04 would not.  I was curious about PCLinux OS so downloaded and burned a CD.  It installs and runs quite well.  There are a differences compared to *buntu but nothing dramatic.

---

### Post by sidzen on 2011-09-09
[Swift Linux Regular]("http://sourceforge.net/projects/swiftlinux/files/swiftlinux-0_1_2-regular.iso/download") is based on antiX-M11, but even lighter -- it's a true Debian-based distro, as is my second recommendation, [CrunchBang-i486]("http://crunchbanglinux.org/wiki/statler_which_version")

Also, see this [review of Light Distros]("http://www.tuxradar.com/content/whats-best-lightweight-linux-distro") -- dated (*e.g.* #! "Statler" is now Debian, not ubuntu-based) but good

Best wishes, from an 'old PC performance junkie' !

---

### Post by fillintheblanks on 2011-09-09
I left Ubuntu for Archbang and it works great for me considering my system is not that new.

---

### Post by sidzen on 2011-09-09
> **sidzen said:**
> [Swift Linux Regular]("http://sourceforge.net/projects/swiftlinux/files/swiftlinux-0_1_2-regular.iso/download") is based on antiX-M11, but even lighter -- it's a true Debian-based distro, as is my second recommendation, [CrunchBang-i486]("http://crunchbanglinux.org/wiki/statler_which_version")

Also, see this [review of Light Distros]("http://www.tuxradar.com/content/whats-best-lightweight-linux-distro") -- dated (*e.g.* #! "Statler" is now Debian, not ubuntu-based) but good

Best wishes, from an 'old PC performance junkie' !

[SIZE="2"]*Addendum*[/SIZE]

For the PC with only 256MB RAM, try Connochaet OS -- see [http://www.connochaetos.org/wiki/]("http://www.connochaetos.org/wiki/") -- I am using it now for the first time.  It uses the ***pacman*** package  manager (a new one on me, but similar to rpm, it appears).  

BTW,  *Connochaet* is the Latin genus name of the wildebeast or **gnu**  LOL!

---

### Post by Khakilang on 2011-09-10
I had Xubuntu 11.04 running on an old Pentium 4 1.5GHz with 512MB RAM. Its run fine provided you don't open too many Window. I am sure you can upgrade the RAM from 256MB to 512MB or even to 1GB that will help a lot.

---

### Post by Sef on 2011-09-10
Another Best OS thread.

---

### Post by XubuRoxMySox on 2011-09-10
The computer you describe is not "crappy" at all! Ubuntu will run on it. I use and love Xubuntu because of the *interface* mostly, not because I need to on my modest hardware. Xfce is quick and configurable, a model of simplicity and elegance. Being "lightweight" is a bonus!

However: I ran a LiveCD of [SalixOS]("http://salixos.org") and was absolutely amazed at it's speed: The Salix *LiveCD* was snappier than *installed* Xubuntu! That surprised the heck out of me. I've never had a LiveCD experience that could outrun my beloved Xubuntu before. It's Slackware-based and therefore offers "long term support" that completely blows most other distros away. Slackware Version 8.1 (2002) still gets security updates. That makes 9 years of support! Salix is one of the few Slackware-based distros that remains fully compatible with it's parent distro - which means SalixOS users enjoy the same long-term support as Slackware users.

On "crappy" hardware I bet it would totally rock. On my hardware - modest by today's standards I guess but hardly "crappy" - it outruns even [my Most Beloved Distro Ever]("http://xubuntu.org"). Amazing.

---

### Post by uKEN on 2011-09-12
Ah yes I see some realy good points..

My laptop's HDD is realy beaten up. I realy don't want to chance multiple formats for testing.I have to tweak the paging . Default sems to lockup an freez if I move the HDD to mutche.

So thaink you for your input ! 

Oh and I didn't mean to exspres that my pc's wer garbadg just that each one has handycaps.

---

### Post by XubuRoxMySox on 2011-09-12
> **XubuRoxMySox said:**
> 
I ran a LiveCD of [SalixOS]("http://salixos.org") and was absolutely amazed at it's speed: The Salix *LiveCD* was snappier than *installed* Xubuntu! That surprised the heck out of me. I've never had a LiveCD experience that could outrun my beloved Xubuntu before.

UPDATE: *Installed to the hard drive*, it turns out to be a little slower than Xubu! Another mystery. It's not nearly as simple and "newbie-friendly," but I think most Windows users could probably find their way around all the configuration options. The LXDE variant of 13.37 seems like a thrown-together mixture on top of the default Xfce distro, only with lighter apps. Fun to play with, but once installed to the hard drive and configured, it shows no improved performance over Xubu 10.04. And I'd bet the newer Xubu versions would run circles around SalixOS.

Just say'n.

---

### Post by lykwydchykyn on 2011-09-12
If you want to minimize hard drive access, TinyCore might be a good option.  The root filesystem loads into RAM at boot and runs out of RAM.  Saves some disk accesses.

Of course, your processors could handle much more, as others have mentioned.

---

