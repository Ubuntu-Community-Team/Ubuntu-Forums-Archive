---
title: "Can't set guest read/write samba share"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by poisonborz on 2012-02-21
Hola,

I try to set up a samba share, like this:

```
[global]
workgroup = WORKGROUP
netbios name = server
guest ok = yes
read only = no
security = user
wins support = yes
null passwords = true
guest account = nobody
map to guest = Bad Password
os level = 66
log level = 2
local master = yes
unix extensions = no
 
[Media]
path = /media/ServerMedia/Media
browseable = Yes
read only = No
guest ok = Yes

[WebTemp]
path = /home/server/www/tmp/stor
browseable = Yes
read only = No
guest ok = Yes
create mask = 0777
available = Yes
create mode = 0777
directory mode = 0777
public = yes
writable = yes
```

Media can be reached by any guest, but with no write access - it works well.
I want the WebTemp share to be fully read/writeable to guests, but somehow it asks for user/password for every access. Why? As you can see above, I've tried a lots of parameters, but none work. The "stor" dir is also chowned by sambashare...
Thanks

---

### Post by poisonborz on 2012-02-22
The problem seemed to be with the folder that was located inside the www folder. No matter the permissions, somehow access was not granted. I "ln -s"-ed it to a folder in the system, and now it can be accessed as it set in Samba.

The (rather obvious :D) lesson here is that when two shares with same options are behaving differently, the problem lies within the folder's permissions/location.

---

