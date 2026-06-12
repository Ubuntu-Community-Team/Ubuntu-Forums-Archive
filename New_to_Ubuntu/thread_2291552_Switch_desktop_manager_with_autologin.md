---
title: "Switch desktop manager with autologin"
date: 2015-08-20
forum: New to Ubuntu
---

### Post by rccharles on 2015-08-20
Is there a way of switching desktop managers when I have set autologing?  I'd like to change the desktop manager for the next boot before I logoff.

Running: Ubuntu and Lubuntu.

Robert

14.04 ltsl

---

### Post by CantankRus on 2015-08-21
You can just logout and change the session at the greeter.
or

If **accountsservice** is running you need to edit /var/lib/AccountsService/users/[COLOR="#FF0000"]username[/COLOR]
Where [COLOR="#FF0000"]username[/COLOR] is your actual username.

Check if accountsservice is running ...
```
ps -aef | grep [a]ccountsservice
```

If so, edit the file in your **/var/lib/AccountsService/users/** directory.
ie the file for me is /var/lib/AccountsService/users/[COLOR="#FF0000"]glen[/COLOR]
```
[User]
XSession=**ubuntu**
Background=/home/glen/.xplanetFX/output/xplanetFX1.png
SystemAccount=false
```


I could manually edit the file as root or 
run a terminal command to edit ....
```
sudo sed -i "/XSession=/c\XSession=**Lubuntu**" /var/lib/AccountsService/users/$USER
```

---

