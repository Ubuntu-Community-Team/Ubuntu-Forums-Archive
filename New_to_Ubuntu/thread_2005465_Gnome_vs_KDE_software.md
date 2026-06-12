---
title: "Gnome vs KDE software"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by lkz6998 on 2012-06-17
I am still new to Linux, I have been using Lubuntu for about 10 days now and love it so far.  I have a question that I have not been able to figure out.
I've noticed that some programs are "made" for KDE or GNOME.  What exactly does that mean?  I use Lubuntu which has neither KDE nor GNOME. But I am able to download programs from the package manager such as Krusader which describes itself as a "file manager for KDE" and I use Gnumeric which is "part of the GNOME desktop environment".
How is it that I can run these programs even though Lubuntu uses LXDE desktop environment?
When I'm searching for a program should I prefer to look for something that is designed for LXDE desktop?
Is a GNOME program going to work better or more optimized if it runs on a GNOME desktop?
Thanks for any help!

---

### Post by Paqman on 2012-06-17
Linux systems are highly modular. You can generally mix and match bits to your heart's content, as long as you're getting them all from your distro's repositories.

> **lkz6998 said:**
> 
How is it that I can run these programs even though Lubuntu uses LXDE desktop environment?

Your package manager gets all the required bits and pieces to run them from the repositories. That means the first Gnome app you download might be quite a big download, because it has to pull in part of the framework it needs to run. Subsequent Gnome apps would then be able to use that same framework, and might not be such big downloads.

In short: the package manager always satisfies all dependencies for any program you tell it you want.


> 
Is a GNOME program going to work better or more optimized if it runs on a GNOME desktop?


Better no, more optimised yes (slightly). For example, a KDE app will run on your system,but to do so it will need to load all of it's supporting libraries into memory before it did. If you were running KDE then those would probably already be loaded, and your app would launch lickety split. On LXDE you'll probably have a bit of a delay while your hard drive chugs away, but once the app finally pops up it'll work fine.

So you can use apps from other desktop environments, but they'll be slow to launch and will consume quite a lot of RAM.

---

### Post by cortman on 2012-06-17
It's usually a good idea NOT to have both Gnome and KDE apps installed on one system- the bloat and extra library build up can get ridiculous.
The main difference is that KDE uses QT libraries, whereas Gnome uses GTK.
If you can, it's best to stick to one or the other.

---

### Post by Paqman on 2012-06-17
> **cortman said:**
> It's usually a good idea NOT to have both Gnome and KDE apps installed on one system- the bloat and extra library build up can get ridiculous.


It won't cause any actual problems though. The libs won't be loaded until they're actually needed. Where it gets really gnarly is if you install the whole DE, and all the apps contained within.

The actual drawbacks are very minor IMO. If (for example) you use a Gnome but think K3B is a great app, by all means use it.

---

### Post by ajgreeny on 2012-06-17
> **cortman said:**
> It's usually a good idea NOT to have both Gnome and KDE apps installed on one system- the bloat and extra library build up can get ridiculous.
The main difference is that KDE uses QT libraries, whereas Gnome uses GTK.
If you can, it's best to stick to one or the other.
Not too sure I totally agree with this comment.

It is probably not a great idea to have both **ubuntu-desktop** and **kubuntu-desktop** packages (plus every application they bring with them) installed on the same OS as there will be a large degree of duplication of applications for particular purposes, eg kate and gedit for text editing, a file manager for each DE etc etc. and your menus will be very unwieldy.

However, I do not believe there is any reason to get worried if you need one or two apps from the KDE DE on a mainly gnome system.  Many users of gnome prefer and install and use **k3b** in place of brasero because they believe that it is much better.  That brings with it a lot of kde lib packages, but so what; this is not windows, and simply having them installed will not slow down the computer in any way.  If you have the disk space to accommodate those extra lib packages there is no real reason to worry about it.

If you like an application from KDE on your gnome system, if you really want it , and will use it, go ahead and install it and enjoy.

EDIT:  Too slow!  Well said Paqman;  we both agree on that.

---

### Post by lkz6998 on 2012-06-17
After reading the above responses I'm a little confused about what is the advantage of using Lubuntu.  I chose Lubuntu because my computer (Acer nettop) has an Atom processor and I wanted a lightweight and fast Linux.  I have 2GB ram and 250GB HD btw.
But if I have to load extra libraries in order to run Gnome or KDE programs then am I losing the "lightweight and fast" advantage??
Are there any programs made for LXDE?  I searched around and couldn't actually find any...

---

### Post by Paqman on 2012-06-17
> **lkz6998 said:**
> 
But if I have to load extra libraries in order to run Gnome or KDE programs then am I losing the "lightweight and fast" advantage??


To some degree, yes.

