---
title: "Lightweight OS"
date: 2020-03-30
forum: New to Ubuntu
---

### Post by jsinclair92 on 2020-03-30
I just installed Ubuntu 16.04 on my Acer 4339-2618, which has 2GB RAM and 2Ghz processor.  The computer previously ran Windows 7 and was _painfully_ slow, nearly inoperable, even after a system wipe and re-install of Win 7. 

Anyway, this is my 3rd or 4th string laptop, and has been relinquished as a "shop" computer and is only used in the garage.  I stumbled upon Ubuntu in a search for a lightweight OS that my old laptop could handle.

I have installed Ubuntu and have played around with it for a few days and am impressed with how much quicker it is!  However, the _only_ functionality I need out of this laptop is an internet browser (ordering auto parts, lumber, research, etc).  

I feel as if I could further lighten the load on this laptop by uninstalling any unnecessary features/apps/programs from Ubuntu.  I have uninstalled a few things but am treading carefully here, as I don't want to break my new OS.  

Can someone shed some light on:


[LIST]
[*]What apps/programs can safely be removed?
[*]Any "minimalist" tips?
[*]What unessential features can be turned off/removed to improve speed?
[*]Any other tips/tricks?
[/LIST]

Again, this is an old laptop that I will only use in the garage, which I will only be using the internet browser on (currently using Firefox).  I am looking to remove anything and everything that's unnecessary.

I greatly appreciate any help!!

---

