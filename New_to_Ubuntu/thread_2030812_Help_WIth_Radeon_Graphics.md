---
title: "Help WIth Radeon Graphics"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by DGINSD on 2012-07-21
I have an HP Pavilion G6 with the AMD Radeon HD 6480G Discrete-Class Graphics. I have installed Ubuntu 12.04 and have been using the Catalyst 12.4 proprietary driver (FGLRX) straight from AMD, and have had plenty of issues with it. Mainly I get frozen screens randomly, sometimes I can SYSRQ R E I S U B out and cleanly reboot, other times it's a hard lock and my only option is to hold the power button and force a hard reboot. As you can imagine this is quite frustrating. The second issue is multi-user/fast used switching will cause lock ups, this is also pretty random on what will actually cause the lock up.

So after much searching I've come up with no fixes for these known issues. I'd like to give the open source drivers a run through, but before I go through all this, I'd like to ask others that are, or have used the open source drivers; have you experienced any similar issues or even other issues? To anyone that's perhaps used both what are some of the differences you've noticed?

Also which is the best one to use as I understand there are a few, as well as where to get them and how to install them properly, given that I've already had the proprietary ones installed?

How is the 3D acceleration with the open source drivers. I don't need anything super fancy, I don't play games, but I do like my desktop effects, so I need them to at least do that?

The most important question of all; am I wasting my time trying them out? Will my issues likely still be there regardless?

I appreciate any input anyone can give so if you got a tid-bit you think may be useful, by all means let 'er rip.

---

### Post by Laiquendi on 2012-07-21
I, unfortunately, have an ati "card" in my PC and have had this problems for several years.
After may battles and wasted hours - first thought - no more ati, ever.
Second, more useful for you - open source drivers will be unable to use all power of your ati card, some of them don't support 3D acceleration at all (not sure how it looks precisely), but they are more stable and compatible than ati proprietary drivers.
To simplify - it's a decision between stability (open source) or power (proprietary).
None of them actually gives ideal solution though.

P.S.
II had tried many variants across few years, if you want to i can enclose you with more accurate results, PM me then.

---

### Post by DGINSD on 2012-07-21
> **Laiquendi said:**
> I, unfortunately, have an ati "card" in my PC and have had this problems for several years.
After may battles and wasted hours - first thought - no more ati, ever.
Second, more useful for you - open source drivers will be unable to use all power of your ati card, some of them don't support 3D acceleration at all (not sure how it looks precisely), but they are more stable and compatible than ati proprietary drivers.
To simplify - it's a decision between stability (open source) or power (proprietary).
None of them actually gives ideal solution though.

P.S.
II had tried many variants across few years, if you want to i can enclose you with more accurate results, PM me then.


With all the issues I've had and after reading a Phoronix article stating that my 6 month old, laptops, graphics card will no longer be supported in future Catalyst releases, "No more AMD, ever" is the conclusion I've come to as well.

---

### Post by DGINSD on 2012-07-29
A couple things I noticed that I though might give some clues as to my issues, and get a bump and hopefully the eyes of someone that recognizes the issue.

User switching using the "me menu" user name and clicking them will always cause the lock up. However If I switch with the "switch user account" in the "me menu" I can switch users all day. I noticed the "switch user account" takes me out to the unity greeter, while clicking on the name of users (if they had already been logged in) takes me to GDM like login for that individual user.

I also noticed that if I used the "me menu" usernames to switch users, often after switching users and dropping down the "me menu" users that were logged in but switched from had no check mark next to their names, as if they were never logged in. If I were to switch to one of these users, using the "me menu" drop down usernames the system will lock up, requiring a sysrq R S E I U B to reboot.

The last thing I noticed was if I saw the checkmarks missing, from logged in users usernames, in the drop down "me menu", I could <ctrl> <alt> <f8> and there would be that same GDM style individual user login prompt, waiting for a password. It seemed as if another X session had gotten started on another tty, how or why is beyond me so I'm hoping this will give a clue to someone with more skill than me.

Also if anyone knows or thinks it would be helpful to see some log files let me know which ones, I can now easily duplicate the hang.

---

