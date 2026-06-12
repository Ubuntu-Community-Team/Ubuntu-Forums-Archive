---
title: "Window's Replacement Apps"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by TOMM_1230 on 2008-11-04
It was suggested that I start a new thread to ask this question as it would confuse my last post so here goes.

I am looking for the best Apps to replace the folowing Window's Apps. I am currently learning Hardy 64-bit with KDE3 (it has LTS), so I don't have any of the compatibility issues with Ibex and KDE4 have currently.  I will wait for the LTS version of KDE4.

1) WMP - as a all-in-one media player.  I am looking for the ability to play everything and ease of use.

2) Office '03 - I know '07 is out but my wife and Mother-In-Law neither one are familiar with it and are intimidated by it (Great time to switch them to Linux.) Is OO.o the best solution?

3) Plugins for Firefox to make it as simple to use as IE when comes to everything opening. (Including Real music/video, Flash, and Java.)

4) Photo Editing - My wife wants this for scrapbooking and I just use whatever came with my printer lexmark photo studio or whatever now so advice on a more advanced one would be appriciated.

5) I need AIM for school can that be ran on Linux?  If not can I get to my AIM acount from a Linux App?

6) Acrobat - can it be ran on linux or is KPDF the best there is?

7) A Anti-Virus for Linux.  I know Linux is not succeptable, however, My system is dual boot and I do not want Window infected while I am running Linux (also I am using the EXT2 driver so Windows can get to my linux drive natively so it really is succeptable) so I want a AV for Linux.  (I do not care if it is needed, I want it so please do not try to convince me otherwise.  _Any posts advising me not to get an AV will be reported as argumentative_:frown:.  Sorry, I want this for my computer. If you want to help me, help me do it my way, I am not about to change my mind.)

Thanks in advance.

---

### Post by LowSky on 2008-11-04
1. VLC, loko up medibuntu on google for DVD playback
2. Open Office is the best availible
3. this will give you flash and java and a few other nice things```
sudo apt-get install kubuntu-restricted-extras
```
4. GIMP is the best but can also be a little hard to learn
5. Pidgin
6. Acrobat maybe... visit the Adobe website, I know Adobe Reader is availible, That I know
7. ClamAV, though virus can only effect the system thay are installed on, which is hard to do in Linux, If you use a virus progrma in Windows you will be fine

---

### Post by Titan8990 on 2008-11-04
1) Try Amarok

2) OO.o is the best solution IMO.

3) Should only need to install flash and only once -- you may have issues with java and the 64bit version of Kubuntu. 

4) Try GIMP

5) Use Pidgin instant messenger. Does lack web cam features.

6) Acrobat makes a ton of products. Need to be more specific.

7) sudo apt-get install clamav  -- Safe browsing practices > any a/v available. Sorry for being argumentative.

---

### Post by cl0ckwork on 2008-11-04
about the a/v program, its not that we are trying to steer you away from one.
there has not been much need for one, so not too many have been developed.
most of the linux a/v programs are for servers and monitoring windows workstations.

[this link]("https://help.ubuntu.com/community/Antivirus") is the ubuntu documentation of the antivirus applications available

---

### Post by rozan on 2008-11-04
Does pidgin support voice chat?

---

### Post by cl0ckwork on 2008-11-04
> **rozan said:**
> Does pidgin support voice chat?

not yet, that and video are in the works

---

### Post by mc4100 on 2008-11-04
I wasn't going to relply here, since you're looking for **K**ubuntu solutions, but I do have to say, it seems like regular ubuntu would meet all your needs:

> **TOMM_1230 said:**
> It was suggested that I start a new thread to ask this question as it would confuse my last post so here goes.

I am looking for the best Apps to replace the folowing Window's Apps. I am currently learning Hardy 64-bit with KDE3 (it has LTS), so I don't have any of the compatibility issues with Ibex and KDE4 have currently.  I will wait for the LTS version of KDE4.

