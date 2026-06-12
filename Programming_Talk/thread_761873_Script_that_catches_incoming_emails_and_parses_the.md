---
title: "Script that catches incoming emails and parses them"
date: 2008-04-21
forum: Programming Talk
---

### Post by Palu on 2008-04-21
I have no idea what technologies to use for this so I'm not sure what to Google. I'd like to have an address that I can send an email to in a standard format and then the data would be pushed to appropriate fields in a new record on my database. We have a third party analysis tool which we aren't allowed to modify and it simply emails us results--though in a standardized format. This is low security data and if someone figured out how to add a bunch of bogus information, it wouldn't be too terrible or annoying.

Will I need to somehow direct an MX record at a script? I'm not sure how I'd do that. Does it have nothing to do with MX at all? I have no experience with administering a mail server / setting one up. I'd want something very simple. No GUI interfaces or outgoing mail, POP3 server, Imap server, etc--just a folder of raw incoming MIME emails. Perhaps mail all gets stored in a folder as text attachments, and I would need to write a program on a 15 minute repeating cron tab to parse, push to the database, then delete the email.

Once I have a string or text file I know enough PHP or C++ to parse the text and input it into a flat file or mySQL. I just don't know anything about mail.

Yes? No? Halfway there?

---

### Post by kidders on 2008-04-22
Hi there,

Most mail servers are capable of passing incoming mails through scripts. Postfix & Exim are two popular choices. Both provide *vastly* more features than you'll be needing, but imo it's always best to stick with well-known, standard applications, so getting them to work the way you want never involves anything more than following a howto.

Anyhow, you would set up your mail server and configure an alias of some sort (eg [email]robot@yourdomain.com[/email]) that points to a script, rather than a mailbox. Languages such as PHP, Perl, or even a quick shell script would probably do the job nicely.

> **Palu said:**
> Will I need to somehow direct an MX record at a script?Whether you need an MX depends on the requirements of whatever will be sending you email. Unless it requires one for some reason, you should avoid storing a public MX record for your mail server.

> **Palu said:**
> Perhaps mail all gets stored in a folder as text attachments, and I would need to write a program on a 15 minute repeating cron tab to parse, push to the database, then delete the email.That would be another way of doing it. Whether synchronous (my suggestion) or asynchronous (your suggestion) processing is best is up to you.



If I were you, I would divide the task in half...

**I - Mail Processing**
Email messages can be quite complicated things to parse, especially when they're carelessly constructed, or contain multipart messages, and so on. Since you know PHP, I would suggest giving it a shot. It has a certain amount of mail parsing capability built in, and it's easy to make it talk to databases. You could try constructing mails like the ones you plan to receive, and piping them through your processing script, to see what happens...```
cat test.eml | ./phpscript
```

**II - SMTP Server**
I would suggest working on the mail server separately, and only after you're sure both the server and your script are behaving themselves, put them together. You could configure your "robot" alias to point to a mailbox for a while, check to make sure mails are delivering as they should, and then point the alias at your script instead.

---

### Post by Palu on 2008-04-24
Thanks. I think I have learned enough to make an attempt. :)

---

