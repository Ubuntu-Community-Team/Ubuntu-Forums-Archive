---
title: "Rsync error (NTFS)"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-10
I am using the following code to rsync to a NTFS formatted drive.
```
#!/bin/bash

sudo rsync -azvu --modify-window=1 --progress --log-file=/home/abhiroop/Computers/Bash/Logs/BackupBig_$(date +%d-%m-%Y_%T).txt  --delete --delete-excluded --exclude-from=/home/abhiroop/Computers/Bash/BackupBigExclude.txt / /media/Applications/BackUp

```

NB: Mostly till now it has been working without any problems. TODAY I get this error.
NB2: This works fine to an ext3 formatted drive without any errors.

I get this error and nothing else backs up

```


rsync: rename "/media/Applications/BackUp/usr/lib/evolution/2.12/plugins/.liborg-gnome-evolution-attachment-reminder.so.ipkKrr" -> "usr/lib/evolution/2.12/plugins/liborg-gnome-evolution-attachment-reminder.so": Operation not supported (95)
rsync: rename "/media/Applications/BackUp/usr/lib/evolution/2.12/plugins/.liborg-gnome-mailing-list-actions.so.YhbafU" -> "usr/lib/evolution/2.12/plugins/liborg-gnome-mailing-list-actions.so": Operation not supported (95)
rsync: rename "/media/Applications/BackUp/usr/lib/evolution/2.12/plugins/.org-gnome-backup-restore.eplug.oSlg3m" -> "usr/lib/evolution/2.12/plugins/org-gnome-backup-restore.eplug": Operation not supported (95)
rsync: rename "/media/Applications/BackUp/usr/lib/evolution/2.12/plugins/.org-gnome-evolution-mail-attachments-import-ics.eplug.QDbNRP" -> "usr/lib/evolution/2.12/plugins/org-gnome-evolution-mail-attachments-import-ics.eplug": Operation not supported (95)
rsync: rename "/media/Applications/BackUp/usr/lib/evolution/2.12/plugins/.org-gnome-mail-account-disable.eplug.mfgWGi" -> "usr/lib/evolution/2.12/plugins/org-gnome-mail-account-disable.eplug": Operation not supported (95)

sent 18330248 bytes  received 1052226 bytes  120763.08 bytes/sec
total size is 47735482580  speedup is 2462.82
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

```

---

