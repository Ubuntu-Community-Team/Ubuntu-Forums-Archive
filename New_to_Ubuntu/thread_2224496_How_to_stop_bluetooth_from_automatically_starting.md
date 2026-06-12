---
title: "How to stop bluetooth from automatically starting"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-05-16
Hi, 

As the title says, I want to find a way to prevent bluetooth from autostarting  but not to remove or disable it. I cannot find an entry for bluetooth in autostart applications even though I have configured it to show all hidden applications already.

Ubuntu 14.04 

Thanks.

---

### Post by deadflowr on 2014-05-16
Ubuntu's wacky reasoning to hide start-up applications, which are system-wide, versus user-only.
Try this
```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
```

Which should list all start-up apps.

From here
[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

---

### Post by monkeybrain20122 on 2014-05-16
> **deadflowr said:**
> Ubuntu's wacky reasoning to hide start-up applications, which are system-wide, versus user-only.
Try this
```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop
```

Which should list all start-up apps.

From here
[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

I did that already, but no bluetooth.

---

### Post by vasa1 on 2014-05-16
See if this link helps: [http://packages.ubuntu.com/trusty/bluez](http://packages.ubuntu.com/trusty/bluez)

---

### Post by deadflowr on 2014-05-17
Well, not the perfect solution, but if you add 
```
rfkill block bluetooth
```
to /etc/rc.local (before the exit 0 line)
it will prevent bluetooth from loading at start-up.

You can easily turn it on by re-toggling the on/off switch in the indicator.

Like I stated, not perfect.

---

### Post by monkeybrain20122 on 2014-05-17
> **deadflowr said:**
> Well, not the perfect solution, but if you add 
```
rfkill block bluetooth
```
to /etc/rc.local (before the exit 0 line)
it will prevent bluetooth from loading at start-up.

You can easily turn it on by re-toggling the on/off switch in the indicator.

Like I stated, not perfect.

Hi, that is what I am doing right now. I am actually doing this just for testing. The laptop doesn't resume from hibernation reliably with 14.04 (13.10 no problem) and based on the screen output Bluetooth seems to be the culprit. Will do some more tests and start a different thread on hibernation.

---

### Post by monkeybrain20122 on 2014-05-17
Opps, I just realize that I can do the test by just  switching it off and then close the lid. It shouldn't start when wake  from hibernation as it is not a reboot.

---

### Post by matt_symes on 2014-05-19
Hi

Create an override file in /etc/init for bluetooth.

This will stop upstart starting the bluetooth service when booting up.

Kind regards

---

