---
title: "Whois Lookup of .co domain"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by Kissell on 2013-05-09
I need to do a whois lookup of a .co domain from the command line.

I installed "whois" and can do lookups on .com domains and others, but I need to get it working with .co

Anyone know a server that will let me query .co domains?

---

### Post by haqking on 2013-05-09
> **Kissell said:**
> I need to do a whois lookup of a .co domain from the command line.

I installed "whois" and can do lookups on .com domains and others, but I need to get it working with .co

Anyone know a server that will let me query .co domains?

[http://whois.marcaria.com/domain-whois/south-america/Colombia-domain-CO/](http://whois.marcaria.com/domain-whois/south-america/Colombia-domain-CO/)

---

### Post by Kissell on 2013-05-09
Thanks, but that's a web interface.  

I need to be able to query the whois information from a bash script.

---

### Post by haqking on 2013-05-09
> **Kissell said:**
> Thanks, but that's a web interface.  

I need to be able to query the whois information from a bash script.

you may need to edit your whois.conf

[http://manpages.ubuntu.com/manpages/lucid/man1/whois.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/whois.1.html)

by default it uses networksoultions and ARIN via internic

ARIN doesnt list South and Latin America, there are 5 major registrars worldwide, APNIC, ARIN, RIPE NCC, Lacnic, and AFRINIC

You could add aliases to your bash profile to allow you do it from command line if you wanted to, allowing you to choose what whois server you wanted, there are many

Edit: here is a good link providing some good alisases for different servers [http://answers.oreilly.com/topic/408-how-to-use-and-understand-whois-in-its-many-forms/](http://answers.oreilly.com/topic/408-how-to-use-and-understand-whois-in-its-many-forms/)

---

### Post by Kissell on 2013-05-09
hmm...  it was a script issue...  I just took out the unnecessary explicit declaration of the whois server and everything works fine now.

---

### Post by haqking on 2013-05-09
> **Kissell said:**
> hmm...  it was a script issue...  I just took out the unnecessary explicit declaration of the whois server and everything works fine now.

that sounds about right, an explicit declaration will limit the results.

There are many whois servers speialising in different domains via the 5 different registrars.

Glad you got it sorted.

Peace

---

