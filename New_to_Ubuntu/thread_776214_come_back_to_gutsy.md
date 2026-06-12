---
title: "come back to gutsy"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by antonio_ing on 2008-04-30
Hi everybody
I have udgraded my laptop (a Toshiba Satellite) just Today from the Gutsy Gibbon ubuntu to the newest Hardy version. I have found it very slow and I have seen that a lot of users have the same problem. Is it possible to come back somehow to Ubuntu 7.10?

---

### Post by aheckler on 2008-04-30
Downgrades aren't possible like that I think. You'll have to do a complete reinstall with a Gutsy LiveCD.

---

### Post by kellemes on 2008-04-30
> **antonio_ing said:**
> Hi everybody
I have udgraded my laptop (a Toshiba Satellite) just Today from the Gutsy Gibbon ubuntu to the newest Hardy version. I have found it very slow and I have seen that a lot of users have the same problem. Is it possible to come back somehow to Ubuntu 7.10?

I'd go for a reinstall indeed..
Still, you could first try to find out why Hardy is slow, who knows there is an easy fix for it..

---

### Post by peterdk on 2008-04-30
If you have your /home on a seperate partition, it is quite easy to reinstall gutsy. All your settings will be kept. You do have to reinstall all your extra software though.

---

### Post by antonio_ing on 2008-04-30
Should I format the partition or just install the older ubuntu version without worrying about the data inside?

---

### Post by cubeist on 2008-04-30
Wait... don't reinstall...The speed issue may be due to trackerd.

Try two things before reinstalling.

First, go to system/admin/system monitor, click on the process tab, sort by cpu load and then cpu time and see what, if anything, is using a lot of cpu.

if it is tracker, go to system/prefs/search and tracking and try turning it off, reboot and see if your system is more responsive.

Or, if there is something else hogging your system, post back with what it is and maybe we can offer a solution.

---

### Post by antonio_ing on 2008-04-30
thx cubeist,
trackerd was high and i have disabled it. Now i'll finish to copy all my data in the external HD and then i'll see if there are some improvement. Otherwise I have already ubuntu 7.04 that was quite good and light

---

### Post by cubeist on 2008-04-30
> **antonio_ing said:**
> thx cubeist,
trackerd was high and i have disabled it. Now i'll finish to copy all my data in the external HD and then i'll see if there are some improvement. Otherwise I have already ubuntu 7.04 that was quite good and light

Once you have everything set-up you could try enabling tracker again and set your preferences to low (as in it does not take over your system when tracking).  However, I think tracker is useless and keep it off via system/preferences/sessions and uncheck tracker and tracker applet.

---

