---
title: "Fails to load at 'checking battery state'"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Mr T1000 on 2012-01-12
My current hardware.....  AMD64 1050T Hex core cpu ASUS M5A99X-EVO motherboard 16Gbs of Corsair XMS RAM 850 PSU NVidia 430 GPU (Palit with 2Gbs of GPU RAM)..  Running 11.10 64bit... Been pretty flawless, unitil recently where it stops on the line checking battery state....  I have googled the issue, I have taken all the advice on blogs and this forum and it stiil does  it....  The list includes Removing and reinstalling the nvidia module... As above with light DM Switching to GDM still does it... Tried with an ATI card still does it.. Restarted X Restarted LDM  Etc. etc. etc... I am at a loss with this one.... For the first time in years, Ubuntu has become unstable....

---

### Post by androssofer on 2012-01-12
> **Mr T1000 said:**
> My current hardware.....  AMD64 1050T Hex core cpu ASUS M5A99X-EVO motherboard 16Gbs of Corsair XMS RAM 850 PSU NVidia 430 GPU (Palit with 2Gbs of GPU RAM)..  Running 11.10 64bit... Been pretty flawless, unitil recently where it stops on the line checking battery state....  I have googled the issue, I have taken all the advice on blogs and this forum and it stiil does  it....  The list includes Removing and reinstalling the nvidia module... As above with light DM Switching to GDM still does it... Tried with an ATI card still does it.. Restarted X Restarted LDM  Etc. etc. etc... I am at a loss with this one.... For the first time in years, Ubuntu has become unstable....

i had this same issue. was when i used the nvidia graphics driver. i removed my x.conf file and it worked.. not sure if you've tried this...

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

note this just renames the x.conf file so if it doesnt work you can change it back and your no worse off...

to put it back:

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by Mr T1000 on 2012-01-12
Yeah, remove X.conf file and replaced it.. I have also reinstalled 64bit and tried 32bit with the same issue... Have tried the following graphics cards....
nVidia 430
nVidia 9500GT
nVidia 460
nvidia 8600GT

ATI 4850
ATI 5450

It happens on them all...

To me if a reinstall (clean) doesn't resolve it, it should be a bug, which it is according to the bug log, but has been 'resolved' when it hasn't...

I am seriously considering jumping the Ubuntu ship at the moment...:(

---

