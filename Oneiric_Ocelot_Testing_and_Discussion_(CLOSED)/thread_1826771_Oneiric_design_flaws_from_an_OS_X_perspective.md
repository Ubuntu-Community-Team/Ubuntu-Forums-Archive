---
title: "Oneiric design flaws from an OS X perspective"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VirtualOzelot on 2011-08-17
Since Oneiric has hit feature freeze and people are already taking turns ventilating their frustration, this post might be superfluos, but here goes anyway. 

As a long time Linux user gone over to the dark side (OS X), I still love keeping an eye on the development in the open source community. Last month I decided to download Natty and give it a go in Virtualbox. At first I was put off by Unity, but then I saw it's potential and was curious to see in what direction it was moving. So I downloaded Oneiric.

Having played around with it for a while now, I noticed some things that I think needs more attention from the Canonical Design Team. While some things are really great, and other things are OK or even good, there are obviously quite a few things that are not so good or even really bad. And then there are outright design flaws. The things I bring up in this post more or less apply to the last category.

From my perspective I think many of these design flaws could be easily remedied by taking a look at how OS X is doing things. Now, before you say anything, I totally agree that good interface design doesn't have to be synonymous with stealing Apple concepts. However I find there is a difference between addressing a usability issue in your own way, and not addressing it at all. Ubuntu and it's desktop environment Unity is quickly approaching the time and place where it could be described as "the third OS", next to Windows and OS X. In some regards however, the level of ambition seems to be a bit low. In this post I will point out a few ways in which I believe the user experience could be quite enhanced by simple means, even if it means "stealing" from OS X.

First of all, Nautilus. As many have pointed out, the sidebar currently looks more or less like a glitch in the rendering software. I'm sorry Unity devs, but it's simply inconsistent with the overall look and feel of your desktop. Applying OS X logic to this application, it might look something like this: (Before and after shot)

[IMG]http://www.bolotin.se/oneiricflaws/nautilus-comparison.jpg[/IMG]

In OS X, if the toolkit of an application is embedded in the window title bar then it's always the same width as that title bar. Otherwise, it's not embedded in the title bar at all. This works well in OS X since both the title bar and the application is drawn in different shades of gray. In Ubuntu, there is more of a contrast between the title bar and application colors. As a result, the contrast between applications with and applications without a title bar-embedded toolkit is a greater one, and I think developers should be aware of that. It does give a slightly inconsistent feel, especially when key applications like Banshee doesn't adhere to the basic aesthetics of the OS.

Next, the menubar. This is a real no-brainer. I don't think I've ever heard anyone say they like the way the menubar currently works, hiding until you blindly point the cursor in it's general direction. The solution is as simple as it is genius, and has been pointed out in the forums many times. Just keep the bloody thing visible all of the time, without exception.

[IMG]http://www.bolotin.se/oneiricflaws/menubar-comparison.jpg[/IMG]

The only logical reason for the current behavior that I can think of is that it saves precious space on your Netbook, which is after all the original Unity user case. The fact that Unity is developed with the Netbook in mind accounts for many of it's strengths in my opinion, but also quite a few of it's weaknesses. I believe that somehow in the way that Unity configures itself it should make an informed decision about these things. For example, check the current resolution. Is it bigger than 800x600? Don't bother with the menu bar hiding stuff!

When it comes to the button for launching the dash, I think Natty really had it down. As some have pointed out, the new dash launcher is a big set back for long term efficiency since it's no longer in the top-left corner of the screen. You shouldn't even have to consult Fitt's law to see that this is true - it's just common sense. Also, the new dash button takes up a lot of unnecessary space in the launcher, which gets crowded pretty fast as it is. Finally, the empty space left in the top bar above the launcher when no program is running looks really, really bad.

I read somewhere that the reason for this design choice was that some users had trouble finding the dash menu, instinctively looking at the launcher instead of the top bar. Well yes, but that really isn't a problem with the top bar as much as the launcher, is it? Try changing the icon theme to Faenza and setting the launcher icon size to 32x32 and you'll see what I mean. There's like five or six different colors there in the default setup, and big childish icons constantly gunning for your attention. No wonder some people couldn't distinguish the tiny, elegant black and white dash icon from the launcher when the launcher itself is a myriad of contrasts.

