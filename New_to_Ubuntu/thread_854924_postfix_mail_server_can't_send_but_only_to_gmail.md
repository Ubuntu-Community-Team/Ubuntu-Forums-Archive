---
title: "postfix mail server can't send but only to gmail"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by richardd2137 on 2008-07-09
Hello, I have a problem, I have a Ubuntu server set up with postfix, This is the weirdest thing, I can send mail to gmail but not to any other provider. I need some help, i can receive from the other providers but can't send to the other providers. I'll post  my postfix configuration if any one needs it, Please help. any answers will be use full. Also this may not be in the right category but i need help a.s.a.p, thanks

---

### Post by kool_kat_os on 2008-07-09
Is your ip address blacklisted?

---

### Post by kool_kat_os on 2008-07-09
check here :
[http://whatismyipaddress.com/staticpages/index.php/is-my-ip-address-blacklisted](http://whatismyipaddress.com/staticpages/index.php/is-my-ip-address-blacklisted)

---

### Post by llamakc on 2008-07-09
Post the output of `postconf -n` and hide any of the juicy tidbits you don't want to share with XXX's. Also give information on your network setup. Are you behind a router? Exposed directly to the internet?

kool probably is on the right path.

---

