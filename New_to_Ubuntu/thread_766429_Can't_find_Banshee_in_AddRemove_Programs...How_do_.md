---
title: "Can't find Banshee in Add/Remove Programs...How do i apply this command?..."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Foghornleghorn on 2008-04-25
sudo apt-get install banshee

Thanks in Advance.
regards,
Foghornleghorn.

---

### Post by FredB on 2008-04-25
In add/remove, look at the center top. You will have list. Select "all available applications" and do you search again.

---

### Post by philinux on 2008-04-25
Applications>Accesories> choose Terminal 

Enter the command there. It will ask for you password. Just type it and press enter. note you password will not appear as you type it.

Or use synaptic package manager and install it from there.

---

### Post by kpkeerthi on 2008-04-25
1. Enable universe and multiverse repositories under System -> Admin -> Software Sources
2. Then run this command in Application -> Accessories -> Terminal
```
sudo aptitude --with-recommends install banshee
```
This should get you banshee along with the recommended codecs.

---

### Post by SunnyRabbiera on 2008-04-25
right or use synaptic as suggested.
Synaptic is a more advanced tool then add/remove.
it is located in system> administration> synaptic.

---

### Post by Foghornleghorn on 2008-04-25
Sweeeeet....Thanks all now installed and working ok.:guitar:

Foghornleghorn.

---

