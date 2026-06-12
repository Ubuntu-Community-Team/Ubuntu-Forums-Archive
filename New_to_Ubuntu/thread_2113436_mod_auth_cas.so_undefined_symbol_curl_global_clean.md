---
title: "mod_auth_cas.so: undefined symbol: curl_global_cleanup"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by Twinbird on 2013-02-07
I have recently gone through instructions on how to set up CAS authentication.
Some of the instructions are found here: [https://source.jasig.org/cas-clients/mod_auth_cas/trunk/README](https://source.jasig.org/cas-clients/mod_auth_cas/trunk/README)

I have a couple of errors going through the steps in the link above. When I go to start my Apache2 server again, I get the following error:
> 
rkomarom@rsg-pc102:/home/rkomaromi$ sudo service apache2 start
[sudo] password for rkomarom: 
 * Starting web server apache2                                                  apache2: Syntax error on line 214 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Cannot load /usr/lib/apache2/modules/mod_auth_cas.so into server: /usr/lib/apache2/modules/mod_auth_cas.so: undefined symbol: curl_global_cleanup
Action 'start' failed.
The Apache error log may have more information.
                                                                         [fail]
rkomarom@rsg-pc102:/home/rkomaromi$ 
I note from the installation that I need to perform the following command:
> 
Use the standard commands below to compile and install: ./configure; make; make installWhen doing this, I receive the following error:
> In file included from mod_auth_cas_test.c:16:0:
../src/mod_auth_cas.h:205:26: error: unknown type name ‘CRYPTO_THREADID’I could not find a solution to this error. Please let me know what I can do.

Thanks!
:D

I am running Ubuntu 12.04 (Precise)

---

