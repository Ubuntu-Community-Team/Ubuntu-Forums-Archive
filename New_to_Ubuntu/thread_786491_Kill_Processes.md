---
title: "Kill Processes"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Jabz.biz on 2008-05-08
Hey,

Last night my ubuntu froze. Never happened to me before, only on windows. In windows you type ctrl+alt+del. The processmanager opens and you can kill processes. I wonder what I can do in ubuntu. So I have two questions: 

1. how can I get to the Terminal if my computer freezes?
2. is there a shortcut to the system monitor respectively the processlist?

Thanks & Regards - Jab

---

### Post by TeoBigusGeekus on 2008-05-08
1)Alt+F1 (I think) will give you a command line.
2)Ctrl+Alt+Backspace will kill all your processes and log you out.
3)Right click one of your panels and choose add to panel. Then select System Monitor. Whenever something freezes, you can click on the System Monitor applet->Tab processes and kill/end the culprit.

---

### Post by prshah on 2008-05-08
> **Jabz.biz said:**
> 1. how can I get to the Terminal if my computer freezes?
2. is there a shortcut to the system monitor respectively the processlist?


Look for the "Magic SysRq Keys" in Wiki.

In summary;

Ctrl+Alt+SysRq+E - Terminate all running process and drop to shell
Ctrl+Alt+SysRq+B - Instant Reboot
Ctrl+Alt+SysRq+S - Sync disks (flushes unwritten data to disk)

And a whole bunch of other useful combos.

---

### Post by lgastmans on 2008-05-08
ctrl+alt+F2 will bring you to command line mode
there you can check processes by typing ps -A
and you can kill a process by typing kill <process number>

ctrl+alt+F7 will take you back to graphics mode

HTH

---

### Post by Jabz.biz on 2008-05-08
Sorry that it took me so long to answer, I`m on holidays and went to the pool. :) 

Thank you for your answers, you helped me a lot!

---

### Post by SunnyRabbiera on 2008-05-08
I usually try to make use out of the kill applet (force quit), you can get it by right clicking your panels and select "add to panel"
and go down to "force quit" and add it to the panel.

---

### Post by glennric on 2008-05-08
If the xserver completely locks up so that you can't do anything in the graphical environment, and Ctrl-Alt-Fn and Ctrl-Alt-Backspace don't work the best thing I have found to do is to use the magic system requests.  
What I usually try is first do Alt-SysRq-R.  Then try Ctrl-Alt-Fn (with n beign one of the numbers 1 through 6, to get a console.  This usually works if it is just the xserver locked up.  If that doesn't work then you can try some of the other magic system requests in the wiki.

---

### Post by Jabz.biz on 2008-05-08
Hmm,...so many great ideas. I`m thinking about summing these up and putting them on a website. I always wanted to have something like that where I can lookup solutions to common problems. As I`m new to linux this makes sense. I`ll post the link later.

---

