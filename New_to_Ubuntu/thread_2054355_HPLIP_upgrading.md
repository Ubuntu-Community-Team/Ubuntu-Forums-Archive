---
title: "HPLIP upgrading"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Primus1 on 2012-09-07
Hi, This morning I had a pop up box on my computer from "HP Upgrade Manager" which said: "Latest version of HPLIP 3.12.9 is available" and asking if I want it installed. 
I'm running on Lucid 10.04 LTS. I'm using the HPLIP from 12.04 because the HPLIP that came with Lucid did not support the all-in-one printer I bought a couple of weeks ago.

My concern is that the request to install the latest HPLIP is not coming from Ubuntus App Update Manager. Do I wait for Ubuntu itself to offer me this latest HPLIP or is it ok to install from the HP manager?
Thanks.

---

### Post by Frogs Hair on 2012-09-07
I don't think the HPLIP version on 10.04 will update via the update manager. I saw a thread a week ago about a person upgrading HPLIP manually on 10.04 because of lack of multi function printer support . As I remember there were some problems but I think they got the printer working. I think the different version of python was the cause of the problem.

---

### Post by moggies on 2012-09-07
I recently installed hplip-3.12.6 from the HP website as my fresh build of Ubuntu 12.04 saw my Photosmart 7660 photo printer but would not reliably print anything. Installing hplip-3.12.6 resolved my issues.

I had the same HPLIP upgrade message this morning and selected the update option, which didn't seem to do anything. I went to the HP website and manually upgraded it. It just seems to handle some bug fixes and new devices. I've rebooted and successfully printed several LibreOffice documents with hplip-3.12.9 since.

I hope this helps.
Alicia

---

### Post by Bartender on 2012-09-07
I don't know if this helps you at all, but I posted several weeks ago with a summary of my experience [updating HPLIP manually]("http://ubuntuforums.org/showthread.php?t=1910222")

---

### Post by pqwoerituytrueiwoq on 2012-09-07
```
sudo apt-add-repository ppa:hplip-isv/ppa;sudo apt-get update;sudo apt-get upgrade;
```

---

### Post by Primus1 on 2012-09-07
Thanks for all the comments everyone. I think I will leave the HPLIP as it is because I just wanted to get the new printer working, which it does without issues now.

---

