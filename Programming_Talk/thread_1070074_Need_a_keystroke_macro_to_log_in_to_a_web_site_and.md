---
title: "Need a keystroke macro to log in to a web site and grab some data"
date: 2009-02-14
forum: Programming Talk
---

### Post by tc101 on 2009-02-14
I need to write code to log in to 15 different bank accounts every day, get the deposit amount for the local office of our company, and write that amount to a file.  These accounts will be in several different banks, Wachovia, Regions, Bank Am and maybe others.  I need some sort of keystroke macro to do this.  

I can use Firefox or IE.  I can not use Ubuntu.  This will be running on windows XP.  My first thought was a firefox extension but I can't find one that does what I want.  

Suggestions?

---

### Post by NathanB on 2009-02-14
Sounds like a job for Ubiquity!

[http://labs.mozilla.com/2008/08/introducing-ubiquity/](http://labs.mozilla.com/2008/08/introducing-ubiquity/)

Give it a try...

---

### Post by Ferrat on 2009-02-14
> **tc101 said:**
> I need to write code to log in to 15 different bank accounts every day, get the deposit amount for the local office of our company, and write that amount to a file.  These accounts will be in several different banks, Wachovia, Regions, Bank Am and maybe others.  I need some sort of keystroke macro to do this.  

I can use Firefox or IE.  I can not use Ubuntu.  This will be running on windows XP.  My first thought was a firefox extension but I can't find one that does what I want.  

Suggestions?

So what you really want is a database for revenue etc collected from all the branches? 
first off why doesn't your local offices use the same bank? 
anyway, wouldn't it be easier just to buy/make a simple software where your local offices just enters the amount the deposit in to the database without going via the bank? 
That would avoid a lot of security issues.

---

### Post by Jacks0n on 2009-02-15
Hm... I'd just use wget to grab each page, and parse it. So there's no macro, just a batch file that you run. Plus it'd work in Ubuntu or Windows.

wget for windows can be found here:
[http://gnuwin32.sourceforge.net/packages/wget.htm](http://gnuwin32.sourceforge.net/packages/wget.htm)

---

### Post by Zugzwang on 2009-02-15
> **Jacks0n said:**
> Hm... I'd just use wget to grab each page, and parse it. So there's no macro, just a batch file that you run. Plus it'd work in Ubuntu or Windows.

wget for windows can be found here:
[http://gnuwin32.sourceforge.net/packages/wget.htm](http://gnuwin32.sourceforge.net/packages/wget.htm)

I doubt that wget will actually do this. The login procedures of banks are normally relatively complicated. You would need to do the cookie handling yourself. Furthermore, some banks use captchas to prevent automatic logins.

---

### Post by Jacks0n on 2009-02-15
> **Zugzwang said:**
> I doubt that wget will actually do this. The login procedures of banks are normally relatively complicated. You would need to do the cookie handling yourself. Furthermore, some banks use captchas to prevent automatic logins.

You'd have to login manually once, then save the cookie. But wget can use existing cookies. The only problem'd be the captchas.

---

### Post by Zugzwang on 2009-02-15
> **Jacks0n said:**
> You'd have to login manually once, then save the cookie. But wget can use existing cookies. The only problem'd be the captchas.

Most banking sites will automatically log the user out after a certain period of inactivity (typically ~15 minutes). The cookie then becomes invalid/unusable. If that script is run only once a day, that won't help much.

---

### Post by Jacks0n on 2009-02-15
> **Zugzwang said:**
> Most banking sites will automatically log the user out after a certain period of inactivity (typically ~15 minutes). The cookie then becomes invalid/unusable. If that script is run only once a day, that won't help much.

Yeah but that's through JavaScript, not the cookie. I wrote a script a while ago for a friend to import all her shares into a spreadsheet using wget and an existing cookie, and it works fine. But my bank doesn't even send a cookie. It depends on the bank.

---

### Post by tc101 on 2009-02-15
> anyway, wouldn't it be easier just to buy/make a simple software where your local offices just enters the amount the deposit in to the database without going via the bank?

The local office already enters the deposit amount in the database, but the problem is fraud.  There is a lot of cash involved.  Recently someone at a local office entered that amount collected in the database, but rather than depositing it in the bank kept it.  We need to check the actual bank deposits daily, so if a deposit is not made we know it that day.

I can't say much more about the details of the business.  The boss might be mad at me for saying this much.

---

### Post by unutbu on 2009-02-15
> I need to write code to log in to 15 different bank accounts
In what language are you thinking about writing this?

If you like python, pycurl+Beautiful Soup could do the job. (Assuming the data to be mined is in html accessible with GETs, POSTs, and cookies.) If the website requires interacting with Flash, Javascript or converting images into letters and numbers, then I don't know.

---

### Post by tc101 on 2009-02-15
I have used Python, but not in several years.  I am currently best with VBscript or VB, second best with javascript.

---

