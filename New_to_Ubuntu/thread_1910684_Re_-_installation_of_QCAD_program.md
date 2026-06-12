---
title: "Re - installation of QCAD program"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by cliveT on 2012-01-17
Hi guys
I recently installed QCAD, I downloaded from website and saved to my desktop - then set permissions and then in the terminal I typed in Desktop/qcad then pressed tab to complete the command and all was well, I was up and running - no problems.

Then I accidentally removed QCAD, so I went through the same procedure but this time I get this error in the Terminal (this is with a new downloaded file to the desktop - the previous bin file is removed)

clive@clive-Inspiron-N5110:~$ Desktop/qcad-3.0.0-rc2-prof-linux.bin 
Verifying archive integrity...Error in MD5 checksums: 7f01d9117f2ec66deb42cc5d72515acc is different from fea5f97bde6f8847790cdbb66f06240c
clive@clive-Inspiron-N5110:~$ 


Please help

regards

Clive

---

### Post by lechien73 on 2012-01-17
Did you re-download the .bin file? This usually indicates an incomplete or corrupted download. A checksum is generated when the archive is created and, if it has changed, then it indicates that the archive is incomplete or corrupted.

If you re-downloaded the file, then I'd suggest deleting it and downloading it a third time :)

---

### Post by cliveT on 2012-01-17
just send to rubbish bin yes/ Do I need to do anything else?

---

### Post by cortman on 2012-01-17
> **cliveT said:**
> Hi guys
I recently installed QCAD, I downloaded from website and saved to my desktop - then set permissions and then in the terminal I typed in Desktop/qcad then pressed tab to complete the command and all was well, I was up and running - no problems.

Then I accidentally removed QCAD, so I went through the same procedure but this time I get this error in the Terminal (this is with a new downloaded file to the desktop - the previous bin file is removed)

clive@clive-Inspiron-N5110:~$ Desktop/qcad-3.0.0-rc2-prof-linux.bin 
Verifying archive integrity...Error in MD5 checksums: 7f01d9117f2ec66deb42cc5d72515acc is different from fea5f97bde6f8847790cdbb66f06240c
clive@clive-Inspiron-N5110:~$ 


Please help

regards

Clive

I would recommend running

```
sudo apt-get purge qcad
```

to totally remove it from your system, and

```
sudo apt-get install qcad
```

to re-install. It's in the repositories, so I'd recommend getting it from there.

---

### Post by cliveT on 2012-01-17
Thats got it! Thanks again lechien73 -you`re a life saver. I certainly am living and learning with this move to Ubuntu, but i like it - its great. So long as you guys don`t mind helping out like this! :p

---

### Post by cliveT on 2012-01-17
Thanks cortman but I need the "Pro" version (I do have to pay for it but it is very cheap to buy!)

---

### Post by cortman on 2012-01-17
> **cliveT said:**
> Thanks cortman but I need the "Pro" version (I do have to pay for it but it is very cheap to buy!)

My mistake- Glad it worked!

---

