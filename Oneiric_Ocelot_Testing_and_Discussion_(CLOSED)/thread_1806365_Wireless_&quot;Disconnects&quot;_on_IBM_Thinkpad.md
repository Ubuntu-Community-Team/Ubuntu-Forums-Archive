---
title: "Wireless &quot;Disconnects&quot; on IBM Thinkpad"
date: 2011-07-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-07-17
Wireless on this IBM Thinkpad T40 works fine on Meerkat.  Does not on Ocelot, tries to connect then disconnects.  I found this in the Ubuntu forums:
```

# http://ubuntuforums.org/showthread.php?t=255704
# Here is my fix (I placed this script in /etc/network/if-pre-up.d):
# Code:

#!/bin/sh
#
# This script takes care of configuring cisco wireless
# cards using the airo driver such as 340 and 350 cards.
# It is run by ifup.

AIROPROC=/proc/driver/aironet
CONFIG=Config
SLEEP=2

#some sanity checks
if [ ! -d $AIROPROC ] ; then
        exit 0
fi

for i in $AIROPROC/* ; do
   if [ -w "$i/$CONFIG" ] ; then
       echo "Preamble: long" > "$i/$CONFIG"
   fi
done
sleep $SLEEP
exit 0

```
The airo driver is in fact in the Ocelot kernel and tries to connect, but then is Disconnected.  I tried ubuntu-bug kernel since the drivers are in the kernel, but ubuntu-bug does not recognize the kernel.

Any clues on how to do a launchpad bug for this?

Thanks, Jerry

---

### Post by mc4man on 2011-07-17
Have you tried doing the initial setup using indicator > edit connections > ect.
(that's the only way i've found recently to get wireless going, after setup works fine on subsequent boots

---

### Post by jerrylamos on 2011-07-17
> **mc4man said:**
> Have you tried doing the initial setup using indicator > edit connections > ect.
(that's the only way i've found recently to get wireless going, after setup works fine on subsequent boots
mc4man, I've spent some time with edit connections with no luck.

Ocelot sees the connection, gets the network name right, tries to connect, then something in the Ocelot kernel Disconnects.  Doesn't say who or why.

I restart boot Maverick or Lynx and they run fine, same airo drivers.  It's either a Ocelot wireless code bug or a Ocelot kernel bug, but ubuntu-bug doesn't recognize "kernel" or "network" as a package so I can't do a launchpad bug with apport.

Thanks, Jerry

---

### Post by mc4man on 2011-07-17
I guess 
ubuntu-bug linux

---

### Post by jerrylamos on 2011-07-17
> **mc4man said:**
> I guess 
ubuntu-bug linux

Thanks, I tried it.

ubuntu-bug linux

"Problem in linux-image-3
 The problem cannot be reported
 This is not a genuine Ubuntu package"

So Ocelot is not a "genuine Ubuntu package"....

Jerry

---

### Post by mc4man on 2011-07-17
Works here, (bug report),  using latest (linux-image-3.0.0-5-generic / linux-image-generic (3.0.0.5.6
Otherwise - 
linux (Ubuntu) bug reporting guidelines:

> Please report a bug about the kernel using the following command in a terminal:

 ubuntu-bug linux

This will automatically gather information that will help us investigate your bug report.

**Alternatively**, at a minimum include the output of the following commands executed in a terminal as separate attachments in your bug report:

1) cat /proc/version_signature > version.log
2) sudo lspci -vnvn > lspci-vnvn.log

Depending on the nature of your bug report following the instructions at [https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging) will make your bug report even more complete. Thanks!

Is there anything related in /var/crash/?

---

### Post by ronacc on 2011-07-17
I had that problem with natty and my realtek 8185 wireless card , fought it the whole time but it never got fixed until the first orc kernel .

---

### Post by jerrylamos on 2011-07-18
> **mc4man said:**
> Works here, (bug report),  using latest (linux-image-3.0.0-5-generic / linux-image-generic (3.0.0.5.6
Otherwise - 
linux (Ubuntu) bug reporting guidelines:


Is there anything related in /var/crash/?

I looked.  Ocelot just decides to disconnect. There might be something in the various logs but I don't know enough to understand the problem(s). 

So I run Lucid LTS for wireless - how long is it before Lucid loses Ubuntu support?

Thanks, Jerry

---

### Post by cariboo on 2011-07-18
@jerrylamos, the LTS desktop release is supported for 3 years, so 10.04 + 3 = 13.04, so you've got a couple of years to get your wireless problem sorted. :) :)

---

