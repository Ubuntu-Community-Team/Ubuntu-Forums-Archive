---
title: "how to see and download videos from youtube"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by johnlvs2run on 2008-06-09
I just downloaded ubuntu, and am wondering how to see and download videos from youtube.

When I click one, it says "click here to download plugin", but nothing happens when it's clicked.

I'd rather not get a huge library of things, but just a basic program or two, to see and download the videos.

Thanks.

---

### Post by Grishka on 2008-06-09
> **johnlvs2run said:**
> I just downloaded ubuntu, and am wondering how to see and download videos from youtube.

When I click one, it says "click here to download plugin", but nothing happens when it's clicked.

I'd rather not get a huge library of things, but just a basic program or two, to see and download the videos.

Thanks.

you need to install the flashplugin-nonfree package. be sure to enable multiverse in software sources.

---

### Post by johnlvs2run on 2008-06-09
Thanks.  

Is there a terminal command for that.  What does the nonfree part mean.

I'm looking for open source, not proprietary.

---

### Post by Grishka on 2008-06-09
> **johnlvs2run said:**
> Thanks.  

Is there a terminal command for that.  What does the nonfree part mean.

I'm looking for open source, not proprietary.

in that case, you'll have to use gnash or swfdec. the commands to install are, respectively:
sudo aptitude install mozilla-plugin-gnash
sudo aptitude install swfdec-mozilla

edit: oh yeah, don't get both of them at once.

---

### Post by johnlvs2run on 2008-06-09
Thanks.  :)

---

### Post by johnlvs2run on 2008-06-09
> **Grishka said:**
> gnash or swfdec. the commands to install are, respectively:
sudo aptitude install mozilla-plugin-gnash
sudo aptitude install swfdec-mozilla

I typed sudo aptitude install mozilla-plugin-gnash, clicked a page in youtube and it's blank.

Maybe it's my drivers?  This is a new computer.

Should gnash be working now, or is it my computer?

---

### Post by Sinkingships7 on 2008-06-09
Did you do both commands? He said not to...

---

### Post by johnlvs2run on 2008-06-09
I typed the command line for gnash:
sudo aptitude install mozilla-plugin-gnash
turned firefox off and back on
clicked a page in youtube
and the space for the video is blank.

Shouldn't it be working now, or is something else needed.

Perhaps relatedly, there's a red arrow pointing downward at the upper right top panel
that says there are 151 updates.  Do I really need to have 151 updates?

---

### Post by Grishka on 2008-06-09
that's why I first advised to install adobe's plugin. gnash and swfdec have some problems with certain flash movies. but see if gnash installed correctly. type: "about: plugins" (sans space, damn emotes...) in firefox's address bar, and see if gnash is associated with flash movies. if it is, but won't work, try swfdec. but remove gnash first. also, be sure to restart firefox after installing each plugin.

---

### Post by johnlvs2run on 2008-06-09
> **Grishka said:**
> that's why I first advised to install adobe's plugin. gnash and swfdec have some problems with certain flash movies. but see if gnash installed correctly. type: "about: plugins" (sans space, damn emotes...) in firefox's address bar, and see if gnash is associated with flash movies. if it is, but won't work, try swfdec. but remove gnash first. also, be sure to restart firefox after installing each plugin.

Thanks for your help.

I typed about:__plugins and gnash is showing up at the bottom of the page under flash.

Others showing up are itunes application detector, vlc plugin, demo print plugin, totem plugin, helix plugin, wmp plugin, quicktime plugin, and shockwave flash gnash plugin at the bottom.

---

### Post by bluepowder7 on 2008-06-09
you're not running the 64-bit version by any chance, are you?

---

### Post by johnlvs2run on 2008-06-09
As far as I know it's the 32-bit version.

Ubuntu didn't see the Sata HD and I had to change the Bios to Achi.  The driver CD finally uploaded
after Ubuntu, but I think still not installed.  I just now went to system > administration > hardware
drivers and it says the Nvidia driver is not enabled, but that it's for accelerated effects.  Is that an issue 
or not important?

---

