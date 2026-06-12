---
title: "Exchange server mail"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by imk59 on 2012-10-22
Are we able to set up an email account based on exchange server. 
I need to work from home and so far been using MS outlook for downloading the exhange server email.
Could we install MS Outlook on Ubunto plateform?

---

### Post by mastablasta on 2012-10-22
> **imk59 said:**
> Are we able to set up an email account based on exchange server. 
I need to work from home and so far been using MS outlook for downloading the exhange server email.
Could we install MS Outlook on Ubunto plateform?
 
 
do you have AD domain/login on server. if so there is an open source solution for that.
if it's just normal email server i think it should go with Thunderbird or Evolution.

---

### Post by mlentink on 2012-10-22
If you're used to Outlook, you would probably like Evolution the best. Evolution is available from Ubuntu Software Center. After that, install the evolution-ews package for remote access to the Exchange server.
If you want to log in to the Exchange server from within your corporate network, you can also install the evolution-mapi package.

Even though I've heard some people have had success with installing older versions of Outlook in Wine, I would personalley much prefer the native Linux solutions.

Should you have a preference for Thunderbird, there are also add-ons available for that, please search the Mozilla add-on directory.

---

### Post by GrouchyGaijin on 2012-12-20
> **mlentink said:**
> 

Should you have a preference for Thunderbird, there are also add-ons available for that, please search the Mozilla add-on directory.

Really?  I couldn't find anything that worked.  I wish I could get Thunderbird to connect to the exchange server at work.  I'm using Thunderbird 17 and I believe that the Exchange server is 2010.

---

### Post by mlentink on 2012-12-20
> **GrouchyGaijin said:**
> Really?  I couldn't find anything that worked.  I wish I could get Thunderbird to connect to the exchange server at work.  I'm using Thunderbird 17 and I believe that the Exchange server is 2010.

The one I used in the past (switched back to Evolution about a year ago) doesn't seem to support TB16 and up yet. But if you search [https://addons.mozilla.org/en-US/thunderbird/search/?q=exchange&appver=&platform=](https://addons.mozilla.org/en-US/thunderbird/search/?q=exchange&appver=&platform=) you'll find a couple you could try

---

### Post by GrouchyGaijin on 2012-12-20
> **mlentink said:**
>  But if you search [https://addons.mozilla.org/en-US/thunderbird/search/?q=exchange&appver=&platform=](https://addons.mozilla.org/en-US/thunderbird/search/?q=exchange&appver=&platform=) you'll find a couple you could try

Thank you,

I had looked there in the past and didn't find much.  I did see ExQuilla, but thought since it is a beta it might be just more hassle than Outlook Web Access.

I just tried ExQuilla and it works pretty well for mail only.
It doesn't pick up the address book or calendar which is not a huge problem.  I use Google calendar.

All in all, this is a better solution than OWA and was much easier to setup than DavMail which sounded promising.  I kept getting an unable to bind error with DavMail.

One less reason to use a Windows product on my own hardware. :p

OOPS - ExQuilla does bring in the Outlook address book. (I'm really happy about that!)

---

