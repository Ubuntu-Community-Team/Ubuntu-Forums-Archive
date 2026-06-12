---
title: "Upgrade to 12.04 Wireless now broken"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by gigi1234 on 2012-11-23
Hi,

I upgraded from 10.04 to 12.04 and now my wireless is broken.

My computer is a Dell XPS m1330. The wireless has always worked with no issues with all previous versions of Ubuntu I've run.

I enter the security code and it appears to connect. But then it immediately disconnects and asks for the code again. 

Any ideas?

The other problem is the new interface is so confusing I can't even find where anything is anymore. 

I'd be grateful for some assistance, please.

Thanks!

---

### Post by wildmanne39 on 2012-11-23
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by gigi1234 on 2012-11-23
Okay thanks for your reply. I think I will wait until tomorrow because I am just too tired right now to dig out the cord and get a wired connection going. Will you be able to help me tomorrow if I post the info then?

---

### Post by wildmanne39 on 2012-11-23
Yes, I am going to bed then.

---

### Post by gigi1234 on 2012-11-23
Hi there! I got some sleep and am back to wanting to solve this issue. Attached is the requested file. Many thanks to you for your help.

---

### Post by wildmanne39 on 2012-11-23
Hi, which network are you trying to connect too? none of them have a very strong signal strength.

Also you should change encryption in your router to just wpa2 if you have that option it will work best.

You will need to change the setting in network manager to wpa/wpa2.
Then reboot.

Please do:
```
echo "options iwl4965 11n_disable=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
Thanks

---

### Post by gigi1234 on 2012-11-23
Hi again. I am trying to connect to qwest6848-the computer is sitting only a few feet from router. It has always worked fine in the past. I don't have any idea how to change the router to WPA2 but I will try to figure it out. What does the code you sent do?

---

### Post by wildmanne39 on 2012-11-23
Hi, the code disables N speed because it does not work with that driver and it will keep you from connecting.

To change encryption in router usually 192.168.0.1 in the browser will open the configuration page for the router, you have to be hard wired to it.

You can try the command first that alone might do the trick.
Thanks

---

### Post by gigi1234 on 2012-11-23
Running that code wasn't enough but I figured out how to change the security to WPA2 and that seemed to work. Thanks for all your help!!!

:)

---

### Post by wildmanne39 on 2012-11-23
Your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

