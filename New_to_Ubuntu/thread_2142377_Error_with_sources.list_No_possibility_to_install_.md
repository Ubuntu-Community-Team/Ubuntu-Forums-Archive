---
title: "Error with sources.list/ No possibility to install software"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by uzh00 on 2013-05-05
Hey everybody!!!! 

It's my first post and I'm looking very forward to use this forum! I started using vm with Ubuntu 12.04 LTS Sever. I tried to install postgresql, but unfortunately it's not possible. I want to install OpenErp 7. 

Aftetr typing ```
sudo apt-get install postgresql-9.1
``` I get following error:


Paketlisten werden gelesen... Fertig
AbhÃ¤ngigkeitsbaum wird aufgebaut
Statusinformationen werden eingelesen... Fertig
Die folgenden zusÃ¤tzlichen Pakete werden installiert:
  libpq5 postgresql-client-9.1 postgresql-client-common postgresql-common ssl-cert
Vorgeschlagene Pakete:
  oidentd ident-server locales-all postgresql-doc-9.1 openssl-blacklist
Die folgenden NEUEN Pakete werden installiert:
  libpq5 postgresql-9.1 postgresql-client-9.1 postgresql-client-common postgresql-common ssl-cert
0 aktualisiert, 6 neu installiert, 0 zu entfernen und 77 nicht aktualisiert.
Es mÃ¼ssen 5'491 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 15.6 MB Plattenplatz zusÃ¤tzlich benutzt.
MÃ¶chten Sie fortfahren [J/n]?

```
J
```
 
 

> Fehl [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) precise-updates/main libpq5 amd64 9.1.9-0ubuntu12.04
  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»ch.archive.ubuntu.comÂ«
Fehl [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) precise-updates/main postgresql-client-common all 129ubuntu1
  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»ch.archive.ubuntu.comÂ«
Fehl [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) precise-updates/main ssl-cert all 1.0.28ubuntu0.1
  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»ch.archive.ubuntu.comÂ«
Fehl [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) precise-updates/main postgresql-common all 129ubuntu1
  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»ch.archive.ubuntu.comÂ«
Fehl [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libpq5 amd64 9.1.9-0ubuntu12.04
  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»security.ubuntu.comÂ«
Fehl [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main postgresql-client-9.1 amd64 9.1.9-0ubuntu12.04
  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»security.ubuntu.comÂ«
Fehl [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main postgresql-9.1 amd64 9.1.9-0ubuntu12.04
  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»security.ubuntu.comÂ«
Fehlschlag beim Holen von [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq5_9.1.9-0ubuntu12.04_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/libpq5_9.1.9-0ubuntu12.04_amd64.deb)  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»security.ubuntu.comÂ«
Fehlschlag beim Holen von [http://ch.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/postgresql-client-common_129ubuntu1_all.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/postgresql-client-common_129ubuntu1_all.deb)  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»ch.archive.ubuntu.comÂ«
Fehlschlag beim Holen von [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/postgresql-client-9.1_9.1.9-0ubuntu12.04_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/postgresql-client-9.1_9.1.9-0ubuntu12.04_amd64.deb)  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»security.ubuntu.comÂ«
Fehlschlag beim Holen von [http://ch.archive.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.28ubuntu0.1_all.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.28ubuntu0.1_all.deb)  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»ch.archive.ubuntu.comÂ«
Fehlschlag beim Holen von [http://ch.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/postgresql-common_129ubuntu1_all.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-common/postgresql-common_129ubuntu1_all.deb)  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»ch.archive.ubuntu.comÂ«
Fehlschlag beim Holen von [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/postgresql-9.1_9.1.9-0ubuntu12.04_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-9.1/postgresql-9.1_9.1.9-0ubuntu12.04_amd64.deb)  TemporÃ¤rer Fehlschlag beim AuflÃ¶sen von Â»security.ubuntu.comÂ«
E:  Einige Archive konnten nicht heruntergeladen werden; vielleicht  Â»apt-get updateÂ« ausfÃ¼hren oder mit Â»--fix-missingÂ« probieren?
root@vm0180:~#


```
sudo apt-get install --fix-missing
``` doesn't solve the problem. 

I tried to change the ".ch" with ```
[FONT=Calibri]sudo nano /etc/apt/sources.list
[/FONT]

``` to ".us" and ".de" and also deleted it. but it's not installing. 

If you know what the problem is, please help me to get the software installed....

Thanks a lot!

---

