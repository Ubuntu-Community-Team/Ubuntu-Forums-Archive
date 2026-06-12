---
title: "Help with python!"
date: 2009-04-27
forum: Programming Talk
---

### Post by B4RR13N705 on 2009-04-27
Hi, im starting with python, and today i was bored :) so i decided to make some stuff with python. I want to make a script that connects to a Hotmail account under python. I get sucked on this.
How can i connect to a hotmail account under python?
Somebody please post a piece of code :popcorn:

---

### Post by ghostdog74 on 2009-04-27
learn about the basics of Python first before even doing that.

---

### Post by ajackson on 2009-04-27
> **B4RR13N705 said:**
> Hi, im starting with python, and today i was bored :) so i decided to make some stuff with python. I want to make a script that connects to a Hotmail account under python. I get sucked on this.
How can i connect to a hotmail account under python?
Somebody please post a piece of code :popcorn:
This isn't rentacoder you know. What have you done so far? What problems have you hit? When is this coursework due in :)?

---

### Post by B4RR13N705 on 2009-04-27
Actually is a script for a screenlet-like. I write all the other stuff. It actually works, showing on the desktop the Hotmail Icon and a number of unread mails. The problem is that i cant figured out how to connect to a hotmail account. I did something similar with gmail, that allows you to write mail with python:
```

import smtplib

FROMADDR = "mail@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "password"
TOADDRS  = ["mailto@gmail.com"]
SUBJECT  = "Test"

msg = ("From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n"
       % (FROMADDR, ", ".join(TOADDRS), SUBJECT) )
msg += "some text that you can send\r\n"

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(LOGIN, PASSWORD)
server.sendmail(FROMADDR, TOADDRS, msg)
server.quit()

```

Im not totally beginner, i think i expressed myself wrong :confused:
Can anybody point me in the right direction?

---

### Post by joey-elijah on 2009-04-27
> **B4RR13N705 said:**
> Actually is a script for a screenlet-like. I write all the other stuff. It actually works, showing on the desktop the Hotmail Icon and a number of unread mails. The problem is that i cant figured out how to connect to a hotmail account. I did something similar with gmail, that allows you to write mail with python:
```

import smtplib

FROMADDR = "mail@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "password"
TOADDRS  = ["mailto@gmail.com"]
SUBJECT  = "Test"

msg = ("From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n"
       % (FROMADDR, ", ".join(TOADDRS), SUBJECT) )
msg += "some text that you can send\r\n"

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(LOGIN, PASSWORD)
server.sendmail(FROMADDR, TOADDRS, msg)
server.quit()

```Im not totally beginner, i think i expressed myself wrong :confused:
Can anybody point me in the right direction?

Sorry, what are you trying to do? You said your hotmail screenlet works and shows the unread count fine. Well that's great already!

You want to be able to write an e-mail in the screenlet and send it? Wow! That would pretty nice, if very complex.

So.. why are you posting code for GMail?

---

### Post by B4RR13N705 on 2009-04-27
I think i counfused you even more :lolflag:
Im doing that hotmail screenlet, i cant figure the way to connect to a hotmail account yet. About the gmail code, i was just puting an example, just ignore it.
The point is:
How to connect to a hotmail account under python??

---

### Post by croto on 2009-04-27
I would start by making sure there's no library that does what you want to do. If not, and you wanna do it yourself, let me tell you that even though it isn't impossinle to do , it is not trivial either, and you'll have to sweat a bit. Hotmail is not a service that is designed to be accessed programmatically, the idea is that you'll have to mimick what the browser does when you login and access your account. In principle you'll have to:

1) Request the login web page: for that you can use python's urllib2 library. It'll make you're life easier because you'll have to establish an ssl connection to the server and also manage the cookies given by it. The cookies will allow to maintain the session - it is strictly necessary.

2) Probably you'll have to fill in a form (with username and password and least) and send it to the server. Urllib2 will come in your help for that. But in order to know what url you have to send the post to, what fields to fill, etc. you'll have to parse the login web page. You might end up doing some regular expressions for that purpose.

3) Access your folders, emails, etc: most probably there will be different http posts you'll have to do in order to get folders and emails. It may help to run a packet analyzer and check exactly what the browser is telling the server (which I guess will be http posts) and do the same thing from your program.

If you've never done anything like what I was trying to describe, consider this as a research project. Basically you'll have to reverse engineer the communication between your browser and hotmail and replicate it.

Good luck!

---

### Post by B4RR13N705 on 2009-04-27
mmm, i think i have some ideas in mind, it will not be that easy :) but it will not be impossible :P 
Thanx for the help! you just pointed me in the right direction.

---

### Post by B4RR13N705 on 2009-04-27
I touch the light! :KS
Im just making some tests, i will base my project to the way that "lynx" do it!

---

### Post by croto on 2009-04-27
mendocino eh?

---

### Post by simeon87 on 2009-04-28
Hotmail also has POP3 support so it's probably easier to use that instead of requesting the login page and all that.

---

### Post by nvteighen on 2009-04-28
Check if there is any Hotmail API documentation. If not, the POP3 solution might be the sanest way to do this.

---

### Post by B4RR13N705 on 2009-04-28
Ive searched for API documentation but i didnt found anything :confused: I thought about POP3 before, it seems to be a much easier way!

---

### Post by B4RR13N705 on 2009-04-28
ive found some suff about POP3
> 
POP server: pop3.live.com (Port 995)
¿POP SSL required? YES
User name: Your Windows Live ID
Password: Your Password
SMTP server: smtp.live.com (Port 25)
¿TLS/SSL Required? YES 


---

