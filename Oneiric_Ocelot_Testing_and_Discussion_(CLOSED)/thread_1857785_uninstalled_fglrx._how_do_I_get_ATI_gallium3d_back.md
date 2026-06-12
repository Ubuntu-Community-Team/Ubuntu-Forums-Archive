---
title: "uninstalled fglrx. how do I get ATI gallium3d back?"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bigfamine on 2011-10-11
Hullo,

I had everything working fine with the default open source gallium 3d ATI drivers, and then I installed fglrx.

Now today I uninstall fglrx and am getting libGl errors so im assuming that means I need to reinstall the gallium driver.

Any help?

---

### Post by sonicb00m on 2011-10-11
Here's a script I made to repair when the proprietary driver goes wrong

```

#!/bin/bash

# Remove ATI catalyst and reinstall open source

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

/usr/share/ati/fglrx-uninstall.sh
apt-get remove --purge xorg-driver-fglrx* fglrx* xserver-xorg-video-ati xserver-xorg-video-radeon
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
rm /etc/X11/xorg.conf

```

---

### Post by bigfamine on 2011-10-11
> **sonicb00m said:**
> Here's a script I made to repair when the proprietary driver goes wrong

```

#!/bin/bash

# Remove ATI catalyst and reinstall open source

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root" 1>&2
   exit 1
fi

/usr/share/ati/fglrx-uninstall.sh
apt-get remove --purge xorg-driver-fglrx* fglrx* xserver-xorg-video-ati xserver-xorg-video-radeon
apt-get install xserver-xorg-video-ati
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
rm /etc/X11/xorg.conf

```

Okay, that sorta worked, at least your script pointed me in the right direction

#$apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

That didnt work...So what I did was #$ apt-get remove mesa-glx libgl1-mesa-dri xserver-xorg-core

That then uninstalled the above three packages plus about 150 others.

So then I reinstalled the 150 packages that were removed. rebooted, and now im back to using the gallium3d driver

---

### Post by sonicb00m on 2011-10-11
Ok good. It's a shame the ATI driver stuff is such a hassle.

---

### Post by sonicb00m on 2011-10-11
If you want to give the prop drivers another bash I have this script I used in my install scripts 


```

FILE_ATI="ati-driver-installer-11-9-x86.x86_64.run"
DISTRO="oneiric"

apt-get install libqtgui4
	wget "http://www2.ati.com/drivers/linux/$FILE_ATI"
	sh "$FILE_ATI --buildpkg Ubuntu/$DISTRO"
	dpkg -i *.deb
	apt-get install -f
	aticonfig --initial
	rm fglrx* "$FILE_ATI"

```

---

