---
title: "Need to rollback to ati fglrx(?)"
date: 2014-11-05
forum: PCLinuxOS
---

### Post by Peter_R._Larsen on 2014-11-05
On PCLinuxos kde i did install nvidia just to see if vga could be higher than 1024x768
Now when I boot to pclinuxos it doesnt start to graphical display just like those terminal
I need to rollback to atity
How can I do it that?
Or Do I have reinstall pclinuxod kde fullmonty

---

### Post by QIII on 2014-11-05
Does the machine have ATI or NVIDIA graphics?

---

### Post by Peter_R._Larsen on 2014-11-05
> **QIII said:**
> Does the machine have ATI or NVIDIA graphics?

Yes, the machine have ATI graphics, I was trying to change vga resolution, the vga max resulotion was 1024x768, I was trying to install AMD Catalyst on PCLinuxos, it couldnt, so I changed to from ATI to Nvidia, that was foolish of, anyways.
Can I rollback to ATI? Or Do I have Reinstall PCLinuxod kde

---

### Post by deadflowr on 2014-11-05
*Thread moved to** PCLinuxOS** sub-forum*

Does the machine even have an nvidia graphics card?
If not what might have happened is when you installed the driver, did you run 
```
sudo nvidia-xconfig
```
or somerthing similar?
It might be possible that you created an xorg.conf file that the system loads, but in it it tells the system to load the nvidia driver for a card that does not exist.
perhaps remove that file
```
rm /etc/X11/xorg.conf
```
if you haven't removed the fglrx driver, the system should find it, or else the open-source radeon driver.

---

### Post by Peter_R._Larsen on 2014-11-06
> **deadflowr said:**
> *Thread moved to** PCLinuxOS** sub-forum*

Does the machine even have an nvidia graphics card?
If not what might have happened is when you installed the driver, did you run 
```
sudo nvidia-xconfig
```
or somerthing similar?
It might be possible that you created an xorg.conf file that the system loads, but in it it tells the system to load the nvidia driver for a card that does not exist.
perhaps remove that file
```
rm /etc/X11/xorg.conf
```
if you haven't removed the fglrx driver, the system should find it, or else the open-source radeon driver.

1. no, it have ati
2. tried, still the same
3. when boot there "cannot open file delete" something like
4. and i got "cannot open file deleted"

---

