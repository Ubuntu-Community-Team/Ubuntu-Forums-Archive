---
title: "Midori (manual build/install) missing in app menu"
date: 2012-09-19
forum: Packaging and Compiling Programs
---

### Post by MElawe on 2012-09-19
Hello all,

For the past few hours I’ve been installing libs I need for the Midori web browser to compile, finally I got it to work and installed it. Prob is, its not in the App Dash. It is installed to: /usr/local/share/midori.

Any help would be much appreciated. :popcorn:

-Mel

---

### Post by GeForce 9500GT on 2012-09-19
:confused: Midori can be found in the repo's, why building it up from scratch?

---

### Post by MElawe on 2012-09-19
The one in the Ubuntu software centre is outdated and has a flash bug(very bad for my gaming time :P ).

---

### Post by vasa1 on 2012-09-19
Just a thought without any practical knowledge ...
What happens if you make it into a .deb package and then install it via the Software Center (by right-clicking on the .deb)? Won't it then show up properly in all the right places in Unity?

---

### Post by MElawe on 2012-09-19
> **vasa1 said:**
> Just a thought without any practical knowledge ...
What happens if you make it into a .deb package and then install it via the Software Center (by right-clicking on the .deb)? Won't it then show up properly in all the right places in Unity?

I would think a .deb file is simply everything packaged together, something like a .exe installer for Windows. If it is so, that wont fix it, that is guessing that the programmer decided where it was going to be installed, and not Ubuntu, if however, Ubuntu is deciding where it will be installed, .deb should do it and I would guess it would be possible to do so in the terminal install.

Edit: I don't know how to make .deb files. :/

---

### Post by MElawe on 2012-09-19
Anyone got a small or big light bulb?:KS

---

### Post by vasa1 on 2012-09-19
As I said, I don't have any first-hand knowledge but see this:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
> Installing the Package

If everything works well and you want to install the program just type:

sudo checkinstall

This creates a .deb file using CheckInstall which makes removing the package at a later stage very easy.


---

### Post by vasa1 on 2012-09-19
> **MElawe said:**
> I would think a .deb file is simply everything packaged together, something like a .exe installer for Windows. If it is so, that wont fix it, ... if however, Ubuntu is deciding where it will be installed, .deb should do it ...
That's why I felt that letting the Software Center "install" the .deb would get "Ubuntu" to recognize that new software has been added and to update its records accordingly which would include getting the "Dash" to "see" it.

BTW, I've installed Midori from here: [s][http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu)[/s]

Better url: [https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa) from [http://ubuntuforums.org/showpost.php?p=12249695&postcount=12](http://ubuntuforums.org/showpost.php?p=12249695&postcount=12)

---

### Post by MElawe on 2012-09-19
> **vasa1 said:**
> As I said, I don't have any first-hand knowledge but see this:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)


Hmm, will take sometime to install and test it all out. I'd learn a lot but need to do some web dev for now. :/  If you could tell me which file to edit or something like that(just a tid bit less time consuming), it would be wonderful. Thanks for looking around for the link though. 

Thanks for taking the time to look for it though, but its seams I'll have to spend a lot of time to get everything for the .deb file, might be the solution but already spent a day on it which was supposed to be spent on web development. I will surly try it sometime, but not today. :/ That said thanks for the link, I'm a programmer and it will be handy when I have something to add to the software center. :)

-Mel

---

### Post by MElawe on 2012-09-19
> **vasa1 said:**
> That's why I felt that letting the Software Center "install" the .deb would get "Ubuntu" to recognize that new software has been added and to update its records accordingly which would include getting the "Dash" to "see" it.

BTW, I've installed Midori from here: [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu)

Could be true, but no time to test it. :/ Took a one day worth of computer time already, but def something to try when bored or in mood to try something different. :KS

Where did your version install to?

---

