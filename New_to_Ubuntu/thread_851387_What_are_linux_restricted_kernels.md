---
title: "What are linux restricted kernels?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by cooltuyul on 2008-07-06
im trying to set up a home wireless network and im using an airlink 101: awlh4130 pci adapter. i havent installed the adapter yet. i dont know what linux restricted kernels are or what to do with the them. 

heres the link: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101)

tk in advance

---

### Post by annda on 2008-07-06
it actually means kernel modules with restricted drivers - without an open source license. in the more recent versions of ubuntu those are usually installed by default. if your card is not working, try system>administration>hardware drivers or synaptic to install linux-restricted-modules for your kernel (search for linux in package name and check the modules for the most recent version of the kernel you have installed - is is checked, probably 2.6.24-19 in hardy)

---

### Post by AngryXshun on 2008-07-31
Why doesn't the os recognize the wireless key? and it keeps asking for the key over and over and over again. please help me?

---

### Post by annda on 2008-07-31
> **AngryXshun said:**
> Why doesn't the os recognize the wireless key? and it keeps asking for the key over and over and over again. please help me?

probably because the key is wrong.

please describe your problem in more detail in a new thread. what does the popup window exactly say? which version of ubuntu are you using? is it a normal ASCII key or hexadecimal one? what is your encryption, WEP or WAP? etc.

---

### Post by AngryXshun on 2008-08-05
> **annda said:**
> probably because the key is wrong.

please describe your problem in more detail in a new thread. what does the popup window exactly say? which version of ubuntu are you using? is it a normal ASCII key or hexadecimal one? what is your encryption, WEP or WAP? etc.
The key is right it works in XP which is installed next to ubuntu 8.04.1 and it just asks me to input the key again. I've tried using the "OPEN" option and the "SHARED KEY" option. and it is WEP normal ASCII key.
Thanks for the reply.

---

