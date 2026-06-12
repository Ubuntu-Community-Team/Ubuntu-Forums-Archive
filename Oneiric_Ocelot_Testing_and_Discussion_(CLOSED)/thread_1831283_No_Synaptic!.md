---
title: "No Synaptic?!"
date: 2011-08-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-08-23
Have I missed this?

I did a fresh install from yesterday's (22nd August) daily live and couldn't launch Synaptic. Obvious reason - it wasn't installed.

Looking at the manifest for today's ISO shows that it is not included. Before I raise a bug report, does anyone know whether this is a deliberate strategic omission, or an error? I do seem to remember reading some time ago that there was a long-term goal to remove Synaptic from the default package list and rely on Software Centre for package management.

---

### Post by Framli on 2011-08-23
IIRC, it has been deliberately removed since Alpha2.

---

### Post by lucazade on 2011-08-23
> **coffeecat said:**
> Have I missed this?

I did a fresh install from yesterday's (22nd August) daily live and couldn't launch Synaptic. Obvious reason - it wasn't installed.

Looking at the manifest for today's ISO shows that it is not included. Before I raise a bug report, does anyone know whether this is a deliberate strategic omission, or an error? I do seem to remember reading some time ago that there was a long-term goal to remove Synaptic from the default package list and rely on Software Centre for package management.

Yep, noticed here as well.
I think the removal is intended to be, the last component keeping synaptic on cd was apt url handler (don't remember exact package name) so, probably, now synaptic is no more dependency of any other package and it is for sure no more included in ubuntu-meta package.

(added synaptic to my post-installation script like other apps!)

---

### Post by coffeecat on 2011-08-23
Thanks! :) Yes, I'll add it to my post-install script as well.

Expect to hear a lot of moaning, groaning, weeping, wailing and gnashing of teeth come October. :p This is going to be even more unpopular than removing the GIMP from the default list!

---

### Post by meborc on 2011-08-23
there was a few quite heated discussions in the forums on removal of synaptic ([http://ubuntuforums.org/showthread.php?t=1789203](http://ubuntuforums.org/showthread.php?t=1789203)). the decision was based on the notion that software center and synaptic were both filling the same functions. also having software center bred "in the house" would allow the developers to add/remove features with more flexibility.

all in all, I really don't care as synaptic has never been my big hairy friend :) I rarely use the software center as well since i have grown used to apt. in any case, synaptic is in the repos and is easily installable

---

### Post by lucazade on 2011-08-23
> **coffeecat said:**
> Thanks! :) Yes, I'll add it to my post-install script as well.

Expect to hear a lot of moaning, groaning, weeping, wailing and gnashing of teeth come October. :p This is going to be even more unpopular than removing the GIMP from the default list!

eheheh..lol
obviously gimp is in the same list ;)

---

