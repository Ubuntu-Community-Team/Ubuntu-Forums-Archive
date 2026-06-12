---
title: "[SOLVED] How Do You Install XBMC?"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by ModdTaco on 2008-10-03
Hey im trying to get XBMC on Ubuntu here but it wont work. I've tried the install commands here.

```
deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
deb-src http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
```

I keep getting a

```
taco@Taco-dator:~$ deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
bash: deb: command not found

```

---

### Post by jrothwell97 on 2008-10-03
You don't run these commands! It's not immediately obvious, but you have to add these to your apt sources.list. Go to System/Administration/Software Sources, and under Third-Party Software Sources click on "Add" and copy in the first line (repeat this for the second.) Then close the dialog and when asked to update tho package information, click 'Reload'.

Good luck.

---

### Post by ModdTaco on 2008-10-03
Thanks Man! Worked great.. Too bad after all that I find out it wont even play in fullscreen. Useless......

---

### Post by phowells on 2008-10-14
It does play in fullscreen.  You need to configure this in XBMC itself.

---

