---
title: "Automatix: Automated Graphical Installer and Tweaker (look here first!)"
date: 2005-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-21
Automatix is a graphical interface for automating the installation of the most commonly requested applications in Debian based linux operating systems.

[Automatix website]("http://www.getautomatix.com")

[B]Automatix 386 version works on both Breezy and Dapper.
Automatix amd64 and ppc versions work only on Dapper.[/B]

[Automatix wiki]("http://www.getautomatix.com/wiki/index.php?title=Main_Page")
[URL="http://www.getautomatix.com/wiki/index.php?title=Software_and_Tweaks"]
Softwares and tweaks installed by Automatix [/URL]

[Automatix Installation (including an automatic installer for automatix)]("http://www.getautomatix.com/wiki/index.php?title=Installation")
[URL="http://www.getautomatix.com/wiki/index.php?title=FAQ"]
Automatix FAQ[/URL]
[URL="http://www.getautomatix.com/wiki/index.php?title=The_Team"]
Automatix Team[/URL]
[URL="http://www.getautomatix.com/wiki/index.php?title=Main_Page#Versions_and_Changelog"]
Automatix Changelog[/URL]
[URL="http://www.getautomatix.com/wiki/index.php?title=Uninstalling_Software"]
Removal of softwares installed by Automatix[/URL]

[Automatix Support]("http://ubuntuforums.org/showthread.php?t=203340")
[URL="http://ubuntuforums.org/showthread.php?t=225967"]
Automatix Bleeder[/URL]

[Automatix Wish List]("http://ubuntuforums.org/showthread.php?t=185603")

---

### Post by fut21 on 2005-10-23
Is it balckdown java or sun java i installe with automatix ?

---

### Post by ykpaiha on 2005-10-23
thanks, looks like a very good idea but, 
sorry I do not find any link to your automatix ?
where  is it please

---

### Post by arnieboy on 2005-10-23
[QUOTE=fut21]Is it balckdown java or sun java i installe with automatix ?[/QUOTE]
Sun's Java 1.5

---

### Post by arnieboy on 2005-10-23
[QUOTE=ykpaiha]thanks, looks like a very good idea but, 
sorry I do not find any link to your automatix ?
where  is it please[/QUOTE]
look just above the "quote" button on the first post (bottom right corner) on [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by wiseguy on 2005-10-23
Nice work!

I noticed keyes has included the w32codecs. Wondering why the legalities are not an issue with Easy Ubuntu and they are with Automatix?

---

### Post by bored2k on 2005-10-23
> 12) Installs Mplayer and mplayerplug-in version 3.05 for Firefox
Why the old mozilla mplayer plugin? 3.11 rocks.
[http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb](http://www.ahacic.5gigs.com/ubuntu/mplayerplug-in_3.11-1_i386.deb)

---

### Post by wiseguy on 2005-10-23
Gotcha. :D

Thanks.

---

### Post by Brando569 on 2005-10-25
one suggestion to make it more automatic, could you remove the "app here"installed successfully notification? i have a slow connection here at college and i set this up assuming it would go through everything sequentially so i left for two or so hours and came back it was at the end of the first thing! :( just a suggestion...

---

### Post by dudinatrix on 2005-10-25
Ok, this is a n00b question....

When starting for the first time, it prompts you to hit OK if you "have not set your root password yet".  Is the root password different from using sudo?  Not sure to hit OK or Cancel.

---

### Post by arnieboy on 2005-10-25
[QUOTE=dudinatrix]Ok, this is a n00b question....

When starting for the first time, it prompts you to hit OK if you "have not set your root password yet".  Is the root password different from using sudo?  Not sure to hit OK or Cancel.[/QUOTE]
yes root password is different(which u have to set with automatix). ur sudo password is your user password.

---

### Post by herot on 2005-10-26
arnieboy, how can i tell what prelinking is doing?? like as its actually doing it
does it get put inside a log file somewhere?

---

### Post by arnieboy on 2005-10-26
[QUOTE=herot]arnieboy, how can i tell what prelinking is doing?? like as its actually doing it
does it get put inside a log file somewhere?[/QUOTE]
[http://www.crast.us/james/articles/prelink.php](http://www.crast.us/james/articles/prelink.php)

---

### Post by funkenstein on 2005-10-27
Hi there, I posted this in [_here_](http://ubuntuforums.org/showthread.php?t=66563&page=41) before I saw this thread, so here goes again.... sorry for the repost, but I really want to get opera running on my 64bit breezy:
```

me@ubuntu:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.50-20050916.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
``` 
What to do now??? :'(

---

### Post by Tm_T on 2005-10-27
This might sound a bit stupid but... how you prevent that not break system if it does install anything using --force-all flag?! I've heard several complains from newbies when automatix break their X or something else as crucial.

I'm just wondering...

---

### Post by arnieboy on 2005-10-27
[QUOTE=fut21]Is it balckdown java or sun java i installe with automatix ?[/QUOTE]
the latest version of automatix (2.13) has sun java 1.5

---

### Post by Nano on 2005-10-28
It works great, indeed!
However, this time I also installed the midi support and I think it's slowing down the performances of my laptop.

What's the best way to uninstall it?

---

### Post by arnieboy on 2005-10-28
[QUOTE=Nano]It works great, indeed!
However, this time I also installed the midi support and I think it's slowing down the performances of my laptop.

What's the best way to uninstall it?[/QUOTE]
read "autoscript" and undo whatever it does for adding midi capability.
In a later version, I will automate "undo" for all options.

---

### Post by kakashi on 2005-10-29
can i get the hoaray version please.
i really don't want to move to breezy cuz when i did it gave me a lot of problems

---

### Post by arnieboy on 2005-10-29
[QUOTE=kakashi]can i get the hoaray version please.
i really don't want to move to breezy cuz when i did it gave me a lot of problems[/QUOTE]
sorry but I have to rewrite the whole thing for hoary.. and thats quite a bit of work.. if I do get time however, I will try and do it for u.

---

### Post by kakashi on 2005-10-29
[QUOTE=arnieboy]sorry but I have to rewrite the whole thing for hoary.. and thats quite a bit of work.. if I do get time however, I will try and do it for u.[/QUOTE]


is this written in python. if so please tell what changes need to be made and i'll make them myself. 
also i see there was a hoaray version. can i have a copy of that.

ok don't mind me. i just looked at the code and it seems to be in bash. 
i can still edit it a bit.

---

### Post by kelean on 2005-10-30
Arnieboy thank you very much.  Your Automatix program is very cool. You have saved me a lot of time setting up my new breezy install.  Java has never been so easy to install.  The only problem I had was that annoying error popup for the motif lib-3 missing.  I just check don't show message again and its all good.

Thanks again, Kelean

---

### Post by arnieboy on 2005-10-30
[QUOTE=kakashi]is this written in python. if so please tell what changes need to be made and i'll make them myself. 
also i see there was a hoaray version. can i have a copy of that.

ok don't mind me. i just looked at the code and it seems to be in bash. 
i can still edit it a bit.[/QUOTE]
its a bash script. I myself dont have a copy of the hoary version.. I think its on one of the posts in the automatix thread.

---

### Post by germex on 2005-11-01
Thanks, pal. Excellent. I already had installed most of the codecs, AMule and a few other things, but I was having problems watching DVDs. After I ran Automatix I tried the DVD and works great i Guess I was missing a codecs or had a wrong one. I wanted to install gnomebaker and now i have it and works great. I am relatively new to linux, i tried Red Hat a few years ago. And a few weeks ago I installed Breezy. 
Thanks for the help, really appreciated.

---

### Post by arnieboy on 2005-11-03
**UPDATE (11/03/2005 07:22 PM ET): [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") updated to version 3.0 Please redownload and reinstall**
Latest version (**3.0**) has the following NEW features:
[B]a) wine repositories added. now u get the latest version of wine from the wine headquarters.
b) ndisgtk added (WiFI configurator Graphical user interface)[/B]

---

### Post by arnieboy on 2005-11-03
If someone could make a debian package out of Automatix version  3.0, it would be awesome!

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=arnieboy]**UPDATE (11/03/2005 07:22 PM ET): [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") updated to version 3.0 Please redownload and reinstall**
Latest version (**3.0**) has the following NEW features:
[B]a) wine repositories added. now u get the latest version of wine from the wine headquarters.
b) ndisgtk added (WiFI configurator Graphical user interface)[/B][/QUOTE]


This warrents a change in the title of the thread.

---

### Post by BLTicklemonster on 2005-11-05
Hey arnieboy, can't you make it where it either only adds the repositories to what I already have, or have it replace the repositories I had once it's done?

---

### Post by ishtvan222 on 2005-11-05
Very nice program, I think it would be a good idea to seperate the flash plugin from the java tho. I have Java SDK installed and when i select the plugins it also installs j2re. Just my opinion tho.

Thanks for making such a nice script

---

### Post by arnieboy on 2005-11-05
[QUOTE=ishtvan222]Very nice program, I think it would be a good idea to seperate the flash plugin from the java tho. I have Java SDK installed and when i select the plugins it also installs j2re. Just my opinion tho.

Thanks for making such a nice script[/QUOTE]
u might have java SDK installed, but most people wudnt have it. and java and its plugin is a core part of FF plugins.

---

### Post by kakashi on 2005-11-06
[QUOTE=BLTicklemonster]Hey arnieboy, can't you make it where it either only adds the repositories to what I already have, or have it replace the repositories I had once it's done?[/QUOTE]


you could do some of the work your self. 
before runing the script. 
```
 
cp /etc/apt/sources.list $HOME/sources.list

```
later you can do this. 
```

mv $HOME/sources.list /etc/apt/

```

---

### Post by bugmenot on 2005-11-06
Could you add the Ooo2 thumbnailer?

[http://www.ubuntuforums.org/showthread.php?t=76566](http://www.ubuntuforums.org/showthread.php?t=76566)

---

### Post by poofyhairguy on 2005-11-07
[QUOTE=bugmenot]Could you add the Ooo2 thumbnailer?

[http://www.ubuntuforums.org/showthread.php?t=76566](http://www.ubuntuforums.org/showthread.php?t=76566)[/QUOTE]

That is an awesome hack.

---

### Post by BLTicklemonster on 2005-11-07
[QUOTE=kakashi]you could do some of the work your self. 
before runing the script. 
```
 
cp /etc/apt/sources.list $HOME/sources.list

```
later you can do this. 
```

mv $HOME/sources.list /etc/apt/

```[/QUOTE]
(I meant make IT do it for ME... like automating... like ... you know automatix)

---

### Post by syphix on 2005-11-07
Am I the only one who can't get Acrobat Reader to install on this?  It stalls on "Installing Acrobat Reader and plugin required for Firefox", never getting installed.

---

### Post by arnieboy on 2005-11-07
[QUOTE=syphix]Am I the only one who can't get Acrobat Reader to install on this?  It stalls on "Installing Acrobat Reader and plugin required for Firefox", never getting installed.[/QUOTE]
it will get installed if u give it time. acrobat reader is a 15 MB download. if ur net speed sucks.. therez nuthing much automatix can do abt it.

---

### Post by syphix on 2005-11-07
Hadn't noticed the net activity.  Thanks, I'll give it mre time.

---

### Post by Navyblue on 2005-11-07
I am trying to install MIDI support, at the end of the installation I get this message:

cat: /usr/local/automatix/conf/bashadd: Permission denied
cat: /usr/local/automatix/conf/bashadd: Permission denied

MIDI sound is still not coming out.

Any clue?

---

### Post by silentQ on 2005-11-07
hey guys... just installed automatix...
now when i load azureus   it says failed to load update plugin, than another notice pops up saying i'm using old javal plugin says i need java 5.0 or above  same with bitcomet :confused:

---

### Post by Navyblue on 2005-11-07
After installing the fonts, my openoffice2 failes to start now. But I am not sure if it is automatix related. But apeart from automatix I did nothing to my system. The error message is:

```

I18N: X Window System doesn't support locale "en_GB"
I18N: X Window System doesn't support locale "en_US"
I18N: X Window System doesn't support locale "C"
Qt: Locales not supported on X server
*** glibc detected *** free(): invalid next size (fast): 0x080def10 ***
KCrash: Application 'soffice.bin.real' crashing...
/usr/lib/openoffice2/program/soffice: line 224: 10397 Alarm clock             "$sd_prog/$sd_binary" "$@"

```

I have used dpkg-reconfigure locales to enable the locale mentioned but the outcome is the same.

---

### Post by pioni on 2005-11-08
Does this support Quicktime? I installed Easy Ubuntu a while ago and at least it doesn't have Quicktime support, or at least it didn't allow me to view Quicktime trailers at apple.com/trailers (Totem said it couldn't find suitable plugin).

---

### Post by arnieboy on 2005-11-08
[QUOTE=pioni]Does this support Quicktime? I installed Easy Ubuntu a while ago and at least it doesn't have Quicktime support, or at least it didn't allow me to view Quicktime trailers at apple.com/trailers (Totem said it couldn't find suitable plugin).[/QUOTE]
check out version 3.1 of automatix.
install mplayer plugin and AUD-DVD codecs
that should solve ur problem.

---

### Post by Navyblue on 2005-11-09
[QUOTE=Navyblue]I am trying to install MIDI support, at the end of the installation I get this message:

cat: /usr/local/automatix/conf/bashadd: Permission denied
cat: /usr/local/automatix/conf/bashadd: Permission denied

MIDI sound is still not coming out.

Any clue?[/QUOTE]

Can someone please help me with this?

---

### Post by Bonarges on 2005-11-09
Oh.. My... God...

If this thing does half of what it says it does, you may have my first born (if you exercise the option before I find a woman to impregnate).  This is amazing.  I'm a total linux noob and just want to get this up to a running level so i can tinker and learn how to really do it.

Thanks for this.

CM

---

### Post by kakashi on 2005-11-09
[QUOTE=Bonarges]Oh.. My... God...

If this thing does half of what it says it does, you may have my first born (if you exercise the option before I find a woman to impregnate).  This is amazing.  I'm a total linux noob and just want to get this up to a running level so i can tinker and learn how to really do it.

Thanks for this.

CM[/QUOTE]

wow this guy must really like  Automatix.
also if you want to learn then don't use automatix.
if you want a system up and running in no time then automatix is for you.

---

### Post by arnieboy on 2005-11-09
[QUOTE=Navyblue]I am trying to install MIDI support, at the end of the installation I get this message:

cat: /usr/local/automatix/conf/bashadd: Permission denied
cat: /usr/local/automatix/conf/bashadd: Permission denied

MIDI sound is still not coming out.

Any clue?[/QUOTE]
yes I will help u out on this and fix this midi bug in the next release of automatix. herez what u have to do:
```
gedit .bashrc
```
add the following lines:
> export ALSA_OUTPUT_PORTS="128:0"
export SCUMMVM_PORT=128:0

```
gedit .gnomerc
```
add the following lines:
> export ALSA_OUTPUT_PORTS="128:0"
export SCUMMVM_PORT=128:0

that shd get u all set. test by running the following:
```
timidity file.mid
```
where file.mid will be replaced by the name of the mid file u are trying to play.

---

### Post by trash on 2005-11-09
Just wondering if a comic book reader can be added for reading .cbr files...

[http://ubuntuforums.org/showthread.php?t=81180&highlight=.cbr](http://ubuntuforums.org/showthread.php?t=81180&highlight=.cbr)
[http://www.jcoppens.com/soft/cbrpager/index.en.php](http://www.jcoppens.com/soft/cbrpager/index.en.php)

---

### Post by Navyblue on 2005-11-09
[QUOTE=arnieboy]yes I will help u out on this and fix this midi bug in the next release of automatix. herez what u have to do:
```
gedit .bashrc
```
add the following lines:

```
gedit .gnomerc
```
add the following lines:


that shd get u all set. test by running the following:
```
timidity file.mid
```
where file.mid will be replaced by the name of the mid file u are trying to play.[/QUOTE]


Thanks a heap, MIDI works now. :)

---

### Post by arnieboy on 2005-11-09
[QUOTE=Navyblue]Thanks a heap, MIDI works now. :)[/QUOTE]
u are welcome. I have also released a bug fix version of automatix (version 3.1.1) in which midi will now work out of the box :)

---

### Post by silentQ on 2005-11-10
hey i posted before, didnt get an answer 
heres the original post

"hey guys... just installed automatix...
now when i load azureus it says failed to load update plugin, than another notice pops up saying i'm using old javal plugin says i need java 5.0 or above same with bitcomet "

---

### Post by Mr_J_ on 2005-11-10
This should be included with Ubuntu.
It's great!
My instalation before I couldn't get videos to play in firefox, and now on this one it works like normal!

This is great!

---

### Post by arnieboy on 2005-11-10
[QUOTE=silentQ]hey i posted before, didnt get an answer 
heres the original post

"hey guys... just installed automatix...
now when i load azureus it says failed to load update plugin, than another notice pops up saying i'm using old javal plugin says i need java 5.0 or above same with bitcomet "[/QUOTE]
the answer is in this post on the other thread:
[http://ubuntuforums.org/showpost.php?p=478713&postcount=636](http://ubuntuforums.org/showpost.php?p=478713&postcount=636)
hope this helps.

---

### Post by silentQ on 2005-11-10
i'll try it now thanx :)

---

### Post by neymac on 2005-11-12
When I used Automatix, my sources.list were changed to a new one.

Is there any option to replace my old one back or must I rename the one saved as sources.list_backup_200511121147 (date and time it changed)?

---

### Post by BLTicklemonster on 2005-11-12
[QUOTE=neymac]When I used Automatix, my sources.list were changed to a new one.

Is there any option to replace my old one back or must I rename the one saved as sources.list_backup_200511121147 (date and time it changed)?[/QUOTE]
That's what I meant when I posted about it automatically putting things back. I don't understand why repository settings are not able to just keep adding and adding and why you should comment out some when using new ones, and vice versa.

Hint: when you finally get your originals back, save them in /home/you/ as repository original, then each others you get, save them by a name you will remember. I'm going to do this one of these days.

I think, though, that you can go to synaptic, and then reset your repositories in there the way you would have set up extra reps originally. Settings>repositories> make sure they are all checked, and press okay. Maybe I'm wrong, but I think I did that once, and it set me back to normal. (like I can be normal, riiiight)

---

### Post by arnieboy on 2005-11-12
[QUOTE=neymac]When I used Automatix, my sources.list were changed to a new one.

Is there any option to replace my old one back or must I rename the one saved as sources.list_backup_200511121147 (date and time it changed)?[/QUOTE]
its simple enough.. delete your existing sources.list and rename the backup file as sources.list in /etc/apt/ (that will replace the one which automatix creates).

---

### Post by neymac on 2005-11-12
[QUOTE=arnieboy]its simple enough.. delete your existing sources.list and rename the backup file as sources.list in /etc/apt/ (that will replace the one which automatix creates).[/QUOTE]

Thank's, Arnieboy. I did it.

By the way, is there any possibility of before you leave the Automatix it renames both files, like it did at the begining, restoring the previous sources.list? 
(It renames /etc/apt/sources.list as backup and created a new one)

---

### Post by jrincon87 on 2005-11-12
I installed, among other things, the MIDI support and now I have no sound at all.
Any clue?

---

### Post by arnieboy on 2005-11-12
[QUOTE=jrincon87]I installed, among other things, the MIDI support and now I have no sound at all.
Any clue?[/QUOTE]
when u say no sound at all.. u need to gimme some more info.. 
do this from terminal:
```
mplayer <filename>
```
where filename is a mp3 file.
paste the terminal out put here.

---

### Post by jrincon87 on 2005-11-13
When I say I have no sound at all, I mean it. I can't hear any system sound, I try to play something with XMMS and I don't hear anything, I prove it with another output (like OSS), and nothing happens. The XMMS seems to be playing the file, but I don't hear anything.

---

### Post by arnieboy on 2005-11-13
[QUOTE=jrincon87]When I say I have no sound at all, I mean it. I can't hear any system sound, I try to play something with XMMS and I don't hear anything, I prove it with another output (like OSS), and nothing happens. The XMMS seems to be playing the file, but I don't hear anything.[/QUOTE]
u probably need to check ur volume settings (or whether ur speakers are properly attached to the sound output of your computer).. if xmms is playing a file that means there shdnt be anything wrong with the sound server.

---

### Post by arnieboy on 2005-11-14
[B] Automatix Version 3.3 released!
Please redownload and reinstall.[/B]

Latest version (**3.3**) has the following new update:
[B]a)Done away with the plf repos (They freaked me out a couple of days back) and replaced them with the seveas repos.
The seveas repos rock! They have all that the plf repos have and much more. They backport quite a few apps from the dapper repos to the breezy repos! That means u will get periodical updates to quite a few of your favorite apps with backports!
b) Added a separate section for sun's java 1.5 JRE and SDK!
c) Added freenx (and a howto on how to configure it)
d) Options 29 to 35 require manual intervention and clicking and hence have been taken to the end. The first 28 options install without any user input.[/B]

---

### Post by jrincon87 on 2005-11-14
> u probably need to check ur volume settings (or whether ur speakers are properly attached to the sound output of your computer).. if xmms is playing a file that means there shdnt be anything wrong with the sound server.

Sorry, this is what happened. I have two sound cards. It seems that during the installation of the Midi support, the default output has been changed. Now, how do I set Ubuntu to output sound through a determinate sound card? (The sound card I want the output is hw:1,0).
Thanks.

---

### Post by tig4 on 2005-11-15
Where's the link?

---

### Post by arnieboy on 2005-11-15
**Automatix is back! Sorry about the downtime...**

[B]Automatix updated to version 3.3.1 Please redownload and reinstall.

Latest version (3.3.1) has the following new bugfix:
a)Minor bugfix in java script and severe juggling with seveas and plf repos to get everything right.everything seems to be fine now but I still have my fingers crossed till I get confirmation from users.[/B]

---

### Post by Zhukov on 2005-11-15
---

---

### Post by arnieboy on 2005-11-15
[QUOTE=Zhukov]Hello ArnieBoy!
Dunno if you remember me (i made a automatix-based app, IT oriented, with ns2, jsdk and so on), and i was wondering if you want to merge my progress with automatix (the DEIUCbuntu online is NOT the new version). I could also get  you the host i was about to receive for my project. What do you think?[/QUOTE]
I think u need to elaborate more on what u mean by "upgrading to OO2 made my laptop unusable". Thats a tall claim and u better support it with some good arguments and data.

---

### Post by Zhukov on 2005-11-15
Easy! Dont take it so deep! I was just saying what happened to me! I upgrade to 002 using automatix and shutdown, all went fine (i only did that). When i rebooted, i opened a ppt using oo2 and gnome-panel crashed and kept on crashing ever since! Since the only thing i did was run automatix and install oo2 i was just trying to see if someone else experienced the same problems! geez...

---

### Post by arnieboy on 2005-11-15
[QUOTE=Zhukov]Easy! Dont take it so deep! I was just saying what happened to me! I upgrade to 002 using automatix and shutdown, all went fine (i only did that). When i rebooted, i opened a ppt using oo2 and gnome-panel crashed and kept on crashing ever since! Since the only thing i did was run automatix and install oo2 i was just trying to see if someone else experienced the same problems! geez...[/QUOTE]
u are the one who needs to take it easy buddy!
there is no way automatix affected anything in the gnome panel (it did not even install an applet). u probably screwed it up in some other way which u dont have the faintest idea of and are merrily attaching the blame to automatix which I dont quite appreciate. "making my laptop unusable" is a very strong statement and it expresses a lot of disdain if u arent already aware of it. this is the last post of yours I am replying to. The last thing I am going on to here is a trollish flame war. 
In future try to avoid making sweeping statements if u dont want to earn the disapproval of the members of this community who give a lot of time and effort in order to make the lives of millions of dummies easier.

---

### Post by Zhukov on 2005-11-15
Nobody wants a flame war and please do not see none of my posts as an attempt to start one! Automatix is great, no doubt! And since you say there is no chance automatix screwed my gnome-panel i do believe in you and my post was edited (you can check it). I started my "claim" saying "maybe it just me". I had no intention of insult your work or something similar! Everyone is gratefull for your work. Maybe my words were harsh, and if they were i apologize. I was merely trying to help.

---

### Post by souled on 2005-11-15
How can I remove the Debian Menu? A suggestion for Automatix - maybe there can be a uninstall function to uninstall previously installed items by Automatix.

---

### Post by arnieboy on 2005-11-15
[QUOTE=souled]How can I remove the Debian Menu? A suggestion for Automatix - maybe there can be a uninstall function to uninstall previously installed items by Automatix.[/QUOTE]
```
sudo apt-get remove menu menu-xdg pdmenu
killall gnome-panel
```
I dont like the idea of automating removal of software.. its something every user shd do manually... its justmy own philosophy.
I am planning to start a thread in the automatix forum on how to remove all the options that automatix installs. that shd help.

---

### Post by souled on 2005-11-15
[QUOTE=arnieboy]```
sudo apt-get remove menu menu-xdg pdmenu
killall gnome-panel
```
I dont like the idea of automating removal of software.. its something every user shd do manually... its justmy own philosophy.
I am planning to start a thread in the automatix forum on how to remove all the options that automatix installs. that shd help.[/QUOTE]

I see... That idea would be very helpful. I'm trying out the newest version, and when the repos were updating or whatever.... it got stuck at 99% said it was downloading headers. In synaptic, I hit reload... and it's pretty much frozen at Download 34 of 35. Is there something wrong with one of the repos?

Edit: After I hit cancel in Synaptic I got a message saying it could not download all of the repository indexes. And these repos listed:
```
http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg: Connection failed
http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release
```

---

### Post by arnieboy on 2005-11-15
[QUOTE=souled]I see... That idea would be very helpful. I'm trying out the newest version, and when the repos were updating or whatever.... it got stuck at 99% said it was downloading headers. In synaptic, I hit reload... and it's pretty much frozen at Download 34 of 35. Is there something wrong with one of the repos?[/QUOTE]
u shd never run automatix and synaptic simultaneously. repos can be slow at times. u shd be a little patient.. if they dont respond for 2minutes or so, cancel and try again.

---

### Post by souled on 2005-11-15
What I meant was I canceled Automatix then I opened up Synaptic. Sorry for the confusion.

---

### Post by arnieboy on 2005-11-15
[QUOTE=souled]What I meant was I canceled Automatix then I opened up Synaptic. Sorry for the confusion.[/QUOTE]
np. the seveas repos seem to be down at the moment. I did an **apt-get update** myself to confirm. wait awhile and try later.

---

### Post by phanboy_iv on 2005-11-15
Geat idea, arnieboy. Fills Ubuntu's cracks.
Every thing worked fine except now flash animations won't play or play very slowly in Firefox. I tried uninstalling all the flash packages with synaptic, deleting the "pluginreg.dat" files, and reinstalling the flash plugins, but the problem remains.

