---
title: "Python: Download Mail"
date: 2010-06-20
forum: Programming Talk
---

### Post by chevloschelios on 2010-06-20
Hello,

i make application. THe application connect to gmail and check the new mail. If there is a new mail the program print "The New Message". But this program return from GMAIL only number of new e-mails. I want to know how i can download the text of mail with Python. Thanks. :confused:

---

### Post by StephenF on 2010-06-20
There is a minimal example in the link. Make sure your Google mail account is enabled for pop3.

[http://docs.python.org/library/poplib.html](http://docs.python.org/library/poplib.html)

---

### Post by soltanis on 2010-06-21
Use IMAP use IMAP use IMAP

IMAP >>> POP3

Python has an imaplib.
By the way if you aren't looking to implement this just because you *want* to write the program yourself, there is a program named fetchmail which can work with gmail and will do this work for you.

```

sudo apt-get install fetchmail

```

---

### Post by chevloschelios on 2010-06-21
I have used imaplib!

---

### Post by chevloschelios on 2010-06-21
Which command is for download e-mail ?

Here is my code:

```
import imaplib
def receive():
    username=xxx
    password=xxx
    i=imaplib.IMAP4_SSL('imap.gmail.com')
    try:
        i.login(username,password)
        x,y=i.status('INBOX','(MESSAGES UNSEEN)')
        messages=int(re.search('MESSAGES\s+(\d+)',y[0]).group(1))
        unseen=int(re.search('UNSEEN\s+(\d+)',y[0]).group(1))
        return(unseen)
    except:
        return False
```

---

### Post by Zugzwang on 2010-06-21
There's an example for fetching mail on the documentation page of your IMAP library: [http://docs.python.org/library/imaplib.html](http://docs.python.org/library/imaplib.html) (at the bottom of the page).

---

### Post by ja660k on 2010-06-21
I hope you dont mind, i used your code...
```

import imaplib
import re

def receive():
    username="xxxx"
    password="xxxx"
    i=imaplib.IMAP4_SSL('imap.gmail.com')
    try:
        i.login(username,password)
        x,y=i.status('INBOX','(MESSAGES UNSEEN)')
        messages=int(re.search('MESSAGES\s+(\d+)',y[0]).group(1))
        unseen=int(re.search('UNSEEN\s+(\d+)',y[0]).group(1))
        [b]i.select("INBOX")
        typ, data = i.search(None, 'ALL')
        for n in data[0].split():
            typ,data = i.fetch(n,'(RFC822)')
            print 'Message %s\n%s\n' % (n, data[0][1])
[/b]
        return(unseen)
    except Exception as e:
        return e

print receive()

```

look at
[http://docs.python.org/library/imaplib.html?highlight=imaplib#module-imaplib](http://docs.python.org/library/imaplib.html?highlight=imaplib#module-imaplib)
because i took it off that page

---

### Post by chevloschelios on 2010-06-21
Thank you very much! But if it is possible can you write the code that program read only unread message ?

---

