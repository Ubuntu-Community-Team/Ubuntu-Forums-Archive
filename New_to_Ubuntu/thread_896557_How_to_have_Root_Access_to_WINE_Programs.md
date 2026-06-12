---
title: "How to have Root Access to WINE Programs?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by JazonEsti on 2008-08-21
I used this [handy utility](www.ssclg.com/epsone.shtml) in Windows. I can't seem to get it to work in WINE. It installs and runs but can't seem to access the printer (no ink levels reported). I had a similar problem with Stylus Toolbox, and solved it by adding gksudo in the launcher. The same trick doesn't seem to work with SSCserve, though. 

Can anyone help me?

If it helps, the launch is 

```
env WINEPREFIX="/home/jason/.wine" wine "C:\Program Files\SSC Service Utility\ssc_serv.exe"
```

Thanks!

---

### Post by ilrudie on 2008-08-21
Its probably looking for the windows drivers for the printer.  They aren't there so I doubt root access is going to help.

---

### Post by JazonEsti on 2008-08-23
I just want to try. It might be worth it.

---

### Post by eightmillion on 2008-08-23
Have you tried:
```
env WINEPREFIX="/home/jason/.wine" gksudo wine "C:\Program Files\SSC Service Utility\ssc_serv.exe"
```?

---

### Post by JazonEsti on 2008-08-23
I tried that, but no information about printer levels is reported. Ilrudie is probably right: it seeks the Windows driver. 

So the next question is: is it safe to install WinXP drivers using WINE perhaps?

---

### Post by eightmillion on 2008-08-23
You can't install drivers in wine. Well, maybe you could, but they wouldn't do anything. They certainly wouldn't interact with the hardware. Is your printer working other than that utility?

---

### Post by LordDelta on 2011-01-23
This might not be the correct place for this...

But I just wanted to say, this helped me in installing NOOKstudy, so it apparently works.

---

### Post by Elfy on 2011-01-23
Closing old thread.

---

