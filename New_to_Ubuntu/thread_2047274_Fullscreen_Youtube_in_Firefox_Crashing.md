---
title: "Fullscreen Youtube in Firefox Crashing"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by d4m1r on 2012-08-24
Hey guys, so this has been going on for a long time but I am actually determined to fix it now...Basically, ever since upgrading to 12.04 LTS, watching fullscreen youtube videos (often in 720p or 1080p) will eventually crash Firefox/Flash and the workspace will just be frozen...

Audio will still work, but I basically have to switch workspaces, kill the firefox and plugin process, and then relaunch firefox. Sometimes happens in under 10 seconds after making the video fullscreen, sometimes 1-2 minutes. Using the latest firefox (14.0.1?) and flash.

Anyone have any ideas/suggestions? Anyone else experiencing this? :confused:

---

### Post by pqwoerituytrueiwoq on 2012-08-24
make sure hardware acceleration is disabled in flash 
you can use flash video replacer to make youtube play in a video player lice totem,vlc,smplayer

---

### Post by d4m1r on 2012-08-25
> **pqwoerituytrueiwoq said:**
> make sure hardware acceleration is disabled in flash 
you can use flash video replacer to make youtube play in a video player lice totem,vlc,smplayer

Hardware acceleration is off and I need flash specifically. GPU is Nvidia if it makes any different.

Is nobody elses firefox/flash crashing when playing fullscreen 720p/1080p youtube videos?? :confused:

---

### Post by khelben1979 on 2012-08-25
> **d4m1r said:**
> Hardware acceleration is off and I need flash specifically. GPU is Nvidia if it makes any different.

Is nobody elses firefox/flash crashing when playing fullscreen 720p/1080p youtube videos?? :confused:

Clearing the cache in the browser has helped for me, a little. Other than that, it can be because running the video in full screen mode stresses both the CPU and the GPU and therefor if you don't have the necessary cooling in your case, that it causes freezes.

Other than the above, there could be something with the graphics driver as well.. Different versions of Ubuntu uses different versions of the nVidia driver which can explain why it works worse with the new version of Ubuntu, but it's really hard to tell exactly what the problem is.

To be sure that the issue has nothing to do with the Firefox web browser, you can try with other web browsers to see if it causes the same effect as from you have experienced here. Try Chrome would be my advice, it has flash inbuilt and does not use the version which you have installed in your Ubuntu system from what I know.

---

### Post by brainwash on 2012-08-25
> **d4m1r said:**
> Is nobody elses firefox/flash crashing when playing fullscreen 720p/1080p youtube videos?? :confused:
Disabling the plugin-container feature might improve performance and stability while playing flash videos in fullscreen mode.

[http://www.faqforge.com/uncategorized/disable-plugin-container-in-firefox/](http://www.faqforge.com/uncategorized/disable-plugin-container-in-firefox/)

---

### Post by d4m1r on 2012-08-29
Thanks for the reply guys but;

1) CPU/RAM usage isn't even @ 50% when watching the video and I have a pretty powerful rig.

2) I have confirmed the latest proprietary Nvidia video driver is installed.

3) I have not tried this within Chromium under Ubuntu or in Windows 7 using the same hardware but I will if it pops up again.....

Luckily for me, I just updated to Firefox 15 and it looks like this is no longer an issue :D

---

### Post by d4m1r on 2012-08-29
Looks like I spoke too soon....I was working for several mintues initially but now it's crashing as fast as it used to :(

I did narrow it down to plugin-container (and specifically flash most likely) however as killing the process and refresh the youtube page fixes Firefox, starts playing the video again, and relaunches an instance of plugin-container...

---

### Post by NikTh on 2012-08-30
Hi , 
try to open Firefox from terminal with this command
```
firefox -safe-mode
``` and test it . If works well then some of your plugins-extensions crash the Firefox and you must  find it. 
Thanks

---

### Post by Dunpostin on 2012-08-30
I've had this problem since 10.04 on two different laptops with onboard intel graphics. I too am determined to fix it. Disabling the plugin container in firefox worked for me, but it made firefox crash way too much.

---

### Post by NikTh on 2012-08-30
> **Ocasio101 said:**
> Disabling the plugin container in firefox worked for me, but it made firefox crash way too much.

I assume you know that plugin container is adobe's flash player. When you disable flash player you are capable to see online videos (e.g: youtube) only via Html5 or Gnash . 
Html 5 wants a good CPU processor and Gnash player is not so good at this time. 

Thanks

---

### Post by brainwash on 2012-08-30
> **NikTh said:**
> I assume you know that plugin container is adobe's flash player. When you disable flash player you are capable to see online videos (e.g: youtube) only via Html5 or Gnash .

That's simply wrong.

