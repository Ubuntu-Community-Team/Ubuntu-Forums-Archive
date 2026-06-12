---
title: "OzOS Talk"
date: 2007-11-26
forum: Other OS Talk
---

### Post by RAV TUX on 2007-11-26
> **Rui Pais]
Hi all,

As you may know I've been put things together to make oz-desktop The DE of OZ OS.

I will resume here the main objectives of it:
[font=Verdana][font=Verdana][color=blue][b]The idea is to do a "dynamic iso". It will be based on Ubuntu, use Ubuntu software 
(wheel was one of the 1st mankind invention and its may be already patented  said:**
> [/color][/font][/font]
For now i have made a first operational sketch of the oz-desktop. 
It's for tests only (although with a little of apt-get commands, some tweaks and you can make it as functional as you wish or even a turn it into a plain Ubuntu install)

So What i ask is to anyone with the desire of test and play with, with time and a little free space, may want to give it a try and give us feedback, suggestions, problems, the usual ...

There is no installer or  iso for now. Just a procedure:

**1)** Download and burn iso for an Ubuntu base, minimalCD (9M) [[from here](https://help.ubuntu.com/community/Installation/MinimalCD)]

**2)** Reboot from it and pass option: **cli**  (on boot command line)
[size=8pt]      (Gutsy its buggy till the end of fur, but on minimal CD it's pure wild life!!
       Toke me 2 hours of despair till i discover that at least cli work)[/size]

**3)** Reboot to it. And add our repos to sources list:
    You can do it by hand:
    ```
sudo nano -w /etc/apt/sources
``` 
   and add those lines:
    **deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) scarecrow main contrib**
    **deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main contrib**

    or simply enter (be careful [color=orange]typos can ruin your sources.list!![/color]):
    ```
 sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os scarecrow main contrib' >> /etc/apt/sources.list"
```
    ```
 sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os tinwoodman main contrib' >> /etc/apt/sources.list"
```

**4)** Update:
    ```
sudo apt-get update
```

**5)** Install: (repeat on ewl failures if needed):
    ```
sudo apt-get install e17-cvs oz-desktop
```
or for a light version:
    ```
sudo apt-get install e17-cvs oz-desktop-light
```

**6)** Start X and  play around:
     ```
sudo /etc/init.d/gdm restart
```

Here it uses 1.9G of disk space for the oz-desktop.
It's very basic at the moment, and maybe a bit ugly. :lol: but you can tune it as usual.

Default important apps:  abiword, firefox, gimp, pokerth, scite, thunar, xfce-terminal.
Default apps of light version:  abiword (no plugins), kazehakaze, scite, thunar, xfce-terminal.
Extra creatures:  stalonetray, xscreensaver.

I add some pics of the default session.

