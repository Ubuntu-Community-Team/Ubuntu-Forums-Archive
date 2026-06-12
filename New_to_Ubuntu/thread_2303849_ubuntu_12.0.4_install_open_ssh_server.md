---
title: "ubuntu 12.0.4 install open ssh server"
date: 2015-11-22
forum: New to Ubuntu
---

### Post by arunsadhasivam on 2015-11-22
[COLOR=#333333][FONT=Ubuntu]i am new to ubuntu . i am using 12.0.4 . please let me know how to install open ssh server in ubuntu 12.04.
as i could not get any of apt-get commands working in my case
>sudo apt-get install openssh-server openssh-client
 is not working.
i try manually downloading the ssh client.
now ssh-keygen -t rsa -P “” command is working
but when i try to connect using
>ssh localhost showing eror cannot connect to localhost :22
please help to install ssh manually with out using apt-get
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]

my full version details:
===============


openssh-server:
  Installed: (none)
  Candidate: (none)
  Version table:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise
Linux ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


i tried dowloading the openssh and try installing manual boot scripts, i installed the boot scripts, but not worked.
install-sshd: create-dirs
 install -m ${MODE} blfs/init.d/sshd ${EXTDIR}/rc.d/init.d/
 ln -sf ../init.d/sshd ${EXTDIR}/rc.d/rc0.d/K30sshd
 ln -sf ../init.d/sshd ${EXTDIR}/rc.d/rc1.d/K30sshd
 ln -sf ../init.d/sshd ${EXTDIR}/rc.d/rc2.d/K30sshd
 ln -sf ../init.d/sshd ${EXTDIR}/rc.d/rc3.d/S30sshd
 ln -sf ../init.d/sshd ${EXTDIR}/rc.d/rc4.d/S30sshd
 ln -sf ../init.d/sshd ${EXTDIR}/rc.d/rc5.d/S30sshd
 ln -sf ../init.d/sshd ${EXTDIR}/rc.d/rc6.d/K30sshd


[/FONT][/COLOR]

---

### Post by howefield on 2015-11-22
Is this a new installation of 12.04 ?

If so, did you do...

```
sudo apt-get update
```

before trying to install openssh-server and what was the exact error you got when you tried ?

---

### Post by arunsadhasivam on 2015-11-23
it is saying error "package openss-server" not exist

---

### Post by LukeMorrison on 2015-11-23
Hello,

The correct command is ```
sudo apt-get install openssh-server
```

It is best practice to cut and paste these commands in order to avoid typos.

LukeMorrison

---

### Post by deadflowr on 2015-11-23
Your system is months out-of-date
Run an update.
You can try it through the update manager, 
or run
```
sudo apt-get update && sudo apt-get dist-upgrade
```
post any errors, if any.
(Note: do not worry that the dist-upgrade command will upgrade you to a different version of Ubuntu, it won't)

I say the system is out-of-date because the kernel in use for you is 3.13.0-32, while the latest kernel for you would be
3.13.0-68(or there abouts)

Also, if you desire both the openssh-server and the openssh-client, then simply install ssh
```
sudo apt-get install ssh
```
will bring in both packages together.
fer what it's worth

---

