---
title: "[kubuntu] Skanlite does not start"
date: 2016-01-02
forum: New to Ubuntu
---

### Post by janjaromirhorak on 2016-01-02
Hi everyone,
I have the Canon PIXMA MP270 printer and scanner, but when I try to scan something the Scanning software does not start. I've tried Skanlite (I'm running Kubuntu 15.10) and xsane.

I've tried scanimage to see, if is the device properly connected and it seems to be:

> scanimage -L
device `pixma:04A9173B' is a CANON Canon PIXMA MP270 multi-function peripheral

And it can scan:

> scanimage -T
scanimage: scanning image of size 638x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1914 bytes...  PASS
scanimage: reading one byte...          PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...    PASS
scanimage: stepped read, 32 bytes...    PASS
scanimage: stepped read, 64 bytes...    PASS
scanimage: stepped read, 128 bytes...   PASS
scanimage: stepped read, 256 bytes...   PASS
scanimage: stepped read, 512 bytes...   PASS
scanimage: stepped read, 1024 bytes...  PASS
scanimage: stepped read, 2048 bytes...  PASS
scanimage: stepped read, 2047 bytes...  PASS
scanimage: stepped read, 1023 bytes...  PASS
scanimage: stepped read, 511 bytes...   PASS
scanimage: stepped read, 255 bytes...   PASS
scanimage: stepped read, 127 bytes...   PASS
scanimage: stepped read, 63 bytes...    PASS
scanimage: stepped read, 31 bytes...    PASS
scanimage: stepped read, 15 bytes...    PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS

Any advice?

(Sorry for my English.)

---

### Post by janjaromirhorak on 2016-01-02
Update: Now, about 10 minutes after trying to start Skanlite, it started and seems to work. Does anybody know if there there is any way to speed this up?

---

### Post by Geoffrey_Arndt on 2016-01-02
Do you have the "Simple Scan" program installed?

---

### Post by janjaromirhorak on 2016-01-02
I didn't have. Now I tried it, the program launches, but when I tried to scan something for the first time, I got an error saying "Can not connect to printer". When I tried for the second time, it suddenly started working (scanning).

---

### Post by Geoffrey_Arndt on 2016-01-02
That's not unusual for first time use . . . . shouldn't be a problem going forward now that device is registered.

Might not be a bad idea to mark thread as "Solved" so other new users can benefit.

---

