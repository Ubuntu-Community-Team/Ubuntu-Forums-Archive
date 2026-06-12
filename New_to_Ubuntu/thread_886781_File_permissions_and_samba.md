---
title: "File permissions and samba"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-08-11
I have my home server that i set up as a Samba PDC.  My shares i have on the machine, and my profiles folder werent working.  I had granted permission in samba for users to have access to the shares.  However my folders were root owned and had access denied to all but root.  Just for getting it up and working, i gave those folders chmod 777 permissions, and they work fine.  What kind of chmod definition should i use on that in order to not let it be wide open, but at the same only allow access to authenticated samba users?

---

### Post by bobnutfield on 2008-08-11
You can set up samba to require a password from authorized users.  This is done is user-level security in your samba config file.

---

### Post by bodhi.zazen on 2008-08-11
> **Mauler5858 said:**
> I have my home server that i set up as a Samba PDC.  My shares i have on the machine, and my profiles folder werent working.  I had granted permission in samba for users to have access to the shares.  However my folders were root owned and had access denied to all but root.  Just for getting it up and working, i gave those folders chmod 777 permissions, and they work fine.  What kind of chmod definition should i use on that in order to not let it be wide open, but at the same only allow access to authenticated samba users?

You should not be sharing files owned by root.

Make a shared directory, either in /home or say /media/samba

The change the ownership and permissions of the mount point to the samba user (the one you use to mount the share).

---

### Post by Nepherte on 2008-08-11
I believe the default permission is 755. Be sure to follow  bodhi.zazen's advice as well.

---

### Post by Mauler5858 on 2008-08-11
The two folders im referring to are:

/home/samba/profiles/(contents are the romaing profiles)

and

/shared/mediastore

So are you guys saying i should take ownership and give 755 permissions to these folders.  My question is...given what i have here, how far back should the permissions and ownership go.  For instance i wouldnt want to chown the /home folder for the first example...just wanting to know where to draw the line.

---

