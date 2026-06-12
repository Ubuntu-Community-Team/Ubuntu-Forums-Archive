---
title: "Unity problems"
date: 2011-05-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by gufide on 2011-05-03
There's some problem or lack of feature on unity, like lack of panel applets... Before, I was able to see my cpu utilization, temperature, I added some custom applets but now I can change nothing, add nothing ](*,)  and Launcher and menu setting... what a joke. What about icon size or backlight? I can't see nothing here! And there's no way to mount drive as fast as before. Why not in the place menu when there's no window selected? Thank you to listen my ideas.

---

### Post by DogMatix on 2011-05-03
Try here: [ Ubuntu Unity Tweaking](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by pbpersson on 2011-05-03
This is very helpful!  I am replying to this so I can find it later when I want to read up on all this good Unity info :)

---

### Post by pbpersson on 2011-05-03
So far in order to configure my Unity desktop I have had to install two things that were not included:

Compiz Configuration Manager
Dconf-Tools

Why in heavens name are:

1.  These things not installed by default?
2.  These things buried so you have to perform research just to configure your desktop?

I mean, when I go to the "themes and tweaks" section in Unity this should all be installed and included in a section "configure Unity"

How can this be considered a production release?  In my opinion, this was not completely planned and thought out.

I am finding all the pieces I need but I feel like I am on some sort of treasure hunt.  :confused:

---

### Post by DogMatix on 2011-05-04
I think the quick lists option for the home folder icon in the launcher should definitely be default in Oneriric.

---

### Post by Randicus on 2011-05-05
[pbpersson]("http://ubuntuforums.org/member.php?u=515872") is absolutely correct. 11.04 is not a finished product. Such problems as the launch bar appearing when someone drags and drops or whenever the left mouse button is pressed should have been fixed before the O.S. was released, not after.
I have read many other complaints about the size of the launcher icons and inability to customise the taskbar. I have not tried to tinker with it yet, but I agree that there should be room for customisation. Especially since the icons are much too large.
With unity, accessing installed programmes is way to tedious. The old applications button with the drop-down menu was quick and easy. Unity requires too much needless navigation.
The powers-that-be were in such a rush to implement the changes that the product was not given sufficient time for testing. The beta was only made available for about two weeks. Not nearly enough time to find all the quirks and bugs in a new system. To make matters worse, old problems have not been fixed. I just discovered that the problem of not being able to download up-dates is still there. That problem has been around since 10.04. Why is it still here? It should have been fixed a long time ago.
Unfortunately, we shall need to live with this unfinished system for the foreseeable future. One can only wonder how many potential Ubuntu users will be turned off by this mess and go elsewhere.

---

### Post by NCLI on 2011-05-05
> **pbpersson said:**
> So far in order to configure my Unity desktop I have had to install two things that were not included:

Compiz Configuration Manager
Dconf-Tools

Why in heavens name are:

1.  These things not installed by default?
2.  These things buried so you have to perform research just to configure your desktop?

I mean, when I go to the "themes and tweaks" section in Unity this should all be installed and included in a section "configure Unity"

How can this be considered a production release?  In my opinion, this was not completely planned and thought out.

I am finding all the pieces I need but I feel like I am on some sort of treasure hunt.  :confused:
Because a lot of those options are still experimental and crashy :)

On my laptop, they all work perfectly fine, but my netbook has various problems after changing them.
> **Randicus said:**
> [pbpersson]("http://ubuntuforums.org/member.php?u=515872") is absolutely correct. 11.04 is not a finished product. Such problems as the launch bar appearing when someone drags and drops or whenever the left mouse button is pressed should have been fixed before the O.S. was released, not after.
["That's not a bug, it's a feature"(TM)]("http://castrojo.tumblr.com/post/3198857225/random-small-bling")
> I have read many other complaints about the size of the launcher icons and inability to customise the taskbar. I have not tried to tinker with it yet, but I agree that there should be room for customisation. Especially since the icons are much too large.
Install CCSM to get at the customisation options.
> With unity, accessing installed programmes is way to tedious. The old applications button with the drop-down menu was quick and easy. Unity requires too much needless navigation.
What navigation? Just hit the super button(Windows key) and start typing.
> The powers-that-be were in such a rush to implement the changes that the product was not given sufficient time for testing. The beta was only made available for about two weeks. Not nearly enough time to find all the quirks and bugs in a new system.
You've been able to test Unity for more than six months.
>  To make matters worse, old problems have not been fixed. I just discovered that the problem of not being able to download up-dates is still there. That problem has been around since 10.04. Why is it still here? It should have been fixed a long time ago.
That would be a problem specific to your setup. If you don't report it as a bug, it's unlikely to be fixed.
> Unfortunately, we shall need to live with this unfinished system for the foreseeable future. One can only wonder how many potential Ubuntu users will be turned off by this mess and go elsewhere.
I don't think it's the potential users who will get scared off. It's mostly older, experienced users, who can't get used to not using menus to launch applications, or don't like the lack of customisability.

