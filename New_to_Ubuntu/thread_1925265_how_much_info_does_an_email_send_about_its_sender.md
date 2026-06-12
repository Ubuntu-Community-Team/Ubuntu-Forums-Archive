---
title: "how much info does an email send about its sender?"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by werty2010 on 2012-02-14
im not talking about the content of the email(ofcourse) but more like ip and stuff like that.

---

### Post by Lars Noodén on 2012-02-14
It sends quite a lot.  You can look at the full message headers in Thunderbird easily.  View->Headers->All, then open a message and use the scroll bar to roll through what has been sent.  Mostly it's routing information on how and when the message found it's way from the sender's machine to your machine. Of course that information call be falsified easily, too.

---

### Post by stmiller on 2012-02-14
It can potentially include:

- Your originating ip, such as your home connection if sent from there

- Lists email servers that the message goes through (gives rough path of email)

- Can list your email program

Ex:
User-Agent: SquirrelMail/1.4.4

Outlook, Thunderbird, etc.


Of course any of these headers can be easily faked though.

---

### Post by jailbait on 2012-02-14
> **werty2010 said:**
> im not talking about the content of the email(ofcourse) but more like ip and stuff like that.
A lot.
Contains both the mailservers (sender mailserver & incoming mailserver), email addresses, mailserver names....

See [http://pastebin.com/waftmK1Q](http://pastebin.com/waftmK1Q) for an example.

---

### Post by sammiev on 2012-02-14
<--- uses a hotmail account and a vpn. :)

---

