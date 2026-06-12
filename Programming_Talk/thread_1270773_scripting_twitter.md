---
title: "scripting twitter"
date: 2009-09-20
forum: Programming Talk
---

### Post by kirk ammon on 2009-09-20
I would like to set up a twitter account that can act as a connection between my computer and cell phone. (i.e. being able to run certain commands on my computer by texting the command to twitter). I have used the API before and know some of the basics, but currently I have my computer running a script every minute through cron to check twitter for messages from my phone. This is a waste of processor and is slow to respond (I have to wait up to a minute each time.) Is there a way for my computer to receive tweets in real time and only run a script after receiving a tweet?

---

### Post by jimi_hendrix on 2009-09-20
You could just use a while loop and sleep at the end of it for a second...this may use more cycles, but it will be a faster response

---

### Post by Reiger on 2009-09-20
You don't need twitter for that (and from a privacy p.o.v. arguably better if you didn't use a &#8216;publicly accessible service&#8217; like that): somebody on these forums already wrote an utility to do that directly via SMS.

---

### Post by fiddler616 on 2009-09-20
Yes. Try SMSing to an email address, and you'll get an email address for your phone's SMS.

I'm actually playing around with that right now--should be done within a month (getting Wikipedia onto phone).

---

### Post by fiddler616 on 2009-09-20
Also:
Look into the smtp library for sending, and either pop3 or imap4 for receving.
I'd get a dedicated Gmail account for all this. And look at the Gmail help center to find out which ports to use. And don't forget to use the SSL-enabled methods, otherwise it won't work.
You can find sample code either at the bottom of the API page, or more feature-ful code by Googling around.

---

### Post by kirk ammon on 2009-09-20
awesome. great ideas fellas.

---

### Post by fiddler616 on 2009-09-20
You would earn major geek points if you got the program running on a separate computer (do you have an old one in the basement?), and then had it SSH things to the main one. That might be a bit ambitious, though.

---

