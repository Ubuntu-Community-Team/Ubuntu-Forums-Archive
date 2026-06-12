---
title: "Webmin and Protected Web Directories Apache"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by heiNey on 2013-01-06
I followed what skodama said to do here:  [http://ubuntuforums.org/showthread.php?t=1252163](http://ubuntuforums.org/showthread.php?t=1252163)

now, it asks for credentials to log in, but when i supply them, it says that the login/pw are wrong.

anyone have any ideas?

---

### Post by heiNey on 2013-01-08
bump.

anyone?

---

### Post by terjef on 2013-03-08
[COLOR=#000000]Hi.

Might be late, but still ;-)

After what skodama said to do here: [/COLOR][http://ubuntuforums.org/showthread.php?t=1252163](http://ubuntuforums.org/showthread.php?t=1252163)

Try this in webmin:

Below are the easy steps to password protect a directory using Webmin:


1) login in to the Webmin interface


2) Main menu -> choose "Others" -> choose "Protected Web Directories" -> "Add protection for a new diretcory"
3) in settings:


Directory path: select the path/directory which you want to protect
File containing users: if any, or choose automatically


File containing groups: if any, or choose None


Password encryption: choose the encryption type


Authentication realm: the name will appear in login box, ex: "Admin Area"


Users to allow: put the username you want to setup in "Only Users:" field


4) click the "Create" button


5) in the next page, you can add/edit password for this user, then click submit/save button. It's done!


Regards
Terje

---

