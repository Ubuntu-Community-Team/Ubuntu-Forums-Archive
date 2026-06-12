---
title: "Wifi keeps disconnecting"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by czmacbudder on 2014-04-18
I keep haveing to reboot my computer because I keep getting disconnected from my internet somebody please help me before I have to reboot again

---

### Post by pfeiffep on 2014-04-18
Some details about your system might help others to help you.
What version OS are you using, what are your PC specifications, what type of internet connection - wired or wifi

---

### Post by czmacbudder on 2014-04-18
> **pfeiffep said:**
> Some details about your system might help others to help you.
What version OS are you using, what are your PC specifications, what type of internet connection - wired or wifi

wifi and I have  Intel® Core™ i3-3110M CPU @ 2.40GHz × 4  hp pavilion g7

---

### Post by oldos2er on 2014-04-19
Which Ubuntu version? What make and model wireless device?

Since 99.9% of people posting here need help, I've changed your thread title to better reflect your problem.

---

### Post by czmacbudder on 2014-04-19
> **oldos2er said:**
> Which Ubuntu version? What make and model wireless device?

Since 99.9% of people posting here need help, I've changed your thread title to better reflect your problem.

I mean its on all internets i'm on ubuntu 14.04

---

### Post by HermanAB on 2014-04-19
Howdy, I'm sure you don't want to hear this, but the best solution is usually to buy a better WiFi adaptor.  Edimax USB WiFi dongles even has a friendly little Linux Penguin on the packaging and should get you going reliably.

---

### Post by wildmanne39 on 2014-04-19
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by czmacbudder on 2014-04-19
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

Thanks man that fixed it!

---

### Post by Navneet_Kumar on 2014-04-19
i have the same problem and i have downloaded the script.please guide me through the further steps..........

---

### Post by wildmanne39 on 2014-04-19
That script just collects information to help fix your issue, it could not have actually fixed it.

---

### Post by wildmanne39 on 2014-04-19
> **Navneet_Kumar said:**
> i have the same problem and i have downloaded the script.please guide me through the further steps..........Hi, I thought your issue was fixed here. 
[http://ubuntuforums.org/showthread.php?t=2217821&page=2](http://ubuntuforums.org/showthread.php?t=2217821&page=2)
if not you need to continue in that thread to get help, please do not hijack someone else's thread.
Thanks

---

### Post by czmacbudder on 2014-04-19
> **Wild Man said:**
> That script just collects information to help fix your issue, it could not have actually fixed it.

Well it did fix it so I don't care

---

### Post by Vladlenin5000 on 2014-04-19
> **czmacbudder said:**
> Well it did fix it so I don't care

You should care... The script is a diagnostics tools only. It can gives us clues about what's wrong and then we (some of us, of course) can start testing solutions.
The script didn't fix your issue. Don't use it later thinking it fixes things because I doesn't, period.
What might have happened is that as soon as it got an alternative internet connection it downloaded proprietary firmware/drivers for your WiFi card and then it started working as expected. It had nothing to do with the script.

---

### Post by wildmanne39 on 2014-04-19
> **czmacbudder said:**
> Well it did fix it so I don't care
I am glad it is working and I don't care sounds a little rude!

---

