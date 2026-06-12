---
title: "how do you block diginotar certificates on epiphany or midori browsers?"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by moonpoppy on 2011-09-08
i'm using ubuntu 11.04. i don't see how you can manage security certificates in the midori or epihpany broswers. the webkit security  update info i have found on the web for linux seem to be for 10.04 and 10.10 for these browsers. all my upgrades are up to date. i hope i'm misunderstanding something.

i went to the site:

[https://www.maestre.com/](https://www.maestre.com/)

this site shows the ev certificate flaw in mac osx (and midori).

it's blocked in firefox and in chromium (maybe because i manually untrusted diginotar certificates in chromium), but this site opens with no issue with midori or ephiphany.

thanks.

for epiphany, i downloaded an extension to manage certificates. when i click on it under tools. nothing happens. and in midori i see no option for managing certificates whatsoever.

---

### Post by moonpoppy on 2011-09-10
it's nice that the certificates were finally taken care of but there is still one flaw

[https://www.maestre.com/](https://www.maestre.com/)

that this link works shows that ev certificates still haven't been revoked for epiphany or midori. this was the flaw everyone was up in arms about concerning macs. 

so stay away from https on those browsers until this problem is fixed in an update or until someone explains how to do this manually. i still haven't figured out how to do it.

---

### Post by gmargo on 2011-09-11
I don't have those browsers installed, so I can't test this specifically, but check the procedure in the following link.  (I only had to hit enter once, not three times, YMMV.)

"How to remove the DigiNotar Root CA certificate in Ubuntu"
[http://www.danielveazey.com/linux/how-to-remove-the-diginotar-root-ca-certificate-in-ubuntu/](http://www.danielveazey.com/linux/how-to-remove-the-diginotar-root-ca-certificate-in-ubuntu/)



Update: alternatively, just wait.  Looks like ca-certificates just got an update, and the DigiNotar certificate is removed.

---

