---
title: "Mailer"
date: 2013-08-14
forum: Programming Talk
---

### Post by wingnut2626 on 2013-08-14
I'm beginning the process of writing an automatic mailer from my server that will send me processes, and whatever else I want.  Here is the code:
```

import smtplib

def Mailer(argument):

  FROMADDR = "fromme@fromme.com"
  LOGIN    = FROMADDR
  PASSWORD = "password"
  TOADDRS  = ["send@send.com"]
  SUBJECT  = "Test"

  msg = argument

  server = smtplib.SMTP('smtp.gmail.com', 587)
  server.set_debuglevel(1)
  server.ehlo()
  server.starttls()
  server.login(LOGIN, PASSWORD)
  server.sendmail(FROMADDR, TOADDRS, msg)
  server.quit()

```

 Saved the module as mail.py. Now if argument is a string created on the fly, or if it is a short string written from another program, say:

```


import mail

b = 'hello world'
mail.Mailer(b)


```

it sends perfectly fine.  However if i run an exteral command, pipe the output to a file, read the file and send the resulting string as 'argument', nothing happens. 

```


import os 
import mail

a = os.popen2('ps -A > /home/user/info.txt')

b = open('/home/user/info.txt').read()

mail.Mailer(a)


```

I don't get a traceback or anything.  As a matter of fact it shows as if the string was being sent successfully.  

Any ideas?

---

### Post by spjackson on 2013-08-14
> **wingnut2626 said:**
> 
```


import os 
import mail

a = os.popen2('ps -A > /home/user/info.txt')

b = open('/home/user/info.txt').read()

mail.Mailer(a)


```

The short answer is that you have read the message into the variable b, so that is the variable you want to pass to your Mailer function.

A fuller answer would include:
[LIST]
[*]os.popen2 and similar functions are deprecated in favour of the subprocess module.
[*]If you want to use a pipe, don't use the intermediate file info.txt; either use a pipe or use the file, not both.
[*]As it stands, at the time you call read() the file may not necessarily have finished being written.
[/LIST]

---

### Post by wingnut2626 on 2013-08-15
Actually what it turned out to be was that I was missing certain headers that Gmail.com requires to be. 'RS' compliant.  Added those headers and it worked perfectly fine.  I also used a file because I had more information I wanted in the email than just a process list.  I changed to a ' a = subprocess.check_output' instead of the os.open.   I know that the subprocess is newer, but does it really make a difference?

---

### Post by wingnut2626 on 2013-08-15
check this out too [http://essays.ajs.com/2011/02/python-subprocess-vs-ospopen-overhead.html](http://essays.ajs.com/2011/02/python-subprocess-vs-ospopen-overhead.html)

---

