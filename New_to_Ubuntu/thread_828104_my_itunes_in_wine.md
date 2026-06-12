---
title: "my itunes in wine"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-13
I didn't know I didn't have freedom with the music I bought from itunes.  But I have quite a bit I want to bring to my Ubuntu partition.  I have Wine, but no idea how to manipulate it.  I also have an itunes account.  how does this work?
  I downloaded i tunes64.exe, then i right click it's icon > open with wine emulator , then nothing happens.

---

### Post by noobuntu_ger on 2008-06-13
copy the exe to your desktop and open the terminal. And use```

cd /home/user_name/Desktop
wine itunes64.exe
```
wine should do the rest and enjoy the music

---

### Post by adamogardner on 2008-06-13
here's what happened:

adamogardner@CRONUS:~$ cd /home/adamogardner/Desktop wine itunes64setup.exe
adamogardner@CRONUS:~/Desktop$

---

### Post by eriqjaffe on 2008-06-13
If you're going to enter all that on one line, it has to be:

```
cd /home/adamogardner/Desktop && wine itunes64setup.exe
```

Otherwise, enter the commands seperately as shown above.

Or just...

```
wine /home/adamogardner/Desktop/itunes64setup.exe
```

---

### Post by joshsmith on 2008-06-13
you want the non 64 bit version of itunes

---

