---
title: "Authenticating to Gmail; Sending txt messages"
date: 2013-01-23
forum: Programming Talk
---

### Post by LearnAlways on 2013-01-23
Hello,

I want to write a python program that can check a gmail account for new emails that match certain criteria (e.g., sender, subject, urgency), and notify the user via text message when such an email has arrived. 

I know the very basics of python programming, but I do not know which libraries I will need to accomplish the above. I'm hoping that someone here may be able to point me in the right direction. 

Perhaps I should start with how to get this program to authenticate to gmail. For now, let's imagine that the program stays open on the user's home PC. Then, at a pre-determined interval, it checks the gmail account. Perhaps in the future I can consider having this execute from a server instead of the user having to keep their home PC on and the program open. But for now, I'm thinking I should keep it as simple as possible.

What do you think?

With much gratitude,

LearnAlways

---

### Post by Zugzwang on 2013-01-23
Hi LearnAlways.

Gmail supports IMAP, which is a standard for accessing e-mail on a server. Since there is a Python library for using IMAP to connect to an e-mail server (see [http://docs.python.org/2/library/imaplib.html](http://docs.python.org/2/library/imaplib.html)), you might probably want to use that.

A quick google search also revealed some examples of using it specifically with gmail:

[http://yuji.wordpress.com/2011/06/22/python-imaplib-imap-example-with-gmail/](http://yuji.wordpress.com/2011/06/22/python-imaplib-imap-example-with-gmail/)

I hope that this helps!

---

### Post by LearnAlways on 2013-01-23
Excellent information! Thank you!

I started tinkering with this, and it is very interesting. I don't understand as much of it, as I would like though.

For instance on the blog post which you linked to:

```
result, data = mail.search(None, "ALL")


ids = data[0] # data is a list.

id_list = ids.split()
```

What is exactly is being returned to "result" and "data" here?

And could you explain the structure of "data"? As I understand:


[[label,body],[label,body],...etc)]

with each "[label,body]" sub-list representing an individual message - with label being the message's number and body its body/main text.


I'm probably mistaken about quite a bit here.

---

### Post by Zugzwang on 2013-01-23
> **LearnAlways said:**
> 
What is exactly is being returned to "result" and "data" here?


The documentation of the library, that I linked to above, contains the information that you are requesting. It says, "Each command returns a tuple: (type, [data, ...]) where type is usually 'OK' or 'NO',". The documentation for the "search" function then tells you what type "data" is of.

Happy coding!

---

### Post by LearnAlways on 2013-01-28
Thanks man. I think I'm going to mark this thread as solved since it may be a while before I move on to the other components of my program.

---

