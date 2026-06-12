---
title: "CheckGmail: how do i add another address to be checked"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by IsraeliHawk on 2008-11-08
hi all, 

how do i add in checkGmail another address to be checked besides by [email]blank@gmail.com[/email]? 

i have another "gmail type" address for the University named [email]blank@mail.huji.ac.il[/email]. in the site, the developers said this: 
> CheckGmail Can be run in multiple instances to check different mail accounts
Use the -profile=[profile name] command-line switch to set up a new account

now that's lovely, but i have no idea where to start..

any ideas? :confused:

thanks in advance..

---

### Post by king.pest on 2008-11-08
hi IsraeliHawk, 

you can run many instances of checkgmail with multiple profiles from the command line, just type in something like:```
checkgmail -profile=hujiacil
```which will start another instance of the program with empty settings. then you can for example add such sommand to your startup programs in GNOME, Xfce, KDE or whatever you use. 

cheers!

---

