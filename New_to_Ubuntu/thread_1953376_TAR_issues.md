---
title: "TAR issues"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by mcreef on 2012-04-06
I posted this question about TAR backups in another sub-forum, but perhaps it really belongs here...

I have (I believe) got the backing up part figured out. I have created a  system baseline backup, and am using cron to create separate  incremental backups of working files hourly, and daily, and a weekly  root level incremental backup. 

Here is how I have cron set up...

0 * * * * sudo tar -cvpzf /media/OMT/BACKUPS_START_4-2-12  incremental_hourly_backup.tar.gz --newer '30 minutes ago' (exclusions  here) /srv/samba
0 22 * * * sudo tar -cvpzf  /media/OMT/BACKUPS_START_4-2-12/incremental_daily_backup.tar.gz --newer  '23 hours ago' (exclusions here) /srv/samba
0 0 * * 1 sudo tar -cvpzf  /media/OMT/BACKUPS_START_4-2-12/incremental_weekly_backup.tar.gz --newer  '1 week ago' (exclusions here) /

Does this look kosher?

The problem I am having is figuring out the restore end of things. I  have made an easily verifiable change to a particular file, and am  attempting to restore that ***single*** directory and all of  it's contents from the backup in it's pre-change state. Ideally, I would  restore this file to a newly created temporary folder where it could be  opened and verified before manually being transferred to it's new home.  I have been unable to get this to work. I also tried restoring it to  it's original location thinking this may have been the issue, but this  has also been unsuccessful. I think it is just time to ask those who  know rather than continuing to keep trying to tweak my commands and risk  possibly really mucking something up.

Here is my latest attempt at restoring the directory "EXPRESS_REV_4" and all of it's contents to the directory "restore_test"...

sudo tar xvf  /media/OMT/BACKUPS_START_4-2-12/baseline_backup_4_2_12.tar.gz -C  /srv/samba/manufacturing_server/pre-2012_files/design_on_g/Dave_Robertson/restore_test   srv/samba/manufacturing_server/pre-2012_files/design_on_g/Dave_Robertson/MISC/BERTRAM/EXPRESS_REV_4/

Where am I going wrong?

Thank you in advance for any help.

---

