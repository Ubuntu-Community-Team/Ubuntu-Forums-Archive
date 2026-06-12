---
title: "Anyone trying the newly designed dash yet? What do we think?"
date: 2011-08-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Curnel_D on 2011-08-12
I looked around on launchpad for some way to post feedback on changes, but didn't see a thing, so I figure I'd post it here instead.  

With the latest batch of updates, there's been a few UI changes.  One of the awesome ones is setting up the login prompt to look good.  And it does.  Huge improvement.  

But the worst change, IMO, is the new 'start' button location.  Instead of having it located at the top left of the screen on the tool bar, it's now vacant from that position entirely, and instead exclusively uses a unity dock button.  It went from looking great to looking not nearly as uniform and being less intuitive.  Not only that, now the menu it brings up just plain doesn't work.  It brings up a new 3D-ish menu that does look quite a bit better, but it closes without result when any buttons are clicked.  

I'll probably post the last bit as a bug on the tracker obviously.

But more to my point: Are there any UI devs that actually read these forums, and if so, could one explain the changes?  And if possible, tell me how to set it back the way it was without downgrading the last updates?

---

### Post by mc4man on 2011-08-12
> Not only that, now the menu it brings up just plain doesn't work. 
The places icons currently don't work, bug here, you can access any of the places thru the search & refined search
[https://bugs.launchpad.net/bugs/824842](https://bugs.launchpad.net/bugs/824842) 
> And if possible, tell me how to set it back the way it was without downgrading the last updates? 
Not much sense doing that, though you could if you wish thru downgrading, will be a whole boatload of packages, -  unity* , nux libs, compiz*, libunity

unity is moving forward, many things were fixed as will the issue(s) with the dash  and whatever else

---

### Post by CaptainMark on 2011-08-14
I think the idea of having the dash icon on the top bar was better, why make a launcher icon for it? it takes up more space on the launcher and now theres just bare space at the top, it was much easier to click when you could just drag to the top left and hit the left mouse button,

---

### Post by kaldor on 2011-08-14
Though I can see the point of doing it, I think it's horrible for aesthetics and general flow of the UI. The global menu now looks out of place, and the BFB now looks like a program. I really hate that change; not from a "I liked the way it was before!" perspective, but I think it just genuinely looks tacky.

The dash itself is much better, though.

---

### Post by lucazade on 2011-08-14
> **CaptainMark said:**
> I think the idea of having the dash icon on the top bar was better, why make a launcher icon for it? it takes up more space on the launcher and now theres just bare space at the top, it was much easier to click when you could just drag to the top left and hit the left mouse button,

From the usabilty test canonical made on unity, they have seen that BFB (the ubuntu button that was present in the panel) was not easily discoverable. So they moved it to the launcher, and probably what we see now it is not yet the final design and implementation.

---

### Post by CaptainMark on 2011-08-14
no i doubt (and hope not) that it will be. it doesnt flow too well, for the time being the dash is incredibly slow on unity3d but okay on unity2d, i expect we will see many changes to this yet because it just doesnt have that smooth user friendly feel to it yet

---

### Post by kaldor on 2011-08-14
> **lucazade said:**
> From the usabilty test canonical made on unity, they have seen that BFB (the ubuntu button that was present in the panel) was not easily discoverable. So they moved it to the launcher, and probably what we see now it is not yet the final design and implementation.

Yeah, they were looking at the Home icon as if it were the Home button on a phone or something like that. I think this would be easily remedied if they used the original "file cabinet" icon that they did during the Natty betas.

---

### Post by pelle.k on 2011-08-14
> **kaldor said:**
> I think this would be easily remedied if they used the original "file cabinet" icon that they did during the Natty betas.
Agreed! If they go through with this, i would appreciate if they at least make the former mode (where the icon is on the bar) optional. It may be user friendly (and discoverable) to have an icon on the sidebar, but it's less obvious to a long time ubuntu user, and also as previously pointed out, it's much easier to just flick the mouse pointer up in the corner and click, than it is having to actually aim for an icon. Surely you shouldn't have to sacrifice long-term usability for ease of discovery?

---

### Post by CaptainMark on 2011-08-14
ive given unity the benefit of the doubt for a while now, i really hope they dont keep making it less useable because in my opinion its actually got worse since it first came out, i can see myself jumping to kubuntu of opensuse if this keeps up

---

### Post by kaldor on 2011-08-14
> **CaptainMark said:**
> ive given unity the benefit of the doubt for a while now, i really hope they dont keep making it less useable because in my opinion its actually got worse since it first came out, i can see myself jumping to kubuntu of opensuse if this keeps up

I was extremely happy and hopeful when Unity was announced as the default for natty. I jumped in to using the 11.04 daily builds on a liveUSB whenever I could, and was very happy with the progress. But then, everything slowed down and not much was changed. I was expecting a lot more things to be happening during this release cycle but I haven't seen much to Unity. I'm not talking about under-the-hood stuff.

To me, it looks like Canonical is ignoring a lot of the UI problems and making downright stupid decisions.

Examples...

- Tiny Cyan triangle for notifications? wtf? I don't even notice it.

- How does a "+" with a magnifying glass have ANYTHING to do with Applications? It just looks like a Zoom button to me.

- Hiding global menu? What's the point of this? It's confusing beyond hell, and has no use. What's wrong with just keeping it visible all the time? As if I need to see "Firefox" written in two places in order to see what I am running. At least give the option to make it permanently visible, because it's a downright stupid design decision to hide it away, especially when it has NO benefit whatsoever. Also, everyone who has ever used my computer when running Unity always says "where is the File menu?". It's not even an obvious thing to figure out. I also remember some posts about people asking "where is File/Edit/View in natty?". It's just useless. 

- What's the point in the BFB? All it does is imitate the same stuff that the launcher does. It doesn't add anything useful. I can get to my files and applications using the Lenses in the launcher anyway.

Stuff like that makes me wonder what people at Canonical are thinking. I know a lot of you will come back with "WorksForMe" replies, or "give it time", but it's just these little things which are just make no sense that cause Unity to feel broken and unusable.

---

### Post by sgage on 2011-08-14
> **kaldor said:**
> I was extremely happy and hopeful when Unity was announced as the default for natty. I jumped in to using the 11.04 daily builds on a liveUSB whenever I could, and was very happy with the progress. But then, everything slowed down and not much was changed. I was expecting a lot more things to be happening during this release cycle but I haven't seen much to Unity. I'm not talking about under-the-hood stuff.

To me, it looks like Canonical is ignoring a lot of the UI problems and making downright stupid decisions.

Examples...

- Tiny Cyan triangle for notifications? wtf? I don't even notice it.

- How does a "+" with a magnifying glass have ANYTHING to do with Applications? It just looks like a Zoom button to me.

- Hiding global menu? What's the point of this? It's confusing beyond hell, and has no use. What's wrong with just keeping it visible all the time? As if I need to see "Firefox" written in two places in order to see what I am running. At least give the option to make it permanently visible, because it's a downright stupid design decision to hide it away, especially when it has NO benefit whatsoever.

- What's the point in the BFB? All it does is imitate the same stuff that the launcher does. It doesn't add anything useful. I can get to my files and applications using the Lenses in the launcher anyway.

Stuff like that makes me wonder what people at Canonical are thinking. I know a lot of you will come back with "WorksForMe" replies, or "give it time", but it's just these little things which are just make no sense that cause Unity to feel broken and unusable.

I feel the same sense of wonderment. I try Unity every day, but spend most of my time in Gnome Shell, which I am really getting to like...

It will be a cold day you-know-where before I go to KDE...

---

### Post by kaldor on 2011-08-14
> **sgage said:**
> I feel the same sense of wonderment. I try Unity every day, but spend most of my time in Gnome Shell, which I am really getting to like...

It will be a cold day you-know-where before I go to KDE...

My problem isn't with the change, but the constant overlooking and forcing of stupid "features" to Unity. Why redesign the whole Dash when things that are actually annoying aren't fixed?

I've also switched to Fedora 15 on my laptop because I was sick of always telling people "sorry, I didn't see your messages". Shell is awesome. I want to keep using Unity quite badly, but Canonical needs to wake up and realize that some things are just plain useless.

---

### Post by lucazade on 2011-08-14
@kaldor
yes, there are some issues here and there but nothing trascendental and i feel quite comfortable with it.
nice thing is we've used gnome2 and its shell for years and this was full of this kind of issues but i've never read a lot of complaints about these (probably because a lot were using third-party docks and shells)!

---

### Post by CaptainMark on 2011-08-14
i dont see the purpose in the applications and files and folders lenses anyway, applications you can search for as soon as you hit the dash icon anyway so why would you want to move the mouse and click on the applications lens at all, the files and folders lens is pointless because you cant really do anything with the folder youve searched for, and you have to know its exact name or the beginning of it to able to find it at all, id rather use a file browser anyday of the week

---

### Post by Sashin on 2011-08-14
This is the way I think it should be done, in order to make the ubuntu button easily discover as well as making it stylised differently from launcher icons so it isn't mistaken for an app, as well as having it capable of being opened from the top left corner (much quicker).

[http://i55.tinypic.com/2ezh2d2.jpg](http://i55.tinypic.com/2ezh2d2.jpg)

---

### Post by kaldor on 2011-08-14
> **lucazade said:**
> @kaldor
yes, there are some issues here and there but nothing trascendental and i feel quite comfortable with it.
nice thing is we've used gnome2 and its shell for years and this was full of this kind of issues but i've never read a lot of complaints about these (probably because a lot were using third-party docks and shells)!

Well, Unity is set up almost identical to how I had my Mac and GNOME setups. It's just little tiny things that drive me (and others) insane that should be so very quick to fix.

GNOME 2 didn't hide the menus away. It didn't have multiple useless menus that do the same thing as the other. It was also very simple for a new user to learn.

Not saying Unity isn't, but it has lots more "wtf?!" moments than any other DE I've used. That said, I still much prefer Unity to the old GNOME 2.x, if not solely due to the integrated dock and indicators. The reason that I am very critical of it is because I like it, and want it to be the best it can be. :)

---

### Post by CaptainMark on 2011-08-14
after using unity since early natty alpha days ive kinda got used to it, today i gave one of my netbooks an overhaul with lubuntu just to see how it runs and wow now i remember what a DE should behave like, its basically windows xp and that doesnt say much for unity

---

### Post by Rifester on 2011-08-14
I am starting to lose my optimism for Unity.     Just can't seem to mesh with KDE (wish that I could).   Seriously considering ending my testing days and installing Xubuntu.   I miss having some ability to configure my system and I don't think it is coming in 11.10.

---

### Post by Sashin on 2011-08-14
It will come, eventually.

---

### Post by jbicha on 2011-08-14
> **kaldor said:**
> I've also switched to Fedora 15 on my laptop because I was sick of always telling people "sorry, I didn't see your messages". Shell is awesome. I want to keep using Unity quite badly, but Canonical needs to wake up and realize that some things are just plain useless.

Gnome Shell works fine in Ubuntu.

---

### Post by teachop on 2011-08-14
> **Rifester said:**
> I am starting to lose my optimism for Unity.     Just can't seem to mesh with KDE (wish that I could).   Seriously considering ending my testing days and installing Xubuntu.   I miss having some ability to configure my system and I don't think it is coming in 11.10.
Xubuntu needs testers too, working pretty good for me.

---

### Post by kaldor on 2011-08-14
> **jbicha said:**
> Gnome Shell works fine in Ubuntu.

Well it was either use Natty or use Fedora 15. I know I could have installed a PPA or whatever, but that would have just been an extra step.

---

### Post by bennachie on 2011-08-15
I'm assuming (optimistically) that the present multiple regressions reflect the processes of making Unity work in the GTK3 framework. At present, Unity is a good deal less pleasant to use and versatile than the standard Gnome 3 Shell (which still has very little capacity for user configuration, but can at least offer internal consistency in the elements of the user interface).

I'm ambivalent about the location of the "Ubuntu Start" icon, and can't really see the point of the "universal menu" approach on anything larger than a 10-inch screen. However, the more immediate problems are that we appear to have lost the capacity to access less-frequently-used software by category, and have to resort to the "search" function, the process of adding icons to the sidebar has become unnecessarily complicated, synaptic has been relegated to the repos, ubuntu software centre remains distinctly flaky, system-config-printer is broken again (yes, I've lodged a bug report on the last of these) and we still have no "restart" button. Incidentally, the login manager no longer offers that option - nor, for that matter, does it offer the option to choose Unity2D or Gnome3.

OK, it's still an Alpha release, and I'm using 11.10 with my eyes wide open, expecting trouble, but we've now passed the "feature freeze" point, and there seems some cause to be concerned. Perhaps 11.10 is being used as no more than a dress rehearsal for 12.04. If so, let's hope that the old theatrical adage about the inverse relationship between the quality of dress rehearsals and that of the subsequent first night performance turns out to be applicable in the world of IT!

---

### Post by CaptainMark on 2011-08-15
im at least going to wait out the alphas before i take any drastic action, i really dont like gnome3 though, its default behaviour of bringing up a window grid and having to search for all application seems so un-natural to me, but for the gnome3 fans fedora is just ubuntu with gnome more or less, unity dash is good but it needs an easily accesible application tree like gnome 2, enough of this searching rubbish for my lesser used applications

---

### Post by jbicha on 2011-08-15
> **bennachie said:**
> Incidentally, the login manager no longer offers that option - nor, for that matter, does it offer the option to choose Unity2D or Gnome3.

Actually you can choose whatever session you want. Ubuntu & Ubuntu 2D are installed by default. Gnome Shell or Gnome Fallback/Classic and others will show up once you install them. Just click the drop-down box next to your name when you go to log in.

---

### Post by cariboo on 2011-08-15
I have Unity 2 and 3D Gnome shell and classic/fallback mode see the screenshot.

---

### Post by ventrical on 2011-08-15
> **cariboo907 said:**
> I have Unity 2 and 3D Gnome shell and classic/fallback mode see the screenshot.

 Same here, except I do not have the fallback classic modes for GNOME.

 Personally, the way Unity 2D is working, I am a real happy camper because the Unity 2D is working like a stable LTS release !!

The GNOME 3 is a little bit better than in Feodra 15, but the Unity2d is just awesome. The way the icons on the app windows scroll is really 'dreamy'.  I'm not sure why the other two DEs do not present the same effects.

---

### Post by Ichtyandr on 2011-08-15
I like the new location of "start button", perhaps because never got used to the old one in the first place. It is distinctly visible and outstanding in orange colors screaming "click me" and attracting attention.

The global menu is actually useful for widescreens, I have 1400x900 on my desktop, and when for example using compiz grid with two rows of apps, you gain two menubar spaces and keep the "notification area", which is nothing to be ashamed of.

The dash is still kinda slow though, particularly the 3d unity dash keeps "thinking" when searching for stuff. Compare to almost instant search&launch on kupfer or synapse eg (those ones do not work normally on oneiric for me)

The only thing missing is an easy way to look through a list of all currently installed programs in a menu somewhere for a peace of mind.

I also think the usability improved overall, as the desktop and the applications load instantly (perhaps I am lucky with hardware) and the whole experience "feels" very responsive.

---

### Post by JRV on 2011-08-15
The shadow from the top panel obscures the top of the dash icon.
It was not noticeable before when I had the terminal icon on top.
The blue dash does not go well with my theme/wallpaper.
Can the color of the dash be changed?

---

### Post by mc4man on 2011-08-15
> **JRV said:**
> The shadow from the top panel obscures the top of the dash icon.
It was not noticeable before when I had the terminal icon on top.
The blue dash does not go well with my theme/wallpaper.
Can the color of the dash be changed?
That's sorta interesting though don't see at all (on unity session
The panel shadow is normally drawn on the desktop so it would go behind the launcher and top icon

The dash is tinted based on your desktop image, is yours blue?

---

### Post by Sashin on 2011-08-15
I think the tinting should be alot more subtle.

---

### Post by JRV on 2011-08-15
I shutdown and restarted, now it is a slightly darker shade of the earth tone desktop.

I can live with that.

---

### Post by sffvba[e0rt on 2011-08-15
I can remember when Win 95 first came to be there used to be a little pop up over the "start" button that said you should click it...  Was one way to get people to do the right thing :)


404

---

### Post by Hardy Severit on 2011-08-15
> **cariboo907 said:**
> I have Unity 2 and 3D Gnome shell and classic/fallback mode see the screenshot.

Would be interresting to see how your classic desktop looks like. Is it Gnome 2 based or just the crippled Gnome3 fallback?

H.

---

### Post by mc4man on 2011-08-15
> **JRV said:**
> I shutdown and restarted, now it is a slightly darker shade of the earth tone desktop.

I can live with that.
It would appear that on the very 1st login on a fresh install (and maybe first time use of new dash on older) produces a weird green blue dash

After that all logins start using the desktop to color

Can also be seen in unity's new Alt+tab switcher which is similarly tinted 
The 'new' switcher has some interesting elements inc. 'details' on a switcher icon that has multiple windows open. (Alt+down arrow
 - not sure if navigation in a nautilus details view is intended, Alt+ l,r arrow keys while in detail view

---

### Post by akand074 on 2011-08-15
I agree with people saying it looks aesthetically odd to have the Ubuntu button on the launcher. Perhaps they should have the launcher take up the whole left side and remove the part of the top panel over the launcher. I'm sure they'll do something about it before the release though.

---

### Post by CaptainMark on 2011-08-15
the dash tint is detecting colours incorrectly, i tried with a few desktop backgrounds both black and white but on with a hint of red, the one with red tints the dash dark blue and the plain black and white tints the dash a horrible shade of brown

---

### Post by mc4man on 2011-08-15
There are several things not quite r. with the current dash - one is obviously the transparency is too high.
The other is the the blur causes the dash to extend into the panel and this causes panel opacity option (lowering) to fail.

If you remove the blur then one can again reduce or use a transparent panel
(if it was up to me i'd drop this tinting/blurring nonsense and create one nice looking lens for all
a couple of current bugs
trans - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824916](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824916)

panel/blur issue
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/827012](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/827012)

---

### Post by bennachie on 2011-08-15
Another odd feature in the current version of Unity on my system is the way that the screen clears completely (except for the wallpaper) for about ten seconds after you remove a USB stick by using "right-click, eject" on the relevant icon. Is anyone else experiencing this?

---

### Post by arpanaut on 2011-08-15
This is disgusting!

[ATTACH]200116[/ATTACH]

I have no green in my desktop or my theme,I never use the BFB, where are my lenses? 
This does not work for me at all, Plus I've lost transparency on the top panel, YUCK!
Ah well, back to Natty 'till things improve.
One step forward, two steps backwards... lame and ugly.

EDIT
[ATTACH]200118[/ATTACH]

On second login,  Still uglier than cow flop.

---

### Post by kaldor on 2011-08-16
The more I look at it, the more Unity looks out of place in Oneiric.

Why won't they address truly valid usability issues (hiding menus!) instead of toying around with these things?

---

### Post by lucazade on 2011-08-16
> **kaldor said:**
> The more I look at it, the more Unity looks out of place in Oneiric.

Why won't they address truly valid usability issues (hiding menus!) instead of toying around with these things?

I don't see any problem about global menu and its autohide feature, it is visible and usable only when you really need it and it allows to remove a lot clutter for the top panel.
(this way it worked also on Amiga more than a decade ago and it was brilliant).

It should be considered also that the final iteration of Unity will be available in the next LTS and not 11.10, so it might look out of place for you in Oneiric because it is an unfinished product (to me it is alredy a good shell, far better than competitors)

---

### Post by grahammechanical on 2011-08-16
As for developers reading these forums, I would forget it. They must be very busy developing. And this is the Ubuntu Forum Community and not the Ubuntu Community Forum. There is a difference. Besides, decisions on how to develop Ubuntu and what to develop it into have already been taken. The path has been set. We are testing a development release after all. I expect things not to work.

Regards.

---

### Post by x-shaney-x on 2011-08-16
One silly thing I keep seeing mentioned is that "usability studies" suggest that people didn't realise that the dash button was a button at all because it wasn't made obvious.

So instead of MAKING it more obvious they move it to the app launcher?
That may well make it more obvious but why not just make the original button more obvious.
I have suggested a "pizza shape" style button in the corner with the panel and launcher coming out of it but something as simple as putting a slight orange glow around the button, either all the time or when the mouse was in the area.

It seems even more ridiculous when you think of the little blue triangle that appears in the top corner when an app on the launcher is seeking attention.
I only found out what that was yesterday, I assumed it was some kind of glitch to do with the messaging menu.

If people aren't going to realise a an ubuntu badge in the corner is a button how on earth are they going to know what a little blue triangle is?

Anyone coming from either windows or mac would probably try the ubuntu badge anyway because they know the apple logo does something on a mac and the windows logo does something on windows.
Anyone who hasn't tried any OS before is likely to press anything they see anyway.

I wonder who are the test subjects for these "usability studies" anyway, goldfish?

<EDIT>
I just did a simple "usability study" of my own.
My missus has very basic computer skills (she can use a web browser) and has never seen unity so I sat her in front of my laptop (running Natty with the dash button in the old location) and told her to start the word processor.

She instantly moved the mouse to the dash logo and clicked it, saw the dash for the first time ever and immediately started typing "word processor" in the search.
So like I said, who on earth are these test subjects?

---

### Post by cariboo on 2011-08-16
/me wonders if moving the BFB to the launcher is in preparation for making the launcher movable, despite what the bug report says. :)

---

### Post by cariboo on 2011-08-16
Merged two threads on the same subject.

---

### Post by sgage on 2011-08-16
> **lucazade said:**
> I don't see any problem about global menu and its autohide feature, it is visible and usable only when you really need it and it allows to remove a lot clutter for the top panel.
(this way it worked also on Amiga more than a decade ago and it was brilliant).

It should be considered also that the final iteration of Unity will be available in the next LTS and not 11.10, so it might look out of place for you in Oneiric because it is an unfinished product (to me it is alredy a good shell, far better than competitors)

I do see a problem with the global menu disappearing - you can't just fly your mouse up to a menu - you first have to get up to the panel, make the menu visible, and then find the menu item that you need. To me it is absurdly anti-ergonomic behavior. Why? Why? What function does it serve to have the menu disappear?

Removing a lot of clutter? It's not clutter, it's how you operate the program! 

Of course, I'm not crazy about global menus anyway. :KS

---

### Post by fjgaude on 2011-08-16
> **cariboo907 said:**
> /me wonders if moving the BFB to the launcher is in preparation for making the launcher movable, despite what the bug report says. :)