---

### Post by Randicus on 2011-05-05
The up-date problem is something many people have. It did not become a problem for me until I had been using 10.10 for five months, then suddenly I had problems adding up-dates. I checked the fora for a solution and found that it is a common problem. I do not know about all the other people who have experienced the problem, but with me it is not a system problem, since I did nothing before the problem suddenly occurred.

---

### Post by NCLI on 2011-05-05
> **Randicus said:**
> The up-date problem is something many people have. It did not become a problem for me until I had been using 10.10 for five months, then suddenly I had problems adding up-dates. I checked the fora for a solution and found that it is a common problem. I do not know about all the other people who have experienced the problem, but with me it is not a system problem, since I did nothing before the problem suddenly occurred.
Could you provide me with a link to the bug report?

---

### Post by Randicus on 2011-05-05
I never checked bug reports. I just followed the advice in the fora. The solution is to remove all but the first two download sources in the settings. Apparently, the main culprits are the last two: third party proprietary something (I forget), and universal. Removing those two usually allows up-date downloads. However, occasionally it will only work with the first source enabled.

---

### Post by NCLI on 2011-05-05
> **Randicus said:**
> I never checked bug reports. I just followed the advice in the fora. The solution is to remove all but the first two download sources in the settings. Apparently, the main culprits are the last two: third party proprietary something (I forget), and universal. Removing those two usually allows up-date downloads. However, occasionally it will only work with the first source enabled.
Sounds very weird, but since I've never encountered that issue, I think it's quite limited. It is a problem though, but if no one has reported it as a bug, it's never going to be solved.

---

### Post by cariboo on 2011-05-05
> **Randicus said:**
> The up-date problem is something many people have. It did not become a problem for me until I had been using 10.10 for five months, then suddenly I had problems adding up-dates. I checked the fora for a solution and found that it is a common problem. I do not know about all the other people who have experienced the problem, but with me it is not a system problem, since I did nothing before the problem suddenly occurred.

I just did an Oneric install, the extras repositories are not available yet, it's simple enough to go to software sources and disable them, to me it sounds more like a problem with the mirror you are using. 

Press the Super key and type syn, then click Synaptic Package Manager, got to Settings->Repositories, and change the Download from: to the Main server, you'll be prompted to update sources.list, then try the update again.

---

### Post by beew on 2011-05-05
> **NCLI said:**
> 
I don't think it's the potential users who will get scared off. It's mostly older, experienced users, who can't get used to not using menus to launch applications, or don't like the lack of customisability.

Why? Because they don't know better? And you think that is a good thing? What if the "potential users" actually try to work with the computer and get frustrated, oh since they are now actually doing things with the computer instead of staring at the UI they are now "old users" so don't count? What is the point of attracting new users but then cannot keep them? 

I should also point out that many "new users" get to know about Ubuntu through the old users who install the OS and set it up for them in the first place.  If the old users find Unity frustrating to use they won't recommend it to potential new users. I am about to set up Ubuntu for my room mate but after testing Unity quite a bit I have decided that I am going to install 10.10 in her system instead. Aside from Unity 11.04 is very buggy, I don't want to be constantly trouble shooting for her.

---

### Post by CreativeReach on 2011-05-05
> **beew said:**
> Why? Because they don't know better? And you think that is a good thing? What if the "potential users" actually try to work with the computer and get frustrated, oh since they are now actually doing things with the computer instead of staring at the UI they are now "old users" so don't count? What is the point of attracting new users but then cannot keep them? 

I should also point out that many "new users" get to know about Ubuntu through the old users who install the OS and set it up for them in the first place.  If the old users find Unity frustrating to use they won't recommend it to potential new users. I am about to set up Ubuntu for my room mate but after testing Unity quite a bit I have decided that I am going to install 10.10 in her system instead. Aside from Unity 11.04 is very buggy, I don't want to be constantly trouble shooting for her.

I've installed Ubuntu 11.4 for 3 different friends, and they all loved loved it.

I've been using Ubuntu since 9.04,and Fedora before that.
I'm loving Ubuntu with Unity, sure there a lot that needs to be improved. But I don't think it will scare the majority of the users.

---

