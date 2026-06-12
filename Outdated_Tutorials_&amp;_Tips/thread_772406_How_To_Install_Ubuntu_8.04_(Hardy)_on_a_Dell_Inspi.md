---
title: "How To Install Ubuntu 8.04 (Hardy) on a Dell Inspiron 1520"
date: 2008-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by ctpaterson on 2008-04-28
Well the [thread for Gutsy on the 1520]("http://ubuntuforums.org/showthread.php?t=577469") started to get a lot of notes for Hardy in it, so I figured it was time Hardy deserved its own thread.  Here's what I did to get Ubuntu 8.04 (Hardy Heron) working on an Inspiron 1520

A few notes, I did this with the 32-bit final release, using the alternate disc.  Using the alternate was necessary since I set up an encrypted partition with this installation.  If you do not want an encrypted partition, then you can probably use the regular disc and skip step 3.

Corrections, additions, and comments are encouraged, especially since some people might have some different hardware than I.

**Computer specs are:**
[list]
[*]Intel Core 2 Duo T7300
[*]2 GB RAM
[*]1680x1050 display
[*]256MB nVidial GeForce TM8600M GT video card
[*]High Definition audio 2.0
[*]Intel PRO/Wireless 3945abg
[*]Integrated webcam
[*]Dell wireless 355 bluetooth internal
[/list]

**What's working...**
[list]
[*]Sound from speakers + speaker cutoff when headphones plugged in
[*]High-res screen, w/ Compiz effects
[*]Internal microphone
[*]Wireless (open network and WEP 128bit Hex)
[*]Webcam (tested in Skype 2.0)
[*]Memory card slot (tested with SD)
[/list]

**What's not working...**
[list]
[*]Suspend
[*]Hibernate
[*]Bluetooth scans and finds other devices (haven't successfully connected yet)
[/list]

**What I haven't tested.**
[list]
[*]Modem (there are some reported issues)
[*]Plug-in microphone
[/list]

**What I did...**
[list=1]
[*]*I had a wireless problem upon install - you may need to start with a wired connection to your network/internet.*
[*]Boot from alternate CD (If you don't want an encrypted partition, I expect the regular CD should suit you fine)
[*]Set up encrypted partition *(optional)*.
[list]
[*]There's a great tutorial for that [here]("http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml") and [here]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html") (for Gutsy, but still worked).  I deviated a bit as I manually partitioned the drive.
[/list]
[*]Install
[*]Boot from hard drive
[*]Install any updates
[*]Enable nVidia restricted drivers
[*]In a terminal, type "sudo apt-get install linux-backports-modules-hardy-generic" to get wireless working, if you're having problems (won't work until after you reboot later)
[*]To enable the digital mic built-in to the laptop lid:
[list]
[*]Run "alsamixer", scroll to the right with the arrow keys until you've selected "Digital".
[*]If the Digital Input Source is "Analog Inputs", use the up/down arrows until it says "Digital Mic 1".
[*]Hit "Escape" to exit.
[*]*(I believe switching the Digital back and forth from "Analog Inputs" to "Digital Mic 1" will cause a switch between the internal mic, and the mic plugged into the side -- but I have not tested this.)*
[*] In a terminal, type "amixer set Mux,0 3 cap"
[*] In a terminal, type "amixer set Capture 15 cap"
[*] In a terminal, type "amixer set Digital 120"
[/list]
[*] For better volume control, do the following
[list]
[*]Right click on speaker icon in system tray, and select "Open Volume Control"
[*]Go to Edit: Preferences
[*]Put a check next to Front. Hit OK
[*]Turn Front volume all the way up.
[*]Now the master volume control raises and lowers the volume between much greater extremes.
[/list]
[*]Reboot
[/list]

Bonus step: "sudo apt-get install compizconfig-settings-manager" to choose from even more effects.

**Known Issues:**
[list]
[*] Excessive hard drive parking; a fix that should not be employed lightly is [here]("http://ubuntuforums.org/showthread.php?p=4834076#post4834076")
[*] audio is not properly shared by multiple apps.  Workaround [here]("http://ubuntuforums.org/showthread.php?p=4844878#post4844878")
[*] nVidia-new driver has visual bugs (a couple of us suffer from this problem).  Links to other discussions here: [Forum Topic]("http://ubuntuforums.org/showthread.php?t=676358") [Official Bug Report]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382") [Partial Fix]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37")
[*]Some people have complained that the backports fix did not take care of their wireless troubles - there's more dicussion [here]("http://ubuntuforums.org/showthread.php?t=765647&page=6").
[*]Playback of video DVDs has some colouring problems - possible solution in [this thread]("http://ubuntuforums.org/showthread.php?t=732931&highlight=dvd+colors&page=2").  I haven't had a chance to try yet.
[/list]