I must say, movable... I wonder if I would ever change it from the left side of the screen? I don't like Apple stuff anyway but I respect those who do. <smile>

Unity is close to being perfect for me, so I'll just wait and see how it evolves. My mini 10-incher likes it already!

---

### Post by x-shaney-x on 2011-08-16
> **sgage said:**
> I do see a problem with the global menu disappearing - you can't just fly your mouse up to a menu - you first have to get up to the panel, make the menu visible, and then find the menu item that you need. 

Well the menu appears instantly when the mouse is at the menubar so I don't see THAT as an issue.
I just think it looks naff for one and another issue I have is if I have a web browser open maximized (as I always do) with several tabs open, if you are moving the mouse along to select a tab, the mouse pointer is moving on and off the panel as you move across.
This gives a very annoying and distracting "flickering" of the window menu as it hides and shows.

Adding a time element to the menu appearing would solve that but be even worse when you WANT to use the menu and have to wait that fraction for it to appear.

To me, they need to choose one way or the other, either have the menu there and showing all the time or put it back on the windows.

---

### Post by sgage on 2011-08-16
> **x-shaney-x said:**
> Well the menu appears instantly when the mouse is at the menubar so I don't see THAT as an issue.
I just think it looks naff for one and another issue I have is if I have a web browser open maximized (as I always do) with several tabs open, if you are moving the mouse along to select a tab, the mouse pointer is moving on and off the panel as you move across.
This gives a very annoying and distracting "flickering" of the window menu as it hides and shows.

