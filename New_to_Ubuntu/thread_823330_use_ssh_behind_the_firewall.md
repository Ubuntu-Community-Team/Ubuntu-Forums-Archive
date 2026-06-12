---
title: "use ssh behind the firewall"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Me! on 2008-06-09
Hi all

I want to access by ssh to make urgent backup, but Network firewall not allow me 

I do not have an access to this firewall 

I can use the web  , so is their a way to use ssh in this network 

Thanks

---

### Post by wannadumpwindows on 2008-06-09
The purpose of the firewall is to keep people that don't have permission out. If you don't have access to the firewall, should you really be making a backup of that machine? Kind of sounds like something a little suspicious, but I could be entirely wrong. Sorry I can't help you.:(

---

### Post by johnhunsley on 2008-06-09
I think he means that his client is behind a firewall which wont let him connect to an ssh server, i.e. port 22 is blocked.

Simple answer - use a web based ssh client like this -

[https://www.browsershell.com](https://www.browsershell.com)

just like a terminal, but all done in your browser :)

---

### Post by wannadumpwindows on 2008-06-09
I gotcha, my bad peeps. Sorry.

---

### Post by Dr Small on 2008-06-09
Wow. Cool. What is that Browsershell?

---

### Post by wannadumpwindows on 2008-06-09
> **Dr Small said:**
> Wow. Cool. What is that Browsershell?

I was wondering the same thing, but the link just takes me to a login page, I'm not registering b4 I even know what it's all about . . .

---

### Post by johnhunsley on 2008-06-10
Hi,

its just a site I set up, not quite finished yet, awaiting graphics!

It gives you ssh access through a browser so you can get shell access to your ssh server through a browser.

If you register you get 5 days free access, go to 'open shell' after login and you'll be able to open the terminal through your browser, hence the name browser shell.

It's completely secure, uses https from your browser to the web server and native ssh from the server to the ssh server you want to access. I don't store anything about the ssh server you are accessing so you can access your important server, web server or whatever from anywhere in confidence.

After the free period it will only cost $5 a month or cheaper if you sign up for a year. 

I'm working on giving users the ability to define the port, currenlty only defaults to port 22. I also want to enable it to work through a phone browser, like the iphone. It works but phone browsers dont 'see' the shell as part of the page form as its all done in javascript.

Anyway, register, have look and give me some feed back.

John.

---

### Post by richard74 on 2008-07-04
alternatively you might want to use the consoleFISH at

[http://www.serfish.com/console]("http://www.serfish.com/console")

it is ad based and can thus be used for free. similar to [www.gotossh.com](www.gotossh.com) and my.anyterm.org. anyway: please make sure to consider security aspects when using such clients. NO web based ssh client is 100% secure as you always have to trust your tunnel provider.

---

### Post by hyper_ch on 2008-07-04
I still see a problem if the computer he tries to access is behind the firewall... if so there's no portforwarding setup and he can't really access it.

---

### Post by richard74 on 2008-07-04
in any case: you need some kind of access to the internet :)
for the mentioned browser ssh software you need port 80/443 open i guess. if you have this, i suppose you can do almost anything you can do on an open/unlocked workstation :)

---

