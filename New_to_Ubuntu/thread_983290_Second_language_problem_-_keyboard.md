---
title: "Second language problem - keyboard"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Costas100 on 2008-11-15
I have Ubuntu 8.04 recently installed as a dual boot with Vista (Vista first). This is not my first UBUNTU experience, I had it before as dual boot with Win 98 and Win XP.
All was and is fine in all three installations except in the last one I have a very peculiar problem:
I installed a second language (Greek) from System/Administration/Language Support and then the same second language from System/Preferences/Keyboard.
Immediately (without reboot) both languages work fine in all aspects.
When I turn the computer off and then restart, the second language (Greek) is not accessible. It is there and I can do the change from USA to Gre (at the panel) with the mouse or the keyboard but under either one it only types in English.
I found a temporary solution:
Upon a new start I go to System/Preferences/Keyboard delete the Greek language and immediately after reinstall it and all by magic things work OK for the session.
I think it is either a bug in 8.04 or there is a very simple fix up. I will greatly appreciate any comments.
Thank you all
Costas

---

### Post by simosx on 2008-11-21
> **Costas100 said:**
> I have Ubuntu 8.04 recently installed as a dual boot with Vista (Vista first). This is not my first UBUNTU experience, I had it before as dual boot with Win 98 and Win XP.
All was and is fine in all three installations except in the last one I have a very peculiar problem:
I installed a second language (Greek) from System/Administration/Language Support and then the same second language from System/Preferences/Keyboard.
Immediately (without reboot) both languages work fine in all aspects.
When I turn the computer off and then restart, the second language (Greek) is not accessible. It is there and I can do the change from USA to Gre (at the panel) with the mouse or the keyboard but under either one it only types in English.
I found a temporary solution:
Upon a new start I go to System/Preferences/Keyboard delete the Greek language and immediately after reinstall it and all by magic things work OK for the session.
I think it is either a bug in 8.04 or there is a very simple fix up. I will greatly appreciate any comments.
Thank you all
Costas

This is a known bug in Ubuntu 8.04. If you have autologin enabled, then your keyboard layout settings do not get enabled automatically on login. If you can disable autologin, then it will be ok. Or you can simply install Ubuntu 8.10.
There are also a few other workarounds.

---

### Post by Costas100 on 2008-11-22
Thank you SimosX. Yes I have enabled autologin and I am wandering now what takes more time, to enter my login datails or to simply go to keyboard and change it at the start of every session? For now I will leave things as they are. It only take me seconds to delete and replace the language in the keyboard.
Regarding 8.10, is it possible to install as an upgrade over 8.04?
Thank's again
Costas

---

### Post by simosx on 2008-11-30
> **Costas100 said:**
> Thank you SimosX. Yes I have enabled autologin and I am wandering now what takes more time, to enter my login datails or to simply go to keyboard and change it at the start of every session? For now I will leave things as they are. It only take me seconds to delete and replace the language in the keyboard.
Regarding 8.10, is it possible to install as an upgrade over 8.04?
Thank's again
Costas

You can install 8.10 as an upgrade to 8.04.

For a workaround in 8.04, see
[https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/196277](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/196277)

---

