---
title: "Forced to create password for administrator account"
date: 2012-04-25
forum: Recurring Discussions
---

### Post by Time Light on 2012-04-25
There's been one problem I've had since I installed Ubuntu to run alongside Windows, I assume this would also be the same if it was installed to replace the other operating system as well, the Wubi installer prompts you to create a password upon typing in the user account name and if you don't put in a password and just put in the user account name, it ends up saying to create a password. In Windows and Mac OS X, you never were forced to create a password.

Oh and what's worse... is if you remove the password on your Admin account in System Settings > User Accounts, you won't be able to authenticate whenever you try to install something, because it requests for a password and putting in no password at all isn't going to work, it will just act as if you put in an invalid password. This is what I call "getting locked out of privileges".

If only if Ubuntu could be more like Windows and Mac OS X, besides... I'm finding the "Authenticate" window that comes up whenever you install something or accessing somewhere a nuisance, 'cause it always requests for your password.

Another thing is... that there are some places that cannot be accessed even by an account that is the administrator, places that are accessible only to the root account, and some areas that you can't move files and folders into areas that are outside your user account "home" folder.

If only if that can all be changed... if only if it could be more like Windows and Mac OS X.

---

### Post by techsupport on 2012-04-25
This is a Wubi issue. If you installed Ubuntu to your hard drive normally this wouldn't be a problem. 

> **Time Light said:**
> There's been one problem I've had since I installed Ubuntu to run alongside Windows, I assume this would also be the same if it was installed to replace the other operating system as well, the Wubi installer prompts you to create a password upon typing in the user account name and if you don't put in a password and just put in the user account name, it ends up saying to create a password. In Windows and Mac OS X, you never were forced to create a password.

Oh and what's worse... is if you remove the password on your Admin account in System Settings > User Accounts, you won't be able to authenticate whenever you try to install something, because it requests for a password and putting in no password at all isn't going to work, it will just act as if you put in an invalid password. This is what I call "getting locked out of privileges".

If only if Ubuntu could be more like Windows and Mac OS X, besides... I'm finding the "Authenticate" window that comes up whenever you install something or accessing somewhere a nuisance, 'cause it always requests for your password.

Another thing is... that there are some places that cannot be accessed even by an account that is the administrator, places that are accessible only to the root account, and some areas that you can't move files and folders into areas that are outside your user account "home" folder.

If only if that can all be changed... if only if it could be more like Windows and Mac OS X.

---

### Post by Time Light on 2012-04-25
> **techsupport said:**
> This is a Wubi issue. If you installed Ubuntu to your hard drive normally this wouldn't be a problem.

Then I just wonder how am I going to remove the admin password without being prompted to authenticate whenever I try to install something?

---

### Post by lisati on 2012-04-25
Welcome to the world of *nix. Please be reassured that the "need" for a password isn't deliberately forced upon you. A short article describing the whys and wherefores more eloquently than I could can be found here: [http://www.ucl.ac.uk/isd/common/registration/passwords/faq/password_purpose](http://www.ucl.ac.uk/isd/common/registration/passwords/faq/password_purpose)

---

### Post by sffvba[e0rt on 2012-04-25
Please note that Linux != Windows.

Your password you create gives you the power of root via sudo - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Trying to run Ubuntu exclusively as root to prevent being asked your password is not supported on this forum - [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)


Regards
404

edit: Ninja'd :)

---

### Post by Time Light on 2012-04-25
> **not found said:**
> Please note that Linux != Windows.

Your password you create gives you the power of root via sudo - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**Trying to run Ubuntu exclusively as root to prevent being asked your password is not supported on this forum - [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)**


Regards
404

edit: Ninja'd :)
Hm... if only if Ubuntu could at least give people a choice if they'd like to have their account as root without a password and display a warning about it.

---

### Post by lisati on 2012-04-25
> **Time Light said:**
> Hm... if only if Ubuntu could at least give people a choice if they'd like to have their account as root without a password and display a warning about it.
You are given a choice: the extra layer of security that the requirement for a password introduces, or an increased risk of accidental damage to your system or compromising of your personal details.

Yes, there is am annoyance factor, but as you get your system configured the way you want, this will reduce.

---

### Post by Grenage on 2012-04-25
> **Time Light said:**
> Hm... if only if Ubuntu could at least give people a choice if they'd like to have their account as root without a password and display a warning about it.

While I used to be in your camp, and would be irritated by the necessity - that changed.  Experience has taught me that if you allow such an option for the handful, a much larger chunk will take it out of laziness.

XP installs of old still cry out in the night.

---

### Post by Elfy on 2012-04-25
*Thread moved to **Recurring Discussions**.*

---

### Post by haqking on 2012-04-25
> **Time Light said:**
> Hm... if only if Ubuntu could at least give people a choice if they'd like to have their account as root without a password and display a warning about it.

You can have your account as root.

If you dont know how or the consequences of such then you shouldnt be using root IMO

Peace

---

### Post by Time Light on 2012-04-25
> **haqking said:**
> You can have your account as root.

If you dont know how or the consequences of such then you shouldnt be using root IMO

Peace
Yeah, but I was actually thinking about having that choice during the wubi installer and during when you're starting up Ubuntu for the first time. It would be brilliant, 'cause... I feel that forcing things is a terrible thing to do.

---

### Post by Elfy on 2012-04-25
> **Time Light said:**
> Yeah, but I was actually thinking about having that choice during the wubi installer and during when you're starting up Ubuntu for the first time. It would be brilliant, 'cause... I feel that forcing things is a terrible thing to do.

Why?

To reinforce what you've done elsewhere? 

Did you read the answers you got on askubuntu for exactly the same question ? The answer is unlikely to be any different.

---

### Post by haqking on 2012-04-25
> **Time Light said:**
> Yeah, but I was actually thinking about having that choice during the wubi installer and during when you're starting up Ubuntu for the first time. It would be brilliant, 'cause... I feel that forcing things is a terrible thing to do.

Its not forced, you can do it if you know how.

Same as other things people complain about like Unity or the default wallpaper, it is not forced and can be changed if you know how.

The fact is logging in as root can be hazardous especially if web browsing, that being said it doesnt mean you cant.

Like i said though if you dont know how to then there is even more reason not to which is exactly why Ubuntu chooses not to enable it by default.

Peadce

---

### Post by Time Light on 2012-04-27
> **forestpiskie said:**
> Why?

To reinforce what you've done elsewhere? 

Did you read the answers you got on askubuntu for exactly the same question ? The answer is unlikely to be any different.
As soon as I read your post, I checked askubuntu and pretty much most of the answers are... as you say, unlikely to be any different. Though I may be new to Linux, I'm the only person that uses the computer... and I wouldn't mind someone else using it on my account if they're using it for a good reason, if one of my friends came over, which is not often.
> **haqking said:**
> Its not forced, you can do it if you know how.

Same as other things people complain about like Unity or the default wallpaper, it is not forced and can be changed if you know how.

The fact is logging in as root can be hazardous especially if web browsing, that being said it doesnt mean you cant.

Like i said though if you dont know how to then there is even more reason not to which is exactly why Ubuntu chooses not to enable it by default.

Peadce
Yeah, I see what you mean, I wouldn't complain about the Unity or the default wallpaper. But of course, once I read up somewhere on how to login to root on the graphical interface, then I won't have to worry about the password anymore. After all, I really enjoy open source software and all of the free software, so I very much enjoy Ubuntu just as much as any open source software.

---

