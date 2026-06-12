---
title: "Can't recieve e-mails and mx loop detected error"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by noahmetz1 on 2014-01-08
Hello, I am trying to setup a email server at home, with postfix, but I can't receive emails. I can send emails just fine and when i use the mx lookup tool on [http://mxtoolbox.com/](http://mxtoolbox.com/) it says Loop detected! I am using a self-hosted domain bought from [http://namecheap.com](http://namecheap.com) and it works fine for hosting websites and gameservers. If it helps here is my main.cf from postfix (I can uncensor the domain if needed)
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version



# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = no


# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.domain.com, ubuntu, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all



```

And this is my zone file, the IP and domain are censored, If I did anything wrong please help me fix it
```

; BIND data file for domain.com
;
$TTL 14400
@ IN SOA ns1.domaincom. host.domaincom. (
201006601 ; Serial
7200 ; Refresh
120 ; Retry
2419200 ; Expire
604800) ; Default TTL
;
domain.com.    IN    NS    ns1.domain.com.
domain.com.    IN    NS    ns2.domain.com.


mail        IN    A    domain.com


@    43200    IN    MX    10    mail.domain.com.


domain.com.    IN    A    xxx.xxx.xxx.xxx
 
ns1        IN    A    xxx.xxx.xxx.xxx
ns2        IN    A    xxx.xxx.xxx.xxx


www        IN    CNAME    domain.com.
ftp        IN    CNAME    domain.com.
play        IN    A    xxx.xxx.xxx.xxx



```

Thanks in advance if anyone can help me get this working!

---

