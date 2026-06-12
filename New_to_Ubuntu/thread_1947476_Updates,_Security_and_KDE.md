---
title: "Updates, Security and KDE"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by GeordieJedi on 2012-03-26
Hi all.

OK, Ive scoured Google and a couple of other forums but I cant find what I'm after.
(I'm sure It's easy and I'm just missing something obvious !)

How do I get security/OS updates in KDE ?
(The equivalent of update manager in Gnome)

I've looked all over and nothing seems to to stand out?


I've installed Ubuntu 11.10 and I'm currently testing KDE as my new DE/WM.
I've installed from a magazine cover disc (LXF #152).

Any help or advice would be greatly appreciated.

Cheers.

---

### Post by Ms. Daisy on 2012-03-26
```
sudo apt-get update
```Not sure about graphically though.

---

### Post by haqking on 2012-03-26
```
sudo apt-get update && upgrade
```

or use the muon updater gui or install synaptic

---

### Post by QIII on 2012-03-26
Use the konsole as Ms. Daisy suggests.  Or, if you have not already, install Synaptic.

Muon, the default Kubuntu package manager, is a disaster.

---

### Post by haqking on 2012-03-26
> **QIII said:**
> Use the konsole as Ms. Daisy suggests.  Or, if you have not already, install Synaptic.

Muon, the default Kubuntu package manager, is a disaster.

i agree i just came back to edit to say install synaptic

---

### Post by QIII on 2012-03-26
Yep.  It's a soup sandwich.

I also use dist-upgrade to be sure it attempts to resolve all dependencies.

---

### Post by haqking on 2012-03-26
> **QIII said:**
> Yep.  It's a soup sandwich.

I also use dist-upgrade to be sure it attempts to resolve all dependencies.

thats spooky i just had chicken noodle soup and it was thick, so i  made a sandwich with the noodles.

---

### Post by ofnuts on 2012-03-26
> **GeordieJedi said:**
> Hi all.

OK, Ive scoured Google and a couple of other forums but I cant find what I'm after.
(I'm sure It's easy and I'm just missing something obvious !)

How do I get security/OS updates in KDE ?
(The equivalent of update manager in Gnome)

I've looked all over and nothing seems to to stand out?


I've installed Ubuntu 11.10 and I'm currently testing KDE as my new DE/WM.
I've installed from a magazine cover disc (LXF #152).

Any help or advice would be greatly appreciated.

Cheers.
The package manaher in KDE is called kpackagekit.

In the KDE services configuration (Systems settings - >"Advanced" tab, "service manager", you can enable the kpackagekit service that will warn you about updates.

---

### Post by QIII on 2012-03-26
Muon replaced kpackagekit in Kubuntu 11.10, I believe.

Installing KDE in Ubuntu may being it in.

I have a fresh copy of Kubuntu at home.  I'll report back if I am mistaken.


Edit:  FYI -- kpackagekit is definitely not included in my fresh installation of Kubuntu 11.10.

---

