---
title: "Howto use duplicity with rsync over ssh"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by lance bermudez on 2014-03-28
Does any one know of a howto guide that will let me use duplicity withrsync over ssh to a remote computer?

---

### Post by papibe on 2014-03-28
Hi lance bermudez.

Take a look at this: [Using Duplicity for Full Server Backup on Ubuntu 12.04]("http://scie.nti.st/2013/4/13/using-duplicity-for-full-server-backup-on-ubuntu-12-dot-04/"). It has a section called 'Perform backup using rsync method.'

Regards.

---

### Post by lance bermudez on 2014-04-02
Thank you that helped alot I just want to make sure I got this.

#take backup encrypt verbose
duplicity --verbosity 9 --encrypt-key 2202FE51 /home/lance/bin/ rsync://lance@192.168.2.19//home/lance/bin/

#list backup files
duplicity --encrypt-key 2202FE51 list-current-files rsync://lance@192.168.2.19//home/lance/bin/

#recover backup files
duplicity --encrypt-key 2202FE51 --file-to-restore sshrsyncdel rsync://lance@192.168.2.19//home/lance/bin /tmp/sshrsyncdel

#clean up bakup files older then 1 month
duplicity --verbosity 5 --encrypt-key 2202FE51 remove-older-than 1M --force rsync://lance@192.168.2.19//home/lance/bin

Any think not look right? I have tested them and they seem to work but not sure about if the clean up will work like I want. What I want it to do is delete any old files that are older than 1 month to save disk space. Also how do I change the port for ssh?

---

### Post by lance bermudez on 2014-04-02
Change ssh port
duplicity --verbosity 5 --encrypt-key 2202FE51 /home/lance/bin/ rsync://lance@192.168.2.2:9455//home/lance/0/bin/

---

### Post by lance bermudez on 2014-04-02
Also found out how to do more than one path

duplicity incr --verbosity 4 --encrypt-key 2202FE51 --include /home/lance/bin/ --include /home/lance/.config/chromium/ --exclude '**' /home/lance --log-file /home/lance/log rsync://lance@192.168.2.2:9455//home/lance/0

---

