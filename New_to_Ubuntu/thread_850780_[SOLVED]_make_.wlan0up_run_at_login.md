---
title: "[SOLVED] make ./wlan0up run at login"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-05
i have an rtl8185 linux driver

every time i start up my computer i have to open a terminal and do this

```
cd wifi
```(it used to be named rtl8185 but i changed it cuz wifi is easier)

then

```
sudo ./wlan0up
```

so how can i make this run at login?


in my other computer i have almost the same driver (rtl8187b) and i was able to add some lines to /etc/rc.local and it worked but with this computer it wont work

any ideas?

---

### Post by sdennie on 2008-07-05
Using /etc/rc.local should work.  Remember that "cd wifi" won't have any meaning from /etc/rc.local.  You will need to use an absolute path to find your script.

---

### Post by tjwoosta on 2008-07-05
what do you mean by absolute path?

what i did was change the actual directory name to wifi instead of rtl8185, should i change it back?

---

### Post by sdennie on 2008-07-05
I mean that if you can login, bring up a terminal and type "cd wifi", that same command won't work because "wifi" is a relative path from your home directory.  You will almost certainly need to do:

```

cd /home/**your_username**/wifi

```

---

### Post by jw5801 on 2008-07-05
Say, for example the script was in your home directory, the absolutel path would be: /home/$(whoami)/wifi.

$(whoami) = your user name.

Why do you need the script to run to get wireless to work? What does the script do?

---

### Post by tjwoosta on 2008-07-05
yea
i already have that

also i renamed the folder back to rtl8185 just incase, but it still didn't work


this is what my rc.local local looks like now (this is my sister ashleys computer so its her home directory)

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
/home/ashley/rtl8185/wlan0up
ifconfig wlan0 up
dhclient wlan0
exit 0

```

this is a the same exact thing thats in my laptop (aside from the directory names obviously) and in my laptop it works great

so why wont it work on this computer?

---

### Post by sdennie on 2008-07-06
> **jw5801 said:**
> Say, for example the script was in your home directory, the absolutel path would be: /home/$(whoami)/wifi.

$(whoami) = your user name.


Yes, this is the general idea but, remember that if something is running from /etc/rc.local, "whoami" should return "root" so, you need to explicitly state the username rather than letting it resolve to $(whoami).

---

### Post by tjwoosta on 2008-07-06
> 
yea
i already have that
.

---

### Post by sdennie on 2008-07-06
> **tjwoosta said:**
> yea
i already have that

also i renamed the folder back to rtl8185 just incase, but it still didn't work


this is what my rc.local local looks like now (this is my sister ashleys computer so its her home directory)


What does the wlan0up script look like?  It's possible that it needs to be run with from the directory in which it lives.  In which case, you'd have to do the "cd" to the right directory and then "./wlan0up".

---

### Post by tjwoosta on 2008-07-06
this is my wlan0up 
```

#!/bin/bash

cd ieee80211
insmod ieee80211_crypt-rtl.ko
insmod ieee80211_crypt_wep-rtl.ko
insmod ieee80211_crypt_tkip-rtl.ko
insmod ieee80211_crypt_ccmp-rtl.ko
insmod ieee80211-rtl.ko

cd ../rtl8185
insmod r8180.ko

cd ../

ifconfig wlan0 up

```

---

### Post by sdennie on 2008-07-06
Right.  That script is using relative paths.  That means that rather than running the script with /home/ashley/rtl8185/wlan0up, you'll have to use:

```

cd /home/ashley/rtl8185
./wlan0up

```

---

### Post by cariboo on 2008-07-06
I don't no if this is correct, but if I use modprobe to load a module I never have to load it agian. If I use insmod I have to reload the module again after a reboot.

Maybe one of the other guys can chime in if my thinking is correct.

Jim

---

### Post by tjwoosta on 2008-07-06
> Right. That script is using relative paths. That means that rather than running the script with /home/ashley/rtl8185/wlan0up, you'll have to use:

Code:

cd /home/ashley/rtl8185
./wlan0up



thanks guys, that did the trick

---

### Post by jw5801 on 2008-07-06
> **vor said:**
> Yes, this is the general idea but, remember that if something is running from /etc/rc.local, "whoami" should return "root" so, you need to explicitly state the username rather than letting it resolve to $(whoami).

I know, it's just good to use as a placeholder :), like <username> or *your-login-goes-here*.

---

### Post by jw5801 on 2008-07-06
> **cariboo907 said:**
> I don't no if this is correct, but if I use modprobe to load a module I never have to load it agian. If I use insmod I have to reload the module again after a reboot.

Maybe one of the other guys can chime in if my thinking is correct.

Jim

That's not correct no. modprobe is a once off, as is insmod. insmod takes a full path and filename, modprobe searches the relevant /lib/modules/$(uname -r)/ directory for *.ko files. I believe that's the main difference.

tjwoosta, why don't you copy the directory to /lib/modules/$(uname -r)/rtl8185/, and then add the names of all those modules to /etc/modules (without the .ko)? That would remove the need to run this clumsy script on every boot.

EDIT: You'd also need to run 'sudo depmod' after copying the folder.

---

### Post by tjwoosta on 2008-07-06
> tjwoosta, why don't you copy the directory to /lib/modules/$(uname -r)/rtl8185/, and then add the names of all those modules to /etc/modules (without the .ko)? That would remove the need to run this clumsy script on every boot.

that sounds like a good idea (it has already failed to run a couple of times), but i have no idea how to do what you said


so i would do this?
```
sudo cp ~/rtl8185 /lib/modules/ashley/rtl8185
```

then i would have to open the ./wlan0up script to see what modules i need

then i write the names of all of theese without the .ko in /etc/modules? 

is that all correct?

---

### Post by jw5801 on 2008-07-07
You've pretty much got it! Except 'uname -r' returns the name of your kernel, rather than your username. You can use it thusly (just copy and paste):
```
sudo cp ~/rtl8185 /lib/modules/$(uname -r)/rtl8185
sudo depmod
```

You need to run the depmod command, as that creates a list of the modules modprobe has available for loading. Then you're correct about adding the modules minus the .ko to /etc/modules.

---

### Post by onewithnature83 on 2008-07-20
from start to finish.

Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

