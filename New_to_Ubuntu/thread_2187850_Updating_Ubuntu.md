---
title: "Updating Ubuntu"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by malcolmmalcolm_19 on 2013-11-14
I am currently running Ubuntu 11.10 for the purposes of XBMC V.11 front end (I believe that is the term?). Now, I know very little about how XBMC interacts with the underlying Ubuntu install. I am having a hell of a time with the bugs in Ubuntu 11.10, can I simply upgrade to Ubuntu 12 or will it break the XBMC front end?

---

### Post by TheFu on 2013-11-14
I've been running Linux for 20+ yrs and have been running XBMC for about 2.  The best answer for you depends on many different things.

Knowing very little about your specific hardware (and getting XBMC to work well can be extremely hardware dependent), I would suggest that you:
[LIST=1]
[*]Backup the XBMC "HOME" directory
[*]Backup any local media - I keep media on a different machine
[*]Backup all machine settings - these are in /etc/
[*]Load Lubuntu 12.04 - you want an LTS release (patched until 2017), not the latest short-support release.
[*]Post-install, patch the new OS to be current with **sudo apt-get dist-upgrade**. 
[*]Find a PPA for XBMC that supports your specific hardware - don’t worry about this if it is just a regular PC; I'm running a AMD/E350 APU that needs hardware support from the GPU to work well. I'm lucky that a guy in France maintains a How-to page with all the complexities solved and documented.
* Restore the ~/.xbmc/ files to the new machine.
[*]Install XBMC - Frodo - XBMC will see the old settings/thumbnails and other stuff and upgrade them to the new data formats
[*]Update all the plugins previously installed inside XBMC. Many have stopped working, but you know the specific ones you like already.
[/LIST]

There are other XBMC specific releases that might be easier to setup if you are not Linux-centric in your computnig.  For me, Frodo was a nice update - fixed all sorts of playback issues (especially flash/youtube stuff) on my machine. 

See my signature for why you probably want to run an LTS. The next LTS will be released in April 2014. Pretty much every other release besides 12.04 will loose support/patches at that point.  Your 11.10 install lost support in 2012. Running a computer on any network without current patches is crazy. If you do decide to install any other OS, know that you'll need to install 14.04 as soon as it is releases and that 13.04 and 12.10 go out of support in January. From a patch and stability perspective, 12.04 is really the only choice for average users.

Be certain to do the backup steps.

Why didn't I suggest an "upgrade" for Ubuntu?  11.10 --> 12.04? Lots of things have changed in 12.04. I've found that upgrades leave some important things in an odd state and that confusion will make it difficult to get help. Fresh install and you NKOW exactly where the OS stands.

BTW, my core XBMC OS and Apps partition is just 20G in size. All the media is stored elsewhere, so you could disconnect the HDDs for the media and not have to backup that stuff.

Anyway, I hope this helped.

---

### Post by malcolmmalcolm_19 on 2013-11-16
TheFu,

Thanks for taking the time for that excellent reply. 

I am definitely not linux-centric in my computing. Far from it, I am a windows gamer who also likes to watch movies. As you probably gathered, I am forced to learn Linux as it goes hand-in-hand with running a decent media center. Of course, one could run windows, but I find it terribly bloated and slow for just running one program (XBMC). It is unfortunate though, that to setup the functions of a media center requires extensive configuration of the Linux subsystem with no GUI assistance. Auto-mounting media, configuring wifi, auto login, etc. Success dependent on your google-fu and persistence. I am not completely in the dark though, my initial Linux experience was with Mandrivia, about 10 years ago. I feel terribly sorry for anyone who has never touched Linux and just wants XBMCbuntu to function as a media center distro right out of the box. That is a pipe-dream.

At the time of building my media center, Frodo was already released, but I was having issues with either the XBMC Frodo or the particular Ubuntu version that came with it. Hence I reverted to (L)Ubuntu 11.10 and in turn, XBMC Eden. However, given that I have found this forum, and how active it is, I am sure I could have my problems solved.

I was under the impression that I had to choose a "pre-built" XBMCbuntu release (Ubuntu with XBMC pre-installed). I have some questions: 


[LIST]
[*]I gather I can use any recent version of Ubuntu and use any recent version of XBMC without issue? This is critical to know, because I can fully appreciate what you are saying about using an LTS release. However the latest XBMCbuntu uses Ubuntu 12.10. If I just loaded Ubuntu 12.04 (LTS) can I simply run: ```
sudo apt-get install xbmc
``` 
[/LIST]

Will that give me the same result as a pre-configured XBMCbuntu release? I still want to have XBMC as a login option in LightDM login.


[LIST]
[*]You mentioned backing up /etc/ . Is it feasible to restore the whole directory upon re installation or should I be selective? 
[/LIST]

---

### Post by TheFu on 2013-11-16
> **malcolmmalcolm_19 said:**
> TheFu,

Thanks for taking the time for that excellent reply. 
Happy it helped.