Again, you could argue that the big intense icons in the launcher is a good design choice for a Netbook environment. I disagree. 32x32 is plenty on a 800x600 resolution. Instead I think you should make two different sets of icons. For the netbook, something along the lines of [Meego]("https://meego.com/devices/netbook/netbook-screenshots") - high contrast, elegant, minimalistic. For the desktop, go with Faenza. It's a beautiful and mature icon set that already is consistent with the squared layout of the launcher buttons. 

As for the notifiers, this is one of my favorite features in Unity. And since the concept's already borrowed from OS X, why not implement it all the way?

[IMG]http://www.bolotin.se/oneiricflaws/notifier-comparison.jpg[/IMG]

Currently, drop down menus are positioned the same way for notifiers and menubar items. In OS X, the drop down menus are aligned in two different ways. For menu items, the left edge of the drop down menu is aligned with the left edge of the menu item. Submenus are placed to the right of the main drop down menu. For notifiers, the right edge of the drop down menu is aligned with the right edge of the notifier. Submenus are placed to the left of the main drop down menu. In Ubuntu, all drop downs are treated according to the menubar model. This practically means that for notifiers, all drop downs share the same position, pressed against the right edge of the screen. 

In OS X, the notifier icon gets properly highlighted with the system-wide "selected" color when pressed. Coupled with the right-to-left-positioning scheme described above you get a very good sense which notifier the drop down menu belongs to. The mockup above illustrates how this would look on Ubuntu, with OS X rounded menu corners as a bonus treat. :-)

Finally, there is a lot of unnecessary clutter in both the dash and Ubuntu Software Center. Any starter that isn't logically a program from the user's perspective should be taken out of the dash. This includes system settings, shortcuts to the file system, help pages etc. (For the inexperienced user, "Keyboard" isn't a program, it's a keyboard. In a system configuration context it might mean "Configure the keyboard," but in a program menu it means absolutely nothing.) If you look at the OS X Program menu you see only objects that activates the user in some way. This, I believe, is the layman's association to the word "computer program": something that will put me to work in some way, be it with disk partitioning or 3D rendering.

[IMG]http://www.bolotin.se/oneiricflaws/dash-clutter-small.jpg[/IMG]

A greater challenge would probably be cleaning up USC. Clicking my way to Developer Tools -> Python, I get a list of objects most of which have very little to do with python programming. In fact, most of them seem to be relevant only in so far as they are applications written in python, or extendible by optional python bindings.

[IMG]http://www.bolotin.se/oneiricflaws/software-center-clutter.jpg[/IMG]

As a python developer, I would probably be more interested in the 1516 technical items that are hidden from me by default. The only problem is that when I click on the link in the bottom of the window I am presented with a brutally unsorted list and end up having to search for the package manually anyway. This makes me sad since this is such a gorgeous and well designed program in Oneiric. I don't know if it is meant to be a serious alternative to APT on the cli for the advanced user. I think it should definitely have that ambition, but right now it just doesn't cut it.

Perhaps Ubuntu needs to change it's release schedule if the amazing and inspiring changes it is attempting really can get a chance to mature? I'm not sure. From where I'm standing, it's still the most complete and most intuitive non-techie operating system in the open source world. As an OS X user on the other hand, I guess I feel I'm entitled to some elitism when it comes to interface design. ;)

Sure someone disagrees with me. If so, feel free to tell me.

Cheers,
/M

---

### Post by zekopeko on 2011-08-17
Completely agree. Non-rounded menus are jarring to look at and with your left-aligned,highlighted suggestion they look GREAT!

BTW the funny part about global menu is that the person who designed the spec actually complained on Ayatana mailing list that the current implementations wasn't how he designed it.

---

### Post by kaldor on 2011-08-17
[img]http://www.bolotin.se/oneiricflaws/menubar-comparison.jpg[/img]

This. And have it always shown.

---

### Post by lucazade on 2011-08-17
@VirtualOzelot

There is no "OSX perspective", there are good and bad ideas.


1. Nautilus toolbar.
This is something that should be addressed to GNOME devs and not to Canonical/Ubuntu.
Yes, It's a bad toolbar also in my opinion but patching it won't solve our issue, we need a strong first implementation to be maintanable in the time.


