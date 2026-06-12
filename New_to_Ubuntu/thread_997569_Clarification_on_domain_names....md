---
title: "Clarification on domain names..."
date: 2008-11-29
forum: New to Ubuntu
---

### Post by RavUn on 2008-11-29
Perhaps this isn't the right forum, but it's the only one I use.  If a domain name isn't taken then is there a way to claim it?  With dyndns you can buy a domain pretty cheaply, but what's stopping me from just getting an unused domain for myself without using another company?  I don't really understand how domains work and how some people control them.  [http://www.slkdfjsldjf.com/](http://www.slkdfjsldjf.com/) isn't used, so why couldn't I just make it my own domain accessible through the web... or can I?

---

### Post by binbash on 2008-11-29
you can buy it from godaddy or anyother if it is not registered.

---

### Post by wilbbe01 on 2008-11-30
Compare it to your name for starters.  You could say "I want my name changed to SDFSDF SDFSDF" but unless others actually recognize you as that name it won't do you a lot of good.  The records are not updated for your new name, as it is self proclaimed and nobody knows about it.  Very similar thing with domain names.  There are servers (DNS) which keep track of such things.  You could claim you were the owner of sdfasdfsdf.com but it would only be accessible as that from inside your network unless you had someone register it (such as your mentioned dyndns.org).  Once they have it they will allow things to propogate through the system so anyone (such as me) can type in asdfasdf.com from wherever I feel like it and be directed to it.  Very roughly like a phone book.  You can look in the phone book for name --> number information.  I could claim my phone number is 999-999-9999 but that won't work anywhere outside of my own phone network unless I actually have that number registered to me in the big network.  Does that help?  If you would like I can give a more technical explanation, but that kind of covers a general idea of why you can't just say you are asdfadsdf.com without registering it with someone.

---

### Post by Xiong Chiamiov on 2008-11-30
More importantly, you have to be registered with [ICANN]("http://en.wikipedia.org/wiki/ICANN").

BTW, monkeyblog's site is no longer up, so the third link in your sig is dead.

---

### Post by RavUn on 2008-11-30
Ok, thanks that helps.  I'm sure it's a little difficult (if possible), but is it possible to setup your own private nameserver (such as .zyx)?  And, I could have my own top-level domain like .com?  From what I understand from howstuffworks.com, there are several top-level domains (.com, .net, .org) that are, generally, maintaned by individual groups.  Wouldn't it be possible to setup your own top-level domain?  

Thanks for the update on my dead signature link Xiong Chiamiov.

---

### Post by wilbbe01 on 2008-11-30
You could have your own nameserver, but anything you assigned would only be accessible from inside your home network (unless you told every computer outside of your home you ever wanted to be able to type in "whatever.xyz" the ip address of your nameserver).  The top level domains also need to be registered through ICANN.  The top level stuff isn't something anyone can just say "I want a new top level" as I think you could imagine things getting pretty messy pretty quickly with everyone wanting a top level.

You in theory could point any computer you were using to your own nameserver by using your public ip address, but unless you have a static (non changing) ip address for your nameserver and a lot of different ip addresses you want mapped it would be a waste of your time.  If you are worried about getting things named in your own home network I suggest using ipcop as your router.  IPCOP makes it easy for people to set up their own names within their own private network, such as printer.local, desktop.local, or anything.anything.  All of those would only be accessible in your own local network though.  Does that make any sense?  Rather confusing topic to try and explain.

---

### Post by RavUn on 2008-11-30
Ah, makes sense.  Thanks for clearing it up.

---