Adding a time element to the menu appearing would solve that but be even worse when you WANT to use the menu and have to wait that fraction for it to appear.

To me, they need to choose one way or the other, either have the menu there and showing all the time or put it back on the windows.

It doesn't matter how instantly the menu shows up - the point is that you can't see where to go with the mouse until you're there and make it visible! Then you slide over to where you want to go. Rather than just going straight to it. To me it is a brain-dead bit of UI "design", anti-ergonomic, and distracting.

And it does look naff.

Unless you have a tiny screen, global menus seem to me to not really be helpful.

---

### Post by x-shaney-x on 2011-08-16
I see what you mean now about the menus.  I hadn't noticed it as a problem but looking at the menu for the gimp I can see that being troublesome :)

---

### Post by sgage on 2011-08-16
> **x-shaney-x said:**
> I see what you mean now about the menus.  I hadn't noticed it as a problem but looking at the menu for the gimp I can see that being troublesome :)

Maybe someday there will be an option to make the global menus persistent for the active window. In any case, it's easy enough for now to remove the global menus for Firefox and Thunderbird, or even altogether.

---

### Post by lucazade on 2011-08-16
@sgage
the menu appears when you reach it with the mouse with no delay and it works the same way of a dock with autohide. The functions of menu are available only when you need it.
Dunno.. sincerly i don't see the problem but I understand that for others could be an issue.
As usual an option to switch behavior could solve this kind of things.

