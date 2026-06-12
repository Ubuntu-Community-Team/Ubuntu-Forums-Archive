---
title: "iscsi service fails to start"
date: 2018-01-24
forum: New to Ubuntu
---

### Post by alampnah on 2018-01-24
My iscsi service was working until I ran the NTFS configuration tool. After that the service would fail to start after reboot. Following is the error:

xxxxxx:~$ systemctl status open-iscsi.service
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

I purged the service and reinstalled it and I still get this error. Any suggestions or solutions will be appreciated.

Thanks.

---

### Post by QIII on 2018-01-24
You already have this [here]("https://ubuntuforums.org/showthread.php?t=2383328").

Closed.

---

