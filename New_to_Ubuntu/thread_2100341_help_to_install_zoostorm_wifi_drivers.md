---
title: "help to install zoostorm wifi drivers"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by nelliebellie on 2013-01-01
[I][B] Hi I am new to the forum and would be grateful to anyone who could explain the instructions to install a drivers for my zoostorm laptop running ubuntu12.10. Every thing works except the wifi which is switched on. I have managed to download the drivers from a dropbox link and the tar.gz file is in my downloads folder. the instructions on how to install are the following :
[/B][/I]
 Support for the RTL8273AE-BT has been added by Realtek in the  92-series driver, version 0006.0514.2012. For unknown reasons, neither  the Windows nor Linux drivers are available on their website (yet). But  Realtek tech support has been providing a Dropbox link with the source  code/firmware tarball which numerous users have reported as working

[LIST]
[*]The driver can be downloaded via [this Dropbox link.]("http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz")
[*]I can confirm that this file is what it claims to be, with [this content listing]("http://paste.ubuntu.com/1097947/"), provided it has the following MD5 or SHA1 hashes: (which you can verify with md5sum or sha1sum)
  MD5: fd10e9a347c6447f649324d6bdab53de SHA1: 1ccd6ae73878d8bf65bd7c0384e333b121606230
[/LIST]
  **How do I build and install the driver on Ubuntu?**

  
[LIST=1]
[*]Open a terminal with Ctrl+Alt+T.
[*]You'll need to install these packages first to build the driver:
  sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
[*]Paste the below line to download and extract the driver archive in one single step:
  wget -O- [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz) | tar -xz
[*]Change to the extracted driver's directory, build and install the driver:
  cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 make sudo make install
[*]Test the driver by loading it (this is a one-time step; after you  reboot once, the driver should automatically load on every boot):
[/LIST]
***I am stuck at number 3 how do I paste the line to the download. I have typed it in terminal but just says not found. I am also baffled by points 4 and 5. I realise I am on a very steep learning curve but any help would be much appreciated.***

---

