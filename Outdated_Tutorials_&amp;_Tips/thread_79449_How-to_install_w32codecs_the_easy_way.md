---
title: "How-to install w32codecs the easy way"
date: 2005-10-20
forum: Outdated Tutorials &amp; Tips
---

### Post by fut21 on 2005-10-20
How to add extra repositories, type:
sudo gedit /etc/apt/sources.list
in a terminal and add these lines:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

hit the "save" button in gedit and close it.

Type:
sudo apt-get update 
in a terminal and
sudo apt-get install w32codecs

There are also other packages like libdvdcss2 and sun-j2re1.5 on the same mirror.
Look here:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

I hope you understand my english are very bad.

---

### Post by fut21 on 2005-10-20
Ubuntu PLF want your support. Read on here:
[http://placelibre.ath.cx/keyes/index.php/2005/10/14/56-plf-ubuntu-meeting-summary](http://placelibre.ath.cx/keyes/index.php/2005/10/14/56-plf-ubuntu-meeting-summary)

---

### Post by souled on 2005-10-20
Are these repos safe to keep in your sources.list? (i.e. they won't break your system if you leave them enabled)

Thanks for this,

---

### Post by fut21 on 2005-10-20
Everythin works, but of course i can not gareentee anyting.

---

### Post by ember on 2005-10-20
O.k. Do I get that right. You need more people that build packages?

---

### Post by fut21 on 2005-10-20
I am not a part of the PLF projekt. But it looks like they want people to help them build packages.

---

### Post by fut21 on 2005-10-20
I have tryed to use them with online radio and DVD-movies, i find these files work better than those from:
ftp.nerim.net or [ftp://cipherfunk.org](ftp://cipherfunk.org)
With libdvdcss2 from
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) 
my dvd menues work better.

---

### Post by ember on 2005-10-20
Fine - I'll have to try that. Maybe my mplayerplugin will crash less often.

---

### Post by !nkubus on 2005-10-20
Wow pretty cool.

I've setuped my 64bit to run 32bit soft and it worked like a charm in forefox :D

---

### Post by majikstreet on 2005-10-20
You should change "konsole" to "in a terminal", because not everyone uses kde and this is not desktop enviroment specific :)

---

### Post by fut21 on 2005-10-20
[QUOTE=majikstreet]You should change "konsole" to "in a terminal", because not everyone uses kde and this is not desktop enviroment specific :)[/QUOTE]

Done :D

---

### Post by ManLord on 2005-10-20
Check.. i now have w32codecs installed. But totem or kaffeine still don't play the media.. like .avi

---

### Post by j_baer on 2005-10-21
fut21,

I tried the Easy Ubuntu on a fresh install of breezy and for the most part it worked. Nice job and thanks for the effort.

Things that didn't work ...

1) Synaptic complained of a broken package which was easily fixed.

2) The nvidia drivers didn't install but the system still worked.

3) Although adding the w32codecs is a step in the right direction, the totem plugin for firefox still doesn't work. You might consider installing mplayer and the mplayer plugin. There is some discussion in the forum about mplayer with GTK. I think would be a nice solution.

Thank you and keep up the good work ...

Cheers ...

---

### Post by keyes on 2005-10-21
Hello, I'm an admin from PLF Ubuntu and also the Easy Ubuntu writer.

PLF need you! Of course we need maintainers for packages but we need testers too.
All the packages are tested before going to the main repositories (free and non-free).

To test packages (i.e: now RealPlayer, Avidemux and divx4linux are purposed to be tested) just add this line to your sources.list:
```
deb http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/ breezy free non-free
```

Please send feedback on our mailing list: [https://www.zarb.org/mailman/listinfo/ubuntu-plf_discuss](https://www.zarb.org/mailman/listinfo/ubuntu-plf_discuss)

---

### Post by fut21 on 2005-10-21
[QUOTE=j_baer]fut21,

I tried the Easy Ubuntu on a fresh install of breezy and for the most part it worked. Nice job and thanks for the effort.

Things that didn't work ...

1) Synaptic complained of a broken package which was easily fixed.