### Post by vasa1 on 2012-09-20
> **MElawe said:**
> ...
Where did your version install to?
I'm leaving out the stuff in /home and most entries from /usr/share/locale/
```

/usr/bin/midori
/usr/include/midori-0.4
/usr/include/midori-0.4/extensions
/usr/include/midori-0.4/extensions/external-download-manager.h
/usr/include/midori-0.4/extensions/history-list.h
/usr/lib/midori
/usr/lib/midori/libadblock.so
/usr/lib/midori/libaddons.so
/usr/lib/midori/libcolorful-tabs.so
/usr/lib/midori/libcookie-manager.so
/usr/lib/midori/libcopy-tabs.so
/usr/lib/midori/libexternal-download-manager.so
/usr/lib/midori/libfeed-panel.so
/usr/lib/midori/libformhistory.so
/usr/lib/midori/libhistory-list.so
/usr/lib/midori/libmouse-gestures.so
/usr/lib/midori/libshortcuts.so
/usr/lib/midori/libstatus-clock.so
/usr/lib/midori/libstatusbar-features.so
/usr/lib/midori/libtab-panel.so
/usr/lib/midori/libtabs-minimized.so
/usr/lib/midori/libtoolbar-editor.so
/usr/lib/midori/libweb-cache.so
/usr/share/midori
/usr/share/app-install/desktop/midori:midori-private.desktop
/usr/share/app-install/desktop/midori:midori.desktop
/usr/share/app-install/icons/midori.png
/usr/share/applications/midori-private.desktop
/usr/share/applications/midori.desktop
/usr/share/bug/midori
/usr/share/bug/midori/presubj
/usr/share/doc/midori
/usr/share/doc/midori/AUTHORS
/usr/share/doc/midori/EXPAT
/usr/share/doc/midori/README
/usr/share/doc/midori/README.Debian
/usr/share/doc/midori/TODO.Debian
/usr/share/doc/midori/changelog.Debian.gz
/usr/share/doc/midori/changelog.gz
/usr/share/doc/midori/copyright
/usr/share/doc/midori/faq.css
/usr/share/doc/midori/faq.html
/usr/share/icons/elementary/apps/24/midori.svg
/usr/share/icons/elementary/apps/48/midori.svg
/usr/share/icons/hicolor/16x16/apps/midori.png
/usr/share/icons/hicolor/22x22/apps/midori.png
/usr/share/icons/hicolor/24x24/apps/midori.png
/usr/share/icons/hicolor/32x32/apps/midori.png
/usr/share/icons/hicolor/48x48/apps/midori.png
/usr/share/icons/hicolor/scalable/apps/midori.svg
/usr/share/locale/en_GB/LC_MESSAGES/midori.mo
/usr/share/man/man1/midori.1.gz
/usr/share/menu/midori
/usr/share/midori/res
/usr/share/midori/res/about.css
/usr/share/midori/res/autosuggestcontrol.css
/usr/share/midori/res/autosuggestcontrol.js
/usr/share/midori/res/close.png
/usr/share/midori/res/error.html
/usr/share/midori/res/logo-shade.png
/usr/share/midori/res/speeddial-head-0.4.6.html
/usr/share/xfce4/helpers/midori.desktop
/var/cache/apt/archives/midori_0.4.6-1~precise~ppa1_i386.deb
/var/lib/dpkg/info/midori.conffiles
/var/lib/dpkg/info/midori.list
/var/lib/dpkg/info/midori.md5sums
/var/lib/dpkg/info/midori.postinst
/var/lib/dpkg/info/midori.postrm
/var/lib/dpkg/info/midori.preinst
/var/lib/dpkg/info/midori.prerm
[11:52 AM] ~ $ 

```

---

### Post by GeForce 9500GT on 2012-09-20
Maybe this can be helpfull: [Midori PPA]("https://launchpad.net/~midori/+archive/ppa"). No worries about compiling stuff or converting packages.

---

### Post by vasa1 on 2012-09-20
> **GeForce 9500GT said:**
> Maybe this can be helpfull: [Midori PPA]("https://launchpad.net/~midori/+archive/ppa"). ...
This was the link I used! I'm editing my earlier post to reflect that.

---

### Post by MElawe on 2012-09-20
Is it latest version? And updated when there are new versions?

---

### Post by vasa1 on 2012-09-20
> **MElawe said:**
> Is it latest version? And updated when there are new versions?
You should be able to find out from the links provided.

---

### Post by MElawe on 2012-09-21
> **vasa1 said:**
> You should be able to find out from the links provided.

Is this the one for 12.04(0.4.6-1~precise~ppa1) or all work for 12.04? I'm new to Ubuntu and don't know anything about ppa's. I added a few ones but never got to install the programs I wanted, do they come int the updates manager?

