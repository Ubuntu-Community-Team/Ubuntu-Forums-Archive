---
title: "Changed group membershipm now I cant login"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by desperado618 on 2008-07-13
I have 2 accounts (root and user).
Some of my backend applications could not be configured to sudo for every command so I decided to change the group membership on the user account from admin to root. Upon doing so, i rebooted and cannot login.

When I attempt to log in, the splash screen flashes and then returns to the login prompt (not the same as typing an invalid password). I am also being told that the root pw is wrong for that account though its the same password I always type when i sudo. 

Any advise would be greatly appreciated.

---

### Post by bab1 on 2008-07-13
Boot off the LiveCD and change the group membership back.  

BTW -- the root account does not have a password when you first install the system.  The sudo password is your user account pw allowing you to perform tasks as root.  Not the same as the root account password.

---

### Post by desperado618 on 2008-07-13
Thanks.. your a lifesaver

---

### Post by desperado618 on 2008-07-13
By the way, when i boot to the live cd, will I be able to see the users on the hard drive? I am not near the pc now to test.

---

### Post by bab1 on 2008-07-13
It should mount the partitions.  You might have to use the CLI accomplish your goal.  I have never had to do what you need to do.  :D  I do know it can be done.  Try the GUI first if that is what you are more comfortable with.  Make sure you are modifying the correct files.  The OS that is in control is the one on the CD,  *NOT* the one you installed.

Read the man pages for "useradd" and see "group" and "passwd"

---

### Post by desperado618 on 2008-07-14
I am now able to log in. My issue was a Path file modification. I logged in via the cli and corrected the path. However, now that im logged in, I cannot change my group membership from root back to admin. All options are greyed out. I need to change it back because it has affected many applications.

As usual. i appreciate any advise.

---

### Post by sisco311 on 2008-07-14
Reboot in Recovery Mode and add your user to the 
admin group from a root shell:
```
addgroup *username *admin
exit
```

---

### Post by desperado618 on 2008-07-15
So the root cause of my issues seems to stem from my Sudo account. After changing my group membership, my sudo account stopped working. Therefore eerything that requires sudo access does not work (including the user management screen). I tried running the addgroup command from the cli but the change was never implimented because of the sudo account. I booted from the LiveCD but it is not seeing my  HD for some odd reason. So I am looking into Recovery Mode now.

---

