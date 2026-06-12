---
title: "How to add user"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by UserJB on 2013-06-07
Hi,

I tried 'sudo adduser Joe' which seemed to work.  I could su to Joe.  But when I logged out and tried to log back in, the login screen didn't give me an option to login as Joe.  What's the correct way to add a user in ubuntu?

---

### Post by slickymaster on 2013-06-07
Using the command line:```
sudo adduser username
```and follow the prompts to give the account a password and identifiable characteristics such as a full name, phone number, etc.

Doing it graphically: [AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by UserJB on 2013-06-07
I can add a user with the 'adduser' command, but when I log out and try to login with that new userid, the ubuntu login screen won't give me the option of logging in as that userid.  It only lists the previous userids.  So, how can I add the new userid to the login screen so I can login as that userid?

---

### Post by UserJB on 2013-06-07
I did that already.  But when I log out and try to log in as the new userid, the ubuntu login screen doesn't list the new userid, and there's no way to change to that userid.  So, what else do I have to do?

---

### Post by overdrank on 2013-06-07
Hi and please do not create multiple threads on the same issue. Threads merged.

---

### Post by UserJB on 2013-06-07
Hi and it's a different issue.  Please read before merging.

---

### Post by slickymaster on 2013-06-07
> **UserJB said:**
> I did that already.  But when I log out and try to log in as the new userid, the ubuntu login screen doesn't list the new userid, and there's no way to change to that userid.  So, what else do I have to do?

Well, it should appear in the drop down list at login screen. Have you try to do it graphically through System > Administration > Users and Groups? Do it and see if that way the same thing happens.

---

### Post by UserJB on 2013-06-07
There is no 'System' menu.  So I haven't tried graphically.

When I try to login to the machine, it doesn't list an 'other' option which allows me to change the username.

---

### Post by Toz on 2013-06-07
Which version of Ubuntu are you using?

Can you post back the /etc/passwd entry for your "joe" account? 

Does a home directory exist for "joe" in /home?

---

### Post by UserJB on 2013-06-07
> /etc/os-release
    ::::::::::::::
    NAME="Ubuntu"
    VERSION="12.04.2 LTS, Precise Pangolin"

The entry for Joe (actually Tom) in /etc/passwd is:
    Tom:x:504:504::/home/Tom:/bin/sh

I think the problem is with the UID and GID.  If I create another username without specifying a UID and GID, and use the default instead, which turns out to be 1001, then that username is selectable in the login prompt.

However, that isn't good enough for me.  I want to create accounts with UID and GID of 500 so that I can read/write files on other partitions (those partitions were created in different distro's on Linux with users that had a UID and GID of 500).  Is there a way in Ubuntu to create accounts with a UID and GID of 500, and have it work?  And, why doesn't that work in Ubuntu?

---

### Post by Toz on 2013-06-07
Yes, the minimum default uid/gid is 1000. 

To change this default:

1. If you are using the accountsservice daemon:
```
ps -ef | grep accounts-daemon
```
...then edit /etc/login.defs and change the values of UID_MIN and GID_MIN (then reboot).

2. If you are not using the accountsservice daemon, the file you want to edit is /etc/lightdm/users.conf then restart the lightdm service.

---

### Post by slickymaster on 2013-06-07
> **UserJB said:**
> > /etc/os-release
    ::::::::::::::
    NAME="Ubuntu"
    VERSION="12.04.2 LTS, Precise Pangolin"

The entry for Joe (actually Tom) in /etc/passwd is:
    Tom:x:504:504::/home/Tom:/bin/sh

I think the problem is with the UID and GID.  If I create another username without specifying a UID and GID, and use the default instead, which turns out to be 1001, then that username is selectable in the login prompt.

However, that isn't good enough for me.  I want to create accounts with UID and GID of 500 so that I can read/write files on other partitions (those partitions were created in different distro's on Linux with users that had a UID and GID of 500).  Is there a way in Ubuntu to create accounts with a UID and GID of 500, and have it work?  And, why doesn't that work in Ubuntu?

In Ubuntu UID and GID start from 1000 rather than 500 such as on fedora, mageia, etc. Please see [UserNamespace]("https://wiki.ubuntu.com/UserNamespace").

---

### Post by UserJB on 2013-06-07
That worked.  Thanks!

---

### Post by matt_symes on 2013-06-07
Hi
> 
I think the problem is with the UID and GID.  If I create another  username without specifying a UID and GID, and use the default instead,  which turns out to be 1001, then that username is selectable in the  login prompt.

Just to clarify.

Lightdm will not display any users with a UID of less that 1000 unless you specifically configure it to.

Otherwise it would display all the system users as well.

Kind regards

---

### Post by Zill on 2013-06-07
> **UserJB said:**
> ...I want to create accounts with UID and GID of 500 so that I can read/write files on other partitions (those partitions were created in different distro's on Linux with users that had a UID and GID of 500).  Is there a way in Ubuntu to create accounts with a UID and GID of 500, and have it work?...
My /etc/login.defs includes the following:
```
#
# Min/max values for automatic uid selection in useradd
#
UID_MIN			 1000
UID_MAX			60000
# System accounts
#SYS_UID_MIN		  100
#SYS_UID_MAX		  999

#
# Min/max values for automatic gid selection in groupadd
#
GID_MIN			 1000
GID_MAX			60000
# System accounts
#SYS_GID_MIN		  100
#SYS_GID_MAX		  999
```
You could try editing these values but I suggest you need to be *very* careful to keep user (normally over 1000) and system (normally under 999) UID/GIDs separate. ;-)

---

