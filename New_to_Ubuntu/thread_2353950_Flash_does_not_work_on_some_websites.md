---
title: "Flash does not work on some websites"
date: 2017-02-26
forum: New to Ubuntu
---

### Post by q123q on 2017-02-26
Hi All,

my problem is that the flash does not work on some websites.It works on Youtube, BBC,Vimeo, etc.But on some sites it does not.
Got a right click in the flash window,then got this:


Player Information
General
Version     5.11.4
Plugins
Name     Version     Active
social     unknown     yes
Source
Current Playback Tech     Html5
Current Media Type     
Current Bandwidth     unknown
Media Bytes Transferred     unknown
Media Requests     unknown
Media Transfer Duration     unknown
---------------------END---------------------------------

Other option in the flash window is to visit this link:
[https://www.brightcove.com/en/](https://www.brightcove.com/en/)

Any idea?

What I've tried,and did not work:

As of 16.04, Fresh Player is available in the official repositories. Installing is as simple as:

 sudo apt-get install browser-plugin-freshplayer-pepperflash

However, if you still want the most up-to-date version, you can add the PPA:

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install browser-plugin-freshplayer-pepperflash

This will install the actual player, but it still needs an extra file. This file is the actual pepperflash library used by the player. To get it, you can use a PPA:

sudo add-apt-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer

--------------------END--------------

Other thing I've tried, and did not work, error msg:
sudo apt-get install hal
-------END-------

Any idea?

Lubuntu  16.04 LTS

Thanks.

---

### Post by him610 on 2017-02-26
Solution to issue is in problem statement "flash does not work on some websites."

Did your mother not advise you to avoid websites? There is no telling what you might catch there. ;)

---

### Post by &amp;KyT$0P# on 2017-02-26
> **q123q said:**
> my problem is that the flash does not work on some websites.It works on Youtube, BBC,Vimeo, etc.But on some sites it does not.
Got a right click in the flash window,then got this:


...
Current Playback Tech     Html5
:confused:

Err..."Html5" means, er, not Flash.  Are you having problems with Flash or HTML5?

---

### Post by q123q on 2017-02-27
Hi All,

it should play a video.Like the flash does on youtube etc... it is some dodgy ufo watch sites, not my pc, I just trying to make it work.Others also wrote that the Ubuntu often does not play videos in  web players.I assumed that it is flash.I don't know what it is.I just wanna make it work.

---

### Post by lysander6662 on 2017-02-27
> **him610 said:**
> Solution to issue is in problem statement "flash does not work on some websites."

"Some websites"...hmmm

I think the confusion is arising from the fact that YouTube does not use Flash anymore but HTML5. I think he means Flash.

---

### Post by howefield on 2017-02-27
Perhaps you could share a link to one of the "dodgy ufo watch sites" ?

If that conflicts with the forums Code of Conduct, then pm it to me and I'll take a look.
> 
Users agree not to post anything abusive, rude, obscene, vulgar, slanderous, hateful, threatening, advertising or marketing related, or sexually-oriented. Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. Given that our forums could be used by people at work and school we want to ensure they will not encounter material that will cause them problems or cause their access to our site to be limited, so all content should be safe for both.

At the minute I'd suggest purging the flash that you have and installing the adobe-flashplugin package from the Canonical Partners repository instead.

---

### Post by nevertellmetheodds on 2017-03-10
Have you tried using Google Chrome?

---

### Post by &amp;KyT$0P# on 2017-03-10
> **nevertellmetheodds said:**
> Have you tried using Google Chrome?
If you are going to go that route, I suggest trying Chromium browser instead of Chrome.  Chromium is available in the standard repositories, which makes it easier to install -
```
sudo apt-get install chromium-browser
```

---

### Post by norafaithrainbow on 2017-03-15
As previously stated, I would suggest downloading chromium or chrome. Chrome is preferable if you have a 64 bit os. Just go to the download page, download it, open your downloads folder and click the file. This should open the software center where you can install it.

---

### Post by Geoffrey_Arndt on 2017-03-15
Be careful what you install (such as HAL).    You don't want to introduce instability or worse into the system.   [COLOR=#252525][FONT=sans-serif]HAL is now [/FONT][/COLOR][deprecated]("https://en.wikipedia.org/wiki/Deprecation")[COLOR=#252525][FONT=sans-serif] on most Linux distributions and on FreeBSD (per wikipedia & forum members).[/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2017-03-15
> **norafaithrainbow said:**
> Chrome is preferable if you have a 64 bit os.
How so?

---

### Post by norafaithrainbow on 2017-03-21
> **halogen2 said:**
> How so?

I've found that not everything that can run on chrome, runs on chromium, like facebook video, and certain games that require flash.

---

### Post by &amp;KyT$0P# on 2017-03-22
> **norafaithrainbow said:**
> I've found that not everything that can run on chrome, runs on chromium, like facebook video, and certain games that require flash.
Ah.  That is because Chrome bundles Flash, but Chromium does not.  Installing Flash ([FONT=Courier New]sudo apt-get install adobe-flashplugin[/FONT]) should close that gap.

* Correction: Apparently the version of Chrome I have on hand is really old.  Chrome 57, the current version, does not "bundle" Flash, but it seems to automatically download it.

---

### Post by sp40140 on 2017-03-22
Ubuntu restricted extras. That's the second package I install from synaptic (1st is synaptic). These restricted extras install things which make life considerably easier. And flash plug-in is part of it.

---

### Post by sp40140 on 2017-03-22
Chorme for 32bit system has been discontinued by Google for a while now. So, if you have 32bit system, you should go with chromium. I use Firefox (primary)and Vivaldi (secondary).

Cheers,

---

### Post by Dennis N on 2017-03-22
Could be a DRM problem. Some web sites use DRM support in the browser for flash video to work; in the U.S., notably t.v. network web sites; almost all of these still have only flash video. The hal flash package used to handle this with old flash player 11.2 series and Firefox; the new versions 24 and 25 are not compatable with hal flash any longer.

Best solution may be to install wine and the Windows version of Firefox, which does support DRM. I did this myself and it works.

---

