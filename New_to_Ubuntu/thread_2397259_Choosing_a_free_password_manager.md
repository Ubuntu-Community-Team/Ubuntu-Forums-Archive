---
title: "Choosing a free password manager"
date: 2018-07-27
forum: New to Ubuntu
---

### Post by dathewolh on 2018-07-27
I was using DashLane Password Manager. But pay 40€ for one year for remembering ~100 string in a secured server seems very onerous  to me. (I could do it myself for free)

So, I'd like to have suggestions to help.
On 3 OS, 2 devices (Win10, Ubuntu, Android) :p

---

### Post by TheFu on 2018-07-27
I use KeePass v2 DBs and select the programs that work with that file format on each platform.  Android, Linux, and Win7 (I won't have win10 on my network).  All are F/LOSS.  I use the F-Droid store (not google's) for Android stuff.

The KeePass compatible programs change, but I avoid tools that require .NET libraries for political reasons.  There are a few in the KeePass family which I avoid.  Thankfully, the other projects fill in nicely.

---

### Post by dathewolh on 2018-07-27
With keePass , is the database usable on different devices? Stored online or locally?

---

### Post by Autodave on 2018-07-27
This not an answer to your question. But, maybe for yourself or others reading this, it may help.  Choose a password. should b e 6 to 8 digits long. It must contain lower and upper case letters, at least one number and at least one character. Now, decide to split that password in the middle somewhere.  Where you split it, insert the first 2 letters of the site. For instance: kT5&4eTt could be your password. Now say that you are going to Amazon. You have previously decided to split it in the middle, so your password for Amazon would be kT5&am4eTt. Or, you could decide to use the password as is and insert the first letter of the site to the front and the second letter to the end.

---

### Post by TheFu on 2018-07-27
> **dathewolh said:**
> With keePass , is the database usable on different devices? Stored online or locally?

The keepass v1 and v2 DBs are cross-platform.  They work on all platforms I've tried, with a compatible program.  ARM, Intel, AMD, 32-bit and 64-bit.

I have 1 "system of record" which is my normal desktop at home.  From there, I rsync the DB nightly to my laptop, tablet, smartphone and a few trusted family systems in different states.  They don't know how to unlock it and it isn't in-the-cloud. I wouldn't trust any "service" that placed my data in the cloud along with 1,000 other customers, much less 50+M customers.  1password and all the other password storage services necessarily fail on this consideration.  I suppose, for twitter, facebook and webmail for only social network accounts, it wouldn't matter, but we still need a solution for banking, brokerage, and online purchase accounts. Those should never be cloud connected. Never.

To change a password, I try to only do that on my desktop.  The other systems are read-only (in my mind).  In a pinch, I have changed a password on the local device, but ensured that modified DB was pushed to the desktop before the nightly rsync everywhere.  If you are going to use a password manager, you need that DB to never be compromised or lost.  That means having it on a few trusted systems that aren't in the same physical location. 

There are other threads here with guidance about 2FA, password lengths, and why you want to have different logins for every account with financial impacts.  Never use that same email for facebook/google and your bank, for example.

[http://www.youtube.com/watch?v=GwZJ4OrhikU](http://www.youtube.com/watch?v=GwZJ4OrhikU) Password Cracking Class for Hackers For Charity 
[https://arstechnica.com/information-technology/2013/05/how-crackers-make-minced-meat-out-of-your-passwords/](https://arstechnica.com/information-technology/2013/05/how-crackers-make-minced-meat-out-of-your-passwords/) - from 2013. Still useful to understand.

On the password reset questions - lie.  Never tell the truth that anyone else would be able to look up.  Your first pet?  "GSDF51bbe82ae4d883e2f33ba77437571bbd%8t"
Hack that.  It isn't like you wouldn't put the answers into the password DB anyway.

A 12-character 100% random password is very different from 1-3 words that are merged/created to get to 12 characters. Very different.  Where I work, 16 characters is the minimal and we push for 20+ characters if people cannot use random, generated, passwords.  In the old days, we'd run password crackers against the internal logins and tell people to change their passwords by telling them "Snoopy88" wasn't secure enough. That would get their attention.

IMHO.

---

### Post by deanr2 on 2018-08-02
I use KeePassX on my Linux PCs and KeePass2 on my android smartphone. I keep the key file in dropbox and/or google drive and there's no problem synching devices when I make changes, additions etc.

---

