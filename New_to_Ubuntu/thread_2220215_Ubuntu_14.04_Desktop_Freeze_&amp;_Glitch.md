---
title: "Ubuntu 14.04 Desktop Freeze &amp; Glitch"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by Delyo_Dobrev on 2014-04-27
So, here's my problem.
I have already used Ubuntu, 13.O4 or something like this, but it [COLOR=#ff8c00]freezed sometimes[/COLOR], and I uninstalled it. Now I want to try Ubuntu [COLOR=#0000ff]14.04[/COLOR].
I installed it with dual boot, the Live DVD works just fine, [COLOR=#ff8c00]except for the slow loading in the install process[/COLOR].
But when I boot it, the screen gets [COLOR=#008000]dark for ten seconds[/COLOR] and then shows the desktop, and after a few seconds, [COLOR=#ff0000]the screen freezes, and glitches[/COLOR] (it draws squared diagonal lines with the background's color)
I checked the required specs, i have 6GB DDR3, AMD Athlon II Dual Core 2.7 GHz Processor, but the video card [COLOR=#ff0000]might[/COLOR] be the problem. It's and NVIDIA GeForce 6150SE NForce 430 with 256MB Memory (I honestly see no "force" in it :D). If I'm right, it' just enough ram.
I can't find the same problem anywhere!
Could it be the Graphics card's driver, its memory, or something else, Unity?
Please help, I'm desperate.
Thanks in advance.

---

### Post by bdog840 on 2014-10-15
Greetings,
I have the same problem [**[COLOR=#000000]Delyo_Dobrev[/COLOR]**]("http://ubuntuforums.org/member.php?u=1920058") posted;

I installed Zorin OS 9 Lite on most of my computers.  I'm pulling my hair out trying to troubleshoot an eMachines I got from a computer lot.  This Emachines Desktop PC also has the same specs; which has 6GB DDR3, AMD Athlon II Dual Core 2.7 GHz Processor.  I am thinking the video card or chip set [COLOR=#000000]might[/COLOR] be the problem which it has NVIDIA on-board video.  First I ran memtest that passed and it crashed at the boot screen of Zorin.  Then I thought it was the ram so I started to pull out each stick and left in 1 GB of memory.  After that it started up Zorin successfully and I was at the desktop.  When I clicked on Firefox I got the diagonal blocks of lines and the system froze. What puzzles me other times Zorin would be fine but it would only freeze when Firefox is launched.  I don't know if it's a video graphics issue or ram.  All of the ram sticks are good because it passed running memtest.

Update:  Virtual Machine needs to be disabled in Bios.  I did get Firefox to open but crashed shortly after. From bench testing two computers that have the Nivida video chipset 6600 or above there is an unknown bug that will cause a system lock.  This could also effect ram issues.  Both Dells towers I have put Zorin on seem to be stable which has Intel video chipsets.

---

