---
title: "[SOLVED] Sudo Commands Don't Work"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by noahclark on 2008-10-01
If I run sudo apt-get update or sudo apt-get upgrade nothing happens.  Same thing if I run sudo adduser xxxxx. No user is added.  The only thing that possibly changed is I deleted my public key on the server used to login by copying a different one to the server, but I just copied the other private key over and that allows me to sign in.  I believe this problem was occurring before I even messed up my keys though.  Any ideas on why sudo commands won't run?  

Thanks!

---

### Post by dwhitney67 on 2008-10-01
Anything dealing with public/private keys shouldn't matter, since sudo does not rely on such.  It's configuration lies in /etc/sudoers (which you cannot peruse without the proper credentials... sorry).

Are you sure that you are logged into an account recognized as a sudo-er?  Obviously without being able to run sudo, I cannot think of a way to determine that.

But in essence, the first account you created for your system is (probably and most likely) the sudo-er account.

List /etc/passwd to see your system's accounts.
```
cat /etc/passwd
```

---

### Post by noahclark on 2008-10-01
I just ran cat /etc/passwd and I got the list of user names, groups, home directories, etc, etc, on each line.

If I run sudo cat /etc/passwd it does nothing.

Thanks.

---

### Post by dwhitney67 on 2008-10-01
On your system, do you have a user with a user-id of 1000 or greater?  Look for the numbers in the /etc/passwd listing.

The user with the lowest number (greater than or equal to 1000) is probably the sudo-er.  Are you logged into this account?

Also, can you verify that sudo is on your system?  Run
```
ls -l sudo
```
Verify that it is an executable file.

P.S.  My notebook battery is dying... this may be my last post for the night.

---

### Post by noahclark on 2008-10-01
ls -l sudo 
ls: sudo: No such file or directory

How do I reinstall this or fix it?

locate sudo returns /usr/bin/sudo in the list

---

### Post by aysiu on 2008-10-01
Try this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by noahclark on 2008-10-01
I'm going to have to boot up into rescue mode over at the office in order to check that out.  I can't ssh in from here.  Thanks again for all your help!

---

### Post by noahclark on 2008-10-01
Fixed! I remember messing around with groups a few weeks back and removed my self from the admin group.

---

