---
title: "Issues unlocking a user's account."
date: 2014-03-13
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-03-13
I am working with Ubuntu 12.04, and currently experiencing issues in unlocking someones account (I'm working on this to study for my LPIC): 
The account below, unless I am mis-reading the output, shows locked -- but the OS isn't allowing me to unlock the account. After trying out the commands below under sudo, I then switched to the root account, but haven't experienced any improvement. 

root@predator451:~# passwd -S silverheart
silverheart L 03/11/2014 0 99999 7 -1
root@predator451:~# usermod -U silverheart
usermod: unlocking the user's password would result in a passwordless account.
You should set a password with usermod -p to unlock this user's password.
root@predator451:~# usermod -p S*nsh!n3
-su: !n3: event not found
root@predator451:~# usermod -p silverheart S*nsh!n3
-su: !n3: event not found
root@predator451:~# usermod -p S*nsh!n3 silverheart
-su: !n3: event not found
root@predator451:~# usermod -p "S*nsh!n3" silverheart
-su: !n3": event not found
root@predator451:~#

*****************************
So, I checked 'man usermod' to find out what am I missing...

       -U, --unlock
           Unlock a user's password. This removes the '!' in front of the encrypted password. You can't use this option with -p or -L.

           Note: if you wish to unlock the account (not only access with a password), you should also set the EXPIRE_DATE (for example to 99999, or to the EXPIRE value from /etc/default/useradd).

 -e, --expiredate EXPIRE_DATE
           The date on which the user account will be disabled. The date is specified in the format YYYY-MM-DD.
*****************************

root@predator451:~# usermod -e 2014-09-05 silverheart
(This seemed to work, so I tried expanding on it.)

root@predator451:~# usermod -U -e 2014-09-05 silverheart
usermod: unlocking the user's password would result in a passwordless account.

root@predator451:~# usermod -p S*nsh!n3  -e 2014-09-05 silverheart
-su: !n3: event not found
root@predator451:~# ^C
root@predator451:~# usermod -p "S*nsh!n3" -e 2014-09-05 silverheart
-su: !n3": event not found
root@predator451:~# usermod -U -p S*nsh!n3 -e 2014-09-05 silverheart
-su: !n3: event not found


What am I doing wrong?

---

### Post by steeldriver on 2014-03-13
1) !n3 is being interpreted as a history command by the shell - double quotes won't prevent that (single quotes might)

2) I don't think you can use usermod -p like that (the argument needs to be the encrypted / hashed password, not a plaintext password)

Have you considered just using the passwd command (i.e.plain  [FONT=courier new]passwd silverheart[/FONT], and then follow the on screen prompts) to set a usable passwd for the account?

---

### Post by Priest Apostate on 2014-03-14
Thanks for the assist. I was able to resolve the issue, as it seems that the account owner didn't set up their password like they told me they did...I handled that, I was able to proceed.

---

