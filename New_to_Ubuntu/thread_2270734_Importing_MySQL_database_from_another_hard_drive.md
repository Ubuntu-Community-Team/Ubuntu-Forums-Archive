---
title: "Importing MySQL database from another hard drive"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by di0xide on 2015-03-25
I take out my new hard drive with Ubuntu 14.04 64-bit installed from my new laptop because of video chipset problem. Now I am using the old laptop of my friend for programming with Ubuntu 10.04 32-bit. Unfortunately, i didn't export the database from my new laptop. I have already tried booting Ubuntu from an external hard drive using USB connection. I am thinking of booting the new hard drive on my old laptop and export the database but right now I cannot boot the new hard drive since the laptop that I am using is already old and cannot boot 64-bit OSs. Does anyone know how to import MySQL database with my situation? Thanks...

---

### Post by nerdtron on 2015-03-25
Setting compatibility from different mysql versions aside, you can accomplish this by stopping mysql, then copy the old mysql folders and just paste them on the new location/hard drive mysql folder, then just start mysql again.

Just make sure the the ownership of the files/folders inside mysql are owned by mysql, so after copying the folders, run
```
sudo chown -R mysql:mysql /var/lib/mysql 
```

---

### Post by Vladlenin5000 on 2015-03-25
Hello and welcome.

Here are a few suggestions: [http://www.itworld.com/article/2833078/it-management/3-ways-to-import-and-export-a-mysql-database.html](http://www.itworld.com/article/2833078/it-management/3-ways-to-import-and-export-a-mysql-database.html)

---

### Post by steeldriver on 2015-03-25
You could use a LiveUSB to mysqldump the data off the new HDD if it's not bootable.

---

### Post by SeijiSensei on 2015-03-25
I had success using the same technique nerdtron describes.  Copy /var/lib/mysql from the old drive to the new one and start MySQL.

OP, I suggest you start running a daily backup using mysqldump.  Here's a copy of the script I wrote for this purpose: [http://ubuntuforums.org/showthread.php?t=2218776&p=12997721&viewfull=1#post12997721](http://ubuntuforums.org/showthread.php?t=2218776&p=12997721&viewfull=1#post12997721)

---

