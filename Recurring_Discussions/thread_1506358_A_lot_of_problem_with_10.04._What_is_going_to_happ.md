---
title: "A lot of problem with 10.04. What is going to happen?"
date: 2010-06-10
forum: Recurring Discussions
---

### Post by irv on 2010-06-10
After reading through all the posts on this thread: [http://ubuntuforums.org/showthread.php?t=1465548&page=111]("http://ubuntuforums.org/showthread.php?t=1465548&page=111") and all the nightmares users were having installing and upgrading 10.04, our community might be getting smaller. I myself could not install 10.04 on one laptop that has been running Ubuntu for about 5 years now and I couldn't even get the CD to boot to a live OS. And I tried two CD that booted in other PC's, just fine. I do have 10.04 running on one Server, one Laptop, and one Desktop. It was just this one laptop I was having problems with. But from reading all the post in the above link thread, I am not the only one out here with that problem.
I finely when back to 9.1 and that is where it will stay on that one.

---

### Post by immoweichert on 2010-06-10
Software moves on , hardware stays behind. Guess this will happen in many operating systems. I don't understand why everybody wants to upgrade if their prior version of a distro is working ok. How many 5 year old laptops will be upgradable from XP to windows 7 ?

---

### Post by del_diablo on 2010-06-10
immoweichert: You will never understand the dream of updated software and a rolling distro.

---

### Post by mikewhatever on 2010-06-10
Some people are so dramatic, the latest and greatest doesn't work for them and they call it a nightmare and are ready to leave. What can I say, all the best, and hope you find a better distro, and a better community. That's the way life is.

---

### Post by philinux on 2010-06-10
Maybe a lot to do with plymouth. Plymouth + nVidia = :shock:

People have found where the livecd wont boot using nomodeset as a boot option.

---

### Post by NCLI on 2010-06-10
> **irv said:**
> After reading through all the posts on this thread: [http://ubuntuforums.org/showthread.php?t=1465548&page=111]("http://ubuntuforums.org/showthread.php?t=1465548&page=111") and all the nightmares users were having installing and upgrading 10.04, our community might be getting smaller. I myself could not install 10.04 on one laptop that has been running Ubuntu for about 5 years now and I couldn't even get the CD to boot to a live OS. And I tried two CD that booted in other PC's, just fine. I do have 10.04 running on one Server, one Laptop, and one Desktop. It was just this one laptop I was having problems with. But from reading all the post in the above link thread, I am not the only one out here with that problem.
I finely when back to 9.1 and that is where it will stay on that one.

True, [it ain't looking pretty]("http://spreadsheets.google.com/pub?key=t0XWfWgqJpYxCGAZ1G8U-og&output=html"), but you should never judge these polls before they've run their course, since it gets moved to different sections of the forums at set intervals.

---

### Post by immoweichert on 2010-06-10
> **del_diablo said:**
> immoweichert: You will never understand the dream of updated software and a rolling distro.
 
OOOh the old totalitarian answer - if you don't agree you are simply not able to understand. :lolflag:Well, at least I do understand the limitations of outdated hardware. There are limits.

---

### Post by RiceMonster on 2010-06-10
People complain about problems every release. Is this one really any different?

---

### Post by NCLI on 2010-06-10
> **RiceMonster said:**
> People complain about problems every release. Is this one really any different?

It does seem that this release is pretty bad in terms of apparent issues, but it is nowhere near the horror that was 8.10 according to my statistic(above) based on the polls here.

---

### Post by Stancel on 2010-06-10
Look at the Networking & Wireless forums. There are threads everyday by people who like me could not maintain a stable wireless connection to the Internet after upgrading to Lucid. 

The main symptoms of Lucid Lunacy is:

1) seeing that your computer sees the networks, clicking on your network, but it won't connect
2) it asks for the network key, you type it in, or it might already be saved on there, you click ok, but it keeps asking for your network key.
3) When it does connect to the Internet successfully, often after a reboot, it will randomly kick you off the Internet, often not after much time.

All this makes trying to find information on the Internet about fixing the Internet connection incredibly difficult, if you can't connect.

I've upgraded to Lucid three times now, each time trying my best to fix the problem, but then giving up. I think if I try it again, I will go insane. Each time I would downgrade with the Jaunty Live CD I have, but now I have decided I will stick with Jaunty. The Internet in Karmic works, but I don't think Karmic was that big of an upgrade to matter to me.