### Post by irv on 2013-01-01
I found another thread that looks like the same problem you are having. Check it out and see if it helps.
[http://ubuntuforums.org/showthread.php?t=1499162]("http://ubuntuforums.org/showthread.php?t=1499162")

---

### Post by Isamu715 on 2013-01-01
Step 3 only downloads the package you already have and extracts it, you can do it manually.  I'll try to break these steps into easier to follow commands.
Step 3:
```
wget http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
tar -xzf rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
```Step 4:
```
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/
make
sudo make install
```For the last step you'd need to know the module name but it should be safe to just reboot and the driver will load.

If something doesn't go right go to the driver's directory and use the following command:
```
sudo make uninstall
```

---

### Post by nelliebellie on 2013-01-02
**Hi Isamu715, Thanks for your help. However when I cut and paste step 4 into terminal I get the following. Do you or anyone know what I am doing wrong? **

tim@tim-W240EU-W250EUQ-W270EUQ:~$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/
tim@tim-W240EU-W250EUQ-W270EUQ:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ make
make -C /lib/modules/3.5.0-21-generic/build M=/home/tim/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012 modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  CC [M]  /home/tim/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o
/home/tim/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c: In function ‘_rtl_init_mac80211’:
/home/tim/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/tim/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.c:320:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/tim/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/base.o] Error 1
make[1]: *** [_module_/home/tim/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
make: *** [all] Error 2
tim@tim-W240EU-W250EUQ-W270EUQ:~/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012$ sudo make install
[sudo] password for tim:

---

### Post by Isamu715 on 2013-01-05
You won't be able to install if *make *returned an error. Use:
```
sudo apt-get install build-essential
```and try again from step 4.

---

### Post by nelliebellie on 2013-01-05
Hi Thank you isamu715 I tried your suggestion and it did look hopeful, but the test failed even after reboot. I'm afraid I have finally admitted defeat and ordered a copy of windows 7 from e bay. Such a shame as I like ubuntu. I run 10.10 on an old hp compact which is faster than my new high spec zoostorm.  Thanks again for your efforts to hel_p_[URL="http://ubuntuforums.org/member.php?u=1724212"]
[/URL]

---

### Post by MikeMiracle on 2013-02-02
nelliebellie , Sad to see you quit so soon.

I recently bought the same laptop , It runs well in ubuntu 12.10.

[LIST=1]
[*]Download and Install Ubuntu 12.10 64 bit using cdrom or usb drive
[*]Everything will work except wireless internet
[*]Make sure you are connected to the Internet through ethernet cable
[*]**Download Driver compatible with ubuntu 12.10 (3.5 + kernel) from here. [www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)**
[*]Please note that the other driver files avalable as dropbox file may not work with ubuntu 12.10
[*]run this cammand for the build essentials ```
sudo apt-get install build-essential linux-headers-generic linux-headers-`uname -r` 
```
[*]extract the tar.gz file using either archive manager or commandline as this ```
tar -xzf rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz
```
[*]using terminal cd to the folder ```
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
```
[*]```
make
```
[*]```
sudo make install
```
[*]```
sudo modprobe rtl8723e
```
[*]Done . wireless will work now
[*]Caveat , you will need to do these steps(from make to modprobe) when ever ur linux kernel gets updated.
[*] save significant quids on bloatware such as windows and antivirus.
[/LIST]

---

### Post by rpaco on 2013-02-07
"Can I ask if you got the brilliance control to work (Fn + F8 or F9) ? It is on full on my laptop and far too bright.  The Fn buttons do not work at all on brilliance though they do on the vol control and everything else."

It's ok I have found another way using the settings editor. I am using Xbuntu 12.04 wiht Xfce 4.10

---

### Post by kurt18947 on 2013-02-07
I'm no help on the script but what O.S. and desktop are you using?  A too bright screen is distracting.  Gnome-shell has an extension to adjust screen brightness.  Another possibility with Gnome-shell and I assume Unity is to search for a brightness and lock app.  I don't have it on my desktop because my monitor doesn't support it but I assume there's a way there to adjust brightness if it's supported by the hardware.

---

### Post by wildmanne39 on 2013-02-07
Hi, please keep the thread on the topic in the title.
Thanks

---

### Post by rpaco on 2013-02-07
Ok I have found a plugin for Xfce. 

Will post a script here for re-installing the wireless driver when I have had a better go at writing it.

---

### Post by ianmillington on 2013-04-03
I'm thinking of buying one of these in maybe the next few days (well the 7877-0905 which appears pretty much the same apart from the fact it has an i3 processor - Does this make it worth the price differential of £90 I wonder?). 

Looking around it appears the drivers for this wireless card are included in the 3.8 kernel. If that's right then it should work OOTB with 13.04. Would that be a correct assumption?

---

### Post by ianmillington on 2013-04-15
To answer my own post I have in fact bought the 7877-0905 and the wireless does work OOTB with 13.04. Result!

---

### Post by charliewarlie on 2013-04-15
I followed these instructions and they worked perfectly the first time. Now I've since updated things and needed to redo those last steps, but it just wasn't working, I had all sorts of problems, so I decided to remove the driver and start again from the beginning. Now when I do step 8, terminal says this: 

charlie@charlie-W240EU-W250EUQ-W270EUQ:~$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
bash: cd: rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012: No such file or directory

I extracted the files myself, but terminal still says there's no such file or directory when I try to cd into the folder: 

charlie@charlie-W240EU-W250EUQ-W270EUQ:~$ cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012
bash: cd: rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012: No such file or directory

Any ideas? It's my first time doing linux - have I done something silly when removing the driver?

---

### Post by ianmillington on 2013-04-15
What version (and variant eg kubuntu) are you running? As noted above, my experience is that with 13.04 (which has the 3.8 kernel) the RTL8723ae wireless card just works.

I've been running kubuntu 13.04 since it hit beta stage without a problem so that might be a relatively pain-free solution to your problem.

---

### Post by charliewarlie on 2013-04-15
I'm running Ubuntu 12.10, which is kernal 3.5 I think(?)

---

### Post by ianmillington on 2013-04-15
Okay so you are not an LTS user (12.04), so I assume that at the end of this month when 13.04 final is out you would be upgrading anyway.

For a permanent fix to this problem back up your data to cover you in the unlikely event something goes wrong and then follow the instructions here:

[https://wiki.ubuntu.com/RaringRingtail/TechnicalOverview](https://wiki.ubuntu.com/RaringRingtail/TechnicalOverview)

Having checked on my own system there don't appear to be any exotic wireless packages and checking for additional drivers discloses no proprietary drivers are available for the system, so simply upgrading to the a version with the 3.8 kernel ought to do it. 

Allow a couple of hours for the whole process (assuming you have a decent broadband speed).

---

### Post by charliewarlie on 2013-04-15
Just had a look at that link - it says for 'desktop system' - does that mean it won't work on my laptop?

---

### Post by ianmillington on 2013-04-15
It'll be fine - it's simply differentiating it from the server version.

---

### Post by charliewarlie on 2013-04-15
Thanks :) I did the first steps, but when I type in "update-manager -d" into the command box, nothing happens... :confused:

---

### Post by ianmillington on 2013-04-15
Very strange! I assume you didn't use the quotes in the command and that you have correctly configured the software manager? 
Wonder whether you might be better downloading and then creating a bootable usb or DVD. Before doing that, however, can I ask whether you have a separate partition for your home directory? If you don't you will absolutely need to back up as a fresh install of 13.04 will wipe all the data and you will definitely need to restore it. The benefit of doing it that way is you will be able to try the new version on a live basis before installation and satisfy yourself that the wireless does, in fact, work out of the box.

---

### Post by charliewarlie on 2013-04-15
Yup, no quotes, and did exactly as it said with the software manager! =S

That might be an idea - I haven't created any partitions, no. I do have an external hd I can back it all up to though. I'm off out now until tomorrow night, will have a go at sorting it this way then.

---

### Post by ianmillington on 2013-04-15
It's certainly worth doing it that way. That way you can do fresh installs of each version when they are out but you don't have to reconfigure everything as all your settings are retained. Saves a lot of time. Come back if you need any pointers on the partitioning.

---

