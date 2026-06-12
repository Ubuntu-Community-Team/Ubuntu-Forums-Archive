---
title: "Live CD Lubuntu fails"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by Clawinus on 2012-03-11
I tried to run the Live CD with Lubuntu and did not get very far.
The system failed with some error messages on the screen.
I photographed the screen and attach the photo to this message.
What do the numbers mean which are located in front of the error messages?
Can some body help to get over this?


[ATTACH]214132[/ATTACH]

---

### Post by ajgreeny on 2012-03-11
It looks as if this is a hardware or network/modem problem of some sort. What is the hardware you're using?

---

### Post by Guilden_NL on 2012-03-12
This error likely can be fixed by adding a parameter to the kernel line before booting. 
In your case it is probably "nomodeset" or "nomodeset noapic".

A good place to start is with this How To: [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Once you've done that, I suspect that your problem will be gone and you'll be enjoying Lubuntu straight away!

---

### Post by Clawinus on 2012-03-12
ajgreeny asked for my hardware.
attached is a PDF file with the listing of mt Windows hardware list
Device Manager.
It is a fairly standard desktop HP Pavilion.

---

### Post by NikTh on 2012-03-12
Hi , 
Except those kernel options that Guilden_NL suggest you (I agree off course) , you can try the alternate iso install . --> [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall) (No graphic enviroment , and internet connection needed) . 
Good luck.

---

### Post by varunendra on 2012-03-12
> **Clawinus said:**
> What do the numbers mean which are located in front of the error messages?
Those represent the time (in seconds) at which those events occurred.

Apart from 'nomodeset', you may try other boot options as well: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You should also check the integrity of both the downloaded iso and the burnt CD: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Usually, if the disc integrity is okay, then the additional boot options should be enough to let you boot on any hardware. The 'Alternate' iso is mainly intended to bypass the graphics and low RAM issues 'during' installation. Although it does help in certain compatibility issues in live CD, it would be best if you could run a live session (even if it is in low graphics mode with 'nomodeset') first to ensure that your hardware is working satisfactorily with Ubuntu.

---

### Post by Clawinus on 2012-03-12
According to the suggestion of Guilden_NL I started the Live CD of Lubuntu again with just the boot option Nomodeset. Success!.
Many thanks.
I installed two packages from Synaptic, works well.

---

