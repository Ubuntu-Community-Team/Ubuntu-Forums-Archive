---
title: "Likewise, Active Directory, and Hardy Heron 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ZTiger on 2008-04-25
I have installed Likewise and figured out how to add the computer to my domain. 

The problem is when I try to log in. I've tried DOMAIN\username and just username. In either case I will get a blank error window. It just says "Error" and has an "OK" button.

The error message happens when I use local or domain account, however after about 3 tries the local account will log into the system.

Any help would be appreciated.

---

### Post by heathlair on 2008-05-05
Try using the following format *username@domain*

---

### Post by nullimage on 2008-05-06
I had a very similar problem, if you check /var/log/auth.log you'll probably see an error regarding daemons. The likewise daemon wasn't running, it had to be started manually from /etc/init.d, like: ```
sudo /etc/init.d/likewise-open start
``` (i'm not sure right now about the name, just do an ls and check).

After try logging in with DOMAIN\username.

---

### Post by lazyart on 2008-05-06
I joined my Ubuntu box to my windows domain using sadms.  When I log in I don't even specify the domain.  To test I disabled another account in AD and tried to log in with just the username and it told me the account was disabled....

---

### Post by capt scroggins on 2008-05-15
> **lazyart said:**
> I joined my Ubuntu box to my windows domain using sadms.  When I log in I don't even specify the domain.  To test I disabled another account in AD and tried to log in with just the username and it told me the account was disabled....

Can you be more specific on how you used sadms? What is that? I was able to join my domain but can not log in even when using FQDN.

---

### Post by rpalmer2181 on 2008-05-20
> **ZTiger said:**
> I have installed Likewise and figured out how to add the computer to my domain. 

The problem is when I try to log in. I've tried DOMAIN\username and just username. In either case I will get a blank error window. It just says "Error" and has an "OK" button.

The error message happens when I use local or domain account, however after about 3 tries the local account will log into the system.

Any help would be appreciated.

That's because the service isn't starting on boot. Run the two commands below.

sudo update-rc.d likewise-open defaults

sudo /etc/init.d/likewise-open start

---