### Post by coffeecat on 2011-08-23
> **meborc said:**
> there was a few quite heated discussions in the forums on removal of synaptic ([http://ubuntuforums.org/showthread.php?t=1789203](http://ubuntuforums.org/showthread.php?t=1789203)).

Ah, right, I did miss it. Thanks.

---

### Post by ronacc on 2011-08-23
I predicted this back when they started that worthless software-center and I was called an alarmist and everything but a child of god . so here it comes . I TOLD YOU SO !

---

### Post by ~!geek!~ on 2011-08-23
Damm it!!! So Team finally came to the conclusion that Software Center was  ready to take place of synaptic manager!!! I doubt it!!!

---

### Post by meborc on 2011-08-23
> **~!geek!~ said:**
> Damm it!!! So Team finally came to the conclusion that Software Center was  ready to take place of synaptic manager!!! I doubt it!!!

I don't think that is the point. Average Joe would not use synaptic anyway. It is a more sophisticated tool which requires some basic knowledge of how linux libraries and programs function.

it is like arguing why mutt is not included in the CD :) (ok, not really, but you get my point)

---

### Post by Quackers on 2011-08-23
I suspect average Joe would use synaptic if he knew its benefits. That's not really a reason to replace it imho. The benefits need advertising! :-)

---

### Post by 3rdalbum on 2011-08-23
I don't really mind. Software Center works okay. It certainly works well enough to use it to install Synaptic, if you really want it.

Synaptic is a powerful piece of software but it's a bit confusing to have two package managers on the CD. Synaptic is a bit too non-appliance-like for new users, so it's obvious that Software Center must stay and Synaptic must leave the CD. I'll certainly install Synaptic straight away, as will most existing users.

I can't wait until they turn Update Manager into a lense. IMHO Software Center should be a lense too.

---

### Post by cariboo on 2011-08-23
> **ronacc said:**
> I predicted this back when they started that worthless software-center and I was called an alarmist and everything but a child of god . so here it comes . I TOLD YOU SO !

Actually it was announced shortly after the software center was released, that synaptic would eventually be dropped from the default install.

---

### Post by CaptainMark on 2011-08-23
just to be nosy id be interesed in comparing our post install scripts i bet us fussy old power-users have very similar packages which we all complain have been removed

---

### Post by ranch hand on 2011-08-23
> **cariboo907 said:**
> Actually it was announced shortly after the software center was released, that synaptic would eventually be dropped from the default install.
Yes.

And to answer the question put by the OP;
It is an intentional error.

---

### Post by madjr on 2011-08-23
wow, some people are acting as it is being removed from the repos or being killed like gnome2.

IT'S NOT !!!1

apt-get install synaptic

is not DEAD, it will be there.

yes i use it frequently and would like it in there by default, but i want software center and update manager to get its features.

specially **update manager** needs **SORTING** of updates by size, name, etc. (like the **linuxmint update manager** tool!)

[IMG]http://www.osdisc.com/images/products/linuxmint10/thumb_mintupdate.png[/IMG]

---

### Post by ranch hand on 2011-08-23
Yes, it is available.  So is Gimp and Aptitude.

This does not mean that removing tools so that the new user does not have the choice is a good thing.

Update Mangler needs jacked up and a new one backed under it.  Could be that the Mint folks got it right, maybe.  It certainly has to be better than the present UM.

---

### Post by ronacc on 2011-08-23
> **madjr said:**
> wow, some people are acting as it is being removed from the repos or being killed like gnome2.

IT'S NOT !!!1

apt-get install synaptic

is not DEAD, it will be there.

yes i use it frequently and would like it in there by default, but i want software center and update manager to get its features.

specially **update manager** needs **SORTING** of updates by size, name, etc. (like the **linuxmint update manager** tool!)

[IMG]http://www.osdisc.com/images/products/linuxmint10/thumb_mintupdate.png[/IMG]

I realize that it can be installed ( or built from source if it comes to that ) but that is not what is at question .The real question that is becoming more pressing with each removal is "what does Ubuntu offer me to entice me to choose it over 100+ other  distro's " and the answer is damn little .

---

### Post by Merk42 on 2011-08-23
> **madjr said:**
> wow, some people are acting as it is being removed from the repos or being killed like gnome2.

IT'S NOT !!!1

apt-get install synaptic

is not DEAD, it will be there.
and if it were dead, Ubuntu/Canonical would STILL be blamed (re: GNOME 2)

---

### Post by IWantFroyo on 2011-08-23
Sad. I always preferred Synaptic to the Software Center.

They do perform more or less the same function, but I find it easier to find technical packages through Synaptic.

Maybe one of the lighter Ubuntus will somehow resurrect Synaptic and ditch the USC. I doubt it, but I'm going to be watching Lubuntu.

---

### Post by cariboo on 2011-08-24
> **IWantFroyo said:**
> Sad. I always preferred Synaptic to the Software Center.

They do perform more or less the same function, but I find it easier to find technical packages through Synaptic.

Maybe one of the lighter Ubuntus will somehow resurrect Synaptic and ditch the USC. I doubt it, but I'm going to be watching Lubuntu.

So because synaptic isn't installed by default, you aren't going to use it?

Over the years, answering questions in the support sub-forums, a great number of users aren't even aware that synaptic was available, or what is is for, even though it was easily found in the System->Administration menu. With the software center being featured prominently in the Launcher, those types of users are never going to even miss synaptic being installed by default.

Just to clarify why synaptic was dropped from the default install I'll quote from [this]("https://wiki.ubuntu.com/SoftwareCenter") wiki page written in 2005:

> Rationale
Early versions of Ubuntu shipped many graphical utilities for installing and removing software: Add/Remove Applications, Synaptic Package Manager, Update Manager, Software Sources, apturl, GDebi, and Computer Janitor. This redundancy increased the amount of interface people had to learn, wasted space on the Ubuntu CD, fragmented development effort, and made people more likely to think that unsanctioned software installation methods were safe. Ubuntu Software Center replaces Add/Remove Applications, Synaptic, apturl, and GDebi, and acts as the main entry point to Software Sources.

Beyond providing a central point for installing and removing software, USC plays a small but important part in encouraging application development on Ubuntu, by providing application developers with a prominent way to offer their software for installation.

Although I agree with dropping synaptic from the default installation, it will still be among the applications I install to make my system usable for me.

---

### Post by jbicha on 2011-08-24
cariboo907 I agree. There's a bunch of specialized apps I install onto a fresh install but Ubuntu out of the box does extremely well at meeting a wide range of needs to get people going without duplication. There's always loads more software available that is an easy install away.

---

### Post by meborc on 2011-08-24
i agree with cariboo as well :) it seems so funny when people get fussy about the default set of programs when they always tweak and tune and mess with their setup anyway