1) WMP - as a all-in-one media player.  I am looking for the ability to play everything and ease of use.

Totem Movie Player, installed by default in Ubuntu, uses gstreamer for handling the files, which supports plugins -- meaning that you should be able to get fantastic support for many proprietary (and open) formats for video and audio.

> 2) Office '03 - I know '07 is out but my wife and Mother-In-Law neither one are familiar with it and are intimidated by it (Great time to switch them to Linux.) Is OO.o the best solution?

OO.o is the best bet, installed by default in Kubuntu and Ubuntu, but there's also [Lotus Symphony]("http://symphony.lotus.com/software/lotus/symphony/home.nsf/home") (Still in beta, not Open Source).

> 3) Plugins for Firefox to make it as simple to use as IE when comes to everything opening. (Including Real music/video, Flash, and Java.)

Flash 10 can be installed from the Ubuntu repositories, or from Adobe's website if you're running a version pre-8.10. Again, if you install the gstreamer plugins, then Firefox will inherit the ability to playback all the same files (due to fact that totem ships with a plugin to do just that)

> 4) Photo Editing - My wife wants this for scrapbooking and I just use whatever came with my printer lexmark photo studio or whatever now so advice on a more advanced one would be appriciated.

Gimp, installed by default in Ubuntu, is great for advanced editing, but you can also install Wine which supports running Photoshop CS2 (see screenshot).

> 5) I need AIM for school can that be ran on Linux?  If not can I get to my AIM acount from a Linux App?

Pidgin should do this -- installed by default.

> 6) Acrobat - can it be ran on linux or is KPDF the best there is?

I assume you mean Adobe Reader; is so, then there is a version that runs on Linux ... but Evince, yeah ... default, works just great for most PDF's.

---

### Post by aktiwers on 2008-11-04
[http://www.osalt.com/](http://www.osalt.com/)

---

### Post by SeattleToJerusalem on 2008-11-04
1) VLC is the simplest and easiest to use that I've found

2) Open Office is the way to go. Easy to learn, and easy to set the defaults to match any version of Office

3) Just Java...everything should work from there...

4) Try GIMP, it's a bit rough at first but then it's great

5) Pidgen for chat and Skype for voice

6) ???

7) sudo apt-get install clamav -- but only if you really think you'll need it. You can't infect one OS from the other, have to be using Windows for it to get infected, and there is virtually nothing you can do to infect Linux...that said, I use Clamav to scan external drives that users have hosed, works great.

---

### Post by TOMM_1230 on 2008-11-04
> **Titan8990 said:**
> 
7) sudo apt-get install clamav  -- Safe browsing practices > any a/v available. Sorry for being argumentative.

This is not argumentative... You still gave me info "ClamAV" which seems to be the hands down winner here, I had heard that Avast had a good AV for Linux in another forum as well.

