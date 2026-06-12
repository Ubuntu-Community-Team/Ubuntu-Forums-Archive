---
title: "Difficulty connecting to internet"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by lyni on 2012-02-26
I have been having problems for some time trying to connect to the internet. when I login I open Firefox and it sits there for ages saying 'Connecting' then 'Server not found'
I have tried turning the modem on and off. I have tried turning the computer on and off.
eventually I somehow connect but it may take up to 45 minutes sometimes.
other times I connect straightaway.

I did ring my service provider but they were hopeless. they tried to get me to reset the modem but it didn't work and they said there was nothing more they could do. I was left with this useless modem. 

fortunately the following day I was able to take the modem to a local Linux Group and they reset the modem for me.

can anyone please tell me in simple language why this would be happening and is there a simple fix?

I have Ubuntu 10.04
Modem - Dynalink RTA 1320

thanks lyn

---

### Post by whatthefunk on 2012-02-26
Do you have a DSL connection?  I had similar problems and so started using the program pppoeconf to connect.  In a terminal, you can type pppoeconf to get it started.

---

### Post by lyni on 2012-02-26
> **whatthefunk said:**
> Do you have a DSL connection?  I had similar problems and so started using the program pppoeconf to connect.  In a terminal, you can type pppoeconf to get it started.

thank you for your reply. yes I do have an ADSL connection. the modem plugs into the computer.
if I put pppoeconf in the terminal what will it do?
I'm a bit wary of the terminal (sorry I'm a big chicken)
lyn

---

### Post by whatthefunk on 2012-02-26
pppoeconf is a text based program that connects you to the internet over Ethernet.  Ill try to walk you through it.

In a terminal, type:
[code]sudo pppoeconf[/quote]

Enter your password.

The terminal will turn blue and the program will scan your system for ethernet connections.

Click yes at the Popular Options dialog.

Enter the username provided by your DSL provider.  This should be in a email address format.  Example: jimbob@comcast.net

Enter your password.

Answer yes to the questions that follow.  It should set it up to start automatically on boot.  You should have a working connection after this.

---

### Post by lyni on 2012-02-26
thank you for the explanation.
I will try and overlook my apprehension about the terminal.
thanks again
lyn

---

