---
title: "[SOLVED] Looking for a new Email Client"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by nixforme on 2008-11-26
Hi,

I have been looking for a new email client and I just cant choose. For my email service I currently use Gmail. And for a client I ave been using a combination of the web interface and Mutt. I myself love Mutt. It is just so easy to use. But it does have its disadvantages. For example, I cant see my labels. Another one is that it seems a bit slow for IMAP. But I guess that would be true for what ever client I choose. So I am asking for recommendations on a new client. What do you all use? I am looking for all types of clients, weather it be a command line client or a regular client. SO what do you all recommend?

---

### Post by SpenceMakesSense on 2008-11-26
thunderbird is great with gmail. Its probably the easiest to setup.

---

### Post by jamesrfla on 2008-11-26
Thunderbird would be your best bet.

---

### Post by MenZa on 2008-11-26
I'm going to go against the two other replies in this thread and recommend Evolution. Lots of features, easy integration with Exchange servers, calendar and everything built-in. It comes pre-installed with Ubuntu.

---

### Post by kestrel1 on 2008-11-26
Another vote for Thunderbird. That is all I use these days. All emails set to IMAP & works great.
Thunderbird is easy to install:
```
sudo apt-get install thunderbird
```

---

### Post by wieman01 on 2008-11-26
Thunderbird.

I always wanted to try out Evolution but have not had the guts yet. I am sure it's also worth a try!

---

### Post by nhasian on 2008-11-26
enable IMAP in your gmail account and install thunderbird

```
sudo apt-get install thunderbird
```

