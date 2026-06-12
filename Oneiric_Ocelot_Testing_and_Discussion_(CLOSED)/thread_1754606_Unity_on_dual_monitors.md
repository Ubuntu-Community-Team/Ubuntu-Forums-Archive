---
title: "Unity on dual monitors"
date: 2011-05-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by meborc on 2011-05-10
I have two identical monitors at work, both running on a nice 1650x1080 resolution.

For the global menu purposes, the top-bar is showing on both of the monitors. It is understandable, as when window is open on the second screen, you would expect to have the program menu accessible also from that screen. 

The problem is that the clock and the indicator area is showing up on both monitors. It is not only esthetically irritating, it is also quite confusing.

Global menu singlehandedly has ruined my Unity experience on multiple monitors and I don't have any great ideas how it could be changed in a way that will both support global menu and not take up much screen real-estate.

Any insights if this will be changed in the future?

---

### Post by kyleabaker on 2011-05-10
I agree. There is no need to duplicate all icons and menus just because there is a top panel. Also, the menu's behave as they are connected between monitors, when they shouldn't. Example in this screenshot:

[[IMG]http://img708.imageshack.us/img708/8125/screenshotgw.png[/IMG]]("http://img268.imageshack.us/img268/3462/screenshotnkn.png")

---

### Post by earthpigg on 2011-05-11
someone may already have asked/answered, but is there any word on the ability to relocate the vertical panel to the rightmost monitor?

---

### Post by fluteflute on 2011-05-11
> **kyleabaker said:**
> I agree. There is no need to duplicate all icons and menus just because there is a top panel. Also, the menu's behave as they are connected between monitors, when they shouldn't. Example in this screenshot:

[[IMG]http://img708.imageshack.us/img708/8125/screenshotgw.png[/IMG]]("http://img268.imageshack.us/img268/3462/screenshotnkn.png")

That's [a known bug]("https://bugs.launchpad.net/unity/+bug/742020").

Personally I'd like to see the ability for both panel's to be used at once: [Bug #755357 ]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/755357")

---

### Post by meborc on 2011-05-12
Usability guys need to buy themselves extra monitors and test it out. I have read through the bug reports and I agree with them.

It is just very interesting, that no-one thought of the issues Unity will introduce for people with multiple monitors :) 

I would have expected Ubuntu devs to have several big DELL screens (and a bottle of sunblock) in front of them :D

---

### Post by CreativeReach on 2011-05-12
Does anyone know how gnome3 operates with several monitors?

---

### Post by meborc on 2011-05-16
> **CreativeReach said:**
> Does anyone know how gnome3 operates with several monitors?

good question! (bump) does anyone have G3 running on multiple displays?

---

### Post by JPorter on 2011-05-16
Users with Gnome3 are reporting similar multi-spanning top bar issues.

[http://forums.gentoo.org/viewtopic-t-875943-start-0.html](http://forums.gentoo.org/viewtopic-t-875943-start-0.html)


I'm simply flabbergasted that the whole development process for Unity apparently proceeded without anyone considering the ramifications for real desktop PC use, particularly for users (like me) who use Ubuntu as their primary work OS.  Primary work PCs tend to be multi-monitor, and multitasking (on all displays) is a hugely important thing.

I'm starting to fear that the adoption of Unity may have significantly delayed the real corporate adoption of Ubuntu as a desktop OS. It was very close to "deployable" in 10.10, another 6 months of basic improvements (without significant UI changes) *would have seen our organization rolling out Ubuntu as our standard load rather than Win7*.  I'm not making a joke, this was seriously our roadmap.  Now, with the damage Unity has done to basic usability for business desktop use, that may never happen.

---

### Post by castrojo on 2011-05-16
> **JPorter said:**
> I'm simply flabbergasted that the whole development process for Unity apparently proceeded without anyone considering the ramifications for real desktop PC use, particularly for users (like me) who use Ubuntu as their primary work OS.  Primary work PCs tend to be multi-monitor, and multitasking (on all displays) is a hugely important thing.


Other than the launcher LeftOf bug (which sucks), multi monitor was extensively tested in 11.04.

On my system the global menu goes onto the panel where the application's window is, and the dual indicators is so you never have to go too far to use the indicator area.

---

### Post by JPorter on 2011-05-16
> **castrojo said:**
> Other than the launcher LeftOf bug (which sucks), multi monitor was extensively tested in 11.04.

On my system the global menu goes onto the panel where the application's window is, and the dual indicators is so you never have to go too far to use the indicator area.
Granted, but come on... a UI for desktop/business use that deletes a basic navigable menu to launch office software?  The "unity button" in the top left should launch a condensed version of the Gnome2 launcher menu, instead it gives users a glorified search function and a series of huge blocky buttons that mean very little to those who aren't already familiar with what they represent.

I didn't post in this thread to complain about Unity, my apologies... it's just that it has created an ongoing issue within our organization that has frustrated me greatly. Average business desktop users find it baffling when they are first confronted with Unity.  To put it simply: the fastest way to launch an application in a graphical UI should not be to search for it using the keyboard!  If Canonical is going to keep Unity around, it needs to be SIGNIFICANTLY improved prior to Oneiric, and the basic "hunt and click" user paradigm restored to the minimum usability that was present in Maverick.

---

### Post by castrojo on 2011-05-16
> **JPorter said:**
> Granted, but come on... 

I'm sorry, I was trying to stay on topic for answering the questions posted on this thread. If you want to complain about Unity there's plenty of those threads to give your feedback on.

---

### Post by kyleabaker on 2011-05-16
> **castrojo said:**
> ..., and the dual indicators is so you never have to go too far to use the indicator area.

This could easily be solved with a toggle setting for Unity, "Mirror Indicator menus across multiple monitors".

---

### Post by NCLI on 2011-05-17
> **JPorter said:**
> Granted, but come on... a UI for desktop/business use that deletes a basic navigable menu to launch office software?  The "unity button" in the top left should launch a condensed version of the Gnome2 launcher menu, instead it gives users a glorified search function and a series of huge blocky buttons that mean very little to those who aren't already familiar with what they represent.

I didn't post in this thread to complain about Unity, my apologies... it's just that it has created an ongoing issue within our organization that has frustrated me greatly. Average business desktop users find it baffling when they are first confronted with Unity.  To put it simply: the fastest way to launch an application in a graphical UI should not be to search for it using the keyboard!  If Canonical is going to keep Unity around, it needs to be SIGNIFICANTLY improved prior to Oneiric, and the basic "hunt and click" user paradigm restored to the minimum usability that was present in Maverick.

[SIZE="4"]REPORT USABILITY BUGS[/SIZE]
The only reason why Unity is usable at all on more than one monitor is because testers reported issues. Mark has even said that this cycle is all about refinement and usability issues, so report them! 

I disagree with a lot of your points though. For me, searching with the Dash is way faster to use than the menues ever were. If it seems like "hunt and click" to you,  you're "doing it wrong". 

It's akin to launching all applications by finding the actual executable. Sure, you can do it, but there are easier ways.

---

### Post by Sennaista on 2011-05-17
> **CreativeReach said:**
> Does anyone know how gnome3 operates with several monitors?

In gnome-shell the top bar only appears on the main monitor, unless you decide to "mirror" them. What I also like about gnome-shell is that the second monitor is considered as shared between different workspaces, so whatever windows you have there will be visible regardless of what workspace you are in.

---

### Post by meborc on 2011-05-17
> **Sennaista said:**
> In gnome-shell the top bar only appears on the main monitor, unless you decide to "mirror" them...

Well, that can not be done with Unity. The global menu requires that there are bars on both monitors.

I would like to open a bug report or give a blueprint of how to fix this, but unfortunately, I see no realistic way how to solve the issue.

The most non-intrusive way would be to have a option to select which monitor (bar) has the me-menu and indicators. But that does not get rid of the additional bar. 

Macs have also the "global menu" thing, how do they deal with multiple monitors? any mac users?

EDIT: A quick consultation with a mac user resulted in this information:
[LIST]
[*]Macs have top bar only on one monitor (left)
[*]If you have a window on the other monitor, the global menu still appears only on the main monitor
[*]This has never been a problem to the user and she acctually was surprised that she has never thought about having a bar on the other monitor as well
[/LIST]

So... lets get rid of the bar at the second monitor!!! :D

---

### Post by teachop on 2011-05-17
For improving dual monitor operation, the best thing Canonical could do with their resources is to get the basic video support working properly on a wider range of hardware.  On Natty I had trouble with external monitors where I didn't in the past.  I was able to get things to work out eventually, but two laptops, Intel integrated graphics on an i3, and nVidia discrete graphics on an i7, both took fooling around and pain.  Both required actions either with gconf-editor or xrandr script just to get basic operations correct.  Base "working" on more hardware is the best GUI tweak we could have if the goal is to reach 200 million users in 4 years (which was stated).

---

### Post by JPorter on 2011-05-17
> **NCLI said:**
> [SIZE="4"]REPORT USABILITY BUGS[/SIZE]
The only reason why Unity is usable at all on more than one monitor is because testers reported issues. Mark has even said that this cycle is all about refinement and usability issues, so report them! I will certainly start doing that, then. In the past, I remember usability bugs being closed constantly by Canonical devs with "Works as designed" type comments, aka "we don't want your input".  If that has changed, that's great.

> **NCLI said:**
> I disagree with a lot of your points though. For me, searching with the Dash is way faster to use than the menues ever were. If it seems like "hunt and click" to you,  you're "doing it wrong".I'm not talking about my own use, I have no problem with a quick text field, because I already know the name of the application that I want to run. I'm talking about the experience for a new user that's completely unfamiliar with Ubuntu. The classic Gnome application menu was part of a user's self-education about the system, they could look clearly at the menu and understand which applications were in which categories, in a quick organized list form. They could see all the options at a glance.  In Unity, you can see three or four at most, and the default (in a fresh load, no user interaction yet) seems to be to put random "installed" applications in the menu, and requires interacting with a non-intuitive dropdown menu to filter by category.  That's the part that's baffling for a new user that is migrating for the first time from Windows.  

I'll make a UI bug about it, but I'm not holding my breath for anything other than dismissal.  If I'm wrong about that, it would certainly help calm the nerves here about Canonical's committment to the business environment in general, and make the money that we could be spending on Landscape for our production servers much easier to justify.

I'm done hijacking the thread, thanks to everyone for their tolerance. :)

---

### Post by meborc on 2011-05-19
When KDE changed it's menu style, they kept the old "classical" menu as optional

Maybe there should be an option that when you click on the Ubuntu logo you get a menu instead of the lense

---

### Post by meborc on 2011-07-18
Just a small update:

Tried the OO image from yesterday and it seems we are going to have bars on both/all displays still.

I would open a usability bug but i get the feeling that this is the intended way.

Does anyone know how to find blueprints for the menu/dock/ui for unity? I have been searching around, but found nothing that states that we WANT to have the bar and indicators on both monitors. I would very much like to oppose this and suggest we go the more conventional Windows and Mac route leaving us more screen real-estate.

---

### Post by wgarcia on 2011-07-19
Eliminating the top bar in a monitor and still having global menus would put the menus very far away from the actual windows in those bar-less monitors. If this is how it is done in Mac OS it must be really irritating.

---

### Post by roololing on 2011-07-19
I think I am okay with there being bars on both monitors, as the bars don't take up a huge amount of space (like on Windows). But still, I strongly believe that having the top panel on both monitors should not be set in stone, they should be optional. Unity is taking so much of the malleability of the UI away, and Ubuntu is starting to feel less and less like Linux.

---

### Post by petersonja on 2011-07-20
Hi all!

I need some help. I use nvidia x server settings (screenshot: [http://farm2.static.flickr.com/1239/1461847980_f87f7c3173.jpg](http://farm2.static.flickr.com/1239/1461847980_f87f7c3173.jpg) - not mine) to activate my TV (second screen) to twinview when I want to watch some movie. It is works well, no problem with it. But I'd like to do it with commands. So what I want:

A terminal command, which activate second screen with Twinvew (not save this to x.org.conf).

And a command, which deactivate it.

Can somebody help me?
Thanks

---

### Post by cariboo on 2011-07-20
> **petersonja said:**
> Hi all!

I need some help. I use nvidia x server settings (screenshot: [http://farm2.static.flickr.com/1239/1461847980_f87f7c3173.jpg](http://farm2.static.flickr.com/1239/1461847980_f87f7c3173.jpg) - not mine) to activate my TV (second screen) to twinview when I want to watch some movie. It is works well, no problem with it. But I'd like to do it with commands. So what I want:

A terminal command, which activate second screen with Twinvew (not save this to x.org.conf).

And a command, which deactivate it.

Can somebody help me?
Thanks

What version are you running, as this is the Oneiric Testing & Discussion sub-forum.

Why do you want to do what you want via the terminal, when it is way easier to set up a second monitor the way you are doing it already.

---

### Post by meborc on 2011-07-21
> **wgarcia said:**
> Eliminating the top bar in a monitor and still having global menus would put the menus very far away from the actual windows in those bar-less monitors. If this is how it is done in Mac OS it must be really irritating.

it seems to work fine on macs... i don't use the menus so often that it would annoy me more than the lost screen space due to multiple bars.

and duplicate indicator area shows off as little unprofessional to me

---

### Post by wgarcia on 2011-07-21
On the duplicate indicators I agree, but on taking out the bar and putting the menus far away not. There are some applications where I use menus a lot, actually most of them that I think.

---

### Post by meborc on 2011-07-22
> **wgarcia said:**
> On the duplicate indicators I agree, but on taking out the bar and putting the menus far away not. There are some applications where I use menus a lot, actually most of them that I think.

maybe we will get an auto-hide feature? that would help on the secondary screen

---

### Post by petersonja on 2011-07-22
> **cariboo907 said:**
> What version are you running, as this is the Oneiric Testing & Discussion sub-forum.

Why do you want to do what you want via the terminal, when it is way easier to set up a second monitor the way you are doing it already.

I found a souliton for my problem: [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/) :)

---

