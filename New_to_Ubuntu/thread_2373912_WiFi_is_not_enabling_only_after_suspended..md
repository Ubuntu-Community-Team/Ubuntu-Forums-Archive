---
title: "WiFi is not enabling only after suspended."
date: 2017-10-10
forum: New to Ubuntu
---

### Post by mohank1432 on 2017-10-10
I've dualbooted Ubuntu budgie. And WiFi is not enabling after it is waken from suspended. Rfkill is hard. I am using Realtek. And I've tried all the solutions in the form which has same thread, but its still not working. WiFi is enabling after reboot only. And my network driver is rtl8723be. Help me

---

### Post by Geoffrey_Arndt on 2017-10-11
Read the linked page to get the current commands to restart the network service (start with first listed command).

Also, if you just click on Network Manager applet and try to click on another network, that should have the same effect as restarting the network and then you can click on your specific network ssid.

[https://linuxconfig.org/how-to-restart-network-on-ubuntu-16-04-xenial-xerus-linux](https://linuxconfig.org/how-to-restart-network-on-ubuntu-16-04-xenial-xerus-linux)

---

### Post by ajgreeny on 2017-10-11
Save the text below in the code box and save it as **NetworkManagerRestartWorkaroundForBug1380480.sh** and make it executable then move it to **/lib/systemd/system-sleep/**

There is information about the script in the text itself, which should make it self explanatory.

That should restart the network after returning from suspend.
```
#!/bin/bash
# Created by Hans Deragon (hans@deragon.biz), 2015-05-14 07:31:11 EDT

# INSTALLATION
#
#   - Move this script under: /lib/systemd/system-sleep
#   - chmod +x /lib/systemd/system-sleep/NetworkManagerRestartWorkaroundForBug1380480.sh

# DESCRIPTION
#
#   Restarting the NetworkManager as a workaround for the following bug:
# 
#   &#8729; https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1380480


# 3 seconds delay is necessary apparently.  May be shorter; needs to be
# tested.  But if no delay is implemented, nm-applet crashes.  Seams that we
# need to leave the system resume completely before attempting a restart of
# NetworkManager.
(sleep 3; systemctl restart NetworkManager.service) &
disown

```

---

