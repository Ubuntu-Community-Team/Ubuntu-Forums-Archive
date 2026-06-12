---
title: "Active directory joining ( and the problem )"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Madvil on 2008-11-20
Hello all,

I am currently running a workstation with Ubuntu 8.10 in my office and I want it to become a part of the domain.
After update, I use sudo apt-get install likewise-open ( following the instructions here : [http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/) ) and then I try to domainjoin-cli but I get the following error : 

Resolving 'yourdomainname.local' failed. Check that the domain name is correctly
entered. Also check that your DNS server is reachable, and that your system is
configured to use DNS in nsswitch.

(I filtered the domain name in the error message of course.)

Can someone help me here? :(

---

### Post by Madvil on 2008-11-20
After I edited /etc/nsswitch.conf to accept wins on hosts, it tried to auth but then it requires Kerberos support from the DC.

:/

---

### Post by brown.hornet on 2008-12-13
Madvil -

Give this link a try - though this is for 8.04 I am sure that it will work with 8.10.  I was able to get both an 8.04 workstation and server into my Windows SBS 2003 domain.  The only issue I have now is that for some reason I can't browse to my network shares from my Ubunto workstation.  I am able to browse to and from all of my other systems.  Windows XP, SBS Server 2003, and my iMac.


[http://esthermofet.blogspot.com/2008/03/howto-ad-domain-authentication-in.html]("http://esthermofet.blogspot.com/2008/03/howto-ad-domain-authentication-in.html")

Respectfully -

BrnHornet

---

