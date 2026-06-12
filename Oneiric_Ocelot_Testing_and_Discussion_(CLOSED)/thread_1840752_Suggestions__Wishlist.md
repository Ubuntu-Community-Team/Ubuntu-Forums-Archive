---
title: "Suggestions / Wishlist"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by crimsonmane on 2011-09-08
Suggestions/Wishlist

Dash is used primarily to locate apps to run them long enough to get them on my Launcher. Would like to be able to right-click and add to Launcher or Start Up apps. Or at least an option to add apps to Launcher/Start-up during installation.

It is difficult for noobs to know where apps are located in the file system to add to start-up apps, let alone which exact file is the right one. Would like to be able to right-click either via Dash or Launcher or Desktop. Or have an option that Dash will instead just list all my installed programs [keywords: NOT categorically, just alphabetically]. 

Remove Empathy and use Pidgin. Empathy does not remember my option to allow certificate for facebook chat even though there's a check box for it. Pidgin default settings are cleaner than Empathy.

There is no option to choose what closing the lid does, nor pushing the power button.

"Disable touchpad while typing" setting does not work.

No option to disable touchpad entirely. Would be especially useful if automatic when using external mouse.

No option to boot with Num Lock on. It always boots with it off, and I use my numeric keypad constantly.

Text-Size setting is located under Universal Access, because it's considered a handicap feature. It should be considered a preference. I like my UI small. It should be located under Screen or Displays or Appearance. The rest of the features under Universal Access are handicaps, so it doesn't naturally belong there.

Option to inherently load whatever mail and messenger client you have installed at startup. These two things are commonly the primary function of the computer, and I like having them connected as soon as i'm connected to the internet. Also, clicking the mail icon always says "Set up mail." It should only say that if I have not configured my client. It should then switch to something else like "Open Mail." But if the mail client loads in the background (minimized) then it would not matter because instead of "set up mail" it will show "compose, contacts, etc"

There is no option to disable the guest account.

---

### Post by sir.sargento on 2011-09-08
> **crimsonmane said:**
> Suggestions/Wishlist

Dash is used primarily to locate apps to run them long enough to get  them on my Launcher. Would like to be able to right-click and add to  Launcher or Start Up apps.[B] Or at least an option to add apps to Launcher/Start-up during installation.
[/B] 

In software center it does ask you at the bottom of the software center screen if you would like to add a launcher icon.. There will be two buttons down at the bottom, one to add a launcher and one to do it at another time. Hope this helps.

---

### Post by crimsonmane on 2011-09-08
I just checked and there are no options at the bottom. I updated the system 5 hours ago.

---

### Post by sir.sargento on 2011-09-08
Hmm, I just installed a game to try this out. I did not see the options at the bottom to make a unity launcher either... This was an option included in the old software center. Does anybody know if this was removed from the new software center or is it a bug?

---

### Post by crimsonmane on 2011-09-08
Please don't derail my suggestions over this one item. For this one item, I would like, and I'm sure most users, especially the common every-day person, would at least want a newly installed application to put arbitrarily put a shortcut to the main program on the desktop, where we can right click or drag it into the Dock (Launcher), or navigate easily to it via Add Start-Up App. Right now this one area is going to prevent anyone but enthusiasts from wanting to use Ubuntu.

I spent 5 minutes looking for the "executable" for Pidgin to make it start when the computer does.

I spent 20 minutes trying to figure out how to make my display smaller (Text-Size).

These are not user-friendly options.

---

### Post by sir.sargento on 2011-09-08
> **crimsonmane said:**
> Please don't derail my suggestions over this one item.

I was not.... Was trying to see if it was still an option for you. Anyways no need to overreact man. Good luck :)

---

### Post by crimsonmane on 2011-09-08
sargento your reply and call to inspect was very much appreciated. i was more asking the second responder to refrain from the shout-out asking more people to talk about the one issue being a bug.

---

