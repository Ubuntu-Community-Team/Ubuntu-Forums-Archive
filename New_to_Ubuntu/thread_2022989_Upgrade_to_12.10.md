---
title: "Upgrade to 12.10"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by Febri Ichsan on 2012-07-11
What's the big difference in xx.04 vs xx.10 ubuntu version like 12.04 vs 12.10?
is it highly recommended to upgrade?
is 'sudo apt-get upgrade' will upgrade my 12.04 to 12.10?

---

### Post by Sendo Eevpix on 2012-07-11
Not much difference.

At most Basic as I can say without any confusion is. If you are using something like Ubuntu 12.04 which is an LTS(Long term support) then you can continue using Ubuntu 12.04 until the next LTS Comes out, and not have to worry about the constant switch and updates EVERY six months. Where non LTS like 12.10, which is just a version to use for six months, then switch to the next, to stay up-to-date, and secure.

So, for time saving, and convienence, stick with Ubuntu 12.04 and LTS series. ;)

---

### Post by epikvision on 2012-07-11
> What's the big difference in xx.04 vs xx.10 ubuntu version like 12.04 vs 12.10?
Ubuntu versions always go by xx.04 and xx.10.  Every six months, Ubuntu has a new release.  Currently, this 6 month cycle is at 12.04, so in October, there will be 12.10.  Next year, by March (i think), the next release would be 13.04, and so on.  

The big difference with the upcoming versions is that they add more features than the previous one.  For instance, at 11.04, Ubuntu had Unity for the first time.  By 12.04, we have a more refined Unity as well as the new alt feature.  

> is it highly recommended to upgrade?
Don't upgrade just yet.  Quantal (12.10) is currently in development release, meaning it isn't as stable as Precise (12.04).   If you want to try it, install VirtualBox from the Ubuntu Software Center, download the appropriate Quantal, and run it on VirtualBox.

---

### Post by Febri Ichsan on 2012-07-11
@Sendo Eevpix : Gee, what a username, lol.
So, it means that there will be no big difference between 12.04 and 12.10 as long as I keep updating my 12.04?

---

### Post by QIII on 2012-07-11
It may sound confusing, but no, that will not upgrade you to the next version of Ubuntu.

```
sudo apt-get update
```

followed by 

```
sudo apt-get upgrade
```

updates you sources and then upgrades any packages you have on your current version.

```
sudo apt-get update
```

by itself does not update your software.

You do NOT want to upgrade to 12.10 because it is still in testing and isn't even a Beta yet.  It is not that it is just unstable -- it is completely unsuitable for daily use unless you want a lot of headaches.

12.10 is not due for release until October.

---

### Post by Febri Ichsan on 2012-07-11
whoa, what a friend I have here!!
thanks guys, for your helps.
anyway, just wondering, why should I choose ubuntu instead of windows' OS?
(not to mention the pricey and piracy thingy).
coz I don't find any reason to love ubuntu as much as u do just yet.

many thanks.
lol...

---

### Post by jmfal on 2012-07-11
Welcome to Ubuntu

"sudo spt-get upgrade"  just upgrades the app/packages in your repositories.

12.10 is a beta  and will be released  in12.10.

I would wait till you are comfortable using 12.04  before jumping into an unstable version.

---

### Post by Febri Ichsan on 2012-07-11
@QIII : there u are (again)!!!
so if i sudo apt-get upgrade, it's just upgrading my software package not my Precise?

---

### Post by QIII on 2012-07-11
It is upgrading your software and any updates to Precise.  It won't upgrade you to 12.10 Quantal.

---

### Post by QIII on 2012-07-11
> **Febri Ichsan said:**
> whoa, what a friend I have here!!
thanks guys, for your helps.
anyway, just wondering, why should I choose ubuntu instead of windows' OS?
(not to mention the pricey and piracy thingy).
coz I don't find any reason to love ubuntu as much as u do just yet.

many thanks.
lol...