Great tool, though. Keep at it.

---

### Post by lameiro on 2005-11-15
I am installing it and I already loving it!
Great!

[http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl)

I saw some problems with it but now I think the server is up again...
and the webpage is also up:)

---

### Post by arnieboy on 2005-11-15
[QUOTE=phanboy_iv]Geat idea, arnieboy. Fills Ubuntu's cracks.
Every thing worked fine except now flash animations won't play or play very slowly in Firefox. I tried uninstalling all the flash packages with synaptic, deleting the "pluginreg.dat" files, and reinstalling the flash plugins, but the problem remains.

Great tool, though. Keep at it.[/QUOTE]
flash on linux has a gazillion problems.
try this thread and see if it works for u or not:
[http://ubuntuforums.org/showthread.php?t=89827](http://ubuntuforums.org/showthread.php?t=89827)

---

### Post by xavierh on 2005-11-16
do I need to set additional repositories in my sources.lst in order for the script to work?

---

### Post by arnieboy on 2005-11-16
Automatix 3.4 is pretty much a stable and final version for the time being. I will not be adding any new functionality to automatix in the near future (of course firefox 1.5 final version and gaim 2.0 being exceptions). I will however be releasing bugfix versions if and when needed. Hope u all enjoy automatix and ubuntu as such. :)
-Arnie

---

### Post by cstudent on 2005-11-16
[QUOTE=arnieboy]Automatix 3.4 is pretty much a stable and final version for the time being. I will not be adding any new functionality to automatix in the near future (of course firefox 1.5 final version and gaim 2.0 being exceptions). I will however be releasing bugfix versions if and when needed. Hope u all enjoy automatix and ubuntu as such. :)
-Arnie[/QUOTE]

bout time you took a break

---

### Post by arnieboy on 2005-11-17
**Automatix updated to version 3.4.2 because of repository issues.. please download and reinstall.**

---

### Post by h0bbe on 2005-11-19
Automatix removed Splashy from my system, why?

---

### Post by h0bbe on 2005-11-19
I noticed another thing after a reboot. Instead of the standard sound when the login-screen appears I hear a beep. The beep occurs once again when I start Firefox (I guess). I had none of this before I ran Automatix :confused:

Hope anyone can help me!

---

### Post by arnieboy on 2005-11-19
[QUOTE=h0bbe]Automatix removed Splashy from my system, why?[/QUOTE]
if u are running breezy.. it doesnt have splashy.. it uses usplash. and automatix does nothing to remove that.

---

### Post by arnieboy on 2005-11-19
[QUOTE=h0bbe]I noticed another thing after a reboot. Instead of the standard sound when the login-screen appears I hear a beep. The beep occurs once again when I start Firefox (I guess). I had none of this before I ran Automatix :confused:

Hope anyone can help me![/QUOTE]
the sound server probably got tunred off.. but even that automatix did not do.
go to system -->preferences--> sound and make sure u have "enable sound server at startup" and "enable sound for events" checked.

---

### Post by bfonseca on 2005-11-19
> **arnieboy]**_Introduction_:**
This is a graphical interface for installation of a lot of apps on **UBUNTU BREEZY (DOES NOT WORK ON Warty, Hoary or Dapper)** and for tweaking a few things to get your Ubuntu box up and working in full throttle in the quickest possible timespan.

**_Features_:**
**a)** Shoots up gnome-terminal for almost all downloads (giving u a good idea about the status of your download ,etc)
**b)** deletes all downloaded files (except those downloaded by apt-get) automatically after installation.
**c)** automatix does not overwrite anything without making a date_and_time_based backup.
**d)** When u install a new version of automatix, it automatically uninstalls the last version.

**_Capabilities_:**
1) Installs multimedia codecs
2) Installs all Firefox plugins (java, flash, etc) (except Adobe reader and mplayer)
3) Installs RAR, ACE and UNRAR archive support
4) Installs skype
5) Installs Acrobat reader 7 and firefox plugin for the same.
6) Installs Gnomebaker (CD/DVD burning s/w for GNOME)
7) Installs gftp (FTP client for GNOME with ssh capability)
8) Installs DC++ , amule and Limewire (file sharing progs)
9) Installs multimedia editors (Audacity (audio), Kino (video), EasyTag (ID3))
10) Installs DVD (dvdrip) ripper 
11) Installs Mplayer and mplayerplug-in version 3.05 for Firefox
12) Installs totem-xine, VLC and Beep Media Player (with docklet)
13) Installs Opera Browser
14) Installs Debian Menu (shows all installed applications) ([COLOR="Blue"]**this kills and restarts your gnome-panel without warning u!**[/COLOR])
15) Installs Bittornado and **Azureus** (Bittorrent clients)
16) Installs Avidemux (Video editing tool)
17) Enables Numlock on (turns numlock on Gnome startup)
18) Installs Programming Tools (Anjuta (C/C++ IDE), Bluefish (HTML editor) and Screem (Web Development Env.))
19) GnomePPP (Graphical Dial up connection tool) 
20) Installs MS true type fonts 
21) Configures ctrl-alt-del to start gnome-system-monitor (*aka* windows)
22) Installs Streamripper and Streamtuner
23) Installs NON-FREE audio and dvd codecs
24) Installs ndisgtk (WiFi configurator Graphical user interface) 
25) Upgrades Open Office to 2.0 (final version), installs openoffice clipart and installs OO2 thumbnailer. (**no support for AMD64 and ppc packages**) 
26) Adds 3 nautilus scripts (open any file with gedit as root said:**
> *[/COLOR]) Installs firestarter (GNOME firewall frontend) and adds firestarter to GNOME startup
30[COLOR="Red"]*[/COLOR]) installs gdesklets (GNOME eyecandy) and adds gdesklets to GNOME startup
31[COLOR="Red"]*[/COLOR]) Gamepads (Makes USB gamepads work)
32[COLOR="Red"]*[/COLOR]) Turns DMA ON on Intel and AMD machines **(needs a restart)**
33[COLOR="Red"]*[/COLOR]) NVIDIA cards (Detects Nvidia cards and installs drivers) **(Needs a restart)**
34[COLOR="Red"]*[/COLOR]) Adds midi capability to your Ubuntu box ** (test by playing a midi file with timidity or pmidi from terminal)**

[COLOR="Red"]*[/COLOR] --> [COLOR="Blue"]**These options require manual intervention and clicking. Please standby!**[/COLOR]

**_Where to find it?_**
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
thanks arnieboy for Automatix. I installed it and it fixed alot of problems. I have recommended this to a few friends aswell.
Brian

---

### Post by h0bbe on 2005-11-20
It was Splashy I had, I installed it. And I also saw Automatix say "removing splashy" but I don't want to argue with you. Both the sound options were checked but I still have the beep and the only thing I've done is to run Automatix. Maybe I should have mentioned that I'm running Ubuntu on a laptop.

I just wanted to tell you what happened to me when I ran Automatix arnieboy, not blame you, apart from those things I think it's great!

---

### Post by ameerirshad on 2005-11-20
1,2,3 testing, running and enjoying it! Very nice tool, easy and fast!

thnx

---

### Post by Zill on 2005-11-20
A newbie question as I have not yet installed Ubuntu...

Does Automatix install the additional packages in the same way as other apt-get/synaptic packages are installed?

eg.  would they then be upgraded automatically with all the other installed applications?

Many thanks.

---

### Post by cstudent on 2005-11-20
[QUOTE=Zill]A newbie question as I have not yet installed Ubuntu...

Does Automatix install the additional packages in the same way as other apt-get/synaptic packages are installed?

eg.  would they then be upgraded automatically with all the other installed applications?

Many thanks.[/QUOTE]

Automatix is essentially a bash script. It will backup your current sources.list and install a new one. Then it will use apt to download software you select and install it. Once finished all the software you install with it will get updated through synaptic because synaptic will use that same sources.list. It's very simple and very slick IMO.

Bill

---

### Post by Maniak on 2005-11-21
Cheers arnieboy - fantastic job making a lot of work very easy. It is guys like you that bring me back to linux over and over again. Thanks.

---

### Post by ezphilosophy on 2005-11-22
This is just fantastic.  Just install Breezy, load automatix, and finished.  It's this kind of thing that will make people switch over.  

-keeping the power of linux for those who can use it, but having the simplicity for those who need it.  That's ezphilosophy.

Well done.

---

### Post by robotgeek on 2005-11-23
This is based on automatix. I  contacted the author of automatix with the corrections, but he refused to correct the bugs in automatix which I've listed below. I hope the original author does correct the mistakes in his original program.I want to make it clear that I have intention of claiming arnieboy's program or anything, but i just fixed what i felt what wrong with it. 

1. Creating the root user

The root user is disabled in ubuntu. It should not be enabled by someone who does not know his way around linux.  

2. The use of --force-yes in apt-get

This is a very dangerous option that should not be enabled. This is what 'man apt-get' says:

> 
--force-yes
Force yes; This is a dangerous option that will cause apt to continue without prompting if it is doing something potentially harmful. It should not be used except in very special situations. Using force-yes can  potentially destroy your system! 

Hence, the entire script has been modified to correct these defects. Also a few packages have been disabled, because they were not meant for breezy or where other sutiable packages are available in the repos. Please refer to the changelog file for details.

---

### Post by jadugarr on 2005-11-23
> 1. Creating the root user

2. The use of --force-yes in apt-get


I don't want to get envolved in flame war but I will have to agree that those are not bugs by definition.

---

### Post by deNoobius on 2005-11-23
All Kudos, Arnieboy!!  I'm a newbie, and your script saved me a world o' pain and frustration!

Installing Ubuntu:  Free.

Getting everything to work:  Free but difficult and annoying.

Starting automatix and getting a cup of coffee to return and find out everything's done:  PRICELESS!

---

### Post by Nu-Buntu on 2005-11-23
The fact that Automatix can be studied and decyphered means that it is easy to see how the features work and how they are used. While derivatives can be improvements, I don't see that being the case here. If anyone wants to disable root again after running automatix, they can do so. If you don't trust the script or its author, study the script or install everything manually. I for one appreciate the research and effort required to put such a useful tool together for the Ubuntu community. I think the author has shown his willingness to keep the script updated and current. Perhaps the author of the so-called "safer" version should build his own program rather than piggybacking on the work of someone who he seems to want to bash.

---

### Post by rohandhruva on 2005-11-23
Hi,

I dont want to be part in a flame war. But i request the original author, arnieboy, to please not enable the root account. Going through the script, not thoroughly, i dont find anything that cannot be done by "sudo" or "sudo su -".
It is against the ubuntu "philosophy" :) 

--force-yes is not a problem. I have done it hundreds of times when i want to install lots of software during the night, when i am sleeping. If arnie considers, and releases a version that does not enable root, i will surely use AutoMatix.

Thanks,
Rohan.

---

### Post by apokryphos on 2005-11-23
[QUOTE=rohandhruva] or "sudo su -".[/QUOTE]
sudo -i is the recommended method, if you need to get into a root shell. It sets up the environment more appropriately. :)

---

### Post by rohandhruva on 2005-11-23
[QUOTE=apokryphos]sudo -i is the recommended method, if you need to get into a root shell. It sets up the environment more appropriately. :)[/QUOTE]
Oops, never knew that :) I stand corrected.

---

### Post by Pablo_Escobar on 2005-11-23
Arnieboy, don't be discouredged by someone having other view on things as You. Even if it's dead wrong.
Please do not leave the great work You're doing.

---

### Post by rohandhruva on 2005-11-23
We all realize that it feels bad to have your work ripped off by other people, and being discredited. However, by taking automatix down, you have stolen opportunity from many new users who anyway dont care whether root is enabled, or --force-yes is used. 

For their sake, i request you to put it back on. And i think that automatix and automatix-proper can both learn from each other, and in the end, provide us wit h a new automatix that combines + points of both.

Consider,
Rohan.

---

### Post by az on 2005-11-23
Is automatix proprietary?

---

### Post by deNoobius on 2005-11-23
[QUOTE=apokryphos]sudo -i is the recommended method, if you need to get into a root shell. It sets up the environment more appropriately. :)[/QUOTE]

Try doing that when launching a program that only allows itself to be run fromt the X11 environment, as happened to me recently.  It won't work.  I would have had to enable root login--or I could use Automatix's right-click to open that particular item as root from the GUI.  Of the two alternatives, the Automatix-provided one was clearly better.

Anyone who doesn't like it--don't select that option.  But don't criticize someone who has spent what I have to guess is hundreds of hours providing the rest of us with a great installer that saves hours of work.  Frankly, when I realized that tool was available via Automatix, I breathed a sigh of relief because it solved a knotty problem for me that I don't yet have the skills to solve myself.

---

### Post by imagine on 2005-11-23
[QUOTE=deNoobius]Try doing that when launching a program that only allows itself to be run fromt the X11 environment, as happened to me recently.  It won't work.  I would have had to enable root login--or I could use Automatix's right-click to open that particular item as root from the GUI.[/QUOTE]Are you speaking of Gnome's gksudo or kdesu on KDE? They should be used for X applications instead of sudo and are installed by default in (K)Ubuntu.

---

### Post by deNoobius on 2005-11-23
[QUOTE=apokryphos]Go find out what "troll" actually means, instead of sounding nonsensical and using it as a person who simply disagrees with you. I suggest you grow up.

GUI applications shouldn't be run with a direct sudo; this is more detrimental in KDE applications, but GNOME applications too can suffer from it. That's why there's gksudo (patched gksu) and kdesu (again, patched specifically for Kubuntu), in order for a user to run GUI applications as root; generally not a good idea in many cases, but it's the safest bet.[/QUOTE]

I wasn't aware of gksudo, but I'm not sure how that's different from the right-click script.  Don't both allow an item to be opened or run as root?  

BTW, do all the other distros discourage root access as well? I find that hard to believe.  My reading so far, as little as it is, leads me to believe that this is more of a Ubuntu thing, to make sure the distro was as foolproof as possible for as many people as possible.  I didn't think you could actually damage your system unless you make a mistake as root, like deleting a critical file.

---

### Post by jadugarr on 2005-11-23
[QUOTE=arnieboy]**Automatix has been taken down till all trolls and their posts pertaining to automatix are taken care of by mods/admins.**[/QUOTE]

Please don't let comments from a few people discourage you.  Most of the people really appreciate the work that you have done.  Sure it sucks that someone said that the code you spent clearly a lot of time writing and testing  has bugs (when they are clearly not), changed a few lines of your code and redistributed it without your consent.  It doesn't make your work any less appreciated by the rest of us though.

---

### Post by BLTicklemonster on 2005-11-23
I know I speak for the entire community (well except for* him*) when I say thank you for your hard work on Automatix, Arnieboy. You have provided an invaluable tool for so many newcomers. Please reconsider and leave it up for the newbs. Rant all you want, but Automatix has become the first thing people get when they install ubuntu. Without it, people are going to have a harder time getting what they need. We all read the post, and know that automatix is unimpeachable, that fellow isn't doing anything but making himself look bad. Let him, but you hold the higher ground and keep automatix up and don't let this get to you.

Thanks for your hard work.

oh, and please. :D

---

### Post by arnieboy on 2005-11-23
**Until the "safer automatix" thread and all similar ones are hard deleted, I will not bring automatix up.. Period.**

---

### Post by BLTicklemonster on 2005-11-23
Looks like you won, it's gone, bro. :p

---

### Post by arnieboy on 2005-11-23
yeah.. automatix is up again.. thanks for standing by.

---

### Post by Black Moon on 2005-11-23
Thanks for all the work it took make such a great program arnieboy. It really made my transition to linux alot smoother

---

### Post by deNoobius on 2005-11-23
I feel the same.  Thanks.

---

### Post by BLTicklemonster on 2005-11-23
[QUOTE=arnieboy]yeah.. automatix is up again.. thanks for standing by.[/QUOTE]
LMAO, LIKE I COULD SIT DOWN DURING ALL THAT?

---

### Post by darkmatter on 2005-11-23
People...if you want to argue....keep it in IRC or the Backyard...and try to be more 'civil'...not in the support/tech areas....

Continue this discussion elsewhere.

---

### Post by arnieboy on 2005-11-23
**Automatix updated to version 3.4.4 with the [Automatix license]("http://ubuntuforums.org/showthread.php?t=94310")**

---

### Post by arnieboy on 2005-11-23
one more thing.. guys I have a request..
If u want to make a real fork of automatix, please do that (like porting it to some fancy python GUI with lots of options) or some other fancy stuff.. but please abstain from changing two lines and claiming it to be safe or whatever (cuz I have had thousands of users worldwide using automatix happily minus any complaints).. The name Automatix from henceforth is trademarked, so even if u come up with any such "2 lines changed" fork , u need to change the name to something else.

If u have any issues with the code, pm me personally, and I will explain stuff to u. u dont need to be rude or take it upon urself to malign me...  cuz really I have done all this for free.. in the true spirit of Ubuntu..

---

### Post by henriquemaia on 2005-11-23
I have just tried Automatix and the ideia is great.

Thanks Arnieboy!

---

### Post by Tosa on 2005-11-24
Thanks for the Automatix.
It really makes life easier for newbies!

Regards,
Tosa.

---

### Post by Zhukov on 2005-11-24
Once again i come here requesting for your authorization to continue with my automatix clone, with some small extras, giving you full credit for the work, as i did so far. I know you're probably 180% feed up with automatix licensing problems, thats why im asking again.

---

### Post by arnieboy on 2005-11-24
[QUOTE=Zhukov]Once again i come here requesting for your authorization to continue with my automatix clone, with some small extras, giving you full credit for the work, as i did so far. I know you're probably 180% feed up with automatix licensing problems, thats why im asking again.[/QUOTE]
I have replied to your question on the main automatix thread.

---

### Post by Tails on 2005-11-26
Just asking... will this works in 64-bit Ubuntu??? :D

cheers!

---

### Post by arnieboy on 2005-11-26
[QUOTE=Tails]Just asking... will this works in 64-bit Ubuntu??? :D

cheers![/QUOTE]
if it has AMD64 bit kernel and packages, it wont work. if it is running an i386. then it will.

---

### Post by quietglow on 2005-11-27
This app ROCKS! I can do all this stuff sans script, but it sure is heck is nice to have it automated. When we start doing installs for people as part of our linux group's work, it will be a real life saver.

Thanks for all your hard work!

---

### Post by Strangerdave on 2005-11-27
I am new to this and followed the install instructions, yet nothing seemed to happen.  I don't have limewire, can't seem to find easytag, as well as the other applications that I selected to be installed.

I downloaded the installer, opened it in the home directory, and it seemed to download things, then it asked for a password and I typed in my root, then it all shut down.

Anyone else experience this?

-SD-

EDIT**Just realized that one must install them individually, it seems to work now.

---

### Post by n0ah on 2005-11-30
I'm really hoping this doesn't kill my 64-bit ubuntu, I used it twice at work (yes I convinced my boss to switch from WinXP to Ubuntu) today and it went very very smoothly, but it's bitching and moaning about the 64-bit, but we'll see how it goes.. hopefully it doesn't kill my install.. if so oh well.. i'll just re-install Breezy fresh, instead of this semi-broken copy i have from updating from Hoary.

I never knew having amd64 would be such a pain in the a$$...

---

### Post by n00blar on 2005-11-30
Great script!!!
This one did wonders on my PC and on my laptop as well.

