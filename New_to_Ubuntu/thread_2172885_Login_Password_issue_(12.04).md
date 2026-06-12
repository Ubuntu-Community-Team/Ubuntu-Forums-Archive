---
title: "Login Password issue (12.04)"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by TrademarkofAZ on 2013-09-06
So for some unknown reason, I can no longer login into my account. There was no problem when I disabled the guest account (now I regret it) & after rebooting my laptop because I wanted to update libimobiledevice (which doesn't even work w/my iphone at all by the way). What I have noticed is no matter how slow & cautious I type the correct password, the screen looks like it'll sign me in but then immediately goes back to the login screen. 

Clearly, there's a problem & being a rookie within the Ubuntu community, I want to go back to having fun & discovering all the cool features I was available to. Oh & one more problem; because I couldn't log in Ubuntu, I put developer mode back on & am currently back on Chrome OS again (I have the Acer C7). My other question is do I need to re-install Ubuntu or is it still on my hard drive once I turn off developer mode again?

Thanks!!

---

### Post by newb85 on 2013-09-06
The login issue seems like the behavior of a system with a home directory that was encrypted where someone tried to use instructions similar to those given here [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword).  While a nice tutorial for non-encrypted systems, using that procedure with an encrypted home directory will prevent you from successfully logging in.  If that is what has happened, you need to use the steps in that tutorial to put your password back to what it was before and log in with that.

---

### Post by protoss96 on 2013-09-07
Try to press Ctrl+Alt+F1, then enter your username and password. Then when your log in, type "startx" command.

---

### Post by TrademarkofAZ on 2013-09-07
Just an update:

I went ahead & re-installed Ubuntu yesterday after posting this. At the time, I couldn't think of anything other ideas and I officially hated Chrome OS after having a taste of Ubuntu. I just got started & didn't really have anything on my laptop besides the tweak to make my theme & icons look like Mac OS X. I didn't need to partition the HDD since it I simply just turned off developer mode again. Thanks newb85 & you as well, protoss96 for giving me links & steps I need to do instead of re-installing again.

---

