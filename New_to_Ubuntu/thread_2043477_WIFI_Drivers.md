---
title: "WIFI Drivers"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by komatsu100 on 2012-08-16
I have a Acer Aspire laptop, running Ubuntu 12.04, my WIFI drivers have become corrupted how can I uninstall and re-install drivers for Athoros AR928X WIFI Card. :confused:

---

### Post by NikTh on 2012-08-16
Hi , 
I also have an Acer Aspire Laptop with Atheros Wireless card and driver is already pre-installed (kernel included) . It is ath9k. 

Can you post the output of 
```
lspci -nnk | grep -iA2 net 
iwconfig 
rfkill list all 
``` 
Put the results inside [CODE] tags , by highlighting the output and click the **#** button on message toolbar.
Thanks

---

### Post by wildmanne39 on 2012-08-16
Hi, what makes you thing the driver is corrupted?

You can also copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by komatsu100 on 2012-08-16
```

```
Sorry but I am green with Ubuntu and I highlighted the terminal return that you asked me for and when I pushed the # on the message bar the two code signs was all I go.  Also the Script file I have in my home director but when I try to attach it tell me it is an invalid file.  You wondered how I knew the drivers were corrupted, because I down loaded a sales add and after that my wireless printer and the Nitro Share won't communicate and my Internet is slower.

---

### Post by wildmanne39 on 2012-08-16
Hi, are you clicking the paper clip to attach the file? then upload it and wait for it to finish before closing the window.

If the file will not attach using the paper clip then right click on it and zip it and see if you can attach it that way.
Thanks

---

### Post by komatsu100 on 2012-08-17
Ok I when I right clicked I didn't see zip, but I saw compress, so it is attached, hope this helps you. If not I will try again, if you tell me how. 
Ron

---

### Post by wildmanne39 on 2012-08-17
Hi, you need to attach this netinfo.txt file, it is the file that is created by the wireless_srcipt, both will be in your home folder, and each time you run it a number will be added to the name starting with 1.
Thanks

---

### Post by komatsu100 on 2012-08-17
Hi; we will try this again and see if we can get everything together, I hope this is what you need.  
Ron

---

### Post by NikTh on 2012-08-17
Hi , 

I can only see (from netinfo.txt) that your problem is not the driver but UFW (the firewall) . 
To determine this , try to disable the firewall and see if connection's behavior corrected. 
```
sudo ufw disable
```Thanks

**Edit:** Although I don't know how to help you with UFW rules . I do not use it.

---

### Post by komatsu100 on 2012-08-17
Hi;Ran the terminal command and open Firestarter to make sure it was all off, and it still will not connect to printer of nitro share.  Went to settings and printers and it can not detect a printer on the network, but there is.   
Ron

---

### Post by wildmanne39 on 2012-08-17
Hi, I do not believe the UFW firewall is causing an issue with wireless but you should disable it, although it may be making your system boot slow.

However you should not have firestarter and UFW installed at the same time and UFW is installed by default because firestarter is outdated an no longer recommended.

Did you set up your connection manually in network manager, if so please remove all settings and reboot.

I recommend you take the period out of your network name, also go into your router settings and change the encryption to just wpa2 if you have that option it works best with linux.

My impression was that you could not connect with wireless is that the case? because now you 
mention can not detect a printer on the network, I help with wireless but I have never connected a printer to a network.

I also recommend you do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
and set your wireless settings in network manager to match the screenshots.
Thanks

---

### Post by komatsu100 on 2012-08-19
Thanks it is working, I uninstalled the printer and reinstalled it and it is working fine now.,  Thanks for all the help, with the router setting, I am sure this will make my router run faster, I also uninstalled the Firestarter Firewall and will reinstalle the UFW firewall, I did not know Ubuntu came with a firewall already installed.  
Thanks for everyting.  
Ron

---

