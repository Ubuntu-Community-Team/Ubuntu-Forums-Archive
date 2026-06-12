---
title: "Boot time slow due to open_iscsi service"
date: 2018-01-23
forum: New to Ubuntu
---

### Post by alampnah on 2018-01-23
I have run the system-analyze blame command (v 16.0.4.3) and identified the culprit for slow boot times (see below):

2min 981ms open-iscsi.service
          8.835s NetworkManager-wait-online.service
          1.219s vmware.service
           941ms dev-sdb4.device
           867ms snapd.service
           451ms nmbd.service
           411ms samba-ad-dc.service
           401ms vmware-workstation-server.service
           218ms vmware-USBArbitrator.service
           176ms ModemManager.service
           170ms apparmor.service

As per some suggestions on the internet I have modified the iscsid.conf file as follow:
node.startup = automatic
node.leading_login = Yes
node.session.timeo.replacement_timeout = 30 (used to be 120)

All other parameters were set to default (as in the original conf file)

I am connecting to a Synology NAS

Appreciate any suggestions or help. Thanks.

---

### Post by tchambers on 2018-01-24
Obviously the bottleneck here is that the open-iscsi.service is waiting to connect to the NAS. 

Was the NAS on during and connected during the boot?

You could disable the iscsi.service from starting at boot with

```
systemctl disable iscsi.service
systemctl disable iscsid.service
```

That will probably make things a bit better, but it's obviously non-optimal.

---

### Post by alampnah on 2018-01-24
I have new problem now my service does not even start. I get teh following error:
xxxxxxxxx:~$ systemctl status open-iscsi.service
&#9679; open-iscsi.service - Login to default iSCSI targets
   Loaded: loaded (/lib/systemd/system/open-iscsi.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2018-01-24 00:55:26 EST; 9s ago
     Docs: man:iscsiadm(8)
           man:iscsid(8)
  Process: 15488 ExecStartPre=/bin/systemctl --quiet is-active iscsid.service (code=exited, status=3)


Jan 24 00:55:26 xxxxxxxxx systemd[1]: Starting Login to default iSCSI targets...
Jan 24 00:55:26 xxxxxxxxx systemd[1]: open-iscsi.service: Control process exited, code=exited status=3
Jan 24 00:55:26 xxxxxxxxx systemd[1]: Failed to start Login to default iSCSI targets.
Jan 24 00:55:26 xxxxxxxxx systemd[1]: open-iscsi.service: Unit entered failed state.
Jan 24 00:55:26 xxxxxxxxx systemd[1]: open-iscsi.service: Failed with result 'exit-code'.

---

### Post by alampnah on 2018-01-24
Here is a new thread for this issue [https://ubuntuforums.org/showthread.php?t=2383360](https://ubuntuforums.org/showthread.php?t=2383360)

---