### Post by adobrakic on 2008-06-09
[http://vixy.net/](http://vixy.net/)

---

### Post by jon8105 on 2008-06-09
I had problems at first trying to view videos, but installing "flashplugin-nonfree" from the repositories(using Synaptic) fixed it for me.

---

### Post by johnlvs2run on 2008-06-09
Thank you.

I typed > sudo aptitude install flashplugin-nonfree > in the terminal,
turned firefox off and back on - still getting a blank for the videos.

system > administration > software sources > multiverse is enabled

---

### Post by jon8105 on 2008-06-09
> **johnlvs2run said:**
> Thank you.

I typed > sudo aptitude install flashplugin-nonfree > in the terminal,
turned firefox off and back on - still getting a blank for the videos.

system > administration > software sources > multiverse is enabled

Ok, after this didn't work I went to Break.com and YouTube and was unable to view videos (even though I would yesterday).  However, once I went to System>Administration>Update Manager, checked for updates and installed them, I was able to view the videos again.

So, once you have "flashplugin-nonfree" installed go and check for (and install) any updates your Update Manager shows and see if that fixes it.

---

### Post by johnlvs2run on 2008-06-09
There are 151 updates, do I need to install all of them?

---

### Post by jon8105 on 2008-06-09
I would.  I always install the updates they provide.

---

### Post by johnlvs2run on 2008-06-10
"An error occurred".
E: Could not get lock /var/cache/apt/archives/lock - open 
(11 resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by jon8105 on 2008-06-10
> **johnlvs2run said:**
> "An error occurred".
E: Could not get lock /var/cache/apt/archives/lock - open 
(11 resource temporarily unavailable)
E: Unable to lock the download directory

Are you using "apt get" or the "update manager"?  Also, make sure you only have one of those running at a time (I think that causes a problem).

---

### Post by cariboo on 2008-06-10
You 've probably got update-manager and synaptic runnig close one of them.

Jim

---

### Post by steveking on 2008-06-10
YouTubeRobot.com today announces YouTube Robot 2.0, a tool that enables you to download video from YouTube.com onto your PC, convert it to various formats to watch it when you are on the road on mobile devices like mobile phone, iPod, iPhone, Pocket PC, PSP, or Zune.

YouTube Robot allows you to search for videos using keywords or browse video by category, author, channel, language, tags, etc. When you find something noteworthy, you can preview the video right in YouTube Robot and then download it onto the hard disk drive. The speed, at which you will be downloading, is very high: up to 5 times faster than other software when you download a single file and up to 4 times faster when you download multiple files at a time.

Manual download is not the only option with YouTube Robot. You may as well schedule the download and conversion tasks to be executed automatically, even when you are not around. Downloading is followed by conversion to the format of your choice and uploading videos to a mobile device (if needed). For example, you can plug in iPod, select the video, go to bed, and when you wake up next morning, your iPod will be ready to play new YouTube videos.

Product page: [http://www.youtuberobot.com](http://www.youtuberobot.com)
Direct download link: [http://www.youtuberobot.com/download/utuberobot.exe](http://www.youtuberobot.com/download/utuberobot.exe)
Company web-site: [http://www.youtuberobot.com](http://www.youtuberobot.com)
E-mail: [email]support@youtuberobot.com[/email]

---

### Post by johnlvs2run on 2008-06-10
They are downloading after rebooting.  It is taking awhile.

I'll check youtube when they're done.

---

### Post by hovzio on 2008-06-10
try this firefox plugin for downloads:

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

Its the best thing I've tried so far.

---

### Post by johnlvs2run on 2008-06-10
Updates downloaded, installed and rebooted.

Youtube is still showing a blank screen, instead of the videos.

---

### Post by jon8105 on 2008-06-10
I am definitely not the most experienced Linux user (actually only been using it for a few months), but I would now uninstall any flash plugins you might have downloaded and start back over by downloading from the Synaptic Package Manager.  That is where you are downloading the "plugin-nonfree" java runtime from, right?

There might be a better solution, but I don't know of it.  :)

---

### Post by cariboo on 2008-06-10
I would suggest installing **ubuntu-resricted-extras** using synaptic. This will install most of the codecs you need for playing most music and video files. It will also install java.

Jim

---

### Post by jon8105 on 2008-06-10
> **cariboo907 said:**
> I would suggest installing **ubuntu-resricted-extras** using synaptic. This will install most of the codecs you need for playing most music and video files. It will also install java.

Jim

Ah, yes, I forgot about having to download ubuntu-restricted-extras.  Hopefully that will solve your problem.

---

### Post by johnlvs2run on 2008-06-10
> **jon8105 said:**
> I am definitely not the most experienced Linux user (actually only been using it for a few months), but I would now uninstall any flash plugins you might have downloaded and start back over by downloading from the Synaptic Package Manager.  That is where you are downloading the "plugin-nonfree" java runtime from, right?

There might be a better solution, but I don't know of it.  :)

I downloaded flash from the terminal.  Right now I'm having major video issues trying to get 1440x900 resolution instead of 800x600.  First the screen came out all streaked, had to do a complete reinstall, tried again, ended up with a black screen.  Now it's running from the liveCD while I'm trying to figure out how to get into the harddrive before doing anything else.  I think also my sound is not working.  :(

---

### Post by aktiwers on 2008-06-10
You could also use Movie Player.
Go to Edit=>Plugins and enable YouTube Browser

Then Pick YouTube instead of Playlist. :) I love this!!

---

### Post by hadjimurad on 2008-06-14
> **Grishka said:**
> in that case, you'll have to use gnash or swfdec. the commands to install are, respectively:
sudo aptitude install mozilla-plugin-gnash
sudo aptitude install swfdec-mozilla

edit: oh yeah, don't get both of them at once.

I got swfdec-mozilla and it fixed my problem, I was having the same issue. I had gnash before and it didn't work. Thanks!

---

