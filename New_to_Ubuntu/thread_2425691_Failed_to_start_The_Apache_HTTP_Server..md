---
title: "Failed to start The Apache HTTP Server."
date: 2019-08-28
forum: New to Ubuntu
---

### Post by pierre232 on 2019-08-28
i ran this command "sudo systemctl status apache2" 
and it gave me this output
 ```
"apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: failed (Result: exit-code) since Tue 2019-08-27 00:30:28 WAT; 8min ag
  Process: 924 ExecStart=/usr/sbin/apachectl start (code=exited, status=127)

Aug 27 00:30:26 thebrains-AMILO-Li3710 systemd[1]: Starting The Apache HTTP Serv
Aug 27 00:30:28 thebrains-AMILO-Li3710 apachectl[924]: /usr/sbin/apachectl: 174:
Aug 27 00:30:28 thebrains-AMILO-Li3710 apachectl[924]: Action 'start' failed.
Aug 27 00:30:28 thebrains-AMILO-Li3710 apachectl[924]: The Apache error log may 
Aug 27 00:30:28 thebrains-AMILO-Li3710 systemd[1]: apache2.service: Control proc
Aug 27 00:30:28 thebrains-AMILO-Li3710 systemd[1]: apache2.service: Failed with 
Aug 27 00:30:28 thebrains-AMILO-Li3710 systemd[1]: Failed to start The Apache HT
lines 1-14/14 (END)...skipping...
&#9679; apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: failed (Result: exit-code) since Tue 2019-08-27 00:30:28 WAT; 8min ago
  Process: 924 ExecStart=/usr/sbin/apachectl start (code=exited, status=127)

Aug 27 00:30:26 thebrains-AMILO-Li3710 systemd[1]: Starting The Apache HTTP Server...
Aug 27 00:30:28 thebrains-AMILO-Li3710 apachectl[924]: /usr/sbin/apachectl: 174: /usr/sbin/apachectl: /usr/sbin/apache2: not found
Aug 27 00:30:28 thebrains-AMILO-Li3710 apachectl[924]: Action 'start' failed.
Aug 27 00:30:28 thebrains-AMILO-Li3710 apachectl[924]: The Apache error log may have more information.
Aug 27 00:30:28 thebrains-AMILO-Li3710 systemd[1]: apache2.service: Control process exited, code=exited status=127
Aug 27 00:30:28 thebrains-AMILO-Li3710 systemd[1]: apache2.service: Failed with result 'exit-code'.
Aug 27 00:30:28 thebrains-AMILO-Li3710 systemd[1]: Failed to start The Apache HTTP Server.

```
"
Anyone with solution please help.
thanks in advance :popcorn::p):Pand best regards.

---

### Post by wildmanne39 on 2019-08-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by SeijiSensei on 2019-08-29
> /usr/sbin/apachectl: 174: /usr/sbin/apachectl: /usr/sbin/apache2: not found

You're missing the binary for the web server.

Might I suggest a complete purge and reinstallation?

---

