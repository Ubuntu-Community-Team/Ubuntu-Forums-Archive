---
title: "Continuing internet woes..."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by kneewax on 2008-05-31
I have been suffering from slow web browsing since migrating to Ubuntu back in March.  At first I put it down to documented Firefox 2.0 issues,  I tried all the usual fixes (IPv6 etc) to no avail.  So I was hoping going to Hardy and FF3 would solve it, but the rendering of pages is still very slow. 

I tried other browsers including Epiphany, opera and FF derivatives like Swiftfox.  All are as slow, and Opera was even worse taking over 90 seconds to display just the favicon and simply not displaying the page at all.

I am fast facing the fact that there is something fundamentally wrong with the way Ubuntu is trying access the outside world.  Trouble is I don't know where to start with Linux.  

The Vista box on the same network has no problems so I am fairly certain it is a machine specific problem.

Can anyone help me check out my current settings.

cheers

---

### Post by superprash2003 on 2008-05-31
have you tried changing dns servers to opendns? their ips are  208.67.222.222 and 208.67.220.220

---

### Post by kneewax on 2008-05-31
Interesting, I'll try those.  I had put my ISP DNS in the seetings, but when I went to add the ones you suggested my settings were no longer there....

I'll try the Open DNS settings and let you know.  Congrats on the 1000th post by the way :-)

---

### Post by kneewax on 2008-05-31
OK, I tried this - for some reason my Network settings are not remembering the DNS servers when I reboot.  Should I try entering these in a hosts file somewhere?

---

### Post by superprash2003 on 2008-05-31
follow this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by kneewax on 2008-05-31
Brilliant Thanks!   Works a treat.

---

### Post by Tomatz on 2008-05-31
> **kneewax said:**
> I have been suffering from slow web browsing since migrating to Ubuntu back in March.  At first I put it down to documented Firefox 2.0 issues,  I tried all the usual fixes (IPv6 etc) to no avail.  So I was hoping going to Hardy and FF3 would solve it, but the rendering of pages is still very slow. 

I tried other browsers including Epiphany, opera and FF derivatives like Swiftfox.  All are as slow, and Opera was even worse taking over 90 seconds to display just the favicon and simply not displaying the page at all.

I am fast facing the fact that there is something fundamentally wrong with the way Ubuntu is trying access the outside world.  Trouble is I don't know where to start with Linux.  

The Vista box on the same network has no problems so I am fairly certain it is a machine specific problem.

Can anyone help me check out my current settings.

cheers
eeeeeeeeeedddddddddddddddddiiiiiiiiiiiiiiiiiiittttttttttttttttttttttttttttttttttttttttttttttttttttttttttt

---

### Post by Tomatz on 2008-05-31
> **superprash2003 said:**
> follow this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Nice tip ;)

---

