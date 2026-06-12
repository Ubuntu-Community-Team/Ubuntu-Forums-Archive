---
title: "Problem sending email in Evolution"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by panand178 on 2008-06-18
Whenever I try sending email in evolution I am getting this weird error:

> 
Error while performing operation.

RCPT TO <anand@gmail.com> failed: [http://www.spamhaus.org/query/bl?ip=122.169.13.39](http://www.spamhaus.org/query/bl?ip=122.169.13.39)

I am able to receive emails fine and the problem is only when I am trying to send emails. 

The email account is my official email id. I also checked with my System Admin at work. He said that in MS Office Outlook I need to check the "Server Required Authentication" and select the "Receive before send" option. In Evolution I am assuming that this translates to the "POP before SMTP" option. But this does not seem to work. 

I am using Hardy and Evolution 2.22.2

Any help is much appreciated!

---

### Post by kool_kat_os on 2008-06-18
looks like youre blacklisted....

---

### Post by prshah on 2008-06-18
> **panand178 said:**
> 
I am able to receive emails fine and the problem is only when I am trying to send emails. 

 I need to check the "Server Required Authentication" and select the 


> 
Outbound Email Policy of The Spamhaus Project for this IP range:

This IP range has been identified by Spamhaus as not meeting our policy for IPs which should deliver 'direct-to-mx' mail to PBL users.

Important: If you are using any normal email software such as Outlook, Entourage, Thunderbird, Apple Mail, and you are being blocked by this Spamhaus PBL listing when you try to send email, the reason is simply that you need to turn on "SMTP Authentication" in your email software settings (Tools : Accounts : Properties : Outgoing Mail Server : check "My server requires authentication").
If you do not know how to do this, ask your Internet Service Provider for help with "SMTP Authentication".

You don't need to do "Receive before send" for GMail. But you do need SMTP Authentication. I'm using Thunderbird, but can let you know the procedure for Evolution after checking my laptop tomorrow.

btw (irrelevant to topic at hand): John Galt is the man who stopped the motor of the world. (Oh this is going to confuse the hell out of people when you change your signature in the future!)

---

### Post by panand178 on 2008-06-20
> **kool_kat_os said:**
> looks like youre blacklisted....

How could I possibly have gotten blacklisted? Meaning its my official email-id!! :confused:

Do you have any idea how this may have happened?

---

### Post by panand178 on 2008-06-20
> **prshah said:**
> You don't need to do "Receive before send" for GMail. But you do need SMTP Authentication. I'm using Thunderbird, but can let you know the procedure for Evolution after checking my laptop tomorrow.


I am not using Evolution for gmail, it is for my official email id. It would be great if you could send across the details. There's no harm in trying rite? :)

> **prshah said:**
> 
btw (irrelevant to topic at hand): John Galt is the man who stopped the motor of the world. (Oh this is going to confuse the hell out of people when you change your signature in the future!)

I know who John Galt is. This particular term "Who is John Galt?" is used as a statement of despair and hopelessness in Atlas Shrugged if you remember. But I use it just for the simple fact that i like it and at times (for instance with the problem that I am facing) it fits in perfectly well with the the actual meaning too... :)

---

### Post by tysonh on 2008-06-20
I've been having problems with evolution myself.  I just downloaded thunderbird using the synaptic package manager and had it working with gmail in under 2 mins.  Thunderbird is a email app made by the same people who make firefox.  Works and looks good.

Give thunderbird a try it might save you a few headaches.

---

### Post by alexandremrj on 2008-06-20
You need to edit SMTP autenthication

so go to Evolution and "Edit" menu, choose "Preferences", select "Email accounts" on the left bar and then choose your email account and press "edit" button on the right.

In the new window that appears go to the fourth tab "Sending Email"

See that server type is SMTP and that in the smtp configuration the box "Server requires autenthication" is checked, press OK the Close on the next window and make a test run.

---

### Post by prshah on 2008-06-20
> **panand178 said:**
> How could I possibly have gotten blacklisted? Meaning its my official email-id!! :confused:


Relax. It's _not_ blacklisted.

> **panand178 said:**
> I am not using Evolution for gmail, it is for my official email id. It would be great if you could send across the details. There's no harm in trying rite? :)

In Evolution, click Edit-Preferences-Mail Accounts-(Your account)-Edit-Sending Email-check (tick) "Server requires authentication".

Note that if you are trying to send over your office smtp server, but using your gmail id as "from" then it's most likely going to fail. (Technical talk: smtp-relay disallowed). To workaround this situation, keep your "from" as the email address supplied by your admin, and enter your gmail address in the reply field. If you are _not_ using your gmail as "from" _or_ not using your office SMTP server (using gmail smtp server) then you need not worry about this.

