---
title: "Ubuntu freezes with keyboard unusable only power down works"
date: 2018-06-12
forum: New to Ubuntu
---

### Post by dracllop on 2018-06-12
Hello to all members!

    I had installed a ubuntu 16.04 LTS partition in my desktop Aspire-M7811 with processor Intel® Core&#8482; i5 CPU 650 @ 3.20GHz × 4 a year ago. It works pretty fine till I use a serious number of applications with the common denominator of firefox...it still going fine with no slowness till ubuntu get frozen, even the keyboard is not responsive, forcing me to power down the entire pc.

   Im using only free software drivers, I cant install the last OP actualization. I will thank you for any help to fix it.

Kind regards

José Antonio

---

### Post by Autodave on 2018-06-14
You may want to install *psensor *and have a look at temps and CPU usage. I have one machine here that just hates Firefox and Dropbox. I get a 50 meg file twice a month via Dropbox. When I go to download that file, all 4 cores go to nearly 100%, the memory maxes out (4 gig) and the swap almost maxes out. The processor temp goes up about 40F in less than 20 seconds. At that point, the machine becomes so slow that it is almost unusable. Once the file is downloaded and I close Firefox and Dropbox, everything returns to normal in about 10 seconds.  I have, however, had it lockup and had to reboot and try again. (The file only takes about 5 or 10 secs to d-l, but it is amazing what happens to the machine in that time.)  You may want to try another browser.

---

### Post by bijayalaxmi1808 on 2018-06-14
Just a thought: I think you can use the top command to see which all apps are eating your CPU and memory.

Moreover I think can psensor will give you an idea (before the whole system freezes) if it is the processor that reaches to 100% ending up freezing the whole system !

---

