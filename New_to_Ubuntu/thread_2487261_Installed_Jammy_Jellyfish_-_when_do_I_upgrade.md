---
title: "Installed Jammy Jellyfish - when do I upgrade?"
date: 2023-05-29
forum: New to Ubuntu
---

### Post by nowindows2 on 2023-05-29
I was going to post in the 'Installation & Upgrades' board, but my question seemed too basic.

So I finally overwrote Windows 11 on my new HP desktop and installed Jammy Jellyfish. All is good (so far) in my Linux world.

I'm a bit confused about updating though - with Windows it's a foregone conclusion. Should I update to 23.04 Lunar Lobster, or do I leave JJ until 202*? Or is it done automatically via the Ubuntu updater?  

Thanks :)

---

### Post by psychohermit on 2023-05-29
I would stay with 22.04 LTS.  if you upgrade to 23.04 you will have to upgrade every 6 months.

--glenn

---

### Post by Holger_Gehrke on 2023-05-29
To update from 22.04 to 23.04 you first have to get to 22.10. You can go from one release to the next OR from one LTS release to the next LTS, usually when the new LTS has its first point release - 24.04.1 in this case - a few month after initial release. If you want to switch to regular releases, you have to make the decision to do so before 22.10 goes out of support. Most of the more experienced users here advocate for staying on LTS releases, release upgrades are not without risks. Quite a few people actually don't do release upgrades ever and instead do a fresh install on every LTS. If you keep your home directory on a separate partition and keep track of your manually installed programs this can be done quite quickly - the last time I did it that way I was done after about three hours including reinstalling programs I had installed from source.

A release upgrade is never done automatically. To do one you can call 'sudo do-release-upgrade' from the command line. If you're on an LTS - which 22.04 is - and want to upgrade to normal releases you have to edit the file /etc/update-manager/release-upgrade and change the line 'Prompt=lts' to 'Prompt=normal'.

Holger

---

### Post by nowindows2 on 2023-05-29
Okay, I'll stick with JJ.

---

### Post by nowindows2 on 2023-05-29
Thanks - I didn't realize I needed 22.10 first, so that's good to know for the future. I'll stick with JJ for now. Thanks again!

---

### Post by grahammechanical on 2023-05-29
In Software & Updates>Updates tab make sure that Notify me of a new Ubuntu version is set to for long-term support versions. Then when the time comes and you do your regular update you will be notified that 24.04 is available and be given an option to update.

Regards

---