I found where th executable file of Midori is located, /usr/local/bin I'm using Midori for this post and all is working well, except for two things. One as you know, its not in the dash board, and two, its already one version outdated. Lol. I'm using 4.6, and now there is 4.7.

---

### Post by vasa1 on 2012-09-21
> **MElawe said:**
> ... its already one version outdated. Lol. I'm using 4.6, and **now there is 4.7**.
Interesting! I'm sure it will be available via ppa in a few days.

---

### Post by vasa1 on 2012-09-21
> **MElawe said:**
> ...
I found where th executable file of Midori is located, /usr/local/bin ...
How did you search for it?
I used the "locate" command which shows it under /usr/bin, not /usr/local/bin. 

The thing that puzzles me that when I navigate, **via the file manager**, to /usr/bin, there's no midori there. And my /usr/local/bin appears empty!

When I use the terminal, ls shows midori in /usr/bin! And /usr/local/bin is still empty (even with ls -a).

Weird!
[center]***[/center]
Also, when you say "One as you know, its not in the dash board," this is Unity's dash? What happens when you type **midori**?

Edit: I don't see midori in /usr/bin with PCManFM 0.9.10 but I do see it with Thunar !!!

---

### Post by MElawe on 2012-09-21
> **vasa1 said:**
> 

How did you search for it?
I used the "locate" command which shows it under /usr/bin, not /usr/local/bin. 

The thing that puzzles me that when I navigate, **via the file manager**, to /usr/bin, there's no midori there. And my /usr/local/bin appears empty!

When I use the terminal, ls shows midori in /usr/bin! And /usr/local/bin is still empty (even with ls -a).

Weird!





I saved the output when I run the install command, and try to track it down. I used the default file manager, but opened it as root(although I can see the file in none admin account with out root privileges). 

> **vasa1 said:**
> 
[center]***[/center]
Also, when you say "One as you know, its not in the dash board," this is Unity's dash? What happens when you type **midori**?

Edit: I don't see midori in /usr/bin with PCManFM 0.9.10 but I do see it with Thunar !!!

Yes I mean the Unity dashboard. This is very strange, but it seams once I run the Midori from /usr/local/bin, it found its way in the dashboard. It wasn't there after I installed it, but is there after running it.

So that problem is solved(*pat on the back for doing it successfully* :P ). So that leaves me with one problem, updating it. Do you get updates from the ppa you use?
I like to get latest updates asap, see whats new and try it out, try new things, etc. :)

---

### Post by vasa1 on 2012-09-21
> **MElawe said:**
> ... So that leaves me with one problem, updating it. Do you get updates from the ppa you use?
Yes, you will get updates from the ppa.> I like to get latest updates asap, see whats new and try it out, try new things, etc. :)
Well, AFAICT, the Midori team is pretty small. If you want "new and shiny" in a browser, you could consider getting on the the [Firefox Aurora channel]("http://www.mozilla.org/en-US/firefox/channel/#aurora"). You'll get nightly updates.
Or, you could go for the [dev channel of Google Chrome]("http://dev.chromium.org/getting-involved/dev-channel"). Quite a lot of action [there]("http://googlechromereleases.blogspot.com/") too.

---

### Post by MElawe on 2012-09-21
> **vasa1 said:**
> Yes, you will get updates from the ppa.
Well, AFAICT, the Midori team is pretty small. If you want "new and shiny" in a browser, you could consider getting on the the [Firefox Aurora channel]("http://www.mozilla.org/en-US/firefox/channel/#aurora"). You'll get nightly updates.
Or, you could go for the [dev channel of Google Chrome]("http://dev.chromium.org/getting-involved/dev-channel"). Quite a lot of action [there]("http://googlechromereleases.blogspot.com/") too.

All I want is updates as soon as they are out. Nightly is a little too dangerous for Ubuntu perhaps, at least not for the installation I do my programming on and family uses. It took a while to get them to agree to getting Ubuntu, so I'd rather not toy to much with this installation. Though I got another installation on this PC for crazy stuff, everyone needs a lil freedom, aye? :)

---

### Post by vasa1 on 2012-09-23
0.47 is available.

---

### Post by MElawe on 2012-10-01
Hmm, still has some flash problems. :/

---

