---
title: "Understandable Guide for CUPS with LDAP"
date: 2019-06-17
forum: New to Ubuntu
---

### Post by artim96 on 2019-06-17
Hi,
we have a CUPS server and I would like to connect it to our LDAP Server so only people with an account in our system can print.
Now, as far as I saw, you need Kerberos to do that, there doesn't seem to be a way without. So I installed it with 
```
apt-get install krb5-kdc krb5-admin-server
```
In the setup, the realm was correctly detected, as admin server I set the server where LDAP is installed, the other server that must be set (don't remember how it was called) to the server where CUPS and Kerberos are installed. That resulted in errors. The most detailed error descriptions I got with journalctl -xe:
> -- Unit krb5-kdc.service has begun starting up.Jun 17 13:22:48 ts krb5kdc[25176]: Cannot open DB2 database '/var/lib/krb5kdc/p
Jun 17 13:22:48 ts krb5kdc[25176]: krb5kdc: Realm *xxx.de* kann nic
Jun 17 13:22:48 ts systemd[1]: krb5-kdc.service: Control process exited, code=e
Jun 17 13:22:48 ts systemd[1]: Failed to start Kerberos 5 Key Distribution Cent
-- Subject: Unit krb5-kdc.service has failed
> -- Unit krb5-kdc.service has begun starting up.Jun 17 13:22:48 ts krb5kdc[25176]: Cannot open DB2 database '/var/lib/krb5kdc/principal': Datei oder Verzeichnis nicht gefunden - beim Initialisieren der Datenbank für Realm *xx*
Jun 17 13:22:48 ts krb5kdc[25176]: krb5kdc: Realm *xxx*.DE kann nicht initialisiert werden - Einzelheiten finden Sie in der Protokolldatei
Jun 17 13:22:48 ts systemd[1]: krb5-kdc.service: Control process exited, code=exited status=1
Jun 17 13:22:48 ts systemd[1]: Failed to start Kerberos 5 Key Distribution Center.
-- Subject: Unit krb5-kdc.service has failed
and
> -- Unit krb5-kdc.service has begun starting up.Jun 17 13:22:48 ts krb5kdc[25176]: Cannot open DB2 database '/var/lib/krb5kdc/principal': Datei oder Verzeichnis nicht gefunden - beim Initialisieren der Datenbank für Realm *xx*
Jun 17 13:22:48 ts krb5kdc[25176]: krb5kdc: Realm *xxx*.DE kann nicht initialisiert werden - Einzelheiten finden Sie in der Protokolldatei
Jun 17 13:22:48 ts systemd[1]: krb5-kdc.service: Control process exited, code=exited status=1
Jun 17 13:22:48 ts systemd[1]: Failed to start Kerberos 5 Key Distribution Center.
-- Subject: Unit krb5-kdc.service has failed
(replacing the realm with xxx and sometimes only xx is intentional, the latter when something was cut-off)
Even enabling the service (it was disabled first for some reason) and starting it didn't help. So I removed the packages and tried using a different manual. So this time I installed with
```
apt-get remove krb5-{admin-server,kdc}
```
but probably since the configuration dialog already run and I wasn't able to remove all its files it didn't came up another time. Even removing the kbr5.conf file and the krb5kdc folder and installing again didn't help.

So does anybody have an understandable guide for me how to connect the CUPS server and our LDAP server, maybe even without Kerberos? Googling I just found either the same guide that didn't work or a lot of guides for samba....the only Windows machines we have in our system are the computers that are supposed to print through the CUPS server so I don't think that should be relevant.

---

