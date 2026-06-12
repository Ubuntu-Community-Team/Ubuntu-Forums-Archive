---
title: "ICEAuthority and SMB mount fix"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by bladedog on 2005-04-11
If you're having problems with mounting a smb $HOME directory and getting the "ICEauthority locking error" when you login to GNOME read further...

Took me forever to figure out what the heck was going on but it's related to file locking problems between UNIX and Samba. To get around this I set an environment variable called ICEAUTHORITY in the /etc/security/pam_env.conf file. This writes the .ICEauthority file somewhere else other than in the samba $HOME share and it set when PAM is invoked. At the bottom of the pam_env.conf put something like this...

# For Ubuntu to write .ICEauthority file somewhere else
ICEAUTHORITY DEFAULT=/tmp/.@{PAM_USER}_ICEauthority

This will create a file in /tmp for each specific user that logs in.

If there's not one already I'll put up a HOWTO for using Ubuntu and mounting SMB $HOME shares soon.

---

### Post by jorns on 2005-04-12
[QUOTE=bladedog]If you're having problems with mounting a smb $HOME directory and getting the "ICEauthority locking error" when you login to GNOME read further...

Took me forever to figure out what the heck was going on but it's related to file locking problems between UNIX and Samba. To get around this I set an environment variable called ICEAUTHORITY in the /etc/security/pam_env.conf file. This writes the .ICEauthority file somewhere else other than in the samba $HOME share and it set when PAM is invoked. At the bottom of the pam_env.conf put something like this...

# For Ubuntu to write .ICEauthority file somewhere else
ICEAUTHORITY DEFAULT=/tmp/.@{PAM_USER}_ICEauthority

This will create a file in /tmp for each specific user that logs in.

If there's not one already I'll put up a HOWTO for using Ubuntu and mounting SMB $HOME shares soon.[/QUOTE]
 Great, an HOWTO had been great, because my 2 linux boxes ( debian and kubuntu ) does'nt like eachother whan i am using sambaserver. Have to use NFS instead, but i samba is bether since we also have some windows mascines here. 

So a HOWTO  would have been great.

thx.
jorns

---

### Post by kuleali on 2005-04-13
thank's

---

### Post by bobp0303 on 2005-07-27
Another seriously ugly hack is to put 
chmod 777 /home/<user name>/.ICEAuthority

in 

/etc/init.d/sysklogd

-- there has to be an uglier way, but this works for me :) :)

---

