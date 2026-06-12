---
title: "Postfix - 1more questions"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by Bob_OHara on 2014-09-11
Hi

Say a customer calls saying he's missing a message from X number  of days ago. Is there a command that will search the deferred queue for a  specific to or from address? 

Bob - USA Choice

---

### Post by claracc on 2014-09-12
What software package are you talking about?, is it evolution, thunderbird?, what operating system?.

Could you describe problem in a more detailed way?.

---

### Post by SeijiSensei on 2014-09-12
Searching the logs is usually the only effective solution.  Look at the user's traffic in /var/log/mail.log.  You'll see entries for the arrival and disposition of every message coming into your server.

Do you or the customer use spam filtering?  Perhaps the message is in the customer's spam folder.  That's the most common reason why someone fails to get an expected message.

---

