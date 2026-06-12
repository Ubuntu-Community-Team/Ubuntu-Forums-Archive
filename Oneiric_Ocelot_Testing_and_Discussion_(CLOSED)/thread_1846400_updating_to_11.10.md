---
title: "updating to 11.10"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by unknow04 on 2011-09-19
ey guys hi I was trying to upgrade my version of ubuntu 11.04 to 11.10 but when I restart there was just a black screen. I can log in on my session and I have been trying for hours to solve it but I cant, so any one know how to copy my files to an usb via terminal ? cause I dont know what directory goes when i connect it 

pd.: would be better if some one knows how to solve the black screen problem

---

### Post by uRock on 2011-09-19
Moved to *ubuntu +1* sub-forum. 11.10 is still in beta testing.

---

### Post by unknow04 on 2011-09-19
ok thanks

---

### Post by Framli on 2011-09-19
Hi unknow04,
maybe there is something wrong with your display manager, so try:
```
sudo stop lightdm
sudo start ligthdm
```

---

### Post by lucazade on 2011-09-19
May I ask why did you upgrade to a beta release of a development version?
Upgrade in every OS is usually a risky business, especially now that oneiric is not yet released and almost every components (DE, Shell, Login manager..) are totally different from the previous version, making migration an hard process.

---

### Post by unknow04 on 2011-09-19
thanks famli but doesn't work

lucazade i don't know it but now i really know T.T

---

### Post by wgarcia on 2011-09-19
Have you tried to log into recovery mode from the Grub menu? If you don't see the Grub menu press the Shift key as soon as you restart your system.

---

### Post by lucazade on 2011-09-19
> **unknow04 said:**
> thanks famli but doesn't work

lucazade i don't know it but now i really know T.T

:) I can imagine your drama..
try what wgarcia suggested you and in case try to purge and reinstall video drivers from recovery mode like nvidia-current or frglx for ati.
if this doesn't work install 'gdm' as login manager and set it as default.
let us know how it goes.

---

### Post by meborc on 2011-09-19
> **Framli said:**
> Hi unknow04,
maybe there is something wrong with your display manager, so try:
```
sudo stop lightdm
sudo start ligthdm
```

you also might need to reconfigure light-dm first ```
sudo dpkg-reconfigure lightdm
```
and then ```
sudo service lightdm restart             OR
sudo service lightdm start
```

---

