---
title: "can't log into xsession"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by msmarc on 2008-07-30
When I was configuring my system I removed gdm thinking that on startup I would be taken to a terminal where I could startx when I wanted. I had problems when rebooting so I reinstalled gdm and now I have new errors.

The first one is the classic:
your $HOME/.dmrc file has incorrect permissions

I try and solve this my chmod ~ 700 and chmod .dmrc 644
But when I reboot the error still comes up and the permissions change back to being wrong

The 2nd error I get is:

{
/etc/gdm/xsession: Beginning session setup...
Can't Create dir /var/Desktop
Can't Create dir /var/Templates
and so on through allt the var folders

Start IM through /etc/x11/xinit/xinput.d/all_ALL link to /etc/x11/xinit/xinput.d/default

(seahorse-agent:5188):libgnomeevfs-WARNING **: Unable to create ~/.gnome2 directory:Permission denied
Could not create per-user gnome configuration directory '/var/.gnome2/' : Permission denied
}

I recently installed vcm and I was changing permissions in the var folder to set up ftp. But i created new dirs for all permissions I changed.

ls -li info for /var is: 
 drwxr-xr-x  19 root root    4096 2008-07-29 15:08 var

ls info for home/(username) is:
drwx------ 29 msmarc msmarc  4096 2008-07-29 19:11 msmarc

Are my permissions for /var or /home wrong?

---

### Post by JoneYee on 2008-07-30
Doubtful it will work but try this if possible:

```
sudo aptitude purge gdm && sudo aptitude install gdm
```

---