You should choose what works best for you and what makes you comfortable.  Use Windows if that is what is most beneficial and just work with Ubuntu to get familiar with it and decide to use it or not.

You may get emotional and zealous answers to that question, but the fact is that there is no reason to choose one over the other beyond the question of what works best and suits your needs.

---

### Post by Febri Ichsan on 2012-07-11
@QIII : will there be no problem if I sudo apt-get upgrade??

---

### Post by Febri Ichsan on 2012-07-11
> **QIII said:**
> You should choose what works best for you and what makes you comfortable.  Use Windows if that is what is most beneficial and just work with Ubuntu to get familiar with it and decide to use it or not.

You may get emotional and zealous answers to that question, but the fact is that there is no reason to choose one over the other beyond the question of what works best and suits your needs.

Yeah, I guess so, but I think I will try my best for my Ubuntu experience, for the sake of myself, lol. well, a least until I get rid my 'beans'.

---

### Post by jmfal on 2012-07-11
You can run the first two commands that QIII gave you and you will be good to go

---

### Post by Sendo Eevpix on 2012-07-11
> **Febri Ichsan said:**
> @Sendo Eevpix : Gee, what a username, lol.
So, it means that there will be no big difference between 12.04 and 12.10 as long as I keep updating my 12.04?

What do you mean by that? I use this name for most the sites I am member of.

Well Yes there will. As I tried to Say. The LTS is for people who doesn't like the six month cycle of Ubuntu Changes. While the difference is mostly in function and appearances. That is simple as I understand and can tell. Well I hope you aren't going to Ubuntu 12.10 right 'now' because it is right now really new in development, so there will be A LOT of bugs in it. I can only suggest you avoiding to bother, unless you are good with computers like Ubuntu, find some bugs, try and fix them, then send the bug report to Ubuntu, along with what ever information of how you fixed the bug on your computer.

---

### Post by DogMatix on 2012-07-11
> **jmfal said:**
> Welcome to Ubuntu

"sudo spt-get upgrade"  just upgrades the app/packages in your repositories.

12.10 is a beta  and will be released  in12.10.

I would wait till you are comfortable using 12.04  before jumping into an unstable version.

```
 sudo _a_pt-get upgrade
```

;)

sorry for being picky, its a good habit.

---

### Post by jmfal on 2012-07-11
Sorry for the typo.

---

### Post by QIII on 2012-07-11
Thanks, DogMatix!

That's what I get for using my cell phone when I'm on the forums.  I'll edit that.

Edit:  Heck, I thought he was talking about me.  Dang.  Thought I had actually made a mistake for the first time in my life.

---

### Post by Ubun2to on 2012-07-11
> **Febri Ichsan said:**
> anyway, just wondering, why should I choose ubuntu instead of windows' OS?
(not to mention the pricey and piracy thingy).

Well, here is my standpoint on why Windows is inferior to Ubuntu:
[call to Microsoft about key not working when I reinstalled Windows due to it not being worth trying to fix without doing this]
Me: Hello, I have a Windows 7 Professional key not activating.
MS Dude (speaking in impossible to understand Indian accent): Did you use a manufacturers disk or an OEM licence?
Me: OEM licence because there was no recovery disk included, and they include a recovery disk maker, but it also loads your system up with bloatware when you use it, and it got corrupted.
MS: Manufacturers buy tons of SLP licences-meaning they are for one use only. Fujitsu has to send you a new disks.
Me: Well, I did the OEM disk because they haven't sent me the disks and it's been over 3 weeks since I've ordered them.
MS: Sorry, we can't help you there. You can call Fujitsu at 888-FUJITSU
[end call with MS]
[call to Fujitsu]
Me: I need help activating a licence that I had to install since you never sent recovery CDs. MS directed me here.
Fujitsu Dude: Did you use the recovery partition?
Me: I don't use that stuff since you load it up with bloatware that advertisers pay you to include and it also gets corrupted really fast in my experience. I ordered recovery disks over 3 weeks ago, and they haven't arrived.
FJ: Let me check the status of your order.
[puts me on hold for half an hour-no kidding]
FJ: Your disks are on backorder right now. However, I can send you a new hard drive that will arrive in 2 days with which you can reinstall the OS.
Me: Do I have to pay for it like I did the recovery disks?
FJ: No.
Me: Send it over.
FJ: Ok. But, I must have your address, shipping address, work address, the S/N, P/N, warranty status, activation key, and credit card number.
[end call to FJ]
This is the most annoying thing I deal with-dumb activation keys. Why does MS require a key for OEM disks, anyway? There is a reason they give these things to technicians-so we don't have to constantly buy ridiculously overpriced keys every time we have to upgrade OSs, wipe hard drives or install new ones.
They don't seem to understand that their crappy key system is also a reason piracy is such a problem.

