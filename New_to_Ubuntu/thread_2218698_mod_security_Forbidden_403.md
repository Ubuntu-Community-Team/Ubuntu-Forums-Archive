---
title: "mod security Forbidden 403"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by Peter1981 on 2014-04-21
Hi

I installed mod security and I can`t reach my website.
If I try "mywebspace.no-ip.org/mywebsite.com" I get the message
If I try "mywebspace.no-ip.org/mywebsite.com/public_html" I can see the main page but I can`t reach the sub pages. I get the Message straight as I click on any menu.

Has anyone got this problem?

Thanks

---

### Post by Peter1981 on 2014-04-21
I have this problem if I instal the 2.2.5 version of mod security.
If I install the latest I get the next message
"Syntax error on line 52 of /etc/modsecurity/activated_rules/modsecurity_crs_20_protocol_violations.conf:
Error parsing actions: Unknown action: ver
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!"

What can I do with this error?

"

---

### Post by Habitual on 2014-04-21
You have the wrong CRS "set" installed, or perhaps try
```
sudo a2enmod mod-security; sudo /etc/init.d/apache2 restart 
``` and try the operation again?

---

### Post by Peter1981 on 2014-04-22
It`s the same
"Module mod-security already enabled"
And the error again

---

### Post by Peter1981 on 2014-04-22
It`s working now. I don`t know the answer but working. I again installed the v2.2.5 mod_security after the latest one (probably third times) and it is working now. How? Mystery I can browse any menu without "Forbidden" message.

---

### Post by Danger_Monkey on 2014-04-22
On mine, the /etc/apache2/sites-available/000-default.conf file had changed; the DocumentRoot pointed to /var/www/html after the upgrade.  I edited it to /var/www and it was able to "see" the web sites again.

---

### Post by Peter1981 on 2014-04-23
My one had not changed.
But still there is a small error. I have to write the whole route to access my website. Like this "mywebsite.no-ip.org/mywebsite.com/public_html". Has anyone got idea why I have to use the public_html at the end? It`s not a big problem but would be better if I shouldn`t write it at the end.
And another one. The PHP script doesn`t run. If I click on the submit button I still get the "Forbidden" message. But now there is not the "403" error code there.

---

### Post by Danger_Monkey on 2014-04-24
It sounds like the DocumentRoot has been changed relative to where the files really reside.  If you have to put in the whole path, it has probably moved back to /var/www when it should be /var/www/mywebsite.com/public_html.  I would check the virtual host in /etc/apache2/sites-enabled/<website_name> and make sure the path is correct.

---

