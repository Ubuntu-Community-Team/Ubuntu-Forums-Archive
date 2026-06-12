---
title: "installation problems with windows xp"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by robert mcfarlane on 2008-05-04
hi, i am having problems installing ubuntu 8.04 inside windows.
i downloaded the iso, burned the image to cd, and the installation starts fine. it gets to the creating inage stage, runs right through till the end, 733.1mb, then it says cannot accesss disk, retry or cancel. every time i retry, the same thing happens. any ideas how i stop this, so i can complete the installation?

---

### Post by overdrank on 2008-05-04
> **robert mcfarlane said:**
> hi, i am having problems installing ubuntu 8.04 inside windows.
i downloaded the iso, burned the image to cd, and the installation starts fine. it gets to the creating inage stage, runs right through till the end, 733.1mb, then it says cannot accesss disk, retry or cancel. every time i retry, the same thing happens. any ideas how i stop this, so i can complete the installation?

HI and welcome, what do you mean installing within windows? Are you using Wubi for the installation? If you have downloaded the iso you can burn it to disc
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then you will boot your computer with the cd.

---

### Post by robert mcfarlane on 2008-05-04
i dont know what wubi is. i downloaded the iso, burned to disk, and a screen comes up with 3 options, demo and full install, or, install inside windows, or, learn more.

i click on the install within windows option, and have the problem i mentioned in the earlier post

---

### Post by kansasnoob on 2008-05-04
Does the install screen you start from look like this?

[http://content.zdnet.com/2347-12554_22-193586-193587.html?seq=1](http://content.zdnet.com/2347-12554_22-193586-193587.html?seq=1)

If so, and you're clicking on "Install inside Windows". you're using Wubi.

If that's the case then Wubi is not finding a continuous available space to install Ubuntu.

Before installing "inside" windows you should:

#1. Create a new restore point!
#2. Clean up!
#3. Defrag!
#4. Check things out, make sure everything is working OK and then create another restore point!
#5. Make sure you have enough available space for Ubuntu ........ I think at least 4GB unzipped if you plan on playing with it!

IMO dual booting is much preferable to using Wubi but the chance of data loss increases.

---

### Post by robert mcfarlane on 2008-05-04
well, everything works ok, i use my pc daily, disk doesnt need defragged, has 220Gb spare, so i think it might be a problem with the iso file.
i thought i was dual booting, maybe i'm being thick, but what i expected was to install inside windows, then next time i restarted, to get the option of booting windows or ubuntu.

if i'm having problems at this stage, and considering all the problems that i see people having to ask about on these forums, then maybe i better stick with windows.

---

### Post by robert mcfarlane on 2008-05-04
another thing, i was told by tiscali, my isp, that they dont support ubuntu, so looks like i wouldnt be able to get online, seems like a lot of hassle involved

---

### Post by Zralou on 2008-05-04
Leave the CD in the drive and restart windows, as long as your system is set to boot from CD, it should start the 'liveCD'.
You can then play around with Ubuntu without affecting anything on your system (it runs from the CD only), that way you can "try before you buy" so to say.
If you don't like it, just reboot, pop the CD out, and reboot back to windows as though nothing happened.

Sara Lou

---

### Post by robert mcfarlane on 2008-05-04
wont everything run much slower if its on the cd, rather than on a hard drive?

---

### Post by Zralou on 2008-05-04
Yes, but if you decide you like it, you can install to the hard drive from there.

Sara Lou

---

### Post by robert mcfarlane on 2008-05-04
that was the problem, i cant install it on the hard drive!

tha\nks anyway, but i think i just have to give up, until i get an alternative to windows which doesnt require a degree in computing to use.

---

### Post by Zralou on 2008-05-04
Linux does have a learning curve, just like any other OS.  As long as you are willing to work at it, the basics can be grasped fairly easily, the rest you learn as you go.  Be aware tho', it's not windows......

Sara Lou

---

### Post by daevyd on 2008-05-04
I'm also having problems installing Hardy Heron inside windows.  After Wubi installs and I reboot I'm unable to login.  It goes to the usual beige screen and then to black and back the login screen.  What the heck?  This is WAY frustrating!

---

