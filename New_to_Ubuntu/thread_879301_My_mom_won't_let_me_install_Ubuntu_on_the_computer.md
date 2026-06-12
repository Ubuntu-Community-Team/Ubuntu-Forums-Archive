---
title: "My mom won't let me install Ubuntu on the computer..."
date: 2008-08-03
forum: New to Ubuntu
---

### Post by I am &gt;= Wes on 2008-08-03
I don't know if this is really where I should be posting this, but it's too late now.  This is my first post so feel free to straighten me out.  Here's the deal:

Earlier this week I ran an Ubuntu live CD, it was my first time ever trying it.  Sadly, I've found that Linux is more addicting than heroin, and it's been tough forcing myself to use Windows.  You see, I can't use Ubuntu on this computer because it is not mine, it is my mother's.  She refuses to allow me to install Ubuntu because she is paranoid and thinks that I will destroy her computer, though all she does is look up recipes occasionally and play spider solitaire.  I have no computer of my own and I lack the funds to purchase one.

Fortunately I have been told that I could probably put Ubuntu on an external hard drive and run it off of that with no change to my mother's beloved computer.  I see no reason why I shouldn't give it a try but just to be safe I'd like some opinions.  

First and foremost, is this a good idea and can any one see how this might not work?

Secondly, if I were to follow through with this plan does any one have any suggestions for external hard drives that would be ideal for this task?

Any help is greatly appreciated,
--Wes

---

### Post by NullHead on 2008-08-03
I'd install [virtualbox](http://www.virtualbox.org/) onto her computer and run Ubuntu inside windows :twisted:

---

### Post by tamoneya on 2008-08-03
1.  this is definitely doable but it will still require modifications of your mothers computer.  It requires that you install a boot loader.  Typically this is GRUB.  Basically the way this works is that when you start the computer it asks you which OS you want to load.
2.  How much space do you want? how much money do you plan on spending on the external drive?

---

### Post by robotman5 on 2008-08-03
Good idea Nullhead! or you could bug your mom for a PC!:lolflag:

---

### Post by collinp on 2008-08-03
Well, yes you can install Ubuntu onto a external hard drive as long as the computer can boot from the port that the external hard drive uses. And, if you want to put any major amount of files onto the hard drive, I would recommend a 250GB or better hard drive.

---

### Post by Joeb454 on 2008-08-03
Well most importantly, don't install it without permission!!

And second, get her to try out the Live CD :) If she likes it, then you'll probably be able to install it

---

### Post by spiderbatdad on 2008-08-03
Tell your mom everyone is going to pick on you if you don't get Ubuntu.

Check out UNetbootin:[http://en.wikipedia.org/wiki/UNetbootin](http://en.wikipedia.org/wiki/UNetbootin)

Or these dual boot guides:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by I am &gt;= Wes on 2008-08-03
> **NullHead said:**
> I'd install [virtualbox](http://www.virtualbox.org/) onto her computer and run Ubuntu inside windows :twisted:

If I do this won't I have to set partitions and what not on the hard drive of the computer itself if I want to save anything, thereby disobeying my mother?

---

### Post by collinp on 2008-08-03
> **tamoneya said:**
> 1.  this is definitely doable but it will still require modifications of your mothers computer.  It requires that you install a boot loader.  Typically this is GRUB.  Basically the way this works is that when you start the computer it asks you which OS you want to load.

Not exactly, you install GRUB onto the MBR of the external hard drive, and when the computer tries to boot from that hard drive it will read the MBR of the external hard drive.

---

### Post by OutOfReach on 2008-08-03
Well any external hard drive that is 5GB+ should be fine. If I am correct if you install Ubuntu to an external hard drive, GRUB will still be installed on the MBR (right? wrong?). Or of course you can install Ubuntu in VirtualBox as mentioned above.

---

### Post by collinp on 2008-08-03
> **OutOfReach said:**
> Well any external hard drive that is 5GB+ should be fine. If I am correct if you install Ubuntu to an external hard drive, GRUB will still be installed on the MBR (right? wrong?). Or of course you can install Ubuntu in VirtualBox as mentioned above.

As i said above, i believe that Ubuntu will install GRUB onto the MBR of the external hard drive and leave the internal hard drives alot. Again, that is what i believe, i could be wrong.

---

### Post by I am &gt;= Wes on 2008-08-03
> **tamoneya said:**
> 1.  this is definitely doable but it will still require modifications of your mothers computer.  It requires that you install a boot loader.  Typically this is GRUB.  Basically the way this works is that when you start the computer it asks you which OS you want to load.
2.  How much space do you want? how much money do you plan on spending on the external drive?

The boot loader shouldn't be a problem

As for the hard drive, I don't want to have to spend more than 200 but I gladly will if what I'm getting is quality. As far as specs I'd like 7200 rpm and 250 - 500 gigs, any more I think would be redundant.

---

### Post by collinp on 2008-08-03
> **I am >= Wes said:**
> The boot loader shouldn't be a problem

As for the hard drive, I don't want to have to spend more than 200 but I gladly will if what I'm getting is quality. As far as specs I'd like 7200 rpm and 250 - 500 gigs, any more I think would be redundant.

This hard drive should suite your needs, and its from a very reliable company: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136175](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136175)

