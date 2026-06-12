---
title: "Sidebar Auto Hide when app pushes it not working on 12.04"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by tgwaste on 2012-05-07
Hello,
  I am on ubuntu 12.04 64bit and I noticed that when an app touches the sidebar it no longer auto hides anymore.  Is there a way to turn that back on?

Thanks!

---

### Post by Derek Karpinski on 2012-05-07
The 'Dodge Windows' option for the unity launcher doesn't exist in 12.04.  You can only auto-hide, or never hide.

To find the options, go to:

System Settings > Appearance > Behavior

---

### Post by tgwaste on 2012-05-07
Damn.  What a shame.  I thought things were supposed to get better in updates and not worse?  A toggle for it would had been nice Ubuntu! :/

---

### Post by Derek Karpinski on 2012-05-07
> **tgwaste said:**
> Damn.  What a shame.  I thought things were supposed to get better in updates and not worse?  A toggle for it would had been nice Ubuntu! :/

Agreed, I loved 'dodge windows', but I've gotten used to 'auto hide'........and besides, I'm getting what I paid for! :p

Besides, there are some inventive users that have written code to get dodge windows back. I'm uncomfortable messing around with this, but you might feel differently.

[https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior](https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior)

---

### Post by colin-m on 2012-05-10
re [https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior](https://help.ubuntu.com/community/Unity-ReplaceDodgeWindowsBehavior)

 I usedthe PPA method, it's the easiest and it does work.

---

### Post by tgwaste on 2012-05-10
You should never under any circumstances install and use CCSM.  There is a reason this garbage POS of a program doesnt come with Ubuntu.

It is the worst software of all time.

---

### Post by Derek Karpinski on 2012-05-10
> **tgwaste said:**
> You should never under any circumstances install and use CCSM.  There is a reason this garbage POS of a program doesnt come with Ubuntu.

It is the worst software of all time.

It's not a POS.......its actually quite powerful......but there definitely are dragons inside! Be very careful changing things if you're not sure what you're doing.

Most people recommend 'My Unity' or 'Ubuntu Tweak' to handle most basic configurations to unity.

---

### Post by tgwaste on 2012-05-10
> **Derek Karpinski said:**
> It's not a POS.......its actually quite powerful......but there definitely are dragons inside! Be very careful changing things if you're not sure what you're doing.

Most people recommend 'My Unity' or 'Ubuntu Tweak' to handle most basic configurations to unity.

if you have to be careful with an app that alters the core components of your desktop to the point where you could need to do a complete reinstall (like me _every single time_ ive ever tried it) then the app is not designed properly and should not be used.

the fact that we have come to a point where we can just use some silly phrase like 'there be dragons inside' to excuse a **** poor programs design is frightening.


sorry i dont meant to be offensive to you but I can not stress enough how horrible this program is.

---

### Post by Baldrick_NZ on 2012-05-10
> **tgwaste said:**
> You should never under any circumstances install and use CCSM.  There is a reason this garbage POS of a program doesnt come with Ubuntu.

It is the worst software of all time.

Ahem... Perhaps you're not aware that Ubuntu comes pre-installed with Compiz. The thing you have to install is the config manager.

The ppa concerned works as good as the original dodge effect did, and all you need ccsm for is to activate it. One simple step, changing from 'Never Hide' to 'Dodge Windows', and you're all set.

---

### Post by eode on 2012-06-26
> **tgwaste said:**
> if you have to be careful with an app that alters the core components of your desktop to the point where you could need to do a complete reinstall (like me _every single time_ ive ever tried it) then the app is not designed properly and should not be used.

the fact that we have come to a point where we can just use some silly phrase like 'there be dragons inside' to excuse a **** poor programs design is frightening.


sorry i dont meant to be offensive to you but I can not stress enough how horrible this program is.

No offense, but making uninformed, opinionated assertions and excusing it with 'no offense' is just morally wrong, and that means you and I are both bad people.

If you know what you're doing, it's an excellent program.  ..but take a cue from the complexity, and from the warning message it gives you when you start (at least in 12.04 it does, and I think it did so before that).  This is not a tool for someone who doesn't know what they're messing with.

***Quote:***
[I]"**CCSM is an advanced tool. Use with caution.**

This tool allows you to deeply configure Compiz's settings. Some options may be incompatible with each other. Unless used with care, it is possible to be left with an unusable desktop."
[/I]

..but, for the record, CCSM affects the user you're logged into, and that's it.  It won't cause you to need to reinstall Ubuntu, except in very, very rare circumstances (If your system freezes, you will have to power off without shutting down, and in rare circumstances, that can cause you to need to reinstall).  However, it might break the desktop environment *for that user account*.  What does this mean?  That user account can't usefully log into anything but a terminal, but other user accounts are still ok.

If your system *does* freeze, then instead of shutting off right away, [read this link]("http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717") and try that out.

If you don't have any other users, and already messed up your only user, you can add a new user at the terminal (ctrl-alt-f1).  Log in as the user you messed up, then create the new user:
```
sudo adduser newguy
sudo adduser newguy sudo
exit
```
then ctrl-alt-f7 or ctrl-alt-f8 to get back to the graphical login, and log in as 'newguy' (who can create and delete accounts by clicking the 'unlock' button in the 'user accounts' control panel)


If you are unsure about whether or not you know enough to use CCSM without breaking your system, or just wish to be extra careful, then:

1) Create a new admin user, just in case.  It'll save you from having to log into a console to do so.
2) Create a new normal user called 'testccsm' or something, and use that user to test unfamiliar CCSM settings.

