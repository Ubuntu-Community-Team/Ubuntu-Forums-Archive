---
title: "Kubuntu 16 not seeing CD/DVD ?"
date: 2016-09-28
forum: New to Ubuntu
---

### Post by Greg Mueller on 2016-09-28
Setting up a used Optiplex 760 with Kubuntu 16 for my mom to try out. 
Finally got it to boot from the SSD drive but it's not showing the CD/DVD unit.
Not 100% sure the player is good as I just bought this unit without a hdrive/operating system from a computer recycler.

Can someone suggest some experiments to try?
Looked at Fstab (saw that while searching the net) but the lines in Fstab are pretty cryptic (to me)

Help?

---

### Post by Greg Mueller on 2016-09-28
Update....

The drive will correctly read a CD and when there is a CD in it it will show in Dolphin
But it does not like DVDs. I originally tried the Kubuntu 16 install disk and it was a no go. Then I tried the CD. Then I tried a commercially made DVD (movie).
Maybe it needs some kind of driver????

---

### Post by Tadaen_Sylvermane on 2016-09-28
Install the libdvdread4 and libdvd-pkg packages and follow the prompts. Should help with commercial dvds

---

### Post by Greg Mueller on 2016-09-28
Can you tell me the syntax for that?

---

### Post by #&amp;thj^% on 2016-09-28
As Tadaen_Sylvermane sugested Install it by

```
sudo apt install libdvd-pkg libdvdread4
```

and follow on-screen directions.


> In some countries, the use of the below unlicensed decryption software is not permitted by law. Verify that you are within your rights to use it.
And others use this method for 16.04
1. Open terminal from App Launcher or via Ctrl+Alt+T keys. When it opens, paste the command below and hit run to install libdvdread and other required codecs:

```
sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg

```

2. Run command and confirm in order to install libdvdcss2 library:

---

### Post by Greg Mueller on 2016-09-28
I think the drive must just be bad. It works for CDs but not DVDs no matter what I have tried. Even redid the bios.
Not that I used a player that much except for updates and big storage jobs.

---

### Post by oldos2er on 2016-09-28
```
sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by mastablasta on 2016-09-29
> **Greg Mueller said:**
> I think the drive must just be bad. It works for CDs but not DVDs no matter what I have tried. Even redid the bios.
Not that I used a player that much except for updates and big storage jobs.
new DVD drive is quite cheap if you need it. it's possibel that laser for DVD is ruined?! had something similar on one of the drives.

regarding the install you can also just use the software center or whatever is now called in Kubuntu (it used to be muon).

---

### Post by Greg Mueller on 2016-09-29
I ordered one off of ebay used. Couldn't find a new one.
I had good luck with using a bootable DOS usb thumb drive for the bios update, so maybe I'll think in that direction.

---

### Post by Greg Mueller on 2016-09-30
That was it!
Bad player.
New/used one fixed it. $8 on Fleabay

---

### Post by DuckHook on 2016-09-30
> **Greg Mueller said:**
> That was it!
Bad player.
New/used one fixed it. $8 on FleabayGood for you Greg. As an old-hardware hound myself, successful HW resurrection stories likes yours are just heartwarming.

FWIW, the lasers in DVD/CD drives degenerate with time. This is a common topic for help on these forums and usually cause an inordinate amount of grief scrounging around the OS before the problem is eventually traced to HW.

Congratulations!

---

