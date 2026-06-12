---
title: "How to find out what options OpenSSH was compiled with?"
date: 2009-03-08
forum: Programming Talk
---

### Post by scooter77 on 2009-03-08
Is there a way to find out from the ssh or sshd binary what options OpenSSH was configured with to produce the binary, eg. --with-pam, --with-tcp-wrappers and so on? I've found nothing on this in the man pages or in -V output.

On a related note, is there a standard set of options that the Ubuntu or Debian binary packages get compiled with? I don't think it's with no options, since they seem to support PAM, for example, which is not enabled by default.

---

### Post by scooter77 on 2009-03-15
Anyone?

---

### Post by supirman on 2009-03-15
I don't know of a great way, but you can track it down via launchpad.

```
configure --build=i486-linux-gnu --prefix=/usr --sysconfdir=/etc/ssh --libexecdir=/usr/lib/openssh --mandir=/usr/share/man --disable-strip --with-mantype=doc --with-4in6 --with-privsep-path=/var/run/sshd --without-rand-helper --with-tcp-wrappers --with-pam --with-libedit --with-kerberos5=/usr --with-ssl-engine --with-selinux --with-consolekit --with-xauth=/usr/bin/X11/xauth --with-default-path=/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games --with-superuser-path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11 --with-cflags='-O2 -fPIE -DLOGIN_PROGRAM=\"/bin/login\" -DLOGIN_NO_ENDOPT -DSSH_EXTRAVERSION=\"Debian-5ubuntu1\"' --with-ldflags='-fPIE -pie'

```

[https://launchpad.net/ubuntu/+source/openssh](https://launchpad.net/ubuntu/+source/openssh)

Click on one of the versions you want to see, then on the right you'll see a block with "Builds".  Click on the one for the architecture you care about, then view the build log.  You can search for "configure" in the build log and find it.  

Again, I would hope there's a better way, but I don't know it.

---

