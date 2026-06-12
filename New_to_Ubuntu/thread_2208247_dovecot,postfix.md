---
title: "dovecot,postfix"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by shad2 on 2014-02-27
do i have to make another certificate for dovecot or should i stick to these as they are in postfix'main.cf:
sudo postconf -e 'smtpd_tls_key_file = /etc/ssl/private/bal-laptopserver.key'
sudo postconf -e 'smtpd_tls_cert_file = /etc/ssl/certs/01.pem'
sudo postconf -e 'smtpd_tls_CAfile = /etc/ssl/certs/CAcertbal-laptop.pem'
in dovecot ifound these lines:
ssl_cert_file =  /etc/ssl/certs/dovecot.crt
ssl_key_file = /etc/ssl/private/dovecot.pem

iam using my own CA to get the postfix key and cert above.what should i put in the dovecot configuration ,can i use the same

---