Another option would be just buying a computer entirely your own. You said that you gladly will spend over $200 for a hard drive, Everex makes a computer that will run Ubuntu well (it in fact runs a ubuntu derivate) for $190 here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883118005](http://www.newegg.com/Product/Product.aspx?Item=N82E16883118005). The only problem with that is that is comes with no monitor, but old CTR monitors are everywhere and that same site sells LCD monitors.

---

### Post by OutOfReach on 2008-08-03
> **I am >= Wes said:**
> If I do this won't I have to set partitions and what not on the hard drive of the computer itself if I want to save anything, thereby disobeying my mother?

Actually, no. It creates a virtual hard drive, the virtual hard drive appears as a mere file.

---

### Post by kansasnoob on 2008-08-03
> **Joeb454 said:**
> Well most importantly, don't install it without permission!!

And second, get her to try out the Live CD :) If she likes it, then you'll probably be able to install it

+1 on that!

Look, anything you do means messing with someone else's property!

Don't look for a sneaky way to do it, just get permission!

---

### Post by I am &gt;= Wes on 2008-08-03
> **kansasnoob said:**
> +1 on that!

Look, anything you do means messing with someone else's property!

Don't look for a sneaky way to do it, just get permission!

I'm not trying to be sneaky, I've already asked her.  She says flat out that as long as the hard drive on her computer is being messed with (partitions and what not) she doesn't want me to install Ubuntu.  VirtualBox sounds like it could be a good solution, but the idea of having an external hard drive that I can put all my stuff on and not worry about cluttering my mom's computer with sounds very appealing.

---

### Post by NullHead on 2008-08-03
> **I am >= Wes said:**
> If I do this won't I have to set partitions and what not on the hard drive of the computer itself if I want to save anything, thereby disobeying my mother?

Virtualbox simply creates a file that it can use as its "virtual hard drive/partition/what ever you wana call it". All you'll have to do is make sure you have about 2-5 gb of free space on the computer, make sure it's ok to install a single program, virtualbox, and then run the disk right from virtualbox and install Ubuntu from the live CD right onto the virtual hard drive. 

It sounds complicated, but once you download virtualbox and get familiar with its settings and preferences, you'll get Ubuntu up and running inside windows as a virtual computer! Really simple! 

:popcorn:

---

### Post by kansasnoob on 2008-08-03
> **Hellow said:**
> As i said above, i believe that Ubuntu will install GRUB onto the MBR of the external hard drive and leave the internal hard drives alot. Again, that is what i believe, i could be wrong.

You are WRONG!

If you install Ubuntu to an external drive with the internal drive still connected stage 1 of GRUB will be on the wrong drive and the puter will NOT boot unless the external drive is plugged in.

If it ain't yours don't mess with it! Or get permission!

