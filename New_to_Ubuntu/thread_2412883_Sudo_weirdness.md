---
title: "Sudo weirdness"
date: 2019-02-18
forum: New to Ubuntu
---

### Post by nselby on 2019-02-18
Suddenly I have been kicked out from sudo in terminal. My user is an administrative user according to the Settings -> User dialogues. 


I can still install (using my password as administrative user in the GUI), but if I pop open a terminal and do sudo foo and try to authenticate it fails. I can also not su - . 


I have dropped into the recovery boot mode, mounted / as rw and done adduser [user] sudo and been told that the user is already in the sudo group. 


I did note that the admin group had been deleted. I recreated it, added my user to admin group. Rebooted. Still cannot sudo anything in terminal. 


This is frustrating. Any ideas? 


Thanks in advance

---

### Post by TheFu on 2019-02-18
Which release?
Please show the output from the 'id' command.
Did you modify the sudoers file in anyway?

The admin group isn't likely connected.

---

### Post by sisco311 on 2019-02-18
Please also post the exact error message. And if you can still use polkit then post the content of the sudoers file:
```
pkexec cat /etc/sudoers
```

---

### Post by nselby on 2019-02-18
Thanks, both.

@TheFu:

```
l@l:$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.2 LTS
Release:	18.04
Codename:	bionic
```

@sisco311:

```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"


# Host alias specification


# User alias specification


# Cmnd alias specification


# User privilege specification
root	ALL=(ALL:ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL


# See sudoers(5) for more information on "#include" directives:


#includedir /etc/sudoers.d
```

Sorry, @TheFu there is no error message other than:

```
l@l:~$ sudo cat output.txt 
[sudo] password for l: 
[sudo] password for l: 
Sorry, try again.
[sudo] password for l: 
```


Note that the output above to @cisco311 means that I can authenticate as sudo through the GUI but not (for some reason) in terminal...

---

### Post by sisco311 on 2019-02-19
Strange. "Sorry, try again."  means that sudo thinks that you did not enter the correct password. 

Make sure that the caps and/or num lock is off and you are using the same input keyboard layout in the terminal emulator as the one in the other apps. Simply type in the password straight in the terminal window to see if it's displayed correctly. 

If the password is correct then check the log file:
```
pkexec tail /var/log/auth.log
```maybe it will reveal more about the nature off the issue.

It also could be something PAM related. In which case we will need to check the PAM settings:
```
head -n-0 /etc/pam.d/*
```

---

### Post by TheFu on 2019-02-19
Just to expand on sisco311's ... is the language and keyboard layout for the console set to the same value as used by the GUI? 

 I've had issues when using US-standard for the console, but US-with dead keys in the GUI. I suspect with other countries and languages, this happens much more often.

and the '**id**' command output?

BTW, my question was if you'd modified the sudoers or not.   Don't really care to do a diff myself.  Also, there are suders.d/ and files in there which could break it.  Did you touch any of those?

---

### Post by nselby on 2019-02-20
Thanks for your hel so far @sisco311 and @TheFu


@sisco311: Thanks. snips below; I am highly suspicious of "auth could not identify password for [l]".  


I'm confident I'm not fatfingering the password because  I am able to do it in the UI, just not in terminal; a couple of days ago before coming her, I typed it plaintext into the terminal just as you suggested and also typed the password into a text editor and cut and pasted it into the terminal to assure myself I hadn't typed poorly. No cigar. I have not (intentionally) altered the sudo files of anything, but there's no accounting for my stupid, so who knows.


Outputs: 


auth:```

Feb 20 10:26:05 l polkitd(authority=local): Operator of unix-session:2 successfully authenticated as unix-user:l to gain ONE-SHOT authorization for action org.freedesktop.policykit.exec for unix-process:7206:1233517 [bash] (owned by unix-user:l)
Feb 20 10:26:05 l pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Feb 20 10:26:05 l pkexec[25309]: l: Executing command [USER=root] [TTY=/dev/pts/1] [CWD=/home/l] [COMMAND=/usr/bin/tail /var/log/auth.log]
Feb 20 10:37:34 l sudo: pam_unix(sudo:auth): authentication failure; logname= uid=1000 euid=0 tty=/dev/pts/1 ruser=l rhost=  user=l
Feb 20 10:37:40 l sudo: pam_unix(sudo:auth): conversation failed
Feb 20 10:37:40 l sudo: pam_unix(sudo:auth): auth could not identify password for [l]
Feb 20 10:37:42 l sudo:        l : 1 incorrect password attempt ; TTY=pts/1 ; PWD=/home/l ; USER=root ; COMMAND=/bin/ls
Feb 20 10:37:50 l polkitd(authority=local): Operator of unix-session:2 successfully authenticated as unix-user:l to gain ONE-SHOT authorization for action org.freedesktop.policykit.exec for unix-process:7206:1233517 [bash] (owned by unix-user:l)
Feb 20 10:37:50 l pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Feb 20 10:37:50 l pkexec[25790]: l: Executing command [USER=root] [TTY=/dev/pts/1] [CWD=/home/l] [COMMAND=/usr/bin/tail /var/log/auth.log]
```

pam:

```

==> /etc/pam.d/sudo <==
#%PAM-1.0


session    required   pam_env.so readenv=1 user_readenv=0
session    required   pam_env.so readenv=1 envfile=/etc/default/locale user_readenv=0
@include common-auth
@include common-account
@include common-session-noninteractive
@include common-auth
auth       required   pam_u2f.so




==> /etc/pam.d/systemd-user <==
# This file is part of systemd.
#
# Used by systemd --user instances.


@include common-account


session  required pam_selinux.so close
session  required pam_selinux.so nottys open
session  required pam_loginuid.so
session  required pam_limits.so
@include common-session-noninteractive
session optional pam_systemd.so
```




@TheFu, great question, and I think the languages are set the same - I cerrtainly didn't change it since the time it was working and then stopped. Also, no I have not touched sudoers.d ... :)


id output:
```
uid=1000(l) gid=1000(l) groups=1000(l),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lpadmin),126(sambashare),1002(admin)
```

---

### Post by nselby on 2019-02-23
?

---

### Post by majcherek-maciek on 2019-02-26
Maybe try setting password again for that user...
or add new one and try on it.

---

