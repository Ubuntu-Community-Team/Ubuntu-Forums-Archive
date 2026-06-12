---
title: "[SOLVED] folder sharing guest access"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by freddybob on 2008-06-15
I'm trying to share folders between two Ubuntu 8.04 machines.

On the first machine everything worked well.  The second machine can see and access the files.

But on the second machine, when I right-click on the folder and go to Sharing Options the "Guest access (for people without a user account)" checkbox is permanently greyed out.

How do I enable guest access?

---

### Post by joshsmith on 2008-06-15
have you fiddled with your samba configuration before, if so the dialog will block some options as they have already been set in the file 
/etc/smb.conf

you should go into synaptic, select completely remove samba (which will get rid of this config file), then install samba to get a fresh one. now that you are back with the default config file, the guest box should be available

---

### Post by freddybob on 2008-06-15
I have tried reinstalling, purging and installing again.  Still no guest access.

I even tried deleting /etc/samba/smb.conf but no luck.

---

### Post by freddybob on 2008-06-30
a screenshot

---

### Post by allartk on 2008-07-02
you're sure you have removed samba-common completly including configuration in synaptic? It solved the same problem on my system.

---

### Post by freddybob on 2008-07-05
thanks, purging samba-common fixed the problem (although the purge also removed wine and ubuntu-desktop which then had to be reinstalled)

---

### Post by khanongsouk on 2009-09-10
i know that this has been marked solved for a while now but i've found another way to enable the grayed out guest access check box without purging smaba-common.

just add this to your /etc/smb.conf

```
usershare allow guests = yes
security = share
guest ok = yes
guest account = your_logon_name_here
```

---

### Post by saidbakr on 2009-09-11
> **khanongsouk said:**
> i know that this has been marked solved for a while now but i've found another way to enable the grayed out guest access check box without purging smaba-common.

just add this to your /etc/smb.conf

```
usershare allow guests = yes
security = share
guest ok = yes
guest account = your_logon_name_here
```

I have made the code suggested in the above quote but I get the following error when press create share:

> 
'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.


Please take a look at the attached image.

---

### Post by khanongsouk on 2009-09-12
is "Everyone" the username you use to login to ubuntu?

---

### Post by sharat87 on 2010-01-07
```
sudo service samba restart
```

solved it for me :P

---