2. If the window title is long the menu will start in the middle of the panel, which is ugly
If the menubar is *always visible* it will appear also when you are using the dash which is wrong. (look at the screenshot below)


3. really doesn't make sense to align menu that way, I don't see any advantage but only the possibility to go with the mouse in the wrong menu. anyway really minor issue.


4. agree about control panel software in the dash are strange if you navigate to search softwares but are handy if you use the search entry. i'll wait final implementation for this.


[IMG]http://i.imgur.com/Dzvc8.png[/IMG]

---

### Post by MacUntu on 2011-08-17
@1. Hit F3 and you know why it looks as ugly as it does.

---

### Post by VirtualOzelot on 2011-08-17
@lucazade:

1. I do realize that a lot of problems come from upstream. It's just that they need to be sorted out sooner or later.

2. Remember that it's not the window title but the application name that is shown. Application names are rarely that long and if they are perhaps the developer should be made aware of the many advantages of a shorter name or at least an acronym to put as the X app name. Don't really know what you mean with the reference to the screenshot here, can't see any menu bar in it. But I guess if it's very annoying to display the menubar while launching dash, just make it disappear when dash is being launched? Shouldn't be so hard to implement.

3. Compared to the other mockups, this is less bug and more wishlist. But it actually does make a big difference in the overall impression. When it comes to notifiers, Ubuntu just looks a little bit sloppy right now compared to OS X.

---

### Post by VirtualOzelot on 2011-08-17
Did a little test to see how OS X handles the menubar when run in low resolutions:

1280x800
[IMG]http://www.bolotin.se/oneiricflaws/osxmenubar1280.jpg[/IMG]

800x600
[IMG]http://www.bolotin.se/oneiricflaws/osxmenubar800.jpg[/IMG]

640x480
[IMG]http://www.bolotin.se/oneiricflaws/osxmenubar640.jpg[/IMG]

As you can see, prio nr. 1 is to let the the menubar show at all times, i.e. the opposite of what Ubuntu is doing. Space between menu items is changed, long menu item names are abbreviated. The notifier is only shown if there is space remaining right of the menu bar.

This might not be the best way to handle it, but it is one way. Apple's had the menu bar in the top bar since the eighties - perhaps we should give them the benefit of the doubt on this one?

---

### Post by lucazade on 2011-08-17
@VirtualOzelot

Yes, your guess was correct, I was referring to the lack of menubar when using the dash and your solution is valid, althought I prefer the current one.

Abbreviated menu for small screens seems good and it is probably better than Unity implementation.

---

### Post by TrueJournals on 2011-08-17
> **VirtualOzelot said:**
> [IMG]http://www.bolotin.se/oneiricflaws/nautilus-comparison.jpg[/IMG]

I kind of disagree with this, using the "address bar in the tabs" argument.  That toolbar is something that modifies your view on the right.  The view on the left affects it, and it does not affect the view on the left.  So, why should it be above the left side?  This is the same change we saw when web browsers started putting tabs above the address bar.  The address bar is affected by choice of tab... why should it be *above* the tabs?

Besides, as MacUntu pointed out, press F3 to get the side-by-side view.  Having this side-by-side view with a toolbar that extends all the way to the left would look weird.

---

### Post by MacUntu on 2011-08-17
Right, but let's agree on this, the current implementation of that bar *does* look weird. Maybe a switch back to the light colored version would fix it.

---

### Post by Merk42 on 2011-08-17
This is the sort of thing that really should be in the [Ayatana Mailing List](https://launchpad.net/~ayatana)

---

### Post by VirtualOzelot on 2011-08-17
@Macuntu, TrueJournals:

Oh yeah, forgot about that functionality. Well, this might be considered blasphemy among *nixers, but is that whole side-by-side thing really that useful? I can't remember having used it since back when I was running midnight commander in early Gnome 2... :)

But ofcourse I agree with you that in such a case the directory path buttons are specific to each pane and can not be placed directly above the side bar.

---

### Post by zekopeko on 2011-08-17
> **lucazade said:**
> @VirtualOzelot

There is no "OSX perspective", there are good and bad ideas.

Considering that he pretty much compared OSX to Unity it is a OSX perspective.

> 
2. If the window title is long the menu will start in the middle of the panel, which is ugly
If the menubar is *always visible* it will appear also when you are using the dash which is wrong. (look at the screenshot below)

Super easy fix. When the Dash is invoked the menu disappears. I hope you noticed the buttons in the upper left. Those buttons control the Dash once it is active. X closes it, square fullscreens it.

> 3. really doesn't make sense to align menu that way, I don't see any advantage but only the possibility to go with the mouse in the wrong menu. anyway really minor issue.

Lets see:

a) It is easier to see which menu item is active because of the colour.
b) It looks better.
c) It is consistent so menus always align with the menu item making it more obvious to the user what exactly is opened.


