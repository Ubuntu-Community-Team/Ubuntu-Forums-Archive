---
title: "MiniHowto: Make Postfix rewrite sender header on local mails"
date: 2005-05-31
forum: Outdated Tutorials &amp; Tips
---

### Post by infinito on 2005-05-31
This Mini-Howto describes howto make Postfix to send local emails with your preferred email addreass as the "sender" header.
This means that when you send mails using "mail" or mails automatically sended by root,you can get your email at the from field.
That's the way you get it:

(1) Create the /etc/postfix/sender_canonical, and add user -> email references like this:
```
$ sudo vi /etc/postfix/sender_canonical

infinito     infinito@hotmail.com
root         infinito@hotmail.com
```
(2) Create /etc/postfix/sender_canonical.db file
```
$ sudo postmap hash:/etc/postfix/sender_canonical
```
(3) Add sender_canonical variable to /etc/postfix/main.cf
```
postconf -e "sender_canonical_maps=hash:/etc/postfix/sender_canonical"
```
(4) Restart Postfix
```
$ sudo /etc/init.d/postfix restart
```
Hope this is useful for someone...

---

### Post by meyerm on 2005-06-26
[QUOTE=infinito]This Mini-Howto describes howto make Postfix to send local emails with your preferred email addreass as the "sender" header.
[/QUOTE]
 Hi infinito,

can you also describe, how postfix can rewrite mails depending on the used username at the SMTP AUTH? So f.ex. you must login at the server to send mails and when you login as "greatguy" all your emails get a "greatguy@company.com" FROM. A nice feature would also be when the mail body could be modified (appending some special signature), but that's not very important, just a nice feature.

Thank you very much!
Marcel

---

### Post by renardeau on 2011-01-12
This was exactly what I needed ! My ISP required a FQDN, and your little howto showed me how to give it just that

Thanks a lot

---

