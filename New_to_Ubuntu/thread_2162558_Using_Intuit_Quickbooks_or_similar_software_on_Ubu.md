---
title: "Using Intuit Quickbooks or similar software on Ubuntu"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by vaibhavananda on 2013-07-15
Dear Ubuntu forum members, 

Is there a way to install Intuit Quickbooks {QuickBooksOnline.com} or similar software on Ubutnu ? Any advise would be appreciated. 

Kind Regards,
Vv

---

### Post by ajgreeny on 2013-07-15
I don't think you can use any of the "Quicken" family of applications in Ubuntu, even using Wine, but there are a number of Linux alternative applications available that may be suitable for you.  Some are probably more for home banking use, but there are a n umber of them that can be used for business financial accounting.

Have a scout around and a long look at the many links given at [http://linuxappfinder.com/businessandfinance](http://linuxappfinder.com/businessandfinance).  You may be able to find something that fits the bill exactly.

EDIT:
It looks as if I am not totally up-to-date nor correct, and that some versions (2007) of quickbooks, and quicken as well, will run in wine.  Things must have moved on since I last looked.
See:-
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=120](http://appdb.winehq.org/objectManager.php?sClass=application&iId=120)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=107](http://appdb.winehq.org/objectManager.php?sClass=application&iId=107)

---

### Post by Cheesehead on 2013-07-15
I have used QuickBooks since 2008.

Some wine users claim to have gotten some versions of QuickBooks to run under Wine. See [http://appdb.winehq.org/objectManager.php?sClass=application&iId=120](http://appdb.winehq.org/objectManager.php?sClass=application&iId=120)

But the real answer to your question is 'no'.

While good for experimentation, a production QB environment should NOT use wine. Future compatibility is not guaranteed, and QB under wine may break at any time. Your data recovery/reentry costs will be significant, and your employees and tax authorities will be quite unsympathetic if your paychecks, filings, payments are late for that reason.

QB requires COM (Windows only) to connect several of it's processes. It also depends on cmd.exe,  Outlook Express, and Internet Explorer.

Any applications you want to communicate with QB also require COM. Python, for example, talks to QuickBooks very well...but only on a Windows system.

---

### Post by HermanAB on 2013-07-15
I've used (an older) QB on Wine for many years, until I moved to a tax free jurisdiction.  That solved the problem quite neatly.

---

### Post by Cheesehead on 2013-07-15
> **HermanAB said:**
> I've used (an older) QB on Wine for many years[...]
Great! I've always wanted to try it again....
Which version?
Any particular hacks? Or did it just work?

---

### Post by BBQdave on 2013-07-15
> **vaibhavananda said:**
> ...Quickbooks ...similar software on Ubutnu ?

[**GnuCash**]("http://www.gnucash.org/") might be of interest :)

---

### Post by Cheesehead on 2013-07-15
GnuCash, when I tried it, seemed closer to Quicken (personal accounting) than QuickBooks (business accounting)...though there is quite the fuzzy area in between, and quite a bit of overlap.

Generally, for business accounting, a professional accountant sets up your books and uses them periodically to do your tax reporting, investor reporting, audits, and other important activities. Since the accountant's time is much more expensive than any relevant software package, and since the learning curve seems about the same, it's usually simplest to have the bookkeepers and managers use whatever software the accountant prefers. It's certainly possible to ask the accountant to try GnuCash or another package...if you want to pay for them to learn it, and keep paying for them to stay current on it. That's why Intuit has the market with QuickBooks - they spend a lot of money and effort convincing accountants, not business owners or managers, to prefer it.

---

