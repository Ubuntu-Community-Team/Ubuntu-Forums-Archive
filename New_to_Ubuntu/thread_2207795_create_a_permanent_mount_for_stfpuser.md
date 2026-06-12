---
title: "create a permanent mount for stfpuser"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by dean.wheatley on 2014-02-25
Hi, 

I have a 12.04 LTS running as a webserver and need to be able to access a folder within the file structure via sftp for users to download various files.  Currently I use "sudo mount --bind /mnt/data/www/domain.name/web/portalfiles /home/sftpusername/web" to create this link so that I am not giving the sftpuser direct access to the whole web site, just the area they need.
 
However this does not propagate through a reboot so I need to re-enter the above command every time the system is rebooted.  I know there must be a way to have this set so that even after reboot the mount is still present, I just don't know how.  Is there a safe/standard method of achieving this?
 
Drac

---

### Post by ian-weisser on 2014-02-27
/etc/fstab is the normal location for systemwide automatic mounts.

---

