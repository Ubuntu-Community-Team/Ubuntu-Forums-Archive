---
title: "Ufw"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by Merisi on 2011-09-30
I've just been configuring UFW and I'm concerned that I may leave my passwords unencrypted when using sites such as Amazon or PayPal.  Which permissions should I be allowing to make sure I can access the Internet properly but am also quite secure?

---

### Post by haqking on 2011-09-30
> **Merisi said:**
> I've just been configuring UFW and I'm concerned that I may leave my passwords unencrypted when using sites such as Amazon or PayPal.  Which permissions should I be allowing to make sure I can access the Internet properly but am also quite secure?

UFW which is a just an interface for IPTables which is the firewall built into your kernel has nothing to do with encryption of your web browsing.

It is a rule based firewall for allowing or denying protocols and given ports access.

Encryption of your web traffic will be achieved automatically on sites such as amazon and paypal as they use HTTPS which is SSL over HTTP which means secure channel. (well reasonably secure as TLS 1.0 has just been cracked ;-)

---

### Post by sffvba[e0rt on 2011-09-30
I am not sure what UFW has to do with your passwords etc... typically the optimal is to run ufw without arguments.  That blocks all incoming ports and allows all outgoing...

*ninja'ed*

404

---

### Post by Merisi on 2011-09-30
> **haqking said:**
> UFW which is a just an interface for IPTables which is the firewall built into your kernel has nothing to do with encryption of your web browsing.

It is a rule based firewall for allowing or denying protocols and given ports access.

Encryption of your web traffic will be achieved automatically on sites such as amazon and paypal as they use HTTPS which is SSL over HTTP which means secure channel.

I've been configuring UFW on the basis of this video [http://www.youtube.com/watch?v=pant4n9OzRQ](http://www.youtube.com/watch?v=pant4n9OzRQ)  because it explains it easily at around 7:30 which says you have to allow on outgoing connection for TCP on port 443 otherwise you'll leave your passwords in plain text to anyone who is potentially sniffing around your machine.

I can't help thinking I might be better off allowing all outgoing and deny all incoming.

---

### Post by 3rdalbum on 2011-09-30
> **Merisi said:**
> I've been configuring UFW on the basis of this video [http://www.youtube.com/watch?v=pant4n9OzRQ](http://www.youtube.com/watch?v=pant4n9OzRQ)  because it explains it easily at around 7:30 which says you have to allow on outgoing connection for TCP on port 443 otherwise you'll leave your passwords in plain text to anyone who is potentially sniffing around your machine.

That sounds very strange.

Your gut intuition is correct: Just block all incoming and allow all outgoing, there's not really a reason to block outgoing ports for normal home computers.

In fact, you've probably already got a firewall in your modem/router that is already set up just the way it should be, which would mean that you don't need UFW.

Even if your modem doesn't have a firewall, your computer probably isn't listening to any incoming connections anyway. You don't need a firewall if nothing on your computer will react to incoming connections. A deaf man doesn't need earmuffs.

---

### Post by haqking on 2011-09-30
> **3rdalbum said:**
> That sounds very strange.

Your gut intuition is correct: Just block all incoming and allow all outgoing, there's not really a reason to block outgoing ports for normal home computers.

In fact, you've probably already got a firewall in your modem/router that is already set up just the way it should be, which would mean that you don't need UFW.

Even if your modem doesn't have a firewall, your computer probably isn't listening to any incoming connections anyway. You don't need a firewall if nothing on your computer will react to incoming connections. **A deaf man doesn't need earmuffs**.

+1

ive always wandered about the last statement though, cos being deaf doesnt mean your ears dont get cold...LOL

---

### Post by JKyleOKC on 2011-09-30
> **Merisi said:**
> I've been configuring UFW on the basis of this video [http://www.youtube.com/watch?v=pant4n9OzRQ](http://www.youtube.com/watch?v=pant4n9OzRQ)  because it explains it easily at around 7:30 which says you have to allow on outgoing connection for TCP on port 443 **otherwise you'll leave your passwords in plain text** to anyone who is potentially sniffing around your machine.

I can't help thinking I might be better off allowing all outgoing and deny all incoming.Many instruction videos are, to be charitable, less than accurate. If you don't allow outgoing for port 443, you simply won't be able to connect to any site that uses "https" as the first part of its name. Only if the web site is very poorly designed would it leave your passwords in plain text -- and if it's that badly designed, you have no guarantee that they aren't always left exposed anyway!

You're correct that you would be better off by allowing all outgoing and blocking all new incoming -- but keep in mind that if any rogue web page did manage to infect you, it would be able to call home. The one time that I did get an actual virus infection (with Win98SE), having outgoing traffic blocked was what alerted me to the problem in time to save most of my data...

---

