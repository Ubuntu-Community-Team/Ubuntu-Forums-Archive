---
title: "&quot;E: Unable to locate package&quot; error"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by metador88 on 2012-03-21
I am trying to install some packages and using this command:
```
sudo apt-get install libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4
```And here is the output I get: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libkadm5clnt-mit7
E: Unable to locate package libkadm5srv-mit7
E: Unable to locate package libkdb5-4

I searched for these packages and found them on this page:

[http://packages.debian.org/source/squeeze/krb5](http://packages.debian.org/source/squeeze/krb5)

How can I get them now?

---

### Post by tomopotamus on 2012-03-21
Maybe those packages are only available in the Debian repos.  I may be wrong though.

---

### Post by ksa618 on 2012-03-21
Maybe this can help:
[https://help.ubuntu.com/community/Kerberos]("https://help.ubuntu.com/community/Kerberos#Realm_Administration:_kadmin")

---

### Post by HiImTye on 2012-03-21
the packages in the Ubuntu repos are newer versions
```
tye@T:~$ aptitude search kadm
p   libheimdal-kadm5-perl                                                                             - Perl module to administer a Heimdal Kerberos KDC                                                           
p   libkadm5clnt-mit8                                                                                 - MIT Kerberos runtime libraries - Administration Clients                                                    
p   libkadm5clnt7-heimdal                                                                             - Heimdal Kerberos - kadmin client library                                                                   
p   libkadm5srv-mit8                                                                                  - MIT Kerberos runtime libraries - KDC and Admin Server                                                      
p   libkadm5srv8-heimdal                                                                              - Libraries for Heimdal Kerberos                                                                             
tye@T:~$ aptitude search kdb
p   kdbg                                                                                              - graphical debugger interface                                                                               
p   libdevel-ptkdb-perl                                                                               - Perl debugger using a Tk GUI                                                                               
p   libkdb5-5                                                                                         - MIT Kerberos runtime libraries - Kerberos database                                                         
tye@T:~$ 
```

---

### Post by 2F4U on 2012-03-21
It may be easier to tell us what you intend to achieve. Additionally, what mirrors are you using? I assume that you got the package names from a tutorial, but was this a tutorial based on Ubuntu? Package names can differ between Linux distributions.

---

### Post by metador88 on 2012-03-21
Hi. I am following a tutorial and I have to install a lot of packages but only these three make a problem.

---

### Post by metador88 on 2012-03-21
> **HiImTye said:**
> the packages in the Ubuntu repos are newer versions
```
tye@T:~$ aptitude search kadm
p   libheimdal-kadm5-perl                                                                             - Perl module to administer a Heimdal Kerberos KDC                                                           
p   libkadm5clnt-mit8                                                                                 - MIT Kerberos runtime libraries - Administration Clients                                                    
p   libkadm5clnt7-heimdal                                                                             - Heimdal Kerberos - kadmin client library                                                                   
p   libkadm5srv-mit8                                                                                  - MIT Kerberos runtime libraries - KDC and Admin Server                                                      
p   libkadm5srv8-heimdal                                                                              - Libraries for Heimdal Kerberos                                                                             
tye@T:~$ aptitude search kdb
p   kdbg                                                                                              - graphical debugger interface                                                                               
p   libdevel-ptkdb-perl                                                                               - Perl debugger using a Tk GUI                                                                               
p   libkdb5-5                                                                                         - MIT Kerberos runtime libraries - Kerberos database                                                         
tye@T:~$ 
```
i am installing the newer versions as you indicated and will try if things work with them. thanks

---