---

### Post by QIII on 2012-07-11
Did you read the OEM license?

Sounds like your issue is with the OEM, not Microsoft.

If you chose not to create a recovery disk, that was your call.

The key process is not what causes piracy.  It is a response to piracy.  Piracy is caused by dishonest people who want what they are not willing to rightfully pay for.

That said, do you have anything helpful for the OP?

---

### Post by madjr on 2012-07-11
you may want to read more about ubuntu / linux:

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by Sendo Eevpix on 2012-07-11
> **Ubun2to said:**
> Well, here is my standpoint on why Windows is inferior to Ubuntu:
[call to Microsoft about key not working when I reinstalled Windows due to it not being worth trying to fix without doing this]
Me: Hello, I have a Windows 7 Professional key not activating.
MS Dude (speaking in impossible to understand Indian accent): Did you use a manufacturers disk or an OEM licence?
Me: OEM licence because there was no recovery disk included, and they include a recovery disk maker, but it also loads your system up with bloatware when you use it, and it got corrupted.
MS: Manufacturers buy tons of SLP licences-meaning they are for one use only. Fujitsu has to send you a new disks.
Me: Well, I did the OEM disk because they haven't sent me the disks and it's been over 3 weeks since I've ordered them.
MS: Sorry, we can't help you there. You can call Fujitsu at 888-FUJITSU
[end call with MS]
[call to Fujitsu]
Me: I need help activating a licence that I had to install since you never sent recovery CDs. MS directed me here.
Fujitsu Dude: Did you use the recovery partition?
Me: I don't use that stuff since you load it up with bloatware that advertisers pay you to include and it also gets corrupted really fast in my experience. I ordered recovery disks over 3 weeks ago, and they haven't arrived.
FJ: Let me check the status of your order.
[puts me on hold for half an hour-no kidding]
FJ: Your disks are on backorder right now. However, I can send you a new hard drive that will arrive in 2 days with which you can reinstall the OS.
Me: Do I have to pay for it like I did the recovery disks?
FJ: No.
Me: Send it over.
FJ: Ok. But, I must have your address, shipping address, work address, the S/N, P/N, warranty status, activation key, and credit card number.
[end call to FJ]
This is the most annoying thing I deal with-dumb activation keys. Why does MS require a key for OEM disks, anyway? There is a reason they give these things to technicians-so we don't have to constantly buy ridiculously overpriced keys every time we have to upgrade OSs, wipe hard drives or install new ones.
They don't seem to understand that their crappy key system is also a reason piracy is such a problem.


Sorta why I left Microsoft for about four years. They fill the computers up with what peoples pays them to, then if it breaks, they disowns in when you complain for service about it. While having to go through multiple people to get something fixed and done right. I had to go through two guys just recently to set up my mom's XP wifi, then had to call their tech support to come to the house.  :mad:

---

### Post by QIII on 2012-07-11
Whereas with Ubuntu you can have a problem and work with someone on the forum over the course of several days to get something to work -- if you get it to work.

Same story on this side, guys.

