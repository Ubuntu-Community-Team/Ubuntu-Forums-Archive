---
title: "getting ubuntu to send a text message (sms) of my daily logs."
date: 2016-03-13
forum: New to Ubuntu
---

### Post by peteclark82 on 2016-03-13
I don't have a domain and cannot set up mail on my server.  I would however like to be able to send a copy of my logs to myself every day.  I understand that I can use cron for this, but just for now I would like to be able to send it manually.  Part of this works, but the /var/log/faillog part does not.  here is the code that I am using.  Any help is appreciated. thanks
#!/bin/bash
curl [http://textbelt.com/text](http://textbelt.com/text) -d number=<myphonenumber> -d "/var/log/faillog.*"
curl [http://textbelt.com/text](http://textbelt.com/text) -d number=<myphonenumber> -d "message=your welcome"

---

### Post by kevdog on 2016-03-14
The first curl statement in the script is going to fail.  You want in actuality to send the log file as an sms, however remember that an sms is limited to a finite number of characters.  Also consider the format of your log file.  Does it span multiple lines?  is each line going to sent as a individual text? If you store the contents of a file within a variable, carriage returns and leading white spaces are stripped.

---

### Post by mastablasta on 2016-03-14
> **peteclark82 said:**
> cannot set up mail on my server.

you can setup sSMTP to (only) send email using google account. [https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

then setup cron to do it for example daily and you compress the logs into one file to be attached.

then you set google account to notify you when specific mail arrives or something like that.

edit I suggest you create separate gmail account for this just in case google decided to close it.

---

