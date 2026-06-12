---
title: "BackupPC error “No files dumped for share”"
date: 2018-02-02
forum: New to Ubuntu
---

### Post by lattimro on 2018-02-02
[COLOR=#111111][FONT=Ubuntu]I had BackupPC working for fine years but I wanted to move it to another server. The backuppc copies all the files but backup = 0 Type = partial Filled = yes (which is OK)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Backup# Type Filled
0-----------partial yes[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can't resolve the following issue:[/FONT][/COLOR]
tarExtract: Done: 0 errors, 15 filesExist, 2342001 sizeExist, 1120139 sizeExistComp, 155 filesTotal, 8019734 sizeTotal
Got fatal error during xfer (No files dumped for share foo)
Backup aborted (No files dumped for share foo)
Not saving this as a partial backup since it has fewer files than the prior one (got 155 and 0 files versus 500)
[COLOR=#111111][FONT=Ubuntu]Contents of file /var/lib/backuppc/pc/*******/XferLOG.bad.z, modified 2018-01-28 18:50:42[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Running: /usr/bin/smbclient \\*******\Scan -I 192.168.0.106 -U backuppc -E -d 1 -c tarmode\ full -Tc - full backup started for share Scan
Xfer PIDs are now 1972,1971
Domain=[********] OS=[Windows 10 Home 16299] Server=[Windows 10 Home 6.3]
tar:316 tarmode is now full, system, hidden, noreset, quiet
tar:712 Total bytes received: 29524103[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]For those who asked for more info:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Backup failed on ... (No files dumped for share ...)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]this is the fatal error I got every single time when backuppc runs[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Note: rsync works OK on Linux clients, only smb fails on Windows clients.[/FONT][/COLOR]

[LIST]
[*]Ubuntu 16.04.3 LTS (Xenial)
[*]BackupPC - Version 3.3.1
[*]Samba - Version 4.3.11-Ubuntu
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Any help would be much appreciated, thank you.[/FONT][/COLOR]

---