> **malcolmmalcolm_19 said:**
> 
I am definitely not linux-centric in my computing. Far from it, I am a windows gamer who also likes to watch movies. As you probably gathered, I am forced to learn Linux as it goes hand-in-hand with running a decent media center. Of course, one could run windows, but I find it terribly bloated and slow for just running one program (XBMC). It is unfortunate though, that to setup the functions of a media center requires extensive configuration of the Linux subsystem with no GUI assistance. Auto-mounting media, configuring wifi, auto login, etc. Success dependent on your google-fu and persistence. I am not completely in the dark though, my initial Linux experience was with Mandrivia, about 10 years ago. I feel terribly sorry for anyone who has never touched Linux and just wants XBMCbuntu to function as a media center distro right out of the box. That is a pipe-dream.

For $1000, I will build an XBMC machine with $200 worth of hardware. Knowledge IS worth something correct? Clearly, my pricing is not going to attract many/any buyers.

> **malcolmmalcolm_19 said:**
> At the time of building my media center, Frodo was already released, but I was having issues with either the XBMC Frodo or the particular Ubuntu version that came with it. Hence I reverted to (L)Ubuntu 11.10 and in turn, XBMC Eden. However, given that I have found this forum, and how active it is, I am sure I could have my problems solved.
Actually, the better place for XBMC answers is the xbmc forums, NOT here.

> **malcolmmalcolm_19 said:**
> 
I was under the impression that I had to choose a "pre-built" XBMCbuntu release (Ubuntu with XBMC pre-installed). I have some questions: 

No need for that, unless you have non-standard hardware or limited CPU.

> **malcolmmalcolm_19 said:**
> 
[LIST]
[*]I gather I can use any recent version of Ubuntu and use any recent version of XBMC without issue? This is critical to know, because I can fully appreciate what you are saying about using an LTS release. However the latest XBMCbuntu uses Ubuntu 12.10. If I just loaded Ubuntu 12.04 (LTS) can I simply run: ```
sudo apt-get install xbmc
``` 
[/LIST]

The way to install xbmc will depend on your needs. USING A NON-LTS RELEASE is foolish, IMHO.  Different people will want different releases of XBMC, which means the installation process may be similar or pointing to a different PPA might be highly desirable.  That is your decision to make, but I use the official XBMC PPA, NOT the Ubuntu version for XBMC.

> **malcolmmalcolm_19 said:**
> 
Will that give me the same result as a pre-configured XBMCbuntu release? I still want to have XBMC as a login option in LightDM login.
I don't know. Never used XBMCbuntu and never had a normal login on my XBMC box after the first day.

> **malcolmmalcolm_19 said:**
> 
[LIST]
[*]You mentioned backing up /etc/ . Is it feasible to restore the whole directory upon re installation or should I be selective? 
[/LIST]
It depends. I don't know your systems.

---

### Post by malcolmmalcolm_19 on 2013-11-16
I am running on standard hardware no more than 1 year old. I will backup and attempt the 12.04 install. 

Edit: I just noticed Lubuntu 12.04 isn't LTS. I might just go with Ubuntu 12.04.

> **TheFu said:**
> 

I don't know. Never used XBMCbuntu and never had a normal login on my XBMC box after the first day.



If you don't mind me asking, when you boot your media center does it boot straight to a stand-alone XBMC session or does it boot to Ubuntu and starts XBMC as an application?

---

### Post by TheFu on 2013-11-17
I always install Ubuntu Server (which is LTS), then add the GUI I want for that install ... which NEVER includes Unity.  IMHO, stock Ubuntu desktop is not worth consideration anymore.

As to your 2nd question ... Ubuntu is not the GUI, it is the OS, so of course ubuntu boots first.   There is no login, as I've swapped out the normal login manager for xbmc-standalone. It has been about 2 yrs since I did that, so I do not recall the details. Sorry.

---

### Post by malcolmmalcolm_19 on 2013-11-17
Well today I successfully setup Ubuntu 12.04 LTS and installed XBMC Frodo and it went as I had hoped. XBMC was added as a boot option in LightDM (as is the case by default with XBMCbuntu). Plenty of little issues as I expected. I did backup /etc before hand but I only used the backup as a reference for reconfiguration. The main issue I had was with sound in XBMC, it is handled differently in Frodo compared to Eden. Eden allowed a custom audio configuration which helped me get audio over HDMI. Frodo does not. For anyone who is wondering the option I used for audio was "HDA Intel PCH, CTV, CVTE, TV on HDMI #2" in the drop down box. Of course that will vary depending on your hardware. 

I know what you mean in regards to Unity. Having said that I didn't particularly like Gnome 3 either. I haven't tried the new KDE environments but I favored KDE when I was using Mandrake. Either way, being a media center I will seldom see the desktop.

Thanks for the help.

---

### Post by TheFu on 2013-11-17
Glad it worked for you. 

For others, lurking, use the **aplay -l** cmd to figure out which audio device you should use for HDMI, analog and digital (toslink/coax) uses.  I recall that changed with Frodo slightly, but within 5 minutes, it was working great again.  I have a need for both HDMI and analog audio, since the XBMC box drives both a TV and a projector.

I avoid DE bloat, preferring a pure window manager ... especially on a low-power system.

---

