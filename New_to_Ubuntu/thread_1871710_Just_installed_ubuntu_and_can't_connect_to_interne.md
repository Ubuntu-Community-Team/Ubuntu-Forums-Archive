---
title: "Just installed ubuntu and can't connect to internet"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by mitchnufc on 2011-10-29
Hello,

I have just installed Ubuntu alongside Windows 7 on my laptop. I have tried to connect to my wireless hub using correct key etc..... But it just won't connect for some reason and is always saying connecting offline, any ideas?

---

### Post by nogoodnamesleft on 2011-10-29
Double check all connection info. Different operating systems might assume certain defaults.

Check the SSID and 'password' (key). Make sure you know whether it is asking for an english language password, or hex digits of the key itself - quite a few older wireless hubs didn't do this properly and I remember having to type in hex digits directly to connect to some older wireless systems eg 'ea87ffbc0091' instead of 'p4sswErd' (this was a fault of the wireless box, not the operating system).

Then check the wireless settings - channel, authentication method etc (probably WPA2-PSK on a new netwotk, but it might be WEP or something.

Might be an idea to look in the settings for Win 7 just in case they aren't what you had remembered them as.

---

### Post by mitchnufc on 2011-10-29
> **nogoodnamesleft said:**
> Double check all connection info. Different operating systems might assume certain defaults.

Check the SSID and 'password' (key). Make sure you know whether it is asking for an english language password, or hex digits of the key itself - quite a few older wireless hubs didn't do this properly and I remember having to type in hex digits directly to connect to some older wireless systems eg 'ea87ffbc0091' instead of 'p4sswErd' (this was a fault of the wireless box, not the operating system).

Then check the wireless settings - channel, authentication method etc (probably WPA2-PSK on a new netwotk, but it might be WEP or something.

Might be an idea to look in the settings for Win 7 just in case they aren't what you had remembered them as.

Its a newer model hub, BT 2.0 to be accurate. I've tried both the WEP & WPA. It seems to accept the first but then nothing happens.

---

### Post by roger_1960 on 2011-10-29
Hi

Is the PC seeing the network ie does it appear in the dropdown list, OR are you pre configuring a connection and then trying to connect?

Do you have "enable networking" and "enable wireless ticked" in the dropdown or are they greyed out?

---

### Post by mitchnufc on 2011-10-29
Yes the wireless network is available from the drop list, will have to get back to you on the later as I'll have to reboot. They are both enabled.

---

### Post by nogoodnamesleft on 2011-10-29
bt home hub 2.0 will not give 2 ip addys to the same mac address

put a static address into the ubuntu box

BT know about this and they say put a static addy into the Ubuntu box until they get a patch out.

Google it, it's a known problem they claim they will fix 'before the end of 2011'

edit: link here from BT's forums

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/2](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/2)

It suppose to be fixed now but i guess you didnt get the update from BT yet



edit 2: this message in the thread has a workaround for ubuntu oneiric

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/m-p/287685#M96919](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/m-p/287685#M96919)

however i would yell at BT for the upgrade

---

### Post by mitchnufc on 2011-10-29
> **nogoodnamesleft said:**
> bt home hub 2.0 will not give 2 ip addys to the same mac address

put a static address into the ubuntu box

BT know about this and they say put a static addy into the Ubuntu box until they get a patch out.

Google it, it's a known problem they claim they will fix 'before the end of 2011'

edit: link here from BT's forums

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/2](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/2)

It suppose to be fixed now but i guess you didnt get the update from BT yet

Cheers for this:D

Also on previous versions of Ubuntu I've used there was a tab at the top left that allowed you to browse all applications this version doesn't seem to have that. Can anyone advise me where I can access gtexteditor and terminal from.

---

### Post by roger_1960 on 2011-10-29
Hi

Press the "windows" key and then type

gedit (or text)

or 

terminal

and icons will appear which you can click.  Once the app is running, right click on its icon in the launcher at the left and select "keep in launcher" if you want a permanent link.

---

### Post by mitchnufc on 2011-10-29
I done the steps for assigning a static ip but it won't allow me to save them, save button is greyed out!

---

### Post by mitchnufc on 2011-10-29
bump

---

### Post by nogoodnamesleft on 2011-10-29
is there a lock icon? i dont use oneiric but it looks like mac os (except mac os's UI works) so it probably has a an icon with a padlock you have to click on to make or save changes. and make sure your user account has appropriate permissions. I cant really help anymore; i know my routers and my comms but not oneiric desktop. Maybe make a 2nd thread for this specific issue, as you need a desktop guy and they might not look at this thread because of the title?

---

### Post by stuarttanner on 2011-10-31
This problem is now fixed on my BT homehub 2. i see BT have now done the update to put this right.



BT what a absolute nightmare...:confused:

---

### Post by nogoodnamesleft on 2011-11-01
> **stuarttanner said:**
> BT what a absolute nightmare...:confused:

Yet you persist with them? :-)

A lot of good smaller ISPs with excellent service. Avoid the national brands which sell on their name rather than QoS.

---

