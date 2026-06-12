---
title: "Adobe Flash and Plug-in Questions"
date: 2014-04-15
forum: New to Ubuntu
---

### Post by bruce17 on 2014-04-15
Just installed Lubuntu 13.10 on a dual boot WinXP laptop.During installation I DIDN'T check to install lubuntu-restricted-extras as I wasn't sure what it was for. After realizing that Firefox needed Adobe Flash player for some videos I:

sudo'd upgrade
sudo'd lubuntu-restricted-extras

Now in Youtube I often get a quick message flash by as the video starts to load saying something about needing a Flash plug-in. The video will then either open as it should or just get a black screen saying I need Adobe Flash to be installed. While either of the above is happening, there is another box open at the top of the video screen asking if I want to download the Flash plug-in. If I say "yes," it just says there is no plug-in available. Then the video sometimes plays as it should or other times I just get the black screen saying that Flash needs to be installed. Seems kind of random so far as to when a video plays and when one doesn't. I haven't tried to establish a pattern. When looking at the list of Forefpx plug-in's there is nothing there relating to Adobe, just Quicktime.

How do I know if Flash Player is really installed or if the plug-in is installed?

I thought installing lubuntu-restricted-extras was supposed to set up Flash Player. Do I need to do something else, like sudo... flashplayer-plugin?

Thanks,
Bruce

---

### Post by Impavidus on 2014-04-15
Part of the Youtube videos are available in html5/webm format. These don't need flash, so they work. The others are only available in flash format and they don't work on your computer.

lubuntu-restricted-extras (indirectly) recommends either adobe-flashplugin or flashplugin-installer (at least on 12.04, I don't know about 13.10 but assume it's similar). This should have brought you the flash player, but it seems it didn't. Either the package wasn't installed or it was not properly configured. In the last case you'd have recieved an error message.

To find out what is the case, run this command:```
dpkg --list *flashplugin*
```If neither of the above mentioned packages is installed, run```
sudo apt-get install flashplugin-installer
```It should be detected by Firefox as Shockwave Flash.

---

### Post by bruce17 on 2014-04-15
Thanks for the quick reply. I'll run those commands when I get home after work as that computer is at home. 

Bruce

---

### Post by mikewhatever on 2014-04-15
[Lubuntu-Restricted-Extras]('http://packages.ubuntu.com/saucy/lubuntu-restricted-extras') in 13.10 basically installes ubuntu-restricted-extras with its dependencies, including Adobe Flash.
You can try checking if the Adobe-Flash plugin is loaded. Type **about:plugins** in the address bar, and look for 'Shockwave Flash'.

---

### Post by bruce17 on 2014-04-15
Neither of the programs were installed. I ran the flash plugin-installer and arrived at the same place I did when I ran the lubuntu-restricted-extras. A lot of info goes by and then the screen stops at the "configuring ttf-mscorefonts-installer."  There's an <ok> at the bottom but nothing happens when you click on it. Did the installation finish and the EULA is just for informational purposes? Or do I need to select something for the process to continue? If so, what or how?

---

### Post by bruce17 on 2014-04-15
Never mind. I just found that the tab key would select the <ok>. Still learning the ropes of how this works.

---

### Post by bruce17 on 2014-04-15
OK, problem solved. Not getting past the ttf-mscorefonts EULA was the hangup. All videos work fine.

---

### Post by protoss96 on 2014-04-16
I would recommend you using google-chrome if you want latest adobe flash player version(13,0,0,182) and last supported version for Linux on other browsers is 11,2,202,350.

---

