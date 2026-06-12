---
title: "Streaming radio suddenly no longer works."
date: 2012-07-22
forum: New to Ubuntu
---

### Post by MibunoOokami on 2012-07-22
Hi all,

I like to stream radio from [www.tunein.com](www.tunein.com) with firefox, it's always worked fine for me until recently. It says that it's streaming and reliable to 98% of users, but I can't hear anything. I've been through all the troubleshooting points, I've tried searching about streaming and even installed chromium, nothing works. Unfortunately, tunein.com needs to play in a browser, I tried making it work through vlc but failed. Last but not least, I've also tried streaming from different websites and for whatever reason it just won't work anymore.
Troubleshooting tips were to check media support, install restricted drivers (already installed) and install gstreamer codecs (also already installed).

Does anyone have any idea why out of the blue I just can't stream anymore? Or better yet, how I can fix this please?

---

### Post by jmfal on 2012-07-22
I  just played some music from "tunein"

not all stations worked, most did, using vlc player

not sure what you should do
can try purging vlc and reinstalling

---

### Post by bobsan on 2012-07-22
Just tried your link, they all work in FF. But you need flash to play them in the browser, so maybe you have a flash problem? Did you  install flashblock?

---

### Post by MibunoOokami on 2012-07-23
> **jmfal said:**
> I  just played some music from "tunein"

not all stations worked, most did, using vlc player

not sure what you should do
can try purging vlc and reinstalling

I'm not sure how to purge VLC. Google keeps bringing up how to install it.

---

### Post by MibunoOokami on 2012-07-23
> **bobsan said:**
> Just tried your link, they all work in FF. But you need flash to play them in the browser, so maybe you have a flash problem? Did you  install flashblock?

I'm not sure what flash block is, just looked at addons and plugins, that's not in there. How do I know if I have a flash problem?
The tunein team emailed me today to say update moonlight (silverlight), I did that and restarted firefox but still no dice.

---

### Post by bobsan on 2012-07-23
> **MibunoOokami said:**
> I'm not sure what flash block is, just looked at addons and plugins, that's not in there. How do I know if I have a flash problem?
The tunein team emailed me today to say update moonlight (silverlight), I did that and restarted firefox but still no dice.

You can check if flash is working by going to a flash site like dailymotion.com. I was about to suggest Youtube but many youtube videos have html5 version so they will play even without flash.

I have no idea what moonlight has to do with it. I tried all the links and they all work, I don't have moonlight on my computer.

EDITED: Hmm.. interesting, they all work in Firefox, but half of them don't work in Chrome. Maybe pepper flash is not compatible with some of these?

---

### Post by NikTh on 2012-07-23
Hi , 
i tested the site you given and plays good. No matter if i am 96% users reliable :P 

It plays from within Firefox. 
So try to install (or reinstall) Ubuntu-restricted-extras..

1) ```
sudo apt-get install ubuntu-restricted-extras
```Also , try other stations , it seems not all stations play well. 

2) Last thing , see if you have flash player installed correct. 
```
apt-cache policy adobe-flashplugin flashplugin-installer
```

3) and as last resort , you can reinstall Firefox . You must delete hidden folder .mozilla too. 
But you will lose any bookmark you have , so its wise to do a bookmarks backup fist.
If you want further assistance post back here.

Thanks

---

### Post by MibunoOokami on 2012-07-23
> **NikTh said:**
> Hi , 
2) Last thing , see if you have flash player installed correct. 
```
apt-cache policy adobe-flashplugin flashplugin-installer
```3) and as last resort 
Thanks

This is what came out when I entered that code. I don't know if I'm reading that correctly, I've got the flashplugin installer, but not adobe-flashplugin is that right?

 apt-cache policy adobe-flashplugin flashplugin-installer
adobe-flashplugin:
  Installed: (none)
  Candidate: (none)
  Version table:
flashplugin-installer:
  Installed: 11.2.202.236ubuntu0.12.04.1
  Candidate: 11.2.202.236ubuntu0.12.04.1
  Version table:
 *** 11.2.202.236ubuntu0.12.04.1 0
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise-updates/multiverse amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     11.2.202.233ubuntu2 0
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) precise/multiverse amd64 Packages

---

### Post by NikTh on 2012-07-23
Hi , 
yes its ok . If you have 64bit version of Ubuntu , then flashplugin-installer its the appropriate package.
Do you have any other  problems, like streaming video ? e.g youtube ? 

Give the results of 
```
 ls /usr/lib/mozilla/plugins/
```

You can try other suggestions , if you want.

Thanks

---

### Post by MibunoOokami on 2012-07-23
> **bobsan said:**
> You can check if flash is working by going to a flash site like dailymotion.com.

Thanks, just went to dailymotion.com, it worked OK, sound was a little scratchy here and there.

---

### Post by MibunoOokami on 2012-07-23
> **NikTh said:**
> Hi , 
yes its ok . If you have 64bit version of Ubuntu , then flashplugin-installer its the appropriate package.
Do you have any other  problems, like streaming video ? e.g youtube ? 