I do have a question, since I messed something up when I ran it on my laptop.
How do I turn off numlock? I turned it ON for my laptop (I don't know what I was thinking :p ).

Thanks.

---

### Post by arnieboy on 2005-11-30
[QUOTE=n0ah]I'm really hoping this doesn't kill my 64-bit ubuntu, I used it twice at work (yes I convinced my boss to switch from WinXP to Ubuntu) today and it went very very smoothly, but it's bitching and moaning about the 64-bit, but we'll see how it goes.. hopefully it doesn't kill my install.. if so oh well.. i'll just re-install Breezy fresh, instead of this semi-broken copy i have from updating from Hoary.

I never knew having amd64 would be such a pain in the a$$...[/QUOTE]
please bear in mind that automatix DOES NOT support AMD64/ppc packages. if u are running an x86 kernel on an AMD64, then alone will it be fully supported.

---

### Post by arnieboy on 2005-12-01
[QUOTE=n00blar]Great script!!!
This one did wonders on my PC and on my laptop as well.

I do have a question, since I messed something up when I ran it on my laptop.
How do I turn off numlock? I turned it ON for my laptop (I don't know what I was thinking :p ).

Thanks.[/QUOTE]
here is how to do it:
first from terminal do:
```
sudo apt-get remove numlockx

```
now do the following:
Go to **/etc/X11/gdm/Init/** as root (use the "open as root nautilus" script which comes with automatix) and delete the file called "**Default**". 
Now look for a file which looks like: **Default_backup200512010316** (the numbers at the end is the date and time when u ran automatix to install numlockx, it will be different for u). 
**Rename** this file as "**Default**" (minus quotes). now log out of gnome and log back in. numlock wont start up again.

---

### Post by JazzCrazed on 2005-12-01
I also wanted to take a quick moment to thank you for this extremely useful installer. I really appreciate your hard work!

---

### Post by tlc on 2005-12-01
Another shout of thanks here! I can't believe I lived with gentoo for two years... :razz: 

This is all so painless! Cheers!

---

### Post by runlevel0 on 2005-12-02
[QUOTE=arnieboy]Sun's Java 1.5[/QUOTE]
Coool!!
Nice work!

---

### Post by runlevel0 on 2005-12-02
[QUOTE=tlc]Another shout of thanks here! I can't believe I lived with gentoo for two years... :razz: 

This is all so painless! Cheers![/QUOTE]

Hey, me too X'D

I was really tired of having the home-page of my browser set to [http://bugs.gentoo.org](http://bugs.gentoo.org), ROFLMAO

---

### Post by ewtesterman@cox.net on 2005-12-02
I have to thank you it worked great and is very helpful. I setup quite a few systems for people and this saves a lot of time. I have only one comment outside of that. Please do not take this as negative feed back. I had to use Easy Ubuntu to install my ATI driver, it would have been nice to have been able to just use Automatix all the way around. Again please do not take that the wrong way I am very impressed with your work. I have noticed as I looked through the repositories that there are tools to build your own distro CD I think that I would like to see how difficult it would be to add Automatix to the Ubuntu install CD, maybe we would lose less newbies that way.

---

### Post by arnieboy on 2005-12-02
[QUOTE=ewtesterman@cox.net]I have to thank you it worked great and is very helpful. I setup quite a few systems for people and this saves a lot of time. I have only one comment outside of that. Please do not take this as negative feed back. I had to use Easy Ubuntu to install my ATI driver, it would have been nice to have been able to just use Automatix all the way around. Again please do not take that the wrong way I am very impressed with your work. I have noticed as I looked through the repositories that there are tools to build your own distro CD I think that I would like to see how difficult it would be to add Automatix to the Ubuntu install CD, maybe we would lose less newbies that way.[/QUOTE]
currently there is one project working on the automatix CD:
[http://ubuntuforums.org/showthread.php?t=87382](http://ubuntuforums.org/showthread.php?t=87382)
as for ATI drivers, there are some complications in installing these drivers which cannot all be automated. Easy Ubuntu merely installs the fglrx package available for ATI cards. However, u wud need to refer to the following thread to know what I am talking about regarding the complications with this package and ATI cards in general:
[http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)

---

### Post by nppro on 2005-12-02
hello -- on most commands I enter I get this 

root@ubuntu:/home/nppro# apt-get update
E: Malformed line 1 in source list /etc/apt/sources.list (dist parse)


and was wondering why and how to fix it -- really want to install this program .. but these obstacles are keeping me from it :) 

help appreciated

---

### Post by nppro on 2005-12-03
nevermind got it -- had to copy paste a exisity source list.

---

### Post by KermitJr on 2005-12-03
Just some feedback, but pmidi stops to ask for Root passwd.

---

### Post by arnieboy on 2005-12-03
[QUOTE=KermitJr]Just some feedback, but pmidi stops to ask for Root passwd.[/QUOTE]
if u mean midi installation and configuration by automatix, yes it will ask for your root password, but when playing a file with pmidi alone, it will not ask for your root password.
play a file with pmidi in the following way:
```
pmidi <filename>
```
Also make sure that u have read permissions on the folder from which u are trying to play the file.

---

### Post by j813 on 2005-12-04
64bit not yet fully or officially supported?
Thanks

---

### Post by arnieboy on 2005-12-04
**Automatix updated to version 3.4.6 with the [Automatix license]("http://ubuntuforums.org/showthread.php?t=94310")**
[B]
Please download and install version 3.4.6.[/B]
Automatix has the new features:
[B]a) Added Ubuntu Backports
b) Removed the --force-yes switch to avoid any further controversy[/B]

---

### Post by arnieboy on 2005-12-04
[QUOTE=j813]64bit not yet fully or officially supported?
Thanks[/QUOTE]
not fully supported.

---

### Post by arnieboy on 2005-12-05
**Automatix updated to version 3.4.7 with the General Public License**

The **automatix license** ceases to be effective for the present and all future versions of automatix starting now.

---

### Post by poofyhairguy on 2005-12-05
[QUOTE=arnieboy]**Automatix updated to version 3.4.7 with the General Public License**

The **automatix license** ceases to be effective for the present and all future versions of automatix starting now.[/QUOTE]


Well thats that.

---

### Post by kalos on 2005-12-05
[QUOTE=arnieboy]Automatix updated to version 3.4.6 with the [Automatix license]("http://ubuntuforums.org/showthread.php?t=94310")[/quote]

Is there a reason I am not allowed to view the licence? I click your [link](http://ubuntuforums.org/showthread.php?t=94310) and I get this:

[quote=vBulletin Message]
kalos, you do not have permission to access this page. This could be due to one of several reasons:

   1. Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
   2. If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.[/quote]

-kalos

---

### Post by kassetra on 2005-12-05
[quote=kalos]Is there a reason I am not allowed to view the licence? I click your [link]("http://ubuntuforums.org/showthread.php?t=94310") and I get this:
-kalos[/quote]

That's because it has been re-released under the gpl.

---

### Post by veehell on 2005-12-06
I just install Automatix; executed, run very nice, thanks for this. Really help me to install some firefox and multimedia stuff (codecs and mplayer and plugins). 
No any problems during the run. Thanks!

---

### Post by Jenda on 2005-12-08
I'm glad to see that this thread has been unlocked (if indeed ever locked?).
Now automatix has ceased to exist. If you're looking for an up-to date version, you will not find it.
However, the project has been forked, and this new project has recently merged with the original project from which even Automatix was forked: EasyUbuntu.
You can download the current version here: easybreezy.robotgeek.org

I hope the forums administration doesn't mind me posting this, since I intend to give a solution to the people looking for Automatix.

---

### Post by arnieboy on 2005-12-08
Automatix is not a dead project. I created it and I will continue to work on it when I feel I should. The last version is currently available for download from the   main automatix thread.

---

### Post by poofyhairguy on 2005-12-08
[QUOTE=arnieboy]Automatix is not a dead project. I created it and I will continue to work on it when I feel I should. The last version is currently available for download from the   main automatix thread.[/QUOTE]

excellent

---

### Post by xyz on 2005-12-08
[QUOTE=poofyhairguy]excellent[/QUOTE]
I second that!and thanks for a great job.

---

### Post by noelferg on 2005-12-08
[quote=arnieboy]Automatix is not a dead project. I created it and I will continue to work on it when I feel I should. The last version is currently available for download from the   main automatix thread.[/quote] 
Hi Arnieboy, You have done a fantastic job with Automatix. Hope the problems can be resolved. Automatix is one of the main reasons I recommend Ubuntu to Linux newbies. (I am not that experienced with it, myself.)

---

### Post by blakamin on 2005-12-08
Just one thing... remind laptop owners not to install numlock.... I couldn't for the life of me work out why my password wasn't working.....:p 
(I installed it out of habit)

---

### Post by Lem on 2005-12-09
Useful script there.. saves a lot of finger-twidling in terminal to get things set-up.

Cheers! :)

---

### Post by starscalling on 2005-12-10
Setting up gdesklets-data (0.35.2-2) ...

cat: /home/nekostar/.gnome2/session-manual: No such file or directory
/usr/local/automatix/autoscript: line 494: 19485 Terminated              zenity --progress --pulsate --title "Automatix" --text "Installing gdesklets"
cat: /home/nekostar/.gnome2/session-manual: No such file or directory
mv: cannot stat `/home/nekostar/.gnome2/session-manual': No such file or directory
tail: cannot open `/home/nekostar/.gnome2/session-manual_backup' for reading: No such file or directory
expr: syntax error
expr: syntax error
gawk: /num_clients/{gsub(//,)};{print}
gawk:                       ^ syntax error
gawk: fatal: 0 is invalid as number of arguments for gsub
gawk: {sub(/0/,);print}
gawk:          ^ syntax error
gawk: fatal: 0 is invalid as number of arguments for sub
Multimedia codecs|Firefox Plugins|MS TTF Fonts|Archives|Skype|Acrobat Reader|gftp|Ctrl-Alt-Del|Ripper and Tuner|File Sharing|Multimedia Editing|DVD Ripper|Mplayer with plugin|Media Players|Opera Browser|Debian Menu|Bittorrent Clients|Avidemux|Numlock ON|Programming Tools|AUD-DVD codecs|Open Office|Nautilus Scripts|SUN JAVA 1.5|Wine|Gdesklets


er it hiccuped?

---

### Post by arnieboy on 2005-12-10
please paste the results of the following command:
```
cat ~/.gnome2/session-manual
```

---

### Post by starscalling on 2005-12-10
i dont get any reply.. sorry it took me so long.. everything ive tried as of yet works fine though :) contents of that directory:
~/.gnome2$ ls
accels              gnomebaker            panel2.d        totem-addons
backgrounds.xml     gnome-volume-control  rhythmbox       totem_config
file-roller         keyrings              session
gedit-2             main                  session-manual
gedit-metadata.xml  nautilus-scripts      share

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]i dont get any reply.. sorry it took me so long.. everything ive tried as of yet works fine though :) contents of that directory:
~/.gnome2$ ls
accels              gnomebaker            panel2.d        totem-addons
backgrounds.xml     gnome-volume-control  rhythmbox       totem_config
file-roller         keyrings              session
gedit-2             main                  session-manual
gedit-metadata.xml  nautilus-scripts      share[/QUOTE]
so gdesklets works as well?

---

### Post by starscalling on 2005-12-10
eh just tried it and heck no :P
let me grab an error here.... ::
eh it wont even start now.. i tried to run one a minute ago and it gave me some error... sorry i knew i should have wrote it down... *checks top*
i dont see it running.. yeah so that doesnt work sorry :/

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]eh just tried it and heck no :P
let me grab an error here.... ::
eh it wont even start now.. i tried to run one a minute ago and it gave me some error... sorry i knew i should have wrote it down... *checks top*
i dont see it running.. yeah so that doesnt work sorry :/[/QUOTE]
alright just paste the results of
```
cat ~/.gnome2/session-manual
```

---

### Post by starscalling on 2005-12-10
nekostar@ubuntu:~$ cat ~/.gnome2/session-manual
nekostar@ubuntu:~$

heh exactly nothing !_!

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]nekostar@ubuntu:~$ cat ~/.gnome2/session-manual
nekostar@ubuntu:~$

heh exactly nothing !_![/QUOTE]
interesting.. try doing the following:
go to system -->preferences-->sessions-->startup programs and add **gdesklets**. log out of gnome and log back in.

---

### Post by starscalling on 2005-12-10
nope nothing.. still doesnt open.. im sure i broke something somewhere....

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]nope nothing.. still doesnt open.. im sure i broke something somewhere....[/QUOTE]
try doing the following:
```
sudo apt-get install gdesklets gdesklets-data
```
after the installation ends, log out of gnome and log back in again.

---

### Post by starscalling on 2005-12-10
nekostar@ubuntu:~$ sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
gdesklets is already the newest version.
gdesklets-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

should i " sudo apt-get remove --purge gdesklets gdeksklets-data " then reinstall?

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]nekostar@ubuntu:~$ sudo apt-get install gdesklets gdesklets-data
Reading package lists... Done
Building dependency tree... Done
gdesklets is already the newest version.
gdesklets-data is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

should i " sudo apt-get remove --purge gdesklets gdeksklets-data " then reinstall?[/QUOTE]
no try running gdesklets from terminal by doing the following:
```
gdesklets
```

---

### Post by starscalling on 2005-12-10
now that is interesting :P
gdesklets
Starting gdesklets-daemon...
Connected to daemon in 226 microseconds.

i still dont see it in top.. under root or nekostar [current user]
and the gui for it doesnt come up either [thanx for all the help btw]

---

### Post by arnieboy on 2005-12-10
[QUOTE=starscalling]now that is interesting :P
gdesklets
Starting gdesklets-daemon...
Connected to daemon in 226 microseconds.

i still dont see it in top.. under root or nekostar [current user]
and the gui for it doesnt come up either [thanx for all the help btw][/QUOTE]
do u have window notification applet added to any of your panels?
if not add that, and run gdesklets from applications-->accessories
u will see a blue gdesklets icon in ur notification area and a startup screen which will let u go on to gdesklets main screen where u can add whichever gdesklets u want. add them and close the main window. log out of gnome and logback in.
u shd see gdesklets start up every time with the chosen desklets starting up automatically.

---

### Post by starscalling on 2005-12-10
yup sure enough your right as rain!!!!!
/gg :P
thanx and keep up the awesome work...
what i dont understand is _why_ it was pissy lol.. though im gonna have to look into gdesklets some more.. *imagines running openbox + gdesklets - gnome-panels* ;)

---

### Post by MicroChris on 2005-12-11
This program....is amazing..

---

### Post by starscalling on 2005-12-11
yeah i agree.. this is gonna make it a bit easier to convert a couple of friends and collegues

---

### Post by arnieboy on 2005-12-11
Thanks for the support guys.. I hope to start working on automatix again in a few days. This thread will become the active support thread.

---

### Post by Gray. on 2005-12-11
Glad to see that Automatix is being worked on again.

---

### Post by Jenda on 2005-12-11
Arnieboy: Any chance of pooling efforts with Easy Ubuntu - now that both projects are GPL'd?

---

### Post by arnieboy on 2005-12-11
[QUOTE=Jenda]Arnieboy: Any chance of pooling efforts with Easy Ubuntu - now that both projects are GPL'd?[/QUOTE]
NO. Automatix will remain independent of all forks and precedents. However, if anyone with sufficient programming skills is interested in contributing to Automatix, he is welcome to contact me.

---

### Post by chrishan on 2005-12-11
arnieboy, you are my hero! thanks for making automatix, and thanks for starting again!

---

### Post by LeTon on 2005-12-11
Hi Arnieboy...
Funny thing happens, or rather does not happen with Automatix.
I followed how-to as per this thread [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
I get a msg that automatix has been installed in Applications - sys. tools....
But it is not there!
And terminal announces that command not found!
Confused.
Thank you in advance.

---

### Post by nix4me on 2005-12-11
I doesn't show up in my menu either.

I start it fine from the terminal though.

nix4me

---

### Post by arnieboy on 2005-12-11
Leton and nix4me do the following:
download the file to your home folder. then from terminal do the following:
```
tar xzf automatix-ubuntu_v3.4.8.tar.gz
cd Automatix
./install
```
this will install Automatix in Applications --> System Tools

---

### Post by LeTon on 2005-12-11
Indeed it did:)
It just makes me wonder...how these things happen:D
Thank you.
Sure I would love to ask millions of other how-to-get-this-done kinda questions...:)

---

### Post by UbunT00L on 2005-12-11
Any chance of automating the Nvidia TV-out support?

---

### Post by arnieboy on 2005-12-11
[QUOTE=UbunT00L]Any chance of automating the Nvidia TV-out support?[/QUOTE]
If u mean this one:
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)
then, No I wont automate it because it involves editing **/etc/X11/xorg.conf** which Automatix has a strict policy of not touching except in the case of installing the nvidia drivers which is done indirectly.

---

### Post by arnieboy on 2005-12-12
Alright, The [Automatix thread]("http://ubuntuforums.org/showthread.php?t=66563") is open once again for support and development. I would be happy to take all your questions and suggestions there once again. Please try and avoid discussions of past controversies here or on [that thread]("http://ubuntuforums.org/showthread.php?t=66563"). if u feel you still have any outstanding issues regarding these past controversies, please take it to the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") to be effectively handled by the admins.
Thanks,
Arnie

---

### Post by bored2k on 2005-12-12
[Avidemux 2.1 **Final]("http://www.ubuntuforums.org/showpost.php?p=564380&postcount=19") ** for the x86 architecture.

Possible requirements: libfaac0 liba52-0.7.4 libsmjs1 (on the repositories).

---

### Post by sabredog on 2005-12-13
Thanks for this app, I am looking forward to running it after I install Breezy later this month.

first time Linux user :)

One question though, Does Automatix ask you and then set up a root password change?

Sorry, it is probably a silly question but I have not used a non Windows OS since my Unix days running MOSS design software 14 years ago.

---

### Post by UbunT00L on 2005-12-13
One small annoyance.  When automatix asks you for your root password, the focus is set on the cancel button.  So unknowingly, you type in your password, and press enter, which will cancel the entire process.  It almost seems as though the process gets completed because it doesn't ask you if you are sure if you want to cancel, it just cancels the entire process without a word.  I think setting the focus to the terminal when it asks for your password would be less confusing for some of the newer users.

---

### Post by arnieboy on 2005-12-16
**Automatix updated to version 3.5 with the General Public License**
[B]Automatix 3.5 has the following new features:
a) Finally bringing to an end a long standing controversy, Automatix no longer uses the root user (su). No need to set root password.
b) Ubuntu release check has been reworked on.[/B]

I sincerely hope this pacifies the group of people who were much against the use of root in Automatix.

---

### Post by robotgeek on 2005-12-16
[QUOTE=arnieboy]
a) Finally bringing to an end a long standing controversy, Automatix no longer uses the root user (su). No need to set root password.

I sincerely hope this pacifies the group of people who were much against the use of root in Automatix.[/QUOTE]

Great!

---

### Post by karma 23 on 2005-12-17
How do I run this on Xubuntu?  I downloaded the file but when I double-click on it, nothing happens.  Worked fine on Ubuntu (GNOME).

---

### Post by arnieboy on 2005-12-18
[QUOTE=karma 23]How do I run this on Xubuntu?  I downloaded the file but when I double-click on it, nothing happens.  Worked fine on Ubuntu (GNOME).[/QUOTE]
it is not made for xubuntu.. or Kubuntu

---

### Post by arnieboy on 2005-12-18
**[Automatix-Kubuntu 1.0]("http://ubuntuforums.org/showthread.php?t=105343") released! (This is only meant for Kubuntu Users (not for Ubuntu or Xubuntu users)**

---

### Post by dabear on 2005-12-18
Arnieboy: I believe the url should be [http://ubuntuforums.org/showthread.php?t=105343](http://ubuntuforums.org/showthread.php?t=105343)

---

### Post by arnieboy on 2005-12-18
Thanks! edited.

---

### Post by karma 23 on 2005-12-18
[QUOTE=arnieboy]it is not made for xubuntu.. or Kubuntu[/QUOTE]

Well, that would explain why.  Thanks!

---

### Post by Nu-Buntu on 2005-12-18
Arnie,

I used your Firefox 1.5 script on my desktop machine and it worked great. I used it on my laptop and it destroyed my firefox, and when I try to start firefox, it says in the toolbar, "Starting Firefox Web Browser" and the wait icon is spinning. Both then disappear with no firefox.

I used Automatix to install Opera which I am using at the moment on this laptop. I saw you added Firefox 1.5 to Automatix 4, so I ran it from there, and it said it installed. Still I get the same results in trying to start firefox. Any ideas?

Thanks!

---

### Post by arnieboy on 2005-12-18
[QUOTE=Nu-Buntu]Arnie,

I used your Firefox 1.5 script on my desktop machine and it worked great. I used it on my laptop and it destroyed my firefox, and when I try to start firefox, it says in the toolbar, "Starting Firefox Web Browser" and the wait icon is spinning. Both then disappear with no firefox.

I used Automatix to install Opera which I am using at the moment on this laptop. I saw you added Firefox 1.5 to Automatix 4, so I ran it from there, and it said it installed. Still I get the same results in trying to start firefox. Any ideas?

Thanks![/QUOTE]
try opening up terminal, and run
```
firefox
```
and paste the results here

---

### Post by Nu-Buntu on 2005-12-18
> randy@UbuntuLaptop:~$ firefox
randy@UbuntuLaptop:~$


It just goes back to a prompt.

---

### Post by arnieboy on 2005-12-18
[QUOTE=Nu-Buntu]It just goes back to a prompt.[/QUOTE]
ok try this:

```
mv ~/.mozilla ~/.mozilla-backup1
```
and restart firefox

---

### Post by Nu-Buntu on 2005-12-18
Arnie, you remain my hero! Thanks friend. This asked about importing settings, gave me the chrome error, but after that it works. 

I appreciate your help greatly.

---

### Post by Fibre on 2005-12-19
Thanks Arnie boy,

I keep finding moments where I see how helpful this is. As a Newbie I can't thank you enough for the time you've spent on getting this thing up and running.

The more I understand what extra stuff has been installed, the more I appreciate the time and effort put into to it. I plan on installing a lot of computers with it through volunteer work and also use Ubuntu to learn about linux based O/S and networking etc to eventually make a living.

You've saved me a hell of a lot of time. At least a week of headache's maybe probably more because of got no idea or very little now.

---

### Post by etchesketch on 2005-12-19
This is the most ingenious tool I have come across for linux.  (But I am a newbie, so that's not saying much.)  However, I have one problem with the NVIDIA driver installation.  I want to use the NVIDIA driver installation which is included in Automatix, but my video card is obviously undetectable if it is not connected.  If I insert my PCI NVIDIA FX5700LE, X will not boot.  X will only boot if I remove the video card and connect my monitor to the onboard video, to which the system defaults.  Is there a way to temporarily disable the video card while it is inserted, so that I can boot to X and use Automatix to install the drivers?  Or, is there a way to install the drivers from the command line while I am using the video card?  I hope I am being clear enough.

---

### Post by HandyAndy on 2005-12-19
[QUOTE=arnieboy]Leton and nix4me do the following:
download the file to your home folder. then from terminal do the following:
```
tar xzf automatix-ubuntu_v3.4.8.tar.gz
cd Automatix
./install
```
this will install Automatix in Applications --> System Tools[/QUOTE]
Hi Arnie

I'm trying to run Automatix 4.0 on Ubuntu 5.10
I followed the installation instructions and got the Automatix folder created but it doesn't show up in Applications > System Tools
So then I followed the instructions you gave here (substituting v4.0 of course) - again it creates the folder but still no menu entry
Any ideas?
Thanks

Andy

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]Hi Arnie

I'm trying to run Automatix 4.0 on Ubuntu 5.10
I followed the installation instructions and got the Automatix folder created but it doesn't show up in Applications > System Tools
So then I followed the instructions you gave here (substituting v4.0 of course) - again it creates the folder but still no menu entry
Any ideas?
Thanks

Andy[/QUOTE]
u need to go into the folder and run the install script from there.
the tar command unzips the tar.gz file.
the cd command takes u to the automatix folder
the ./install command installs automatix in /usr/local/automatix and creates an entry in Application --> System Tools
Please dont try to run Automatix from your home folder. run it only from applications --> system tools
or from terminal as
```
automatix
```

---

### Post by arnieboy on 2005-12-19
[QUOTE=etchesketch]This is the most ingenious tool I have come across for linux.  (But I am a newbie, so that's not saying much.)  However, I have one problem with the NVIDIA driver installation.  I want to use the NVIDIA driver installation which is included in Automatix, but my video card is obviously undetectable if it is not connected.  If I insert my PCI NVIDIA FX5700LE, X will not boot.  X will only boot if I remove the video card and connect my monitor to the onboard video, to which the system defaults.  Is there a way to temporarily disable the video card while it is inserted, so that I can boot to X and use Automatix to install the drivers?  Or, is there a way to install the drivers from the command line while I am using the video card?  I hope I am being clear enough.[/QUOTE]
Automatix merely installs the nvidia driver package in the official breezy repos and enables the nvidia drivers when it detects that the card is nvidia.
Your issue is one with dual cards. I think u should do the following:
1) take ur nvidia card off.
2) plug ur monitor into the integrated card.
3) boot into X.
4) make a back up of xorg.conf as follows:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1
```
5) edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
and look for the word "**nvidia**" under the "**Devices**" section
change "**nvidia**" to "**nv**".
6) Save xorg.conf and exit and shut down your comp.
7) Now plug in your nvidia card and restart your comp. X should boot up fine but u wont get 3D acceleration.
8) Now use automatix to install your nvidia drivers.
9) Restart your comp.
Have fun.

---

### Post by HandyAndy on 2005-12-19
Hi Arnie

Thanks for your reply. That's what I'm doing, but when I click the install script in the Automatix folder in Home it doesn't create the folder in usr/local/ or create the entry in Applications > System.

What I get is the text editor opening up with this:

#!/bin/bash
# Licence GPL, see gpl.txt
# Written by arnieboy
# Automatix is copyrighted by arnieboy
# Automatix is released under the General Public License (Please refer to GPL.txt)

gksudo -t "Installing Automatix" "rm -rf /usr/local/automatix"
sudo mkdir /usr/local/automatix
sudo cp conf/Automatix.desktop /usr/share/applications/
sudo cp -R * /usr/local/automatix/
sudo rm -rf /usr/bin/automatix
sudo ln -s /usr/local/automatix/Automatix /usr/bin/automatix
zenity --info --title "Automatix" --text $"Automatix has been installed in Applications-->System Tools !"

Doing it by the command line doesn't work either

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]Hi Arnie

Thanks for your reply. That's what I'm doing, but when I click the install script in the Automatix folder in Home it doesn't create the folder in usr/local/ or create the entry in Applications > System.

What I get is the text editor opening up with this:

#!/bin/bash
# Licence GPL, see gpl.txt
# Written by arnieboy
# Automatix is copyrighted by arnieboy
# Automatix is released under the General Public License (Please refer to GPL.txt)

gksudo -t "Installing Automatix" "rm -rf /usr/local/automatix"
sudo mkdir /usr/local/automatix
sudo cp conf/Automatix.desktop /usr/share/applications/
sudo cp -R * /usr/local/automatix/
sudo rm -rf /usr/bin/automatix
sudo ln -s /usr/local/automatix/Automatix /usr/bin/automatix
zenity --info --title "Automatix" --text $"Automatix has been installed in Applications-->System Tools !"

Doing it by the command line doesn't work either[/QUOTE]
u need to double click the install script and hit run..

---

### Post by HandyAndy on 2005-12-19
[QUOTE=arnieboy]u need to double click the install script and hit run..[/QUOTE]
I don't get any option to 'run' - just the text editor

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]I don't get any option to 'run' - just the text editor[/QUOTE]
ok open terminal, 
```
cd Automatix
./install
```
what errors do u get?

---

### Post by HandyAndy on 2005-12-19
[QUOTE=arnieboy]ok open terminal, 
```
cd Automatix
./install
```
what errors do u get?[/QUOTE]
That did it
It asked for my password and when I gave it, it worked
Now I've got the menu entry and the automatix folder in usr/local/

Thanks a lot, Arnie
Any idea why my system should respond differently? It's only a couple of weeks old and pretty much unmodified from the install defaults.

---

### Post by arnieboy on 2005-12-19
[QUOTE=HandyAndy]That did it
It asked for my password and when I gave it, it worked
Now I've got the menu entry and the automatix folder in usr/local/

Thanks a lot, Arnie
Any idea why my system should respond differently? It's only a couple of weeks old and pretty much unmodified from the install defaults.[/QUOTE]
you possibly made your executable scripts default to text editor. On a default Ubuntu install, one gets the option to read it, run it etc. but u possibly overrode them with a check on "dont ask me again"

---

### Post by joewilliams on 2005-12-19
Hey Arnie,

It worked great for me on a fresh 5.10 install with AMD Sempron 2800 and nvidea video card. Thanxs for all your hard work. I was considering upgrading to the 686 or K7 kernel. Do you know if this will create any problems with any of the packages Automatix installed...especially the nvidia drivers?



thanks,
Joe

---

### Post by arnieboy on 2005-12-19
[QUOTE=joewilliams]Hey Arnie,

It worked great for me on a fresh 5.10 install with AMD Sempron 2800 and nvidea video card. Thanxs for all your hard work. I was considering upgrading to the 686 or K7 kernel. Do you know if this will create any problems with any of the packages Automatix installed...especially the nvidia drivers?



thanks,
Joe[/QUOTE]
should not create a problem..

---

### Post by arnieboy on 2005-12-19
[COLOR="Navy"]I have created a debian package for automatix. I need someone to host it for me (someone with sufficient bandwidth and a 24/7 reliable server). file is just 32 KB.
Please send me a pm if you are interested.
Thanks,
Arnie[/COLOR]

---

### Post by etchesketch on 2005-12-20
[QUOTE=arnieboy]Automatix merely installs the nvidia driver package in the official breezy repos and enables the nvidia drivers when it detects that the card is nvidia.
Your issue is one with dual cards. I think u should do the following:
1) take ur nvidia card off.
2) plug ur monitor into the integrated card.
3) boot into X.
4) make a back up of xorg.conf as follows:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1
```
5) edit xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```
and look for the word "**nvidia**" under the "**Devices**" section
change "**nvidia**" to "**nv**".
6) Save xorg.conf and exit and shut down your comp.
7) Now plug in your nvidia card and restart your comp. X should boot up fine but u wont get 3D acceleration.
8) Now use automatix to install your nvidia drivers.
9) Restart your comp.
Have fun.[/QUOTE]

My xorg.conf does not have an entry for my nVidia card.

I went into bios and set it to boot using onboard video.  This way my computer can still see the nVidia card without trying to use it.

lspci gives me a line about *Unknown device 0343*:

```
0000:02:0b.0 VGA compatible controller: nVidia Corporation: Unknown device 0343 (rev a1)
```

EDIT: I have gotten my NVIDIA card to work now, using the instructions I found here:
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by arnieboy on 2005-12-20
[B]Please Note: Automatix is now available as a deb package for easier installation (read the installation instructions for details).

A BIG WOOT to [beerorkid]("http://ubuntuforums.org/member.php?u=9536") for hosting Automatix![/B]

To install Automatix do the following:
```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```

To uninstall automatix do the following:
```
sudo apt-get remove automatix
```

---

### Post by kuru on 2005-12-20
I'm going to try automatix on edubuntu-5.10. It is based on ubuntu-5.10. 
I think the installed apps will work ok for the clients, and automatix will be installed by the main user , so the icon should not be available to clients to change things.
I'll let you know as soon as my dd of the drive finishes so I can test it.

cheers
kuru

---

### Post by r4ik on 2005-12-21
Got my system back up and runnin in less than an hour.(smashed the command-line just a little to hard)
Thanks Arnieboy keep up the good work !

---

### Post by kuru on 2005-12-22
Just a note about my Automatix install on Edubuntu. The deb worked fine.
I selected a couple of the packages, since alot of them were already installed,
and away the script went . Fetching packages and installing. It's a good thing theres a check right at the startup for sudo, otherwise a client could launch the app from remote. 
To paraphrase some one wise >     Just works!

I had a couple of errors, but it was a missing gthumb-logo.png. Not sure which package it popped up from. It wasn't an Automatix error.

off-topic note: I know some people frown on Totem player, but somehow it's the only player installed on this system that can launch an avi & play it remotely via a client from clicking on a networked server. Sadly sound is not available to clients, not yet anyway.

cheers and thanks for a very nifty app.
kuru

---

### Post by n0ah on 2005-12-22
It installed -most- of the stuff just fine, but a bunch of them crapped out.. as I expected.. Opera being one of the most notable ones.. (damn them all to hell for not creating x64 version already!)

oh well.. i'm ditchin the x64 ubuntu and throwing it on my old machine and throwing win2k back on.. *ducks* i miss my games and there aren't enough programs for x64 yet that i want.. i'll be back.. that's for damn sure.. just not till x64 becomes more mainstream though

---

### Post by Styles on 2005-12-22
Just an FYI I mirrored the deb file as well

[http://www.linuxsystems.net/automatix-ubuntu_4.0-1_i386.deb](http://www.linuxsystems.net/automatix-ubuntu_4.0-1_i386.deb)

Cheers,

Eric



[QUOTE=arnieboy][B]Please Note: Automatix is now available as a deb package for easier installation (read the installation instructions for details).

A BIG WOOT to [beerorkid]("http://ubuntuforums.org/member.php?u=9536") for hosting Automatix![/B]

To install Automatix do the following:
```
wget http://beerorkid.com/automatix/automatix-ubuntu_4.0-1_i386.deb
sudo dpkg -i automatix-ubuntu_4.0-1_i386.deb
```

To uninstall automatix do the following:
```
sudo apt-get remove automatix
```[/QUOTE]

---

### Post by tagg3rx on 2005-12-22
WOW -

I have been trying to install things mannualy tracking down walk through after walk through banging my head agianst the linux wall.  On more than one occasion saying linux is still no where near user friendly....

Then I found automatix

WOW

Arnieboy you have done well

now i can get on to using my computer not trying to get it working.

Rock ON!

---

### Post by PYR on 2005-12-22
there is a possible bug with automatix. 

when using the "install firefox 1.5 and plugins" option i ran into a problem, after the task was complete i could no longer open links from gaim, irssi, etc. when i clicked on a link nothing happened, so i went to system->pref->preferred apps and found that my preferred web browser had changed from firefox %s to mozilla-firefox %s (which is a binary that does not exist), to remedy the problem i just changed it back to firefox and now everything works.

---

### Post by jasongrieves on 2005-12-23
[QUOTE=PYR]there is a possible bug with automatix. 

when using the "install firefox 1.5 and plugins" option i ran into a problem, after the task was complete i could no longer open links from gaim, irssi, etc. when i clicked on a link nothing happened, so i went to system->pref->preferred apps and found that my preferred web browser had changed from firefox %s to mozilla-firefox %s (which is a binary that does not exist), to remedy the problem i just changed it back to firefox and now everything works.[/QUOTE]

Good catch.  Same over here

---

### Post by nix4me on 2005-12-24
Arnieboy,

I just tried your script and Firefox 1.5 is not working.  I had Firefox installed in /opt before so I went ahead and removed it.

Re-ran Automatix, still no good.  Opened Synaptic and removed Firefox altogether, re-ran Automatix, no good.  1.07 keeps opening.

How do I get back to square 1.

nix4me

---

### Post by nix4me on 2005-12-24
This is what i see in the Automatix terminal.

cp: cannot stat `/home/nix4me/firefox': No such file or directory
cp: `/opt/firefox/plugins/': specified destination directory does not exist
Try `cp --help' for more information.
cp: `/opt/firefox/plugins/': specified destination directory does not exist
Try `cp --help' for more information.
mv: cannot stat `/home/nix4me/.mozilla': No such file or directory
Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
dpkg-divert: `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu' clashes with `local diversion of /usr/bin/firef to /usr/bin/firefox.ubuntu'
ln: `/usr/bin/firefox': File exists
ln: `/usr/bin/mozilla-firefox': File exists
./autoscript: line 603:  9710 Terminated              zenity --progress --pulsate --title "Automatix" --text "Installing Firefox 1.5"


