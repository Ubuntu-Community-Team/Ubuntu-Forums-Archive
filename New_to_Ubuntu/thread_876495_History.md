---
title: "History"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by lizandeen on 2008-07-31
Are there any decent and easy to use applications along the lines of CCleaner or WindowWasher, for clearing history from my computer (both desktop and internet)for Ubuntu? Thanks in advance, Lizandeen

---

### Post by collinp on 2008-07-31
I believe that whenever you reboot your computer Linux clears the /tmp directory, and if you use Firefox for your web browsing use the tool in Tools/Clear Private Data to delete the internet temp files.

---

### Post by halitech on 2008-07-31
if you have multiple users and everyone logs in under their own account, no one will ever see where you've been or what you've looked at. at most, all you need to do is set Firefox to clear history and clear cache when closed (Edit Preferences - Privacy and put the check in beside clear data when closing firefox)

---

### Post by ibuclaw on 2008-07-31
> **halitech said:**
> if you have multiple users and everyone logs in under their own account, no one will ever see where you've been or what you've looked at. at most, all you need to do is set Firefox to clear history and clear cache when closed (Edit Preferences - Privacy and put the check in beside clear data when closing firefox)

... Provided that the "other" bit is set to 0.

Regards
Iain

---

### Post by halitech on 2008-07-31
> **tinivole said:**
> ... Provided that the "other" bit is set to 0.

Regards
Iain

you lost me here on this one...:(

---

### Post by ibuclaw on 2008-07-31
750 permissions on the top home directory :)

By default, the permissions are set to 755, so any "other" user can read/execute your files.
ie:
[PHP]
ls -ld $HOME
drwxr-xr-x 75 iain iain 4096 2008-08-01 02:22 /home/iain
[/PHP]
that is
owner=rwx
group=r-x
other=r-x

chmod it to 750 and we get
[PHP]
ls -ld $HOME
drwxr-x--- 75 iain iain 4096 2008-08-01 02:22 /home/iain
[/PHP]
other is now=---
So anyone who isn't "iain" or a member of the group "iain" will not have the permissions to view the contents.

To set it, run
```
chmod 750 $HOME
```

Regards
Iain

---

### Post by halitech on 2008-07-31
ok, I learned something new tonight :D I never looked into this as I am a single user (my son as his own little windows computer that he is just a normal user of and doesn't touch mine :) )

---

### Post by sstvinc2 on 2008-07-31
I agree with all of the posts above, unless lizandeen is trying to be really sneaky.  My recollection is that WindowWasher overwrites all of the disk area that the history data was stored in with zeroes so that it can't ever be recovered (as opposed to just delinking the file pointers).  I'm kinda curious now.  Anyone know of a good way to do that?

---

### Post by sharks on 2008-07-31
go to places---recent documents and clear history.

---

### Post by lizandeen on 2008-08-04
Re:History
sstvinc2 is kind of correct (though I prefer privacy/security conscious to sneaky ha ha!).So is there anyway to completely and irretrivably wipe my history to all prying eyes? Thanks to all who have replied.

---

### Post by halitech on 2008-08-05
follow tinivoles instructions and use a strong password that no one else knows and you won't have to worry about removing anything.

---

