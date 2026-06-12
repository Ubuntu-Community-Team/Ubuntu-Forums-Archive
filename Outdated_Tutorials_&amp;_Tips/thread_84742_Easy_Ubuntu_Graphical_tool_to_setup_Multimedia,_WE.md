---
title: "Easy Ubuntu: Graphical tool to setup Multimedia, WEB plugins and more!"
date: 2005-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by keyes on 2005-10-31
**Admin: can you stick and lock this topic?**

Easy Ubuntu is an easy way to make Ubuntu usable in few minutes. This a graphical tool for begginers.
With Easy Ubuntu you can use Ubuntu as your main system without any knowledge about Linux!

(This is a French outdated screenshot but Easy Ubuntu is translated in English and many other languages)
[img]http://placelibre.ath.cx/keyes/images/Informatique/EasyUbuntu2.3.png[/img]

**Easy Ubuntu allow you to:**
    * Add extra repositories for installing a lot of additional software.
    * Install multimedia codecs for reading all videos, musics and DVDs.
    * Activate the "audio preview" feature in Nautilus.
    * Active DMA if possible
    * Install the most needed Firefox plugins: Flash, Java, Real, videos. Adds Microsoft fonts, GNOME's Firefox buttons, officials Firefox icons.
    * Install archiving support for RAR, ACE and 7ZIP.
    * Install aMule,a clone of eMule.
    * Install the Skype voice-over-IP software.
    * Install AMSN cvs with webcam support.
    * Active the num lock at system startup.
    * Install the NVIDIA or ATI driver for 3D support.

A "Remover" is provided.

