---
title: "cant change desktop background"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-11-20
when i right click the desktop and the contextual menu comes up i click on desktop preferences and nothing come ups. any ideas./tks

---

### Post by rburkartjo on 2013-11-21
what is really weird is that if i start variety (wallpaper changer) i can get the background to change.

---

### Post by simbauad on 2013-11-21
Well used LXDE for only a few days, could you post output of
```
[COLOR=#000000][FONT=Ubuntu Mono]pcmanfm --desktop-pref
```[/FONT][/COLOR]

---

### Post by rburkartjo on 2013-11-21
i get no output when i run
ray@ray-Latitude-D630:~$ pcmanfm --desktop-pref
ray@ray-Latitude-D630:~$

---

### Post by rburkartjo on 2013-11-21
also if i switch to an ubuntu (unity) session. and click on desktop preferences it opens the settings manager however there is no option in the settings to change the wallpaper. wonder if i am missing something in the settings manager.

---

### Post by simbauad on 2013-11-21
Do you have lxappearance installed?

---

### Post by simbauad on 2013-11-21
```
pcmanfm --show-pref=2
```
You are running Lubuntu or Ubuntu+LXDE?
And is lxappearance installed?

---

### Post by rburkartjo on 2013-11-22
i have both lubuntu and lxde installed. and have the same problem with both. also yes on the lxappearance

---

### Post by rburkartjo on 2013-11-22
i found a solution. opened the spm and reinstalled lxde and lxappearance. rebooted. fixed issue with both lxde and lubuntu.

---

### Post by simbauad on 2013-11-22
Yup! Re-installing lxde would have been a last resort. Glad to know your problem was fixed! Mark this thred as solved. Thread Tools > Mark as solved.

---