---

### Post by panand178 on 2008-06-20
> **prshah said:**
> In Evolution, click Edit-Preferences-Mail Accounts-(Your account)-Edit-Sending Email-check (tick) "Server requires authentication".

Note that if you are trying to send over your office smtp server, but using your gmail id as "from" then it's most likely going to fail. (Technical talk: smtp-relay disallowed). To workaround this situation, keep your "from" as the email address supplied by your admin, and enter your gmail address in the reply field. If you are _not_ using your gmail as "from" _or_ not using your office SMTP server (using gmail smtp server) then you need not worry about this.

1. I have chosen the "Server requires authentication" option.
2. I'm not trying to use my gmail id anywhere. It's not there in the picture at all. All I need is to be able to send mails using my official id.

> **alexandremrj said:**
> You need to edit SMTP autenthication

so go to Evolution and "Edit" menu, choose "Preferences", select "Email accounts" on the left bar and then choose your email account and press "edit" button on the right.

In the new window that appears go to the fourth tab "Sending Email"

See that server type is SMTP and that in the smtp configuration the box "Server requires autenthication" is checked, press OK the Close on the next window and make a test run.

I've already tried this out with both "Server requires authentication" checked and unchecked. Still no luck!

---

### Post by alexandremrj on 2008-06-20
What is the information that was supplied about the smtp server you are supposed to use?

Server:
Port:
Encryption:

---

### Post by panand178 on 2008-06-22
> **alexandremrj said:**
> What is the information that was supplied about the smtp server you are supposed to use?

Server:
Port:
Encryption:

Here is a screenshot of my send mail options:

[ATTACH]74921[/ATTACH]

I have removed my SMTP server since I dont want to take a risk and like I told you it is my official email id.

---

### Post by alexandremrj on 2008-06-23
Hello,

sorry for the late reply.

Looking thru your screenshot i think i see the problem but you will have to test it.

From the previous posts i see that you need secure authentication and as such you need to select in the "security" part Use Secure authentication (i believe that TLS encryption will work for you).

Also, in authentication i would recommend to press the "Check for supported types" button, so that you will see if the POP before SMTP works.

---

### Post by panand178 on 2008-06-23
No my SMTP server does not support TLS. I am getting the following error. 

> Error while performing operation.

Failed to connect to SMTP server in secure mode: STARTTLS not supported
Also when I click on "Check for Supported Types" I can still see the "Pop before SMTP option"

---

### Post by Canis familiaris on 2008-06-23
Try changing SMTP port to 587

---

### Post by panand178 on 2008-06-23
> **Anurag_panda said:**
> Try changing SMTP port to 587

