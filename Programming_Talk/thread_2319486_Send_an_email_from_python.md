---
title: "Send an email from python"
date: 2016-04-04
forum: Programming Talk
---

### Post by mfvpcrec on 2016-04-04
Hello everybody. I have a simple question for you. I need send an email from a python 
script but not using an existing email  but  from the python script itself. I mean There is
 a way to send an email from python with their own smtp server?

Thanks!

---

### Post by ian-weisser on 2016-04-04
import email. Part of the standard library.

---

### Post by 1clue on 2016-04-04
You can't have tried Google. The first 10 hits from "send an email from python" are on point.

[https://docs.python.org/3/library/email-examples.html](https://docs.python.org/3/library/email-examples.html)

---

### Post by mfvpcrec on 2016-04-06
Yes ian-weisser I saw that module and I know that is useful but I don't  know how use it like I need. I need send an email with its own domain  without using an existing email.

Yes 1clue i tried in Google but i  did not find any  page that explains how send an email with its own  domain without using an existing email , or none  explication worked for  me :'-(

Another thing that I don't get it is this in the examples of python:

```
# Send the message via local SMTP server.
s = smtplib.SMTP('localhost')
```

How?  How I make a local SMTP server?  I mean , that example it is not  stand-alone , the example  need another thing .. a SMTP server... but  How?

Thanks to everyone! Bye!

---

### Post by 1clue on 2016-04-06
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

One could technically write the SMTP code into your python script, but that would be a waste of time. As well there are some really good reasons why it's best not to.

If you're talking about sending mail to you personally, or to someone in your company, then this is not so big a deal.  If you're talking about sending to someone with a gmail account, either in some other company or personal accounts, then you have a whole lot of hoops to jump through. There are a lot of technologies in use to prevent spam from getting into people's inboxes. Not having a legitimate mail server registered to a domain name means most of your mail will wind up in the spam folder when sent to places which advertise spam filtering.

So, I need to ask more detail: Who are the recipients?
[LIST=1]
[*]Local sysadmins on a single mail domain?
[*]In-company coworkers on a single mail domain?
[*]Diverse recipients with diverse mail domains who will make exceptions to not send you to spam?
[*]Diverse recipients who will make no provisions on your account.
[/LIST]

If you're talking about 1 or 2, then you can probably hack something together.

If you're going to include 3 then you'll need a registered domain, a mail server with a fixed IP address and properly configured DNS MX records, and a bunch of other DNS-related entries.
If you're going to include 4, then you'll need everything for 3, and probably a valid SSL certificate from a certificate authority like VeriSign which you'll have to renew every year or two.

---

### Post by 1clue on 2016-04-06
I've written software to send information to paying customers.  There's a lot to this beyond the simple mechanics of sending mail.

The sending mail part is really easy, programmatically speaking. It can be done in a single line of code. The hard part is to do so in a way that:
[LIST=1]
[*]The email gets to their inbox without being marked as spam.
[*]Your mail sending app does not get your IP address listed as a spammer site and thus blocked by pretty much every publicly used mail server (gmail, yahoo, live, ...)
[/LIST]

This has not only to do with what I mentioned above, but also the contents of your message.  Lots of attachments? Spammer. Lots of images? spammer.  Lots of links off to some web site? Spammer.

You can get by with a single link, and maybe a small company logo as an included attachment. Better if it's text-only or html without images. Any links better go back to the domain the mail came from, and the fewer of those the better.

---

### Post by mfvpcrec on 2016-04-06
1clue That was the best answer that I read in my life.
I cant say anything more than thank you.

---

### Post by 1clue on 2016-04-06
Thanks.

To wrap this up I'm going to assume you're talking about server maintenance.  It's typical for computers (servers especially) in a corporate environment to be configured with a local mail transfer agent, or MTA.

This MTA's job is to notify the administrator(s) of the box about any notable activity or condition. The MTA can either be a mail server or it can be a forwarding  mechanism to a mail server, or it could be local mail meaning you have to login to the account on that box in order to get it.

In my experience if you have a mainstream mail server (gmail, etc) then the MTA-forwarded message will not get to you. This includes setting up your own internal mail server.  I recommend that you set up one internal mail server (item 2 above) and create one ore more accounts on it for your admins. Your individual Linux boxes have MTAs which forward all mail to your private server, and then you check the mail on that every now and then, as a separate mail account rather than going through your public email.

I'll also put in a plug on security. If this mail server need not be publicly reachable then don't make it publicly reachable.  No matter what, enforce good password policies on it.  Black-hat hackers think mail servers are delicious. If you're able, consider setting up a personally-generated ssl/tls certificate and have all your systems trust it so you can get encryption. You can then generate certs for all your servers and work without further inconvenience.

---