nix4me

---

### Post by WackToMack on 2005-12-24
How can I tell which version of Automatix I have?

---

### Post by Aero-Z on 2005-12-24
[QUOTE=WackToMack]How can I tell which version of Automatix I have?[/QUOTE]
Open up Synaptic and search for Automatix

---

### Post by WackToMack on 2005-12-24
Oh... cool... thanks.  But then why didn't Automatix install Firefox Version 1.5?  That is the latest version, right?  I'm still using 1.0.7...  Does Automatix remove older programs and then install the newer versions, does it just overwrite them, or does it skip installing programs that are already installed?

---

### Post by Aero-Z on 2005-12-24
[QUOTE=WackToMack]Oh... cool... thanks.  But then why didn't Automatix install Firefox Version 1.5?  That is the latest version, right?  I'm still using 1.0.7...  Does Automatix remove older programs and then install the newer versions, does it just overwrite them, or does it skip installing programs that are already installed?[/QUOTE]
Search the forum for the Firefox issue.There are more people who have problems intalling Firefox 1.5 with Automatix

---

### Post by nix4me on 2005-12-25
The only way I get Firfox 1.5 to work is by using the Wiki instructions and install it to /opt.  Works fine.

On my Debian box, there is already a Firefox 1.5 in the unstable repositories.

nix4me

---

### Post by tseliot on 2005-12-25
[QUOTE=Aero-Z]Search the forum for the Firefox issue.There are more people who have problems intalling Firefox 1.5 with Automatix[/QUOTE]
No problems whatsoever here (Firefox 1.5 installed with Automatix)

---

### Post by Aero-Z on 2005-12-25
[QUOTE=tseliot]No problems whatsoever here (Firefox 1.5 installed with Automatix)[/QUOTE]
No problems with Firefox 1.5 and Automatix here also. I had somekind of error when I ran Firefox 1.5 the first time, but after that everything seems to work fine.

---

### Post by azteech on 2005-12-26
[quote=Aero-Z]No problems with Firefox 1.5 and Automatix here also. I had somekind of error when I ran Firefox 1.5 the first time, but after that everything seems to work fine.[/quote] 
While I have no problems with installing firefox 1.5, using automatix, I am not able to get the firefox 1.5 to recognize the java plugin that is downloaded by automatix. Has anyone else experienced this, and is there a solution?
If it helps, I 1st downloaded/installed firefox 1.5 using automatix, then after restarting the system, I downloaded the plugins. during download/install I did not note any error messages.

Edit: corrected misspellings

---

### Post by arnieboy on 2005-12-26
[QUOTE=azteech]While I have no problems with installing firefox 1.5, using automatrix, I am not able to get the firefox 1.5 to recognize the java plugin that is downloaded by automatrix. Has anyone else experienced this, and is there a solution?
If it helps, I 1st downloaded/installed firefox 1.5 using automatrix, then after restarting the system, I downloaded the plugins. during download/install I did not note any error messages.[/QUOTE]
the following will solve your java problem:
[http://ubuntuforums.org/showpost.php?p=594437&postcount=223](http://ubuntuforums.org/showpost.php?p=594437&postcount=223)
now please be nice enuf to help others with the same problem and give them this link. I will correct this bug in automatix in a few days (I am on vacation right now).


and please spell it right.. lol.. its automatix.

---

### Post by azteech on 2005-12-26
[quote=arnieboy]the following will solve your java problem:
[http://ubuntuforums.org/showpost.php?p=594437&postcount=223]("http://ubuntuforums.org/showpost.php?p=594437&postcount=223")
now please be nice enuf to help others with the same problem and give them this link. I will correct this bug in automatix in a few days (I am on vacation right now).


and please spell it right.. lol.. its automatix.[/quote] 
Thank you arnieboy. That did the trick. 
Have a great vacation and Happy Holidays.

BTW, sorry for the misspelling of automatix. ...

---

### Post by Nu-Buntu on 2005-12-27
Arnie,

I noticed there is an update to OOo, version 2.0.1 available. It appears to be more than a minor bug fix, as it adds some new capabilities. You might want to take a look for the next version of Automatix.

---

### Post by Sokraates on 2005-12-28
[QUOTE=Nu-Buntu]Arnie,

I noticed there is an update to OOo, version 2.0.1 available. It appears to be more than a minor bug fix, as it adds some new capabilities. You might want to take a look for the next version of Automatix.[/QUOTE]

To update OOo from 2.0 to 2.0.1 we will first need debs and a repo where Automatix can get it from. AFAIK there are none yet.

Once we've got them, I'm sure arnieboy will update Automatix ASAP.

---

### Post by huh? on 2005-12-28
having trouble with the public.planetmirror.com link...is it broken ?

---

### Post by Sokraates on 2005-12-28
[QUOTE=huh?]having trouble with the public.planetmirror.com link...is it broken ?[/QUOTE]

Yup ... again. Guess arnieboy will have to remove the repo after all (see post #1232 [here](http://ubuntuforums.org/showthread.php?t=66563&page=124)).

---

### Post by arnieboy on 2005-12-29
planetmirror removed and java firefox issue fixed in version 4.1

---

### Post by nimd4 on 2005-12-29
Hi, from what I can see, automatix offers to install OoO 2.0 while version 2.0.1 is available and besides, Ubuntu does come with Office anyway .. the whole issue seems a little confusing; just a heads-up, plz don't bother with my observation :)

Vladimir

---

### Post by arnieboy on 2005-12-29
[QUOTE=nimd4]Hi, from what I can see, automatix offers to install OoO 2.0 while version 2.0.1 is available and besides, Ubuntu does come with Office anyway .. the whole issue seems a little confusing; just a heads-up, plz don't bother with my observation :)

Vladimir[/QUOTE]
ubuntu comes with version 1.9x . automatix upgrades it to 2.0. version 2.0.1 is available yes, but its still not been made into reliable debs. once thats done, automatix will also get them for u.

---

### Post by nimd4 on 2005-12-30
Thanks for following up on that. I am finding my way extremely difficult around this (desktop) Linux, there seems to be a lot to discover and learn since I am a first-time user. Thanks again.

Vladimir

---

### Post by canadianwriterman on 2005-12-30
[QUOTE=nimd4]Thanks for following up on that. I am finding my way extremely difficult around this (desktop) Linux, there seems to be a lot to discover and learn since I am a first-time user. Thanks again.

Vladimir[/QUOTE]

Keep at it, nimd4. I spent about two months figuring out how everything works in Ubuntu and Linux. While I'm no expert yet, I have got Ubuntu working perfectly for me and customized just the way I want. These forums are an excellent way to navigate your way through that learning phase.

---

### Post by nimd4 on 2005-12-30
I will :) The forums are awesome and so are the people, thanks for the *words of encouragement* :D

---

### Post by corefile on 2005-12-31
Arnieboy, are you still insiting on messing up this great script you have created (with the help of others) by using the NON OPENSOURCE license that you unforunatly decide to use?

---

### Post by cjm5229 on 2005-12-31
Arnieboy,
  I have a question, My son's computer (an old Compaq Presario). He's 10 yrs old and thinks he's a computer expert, so we give him the old one to break. Gstreamer and Skype will not install from either Automatix or Easy Ubuntu. He just wiped his Windows completely and put Ubuntu in to it. Could it be a sound card issue? I would rell you what the errors were, but he is busy adding a second harddrive right now to put Win back on as a Dual boot until he gets these problems solved. I might get to catch him between computer dismantleings and find out if he has the errors. If so I will add an edit to this. I really appreciate what you do for Ubuntu, With out Automatix and the Howto's that you have written I would have thrown up my hands a long time ago. I hardly ever have to go to my Windows partition anymore, when I get the rest of my files transferred, I might just remove windows completely. If it weren't for you and a few of the others on this forum I would probably have gone back to fighting virii and spyware for kicks.:smile:  
Carl

---

### Post by philetus on 2006-01-04
Thanks for the tool, Arnieboy.
MS has got to be squirming.

---

### Post by ausm on 2006-01-04
Hi Arnieboy,

I really appreciate all your hard work with this awesome graphical Installer. It made my transition from Windows soooo much easier. I have tried many flavors of Linux but none of them offer a tool as handy as the one you created or have such a large,helpful and FRIENDLY community as this one.

Keep up the great work!

Ausm

---

### Post by jeepmanjr on 2006-01-06
See Above

---

### Post by jeepmanjr on 2006-01-06
See Above

---

### Post by jeepmanjr on 2006-01-06
WOW...three posts!  How'd that happen?!


OUTSTANDING script!!  Loaded without a hitch.  I recently installed Breezy and manually loaded quite a bit of software.  It took me more than FOUR DAYS of sitting in front of my 'puter researching, downloading and attempting installs...one after the other.  While I did manage to get most everything up 'n running, I was still missing a bunch of stuff.  Now I have it.  If you've been there/done that, you will absolutely love this script.

Manually installing packages is a very good learning experience for a noob (like me) and everyone should take a stab at it.  You'll learn a whole lot in the process.

This script replaces countless hours of installation effort.  Arnieboy deserves a bottomless beer from the Ubuntu community for this fine peice.  If you utilize his work, please take the time to give him a shout and express your appreciation.  It's the least we could do.

Arnieboy, my hat is off to you sir....

:cool:  Mike

---

### Post by arnieboy on 2006-01-06
[QUOTE=jeepmanjr]WOW...three posts!  How'd that happen?!


OUTSTANDING script!!  Loaded without a hitch.  I recently installed Breezy and manually loaded quite a bit of software.  It took me more than FOUR DAYS of sitting in front of my 'puter researching, downloading and attempting installs...one after the other.  While I did manage to get most everything up 'n running, I was still missing a bunch of stuff.  Now I have it.  If you've been there/done that, you will absolutely love this script.

Manually installing packages is a very good learning experience for a noob (like me) and everyone should take a stab at it.  You'll learn a whole lot in the process.

This script replaces countless hours of installation effort.  Arnieboy deserves a bottomless beer from the Ubuntu community for this fine peice.  If you utilize his work, please take the time to give him a shout and express your appreciation.  It's the least we could do.

Arnieboy, my hat is off to you sir....

:cool:  Mike[/QUOTE]
Thank you sir :) I really appreciate this overwhelming appreciation :)

---

### Post by Onos on 2006-01-08
Is there any plans in the works for an Xubuntu port of Automatix?

I am pulling my teeth and hair out trying to get a working version of mplayer installed; mplayer appears not to be supported anymore (for Xubuntu) in Synaptic or via apt-get... and the thought of trying to compile anything scares me witless.

---

### Post by cyberwisdom on 2006-01-09
I just installed automatix and when I run it I get the following error:

./autoscript: line 634: zenity: command not found
## created by arnieplanetremoved
./autoscript: line 59: zenity: command not found
./autoscript: line 637: zenity: command not found

I get the same error when I run it as sudo.


What could it be?

Thanx!

---

### Post by arnieboy on 2006-01-09
[QUOTE=cyberwisdom]I just installed automatix and when I run it I get the following error:

./autoscript: line 634: zenity: command not found
## created by arnieplanetremoved
./autoscript: line 59: zenity: command not found
./autoscript: line 637: zenity: command not found

I get the same error when I run it as sudo.


What could it be?

Thanx![/QUOTE]
are u using KDE? if yes, then this is what the first post of this thread says:
> For a KUBUNTU BREEZY version of Automatix go to [this thread]("http://ubuntuforums.org/showthread.php?t=105343")

---

### Post by jeepmanjr on 2006-01-09
Copy and paste the original script into a terminal window.  It will auto-load Automatix for you.

Afterwards, type:

sudo automatix

in the terminal window and follow instructions.  Just that simple.

---

### Post by arnieboy on 2006-01-09
[QUOTE=jeepmanjr]Copy and paste the original script into a terminal window.  It will auto-load Automatix for you.

Afterwards, type:

sudo automatix

in the terminal window and follow instructions.  Just that simple.[/QUOTE]
**Please dont run Automatix as sudo**
if u want to run it from terminal run it as follows:
```
Automatix
```

---

### Post by jeepmanjr on 2006-01-09
Odd.  When I originally ran the script, that's what I did.  However, it asked for my password later on, which I provided, hit enter and it quit installing.  I started it again, but the second time I sudo'd first, didn't have a problem, everything installed like cake.

Once again, GREAT script senor!!  Thanks!!

---

### Post by whector on 2006-01-10
2 problems:

first of all, automatix edited my sources.list and removed my .fi (finland :) ) mirror. Is it possible to save my old sources.list?

Automatix also installed Firefox 1.5 (US-version) and I would like to use finnish version. Is it possible to install finnish language support to the new firefox1.5?

Thanks!

---

### Post by the_it on 2006-01-10
I've got a weird problem with firefox 1.5 in automatix.  The root user has access to the search engines in the search bar like google, wikipedia etc etc, whereas everyone else doesn't (only the magnifiying glass icon is there).  I don't want to browse in root.  Can anything be done about this?

---

### Post by arnieboy on 2006-01-10
[QUOTE=whector]Automatix also installed Firefox 1.5 (US-version) and I would like to use finnish version. Is it possible to install finnish language support to the new firefox1.5?[/QUOTE]
yes its quite easy. do the following:
```
gedit /usr/local/automatix/autoscript
```
look for the line:
[PHP]wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/en-US/firefox-1.5.tar.gz
[/PHP]
change that to:
[PHP]wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5/linux-i686/fi/firefox-1.5.tar.gz
[/PHP]save the file, exit, run automatix again and install firefox 1.5
[QUOTE=whector]automatix edited my sources.list and removed my .fi (finland :) ) mirror. Is it possible to save my old sources.list?[/quote]
when u are done installing the finnish version of firefox 1.5: do the following:
```
sudo gedit /etc/apt/sources.list

```and change the **official ubuntu breezy** repos to the finnish ones. Dont touch the other repos (and DONT DELETE **#arnieplanetremoved** at the end). save and exit and do a :
```
sudo apt-get update

```
things will be back to exactly what u want them to be. have fun!

---

### Post by arnieboy on 2006-01-10
[QUOTE=the_it]I've got a weird problem with firefox 1.5 in automatix.  The root user has access to the search engines in the search bar like google, wikipedia etc etc, whereas everyone else doesn't (only the magnifiying glass icon is there).  I don't want to browse in root.  Can anything be done about this?[/QUOTE]
u mean u tried to run it as ```
sudo firefox
```? please dont do that.
do the following (**after closing all firefox windows**):
```
mv ~/.mozilla ~/.mozilla_new_backup
```
and restart firefox from menu.

---

### Post by cwallace on 2006-01-10
Does anyone know how to uninstall the "CTRL-ALT-DELETE" patch?

---

### Post by the_it on 2006-01-10
[QUOTE=arnieboy]u mean u tried to run it as ```
sudo firefox
```? please dont do that.[/QUOTE]

I know, I was just testing to see where the problem came from.

do the following (**after closing all firefox windows**):
```
mv ~/.mozilla ~/.mozilla_new_backup
```
and restart firefox from menu.[/QUOTE]

WTF strange!  It worked.  But I swear I already tried that before.  Anyhow, since it deleted my extensions, I just copied over my old extensions to my newly regenerated ones using

```
$ cp -Rvf .mozilla_new_backup/firefox/*.default/extensions* .mozilla/firefox/*default/
```

Voila extensions back.  Thanks for the help.

---

### Post by cyberwisdom on 2006-01-12
[QUOTE=arnieboy]are u using KDE? if yes, then this is what the first post of this thread says:[/QUOTE]
I'm not using KDE. I'm using Gnome on Ubuntu breezy 5.10.  

I tried Automatix on the default installation of 5.10 and got the above error.  Now I did a smart upgrade via synaptic and downloaded your lastes Automatix  4.4-1 and I get a similar error but with different line numbers:

```
./autoscript: line 649: zenity: command not found
## created by arnieplanetremoved
./autoscript: line 60: zenity: command not found
./autoscript: line 652: zenity: command not found

```

I've used Automatix before with breezy and never had this issue.

What do you think it could be?

---

### Post by arnieboy on 2006-01-12
[QUOTE=cyberwisdom]I'm not using KDE. I'm using Gnome on Ubuntu breezy 5.10.  

I tried Automatix on the default installation of 5.10 and got the above error.  Now I did a smart upgrade via synaptic and downloaded your lastes Automatix  4.4-1 and I get a similar error but with different line numbers:

```
./autoscript: line 649: zenity: command not found
## created by arnieplanetremoved
./autoscript: line 60: zenity: command not found
./autoscript: line 652: zenity: command not found

```

I've used Automatix before with breezy and never had this issue.

What do you think it could be?[/QUOTE]
```
sudo apt-get install zenity
```
and run automatix again.

---

### Post by cyberwisdom on 2006-01-12
Your quick!

I just came back to say I did apt-get install zenity that it worked, but you had already suggested it.:D 

Weird, for some reason zenity wasn't installed...

Thanx!!!!

---

### Post by gpeck157 on 2006-01-12
Hey Arnieboy or Anyone,

I installed Firestarter using Automatix, and had it automatically startup when my system boots, but now I no longer want to use Firestarter. I removed the Firestarter package, but it's still trying to start up every time my system boots (it's asking for my password). How do I get it to stop asking me for my password on startup, and how do I make sure it is completely removed?

Thanks...

---

### Post by arnieboy on 2006-01-12
[QUOTE=gpeck157]Hey Arnieboy,

I installed Firestarter using Automatix, and had it automatically startup when my system boots, but now I no longer want to use Firestarter. I removed the Firestarter package, but it's still trying to start up every time my system boots (it's asking for my password). How do I get it to stop asking me for my password on startup, and how do I make sure it is completely removed?

Thanks...[/QUOTE]
go to system-->preferences-->sessions-->startup programs and delete "gksudo firestarter"

---

### Post by gpeck157 on 2006-01-12
Thanks! It worked beautifully, appreciate the quick response!

Glen

---

### Post by HJThis on 2006-01-15
Hello,To all

Wow this is great i just have one thing to ask
i see that you can also get Firefox1.5

has anyone done this yet if so how did the install
go having any problems

should i just go ahead & install FF-1.5

Thank you

---

### Post by nicdaug on 2006-01-15
Hi everybody, I am new to linux.  I installed ubuntu a few days ago and then I found this forum and automatix(which I think is a great program). My only problem is that since I ran it, my firefox home page has been stuck at mcdonalds.com. Its really annoying me and I just cant seem to figure out how to change it. It seems like a browser hijack that you get with windows IE, but that doesnt seem likely. Does anyone know how to fix this? 

Oh and I was just assuming that it was automatix that caused the problem because it didnt start happening until automatix was run.

Thanks in advance

---

### Post by arnieboy on 2006-01-15
[QUOTE=nicdaug]Hi everybody, I am new to linux.  I installed ubuntu a few days ago and then I found this forum and automatix(which I think is a great program). My only problem is that since I ran it, my firefox home page has been stuck at mcdonalds.com. Its really annoying me and I just cant seem to figure out how to change it. It seems like a browser hijack that you get with windows IE, but that doesnt seem likely. Does anyone know how to fix this? 

Oh and I was just assuming that it was automatix that caused the problem because it didnt start happening until automatix was run.

Thanks in advance[/QUOTE]
edit -->preferences-->General --> Home page

---

### Post by HJThis on 2006-01-15
Hello,nicdaug & Welcome

Could you please tell me if you installed Firefox1.5
using Automatix.

Thank you

---

### Post by souled on 2006-01-15
I just installed 1.5 using Automatix. No problems here. Go for it!

---

### Post by HJThis on 2006-01-15
Hi,souled

Ok thanks i will give it a go at

Thank you

---

### Post by Twizz on 2006-01-15
I installed it yesterday worked really well for me.  I read trew this thread first and found a way to get my bookmarks back to.  You can really tell the difference between 1.0 and 1.5.

---

### Post by nicdaug on 2006-01-15
hey, arnieboy, my homepage is set to [www.linuxquestions.org](www.linuxquestions.org).  I just dont understand why it directs me to [www.mcdonalds.com](www.mcdonalds.com) upon start up of firefox.

---

### Post by arnieboy on 2006-01-15
[QUOTE=nicdaug]hey, arnieboy, my homepage is set to [www.linuxquestions.org](www.linuxquestions.org).  I just dont understand why it directs me to [www.mcdonalds.com](www.mcdonalds.com) upon start up of firefox.[/QUOTE]
do the following:
**first close all firefox windows**. 
now open up terminal and do the following:
```
mv ~/.mozilla ~/.mozilla_new_backup
```
restart firefox.

---

### Post by LeTon on 2006-01-15
Hi arnieboy...

I'm a bit puzzled because the latest automatix installed everything in my home directory...well it is cluttered now...


EDIT:I Guess that is where everything is supposed to be, right?
I have my hidden file viewer enabled.

---

### Post by tkjacobsen on 2006-01-17
I thint you should remove --force-yes from the code. Automatix really messed up my system so i have to reinstall. I think it is a very god consept, os i made my own version, with a little modification in the code. It only installs packages form ubuntu repos and kde3.5 and amarok 1.7.5 from kubuntu. Works much more stable for me. (mainly for Kubuntu, but not only):
[http://www.student.dtu.dk/~s052580/files/autoinstaller.tar.gz](http://www.student.dtu.dk/~s052580/files/autoinstaller.tar.gz)

---

### Post by iansyngin on 2006-01-19
is amarok included in the script?
if not, it defo should be.

---

### Post by lzfy on 2006-01-19
Hi, im using Automatix now and it makes my life really easier but i have one problem, when i play files with Totem they're playing really fast, also gif's and flash is playing very fast. is there a solution for this?

---

### Post by nrayever on 2006-01-20
cool!! this thing works great!!! great app!! :razz: :razz:

---

### Post by Nezmin2 on 2006-01-20
Hey arnieboy,
 
I dual boot between Ubuntu & Fedora Core 4. Does automatix work in other distributions or is it Ubuntu specific?

---

### Post by welsh_spud on 2006-01-20
> I dual boot between Ubuntu & Fedora Core 4. Does automatix work in other distributions or is it Ubuntu specific?

Automatix is very very ubuntu specific, so much so that it only works with certain versions of Ubuntu (breezy)

---

### Post by arnieboy on 2006-01-20
[QUOTE=iansyngin]is amarok included in the script?
if not, it defo should be.[/QUOTE]
including amarok in automatix is not a great idea because it will make a hundred KDE libs get downloaded as well.
to install amarok, all that one needs to do is:
```
sudo apt-get install amarok
```

---

### Post by arnieboy on 2006-01-20
[QUOTE=LeTon]Hi arnieboy...

I'm a bit puzzled because the latest automatix installed everything in my home directory...well it is cluttered now...


EDIT:I Guess that is where everything is supposed to be, right?
I have my hidden file viewer enabled.[/QUOTE]
all user specific folders and files for different softwares will reside in your home directory. they will start with a  dot. (like .mozilla). thats how linux works.
open nautilus and press ctrl-H if u dont want to see them.

---

### Post by thava on 2006-01-24
How can i uninstall Limeware, Dc++, i used Automatix to isntall thease tools.

I have uninstall Amule with apt-get remove

but, i can't do the same with limeware and dc++

Any idea?

/ Thava

---

### Post by arnieboy on 2006-01-24
[QUOTE=thava]How can i uninstall Limeware, Dc++, i used Automatix to isntall thease tools.

I have uninstall Amule with apt-get remove

but, i can't do the same with limeware and dc++

Any idea?

/ Thava[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)

---

### Post by thava on 2006-01-24
thanx a lot for the link and its work.

/ Thava
[QUOTE=arnieboy][http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)[/QUOTE]

---

### Post by arnieboy on 2006-01-24
[B]_Automatix updated to version 5.0_
New features in version 5.0 :
a) Automatix-Kubuntu merged with Automatix (now there is just one version of Automatix for Gnome/KDE/XFCE)
b) Frostwire updated to version 4.10[/B]

**To install Automatix in Ubuntu, do the following from terminal:**
```
sudo apt-get install xterm
wget http://beerorkid.com/automatix/automatix_5.0-1_i386.deb
sudo dpkg -i automatix_5.0-1_i386.deb
```
**To install Automatix in Kubuntu/Xubuntu do the following:**
```
sudo apt-get remove automatix-kubuntu
sudo apt-get install xterm libglade2-0 libgnomecanvas2-0
wget http://kambing.vlsm.org/ubuntu/pool/main/z/zenity/zenity_2.10.0-0ubuntu1_i386.deb
sudo dpkg -i zenity_2.10.0-0ubuntu1_i386.deb
wget http://beerorkid.com/automatix/automatix_5.0-1_i386.deb
sudo dpkg -i automatix_5.0-1_i386.deb
```