### Post by demilord on 2011-05-06
> **Randicus said:**
> [pbpersson]("http://ubuntuforums.org/member.php?u=515872") is absolutely correct. 11.04 is not a finished product. Such problems as the launch bar appearing when someone drags and drops or whenever the left mouse button is pressed should have been fixed before the O.S. was released, not after.
I have read many other complaints about the size of the launcher icons and inability to customise the taskbar. I have not tried to tinker with it yet, but I agree that there should be room for customisation. Especially since the icons are much too large.
With unity, accessing installed programmes is way to tedious. The old applications button with the drop-down menu was quick and easy. Unity requires too much needless navigation.
The powers-that-be were in such a rush to implement the changes that the product was not given sufficient time for testing. The beta was only made available for about two weeks. Not nearly enough time to find all the quirks and bugs in a new system. To make matters worse, old problems have not been fixed. I just discovered that the problem of not being able to download up-dates is still there. That problem has been around since 10.04. Why is it still here? It should have been fixed a long time ago.
Unfortunately, we shall need to live with this unfinished system for the foreseeable future. One can only wonder how many potential Ubuntu users will be turned off by this mess and go elsewhere.


I agree with you, but we still have 10.04.2 LTS and 10.10.

It never should have been released in my opnion.. the classic gnome even didnt work properly and the continu blowing of my fan drived me crazy.. idk what it all is doing when being idle.. it might have to do with the lower battery time.. new process scheduler..  also i had problems opening programs.. it took sometimes 5 seconds before a program started to launch.. like there was a big delay.. or right click for customing the bottom panel the menu's are corrupted..

---

### Post by dino99 on 2011-05-06
Unity is a misery

why ? because it is built on an other misery: compiz

you doubt ? look at bugtracker: how many, how old, how is bug activity to fix the bugs related to both compiz & unity

Why all this ? its only an other shell in the gnome's land. On my end i'm waiting the next gnome-panel based on gtk3 (should be gnome-shell as per design)

---

### Post by macroshaft on 2011-05-06
What a sad sorry bunch you all are! Throwing in the towel at the first sign of a hurdle. Yes unity is unfamiliar and ubuntu is treading way off the beaten path. For that reason they need to tread with caution. How would you all feel if they presumed to know what we want, packed it full of useless features and got it wrong?

They made it work, in a measley 6 months they made it go and now is a time to sit back and see which bits are good, which bits are bad and which bits are missing. For ubuntu's take on this subject see here:-
[http://www.omgubuntu.co.uk/2011/05/mark-shuttleworth-talks-windicators-changes-for-unity-in-oneiric-and-whole-lot-more/]("http://www.omgubuntu.co.uk/2011/05/mark-shuttleworth-talks-windicators-changes-for-unity-in-oneiric-and-whole-lot-more/")

I see a load of complaining by people who have done NOTHING to change it. File bugs, give the devs a chance to take unity where it's going. I was very skeptical at first but I've grown to love it. That said however someone in this thread mentioned compiz being a root of the troubles and they are right. I installed unity 2D a few days back and quite frankly what's the difference? Do we need unity 3D at all?

---

### Post by ronacc on 2011-05-06
> **macroshaft said:**
>  How would you all feel if they presumed to know what we want, packed it full of useless features and got it wrong?



Isn't that EXACTLY what they did ?

---

### Post by macroshaft on 2011-05-06
> **ronacc said:**
> Isn't that EXACTLY what they did ?

Of course not, unity doesn't have any features yet, lol

---

### Post by Mortesins93 on 2011-05-06
I think that as macroshaft said we should not throw in the towel and should help out by filing bugs and such. I like the unity interface, although I never got a chance to use thoroughly because my wireless keyboard doesn't work (didn't work on ubuntu 9.10, 10.04 and 10.10 either), and I think it could be great for beginners but obviously it cannot have all these bugs people have been talking about to be "beginner-friendly". Infact as beew said most new users get to know about Ubuntu through the old users who install the OS and set it up for them so if I have to set up ubuntu for my friends I don't really know which version to choose because I'd like to install unity but can't because of all the problems.
As I said before, I haven't tried it out that much and I am trying to understand if it is really that buggy and shouldn't be given to beginners.

---

### Post by macroshaft on 2011-05-06
Let me ask you, how buggy was gnome panels v1.0? Probably a lot more than what we see today, it probably lacked features too! I have 100% confidence that they will iron most of this out by October.

---

