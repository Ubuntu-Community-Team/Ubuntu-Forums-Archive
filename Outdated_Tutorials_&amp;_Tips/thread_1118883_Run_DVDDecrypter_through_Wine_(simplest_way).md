---
title: "Run DVDDecrypter through Wine (simplest way)"
date: 2009-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by ajitem on 2009-04-07
I did read several threads having this tutorials and some solutions but they were too old to be bumped. Hence, I decided to make this one. 

First of all install Wine if you have not done so already. To do that, open the terminal and type following to get wine installed.

```

sudo apt-get install wine

```

Next step, install  DVDDecrypter  through wine and Open it.

You will be presented with the following in the log

```

I 22:08:39 DVD Decrypter Version 3.5.4.0 started!
I 22:08:39 Microsoft Windows XP Professional (5.1, Build 2600 : Service Pack 2)
I 22:08:44 Initialising SPTI...
I 22:08:44 Searching for SCSI / ATAPI devices...
W 22:08:44 No devices detected!
I 22:09:33 Searching for SCSI / ATAPI devices...
W 22:09:33 No devices detected!

```

After some fiddling with the program options, I got this...

```

W 22:10:37 I/O Interface has been changed!
I 22:10:37 Shutting down ASAPI...
I 22:10:37 Initialising ASPI...
I 22:10:37 Searching for SCSI / ATAPI devices...
I 22:10:39 Found 1 DVD-RAM/±RW!

```

All I did was go to Tools->Settings-> I/O and changed the mode from SPTI to ASPI ! That Simple.

---

