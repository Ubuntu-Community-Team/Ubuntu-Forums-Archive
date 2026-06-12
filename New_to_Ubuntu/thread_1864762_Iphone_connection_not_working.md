---
title: "Iphone connection not working"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by flyfishingphil on 2011-10-19
Just got an Iphone 4 and tried connecting but all I get is is:

"Unable to connect. Unhandled Lockdown error (-4)"

Did a search for Iphone 4 but only found 3 and none dealt with initial connection. Anybody able to help me get this connected?

Update:

Found references to iFuse and went in to Synaptics and installed both but all I get are a photo and a music opportunity. Is there a way to set it up to share info (like ringtones or pdf info) between them?

---

### Post by protpisys on 2011-10-19
I was able to get photos and music for a couple of days after upgrading ios5 and or ubuntu 11.10 but now I get the same message and am unable to access anything on my phone at all...very frustrating

---

### Post by flyfishingphil on 2011-10-20
Gave up on the iPhone4 and replaced it with a Motorala Atrix 2. Now all I need to do is figure out how to connect this one.

No solution on the iPhone 4 but I'll list it as solved.

---

### Post by d4m1r on 2011-10-20
> **protpisys said:**
> I was able to get photos and music for a couple of days after upgrading ios5 and or ubuntu 11.10 but now I get the same message and am unable to access anything on my phone at all...very frustrating


What happened when you were running iOS 4.x? Sometimes I'd liked to connect my iPhone in my Ubuntu partition just to pull a few photos from it (and NOT have it sync music). Does 11.04 recognize it as a USB device?

---

### Post by dniMretsaM on 2011-10-20
> **d4m1r said:**
> What happened when you were running iOS 4.x? Sometimes I'd liked to connect my iPhone in my Ubuntu partition just to pull a few photos from it (and NOT have it sync music). Does 11.04 recognize it as a USB device?

It should. Test it out.

---

### Post by flyfishingphil on 2011-10-20
> **d4m1r said:**
> What happened when you were running iOS 4.x? Sometimes I'd liked to connect my iPhone in my Ubuntu partition just to pull a few photos from it (and NOT have it sync music). Does 11.04 recognize it as a USB device?

I didn't get it to respond as a usb device. Don't remember what it said on the box that popped up mid-screen on the laptop but it did say it was not able to open because of some conflict and missing app's.

---

### Post by wolfen69 on 2011-10-20
> **d4m1r said:**
> Does 11.04 recognize it as a USB device?

No it won't. I suggest trying gtkpod to try and see the phone. If it doesn't you will need windows/mac and itunes. Windows in virtualbox is a decent solution.

---

### Post by d4m1r on 2011-10-20
I don't want things to sync automatically and gtkpod does exactly that. I have Windows 7 and iTunes for that, just sometimes I'd like to transfer pictures from my iPhone to Ubuntu manually. Found out 2 things after investigating:

1)libimobiledevice2 was install by default in 11.04 (search for it in software centre
2)but it does not seem to work with 4.3.2 even though the name of my iPhone and even the icon appear
3)can't mount it though (Unable to connect. Unhandled Lockdown error)
4)does charge it, and quick
5)found a stable version online (libimobiledevice-1.0.6.tar.bz2) but I don't know what to do with .tar.bz2 files yet...

Anyone able to connect their 4.x iPhone 4 in their Ubuntu partition and mount is successfully?

---

### Post by flyfishingphil on 2011-10-20
> **wolfen69 said:**
> No it won't. I suggest trying gtkpod to try and see the phone. If it doesn't you will need windows/mac and itunes. Windows in virtualbox is a decent solution.

I gave up on VBox. It continually wouldn't start unless I did a change then, more than half the time, it wouldn't recognize the change. Also I trust Windough$ about as much as I do politicians so strictly Ubuntu and will put up with any deficiencies before I'd ever go back to Win.

---

### Post by d4m1r on 2011-10-21
UPDATE: got it working without having to manually install anything! Simply added a PPA (whatever that is :p)

```
 

sudo add-apt-repository ppa:pmcenery/ppa  
sudo apt-get update  
sudo apt-get dist-upgrade 

```

Worked like a charm! iOS 4.3.2, iPhone 4, Natty 11.04...

---

### Post by protpisys on 2011-10-22
> **d4m1r said:**
> What happened when you were running iOS 4.x? Sometimes I'd liked to connect my iPhone in my Ubuntu partition just to pull a few photos from it (and NOT have it sync music). Does 11.04 recognize it as a USB device?

the iphone would appear on the desktop as 2 icons, from which I could get at my pics, my main concern, and music files...it appeared to work like a usb drive does

---

### Post by protpisys on 2011-10-22
not anymore it doesn't

---

### Post by protpisys on 2011-10-22
> **d4m1r said:**
> UPDATE: got it working without having to manually install anything! Simply added a PPA (whatever that is :p)

```
 

sudo add-apt-repository ppa:pmcenery/ppa  
sudo apt-get update  
sudo apt-get dist-upgrade 

```Worked like a charm! iOS 4.3.2, iPhone 4, Natty 11.04...

d4m1r, that did it...I owe you one If I can ever figure anything out on my own I'll be sure to share it...thanks, this is huge for me...Bob

---

### Post by dniMretsaM on 2011-10-22
> **d4m1r said:**
> UPDATE: got it working without having to manually install anything! Simply added a PPA (whatever that is :p)

```
 sudo add-apt-repository ppa:pmcenery/ppa  
sudo apt-get update  
sudo apt-get dist-upgrade 

```Worked like a charm! iOS 4.3.2, iPhone 4, Natty 11.04...

PPA stands for **P**ersonal **P**ackage **A**rchive. Anyway, I didn't even realize that PPA had been updated for Natty. Good to know for the future.

---

### Post by d4m1r on 2011-10-22
> **protpisys said:**
> d4m1r, that did it...I owe you one If I can ever figure anything out on my own I'll be sure to share it...thanks, this is huge for me...Bob


No problem!

---