the instructions to setup Thunderbird with Gmail are here:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=77662](http://mail.google.com/support/bin/answer.py?hl=en&answer=77662)

after you've done that, you should also follow the steps for Recommended IMAP client settings here:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=78892#](http://mail.google.com/support/bin/answer.py?hl=en&answer=78892#)

---

### Post by andrew.46 on 2008-11-26
Hi,

Have you thought of trying mutt without IMAP? If you use pop3 over ssl with for example fetchmail, procmail and msmtp it is very fast.

  Andrew

---

### Post by halitech on 2008-11-26
I use thunderbird and evolution, found both easy to set and use with both gmail and other providers.

---

### Post by nixforme on 2008-11-26
> **andrew.46 said:**
> Hi,

Have you thought of trying mutt without IMAP? If you use pop3 over ssl with for example fetchmail, procmail and msmtp it is very fast.

  Andrew

Would I follow your guide in your sig to set that up?

---

### Post by nixforme on 2008-11-26
> **MenZa said:**
> I'm going to go against the two other replies in this thread and recommend Evolution. Lots of features, easy integration with Exchange servers, calendar and everything built-in. It comes pre-installed with Ubuntu.

Just to let you know. Evolution DOES NOT work with Exchange 2007.

---

### Post by HittingSmoke on 2008-11-26
Evolution is nice as it integrates with a lot of other Ubuntu programs. I do however prefer Thunderbird. Four out of five dentists recommend it.

And IMHO, the Gmail web interface is better than using POP3. IMAP is the way to go for email clients

---

### Post by nixforme on 2008-11-26
> **nhasian said:**
> enable IMAP in your gmail account and install thunderbird

```
sudo apt-get install thunderbird
```

the instructions to setup Thunderbird with Gmail are here:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=77662](http://mail.google.com/support/bin/answer.py?hl=en&answer=77662)

after you've done that, you should also follow the steps for Recommended IMAP client settings here:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=78892#](http://mail.google.com/support/bin/answer.py?hl=en&answer=78892#)

Ok I looked at the re commanded settings but how the heck do I even configure what they are asking. Sorry it that i a stupid question. I am just a bit confused and what they are wanting.

---

### Post by nixforme on 2008-11-26
> **HittingSmoke said:**
> Evolution is nice as it integrates with a lot of other Ubuntu programs. I do however prefer Thunderbird. Four out of five dentists recommend it.

And IMHO, the Gmail web interface is better than using POP3. IMAP is the way to go for email clients

I agree with you there. I am looking for a more professional/integrated kinda feel for me. The web interface is a little boring to me.

---

### Post by andrew.46 on 2008-11-26
Hi,

> **nixforme said:**
> Would I follow your guide in your sig to set that up?

That certainly reflects my own setup and might be worth a try for you. That guide uses ssmtp rather than msmtp but has worked well for me for some time. Settings for msmtp can be seen on my [web site version]("http://www.andrews-corner.org/mutt.html") of this guide.

I know IMAP is the current flavour of the month but I have a strong dislike for it. Not the least because it represents a breakdown of the traditional [mail concept]("http://wiki.mutt.org/?MailConcept").

Andrew

---

### Post by nhandler on 2008-11-26
Another email client that you can try is [Claws Mail]("http://www.claws-mail.org/"). I personally do not use it, but I know many Ubuntu users who love it. It also supports [plugins]("http://www.claws-mail.org/plugins.php?section=downloads") and [themes]("http://www.claws-mail.org/themes.php?section=downloads").

Claws Mail (claws-mail) is in the Ubuntu repositories. There are also many claws-mail-* packages in the repositories that you should look at.

---

### Post by nixforme on 2008-11-26
> **andrew.46 said:**
> Hi,



That certainly reflects my own setup and might be worth a try for you. That guide uses ssmtp rather than msmtp but has worked well for me for some time. Settings for msmtp can be seen on my [web site version]("http://www.andrews-corner.org/mutt.html") of this guide.

I know IMAP is the current flavour of the month but I have a strong dislike for it. Not the least because it represents a breakdown of the traditional [mail concept]("http://wiki.mutt.org/?MailConcept").

Andrew

In your opinion which is better to use, ssmtp or msmtp?

---

### Post by nixforme on 2008-11-26
Has any one ever used GMAIL with Alpine?

---

### Post by nixforme on 2008-11-26
> **andrew.46 said:**
> Hi,



That certainly reflects my own setup and might be worth a try for you. That guide uses ssmtp rather than msmtp but has worked well for me for some time. Settings for msmtp can be seen on my [web site version]("http://www.andrews-corner.org/mutt.html") of this guide.

I know IMAP is the current flavour of the month but I have a strong dislike for it. Not the least because it represents a breakdown of the traditional [mail concept]("http://wiki.mutt.org/?MailConcept").

Andrew

I have to agree with you about IMAP in a way. Lately it has failed me becasue I seem to have lost some mail.

---

### Post by nixforme on 2008-11-26
> **nhandler said:**
> Another email client that you can try is [Claws Mail]("http://www.claws-mail.org/"). I personally do not use it, but I know many Ubuntu users who love it. It also supports [plugins]("http://www.claws-mail.org/plugins.php?section=downloads") and [themes]("http://www.claws-mail.org/themes.php?section=downloads").

Claws Mail (claws-mail) is in the Ubuntu repositories. There are also many claws-mail-* packages in the repositories that you should look at.

Hmmm, seems interesting. Ill give it a shot. Thanks.

---

### Post by nhasian on 2008-11-26
actually if you just click on the *Thunderbird 2.0* link in the webpage it opens up to show thunderbird specific instructions on how to do it.

> **nixforme said:**
> Ok I looked at the re commanded settings but how the heck do I even configure what they are asking. Sorry it that i a stupid question. I am just a bit confused and what they are wanting.

---

### Post by andrew.46 on 2008-11-27
Hi nixforme,

> **nixforme said:**
> In your opinion which is better to use, ssmtp or msmtp?

I have used both and both are fine programs. (ssmtp has not been developed for a while I think you may find though.) If your purpose is only to send a little mail from your system to a single server then ssmtp is perfect and requires no upkeep and only a simple config file. I started with ssmtp + gmail a few years ago running mutt and slrn with a single mail account and had zero problems. 

If your needs are a little more complex, you need multiple accounts for example, then msmtp would serve you a little better.

  Andrew

---

### Post by lordCovenant on 2008-11-27
Thunderbird for me. . .fast and easy installation! and has no problems with my gmail account.
I've tried Evolution but can't get all emails that I have. . :(
So, I made a switch and im a happy ubuntu user now! :)

---

### Post by c2olen on 2008-11-27
I've been using both Evolution and Thunderbird alongside eachother for a while because I could not make a final decision. In the end I choose Thunderbird because it works just a tad faster, and has a nicer interface (a matter of taste though). 
I use kerio mailserver as a primairy mail account and have a couple of others in use as well, including gmail. All using secure IMAP.
Thunderbirds integrates the email address lookup in LDAP just a bit better than Evolution. It looks up the names as you type and suggest all possible matches. In Evolution I  have to use the search option for every address i'd like to send my mail to (this could also be my lack of evolution know-how).

I've read several articles on Claws-Mail too, and it should be a nice alternative as well. I have no experience on Claws however. I will give it a try.

Cheers and good luck making a decision.

---

### Post by nixforme on 2008-12-03
Thanks for the info all. It looks like Thunderbird has one!

---

### Post by stchman on 2008-12-03
I use Evolution for all my email needs.  Granted my email is POP so it is really easy to setup.

I used to use Outlook and I find the interface very familiar and intuitive.  I also use to use Thunderbird as well.

---

### Post by nixforme on 2008-12-04
I changed my mind. I am going to use Evolution and Mutt.

---

### Post by philinux on 2008-12-04
I just gave evolution a go on my spare email address. What's a default keyring password as is not my admin password.

Also it crashes. Not impressed by first impressions.

---