### Post by CelticWarrior on 2020-03-30
For old laptops (and if you don't mind a desktop with an oldish look&feel), an Ubuntu flavor called Lubuntu will work better, more fluid. This should be your concern instead of the attempt to bring that "Windows mentality" of trimming down stuff.

---

### Post by oldfred on 2020-03-30
Removing apps will not save anything.
But what flavor you use does make a difference. Did you install Ubuntu or a lightweight flavor.
Light weight flavors
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

One flavor/gui not often mentioned is gnome-panel/flashback. It is like the old gnome2 or now Mint, but is updated to gnome3.
My 2006 laptop has 1.5GB of RAM. I could run Firefox and one or two other small apps like terminal or Zim, but if I accidentally clicked on something that opened a large app, screen would go gray. I knew it use using swap on slow 5400RPM drive. It last has 12.04. Just to experiment I installed 16.04 and it almost worked with full Ubuntu, but once gnome-panel was installed and chosen on sign-on screen it still worked well. 

Gnome-panel is not same as Gnome Classic as different underlying software. But somewhat similar.

sudo apt install gnome-panel
Reboot and on sign-on screen & gear icon, choose it.

---

### Post by Topsiho on 2020-03-30
You could try and use Q4OS. It's lean, uses a desktop that resembles the old KDE3 desktop, and runs well on my Acer Aspire One netbook (2008), which has a SSD drive of only 8 GB (with about 2 GB available for use, which is only just enough. And 1.5 GB RAM. It runs FireFox well enough, for me.
Topsiho

---

### Post by Autodave on 2020-03-30
Xubuntu would be a little fancier than Lubuntu and would run fine on 2g.

---

### Post by Impavidus on 2020-03-30
Applications that don't run don't take resources, other than a few MB hard drive space. So there's just the OS, the desktop environment and the web browser. Several suggestions for lighter desktop environments have been made above. Keep in mind though that these flavours of Ubuntu are only supported for 3 years for the LTS releases, so 16.04 is not an option. Take 18.04, supported until 4-2021, or 19.10, supported until 7-2020, with an option to upgrade to 20.04.

Instead of stripping down, you can start with a minimal system and build up. Look for the minimal net install and install just the packages you need.

However, your web browser is probably the heaviest application on your computer already, heavier than the OS itself. Without removing the web browser, you won't be able to gain much.

---

### Post by TheFu on 2020-03-30
if staying in the ubuntu family, check out Lubuntu/Xubuntu/Ubuntu-Mate.  There are good reasons to use one of those ubuntu flavors.

But, if you want something really lite, get TinyCore. Think it is about 100x lighter than any Ubuntu-desktop.  The huge version of TinyCore is 106MB in size, called CorePlus.  [http://tinycorelinux.net/](http://tinycorelinux.net/)   The minimal GUi version is just 16MB.  Both versions load into RAM and run that way. Extremely fast.

Disabling Javascript would be a huge help to speed up any browser, assuming enough of the website is still useful.  Generally, i disable javascript on all but trusted websites and block over 130K different advertising and tracking domains.  This can make a huge difference in browser speed.

---

### Post by grahammechanical on 2020-03-30
When using the internet the thing that slows things down are the web sites themselves. Web sites that are loaded with embedded images, videos and adverts require a fast internet connection and may be a faster network card as well. And then there is the matter of the video card. How much memory does it have? How fast is it Graphic Processor unit.

Web sites are not so far behind games in requiring fast CPU's and GPU's as well plenty of system memory and video memory.

An OS and User Interface that does not hog the CPU and the system memory is a step in the right direction but it is not the complete solution. 

Regards

---

### Post by Artim on 2020-03-31
I like [Linux Lite]("http://linuxliteos.com"), especially for beginners on Linux.  It uses the awesome Xfce desktop (like Xubuntu) but they've got it going leaner and faster.

---

### Post by GhX6GZMB on 2020-03-31
With 2 GB RAM and a 2 GHz processor, Lubuntu will work perfectly.
Then, for your application, remove Firefox completely and install Opera as browser. Firefox has unfortunately evolved into the most bloated browser around.

Then you have your workshop machine.

---

### Post by MoebusNet on 2020-03-31
For a comparison, I'm running Lubuntu 18.04 on my 2003 Dell D800 32-bit-only notebook. Its' CPU is a single-core Pentium-M (basically a Pentium 3 with a faster bus). Lubuntu is perfectly usable out-of-the-box; I haven't swapped Firefox for Opera to try it out. You'll want the 64-bit version of Ubuntu; 32-bit is being dropped. I would recommend the 18.04LTS version, then you can upgrade to 20.04 after it has been out a few months.

---

### Post by mörgæs on 2020-04-01
Lubuntu is a good idea but people should forget about 18.04. It's based upon LXDE and hence a dead end. A clean install of the LXQT based 19.10 is a better option.

---

### Post by GhX6GZMB on 2020-04-01
+1 to mörgæs. I'm running Lubuntu 19.10 and it's completely reliable and stable.

---

### Post by MoebusNet on 2020-04-02
@morgaes - I'm sure you're right about 19.10; I guess I have a bit of tunnel vision about 18.04 because it is the last desktop *buntu my older 32-bit-only notebook can run.

---

### Post by mörgæs on 2020-04-03
I had the same problem finding a good OS for my 32 bit hardware. This one proved to be one of the better:
[https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890](https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890)

---

### Post by ActionParsnip on 2020-04-03
Install Lubuntu. It's an official flavour and super light. If you run:

sudo apt-get install lxde

Then log off and log in to the LXDE session it will be much lighter.

---

### Post by CelticWarrior on 2020-04-03
> **ActionParsnip said:**
> Install Lubuntu. It's an official flavour and super light. If you run:

sudo apt-get install lxde

Then log off and log in to the LXDE session it will be much lighter.


Lubuntu is light, not super light (it used to be but no longer is; there are better alternatives for very old machines but outside of the "Ubuntu family").

Installing LXDE does NOT "install Lubuntu", it install the "Lightweight X11 Desktop Environment" on top of whatever you're installing it on. Lubuntu is a full featured distro, an Ubuntu "flavor" and it includes the DE but it's not limited to the DE. And LXDE is now "old news", Lubuntu uses LXQt currently, ther old LXDE is a dead-end.

---

### Post by similar2 on 2020-04-04
You should give Bodhi Linux a spin.

---

### Post by jsinclair92 on 2020-04-07
Guys,
 
First off, thanks for the great responses!  You definitely gave me a lot to think about/research.  I ended up installing Lubuntu on my workshop laptop and love it!... So much so, that I am trying to install it on my tablet as well, but am running into some issues.  Should I create a new post or can we address that on this one?

Thanks again!!  I am really looking forward to the fresh new OS!

---

### Post by Artim on 2020-04-07
Make a new post, as specific as you can.  Lots of awesome folks here to help!

---

### Post by leok2 on 2020-04-10
Just curious - what version of Lubuntu did you install?

---

