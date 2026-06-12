---
title: "Help with SNMP &amp; MRTG Setup"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by 11Bravo on 2008-06-08
Awesome forum here!!! SOOOOOOOOO Much great information!

I'm struggling here trying to setup MRTG. Ok, I'm trying to use lighttpd instead of Apache. First I did:
#aptitude install snmp snmpd mrtg lighttpd

Then checked it with
#snmpwalk -v 2c -c public localhost system

I get 'Timeout: No Response from localhost'

Looked in /etc/snmp and there is no snmpd.conf, only snmpd.conf-old.

I found snmpd.conf and it is under /var/lib/snmp/snmpd.conf

I tried:
#sudo cp snmpd.conf /etc/snmp
'cp: cannot stat snmpd.conf: No such file or directory'

I'm kinda stuck at this point, why the snmpd.conf file is being such a PITA...Any ideas???

Thanks

---

### Post by kakka256 on 2008-06-09
Im no Net-SNMP expert but as far as i know, the snmpd.conf you found under /var/lib/snmp/snmpd.conf is not for you to edit. Leave that one alone and do not edit it. 

You can use the snmpconf script file when configurating you snmp setup, that might be easier. 

The Net-SNMP homepage has useful information for you (e.g. [http://www.net-snmp.org/docs/readmefiles.html](http://www.net-snmp.org/docs/readmefiles.html))
There are also tutorials etc. You should check them out (e.g.  [http://www.net-snmp.org/tutorial/tutorial-5/](http://www.net-snmp.org/tutorial/tutorial-5/))

Perhaps that will help you on your way.

---

