---
title: "HOWTO get remote access from VMware-server in Ubuntu repository"
date: 2007-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by handband2 on 2007-05-30
This is for those who want to remotely connect to VMware-server which was installed through the Ubuntu repository.  If you haven't or don't know about VMware-server go here:  [[COLOR="Red"]**Install VMware-server**[/COLOR]]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")  

If you have more than one network card I recommend using the following command to configure the settings:
```
$ sudo /usr/bin/vmware-config-network.pl
```

Now lets get VMware-server working so we can remotely connect to it:

**Download** the [[COLOR="Red"]**pam_unix_vm.so.tar.gz**[/COLOR]]("http://ubuntuforums.org/attachment.php?attachmentid=33866&stc=1&d=1180566886")
```

$ tar zxvf pam_unix_mv.so.tar.gz
$ sudo mv pam_unix_vm.so /lib/security/
```

Now lets change vmware-authd file:
```
$ sudo gedit /etc/pam.d/vmware-authd
```
Change the file to this:
```
#%PAM-1.0
auth sufficient pam_unix_vm.so shadow nullok
auth required pam_unix_auth.so shadow nullok
account sufficient pam_unix_vm.so
account required pam_unix_acct.so
```

Reboot the system and you should now be able to connect remotely to your VMware-server

Sources:
[http://www.vmware.com/community/thread.jspa?messageID=636956]("http://www.vmware.com/community/thread.jspa?messageID=636956")
[http://ubuntuforums.org/showthread.php?t=426026&highlight=vmware+deb+package]("http://ubuntuforums.org/showthread.php?t=426026&highlight=vmware+deb+package")
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")

---

### Post by linuxhelp on 2008-11-14
Hello

System Ubuntu 8.10 AMD64/4GB/Raid1 /VMWARE 1.08
 
does it work to setup vmware Server at 8.10 ubuntu 64bit
with Network-bonding??

My Server uses eth0+eth1 as bond0 at vmware i setup to connect to
bond0.

Have tried it but got problems..


My VMs can no connect to bridge mode net?

---