Good luck.

---

### Post by bayonetblaha on 2008-04-28
I think it should be noted that turning up "front" in alsamixer facilitates a more appropriate volume capability.

---

### Post by steve_4802 on 2008-04-28
Hi mate,
I started with ubuntu (and linux for that matter) only 6 months ago so made very good use of your Gutsy how to for the inspiron 1520 - thanks heaps for that one!

Regarding the Hardy upgrade. I've got an issue you haven't mentioned and would be interested if you also have it. When playing DVD's my colour for the DVD colour is all messed up, typically people are blue etc (basically the negative of what the colour should be). Other than DVD playback all colours are normal.

I can't remember what nvidia driver I was using in Gutsy but in Hardy I currently have 192.12 +2.6.24.12 installed. My graphics card is an nVidial GeForce TM8600M GT video card.

Note: I've seen lots of bug reports for this DVD colour problem with nvidia cards for older versions of ubuntu (before Gutsy) but nothing in reference to Hardy.

Cheers mate.

---

### Post by ctpaterson on 2008-04-28
> **steve_4802 said:**
> Hi mate,
I started with ubuntu (and linux for that matter) only 6 months ago so made very good use of your Gutsy how to for the inspiron 1520 - thanks heaps for that one!

Regarding the Hardy upgrade. I've got an issue you haven't mentioned and would be interested if you also have it. When playing DVD's my colour for the DVD colour is all messed up, typically people are blue etc (basically the negative of what the colour should be). Other than DVD playback all colours are normal.

I can't remember what nvidia driver I was using in Gutsy but in Hardy I currently have 192.12 +2.6.24.12 installed. My graphics card is an nVidial GeForce TM8600M GT video card.

Note: I've seen lots of bug reports for this DVD colour problem with nvidia cards for older versions of ubuntu (before Gutsy) but nothing in reference to Hardy.

Cheers mate.

Glad the articles were of some help.  Admittedly - commercial DVD playback is not something I've attempted to get working yet.  I was mucking with the RC on another system, and after some awful recipe of commands that I could never hope to recall - I ended up seeing the same thing you described above.

So, nothing to report yet - but perhaps others reading the thread could chime in...and if you're fortunate enough to find a solution elsewhere, I hope you'll share.

---

### Post by alfredska on 2008-04-28
1) Bluetooth works for me as soon as I issue the command:
```
sudo hidd --search
```

2) My [post]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81") on dual booting Vista/Ubuntu while keeping MediaDirect intact is still applicable.

> **ctpaterson said:**
> 
8. In a terminal, type "sudo apt-get install linux-backports-modules-hardy-generic" to get wireless working (won't work until after you reboot later)
3) I wouldn't recommend following step 8 unless you are having wireless troubles.  I did not need the backport myself (while it fixes some bugs such as the wireless LED, it introduces a new set of bugs)

---

### Post by mac-duff on 2008-04-28
Hi there,
thanks for the new thread. 
Of course I have some trouble and every time something different. Sound works great and also the speak go to mute by unplugging a headset. But it seems that only one application at the same time can access by sound device. For example I listen a mp3 and start a VM, VMware tells me that the sound device is busy and also in Skype I have no sound actually.
Can also someone confirm that the system hangs very often? I mean I listen again a mp3 and if I switch the tabs in my Firefox the sound stucks for a second. In fact everything seems a bit slowly, closing windows, see the poweroff menu and go on.
If u need some special output, please tell me exact what, I am still a newbie and already playing with the thought to reinstall XP after 8months Ubuntu.
cu

---

### Post by trmentry on 2008-04-28
> **ctpaterson said:**
> 
[*]In a terminal, type "sudo apt-get install linux-backports-modules-hardy-generic" to get wireless working (won't work until after you reboot later)



Is this for help with Broadcom based wireless cards?  My 1520 has a Intel based card in it.  On Gutsy it loaded up the restricted module ipw3945.  I did the Hardy upgrade and now its using the iwl3945 module.  

I'm going to test it out at work tomorrow.  The iwl3945 gave me issues in the past as it wouldn't associate to Cisco APs at work.  But the ipw3945 did.



Edit2: Nevermind... I just re-read the post again and saw you have the Intel based card.  I need more caffeine.

---

### Post by bayonetblaha on 2008-04-28
I've got multimedia buttons working for rhythmbox by default, but I much prefer amarok and for some reason they don't control amarok. Any ideas on how to get this going?

---

### Post by someguy2000 on 2008-04-28
My Inspiron 1520 came with the Dell Wireless 1395 card. After hours of headaches I finally figured out that to get this card working in Ubuntu, you need to use a Windows driver with ndiswrapper. WEP and WPA work flawlessly and I have very good connectivity. The driver ID is R174291 and can be found here ( [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174291&SystemID=INS_PNT_PM_1520&servicetag=&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R174291&SystemID=INS_PNT_PM_1520&servicetag=&os=WW1&osl=en&deviceid=15680&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=236819) ). 
Extract all the files to a folder somewhere, I just put them in a folder called wireless_drivers in my home folder.
Go to Synaptic Package Manager and install ndiswrapper.
Go to Administration -> Windows Wireless Drivers, and browse for the bcmwl5.inf file which is in the DRIVER_US folder.
Oh yeah, and make sure you add **blacklist bcm43xx** in /etc/modprobe.d/blacklist

---

### Post by ctpaterson on 2008-04-29
So, as it turned out I **do** have the laptop drive parking problem.  There is a bug detailing the problem here: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695).

