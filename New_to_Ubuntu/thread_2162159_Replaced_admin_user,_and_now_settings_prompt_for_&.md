---
title: "Replaced admin user, and now settings prompt for &quot;root&quot; password rather than user's"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by TuxImpersonator on 2013-07-13
Hi all,

I recently wanted to encrypt my home folder so set up a new admin user, with an encrypted home, transferred files across from the old user, then deleted the old user. However going to a system settings that requires root (e.g. Software and Updates) now prompt for "root"'s password rather than the new (or old) user's password. The new user is definately in the sudo group and can run sudo commands in the terminal.

I realise that I could set the password for root ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)), but it seems there should be a better way. Is there a config file somewhere that set something like a default admin user?

Thanks,
Phil

---

### Post by steeldriver on 2013-07-13
I'm guessing here but try running

```
gksu-properties
```

from a terminal in the new account and making sure the mode is set to 'sudo' not 'su'

---

### Post by TuxImpersonator on 2013-07-13
> **steeldriver said:**
> from a terminal in the new account and making sure the mode is set to 'sudo' not 'su'

Thanks, but authentication mode is already set to sudo.

---

### Post by newb85 on 2013-07-13
How did you go about adding this new admin user?  When you open User Accounts and click on that user, does it show Account Type as Administrator or Standard?

Sorry if these seem like dumb questions, but it is possible to add a user to the sudoers list without making that user a part of the admin group.  I suspect that would result in behavior like what you're experiencing.  That's the only reason I ask.

---

### Post by TuxImpersonator on 2013-07-17
@newb85 : don't worry, it's normally a "dumb" question that finds the problem!

I can confirm the new user is an admin as well as being in the sudo group.

---

### Post by lotharmat on 2013-07-17
I think the behaviour you are after can be achieved as follows

open a terminal (How often is this said??)

type:

```
sudo visudo
```

look for the following line and copy it to the line below (replacing root with the username you want to have sudo access

```
root    ALL=(ALL:ALL) ALL

```

I did this to daughters debian install and it worked a treat - no admin access but she could install certain software! Anything major expected the admin (root) password.

HTH

---

### Post by lotharmat on 2013-07-17
I think you can also add

gnome-system-tools 

This will give you back the old familiar 'Users and Groups' gui.

---

### Post by TuxImpersonator on 2013-07-17
I'm in the sudoer list through the sudo group:
```
%sudo ALL=(ALL:ALL) ALL
```
Adding myself as a seperate line doesn't seem to fix the problem either.

Think I might need to file an ubuntu bug :(

---

### Post by Dave_L on 2013-07-17
I'm not sure if this is a factor, but is it possible that you inadvertantly enabled root login?

You can determine that by looking at root's entry in /etc/shadow, to see whether the second field is "!" (disabled) or a password hash (enabled).

If root login is enabled, you can disable it (recommended) using these instructions: [https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account](https://help.ubuntu.com/community/RootSudo#Re-disabling_your_root_account)

---

### Post by dannyboy79 on 2013-07-17
can you show us the following output please?
```
cat /etc/group
```

---

### Post by TuxImpersonator on 2013-07-17
@Dave_L
Yep, root is diabled

@dannyboy79
```
cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:philip
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:philip
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:philip
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:philip
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:
messagebus:x:105:
bluetooth:x:106:
scanner:x:107:
colord:x:108:
lpadmin:x:109:philip
ssl-cert:x:110:
lightdm:x:111:
nopasswdlogin:x:112:
netdev:x:113:
whoopsie:x:114:
mlocate:x:115:
ssh:x:116:
avahi-autoipd:x:117:
avahi:x:118:
pulse:x:119:
pulse-access:x:120:
utempter:x:121:
rtkit:x:122:
saned:x:123:
phil:x:1000:philip
sambashare:x:124:philip
mysql:x:125:
```

Thanks for the help guys, it's greatly appreciated!

---

### Post by Dave_L on 2013-07-17
```
sudo:x:27:
```

That's the only notable difference between your /etc/group file and mine.

You have no users in your "sudo" group.

Mine looks like:

```
sudo:x:27:USER
```

where USER is my actual username.

---

### Post by TuxImpersonator on 2013-07-17
That was it!

I didn't see it until I posted the above: whilst 
```
groups philip
```
included sudo, for some reason /etc/group didn't reflect that. I've manually added myself to the sudo group in /etc/group and everythings working again :)

Thanks again!

---

### Post by TuxImpersonator on 2013-07-17
Thanks @Dave_L, looks like we posted at the exact same time (great minds think alike and all that :) )

---