---

### Post by sgage on 2011-08-16
> **lucazade said:**
> @sgage
the menu appears when you reach it with the mouse with no delay and it works the same way of a dock with autohide. The functions of menu are available only when you need it.
Dunno.. sincerly i don't see the problem but I understand that for others could be an issue.
As usual an option to switch behavior could solve this kind of things.

Again, it does not matter now quickly the menu is revealed - the point is that you have to put your mouse up there before it is, and THEN locate the item you want. As opposed to seeing it up there and just going straight to it. It is anti-ergonomic and disruptive of the workflow. It should absolutely be an option, IMO.

But then again, what do I know -  I think global menus are absurd  ;)

---

### Post by lucazade on 2011-08-16
> **sgage said:**
> Again, it does not matter now quickly the menu is revealed - the point is that you have to put your mouse up there before it is, and THEN locate the item you want. As opposed to seeing it up there and just going straight to it. It is anti-ergonomic and disruptive of the workflow. It should absolutely be an option, IMO.

But then again, what do I know -  I think global menus are absurd  ;)

again?
it is my opinion, am i entitled to have one?
how much often do you use the menu? I use it rarely so i (again) don't see any drawback.

---

### Post by sgage on 2011-08-16
> **lucazade said:**
> again?
it is my opinion, am i entitled to have one?
how much often do you use the menu? I use it rarely so i (again) don't see any drawback.

