---
title: "I Can't get super user privileges 8.04"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by wbrokow1 on 2008-05-01
I tried to edit /etc/modprobe.d/blacklist and I can't become 
super user; I tried su & sudo. but it won't let me save the edited file. 

 I usually use gentoo but ubuntu installed fine on my 
IBM a22m laptop and ran well, except for the netgear wireless 
card.

Any help on this would be appreciated.
Also, I get an error when I do "sudo" in a terminal.
I'll post the error when I get home tonight.

ANy help is appreciated.
Thanks

---

### Post by aysiu on 2008-05-01
The correct command should be ```
sudo nano -B /etc/modprobe.d/blacklist
``` If that doesn't work, perhaps you've accidentally taken your own *sudo* privileges away, in which case [this](http://www.psychocats.net/ubuntu/fixsudo) should help.

---

### Post by Hospadar on 2008-05-01
what happens when you go in a terminal "sudo nano /etc/modules.d/blacklist", then after you edit the file, Ctrl-o to save.

Please post up any errors or messages you get.

---

### Post by wbrokow1 on 2008-05-01
When I typed su, it asks for a password, I type the password and it gives an authentication failure.

When I type sudo it gives a "Unable to Resolve host Rowena-laptop" error.  

Now, let me first say I have been messing around to get my 
netgear WG511 card to work and deleted one of the 127.0.0.1 entries in the network setup.  Could this be the source of the host error.

Thanks again for any help

---

### Post by Monicker on 2008-05-01
> **wbrokow1 said:**
> When I typed su, it asks for a password, I type the password and it gives an authentication failure.

When I type sudo it gives a "Unable to Resolve host Rowena-laptop" error.  

Now, let me first say I have been messing around to get my 
netgear WG511 card to work and deleted one of the 127.0.0.1 entries in the network setup.  Could this be the source of the host error.

Thanks again for any help

See this to resolve the localhost error:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by wbrokow1 on 2008-05-01
Wow, you guys are fast!!!
Thanks for the responses.
You truly blow away gentoo support forums!
I might just totally switch, let me give it a couple months.
What kernel version is in 8.04 by the way?
Thanks.

---

