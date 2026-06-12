---
title: "A switch to a open-sourced forum software?"
date: 2009-04-20
forum: Recurring Discussions
---

### Post by LinuxGuy1234 on 2009-04-20
This forum uses vBulletin, which is not open source software. How many agree to switch this forum to open-sourced forum software like phpBB?

---

### Post by lisati on 2009-04-20
As I understand it, vBulletin was chosen because it has features that the admins wanted.

---

### Post by mips on 2009-04-20
Yeah and while we are at it they should also design their own open source hardware for the servers to run on ;)

[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)
> **Why does a forum for free software use a proprietary software? **
 While we would love to use an open source solution, vBulletin provides all that we need right now and also much of what we want. Other software does not. Serving this community well is our main priority and so we can/will not use something that does not provide what we require. If anything else provided what we must have and what we really would like to have, we would be using it instead; at this juncture, there is no viable alternative. 


---

### Post by .Maleficus. on 2009-04-20
> **lisati said:**
> As I understand it, vBulletin was chosen because it has features that the admins wanted.
This is correct.  vBulletin is also very well maintained, very stable and pretty much the standard for BB software.  Tons of useful plugins, very good support and with a user base this large, that's the kind of stuff you need.

---

### Post by matthew on 2009-04-20
Moved to Recurring Discussions.

---

### Post by LinuxGuy1234 on 2009-04-30
Time that we need to find out *what* the forum needs to find a open-sourced BB.

---

### Post by TheBuzzSaw on 2009-05-01
Maybe we ought to just rally together and *make* a superior open source alternative. Any PHP/MySQL devs wanna assist me? :P

---

### Post by LinuxGuy1234 on 2009-05-01
I do some PHP. I'm in!

---

### Post by wsonar on 2009-05-01
That's how MS got big is creating something everybody wants and thinks they have to use and being the only one that can provide it.

that and the number one thing licensing

---

### Post by Kareeser on 2009-05-01
An important factor MUST be scalability, efficiency, and robustness.

The Ubuntuforums database probably gets reads and writes every single second, and it must never go down or lost a record in the process.

I'm guessing vBulletin has a good tradeoff of speed vs. features that the UbuntuForums admins prefer.

---

### Post by pparks1 on 2009-05-01
phpBB is a good system, but it has tons of patches and it's a little tough to maintain.   For commercial use, VBulletin is pretty much where it is at.  I think it's important to use the best product for the job..and I'm sure if phpBB met all of the needs of this forum, they would use it.

---

### Post by LinuxGuy1234 on 2009-05-02
[SMF claims to have some features, but the admins would need to trial it first before we migrate the vBuletin database to SMF... and for features they need plugins and make a theme...]("http://www.simplemachines.org/about/features.php")

---

### Post by matthew on 2009-05-02
(politely and gently, because I know those requesting the change mean well)

FYI, we have made public statements about this several times, but I'll chime in again. 

One of the major factors is the admin tools available in vBulletin. They are unsurpassed, and I have used phpBB, SMF, and others for other projects. They serve a great purpose and are good products, but are nowhere near the same level on the backend.

Another factor at this point is the size of the database. Our DB is HUGE, and a migration would not be easy and would be likely to cause some serious problems and potential data loss, even for experienced DB admins. It would not be a good idea.

Sorry.

For what it's worth, I do use SMF on two other projects.

---

### Post by Phreaker on 2009-05-03
phpBB is really great, but Ubuntu Forums should make a beta to test it

---

### Post by LinuxGuy1234 on 2009-05-03
> **matthew said:**
> (politely and gently, because I know those requesting the change mean well)

FYI, we have made public statements about this several times, but I'll chime in again. 

One of the major factors is the admin tools available in vBulletin. They are unsurpassed, and I have used phpBB, SMF, and others for other projects. They serve a great purpose and are good products, but are nowhere near the same level on the backend.

Another factor at this point is the size of the database. Our DB is HUGE, and a migration would not be easy and would be likely to cause some serious problems and potential data loss, even for experienced DB admins. It would not be a good idea.

Sorry.

For what it's worth, I do use SMF on two other projects.

I have not experimented with vBulletin, but have used YaBB, SMF, phpBB and PunBB.

---