### Post by 3rdalbum on 2011-09-08
> **crimsonmane said:**
> Please don't derail my suggestions over this one item. For this one item, I would like, and I'm sure most users, especially the common every-day person, would at least want a newly installed application to put arbitrarily put a shortcut to the main program on the desktop

Oh, god no. For a number of reasons:

1. My desktop is MY desktop, and I hate it when programs decide to litter MY desktop.

2. It would take me five minutes to find a new icon on my desktop.

3. What you don't understand is that your user account hasn't installed a program. In fact, root has installed a program. Whose user account gets the desktop shortcut? Everyone's? If not, then how are the other users going to find the program?

"Ahh", you say, "They'd find it in the dash". But that's what you're saying is too hard for the administrator of the computer.

> Right now this one area is going to prevent anyone but enthusiasts from wanting to use Ubuntu.

Pfft. Sorry, but I had to make that noise. Millions of people who don't regard themselves as "enthusiasts" use Android, Symbian and Blackberry phones where new programs appear not on the desktop, but inside an "Applications drawer". Those people manage just fine. Why wouldn't they look inside the Applications drawer on Ubuntu?

The goalposts for Linux adoption keep shifting. First, the need to manually configure the monitor was going to keep people away from Linux. Then, when that no longer became a hurdle, people started saying that the lack of Flash 8 would stop potential Linux adopters. And now that we've got the latest Flash Player that the other platforms have, people reckon that the big issue holding people back from Linux is some tiny insignificant thing such as "Programs don't litter themselves upon your desktop" or "The system settings are under the on/off cog menu" or "There's no easy way to format a floppy disk" (no joke, I heard this one about ten years after everyone stopped using floppy disks).

Linux is here today. It's ready for most people. When they're switching to a new operating system, I highly doubt that they're going to run screaming away from a slight change in the user interface when they've just weathered a drastic landslide of UI changes.

---

### Post by jbicha on 2011-09-08
> **crimsonmane said:**
> 
It is difficult for noobs to know where apps are located in the file system to add to start-up apps, let alone which exact file is the right one. Would like to be able to right-click either via Dash or Launcher or Desktop. Or have an option that Dash will instead just list all my installed programs [keywords: NOT categorically, just alphabetically]

I'm not convinced that users need an easy way to make apps run at startup. However, Startup Applications was given prominence in Oneiric for some reason. I'd be happy if you opened a bug against gnome-session-properties asking for an easier way to add programs. Currently Add just throws you into the file system and users shouldn't need to worry about where exactly their apps are stored.


> **crimsonmane said:**
> 
Remove Empathy and use Pidgin. Empathy does not remember my option to allow certificate for facebook chat even though there's a check box for it. Pidgin default settings are cleaner than Empathy.


Sorry, but Empathy was chosen because telepathy promised easy chat/messaging integration in other apps. For instance, gnome-games got rid of ggz and was going to get multiplayer that used telepathy as a backend. But I don't believe anyone stepped up to do the work in gnome-games. There's probably some other benefits I don't know off hand.

> **crimsonmane said:**
> 
There is no option to choose what closing the lid does, nor pushing the power button.


That is a GNOME decision and many have already complained about it. Please just use gnome-tweak-tool.

> **crimsonmane said:**
> 
"Disable touchpad while typing" setting does not work.


I believe it works here, but the touchpad delay was turned down as it was annoying before to have to wait when trying to use the touchpad at nearly the same time as the keyboard.

> **crimsonmane said:**
> 
No option to disable touchpad entirely. Would be especially useful if automatic when using external mouse.


Feel free to open a bug against gnome-control-center. It should be opened against GNOME too if you know how. On the other hand, I believe many laptops have either a hardware button or a Fn key combination to turn off the touchpad. If you have one that doesn't work, use ubuntu-bug linux to report that.

> **crimsonmane said:**
> 
No option to boot with Num Lock on. It always boots with it off, and I use my numeric keypad constantly.


Check your BIOS settings. This seems to do the Right Thing on my computers.