Tell me your issues, questions, lists of bugs...
Give your suggestions and generic comments in this other thread:
[http://cafelinux.org/forum/index.php/topic,906.0.html](http://cafelinux.org/forum/index.php/topic,906.0.html)

Till Wednesday i will not probably have time to work on new versions, after that i will try to make things more stable and do an extra packages.

keep happy all, 
Rui




[[IMG]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_OzOs_0%28Rui_Pais_Screenshot.png[/IMG]]("http://www.cafelinux.org/OptickleArt/displayimage.php?pos=-352")

[[IMG]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_OzOs_1%28Rui_Pais_Screenshot.png[/IMG]]("http://www.cafelinux.org/OptickleArt/displayimage.php?pos=-351")

[[IMG]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_OzOs_2%28Rui_Pais_Screenshot.png[/IMG]]("http://www.cafelinux.org/OptickleArt/displayimage.php?pos=-350")

[[IMG]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_OzOs_3%28Rui_Pais_Screenshot.png[/IMG]]("http://www.cafelinux.org/OptickleArt/displayimage.php?pos=-349")

[[IMG]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_OzOs_4%28Rui_Pais_Screenshot.png[/IMG]]("http://www.cafelinux.org/OptickleArt/displayimage.php?pos=-348")


[http://cafelinux.org/forum/index.php/topic,907.0.html](http://cafelinux.org/forum/index.php/topic,907.0.html)

OzOs is a CafeLinux.org Team Development, I speak for all Team members when I welcome and encourage all to help us out to test and refine OzOs.

For a list of CafeLinux.org Developments see the [CafeLinux.org  Homepage]("http://www.cafelinux.org/home/").

Also take a quick look at our [ToDo List]("http://cafelinux.org/home/?q=node/2") and [Downloads]("http://www.cafelinux.org/Downloads/")(more to come) ;)

Here is a quick list of the CafeLinux.org Team:

>   The CaféLinux.org Team

 Jozef (RAV TUX) - USA (DC in route to Portland, Oregon) - Core Founder of CaféLinux.org
Paul (Aubrey, Tux Aubrey) - Australia - Core Founder of CaféLinux.org
Arthur (Arty, A to the O) - USA (Maryland) - Core Founder of CaféLinux.org
Chanuch (Chanuch) - USA (Maryland) - Lead CafeLinux.org Legal Admin.(Lawyer)
Tom (bodhi.zazen) - USA (Montana) - Primary "Root" Server Admin. of CaféLinux.org & Lead Technical Admin. of CaféLinux.org
Rui (Rui Pais) - Portugal - Lead Dev. "Development Division" Admin. of CaféLinux.org(Lead Dev. of OZ OS)
Lothar (Lotodore) - Germany - Technical Admin. of CaféLinux.org(Network Dev. of PokerTH)
Felix (doitux) - Germany - Technical Admin. of CaféLinux.org(Webmaster & Dev. of PokerTH)
Christopher (devilhorns) -  USA - Technical Admin. of CafeLinux.org(Enlightenment Dev. & Core Dev. of OZ OS)
Carsten (Raster, Rasterman)   - Taiwan/Australia - Technical Admin. of CaféLinux.org(Lead Dev. of Enlightenment & OpenMoko)
Nicholas (mekius) - USA(Wisconsin in route to Illinois) - Technical Admin. of CaféLinux.org(Lead Dev. of gOS & Dev. of Enlightenment)
Master Goodheart (MasterGH) - Australia - Technical Admin. of CafeLinux.org(Core Dev. of OZ OS)
Colton (C J Pro) - USA (Pennsylvania) - Technical Admin. of CaféLinux.org
Jacob (Jacob) - USA (Ohio) - Technical Admin. of CaféLinux.org
Steve (Vorian, Duncan) - USA (Ohio) - Technical Admin. of CaféLinux.org[http://cafelinux.org/home/?q=node/1](http://cafelinux.org/home/?q=node/1)

As you can see we have many projects that we are involved in and support, our primary objective is to help and advance Linux and Open Source projects and help out when and where needed. Small upstart projects are our speciality, we have become like an incubator or farm if you will. The CafeLinux.org Team strives to make a difference in the Future of Linux and Open Source, The Future Now.

Please let us know if you can help or need help with any Linux or Open Source project.

...and as Rui Pais has posted [OzOs needs testers]("http://cafelinux.org/forum/index.php/topic,907.0.html").

Have a Happy Day,

Jozef

---

### Post by n3tfury on 2007-11-26
looks real nice.  i might give this a shot this weekend.

---

### Post by Flyingjester on 2007-11-26
downloading now :D

---

### Post by machoo02 on 2007-11-26
Building e17 inside of Virtualbox as we type....

---

### Post by p_quarles on 2007-11-26
> **machoo02 said:**
> Building e17 inside of Virtualbox as we type....
Ditto. I look forward to playing around with this, and will do my best to write useful feedback.

---

### Post by RAV TUX on 2007-11-26
> **n3tfury said:**
> looks real nice.  i might give this a shot this weekend.

> **Flyingjester said:**
> downloading now :D

> **machoo02 said:**
> Building e17 inside of Virtualbox as we type....

> **p_quarles said:**
> Ditto. I look forward to playing around with this, and will do my best to write useful feedback.

This is awesome I am glad to see everybody trying OzOs out ;)

Here is an update the downloads can found here now:

[http://www.cafelinux.org/Downloads/oz-os/pool/main/](http://www.cafelinux.org/Downloads/oz-os/pool/main/)


 [IMG]http://www.cafelinux.org/icons/folder.gif[/IMG][ e/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/e/") 26-Nov-2007 14:54 

 [IMG]http://www.cafelinux.org/icons/folder.gif[/IMG][ o/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/") 26-Nov-2007 14:54    

specifically:

[e17-cvs_0.0-4.1_all.deb]("http://www.cafelinux.org/Downloads/oz-os/pool/main/e/e17-cvs/e17-cvs_0.0-4.1_all.deb")26-Nov-2007 14:55  2.3M

[oz-desktop-light_0.02_all.deb]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop-light/oz-desktop-light_0.02_all.deb")26-Nov-2007 14:55  321K

[oz-desktop_0.02_all.deb]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop/oz-desktop_0.02_all.deb")26-Nov-2007 14:56  1.2M

---

### Post by -grubby on 2007-11-26
using it, but not now. RAV TUX, all windows are transparent and so is the panel, this happened after I enabled the eye-candy (can't remember the specific name)
EDIT: what I mean specifically is that all windows and the panel are too transparent to see; in fact, they don't even look like windows

---

### Post by RAV TUX on 2007-11-26
> **nathangrubb said:**
> using it, but not now. RAV TUX, all windows are transparent and so is the panel, this happened after I enabled the eye-candy (can't remember the specific name)Not sure what you mean here?

Do you mean a theme?

---

### Post by -grubby on 2007-11-26
> **RAV TUX said:**
> Not sure what you mean here?

Do you mean a theme?

I mean that all windows are like, transparent but I don't see anything like window borders it's just looks like a giant piece of glass with a shadow. The desktop works fine (the theme and all) and the icons are OK. I'll try to get a screenshot to show you what I mean if you still are confused

---

### Post by RAV TUX on 2007-11-26
Here's a snapshot of my current OzOs:

[[IMG]http://www.cafelinux.org/OptickleArt/albums/userpics/normal_snapshot2%7E2.png[/IMG]]("http://www.cafelinux.org/OptickleArt/displayimage.php?pos=-354")

---

### Post by RAV TUX on 2007-11-26
> **nathangrubb said:**
> I mean that all windows are like, transparent but I don't see anything like window borders it's just looks like a giant piece of glass with a shadow. The desktop works fine (the theme and all) and the icons are OK. I'll try to get a screenshot to show you what I mean if you still are confused

Please post in this thread for Rui Pais to review:

[http://cafelinux.org/forum/index.php/topic,907.0.html](http://cafelinux.org/forum/index.php/topic,907.0.html)

---

### Post by -grubby on 2007-11-26
> **RAV TUX said:**
> Please post in this thread for Rui Pais to review:

[http://cafelinux.org/forum/index.php/topic,907.0.html](http://cafelinux.org/forum/index.php/topic,907.0.html)

I will get a screenshot and then post in that thread

---

### Post by RAV TUX on 2007-11-26
> **nathangrubb said:**
> I will get a screenshot and then post in that thread

Thanks that will help Rui out immensely

---

### Post by -grubby on 2007-11-26
> **RAV TUX said:**
> Thanks that will help Rui out immensely

that's weird, I can't get a screenshot and when I click on your apt:ozos link it says I dont' have it installed

---

### Post by -grubby on 2007-11-26
> **nathangrubb said:**
> that's weird, I can't get a screenshot and when I click on your apt:ozos link it says I dont' have it installed

that's just funky. I tried installing it from your link and now it says "reinstall" ! I will delete my ./enlightenment folder to see if that fixes it

---

### Post by -grubby on 2007-11-26
> **nathangrubb said:**
> that's just funky. I tried installing it from your link and now it says "reinstall" ! I will delete my ./enlightenment folder to see if that fixes it

K that fixed it

---

### Post by init1 on 2007-11-26
Looks good, I'll have to try it out when I have the time. :D

---

### Post by RAV TUX on 2007-11-26
> **init1 said:**
> Looks good, I'll have to try it out when I have the time. :DI'll look forward to your feedback. ;)

---

### Post by Flying caveman on 2007-11-27
It seems to be doing something.

I wgetted the .debs oz,oz-light and e17 it from cafelinux

but I didn't gdebi the light version. 

Right now building 2/3 installing Libtaries

---

### Post by K.Mandla on 2007-11-27
Shifted to Other OS Talk.

---

### Post by Rui Pais on 2007-11-27
Hi All, 

sorry only now i post something here... but i've been very busy.

I'm very happy to announce that our repos are now available Smiley

    deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) scarecrow main contrib
    deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main contrib

If you just want to try e17-cvs use just the last tinwoodman fro the moment.
oz-desktops will be on scarecrow (to keep black things those away Smiley) until they get a little more "brains" ... Wink

[HERE are the link]("http://cafelinux.org/forum/index.php/topic,907.msg2509.html") for a complete refurbish of the install process of Oz OS. A light version is included.
From now own it's just apt-get, aptitude or synaptic. (No more gdbis needed)

Hope you like it.
Rui

---

### Post by Rui Pais on 2007-11-27
> **nathangrubb said:**
> that's just funky. I tried installing it from your link and now it says "reinstall" ! I will delete my ./enlightenment folder to see if that fixes it

> **nathangrubb said:**
> K that fixed it

Hi, only now i read this a see your issues... sorry you have to delete your personal confs (i presume that by .enlightenment you mean ~/.e)
Hope you haven't personalized a lot or you will have to do all by and hand... 
when that may be needed, remove .e, i suggest a simple mv for .e_BAK or somethink like to make more easy to recover settings if the move reveals useless or unneeded.

Your problem it's an e17 issue with rendering engine.
[See here]("http://cafelinux.org/forum/index.php/topic,894.msg2447.html#msg2447") how to workaround that, and some alternatives.

About the reinstall... thats what it's suppose to do. e17-cvs deb it's just a wrapper for the morlenxus script+saned install method of my sign... i opt for keep things at minimum, do reinstall the package only do a update of the script when an already existent installation is found.

Thanks a lot for your reports and comments. 
And for help us test this. :)

Rui

---

### Post by thecow on 2007-11-27
I am confused a bit, what is the difference between the Oz-desktop and e17.  I mean, what does OzOs add to it?
And also, I just installed a fresh version of ubuntu.  If I install this can I run it as a seperate session?  I mean when I login in, can I choose either the normal Gnome startup, or the new e17 startup?

---

### Post by Rui Pais on 2007-11-27
> **thecow said:**
> I am confused a bit, what is the difference between the Oz-desktop and e17.  I mean, what does OzOs add to it?
And also, I just installed a fresh version of ubuntu.  If I install this can I run it as a seperate session?  I mean when I login in, can I choose either the normal Gnome startup, or the new e17 startup?

Ok,
it's like gnome and ubuntu-desktop or kde and kubuntu-desktop

e17-cvs gives you the base DE (it's a Desktop Shell, but you get the idea...)

oz-desktop will be the future desktop default of Oz OS (an ubuntu based distro in build construction phase)

For a fresh ubuntu install just go for e17-cvs. oz-desktop it's for testing only purposes now.

Rui

---

### Post by thecow on 2007-11-27
Ah thanks.  So I should just apt-get install the e17 cvs files?  And then I can run it as a seperate session?

Edit: Ha Waiting for Godot eh

---

### Post by Rui Pais on 2007-11-27
> **thecow said:**
> Ah thanks.  So I should just apt-get install the e17 cvs files?  And then I can run it as a seperate session?

Yes, exactly.
Check here for tips and help: [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

Edit on edit:
Ahh for a moment i thought that you were referring the time i take to answer (i was lunching ;)) 
:lol:

Yes, what else are we doing here?
don't answer we know... waiting for Godot ;)

---

### Post by utUtu on 2007-11-27
I'm geting errors

```

--------------------------- Installing libraries (EFL) -------------------------
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- epeg ....................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... previously installed
- emotion .................... SKIPPED
- engrave .................... previously installed
- etk ........................ previously installed
- etk_extra .................. previously installed
- ewl ........................ ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
edje_cc: Wrote      5741 bytes (   6Kb) for "images/1" image entry "e17_gadman_overlay_right.png" compress: [raw: 90.1%] [real: -109.0%]
edje_cc: Wrote       660 bytes (   1Kb) for "images/2" image entry "e17_menu_bg.png" compress: [raw: 14.1%] [real: -312.5%]
edje_cc: Wrote      1492 bytes (   1Kb) for "collections/0" collection entry
Summary:
  Wrote 1 collections
  Wrote 3 images
  Wrote 0 fonts
  Wrote 710 bytes (1Kb) of original source data
  Wrote 0 bytes (0Kb) of original source font map
Conservative compression summary:
  Wrote total 14294 bytes (14Kb) from 5557 (5Kb) input data
  Output file is 257.2% the size of the input data
  Saved -8737 bytes (-8Kb)
Raw compression summary:
  Wrote total 14294 bytes (14Kb) from 116368 (114Kb) raw input data
  Output file is 12.3% the size of the raw input data
  Saved 102074 bytes (100Kb)
make[4]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes/ewl_embed_test'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/.e17_cvs/e17/libs/ewl'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/ewl.log'!


```

ewl.log

```

make[5]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes/e17'
make[4]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes/e17'
Making all in ewl_embed_test
make[4]: Entering directory `/root/.e17_cvs/e17/libs/ewl/data/themes/ewl_embed_t                             est'
edje_cc -v -id ../../../data/themes/ewl_embed_test/images ../../../data/themes/e                             wl_embed_test/ewl_embed_test.edc ../../../data/themes/ewl_embed_test/ewl_embed_t                             est.edj
Making all in images
make[5]: Entering directory `/root/.e17_cvs/e17/libs/ewl/data/themes/ewl_embed_t                             est/images'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes/ewl_embed_te                             st/images'
make[5]: Entering directory `/root/.e17_cvs/e17/libs/ewl/data/themes/ewl_embed_t                             est'
edje_cc -v -id ../../../data/themes/ewl_embed_test/images ../../../data/themes/e                             wl_embed_test/ewl_embed_test.edc ../../../data/themes/ewl_embed_test/ewl_embed_t                             est.edj
edje_cc: Error. unable to open "../../../data/themes/ewl_embed_test/ewl_embed_te                             st.edj" for writing output
edje_cc: Opening "/tmp/edje_cc.edc-tmp-w1Yv1h" for input
edje_cc: Parsing input file
edje_cc: Parsing done
make[5]: *** [ewl_embed_test.edj] Error 255
make[5]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes/ewl_embed_te                             st'
make[4]: *** [all-recursive] Error 1
make[4]: *** Waiting for unfinished jobs....
edje_cc: Opening "/tmp/edje_cc.edc-tmp-VrDSPh" for input
edje_cc: Parsing input file
edje_cc: Parsing done
edje_cc: Wrote       283 bytes (   0Kb) for "edje_file" header
edje_cc: Wrote      5408 bytes (   5Kb) for "images/0" image entry "e17_gadman_o                             verlay_left.png" compress: [raw: 90.6%] [real: -104.1%]
edje_cc: Wrote      5741 bytes (   6Kb) for "images/1" image entry "e17_gadman_o                             verlay_right.png" compress: [raw: 90.1%] [real: -109.0%]
edje_cc: Wrote       660 bytes (   1Kb) for "images/2" image entry "e17_menu_bg.                             png" compress: [raw: 14.1%] [real: -312.5%]
edje_cc: Wrote      1492 bytes (   1Kb) for "collections/0" collection entry
Summary:
  Wrote 1 collections
  Wrote 3 images
  Wrote 0 fonts
  Wrote 710 bytes (1Kb) of original source data
  Wrote 0 bytes (0Kb) of original source font map
Conservative compression summary:
  Wrote total 14294 bytes (14Kb) from 5557 (5Kb) input data
  Output file is 257.2% the size of the input data
  Saved -8737 bytes (-8Kb)
Raw compression summary:
  Wrote total 14294 bytes (14Kb) from 116368 (114Kb) raw input data
  Output file is 12.3% the size of the raw input data
  Saved 102074 bytes (100Kb)
make[4]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes/ewl_embed_te                             st'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data/themes'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/.e17_cvs/e17/libs/ewl/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/.e17_cvs/e17/libs/ewl'
make: *** [all] Error 2
root@ik6401:~# 

```

I recompiled twice and got the same error.
:confused:

---

### Post by Rui Pais on 2007-11-27
> **utUtu said:**
> I'm geting errors

```

...

```

I recompiled twice and got the same error.
:confused:

A very boring and persistent issue :(

Sorry you must retry 2 or 3 times till it continues (most people now are reporting that 3 seems to be the usual)

Good Luck

---

### Post by smartboyathome on 2007-11-27
> **nathangrubb said:**
> I mean that all windows are like, transparent but I don't see anything like window borders it's just looks like a giant piece of glass with a shadow. The desktop works fine (the theme and all) and the icons are OK. I'll try to get a screenshot to show you what I mean if you still are confused

You must have installed the Bling module (which is broken). You will have to navigate to /opt/e17/lib/enlightenment/modules, rename bling to bling.bkup, then start enlightenment. Now it will unload the module, and you can safely rename it back to the default (though I don't know why you would :p).

---

### Post by utUtu on 2007-11-27
> **Rui Pais said:**
> A very boring and persistent issue :(

Sorry you must retry 2 or 3 times till it continues (most people now are reporting that 3 seems to be the usual)

Good Luck

Indeed 3x works.  So far looking good, and posting this now from my OzOS 64bit.

It's very close to the newly released Elive, but pretty good and it's 64bit which elive doesn't have.

Thanks guys for the good job.
:guitar:

---

### Post by RAV TUX on 2007-11-27
> **utUtu said:**
> Indeed 3x works.  So far looking good, and posting this now from my OzOS 64bit.

It's very close to the newly released Elive, but pretty good and it's 64bit which elive doesn't have.

Thanks guys for the good job.
:guitar:Do you have a screenshot of your new 64bit OzOs?

---

### Post by utUtu on 2007-11-27
> **RAV TUX said:**
> Do you have a screenshot of your new 64bit OzOs?

Originally I only have CLI + Fluxbox and a few Netapps and audio apps.  
Once I get a screen capture I will.

OTOH, Htop is failing to start with 'stop unexpectedly' error message.??
I see the same messages with Exaile when I close it though.
:confused:

---

### Post by Masterizaak on 2007-11-27
While it was installing it came up with this error. does this mean e17  didnt install?

---

### Post by p_quarles on 2007-11-27
I was able to get everything up and running in Virtualbox (and it looks lovely, btw). The only problem I've had so far is that the poker game won't run. The message was something like "failed to initialize." 

If this is an unknown bug, I'll be happy to run it from the terminal and post the full output.

---

### Post by RAV TUX on 2007-11-28
> **p_quarles said:**
> I was able to get everything up and running in Virtualbox (and it looks lovely, btw). The only problem I've had so far is that the poker game won't run. The message was something like "failed to initialize." 

If this is an unknown bug, I'll be happy to run it from the terminal and post the full output.
It's very important that the PokerTh game run, so please post the full output here.

---

### Post by Rui Pais on 2007-11-28
> **utUtu said:**
> Indeed 3x works.  So far looking good, and posting this now from my OzOS 64bit.

It's very close to the newly released Elive, but pretty good and it's 64bit which elive doesn't have.

Thanks guys for the good job.
:guitar:

Yes thats the beauty of compile it at user box. It's for any arch :)

To do a screenshot you should have scrot installed (or can apt-get it). 
just type scrot on a command line or from 'Run command' on main menu. scrot -h will tell you other options, like name, format, delay ... you can use too.
And you can use e17 module screenshot.
We are still deciding which apps to include, and screenshots are one of them. 
(@RAV TUX probably we will go with one different for each flavour) 

> **utUtu said:**
> Originally I only have CLI + Fluxbox and a few Netapps and audio apps.  
Once I get a screen capture I will.

OTOH, Htop is failing to start with 'stop unexpectedly' error message.??
I see the same messages with Exaile when I close it though.
:confused:

That i don't know exactly... 
can you, please, post the exact output?
Have you done something that may have change configs after your last login?

you may try too to update (sudo easy_e17.sh -u) and see if it was soem bug on e code... i compiled a few minutes and everything is running.

Post the exact error message, ok?
Rui

---

### Post by Rui Pais on 2007-11-28
> **p_quarles said:**
> I was able to get everything up and running in Virtualbox (and it looks lovely, btw). The only problem I've had so far is that the poker game won't run. The message was something like "failed to initialize." 

If this is an unknown bug, I'll be happy to run it from the terminal and post the full output.

> **RAV TUX said:**
> It's very important that the PokerTh game run, so please post the full output here.

Well, after i made a deb for PokerTh, one of it's devs called my attention for the fact that there was already a deb for it on repos.

Thats a bug on the ubuntu packages, a typical one... 
ubuntu package set the executable on /usr/games/ but /usr/games/ it's on $PATH on Ubuntu by default :(

You can edit you $PATH (on /etc/environment) or do a ln of /usr/games/pokerth on /usr/bin.


@RAV TUX
I had an idea that i had already take care of that... but maybe i forget to upload or update the install script.
I will be out today for the all day, but at night i will give an eye on this one.

---

### Post by Rui Pais on 2007-11-28
> **Masterizaak said:**
> While it was installing it came up with this error. does this mean e17  didnt install?

That happens if e17-cvs compile/install fails, that probabilly means that it aborted previously compile e main app.

Maybe you are on ewl bug issue, yet. 
Have you checked my suggestion for utUtu on this thread?
repeat twice (or even 3 times) the sudo apt-get install e17-cvs... till it finishes successfully.


I have to leave now, at nigh i'll give a look on this.
Have a good day.
Rui

---

### Post by kazuya on 2007-11-28
this seems very nice and fun to say the least. I shall try it out. Now if i already have Ubuntu gutsy, can I just download or add your repos in synaptic or apt/atc/sources.list and install e17 or OzOS that way as compared to reinstalling with Ubuntu gutsy..

Good job again folks and RAvtux for bringing this to our attention.

EDIT: I think, I'll just experiemnt it anyways and see what happens. I have got the howto from cafelinux.. I'll report on how it goes.

---

### Post by Rui Pais on 2007-11-28
> **kazuya said:**
> this seems very nice and fun to say the least. I shall try it out. Now if i already have Ubuntu gutsy, can I just download or add your repos in synaptic or apt/atc/sources.list and install e17 or OzOS that way as compared to reinstalling with Ubuntu gutsy..

Good job again folks and RAvtux for bringing this to our attention.

EDIT: I think, I'll just experiemnt it anyways and see what happens. I have got the howto from cafelinux.. I'll report on how it goes.

Hi,
on e17-cvs part should be no problem, just read about the issue with ewl on this thread.

oz-desktop it's at very beginning and it's been mainly for tests. But it's essentially a xfce reduced, so the worst that can happen it's things don't works as you like and just remove it...

Please, tells us how it go.
Rui

---

### Post by Masterizaak on 2007-11-28
> **Rui Pais said:**
> That happens if e17-cvs compile/install fails, that probabilly means that it aborted previously compile e main app.

Maybe you are on ewl bug issue, yet. 
Have you checked my suggestion for utUtu on this thread?
repeat twice (or even 3 times) the sudo apt-get install e17-cvs... till it finishes successfully.


I have to leave now, at nigh i'll give a look on this.
Have a good day.
Rui

Well e17 seemed to have installed, i tried like 10 times :redface::
but when I tried install oz-desktop, it couldnt find it

---

### Post by RAV TUX on 2007-11-29
> **Masterizaak said:**
> Well e17 seemed to have installed, i tried like 10 times :redface::
but when I tried install oz-desktop, it couldnt find it

[http://www.cafelinux.org/Downloads/oz-os/pool/main/o/](http://www.cafelinux.org/Downloads/oz-os/pool/main/o/)

---

### Post by Masterizaak on 2007-11-29
> **RAV TUX said:**
> [http://www.cafelinux.org/Downloads/oz-os/pool/main/o/](http://www.cafelinux.org/Downloads/oz-os/pool/main/o/)

should I put that in sources?

---

### Post by RAV TUX on 2007-11-29
> **Masterizaak said:**
> should I put that in sources?
Those are OzOs Desktop Debs that you can install with the Gdebi Package Installer.

[oz-desktop-light_0.02_all.deb]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop-light/oz-desktop-light_0.02_all.deb")28-Nov-2007 22:22  321K

or

[oz-desktop_0.02.2_all.deb]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop/oz-desktop_0.02.2_all.deb")28-Nov-2007 22:22  1.2M

---

### Post by -grubby on 2007-11-29
> **Rui Pais said:**
> Hi, only now i read this a see your issues... sorry you have to delete your personal confs (i presume that by .enlightenment you mean ~/.e)
Hope you haven't personalized a lot or you will have to do all by and hand... 
when that may be needed, remove .e, i suggest a simple mv for .e_BAK or somethink like to make more easy to recover settings if the move reveals useless or unneeded.

Your problem it's an e17 issue with rendering engine.
[See here]("http://cafelinux.org/forum/index.php/topic,894.msg2447.html#msg2447") how to workaround that, and some alternatives.

About the reinstall... thats what it's suppose to do. e17-cvs deb it's just a wrapper for the morlenxus script+saned install method of my sign... i opt for keep things at minimum, do reinstall the package only do a update of the script when an already existent installation is found.

Thanks a lot for your reports and comments. 
And for help us test this. :)

Rui


I just saw this thread and I know this is a late reply, anyway, at least I didn't customize that much, it was indeed when I selected "bling"

---

### Post by p_quarles on 2007-11-29
> **RAV TUX said:**
> It's very important that the PokerTh game run, so please post the full output here.

> **Rui Pais said:**
> Well, after i made a deb for PokerTh, one of it's devs called my attention for the fact that there was already a deb for it on repos.

Thats a bug on the ubuntu packages, a typical one... 
ubuntu package set the executable on /usr/games/ but /usr/games/ it's on $PATH on Ubuntu by default :(

You can edit you $PATH (on /etc/environment) or do a ln of /usr/games/pokerth on /usr/bin.


@RAV TUX
I had an idea that i had already take care of that... but maybe i forget to upload or update the install script.
I will be out today for the all day, but at night i will give an eye on this one.
Okay, well I did try to boot up the VM again, and I was going to run pokerth from the term (even though I'm sure that Rui Pais' diagnosis is correct -- just a missing executable path) -- and it was unbelievably slow. It took longer than I had available just to boot (this was the first full bootup after installing e17 and OzOS-desktop). 

Anyway, I've given the VM 512 MB of RAM, which runs WinXP-SP2 very nicely, so it's not that. 

I think this may be a PEBKAC situation, since I mistakenly skipped one of the installation steps the first time around, and discovered this after the next step didn't work. That could explain things, and I'll go into more detail if it's helpful.

For what it's worth, though, I noticed that my installation is using the Ubuntu Studio usplash artwork. I figure that this could be due to one of the following things:
1) OzOS chose to use the Ubuntu Studio usplash
2) OzOS was deliberately based on Ubuntu Studio
3) One of the OzOS packages is unintentionally dependent on the Ubuntu Studio package
or 
4) The mistake I made during installation caused Ubuntu Studio to be installed

I mention this just because the slowness I experienced could very well be due to trying to run a low-latency kernel in a virtual machine. But, like I said, I will reinstall this weekend and see if I am able to get better results.

---

### Post by Rui Pais on 2007-11-30
> **p_quarles said:**
> Okay, well I did try to boot up the VM again, and I was going to run pokerth from the term (even though I'm sure that Rui Pais' diagnosis is correct -- just a missing executable path) -- and it was unbelievably slow. It took longer than I had available just to boot (this was the first full bootup after installing e17 and OzOS-desktop). 

Anyway, I've given the VM 512 MB of RAM, which runs WinXP-SP2 very nicely, so it's not that. 

I think this may be a PEBKAC situation, since I mistakenly skipped one of the installation steps the first time around, and discovered this after the next step didn't work. That could explain things, and I'll go into more detail if it's helpful.
Yes, it will, thanks.
PokerTH, should now work, after last update. I'm not familiar with VM, I will try to install that way and see if a get some serious slowdown.

> 
For what it's worth, though, I noticed that my installation is using the Ubuntu Studio usplash artwork. I figure that this could be due to one of the following things:
1) OzOS chose to use the Ubuntu Studio usplash
2) OzOS was deliberately based on Ubuntu Studio
3) One of the OzOS packages is unintentionally dependent on the Ubuntu Studio package
or 
4) The mistake I made during installation caused Ubuntu Studio to be installed

I mention this just because the slowness I experienced could very well be due to trying to run a low-latency kernel in a virtual machine. But, like I said, I will reinstall this weekend and see if I am able to get better results.

No it's simpler, this is a run of trial and tests... i was only testing another usplash other then default (i had problems installing different usplash on the past, and i wanted to check), since we haven't yet get much far on settle look and work on graphics, i just pick one random usplash of the ones less tested (neither default, kubuntu or xubuntu). ANd at the time we don't had repos yet, i had to chose one from ubuntu repos or impose another extra package to download, something i don't wanted...
But it's a base ubuntu beyond, and the kernel used it's the default ubuntu one.

Thanks for testing and gives us your thoughts and comments. They are well appreciated.

---

### Post by p_quarles on 2007-11-30
> **Rui Pais said:**
> Yes, it will, thanks.
PokerTH, should now work, after last update. I'm not familiar with VM, I will try to install that way and see if a get some serious slowdown.
Well, basically, I attempted to use dpkg instead of gdebi to install the two packages (because, well, it slipped my mind that gdebi handles dependencies). 

So, following the dependency error, I looked at the instructions again, saw the correct way to do it, and installed gdebi-core. This gave me a broken package error, which was repaired with apt-get -f install. 

I think this may have installed a lot of extra and unnecessary stuff. I'll know for sure after I reinstall.

> No it's simpler, this is a run of trial and tests... i was only testing another usplash other then default (i had problems installing different usplash on the past, and i wanted to check), since we haven't yet get much far on settle look and work on graphics, i just pick one random usplash of the ones less tested (neither default, kubuntu or xubuntu). ANd at the time we don't had repos yet, i had to chose one from ubuntu repos or impose another extra package to download, something i don't wanted...
But it's a base ubuntu beyond, and the kernel used it's the default ubuntu one.
Okay, so it's just the artwork. That makes sense. As I said, I think my dependency error resulted in fetching extra packages, so I wondered if the wrong kernel was one of them, but apparently not.

I'll let you know how it goes.

---

### Post by kazuya on 2007-11-30
I tried from Linux mint and got this error when I tried OzOs full

E: oz-desktop: subprocess post-installation script returned error exit status 1
It shows e17-cvs installed, but tries to update it and fails. any ideas.  do we need something else.

It seems to work fine for me though. I do not know what happened but I love this desktop so much. great work.

---

### Post by RAV TUX on 2007-12-01
> **kazuya said:**
> 

It seems to work fine for me though. I do not know what happened but I love this desktop so much. great work.

I'm glad to hear you like the OzOs desktop. ;)

---

### Post by RAV TUX on 2007-12-02
> **p_quarles said:**
> Well, basically, I attempted to use dpkg instead of gdebi to install the two packages (because, well, it slipped my mind that gdebi handles dependencies). 

So, following the dependency error, I looked at the instructions again, saw the correct way to do it, and installed gdebi-core. This gave me a broken package error, which was repaired with apt-get -f install. 

I think this may have installed a lot of extra and unnecessary stuff. I'll know for sure after I reinstall.


Okay, so it's just the artwork. That makes sense. As I said, I think my dependency error resulted in fetching extra packages, so I wondered if the wrong kernel was one of them, but apparently not.

I'll let you know how it goes.

I was just wondering how it is going for you?

---

### Post by Rui Pais on 2007-12-02
> **kazuya said:**
> I tried from Linux mint and got this error when I tried OzOs full

E: oz-desktop: subprocess post-installation script returned error exit status 1
It shows e17-cvs installed, but tries to update it and fails. any ideas.  do we need something else.

It seems to work fine for me though. I do not know what happened but I love this desktop so much. great work.

Great! 
Thanks for trying. Glad to hear it works on other variants other then Ubuntu.

About your error on oz-desktop, don't worry i just dealing with that (scripts act a little different when run by dpkg...) soon it will be fixed.
It's not a real problem (at worst it failed to copy default profile, and in that case it launchs your session with bling bling theme).
I'm glad you like it.
:)

---

### Post by Rui Pais on 2007-12-02
> **kazuya said:**
> I tried from Linux mint and got this error when I tried OzOs full

E: oz-desktop: subprocess post-installation script returned error exit status 1
It shows e17-cvs installed, but tries to update it and fails. any ideas.  do we need something else.

Hi again,
do you mind to try again to see if problem it's solved? 
```
sudo apt-get update
```
```
sudo apt-get install oz-desktop
```

thanks, 
Rui

---

### Post by p_quarles on 2007-12-02
> **RAV TUX said:**
> I was just wondering how it is going for you?
It works beautifully after reinstalling. Posting this message from it, incidentally. Haven't encountered any further problems, but will definitely report back if I do.

---

### Post by RAV TUX on 2007-12-02
> **p_quarles said:**
> It works beautifully after reinstalling. Posting this message from it, incidentally. Haven't encountered any further problems, but will definitely report back if I do.
Awesome do you have a screenshot? ;)

---

### Post by p_quarles on 2007-12-02
I will at some point. It looks like the default right now, and I definitely want to play around with theming it soon. Today has been consumed by bending Fluxbox to my will, though. :)

---

### Post by RAV TUX on 2007-12-02
> **p_quarles said:**
> I will at some point. It looks like the default right now, and I definitely want to play around with theming it soon. Today has been consumed by bending Fluxbox to my will, though. :)
Here is two great sources for e17 themes:

[http://www0.get-e.org/](http://www0.get-e.org/)

[http://www.e17-stuff.org/index.php?xcontentmode=7000&PHPSESSID=91776ea3f0bb80f2fb57d00e84397616](http://www.e17-stuff.org/index.php?xcontentmode=7000&PHPSESSID=91776ea3f0bb80f2fb57d00e84397616)

The best are by Rui Pais of course and can be found here:

[http://cafelinux.org/forum/index.php/topic,885.0.html](http://cafelinux.org/forum/index.php/topic,885.0.html)

---

### Post by McDuff on 2007-12-04
hi!
i'm currently trying to install oz-desktop-light in a virtual machine. installation aborts wirh an error saying it couldn't create those hardlinks:
/home/georg/oz-desktop to directory /home/georg/.
/home/georg/.e to directory /home/georg/./.e
/home/georg/.local to directory /home/georg/./.local
i will try now to install oz-desktop

---

### Post by smartboyathome on 2007-12-04
I think that happened because of bad coding. Good catch. ;)

---

### Post by kazuya on 2007-12-04
> **Rui Pais said:**
> Hi again,
do you mind to try again to see if problem it's solved? 
```
sudo apt-get update
```
```
sudo apt-get install oz-desktop
```

thanks, 
Rui

I shall try it tonight when I get back home. thanks again.

---

### Post by kelvin spratt on 2007-12-05
you need to copy paste the sources to the apt sources file i used a live CD opened the file in root paste saved the rebooted the minimal gutsy, login then sudo apt-get update. then sudo apt-get install bla bla bla. No errors remember it takes a long time to setup and ideally needs to be left alone to do its stuff.
[IMG]http://ubuntuforums.org/g/images/264885/1_2007-12-04-233739.png[/IMG]

---

### Post by Rui Pais on 2007-12-05
> **McDuff said:**
> hi!
i'm currently trying to install oz-desktop-light in a virtual machine. installation aborts wirh an error saying it couldn't create those hardlinks:
/home/georg/oz-desktop to directory /home/georg/.
/home/georg/.e to directory /home/georg/./.e
/home/georg/.local to directory /home/georg/./.local
i will try now to install oz-desktop

Hi sorry about that problem. I workaround that on base oz-desktop but oz-desktop-light still needs changes. 
I need to do a better approach to default profiles, anyway... 
I will try to update soon with that annoyance removed.
Thanks for call my attention to that (few testers of the light version :))
Rui

---

### Post by kazuya on 2007-12-05
apt-get worked great for me. Running fine here.
EDIT: The system runs very well. It is very fast, elegant, but taking me sometime to get the hang of totally radifying the look. It works and looks beautifully. I could almost convert to it totally. You can even use the icon themes from working gnome DE on it. Now next is to learn how to install new icons, etc.. and how to add more items to the ibox or ibar . - some stuff i tried to add did not have icons for them. very few, but in all wonderful.

Also, how do I make the browser fonts or total look smaller to be able to see more of the page. I would almost like to increase the resolution slightly.

---

### Post by smartboyathome on 2007-12-06
Are you using Firefox or Opera (or something else)? If you are using Firefox, just use control+scrollwheel down to make the fonts smaller.

Also, you may have to search through /usr/share/icons in order to find one for your program.

---

### Post by Rui Pais on 2007-12-06
> **kazuya said:**
> apt-get worked great for me. Running fine here.
EDIT: The system runs very well. It is very fast, elegant, but taking me sometime to get the hang of totally radifying the look. It works and looks beautifully. I could almost convert to it totally. You can even use the icon themes from working gnome DE on it. Now next is to learn how to install new icons, etc.. and how to add more items to the ibox or ibar . - some stuff i tried to add did not have icons for them. very few, but in all wonderful.

Hi. 
Glad you like it :)

Some tips. 
cons can belong to gtk themes (you can install new ones simply by decompress the themes to folder ~/.icons, nothing to do with e17) or e17 specific ones (folder ~/.e/e/icons)  Check some here:
[http://www0.get-e.org/Resources/Animated_Icons/](http://www0.get-e.org/Resources/Animated_Icons/)
or here:
[http://e17-stuff.org/index.php?xcontentmode=7070](http://e17-stuff.org/index.php?xcontentmode=7070)

ibar can be configured by mouse left click: Configuration -> Configuration Panel -> Applications ->IBar Applications.

Another way it's to click on icon of the running app (top of the window, usually on the left) and choose Add to Launcher-> Default or Add to Favorite Menu (the one on mouse right click). 

If you dont have an icon for it you can add your own: 
Right click on icon of running app, choose Edit Icon, and just pic your favorite icon :)

ibox it's the module that shows your minimized apps ;)



Just one thing? do you have menus available on your Mouse left click: Menu -> Applications? or it's empty?
Rui

---

### Post by RAV TUX on 2007-12-06
> **kazuya said:**
> apt-get worked great for me. Running fine here.
EDIT: The system runs very well. It is very fast, elegant, but taking me sometime to get the hang of totally radifying the look. It works and looks beautifully. I could almost convert to it totally. You can even use the icon themes from working gnome DE on it. Now next is to learn how to install new icons, etc.. and how to add more items to the ibox or ibar . - some stuff i tried to add did not have icons for them. very few, but in all wonderful.

I am glad to hear that you like OzOs, the elegant easy stable e17 ubuntu based OS. ;)

---

### Post by neonl on 2007-12-07
Rui, my friend, I'm glad to inform you that I created a thread about Oz @ techzone. Please [visit here]("http://www.techzonept.com/showthread.php?t=218334").

Abraço, Rui.

---

### Post by Rui Pais on 2007-12-07
> **neonl said:**
> Rui, my friend, I'm glad to inform you that I created a thread about Oz @ techzone. Please [visit here]("http://www.techzonept.com/showthread.php?t=218334").

Abraço, Rui.

Thanks a lot Rui, i should have done that a long time, but complete forget (to much threads to look...)

I will post something and answer question there.
Thanks. Um abraço.

Rui

---

### Post by justin whitaker on 2007-12-07
That's one beautiful desktop. So it's just sever+enlightenment?

---

### Post by Rui Pais on 2007-12-07
Hello All

**[COLOR="Blue"]I'm glad to announce that finally Oz received a major upgrade (and bugs smash).[/COLOR]**

I am intended to try a fresh install this afternoon, but an insidious bug that i've been warned on another thread keep me testing so time was enough... but i think it must install with the usual procedure.
If you have previous installed ****it's highly recommended an update****.

This pre-release highlights:
[LIST]
[*] - No more 'Human.xml not found' warnings.
[*] - No more peach/pinky backgrounds at logins
[*] - Add/use some default OzOS gdm themes 
 (artwork at this time it's just as sketch, since we are still defining Oz OS look)
[*] - Better management of default profile
[*] - Default profile sticks for any new user add to system 
[*] - Solved a bad bug related with format: 'font: "Sans:style=Bold,Edje-Vera-Bold"' on themes,
that cause legends/captions on modules to disappear (thanks to kelvin spratt, for call my attention to that).
[*] - Solved (same issue) absence of desktop icons when that option was turned on.
[/LIST]

To update it's recommended that:
```
sudo aptitude purge e17-cvs
sudo apt-get update
sudo apt-get install e17-cvs oz-desktop

```or
```
sudo apt-get install e17-cvs oz-desktop-light
```
 
Good luck and give me your feedback.
Rui

---

### Post by neonl on 2007-12-07
> **Rui Pais said:**
> Thanks a lot Rui, i should have done that a long time, but complete forget (to much threads to look...)

I will post something and answer question there.
Thanks. Um abraço.

Rui

Ok, no worries. I'm afraid it won't be very successfully most of the good linuxers @ TZ use either gnome or *box and don't want to change.

> **justin whitaker said:**
> That's one beautiful desktop. So it's just sever+enlightenment?

It is neither server (it's standard edition but only with a basic system) nor only enlightenment, you can load whatever you want to.

> **Rui Pais said:**
> Hello All

**[COLOR="Blue"]I'm glad to announce that finally Oz received a major upgrade (and bugs smash).[/COLOR]**

I am intended to try a fresh install this afternoon, but an insidious bug that i've been warned on another thread keep me testing so time was enough... but i think it must install with the usual procedure.
If you have previous installed ****it's highly recommended an update****.

This pre-release highlights:
[LIST]
[*] - No more 'Human.xml not found' warnings.
[*] - No more peach/pinky backgrounds at logins
[*] - Add/use some default OzOS gdm themes 
 (artwork at this time it's just as sketch, since we are still defining Oz OS look)
[*] - Better management of default profile
[*] - Default profile sticks for any new user add to system 
[*] - Solved a bad bug related with format: 'font: "Sans:style=Bold,Edje-Vera-Bold"' on themes,
that cause legends/captions on modules to disappear (thanks to kelvin spratt, for call my attention to that).
[*] - Solved (same issue) absence of desktop icons when that option was turned on.
[/LIST]

To update it's recommended that:
```
sudo aptitude purge e17-cvs
sudo apt-get update
sudo apt-get install e17-cvs oz-desktop

```or
```
sudo apt-get install e17-cvs oz-desktop-light
```
 
Good luck and give me your feedback.
Rui

I'll try. I'm not using Oz @ the moment, I'm using Ubuntu standard installed from 64 bits' liveCD and with e17-cvs over. I'm using Oz from a VM though.

I'll post feedback (installing from fresh @ VM).

---

### Post by RAV TUX on 2007-12-08
> **Rui Pais said:**
> Hello All

**[COLOR=Blue]I'm glad to announce that finally Oz received a major upgrade (and bugs smash).[/COLOR]**

I am intended to try a fresh install this afternoon, but an insidious bug that i've been warned on another thread keep me testing so time was enough... but i think it must install with the usual procedure.
If you have previous installed ****it's highly recommended an update****.

This pre-release highlights:[LIST]
[*] - No more 'Human.xml not found' warnings.
[*] - No more peach/pinky backgrounds at logins
[*] - Add/use some default OzOS gdm themes 
 (artwork at this time it's just as sketch, since we are still defining Oz OS look)
[*] - Better management of default profile
[*] - Default profile sticks for any new user add to system
[*] - Solved a bad bug related with format: 'font: "Sans:style=Bold,Edje-Vera-Bold"' on themes,
that cause legends/captions on modules to disappear (thanks to kelvin spratt, for call my attention to that).
[*] - Solved (same issue) absence of desktop icons when that option was turned on.[/LIST]To update it's recommended that:
```
sudo aptitude purge e17-cvs
sudo apt-get update
sudo apt-get install e17-cvs oz-desktop

```or
```
sudo apt-get install e17-cvs oz-desktop-light
```Good luck and give me your feedback.
RuiRui Pais you have created the most beautiful and most stable e17 desktop with OzOs!

You are an artist and a genius ;)

OzOs is simply awesome and a dream come true!

I invite all to try OzOs and experience the true beauty and stability of e17 & Ubuntu.

This kind of e17 reality is only possible through the most discriminating e17 user. Rui Pais is the most discriminating e17 user I know! He brings to you a beautiful reality. This is different from any other e17 Debian based derivative...give it a try and see.

OzOs "A Reality Different"

---

### Post by neonl on 2007-12-08
> **RAV TUX said:**
> Rui Pais you have created the most beautiful and most stable e17 desktop with OzOs!

You are an artist and a genius ;)

OzOs is simply awesome and a dream come true!

I invite all to try OzOs and experience the true beauty and stability of e17 & Ubuntu.

This kind of e17 reality is only possible through the most discriminating e17 user. Rui Pais is the most discriminating e17 user I know! He brings to you a beautiful reality. This is different from any other e17 Debian based derivative...give it a try an see.

OzOs "A Reality Different"

Yeah, that's true! I know Rui and that you say it's true (must be an inherent quality to people named Rui :D).

Oz it's really good, now you only need a CD image.

Regards,

Rui

---

### Post by init1 on 2007-12-08
I finally tried OzOS last night and ran into a few problems. The first thing I notices was that my keyboard didn't seem to be mapped correctly. For example, when I pressed the "p" key, it displayed "*". This only happens when I log into e17, it's not an issue for GDM or the terminal. Next, I tried to fix it by activating the new user module. Now every time I login, it asks for a language to use, but there is nothing to choose. I see no way out of it. 
Beyond that, I was impressed the GDM theme, and the over all appearance of the distro.

---

### Post by Rui Pais on 2007-12-08
RAV TUX, neonl :popcorn:

[COLOR="Silver"](you make me :oops: guys)[/COLOR]

___________________________________-

> **init1 said:**
> I finally tried OzOS last night and ran into a few problems. The first thing I notices was that my keyboard didn't seem to be mapped correctly. For example, when I pressed the "p" key, it displayed "*". This only happens when I log into e17, it's not an issue for GDM or the terminal. Next, I tried to fix it by activating the new user module. Now every time I login, it asks for a language to use, but there is nothing to choose. I see no way out of it. 
Beyond that, I was impressed the GDM theme, and the over all appearance of the distro.

uhmm... maybe xorg failed to create xorg.conf correctly... Check if you have your keyboard language correctly set on /etc/X11/xorg.conf. Do you use English or other language?

whats the output of:
```
cat .dmrc
```

Sorry, what do you mean by new user module?

---

### Post by RAV TUX on 2007-12-08
> **init1 said:**
> I finally tried OzOS last night and ran into a few problems. The first thing I notices was that my keyboard didn't seem to be mapped correctly. For example, when I pressed the "p" key, it displayed "*". This only happens when I log into e17, it's not an issue for GDM or the terminal. Next, I tried to fix it by activating the new user module. Now every time I login, it asks for a language to use, but there is nothing to choose. I see no way out of it. 
Beyond that, I was impressed the GDM theme, and the over all appearance of the distro.try main menu>configuration>configuration panel>keyboard & mouse

---

### Post by neonl on 2007-12-08
Hello.

I installed fresh @ a virtual machine and everything went okay,

Is it on purpose that it isn't customized anymore? If so too bad, I won't be able to copy some tweaks I was interested in :).

---

### Post by Rui Pais on 2007-12-08
> **neonl said:**
> Hello.

I installed fresh @ a virtual machine and everything went okay,

Is it on purpose that it isn't customized anymore? If so too bad, I won't be able to copy some tweaks I was interested in :).

Oh... i see what the problem is. 
Silly me. 1st user it's done when oz-desktop it's not installed yet... so Oz default profile has not been applied ... It will only for new users add *a posteriori*.

I will correct that on next update. Sorry about the inconvenience.

Meanwhile just do from a console:
```
cp -a /etc/skel/.e ~/
cp -a /etc/skel/.local ~/
cp -a /etc/skel/.gtkrc-2.0 ~/
```

Rui

---

### Post by Rui Pais on 2007-12-08
New update 0.03.1

highlight:
[LIST]
[*]default profile to 1st user too (will change to Rusted soon)
[*] don't overlap profile if one already exist 
[*] tango icons by default (will change soon)
[*] ipv6 turned off (requires reboot)
[*] turn off transparency of systray (still looks bad :()
[/LIST]

---

### Post by neonl on 2007-12-08
Uhmm it's going more and more interesting...

Today it's a bit late and I'm tired of computers but tomorrow I'll check on those updates.

Good night (people who are near the Greenwich meridian) or cya (people who aren't) ;)

---

### Post by stalker145 on 2007-12-09
Now this looks like a good way to spend my time. Not that I know anything about coding, but I sure as hell can break things ;)

I'm installing as we speak in VirtualBox and was wondering if it's me, the fact that it's a VM, or if the install really is this slow. I've been patiently going for about 2 hours now. 

I had the requisite dump straight off, but everything seems to be installing well as I have yet to notice any in-your-face errors.

I look forward to helping if I can.

---

### Post by init1 on 2007-12-09
> **stalker145 said:**
> Now this looks like a good way to spend my time. Not that I know anything about coding, but I sure as hell can break things ;)

I'm installing as we speak in VirtualBox and was wondering if it's me, the fact that it's a VM, or if the install really is this slow. I've been patiently going for about 2 hours now. 

I had the requisite dump straight off, but everything seems to be installing well as I have yet to notice any in-your-face errors.

I look forward to helping if I can.
Yeah it's slow. But it's worth it ;)

---

### Post by stalker145 on 2007-12-09
> **init1 said:**
> Yeah it's slow. But it's worth it ;)

Thanks. I'm just glad to hear that I'm not doing it wrong ;)

---

### Post by init1 on 2007-12-09
I've reinstalled OzOs and still have that odd keyboard problem. I use a standard US keyboard. This issue seems to be related to GDM, because it only happens when I log into a session with GDM. Any ideas?

---

### Post by kazuya on 2007-12-10
Hello Rav and Rais, and others on this Oz-desktop project. is there a chance i could run this desktop in a slackware equivalent like Vector Linux or zenwalk or even wolvix..

I am currently running Vector Linux on an older 256 MB machine, it runs like a dream even with kde environment, but I am itching to have a desktop like oz or e17-cvs on there as well to test performance..
Great job again folks..

My only gripe is not knowing how to adjust the desktop scrren resolution to be 1280X1024 instead of 1024X768; like I could do in gnome or kde? I  do not know where you would set that in?

---

### Post by smartboyathome on 2007-12-10
> **kazuya said:**
> Hello Rav and Rais, and others on this Oz-desktop project. is there a chance i could run this desktop in a slackware equivalent like Vector Linux or zenwalk or even wolvix..

I am currently running Vector Linux on an older 256 MB machine, it runs like a dream even with kde environment, but I am itching to have a desktop like oz or e17-cvs on there as well to test performance..
Great job again folks..

My only gripe is not knowing how to adjust the desktop scrren resolution to be 1280X1024 instead of 1024X768; like I could do in gnome or kde? I  do not know where you would set that in?

You might be able to use alien to change the debian package into a slackware package. I would suggest using oz-desktop-light if you want it to be fast though, since you probably want it to be light (the default oz-desktop is laiden with gnome dependancies).

---

### Post by Rui Pais on 2007-12-10
> **init1 said:**
> I've reinstalled OzOs and still have that odd keyboard problem. I use a standard US keyboard. This issue seems to be related to GDM, because it only happens when I log into a session with GDM. Any ideas?

hi again,
this is definitily a weird thing... have you tried Configuration > Configuration Panel > Language > LAnguage settings? Do you have several languages, only English or none?

Have you checked your xorg.conf to see if your keyboard it's correctly set up?

Check too if your ~/.dmrc contains a line:
```
Language=en_US.UTF-8
```

You must give more info... i can't do much with only what you posted...

---

### Post by Rui Pais on 2007-12-10
> **init1 said:**
> Yeah it's slow. But it's worth it ;)

> **stalker145 said:**
> Thanks. I'm just glad to hear that I'm not doing it wrong ;)

I haven't tried yet on VirtualBox... it's normal take that long? 
did it happen during the installation of mini.iso or Oz related stuff?

---

### Post by Rui Pais on 2007-12-10
> **kazuya said:**
> Hello Rav and Rais, and others on this Oz-desktop project. is there a chance i could run this desktop in a slackware equivalent like Vector Linux or zenwalk or even wolvix..

I am currently running Vector Linux on an older 256 MB machine, it runs like a dream even with kde environment, but I am itching to have a desktop like oz or e17-cvs on there as well to test performance..
Great job again folks..

My only gripe is not knowing how to adjust the desktop scrren resolution to be 1280X1024 instead of 1024X768; like I could do in gnome or kde? I  do not know where you would set that in?

uhmm.... either e17-cvs as oz-desktop are special packages. 
The first it's a wrapper for morlenxus script with an extra dependency list and the second its just a list of packages (with names that my not be the same on other distro) and some configurations that maybe to pertinent to another distro...

I would advice to try the old manual method, see a [pdf here]("http://cafelinux.org/forum/index.php?action=dlattach;topic=881.0;attach=2449"). You need to see from the dependencies list the names of equivalent ones on slackware. packages -dev i don't know how they are managed under that distro... but that you should know better. The rest of instructions apply identically. Morlenxus, lists slackware as one of the tested distros, so it should work.

For the rest of desktop, if you are used to kde, maybe it's even better not go for oz-desktop package. Just install side-by-side your kde and it should give you access to all already installed kde apps 
:)

---

### Post by neonl on 2007-12-10
Hi.

In first place I want to say, that if anyone needs to know if it works or not in virtualbox I can tell it does (@ least with me it does).

*I had something wrote in here but it wasn't right (confused with so many threads, offtopic*

---

### Post by Rui Pais on 2007-12-10
> **neonl said:**
> Hi.

In first place I want to say, that if anyone needs to know if it works or not in virtualbox I can tell it does (@ least with me it does).

*I had something wrote in here but it wasn't right (confused with so many threads, offtopic*

I know what you mean ... several threads on at least 3 forum and 2 different languages! Sometimes its hard :lol: (i find a translation of my howto in italian, but that one i skip...)


I finish to upload an e17-cvs new version.
It contains the last morlenxus script version (minor changes) my patchs and this time i leave what you all always wanted ... penguins ;)

---

### Post by neonl on 2007-12-10
> **Rui Pais said:**
> I finish to upload an e17-cvs new version.
It contains the last morlenxus script version (minor changes) my patchs and this time i leave what you all always wanted ... penguins ;)

I found out before reading your reply ;). I was doing my apt-get update && apt-get dist-upgrade and it said to update the e17 package.

Cumpz :)

---

### Post by Eagleevil on 2007-12-10
I tried to install OzOS on virtualbox and twice so far once it is all done and installed (everything seemed fine) I see a login screen with some OzOS background, but after I log in all I see is what is shown in the attached image.

---

### Post by Rui Pais on 2007-12-11
> **neonl said:**
> I found out before reading your reply ;). I was doing my apt-get update && apt-get dist-upgrade and it said to update the e17 package.

Cumpz :)

:) thats the beauty of having repos!


> **Eagleevil said:**
> I tried to install OzOS on virtualbox and twice so far once it is all done and installed (everything seemed fine) I see a login screen with some OzOS background, but after I log in all I see is what is shown in the attached image.

I forget that possibility...
thats not e17 (ofcourse) it's safe console.
On gdm (login screen) click on 'Sessions' and choose 'Enlightenment'.
That will log you to e17.
Don't forget to accept that as default when it asked.

I will try to fix that on next update. 
Thanks for the report.

---

### Post by RAV TUX on 2007-12-11
> **neonl said:**
> Hi.

In first place I want to say, that if anyone needs to know if it works or not in virtualbox I can tell it does (@ least with me it does).

*I had something wrote in here but it wasn't right (confused with so many threads, offtopic*You could write a HOW TO on a "Virtual" OzOs. :)

---

### Post by Eagleevil on 2007-12-11
> **Rui Pais said:**
> 
I forget that possibility...
thats not e17 (ofcourse) it's safe console.
On gdm (login screen) click on 'Sessions' and choose 'Enlightenment'.
That will log you to e17.
Don't forget to accept that as default when it asked.

I will try to fix that on next update. 
Thanks for the report.

For some reason even checking that skipped my mind, but it works now. Now to play with it some more.

---

### Post by RAV TUX on 2007-12-11
> **Eagleevil said:**
> For some reason even checking that skipped my mind, but it works now. Now to play with it some more.Glad to hear you got it working please let us know your thoughts.

---

### Post by Rui Pais on 2007-12-11
> **RAV TUX said:**
> You could write a HOW TO on a "Virtual" OzOs. :)

Yes, a good idea. 

neonl you know you can count on me on any details/doubts on e17/oz part.

---

### Post by neonl on 2007-12-12
Hi.

Did anyone try this @ Debian. I'm going to do it in Lenny (just to try, I prefer the Ubuntu base),

Cya.

---

### Post by stalker145 on 2007-12-12
> **Rui Pais said:**
> I haven't tried yet on VirtualBox... it's normal take that long? 
did it happen during the installation of mini.iso or Oz related stuff?

Sorry it took a while to get back. It was taking forever installing the Oz stuff. I think it totaled out to be about 2.5-3 hours when all was said and done. 

My VM was running 256MB of RAM and a 2GB virtual drive. Host processor is a 2GHz PIII with a gig of RAM.

I'll try installing it again over the next few days and see if I can replicate the issue. I'll get back with you either way.

---

### Post by init1 on 2007-12-12
> **neonl said:**
> Hi.

Did anyone try this @ Debian. I'm going to do it in Lenny (just to try, I prefer the Ubuntu base),

Cya.
I tried to install it in Lenny, but apt wouldn't install CVS. Maybe Etch will work better.

---

### Post by Masterizaak on 2007-12-13
When might an ISO be made for OZ desktop?

---

### Post by RAV TUX on 2007-12-14
> **Masterizaak said:**
> When might an ISO be made for OZ desktop?Lets hope soon, I actually made a Live DVD with an installer but it was a bit  big:

Ubuntu Hebrew Remix base, OzOs, and I don't remember what else.

Right now Rui Pais and init1 are both working on a minimal iso and a standard iso

keep a look out for an announcement.

---

### Post by molom on 2007-12-14
This seems to be a nice distro. I really like the theme you have picked as the default. I will test it when the final release comes out.

Shalom/Cheers,
molom

---

### Post by BoneSaw on 2007-12-14
i may try this this weekend

---

### Post by RAV TUX on 2007-12-14
> **molom said:**
> This seems to be a nice distro. I really like the theme you have picked as the default. I will test it when the final release comes out.

Shalom/Cheers,
molom

Shalom/Cheers to you molom, I just read in the other thread that you are part of reinvigorating the Linux Mint E17 version.

I had tried the old version out and liked it but then they removed the downloads and it seemed to die, I am over joyed to see in reinvigorated.

I would like to extend an invitation for you and all Linux Mint e17 devs to join the UEOSC.

reference:

[http://cafelinux.org/ueosc/](http://cafelinux.org/ueosc/)

please supply links to the project so I can include it.

> **BoneSaw said:**
> i may try this this weekendCool, please give us your feed back. ;)

---

### Post by mthakur2006 on 2007-12-14
I am hooked to this distro!
I have tried so many other ones e.g. elive, elbuntu and just plain e17, but this one is so nicely done, even with its faults!
RAV TUX you beauty!

---

### Post by molom on 2007-12-14
> **RAV TUX said:**
> Shalom/Cheers to you molom, I just read in the other thread that you are part of reinvigorating the Linux Mint E17 version.

I had tried the old version out and liked it but then they removed the downloads and it seemed to die, I am over joyed to see in reinvigorated.



That's because one of the main developers for that project left the Linux Mint community (I think it was because he got a job so he didn't have any time). But a new developer has volunteered late november and is going to release beta 1 again soon. I am the artwork manager for the project.

> **RAV TUX said:**
> 
I would like to extend an invitation for you and all Linux Mint e17 devs to join the UEOSC.

reference:

[http://cafelinux.org/ueosc/](http://cafelinux.org/ueosc/)



I will get confirmation from the developer and join the UEOSC when the beta is released (To much work for the moment :) ) 

> **RAV TUX said:**
> 

Cool, please give us your feed back. ;)

I will. Thanks for your reply.

Shalom,
molom

---

### Post by RAV TUX on 2007-12-14
> **mthakur2006 said:**
> I am hooked to this distro!
I have tried so many other ones e.g. elive, elbuntu and just plain e17, but this one is so nicely done, even with its faults!
RAV TUX you beauty!All credit for OzOs goes to Rui Pais he is the main developer for OzOs, and his happy "e"lves. ;)

Thanks anyway I am over joyed that you like it.

Rock on!

:guitar:

---

### Post by mthakur2006 on 2007-12-15
> **RAV TUX said:**
> All credit for OzOs goes to Rui Pais he is the main developer for OzOs, and his happy "e"lves. ;)

Thanks anyway I am over joyed that you like it.

Rock on!

:guitar:

:D :D :D
There's is just one minor problem, though:
In my /home/Desktop folder, I have many things, but none of them show up on my screen. Similarly, I have nothing in my Applications menu and the OzOs usplash doesn't work :(
Help will be very appreciated!

---

### Post by RAV TUX on 2007-12-15
> **mthakur2006 said:**
> :D :D :D
There's is just one minor problem, though:
In my /home/Desktop folder, I have many things, but none of them show up on my screen. Similarly, I have nothing in my Applications menu and the OzOs usplash doesn't work :(
Help will be very appreciated!A few questions:

1. What version of OzOs Desktop are you using?

a.[oz-desktop-light/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop-light/")
b.[oz-desktop/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop/")

2. Are you using the latest Rui Pais' E17 CVS Deb?


[e17-cvs/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/e/e17-cvs/")12-Dec-2007 14:54  

3. Do you have the OzOs Repos enabled?

[B]deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) scarecrow main contrib
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main contrib[/B]

(If you just want e17-cvs use only the last one, tinwoodman.)

If so you may just want to do:

```
sudo apt-get update
```Until Rui Pais comes around here is a temporary work around if 'sudo apt-get update' doesn't work.

main menu>configuration>applications>ibar

place your real favorites here to show up on your ibar

then 

main menu>configuration>menus>favorites

place your other most frequently used applications here


This should hold you over.

---

### Post by mthakur2006 on 2007-12-15
> **RAV TUX said:**
> A few questions:

1. What version of OzOs Desktop are you using?

a.[oz-desktop-light/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop-light/")
b.[oz-desktop/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/o/oz-desktop/")

oz-desktop.

2. Are you using the latest Rui Pais' E17 CVS Deb?


[e17-cvs/]("http://www.cafelinux.org/Downloads/oz-os/pool/main/e/e17-cvs/")12-Dec-2007 14:54  

yes.

3. Do you have the OzOs Repos enabled?

[B]deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) scarecrow main contrib
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main contrib[/B]

(If you just want e17-cvs use only the last one, tinwoodman.)

yes.

If so you may just want to do:

```
sudo apt-get update
```Until Rui Pais comes around here is a temporary work around if 'sudo apt-get update' doesn't work.

main menu>configuration>applications>ibar

place your real favorites here to show up on your ibar

then 

main menu>configuration>menus>favorites

place your other most frequently used applications here


This should hold you over.

yes to all. :D:D

---

### Post by Alyx on 2007-12-16
Well Im here to jump on this project as well!! GE has kept me busy but im loading the OzOs up in the VM right now. U know I could build a virtual machine for it and post it up on VMware.

---

### Post by Rui Pais on 2007-12-16
> **mthakur2006 said:**
> :D :D :D
There's is just one minor problem, though:
In my /home/Desktop folder, I have many things, but none of them show up on my screen. Similarly, I have nothing in my Applications menu and the OzOs usplash doesn't work :(
Help will be very appreciated!

Hi,
sorry this late answer.

I must have to solve that issue with menus once for all... 
Can you post the output of:
```
ls /etc/xdg/menus/
```
and ```
ls ~/.config/menus/
```

About Desktop stuff you must have module 'File Manager' loaded to "see" them on the screen.

About usplash, please keep in mind that it's just a 1st sketch to my tests while i'm experiment with iso buildings... 
Can you post the output of:
```
ls -l /usr/lib/usplash/usplash-artwork.so
```
and
```
ls -l /etc/alternatives/usplash-artwork.so
```

Thanks 
Rui

---

### Post by mthakur2006 on 2007-12-17
> **Rui Pais said:**
> Hi,
sorry this late answer.

I must have to solve that issue with menus once for all... 
Can you post the output of:
```
ls /etc/xdg/menus/
```
and ```
ls ~/.config/menus/
```

About Desktop stuff you must have module 'File Manager' loaded to "see" them on the screen.

About usplash, please keep in mind that it's just a 1st sketch to my tests while i'm experiment with iso buildings... 
Can you post the output of:
```
ls -l /usr/lib/usplash/usplash-artwork.so
```
and
```
ls -l /etc/alternatives/usplash-artwork.so
```

Thanks 
Rui

i'd love to but i was trying to compile a custom kernel which didn't go too well...so I had to reinstall everything all over again + i have gotten very busy lately so i will give it a shot again sometime :)
using arch linux atm tho (it is amazingly fast with KDE, ozos would be  so much faster on this than xubuntu.....)

---

### Post by Rui Pais on 2007-12-17
> **mthakur2006 said:**
> i'd love to but i was trying to compile a custom kernel which didn't go too well...so I had to reinstall everything all over again + i have gotten very busy lately so i will give it a shot again sometime :)
using arch linux atm tho (it is amazingly fast with KDE, ozos would be  so much faster on this than xubuntu.....)

I loved to use Arch... but i always hit some annoying block that i can't surpass :( (last one my router was disconnect randomly and for no apparent reason without leaving a trace of what ever make them disconnect... ) 
Arch too it's strangely very unfrendly for 64bits users. Too few packages...

But you can try at least the e17 from cvs install on Arch. 
See pdf version of my how-to and skip the first line of apt-get the devs packages. Just get a compiler, and under arch header files (for compilation of e code) are inside packages of apps not inside -dev packages. 
Check too the how-to for the different path of gdm.

I have always installed that way and work very well (never noted any special speed... )

---

### Post by RAV TUX on 2007-12-18
> **Alyx said:**
> Well Im here to jump on this project as well!! GE has kept me busy but im loading the OzOs up in the VM right now. U know I could build a virtual machine for it and post it up on VMware.Alyx that would be great! ;)

---

### Post by stalker145 on 2007-12-18
Well, I have finally gotten around to my tinkering and ran into an interesting issue. 

I installed both the full version and the light version in VirtualBox. The full version looks GORGEOUS, runs well, and may just become my default in the future. The light, however, seems to not like the default keyboard settings. 

I opened a terminal to do a quick ping to make sure the network was networking (don't ask why I didn't just open a browser) and everything I typed came out > [p[i[n[g It was a very interesting error. The full version had no such problem.

I did notice, however, that in the full version the icon on the left below FireFox (gdmflexiserver) gets it's kicks out of crashing my session. It's odd...

I also receive > Your X server is missing support for the XRandr(X resize and rotate) Extension. if I try to change the resolution. I'm not sure if this is because I'm in VM or if, as mentioned in the error, there was no XRandr support when the ecore (ummm, i hope you guys know what this means) was built.

So far, though, I am really loving the OzOS and its default black theme :D

Thanks for all of your hard work.

---

### Post by mthakur2006 on 2007-12-18
> **Rui Pais said:**
> I loved to use Arch... but i always hit some annoying block that i can't surpass :( (last one my router was disconnect randomly and for no apparent reason without leaving a trace of what ever make them disconnect... ) 
Arch too it's strangely very unfrendly for 64bits users. Too few packages...

But you can try at least the e17 from cvs install on Arch. 
See pdf version of my how-to and skip the first line of apt-get the devs packages. Just get a compiler, and under arch header files (for compilation of e code) are inside packages of apps not inside -dev packages. 
Check too the how-to for the different path of gdm.

I have always installed that way and work very well (never noted any special speed... )

okay thanks...
i will try and let you know :D

---

### Post by Rui Pais on 2007-12-18
> **stalker145 said:**
> Well, I have finally gotten around to my tinkering and ran into an interesting issue. 

I installed both the full version and the light version in VirtualBox. The full version looks GORGEOUS, runs well, and may just become my default in the future. The light, however, seems to not like the default keyboard settings. 

I opened a terminal to do a quick ping to make sure the network was networking (don't ask why I didn't just open a browser) and everything I typed came out  It was a very interesting error. The full version had no such problem.

I did notice, however, that in the full version the icon on the left below FireFox (gdmflexiserver) gets it's kicks out of crashing my session. It's odd...

I also receive  if I try to change the resolution. I'm not sure if this is because I'm in VM or if, as mentioned in the error, there was no XRandr support when the ecore (ummm, i hope you guys know what this means) was built.

So far, though, I am really loving the OzOS and its default black theme :D

Thanks for all of your hard work.

Hi, 
thank for testing and report.

Glad you like the default version and theme :)

The light version it's a little neglected this days... i plan to stabilize oz-desktop and after chop it down (essencially no gnome/firefox) to remake the light one. So i don't give it much attention right now. 
I would suggest people install oz-desktop and remove unneeded apps instead of trying the light version (unless of course space or downloads are a problem). 
I take note of that weird keyboard problem, anyway (i have the faintest idea... never heard about it...)

About gdmflexiserver. Can you run it from a terminal? Don't know if thats an issue with VirtualBox (it's suppose to create an extra xserver...)

About xrandr, this is a xorg.conf problem. 
Check 1st if you have it installed (type xrandr on a terminal, if it says somethig like: "xrandr: command not found" you may need to install with apt-get).
But that should not be the issue. It must be a bad configuration by the process of monitor/graphics autodetection... e17 use a different tool than Gnome, and some resolutions fail when checked by xrandr, the tool e17 uses. Check the e17 [thread here]("http://ubuntuforums.org/showthread.php?p=3596549#post3596549"). On post [#90]("http://ubuntuforums.org/showpost.php?p=3600670&postcount=90") theres a solution, remove of all resolutions higher then your monitor can handle. 


Glad you like this pre-version of OZ OS
:)

---

### Post by Rui Pais on 2007-12-18
> **mthakur2006 said:**
> okay thanks...
i will try and let you know :D

Good.
Since oz-desktop would not make much sense on Arch and you are experiment on e17-cvs post your results (or problems) on it's thread (check my sig.)

hope it runs well :)

---

### Post by stalker145 on 2007-12-18
> **Rui Pais said:**
> About gdmflexiserver. Can you run it from a terminal? Don't know if thats an issue with VirtualBox (it's suppose to create an extra xserver...)

I understand now. I tried running from the terminal and it did the exact same thing as running from the icon... only this time I paid better attention. What I thought of as crashing was, as you described, spawning a new session. The login screen shows I'm already logged in and I can bring up my running session... duh ](*,)

> About xrandr, this is a xorg.conf problem. 
Check 1st if you have it installed (type xrandr on a terminal, if it says somethig like: "xrandr: command not found" you may need to install with apt-get).
But that should not be the issue. It must be a bad configuration by the process of monitor/graphics autodetection... e17 use a different tool than Gnome, and some resolutions fail when checked by xrandr, the tool e17 uses. Check the e17 [thread here]("http://ubuntuforums.org/showthread.php?p=3596549#post3596549"). On post [#90]("http://ubuntuforums.org/showpost.php?p=3600670&postcount=90") theres a solution, remove of all resolutions higher then your monitor can handle. 

OK, running xrandr in the terminal gives me this:```
stalker145@OzOS:~$ xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0  
   640x480        60.0 
```I'm assuming that means it's installed, but there is a config issue *somewhere* as you mentioned. Not that big of a deal now that I can look at that and see that I'm running at maximum possible resolution :D

So, in essence, it appears that the bugs I noted are more along the lines of a PEBKAC error ;)

---

### Post by Rui Pais on 2007-12-20
> **stalker145 said:**
> I understand now. I tried running from the terminal and it did the exact same thing as running from the icon... only this time I paid better attention. What I thought of as crashing was, as you described, spawning a new session. The login screen shows I'm already logged in and I can bring up my running session... duh ](*,)
:)
yes, thats only useful if you have several users on your system.
Its a way to simulate the "fast-user-switch" applet from gnome or same functionality from others DE.

> **stalker145 said:**
> 
OK, running xrandr in the terminal gives me this:```
stalker145@OzOS:~$ xrandr
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       60.0* 
   800x600        60.0  
   640x480        60.0 
```I'm assuming that means it's installed, but there is a config issue *somewhere* as you mentioned. Not that big of a deal now that I can look at that and see that I'm running at maximum possible resolution :D

You need to edit file /etc/X11/xorg.conf and look for lines started with "Modes". Delete all resolutions there above 1027x768. That it's been reported to solve the problem and will allow to change resolution (to the others listed, of course).

Other DEs dont' seems to rely on xrandr and allow to use other (higher) resolutions... but thats not a much wise choice. Usually those are bad for your monitor... or worst, for your eyes :)

---

### Post by mthakur2006 on 2007-12-20
> **Rui Pais said:**
> Good.
Since oz-desktop would not make much sense on Arch and you are experiment on e17-cvs post your results (or problems) on it's thread (check my sig.)

hope it runs well :)

Didn't work :(
Gave me compiling errors and although I liked arch, it is just too lean for my tastes so I am back to OzOs on ubuntu minimal install like you suggested :D

---

### Post by mthakur2006 on 2007-12-20
> **Rui Pais said:**
> Hi,
sorry this late answer.

I must have to solve that issue with menus once for all... 
Can you post the output of:
```
ls /etc/xdg/menus/
```
and ```
ls ~/.config/menus/
```

About Desktop stuff you must have module 'File Manager' loaded to "see" them on the screen.

About usplash, please keep in mind that it's just a 1st sketch to my tests while i'm experiment with iso buildings... 
Can you post the output of:
```
ls -l /usr/lib/usplash/usplash-artwork.so
```
and
```
ls -l /etc/alternatives/usplash-artwork.so
```

Thanks 
Rui

Now that I am back to OzOs, I might as well post the results of these and help you out :)

Here's my ls /etc/xdg/menus/:
```
mtha@ozos:~$ ls /etc/xdg/menus/
debian-menu.menu
mtha@ozos:~$ 

```

the ls ~/.config/menus/:
```
mtha@ozos:~$ ls ~/.config/menus/
ls: /home/mtha/.config/menus/: No such file or directory
mtha@ozos:~$ 

```

Yes, loading the filemanager module works perfectly :)

Here's the ls -l /usr/lib/usplash/usplash-artwork.so:
```
 mtha@ozos:~$ ls -l /usr/lib/usplash/usplash-artwork.so
ls: /usr/lib/usplash/usplash-artwork.so: No such file or directory
mtha@ozos:~$ 

```

And the ls -l /etc/alternatives/usplash-artwork.so:
```
 mtha@ozos:~$ ls -l /etc/alternatives/usplash-artwork.so
ls: /etc/alternatives/usplash-artwork.so: No such file or directory
mtha@ozos:~$ 

```

Thanks.
:popcorn::guitar:

---

### Post by Rui Pais on 2007-12-21
> **mthakur2006 said:**
> Didn't work :(
Gave me compiling errors and although I liked arch, it is just too lean for my tastes so I am back to OzOs on ubuntu minimal install like you suggested :D

Hey, thanks for gives Oz OS another try. :)


> **mthakur2006 said:**
> Now that I am back to OzOs, I might as well post the results of these and help you out :)

Here's my ls /etc/xdg/menus/:
```
mtha@ozos:~$ ls /etc/xdg/menus/
debian-menu.menu
mtha@ozos:~$ 

```

the ls ~/.config/menus/:
```
mtha@ozos:~$ ls ~/.config/menus/
ls: /home/mtha/.config/menus/: No such file or directory
mtha@ozos:~$ 

```

Yes, loading the filemanager module works perfectly :)

Here's the ls -l /usr/lib/usplash/usplash-artwork.so:
```
 mtha@ozos:~$ ls -l /usr/lib/usplash/usplash-artwork.so
ls: /usr/lib/usplash/usplash-artwork.so: No such file or directory
mtha@ozos:~$ 

```

And the ls -l /etc/alternatives/usplash-artwork.so:
```
 mtha@ozos:~$ ls -l /etc/alternatives/usplash-artwork.so
ls: /etc/alternatives/usplash-artwork.so: No such file or directory
mtha@ozos:~$ 

```

Thanks.
:popcorn::guitar:

Thanks for the report.
About menus, do you you still have empty menus on the new installation?
And usplash, do you used the latest versions or the old packages you have downloaded before. It's important to have the latest version, that should have that issue solved...

I will check oz-desktop-light to see if i have already tuned menus or can do anything better for them.
Rui

---

### Post by mthakur2006 on 2007-12-21
> **Rui Pais said:**
> Hey, thanks for gives Oz OS another try. :)




Thanks for the report.
About menus, do you you still have empty menus on the new installation?
And usplash, do you used the latest versions or the old packages you have downloaded before. It's important to have the latest version, that should have that issue solved...

I will check oz-desktop-light to see if i have already tuned menus or can do anything better for them.
Rui

nope, still no application menus + no usplash in oz-desktop.
merry christmas to all of you :D :grin:

---

### Post by Rui Pais on 2007-12-21
> **mthakur2006 said:**
> nope, still no application menus + no usplash in oz-desktop.
merry christmas to all of you :D :grin:

weird...
do you have cafelinux repos on your sources.list?
Do you mind to try a: 
```
sudo aptitude update && sudo aptitude reinstall oz-desktop-light usplash-theme-oz
```

A nice Christams to you and to all too :)

---

### Post by mthakur2006 on 2007-12-27
> **Rui Pais said:**
> weird...
do you have cafelinux repos on your sources.list?
Do you mind to try a: 
```
sudo aptitude update && sudo aptitude reinstall oz-desktop-light usplash-theme-oz
```

A nice Christams to you and to all too :)

sorry about the late reply.
did that, no luck still :(

---

### Post by chris4585 on 2007-12-29
very nice, i like, only thing i cant figure out is how to get all the usual codecs installed

i installed it flawlessly no problems, it took a little while running in a vm, it was very nice looking

good work!

---

### Post by smartboyathome on 2007-12-29
> **mthakur2006 said:**
> sorry about the late reply.
did that, no luck still :(

Try this (boot into recovery mode before doing this):

```
sudo aptitude purge oz-desktop-light usplash-theme-oz && sudo aptitude install oz-desktop-light usplash-theme-oz
```

Then reboot. Does it help?

---

### Post by Masterizaak on 2007-12-30
Great job :D

---

### Post by Masterizaak on 2007-12-30
> **Masterizaak said:**
> Great job :D

theres one thing, in the menu ¨applications¨ when I install things, nothing shows up, not even firefox is there. Do I have to do something? or make a file for it?

---

### Post by Rui Pais on 2008-01-02
> **Masterizaak said:**
> theres one thing, in the menu ¨applications¨ when I install things, nothing shows up, not even firefox is there. Do I have to do something? or make a file for it?

uhmm sorry to hear it. Thats a recurrent issue that some users seems to have (i still figure why it fails sometimes :()

Meanwhile, maybe trying the suggestions here:
[http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/13/About-the-Applications-menu-files](http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/13/About-the-Applications-menu-files)

good luck

---

### Post by Rui Pais on 2008-01-03
Hi all.

I updated the repos right now. 
I hope the menu issue it's solved now.
(Note that we still having issues with speed on Cafelinux server. If it aborts update just wait a few minutes and retry. Sorry about the inconvenience).

I plan to upload an iso in a day or two. 
I'm just tweaking things a little and take some time to do tests on installations (a slowly process...).
Keep tuned :)

Rui

---

### Post by molom on 2008-01-07
@ Rui Pais or RAV TUX
What is the difference between the standard E17 package and the Rui Pais CVS E17 package?

Cheers,
molom

---

### Post by Rui Pais on 2008-01-07
> **molom said:**
> @ Rui Pais or RAV TUX
What is the difference between the standard E17 package and the Rui Pais CVS E17 package?

Cheers,
molom

What standard E17 package? There is no standard package... 

The difference between my e17- cvs and any other pre-compiled packages it's that deb only installs the needed dependencies and configs.
Installation it's done automatically by compilation of the latest cvs code, using the morlenxus script. 
Thats what enlightenment devs use at [enlightenment test server]("http://download.enlightenment.org/tests/") and the closest to an [*"official"* installation]("http://wiki.enlightenment.org/index.php/Category:Enlightenment_Desktop_Shell").

The focus was keep it simple as possible, even for users with no experience, but preserve the flexibility  of installations done by code compilation from cvs code. 

Since installation it's done on user machine, it will act upon $CFLAGS and $LDFLAGS environment variables. Advanced users may wanted to tuned those. They can too tune precisely what will get from cvs or from which time. Users can keep as updated as they wish, since they keep all control of cvs access and update. 
 
But non advanced users still can have e17 by running a single apt command or a synaptic click.They will get a very stable, carefully chosen e17 core, that experience shows don't give much problems and it's very stable.

And finally one point i find important, it installs all on a single folder /opt/e17 (contrary to the packages that Mint or Geubuntu uses) that make it simple removals, backups and maintenance in general. 
Theres plenty reported problems of users get lost libs mixed with the system, that create problems with updates, libs not cleaned for some reason by the apt/dpkg (although this problems it's not very frequent lately, e devs seems to have standardized the libs paths...) 
Anyway keep pre-alpha/testing stuff away and well separated of main /usr/ it's a natural and wealthy practice, imho.

---

### Post by RAV TUX on 2008-01-17
> **Rui Pais said:**
> What standard E17 package? There is no standard package... 

The difference between my e17- cvs and any other pre-compiled packages it's that deb only installs the needed dependencies and configs.
Installation it's done automatically by compilation of the latest cvs code, using the morlenxus script. 
Thats what enlightenment devs use at [enlightenment test server]("http://download.enlightenment.org/tests/") and the closest to an [*"official"* installation]("http://wiki.enlightenment.org/index.php/Category:Enlightenment_Desktop_Shell").

The focus was keep it simple as possible, even for users with no experience, but preserve the flexibility  of installations done by code compilation from cvs code. 

Since installation it's done on user machine, it will act upon $CFLAGS and $LDFLAGS environment variables. Advanced users may wanted to tuned those. They can too tune precisely what will get from cvs or from which time. Users can keep as updated as they wish, since they keep all control of cvs access and update. 
 
But non advanced users still can have e17 by running a single apt command or a synaptic click.They will get a very stable, carefully chosen e17 core, that experience shows don't give much problems and it's very stable.

And finally one point i find important, it installs all on a single folder /opt/e17 (contrary to the packages that Mint or Geubuntu uses) that make it simple removals, backups and maintenance in general. 
Theres plenty reported problems of users get lost libs mixed with the system, that create problems with updates, libs not cleaned for some reason by the apt/dpkg (although this problems it's not very frequent lately, e devs seems to have standardized the libs paths...) 
Anyway keep pre-alpha/testing stuff away and well separated of main /usr/ it's a natural and wealthy practice, imho.Rui Thanks for keeping the home fires burning in my absence. I look forward to becoming more active once I get settled in. I suspect this will be in February. 

I look forward to using the new Oz Os also. ;)

---

### Post by RAV TUX on 2008-01-17
> **Rui Pais said:**
> Hi all.

I updated the repos right now. 
I hope the menu issue it's solved now.
(Note that we still having issues with speed on Cafelinux server. If it aborts update just wait a few minutes and retry. Sorry about the inconvenience).

I plan to upload an iso in a day or two. 
I'm just tweaking things a little and take some time to do tests on installations (a slowly process...).
Keep tuned :)

RuiRui let me know if you need anything in relation to the server.

---

### Post by Rui Pais on 2008-01-17
> **RAV TUX said:**
> Rui Thanks for keeping the home fires burning in my absence. I look forward to becoming more active once I get settled in. I suspect this will be in February. 

I look forward to using the new Oz Os also. ;)

Well i've been working on a liveCD and tunning it's more or less done to a decent RC version... 
my problem now it's that when install to HD, installer aborts around 87% of the proccess... and i haven't the faintest idea why... 

By that time it already installed the system on HD (nicely i checked, all e17 it's there correctly, 1st user, everything) i think it fails when it enters the part where it installs grub and grub menus... i'll have to check this. Just have little time and little knowledge on that, besides make isos take a long time and it's so easy to make errors by distraction 8-[


> **RAV TUX said:**
> Rui let me know if you need anything in relation to the server.

Everything it's running fine now :)

---

### Post by smartboyathome on 2008-01-17
By the way, Rui, what are you using to make the livecd?

---

### Post by Rui Pais on 2008-01-17
> **smartboyathome said:**
> By the way, Rui, what are you using to make the livecd?

My own bare hands ;)

Now seriously, i'm doing it all from command line, based on Xubuntu liveCD (the closest to to oz-desktop). I tried remastersys, UCK, reconstructor and give an eye for a some other projects... but they are all buggy or useless for my purposes or imply use ubuntu liveCD specific or the i386 version only...

The far i could go was reconstructor (that make the tenderness of duplicate, once triplicate, all my /var/cache/apt draining all free space of my disc) and create isos that don't boot because, according to error output, bad md5sum checks :(

I end up following 2 good articles i found on the net, and copied the command lines into a script to optimize/speed up the process.

EDIT:
btw. here a screenshot of the look atm a few seconds before crash:
[ATTACH]56723[/ATTACH]
(I opt by Portuguese on install but translations it's more or less obvious... seems to crash "importing definitions")

---

### Post by RAV TUX on 2008-01-19
> **Rui Pais said:**
> 



EDIT:
btw. here a screenshot of the look atm ...
[ATTACH]56723[/ATTACH]
It looks beautiful as always, I look forward to giving this a try. ;)

---

### Post by smartboyathome on 2008-01-20
> **Rui Pais said:**
> My own bare hands ;)

Now seriously, i'm doing it all from command line, based on Xubuntu liveCD (the closest to to oz-desktop). I tried remastersys, UCK, reconstructor and give an eye for a some other projects... but they are all buggy or useless for my purposes or imply use ubuntu liveCD specific or the i386 version only...

The far i could go was reconstructor (that make the tenderness of duplicate, once triplicate, all my /var/cache/apt draining all free space of my disc) and create isos that don't boot because, according to error output, bad md5sum checks :(

I end up following 2 good articles i found on the net, and copied the command lines into a script to optimize/speed up the process.

EDIT:
btw. here a screenshot of the look atm a few seconds before crash:
[ATTACH]56723[/ATTACH]
(I opt by Portuguese on install but translations it's more or less obvious... seems to crash "importing definitions")

If it is just crashing on the translations, I would say it is safe to release a beta and see if it happens to others.

---

### Post by Rui Pais on 2008-01-20
> **smartboyathome said:**
> If it is just crashing on the translations, I would say it is safe to release a beta and see if it happens to others.

Yes, i thought that too (i started to suspect my drives had some problem), but meanwhile i track down the faulty one.

I tried an install on plain English, only 1 HD, the newer, and my best CD drive... and problems gone away, So it was just reinstall adding one extra a time, till things broken again.

Problem it's a bug on Gutsy ubiquity, a part of the wizard named MigrantAssistant. It is python script, i think, and it checks all partitions for /home/* to ask user if wants to migrate that data to new install.
Ubiquity has some know problem in dealing with specialized tunned partitions (i have one xfs and one ext2 with special settings). That problem it's easy worked around by telling the installer to ignore those partitions... but MigrantAssistant, don't care about that and insists on check on them, becoming the MigrantAssassin :(

Of course that has nothing to do with Oz OS. It happens in all gutsy variants and all gutsy based distros. 
People installing Gutsy can suspect (and detect the problem earlier) if installer skips step 5. That means that it will almost for sure broken at 89% of install. 

The only solution for that cases it's disconnect the drive with such partitions or if one wants to install on that disc remove the problematic partitions (:(... Luckly this kind of problems are rare and happen only to experimented users).

If anyone knows a bug report related with this, please let me know.
Other wise i'll make a new bug report for it on launchpad.


Oz OS its now on the phase of final personalizations and settings, don't have much time on weekends... so on tuesday i should release a 1st RC, full functional (but without much artwork tunning)
:)

---

### Post by RAV TUX on 2008-01-21
> **Rui Pais said:**
> 

Oz OS its now on the phase of final personalizations and settings, don't have much time on weekends... so on tuesday i should release a 1st RC, full functional (but without much artwork tunning)
:)

Looking forward to the new release.

I will have to get someone started on the artwork.

---

### Post by Rui Pais on 2008-01-25
Hi all.
as you may know I've been working on an Ubuntu variation with e17 compiled from CVS, named OzOS ([check here]("http://ubuntuforums.org/showthread.php?t=623803")).

[B][COLOR="Blue"]A new release 0.8 it's available ( 30/June/2008 ).
It solves major issues and updates all software.
[/COLOR][/B]


[COLOR="Gray"]
So the first RC1.0 it's finally available (for 64bits only at the time).
Here it's the official announcement:[/COLOR]
[http://cafelinux.org/forum/index.php/topic,974.0.html](http://cafelinux.org/forum/index.php/topic,974.0.html)

Hope you like it!



> 
**- So whats is Oz OS?**

Oz OS it's an Enlightenment (e17) Desktop Linux build over an Ubuntu Gutsy.


**- A little more Enlightenment, please?**

The e17 version of Oz OS it's compiled directly from the latest cvs source and all updates will be done at user choice always by compilation of updated code.

The process can be done automatically (by click on an icon) or from a terminal offering all kind of advanced control (specific dates, compiler flags, partial/specific sections of cvs, whatever...)


**- But whats on Oz OS? **

Oz OS tries to implements a functional and viable enlightenment, keeping close as possible to it's own way of doing the desktop environment. It will not try to emulate other DEs or other desktop methods/ways.
New users of e17 may need an adaptation time, but we believe that the "effort" is rewarding. Cheesy

On contrary, e applications are reduced to a minimum of those who are relatively stable. Users that may want to try those applications can easily get and compiled them from CVS. No need to worry if they are already on some repository or if they are compatible with your e17 version... you made them compatible.
 

The Gutsy base it's a full updated version of the original 7.10, offering all security updates and bug corrections. Oz OS can use any of Ubuntu packages as any updates to the base system.
Oz OS can be used side by side with any other Ubuntu desktop.
In fact, since Oz OS it's more update then original Gutsy, an Oz OS + ubuntu-desktop it's a more update Ubuntu Linux than plain Ubuntu Gutsy Smiley


**- Whats "in-the-box"?**

. e17 (always update)
. build-essential (the full GNU compilers/tools set)
. Latest X server of Gutsy (not the original much buggier one)
. SCite (an all-in-one text editor to a mini-IDE)
. Thunar and Terminal
. Firefox (2.0.0.11) and Thunderbird.
. Gimp 2.4.2 (final release, interface personalized)
and many others...
You can add all you want, from the huge Ubuntu repos, using synaptic, apt or plain apt:foo from your browser.


**- The install CD as an hole in the middle?**

Yes. Just burn it. It's a LiveCD (it runs fully from CD, installations it's a simple click away).
It can be used as an all-in-one tool, since live cd includes among the usual GNU/Linux tools to deal with partitions and filesystems, gParted and TestDisc, 2 precious apps to visualize, change, edit or restore your hard drives, from simple resize of partitions to a full partitions table recover or partition imaging.

Finally, and since Oz tries to be different and think in the future, this is one of the few distro that starts by a 64bits release. (Eh! this is Linux, 2008, right?)
With time we will make 32bits version. Meanwhile... the old manual method it's always available ;)



Tank You All,
Rui

---

### Post by Rui Pais on 2008-01-25
(here will be the FAQ section, to make it easy to edit)



Screenshots:
[ATTACH]57567[/ATTACH]  [ATTACH]57560[/ATTACH]  [ATTACH]57561[/ATTACH]  [ATTACH]57568[/ATTACH]

---

### Post by neonl on 2008-01-25
A great step to Linux!

Updated the post @ TZ, pls check ;). I bumped so people read the *warning*.

Congrats, great job, Rui.

Hug, Rui *neonl*

---

### Post by Rui Pais on 2008-01-25
> **neonl said:**
> A great step to Linux!

Updated the post @ TZ, pls check ;). I bumped so people read the *warning*.

Congrats, great job, Rui.

Hug, Rui *neonl*

Thanks neonl!!
For the compliment and for spreading the word on the Pt Forum :)

Do you have the possibility of check if torrent file it's working (try download some bits to see if it works)?
Would be very helpful. 
Obrigado Rui.

[http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent)

---

### Post by neonl on 2008-01-25
> **Rui Pais said:**
> Thanks neonl!!
For the compliment and for spreading the word on the Pt Forum :)Thank YOU! :D

> Do you have the possibility of check if torrent file it's working (try download some bits to see if it works)?
Would be very helpful. 
Obrigado Rui.

[http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent)

Well I never use torrents and usually they don't work with me, so I asked a "friend" form TZ and he said that it's working (peers are slowly appearing) :).

Regards

---

### Post by Rui Pais on 2008-01-25
> **neonl said:**
> 
Well I never use torrents and usually they don't work with me, so I asked a "friend" form TZ and he said that it's working (peers are slowly appearing) :).

Regards

Yes, good! I see 2 peers already!

(I have had bad experiences with torrent too... have to tweak a something, port forwarding, on my router to make it work.... luckly i find a site with detailed instructions for huge list of routers :))

Thanks for the help, neonl :popcorn:

Rui

---

### Post by neonl on 2008-01-25
> **Rui Pais said:**
> Yes, good! I see 2 peers already!

(I have had bad experiences with torrent too... have to tweak a something, port forwarding, on my router to make it work.... luckly i find a site with detailed instructions for huge list of routers :))

Thanks for the help, neonl :popcorn:

Rui

The part of port forwarding I'm quite familiarized, since I use e(a)mule.

Btw, maybe it is a good idea to release this with ed2k, but this weekend and in the next week I won't be able to think about computers (physics, maths, spanish and portuguese tests :().

Cya.

---

### Post by Rui Pais on 2008-01-25
> **neonl said:**
> The part of port forwarding I'm quite familiarized, since I use e(a)mule.

Btw, maybe it is a good idea to release this with ed2k, but this weekend and in the next week I won't be able to think about computers (physics, maths, spanish and portuguese tests :().

Cya.

Regretably i don't understand much of those animals (mules)

But don't worry. You will have an hard week, with much more things to concentrate.
Good luck with your tests/exams!

---

### Post by RAV TUX on 2008-01-25
> **Rui Pais said:**
> Hi all.
as you may know i've been working on an Ubuntu variation with e17 compiled from CVS, named Oz OS ([check here]("http://ubuntuforums.org/showthread.php?t=623803")).

So the first RC1.0 it's finally available (for 64bits only at the time).
Here it's the official announcement:
[http://cafelinux.org/forum/index.php/topic,974.0.html](http://cafelinux.org/forum/index.php/topic,974.0.html)

Hope some of you like it!



Tank You All,
Rui
Awesome! Simply Awesome! Rui I am currently downloading the ISO, The torrent hasn't started yet so we may need more seeds, if anyone can help seed the OzOs Torrent please help out.

Oz Os loooks simply beautiful in classic Rui Pais Style!

I look forward to hearing feed back from testers/users...


;)

RAV TUX

---

### Post by RAV TUX on 2008-01-25
Just a reminder

There are 3 primary IRC channels for instant discussion:

#cafelinux

#ozos

#aptfoo

---

### Post by chris4585 on 2008-01-26
Rui Pais i am excited about downloading and installing ozos, i tried ozos before when it wasnt installed by a livecd, and i found a few things didnt work, it was a while ago, but the menu's didnt work properly, right now i'm downloading the torrent with the iso, its going a bit slow :/

P.S. what did you use to make the livecd? i'm not advanced but i've been around a while, and i've decided i want to make a distro, i have a few ideas i have, and i know what i want, i have a understanding how to make a livecd with remastersys but it doesnt do exactly as i want, i want to make a custom livecd, using remastersys it uses the same boot options and logo's and uses the same usplash, i have to logout and login to my account i have created to build the system, the user is guest for obvious reasons, and then it logs into my desktop that i've been working on, but this seems a bit more than what i want, so any pointers or anything on making a distro is appreciated

P.S. ozos is very sexy and smooth in my opinion

---

### Post by Rui Pais on 2008-01-26
> **chris4585 said:**
> Rui Pais i am excited about downloading and installing ozos, i tried ozos before when it wasnt installed by a livecd, and i found a few things didnt work, it was a while ago, but the menu's didnt work properly, right now i'm downloading the torrent with the iso, its going a bit slow :/

P.S. what did you use to make the livecd? i'm not advanced but i've been around a while, and i've decided i want to make a distro, i have a few ideas i have, and i know what i want, i have a understanding how to make a livecd with remastersys but it doesnt do exactly as i want, i want to make a custom livecd, using remastersys it uses the same boot options and logo's and uses the same usplash, i have to logout and login to my account i have created to build the system, the user is guest for obvious reasons, and then it logs into my desktop that i've been working on, but this seems a bit more than what i want, so any pointers or anything on making a distro is appreciated

P.S. ozos is very sexy and smooth in my opinion

Thanks, chris4585.

About the making of liveCD, [see here]("http://ubuntuforums.org/showpost.php?p=4154215&postcount=142") for my previous answer and comments on my CD remasters saga :(


Yes the torrent it's been pretty slow. It will only be fast if there are more seeders... till now average has been 2, some times only one (me, i presume).

Please anyone, even if you already download the iso directly you can help seeding.
Just hit the link:
[http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent)
and on your torrent client choose save iso file setting the path for the one you have already on your disk.
That would "complete" the task (it's already downloaded) and will start to seed to others.

Many, many thanks.

---

### Post by Rui Pais on 2008-01-26
> **RAV TUX said:**
> Awesome! Simply Awesome! Rui I am currently downloading the ISO, The torrent hasn't started yet so we may need more seeds, if anyone can help seed the OzOs Torrent please help out.

Oz Os loooks simply beautiful in classic Rui Pais Style!

I look forward to hearing feed back from testers/users...


;)

RAV TUX


Thanks a lot RAV TUX! :D

I'm looking forward for people feedback too.
:)

---

### Post by chris4585 on 2008-01-26
i'm downloading right now and its at 85% i will seed for possibly a week or so, and thanks Rui Pais, this helps a bit even though i've seen this post before, i'll just have to think outside of the box for the livecd, possibly editing the remastersys script, i see potential within remastersys, also i cant wait till the iso is done, i was a bit disappointed last time i tested ozos, now i have high hopes, i'm glad my computer is 64bit ;)

---

### Post by neonl on 2008-01-26
I'm having a problem which is that I'm not being able to download the iso from torrent since I don't see one single peer/seed, I think it's not recognizing the tracker. I'm using Deluge Torrent, if that matters. Yesterday I was with 2% done, but I deleted the torrent when configured the router to start again...

---

### Post by meborc on 2008-01-26
ok... downloading/uploading now

---

### Post by neonl on 2008-01-26
Great! Mine found tracker successfully now! :guitar::guitar:

When I have it @ 100% I'll share it on ed2k so that people who use emule/amule rather than torrent can have it too :)

---

### Post by meborc on 2008-01-26
> In fact, since Oz OS it's more update then original Gutsy, an Oz OS + ubuntu-desktop it's a more update Ubuntu Linux than plain Ubuntu Gutsy Smiley


wait, how is it that oz is more up to date than gutsy? :D ... they both use the same repos... don't they?

---

### Post by chris4585 on 2008-01-26
i'm at 100% finished

---

### Post by Rui Pais on 2008-01-26
> **meborc said:**
> ok... downloading/uploading now

> **neonl said:**
> Great! Mine found tracker successfully now! :guitar::guitar:

When I have it @ 100% I'll share it on ed2k so that people who use emule/amule rather than torrent can have it too :)

Thank you a lot guys for giving this preference for torrent.
If possible keep the port open so seed will continue to others :)

Thanks neonl for the ed2k (i have no experience with that), if you have time it will be good (as long as don't prejudice your studying time, ok?)

---

### Post by Rui Pais on 2008-01-26
> **meborc said:**
> wait, how is it that oz is more up to date than gutsy? :D ... they both use the same repos... don't they?

Oops... a typo.
It's suppose to say to more up to date than  Original Gutsy CD. Sorry. 

And yes they use the same repos (or, give credits correctly, Oz main system use ubuntu repos).

I'll correct my original post. Thanks for call my attention to it.

---

### Post by Rui Pais on 2008-01-26
> **chris4585 said:**
> i'm at 100% finished

Great! Hope you like it!


> **chris4585 said:**
> i'm downloading right now and its at 85% i will seed for possibly a week or so, and thanks Rui Pais, this helps a bit even though i've seen this post before, i'll just have to think outside of the box for the livecd, possibly editing the remastersys script, i see potential within remastersys, also i cant wait till the iso is done, i was a bit disappointed last time i tested ozos, now i have high hopes, i'm glad my computer is 64bit ;)

I tried remastersys and reconstructor, but find hard to fine tune (besides very annoying bugs...)

I recommend do it by hand (it's easier in fact). Check here:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

It very well explained, and if you type the needed commands on a text file you can later copy past the needed ones to a terminal allowing quick changes and fast editing of you liveCD :)

hth

---

### Post by Rui Pais on 2008-01-26
Hi all.

For those who didn't noted yet, theres finally a liveCD:
[http://cafelinux.org/forum/index.php/topic,974.0.html](http://cafelinux.org/forum/index.php/topic,974.0.html)
and
[http://ubuntuforums.org/showthread.php?t=677962](http://ubuntuforums.org/showthread.php?t=677962)

It's a 64bits release. 32 bits still have to do the method outlines in this threads.

A lot of thanks to you all who test and give your opinions and suggestions.
:)

---

### Post by neonl on 2008-01-26
> **Rui Pais said:**
> Thanks neonl for the ed2k (i have no experience with that), if you have time it will be good (as long as don't prejudice your studying time, ok?)

No problem. I will just share it and let the PC on most of the time. I'm folding, seeding on torrents and sharing on ed2k, these are all things that don't require much human intervention, so I don't think there will be any problem (on studies) caused by this :popcorn:

Btw, torrent @ 6%. In an hour or so I'll have it full.

Btw #2, are you going to do a i386/i686 CD?

---

### Post by chris4585 on 2008-01-26
> **Rui Pais said:**
> Great! Hope you like it!




I tried remastersys and reconstructor, but find hard to fine tune (besides very annoying bugs...)

I recommend do it by hand (it's easier in fact). Check here:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

It very well explained, and if you type the needed commands on a text file you can later copy past the needed ones to a terminal allowing quick changes and fast editing of you liveCD :)

hth

thank you, you've probably helped me more than anyone so far Rui Pais, as soon as i make a backup with remastersys i will work on fine tuning and fixing things, then try the guide you posted, many thanks

this is what my system will look like a bit

---

### Post by Rui Pais on 2008-01-27
> **neonl said:**
> No problem. I will just share it and let the PC on most of the time. I'm folding, seeding on torrents and sharing on ed2k, these are all things that don't require much human intervention, so I don't think there will be any problem (on studies) caused by this :popcorn:

Btw, torrent @ 6%. In an hour or so I'll have it full.

Great. Thanks Rui.

> **neonl said:**
> 
Btw #2, are you going to do a i386/i686 CD?
I think so, lets see how my time will be in the next week (and we have the problem of bandwidth that we need to solve at CafeLinux...)

I'm fascinated, anyway, that the manual method recieved much more attention and comments that the CD with installer.
I, in my case, prefer to manual install from a minimal CD or a system base choose by me, but it looked that most people prefer
a CD with a release... it's much harder for me, and for net bandwidth.

---

### Post by Rui Pais on 2008-01-27
> **chris4585 said:**
> thank you, you've probably helped me more than anyone so far Rui Pais, as soon as i make a backup with remastersys i will work on fine tuning and fixing things, then try the guide you posted, many thanks

this is what my system will look like a bit

:)
Glad you find it useful.
You pic looks good (but i'm suspect, i like minimal desktop with colors different from blue ;))

whats that environment? xfwm?


btw, here another tutorial with some extra info that, even some times a little twisted, it's explained in details, so it teaches a lot:
[http://www.cyberpunkcafe.com/page.php?31](http://www.cyberpunkcafe.com/page.php?31)

Just one thing more about the LiveCD documentation i pointed you previously. At gutsy version (any flavour that uses a squashfs) the tip of testing with qemu didn't work. It loads fine and seems to work, but it will soon leave you with a busybox line command. (For days i take that as a problem on my liveCDs  ](*,)...)
I

---

### Post by chris4585 on 2008-01-27
> **Rui Pais said:**
> :)
Glad you find it useful.
You pic looks good (but i'm suspect, i like minimal desktop with colors different from blue ;))

whats that environment? xfwm?


btw, here another tutorial with some extra info that, even some times a little twisted, it's explained in details, so it teaches a lot:
[http://www.cyberpunkcafe.com/page.php?31](http://www.cyberpunkcafe.com/page.php?31)

Just one thing more about the LiveCD documentation i pointed you previously. At gutsy version (any flavour that uses a squashfs) the tip of testing with qemu didn't work. It loads fine and seems to work, but it will soon leave you with a busybox line command. (For days i take that as a problem on my liveCDs  ](*,)...)
I

Thanks, this distro will be as lightweight as i can make it without suffering functionality and ease of use, the environment is actually gnome, i have plans  to come up with a fvwm-crystal version in the future, possibly others aswell, i think i will install another theme with more color to go into the distro, but the original idea was go to for old and lightweight look and feel.  

Thanks again for the tips i will more than likely use them, today i will make a backup so i dont mess something up, i'm using virtualbox for testing and it works pretty well

Chris

---

### Post by chris4585 on 2008-01-27
Rui Pais i have just tested ozos and it is amazing, alot of programs were super fast, but one error i did get was with gnumeric, it wouldnt load for some reason, great job! (woops i left this open for a day, so this is a late message)

---

### Post by handy on 2008-01-27
I'm installing now.

Oz looks great on the LiveCD, & my internet worked straight away.

Having spent all yesterday dealing with problems in the DreamLinux 3 Beta install, Oz looks to be plain sailing already! :-D

---

### Post by handy on 2008-01-27
I've installed & updated all via synaptic.

My major problem is that I find it very hard to read any text displayed in the DE.  Firefox is no problem I've adjusted the fonts there.

I used the Enlightenment Configuration to adjust every font to 19 pixels, which seems to have had no effect?  It was very hard to even do that, as the fonts are so small on my 19" CRT monitor which was automatically set to run at a screen resolution of 1680X1050 @ 60 Hz. I tried to reset the resolution to 1280x1024, but it won't take?  It goes to the crosshatch test screen for so many seconds, then returns with a configuration failed error.

After a reboot the screen resolution of 1280x1024 was accepted, but the fonts have not changed.

I'm sure that this problem will become history; I am looking forward to getting to know this new DE, but I really can't do much with it at the moment...

---

### Post by handy on 2008-01-27
Well at 800x600 I can use the left & right mouse button menu's without much strain.

I have tried a couple of different ways to get the nVidia restricted drivers installed, but no go so far.  Keep landing back in low graphics mode. After those attempts.  Landed black screen of death once also! :-)

(EE) Failed to initialize GLX extension (Comatible NVIDIA X driver not found)

---

### Post by Rui Pais on 2008-01-28
> **handy said:**
> I've installed & updated all via synaptic.

My major problem is that I find it very hard to read any text displayed in the DE.  Firefox is no problem I've adjusted the fonts there.

I used the Enlightenment Configuration to adjust every font to 19 pixels, which seems to have had no effect?  It was very hard to even do that, as the fonts are so small on my 19" CRT monitor which was automatically set to run at a screen resolution of 1680X1050 @ 60 Hz. I tried to reset the resolution to 1280x1024, but it won't take?  It goes to the crosshatch test screen for so many seconds, then returns with a configuration failed error.

After a reboot the screen resolution of 1280x1024 was accepted, but the fonts have not changed.

I'm sure that this problem will become history; I am looking forward to getting to know this new DE, but I really can't do much with it at the moment...

> **handy said:**
> Well at 800x600 I can use the left & right mouse button menu's without much strain.

I have tried a couple of different ways to get the nVidia restricted drivers installed, but no go so far.  Keep landing back in low graphics mode. After those attempts.  Landed black screen of death once also! :-)

(EE) Failed to initialize GLX extension (Comatible NVIDIA X driver not found)


Hi Handy.
Thanks for your reports and comments! 
They very appreciated :)

Sorry to hear about your problems. They are in fact Xorg issues. 

There's plenty threads around where installer, after done a correct work on liveCD, on installed system creates a bad xorg.conf file.
Since Xorg versions from Gutsy and Oz are different, that may explain why that only happen to you on Oz OS.

There are 2 ways of solve that. The first it's the standard:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and restart X server (ctrl+alt+backspace)

One thing most people don't know and i think it's important it's the relation of xorg.conf files with your OS. Thats a configuration file, easy. But it's related with your hardware, not with your Linux or Xserver version. A good working xorg.conf should work with all other Linuxs you install. 
(I used to have 17'' Philips monitors that were hard even under Windows. Once i made a correct xorg.conf i put it on a pen and any Linux i tried i always replace xorg.conf without even care with the one installed)

So, of course, the second way it's to just copy a working xorg.conf from another distro where it works. Note that it must have both same driver so maybe go for the first approach in first place.

About NVidia drivers, the easier and reliable way i know of get those it's using [envy]("http://albertomilone.com/nvidia_scripts1.html"). Here it's a link to deb:
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb)

Please, let me know how it goes.
good luck.

---

### Post by Rui Pais on 2008-01-28
> **chris4585 said:**
> Rui Pais i have just tested ozos and it is amazing, alot of programs were super fast, but one error i did get was with gnumeric, it wouldnt load for some reason, great job! (woops i left this open for a day, so this is a late message)

Hi again.

Thats one thing that needs be polish to the next version, menus :(

The reason it' sbecause default menus (i used ubuntu ones) have a gnumeric entry that it's not installed by default...

If you want gnumeric just do
sudo apt-get install gnumeric 
or simply, on your OzOS, click here:
[apt:gnumeric]("apt:gnumeric")

I will clean menus of inexistent apps and eventually tuned a bit.



You can do this by installing [alacarte]("apt:alacarte")
and set them to you specific taste. 
Of course it's a gnome app and have dependencies on that, so you may not wanted around. In that case, after use it just remove it with apt/synaptic and any other dependencies it may have installed.
Take note manually or use aptitude, that do an excellent job removing an app and it's dependencies:
```
sudo aptitude install alacarte
```
to remove:
(sudo aptitude purge alacarte)


Thanks a lot to give OzOS a try. You are all helping to make it better :)
Rui

---

### Post by handy on 2008-01-28
> **Rui Pais said:**
> 
Hi Handy.
Thanks for your reports and comments! 
They very appreciated :)

Sorry to hear about your problems. They are in fact Xorg issues. 

There's plenty threads around where installer, after done a correct work on liveCD, on installed system creates a bad xorg.conf file.
Since Xorg versions from Gutsy and Oz are different, that may explain why that only happen to you on Oz OS.

There are 2 ways of solve that. The first it's the standard:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and restart X server (ctrl+alt+backspace)

One thing most people don't know and i think it's important it's the relation of xorg.conf files with your OS. Thats a configuration file, easy. But it's related with your hardware, not with your Linux or Xserver version. A good working xorg.conf should work with all other Linuxs you install. 
(I used to have 17'' Philips monitors that were hard even under Windows. Once i made a correct xorg.conf i put it on a pen and any Linux i tried i always replace xorg.conf without even care with the one installed)

So, of course, the second way it's to just copy a working xorg.conf from another distro where it works. Note that it must have both same driver so maybe go for the first approach in first place. 

Thanks for your reply Rui. :-)

That is very useful information regarding the xorg.conf file.  I have another machine running Ubuntu 7.10, perfectly.  So I will make a copy of that to keep for future uses.

> **Rui Pais said:**
> 
About NVidia drivers, the easier and reliable way i know of get those it's using [envy]("http://albertomilone.com/nvidia_scripts1.html"). Here it's a link to deb:
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb)

Please, let me know how it goes.
good luck.

Yes, I did actually give envy a try, but it did nothing?

Not a line of code for any of the commands in the terminal.  So I uninstalled it, without a line of code following that command either?

I wonder if I actually ever even installed it... :lolflag:

Anyway, I will pursue these things tomorrow I expect, & see if I can get a little further down the track.

---

### Post by Rui Pais on 2008-01-28
> **handy said:**
> Thanks for your reply Rui. :-)

That is very useful information regarding the xorg.conf file.  I have another machine running Ubuntu 7.10, perfectly.  So I will make a copy of that to keep for future uses.


A good option. keep in mind that until you managed to install nvidia prop. drivers, you must have a line 
```
 Driver         "nv"
```
instead of 
```
 Driver         "nvidia"
```
And some settings for nvidia don't work with nv.

Try first install Nvidia drivers.

Have you tried to run envy with -t or -g flag?
envy -t  <- command line for terminal or console
envy -g <- GUI interface

> **handy said:**
> 
Yes, I did actually give envy a try, but it did nothing?

Not a line of code for any of the commands in the terminal.  So I uninstalled it, without a line of code following that command either?

I wonder if I actually ever even installed it... :lolflag:

Anyway, I will pursue these things tomorrow I expect, & see if I can get a little further down the track.

Another alternative it's the ubuntu way:
Have you tried run:
restricted-manager from a console or a terminal and enabled:
"NIVIA acceletared graphics card" option?

---

### Post by handy on 2008-01-28
Thanks for your reply Rui,

I played around with the xorg.conf file, a couple of times, I had to to get the xserver working.  I'm aware of the nv & nvidia settings.

I did actually use the envy -t setting when I tried to install it.  I had to.

I will try envy again tomorrow, & will use the -g command.  It will be nice to see something happening. :-) 

I did not run restricted manager from a console, but I did use synaptic & made sure the restricted drivers were installed & new_nvidia_glx, or how ever it is named.

---

### Post by zubrug on 2008-01-28
Tried the live cd,
I ended up getting it to work with f6 + all generic ide. (this has been the story with most install's on this system - Phenom 9500, a770m-a elitegroup mobo, 8500gt, and pata hd)
The OZ installed without any trouble, nvidia-glx-new from Synaptic worked, installed 64 bit opera, YeeeHaaaaa!

Very nice, ........... will set up a torrent and cruise the cafe.

---

### Post by RAV TUX on 2008-01-28
> **zubrug said:**
> Tried the live cd,
I ended up getting it to work with f6 + all generic ide. (this has been the story with most install's on this system - Phenom 9500, a770m-a elitegroup mobo, 8500gt, and pata hd)
The OZ installed without any trouble, nvidia-glx-new from Synaptic worked, installed 64 bit opera, YeeeHaaaaa!

Very nice, ........... will set up a torrent and cruise the cafe.Awesome news! Thanks for seeding and look forward to seeing you at the Cafe.

Glad to see the Oz install worked for you , and glad to hear your using  the 64bit Opera also.

Rui  will now bring more people to e17 then ever before.

Thanks be to Rui. ;)

---

### Post by RAV TUX on 2008-01-28
> **handy said:**
> I'm installing now.

Oz looks great on the LiveCD, & my internet worked straight away.

Having spent all yesterday dealing with problems in the DreamLinux 3 Beta install, Oz looks to be plain sailing already! :-D

> **chris4585 said:**
> Rui Pais i have just tested ozos and it is amazing, alot of programs were super fast, but one error i did get was with gnumeric, it wouldnt load for some reason, great job! (woops i left this open for a day, so this is a late message)

This is awesome news to hear.

I can hardly wait to install the OzOs RC myself, I left the Torrent running in Opera at home, hopefully tomorrow when I get home the download will be complete and I will be seeding.

---

### Post by init1 on 2008-01-29
Great! I'll have to try it out. I wasn't able to create my own (I've been busy recently, and I had many problems with the software I was using) but hopefully I can be of some use in this project. :D I'll try the ISO in any case (if my CD burner is working)

---

### Post by DJiNN on 2008-01-29
Does anyone know if e17 is compiled for 64 bit or is it 32 bit only? Just curious as at the moment i'm running 64bit Xubuntu & "Loving it!". :)

I'm going to see if i can also grab the live CD iso & have a looksee..... i LOVE the screenshot above.... Looks great! I've been meaning to spend some time getting into e17, so may as well start now! :)

---

### Post by p_quarles on 2008-01-29
Actually, the live CD for OzOS is 64-bit only at this point.

---

### Post by DJiNN on 2008-01-29
> **p_quarles said:**
> Actually, the live CD for OzOS is 64-bit only at this point.

Thanks... that's great.... just what i'm after! Can't get the link to download though (have to join the forum or somesuch?) so i'll see if there's a torrent available? Can't wait to give it a try. :)

---

### Post by p_quarles on 2008-01-29
[http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent)

---

### Post by RAV TUX on 2008-01-30
> **init1 said:**
> Great! I'll have to try it out. I wasn't able to create my own (I've been busy recently, and I had many problems with the software I was using) but hopefully I can be of some use in this project. :D I'll try the ISO in any case (if my CD burner is working)

Init1 it is great to hear from you,...

I am currently seeding the torrent

I look forward to your help in the OzOs project.

email me at ravtux AT gmail DOT com, if you need anything or just look for Rui or myself at the [CafeLinux.org Forum]("http://www.cafelinux.org/forum/")

Again I look forward to you helping us out ;)

---

### Post by RAV TUX on 2008-01-30
> **DJiNN said:**
> Does anyone know if e17 is compiled for 64 bit or is it 32 bit only? Just curious as at the moment i'm running 64bit Xubuntu & "Loving it!". :)

I'm going to see if i can also grab the live CD iso & have a looksee..... i LOVE the screenshot above.... Looks great! I've been meaning to spend some time getting into e17, so may as well start now! :)

> **p_quarles said:**
> Actually, the live CD for OzOS is 64-bit only at this point.

Thanks for providing the needed info p_quarles. ;)

DJiNN OzOs is a bit unique that the 64bit version was released first. 

I hope you enjoy it.

> **DJiNN said:**
> Thanks... that's great.... just what i'm after! Can't get the link to download though (have to join the forum or somesuch?) so i'll see if there's a torrent available? Can't wait to give it a try. :)

The link is open and available to all no need to join the Forum but we would be overjoyed to see you. ;)

[http://www.cafelinux.org/forum/](http://www.cafelinux.org/forum/)


> **p_quarles said:**
> [http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.torrent)

Thanks again p_quarles, for providing a direct link to the torrent.

There are two other places it is readily available for everyones downloading enjoyment:

1. On the download page of the OzOS|apt:foo webpage:

[http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents](http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents)

2. On the Download section of the CafeLinux.org Homepage:

[http://www.cafelinux.org/Downloads/oz-os/iso/](http://www.cafelinux.org/Downloads/oz-os/iso/)

Please remember to check the md5

[IMG]http://www.cafelinux.org/icons/unknown.gif[/IMG][oz-os-RC1.0-livecd-amd64.iso.md5]("http://www.cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.0-livecd-amd64.iso.md5")

---

### Post by Shazaam on 2008-01-30
+1 on this....

"One thing most people don't know and i think it's important it's the relation of xorg.conf files with your OS. Thats a configuration file, easy. But it's related with your hardware, not with your Linux or Xserver version. A good working xorg.conf should work with all other Linuxs you install. So, of course, the second way it's to just copy a working xorg.conf from another distro where it works".

I have copied a working xorg.conf from a Dapper install running older nvidia drivers and replaced a non-working version in Gutsy using the 169.07 nvidia drivers with success.:)

---

### Post by RAV TUX on 2008-01-30
> **Shazaam said:**
> +1 on this....

"One thing most people don't know and i think it's important it's the relation of xorg.conf files with your OS. Thats a configuration file, easy. But it's related with your hardware, not with your Linux or Xserver version. A good working xorg.conf should work with all other Linuxs you install. So, of course, the second way it's to just copy a working xorg.conf from another distro where it works".

I have copied a working xorg.conf from a Dapper install running older nvidia drivers and replaced a non-working version in Gutsy using the 169.07 nvidia drivers with success.:)

This is a very important point I wish I would have known first learning about Xorg. ;)

Thanks again Rui for sharing this important bit of knowledge.

---

### Post by handy on 2008-01-30
Sorry I haven't had time to follow up on Rui Pais advice, I won't be able to proceed until next week.  I will feed back when I have something for you.

---

### Post by DJiNN on 2008-01-30
> **RAV TUX said:**
> Thanks for providing the needed info p_quarles. ;)

DJiNN OzOs is a bit unique that the 64bit version was released first. 

I hope you enjoy it.

Hi RAV, thanks for the reply. I've been trying out a few 64bit distros lately, so saw this one & as i'm also after having a go with Enlightenment, this looks like it could be a great step forwards..... :)  I'm just downloading now, and MANY THANKS to **p_quarles  **for the torrent link.... much appreciated.

> The link is open and available to all no need to join the Forum but we would be overjoyed to see you. ;)

[http://www.cafelinux.org/forum/](http://www.cafelinux.org/forum/) 

OK, i'll pop on over & register. Thanks for the invite. :) Hopefully this won't take too long to D/L so within a few days i'll be back with some thoughts etc..... really looking forward to this. 64 bit is the way to go, definitely!

---

### Post by DJiNN on 2008-01-30
Hey RAV, me again..... i just realised that i'm already registered with CafeLinux, did it back in Sept 2k6, but it's been that long since i've been over there that i almost forgot!! :oops: :grin: 

Where does the time go eh? Anyway, i've just logged in, and as i'm giving this OS a try i'll probably be around asking some questions etc. :) See you there.....

---

### Post by Rui Pais on 2008-01-30
> **RAV TUX said:**
> This is a very important point I wish I would have known first learning about Xorg. ;)

Thanks again Rui for sharing this important bit of knowledge.

No problem :)

I always prefer to point to that little aspect, a little confusing (it's Xorg that creates the file, but the correct one really depends only on graphic card and driver alone...) 
The process of creation it's just a script automatizing the hardness of that configuration.

Although the classic, run *sudo dpkg-reconfigure -phigh xserver-xorg* it's always good, the user don't learn much...

---

### Post by Rui Pais on 2008-01-30
> **init1 said:**
> Great! I'll have to try it out. I wasn't able to create my own (I've been busy recently, and I had many problems with the software I was using) but hopefully I can be of some use in this project. :D I'll try the ISO in any case (if my CD burner is working)

Uff, and with all this, i keep  forgetting to mail at least some words for you, init1...
I'm sorry about that, but as the process of making the live CD became more and more wild (and my free time became smaller lately, that make things worst) i focused on do what it was possible and keep go apart from our original project... But i should have at list keep you informed. Please excuse me.

In the end maybe it's better to have a full working e17 on liveCD, instead of just an installer that would compile it, because users can immediately see what it's all about. Of course, like you, i like light installs and small CD. If you still have time, and manage to fix your hardware and keep interesting in doing a minimal version of OzOS install, just let me know and if i can help in any way.

(I will mail you with some other suggestions i'm in the meddle of the process of repack the oz-desktop to make it more flexible)

---

### Post by Rui Pais on 2008-01-30
> **handy said:**
> Sorry I haven't had time to follow up on Rui Pais advice, I won't be able to proceed until next week.  I will feed back when I have something for you.

No problem, we'll be around ;)
When you get something, just say, either doubts, issues as comments.
:)

---

### Post by init1 on 2008-01-30
> **Rui Pais said:**
> Uff, and with all this, i keep  forgetting to mail at least some words for you, init1...
I'm sorry about that, but as the process of making the live CD became more and more wild (and my free time became smaller lately, that make things worst) i focused on do what it was possible and keep go apart from our original project... But i should have at list keep you informed. Please excuse me.

In the end maybe it's better to have a full working e17 on liveCD, instead of just an installer that would compile it, because users can immediately see what it's all about. Of course, like you, i like light installs and small CD. If you still have time, and manage to fix your hardware and keep interesting in doing a minimal version of OzOS install, just let me know and if i can help in any way.

(I will mail you with some other suggestions i'm in the meddle of the process of repack the oz-desktop to make it more flexible)
Yeah I like the idea of Live CD because I know that I probably wouldn't have bothered with a manual install if I hadn't had any interest in the project. Maybe I could get a 32-bit CD working, especially since I don't have any 64-bit computers.

---

### Post by RAV TUX on 2008-01-30
> **DJiNN said:**
> Hey RAV, me again..... i just realised that i'm already registered with CafeLinux, did it back in Sept 2k6, but it's been that long since i've been over there that i almost forgot!! :oops: :grin: 

Where does the time go eh? Anyway, i've just logged in, and as i'm giving this OS a try i'll probably be around asking some questions etc. :) See you there.....

DjiNN, I am overjoyed to see you active again on the forums, and this time for a very good reason. 

OzOS will be here for the long haul, it is good to see the beginning starting so beautifully.

Rui Pais as the OzOS architect has transcended enlightenment limitations and brings to all a true work of art.

"...and I think to myself what a wonderful world"
(does anybody remember who sang this?)

---

### Post by p_quarles on 2008-01-30
> **RAV TUX said:**
> (does anybody remember who sang this?)
Many, but Louis Armstrong most famously.

---

### Post by Rui Pais on 2008-01-31
> **init1 said:**
> Yeah I like the idea of Live CD because I know that I probably wouldn't have bothered with a manual install if I hadn't had any interest in the project. Maybe I could get a 32-bit CD working, especially since I don't have any 64-bit computers.

Great! 
I'll mail you to suggest 2 ways i can think we can easily do this and keep both versions synchronized. :)

---

### Post by snakeeyes on 2008-01-31
Will there be a Hardy Heron version of this as well?

---

### Post by Rui Pais on 2008-01-31
> **snakeeyes said:**
> Will there be a Hardy Heron version of this as well?

Yes, it will go side by side with Ubuntu versions, even may be released sooner than official Hardy Heron (from an RC) if it works stable enough.

Meanwhile you can always do it by this method:
[http://ubuntuforums.org/showthread.php?t=623803](http://ubuntuforums.org/showthread.php?t=623803)

hth

---

### Post by DJiNN on 2008-01-31
Hi Rui & RAV. Just installed RC1 and it installed fine, but the screen's stuck at 800x600 and the mouse keeps dropping in & out...?? 

I installed it onto a spare partition that i have on an external (USB 2) hard drive, so don't know if this has any relation to these problems. 

I've had a look at xorg.conf & that looks fine, so i'm going to re-install on another partition later on, just to see if it changes anything.

Does look very nice though.... :)  I love the programs that you have chosen for it, really nice mixture & not too "Heavyweight". 

I'll be back soon with some more details of what's happening.

---

### Post by Rui Pais on 2008-02-01
> **DJiNN said:**
> Hi Rui & RAV. Just installed RC1 and it installed fine, but the screen's stuck at 800x600 and the mouse keeps dropping in & out...?? 

I installed it onto a spare partition that i have on an external (USB 2) hard drive, so don't know if this has any relation to these problems. 

I've had a look at xorg.conf & that looks fine, so i'm going to re-install on another partition later on, just to see if it changes anything.

Does look very nice though.... :)  I love the programs that you have chosen for it, really nice mixture & not too "Heavyweight". 

I'll be back soon with some more details of what's happening.

Many thanks. :)
I'm very pleased that general looks and options are considered good.

About your issues, weird screen resolution apparently are frequent with Xorg version that Gutsy (and OzOS) uses...

There are several way to try to get things fix. You can try to run 'Screens and graphics" from main menu (displayconfig-gtk from a terminal). Or you can try to fix/improve xorg.conf by running:
sudo dpkg-reconfigure -phigh xserver-xorg

But first of all i suggest you check my comment on this post:
[http://ubuntuforums.org/showpost.php?p=4222211&postcount=32](http://ubuntuforums.org/showpost.php?p=4222211&postcount=32)

Hope some of those help. 
Please post your results, ok?

---

### Post by DJiNN on 2008-02-01
HI Rui.... thanks for the reply and the help. I'll get stuck in over the weekend & see if i can get it sorted out. I'll get a working xorg.conf & put that in..... maybe that will make a difference. I'll let you know how it goes anyway. :) 

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

I've tried that on 7.10 a few times now, and for some reason it just produces the most BASIC xorg.conf i've ever seen, that never seems to work. :)   Maybe that's because of that bug that you spoke about?

---

### Post by RAV TUX on 2008-02-01
> **p_quarles said:**
> Many, but Louis Armstrong most famously.Ahhh, Thanks I enjoy that song very much and for some reason it runs through my head.

---

### Post by DJiNN on 2008-02-04
Hey RAV, as you know i have now installed Oz, and i have finally got it working - and i'm soooo impressed with it, that i just had to put a post in here saying so. :)

If there's anyone that reads this that's wondering what OzOs is like.... If you have a 64 bit machine & you want a really fantastic OS, both in looks & functionality, and also one that's based on Debian/Ubuntu and uses the Ubuntu repos, then this is the one for you. Download it & give it a try..... you won't be disappointed. 

Thanks for all your help RAV..... see you at Cafe Linux? :)

---

### Post by RRS on 2008-02-04
Only had about 15 or 20 minutes to play with the live cd yesterday but was impressed. Hope to install and explore further before weekend.

Guess I should probably start spending a bit more time at CafeLinux too, maybe even register too, :oops:

BTW, seeding the torrent in case anyone still needs it, i'll try to keep it open as long as there's activity.

---

### Post by RAV TUX on 2008-02-04
> **DJiNN said:**
> Hey RAV, as you know i have now installed Oz, and i have finally got it working - and i'm soooo impressed with it, that i just had to put a post in here saying so. :)

If there's anyone that reads this that's wondering what OzOs is like.... If you have a 64 bit machine & you want a really fantastic OS, both in looks & functionality, and also one that's based on Debian/Ubuntu and uses the Ubuntu repos, then this is the one for you. Download it & give it a try..... you won't be disappointed. 

Thanks for all your help RAV..... see you at Cafe Linux? :)

Thanks DJiNN, I am just over joyed that enjoy OzOs so much. This makes me the happiest to hear happy comments from OzOs users.

OzOs makes people Happy!

;)

> **RRS said:**
> Only had about 15 or 20 minutes to play with the live cd yesterday but was impressed. Hope to install and explore further before weekend.

Guess I should probably start spending a bit more time at CafeLinux too, maybe even register too, :oops:

BTW, seeding the torrent in case anyone still needs it, i'll try to keep it open as long as there's activity.

Awesome news I hope to see you at CafeLinux.org Forum also...

Glad you like OzOs.

Also for all out there OzOs is now on LinuxTracker.org...Thanks to CatWalk:

[OzOs Torrent Link on LinuxTracker]("http://linuxtracker.org/index.php?page=torrent-details&id=a275c71539d8228e0608528868ebb8029a3d0af4")

---

### Post by RAV TUX on 2008-02-06
> **DJiNN said:**
> HI Rui.... thanks for the reply and the help. I'll get stuck in over the weekend & see if i can get it sorted out. I'll get a working xorg.conf & put that in..... maybe that will make a difference. I'll let you know how it goes anyway. :) 

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```I've tried that on 7.10 a few times now, and for some reason it just produces the most BASIC xorg.conf i've ever seen, that never seems to work. :)   Maybe that's because of that bug that you spoke about?

Did you sort through this?

---

### Post by DJiNN on 2008-02-06
Hi RAV.....

Yes, i finally got it all sorted out by installing "Envy" & letting that do it all..... worked like a charm! :)

Having problems with Networking (Local shares etc) at the moment. Is there anything built into Enlightenment to deal with this or do i need to install something like Nautilus or Konqueror etc?  

Otherwise all is running well..... made a few mistakes etc but it's all part of the learning process. :)

---

### Post by smartboyathome on 2008-02-06
I think you have to install Nautilus. I had to do that in order to connect to samba at a friend's house.

---

### Post by Rui Pais on 2008-02-06
> **DJiNN said:**
> Hi RAV.....

Yes, i finally got it all sorted out by installing "Envy" & letting that do it all..... worked like a charm! :)

Having problems with Networking (Local shares etc) at the moment. Is there anything built into Enlightenment to deal with this or do i need to install something like Nautilus or Konqueror etc?  

Otherwise all is running well..... made a few mistakes etc but it's all part of the learning process. :)

Yes i agree with smartboyathome... don't know nothing from e17 specifics for that.

Or maybe something from repos lighter than nautilus (i'm very curious to try the new nautilus at hardy, finally they move to the new GVFS so it would became lighter and finally flexible enough to get some really needed updates).

PS I answered too [at cafelinux]("http://cafelinux.org/forum/index.php/topic,1003.0.html") :)

---

### Post by leftorvo on 2008-02-07
i remember seeing screenshots of this distro on a photo gallery site (possibly run by one of the makers of it?) and it had a really nice E17 configuration, I wanted to copy it :P

---

### Post by RAV TUX on 2008-02-07
> **leftorvo said:**
> i remember seeing screenshots of this distro on a photo gallery site (possibly run by one of the makers of it?) and it had a really nice E17 configuration, I wanted to copy it :PCopy of the image? or the e17 configuration?

---

### Post by leftorvo on 2008-02-08
the configuration, I remember that it looked good and I wanted to configure my E17 like that.

---

### Post by Rui Pais on 2008-02-09
> **leftorvo said:**
> the configuration, I remember that it looked good and I wanted to configure my E17 like that.

Well, you can install my themes alone (e17-themes on CafeLinux repos). The rest, several shelfs set to invisible and some to auto-hide.

I take advantage of pager be full transparent to set them to a "huge" size, thats mimics well the several virtual desktops... 

If you need something i not mentioned, just say...



(RAV TUX nice avatar ;))

---

### Post by RAV TUX on 2008-02-09
> **Rui Pais said:**
> 



(RAV TUX nice avatar ;))

