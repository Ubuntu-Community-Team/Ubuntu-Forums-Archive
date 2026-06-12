---
title: "[SOLVED] getting a gui going"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by dalibred on 2008-08-04
hi, i started to install xubuntu on a old dell laptop, using the alternative cd, thing is it seemed the packages or software didnt install so when the insatllation finished i can only work from the command line, can anyone tell me how to install xwindow or how to get the packages and then install them from the command line?

---

### Post by bodhi.zazen on 2008-08-04
sudo apt-get update && sudo apt-get -y install xubuntu-desktop && sudo apt-get /etc/init.d/gdm start

---

### Post by dalibred on 2008-08-05
hi, thank you for your help, the comands work, but on putting in the second command i am getting this "i/o error on device sro logical block", i am wondering if this is a error on the cd itself and if the installation program wasnt downloaded and written to the cd properly?

---

### Post by hyper_ch on 2008-08-05
boot from the cd again an in the the boot menu select to check the cd for defects.

---

### Post by dalibred on 2008-08-06
ok, Thank you, i did that and the cd has issues, i got it from the xubuntu website, do u think another mirror will give a good copy or do u know any link that gurantees near a hundred percent getting a good copy of the alternative cd, or is there another way to get the packages given i have the command line already?

---

### Post by halitech on 2008-08-06
do you know if you have a connection to the internet?

if you do, just try
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Jack M. on 2008-08-06
Most likely, the *download* of the .iso file is fine. You can check this by following [this guide]("https://help.ubuntu.com/community/HowToMD5SUM"). If the md5 sums match, then it was a bad burn - try using another CD at a lower speed.

---

### Post by dalibred on 2008-08-09
ok, thanks, i compared the hash of the iso image and it was the same, so i just burned a new cd at a very slow speed and it worked, the cd had no issues, so i was able to update from that, thanks for ur help

---

### Post by hyper_ch on 2008-08-09
use bittorrent to download the iso. that will auto-check the downloaded file for defects. then burn it at 4x speed to make sure the burning does not end in an error.

---