### Post by Mortesins93 on 2011-05-06
If you are asking me I have no clue since I have been using ubuntu for a year an a half. I was reading about the interview with Mark Shuttleworth on omgubuntu and in the comments a guy said that his processor was not compatible with unity and some other guy said that his graphic card wasn't. I am not an expert and I don't know if these two guys were but I think that it is unacceptable (if it is so) that new releases have less support for hardware because in my opinion i think that is the big cause of ubuntu not being usable for everyone. When I my friends ask me downside of ubuntu and why it isn't used by everyone I always say that hardware compatibility is what I think is the biggest problem with ubuntu. I mean if i didn't have passion to learn about ubuntu and just wanted to use it to speed up my computer, to not have viruses and stuff like that, which is why some of my friends use it after I installed it for them, I would have left ubuntu long ago for all the problems I had with my wireless keyboard and most of all with my wireless d-link adapter even though on the box it said it had Linux support ( can't even imagine if it hadn't).

---

### Post by macroshaft on 2011-05-06
> **Mortesins93 said:**
> in the comments a guy said that his processor was not compatible with unity and some other guy said that his graphic card wasn't.

Firstly I can't understand why a processor would not be compatible with unity. As far as graphics compatibility goes this has been thought through. If your graphics card does not support compiz (and therefore unity) simply use unity 2D, it will become one of the defaults in oneiric.

I understand what you say about hardware compatibility so it's worth saving this link

[http://www.ubuntu.com/certification/catalog]("http://www.ubuntu.com/certification/catalog")

It is a database of certified ubuntu compatible hardware.

---

### Post by scradock on 2011-05-06
> **dino99 said:**
> Unity is a misery

why ? because it is built on an other misery: compiz

you doubt ? look at bugtracker: how many, how old, how is bug activity to fix the bugs related to both compiz & unity

Why all this ? its only an other shell in the gnome's land. On my end i'm waiting the next gnome-panel based on gtk3 (should be gnome-shell as per design)

The new gnome-panel is available as the fallback using the gnome-shell ppa.

I tried it - it looks old-fashioned and boring, now I've gotten used to Unity and Gnome-shell.

Just my 2 cents....

---

### Post by dino99 on 2011-05-06
> **scradock said:**
> The new gnome-panel is available as the fallback using the gnome-shell ppa.

Just my 2 cents....

agree but its too young right now, wait a few month for real alternative

---

### Post by cecilpierce on 2011-05-06
I went to G3 and it was cool for awhile and now Unity is getting a little better I'm back to it.
It will get alot better as time goes on, I just hope all the new people will figure it out, its not easy but fun...:)

---

### Post by NCLI on 2011-05-07
> **beew said:**
> Why? Because they don't know better? And you think that is a good thing? What if the "potential users" actually try to work with the computer and get frustrated, oh since they are now actually doing things with the computer instead of staring at the UI they are now "old users" so don't count? What is the point of attracting new users but then cannot keep them? 
You missed the point. The point is that many older users, who are set in their ways, and have used years to set up Gnome 2.XX just how they like it, are pissed off at Unity because it's currently not very customisable. At the same time, new users generally seem to find Unity an excellent UI, since they haven't invested any time in customising Gnome 2.XX, and were already prepared to learn something new when they left windows.

> I should also point out that many "new users" get to know about Ubuntu through the old users who install the OS and set it up for them in the first place.  If the old users find Unity frustrating to use they won't recommend it to potential new users. I am about to set up Ubuntu for my room mate but after testing Unity quite a bit I have decided that I am going to install 10.10 in her system instead. Aside from Unity 11.04 is very buggy, I don't want to be constantly trouble shooting for her.
I thin kyou''re going to get less troubleshooting with Unity. Boot up an Ubuntu 11.04 laptop/live USB, see what she thinks about Unity(Without interjecting your own bias), and if she doesn't like it, install 10.04 instead.

> **demilord said:**
> I agree with you, but we still have 10.04.2 LTS and 10.10.

It never should have been released in my opnion.. the classic gnome even didnt work properly and the continu blowing of my fan drived me crazy.. idk what it all is doing when being idle.. it might have to do with the lower battery time.. new process scheduler..  also i had problems opening programs.. it took sometimes 5 seconds before a program started to launch.. like there was a big delay.. or right click for customing the bottom panel the menu's are corrupted..
Have you checked the System Monitor? On my system, the UbuntuOne syncdaemon sometimes goes crazy.

> **Mortesins93 said:**
> If you are asking me I have no clue since I have been using ubuntu for a year an a half. I was reading about the interview with Mark Shuttleworth on omgubuntu and in the comments a guy said that his processor was not compatible with unity and some other guy said that his graphic card wasn't.
All fairly modern CPUs can run Ubuntu. You need some really, REALLY old CPU before you can't. Unity isn't substantially more demanding on the CPU side of things than Gnome 2.XX with Compiz.

