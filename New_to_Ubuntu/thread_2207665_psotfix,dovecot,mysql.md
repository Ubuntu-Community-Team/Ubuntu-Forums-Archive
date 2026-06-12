---
title: "psotfix,dovecot,mysql"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by shad2 on 2014-02-24
how can i configure postfix.i have made my own CA and am able to sign certificates,but I am puzzled as to what i should enter here:   sudo postconf -e 'smtpd_tls_key_file = '
sudo postconf -e 'smtpd_tls_cert_file = '

the path to CA root key file and CA certificate file  respectively or the path to the new certificate i have just signed ?

Also when it comes to configuring dovecot there are some "ssl_file_key=" parameters that i need to enter,do i have to make another certificate for dovecot
too,or can i just use the main CA certificate and its  key?

---

