---
title: "web application and sms?"
date: 2007-03-08
forum: Programming Talk
---

### Post by michie86 on 2007-03-08
Hi,

Has anyone tried using Ultrasms here? I would like my web application(PHP) to be able to send receive SMS.

Thanks,
michie

---

### Post by lnostdal on 2007-03-08
i haven't tried ultrasms, but using SMS in a webapp is easy using a SMS gateway

just google for "SMS gateway" and you'll find several providers

edit:
looking at the PDF-file provided with ultrasms it looks very easy to use though .. you just use SQL to send and receive via the smsout and smsin tables

---

### Post by michie86 on 2007-03-08
thanks for the reply..

but I think that's not for free right?

do you now any provider for free? suggestions? or maybe a cheap one? Coz I'm only a student, unfortunately, I cant afford costly ones.. thanks ;)

---

### Post by lnostdal on 2007-03-08
no, you are right; the sms gateways are not free (well, i haven't seen any that are .. edit: or maybe i'm wrong: [http://en.wikipedia.org/wiki/SMS_gateways#Carrier_Gateways](http://en.wikipedia.org/wiki/SMS_gateways#Carrier_Gateways) )

i've used these before: [http://www.pswin.com/](http://www.pswin.com/) .. but i do not know if they are the cheapest ones around

it might be cheaper using your own phone as a gateway .. have you checked out kannel ( [http://www.kannel.org/](http://www.kannel.org/) )? .. it's in the ubuntu repositories :)

---

