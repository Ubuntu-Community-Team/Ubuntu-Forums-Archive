---
title: "[SOLVED] Mail sent from my website"
date: 2008-11-19
forum: Programming Talk
---

### Post by Maratonda on 2008-11-19
Why do I have this header in email sent from my website?

MIME-Version: 1.0

Content-Transfer-Encoding: 8bit

Message-Id: <20081119190138.23270454EA@997642e3.fb.joyent.us>
Date: Wed, 19 Nov 2008 19:01:38 +0000 (GMT)

---

### Post by snova on 2008-11-19
The obvious question I ask is, which header in particular? There are four. Or all of them?

Well, the first one looks like a version number, presumably to help compatibility with different versions.

The second is just an encoding declaration.

The third... no idea what that means.

The last one is just a date...

---

### Post by Maratonda on 2008-11-19
All of them are not part of the message I need to send...the code looks like this:
> 		$headers = "From: \"$sitename\" <$from>\n"
			. "Content-Type: text/plain; charset=UTF-8; format=flowed\n"
    		. "MIME-Version: 1.0\n"
    		. "Content-Transfer-Encoding: 8bit\n";

---

### Post by snova on 2008-11-19
Ah...

The first thing I think of is that the program you use to send mail is adding them automatically.

The second thing I think of is, how do you know? Perhaps your email client added them. I know mine adds a few things...

I don't know much about the inner workings of email, though.

---

### Post by tomchuk on 2008-11-19
Your MTA has added the Message-Id and Date headers as it should.

---

### Post by Maratonda on 2008-11-19
Right, but why is it showing the headers in the message body?

---

### Post by drubin on 2008-11-19
> **Maratonda said:**
> Right, but why is it showing the headers in the message body?

Maybe post a little bit more of your code/details maybe the email. (the full source email). We are all kinda in the dark on this one until you provide us with some more information.

Maybe also take a look at my sig for how to ask questions. ie provide as much information as possible this will help us to help you.

---

### Post by Maratonda on 2008-11-19
Yes, sorry for the confusion...

I'm using an open-source community builder named [elgg]("http://elgg.org/") for a small community I want to set up, therefore I did not write the code for it.

When the system sends out registration emails, the following > MIME-Version: 1.0

Content-Transfer-Encoding: 8bit

Message-Id: <20081119190138.23270454EA@997642e3.fb.joyent.us >
Date: Wed, 19 Nov 2008 19:01:38 +0000 (GMT)

shows up on the email's body.

The PHP code that generates it is:

> 		$headers = "From: \"$sitename\" <$from>\r\n"
			. "Content-Type: html/text; charset=UTF-8; format=flowed\r\n"
    		. "MIME-Version: 1.0\r\n"
    		. "Content-Transfer-Encoding: 8bit\r\n";



then there is of course *mail($to, $subject, wordwrap($message), $headers);*


This is the code of the email I receive on my gmail account:

> Delivered-To: [email]xxx.yyy@gmail.com[/email]
Received: by 10.142.126.19 with SMTP id y19cs322754wfc;
        Wed, 19 Nov 2008 12:57:29 -0800 (PST)
Received: by 10.142.11.20 with SMTP id 20mr746454wfk.62.1227128249038;
        Wed, 19 Nov 2008 12:57:29 -0800 (PST)
Return-Path: <www@997642e3.fb.joyent.us>
Received: from smtp1.fb.joyent.us (smtp1.fb.joyent.us [8.7.217.8])
        by mx.google.com with ESMTP id 30si87563wfa.1.2008.11.19.12.57.28;
        Wed, 19 Nov 2008 12:57:28 -0800 (PST)
Received-SPF: pass (google.com: domain of [email]www@997642e3.fb.joyent.us[/email] designates 8.7.217.8 as permitted sender) client-ip=8.7.217.8;
Authentication-Results: mx.google.com; spf=pass (google.com: domain of [email]www@997642e3.fb.joyent.us[/email] designates 8.7.217.8 as permitted sender) smtp.mail=www@997642e3.fb.joyent.us
Date: Wed, 19 Nov 2008 12:57:28 -0800 (PST)
Message-Id: <6vp7fs$1qi880@smtp1.fb.joyent.us>
Received: from unknown (HELO 997642e3.fb.joyent.us) ([8.17.80.203])
  by smtp1.fb.joyent.us with ESMTP; 19 Nov 2008 12:57:29 -0800
Received: by 997642e3.fb.joyent.us (Postfix, from userid 80)
	id A146A454FE; Wed, 19 Nov 2008 20:57:28 +0000 (GMT)
To: [email]xxx.yyy@gmail.com[/email]
Subject: Alessandro Plasmati invited you to B.O.S.S. Community
From: "B.O.S.S. Community" <noreply@997642e3.fb.joyent.us>
[COLOR="Red"]
Content-Type: text/plain; charset=UTF-8; format=flowed

MIME-Version: 1.0

