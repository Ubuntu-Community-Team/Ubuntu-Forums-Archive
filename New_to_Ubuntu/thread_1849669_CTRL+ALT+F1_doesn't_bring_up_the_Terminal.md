---
title: "CTRL+ALT+F1 doesn't bring up the Terminal"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by sanoysyu on 2011-09-24
Hello, I have been having trouble with the terminal. When I press the CTRL+ALT+F1 (or F2/F3/F4/F5/F6 for that matter) it doesn't bring up the terminal. I installed Ubuntu 11.04 just 3 days ago on my Alienware M14x laptop and at first I was able to see the terminal when I pressed CTRL+ALT+F1 but now I don't. 

When I press CTRL+ALT+F1 the mouse pointer disappears and the GUI becomes unresponsive. Only when I press the CTRL+ALT+F7 the mouse pointer comes back and the GUI starts working again.

I thought the problem was with the GNOME console and reinstalled GNOME from Synaptic Application manager. But it didn't work in the same session. When I rebooted and tried CTRL+ALT+F1 I could see the terminal and it was working fine. I rebooted again and the same problem: when I press CTRL+ALT+F1, it doesn't bring up the terminal! Please, I need help!

---

### Post by wildmanne39 on 2011-09-25
Hi, to open the terminal it is ctrl+alt+t,
the f1 thru f6 takes you out to the tty and you have to enter your username and password to use it and f7 brings you back to the desktop.
Thank you

---

### Post by sanoysyu on 2011-09-25
Thanks for your reply wildmanne39! As you suggested, the CTRL+ALT+t key works the question still remains, why doesn't the CTRL+ALT+F1 key work?

---

### Post by wildmanne39 on 2011-09-25
Hi, from your description it does.

When you it ctrl+alt+f1 it takes you to a black screen it is different from the terminal, tty you enter your login name, then password and you can use it pretty much like a terminal, but as far as I know ctrl+f1 has never open the actual terminal.

So is the problem you are trying to use tty and it has crashed?
Thank you

---

### Post by sanoysyu on 2011-09-25
I think you are right, I think it was yesterday, when I tried to open the TTY (or terminal) by hitting CTRL+ALT+F1, the terminal didn't show up and GUI became unresponsive. And in a panic I hard-rebooted the system. I think that's when it crashed. And now it doesn't work. But I hoped reinstalling GNOME would have fixed it but apparently, it's not.

---

### Post by wildmanne39 on 2011-09-25
Hi, what version of ubuntu are you using?
Thank you

---

### Post by sanoysyu on 2011-09-25
I am using Ubuntu 11.04

---

### Post by wildmanne39 on 2011-09-25
Hi, here is one site that talks about that problem but read carefully the whole page before you think about making changes, and if you are unsure post for help and hopefully someone will answer.
[http://askubuntu.com/questions/43386/how-do-i-get-my-blacked-out-ttys-back](http://askubuntu.com/questions/43386/how-do-i-get-my-blacked-out-ttys-back)

Also you  can goggle tty will not work in ubuntu and you will get more results.

I am off for tonight it is getting late here.
Thank you

---

### Post by haqking on 2011-09-25
> **wildmanne39 said:**
> Hi, to open the terminal it is ctrl+alt+t,
the f1 thru f6 takes you out to the tty and you have to enter your username and password to use it and f7 brings you back to the desktop.
Thank you

mmm not picking but for clarity for the OP, tty and the terminal are no different.  The gnome-terminal uses the first tty or tty0

Every instance of it after that is incremented.

ctrl+alt+f1 etc are virtual consoles still using tty or teletypewriter.

If you type tty from a terminal window it will tell you what tty you are using.  If you open multiple instance of a terminal then each tty will show an incremented number from the one you started with.

i read your post like the terminal and tty were different which i suppose they are in terms of pts and tty but pts is still using a tty, perhaps you werent saying that though, in which case my apologies for butting in LOL ;-)

---

### Post by HolyDonut on 2011-09-26
Ctrl + Alt + F1 (through F6) take me to a blank black screen.

When I hit Ctrl Alt F7 my desktop gets all distorted (see the screenshot). 

Is it the NVIDIA proprietary driver just sucking? I'm on a laptop with an NVIDIA GeForce video card.

I'm using a fully updated Natty 11.04 Ubuntu. I'm in Ubuntu Classic (no Unity). I have Compiz installed.

---

### Post by FerroPower on 2011-09-26
> **HolyDonut said:**
> Ctrl + Alt + F1 (through F6) take me to a blank black screen.

When I hit Ctrl Alt F7 my desktop gets all distorted (see the screenshot). 

Is it the NVIDIA proprietary driver just sucking? I'm on a laptop with an NVIDIA GeForce video card.

I'm using a fully updated Natty 11.04 Ubuntu. I'm in Ubuntu Classic (no Unity). I have Compiz installed.

have you by any chance edited xorg.conf or change dri settings ?

---

### Post by wildmanne39 on 2011-09-26
Hi, I believe it is an issue with hibernate and resume, but I do not know a solution for it, You should start your own thread with a good title.
Thank you

---

### Post by HolyDonut on 2011-09-26
Thanks wildmanne39 I will set up a new thread then.  EDIT: Here's the link to the new post - [http://ubuntuforums.org/showthread.php?p=11288986#post11288986](http://ubuntuforums.org/showthread.php?p=11288986#post11288986).

FerroPower, I may have messed with the xorg.conf settings, not directly, but through the NVIDIA X Server Settings app in System > Administration. I did NOT click the "Save to X Configuration File" button though.

---

