---
title: "wg111v2 ndis guide"
date: 2006-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by wthww on 2006-07-30
ok, this is my first attempt at a "guide". so please, bear with me. 

ok,

#1 Download this gzipped file [http://compusplurge.scratchdrive.com/win2000-wg111v2.tar.gz](http://compusplurge.scratchdrive.com/win2000-wg111v2.tar.gz)

2 Go to Synaptic. Select Ndis tools, and mark for installation. click "apply" at the top

3 click search. type in "ndisgtk". mar for install and click "apply"

4 unzip the file youve downloaded. to your desktop.

5 open a terminal. type ```
 sudo ndisgtk 
``` and hit enter. it mat 
ask you for a password. enter it and click ok.

6 Now you should have the Ndisgtk autility open. click "install new drivers"

7 CLick the drop-down-box. double click "Desktop", then double click "WIN2000".

8 Select net111v2.inf. Clcik close.

9 open a terminal. type this into your terminal.
```
sudo gedit /etc/modeprobe.d/blacklist 
```
it may ask for a password. enter your password, and press the "enter" key
add these lines to the bottom:
blacklist rtl818x
blacklist r818x
blacklist rtl8187
blacklist r8187
blacklist islsm_usb
blacklist islsm

10 Save and exit Gedit. Restart and enjoy your wifi. NOTE:You still have to select your accesspoint/router in the network config pannel.

//wthww

---

