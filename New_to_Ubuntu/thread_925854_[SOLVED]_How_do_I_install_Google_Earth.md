---
title: "[SOLVED] How do I install Google Earth?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Drakkor on 2008-09-21
Yeah, I just downloaded google-earth which is a .bin file, but don't know how to install it ! thanks :)

---

### Post by mikewhatever on 2008-09-21
Have a look [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by acidsolution on 2008-09-21
change the permission of the file to executible
```
 chmod 777 filename.bin 
```
and than 
```
./filename.bin
```

this must help

---

### Post by mailtwogopal on 2008-09-21
Hi all, 

 i searched regarding Google Earth and found this thread. i followed the steps from [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) and successfully installed google earth in my ubuntu hardy box. But whenever i open "Googleearth" thru Apps - Internet - Googleearth, i am getting initializing screen but after that my PC automatically migrating to login screen which appears as at time of booting machine. I tried 4 times to open google earth but it went in vain. Can anybody help me on this?

---

### Post by Drakkor on 2008-09-21
Thanks, mikewhatever, got it ! :)

---

### Post by billgoldberg on 2008-09-21
Mark as solved please.

--

For future readers of this thread, Google Earth is in the Medibuntu repo.

To install Google Earth with one command, use this command in a terminal (applications -> accessories -> terminal) 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install googleearth
```

Afterwards it will be in the applications menu.

Or you can launch it by pressing "alt + f2" and then entering "googleearth" (without the " "). Or use this command in a terminal

```
googleearth &
```

---

### Post by ibizatunes on 2008-09-21
system > admin > synapitc > google and you can install google earth, if you have the right repos enabled

---