Well, that settles it then. You don't see any drawback, so there isn't any drawback - case closed.

I said "again" because I had just explained why I felt it was a problem a couple of messages up thread, which perhaps you didn't see.

And where did anyone say that you weren't entitled to your opinion? I was simply stating mine. Am I not entitled to it? Or is disagreeing with you not allowed? :KS  

YOU use menus so rarely that YOU don't see any drawback. I and others DO. We all work differently, and it would be nice if the UI didn't force everyone to work the same way.

---

### Post by kaldor on 2011-08-16
> **sgage said:**
> I do see a problem with the global menu disappearing - you can't just fly your mouse up to a menu - you first have to get up to the panel, make the menu visible, and then find the menu item that you need. To me it is absurdly anti-ergonomic behavior. Why? Why? What function does it serve to have the menu disappear?

Removing a lot of clutter? It's not clutter, it's how you operate the program! 

Of course, I'm not crazy about global menus anyway. :KS

+&#8734;

Plus, with multiple monitors. Where do I aim my cursor?!

It's highly anti-ergonomic and is nothing more than sacrificing functionality for appearance; a huge issue.

Again, I need to say I'm not slagging Unity. It's a great shell and a great idea, but I am amazed at the downright stupid or weird changes/features that are being made without taking usability or feedback into it.

Edit: And now, we're cluttering up the Ubuntu button with stuff the lenses used to take care of. The Windows Start menu is a huge UI nightmare in itself, and I don't want to see a cluttered and confusing Ubuntu/BFB menu either.

Edit 2: Another argument against the use of a hiding menu is that I commonly select something instead of grabbing the window border. For example, if I want to unmaximize a window, I will grab the top bar and drag it. This often results in opening a menu or unwanted window due to the fact the appmenu suddenly appears. To make it worse, it varies depending on the program, meaning there's no clear way to find out where the appmenu is.

---

### Post by ranch hand on 2011-08-17
> **sgage said:**
> Well, that settles it then. You don't see any drawback, so there isn't any drawback - case closed.

I said "again" because I had just explained why I felt it was a problem a couple of messages up thread, which perhaps you didn't see.

And where did anyone say that you weren't entitled to your opinion? I was simply stating mine. Am I not entitled to it? Or is disagreeing with you not allowed? :KS  

YOU use menus so rarely that YOU don't see any drawback. I and others DO. We all work differently, and it would be nice if the UI didn't force everyone to work the same way.
Well at least the question of where the thought police are is answered.

