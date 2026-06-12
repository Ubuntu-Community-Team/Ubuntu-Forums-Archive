---
title: "Changing operating system to Ubuntu 14.04"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by lewis4 on 2014-07-27
Hello!

I have recently just brought 3 second have racks which I would like to use you hosting Game server such as Minecraft, TF2 etc etc etc. But I am having some problems, I have installed the Ubtuntu 14.04 Iso onto a DVD-R (I am assuming that means a only writeable disc) and put it into the **** drive of one of my computers, I pressed F12 and Ubuntu started to load up, but when I click "Install Ubuntu" my screen says "Out of range" or it just disconnects from the Screen like it's restarting or something. I don't know what's wrong with it. Is it because it is wiping the hard drive as the previous owners forgot to wipe the hard drive?

Thanks,
Lewis

---

### Post by chris262 on 2014-07-27
I would have tried booting from USB instead, or perhaps check the ISO for defects. I had an issue where I could not use the keyboard once the language screens pops up, tried everything from changing hardware, to downgrading from 14.04 to 12.04, which finally got me through the install.

---

### Post by grahammechanical on 2014-07-27
Out of range is referring to the monitor video setting. That is my guess. Did you run a live session? Have you used the live session to test if all your hardware is compatible? This is what the installer will show you before it gets to the part where it formats something.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

The installer will only wipe the disk if we choose the option to Erase the Disk and Install Ubuntu. See the image for Installation Type .

Do any of these computers have a video adapter card? If they are "racks" they may be from a server set up without a video card. Or you may need to use the nomodeset boot parameter. 

See section 6 - F6

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards.

---

### Post by oldos2er on 2014-07-27
What are your hardware specs, particularly graphics card?

---