When it comes to graphics cards, any card made within the last five years should run Unity perfectly fine, and for those that don't have one, there's Unity 2D.

> I am not an expert and I don't know if these two guys were but I think that it is unacceptable (if it is so) that new releases have less support for hardware because in my opinion i think that is the big cause of ubuntu not being usable for everyone.
According to this logic, we should still be using DOS, since a GUI requires a more powerful GPU, thus making it impossible for users without one to use it.

>  When I my friends ask me downside of ubuntu and why it isn't used by everyone I always say that hardware compatibility is what I think is the biggest problem with ubuntu.
That has nothing to do with Unity, it has to do with hardware vendors being late in releasing drivers. Also, "It's getting better all the time". It's was MUCH worse than it is now just 5 years ago.

> I mean if i didn't have passion to learn about ubuntu and just wanted to use it to speed up my computer, to not have viruses and stuff like that, which is why some of my friends use it after I installed it for them, I would have left ubuntu long ago for all the problems I had with my wireless keyboard and most of all with my wireless d-link adapter even though on the box it said it had Linux support ( can't even imagine if it hadn't).
Obviously it didn't have very good linux support. Again, this has nothing to do with Unity.

---

### Post by beew on 2011-05-07
> **NCLI said:**
> You missed the point. The point is that many older users, who are set in their ways, and have used years to set up Gnome 2.XX just how they like it, are pissed off at Unity because it's currently not very customisable. At the same time, new users generally seem to find Unity an excellent UI, since they haven't invested any time in customising Gnome 2.XX, and were already prepared to learn something new when they left windows.

I didn't miss the point, I get the point exactly and it is a very poor argument/excuse for a bad design.

There are objective ways to measure how easy or hard to perform a task regardless of whether you are an old user "set in your way" or  a new user. For examples, how many clicks it would require to open an applications, how far the mouse has to travel to reach the menu, how easy to switch between open windows and how intuitive to use the mouse as oppose to memorizing a long list of more or less arbitrary key combinations without rhyme and logic to do simple tasks (heard of the Unity cheat sheet wall paper? )

So** if **the new users generally find Unity an excellent UI it is because they don't know there are better alternatives, hardly a proof that Unity is an excellent UI in an objective sense. I would also ask you to back up your assertion that new users generally find unity an excellent UI with evidence. The only data available are Canonical's two userbility studies and they hardly supported your assertion.

The argument is as absurd as saying that the high heel is well designed  for running, if you disagree it is only because you are too  'set in your way' and are not 'prepared to  learn new things'.

BTW, I started using Ubuntu 2 months after Lucid's release, so it has been less than a year, I wouldn't think I am an old user very set in his way , there was a steep learning curve to switch from Windows and  I have been doing ok.

> I thin you''re going to get less troubleshooting with Unity. Boot up an Ubuntu 11.04 laptop/live USB, see what she thinks about Unity(Without interjecting your own bias), and if she doesn't like it, install 10.04 instead.
Actually I have a full install of 11.04  in an external drive (so I can boot it off different machines) and I have been testing since alpha2 and I use Unity only,--I don't use the Classical desktop. I don't test with live usb, I always do full install to get the real picture of performance and to keep up with system updates. I have tested it on her computer vs 10.10. Aside from the UI there are performance differences. At least 10.10 never crashed on me and there is no show stopping bugs like windows opening without max/min/close/restore buttons. Natty gets better ATI driver (open source) for her card but that difference disappears after I have installed the driver from xorg-edgers in Maverick. 

But to end this on a positive note even Natty with Unity is much better than the resource hogging virus magnet running on her laptop that is Vista so she would be easily impressed, cos she has very low expectations.

---

### Post by Peter09 on 2011-05-07
In you're assesment of how hard it is to do something - 

UI designers have long recognised that the mouse/menu system is not the best way of 
driving a computer. Navigating a mouse to a small target, moving over multiple other targets before selecting your target and clicking requires concentration and coordination. Just watch a beginner try to find a menu target by navigating across  a big menu.

Power users have for a long time deferred to keyboard shortcuts, command lines and searches to perform these tasks, even in MS Windows. They do it because it is quicker and easier - it allows the user to concentrate on the task in hand.

---

### Post by beew on 2011-05-07
> **Peter09 said:**
> In you're assesment of how hard it is to do something - 

UI designers have long recognised that the mouse/menu system is not the best way of 
driving a computer. Navigating a mouse to a small target, moving over multiple other targets before selecting your target and clicking requires concentration and coordination. Just watch a beginner try to find a menu target by navigating across  a big menu.