---

### Post by lucazade on 2011-08-17
> **sgage said:**
> Well, that settles it then. You don't see any drawback, so there isn't any drawback - case closed.

Tell me where I said "case closed"? No where.

Functions that are not always used can be hidden and revelead when necessary, like a dock with autohide or the global menu on the panel. 
There is no design issue or workflow broken as you stated to support your opinion, if it works it works and this is for ME.

> I said "again" because I had just explained why I felt it was a problem a couple of messages up thread, which perhaps you didn't see.

I was answering to your first quote to my message. I think I'm allowed to answer to you and "again"  is quite superfluous.

> And where did anyone say that you weren't entitled to your opinion? I was simply stating mine. Am I not entitled to it? Or is disagreeing with you not allowed? :KS  

YOU use menus so rarely that YOU don't see any drawback. I and others DO. We all work differently, and it would be nice if the UI didn't force everyone to work the same way.

Yes, I use the menu rarely and for this reason I don't have problem with a global menu like the one of unity and I never said this is the way for everyone (like you tried to meant).

@ranch hand
no police in the yard.

---

### Post by sgage on 2011-08-17
> **lucazade said:**
> Tell me where I said "case closed"? No where.

Functions that are not always used can be hidden and revelead when necessary, like a dock with autohide or the global menu on the panel. 
There is no design issue or workflow broken as you stated to support your opinion, if it works it works and this is for ME.



I was answering to your first quote to my message. I think I'm allowed to answer to you and "again"  is quite superfluous.



Yes, I use the menu rarely and for this reason I don't have problem with a global menu like the one of unity and I never said this is the way for everyone (like you tried to meant).

@ranch hand
no police in the yard.

The "again" was not superfluous, nor aggressive, nor anything else, and I really don't understand your issue with it. It was a perfectly reasonable use of the word in the context of the thread.

As to the rest, I think you're being overly sensitive. I was exaggerating for effect, and perhaps being a little sarcastic, and if you took it wrong, well, I'm sorry.

The real point I (and several others) have been trying to make is that a lot of the time when folks on this forum point out very real issues that they're having with a feature or the interface, someone answers that it works for them, so what's the problem?  This is not addressing the issue, and gets a bit frustrating sometimes.

---

### Post by lucazade on 2011-08-17
@sgage
now that our position are clear and we haven't changed them we can continue to test oneiric. have a good day ;)

---

### Post by sgage on 2011-08-17
> **lucazade said:**
> @sgage
now that our position are clear and we haven't changed them we can continue to test oneiric. have a good day ;)

An excellent plan, my friend! :KS

---

### Post by dsfitzpat on 2011-08-22
Umm... if the global menu is a problem, why not just revert back?
sudo apt-get remove indicator-appmenu and the global menu is gone.
Isn't that an option for those who don't like it?  I see so many people complaining about the global menu, and as often as not, nobody suggests this, so I thought there must be some problem with doing so. 
I tried removing it and so far don't see any issues - I have menus in all my application windows and no global menu.
I guess one downside is that you lose the menu associated to the desktop.
So yeah, in summary - it's not mandatory!

---

### Post by lucazade on 2011-08-22
> **dsfitzpat said:**
> Umm... if the global menu is a problem, why not just revert back?
sudo apt-get remove indicator-appmenu and the global menu is gone.
Isn't that an option for those who don't like it?  I see so many people complaining about the global menu, and as often as not, nobody suggests this, so I thought there must be some problem with doing so. 
I tried removing it and so far don't see any issues - I have menus in all my application windows and no global menu.
I guess one downside is that you lose the menu associated to the desktop.
So yeah, in summary - it's not mandatory!

More or less a week ago Mark said in his blog about globalmenu hidden by default:
"Yes, the hidden menu is suboptimal for now. We’re working towards something better."
[http://www.markshuttleworth.com/archives/717#comment-364719](http://www.markshuttleworth.com/archives/717#comment-364719)

so things might improve for the happiness of some!

---

### Post by dsfitzpat on 2011-08-22
To be clear, I should point out that I use the global menu - I'm actually quite happy with Unity.  I'd like a bit more customisation, but then on the other hand, I haven't felt the need to change much from the default setup.

In past years after a new Ubuntu install I'd spend an hour or so fiddling with appearance settings, installing a dock, new icon themes, etc.  In Unity, aside from changing the programs on the launcher - dropping Office, adding a TeX editor and some games - I only made three changes: replacing the Bluetooth manager with Blueman (the default won't pair with my remote for some reason), whitelisting all programs for the notification area, and reverting the update manager to the old behaviour, using a notification icon.
Ubuntu continues to work for me and I'm hopeful that it'll continue to get better.

---

### Post by Rasa1111 on 2011-08-22
Just glad Ive been learning to love gnome shell. lol ;)

---

### Post by CaptainMark on 2011-08-23
im still confused as the whether im running gnome shell or not, i have unity 3d & 2d installed and nothing else but am i right in thinking unity is some sort of skin running over gnome shell underneath, i still see the gnome3 style menu when you go to log back in after locking the screen

---

### Post by Noz3001 on 2011-08-23
> **CaptainMark said:**
> im still confused as the whether im running gnome shell or not, i have unity 3d & 2d installed and nothing else but am i right in thinking unity is some sort of skin running over gnome shell underneath, i still see the gnome3 style menu when you go to log back in after locking the screen

Unity is the same thing as gnome-shell, a shell running over GNOME 3

---

### Post by CaptainMark on 2011-08-23
i see so i had the right idea but i had the names backwards, gnome3 is the background system and gnome-shell is the visual part of it

---

### Post by dsfitzpat on 2011-08-23
Yeah - if you want to see the difference in appearance/behaviour, you can install the gnome-shell package and then select Gnome at the login prompt.

---

### Post by CaptainMark on 2011-08-23
no i have used the gnome shell, i cant stand it, i just got confused with the shell and gnome3 and didnt realise unity is running over gnome3

