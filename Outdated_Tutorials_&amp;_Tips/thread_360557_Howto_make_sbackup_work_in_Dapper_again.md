---
title: "Howto make sbackup work in Dapper again"
date: 2007-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by pjbgravely on 2007-02-13
At the end of last year I started noticing that sbackup was not working all of the time. I started looking for  a fix but kept finding other people's unanswered questions about the same problem. I looked through the bug reports and found this comment from the developer.

>  Re: Empty past backup directory causes simple-backup to fail silently from Aigars Mahinovs at 2007-01-08 02:27:06 UTC

You are not the only one using it or seeing this bug (and few others). It is just that small changes introduced several bugs that only appear down the line of use right before the development efforts basically stopped because of Real Life interference (finishing up a Masters degree in a couple months).

    I found that sbackup was updated from 0.8-1 to 0.9-1 in November of 2006. I tried to revert but found that the old package was no longer in the repositories. The sbackup version 0.10-1 in Edgy works so I decided see if I could backport it to Dapper. Here is how I did it.

First you need to do some clean up.
Open a terminal and:

```

sudo cp /etc/sbackup.conf  /etc/sbackup.conf.bak
sudo rm /etc/cron.d/sbackup
sudo rm /var/lock/sbackup.lock
sudo rm /root/sbackup.lock

```

Don't worry if any of the remove commands ( rm) gives an error.

    I found that sbackup chokes if you have any old backup files in your backup directory, so you will need to either move the old backups or point sbackup to a new backup directory. If you go the new directory route you have to make the directory first.

sudo nautilus /var/backup

 Above will take you to the default backup location. Remember that you are in root so you can do damage to the system.


Now you need to get the new package from Edgy.

[  sbackup 0.10-1 ](http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fs%2Fsbackup%2Fsbackup_0.10.3_all.deb&md5sum=e1f7cf6770578231c3797f2eae3b0e49&arch=all&type=main)

    Download it to your desktop, click on it ( or double click) , the package installer will come up, click install and ignore the warning about not being in the repositories.

    Now start sbackup, and check that everything is set right, and make sure that you change you back up to directory if that is the way you went. You will notice new options about purging old backups. I have not tried it but it should work.

Paul

---

