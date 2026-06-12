---
title: "script to start openfire on startup"
date: 2012-08-07
forum: Programming Talk
---

### Post by c2tarun on 2012-08-07
Hi friends,

I configured openfire on my system as a LAN chat server. I want to write a script to start openfire automatically when system starts.
Lets say I write the script as:

```

sudo /etc/init.d/openfire start

```

The problem is it requires sudo access. It will ask for password or may give an error or something but there are chances that openfire will not be started. Is there anyother way to write this kind of script?

---

### Post by mevun on 2012-08-07
I haven't tried it before, but supposedly you want to use a program like "sysv-rc-conf" or "sysvconfig" which will start the program at boot time.

e.g. sysv-rc-conf openfire on

It won't start the service when you enter that command; it just configures it to do so the next time your system boots.

---

### Post by Pinoy Tux on 2012-08-08
Add it to the /etc/rc.local file, before the exit 0:

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

/etc/init.d/openfire start

exit 0
```IINM, commands in the rc.local file gets executed as root.  There may be no need for sudo.

HTH.

---

