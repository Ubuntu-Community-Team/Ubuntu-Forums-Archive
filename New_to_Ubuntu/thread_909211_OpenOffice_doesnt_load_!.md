---
title: "OpenOffice doesnt load !"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by medya on 2008-09-03
my kubuntu is fresh, open office used to work fine, but now I click on it and the OpenOffice Splash appears , but it doesnt load, 
I tried to do it in Konsole and here is the message  :
> ~$ ooffice -writer %U
/usr/lib/openoffice/program/javaldx: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
/usr/lib/openoffice/program/soffice.bin: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64


---

### Post by Pro-reason on 2008-09-03
I have no idea why that is happening.  I can only suggest reinstalling.

```

sudo apt-get purge openoffice.org-writer
sudo apt-get install openoffice.org-writer

```

You could also try AbiWord.

```

sudo apt-get install abiword

```

Or else use LaTeX.

---

### Post by medya on 2008-09-03
I had re-installed and even upgraded it, it doesnt fix it .

and by the way my Strigi Search on kubuntu is broken too , 
strigi on Konsole gives this msg :
> 'kfmclient' exec strigi:/
kfmclient: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Error loading 'kio_strigi'.
kfmclient:
kio (KRun): ERROR: 0x68f4a0 ERROR (stat) : 3 Could not start process Unable to create io-slave:
klauncher said: Error loading 'kio_strigi'.

and firefox crushes when I try to download a file .

it seems my kubuntu Broke down by a virus . !

---

### Post by clive littlewood on 2008-09-03
Hi

I dout whether you have a virus !!

It would appear you probably have corrupted files in your os.

I would back up any data you need and re-install Kububtu.


Hope everything works

Cl

---

### Post by Pro-reason on 2008-09-03
Create a new user, and then log in as that user.  Do you get the same errors?

---

### Post by medya on 2008-09-03
Pro-reason
I created a new user and I still have the same problem .


clive littlewood 
no I am not gonna install a new kubuntu, I installed it just last week and I didnt do anything stupid or strange on it. so it is pretty fresh.

---

### Post by medya on 2008-09-03
here is the error message when I run Strigi search
> could not start process Unable to create io-slave:
klauncher said: Error loading 'kio_strigi'.

---

### Post by medya on 2008-09-03
here is the error message when I run Strigi search
> could not start process Unable to create io-slave:
klauncher said: Error loading 'kio_strigi'.

---

### Post by medya on 2008-09-04
hey Guys each day another program gets corrupted , today kaffeine stoped working
here is the error message of kafeine when I try to play a video
> 
kaffeine: symbol lookup error: /usr/lib/libxine.so.1: undefined symbol: gzopen6

---

### Post by Pro-reason on 2008-09-04
> **medya said:**
> hey Guys each day another program gets corrupted , today kaffeine stoped working
here is the error message of kafeine when I try to play a video

I don't understand what could have happened.  I would just reinstall.

---

