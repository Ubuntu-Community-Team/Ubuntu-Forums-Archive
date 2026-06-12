---
title: "auto-mounting network share problem!"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by len1x on 2008-07-01
What's up,
Been struggling with this since an hour.. I want to automount some share on my network.

I added a line to fstab, here is the line
//server/LENiX /media/LENiX smbfs credentials=/etc/samba/creds 0 0

saved the fstab, tried to run sudo mount -a , it asks for a password, i put the password , and the share mounts just fine..

but the problem is, when I reboot, the share doesn't get auto mounted :confused:

Any idea how to make it auto mount?

many thanks in advance

p.s: thanks for jameslr on irc for helping me a lot with this issue, although we reached to what i explained..

Thanks again :)

---

### Post by benfindlay on 2008-07-01
You could write a script to mount it and then set the script to run at boot. This would also bypass the need for it to be in fstab. I use this specific tactic to mount 3 separate USB external drives to share points on my server, so I can access them from Windows and Mac OS X machines.

Would this work for you?

---

### Post by len1x on 2008-07-01
I'd do that (as a last resort) but I'd like to fix my fstab, I'd like to know the reason why it's not working, let's call it more info :)..

I think it should work, because I read some other threads and nobody complained about adding a line to fstab.

So anybody? I hope somebody knows how to fix it :)

---

### Post by len1x on 2008-07-01
I fixed it.. I got rid of the Credentials option, i passed the username and password directly ( username=aaa.password=aaa ).. and it worked ;/

Any idea why using credentials gave me trouble ?

---

