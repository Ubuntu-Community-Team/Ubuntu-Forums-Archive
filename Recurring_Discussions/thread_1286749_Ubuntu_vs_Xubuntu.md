---
title: "Ubuntu vs Xubuntu"
date: 2009-10-09
forum: Recurring Discussions
---

### Post by Redsandro on 2009-10-09
Hi there,

I use Ubuntu on my server/DAW and Xubuntu on my Media Center/desktop machine. The latter being an older computer, that's why I chose Xubuntu.

However, I kind of like Xubuntu better. I was playing with the idea to change Ubuntu to Xubuntu also.

So I was wondering, what are major or important differences between the two, apart from small cosmetic differences which make me prefer Xubuntu anyway?

Stuff I bump into:

**Xubuntu Pro's:**
[LIST][*]xfce is lighter and faster
[*]Thunar and others have a "warning, root" bar, I like.
[/LIST]

**Xubuntu Con's:**
[LIST][*]No built-in SAMBA support (fusesmb to the rescue)
[*]No built-in CD burning support (I use stand-alone app anyway)
[/LIST]

But is that really all? [SIZE="1"]If the difference is so small, it could fit on a DVD or maybe even CD with the installer asking you if you want K- X- Flux- or U- buntu in stead of all different releases.[/SIZE]

Also feel free to share why you prefer (x)Ubuntu.

---

### Post by scragar on 2009-10-09
Xubuntu comes with a different WM, a different file manager, a different office suit...

The CDs are already quite packed, I doubt there's space on a CD to merge them all, on a DVD though I don't doubt that it would all fit, you'd still need to provide CDs though since not everyone has a DVD writer/reader.

---

### Post by Redsandro on 2009-10-09
Ah yes true.
Well I like the xfce window manager and file manager. And I install Open Office anyway amongst other apps I need such as Ardour and Wine.

But as long as I don't find big differences that really make Ubuntu/Gnome look good, I think I will convert.

---

### Post by snowpine on 2009-10-09
These tutorials will help you add the Xubuntu desktop to your existing Ubuntu install:

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Good luck!

---

### Post by Redsandro on 2009-10-09
Thanks. That second one looks nice and easy, but not a total conversion. The first one looks also easy, but is it only about the desktop?

I was wondering, what stuff will be broken after a conversion like that? Am I forgetting something?

[list]
[*]All panel items and pinned shortcuts
[*]Desktop contents
[*]Shared folders [SIZE="1"](Xub uses samba and Ub uses netuser?)[/SIZE]
[*]Not a total conversion (boot screen, login screen, etc)
[/list]

But stuff like wine + configuration + apps + games, Open Office, Opera browser and config for all apps will remain intact?

Because I like it easy like that. But if it will make my system messy and buggy, I'll wait for some bigger free time to do a clean install.

---

