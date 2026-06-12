---
title: "how to write in /var/www with a perl script"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by dersu on 2008-10-15
hi,
I try to create an html file from a perl script, but I cant!!
my script will read a data file from cgi-bin and then create an html file in /var/www. why I cant it with:

open PAGEIN, ">/$FORM_DATA{'subject'}.html";

or what is the paths to write files in /var/www and /usr/lib/cgi-bin in a perl script running on apache2.

Thanks.

---

### Post by cmnorton on 2008-10-15
What's the error? Our perl scripts are owned by root.

---

### Post by dersu on 2008-10-15
> **cmnorton said:**
> What's the error? Our perl scripts are owned by root.

the error is page not found in localhost/xxx.html on apache logs.

if the syntax of the code below is correct.
open PAGEIN, ">/$FORM_DATA{'subject'}.html";

I think its the owner of directories /var/www or /usr/lib/cgi-bin.

the owner of /var/www was www-data, I changed it to me as user.

should I change it to root?

---

### Post by cmnorton on 2008-10-16
If you have already changed the owner once, it probably cannot hurt to change to root, but owner www-data implies seems to indicate something else installed in /var/www. I've looked on a Red Hat system and my Kubuntu system and root owns /var/www and the files within. Those perl scripts that need write access to our Informix database are owned by root but their group is the database's user name.

---

