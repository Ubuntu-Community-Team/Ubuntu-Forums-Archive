---
title: "SH/BASH: How to display the last 5 emails using IMAP GMAIL into the console?"
date: 2011-01-31
forum: Programming Talk
---

### Post by honeybear on 2011-01-31
Hello

I would like to display the last 5 emails using IMAP GMAIL into the console: 
[B] from
 subject
 content | head -n 5[/B]


would have someone the script to that? 

Thanks 
Kind regards

---

### Post by Rany Albeg on 2011-02-01
```
curl -u username --silent "https://mail.google.com/mail/feed/atom" | perl -ne 'print "\t" if /<name>/; print "$2\n" if /<(title|name)>(.*)<\/\1>/;'
```

Will prompt the user for a password and will print a list of unread messages.

---

### Post by honeybear on 2011-02-01
> **Rany Albeg said:**
> ```
curl -u username --silent "https://mail.google.com/mail/feed/atom" | perl -ne 'print "\t" if /<name>/; print "$2\n" if /<(title|name)>(.*)<\/\1>/;'
```

Will prompt the user for a password and will print a list of unread messages.

thank you, sounds good way.... would you know how to pass the password secured, withotu anyone can find it using ps aux?

---

### Post by Rany Albeg on 2011-02-02
Taken from ''curl --help''
```
 -u/--user <user[:password]> Set server user and password
```

I don't recommend you to hardcode your password.

---

### Post by honeybear on 2011-02-18
> **Rany Albeg said:**
> Taken from ''curl --help''
```
 -u/--user <user[:password]> Set server user and password
```

I don't recommend you to hardcode your password.

[SIZE="5"][COLOR="Red"]**[COLOR="Red"]ps aux: Man, the password is in plaintext !! feed/atom, it is not secured. TRY the command: ps aux [/COLOR]**[/COLOR][/SIZE]

```
 25058  0.0  0.0   5656  2012 pts/8    S    22:06   0:00 wget -T 3 -t 1 -q --secure-protocol=TLSv1
```

```


#!/bin/bash
## Quickly checks if I have new gmail
USERNAME=`cat $HOME/.muttrc  | grep "imap_login ="  | cut -f2 -d\' `
PASSWORD=`cat $HOME/.muttrc  | grep "imap_pass ="  | cut -f2 -d\' `
atomlines=`wget -T 3 -t 1 -q --secure-protocol=TLSv1 \
 --no-check-certificate \
 --user="$USERNAME" --password="$PASSWORD" \
 https://mail.google.com/mail/feed/atom -O - \
 | wc -l`
 
echo  "\r\c"
 
[ $atomlines -gt "8" ] \
 && echo " You have new gmail" || echo  "0"

```

---

### Post by Rany Albeg on 2011-02-18
WTF, are you on drugs?

---

