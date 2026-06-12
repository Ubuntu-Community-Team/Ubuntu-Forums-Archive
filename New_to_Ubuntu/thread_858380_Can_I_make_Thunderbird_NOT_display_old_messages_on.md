---
title: "Can I make Thunderbird NOT display old messages on startup?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by blazyyo on 2008-07-13
When I open Thunderbird, my previously downloaded mail is available to review, even before entering email password.

Is there a way to change this? I don't want someone else using the computer to read my mail. I don't mind entering my password at each login.

I'm using Ubuntu 8.04 Hardy and Thunderbird 2.0.0.14. Thank you.

---

### Post by msrinath80 on 2008-07-13
> **blazyyo said:**
> When I open Thunderbird, my previously downloaded mail is available to review, even before entering email password.

Is there a way to change this? I don't want someone else using the computer to read my mail. I don't mind entering my password at each login.

I'm using Ubuntu 8.04 Hardy and Thunderbird 2.0.0.14. Thank you.

I think thunderbird has an option somewhere under either preferences or account settings where you can get it to start with a generic page which has hyperlinks to reading/composing messages etc. That way, nobody gets to see your email senders/subjects. Hope that helps.

---

### Post by chrisod on 2008-07-13
Edit / Preferences / Enable Start Page is what the first reply is referring to. I don't think that helps though because the rougue user could simply click on the inbox. It wouldn't ask for a password until it tried to check mail. If it's pop, all the existing mail is there and accessible.

What you need I think is to set Ubuntu to log you out after 5 minutes  of inactivity and set up separate user accounts for anybody else that uses the computer. You do that by setting the screen saver to kick in after 5 minutes and to lock the computer when it does so.

---

### Post by RD1 on 2008-07-13
Take a look here: [http://kb.mozillazine.org/Protect_the_profiles_contents]("http://kb.mozillazine.org/Protect_the_profiles_contents")

.... looks like several methods of securing Thunderbird profiles

I just downloaded and tried the [ProfilePassword extension]("http://nic-nac-project.de/~kaosmos/profilepassword-en.html"). It does ask for a password before showing ANY Thunderbird window or contents. :)

---

### Post by WiseGuy1020 on 2009-06-25
In thunderbird go to Edit >> Prefrences >> Advanced >> Config Editor

Then search for mail.password_protect_local_cache and set it to true.

Peace,

D

---