I'm not trying to whine, just show people what is going on for many people. A lot of people want to get defensive and talk about how they have no problems with Lucid. Yes, but the fact is, many people are having problems.

---

### Post by irv on 2010-06-10
> **immoweichert said:**
> Software moves on , hardware stays behind. Guess this will happen in many operating systems. I don't understand why everybody wants to upgrade if their prior version of a distro is working ok. How many 5 year old laptops will be upgradable from XP to windows 7 ?

You are right on your last statement about 5 year old laptops going from XP with Win7, but I can get most every flavor of Linux to run on older machines. Right now I am triple booting with Windows and a couple of Linux OS's. I have Peppermint booting on my laptop because it boots up in about 10 seconds if I have to get on the Internet fast. It is no more that a cut down Ubuntu with a little different look. I like it because many of the features are the same as Ubuntu, and I just like Ubuntu.
I did notice a lot of those moving away from Ubuntu in the other thread were low beaners, (newer users). I believe the old user will hang in there.
Oh yes, I do agree that there is nothing wrong with staying with an older version, but the support will die by the wayside.

---

### Post by kamaboko on 2010-06-10
> **immoweichert said:**
> Software moves on , hardware stays behind. Guess this will happen in many operating systems. I don't understand why everybody wants to upgrade if their prior version of a distro is working ok. How many 5 year old laptops will be upgradable from XP to windows 7 ?

My dad's HP is.

---

### Post by buellman on 2010-06-10
> **RiceMonster said:**
> People complain about problems every release. Is this one really any different?
It is!

