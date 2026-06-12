---
title: "Wi-fi adapter not working"
date: 2015-04-06
forum: New to Ubuntu
---

### Post by Anton_Hristov on 2015-04-06
Hello, I installed my ubuntu a few hours ago and I have been trying to get the Wi-fi adapter to work with no success so far. I am able to connect to my home network using a cable. In the beginning when I typed the lshw command I could see that the network adapter was unclaimed but after trying some fixes which I some people said should fix the issue it does not say unclaimed anymore but still does not work. Please noet that I am a complete beginner.

Thank you in advance!

---

### Post by oldrocker99 on 2015-04-06
What kind of wireless adapter are you using? Find out this way:```
lspci | grep Wireless
``` and post the results. Many, but not all, wireless adapters are supported by the Linux kernel. If it isn't supported, there is a way to install the Windows driver, which is called ndiswrapper. Install it with[code]sudo apt-get install ndisgtk [/b]

Run it and you'll get a window, in which open the driver from where you extracted it. Point to the .INF file and click Install. 

Here's expanded directions: [http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/](http://www.howtogeek.com/howto/43752/how-to-install-a-wireless-card-in-linux-using-windows-drivers/).

Note that this doesn't always work; but it frequently does. I had, 6 years ago, to use this method on a Toshiba laptop. When the 2.6.28 kernel came out, the wireless chip was supported. So...keep hope alive that it'll eventually be supported!

---

### Post by Anton_Hristov on 2015-04-06
I tried copying the code you provided but for some reason it does not do anything. I tried just "lspci" and it says that my network controller is Broadcom BCM43142. I tried installing the drivers using a guide on the Interner a few times. Do you think that not removing the previous driver completely before installing another one might have caused the issue?

---

### Post by slickymaster on 2015-04-06
> **Anton_Hristov said:**
> I tried copying the code you provided but for some reason it does not do anything. I tried just "lspci" and it says that my network controller is Broadcom BCM43142. I tried installing the drivers using a guide on the Interner a few times. Do you think that not removing the previous driver completely before installing another one might have caused the issue?
Please download and run this [wireless script]("http://dl.dropboxusercontent.com/u/57264241/wireless_script"), which will diagnose your system. It will download a script and create a file named (**wireless-info.txt** or **wireless-info.txt.tar.gz**) depending on the size of the file. It will be placed in your home folder.
Once that done, please post back here in the thread the results of the wireless script in [CODE tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168") (or attach the .tar.gz-file).

---

### Post by riverguy99 on 2015-04-06
You didn't say what your computer is, but I discovered that Intel WiFi card WM3945ABG fixed the problem for me in several different laptops.  There are lots of these cards for sale on eBay for around $5, shipping included!  Once installed, Ubuntu finds and configured the connection instantly.

---

### Post by Anton_Hristov on 2015-04-06
Here is the file with the information from the script.

---

### Post by Vladlenin5000 on 2015-04-06
You probably need just this:```
sudo apt-get install bcmwl-kernel-source
```
Reboot and try again.

---

### Post by wildmanne39 on 2015-04-06
> **Vladlenin5000 said:**
> You probably need just this:```
sudo apt-get install bcmwl-kernel-source
```
Reboot and try again.+1 you also need to blackist the b43, ssb and bcma driver.
Examle ```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
``` run the command three times changing the driver each time.
Reboot

---

### Post by Anton_Hristov on 2015-04-07
Hello again, I tried running the code you provided and it said that bcmwl-kernel-source is already the newest version. I also ran the blacklisting code changing the name in the brackets(I dont know if that is what I was supposed to to) and rebooted. Still no success, when I go to the network manager it only shows ethernet and I cant detect any wireless networks.

Sorry that I am such a noob but I recently got into ubuntu and this whole thing is new to me.

P.S when I run sudo modprobe wl I get "FATAL Module wl not found"

---

### Post by Anton_Hristov on 2015-04-07
I almost fixed it after following this guide: [http://itsfoss.com/fix-no-wireless-network-ubuntu/](http://itsfoss.com/fix-no-wireless-network-ubuntu/) . I did everything from the guide and the wi-fi started working but the problem is that after restart I have to go to Software & Updates>>Additional Drivers , select not to use the device, apply and then choose the driver and apply again. I don't know why but it starts working after that. Does anyone know how to make it so that I dont have to repeat the process after each restart?

---

### Post by DCO on 2015-04-07
I have the broadcom 4312 as well on my Dell. This is the page I used to get this laptop's wireless working:
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by wildmanne39 on 2015-04-08
Run this command one line at a time as see if it works after boot if not run the script in my signature and post the file here.
```
sudo su 
echo wl >> /etc/modules 
exit
```

---

