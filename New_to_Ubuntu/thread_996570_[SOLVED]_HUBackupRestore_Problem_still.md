---
title: "[SOLVED] HUBackup/Restore Problem still?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by cliffm on 2008-11-29
Re: HUBackup/Restore Problem
Help! All my files are here. Just upgraded to Ubuntu 8.10
I have followed several answer to this problem and can not get any of them to work.
What am I doing wrong? The HUBackup file is 518.7MB, and was saved to a CD. These are some of my attempts to restore and there responses.


~$ dar -l /media/sdb1/backup/cliffm-master-archive
/media/sdb1/backup/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]

:~$ sudo dar -x /cdrom0/backup/cliffm-master-archive -R /home/cliffm -wa -v
[sudo] password for cliffm:
/cdrom0/backup/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]

m:~$ dar -x.hubackup-data/cliffm-master-archive -R TARGET_DIR
File ownership will not be restored as dar is not run as root. to avoid this message use -O option [return = OK | Esc = cancel]
Escaping...
Aborting program. User refused to continue while asking: File ownership will not be restored as dar is not run as root. to avoid this message use -O option
cliffm@cliffm:~$ sudo dar -x.hubackup-data/cliffm-master-archive -R TARGET_DIR
[sudo] password for cliffm:
.hubackup-data/cliffm-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]
Escaping...
Aborting program. User refused to continue while asking: .hubackup-data/cliffm-master-archive.1.dar is required for further operation, please provide the file.

---

### Post by HHelsinger on 2009-01-18
Cliff,
did you ever get an effective solution?   Like you, all my files are there, and I'd like to restore them.

Do you know how I can test a restore command before implementing it?   can I redirect the output of DAR to a file?

It would be nice if HuBackup/Restore worked in Hardy or Ibis, wouldn't it.  

Is anyone working on that?

---

