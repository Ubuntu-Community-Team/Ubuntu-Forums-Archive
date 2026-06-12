---
title: "how do I set my first password"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by SirRoverofIvories on 2013-10-06
I am trying to add items from the software center and it requires authentication with the administrator's password.   I am the administrator, but am  unable to set a password as it appears that there is already a password.   How can I find out what this password is so that I can change it.

---

### Post by DuckHook on 2013-10-06
Assuming that you have the default install, your "administrator" password is that same one you log in with.

---

### Post by SirRoverofIvories on 2013-10-06
What is a "default install"?    I do not log in with a password.

---

### Post by DuckHook on 2013-10-07
You had to have defined a password when you installed. As far as I can remember, the system will not permit you to proceed with the install without one. You probably turned on "Login without password" when you set up your install, a very bad practice that many new users port from their Windows habits into Ubuntu. The downside is that you now don't recall what that password was. Since Linux is very security-based, that password is all-important. As you have discovered, the operating system will not allow anyone to install apps willy-nilly or change basic elements of the OS without password authentication. This is one of the main reasons (but there are others) that Linux has been able to avoid the viruses that infest Windows.

[This]("http://www.psychocats.net/ubuntu/resetpassword") site provides a detailed and step-by-step method to define a new password. After you have finished the procedure, I highly, highly recommend that you turn login password authentication back on and start cultivating good security practices. You will find this to be a godsend later, when your friends must battle malware from every direction while you have hardened your system into a very tough nut to crack. The following are all good security websites for new users:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

---

### Post by deadflowr on 2013-10-07
> **SirRoverofIvories said:**
> I am trying to add items from the software center and it requires authentication with the administrator's password.   I am the administrator, but am  unable to set a password as it appears that there is already a password.   How can I find out what this password is so that I can change it.

Unless you know the password, follow the psychocats guide posted earlier.

How exactly did you come across this Operating system.
Did you install it yourself, or was it given to you?

If you installed it yourself, then you set the password.
It doesn't finish installing unless you do.

---

### Post by SirRoverofIvories on 2013-10-07
Thank you.   The problem is that I did not install Ubuntu but was done by a trusted Geek while the computer was being "cleaned."   I will call on Monday and try to get the password from  him.   If he does not remember it, can I use my CD and just reinstall Ubuntu.   The reason I had him install it was that when I tried to install before the computer was cleaned there was a Windows8 problem that prevented it and the Ubuntu instructions were confusing to me.
Thanks for your help!

---

### Post by DuckHook on 2013-10-07
Ah. Thanks for clarification. I hope you don't mind my saying this, but  in future, providing such context and background at the outset prevents hours of  unnecessary dead ends and confusion. (@deadflowr--good antennae!).

If you follow the instructions in my previous link, you will not have to reinstall Ubuntu. On the other hand, I firmly believe that installing it on your own from scratch is not only instructive, but will assist you if you find yourself needing to do so again. Whichever option you choose, I strongly urge you to not just leave the password in your "trusted geek's" hands. While in no way impugning the integrity of your trusted geek, it is just bad security (s/he may lose it or have unscrupulous roommates) and the opposite of good habit. But, obviously, it's entirely your call.

---

### Post by SirRoverofIvories on 2013-10-08
Thanks to everyone who offered assistance.  I've learn some (read alot - learned some!) and the problem has been solved.  I dropped by Best Buy and the geek who installed Ubuntu told me the password.   I'm operating happily.

One last question.   If I'm the only one using the computer (and live alone) do I need to use a password to start.   I do not save anything on the computer.   Everything is saved on a flashdrive.   Thanks again.

---

### Post by deadflowr on 2013-10-08
You can it the computer to auto-login.
Go to the system settings > user accounts(or whatever the name is for you version of Ubuntu) and unlock it.
You'll need to you your password to unlock, then set the automatic login switch to on.
Whatever you do though, DO NOT do anything to the line about password, some user think if you disable the password then you can run the system without needing it, but what happens is disabling the password effectively disables the users account.

Another thing you can do is disable the lock in brightness and lock in system settings.
That way, you won't need to enter your password if your screensaver goes off.
Or simply set the screensaver to never.

Other than that, you should only need to use your password to do system wide changes.
Installing new software and some updates will require authentication.

---

### Post by Elfy on 2013-10-08
> **SirRoverofIvories said:**
> ...  I dropped by Best Buy and the geek who installed Ubuntu told me the password.   I'm operating happily...

I'd be changing that then.

---

### Post by DuckHook on 2013-10-08
> **SirRoverofIvories said:**
> If I'm the only one using the computer (and live alone) do I need to use a password to start.I find that we are all creatures of habit. If we don't enforce authentication at log in, we tend to stop enforcing it at any other time either. Conversely, if we get used to this discipline, then we aren't "bothered" by it when it counts even more. I practice login authentication religiously because, among other reasons, it is this strict adherence to Linux security that allows me to kiss antivirus software goodbye. I would rather put up with 2 seconds of login authentication than 15 minutes of signature downloads, disk thrashing and filesystem audits, never mind the permanently hobbled processing, squandered resources and system bloat caused by antivirus routines.

Maybe it's just me, but I've never understood why Windows users prefer installing and maintaining motion sensors, closed-circuit cameras, electric fences, pits, tripwires, antipersonnel mines and laser-guided infrared homing missiles just so they can have the "convenience" of leaving their front door unlocked. It's pretty much the definition of insanity.

Sorry for the rant. Security blindness just gets me all worked up.

---

### Post by heir4c on 2013-10-08
@SirRoverofIvories, In Ubuntu root have no password. In other distro 'he' have. In Ubuntu, the user who is made when it is installed, (s)he have a password and with that (s)he can become root for different reasons. When the password is given, the user get root rights for about 15 min. (or is it root privileges? I try to search it with google but I doubt)   Than the system ask again for the password. So just for that specific job are the root privileges given. No other command/job/program that need root rights can be executed.

---

