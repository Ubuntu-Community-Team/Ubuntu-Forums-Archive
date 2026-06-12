---
title: "Chromium and Adobe Flash giving me fits."
date: 2012-09-14
forum: New to Ubuntu
---

### Post by zuren on 2012-09-14
I found a lot of threads covering Adobe Flash but nothing has solved my issue.

I tried viewing Youtube with Chromium and got the error that Adobe Flash was not installed.  So I installed Flash as suggested via Synaptic Package Manager.  I go back to Youtube and I get a "Missing Plug-in" message where the video should be.

I have tried many iterations of what I can try:

- removed Flash and reinstalled
- ran updates
- reinstalled Chromium
- installed Firefox
- rebooted several times

I have tried everything above in different orders.  Flash will not work in either browser.

My only other thought is something got corrupted and I should reinstall Lubuntu, followed immediately by Flash.  Any thoughts?

Thanks!

---

### Post by dniMretsaM on 2012-09-14
For Firefox, you can use [Flasd-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/?src=ss") to install the correct version of Flash. What package are you installing through Synaptic?

EDIT: Found [this tutorial](http://linuxologist.com/01general/howto-chromium-browser-on-linux-with-flash/) via a quick search. Take a look at the section titled "Getting Flash To Work." I haven't tested it myself, though, as I don't use Chromium.

---

### Post by skabople on 2012-09-14
Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. They will continue to provide security backports.

Reference:
[http://get.adobe.com/flashplayer/?promoid=JZEFT](http://get.adobe.com/flashplayer/?promoid=JZEFT)

Regards

---

### Post by alphacrucis2 on 2012-09-14
> **skabople said:**
> Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. They will continue to provide security backports.

Reference:
[http://get.adobe.com/flashplayer/?promoid=JZEFT](http://get.adobe.com/flashplayer/?promoid=JZEFT)

Regards

That's not the case for chrome. Google will support more recent versions via the pepper api. 

[http://www.geek.com/articles/news/chrome-20-brings-64-bit-flash-with-a-dash-of-pepper-to-linux-20120628/](http://www.geek.com/articles/news/chrome-20-brings-64-bit-flash-with-a-dash-of-pepper-to-linux-20120628/)

---

### Post by dniMretsaM on 2012-09-14
> **alphacrucis2 said:**
> That's not the case for chrome. Google will support more recent versions via the pepper api. 

[http://www.geek.com/articles/news/chrome-20-brings-64-bit-flash-with-a-dash-of-pepper-to-linux-20120628/](http://www.geek.com/articles/news/chrome-20-brings-64-bit-flash-with-a-dash-of-pepper-to-linux-20120628/)

Chromium != Chrome.

---

### Post by alphacrucis2 on 2012-09-14
> **dniMretsaM said:**
> Chromium != Chrome.

Who said it was?

---

### Post by dniMretsaM on 2012-09-14
> **alphacrucis2 said:**
> Who said it was?

I read your post as you saying that, since the OP was using Chrome, he would have a newer version than 11.2. I was correcting that. If that's not what you meant, I apologize for misinterpreting.

---

### Post by zuren on 2012-09-15
UPDATE:

Thanks for those links.

Last night I reinstalled Lubuntu from scratch, ran the Update Manager, installed Firefox, installed Flash-Aid.  i did nothing else that could conflict and still no video.  I'm beginning to wonder if this system doesn't have the horsepower to play video well... 

System:
Dell Dimension L866r
P3 866MHz processor
512MB RAM (max)
ATI Radeon 7500 PCI video card
Lubuntu 12.04

If you see anything glaring, please let me know.  I'll look through the links posted.

Thanks!

---

### Post by critin on 2012-09-15
Does lubuntu have the 'extras' packages like ubuntu?  Does it contain flash?

(I don't use it so don't know, but  I thought they all did.)

---

### Post by kalehrl on 2012-09-15
Open Synaptic and install flashplugin-installer.

---

### Post by dniMretsaM on 2012-09-15
> **critin said:**
> Does lubuntu have the 'extras' packages like ubuntu?  Does it contain flash?

(I don't use it so don't know, but  I thought they all did.)

It does. It can be installed with:
```
sudo apt-get install lubuntu-restricted-extras
```.

OP, install that and then see if the file [FONT=Courier New]/usr/lib/flashplugin-installer/flashplugin.so [/FONT]exists.

---

### Post by zuren on 2012-09-16
> **dniMretsaM said:**
> It does. It can be installed with:
```
sudo apt-get install lubuntu-restricted-extras
```.

OP, install that and then see if the file [FONT=Courier New]/usr/lib/flashplugin-installer/flashplugin.so [/FONT]exists.

I did as instructed.  When I navigate to /usr/lib/flashplugin-installer/ there are 2 files:

- install_plugin (shell script)
- libflashplayer.so (shared library)

Flashplugin.so does not appear to exist.

Thanks!

---

### Post by critin on 2012-09-16
Have you seen this?  Looks like exactly what you need.

[http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html](http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html)

---

### Post by zuren on 2012-09-16
> **critin said:**
> Have you seen this?  Looks like exactly what you need.

[http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html](http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html)

No, I had not seen this and had high hopes for it.  I followed everything to the letter except when I entered this command in step 2:

```
chromium-browser --ppapi-flash-path=/opt/google/chrome/PepperFlash/libpepflashplayer.so --ppapi-flash-version=11.3.31.323
```

...nothing happens in the terminal.  The cursor simply dropped down a line.  I went on to check the plugin version and Chromium is still seeing 11.2 r202.  

Flash is not working in 3 browsers now; Chromium, Chrome and Firefox all give me the "Missing Plug-In" message.  I get a message bar at the top stating "Could not load Shockwave Flash" in Chrome.  Chromium and Firefox is nothing but the "missing plug-in" message where the video should be.

Thanks!

---

### Post by critin on 2012-09-16
I'm sure you opened Add-Ons in firefox and updated Shockwave flash there and made sure it wasn't disabled.  Sometimes the browser will disable mine if it isn't up to date, and I don't know it until youtube fails.

Looks like you've tried everything.

I'm using FF 15.01 with working flash.

---

### Post by critin on 2012-09-16
>  I went on to check the plugin version and Chromium is still seeing 11.2 r202.  

My FF is also running this version.

---

### Post by critin on 2012-09-16
>  So I installed Flash as suggested via Synaptic Package ManagerI always install Flash through the regular adobe update that pops up while on youtube.

edit to add one more link:

[http://www.muktware.com/3778/chrome-20-google-takes-over-adobe-flash-linux-development](http://www.muktware.com/3778/chrome-20-google-takes-over-adobe-flash-linux-development)

Since the last version of Adobe Flash, 11. will be maintained for 5 years, can't you use it?  You may have to install your previous version of browser, but it should work if you let adobe update it.

From what I'm reading, a lot of people are having issues with Pepper.

---

### Post by zuren on 2012-09-16
> **critin said:**
> I'm sure you opened Add-Ons in firefox and updated Shockwave flash there and made sure it wasn't disabled.  Sometimes the browser will disable mine if it isn't up to date, and I don't know it until youtube fails.

Looks like you've tried everything.

I'm using FF 15.01 with working flash.

I went into the Add-Ons and everything seems to updated and in order.

Here is something interesting I just found:

> Adobe Flash 11 system requirements -    
[LIST]
[*]2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
[*]Red Hat® Enterprise Linux® (RHEL) 5.6 or later (32 bit  and 64 bit), openSUSE® 11.3 or later (32 bit and 64 bit), or Ubuntu  10.04 or later (32 bit and 64 bit)
[*]Mozilla Firefox 4.0 or Google Chrome
[*]512MB of RAM; 128MB of graphics memory
[/LIST]
          Note: Flash Player 11.2 is the last supported Flash Player version for Linux. Adobe will continue provide security updates.



[http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)


I posted my system but here it is again- 

- [COLOR=Red]866MHz processor[/COLOR]
- Lubuntu 12.04
- Firefox 15.x
- 512MB of RAM; [COLOR=Red]64MB graphics memory[/COLOR]

My processor is too slow and have too little graphics memory according the required specs.  If Flash isn't seeing the correct hardware, would it cause it to not install correctly?

I found an add on for Firefox called "Low Quality Flash 0.2" that supposedly helps older systems.  The "missing plug-in" message is gone but still no video.  I wonder if I need an older version of Flash due to my hardware?

Thanks

---

### Post by dniMretsaM on 2012-09-16
> **zuren said:**
> I did as instructed.  When I navigate to /usr/lib/flashplugin-installer/ there are 2 files:

- install_plugin (shell script)
- libflashplayer.so (shared library)

Flashplugin.so does not appear to exist.

Thanks!

That's correct (I forgot the "[FONT=Courier New]lib[/FONT]"). So Flash IS installed on you're system. The problem is that it's not working.  Open about[NOPARSE]:p[/NOPARSE]lugins in Firefox and see if Shockwave Flash is there.

---

### Post by zuren on 2012-09-16
> **dniMretsaM said:**
> That's correct (I forgot the "[FONT=Courier New]lib[/FONT]"). So Flash IS installed on you're system. The problem is that it's not working.  Open about[NOPARSE]:p[/NOPARSE]lugins in Firefox and see if Shockwave Flash is there.

Installed a screenshot tool to help with all of this.  Looks like Shockwave is there.  Let me know if there are any other screenshots I can take to be helpful.

---

### Post by dniMretsaM on 2012-09-16
> **zuren said:**
> Installed a screenshot tool to help with all of this.  Looks like Shockwave is there.  Let me know if there are any other screenshots I can take to be helpful.

OK, so Firefox sees it, but it apparently isn't working. Maybe your system isn't powerful enough. Try another site than YouTube. Also try a YT video in HTML5 and see if it plays.

---

### Post by critin on 2012-09-16
I went to FF add on's and did a search for Flash.  There are a few, 1 for Low Quality Flash 0.2 for low spec hardware, and Flash Aid 2.2.3.

---

### Post by TenPlus1 on 2012-09-16
> **zuren said:**
> No, I had not seen this and had high hopes for it.  I followed everything to the letter except when I entered this command in step 2:

```
chromium-browser --ppapi-flash-path=/opt/google/chrome/PepperFlash/libpepflashplayer.so --ppapi-flash-version=11.3.31.323
```

...nothing happens in the terminal.  The cursor simply dropped down a line.  I went on to check the plugin version and Chromium is still seeing 11.2 r202.  

Flash is not working in 3 browsers now; Chromium, Chrome and Firefox all give me the "Missing Plug-In" message.  I get a message bar at the top stating "Could not load Shockwave Flash" in Chrome.  Chromium and Firefox is nothing but the "missing plug-in" message where the video should be.

Thanks!

Did you go into chrome://plugins and disable Flash Player 11.2 so it only uses PepperFlash 11.3 ?!?!?!

---

### Post by redsand on 2012-09-16
I'm disappointed to see yet someone else having problems with this flash thing. I've been having the exact same issues with two graphic cards now.  One a Radeon 9200 AGP and also an older Nvidia G-force.  Make me wonder if there's something else we're not seeing here. I've tried everything zuren has with like results.

RS

---

### Post by dniMretsaM on 2012-09-16
> **redsand said:**
> I'm disappointed to see yet someone else having problems with this flash thing. I've been having the exact same issues with two graphic cards now.  One a Radeon 9200 AGP and also an older Nvidia G-force.  Make me wonder if there's something else we're not seeing here. I've tried everything zuren has with like results.

RS

It's probably a software problem.  It's not likely that any software is messing it up. And only Adobe can fix those issues, since Flash is proprietary (they won't fix them, of course, because they're only doing security updates for GNU/Linux). Just another danger of non-free software, I guess. You guys can always try things like GNASH and Lightspark. They will give you some support if they work on your hardware.

---

### Post by marinara on 2012-09-16
please try this, you should see an animation
[http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html)

---

### Post by zuren on 2012-09-16
> **marinara said:**
> please try this, you should see an animation
[http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html](http://helpx.adobe.com/flash-player/kb/find-version-flash-player.html)

I see no animation...

---

### Post by zuren on 2012-09-16
UPDATE:

**Partial Success!**

As per TenPlus1's comment, I checked if Flash was still installed and it was.  I completely uninstalled it with Synaptic Package Manager so there was no Flash on the computer.

I went back to the instructions found here:
[http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html](http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html)

As per step #2, I was able to get video working in Chromium with the terminal open and active.  I went to step #3 to make it permanent and this is where issues started again.  I changed the file, closed everything and tried to reopen to find that Chromium was now unresponsive; would not open at all.  I undid the steps in #3 and got Chromium back.

I opened Chrome and could view most of the videos at Youtube.  Some gave me an Adobe Flash error, others ran.  There did not seem to be a rhyme or reason to this.  So if Flash Player is not installed, Chrome should mostly work.    

Bottom line is that I have some Flash videos able to run in Chrome.  The instructions at the above website seemed to "break" my Chromium.  I have not attempted fixing Firefox yet.  Now that I have something working, I'm a little hesitant to try anything else that could undo my working solution.  I'm betting my ancient hardware lies at the root of what was causing me issues and my guess is that PepperFlash is a little more tolerant to my old, low-end specs.

If you are having Flash issues, try uninstalling Flash through Synaptic (remove completely) and install/use Chrome (if you don't already have it).  I can't explain why some video works and others do not, but it is better than nothing.  

Hope this helps!

---

### Post by firebug on 2012-09-17
I don't know if this helps but I had the same problem and resolved it by installing the adobe flash plugin for mozila from the software center(using a fresh install of 12.04) I do have firefox installed as well but do not use it.  After the plugin finished installing I just closed and reopened chromium and everything worked great.

---

### Post by TenPlus1 on 2012-09-17
I currently use Chromium 22.0 and have extracted the libpepeflashplayer.so file from google-chrome.deb file and placed it in /usr/lib/chromium-browser/

I have edited the file /etc/chromium-browser/default and changed the line to read:

CHROMIUM_FLAGS="--ppapi-flash-path=/usr/lib/chromium-browser/libpepflashplayer.so --ppapi-flash-version=11.3.31.103"

and saved, then run Chromium and tested flash on [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) to which it reports that all is well and flash 11.3 is working fine...  This is also confirmed when playing youtube movies in full screen hi-definition using hardware acceleration...

---

### Post by zuren on 2012-09-17
> **TenPlus1 said:**
> I currently use Chromium 22.0 and have extracted the libpepeflashplayer.so file from google-chrome.deb file and placed it in /usr/lib/chromium-browser/

I have edited the file /etc/chromium-browser/default and changed the line to read:

CHROMIUM_FLAGS="--ppapi-flash-path=/usr/lib/chromium-browser/libpepflashplayer.so --ppapi-flash-version=11.3.31.103"

and saved, then run Chromium and tested flash on [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) to which it reports that all is well and flash 11.3 is working fine...  This is also confirmed when playing youtube movies in full screen hi-definition using hardware acceleration...

How exactly does one extract the file to the new location?  I tried simply copy-n-pasting but Lubuntu didn't like that idea.  I would like to give this a try.  I'm not sure which version of Chromium I'm running; looks like 23 is the most recent.

Thanks!

---

### Post by zuren on 2012-09-17
I also wanted to add this to the discussion.  I'm playing with 2 desktops at the moment:

- Dell Dimension L866r (focus of this thread)
- Dell Dimension 4550

Both are running the same OS from the same install disk and have the same browsers loaded.  The Dimension L866r is having these issues while the Dimension 4550 runs Flash flawlessly.  The only thing I can point to is hardware.  Compared to the L866r, the Dimension 4550 is running a Pentium4 2.4Ghz, same amount of RAM, and an OEM Geforce4 MX AGP video card.

I can't do much about the processor in the L866r and the RAM is maxxed out, but would a better graphics card make a difference?

---

### Post by zuren on 2012-09-17
> **redsand said:**
> I'm disappointed to see yet someone else having problems with this flash thing. I've been having the exact same issues with two graphic cards now.  One a Radeon 9200 AGP and also an older Nvidia G-force.  Make me wonder if there's something else we're not seeing here. I've tried everything zuren has with like results.

RS

redsand - what are your system specs?  I'm wondering if a better graphics card is the answer but your experience would suggest otherwise.

---

### Post by zuren on 2012-09-18
UPDATE:

Lightspark and GNASH were suggested earlier in the thread so I decided to give those a try.  Lightspark didn't help but GNASH seems to be working in both Firefox and Chrome.  The playback seems to be better in Chrome than Firefox.  I notice that an older version of "flash" is what the browser sees, so I think the later versions (11.x) are looking for hardware that doesn't meet the minimum spec.  I do get messages to update but there is typically a button to "run this time".    

I think the old spec of the hardware is the primary limitation so I'm going to call this "good enough".  Give GNASH a try (its in Synaptic Package Manager) if you have an older machine that is having issues with Flash.

Thanks for the suggestions and links!

---

