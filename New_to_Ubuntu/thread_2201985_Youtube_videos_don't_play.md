---
title: "Youtube videos don't play"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by alberto8 on 2014-01-26
Hello, I have read similar posts related to my problem but none have helped so far. 

I just recently installed lubuntu 13.10, ran firefox and couldn't watch youtube videos. I downloaded chromium, same result.

Here is my hardware:

home@home:~$ lspci
00:00.0 Host bridge: NVIDIA Corporation nForce2 IGP2 (rev a2)
00:00.1 RAM memory: NVIDIA Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: NVIDIA Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: NVIDIA Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB controller: NVIDIA Corporation nForce2 USB Controller (rev a4)
00:02.1 USB controller: NVIDIA Corporation nForce2 USB Controller (rev a4)
00:02.2 USB controller: NVIDIA Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: NVIDIA Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: NVIDIA Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: NVIDIA Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: NVIDIA Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: NVIDIA Corporation nForce2 AGP (rev a2)
01:08.0 Multimedia controller: Motorola DSP56361 Digital Signal Processor (rev 01)
02:00.0 VGA compatible controller: NVIDIA Corporation C17 [GeForce4 MX IGP] (rev a3)

I have installed several packages, including adobe-flashplugin and gnash via the lubuntu software center, but nothing helps.

Please help! My family is mad at me because I deleted Windows XP and now they can't watch videos on youtube or listen to music on soundcloud.com

---

### Post by jeremy1138 on 2014-01-26
Open up a terminal and type the following

```

sudo apt-get install lubuntu-restricted-extras

```

---

### Post by mörgæs on 2014-01-27
In this case it would be better with

```
sudo apt-get install lubuntu-restricted-extras
```

or installing Chrome.

By the way, which CPU do you have? If we are dealing with an old AMD there could be other problems.

---

### Post by Yellow Pasque on 2014-01-27
nforce2 = Socket A = no SSE2

Chrome won't help. You should remove the flashplugin and gnash, and then downloadn this: [http://www65.zippyshare.com/v/78802631/file.html](http://www65.zippyshare.com/v/78802631/file.html)

You don't want to install the .deb. All you want is the libflashplayer.so file inside. Put the file in ~/.mozilla/plugins (you'll need to create it):
```
cd ~/.mozilla
mkdir plugins
```

---

### Post by jeremy1138 on 2014-01-27
> **mörgæs said:**
> In this case it would be better with

```
sudo apt-get install lubuntu-restricted-extras
```

or installing Chrome.

By the way, which CPU do you have? If we are dealing with an old AMD there could be other problems.

Woops.  Didn't even see that the OP was using Lubuntu.  Fixed.

Thanks.

---

### Post by monkeybrain20122 on 2014-01-27
Youtube is the least things to worry about as there are so many options. I don't even use flash for Youtube. [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
Lots smoother and easier on cpu. On an old hp netbook running lubuntu I could watch full 720p with Viewtube and mplayer plugin while with flash 480p max. On a still older Dell Inspiron 8500 flash can only handle 360p and Viewtube can get 480p

---

### Post by GrouchyGaijin on 2014-01-27
> **monkeybrain20122 said:**
> Youtube is the least things to worry about as there are so many options. I don't even use flash for Youtube. [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)
Lots smoother and easier on cpu. On an old hp netbook running lubuntu I could watch full 720p with Viewtube and mplayer plugin while with flash 480p max. On a still older Dell Inspiron 8500 flash can only handle 360p and Viewtube can get 480p
Thanks for the tip!

---

### Post by alberto8 on 2014-01-27
> **Temüjin said:**
> nforce2 = Socket A = no SSE2

Chrome won't help. You should remove the flashplugin and gnash, and then downloadn this: [http://www65.zippyshare.com/v/78802631/file.html](http://www65.zippyshare.com/v/78802631/file.html)

You don't want to install the .deb. All you want is the libflashplayer.so file inside. Put the file in ~/.mozilla/plugins (you'll need to create it):
```
cd ~/.mozilla
mkdir plugins
```

