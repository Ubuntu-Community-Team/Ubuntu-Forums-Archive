---
title: "USB Device Permissions Change At Reboot"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by AlistairH on 2013-07-16
I'm in the middle of a project to illustrate to a client that they could use Xubuntu instead of Windows XP and save themselves a bundle in upgrade costs.

They currently use a digital dictation transcript program for which I've found a Linux based replacement.... Express Scribe. I'm having an issue with the use of USB foot pedals however. When running the software, the users are presented with a request for a root password in order to use the foot pedal (which is recognised at /dev/usb/hiddev0). Unfortunately, the ownership and permissions for this device are assigned to root and so, as desktop users, have no administrative rights at all.

Changing the permissions and ownership using chmod and chown work temporarily, but if the foot pedal is unplugged or the machine rebooted, the permissions and ownership are reset to root.

I've temporarily assigned the users to the sudo group to allow them to supply their own password when prompted, but ideally I don't want them to be pestered with this at all and I certainly don't want them to belong to the sudo group when/if things go live.

How/where/what do I configure to permanently assign the ownership/permissions of /dev/usb/hiddev0 to the users group say, without them resetting to root on each reboot?

Thanks in advance

---

### Post by dannyboy79 on 2013-07-16
see if this helps: [http://www.weather-watch.com/smf/index.php/topic,39257.0.html](http://www.weather-watch.com/smf/index.php/topic,39257.0.html)
i know the directions talk about a weather-watch device but it all boils down to the correct way to access device nodes by using a group

---

### Post by AlistairH on 2013-07-17
Thanks dannyboy

I won't be back at my clients for a fortnight but that will give me plenty time to get my head around that article. I'll let you know how it goes.

---

