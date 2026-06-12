---
title: "How can install XP inside Ubuntu OS?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by mac143_01 on 2008-06-01
please tell me the step by step procedure, thanks...

---

### Post by bumanie on 2008-06-01
You can't unless you use a virtual environment such as virtualbox or vmware etc. You can put ubuntu inside windows, where windows sees ubuntu as just another windows program, but you can't do it the other way around. You would be best to use a virtualised environment or to dual boot xp and ubuntu. If you dual boot, install xp first.

---

### Post by k3lt01 on 2008-06-01
I wouldn't think you could install XP within Ubuntu. Why would you want to anyway? Yes there is WINE but it would be an exercise in futility installing Windows through that. If you really need XP do a dual boot setup

---

### Post by rraj.be on 2008-06-01
The best solution is to setup virtual environment like vmware or virtual box.

you can get vmware from vmware website

[http://register.vmware.com/content/download.html -]("http://register.vmware.com/content/download.html -")

---

### Post by mlentink on 2008-06-01
> **bumanie said:**
> You can put ubuntu inside windows, where windows sees ubuntu as just another windows program

I'd be extremely interested to learn how you do this. Could you elaborate?

Edit: to the OP: I run Virtualbox 1.6, start it up in a separate workspace and use the seamless mode. Works for most Windows stuff, except for software that needs hardware 3D acceleration. Office, and the usual stuff work fine

---

### Post by sayakb on 2008-06-01
> **mlentink said:**
> I'd be extremely interested to learn how you do this. Could you elaborate?

Read [here]("http://http://wubi-installer.org/").
Also +1 to [VirtualBox]("http://www.virtualbox.org/"). It goes easy on the resources.. :)

---

### Post by mlentink on 2008-06-01
Sorry. Wubi does ***not*** run Ubuntu as a windows program. It merely installs ubuntu in a virtual partition which you can manipulate as  Windows (or rather: NTFS) files. You will not be able to start up Ubuntu from within windows, but only at boot-time.

---

### Post by sayakb on 2008-06-01
> 
Quote:
                                                                      Originally Posted by **bumanie**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5090750#post5090750")                 
                 *You can put ubuntu inside windows, where windows sees ubuntu as just another windows program*
                                 
I'd be extremely interested to learn how you do this. Could you elaborate?

I have never used Wubi (It didn't exist during my Windows days ;)).. And if it's not Wubi, count me into the list of those seeking answer to the question you asked.. :D

---

