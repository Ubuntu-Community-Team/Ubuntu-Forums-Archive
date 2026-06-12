---
title: "CD/DVD drive and password issues"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by Colin AS on 2012-10-09
I am a complete beginner and have 2 problems. I installed ubuntu 12.04 LTS 32 bit on a packard bell desktop computer on  a newly reformatted hard drive. It mostly works brilliantly but the first problem is that the CD/DVD drive is not working - this must be some kind of installation/driver issue I think.
Second problem is that when i do ctrl alt F1 to access the command line it asks for a password for packardbell (computer name) but I didn;t set one up! If I try my login name i am unable to enter any characters as password.
Can anybody help at all?

---

### Post by mcduck on 2012-10-09
just type in your own password and press enter, it will work. The command line will not display anything on screen when typing in passwords (for security reasons).

I can't say much about the CD drive, though. Did you make the install using USB drive then? Have ytou tried the CD drive on another operating system, it's unlikely a CD drive would have any driver problems so it's worth making sure the drive ins't just broken...

---

### Post by audiomick on 2012-10-09
> **mcduck said:**
>  so it's worth making sure the drive ins't just broken...

First thing would be to open up the box and pull the cables out and re-plug them to make sure they are seated properly.
You might also want to blow out the dust if the computer is a bit older.

---

### Post by Colin AS on 2012-10-09
I did install from USB, however the DVD drive is working, I am able to boot AVG rescue CD

---

### Post by Colin AS on 2012-10-09
thanks mcduck
The only issue was that my username is Colin and it wanted colin with lower case "c"

---

### Post by Colin AS on 2012-10-10
The DVD drive definitely works, but I can't play a CD or DVD.
The eject command works. If I boot from DVD that works too.
When I put in a CD/DVD it fails to read.

---

### Post by androssofer on 2012-10-10
> **Colin AS said:**
> The DVD drive definitely works, but I can't play a CD or DVD.
The eject command works. If I boot from DVD that works too.
When I put in a CD/DVD it fails to read.

try:

```
sudo apt-get install ubuntu-restricted-extras
```

then do:

```
sudo apt-get install libdvdread4
```

and finally:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

then reboot and try playing the DVDs etc

---

### Post by Colin AS on 2012-10-10
Brilliant! I tried that and it is working.
thank you very much.

---

