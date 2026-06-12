---
title: "HOW-TO: Always stay up-to-date with Exaile using SVN"
date: 2007-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by MetalMusicAddict on 2007-02-24
[CENTER][SIZE="3"]**[COLOR="Red"]WARNING![/COLOR] This is only for people who want to stay on the bleeding edge of [Exaile]("http://www.exaile.org/")! [COLOR="Red"]WARNING![/COLOR]**[/SIZE][/CENTER]

[IMG]http://img385.imageshack.us/img385/7503/tracbannerxp7.png[/IMG]

I'm a [Exaile]("http://www.exaile.org/") fanboy at the moment. I use BZR and no real problems. This HOW-TO assumes you have all the proper things installed to run Exaile normally. This works for me on Edgy, Feisty and Gutsy. If you want to stay on the edge like I do, here you go.

**[SIZE="3"]1[/SIZE].** We need some software. From a terminal:
```
[SIZE="1"]sudo apt-get install bzr[/SIZE]
```

**[SIZE="3"]2[/SIZE].** Now a script. From a terminal:
```
[SIZE="1"]sudo gedit /usr/local/bin/exaile-bzr[/SIZE]
```
Now paste in this text:
```
[SIZE="1"]#!/bin/bash
cd Exaile-BZR && bzr pull
~/Exaile-BZR/exaile[/SIZE]
```
Now we make it executable:
```
[SIZE="1"]sudo chmod +x /usr/local/bin/exaile-bzr[/SIZE]
```

**[SIZE="3"]3[/SIZE].** Now lets make a launcher.  From a terminal:
```
[SIZE="1"]sudo gedit /usr/share/applications/exaile-bzr.desktop[/SIZE]
```
Now paste in this text:
```
[SIZE="1"][Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Exaile!-BZR
GenericName=Music Player
Comment=Listen to, browse, or edit your audio collection
Exec=exaile-bzr
Terminal=false
Type=Application
Icon=/home/atm/Exaile-BZR/images/icon.png
Categories=Application;AudioVideo;AudioPlayer;GTK
MimeType=audio/x-musepack;application/x-musepack;audio/musepack;application/musepack;application/x-ape;audio/ape;audio/x-ape;audio/x-musepack;application/x-musepack;audio/musepack;application/musepack;application/x-ape;audio/ape;audio/x-ape;audio/x-mp3;application/x-id3;audio/mpeg;audio/x-mpeg;audio/x-mpeg-3;audio/mpeg3;audip/mp3;audio/x-mp3;application/x-id3;audio/mpeg;audio/x-mpeg;audio/x-mpeg-3;audio/mpeg3;audip/mp3;audio/x-m4a;audio/x-m4a;audio/mpc;audio/x-mpc;audio/mp;audio/x-mp;audio/mpc;audio/x-mpc;audio/mp;audio/x-mp;application/ogg;application/x-ogg;audio/vorbis;audio/x-vorbis;audio/ogg;audio/x-ogg;application/ogg;application/x-ogg;audio/vorbis;audio/x-vorbis;audio/ogg;audio/x-ogg;audio/x-flac;application/x-flac;audio/flac;audio/x-flac;application/x-flac;audio/flac;[/SIZE]
```

**[SIZE="3"]4[/SIZE].** In a Terminal:
```
bzr branch http://bazaar.launchpad.net/~exaile-devel/exaile/main Exaile-BZR

```
**[SIZE="3"]5[/SIZE].** Find the entry in your Sound&Video section of the menu and launch it.

The icon will be missing from the menu entry until you restart Gnome. You can just log out then in again.

Two folders should appear in your Home folder. A "Exaile-BZR" folder [SIZE="1"](where the app gets stored)[/SIZE] and a ".exaile" folder [SIZE="1"](where your user settings go)[/SIZE].

Now this will do a BZR checkout _every_ time you launch Exaile from the icon we made here. If your on broadband this should only cause a minor delay. There's usually only minor updates after the 1st time you run it from the menu.

**[SIZE="3"]6[/SIZE].** Enjoy [Exaile]("http://www.exaile.org/")!

Also if at anytime Exaile doesnt start from the launcher run it from a terminal to help diagnose the problem. **~/Exaile-BZR/exaile** This _will_ happen. Not often but it will.