Thanks, that's me and my wife. ;)

---

### Post by yabbadabbadont on 2008-02-09
If you ever run into someone there in Portland, who looks quite like you, but with a buzz cut, then tell Frank I said "Hi."  :D

---

### Post by Tux Aubrey on 2008-02-10
> **RAV TUX said:**
> Thanks, that's me and my wife. ;)

What a relief.  I thought some poor sick woman was actually enjoying being groped by Michael Moore.  My apologies to your wife.:)

---

### Post by ahaslam on 2008-02-10
Trying it in Qemu, it faps out after a few seconds. Anyone got it virtualized?
```
[ahaslam@voodoo ~]$ qemu-system-x86_64 -M pc -cdrom /home/ahaslam/isos/oz-os-RC1.0-livecd-amd64.iso -m 512 -kernel-kqemu -net nic,vlan=0 -net user,vlan=0,hostname=emu  -boot d
RAX=0000000000000000 RBX=ffffffff80536780 RCX=000000000000001f RDX=0000000000000000
RSI=000000000000001f RDI=ffffffff80536780 RBP=0000000000000282 RSP=ffffffff805d7ec0
R8 =0000000000000000 R9 =ffffffff805ce880 R10=ffff810080a3d000 R11=0000000000000000
R12=0000000000000006 R13=0000000000000000 R14=0000000000000007 R15=0000000000000000
RIP=ffffffff8023faeb RFL=00010287 [--S--PC] CPL=0 II=0 A20=1 SMM=0 HLT=0
ES =0000 0000000000000000 00000000 00000000
CS =0010 0000000000000000 ffffffff 00affb00
SS =0018 0000000000000000 ffffffff 00cff300
DS =0000 0000000000000000 00000000 00000000
FS =0000 0000000000000000 00000000 00000000
GS =0000 ffffffff80560000 00000000 00000000
LDT=0000 0000000000000000 00000000 00008000
TR =0040 ffff810001008000 0000206f 00008900
GDT=     ffffffff80580000 00000080
IDT=     ffffffff805de000 00000fff
CR0=8005003b CR2=0000000000711120 CR3=000000001de8f000 CR4=000006e0
Unsupported return value: 0xffffffff
```

