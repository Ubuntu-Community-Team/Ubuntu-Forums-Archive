---
title: "Passwords"
date: 2022-08-18
forum: New to Ubuntu
---

### Post by dmacpeak on 2022-08-18
I was going to let Firefox store my passwords before I get aquatinted with a password manager.

As for User passwords, should I write them down and enter manually, bc the password manager or auto fill won't be available at login?

Also, do I need different password managers set up with each user or will one work for all the users if I set it up in an admin user?

---

### Post by TheFu on 2022-08-18
> **dmacpeak said:**
> I was going to let Firefox store my passwords before I get aquatinted with a password manager.

As for User passwords, should I write them down and enter manually, bc the password manager or auto fill won't be available at login?

Also, do I need different password managers set up with each user or will one work for all the users if I set it up in an admin user?

Don't trust any browser with your passwords, unless you want them to be shared with the world. All browser have bugs and they have a long history of failing in security without anyone noticing for some time.

You should never write down complete passwords or complete credentials.  You can write down the system/URL, username (use a unique one for every website), and half of the password - make it random, unique and complex for each login, then keep the 2nd half in your head.

As for password managers, I have a few rules.  Only use one that is 100% offline and has no networking code built in.  KeePassXC is one.  

Each user probably needs a few password databases, but that depends on their individual needs.
I have a db for personal stuff, a db for work systems, and a shared DB that is shared with my better half.  Each of these is just a different password DB file, stored encrypted.  Be certain to have at least 3 copies and backup the files daily, at the minimum.
* [https://blog.jdpfu.com/2014/12/20/more-on-passwords-and-online-security](https://blog.jdpfu.com/2014/12/20/more-on-passwords-and-online-security)
* [https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](https://blog.jdpfu.com/2011/03/25/101-uses-for-a-password-manager) - password managers aren't just for passwords. Lots of things, some sensitive and some not are perfect to be stored, since we'll be careful to backup these DBs all the time.
* [https://blog.jdpfu.com/2010/04/24/keepassx-password-manager](https://blog.jdpfu.com/2010/04/24/keepassx-password-manager) was written for KeePassX, but applies to KeePassXC with is actively maintained.  Over time, different KeePass projects have come and gone, but the DB format is well supported by lots of different tools. We'll never be abandoned. That is very important.  The DB files are cross-platform too, so when I back them up, I also ensure they are placed on tables, phones, and other computers (some even running _that_ other OS).

---

### Post by dmacpeak on 2022-08-18
Wow!!!  Everytime I look for a quick fix and find out there isn't one when it comes to privacy.  Thanks for the help!

---

### Post by Autodave on 2022-08-18
I'll give another suggestion for anyone who is interested.  Make a 6 digit password: use upper and lower case letters, at least one number, and at least one character such as # or ! or whatever.  Memorize it and you can even write it down.  Now, decide that somewhere in the beginning, middle, or end, you are going to INSERT 2 additional letters.  These 2 letters will be the first 2 letters of the name of the website.  For instance:
Let's say that you chose  Rf49#Q  as your password.  And you want to log in to Facebook.  You have decided that you will split your password in the middle.  Therefor, your password for Facebook would be: Rf4fa9#Q.  For Twitter it would be Rf4tw9#Q.

---

### Post by ActionParsnip on 2022-08-19
Here are some options:
[https://www.linuxandubuntu.com/home/best-password-managers-for-linux](https://www.linuxandubuntu.com/home/best-password-managers-for-linux)

---

### Post by TheFu on 2022-08-19
> **Autodave said:**
> I'll give another suggestion for anyone who is interested.  Make a 6 digit password: use upper and lower case letters, at least one number, and at least one character such as # or ! or whatever.  Memorize it and you can even write it down.  Now, decide that somewhere in the beginning, middle, or end, you are going to INSERT 2 additional letters.  These 2 letters will be the first 2 letters of the name of the website.  For instance:
Let's say that you chose  Rf49#Q  as your password.  And you want to log in to Facebook.  You have decided that you will split your password in the middle.  Therefor, your password for Facebook would be: Rf4fa9#Q.  For Twitter it would be Rf4tw9#Q.

I like the idea, but anything less than 12 completely random characters is too short.  Cracking tools can test every possible combination of 96 character (that's the keyboard) passwords up to 11 in length fairly quickly.  12 is exponentially harder, 13, in theory, is harder, but that assumes 100% random characters.  There are lots of "how to crack passwords" videos from security conferences, so don't expect a dumb attacker.  If allowed to run attacks without limit, over 80% of passwords in a huge database will be cracked in the first week.

We want ours to take at least a year, if not 5 yrs, or never, right?

By using a password manager, length means nothing. We aren't going to type it in anyway.  The math says that 13 is sufficient, at least it was 3 yrs ago, but what's the difference to us with 13, 25, 35, 55, 66 length, random, unique, passwords, if we never type them in?  It doesn't matter, so why not go with a longer one?  There isn't much we can do to fix poor coding on the server-side anyway.  Lots of webapps have been found with terrible password techniques. After discovery, the publication of those issues has been sufficiently embarrassing to corrections to be made, usually.

My stance is that if I can remember any online password, it is much too short.  Thanks to a password manager, I have hundreds of long, unique, passwords, most using completely unique login names.  Using centralized logins like google, twitter, facebook, help those systems track us and combine data between commonly used websites, so I don't do it.  We all have different privacy considerations, I suppose.

Some webapps don't allow sufficiently long passwords nor 2FA.  For those, I use very long logins with random characters ... which I don't know either. 

One of the best protections for login security is to use 2FA with a hardware device.  This raises some other complexities, like being able to access accounts from different devices may not be possible.  A phone should never be considered a "hardware device" for security. For most people, their phone is the least secure device they use. Sad to say, but all that 3rd party software seems to use root-kit like tools to have free reign over all the data and connections from our phones. Beware.

All things being the same, longer is better, for passwords.

---

