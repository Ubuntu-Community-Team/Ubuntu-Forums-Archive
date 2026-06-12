---
title: "Compiz error"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by naikmanoj1991 on 2011-09-22
:icon_frown::icon_frown::icon_frown::icon_frown: Overcome the  error after making changes in Compiz Config Manager....and also in Update Manager...
.
.
.
I m using  Ubuntu 11.10.:):)

---

### Post by howefield on 2011-09-22
Moved to the development forum " Ubuntu +1 (Oneiric Ocelot)".

You might want to include some more information, like the error you have.

---

### Post by naikmanoj1991 on 2011-09-22
Error Shows that..
..............................................................................................................................................................
Application Error
Sorry, CompizConfigSetting Manager closed unexpectedly
.............................................................................................................................................................
i was already report this error but cant solved issue..

when  i make changes in compiz...my unity pannel and main menu bar which is shows time,battery status etc...automatically closed...it cant open after restarting the sysytem............:confused::confused:

so last optn  remaining is reset the unity:(:(:(..............after reseting the unity it comes to the default..

---

### Post by dino99 on 2011-09-22
rough way: purge then reinstall it via synaptic (should say: all related installed compiz pckages)

---

### Post by naikmanoj1991 on 2011-09-22
k...but i also got the same error in Ubuntu Software Center

---

### Post by naikmanoj1991 on 2011-09-22
i think i got error in every application today i was install bluefish editor..when i was closed the bluefish editor same error occur....](*,)](*,)](*,)

---

### Post by dino99 on 2011-09-22
are you using third party repos ?

---

### Post by naikmanoj1991 on 2011-09-22
what u say?
i was download the Ubuntu 11.10 from the official website of the Ubuntu

---

### Post by mörgæs on 2011-09-22
Posting a good question is not easy, and it might take time to learn. Here is some advice:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by naikmanoj1991 on 2011-09-22
> **mörgæs said:**
> Posting a good question is not easy, and it might take time to learn. Here is some advice:

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

**What are you thinking? I'm not kidding here?**:(:(:(

---

### Post by dino99 on 2011-09-22
What do you really expect with such title: "Compiz error"

have you followed post #4 ?

---

### Post by P-I H on 2011-09-22
Compiz crashes always in my installation when I open settings for the Unity plugin. The changes I make are anyhow performed, so there isn't a big problem. There is a bug report on this, bug #832458.

---

### Post by mörgæs on 2011-09-22
> **dino99 said:**
> What do you really expect with such title: "Compiz error"

have you followed post #4 ?

I changed the title, hoping it was a little more specific than the original 'Error!!!!'.

---

### Post by dino99 on 2011-09-22
> **mörgæs said:**
> I changed the title, hoping it was a little more specific than the original 'Error!!!!'.

Well done :)
the point is we see some noobs testing a dev release without trying/following solutions

---

### Post by mc4man on 2011-09-22
> **naikmanoj1991 said:**
> 

when  i make changes in compiz...my unity pannel and main menu bar which is shows time,battery status etc...automatically closed...it cant open after restarting the sysytem

so last optn  remaining is reset the unity:(:(:(..............after reseting the unity it comes to the default..

Whenever you are in ccsm, before exiting make sure the unity plugin is still enabled, it can easily become disabled
If you happen exit without checking and lose the launcher & panel, then don't reset unity, just open ccsm again & enable unity
(in that case just browse to /usr/share/applications & d. click on the compizconfig... icon if no other way to open is available.

---

### Post by bikewrecker on 2011-09-22
> **mc4man said:**
> Whenever you are in ccsm, before exiting make sure the unity plugin is still enabled, it can easily become disabled
If you happen exit without checking and lose the launcher & panel, then don't reset unity, just open ccsm again & enable unity
(in that case just browse to /usr/share/applications & d. click on the compizconfig... icon if no other way to open is available.
I think I've been having the same problems as the thread creator. About every time when I try to change things in the compiz settings manager It randomly pops up error messages saying that compiz has closed unexpectedly; however, usually nothing has gone noticeably wrong so I continue doing whatever I'm doing. 
Every once in a while the whole thing crashes and I cant do ANYTHING, even ctrl-alt-t wont open the terminal. The bar on the top of my desktop is missing and i cant get my unity sidebar to open even by holding the super key. My only option is to ctrl-alt-F6, login and reset unity, then restart. 
I'm a ubuntu noob so i shouldnt have gotten 11.10 yet because I cant fix anything, but compiz has some serious problems on my computer. Now that I've had to reset unity twice some of the compiz settings that were working before don't work anymore, (ie. emerald --replace in the window decoration command line.) 
Hopefully this extra information helps the ppl who actually know what theyre doing help us ubuntu noobs out.

Thanks in advance!

---

### Post by ventrical on 2011-09-22
> **bikewrecker said:**
> I think I've been having the same problems as the thread creator. About every time when I try to change things in the compiz settings manager It randomly pops up error messages saying that compiz has closed unexpectedly; however, usually nothing has gone noticeably wrong so I continue doing whatever I'm doing. 
Every once in a while the whole thing crashes and I cant do ANYTHING, even ctrl-alt-t wont open the terminal. The bar on the top of my desktop is missing and i cant get my unity sidebar to open even by holding the super key. My only option is to ctrl-alt-F6, login and reset unity, then restart. 
I'm a ubuntu noob so i shouldnt have gotten 11.10 yet because I cant fix anything, but compiz has some serious problems on my computer. Now that I've had to reset unity twice some of the compiz settings that were working before don't work anymore, (ie. emerald --replace in the window decoration command line.) 
Hopefully this extra information helps the ppl who actually know what theyre doing help us ubuntu noobs out.

Thanks in advance!


You have to wait and be patient. The error message is a false positive for beta1. Compiz is resetting every time you change a setting. after you change a setting it is always good to log-out and then log back on. Wait , wait , wait !!!! It seems like a system hang with compiz error but it is not in 90% of cases.

---

### Post by bikewrecker on 2011-09-22
> **ventrical said:**
> You have to wait and be patient. The error message is a false positive for beta1. Compiz is resetting every time you change a setting. after you change a setting it is always good to log-out and then log back on. Wait , wait , wait !!!! It seems like a system hang with compiz error but it is not in 90% of cases.
ooook. that makes sense. I knew I was over my head getting into 11.10 too early. Thats the answer to the thread posters question. The error is just telling you that compiz is reseting. Their's nothing really wrong. 

I got emerald working again. I had just forgotten to type 'emerald --reset' in the alt-f2 command line as well as the compiz line. That fixed everything wrong with emerald not working. 

The first time compiz messed up on me, I restarted my computer and it brought up nothing but the desktop. The Unity interface (which I'd like to replace) was gone and none of my key commmands worked. So I had to reset unity. Ive got it pretty much how I want it now, so I'll try not to mess with compiz as long as I can put it off. When I do use it again ill take your suggestions.

Thank you so much for the help!

---

