---
title: "text vanished in Firefox 12, 13"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by pratikk on 2012-06-09
After the recent upgrades, Firefox (now 13) on my 12.04 machine has stopped rendering text on some sites like Facebook. A text-free PDF of getfoxyproxy.org is attached to illustrate. Text areas are intact but blank and no text can be selected in them. However, the page source shows the full text.

I wonder if it was the upgrades, or the fact that i created a separate /home partition about the same time? Is there an implication for fonts? Mine are at /usr/share/fonts and  behaving themselves in all applications, including Midori. Only FF has this problem, which is not cured by safe mode or reinstall. Both plain FF and FF in the Tor browser bundle behave like this. 

Enlightenment urgently required. I really can't figure this out.

Pratik

---

### Post by drpjkurian on 2012-06-09
Hi try this
Go-->Edit-->Preference-->Advanced (Near fonts)-->uncheck the box stating "allow pages to choose their own fonts "

---

### Post by pratikk on 2012-06-09
> **drpjkurian said:**
> Hi try this
Go-->Edit-->Preference-->Advanced (Near fonts)-->uncheck the box stating "allow pages to choose their own fonts "

Thanks, but I don't have this option in FF 13. Does it point to a config file I can edit manually?

---

### Post by numand on 2012-06-09
@pratikk, you can find the option that is pointed by @drpjkurian at Preferences>Content>Advanced.

---

### Post by drpjkurian on 2012-06-10
You are right 'numand' I made a mistake

---

### Post by pratikk on 2012-06-10
> **numand said:**
> @pratikk, you can find the option that is pointed by @drpjkurian at Preferences>Content>Advanced.

Thanks, found it. But it's already checked. Not the issue. Really at a loss here, because there are no text issues in any other package, including browsers.

---

### Post by drpjkurian on 2012-06-10
I would like you to uncheck it

---

### Post by pratikk on 2012-06-10
> **drpjkurian said:**
> I would like you to uncheck it

Brilliant! Works fine now. Sorry, I had misread your reply. There was a baby on the rampage in my lap at the time. 

Thanks a lot!

Pratik

---

### Post by drpjkurian on 2012-06-10
You are most welcome

---

