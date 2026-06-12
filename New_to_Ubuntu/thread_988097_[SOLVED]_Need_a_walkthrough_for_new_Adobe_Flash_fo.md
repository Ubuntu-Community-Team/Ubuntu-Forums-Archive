---
title: "[SOLVED] Need a walkthrough for new Adobe Flash for 64bit"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-11-20
Hi Guys,

Any chance getting an idiot proof, SBS, walkthrough (including commands to cut and paste) for installing the new Adobe Flash plug in for 64 bit Linux?

I tried but do not know what and how to remove, copy or create...

Cheers,

Udi

---

### Post by bumanie on 2008-11-20
[Follow this]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html"). It's done via a self installing script

---

### Post by steveneddy on 2008-11-20
From this thread:

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

First
1. Open a terminal and execute the following commands for removal of old plugins. Some may error out saying they cant find a file, that's ok. We just want to make sure they are removed if they exist.

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
sudo apt-get purge flashplugin-nonfree
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```


Then install the .so file that you will get after you unpack it to the following folders:

```
/usr/lib/mozilla/plugins/

/usr/lib/firefox-addons/plugins/
```


That should do it.

It is important to uninstall all of the old flash stuff before trying to install the new flash.

You can 

```
gksudo nautilus
```

to open up a root window to make it a click and drop function if you like.

---

### Post by Udibuntu on 2008-11-20
> **bumanie said:**
> [Follow this]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html"). It's done via a self installing script

Uhhm, thanks, but this is for flash under 64 bit Ubuntu, I think, am I right?

What I need is the new **Adobe** Flash plugin for 64bit Linux.

Udi

---

### Post by philinux on 2008-11-20
64 bit uses nspluggin-wrapper and flashplugin-nonfree. Just install from synaptic.

Or

sudo apt-get install ubuntu-restricted-extras
one stop shop.

---

### Post by Udibuntu on 2008-11-20
Hi,

It seems I wasn't clear about what I need, so:

I'm already running Flash plugin for 64bit Ubuntu, per Kilz's guide.

What I'm asking is a walkthrough for installing Adobe's new Flash plugin for 64bit Linux.

I've seen threads about it but I don't know how to actually do what their advising.

Cheers,

Udi

---

### Post by philinux on 2008-11-20
They've only got a 32 bit version out. 64 bit version is a bit off yet.
There's is an alpha.
[http://arstechnica.com/news.ars/post/20081117-adobe-starts-64-bit-flash-testing-with-linux-alpha.html](http://arstechnica.com/news.ars/post/20081117-adobe-starts-64-bit-flash-testing-with-linux-alpha.html)
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by Udibuntu on 2008-11-20
> **philinux said:**
> They've only got a 32 bit version out. 64 bit version is a bit off yet.
There's is an alpha.
[http://arstechnica.com/news.ars/post/20081117-adobe-starts-64-bit-flash-testing-with-linux-alpha.html](http://arstechnica.com/news.ars/post/20081117-adobe-starts-64-bit-flash-testing-with-linux-alpha.html)
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Yep, that's the one.

What I need the step by step commands are for this:

> All I had to do was ... put the .so file in the Firefox plugin's directory.

I (hope I) can decompress the .so and remove previous plugins, but the above is obscure for me.

Cheers Philinux,

Udi

---

### Post by philinux on 2008-11-20
libflashplayer.so is really all you need. Probable replace the current one with it.

Find where it is now.

locate libflashplayer.so

I would uninstall previous flash via synaptic etc.

---

### Post by Udibuntu on 2008-11-20
Uninstalled per first reply, extracted per download instructions.

How do I proceed? What do I paste into the terminal?

---

### Post by Udibuntu on 2008-11-20
YES!!!

Did it!!

Dragged and dropped the .so file, after sudo nautilus, to usr/lib64/firefox-addons/plugins

Works great, no grey boxes even with 2 tabs running flash!

Hope it keeps that way!!

Thanks all,

Udi

---

### Post by Keen101 on 2008-11-20
Adobe has just released adobe alpha 64bit version

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

EDIT:    oops. I hadn't read the whole thread. I guess you got it then.

---

### Post by steveneddy on 2008-11-20
> **Udibuntu said:**
> YES!!!

Did it!!

Dragged and dropped the .so file, after sudo nautilus, to usr/lib64/firefox-addons/plugins

Works great, no grey boxes even with 2 tabs running flash!

Hope it keeps that way!!

Thanks all,

Udi

One small bit of advice.

When using sudo graphically, call it by

**gksudo** *command*

instead of just

**sudo** *command*

it will keep you from copying a file to a folder and not seeing it because of root permissions.

Glad you got Flash working.

---

### Post by Udibuntu on 2008-11-22
> **steveneddy said:**
> One small bit of advice.

When using sudo graphically, call it by

**gksudo** *command*

instead of just

**sudo** *command*

it will keep you from copying a file to a folder and not seeing it because of root permissions.

Glad you got Flash working.

Thank you, I didn't know that.

I'm going to Google a little on "terminal use for dummies"; I think I aught to start somewhere...

Cheers,

Udi

---