If everything in Ubuntu smelled like roses and worked automagically, this forum would be a ghost town.

---

### Post by Sendo Eevpix on 2012-07-11
> **QIII said:**
> Whereas with Ubuntu you can have a problem and work with someone on the forum over the course of several days to get something to work -- if you get it to work.

Same story on this side, guys.

If everything in Ubuntu smelled like roses and worked automagically, this forum would be a ghost town.

Yeah. Know what you mean. I have a huge problem with my Ubuntu, turns out it isn't a software problem, its a hardware problem, because my mom wanted to be cheap. Though two of my friends being die-heart windows fans are constantly say "Oh that problem is because programs like Firefox are meant for Windows, not Ubuntu", which is so far from the truth, it is sorta funny.

Though yes, to be serious I have had more then my fair share of Linux troubles with Linux and several programs, and hard wares.

---

### Post by Kopkins on 2012-07-11
[quote="Febri Ichsan"]
                 [I]anyway, just wondering, why should I choose ubuntu instead of windows' OS?
[/I][/quote]

In regard to Ubuntu vs. Windows, theres a lot that each system has going for it.

Ubuntu:

[LIST]
[*]You are free to do whatever you like with the system. I love tweaking stuff to my own liking. My whole life I've sought to be unique, in fourth grade a developed a disliking for ipods because *everyone* had an ipod mini. Ever since then I've never been able to comfortably use an ipod. That said, ***nobody ***has an Ubuntu system just like mine.
[*]Open source - This means that you don't have to pay for your OS. You can do most things with open source software, whether it be photo editing, 3D rendering, watching DVD's or whatever.
[*]Software center - One of my favorite things about Ubuntu, and GNU/Linux in general, is the software. You have various repositories that you can download and install all sorts of software from. Ubuntu happens to have a decent GUI that lets you search and browse through all the available software with relative ease.
[*]You don't *need *virus protection.
[/LIST]

[LIST]
[*]Different desktop options - you can choose any of the Ubuntu distributions to change the desktop layout to what you prefer.
[*]The community - I have yet to find as good of an online community as I have found with GNU/Linux. Ubuntu's community is among the best.
[/LIST]
Windows: 

[LIST]
[*]You have access to a lot more proprietary software with greater ease. You can run many windows programs under wine in GNU/Linux, but some people would rather not. You have photoshop and all sorts of other similar programs available to you to run without any additional software. Of course these cost money unlike open source programs.
[*]You **have** technical support - You will, without a doubt, hear several people whine and moan about how terrible technical support is. While I personally don't care to try to understand my Indian support operator so I can get windows working, I have found that they are generally pretty knowledgeable. This is not something you have in Ubuntu; Instead, we have forums and the community.
[*]It's familiar - for most people, MS Windows is something they have been around all their life. They know how to navigate and do many things with relative ease. Switching OSs forces them to relearn many things.
[/LIST]
Remember, It's like QIII said, it's all about what suits your needs. If you don't have any reasons for switching OSs then you probably shouldn't. Also, I just listed a few things, and it's not like both systems don't have problems. They both have many problems, they just happen to be in different areas of the system. 

Kopkins

---

### Post by Sendo Eevpix on 2012-07-11
> **Kopkins said:**
> In regard to Ubuntu vs. Windows, theres a lot that each system has going for it.

Ubuntu:

[LIST]
[*]You are free to do whatever you like with the system. I love tweaking stuff to my own liking. My whole life I've sought to be unique, in fourth grade a developed a disliking for ipods because *everyone* had an ipod mini. Ever since then I've never been able to comfortably use an ipod. That said, ***nobody ***has an Ubuntu system just like mine.
[*]Open source - This means that you don't have to pay for your OS. You can do most things with open source software, whether it be photo editing, 3D rendering, watching DVD's or whatever.
[*]Software center - One of my favorite things about Ubuntu, and GNU/Linux in general, is the software. You have various repositories that you can download and install all sorts of software from. Ubuntu happens to have a decent GUI that lets you search and browse through all the available software with relative ease.
[*]You don't *need *virus protection.
[/LIST]