[B]Automatix gets installed in Applications--> System Tools (GNOME)
and in main menu-->System (KDE/XFCE)[/B]

---

### Post by vayu on 2006-01-26
[QUOTE=arnieboy][B]_Automatix updated to version 5.0_
New features in version 5.0 :
a) Automatix-Kubuntu merged with Automatix (now there is just one version of Automatix for Gnome/KDE/XFCE)
[/QUOTE]

I Use GNOME and KDE.  (Ubuntu, then apt-get Kubuntu-desktop).  I have used Automatix for multimedia on GNOME, it works great.  In KDE (3.5)  I have problems with kaffeine as file associations with other programs.  Should I use the new Automatix?  Should I remove the old one?  Should I run it in KDE?  I don't want to disturb GNOME.

---

### Post by arnieboy on 2006-01-26
[QUOTE=vayu]I Use GNOME and KDE.  (Ubuntu, then apt-get Kubuntu-desktop).  I have used Automatix for multimedia on GNOME, it works great.  In KDE (3.5)  I have problems with kaffeine as file associations with other programs.  Should I use the new Automatix?  Should I remove the old one?  Should I run it in KDE?  I don't want to disturb GNOME.[/QUOTE]
the installation procedure outlines clearly that u need to remove automatix-kubuntu. the automatix package will get automatically replaced.

---

### Post by desperado666 on 2006-01-27
I would like to have the latest relase of 

K3b
gimp

in future versions of automatix


Thx

---

### Post by JLChafardet on 2006-01-28
i would like to see it for x64

---

### Post by realthor on 2006-01-28
hello, just another linux starter here. I've been playing at linux for some months but i waited to set up an internet connection at home because everything in linux works with internet. I recently started downloading distro after distro first trying them under vmware and just one week ago directly from hdd install. I settled on a debian-based distro just after reading about linux, before having cable internet at home, so my option was tighter: after some testing i remained with mepis, kanotix and kubuntu, but both mepis and kanotix had some bad points (mepis being a corporate business and kanotix being too small to have a long-term perspective).

Of course Kubuntu has its bad point namely not being multimedia friendly due to patents in usa. After getting a kde error in both mepis and kanotix (something related to inter-process communication at start-up) i gave them up and reinstalled kubuntu with the hope of succeding installing all those codecs for dvd,cd,divx,xvid,vmw,avi,flash,mp3 and so on. I managed to play mp3s due tu a g-streamer plugin in the universe repo i guess that was used by amarok and then uninstalled amarok and put xmms instead today in the morning before coming here to work. Here i browsed a few minutes and after discovering this thread, for about 5 hours i am reading it and marveling at this tool. 

Arnieman you're a genious, really, this tool will make hoards of noobs to move to linux. You probably did a better job than all other distros alltogether just because you make it easy. My sincere congratulations and my heat is down for u mister.

Too bad i use dapper flight3 but i'm seriously considering going back to kubuntu breezy as there's no dapper support from automatix:(.
Anyway great tool, worth downgrading so next days i will do this.
I had a few questions when starting this thread but lost them now, so i'll be back.
Cheers! and again WOW, great work, keep it up!

---

### Post by realthor on 2006-01-28
Ah, i knew i had a question: why don't u bundle in the script some software to watch television on screen?- or i didn't see it?
And again, which thread is to be used this one or the other, with the latest posts on [http://ubuntuforums.org/showthread.php?t=66563&page=158???](http://ubuntuforums.org/showthread.php?t=66563&page=158???)
Another one :D what about 

Freeevo ([http://freevo.sourceforge.net/](http://freevo.sourceforge.net/)) or 

MythTV ([http://www.mythtv.org/modules.php?name=MythFeatures](http://www.mythtv.org/modules.php?name=MythFeatures)) 

included? (just an ideea, don't know too much about them) but since windows media center is on wave now how about a linux media center for those whoo convert?

One more thing : take a look at sbackup at [http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)
Cheers and keep up the grat work!

---

### Post by TheSource on 2006-01-28
Sorta off topic but anyone know how I can get my terminal window to always have the style that Automatix script uses?

---

### Post by arnieboy on 2006-01-28
[QUOTE=TheSource]Sorta off topic but anyone know how I can get my terminal window to always have the style that Automatix script uses?[/QUOTE]
Automatix uses xterm while you use gnome-terminal.
press alt-F2 and type **xterm** and press enter.
Enjoy!

---

### Post by TheSource on 2006-01-28
I see. Thanks.

Too bad it dont have the right click menu to open a new tab. I really like that.

---

### Post by breezyfox on 2006-01-29
HI 
I am looking to install firefox 1.5 without installing all firefox plugins.
I am on dial up and through automatix it asks to downloads tons of pluguns, too much to down load on dialup.
So for the time being i would prefer to install without xtra plugins like no sun jawa, acrobat read etc etc. is there any way out.

thanks

bz

---

### Post by Trespasser on 2006-01-29
I second that. Love Automatix, Arnieboy. Thanks for your efforts. :)

---

### Post by breezyfox on 2006-01-29
[QUOTE=breezyfox]HI 
I am looking to install firefox 1.5 without installing all firefox plugins.
I am on dial up and through automatix it asks to downloads tons of pluguns, too 


bz[/QUOTE]
 Hi all. 
I have installed firefox 1.5 directly from mozilla. thanks for wiki guide in this regard. worked perfect.

bz

---

### Post by SolidAndShade on 2006-01-31
Automatix works great, except for one thing. I used it to install firestarter, and now whenever I start Gnome, I get a dialog asking me for my password to start Firestarter. When I input the password, I get a dialog saying "process terminated child 0" or something along those lines. I can look at the message again and type it exactly if necessary. I can start Firestarter with no problems by selecting it from the menu, but it would be nice if I could start it along with Gnome. Do you have any ideas as to why this happens? Thanks.

---

### Post by KrazyPenguin on 2006-01-31
[QUOTE=SolidAndShade]Automatix works great, except for one thing. I used it to install firestarter, and now whenever I start Gnome, I get a dialog asking me for my password to start Firestarter. When I input the password, I get a dialog saying "process terminated child 0" or something along those lines. I can look at the message again and type it exactly if necessary. I can start Firestarter with no problems by selecting it from the menu, but it would be nice if I could start it along with Gnome. Do you have any ideas as to why this happens? Thanks.[/QUOTE]


Here is a little guide I wrote: You need to give root privilages, so the easiest way is to add firestarter to sudoers.  Check out step #2.

By KrazyPenguin
Created On: 12.30.05
This guide shows how to easily install Firestarter, and have your system start without the root password prompt with 		Firestarter minimized to the system tray.  
1) Install Firestarter using Add Applications, Automatix or Synaptic
Open Applications (top left of screen) --> Click on “Add Applications” (bottom of menu)
After the password prompt the “Add Applications” GUI will open, then type in the search box “firestarter” and enter. 
After a few seconds the search brings up “Firestarter”, check the little box to the left of it, and then click “Apply” on the 		bottom right.  A “Changes Pending” box will appear saying that Firestarter is to be Added.  Click apply to install.
Note: Firestarter will be automatically added to Applications --> System Tools --> Firestarter
2) Giving the user permission to launch Firestarter without the root password.
Open a terminal and type: sudo gedit /etc/sudoers
Add this line to the bottom: username ALL=NOPASSWD:/usr/sbin/firestarter
Save the file and close the terminal.
Note: Make sure “username” is your actual username ;-)
3) Start Firestarter
Alt – F2 (to Run Application) or open a terminal and type:
sudo firestarter
The Wizard should open and will ask for some information.  Go here for more help:
 [http://www.fs-security.com/docs/wizard.php](http://www.fs-security.com/docs/wizard.php)
4) Minimize Firestarter to tray on window close.
With Firestarter already open click --> Preferences --> check “Minimize to tray on window close”
5) Launching Firestarter minimized to the tray on login.
System --> Preferences --> Sessions --> Startup Programs --> Add 
Enter this line:
sudo firestarter --start-hidden
.....and click Ok and you're done.
6) Stop Firestarter from loading on login.
System --> Preferences --> Sessions --> Startup Programs
Click on “sudo firestarter --start-hidden” and then choose “Delete”.
7) Remove Firestarter using Add Applications.
Open Applications --> Click on “Add Applications”
After the password prompt the “Add Applications” GUI will open, then type in the search box “firestarter” and enter.
After a few seconds the search brings up “Firestarter”, UNcheck the little box to the left of it, and then click “Apply” on the 	bottom right.  A “Changes Pending” box will appear saying that Firestarter is to be removed.  Click apply to remove.
8) Test the Firewall
[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/) 
[http://www.pcflank.com](http://www.pcflank.com)
 Shields Up! >> [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by arnieboy on 2006-01-31
[QUOTE=KrazyPenguin]
2) Giving the user permission to launch Firestarter without the root password.
Open a terminal and type: sudo gedit /etc/sudoers
Add this line to the bottom: username ALL=NOPASSWD:/usr/sbin/firestarter
Save the file and close the terminal.
Note: Make sure “username” is your actual username ;-)
[/QUOTE]
The above step is a potential security hazard.
Automatix adds "gksudo firestarter" to system --> preferences--> sessions--> startup programs but if in somebody's case, that somehow does not happen, it should be easy enough to do the same manually.

---

### Post by SolidAndShade on 2006-02-01
The problem isn't that I have to input the password to get Firestarter to run when Gnome starts. The problem is that after I input the password, Firestarter crashes instead of running and I have to select it in the menu to get it to run. I'm wondering what might be causing Firestarter to crash after I type the password into the popup window.

---

### Post by arnieboy on 2006-02-01
please find possible solution in next post

---

### Post by arnieboy on 2006-02-01
[QUOTE=SolidAndShade]The problem isn't that I have to input the password to get Firestarter to run when Gnome starts. The problem is that after I input the password, Firestarter crashes instead of running and I have to select it in the menu to get it to run. I'm wondering what might be causing Firestarter to crash after I type the password into the popup window.[/QUOTE]
I have made a possible bugfix of the same in automatix version 5.1
In the meanwhile you can do the following:
go to system --> preferences -->sessions--> startup programs
and delete "gksudo firestarter"
and add **gksudo /usr/sbin/firestarter** 
now log out of gnome and log back in. 
Firestarter should start up just fine.

---

### Post by SolidAndShade on 2006-02-02
Firestarter works perfectly now. Thanks!

---

### Post by Orval on 2006-02-03
I used Automatix before and yesterday I used it to install Firefox 1.5. It worked great. You make life easy for us, Arnieboy. Thanks!

---

### Post by firingstone on 2006-02-05
this tool really help me a lot, thx for your work.
but recently I've got a problem with it, after I install amsn with the automatix.
the package manager told me that there was a broken package, which I found out was the totem-gstreamer, and I could not remove it totally cause that would remove the amsn as well. So what shall I do? Need help here

---

### Post by arnieboy on 2006-02-05
[QUOTE=firingstone]this tool really help me a lot, thx for your work.
but recently I've got a problem with it, after I install amsn with the automatix.
the package manager told me that there was a broken package, which I found out was the totem-gstreamer, and I could not remove it totally cause that would remove the amsn as well. So what shall I do? Need help here[/QUOTE]
if its removing just the amsn package (and nothing else), do the following:
```
wget http://public.omnipotents.com/kubuntu/amsn_0.95-1~neto1_i386.deb
sudo apt-get remove totem-gstreamer
sudo dpkg -i amsn_0.95-1~neto1_i386.deb
```

this will remove the broken package and reinstall amsn.

---

### Post by firingstone on 2006-02-05
Well,that helped after I do the
**sudo apt-get -f install**
to install two packages called 
i**mlib1**and **libpng10-0**
thank you:)

---

### Post by joplass on 2006-02-05
arnieboy or some other wizard please help!
I installed "avidemux" using "Automatix" but it does not start.  I get this message:

Cannot lunch entry:
Details: failed to execute child process
"avidemux2" (no such file or directoty)

Meanwhile, avidemux is listed in Applications => Sound & Video
I will appreciate some help.
Thanks!

---

### Post by arnieboy on 2006-02-05
[QUOTE=joplass]arnieboy or some other wizard please help!
I installed "avidemux" using "Automatix" but it does not start.  I get this message:

Cannot lunch entry:
Details: failed to execute child process
"avidemux2" (no such file or directoty)

Meanwhile, avidemux is listed in Applications => Sound & Video
I will appreciate some help.
Thanks![/QUOTE]
something failed to get downloaded.. most possibly the avidemux deb. let me look into this.
**EDIT: try the following:**
```
wget http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb
sudo dpkg -i avidemux-2.1.0-1_i386.deb
```

---

### Post by joplass on 2006-02-05
Thanks for the quick reply.  Here is the result of the first line.  It seems there no connection.

job@UbuntuServer:~$ wget [http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb](http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb)
--17:40:21--  [http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb](http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb)
           => `avidemux-2.1.0-1_i386.deb'
Resolving etotheipiplusone.com... 70.84.223.130
Connecting to etotheipiplusone.com|70.84.223.130|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:40:21 ERROR 404: Not Found.

job@UbuntuServer:~$

---

### Post by arnieboy on 2006-02-05
[QUOTE=joplass]Thanks for the quick reply.  Here is the result of the first line.  It seems there no connection.

job@UbuntuServer:~$ wget [http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb](http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb)
--17:40:21--  [http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb](http://etotheipiplusone.com/avidemux-2.1.0-1_i386.deb)
           => `avidemux-2.1.0-1_i386.deb'
Resolving etotheipiplusone.com... 70.84.223.130
Connecting to etotheipiplusone.com|70.84.223.130|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:40:21 ERROR 404: Not Found.

job@UbuntuServer:~$[/QUOTE]
yeah seems like the host brought it down.
I will have to look for an alternate host now.

---

### Post by vincebs on 2006-02-06
Hey there,

I tried using Automatix two weeks ago and it worked fine. But when I tried switching my Ubuntu interface to Spanish, and then tried to load Openoffice2, first OpenOffice failed, then I found that I could no longer shut down Ubuntu from the GNOME menu! When I click Shutdown, the whole GNOME interfaces becomes unresponsive, I can move my mouse around but nothing happens when I click anything. Is Automatix configured to handle localized versions of software? If not should I then make sure my default language is English before using Automatix?

Thanks for making this useful program,

Vince

---

### Post by arnieboy on 2006-02-06
[QUOTE=vincebs]Hey there,

I tried using Automatix two weeks ago and it worked fine. But when I tried switching my Ubuntu interface to Spanish, and then tried to load Openoffice2, first OpenOffice failed, then I found that I could no longer shut down Ubuntu from the GNOME menu! When I click Shutdown, the whole GNOME interfaces becomes unresponsive, I can move my mouse around but nothing happens when I click anything. Is Automatix configured to handle localized versions of software? If not should I then make sure my default language is English before using Automatix?

Thanks for making this useful program,

Vince[/QUOTE]
I dont think automatix handles localizations. sorry about that.

---

### Post by icetemplaire on 2006-02-06
Ok estoo, let we think im really really noob on linux, and i need AMULE whit KAD, that means I need Amule 2.1.0 And I have 72 hours of dreams because i coudn't install it. If i have ubuntu from 0 and i chose to install whit Automatix Amule, it will be the 2.1.0 version? 

Sorry for my english, i speak spanish :P

---

### Post by arnieboy on 2006-02-06
[QUOTE=icetemplaire]Ok estoo, let we think im really really noob on linux, and i need AMULE whit KAD, that means I need Amule 2.1.0 And I have 72 hours of dreams because i coudn't install it. If i have ubuntu from 0 and i chose to install whit Automatix Amule, it will be the 2.1.0 version? 

Sorry for my english, i speak spanish :P[/QUOTE]
automatix gives u the version of amule in the breezy repos (not the latest)

---

### Post by arnieboy on 2006-02-06
**[COLOR="DarkRed"]Major update:[/COLOR]**

[B]_Automatix updated to version 5.3_

New features in version 5.3 :

a) ATI cards proprietary/open source driver installation added. Drivers will be automatically chosen and installed based on ATI model number.
b) Automatix will now refuse to run if user has synaptic/update-manager/apt-get/dpkg running even if he/she runs these after Automatix starts. (hence one splash screen removed from the start :) )
c) two more AMSN deps added
d) avidemux package host 404 fixed. [/B] 
[COLOR="Blue"]
a big thanks to **[dfarning]("http://ubuntuforums.org/member.php?u=51350")** for writing the ATI drivers patch which I eventually edited to some extent and included in the Automatix codebase.[/COLOR]

---

### Post by arnieboy on 2006-02-06
[QUOTE=icetemplaire]Ok estoo, let we think im really really noob on linux, and i need AMULE whit KAD, that means I need Amule 2.1.0 And I have 72 hours of dreams because i coudn't install it. If i have ubuntu from 0 and i chose to install whit Automatix Amule, it will be the 2.1.0 version? 

Sorry for my english, i speak spanish :P[/QUOTE]
if u want the latest version of amule do the following **at your own risk:**
```
sudo gedit /etc/apt/sources.list
```
and add the following two lines at the end:
> deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
now save and exit and do the following:
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 70188C3B
gpg --armor --export 70188C3B | sudo apt-key add -
sudo apt-get update
```
now if u already have amule installed do
```
sudo apt-get upgrade
```
if u dont have amule installed do:
```
sudo apt-get install amule
```

---

### Post by joplass on 2006-02-07
[QUOTE=arnieboy]**[COLOR="DarkRed"]Major update:[/COLOR]**

[B]_Automatix updated to version 5.3_

New features in version 5.3 :

a) ATI cards proprietary/open source driver installation added. Drivers will be automatically chosen and installed based on ATI model number.
b) Automatix will now refuse to run if user has synaptic/update-manager/apt-get/dpkg running even if he/she runs these after Automatix starts. (hence one splash screen removed from the start :) )
c) two more AMSN deps added
d) avidemux package host 404 fixed. [/B] 
[COLOR="Blue"]
a big thanks to **[dfarning]("http://ubuntuforums.org/member.php?u=51350")** for writing the ATI drivers patch which I eventually edited to some extent and included in the Automatix codebase.[/COLOR][/QUOTE]

Man,
What can I say?  Amazing project and amazing work ethic.  I can't wait to get home tonight.
As always thanks a lot arnieboy!

---

### Post by joplass on 2006-02-07
arnie,
I have some trouble.  I installed the ATI driver but at reboot I got the blue screen of Xserver trouble.  I typed "sudo cp /etc/X11/Xorg.conf_backup_200602071658 /etc/X11/xorg.conf" but that did not take me anywhere.
After rebooting I still get the blue screen with this message: "Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

If click yes there is another long message.

Any idea as of what I can do here?

Thanks

---

### Post by arnieboy on 2006-02-07
yes two things:
1) from console go to /etc/X11/ and check for the actual backup file name.
now do 
```
sudo cp -f /etc/X11/xorg.conf_backup_whatever_data_and_time /etc/X11/xorg.conf
```


**the -f flag is crucial.**

now reboot.

2) tell me the name of your video card.

EDIT: I think the mistake that u did was that u typed upper case X instead of lower case x when typing the backup file name.

---

### Post by joplass on 2006-02-07
for some reason I get "cp cannot stat '/etc/X11/Xorg.conf_backup_200602071658'

Since I made that mistake by using X instead of x do you think I have a chance of getting my system back?

I was able to dig up this info on my video card: ATI Technologies Inc. Mobility M6 (9/11/2006)

---

### Post by arnieboy on 2006-02-07
[QUOTE=joplass]for some reason I get "cp cannot stat '/etc/X11/Xorg.conf_backup_200602071658'

Since I made that mistake by using X instead of x do you think I have a chance of getting my system back?

I was able to dig up this info on my video card: ATI Technologies Inc. Mobility M6 (9/11/2006)[/QUOTE]
u are getting the error because the file name you are typing (with the upper case X) does not exist.
yes indeed u do. just do:
```
sudo cp -f /etc/X11/xorg.conf_backup_200602071658 /etc/X11/xorg.conf
```
and reboot. **remember the lower case x**

ATI mobility is not on the list of cards that I covered in the ATI module.. I have to do some more digging. In the meanwhile u should be able to get your xserver working back again from the backup.

as of now **for your card**, Automatix installed the open source ATI drivers thats there in the breezy repositories. quite obviously those drivers did not work for your card.

---

### Post by shamrock_uk on 2006-02-07
[QUOTE=arnieboy]
a) ATI cards proprietary/open source driver installation added. Drivers will be automatically chosen and installed based on ATI model number.[/QUOTE]

Great idea, but unfortunately not working here. Installing with a 2.6.12.10 kernel gives me dependency problems (sorry, the xterm closed or I would post the exact message). Installation with the 2.6.12.9 kernel claims to have succeeded, but unfortunately it still doesn't work for me.

The X error message is:
> *snip*
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): cpuSpeedMHz: 0x0000067e
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xd8701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xd8701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xd1075000
(II) fglrx(0): [drm] mapped SAREA 0xd1075000 to 0xb7aee000
(II) fglrx(0): [drm] framebuffer handle = 0xd8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xd1075000 at 0xb7aee000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled


Any ideas on this one arnieboy?

Thanks for taking the trouble to produce this wonderful time-saving piece of software though - Ubuntu is firmly cemented as my number one distro because of it.  :)

---

### Post by arnieboy on 2006-02-07
alright guys.. too many people reporting problems on this one. I will take the "ATI  cards" module down... The patch seems to have problems.

also please visit [this thread]("http://ubuntuforums.org/showthread.php?t=126926")

---

### Post by arnieboy on 2006-02-08
The ATI cards function (which was supposed to automatically detect and install ATI drivers) was removed from The Automatix codebase because it did not work. However, the writer of the patch has rewritten a new patch which is open for **testing** in [this thread]("http://ubuntuforums.org/showthread.php?t=127157"). Those of you who are (not absolutely new to linux/ubuntu) and are willing to test this patch, please go ahead and do so. It will go a long way in automating ATI card installation in Automatix.

---

### Post by peterthewolf on 2006-02-08
Mplayer plugin to firefox once it starts playing I cannot do anything else on tinternet.
Mplayer seems to hog everything. 
Got rid of mplayer plugin via synaptic. 
Manually reinstalled realplayer but it did not ask for firefox location and did not install plugin to firefox. 
Since I like to listen to BBC radio while using my PC and mplayer effect not acceptable.
Any suggestions of how I may get real player to install. 2 or 3 months ago automatix used to install real player not mplayer plugin it would be nice to return to then.
Other than this moan automatix fixes everything else I want THANKYOU

---

### Post by arnieboy on 2006-02-08
are you using Firefox 1.5?
if yes do the following from terminal:

```
sudo rm -f /opt/firefox/mplayerplug-in-rm.xpt
sudo rm -f /opt/firefox/mplayerplug-in-rm.so
sudo apt-get install realplay
sudo cp /usr/lib/mozilla/plugins/nphelix.so /opt/firefox/plugins/
sudo cp /usr/lib/mozilla/plugins/nphelix.xpt /opt/firefox/plugins/
```

if you are using firefox 1.0.7
do the following:

```
sudo rm -f /usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.xpt
sudo rm -f /usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.so
sudo apt-get install realplay
```

---

### Post by arnieboy on 2006-02-08
[B]_Automatix updated to version 5.4.1_
New features in version 5.4.1 :

a) Automatix will now give the user the option to restore his/her original sources.list after finishing all installations (if it changes the sources.list at the beginning).

(The above should pacify a few more critics of Automatix.)

b) Firefox 1.5.0.1 installation added
c) Installation of latest version of amule from cvs
d) kde 3.5.1 repositories added 
e) installation of dcpp removed[/B]

---

### Post by nmsmith on 2006-02-09
I too got the firefox not loading problem on my laptop.

In the taskbar the "loading firefox" doodah disappears, but in a terminal I get:

```
nick@thrymr:~$ firefox
/opt/firefox/firefox-bin: error while loading shared
libraries: libstdc++.so.5: cannot open shared object
file: No such file or directory
nick@thrymr:~$

```

Can this be sorted?

---

### Post by arnieboy on 2006-02-09
[QUOTE=nmsmith]I too got the firefox not loading problem on my laptop.

In the taskbar the "loading firefox" doodah disappears, but in a terminal I get:

```
nick@thrymr:~$ firefox
/opt/firefox/firefox-bin: error while loading shared
libraries: libstdc++.so.5: cannot open shared object
file: No such file or directory
nick@thrymr:~$

```

Can this be sorted?[/QUOTE]
from terminal do the following:
```
sudo apt-get install libstdc++5
```
and restart firefox.

---

### Post by nmsmith on 2006-02-09
That works! Thank you for the speedy reply. Better than M$ 'customer relations' arnieboy!

---

### Post by abelethan on 2006-02-09
I have a question. I downloaded the newest automatrix the other night. After it was downloaded my system crashed. Now I cant log in. I get to the log in screen but when I attempt to log in i get an error saying I was logged in for less then 10 seconds. Is this a problem with automatix or could it be somthing else. I am new to this whole thing. Wondering what I should do and how. Thanks for any info

---

### Post by arnieboy on 2006-02-09
well just downloading automatix cannot crash your system my friend.. seems to be some other problem. did u install anything from automatix?

---

### Post by abelethan on 2006-02-09
yes after it crashed I used terminal to install most of it. Thought maybe that would help. But no luck and by the looks of things it all install fine.

---

### Post by arnieboy on 2006-02-09
Yeah well then it appears it wasnt automatix after all. it was your x server which in turn depends on whether u have the proper drivers installed for your video card. now tell me the exact make and model of your video card and I will redirect you to the correct forum for more help.

-Arnie

---

### Post by abelethan on 2006-02-09
Its a Nvidia GeForce FX 5500, plugged into PCI bus 1, device 4, function 0

---

### Post by arnieboy on 2006-02-09
[QUOTE=abelethan]Its a Nvidia GeForce FX 5500, plugged into PCI bus 1, device 4, function 0[/QUOTE]
alright here is what u need to do first of all..
```
sudo nano /etc/X11/xorg.conf
```
and find the entry "**nvidia**" under "Devices" and change it (nvidia) to "**nv**". 
save and exit. and restart your computer. u will have your x server back. once u get it back, come back and message me.

---

### Post by handy on 2006-02-10
Arnieboy,

I've been using Automatix, for a bit over 3 months.  Initially on a 64bit Breezy 5.10, (with no problems), then I thought I'd try 32bit, out of curiosity, after following a guide for installing Firefox 1.5 & my system had a meltdown!?  (ff 1.5 was not long out then).

Anyway, having updated to 5.4.1, last night, I then added a couple of the new things available on your appealing gourmet menu, one being Firefox 1.5!  Everything went without a hitch, & I would just like to make this oportunity to thankyou for the remarkable service that you are providing for so many in the Ubuntu community.

As you allready know I'm sure, us noobs come in all shapes & sizes, & due to the existance of Automatix, the initial learning curve is now not so steep, & because of that fact, many new users will stay with Ubuntu, who otherwise, would have bailed out & gone (back)to join the flock!  ***(No elitist spin intended!)*** Due to being overwhelmed by the initial intimidation, stress & frustration of learning a new OS.  (Not everyone thinks that's fun!)

Most people who use Automatix, would have no idea just how much time that you have dedicated to this project. Not just in developement, but in support.  You are a patient man, who I'm sure has had it tested more than once... :rolleyes:

**Arnieboy**, thankyou **VERY** much, you are helping to lower stress in the world!

& that's allways a good thing! :KS

---

### Post by simone.brunozzi on 2006-02-11
I agree with Handy: Arnieboy, your efforts are very much appreciated!

I suppose that Automatix could soon be a real part inside ubuntu itself (I mean: project leaders can think of including it in the next dapper release, for instance).

Self-glorification is not, however, what you Arnieboy really want (I suppose), but in any case be sure that your contribution is always exposed every time I use (or let others use) automatix.
I hope you like it. :-)

Thanks very much!

---

### Post by Kid G on 2006-02-11
Hi, 

My X server is not running since I installed Automatix. I have tried:

[INDENT]sudo cp /etc/X11/xorg.conf_backup_200602120130 /etc/X11/xorg.conf[/INDENT]

but i get an error message.

I have an Nvidia Geforce MX 420 video card.

Any ideas?

---

### Post by arnieboy on 2006-02-11
[QUOTE=Kid G]Hi, 

My X server is not running since I installed Automatix. I have tried:

[INDENT]sudo cp /etc/X11/xorg.conf_backup_200602120130 /etc/X11/xorg.conf[/INDENT]

but i get an error message.

I have an Nvidia Geforce MX 420 video card.

Any ideas?[/QUOTE]
try manually changing "nvidia" to "nv" in /etc/X11/xorg.conf
```

