---
title: "Build essential package problem"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by Shreyas_Raj on 2013-10-14
This message is being displayed when I type this command 

$ sudo apt-get install build-essential

"CD/DVD "Ubuntu 13.04_Raring Ringtail_-Releas amd64(20130424)" is required.
please inert the above CD/DVD .

---

### Post by steeldriver on 2013-10-14
Hello and welcome to the forum

It sounds like the installation CD is still selected as a 'software source' - try opening the 'Software Center' application, then go to the 'Edit' menu and select 'Software Sources...' and make sure the box for the 'Installable from CD-ROM/DVD' is unchecked. Then run

```

sudo apt-get update
sudo apt-get install build-essential

```

---