As for Safe browsing practices > any a/v available, that may be true, as well as Linux can not directly infect Windows maybe true but Windows will have direct native access to my Linux drive.  So if I pick up a Windows Virus while in Linux I am worried that it can go in a backdoor on my next boot into Windows before my Windows AV is loaded.  It is a long shot I know but if there is a one in a million shot I would still rather be safe than sorry.  I would like to get away from the dominance of MS and the unbelivablely high cost of MS products but with school and most High end games (mostly for me "Mass Effect" and new RPG's) being completely dependent on MS software it is a permanent part of my life.:cry:

And Pigin can access AIM user accounts by default?  How does it do that without breaking any laws?

---

### Post by TOMM_1230 on 2008-11-04
I choose KDE over GNOME because it is supposed to "feel" more like Windows, and my goal is to come up with a OS and office suite that can replace XP for a compuidiot, or beginner user.(Don't tell my mother-in-law I called her a compuidiot :lolflag:)  So the Visual interface is important, and I must say that I like Kubuntu so far, there is just a steep learning curve to be familiar enough with Linux to get it to run similiar Windows (without the rampant security issues).  It is funny that even the experts don't seem to agree on what the most feature rich multi-use media programs are. I am glad that so much user support is available though, this is crazy, I am use to having to wait days for an e-mail from MS.:guitar:

Thanks to all of you.

---

### Post by jimv on 2008-11-04
The default media programs are fine, just make sure that you installed the ubuntu-restricted-extras package to get all the codecs.

Office 2003 runs great in WINE, if you want to use it.

Picasa3 from Google is a great, basic photo editor/touch-up.  For anything more advanced, there's the GIMP.

Pidgin is a great IM that supports all kinds of messengers, like AIM, MSN, Yahoo, GoogleTAlk, etc.  Oh, and about the AIM/legality question...I don't think there are any laws regarding the use of which chat program you use with a service.

Adobe Reader is the best PDF reader hands down as far as features go (and it integrates with Firefox).  The ones included with Ubuntu/Kubuntu are a bit faster though, but with less features and no browser integration.

ClamAV or Avast would be a good antivirus.

---

### Post by SuperSonic4 on 2008-11-04
1. Amarok for audio and VLC for Video

2. OO.o is the best but KOffice is available

3. The gstreamer plugins and codecs (see the multimedia and video sticky- The Comprehensive Guide - [Click me]("http://ubuntuforums.org/showthread.php?t=766683"))

4. GIMP is best although Kolourpaint is an MS Paint style light editor. DigiKam (sp?) could work.

5. Kopete, Pidgin will work but has gnome dependencies whereas Kopete comes by default and has webcam support. Skype has VoiP support although Kopete might too.

6. KPDF is fine for reading and writing pdf files although a firefox plugin for pdf is available. ```
sudo apt-get remove mozplugger && sudo apt-get install acroread acroread-plugins mozilla-acroread
```

7. clamtk with the KlamAV frontend will be fine although security in windows works equally well.

---

Notes.

Amarok, (OO.o/KOffice), GIMP, (kolourpaint), Kopete and KPDF are all defaults in kubuntu.
The rest of them apart from adobe are for KDE in particular so there will be minimal dependencies.

---

### Post by philinux on 2008-11-04
You could use ext3 as this supports it.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Have a look at the faq's

---

### Post by cl0ckwork on 2008-11-04
> **TOMM_1230 said:**
> 

And Pigin can access AIM user accounts by default?  How does it do that without breaking any laws?

pidgin can access AIM,MSN, Yahoo, Bonjour, IRC, ICQ, Myspace IM, Google talk, Facebook chat, and many others supported.

there are no restictions to what network is used, its free :)

now if you had to pay to access AIM or any other, that would be a whole other story...

---

### Post by kazuni on 2008-11-16
1) WMP - as a all-in-one media player. I am looking for the ability to play everything and ease of use.

-I used MPC for a long time, now I use smplayer (a gui wraparound for mplayer, works for almost all codecs i found so far, with winehq's codec pack)

2) Office '03 - I know '07 is out but my wife and Mother-In-Law neither one are familiar with it and are intimidated by it (Great time to switch them to Linux.) Is OO.o the best solution?

-OpenOffice 3.0, possibly wine-emulate installing office 2007 (which i did and works wonderfully).

3) Plugins for Firefox to make it as simple to use as IE when comes to everything opening. (Including Real music/video, Flash, and Java.)

-don't get what you mean here, but ies4linux may suit your needs.

4) Photo Editing - My wife wants this for scrapbooking and I just use whatever came with my printer lexmark photo studio or whatever now so advice on a more advanced one would be appriciated.

gimp, hands down. or cs2 on wine.

5) I need AIM for school can that be ran on Linux? If not can I get to my AIM acount from a Linux App?

-I use aMSN for msn only, but again, pidgin works wonderfully with it.

6) Acrobat - can it be ran on linux or is KPDF the best there is?

-tons of 3rd party pdf readers in linux.

