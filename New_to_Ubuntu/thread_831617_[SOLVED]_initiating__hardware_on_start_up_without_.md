---
title: "[SOLVED] initiating  hardware on start up without typing in the commands continually"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by fr.theo on 2008-06-17
hello, all 

just like to say thanks for the great support I am getting from all those in the forum, I hope I can return the kind gestures I have received to others in need. 

but I have a long way to go before I fully understand the linux system until then I have a inquiry.

I have a wirless modem which I use to access the web, however I continually have to type in the command "sudo insmod /lib/moduels/'uname -r '/kernel/\drivers /usb/serial/usbserial.ko \ vendor=0x16d8 product=0x6280"in terminal to initiate the device 

then I type pon provider to turn on the device in order to get connection

is there any way to get Ubuntu to regognize the device on boot up, I have created a shortcut to launch the "pon provider" so that is not a problem I just don't want to continually type the command to initiate the device.

thanks once again for all your help.

Kind regards 

FR. T

---

### Post by sdennie on 2008-06-17
You should be able to add those commands to /etc/rc.local and they will start when the system boots.  You won't need the "sudo" part of the commands because they will be run as root.

---

### Post by fr.theo on 2008-06-17
please exuse my lack of knowladge but could you give me an example of how to input that information into the "RC.LOCAl" file. I have opened the file but need some guidance as I am still an armature at this.



thanks again.


Kind regards 

FR. T.

---

### Post by sdennie on 2008-06-17
Sure.  If I understand your post correctly, I think you will just need to change the file to look like this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe usbserial vendor=0x16d8 product=0x6280
pon provider

exit 0

```

---

### Post by fr.theo on 2008-06-17
thankyou very much, really appreciate it, would like to know would that work for all things like scanners as well?.

---

### Post by sdennie on 2008-06-17
Using rc.local will work for anything that doesn't depend on a user being logged into X.  

There are actually more correct ways to insert modules at boot time (specifically /etc/modules) and more formal ways to set static options for modules (/etc/modprobe.d/options) but, I mostly just mention that so you know.  I can't think of any reason why doing a modprobe in /etc/rc.local would cause any problems.

---

### Post by fr.theo on 2008-06-17
thanks once again for your help, that should cover me for now.


king regards 

FR. T.

---

### Post by sdennie on 2008-06-17
Glad to help.

---

