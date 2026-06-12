---
title: "help needed unable to upgrade postgresql"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by gav-the-lad on 2008-05-21
I just installed postgresql 8.2 only to find out it is obsolete. The message i received is:

[COLOR="Red"]"Obsolete major version 8.2                                                &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; The PostgreSQL version 8.2 is obsolete, but the server or client          &#9618; 
 &#9474; packages are still installed. Please install the latest packages          &#9618; 
 &#9474; (postgresql-8.3 and postgresql-client-8.3) and upgrade the existing       &#9618; 
 &#9474; clusters with pg_upgradecluster (see manpage).                            &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; Please be aware that the installation of postgresql-8.3 will              &#9618; 
 &#9474; automatically create a default cluster 8.3/main. If you want to upgrade   &#9618; 
 &#9474; the 8.2/main cluster, you need to remove the already existing 8.3         &#9618; 
 &#9474; cluster (pg_dropcluster --stop 8.3 main, see manpage for details).        &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; The old server and client packages are no longer supported. After the     &#9618; 
 &#9474; existing clusters are upgraded, the postgresql-8.2 and  postgresql-client-8.2 packages should be removed.                         &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; Please see /usr/share/doc/postgresql-common/README.Debian.gz for          &#9646; 
 &#9474; details."[/COLOR]

So i tried to upgrade by sudo apt-get install postgresql-8.3 but received an error message telling me to run "dpkg --configure -a" i did that, but this just leads me back to the original  postgresql 8.2 obsolete message.

Also just tried sudo apt-get update, and the last 2 lines read :

[COLOR="Blue"]"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"[/COLOR]

---

### Post by Monicker on 2008-05-21
I haven't touched postgres in ages, so I can't help there.  However, that last message is generated when more than one package manager is running.  Mulitple front ends cannot access the backend files at the same time.  Did you have Synaptic or the Update Manager up when you attempted to run apt when that message came up?

---

### Post by gav-the-lad on 2008-05-21
yeah i had them both running at the same time, still getting problems though. I now receive this error when trying to install postgresql 8.3 :


Setting up postgresql-common (87) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing postgresql-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql-8.3:
 postgresql-8.3 depends on postgresql-common (>= 79); however:
  Package postgresql-common is not configured yet.
dpkg: error processing postgresql-8.3 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-common
 postgresql-8.3
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

