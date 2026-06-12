---
title: "Google Chrome freezes Ubuntu"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by JSF1992 on 2013-02-06
I have been experiencing frequent, random freezes when using Google Chrome in Ubuntu 12.04. The entire desktop freezes, the mouse won't move, the audio loops, and Ctrl-Alt-F1 does nothing. I've googled the problem multiple times and checked this forum, but to no avail. I really like Chrome when it's not freezing on me, so if y'all could give me some pointers on how to fix it, I'd appreciate it!

Here's my graphics controller, though I'm not confident it's a graphics problem:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
```I've been using Ubuntu less than a year, so I'm not proficient with the terminology yet.

Thanks!

---

### Post by Frogs Hair on 2013-02-06
Hello and Welcome

You may want got to the menu > history and clear your cache and  browsing history from the beginning of time to eliminate that possibility.

---

### Post by JSF1992 on 2013-02-06
I cleared the cache, cookies, and browsing history. It was good for a while, but it's freezing again now.

---

### Post by Frogs Hair on 2013-02-06
How is your free memory ? ```
free -m
```

---

### Post by JSF1992 on 2013-02-06
Here's what I've got now:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          7889       2252       5636          0        101        821
-/+ buffers/cache:       1328       6560
Swap:         8091          0       8091
```

I'm far from an expert, but I would think RAM's probably not the issue, if I'm only using 1/3 of it. Of course, Ubuntu isn't frozen at the moment either. Is there any chance I can get a real time readout of my RAM usage so I can see what it looks like next time it crashes?

---

### Post by monkeybrain2012 on 2013-02-06
Did you install any Chrome addon? If you do try disabling them and see if the problem persists.

---

### Post by offgridguy on 2013-02-06
I find Chromium less problematic.:)

---

### Post by no2498 on 2013-02-07
as of the late chrome and flash player are fighting each other
chrome uses pepper flash
and it turns off flash player

john

---

### Post by JSF1992 on 2013-02-07
> **offgridguy said:**
> I find Chromium less problematic.:)
Yeah, I may switch to that if the problem can't be resolved.  I kind of like Chrome's flash support, though - if I remember correctly, Chromium doesn't do such a good job of that.

Chrome hasn't crashed since I turned off all my extensions, but we'll see how long that lasts - if Chrome behaves for a few days, I'll mark this as solved. I'll miss Adblock in the interim, though.

> **no2498 said:**
> as of the late chrome and flash player are fighting each other
chrome uses pepper flash
and it turns off flash player

I ran into that problem a few days ago. I went to chrome://plugins and disabled the plugin labeled "Shockwave Flash 11.5 r31", and it started working again.

---

### Post by JSF1992 on 2013-02-08
Chrome froze my machine again this morning. 

Disabling all my extensions does appear to decrease the frequency of the events, but it hasn't eliminated the problem. Do y'all have any other suggestions? I'm thoroughly baffled.

---

### Post by Frogs Hair on 2013-02-08
You could remove Chrome-open home/hidden folders/.config and delete the google chrome folder and re-install Chrome.  

If the profile is corrupt it will be removed with the folder and a new one created during installation. If you use the sign in to chrome feature your previous book marks and settings will be restored when you sign in.

---

### Post by JSF1992 on 2013-02-11
Chrome crashed again this afternoon. A few days ago, I ran:
```
sudo apt-get autoremove google-chrome

sudo-apt-get purge google-chrome-stable
```

and removed the Chrome folder in the .config directory as Frogs Hair said. I then redownloaded the 64-bit .deb and reinstalled Chrome. Nevertheless, I got the same freeze again when I followed a link to youtube.

Thanks for taking the time to help me sort this out - I certainly appreciate it!

---

### Post by Frogs Hair on 2013-02-11
I run Opera and Chrome with less memory without Flash,crash, or freeze problems, so  I would see if there are any drivers available for your graphics card/controller in additional drivers. 

Being an AMD and Nvidia user I have on experience with Intel graphics and Ubuntu. Run the following to display you CPU information. 
```
cat /proc/cpuinfo
```

