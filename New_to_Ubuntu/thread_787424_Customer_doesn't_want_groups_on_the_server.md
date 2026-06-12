---
title: "Customer doesn't want groups on the server"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by hopelessnecro on 2008-05-08
I set up a file server in ubuntu for a client. They do not want a logon from their windows workstations, so they have an ownership problem with the files. They all work in the same files from time to time, but when one of them does open a file they get ownership, therefore making the file read only for everyone else.
Is there anyway to change this to work like windows giving everybody access?

yes. I know that is unsafe, that is why i used linux, to set up a secure way to do things and save money.

If there isn't any way to change this, how can i write a chmod script that loads at boot and executes every 30 seconds to a minute.

thanks folks.

---

### Post by freebeer on 2008-05-08
Are you connecting through Samba?

If so, you might want to look at the "create mask" directive.  I think "create mask = 666" will do what you want, but best to read up on it.  No need for a script running every few seconds. :D

---

