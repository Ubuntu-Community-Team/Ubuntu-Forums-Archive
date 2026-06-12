---
title: "available wireless networks?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by will22 on 2008-10-31
I've upgraded to 8.10, but now i can't find where i can see available wireless networks?
The network icon in the right top corner is gone as well.

Please advise.

Thank you.

---

### Post by bumanie on 2008-10-31
What type of wireless card do you have? If it is atheros AR242x it doesn't work without tweaking. I used ndiswrapper to get mine going.

---

### Post by Pconfig on 2008-10-31
Does it use restricted drivers? If yes, you'll have to enable them again in 

System > Administration > Hardware drivers

---

### Post by will22 on 2008-10-31
my card is PRO/Wireless 3945ABG (dell inspiron 9400)
everything was working fine before upgrade.

I can connect wireless in i enter info manually via network manager (SSID, etc).
But where i can see all available networks, signal strength?

---

### Post by Pconfig on 2008-10-31
Have you got the package 'network-manager-gnome' installed?

---

### Post by will22 on 2008-10-31
yes, installed

---

### Post by Pconfig on 2008-10-31
Does

nm-applet --sm-disable

make the network icon appear?

---

### Post by will22 on 2008-10-31
> **Pconfig said:**
> Does

nm-applet --sm-disable

make the network icon appear?

this is what i get:

** (nm-applet:13086): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:13086): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by Pconfig on 2008-10-31
Hm, could it be possible that your accidentally removed the notification area from you gnome panel? Do you still see the speaker icon and such?

Try adding one again

---

### Post by will22 on 2008-10-31
i added network monitor, but it only shows current connection.
and i see that it ignore my settings - just blindly broadcasting

---

### Post by Pconfig on 2008-10-31
Well the default network manager should show up in the notification area. If you don't have one on your panels it might not show up..

---

### Post by will22 on 2008-10-31
yes, it's missing. How can i add it?

---

### Post by Pconfig on 2008-10-31
Just right click a gnome panel --> Add to panel --> Notification area

You might need to reboot to get icons in there.

---

### Post by will22 on 2008-10-31
i'm sorry, i didn't make myself clear.
Notification area is there, but no default network manager

---

### Post by Pconfig on 2008-10-31
Well, i ran out of options then. Hope someone else can help you out :)

---

### Post by will22 on 2008-10-31
Thanks for the effort :)

---

### Post by barnabus on 2008-10-31
I had the same issue when on my first boot after the upgrade, but after i rebooted again it was back

---

### Post by will22 on 2008-10-31
rebooted, network manager still missing :(

---

### Post by Amurko on 2008-10-31
I've had this issue when upgrading..  it seems the wlanassistant program I used to use to select wireless networks is no longer supported.

try sudo apt-get wlan-radar

for a new wlan manager that's currently supported.  If you can't get on the internet, you may need to download the deb to a usb disk first

---

### Post by hyper_ch on 2008-10-31
I started to like WICD as network manager. You may want to try that one :)

---

### Post by will22 on 2008-10-31
E: Invalid operation wlan-radar

---

### Post by bumanie on 2008-10-31
With an atheros wi-fi card, I had to resort to using ndiswrapper - nothing else would work, however it worked until the final kernel upgrade during the rc stage. May be try ndiswrapper - available from the repo's - then find the .inf file for your card.

---

### Post by Pconfig on 2008-10-31
> **will22 said:**
> E: Invalid operation wlan-radar

sudo apt-get install wlan-radar

He forgot the install ;)

---

### Post by will22 on 2008-11-01
Thank you, guys!

Only hyper_ch suggestion worked for me (WICD manager)

---

