---
title: "Flash Player in Firefox &amp; Chrome"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by don62 on 2014-12-18
Not sure where to put this problem, but let's give this a go.

 I am now totally confused. Let me first say I am a ubuntu newbie & know nothing.

 I recently upgraded to ubuntu 14.04 LTS & was very happy until a few days ago when BBCiPlayer, ITVplayer & all my applications that streamed video in Firefox failed, displaying the message  

 &#8220;Failed to load libpepflashplayer.so&#8221;
 I checked these forums & saw that there were various problems concerning EOL ubuntu versions, but it didn't seem that 14.04 was affected. Nevertheless, I have tried various  suggested  &#8220;sudo&#8221; solutions to try & restore my  streaming video, none of which have worked. Another suggestion has been to use Chrome as my browser but when I do that, whichever application I am using, being BBCiPlayer or whatever informs me  &#8220;Click to continue - We need to upgrade your Flash Player&#8221;

 I am then presented with a choice of 4 versions:-

 YUM for Linux (YUM)
 .tar.gz for other Linux
 .rpm for other Linux
 APT for Ubuntu 10.04+
 

 I have tried all 4, all to no avail.
 Can any STAR please inform me in simple terms what I need to do to bring light back into my life.

---

### Post by grahammechanical on 2014-12-18
Have you tried using the Ubuntu Software Centre? Search for Flash and you should get the offer to install Adobe Flash Plugin Installer. For those of us using Chrominum, then search for Pepper Flash and get an offer to install Pepper Flash Plugin-nonfree.

Right now I am using BBC iplayer to listen to an episode of  Bob Harris Country. I am using Chromium to do this. And I am on the development version of the next release of Ubuntu so it should still be possible to do this on 14.04 and 14.10.

Regards.

---

### Post by don62 on 2014-12-18
[COLOR=#000000][[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323") [/COLOR]
[COLOR=#000000][/COLOR][IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  You are my HERO!
Worked a treat for Chromium, but as you probably already know, it made no difference to Firefox.
Who cares! I've got my catchups back.
What about all these "sudos" I've tried unsuccessfully?
Are they going to leave loads of worthless rubbish on my laptop, or is there a way of
getting rid of "stuff" that is no use to man or beast?
I'm already in your debt, so don't bother to respond if you don't know.
Cheers.
Don.

---

### Post by ajgreeny on 2014-12-18
BBC-iPlayer works fine in firefox with flash 11.2.202; I have just tried it and there is no problem at all, so either your flash is not set up properly or you have some other problem with your machine.

There is a way of getting the pepperflash into firefox but I have not bothered yet as the latest version available for FF in the repos still works fine whenever I try it on any site, including BBC-iPlayer, 4OD, ITV-player, so I am mystified.

Just one sudden thought!
4OD, and maybe other  TV catchup services, requires that the system has **hal** installed which is no longer available in the standard repos for 14.04; you need to get it from the ppa at [https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal) and install it in the usual way.

---

### Post by don62 on 2014-12-18
Many thanks for your input, ajgreeny.
Will follow up your suggestions later.
Cheers.
Don.

---