My biggest complain is that they made KMS default for most ATI-cards even though it provides more problems than anything else:
+ nice plymouth
+ nice switching between terminals and X
- very limited powermanagement --> all ATI-cards
- not working suspend + hibernate --> at least for owners of old radeon cards (for example radeon 7000 and 7500... don't know about newer ones). My radeon 4670 at least does proper suspend... but no hibernate.

So... if I would have to decide: would I like a nice boot experience on my notebook or working suspend, hibernate and powermanagement... I would prefer working suspend, hibernate and powermanagement any time.

One could say: just disable KMS. Well... I tried that:
+ working powermanagement
+ working suspend and hibernate
- not so nice boot experience
- freezing screensaver --> does not turn on the backlight after some time of activation (at least with my radeon 7000. Have not tested it with 7500 or the 4670)

To sum it up: how can it be that in a LTS at least such an important feature like powermanagement is left behind in favour of a good looking boot screen? I know that more powermanagement for ATI is coming with 2.6.34 and the versions following but that does not help anyone with an ATI-card
- who wants to use a LTS for the coming 2 years because afaik there are no upgrades for kernels in a LTS which could provide more powermanagement features
- who prefers the open radeon driver over the closed one
- who has not the choice to use fglrx over the open radeon driver because the card in use is to old and therefore not supported by fglrx
Well... you could try to disable KMS in the hope to get powermanagement working. But then: why the whole trouble in the first place?
Well... you could install fglrx to get powermanagement working. But as it does not support KMS: again... why the trouble in the first place?

Sooooo... YES. At least this release is different to me than the others before. Why? Because it is a LTS from what I would expect that it would just work and not break an important feature (powermanagement) for a complete group of users... the users who own an ATI-card.
That could happen in every release... but in a LTS? I don't think so.

Greets. Buellman

---

### Post by mikewhatever on 2010-06-10
> **Stancel said:**
> ...

I'm not trying to whine, just show people what is going on for many people. A lot of people want to get defensive and talk about how they have no problems with Lucid. Yes, but the fact is, many people are having problems.

That's the way life is. Many people have problems and will continue to do so. It may be you today or me tomorrow, c'est la vi. Have you seen a perfect piece of software that is guaranteed to work every time on every hardware?

---

### Post by Frogs Hair on 2010-06-10
I installed 9.10 pretty late in the game and  the forums were full of 9.10 issues . With 10.04 I have had two issues both graphics related , one solved by removing emerald and the second solved by an update two days ago.
 
It is hard to tell what someone has done to their computer before coming to the forums for help and an unknown operating system makes matters worse. I have to admit that all my 9.10 issues were due to lack of Linux know how  Starting with a healthy computer is rule 1 for me.

---

### Post by kaldor on 2010-06-10
> **philinux said:**
> Maybe a lot to do with plymouth. Plymouth + nVidia = :shock:

People have found where the livecd wont boot using nomodeset as a boot option.

The bootup screen was one of the minor things that led me to removing Ubuntu. Hated it and kept getting "your computer is broken" or "linux is gross" comments all the time.

---

### Post by irv on 2010-06-10
I don't really put much stock in polls, but just for the record the thread that got this thread started shows the four groups, "Upgrade - worked flawlessly", "Upgrade - worked but had few things to fix, nothing serious though", "Install - worked flawlessly", and "Install - worked but had few things to fix, nothing serious though." Which makes up over 60% of upgrades and Installs went fairly well. And the two groups "Upgrade - got many problems that i've not been able to solve" and "Install - got many problems that i've not been able to solve" make up a little less then 40%. So we are looking at about 20% more installs and upgrades that went well. So I guess the bottom line is we are looking at 40% which I would hope would be less if we slowed down with pushing upgrades and new releases out to quickly. Maybe more bata testing and more users getting involved in our community. I believe Ubuntu is one of the best Linux distros out here, and I want it to stay that way so we must move forward but maybe just a little slower.
I know we will never get rid of all the bugs, but some were very serious one. Testing has to be done on as many different platforms as possible before releasing the upgrade.

---

### Post by WinterRain on 2010-06-10
> **mikewhatever said:**
> Some people are so dramatic, the latest and greatest doesn't work for them and they call it a nightmare and are ready to leave. What can I say, all the best, and hope you find a better distro, and a better community. That's the way life is.

I agree.

Match the OS to the hardware, and stop complaining. Why do people expect it to work on every computer in the world? Can I take a windows 7 cd and expect it to work on every single computer? Mac OS? Not even close. Why is ubuntu held to a different standard, and scrutinized more heavily?

Btw, the thread link provided by the OS doesn't mean anything. Considering there are millions of ubuntu users, the number of people in that thread is a drop in the bucket.

I love it when I hear: "I have 5 computers at home and all but one install went well. Ubuntu needs to fix these major problems quick." Can we stop the madness already?

And one other thing. If people would stop upgrading and doing more clean installs, there would be a lot less problems.

---

### Post by OLDMANHOOK on 2010-06-10
> **irv said:**
> I don't really put much stock in polls, but just for the record the thread that got this thread started shows the four groups, "Upgrade - worked flawlessly", "Upgrade - worked but had few things to fix, nothing serious though", "Install - worked flawlessly", and "Install - worked but had few things to fix, nothing serious though." Which makes up over 60% of upgrades and Installs went fairly well. And the two groups "Upgrade - got many problems that i've not been able to solve" and "Install - got many problems that i've not been able to solve" make up a little less then 40%. So we are looking at about 20% more installs and upgrades that went well. So I guess the bottom line is we are looking at 40% which I would hope would be less if we slowed down with pushing upgrades and new releases out to quickly. Maybe more bata testing and more users getting involved in our community. I believe Ubuntu is one of the best Linux distros out here, and I want it to stay that way so we must move forward but maybe just a little slower.
I know we will never get rid of all the bugs, but some were very serious one. Testing has to be done on as many different platforms as possible before releasing the upgrade. 40% Fail Rate is Not GOOD any where But on computers it's More than bad in this Windows World. I Posted a Few days ago about a post on OMG Ubuntu Many of the members of this forum blame everyone,everthing but the OS I'm trying Mint 9 Wireless works great on a laptop that worked in 9.10 but not 10.04

---

### Post by WinterRain on 2010-06-10
> **kaldor said:**
> The bootup screen was one of the minor things that led me to removing Ubuntu. Hated it and kept getting "your computer is broken" or "linux is gross" comments all the time.

Do you always have a crowd of people gathered around your computer every time you boot up? And secondly, who cares what other people think? You are a perfect example of succumbing to peer pressure. Must be a teen thing.

I'll be damned if I'm going to remove my favorite OS just because of some juvenile comments.

---

### Post by kabloink on 2010-06-10
> **immoweichert said:**
> Software moves on , hardware stays behind. Guess this will happen in many operating systems. I don't understand why everybody wants to upgrade if their prior version of a distro is working ok. How many 5 year old laptops will be upgradable from XP to windows 7 ?

On the other hand, how many 1 year old laptops would be able to upgrade from Vista to Windows 7? Some of the regressions are hitting recent computers that worked fine with 9.10.

---

### Post by SunnyRabbiera on 2010-06-10
Regressions happen a lot in linux, but some do it better then others.
openSUSE might be a good option, or even pure debian.

---

### Post by pete_m on 2010-06-10
After the precaution of updatting the kernel and making a sucessful reboot with grahpcis network wirelss n sound all playing nicley . 

I allowed aptitude to safe-upgrade  . .then can't reboot  .. . oh well - :confused:

writing this on eb4 booted from a  USB stick - those guys cut links wiht ubuntu after eb3. .  .n it's all  sid-based. .  .

I  thought that having sucessfully used an up to date kernel that issues with outdated hardware were not relevant - .  .. 
n the point about dad's old HP is well made - old hardware is standard(ish) n has always been supported understanable 
if some of the whizz bang stuff won't function on older machines but that's not an excuse - there should be an easy fallback when any such is found - cf. windows safe modes, n gfx. .  .

as for a lot being to do with an animmated splash render being  involved with handling strart up - looks to mee like it's just to do with the messaging..n shouldn't have been allowed anywhere near the realese - a staic splash or something ike the karmic n lode rones would be fine evenn for typical desktop users -- how much value does the animated thingy add . .

My upgrade was made  using lucid -only repositories  -ie without ppa mediahacks for mountall plymotuh related fixes) . . . 