Content-Transfer-Encoding: 8bit

Message-Id: <20081119205728.A146A454FE@997642e3.fb.joyent.us>
Date: Wed, 19 Nov 2008 20:57:28 +0000 (GMT)


Hello afwoe,	

Alessandro Plasmati has invited you to the B.O.S.S. Community network website.

If you want to join the community, click the following link: 

[http://997642e3.fb.joyent.us/community/action/invitations/register?i=18&c=c3a10882](http://997642e3.fb.joyent.us/community/action/invitations/register?i=18&c=c3a10882)

This mail was generated automatically. Please do not reply to it.



Here is a message from the user that invited you:



asd[/COLOR]


In red there is the body of the message.

There is [this]("http://groups.google.com/group/elgg-development/browse_thread/thread/82349c45aeffa280/34c296223b7a2e51?lnk=gst&q=headers#34c296223b7a2e51") post on the elgg group but nobody gives a solution...

Last thing I forgot to add: it has to do with elgg, because I installed wordpress and emails from wordpress are fine.

---

### Post by drubin on 2008-11-19
You should be able to resolve this issue by removing \r in \r\n in windows it requires you to have both a return and a newline feed in unix/line a simple newline will surfise. **unix \n is the new line char.**

Emails are made up of the headers and then a SINGLE blank line to reparate the email body, Having both the \r\n adds a 2newlines between the lines and such would end the header information.

Hope this helps you. 

Ps thanks for the much more details question.

**EDIT:**
Unix/linux newline char=\n  sorry I forgot that :)

---

### Post by Maratonda on 2008-11-19
Medal for you man, problem solved.
And by the way, it's always Windows' fault!!

---

### Post by drubin on 2008-11-19
> **Maratonda said:**
> Medal for you man, problem solved.
And by the way, it's always Windows' fault!!

I actually blame the code on this one. If I were you I would submit this back to them as a bug. As I am sure they have windows only control chars all over their code. This would be your way of giving back since you are a user of the OSS. 

I used to remember there being a constant for EOL but I cant seem to find it now. O well maybe some one else will find it.

---

### Post by drubin on 2008-11-19
I think it is  [PHP_EOL ]("http://pear.php.net/reference/PHP_Compat-1.3.0/PHP_Compat/_PHP_Compat-1.3.0_Compat_Constant_PHP_EOL_php.html") but not 100% sure if that is only for the pear packages or not.

---

### Post by drubin on 2008-11-23
> **Maratonda said:**
> Medal for you man, problem solved.
And by the way, it's always Windows' fault!!

Did you ever submit this bug upstream?

---

### Post by Maratonda on 2008-11-23
It was submitted to the elgg development team, I do not actually know if there is some other PHP module that is actually causing it!

---

### Post by drubin on 2008-11-23
> **Maratonda said:**
> It was submitted to the elgg development team, I do not actually know if there is some other PHP module that is actually causing it!

I tried to look for the bug re-port but I couldn't find it can you add the link here? (or was it just an email)?

Nice that is the way things in opensource work!! help them to help us.

---

### Post by Maratonda on 2008-11-23
On a second thought, I made the assumption that the guy who replied to me has submitted it to the bug tracker, which could probably be wrong!

[http://groups.google.com/group/elgg-development/browse_thread/thread/f1ea263b3df3576d/0f0af41992f30a30?lnk=gst&q=headers#0f0af41992f30a30](http://groups.google.com/group/elgg-development/browse_thread/thread/f1ea263b3df3576d/0f0af41992f30a30?lnk=gst&q=headers#0f0af41992f30a30)

---

### Post by drubin on 2008-11-23
> **Maratonda said:**
> On a second thought, I made the assumption that the guy who replied to me has submitted it to the bug tracker, which could probably be wrong!

[http://groups.google.com/group/elgg-development/browse_thread/thread/f1ea263b3df3576d/0f0af41992f30a30?lnk=gst&q=headers#0f0af41992f30a30](http://groups.google.com/group/elgg-development/browse_thread/thread/f1ea263b3df3576d/0f0af41992f30a30?lnk=gst&q=headers#0f0af41992f30a30)

That assumption I think is wrong looking at the bug tracker.

Where you the first/second/third person? Ie did you help the others after seeing the answer here? If you did well done :)

---

### Post by Maratonda on 2008-11-23
I actually asked the question, but now I'm going to post the bug to the tracker...

EDIT: there we go...

[http://trac.elgg.org/elgg/ticket/579](http://trac.elgg.org/elgg/ticket/579)

---

### Post by drubin on 2008-11-23
> **Maratonda said:**
> I actually asked the question, but now I'm going to post the bug to the tracker...

EDIT: there we go...

[http://trac.elgg.org/elgg/ticket/579](http://trac.elgg.org/elgg/ticket/579)

NICE.: I suggest you add this, and the google groups link to that report so they can view full explanations/history as well.  :)

---