sudo nano /etc/X11/xorg.conf
```

---

### Post by Kid G on 2006-02-11
[QUOTE=arnieboy]try manually changing "nvidia" to "nv" in /etc/X11/xorg.conf
```

sudo nano /etc/X11/xorg.conf
```[/QUOTE]

Thanks - got ubuntu back!

---

### Post by abelethan on 2006-02-12
Hey I was trying to get Automatix on my sisters computer and it did. So I started installing the opera and firefox updates and what not and now I am getting an error of
"Failed to execute child process "firefox" (no such file or director)
I get this same error for opera. Also Gaim isnt connecting either. When I look under network settings it shows her wireless connection connected to comcast.net and all that jazz. Even ifconfig shows her running her wlan0 fine..So I am at a lose for what to do. Shes kinda mad at me for breaking her computer when all I was trying to do was add more content :rolleyes:
Anyhelp would be appraciated

---

### Post by arnieboy on 2006-02-12
[QUOTE=abelethan]Hey I was trying to get Automatix on my sisters computer and it did. So I started installing the opera and firefox updates and what not and now I am getting an error of
"Failed to execute child process "firefox" (no such file or director)
I get this same error for opera. Also Gaim isnt connecting either. When I look under network settings it shows her wireless connection connected to comcast.net and all that jazz. Even ifconfig shows her running her wlan0 fine..So I am at a lose for what to do. Shes kinda mad at me for breaking her computer when all I was trying to do was add more content :rolleyes:
Anyhelp would be appraciated[/QUOTE]
try reinstalling the options again from automatix. my guess is that the connection broke somewhere in between.

---

### Post by abelethan on 2006-02-12
[QUOTE=arnieboy]try reinstalling the options again from automatix. my guess is that the connection broke somewhere in between.[/QUOTE]


Ok just did that and said applications all installed fine. Didnt take but a min and still having the same error

---

### Post by arnieboy on 2006-02-12
alright message me on yahoo.

---

### Post by facefur on 2006-02-13
[QUOTE=abelethan]Hey I was trying to get Automatix on my sisters computer and it did. So I started installing the opera and firefox updates and what not and now I am getting an error of
"Failed to execute child process "firefox" (no such file or director)
[/QUOTE]


Please post the solution here - I have the same problem.  now I cna't reinstall because the internet connection at my hotel requires me to have a web browser to validate my connection, and I have no working web browser :o(  I had to dual back to winXP to send this message.  Apparently the install process makes FF 1.0.7 go away, and it's the only browser I had.

---

### Post by arnieboy on 2006-02-13
[QUOTE=facefur]Please post the solution here - I have the same problem.  now I cna't reinstall because the internet connection at my hotel requires me to have a web browser to validate my connection, and I have no working web browser :o(  I had to dual back to winXP to send this message.  Apparently the install process makes FF 1.0.7 go away, and it's the only browser I had.[/QUOTE]
try running
```
/opt/firefox/firefox
``` for firefox 1.5
if that does not work, run:
```
/usr/lib/mozilla-firefox/firefox
```
to run firefox 1.0.7

---

### Post by aseem_mal on 2006-02-13
Hi. I installed Automatix. At the end, it recommended me to let Automatix manage my repositeries. I let it do that.:( 

And now, whenever, I go to the Synaptic Package Manager, I get this Error Message::-k 
> 
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)



Please help.:???:

---

### Post by arnieboy on 2006-02-13
check two things:
1) u are connected to the net
2) do the following from terminal:
```
sudo apt-get update
```

---

### Post by anmlcrckrs on 2006-02-13
I've got a problem trying to install automatix, I just reinstalled Kubuntu because I messed up something and couldn't get my net to work at all but I could ping, anyway the net works great now but I have this problem when I try to install Automatix

```

david@bigkubu:~$ sudo dpkg -i automatix_5.4-2_i386.deb
Selecting previously deselected package automatix.
(Reading database ... 57910 files and directories currently installed.)
Unpacking automatix (from automatix_5.4-2_i386.deb) ...
dpkg: dependency problems prevent configuration of automatix:
 automatix depends on zenity; however:
  Package zenity is not installed.
dpkg: error processing automatix (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 automatix
david@bigkubu:~$

```

actually even though i've removed automatix it's still listed in my system folder, and when i run it, it gets the lists and then shuts down.  i'm lost.  

Any ideas?  I tried to run apt-get update but it fails half way through and says I should try and run apt-get update to fix the problem...

---

### Post by arnieboy on 2006-02-13
do the following:
```
wget http://kambing.vlsm.org/ubuntu/pool/main/z/zenity/zenity_2.10.0-0ubuntu1_i386.deb
sudo dpkg -i zenity_2.10.0-0ubuntu1_i386.deb
```

and restart automatix.

---

### Post by anmlcrckrs on 2006-02-13
after i try to install zenity i get 

```
avid@bigkubu:~$ sudo dpkg -i zenity_2.10.0-0ubuntu1_i386.deb
Password:
Selecting previously deselected package zenity.
(Reading database ... 57951 files and directories currently installed.)
Unpacking zenity (from zenity_2.10.0-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of zenity:
 zenity depends on libglade2-0 (>= 1:2.5.1); however:
  Package libglade2-0 is not installed.
 zenity depends on libgnomecanvas2-0 (>= 2.6.0); however:
  Package libgnomecanvas2-0 is not installed.
dpkg: error processing zenity (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zenity
david@bigkubu:~$ 
```

sorry during my first install none of this was an issue, why is it now?

---

### Post by arnieboy on 2006-02-13
u need to read the first post of the main Automatix thread. Installation of automatix on kubuntu is clearly outlined in that post.

---

### Post by facefur on 2006-02-14
[QUOTE=arnieboy]try running
```
/opt/firefox/firefox
``` for firefox 1.5
if that does not work, run:
```
/usr/lib/mozilla-firefox/firefox
```
to run firefox 1.0.7[/QUOTE]

Before I got to your suggestions, I tried just downloading the Firefox tar file to my pen drive, unpacked it to my Home folder, and told Automatix to install it again.  Worked like a charm - Firefox 1.5.0.1 is running fine.  That's one cool installation script you have produced.  Merci, grazie, gracias, danke, spasiba, etc.

---

### Post by kix on 2006-02-16
Very impressive tool.

I encountered a problem when Automatix tried to install Wine, the source drops the connection half way through the download.  Tried to manually install with apt, but the result is the same.

Not the fault of Automatix.

---

### Post by rogeriovinhal on 2006-02-17
I have installed Firefox 1.5 with Automatix. How do I upgrade to 1.5.0.1 now?

Is there a way to make auto-update work?

EDIT:
Nevermind, I tried this:
[http://ubuntuforums.org/showthread.php?t=128806](http://ubuntuforums.org/showthread.php?t=128806)
And worked like a charm...
Even the plguins work great still.

---

### Post by arnieboy on 2006-02-17
if u used the latest version of automatix to install firefox, u already have 1.5.0.1.
if u are sure u have 1.5 then refer to this howto:
[http://www.ubuntuforums.org/showthread.php?t=128806](http://www.ubuntuforums.org/showthread.php?t=128806)

---

### Post by yasenov on 2006-02-19
think about including these applications:

kleansweep
yakuake
krusader
clamav(with some GUI)
kiso(making .iso files very easy to mount,work ,etc.)

---

### Post by lukem on 2006-02-19
Any idea what could be causing this message when trying to install automatix?

:~$ wget [http://beerorkid.com/automatix/automatix_5.4-3_i386.deb](http://beerorkid.com/automatix/automatix_5.4-3_i386.deb)
--15:24:12--  [http://beerorkid.com/automatix/automatix_5.4-3_i386.deb](http://beerorkid.com/automatix/automatix_5.4-3_i386.deb)
           => `automatix_5.4-3_i386.deb'
Resolving beerorkid.com... 208.97.133.175
Connecting to beerorkid.com|208.97.133.175|:80... failed: Connection refused.

Thanks so much

lukem

---

### Post by lukem on 2006-02-19
The site is responding now.  Thanks :)
Will post results after upgrade
lukem

---

### Post by mssm on 2006-02-20
Hi, I am having trouble with opening adobe acrobat reader inside firefox. I have installed adobe acrobat and necessary plug-ins for firefox using automatix. I am not using firefox 1.5 but firefox 1.0.7. Whenever I click on a pdf file acrobat fails to launch complaining that it fails to intialize the plugin ewh.api. What is the problem?

---

### Post by arnieboy on 2006-02-20
[QUOTE=mssm]Hi, I am having trouble with opening adobe acrobat reader inside firefox. I have installed adobe acrobat and necessary plug-ins for firefox using automatix. I am not using firefox 1.5 but firefox 1.0.7. Whenever I click on a pdf file acrobat fails to launch complaining that it fails to intialize the plugin ewh.api. What is the problem?[/QUOTE]
please try doing the following:
```
sudo apt-get install acroread mozilla-acroread
```

---

### Post by mssm on 2006-02-21
[QUOTE=arnieboy]please try doing the following:
```
sudo apt-get install acroread mozilla-acroread
```[/QUOTE]

I did that. It's already installed. Output was :

Reading package lists... Done
Building dependency tree... Done
acroread is already the newest version.
mozilla-acroread is already the newest version.

I did it after closing firefox. When I restarted the firefox and tried to download a pdf file, it is still showing the same problem.

---

### Post by dweez on 2006-02-21
Sorry if this is not the place for the following but...

I'm having problems installing the Bittorrent clients through automatix.  Here are a couple screenshots of the autoscript terminal.  Automatix says everything gets installed though.  Everything else I've attempted to install via Automatix has worked great.

[[img]http://suprfile.com/src/2/s538u/Screenshot-autoscript-1.png[/img]](http://suprfile.com/get.php?id=s538u) [[img]http://suprfile.com/src/2/sfnwv/Screenshot-autoscript.png[/img]](http://suprfile.com/get.php?id=sfnwv)

---

### Post by arnieboy on 2006-02-21
[QUOTE=mssm]I did that. It's already installed. Output was :

Reading package lists... Done
Building dependency tree... Done
acroread is already the newest version.
mozilla-acroread is already the newest version.

I did it after closing firefox. When I restarted the firefox and tried to download a pdf file, it is still showing the same problem.[/QUOTE]
alright please update your file database by doing the following:
```
sudo updatedb
```
and then paste the results of 
```
slocate ewh.api
```

---

### Post by arnieboy on 2006-02-21
[QUOTE=dweez]Sorry if this is not the place for the following but...

I'm having problems installing the Bittorrent clients through automatix.  Here are a couple screenshots of the autoscript terminal.  Automatix says everything gets installed though.  Everything else I've attempted to install via Automatix has worked great.[/QUOTE]

alright there are two reasons for this problem:
1) If u are sure u have retained Automatix's sources.list, do the following:
```
sudo apt-get update
``` and then run automatix to install stuff.
2) The azureus version that Automatix installs is no longer present in the debian pool. It seems they have simply removed it and replaced it with higher versions. I will update the Azureus version in the next release of Automatix, sometime later today or tomorrow.

---

### Post by KermitJr on 2006-02-21
Arnieboy,

Great stuff, as always.  What about adding the Folding@Home scripts from the wiki?

Thanks,
KermitJr

---

### Post by mssm on 2006-02-21
[QUOTE=arnieboy]alright please update your file database by doing the following:
```
sudo updatedb
```
and then paste the results of 
```
slocate ewh.api
```[/QUOTE]

Results:

/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/ewh.api
/usr/lib/firefox/plugins/ewh.api

---

### Post by arnieboy on 2006-02-21
[QUOTE=mssm]Results:

/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/ewh.api
/usr/lib/firefox/plugins/ewh.api[/QUOTE]
everything seems to be in order.. is Acrobat reader opening independently? have u tried that? its in applications --> Office

---

### Post by mssm on 2006-02-21
[QUOTE=arnieboy]everything seems to be in order.. is Acrobat reader opening independently? have u tried that? its in applications --> Office[/QUOTE]

Yes, it's opening independently. I can read pdf files from my folder. I have flashblock turned on in firefox. Is it interfering somehow? I remember I could open acrobat inside firefox few months back. I started having this trouble recently.

---

### Post by arnieboy on 2006-02-21
yeah well that might be causing problems.. I remember installing adblock once in firefox and after that hell broke loose.. it got in everywhere and started interfering with all plugins. even deleting the user directory did not change much.

---

### Post by mssm on 2006-02-21
[QUOTE=arnieboy]yeah well that might be causing problems.. I remember installing adblock once in firefox and after that hell broke loose.. it got in everywhere and started interfering with all plugins. even deleting the user directory did not change much.[/QUOTE]

I see. I have uninstalled adblock, fasterfox and flashblock from firefox but still I am having trouble. Has anybody else faced the problem?

[COLOR="Red"]Update :[/COLOR] I am running acrobat under firefox  with adblock, flashblock, fasterfox turned on, in my office under FC2 without any problem.

BTW : A completely different thing, a request actually : can we have banshee in automatix?

---

### Post by arnieboy on 2006-02-22
[B]_Automatix updated to version 5.5_

New features in version 5.5:[/B]
a) Installs Mozilla-Thunderbird 1.5 **(US-only version)**(**no support for non-US-english language packs and enigmail**)
b) Fixes Gnome sound related issues (ALSA and ESD config) **(needs a restart)**

---

### Post by jackwhite on 2006-02-23
Hi Arnieboy,

I've just used automatix to install mozilla versions of firefox and thunderbird.
i keep my rofiles on an encrypted hard drive and thought i could use it by setting up with firefox -p

when I tried this though the result i get in terminal is:
```
run-mozilla.sh: Cannot execute /opt/firefox/firefox-bin.pure.

```

Is it possible to use my old profile in the new firefox?

(thunderbird seems to use my profile by default which is cool!)

BTW thanks for all the awesome work you've done on automatix. I used it when i first installed breezy and its great to see that its still being improved)

Regards,

jack white

---

### Post by arnieboy on 2006-02-23
[QUOTE=jackwhite]
Is it possible to use my old profile in the new firefox?[/QUOTE]
no u shdnt attempt it. u can manually copy files like bookmarks, cookies etc though. reinstall all the extensions.

---

### Post by jackwhite on 2006-02-23
ok cool.. I guess my next question is whether or not its possible to creat a new profile that i can copy everything to? (i use a dual boot machine cos i need windows for some work stuff)

i guess i should have researched this first!

---

### Post by arnieboy on 2006-02-23
do the following:
close all firefox windows and do the following from terminal
```
mv ~/.mozilla ~/.mozilla_new_backup
```
now restart firefox.
a new profile will be created.
to copy your bookmarks over to the new profile do the following:
```
cp -f ~/.mozilla_new_backup/firefox/*default/bookmarks.html ~/.mozilla/firefox/*default/bookmarks.html
```

---

### Post by sohailubuntu on 2006-02-24
I was installing Automatix and everything was going fine until it asked to plug in USB game pad, and I no longer wanted this option so I clicked cancel. And it stopped altogether- so how do I restart where I left off?  Thanks a lot

---

### Post by Sokraates on 2006-02-24
[quote=arnieboy]no u shdnt attempt it. u can manually copy files like bookmarks, cookies etc though. reinstall all the extensions.[/quote] 
If you absolutely want to be on the safe side, do as arnieboy suggests. Firefox 1.5 needs to adapt old profiles a bit, so you **can not go back** using those with 1.0.x. If you want to try out, whether everything works out of the box for you, do the following:

1) Backup you old profile by making a **copy**:
```
cp ~/.mozilla ~/.mozilla_new_backup
``` [I]@ arnieboy: Doesn't Automatix do an automatic backup?

[/I]2)Install Firefox 1.5 and start it.

It works flawlessly in about 97% of all upgrades.

If you have any problems, you can simply delete the "~/.mozilla"-folder. A new profile will be created and you need to manually copy your backedup files.

Extensions or themes not working is no error but indended. Firefox will search for new, compatible versions.

---

### Post by lukem on 2006-02-26
fantastic - thank you so much.  everything went well.

---

### Post by coldrick on 2006-02-28
I've upgraded Firefox to 1.5.0.1 using the Fireupdate script referred to above. That worked fine.

Then I installed the latest (5.5?) Automatix, and installed ThunderBird 1.5. Coupla problems:

1) Well, not really a problem, but why is it calling itself "Mail/News" instead of Tbird?

2) It came with Plaxo installed: again, not a problem really, I uninstalled it.

3) This *is* a problem: hyperlinks in emails do *not* get sent to Firefox when clicked.

Suggestions??

Regards,
David

---

### Post by coldrick on 2006-02-28
Oops - forgot to say: Ubuntu Breezy

---

### Post by arnieboy on 2006-02-28
[QUOTE=coldrick]3) This *is* a problem: hyperlinks in emails do *not* get sent to Firefox when clicked.[/QUOTE]
solve this the following way:
in thunderbird:
go to edit --> preferences --> Advanced --> General --> Config editor
and look for the following 2 options:
> [B]network.protocol-handler.app.https
network.protocol-handler.app.http[/B]

double click on each of them and change their values from **x-www-browser** to **firefox**
close config editor and preferences.
now all hyperlinks will open in firefox.

---

### Post by coldrick on 2006-02-28
Worked fine! Thanks, arnieboy.

Regards,
David

---

### Post by Phlegethon on 2006-03-02
The distribution thread ([http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)) seems to be gone. When I click on the link, I get this error message:
> No Thread specified. If you followed a valid link, please notify the administrator

---

### Post by dgrafix on 2006-03-02
Your auto thingy worked great last time, nice work
Now i had to reset everything up after getting a new motherboard and
your link doesnt work, also, how do i get it to run the alsa fix?

---

### Post by arnieboy on 2006-03-02
the new link is:
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by mcwtlg on 2006-03-02
Well Arnieboy, I made the big jump to OO 2.0, FF 1.5.0.1, and T-Bird 1.5 via Automatix and I can saw that it all worked as expected.

Thanx for helping people like me (trying to dump Windoze for good) to join the Linux army.  I am 98% linux (I still cannot synch my Tungsten E properly and I have 2 windows proggies my wife and I both love that will not run properly in WINE) and love it.  All my surfing, media, web publishing, e-mail, word processing, and shreadsheets are handled by Ubuntu.

Not bad for a 40 year old who dropped out of college :).

I am as excited about Linux as I was when I first started working on hardware in the early Windows days.

---

### Post by guleblanc on 2006-03-03
[QUOTE=arnieboy]look just above the "quote" button on the first post (bottom right corner) on [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)[/QUOTE]

Hi.  I'm very interested in installing this, but the link above does not work for me.  I get an error message which tells me "no thread specified".  Is it possible that this thread has timed out in the forum somehow?

thanks.

---

### Post by arnieboy on 2006-03-03
link fixed. 
-Arnie

---

### Post by screamingindigital on 2006-03-04
arnie....love the program.  I screwed up wine and I cannot get it to run.  How do I uninstall it so I can configure it again?  Also, do you know where the .wine folder is located?  Thanks for the help.

**EDIT**

nevermind...found this>> [http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)

---

### Post by Linuxrising on 2006-03-06
Very Helpful Thanks

---

### Post by prime on 2006-03-06
dude you rock. thanks.

---

### Post by nmatheis on 2006-03-09
Hello

Thanks for providing such a great service to the Ubuntu community!!!  

After running Automatix, I have a few questions.  

1. SMEG only opens now if I open it with the sudo command.  How can I change it back to opening with the sudo command?

2. Opera and Avidemux don't show up in their respective submenus (ie, Internet and Sound & Video, respectively).  When I open SMEG, I can see that they are indeed there and their boxes are checked - I can't see them when I open the menu on my desktop, though.

3. I ran the Gnome Audio Configuration (#41 - Fixes Gnome sound related issues).  If I want to install the Kubuntu-desktop (So I can choose between Gnome and KDE at login) do I need to reverse that configuration?

Thanks!
Nikolaus

---

### Post by arnieboy on 2006-03-09
install the latest version of automatix (5.6) and install avidemux and opera. The menu items should show up this time. A few permission-related bugs had crept into the last few versions.
about smeg:
from terminal do the following:
```
smeg
```
and paste the results.

---

### Post by nmatheis on 2006-03-09
Damn, that was fast!  I've got Synaptic running to get me some extra packages I like to have and was thinking that they might be some good packages to add to Automatix (if you think other people would like them, too).  A few I find to be essential are:

1. Soundconverter (I rip to FLAC and then convert to OGG with this app)

2. mp3gain + vorbisgain (nice console-based apps for replaygain-ing mp3 & ogg files - my Rockbox-ed IHP-120 supports replaygain, so I find this very useful)

Others might find these useful, as well - especially Soundconverter.

I'll get the new Automatix going after Synaptic is done.  Btw, do I have to uninstall the old Automatix before I get the new one going?

Thanks!
Nikolaus

---

### Post by arnieboy on 2006-03-09
[QUOTE=nmatheis]Btw, do I have to uninstall the old Automatix before I get the new one going?
Nikolaus[/QUOTE]
nopes.

---

### Post by nmatheis on 2006-03-09
[QUOTE=arnieboy]install the latest version of automatix (5.6) and install avidemux and opera. The menu items should show up this time. A few permission-related bugs had crept into the last few versions.
about smeg:
from terminal do the following:
```
smeg
```
and paste the results.[/QUOTE]

```
nikolaus@ubuntu:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init_ _
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNot OnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNot OnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntr ies
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __ini t__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse
    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/dvdrip.desktop'

```

BTW, just ran Automatix 5.6 with Opera, Avidemux, and Mercury Messenger selected but they weren't added to my menu.  I can still see them inside smeg (after I sudo it).  I also noticed that DVD-Rip isn't being auto-added to the menu.  It's in smeg but not in the menu when I go into it from the panel.  After the Automatix 5.6 run, I noticed Mercury Messenger was added to the "Other" menu but Opera and Avidemux and DVD-Rip weren't there.  So I did "killall gnome-panel".  MM was then added to my "Internet" menu.  Still no Opera, DVD-Rip, and Avidemux in the menu.

And still owndering if I want to add Kubuntu-desktop, so I need to undo the Gnome Sound Fix thing?

Thanks again!
Nikolaus

---

### Post by arnieboy on 2006-03-09
alright try this from terminal:
```
sudo chmod 644 /usr/share/applications/dvdrip.desktop
```
now run smeg again
if it runs fine, log out of gnome and log back in. did u try installing opera and avidemux again from Auitomatix 5.6? if not, do it and u should see both menu items.

---

### Post by arnieboy on 2006-03-09
[QUOTE=nmatheis]And still owndering if I want to add Kubuntu-desktop, so I need to undo the Gnome Sound Fix thing?[/QUOTE]
NO u dont have to.

---

### Post by nmatheis on 2006-03-09
Ran that command, logged out, and back in.  DVD-Rip is now in the menu.  

When I ran Autoamtix 5.6, I did check Opera and Avidemux for install - but they didn't appear in the menu after the Automatix run and aren't there after logout / login.  And smeg still requires sudo to open.

Nikolaus

---

### Post by arnieboy on 2006-03-09
ok opera and avidemux (if they have been installed) can be run as follows:
```
opera
```
```
avidemux2
```
Please try pasting the results from terminal for the following command again 
```
smeg
```

---

### Post by nmatheis on 2006-03-09
```
nikolaus@ubuntu:~$ smeg
Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init_ _
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNot OnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNot OnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntr ies
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __ini t__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse
    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/avidemux.desktop '
```

Oh yeah, I know I can run them with Alt+F2 and then opera or avidemux2.   just think it's really strange that I can see them with smeg but can't see them in the actual menu!  And it's strange that I can't get into smeg without being su.  Hopefully this will be easy to resolve.  Still the easiest way to get up & running :)

---

### Post by arnieboy on 2006-03-09
alright do the following from terminal:
```
sudo chmod 644 /usr/share/applications/opera.desktop
sudo chmod 644 /usr/share/applications/avidemux.desktop
```
now run smeg again. If it still fails to run, run it from terminal again and paste the errors here.

---

### Post by nmatheis on 2006-03-09
[QUOTE=arnieboy]alright do the following from terminal:
```
sudo chmod 644 /usr/share/applications/opera.desktop
sudo chmod 644 /usr/share/applications/avidemux.desktop
```
now run smeg again. If it still fails to run, run it from terminal again and paste the errors here.[/QUOTE]

BINGO!!!  Got the permissions changed, and smeg started up from the menu as it should. 

Two more things, though...

1. Should Avidemux have an icon in the menu.  I'm not getting an icon for it, and there isn't one labeled Avidemux in /usr/share/pixmaps.
[b]Edit: I see avidemux.png but when I select it for the icon, it doesn't fill in the icon box in smeg or in the menu.  Any idea?
Another Edit: Opened avidemux.png in Gimp as su and resaved it as avidemx.xpm in /usr/share/pixmaps.  I then set this as the icon, and now it shows up.[/b]