[LIST]
[*]Different desktop options - you can choose any of the Ubuntu distributions to change the desktop layout to what you prefer.
[*]The community - I have yet to find as good of an online community as I have found with GNU/Linux. Ubuntu's community is among the best.
[/LIST]
Windows: 

[LIST]
[*]You have access to a lot more proprietary software with greater ease. You can run many windows programs under wine in GNU/Linux, but some people would rather not. You have photoshop and all sorts of other similar programs available to you to run without any additional software. Of course these cost money unlike open source programs.
[*]You **have** technical support - You will, without a doubt, hear several people whine and moan about how terrible technical support is. While I personally don't care to try to understand my Indian support operator so I can get windows working, I have found that they are generally pretty knowledgeable. This is not something you have in Ubuntu; Instead, we have forums and the community.
[*]It's familiar - for most people, MS Windows is something they have been around all their life. They know how to navigate and do many things with relative ease. Switching OSs forces them to relearn many things.
[/LIST]
Remember, It's like QIII said, it's all about what suits your needs. If you don't have any reasons for switching OSs then you probably shouldn't. Also, I just listed a few things, and it's not like both systems don't have problems. They both have many problems, they just happen to be in different areas of the system. 

Kopkins


That is true, but there is a LOT more reasons to Go Ubuntu, though you are a bit off on the different desktop option, because Macs, Windows(7) offers the features now.

---

### Post by Kopkins on 2012-07-12
> **Sendo Eevpix said:**
> That is true, but there is a LOT more reasons to Go Ubuntu, though you are a bit off on the different desktop option, because Macs, Windows(7) offers the features now.

Perhaps different themes/looks, but I doubt there are actually entirely different desktop layouts. In GNU/Linux we have: Gnome, Unity, xfce, ldxe, KDE. All are very different from each other. 

I would be very interested to see what you are talking about. Link?

---

### Post by Ubun2to on 2012-07-13
> **QIII said:**
> Did you read the OEM license?

Sounds like your issue is with the OEM, not Microsoft.

If you chose not to create a recovery disk, that was your call.

The key process is not what causes piracy.  It is a response to piracy.  Piracy is caused by dishonest people who want what they are not willing to rightfully pay for.

That said, do you have anything helpful for the OP?

MS was OK with me doing it in the past. But, recovery disks should've been shipped with the laptop in the first place (or at least they should send disks to maker recovery disks with-CDs are literally a dozen for a dime and their 1.5" hard drives cost over $100). Their crappy key system is so annoying.
But, I do have some advice. Don't jump into Ubuntu expecting a Windows clone. That you will not have.

---

### Post by Febri Ichsan on 2012-07-14
:guitar:

u guys rock!!!
so much sorry for my comparing things, making a debate forum lol.
i get it now.

mom, watch this, ur son is no longer a pirate! lol.

---

### Post by j0n4t on 2012-07-30
I am still new to linux world, but i found an article on the net that helped me understand a little more about Linux in general, comparing it with Windows: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
   It is similar  that Kopkins said in the sense.

OBS: Sorry if my english is not good, not my native language.

---

### Post by Ubun2to on 2012-07-30
> **Febri Ichsan said:**
> mom, watch this, ur son is no longer a pirate! lol.

And you can no longer get sued my Microsoft for everything you own!
Also, try to improve your grammar. I'm not going to be a Grammar Nazi, but I hate it when people butcher the English language.

---

### Post by madjr on 2012-07-30
> **Ubun2to said:**
> And you can no longer get sued my Microsoft for everything you own!
Also, try to improve your grammar. I'm not going to be a Grammar Nazi, but I hate it when people butcher the English language.

well is not only english that gets butchered , basically any language in my experience (like spanish) which gets hammered hard too :p

---