..if something goes wrong in the test user account, you can always delete your test user along with his files.  If you mess something up in your own account, you can log in as the admin user you created, and create a new account for yourself, then manually copy over all the normal files from your old home directory.

---

### Post by tgwaste on 2012-06-26
> **eode said:**
> No offense, but making uninformed, opinionated assertions and excusing it with 'no offense' is just morally wrong, and that means you and I are both bad people.

If you know what you're doing, it's an excellent program.  ..but take a cue from the complexity, and from the warning message it gives you when you start (at least in 12.04 it does, and I think it did so before that).  This is not a tool for someone who doesn't know what they're messing with.

***Quote:***
[I]"**CCSM is an advanced tool. Use with caution.**

This tool allows you to deeply configure Compiz's settings. Some options may be incompatible with each other. Unless used with care, it is possible to be left with an unusable desktop."
[/I]

..but, for the record, CCSM affects the user you're logged into, and that's it.  It won't cause you to need to reinstall Ubuntu, except in very, very rare circumstances (If your system freezes, you will have to power off without shutting down, and in rare circumstances, that can cause you to need to reinstall).  However, it might break the desktop environment *for that user account*.  What does this mean?  That user account can't usefully log into anything but a terminal, but other user accounts are still ok.

If your system *does* freeze, then instead of shutting off right away, [read this link]("http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717") and try that out.

If you don't have any other users, and already messed up your only user, you can add a new user at the terminal (ctrl-alt-f1).  Log in as the user you messed up, then create the new user:
```
sudo adduser newguy
sudo adduser newguy sudo
exit
```then ctrl-alt-f7 or ctrl-alt-f8 to get back to the graphical login, and log in as 'newguy' (who can create and delete accounts by clicking the 'unlock' button in the 'user accounts' control panel)


If you are unsure about whether or not you know enough to use CCSM without breaking your system, or just wish to be extra careful, then:

1) Create a new admin user, just in case.  It'll save you from having to log into a console to do so.
2) Create a new normal user called 'testccsm' or something, and use that user to test unfamiliar CCSM settings.

..if something goes wrong in the test user account, you can always delete your test user along with his files.  If you mess something up in your own account, you can log in as the admin user you created, and create a new account for yourself, then manually copy over all the normal files from your old home directory.


All of this just to TRY to use an app.  That should tell you something.

Again.. there is a reason this app is not included with Ubuntu and most likely never will be.

---

### Post by eode on 2012-06-29
On the other hand, when you know what you're doing, there's no tool like it.  In about ten minutes, I have a *very* slick, featureful, and useful desktop.

Nothing wrong with the program.  It's just not made for you.  I have no sympathy for anyone who ignores a message that says "You may be left with an unusable desktop", and ends up with an unusable desktop -- and then proceeds to blame the program.  

There are much better people to have sympathy for -- like those who ignore a message that says "You may be left with an unusable desktop", and end up with an unusable desktop, and instead say things like "I broke my computer exploring!  Help me fix it please!"

---

