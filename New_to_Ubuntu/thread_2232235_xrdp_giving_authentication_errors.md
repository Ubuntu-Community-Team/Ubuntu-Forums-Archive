---
title: "xrdp giving authentication errors"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by Ayush_Maheshwari on 2014-06-30
I am using xrdp to remote login to my Xubuntu desktop addition. Whenever I try to install anything or access system settings I get the following error:

Authentication Error
Software can't be installed or removed because the authentication service is not available. 

I can install the application without any issues if I do it directly.

Any idea as to what I might have done wrong with xrdp configuration?

---

### Post by Ayush_Maheshwari on 2014-06-30
Any ideas?

I read some post and they pointed to Xauthority issue. I tried 2 things:

1. Create an Xauthority file under my home directory and give it permission 600. --> Did not work
2. Added following in Xsession --> Did not work[FONT=arial]
[/FONT]
[COLOR=#2E8B57][FONT=Monaco]mcookie|sed -e 's/^/add :0 . /'|xauth -q[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]xinit -- -auth "$HOME/.Xauthority"[/FONT][/COLOR]

---

