---
title: "[SOLVED] How do I join a Windows workgroup?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by nathanscottdaniels on 2008-08-05
I have all my shared folders set up in Ubuntu.  On my Vista PC, when I go to look at the network computers, it shows two separate workgroups.  "4029", the one where all my windows PC's are, and "WORKGROUP," which contains only my Ubuntu laptop.  This is no big deal it is just annoying.  So how do I choose what workgroup I am in in Ubuntu.  I can't, for the life of me, find the option.  I bet I have to go edit some ultra-volatile file somewhere...

---

### Post by bpowell2005 on 2008-08-05
I believe you'll need to install Samba (which is a networking / file-sharing application) and then edit the /etc/samba/smb.conf file and look for "workgroup = " and add your workgroup name after the "=".

Once you make a change to Smb.conf, you'll most likely have to restart the samba service for the change to take effect.

---

### Post by Moridin333 on 2008-08-05
it's not hard at all

sudo gedit /etc/samba/smb.config

look for "# Change this to the workgroup/NT-domain name your Samba server will part of" (it's the first option)

sudo /etc/init.d/samba restart

and you're done.

---

### Post by nathanscottdaniels on 2008-08-05
I already had Samba, thats how I got the networking to work. 
Anyway, that was far too easy. Thanks for the help!

---

### Post by bpowell2005 on 2008-08-05
> **nathanscottdaniels said:**
> I already had Samba, thats how I got the networking to work. 
Anyway, that was far too easy. Thanks for the help!

That's what it's all about! Enjoy! I love your signature by the way; too true!

---

### Post by Moridin333 on 2008-08-06
Glad it worked.  let me know if you have any other problems.

---

### Post by W4JKA on 2008-08-19
Whatever version I have of samba, my config file is samba.conf.  I was able to edit it and make the windows workgroup name change.

Thanks

---

