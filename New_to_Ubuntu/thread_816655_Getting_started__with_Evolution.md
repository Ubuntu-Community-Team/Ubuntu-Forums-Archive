---
title: "Getting started  with Evolution"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-02
Hello i havent yet used any Mailing appliactions like Evolution.

i use to check my mails by loging into corresponding websites.


Could i download all my inbox messages to my computer.

how could i configure my Evolution.

What should i enter in place asking server address.

---

### Post by spiderbatdad on 2008-06-02
I don't use evolution. I use thunderbird...but typically, sever address would be the web address of your mail server. Then incoming mail might be something like pop.short_name.net And outgoing: smtp.short_name.net.

So if [www.charter.net](www.charter.net) were your mail server:

pop.charter.net
smtp.charter.net

---

### Post by lisati on 2008-06-02
Once you have set up your first email account in Evolution, you can add others with Evolution's Edit->Preference menu.

EDIT: If it's a Yahoo email account, you will have to go to the Yahoo webmail site and edit your options for "Pop mail and forwarding", which will also have information on what settings to put into Evolution. Depending on what sort of Yahoo account and where you live, you might have to pay. Similarly you have to tell Gmail that you want POP access. Hotmail's a different story - you used to be able to get it for free, but now they like to get paid.

---

### Post by rraj.be on 2008-06-02
I am a bit new to these areas.

I use gmail and i am using airtel GPRS  for my intenet connection.

what should i enter.

---

### Post by rraj.be on 2008-06-02
could any one get me how to configure thunderbird or evolution with some examples.

---

### Post by spiderbatdad on 2008-06-02
thunderbird will automatically do gmail for you if you check the gmail button...but as already mentioned, you have to go to gmail and edit you preferences to forward pop mail.

Click the 'settings' upper right. and select forwarding pop/imap.

---

### Post by EXCiD3 on 2008-06-02
Here is a quick tutorial with pictures on setting up evolution: [http://www.astro.ufl.edu/it/filtering/evolution/](http://www.astro.ufl.edu/it/filtering/evolution/)

What email addresses are you trying to setup for evolution? If you know the company its with we can probably get you the information you need to type in such as the server address etc.

---

### Post by lisati on 2008-06-02
To use Evolution (or Thunderbird) with Gmail, you will need to do the following first:
[LIST=1]
[*]Log into your gmail account online as normal
[*]Click on "settings" (at the top right of the web page)
[*]Click on "Forwarding and POP/IMAP"
[*]Choose either "Enable pop for all mail" or "Enable pop for mail that arrives from now on" according to your preferences
[*]Click on the "Save changes" button
[/LIST]

Information on the proper settings for your email software can be found at [http://http://mail.google.com/support/bin/answer.py?hl=en_GB&ctx=mail&answer=12103]("http://http://mail.google.com/support/bin/answer.py?hl=en_GB&ctx=mail&answer=12103")

---

### Post by rraj.be on 2008-06-02
I want to configure for my id 

[email]rraj.be@gmail.com[/email]

i am using airtel GPRS service for my internet connection

---

### Post by EXCiD3 on 2008-06-02
Here's what you need to do:

1) Log onto your gmail account at [www.gmail.com]("http://www.gmail.com/") and select &#8220;settings&#8221; which is located in the top right corner. Then click on &#8220;forwarding and pop.&#8221; Enable the option &#8220;Enable POP for all mail (even mail that's already been downloaded).

2)  Start Evolution
 
3) Type in your name, email address, reply to address, (what email address you want people to write back to you with) and your organization, if any, and click forward.
 
4) Select your server type as &#8220;POP,&#8221; your host as &#8220;pop.gmail.com,&#8221; and make sure that your username is the same as your email address. Then under &#8220;Use Secure Connection&#8221; select always, and your &#8220;Authentication Type&#8221; as password, and finally click forward.
 
5) On the next page adjust settings as you like, they will not interfere with whether gmail will work with evolution or not. Then click forward.
 
6) Select server type as &#8220;smtp,&#8221; type in &#8220;smtp.gmail.com&#8221; as the host, and check that the &#8220;Host requires authentication&#8221; box is checked. Next, select, for &#8220;Use Secure Connection,&#8221; always. Finally, make sure that Authentication type is &#8220;Plain&#8221; and your user name should be the same as you email address. Click Forward.
 
7) On this page name your account whatever you want, it will not interfere with setup and click Forward.
 
8) Click apply.
 
Your done!

Source: [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/41552-complete-guide-using-gmail-thunderbird-mozilla-mail-evolution-kmai.html)

---

### Post by rraj.be on 2008-06-03
I have already created an evolution mail acount in my ubuntu with wrong information.

how can i create my new acount.

---

### Post by EXCiD3 on 2008-06-03
> **rraj.be said:**
> I have already created an evolution mail acount in my ubuntu with wrong information.

how can i create my new acount.

Start Evolution
Click on “Edit,” then “Preferences”
 Click “Add”

You should also be able to delete the old account with the wrong info from there also.

---

### Post by lisati on 2008-06-03
> **rraj.be said:**
> I have already created an evolution mail acount in my ubuntu with wrong information.

how can i create my new acount.

[LIST=1]
[*]Start Evolution
[*]Click on "Edit"
[*]Click on "Preferences"
[*]Click on "Edit"
[/LIST]

You will now be able to change Evoulution's settings to the correct information.

---

### Post by EXCiD3 on 2008-06-03
> **lisati said:**
> 
[LIST=1]
[*]Start Evolution
[*]Click on "Edit"
[*]Click on "Preferences"
[*]Click on "Edit"
[/LIST]

You will now be able to change Evoulution's settings to the correct information.

beat you :lolflag:

---

### Post by rraj.be on 2008-06-03
Ok now  created my acount.

how to import all my inbox messages from my gmail server to my computer.

---

### Post by rraj.be on 2008-06-03
any one there

---

### Post by mix. on 2008-06-03
Click the Send/Receive button on the toolbar. If you properly configured everything, it should start downloading your messages.

By the way, if you want to synch changes in your Evolution inbox with your Gmail inbox (ie, when you delete something in Evolution it also deletes it in Gmail), choose IMAP instead of POP when doing the configurations. POP doesn't do this.

---

### Post by rraj.be on 2008-06-03
But that button  [send/recive] is not enabled for me.

---

### Post by MJWitter on 2008-06-03
IF everythig is set up correctly(ie in Gmail Preferences and in Evolution) then getting all your old mail should be as simple as pressing Send/Receive in Evolution

---

### Post by rraj.be on 2008-06-03
when i clicked my send/recive button  its showing a message with progres.

but after a minuite its displaying 

```
Error in fetching mail
```

What could be the problem.

---

### Post by edemkrimea on 2008-07-07
thank you friends.I appreciate your help

---