2) The nvidia drivers didn't install but the system still worked.

3) Although adding the w32codecs is a step in the right direction, the totem plugin for firefox still doesn't work. You might consider installing mplayer and the mplayer plugin. There is some discussion in the forum about mplayer with GTK. I think would be a nice solution.

Thank you and keep up the good work ...

Cheers ...[/QUOTE]

I have nothing to do with the "easy ubuntu" projekt. It`s KEYES`s projekt and now he also have made PLF ubuntu, a very nice projekt indeed !

---

### Post by bored2k on 2005-10-21
[QUOTE=ManLord]Check.. i now have w32codecs installed. But totem or kaffeine still don't play the media.. like .avi[/QUOTE]
install totem-xine and kaffeine-xine

---

### Post by sk545 on 2005-10-21
hmm, so how does the w32codecs package differ from the one that is in multiverse/or universe?

---

### Post by bored2k on 2005-10-21
[QUOTE=sk545]hmm, so how does the w32codecs package differ from the one that is in multiverse/or universe?[/QUOTE]
Simply put, there is no equivalent to w32codecs in multi/universe. This package contains codecs which could be considered illegal to distribute in certain countries, so "stable" repositories try to avoid them in order to _not get closed down.

---

### Post by corefile on 2005-10-22
[QUOTE=fut21]How to add extra repositories, type:
sudo gedit /etc/apt/sources.list
in a terminal and add these lines:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

hit the "save" button in gedit and close it.

Type:
sudo apt-get update 
in a terminal and
sudo apt-get install w32codecs

