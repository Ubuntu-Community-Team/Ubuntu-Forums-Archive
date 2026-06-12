---
title: "Can't get wireless working in Asus Aspire one"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by jpsantell on 2012-11-27
I have been driving myself crazy trying to get the wireless working in my Asus Aspire One. It previously ran xp but is totally on Ubuntu 12.10 now. The slider switch does not work in Ubuntu and my hardware is a Broadcom Corp. BCM4312 802.11 b/g LPPHW. Any ideas on how to activate the wireless?

---

### Post by wildmanne39 on 2012-11-27
Hi, please do:
```
sudo apt-get install --reinstall linux-headers-$(uname -r)
```
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Reboot
Thanks

---

### Post by jpsantell on 2012-11-28
I entered in all of the lines as stated and got nothing, still not showing wireless as working. After every line I got failed to start messages, is there anything else I can try? A netbook that won't connect to the net is pretty useless.:confused:

---

### Post by westie457 on 2012-11-28
Hi could you post those error messages please, we need to know so we can work out what has gone wrong.

Did you run those commands with an ethernet cable plugged in?

If not try again with a cable attached.

Thank you.

---

### Post by wildmanne39 on 2012-11-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