Get [Easy Ubuntu 2.4 beta3](http://placelibre.ath.cx/keyes/index.php/2005/10/27/65-easy-ubuntu-24-beta)

**To run Easy Ubuntu**
* Double click on EayUbuntu-2.4beta3.tar.bz2
* Click on the "Extract" button in file-roller
* Go to the created "EasyUbuntu" directory
* Double click on EasyUbuntu
* Nautilus ask you what do you want, click "Run"
* EasyUbuntu ask **your** password
* Fill the form and follow the instructions

Note:
* Kubuntu users can use the exellent [Easy Kubuntu](http://olwin.free.fr/serendipity/index.php?/archives/1-Easy-Kubuntu-0.4-beta.html) (translated in French and English) by Olwin
*  Experimented users would take a look at [Automatix](http://ubuntuforums.org/showthread.php?t=66563) a powerful script who allow to install lot of softwares not included in Easy Ubuntu !

**Please go to the [official Easy Ubuntu forum](http://ubuntuforums.org/forumdisplay.php?f=86) for help and support**

---

### Post by imagine on 2005-10-31
Hmm what exactly is the difference between Easy Ubuntu and Automatix?

---

### Post by keyes on 2005-11-01
Easy Ubuntu is designed for beginners. It just install needed packages and repositories to a Multimedia and WEB usage according to the Ubuntu developers choices (i.e: don't replace Totem by Mplayer).
It also touch configurations files only if highly needed (just sources.list and /etc/X11/gdm/Init if "Num Lock" is checked).
The goal of this script is to be easy and safe (no prelink, no Debian Menu, no programming tools and other stuff who afraid beginners).
Easy Ubuntu is also translated in few languages (French, Spanish, Finnish, German, Deutsch, Japanese, Russian, Italian, Brazilian).

Automatix is derived from Easy Ubuntu (Easy Ubuntu was the first and Autmatix include a lot of code coming from Easy Ubuntu) to help middle and advanced users. This is not the same goal.

---

### Post by imagine on 2005-11-01
Ok, thanks for both the answer and the tool.

Btw "Deutsch" == "German" : )

---

### Post by keyes on 2005-11-01
Dutch not Deutsh i'm sorry :)

---

### Post by fut21 on 2005-11-02
Why is this thread not in the sticky ones like "Automatix".

---

### Post by gitfiddler on 2005-11-02
Truly Excellent! I recommend this to everyone, even those who like to "roll your own" config after a fresh install. It takes care of (almost) all of those things we were going to do anyway! Many thanks.

---

### Post by Dracontopes on 2005-11-03
This will come in handy when I'm reinstalling Ubuntu sometimes. :D

Offtopic: what theme is that on your screenshot?

---

### Post by fut21 on 2005-11-04
It`s nearly "to easy", a really nice tool witch setup your newly installed ubuntubox i 20 minutes.

---

### Post by Poul on 2005-11-04
[quote=Dracontopes]
Offtopic: what theme is that on your screenshot?[/quote]
Same question here:smile:

---

### Post by christooss on 2005-11-04
Hm  does Easy ubuntu checks which programs are already installed. There shouldn't be so many default checked programs.

---

### Post by XDevHald on 2005-11-06
Just a quick heads up, this does work on Dapper Drake 6.04 and has been tested with gtk2 :)

Breezy users might experience a difference in the application using compared to Dapper users as the repo version and lib versions are different in Dapper compared to Breezy.

---

### Post by pioni on 2005-11-08
Very nice, but where's Quicktime support? I tried viewing the trailers at apple.com/trailers and Totem said it didn't find suitable plugin. How do I add support for Quicktime? I'm using a fresh install of Breezy.

---

### Post by mdsmedia on 2005-11-08
Not sure if I did something wrong, but having run Easy Ubuntu...and no change in the applications on my system, still cant play real video in firefox....I opened synaptic and it came up with a list of problem files...all with Breezy mentioned.

Does Easy Ubuntu know that I'm using Hoary? Or should I have changed something within Easy Ubuntu first?

The initial post gave step by step instructions on running Easy Ubuntu and I just followed them.

---

### Post by igor4u on 2005-11-12
Sorry, but cyrillic fonts not working after install

---

### Post by jmeadows111 on 2005-11-13
I was setting up a new install of Breezy, and trying to use Easy Ubuntu. When I run the script (and it tries to update sources) I get:

cp: cannot stat `lang/en/EasyUbuntu.mo': No such file or directory
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by foolio0001 on 2005-11-15
I just installed Kubuntu last night, and tried to use Easy Kubuntu to load my codecs and Nvidia drivers and before it even lets me select what I want to install. It gives the error 'Update Repositiories Failed'

---

### Post by missmoondog on 2005-11-17
well, just like most apps i've noticed in ubuntu, it doesn't work correctly the first try. the only thing it did, other than give me the same long list of errors as somebody already posted, was set the number lock on, i think. i might have already edited that a few minutes go, i forget. going through all these hoops just to get audio/video to work, i forgot what i'm doing.

hey dad,
if you're still going through these postings to see what i'm saying about ubuntu, here's one for you:

STICK IT UP YOUR A**!! 
you can use this stupid os, i'm going back to windows!!

---

### Post by Nasso on 2005-11-18
thank you for this wonderful piece of software :)
Getting ubuntu go work as you want with multimediasupport and all that can be hard for a beginner. Using easyubuntu all you have to do is install ubuntu and run easyubuntu and everything works fine!  THX!

---

### Post by migo on 2005-11-19
The progress bar on installing archiving tools has been playing pong for the past 3 hours, is it safe to click cancel?

---

### Post by cornishr on 2005-11-19
I installed Easy Ubuntu into Breezy.  I call Quicktime Movie Trailers and try Small, Medium and Large.  Totem plays small but I get an Error Message with Med or Large that there is no plugin for that movie.  At Location on the Browser I entered "about:plugins" and the listing includes other players such as Gxine and Mplayer.   Which of these players should be called for the Medium/Large QT products and how do I change either the player or browser to execute the right player?:confused:  How can I setup Firefox to automatically play the media stream provided by the site?

---

### Post by 0okami on 2005-11-22
[QUOTE=Poul]
Originally Posted by Dracontopes
Offtopic: what theme is that on your screenshot?
----
Same question here:smile:

[/QUOTE]

That looks like... [http://www.gnome-look.org/content/show.php?content=26050](http://www.gnome-look.org/content/show.php?content=26050)
Blended meta city theme.... i could be drasticly wrong.

---

### Post by bored2k on 2005-11-22
keyes wants this thread locked and I think I'll grant him that.

---

