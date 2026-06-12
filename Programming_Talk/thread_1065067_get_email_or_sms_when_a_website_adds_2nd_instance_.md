---
title: "get email or sms when a website adds 2nd instance of a phrase into a webpage"
date: 2009-02-09
forum: Programming Talk
---

### Post by hanzj on 2009-02-09
Hello.


 I need to be able to track when a website [COLOR=Red]***adds***[/COLOR] a phrase onto one of its pages, the home page. The thing is, the phrase (e.g. HELLO WORLD) is [COLOR=Red]already[/COLOR] on the page. So I need to be able to receive an alert when an[COLOR=Magenta] [COLOR=Red]**ADDITIONAL copy**[/COLOR] [/COLOR]of the phrase is added to the page. 

How can I do this? I don't want to have to keep checking the site every 5-10 minutes manually. Thanks.


Is there some sort of program that I can run on my computer that will check xyzwebsite.com every XX minutes and then, when it finds "Hello World" more than once on the site, I will then immediately receive an email (or sms)?

The number one important thing is SPEED. I need to receive an ALERT to my gmail address or to to my cellphone via SMS as soon as the webmaster adds that additional "HELLO WORLD" phrase onto his website's homepage.

I have NO programming skills at all, but I hope my envisioned goal wouldn't be too hard to create. Thank you.

Note: --I don't own the site / server. I have no control over the site. 


Thanks.

---

### Post by UbuKunubi on 2009-02-11
Hello!

There are many ways to do this.I've something very similar in the past - similar as in the reverse! (I wanted to change my webpage header with the contents of an sms payload).

So first of all you need to collect the information from the webpage. My personal favorite is using python and Beautiful Soup - please google around for the tips and hints on how to read the page, and parse its contents for the phrases and counting instances of matches.

Secondly, after identifying that you have found the target '2nd phrase' you need to store it off somewhere so you avoid constant sms being sent about the same instance. (hope i'm not teaching you how to suck eggs - but since this is almost a 'real time' application these things can go missed'

Third: send the SMS. Personally I use a bluetooth connection for sms sending, but there are also serial GSM modems that accept AT commands - but may i also suggest (assuming your phone supports Skype) that you use the Skype API to send either an sms (which always costs) or an Skype chat I.M.

I have posted some examples to sourceforge.net, but if you need more help please send me message.

---

