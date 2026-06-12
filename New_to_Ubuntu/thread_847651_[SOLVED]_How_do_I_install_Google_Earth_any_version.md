---
title: "[SOLVED] How do I install Google Earth any version."
date: 2008-07-02
forum: New to Ubuntu
---

### Post by PureRicanGringo on 2008-07-02
I downloaded version 4.2 of Google Earth because I understand that is the version that is supposed to work. Anyway, I click on it and nothing happens. I assume that is because it is a .bin file and here I need a .deb file or something right? Well, if anyone could help me figure out what is the next step I would appreciate it greatly.

---

### Post by tjwoosta on 2008-07-02
you can get google earth in the repository (the latest version in there is 4.3 but i think 4.2 is more stable)


system-administration-syaptic package manager  then search googleearth

(you should always get apps from the repositlry rather than the net, if available)

Edit: now that i think about it you may need the medibuntu repositories to get 4.3 

how to get medibuntu
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")


Rest of post removed   (dont pay attention to it im spacin it today)

---

### Post by Methuselah on 2008-07-02
You have to do:

```

sh GoogleEarthLinux.bin

```

In a terminal.
See [http://earth.google.com/support/bin/answer.py?hl=en&answer=44713](http://earth.google.com/support/bin/answer.py?hl=en&answer=44713)

But I also recommend you get it from the ubuntu repositories if possible.

---

### Post by spiderbatdad on 2008-07-02
Very easy to install. Download 4.3 from googleEarth...Save the file to your desktop.

Open a terminal, and make the file executable:```
cd Desktop
sudo chmod a+x GoogleEarthLinux.bin
```

Run the file:```
./GoogleEarthLinux.bin
```

---

### Post by bhadotia on 2008-07-02
Just install it from the repositries. Open a terminal Applications>Accessories>Terminal and copy ans paste this command:
```
 sudo apt-get install googleearth4.3

```
If you want the 4.2 version manipulate accordingly .

---

### Post by PureRicanGringo on 2008-07-03
Thanks, all. I appreciate it.

---

