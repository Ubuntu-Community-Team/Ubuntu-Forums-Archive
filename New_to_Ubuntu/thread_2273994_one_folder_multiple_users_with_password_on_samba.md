---
title: "one folder multiple users with password on samba"
date: 2015-04-17
forum: New to Ubuntu
---

### Post by myron2 on 2015-04-17
Hi all

is there any tricks to achieve this problem? the problem is ex /accounting_folder with valid user pasword now if more than 3 computer access the folder with same username, password and the fourth computer wont login can you check if my samba is correct. thanks
```

  security = share

[fbpublic_folders]
     comment = open folder for everyone
     writable = yes
     path = /home/samba/fbpublic_folders
     public = yes
     guest ok = yes
     guest only = yes
     guest account = nobody
     browsable = yes

[misdept]
     comment = for mis folders only
     browseable = yes
     writeable = yes
     path = /home/samba/misdept
     available = yes
     valid users = mis
     guest ok = no

[accounting]
     comment = for accounting folders only
     browseable = yes
     writeable = yes
     path = /home/samba/accounting
     available = yes
     valid users = accounting
     guest ok = no

[operations]
     comment = for RM's folders only
     browseable = yes
     writeable = yes
     path = /home/samba/operations
     available = yes
     valid users = operations
     guest ok = no

[feudc_accounting]
    comment = for feudc accounting files only
        browseable = yes
        writeable = yes
        path = /home/samba/feudc
        available = yes
        valid users = feudcaccnt
        guest ok = no

[audit]
        comment = for audit only
        browseable = yes
        writeable = yes
        path = /home/samba/audit
        available = yes
        valid users = audit
        guest ok = no

[cusa]
        comment = central services folders
        browseable = yes
        writeable = yes
        path = /home/samba/cusa
        available = yes
        valid users = cusa
        guest ok = no

[purchasing]
        comment = purchasing folders
        browseable = yes
        writeable = yes
        path = /home/samba/purchasing
        available = yes
        valid users = purchasing
        guest ok = no

[costcontroller]
        comment = cost folders
        browseable = yes
        writeable = yes
        path = /home/samba/costcontroller
        available = yes
        valid users = costcontroller
        guest ok = no

[engineering]
        comment = engineering folders
        browseable = yes
        writeable = yes
        path = /home/samba/engineering
        available = yes
        valid users = engineering
        guest ok = no

[golfoperations]
        comment = golf operations folders
        browseable = yes
        writeable = yes
        path = /home/samba/golfoperations
        available = yes
        valid users = golf
        guest ok = no

[housekeeping]
        comment = housekeeping folders
        browseable = yes
        writeable = yes
        path = /home/samba/housekeeping
        available = yes
        valid users = housekeeping
        guest ok = no

[warehouse]
        comment = warehouse folders
        browseable = yes
        writeable = yes
        path = /home/samba/warehouse
        available = yes
        valid users = warehouse
        guest ok = no

[resortmanager]
        comment = RM folders
        browseable = yes
        writeable = yes
        path = /home/samba/resortmanager
        available = yes
        valid users = resortmanager
        guest ok = no

[humanresource]
        comment = human resources folder
        browseable = yes
        writeable = yes
        path = /home/samba/hr
        available = yes
        valid users = humanresource
        guest ok = no
```

---

### Post by bab1 on 2015-04-17
> **myron2 said:**
> Hi all

is there any tricks to achieve this problem? the problem is ex /accounting_folder with valid user pasword now if more than 3 computer access the folder with same username, password and the fourth computer wont login can you check if my samba is correct. thanks

 ```
 
security = share


[accounting]
     comment = for accounting folders only
     browseable = yes
     writeable = yes
     path = /home/samba/accounting
     available = yes
     valid users = accounting
     guest ok = no

[operations]
     comment = for RM's folders only
     browseable = yes
     writeable = yes
     path = /home/samba/operations
     available = yes
     valid users = operations
     guest ok = no

[feudc_accounting]
    comment = for feudc accounting files only
        browseable = yes
        writeable = yes
        path = /home/samba/feudc
        available = yes
        valid users = feudcaccnt
        guest ok = no

```
There is no limit set for simultaneous users by default.  You would have to explicitly set that in the smb.conf file

I notice thta you have set the security to  ```
security = share
```...this is deprecated in current versions of Samba and makes the following useless ```
valid users = <whatever>
```

So what do you have for this parameter in your smb.conf file```
max connections =  <some-number>
```

Please post all terminal output using the [noparse]```

```[/noparse] code blocks.  You can do that by clicking on the [SIZE=5]**#**[/SIZE] icon at the top of the *advanced editor* or by manually wrapping the code blocks around the text.

---

