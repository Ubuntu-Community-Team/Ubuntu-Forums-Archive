---
title: "[problem] Conky / Conkycolors / Startup"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by chresto on 2012-09-05
Greetings,

I've been trying to set Conky on startup but it seems to be a problem. I used Conkycolors to configure it and I added on Startup Applications the ConkyStart file, but Conky never starts automatically.
When I enter in Terminal the following command "conky -c ~/.conkycolors/conkyrc", it gives me the following:

Conky: desktop window (1a00095) is subwindow of root window (1ad)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Segmentation fault (core dumped)

What should I do to fix this error? Thank you in advance :)

---

### Post by ajgreeny on 2012-09-05
So are you saying that conky will not start at all, or just will not start from the startup applications list?

If it's just from the startup applications that you can not get it to run it may because it is attempting to start too quickly, before the desktop is ready.  Try the command ```
bash -c "sleep 15; conky -c /home/*username*/.conkycolors/conkyrc"
```in the startup applications command box (note the full pathway to the configuration file)

---

### Post by chresto on 2012-09-11
I'm sorry for the delay, after many trials and errors, I searched it for one last time and found out that the problem was incompatability between conky 1.8 and ubuntu's unity3D, so, I just downloaded the 1.9 version.

```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt-get update
sudo apt-get upgrade
```

---

