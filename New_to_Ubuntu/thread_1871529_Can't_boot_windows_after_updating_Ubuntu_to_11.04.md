---
title: "Can't boot windows after updating Ubuntu to 11.04"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by jsosa01 on 2011-10-29
So I have windows vista in my computer and then I installed Ubuntu, it was an old version so it needed to be updated, when I updated I boot into Linux and everything work fine but the wireless, it doesn't work so I was going to boot into windows to check for an answer but when I selected windows sda1 it just goes to a black screen and with a flashing line for a while until my computer shuts down about 30 minutes, I don't know if is grub or something so please help me.

---

### Post by Mark Phelps on 2011-10-29
Was Vista able to work , after you installed Ubuntu, but before you did the Ubuntu update?  OR has it only failed since you did the Ubuntu update?

---

### Post by nogoodnamesleft on 2011-10-29
Do you see Vista attempting to start? the vista boot loader (black text on a white screen saying 'starting' - I dont remember the exact wording of it and I can't be bothered to look it up or boot it to check). If not that's probably a partition issue caused by the install.

If you do see Vista starting (The starting windows... etc, white text on a black screen) that's probably Vista broken.

edit - you say an old vesion of ubuntu which was then upgraded TO natty?  I *vaguely* remember a problem with the install of either maverick or lucid breaking windows by doing something it shouldnt to the partition table. Can you please provide more information? What version of ubuntu and what EXACTLY do you see on the screen?

---

### Post by jsosa01 on 2011-10-30
Okay so I had Ubuntu 10 when I installed as a dual partition with my windows vista, I never checked if vista worked before upgrading it. What I see after I choose the windows vista partition is a black screen with a flashing line but I can't write anything and I dont see anything else. I think it has something to do with grub because when I installed Ubuntu grub went into grub rescue and I had to get into Ubuntu live cd install boot repair and repair grub after that it all boot well until the poit where I had to choose Ubuntu or windows

---

### Post by nogoodnamesleft on 2011-10-30
Am sure this is grub, becuase it appears the vista boot loader isnt being called, i recommend the installation subforum. I dont remember how to fix grub as I dont use it.

---

### Post by oldfred on 2011-10-30
We really need to know what is where, from Ubuntu install or liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by rng on 2011-10-30
You should bakup your data since you may lose data/partitions while trying to correct the problem.

The command 'sudo update-grub' run from linux terminal is generally mentioned for correcting the grub entries.

---

### Post by Sef on 2011-10-30
>  ...I installed Ubuntu, it was an old version so it needed to be updated....

> Okay so I had Ubuntu 10 when I installed....

What version exactly did you have: 10.04 or 10.10?

---

### Post by verymadpip on 2011-10-30
sorry it's already been said.

---

