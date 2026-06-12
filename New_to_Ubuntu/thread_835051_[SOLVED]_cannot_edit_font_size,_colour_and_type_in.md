---
title: "[SOLVED] cannot edit font size, colour and type in evolution"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-06-20
why can't i edit any font size, font colour and font type in evolution?

---

### Post by Dynaflow on 2008-06-20
You're probably writing e-mails in plaintext, which has no inherent color, font, etc.  You need to use HTML formatting to make things pretty.

In the Compose Message window, go to Format in the toolbar and check the box next to HTML.  Voila.

If you would like to make HTML formatting a persistent feature, go to Evolution's main toolbar and click Edit -> Preferences -> Composer Preferences.  Under the heading "Default Behavior," check the box for "Format messages in HTML."

---

### Post by afeasfaerw23231233 on 2008-06-20
thank you! it works.
but i have another problem. why the mail in my inbox are all black and white though the text has been colourized by the sender?

---

### Post by Dynaflow on 2008-06-20
Same thing, likely.  Edit -> Preferences -> Mail Preferences -> HTML Messages [tab].  At "HTML Mode," make sure the drop-down box has selected "Show HTML if present."

---

### Post by afeasfaerw23231233 on 2008-06-20
oops... this time it doesn't work. the default setting is already "show HTML if present" . but my mails received are still black and white

---

### Post by afeasfaerw23231233 on 2008-06-22
BUmp

---

### Post by afeasfaerw23231233 on 2008-06-22
strange enough. i selected "show plain", shut down evolution, restarted it, and reselect "show HTML", shut down and restarted it again and the colour shown up properly. problem solved, thanks

---

