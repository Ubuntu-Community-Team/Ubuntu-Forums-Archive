---
title: "can't log in  http://localhost:631/printers"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by klein5366 on 2013-05-21
hi 
i'v spent my day installing, a printer a brother mfc-j410w and it went ok but long i'm down to installing the fax software and it wont let me edit  [http://localhost:631/printers](http://localhost:631/printers) it asks for a username and password i'v tried everything no mater what i change it still wont let me in , is there an easy way to fix this easily?

---

### Post by steeldriver on 2013-05-21
Does your user account belong to the lpadmin group? that's required for some CUPS operations. You can check with the 'groups' or 'id' command (or 'getent group lpadmin' if you want to get fancy). If not you may need to add the account - either via usermod or (safer imho)

```
sudo gpasswd --add *youruser* lpadmin
```

---

### Post by pqwoerituytrueiwoq on 2013-05-21
for me my account username/password work, just like at the login screen

---

### Post by klein5366 on 2013-05-22
thanks  				 				 					 						 	[**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500") that worked like a charm. pqwoerituytrueiwoq after i did what 
				 				 					 						 	[**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500") suggested  that is the way it worked for me too i had never installed a brother printer before in Linux i got the printer part installed and the scanner is working but when i fax by the command line one line of text from gedit it faxes 17 blank pages lol and nothing but the headers from the fax machine hp's are much easer any ideas why it is sending all those pages ?

---