---

### Post by Tux Aubrey on 2008-02-10
[QUOTE=ahaslam;4304514]Trying it in Qemu, it faps out after a few seconds. Anyone got it virtualized?

I run OzOs in Virtual Box - BUT it is the 32 bit version (just Xubuntu plus the OzOs desktop installed with Rui's deb).

The current RC is 64bit only and will not run in a 32 bit VM. (I should have known this, but I tried it anyway!)

---

### Post by ahaslam on 2008-02-10
I'm on 64bit, as you can see from the command.

---

### Post by Rui Pais on 2008-02-10
> **RAV TUX said:**
> Thanks, that's me and my wife. ;)

:) I recognized you from a movie (you are "acting" in front of a desolated and windy mountain countryside... you look cold ) 
You are preparing for a great St. Valentin's day :lol:

---

### Post by Rui Pais on 2008-02-10
> **ahaslam said:**
> Trying it in Qemu, it faps out after a few seconds. Anyone got it virtualized?
```
[ahaslam@voodoo ~]$ qemu-system-x86_64 -M pc -cdrom /home/ahaslam/isos/oz-os-RC1.0-livecd-amd64.iso -m 512 -kernel-kqemu -net nic,vlan=0 -net user,vlan=0,hostname=emu  -boot d
RAX=0000000000000000 RBX=ffffffff80536780 RCX=000000000000001f RDX=0000000000000000
RSI=000000000000001f RDI=ffffffff80536780 RBP=0000000000000282 RSP=ffffffff805d7ec0
R8 =0000000000000000 R9 =ffffffff805ce880 R10=ffff810080a3d000 R11=0000000000000000
R12=0000000000000006 R13=0000000000000000 R14=0000000000000007 R15=0000000000000000
RIP=ffffffff8023faeb RFL=00010287 [--S--PC] CPL=0 II=0 A20=1 SMM=0 HLT=0
ES =0000 0000000000000000 00000000 00000000
CS =0010 0000000000000000 ffffffff 00affb00
SS =0018 0000000000000000 ffffffff 00cff300
DS =0000 0000000000000000 00000000 00000000
FS =0000 0000000000000000 00000000 00000000
GS =0000 ffffffff80560000 00000000 00000000
LDT=0000 0000000000000000 00000000 00008000
TR =0040 ffff810001008000 0000206f 00008900
GDT=     ffffffff80580000 00000080
IDT=     ffffffff805de000 00000fff
CR0=8005003b CR2=0000000000711120 CR3=000000001de8f000 CR4=000006e0
Unsupported return value: 0xffffffff
```

