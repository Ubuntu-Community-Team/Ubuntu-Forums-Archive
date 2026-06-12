---
title: "GPRS USB Modem Treo 650 Cingular Linux"
date: 2006-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by oneguynick on 2006-05-24
*Software*
Make sure you are running the latest versions of firmware for the Treo 650. I happen to have an unlocked edition so this is very easy to fix from PalmOne. I recommend going with the latest but this isnt a deal breaker. I am going to assume this from a total newbie position as yes, you can use pppd or wvdial from CLI. For our test we will be using Ubuntu 6.06 and Gnome-ppp. To enable “tethered” mode on the Treo you maybe lucky and dial #*83843733. I was unable with GSM and Cingular and instead used this software which works wonderfully. If anything they also officially support Linux. Sweet!

[http://mobile-stream.com/usbmodem.html](http://mobile-stream.com/usbmodem.html)

*Hardware*
The hotsync USB cable will be all that is needed. I have problems in the past plugging into an external USB hub so keep that in mind.

*Installing Software*
I downloaded the USB Treo program and explored the zip file. I extracted the PRC to a SD-Card 
```
PALM\LAUNCHERS
```

and reinserted into the Treo. There was the program. I clicked enable USB modem and plugged the USB hotsync cable in. At this point I
```
apt-get install gnome-ppp
```

and waited for that to finish. Check dmesg for ttyACM0 to ensure that the kernel did pickup the hotplug device.

*Gnome-PPP Settings*
Before we can even start on that portion of the install lets enable a few LCP options we will need to ensure the connection stays put.

```
sudo vi /etc/ppp/options
```

Find in the conf file:
```
lcp-echo-failure 4
``` and change it to... ```
lcp-echo-failure 0
```

Next run Gnome-PPP from your applications menu. The settings most important here will be the username and password:

```
u: WAP@CINGULARGPRS.COM
p: CINGULAR1
```

Also for the phone number put: ```
*99***1#
```

The final dialog box should look like this:

[img]http://i39.photobucket.com/albums/e192/oneguynick/Screenshot-GNOME20PPP.png[/img]

Lets digg into some of the options you may need to check to ensure this is transparent:

Init Strings needed:

[img]http://i39.photobucket.com/albums/e192/oneguynick/Screenshot-Init20Strings.png[/img]

Setup Dialog Box 1:

[img]http://i39.photobucket.com/albums/e192/oneguynick/Screenshot-Setup.png[/img]

Setup Dialog Box 2:

[img]http://i39.photobucket.com/albums/e192/oneguynick/Screenshot-Setup-1.png[/img]

After all is said and done. Click connect! You should see the gnome-ppp dock itself and lights start flashing. Something to keep in mind is that if your default route is pointing to eth0/wifi0 you will need to pull those interfaces down before the ppp0 can take over. Enjoy!

---

