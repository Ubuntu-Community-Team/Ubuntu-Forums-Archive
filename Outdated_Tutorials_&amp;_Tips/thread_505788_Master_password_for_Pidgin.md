---
title: "Master password for Pidgin"
date: 2007-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by jmazzarelli on 2007-07-20
Pidgin stores you passwords in plain text in ~/.purple/accounts.xml. At home, I am fine with this, but on a computer that is not mine (like at work), I am less comfortable with this. Someone can easily boot into recovery mode while I am away and find my passwords in plain text.

There is a patch for Gaim at [http://dooglus.rincevent.net/gaim/](http://dooglus.rincevent.net/gaim/) . Attached is a patch for Pidgin.

In order to use the patch, you will need a couple libraries and development headers.
```
sudo apt-get install libnspr4-0d libnss3-0d
sudo apt-get install libnss-dev libnspr-dev
```

Download the source from [http://pidgin.im/pidgin/download/source/](http://pidgin.im/pidgin/download/source/) if you haven't already, and unzip it.
Download the patch into the same directory and do the following
```
tar xf master-password.patch.tar
patch -p 1 < master-password.patch

```

You should be ready to configure, make, and install as normal.
```
./configure
make && sudo make install
```

When you launch pidgin, you will see a new tab in the preferences called "security". You can set a master password there. The link above has screenshots. After configuring, you should notice that the accounts.xml file now has gibberish where there once were passwords. This has been tested on Kubuntu 7.04

To remove pidgin, run the following from the directory in which you built pidgin:
```
make uninstall
```

---

### Post by jmazzarelli on 2007-08-08
Same patch works for version 2.1.0 as well.

---

### Post by jmazzarelli on 2007-08-21
The patch also works for 2.1.1. It will warn you about offsets, but it handles itself fine and works as expected.

---

### Post by H4ck3rx on 2008-02-26
How about Pidgin 2.3.1?

---

### Post by Schok on 2009-03-17
i managed to patch it but how do i configure, make and install it?

it will just say no such file or directory..sry newbie here..

---