I've employed a fix which seems to be generally good - I believe the net effect is to prevent the parking while the laptop is plugged in to AC power, but it still parks while running on battery.

I see a parking rate of about once a minute when idle and on battery life.  More parking when I type and stop, type and stop.  I might still tweak - but here's what I have.

The steps I took are as follows:

[list]
[*]edit /etc/default/acpi-support
[*]change ENABLE_LAPTOP_MODE value from false to true
[*]change SPINDOWN_TIME to 0
[*]edit /etc/laptop-mode/laptop-mode.conf
[*]change CONTROL_HD_POWERMGMT to 1
[*]change BATT_HD_POWERMGMT to 255
[*]change LM_AC_HD_POWERMGMT to 255
[*]change NOLM_AC_HD_POWERMGMT to 255
[/list]

Please note that this kind of thing is a little more than suggesting you install this package or that.  We're changing how the hardware behaves.  Get yourself informed about what this does and whether you're comfortable with it.  Proceed at your own risk.

---

### Post by ctpaterson on 2008-04-29
> **mac-duff said:**
> Hi there,
thanks for the new thread. 
Of course I have some trouble and every time something different. Sound works great and also the speak go to mute by unplugging a headset. But it seems that only one application at the same time can access by sound device. For example I listen a mp3 and start a VM, VMware tells me that the sound device is busy and also in Skype I have no sound actually.
Can also someone confirm that the system hangs very often? I mean I listen again a mp3 and if I switch the tabs in my Firefox the sound stucks for a second. In fact everything seems a bit slowly, closing windows, see the poweroff menu and go on.
If u need some special output, please tell me exact what, I am still a newbie and already playing with the thought to reinstall XP after 8months Ubuntu.
cu

Hey mac-duff.  I'm seeing the same thing; I played rhythmbox, paused it, tried to play a youtube video, and youtube was silent.  No idea how to fix it yet - but just thought I'd let you know you're not alone.

Cheers.

---

### Post by someguy2000 on 2008-04-29
I have exactly the same problem. Restarting firefox a couple times seems to get the sound back sometimes.

---

### Post by mac-duff on 2008-04-30
Well, I am going to try Fedora... I am a bit pissed there the most things work fine with version 7.10.
And what I dont understand, we have more or less all the same notebook (Bios Version A07) and all independent problems

---

### Post by ctpaterson on 2008-04-30
> **mac-duff said:**
> Well, I am going to try Fedora... I am a bit pissed there the most things work fine with version 7.10.
And what I dont understand, we have more or less all the same notebook (Bios Version A07) and all independent problems

It's part of the fun and adventure of Linux - I'm afraid.  I'm a big fan, but when people ask me whether "regular" people could use it...I'm inclined to compare it to the Win98ish experience; pretty much there - but occasional oddities that must be addressed.


As for the audio issue - I think I've come on to something.  Apparently the default audio manager for Hardy has been changed from ALSA to PulseAudio.  I'm not sure what the benefits of the change are supposed to be, but my multi-audio-tasking seems better served by switching back.

In System -> Preferences -> Sound, under the Devices tab; I've changed all the options from "Autodetect" to "ALSA".  I needed to shut down the applications attempting to use the soundcard before I could reap the benefits; but I can now play music and the audio from a youtube video at the same time (the means by which I reproduced your problem).

If you haven't switched yet, give it a whirl, and let me know how it works.

As an aside...I think I now know how to fix the audio problems I've been having with my Mythbuntu installation...

Cheers.

---

### Post by steve_4802 on 2008-04-30
Regarding the DVD playback colour issue, I go my video card wrong - I actually have an Nvidia GeForce 8400M GS.

If I track down a solution I'll let you know

---

### Post by ctpaterson on 2008-04-30
> **steve_4802 said:**
> Regarding the DVD playback colour issue, I go my video card wrong - I actually have an Nvidia GeForce 8400M GS.

