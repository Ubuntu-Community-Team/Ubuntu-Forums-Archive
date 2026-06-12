---
title: "How to make a shared folder please?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-08-16
I have a linux set top box, and have created a NAS mount to my windows machine.

Now i would like to create the same on my laptop.

I have a folder on my ubuntu laptop which i want to share. I right click on it > sharing options > ticked share this folder.Then clicked on create share.

But i keep getting:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Can someone please guide me

Thanks

---

### Post by lisati on 2008-08-16
Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by jualin on 2008-08-16
I had that problem before when my system wasn't updated, have you run all the updates in your system?

---

### Post by iwannalearn on 2008-08-16
@lisati not sure if it's samba i need, as i need my linux stb to connect to my ubuntu laptop to share a folder. Is it not NAS (maybe i am mixing things up)

When i did it from my windows pc, i made a folder, right click, properties and shared this folder over network.

From my stb i used Windows (CIFS)
Server Name/IP : enter your server name or IP
Remote Path    : enter remote path ( e.g /my_shared_folder)
Username       : enter username needed to log in
Password       : enter password needed to log in, if password isn&#8217;t needed stay <no password>
Domain         : enter domain name, must be the same what is on server


This all went fine.


The linux options i have on my stb are

If selected is Unix/Linux ( NFSv3):
Server Name/IP          : enter the server name
Remote Path             : enter remote path
Save Configuration      : enter to confirm changes

Does this make any more sence?

@jualin yes mate my system is upto date

---

### Post by issih on 2008-08-16
I suspect you are using samba (at a guess you installed the nautilus-share package). In that case you probably need to reboot your machine to synchronise your login and smb passwords. Once thats done you should be able to share the folder quite happily.

You will want to use the windows settings (cifs) to connect to the samba share though, not nfs, thats a different kettle of fish.

Hope that helps

---

### Post by iwannalearn on 2008-08-16
@issih

That was it, just needed to reboot:lol:

Thanks to all for answering

Cheers

---

