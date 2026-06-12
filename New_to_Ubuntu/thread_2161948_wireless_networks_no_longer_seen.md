---
title: "wireless networks no longer seen"
date: 2013-07-12
forum: New to Ubuntu
---

### Post by philpense on 2013-07-12
Lubuntu has worked on my netbook for months with no connectivity issue.  used to be able to see my network and other local networks.  how does one troubleshoot such an issue?

---

### Post by claracc on 2013-07-12
It would be good to know about:

What is the lubuntu release you are running?
What are the hardware specs of your computer?, particularly important in this case the wireless card and the ethernet ( if any)

What is the network manager are you using?

How long ago, you cannot connect to the wifi?

---

### Post by wildmanne39 on 2013-07-12
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by philpense on 2013-07-12
This is an asus  netbook with intel celeron  m chip
2GB memory
Ubuntu 12.04.2 LTS
This is a linksys wrv200 router   configured to access via MAC address
Went to the public library... the usual wifi is not seen
No wifi for three days

---

### Post by philpense on 2013-07-14
Much  thanks for the guidance.  The command was entered and the result is uploaded to an online folder found at:
[https://skydrive.live.com/redir?resid=1727C265A60F257A!405](https://skydrive.live.com/redir?resid=1727C265A60F257A!405)

At reports end,  I am prompted for the system password.  Appreciate your continued support

---

### Post by wildmanne39 on 2013-07-14
The wireless info.txt file is in your home folder please attach it here.
Thanks

---

### Post by philpense on 2013-07-14
The wireless info file is uploaded to the same skydrive folder. Much appreciation

---

### Post by philpense on 2013-07-14
maurice@maurice-900:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2013-07-13 18:59:45--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 50.19.107.159
Connecting to dl.dropbox.com (dl.dropbox.com)|50.19.107.159|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2013-07-13 18:59:52--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 54.235.184.27
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|54.235.184.27|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3771 (3.7K) [text/plain]
Saving to: `wireless_script'


100%[======================================>] 3,771       --.-K/s   in 0.02s   


Last-modified header missing -- time-stamps turned off.
2013-07-13 18:59:53 (156 KB/s) - `wireless_script' saved [3771/3771]


[sudo] password for maurice: 
[sudo] password for maurice: 
[sudo] password for maurice: 


Results saved in "wireless-info.txt".


maurice@maurice-900:~$ My1secret

---

### Post by wildmanne39 on 2013-07-14
>  Results saved in "wireless-info.txt".This is what we need, I do not see that in the skydrive file onlky a screenshot of what you posted here.
This file is in your home folder please attach it here.
Thanks

---

### Post by philpense on 2013-07-14
Greetings:

Just found the attachment feature in advanced reply.  I believe that it is properly done.

Thank you

---

### Post by wildmanne39 on 2013-07-14
Please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Then:
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by philpense on 2013-07-17
Just  now able to respond

maurice@maurice-900:~$ echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
[sudo] password for maurice: 
options ath5k nohwcrypt=1
maurice@maurice-900:~$ sudo modprobe -rfv ath5k
rmmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-49-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-49-generic/kernel/net/wireless/cfg80211.ko
maurice@maurice-900:~$ sudo modprobe -v ath5k
insmod /lib/modules/3.2.0-49-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-49-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1
maurice@maurice-900:~$ sudo modprobe -v ath5k
maurice@maurice-900:~$ gksudo gedit /etc/pm/power.d/wireless
maurice@maurice-900:~$ #!/bin/sh
maurice@maurice-900:~$ /sbin/iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not permitted.
maurice@maurice-900:~$ 


Not sure how to interpret. Continued Guidance Sought

---

### Post by philpense on 2013-07-17
maurice@maurice-900:~$ echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
[sudo] password for maurice: 
options ath5k nohwcrypt=1
maurice@maurice-900:~$ sudo modprobe -rfv ath5k
rmmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.2.0-49-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-49-generic/kernel/net/wireless/cfg80211.ko
maurice@maurice-900:~$ sudo modprobe -v ath5k
insmod /lib/modules/3.2.0-49-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-49-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.2.0-49-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1
maurice@maurice-900:~$ sudo modprobe -v ath5k
maurice@maurice-900:~$ gksudo gedit /etc/pm/power.d/wireless
maurice@maurice-900:~$ #!/bin/sh
maurice@maurice-900:~$ /sbin/iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not permitted.
maurice@maurice-900:~$ 


Not sure how to interpret the results... Continued guidance sought

---

### Post by wildmanne39 on 2013-07-17
After you entered ```
gksudo gedit /etc/pm/power.d/wireless
```
and you entered your password a balnk file opened and that is where you put
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```right? then you saved the gedit text file closed and rebooted?
Thanks

---

### Post by ndex477 on 2013-07-18
Since you are using your internal WiFi card make sure that in Network Manager under Preferences your wireless interface is wlan1. This could be the issue. Sometime this can get changed somehow.

---

