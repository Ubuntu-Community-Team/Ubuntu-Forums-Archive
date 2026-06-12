---
title: "Backup question"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by guilly on 2008-08-13
I was wondering if anyone knows of any backup utilities that can be configured on a server that automatically backs up certain files from a host computer whenever that particular host logs onto the network?? I doubt this is possible but I thought it would be worth a shot. 

Also, My server is running 7.04 with LAMP, the host would be a variety of OS X Leopard and Windows Vista.

Thanks

---

### Post by Pro-reason on 2008-08-13
That sort of thing would normally be initiated from the host computer, wouldn't it?

---

### Post by powerpleb on 2008-08-13
> **guilly said:**
> I was wondering if anyone knows of any backup utilities that can be configured on a server that automatically backs up certain files from a host computer whenever that particular host logs onto the network?? I doubt this is possible but I thought it would be worth a shot. 

You could probably write a script that tests to see if hosts are connected and if they are, performs the backup. Then you could make it a cron job to happen how ever often you think necessary.

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

---

### Post by guilly on 2008-08-13
> **Pro-reason said:**
> That sort of thing would normally be initiated from the host computer, wouldn't it?

I was thinking the same thing as well but I thought it was worth a shot any ways.

---

### Post by guilly on 2008-08-13
> **powerpleb said:**
> You could probably write a script that tests to see if hosts are connected and if they are, performs the backup. Then you could make it a cron job to happen how ever often you think necessary.

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html](http://www.unixgeeks.org/security/newbie/unix/cron-1.html)

humm never thought of that. I'll check out the link thanks. Now I'm assuming the folders would need to be shared some how from the host p.c in order for the server to be able to access them correct?

thanks again

---

### Post by DGortze380 on 2008-08-13
my guess is you would need a script in conjunction with the rsync command.

---

