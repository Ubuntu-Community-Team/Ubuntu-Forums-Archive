---
title: "Occasionally cors error out of the blue for x seconds"
date: 2019-03-24
forum: New to Ubuntu
---

### Post by mithradantor on 2019-03-24
I am building my API with Laravel's Lumen (newest version). My front-end is build with VueJS.

Everything is working perfectly fine, but every now and then out of the blue I receive CORS errors. After x-amount of minutes (or seconds) it will be gone again like nothing ever happened.

I have been searching for error logs and other stuff for days but without results. Could anyone please tell me how I can find out what is wrong?

I am totally clueless at the moment.

Ubuntu 18.04 with Apache2. Lumen (newest) with VueJS (newest).

The error that I am receiving is:

Cross-Origin-aanvraag geblokkeerd: de Same Origin Policy staat het lezen van de externe bron op [https://example.com/v1/verify-token](https://example.com/v1/verify-token) niet toe. (Reden: CORS-aanvraag is niet gelukt).

Translated to English:

Cross-Origin-Request blocked. The Same Origin Policy does not allow reading from the external source at {website}. Reason: CORS-request failed.

As said, sometimes I can work for half an hour or so before this error occurs. After a couple of refreshes the error is gone and everything works as intended.

I checked my PHP7.2-FPM log, Apache2 log, Laravel (Lumen) logs but nothing is mentioned anywhere.

I also checked RAM and CPU, compared to when I have this error and when not. No difference. Same for network information with (sudo ifconfig). Both the same no difference.

Does anyone have a clue where to look?

---

### Post by wildmanne39 on 2019-03-24
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