If I track down a solution I'll let you know

Thanks, Steve!  I've updated the top post to point to a thread I was reading where some have been able to correct the problem (which seems to gravitate to Totem).  I haven't had a chance to test it with my 8600 card - but I'm hoping to try tonight or tomorrow.

Cheers.

---

### Post by mac-duff on 2008-04-30
Hi,
thx for the tip with the sound but thats not all, sadly. the sound is still stucking by switching tabs in firefox and also firefox itself hangs very often. Very frustrating, by Windows98 I never had problems like that :D

---

### Post by amyst on 2008-04-30
With compizconfig-settings-manager, emerald, and gnome-compiz-manager, I could get compiz fusion effects on Gutsy. On a fresh install of Hardy, I don't see gnome-compiz-manager in Synaptic anymore. What packages do I need to get cube, etc working in Hardy?

---

### Post by ctpaterson on 2008-05-01
> **amyst8 said:**
> With compizconfig-settings-manager, emerald, and gnome-compiz-manager, I could get compiz fusion effects on Gutsy. On a fresh install of Hardy, I don't see gnome-compiz-manager in Synaptic anymore. What packages do I need to get cube, etc working in Hardy?

As per the top post, I did it by running "sudo apt-get install compizconfig-settings-manager"

After that, there's a new menu option: System -> Preferences -> Advanced Desktop Effects Settings.

In that settings window, I'm able to configure all sorts of desktop candy.

---

### Post by ctpaterson on 2008-05-01
> **mac-duff said:**
> Hi,
thx for the tip with the sound but thats not all, sadly. the sound is still stucking by switching tabs in firefox and also firefox itself hangs very often. Very frustrating, by Windows98 I never had problems like that :D

Dude - if you never had Win98 applications, or Win98 itself crash on you...then you were the luckiest user there was.

In Feisty and in Gutsy, I had the occasional Firefox crash.  I think it's gone south since my Hardy upgrade - but I can't be sure.  I haven't seen any oddities by switching tabs - but then I didn't notice any sound problems until you drew my attention to it, so they might well be there.

I'll look to see if I see any of these symptoms - but in the mean time, is there any procedure or set of steps you can give us to reproduce the problems you're seeing?  I also have to ask if you're running the default Firefox installation that came with Hardy (Firefox 3 Beta 5), and whether you have any plugins installed.

Cheers.

---

### Post by liferock on 2008-05-01
ohh i have many questions....for i can see this troubles remain that will say one for one:
1º still are excessive parking hard disk in this laptop? 
2º the wifi led dont works??
3º i have a inspiron 1520 with a chipset intel GMA 965(x3100). can i hibernate and suspend with this chipset??
4º can i now Playback of video DVDs??? i did make a question because on my gusty just eared the dvd movies but not see the video

i hope that to be respond my questions and maybe (If troubles least in this version) upgrade to hardy 
Thanks

---

### Post by bayonetblaha on 2008-05-01
wow, try recording on audacity set to alsa:default while the alsamixer is set to analog input. Intense static sound completely ruins whatever you're trying to do; it's there even when nothing is plugged in. Is this just a shitty sound card? Anyone find a fix for this?

could anyone with audacity working properly list their configuration as far as audacity settings and volume prefs?

---

### Post by alfredska on 2008-05-27
It's been some time since Hardy was released to the masses.  I noticed that  a kernel update was made available a couple of days ago.  Out of curiosity, I formatted and reinstalled Hardy to see how the base install + updates cope with the 1520.

The procedure I followed:
 Install Hardy from i386 DVD
 Install updates available through official sources (no backports or pre-releases)
 Install nVidia restricted driver
 Customize

I'm pleasantly surprised, this release has come some distance since initial release.  Most of my problems were video related and they seem to be resolved.
 - The nVidia non-black shadows bug no longer requires a hack (ie. shadows are the correct color).
 - Both DVD and MPEG4/x264 videos play without color (hue) problems.

Wireless worked out of the box (I never suffered from this problem, it would be nice to hear if this has been fixed for others).

Sound worked out of the box (I did need to up the "Front" volume).

My bluetooth mouse worked after issuing: sudo hidd --search

I followed the instructions in the first post about correct levels for the built in digital mic.  It works well with skype.  I also tried the side mic jack (as the OP mentioned, changing input source from digital mic to analog mic does switch to the side jack).  You'll want to add "Capture" to the volume controls dialog (right click on speaker icon, Open Volume Control, Edit: Preferences, checkmark: Capture and Input Source).  You can select between the digital mic and side jack using Options tab of the volume control window, and adjust the mic volume on the recording tab.

It's... just... working!

---

