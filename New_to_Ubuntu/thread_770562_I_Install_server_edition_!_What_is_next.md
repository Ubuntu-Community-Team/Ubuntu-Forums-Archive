---
title: "I Install server edition ! What is next ?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Me! on 2008-04-27
Hi

how to set My IP & logon by ssh from the Internet ?

---

### Post by louieb on 2008-04-27
1st you need to install openssh-server.

Easiest way to get set up to ssh into it from the internet  is to let your router  assign a static IP for your server.  Also you need to set your router to port forward the ssh port (usually 22).

Then you need to setup a service like dyndns.org to route internet request to your server. Your router may have an option to update your account on dyndns when your ISP   changes your IP address. 

Its not hard but it can be frustrating if you haven't done it before.
Good Luck.

---

### Post by Me! on 2008-04-28
> **louieb said:**
> 1st you need to install openssh-server.

Easiest way to get set up to ssh into it from the internet  is to let your router  assign a static IP for your server.  Also you need to set your router to port forward the ssh port (usually 22).

Then you need to setup a service like dyndns.org to route internet request to your server. Your router may have an option to update your account on dyndns when your ISP   changes your IP address. 

Its not hard but it can be frustrating if you haven't done it before.
Good Luck.

I have an IP from my provider , how to set network configuration in command line ?
How to allow external IP to login by ssh ? 

I think to install Ubuntu for Desktop !! it is more easy ! :(

---

### Post by hyper_ch on 2008-04-28
```

sudo apt-get install openssh-server

```

Well, do you have a static IP by your provider?
Do you have a router and operate a local lan?
...
...
There are a few more questions before we can help you there.

---

### Post by Me! on 2008-04-28
> **hyper_ch said:**
> 
Well, do you have a static IP by your provider?

Yes

---

### Post by hyper_ch on 2008-04-28
and the other question?

---

### Post by Me! on 2008-05-04
> **hyper_ch said:**
> and the other question?

I don't have a router now ! but I think to buy small wireless DSL to access to the internet by server & others.

so is the router a big problem now!

---

### Post by Me! on 2008-05-07
[https://help.ubuntu.com/8.04]("https://help.ubuntu.com/8.04")

I will read this help to find what I want to know !

Thanks all
:popcorn:

---

### Post by Xiong Chiamiov on 2008-05-07
You may want to take a look specifically at [this guide]("https://help.ubuntu.com/community/SSHHowto").

---

