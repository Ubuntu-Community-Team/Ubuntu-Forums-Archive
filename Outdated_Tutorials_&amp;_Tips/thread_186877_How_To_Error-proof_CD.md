---
title: "How To: Error-proof CD"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Chris03 on 2006-06-02
Hey everyone. These steps will show how to do an error-free burn for people that are addicted to MD5 checksums. It applies to the Ubuntu Dapper Desktop CD:

1) Get the torrent here: [http://www.mininova.org/tor/327545](http://www.mininova.org/tor/327545)

2) MD5 should be: c73cb9d33b25f2263fe88cbc6f76d24d (it's the same as torrent.ubuntu.com:6969)

3) When you have the .iso finished, check the MD5 and it should be: e2e5e0bfb2edffd2ce02dd77bda4558e

4) Right click on the .iso and select "Write to disc" and finish the burn.

5) Type md5sum /dev/cdrom in a terminal and it should match the .iso

6) Install!

This is how to do an error-proof download/burn/verify of the CD =D> =D> =D>

---

### Post by mitja on 2006-06-06
> 5) Type md5sum /dev/cdrom in a terminal and it should match the .iso

When I tried to do step 5, I got an error message: "md5sum: /dev/cdrom: I/O error". I wonder why? It seemed like the md5sum program went through the CD normally (I heard the CD spinning couple of minutes), so I got this message after it had checked the CD, not immediately. I did this several times, but the result was always the same.

However, I found another instruction from Ubuntus official wiki for verifying installation CD: [https://wiki.ubuntu.com/HowToMD5SUM]("https://wiki.ubuntu.com/HowToMD5SUM")

It says there that you can use the supplied md5sum file on the CD, so just type

```
cd /cdrom
md5sum -c md5sum.txt | grep -v 'OK$'
```

and if the command outputs any errors, you'll know the burn was corrupted.

---

### Post by Chris03 on 2006-06-06
Cool! Seems a bit more complicated though and it doesn't check the MD5 of the CD as a whole. Maybe the I/O error was because I used CD-RW and you used CD-R, or you used a different type of drive? Only things I can think of.

---

