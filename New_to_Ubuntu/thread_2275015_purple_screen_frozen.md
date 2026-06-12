---
title: "purple screen frozen"
date: 2015-04-23
forum: New to Ubuntu
---

### Post by pravhema on 2015-04-23
unable to use mouse and keyboard. When i boot and use ubuntu 14.04 on trial basis all works but the hard disk files unable to open. I just need to remove the files to an external harddisk so that i can reload ubuntu on my desktop. Appreciate some assistance.

---

### Post by pepsifx357 on 2015-04-23
If you're trying to read a Windows hard drive from Ubuntu you'll need to install the ntfs-3g package.

```
sudo apt-get install ntfs-3g
```

As far as the keyboard and the mouse, I would need more info.  What kind of computer, usb or PS/2, brand ect.

---

### Post by pravhema on 2015-04-24
i had a old pc running window xp...it was hanging and i decided to load ubuntu 12.10. I started to tfr videos and some photos to the 1T hard disk. Now it has frozen on a purple page. Unable to use mouse to start ubuntu or do the test. I tried removing the hard disk and inserting into a cover to make it a external disk to retrieve the saved file but i'm unable to open. I install ubuntu 14.04 on a trial basis and see the files but unable to open.

---

### Post by pravhema on 2015-04-24
How about reading a ubuntu hard drive from window??

---

### Post by sandyd on 2015-04-24
Have you checked if the HDD is damaged?

After starting up, post the output of
```

dmesg
```

---