---

### Post by JSF1992 on 2013-02-11
```
cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
stepping	: 9
microcode	: 0x12
cpu MHz		: 1200.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips	: 4988.62
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
stepping	: 9
microcode	: 0x12
cpu MHz		: 1200.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips	: 4988.43
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
stepping	: 9
microcode	: 0x12
cpu MHz		: 1200.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips	: 4988.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 58
model name	: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
stepping	: 9
microcode	: 0x12
cpu MHz		: 1200.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips	: 4988.44
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


```

When I looked in additional drivers, the menu was blank and was titled "No proprietary drivers are in use on this system". A quick Google search turned up no additional drivers other than the ones packaged with Ubuntu. I ran
```
sudo apt-get install xserver-xorg-video-intel

```

and it merely confirmed I already had the latest version of the intel driver package. I'll certainly keep looking for a new driver, though.

I don't know if it matters, but I've tried several times hitting Ctrl-Alt-F1, logging in, and running "sudo reboot", but the computer does nothing. I don't know if that indicates whether it's a graphics problem or not, but I figure it can't hurt to mention.

---

### Post by Frogs Hair on 2013-02-11
You have a capable CPU and more than enough memory so I have no further suggestions. ](*,)

---

### Post by JSF1992 on 2013-02-11
Thanks for your help!

---

### Post by JSF1992 on 2013-03-05
Finally got the problem fixed. I did a reinstall of Ubuntu 12.04 about a week ago, and haven't had a problem since. Still not sure what the cause was, but hopefully this'll be useful for anyone else who encounters a similar problem.

---

### Post by longtro on 2013-03-06
awesome.. 
now I will attempt the chrome! : )

---

### Post by VMC on 2013-05-16
> **JSF1992 said:**
> Finally got the problem fixed. I did a reinstall of Ubuntu 12.04 about a week ago, and haven't had a problem since. Still not sure what the cause was, but hopefully this'll be useful for anyone else who encounters a similar problem.

I've had the exact same roblem. I have re-installed 12.04 and it gets fixed for a short time, ten re-appears again. Right now I did another re-install, I will use firefox and see if the problem goes away.

I never had a problem in the past using 12.04 and chrome. I stopped using 13.04 and Saucy because of freezes. I kept shooting the trouble as kernel or nouveau related, but now it aprrears its been the latest chrome stable that's the culprit.

---

### Post by djmarty on 2013-06-15
I am experiencing the same system freeze when running Chrome in Ubuntu 13.04.  Things run fine for a few hours then total freeze.  Sometimes the mouse cursor is still responsive but this also stops after a while.  I can't ctrl-al F1 to get a console and I can't ssh into the machine.
Frustrating as I was hoping to switch to Chrome from Firefox.

---

### Post by craig10x on 2013-06-15
I have the latest Chrome stable....it doesn't freeze on my system but it occasionally seems to hang when it comes to a web page loading in and i never had that problem before with all the various updated versions i have gotten from them, so perhaps this particular version is problematic...