> **crimsonmane said:**
> 
Text-Size setting is located under Universal Access, because it's considered a handicap feature. It should be considered a preference. I like my UI small. It should be located under Screen or Displays or Appearance. The rest of the features under Universal Access are handicaps, so it doesn't naturally belong there.


GNOME designers do not consider settings in Universal Access to be handicap features. For instance, they expect that laptop users operating in the sun will find the High Contrast feature useful. And you don't have to be handicapped to want to use the screen keyboard.

> **crimsonmane said:**
> 
Option to inherently load whatever mail and messenger client you have installed at startup. These two things are commonly the primary function of the computer, and I like having them connected as soon as i'm connected to the internet. Also, clicking the mail icon always says "Set up mail." It should only say that if I have not configured my client. It should then switch to something else like "Open Mail." But if the mail client loads in the background (minimized) then it would not matter because instead of "set up mail" it will show "compose, contacts, etc"


The setup mail bug was already reported. Having the mail client always run in the background should be reported as a feature request (if it hasn't been already). And we'll see what the developers think. It's too late for that to happen for Oneiric though.

> **crimsonmane said:**
> 
There is no option to disable the guest account.

Set allow-guest=false in /etc/lightdm/lightdm.conf

---

### Post by crimsonmane on 2011-09-08
@3rdalbum:
you're a major *******. i just so happen to be on a conversion mission to get local people using Linux, and what i have stated is not just "oh poor me" suggestions/wishlist items, they are legitimate end-user want and/or needs.

If people want Linux to rule the pc world, these suggestions should not be ignored or scoffed at the way you do. It is my suggestion to the Mods here to ban you.

@jbicha:
how can the community expect people to learn the ins and outs of linux/ubuntu? we're talking about every-day people. Linux will not be ready for "most people" until it drops the developers need to tailor to the tech savvy population.

@the rest:
we don't need responses that redirect people to back-doors and work-arounds. we need an operating system that works for 90% of people. that's called Critical Mass. and you should strive to reach it.

---

### Post by cariboo on 2011-09-08
> **crimsonmane said:**
> @3rdalbum:
you're a major *******. i just so happen to be on a conversion mission to get local people using Linux, and what i have stated is not just "oh poor me" suggestions/wishlist items, they are legitimate end-user want and/or needs.

If people want Linux to rule the pc world, these suggestions should not be ignored or scoffed at the way you do. It is my suggestion to the Mods here to ban you.

@jbicha:
how can the community expect people to learn the ins and outs of linux/ubuntu? we're talking about every-day people. Linux will not be ready for "most people" until it drops the developers need to tailor to the tech savvy population.

@the rest:
we don't need responses that redirect people to back-doors and work-arounds. we need an operating system that works for 90% of people. that's called Critical Mass. and you should strive to reach it.

Desktop interfaces are going through a major overhaul, do you expect a testing version to be feature complete?

If you are converting people to Ubuntu, you are doing them a major disservice by recommending an interim release. Interim releases (not LTS) have always been experimental in nature, and things don't always work as expected. I'd suggest if you are converting people, that you start them off on an LTS release, as they are supported for 3 three years. The majority of average users stick with what came on their computers, and really don't have any interest in updating every six months, the people that do update every six months are usually more computer savvy than your average user and are more willing to look for work arounds for problems they encounter.

Also keep in mind that we are all volunteers here, so please treat everyone with a bit of respect. If you don't like the answers given to you, you are free to go elsewhere to have your questions answered.

---

### Post by jbicha on 2011-09-08
crimsonmane, please calm down. If you feel someone is rude to you, the Right Thing is not to be rude back: in other words, don't call people names or threaten to report someone to get banned. As cariboo says, I don't know anyone that gets paid to answer questions like yours on the forums; I certainly haven't been paid for my Ubuntu contributions.

Also as I read it, every single one of your "problems" are actually feature requests, many of which are just differences of opinion. Ubuntu will not out of the box support everyone's personal preferences. Nothing you've mentioned is actually a critical mass issue. And as I said, there is a known need for an easy to work with advanced configuration tool which likely will still be too complex to be installed by default. CCSM is definitely not it; gnome-tweak-tool has potential (and already does well to configure GNOME Shell), or someone could write something new but they will almost certainly be doing so as a volunteer effort.

I agree with 3rdalbum that having a new launcher on your desktop every time you install an app may make sense on the iPhone but it doesn't make sense in Android nor does it make sense in Unity or GNOME Shell where there is easy 1 click access to all of your apps. It's quite easy to add items to the launcher on the side for easy access.

By the way your number lock issue should be [fixed]("http://git.gnome.org/browse/gnome-settings-daemon/commit/?id=808640667656668693cedd685f6a830bddc0117d") before Ubuntu 11.10 is released. I'm sorry if you were under the impression that all of the bugs had been worked out of Ubuntu 11.10 as that's definitely not the case. Beta means "not ready yet" but should be usable by technical users who know how to fix things if someone should go wrong.

---

### Post by ranch hand on 2011-09-08
> **cariboo907 said:**
> Desktop interfaces are going through a major overhaul, do you expect a testing version to be feature complete?

If you are converting people to Ubuntu, you are doing them a major disservice by recommending an interim release. Interim releases (not LTS) have always been experimental in nature, and things don't always work as expected. I'd suggest if you are converting people, that you start them off on an LTS release, as they are supported for 3 three years. The majority of average users stick with what came on their computers, and really don't have any interest in updating every six months, the people that do update every six months are usually more computer savvy than your average user and are more willing to look for work arounds for problems they encounter.

Also keep in mind that we are all volunteers here, so please treat everyone with a bit of respect. If you don't like the answers given to you, you are free to go elsewhere to have your questions answered.
I really wish that the Ubuntu folks would make it more clear about the LTS and its differences with the "regular" releases.

I am glad to see you do this in a forum that seems to be full of enthusiasts with little experience.  This may lead to some better understanding.

Thank you.

---

### Post by cariboo on 2011-09-08
> **ranch hand said:**
> I really wish that the Ubuntu folks would make it more clear about the LTS and its differences with the "regular" releases.

I am glad to see you do this in a forum that seems to be full of enthusiasts with little experience.  This may lead to some better understanding.

Thank you.

Unfortunately, announcing new release on the main Ubuntu page is part of their marketing plan. What better way to keep Ubuntu in the news, then to put a big push on new releases.

---

### Post by Harry33 on 2011-09-09
The numlock issue is finally fixed by this update:
gnome-settings-daemon_3.1.91-0ubuntu4

> gnome-settings-daemon (3.1.91-0ubuntu4) oneiric; urgency=low

  * debian/patches/00git_numlock_status.patch:
    - git backport, store the numlock status and apply it (lp: #841748)

---

### Post by crimsonmane on 2011-09-09
Thank you for all the replies.

First, in regards to my being rude, my apologies. I felt justified because of the mockery that particular user presented. If you expect everyone to be respectful, then you should extend that expectation to everyone.

My [psuedo] business model is to get people on LTS, because yes the bugs are worked out. The thing is, this new UI is, in my opinion, so easy to work with, and I want it to be successful, but it needs a bit more. If something is a bug, it may not appear to be a bug, because you don't list the designed functionality. How am I to know what is a bug vs design flaw? That's why it's here in suggestions. Do you know that none of the Ubuntu releases will play a DVD by default? That's silly and turns people away.

Of course there's lots of people who don't want their desktop littered with applications. But that's what I'm pointing out: Give people a choice. Don't take your personal preference and force it on others. That's not how you get people interested. The big problem with Linux is "too many choices for distros" and "not enough choices for usability within any of them." But like I said earlier, don't derail the big picture over the one idea about how to make newly installed applications accessible. Too late for that, it seems.

Typical forum behavior.

---

### Post by DogMatix on 2011-09-09
Why is there an awful banner at the top of the software centre, wasting screen real-estate?

Netbook users are not impressed

---

### Post by cariboo on 2011-09-09
> **crimsonmane said:**
> Thank you for all the replies.

First, in regards to my being rude, my apologies. I felt justified because of the mockery that particular user presented. If you expect everyone to be respectful, then you should extend that expectation to everyone.

My [psuedo] business model is to get people on LTS, because yes the bugs are worked out. The thing is, this new UI is, in my opinion, so easy to work with, and I want it to be successful, but it needs a bit more. If something is a bug, it may not appear to be a bug, because you don't list the designed functionality. How am I to know what is a bug vs design flaw? That's why it's here in suggestions. Do you know that none of the Ubuntu releases will play a DVD by default? That's silly and turns people away.

Of course there's lots of people who don't want their desktop littered with applications. But that's what I'm pointing out: Give people a choice. Don't take your personal preference and force it on others. That's not how you get people interested. The big problem with Linux is "too many choices for distros" and "not enough choices for usability within any of them." But like I said earlier, don't derail the big picture over the one idea about how to make newly installed applications accessible. Too late for that, it seems.

Typical forum behavior.

I just want to point out, that this is an interim release, and some of the features we are using may not make it into the next LTS release. If you have big concerns, create bug reports, or become a member of the [Ayatana]("https://launchpad.net/ayatana") mailing list. We don't normally see a lot of developers in this sub-forum, when they do chime in, it's usually to address a specific problem.

---

### Post by crimsonmane on 2011-09-09
I'll let the people in #ubuntu+1 know that they were wrong and this is not the suggestions forums they thought it was.

---

### Post by cariboo on 2011-09-09
> **crimsonmane said:**
> I'll let the people in #ubuntu+1 know that they were wrong and this is not the suggestions forums they thought it was.

Someone is feeding you the wrong information, it's a well known fact that most developers don't frequent the forums.

---

### Post by VinDSL on 2011-09-11
> **crimsonmane said:**
> No option to boot with Num Lock on. It always boots with it off, and I use my numeric keypad constantly.[...]
This has been a major PITA for me too, but...

For the last couple of days, the numlock has been turning on at boot.  Yeah!

Anybody else seeing this?!?!?

---

### Post by jbicha on 2011-09-11
That was fixed here: [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.91-0ubuntu4](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.91-0ubuntu4)

---

### Post by VinDSL on 2011-09-11
> **jbicha said:**
> That was fixed here: [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.91-0ubuntu4](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.91-0ubuntu4)
Okay, thanks!

2 days ago...

That man deserves a Nobel!  :)

---

### Post by dmoconnell on 2011-09-12
I don't get why someone would signup for an account just to cause trouble. anyway, looking forward to the new release. I got a question for anyone (maybe VinDSL can answer) Have they full integrated Thunderbird and Lightning (mail and calendar clients) into Ocelot yet? I have evolution with a passion, had way to many problems with it that when i had to reinstall my system I never reset that up.
thanks
Dm

---

### Post by jbicha on 2011-09-12
No, Lightning is not installed by default nor is it integrated into the clock menu. I believe that's a goal for Ubuntu 12.04.

---

### Post by VinDSL on 2011-09-12
Thunderbird is working great!

I've never been a T-Bird fanboui, but I'm pleased with its implimentation in UbuOO.  Looks fully integrated, to me.  ;)