---

### Post by jflaker on 2008-08-03
IF you get to install it, remember you will need to migrate any files on that system....I made the mistake once and always store the files offline for later use.

---

### Post by Joeb454 on 2008-08-03
Just thought of something.

What about wubi?

---

### Post by kansasnoob on 2008-08-03
> **I am >= Wes said:**
> I'm not trying to be sneaky, I've already asked her.  She says flat out that as long as the hard drive on her computer is being messed with (partitions and what not) she doesn't want me to install Ubuntu.  VirtualBox sounds like it could be a good solution, but the idea of having an external hard drive that I can put all my stuff on and not worry about cluttering my mom's computer with sounds very appealing.

Where do you think Virtual box lives? In outer space? You're still installing something within a machine you don't own!

---

### Post by collinp on 2008-08-03
> **I am >= Wes said:**
> I'm not trying to be sneaky, I've already asked her.  She says flat out that as long as the hard drive on her computer is being messed with (partitions and what not) she doesn't want me to install Ubuntu.  VirtualBox sounds like it could be a good solution, but the idea of having an external hard drive that I can put all my stuff on and not worry about cluttering my mom's computer with sounds very appealing.

As i said above, Everex sells computers for $190, the one that i linked to runs a derivate of Ubuntu called gOS2 and you could run standard Ubuntu on it easily. It does not come with a monitor, but older CTR monitors can be found anywhere and the same site that i linked to sells LCD monitors. The computer is here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16883118005](http://www.newegg.com/Product/Product.aspx?Item=N82E16883118005)

---

### Post by oldsoundguy on 2008-08-03
I haven't seen anyone side with Mom.  It is HER computer (maybe she uses it for business)  It is HER house.  And it is HER rules.

Granted, she is frightened of Linux .. MANY ARE.  They believe the propaganda from Redmond that it is the product of the devil and will rot their minds, destroy their computer, turn their kids into zombies and in general is just bad news.

The youngster needs to realize who is boss. NO usually means NO.  Not trying to circumvent her wishes and do a sneaky install.

IF an Ubuntu computer is wanted .. build one!  Parts suitable are available at all kinds of resale shops (this will not be a "melt your eyes" gaming machine, but a practical learning machine.)

no funds?

Repeat after me: "Do you want fries with that?"

---

### Post by OutOfReach on 2008-08-03
> **Joeb454 said:**
> Just thought of something.

What about wubi?

I completely forgot about Wubi! Yes Wubi would probably be the easiest.

---

### Post by collinp on 2008-08-03
> **oldsoundguy said:**
> I haven't seen anyone side with Mom.  It is HER computer (maybe she uses it for business)  It is HER house.  And it is HER rules.

Granted, she is frightened of Linux .. MANY ARE.  They believe the propaganda from Redmond that it is the product of the devil and will rot their minds, destroy their computer, turn their kids into zombies and in general is just bad news.

The youngster needs to realize who is boss. NO usually means NO.  Not trying to circumvent her wishes and do a sneaky install.

IF an Ubuntu computer is wanted .. build one!  Parts suitable are available at all kinds of resale shops (this will not be a "melt your eyes" gaming machine, but a practical learning machine.)

no funds?

Repeat after me: "Do you want fries with that?"

She said dont install it on her computer, never said cant install it on a external hard drive or on a totally different computer :KS.

---

### Post by noobuntu35 on 2008-08-03
> **I am >= Wes said:**
> I don't know if this is really where I should be posting this, but it's too late now.  This is my first post so feel free to straighten me out.  Here's the deal:

Earlier this week I ran an Ubuntu live CD, it was my first time ever trying it.  Sadly, I've found that Linux is more addicting than heroin, and it's been tough forcing myself to use Windows.  You see, I can't use Ubuntu on this computer because it is not mine, it is my mother's.  She refuses to allow me to install Ubuntu because she is paranoid and thinks that I will destroy her computer, though all she does is look up recipes occasionally and play spider solitaire.  I have no computer of my own and I lack the funds to purchase one.

Fortunately I have been told that I could probably put Ubuntu on an external hard drive and run it off of that with no change to my mother's beloved computer.  I see no reason why I shouldn't give it a try but just to be safe I'd like some opinions.  

First and foremost, is this a good idea and can any one see how this might not work?

Secondly, if I were to follow through with this plan does any one have any suggestions for external hard drives that would be ideal for this task?

Any help is greatly appreciated,
--Wes

Try using Wubi you can find it and Other really cool Ubuntu stuff at getdeb.net or [click here]("http://www.getdeb.net") it runs from within Windows Actually installs/uninstalls from windows, Save the file where you'll know it is. this helps embarrassing things like like oops where'd the Windows Partition go???

---

### Post by collinp on 2008-08-03
> **noobuntu35 said:**
> Try using Wubi you can find it and Other really cool Ubuntu stuff at getdeb.net or [click here]("http://www.getdeb.net") it runs from within Windows Actually installs/uninstalls from windows, Save the file where you'll know it is. this helps embarrassing things like like oops where'd the Windows Partition go???

Wubi is on the LiveCD...

---

### Post by kansasnoob on 2008-08-03
> **Joeb454 said:**
> Just thought of something.

What about wubi?

How bad would you crap if you found a new app in your win program list?

Ask permission, explain what you want to do!

I've had kids and kids boyfriends / girlfriends totally mess up my machines. It's not pleasant.

Ask for permission!

---

### Post by collinp on 2008-08-03
> **kansasnoob said:**
> How bad would you crap if you found a new app in your win program list?

Ask permission, explain what you want to do!

I've had kids and kids boyfriends / girlfriends totally mess up my machines. It's not pleasant.

Ask for permission!

I dont use windows so I guess i dont count :guitar:.

---

### Post by I am &gt;= Wes on 2008-08-03
First off, my mom just doesn't want Ubuntu installed completely on the computer for whatever reason.  I'm not doing this without letting her know exactly what I'm doing.

I don't think she has a problem with what I'm proposing.

I do have money and a job, how else would I be able to afford a 200 dollar external hard drive?  I don't want to spend much more because I'm going to be going to college soon and I'll probably have to buy my own computer. (and I'm looking at system76)