### Post by alfredska on 2008-05-27
> **bayonetblaha said:**
> wow, try recording on audacity set to alsa:default while the alsamixer is set to analog input. Intense static sound completely ruins whatever you're trying to do; it's there even when nothing is plugged in. Is this just a shitty sound card? Anyone find a fix for this?

could anyone with audacity working properly list their configuration as far as audacity settings and volume prefs?

Recording at 48000Hz, 16 bit PCM, my dinky little microphone does not produce an abnormal amount of static.  Any static present is because of the low quality of my microphone.  Here are my volume settings:
 - In audacity, the mic volume is set to 1.0
 - In the volume control applet, the capture volume is set to 75%.

On a partially related note, I used to have trouble with lots of static, hissing, beeping from the sound OUT jack.  I followed the hardware fix [_here_]("http://forum.notebookreview.com/showthread.php?t=197809") and 90% of the static, hiss, beep has gone away.  (unfortunately, the OP of that post took the pictures offline)

---

### Post by carminez on 2008-06-20
Has anyone upgraded Gutsy (7.10) to Hardy (8.04)? Not a fresh install of Hardy? Any know issues with upgrading? I'd rather not wipe my machine for a fresh install if I don't have to.

---

### Post by bobstro on 2008-07-01
> **alfredska said:**
> 1) Bluetooth works for me as soon as I issue the command:
```
sudo hidd --search
```2) 
This fixed my bluetooth mouse problem under Hardy. Thanks!

- Bob

---

### Post by alfredska on 2008-07-01
Glad to hear it worked for you Bob.

I'd like to add a link to a thread discussing audio playback of multiple streams using Pulse (the default audio server for Hardy).  First, a disclaimer: Pulse is immature; you are likely to run into bugs, hence the length of the guide in the subsequent link.  I tend to agree with the recommendation of the OP, just switch the default device to ALSA until Pulse matures.  With that said, if you're adventurous: [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)]("http://ubuntuforums.org/showthread.php?t=789578")
Following the steps in Parts A and C (opted against Part B, instead using "libflashsupport" since flash 10 beta caused slowdowns), our laptops can play multiple sound sources at the same time, such as Skype, Songbird and flash media.

Also, as far as wireless is concerned, it tuns out my LED doesn't work either, I just noticed this for the first time last week.  Still, the connection has always worked well and I could care less about the LED.

With that said, I have recently helped someone with the same Intel 3945 wireless card get past some connection problems.  We opted to NOT install the backport-modules, and instead use the latest kernel update with the following file modification ([source]("http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/")):

