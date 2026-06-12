---
title: "How to disable USB wireless adapter?"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by palmgrower on 2013-12-22
I used to have realtek8192 based wifi adapter. It had connection problem, and I installed a linux fix. Still it slowed down unbearably slow occasionally, I am using a different wifi adapter. Problem now is that the pc boots without inernet connection and takes about 5 minutes to connect to internet. I wonder if the delay comes from the installation of realtek8192 fix, making PC seek the now-gone usb adapter. The following is what I did to install the realtek8192 fix. Is there a way to undo it? Even a partial undo may do the trick. Thanks.

sudo apt-get install linux-headers-generic build-essential dkms
git clone [URL="https://github.com/pvaret/rtl8192cu-fixes.gitsudo"]https://github.com/pvaret/rtl8192cu-fixes.git
[/URL]sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.8
sudo depmod -a

---

### Post by varunendra on 2013-12-23
Try this -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
This will remove your current udev rules file for network devices, resulting in generation of a new, fresh one at next boot. If the problem persists after a reboot, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. Make sure the new adapter is plugged in when you run the script.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

