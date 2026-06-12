---
title: "Admin access and password problem"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by roboamebo on 2012-07-21
Hi all,

I'm new to Ubuntu and this community.

I installed ubuntu (the latest version) and have to say that is fantastic. All good.

But I made a mistake. I was checking around all the functions and changed my user account from "Administrator" to "Standard".

Of course, I used my (admin) password to "Unlock" the possibility to change settings.

After that I wanted to change it back to "Administrator", but I can not "Unlock" the function. A password is required and when I type my password (the one created during the installation and which is an admin password) it tells me that the password is wrong.

Is there an option to solve that, or should I delete all and install it again?

Thank you in advance... any help is much appreciated.

robi

---

### Post by cupera on 2012-07-21
Hi,
you may start your box in recovery mode. It will offer you a root prompt. Running following command should make you administrator again.
```
gpasswd -a admin robi
```Of course you replace *robi* with your actual linux username.
Then press Ctrl+Alt+Del to reboot.

I believe, that fresh installations don't show boot menu anymore, so you just keep pressing Esc or Ctrl or some cursor key when machine starts. You should then see a menu with few entries, one being marked *(recovery mode)*, pick it and proceed.

---

### Post by roboamebo on 2012-07-21
Hi Cupera,

thank you for the super fast reply. 

I've tried your suggestion few time, but unfortunately didn't changed the situation. I'm still not an admin.

Is there another option? 

Thank you again.
cheers
robi

---

### Post by steeldriver on 2012-07-21
Hi - what happens when you try cupera's solution exactly? in newer Ubuntu versions the admin group is 'sudo' not 'admin' and also the recovery console mounts the root filesystem read-only - have a go with the method described here

[http://ubuntuforums.org/showthread.php?t=2027450](http://ubuntuforums.org/showthread.php?t=2027450)

Substitute your actual username for *user*

---

### Post by roboamebo on 2012-07-24
Hi steeldriver,

Sorry for the late reply. I went to holidays on the date of your post and have limited acces to my home computer (on which I have Ubuntu).

As I am not in front of my computer, I can not tell you exactly what happened, but all looked fine, just didn't solved the problem.

I'm returning back on the 6th of August. I'll try the first option and document all detais/schreenshots and also try your option.

Will post backnthen.

Thank you again for the help.

I am realy pleased by the great comunity here.

Best
Robi

---

