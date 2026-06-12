---
title: "Compiz in hardy?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by BluePlum on 2008-04-25
So yer i DL hardy and install it. All goes well. I notice my graphic card is now supported in the loading screen and i can flip my screen and do more stuff now. I went to enable effects. But it says effects cannot be enabled... They worked fine with gusty why not hardy? also tried to install CCSM and i get:

assasin@Invisible-Assasin:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
assasin@Invisible-Assasin:~$ 

HELP!

---

### Post by MONODA on 2008-04-25
try:
> sudo apt-cache search compiz settings
and install the most relavant one. I am not running hardy but I assume that the package name is different.

---

### Post by BluePlum on 2008-04-25
assasin@Invisible-Assasin:~$ sudo apt-cache search compiz settings 
assasin@Invisible-Assasin:~$ 

Hmmmmmmm That failed lol.

---

### Post by alejo0823 on 2008-04-25
that package its in the universe make sure you have it enable. in the synaptic go to configuration repositories.

---

### Post by BluePlum on 2008-04-25
Yer installing it now. It said it was enabled but i turned em all of and en and now it's Installing it. Lets all prey it works.

---

### Post by BluePlum on 2008-04-25
T_T. I installed CCSM and went into visual effects try'd to enable advanced. FAIL!
And it did not say custom effects anywere. I pressed alt-f2. Typed CCSM. The CCSM then came up. but no effects are working. It's a little wierd... been 5 minutes and found alot of bugs heh....

---

### Post by alejo0823 on 2008-04-25
ok, I had that problem too, I installed another version of the compiz manager so it conflicted, have you done that?, try to reinstall all the compiz packages at the same time.

---

### Post by BluePlum on 2008-04-25
and how do i do this? ty for reply

---

### Post by alejo0823 on 2008-04-25
In synaptic search "compiz" and right click reinstall the ones are checked, when you are doing this try to find one that haves a different name, I don't remember the name but try looking for it while I search it.

---

### Post by alejo0823 on 2008-04-25
I didn't found the alternate compiz manager that conflicted in my case. if you install the fusion-icon you might be able to change the effects settings to extra.

---

### Post by BluePlum on 2008-04-25
doing what you said :D well see if it works in 5 minutes thx. And u earned a thx :D

---

