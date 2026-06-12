---
title: "No printer management and other appplets in xubuntu"
date: 2016-03-17
forum: New to Ubuntu
---

### Post by dcdc on 2016-03-17
Hello,
I'm very new to linux.
I recently purchased an android / xubuntu dual boot UGOOS UT3S box; it has xubuntu pre-installed.
I connected the printer (a samsung m2070) on a USB port, but no reaction.
I believe many applet are not installed, as I can't find any "printer" entry or "administrator", or "synaptic"...
I also triied to open from browser locaalhost:631, but nothing.
I also downloaded the printer driveers but I don't know what to do with them.

Could you explain me please how to install / access those applet, mainly how to install my printer?
Many thanks:)

---

### Post by grahammechanical on 2016-03-17
Synaptic Package Manager is has not been part of the default installed applications of Xubuntu/Ubuntu for a couple of years. So, it is no surprise that synaptic is not present. Is this the product?

[http://hometheatrelife.com/ugoos-ut3s-review-quadcore-android-media-player/](http://hometheatrelife.com/ugoos-ut3s-review-quadcore-android-media-player/)

I have read the review and although the claim is made that it dual boots Android and Ubuntu 14.10 I can not see anything in the review in regards to this dual boot feature. You say your device is dual booting Xubuntu. I wonder if it is Xubuntu Desktop or Xubuntu Core which has very few utilities & applications default installed.

The device has an ARM CPU so it would need an ARM architecture version of Xubuntu. Are there ARM builds of Xubuntu? I question that. This link says that there is a dual boot with Xubuntu option but the two versions offered are now end of life and out of support.

[http://ugoos.net/downloads](http://ugoos.net/downloads)

Do you not have a user manual? Does that not explain how to use this device?

Regards

EDIT: There is this. But because the 2 versions offered are end of life it is not possible to install additional software without editing some files.

[http://ugoos.net/blog/ugoos-ut3-android-linux-dualboot](http://ugoos.net/blog/ugoos-ut3-android-linux-dualboot)

---

### Post by HermanAB on 2016-03-18
You don't need any apps.

CUPS has a web browser interface on [http://localhost:631](http://localhost:631)

---

### Post by grahammechanical on 2016-03-18
On reflection, I am going to guess that you have on that device an ARM version of Ubuntu server. Either 14.10 or 15.04 as they are what UGOOS were offering. And on top of Ubuntu server there is Xfce, which has a limited set of utilities. Things are done this way, first, because the device needs an ARM version of a Linux OS, and second, because storage space is limited. It would not be useful to have utilities and apps that are not needed taking up limited storage space.

Now, it would be nice if UGOOS had provided a firmware update of a later version of Android & Ubuntu 15.10. Then you could have a version of Ubuntu that is still being supported. Perhaps they will provide a firmware update with 16.04 LTS as the basis for this Android/Ubuntu dual boot.

To find out what version of Ubuntu you are using run this command

```
lsb_release -a
```

Then you have to decide if you want to experiment. The software repositories of both 14.10 & 15.04 are now closed and unaccessible. But it is possible to edit a certain file to point to the new location of those old repositories. Then you should be able to install an application or two. And even upgrade to a newer (hopefully, supported) version of Ubuntu. 

You may be the only person to attempt to do this with that device. You may want to become familiar with flashing the device with firmware just in case things go pear-shaped.

Regards

---

### Post by dcdc on 2016-03-18
Thank you so much for all answers.
I was exactly wondering how to check the OS version, since on the "Application" menu they put a link to the Xubuntu 14.10 support, while it seems to have Ubuntu.
In fact, version is the following: 
```
ugoos@ugoos:~$ lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

```
Well I am wiling to do some simple tests, but I don't want to risk to mess up everything.
I hope, also, that Ugoos will publish soon a dual-boot firmware with latest ubuntu+Android 5, as they already published the firmware with android 5 only.
The first step would be to print (and possibly scan) connecting the M2700 printer to the UT3S via USB.
My final target would be to print and scan using the usb printer server from a TP-Link router, that's already working on my windows pc.

---

### Post by oldos2er on 2016-03-18
14.10 is end-of-life, no longer supported. 14.04 is the current Long Term Support version, 15.10 the "regular" nine months' support version. 

Your lsb_release result is normal for Xubuntu; I run Xubuntu too, and see ```
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily
```

---

### Post by grahammechanical on 2016-03-18
Now we can find out what desktop you have

```
echo $DESKTOP_SESSION
```

Is the response xubuntu or xfce? To go further and re-active the repositories you will need a file manager and a text editor. Are those installed? What you need to do can be done with a text editor called nano with this command

```
sudo -H nano /etc/apt/sources.list
```

You will see lines like this

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) utopic main restricted

You need to change all those line to this

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) utopic main restricted

Lines that begin with deb-scr are for obtaining source code. You do not need to modify those lines. And lines that begin with # are comments and will not be acted upon when the file is read.

The source for this information is

[URL="https://help.ubuntu.com/community/EOLUpgrades"]https://help.ubuntu.com/community/EOLUpgrades

[/URL]Save the changes by pressing ctrl = O that is Write out which is save. To exit nano = ctrl + X. When the file is opened the cursor should at the top of the page and can be moved by arrow keys to the places you want to edit.

Now you can run

```
sudo apt-get update
```

and see if it connects to the old-releases repositories. Make a note of the lines that you change as you change them and what the changes are. This should let you install an application or two. This method can be used to upgrade to 15.04 and then to 15.10 but that has a greater risk of failure.

In this situation on a desktop or laptop machine I would be recommending a fresh install for safety. So, I consider upgrading to newer versions an experiment. Which is why i suggest becoming familiar with flashing the firmware. Or wait and see if UGOOS comes out with a dual boot 16.04 version. And do not be tempted to upgrade to 16.10. That version will only have 9 months support like 14.10 & 15.04.

Regards.

---

### Post by dcdc on 2016-03-19
So, latest dual boot firmware from Ugoos at the moment includes only xubuntu 15.04, unfortunately.
Seems that they choose the "short support" version on purpose...
Do I really need to upgrade xubuntu in order to install only the printer management? 
Thanks

---

