---
title: "Using NDIS to enable a wireless card driver"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by katkanemoto on 2008-07-20
I am trying to get a Linksys Wireless-B card, version 4, to work on xubuntu.  After some research I think I need to install NDIS and then an XP driver to get the card to work.  Is this the best way to get this card to work?

Sorry if this is a dumb question but I am new and all.

---

### Post by macaholic on 2008-07-20
Ndiswrapper should work, the manual way is a little messy, so I will suggest auto-ndiswrapper, it is still in early development, but it will be alot easier than the manual way if it works. download it [here]("http://easylinuxwifi.org/Auto-NDIS-0.1.tar.gz") Before running anything make sure you have python installed. Extract the tar.gz file to your desktop, and then run the following:
```
cd Desktop/Auto-NDIS*
sudo python auto-ndis.py
```
Follow the prompts and hopefully that will work. if that doesn't post back and I'll refer you to other methods.

---

### Post by JagDragon on 2008-07-20
What is the card you are using? Post the output of ```
lspci | grep Network
```

---

### Post by phidia on 2008-07-20
We will probably need more detailed info on the card-is it an internal pci slot card, pcmcia, something else? If you can open a terminal from Applications>Acessories>Terminal and put this in there > lspci -vand this > lshw -C network paste the output of both those here.

---

