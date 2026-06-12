---
title: "Suspend on Dell E1505 with ati X1400 +edgy"
date: 2007-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by jlc on 2007-01-15
Here is what I did to get it to work, I used several post to get it to work and I haven't had suspend not work yet!  Check my blog for updates:

[http://blog.justinconover.com/2007/01/15/suspend-on-ubuntu-dell-e1505-part-2/](http://blog.justinconover.com/2007/01/15/suspend-on-ubuntu-dell-e1505-part-2/)

1.)  Add the fglrx drivers doing the manual and add the following:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

$ sudo vi /etc/default/linux-restricted-modules-common
```

DISABLED_MODULES=&#8221;fglrx&#8221;

```

2.)  Add the following &#8220;return 1;&#8221; to powernowd at use_ondemand

$ sudo vi /etc/init.d/powernowd
```

use_ondemand() {
return 1;
for x in /sys/devices/system/cpu/*; do
echo -n ondemand >$x/cpufreq/scaling_governor;
status=$?
if [ $status != 0 ]; then
return $status
fi
done
return 0
}

```

$ sudo /etc/init.d/powernowd restart

3.)  Create 2 network scripts to restart ipw3945
$ sudo vi /etc/acpi/suspend.d/07-networkmanager.sh
```

!/bin/sh

/usr/bin/dbus-send &#8211;system \
&#8211;dest=org.freedesktop.NetworkManager \
&#8211;type=method_call \
/org/freedesktop/NetworkManager \
org.freedesktop.NetworkManager.sleep

```

And

$ sudo vi /etc/acpi/resume.d/63-networkmanager.sh
```

#!/bin/sh

/usr/bin/dbus-send &#8211;system \
&#8211;dest=org.freedesktop.NetworkManager \
&#8211;type=method_call \
/org/freedesktop/NetworkManager \
org.freedesktop.NetworkManager.wake

```
If the formating gets messed up, check out this post, about 7 down:
[http://www.ubuntuforums.org/showthread.php?t=271980&highlight=ipw3945+%2Bsuspend](http://www.ubuntuforums.org/showthread.php?t=271980&highlight=ipw3945+%2Bsuspend)

4.)  Add the following to acpi-support

$ sudo vi /etc/default/acpi-support
```

MODULES_WHITELIST=&#8221;ipw3945 fglrx&#8221;
SAVE_VBE_STATE=true
POST_VIDEO=false
SAVE_VIDEO_PCI_STATE=true
USE_DPMS=tru
# DOUBLE_CONSOLE_SWITCH=true

```

5.)  Change Power Management &#8220;Running on Battery&#8221; to &#8220;SUSPEND&#8221; when laptop lid is closed:
```

System > Preferences > Power Management > Running on Battery
When laptop lid is closed;    Suspend

```


That seems to be the special mojo to get suspend working.

---

### Post by watersprayer on 2007-12-07
Hello,
Ubuntu 7.10 on Dell E1505 with Ati x1300

I follow your instructions completely, but at step #2 where I need to modify "powernowd at use_ondemand" I am unable to edit the module, for some reason I am unable to type "return 1:"

I did get this message: "E325: ATTENTION
Found a swap file by the name "/etc/init.d/.powernowd.swp"
          owned by: root   dated: Fri Dec  7 08:02:45 2007
         file name: /etc/init.d/powernowd
          modified: YES
         user name: root   host name: brian-laptop
        process ID: 6135
While opening file "/etc/init.d/powernowd"
             dated: Mon Dec 18 19:35:32 2006

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/init.d/powernowd"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/init.d/.powernowd.swp"
    to avoid this message.
"/etc/init.d/powernowd" 158 lines, 4108 characters
Press ENTER or type command to continue

"

I am not sure how to edit the swap file or if this is the correct method.

---

