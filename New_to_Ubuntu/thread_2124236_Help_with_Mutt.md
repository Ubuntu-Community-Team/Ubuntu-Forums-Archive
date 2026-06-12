---
title: "Help with Mutt"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2013-03-10
Hey, I've decided to give mutt a go, seeing as it's spoken of so highly. 

I'm struggling a little to get it up and running. I've read the wiki page but it doesn't state specifics, more a run over about how it should work. (at least that's what I got from it)

I created ~/.muttrc 
added 
```
set my_user=myuser@hotmail.com
set my_pass='password'
set mbox_type=Maildir
set folder=$home/mail
set spoolfile=+/
set header_cache=~/.hcache
set smtp_url=smtps://username@smtp.live.com
set smtp_pass=password
set realname=
set ssl_force_tls = yes


```

which I got from online. then open mutt. I'm promted with '/mail does not exist,  create it?' which I say yes, and responded with '/mail// : no such file or directory (errno =2)' then as would expect - no mail box is open. 

Assuming that the input in the .muttrc is correct. Do I just manually create a /mail folder within .muttrc? if so, how does mutt locate it, does it do that automatically or do I have to?

I've also found a few articles about mutt, from the comments - they are great for beginners - but they fail to load after the first page, so if anyone knows one which is up and running - appreciated. 


Cheers.

---

### Post by schragge on 2013-03-17
Try
```

set my_user=myuser@hotmail.com
set my_pass='password'
set mbox_type=Maildir
set folder=$home/mail
set spoolfile=+/
set header_cache=~/.hcache
set smtp_url=smtp://$my_user:$my_pass@smtp.live.com
set smtp_pass=password
set realname=
set ssl_force_tls = yes

```Note smtp instead of smtps

---

### Post by andrew.46 on 2013-03-18
I have written up the old way of doing things here:

Using Mutt with Gmail
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

Still works well for me...

---