> 
Are there any programs made for LXDE?  I searched around and couldn't actually find any...

There are plenty of apps which don't depend heavily on any particular desktop environment. For example, the Abiword word processor that ships in Lubuntu is pretty generic.

Also, Lubuntu actually includes a reasonable amount of Gnome stuff anyway, as the devs use the tools from the more mature and complete Gnome ecosystem to plug the gaps in LXDE. So you may find that some Gnome apps will find themselves quite at home.

---

### Post by whatthefunk on 2012-06-17
> **lkz6998 said:**
> After reading the above responses I'm a little confused about what is the advantage of using Lubuntu.  I chose Lubuntu because my computer (Acer nettop) has an Atom processor and I wanted a lightweight and fast Linux.  I have 2GB ram and 250GB HD btw.
But if I have to load extra libraries in order to run Gnome or KDE programs then am I losing the "lightweight and fast" advantage??
Are there any programs made for LXDE?  I searched around and couldn't actually find any...

I wouldnt worry too much about it.  I would stick with gnome programs though as all the extra KDE libraries might weight down a light system.

---

### Post by cortman on 2012-06-17
> **Paqman said:**
> It won't cause any actual problems though.

> **ajgreeny said:**
> Not too sure I totally agree with this comment.


Right; I think my comment was misleading. It's not the end of the world to have a couple KDE apps on a Gnome system or vice versa; and other than taking up system storage (which should be fairly minimal) there really shouldn't be many drawbacks. It WILL build up more system cruft though.
I guess it has more to do with my own OCD; I look at a huge list of dependents from apt-get and shudder. :)

---

### Post by Peripheral Visionary on 2012-06-18
LXDE gets along nicely with GTK, as does Xfce and of course Gnome. KDE is a whole 'nother animal! That's why in both Lubuntu and Xubuntu you find alot of GTK apps and no KDE apps by default.

That doesn't mean you can't use KDE apps in your Lubu or Xubu. You can! But installing them "pulls in" a bunch of Qt libraries and stuff to enable KDE stuff to run in your GTK-friendly Lubu, Xubu, or Ubu.

On your 2 GB RAM machine with its mega-huge hard drive, it's not an issue and there is no real advantage for you to run a "lightweight" distro unless you just *prefer* the Xfce or LXDE desktop environment.

The best article I've ever seen on the subject, written "in layman's terms" on desktop environments, window managers, and "integration" (that's what your question is really about) can be found [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893").

---

### Post by lkz6998 on 2012-06-18
> **Peripheral Visionary said:**
> 

The best article I've ever seen on the subject, written "in layman's terms" on desktop environments, window managers, and "integration" (that's what your question is really about) can be found [here]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893").


Excellent article, thanks.

---

### Post by mastablasta on 2012-06-18
> **Peripheral Visionary said:**
> 
On your 2 GB RAM machine with its mega-huge hard drive, it's not an issue and there is no real advantage for you to run a "lightweight" distro unless you just *prefer* the Xfce or LXDE desktop environment.
.

there actually is an advantage if you want to save some ram for some other application (KDE can get heavy if you enable all special effects) as well as soem PCU power. LXDE draws windows and desktop differently so it should be friendlier on lighter CPU (such as Atom).

However, it's worth to mention here that there are such things as netbook version of kubuntu and also low-fat-package which substantially reduces system requirements for KDE.

and back to DE - it is possible to install Gnome applicaitons or KDE application in windows as well. However, i installed skrooge (a rather small personal money managing application). But to do it in windows it required a 350 MB of libraries to be pulled in as well. It's juts an example. GIMP in windows (i believe a GTK app) probably also takes more than in linux.

but yes with such a maschine (plenty ram and disk) you can choose either environemn and then reduce the bling to speed it up (due to a bit poorer GPU you probably have) or if you simply wish to use more GPU power for something else rather than drawing nice windows and special effects.

with your configuration i would probably go with XFCE. it's easy to configure and more mature than LXDE. due to it's configuration abilities it is very good option for low powered CPU.

Additionally Lubuntu LTS has 3 years of support while Xubuntu has 5 years if that even matters to you.

---

### Post by ajgreeny on 2012-06-18
Unfortunately the most recent version of Lubuntu, 12.04, is not an LTS version, and in spite of all the other family of *ubuntu OSs having either 5 or 3 years support, Lubuntu only has 18 months support.

Apart from that comment I go along with the rest of what mastsblasta has to say, and agree that both Xubuntu, (XFCE) and Lubuntu, (LXDE), are possibly the way to go on a netbook.   If you like the look of it Lubuntu also includes a netbook desktop with the standard OS, so just choose it from the login screen and see what you think of it.  It's very clean and minimal looking, but not my kind of thing, though that is just a personal opinion.

---

