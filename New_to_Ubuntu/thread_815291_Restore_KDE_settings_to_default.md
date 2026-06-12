---
title: "Restore KDE settings to default"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by quickk on 2008-06-01
Hi everyone, 

   I would like to reset all kde settings to the default values.  I'm running ubuntu 8.04, with a few kde applications like digikam and amarok.  For some reason digikam won't play any videos (keeps saying "no media player available").  This used to work last night, but now it does not anymore.  I've probably spent 8 hours so far trying to fix this and it is driving me crazy!

I found out that you can configure kde via the kcontrol command.  I'm thinking maybe this got messed up and I want to reset it to default, but this seems impossible.  I've:

-deleted my ~/.kde folder
-"completely uninstalled" anything with kde in its name with synaptic package manager
-searched the whole drive for anything with kde and deleted what I thought was anything related to kde settings
-reinstalled my kde applications (amarok, kile, kate, kcontrol)

When I start kcontrol, it still has the same (altered) settings as before!!!!!!!!!  

Can somebody please tell me what's going on?

---

### Post by Xiong Chiamiov on 2008-06-03
All of your KDE settings are in ~/.kde, so deleting that *should* work.  Did you install KDE on top of an Ubuntu install?

---

