---
title: "Touchpad not working in Ubuntu 11.10"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by Jary316 on 2011-10-30
Hi,

I have a problem with my touchpad since I updated from Ubuntu 11.04 to 11.10 on my ASUS N61J laptop.

My touchpad used to work just fine, and I had touchpad-indicator installed, but since the update, the touchpad doesn't work at all.

I have tried to:
  - Update touchpad-indicator
  - Uninstall touchpad-indicator through apt-get
  - Install synaptiks. I've read that this is a common problem and the way to solve it is to install synaptiks, reboot and launch synaptiks.

None of the things I have tried worked. I cannot move the mouse with the touchpad, or left click, or right click.

Does anyone please have a solution?

Thank you very much.

---

### Post by antoinethewiz on 2011-10-30
First, make sure the touchpad is enabled (should be a button above pad that enables/disables). Now, did you have to install proprietary drivers for the touchpad on 11.04? If so, open up "System > Administration > Hardware Devices" and activate the appropriate driver. If it's not there, check the manufacturer's website. Then, go to "System > Administration > Update Manager" to check for driver updates.

If it's none of these, I suppose it's possible that an update was corrupted due to network packet failures (should result in a different md5sum). So, you could either re-update or rollback the driver.

If that doesn't solve it, then I couldn't tell you (Xorg.conf maybe? doubt it). I would recommend contacting the manufacturer.

---

### Post by Jary316 on 2011-10-31
> **antoinethewiz said:**
> First, make sure the touchpad is enabled (should be a button above pad that enables/disables). Now, did you have to install proprietary drivers for the touchpad on 11.04? If so, open up "System > Administration > Hardware Devices" and activate the appropriate driver. If it's not there, check the manufacturer's website. Then, go to "System > Administration > Update Manager" to check for driver updates.

If it's none of these, I suppose it's possible that an update was corrupted due to network packet failures (should result in a different md5sum). So, you could either re-update or rollback the driver.

If that doesn't solve it, then I couldn't tell you (Xorg.conf maybe? doubt it). I would recommend contacting the manufacturer.

Hi, thanks a lot for your help.

I checked your ideas, this is what I can report: there are no buttons to turn on or off my touchpad. My touchpad still works in Windows 7. When I installed Ubuntu 11.04, the touchpad started working immediately (no driver installation were made by me).

I cannot find Hardware Devices in Unity. I checked "Additional drivers", but it is not there.

Any advice please?

Thank you.

---

### Post by christian.convey on 2011-11-01
Try this: [http://askubuntu.com/questions/66907/touchpad-not-working-on-msi-u130-after-login-in]("http://askubuntu.com/questions/66907/touchpad-not-working-on-msi-u130-after-login-in")

---

### Post by Jary316 on 2011-11-03
> **christian.convey said:**
> Try this: [http://askubuntu.com/questions/66907/touchpad-not-working-on-msi-u130-after-login-in]("http://askubuntu.com/questions/66907/touchpad-not-working-on-msi-u130-after-login-in")


Thanks a lot! The second comment fixed my problem! Awesome, thank you very much!

---

