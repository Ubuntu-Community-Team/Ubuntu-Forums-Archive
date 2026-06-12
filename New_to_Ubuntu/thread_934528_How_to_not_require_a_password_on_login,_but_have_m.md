---
title: "How to not require a password on login, but have multiple users?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Madman6510 on 2008-09-30
Is there any way to get around the 6 character password limit, to allow an empty password?

I'm setting it up for family, and one of the users would be fairly young, and not able to remember a password easily, while one of the others would whine too much about how they have to have a password, and Windows doesn't need it ](*,)

---

### Post by Gannon8 on 2008-09-30
I think linux requires that you have a password (Why not?). Especially administrators with sudo access.

---

### Post by Madman6510 on 2008-09-30
Don't think so. Plain Debian didn't require a password last time I used it.

---

### Post by wolfen69 on 2008-09-30
> **Madman6510 said:**
> Don't think so. Plain Debian didn't require a password last time I used it.

yes it does. you can go to system>administration>login window and set it for auto login. you will have to do this for each user.

---

### Post by aomlives on 2008-09-30
> **Madman6510 said:**
> Is there any way to get around the 6 character password limit, to allow an empty password?

I'm setting it up for family, and one of the users would be fairly young, and not able to remember a password easily, while one of the others would whine too much about how they have to have a password, and Windows doesn't need it ](*,)

I think you can change the minimum password length to 0 using the instructions [here]("http://ubuntuforums.org/showpost.php?p=2073899&postcount=2"), and then set empty passwords for all your users. Then you can get the login screen with all the users listed where you can simply click on them (and hit enter) just like in Windows which is what you want I believe.

Hope this helps.

---

### Post by KIAaze on 2008-09-30
Here's another way: [http://ubuntunext810.blogspot.com/2008/09/guest-session.html](http://ubuntunext810.blogspot.com/2008/09/guest-session.html)

At the end, it explains how to set up a passwordless guest account at the login screen.
You should be able to add all passwordless users that way.

---

### Post by smuki on 2008-09-30
Good thing I looked here, I am going to have the same issue go on in the next month or so when this new machine is ready to go live.

---

### Post by markbuntu on 2008-09-30
Autologin is very dangerous. If your video gets screwed up you have no way to get into gnome safe mode. Timed login is much better, automatic and leaves you time to get into gnome safe mode when you need to. I set it at 10 seconds.

---

