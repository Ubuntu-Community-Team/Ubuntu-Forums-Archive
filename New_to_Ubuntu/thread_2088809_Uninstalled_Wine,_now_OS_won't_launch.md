---
title: "Uninstalled Wine, now OS won't launch"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by Zeriercahl on 2012-11-27
So this WAS my problem: [http://ubuntuforums.org/showthread.php?t=2087519](http://ubuntuforums.org/showthread.php?t=2087519)
(Summary: I installed directx by mistake and could not fix resolution)

So bascially to fix the above problem I uninstalled wine with the following command:

sudo apt-get –purge remove wine

but it said wine wasn't installed so I ran this command:

sudo apt-get purge wine\*

and that deleted stuff for a couple of minutes.
I also deleted my .wine folder.
When it was done my problem didn't fix itself, so I opened my internet browser back up. I then noticed my terminal had disappeared. I tried to alt+tab to it which made my screen lock up for a second. Then my internet browser became full screen and I got an error that I cannot remember now, but it said that some file had crashed or something. I couldn't see or get to my desktop, and when I tried to close the internet browser the computer just froze. I forced a restart, and when I try to launch Ubuntu it just sits there at a blank black screen.

All I did was uninstall wine so I have no idea what happened. I'd really like to avoid reinstalling Ubuntu and losing all the work I have, if that's at all possible. I'm really stuck here so I'd appreciate some kind of help.

Ubuntu 12.04
Wine 1.4.1
Let me know if you need any other information. Thanks a lot.

---

### Post by howefield on 2012-11-27
Can you get to a virtual terminal ?

Ctrl + Alt + F1

If you can, see if you have removed ubuntu-desktop along with wine, by trying to install it.

```
sudo apt-get install ubuntu-desktop
```

Just a suggestion, but I would reinstall for 2 reasons. Firstly it is likely to be quicker than fixing the issue when you don't know how to and secondly after a nice pristine installation, you can take an image of the partition/disk so that the next time you mess up, and there will be a next time :) you have an easy way of getting back to starting point.

---

### Post by Zeriercahl on 2012-11-27
Ok, I got to the virtual terminal.
Before running that command, I pressed "up" on keyboard keys, which brings up the history of commands right? Looking through the commands I can see all the commands I've run for the past couple days (at least). Looking at the most recent I found something perplexing...
So I think I may have entered the command:

sudo apt-get purge wint\*

wint instead of wine... Uhm, would that be problematic?

Anyways, I ran the install ubuntu desktop command and it looks like it's getting somethin'.
"After this operation, 376 MB of additional disk space will be used."

[I]Shall I continue?
[/I]Nevermind ^ that. I got impatient and hit Y. Looks like it installed and is back to a command line. Now what? Should I try to reboot?

---

### Post by Zeriercahl on 2012-11-27
Compiz! I'm pretty sure Compiz is the file that couldn't launch/crashed after I uninstalled wine (or wint...) I'll just edit the top then...

---

### Post by Zeriercahl on 2012-11-27
Okay! I rebooted and I'm back on my desktop! Great! Thanks so much Mr. howefield!

However, as per my previous problem, my resolution is still not fixed. I had removed wine to do try to fix that but now I'm not sure if it just didn't work or my typeo of wint instead of wine messed that up?

This particular thread here is solved (: but if anyone wants to help with my original problem (before I get myself into another deeper hole) that'd be much appreciated.
Anyways, thanks so much!

---

### Post by howefield on 2012-11-27
Glad you are sorted, on that one at least :)

---

