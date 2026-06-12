---
title: "Lubuntu on low spec computers"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by JoeRizzo on 2013-06-28
[COLOR=#222222][FONT=Verdana]Hi everyone,this is my first post so apologies for what may seem like daft questions:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana] I read about installing Lubuntu on low spec computers and as I had one sitting in the corner I thought it would be a good first step into the world of Ubuntu/ Linux. Computer has CPU - 950 MHz and 256 MB ram. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Did the alternate install of lubuntu 13.04 and did the updates. Everything seems to beworking OK except for the following 2 problems:[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]First - Despite installing flashplugin installer cannot get flash player to work in Chromium of Firefox. In both browsers I get the message that Flash couldn't load. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Second - I have an ALS40000 soundcard installed. When playing music the vocals are barely audible. Have tried fiddling with the graphic equalizer in Pulseaudio but to noeffect. [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana]Any suggestionswould be appreciated.[/FONT][/COLOR]

---

### Post by snowpine on 2013-06-28
Your computer simply does not meet the minimum hardware specs for the Adobe Flash player according to [http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

```
Linux
•2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
•Red Hat® Enterprise Linux® (RHEL) 5.6 or later (32 bit and 64 bit), openSUSE® 11.3 or later (32 bit and 64 bit), or Ubuntu 10.04 or later (32 bit and 64 bit)
•Mozilla Firefox 17 or Google Chrome
•512MB of RAM; 128MB of graphics memory
```

Flash is a proprietary, closed-source product of AdobeCorp, so there is really nothing Ubuntu developers can do to modify or improve it.

My suggestion would be to download the video to your hard drive and then watch it with your favorite video player app. (My personal favorite for low-spec machiens is mplayer.)

I'm sorry but I am not familiar with your sound card.

---

### Post by JoeRizzo on 2013-06-28
Thanks for the info. What puzzles me is that previously this computer ran Windows XP with IE 8. I'm sure that I was able to watch YouTube videos under that setup.> **snowpine said:**
> Your computer simply does not meet the minimum hardware specs for the Adobe Flash player according to [http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

```
Linux
•2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
•Red Hat® Enterprise Linux® (RHEL) 5.6 or later (32 bit and 64 bit), openSUSE® 11.3 or later (32 bit and 64 bit), or Ubuntu 10.04 or later (32 bit and 64 bit)
•Mozilla Firefox 17 or Google Chrome
•512MB of RAM; 128MB of graphics memory
```

Flash is a proprietary, closed-source product of AdobeCorp, so there is really nothing Ubuntu developers can do to modify or improve it.

My suggestion would be to download the video to your hard drive and then watch it with your favorite video player app. (My personal favorite for low-spec machiens is mplayer.)

I'm sorry but I am not familiar with your sound card.

---

### Post by snowpine on 2013-06-28
My personal experience is that Flash performance is much better in XP than Linux on older hardware. It seems Adobe devotes more resources to the Windows version of the plugin. :)

---

### Post by ajgreeny on 2013-06-28
Your problem may be more related to the age of your processor and whether or not it is sse2 capable.  Use command ```
cat /proc/cpuinfo | grep sse
``` to see if there is any mention of sse2; if it is just sse your cpu is incapable of running the latest flash.

You could use a much older and now a bit unsafe version (11.1.202-63) which I used to have to use with a sempron 2400+ cpu.

Thanks to lovinglinux, a longtime ubuntu forum member, you may still be able to get that older version from [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) which has two links:-
[https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz)
[https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.x86_64.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.x86_64.tar.gz)
for the archives.  After downloading the archive, extract it using the file manager, copy the file *libflashplayer.so*  and paste into ~/.mozilla/plugins/.
You may need to make that folder first with command ```
mkdir .mozilla/plugins/
```To see that .mozilla directory under your  home, you need to show hidden files. You can do that in pcmanfm, thunar or nautilus by  hitting CTRL+H.

Be warned; there are some websites that will either totally block that old flash version or will keep on warning you that it is outdated, so I'm afraid your troubles are not completely over even if flash now works sometimes.

---

### Post by snowpine on 2013-06-28
^ awesome info, ajgreeny! :)

---

### Post by grahammechanical on 2013-06-28
Chrome has built in flash player but Chromium does not. You might find this interesting. I use it. It might solve the problem.

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

Regards.

---

### Post by JoeRizzo on 2013-06-28
> **ajgreeny said:**
> Your problem may be more related to the age of your processor and whether or not it is sse2 capable.  Use command ```
cat /proc/cpuinfo | grep sse
``` to see if there is any mention of sse2; if it is just sse your cpu is incapable of running the latest flash.

You could use a much older and now a bit unsafe version (11.1.202-63) which I used to have to use with a sempron 2400+ cpu.

Thanks to lovinglinux, a longtime ubuntu forum member, you may still be able to get that older version from [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) which has two links:-
[https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz)
[https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.x86_64.tar.gz](https://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.x86_64.tar.gz)
for the archives.  After downloading the archive, extract it using the file manager, copy the file *libflashplayer.so*  and paste into ~/.mozilla/plugins/.
You may need to make that folder first with command ```
mkdir .mozilla/plugins/
```To see that .mozilla directory under your  home, you need to show hidden files. You can do that in pcmanfm, thunar or nautilus by  hitting CTRL+H.

Be warned; there are some websites that will either totally block that old flash version or will keep on warning you that it is outdated, so I'm afraid your troubles are not completely over even if flash now works sometimes.Cheers Aj, lots of info there for me to get my teeth into.... just what I was looking for as a newbie.    Any ideas on how to get the ALS4000 soundcard working properly?

---

### Post by JoeRizzo on 2013-06-28
> **grahammechanical said:**
> Chrome has built in flash player but Chromium does not. You might find this interesting. I use it. It might solve the problem.

[http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html](http://www.webupd8.org/2013/04/install-pepper-flash-player-for.html)

Regards.Thanks m8, I have tried Chrome but it just gives the same error messages as Chromium.

---

### Post by ajgreeny on 2013-06-28
> **JoeRizzo said:**
> Thanks m8, I have tried Chrome but it just gives the same error messages as Chromium.

That is possibly for the same lack of sse2 that your cpu may have.  My sempron machine which needed the older flash version could not use pepperflash from chrome either, as that also needs sse2.

If flash works with the older version, you will probably find that chromium and google-chrome both find it, and flash should work in both of those browsers as well as Firefox.

---

### Post by kennerc on 2013-06-28
Still about the flash issue, if you're watching youtube videos, you could try html5, just put /html5 on the end of the link.
It may run a little better.

---

