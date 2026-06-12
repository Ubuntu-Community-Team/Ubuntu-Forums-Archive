---
title: "Ubuntu FreeRadius Permission Denied"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by hoffmeyer4 on 2012-02-14
I am trying to set up CoovaChilli on Ubuntu Server 9.04. When I get to the step:
mysql -u root -p radius < /etc/freeradius/sql/mysql/schema.sql
I get "Permssion Denied" for the schema.sql file. I believe that it is a permission issue for that file, because when I change to that directory, I get Permssion Denied if I try to do a "dir". If I use the "sudo dir" it works. How can I get permssion to use the file, or is it something else? My background is in Windows servers, so this is my first Ubuntu experience. I will be glad to read any documentation, but I could not find an answer to this through Google. I thank you for any answers.

---

### Post by MG&amp;TL on 2012-02-14
Does 

```
sudo mysql -u root -p radius < /etc/freeradius/sql/mysql/schema.sql
```

work?

You probably don't need to (and shouldn't) take ownership of that file, but you might get some joy with chown (change ownership).

See:

```
man chown
```

for details.

Incidentally, while "dir" works, "ls" is 'more Linux'.

---

### Post by hoffmeyer4 on 2012-02-14
Thanks!  The sudo, did not work, but your response did get me to thinking.  I checked the owner of the files, and saw that they were owned by root.  I logged in as root, and retried the command, and it works perfect.
Thank you for the tip.

---

### Post by MG&amp;TL on 2012-02-14
> **hoffmeyer4 said:**
> Thanks!  The sudo, did not work, but your response did get me to thinking.  I checked the owner of the files, and saw that they were owned by root.  I logged in as root, and retried the command, and it works perfect.
Thank you for the tip.

No problem, hope you enjoy your sql. :)

Can you show others your problem is solved by marking it solved, under 'thread tools' at the top. Thanks.

---

