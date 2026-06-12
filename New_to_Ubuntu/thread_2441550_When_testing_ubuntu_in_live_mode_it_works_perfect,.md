---
title: "When testing ubuntu in live mode it works perfect, but when I install it and login it"
date: 2020-04-24
forum: New to Ubuntu
---

### Post by jorgelpr on 2020-04-24
When testing ubuntu in live mode it works perfect, but when I install it and login it doesn't let me do anything, it is extremely slow. My PC has 4gb of RAM, 2.0 GHZ core i3 processor. HDD 500 GB. HP laptop. Please help.

---

### Post by VMC on 2020-04-24
From terminal type the following and see if there is long boot issue: ```
systemd-analyze blame
```

---

### Post by CelticWarrior on 2020-04-24
Welcome.

Your hardware is nothing to brag about, an old i3, the bare minimum RAM and a very slow HDD... Expectations should be set accordingly.

The above notwithstanding, during the first minutes after installing it is expected to be even slower than normal due to a lot of things happening in the background. Just wait some time and then make sure all updates are installed. Then, if you have a discrete Nvidia GPU you certainly want to install Nvidia drivers. Finally, the major bottleneck is the HDD. Replacing it with a modern SATA SSD will make a huge difference and if you can add more RAM, even better.

---

### Post by jorgelpr on 2020-04-24
It takes forever to open the terminal. And it shows pcieport error, PCIe bus error

---

### Post by CelticWarrior on 2020-04-24
> **jorgelpr said:**
>  And it shows pcieport error, PCIe bus error
Where? When?

---

### Post by jorgelpr on 2020-04-24
Excuse me, I'm a novice. On this same PC I have windows 10 installed and it is going very well. Any suggestion

---

### Post by jorgelpr on 2020-04-24
The error shows it when trying to open a window and it doesn't respond. Sometimes before logging in.

---

### Post by VMC on 2020-04-24
Those *pci* errors have been around for a long time. Add "pci=noaer" to the end of the linux line on grub.cfg to stop them. That way you can view "dmesg" without a ton of those errors.
Off hand I don't know the launchpad bug report of the *pci* errors.

---

### Post by jorgelpr on 2020-04-24
Thanks friends for your responses. I think it may be a hardware compatibility issue. I even tried Lubuntu and it is also super slow. I think I will want to have a dual boot.

---

### Post by CelticWarrior on 2020-04-24
It isn't a compatibility issue. Other than the quirks mentioned above about the error (and its simple solution), the main question remains unanswered: Do you have a Nvidia Graphics or not? If not, which graphics do you have?

---

### Post by jorgelpr on 2020-04-24
My PC has an Intel (R) HD Graphics 520. 2118MB.

---

### Post by jorgelpr on 2020-04-24
My PC has an Intel (R) HD Graphics 520. 2118MB.

---

### Post by CelticWarrior on 2020-04-24
> **jorgelpr said:**
> My PC has an Intel (R) HD Graphics 520. 2118MB.

So not that.
Intel graphics drivers are open-source and installed by default. Graphics such as yours just work. And everything else should work as well within re3alistic expectations. The current Ubuntu should have the same or better performance than Windows 10. If yours is so much different then something else is seriously wrong.

---

### Post by jorgelpr on 2020-04-24
That's what I do not understand. Because windows is going well. And no linux distro has wanted to work for me. They are well installed and everything. The problem is that they are not doing well. It moves in slow motion.

---

### Post by mc4man on 2020-04-24
What release of Ubuntu? You have a skylake chipset which had some issues  a ways back.
Almost sounds like you're using llvmpipe which can have terrible performance of older/weak cpu's.
If you can get to System settings > Details or About it would show.
If you can install inxi (sudo apt-get install inxi) then eventually run this, post results
```
inxi -CG
```

---

### Post by rbmorse on 2020-04-24
Used to be that you could not install Linux to a logical drive on an extended partition.  Is that still true?

---

### Post by CelticWarrior on 2020-04-24
> **rbmorse said:**
> Used to be that you could not install Linux to a logical drive on an extended partition.  Is that still true?

No, not the the case and never has been (for the second time) and I really don't know why you're commenting in multiple threads with this wrong information? And in this one in particular where - hopefully - the preinstalled Windows implies GPT?

---

