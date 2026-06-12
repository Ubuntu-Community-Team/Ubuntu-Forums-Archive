---
title: "/etc/crontab runs script for &lt;user&gt; but not root"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by xiney1 on 2008-05-28
Greetings all:

I want to run a backup script as root, but crontab doesn't execute the script. To verify it wasn't my script I am running a couple simple commands as can be seen in the below excerpt from my /etc/crontab entry. I noticed that if I ran the commands as user "csmith" they execute fine but if I try to run the same command as "root" nothing is written out. (That is, according to my crontab entry, I'm writing out the date and a comment to a temp file which works for "csmith" for "root". The file has permissions 777 and is owned by csmith)

After the crontab script below I've included what I'm seeing in the file /var/log/auth.log. Notable is the indication that 
   "pam_unix(cron:account): account root has expired (account expired)"
but I didn't think that root was supposed to be an active login.

Ultimately this script will probably be run from cron.daily but I wanted to test it out in /etc/crontab first.

Any ideas?

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
* *     * * *   csmith  echo "... date by csmith..." >> /tmp/cas.date 2>&1
* *     * * *   csmith  /bin/date >> /tmp/cas.date 2>&1
* *     * * *   root    echo "... date by root..." >> /tmp/cas.date 2>&1
* *     * * *   root    /bin/date >> /tmp/cas.date 2>&1

---------- Produces the following output in /tmp/cas.date------
---------- I noticed the msg & the date are reversed in order
---------- but I figure that's just a caching issue or something
Wed May 28 08:35:01 MDT 2008
... date by csmith...
Wed May 28 08:36:01 MDT 2008
... date by csmith...


---------- /var/log/auth.log ----------------
May 28 08:29:01 charles CRON[791]: PAM adding faulty module: /lib/security/pam_smbpass.so
May 28 08:29:01 charles CRON[791]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May 28 08:29:01 charles CRON[791]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May 28 08:29:01 charles CRON[791]: pam_unix(cron:account): account root has expired (account expired)
May 28 08:29:01 charles CRON[792]: PAM adding faulty module: /lib/security/pam_smbpass.so
May 28 08:29:01 charles CRON[792]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May 28 08:29:01 charles CRON[792]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May 28 08:29:01 charles CRON[792]: pam_unix(cron:account): account root has expired (account expired)
May 28 08:29:01 charles CRON[793]: PAM adding faulty module: /lib/security/pam_smbpass.so
May 28 08:29:01 charles CRON[793]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May 28 08:29:01 charles CRON[793]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May 28 08:29:01 charles CRON[793]: pam_unix(cron:session): session closed for user csmith
May 28 08:29:01 charles CRON[793]: pam_unix(cron:session): session opened for user csmith by (uid=0)
May 28 08:29:01 charles CRON[794]: PAM adding faulty module: /lib/security/pam_smbpass.so
May 28 08:29:01 charles CRON[794]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May 28 08:29:01 charles CRON[794]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May 28 08:29:01 charles CRON[794]: pam_unix(cron:session): session closed for user csmith
May 28 08:29:01 charles CRON[794]: pam_unix(cron:session): session opened for user csmith by (uid=0)
May 28 08:29:01 charles CRON[795]: PAM adding faulty module: /lib/security/pam_smbpass.so
May 28 08:29:01 charles CRON[795]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May 28 08:29:01 charles CRON[795]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May 28 08:29:01 charles CRON[795]: pam_unix(cron:account): account root has expired (account expired)

---

### Post by quelx on 2008-05-28
Try adding the command to the roots crontab directly ```
sudo crontab -e
```

---

### Post by xiney1 on 2008-05-28
I tried that earlier to no avail, but I tried it again. Note that the below cron entry includes "who it should run as" - I didn't think I needed that the first time I ran it (just now) but I got the same results - namely, nothing gets output.

Which makes me wonder... why is it that the entry in the /etc/crontab file gets run, but the entry I enter via "sudo crontab -e" doesn't seem to get run?


Here's the output from...
--------- sudo crontab -l-----------
#
# /etc/cron.d/svn: crontab fragment for svn
#  This does a backup of all theSVN repositories defined within the command below

* *   * * * root   echo "-- date by root via sudo crontab -e" >> /tmp/cas.date 2>&1
* *   * * * root   /bin/date >> /tmp/cas.date 2>&1
* *   * * * csmith   echo "-- date by csmith via sudo crontab -e" >> /tmp/cas.date 2>&1
* *   * * * csmith   /bin/date >> /temp/cas.date 2>&1

---

### Post by quelx on 2008-05-28
remove the user references when editing a users crontab (**crontab -e**)

```
* * * * * echo "-- date by root via sudo crontab -e" >> /tmp/cas.date 2>&1
* * * * * /bin/date >> /tmp/cas.date 2>&1 
```

EDIT: I noticed a mistype I don't know if you had it in your script date line has **temp** when it should be **tmp** plus the user csmith will not be able to write to the **/tmp/cas.date** because the root user will own the file.

---

### Post by xiney1 on 2008-05-29
First, thanks for the "temp" correction. Terribly embarassing.

However, removing the user from the "sudo crontab -e" entry didn't do me any good - still nothing gets executed. For temporary purposes the /tmp/cas.date file was set as 777.

I thought that perhaps if the file /etc/crontab existed (I renamed /etc/crontab) that the cron entries set for root by "sudo crontab -e" wouldn't get executed but that wasn't true.

A colleague asked why my script had to run as root. Well, it didn't, if I diddled with some group permissions, which was really the proper thing to do. So now my script executes fine as a user != root. But it sure makes me wonder why I can't get a cron entry to run as root. Oh, well, my immediate problem is solved.

---

### Post by nealmcb on 2008-07-30
This is probably related to this bug in hardy:

'Account has expired' message when adding a new user, after "passwd -l root"

 [https://bugs.edge.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.edge.launchpad.net/ubuntu/+source/shadow/+bug/238755)

There is a workaround there.

---

