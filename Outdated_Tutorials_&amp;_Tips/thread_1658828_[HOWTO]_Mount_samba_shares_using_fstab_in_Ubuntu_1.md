---
title: "[HOWTO] Mount samba shares using fstab in Ubuntu 10.10"
date: 2011-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by krippa on 2011-01-03
You can likely find this somewhere else but it was giving me a lot of headache so I decided to put some info here, surely it will at least help me in the future.

Scenario: You have a samba share on your network and you want to put it in fstab instead of using ubuntu default gvfs that are not accessible using all types of applications and also do not mount on boot. Also you want read and write access and not show the password to anybody who knows some linux basics.

So here are the options I use, feel free to improve and comment:
credentials - stores username and password, should not be readable by anyone other than root
rw - read/write
iocharset - since my samba server is linux I specify utf8 to make sure the right encoding of special chars
uid - this is what was giving me the headache - without this I could create folders but nautilus thought I didn't have permissions to create files/folders within that directory. 
gid should solve previous problem to let users of a group access the share

So lets go to the command line and start configuring stuff:
```

sudo mkdir /root/smb/ 
sudo chmod 700 /root/smb/
sudo gedit /root/smb/credentials

```
and copy paste user/password in here in the following format:
```

username=<username>
password=<pass>

```

Next up lets create share dir and edit fstab:
```

sudo mkdir /media/<wherever-you-want-it>
sudo gedit /etc/fstab

```

And paste the following line (replacing stuff with brackets to their applicable value)

```
//<samba-server>/<share-name> /media/<wherever-you-want-it> cifs credentials=/root/smb/credentials,rw,iocharset=utf8,uid=1000,gid=1000 0 0
```

NOTE: uid and gid might change if you don't want to use the first user and first group created on the installation to access the share. Look at /etc/passwd file to figure out which uid/gid to use.

---

### Post by splurben on 2011-01-10
[SIZE="4"]Why are the characters **[COLOR="Red"]it>[/COLOR]** in the final code snippet with the line to be added to fstab?

I'm pretty sure they shouldn't be there. I left them out and this fstab entry worked, just out of curiosity, I put it in and it definitely didn't work (bad line in fstab error).

Kirk[/SIZE]

---

### Post by krippa on 2011-01-11
> **splurben said:**
> [SIZE="4"]Why are the characters **[COLOR="Red"]it>[/COLOR]** in the final code snippet with the line to be added to fstab?

I'm pretty sure they shouldn't be there. I left them out and this fstab entry worked, just out of curiosity, I put it in and it definitely didn't work (bad line in fstab error).

Kirk[/SIZE]

You're right. The whole "<wherever-you-want it>" is just a placeholder where you put the name of the folder you want to mount in. I guess me missing the last dash might make it more confusing. I will change the original.

---

### Post by ledzpg on 2011-01-13
Nice, I'll try this tonight. :D

---

