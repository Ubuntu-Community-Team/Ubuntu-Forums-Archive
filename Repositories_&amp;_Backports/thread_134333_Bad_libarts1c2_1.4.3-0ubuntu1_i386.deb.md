---
title: "Bad libarts1c2_1.4.3-0ubuntu1_i386.deb"
date: 2006-02-21
forum: Repositories &amp; Backports
---

### Post by bb002 on 2006-02-21
I'm following a howto to install a pvr-350 and mythtv. I've made it to the point that i install mythtv. however apt-get gives the error ```
Get:1 http://archive.ubuntu.com breezy/main libarts1c2 1.4.3-0ubuntu1 [1178kB]
Fetched 558B in 0s (2945B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
I've followed the steps it lists there but they didn't work. so I pointed firefox to [http://archive.ubuntu.com/ubuntu/pool/main/a/arts/](http://archive.ubuntu.com/ubuntu/pool/main/a/arts/). That says the file is supposed to be 1.1MB but the file I receive is only 558Bytes. I decided to check the contents of the file and this is what it contained ```
<br />
<b>Warning</b>:  Unexpected character in input:  '' (ASCII=2) state=1 in <b>/u01/ftpubuntu/pub/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb</b> on line <b>901</b><br />
<br />
<b>Warning</b>:  Unexpected character in input:  '' (ASCII=21) state=1 in <b>/u01/ftpubuntu/pub/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb</b> on line <b>901</b><br />
<br />
<b>Parse error</b>:  syntax error, unexpected T_STRING in <b>/u01/ftpubuntu/pub/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb</b> on line <b>901</b><br />

```

Since this is the only place i know to post these types of errors. I can't contact someone that is able to fix this....

---

### Post by bb002 on 2006-02-21
Well I just got it to work.

had to do a few things though. seems the issue is on the http side of things...

```

cd /var/cache/apt/archives
sudo wget ftp://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2_1.4.3-0ubuntu1_i386.deb

```
now my "apt-get install" worked...

No idea why it failed on that one deb file it downloaded 35 of 36 files without a hitch.

---