[http://support.mozilla.org/en-US/kb/What%20is%20plugin-container](http://support.mozilla.org/en-US/kb/What%20is%20plugin-container)

---

### Post by Dunpostin on 2012-08-30
You sure? I disabled dom.ipc.plugins.enable via about:config in firefox and flash still worked on youtube. The only difference was that when flash crashed, firefox completely crashed. Usually just the plugin crashes and the video player shows that error with the sad lego like block.

---

### Post by Dunpostin on 2012-08-30
>                      Originally Posted by **NikTh**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12205712#post12205712")                 
                 *I assume you know that plugin  container is adobe's flash player. When you disable flash player you are  capable to see online videos (e.g: youtube) only via Html5 or Gnash .*
You sure? I disabled dom.ipc.plugins.enable via about:config in firefox and flash still worked on youtube. The only difference was that when flash crashed, firefox completely crashed. Usually just the plugin crashes and the video player shows that error with the sad lego like block.[/QUOTE]

---

### Post by MadmanRB on 2012-08-30
Flash in firefox will never get better, I know how much some people hate it but chrome is the only answer to the issue thanks to adobe dropping linux support.
Or at the very least use chromium

---

### Post by NikTh on 2012-08-30
Hi , 
this is not completely wrong. 

I can see plugin-container process with top command only and only if I use flash player. No other separate plugin-container running , ever. 

According to link that Braniwash gave , flash-player is inside plugin-containter. So if you disable plugin-container where flash will load ? 

@Brainwash thanks for the link. 

Did you guys tried the firefox --safe-mode command ?

---

### Post by d4m1r on 2012-08-30
1) Disabling plugin-container does NOT disable flash. It only integrates the process into the existing firefox one like how it used to be (1 process). Plugin-container was only recently added to provide a sandbox for plugins to run so if 1 crashed, it wouldn't crash the whole browser.

2) I do not want to try disable however, even if it could potentially fix my fullscreen youtube issue because as someone mentioned who tried it, the main firefox main process is then more likely to crash.

3) I will try the --safe mode extension sometime soon hopefully.

4) I still haven't been able to figuire out if this is a flash problem specifically, xorg/compiz like a few people have suggested (one bug on launchpad about it), or a firefox one (with plugin-container specifically).

---

### Post by brainwash on 2012-08-31
> **d4m1r said:**
> 2) I do not want to try disable however, even if it could potentially fix my fullscreen youtube issue because as someone mentioned who tried it, the main firefox main process is then more likely to crash.
Does  your Flash Player crash frequently while not watching fullscreen videos? The given solution works on my old system (not a single crash related to Flash content so far). However, more information and log files are needed to solve this mystery.

---

### Post by d4m1r on 2012-08-31
> **brainwash said:**
> Does  your Flash Player crash frequently while not watching fullscreen videos? The given solution works on my old system (not a single crash related to Flash content so far). However, more information and log files are needed to solve this mystery.

Hey, no flash/firefox/plugin-container do not ever freeze or crash other than when I watch HD fullscreen youtube videos....I still also try launching firefox from the command line and get some helpful logs soon...

---

### Post by md2020 on 2012-10-31
I had a similar issue with playing videos with VLC and Ubuntu 12.04 that I was able to resolve. You could see if this works for you:  [http://ubuntuforums.org/showpost.php?p=12328809&postcount=19]("http://ubuntuforums.org/showpost.php?p=12328809&postcount=19")

---

### Post by Bobapatatas on 2013-02-12
> **d4m1r said:**
> Hey, no flash/firefox/plugin-container do not ever freeze or crash other than when I watch HD fullscreen youtube videos....I still also try launching firefox from the command line and get some helpful logs soon...

I Have the same problem! I think it is Flash related. Did you find a solution yet?

---

### Post by d4m1r on 2013-02-12
Nope....It still happens occasionally. There have been several flash and firefox updates since I posted in this thread and while I'll admit they've helped (it crashes less), it still happens sometimes....

The only work around I've found is to switch to another workspace, kill plugin-container using system monitor, and then reload the page. That doesn't guarantee the same video won't crash flash again though...Does anyone having this problem have a dedicated ATI video card? I have a dedicated Nvidia card and the nvidia drivers might have a part to play in this problem as well..

---

### Post by patrickstar777 on 2013-05-10
i have the same problem using an ati radeon card on my hp pavilion g7 every since i upgrade with a fresh live-install to ubuntu 13.04.

over some time i now figured out that the error is not dependent on the video quality i use for watching on youtube. when the screen freezes, i can navigate out of the plugin-container with alt+tab. firefox shows a 'unresponsive script' (javascript?) error box that always pops up right at the moment the video freezes.

can anyone help me with this? on quantal everything worked just fine, out of the box! so i suppose it's some really tiny thing that causes this.

---

