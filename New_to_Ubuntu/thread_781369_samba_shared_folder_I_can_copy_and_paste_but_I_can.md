---
title: "samba: shared folder: I can copy and paste but I can't modify"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Telius on 2008-05-04
Hi guys,

I'm new at ubuntu and samba; I've been reading online for a week about them and succeded in installing ubuntu and samba on it. 

Now I've got a problem: with samba I've defined a shared folder (an ntfs from windows existing partitions on the same ubuntu pc) on my ubuntu pc that my other windows pc on the lan can access to. Assigned to my windows user write and read rights on samba.  The problem: I can see that shared folder, I can copy from my windows pc and paste in my ubuntu's shared folder but I can't modify those files... :(
Actually from my windows pc that shared folder appears to be set (in properties) as "only read" while on my ubuntu pc in samba it's set as write&read.

Could u pleas help me solving it? Thx

---

### Post by evymetal on 2008-05-04
Edit: I've just re-read your post - This should be doable somehow since you are reading a samba share from windows, not the other way around (afraid I don't know the trick, though)

I'm not 100% certain about this, but my experience is that this may not be something you can overcome (for a little while). If someone has got a fix for this then I'm really interested

Basically Samba tries to copy the system that Windows uses for filesharing. Microsoft always tried to keep this really secret to stop the open source community from being able to do this (and hence keep people stuck with windows so they can keep using their existing file shares). Despite this the samba team have, as you have seen, managed to guess/ spy their way into doing as much as possible, although Microsoft kept updating their system to try to stop samba working fully.

Recently there has been a huge court ruling that means Microsoft **have to** give this information away to the samba team and let it work (although they have to pay Microsoft a lot of money to get the information). It may take a few months to get the changes fully implemented, checked and packaged for Ubuntu - but I'm sure it's coming soon.

(hope that gives you a feel about why some of us don't like the way Microsoft have behaved)

BTW, Apple have started to behave like this recently too - e.g. you can stream music from Itunes to Rhythmbox, but Itunes has been updated so it won't play music streamed from Rhythmbox.

---

### Post by bilal.17 on 2008-05-04
I think you have to change the permissions from ubuntu to allow read and write to all users, you can do this by right clicking on the file and going to the permissions tab.

---

### Post by joshsmith on 2008-05-04
yes you need to change the permission of the folder in ubuntu. (not a samba specific thing)
to do this run
sudo gedit /etc/fstab
which is where drive info is stored

you should see the line associated with your ntfs drive(s) which will have something like 
umask =  007
change that bit to
umask = 000
this will give everyone permission to the group "others" permission to read/write to this drive (ie samba)

samba itself then decides whether it wants to give users over the network read/write access

---

### Post by Nythain on 2008-05-04
whats your /etc/samba/smb.conf file look like
and what do the permissions for the shared folder look like

---

### Post by Telius on 2008-05-05
> **Nythain said:**
> whats your /etc/samba/smb.conf file look like
and what do the permissions for the shared folder look like

I think  you got it:

```
Share definitions:

read only = yes

create mask = 0700

directory mask = 0700
```

which of these lines do I have to change (I don't want to make mistakes involving security: my aim is to let read and write only the windows' pcs users (with their own password) I have defined in samba)

Thank you all guys for your support :)

---

### Post by Telius on 2008-05-05
it doesn't work :(

trying to modify fstab in which i have umask set to 0222

EDIT:
done: set umask to 000 (thx again joshsmith :)) and now it works.

Now: is my system safe or can everybody from anywhere (not only the users I allow to in samba) access to my share folders? In other words (just to be sure :)) who does decide last? Samba with smb.conf or the fstab file? Thx

---

