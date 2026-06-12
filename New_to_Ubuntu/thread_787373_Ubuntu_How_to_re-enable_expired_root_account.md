---
title: "Ubuntu: How to re-enable expired root account?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Chimmer on 2008-05-08
Running Ubuntu 8.04. 

Quick summary:
Had a password assigned to root at one time. Disabled it using the command $sudo passwd -l root

Wanted to log in as root again, tried sudo su and got the message "Your account has expired; please contact your system administrator.
su: user account has expired"

Tried re-enabling using the command $sudo passwd root

It accepted the password change but still won't let me log in as root. I get the same error message about account expiring.

Any idea how to fix this?

---

### Post by Cappy on 2008-05-08
man passwd shows this option:
```
       -u, --unlock
           Unlock the named account. This option re-enables an account by
           changing the password back to its previous value (to value before
           using -l option).

```

---

### Post by bodhi.zazen on 2008-05-08
There is no need to enable the root account. Ubuntu uses sudo.

To obtain a root shell :

```
sudo -i
```

---

### Post by lemming465 on 2008-05-08
Try *sudo passwd -u root*.  The lock behavior is controlled by whether or not the second field of /etc/shadow starts with "!" or "!!" (locked) or "$" (unlocked).  You can fix it by hand using "sudo vipw" if you have to; that will edit /etc/passwd first and /etc/shadow second.

In generally a combination of "sudo" for individual commands, "sudo -i" for multiple comamands, and "gksu ..." for GUI programs can let you do everything you need without enabling the root account.  On Ubuntu I hardly ever enable root.

---

### Post by Chimmer on 2008-05-08
Thanks for all of the replies. I rarely use root but I was having some problems with Firefox and I was trying to delete some of the files. 

The sudo -i works for me.

---

### Post by 2CV67 on 2009-02-06
I have not logged in as root since Edgy & haven't needed or wanted to, thanks to sudo & gknautilus.

Today though, I did want to (to look at some GUI stuff - I know how dangerous it is & have no intention of launching browsers or staying in root for any time or going there repeatedly).

I tried with the old password from Edgy days & got the usual error message about wrong password.

I checked that the option "Allow local system administrator login" was checked.

I went into Users & Groups & "Set password by hand" for root.

Now when I try to log-in with that password I get the message about "your account has expired - contact system administrator".

I looked in etc/shadow which starts "root:$1$r..."
and in etc/shadow- (is that previous version?) which starts "root:!$1$Y..."

How can I get from there to being able to log-in as root, even though I know very well that this is not recommended & should not be used where avoidable?

...by PM if you don't want to publish "dangerous" information!

Thanks!

---

