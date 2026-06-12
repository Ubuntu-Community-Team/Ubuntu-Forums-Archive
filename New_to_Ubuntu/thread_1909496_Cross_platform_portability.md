---
title: "Cross platform portability"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by learning_ubu on 2012-01-15
Total newbie here. Just starting to explore Ubuntu. I use Windows (XP, Vista, 7) and Mac OS at work/home.

Is it possible to have an instance of Ubuntu on a thumb drive and run it from within a window on Windows/Mac/Other Linux? Not booting from the thumb drive but running Ubuntu like an application itself.

My thought is functionality like but for more than Windows:
[http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows](http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows)

If I can build that on a thumb drive I can carry an Ubuntu instance with me consistently across platforms. Right now I can do it with a VMWare image but that requires the their environment - at least the player on Windows and full Fusion on the Mac. Not likely that I can get administrator access to install player on all Windows machines I use or getting Fusion for any Mac I use.

Any chance to use Ubuntu like a "portable app"? Even a portable app player for each platform that would launch the same instance of Ubuntu would work.

Thoughts?

---

### Post by Double.J on 2012-01-15
Hi there and welcome to the forums!

To answer your question, to the best of my knowledge you're already doing this the best way. After all Ubuntu is a full featured desktop OS, even using a live USB has limitations - you have to use a special read only compressed filesystem to fit it on small sticks. You can of course do an install on a USB stick, but then you still wouldn't be able to run inside Windows or OS X without another application... if such a thing existed!

You can move the virtual machine around on a USB? But for what it seems you are wanting to do, running it inside a virtual machine through VMWare or Vbox is probably the best way to go?

Sorry :( Hope someone else comes up with something more useful!

---

### Post by Mark Phelps on 2012-01-16
Basically -- no.  

To run it inside any other OS, you would need a VM of some kind -- which you already are using.

---

### Post by WasMeHere on 2012-01-16
It is not exactly what you ask for but it can be convenient to carry a persistent live system on a USB flash drive (stick). Look at the following system by *sudodus*

[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

Such a system can be configured as you like (for example some application programs and your favourite web bookmarks) and you can have copies of important private files.

---

### Post by mastablasta on 2012-01-16
Ubuntu is an operating system not an application. it is a portable operating system as you can stuck the live media in a PC and it would boot (command line if nothing else).
 
it can be carried across platforms which include PC, tablets, smartphones, TV, routers, Mac's, gaming consoles...

---

### Post by Mark Phelps on 2012-01-16
My bad, should have mentioned that Linux OSs are much more portable than Windows OS.  There's no activation required, and hardware detection is done automatically.

But, a portable OS does not run "within a window ..." as you first asked; instead, you can boot to the USB drive and run the OS from it.

---

