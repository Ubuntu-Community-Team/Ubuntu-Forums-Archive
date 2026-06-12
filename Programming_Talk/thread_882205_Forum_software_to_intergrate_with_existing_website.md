---
title: "Forum software to intergrate with existing website"
date: 2008-08-06
forum: Programming Talk
---

### Post by drubin on 2008-08-06
I have a website with an existing user base. Now I would very much like to integrate some sort of forum software onto the site.

Here are the draw backs. :(
1) Needs to maintain credentials across both systems. (Ie on password updates) I can not expect the user to sign up 2 times.
2) Needs to maintain login session, This will only be logged in from the website.

This "sync" would only need to happen from the main site being the primary data source/login system. 

I have looked into a couple I started with PHPBB as it was free and opensource, but I struggled to find an easy way to incorporate the single login that I would need. PHPBB is a big project so yes I could change some stuff around to get it to work but it worries me that PHPBB is such a widely used product that when ever a security patch is released or a flaw is found it would take me for ever to re implement "the auth system" with the updated phpbb code.


Has any one done this before and have some advice. The forum software does not have to be as advanced and phpbb. I am sure that this has been done a few times as  it seems like a common request but i can not seem to find resources.

---

### Post by nanotube on 2008-08-07
well, so your website stores the usernames/passwords in some kind of a database, right? so, what you need to do is write a custom script on the backend to sync that user/pass db with the one in phpbb (or whatever forum you end up using).

to maintain session, you'd have to look at how phpbb sets the session cookies on user login, and have your site set those cookies (in addition to the regular site cookies) upon login. even better - just use the phpbb-style cookies for authentication, rather than your custom site cookies, so you only have to maintain one set of them, and so that if a user logs in from phpbb, your site also recognizes his login, and the other way around.

these mods would allow you to do what you want, without modifying phpbb source code in any way (thus preserving ability to easily upgrade for security patches, etc - until they change their database layout or cookie format, neither of which is very likely).

---

### Post by drubin on 2008-08-07
> **nanotube said:**
> well, so your website stores the usernames/passwords in some kind of a database, right? so, what you need to do is write a custom script on the backend to sync that user/pass db with the one in phpbb (or whatever forum you end up using).

That was the exact idea. I was hoping this had been done before or at least pointers to sites with explanations/tutorials.

---

### Post by Reiger on 2008-08-07
Right, the scenario is: your DB x which currently stores every userinfo you may need for the website, would be expanded to include the tables required for the forum?

Then I don't really see the problem because you would already have an "ON UPDATE CASCADE" trigger? So the DB would auto-sync it accross 'the board'. Therefore, me is :confused:

---

### Post by drubin on 2008-08-07
> **Reiger said:**
> Right, the scenario is: your DB x which currently stores every userinfo you may need for the website, would be expanded to include the tables required for the forum?

Then I don't really see the problem because you would already have an "ON UPDATE CASCADE" trigger? So the DB would auto-sync it accross 'the board'. Therefore, me is :confused:

Triggers might an a simpler solution...  I was originally thinking of creating a view on the users table. but the columns are stored in a different format (the passwords are stored encrypted differently)
**EDIT** Has no one come cross this being solved any where, it seems like a simple solution?

Or does any one have any other free opensource forums (php) that are like from 2000 all the ones I have found on freshmeat were last maintained in 2000

---

