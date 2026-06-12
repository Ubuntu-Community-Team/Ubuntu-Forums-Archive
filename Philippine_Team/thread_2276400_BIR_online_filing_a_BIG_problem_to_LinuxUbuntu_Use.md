---
title: "BIR online filing a BIG problem to Linux/Ubuntu Users"
date: 2015-05-02
forum: Philippine Team
---

### Post by arvin5552 on 2015-05-02
Do you guys have any suggestions on how to actually get IE V9 working on Ubuntu?  

Not sure if this is the place to gripe or to report, but you guys have heard of all the hoopla about BIR's hard stand about online filing of Tax returns?

Well our company has been trying our best to comply, but we always get hit with one wall after another.  The latest of which makes me think that BIR is actually violating some kind of Law that prohibits government agencies from requiring individuals or companies to purchase a specific software.

1. In their FAQ, they said that ebirforms can be accessed with Firefox, Chrome, and IE.  Okay at least there are options.
2. But in the same FAQ it says that in order to file you can only use IE version 9.

Okay!  Wait, that means, everyone using Linux and of course older windows software and Mac, etc.  can't file anymore.  

Thus, basically what BIR is saying, upgrade and buy Windows 7 and above or else you won't be able to file.... specially because there is no more alternative form of Filing.

There has got to be a Group, Organization or individual who should go out and file a TRO and a case against BIR for doing this!

---

### Post by KayeNg on 2015-06-17
This is a good thread, shame no one is responding. Anong company kayo? Manufacturing? and totoo ba na Windows Internet Explorer lang pwede?

---

### Post by KayeNg on 2015-06-17
Maybe try WINE?

---

### Post by nerdtron on 2015-06-17
1. Install firefox.
2. Install useragent switcher for firefox: [https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher](https://addons.mozilla.org/en-us/firefox/addon/user-agent-switcher)
3. Set the user agent to IE9.
4. Try to browse the BIR

---

### Post by KayeNg on 2015-06-18
thanks for that nerdtron

---

### Post by arvin5552 on 2015-06-23
Unfortunately I don't think Wine will work, IE 9 requires a lot of MS Windows stuff, even a Win 7 (basic) install isn't capable of having IE9 (if I remember correctly).

I tried installing useragent switcher, but I get an error and this happens with other switcher add ons that I tried, I am however testing on an older Jaunty Ubuntu running Firefox 3.0+  

Yes it is confirmed that BIR requires IE9 and to make matters worse Phil Health has followed suit as well.  

No matter which industry you are in, you are required to file online with BIR and Philhealth.  But if you are asking because you are wondering what does a company use Ubuntu for, we are just a trading company.  I pushed for Ubuntu as it is less prone to the more common viruses.  Heck we use our Ubuntu to delete exe files from USB drives, basically using it as a "quarantine"

---

### Post by Bucky Ball on 2015-06-23
You could install Virtualbox from the repos and run Win whatever as a guest virtual machine, then install BIR in that. Or, of course, look for a Linux friendly alternative to BIR.

---

### Post by qamelian on 2015-06-23
> **Bucky Ball said:**
> You could install Virtualbox from the repos and run Win whatever as a guest virtual machine, then install BIR in that. Or, of course, look for a Linux friendly alternative to BIR.

BIR isn't something you install. It's the Bureau of Internal Revenue in the Philippines. 
If they're anything like the IRS or CRA in the US and Canada, I think most people would happily uninstall them! :)

---

### Post by Bucky Ball on 2015-06-23
Ah, my mistake. So this is actually a Wine issue and how to get IE working in Wine, not really about BIR at all as BIR is, as stated by its creators, Windows specific and not intended for Linux.

The Virtualbox/Windows virtual machine option would be the route I think I'd follow if I were to be forced to go down it as it sounds you are.

---

### Post by arvin5552 on 2015-06-29
Hehehe,  actually it isn't a Wine or Linux issue, it's a Government policy issue because they seem to think that everyone in this world is using Windows 7 or higher. :(

Yes BIR = IRS.  

Does the IRS REQUIRE all tax payers to file online?  Coz our BIR does! When asked, how about those that don't have access to computers, the answer was,  go to an internet cafe!  Oh makes it sound so simple!

I just found out though from a Mac user that at least he can access the BIR submission website.  But there are two types, the efps and the eBIRFORMS.

For efps [https://efps.bir.gov.ph/index.html](https://efps.bir.gov.ph/index.html)   it is accessible by Firefox.

However for ebirforms,  it is more complicated because they require to download an xml file which is what you fill up and when you click a button the IE9 will automatically open.  I feel that if there is Wine Win7 (higher than basic) then maybe there is a chance.  

Is there a WINE that is Win7 professional?

TTFN
Arvin

---

### Post by arvin5552 on 2015-06-29
Just want to update also that we temporarily had to give in and installed Win7 dual boot in one of our systems just for BIR filing.  SUCKs!  But what can we do! :(

---

### Post by Bucky Ball on 2015-06-29
That's hilarious! Submit your online tax return in an internet cafe. Priceless. #-o

---

### Post by nerdtron on 2015-06-30
Not just BIR. I just submitted my online registration on SSS (Social Security System) and the website only works properly on IE7/IE8 on windows 7. Using latest chrome and firefox is not working. I even tried changing user agents. It seems the website itself is just compatible on IE

-_-

---

### Post by DizNeo on 2015-09-03
That sucks. 

Department of Education (Philippines) also have an online registration where it requires Google Chrome (only) to be able to successfully enroll a student (elementary/highschool) online. If you use other browser (IE, Firefox, etc) other than Chrome, you will be disappointed as some features on the website, like those drop down date selection, only works on Chrome. I've tried it on Chrome for Linux and it works also.

BIR system seems worst as it can only be used with IE.

---

### Post by arvin5552 on 2015-09-07
Diz, for your info, I have chrome working on my Lucid Lynx system.  However I understand that, that is not your point, it's the really bad practice of government IT "specialists" developing government website that will work specifically on one browser.
When I used to design websites (simple ones) some time ago, I'd have multiple browsers to test compatibility, and I was doing this as a hobby and for free... these guys are paid to do this! Sheesh.

I hope someone in the media will actually get hold of this info and make a report on this.  

One thing I hate more than government websites working only on specific OS and browsers are the replies when they are given feedback... stuff like... "well use an internet cafe then!".

---

