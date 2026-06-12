---
title: "Finding out which wifi card i have"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by mike941 on 2008-05-13
I just used lspci and one of the devices was an atheros wifi card. At the company website(acer) the driver for my wifi card is suppose to be a broadcom driver. Is acer just really dumb or negligent or do i need to find a better way to find out what wifi card i have? I can swear in a diffrent thread i used a diffrent command and it showed i had a broadcom card but then again lspci deosn't lie.

---

### Post by zenwalker on 2008-05-13
Well is u r wifi card a usb or pci slotted one? if usb, u can issue lsusb cmd. 

IF u want to see if a driver has been loaded by u r OS for that h/w, ussiue modprobe.

---

### Post by FakeOutdoorsman on 2008-05-14
Did you try lspci in "very verbose" mode?
```
lspci -vv
```
Also, lshw might list something that lspci misses:
```
sudo lshw
```

---

### Post by nicedude on 2008-05-14
lspci isn't always correct. With my acer 5520-5716 it lists my wifi card as a AR5006 when it is in fact a AR5007 so while it should show you the brand in general it isn't always correct with the model #

I would recomend using your Acer documentation or one of their websites to find out for sure what wifi chipset your laptop uses, It wasn't easy for me either but after looking at different Acer websites for different countries I found one that told my wifi chipset model.

I think you will find you have an Atheros brand wifi of some sort though as it seems to be what Acer uses.

ALSO HERE IS A TIP FOR ALL ABOUT LSPCI

How to update your PCI known device list that lspci uses. 

run this update command -> sudo update-pciids

this will download the most recent PCI device list from the internet :-)

---

