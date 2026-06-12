---
title: "Howto: Terratec Cinergy C HD in Ubuntu 10.10"
date: 2010-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by blueturtl on 2010-10-12
[SIZE="4"]View and record digital broadcasts with Terratec Cinergy C HD[/SIZE]
Last updated on April 3rd, 2011

This DVB-C tuner works in Ubuntu with relative ease since 10.10 (probably even 10.04) since the Mantis driver is now included in the kernel. However for some reason the driver does not load automatically as I write this.

To load the driver manually open a terminal from the menu (Applications->Accessories->Terminal) and enter the following commands:
```
sudo modprobe tda10021
sudo modprobe mantis
```

Alternatively append the mentioned modules in your /etc/modules file.
You may do this with the command:
```
gksu gedit /etc/modules
```

After this the tuner is present and fully functional.

For a quick and easy solution on how to watch broadcasts do the following:
```
sudo apt-get install w-scan me-tv
```

```
w_scan -fc -c<country code> -x >> initial_scan.txt
```

Then run Me TV from the menu, and when prompted about channel search choose the option to use initial scan data and feed the initial_scan.txt file you just generated to the program.

Me TV also allows for recording if you leave it on (you can click the tray icon to hide the video/mute the audio while doing so).

**_Known issues:_**

For me the card no longer seems to function after waking up from suspend: Me TV will run, but fail to lock on to any channel. This can be remedied by re-inserting the driver modules (happens automatically on reboot). To restore the card to working order without rebooting remove the modules first by going back to the terminal and removing the modules:
```

sudo modprobe -r mantis
sudo modprobe -r tda10021
```

Then just reinsert them as already instructed above.

You can automate this process by editing the file /etc/pm/config.d/modules and appending the following to it:
```
#These modules will be automatically removed when suspending
SUSPEND_MODULES="mantis"
```
If the file or said line are already present, just add the module "mantis" to the end of the list.

Then to have the same module reinserted, create the file /etc/pm/sleep.d/01mantis.sh and add the following content to it:

```
#!/bin/bash
case $1 in
resume)
/sbin/modprobe mantis
;;
thaw)
/sbin/modprobe mantis
;;
esac
```

Then make the file executable with
```
sudo chmod +x /etc/pm/sleep.d/01mantis.sh
```

This script will be run whenever the computer comes out of suspend and will reload the module for you automatically. If you need to, you can append the module tda10021 to both of these files, but I found for me it was not necessary. If you need to, make sure the tda10021 is loaded first, and unloaded last.

_**More information**_
I have submitted a bug report ([bug #663892]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/663892")) to launchpad so that the card would be automatically detected and used in future versions and also work with suspend.

---

### Post by mixu75 on 2010-11-03
Thank you, iso kiitos! :popcorn:

---

### Post by blueturtl on 2011-04-03
> Thank you, iso kiitos! :popcorn:

Ole hyvä!

Nyt toimii myös valmiustilan kanssa...

Now with a work-around for suspend. :)

---

