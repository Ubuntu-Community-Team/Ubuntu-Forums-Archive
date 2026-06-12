---
title: "Random Reboots? Fsck, Lightmanager Corruption?"
date: 2016-03-19
forum: New to Ubuntu
---

### Post by whit2 on 2016-03-19
Hello,

First, I would like to say that although I am new to these forums, I have come to this site often to solve issues and more often than not find what I'm looking for. This is an amazing community and I hope someday I can become proficient enough to give back to it. I only have a few months of experience with command line and gedit workarounds, generally for superficial things like backwards compatibility and basic customization.  I've already messed up my display driver once trying to fix a bug and had to reinstall the OS (15.10), so since then I've been content not to dig any deeper.

But it seems I have to because this issue is persistently frustrating. Without warning, my screen shifts to a black BIOS/terminal-like screen with a few lines of code, then restarts to the login screen.  Things to note:

1) The transitions are almost instantaneous. The screen immediately shifts to this BlackSOD, lingers for five to ten seconds, then immediately boots to the login screen. It doesn't go through the usual restart process of bios, manufacturer loading screen, ubuntu loading screen, etc. I can login again almost immediately. But it is clearly a restart because all of my scheduled processes can be seen to start up again upon login, and all files that were open at the time have to be recovered.

2) I can't screenshot, and the screen doesn't stay around long enough for me to decipher what the issue is. The first line is always about fsck (which to my understanding
is a troubleshooting process; suggests something's wrong but doesn't say what that might be), then a couple lines about lightmanager and maybe other processes. In short, because of how brief these episodes are, I can't tell what the problem is, or how to record it for someone else to interpret it.

3) This seems to primarily happen during memory intensive things, but that is my speculation. It most frequently happens when I skip around in VLC media player, but also has happened while doing things in LibreCalc, Audacity, and GIMP, as well as after I login and scheduled processes start up. It has never happened while web browsing or streaming though. The latter instance sometimes happens in a continuous loop, where I login, a couple processes start and are interrupted by BSOD, reload to login screen, repeat.

4) The code itself is usually only a few lines long, maybe two lines below the initial fsck message. The only time I've seen a significant change is with VLC media player, which sometimes has a long list of 20 or so similar lines. The beginning is still the same: fsck blah blah.

So, in summary, I would like to know how best to troubleshoot this problem. This seems to be a memory or display issue and I have no familiarity with either. I can't find any prior posts that address this issue, but if I missed them I would appreciate being steered in the right direction.

Thanks for the help,

Whit

---