Empathy has been working okay too, surprisingly.  I don't know how many times I've tried it, but it usually breaks within a few days... and I'm back to Pidgin.  

Anyway, Empathy has been hanging in there, and it's fully integrated, as far as I can tell.

---

### Post by vasa1 on 2011-09-12
> **cariboo907 said:**
> ...
If you are converting people to Ubuntu, you are doing them a major disservice by recommending an interim release. Interim releases (not LTS) have always been experimental in nature, and things don't always work as expected. I'd suggest if you are converting people, that you start them off on an LTS release, as they are supported for 3 three years. The majority of average users stick with what came on their computers, and really don't have any interest in updating every six months, the people that do update every six months are usually more computer savvy than your average user and are more willing to look for work arounds for problems they encounter.
...

As Oscar Wilde put it, "The only thing worse than being talked about is not being talked about." so that may explain the prominence Canonical gives to the six-monthly releases.

Even I had the impression (for which I blame myself) that the releases that come out every six months are "stable" since they appear after a period of "beta" testing. I'm sure a lot of people not steeped in beans have the same misunderstanding.

But I'll do my best to suggest to people who are trying Ubuntu for the first time **and** who want stability to stay on the LTS track.

All that said, I don't really find 11.04 to be the nightmare it's being made out to be by some tech sites and blogs.

