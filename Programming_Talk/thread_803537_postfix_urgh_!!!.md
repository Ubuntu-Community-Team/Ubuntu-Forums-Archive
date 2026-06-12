---
title: "postfix urgh !!!"
date: 2008-05-22
forum: Programming Talk
---

### Post by hockey97 on 2008-05-22
Hi I have webmin  and just installed postfix admin which somone on the ubuntu fourm website suggested.

I am trying to config postfix to use mysql for the users and mail dir ect info.

I had postfix working but it was using files  and I couldn't send e-mails to aol or any top e-mail companies users which I found out that I was on a residential list which my ip shows I am in a residential zone which they block to prevent them from getting spam. The company that provided this list allowed you to also take it off the list by a request which I did.

Now this is after I tried to config my postfix to use mysql so when I went to test the mail server sending e-mail to a aol user I got now an error unknown transport map.

Do you know how I can fix this??

I was suggested that postfixadmin would show if anything in the configs is wrong.

which I logged in postfixadmin and I found that my configs were right.

It's just postfix can't see the transport map.


I am trying to make a automated e-mail service. Meaning that when I get new users using php I can update the mysql database which then would provide the information to postfix to add the user and the e-mail address ect and password.

I don't want to have to use a file and have to manually open it and add new yousers and I don't feel like manually changning the configs to add new users and all the info postfix needs to send and recive mail.

Any Ideas??

---

### Post by hockey97 on 2008-05-22
I got the thing to work but I still get refused by aol mail servers.

I get the error refused to talk to .

what does that mean??

how can I send mail from my mail server to a well known mail company?? like aol.??

---

### Post by mssever on 2008-05-23
> **hockey97 said:**
> how can I send mail from my mail server to a well known mail company?? like aol.??
It depends on why you can't send mail to AOL, etc. It's likely that either: 1) Postfix is misconfigured somehow, and/or 2) you're (still) on a spam blacklist. In either case, it's likely an anti-spam measure. (If your SMTP server is misconfigured, it's likely that spammers will find and exploit it. And if that happens, ISPs will (correctly) blame you for it, because anyone who runs a mail server had better know how to run it properly.)

Try Googling the error message you get and see if you learn something from it.

---

### Post by hockey97 on 2008-05-23
ok I done some googling and I found people that are in my situation but never figured it out some are blocked and are on AOL's spam list.

Well I used online mail server testing tools and everything checks out I can even send e-mail from my AOL account to my mail server So it looks like they are blocking me for some reason.

I used some online lookup tools that would check if my ip is on a block list which I found I was clean. I then tested my mail server sending an e-mail to my hotmail account which I got refused but they had a link to the reason which my ip was a residentuar area and they gave the link to what company they use to get the list and then they had a place where I can make a request to get it removed. They then e-mailed me a code which I had to put on there website to complete the removal and then they had a tool on their website which I can do a lookup on my ip address and I found it was clean fully.

now I tried to send an e-mail to  my hotmail account which this time I didn't get any error but it didn't even make it to my hotmail account that e-mail.

Aol gives an e-mail saying I am on a block list due to there users complaining about spam from my ip address.

Which I don't see how this is possible since I never had a mail server up before.

---

### Post by CptPicard on 2008-05-23
> **hockey97 said:**
> my ip was a resident zoning area

Operative words. Residential IP blocks usually just get blanket blocks at the receiving end if your ISP doesn't filter outgoing SMTP to other servers than their own already.

If you really want to run a mail server, get your own proper server somewhere... don't run it out of your bedroom. There is a very good reason why it's reasonable to suspect anything that comes from Average Joe User's computer that looks like outgoing mail is produced by a spambot.

---

### Post by hockey97 on 2008-05-23
> **CptPicard said:**
> Operative words. Residential IP blocks usually just get blanket blocks at the receiving end if your ISP doesn't filter outgoing SMTP to other servers than their own already.

If you really want to run a mail server, get your own proper server somewhere... don't run it out of your bedroom. There is a very good reason why it's reasonable to suspect anything that comes from Average Joe User's computer that looks like outgoing mail is produced by a spambot.

Well the reason I don't want to pay for some hosting company to host my mail server is because I would lose control. It would mean I have to depend on them for my mail server to be up and running. 

Also if AOL is very worried about spam how come I get a buch in my AOL account?
I get spam about 81 e-mails a day that's spam.I also get phishing e-mails at my account.



My main goal is to have a working website and mail server that would be in my control which I can fix any errors that occurs. So for some that will host my website and mail ect then if I get lets say locked out of there system it would take time for me to contact there tech people to fix this and time cost money.

My postfix server is configured right but it's just Aol that is blocking me.

Also I have 2 domain names that use my mail server so it's not like it's coming from a persons bedroom.

---

### Post by CptPicard on 2008-05-23
> **hockey97 said:**
> Well the reason I don't want to pay for some hosting company to host my mail server is because I would lose control.

********. You can have a 100% self-administered server if you want to. If your host won't give you one, you switch hosts. It's that simple.

On the other hand, it doesn't  seem like you *need* the control. It would be far better for you to have your mail hosted for you. Additionally, even though I am capable of running my own mail server, I don't bother because of the work -- I run a fairly big website and *gladly* hand over email hosting to the hosting company because it's just more work off my hands.

I really would love to hear what exactly it is that you're afraid of losing control of.

---

### Post by mssever on 2008-05-23
> **hockey97 said:**
> Also if AOL is very worried about spam how come I get a buch in my AOL account?
I get spam about 81 e-mails a day that's spam.I also get phishing e-mails at my account.Imagine how bad it would be if AOL did nothing.
Try Google Apps. You get Gmail-like access, complete with SMTP--all for free. I use it and it works great.

---

