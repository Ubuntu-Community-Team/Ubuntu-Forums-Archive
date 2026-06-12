---
title: "MSI RTX 2060 gaming x software?"
date: 2024-10-18
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-18
Heyo guys.

MSI RTX 2060 gaming x, is there a software that I can use to control fan curves and RGB on this card?

---

### Post by Perfect Storm on 2024-10-18
Have you tried OpenRGB, it's available as a flatpak.

---

### Post by shadowtabby on 2024-10-18
Hey.  No

How do I install it?  How do I use it?

---

### Post by shadowtabby on 2024-10-19
I cannot seem to create a new post. To ask for help about installing davinci resolve.

Oh now I can.

---

### Post by Perfect Storm on 2024-10-19
```
sudo apt install flatpak
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

Reboot.


```
flatpak install flathub org.openrgb.OpenRGB
```

---

### Post by shadowtabby on 2024-10-19
Heyo,

Thankies, I have done the 1st 3 and now doing the last.

The first 2 said it was done but I didnt reboot between set one and the last part you said.  Should be ok right?  I will reboot after this.

---

### Post by shadowtabby on 2024-10-19
Heyo,

i just tried it and it does nothing for my MSI card.

---

