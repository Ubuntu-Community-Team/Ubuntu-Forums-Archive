---
title: "Mail server help..."
date: 2007-06-08
forum: Programming Talk
---

### Post by hockey97 on 2007-06-08
Hi I installed my mail server  and now want to make a web page interface for my user's to use, I am providing a mail service ect.

I  am using webmin to config my mail server ect and I want to be able to test the mail server ect. 

I don't have a domain name I will soon in the near future have one but for now I don't.

I also hear that pop mail is much more secure than smpt mail is that true?? I have the smpt mail one.

I also would love to make a login system using mysql database to host the passwords and usernames.

and would love to see where I could make a automated registering thing.

---

### Post by Mr. C. on 2007-06-08
Have a look at Squirrelmail.

Make sure your ISP allows outbound email delivery from your mail server.

POP and SMTP are two different animals.  The former retrieves email from a mail store, the latter delivers mail.  POP transmits passwords in clear text.  Both are clear text protocols, but both can be used over an encrypted link.

Automatic registration of email services?  Be prepared to a) become a SPAM source, and b) get blacklisted quickly.

MrC

---

### Post by hockey97 on 2007-06-08
I have seen that mail server, I ma using fetchmail and also mailman mail server .

I am trying to make my own webpage that uses the mail server to serve mail  but I am trying to imake my own e-mail web interface.

Basicly a web page that you can login and read your mail, and I could intergrad anything like spell check ect into that page.

also automated register would be that you fill out a form and it then get's sent to my e-mail  and then send's a letter thanking you to register and a link that you have to click to activate the account.

Whould making web pages and features be better programming in python?? or in php??

---

### Post by Mr. C. on 2007-06-08
I see... you want to build your own for some reason. Its a lot of work.

There is no answer to the Which Is Better question.  Choose the one that is more useful to you, and that you know best.

Best of luck,
MrC

---

### Post by hockey97 on 2007-06-08
Thanks, I have alot of time on my hands kinda.

I have this whole summer , and I am thinking into going in the ISP business ect.

---

