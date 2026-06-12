---
title: "VSFTPD Fix Ubuntu 14.04 x64 -  libgcc_s.so.1 must be installed for pthread_cancel 500"
date: 2014-04-22
forum: Packaging and Compiling Programs
---

### Post by own3mall on 2014-04-22
Hey guys, this has been a problem for a long time in Ubuntu.  Each time a new version of Ubuntu is released, the VSFTPD package needs to be patched or configured in a strange manner in order to support MySQL integration for virtual users.  

On Ubuntu 14.04 (x64 only) which just came out, I was getting this error when attempting to connect as a valid user:

[I][COLOR=#ff0000]libgcc_s.so.1 must be installed for pthread_cancel
500 OOPS: priv_sock_get_result[/COLOR][/I]

The connection would fail and no files could be uploaded.  I am a developer for open source software, and I've posted a list containing the _[fixes for previous versions of Ubuntu]("http://ehcpforce.tk/faq/index.php?sid=2579&lang=en&action=artikel&cat=1&id=3&artlang=en")_.  However, 14.04 x64 (64-bit Only) required the fix in the link below last reply to be applied:

_[http://askubuntu.com/questions/126625/libgcc-s-so-1-must-be-installed-for-pthread-cancel-to-work](http://askubuntu.com/questions/126625/libgcc-s-so-1-must-be-installed-for-pthread-cancel-to-work)_

I have packaged the fixed version up into a deb package.  I tested it, and it's working great on Ubuntu 14.04.  I hope this helps others.  The full script to run is located here: 

```

sudo apt-get remove vsftpd
sudo dpkg --remove vsftpd
sudo sed -i 's/chroot_local_user=NO/chroot_local_user=YES/g' /etc/vsftpd.conf
sudo sed -i 's/allow_writeable_chroot=NO/allow_writeable_chroot=YES/g' /etc/vsftpd.conf
sudo sed -i 's/seccomp_sandbox=YES/seccomp_sandbox=NO/g' /etc/vsftpd.conf
wget -N -O "vsftpd_3.0.2-1ubuntu2.deb" http://dinofly.com/files/linux/vsftpd_3.0.2-1ubuntu2_amd64.deb
sudo dpkg -i vsftpd_3.0.2-1ubuntu2.deb
sudo service vsftpd restart



```

Again, this is only for Ubuntu 14.04 x64, previous Ubuntu fixes for VSFTPD based on Ubuntu version are linked above.  VSFTPD with minor fixes in 32-bit worked just fine out of the box.  The fix for 32-bit is this:

```

sudo sed -i 's/chroot_local_user=NO/chroot_local_user=YES/g' /etc/vsftpd.conf
sudo sed -i 's/allow_writeable_chroot=NO/allow_writeable_chroot=YES/g' /etc/vsftpd.conf
sudo service vsftpd restart



```

---

### Post by ricardo16 on 2014-04-27
I only registered to tell you.. God bless you. Seriously, I spent like 2 hours on this, and who knows how many more I would have wasted.
Thanks!

---

### Post by vturbanov on 2014-10-22
Wow, this seems like a criminal bug. This pretty much means the vsftpd service is broken, at least for virtual user authentication in my case. Thank you very much for a solution. I'm not sure I had the same specific problem as you, btw. My error log stated this:
```
 toad kernel: [6565855.048206] vsftpd[13568]: segfault at 24f0 ip 00000000000024f0 sp 00007fffa1f6dd28 error 14 in librt-2.19.so[7f04289d4000+7000]
```

BTW, have you tried to send this issue to the Ubuntu's devs?

---

### Post by vturbanov on 2014-12-05
This ALSO seems to fix the following issue (taken from from [FONT=courier new]/var/log/auth.log[/FONT]):

```
vsftpd: PAM unable to dlopen(pam_smbpass.so): /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory
vsftpd: PAM adding faulty module: pam_smbpass.so
```

---

### Post by charly_saenz on 2015-02-15
Also registered to thank you!! Here a total linux noob trying to run some Ubuntu services for home. BTW must be first time I copied and paste such a complex set of commands and they work right away. THANKS !!

---

### Post by commifreak2 on 2015-03-23
But what is the root cause? Why is it not fixed?

Last week I got new update (2015-03-20 10:42:07 status installed vsftpd:amd64 3.0.2-1ubuntu2.14.04.1) and the error returned - I have to patch it again.

Any chance that the developer of vsftpd fixes that and push it to the official 14.04 repo?

---

### Post by gollum53 on 2015-06-16
This bug is connected with the Samba bug and PAM found here: [http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory](http://askubuntu.com/questions/477002/loadparm-c4864-leaking-memory). Can be resolved by running pam-auth-update and deselecting SMB password synchronization. Then you do not need to install anything. 
Best regards
Roman

---

### Post by commifreak2 on 2015-07-06
> **gollum53 said:**
> This bug is connected with the Samba bug and PAM
Ehm - sorry, this seems not work in my case - I dont have such an entry..?

[ATTACH=CONFIG]263046[/ATTACH]

EDIT: Oh, okay - you are talking about #4. So, I still wonder, that this is still not updated in the Ubuntu-package. I still have to install the patched version after each update.

Is it possible to block future updates if vsftpd (which is not the best solution at all...)?

---

### Post by Daniel_Bastos on 2016-05-13
Hi these steps worked in my server.

Thanks.

> **own3mall said:**
> Hey guys, this has been a problem for a long time in Ubuntu.  Each time a new version of Ubuntu is released, the VSFTPD package needs to be patched or configured in a strange manner in order to support MySQL integration for virtual users.  

On Ubuntu 14.04 (x64 only) which just came out, I was getting this error when attempting to connect as a valid user:

[I][COLOR=#ff0000]libgcc_s.so.1 must be installed for pthread_cancel
500 OOPS: priv_sock_get_result[/COLOR][/I]

The connection would fail and no files could be uploaded.  I am a developer for open source software, and I've posted a list containing the _[fixes for previous versions of Ubuntu]("http://ehcpforce.tk/faq/index.php?sid=2579&lang=en&action=artikel&cat=1&id=3&artlang=en")_.  However, 14.04 x64 (64-bit Only) required the fix in the link below last reply to be applied:

_[http://askubuntu.com/questions/126625/libgcc-s-so-1-must-be-installed-for-pthread-cancel-to-work](http://askubuntu.com/questions/126625/libgcc-s-so-1-must-be-installed-for-pthread-cancel-to-work)_

I have packaged the fixed version up into a deb package.  I tested it, and it's working great on Ubuntu 14.04.  I hope this helps others.  The full script to run is located here: 

```

sudo apt-get remove vsftpd
sudo dpkg --remove vsftpd
sudo sed -i 's/chroot_local_user=NO/chroot_local_user=YES/g' /etc/vsftpd.conf
sudo sed -i 's/allow_writeable_chroot=NO/allow_writeable_chroot=YES/g' /etc/vsftpd.conf
sudo sed -i 's/seccomp_sandbox=YES/seccomp_sandbox=NO/g' /etc/vsftpd.conf
wget -N -O "vsftpd_3.0.2-1ubuntu2.deb" http://dinofly.com/files/linux/vsftpd_3.0.2-1ubuntu2_amd64.deb
sudo dpkg -i vsftpd_3.0.2-1ubuntu2.deb
sudo service vsftpd restart



```

Again, this is only for Ubuntu 14.04 x64, previous Ubuntu fixes for VSFTPD based on Ubuntu version are linked above.  VSFTPD with minor fixes in 32-bit worked just fine out of the box.  The fix for 32-bit is this:

```

sudo sed -i 's/chroot_local_user=NO/chroot_local_user=YES/g' /etc/vsftpd.conf
sudo sed -i 's/allow_writeable_chroot=NO/allow_writeable_chroot=YES/g' /etc/vsftpd.conf
sudo service vsftpd restart



```

---

