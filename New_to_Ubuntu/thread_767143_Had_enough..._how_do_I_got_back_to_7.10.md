---
title: "Had enough... how do I got back to 7.10 ?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by vidus on 2008-04-25
I just want a working system...

1. After the upgrade, my resolution is stuck in 600x800, but it does not list my graphics card in the hardware manager. So there is nothing to enable...

2. Broadcomm worked fine in 7.10, no longer works in 8.04. I tried to enable it in the hardware manager, it aks for the 8.04 disc. I insert the disc and press ok, but it just keeps asking for the disc... so I cant enable it.

So ya, that's enough for me.. screw 8.04, how do I go back to 7.10?

---

### Post by Calash on 2008-04-25
I believe you have to reinstall from scratch.  There may be a way to go back, but it would likely leave your system very unstable.

---

### Post by Paqman on 2008-04-25
There's no downgrade path available, i'm afraid. You would have to reinstall.

Re your Broadcom card: check your Software Sources. If the CD option is checked, uncheck it. And check all the others.

Your screen resolution: what graphics card do you have? Do you know what driver your system is currently using? Have you tried to reconfigure Xorg?

---

### Post by sam_delta on 2008-04-25
for your broadcom

try reinstalling fwcutter with aptitude (not synaptic)
worked with friend's broadcom and also worked in this guy's thread
[http://ubuntuforums.org/showthread.php?t=762248](http://ubuntuforums.org/showthread.php?t=762248)

you need a internet conection to do this, so , plug a cable or something
first make sure you have your system up to date and then 
go to a terminal and type to remove

```
sudo aptitude purge b43-fwcutter
```

update your repos with

```
sudo aptitude update
```

to reinstall type

```
sudo aptitude install b43-fwcutter
```

then restart pc, goto in system>administrator>hardware drivers, and activate broadcom driver


tell us how it goes
sam

---

### Post by vidus on 2008-04-25
Sam_delta. Thanks for the info.

When I get to "sudo aptitude install b43-fwcutter", it again asks for the 8.04 disc.. When I insert the disc and press enter, it again asks for the disc.. it does not see the disc, yet the disc folder pops up on the screen.

---

### Post by Michael.Godawski on 2008-04-25
Perhaps you can try to disable the CD as a software source. Go to System > Administration > Software Sources and disable cd, then reload and try again.

---

### Post by sam_delta on 2008-04-25
alright, it seems like youll have to activate repositories, universe and mutliuniverse

you can do this by going into synaptic then settings>repositories then make sure everything its checked (cononical supported open source, community mainteined open source, propetary drivers for devices, software restricted by copyright and source codes), and make sure you uncheck the "installable from the CD/DVD" on the bottom of the window, then, close synaptic , go into the terminal and try again, make sure you have a cable plugged in, or any type of internet connection

tell us if it works

sam

---

### Post by vidus on 2008-04-25
Sam,
This worked. It was the repos that did it.

Only thing left is my resolution.. then I will be fine with 8.04. I am currently in 800x600, and everything is HUGE!

It's an ATI card, in 7.10 I just enabled it in the hardware manager, but this time, its not listed.. so how can I enable something that's not listed?

---

### Post by sam_delta on 2008-04-25
alright, ull have to install ati drivers, ive heard many people doing this with a program called ENVY and its pretty easy, 

i would like someone that has done this before to tell us the exact instructions on installing ATI drivers, ill investigate on this tho, so if no one comes up, ill see if i find something on the net.

btw, your wireless worked?

sam

---

### Post by vidus on 2008-04-25
Sam yes I am on wireless right now! Very happy about that thank you. I did a quick search on this "envy" but all the info on google is still for 7.10...

---

### Post by nina_aoki on 2008-04-25
> So ya, that's enough for me.. screw 8.04, how do I go back to 7.10?

Well - you're going to have to reinstall from scratch.  But come on now... is it that bad?  Wouldn't you rather try and work the problem?  8.04 is a very mature OS -- there's a lot there.  If you could get your problems fixed would you stay with it?

These are all driver issues.  Maybe your upgrade was corrupted?  You could wipe your HDD and try again and let Ubuntu discover the appropriate drivers and get them for you rather than going backwards.

I do understand the frustration -- I work with Wordpress as well and I've been frustrated with upgrades when they didn't behave as expected; and usually after some patience and working thru the problem, I've been able to go forward.

Don't give up yet!  ;)

- nina

---

### Post by nhandler on 2008-04-25
Most of the guides that talk about 7.10 should still work on hardy. This is not true in all cases, but you could give it a try.

---

### Post by sam_delta on 2008-04-25
ight, glad your wireless worked
ill research on this, if anyone else can help on the AIT drivers, itll will be faster, ill get back here as fast as i find something on this

---

### Post by vidus on 2008-04-25
thanks guys.. i will stick with it... just frustrating when i had a perfectly operating OS with my purdy rotating cube and everything, then you upgrade and the system looks like crap and nothing works...

wireless is fixed, just need my resolution fixed.. 800x600 is massive.

---

### Post by Mazza558 on 2008-04-25
> **vidus said:**
> thanks guys.. i will stick with it... just frustrating when i had a perfectly operating OS with my purdy rotating cube and everything, then you upgrade and the system looks like crap and nothing works...

wireless is fixed, just need my resolution fixed.. 800x600 is massive.

Can you post your Xorg.conf?

---

### Post by Paqman on 2008-04-25
> **sam_delta said:**
> 
i would like someone that has done this before to tell us the exact instructions on installing ATI drivers, ill investigate on this tho, so if no one comes up, ill see if i find something on the net.


AFAIK, Envy works the same for ATI as it does for Nvidia. Envy is now in the Universe repo, you'll need [envyng-core](apt:envyng-core) and [envyng-gtk](apt:envyng-gtk) (for Gnome or XFCE)

Go to Applications > System > EnvyNG and run it. It's pretty goof-proof.

---

### Post by Saint Angeles on 2008-04-25
heres my mini-tutorial for getting ATI working...

i'll also post my xorg.conf file for fun

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by vidus on 2008-04-25
paqman is correct. envy is available in synaptic. I marked for install, unfortunately the download hasnt even begun... it's just sitting there. I would guesse the load on the ubuntu servers are too much at the moment? Ill give it some time.

---

### Post by sam_delta on 2008-04-25
i found that envy actually works on 8.04, you just need to go into synaptic and install EnvyNG (version for 8.04 according to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html))


