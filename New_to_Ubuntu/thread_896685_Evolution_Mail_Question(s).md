---
title: "Evolution Mail Question(s)"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by jfbays on 2008-08-21
Is there a _detailed_ tutorial for setting up Evolution Mail?  I looked at the Setup Assistant, but I don't quite understand what it's asking for -- which email address, server type, server configuration, etc..  I guess what I'm looking for is a "Setup Evolution Mail For Dummies" type of thing...

While looking through the forum, I saw a mention of "Thunderbird".  Is that an alternative to EM, or is it something else?

---

### Post by Titan8990 on 2008-08-21
Thunderbird is a cross platform MUA (Mail User Agent). Thunderbird will require the same set up steps and Evolution.

Is this your first time configuring a mail client?

> which email address, server type, server configuration

What is your email address (don't answer that on the forums)?

What type of server does your mail service provide? IMAP? POP? If it is a free mail service such as yahoo, this will most likely be POP. If it is your ISP they most likely offer both.

Does your mail service use encyption? TLS/SSL?


What I am trying to get at here is that it sounds like you don't know the right information about your email service, not that you don't know how to set it up.

---

### Post by jfbays on 2008-08-21
Yes, this is my first time trying to set up an email client, other than signing up and making up a handle...

And yes, I don't know the right information.  Where would I get it?

---

### Post by Titan8990 on 2008-08-21
Typically, you can guess. For example if you have email through foobar.com (yes that is made up), then you can take a guess that their POP server is: pop.foobar.com. 


What mail service are you using?

---

### Post by DFord425 on 2008-08-21
I know that if you look around gmail it says what type of server it is, thats how i setup thunderbird. Yahoo, i believe, you have to have an account you pay for for them to give you that info.(I could be wrong about yahoo, but i know it was not readily availible to me). If you look around what ever mail service you have, you could probably find the server type, or information about how to get it.

PS if you use gmail, if you log into your gmail account and go to settings, it will tell you about the server types.

---

### Post by jfbays on 2008-08-21
I'll give it another try...

---

### Post by jfbays on 2008-08-22
Perhaps I don't understand the concept of Evolution Mail.  Am I setting up a brand new email account with a new email address that goes through my internet provider, OR am I simply tying into (linking to) an existing email account that will be channeled through Evolution Mail?  I know this question shows my ignorance, but please answer, so I will at least have some idea of what I'm trying to do with EM... Thanks.

---

### Post by Cheesehead on 2008-08-22
Your *mail client* requires a pre-existing account. It only sends, receives, and stores mail from your account(s). It needs to talk to a *mail server*, provided by your ISP or someone else.

Your *mail account*, including your e-mail address (you@example.com), is assigned to you by the *mail host* (typically your ISP). 'you' are the account, and 'example.com' is the mail host. For example, Gmail is a mail host(provider).

Each *mail host* runs a piece of equipment called a *mail server*, the e-post office.

*Mail servers* send mail to your *mail client* (Evolution) in one of two flavors: POP or IMAP. These flavors are important to you.

*IMAP* means that the mail is kept by the server, and a copy is sent to you. These are used mostly by webmail operators like Gmail or the US Department of Defense. They are handy when you use multiple computers or guest computers but want access to all of your mail at once. No mail is stored locally. For example, Gmail via the web is IMAP.
Your *IMAP mail server*, if you have one, is typically 'imap.company.com' for incoming and outgoing mail.

*POP* means that the server forwards the message to you and usually doesn't keep a copy for itself. You save your own mail on your own computer. POP is often used by older systems, since it dates back to when storage was expensive.
Your *POP mail server*, if you have one, is typically 'mail.company.com' or 'pop.company.com' for incoming messages (stuff sent TO you), and 'mail.company.com' or 'smtp.company.com' for outgoing messages (stuff YOU send out).

YOU DON"T KNOW those server names until your *mail host* tells them to you. Check their website, search for 'e-mail'. It's a very, very common question.

Finally, if you could provide a little more info about the type of setup (POP or IMAP) you *want*, the type of mail host (ISP or Gmail or other), and the type of information you are stuck on, we can help you better.

Of course, we don't need to know your e-mail address, or your ISP, or any other specific info - just the general type is enough.

---

### Post by jfbays on 2008-08-22
Thanks for the great information!  It gave me some idea what information to seek from my ISP.  Unfortunately, the answer I got was this:

> What are Juno's POP and SMTP settings to check Juno email using a dedicated email program? (Juno 5.0)

At this time, you cannot use other email programs to get or send your Juno email. For this reason, Juno's POP3 and SMTP mail server addresses are not available.

I'm assuming that's the end.  But is it?  Are there ways around these things?

---

