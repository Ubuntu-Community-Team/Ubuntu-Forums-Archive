---
title: "Problem retrieving Hotmail"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-20
Hello, 

I'm using Thunderbird to access my Hotmail, Gmail and Yahoo account. So far everything is fine but a few moment ago I got this error message (seee attachment) when I click "Get Mail" button. Is this problem for temporary and related to Ubuntu. Thanks

---

### Post by KenBW2 on 2008-05-20
As far as I know, Hotmail doesn't allow you to use any email client other than Microsoft ones (Outlook/Express, Windows Live Mail), but I could be wrong

---

### Post by dannyboy79 on 2008-05-20
you could check this out but I am pretty sure that Free hotmail doesn't allow pop access.

[http://www.linuxforums.org/forum/ubuntu-help/108340-retrieving-hotmail-gmail.html](http://www.linuxforums.org/forum/ubuntu-help/108340-retrieving-hotmail-gmail.html)

---

### Post by PmDematagoda on 2008-05-20
> **KenBW2 said:**
> As far as I know, Hotmail doesn't allow you to use any email client other than Microsoft ones (Outlook/Express, Windows Live Mail), but I could be wrong

You are right, but you can use certain applications/add-ons that will allow you to use Hotmail.

One way you can use Hotmail with Thunderbird by reading the Thunderbird FAQ here:-
[http://www.mozilla.org/support/thunderbird/faq](http://www.mozilla.org/support/thunderbird/faq)

What you will want is the Migration section.

---

### Post by kellemes on 2008-05-20
> **KenBW2 said:**
> As far as I know, Hotmail doesn't allow you to use any email client other than Microsoft ones (Outlook/Express, Windows Live Mail), but I could be wrong

You're wrong indeed, the Thunderbird webmail extension is made for this and works fine with the free hotmail account.

This error could be temporary, I get it sometimes, don't know why..

---

### Post by Flare183 on 2008-05-20
I use Hotway and Hotsmtp. Look at this URL: [http://sourceforge.net/projects/hotwayd/](http://sourceforge.net/projects/hotwayd/)

---

### Post by wariskampar on 2008-05-20
Thank guys! My problem solve. Maybe there some glitch with live.mail server because I just receive one weird email from them (html code instead of normal email). Btw I'm using  WebMail extension to access my Hotmail and contrary to opinion that Hotmail dont support POP3(sure it doesnt!), so far I have no problem accessing my Hotmail account within Thunderbird. Try few hour to configure Evolution but since I use Thunderbird since my XP days, might as well stick with it!

---

### Post by hellomoto on 2008-05-20
hotmail doesn't support POP 3 anymore. I use izymail to download my hotmail messages to evolution.

you can setup an account with them  here:
[izymail]("http://v3.izymail.com/")

---

### Post by philinux on 2008-05-20
> **hellomoto said:**
> hotmail doesn't support POP 3 anymore. I use izymail to download my hotmail messages to evolution.

you can setup an account with them  here:
[izymail]("http://v3.izymail.com/")


Yes it does and it works fine. Occasionally there the bad vibes error that pops up now and again, and sometimes you have to updates the addons.

---

### Post by wariskampar on 2008-05-20
i also came across izymail when try to setup evolution but when reconsider the security issue of my email, i drop the idea. maybe i'm wrong but our email will go to izymail account first and then re direct to mail client (namely evolution).

---

### Post by stchman on 2008-05-20
> **wariskampar said:**
> Hello, 

I'm using Thunderbird to access my Hotmail, Gmail and Yahoo account. So far everything is fine but a few moment ago I got this error message (seee attachment) when I click "Get Mail" button. Is this problem for temporary and related to Ubuntu. Thanks

As far as I know Hotmail does not allow POP access for free accounts.  If you pay $20 a year then you get POP access.  I have heard that very old Hotmail accounts still have free POP access.

Now knowing that I have also read that POP access on Hotmail does not work very well with non M$ OS and mail clients.

---

### Post by kellemes on 2008-05-20
> **stchman said:**
> As far as I know Hotmail does not allow POP access for free accounts.  If you pay $20 a year then you get POP access.  I have heard that very old Hotmail accounts still have free POP access.

Now knowing that I have also read that POP access on Hotmail does not work very well with non M$ OS and mail clients.

This has nothing to do with pop access..
Thunderbird can read **free** hotmail accounts (and also free @yahoo) using the webmail extension. I'm doing this for years.. from GNU/Linux.

---

### Post by viniciuscamargo on 2008-06-27
Hotmails do works in Thunderbird with the add-ons webmail and webmail-hotmail that you can download from [http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html).

This error message some times hapen to me too and I don't now why yet, but to solve that I just restart the Thunderbird and everything comes back to work fine.

Try to change your 'webmail-hotmail' add-on preferences to 'Hotmail Live' instead of just 'Hotmail'.

---

