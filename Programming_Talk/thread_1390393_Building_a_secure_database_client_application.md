---
title: "Building a secure database client application"
date: 2010-01-25
forum: Programming Talk
---

### Post by lykwydchykyn on 2010-01-25
Here's a question I've been mulling over for a while that might come up for me in the next year at work.

Suppose I've been tasked at building a multi-user database application that will be working with sensitive data.  They don't want a web application, they'd rather have a local desktop application.

How would you go about managing secure connections to the database?

In other words, you need to authenticate to the database in some way.  Do your users use database accounts, or are you storing separate user accounts in a database table the way web applications do, and authenticating to the database through a master account?

Much of the vertical software I support at work uses the latter approach (storing the master username/password for the db in a config file or registry key), but it seems horribly insecure to me.  Not only do you have a single database account with absolute power over the data, but changing the password for that account regularly is impossible because you'd have to update every single client with the new master password.

Has anyone built a client like this, and how did you approach user security?

---

### Post by dwhitney67 on 2010-01-25
Why not assume that the Linux (or is it Unix) account and password are sufficient guards against unauthorized access to the system, and hence the database?

Safeguard the DB account/password in a (config) file that can _only_ be read by the user account that is running the application.  Never store account/password information as hard-coded text within the code.  Furthermore, never pass the account/password via the command line when running the application.

You did not indicate which database you would be using.  In the past I have used MySQL, and I have found that there are several APIs that one can use, for various programming languages, to securely access the database.

---

### Post by lykwydchykyn on 2010-01-25
> **dwhitney67 said:**
> Why not assume that the Linux (or is it Unix) account and password are sufficient guards against unauthorized access to the system, and hence the database?

Safeguard the DB account/password in a (config) file that can _only_ be read by the user account that is running the application.  Never store account/password information as hard-coded text within the code.  Furthermore, never pass the account/password via the command line when running the application.

You did not indicate which database you would be using.  In the past I have used MySQL, and I have found that there are several APIs that one can use, for various programming languages, to securely access the database.

It's more of a design question than an implementation-specific question.  Though I'd probably use Postgresql, it's become our standard for in-house stuff.

Clients would probably be Windows XP, the app would probably be written in Python + pyQT.

The issue I have with using a master access account is that the password is pretty much stuck unless I touch every client with a new set of configs.  That will mean, in practice, that the password will never get changed.  Bad practice.


Is this the way it's done, though?

---

### Post by dwhitney67 on 2010-01-25
> **lykwydchykyn said:**
> It's more of a design question than an implementation-specific question.  Though I'd probably use Postgresql, it's become our standard for in-house stuff.

Clients would probably be Windows XP, the app would probably be written in Python + pyQT.

The issue I have with using a master access account is that the password is pretty much stuck unless I touch every client with a new set of configs.  That will mean, in practice, that the password will never get changed.  Bad practice.


Is this the way it's done, though?

No, it is not bad practice.  Make sure that you Unix/Linux/Windoze accounts are secure.  Where I work, passwords must be changed every 120 days.  They must be 12-characters long, consist of upper- and lowercase letters, numbers, and special characters.

For the database account information, we have no need to change this.  But if we were required to do so, then all we need to do is edit one configuration file.  Only two  users that can read/edit that configuration file:  the System Administrator and the owner of the file.

---

### Post by mikejonesey on 2010-01-25
your main vunrebility (no different to web apps) is your lan being hacked or monitored, it's a shame nonce tech does not exists for db acount passwords (date in salt for md5 eg, md5(date()+'password'+'endS4ltKEY')), i use this tech for file download / upload via curl. (this makes it imposible for the password to be hacked as it changes every few seconds). however all majour dbs provide ssl support via api's which makes wan part secure enough (works like vpn).

 - So long as you keep your lan secure your software will be secure.
- if data contained is finalcial or sesitive ssl is a cheap option to increase security.

---

### Post by Some Penguin on 2010-01-25
> **dwhitney67 said:**
> No, it is not bad practice.  Make sure that you Unix/Linux/Windoze accounts are secure.  Where I work, passwords must be changed every 120 days.  They must be 12-characters long, consist of upper- and lowercase letters, numbers, and special characters.

For the database account information, we have no need to change this.  But if we were required to do so, then all we need to do is edit one configuration file.  Only two  users that can read/edit that configuration file:  the System Administrator and the owner of the file.

With only one account, it becomes very difficult to have a sane audit trail.  Furthermore, you have greatly increased the risk to any compromise.  And in addition, it would be foolhardy to assume that Linux's security model is perfect, considering that it is not particularly rare for root exploits (let alone the more common run-as-user exploits) to still be found.

---

### Post by lykwydchykyn on 2010-01-26
> **Some Penguin said:**
> With only one account, it becomes very difficult to have a sane audit trail.  Furthermore, you have greatly increased the risk to any compromise.  And in addition, it would be foolhardy to assume that Linux's security model is perfect, considering that it is not particularly rare for root exploits (let alone the more common run-as-user exploits) to still be found.

What sort of design would you recommend?

---

### Post by Some Penguin on 2010-01-26
Separate database accounts.  Note that depending on the database (I'm much more familiar with MySQL than PostgreSQL), it might be quite tractable to have multiple user accounts with overlapping permissions if necessary.  For the user's convenience, it's probably a good idea for the application to cache (in memory) the db credentials. 

That way, it's easier to avoid users from messing up data they shouldn't really have access to (less possible damage from any badly-written stored procedures, for instance), your logs will be more informative, and there may be other benefits such as multiple user accounts make it easier to figure out who's queries seem to be causing deadlocks.  And if you need to shut down somebody's access, it's much easier to do so without affecting anybody else's.

I'm not too familiar with PostgreSQL but browsing the docs, I see that you can use GSSAPI + Kerberos, for instance, as well as more ordinary password-based authentication and quite a few other means.  It also provides SSL for link-layer encryption, making eavesdropping less interesting.  

If you use password-based methods, and you let the users set their passwords (passing them through an ALTER USER command), you might want to run the potential password through some cracklib-type tests.

---

