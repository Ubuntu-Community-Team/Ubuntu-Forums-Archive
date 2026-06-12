---
title: "Users logged in via GUI not listed by 'who', 'w', or 'last'."
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Brian Vaughan on 2011-10-01
It looks like some update on September 30 or October 1 inhibits correct tracking of GUI logins. At a guess, I think lightDM is not updating /var/log/wtmp. I'm not sure, though, and I'd appreciate suggestions on how to narrow it down so I can make a proper bug report.

I often log in to my desktop via ssh, then execute 'w' or 'who' to see if anyone is logged in, before I do any work on my system. I executed 'w', found that there was only one user logged in, which was me, then I started x11vnc and connected to my desktop, only to see that my stepson was logged in and playing Minecraft. I tried 'who', and it indicated only my login; 'last' didn't show my son's login today.

'last' did show his login via GUI from yesterday, before I applied a batch of updates, so that's why I think this was just broken:
```
kidongui     tty7         :0               Thu Sep  1 16:50 - 21:37  (04:46)

```

I did see that his processes were correctly listed by 'ps' and 'top'.

---

### Post by Toz on 2011-10-07
I can confirm that I am seeing the same behaviour here. If I go to another virtual terminal (Ctrl+Alt+F1) and log in, it gets logged, but no logging for lightdm logins.

Have you created a bug report? I will add my info to it.

---

### Post by effenberg0x0 on 2011-10-07
I am seeing all logins. Local VT, ssh, Lightdm.

[04:40 ][al:AL-DESK:/usr/share]
$ who
al       tty1         2011-10-06 20:04
al       pts/0        2011-10-06 20:05 (:0)
al       pts/2        2011-10-07 17:30 (al-home-office.local)

It'd be a serious security issue if a user could login to the system without being detected by who, etc. You gotta look into it further and report immediately if you're sure of this behavior.

Regards,
Effenberg

---

### Post by Toz on 2011-10-07
Reviewed lightdm bugs and could not find relative bug. Have created new bug report: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297").

---

### Post by Brian Vaughan on 2011-10-07
Thanks for creating the bug report. I thought I had, but I don't have an email confirmation. I can't seem to see the bug report you've linked, though.

On further experimentation, I found that if I logged into the GUI, then opened a GNOME terminal window, both the GUI login and the terminal were listed by w, etc.

---

### Post by Toz on 2011-10-07
The report I created is still flagged private. It needs to be reviewed and made public before others can view it. Should happen shortly.

I have many terminal windows open (xfce4-terminal) but still nothing showing up in w, who or last.

---

### Post by cariboo on 2011-10-07
You can make the bug public yourself, you don't have to wait for anything.

---

### Post by Toz on 2011-10-08
And so I can. All of my earlier reports became public on their own. Interesting.

Anyways, its public now.

---

