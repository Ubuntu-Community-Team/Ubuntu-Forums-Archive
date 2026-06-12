---
title: "Setting up a web server"
date: 2009-06-27
forum: Programming Talk
---

### Post by PaulM1985 on 2009-06-27
Hi

I am setting up a webserver on my computer and I am able to view the page I have created using [http://myIPaddress:8080/My_Website/](http://myIPaddress:8080/My_Website/)  but when I have asked friends to view it that have been unable to.

I have some settings on my router to allow the connection.  The fields I have are:

Protocol, Port Range, Translate To ..., Trigger Protocol and Trigger Port.

What values do I need to set for these.  I have tried:
TCP 80-80 8080-8080 - -
TCP 8080-8080 80-80 - -
TCP 80-80 80-80 - -

With no luck.

Anybody with any ideas?

Thanks in advance

Paul

---

### Post by philcamlin on 2009-06-27
do you have port forwarding?:popcorn:

---

### Post by PaulM1985 on 2009-06-27
Whats that?

Sorry I probably should have said, have never done this before and I am not sure what exactly I have to do.  Just followed my nose so far.
Has the port forwarding not been done by setting the Port range and translate to sections mentioned above

---

### Post by secondstage on 2009-06-27
What make/model router are you using?

I would suggest googling the name of your router and "port forwarding". You will be enlightened.

With port forwarding the outside people are just getting nothing in response, because they are only getting to your router.

For example, I have got an old Linksys WRT54G, and it has a page on the local router site to set up port forwarding, which makes the router forward incoming requests on a certain port to a computer on the internal network on a certain port. I have a web/mail server, so I have ports 80, and a few others forwarded.

---

### Post by PaulM1985 on 2009-06-27
Ive got a BT Home Hub

---

### Post by PaulM1985 on 2009-06-27
By setting up the stuff as described in my first post I thought I had dealt with port forwarding.  Is this not the case?

---

### Post by secondstage on 2009-06-27
I do not feel like rewriting what it already written on another site, so [here]("http://www.portforward.com/english/routers/port_forwarding/BT/BTHub/") is a link about how to setup port forwarding on your router. Read it through, and follow the instructions. I used that site once upon a time, and it worked perfectly. If you have any questions just ask.

---

### Post by PaulM1985 on 2009-06-27
I have never felt like such a muppet.  My Hub was set up correctly.  Problem occured when the incapable user (me) typed in the wrong IP address.

Sorry.

Paul

---

### Post by secondstage on 2009-06-27
Don't sweat it. Solved?

---

### Post by PaulM1985 on 2009-06-27
Yep all working.

My friends are downloading me and my fiances stag and hen nights as we speak.

Thanks for everyone for looking at this.

Paul

---

