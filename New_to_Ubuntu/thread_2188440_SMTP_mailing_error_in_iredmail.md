---
title: "SMTP mailing error in iredmail"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by salmendar on 2013-11-17
Nov xx xx:xx:xx www roundcube: SMTP Error: SMTP error: Failed to add recipient 'xxxxx@xxxxxxxx.net' in /usr/share/apache2/roundcubemail-0.9.2/program/include/rcmail.php on line 1014 (POST /mail/?_unlock=loadingxxxxxxxxxxxxxx&_lang=undefined?_task=mail&_action=send)



i am completely new to mailing information and this also gives error in browser which is error #451.


please help

---

### Post by salmendar on 2013-11-18
the soultion was simple.... i had to go and edit the postfix to direct the smtpd_sasl_local_domain = [www.mydomain.com](www.mydomain.com)

---