Hi ahaslam,
Thanks for the interest in OzOS!

That specific error i don't know...

Here, with qemu, i couldn't never boot any gutsy based version variation (from original Gutsy to OzOS... make testing iso much harder).

Maybe trying with other VM...

---

### Post by ahaslam on 2008-02-10
Xubuntu64 7.10 works in Qemu with that command, at least here. I look forward to your final release, which I'll burn & try properly. ;)

---

### Post by smartboyathome on 2008-02-10
edit: wrong topic :(

---

### Post by RAV TUX on 2008-02-11
> **Rui Pais said:**
> :) I recognized you from a movie (you are "acting" in front of a desolated and windy mountain countryside... you look cold ) 
You are preparing for a great St. Valentin's day :lol:
I have more videos that I have yet to upload.

V-day...romance is in the air. ;)

---

### Post by Rui Pais on 2008-02-12
> **ahaslam said:**
> Xubuntu64 7.10 works in Qemu with that command, at least here. I look forward to your final release, which I'll burn & try properly. ;)

Well, if you can run Xubuntu10 7.10 with qemu than you should be able to run OzOS (since it's based precisely on Xubuntu)...

Have you checked md5sum of iso? Apart a bad iso i have no idea why it work with one and fails with the other :confused:

---

### Post by koleoptero on 2008-02-12
Do you plan to release a 32bit iso for RC1 or are you going to wait for the final release?

---

### Post by Rui Pais on 2008-02-12
> **koleoptero said:**
> Do you plan to release a 32bit iso for RC1 or are you going to wait for the final release?

No a 32bits RC should be release first. 
Another person it's take care of 32b iso (that should mirror RC1 configs, but have updates)... maybe we will alternate RCs till things are running smooth...

Thanks for the interest on Oz :)

Hope 32 bits will be out soon.

---

