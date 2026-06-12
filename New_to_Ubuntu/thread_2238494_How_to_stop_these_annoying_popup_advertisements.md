---
title: "How to stop these annoying popup advertisements?"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by resander on 2014-08-08
Have been using Ubuntu and Firefox for about 7 years (now on Ubuntu 12.04 LTS). 

Quite recently I have been annoyed and disturbed by popups that I cannot move, close and get rid of. They just sit there and block the view. There is always a popup on the left-hand side with caption 'Recently Bought' showing goods that I would never dream of buying, like an accordion (hate the sound), Stainless microwave (already have a white goods micro), a Trixie Dog Kennel (have no dog) etc. There is also always a popup on the right-hand side with Caption 'Hot Deals'. All these popups have 'Powered by Shop Smart®' displayed in the lower right corner, but no X close button.

I get these popups when going to online ASDA, Tesco, Sainsbury, Amazon, Ebay and even an online overseas newspaper and probably many other too.

How do I stop these, ideally permanently?

Cannot recall having seen other popups, but would be nice to be able to block all popups. How?

---

### Post by Jesse_Campton on 2014-08-08
Have you tried another browser such as Chromium? Do you get the pop-ups? Save your bookmarks and such and reinstall Firefox? I would delete the Firefox folder before reinstalling though, just to be sure.

---

### Post by Polydorus on 2014-08-08
Have you tried installing the extensions Adblock Plus and NoScript for Firefox?

---

### Post by buzzingrobot on 2014-08-08
A quick Google finds several explanations of how to stop this on Windows (which might be extrapolated to Linux) and explanations that Smart Shop is legitimate but the ads are malicously triggered by third parties to generate money. 

As suggested, backup bookmarks and anything else you want to preserve. Then, purge Firefox (apt-get purge Firefox). Then, check if the ".mozilla/firefox" directory in your home directory has been deleted. If not, delete it manually. Reinstall Firefox.

---

### Post by tgalati4 on 2014-08-08
Try installing Ad Block Edge.  It's possible that Smart Shop is using an exploit in Ad Block Plus that allows "acceptable ads".

---

### Post by resander on 2014-08-09
The Chrome browser did not bring up any popups for the same files, so the culprit is Firefox.

Removed and reinstalled Firefox from the Ubuntu Software Centre on the Applications menu and this stopped the popups. Also installed the AdBlock Plus and NOSCRIPT addons via the Add-Ons manager in Firefox. Never used these before.

Many thanks for kind advice.
P.S. I have not seen any ad-popups before when using Ubuntu+Firefox as far as can remember. I don't click links in emails and visit dodgy websites, so what could have caused this infection?

---

### Post by Jesse_Campton on 2014-08-09
Welcome and please mark this thread as solved. :p

---

### Post by phedup on 2015-02-19
[QUOTE=resander;13094002] "The Chrome browser did not bring up any popups for the same files, so the culprit is Firefox."

Hi Resander,

Though this thread is closed, I wanted to let folks know that these lower right hand corner pop ups DO occur frequently for me in Chrome.  (Ubuntu 14.4 user.)

---

### Post by sammiev on 2015-02-19
I use adblock plus and do not have that problem, make sure this field where the mouse pointer is, is not check marked as it is by default.

---