There are also other packages like libdvdcss2 and sun-j2re1.5 on the same mirror.
Look here:
[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

I hope you understand my english are very bad.[/QUOTE]



I tried this (+libdvdcss2) and it wants to install gcc3.3 base and libstdc++5, I really don't want to install those, why do I need to install gcc3.3 to install these packages? Or just libstdc++5 if I want to install just the w32codecs

---

### Post by fut21 on 2005-10-22
[QUOTE=corefile]I tried this (+libdvdcss2) and it wants to install gcc3.3 base and libstdc++5, I really don't want to install those, why do I need to install gcc3.3 to install these packages? Or just libstdc++5 if I want to install just the w32codecs[/QUOTE]

I have no problems at all, everything work the right way.

---

### Post by theraginasian on 2005-10-23
Thanks a ton, this nice considering the lack of backports, AND, the fact that Backports will now have to come up with a different method of offering these codecs... stupid media jerks have to ruin all the fun don't they :p.

---

### Post by iNerdSure on 2005-10-23
Hi, can't progress beyond:
11:~$ sudo gedit /etc/apt/sources.list

(gedit:17292): Gdk-WARNING **: locale not supported by Xlib

(gedit:17292): Gdk-WARNING **: cannot set locale modifiers

What am I missing? I'm a Linux convert newbie. Please help. Thanks.

---

### Post by ludzter on 2005-10-23
Hi 

I got the same problem as [COLOR="red"]corefile[/COLOR].
[quote="corefile"]
I tried this (+libdvdcss2) and it wants to install gcc3.3 base and libstdc++5, I really don't want to install those, why do I need to install gcc3.3 to install these packages? Or just libstdc++5 if I want to install just the w32codecs[/quote]

I did install it, but now i run with the old gcc3.3 in my system, can i fix this?

/Ludzter

---

### Post by MirSPCM on 2005-10-23
Hi i'm Philippe Mironov.
I mantain the ubuntu-plf repositories and i'm the author of w32codecs.


Thank you very much for your feedback. We really need testers if you have some spare time testing such packages please join our mailing list.


I'm here to answer your questions about gcc3 dependencies ...

In fact, it's pretty simple :
The the w32codecs package contains *cook* and *drvc* codecs wich depend on libstdc++.so.5 wich depends on the gcc3.3 package.

So, if you want to be able to use theses codecs you will need libstdc++5 (and gcc3.3 as it depends on it, why ? ask ubuntu). If you don't care about this codecs, you can force the installation without checking dependencies.

You should note most of plf packages will be needing libstdc++5 (as it's often binary release we don't have control on) to work (as realplay skype etc)

Please mail me directly or join our mailing list as i'm not following the ubuntu forums actively.


All up to date information can be found on our wiki page, (if not, ask the mailing list) : [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

---

### Post by pcatiprodotnet on 2005-10-23
[QUOTE=corefile]I tried this (+libdvdcss2) and it wants to install gcc3.3 base and libstdc++5, I really don't want to install those, why do I need to install gcc3.3 to install these packages? Or just libstdc++5 if I want to install just the w32codecs[/QUOTE]

Does this mean it Uninstalls the higher version gcc?  If not, does it hurt anything to have two gcc versions on your pc?  And, will programs automatically use the highest version if they can?

---

### Post by MirSPCM on 2005-10-24
[QUOTE=pcatiprodotnet]Does this mean it Uninstalls the higher version gcc?  If not, does it hurt anything to have two gcc versions on your pc?  And, will programs automatically use the highest version if they can?[/QUOTE]

It does not uninstall the other version of gcc.
You can have both packages on your system they don't conflict.

reinstall gcc 4.0.1 after installing gcc3.3 just in case thought.

---

### Post by pato101 on 2005-10-24
Hmmm, is there a w64codecs package?
I'm a happy AMD64 user, with limited multimedia capabilities right now...

---

### Post by MirSPCM on 2005-11-03
[QUOTE=pato101]Hmmm, is there a w64codecs package?
I'm a happy AMD64 user, with limited multimedia capabilities right now...[/QUOTE]

Well i didn't see any codec pack release for windows 64 bit yet .. if ever that exists :)

---

### Post by missmoondog on 2005-11-03
now i find this thread after just i spent the better part of 2 days trying to get the audio and video working on 3 machines/new install of Ubuntu 5.04!! turned out to be nothing more than getting fffmplayplugin (something like that).

---

### Post by iluminate on 2005-12-14
Well it was easy to install the w32codecs (as the title of this thread) but I still can not get it to work.
Have tried xine, Mplayer, Totem, gXine, VLC to play .wmv files but with out success.
The screen is green and scrambled<< Obviously a codec issue.
Do I have to do something to the config files of each player to point out the directory to /usr/lib/win32???
Any help would be very much appreciated.

P.S
Have ditched M$ completely now and I feel FREE...FREE like a bird.....:D  Except for this codec issue I love Linux - a big thanks for the Ubuntu Team and to this forum who has made it possible
D.S

---

### Post by cramlow on 2005-12-18
I followed exactly what you typed and got this -

cramlow@ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package w32codecs
cramlow@ubuntu:~$

What to do pleasy.

---

### Post by cramlow on 2005-12-18
I got this -

cramlow@ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_mai n_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_res tricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package w32codecs
cramlow@ubuntu:~$

---

### Post by L34NN3 on 2007-01-13
Hi. I'm having the same problem - I got this with the previous command. Having spent the best part of 2 days trying to sort this mess out I'm startin to think maybe binning windows was a bad idea! At least it worked...

leanne@leanne-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

I have also tried installing (without success) libdvdcss2 using symantec and adept with no success. It just doesn't seem to register that they are there.

---

### Post by asnd16 on 2007-02-17
Package w32codecs has no installation candidate


I get this error:popcorn:

---

### Post by kobewan on 2007-02-17
I think that the PLF repository has moved to:

# PLF Repository
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

So you may want to put that in your sorces.list, update and then try again.

If that still doesn't work, I recommend:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Works like a charm.

---

### Post by brodiepearce on 2007-02-18
> **kobewan said:**
> I think that the PLF repository has moved to:

# PLF Repository
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

So you may want to put that in your sorces.list, update and then try again.


This worked for me, just needed to replace edgy with dapper.  Thank you!

---

