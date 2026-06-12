---
title: "firefox 48.0.2 keeps crashing on lubuntu 16.04.2"
date: 2017-07-12
forum: New to Ubuntu
---

### Post by gazzawazza on 2017-07-12
hi all

**problem:**
please forgive me for being a complete and utter linux noob but I'm finding linux fairly heavy going, being utterly unfamiliar with it, and am totally struggling with why firefox 48.0.2 keeps crashing on startup.

**background:**
i installed lubuntu 15.10 approx 6 weeks ago from a boot CD. That was ok.

I struggled a bit to get updating working but sorted that out (had to change repositories, etc)

Went to 16.04.x (don't know which exact build). This too went well.

I'm almost 100% whichever update i went to from 15.10 gave me Firefox 48

Anyway, i updated again, i believe going to 16.04.1 or 16.04.2

This installed FF53, which i know (from my winXP installation) isn't supported on my hardware (athlon xp1800). So, when it crashed, I wasn't surprised.

**action taken:**
I removed FF53 and attempted to return to FF48. I can't remember what uninstallation order I followed but i know at some point I used Synaptic to do a thorough cleanse. If I recall too, I did use apt-get clean and autoremove.

After horrible fumbling because I just didn't understand how software installation works on linux (and am only a touch more informed now), I got to a point where I had firefox on my system (I'd downloaded the tar.bz2 from mozilla directly, extracted and copied across).

Unfortunately, FF48 just crashed on starting and I simply don't know why, since it worked on the first build of lubuntu 16.04 i updated to.

After uninstalling, I removed the main firefox folder (/usr/lib) and .mozilla (/home/user), in case of a profile problem, so i believe my subsequent installation was 'clean'.

I tried the latest repository version of FF (v54), to check where it installs to (that's how ignorant i am of linux - i don't/didn't even know where stuff gets installed :(), then removed it and tried FF48 again.

I found a deb of FF48 (ubuntuzilla repository) and on installation it reported dependencies ok, so i thought things would be ok. Unfortunately, Firefox still crashes on startup (when I run from the firefox shortcut in the program menu), so I'm reasonably confident that I'm not missing a fundamental library or something obvious like that, which of course points to some other issue.

I was very careful to select x686 or i386 versions of firefox.

I've looked at the firefox crash report but couldn't see anything obvious (though it is 6am and I could quite easily have missed something).

I thought of checking the equivalent of Event Viewer but don't have a clue about troubleshooting in linux :(

Any ideas on why firefox might be crashing?

Something that was installed with 16.04.2 LTS and FF53, which FF48 doesn't 'like'?

**workrounds:**
I've tried some other browsers from the software centre but found they are extremely unstable (arora, qupzilla and web). I'm talking crashing either on startup or within 2 pages of use. The current repository version of chromium won't work because of SSE2 requirements (like latest firefox).

**end-goal:**
I'd just like to get back to firefox 48, since it's my preferred browser on windows and of course worked fine at one point with lubuntu.

Any help would be appreciated.



Regards,

Gary

---

### Post by Autodave on 2017-07-12
Lubuntu 16.04 is where you want to stay for now. How about some specs on your machine? Do you have a video card installed or are you running from the motherboard's video?

---

### Post by poorguy on 2017-07-12
Hey gazzawazza,

I believe with that processor being SSE and not SSE2 or newer you are going to run into problems with most browsers as they no longer support processors that are only SSE.

---

### Post by gazzawazza on 2017-07-12
> **Autodave said:**
> Lubuntu 16.04 is where you want to stay for now. How about some specs on your machine? Do you have a video card installed or are you running from the motherboard's video?

thanks Dave

CPU  - athlon XP1800+
RAM - 761MB (reported by system summary tool) / 744MB reported by task manager
audio - cmedia CMI87638
**EDIT: **graphics - pretty sure it's discrete. *Asus Nvidia geforce 2 MX400.*

Anything else you need?


Thanks,

Gaz

PS can I tag your forum username? Tried @ and # but no picklist

---

### Post by gazzawazza on 2017-07-12
> **poorguy said:**
> Hey gazzawazza,

I believe with that processor being SSE and not SSE2 or newer you are going to run into problems with most browsers as they no longer support processors that are only SSE.

Hi Poorguy

OK thanks. I'd agree.

However, it's the fact that firefox was working quite happily until my 2nd OS update AND that i know FF48.0.2 supports SSE, that is frustrating.

Also, quipzilla and Arora don't do a hardware check and refuse to work (like post FF48 builds). They just crash after 1-2 pages browsing.

Sorry - gotta dash. business call.

Anyway thoughts?



Regards,

Gary

---

### Post by poorguy on 2017-07-12
This is my oldest Machine:  

Mobo: Gigabyte model: GA-K8VM800M (rev 2.x)  Bios: Award v: FD date: 12/07/2005
CPU: Single core AMD Sempron 2800+ (1.60GHz) cache: 256 KBand 

I'm using antix 17 and FF 52.2 ESR it works but I mean Firefox crawls.
I beleive up to FF 53 ESR will support SSE processors.

Whatever will work is what you use.

---

### Post by gazzawazza on 2017-07-12
> **poorguy said:**
> This is my oldest Machine:  

Mobo: Gigabyte model: GA-K8VM800M (rev 2.x)  Bios: Award v: FD date: 12/07/2005
CPU: Single core AMD Sempron 2800+ (1.60GHz) cache: 256 KBand 

I'm using antix 17 and FF 52.2 ESR it works but I mean Firefox crawls.
I beleive up to FF 53 ESR will support SSE processors.

Whatever will work is what you use.

Am 100% that FF49 onwards requires SSE2 support

Sempron does that, though I wonder whether the sluggish browsing is down to choking on a single core.

Also, I guess I'm used to everything happening slloooooowwwwwllllyyy on the box we're discussing. I didn't actually feel linux was slow. Maybe a little faster than winXP but I'm just used to it being slow compared to my main box which is haswell i5, SSD, etc.

---

### Post by poorguy on 2017-07-12
> **gazzawazza said:**
> Am 100% that FF49 onwards requires SSE2 support

Sempron does that, though I wonder whether the sluggish browsing is down to choking on a single core.
You are right about the Sempron being SSE2 and above I hadn't realized that it was.

FF 52.2 is probably a resource hog and the single core processor just can't run it.

---

### Post by gazzawazza on 2017-07-12
> **poorguy said:**
> You are right about the Sempron being SSE2 and above I hadn't realized that it was.

FF 52.2 is probably a resource hog and the single core processor just can't run it.

depends of course what you're viewing too.

I've historically turned off FF hardware acceleration (if I recall correctly, it's one of the first troubleshooting steps cited by mozilla, etc), so that means there's a lot dumped on the CPU i.e. multimedia scenarios, webGL, etc. Also, though flash in theory uses hardware acceleration, HTML5 presumably doesn't if hardware acceleration is off in FF.