This did it for me. Thanks! Youtube works now, although i have a slight flickering-image problem in general, in and outside of youtube, ever since in installed lubuntu a couple of days ago.  It also didn't help for soundcloud.com, where it tells me, whenever i hit play on a song: 
"You need Adobe Flash to play this track.Please [install Flash]("http://get.adobe.com/flashplayer") and reload the page."

---

### Post by Yellow Pasque on 2014-01-28
It's possible that soundcloud checks the version number and considers your flash outdated. Nothing you can do about that..

---

### Post by monkeybrain20122 on 2014-01-28
Soundcloud doesn't need flash, it plays in html5 if you have flash disabled or set to "ask to activate" in Firefox (for most tracks anyway, though I have come across  exceptions)

However for its html5 player to work in FF you need to enable gstreamer, go to about:config and set media.gstreamer.enabled=true.

---

### Post by alberto8 on 2014-01-30
> **monkeybrain20122 said:**
> Soundcloud doesn't need flash, it plays in html5 if you have flash disabled or set to "ask to activate" in Firefox (for most tracks anyway, though I have come across  exceptions)

However for its html5 player to work in FF you need to enable gstreamer, go to about:config and set media.gstreamer.enabled=true.

Enabling the gstreamer in Firefox worked like a charm. Thanks!

---

### Post by mrag on 2014-01-31
> By the way, which CPU do you have? If we are dealing with an old AMD there could be other problems. That's curious. I have a 9 year old Compaq Pressario with an **AMD** Athlon XP processor and I've loaded _Xubuntu_ 12.04.3 twice now, did the updates, followed the tips here and still cannot play YouTube videos. I can't even get porn sites to work (don't laugh, porn sites play for most everybody). Oddly enough, I have an old eMachine also with an AMD Athlon 64 processor and that is running _Ubuntu_ 12.04.3 LTS quite well. I tried putting that Ubuntu on the Compaq, but the DVD player does not seem to work and I can't figure out how to get the bios to boot a USB so I only have the CD player for install and I'm over the 700MB install size.

I am open to any suggestions on Xubuntu or Ubuntu, swapping out hard drives (I have some small spares), whatever. Just no way I can have a unit that cannot play YouTube.

---

### Post by fireflower on 2014-02-01
> **alberto8 said:**
> Youtube works now, although i have a slight flickering-image problem in general, in and outside of youtube, ever since in installed lubuntu a couple of days ago. Video artifacts are usually an issue with the graphics card and/or graphics card drivers. Flickering is usually an issue with display frequency; laptops for instance are often hard-wired for 60 Hz, and any difference will cause flickering.

What is your graphics card situation? When I installed lubuntu, I was prompted that my graphics card drivers were proprietary. I checked the driver list on lubuntu, and was presented with a dozen confusing options. Checking the Nvidia site, it turns out the selection made by default by lubuntu was unfitting for my graphics card. Happily, drivers for my card were displayed in the list of options.

Unfortunately for scientific purposes, but fortunately for my own sanity, I addressed this potential problem before it became a real problem. That means it's a lousy control test to compare to your situation. It's entirely possible that, had I not switched drivers, I would have had issues, just as it's possible that, if you take this advice and check your drivers, the problem will go away. But we won't know until you try it.

FYI there is a whole list of standard practices when it comes to installing a new linux OS that begins after the official install checklist ends. Checking your graphics card drivers is just a start. After that, you need to go into the software center and install Ubuntu Restricted Extras. Then there's java to install. Not every packaged app is worth using; I immediately replace Transmission with Qbit, for instance. Gimp is mandatory for putting words on pictures of cats. Then you should fire up all your favorite video games and see if they work. You actually learn to make your own version of this checklist yourself; as you can see, I have!

I'm sorry to hear about your family being mad at you. If it's any solace, you can tell them a stranger you met on the internet (me) recommends lubuntu for Windows XP refugees. Microsoft is finally ending official support come April of this year, so I expect there will be a lot of people with old computers who will want something efficient, familiar, easy to use, and functional that they don't have to pay for. Lubuntu has that in spades. It's got a lot of polish with one of the least painful installs I've ever seen. It lacks the Unity desktop environment of vanilla Ubuntu, which Windows users will appreciate. (All PC users will appreciate it, really.) And of course the 12.04 release is ground zero for the great PC gaming migration.

