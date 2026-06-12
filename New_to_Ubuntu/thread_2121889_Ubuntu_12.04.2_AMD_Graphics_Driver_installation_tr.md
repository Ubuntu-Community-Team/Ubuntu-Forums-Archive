---
title: "Ubuntu 12.04.2 AMD Graphics Driver installation troubles"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by emugod on 2013-03-03
I have installed Ubuntu 12.04 to my Lenovo G585 laptop; this laptop has an AMD Radeon 6310 graphics card. After downloading and installing over 300MB of stuff, including the 'restricted' AMD driver, Ubuntu could no longer boot. I resolved this by managing to enter the terminal-only mode and disabling the new driver through jockey-text. My goal is to get a proper driver installed so that I can play TF2, and I have a few options at this juncture which I would appreciate input on;

Firstly is OldFreds suggestion from the previous thread that I need to try installing the headers - I will definitely do this, and then reinstall the jockey-recommended driver, because there is no apparent risk in it. [COLOR=#000000]My only question before I go and do it is, [/COLOR][COLOR=#000000]does jockey always redownload the driver, or not? This will be the third time I have told it to download+install the same driver, and there was a potential that I had created a corrupt version by forcing Jockey to terminate the first time. I don't want to just keep reinstalling the same corrupt version, I want to force it to redownload (if it isn't already).[/COLOR]

Then, if that does not work, is [http://steamcommunity.com/app/221410...scn=1361421411]("http://steamcommunity.com/app/221410/discussions/4/864960353822274949/?tscn=1361421411"). [COLOR=#000000]Before I do that, though, I want to make sure that, in the event of failure, this driver will be available to deactivation through the jockey-text program? Otherwise how would I disable it and return to basic driver? Or should I just try the 'experimental' driver, first, before leaving the realm of 'jockey'? Is there any good chance of it working where the 'update' version seemed not to?[/COLOR]

You can see the previous thread if you want more detailed info, but it shouldn't be necessary.
[http://ubuntuforums.org/showthread.php?t=2121279](http://ubuntuforums.org/showthread.php?t=2121279)

A very side question: currently I am entering terminal-only mode by booting to the 'recovery mode' on the grub2 menu, selecting the terminal option, and then ordering a shut down. This last step troubles me somewhat, but works and seems to be essential? Without it I cannot login and the jockey-text gives strange complaints/warnings, does not function properly. I am thinking the 'recovery mode' terminal is not a true terminal? But it is still strange to me that I order a 'shut down' in order to actually start the machine proper. I discovered this by accident.

---

### Post by emugod on 2013-03-03
> **oldfred said:**
> 
Do this before installing any video drivers, if you have headers it will just say so.
       # You may need headers first - meta package :
sudo apt-get install linux-headers-generic


I am back on linux and just tried this recommendation from the previous thread. Below is the response;
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1 dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
This does not look promising, in terms of being a likely solution to my problem. Three packages, but no headers? I must admit I am not sure of the distinction. Anyone who can tell me if it is worth trying the jockey installed driver again (and confirm it will not be using the same old potentially-corrupt download)?

---

### Post by emugod on 2013-03-03
Well, i very stupidly went ahead with it (activating the 'prototype' restricted driver), and the results were just next to the worst possible. I'm in Windows8 again now, because Ubuntu will not boot and I have no means to deactivate the bad driver, this time. I can't believe i did this very stupid thing; when returning to Ubuntu the last time (before making the previous post) I had noticed the grub2 display had returned to the illegible distorted version (scrunched into the top 500 or so lines of the screen and repeated horizontally, maybe with some overlap as well). I have no idea what caused this, but it barely registered because it was just on grub and the menu worked well enough to see whch option (counting from the top) was selected and hit enter (or i could have just done nothing and it would have gone through automatically).

I can't think of anything to do now but keep retrying and maybe I will get lucky with a legible display (it did seem to be an intermittent problem, at least before, and I have only tried twice now)? Is there any way to use my LiveUSB to get into my installed copy, or could another go of boot-repair possibly help in any way?

[COLOR=#dda0dd][SIZE=1]I saved the worst for last; for some reason at some point in this (i was kind of groping blindly in the 'restore' mode/option while trying to find the 'drop to terminal' option, and so may have only myself to blame) the laptops screen was set to (what I very much hope is) the lowest possible brightness. And due to a long-standing (since last month when I updated catalyst control center) problem in windows, I can't change it (when it was initially disabled it was at a fairly bright setting, which was often very annoying but ultimately always functional). It is just barely functional at normal room brightness, and pretty ok with a blanket stretched between me and the screen, but definitely a problem to fix asap! And I think getting back into Linux may actually be my only chance of that, barring the release of a fixed catalyst control center (the next thing i check). [/SIZE][/COLOR][SIZE=1][SIZE=2]- Nevermind, restored adjustable brightness by rolling back the driver, which is what I should have done in the first place (iirc there was some game I was playing at the time that preferred the newer, but since I don't even remember which game it was...). Why don't any forums seem to have strike-through anymore?[/SIZE][/SIZE]

edit:
tried booting a bunch more times (on both options), i think i can confirm it's no longer just intermittent. also that the distorting actually IS tearing (whereas i had though it was compression), so next i am going to check out the link oldfred provided last thread, about graphics tearing. it really is impossible in this form, i managed to navigate to what i am pretty sure was the terminal, but could not get any further. there is definitely no way i would be able to read the alphanumeric of the driver from jockey-text -l.

---

### Post by emugod on 2013-03-03
Should I make a new thread with more accurate/descriptive title, and more concise explanation of the problem? I don't want to spam.

My problem at present is this: bad graphics driver preventing boot to gui, and intense graphical distortion of grub2/terminal screens (which I do not believe to be caused by the graphics driver at all) preventing disabling of the bad driver.

---

