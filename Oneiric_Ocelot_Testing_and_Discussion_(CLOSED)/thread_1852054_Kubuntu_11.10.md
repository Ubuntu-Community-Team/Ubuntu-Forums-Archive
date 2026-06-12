---
title: "Kubuntu 11.10"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PaulW2U on 2011-09-29
After today's updates and a reboot I'm finding that all Gnome/GTK applications no longer run. Application window opens and closes immediately.

Can anyone using Kubuntu 11.10 confirm?

I'd appreciate help in reporting this bug. :(

**[COLOR="Red"][Edit: thread title is obviously wrong!][/COLOR]**

---

### Post by cariboo on 2011-09-29
I fixed the title for you.

---

### Post by PaulW2U on 2011-09-29
> **cariboo907 said:**
> I fixed the title for you.

Thanks cariboo907, too much wine with my evening meal. :)

Applications tested that other users may well have installed are Thunderbird, Firefox, gVim, Emacs and Chrome.

Opera and Libreoffice do work though. :confused:

---

### Post by sumski on 2011-09-29
I don't have any issues with GTK apps. Whats the output if started from konsole?

---

### Post by PaulW2U on 2011-09-29
Starting gvim from a console produces:

```
paul@DELL:~$ gvim
gvim: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gdk_error_trap_pop_ignored

```

and emacs

```
paul@DELL:~$ emacs
emacs: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gdk_error_trap_pop_ignored

```

and firefox

```
paul@DELL:~$ firefox 
[NoScript] Adding category
[NoScript] Adding category
[NoScript] Adding category
[NoScript] Adding category
[NoScript] Adding category
[NoScript] Adding category
[NoScript] Adding category
[NoScript] Adding category
[NoScript] Adding category
/usr/lib/firefox-7.0.1/firefox: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gdk_error_trap_pop_ignored

```

and thunderbird

```
paul@DELL:~$ thunderbird
/usr/lib/thunderbird-7.0/thunderbird-bin: symbol lookup error: /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: undefined symbol: gdk_error_trap_pop_ignored

```

---

### Post by collisionystm on 2011-09-29
> /usr/lib/gtk-2.0/modules

Were your gtk modules updated to 3.0?

---

### Post by PaulW2U on 2011-09-29
> **collisionystm said:**
> Were your gtk modules updated to 3.0?
On the basis of the following output, yes

```
paul@DELL:~$ sudo aptitude show libgtk-3-0
Package: libgtk-3-0                      
State: installed
Automatically installed: no
Version: 3.2.0-0ubuntu1
Priority: optional

```

This is not looking good. :sad:

---

### Post by collisionystm on 2011-09-29
Reinstall firefox and see if it runs. Your programs are all looking for gtk-2.0 modules. They need to be reinstalled to point towards 3.0. Sorry mate... the joys of using beta software =/

---

### Post by PaulW2U on 2011-09-29
> **collisionystm said:**
> Reinstall firefox and see if it runs. Your programs are all looking for gtk-2.0 modules. They need to be reinstalled to point towards 3.0. Sorry mate... the joys of using beta software =/

Not a problem, just disappointed that at the stage where my bug reports were being acknowledged and fixed that I came across this just a couple of weeks before release.

Anyway, I reinstalled Firefox, gVim and emacs, no change. :confused:

---

### Post by collisionystm on 2011-09-29
Hmm... I wonder where Kubuntu is pulling the software from for gnome? Maybe it is still grabbing old gnome 2 versions for some reason?

---

### Post by FerroPower on 2011-09-29
I am also facing EXACT bug
cannot open Chromium or Firefox I posting this info from Songbird inbuilt browser. 

Please help I too updated my system hour back now gtk based softwares dont work even Deluge is not working.

---

### Post by apfejes on 2011-09-29
Having the same problem in Kubuntu as well.  Wondering if this has something to do with one of the Kubuntu default settings pointing non kde towards gtk2 libs instead of 3.

(For the record, Oneiric has been one steady thrashing of non-gnome programs after the other, so I'm not surprised by this turn of events at all...)

---

### Post by apfejes on 2011-09-29
My theory failed. Chaning the GTK+ syles for gtk apps in kde did not help. 

I suspect we'll have to wait for a recompile of all the apps that point to libcanberra-gtk-modules.so.

---

### Post by apfejes on 2011-09-29
Also note - there is a bug filed on this:

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862553]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862553")

---

### Post by PaulW2U on 2011-09-29
> **apfejes said:**
> Also note - there is a bug filed on this:

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862553]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/862553")
Thank you apfejes, I hadn't got around to looking at Launchpad. I've added my "me too".

---

### Post by apfejes on 2011-09-29
And here's the workaround, for the moment:

Download [https://launchpad.net/ubuntu/oneiric/amd64/libcanberra-gtk-module/0.28-0ubuntu8]("https://launchpad.net/ubuntu/oneiric/amd64/libcanberra-gtk-module/0.28-0ubuntu8")

install it from the command line:

sudo dkpg -i libcanberra-gtk-module_0.28-0ubuntu8_amd64.deb

That will replace the buggy version 0.28-0ubuntu9, and GTK windows will work again.

---

### Post by FerroPower on 2011-09-29
> **apfejes said:**
> And here's the workaround, for the moment:

Download [https://launchpad.net/ubuntu/oneiric/amd64/libcanberra-gtk-module/0.28-0ubuntu8](https://launchpad.net/ubuntu/oneiric/amd64/libcanberra-gtk-module/0.28-0ubuntu8)

install it from the command line:

sudo dkpg -i libcanberra-gtk-module_0.28-0ubuntu8_amd64.deb

That will replace the buggy version 0.28-0ubuntu9, and GTK windows will work again.


BIG THANKS !! man it works like charm thanks 
btw that command you gave dont work in my PC I directly double **click **on the file it ran installer and got installed. !!

---

### Post by apfejes on 2011-09-29
> **FerroPower said:**
> BIG THANKS !! man it works like charm thanks 
btw that command you gave dont work in my PC I directly double on the file it ran installer and got installed. !!

The command will only work if you're in the same directory as the file you downloaded (or if you give the path to the file), but it seems you got it to work anyhow, so it's all good.

Cheers

---