> 4. agree about control panel software in the dash are strange if you navigate to search softwares but are handy if you use the search entry. i'll wait final implementation for this.

AFAIK Apple doesn't expose items in their System Preferences to either the Finder's Applications folder or Launchpad or grid Stacks. Another OSX perspective.

---

### Post by lucazade on 2011-08-17
> **zekopeko said:**
>  Another OSX perspective.

do we need "osx perspectives" necessarily or maybe, is it better if are presented only good ideas and no matter from what are inspired of (if are they inspired at all)?

unfortunately all the things you pointed out are not improvements but personal preferences in *my perspective*, I prefer present implementations.
I haven't seen better appearance of enhanced functionalities in your points, althought i respect them and suggest you to open a bug report each, you won't see my vote, obviously, but I don't think you'll care about it. :)

---

### Post by sffvba[e0rt on 2011-08-17
All I can say is that every day the Unity interface gets better and better and with ideas like the OP's and others it is going to really become very slick :)


404

---

### Post by VirtualOzelot on 2011-08-17
Regarding the issue of directory level controls being placed above the side bar, I would like to suggest another way of looking at it. With desktops everywhere moving toward document oriented interfaces, I think the crucial question for the end user is: "Where does my document begin and where does it end?"

[IMG]http://www.bolotin.se/oneiricflaws/control-levels.jpg[/IMG]

In vintage Nautilus, on GNOME 2, you had a lot of drop down menus directly above the side bar. That didn't mean they were misinterpreted as only controlling the side bar, and I believe the same goes for buttons in the toolbar. 

Clearly distinguishing between the application and document control level of an application, by for example making the look and size of the embedded toolbar consistent with the window title bar rather than the file browser, is simply a way of assisting the end user in answering the question above.

On one hand you got one part of the program (Nautilus in this case) where the user can explore his or her file system directly using the sidebar and the icons in the file view. On this level, we need as few extra controls possible since the user understands what is going on here as a representation of how the document (in this case, his or her filesystem) actually looks.

On the other hand you got another part of the program where the user can make the application do certain actions like going back and forward, going up one level in the directory tree, searching for files, choosing the way files are going to be displayed etc. Most of this functionality is being moved to the top bar in document oriented interfaces, but some useful visual shortcuts remain for maximum efficiency. 

Finally, if the back and forward and directory tree buttons always remain in one place throughout the entire system the user will be able to retain his/her document focus, not constantly distracted by the application and where *it* chooses to place *it's* controls. You shouldn't have to go: "Oh yeah, Nautilus is capable of displaying multiple panes and therefore probably places forwards and backwards buttons contextually based on where in the window the pane is displayed." In a perfect system you shouldn't even have to reflect over where your buttons are at all.

Just my two cents.

EDIT:

As for the OS X comparisons. The way I see it, Unity is already moving toward a more document oriented way of handling things. In that regard I think OS X provides a good source of inspiration since in my opinion it's *the* document oriented desktop environment. Furthermore, a lot of features have already been borrowed from OS X and I see no harm in not reinventing the wheel when it comes to interface design. OS X isn't perfect, no environment is, but ideas are free (not really but you know what I mean) and usability should be prioritized over originality.

---

### Post by Merk42 on 2011-08-17
> **zekopeko said:**
> Considering that he pretty much compared OSX to Unity it is a OSX perspectiveI think what lucazade was saying was that we shouldn't look at Unity "from a OSX perspective", but look for good and bad ideas in Unity's current form.

---

### Post by kaldor on 2011-08-17
After re-reading the post, I think I should say that I agree 100% with everything the OP said. They're the same type of issues I've been complaining about myself.

---

