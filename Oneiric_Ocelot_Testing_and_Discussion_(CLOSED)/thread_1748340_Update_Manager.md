---
title: "Update Manager"
date: 2011-05-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chrismine on 2011-05-03
Not opening here, do everybody have this problem? Oh well back to terminal...

---

### Post by deltacomp on 2011-05-03
Your update manager is not working? My update manager works fine when accessed through System->Administration->Update Manager. 
You may need to change your source. Open update manager from System->Administration->Update Manager, click settings (bottom left corner) select the "ubuntu Software" tab then change the software source (download from).

---

### Post by matt_symes on 2011-05-03
> **chrismine said:**
> Not opening here, do everybody have this problem? Oh well back to terminal...

Same as me. Using terminal for updating at the moment.

2.6.39 does not seem to like working with fglrx and my card as well. 

Works alright with radeon dirver though.

---

### Post by Harry33 on 2011-05-03
No need to use terminal, though it works OK. But dependency problems may arise.
Update Manager is not even a good application to use with dev versions.

I use Synaptic.
It shows dependency issues and automatically solves many of them, if they can be solved at the moment.

---

### Post by dino99 on 2011-05-03
oneiric i386 here, logged as "classic" and get a unitysupport issue

dont work via menu or terminal

[https://bugs.launchpad.net/ubuntu/oneiric/+source/update-manager/+bug/776311](https://bugs.launchpad.net/ubuntu/oneiric/+source/update-manager/+bug/776311)

---

### Post by pAsM on 2011-05-03
Hello,
[INDENT]It seems this bug only impacts those not using Unity (Gnome3/Classic). I was able to resolve this in a "hackish" way using the following instructions

```
sudo gedit /usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py

```

Now locate any line containing "unity" and comment it out using a hash sign (#). Update Manager should work fine after. These lines are harmless and seem to just be used to post notifications to Unity.
[/INDENT]

---

### Post by scradock on 2011-05-04
> **pAsM said:**
> Hello,
[INDENT]It seems this bug only impacts those not using Unity (Gnome3/Classic). I was able to resolve this in a "hackish" way using the following instructions

```
sudo gedit /usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py

```

Now locate any line containing "unity" and comment it out using a hash sign (#). Update Manager should work fine after. These lines are harmless and seem to just be used to post notifications to Unity.
[/INDENT]
I'm using Unity in Oneiric and have the same bug, so it's NOT just affecting people not using Unity. I see the bug has been confirmed and triaged, so hopefully there will be a fix soon....I'll try the hack, in the meantime.

---

### Post by dino99 on 2011-05-04
commenting lines 87 & 303 (eg: unitysupport) let update-manager to open, but immediatly close after scan done; so all the lines with "unity" need to be commented. But im not sure about the bad effects that will generate, so better to wait a real fix.

note: its with unity installed but logged as classic

---

### Post by chrismine on 2011-05-06
Used the hack and Update Manager works again. Thanks for the info

---

### Post by dino99 on 2011-05-07
confirm commenting all lines with "unity*" but 674 & 681 let update-manager working

---

### Post by NCLI on 2011-05-07
Thanks for the fix. Annoying issue.

---

