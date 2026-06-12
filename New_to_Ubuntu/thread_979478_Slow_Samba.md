---
title: "Slow Samba"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-11-12
I am getting extremely slow login and logoff when logging onto my Samba domain.  Posted below is my conf file.  what am i doing wrong?
```


[global]
	name resolve order = wins bcast hosts
	server string = %h 
	logon path = \\vader\profiles\%U
	workgroup = sithlords.com
	os level = 20
	domain master = yes
	encrypt passwords = true
	security = user
	passdb backend = tdbsam
	wins support = true
	domain logons = yes
# <...remainder of parameters...>
add machine script = /usr/sbin/useradd -d /dev/null -g samba-clients -s /bin/false -M %u





[profiles]
	csc policy = disable
	preserve case = no
	write list = %u,%root
	store dos attributes = yes
	default case = lower
	create mask = 0600
	case sensitive = no
	browseable = no
	writeable = yes
	printable = no
	path = /home/samba/profiles
	hide files = /desktop.ini/ntuser.ini/NTUSER.*/
	comment = Users profiles
	directory mask = 0700

[Media Store]
	writeable = yes
	write list = darth
	path = /share/mediastore
	revalidate = yes
	comment = 
	valid users = darth
	public = yes
	create mode = 0600
	browsable = yes
	directory mode = 0700

```

---

### Post by Crafty Kisses on 2008-11-12
What are the results of this command?
```
lsmod | grep sk
```

---

### Post by Mauler5858 on 2008-11-12
when i do that it returns me to the next line with no results.

---