sam

---

### Post by sam_delta on 2008-04-25
> **vidus said:**
> paqman is correct. envy is available in synaptic. I marked for install, unfortunately the download hasnt even begun... it's just sitting there. I would guesse the load on the ubuntu servers are too much at the moment? Ill give it some time.

you can try changing the server, go into synaptic settings>repositories, and where it says "download from" select other, and a window will pop up, click on "select best server" and let it test and select the best server suitable to you,

sam

---

### Post by vidus on 2008-04-25
thanks for that tip sam.. i am in canada, and the fastest server is new zealand! go figure... it's blazing at almost 200kb/s.

---

### Post by sam_delta on 2008-04-25
yeah, no problem, ull better wait till night to download , severs are being overloaded due to hardy , i was using some mexican server today until it just died or got exremely overloaded that it just stop working for me. had to change server in synaptic, it choose some server in texas and its working fine now. slow but working

good luck, ill be around if you have more questins, fortunely ill be able to help

---

### Post by vidus on 2008-04-25
update: ITS ALIVE!

For anyone else that stumbles upon this thread for the ATI card, heres a quick summary.

Go to synaptic, search for "envy" and mark for installation, core and gtk. and apply. Once installed it will be in applications, system utils. run it and follow the screens to select ATI and apply. Restart and your done!

Thanks everyone for the help, I am happy now. Ubuntu would be nothing without the great community that is eager to help the newbs like me get thing right, even through my frustration. Thanks guys.

Now to figure out why any menus are not showing up......

---

### Post by sam_delta on 2008-04-25
what do you mean menues are not showing up? if you click aplications , nothing shows up?

sam

---

### Post by vidus on 2008-04-25
uh oh... this is a bigger problem than I had thought.

Apps, places, sytem, right clicks, bookmars... no menus showing up anywhere. I have a feeling maybe the transparency has something to do with it but I cant change it cus I cant get into the system menu. ah!

---

### Post by sam_delta on 2008-04-25
humm, well have to figure something out, i was thinking of right clicking the aplications button on the top pannel and edit menue's properties, but you cant right click, so, let me figure something out

---

### Post by sam_delta on 2008-04-25
try turning compiz off, type alt-f2

```
emerald --replace
```

---

### Post by vidus on 2008-04-25
I realized if I click a menu and then click what "would" be there, it works... i got back to this thread after a reboot by clicking where I though the bookmark was in the list and it worked... so they are there, just invisible.

If I remove compiz then get it back, will my menus dissapear again?

---

### Post by vidus on 2008-04-25
emerald --replace does nothing: Could not open location 'file:///home/rob/emerald%20--replace'

---

### Post by sam_delta on 2008-04-25
i dont know, ive been reading of similar things caused by compiz, but its much esier to fix the problem with a working menu :P

sam

ill brb in 20 mins

---

### Post by sam_delta on 2008-04-25
my bad, try 
```
metacity --replace
``` 

brb in 20 mins

---

### Post by vidus on 2008-04-25
problem solved.. you can get to compiz setting by pressing alt+f2, and type in ccsm to start up compiz settings manager.

Look like in 8.04 they changed the way opacity setting are made, so the old setting I had in 7.10 = 0 in 8.04, which means my menus were invisible.

In the custom field under general --> opacity setting you can change the % to go the other way... apparently 100% in 7.10 = 0% in 8.04. What a crazy world. I hope Ubuntu devs know about this!

---

### Post by sam_delta on 2008-04-25
Alright, vidus, glad you made it work, and thx for explaining the solution, this way well be able to help other people with similar problems.

over the time ive learned that for every ubuntu issue, theres a solution.

Enjoy 8.04 hardy!!!!!! :)

---

### Post by vidus on 2008-04-25
I am beginning to see that Sam. Thanks for all you help again. The community needs people like you!

So far I am enjoying hardy. The fonts look much better!

---

### Post by sam_delta on 2008-04-25
thx for the words, ill be around if you have more problems :)

---