I hope this helps fix your technical problem and keeps you from getting discouraged.

---

### Post by mörgæs on 2014-02-01
**Mrag**: I think you have made a good example of the difference between Athlon XP (AMD K7 family) and Athlon 64 (AMD K8 family). 

To be sure, please run 
```
sudo lshw -C cpu
```
for the two computers and post the results in CODE tags.

For the CD problem I recommend installing from the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") and adding the desktop later.

(and I have nothing against people watching porn)

---

### Post by mrag on 2014-02-01
Here is the code you requested for the problem install. The other machines (with 12.04 Ubuntu working) is at a friends and I will provide that later.
```
sidney@sidney-DQ180A-ABA-S6300NX-NA411:~$ sudo lshw -C cpu
[sudo] password for sidney: 
  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) XP 2800+
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: cpu@0
       version: 6.10.0
       slot: Socket A
       size: 2083MHz
       capacity: 3GHz
       width: 32 bits
       clock: 166MHz
        capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8  apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext  3dnow up
sidney@sidney-DQ180A-ABA-S6300NX-NA411:~$
```
This Compaq XP came with 'only' 512 RAM so I thought to try Xubuntu as I read it was not as resource demanding. I then found 1GB stick which I added before install. From what I've seen, Xubuntu would suit my purposes quite well and actually I like it better (YouTube, etc excepted). I originally installed Xubuntu 12.04.3 as dual boot along side XP. Both appear to work except Xubuntu will not play video (YouTube).

I then took that HD out, put in an old 40GB HD and again installed Xubuntu by itself. Same problem. FWIW, I tried Chromium and Chrome and each time they start, I get a 'crash report' ??? At some point and I don't remember specifics, either FireFox or Chrome gave me like a standard Windows notice "you need a plug in, click here." I did and for a while a single YouTube video would play. I have not been able to reproduce that situation.

Question: if YouTube will not play in my pc with Xubuntu, might it play in Ubuntu? (same browsers, same code?)

Thank you for your help.

---

### Post by alberto8 on 2014-02-01
> **alberto8 said:**
> Enabling the gstreamer in Firefox worked like a charm. Thanks!

After a few days of experience, i have realized that there are many videos which don't play on youtube. This one for example: [http://www.youtube.com/budlight](http://www.youtube.com/budlight)

gives me a link on the screen: "click here to visit our FAQ about html5", where it tells me that my system can't play the following:

- Media Source Extensions
- MSE & H.264
- MSE & WebM VP9

but also tells me that my browser does support:
- HTMLVideoElement 
- H.264      
- WebM VP8

so it sounds like my Firefox needs to support the first three that i mentioned above. How do i do that?

---

### Post by monkeybrain20122 on 2014-02-01
> **alberto8 said:**
> After a few days of experience, i have realized that there are many videos which don't play on youtube. This one for example: [http://www.youtube.com/budlight](http://www.youtube.com/budlight)

gives me a link on the screen: "click here to visit our FAQ about html5", where it tells me that my system can't play the following:

- Media Source Extensions
- MSE & H.264
- MSE & WebM VP9

but also tells me that my browser does support:
- HTMLVideoElement 
- H.264      
- WebM VP8

so it sounds like my Firefox needs to support the first three that i mentioned above. How do i do that?

To play those formats in FF in HTML5 you need to enable gstreamer in FF (which you already did) and install the packages x264 and gstreamer-ffmpeg. To check, after installing these packages relaunch FF and go to vimeo.com and see if videos play.

