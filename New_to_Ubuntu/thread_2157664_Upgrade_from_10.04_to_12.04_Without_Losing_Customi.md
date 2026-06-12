---
title: "Upgrade from 10.04 to 12.04 Without Losing Customization"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by alehawk on 2013-06-26
Hi!
I got Ubuntu 10.04 installed with the Gnome shell.
Is there anyway I can upgrade to the 12.10 version without touching my shell and its customization?
I dont have special modules installed etc but I got the desktop environment and shorcuts, etc the way I like it and I dont want to have to customize it agaig uninstalling uniti, installing the new gnome, etc, etc.
If there is a way I can try it, if not, I will have to leave this version.
Tnx!!

---

### Post by newb85 on 2013-06-26
As 10.04 Desktop is EOL, you'll need to follow the instructions at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades).

You'll have to go from 10.04 to 12.04, and then to 12.10, if that is your goal.  12.10 would not be my choice, as 13.04 is the latest, and 12.04 is the latest LTS.  Given that you're still running 10.04 in 2013, I recommend you stick with 12.04.

---

### Post by grahammechanical on 2013-06-26
It is an odds on bet (whatever that means) that the upgrade will break the system. Why? Because you do not have a standard (default) desktop environment. I would be very surprised if you got through two upgrades successfully. There is a massive difference between the code in 10.04 and 12.04. I have tested the upgrade path from 10.04 to 12.04 but only on a default install put in for the purpose. There is also a big difference in code between 12.04 and 12.10. You would not think so, but there is.

The upgrade scripts cannot take into account every variation in modification that users make. Ubuntu 10.04 is built upon Gnome 2. Ubuntu 12.04 is built on Gnome 3. That is one big difference. Then there is the switch over to themes built from the GTK3 tool kit instead of GTK2 tool kit. I would expect an upgrade to trip up if there is a non-fault theme in place. I could go on. 

Regards.

---

### Post by Mark Phelps on 2013-06-26
Couple of suggestions ...

First, I would personally NOT upgrade to 13.04.  Canonical is only going to support this version for a few months.

Second, before you attempt the upgrades, you should consider using Clonezilla and imaging off the install you have now.  That way, if the upgrades go badly, you will be able to restore what you have now in only a few minutes.

---

### Post by alehawk on 2013-06-26
> **Mark Phelps said:**
> Couple of suggestions ...

First, I would personally NOT upgrade to 13.04.  Canonical is only going to support this version for a few months.

Second, before you attempt the upgrades, you should consider using Clonezilla and imaging off the install you have now.  That way, if the upgrades go badly, you will be able to restore what you have now in only a few minutes.
Hi! Yes, I got one, I made one yesterday so thats why Im trying to do it now :D

@newb85 thank you for your reply, Ill ttry to follow that and see if it works.

What was the codename of version 10.04LTS?

Tnx!

---

### Post by colin.p on 2013-06-26
> **alehawk said:**
> 
What was the codename of version 10.04LTS?

Tnx!

10.04 - Lucid Lynx
12.04 Precise Pangolin

---

### Post by newb85 on 2013-06-26
> **grahammechanical said:**
>  Ubuntu 10.04 is built upon Gnome 2. Ubuntu 12.04 is built on Gnome 3.

I don't think that second statement is strictly true. 12.04 runs in Compiz, while Gnome 3 runs on Mutter. 12.04 runs on LightDM, rather than GDM. I could go on.

Your overall point still stands, though.  Lots of changes...

---

### Post by BBQdave on 2013-06-26
> **alehawk said:**
> I got Ubuntu 10.04 installed with the Gnome shell.

Depending on the age of your hardware - and capabilities - you may want to consider Xubuntu 12.04LTS. It will be similiar to your experience with 10.04 Gnome 2, and may run smoother on your hardware :)

---

### Post by 3rdalbum on 2013-06-26
When you perform the upgrade, your software will be updated. Your "ubuntu-desktop" package in 10.04 depends on Gnome 2.x plus a few modifications. In 12.04, the ubuntu-desktop package depends on Gnome 3.x with Unity.

Gnome 3's shell is totally rewritten and won't bring over your Gnome 2 desktop arrangement.

You might, just possibly, have some luck with Mate - maybe it will read the Gnome 2 desktop settings.

However, Gnome 2 is dead. If you want to upgrade, you have to let your old software go to sleep and never wake up.

---

