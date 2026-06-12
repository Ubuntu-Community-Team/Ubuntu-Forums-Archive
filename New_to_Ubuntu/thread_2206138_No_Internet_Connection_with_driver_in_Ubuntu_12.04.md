---
title: "No Internet Connection with driver in Ubuntu 12.04"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by qlAnBqCtFJ on 2014-02-17
After freshly installing Ubuntu 12.04 LTS on my Sony Vaio, I downloaded a working Windows 7 driver for my Atheros AR928X chip and successfully used Ndiswrapper to wirelessly connect to the internet (since I couldn't find any AR928X Ubuntu compatible drivers). However, when I later shut down, and then later turned back on, I could not connect, and no possible network connections showed up under the wi-fi tab.

I'm able to connect to the internet using an ethernet cable, but I need to be mobile.
On my PC, several wi-fi connections show up, and the one i'm currently using is WPA2 encrypted.

I'd rather download a driver directly compatible with Ubuntu, but again, after hours of searching, I couldn't find any.

There are several posts addressing this issue, yet none seemed to work for me.

---

### Post by wildmanne39 on 2014-02-17
The driver is already a part of ubuntu, it just needs a little tweaking sometimes.

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-17
[ATTACH=CONFIG]250441[/ATTACH]

---

### Post by wildmanne39 on 2014-02-17
Did you upgrade your kernel or a minimal install? if so post the link so we can take a look because it looks like you have several things missing.
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-17
No, I fully installed Ubuntu 12.04 LTS, 64 Bit recently off a CD, and I haven't really tweaked or upgraded anything other than my desktop background..
What do I seem to be mssing?

---

### Post by wildmanne39 on 2014-02-17
Their is no driver loaded, when you installed ndiswrapper did you blacklist any drivers? Their is a lot of information missing from the file you ran is it possible you did not get it all posted here?

Please do:
```
sudo modprobe -v ath9k
```
Watch for errors then run and post a new file here hopefully that will show all the information this time.
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-17
[ATTACH=CONFIG]250444[/ATTACH]I added it as the tar.gz file, because I ran the code again and this time the file exceeded the allowed size of 19kb.

---

### Post by wildmanne39 on 2014-02-17
Please do:
```
sudo dpkg-reconfigure resolvconf
```
Then:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-17
Hi, I tried each command, and now all the different available connections show up, but when I type in my password and attempt to connect, it just loads forever and eventually asks me for the password again. I'm positive I typed in the right password for the right connection. Is it okay if I try each command again?

---

### Post by wildmanne39 on 2014-02-17
That is progress! Did you uninstall ndiswrapper? I suggest we run the following commands:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Then go into your router and change the channel to 1 or 11 and encryption to wpa2 AES (CCMP) not TKIP and save the changes.
If it does not connect reboot and post a new file so we can see the results of our efforts.
In my case I also had to go into network manger and delete the wifi connection and reboot after the changes to make mine work.
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-17
For the 1st command, I got:  FATAL: Module ndiswrapper not found    
The 3rd,4th, and 5th commands *appeared* to do nothing in the terminal.

I can't go in my router at the moment, so can I post back in a few hours?

---

### Post by qlAnBqCtFJ on 2014-02-17
[ATTACH=CONFIG]250446[/ATTACH]I changed my channel to 11 and was already on WPA2 AES (CCMP) and saved.
I still cannot connect, so can you please explain how you went to the network manager deleted the wi-fi connection and rebooted, etc.?
I atached the new file--

---

### Post by wildmanne39 on 2014-02-17
In your router enable this > disabling HT as WMM/QoS is not supported by the AP
network manager is in the top right corner of the screen click on it>click edit connections then click on wireless and remove them reboot and network manager should find your network name and try to connect to it.

Also please post the contents of:
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
It may be a bug in this driver version and we may have to find a new one to install if we can.
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-17
I couldn't find the [COLOR=#000000]*disabling HT as WMM/QoS is not supported by the AP, in my router after checking every link on the frontier page for my linksys router.*[/COLOR]

---

### Post by wildmanne39 on 2014-02-17
Did you see > HT as WMM/QoSwhere it can be enabled, it should not stop you from connecting but it can slow your connection way down.

Also please set your wireless settings in network manager top right corner of the screen to match the screenshots I have attached.

Please post the contents of the file I asked about in my last post.
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-17
When I entered the command, a window in text editor popped up saying only  'options ath9k nohwcrypt=1'
I found and enabled HT as WMM/QoS, as well as deleted connections, rebooted and changed the windows to match yours, but my problem persists and I cannot connect.

---

### Post by qlAnBqCtFJ on 2014-02-17
Since none of this has worked, are their any other working Ubuntu compatible AR928X drivers I just haven't found?

---

### Post by wildmanne39 on 2014-02-17
Their should be, I will need a little while to find it and get the directions written to install it.

Thanks

---

### Post by wildmanne39 on 2014-02-17
Click on the following link and download the file to your desktop.
[https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.13.2/backports-3.13.2-1.tar.gz)
With the file on the desktop right click and extract here then:
```
cd ~/Desktop/backports-3.13.2-1
make defconfig-ath9k
make
sudo make install
sudo modprobe -r ath9k && sudo modprobe ath9k

```
sudo make install' may produce a signing key warning just ignore it.
Thanks

---

### Post by qlAnBqCtFJ on 2014-02-18
Hi, it worked, i'm online wirelessly as we speak! Thank you so much for your continuous help!

---

### Post by wildmanne39 on 2014-02-18
Your welcome! Glad I could help.
Enjoy

---