Power users have for a long time deferred to keyboard shortcuts, command lines and searches to perform these tasks, even in MS Windows. They do it because it is quicker and easier - it allows the user to concentrate on the task in hand.

So now Unity is for the power user rather than the "average user"?!!

BTW,  there is a glaring omission in the "expert's" observations, namely they don't take into the account of the time and effort to memorize random key combinations and becoming proficient in using them.I'll bet it is a lot easier for the new user to find the menu than to acquire the proficiency of keyboard gymnastics.

You are confusing ease of use (as in usability) and power, the command line is powerful but it is not easy to use and doesn't make for a good UI, otherwise Ubuntu will just have a terminal and that's it.

---

### Post by Peter09 on 2011-05-07
> So now Unity is for the power user rather than the "average user"?!!

Never said that, don't set up a straw man argument here.

Most casual users don't use short cuts because they are difficult to remember. Many Unity shortcuts are not difficult, Super+(icon number), Super+W(windows), Super+S(spaces) and Super+(D)desktop are some examples.

Now I am not saying that users will adopt these straight away, what I am saying that the 'it only takes one click' argument ignores the difficult part of the task.

---

### Post by NCLI on 2011-05-07
> **beew said:**
> I didn't miss the point, I get the point exactly and it is a very poor argument/excuse for a bad design.

> There are objective ways to measure how easy or hard to perform a task regardless of whether you are an old user "set in your way" or  a new user. For examples, how many clicks it would require to open an applications,
Zero in Unity, two in Gnome 2.
>  how far the mouse has to travel to reach the menu,
The menus is in the same place in Unity and Gnome 2, though to be efficient in Unity, you shouldn't use the mouse to open it.
>  how easy to switch between open windows
I agree that Unity currently has some shortcomings in this area. Which is why I'm glad that this is only a 1.00 release.

>  and how intuitive to use the mouse as oppose to memorizing a long list of more or less arbitrary key combinations without rhyme and logic to do simple tasks (heard of the Unity cheat sheet wall paper? )
To be efficient in Unity, you really only need to remember three things:

1. Tap the super key to open the dash.
2. Hold the super key to show quicklaunch combinations.
3. Super+D to show desktop.

I hardly ever use the third one, so for me it's actually only two things.

> So** if **the new users generally find Unity an excellent UI it is because they don't know there are better alternatives, hardly a proof that Unity is an excellent UI in an objective sense.
That is not what I was saying. What I am trying to say is th
at Unity, out of the box, is way better than Gnome 2.XX out of the box, and pretty much on-par with the best setups I've been able to put together, even though it's still rough around the edges.What it needs now is polish and customisability, which is what this cycle and the next is all about.
> 
 I would also ask you to back up your assertion that new users generally find unity an excellent UI with evidence. The only data available are Canonical's two userbility studies and they hardly supported your assertion.
We must have read different studies O.o

Anyway, I can really only back it up with personal anecdotes: Every single new/inexperienced user I've upgraded to Unity has found it easier to use than Gnome 2.XX. My tech illiterate mother even managed to upgrade herself, I only found out when I nx'ed into her computer last week to help her attach some documents to a mail she needed to send. She has had no issues with it whatsoever.

But anecdotes are useless, and therefore, all I can do is implore you to read through [the latest usability study]("http://design.canonical.com/2011/04/unity-benchmark-usability-april-2011/") again.

Yes, there are issues, but Mark has acknowledged this, and I expect most of them to be solved in 11.10.

> The argument is as absurd as saying that the high heel is well designed  for running, if you disagree it is only because you are too  'set in your way' and are not 'prepared to  learn new things'.

Stop using strawman arguments, it's pointless.

> BTW, I started using Ubuntu 2 months after Lucid's release, so it has been less than a year, I wouldn't think I am an old user very set in his way , there was a steep learning curve to switch from Windows and  I have been doing ok.
I was talking about my general impression of the people complaining. Obviously there are exceptions.
> 
Actually I have a full install of 11.04  in an external drive (so I can boot it off different machines) and I have been testing since alpha2 and I use Unity only,--I don't use the Classical desktop. I don't test with live usb, I always do full install to get the real picture of performance and to keep up with system updates. I have tested it on her computer vs 10.10. Aside from the UI there are performance differences. At least 10.10 never crashed on me and there is no show stopping bugs like windows opening without max/min/close/restore buttons. Natty gets better ATI driver (open source) for her card but that difference disappears after I have installed the driver from xorg-edgers in Maverick. 
I'm sure it will be fixed in 11.10. This cycle hasn't had much time for bug fixing outside of Unity and Compiz. I'm only interested in discussing the core design, more general issues are outside of the scope of this thread, IMHO.

