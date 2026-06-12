---
title: "[SOLVED] Software no show after installing"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by imjscn on 2008-06-29
I installed ckrootkit from Snaptic, then I can't find it in Applications. It's not in usr/bin either. where can I find it?

---

### Post by bumanie on 2008-06-29
In terminal > sudo chkrootkit I don't know of a graphical front-end for it.

---

### Post by paulmilliken on 2008-06-29
Try typing "man chkrootkit" in a terminal to see if the program has a manual page.  If you get a manual page, then the program has installed correctly and the manual should provide instructions for how to use it.

Paul

---

### Post by iaculallad on 2008-06-29
Login as root:

```
sudo -i
chkrootkit
```

Chkrootkit is a terminal-end application so you cannot see it on the Applications menu.

---

### Post by imjscn on 2008-06-29
Thanks, guys!
man finds the manual page
sudo excuted the scan

Pefect!

---

### Post by kansasnoob on 2008-06-29
> **paulmilliken said:**
> Try typing "man chkrootkit" in a terminal to see if the program has a manual page.  If you get a manual page, then the program has installed correctly and the manual should provide instructions for how to use it.

Paul

Awesome! I didn't know that but just tried it with a couple of other apps! Works great! Thanks!

---

### Post by hyper_ch on 2008-06-30
programs that are for the cli won't be added to the menu except if there is a a gui interface (and you install that also).

If you run chkrootkit you might also want to install rkhunter. It's a similar tool.

---

### Post by imjscn on 2008-06-30
Thanks! I tried to download rkhunter, but that download link seems dead, will try it again later.

---

### Post by hyper_ch on 2008-06-30
rkhunter should be in the repos... at least that's what I remember.

---

