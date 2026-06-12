---
title: "&quot;Can you send this file to my email address?&quot; - Script to automate the process"
date: 2009-01-28
forum: Programming Talk
---

### Post by Amurko on 2009-01-28
I have a gmail account and I'm considering writing a script to automate this process.  At school, people often ask me to send files to their emails..  I would like to write a script that takes a file and an email address as input and sends the file to the email.  It should utilize Gmail's SMTP servers and can have my gmail account's login and password hard-coded into the script.  Ideally, I'd like to write-click on a file in Nautilus, have a dialogue pop up asking for an email address to send the file to, and hit send.

Any ideas if this is possible?

---

### Post by slavik on 2009-01-28
very much so, pick a good scripting language and it has the needed modules.

---

### Post by Cracauer on 2009-01-30
```
echo Here it is dude | mutt -a somejunk.zip -s file somemoron@foobar.com
```

---