The Everex isn't a bad idea but 1.5ghz and 512mb ram doesn't appeal to me.

Please explain to me what wubi is.

---

### Post by noobuntu35 on 2008-08-03
> **oldsoundguy said:**
> I haven't seen anyone side with Mom.  It is HER computer (maybe she uses it for business)  It is HER house.  And it is HER rules.

Granted, she is frightened of Linux .. MANY ARE.  They believe the propaganda from Redmond that it is the product of the devil and will rot their minds, destroy their computer, turn their kids into zombies and in general is just bad news.

The youngster needs to realize who is boss. NO usually means NO.  Not trying to circumvent her wishes and do a sneaky install.

IF an Ubuntu computer is wanted .. build one!  Parts suitable are available at all kinds of resale shops (this will not be a "melt your eyes" gaming machine, but a practical learning machine.)

no funds?

Repeat after me: "Do you want fries with that?"

OLDSOUNDGUY is right. I'm siding with the MOM. I hosed my own HDD because of a botched dual boot. find an old system Linux will run on an old 386 if you have too, Networking might be an issue... 
Building a computer from scratch is not hard but replacing data that has accidentally been erased is. Don't mess with Moms computer. Show her Wubi and let her decide I've Posted a link further down

---

### Post by CatKiller on 2008-08-03
> **I am >= Wes said:**
> Please explain to me what wubi is.

[WUBI on Wikipedia]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu)").

---

### Post by collinp on 2008-08-03
> **I am >= Wes said:**
> First off, my mom just doesn't want Ubuntu installed completely on the computer for whatever reason.  I'm not doing this without letting her know exactly what I'm doing.

I don't think she has a problem with what I'm proposing.

I do have money and a job, how else would I be able to afford a 200 dollar external hard drive?  I don't want to spend much more because I'm going to be going to college soon and I'll probably have to buy my own computer. (and I'm looking at system76)