Oh, and I have seen none of the bugs you talk about. I think it'd be a good idea to report them, since they're probably hardware specific.

---

### Post by Johnsie on 2011-05-07
Alot of people mostly use their mouse. They only use their keyboard when they want to type text.

---

### Post by Peter09 on 2011-05-07
> Alot of people mostly use their mouse. They only use their keyboard when they want to type text.

Yes, but that is inherited from MSWindows, where keyboard shortcuts are a bit of a afterthough. 

Again - why to PowerUsers favour keyboard shortcuts - easy to remember shortcuts are worth using and Unity has these.

---

### Post by beew on 2011-05-07
> **Peter09 said:**
> Yes, but that is inherited from MSWindows, where keyboard shortcuts are a bit of a afterthough. 

Again - why to PowerUsers favour keyboard shortcuts - easy to remember shortcuts are worth using and Unity has these.

Easy to remember? Did you create those? Seen the Unity cheat sheet wall paper? The point is why should I have to memorize a bunch of random key combos when my brain cells can be used for better things? I am a mathematician and I am not big on memorizing random stuffs with no logical or conceptual content to them, if I were I would be a historian or an organic chemist.

---

### Post by Mortesins93 on 2011-05-07
To NCLI and macroshaft,
Okay, so I am happy to hear that unsupported graphics card work fine with unity 2D (I didn't know).
About the hardware compatibility, first of all I am sorry I did not make it clear that I was talking about the OS in general and not only about Unity even though this thread should be about Unity. Second, I am not saying that Unity should work on 10 year old computers, for those there are other distros. What I was trying to say is that I think Unity is great and in my opinion it is a good way to attract new users but to attract new users it should be easy to use and not having your hardware working is not easy. For example, if someone tries out ubuntu and has my wireless keyboard he or she will leave it soon because it only works with xfce (why?). Or if someone has my wireless network adapter he or she will find it working out of the box for 2 or 3 months and then it won't work anymore (why? btw I have to say that this happened in Ubuntu 9.10 10.04 and 10.10, don't know if it will happen in 11.04). In other words, it's a pity to have such a nice and simple inteface and then can't use it because of drivers, but as you said it is not canonical's fault. In conclusion, all my talk is not against Unity or canonical but it is just a dissapointment about the fact that I can't ensure to my friends when I install Ubuntu that every hardware will work like on Windows. 
Anyways, I am disappointed to hear that this release has many bugs and hope 11.10 will be better so that I can installed it on my friends' computers.

---

### Post by rg4w on 2011-05-07
> **Peter09 said:**
> Yes, but that is inherited from MSWindows, where keyboard shortcuts are a bit of a afterthough. .
Keyboard-based navigation predates menus.  Menus evolved as a solution to that problem, not the other way around.

I don't understand this current anti-menu meme running around.  Menus aren't the answer for every problem, but for feature-rich apps they provide tremendous utility in making a command set immediately visible, discoverable, and accessible, and they pull all that off in very little space.

Typing is a useful *option*, but not a replacement for menus.

The better design for Natty would have been to have apps visible, listed by the same groups previously used as submenu names, allowing one to filter the display with typing as an option.  That way those who prefer typing can have the same functionality they enjoy in Natty, but new users can more readily discover things.

I'll be surprised if Unity doesn't evolve to use that by Oneiric.

---

### Post by teachop on 2011-05-07
> **Peter09 said:**
> MSWindows, where keyboard shortcuts are a bit of a afterthough
I coded some MSWin applications pretty early, before 3.1, before you could compile in Windows.  Code and compile was done in DOS, then you started up windows from the command line to test.  They had and encouraged hotkey accelerators for nearly every menu item, had them for window management, so it was not an afterthought.  Not that it was good, but you could pretty much run windows applications without a mouse.

---

### Post by RavensKrag on 2011-05-07
> **rg4w said:**
> 
The better design for Natty would have been to have apps visible, listed by the same groups previously used as submenu names, allowing one to filter the display with typing as an option.  That way those who prefer typing can have the same functionality they enjoy in Natty, but new users can more readily discover things.

Totally agree.  I feel like in their desire to counter bloated menus, Canonical switched to a more search-friendly interface.  In doing so, they over-corrected and missed the mark.  It seems like they do have the framework established for such a thing though, what with the shortcuts already in dash and the upcoming lenses.

