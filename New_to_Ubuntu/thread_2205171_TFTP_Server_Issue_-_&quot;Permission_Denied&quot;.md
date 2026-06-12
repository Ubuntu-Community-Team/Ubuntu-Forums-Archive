---
title: "TFTP Server Issue - &quot;Permission Denied&quot;"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by pete15 on 2014-02-12
Hi guys,

I'm having problems with a TFTP server I set up on my Ubuntu box.

I installed tftp using this link [http://askubuntu.com/questions/201505/how-do-i-install-and-run-a-tftp-server](http://askubuntu.com/questions/201505/how-do-i-install-and-run-a-tftp-server) 

Install went well, however, trying to tftp to this box constantly results in a Permission Denied (16739). To give further context, I am copying a config file from a Cisco switch (I have also tried this by creating a file in the tftpboot so that the copy can overwrite without success). My more experienced colleague believes this might have something to do with anonymous access to the tftp service, but was a little hazy on any further details!

Any suggestions would be very much appreciated.

Thank you.

---

### Post by Lars Noodén on 2014-02-12
If you're only going to be serving one file now and not regularly, you might not want to spend time on xinetd and such.  If you uninstall tftpd and install tftpd-hpa, then all you need to do is place your file in /var/lib/tftpboot/ and you're set.  

tftpd-hpa is managed via upstart like other services.  So you can turn it on and off easily.  

Also be sure to open the right port in the firewall.

```

sudo ufw allow tftp

```

---

### Post by pete15 on 2014-02-12
Thanks Lars. I am expecting to use the tftp service quite frequently (if that makes any difference).

---

