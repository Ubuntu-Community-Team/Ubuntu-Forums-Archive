---
title: "Wireless won't work Newley installed ubuntu 13"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by flagrl on 2013-10-15
I installed ubuntu last night and tonight I tried to get my wireless working. I have a hp pavilion laptop. I tried installing the b43 from the terminal. Didn't work. Checked the additional drivers there is none except for video card. I was connected to internet via Ethernet cord. I ran updates. I rebooted it and still nothing? Any help would be so nice. Thank you

---

### Post by wildmanne39 on 2013-10-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

