---
title: "[SOLVED] Backing up DVD9 to DVD5"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by zalnn on 2008-08-08
Hi All,

Recently I have been trying to backup some of my DVDs to DVD-R. 

In the backup process, I want to only keep the main feature, (eng) sound track, subtitles and the original menu. Basically rip out all the extra/bonus material, sound etc. Then if the feature is still too big, compress (?) it and convert it to a DVD video image, ie; a 4.7GB ISO.

K9Copy work fine and to be honest is a pretty darn good.

However, what I am looking for is a method to use a script to automate the process, reasons being;

1) My server has the most resources and is purely command line and I would like to keep it that way.

2) Because I am going to be backing up over 100 DVDs, clicking is going to get old.

I am pretty Linux literate, but have no experience with the stuff mentioned above.

Thanks in advance for looking and any help/advice you might be able to give.

---

### Post by kpkeerthi on 2008-08-08
[xdvdshrink]("http://dvdshrink.sourceforge.net/dvdshrink.html") should get you started.

It comes with shell scripts (and even one that can do conversion in [batch mode]("http://dvdshrink.sourceforge.net/batchrip.html")) and is easily scriptable for automation.

---

### Post by mikewhatever on 2008-08-08
I'd go with dvd95 or k3b. DVDshrink is only an option if you don't mind messing with wine.

---

### Post by andrewjoy on 2008-08-08
I would also go with dvd95 had no problems with it myself works just fine.

sudo apt-get install dvd95

---

### Post by Hallvor on 2008-08-08
dvd95 for Gnome and k9copy for KDE...

---

### Post by philinux on 2008-08-08
> **Hallvor said:**
> dvd95 for Gnome and k9copy for KDE...

I'm using gnome and k9copy runs fine.

---

### Post by zalnn on 2008-08-08
> **kpkeerthi said:**
> [xdvdshrink]("http://dvdshrink.sourceforge.net/dvdshrink.html") should get you started.

It comes with shell scripts (and even one that can do conversion in [batch mode]("http://dvdshrink.sourceforge.net/batchrip.html")) and is easily scriptable for automation.

> **mikewhatever said:**
> I'd go with dvd95 or k3b. DVDshrink is only an option if you don't mind messing with wine.

I think kpkeerthi is referring to XDVDShrink; its a Perl script that ties together many different tools/utilities via a GUI front end. 


> **Hallvor said:**
> dvd95 for Gnome and k9copy for KDE...

> **philinux said:**
> I'm using gnome and k9copy runs fine.

K9Copy is what I tried out and am using right now in Gnome. It is great and does what I want, but its a GUI. I don't know how to configure it and run it via  the CLI.

What I want is to backup the main feature with the some of the sound tracks associated with it. 
The ORIGINAL menus. 
The subtitles.

k9Copy does this great, but **I want command line**!

I am sure that xDVDShrink would work. I will give it a shot this weekend and report back... I am not very familiar with Perl scripting, so its going to take me a while to figure out what xDVDShrink is doing, in order for me to reverse engineer it and write my own script. Any help on where to get started in deciphering what xDVDShrink does would be welcome.

Any experiences with **lxdvdrip**?

Thanks again guys :)

---

### Post by philinux on 2008-08-08
Looks like lxdvdrip is the candidate,

