---
title: "More SFTP questions"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by antony7 on 2014-04-26
Hi Guys,

I'm still playing with SFTP and have a number of issues:

1) If I run sftp user@host on the host itself I can successfully connect to sftp. However if I try this through Core FTP - I get "Permission Denied - Data port failed - Error loading directory"
2) If I try and connect to SSH through Putty I login and am booted straight out - I guess the Permission denied issue above has different effects for Putty
3) Is it possible to have some users Chrooted with others not? Its just if I connect through Putty I want full server control but with SFTP i'm limiting the path access. Does sudo break out of restrictions set in place for SFTP/SSH?
4) Oh and late addition: SSH from the localhost errors as well with permission denied? SFTP fine.

Thanks

Antony

---

### Post by Lars Noodén on 2014-04-26
For question #3, yes, it is possible to chroot some users and not others.  Use the [Match](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) directive to define which group to apply the chroot to. 

```

Subsystem sftp internal-sftp

Match Group sftp-only
        ChrootDirectory /home
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp -d %u

```

Then just add the users to be chrooted to the group *sftp-only*.  Users not in that group will have normal access, assuming that the rest of the configuration is left as it was with the defaults.  That arrangement also forces SFTP and disallows shell access for the group.

---

### Post by antony7 on 2014-04-26
That is super thanks. By amending my user to be in the root group rather than my remotefileaccess I bypassed the MatchGroup parameters. The issue however is that for some reason the user did not have the correct permissions to my /var/www/%USER/www folder so when they logged in Chrooted it said permission denied. But great help. THanks.

---

### Post by Lars Noodén on 2014-04-27
/var/www/%USER/www should be owned by the user, but the ones above it owned by root.

```

sudo chown root:root /var/www
sudo chown root:root /var/www/*
sudo chmod 755 /var/www
sudo chmod 755 /var/www/*

```

(You could also use 701 instead of 755.)

Then you can chroot to %u and cd to /var/www/%u/www, which will appear as /www inside the chroot.

```

ChrootDirectory /var/www/%u
ForceCommand internal-sftp -d /www

```

---

### Post by Adonosonix on 2014-04-27
deleted. Sorry.

---

