---
title: "Cant install the .bin file"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by crazyjordan on 2008-06-01
[SOLVED]

hi i cant install a program its the steam dedicated server file wich is a .bin when i click on it , it says there isnt a program for the file and i tryed installing with the command prompt but whatever i try it just says cannot find the file "hldsupdatetool.bin"

if you need any more info just ask, thanks.

---

### Post by Rocket2DMn on 2008-06-01
You need to set executable permissions on the file first
```
chmod +x hldsupdatetool.bin
./hldsupdatetool.bin
```

---

### Post by SunnyRabbiera on 2008-06-01
instlling applications in ubuntu is different then in wondows, please see this guide:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by shifty_powers on 2008-06-01
think you need to change it to an executable first.

iirc

```
sudo chmod a+x *package name*
```

when you are in the right path in the terinal.

or think you can do it through right clicking the bin file and going to properties...

---

### Post by crazyjordan on 2008-06-01
i tried all of these but i just get cannot access hldsupdatetool.bin no such file or directory. its on the desktop.

this is it asactly:
jordan@jordan-desktop:~$ sudo chmod a+x hldsupdatetool.bin
chmod: cannot access `hldsupdatetool.bin` : no such file or directory

---

### Post by Rocket2DMn on 2008-06-01
Your first command needs to change your directory so that the terminal is looking at the desktop (where you saved the file)
```
cd ~/Desktop
chmod a+x hldsupdatetool.bin
./hldsupdatetool.bin
```
Note that Desktop has a capital D, case matters in linux.

---

### Post by crazyjordan on 2008-06-01
Thank you so much! this has solved my problem and il note this for the future thank you so much =)

---

