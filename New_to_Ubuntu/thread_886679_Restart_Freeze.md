---
title: "Restart Freeze"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Pssst on 2008-08-11
Hello

I need to occasionally switch between one and two monitors. To do this I created two new xorg.conf and added an alias to overwrite whichever I needed to use, then restart gdm.

The problem is, sometimes (not always) when I restart gdm 
(sudo gdm restart), I get a freeze after "running local boot scripts (/etc/rc.local)   [ok]".

I use the 8.04 dist if that helps.

Anyone familiar with this problem?

---

### Post by ggaaron on 2008-08-11
Modern Xorg doesn't need xorg.conf configuration and in fact works better without it. Have you tried using xrandr? This is the default new tool for plugging new monitors and it doesn't need xserver restart.

---

### Post by Pssst on 2008-08-12
Thanks for the xrandr tip, it turned out quite useful =). 
It doesn't find my other screen, but I assume that's just because I haven't rewritten my xorg.conf properly, or what do you mean by not needing configuration? Should I remove the conf all together?

The original problem still remains though, when I restart gdm it freezes after "running local boot scripts"

---

### Post by ggaaron on 2008-08-12
Xorg uses now hal and even ignores some parts of xorg.conf. You don't have to remove it, but by default ubuntu has very limited xorg.conf (without anything specific to your hardware in it) and lets hal to find your hardware. Xrandr doesn't need any xorg.conf configuration, check in google if your graphic card drivers support xrandr. This is not a solution but a workaround - xrandr doesn't need gdm to be restarted.

Back to your problem - how do you restart gdm? 'running local boot scripts' should be somewhere on the top of boot sequence and gdm on the bottom, having nothing in common with boot scripts... How do you restart gdm, have you tried 'sudo /etc/init.d/gdm restart' from console?

---

### Post by Pssst on 2008-08-12
Hmmm, I realise that the xrandr thing might be appropriate to put in another thread.

I restart gdm exactly as you describe it, "sudo /etc/init.d/gdm restart"

---

### Post by ggaaron on 2008-08-12
Can you post all messages that come after this command?

---

### Post by Pssst on 2008-08-12
* Starting anachronistic cron anacron                                   [OK]
* Starting deterred execution scheduler aid                             [OK]
* Starting periodic command scheduler crond                             [OK]
* Enabling additional executable binary formats binfmt-support          [OK]
* Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName                                    [OK]

* Checking battery state...                                             [OK]
* Running local boot scripts (/etc/rc.local)                            [OK]


that's it

---

### Post by ggaaron on 2008-08-12
Do you run restart command from text console (ctrl+alt+F1 for example) or from X terminal? Because restarting gdm should not restart cron or apache for example. It seems to me as if you are restarting it from X and get back to console when X is killed and see logs of your boot, but not logs of actual X restart.

---

### Post by Pssst on 2008-08-12
Ah, that's what I've been looking at!
After doing some testing I've concluded that running the gdm script with restart does not start up a new gdm in my case.

---

### Post by ggaaron on 2008-08-12
Have you tried looking if something hangs and takes all cpu? In top for example. You can also find out if gdm is running by ps -e | grep gdm and kill all of it before restart with killall -9 gdm. I find GNOME quite unstable and I've experienced similar problems myself, but for me it has shown me that it was not gdm, but gnome-panel hanging...

---

### Post by Pssst on 2008-08-12
Nope, gdm is not running after the restart. Can it have something to do with me restarting from within the X terminal?

---

### Post by ggaaron on 2008-08-12
It shouldn't have. You can try to restart it from real console.

---

### Post by Pssst on 2008-08-12
There seems to be a difference, when restarting from within a X terminal, it just sends me back to the terminal I was running it from in the first place, no gdm processes running.
When running restart from a "real" terminal, everything works fine.

---

### Post by ggaaron on 2008-08-12
So everything you wanted works?

It can be a problematic issue - running a command from a terminal what will be killed before this command is done=)

---

### Post by Pssst on 2008-08-12
Hmmm, what i mean is, if i crtl+alt+f1 (or another number) to another session, the gdm restart works fine. If I run from the X session, it seems to just execute the stop command.
Do bash run within X? So terminating X would terminate the bash shell currently running?

---

### Post by ggaaron on 2008-08-12
X kills all graphical programs, including your terminal and terminal kills bash inside. You can try with screen. Just run screen in terminal - it's a GNU terminal multiplexer but the feature we want now is that it isn't easily killed=) Terminal close won't kill screen - just deattach it. To attach a deattach screen run 'screen -r'. You can try running restart in a screen session, probably it will succeed as screen will detach, but all programs within screen keep running.

---

### Post by Pssst on 2008-08-12
Ah, that clears it =) It was a feature, after all...
Thanks for yer time though.

---

### Post by ggaaron on 2008-08-12
No problem, I'm happy that I managed to help=)

---

