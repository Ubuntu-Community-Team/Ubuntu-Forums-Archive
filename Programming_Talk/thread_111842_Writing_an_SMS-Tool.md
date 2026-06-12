---
title: "Writing an SMS-Tool"
date: 2006-01-03
forum: Programming Talk
---

### Post by doni on 2006-01-03
Hi There!
A happy 2006 to everyone :KS 

Maybe some of you know [sms-star]("http://sms-star.ch.vu/"). A tool which can send sms (texts) over online-services of our local mobile phone providers here in Switzerland (e.g. [Natelskyline]("http://www.natelskyline.ch/pub_asp/pub_content.asp"))  if you've got an account there. 

I would like to write something similiar to this for my personal usage or the usage of others, but it should work on Linux, so I can use it ;) 

Does any of you know, how that works? I don't think that they've got a public API or something!

Thanks for help
doni

---

### Post by dwessell on 2006-01-03
Hi... Well, I can't say to much aboout SMSStar, as I couldn't read their webpage...

However.. You'll need an SMS gateway.. Good luck finding one :) I've been searching for a week for an SMS gateway, that allows 2way messaging, and users to msg back pictures.. But I've not found anything without a large setup fee.

Once you have the SMS gateway, you can write an app around whatever API they have. It's typically going to be SMTP, or HTTP (Post)..

I'm at the point now where I'm just going to build my own gateway... From what I can tell, there's some open source software available, and after that I just need the server and a GSM modem..

I hope that helps some..

---