---

### Post by dmoconnell on 2011-09-12
> **jbicha said:**
> No, Lightning is not installed by default nor is it integrated into the clock menu. I believe that's a goal for Ubuntu 12.04.

> **VinDSL said:**
> Thunderbird is working great!

I've never been a T-Bird fanboui, but I'm pleased with its implimentation in UbuOO.  Looks fully integrated, to me.  ;)...

At least Thunderbird is
Its kinda (word that rimes with witty) that they didn't integrate Lightning as well in 11.10 I mean what are we suppose to do. I liked the fact that I could see upcoming events in one click.  Does anyone know of a "hack" that I could do to integrate Lightning into UbuOO? 
Thanks 
Dm

---

### Post by 3rdalbum on 2011-09-13
> **crimsonmane said:**
> @3rdalbum:
you're a major *******. i just so happen to be on a conversion mission to get local people using Linux, and what i have stated is not just "oh poor me" suggestions/wishlist items, they are legitimate end-user want and/or needs.

Okay, my tone wasn't exactly respectful on reflection. I'm sorry about that. My point about the applications drawer stands, though; the desktop is not the appropriate place for littering program launchers around. The Applications menu (or the Applications Lense) brings some organisation to it all, and that's the appropriate place for program shortcuts.

I do hear a lot of people saying "If Ubuntu did *xyz* exactly the same as Windows, hoardes of people would convert straight away". Usually, "xyz" is something really insignificant like "floppy disk formatting" or "program installers"; things that are holding nobody back from installing any form of Linux.

