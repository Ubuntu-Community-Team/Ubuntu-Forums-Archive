---
title: "[SOLVED] Curious Shutdown Message"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Dumpy Dumpster on 2008-06-17
First of all Hardy Heron is working fine and I don't want to upset it!!  But I am curious as to what this message means when it is displayed on shutdown, which also works fine.  I have dragged and dropped the image into this message so I hope it will work, if not I will submit a transcript
file:///home/michael/Desktop/Screenshot.png.

---

### Post by Dumpy Dumpster on 2008-06-17
My attempt to get the photo has not worked - so here is what it says:

Network Manager: <WARN> nm_hal_deinit():shutdown failed - connection is closed
Network Manager <WARN> nm_dbus_init():nm_dbus_init() could not get the system bus.  Make sure the message bus daemon is running
*And then three times:*
Network Manager :nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus connection' failed

---

### Post by _sphinx_ on 2008-06-17
no image..

---

### Post by forestpixie on 2008-06-17
I get the same message but take absolutely no notice at all :) - but it must be said that restart doesn't on hardy (or feisty or gutsy)

This might help you as well

[How do I attach an image to my post?]("http://ubuntuforums.org/showpost.php?p=4527031&postcount=4")

---

### Post by prshah on 2008-06-17
> **Dumpy Dumpster said:**
> - so here is what it says:

Network Manager: <WARN> nm_hal_deinit():shutdown failed - connection is closed
Network Manager :nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus connection' failed

> **forestpixie said:**
> 
but it must be said that restart doesn't on hardy (or feisty or gutsy)



That message comes for me too; you can safely ignore it, it's just a debug message.

For failing reboots, first try this a couple of times:```
sudo reboot -hni
``` and if it works fine, post back on how to make it the permanent method.

---

### Post by fatality_uk on 2008-06-17
Agreed. It's just debug messages.
Unless it's effecting you shutdown, it's safe to ignore.

Mine does it on each shutdown :D

---

### Post by forestpixie on 2008-06-17
> **prshah said:**
> For failing reboots, first try this a couple of times:```
sudo reboot -hni
``` and if it works fine, post back on how to make it the permanent method.


No different - but I think I tried that once before - it's no biggy if I need to restart I let it get as far as it as the splash screen or whatever it's called weait and see and press the button :)

What is a touch peculiar is that sometimes it works, most times it doesnt - but if it's a restart from a kernel change etc. it's the other way round - most times it works and sometimes it doesn't.

---

### Post by Dumpy Dumpster on 2008-06-17
Thank all for your treouble - I thought that it was not doing any harm, but always to check with the experts.
Thanks also, forestpixie for your help in adding images to posts - duly bookmarked.

---

### Post by Dumpy Dumpster on 2008-06-17
Thank all for your trouble - I thought that it was not doing any harm, but always to check with the experts.
Thanks also, forestpixie for your help in adding images to posts - duly bookmarked.

---

