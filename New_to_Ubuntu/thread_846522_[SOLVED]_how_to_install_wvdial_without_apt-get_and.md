---
title: "[SOLVED] how to install wvdial without apt-get and using a ISO image"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by WildOscar on 2008-07-01
I tried uninstalling gnome ppp and ended up unistalling wvdial as well. Since the only way i connect to internet is using my E220 Huawei modem, I now have no way of connecting to the internet.

How ever i have the ISO-image of Hardy Heron. How do  I include that in to repositories. I tried mounting the image but when i click add cdrom. It goes directly to my physical cdrom even thou i have no cd in it.

My question;

1. Is it possible to install wvdial by adding the cdrom into the repositories. ( I dun see why not since wvdial installed from the cd)

2. How do i get that done when I only have the ISO image.

- If not i have to download the dependencies one by one! trying to avoid that. In my previous attempts i have not been so successful.

---

### Post by Hospadar on 2008-07-01
I believe if you put in the cd, go to System->Administration->Software Sources and check the CD, you'll be able to install that through synaptic.  If that doesn't work, try unchecking the normal repos and see if that gives you any different performance.

---

### Post by kuja on 2008-07-01
It can be done.

Lets make a few assumptions.

Lets say the iso is at /home/blah/somefile.iso
Lets assume the iso is for the alternate installer, because the live one will not work, at all, ever, for this type of use.
```
sudo mkdir /media/ubuntuiso
sudo mount -o loop /home/blah/somefile.iso /media/ubuntu
sudo bash -c 'echo "deb file:///media/ubuntu/ubuntu hardy main restricted" >> /etc/apt/sources.list'
sudo apt-get update #Yes, I know, most of it is going to fail
sudo apt-get install wvdial #If all is good and well, this will work.
```

---

### Post by WildOscar on 2008-07-01
I don't have the CD. Only the image of the Ubuntu Installation CD?

1. I beleive I have to mount the image (guessing here)
2. Add that image into the sources (how do I this)

---

### Post by WildOscar on 2008-07-03
> **kuja said:**
> It can be done.

Lets make a few assumptions.

Lets say the iso is at /home/blah/somefile.iso
Lets assume the iso is for the alternate installer, because the live one will not work, at all, ever, for this type of use.
```
sudo mkdir /media/ubuntuiso
sudo mount -o loop /home/blah/somefile.iso /media/ubuntu
sudo bash -c 'echo "deb file:///media/ubuntu/ubuntu hardy main restricted" >> /etc/apt/sources.list'
sudo apt-get update #Yes, I know, most of it is going to fail
sudo apt-get install wvdial #If all is good and well, this will work.
```

Thanks mate, however it did not work i am still missing files
but this is a great way to include the iso image into the package  source.

Once the package was listed and updated wvdial is still missing a few dependencies. I have decided to download them manually and install them. Give post updates.

---

### Post by WildOscar on 2008-07-04
Ok my issue is solved. Used my Weirdos to download the wvdial dependencies and once installed in ubuntu. I ran a apt-get wvdial just to make sure everyhting was alright. Able to connect to internet. Thanks people for ur help and guidance. :)

---

### Post by mevan_snp on 2009-06-02
thanks but i have dowenload .deb files . i have installed it but it give some mising files..

---

### Post by GeorgeVita on 2009-06-02
Hi ****,
assuming that you do not have an internet connection to the Ubuntu 9.04 PC, which is i386 32 bit, you need all files below:

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

and install them in above sequence 1-2-3-4-5

take a look my note at:
[http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html)
where you can find a .zip file also.

Regards,
George

---

### Post by r.v.the.evil on 2009-07-28
hello i am using ubuntu jaunty jackalope 9.04 i have tata indicom plug 2 surf and wen i install it in terminal it asks for wvdial install
whic i am trying by sudo apt-get install wvdial 
but it replies the package is missing or destroyed
what should i do

---

### Post by GeorgeVita on 2009-07-28
Hi **r.v.the.evil**,
if you have an active internet connection on your Ubuntu PC this should work. Try also the System > Administration > Synaptic Package Manager and find it to packages, choose **wvdial** to install.

If you do not have an internet connection you must follow instructions from my previous post (download to another PC, copy to a usb mem and install all 5 .deb packages).

Read also: [http://ubuntuforums.org/showthread.php?p=7245790#post7245790](http://ubuntuforums.org/showthread.php?p=7245790#post7245790)
Regards,
George

---

### Post by wailedhero on 2009-08-30
> **kuja said:**
> It can be done.

Lets make a few assumptions.

Lets say the iso is at /home/blah/somefile.iso
Lets assume the iso is for the alternate installer, because the live one will not work, at all, ever, for this type of use.
```
sudo mkdir /media/ubuntuiso
sudo mount -o loop /home/blah/somefile.iso /media/ubuntu
sudo bash -c 'echo "deb file:///media/ubuntu/ubuntu hardy main restricted" >> /etc/apt/sources.list'
sudo apt-get update #Yes, I know, most of it is going to fail
sudo apt-get install wvdial #If all is good and well, this will work.
```

Failure! Although thanks for sharing how to mount an ISO.:P
Will try the 5 files...

---

### Post by tallharish on 2010-01-01
@GeorgeVita

How do I install wvdial on Ubuntu x64?
I tried one of the .deb files given above, and it didnt install, saying that platform doesnt match

Thanks

Harish

---

### Post by GeorgeVita on 2010-01-01
Hi **tallharish**, happy new year!

read: [http://ubuntuforums.org/showthread.php?t=1368648](http://ubuntuforums.org/showthread.php?t=1368648)

and try to see all packages needed for your Ubuntu version via Synaptic:

**System > Administration > Synaptic Package Manager**

type in at 'search' field the word **wvdial** and press enter. Find it below at '**package**' column, click on box of column **S**, '**mark for installation**', '**Mark**'

>>> Instead of 'Apply' select **File > Generate Package Download Script**
give a **filename**, **close** Synaptic, **Quit** (cancels all marks). The created script includes all links for wvdial and dependencies. You can use this script to any 'connected' linux for download, or use just the links (copy paste to firefox) and get them using any O.S.

Regards,
George

---

### Post by aneesh.r on 2010-06-19
Hello,

I have tried all the steps specified in the thread to configure the gprs/edge connection in my ubuntu 10.04 (Lucid). The installation of wvdial and configuration are successful. Actually i was trying to connect my 
nokia N72 phone via an aircel connection (INDIA). Everything seems to be fine. Modem is also initialized with out any any warnings. When i try to connect to the network, it is getting disconnected after a 20-30 sec attempts. I checked the logs, it is saying "Connection terminated by the peer, error -15 " . I have used the  same settings given by the network provider for dialing. (Phone number : *99***1# and User Name and Password are blank). I could easily connect my phone to the network via the Nokia pc suit utility installed in my Windows 7. And also I have already spent 4-5 hours on debugging on this :( Can any body please help me on this? :confused:

Thanks in advance..

-itsmeanee

---

