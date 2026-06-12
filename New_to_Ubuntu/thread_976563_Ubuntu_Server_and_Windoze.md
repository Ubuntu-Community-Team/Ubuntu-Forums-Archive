---
title: "Ubuntu Server and Windoze"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by warhelmet on 2008-11-09
Hi folks - newbie here. First post.

I've bought a Dell PowerEdge605 and installed Ubuntu Server on it.

I sort-of know what I want to do with it. I'm reasonably tech-savvy and can read documentation including how-tos. But I do get a bit confused and there is a lot to take in.

I've got a bunch of Windoze machines on my network. I want to have file and printer sharing. Given that they are XP Home, XP Pro, Vista Home premium - am I better off going the Samba route or making the Windoze machines - say - talk NFS? I don't have any Windoze Server machines at the mo, so AD is out of the question.

---

### Post by _sAm_ on 2008-11-09
Samba works great with both Windows xp and Vista - so learn how to set it up the way you want it. Here is two guides(there is a lot of guides out there for samba and Ubuntu server - google will show you); 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

You can adm the server from Windows with putty([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)) using ssh([https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)). 

Many like to have GUI in the beginning(and not just a terminal), if that is the case you could;

1. Install swat([https://help.ubuntu.com/community/Swat](https://help.ubuntu.com/community/Swat)) so you can adm the server via Firefox on the XP pc. 
or
2. Install the Ubuntu desktop on the server and the nx server([http://www.nomachine.com/](http://www.nomachine.com/)). 

I started with Ubuntu desktop and NX and liked it alot. After learning more I now only use Ubuntu server and ssh.

---

### Post by warhelmet on 2008-11-10
Thanks,

It's got me a bit further down the road I want to go on. I can get things working but...

---

### Post by _sAm_ on 2008-11-10
> I can get things working but...

Just ask if you have more questions:-)

---

### Post by PreviousN on 2008-11-10
My input: NFS is near impossible on Windows. I tried it on multiple machines multiple times and for (many) multiple hours (reading multiple sources/documentation). It gave me multiple headaches. 

Stay with samba, you'll thank yourself in the end. Also, consider sharing the printers with CUPS. Its pretty good and I've got a duplexing laser printer hooked up to a network of around 7 computers. :-)

Another tip: VNC also works well at first when you are adjusting to ssh.

---

### Post by PreviousN on 2008-11-10
Opps. Accidental double post.

---

### Post by cdtech on 2008-11-10
Samba, ldap and cups would be worth looking into for a full file server setup.

---

