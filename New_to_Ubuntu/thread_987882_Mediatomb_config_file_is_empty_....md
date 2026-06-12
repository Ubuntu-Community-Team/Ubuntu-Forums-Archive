---
title: "Mediatomb config file is empty ..."
date: 2008-11-20
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-11-20
I installed mediatomb and while following several tutorials none of them tell me how to access the mediatombs gui and when they say open file **gedit ~/.mediatomb.config.xml** I end up looking at a totally blank file.

In the tutorials they all talk as if there should be some code in that file but I have none, ive even erased mediatomb and its folder in the home directory and when i reinstalled and tried to open that file theres still nothing in it.

Can someone point to a GOOD tuturial on mediatomb or tell me what im doing wrong?

Thanks a ton ...

---

### Post by amak79 on 2008-11-26
The location of the configuration file depends on how MediaTomb is started. If are starting MediaTomb during boot via an init script, then you need to run **gksudo gedit /etc/mediatomb/config.xml**. gksudo is necessary since it's likely that your user won't have sufficient permissions to edit this file.

If you are starting MediaTomb manually in a terminal, then you need to run **gedit ~/.mediatomb/config.xml**. Please note this file will **not** exist until you have run MediaTomb at least once in a terminal.

---

