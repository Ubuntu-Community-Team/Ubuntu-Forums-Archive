---
title: "Fresh 13.04 Install Remmina not working"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by z3llin on 2013-09-06
I need to remote into Windows machines on a daily basis. From what I've gathered from numerous sources is that Remmina is best suited to my needs and comes pre-installed on 13.04 to boot. So I start the app and nothing happens. Even going into terminal and running sudo remmina doesn't do much other than registering the plugins. The GUI never actually launches. I've tried uninstalling and reinstalling freerdp and remmina and the associated plugins, no luck. What exactly should I do to get this up and running?
I'm running a fresh install of 13.04 updated to today.

Yet another newbie to linux.

---

### Post by tripp98 on 2013-09-06
Open a terminal.  Type remmina.  Update thread with output and result.

---

### Post by gps1539 on 2013-09-06
Remmina also broke for me in 13.04, not sure if there is a fix. I now use rdesktop from the command line for rdp sessions. There is also a gui, grdesktop that can open/save .rdp files

---

### Post by r_avital on 2013-09-07
Simple fix (it is known to be a bug in 13.04)

If your connection type is RDP, edit it, and look under the Advanced tab - Security defaults to "Negotiate" " or some auto-magic option.  Make sure it's anything but -- I suppose in the case of an RDP-type connection you should simply select RDP in that box.

Save and connect.  This is working for me (it did initially break with a segmentation fault when security was at the default setting).

If that still fails, as tripp98 said above, please type remmina in a terminal, copy the output, and post it in a reply here.

Let us know :)

---

### Post by z3llin on 2013-09-11
Sorry for the delay I was away for a while. Here is the terminal's output:
```
Remmina plugin VNC (type=Protocol) registered.
Remmina plugin VNCI (type=Protocol) registered.
Remmina plugin RDP (type=Protocol) registered.
Remmina plugin RDPF (type=File) registered.
Remmina plugin RDPS (type=Preference) registered.
Segmentation fault (core dumped)
```

I found this:
[http://ubuntuforums.org/showthread.php?t=1664620](http://ubuntuforums.org/showthread.php?t=1664620)

Turns out Remmina thinks South African keyboard layouts are so bad its worth breaking over!
Fixed, Thanks for being willing to helping out peoples!

---

### Post by auburn on 2013-11-04
> **r_avital said:**
> Simple fix (it is known to be a bug in 13.04)

If your connection type is RDP, edit it, and look under the Advanced tab - Security defaults to "Negotiate" " or some auto-magic option.  Make sure it's anything but -- I suppose in the case of an RDP-type connection you should simply select RDP in that box.

Save and connect.  This is working for me (it did initially break with a segmentation fault when security was at the default setting).

If that still fails, as tripp98 said above, please type remmina in a terminal, copy the output, and post it in a reply here.

Let us know :)

Thank you!

---