### Post by RAV TUX on 2008-02-13
> **Rui Pais said:**
> No a 32bits RC should be release first. 
Another person it's take care of 32b iso (that should mirror RC1 configs, but have updates)... maybe we will alternate RCs till things are running smooth...

Thanks for the interest on Oz :)

Hope 32 bits will be out soon.How is the 32-bit release coming?

---

### Post by koleoptero on 2008-02-13
> **Rui Pais said:**
> No a 32bits RC should be release first. 
Another person it's take care of 32b iso (that should mirror RC1 configs, but have updates)... maybe we will alternate RCs till things are running smooth...

Thanks for the interest on Oz :)

Hope 32 bits will be out soon.

I will be waiting :) I want to test it normally from a live cd cause most of the DEs don't agree with my intel 915GM graphics card. But I really like Enlightenment.

---

### Post by Zero Prime on 2008-02-13
I'm downloading now to test in VBox.  It looks good from the screen shots.

---

### Post by RAV TUX on 2008-02-13
> **koleoptero said:**
> I will be waiting :) I want to test it normally from a live cd cause most of the DEs don't agree with my intel 915GM graphics card. But I really like Enlightenment.great!

> **Zero Prime said:**
> I'm downloading now to test in VBox.  It looks good from the screen shots.Awesome, glad to here you'll be trying OzOs, and Thanks for joining the [CafeLinux Forum]("http://www.cafelinux.org/forum/").

---

### Post by RAV TUX on 2008-02-17
> **yabbadabbadont said:**
> If you ever run into someone there in Portland, who looks quite like you, but with a buzz cut, then tell Frank I said "Hi."  :D

Will do.

> **Tux Aubrey said:**
> What a relief.  I thought some poor sick woman was actually enjoying being groped by Michael Moore.  My apologies to your wife.:)

HAHA...Very Funny! :lolflag:

---

### Post by Rui Pais on 2008-03-05
Hi all.

Just a quick note to call your attention to 2 new apps on OzOS repos.

The 1st it's the excellent, well known, **Envy** by Alberto Milone (tseliot on this forum).
You can get it now, after a *sudo apt-get update*, simply with:
```
sudo apt-get install envy
```
Thanks tseliot!

The 2nd it's a meta-package, oz-phys-math.
Check the announcement here:
[http://cafelinux.org/forum/index.php/topic,1087.0.html](http://cafelinux.org/forum/index.php/topic,1087.0.html)

Have fun!

(RC2 almost done with the previous bugs solved...)

---

### Post by RAV TUX on 2008-03-11
> **Rui Pais said:**
> Hi all.

Just a quick note to call your attention to 2 new apps on OzOS repos.

The 1st it's the excellent, well known, **Envy** by Alberto Milone (tseliot on this forum).
You can get it now, after a *sudo apt-get update*, simply with:
```
sudo apt-get install envy
```Thanks tseliot!

The 2nd it's a meta-package, oz-phys-math.
Check the announcement here:
[http://cafelinux.org/forum/index.php/topic,1087.0.html](http://cafelinux.org/forum/index.php/topic,1087.0.html)

Have fun!

(RC2 almost done with the previous bugs solved...)Awesome work Rui, I look forward to RC2.

---

### Post by Rui Pais on 2008-03-11
> **RAV TUX said:**
> Awesome work Rui, I look forward to RC2.

Soon, soon. :)
64bits it's ready. This time we will put a 64 and a 32 bits version out at the same time. :D

---

### Post by /home on 2008-03-11
I would try it out if i had a 64bit That worked
when is a 32bit Oz Os cd coming out?

---

### Post by Rui Pais on 2008-03-11
> **/home said:**
> I would try it out if i had a 64bit That worked
when is a 32bit Oz Os cd coming out?

Hi, not sure exactly. A couple of days i think.
I'll put an announcement here.

Thanks for your interest!
:)

---

### Post by RAV TUX on 2008-03-13
> **Rui Pais said:**
> Soon, soon. :)
64bits it's ready. This time we will put a 64 and a 32 bits version out at the same time. :D

> **/home said:**
> I would try it out if i had a 64bit That worked
when is a 32bit Oz Os cd coming out?

> **Rui Pais said:**
> Hi, not sure exactly. A couple of days i think.
I'll put an announcement here.

Thanks for your interest!
:)

Sweet! anticipation.

---

### Post by berZirker on 2008-03-21
Couple things:

I downloaded the ISO from both sources, but neither matched the md5 sum from [http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents](http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents).  I burned both to disks and tried the live cds just to have a look around.  The first problem was that everything was extremely slow.  The second that the keypad was acting as though the function key was held down on my laptop.  This emulates a keypad over the uio,jkl, and m keys.  I don't mind doing a little tinkering, but I thought I would point this out, and ask if the different md5sum might have something to do with it.  Looks great though, and I like the modified E windows.

---

### Post by Rui Pais on 2008-03-25
> **berZirker said:**
> Couple things:

I downloaded the ISO from both sources, but neither matched the md5 sum from [http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents](http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents).  I burned both to disks and tried the live cds just to have a look around.  The first problem was that everything was extremely slow.  The second that the keypad was acting as though the function key was held down on my laptop.  This emulates a keypad over the uio,jkl, and m keys.  I don't mind doing a little tinkering, but I thought I would point this out, and ask if the different md5sum might have something to do with it.  Looks great though, and I like the modified E windows.

Hi berZirker, sorry this late answer (been out-of-town)...

The md5sum must be:
```
a0dc3a94e580fc616fa31161b22f6ba2  oz-os-RC1.0-livecd-amd64.iso
```
If that was not the case, the iso would be corrupted.

It's stange that you seems to be able to boot it... 
maybe they one of your copies are ok and you have some problematic hardware (did it work well under Ubuntu?) or maybe some corruption of iso happened but just on some few bits that make it bootable but with weird effects...

Please, do you mind to check your md5sums?...

---

### Post by Rui Pais on 2008-04-05
Hi all.

A new RC of OzOS it's available for download.
It's based on Gutsy and it's 64bits.

You can download now:
[http://cafelinux.org/Downloads/oz-os/iso/](http://cafelinux.org/Downloads/oz-os/iso/)

if possible by [Torrent]("http://cafelinux.org/Downloads/oz-os/iso/oz-os-RC1.2-livecd-amd64.iso.torrent")


This release correct/solves some major problems:
- Identify OS as OzOS and on grub menu.
- Repos of Cafelinux works now after install.
and
- new module "echo" for sound volume by default
- Wicd instead of Network-Manager (not useful under e17)
- e17 0.16.999.042,
- all recent updates of Gutsy
- some minor tweaks...

Hardy will be out soon, so i think it's better base the new versions on Hardy.
I hope soon i finish 32 and a 64bits on that base. 

Hope you liked.

Rui

---

### Post by Rui Pais on 2008-04-15
Hi all,
the so awaited 32 bits version of OzOS, codename 'Audrey Hepburn on crack', it's finally available! :D

I tried to keep the look and features as close as possible with RC1.2 64bits, but underneath it's a very different thing.
Its a Hardy base, with all updates till 14/Apr/08.


Download and General info page, it's here:
**[http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents](http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents)**


You can get it directly [**from here** (click me).](http://cafelinux.org/Downloads/oz-os/iso)

Torrent it's:
[color=blue]**[http://www.cafelinux.org/Downloads/oz-os/iso/oz-os-0.5-livecd-i386.iso.torrent](http://www.cafelinux.org/Downloads/oz-os/iso/oz-os-0.5-livecd-i386.iso.torrent)**[/color]
(just click to get your hot new OzOS iso) 

and 
[LinuxTracker torrent page it's here (click me)](http://linuxtracker.org/index.php?page=torrent-details&id=58748fc4a52eaf895d5bada81a76fc8a2a1553cc).

If possible go for the torrent and keep seeding, at least for a while after you get it. 
_______________________________


As usual it's a liveCD. Installation it's done by clicking on install icon:               [INDENT][IMG]http://cafelinux.org/forum/index.php?action=dlattach;topic=974.0;attach=2861;image[/IMG][/INDENT]
and press enter if it ask you for a password.

[COLOR="Blue"]**This release includes all corrections of RC1.2 and the news are:**[/COLOR]
- Recent e17 0.16.999.042,
- new module "echo" for sound volume by default,
- Wicd instead of Network-Manager (disable by default, require activation of service),
- A Torrent installed by default,
- Kernel 2.6.24-16,
- all updates of Hardy (14/April)

[COLOR="Navy"]* Included applications:[/COLOR]
 xfce-terminal - terminal
 Scite - text/code editor
 Abiword - text processor
 Thunar - File manager
 Transmission - Torrent client
 Firefox 2.0.0.12 (default) and Firefox 3.0beta5
 Thunderbird2 - email client
 and more (gimp, gpicview, stalonetray, gtk-theme-switch, meld, geany, etc.)


Hope you all like!


(Check [this announcement on Cafelinux too]("http://cafelinux.org/forum/index.php/topic,1283.0.html") too.) 

For more info on known issues, bugs, workarounds and tips, check:
[http://cafelinux.org/forum/index.php/topic,1283.msg4010.html#msg4010](http://cafelinux.org/forum/index.php/topic,1283.msg4010.html#msg4010)

Rui

---

### Post by LaRoza on 2008-04-15
I will try it out. I will likely install it for the full experience (probably a dual boot)

Torrenting in the background. Will be seeding.

---

### Post by Rui Pais on 2008-04-15
OzOS 32bits New version 0.5 (Hardy based) it's available. 
Thread here: [http://ubuntuforums.org/showthread.php?t=756038](http://ubuntuforums.org/showthread.php?t=756038)

Hope you like it :)

---

### Post by Rui Pais on 2008-04-15
> **LaRoza said:**
> I will try it out. I will likely install it for the full experience (probably a dual boot)

Torrenting in the background. Will be seeding.

Many thanks LaRoza!!

For the interest on OzOS and for help seeding :)
Very appreciated both!

Let me know about your opinion and experience with with it, ok?

Rui

---

### Post by myusername on 2008-04-15
sweet! i have been waiting on this

---

### Post by Freddy on 2008-04-15
You might have to update OzOS download page Rui, your signature link points to a page with no downloads and the download tab points to a page with no downloads for the 32bit version :).

Btw, great version :).

---

### Post by LaRoza on 2008-04-15
Torret is done for me. I am a "seeder" now.

Burning...

---

### Post by LaRoza on 2008-04-15
> **LaRoza said:**
> Torret is done for me. I am a "seeder" now.

Burning...

Ok, I am back (I left for the store a while ago)

Hopefully we can get some more seeders, I have had to limit the upload speed because it was using all the bandwidth, sorry whoever is leeching.

---

### Post by Rui Pais on 2008-04-16
> **Freddy said:**
> You might have to update OzOS download page Rui, your signature link points to a page with no downloads and the download tab points to a page with no downloads for the 32bit version :).

Btw, great version :).

Thanks Freddy for point it out. I edit temporarily my signature. 

We'll need to edit the OzOS main and download's page. 
RAV TUX it's the one that usually do this, but as he's out of town atm...


Thanks for your kind words on this new version of OzOS :D

---

### Post by Rui Pais on 2008-04-16
> **LaRoza said:**
> Ok, I am back (I left for the store a while ago)

Hopefully we can get some more seeders, I have had to limit the upload speed because it was using all the bandwidth, sorry whoever is leeching.

No problem with the the brandwidth limit :)
I still see more seeders than leechers (:() logged on my torrent client...

---

### Post by Rui Pais on 2008-04-16
Hi all.

[color=blue]**> UPDATE <**[/color] **[color=orange]**IMPORTANT**[/color]**
I updated the repos ( 16/Apr/2008 ).

On 0.5 you must do:```

sudo apt-get update
sudo aptitude dist-upgrade
```
If it asks to replace /etc/lsb-release _you must accept_ the default option, keep original file (thats an update for Hardy-Development).

This updates resolves some issues reported, and includes a new gdm theme, identical to default wallpaper, for consistency of look&feel.
You can change it by run:
```
sudo gdmsetup
```
and on local pick the one you want to use or set choice too random :)

**[color=blue]> KNOWN ISSUES <[/color]**
_There's a bug with gtk theme switcher launcher on menu._
To workaround users must enter (no sudo) on terminal:
```
sed -i 's/gtk-theme-switcher2/\gtk-theme-switch2/' ~/.local/share/applications/gtk-theme-switcher.desktop
```
(updates include this for all new users you make on your system)

---

### Post by vishzilla on 2008-04-16
I was looking forward for this. The torrent needs more seeders, very slow

---

### Post by Rui Pais on 2008-04-17
> **vishzilla said:**
> I was looking forward for this. The torrent needs more seeders, very slow

Thanks for your interest in OzOS vishzilla!!

Yes, you're right. I have listed 4 seeders and 2 peers only ... 
but today downloads are a bit slower than usual, at most half of it use to be (me wonders...).

---

### Post by Rui Pais on 2008-04-17
Hi. 
(Sorry this double post.)

I'm not sure if there was some problems with torrent file... it has been unexpectantly slow (special if there are more than 1 peers) 
I made a new one, already update to [Download links](http://www.cafelinux.org/Downloads/oz-os/iso/)
Hope now it goes better.

Seeders should stop/remove the old seed, download the new torrent:
[http://www.cafelinux.org/Downloads/oz-os/iso/oz-os-0.5-livecd-i386.iso.torrent](http://www.cafelinux.org/Downloads/oz-os/iso/oz-os-0.5-livecd-i386.iso.torrent)
and choose as download place on torrent client the already downloaded iso.

Sorry about the inconvenience :( 

I upload it too to LinuxTracker: 
[Click here for it's page](http://linuxtracker.org/index.php?page=torrent-details&id=58748fc4a52eaf895d5bada81a76fc8a2a1553cc)

hope that helps to spread the word about OzOS and gives us more seeders and faster downloads!  

Thank you All,
Rui

---

### Post by smartboyathome on 2008-04-17
I can't download it now. I am using Transmission, and it says "unregistered torrent pass". :(

---

### Post by dmiller40 on 2008-04-17
Hey Rui Pais,

I appreciate your help in the gOS link, lol. Well i finally got Oz installed and it looks great! I was wondering what network manager it uses. I read somewhere that it used Wicd? If thats the case Wicd isnt installed on my system but i do see network-manager from gnome i guess. 

I liked in xfce that there was a nm-applet in my panel so i could monitor it. Is there anything like that for enlightenment? Also would like to change the battery image, and my Volume Monitor doesn't seem to be installed.

thanks again
dm

---

### Post by Rui Pais on 2008-04-17
> **smartboyathome said:**
> I can't download it now. I am using Transmission, and it says "unregistered torrent pass". :(

hi smartboyathome.
Thats strange... do you mean the torrent file from my above post or the old ones on Downloads cafelinux site?

---

### Post by smartboyathome on 2008-04-17
> **Rui Pais said:**
> hi smartboyathome.
Thats strange... do you mean the torrent file from my above post or the old ones on Downloads cafelinux site?

I mean the new one (which is on the download page an d here). I will try Deluge to see if I can get it downloading.

EDIT: Deluge doesn't connect. I am afraid I won't be able to download the torrent right now. :(

---

### Post by Rui Pais on 2008-04-17
> **dmiller40 said:**
> Hey Rui Pais,

I appreciate your help in the gOS link, lol. Well i finally got Oz installed and it looks great! I was wondering what network manager it uses. I read somewhere that it used Wicd? If thats the case Wicd isnt installed on my system but i do see network-manager from gnome i guess. 

I liked in xfce that there was a nm-applet in my panel so i could monitor it. Is there anything like that for enlightenment? Also would like to change the battery image, and my Volume Monitor doesn't seem to be installed.

thanks again
dm

Welcome to OzOS dmiller40 :).
The network manager (for wireless) it's wicd.
It's installed but not enabled by default.
To use it do on a terminal:
```
sudo sysv-rc-conf
```
use the arrow keys to go to wicd line and press space on columns 2, 3, 4, 5.
Finally start it:
```
sudo /etc/init.d/wicd start
```

Change image of an e17 module require the recompilation of the theme. Check here:
[http://cafelinux.org/forum/index.php/topic,885.0.html](http://cafelinux.org/forum/index.php/topic,885.0.html)
if you want to do it (most people prefer change theme for something they like more). 

About Volume Monitor, i presume you mean gnome-volume-manager. We tried to reduce gnome apps to a minimum, so it's not included by default.
You can install it with apt, synaptic or simply by pass apt:gnome-volume-manager at your browser address bar.

Post if you have doubts?

---

### Post by Rui Pais on 2008-04-17
> **smartboyathome said:**
> I mean the new one (which is on the download page an d here). I will try Deluge to see if I can get it downloading.

EDIT: Deluge doesn't connect. I am afraid I won't be able to download the torrent right now. :(

Sorry to hear about it :(

Are you sure you have your torrent port open?

I have right now 9 peers listed, uTorrent, ktorrent, BitTorrent listed... shouldn't be a problem neither with torrent file or the torrent client used.

If you want you can try the old torrent file:
[http://www.cafelinux.org/Downloads/oz-os/old/oz-os-0.5-livecd-i386.iso.torrent](http://www.cafelinux.org/Downloads/oz-os/old/oz-os-0.5-livecd-i386.iso.torrent)
Or download iso directly...

---

### Post by dmiller40 on 2008-04-17
Ok it does not seem Wicd is installed. What is used for wired network? I need to switch between static ip and dhcp, depending on my location (work/home).

Also the number lock is on when i login how can i turn this off?

thanks
dm

---

### Post by LaRoza on 2008-04-17
Rats. Failed to install. 

Most likely not enough RAM (192 MB) would 256 be enough?

---

### Post by dmiller40 on 2008-04-17
I got Wicd installed, but it runs super slow. Is there something wrong with it or should i use something else. I used Exalt w/ gOS, would that be better?

dm

---

### Post by Rui Pais on 2008-04-17
> **dmiller40 said:**
> Ok it does not seem Wicd is installed. What is used for wired network? I need to switch between static ip and dhcp, depending on my location (work/home).

Also the number lock is on when i login how can i turn this off?

thanks
dm

Oops sorry, i forget you installed manually...

do a: 
sudo apt-get install wicd
it should install and you get all activated... you got a entry on menu:
Applications > Internet > Wicd

About the numlockX, i think it came on by default on Hardy. 
The only way i know to disable it it's by running: 
```
numlockx off
```
(you can make a launch for it and enable it at Startup Applications)

hth


***EDIT***
Only now i see your most recent post ...
I tried exalt and it was buggy as hell. I give up of it. Wicd it's a favorite around. 
(I don't use cause i have a alway on connection and no Wifi...) Most people seems very pleased with it.

A velocity issue look more a net configuration issue than wicd trouble.
Have you tried to unload ipv6? and stop ahavi-daemon?

---

### Post by Rui Pais on 2008-04-17
> **LaRoza said:**
> Rats. Failed to install. 

Most likely not enough RAM (192 MB) would 256 be enough?

Uhmm. Thats strange... unless Ubuntu base it's now much more heavy... that i don't think it's the case.

Where did it fail when install? Did Ubiquity even start the install process, or aborted on initial user interaction steps?
Do you have mixed harddrives (sata+pata) or some driver with anormal settings (ext2, ext4,inotes tweaking...)?
It's the CD burned on high speed (>24x)?

Don't know much other possible causes :( (maybe check too ubiquity bugs on hardy...)

Sorry to know that you hit problems :(

---

### Post by LaRoza on 2008-04-17
> **Rui Pais said:**
> Uhmm. Thats strange... unless Ubuntu base it's now much more heavy... that i don't think it's the case.

Where did it fail when install? Did Ubiquity even start the install process, or aborted on initial user interaction steps?
Do you have mixed harddrives (sata+pata) or some driver with anormal settings (ext2, ext4,inotes tweaking...)?
It's the CD burned on high speed (>24x)?

Don't know much other possible causes :( (maybe check too ubiquity bugs on hardy...)

Sorry to know that you hit problems :(

It may be an X problem. I am also on a KVM and sometimes that throws installers off when the screen is being used by the other computer.

I will likely succed later. Right now, I am waiting for the RAM and nic.

---

### Post by Rui Pais on 2008-04-17
> **LaRoza said:**
> It may be an X problem. I am also on a KVM and sometimes that throws installers off when the screen is being used by the other computer.

I will likely succed later. Right now, I am waiting for the RAM and nic.

Ahh good to know.
I'm always a little fear that using a pre-release base would explode suddenly in a myriad of issues :-# (better keep mouth closed).

---

### Post by aircooledbusnut on 2008-04-17
i installed oz on my Acer 5520 laptop,  I love it.  couple of issues though.  Can not access the repositories through synaptic, it does not open when selected.  Tried to install skype but enlightenment will not launch.  But everything (all Hardware) works perfectly).  Thanks for providing this wonderful os.

---

### Post by justin whitaker on 2008-04-17
> **aircooledbusnut said:**
> i installed oz on my Acer 5520 laptop,  I love it.  couple of issues though.  Can not access the repositories through synaptic, it does not open when selected.  Tried to install skype but enlightenment will not launch.  But everything (all Hardware) works perfectly).  Thanks for providing this wonderful os.

Hmm...there is probably a dependency that is missing. Use aptitude or apt-get to update the system, then try again.

---

### Post by aircooledbusnut on 2008-04-17
I ran both apt-get update/apt-get upgrade and aptitude update/aptitude upgrade, as well as apt-get install --reinstall synaptic.  still have same problem i hit the settings tab then repositories and only get the spinning icon for a few seconds but no window to make changes.

Thanks

---

### Post by aircooledbusnut on 2008-04-17
Synaptic repository issue solved.  I removed using apt-get then cleaned and reinstalled.  the window has a different appearance than ubuntu but it works well.

Thanks for the ideas.

---

### Post by Freddy on 2008-04-18
> **aircooledbusnut said:**
> Synaptic repository issue solved.  I removed using apt-get then cleaned and reinstalled.  the window has a different appearance than ubuntu but it works well.

Thanks for the ideas.
For questions and help about OzOS, it's better to make a visit to [CafeLinux]("http://cafelinux.org/forum/") which is the forum OzOS uses.

---

### Post by Rui Pais on 2008-04-19
> **aircooledbusnut said:**
> I ran both apt-get update/apt-get upgrade and aptitude update/aptitude upgrade, as well as apt-get install --reinstall synaptic.  still have same problem i hit the settings tab then repositories and only get the spinning icon for a few seconds but no window to make changes.

Thanks

> **aircooledbusnut said:**
> Synaptic repository issue solved.  I removed using apt-get then cleaned and reinstalled.  the window has a different appearance than ubuntu but it works well.

Thanks for the ideas.

Hi, glad to hear that you solved that problem. :)


Thats a known issue with the OzOS liveCD RC1.2 (64bits) and Synaptic.
Gutsy version of Synaptic seems that can't open the Repositories settings window on too changed Ubuntu variations. :(
Users od OzOS RC1.2 must edit sources.list directly with a text editor.

This is solved on next release. 
Rui

---

### Post by Rui Pais on 2008-04-19
> **Freddy said:**
> For questions and help about OzOS, it's better to make a visit to [CafeLinux]("http://cafelinux.org/forum/") which is the forum OzOS uses.

Yes. :) Cafelinux houses OzOS (and other Linux projects)
Everybody it's welcome!

Just a note to let anyone knows that after a bad day yesterday, Cafelinux it's up and running again.:D

Questions about OzOS can be asked there or here on this threads about OzOS.


@Freddy.
Nice sig :) 
Thanks for help spreading the word about Enlightenment and OzOS. 
And thank you for your kind words!
Rui

---

### Post by chris4585 on 2008-04-19
i have to say that OzOS is one of the sexiest distro's i've tried ;)

---

### Post by Rui Pais on 2008-04-20
> **chris4585 said:**
> i have to say that OzOS is one of the sexiest distro's i've tried ;)

:)
Thanks for your comment!

Yes enlightenment can be very sexy... and we tried to tune it to be as elegant as possible!

Glad you liked :D

---

### Post by dmiller40 on 2008-04-22
I'm having a problem connecting to my wireless network with Wicd. I have a WPA/PSK encription and just can get it to connect. I've check marked encryption and using the WPA 1/2, but still no go.

thanks
dm

---

### Post by Rui Pais on 2008-04-23
> **dmiller40 said:**
> I'm having a problem connecting to my wireless network with Wicd. I have a WPA/PSK encription and just can get it to connect. I've check marked encryption and using the WPA 1/2, but still no go.

thanks
dm

Sorry to hear you got problems with Wireless.

I'm of no much help on this one. Have you tried to search forum for 'WPA/PSK encryption with WICD'? The [network&Wireless forum]("http://ubuntuforums.org/forumdisplay.php?f=336") may have too some answers.

Check WICD site, too, to see if you find something.

Good luck.

---

### Post by dmiller40 on 2008-04-23
I did get it working last night, with the help of my friend google. I went into preferences and changed the driver to wext. I was using broadcom or madwifi.

thanks
dm

---

### Post by Rui Pais on 2008-04-23
> **dmiller40 said:**
> I did get it working last night, with the help of my friend google. I went into preferences and changed the driver to wext. I was using broadcom or madwifi.

thanks
dm

Excellent! Good to know that its working.

I'll keep this post of your in mind for the case of identical issue being reported by other users.

Many thanks for sharing. 
:)

---

### Post by dmiller40 on 2008-05-05
I just discovered Cairo-Dock and was wondering if it would work in enlightenment-OzOs desktop? Also if it was resource heavy?

thanks
dm

---

### Post by Rui Pais on 2008-05-05
> **dmiller40 said:**
> I just discovered Cairo-Dock and was wondering if it would work in enlightenment-OzOs desktop? Also if it was resource heavy?

thanks
dm

like this?
[ATTACH]68903[/ATTACH]
but,
[ATTACH]68904[/ATTACH]
the problem it's that animations leave some parts of the screen black due to the way that e17 draws the background... 
It's the that way to any eye-candy from outside e17. Transparency never work quite well.

But you can get some of the effects with ibar... 

Thanks for the suggestion anyway dmiller40, maybe users with a dark/black wallpaper may find it useful.
:)

---

### Post by smartboyathome on 2008-05-07
You can use Ecomorph if you can get it to compile. It will provide compositing via compiz for e17. It isn't stable yet, though. :(

---

### Post by Tikkun olam on 2008-06-24
I found an extensive list [here]("http://en.wikipedia.org/wiki/List_of_Ubuntu-based_distributions") and another one [here.]("https://wiki.ubuntu.com/DerivativeTeam/Derivatives")

I am experimenting and I wanted to try something that is a bit different then the official releases and perhaps one that uses something a bit different then GNOME, KDE or XFCE.

Perhaps something with Fluxbox, e17 or something else?

I'm open for suggestions and am interested in something that others may have tried. The two list of Ubuntu derivatives is extensive so I was looking to trim some choices down.

---

### Post by FFighter on 2008-06-24
Well, Linux Mint uses Gnome as DE, but is, from what I could see, implemented in a significantly different way, focusing more on usability and "out-of-the-boxness".

There's also Fluxbuntu, which is a distribution based on Ubuntu, but cut in a half (lighter, less software installed by default) and with Fluxbox as default DE.

---

### Post by madjr on 2008-06-24
openGEU

gOS e17 edition

---

### Post by Tikkun olam on 2008-06-24
> **FFighter said:**
> Well, Linux Mint uses Gnome as DE, but is, from what I could see, implemented in a significantly different way, focusing more on usability and "out-of-the-boxness".

There's also Fluxbuntu, which is a distribution based on Ubuntu, but cut in a half (lighter, less software installed by default) and with Fluxbox as default DE.While Linux Mint does look interesting I am looking for something other then Gnome/KDE/XFCE.

Fluxbuntu does look interesting I will give it a try, they appear to have a nice forum for support also.

> **madjr said:**
> openGEU

gOS e17 editionNeither one of these appear to have very active forums for support. While e17 does look interesting I wonder if  there are any viable options that have good active forums for support?

Are then any other Ubuntu derivatives that utilize e17 or any other WM that come with a strong recommendation?

---

### Post by Rui Pais on 2008-06-24
> **Tikkun olam said:**
> While Linux Mint does look interesting I am looking for something other then Gnome/KDE/XFCE.

Fluxbuntu does look interesting I will give it a try, they appear to have a nice forum for support also.

Neither one of these appear to have very active forums for support. While e17 does look interesting I wonder if  there are any viable options that have good active forums for support?

Are then any other Ubuntu derivatives that utilize e17 or any other WM that come with a strong recommendation?

Yes :)

Read my sig. 1st link for OzOS, 32 and 64bits and distro, 2nd link for e17 implementation on almost any debian variation and 3rd link for support forum (and other bizarries ;)) 

hth

---

### Post by Tux Aubrey on 2008-06-24
Ok, Rui Pais types quicker than I do.  Big Deal!  Here's my reply anyway.

> **Tikkun olam said:**
> 

Neither one of these appear to have very active forums for support. While e17 does look interesting I wonder if  there are any viable options that have good active forums for support?

Are then any other Ubuntu derivatives that utilize e17 or any other WM that come with a strong recommendation?

