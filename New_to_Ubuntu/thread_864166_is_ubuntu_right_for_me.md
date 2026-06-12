---
title: "is ubuntu right for me?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by eyebrow on 2008-07-19
i have a pretty old Dell inspiron 8200:

pentium 4 1.7 GHz
768 mb ram
whatever the standard graphics card is

will I be able to run ubuntu 8 or should i choose an earlier version?

---

### Post by Canis familiaris on 2008-07-19
> **eyebrow said:**
> i have a pretty old Dell inspiron 8200:

pentium 4 1.7 GHz
768 mb ram
whatever the standard graphics card is

will I be able to run ubuntu 8 or should i choose an earlier version?

Ubuntu Hardy will work great.
What are your graphics?
If you can mention them, I could tell whether you'll be able to run Compiz. Most probably you could.

In Windows:
```
dxdiag
```
In Linux:
```
lspci | grep VGA
```

---

### Post by Karlos on 2008-07-19
Try the live CD and see if it works... if it does hit INSTALL..

---

### Post by UbuntuNerd on 2008-07-19
What are you using the pc for just to get online?

---

### Post by lswb on 2008-07-19
That system will work fine. I have hardy installed on a 650Mhz P3 laptop with 512MB memory, and it works without any problems. (no compiz of course due to graphics limitations)

---

### Post by eyebrow on 2008-07-19
wow, thanks for all the replies.  heres the graphics info:

Card name: Dell 8200
     Manufacturer: NVIDIA
        Chip type: GeForce2 Go
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0112&SUBSYS_00D41028&REV_B2
   Display Memory: 32.0 MB
     Current Mode: 1024 x 768 (32 bit) (60Hz)
          Monitor: Default Monitor
  Monitor Max Res: 
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0010.4482 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 6/24/2003 18:32:00, 3343051 bytes


ill just be using it for getting online and schoolwork.  maybe play some games like monopoly and backgammon.  let me know what you guys think.  i think im just going to try it out though and see what happens.  i guess my real question is should i try an older version?

---

### Post by bumanie on 2008-07-19
Hardy should work OK, but 32mb graphics card is pretty slow. Don't enable compiz IMO - it would probably cause more problems than it's worth. Should be able to play the games you mention though.

---

### Post by Vorian Grey on 2008-07-19
> **Karlos said:**
> Try the live CD and see if it works... if it does hit INSTALL..

Yeah, that's what I use to see if any distro will work on my computer. If the LiveCd works, it will usually work for you. 

8.04 should work for you according to your specs. :)

---

### Post by Gamma746 on 2008-07-19
> **Karlos said:**
> Try the live CD and see if it works... if it does hit INSTALL..

Just keep in mind that the LiveCD will be *significantly* slower than a real install, especially in terms of startup time.

---

### Post by Canis familiaris on 2008-07-19
I think Ubuntu will run very well in your system. I am not sure about Compiz (i.e. Extra effects). Try increasing the shared graphics RAM size to 64MB and see whether it helps.
But you as such do not need Compiz, so Ubuntu will run great and you'll enjoy it. :)

---

