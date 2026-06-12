---
title: "php/html not showing"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by grofstepe on 2018-03-20
hello everyone

i use ubuntu 14.04
and i have a small problem
before i use cpanel and i put some files for one website
but now i have my own vps ubuntu adn i copy files from cpanel and i paste here
but i have a litle problem
well
this page work
[HTML]http://173.212.241.203/hosting/[/HTML]

but when i click to counter strike or csgo or team speak for example then i see this
[HTML]http://173.212.241.203/hosting/cs16.html[/HTML]

to all other sites
i dont know where is problem maybe i miss something
please can anyone help me

---

### Post by mg2003 on 2018-03-20
Tough to say without seeing your php code, but I'm guessing your headers are off by a directory.  I suspect this because I can see evidence for the image.

View source on each page and then flip back and forth between the tabs quickly and you'll see what I mean for the broken image.

Note that your first page has this:
[HTML]<img src="images/logo.png" alt="Logo" />[/HTML]

But the second page you provided has this:
[HTML]<img src="../images/logo.png" alt="Logo" />[/HTML]

So it doesn't sound like an OS problem so much as a problem with where your directories got copied to when you moved everything.

---

### Post by grofstepe on 2018-03-20
wowww woow wowww
yesss i fix 
thank u my bro
u r genius
thank u 
thank u
thank :)

---

### Post by mg2003 on 2018-03-22
You're welcome! Glad I could help!

---

