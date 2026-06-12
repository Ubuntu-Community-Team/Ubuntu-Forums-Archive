---
title: "[SOLVED] Open Office"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by F.R Mostert on 2008-08-05
Hi,

I originally installed Ubuntu 7.10 and then upgraded to 8.04 (Hardy) ever since that I had a problem with a broken package in OO I used synaptic to fix broken package abd dkpg -a but nothing helped. Eventually I deleted the entire OO Now I have tried to install again but still have the broken package.  Is there any way I can delete OO in Ubuntu and redownload it to get it working?

Regards

---

### Post by Joeb454 on 2008-08-05
So ```
sudo dpkg --configure -a
``` doesn't work at all?

---

### Post by F.R Mostert on 2008-08-05
Not At al I have tried sudo dpkg --configure -a many times also sudo apt-get upgrade & update several times.

Regards

---

### Post by sharks on 2008-08-05
i think the downloaded packages are still in ur system. 

> sudo apt-get clean

or go to syanptic and go to settings--preferences and files and click on delete cached package files.

---

### Post by Archmage on 2008-08-05
And what message do you get? As an example the name of package would be interessting.

---

### Post by lisati on 2008-08-05
I upgraded to 7.10 (from 7.04) last week and also encountered problems with Open Office (something to do with broken packages and problems with installing fonts). The way I eventually dealt with it was to backup my data, and do a clean install of 7.04.

---

### Post by F.R Mostert on 2008-08-05
Thank you very much I did not want to hear I must reinstall 8.04 but if I have I will. I think I will first clear the cach and then try again.

regards

---

### Post by Archmage on 2008-08-06
> **F.R Mostert said:**
> Thank you very much I did not want to hear I must reinstall 8.04 but if I have I will. I think I will first clear the cach and then try again.

Please give us the full output of the message, so that we can see what the problem with this package is.

I think for 99,999% it is not nessacary to reinstall.

---