Why not try [OzOS]("http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents")?  It is a cut-down Xubuntu with its own e17 desktop package (that can also be installed by itself alongside Ubuntu/Kubuntu/Xubuntu or any other Debian-based distro - [HowTo Here]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os")). The e17 package is kept up-to-date and does not include by default many of the Enlightenment apps that are just "not quite ready yet". 

OzOS also has a nice (and expanding) set of optional "-extras" that make maintenance much easier that most of the other e17 distros around. 

[The OzOS forums]("http://www.cafelinux.org/forum/") (at CafeLinux) are quite active and support is always forthcoming.

The whole thing is put together by current and former Ubuntu Forums members and staff (including me, but not as a dev).

That said, I have also found both [Maryan Linux]("http://maryanlinux.wordpress.com/") (page currently off line) and OpenGeu to be excellent implementations of e17 on Ubuntu.  I used to use eLive but it seems to have been in the doldrums a bit lately and its Enlightenment implementation seems very outdated compared to the Ubuntu-based ones.

Good Luck on your quest for Enlightenment.

---

### Post by Rui Pais on 2008-06-24
> **Tux Aubrey said:**
> Ok, Rui Pais types quicker than I do.  Big Deal!  Here's my reply anyway.


:shock:

it was first time i could type faster than you, Aubrey :lol:
(your fingers are tired from typing how-tos :))

anyway it was a much better and explained post :)

---

### Post by sujoy on 2008-06-24
you might also use the alternate disc to install a minimal system and build up on it along with any WM you want to try out.

---

### Post by acelin on 2008-06-24
Try out Nexenta - its a Ubuntu based distro that uses an Open Solaris kernel.

---

### Post by Tikkun olam on 2008-06-24
> **Rui Pais said:**
> Yes :)

Read my sig. 1st link for OzOS, 32 and 64bits and distro, 2nd link for e17 implementation on almost any debian variation and 3rd link for support forum (and other bizarries ;)) 

hth

OzOS looks pretty awesome! 

> **Tux Aubrey said:**
> Ok, Rui Pais types quicker than I do.  Big Deal!  Here's my reply anyway.



Why not try [OzOS]("http://cafelinux.org/OzOs/content/ozos-iso-downloads-torrents")?  It is a cut-down Xubuntu with its own e17 desktop package (that can also be installed by itself alongside Ubuntu/Kubuntu/Xubuntu or any other Debian-based distro - [HowTo Here]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os")). The e17 package is kept up-to-date and does not include by default many of the Enlightenment apps that are just "not quite ready yet". 

OzOS also has a nice (and expanding) set of optional "-extras" that make maintenance much easier that most of the other e17 distros around. 

[The OzOS forums]("http://www.cafelinux.org/forum/") (at CafeLinux) are quite active and support is always forthcoming.

The whole thing is put together by current and former Ubuntu Forums members and staff (including me, but not as a dev).

Good Luck on your quest for Enlightenment.Aubrey, Thanks also for your post and suggestion OzOS looks very professional and the forums for support are active and professional.

I am downloading OzOS now and very excited to install and use it.

---

### Post by zmjjmz on 2008-06-24
<spam>
You could try Icebuntu
</spam>

---

### Post by Tikkun olam on 2008-06-25
> **zmjjmz said:**
> <spam>
You could try Icebuntu
</spam>

Icebuntu also looks interesting, but unfortunately the forums don't seem to be very active for Icebuntu.

Here are the 2 Ubuntu derivatives I am going to try:

1. [OzOS]("http://cafelinux.org/OzOs/")
2. [Fluxbuntu]("http://fluxbuntu.org/js.html")

These look to be the two most promising Ubuntu derivatives that use something other then Gnome/KDE/XFCE.

---

### Post by Tikkun olam on 2008-06-26
> **acelin said:**
> Try out Nexenta - its a Ubuntu based distro that uses an Open Solaris kernel.
I'm not so interested in a different kernel as I am in a different WM/DE, something other then the usual Gnome/KDE/XFCE.

After downloading, installing and evaluating Fluxbuntu and OzOS, I have found them both to be very nice. OzOS I find more of my cup of tea for a daily use. The OzOS Devs have done a wonderful job of making a very nice Xubuntu Derivative that can be used on a daily basis as a primary OS.

I highly recommend OzOS for those who crave "A Reality Different" (As they say on the OzOS website)

---

### Post by billgoldberg on 2008-06-26
Tried them all, and found gnome to be the best.

---

### Post by Tikkun olam on 2008-06-26
> **billgoldberg said:**
> Tried them all, and found gnome to be the best.Gnome is indeed good. This being a Gnome-centric forum the base of us as Gnome users is a given. Sometimes I crave something different, I like the idea of using an OzOS base and installing Gnome or KDE applications on the E17 base. 

It would be nice if this came in a nifty package for OzOS.

---

### Post by K.Mandla on 2008-06-26
Moved to Other OS Talk.

---

### Post by Rui Pais on 2008-06-26
> **Tikkun olam said:**
> I'm not so interested in a different kernel as I am in a different WM/DE, something other then the usual Gnome/KDE/XFCE.

After downloading, installing and evaluating Fluxbuntu and OzOS, I have found them both to be very nice. OzOS I find more of my cup of tea for a daily use. The OzOS Devs have done a wonderful job of making a very nice Xubuntu Derivative that can be used on a daily basis as a primary OS.

I highly recommend OzOS for those who crave "A Reality Different" (As they say on the OzOS website)

:)
Thank you for your kind words on OzOS!
Much appreciated!!. 
It's always good to hear about users satisfaction :D




> **Tikkun olam said:**
> Gnome is indeed good. This being a Gnome-centric forum the base of us as Gnome users is a given. Sometimes I crave something different, I like the idea of using an OzOS base and installing Gnome or KDE applications on the E17 base. 

It would be nice if this came in a nifty package for OzOS.

In fact there is :)

It's called oz-gnome-desktop and it's available from OzOS repos :)

Can be installed directly on OzOS or on any Ubuntu or Debian (tested on Lenn,y should work on stable too) by simply add OzOS repos to sources.list.

It can be done on a usual installation or on an installation from The MinimalCD or from alternate CD.

It was made to have a full Gnome, Ubuntu like, desktop, but lighter and more flexible.
It won't impose less popular apps (see, as an example, The most useless things on Ubuntu thread) like Evolution, F-spot, Tomboy, Ekiga, Compiz, etc.
User decide can install any one of them or any alternative at they will.

That's how i think things should work. 
Impose little as default and leave the rest on users choice. 
:)

---

### Post by shebuwa on 2008-06-26
OzOS is just what I have been looking for! I am downloading it now, on another machine, and I intend to install it later today on this one.

Thank you, Rui Pais, for creating such a perfect Ubuntu variant.

gasho

Lynn

---

### Post by zmjjmz on 2008-06-26
PUD with LXDE is another thing to try.

---

### Post by Tikkun olam on 2008-06-27
> **Rui Pais said:**
> :)
Thank you for your kind words on OzOS!
Much appreciated!!. 
It's always good to hear about users satisfaction :D

Good Welcome, I have found OzOS to be the best little known OS to date.

I appreciate all your hard work and effort.




> **Rui Pais said:**
> 

In fact there is :)

It's called oz-gnome-desktop and it's available from OzOS repos :)

Can be installed directly on OzOS or on any Ubuntu or Debian (tested on Lenn,y should work on stable too) by simply add OzOS repos to sources.list.

It can be done on a usual installation or on an installation from The MinimalCD or from alternate CD.

It was made to have a full Gnome, Ubuntu like, desktop, but lighter and more flexible.
It won't impose less popular apps (see, as an example, The most useless things on Ubuntu thread) like Evolution, F-spot, Tomboy, Ekiga, Compiz, etc.
User decide can install any one of them or any alternative at they will.

That's how i think things should work. 
Impose little as default and leave the rest on users choice. 
:)

This is awesome Rui!

Who would of thought that the best Gnome OS would be a e17 based Xubuntu derivative.
 
OzOS is refined poetry in motion.

> **shebuwa said:**
> OzOS is just what I have been looking for! I am downloading it now, on another machine, and I intend to install it later today on this one.

Thank you, Rui Pais, for creating such a perfect Ubuntu variant.

gasho

LynnDitto!

---

### Post by shebuwa on 2008-06-27
OzOs really is darn cool. I found it a little too spartan for my needs though, and so I am trying to flesh out Xubuntu right now. I may come back to Oz later though. We'll see how it goes with Xubu first.

---

### Post by Rui Pais on 2008-07-02
Hi all,
a new OzOS it's available!

This is a major update for the 64bits version of OzOS, build with latest e17 from CVS and based on Gutsy.
It corrects several bugs and incorrect identification, adds extra functionality and all recent updates for Gutsy repositories.

It's main focus is stability (base code more tested) and will be acting as a final test for the upcoming 1.0, hardy based.  

**Torrents (preferred):**
[http://cafelinux.org/Downloads/oz-os/iso/ozos-0.8-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/ozos-0.8-livecd-amd64.iso.torrent)

Downloads:
[http://cafelinux.org/Downloads/oz-os/iso](http://cafelinux.org/Downloads/oz-os/iso)


[color=blue]**NEWS & FEATURES:**[/color]
- Minor bugs solved (like incorrect menu entry for gtk-theme-switch, no restarts for stalonetray, etc...)
- Correct identification of OS did not make synaptic change of repos (software-properties-gtk) fail anymore.
- Signed authenticated repos.
- Default gdm theme more consistent.
- Cleaner e17 and oz-desktop dependencies (debian/lenny compatible by now)
- oz-e17-tools and Aubrey's 6dozd by default with menu entries.
- New tool/entry on System tools named 'Graphics Driver Installation' that launch Envy or install it if not present 
   (users don't need to know what envy is :))
- Wicd supported same way, only install on user request, and descriptively named 'Wireless Wicd start'.
- Firefox installed, but no longer a dependency of desktop (user may want to delete/replace by any other browser)
- Swiftweasel repos automatically available for the case (see below comment)
- Thunar with gutsy abilities of auto-mounting partitions and a "unique" search function implemented (by catfish)
- Transmission and gajim on Favorites menus (they should run 1/section so not on ibar where they would be useless most of time)
- LiveCD translations and help files get reference for OzOS not Ubuntu.
- Better branding from Ubuntu->OzOS on system

**Some version numbers:**
Kernel: 2.6.22-15
e17:    0.16.999.043
gcc:    4.2.3 
Firefox: 2.0.0.14

Users that want FF3 may install it directly from Mozilla site, by add (through synaptic) extra repos from Ubuntu or, *recommended*, opt by Swiftweasel.
Swiftweasel it's a CPU optimized Firefox build, available from repos. It has 64bits for several CPUs and even a 32bits one, swiftweasel32, made specially for use in  64bits arch and available for several CPUs too.

Hope you all like it! 

Rui

---

### Post by Rui Pais on 2008-07-02
New OzOS 64bits version 0.8 (Gutsy based) it's available.
Thread here: 
[http://ubuntuforums.org/showthread.php?t=847082](http://ubuntuforums.org/showthread.php?t=847082)

Hope you like it

---

### Post by Rui Pais on 2008-07-02
> **Tikkun olam said:**
> 

This is awesome Rui!

Who would of thought that the best Gnome OS would be a e17 based Xubuntu derivative.
 
OzOS is refined poetry in motion.

Ditto!

:)
I loved your new *motto*!!
"OzOS is refined poetry in motion."

Thank you again for your kind word :)



> **shebuwa said:**
> OzOs really is darn cool. I found it a little too spartan for my needs though, and so I am trying to flesh out Xubuntu right now. I may come back to Oz later though. We'll see how it goes with Xubu first.

shebuwa, you can always what software/applications on what ever versions/derivatives you have. 
No need for a full reinstall!
Use synaptic (and/or apt:foo page) or from command line:
```
sudo aptitude install xubuntu-desktop
```
to install xubuntu on OzOS
or (after add Oz repos):
```
sudo aptitude install oz-desktop 
```
to install OzOS on Xubuntu

Same for any other Desktop Environment (Gnome/Kde/Fluxbox/etc.)
:)

---

### Post by Tikkun olam on 2008-07-02
> **Rui Pais said:**
> Hi all,
a new OzOS it's available!

This is a major update for the 64bits version of OzOS, build with latest e17 from CVS and based on Gutsy.
It corrects several bugs and incorrect identification, adds extra functionality and all recent updates for Gutsy repositories.

It's main focus is stability (base code more tested) and will be acting as a final test for the upcoming 1.0, hardy based.  

**Torrents (preferred):**
[http://cafelinux.org/Downloads/oz-os/iso/ozos-0.8-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/ozos-0.8-livecd-amd64.iso.torrent)

Downloads:
[http://cafelinux.org/Downloads/oz-os/iso](http://cafelinux.org/Downloads/oz-os/iso)


[COLOR=blue]**NEWS & FEATURES:**[/COLOR]
- Minor bugs solved (like incorrect menu entry for gtk-theme-switch, no restarts for stalonetray, etc...)
- Correct identification of OS did not make synaptic change of repos (software-properties-gtk) fail anymore.
- Signed authenticated repos.
- Default gdm theme more consistent.
- Cleaner e17 and oz-desktop dependencies (debian/lenny compatible by now)
- oz-e17-tools and Aubrey's 6dozd by default with menu entries.
- New tool/entry on System tools named 'Graphics Driver Installation' that launch Envy or install it if not present 
   (users don't need to know what envy is :))
- Wicd supported same way, only install on user request, and descriptively named 'Wireless Wicd start'.
- Firefox installed, but no longer a dependency of desktop (user may want to delete/replace by any other browser)
- Swiftweasel repos automatically available for the case (see below comment)
- Thunar with gutsy abilities of auto-mounting partitions and a "unique" search function implemented (by catfish)
- Transmission and gajim on Favorites menus (they should run 1/section so not on ibar where they would be useless most of time)
- LiveCD translations and help files get reference for OzOS not Ubuntu.
- Better branding from Ubuntu->OzOS on system

**Some version numbers:**
Kernel: 2.6.22-15
e17:    0.16.999.043
gcc:    4.2.3 
Firefox: 2.0.0.14

Users that want FF3 may install it directly from Mozilla site, by add (through synaptic) extra repos from Ubuntu or, *recommended*, opt by Swiftweasel.
Swiftweasel it's a CPU optimized Firefox build, available from repos. It has 64bits for several CPUs and even a 32bits one, swiftweasel32, made specially for use in  64bits arch and available for several CPUs too.

Hope you all like it! 

Rui

Awesome news Rui! Thanks for the announcement.

---

### Post by K.Mandla on 2008-07-02
Multiple similar threads merged.

---

### Post by Freddy on 2008-07-02
I love this new release Rui everything is running smoothly, keep up the good work and good luck with the transition to a Hardy based OzOS.

---

### Post by Rui Pais on 2008-07-03
> **Freddy said:**
> I love this new release Rui everything is running smoothly, keep up the good work and good luck with the transition to a Hardy based OzOS.

Thank you Freddy! 
You are very kind. :)




> **K.Mandla said:**
> Multiple similar threads merged.
Hi K.Mandla.
I created new threads as new releases come up, because i though it was normal procedure (and make things simpler to read). 
No problem with a single thread.

But, with all respect, the gOS forum thread has nothing to do with this subject, and, beside lost in the middle of this, looks quite weird some talk about a forum support of a distro on the middle of talk about another distro. 

I don't care much about gOS, but it's a very known one and the subject may interest several users of this forum.
Tanks,
Rui

---

### Post by LaRoza on 2008-07-03
> **Rui Pais said:**
> 
Hi K.Mandla.
I created new threads as new releases come up, because i though it was normal procedure (and make things simpler to read). 

It is alright to have multiple threads, but I noticed the threads have a tendency to live for a while, which seems to result in more than one active thread on the subject.

> 
But, with all respect, the gOS forum thread has nothing to do with this subject, and, beside lost in the middle of this, looks quite weird some talk about a forum support of a distro on the middle of talk about another distro. 

I don't care much about gOS, but it's a very known one and the subject may interest several users of this forum.


I see that discussion as rather odd, as I see that Cafelinux.org's offical forum has that listed already. I will remove those posts so the discussion is more continous (and because it wasn't your thread)

---

### Post by Rui Pais on 2008-07-03
> **LaRoza said:**
> It is alright to have multiple threads, but I noticed the threads have a tendency to live for a while, which seems to result in more than one active thread on the subject.

Ah, I see. Ok. 
Thank you for the explanation.


> **LaRoza said:**
> 
I see that discussion as rather odd, as I see that Cafelinux.org's offical forum has that listed already. I will remove those posts so the discussion is more continous (and because it wasn't your thread)

Yes, the official forum has that announcement (waiting for the situation to solve). I just answered on the thread that appear here to clarify the situation for Ubuntu users that use gOS or have interest on the subject. 
Of course that had nothing to do with this topic.

Thanks, LaRoza, for move them away.

---

### Post by LaRoza on 2008-07-03
> **Rui Pais said:**
> Ah, I see. Ok. 
Thank you for the explanation.


Will there be a Hardy based OzOS soon? I will be trying out this latest one on my laptop as soon as I can.

---

### Post by Rui Pais on 2008-07-04
> **LaRoza said:**
> Will there be a Hardy based OzOS soon? I will be trying out this latest one on my laptop as soon as I can.

Yes, we are planning on it :)
Just waiting that hardy updates came in a slow rate, tunning a little more oz-desktop (e17-cvs had going for a cleaning phase recently) and finish the themes and artwork.

Thanks for your interest, LaRoza. As usual i'll post here when it's up.

---

### Post by LaRoza on 2008-07-04
> **Rui Pais said:**
> Yes, we are planning on it :)
Just waiting that hardy updates came in a slow rate, tunning a little more oz-desktop (e17-cvs had going for a cleaning phase recently) and finish the themes and artwork.

Thanks for your interest, LaRoza. As usual i'll post here when it's up.
Nice to hear (I only care because I like to use the same versions from the repos, but it Gutsy was a solid release for me)

I wasn't able to get it last night (no seeders :() but I will try again.

---

### Post by Rui Pais on 2008-07-04
> **LaRoza said:**
> Nice to hear (I only care because I like to use the same versions from the repos, but it Gutsy was a solid release for me)

Yes, Gutsy was a little problematic at beginning, but after a month or so it get very nice.
With Hardy has been same thing... several problems, but keep going better.

