---
title: "mail server web interface php"
date: 2007-11-01
forum: Programming Talk
---

### Post by hockey97 on 2007-11-01
HI I want to know how I could make a web interface with my mail server.

Like I am making a webpage in php, and want to give a e-mail service.
I know there is squirrel mail  but I  want to make my own .

so what I want to do is on my webpage after the user login their will be a mail button on the users profile thing, and when click takes them to their own mail page where they could write e-mail or look at new ones.

but I want it to look custom, I want to be able to create how the web interface would be layed out and how it looks artwise.

is their any website that you could suggest that would give me a better understanding of what goes on when interfacing a mail server with the web.

I know php, html, c++, python.

---

### Post by dataw0lf on 2007-11-01
[http://us2.php.net/manual/en/ref.imap.php](http://us2.php.net/manual/en/ref.imap.php)

---

### Post by nanotube on 2007-11-01
if your goal is just to make it "look custom", take an existing webmail implementation, and change the looks - you'll have an easier time of that. some of them even support skins, so you could just make a custom skin, without tweaking actual code.

---

### Post by hockey97 on 2007-11-03
not fully just custome, I just want to do the web programming part, where I can make the layout and also use my own art to be used on my website, but the server itself I don't want to mod it or anything, just be able to use the functions in php on my page so It can be a web user interface.

pro looking in other words.

the reason I want to web program it myself on my page, so I can have a full control on security and other stuff.

I mainly for now want to be able to get a mail server up and working and have my web interface working then later on I will worry about the security..

---

### Post by CptPicard on 2007-11-03
Security is one of the main reasons why you should NOT reinvent the wheel. Considering how much trouble you had with salting password hashes, I really recommend you take existing code and go from there -- you'll learn a LOT reading it, the code will be more correct out of the box than what you'd come up with, and as you customize it to your liking, you'll learn more...

---