2. Should Wine show up in the menu.  Noticed that it's not there, either.

Thanks so much for the help in tracking down the problems I was having.  You're a great asset for the Ubuntu community !!!

Nikolaus

---

### Post by arnieboy on 2006-03-09
[QUOTE=nmatheis]2. Should Wine show up in the menu.  Noticed that it's not there, either[/QUOTE]
wine does not have a menu entry. It does not need one either because its just a command line wrapper for running windows programs. when u install a windows program through wine, you can create a menu entry for that with smeg.

---

### Post by nmatheis on 2006-03-09
Thanks again for the tip!  I haven't used Wine before but think it'd be handy for running Foobar2k in Linux.  Got the Wine webpage loaded up so I can learn how to use it.
Nikolaus

---

### Post by David Valentine on 2006-03-10
I, too, am getting the following error when attempting to open a .pdf document in firefox 1.501:  > Adobe Reader:  There was an error while loading the plug-in 'ewh.api'. The plug-in failed to initialize.The output resulting from ```
sudo updatedb
slocate ewh.api
```is> /usr/lib/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/ewh.api
Any ideas?

Thanks again, by the way, for doing such an amazing job of supporting Automatix.

---

### Post by coldrick on 2006-03-12
Arnieboy, have you changed your mind and decided to support a Dapper version of Automatix (we all hope!)?

Regards,
David

---

### Post by Termina on 2006-03-13
Now that more and more amd64 users are turning to Ubuntu, is there going to be a 64-bit version?

Is there a source anywhere, so we can compile it ourselves?

---

### Post by Offthedeepend on 2006-03-13
Hi,
Thanks for Automatix - it's a great tool for a first time Linux user like me.  But I'm having a problem with very slow downloads so hope you can help me figure it out.  

I've installed Ubuntu 5.10 on a Dell i9300 laptop (dual boot with WinXP) and I'm trying to use Automatix to install various extras.  My ADSL connection is reasonably fast, and browsing the internet with firefox is fine, pages load quick.  But with Automatix, although the script seems to be working, it is downloading files extremely slowly, mostly less than 5kb/s. I can't leave my laptop permanently connected to the internet so I have had to cancel Automatix and restart several times, which seems to be OK (??).  But so far, it has taken me a couple of days just to get half way through the list.

I'm a complete beginner with Linux so am not sure whether I need to adjust some configuration settings or something else.  I've read in some threads about about slow repositories, etc and I suspected it might be some sort of server overload, but dunno.  Seems too slow even for that. 

Any ideas?  
Thanks.

---

### Post by Ramon on 2006-03-16
A bit of topic : [http://os.newsforge.com/article.pl?sid=06/03/12/2010242&from=rss]("http://os.newsforge.com/article.pl?sid=06/03/12/2010242&from=rss")

=D>

---

### Post by loafula on 2006-03-16
how about adding a script to optionally update the current running version of automatix from within the program itself?

---

### Post by David Valentine on 2006-03-16
For anyone who gets the following error when attempting to load a .pdf file in Firefox 1.5 after the Automatix install:> Adobe Reader: There was an error while loading the plug-in 'ewh.api'. The plug-in failed to initialize.All you need to do is uninstall and re-install the acroread plug-in using the synaptic package manager.

---

### Post by fishfillet on 2006-03-16
Thanks David, you're right.

Now I can download and view pdf files :)\\:D/

---

### Post by seanmc42 on 2006-03-16
Am I the only one getting a "failed: Xonnection refused" from beerorkid ???
Has automatix moved?

---

### Post by seanmc42 on 2006-03-16
Ah - methinks it got /.ed

---

### Post by seanmc42 on 2006-03-17
Well done!
Gots me lots o' crap installed now!

---

### Post by tseliot on 2006-03-18
[QUOTE=Offthedeepend]Hi,
Thanks for Automatix - it's a great tool for a first time Linux user like me.  But I'm having a problem with very slow downloads so hope you can help me figure it out.  

I've installed Ubuntu 5.10 on a Dell i9300 laptop (dual boot with WinXP) and I'm trying to use Automatix to install various extras.  My ADSL connection is reasonably fast, and browsing the internet with firefox is fine, pages load quick.  But with Automatix, although the script seems to be working, it is downloading files extremely slowly, mostly less than 5kb/s. I can't leave my laptop permanently connected to the internet so I have had to cancel Automatix and restart several times, which seems to be OK (??).  But so far, it has taken me a couple of days just to get half way through the list.

I'm a complete beginner with Linux so am not sure whether I need to adjust some configuration settings or something else.  I've read in some threads about about slow repositories, etc and I suspected it might be some sort of server overload, but dunno.  Seems too slow even for that. 

Any ideas?  
Thanks.[/QUOTE]
Arnie can't do anything about that. Automatix uses certain repositories (which are unofficial) which sometimes are slow.

---

### Post by madKoka on 2006-03-22
General problems:

After running Automatix I can no longer run Firefox. Automatix log indicated that Firefox 1.5 was installed, but both the menu (Applications>Internet>Firefox) and quick launch button produce an error message when trying to launch Firefox. Where does Automatix put the newer version of Firefox? I was able to find firefox.sh under usr/lib, but it opens 1.0.4 not 1.5.

I can't seem to figure out how to play mp3 files. I installed multimedia codecs and aud-dvd codecs that come with Automatix, but still can't play mp3s in Totem. Is there some config that I'm missing?

Thanks in advance,

---

### Post by arnieboy on 2006-03-22
make sure u have Automatix 5.6.2 installed 
do the following from terminal to manually install Firefox 1.5
```
sudo apt-get install libstdc++5
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/linux-i686/en-US/firefox-1.5.0.1.tar.gz
sudo rm -rf ~/firefox
tar xzf firefox-1.5.0.1.tar.gz
sudo rm -rf /opt/firefox
sudo cp -rf ~/firefox /opt/
sudo cp -f /usr/lib/mozilla-firefox/plugins/* /opt/firefox/plugins/
sudo cp -f /usr/lib/mozilla/plugins/* /opt/firefox/plugins/
sudo rm -f /opt/firefox/plugins/libtotem_mozilla.*
sudo rm -f /opt/firefox/plugins/libjava*
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
sudo touch /opt/firefox/extensions/talkback@mozilla.org/chrome.manifest
rm -f ~/firefox-1.5.0.1.tar.gz 
rm -rf ~/firefox 
gconftool-2 -t str -s /desktop/gnome/url-handlers/http/command "firefox %s"
gconftool-2 -t str -s /desktop/gnome/url-handlers/https/command "firefox %s"
```

---

### Post by arnieboy on 2006-03-22
for multimedia and audio dvd codecs do the following (provided u allowed automatix to set your sources.list):
```
sudo apt-get install totem-xine gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-faac gstreamer0.8-faad libxvidcore4 lame sox ffmpeg mjpegtools vorbis-tools mpg321
gst-register-0.8
sudo apt-get install w32codecs libdvdcss2 libdvdread3 libdvdnav4 libxvidcore4
```

---

### Post by Dragineez on 2006-03-24
Have I gone blind or lost my mind? Or is there no longer a download link for Automatix?

---

### Post by arnieboy on 2006-03-24
```
wget http://beerorkid.com/automatix/automatix_5.7-2_i386.deb
sudo dpkg -i automatix_5.7-2_i386.deb
```

---

### Post by mailmaldi on 2006-03-24
a very basic doubt...

after a fresh breezy installation, what do u recommend i do first...

install automatix & the packages i want & then do apt-get dist-upgrade

or immed after installation i do an apt-get dist-upgrade & only after that i use automatix to install new packages...

---

### Post by arnieboy on 2006-03-24
[QUOTE=mailmaldi]a very basic doubt...

after a fresh breezy installation, what do u recommend i do first...

install automatix & the packages i want & then do apt-get dist-upgrade

or immed after installation i do an apt-get dist-upgrade & only after that i use automatix to install new packages...[/QUOTE]
you probably dont mean dist-upgrade
if u mean sudo apt-get upgrade, yes then do that first and then run automatix.

---

### Post by ububaba on 2006-03-24
[QUOTE=ameerirshad]1,2,3 testing, running and enjoying it! Very nice tool, easy and fast!

thnx[/QUOTE]

I don't think it is a bright idea to use a serious forum like this 
for religious propaganda.

---

### Post by abloylas on 2006-03-29
Hi!
I just tried Automatix yesterday and it seems like a really nice script. Thanks! For some reason the quicktime plugin for firefox 1.5 doesn't work, though. And I get no sound with the flash plugin. I'll have to look into that later.

Have you considered creating a home page for Automatix? On Sourceforge maybe, or something? Now the info seems scattered in the ubuntu forums. There are also some broken links laying around to forums that don't exist anymore. It would be nice to be able to follow the development of Automatix in one place.

Automatix is still a bit Gnomecentric. Are there any plans for more Kubuntu stuff and more development in general? Dapper? 64 bit?

How about joining forces with EasyUbuntu? And maybe finetune the repositories countrywise like source-o-matic?

I firmly believe that it's tools like this that are going to put Linux on the desktop. Just a tiny bit more polish.

Oh, one more thing. Could Automatix get Firefox to open external movie viewers for wmf-files, say Totem player or something? Klicking on some movie links now just offers you to save them to disk. I think mozplugger is supposed to do something like that, but installing it seems to require uninstalling Mplayer.

abloylas

---

### Post by Papa-san on 2006-03-29
I have tried installing frostwire for the last two days. I (Automatix) have/has not been able to connect to the sourceforge server for this program. Twice now the requests have timed out twenty times, and Automatix gives up. I know it is working, because I got the java install OK, and the other choices I installed. It just seems like this one program ?!? Am i doing something wrong, or is the server that busy?

BTW... I love the way this works.... Kudos to the developers

It looks like it is trying to connect to a different IP than the one it 'resolved' ? resolves 69.9.164.2 and tries to connect to 169.9.164.21:80
(Please remember I really don't know much about all this stuff.) This is the beauty of Automatix... It works for dummies like me!

---

### Post by arnieboy on 2006-03-29
[QUOTE=Papa-san]I have tried installing frostwire for the last two days. I (Automatix) have/has not been able to connect to the sourceforge server for this program. Twice now the requests have timed out twenty times, and Automatix gives up. I know it is working, because I got the java install OK, and the other choices I installed. It just seems like this one program ?!? Am i doing something wrong, or is the server that busy?

BTW... I love the way this works.... Kudos to the developers![/QUOTE]
the frostwire link should be working in version 5.7.3 
which version are u using?

---

### Post by Papa-san on 2006-03-29
> the frostwire link should be working in version 5.7.3
which version are u using?

Um.... I don't know... How do I check? 

refer to:
> This is the beauty of Automatix... It works for dummies like me!
:-)

---

### Post by arnieboy on 2006-03-29
[QUOTE=Papa-san]Um.... I don't know... How do I check? 

refer to:

:-)[/QUOTE]
paste the results of:
```
cat /usr/local/automatix/autoscript | grep "Automatix version"
```

---

### Post by Papa-san on 2006-03-29
> the frostwire link should be working in version 5.7.3
which version are u using?

Ummm... I don't know... how do I check?

(please refer to my post about dummies like me!)

:D    OOPS didn't see it post... sorry

version 5.6.2... nuff said...
(that's a quick new version!)

---

### Post by Van on 2006-04-06
Automatix the best thing to happen since Ubuntu!

---

### Post by domino on 2006-04-06
I'm having a issue with Thunderbird 1.5 installed with this script. It seams that it will not use Firefox when opeing links from within the received mail. I uninstalled 1.5, installed 1.07, and it opens links using Firefox. I'll try to manually install version 1.5 and see wha happens.

---

### Post by monomaniacpat on 2006-04-12
Is there a way to uninstall programs that have been installed by automatix through automatix itself? As I've installed firestarter and now it asks me for my password *every* time I log in, even having uninstalled the program. It's very annoying - ideas?

---

### Post by arnieboy on 2006-04-12
[QUOTE=monomaniacpat]Is there a way to uninstall programs that have been installed by automatix through automatix itself? As I've installed firestarter and now it asks me for my password *every* time I log in, even having uninstalled the program. It's very annoying - ideas?[/QUOTE]
remove the firestarter entry from System --> Preferences --> Sessions --> Startup programs

---

### Post by mishranurag on 2006-04-12
Will this be available for Dapper Drake soon?
Anurag

---

### Post by monomaniacpat on 2006-04-12
[QUOTE=arnieboy]remove the firestarter entry from System --> Preferences --> Sessions --> Startup programs[/QUOTE]

Thanks!

---

### Post by Pilsner on 2006-04-13
Hey folks.

Automatix works very good for me except the installation of the Mercury Messenger software.
There comes a message "Connecting to voxel.dl.sourceforge.net" and it keeps retry connect to that server but never success.
Here is a screenshot:
[IMG]http://img233.imageshack.us/img233/5251/automatixmercury8tm.png[/IMG]
1. Has Mercury path at server been changed?
2. Is it something else?

I have also installed it manually but I am not sure if it installs in same ways as automatix does.

Happy Easter :KS :KS

---

### Post by surfgeek on 2006-04-14
Just getting 404 no reply:-k

---

### Post by oltix on 2006-04-14
Automatix is great!

But I have a problem. I have installed gftp, but i don't see it anywhere!! 

Some  help?

---

### Post by oltix on 2006-04-15
???!

---

### Post by Sokraates on 2006-04-15
Some apps don't add an icon to the menu. I don't have gftp (or GNOME, for that matter) so I can't say, if this is the case with gftp.

So I suggest the following: First open a terminal and type
```
gftp
``` 
to see, whether the app has been installed.

If yes, use SMEG or the menu-editor of your choice to create an icon.

---

### Post by polo_step on 2006-04-15
[FONT="Courier New"]Be advised that the download URL for Mercury Messenger in the script

[http://voxel.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb](http://voxel.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb)

is stone dead.

For the last several eternities, Automatix has been retrying it, with no result.

Will Automatix ever get the message, abort that and move on to the next part of the installation, or should I just hit reset and blow the whole thing off?  It's up to the seventh retry already.

](*,) 

Thanks.

[Later:]  Yeah, the script eventually just packed it in and curled up its toes.

OK, so what next?  Automatix didn't get to finish its thing, so where am I now and what do I do about it?

I've rebooted, but don't really have any clear idea of where I stand with this new 5.10 install (which actually seems flawless so far, with the exception of that dead link in Automatix...man, 5.10 is so much better here than 5.04 was!).

As always, thanks for any help![/FONT]

---

### Post by arnieboy on 2006-04-15
do the following:
```
gedit /usr/local/automatix/autoscript
```
and change the word "**voxel**" to "**easynews**".
save and exit and reinstall mercury from Automatix.

---

### Post by polo_step on 2006-04-15
[FONT="Courier New"]OK, cool...but where am I relative to the script?

Is everything listed in the menu prior to the Mercury Messenger thing installed OK and everything after it still to go?

BTW, I have to say that this is about twelve lightyears better than my previous Ubuntu experience with 5.04 on the identical machine.

Even given the aborted script, I am much further along with a 100% functional, bug-free setup than I was after FIVE MONTHS of futilely screwing around with 5.04!  

So far, every nosebleed I had with 5.04 is simply **gone**.  Stuff actually works for a change, hardware and software.  Every dang thing, clear down to my proprietary Microsoft ergo keyboard's nutty special keys.

This is PROGRESS!

Many thanks for Automatix.  It installed a ton of stuff I wanted, but just didn't have the ambition to screw with installing myself.  [/FONT]

---

### Post by dweez on 2006-04-17
Just curious, what version of Firefox comes with the latest version of Automatix (Firefox 1.5.0.2 was just released).

---

### Post by dexter on 2006-04-18
Automatix is a great program, it installs a lot of things i used to do manually but like a 100 times faster :).

Yesterday i used it once again and one of the things i installed were the MS TTF Fonts, however i don't like it that much, text isn't as "clear" as it used to be. How do I get rid of them ?

---

### Post by punchy on 2006-04-19
Hello,

I did a cursory look before posting this question, but I may have missed the information somehwere else. Sorry if thats the case.

My question:
I'm running Dapper. And I'd love to have Automatix going for it. Whats the status on that ?

Thanks much!
Punchy

---

### Post by souled on 2006-04-20
There is an update for Firefox 1.0.8. Will updating to this version mess up my 1.5 install (which was installed through Automatix)?

---

### Post by arnieboy on 2006-04-20
no

---

### Post by Sokraates on 2006-04-20
Not if you use different profiles. The profile you use for FF 1.5 will not work or even break FF 1.0.8. Best don't even start 1.0.8 and keep using 1.5.

Installing 1.0.8 through the repos will delete the mozilla-icons, if you have installed them, though.

---

### Post by Corvair on 2006-04-23
Hello Arnieboy and everybody else,

Thanks for the great work you have done with Automatix and for all the support you are giving. I only wish I had discoverred it before , it would have saved me a lot of frustrations, as I was ready to give up. It has helped me install a lot of stuff and to correct problems I have caused myself through my ignorance.
I have been able to recover Thunderbird by installing TBird 1.5 and also my address book. The problem remaining is that I failed installing the new version Firefox, 1.5 and I don t have access to Firefoxx anymore.
I am using Mozilla Webb Browser.This allows me to be able to use the Webb.
I am using Ubuntu 5.1.
I have 3 broken packs:
1- Thunderbird  -enigmail
2-    "             -offline
3-    "             -locale-fr
Synoptic refuses to uninstall them, which has to be done, I believe before I can do anything else. Also I want to install a Canadian Bilingual keyboard and synaptic does not give it to me although it shows the correct layout.

I get error exit status 1
I have a limited knowledge and would like some help.  [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

Thanks for your listening.
Claude

---

### Post by Corvair on 2006-04-23
I forgot, the 3 broken packs are all mozilla-thunderbird.
Claude

---

### Post by Corvair on 2006-04-24
Hello Arniboy,
I thought this might help you to know what can be done.
Claude  (Corvair)

claudecor@ubuntu:~$ sudo ap-get remove
Password:
sudo: ap-get: command not found
claudecor@ubuntu:~$ sudo apt-get remove mozilla-thunderbird-offline
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mozilla-thunderbird-enigmail: Depends: mozilla-thunderbird (< 1.0.7.0) but 1.5 -0ubuntu4~breezy is to be installed
  mozilla-thunderbird-locale-fr: Conflicts: mozilla-thunderbird (>= 1.0.99) but 1.5-0ubuntu4~breezy is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).
claudecor@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  mozilla-thunderbird-enigmail mozilla-thunderbird-locale-fr mozilla-thunderbird-offline
0 upgraded, 0 newly installed, 3 to remove and 15 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2572kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 76646 files and directories currently installed.)
Removing mozilla-thunderbird-enigmail ...
Updating mozilla-thunderbird chrome registry...find: /usr/lib/mozilla-thunderbird/defaults/profile/extensions/: No such file or directory
E: /usr/lib/mozilla-thunderbird/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-thunderbird/defaults.ini': No such file or directory
dpkg: error processing mozilla-thunderbird-enigmail (--remove):
 subprocess post-removal script returned error exit status 1
Removing mozilla-thunderbird-locale-fr ...
Updating mozilla-thunderbird chrome registry...find: /usr/lib/mozilla-thunderbird/defaults/profile/extensions/: No such file or directory
E: /usr/lib/mozilla-thunderbird/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-thunderbird/defaults.ini': No such file or directory
dpkg: error processing mozilla-thunderbird-locale-fr (--remove):
 subprocess post-removal script returned error exit status 1
Removing mozilla-thunderbird-offline ...
Updating mozilla-thunderbird chrome registry...find: /usr/lib/mozilla-thunderbird/defaults/profile/extensions/: No such file or directory
E: /usr/lib/mozilla-thunderbird/extensions/installed-extensions.txt still present. Registration might have gone wrong.
mv: cannot stat `/usr/lib/mozilla-thunderbird/defaults.ini': No such file or directory
dpkg: error processing mozilla-thunderbird-offline (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 mozilla-thunderbird-enigmail
 mozilla-thunderbird-locale-fr
 mozilla-thunderbird-offline
E: Sub-process /usr/bin/dpkg returned an error code (1)
claudecor@ubuntu:~$

:mrgreen:

---

### Post by GazzaK on 2006-04-24
Arnieboy - wow, this is a great bit of work you have done here.

well done for it all and thank you.

---

### Post by Sokraates on 2006-04-24
@Corvair: Open Synaptic, klick on "Edit" - > "Fix broken Packages". Might also be "Packages" - > "Fix broken Packages" (I'm not in front of my linux-box at the moment).

Before applying the changes, check what will be removed.

---

### Post by Corvair on 2006-04-24
Hi Socrates,
I tried what you suggested but It does not seam to work. This is what I get when I try to take them out.

Corvair



E: mozilla-thunderbird-enigmail: subprocess post-removal script returned error exit status 1
E: mozilla-thunderbird-offline: subprocess post-removal script returned error exit status 1
E: mozilla-thunderbird-locale-fr: subprocess post-removal script returned error exit status 1

---

### Post by mickutz on 2006-04-24
when is there going to be a version of automatix that works on dapper?

---

### Post by Corvair on 2006-04-24
I was finally able to repair the broken packages and remove them.
So now I can go back to Automatix and to load firefox 1.5.

Thanks

---

### Post by Sokraates on 2006-04-24
How did you do it?

---

### Post by Corvair on 2006-04-24
Hi gang,
I was able to install Firefox 1.5 using Automatix, this is great.

When reinstalling Thunderbird 1.5 I lost my addresw book and also my local folders, is there anything I can do to recuperate them?

Claude  :confused:

---

### Post by Corvair on 2006-04-24
I am not sure How I did it. I tried again what you suggested so maybe that is what did it.

---

### Post by Sokraates on 2006-04-25
Automatix does not retain any settings from a previosly used Firefox profile.

To restore your bookmarks, follow [this]("http://ubuntuforums.org/showpost.php?p=681904&postcount=1545") instruction. 

You can also use konqueror or nautilus to restore your old bookmarks (if you are more the GUI fan, like myself). You will nee to make konqueror or nautilus **show hidden files**, since all files and folders starting wih a "." are hidden in linux.

---

### Post by Corvair on 2006-04-25
When I fire up Synaptic I get the following information. I know there is something not configured correctly but I dont know how to correct it.

Thank you for the info. you sent for my address book. I did not have a chance to look after it yet. I have copied my address book from Windows Thunderbird so I can operate ok for now. After a while I get a weid keyboard setup, well weid for my use anyway, and I cannot even write in my p0-assword because the characters are different.
Thanks for the help.:D 


W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Hephaistos on 2006-04-25
Hey guys, i am a linux noob and i couldnt read everything in this thread... Ubuntu was working fine, i installed automatix (quite everything), and it just completly screwed my system: Now i am using windows xp running in vmware to write this  with iexplore(firefox, as lots of other things, just cant run anymore). That' s cool, but not what i expected :-k could somebody help? PLease?

---

### Post by Corvair on 2006-04-26
Hello Socrates or Arniboy or anyone esle who can help.

This is the report I got after doing this : sudo apt-get upgrade

Can you help me on this or direct me to someone else if I am not at the right place?
Thank you in advance,
Claude (Corvair)

 section
/usr/share/i18n/locales/en_CA:1509: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1510: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1511: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1512: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1513: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1514: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1515: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1516: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1517: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1518: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1519: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1520: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1521: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1522: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1524: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1525: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1526: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1527: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1528: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1529: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1530: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1531: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1532: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1534: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1535: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1536: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1537: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1538: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1539: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1540: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1541: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1542: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1543: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1545: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1546: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1547: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1548: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1549: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1550: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1551: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1552: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1554: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1555: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1556: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1557: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1558: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1560: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1561: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1562: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1563: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1564: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1565: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1566: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1567: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1568: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1569: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1570: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1571: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1572: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1573: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1574: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1575: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1576: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1577: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1578: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1579: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1580: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1581: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1582: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1583: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1584: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1585: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1586: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1587: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1588: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1589: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1590: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1591: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1592: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1593: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1594: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1595: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1596: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1597: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1598: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1599: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1600: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1601: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1602: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1603: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1604: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1605: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1606: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1607: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1608: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1609: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1610: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1611: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1612: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1613: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1614: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1615: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1616: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1617: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1618: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1619: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1620: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1621: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1622: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1623: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1624: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1625: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1626: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1627: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1628: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1629: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1630: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1631: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1632: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1633: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1634: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1635: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1636: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1637: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1638: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1639: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1640: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1641: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1642: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1643: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1644: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1645: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1646: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1647: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1648: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1649: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1650: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1651: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1652: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1653: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1654: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1655: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1656: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1657: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1658: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1659: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1660: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1661: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1662: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1663: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1664: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1665: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1666: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1667: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1668: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1669: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1670: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1671: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1672: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1673: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1674: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1675: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1676: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1677: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1678: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1679: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1680: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1681: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1682: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1683: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1684: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1685: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1686: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1687: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1688: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1689: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1690: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1691: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1692: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1693: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1694: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1695: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1696: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1697: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1698: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1699: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1700: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1701: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1702: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1703: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1704: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1705: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1706: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1707: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1708: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1709: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1710: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1711: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1712: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1713: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1714: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1715: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1716: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1717: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1718: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1719: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1720: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1721: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1722: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1723: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1724: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1725: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1726: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1727: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1728: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1730: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1732: syntax error: not inside a locale definition  section
/usr/share/i18n/locales/en_CA:1763: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1764: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1765: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1766: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1767: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1768: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1769: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1770: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1771: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1772: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1773: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1774: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1775: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1776: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1777: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1778: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1779: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1780: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1781: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1782: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1783: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1784: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1785: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1786: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1787: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1788: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1789: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1790: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1791: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1797: unterminated string
/usr/share/i18n/locales/en_CA:1797: LC_TIME: unknown character in field `date_fm t'
/usr/share/i18n/locales/en_CA:1798: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1799: LC_TIME: syntax error
/usr/share/i18n/locales/en_CA:1813: unterminated string
/usr/share/i18n/locales/en_CA:1813: LC_TELEPHONE: unknown character in field `te l_int_fmt'
/usr/share/i18n/locales/en_CA:1814: LC_TELEPHONE: syntax error
/usr/share/i18n/locales/en_CA:1820: LC_MEASUREMENT: syntax error
/usr/share/i18n/locales/en_CA:1825: unterminated string
/usr/share/i18n/locales/en_CA:1825: LC_NAME: unknown character in field `name_fm t'
/usr/share/i18n/locales/en_CA:1826: LC_NAME: syntax error
/usr/share/i18n/locales/en_CA:1830: unterminated string
/usr/share/i18n/locales/en_CA:1830: LC_ADDRESS: unknown character in field `post al_fmt'
/usr/share/i18n/locales/en_CA:1831: LC_ADDRESS: syntax error
/usr/share/i18n/locales/en_CA:1832: LC_ADDRESS: syntax error
/usr/share/i18n/locales/en_CA:1833: LC_ADDRESS: syntax error
/usr/share/i18n/locales/en_CA:1834: LC_ADDRESS: syntax error
LC_TIME: field `abday' not defined
LC_TIME: field `day' not defined
LC_TIME: field `abmon' not defined
LC_TIME: field `mon' not defined
No definition for LC_COLLATE category found
LC_NAME: field `name_fmt' must not be empty
LC_ADDRESS: field `postal_fmt' must not be empty
LC_TELEPHONE: field `tel_int_fmt' must not be empty
No definition for LC_IDENTIFICATION category found
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)
claudecor@ubuntu:~$