For a possible experiment, perhaps you should try Google Chrome Beta which is in the next version past stable...and see how that does for you, so at least you know if the next version will clear things up...
If you prefer, download and run it in a live iso session to test it there....(if you do it on live...don't forget to also install ubuntu restricted extras for a proper test with flash and all...)

---

### Post by wyth on 2013-06-18
Aha -- I'm not alone in this. For some time I've had the exact same problem, and Chromium was actually worse; it would freeze up the system within minutes of opening it, instead of the hour or two with Chrome. (On an Intel GM965 gfx card.)

I upgraded from 12.04 to 13.04 with the same results. I then re-installed the system, and that seemed to fixed the hard freezes, but it still slows to an unbearable crawl for extended periods of time. Eventually I might get a warning that a tab is non-responsive, but that can take anywhere from 20 minutes to well over 1 or 2 hours. I have been able to get to a terminal, though, since re-installing the system. (What I mean by that is I just used the live USB and re-installed the system files; it wasn't a clean install proper.)

The latest move was to get rid of all the files in ~/.config/google-chrome, which made it *still less* likely to completely lock up, but it still does. I may try going to the beta version again, but I experienced the same issues there before. 

It seems like there's an issue with Chrome gracefully crashing a tab rather than everything. This is strange, because one of the features of Chrome was a runaway tab was supposed to go down on its own without taking down the rest of the browser, let alone the machine (although I'd take the browser crashing over locking up the entire system). I'd love to get to the bottom of this, because there are a few features on Chrome that I find I really miss when I go back to Firefox (and this never happens with Firefox). Plus, when it works, Chrome feels a half-step snappier than Firefox. 

But I'm not sure I could file a bug at this point because I don't know where to look for issues (nothing in the logs) or where the problem really exists. The only thing I know for certain is it almost never happens on my desktop machine with the nvidia GeForce 8600GT-DDR3 card, so maybe it's something with the Intel onboard gfx. For now I'm having to break myself of the Chrome habit because it's making browsing nearly impossible.

---

### Post by thaper on 2013-10-17
I have the latest ubuntu with chrome on 3 different machines all with different hardware - i hangs on all of them

---

### Post by ronliu2k on 2013-10-18
I had the exact chrome display crush issue for the last 3 months, and finally I fixed ti totally by install gnome desktop. I guess probably some unity stuff conflict with chrome.

---

### Post by cagnulein2 on 2013-10-27
I have the same problem! Is there a bug open about this issue?

---

### Post by juliobahar on 2013-11-04
Same problem with latest chrome Version 30.0.1599.114 and on both Ubuntu 13.04 and 13.10. It doesn't seem to happen on my laptop which has an Nvidia graphics card.

---

### Post by nikola.kambourov on 2013-12-04
Same problem on ubuntu 12.04., both Chrome and Chromium freeze my whole system. I`m with ATI Radeon x1250 graphic card.

---

### Post by Paul91 on 2013-12-08
Did this ever get sorted? I am still having a lot of problems. Seems to happen with web pages with significant graphical content. Sometimes with other programs like opening pdf files. Scroll up and down and that is it - Ubuntu freezes and I have to reboot. I can Ctrl-Alt-F1 which closes the graphical interface but I have found no way of reloading Unity to carry on. I always have to reboot. Shotwell used to be terrible - hardly usable - but this improved after the AMD bug fix mentioned below.

The processor is a 3 core AMD which I suppose is unusual. A few months ago everything got a lot better with a major upgrade to fix a bug with AMD processors but things have slipped back again since then. I have Radion 1200 Graphics.

(New edit: Just checked my post by scrolling up and down and the whole machine froze! I am using Firefox right now so cannot blame Chrome.)

---

### Post by art-hens-teeth on 2013-12-10
For me, Chrome goes to 100% CPU on one of the three machines here. All run Ubuntu 12.04. Two run Gnome shell, one runs Unity. On the one that freezes, it happens with both Gnome shell and Unity. To reproduce it, I need to do the following:
[LIST=1]
[*]aptitude purge and then reinstall google-chrome-stable and google-talk-plugin
[*]rm -rf ~/{.config,.cache}/google*
[*]start Chrome
[*]log Chrome into my Google account
[*]enter my sync passphrase
[*]wait a few minutes
[*]open the settings menu (three horizontal bars in the top, right corner)
[/LIST]
The menu will pop down, Chrome will go to 100%. After that, the mouse will track but Gnome and Unity are otherwise unresponsive. Once I kill -9 chrome, things go back to normal.

Syncing with Google is the bad step. The problem never happens if I don't sync. The problem still happens if I sync with Google but start Chrome with --disable-extensions

I would gladly purge and reinstall something but don't know what package(s) might be the culprit.

-- Art Z.

---

### Post by monkeybrain20122 on 2013-12-10
Open Chrome, on the url bar type about:flag and play with some settings there. I think it has something to do with hardware acceleration not working right. 

I haven't experienced any problem, both with the Nividia driver and nouveau. But then maybe i never use chrome for long duration (mostly on Firefox)

---

### Post by douglas.conley on 2013-12-17
Hi all ... I've just uncheck [COLOR=#000000]the Hardware Acceleration option from Chrome Config/Advanced ... and it's ok until now ... I'll post again if something goes wrong.[/COLOR]

---

### Post by dkhajavi@gmail.com on 2014-01-28
Just want to confirm same bug on 13.10 with Chromium [FONT=Ubuntu, Arial, sans-serif][COLOR=#303942]Version 31.0.1650.63 Ubuntu 13.10 (31.0.1650.63-0ubuntu0.13.10.1~20131204.1)[/COLOR][/FONT]

[FONT=Ubuntu, Arial, sans-serif][COLOR=#303942]Seems like sites with lots of flash and embedded video are the worst culprits in causing crashes.  I have these every hour or so and as often as 5 mins after boot up.  I can also go for hours with no lockup...very strange indeed.

I am on an Alienware machine with 8 gigs RAM, fast CPUs, Nvidia SLI Graphics cards, SSD Drives  etc... so not a system limitation by any means.

Full hard lockups with only option hard power off and restart (sometimes starts with desktop lock and moving mouse but no ability to click on anything and CTRL-ALT-F1 non-functional, but ALWAYS ends up in a full lock within seconds).

Very frustrating....[/COLOR][/FONT][COLOR=#303942][FONT=Ubuntu]
[/FONT][/COLOR]
[COLOR=#303942][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by Joe2832 on 2014-02-08
Same problem here I think.  Running 12.04.4  with 2 gb RAM, AMD Athlon 64 X2 Dual Core Processor 3800+.   Problem seemed to start around December of last year.  Usually when on youtube and bunch of tabs open, Chromium [COLOR=#303942][FONT=Ubuntu]32.0.1700.102 will freeze entire system and then black screen.

I think maybe this corrupted my graphics driver, I had to downgrade linux version and update nvidia driver. 

Using Adblock extension.  Considering adding ScriptSafe.
[/FONT][/COLOR]

---

### Post by Joe2832 on 2014-02-15
Any fixes?  I've uninstalled Chromium.  May try intalling at a later time.

---

### Post by oren2 on 2014-02-26
I have the same problem ( Gentoo linux) chrome version 32.0.1700.107
Is there a bug ticket for this thing?

---

### Post by vasa1 on 2014-02-26
> **oren2 said:**
> I have the same problem ( Gentoo linux) chrome version 32.0.1700.107
Is there a bug ticket for this thing?
Do you want information about Gentoo linux here?
BTW, Chrome stable is now v33

---

### Post by bill-wilken-wilkenmail on 2014-03-17
Chrome freezes my up-to-date 12.04 system as well.  I have not encountered a comparable problem with Firefox.  My 32-bit system is hosted on an Intel® Core™ i5-3450 CPU @ 3.10GHz × 4 platform with an Intel® Ivybridge Desktop x86/MMX/SSE2 video card connected to an Asus monitor via an HDMI cable.  The computer has 7.7 giB RAM and a 2TB disk which is largely empty.

---

### Post by thelinuxkidd on 2014-03-22
> **douglas.conley said:**
> Hi all ... I've just uncheck [COLOR=#000000]the Hardware Acceleration option from Chrome Config/Advanced ... and it's ok until now ... I'll post again if something goes wrong.[/COLOR]

Did this fix the problem for you?

---

### Post by thelinuxkidd on 2014-03-22
Is there no fix for this yet? I'm having the same problem and it's absolutely frustrating. I don't want to switch to Firefox but I'm not going to have a choice if this continues.

---

### Post by jruberto on 2014-03-22
I've been living with this a long time -- in my 40-50 hour a week dayjob, my Acer ASpire M laptop freezes at least once a week, but sometimes it's a couple times a day.  Here are the consistencies I've observed, **does this sound familiar to anyone?**

- Every time it's triggered by an interaction:  usually a click, sometimes a mouseover that I know will do something.  (i.e. i don't walk back to my idle computer to find it locked up)
- Sometimes, the machine gets laggy and unresponsive in the moments before the freeze with a 100%CPU spike.  If I close chromium quickly enough I can avert disaster.  Considering binding a hotkey to "killall chromium-browser"
- I'm *pretty sure *it mostly only happens when using an external monitor -- tho I mostly always use an external monitor.

_Hardware, software & driver info_
Chromium 32.0.1700.107
Ubuntu 12.04LTS (without the LTS hardware enablement upgrades, so kernel 3.2.0-60-generic x86_64)
nvidia-experimental-304 video
bumblebee-nvidia to manage the multiple adapters
plenty of RAM / CPU, never hitting swap
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M LE] (rev ff)


I do get the occasional this:
[ 6028.664558] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15000000, was 12000000
which may or may not correlate, haven't been able to prove. The LTS enablement upgrade supposedly solves this, but I'm scared to do it, I don't have time to reinstall my machine if that goes horribly wrong.  I went through a lot of pain to get video drivers / mesa / bumblebee working in harmony.

I did just now disable the "GPU compositing on all pages" so we'll see if that has an effect.  [B]Has that been successful for anyone here?

[/B]Also I'm working on a new SaaS platform at work that works best in Firefox, so may also (grudgingly) switch to Firefox.

---

### Post by thelinuxkidd on 2014-03-23
Having gotten fed up with this and having tried everything suggestion without luck, I took a drastic approach. Thanks to this post [Turning Off GPU acceleration in Google Chrome]("http://jamisondance.com/post/22387219496/turning-off-gpu-acceleration-in-google-chrome/") I was able to find a list of Chrome's [command line switches]("http://peter.sh/experiments/chromium-command-line-switches/"). I literally used every switch that disabled something related to the GPU or to hardware acceleration:
> google-chrome --blacklist-accelerated-compositing --blacklist-webgl --disable-accelerated-2d-canvas --disable-accelerated-compositing --disable-accelerated-layers --disable-accelerated-video --disable-accelerated-video-decode --disable-gpu --disable-gpu-compositing --disable-gpu-driver-bug-workarounds --disable-gpu-process-prelaunch --disable-gpu-program-cache --disable-gpu-rasterization --disable-gpu-shader-disk-cache --disable-gpu-vsync --disable-gpu-watchdog --disable-map-image --disable-threaded-compositing --log-gpu-control-list-decisions --disable-accelerated-fixed-root-background --disable-accelerated-overflow-scroll --disable-pinch --disable-universal-accelerated-overflow-scroll --disable-webrtc-hw-decoding --disable-webrtc-hw-encoding --enable-deferred-filters
I don't know if every switch is needed or even what some of them do. But, I have been playing 10 YouTube videos simultaneously for a few minutes while keeping another 10 tabs open and I've had no problems.
I have dealt with this issue for so long I honestly don't want to spend more time finding out what the right switches are. But, if anyone has better knowledge than me and can condense the command I would welcome it.
I will report back in a few days to let you know if it continues to work.

---

### Post by thelinuxkidd on 2014-03-29
> **thelinuxkidd said:**
> Having gotten fed up with this and having tried everything suggestion without luck, I took a drastic approach. Thanks to this post [Turning Off GPU acceleration in Google Chrome]("http://jamisondance.com/post/22387219496/turning-off-gpu-acceleration-in-google-chrome/") I was able to find a list of Chrome's [command line switches]("http://peter.sh/experiments/chromium-command-line-switches/"). I literally used every switch that disabled something related to the GPU or to hardware acceleration:

I don't know if every switch is needed or even what some of them do. But, I have been playing 10 YouTube videos simultaneously for a few minutes while keeping another 10 tabs open and I've had no problems.
I have dealt with this issue for so long I honestly don't want to spend more time finding out what the right switches are. But, if anyone has better knowledge than me and can condense the command I would welcome it.
I will report back in a few days to let you know if it continues to work.

I have not had any major problems since I started using the fix above a few days ago. The only change I had to make was to remove the --disable-gpu-sandbox switch. I got a warning saying using it compromised stability and security in the browser. I edited the original post and removed the flag from there too.

---

### Post by Ubi_one_2014 on 2014-03-30
chrome is working perfect here

---

### Post by trag on 2014-03-31
If chrome has hardware acceleration enabled you will have these symptoms. In url bar type' about:flags' and enable 'reset to defaults'

---

### Post by akg-bruggeman on 2014-04-29
Turning off GPU acceleratuin does NOT work.
Chrome hangs all the time, also on pages without flash.
On: Dell D630 (intel chipset, 2Gb mem) with Zorin 6.4 (based on Ubuntu 12.04)

---

### Post by thelinuxkidd on 2014-04-29
> **akg-bruggeman said:**
> Turning off GPU acceleratuin does NOT work.
Chrome hangs all the time, also on pages without flash.
On: Dell D630 (intel chipset, 2Gb mem) with Zorin 6.4 (based on Ubuntu 12.04)

Try using the flags in my post above

---

### Post by pavankumarkn on 2014-05-14
Not sure if I am adding redundant information here. I was also getting the same problem.
On 14.04 LTS with Chrome [COLOR=#303942][FONT=Ubuntu]Version 34.0.1847.132,[/FONT][/COLOR] I have disabled Harware accelaration option and it stopped freezing there after.

---

### Post by skyeagle on 2014-05-17
The same here. Who among you use the AdBlock extension for Chromium? I suppose AdBLock is the culprit.

---

### Post by monkeybrain20122 on 2014-05-17
> **skyeagle said:**
> The same here. Who among you use the AdBlock extension for Chromium? I suppose AdBLock is the culprit.

I don't think it has anything to do with it, I put Chrome as a second browser (Mainly  Firefox but Chrome for some flash sites) on all the computers I have installed *buntu on (~10 of them for myself and friends) and I have adblock on all of them, never have any problem.

---

### Post by lotharmat on 2014-05-18
I'm using Chrome with adblock with no issues at all - Uses H/W acceleration when available!

---

### Post by Andrs_Chacon on 2014-06-05
Hello folks:


I was experiencing the exact same scenario, with both Kubuntu 12.04 and LinuxMint 12 (I do not quite remember what version of KDE I was using with Kubuntu, but I am using KDE 4.8.5 just now with LinuxMint. My version of Chromium is 34.0.1847.116. I had the same exact scenario (the whole system will not respond to any command and you stare at the HDD activity LED indicator it was not blinking anymore). The only solution was to force a shut down. Following your advices from this thread, I solved this by disabling the Hardware Acceleration under Chromium settings and also, I went to the address bar, type ' about:flags' and enable 'reset to defaults'. I am not sure if it´s a duplicate step. It is being 2 days now and no more lock ups :)

---

### Post by monkeybrain20122 on 2014-06-05
Actually I find the most compelling feature of Chrome/Chromium over Firefox is hardware acceleration, if you have to disable it I see little point in using Chrome/Chromium at all except for the rare occasions where up to date flash is needed, but even that can be solved in FF with pipelight.

---

### Post by sverker_wahlin on 2015-03-15
I get the same problem, but it also shows up in firefox. Occasionally, when I saw it coming and shut firefox down at the right moment, I got Firefox to chrash instead, and have submitted an error report. Maybe one could dig that one up?

Anyway, I've tried Firefox, chrome and chromium. Nothing works.

---

### Post by Piotr_Masekowski on 2015-09-15
I've been strugling with freezes on both Firefox and Chrome and Ubuntu 14.04 and 15.04. Tried everything I could think of.

I suspected my ATI Radeon, installing proprietary Radeon driver solved issues!

> sudo apt-get install fglrx

After installing only once had some Chrome heavy lagging, but it did not freeze entire system, just restarted Chrome and system was still fine.

My video adapter is Intel(R) HD Graphics 3000 on Dell laptop.

---

### Post by coffeecat on 2015-09-15
Rest in peace, ancient thread. If anyone needs help with any related problem, please start a new thread.

Closed.

---