hopefully i'll get the last plymouth stuff resolved
 soon as i can get network access form the init-/bin/bash which is all i can get to. 
. the recovery with network n such not being reached due to the plymouht upstart LXB mess ..  

.all largely beyond me. . hope i can get something fixed .

[SIZE=2]I do hope Ubuntu  is strong enough. . n that the seqeel to Maverick
[/SIZE]
 - whcih with its UNE desktp n gonme-shell on the way and dual-booting on lots of end-user laptops should be very exciting . . 
[SIZE=2]
won't be Neurotic Newt or Neglected Narwhal. . [/SIZE]

with best wishes to all. .  . scuse the ( my first ) rant 

[screenshots]("http://www.youtube.com/watch?v=YoI4wRVVjBs") of interrupted work in progress . .

the upgrade was hoping to preserve the desktop experiments i had made . .so i'm still resisting a fresh install - not least cos i haven't got Lucid iso to run form stick.. nor my own karmic derivative - tho the latter is happry with VirtualBox. . .
so a clean instal will likelyhave to  be made using the eb4 i'm using now wiht its Sid-based sources . .
and this eb4 being sid-based is probly using plymoouth from sid when it gracefully boots.   with LSB stuff.
plymouth aparently removed form squeeze so teh lucid one is its own beast . . .

):P - i had liked hte idea of basing machines on an LTS so that when sent out  into the world they would not need individual care uych as one is happy to lavish ion a  development and unstable machine

P.S. any help and comment welcomed - and speciifcally  how to get internet access from that raw root shell . ..
i tried to chroot but apt-get still wanted to use the live-cd's sources . .

---

### Post by ubunterooster on 2010-06-10
!0.04 was the biggest pain so far. I have set up Mint and it seems to work much better, faster, lighter (6 watts lighter) and way to green (I fixed that), and i needed to go back to the default gnome menu (I dislike both the default Ubuntu and Mint menus)

---

### Post by pete_m on 2010-06-11
cheers rooster - that sounds like it might be the way to go.  . .

tho as i can't boot mint nor lucid from nor my own larmic remix from iso ( unlike the eb4 i'm on now - phew! )

my upgrade is[SIZE=3] stuck[/SIZE] now - trying to get network access from a root shell gives me.  .
init 2
failed to connect to socket /com/ubuntu/upstart

this when trying an init=/bin/bash recovery as boot doesn't get to the recovery menu.  .

don't know what this error is - woud have been re-assuring to see org rather than com there - tho i daresay that's spurious !

for what it's worth Alt F1( or was it 2 ) tot change tty said - swithcing to colour frame buffer 128x37

guess it may be worth trying out Lucid again later - much later.  .in its lifecycle. .

---

### Post by OLDMANHOOK on 2010-06-11
I was going to start a new thread, but this one will do. I posted about a blog on omgubuntu a few days ago and was dismissed as  we done heard that,same old same O same ole song, reading reddit this morning hope everbody who thinks 10.04 is so good needs to think about what others are saying,It don't have to be true but if it put out there more and more people belive it and that will be the death of Ubuntu-- What people think about a product is 99% of the sale, As i have posted before I'm using Mint 9 and love it, Not as many Bugs, also MP3's and Stuff works out of the box---- Just Saying

Check Out This:[EMAIL="comp.os.linux.advocacy"]comp.os.linux.advocacy[/EMAIL] Hope it's typed right firefox don't want to copy and paste.

---

