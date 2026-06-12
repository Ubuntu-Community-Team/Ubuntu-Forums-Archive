---
title: "Ubuntu 11.10 crashed - help me determine what this log means"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by jrs2 on 2014-01-29
Running a headless version of 11.10. The unit crashed at some point, and I could no longer see it on my network. Since it's headless, I had no way of remoting into it to troubleshoot. I had someone onsite attempt to reset the machine, with no avail. A week goes by, and all of a sudden a reset brings it back online, and I'm able to remote in and look at log files. 

In the dmesg log, I see the following status at the bottom:

[    9.465024] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.908733] init: failsafe main process (897) killed by TERM signal
[   14.948839] type=1400 audit(1391005042.331:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1036 comm="apparmor_parser"
[   14.949197] type=1400 audit(1391005042.331:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1037 comm="apparmor_parser"
[   14.949967] type=1400 audit(1391005042.331:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1037 comm="apparmor_parser"
[   14.950448] type=1400 audit(1391005042.331:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1037 comm="apparmor_parser"
[   14.957901] type=1400 audit(1391005042.339:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1040 comm="apparmor_parser"
[   14.958682] type=1400 audit(1391005042.339:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1040 comm="apparmor_parser"
[   14.960319] type=1400 audit(1391005042.343:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1038 comm="apparmor_parser"
[   14.964531] type=1400 audit(1391005042.347:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1041 comm="apparmor_parser"
[   14.965470] type=1400 audit(1391005042.347:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1041 comm="apparmor_parser"
[   14.969646] type=1400 audit(1391005042.351:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1042 comm="apparmor_parser"
[   15.100258] init: apport pre-start process (1076) terminated with status 1
[   15.157578] init: apport post-stop process (1115) terminated with status 1

Any ideas as to what could have caused this? Are there any other logs I should check for further details?

---

