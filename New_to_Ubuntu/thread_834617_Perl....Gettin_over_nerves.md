---
title: "Perl....Gettin over nerves"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by harsh_ on 2008-06-19
I have a script to reboot router in perl given by a friend...but canno execute it...got sum replies like

using perl router.pl
(router.pl is tye file that i want to execite)
did chmod, moved it to /usr/bin/ and then fired it, as
router.pl
./router.pl
perl router.pl
 but all in vain.. Plz guys plz help me out

---

### Post by harsh_ on 2008-06-19
Also executing perl router.pl gives me this error
Can't locate Net/Telnet.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at router.pl line 6.
BEGIN failed--compilation aborted at router.pl line 6.

---

### Post by tr333 on 2008-07-05
```
sudo apt-get install libnet-telnet-perl
```

---

