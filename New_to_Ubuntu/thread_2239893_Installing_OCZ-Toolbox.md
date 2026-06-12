---
title: "Installing OCZ-Toolbox"
date: 2014-08-16
forum: New to Ubuntu
---

### Post by t0b12 on 2014-08-16
Dear All,

I am trying to install the OCZ- Toolbox in order to update the firmware of a Vertex SSD. After downloading the OCZToolbox_v4.5.2.298_linux package and doubleklicking on the  OCZToolbox-symbol (which is an application/x-executable type), the program opens with the remark: "This program must be run as a administrator".

Using the Terminal and typing ```
sudo ./OCZToolbox
``` doesnot work and will create the answer: ```
command not found
```

As far as I understand, I am already logged-in as administrator:

```
groups <myname>
<myname> adm cdrom sudo dip plugdev lpadmin sambashare
```

Any advice for me? 

Thanks a lot in advance.

---

### Post by Rob Sayer on 2014-08-16
I haven't used this package but looking at:

[http://ocz.com/consumer/download/firmware](http://ocz.com/consumer/download/firmware)

I see that the linux package is for ubuntu up to 13.10.  this could be a problem.

And it downloads a tar.gz package, which is quite normal, but it's not a linux executable file.  You're still thinking Windoze.  Here's a guide:

[http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file)

You aren't an 'administrator' like you are in Windoze.  Unlike there the permission levels in Linux actually work properly.  You can't install *anything* without your user password.  This is a feature, not a bug.  It's a big part of the reason there aren't any known Linux viruses.

---

### Post by whitesmith on 2014-08-16
Please open a GUI terminal and rerun the command```
sudo ./OCZToolbox
```but this time copy the screenful of data and post it for us. I want to examine the whole process on its deathbed. Usually *nix apps don't say anything about Administrator, since there is no such thing in the Unix world. Unix (and derivatives like Linux) control access using ownership and permissions, not some feared entity with magical properties that calls itself Administrator. That's a Windows thingie, as Rob Sayer said. Regards.

---

