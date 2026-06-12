---
title: "Possible conflict between my desktop, and Kate"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by dyers2 on 2013-08-13
I'm using Ubuntu Studio with the included Xfce desktop environment. Not thrilled with Gedit, I tried Medit, Kate, and another text editor whose name I forget. Of those, I like Kate the best, though Kate is part of the KDE desktop, I think. In any case, yesterday I tried to print from Kate, but the printer printed 1 line per page for many pages before I caught it. Each line was a wide variety of sumbols, and characters, none of which are legible. Encoding is set to Unicode (UTF-8) which is what I anticipated.

Early this morning, I tried to open a new document in Kate, not the first by any means, and was met with this impass: 

 > Could not start process Unable to create io-slave: klauncher said: Error loading 'kio_file'.

Last week, I installed v.12.10 with the intention of elimating Windows. No problem printing from Gedit. Overnight, I let the software upgrade Ubuntu to v.13.04. Other than that, I haven't done anything to my system. Is Kate compatible with Xfce?  If so, do you have any advice about the printing issue, and about klauncher? If not, can you recommend a full featured text editor that is compatible with Xfce?

---

### Post by tgalati4 on 2013-08-13
You have a lot going on and this has confounded the problem--there are several factors mushed together.  

First, you performed an in-place upgrade from 12.10 to 13.04 so that will usually cause breakage.  It is better to back up your personal data and do a clean install to 13.04.

Upgrading the kernel (which happens when you upgrade distros) will often break cups and some printer drivers.

Using Kate in an XFCE environment means that all of the KDE dependencies will get pulled into your distro.  This may cause some breakage.

What is missing in gedit?

---