---

### Post by mc4man on 2011-08-25
The best solution here to get a usable dash (unity-4.10) is to use the 'static blur' option
When doing so, -  whatever is 'seen' on the desktop when **1st**. opening dash is what will be used for the rest of the session

So definitely don't open dash for the 1st. time over an inappropriate window like nautilus, either do over just the desktop or choose a window/background that gives the best blur effect
(haven't found what's best here yet, may just choose a plain dark desktop to create the 'snapshot' then go back to normal

Too bad one can't save the 'static' across sessions

---

### Post by arpanaut on 2011-08-25
> **mc4man said:**
> 

Too bad one can't save the 'static' across sessions

Too bad one cannot set a single theme for the dash, I'm partial to the one in Natty
I think that this color picking scheme is hideous...
It has yet to pick a color that I find appealing, and has never picked an actual true color from any background I have tried.

the way it grabs the launcher and top panel is just plain ugly.

(mc4man, yes I have me-tooed your bugs on these issues.)

Edit: At least they got rid of that big Red icon on the BFB, yay

---

### Post by mc4man on 2011-08-25
> **arpanaut said:**
> Too bad one cannot set a single theme for the dash, I'm partial to the one in Natty

Same here - I'd just as soon have 1 dash with a dark background or smoked glass effect
Overall could care less about a 'look' for the dash, i'm opening it to use it, not look at or thru  'effects'

What has just broken completely is the 0.00 opacity in the unity panel - before if you set blur to none it would work
Would be nice if 'blur=none' just gives a simple, dark dash like natty or unity-2d, & allows a trans unity panel if desired.

---

### Post by arpanaut on 2011-08-25
> **mc4man said:**
> Same here - I'd just as soon have 1 dash with a dark background or smoked glass effect
Overall could care less about a 'look' for the dash, i'm opening it to use it, not look at or thru  'effects'

What has just broken completely is the 0.00 opacity in the unity panel - before if you set blur to none it would work
Would be nice if 'blur=none' just gives a simple, dark dash like natty or unity-2d, & allows a trans unity panel if desired.

I'm with you on all of that, brother.
Sometimes all these changes are painful.

Alas, My name is John, and I am a testing junkie.

---

### Post by dsfitzpat on 2011-08-25
Oh man... I assumed when I started seeing the dash come up bright orange or yellow (and therefore almost unreadable) that this was some bug due to running it in VirtualBox and not having full display capabilities.  These last few comments have me worried that this is on purpose!
How does one go about turning off this 'feature'?

---

### Post by arpanaut on 2011-08-25
> How does one go about turning off this 'feature'?

No offense towards anyone or anything, but

ROFLMAO

---

### Post by dsfitzpat on 2011-08-25
OK, I went back and found the links to the bug reports from earlier in the thread, and I'll add my 'me too' to them.  As long as the most likely background for the dash is an eye-searingly-bright shade of Gatorade orange (or even worse, fluorescent yellow, which I've also had), the dash is basically broken for me - I'm not willing to submit my retinas to that sort of abuse.
I'm assuming they've realised that this doesn't work and we'll see an adjustment before the final release.  I'll see what I can change in CCSM to make this go away in the meantime.

---

### Post by Curnel_D on 2011-08-26
Well, we've hit UI lock, and all the asinine UI choices they've made are stuck.  If this is really what the 11.10 release will look like, I'll be using gnome-shell.

---

### Post by Sashin on 2011-08-26
Bugs can still be fixed between now and final release. Those alone may have a significant impact on your perception of Unity's user experience. For example the problems with the dash are probably a bug.

---

### Post by dsfitzpat on 2011-08-26
I expect we'll see changes since for some people (esp. those with light-coloured backgrounds) the dash is completely unreadable (whereas in my case, I can read it, but it makes me want to vomit).  There are a couple of related bugs on Launchpad marked high priority.

---

### Post by zekopeko on 2011-08-26
I'm loving the frosted glass look.

---

### Post by pelle.k on 2011-08-26
> **Curnel_D said:**
> Well, we've hit UI lock, and all the asinine UI choices they've made are stuck.  If this is really what the 11.10 release will look like, I'll be using gnome-shell.

