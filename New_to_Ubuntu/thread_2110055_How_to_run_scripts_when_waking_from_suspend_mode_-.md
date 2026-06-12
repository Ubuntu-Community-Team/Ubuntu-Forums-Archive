---
title: "How to run scripts when waking from suspend mode - UFW &amp; VPN"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by abexman on 2013-01-29
So I am guessing I can add scripts at /etc/pm/sleep.d for Ubuntu 12.04 LTS to do things when a laptop wakes from suspend mode. 

A few questions:
a. Do I add new scripts to an existing file here or create new ones in the same folder? Do new filenames matter?
b. My VPN & UFW seem to be disabled after suspend mode. I am guessing I can add a script to start up UFW, would it be as simple as a script saying "start ufw" or "start gufw"? c. What would be the command to restart a particular VPN connection?

Here's the current contents of my sleep.d folder:
00_check_touchpad_status  10_unattended-upgrades-hibernate
10_grub-common            novatel_3g_suspend

Thanks!

---

### Post by abexman on 2013-02-09
Anyone?

---