7) A Anti-Virus for Linux. I know Linux is not succeptable, however, My system is dual boot and I do not want Window infected while I am running Linux (also I am using the EXT2 driver so Windows can get to my linux drive natively so it really is succeptable) so I want a AV for Linux. (I do not care if it is needed, I want it so please do not try to convince me otherwise. Any posts advising me not to get an AV will be reported as argumentative. Sorry, I want this for my computer. If you want to help me, help me do it my way, I am not about to change my mind.

-you rarely need any antivirus on linux. I don't install one myself :P

---

### Post by FrostDust on 2008-11-17
It'd probably make it stand out compared to the themes of other apps, but there are several Internet Explorer skins for FireFox,such as [this one]("https://addons.mozilla.org/en-US/firefox/addon/8885"), if you wanted to further help your mom in making the transition between browsers.

---

### Post by Yudraciell on 2008-11-17
> **TOMM_1230 said:**
> This is not argumentative... You still gave me info "ClamAV" which seems to be the hands down winner here, I had heard that Avast had a good AV for Linux in another forum as well.

As for Safe browsing practices > any a/v available, that may be true, as well as Linux can not directly infect Windows maybe true but Windows will have direct native access to my Linux drive.  So if I pick up a Windows Virus while in Linux I am worried that it can go in a back door on my next boot into Windows before my Windows AV is loaded.  It is a long shot I know but if there is a one in a million shot I would still rather be safe than sorry.  I would like to get away from the dominance of MS and the unbelivablely high cost of MS products but with school and most High end games (mostly for me "Mass Effect" and new RPG's) being completely dependent on MS software it is a permanent part of my life.:cry:

And Pigin can access AIM user accounts by default?  How does it do that without breaking any laws?

well ur kinda screwed on the gaming part... there is a substitute....but it is nowhere near perfection "WINE" it utilizes dx and makes it readable by OGL, and watnot...

and for pigeon to access aim....easy they have permission and have gotten the protocols for the servers used to relay messages

---

### Post by tomtom1982 on 2008-11-17
*As for Safe browsing practices > any a/v available, that may be true, as well as Linux can not directly infect Windows maybe true but Windows will have direct native access to my Linux drive. So if I pick up a Windows Virus while in Linux I am worried that it can go in a backdoor on my next boot into Windows before my Windows AV is loaded.*

Well, where do you think the virus will be installed? On your Linux machine it wouldn´t find such directories like C:/WINDOWS or something else. I can´t imagine that a windows virus will be work in folder /home/username or someone else. And if you aren´t mounting your Windows Partition automaticly, the virus won´t get access to it.

---

### Post by egalvan on 2008-11-17
As for the Ubuntu/Kubuntu (Gnome/KDE) arguments, don't let anyone tell you that apps from one won't run on the other.

I have been running both Gnome and KDE desktops for the last two years.

On my "heavy iron" machines (2-4 gigs of RAM, higher-speed CPU) I do a full install of Ubuntu, then use Synaptic to install the full KDE and Xubuntu environments.
I run them all.

Apps from one run on the other.

On my lighter-weight machines (256 to 512 megs RAM, maybe 1 gig, slower P-III CPU) I usually run Fluxbox on a minimal Ubuntu install.

Or I run Puppy.


But realize that Gnome has full customizations, and can be made to emulate Windows quite well....

As does KDE...

Use what you like, and what works for you. Ultimately, it's your choice... which is one of the greatest strengths of our GNU/Linux community.

ErnestG

---

### Post by LowSky on 2008-11-17
I will point out that AIM does have a Linux version. [www.aim.com](www.aim.com)
There are alot off issues with it, the first being it is really out of date, and I don't know anyone who can actually get it installed and working properly. Pigin is the best option, and to bring up the leagal issue, it sort a grey area, Pidgin used to be called Gaim, but AOL had an issue with the name, so they changed it. It seems that while it may work with their networks the IM companies are not seeing any revenue from the use like they would from their own applications from advirtisement, so that may  become an issue later on. We will see.

---