I wished that Ubuntu stop release on such defined dates/period and could give a month or two for better tunning and issue solving :(  


> **LaRoza said:**
> 
I wasn't able to get it last night (no seeders :() but I will try again.
:( sorry to hear it. You know, very small distro and 64bits version...
I'm moving things to my laptop, when i finish i can keep it seed at night, but meanwhile my main computer it's too noise and make to hot for summer nights...

---

### Post by LaRoza on 2008-07-04
> **Rui Pais said:**
> 
I wished that Ubuntu stop release on such defined dates/period and could give a month or two for better tunning and issue solving :(  

Well, Ubuntu has a new ISO out which has all the updates, that should be good.

> 
:( sorry to hear it. You know, very small distro and 64bits version...
I'm moving things to my laptop, when i finish i can keep it seed at night, but meanwhile my main computer it's too noise and make to hot for summer nights...
I'll get it soon. I wouldn't have been able to install it anyway (I am going to redo the laptop later)

---

### Post by Rui Pais on 2008-07-04
> **LaRoza said:**
> Well, Ubuntu has a new ISO out which has all the updates, that should be good.


Great! 
I knew that base-files was updated to 8.04.1, but had no idea that Ubuntu released a new iso, so soon. Good, very need it! 
I will give it a try and work base on it. Thanks LaRoza!


> **LaRoza said:**
> 
I'll get it soon. I wouldn't have been able to install it anyway (I am going to redo the laptop later)
Ok. Let me know what you think or if you get problems. 

**Knowing issues, so far:**
-To use/run Gadget modules an apt-get update and an update of e17 it's needed first (or e starts to segfaults furiously)

---

### Post by LaRoza on 2008-07-04
> **Rui Pais said:**
> Great! 
I knew that base-files was updated to 8.04.1, but had no idea that Ubuntu released a new iso, so soon. Good, very need it! 
I will give it a try and work base on it. Thanks LaRoza!


Yep, they new ISO's are up (I just got them for my own use).

It isn't obvious from the download page, but the iso's are named as such.

I am myself not particularly fond of Enlightenment, but I like to have my laptop capable of showing off to potential new users (me using my setup is unimpressive and too geeky, I need to have things that are capable of wowing people)

---

### Post by mips on 2008-07-05
Rui,

Went to have a look at the screenshots and I must say it looks really sweet!

I might try it in a VM at some later stage as I love Arch too much to replace it.

---

### Post by Rui Pais on 2008-07-05
> **LaRoza said:**
> 
I am myself not particularly fond of Enlightenment, but I like to have my laptop capable of showing off to potential new users (me using my setup is unimpressive and too geeky, I need to have things that are capable of wowing people)

:) Thats the beauty of Linux, So many DE/WM to pick. It's sp nice wandering around till find one that serve our purposes.

I think i remember some pics of your desktop, wmii, if i remember well... must look very frightneing when showing to new users :lol:

If you prefer you can just install e17-cvs and themes without going for the all OS, maybe even lighter then set a VM for the all OzOS, if it's just for demonstrative purposes.
 

> **mips said:**
> Rui,

Went to have a look at the screenshots and I must say it looks really sweet!

I might try it in a VM at some later stage as I love Arch too much to replace it.

Great, mips. Thanks for your interest on it!

If you want you can install on ARCH only e17 from cvs running morlenxus scripts and apply themes at your will...
OzOS and some few others from users, are available directly from Cafelinux page:
[http://cafelinux.org/OzOs/content/enlightenment-themes-ozos](http://cafelinux.org/OzOs/content/enlightenment-themes-ozos)
and thread for themes ideas:
[http://cafelinux.org/forum/index.php?topic=1644](http://cafelinux.org/forum/index.php?topic=1644)

Let me know your toughs about it, if you decided to get a try on OzOS.
:)

---

### Post by LaRoza on 2008-07-05
> **Rui Pais said:**
> 
I think i remember some pics of your desktop, wmii, if i remember well... must look very frightneing when showing to new users :lol:

Yeah, it is either wmii, ratpoison, or a plain terminal. My use of terminals apps (irssi, finch, mc, vim, etc), and I use the DOS theme for Opera (plain black, with ascii) and my desktop is beauty, when I am the beholder.

> 
If you prefer you can just install e17-cvs and themes without going for the all OS, maybe even lighter then set a VM for the all OzOS, if it's just for demonstrative purposes.

I can use the Gutsy repos in OzOS right? I may just install wmii and my apps on OzOS. As I recall, OzOS is pretty light, at least when compared to Ubuntu, and if everything works, I may just use it.

---

### Post by Rui Pais on 2008-07-05
> **LaRoza said:**
> 
I can use the Gutsy repos in OzOS right? I may just install wmii and my apps on OzOS. As I recall, OzOS is pretty light, at least when compared to Ubuntu, and if everything works, I may just use it.
Yes, yes. OzOS repos are just extras added over Gutsy ones, all rest it's gutsy (on 0.8, hardy on 0.5).
 
The OS itself it's a Xubuntu, without XFCE4 and without some boot services.
Enlightenemnt takes around 65M of disc, all in a single folder on /opt/.

---

### Post by squidmaster on 2008-07-06
This gets a giant thumbs up for looking damn good.

downloading and installing it as soon as I return for japan.

---

### Post by squidmaster on 2008-07-06
so this OS look good
damn good.
can't wait to finish the download and give it a shot.

---

### Post by shuttleworthwannabe on 2008-07-06
So does OzOs come with bulletproofX; I have a ATI graphics video card that hates Linux installations---only Ubuntu picks it up and falls back on VESA drivers with the correct resolution 1920x1200 (2D only).

Tell me it will load to desktop without a glitch (no flares, intense lighting, and balck screen) on live cd bootup; then I will download.

The eye-candy really looks breath-taking.

Thanks
S

---

### Post by LaRoza on 2008-07-06
> **shuttleworthwannabe said:**
> 
Tell me it will load to desktop without a glitch (no flares, intense lighting, and balck screen) on live cd bootup; then I will download.


There is really no way to tell without trying it.

---

### Post by Rui Pais on 2008-07-06
> **squidmaster said:**
> so this OS look good
damn good.
can't wait to finish the download and give it a shot.

Great! Thanks for your interest on OzOS!

As usual comments, opinnions, suggestions are welcome :)


> **shuttleworthwannabe said:**
> So does OzOs come with bulletproofX; I have a ATI graphics video card that hates Linux installations---only Ubuntu picks it up and falls back on VESA drivers with the correct resolution 1920x1200 (2D only).

Tell me it will load to desktop without a glitch (no flares, intense lighting, and balck screen) on live cd bootup; then I will download.

The eye-candy really looks breath-taking.

Thanks
S

> **LaRoza said:**
> There is really no way to tell without trying it.


Yes, like LaRoza said, only trying can really answer that.
if you said it works with Ubuntu, i see no reason for not work with OzOS...

I personally find the original xorg version on gutsy very different than the latest on updates (on gutsy). 
My original gutsy had weird frozen on e17 (black top windows and no response to mouse clicks), after some updates it get better to me and the updated version was the one on OzOS. But some users reported the opposite, original gutsy work 100% and OzOS version give them incorrect resolutions. But this with nvidia cards and drivers.

---

### Post by shuttleworthwannabe on 2008-07-07
I have just downloaded Linux Mint (another Ubuntu variant)..and this sticks at the opening of the desktop...falls back to terminal login; startx gives a 'fatal error" in xserver. hence my concern. I will download and give some feedback though.
What Ubuntu (from hardy) does is that it uses bulletproofX to at least load the desktop environment..so at least the user can see what he is doing (albeit all in 2D). 3D rendering is just > sudo apt-get install xorg-driver-fglrx.

Note I have also tried: Fedora 9, OpenSuSe 11, and DreamLinux 3.1, and all of them do the same thing; fatal error on boot up. I am back to Ubuntu 8.04

Anyway, I divert. Good work with OzOs. I look forward to trying it.
S

---

### Post by squidmaster on 2008-07-08
in japan so the download is taking painfully long
about 12kb/s

---

### Post by Rui Pais on 2008-07-18
Sorry about this late answers.

> **squidmaster said:**
> in japan so the download is taking painfully long
about 12kb/s

:(

You know, less known distro... few seeders.
You can always download directly from Cafelinux server. 
We ask for torrents preferably, but it only really affects servers on release dates, when several direct downloads make server slow.
Now a couple of downloads at same time won't hurt much :)



@shuttleworthwannabe
Yes, OzOS implements xorg.conf via Ubuntu repos, so BulletproofX tool it's on.

---

### Post by john_spiral on 2008-08-16
Hi,

I've been running eLive GEM on an old beast of a machine for ages (2007/07). I fell in love with version 6 of the window manger with it's 3d twirling windows, MacOSX like doc, previewed minimized windows and it's clean beautiful interface.  

I finally decided to look for more modern enlightenment distro and came across OzOS.

A few basic/dumb questions:

Are there any dummy GUI tools to configure stuff like mouse speed, keyboard layout, network connection...

Will I be getting more from OzOS than eLive, stability?

thanks

John

---

### Post by molom on 2008-08-17
> **john_spiral said:**
> 
Are there any dummy GUI tools to configure stuff like mouse speed, keyboard layout, network connection...


Mouse... Yes, its under E17 configurations
Keyboard Layout... Ditto
Network Connection... I believe Wicd is installed by default, so yes.

> **john_spiral said:**
> 
Will I be getting more from OzOS than eLive, stability?


Definitely yes. More stability, far more features due to updated E17 version, more functionality, E17 can be updated, nicer community (Trust me, I'm always there ;) )

Cheers,
molom

---

### Post by Tux Aubrey on 2008-08-17
> **john_spiral said:**
> Hi,
I fell in love with version 6 of the window manger with it's 3d twirling windows, MacOSX like doc, previewed minimized windows and it's clean beautiful interface. 

e17 was a totally fresh start.  Elive maintained compatibility with a lot of e16 eye-candy that was dropped (or deferred) in the e17 development process.  Things like the dock and free floating gadgets and transition effects were the main causalities - but are slowly finding their way back. You will find a "pure" e17 a little less exciting but much quicker and cleaner.  

OzOS really does take a minimal and modular approach to almost everything - including the native e17 apps and eye-candy.  Basically, if it isn't totally stable in the wild, its not in the default OzOS install and you would have to add it.  (I'm playing around with itask-ng at the moment - it is a dock-like desktop gadget - very animated and cool but not the most stable of things and so not installed by default).

> **john_spiral said:**
> 
Are there any dummy GUI tools to configure stuff like mouse speed, keyboard layout, network connection...

Yes- as Molom says, all the configuration tools are easily available via gui (see pic below of the main config panel open at the mouse and keyboard bindings section).  We replaced the native e17 network manager with wiicd (a GTK front end) because it seemed to be more reliable, especially for wifi (but the e17 one is easily installed)

[IMG]http://cafelinux.org/forum/gallery/74_17_08_08_5_09_29.png[/IMG]
> **john_spiral said:**
> Will I be getting more from OzOS than eLive, stability?
Stability is what we are striving for - as well as lightness, elegance and ease of use  - all at the bleeding edge :)  

We are also trying to document things, especially for people just moving into Enlightenment from other WMs.

Enlightenment moves "sporadically" but there have been signs of new life recently and a new web site ( [http://exchange.enlightenment.org/](http://exchange.enlightenment.org/) ) that is a very active showcase for new themes and apps etc.

As Molom said, you'll get any support you need through the OzOS forums. - we love bug reports and suggestions too!

---

### Post by molom on 2008-08-17
I couldn't have put it any better Aubrey ;)

Cheers,
molom

---

### Post by smartboyathome on 2008-08-17
> **Tux Aubrey said:**
> We replaced the native e17 network manager with wiicd (a GTK front end) because it seemed to be more reliable, especially for wifi (but the e17 one is easily installed)

E17 doesn't have an "official" network manager. There is a 3rd party one in development on the exchange site, but its not nearly finished yet. I would say it was a wise decision to use WICD since it is modular and doesn't rely on the system tray like Network Manager.

**_*NOTICE: ALL E17 USERS:*_**
Yesterday, today, and maybe tomorrow if things don't go as planned (from what I understand), E17 will be moving to SVN. If you are using the OzOS repo, it won't be updating to the latest code (the CVS repository has been halted for changes). If you do want the latest code, you'll have to rewrite the script or wait for it to be updated (I have also posted this in the E17 tutorial thread, hopefully Rui will see it in a timely manor).

If all else fails, Aubrey, will you notify RAV for me, or Rui if he is more active on the OzOS board? That'd be great. Cheers and keep using E17!

Smartboy

---

### Post by Tux Aubrey on 2008-08-17
> NOTICE: ALL E17 USERS:
Yesterday, today, and maybe tomorrow if things don't go as planned (from what I understand), E17 will be moving to SVN. If you are using the OzOS repo, it won't be updating to the latest code (the CVS repository has been halted for changes). If you do want the latest code, you'll have to rewrite the script or wait for it to be updated (I have also posted this in the E17 tutorial thread, hopefully Rui will see it in a timely manor).


Thanks heaps for the warning!  I'll do an all points bulletin and shine the big "e" searchlight in the sky in the hope that Rui sees it.

---

### Post by molom on 2008-08-18
Are there any benefits to this change that you are specifying smartboyathome? Is this an indication of E17 being developed faster?

---

### Post by joker0n3 on 2008-08-20
Ive test the live cd. Id like to hear what others think cuase im personally thinking of using this over regular Ubuntu. Looks like it might use less resources. Well, opinions.....

---

### Post by smartboyathome on 2008-08-20
I use E17 on Arch, and I like it. I tried the OzOS cd setup, but I don't like some of the apps chosen (for example, I use PCManFM instead of Thunar). Anyway, it is really good, just not for me. :)

---

### Post by Calash on 2008-08-20
I put it on an older Dell Laptop in preparation for a vacation. I was going to tether it to my Windows Mobile phone for Internet.

Going from Ubuntu and it's Gnome interface it took some getting use to.  Once you get the hang of it the interface works well with the track-point style mouse.

I had some issues locating some of the control panels, but when in doubt you can go to the terminal and get where you need to be.

Functionality it works great.  It loads fast, runs very solid, and had no issues at all with my hardware.  I was surprised that it picked up the Hotel's hot-spot without me having to do a thing.

I would recommend trying it out.

---

### Post by enlightenment now on 2008-08-20
OzOS is great! The nice thing is that you can use a refined version of Gnome by installing their Gnome-Desktop-Package to have OzOS run even more efficient then vanilla Ubuntu.

Of course it is the most stable and elegant of any e17 distro I have used.

The nice thing is that beyond being a stable and efficient OS, the OzOS forums  are outstanding, the How-To's written are the best I have seen from any Linux distro. The How-To on how to run OzOS on a pen drive is particularly awesome.

Rui Pais, Aubrey and the development team at OzOS have done an outstanding job.

I overwhelmingly recommend all to try OzOS.

---

### Post by Mardon on 2008-08-20
I like the look of OzOs, I have downloaded it 3 times and i burn the iso to a cd and do a data integrity with Brasero and it shows corrupt files, so i tried to boot and it gets to running local boot scripts /etc/rc/local and stays their doing nothing. I tried the OzOs forum and no one seems to know what to do.I have burned allot of iso's over the years and never had this happen. Any ideas anyone? :confused: Thanks
Mark

---

### Post by 4Orbs on 2008-08-20
Did you check the md5sum before burning the iso?

If you already have Ubuntu installed, you can just add the OzOS desktop by following the instructions from their website [HERE.]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os")

---

### Post by Mardon on 2008-08-20
> **4Orbs said:**
> Did you check the md5sum before burning the iso?

If you already have Ubuntu installed, you can just add the OzOS desktop by following the instructions from their website [HERE.]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os")

Thanks 4Orbs, i solved the problem ( I think ) I burned it with another burner and it works fine .Thanks,
Mark
SOLVED

---

### Post by Sorivenul on 2008-08-21
OzOS is one of, if not THE best e17 distribution out there.  The crew and forums are awesome.  Maryan comes in a close second, IMHO.

---

### Post by K.Mandla on 2008-08-21
Merged several similar threads.

---

### Post by enlightenment now on 2008-08-24
> **Sorivenul said:**
> OzOS is one of, if not THE best e17 distribution out there.  The crew and forums are awesome.  Maryan comes in a close second, IMHO.

Agreed that OzOS is the best e17 distribution out there. The crew and the forums are incredible! (I can't speak for Maryan, I have never tried it)

---

### Post by Trespasser on 2008-08-26
Put me on the list of OzOS users, as well. And I agree that this is the best E17 distro that I have tried so far. I chose to use the install disc instead of adding the OzOS repos to Ubuntu's sources list. The only trouble I've had in OzOS is changing the system font size (very small) but I'm slowly working that out, too. A very beautiful and fast distro. All I can say is I'm very pleased so far.

Later...

---

### Post by enlightenment now on 2008-08-30
> **Trespasser said:**
> Put me on the list of OzOS users, as well. And I agree that this is the best E17 distro that I have tried so far. I chose to use the install disc instead of adding the OzOS repos to Ubuntu's sources list. The only trouble I've had in OzOS is changing the system font size (very small) but I'm slowly working that out, too. A very beautiful and fast distro. All I can say is I'm very pleased so far.

Later...

Glad to hear you like OzOS as much as I do.

The Devs have done an outstanding job, OzOS is truly not just the best e17 distro but with the Gnome-Package install it is also the best Gnome distro, albeit it would not be too far to even say it is the best Linux distro in existence, ever. ;)

Again, Thanks be to the Devs especially Rui Pais, Aubrey and others.

I am glad that these Devs have devoted their time and efforts to such a worthy cause.

---

### Post by Tux Aubrey on 2008-09-10
Last week, smartyboyathome posted:
> NOTICE: ALL E17 USERS:
Yesterday, today, and maybe tomorrow if things don't go as planned (from what I understand), E17 will be moving to SVN. If you are using the OzOS repo, it won't be updating to the latest code (the CVS repository has been halted for changes). If you do want the latest code, you'll have to rewrite the script or wait for it to be updated).

New scripts to update OzOS from the e17 svn are now available.  This hasn't been as straightforward as we thought it would be (partly due to some simultaneous breakage in the code base being uploaded to the svn while Rui was coding the changes!) But all seems well now (we have tested both the 64bit and 32bit OzOS).

The process is still manual for the moment but can be cut and pasted from [this thread at the CafeLinux forums]("http://cafelinux.org/forum/index.php/topic,1899.msg6304.html#msg6304").

---

### Post by enlightenment now on 2008-09-11
> **Tux Aubrey said:**
> Last week, smartyboyathome posted:


New scripts to update OzOS from the e17 svn are now available.  This hasn't been as straightforward as we thought it would be (partly due to some simultaneous breakage in the code base being uploaded to the svn while Rui was coding the changes!) But all seems well now (we have tested both the 64bit and 32bit OzOS).

The process is still manual for the moment but can be cut and pasted from [this thread at the CafeLinux forums]("http://cafelinux.org/forum/index.php/topic,1899.msg6304.html#msg6304").Thanks for the informative post Tux Aubrey it is greatly appreciated!

---

### Post by misterhead on 2008-09-11
I just started using OzOS yesterday, and absolutely love it so far. 
Right now I have 2 issues...

1. can't figure out how to switch monitor outputs like I could with Output Switcher, found here

[http://lilserenity.wordpress.com/2007/10/21/output-switcher-easy-linux-screen-management/](http://lilserenity.wordpress.com/2007/10/21/output-switcher-easy-linux-screen-management/)

2. Mouse side buttons aren't working yet.

... but as for the look and feel (when my laptop isn't docked with a second monitor, that is) I dig it.

---

### Post by misterhead on 2008-09-11
O.K. used aticonfig for outputs. It will be interesting to see what happes when I'm no longer docked, though. 
AND as it turns out the same xorg.conf adjustment for regular ubuntu, that gets side buttons to work, also did the trick on my OzOS. 
This is gonna take some getting used to, but I like it.

---

### Post by enlightenment now on 2008-09-13
> **misterhead said:**
> ...on my OzOS. 
This is gonna take some getting used to, but I like it.

This is exactly how I felt when I started using OzOS, now I just could not live without it.

---

### Post by Rui Pais on 2008-09-14
> **Tux Aubrey said:**
> Last week, smartyboyathome posted:


New scripts to update OzOS from the e17 svn are now available.  This hasn't been as straightforward as we thought it would be (partly due to some simultaneous breakage in the code base being uploaded to the svn while Rui was coding the changes!) But all seems well now (we have tested both the 64bit and 32bit OzOS).

The process is still manual for the moment but can be cut and pasted from [this thread at the CafeLinux forums]("http://cafelinux.org/forum/index.php/topic,1899.msg6304.html#msg6304").

Thanks for link here, Aubrey!

Just want to add that the new thread on Ubuntu forum about e17-svn it's here:
[http://ubuntuforums.org/showthread.php?t=916690](http://ubuntuforums.org/showthread.php?t=916690) 

Any issues specifically related with e17-svn can be put it there too.
Thanks all.

---

### Post by Rui Pais on 2008-09-14
> **enlightenment now said:**
> Glad to hear you like OzOS as much as I do.

The Devs have done an outstanding job, OzOS is truly not just the best e17 distro but with the Gnome-Package install it is also the best Gnome distro, albeit it would not be too far to even say it is the best Linux distro in existence, ever. ;)

Again, Thanks be to the Devs especially Rui Pais, Aubrey and others.

I am glad that these Devs have devoted their time and efforts to such a worthy cause.

> **enlightenment now said:**
> This is exactly how I felt when I started using OzOS, now I just could not live without it.


Thanks enlightenment now for your kind words!!

We are very happy to see such enthusiastic users. 
I'm very pleased that you're have a great time and a pleasant experience to with OzOS.

:)

---

### Post by Rui Pais on 2008-09-14
> **misterhead said:**
> O.K. used aticonfig for outputs. It will be interesting to see what happes when I'm no longer docked, though. 
AND as it turns out the same xorg.conf adjustment for regular ubuntu, that gets side buttons to work, also did the trick on my OzOS. 
This is gonna take some getting used to, but I like it.

Hi misterhead, sorry this late answer :( 
Glad to see you are find your your way around.

Your it's ofcourse the correct solution.
Just a generic advise, xorg.conf it's related to the hardware in a computer, not the linux installed. 
Once a user have a working xorg.conf he/she can use it on any linux installed, even if the linux install fails to automatically create a correct one (as long as xorg version don't be much outdated and drivers are present, of course).
I always keep a good xorg.conf for each box i have on a pen, so any times i got problems i just override the bad/incorrect one :)

---

### Post by misterhead on 2008-09-14
> **Rui Pais said:**
>  xorg.conf it's related to the hardware in a computer, not the linux installed. 
Once a user have a working xorg.conf he/she can use it on any linux installed, even if the linux install fails to automatically create a correct one 

Wow, I did not know that. So Since I have many different distro's on different hard drives and/or partitions, but all for the same laptop, I should be able to use the same working xorg.conf for all of them. 

Makes sense. Don't know why I never thought of that.

Thank you. 

B.T.W. On the Cafelinux OzOS forums, I am PerryEarl. I guess maybee I should keep things consistent, but... Oh well.

---

### Post by enlightenment now on 2008-09-16
> **Rui Pais said:**
> Thanks enlightenment now for your kind words!!

We are very happy to see such enthusiastic users. 
I'm very pleased that you're have a great time and a pleasant experience to with OzOS.

:)Good Welcome. Perhaps I am just a bit too over enthusiastic for some people.

I am Thankful that you have been the primary driving force behind OzOS, and what you have created could be called the best OS in existence.

---

### Post by Rui Pais on 2008-09-16
> **enlightenment now said:**
> Good Welcome. Perhaps I am just a bit too over enthusiastic for some people.

I am Thankful that you have been the primary driving force behind OzOS, and what you have created could be called the best OS in existence.


8) :D


> **misterhead said:**
> Wow, I did not know that. So Since I have many different distro's on different hard drives and/or partitions, but all for the same laptop, I should be able to use the same working xorg.conf for all of them. 

Makes sense. Don't know why I never thought of that.

Thank you. 

No problem :)
Yes, it's specially easier if autodetection on some of those distros don't figure things quite right (just as an example, i remember see several post of bad xorg.confs on 1st versions of Gutsy) or if you have some special set like drivers options or hardware flag.
In my case i have nvidia and don't like see the logo when X starts, so i always put that option off, and my Pt keyboard are only set if i do installation in Portuguese...

> **misterhead said:**
> 
B.T.W. On the Cafelinux OzOS forums, I am PerryEarl. I guess maybee I should keep things consistent, but... Oh well.
:lol:
I am RuiP on several forum, when i sigh UF i put my complete name don't remember why and now i use both. Not much consistent either...

---

### Post by Rui Pais on 2008-09-16
One thing that never cease to amaze me in relation to OzOS and a Wikipedia article i put there about it, it's the speed my article it's target for so many things... Neutrality, Notability... :-k

I checked the pages of close related distros like Maryan Linux and OpenGEU and they don't seems to suffer this :(

Looking for Ubuntu variants there are pages of one line entries of simplistic variants, others like Super Ubuntu may even violate trademarks or have license issues with so many proprietary apps, but have not a single reference to notability or whatever. 
No issues in "meet Wikipedia's quality standards"... 

Most of Ubuntu variation pages link only to distro site. 
I put on OzOS entry links for some articles i found about it on internet, totally independent, but no use. But it was always target for deletion.


Now it seems that will be delete on "**2008-09-20 17:27**" 
Cool!

For those that haven't read it yet, you have a few days left for read it.
:lol: :lol:

---

### Post by Rui Pais on 2008-09-16
A new procedure for OzOS users update they OZOS to new SVN source repo is now available.
Please let us know how your experience was!

So here the new procedure:
```
sudo apt-get update
sudo apt-get dist-upgrade

```
It must be dist-upgrade! (an ordinary upgrade will nor work and will fail on oz-e17-tools package)
After that you still need to run
```
update_e17.sh
```
or Click 'Update e17' on menu, under:
Applications > System tools > Update e17


A new release for both archs it's planned for soon, based on 8.04.1 and with the svn version implemented.

Have all fun
Rui

---

### Post by Rui Pais on 2008-11-09
Hi all,
a new OzOS it's available!

This is an update for the Hardy base, build with latest e17 from SVN.

It essentially corrects some issues that users report, contains all recent updates for the changes to SVN repositories and uses the most updated software of Xubuntu 8.10.1 base+Updates.

It's a 64bits version. A 32bits build by Tux Aubrey will be up soon!

Torrents (preferred):
[http://cafelinux.org/Downloads/oz-os/iso/ozos-0.9-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/ozos-0.9-livecd-amd64.iso.torrent)

Downloads:
[http://cafelinux.org/Downloads/oz-os/iso](http://cafelinux.org/Downloads/oz-os/iso)


NEWS & FEATURES:
- Signed authenticated repos.
- New Session it's now on Main menu and not on ibar, since it's only useful for multiusers systems.
- Menu cleanings (less duplicates)
- Entry on System tools named 'Graphics Driver Installation' that launch Envy or install it if not present
   (users don't need to know what envy is Smiley)
- WiCD installed by default, but not enabled. It use a similar scheme than envy, with a descriptively named 'Wireless Wicd start'.
- Firefox installed, but no longer a dependency of desktop (user may want to delete/replace by any other browser)
- oz-e17-tools and Aubrey's 6dozd by default with menu entries.
- Thunar with a "OzOS unique" search function implemented (by catfish)
- Scite completely tuned for text editor and code writer with an integrate look.
- Transmission and gajim on Favorites menus (they should run 1/section so not on ibar where they would be useless most of time)
- LiveCD translations and help files get reference for OzOS not Ubuntu.
- Better choice of default modules (more general and hardware compatible)

Some version numbers:
Kernel: 2.6.24-21
e17:  0.16.999.050
gcc:  4.2.4
Firefox: 3.0.3

Hope you all like it!

Rui

---

### Post by kagashe on 2008-11-09
SOLVED
I am running OZ-OS 0.5 Live CD (i386). I don't see any panels on the desktop. If I right click, I get a menu which does not show all applications, e.g. I can start abiword from command but it does not show in the right click menu.

I am trying to attach screenshot.

kagashe

I accidentally left clicked on the desktop and got the menu.

---

### Post by smartboyathome on 2008-11-09
You have to add some applicaations in order to use them. Menu > Configuration > Configuration Panel > Applications > Add Application.

---

### Post by kagashe on 2008-11-09
> **smartboyathome said:**
> You have to add some applicaations in order to use them. Menu > Configuration > Configuration Panel > Applications > Add Application.Yes I know but I am trying Live CD and yet to install. I should be able to add bottom panel on Live CD isn't it?

kagashe

---

### Post by Tux Aubrey on 2008-11-09
kagashe 

There are no panels - just the "shelves" you see on your screenshot.

You can configure shelves however you like in e17 - including by making them into full width (or height) "panels".

I did a "How-To" on it [**here**]("http://cafelinux.org/OzOs/content/how-use-gadgets-modules-and-shelves").  You can make it look anyway you want, including having a "Start" button.

I'm more concerned that you don't have your menus!  Try _LEFT_ CLICKING on the desktop and looking under "Applications"

By the way - the 32 bit OzOS version 0.9 should be available tomorrow.  It is based on Hardy and has some nice new features (but the default desktop is still like your screenshot.

---

### Post by kagashe on 2008-11-09
> **Tux Aubrey said:**
> kagashe 

There are no panels - just the "shelves" you see on your screenshot.

You can configure shelves however you like in e17 - including by making them into full width (or height) "panels".

I did a "How-To" on it [**here**]("http://cafelinux.org/OzOs/content/how-use-gadgets-modules-and-shelves").  You can make it look anyway you want, including having a "Start" button.

I'm more concerned that you don't have your menus!  Try _LEFT_ CLICKING on the desktop and looking under "Applications"

By the way - the 32 bit OzOS version 0.9 should be available tomorrow.  It is based on Hardy and has some nice new features (but the default desktop is still like your screenshot.Thanks.I had used gOS briefly and remembered that there are no panels but "shelves" "ibox" "ibar" etc. I could add other applications in the ibar.

Thanks for the information. I will wait for 8.10 version, meanwhile I could play with the Live CD.

kagashe

---

### Post by Tux Aubrey on 2008-11-11
Both versions of OzOS 0.9 are now available:


64 bit Torrent
[http://cafelinux.org/Downloads/oz-os/iso/ozos-0.9-livecd-amd64.iso.torrent](http://cafelinux.org/Downloads/oz-os/iso/ozos-0.9-livecd-amd64.iso.torrent)

32 bit Torrent on LinuxTracker:
[http://linuxtracker.org/index.php?page=torrent-details&id=aa0bbe0f193803cc35862e9da8145e9d3f255240](http://linuxtracker.org/index.php?page=torrent-details&id=aa0bbe0f193803cc35862e9da8145e9d3f255240)


Downloads:
[http://cafelinux.org/Downloads/oz-os/iso](http://cafelinux.org/Downloads/oz-os/iso)

Both are Hardy-based and incorporate updated OzOS utilities (the e17 backup, restore functions etc).

enjoy

---

### Post by Tux Aubrey on 2008-11-24
Since the release of OzOS 0.9, there have been a few other Oz and e17 developments that might be of interest to anyone using e17 built from svn source code.  In particular, Rui Pais has reworked the OzOS scripts to provide a warning if the current version of code on the svn has any fatal flaws that prevent it compiling.  That should help people avoid those, all too frequent, Bad Code Days over at the svn.  There have also been some recent changes to the e17 API that have broken a number of (well, almost all really) Enlightenment themes.  Its more annoying than fatal and there are work-arounds.  Shades of 2006 (for those who remember The Great e17 Theme Breakage)!.  

I have started [a blog ]("http://cafelinux.org/OzOs/blogs/aubrey")about the key developments in OzOS and the e17 desktop so that anyone interested can have a single source of regular (like weekly) news.

---

### Post by Ripfox on 2008-11-26
Am using this on an old athlon 1ghz 320mb ram and it is doing QUITE WELL.

Thank you.

---

### Post by Rui Pais on 2008-11-28
> **Ripfox said:**
> Am using this on an old athlon 1ghz 320mb ram and it is doing QUITE WELL.

Thank you.

You're welcome.

Glad you like it!

---

### Post by Rui Pais on 2009-01-06
Hi.
Just some news on OzOS.

A screenshot illustrated installation, in Portuguese:

[http://cafelinux.org/forum/index.php/topic,2488.0.html](http://cafelinux.org/forum/index.php/topic,2488.0.html)

---

### Post by mpsii on 2009-02-04
Just a quick question:

Why is GDM used instead of Entrance for the login manager? Not complaining... just curious.

I like the ELive CD's use of Entrance and basically all things e17. I know you are utilizing Xubuntu as a base (still? not 100% sure). Is that why GDM is used?

---

### Post by smartboyathome on 2009-02-05
> **mpsii said:**
> Just a quick question:

Why is GDM used instead of Entrance for the login manager? Not complaining... just curious.

I like the ELive CD's use of Entrance and basically all things e17. I know you are utilizing Xubuntu as a base (still? not 100% sure). Is that why GDM is used?

Because GDM is stabler than Entrance... and Entrance doesn't play well with the easy_e17.sh script. ;)

---

### Post by mpsii on 2009-02-05
Is it an Ubuntu thing? If it all works with Debian (lenny/sid) for ELive...

Is the script not used by the ELive group?

---

### Post by Tux Aubrey on 2009-02-05
>  Is it an Ubuntu thing? 

There are two related aspects of OzOS 

- at the "core" are scripts that download, compile, install etc e17 source code from the developers server (using svn).  These are available separately for "any" Debian-based distro that is **NOT** using an e17 .deb package (from repos).  I say "any" because I'm not sure that all, beyond the 'buntus and Debian itself have been thoroughly tested.  

The scripts are available via metapackages are available from the OzOS repos.  They include:

e17_svn - which is the stuff for getting a very "raw" and fairly minimal e17 installed from source.  The script is actually easy_e17.sh (by e17 dev Morlenxus) with some modifications by Rui Pais. ([This thread]("http://ubuntuforums.org/showthread.php?t=916690") covers just e17_svn)

oz-e17-tools - tools for updating and general managing of Enlightenment from SVN.  This one adds a lot of user control over the install and maintenance of e17.  The core script is update_e17.sh by Rui Pais.  

oz-desktop - which is a "real" metapackage" that pulls in all the additional applications, profiles etc that give the distro its characteristic "look and feel" and functionality.  Rui put this one together too.

There are about a dozen other packages - extra e17 themes, gtk and gdm themes, a optional minimal gnome desktop as well as science and kids packages.

There's an off-site How-To on getting the "full" OzOS onto an existing install [here]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os").  (I currently have versions running on Feisty, Intrepid and Jaunty, as well as Debian Lenny and Dreamlinux - and I know at least one user has also done the deed with Linux Mint)

- the LiveCD version is based on Xubuntu (cut down a little), the OzOS scripts and the main packages from the repos.  It does come with a version of e17 already installed and can be used like a "normal" distro - but we'd recommend running the automated e17 update function at least once to get things aligned and current (I run mine every day, but I'm an addict). The build on the iso is from last November - about the same vintage in fact that OpenGEU and ELive are currently using, I believe.  Everything else can be updated via Update Manager or Synaptic or apt - just like any 'buntu - and all the Ubuntu repos are enabled.

> 
If it all works with Debian (lenny/sid) for ELive...


Is the script not used by the ELive group? 

While the script (or something like it) is probably used somewhere upstream in the ELive development process, it is not part of the distro.  They (or someone else) compile e17 (and some parts of e16) into a .deb and then install it onto Debian Lenny and then add a couple of their unique tools (ELPanel). Similarly Open GEU (and Maryan Linux) use e17 debs to add it to 'buntu.  Updates happen when someone compiles a more up-to-date build into a deb.

OzOS is quite a different concept. The compiling happens on your machine whenever you feel like getting an up-to-date (literally to-the-minute) version of e17.  (We did this partly out of frustration with the lack of regular - like even yearly - snapshot updates from the e17 developers and debian packagers - no offense to those good people!).

The two different approaches (as opposed to the developers and the communities ;) ) are quite antagonistic.  Like matter and anti-matter really - with similar results if you were to put the two on the same install.  Basically the config files would fight to the death until one or both died a grizzly and messy death.  I don't want to even think about it!

There's a longer version of this story but it would probably bore you.

---

### Post by meborc on 2009-02-05
> **Tux Aubrey said:**
> ...

so what you are saying is - entrance does not play nice with current (very up-to-date) e17, but does work with older e17 deb packages?

sorry for this question, but for me, entrance seems to be just one part of enlightenment and it gives a very important visual impact for the user

isn't there a entrance svn? which you could also install/update via a script?

---

### Post by smartboyathome on 2009-02-05
> **meborc said:**
> so what you are saying is - entrance does not play nice with current (very up-to-date) e17, but does work with older e17 deb packages?

sorry for this question, but for me, entrance seems to be just one part of enlightenment and it gives a very important visual impact for the user

isn't there a entrance svn? which you could also install/update via a script?

Entrance is in SVN, but if you install it with the easy_e17.sh script, it installs everything in /opt/e17, when Entrance has some hardcoded paths. Instead, we would have to provide an extra binary package (not in the spirit of OzOs).

---

### Post by meborc on 2009-02-05
> **smartboyathome said:**
> Entrance is in SVN, but if you install it with the easy_e17.sh script, it installs everything in /opt/e17, when Entrance has some hardcoded paths. Instead, we would have to provide an extra binary package (not in the spirit of OzOs).

well, too bad... i hope enlightenment will reach some sort of stable stage some day that distributions could benefit from the impressive eyecandy entrance and e17 can offer...

gdm+e17 seems so unnatural, but that's just me :)

---

### Post by smartboyathome on 2009-02-05
> **meborc said:**
> well, too bad... i hope enlightenment will reach some sort of stable stage some day that distributions could benefit from the impressive eyecandy entrance and e17 can offer...

gdm+e17 seems so unnatural, but that's just me :)

You can always disable the login manager and start E17 from the shell (or even autostart it! :D). I do this on Arch, as I set it to autostart when I start up, logging in and all, without GDM or anything.

---

### Post by meborc on 2009-02-06
> **smartboyathome said:**
> You can always disable the login manager and start E17 from the shell (or even autostart it! :D). I do this on Arch, as I set it to autostart when I start up, logging in and all, without GDM or anything.

yes, that makes it faster... but i so much prefer the sleekness and eyecandy of entrance

---

### Post by chris4585 on 2009-02-06
This isn't OzOS specific, but could someone help me.  I'm running arch, and when trying to load the module gadgets I get the error in my thumbnail.

Thanks.

---

### Post by smartboyathome on 2009-02-06
> **chris4585 said:**
> This isn't OzOS specific, but could someone help me.  I'm running arch, and when trying to load the module gadgets I get the error in my thumbnail.

Thanks.

First off, how did you install E17 on Arch. Via the Community repos, Ronald's update script, or my easy-e17 package.

---

### Post by chris4585 on 2009-02-06
> **smartboyathome said:**
> First off, how did you install E17 on Arch. Via the Community repos, Ronald's update script, or my easy-e17 package.

Through the community repo.

---

### Post by smartboyathome on 2009-02-06
> **chris4585 said:**
> Through the community repo.

In that case, you might want to update via Ronald's script (see the wiki). It was probably a bug at the time of the snapshot. I, personally, find it easiest to use my easy-e17 package to keep things up to date (its basically the same as what OzOs uses, but for Arch), as it allows me to not spend unnecessary time compiling unneeded updates (Ronald's script recompiles everything, easy_e17 only recompiles what is updated).

---

