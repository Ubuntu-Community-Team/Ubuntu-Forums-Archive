---
title: "HowTo: Gaim to the latest version with autopackage"
date: 2005-04-16
forum: Outdated Tutorials &amp; Tips
---

### Post by soul_rebel on 2005-04-16
If you want the latest Gaim version, without messing dependencies and using .deb packages for plugins, this is for you.

remove gaim and gaim-data, regardless of ubuntu-desktop being removed too.

get this dummy package and install it with dpkg -i
[http://soulrebel.altervista.org/gaim-dummy_99.0_all.deb](http://soulrebel.altervista.org/gaim-dummy_99.0_all.deb)

install gaim using autopackage from gaim website.

install again ubuntu-desktop and gaim plugins. (Some of them could need some tweaking.)

Now it's up to you to mantain gaim on your system, but it is all up to getting a new autopackage from gaim website when gaim's update notifier pops up.

Please handle with care.

---

### Post by kuleali on 2005-04-16
nice, guide

---

### Post by rykel on 2005-05-31
hi rebel,

i just have 2 questions...

1.   i am using the gaim 1.3.0 autopackage, but i kept the ubuntu gaim-data, thinking tat the autopackage "might" have some use for it... does it matter?

2.   wat is the logic behind the dummy package, and re-installing the ubuntu-desktop/gaim plugins etc.?


best regards,

rykel

ps. i love autopackage!

---

### Post by pdk001 on 2005-05-31
i got an error message after typing "sudo dpkg -i gaim-dummy_99.0_all.deb

pdk001@ubuntu:~$ sudo dpkg -i gaim-dummy_99.0_all.deb
dpkg: regarding gaim-dummy_99.0_all.deb containing gaim-dummy:
 gaim-dummy conflicts with gaim-gnome
  gaim provides gaim-gnome and is installed.
dpkg: error processing gaim-dummy_99.0_all.deb (--install):
 conflicting packages - not installing gaim-dummy
Errors were encountered while processing:
 gaim-dummy_99.0_all.deb

---

### Post by rykel on 2005-07-06
Hi guys,

I did a simple thing.

I fully uninstalled Gaim using Synaptic Package Manager (right-click and choose **"Mark for complete removal"**), and then installed the latest version with its [autopackage](http://www.autopackage.org)  file.

Autopackage is really the easy way to install programs in Linux - just click and run like you do in Windows XP.

---

### Post by rendi on 2005-08-14
link is death guy wget [http://soulrebel.altervista.org/gaim-dummy_99.0_all.deb](http://soulrebel.altervista.org/gaim-dummy_99.0_all.deb)
--21:22:52--  [http://soulrebel.altervista.org/gaim-dummy_99.0_all.deb](http://soulrebel.altervista.org/gaim-dummy_99.0_all.deb)
           => `gaim-dummy_99.0_all.deb'
Resolving soulrebel.altervista.org... 67.15.6.91
Connecting to soulrebel.altervista.org[67.15.6.91]:80... connected.
HTTP request sent, awaiting response... 404 Not Found
21:22:54 ERROR 404: Not Found.
  ](*,)

---

### Post by xodeus on 2005-08-14
Reply to post #1

 Can you please make a step by step thing with codes and so on in code boxes??

Really confusing.

---

### Post by soul_rebel on 2005-08-14
I just started to think that this way of doing it it's wrong! It's a dirty hack and can cause problems. I can't support it anymore. This is beacause links are dead. 
I am really unhappy about ubuntu not updating packages after stable release.... search for backports or debian packages...
Sorry guys.

---

### Post by rykel on 2005-08-14
Hi friends,

Great news!!

**Gaim 1.5.0** [autopackage](http://www.autopackage.org) (the latest) is now officially available! Click [here](http://gaim.sourceforge.net/downloads.php) to download.

---

### Post by xodeus on 2005-08-14
[QUOTE=rykel]Hi friends,

Great news!!

**Gaim 1.5.0** [autopackage](http://www.autopackage.org) (the latest) is now officially available! Click [here](http://gaim.sourceforge.net/downloads.php) to download.[/QUOTE]
 Please explain step by step about this autopackage setup of gaim.

---

### Post by ghostintheshell on 2005-08-14
[QUOTE=xodeus]Please explain step by step about this autopackage setup of gaim.[/QUOTE]

I always install Gaim from source :razz: but following the links I fall on this web page:
[http://autopackage.org/docs/howto-install/index.html]("http://autopackage.org/docs/howto-install/index.html")

Just read it :wink:

[EDIT] Check this demo: [http://autopackage.org/flash-demo-install.html](http://autopackage.org/flash-demo-install.html) !! :grin:[/EDIT]

---

### Post by Lizzy on 2005-08-14
Hmm??? Looks nice, but which package i'm a supposed to download???
Sorry for the stupid question... it's all Red-Hat, Mandrake, Windows??? Where is Debian/Ubuntu??? 
I would love to have the new gAIM, since i'm constantly receiving the message that i should have the new version!! But this download thing is a little too much for me  :roll: !

Step by step..plz  :grin:

---

### Post by ghostintheshell on 2005-08-14
[QUOTE=Lizzy]Hmm??? Looks nice, but which package i'm a supposed to download???
Sorry for the stupid question... it's all Red-Hat, Mandrake, Windows??? Where is Debian/Ubuntu??? 
I would love to have the new gAIM, since i'm constantly receiving the message that i should have the new version!! But this download thing is a little too much for me :roll: !

Step by step..plz  :grin:[/QUOTE]


I don't think the windows package will help you :wink:
the autopackage for gAIM is [there]("http://gaim.sourceforge.net/downloads.php") -> Gaim 1.5.0 ([size=4]**[Autopackage]("http://prdownloads.sourceforge.net/gaim/gaim-1.5.0.x86.package?download")**[/size])
don't care about other packages!!!
go directly to the [size=4]**[Autopackage]("http://prdownloads.sourceforge.net/gaim/gaim-1.5.0.x86.package?download")**[/size] section 
the autopackage system is distros independant ("*universal*")

_**How to install Linux autopackages in 4 easy steps**_

**Step 1: Download & save**

              Download the packages you want to install and save them on your computer.
         Go to the folder where you saved the software package to.

**Step 2: Open Properties dialog**

                  Click on the package with your *right mouse button*.
         Then click on the *Properties* menu item.

**Step 3: Enable permissions**

                  Go to the *Permissions* tab.
         Check the *Execute, Exec or Is Executable* checkbox.         If there are more than one *Execute/Exec* checkboxes, check the top-most one.
                    Click *Close* or *OK*, depending on the dialog.

 **Step 4: Uninstall previous and open**

 If you already have the software installed from your distributions packages or from the source, remove it first. Then *open* the package file.     

         If you are asked whether you want to display or run the package, click *Run*.     

**Done**

The installation will now begin. Follow further intructions that are displayed on the screen, if any. You only have to follow these instructions once. Next time, you can just skip step 1-4 and open the .package file directly.

   ***Instructions for commandline users***

  (If you have followed the graphical instructions above, then you don't need to follow these instructions.)




[list=1]
[*]Download the packages you want to install and save them on your computer.
[*]Open a terminal and go to the folder in which you saved the package:  ```
[bash@localhost]$ cd YourDownloadsFolder
/home/example/YourDownloadsFolder
[bash@localhost]$ _
```
[*]Run the package with the following command  ```
[bash@localhost]$ bash Example.package
```
[*]You're done! Follow further instructions on screen, if any.
[/list]*_source:_ [http://autopackage.org/docs/howto-install/index.html]("http://autopackage.org/docs/howto-install/index.html")*

I can do anything more for you guy. I don't use autopackage, I compile gAIM from sources ( apparently easier :cool: ). I just write you what I read :razz:

Good luck!

---

### Post by rykel on 2005-08-15
[QUOTE=xodeus]Please explain step by step about this autopackage setup of gaim.[/QUOTE]

our friend above explained it very well. well, verbatim from the autopackage website.  :) 

anyway, in a nutshell:

1. download the gaim.package. (don't bother with Redhat RPM watever)

2. make it "executable" (one time only... follow the 4-step instructions given by ghostintheshell)

3. double-click on the icon and it's done.

---

### Post by Fummie on 2005-08-15
[QUOTE=ghostintheshell] the autopackage for gAIM is [there]("http://gaim.sourceforge.net/downloads.php") -> Gaim 1.5.0 [/QUOTE]
Thanks for your guide, that worked a treat.  :)

---

### Post by ghostintheshell on 2005-08-15
[QUOTE=Fummie]Thanks for your guide, that worked a treat.  :)[/QUOTE]

You make my day :grin:

Also, while surfin' the autopackage web site, I found a list with all available packages working with the autopackage system:

[http://autopackage.org/packages/](http://autopackage.org/packages/)

nvu, the gimp, gaim, abiword, inkscape, firefox, amsn, ... not so bad!

If you like this system, think about subscribe to the rss feed!
You can do it with Firefox (you'll see an icon in the right bottom corner).

Also, do not hesitate to surf this web site: they did/do a great job.

Enjoy.

---

### Post by Maxkekaxke on 2005-08-15
Hmm, 
after I installed it, I can't select my guifications anymore... :???:

---

### Post by ghostintheshell on 2005-08-15
[QUOTE=Maxkekaxke]Hmm, 
after I installed it, I can't select my guifications anymore... :???:[/QUOTE]

Hi, 

I can't help you, perhaps someone else will do it.

But I propose to you to post your question/issue on the autopackage forum, here: [http://autopackage.org/forums/index.php](http://autopackage.org/forums/index.php)

Personaly, I use guifications too but I compile it from sources just after compiling gAIM from sources. So, any idea about this autopackage issue ...

Good luck.

---

### Post by Lizzy on 2005-08-15
Thanks ever so much," ghostintheshell", i would like every program to be installed as easy as this one  :grin:  !! Thx again   :grin: 
What would i do without the help this forum ??!!

---

### Post by ghostintheshell on 2005-08-15
[QUOTE=Lizzy]Thanks ever so much," ghostintheshell", i would like every program to be installed as easy as this one  :grin:  !! Thx again   :grin: 
What would i do without the help this forum ??!![/QUOTE]

you're welcome ;-)

don't forget to take a look at all available (auto)packages:
[http://www.autopackage.org/packages/](http://www.autopackage.org/packages/)

if you meet a issue or have a more specific question about autopackage, do not hesitate to talk about it on the official forum: [http://www.autopackage.org/forums/index.php](http://www.autopackage.org/forums/index.php)

enjoy.

---

### Post by taktu on 2005-08-30
hi guys, i followed the instructions from this thread and also autopackage.org's instructions but i can't seem to finish the installation. i keep geting this error:

"The autopackage support code could not be installed.
 It can be manually downloaded and installed by running the installation script located in the downloaded archive."
 ](*,) 
i tried downloading the file manually from their website but i got the same result (or lack of).

Please help.

EDIT: this is the actual error:
"/dev/shm/autopackage.1244621497/meta/@gaim.sourceforge.net/gaim:1.5.0/apkg-downloader: line 543: autopackage/libexec/autosu-gtk: cannot execute binary file"

hope that helps

---

### Post by LaSSarD on 2005-08-30
guys, **is there any way to keep my gaim configurations when i install the autopackage?** as you know, when you work with **debs**, you can **update** it and the **configurations** will me **maintained**. does **autopackage works in the same way?**

---

### Post by taktu on 2005-08-31
[QUOTE=taktu]hi guys, i followed the instructions from this thread and also autopackage.org's instructions but i can't seem to finish the installation. i keep geting this error:

"The autopackage support code could not be installed.
 It can be manually downloaded and installed by running the installation script located in the downloaded archive."
 ](*,) 
i tried downloading the file manually from their website but i got the same result (or lack of).

Please help.

EDIT: this is the actual error:
"/dev/shm/autopackage.1244621497/meta/@gaim.sourceforge.net/gaim:1.5.0/apkg-downloader: line 543: autopackage/libexec/autosu-gtk: cannot execute binary file"

hope that helps[/QUOTE]
 never mind my post. i made the n00best of all mistakes which i am to ashamed to mention.

---

### Post by rykel on 2005-08-31
[QUOTE=taktu]never mind my post. i made the n00best of all mistakes which i am to ashamed to mention.[/QUOTE]

i was just going to attempt to answer ur post when i read ur last statement... just curious, taktu, wat was the most newbie mistake u made?

as for the configurations, yes, the IMs themselves (such as yahoo messenger, msn, icq etc.) seem to keep a record of ur buddies, and gaim config/log files can be found in ~/.gaim. (ie. the hidden ".gaim" folder in ur HOME)

hope tat helps!!

---

### Post by taktu on 2005-08-31
[QUOTE=rykel]just curious, taktu, wat was the most newbie mistake u made?[/QUOTE]

well... here goes nothing:
installing (at least trying to) the x86 version on PPC  #-o  ](*,) 

so there: tattooed 'n00b' on my forehead after this one
kill me please!

---

### Post by rykel on 2005-09-01
[QUOTE=taktu]well... here goes nothing:
installing (at least trying to) the x86 version on PPC  #-o  ](*,) 

so there: tattooed 'n00b' on my forehead after this one
kill me please![/QUOTE]


   haha, OK, i see ur point... well, it happens to all of us at one point.   :)

---