### Post by dyers2 on 2013-08-13
> **tgalati4 said:**
> [COLOR=#008000]You have a lot going on and this has confounded the problem--there are several factors mushed together.[/COLOR]

Truth. This move hasn't been easy from the start. It's an older machine with a CD ROM that's undependable, and BIOS that don't let me boot from a USB flash drive. I asked in another thread for some advice. One fellow suggested using Plop, which I did. Very handy.

> [COLOR=#008000]First, you performed an in-place upgrade from 12.10 to 13.04 so that will usually cause breakage.  It is better to back up your personal data and do a clean install to 13.04[/COLOR].

The same gentleman also suggested:

> **Boab1993 said:**
> [COLOR=#0000cd]Also another point is that 13.04 is a bit buggy sometimes when booting  for USB, id advise installing an older LTS Ubuntu install such as 12.04,  you can then upgrade it via the update manager when youve installed it[/COLOR]

Reasonable minds can, and often do disagree. Both approaches seem reasonable, so how to decide when you have next to nothing by way of experience? For me, it's just weigh what you know at the time, and make the best decision I can knowing that mistakes will be made. I don't remember where, but I read about the Universal USB Jnstaller 1.9.3. (UUSBI).  The way that works is that you download the Linux distro iso you want, select it from a list in the software, and it loads the flash drive.

All ready to go with 13.04, I found the supported list in UUSBI included the other Ubunto 13.04 distros, but not Ubuntu Studio. About that same time, Boab said what I quoted, and parts seemed to fit together. After days of not finding a way past a number of walls, I was eager to find a way forward, and it seemed to work, at least.

> [COLOR=#006400]Upgrading the kernel (which happens when you upgrade distros) will often break cups and some printer drivers.  Using Kate in an XFCE environment means that all of the KDE dependencies will get pulled into your distro.  This may cause some breakage.[/COLOR]

I'm not heavily invested in this installation, and many of the files I used so far are still on my old external data drive. I know of a few files on the Ubuntu partition to save, but most everything else can be re-done if that's what it takes. But I'd like to ask while on the topic: let's say I'd been using this for a year. What's the advised way to upgrade? I f things break when upgrading via Canonical, it makes one wonder why they still do it.

Anyway, at this point, I'm looking for the best way forward from where I am.

> [COLOR=#006400]What is missing in gedit?[/COLOR]

Sorry, I meant no offense. I often learn about new software by reading the prefs, trying the options out to see what they do. My only real issue involves it's configurability; the prefs are minimal, and the toolbar might also help to make it easier to access options. I've been a visual artist for some 50+ years, and as such, color is important to me. Gedit allows me to pick from several themes, but to make my own, I think I'd have to find the right file, and edit it with  colors manually, then save it as a new theme.  It's GUI ignores system colors in favor of a bland palette of pale grays.

---

### Post by tgalati4 on 2013-08-13
Gedit is a notepad editor for programmers.  It uses color for highlighting different programming languages and does not have a lot of style points.  If you like Kate then you might consider installing the KDE deskop (kubuntu or another distro that uses KDE natively).

In-place distro upgrades should work in theory, but in practice they tend to break things.  So the general advice is to upgrade distros by doing a clean install.  I was not aware of installation issues with 13.04 via USB.  I'm still on 12.10.  I find that 6 months to a year needs to elapse before any linux distro is fully baked.  

For your printing issue, look in /var/log/cups for errors.  I think there is an installation issue--KDE must have some pieces that you are missing, so that printing is broken with Kate, but works with Gedit.  Don't forget, with printing, there is a framework for printing notification which is different between XFCE and KDE and that alone would break printing for one application but not another.

My only advice is to keep at it until you run out of patience.  Everything is fixable in linux, but finding the patience is key.

---

### Post by dyers2 on 2013-08-14
> **tgalati4 said:**
> Gedit is a notepad editor for programmers.  It uses color for highlighting different programming languages and does not have a lot of style points.

True enough. With so much new about Linux in the last week, I find that I crave familiarity. I'd like to use similar colors to those I'm used to for my coding.

 > If you like Kate then you might consider installing the KDE deskop (kubuntu or another distro that uses KDE natively).

That's a thought. I initially went from thinking Lubuntu was the right choice based on it's low taxation of system resources. Then I read about how much more configurable KDE is, but also of it's higher use of resources. I finally settled on Xfce because it seemed to balance both a lower draw on RAM, and CPU, and fair degree of configurability. My older computer, a Toshiba Satellite A105 looks like,


[LIST]
[*]Processor: Intel(R) Celeron(R) M processor 1.70GHz, x86 Family 6 Model 13 Stepping 8 
[*]RAM: 894 Mb 
[*]Graphics Card: ATI RADEON XPRESS 200M Series, 128 Mb 
[*]Hard Drives: C: Total - 57231 MB, Free - 25130 MB; E: Total - 28003  MB,  Free - 9505 MB; G: Total - 29996 MB, Free - 10867 MB; H: Total -  180464  MB, Free - 12570 MB; 
[*]Motherboard: ATI, SB450 
[/LIST]
 
> In-place distro upgrades should work in theory, but in practice they tend to break things.  So the general advice is to upgrade distros by doing a clean install.  I was not aware of installation issues with 13.04 via USB.  I'm still on 12.10.  I find that 6 months to a year needs to elapse before any linux distro is fully baked.

I understand. I hadn't ever upgraded from WinXP until it had been out a couple of years, was equally slow to upgrade to 98 from 95, and used DOS all the way through 3.1, and well into 95's existence.

> For your printing issue, look in /var/log/cups for errors.  I think there is an installation issue--KDE must have some pieces that you are missing, so that printing is broken with Kate, but works with Gedit.  Don't forget, with printing, there is a framework for printing notification which is different between XFCE and KDE and that alone would break printing for one application but not another.

I don't really know what the data in the error log means, and I don't know how to interpret it, but I've pasted it below in a code box for you to see. At this point, while willing to format, and re-install, I think I might lean slightly towards removing Kate, and any KDE dependencies that were installed with it, and work best I can with packages intended to be used with Xfce.

> My only advice is to keep at it until you run out of patience.  Everything is fixable in linux, but finding the patience is key.

Thanks; good advice. Fortunately, patience is not hard for me to muster. I also have a fair amount of time. If only I could say the same about $$. I've been learning HTML, CSS, and more recently PHP using few tools, little to no cash, curiosity, high level of interest, and a drive to get it right.

Thank you again for your time, your willingness to share what you know, and for your help.

Error Log
```
W [14/Aug/2013:02:11:19 -0400] Please move "SystemGroup lpadmin" on line 4 of /etc/cups/cupsd.conf to the /etc/cups/cups-files.conf file; this will become an error in a future release.
I [14/Aug/2013:02:11:19 -0400] Listening to [v1.::1]:631 (IPv6)
I [14/Aug/2013:02:11:19 -0400] Listening to 127.0.0.1:631 (IPv4)
I [14/Aug/2013:02:11:19 -0400] Listening to /var/run/cups/cups.sock (Domain)
E [14/Aug/2013:02:11:19 -0400] Unknown directive JobPrivateAccess on line 85 of /etc/cups/cupsd.conf.
E [14/Aug/2013:02:11:19 -0400] Unknown directive JobPrivateValues on line 86 of /etc/cups/cupsd.conf.
E [14/Aug/2013:02:11:19 -0400] Unknown directive SubscriptionPrivateAccess on line 87 of /etc/cups/cupsd.conf.
E [14/Aug/2013:02:11:19 -0400] Unknown directive SubscriptionPrivateValues on line 88 of /etc/cups/cupsd.conf.
I [14/Aug/2013:02:11:19 -0400] Remote access is disabled.
D [14/Aug/2013:02:11:19 -0400] Added auto ServerAlias Pokey
I [14/Aug/2013:02:11:19 -0400] Loaded configuration file "/etc/cups/cupsd.conf"
I [14/Aug/2013:02:11:19 -0400] Using default TempDir of /var/spool/cups/tmp...
I [14/Aug/2013:02:11:19 -0400] Configured for up to 100 clients.
I [14/Aug/2013:02:11:19 -0400] Allowing up to 100 client connections per host.
I [14/Aug/2013:02:11:19 -0400] Using policy "default" as the default.
I [14/Aug/2013:02:11:19 -0400] Full reload is required.
I [14/Aug/2013:02:11:19 -0400] Saving job.cache...
D [14/Aug/2013:02:11:19 -0400] Discarding unused printer-stopped event...
D [14/Aug/2013:02:11:19 -0400] cupsdMarkDirty(P----)
D [14/Aug/2013:02:11:19 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Not busy"
D [14/Aug/2013:02:11:19 -0400] cupsdDeregisterPrinter(p=0xb8fe70c0(Samsung-CLX-3180), removeit=1)
I [14/Aug/2013:02:11:20 -0400] Loaded MIME database from "/usr/share/cups/mime" and "/etc/cups": 39 types, 56 filters...
D [14/Aug/2013:02:11:20 -0400] Loading printer Samsung-CLX-3180...
D [14/Aug/2013:02:11:20 -0400] load_ppd: Loading /var/cache/cups/Samsung-CLX-3180.data...
D [14/Aug/2013:02:11:20 -0400] cupsdRegisterPrinter(p=0xb8ff97f8(Samsung-CLX-3180))
I [14/Aug/2013:02:11:20 -0400] Loading job cache file "/var/cache/cups/job.cache"...
D [14/Aug/2013:02:11:20 -0400] [Job 1] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 1] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 2] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 3] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 4] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 5] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 5] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 6] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 6] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 7] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 8] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 9] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 10] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 11] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 12] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 13] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 14] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 15] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] [Job 16] Loading from cache...
D [14/Aug/2013:02:11:20 -0400] cupsdAddSubscription(mask=0, dest=(nil)(), job=(nil)(0), uri="(null)")
I [14/Aug/2013:02:11:20 -0400] Full reload complete.
D [14/Aug/2013:02:11:20 -0400] Calling FindDeviceById(cups-Samsung-CLX-3180)
D [14/Aug/2013:02:11:20 -0400] Calling DeleteDevice(/org/freedesktop/ColorManager/devices/cups_Samsung_CLX_3180)
D [14/Aug/2013:02:11:20 -0400] Using profile ID "Samsung-CLX-3180-Gray..".
D [14/Aug/2013:02:11:20 -0400] Calling CreateProfile(Samsung-CLX-3180-Gray..,temp)
W [14/Aug/2013:02:11:20 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Samsung-CLX-3180-Gray..' already exists
D [14/Aug/2013:02:11:20 -0400] Using profile ID "Samsung-CLX-3180-RGB..".
D [14/Aug/2013:02:11:20 -0400] Calling CreateProfile(Samsung-CLX-3180-RGB..,temp)
W [14/Aug/2013:02:11:20 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Samsung-CLX-3180-RGB..' already exists
I [14/Aug/2013:02:11:20 -0400] Registering ICC color profiles for "Samsung-CLX-3180".
D [14/Aug/2013:02:11:20 -0400] Calling CreateDevice(cups-Samsung-CLX-3180,temp)
D [14/Aug/2013:02:11:20 -0400] Created device "/org/freedesktop/ColorManager/devices/cups_Samsung_CLX_3180".
I [14/Aug/2013:02:11:20 -0400] Listening to [v1.::1]:631 on fd 9...
I [14/Aug/2013:02:11:20 -0400] Listening to 127.0.0.1:631 on fd 10...
I [14/Aug/2013:02:11:20 -0400] Listening to /var/run/cups/cups.sock:631 on fd 11...
I [14/Aug/2013:02:11:20 -0400] Resuming new connection processing...
D [14/Aug/2013:02:11:20 -0400] cupsdSetBusyState: newbusy="Dirty files", busy="Dirty files"
D [14/Aug/2013:02:11:20 -0400] Discarding unused server-restarted event...
D [14/Aug/2013:02:11:21 -0400] Report: clients=0
D [14/Aug/2013:02:11:21 -0400] Report: jobs=19
D [14/Aug/2013:02:11:21 -0400] Report: jobs-active=0
D [14/Aug/2013:02:11:21 -0400] Report: printers=1
D [14/Aug/2013:02:11:21 -0400] Report: stringpool-string-count=10925
D [14/Aug/2013:02:11:21 -0400] Report: stringpool-alloc-bytes=9056
D [14/Aug/2013:02:11:21 -0400] Report: stringpool-total-bytes=194824
I [14/Aug/2013:02:11:50 -0400] Saving printers.conf...
D [14/Aug/2013:02:11:50 -0400] cupsdSetBusyState: newbusy="Not busy", busy="Dirty files"
```

---

### Post by alan9800 on 2013-08-14
you might install [Kubuntu 12.04 LTS](http://old-releases.ubuntu.com/releases/kubuntu/releases/12.04.1/release/) and then run the following command from Konsole (the Kubuntu terminal):```
sudo apt-get install kubuntu-low-fat-settings
```so that the OS is tuned for your hardware.

---

### Post by vasa1 on 2013-08-14
> **dyers2 said:**
> .... My only **real issue** involves it's configurability; the prefs are minimal, and the toolbar might also help to make it easier to access options. I've been a visual artist for some 50+ years, and as such, color is important to me. Gedit allows me to pick from several themes, but to make my own, I think I'd have to find the right file, and edit it with  colors manually, then save it as a new theme.  It's GUI ignores system colors in favor of a bland palette of pale grays.

How exactly is it a real issue? What exactly do you wish to configure? Maybe someone here can help if you have a specific question?

Re.: "*I'd have to find the right file, and edit it with  colors manually, then save it as a new theme.*" ...
The files are here: /usr/share/gtksourceview-3.0/styles/
You could also create ~/.local/share/gtksourceview-3.0/styles/and keep styles there.
Anyway, if you need to look at this aspect in the future just ask!

---

### Post by mastablasta on 2013-08-14
Geany is another nice editor. there are also plenty of IDE or what are they called. that are specifically aimed at programing.

you are not really saving much system resources if oyu use XFCE or LXDE and then KDE or Gnome aplications. OK the Xubuntu OS is a bit lighter than KDE with low fat settings but not that much. mostly only on RAM.

---

### Post by tgalati4 on 2013-08-14
There are so many editors available:

```
apt-cache search editor
```

All of them will be different from the development environments that you are used to, but with some time, you will eventually find one you like.  Gedit is just a swiss army knife of editors and it's quick and simple to use, but not really an integrated development environment (IDE).  So if you have a specific language that you want to develop in, there will be several IDE's and editors available.

Based on the spec's of the OP's laptop, XFCE or LXDE may be the only ones that run decently.  Add more RAM (like 2GB) then KDE becomes viable.

As far as cups, monitor the status of your printer using [http://localhost:631](http://localhost:631) .  I didn't see any fatal errors from CUPs so I'm guessing there is a notification issue or a KDE print event issue that is causing a problem.

---

### Post by dyers2 on 2013-08-15
> **alan9800 said:**
> you might install [Kubuntu 12.04 LTS]("http://old-releases.ubuntu.com/releases/kubuntu/releases/12.04.1/release/") and then run the following command from Konsole (the Kubuntu terminal):```
sudo apt-get install kubuntu-low-fat-settings
```so that the OS is tuned for your hardware.

This sounds like excellent advice, and I believe I'll head in this direction if I feel like Xfce is the source of any unresolvable issues, or if I just can't get as much configuration as I want from Xfce programs.

ETA: Do you think that those low-fat-settings might help me, too?

---

### Post by dyers2 on 2013-08-15
> **vasa1 said:**
> How exactly is it a real issue? 

I've been using a piece of software, NoteTabPro for 15 years in Windows. It is, and long has been highly configurable, and as a result, is tailor made for people who like tinkering with software to make it work best for their own needs, and again as their needs change. When I have trouble finding something for Linux that is virtually ubiquitous in Windows, that is a real issue for me. If it doesn't exist, I can live with that, but not so much to have my need/desire for that challenged. 

There's a reason that cars are painted in a wide variety of colors. There's a reason for the fact that many people set about painting their now residence before, or just after moving in. It's not a one size fits all, take it or leave it world, is it? I mean, if I don't want ketchup on my McDonald's burger, I can ask for them to leave it off. Sometimes, they actually do.

> What exactly do you wish to configure? Maybe someone here can help if you have a specific question?

[FONT=arial black]**[COLOR=#FF0000]C[/COLOR][COLOR=#FF8C00]o[/COLOR][COLOR=#008000]l[/COLOR][COLOR=#0000FF]o[/COLOR][COLOR=#008080]r[/COLOR]**[/FONT]. 

As a visual artist, color is an important tool to me. It can be used for instant visual clues about what something is, should do, in organization, in learning, and on, and on. My specific question was to know if you knew of a Xfce compatible, full featured text editor for developers. I'd think that in Linux, a world where more people code in some way or other than not, a text editor that's not been stripped down to the essentials wouldn't be so much to ask. There are a number of programs made for Windows that display a postage stamp swatch of a color when you hover over the hex or RGB codes.

> Re.: "*I'd have to find the right file, and edit it with  colors manually, then save it as a new theme.*" ...
The files are here: /usr/share/gtksourceview-3.0/styles/
You could also create ~/.local/share/gtksourceview-3.0/styles/and keep styles there.
Anyway, if you need to look at this aspect in the future just ask!

Thank you for the references to those individual files. I can find those when I need to, but I'm still very slow at it, so these are helpful. Actually, I'm still very slow at everything in Ubuntu because of the time required to Google, read through one or more articles or forum threads, and try to put it into practice. A thorough, clean, well designed editor that's built into the app's options make that job fast, and simple which is, after all, what computers & software are supposed to do.

---

### Post by vasa1 on 2013-08-15
Sorry to read that the existing editors don't meet your standards.

---

### Post by dyers2 on 2013-08-15
> **mastablasta said:**
> Geany is another nice editor. there are also plenty of IDE or what are they called. that are specifically aimed at programing.

Dang! Right you are. I know the term IDE, but it's not yet part of my vocabulary. After this, it'll become a lot more so. I don't know why I didn't think to search the repository for IDE on my own, but thanks for the reminder. After entering search, I filtered for highest rated, and when I did, Geany was the top of the list. I've installed it, and will try it on over the next day or two.

> you are not really saving much system resources if oyu use XFCE or LXDE and then KDE or Gnome aplications. OK the Xubuntu OS is a bit lighter than KDE with low fat settings but not that much. mostly only on RAM. Yes, I see that, now. I've already ditched Kate, and all it's dependencies. I was hoping the bits were more interchangeable than they are.

---

### Post by dyers2 on 2013-08-15
> **tgalati4 said:**
> There are so many editors available:  All of them will be different from the development environments that you are used to, but with some time, you will eventually find one you like. 

That's a great way to put it, and I agree. I also have the possibility of getting a familiar editor/IDE to run in Wine, but I want to avoid that whenever possible.

 > Gedit is just a swiss army knife of editors and it's quick and simple to use, but not really an integrated development environment (IDE).  So if you have a specific language that you want to develop in, there will be several IDE's and editors available.

That's another good point

---

### Post by dyers2 on 2013-08-15
> **vasa1 said:**
> Sorry to read that the existing editors don't meet your standards.

Thank you. 

In turn, I'm sorry that my dissatisfaction falls short of your standards.

---

### Post by dyers2 on 2013-08-15
And now for something completely different

[http://www.youtube.com/watch?v=MrCPIrs90eg](http://www.youtube.com/watch?v=MrCPIrs90eg)

(6 seconds)

---

