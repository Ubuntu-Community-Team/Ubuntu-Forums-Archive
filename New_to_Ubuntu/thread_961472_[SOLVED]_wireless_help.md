---
title: "[SOLVED] wireless help"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by dog-soldier on 2008-10-28
im going to be going to a friends house in a bit to installl 
ubuntu 8.04.1 LTS . the computer im installing on has wireless internet. the question is do i need to do anything special to get wireless to work?

---

### Post by sudo_chop on 2008-10-28
> **dog-soldier said:**
> im going to be going to a friends house in a bit to installl 
ubuntu 8.04.1 LTS . the computer im installing on has wireless internet. the question is do i need to do anything special to get wireless to work?
 
Do you know what model computer it is? We would need to make sure linux supports the wireless NIC that the computer has. If we know the computer we can probably figure out what NIC it has.
 
-sudo chop

---

### Post by roger_1960 on 2008-10-28
Hi

Luck and a spare network lead!

Seriously, it depends upon the hardware.  Try to have another PC there working so you can go online to solve any issues.
Good luck......

---

### Post by phidia on 2008-10-28
This is another reason a live cd is useful. If you don't get a connection with the live cd you can poll the system with "lspc -v" or "lshw -C network".

---

### Post by dog-soldier on 2008-10-28
its a custom built computer. is there a way to use the live cd and check what nic card it has?
he does have another computer there so ill be able to get back here if need be or search online.
thanks

---

### Post by sudo_chop on 2008-10-28
If you boot the live CD you will likely find out very quickly if your wireless hardware is supported because it will work/not work on the Live CD. But on rare occasion the Live CD has not supported my hardware while an install has.
 
All of the advice given in this thread would be good to follow. DL a Live CD, grab a spare PC, and head over there! The intarweb will still be here to help you if you get stuck.
 
-sudo chop

---

### Post by random turnip on 2008-10-28
You may do.  Certain wireless cards do have difficulty working with Ubuntu, but technically you shoudln't need anything extra.  But until you've installed Ubuntu you can't really tell weather it will wor straight off, my adivce is to keep a computer near by and come here for help, people here have helped me with a few problems.

Good luck, it's well worth the switch, trust me!

---

### Post by dog-soldier on 2008-10-28
ok working with the live cd the internet dont work. i ran lshw -C network command and it says the nic card is a SIS900 pci fast ethernet.

also he has a antenna to get the internet in the other room

---

### Post by fooman on 2008-10-28
are you saying the internet does not work even when plugged into the ethernet card?  ...or are you just trying to connect wirelessly?

what wireless card are you using?

---

### Post by dog-soldier on 2008-10-28
he had a belkin wireless usb antenna hooked up. he is going to take the antenna back and get a wireless card. should he get a linksys or a belkin card.

---

### Post by dog-soldier on 2008-10-30
sorry for bringing this back up but wanted to let you know after he got a linksys wireless card and shutting off wep it now works. i tired many times to get it to work with wep but no luck. so i went into the router and turned wep off. im going to try and figure out how to get it to work with wep but right now he is so happy with how much faster his computer is with Ubuntu then it was with windows. the wireless card he got was a linksys WMP54G ver.4.1
thanks to all that helped

---