1) Create a file named iwl3945 in /etc/modprobe.d with the following contents:
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```
2) Restart the computer

While the LED still wont work ([link]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090") to bug report), the connections works well.

Finally, [here is a terrific post]("http://ubuntuforums.org/showthread.php?p=4910397") about Bluetooth headsets in Ubuntu Hardy.

---

### Post by scobb99 on 2008-07-01
> **ctpaterson said:**
> In System -> Preferences -> Sound, under the Devices tab; I've changed all the options from "Autodetect" to "ALSA"....If you haven't switched yet, give it a whirl, and let me know how it works.

Works great on my Ubuntu Dell! Thanks a bunch for this tip.

I have to say I was very impressed overall with the upgrade to 8.04. It downloaded and installed 666 megabytes of code and the 'failure' of audio was the only glitch, so far, touch silicon. I could have probably figured this one out myself eventually if I had bothered to muck about in System Preferences but your message saved me a lot of guess work.

Unilaterally changing the sound system, without much fanfare [apologies for the pun] was probably not the smart thing to do with Hardy, given the large number of messages I have spotted from folks who are having issues with PulseAudio. 

Personally, I've found ALSA works fine -- the 64k AAC+ audio stream from RadioParadise.com sounds great.

Cheers...Stephen

---

### Post by lellyville on 2008-09-27
my dell's spec is exactly the same as the thread starter, this is problem i'm having
It started today, when i suspended my laptop and i went to a tutorial, after tutorial about 45 minutes i went to one of my afternoon lectures. Since before i was always suspend in windows this time i suspended from unbuntu. so when i took it out of my bag it was super hot everywhere, so i quickly opened the lid, typed my password in and shut it off. I found that my battery was also drained from 70% down to 7% !!!!. So how do i fix this? or i just can't??

suspend and hibernate works but my laptop just overheats than when it's not in susp/hib mode.

---

### Post by bobstro on 2008-09-28
> **lellyville said:**
>  [...] suspend and hibernate works but my laptop just overheats than when it's not in susp/hib mode.

That sounds like it's not going fully into hibernate or suspend mode. The same thing happens with my D420 if it doesn't completely 'sleep' before I close the lid. Does the LED do the same slow blink or whatever the indicators are in Windows that it's fully suspended? What are your power settings?

- Bob

---

### Post by lellyville on 2008-09-28
Awesome ! found someone with the same problem, i just tested today that hibernation works, except it takes like 2 minutes to wake up from hibernation. I also tested in Vista when i go into suspend mode the power led flashes, it's the same as in ubuntu except it heats up over time, it feel more hot than when it's not in suspend mode.
Sorry i'm still new at this what do you mean by power settings?

---

### Post by perfectska04@hotmail.com on 2008-10-23
This guide and the previous one for Ubuntu 7.10 really saved me a lot of time with my laptop. Will there be a new one for Ubuntu 8.10, or does anyone who has tested the new release know if everything finally works perfectly out of the box?

---

### Post by ctpaterson on 2008-10-24
> **perfectska04@hotmail.com said:**
> This guide and the previous one for Ubuntu 7.10 really saved me a lot of time with my laptop. Will there be a new one for Ubuntu 8.10, or does anyone who has tested the new release know if everything finally works perfectly out of the box?

Glad to hear they were of use to you.  I have only continued forward after the steps taken in the original post, and any comments that followed.  I did not revert back to see if the updates ended up settling some of the things that needed to be tweaked at release.

At this time, I have no plans to upgrade to 8.10.  The laptop I used for these guides is my main machine...so I'm happy to document the work I end up doing on it for the benefit of others - but the guide wasn't the point of the exercise.  So, if I don't have a reason to upgrade (and I currently don't), I'm afraid there won't be a guide coming from this corner.

I'll take another look when it comes out, and I have a friend and colleague who sits less than six feet from me every day who is sure to give 8.10 a drive -- so maybe I'll be convinced...and if it happens, I'll be kinda hoping someone else has taken up the cause.

You guys should lobby alfredska to write one.  He's been way more help to everyone than I have anyway.  ;>

Cheers.

---

### Post by perfectska04@hotmail.com on 2008-10-25
> **ctpaterson said:**
> Glad to hear they were of use to you.  I have only continued forward after the steps taken in the original post, and any comments that followed.  I did not revert back to see if the updates ended up settling some of the things that needed to be tweaked at release.

At this time, I have no plans to upgrade to 8.10.  The laptop I used for these guides is my main machine...so I'm happy to document the work I end up doing on it for the benefit of others - but the guide wasn't the point of the exercise.  So, if I don't have a reason to upgrade (and I currently don't), I'm afraid there won't be a guide coming from this corner.

I'll take another look when it comes out, and I have a friend and colleague who sits less than six feet from me every day who is sure to give 8.10 a drive -- so maybe I'll be convinced...and if it happens, I'll be kinda hoping someone else has taken up the cause.

You guys should lobby alfredska to write one.  He's been way more help to everyone than I have anyway.  ;>

Cheers.

Well, thanks for your posts regardless. I'll be installing Intrepid on my 1520 tonight, so I'll post here and comment on how well everything works (although it might not be as thorough and would be limited to my configuration, which is pretty much the same as OP)

---

### Post by perfectska04@hotmail.com on 2008-10-30
Ok, I just did a fresh Intrepid install.
Here are my specs:

    * Ubuntu Intrepid 64-Bits.
    * Intel Core 2 Duo T7500
    * 2 GB RAM
    * 1680x1050 display
    * 256MB Nvidia GeForce 8600M GT
    * High Definition Audio 2.0
    * Intel PRO/Wireless 3945abg
    * Integrated webcam

Everything I tested is working out of the box (Including Hibernate and Suspend). The "Hardware Drivers" tool set up my Nvidia card perfectly by installing driver 177, so after a reboot Compiz Fusion was working correctly.

The media slots, ethernet, dvd drive, usb, wireless, headphone jack and sound all worked (although you still need to go to the volume control and raise the "Front" slider to hear sound at a reasonable volume).

The webcam turns on but I tried it in "Cheese" and it crashed. Perhaps it works in Ekiga or other apps, but I haven't gotten around to test that yet. 

Things I haven't yet tested because I don't really use them:
    * Dial-Up Modem
    * Firewire
    * Bluetooth
    * Microphone/Input Jack
    * Mobile Broadband
    * Vga Output

One other thing to note, this time you can fix the hard drive clicking noises (if your drive has that issue) simply by enabling laptop-mode. You can enable laptop-mode by editing /etc/default/acpi-support and its relevant line.

If you're using Nvidia, it's **very** recommended to go to this official Nvidia site and follow its instructions in order to greatly improve your graphics performance:
[http://www.nvnews.net/vbulletin/showthread.php?t=118088]("http://www.nvnews.net/vbulletin/showthread.php?t=118088")

---

### Post by ctpaterson on 2008-10-31
> **perfectska04@hotmail.com said:**
> Everything I tested is working out of the box (Including Hibernate and Suspend). The "Hardware Drivers" tool set up my Nvidia card perfectly by installing driver 177, so after a reboot Compiz Fusion was working correctly.

Hibernate and suspend are working?  Can anyone confirm this with 32 bit?

Bugger...now I'll have to go and upgrade.  ;>

Thanks.

---

### Post by alfredska on 2008-11-02
> **ctpaterson said:**
> Bugger...now I'll have to go and upgrade.  ;>

Thanks.

Oh boy, here we go again.  If it ain't broke... fix it...

I'll add my results later next week, perhaps when some decent info is collected between several of us a new 8.10/1520 post can be erected.

~Matt

---

### Post by ctpaterson on 2008-11-10
> **ctpaterson said:**
> Hibernate and suspend are working?  Can anyone confirm this with 32 bit?

So, I was on vacation last week, and so kicked-off an in-place upgrade from Hardy to Intrepid.  First off, you actually have to do a bit of work to be able to do that: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Once that was upgraded (took a long time), I followed perfectska's advice in terms of enabling laptop mode, and using the xorg options to improve video performance.

Suspend and hibernate work like a charm - making this venture worthwhile.  I've noticed no other issues with the things that I had working before (see the top post), though I have not done a thorough test yet.

I have had to re-enter my wireless keys - which seems wrong for an in-place upgrade, but I've moved on with it.

Cheers.

---

### Post by perfectska04@hotmail.com on 2008-11-10
> **ctpaterson said:**
> So, I was on vacation last week, and so kicked-off an in-place upgrade from Hardy to Intrepid.  First off, you actually have to do a bit of work to be able to do that: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Once that was upgraded (took a long time), I followed perfectska's advice in terms of enabling laptop mode, and using the xorg options to improve video performance.

Suspend and hibernate work like a charm - making this venture worthwhile.  I've noticed no other issues with the things that I had working before (see the top post), though I have not done a thorough test yet.

I have had to re-enter my wireless keys - which seems wrong for an in-place upgrade, but I've moved on with it.

Cheers.

Thanks for the input!
Oh and a little update from my part:
-Webcam works out of the box, the only app that won't work with it is "Cheese".
-For switching between the laptop Mic and the input Mic, instead of running alsamixer, etc, you can just run the "Volume Control", click preferences, enable "Digital Input Source" and then switch betweeen "Analog Inputs" and "Digital Mic 1".

---

### Post by vandorjw on 2008-11-21
I am running ubuntu 8.10 and the only program that works with my webcam is skype.

camera; cheese; & camorama do not work.

camorama tells me that it cannot connect to dev0, and to check my wires?

---

### Post by woculp on 2009-05-06
Would any of you Gurus be interested in posting a comprehensive guide to installing and tweaking Ubuntu 9.xx on the Inspiron 1520?  I know this laptop is now showing it's age, but I'm sure there are many of us owners still out there.

---

### Post by alfredska on 2009-05-06
I agree that there are still many of us 1520 users out there (I'm typing this from mine), but there isn't much of anything that does not work out of box, since 8.10.  The purpose of these threads was to get all sound/graphics/standby/bluetooth, etc issues resolved, but this is not an issue anymore.  I'd just say, install 9.xx, allow the proprietary nVidia graphics driver, and enjoy your computer.  MediaDirect is the only gotcha, but my old topic (listed in my signature) still works.

---

### Post by ctpaterson on 2009-05-22
> **alfredska said:**
> I agree that there are still many of us 1520 users out there (I'm typing this from mine), but there isn't much of anything that does not work out of box, since 8.10.  The purpose of these threads was to get all sound/graphics/standby/bluetooth, etc issues resolved, but this is not an issue anymore.  I'd just say, install 9.xx, allow the proprietary nVidia graphics driver, and enjoy your computer.  MediaDirect is the only gotcha, but my old topic (listed in my signature) still works.

Seconded from this corner.  I'm running 64-bit 9.04 now, and I thought about writing a guide in a similar vein to the last two...but then there was really nothing to say.  Everything I've done post install was a matter of preferences.

The only thing worth mentioning, I suppose, is that I've got a problem in that the laptop does not shutdown properly.  I believe this is a known bug, and will simply be resolved in time.  Other than that, it's smooth sailing.  Drivers are good; suspend, hibernate, I think even Bluetooth works, now (though I haven't gone all the way to do a pairing).

If you're having problems, I'd recommend a specific post about them.  Ubuntu on an Inspiron 1520 seems to have graduated.

Cheers.

---

### Post by mac-duff on 2009-05-23
Hi,
just wanted to say that I still have problems with my Bluetooth device on my 1520 with Ubuntu 9.04.
Has anybody an idea how I can get it working?

Thx

---

### Post by alfredska on 2009-06-18
> **mac-duff said:**
> Hi,
just wanted to say that I still have problems with my Bluetooth device on my 1520 with Ubuntu 9.04.
Has anybody an idea how I can get it working?

Ok, I spoke too soon about Jaunty's out-of-box compatibility with the Inspiron 1520.  My Intrepid installation was working so well that I never put much testing into Jaunty.

Here's the two main fixes that I needed:
[LIST=1]
[*]**Bluetooth**: [This bug report]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727") will help in correcting bluetooth mice issues.  (It works for more than the titled Microsoft 5000)  The comments of interest are: [Workaround 1 by abais]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727/comments/10") (for some the search must be done at each reboot), [Extension 1 of Workaround 1]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727/comments/57") by Priit Tamboom (some people STILL need to search after each reboot), [Extension 2 of Workaround 1]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/343727/comments/69") by John K.
[*]**nVidia Display Drivers**: Both the open source nvidia driver and the proprietary driver caused hangs during shutdown for me.  [This thread]("http://ubuntuforums.org/showthread.php?t=1125400") details (in excruciating detail) how to install nVidia 185.18, which works well.
[/LIST]

ctpaterson, you're the thread starting king so far, these two points might warrant a new thread if you're interested in putting up an "Inspiron 1520 & Jaunty Tutorial".

A couple of non-inspiron-specific notes:
[LIST=1]
[*]**KDE4 Applications**: If you use some KDE apps under the GNOME desktop, and don't much care for the new window decorations, install packages: systemsettings, kdeartwork
Then you can access the KDE settings from Applications -> System Tools -> System Settings (settings changed here will only affect KDE applications)
[*]**Non-GNU Licensed Software**: Considerably more applications, audo/video decoders, and fonts are available if you enable the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu").  For instance, the package "ubuntu-restricted-extras" provides microsoft fonts, sun java, adobe flash, video decoders, and much more.
[/LIST]

Edit 1: Ok, so I'm still experiencing a hang at shutdown.  A cross-hatch of colored lines over most of the screen.  Issuing CTRL-ALT-DEL gets past the hang, but this turns a shutdown into a reboot. [This bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/302452") may be related (if so, a kernel update is required).

Edit 2: Perhaps Intrepid is just far more stable on these machines (most machines?).  Even WINE is throwing new errors with applications that always worked well in the past.  At this point I see very little compelling reason to use Jaunty.  Intrepid just works so well.

---

### Post by ctpaterson on 2009-06-24
> **alfredska said:**
> 
[LIST]
[*]**nVidia Display Drivers**: Both the open source nvidia driver and the proprietary driver caused hangs during shutdown for me.  [This thread]("http://ubuntuforums.org/showthread.php?t=1125400") details (in excruciating detail) how to install nVidia 185.18, which works well.
[/LIST]


Well, that's interesting - I get a hanging issue at shutdown as well, but I'm currently working around it by administratively bringing the wireless card down before halting.  There's a bug about that, too, but the number escapes me at the moment.

> 
ctpaterson, you're the thread starting king so far, these two points might warrant a new thread if you're interested in putting up an "Inspiron 1520 & Jaunty Tutorial".


Aw hell.  ;>  Okay, I'll try and get 'round to it, if there isn't one already.

> 
Edit 2: Perhaps Intrepid is just far more stable on these machines (most machines?).  Even WINE is throwing new errors with applications that always worked well in the past.  At this point I see very little compelling reason to use Jaunty.  Intrepid just works so well.

The thought has occurred to me.  I'm getting hangs at shutdown, the occasionally GUI glitch (minor stuff; window title bars don't change colour when focused, text disappears until window redrawn, etc), and flash on Firefox sometimes won't play (could be a problem with the FlashBlock plugin).

As for the wine problems you mentioned, alfredska; I run Quicken 2000 under Wine...it mostly works except for a few glitches.  I've changed wine versions many times over the years, and each time I do, the glitches I had get traded in for a new set...sometimes I'm better off, sometimes worse.

Cheers.

---

### Post by alfredska on 2009-07-06
Note: This post is about Jaunty.

Following a suggestion in [Launchpad Bug Report #326988]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/326988"), installing linux-backports-modules-jaunty finally did resolve my shutdown hangs.  I still have ugly colored crosshatch, but I relate this to the nVidia driver I installed, as it was a blank screen with flashing cursor before installing the driver.
```
sudo apt-get install linux-backports-modules-jaunty
```

My problems with wine were resolved by killing all running wine processes, then running winecfg, and setting emulation type and audio output.  After closing winecfg, I was able to run my wine program without errors.

---

