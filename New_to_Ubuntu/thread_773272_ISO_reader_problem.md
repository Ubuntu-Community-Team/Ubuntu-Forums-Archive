---
title: "ISO reader problem"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Shnooky on 2008-04-28
How do i mount an iso...or install diablo 2, but mostly mount an iso?
I have acetoneiso-6.7 but i dont no how to install it, i followed the instructions but it doesnt work so i could use some help

assistance need...thx

-shnooky

---

### Post by RealPSL on 2008-04-28
Assuming you have an iso my.iso, a simple way to mount an iso from the command line is to first create a directory to mount it to:

```
mkdir /var/tmp/myisomount
```

Then mount the iso to the directory created above with 

```
sudo mount -o loop -t iso9660 my.iso /var/tmp/myisomount
```

Enter your password as prompted at the terminal for the second command.

---

### Post by Sjovan on 2008-04-29
yeah, what he said...

Then you should tell the wine-config that /var/tmp/myisomount is the location of the cd-rom.

Any ways, if you take a look on [appdb.winehq.com]("appdb.winehq.com") then you would know that diablo doesn't work well with an iso. After you update, then it wont detect the "cd" any more.

---

### Post by bigken on 2008-04-29
applications add/remove search for gmount ISO and install

---

### Post by tliotis on 2008-04-29
i just instal gmount very nice !like daemon tools !

---