Give the results of 
```
 ls /usr/lib/mozilla/plugins/
```You can try other suggestions , if you want.

Thanks

I have no problems with video streaming. These are the results

flashplugin-alternative.so             libtotem-gmp-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-mully-plugin.so
libtotem-cone-plugin.so                libtotem-narrowspace-plugin.so

---

### Post by NikTh on 2012-07-23
Hi , 
ok , so its not a problem with flash player. 

Did you reinstall ubuntu -restricted - extras ? 
also i noticed that streaming in that page its not very good. I had corruptions from time to time. 
So maybe at the end its not your problem , but page's problem.  (or slow connection problem)
You can wait one-two days and try again. 

Thanks

---

### Post by MibunoOokami on 2012-07-23
> **NikTh said:**
> Hi , 
ok , so its not a problem with flash player. 

Did you reinstall ubuntu -restricted - extras ? 
also i noticed that streaming in that page its not very good. I had corruptions from time to time. 
So maybe at the end its not your problem , but page's problem.  (or slow connection problem)
You can wait one-two days and try again. 

Thanks

Hi,

sudo apt-get install ubuntu-restricted-extras
[sudo] password for mno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 liboil0.3:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by NikTh on 2012-07-23
> **MibunoOokami said:**
> Hi,

[B]The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 liboil0.3:i386[/B]
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Hi , 
you can safely remove these packages .. 
open a terminal and ```
sudo apt-get autoremove
```Thanks

---

### Post by MibunoOokami on 2012-07-24
> **NikTh said:**
> Hi , 

So maybe at the end its not your problem , but page's problem.  (or slow connection problem)
You can wait one-two days and try again. 

Thanks

I think it is at my end, because no stations work. Thanks.

---

### Post by madjr on 2012-07-24
maybe you can try other methods to listen to radio, like radio tray:

[http://www.webupd8.org/2011/12/radio-tray-gets-plugins-support.html](http://www.webupd8.org/2011/12/radio-tray-gets-plugins-support.html)



Also there seems to be some integration for radio soon, if you use unity:

[http://www.iloveubuntu.net/upcoming-unity-60-feature-rhythmboxs-radio-support-unity-music-lens](http://www.iloveubuntu.net/upcoming-unity-60-feature-rhythmboxs-radio-support-unity-music-lens)

---

### Post by MibunoOokami on 2012-07-24
> **madjr said:**
> maybe you can try other methods to listen to radio, like radio tray:

[http://www.webupd8.org/2011/12/radio-tray-gets-plugins-support.html](http://www.webupd8.org/2011/12/radio-tray-gets-plugins-support.html)



Also there seems to be some integration for radio soon, if you use unity:

[http://www.iloveubuntu.net/upcoming-unity-60-feature-rhythmboxs-radio-support-unity-music-lens](http://www.iloveubuntu.net/upcoming-unity-60-feature-rhythmboxs-radio-support-unity-music-lens)

Hi there, radio tray doesn't want to launch. I've installed, removed, reinstalled and rebooted etc, the icon just flashes at me. I wonder if it's not compatible with 64bit, I didn't see any options so assumed it covers both 32 and 64 bit machines.

I didn't realize you can't stream via rhythm box yet, so that explains why that never worked, I just figured I'd been doing something wrong. 

Thanks.

---

### Post by madjr on 2012-07-24
> **MibunoOokami said:**
> Hi there, radio tray doesn't want to launch. I've installed, removed, reinstalled and rebooted etc, the icon just flashes at me. I wonder if it's not compatible with 64bit, I didn't see any options so assumed it covers both 32 and 64 bit machines.

I didn't realize you can't stream via rhythm box yet, so that explains why that never worked, I just figured I'd been doing something wrong. 

Thanks.

maybe you can try this:

[http://www.ubuntuupdates.org/package/core/precise/universe/base/radiotray](http://www.ubuntuupdates.org/package/core/precise/universe/base/radiotray)

---

### Post by uradhalat on 2012-07-24
Live streaming is best on VLC whether its radio or live tv

---

### Post by MibunoOokami on 2012-07-25
> **MibunoOokami said:**
> Hi there, radio tray doesn't want to launch. I've installed, removed, reinstalled and rebooted etc, the icon just flashes at me. I wonder if it's not compatible with 64bit, I didn't see any options so assumed it covers both 32 and 64 bit machines.

Long story short, I learned that uninstalling and purging doesn't actually remove directories of a program, you need to do that yourself. That'll explain why the uninstall and reinstall didn't work. I've got radiotray working now, after learning I had to find specific streaming links (couldn't use the tunein ones). 
I'd like to express my gratitude for the help and the recommendation of radio tray. As it happens, using radio tray consumes a fraction of data compared with streaming through tunein. I have Gkrellm installed and when streaming through tunein it would stream around 980k - 1.2M whereas radio tray hasn't gone higher than 10.5k. 

Thanks again everyone.

---

