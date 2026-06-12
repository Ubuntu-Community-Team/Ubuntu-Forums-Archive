---
title: "how to give in ubuntu"
date: 2007-09-06
forum: Programming Talk
---

### Post by munna_dude on 2007-09-06
hi all
let me explain about my problem

this is my querry in fedora forum
> 
i created a rpm for my application.
i am asking about, is there any way to write in spec file.....
at the time of installation give the permission to a file placed in /usr/lib/

how to give the permissions for that file in /usr/lib while installing the rpm.

for this, how to write in spec file.
please help me

thank you in advance


and the responce is
> 
Use the %attr directive in the %files section to set file ownership and permissions


this is worked fine for rpm...


my querry is 

how to give the file permissing while installing the .deb package.

please help me 

thank you in advance

---

### Post by slavik on 2007-09-06
post-install script. :)

---

### Post by munna_dude on 2007-09-07
> **slavik said:**
> post-install script. :)

sorry i am unable to get this..

can you please helpme..

thank you in advance

---

### Post by nanotube on 2007-09-07
> **munna_dude said:**
> sorry i am unable to get this..

can you please helpme..

thank you in advance

i use the epm package creator to make .debs - and there you specify directly in the .list file what ownership and permissions you want for all your files.

here's the link to the project site:
[http://www.easysw.com/epm/](http://www.easysw.com/epm/)

---

