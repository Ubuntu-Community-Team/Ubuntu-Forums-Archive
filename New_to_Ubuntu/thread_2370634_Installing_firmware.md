---
title: "Installing firmware"
date: 2017-09-05
forum: New to Ubuntu
---

### Post by twostops on 2017-09-05
Hi all could someone point me in the correct direction, I am trying to get my Geniatech T230 dvb-t usb working, and I am now stuck, can someone tell me how I go about installing the .fw files I have downloaded from Linux.tv

---

### Post by deadflowr on 2017-09-05
Simply copy the files into the /lib/firmware folder
```
sudo cp -R ~/Downloads/*.fw /lib/firmware
```
Change the location to where ever the files are, if not in your Downloads folder

the *.fw means all files with the .fw extension, so it'll copy more than one if you have more than one.

---

### Post by twostops on 2017-09-06
Many thanks deadflowr, that was easy LOL, tv tuner now working in Kaffeine. I still have a lot to learn, but the more I learn the less inclined to return to Windows. Once again thank you

---

### Post by Perfect Storm on 2017-09-06
Marked thread 'solved'.

---

