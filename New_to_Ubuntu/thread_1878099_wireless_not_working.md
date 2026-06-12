---
title: "wireless not working"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by Ashok rajpurohit on 2011-11-09
I am just biginner at ubuntu 10.10 .I have dell vostro 1540 notebook my wireless is not working in ubuntu .How this problem can overcome?

---

### Post by blade4 on 2011-11-09
What is your wireless card model ? If you don't know you can find out by entering this in your terminal : 

lspci 

and checking the output of 'Network Controller' entry .

---

### Post by Matt__ on 2011-11-09
the wireless on this machine is BCM4313 802.11b/g/n 

the said machine has [CERTIFIED FOR 10.10]("http://www.ubuntu.com/certification/hardware/201105-8078") 32bit status pre installed.

First check for additional drivers in system/admin/additional drivers. Two should show up, try bcm first and STA if that dosnt work to your satisfaction after reboot.

alternatively you could try these commands, one line at a time in the terminal;
```
sudo apt-get remove bcmwl-kernel-source

sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer

sudo reboot
```There is also the option to upgrade to Natty where this wireless chip is supported without issue or go to the dell site and get  their driver version.

---

### Post by Ashok rajpurohit on 2011-11-09
Thanks for your valuable reply
 
I tried to connect by ethernet but it aly wso not working can you send me link by which i download package for wireless and ethernet.
Hope i will get good suggestion.

---

### Post by blade4 on 2011-11-10
My set is broadcom 4311 , so what worked for me might work for you too : here's what I did ....

You will have to install b43-fwcutter and patch packages. After that you will need to setup firmware manually (without the firmware automatically downloading and being set up).

b43-fwcutter is located on the Ubuntu install cd under ../pool/main/b/b43-fwcutter/ and patch is located under ../pool/main/p/patch/ or both in the official repositories online.

Double click on the package to install or in a terminal navigate to the folder containing the package and issue the following command:

:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*

Step 1.

On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Step 2.

Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware:

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

Note: A computer restart may be required before using the wifi card.

---

### Post by Ashok rajpurohit on 2011-11-12
hi blad4 I followed your suggestion .I installed b43-fwcutter from CD.i downloded two package which you define in link . When i wrote above code in  gnome terminal then first and third has executed but in second ( sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o) then the out was wl file cannot open. when check list of all file by typing ls  b43-fwcutter then i did not find this file .My problem is not solved yet . Hope it will solved very soon my eathernet and wireless is not working yet .
thanks And waiting for your reply

---

### Post by bkratz on 2011-11-13
for this wireless device -BCM4313 you need to actvate the Broadcom-STA driver in "additional drivers", and to blacklist the following modules: (In terminal)

echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf

Reboot after that


Sorry, reread the post, ignore since you are using 10.10 these instructions are for 11.10

---

### Post by blade4 on 2011-11-29
Hi Ashok , I notice that you didn't mention installing the patch package . If you didn't , try installing that and then go for the codes in the terminal . If you did , well then I'm stumped for now .... will get back to you on this .

---

### Post by Ashok rajpurohit on 2012-01-03
Thanks blade4 .For a long time I was busy in my exam preparation .I have installed this package successfully . . .

---