No Luck! :(

---

### Post by sostenible on 2008-08-23
I have found a bug in Evolution: if I automatically include a signature to my messages, these will never reach some addresses (mainly for public agencies), however Evolution provides no error message and the sent message appears in the "sent messages" carpet of evolution.

I found out because I myself work at a public agency and my wife too (in a different one: a ministry).

I thought it was an ubuntu problem, but I get the same problem using evolution in Suse and DestopBSD.

No problem if sending from Evolution choosing "no signature" or from Outlook Express.

It's got nothing to do either with including or not images or links into the signature.

Any hints? Also, any one knows where can I inform about this bug in order that evolution developers can solve it?

---

### Post by haydemon on 2008-09-05
> **Anurag_panda said:**
> Try changing SMTP port to 587
I started having the sending problem in Evolution just yesterday, after using it successfully for months! I didn't change anything. Just after coming back from the wk-end, it stopped working. I can send, but cannot receive. I've reconfigured the account several times with the correct information (provided by my IT Admin), and still no send. My server is SMTP, requires authentication, and the port is in fact 587; however, I see nowhere where I can indicate the port under Edit --> Preferences -->Mail Accounts. HELP!

---

### Post by halitech on 2008-09-05
are you using a laptop that you have taken home (or other computer at home) to send email from your work (whatever that may be) email address?

if yes, are you trying to use your works outgoing mail server?

if yes to above, have you tried either a. contacting your ISP and seeing if they are blocking other SMTP servers or b. using your ISPs outgoing mail server?

the reason I'm asking is because alot of mail servers are starting to lock down using other servers (ie, possibly windows infected computer sending viruses or spam) so you have to use their mail server in order to send email.

---

### Post by haydemon on 2008-09-05
Nope. I'm using my desktop computer at work. Just like always. It's very strange... When I came back from vacation, I couldn't get online or anything. Then I rebooted, changed a few settings (deselected "allow roaming" from my network settings), and my internet connections came back, as well as my ability to SEND email, but nevermore to RECEIVE. I've since then switched to Thunderbird--at least for the time being--but I have all my contacts and saved emails in Evolution. Quite a drag!:mad:

---

### Post by halitech on 2008-09-05
what happens when you try to recieve email?

---

### Post by haydemon on 2008-09-08
> **halitech said:**
> what happens when you try to recieve email?
I can receive mail, but it gets hung when trying to send.

---

### Post by halitech on 2008-09-08
> **haydemon said:**
> Nope. I'm using my desktop computer at work. Just like always. It's very strange... When I came back from vacation, I couldn't get online or anything. Then I rebooted, changed a few settings (deselected "allow roaming" from my network settings), and my internet connections came back, as well as my ability to SEND email, but nevermore to RECEIVE. I've since then switched to Thunderbird--at least for the time being--but I have all my contacts and saved emails in Evolution. Quite a drag!:mad:

> **haydemon said:**
> I can receive mail, but it gets hung when trying to send.

in the first post you said you could send but not receive and then you say you can receive but not send so which are you having a problem with and in what program?

---

### Post by haydemon on 2008-09-08
> **halitech said:**
> in the first post you said you could send but not receive and then you say you can receive but not send so which are you having a problem with and in what program?
I'm sorry for the confusion! I've always been able to RECEIVE. I'm having a problem with Sending. Program is Evolution. OS is Ubuntu Hardy Heron. It started happening without apparent reason.:(

---

### Post by halitech on 2008-09-09
ok, try this and post the results. Open a terminal and type in```
telnet smtp.mailserver.com 25
```

replace smtp.mailserver.com with whatever the outgoing mail server is. Also, if its not using the standard port of 25, change that to whatever is being used. You should get something like this:```
daryl@ubuntu:~$ telnet smtp.gmail.com 587
Trying 209.85.199.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP f42sm9713513rvb.6
```

---

### Post by haydemon on 2008-09-09
Trying 74.208.5.2...
Connected to smtp.1and1.com.
Escape character is '^]'.
220 smtp.perfora.net (mrus1) Welcome to Nemesis ESMTP server

This is what I got (above).

---

### Post by halitech on 2008-09-09
ok, that tells us the route to the mail server is clear and the server address is correct and the DNS is working properly (it found the mail server at the IP address)

Since there is no problem with the server, the issue is with Evolution. Have you tried recreating the account?

---

### Post by haydemon on 2008-09-09
> **halitech said:**
> ok, that tells us the route to the mail server is clear and the server address is correct and the DNS is working properly (it found the mail server at the IP address)

Since there is no problem with the server, the issue is with Evolution. Have you tried recreating the account?
I tried recreating the outgoing server settings on the account, not the entire account. I'm afraid to lose a bunch of emails I have already stored in this account if I delete it & recreate it (messages already been deleted from the server).

---

### Post by halitech on 2008-09-09
how did you "recreate" the outgoing server settings?

---

### Post by haydemon on 2008-09-09
> **halitech said:**
> how did you "recreate" the outgoing server settings?
I erased the original settings and re-entered them (smtp.1and1.com, port 587, unencrypted,plain authenticaton).

---

### Post by halitech on 2008-09-09
try setting them to gmails settings, then try to send an email and then change them back to your original settings

---

### Post by haydemon on 2008-09-09
OK. I&#314;l do it tomorrow from the office (at home right now). Thx!

---

### Post by haydemon on 2008-09-10
If finally worked! I deleted the account and set it up again (with the same settings I had before), and this time it worked. I am receiving AND sending emails with Evolution again! Thanks all for your help.:lolflag:

---

### Post by halitech on 2008-09-10
glad to hear its working. Don't forget to mark the thread solved so others will know :)

---

### Post by haydemon on 2008-09-10
> **halitech said:**
> glad to hear its working. Don't forget to mark the thread solved so others will know :)
where do I mark it? I was looking around, but couldn't find where to do it. I thought maybe there was an administrator or something like that who did those things... :confused:

---

### Post by halitech on 2008-09-10
if you look up at the top you'll see where it says Thread tools, click that and you should have an option to mark as solved

---

### Post by haydemon on 2008-09-11
I don't get that option. :(

---

### Post by haydemon on 2008-09-11
> **haydemon said:**
> OK. I&#314;l do it tomorrow from the office (at home right now). Thx!
It's not my original thread, that's probably why.

---

### Post by halitech on 2008-09-11
right, I forgot you added on afterwards :) no worries then, the OP will when they get a chance I get

---

