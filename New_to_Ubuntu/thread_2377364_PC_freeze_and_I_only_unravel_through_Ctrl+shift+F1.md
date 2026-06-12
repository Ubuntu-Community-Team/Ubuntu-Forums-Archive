---
title: "PC freeze and I only unravel through Ctrl+shift+F1"
date: 2017-11-12
forum: New to Ubuntu
---

### Post by sed_faster on 2017-11-12
Hello, 

I was use a firefox to surf on the internet when I need uploaded some photos to the website, through browser. When I press the option to open dialog box to choose which images I intend upload my system crash/freeze. I could only move the mouse (but very slowly). Any more works.
Fortunately I remember press "Ctrl+Alt+F1" and I can login as a root and execute Htop, on terminal, and I see this scenario: [link]("https://drive.google.com/open?id=1CQVGsqQ9lTSW_P5lkV9uGETQQn7j9nDv")

The first line blue points to the process which consume a lot ram and cpu. I need kill this process, through button "F9" some times to save my system. Because I didn't want reboot entire system because I will lose work. I need two things:

1-What is this process?
2-Which manner has I to resolve this problem (to sometimes lock the computer to another program)?

Thanks

---

### Post by Holger_Gehrke on 2017-11-12
Since you still have access to the system -- at least to a command line -- , why don't you ask your computer ?
```
man openbox
```
should give you the manual for the program. That should tell you what it is. 
AFAIK openbox is a window manager. If you kill it, it should get restarted by the session manager.
What kind of surprises me: openbox is known for it's low use of resources. If it's producing this kind of load, some other program is doing something seriously wrong and forcing openbox to do more work. I had a similar problem recently with xfwm4 - the real problem was a panel plugin which used some brain dead way to update it's display -- especially when the panel actually isn't visible - and didn't produce much load itself. The funny thing: it was a plugin to show cpu load ...

To stop the process you can do
```
sudo kill -9 1493
```
The 1493 is the process id (PID) of the process you want to stop as shown by htop (or top or ps ...)

Holger

---

### Post by DuckHook on 2017-11-12
Openbox is needed by the LXDE environment and is highly unlikely to be the culprit. As Holger_Gerhke points out, the problem is probably with another app that is abusing openbox systems calls. Try keeping track of what apps you launch that cause this problem. Also, try killing apps other than openbox, like Firefox, which seems to be what started your problem.

The next time you try to download something, open Firefox from the command line instead of using the graphical shortcut. That way, terminal will provide the needed error messages to further diagnose what the possible problem might be.

You should also have a look in your logs, especially syslog and kern.log.

---

