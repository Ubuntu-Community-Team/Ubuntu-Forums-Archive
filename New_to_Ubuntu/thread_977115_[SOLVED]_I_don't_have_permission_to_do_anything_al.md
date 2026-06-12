---
title: "[SOLVED] I don't have permission to do anything all of a sudden"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by sweetberry14 on 2008-11-09
I am not sure what happened, but I cannot save sound settings

stephanie@sexy-beast:~$ alsactl store 0
alsactl: save_state:1541: Cannot open /etc/asound.state for writing: Permission denied

or save files into /usr/local for installing a program

Help please!

---

### Post by skitter.rusty on 2008-11-10
> **sweetberry14 said:**
> I am not sure what happened, but I cannot save sound settings

stephanie@sexy-beast:~$ alsactl store 0
alsactl: save_state:1541: Cannot open /etc/asound.state for writing: Permission denied

or save files into /usr/local for installing a program

Help please!
Try going to **System > Administration > Users and Groups**. Select your account, click Unlock, Enter your Password and authenticate, then click properties and select the _User Privileges_ tab. Make sure _Administer the System_ is selected and click OK.

---

### Post by bodhi.zazen on 2008-11-10
use sudo or gksu for root access :)

---

### Post by sweetberry14 on 2008-11-12
ah ha! Thank you.

---

