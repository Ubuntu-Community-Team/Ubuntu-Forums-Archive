---
title: "While migrate the OpenLDAP and OpenSSL"
date: 2023-12-06
forum: New to Ubuntu
---

### Post by maria80e on 2023-12-06
[COLOR=#0C0D0E][FONT=-apple-system]While upgrading Openssl(1.1.1k) & openLDAP (2.4.47) to the version Openssl(3.0.10) & OpenLDAP(2.5.16) in windows server 2016 & 2019,[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I am getting an error which is posted below[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]**Note:** Verified that the certificates are valid. The client communicates with the LDAP server using TLS protocol version 1.2. We are using Windows API to connect the LDAP server.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]**Error Log:**[/FONT][/COLOR]
TLS trace: SSL_accept:before SSL initialization
TLS trace: SSL_accept:SSLv3/TLS read client hello
TLS trace: SSL_accept:SSLv3/TLS write server hello
TLS trace: SSL_accept:SSLv3/TLS write certificate
TLS trace: SSL_accept:SSLv3/TLS write key exchange
TLS trace: SSL_accept:SSLv3/TLS write certificate request
tls_write: want=1800, written=1800
TLS trace: SSL_accept:SSLv3/TLS write server done
tls_read: want=5 error=Unknown error
TLS trace: SSL_accept:error in SSLv3/TLS write server done
daemon: activity on 1 descriptor
daemon: waked
daemon: WSselect: listen=2 active_threads=0 tvp=NULL
daemon: activity on 4 descriptors
daemon: activity on:656830b0.2bc5f387 000027C0  3r656830b0.2bc7812f 000027C0
daemon: read activity on 3
daemon: WSselect: listen=2 active_threads=0 tvp=NULL
connection_get(3)
connection_get(3): got connid=1000
connection_read(3): checking for input on id=1000
tls_read: want=5, got=0
TLS trace: SSL_accept:error in SSLv3/TLS write server done
TLS: can't accept: (unknown).
connection_read(3): TLS accept failure error=-1 id=1000, closing
connection_closing: readying conn=1000 sd=3 for close
daemon: activity on 1 descriptor
daemon: waked
daemon: WSselect: listen=2 active_threads=0 tvp=NULL
connection_close: conn=1000 sd=3
daemon: removing 3
conn=1000 fd=3 closed (TLS negotiation failure)

[FONT=-apple-system]**Open LDAP 2.5.16 configuration**[/FONT]

./configure --prefix=/d/openldap-2.5.16/openldap_install --build=i686-w64-mingw32 --host=i686-w64-mingw32 \
    
      --enable-spasswd \
      --with-cyrus-sasl \
      --with-tls=openssl \
      --enable-rwm \
      --enable-auditlog \
      --enable-static \
      --libexecdir=/d/openldap-2.5.16/openldap_install/bin \
      --libdir=/d/openldap-2.5.16/deps/lib \
      --includedir=/d/openldap-2.5.16/deps/includeEnable Ginger*Cannot connect to Ginger* Check your internet connection
 or reload the browserDisable in this text fieldRephraseRephrase current sentenceEdit in Ginger×Enable Ginger*Cannot connect to Ginger* Check your internet connection
 or reload the browserDisable in this text fieldRephraseRephrase current sentenceEdit in Ginger×

---

### Post by MAFoElffen on 2023-12-06
You just mention Win Server 2k16 & 2k19... From what you posted so far, this is all purely Windows Server related. 

How does Ubuntu fit into this? Where is anything Ubuntu related in your infrastructure? I assume that is 'somewhere' or you would be here trying to get answers, right? 

You did not mention any of that. I believe that information might be useful.

---

