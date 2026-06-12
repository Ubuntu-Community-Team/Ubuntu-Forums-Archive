---
title: "root password prompt for sudoonly once??"
date: 2005-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by bjunix on 2005-04-14
Hello,

i regulary have set a root passwd at expert installation. i altered sudoers the way that i need rootpw to execute sudo commands.
now if sudo has got the root passwd it remembers it and wont ask for any password the next time i execute sudo.

what do i have to do that sudo losses its password memory?

thanks in advance.
greetings
bjunix

edit:

allright i got it by myself:
this is what my /etc/sudoers.conf looks like: 
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification
User_Alias                                      ADMIN = bjunix
# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn
Defaults:ADMIN          timestamp_timeout=0, rootpw, passwd_tries=1

# User privilege specification
root    ALL=(ALL) ALL
ADMIN  ALL=(ALL) ALL



```

---

### Post by accuser on 2005-04-15
You can also do:
```

$ sudo su

```
which will start a new shell as root. The benefit of this over other methods is that the shell prompt changes, giving some indication of the nature of the newly acquired power... :-)

---

### Post by packet on 2005-04-15
Personally I always do:

```
sudo bash
``` 

to make a root shell, don't know if sudo su is any better or not.  But this way it does read in the .bash_rc and everything.

--P>G>>

---

### Post by moky on 2005-04-20
I had the same problem : when I type 
$ sudo su,
the console take  the root privileges without asking password. (He just ask the first time)

I realy think that this "no root" system of Ubuntu is mostly "Windows like" as far as security is concerned : how should do someone which is too bad to search on a forum and hack  /etc/sudoers.conf ?

Laurent

---

### Post by moky on 2005-04-20
I made the same change than bjunix (but typing my username instead of bjunix of course).

Now I have this discution with my terminal :

```

moky@ubuntu:~$ sudo su
Password:
Sorry, try again.
sudo: 1 incorrect password attempt
moky@ubuntu:~$ sudo su
Password:
Sorry, try again.
sudo: 1 incorrect password attempt
moky@ubuntu:~$ sudo bash
Password:
Sorry, try again.
sudo: 1 incorrect password attempt
moky@ubuntu:~$

``` 

any comment ? It is possible I made mistake in /etc/sudoers but I can not check : I am no more root ! :sad: 

Thanks for help
Laurent

---

### Post by matid on 2005-04-20
[QUOTE=packet]Personally I always do:

```
sudo bash
``` 

to make a root shell, don't know if sudo su is any better or not.  But this way it does read in the .bash_rc and everything.

--P>G>>[/QUOTE]

That's IMO the best way:

```
sudo -s
```

---