IMHO, oneiric is gonna be a troublesome release how ever you look at it. Strange design choices with unity (and lack of customization options), the whole userland (and it's familiar configuration tools) of gnome2 ripped out and replaced with gnome3's userland which is also lacking a lot from gnome2. So even if you decide to run gnome-shell in oneiric, it's not gonna be a smooth ride. Mutter lacks for example the smart window placement of compiz and old metacity, now it *only* cascades windows :/ I could add a lot to that list, but suffice it to say gnome-shell/gnome3 is pretty feature incomplete ATM.

---

### Post by Mesanna on 2011-08-26
What's going on with the Music icon on the dash? Is there something you have to do to make that work?

I keep all my music in the Music folder, and everything is correctly tagged with ID3 tags except, for various reasons, I've never bothered with music genres. Do you need to have genres for the search feature to work, or is it just not working at all right now? I tried searching for a song and an artist, but nothing is returned.

Just as I was typing this, it occurred to me that I do have release dates in the tags (i.e. the year), but searching by decade doesn't return anything either. I guess it is just broken at the moment? Or, maybe, is it just my setup that's broken?

---

### Post by mc4man on 2011-08-26
The music lens is tied to banshee - have you imported your music into banshee?

---

### Post by Mesanna on 2011-08-26
Ah, that's the problem! I use Exaile as my default player. 

I imported my music into Banshee, and it does appear in the Dash now, so thanks for that tip, but I doubt I'll use this feature since clicking on any song opens Banshee, despite me having Exaile set as the default player. 

Does anyone know if it's possible to change this behaviour and make a different media player open? It's not a huge deal if it can't be changed, as I can just navigate via folders, but it is a little annoying to have these choices forced on us :(

---

### Post by pelle.k on 2011-08-26
> **mc4man said:**
> The music lens is tied to banshee - have you imported your music into banshee?

For real!? These kind of features should be tied to the file system and not an application IMHO. That smells too much of itunes library business to me. :/

> **Mesanna said:**
> It's not a huge deal if it can't be changed, as I can just navigate via folders, but it is a little annoying to have these choices forced on us :(

Agreed!

---

### Post by mc4man on 2011-08-26
> **Mesanna said:**
> 
Does anyone know if it's possible to change this behaviour and make a different media player open? It's not a huge deal if it can't be changed, as I can just navigate via folders, but it is a little annoying to have these choices forced on us :(
I don´t believe you can w/ that lens, it&#347; designed for banshee. I gather someone could create another music type lens, player specific or otherwise?

---

### Post by Mesanna on 2011-08-26
> **pelle.k said:**
> For real!? These kind of features should be tied to the file system and not an application IMHO. That smells too much of itunes library business to me. :/


This was my feeling exactly. It reeks of wanting Apple-like control over a user's system, which - to me - is the opposite of what Ubuntu should be about. I shouldn't lose features of an operating system because I chose Program B over Program A. But, I'm trying not be too judgemental, as this is still a very new feature and may possibly be updated in the future (though I'm not sure I really believe that, as surely it would have been simpler to build integration with the user's default player from start).

---

### Post by Mesanna on 2011-08-26
> **mc4man said:**
> I don´t believe you can w/ that lens, it&#347; designed for banshee. I gather someone could create another music type lens, player specific or otherwise?

OK, thanks. I'm still getting to grips with how these lenses work. Maybe the Exaile folks will push out something at some point in the future.

---

### Post by dsfitzpat on 2011-08-26
I've always searched for music from within my music player, and I expect I'll continue to do so.  For me, Banshee is lacking in some pretty basic functionality; namely, the ability to sort music by more than just artist/album.  I've got a lot of music over many genres, so at the very least there has to be a genre tag for me to use it.  (The best right now is Clementine, which allows completely custom shorting.  The only downside is that it uses 5x the resources of Rhythmbox.)

---

### Post by step21 on 2011-08-27
file system search = slow. So it does make sense to just search the database of one or more players that already did all the indexing.

---

### Post by pelle.k on 2011-08-27
> **step21 said:**
> file system search = slow. So it does make sense to just search the database of one or more players that already did all the indexing.
But that's the lazy (and in many ways limiting) way of implementing this feature. The lens should preferably (and perhaps optionally) do _file system level indexing_, so that you have the best of both worlds.

---

### Post by Curnel_D on 2011-08-27
> **Sashin said:**
> Bugs can still be fixed between now and final release. Those alone may have a significant impact on your perception of Unity's user experience. For example the problems with the dash are probably a bug.

Nah, all of my problems with the dash and unity overall with this release stems from UI regression.  With every change, things become less and less intuitive.

---

### Post by Sashin on 2011-08-27
> **Curnel_D said:**
> Nah, all of my problems with the dash and unity overall with this release stems from UI regression.  With every change, things become less and less intuitive.

List them, and explain why they are regressions.

---

### Post by nrundy on 2011-08-27
I like the changes that have been made. Dash, new BFB placement, indicator changes. Everything is smart improvements IMHO.

The new monochrome icons that are in Thunderbird and USC are great!

I hope these Monochrome icons also get implemented in Firefox, Gwibber, Nautilus, etc. I don't like the current "colored" icons that exist in Nautilus, Gwibber, Firefox, etc.

---

### Post by Curnel_D on 2011-08-28
> **Sashin said:**
> List them, and explain why they are regressions.
It's 1 in the morning, so I won't bother listing them.  There are quite a few.  And IMO the BFB placement and the new user menu are my two biggest pet peaves atm.  

But overall, there have been quite a few changes to the user UI for this release.  And every single one of them seem to have been made contrary to user choice.  

Sure, for instance the guy above me likes the new BFB placement.  And that's awesome.  But I think it's stupid.  IMO it breaks UI 'unity' for no other reason than 'change'.  But where as, even with something like Windows (lol), I can still make the windows UI look nearly identical in looks and function to win98/2k UI with little more than a few button clicks.  But with each unity release, it becomes less and less about my choice, the way "I" want it to look, and more and more about how some designer wants it to look.

Less user choice = regression

---

### Post by cariboo on 2011-08-28
> **Curnel_D said:**
> It's 1 in the morning, so I won't bother listing them.  There are quite a few.  And IMO the BFB placement and the new user menu are my two biggest pet peaves atm.  

But overall, there have been quite a few changes to the user UI for this release.  And every single one of them seem to have been made contrary to user choice.  

Sure, for instance the guy above me likes the new BFB placement.  And that's awesome.  But I think it's stupid.  IMO it breaks UI 'unity' for no other reason than 'change'.  But where as, even with something like Windows (lol), I can still make the windows UI look nearly identical in looks and function to win98/2k UI with little more than a few button clicks.  But with each unity release, it becomes less and less about my choice, the way "I" want it to look, and more and more about how some designer wants it to look.

Less user choice = regression

I suggest you subscribe to the [Ayatna mailing list]("https://launchpad.net/~ayatana"), you'll see that these latest changes may not make it through to the next version.

---

### Post by step21 on 2011-08-28
> **pelle.k said:**
> But that's the lazy (and in many ways limiting) way of implementing this feature. The lens should preferably (and perhaps optionally) do _file system level indexing_, so that you have the best of both worlds.

Sure, there can always be better/additional ways. However in case I'm using a player with an index already, I'd rather have my system use that instead of indexing everything all over again. So it should be optional.

---

### Post by mc4man on 2011-08-31
The [bug on the design]("https://bugs.launchpad.net/ayatana-design/+bug/824916") of the new dash in regards to the blurs, which started focusing too much on text readability,  has gotten a new 'design decision'. Those interested can see here  - 
[turning a sows ear to silk purse]("https://bugs.launchpad.net/ayatana-design/+bug/837993")

---

