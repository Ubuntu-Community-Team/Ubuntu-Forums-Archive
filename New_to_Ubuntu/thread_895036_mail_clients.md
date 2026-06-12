---
title: "mail clients"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ub007 on 2008-08-19
I have installed postfix & courier IMAP on my ubuntu server.Now wish to install a mail client on my client PC to retrieve the mails from the IMAP server.

I was wondering which is the best option

> getmail is a simple mail retrieval agent intended as a replacement for fetchmail, implemented in Python. It can retrieve mail from POP3, IMAP4 and Standard Dial-up POP3 Service servers, with or without SSL.

> fetchmail is an open-source software utility for POSIX-compliant operating systems which is used to retrieve e-mail from a remote POP3, IMAP,

i found this info on the wiki as well as other IMAP clients-Kmail & mozilla Thunderbird....a bit confused now...do they all serve the same purpose..or is there some fundamendal difference between getmail/fetchmail opposed to the Kmail/Thunderbird solutoin(apart from the GUI factor)

like for instance 
mailx is a Unix utility program for sending and receiving mail, also known as a Mail User Agent program. It is an improved version of the mail utility.

> mailx is a lightweight mail program which has a command syntax similar to ed. Mailx allows one to send and read email. **Mailx cannot, by itself, receive email from another computer. It reads messages from a file on the local machine, which are delivered there by a local delivery agent such as procmail.**

are getmail and fetchmail stand alone utilities that would enable me to access & read mails from the IMAP server on my client PC?

---

### Post by Cheesehead on 2008-08-19
If you're looking for a mail client for the *mail server*, you shouldn't need a mail backend to communicate with the distant server. Installing one shouldn't hurt, though.

If you're looking for a mail client for the *non-server*, then you do need an smtp backend.

Happily, in the Ubuntu world, your backend is already suggested by the client you want. Unless you have good reason, just let it go with the default.

For super-lightweight command-line e-mail, I use 'nail' for mail and 'ssmtp' for backend - and they work great. Easy to script, too.

---

### Post by Sorivenul on 2008-08-19
> **Cheesehead said:**
> For super-lightweight command-line e-mail, I use 'nail' for mail and 'ssmtp' for backend - and they work great. Easy to script, too.
+1 for both of these.  Keeps things fast and light.

---

### Post by ub007 on 2008-08-19
> If you're looking for a mail client for the mail server, you shouldn't need a mail backend to communicate with the distant server. Installing one shouldn't hurt, though.

If you're looking for a mail client for the non-server, then you do need an smtp backend.

Happily, in the Ubuntu world, your backend is already suggested by the client you want. Unless you have good reason, just let it go with the default.

For super-lightweight command-line e-mail, I use 'nail' for mail and 'ssmtp' for backend - and they work great. Easy to script, too.

To be honest ,i didnt understand the mail backend  part.Anyways,this is what i have at the moment...
An intranet of 10 PCs-all ubuntu;no internet access.I have installed a mail server(postfix + courier-imap) on on one of the machines.
So now i need to connect to the imap server from my clients and retrieve mails.Obviously that will require a mail client;came across getmail,fetchmail n lotta GUI stuff like thunderbird & kmail and was struggling to find what the major differnce between these clients....In the context of my n/w could anyone tell me what the fundamendal difference is between using a getmail/fetchmail and a t-b/kmail....

---

### Post by ub007 on 2008-08-19
Tell ya what nail seems to be the best solution- super-lightweight !

Could you tell me how to configure it for imap.....?

n secondly i came across this 'Nail supports POP3, IMAP, and SMTP out of the box, so there's no need for further programs like Fetchmail or Postfix'

So have i wrongly assumed 'fetchmail and getmail are mail clients;infact they are MTAs like postfix & exim,or am i still missing something...

---