My recommended way is to use Totem or the gecko-mediaplayer (install from repo) with the greasemonkey script Viewtube [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) It is by far the best in terms of performance and it works on other supported sites besides Youtube. To use the script you need to install the firefox addon greasedmonkey. Since Youtube keeps changing its access it may stop playing once in a while but the script is updated every few days to keep up so if Youtube doesn't play it is usually fixed in half a day or so.  
Also, FF blocks Active mixed contents you may have to unblock and reload by clicking the url bar, alternatively install this FF addon [https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/](https://addons.mozilla.org/en-us/firefox/addon/toggle-mixed-active-content/) A small green square with an "A" would appear in the url bar, click it and change it to red.

I think there is also a vlc addon for Firefox but I have never used it so you have to google about it yourself.

Finally you can use minitube-ubuntu, it is a standalone Youtube viewer. You can install from the Software Centre ( there is an old version just called "minitube" in the repo that doesn't work) I am not sure if it is in synaptic, it used to cost $4 but now I think it is free. It is always free if you just grab the source code and build it (which I did)
To use it install phonon-backend-vlc from repo (it will remove phonon-backend-gstreamer if it is already installed)

---

### Post by mörgæs on 2014-02-01
Mrag, as you see the CPU has SSE, but not SSE2. If you mail your friend and ask him to run the same command you will find that SSE2 is offered.

Modern Flash players need SSE2. Your options for the Athlon XP are the workarounds discussed in this thread.

It does not matter which of the Buntus you use with regards to Flash. Lubuntu might generally be a little faster than Xubuntu, though.

---

### Post by alberto8 on 2014-02-01
installed greasemonkey and viewtube. seems like now i can play anything! but audio skips, mostly at the begining of videos.

---

### Post by monkeybrain20122 on 2014-02-01
> **alberto8 said:**
> installed greasemonkey and viewtube. seems like now i can play anything! but audio skips, mostly at the begining of videos.

That is probably because the resolution is too high for your cpu to handle. Viewtube's resolution is set to the highest by default, you can change that to standard or low. Also you can try switching between totem and gecko-mediaplayer plugins in FF and see if it makes a difference (go to Tools > Addon > plugins and disable/endable one or the other)

---

### Post by mrag on 2014-02-01
> **mörgæs said:**
> Mrag, as you see the CPU has SSE, but not SSE2. If you mail your friend and ask him to run the same command you will find that SSE2 is offered. Modern Flash players need SSE2. Your options for the Athlon XP are the workarounds discussed in this thread..

```
al@al-T6520:~$ sudo lshw -C cpu
[sudo] password for al: 
  *-cpu                   
       description: CPU
       product: AMD Athlon(tm) 64 Processor 3400+
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 4
       bus info: cpu@0
       version: 15.12.0
       slot: Socket 754
       size: 2388MHz
       capacity: 3GHz
       width: 64 bits
       clock: 199MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up


```
While I did not know the significance, I see the 'sse2' listed in the working (meaning YouTube plays) Ubuntu 12.04 install.

Now this might be interesting, I was able to use a 'Live Boot' Ubuntu 12.04.3 DVD in the Athlon XP and have it run. I selected "Try Ubuntu" rather than 'Install Ubuntu." YouTube WORKED in FireFox when running off the dvd in the Athlon XP!!!???!!!  YouTube however appears not to work when Ubuntu installed. I have never tried just using the Xubuntu CD with YouTube. Perhaps when I return home I can see if Xbuntu live will play YouTube from the CD as Ubuntu live did.

(I think the Athlon XP dvd player is deteriorating, sometimes a disk can boot from it, sometimes not. Different installs seem to go along for 20-40 minutes and then hang in different spots.)

---

### Post by mrag on 2014-02-01
Let me clarify, **some** YouTube videos played, **some** would not. And I tried a 'Live Xubuntu' cd and that also "played" (some) YouTube videos the same as the Ubuntu DVD. Frankly I think I have more problems here with the Athlon XP than simply YouTube. Among other things, I could not get "updates" (259 of them!) to work and my wireless internet connection kept dropping (although it did NOT on my iPad or my Win 7 system).

I still have the dual boot setup though; XP for a few more months along and a semi working Xubuntu 12.04.3. I think that around spring time the pc deservedly becomes a planter for geraniums. Thanks for all the wise counsel. Much appreciated. And as Arnold says' "I'll be back" probably with another crappy Win pc ;-)

---

### Post by mörgæs on 2014-02-02
The live boot might show Youtube using HTML 5, not Flash.

For the partly failing DVD drive please see post 14.

Don't give up getting Buntu to work! I suggest that you try Lubuntu built on a minimal 13.10 before you decide. If you get into problem not related to Flash please open a new thread.

---