The Everex isn't a bad idea but 1.5ghz and 512mb ram doesn't appeal to me.

Please explain to me what wubi is.

The Everex is in fact better than the machine i have right now, a 1.1GHz Intel Celeron with 512MBs ram and a 18GB hard drive, this computer runs Ubuntu fast. The ram in that Everex is expandable to 2GBs, you can add a PCI graphics card to it too.

---

### Post by kk0sse54 on 2008-08-03
Install VMware on her computer and then download the vm image of Ubuntu so that you can run Ubuntu inside of Windows so it just becomes another open application in Windows. I would recommend it more than virtual box because it's so devilishly simple in which it requires  no configuration and it will not change your mother's computer at all ( virtual box won't make any changes either since both are just running a virtual machine within Windows yet for simple things like this the simpler the better for me)

---

### Post by NullHead on 2008-08-03
I tested wubi before .. all it does is install ubuntu on a new partition wile running windows ... it also activates windows boot loader, which btw is a pain in the ****. 

Perhaps it was simply my personal experience, but I found it to be a terrible pain.

---

### Post by Sef on 2008-08-03
> First off, my mom just doesn't want Ubuntu installed completely on the computer for whatever reason. I'm not doing this without letting her know exactly what I'm doing.

I don't think she has a problem with what I'm proposing.

I do have money and a job, how else would I be able to afford a 200 dollar external hard drive? I don't want to spend much more because I'm going to be going to college soon and I'll probably have to buy my own computer. (and I'm looking at system76)

The Everex isn't a bad idea but 1.5ghz and 512mb ram doesn't appeal to me.


How about buying a used computer?  You could always upgrade the ram.

---

### Post by collinp on 2008-08-03
> **Sef said:**
> How about buying a used computer?

I was about to say that, they sell some old gaming computers that can still do alot by todays standards on ebay for $200 or $300.

---

### Post by I am &gt;= Wes on 2008-08-03
The problem with buying my own computer is that when college rolls around in a year I'll be stuck with whatever I buy now because my parents won't want me buying a new one and I would really prefer a really nice computer that will last through college.

---

### Post by Methuselah on 2008-08-03
If you are allowed to use that computer and install windows programs then the most feasible solution would be to download and install vmware server and install ubuntu in that.

You could explain to your mother that this is just like any other program installation (microsoft word etc). Anything else that she's unfamiliar with will probably make her uneasy (disk paritioning, wubi etc).

You won't be able to do compiz etc. in vmware.

---

### Post by bpowell2005 on 2008-08-03
> **I am >= Wes said:**
> The problem with buying my own computer is that when college rolls around in a year I'll be stuck with whatever I buy now because my parents won't want me buying a new one and I would really prefer a really nice computer that will last through college.

Good luck with that! My computer was woefully out of date by my fourth Freshman year!

---

### Post by Trav1s on 2008-08-03
I think the everex machine or any old computer with a processor over 1 ghz would fit the bill.  I am running Hardy on an old Toshiba Satellite 1005 laptop... 
- 1.033 celery processor
- 512 megs of ram (8 megs shared video)
- CD-burner
- original 20 gig 4200 rpm drive

Works great to mess around with Linux... Awesome web surfing, does well with OpenOffice and will likely become a file server.  Consider the Everex system.... unless you can find a free older box.

---

### Post by Jforce93 on 2010-05-13
get a PC from your public school, they usually have some old ones laying around that they might be able to give you :)

---

### Post by mkvnmtr on 2010-05-13
The computer I am on right now I paid $25 for. It runs Ubuntu great. Any other Linux distro also. Even when I was 12 years old and delivering circulars door to door I could afford that kind of money. A computer that runs linux does not have to cost much .No need to upset mom.

---

### Post by CharlesA on 2010-05-13
Cripes, thread is old - from 2008. Did it really need to be ressed?

---

### Post by cariboo on 2010-05-13
This thread didn't need to be reopened. Closed

---

