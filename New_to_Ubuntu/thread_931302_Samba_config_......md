---
title: "Samba config ....."
date: 2008-09-27
forum: New to Ubuntu
---

### Post by stevoo on 2008-09-27
I have just come home after a long time and set up my network as it should. 
Since i am back to my old pc, i networked everything.

I have my server for the time being running on my laptop on ubuntu and i have my desktop running XP.

I have set up my samba for the place where a website that i was creating on my laptop and shared that directory in order to be able to develop on both computers when and if required.

Although i can see everything correctly and create files i cannot edit any files that were created on the other computer.

How can i bypass that?

---

### Post by stevoo on 2008-09-27
my smb.conf file....
> [Game]
comment = My online game
path = /var/www
available = yes
read only = no
browsable = yes
public = yes
writable = yes
create mask = 0775
directory mask = 0755

---

