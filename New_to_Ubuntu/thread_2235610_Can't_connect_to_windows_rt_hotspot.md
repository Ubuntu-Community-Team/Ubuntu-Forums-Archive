---
title: "Can't connect to windows rt hotspot"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by kris22 on 2014-07-22
Hi

I have ubuntu 14.04 installed and can connect to my galaxy S4 AP but for some reason it won't connect to my windows RT tablet's AP. It shows up in connections and I can click to connect to it but it automatically disconnects while trying to connect. Any ideas? I've tried unplugging and plugging in the USB Wi-Fi adapter, restarting the PC and tablet, that's about the extent of my knowledge in troubleshooting this though. 

Thanks

---

### Post by kris22 on 2014-07-25
97 views and no one has an idea how to fix this problem? :(

So I ended up getting it to connect, didn't do a thing differently, just connected. But it doesn't connect every time. Sometimes it does and sometimes it doesn't. Any ideas on how to fix this?

---

### Post by wildmanne39 on 2014-07-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by kris22 on 2014-07-28
Hi Wild Man, thanks for your reply. All seems to be good now, connecting every time. Not sure why it wasn't though :/ Thanks anyway.

---

