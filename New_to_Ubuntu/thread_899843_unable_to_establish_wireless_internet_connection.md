---
title: "unable to establish wireless internet connection"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by bmatthew on 2008-08-24
I just installed hardy 8.04 on my dell laptop, but am unable to find my wireless network.  I have no linux experience and am just diving into this so any help or suggestions are appreciated.

---

### Post by zamadatix on 2008-08-24
have oyu tried the wiki.
this should give a list of supported hardware [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by silent contender on 2008-08-24
Does Ubuntu recognize you wireless card.  Run lspci (someone correct me if I am wrong, I still learning), see if someone help you from there.  If it doesn't recognize your card, you may need ndiswrapper and ndisgtk.

---

### Post by mgranet on 2008-08-24
What model # is your laptop?

---

### Post by zamadatix on 2008-08-24
to save some more post just say all of your laptop and hardware information

---

### Post by DrPppr242 on 2008-08-24
if you're new to linux 'lspci|grep -i ethernet' might be a more direct way to list detect network cards (wired and wireless) you'll likely have at least two listed, a wired and wireless if that shows a wireless but the command 'ifconfig' only shows one interface probably eth0 then you'll need the proper drivers for your wireless card which is different depending on the model.  If that is the case post the output of lspci|grep -i ethernet' and someone here can probably point you in the right direction to install the neccesary drivers/modules

---

### Post by pizzavortex on 2008-08-24
What does iwconfig say?

---

