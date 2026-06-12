---
title: "Modify Samba Conf with Sed - Help"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by ubunnewbie on 2013-01-14
I am trying to add this line to my script to modify the samba conf. I tested this in terminal and it would open up the conf inline and replace the "#   security = user" with "security = user". However, when I open up the samba.conf file using gedit, it doesn't reflect the change. Can someone point me in the right direction?

```
sed 's\#   security = user\security = user\'  /etc/samba/smb.conf
```Thank you.

---

### Post by steeldriver on 2013-01-14
'sed' is not interactive by default (i.e. the changes are only reflected in the output stream, not the original file) - you either need to redirect the output to a temp file and then copy it e.g. you could do

```

cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
sed 'your command' /etc/samba/smb.conf.bak > /etc/samba/smb.conf

```or use the '-i' option on the sed command line

FYI you should be leery of specify exact amounts of whitespace in pattern matches - it makes the expression rather fragile

---

### Post by bab1 on 2013-01-14
> **ubunnewbie said:**
> I am trying to add this line to my script to modify the samba conf. I tested this in terminal and it would open up the conf inline and replace the "#   security = user" with "security = user". However, when I open up the samba.conf file using gedit, it doesn't reflect the change. Can someone point me in the right direction?

```
sed 's\#   security = user\security = user\'  /etc/samba/smb.conf
```Thank you.

FYI -- the default for Samba is *security = user*.  There is no need to explicitly state that.

---

### Post by ubunnewbie on 2013-01-14
Taking what you said about sed not being interactive and needed to be redirect, I used the following code and it worked. I created a new conf just for testing.
```

sed 's\#   security = user\security = user\'  /etc/samba/smb.conf | sudo tee /etc/samba/smb1.conf
```

Thank you!:-D

---

