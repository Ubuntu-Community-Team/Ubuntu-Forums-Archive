---
title: "Checking mail in terminal"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by joetait on 2012-05-07
Hi

I want to try and use nothing but the terminal for about a week or so, as a small test of proficiency (and also the lack of youtube should increase my work output). I wondered if anyone knew if there was anyway to check email in the terminal, other than potentially in browser (eg links).

Thanks in advance :)

---

### Post by billyseth on 2012-05-07
though I've never used it, I have always heard good things about mutt

[http://www.mutt.org/](http://www.mutt.org/)

---

### Post by jerome1232 on 2012-05-07
I like to use mutt, it can connect to pop3 or imap accounts easily.

---

### Post by joetait on 2012-05-07
> **billyseth said:**
> though I've never used it, I have always heard good things about mutt

[http://www.mutt.org/](http://www.mutt.org/)


Looks great, thanks very much :)

---

### Post by Derek Karpinski on 2012-05-07
A guide with gmail and mutt

[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

---

### Post by jerome1232 on 2012-05-07
Wow, that's overly complicated.

Just set this in your .muttrc

```
set imap_user = "username@gmail.com"
set imap_pass = "password"

set smtp_url = "smtp://username@smtp.gmail.com:587/"
set smtp_pass = "password"
set from = "username@gmail.com"
set realname = "Your Real Name"

set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed="+[Gmail]/Drafts"

set header_cache=~/.mutt/cache/headers
set message_cachedir=~/.mutt/cache/bodies
set certificate_file=~/.mutt/certificates

set move = no

```

---

### Post by andrew.46 on 2012-07-01
> **jerome1232 said:**
> Wow, that's overly complicated.

Ouch :). Once this guide is setup no further modification is required, and [something very similar]("http://www.andrews-corner.org/mutt.html") has served me for many years. Of course the setup for imap is a lot simpler and I know many have gravitated to this rather than POP3 over SSL. Perhaps I am slowly becoming a dinosaur :(.

---