---

### Post by Impavidus on 2017-07-12
> **gazzawazza said:**
> 
i installed lubuntu 15.10 approx 6 weeks ago from a boot CD. That was ok.

I struggled a bit to get updating working but sorted that out (had to change repositories, etc)

Went to 16.04.x (don't know which exact build). This too went well.

I'm almost 100% whichever update i went to from 15.10 gave me Firefox 48

Anyway, i updated again, i believe going to 16.04.1 or 16.04.2

This installed FF53, which i know (from my winXP installation) isn't supported on my hardware (athlon xp1800). So, when it crashed, I wasn't surprised.

Ubuntu 15.10 has been dead for a while. The original repository (with Firefox 41 I think) and the updates to that (up to Firefox 48) have been archived in August 2016, so that's why you had to change repositories. So that gave you some updates, but no more updates for 15.10 have been made for 11 months, so you were running outdated software. Upgrading to 16.04 gave you the latest Firefox, that is 54 (or 53, a short while ago).

> **gazzawazza said:**
> Am 100% that FF49 onwards requires SSE2 support

If I have to believe Wikipedia, SSE2 is required on Windows from FF49 onwards and on Linux from FF53 onwards. So you may be able to run FF52, which is a extended support release (supported until June next year). You can't install it from the Ubuntu repositories.

---

### Post by gazzawazza on 2017-07-12
> **Impavidus said:**
> Ubuntu 15.10 has been dead for a while. The original repository (with Firefox 41 I think) and the updates to that (up to Firefox 48) have been archived in August 2016, so that's why you had to change repositories. So that gave you some updates, but no more updates for 15.10 have been made for 11 months, so you were running outdated software. Upgrading to 16.04 gave you the latest Firefox, that is 54 (or 53, a short while ago).


If I have to believe Wikipedia, SSE2 is required on Windows from FF49 onwards and on Linux from FF53 onwards. So you may be able to run FF52, which is a extended support release (supported until June next year). You can't install it from the Ubuntu repositories.

thanks for the insights Impavidus

I have no problem upgrading the OS, etc. Quite the opposite. I appreciate the (hopeful) stability and security improvements, as well as improved functionality.

However, when one is fumbling like a child to work out how to do things, browsers are indispensable, so when FF got updated, I was basically in a pickle.

I stand corrected regarding SSE2 requirement on linux.

However, there's still no inherent reason why I shouldn't be able to use FF48 (i.e. anything upto & incl FF52), unless you suspect that trying FF52 ESR might yield results?

Is there any way I can troubleshoot what's going wrong?

Is there anything centralised like the Windows Event Viewer (or other tools for checking on app crashes or troubleshooting in general i.e. logs, etc)?

Is there any reason, to your knowledge, for FF48 not being able to work with 16.04.2?

Amidst all my fatigued waffle from my initial post, I still find it frustrating that FF48 worked and an system update seemed to knacker it (though it's just as likely that I did something in my fumblings to uninstall and regress back to FF48). Is there a way to block app updates? I know there's an internal update option in FF but since system updates are effectively an external check (against the repository), can I stop those (granularly)?

In my position, how would you roll back to an earlier FF build and what things should I watch out for? Presumably I need my system to be as free as possible from the later FF build? Any other housekeeping that you'd recommend?



Regards,

Gary

---

### Post by &amp;KyT$0P# on 2017-07-13
Did you try the official build direct from Mozilla?  Latest version is [here]("https://www.mozilla.org/firefox/all/"), older versions are [here]("https://ftp.mozilla.org/pub/firefox/releases/").

Make sure you test it with a new [profile]("http://kb.mozillazine.org/Profile_folder_-_Firefox").  In my experience, the distribution builds of Firefox are not always fully compatible with the official builds.

> **gazzawazza said:**
> Is there a way to block app updates? I know there's an internal update option in FF but since system updates are effectively an external check (against the repository), can I stop those (granularly)?
Yes.  For example, to stop updating the package named "firefox" -
```
sudo apt-mark hold firefox
```

---

### Post by deadflowr on 2017-07-13
You might try palemoon for sse only:
[https://forum.palemoon.org/viewtopic.php?f=40&t=13530]("https://forum.palemoon.org/viewtopic.php?f=40&t=13530")
More on Palemoon here:
[https://linux.palemoon.org/]("https://linux.palemoon.org/")

---

### Post by gazzawazza on 2017-07-13
> **halogen2 said:**
> Did you try the official build direct from Mozilla?  Latest version is [here]("https://www.mozilla.org/firefox/all/"), older versions are [here]("https://ftp.mozilla.org/pub/firefox/releases/").

Make sure you test it with a new [profile]("http://kb.mozillazine.org/Profile_folder_-_Firefox").  In my experience, the distribution builds of Firefox are not always fully compatible with the official builds.


Yes.  For example, to stop updating the package named "firefox" -
```
sudo apt-mark hold firefox
```

thanks halogen2

VICTORY!!!!!!!! :)

Have seemingly stable FF52.0.2 running on my system.

Not to do with your profile advice, i don't think. Sorry (had done that prior to your suggestion).

Have to goto work so a bit rushed.

Basic approach though was to do clean uninstall of firefox, then found deb for 52.0.2 (as previously confirmed by Impavidus, this is last SSE supported build of FF on linux) and installed. Ubuntuzilla was source for deb (claims to be off of official FF build).

Had removed flash 26 too.

Software updater interestingly and randomly installed some audio component (pureaudio or maybe pulseaudio) too after uninstall but before reinstall.

I used both synaptic and command  line to remove firefox and qupzilla (sudo apt-get purge and then sudo apt autoremove).

Something has worked!

Just quickly, are there logs for the software updater (so I can check what/when something was updated)?




Regards,

Gary

---

### Post by &amp;KyT$0P# on 2017-07-13
> **gazzawazza said:**
> Just quickly, are there logs for the software updater (so I can check what/when something was updated)?
Check [FONT=Courier New]/var/log/apt/history.log[/FONT] and the history.(number).gz files in the same directory.

---

### Post by gazzawazza on 2017-07-13
> **halogen2 said:**
> Check [FONT=Courier New]/var/log/apt/history.log[/FONT] and the history.(number).gz files in the same directory.

thanks.

_**pulseaudio**_
checked APT logs and it the audio update appears to have been pulseaudio (a couple of libpulse files), oddly** not **triggered, to my knowledge, by me and was installed before I ran the FF52.0.2 deb.

EDIT: subsequently discovered that although libpulse files exist in this distro, i needed the full version of pulseaudio to get sound out of FF

_**FF crash trigger?**_
Also, more importantly, installing **the flashplugin-installer seems to trigger the FF crashes**. 

Just tested by installing it. FF crashed afterwards on startup and removing flashplugin-installer restored normal FF functionality.



Cheers,

Gary

---

### Post by gazzawazza on 2017-07-13
> **deadflowr said:**
> You might try palemoon for sse only:
[https://forum.palemoon.org/viewtopic.php?f=40&t=13530](https://forum.palemoon.org/viewtopic.php?f=40&t=13530)
More on Palemoon here:
[https://linux.palemoon.org/](https://linux.palemoon.org/)

thanks deadflowr

Appreciate that. Was actually considering trying palemoon after all the pain I'd experienced with other browsers but i seem to have got FF working now.

Seems like it's the latest flash (install/uninstall of flashplugin-installer introduces the FF crashing on start and then restores stability).

Any thoughts on this?

EDIT: does flash require SSE2?



Thanks,

Gary

---

### Post by &amp;KyT$0P# on 2017-07-13
Do you need Flash in your browser?

If so - if you purge [FONT=Courier New]flashplugin-installer[/FONT], and install the [FONT=Courier New]adobe-flashplugin[/FONT] package from the Canonical Partners repository, do you still get the crashing?

---

### Post by gazzawazza on 2017-07-13
> **halogen2 said:**
> Do you need Flash in your browser?

If so - if you purge [FONT=Courier New]flashplugin-installer[/FONT], and install the [FONT=Courier New]adobe-flashplugin[/FONT] package from the Canonical Partners repository, do you still get the crashing?

hello halogen2

To be fair, I've not noticed the absence of flash (and it's probably sped up my browsing). Equally well, maybe HTML5 solutions are providing an alternative.

RE: adobe-flashplugin. Couldn't find it in Synaptic. Searched on "adobe" and "flash". I guess though what I see in my package list is dependent on the download server I'm using (gb.archive.ubuntu.com/ubuntu)?

Tried sudo apt-get install adobe-flashplugin and got this as part of the response:

"Package adobe-flashplugin is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source"

"Canonical partners" is a volume under the "other software" tab of software & updates, so I'm guessing that I'm already got the "canonical partners repository" that you refer to, as a source to check for software from?



Thanks,

Gaz

PS sorry for being noobish

---

### Post by &amp;KyT$0P# on 2017-07-13
> **gazzawazza said:**
> To be fair, I've not noticed the absence of flash (and it's probably sped up my browsing). 
Then I suggest simply leaving it uninstalled until you need it.  In addition to what you said, a browser without Flash is probably more secure too.

> "Canonical partners" is a volume under the "other software" tab of software & updates, so I'm guessing that I'm already got the "canonical partners repository" that you refer to, as a source to check for software from?
You're in the right place.  The checkbox for Canonical Partners would need to be ticked.  If it already is, try running
```
sudo apt-get update
```

---

### Post by vasa1 on 2017-07-13
> **gazzawazza said:**
> .... I guess though what I see in my package list is dependent on the download server I'm using (gb.archive.ubuntu.com/ubuntu)?
...I think that *all* the official download servers would, sooner or later, have the same contents as the main server.

---

### Post by monkeybrain20122 on 2017-07-14
For your use case it is a lot easier to download the Firefox binary from Mozilla and run it off its folder instead of installing it in the system.It doesn't need installation and messing with respositories. Just download the version you want from [here]("https://ftp.mozilla.org/pub/firefox/releases/"). extract the tar.bz2 somewhere in your $HOME. To use just  navigate inside the Firefox folder and click firefox.

---

### Post by vasa1 on 2017-07-14
A friendlier download page is this: [https://www.mozilla.org/en-US/firefox/desktop/](https://www.mozilla.org/en-US/firefox/desktop/)

Keep in mind that versions obtained directly from Mozilla will require Pulseaudio on your system to hear audio.

Lubuntu 16.04 doesn't have Pulseaudio installed by default.

---

### Post by monkeybrain20122 on 2017-07-14
> **vasa1 said:**
> A friendlier download page is this: [https://www.mozilla.org/en-US/firefox/desktop/](https://www.mozilla.org/en-US/firefox/desktop/)

Keep in mind that versions obtained directly from Mozilla will require Pulseaudio on your system to hear audio.

Lubuntu 16.04 doesn't have Pulseaudio installed by default.

That link only has the latest FF. I think OP might want to run an earlier version.

---

### Post by vasa1 on 2017-07-14
> **monkeybrain20122 said:**
> That link only has the latest FF. I think OP might want to run an earlier version.

True! I forgot OP's SSE2 situation :(

---

### Post by gazzawazza on 2017-07-14
> **halogen2 said:**
> Then I suggest simply leaving it uninstalled until you need it.  In addition to what you said, a browser without Flash is probably more secure too.

You're in the right place.  The checkbox for Canonical Partners would need to be ticked.  If it already is, try running```
sudo apt-get update
```

Hey Halogen2

The canonical partners repository was unchecked. Checking this allowed adobe-flashplugin appear as a package. Using this installed flash 11.2 r202 - 29 june 2016 (according to FF).

Firefox didn't crash..... at first :) Didn't take long though. Good old flash.

So I'm not sure what this proves. An incompatibility between flash 26 and FF52.0.2? Something specific to do with the ubuntu flash 26 package?

Did you suggest this, just so I can get access to the adobe-flashplugin and test whether any version of flash would work?

Not sure I'm too comfortable with an antiquated version of flash but at least it shows flash can work with FF.

So what kind of software ends up in the canonical partners repository?


Thanks,

Gaz

---

### Post by gazzawazza on 2017-07-14
> **vasa1 said:**
> I think that *all* the official download servers would, sooner or later, have the same contents as the main server.

thanks Vasa1

yes logically, you'd have thought, as mirrors, that they'd replicate all content but it doesn't have to be like that I suppose. It's really just having the convenience of multiple sources to download from. One could limit the software you mirror i guess (though that would be a hindrance, if you had to swap server because a package wasn't on there). Perhaps a server could pull a requested package from another location, if it didn't have it?


Cheers,

Gaz

---

### Post by gazzawazza on 2017-07-14
> **monkeybrain20122 said:**
> For your use case it is a lot easier to download the Firefox binary from Mozilla and run it off its folder instead of installing it in the system.It doesn't need installation and messing with respositories. Just download the version you want from [here]("https://ftp.mozilla.org/pub/firefox/releases/"). extract the tar.bz2 somewhere in your $HOME. To use just  navigate inside the Firefox folder and click firefox.

thanks Monkeybrain20122

Why do you feel this would be easier?

I've discovered the joys of deb files. Obviously someone has to maintain these though.

Also, with tar.bz2 there's presumably no guarantee that it's been compiled and would i not be running the risk of missing dependencies?


Cheers,

Gaz

---

### Post by monkeybrain20122 on 2017-07-14
> **gazzawazza said:**
> thanks Monkeybrain20122

Why do you feel this would be easier?

I've discovered the joys of deb files. Obviously someone has to maintain these though.




It is easier because there is nothing to install and you don't need to worry about potential version conflicts, sources list and updates etc.


> Also, with tar.bz2 there's presumably no guarantee that it's been compiled and would i not be running the risk of missing dependencies?

Like I said this is a precompiled binary, just click and use.

---

### Post by gazzawazza on 2017-07-14
> **vasa1 said:**
> A friendlier download page is this: [https://www.mozilla.org/en-US/firefox/desktop/](https://www.mozilla.org/en-US/firefox/desktop/)

Keep in mind that versions obtained directly from Mozilla will require Pulseaudio on your system to hear audio.

Lubuntu 16.04 doesn't have Pulseaudio installed by default.


thanks vasa1

It's all ok. Don't worry about the wrong link. I appreciate your assistance. I sorted pulseaudio out too because FF warned me i might need it. What was confusing was that I'd had a pulseaudio system update on lubuntu BEFORE i did the all the faff (listed below) but I needed the full pulseaudio sound server installed for FF to produce audio.

To catch up:
[LIST]
[*]I'd already got a tar.bz2 for FF48.0.2 6 weeks ago (because FF48 was last to support SSE on windows, so I presumed the same for linux), when I first started having issues (not understanding anything about installing software on linux) and just about managed to install that.
[*]This didn't fix things. I didn't realise at the time but it appears that it's the official ubuntu flash 26 package which was causing the problems
[*]Impavidus (on this thread) suggested that FF52 was last SSE compatible on linux.
[*]I'd found out what deb files do and then found some cool dude called nanotube (on sourceforge) had made the ubuntuzilla repository, which hosts packages for both FF48 and FF52.
[*]I did a clean uninstall (purge/autoclean/autoremove) of FF versions, as best I could, and then as part of that tidy-up, removed flash 26 too, then installed FF52. Crashing stopped. I then tested and found addition/removal of flash26 triggered/stopped FF crashing.
[*]Halogen2 has got me to try an old flash version (from canonical partners repo), which does work with FF.
[*]So, don't know if it's a quirk of flash26.0.0.137 with FF52 or just this flash build
[/LIST]

Any thoughts?


Regards,

Gary

---

### Post by gazzawazza on 2017-07-14
> **monkeybrain20122 said:**
> It is easier because there is nothing to install and you don't need to worry about potential version conflicts, sources list and updates etc.




Like I said this is a precompiled binary, just click and use.

Thanks.

From my research about installing linux software, speaking generally, i thought deb files are more complete and tidy and it's just fortunate that the firefox tar.bz2 is precompiled. There's no guarantee that tar.bz2 files are compiled. Have I got that right?

EDIT: and I cheated with ubuntuzilla and just downloaded the deb files directly, rather than, as you said, having to mess with repositories. If nothing else, this should prevent any auto-updates, though I have put the firefox-mozilla-build package on apt-mark hold.

EDIT: I'm not quite sure exactly what behaviour a package exhibits on hold, if an update gets run? I found that even on hold, if update is enabled in firefox, i got what amounts to a permission denied statement regarding software needing updating (but I swear I got that same message before I put the ubuntuzilla FF package on hold, so maybe there's something else preventing the update).

EDIT1: this is the firefox message about wanting to update but permissions lacking. As I swear this occurred before putting package on hold, I suspect it's because I've not added the ubuntuzilla repository. I can prevent this by just turning off update in FF:


[IMG]http://storage2.static.itmages.com/i/17/0715/h_1500136679_1510868_b212212448.png[/IMG]




Cheers,

Gaz

---

### Post by &amp;KyT$0P# on 2017-07-15
> **gazzawazza said:**
> Using this installed flash 11.2 r202 - 29 june 2016 (according to FF).
Wait, what??  That package is supposed to contain Flash version 26.0.0.137.

> Did you suggest this, just so I can get access to the adobe-flashplugin and test whether any version of flash would work?
I suggested it in case you needed Flash and in case that version was different somehow and would work.  Again, if you don't need Flash, uninstalling Flash is the best answer here.

> **gazzawazza said:**
> Firefox didn't crash..... at first :) Didn't take long though. Good old flash.

... at least it shows flash can work with FF.
So which is it?  Does the older Flash cause crashing or not?

---

### Post by gazzawazza on 2017-07-15
> **halogen2 said:**
> Wait, what??  That package is supposed to contain Flash version 26.0.0.137.


I suggested it in case you needed Flash and in case that version was different somehow and would work.  Again, if you don't need Flash, uninstalling Flash is the best answer here.


So which is it?  Does the older Flash cause crashing or not?


Sorry for the confusion, Halogen2

The adobe-flashplugin installed the old version of flash (looks like it might have been for ubuntu 15.10, going on the filenames).

EDIT: 

[IMG]http://storage8.static.itmages.com/i/17/0715/h_1500094631_5044450_6a3c4b39b6.png[/IMG]

[http://storage8.static.itmages.com/i/17/0715/h_1500094631_5044450_6a3c4b39b6.png](http://storage8.static.itmages.com/i/17/0715/h_1500094631_5044450_6a3c4b39b6.png)


Firefox opened without crashing using the older version of flash but then firefox crashed a few mins later. The error, this time, was caught by ubuntu and recorded as being to do with firefox plugin-container. I immediately suspected flash (as it's about the only plug-in). Other details in the crash report pointed to flash being the culprit.

EDIT: just some seemingly relevant snippets from the ubuntu crash report:

"executablepath
/opt/firefox/plugin-container

ProcCmdline
/opt/firefox/plugin-container
/user/lib/adobe-flashplugin/libflashplayer.so -greomni
/opt/firefox/omni.ja -appomni
/opt/firefox/browser/omin.ja -appdir
/opt/firefox/browser 2690 true plugin"




Thanks,

Gary

---

### Post by monkeybrain20122 on 2017-07-15
> **gazzawazza said:**
> Thanks.

From my research about installing linux software, speaking generally, i thought deb files are more complete and tidy and it's just fortunate that the firefox tar.bz2 is precompiled. There's no guarantee that tar.bz2 files are compiled. Have I got that right?



A tar.bz2 is just an archive, like a .zip file. Basically it can be anything. Some software has source codes in the archive that need to be compiled, some like Firefox puts a binary there which is ready to run without installation. Some may put an installer which you need to run to install the software. What is in the tar.bz2 depends on the provider of the tar file rather than the file format. 

A .deb file is not always preferred. It is tightly integrated with the system so if everything is in step then it save you disk space by using shared libraries and might work more smoothly. but in your case your requirement is out of sync with the rest of the system. Instead of tweaking source lists and pinning Firefox  to accommodate inconsistent requirements you may as well run a standalone version of FF cleanly separated from the system.

Edited: What do you need flash for? Most video sites now use html5. For many video sites you can use the mpv addon and bypass flash altogether
[https://addons.mozilla.org/en-GB/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-GB/firefox/addon/watch-with-mpv/)

---

### Post by &amp;KyT$0P# on 2017-07-15
> **gazzawazza said:**
> The adobe-flashplugin installed the old version of flash (looks like it might have been for ubuntu 15.10, going on the filenames).
It *is* for Ubuntu 15.10, not 16.04.  The correct version for 16.04 is 20170711.1-0ubuntu0.16.04.1

You may be facing a much bigger problem than Flash crashing your browser.  I've never dealt with this sort of situation myself, but I'd start with running this command in Terminal -
```
grep -i -P -v -r '^#|xenial|^$' /etc/apt/sources*
```
If it outputs anything, please post its output here.

---

### Post by gazzawazza on 2017-07-15
> **monkeybrain20122 said:**
> A tar.bz2 is just an archive, like a .zip file. Basically it can be anything. Some software has source codes in the archive that need to be compiled, some like Firefox puts a binary there which is ready to run without installation. Some may put an installer which you need to run to install the software. What is in the tar.bz2 depends on the provider of the tar file rather than the file format. 

A .deb file is not always preferred. It is tightly integrated with the system so if everything is in step then it save you disk space by using shared libraries and might work more smoothly. but in your case your requirement is out of sync with the rest of the system. Instead of tweaking source lists and pinning Firefox  to accommodate inconsistent requirements you may as well run a standalone version of FF cleanly separated from the system.

Edited: What do you need flash for? Most video sites now use html5. For many video sites you can use the mpv addon and bypass flash altogether
[https://addons.mozilla.org/en-GB/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-GB/firefox/addon/watch-with-mpv/)

Thanks monkey :)

I was randomly looking at bz2 format last night - do appreciate it's a compressed file. Had previously just been trying to establish what file formats were associated with the most fire-and-forget approach to installation. Tar could result in different scenarios and i thought deb seemed more 'complete'.

thanks for MPV tip - i tried it on youtube but couldn't seemingly get MPV extension to playback (i've got it installed on lubuntu as well as firefox). Agreed - thankfully flash has decent alternatives now.

Regarding installations, is there an equivalent to .msi then?

Also, what's the best practice for storing programs? I think you suggested just bunging firefox into my home directory. I've found a good few references to installing to /opt. What should i do and when?



Thanks,

Gary

---

### Post by gazzawazza on 2017-07-15
> **halogen2 said:**
> It *is* for Ubuntu 15.10, not 16.04.  The correct version for 16.04 is 20170711.1-0ubuntu0.16.04.1

You may be facing a much bigger problem than Flash crashing your browser.  I've never dealt with this sort of situation myself, but I'd start with running this command in Terminal -
```
grep -i -P -v -r '^#|xenial|^$' /etc/apt/sources*
```
If it outputs anything, please post its output here.

oh dear that sounds ominous :(

```
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu wily partner
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily main restricted
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-updates main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-updates main restricted
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily universe
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily universe
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-updates universe
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-updates universe
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily multiverse
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-updates multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-updates multiverse
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-security main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-security main restricted
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-security universe
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-security universe
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-security multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-security multiverse
```

EDIT: so if I understand your terminal command, it's looking for anything which doesn't match Xenial? The output seems to indicate a shedload of repository paths for wily werewolf, when presumably we want it to read xenial?

---

### Post by &amp;KyT$0P# on 2017-07-15
> **gazzawazza said:**
> Also, what's the best practice for storing programs? I think you suggested just bunging firefox into my home directory. I've found a good few references to installing to /opt. What should i do and when?
There are several different kinds of software tarballs, and the answer is not the same in every case.

For tarballs such as Firefox, your home directory is simpler if you only need the software in that specific user account.  If you need it system-wide, best practice is to put it in its own subfolder of [FONT=Courier New]/opt[/FONT].

> **gazzawazza said:**
> oh dear that sounds ominous :(

```
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu wily partner
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily main restricted
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-updates main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-updates main restricted
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily universe
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily universe
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-updates universe
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-updates universe
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily multiverse
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-updates multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-updates multiverse
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-security main restricted
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-security main restricted
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-security universe
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-security universe
/etc/apt/sources.list.distUpgrade:deb http://gb.archive.ubuntu.com/ubuntu/ wily-security multiverse
/etc/apt/sources.list.distUpgrade:deb-src http://gb.archive.ubuntu.com/ubuntu/ wily-security multiverse
```

EDIT: so if I understand your terminal command, it's looking for anything which doesn't match Xenial? The output seems to indicate a shedload of repository paths for wily werewolf, when presumably we want it to read xenial?
The command prints out any uncommented, non-blank lines not containing "xenial" in the software sources.  i.e. all enabled software sources that may not be intended for 16.04.

Your "Canonical Partners" line in [FONT=Courier New]sources.list[/FONT] is supposed to be
```
deb http://archive.canonical.com/ubuntu xenial partner
```

Not sure what [FONT=Courier New]sources.list.distUpgrade[/FONT] is, so I'm not sure what to suggest from here, sorry.

---

### Post by monkeybrain20122 on 2017-07-15
> **gazzawazza said:**
> Thanks monkey :)


thanks for MPV tip - i tried it on youtube but couldn't seemingly get MPV extension to playback (i've got it installed on lubuntu as well as firefox). Agreed - thankfully flash has decent alternatives now.



The mpv addon does work. But you have to install mpv first of course. You can install an up to date version of mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)
Then you will need youtube-dl, I can't give more info about that because of forum rules. You can pm me if you wish.


> Regarding installations, is there an equivalent to .msi then?

Also, what's the best practice for storing programs? I think you suggested just bunging firefox into my home directory. I've found a good few references to installing to /opt. What should i do and when?

I don't know about .msi. In Linux programs come in several formats. A .deb is an installer for debian based system, a .rpm is the equivalent for Redhat based system and Susi, then there are generic install scripts you run in the terminal. Then there are precompiled binaries which you don't need to install, just extract and click the binary and it will work, e.g Firefox, blender. finally there are source codes that you need to compile. These are the more common formats, then there are other newer ones, like an appimage is something that in self contained, you just download it and click, no need for installation (e.g Kitra provides an appimage for linux), docker images and snap images..

Installing a .deb is more integrated with the system as it uses shared components and dependencies. But it is not "more complete", in fact quite the opposite, a package with pre-compiled binaries or appimages are self contained.

You don't need to put firefox in /opt if you are the only user. I would just put it in your home (/home/yourusername)

---

### Post by gazzawazza on 2017-07-17
> **halogen2 said:**
> There are several different kinds of software tarballs, and the answer is not the same in every case.

For tarballs such as Firefox, your home directory is simpler if you only need the software in that specific user account.  If you need it system-wide, best practice is to put it in its own subfolder of [FONT=Courier New]/opt[/FONT].


The command prints out any uncommented, non-blank lines not containing "xenial" in the software sources.  i.e. all enabled software sources that may not be intended for 16.04.

Your "Canonical Partners" line in [FONT=Courier New]sources.list[/FONT] is supposed to be
```
deb http://archive.canonical.com/ubuntu xenial partner
```

Not sure what [FONT=Courier New]sources.list.distUpgrade[/FONT] is, so I'm not sure what to suggest from here, sorry.

thanks mate

I was actually a little ahead of you here and had a look at my sources.list

To my uneducated eye, it looks 'clean'.

I'd guess that a new sources.list was created during a system upgrade (i.e. the sources.list.distupgrade is a backup of an old .list).

Will post what's in the folder and what my sources.list looks like when i can goto my linux box.

This doesn't explain of course why I'm getting 15.10 flash files. Any idea at all?



Thanks,

Gaz

---

### Post by gazzawazza on 2017-07-17
> **monkeybrain20122 said:**
> The mpv addon does work. But you have to install mpv first of course. You can install an up to date version of mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)
Then you will need youtube-dl, I can't give more info about that because of forum rules. You can pm me if you wish.




I don't know about .msi. In Linux programs come in several formats. A .deb is an installer for debian based system, a .rpm is the equivalent for Redhat based system and Susi, then there are generic install scripts you run in the terminal. Then there are precompiled binaries which you don't need to install, just extract and click the binary and it will work, e.g Firefox, blender. finally there are source codes that you need to compile. These are the more common formats, then there are other newer ones, like an appimage is something that in self contained, you just download it and click, no need for installation (e.g Kitra provides an appimage for linux), docker images and snap images..

Installing a .deb is more integrated with the system as it uses shared components and dependencies. But it is not "more complete", in fact quite the opposite, a package with pre-compiled binaries or appimages are self contained.

You don't need to put firefox in /opt if you are the only user. I would just put it in your home (/home/yourusername)


thanks man.

I did install MPV first. I got as far as youtube-dl.org but didn't 'complete' that step. From what I can see is, videos basically get saved/cached locally and then get played through MPV (presumably either in the main player or through the firefox extension. Apologies to the mods if I'm saying stuff I shouldn't here.

Re: installers. Thanks. That makes much more sense. Really useful info. I'm puzzled by your MSI comment though - are you just saying you're not sure about how it works technically or you've never heard of it (can't believe that tbh)?



Cheers,

Gaz

---

### Post by &amp;KyT$0P# on 2017-07-17
> **gazzawazza said:**
> This doesn't explain of course why I'm getting 15.10 flash files. Any idea at all?
More than just an idea -
> **halogen2 said:**
> Your "Canonical Partners" line in [FONT=Courier New]sources.list[/FONT] is supposed to be
```
deb http://archive.canonical.com/ubuntu **[COLOR="#FF0000"]xenial[/COLOR]** partner
```
... but you have -
```
deb http://archive.canonical.com/ubuntu **[COLOR="#FF0000"]wily[/COLOR]** partner
```
... and "wily" = 15.10... so...you connect the dots. :)

Since the rest of your [FONT=Courier New]sources.list[/FONT] looks clean to you, you might try just changing "wily" to "xenial" in that line.  If I remember right, Lubuntu uses Leafpad as the text editor.  So, to edit [FONT=Courier New]sources.list[/FONT], run this command in Terminal -
```
sudo -H leafpad /etc/apt/sources.list
```

Once you've made the change, run [FONT=Courier New]sudo apt-get update[/FONT] to apply it.

---

### Post by gazzawazza on 2017-07-23
> **halogen2 said:**
> More than just an idea -

... but you have -
```
deb http://archive.canonical.com/ubuntu **[COLOR=#FF0000]wily[/COLOR]** partner
```
... and "wily" = 15.10... so...you connect the dots. :)

Since the rest of your [FONT=Courier New]sources.list[/FONT] looks clean to you, you might try just changing "wily" to "xenial" in that line.  If I remember right, Lubuntu uses Leafpad as the text editor.  So, to edit [FONT=Courier New]sources.list[/FONT], run this command in Terminal -
```
sudo -H leafpad /etc/apt/sources.list
```

Once you've made the change, run [FONT=Courier New]sudo apt-get update[/FONT] to apply it.

hi halogen

sorry for the delay. life got in the way (along with Raspberry Pi 3 and pi-hole) :)

this is what my sources.list folder looks like:

[IMG]http://storage2.static.itmages.com/i/17/0724/h_1500861774_9261718_d64da5e4f1.png[/IMG]

and this is what my sources.list contains:
```

# deb cdrom:[Lubuntu 15.10 _Wily Werewolf_ - Release i386 (20151021)]/ wily main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial universe
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu wily partner
# deb-src http://archive.canonical.com/ubuntu wily partner

```

I managed to modify sources.list (so last two lines of above code now contain xenial not wily) and the adobe-flashplugin is now 20170711 :)

I'll post this before FF crashes :D

EDIT: and yes the reasonably current adobe-flashplugin (20170711) crashes FF, so flash stayed on my system for about 2 mins :)


Cheers,

Gaz

---