The real answers to desktop Linux adoption are not these papercut-sized differences from Windows. I don't know what the answers are, but I can tell what the answers **aren't**.

Sorry for my tone earlier. I hope you don't have any hard feelings.

---

### Post by dmoconnell on 2011-09-13
> **3rdalbum said:**
> Okay, my tone wasn't exactly respectful on reflection. I'm sorry about that. My point about the applications drawer stands, though; the desktop is not the appropriate place for littering program launchers around. The Applications menu (or the Applications Lense) brings some organisation to it all, and that's the appropriate place for program shortcuts. 

just my 2 cents. you were being blunt. and (IMO) blunt is not always a  bad thing. Some people hate piers morgan on America's. Got Talent cause  he's extremely blunt at times.


> **3rdalbum said:**
> I do hear a lot of people saying "If Ubuntu did *xyz* exactly the same as Windows, hoardes of people would convert straight away". Usually, "xyz" is something really insignificant like *"floppy disk formatting"* or* "program installers"*; things that are holding nobody back from installing any form of Linux.

The real answers to desktop Linux adoption are not these papercut-sized differences from Windows. I don't know what the answers are, but I can tell what the answers **aren't**.

Sorry for my tone earlier. I hope you don't have any hard feelings.

haha save for your knowledgeable computer enthusiast or IT guy going "old-school" on a computer,  who uses a floppy any more? and as for program installers I like the fact that I can go to one place and install everything (2 if you count installing via terminal) Just recently I (word that rhymes with mucked) my computer and had to restore it. It took me 1.5 hours just to get it to factory new then another several hours of updates. Ubuntu only took about 30 minutes to get everything back up and running. and part of that is because A) Ubuntu (IMO) doesn't install a ton of trial stuff that you have to remove B) all my stuff to install is in one place and i can go click click click.

and in the tone of Mark Zimmerman " If people wanted to convert to Ubuntu, then they would convert to Ubuntu"  

That's my 2 cents (feels more like i tossed in a buck fifty their)
Dm

---

