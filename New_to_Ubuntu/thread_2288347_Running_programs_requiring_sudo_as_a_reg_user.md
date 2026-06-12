---
title: "Running programs requiring sudo as a reg user?"
date: 2015-07-26
forum: New to Ubuntu
---

### Post by MGrowl on 2015-07-26
i.e. Powertop. Is there anyway a normal user can run it without root privilege? 

 Let's say I ```
chmod
``` the program or use ```
chown
``` to a reg user?

I'm trying to do this to arpon, and I don't see any of these working. 

Are programs like these "hard-coded" to only run as root? 

Or is there a conf file that can be manipulated so a reg user can run these?

---

### Post by jason_gibson2 on 2015-07-26
You can run them as any user. The restriction requiring root is determined by what file you are trying to modify. The easiest way to do it in my eye would be to give a no password sudo to a given user like so

I like separate lines for each thing, easier to manage I think. YMMV

```
user hostname =NOPASSWD:/bin/chmod
user hostname =NOPASSWD:/bin/chown
```

I'm pretty sure this way is how you do multiple commands in one line in the sudoers file

```
user hostname =NOPASSWD:/bin/chmod:/bin/chown
```

Can also do by group

```
%group hostname =NOPASSWD:/bin/chown
```

This will give the user or group sudo rights to only that command. However this gives them rights to chown and chmod files outside of their $HOME as well so not exactly the best idea.

*EDIT* These would of course go into a file in /etc/sudoers.d/
I highly recommend activating the root password when messing with the sudoers file as you can easily lock yourself out of sudo if you have a typo or some other syntax error in the file. Then just wipe out the root password when done to lock the root account again.

---

### Post by sandyd on 2015-07-26
> **MGrowl said:**
> i.e. Powertop. Is there anyway a normal user can run it without root privilege? 

 Let's say I ```
chmod
``` the program or use ```
chown
``` to a reg user?

I'm trying to do this to arpon, and I don't see any of these working. 

Are programs like these "hard-coded" to only run as root? 

Or is there a conf file that can be manipulated so a reg user can run these?

There are two main reasons that apps require root privileges to run

a) Program is not readable by users other than the user/group owner
b) Program itself requires root privileges for what it does.

In this case, I would guess that it is b). Arpon likely requires to write/intercept traffic on network devices to function, which requires root privileges (Disclaimer, this is a guess, I have never used arpon, or know how it works)

---

### Post by MGrowl on 2015-07-26
Thanks @jason & @Sandyd

Let's say, as an example, I run **powertop **on an adm account with the tunables turned to "good", then I switch to a regular user. Would **powertop **still be running when one is logged-in to a reg user acct...all still tuned to "good"? 

*I'm thinking this would also apply to **arpon**, if the answer is "yes" to the former question?*

---

### Post by MGrowl on 2015-07-26
Thanks for the help. Just ran the said applications and switched accounts. And they're still running. I should've checked that as a first solution, my bad.

---

### Post by Lars Noodén on 2015-07-26
You could make a group to run powertop and the other programs and then grant limited permission to that group.  Below is an excerpt from sudoers where users in the group "power" can run powertop as root but only with no options:

```

%power ALL=(ALL:ALL) NOEXEC: /usr/sbin/powertop ""

```

The double quotes after the program mean that no options are allowed.  The NOEXEC is there just in case, it prevents shell escapes, but powertop probably doesn't have any.

---