Exaile resources:
[LIST]
[*]Main site: [http://www.exaile.org/trac](http://www.exaile.org/trac)
[*]Bug reports: [http://www.exaile.org/trac/report](http://www.exaile.org/trac/report)
[*]IRC channel: #exaile on Freenode
[/LIST]

Everyone in encouraged to help and report bugs. :) I hope you like it.

---

### Post by doggie on 2007-02-24
hey thanks for how to... but, dont you think is easier by adding a line to the sources.list file :confused: ... 

```
deb http://download.tuxfamily.org/syzygy42 edgy exaile-svn
```

You need to add the key from exaile and then just install it

```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install exaile
```



I guess that the svn version and the repository version are same version...... right?? 
correct me if Im wrong...

ps: sorry for my english :lolflag:

---

### Post by MetalMusicAddict on 2007-02-24
No. Its not the same. With a repo you have to wait for someone to build the .deb.

With python apps you can just run them.

Also adding repos opens you up to things you might not want to be exposed to.

---

### Post by doggie on 2007-02-25
I think the same... You could have a lot of problems with the repos, but in this case, the repo is in the official exaile website, so they, i guess, keep it up to date

[http://www.exaile.org/trac/wiki/Releases](http://www.exaile.org/trac/wiki/Releases)

but how I said before, thanks for the how to

---

### Post by MetalMusicAddict on 2007-02-25
> **doggie said:**
> I think the same... You could have a lot of problems with the repos, but in this case, the repo is in the official exaile website, so they, i guess, keep it up to date

[http://www.exaile.org/trac/wiki/Releases](http://www.exaile.org/trac/wiki/Releases)

but how I said before, thanks for the how to

They do not maintain that repo.

---

### Post by SishGupta on 2007-02-26
Thank you for this!

---

### Post by aktiwers on 2007-02-26
Worked great, thanks!

---

### Post by MetalMusicAddict on 2007-02-27
To let you guys know, there is some current flux going on and Im having issues with SVN. I still have .2.8 installed as a back-up. ;)

---

### Post by gosh on 2007-03-13
Thanx for this HowTo.
Worked perfectly

---

### Post by dn* on 2007-06-22
Wow, this is great, thanks! The SVN repo wasn't working for me, probably because I'm AMD64 so thanks. The SVN I just got has fixed almost all of the major issues I had with the last stable release.

---

### Post by MetalMusicAddict on 2007-06-22
Thanx for the thanx. :)

---

### Post by dn* on 2007-08-29
Exaile has moved from subversion to bazaar. For those using this script, a few modifications must be made. You have to start clean, so I moved my Exaile-SVN folder to Exaile-OLD
```
mv Exaile-SVN Exaile-OLD
```

and then edited the exaile-svn command
```
sudo gedit /usr/local/bin/exaile-svn
```
change it to:
```
#!/bin/bash
cd Exaile-SVN && bzr up
~/Exaile-SVN/exaile
```

---

### Post by MetalMusicAddict on 2007-08-29
Yes thanx. I meant to make the change. Ill do it now. ;)

---

### Post by dn* on 2007-08-29
oops, got it wrong. fixed now. thanks to #exaile :)

---

### Post by dn* on 2007-09-13
x

---

### Post by olavjunior on 2007-09-30
GREAT!! Thanx alot :

---

### Post by olavjunior on 2007-10-02
bzr: ERROR: Target directory "Exaile-BZR" already exists.
&
ImportError: No module named mutagen

Exaile won't start..

---

### Post by MetalMusicAddict on 2007-10-02
> **MetalMusicAddict said:**
> This HOW-TO assumes you have all the proper things installed to run Exaile normally.

> **olavjunior said:**
> bzr: ERROR: Target directory "Exaile-BZR" already exists.
&
ImportError: No module named mutagen

Exaile won't start..

You're missing depends. Install Exaile from the repos to grab them. Then just remove the exaile package installed from the repo.You should then be fine.

---

### Post by olavjunior on 2008-04-04
This isn't cutting edge anymore, cause they're working on a brand new 0.3 version! But this will give you the latest 0.2 version, but there's not much happening with that one anymore, so no need to pull from bzr everytime you start

---

### Post by jordey24 on 2008-10-22
It didnt work :(
when i type ```
 bzr branch http://bazaar.launchpad.net/~exaile-devel/exaile/main Exaile-BZR

``` in the terminal,it gives me an error:
```
bzr: ERROR: Not a branch: "https://code.launchpad.net/".

```
What did i do wrong?
-Jordey24

---

### Post by puppy on 2008-10-22
same error here... ?

---

### Post by unc0nn3ct3d on 2008-10-26
Yep, getting the same error here..Hope to have a solution soon

Ok, so the problem is that with the above instructions the BZR updates are going into ~/exaile .

So what you want to do to start is check to see if there already is a ~/exaile dir.. If so just rename it for now and in your home directory run **bzr branch lp:exaile**

That will create the exaile dir and stick everything new in there..

you will also need to edit your /usr/local/bin/exaile-bzr file so that it reads like this

> 
#!/bin/bash
cd exaile && bzr pull
~/exaile/exaile


that should set you up for the latest updates

---