I don't believe this "You removed program X, I will now move to os Y..." stuff. I don't think anyone uses Ubuntu for the default set of programs. I use it because it gives me a very nice and fast install of a good linux operating system which recognizes my hardware and has enormous amounts of support documentation (forums, wiki, blogs, etc.)

I could just install the minimal alternative ubuntu base and work up from there. That does not mean that I use a different operating system. I still use Ubuntu ant it's repositories. I still install all the tools I am used to (not synaptic) as I rely on Ubuntu for my work.

Instead of worrying over decisions like that we should be filing bugs on stuff that really matters like stability issues or regressions in new packages.

---

### Post by lucazade on 2011-08-24
Don't want to disturb guys..
but I haven't see anyone complaining about synaptic removal in this thread in a noisy way.

---

### Post by meborc on 2011-08-24
> **lucazade said:**
> Don't want to disturb guys..
but I haven't see anyone complaining about synaptic removal in this thread in a noisy way.

yep, you are right... my rant is meant more towards the other thread :)

---

### Post by lucazade on 2011-08-24
> **meborc said:**
> yep, you are right... my rant is meant more towards the other thread :)

ah ok :)

---

### Post by ventrical on 2011-08-24
Synunity Software Manager :)

Never mind :)

---

### Post by dino99 on 2011-08-24
hm, not localized now :(

edit: fixed with dpkg :)

---

### Post by jerrylamos on 2011-08-24
> **lucazade said:**
> Don't want to disturb guys..
but I haven't see anyone complaining about synaptic removal in this thread in a noisy way.

I just did 
sudo synaptic
and it worked.

I don't know if I installed it with 
sudo apt-get install synaptic
or whether it was left over before an upgrade.

I don't usually use the BFB "Ubuntu Start" if I can avoid it because I can hardly readl white text on white background.

Jerry

---

### Post by madjr on 2011-08-25
> **jerrylamos said:**
> 

I don't usually use the BFB "Ubuntu Start" if I can avoid it because I can hardly readl white text on white background.

Jerry

what u mean? mind sharing a pic

---

### Post by cariboo on 2011-08-25
For me the background of the dash has been different colours at different times of the day, at one point is was blue, then it changed to black, now it's a dark gray/charcoal.

---

### Post by CaptainMark on 2011-08-25
this is my dash today, wtf??

---

### Post by coffeecat on 2011-08-25
> **cariboo907 said:**
> For me the background of the dash has been different colours at different times of the day, at one point is was blue, then it changed to black, now it's a dark gray/charcoal.

Had you been changing the wallpaper? Mine always picks up a colour from the wallpaper.

---

### Post by meborc on 2011-08-25
> **coffeecat said:**
> Had you been changing the wallpaper? Mine always picks up a colour from the wallpaper.

For me also, but it seems that when a light colored wallpaper is used, the dash is way too white

See my 2 screenshoths. Even with the included wallpapers the problem is visible

---

### Post by coffeecat on 2011-08-25
> **meborc said:**
> For me also, but it seems that when a light colored wallpaper is used, the dash is way too white

Your second screenshot looks to be grey, not opaque white as in CaptainMark's screenshot Interestingly, if I change my background to solid white (#FFFFFF) the dash is white, but semi-transparent. Or rather, if I look closely where just the background is showing through, as it were, the dash looks to be a very pale grey. If I change the background to solid black (#000000) the dash is definitely not black, but a mid-grey, and semi-transparent.

@CaptainMark, are you using Unity 3d or 2d?

---

### Post by meborc on 2011-08-25
> **coffeecat said:**
> Your second screenshot looks to be grey, not opaque white as in CaptainMark's screenshot Interestingly, if I change my background to solid white (#FFFFFF) the dash is white, but semi-transparent. Or rather, if I look closely where just the background is showing through, as it were, the dash looks to be a very pale grey. If I change the background to solid black (#000000) the dash is definitely not black, but a mid-grey, and semi-transparent.

@CaptainMark, are you using Unity 3d or 2d?

Yes, it seems that using dark colors/wallpaper results in a much more readable dash. I have also tried White/Black backgrounds and the text is almost not readable on White background. I hope someone is working on this. I'll take a look in launchpad if there is a bug related to this.

EDIT: found it - [Bug #824916]("https://bugs.launchpad.net/unity/+bug/824916")

---

### Post by CaptainMark on 2011-08-25
@ coffeecat thats 3d, 2d appears as it should do

---

