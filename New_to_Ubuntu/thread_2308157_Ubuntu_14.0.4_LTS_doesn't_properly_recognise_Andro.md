---
title: "Ubuntu 14.0.4 LTS doesn't properly recognise Android 6.0.1"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by Daveski17 on 2015-12-31
I used to be able to connect my Nexus 7 to my Lenovo laptop (factory installed with Ubuntu 14.0.4 LTS) via USB to transfer files. I have recently discovered Android 6.0.1 will not do this anymore. Furthermore, Windows Vista, which previously allowed file transfers, won't either. Win 7 has never been able to allow file transfer with my Nexus 7.

[IMG]http://i386.photobucket.com/albums/oo307/Davebucket17/nexusdocked1_zpsubg76qgs.jpg[/IMG]

As you can see, it will recognise the Nexus but it will not display any of its file folders. Is there a fix for this?

Thanks, Dave.

---

### Post by sandyd on 2015-12-31
I'm running CM 13 on Nexus 7. Not sure if this solution requires 15.10 as that is what I am running. I don't have a 14.04 machine to test - sorry.

This issue seems to be caused by android.

Normally, plugging in the nexus 7 results in a blank folder, or no storage, or a message requiring me to unlock my device (which I have).

Open up the Developer Options, and make sure "Select USB Configuration" is set to MTP. Then, plug in the Nexus 7 to the computer. Pull the status bar down (There will be no icon indicating for you to do this), and tap on "USB for file transfer" (or similar, CM has renamed some stuff). Choose "File Transfers" and it should start working automatically.

---

### Post by Daveski17 on 2015-12-31
> **sandyd said:**
> I'm running CM 13 on Nexus 7. Not sure if this solution requires 15.10 as that is what I am running. I don't have a 14.04 machine to test - sorry.

This issue seems to be caused by android.

Normally, plugging in the nexus 7 results in a blank folder, or no storage, or a message requiring me to unlock my device (which I have).

Open up the Developer Options, and make sure "Select USB Configuration" is set to MTP. Then, plug in the Nexus 7 to the computer. Pull the status bar down (There will be no icon indicating for you to do this), and tap on "USB for file transfer" (or similar, CM has renamed some stuff). Choose "File Transfers" and it should start working automatically.

OK thanks.

---

### Post by mc4man on 2016-01-01
While dev mode would 'work', here (nexus7, nexus 6p on marshmallow),  it's not needed. After plugging in the option will show up in Notifications, default is USB for charging.. touch to change.
There isn't any means I see to change the default, here charging is the most likely anyway.

---

### Post by Daveski17 on 2016-01-01
> **mc4man said:**
> While dev mode would 'work', here (nexus7, nexus 6p on marshmallow),  it's not needed. After plugging in the option will show up in Notifications, default is USB for charging.. touch to change.
There isn't any means I see to change the default, here charging is the most likely anyway.

Yes, you are right. I discovered that you have to change the default enable file transferring by tapping a radio button on the Android dropdown.

---

