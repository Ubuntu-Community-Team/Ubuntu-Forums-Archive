---
title: "Install hangs at wireless part."
date: 2013-09-11
forum: New to Ubuntu
---

### Post by naquan2 on 2013-09-11
I've tried to install Ubuntu twice but when it gets to setup wireless part and just hangs like the cursor turns into a circle thingy xD. I tried to install Ubuntu because my pc no longer has an OS. Its an ASUS R503U. Everything goes fine in test mode but when I try to actually install it just hangs... I've tried connecting to a wireless network and I've not connecting  it. I have no clue whats going on. PLEASE HELP!!:(:(

---

### Post by Panderz on 2013-09-11
Would it be possible to plug in a wired connection? When you boot to a livecd in Ubuntu, it loads a default driver for your wireless card. Seems like your card is having problems with that driver. 
You can boot into try Ubuntu instead of just going right to install and try to load the right driver manually and then install.

---

### Post by varunendra on 2013-09-12
> **naquan2 said:**
> Everything goes fine in test mode but when I try to actually install it just hangs...
Hi naquan2, Welcome to the forums !

What Panderz posted -
> **Panderz said:**
> Would it be possible to plug in a wired connection?
....
You can boot into try Ubuntu instead of just going right to install and try to load the right driver manually and then install.
..sounds a good question and a good suggestion to me.

When in Live (test) mode, please open a terminal (Ctrl+Alt+T) and post the output of following command -
```
lspci -nnk | grep -iA2 net
```

If it does not list your wireless card (or if you are not sure), please also post the output of -
```
lsusb
```

If you have a wired connection and it works, it would be best to NOT check the "Install Updates" and "Install Third party software" checkboxes while installing. You can install them later.

---

### Post by buzzingrobot on 2013-09-12
Just to be sure, can you enable wireless while using the LiveCD in test mode?

---