### Post by snowpine on 2009-10-09
> **snowpine said:**
> [http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

The first tutorial simply adds the Xfce desktop to your existing system. Nothing is deleted. You'll be able to use all the same apps and data as you have now.

The second tutorial complely removes Gnome/Ubuntu and gives you the exact same system as a completely fresh Xubuntu install. None of your user data/documents will be deleted, but you might lose some applications you're used to (like Openoffice for example).

I would recommend tutorial #1 in your situation. Without making any major changes to your system, it will give you the choice between Xfce or Gnome every time you log in. That way, you can compare them easily and see which works for you in the long run.

---

### Post by Redsandro on 2009-10-10
I haven't done the conversion yet. I just realised, I use the Gnome built-in shared desktop a LOT because it's a headless machine and I remote-connect through VNC often to take care of server stuff and automated downloads.

I also use FreeNX, but it does not support sharing a desktop either. I use it to run stuff that doesn't need a shared desktop because it's much faster than VNC.

On my Xubuntu machine I have also installed a VNC server, but the difference is that I cannot get it to share a desktop. It will just log in with a new session. And I need the shared desktop for I cannot control apps that are auto-started with a certain auto-login if you follow me.

---

### Post by RichardLinx on 2009-10-10
Xubuntu is actually slower than Ubuntu even though xfce is a lighter window manager than GNOME. I came across an article a few weeks ago which compared performance on Ubuntu, Lubuntu and Xubuntu.

> The first test is simply to check how much memory is used after a fresh boot of the respective live CDs, all the way into the default desktop.
Lubuntu: 57,908 KB
Xubuntu: 156,852 KB
Ubuntu: 153,840 KB

It&#8217;s clear here that Lubuntu is the outright winner using almost one third less memory than the others. Interestingly, Xubuntu is using slightly more memory than its big brother.

The second test compares the amount of memory used when opening every day applications on the live system. While not completely realistic, it shows how application choice can greatly affect the performance of a system.

Lubuntu with every day applications loaded, including a terminal (LXTerminal), file manager (PCMan), calculator (Galculator), image viewer (GPicView), text editor (Leafpad), archive manager (Xarchiver), web browser (Firefox), mail client (Claws), chat program (Pidgin), bittorrent client (Transmission), audio player (Aqualung), video player (MPlayer):
Usage: 162,272 KB

Xubuntu with every day applications loaded, including a terminal (Terminal), file manager (Thunar), calculator (Gcalctool), image viewer (Ristretto), text editor (Mousepad), archive manager (File-roller), web browser (Firefox), mail client (Thunderbird), chat program (Pidgin), bittorrent client (Transmission), audio player (Exaile), video player (Totem):
Usage: 311,560 KB

Ubuntu itself with every day applications loaded, including a terminal (GNOME Terminal), file manager (Nautilus), calculator (Gcalctool), image viewer (F-Spot), text editor (Gedit), archive manager (File-roller), web browser (Firefox), mail client (Evolution), chat program (Empathy), bittorrent client (Transmission), audio player (Rhythmbox), video player (Totem):
Usage: 289,744 KB

> **What is also interesting is that Ubuntu itself, even with is GNOME desktop and heavier applications such as Evolution and F-Spot, is actually using less memory than Xubuntu** - the perceived lightweight option for the community.

Pretty interesting, huh?

Sorry, forgot to add the source: [http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)

---

### Post by Redsandro on 2009-10-11
That's interesting.. needless to say, that goes against pretty much everyone here's common knowledge. Do you have a source for that?

The only thing I can say against it is that I've come to know Xubuntu because I kept it after noticing it's much more workable than it's bigger brother on my low end machines.

That makes me think, if the system is somewhat 'smart', like for example Windows does in it's newer versions, the memory usage is scaled over the amount of available memory. Why not use memory that is sitting there doing nothing if you can use it to speed up things?

You mention that Xubuntu is actually slower, but nowhere in that article is a speed comparison layed out. Maybe Xubuntu is faster because it uses more memory for lighter apps. And maybe the test machine just had too much free memory. They should run an actual speed test with the same programs on a 128 MB, 512 MB and a 2 GB machine. That would really caress my interest.

---

### Post by RichardLinx on 2009-10-11
> **Redsandro said:**
> That's interesting.. needless to say, that goes against pretty much everyone here's common knowledge. Do you have a source for that?
Yes, here it is: [http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)

---

### Post by sideaway on 2009-10-11
Both Ubuntu and Xubuntu both use the same memory management... You'd see no difference. What you're seeing is idle memory usage. That's with no programs running. Just the Desktop Environment, that's the memory that's going to be constantly used no matter what. In my experience, Exaile and Thunderbird use more memory than Rhythmbox and Evolution however.

Using more memory for the same (version of a) program to do the same task doesn't make any sense... I don't think you quite understand how RAM and its usage contributes to the speed of a computer... 
The speed of a computer is largely attributed to the CPU, the CPU reads the information on your HDD, and places necessary information (for quick access) on your RAM. The less you have to put on your RAM, the faster your computer will run the program. If you are running RAM intensive applications or many applications, and have insufficient RAM, your computer will slow to a crawl as it has to use the HDD to do the RAMs job. Think of RAM as fast access, temporary storage, like your short-term memory for your brain.

---