### Post by alejo0823 on 2008-04-25
ok np. I think that will solve your problem but if everything fails try this.
[http://ubuntuforums.org/showthread.php?t=763829](http://ubuntuforums.org/showthread.php?t=763829)

---

### Post by forestpixie on 2008-04-25
You need to install

```
simple-ccsm
```
then you'll get the Extra in appearances

---

### Post by BluePlum on 2008-04-25
I reinstalled all green things, FAIL! i tried to install the fuision-icon thing. It wouldnt DL it.... Installing simple CCSM now...... god im never getting new ubuntu again lol

---

### Post by BluePlum on 2008-04-25
still says cannot enable effects.... cmon guys ubuntu is nothing without effects!

---

### Post by alejo0823 on 2008-04-25
what video card do you have?
have you tried the link I gave you?
do you have the restricted drivers installed?
when you try to change the effects does it give you an error?

---

### Post by BluePlum on 2008-04-25
I have an Ati radeon something. Its not new and its a laptop.
Effects ran fine in Gusty.
I cant seem to find restricted drivers in hardy.
I have not tryd the link i try now tho :D
It says effects can not be enabled. So i guess thats an error.

---

### Post by alejo0823 on 2008-04-25
well thats the problem, there is no way to enable compiz without the drivers, unfortunately I never have to use an ati card so I dont know how to get their drivers, but it should be tru the restricted drivers administrator in system administration.

---

### Post by Google Spider on 2008-04-25
> **alejo0823 said:**
>  I dont know how to get their drivers, but it should be tru the restricted drivers administrator in system administration.

yeah System>Administrator>Restricted drivers manager.


**OR **

```

sudo apt-get update

sudo apt-get install xorg-driver-fglrx
```

I had to install XGL along with the driver on Gusty for my ATI radeon xpress 200

---

### Post by mister_pink on 2008-04-25
If you're a bit lost its because its not called Restricted Drivers Manager anymore, its called "Hardware Drivers"

Good luck!

---

### Post by BluePlum on 2008-04-25
For some reason theres no restricted drivers there, The was some random one in gusty that wasn't my GPU but the effects worked 100% right. 

i did sudo apt-get update

sudo apt-get install xorg-driver-fglrx wat happens now?

and im doing the link now. WHY MUST EVERYTHING IN LIFE BE SO HARD!

---

### Post by Google Spider on 2008-04-25
> **BluePlum said:**
> 

i did sudo apt-get update

sudo apt-get install xorg-driver-fglrx wat happens now?


It should have downloaded and installed your driver. Now you restart your computer to get it working.

---

### Post by forestpixie on 2008-04-25
You could try to use envy to install the driver if there is one.

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

---

### Post by BluePlum on 2008-04-25
LAST TIME I USED ENVY IN GUST MT OS DIED! :D. 

+ i did what the link said and now when i click. System tools>Compiz Fusion Icon. Nothing hapens o.o

---

### Post by Google Spider on 2008-04-25
Did you restart after installing the driver?

---

### Post by alejo0823 on 2008-04-25
try this and post errors

> compiz --replace

---

### Post by BluePlum on 2008-04-25
Well i got the new bugged compiz working in the link. Which is rly hates my GPU. I gotta configure it now to make it work smooth. YAY FOR ME!

---

### Post by BluePlum on 2008-04-25
ok all i had to do was install the driver. How do i remove this gay buggy 2 hard to run compiz and get the good compiz? :D

---

### Post by joshrobinson on 2008-04-25
> **BluePlum said:**
> ok all i had to do was install the driver. How do i remove this gay buggy 2 hard to run compiz and get the good compiz? :D

what is exactly buggy about it? i was under the impression that compiz-fusion 0.7.4 was the only version in the repo?

im personally not using the repo version though

---

### Post by BluePlum on 2008-04-25
this one makes my comp work a 0.1 miles an hour. While the orginal one doesnt. The default 1.... some douche told me to delete it and install  a differnt one which SUX!

---

### Post by ptelder on 2008-04-25
> **BluePlum said:**
> this one makes my comp work a 0.1 miles an hour. While the orginal one doesnt. The default 1.... some douche told me to delete it and install  a differnt one which SUX!


Unless you've enabled any additional repos since the upgrade, you have the same compiz you did before the reinstall.

Chances are the slowness is coming from switching to fglrx. I'm having the same problem you have. Under Gutsy I used the open source Radeon driver.

Under Hardy I can see AIGLX is working okay in the Xorg log. Even when told specifically with the "--indirect-rendering" option, Compiz still doesn't work.

All Compiz outputs for me is:

```

Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

```

I've tried reinstalling Compiz myself, but no change. This seems like something that should have been caught before release....

---

### Post by BluePlum on 2008-04-25
so what do we do?

---

### Post by ptelder on 2008-04-25
Essentially. we get to bend over and take it. According to my friends Google and Launchpad: [It won't be fixed until Intrepid]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330").

The short version is that our ATI chipsets have been blacklisted. adding 

```
SKIP_CHECKS=yes
```

to /etc/xdg/compiz/compiz-manager will disable the blacklist check (along with every other sanity check compiz does). Brought the wobblies back for me.

You'll probably want to pull fglrx out before trying it though.

---

### Post by BluePlum on 2008-04-25
ok not everyone is an ubuntu pro.. sum it down?

---

### Post by ZooLA_IL on 2008-04-25
Here you go:
[HowTo: Compiz Fusion in Hardy on cards with "ati"/"radeon" open source drivers]("http://ubuntuforums.org/showthread.php?t=764633&highlight=SKIP_CHECKS")

---

### Post by BluePlum on 2008-04-25
yes but some douche told me to uninstall Compiz Fusion and install some slow crap one. How do i get rid of that can get the REAL compiz back?

---

### Post by ptelder on 2008-04-25
> **BluePlum said:**
> yes but some douche told me to uninstall Compiz Fusion and install some slow crap one. How do i get rid of that can get the REAL compiz back?

What we're saying is that the is no *slow crap Compiz*. There is however, a slow crap video driver - fglrx.

Presumably, when things were working under Gutsy. you were using the open source Radeon driver.

You seemed to say earlier in the thread that you had installed fglrx (after also reinstalling Compiz), and that Compiz had started working after that. What we're saying is that you need to undo what you did to switch to fglrx, and then follow either my or ZooLA_IL's lead on disabling the Radeon open source driver check.

---

### Post by BluePlum on 2008-04-25
well that worked but
Turns out for some reason my graphics card isnt good enough to run effects in hardy. Even tho it ran with 0 stress in gusty

---

### Post by alejo0823 on 2008-04-25
first you say I earned a lot of thx and now you say Im a douche?
well you are an idiot but still Im gona help you, to get the original compiz back you have to go to the link I gave you and uninstall what you installed and install the old compiz, all this with the names you have there and searching the names in synaptic, hope you dont get lost even if you are a stupid its not that hard to do.
if this doesn't work get a new video card.

---

### Post by ptelder on 2008-04-25
> **BluePlum said:**
> well that worked but
Turns out for some reason my graphics card isnt good enough to run effects in hardy. Even tho it ran with 0 stress in gusty
Okay, if you've switched back to the open source driver and it's still slow, it may be that some part of compiz has changed on you and now takes more video horsepower. Since most of compiz is modular, you may be able to get away with disabling all the effects you can live without and just keeping the ones you really want.

[The Compiz Wiki]("http://wiki.compiz-fusion.org/CCSM") has information about how the Compiz Settings Manager works. You can find it in Aptitude and/or SYnaptic if you accidently uninstalled it while troubleshooting.

If I were you, I'd use it to disable everything in Compiz, and see if it speeds up. If it does, then start adding effects and plugins back in until it gets too slow to use. If you can't ever get it to speed back up, find someone smarter to ask than us.

That's all I've got. Good luck.

---

### Post by BluePlum on 2008-04-27
crap the douche found are i called him a douche heh...

Is there someway to downgrade compiz to previous verson? 1 in gusty?

---

### Post by FredB on 2008-04-27
What are your problem(s) with Compiz 0.7 ? Compiz is not guilty for bad written drivers after all.

---

### Post by BluePlum on 2008-04-27
newest version wont run well extremly low FPS. DOnt understand all this mumbo jumbo so why not go to version which worked fine.

---

### Post by alejo0823 on 2008-04-27
oh men this compiz effects are great, sorry for the loser that cant have them because hes too cheap to buy a decent video card.

---

### Post by brommage on 2008-04-27
> **BluePlum said:**
> I have an Ati radeon something. Its not new and its a laptop.
Effects ran fine in Gusty.
I cant seem to find restricted drivers in hardy.
I have not tryd the link i try now tho :D
It says effects can not be enabled. So i guess thats an error.


I have the same problem with a Radeon Mobility U1 card.  After screwing up my first install, I figured out that Hardy had blacklisted some old ATI cards due to some problems with the drivers.  There's a workaround here: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by BluePlum on 2008-04-27
> **alejo0823 said:**
> oh men this compiz effects are great, sorry for the loser that cant have them because hes too cheap to buy a decent video card.



And ill look at that link soon thx for helping every1.

---

### Post by BluePlum on 2008-04-27
I did that and turned ALL effects of in compiz. Still low FPS. What is WITH THIS! What do i do now? :(

---

### Post by BluePlum on 2008-04-28
Ok im more confused then when i started so lets just STOP for a second. Let me resay my problem. Then we can re think the solution because nothing is working.

In gusty compiz ran fine. I have an old ATI radeon card. But compiz still ran stress free. I installed gusty. I Went to turn on effects. Said effects could not be turned on. I made this thread. Somehow we got compiz working.  I got 8 fps. I disabled all compiz effects. Still 8fps or low. 

What is the next step?

---

### Post by BluePlum on 2008-04-28
zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz

---

### Post by BluePlum on 2008-05-02
More ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ

---

### Post by Saint Angeles on 2008-05-02
try my groovy mini-tutorial for getting ATI working...

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

its just super amazing and awesome

---

### Post by MongooseCage on 2008-05-04
> **BluePlum said:**
> More ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ

Seriously, whats wrong with you? Chill out... Reinstall Hardy, there is no douchebag Compiz effects there is only one... you could just reinstall ccsm again. Everythign should just work like a charm then. Remember its being developed on a 6 month scale, within 6 months they are coming up with something better than Vista and XP.

---

### Post by BluePlum on 2008-05-05
your opinion :D.

+ ty for the guide but im sure im doing something wrong. On the first step i did,

assasin@Invisible-Assasin:~$ sudo sh ati[tab]
[sudo] password for assasin: 
sh: Can't open ati[tab]


:(

---

### Post by MongooseCage on 2008-05-05
> **BluePlum said:**
> your opinion :D.

+ ty for the guide but im sure im doing something wrong. On the first step i did,

assasin@Invisible-Assasin:~$ sudo sh ati[tab]
[sudo] password for assasin: 
sh: Can't open ati[tab]


:(

you tried restarting? Because I remember in gutsy. My compiz effects were slow... Then after a couple of restarts and fiddling around it fixed.

Have you tried checking out the blacklists? etc/modprobe.d/blacklist?

---

### Post by BluePlum on 2008-05-05
its not a restart issue.... + what do u mean backlist? i have a ati radeon 9000 :P

---

### Post by MongooseCage on 2008-06-19
> **BluePlum said:**
> its not a restart issue.... + what do u mean backlist? i have a ati radeon 9000 :P

Its a file that you can control whatever drivers that you want to allow or block.But I doubt it would do much good. Just screw your graphic card seriously. Such a shitty graphic card that is not widely supported nor high powered doesnt deserve to exist in such times.

---

### Post by BluePlum on 2008-06-28
> **MongooseCage said:**
> Its a file that you can control whatever drivers that you want to allow or block.But I doubt it would do much good. Just screw your graphic card seriously. Such a shitty graphic card that is not widely supported nor high powered doesnt deserve to exist in such times.

HOW DARE U DISS MY ATI RADEON 9000! Sure he may not be as flash as his grandkids. BUT I LOVE HIM AND THATS ALL THAT MATTERS!

---

### Post by MongooseCage on 2008-07-03
lol, freaking hilarious!:lolflag: let grandpa rest its his grand childrens generation, unless you suddenly become into a computer wizard and write the entire driver.

---

### Post by BluePlum on 2008-07-03
Maby i will.... " does a 1980's Montage of BluePlum Sitting at the computer Sweating and furiously writing the driver code while Eye of the tiger is playing "

" 1 week of montages later " aaahhhh Screw it " chucks GPU in bin.

---

### Post by MongooseCage on 2008-07-05
> **BluePlum said:**
> Maby i will.... " does a 1980's Montage of BluePlum Sitting at the computer Sweating and furiously writing the driver code while Eye of the tiger is playing "

" 1 week of montages later " aaahhhh Screw it " chucks GPU in bin.

Gets a 9800 GX2 x2 SLI, now working on the driver for it. lol, repeats the process.

---

### Post by BluePlum on 2008-07-06
lol xD

---

