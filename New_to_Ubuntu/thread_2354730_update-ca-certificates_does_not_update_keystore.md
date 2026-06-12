---
title: "update-ca-certificates does not update keystore"
date: 2017-03-05
forum: New to Ubuntu
---

### Post by subtlecinema on 2017-03-05
This is on 16.04 server.  Each time I run the update-ca-certificates, I receive:  *updates of cacerts keystore disabled.*

I am trying to validate a certificate, and I receive a request for my company's root certificate, which I've already added.  I'm concerned that even though the key makes it's way into */etc/ssl/certs/ca-certificates.crt*,it's somehow still not able to validate because of the above message in blue?  Why else would I be receiving so many SSL errors, and using an openssl inspect I find it asking for the root ca I can see sitting right there?

---

### Post by marchello_lippi2 on 2017-03-15
Hi, 

Please try >  sudo dpkg-reconfigure ca-certificates and show the output.

---

### Post by dbaron on 2017-10-02
This message comes from the file /etc/ca-certificates/update.d/jks-keystore, and in my case it was happening because the file /usr/share/ca-certificates-java/ca-certificates-java.jar doesn't exist.  I think it was because I'd previously *removed* ca-certificates-java, but hadn't *purged* it.  I think doing 'sudo apt purge ca-certificates-java' fixed it.

---