[http://openfacts.berlios.de/index-en.phtml?title=lxdvdrip](http://openfacts.berlios.de/index-en.phtml?title=lxdvdrip)

---

### Post by mc4man on 2008-08-08
> figure out what xDVDShrink is doing, in order for me to reverse engineer it and write my own script
i don't think you'll need to do that, you can just set up a config. that will work with most of your titles or run a config with some add. options.
Probably similar with the lx.... one, find a cli comm. that works with most titles and then write a little executing script that runs either app the same way every time.

Your only problem titles may be the occasional ones that have 2 separate versions or are interleaved for one reason or the other.
If subs are important you may want to ck. how either deals with them

If you really wanted to automate things you could use the launch comm. of a default choice for dvd movies to run your executing script, ie. put the movie in the drive and your exec. script will auto run. (either in a visible terminal or in the background) 
I installed gxine just to use for auto running a vobcopy script

There are also a couple of other ways to auto run the process for server setup, see here

[http://ubuntuforums.org/showthread.php?t=869865](http://ubuntuforums.org/showthread.php?t=869865)

---

### Post by Hallvor on 2008-08-09
> **philinux said:**
> I'm using gnome and k9copy runs fine.

I`ve done that myself, and k9copy did run. Not as stable as in KDE, but it did run. However, I prefer clean environments. There is no need to load those large KDE libraries to backup a DVD if you can get the job done with a native application, in my opinion.

---

### Post by starcannon on 2008-08-09
Ironically this is one of the few tasks I still recommend windows for.

anyDVD for decryption, dvdShrink to convert from 9 to 5.

There are Linux alternative, I just haven't witnessed a lot of them working on set top dvd players. Prolly some setting not being set correctly. Because of where I live, I of course have never, and would never back up a DVD.

---

### Post by Hallvor on 2008-08-09
+1.. Windows tools are regrettably better on that point. The only application that can back up some protected dvds is VLC, but not even that works on all.

---

### Post by zalnn on 2008-08-09
> **mc4man said:**
> i don't think you'll need to do that, you can just set up a config. that will work with most of your titles or run a config with some add. options.
Probably similar with the lx.... one, find a cli comm. that works with most titles and then write a little executing script that runs either app the same way every time.

Your only problem titles may be the occasional ones that have 2 separate versions or are interleaved for one reason or the other.
If subs are important you may want to ck. how either deals with them

If you really wanted to automate things you could use the launch comm. of a default choice for dvd movies to run your executing script, ie. put the movie in the drive and your exec. script will auto run. (either in a visible terminal or in the background) 
I installed gxine just to use for auto running a vobcopy script

There are also a couple of other ways to auto run the process for server setup, see here

[http://ubuntuforums.org/showthread.php?t=869865](http://ubuntuforums.org/showthread.php?t=869865)

mc4man you and and I are on the same page :) This is **EXACTLY** what I want to do.  You have answered my question of automating the process before I got to that step. Thanks :)

So, I installed xdvdshrink and it works as it is supposed to. Problem with it is that xdvdshrink removes the original menu.

I would like to keep the original menu (even though I am removing everything but the main feature, sound track and subtitles from the disk)

I read [here]("http://gentoo-wiki.com/HOWTO_Backup_a_DVD#lxdvdrip") that lxdvdshrink can do exactly what I want.

My problem now is that I am not sure **how to install lxdvdrip**.

Any help is, as always greatly appreciated. Please bare with me guys, I feel like I am SO close and can't bare to loose at this point.

---

### Post by mc4man on 2008-08-09
Your going to have to compile it and maybe another package. Look in the extracted source for doc-pak and carefully read the read me's

There are 2 .debs available from christan marillat's debian repo. the earlier ver. will install into hardy straight up. The newest ver. requires a new dvdnav4. I installed the newer dvdnav and so far no issues. (actually like it, replaces the need for dvdnav4-ifo. (playback of x-protect titles

install deps of earlier ver.
```
Package: lxdvdrip
Version: 1.62-0.0
Section: otherosfs
Priority: optional
Architecture: i386
Depends: libc6 (>= 2.3.6-6), libdvdnav4 (>= 0.1.10), libdvdread3 (>= 0.9.6), dvdauthor, mplayer, dvd+rw-tools, dvdbackup, vamps, dvdwizard
```

of latest
```
Package: lxdvdrip
Version: 1.71-0.0
Architecture: i386
Bugs: mailto:marillat@debian.org
Maintainer: Christian Marillat <marillat@debian.org>
Installed-Size: 468
Depends: libc6 (>= 2.7-1), libdvdnav4 (>= 4.1.2), libdvdread3 (>= 0.9.7), dvdauthor, mplayer, dvd+rw-tools, dvdbackup, vamps, dvdwizard, buffer
```

If you want to try either .deb then first make sure mplayer is installed and then go here and install dvdwizard (other packages will be installed) I choose the later ver.

[http://www.repositorios.pr.gov.br/marillat/pool/main/d/dvdwizard/](http://www.repositorios.pr.gov.br/marillat/pool/main/d/dvdwizard/)

The lxdvdrip .deps are here

[http://www.repositorios.pr.gov.br/marillat/pool/main/l/lxdvdrip/](http://www.repositorios.pr.gov.br/marillat/pool/main/l/lxdvdrip/)

For ver 1.62.. just go ahead and d. click and let gdebi handle it.

For ver. 1.71.. first go into synaptic and ck. if _libdvdnav4-dev_ is installed, if so remove. (_leave libdvdnav4)_
Then go here and install libdvdnav4 (again just let gdebi handle - _don't remove current libdvdnav_, it will be removed for you without losing your movie players)

[http://packages.debian.org/lenny/libdvdnav4](http://packages.debian.org/lenny/libdvdnav4)

after that installs then go ahead and install lxdvdrip 1.71...

Note; you should have medibuntu as a repo source before starting.
I have a built ver. of mplayer (has it's own ver. of mencoder) so I'm not sure if your using the repo ver. if mencoder has to be installed separately. (ck. around or just install it)

Do not try this to install the latest ver. to Gutsy, the libc6 needed is not compatible and if you happen to force an upgrade of libc6 then you might as well break out the live cd.

Don't have time to ck. how the app works or to really say if you should compile or use the .debs, just giving you some options. (though i'm happy with the new dvdnav4)

side note
here's ex. of title that can't be played, ripped with normal dvdnav4. (previously required patched dvdnav - dvdnav4-ifo)
> doug@doug-desktop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using [COLOR="Red"]dvdnav version 4.1.2[/COLOR] from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: HAIRSPRAY_WS
libdvdnav: DVD Serial Number: 371bb6dc
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/doug/.dvdnav/HAIRSPRAY_WS.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
[00000336] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000

Do note that ripping such titles as above isn't possible in linux (exception is using DVD Fab HD Decrypter in wine) though playback is with patched or new dvdnav4

edit: forgot to mention i ran across this (mixed up the 2 names, as did you in previous post). It just runs off of some scripts, one goes to /usr/bin. the other is in a folder you put in opt. The one in opt is a perl script you modify to suit (run from terminal and you'll see, starts requesting mods at line 29 ,ect. ) How you make proper entries is well above me.

[http://sourceforge.net/project/showfiles.php?group_id=172070](http://sourceforge.net/project/showfiles.php?group_id=172070)
[http://freshmeat.net/projects/lxdvdshrink/](http://freshmeat.net/projects/lxdvdshrink/)

---

### Post by zalnn on 2008-08-13
Wow, I didn't even realize that I made that typo with lxdvdshrink and lxdvdrip

So... We have 
lxdvdrip
lxdvdshrink
xdvdshrink
All for ripping DVDs in Linux.

Anyway... I successfully installed lxdvdrip 1.71. It worked as expected and I am happy!
Thank you **mc4man **for your help!

I might give lxdvdshrink a shot. I'll report back, if I ever get around to installing and ripping with it.

---

