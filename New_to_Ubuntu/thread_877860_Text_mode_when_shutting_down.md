---
title: "Text mode when shutting down"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by el-mar01 on 2008-08-02
Hi all,

I have a weird problem ...

When I start ubuntu it boots up fine and shows the usplash correctly but when I shut down ubuntu shows text mode when it is in the process of shutting down (It does show the usplash at the very last minute before the computer shuts off)

I don't think theres anything wrong with my system because everything seems to work fine.

Thanks very much,
el-mar01

---

### Post by aheckler on 2008-08-02
Mine does this too, but it's never been a problem or anything.

---

### Post by mudrain911 on 2008-08-02
I posted about this a few days ago. This is one of those problems that is just there for some people, and it will probably take some updates from Ubuntu to fix it. Its coming up with stuff about the Network Manager right?

---

### Post by coffeecat on 2008-08-02
Have a look at my post in [this thread]("http://ubuntuforums.org/showthread.php?t=865670"). Is this what you were after?

---

### Post by el-mar01 on 2008-08-02
> **coffeecat said:**
> Have a look at my post in [this thread]("http://ubuntuforums.org/showthread.php?t=865670"). Is this what you were after?

Yeah I tried searching but couldn't come up with that thread thanks.

> **mudrain911 said:**
> Its coming up with stuff about the Network Manager right?

Yeah that is correct.

---

### Post by mudrain911 on 2008-08-02
Coffeecat's solution didn't work for me, but it says it works for alot of people. Some people don't even have this problem at all, some do and can fix it. I think I'm just stuck with it hehe. I hope you can fix yours!

---

### Post by coffeecat on 2008-08-02
> **mudrain911 said:**
> Coffeecat's solution didn't work for me, but it says it works for alot of people.

It wasn't mine. I simply found it and passed it along. :) I came across a thread the other day (sorry, haven't got the link) where someone had a different fix which was to open the login window manager, click on the default theme, close the login window manager, reopen it and find that a different theme was now ticked ( :? ), reselect the default theme and then close the login manager.

Or something like that.... :( Sounds like voodoo to me. :-k

---

### Post by mudrain911 on 2008-08-02
I saw that one too... Also tried it. Didn't work for me either. I'm not really worried about it anymore, I'm just glad I have Xubuntu instead of Windows now :)

---

### Post by Troll_the_Great on 2008-08-02
There's nothing to worry about.It's just the order in which the daemons shut down.If you see the text it means that the display manager shuts down before other processes.So, without a display manager, you just see lines of text.
Cheers!

---

