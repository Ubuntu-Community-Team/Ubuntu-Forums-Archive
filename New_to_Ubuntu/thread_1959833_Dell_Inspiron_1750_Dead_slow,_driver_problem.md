---
title: "Dell Inspiron 1750 Dead slow, driver problem?"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by ljt3759 on 2012-04-16
Hey guys, I've just decided to start using Ubuntu again, first I'll give you my problems(s):

I'm dual booting along side windows 7 (I used wubi)

My computer is dead slow running ubuntu, which is strange since I have 4gb of ram with (I believe) a 2.1ghz processor (64 bit).

I tried playing some games to see if they would be slow too, and they are, so I thought this might be a driver problem, I've gone into driver settings and it says "no propriety drivers are in use on this system" also there are no drivers available to download, it's just a blank space.(I don't know what drivers I need either)

I don't know all that much about Linux, only used it briefly before, now I'm in a bit of a pickle.

Any help would be amazing, thanks for your time.

---

### Post by ljt3759 on 2012-04-16
Bump ^

---

### Post by PhantomTurtle on 2012-04-16
First of all, you can only bump every 24 hours. I'm not a mod, but you might get in trouble if you keep doing that. The way Wubi is designed, it slows you system down a bit. It shouldn't cause a very big degration in speed though. Try dual booting without using Wubi. Here is a tutorial, it is for 11.04, but will work with 11.10(it's basically the same). [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/]("http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/").

---

### Post by Mark Phelps on 2012-04-16
The Additional Drivers is only for proprietary drivers -- which is basically AMD and Nvidia, not Intel.  So, you won't see any drivers being offered there.

Are these MS Window games?  If so, you're probably not going to have a good experience running them in Linux as they expect to have the MS Windows video drivers installed -- and may require a higher DirectX version than the Intel Linux drivers provide.

While installing under Wubi does yield a system that is a little bit slower, it's not enough difference that you would really notice it.

IF your Ubuntu is running REAL slow, there is a different problem involved than simply having installed using Wubi.

---

### Post by ljt3759 on 2012-04-16
Sorry for the early bump, I should have read the rules, forgot to in my panic :(

I may do a dual boot then, or maybe I'll downgrade to an older version of ubuntu, could that help? 

Thanks for the tutorial, I'll check it out.

Thanks for that Mark Phelps, I know it's not the drivers now, glad I know, I won't be looking for another hour for the right drivers.

No, these were games from the standard linux repositories, most of them quite basic, although I know I have a terrible graphics card. (compared to my other hardware)

Do you know what else it could be?

edit: just defragged windows 7 was 9% fragged (If my memory is correct)

Thanks for the help guys.

---

### Post by PhantomTurtle on 2012-04-16
Like Mark said, WUBI doesn't make a big difference in performance. There could be something wrong with your installation.

---

### Post by ljt3759 on 2012-04-17
Oh yes that reminds me!

I got this error: [http://ubuntuforums.org/showthread.php?t=1879950](http://ubuntuforums.org/showthread.php?t=1879950)

And thus used the wubi installer twice also, here is some info on the bug: [https://bugs.launchpad.net/wubi/+bug/862003](https://bugs.launchpad.net/wubi/+bug/862003)

I think this is it then.

---

### Post by mastablasta on 2012-04-17
it would help if told us what GPU do you have.
latest intel GPU should have relatively good support and are not as bad as some older version of their chips.

---

### Post by PhantomTurtle on 2012-04-17
> **ljt3759 said:**
> Oh yes that reminds me!

I got this error: [http://ubuntuforums.org/showthread.php?t=1879950](http://ubuntuforums.org/showthread.php?t=1879950)

And thus used the wubi installer twice also, here is some info on the bug: [https://bugs.launchpad.net/wubi/+bug/862003](https://bugs.launchpad.net/wubi/+bug/862003)

I think this is it then.

It looks like some kind of permission issue. I would remove WUBI and install again, make sure to open it as an administrator.

---

### Post by Mark Phelps on 2012-04-18
> **ljt3759 said:**
> ... I think this is it then.

Sorry to disappoint, but that only affects installation.

IF you can boot into Ubuntu and run it, that bug is not going to be the cause of it running slowly.

---