---

### Post by safetycool on 2006-04-26
[QUOTE=arnieboy]look just above the "quote" button on the first post (bottom right corner) on [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)[/QUOTE]


I am new to linux and this site. I have looked where you said to look, and I get sent back to the same page. I have gone to "terminal" and entered the lines indicated by the instructions to no avail. My dvd player will not play movies. Any suggestions?

:-k

---

### Post by Melciah on 2006-04-27
hi all. im very new to this linux thing and ive run into trouble. i installed automatrix as per the instructions. many of the programs i selected did not install and a few of the ones that did were broken (ie. amsn). i really wasnt taking note, but i believe it had something to do with the server not being found. 

i used the package manager to remove amsn among other programs and now when i either use apt-get update or the package managers, i get a buttload of errors like the following: 

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
etc...

i saw the other posts on this, suggestion was just to try again later i believe.

suggestions anyone. cheers.

---

### Post by Melciah on 2006-04-27
hi all. im very new to this linux thing and ive run into trouble. i installed automatrix as per the instructions. many of the programs i selected did not install and a few of the ones that did were broken (ie. amsn). i really wasnt taking note, but i believe it had something to do with the server not being found. 

i used the package manager to remove amsn among other programs and now when i either use apt-get update or the package managers, i get a buttload of errors like the following: 

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
etc...

i saw the other posts on this, suggestion was just to try again later i believe.

suggestions anyone. cheers.

EDIT: also i forgot to mention that my firefox is now broken too. it begins to load, but disappears shortly after.

---

### Post by arnieboy on 2006-04-27
[QUOTE=Melciah]hi all. im very new to this linux thing and ive run into trouble. i installed automatrix as per the instructions. many of the programs i selected did not install and a few of the ones that did were broken (ie. amsn). i really wasnt taking note, but i believe it had something to do with the server not being found. 

i used the package manager to remove amsn among other programs and now when i either use apt-get update or the package managers, i get a buttload of errors like the following: 

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
etc...

i saw the other posts on this, suggestion was just to try again later i believe.

suggestions anyone. cheers.

EDIT: also i forgot to mention that my firefox is now broken too. it begins to load, but disappears shortly after.[/QUOTE]
to try and resurrect firefox do the following from terminal:
```
mv ~/.mozilla ~/.mozilla_new_backup
```
and restart firefox.

not sure why the repositories are freaking up. maybe a server side error..

---

### Post by Melciah on 2006-04-28
thanks arnie, that fixed my firefox.

---

### Post by Melciah on 2006-04-28
for anyone interested, i fixed my update problems. all i did was use the "easy ubuntu" tool.

all my repos are working fine now, and ive got most of the programs and codecs i needed through it, so im in a pretty good mood.

ill give automatrix a try a little later.

---

### Post by jon_z on 2006-05-01
*EDIT* I was dumb and didn't search the forums well before I posted.  Automatix will be released with finaly release of dapper

---

### Post by BobSongs on 2006-05-14
Greets;

Couple of points on Automatix. There was a version, I can't recall which number, where an install would produce an odd effect if I selected everything at once. Boxes started opening everywhere. This is on a fresh install of Ubuntu 5.10 with a clean /home folder. See attached images below.

If I select just a few items, five or so, then they install pretty much without a hitch. If I select everything I want all at once... well, you get the point. Problem was when Automatix said it was finished setting itself up all the boxes closed and most of the software wasn't properly installed. Synaptic complained that things were broken.

Also: I've got a friend who's interested in tinkering with Automatix for Kubuntu (Dapper Drake Beta). Let me know what you think.

---

### Post by Brando569 on 2006-06-01
any chance you're gonna port this to work on dapper?

---

### Post by mstlyevil on 2006-06-02
[QUOTE=Brando569]any chance you're gonna port this to work on dapper?[/QUOTE]

We already have ported it to Dapper.

---

### Post by f4nt0m3t on 2006-06-02
Can't Automatix install Ati Driver?

---

### Post by Titus A Duxass on 2006-06-03
Having problems with codecs and realplayer not being installed, otherwise ran good.  Thanks.

---

### Post by bk452 on 2006-06-03
You are my hero!!!  Fantastic job!!!

---

### Post by Zdravko on 2006-06-04
I typed the following:
> 
wget [http://beerorkid.com/arnieboy/automatix_6.1_i386.deb](http://beerorkid.com/arnieboy/automatix_6.1_i386.deb) 

As a result:
> 
404 not found


---

### Post by xyz on 2006-06-04
Hi-
According to the thread I just checked,type:
```
wget http://beerorkid.com/automatix/automatix_6.1-2_i386.deb
```
You seem to have omitted to type **-2**

---

### Post by fuelman on 2006-06-04
it ```
wget http://beerorkid.com/automatix/automatix_6.1-4_i386.deb
``` now

**Edits**: No thatd wrong .. wget [http://beerorkid.com/automatix/automatix_6.1-2_i386.deb](http://beerorkid.com/automatix/automatix_6.1-2_i386.deb) is right .. sorry

---

### Post by Trosky on 2006-06-04
Hi, I got a problem when I try to update 

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The next signatures couldn't be verified because your public key is not available: NO_PUBKEY 18B52FE3521A9C7C

How can I fixed?

Thanks

---

### Post by The Darkness on 2006-06-05
[QUOTE=Trosky]Hi, I got a problem when I try to update 

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The next signatures couldn't be verified because your public key is not available: NO_PUBKEY 18B52FE3521A9C7C

How can I fixed?

Thanks[/QUOTE]
From the automatix website:
The Automatix repository is now GPG-secured, to make sure apt recognises our key, run these two commands in a terminal:

gpg --keyserver subkeys.pgp.net --recv-keys 521A9C7C
gpg --export --armor 521A9C7C | sudo apt-key add -

Finally, enter "sudo apt-get update" in a terminal, and when its finished, "sudo apt-get install automatix"

Or if you'd prefer to download with a browser or wget:

---

### Post by tomski on 2006-06-05
Hi all,
just wondering, now that automatix is compatible with dapper will this remove/replace some of the packages labeled 'obsolete'
or is there another reason why i have 116 of these packages labeled in such a way ie: upgrade from brezzy
is this something i need to address or do i just 'keep an eye on them'??

---

### Post by j0eb0b on 2006-06-05
Arnieboy and team,

Thanks for a good piece of work.  i struggled mightly using 5.10 with Multimedia issues and automatix has made my otherwise painful migration to 6.0.6 LTS successful.  Maybe this is the distro that will allow me to pull the plug on my other MS machines.

Joe

---

### Post by elemental666 on 2006-06-10
heh, I just spent 3 days manually doing half of what Automatix does autmatically...

look here first - who knew you meant it...

I managed to hose several things on my laptop, so when I get home tonight, I'm gonna give this a go.  ONe question though, will installing a new kernel break any of these installs?  For example, I have a broadcom based wireless nic and everytime I install a new kernel I have to reinstall the wireless card.

---

### Post by DJ-Power on 2006-06-10
What a fantastic bit of scripting. This proggy worked  a treat on my recently upgraded dapper install from breezy. Good job guys. 
Regards

---

### Post by elemental666 on 2006-06-10
hmmm, I installed automatix per [these instructions]("http://ubuntuforums.org/showthread.php?t=190025"). Then installed most of the list.  I noticed A LOT of depency errors scrolling by. When it was all said and done, I had a bunch of broken links in my menus, didn't have several apps chosen form the list in the menus at all (Listen was one).  All in all, it was a train wreck.  However, given the 50 pages of kudos I see here, I'm willing to give it another go.

I'm going to:
reintall Dapper from the Desktop CD, install the k7 kernel, enable the rest of the ubuntu repos, update the system, then install automatix per those same instructions.  This time I'll install the stuff in automatix 1 at a time, and I"ll note my errors here...

---

### Post by Redindian on 2006-06-11
I'm getting the following errors:

root@Ind:/# automatix
GTK Accessibility Module initialized
GTK Accessibility Module initialized
cat: /root/automatix.log: No such file or directory
GTK Accessibility Module initialized
Codename:       dapper
Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
root@Ind:/#

Any help please. thanks.

---

### Post by elemental666 on 2006-06-12
[QUOTE=elemental666]This time I'll install the stuff in automatix 1 at a time, and I"ll note my errors here...[/QUOTE]

OK so far, all i've come across is a Java dependancy issue.  java5_bin, java5_jre and java5_plugin seem to be suffering from some sort of circular dependancy issue.  Synaptic was able to repair the broken java5_plugin package and I have resumed installing apps.

---

### Post by otis_u on 2006-06-16
Hi, I'm just letting you know that after installing various packages with Automatix it broke all my sound- somehow changing the samplerate so that all audio is horribly buzzy and garbled.

I'm trying to figure out what was changed so I can set the saplerate back to 48000- what I hope will fix the problem.

other than that automatix was a handy tool :)

---

### Post by lagerman on 2006-06-19
Is there any way that you can add that it installs plugins for opera browser. Thanks

---

### Post by Wermut on 2006-06-20
1. Nice tool!

2. The installation of the firefox plugins does not work for me. It does not download  or install anything after I click <OK>.

3. How can the installed packages be updated?

---

### Post by joeybunda on 2006-06-21
I figured out my sound issue... Just an FYI for anyone having similar issues - open up your sound control and enable everything in playback and turn it up... That's it - or that was it for me. I think Dapper was recognizing anything and everything that had a chip that handled audio as a sound card - well something like that anyhow... I don't think it was automatix.

---

### Post by fade510 on 2006-06-22
I was wondering if uninstalling some of this stuff is as easy as point in click in the package manager, because i don't need some of these things but most of them I do. sorry for the newb post
thanks:-?

---

### Post by markmaus on 2006-06-23
When I run Automatix in Dapper, the script stalls out when trying to connect to ftp.free.fr/pub/Distrobutions/.......  Does anyone else have this problem?  It's like that site doesn't exist!

---

### Post by masterjonny on 2006-06-23
Got this just now and it's a great app!! All the things I need minus the fighting with Linux :D  10/10

---

### Post by chanders on 2006-06-25
I love this program.... One request though... Is it possible for Automatix to show what has already been installed?

Thanks in advance!

---

### Post by mjkey on 2006-06-25
[QUOTE=chanders]I love this program.... One request though... Is it possible for Automatix to show what has already been installed?

Thanks in advance![/QUOTE]
Check your automatix.log within your home folder.:D

---

### Post by chanders on 2006-06-26
[QUOTE=mjkey]Check your automatix.log within your home folder.:D[/QUOTE]

Thanks, but this just shows what I just installed, not what is already installed on the system. I remove the log file everytime I install something and so it just shows the last install. I wish there was some way that Automatix could show all that I have installed from the list it provides...

---

### Post by arnieboy on 2006-06-26
[QUOTE=chanders]Thanks, but this just shows what I just installed, not what is already installed on the system. I remove the log file everytime I install something and so it just shows the last install. I wish there was some way that Automatix could show all that I have installed from the list it provides...[/QUOTE]
if u dont delete the log everytime, it will show u all that u checked over multiple runs.

---

### Post by menawollas on 2006-06-26
Having a problem with Automatix installing Azureus. It Didn't. Not even when bitorrent clients are the only thing connected.

Not sure what going wrong - ended up installing it manually.

---

### Post by arnieboy on 2006-06-26
[QUOTE=menawollas]Having a problem with Automatix installing Azureus. It Didn't. Not even when bitorrent clients are the only thing connected.

Not sure what going wrong - ended up installing it manually.[/QUOTE]
upgrade to the latest version of automatix which fixes an azureus installation related bug.

---

### Post by menawollas on 2006-06-27
Thankyou

---

### Post by n8bounds on 2006-07-01
Thanks, Arnie--you rock \m/

---

### Post by kevanf1 on 2006-07-06
:KS I'd just like to say thank you very much for the hard work that has gone into producing Automatix.  It is fantastic :)  Everything has installed as it should and, for the first time ever, I can watch my legally purchased DVDs....without them going all choppy ;)  I did get libdvdcss installed in SuSE but it was awful.  Now in Kubuntu it is brilliant.

Again, thank you and well done.

---

### Post by mstlyevil on 2006-07-09
> **kevanf1 said:**
> :KS I'd just like to say thank you very much for the hard work that has gone into producing Automatix.  It is fantastic :)  Everything has installed as it should and, for the first time ever, I can watch my legally purchased DVDs....without them going all choppy ;)  I did get libdvdcss installed in SuSE but it was awful.  Now in Kubuntu it is brilliant.

Again, thank you and well done.

You are very welcome.

---

### Post by oss_monkey on 2006-07-09
**Three cheers for the [COLOR="Blue"]Automatix[/COLOR] team!** :)

Thanks for making the lives of linux newbies like me a lot easier.

---

### Post by nickless on 2006-07-09
Automatix is really nice, but why is azureus the only program that gets installed in /opt/ ? Wouldn't it be nicer to install all there? And azureus can't get started through simple terminal: azureus Maybe symlinks would be nice...
..actually I didn't get it to work this way, no idea why :D I did
```
ln -s /opt/azureus/azureus /usr/bin/
``` also one in /usr/local/bin/
but I get this error:
```
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/usr/local/bin/*.jar" -Djava.library.path="/usr/local/bin" -Dazureus.install.path="/usr/local/bin" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/ui/swt/Main
Azureus TERMINATED.

```
... :)

EDIT: Possible workaround or solution: Added an alias in my bash.rc

---

### Post by Scorpuk on 2006-07-09
Having a problem with the Automatix for AMD64.


Can't install the DVD codecs (non free).


Get to log on, but says file, or folder, not found for libdvdcss and has done for past 2 days. :(


yup deff looking for a folder and not a file is when it fails:

```

CWD /debian-marillat/pool/main/libd/libdvdcss ...
No such directory 'debian-marillat/pool/main/libd/libdvdcss'.

```



Anyone know what is going on?


tnx.

---

### Post by ekravche on 2006-07-15
How does automatix handle application updates? By that I mean what if there is a new release of the codecs for instance. Will automatix get the latest version of the codecs?

Thanks in advance.

---

### Post by peterthewolf on 2006-07-15
Installed gnucash seemed to install a lot of software but when finished could not find any link in applications. A places find on cash found nothing useful or executable.

---

### Post by petersjm on 2006-07-18
> **peterthewolf said:**
> Installed gnucash seemed to install a lot of software but when finished could not find any link in applications. A places find on cash found nothing useful or executable.

I haven't used gnucash, but try the locate command?

```
locate /gnucash
```

That should bring up any folder called gnucash and you should be able to work out where it's stored from that.

---

### Post by peterthewolf on 2006-07-18
locate /gnucash shows lots of files but nothing that suggests its executable.
using applications/add/remove or al a carte menu shows no entries for gnucash. beagle cannot even find what locate finds. tried to uninstall beagle it went but the old find files through places did not get put back.

---

### Post by arnieboy on 2006-07-18
just try doing
```
gnucash
``` 
from terminal

---

### Post by lmaestas on 2006-07-18
I must be really dumb
I am following the instructions to install automatix exactly as posted here.  I think my mistake is in the very beggining.  when you say edit the sources.list use getedit.  ok I understand that but isn't this an existing list?  Do I just open the tex editor (gedit) and write
sudo gedit /etc/apt/sources.list and then after that line paste
deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main 
then save?  save as?  am I replacing something.  


everything else in terminal goes fine except when it is time to install automatix can't be found.  

sorry for my ignorance.

---

### Post by PowerRanger on 2006-07-18
I have a fresh install of 6.06, installing nvidia driver via Automatix results in x server errors.  

I have an nvidia 5500 agp on pci:2:0:0.  Here's my xorg.conf before installing:

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Here it is after:

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

Kinda weird that there's no BusID entry, but I don't think that's the problem.

Here's the Xorg.log 

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Video Driver

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***

TIA
Mike

---

### Post by sorin7486 on 2006-07-20
Quick question about the repository:

can I use a CD/DVD as a repository for Automatix ?... I have already installed alot of things on my home PC and I want to do the same thing using Automatix at work... but as the bandwith is limited I wold prefere just copying the packages from home and use that instead of the net...

10x for the great job...

---

### Post by handy on 2006-07-24
For some reason on both my wife's & my Dapper machines, (running Gnome), we don't get the option to **turn on numlock** at startup?

Also, even though I check the **Nautilus Scripts** option in Automatix, they do not show on my wife's machine?

Any input greatly appreciated?

---

### Post by arnieboy on 2006-07-24
> **handy said:**
> For some reason on both my wife's & my Dapper machines, (running Gnome), we don't get the option to **turn on numlock** at startup?

Also, even though I check the **Nautilus Scripts** option in Automatix, they do not show on my wife's machine?

Any input greatly appreciated?

numlock option has been removed.
which version and architecture of automatix is your wife using? she might need to upgrade to the latest version. There was a nautilus-scripts-permissions-related bug in one of the earlier automatix releases

---

### Post by handy on 2006-07-24
> **arnieboy said:**
> numlock option has been removed.
which version and architecture of automatix is your wife using? she might need to upgrade to the latest version. There was a nautilus-scripts-permissions-related bug in one of the earlier automatix releases

Thanks for the reply.

I updated her's & mine yesterday, in the hope that the script & the numlock would work.

---

### Post by arnieboy on 2006-07-24
> **handy said:**
> Thanks for the reply.

I updated her Automatix yesterday!

try this

```
chmod 755 ~/.gnome2/nautilus-scripts/*
```

---

### Post by handy on 2006-07-24
> **arnieboy said:**
> try this

```
chmod 755 ~/.gnome2/nautilus-scripts/*
```

Thanks Arnieboy.

I did the chmod & then told Automatix to install the scripts thing & it works...

---

### Post by petersjm on 2006-07-25
> **lmaestas said:**
> I must be really dumb
I am following the instructions to install automatix exactly as posted here.  I think my mistake is in the very beggining.  when you say edit the sources.list use getedit.  ok I understand that but isn't this an existing list?  Do I just open the tex editor (gedit) and write
sudo gedit /etc/apt/sources.list and then after that line paste
deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main 
then save?  save as?  am I replacing something.

You need to put **sudo gedit /etc/apt/sources.list** in the terminal. This opens the sources.list file (using gedit). Paste in the code as mentioned and click Save (not Save As). Bingo.

---

### Post by rand0m3r on 2006-07-26
hey, does anyone know what this error means? it happens when i try to d/l and install anything from automatix.

[1] 5587
dshum@dshum:~$ X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
Codename: dapper

---

### Post by M.Verkerk on 2006-07-28
PowerRanger:

Are you sure you have installed the nvidia kernel module?

It's located in: linux-restricted-modules-XXXX

Where XXXX is the version of your installed kernel.

---

### Post by M.Verkerk on 2006-07-28
PowerRanger:

Are you sure you have installed the nvidia kernel module?

It's located in: linux-restricted-modules-XXXX

Where XXXX is the version of your installed kernel.

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***

---

### Post by Iandefor on 2006-07-28
> **rand0m3r said:**
> hey, does anyone know what this error means? it happens when i try to d/l and install anything from automatix.

[1] 5587
dshum@dshum:~$ X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
Codename: dapper What locale are you using? I've seen this problem on xterm before. It seems t be related to the locales used.

---

### Post by cville on 2006-07-30
When we can have the ATI driver installation too :)

Thanks

---

### Post by happogiri on 2006-07-31
This makes my life much more comfortable... Thanks!!

---

### Post by hansi70 on 2006-08-03
Hi Guys,

When I run automatix I get the following error:

cat: /home/hansi/automatix.log: No such file or directory
Codename:       dapper

When I created an empty automatix.log on the suggested directory

The message is reducted to:
Codename:       dapper

and it still doesn't work!

Pleas help me!

---

### Post by ba5e on 2006-08-04
I had exactly the same error, but a recent (as in last night) update of automatix has fixed this error. did you automatix simply exit after that screen came up?

---

### Post by hansi70 on 2006-08-04
Yes id did.

However, I did manage to sort it out. One needs to wait for the sudo apt-get  update to finish before summoning the sudo apt-get install automatix.

Regards,

Hansi

---

### Post by Thinh on 2006-08-07
I dont know if automatix does this automatic, but mine doesnt deselect the items i have installed on the systems. it a pain for me because one my connection goes down in the middle of an update i have to select all the package to install again, is there away to see which package has been installed so i just install the one that wasnt fully downloaded

Thinh Noob and loving Ubuntu

---

### Post by arnieboy on 2006-08-07
> **Thinh said:**
> I dont know if automatix does this automatic, but mine doesnt deselect the items i have installed on the systems. it a pain for me because one my connection goes down in the middle of an update i have to select all the package to install again, is there away to see which package has been installed so i just install the one that wasnt fully downloaded

Thinh Noob and loving Ubuntu

automatix automatically skips over all installed options and resumes where it left off. so checking something multiple number of times will not slow you down.

---

### Post by TheLive1 on 2006-08-08
N/a

---

### Post by qrm on 2006-08-08
great script, makes my life much easier :) btw i saw automatixbleeder or something like that in the repos - which programs does that one install in addition to the usual "safe" automatix?

---

### Post by Mark_in_Hollywood on 2006-08-08
In a terminal 

mark@Lexington:~$ cat $HOME/automatix.log
Google Picasa
Acrobat Reader
Flashplayer
Extra Fonts
Boot-up Manager
SUN JAVA 1.5 JRE

but when I go to [http://www.time.gov/](http://www.time.gov/)

I offered Java Runtime Environment as a plug-in. As I just installed Dapper Drake (clean install) August 4, and as I didn't see JRE offered then I need to know what is happening here.

By the bye: Acrobat Reader, Flashplayer, Extra Fonts aren't installed either. Nor BUM? What gives with this?

Meanwhile, I love the new Automatix look, and WOW does it offer a lot of help.

---

### Post by Xera on 2006-08-09
probably a silly question, but how do i uninstall Swiftfox?
i checked it by accident, and now i have no idea how to remove it :(

//Xera

---

### Post by realrbman on 2006-08-09
i just did a fresh install of dapper, tried automatrix instead of doing everything manually like usual.

it worked great, but after using it.

i attempted to install build-essentials and apt complained about gcc being an unmet dependencie.

so i just try 
```

burny@sixtybit:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcc: Depends: cpp (>= 4:4.0.1-3) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages

```
automatrix was the first thing i installed, after upgrading to the latest versions of the base packages.  any ideas how i can fix this?


thanks

---

### Post by arnieboy on 2006-08-09
> **Xera said:**
> probably a silly question, but how do i uninstall Swiftfox?
i checked it by accident, and now i have no idea how to remove it :(

//Xera

for how to uninstall stuff installed by automatix visit the following thread:
[http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)
if something isnt listed, let us know and we will add it.

---

### Post by arnieboy on 2006-08-09
> **realrbman said:**
> i just did a fresh install of dapper, tried automatrix instead of doing everything manually like usual.

it worked great, but after using it.

i attempted to install build-essentials and apt complained about gcc being an unmet dependencie.

so i just try 
```

burny@sixtybit:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gcc: Depends: cpp (>= 4:4.0.1-3) but it is not going to be installed
       Depends: gcc-4.0 (>= 4.0.1-2) but it is not going to be installed
E: Broken packages

```
automatrix was the first thing i installed, after upgrading to the latest versions of the base packages.  any ideas how i can fix this?


thanks
try a:
```

sudo apt-get update
sudo apt-get -f install

```

---

### Post by spotinthesky on 2006-08-10
Hi, after aa lot of thinking and tryouts, I finally decided to get some help, I've just installed Xubuntu (dapper) and I'm while I was trying to install automatix, I get the following when I do this coommand

gpg --import key.gpg.asc

aand this is what I get
 
gpg: la clave 521A9C7C fue creada 234187766 segundos en el futuro (salto en el tiempo
o problemas con el reloj)
gpg: la clave 521A9C7C fue creada 234187766 segundos en el futuro (salto en el tiempo
o problemas con el reloj)
gpg: la clave 521A9C7C fue creada 234187766 segundos en el futuro (salto en el tiempo
o problemas con el reloj)
gpg: la clave 521A9C7C fue creada 234187766 segundos en el futuro (salto en el tiempo
o problemas con el reloj)
gpg: clave 521A9C7C: sin identificadores de usuario válidos
gpg: esto puede ser debido a la ausencia de autofirma
gpg: Cantidad total procesada: 1
gpg:           sin identificador: 1



It's in spanish, but it says, that the Key 521A9C7C: without valid user identificators, this might be because of the absesnce of autosign

and I can't continue from this, I've done everything, I had installed automatix on Ubuntu ( dapper )= without problems, so I don't know whats happening, I've also tried the automatic installer for newer users, and didn't success, it asked for Zenity , which I read is neccesary for Xubuntu, but didn't have success trying to install it

thanks in advance

---

### Post by carney1979 on 2006-08-17
Running Automatix from a .deb version 6.4-6-6.06dapper on an up-to-date Dapper i386 box.

When viewing multimedia files online such as at CNN or Apple, the Mplayer plugin opens the media in it's own window. In other words, the actual video is entirely in it's own window. Please see the attached screenshot. Note that the actual video has been moved by me to the lower right corner of the screenshot. I would expect the video to stay "anchored" in the Mplayer window area in the upper left part of the screenshot.

This seperate window is managed by Metacity.

Is there a way to get the plugin to NOT open media in it's own window?

David

---

### Post by mips on 2006-08-17
arnieboy,

before this thread gets locked I have to ask one question. Is their anyway to see what packages/modules/software are installed in a simple list format for each of the listed sections in automatix. Alternatively where can we see the source ?

Thanks
mips

---

### Post by matthew on 2006-08-17
Closed by request.
[http://www.ubuntuforums.org/showthread.php?t=238324](http://www.ubuntuforums.org/showthread.php?t=238324)

---

