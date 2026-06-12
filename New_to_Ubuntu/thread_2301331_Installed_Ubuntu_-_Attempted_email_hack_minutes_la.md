---
title: "Installed Ubuntu - Attempted email hack minutes later?"
date: 2015-11-01
forum: New to Ubuntu
---

### Post by derek37 on 2015-11-01
Hello,

I am completely new to Linux. I just installed Ubuntu on my laptop, and within five minutes, received this message, "
[TABLE="width: 100%"]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][TABLE="width: 300"]
[TR]
[TD][/TD]
[/TR]
[TR]
[TD]Someone just tried to sign in to your Google Account xxxxxxxx from an app that doesn't meet modern security standards.[TABLE]
[TR]
[TD][/TD]
[TD][COLOR=#202020][FONT=Roboto-Regular]Details:[/FONT][/COLOR]
[COLOR=#727272][FONT=Roboto-Regular]Monday, November 2, 2015 4:20 AM (China Standard Time)
China*[/FONT][/COLOR][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
Is this a coincidence? My wired university internet actually disconnected shortly before this, which I was trying to figure out as well (it seemed to still be connected as it was recognized in my network settings, but firefox wouldn't connect).

So - I guess to sum this up I have three questions:

-Is this email attempt something I could have done wrong with my installation that made me vulnerable(all done from this website, booted from my flashdrive)?
-I switched from windows 8 and did a complete install of Ubuntu (not alongside), is there anything I should know regarding this?
-What are some possible fixes to my wired internet not working correctly?

Thank you -

Update: Internet mysteriously works.

---

### Post by bapoumba on 2015-11-01
The most likely explanation is you do not use the 2-Step Verification in your Google account (see here for ex : [https://googleonlinesecurity.blogspot.ca/2014/04/new-security-measures-will-affect-older.html](https://googleonlinesecurity.blogspot.ca/2014/04/new-security-measures-will-affect-older.html)) or that you signed with an app that does not support the preferred Google auth method (Google app, mail client etc.).
[https://support.google.com/accounts/answer/6010255](https://support.google.com/accounts/answer/6010255)

---

### Post by derek37 on 2015-11-01
It just seems rather bizare timing as I've never had this happen before. I hadn't even opened my email as I was "connected" to a wired connection, but couldn't get firefox working. I guess I'm just paranoid that I did something wrong. I was connected to a wired connection, but was unable to get my browser to connect at all, so I understand it seems rather silly to worry. As I said before, it is just very bizarre timing.

---

### Post by bapoumba on 2015-11-01
Yeah, gremlins going back home from Halloween maybe :)

You need to be careful though, in particular if you connect to access points you cannot trust. I would assume a univ network be secure enough.

---

### Post by grahammechanical on 2015-11-01
You do not say what version of Ubuntu you installed. Ubuntu comes with a dedicated email client called Thunderbird. Were you running Thunderbird or some other email client? Have you already set up Thunderbird to connect to your email account? I am just wondering how you can receive an email if you are not connected to your email account. Ubuntu does have a utility called Online Accounts. Did you set that up to connect to your Gmail account?

It is possible to have a valid connection to an internet access point (router) and the ISP have some kind of a failure. The other day I was unable to connect to the internet for several hours. There was nothing wrong with Ubuntu. There was nothing wrong with the router. I used the router's settings utility to test the connection to the ISP and it reported back with green tick marks everywhere necessary. So, I concluded that there was some break between the ISP's servers and the rest of the Internet.

Coincidences do happen.

Edit: Try checking the ISP's service status record. In my case I see that the National Telecoms company was doing network maintenance during much of this week and after that the ISP's customers were affected by data transfer issues for a day or two.

Regards.




Regards.

---

### Post by derek37 on 2015-11-01
> **grahammechanical said:**
> You do not say what version of Ubuntu you installed. Ubuntu comes with a dedicated email client called Thunderbird. Were you running Thunderbird or some other email client? Have you already set up Thunderbird to connect to your email account? I am just wondering how you can receive an email if you are not connected to your email account. Ubuntu does have a utility called Online Accounts. Did you set that up to connect to your Gmail account?

It is possible to have a valid connection to an internet access point (router) and the ISP have some kind of a failure. The other day I was unable to connect to the internet for several hours. There was nothing wrong with Ubuntu. There was nothing wrong with the router. I used the router's settings utility to test the connection to the ISP and it reported back with green tick marks everywhere necessary. So, I concluded that there was some break between the ISP's servers and the rest of the Internet.

Coincidences do happen.

Edit: Try checking the ISP's service status record. In my case I see that the National Telecoms company was doing network maintenance during much of this week and after that the ISP's customers were affected by data transfer issues for a day or two.

Regards.




Regards.

Thank you for your response. To answer your questions:

-I installed 14.04.3 desktop version.
-I did not set up thunderbird or anything else, I had just been fumbling around on my desktop for about five minutes trying to get firefox to work. I received a notification on my phone that an unauthorized login attempt was made.

Lastly, I know there isn't a problem with my internet. I'm plugged into my university wired internet on my main PC right now, and it was working on my laptop several hours ago before I switched to Ubuntu. I've been searching around online so I'll try several things to enable my internet before complaining more :).

-Thanks again.

Update, plugged my laptop in and internet seems to be working now for some mysterious reason :).

---

### Post by mastablasta on 2015-11-02
> **derek37 said:**
>  I received a notification on my phone that an unauthorized login attempt was made.


i have SSH port open on server and i get about 3-5 bans per day. this only records those that tried more than 2 times and failed. there are also some one time attempts. most of them come from china. so yes it's a nasty world out there.

---

### Post by bapoumba on 2015-11-02
Hmm, did you receive the message on Ubuntu or on your phone ?
If on your phone, that may have nothing to do with Ubuntu and something to do with someone trying to access the account.
Once logged into google, you can review where and when your account has been accessed.

---

### Post by poorguy on 2015-11-05
i get that when i sign into my gmail account from a different computer or a different location.

---

### Post by Mike_Walsh on 2015-11-06
^^^ +1.

Same here. When you run 4 or 5 different different OSs from the same machine, as I do, and swap around frequently, well.....I think it **really **confuses the ISPs (and Google in particular).

I must get that at **least** 7 or 8 times a week..!

I also sign into my Google account from a mate's machine 2-3 times a month. Google throws a wobbly then; it can't make out what I'm doing...**or** why. And Google always requires your phone number anyway.....for backup verification.

It's just the 'system' doing what it was designed to do.


Regards,

Mike. ;)

---

### Post by tripp98 on 2015-11-07
Recommend changing your gmail password immediately.  Inside of gmail Look in the details in the lower right corner.  It will tell you where you have logged in.  Also check your rules within gmail.  If your account has been hacked normally they will cover their tracks by adding rules to delete all your future emails or forward your email to external accounts.

---

### Post by sammiev on 2015-11-07
> **poorguy said:**
> i get that when i sign into my gmail account from a different computer or a different location.

Correct and if you do a fresh install like me ever month, you get the same.

When I travel I get the same as well.

I think it's great, if someone hacks my account I would likely know in mins.

---

### Post by fyfe54 on 2015-11-08
I get those messages when I use my laptop on a public wifi (with a VPN).  Gmail seems to think I am in Arizona, Texas or even Alaska when I am actually in Brooklyn.   It is a little annoying, but as sammiev says, I want to know if someone hacks my email.

---

