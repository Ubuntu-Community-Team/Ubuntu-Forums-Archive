---
title: "Youtube and MP4 playback"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by kevin74 on 2014-04-09
I just installed 12.04.4 LTS last week, and aside from a few issues with Calc not being able to deal with some old large Excel files I'm really enjoying my experience with Ubuntu. I have an old Compaq computer AMD 2400 64 bit 1.7GB ram, problem I'm having is with audio video sync in Youtube when the video is displayed in full screen also cpu usage is at 100%, I don't have this issue when I run view full screen in Windows XP. My question is this a plugin issue for firefox a Ubuntu only issue or widespread in other Linux distros for an older weaker PC. Is there anything I can do to resolve it? The mp4 problem is sound related and the sound is clipping, checked the file in both of my windows 7 pcs and it's not the file. Thanks for any help.

---

### Post by grier-devon on 2014-04-09
Welcome to Ubuntu, I am unsure of your graphics with AMD but it might have to do with Unity is graphic intense on hardware. Probably Xubuntu would work better for your needs as xfce desktop uses far less GPU then Unity. Also install the "Ubuntu Restricted extra's" in the software center as those will ensure you get all your codecs for video and audio playback.

As for Firefox and Flash, Adobe no longer supports Flash for Linux. SO the one available for Firefox is a older flash plugin and I would recommend using Chrome as it has built in flash support. If you prefer to stay open source as possible then install Chromium and then install the pepper plugin in terminal with these commands....
For Ubuntu and flavors 12.04 - 13.10
```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo add-apt-repository ppa:skunk/pepper-flash
[/FONT][/COLOR]sudo apt-get update
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install pepflashplugin-installer[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install gksu #it`s not installed by default in Ubuntu 13.04
[/FONT][/COLOR][COLOR=#000000][FONT=UbuntuBeta Mono]gksu gksu gedit /etc/chromium-browser/default[/FONT][/COLOR]
```
For Ubuntu and flavors 14.04
```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo apt-get install pepperflashplugin-nonfree[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=UbuntuBeta Mono]sudo update-pepperflashplugin-nonfree --install[/FONT][/COLOR]
```

---

### Post by kevn57 on 2014-04-09
Thank you very much for the help, I will try out what you said, I had already installed the restricted but haven't tried Chrome or a different plugin I'll try those out when I get home from work and I think I'll wipe out the XP partition and install either Xubuntu or Lubuntu. Could you tell me is Xubuntu or Lubuntu the lighter distro.

---

### Post by grier-devon on 2014-04-09
Lubuntu is less heavy, I prefer Xubuntu but Lubuntu will provide a more traditional XP look out of the box and if you like the look of XP there are some ways to make Lubuntu look just like XP...

[http://www.omgubuntu.co.uk/2014/04/windows-xp-theme-lubuntu](http://www.omgubuntu.co.uk/2014/04/windows-xp-theme-lubuntu)

With the video playback it is going to be linked to Unity being to heavy graphics wise, so you should notice it fixed in using either Xubuntu and Lubuntu. The only reason I would pick Xubuntu over Lubuntu is I believe and could be wrong but Lubuntu first LTS is going to be 14.04 which means Lubuntu 12.04 release is no longer supported. Xubuntu on the other hand 12.04 is an LTS which means it has the same life cycle as Ubuntu, plus if your current computer can run Unity then Xubuntu will feel lighting fast.

Lubuntu System requirements:
> [COLOR=#666666][FONT=Ubuntu]A Pentium II or Celeron system with 128 MB of RAM is probably a bottom-line configuration that may yield slow yet usable system with a reduced lubuntu desktop.[/FONT][/COLOR]

Xubuntu System Requirements:
> [COLOR=#333333][FONT=Open Sans]To install and run the Xubuntu 12.04 release, it is strongly recommended to have at least [/FONT][/COLOR]**512 MB**[COLOR=#333333][FONT=Open Sans] of memory. Installing with the alternate or Minimal CD requires you to have only 128 MB of memory.[/FONT][/COLOR]

---

### Post by mörgæs on 2014-04-09
The requirements for Lubuntu are out of touch with the real world. It might be possible to install something on 128 MB but it will be useless. 
512 MB is minimum and 1 GB is recommended.

For both Lubuntu and Xubuntu I recommend 13.10 (or the beta version 14.04).

---

### Post by kevn57 on 2014-04-11
I did try Chrome and still had the same issue, then I wiped out the XP partition and loaded Lubuntu along side Ubuntu and still same sync issues with youtube in full screen. Lastly I installed VLC and streamed through that and that seems to do the trick. Thank you so much for the help.

---

### Post by kevn57 on 2014-04-11
Thanks, I have another old PC with XP this weekend I'm going to install  Xubuntu on that way I'll have 3 versions to compare U,L and X.

Sorry for the double post, I can't find anyway to delete a post.

---

### Post by mörgæs on 2014-04-11
There's no way to delete a post for a user. If you want it removed please use the 'report' button.

If we are going to take a better look at the problem please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