It does indeed seem like the best interface would incorporate both typing and clicking.

---

### Post by beew on 2011-05-07
> **RavensKrag said:**
> Totally agree.  I feel like in their desire to counter bloated menus, Canonical switched to a more search-friendly interface.  In doing so, they over-corrected and missed the mark.  It seems like they do have the framework established for such a thing though, what with the shortcuts already in dash and the upcoming lenses.

It does indeed seem like the best interface would incorporate both typing and clicking.

The thing is it is not even that search friendly. If they intend you to use the search why the elaborate cartoon menu (the dash)? And why is it that you can only access the search function by opening the dash which takes up the whole screen (or 3/4 of it)? That is intrusive and bloated. They could have just put in a smart search launcher like Synapse. It has the same search functionality as unity but it is just a button sitting on the top  panel in Unity and when clicked a small search box opens up instead of the huge dash. I use Synapse instead of Unity's search most of the time.

So I am not sure really who the intended users of Unity are. Right now I see the Unity fan club is playing a certain sophist game. If you say Unity is not friendly to experienced users, they tell you it is good for the new users, if you point out its features are not really intuitive or convenient to the less experienced users they tell you it is great for power users. So basically it caters to neither.

---

### Post by rg4w on 2011-05-07
> **beew said:**
> The thing is it is not even that search friendly. If they intend you to use the search why the elaborate cartoon menu (the dash)? And why is it that you can only access the search function by opening the dash which takes up the whole screen (or 3/4 of it)?
Because if they put it in the top panel everyone would say they're trying to be like Mac. ;)

---

### Post by teachop on 2011-05-07
> **beew said:**
> The thing is it is not even that search friendly.
I was surprised it doesn't find everything, for example gconf-editor come up empty, but works if you use alt-F2 instead.  Probably this is to protect people, but it would be better if it found all the commands.

---

### Post by beew on 2011-05-07
> **teachop said:**
> I was surprised it doesn't find everything, for example gconf-editor come up empty, but works if you use alt-F2 instead.  Probably this is to protect people, but it would be better if it found all the commands.

Actually it does come up. I just tried.

---

### Post by teachop on 2011-05-07
> **beew said:**
> Actually it does come up. I just tried.
I wonder why not for me...  Works fine with alt-F2, dash just draws a blank...

---

### Post by ranch hand on 2011-05-08
> **Peter09 said:**
> Never said that, don't set up a straw man argument here.

Most casual users don't use short cuts because they are difficult to remember. Many Unity shortcuts are not difficult, Super+(icon number), Super+W(windows), Super+S(spaces) and Super+(D)desktop are some examples.

Now I am not saying that users will adopt these straight away, what I am saying that the 'it only takes one click' argument ignores the difficult part of the task.
I use keyboard shortcuts.  Unity is much slower to use than the old panel system, xfce or lxde and, possibly kde (I wouldn't know because I can't stand it).

The keyboard shortcuts were better designed in DOS.  Yes I do go back a ways.

Unity is fixing a problem for Ubuntu in that they have never gotten a decent desktop for smaller devices with a touch screen.  This is should be a lot better on one of those.

On a serious box with a literate and serious user it is just a poor gimick.

There are a number of things that would make it more usable on a decent laptop or desktop box.  It is not going to happen.

Why?  Because no one is interested in listening.  Ubuntu is going to be the OS for those with a lot of time and no serious interest in getting things done.  That is fine.

Just don't try to pretend otherwise.

For folks that want to stick within the Ubuntu family there are other choices and they work great.  GS may even turn out well.

I have an install of Debian Sid that is just waiting a bit to jump onto GS.  Neither are quite ready for that yet but I kind of look forward to it.

For those that are die hard Gnome 2 users there is Debian Squeeze.  It will be supported for a long time but it will certainly not be cutting edge.

@ronacc an beew
Watch your butts the fanboys are out in force.

---

### Post by teachop on 2011-05-08
> **ranch hand said:**
> the OS for those with a lot of time and no serious interest in getting things done.
Oy.

---

### Post by seeker5528 on 2011-05-09
> **NCLI said:**
> To be efficient in Unity, you really only need to remember three things:

1. Tap the super key to open the dash.
2. Hold the super key to show quicklaunch combinations.
3. Super+D to show desktop.

I hardly ever use the third one, so for me it's actually only two things.

Generally speaking all I need to remember is....

1: Left click for select.
2: Right click for context menu.

Don't use middle click much, even in Firefox since you never now how well it's going to work from one windows install to the next and 'Ctrl'+'left click' always seems to work, no matter what windows or linux computer you are on.

Later, Seeker

---

