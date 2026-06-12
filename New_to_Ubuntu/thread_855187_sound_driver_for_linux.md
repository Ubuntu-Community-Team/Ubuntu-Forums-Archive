---
title: "sound driver for linux"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by alien8predator on 2008-07-10
How do I install a sound driver for my soundcard if I can't find a linux driver on the manufacterer's website? Are there alternative drivers or standard linux sound drivers I can use for it?

Sweex 5.1 PCI Sound card



and samething from my usb headset:  ClearChat Pro usb

---

### Post by billgoldberg on 2008-07-10
> **alien8predator said:**
> How do I install a sound driver for my soundcard if I can't find a linux driver on the manufacterer's website? Are there alternative drivers or standard linux sound drivers I can use for it?

Sweex 5.1 PCI Sound card



and samething from my usb headset:  ClearChat Pro usb

Don't know about the sound card, but I **might** be able to help with the headset.

After you plugged it in, go to "system -> preferences -> sound" and look if your usb headset is recognized in on of the bottom drop-down boxes.

If it is listed there, click [this link]("http://linuxowns.wordpress.com/2008/07/08/how-i-got-my-usb-headset-to-work/") to get it working.

If not, can't help.

---

### Post by brian_p on 2008-07-10
> **alien8predator said:**
> How do I install a sound driver for my soundcard if I can't find a linux driver on the manufacterer's website? Are there alternative drivers or standard linux sound drivers I can use for it?

Sweex 5.1 PCI Sound card

snd-cmipci.ko should be on your machine. Apparently it is the module to use with the card.

```
sudo lsmod | grep snd-cmipci

```

tells you if it loaded and ready to use.

```
sudo modprobe snd-cmipci
```

loads it into the kernel.

---

### Post by alien8predator on 2008-07-10
I had no succes on the headset, but that probably has to do with the fact that my soundcard isn't working yet. Could there be a complication since I running ubuntu on vmware server until I get totally adjusted to it? but I tried running  the code in the terminal but doesnt doe anything?just asks me for a password verification and then it doesnt do anything.

---

