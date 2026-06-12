---
title: "Improving Unity"
date: 2011-05-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Johnsie on 2011-05-01
Now that we have got alot of feedback after the release of Unity I think it's important that we take alot  of that feedback into consideration and look for ways to improve it. 

Here are some of my suggestions:

-Create a suitable replacement for the 'Places' menu that was on the Gnome2 panel. That was a great way to easily access bookmarked shared folders without needing to go into nautilus first

-Create a replacement for the 'Applications' menu from gnome2. that quickly shows the installed apps withotu having to go full screen or type into a search box. If people don't like this idea then make it optional.


-Implement a 'show desktop' button. Alot of us like to keep shortcuts and folders on our desktops. Having a show desktop button would make that easily accessible.

---

### Post by screaminj3sus on 2011-05-01
Agreed. The home folder on the dock needs to have quicklists for places. This would be an easy way to replace the places functionality. The places lense doesn't cut it, too slow.

---

### Post by mgmiller on 2011-05-01
Well, for the first and third suggestions, they are kind of interrelated.  The Places menu is still there at the top, but it's only visible if nothing else is open on the desktop.  So try hitting the "super" + D key combo to quickly show desktop.  Then hover your mouse over the top panel to reveal the Places menu, among other things.  "Connect to server" is in the "File" drop down, rather then "Places" now.

I agree a replacement for the Applications menu would be nice.  It seems to me it took less effort to get to an app from there then by the new method.

There are some things that can be tweaked if you install compizconfig-settings-manager.  Once it's installed, look at the unity plugin and you can adjust transparency in the top panel, the size of the icons in the launcher and their appearance (back lighting) as well.  There are other things you can change also.

There is an extensive list of things you can tweak in Unity at this link:
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by mgmiller on 2011-05-01
> **screaminj3sus said:**
> Agreed. The home folder on the dock needs to have quicklists for places. This would be an easy way to replace the places functionality. The places lense doesn't cut it, too slow.


This exact fix is in the link I just posted.  It's a quick copy and paste into your terminal to implement it.

Adding the "Show Desktop" icon to the launcher as requested by the OP is also covered in the link I posted above.

Lots more neat stuff there, read through it all and have fun.

---

### Post by teachop on 2011-05-01
Movable launcher.  I may never stop banging my mouse off the bottom of the screen waiting for something to happen...

---

### Post by Rifester on 2011-05-01
It would be nice if the launcher background was the same color/transparency of the upper panel (or you had the option to change theme colors to match like AWN themes).   It looks out of place with lighter GTK themes and it bugs the crap of me.

---

### Post by RavensKrag on 2011-05-01
I'd like to see a better search system.  It'd be nice if all programs were tagged in some way, and the search could use that metadata to find programs that the user desires.  Some of this is already evident, as when you search for "photoshop," gimp shows up as a program which you can download.

It would be extra great if, in the spirit of open source, users could add on extra tags.  These new tags could then be used not only locally, but could be forwarded to some database managed by Canonical, so that all can benefit from a search experience more attuned to actual usage.

---

### Post by kyleabaker on 2011-05-01
> **screaminj3sus said:**
> Agreed. The home folder on the dock needs to have quicklists for places. This would be an easy way to replace the places functionality. The places lense doesn't cut it, too slow.

+1 The quicklist option is a nice idea and it would be consistent.

---

### Post by CreativeReach on 2011-05-02
A Quicklist would help, but i think places in the dash would be cool as well.

---

### Post by Peter09 on 2011-05-02
I like the Dash - I think its a great way to open applications, especially ones that you do not often use, similarly it should develop into and effective way of opening files. we should not water down this function, but ensure that it is developed and becomes a recognised part of unity. As with much of Unity we need to change the looks somewhat to be less clunky.

---

### Post by cariboo on 2011-05-02
I have to agree, a quicklist connected to the home icon would be great.

---

### Post by nrundy on 2011-05-02
3 things I think would make things easier for me. What are your feelings on the following?

1. when one occurrence of an app is open and focused (e.g., nautilus in launcher position 1) make tapping super + 1 or clicking on the nautilus-launcher-icon MINIMIZE the nautilus window.  On second thought maybe it's best that these actions only bring the window to the foreground. prevents it from accidentally being miimized when user is trying to bring it the foreground.

2.  being able to cycle through an app's open windows by holding super while pressing 1-9 (essentially like Windows allows). For example, say I have three nautilus windows open. and currently I'm looking at firefox. I want to go to the third nautilus window (nautilus-3). I tap super + 1 and nautilus-1 appears. I am forced to re-tap super + 1 to get "expose mode". It would be easier to just be able tap 1 twice more to bring up nautilus-3 (e.g., from viewing firefox, hold super and tap 1 three times)

3. for me, having the launcher on the left side of screen mandates using some sort of hide function. But it would be nice to be able to put the launcher on the right side of the screen and set it to never-hide.

---

### Post by Fraoch on 2011-05-02
It would be nice if Unity was more customizeable.

I'd like to remove the workspace switcher from the Launcher and a whole whack of notifications from the top bar.  Googling and checking forum posts here hasn't turned up anything so far.

My instinct was to right-click on a notification to remove it - to my surprise right-click did the same as left-click.

It would also be nice to move the top bar to the bottom.  Its name, "top bar", suggests that it's never intended to be used this way.

I'm a little surprised by the lack of flexibility in Unity.  Linux should be all about customization and flexibility.

---

### Post by CreativeReach on 2011-05-02
Being able to move the launcher would be awesome as well! But it may conflict with dash button?

---

### Post by cariboo on 2011-05-02
> **Fraoch said:**
> It would be nice if Unity was more customizeable.

I'd like to remove the workspace switcher from the Launcher and a whole whack of notifications from the top bar.  Googling and checking forum posts here hasn't turned up anything so far.

My instinct was to right-click on a notification to remove it - to my surprise right-click did the same as left-click.

It would also be nice to move the top bar to the bottom.  Its name, "top bar", suggests that it's never intended to be used this way.

I'm a little surprised by the lack of flexibility in Unity.  Linux should be all about customization and flexibility.

Moving the top panel to the bottom to make it look more Windows like, wouldn't work very well with global menus.

---

### Post by Fraoch on 2011-05-02
> **cariboo907 said:**
> Moving the top panel to the bottom to make it look more Windows like, wouldn't work very well with global menus.

Right, sorry, I didn't think of that.  I'm still getting used to Unity and I only just started noticing the global menu.  And yes, I see the point of it.

I guess I'm still in the GNOME panel mindset that I can move it, and putting it on the bottom is the old Windows mindset that I didn't even realize I still had.

---

### Post by CreativeReach on 2011-05-02
But being able to move the launcher would be great!

---

### Post by dixonstalbert on 2011-05-02
I would like to see an option to move Launcher with a dual (or triple) monitor set up.

My left monitor is much smaller and in the corner of my desk. I am getting a stiff neck looking way over to the left when I use it a lot.:(

---

### Post by CreativeReach on 2011-05-02
Simply Make it the secondary monitor instead of the first.

---

### Post by cntrational on 2011-05-03
Have a list of open windows pop up when you hover over an icon in the launcher, [similar to what Windows 7 does. ]("http://media.arstechnica.com/images/windows7/Windows%20Taskbar%20Previews.png")

The current way of switching windows is awkward. Let's say I am on Firefox and have two terminal windows minimized. If I click on the icon, *both* windows open. How do I choose which one to open?

Now, I have 5 windows of evince open. I'm reading one, and I go to Firefox. If I click on the evince icon, I get taken to a seemingly random window, instead of the one I was viewing! I have to click the icon again to go to that Mac-esque "Expose" screen. How do I go directly to the "Expose" screen?

And speaking of the "Expose" screen (whatever the official Unity name for it is), why is it the only way of switching windows? Can't I get a convenient list somewhere -- oh, like when I hover over the icon -- instead of having to go to another special view? I don't like it, at all.

The window switching system is a mess.

---

### Post by gufide on 2011-05-03
A better Launcher & menu config... 2 option when it have animation option, backlight, size...

---

### Post by mgmiller on 2011-05-03
> **gufide said:**
> A better Launcher & menu config... 2 option when it have animation option, backlight, size...

These are all configurable in the CCSM.  Look at the unity plugin.

---

### Post by fragos on 2011-05-03
"Files & Folders" gets it Favorites from the Nautilus Bookmarks -- a bit like "Places" but when one of those Favorites is an FTP link it is opened in a Browser as read only instead of in Nautilus so that it can be read write. A proper implementation of Places would have to open FTP in Nautilus.

---

### Post by cntrational on 2011-05-03
> **cntrational said:**
> Have a list of open windows pop up when you hover over an icon in the launcher, [similar to what Windows 7 does. ]("http://media.arstechnica.com/images/windows7/Windows%20Taskbar%20Previews.png")

The current way of switching windows is awkward. Let's say I am on Firefox and have two terminal windows minimized. If I click on the icon, *both* windows open. How do I choose which one to open?

Now, I have 5 windows of evince open. I'm reading one, and I go to Firefox. If I click on the evince icon, I get taken to a seemingly random window, instead of the one I was viewing! I have to click the icon again to go to that Mac-esque "Expose" screen. How do I go directly to the "Expose" screen?

And speaking of the "Expose" screen (whatever the official Unity name for it is), why is it the only way of switching windows? Can't I get a convenient list somewhere -- oh, like when I hover over the icon -- instead of having to go to another special view? I don't like it, at all.

The window switching system is a mess.One more thing (and a quote for the new page): I was looking at my Nautilus/Home icon, and I noticed that I had a window open. There was no way to check what window I had open! Was it the Downloads window, or the Documents, or the Videos, or some other folder? There was absolutely no way to check without switching. Ridiculous.

---

### Post by azupan on 2011-05-04
[LIST=1]
[*]Top Panel autohide. Puhleeeze! It's the only thing that keeps me from switching to Unity right away. OK, I know it's menu in there, but most of the people don't use menus much theese days. Microsoft Office menus have been autohidden/hidden since 2007 I think, and it works just fine.
[*]Dash customization. I don't have photos on my computer, I don't use mail, and seldomly listen to music. I'd certainly like to have shortcuts to the most frequently used apps in there instead.
[*]Keep working MT Grab Handles. I like the idea. The ideal desktop for me would be windows without titlebars & frames, and autohidden menu on the top of the screen.
[/LIST]

---

### Post by 3abdo3asal on 2011-05-04
Hey when i right click appliation that has 2 windows open it doesn't show any of them it just shows the "keep in luncher"and "quit" and don't any of u tell its there cause i tried it on unity 3d and 2d both suck ..

---

### Post by Peter09 on 2011-05-04
Yep - that’s because the command is 'double click'.

---

### Post by Peter09 on 2011-05-04
> Top Panel autohide. Puhleeeze! It's the only thing that keeps me from  switching to Unity right away. OK, I know it's menu in there, but most  of the people don't use menus much theese days. Microsoft Office menus  have been autohidden/hidden since 2007 I think, and it works just fine

I really do not get this, here is my screen shot of firefox, where is the wasted space?

---

### Post by azupan on 2011-05-04
> **Peter09 said:**
> I really do not get this, here is my screen shot of firefox, where is the wasted space?In the middle. A lot of it. Left and/or right at most of the other websites.
 
First off, excuse me for being a bit unorthodox. I installed Ubuntu about 6 months ago, and started doing serious work about 3 months ago. At the moment, I actively use Vista, Windows 7, and Ubuntu at the same time (dual... actually triple boot, so to speak).
 
Maximizing windows throughout entire desktop workspace is not the best way of utilizing space on the wide screen monitor. Placing windows stretched from top to bottom one besides another is much better, especially during web browsing. Most of the websites are designed pretty narrow. Wieved in browser without too much empty space on the sides, they fit into a little bit more than 50% of the typical screen width.
 
Windows 7 supports this arrangement very nicely. When you drag upper part of the window to the top of the screen, window maximizes only top to bottom, not to the entire screen. The width of the window remains unchanged.
 
Major new Windows applications also have their menus hidden, like Microsoft Office since 2007, Internet Explorer, and Windows Explorer (windows's Nautilus equivalent). You have to press Alt to see the menu. Very useful IMHE. Menus are clumsy, yet indispensable remnant of a distant past. They are seldomly used nowadays, therefore there's no need to be shown all the time.
 
Something similar would be very nice in Unity as well. For example, when you press Alt, MT Grab Handles appear, together with menu, wherever it might be.
 
Again: I like MT Grab Handles. Excellent idea, very useful. Placing the mouse pointer over the tiny window frame in order to grab it is simply annoying.

---

### Post by Peter09 on 2011-05-04
>  			 		 	 	 In the middle. A lot of it. Left and/or right at most of the other websites

Yes - but the point being made was that Unity does not intrude into the desktop at all.

---

### Post by azupan on 2011-05-04
> **Peter09 said:**
> Yes - but the point being made was that Unity does not intrude into the desktop at all.It does. Screenshot.jpg illustrates what I've been trying to say in my previous post. Screenshot-1.jpg is quite an eyesore. Netbeans has its own menu system (as well as plenty of other apps), its not integrated into Unity, and consequently stays where it is. When running such apps, top panel is a waste of space.

Make no mistake- I understand the idea behind the Unity top panel, and, in most cases it certainly is a good one, but... there are situations where it could be a bit intrusive.

---

### Post by Peter09 on 2011-05-04
I guess the point here is - will the majority of applications in the next year or so be using the top panel as a menu.

---

### Post by azupan on 2011-05-04
> **azupan said:**
> Again: I like MT Grab Handles. Excellent idea, very useful. Placing the mouse pointer over the tiny window frame in order to grab it is simply annoying.I'm sending a screenshot to illustrate what I've meant. There are no window frames whatsoever. A shade and/or reflection is painted around window instead. Other windows could be dimmed a bit. Menus and top panel are not displayed. When the user presses --say-- Alt,  MT Grab Handles, and menus/top panel appear. Windows are dragged and resized only by MT Grab Handles. It's far better than dragging edges, because they are hard to hit with a mouse.

---

### Post by azupan on 2011-05-04
> **Peter09 said:**
> I guess the point here is - will the majority of applications in the next year or so be using the top panel as a menu.And my point is: Majority of Windows applications have menus hidden, and the rest of them should follow their fine example. If the application menu is hidden, the top panel should be hidden also.

---

### Post by azupan on 2011-05-04
*** Back after Windows 7 reboot ***

Windows Explorer.png is a screenshot of how Windows Nautilus ... errr ... Explorer normally looks. You will notice, that there is no menu anywhere. Menu appears only when Alt is pressed (Windows Explorer Alt.png). I need this menu maybe once every 3 months, most people never.

In Microsoft Office 2010, menus are abandoned alltogether, and replaced with so called "ribbons". There was a lot of bitching when ribbons were first introduced (ribbons sucks blah blah, probably sounds familiar right now ;)), but eventually, people got used to them.

Application menus are becoming almost useless if not obsolete, justifiably so. It therefore doesn't make much sense to incorporate them into a desktop element, which is always there, which can't be hidden.

EDIT:  Chromium, for example, has no menu nor heading, and consequently no use for the top panel. I think it's reasonable to expect more applications like this.

---

### Post by ZarathustraDK on 2011-05-04
I've made a unity-mockup in [_this thread_]("http://ubuntuforums.org/showthread.php?t=1748401"), if people are interested.

Here's also a [_direct link to the full-resolution image_]("http://fc05.deviantart.net/fs70/f/2011/124/2/9/ubunty_unity_mockup_v2_by_zarathustradk-d3fkdc6.jpg") (ubuntuforums downsizes large images when they get over a certain resolution, and then you can't read the text so...)

Cheers :popcorn:

---

### Post by azupan on 2011-05-04
> **ZarathustraDK said:**
> I've made a unity-mockup in [_this thread_]("http://ubuntuforums.org/showthread.php?t=1748401"), if people are interested.

Here's also a [_direct link to the full-resolution image_]("http://fc05.deviantart.net/fs70/f/2011/124/2/9/ubunty_unity_mockup_v2_by_zarathustradk-d3fkdc6.jpg") (ubuntuforums downsizes large images when they get over a certain resolution, and then you can't read the text so...)Good job, I like it! :biggrin:

Alternative idea: Instead of "Global menu is not visible when no windows are maximized" it could be "Global menu is not visible (or auto-hidden) when it's not used by any window". Chromium, for example, has no menu at all, therefore there's no need to show global menu even if it's maximized.

---

### Post by compmodder26 on 2011-05-05
Would be nice to be able to specify which files/folders would get indexed for searching.  Unless somebody knows something I don't (which is highly likely), files only get indexed when accessed.  I would greatly prefer to have them indexed before hand.

---

### Post by donkyhotay on 2011-05-05
> **ZarathustraDK said:**
> I've made a unity-mockup in [_this thread_]("http://ubuntuforums.org/showthread.php?t=1748401"), if people are interested.

Here's also a [_direct link to the full-resolution image_]("http://fc05.deviantart.net/fs70/f/2011/124/2/9/ubunty_unity_mockup_v2_by_zarathustradk-d3fkdc6.jpg") (ubuntuforums downsizes large images when they get over a certain resolution, and then you can't read the text so...)

Cheers :popcorn:

I like that as well, especially moving plugged in devices away from the apps. One thing I'd like to see (and I've posted this in other threads but not as an improvement) is an easier way to customize the app lens. With unity the way it is I go to apps, right click for the major catagory I want (I'll use games as an example) then it displays a list of my most commonly used games, a list of about 5-10 more games listed alphabetically, then maybe some recommended games tied into the software center. My issue is that I'd like to be able to customize that screen. I can understand the way it's set now and would recommend that as a default but I'd like to be able to eliminate the recommended apps (I know what I want already) and use that space more for my installed apps. Currently if I want to use an app that I don't use often and don't feel like typing in the name I have to go to apps, select the catagory, click the drop-down to show more, scroll down to the one I want, then select it. If I could customize that so I can have it immediately show a specific listing of related apps I'd really like it. For example selecting games and then having it show a list of all my games. Having it more similar to the way ubuntu netbook edition works (or having an option to make it that way) is what I really want. Actually I would probably be content just to have my list of all installed apps as "shown" by default instead of having to select "show more" like is necessary now. If people are concerned about having space just make it use a scroll bar so people can scroll through the various catagories.

---

### Post by rg4w on 2011-05-05
> **azupan said:**
> And my point is: Majority of Windows applications have menus hidden
I don't believe I've seen Windows apps - or any apps outside of Unity - that have menus but conceal them by default.

Can you point me to some examples in Win?

---

### Post by azupan on 2011-05-05
> **rg4w said:**
> I don't believe I've seen Windows apps - or any apps outside of Unity - that have menus but conceal them by default.

Can you point me to some examples in Win?I already did, see screenshots in post #35 ([http://ubuntuforums.org/showpost.php?p=10768794&postcount=35](http://ubuntuforums.org/showpost.php?p=10768794&postcount=35) ). Windows Explorer is not the only application with menu hidden by default, but it's the first one that comes to my mind, because it's probably the most heavily used.

Then there are Google Chrome/ Chromium and Internet Explorer 9, which have menu hidden all the time. Actually, they have no menu in classical sense at all. If you want menu to pop out, you have to click a little button in the corner. Such UI design makes a lot of sense, because menu is very seldomly used. It therefore makes no sense to waste space with it in application window, let alone desktop.

If you take a look at ZarathustraDK's design you'll notice, that I'm not the only one thinking along this lines.

Now, don't get me wrong, I'm not against global menu/top panel at all- actually, I think it's very useful idea. There are a lot of apps out there, where menu is necessary, IDEs, and such. But, there is also increasing number of apps without menu, and that must be taken into account.

---

### Post by CreativeReach on 2011-05-05
Firefox 4 also has a hidden menu in windows.

---

### Post by rg4w on 2011-05-05
> **azupan said:**
> I already did, see screenshots in post #35 ([http://ubuntuforums.org/showpost.php?p=10768794&postcount=35](http://ubuntuforums.org/showpost.php?p=10768794&postcount=35) ). Windows Explorer is not the only application with menu hidden by default, but it's the first one that comes to my mind, because it's probably the most heavily used.

Then there are Google Chrome/ Chromium and Internet Explorer 9, which have menu hidden all the time. Actually, they have no menu in classical sense at all. If you want menu to pop out, you have to click a little button in the corner. Such UI design makes a lot of sense, because menu is very seldomly used. It therefore makes no sense to waste space with it in application window, let alone desktop.

If you take a look at ZarathustraDK's design you'll notice, that I'm not the only one thinking along this lines.

Now, don't get me wrong, I'm not against global menu/top panel at all- actually, I think it's very useful idea. There are a lot of apps out there, where menu is necessary, IDEs, and such. But, there is also increasing number of apps without menu, and that must be taken into account.
I think you said it very well, though initially we were looking at two different types of applications.

Yes, I followed the evolution of Ribbons at the Jensen Harris blog with great interest, and recognize that Windows is finally getting around to using Ribbons-like UIs in other apps outside of Office.

Browsers are also evolving away from menus because of their nature and the nature of menus:  menus are a means of accessing commands within an app, but on the Web most of the commands are within the page, so the app's own menus play a relatively minor role.

But as you noted, a great many apps, like IDEs, GIMP, Scribus, and others, a feature-rich applications, and for them menus play an important role; it's hard to find a more concise way to make so many commands so easily available.

That is, if they can be seen.

And there's the rub:

For apps that have no menus, Unity isn't hiding them since they're not there at all.

But for apps that have menus, it's a significant disservice to the user to hide them until the user figures out to hunt for them by mousing over the menu bar.  

Sure, they'll get used to it, but why make them hunt?

And even after they get used to hunting for menus, because they can't be seen until the mouse is moved to the menu bar they can't be aimed at, lengthening the time to acquire the sort of muscle memory which has historically made menus so useful.

So there's a downside to concealment for both new and experienced users alike.

And the benefit?

It was initially proposed as having a cleaner look, but menus aren't exactly noise, they're information, and as a primary means of command access they're very important information.

If the goal is cleanliness at any cost, the simplest solution is to turn the computer off -- there, nice clean screen. :)

Fortunately Mr. Shuttleworth appears less enchanted with Unity in its current state than some, very excited by the potential but soberly acknowledging that there are details that need refinement:
[http://ubuntuforums.org/showthread.php?p=10774258](http://ubuntuforums.org/showthread.php?p=10774258)

I'd be surprised if concealing menus from users remains the default in 11.10.

---

### Post by seeker5528 on 2011-05-05
> **CreativeReach said:**
> Firefox 4 also has a hidden menu in windows.

I guess since the Firefox 4 menus are easily found, that by hidden you don't mean unaddressable until you right click the toolbar area and click an option to see the menus or like one or more of the Windows Live programs where you actually have to click on 'Help' to find an option to see the menus.

Later, Seeker

---

### Post by azupan on 2011-05-05
> **rg4w said:**
>  . . . snip . . .

If the goal is cleanliness at any cost, the simplest solution is to turn the computer off -- there, nice clean screen. :) There is simple, yet workable solution to this dilemma: Top panel is shown if application puts its menu on it, otherwise it's (auto)hidden.

---

### Post by CreativeReach on 2011-05-06
A big problem in the unity launcher is that when I click on an Icon of a open window, it doesn't minimize.

---

### Post by srisharan on 2011-05-06
Yes, I agree.The icon in the launcher should have the ability to minimize windows.

---

### Post by CreativeReach on 2011-05-06
> **seeker5528 said:**
> I guess since the Firefox 4 menus are easily found, that by hidden you don't mean unaddressable until you right click the toolbar area and click an option to see the menus or like one or more of the Windows Live programs where you actually have to click on 'Help' to find an option to see the menus.

Later, Seeker

By hidden, I am saying they are not displayed in the traditional manner. But they are rather concealed.

---

### Post by mihalybaci on 2011-05-06
> **Johnsie said:**
> Now that we have got alot of feedback after the release of Unity I think it's important that we take alot  of that feedback into consideration and look for ways to improve it. 

Here are some of my suggestions:

-Create a suitable replacement for the 'Places' menu that was on the Gnome2 panel. That was a great way to easily access bookmarked shared folders without needing to go into nautilus first

-Create a replacement for the 'Applications' menu from gnome2. that quickly shows the installed apps withotu having to go full screen or type into a search box. If people don't like this idea then make it optional.


-Implement a 'show desktop' button. Alot of us like to keep shortcuts and folders on our desktops. Having a show desktop button would make that easily accessible.
I love all those options, in fact, the lack of 'show desktop' and 'app menu' are easily my two biggest problems with Unity thus far.

---

### Post by cloroxmartini on 2011-05-06
I believe that gnome should be dropped altogether and Unity made the default desktop environment. I think that the top panel should be done away completely, leaving the Unity bar as the main staple of the Ubuntu desktop. It should be visible at all time by default with options for autohide, window dodge, etc.

The first screenshot was made using AWN as the default windows manager instead of gnome. Obviously this is not Unity but I believe that it still gets the idea across. The gnome panel is now gone leaving behind the Unity bar. This frees up more space on the desktop and in my opinion has a better visual appeal.

I know Canonical spent a lot of time with appmenu but I really don’t think it’s necessary. Menu bars should be integrated back into their respective windows. If clutter is an issue, I believe there could at least be a menu button on the title bar.

---

### Post by CreativeReach on 2011-05-07
Unity will be the default in 11.10, GNOME3 is for the supers....or not. let fedora and others have it UNITY gives ubuntu a reason to stand out of the crowd of distros.

---

### Post by awi on 2011-05-07
I don't like Unity, I've  been Ubuntu's fan, but for the first time since 2005, I'm looking for an alternative distro. I've finally had several former windows users to change to ubuntu, for development and now this change makes them wants to go back to windows. It's just not suitable for desktop.
Here are some interesting points you might want to read

[http://jaderobbins.com/2011/04/hate-ubuntus-unity-use-ubuntu-classic/](http://jaderobbins.com/2011/04/hate-ubuntus-unity-use-ubuntu-classic/)

---

### Post by tumbes2000 on 2011-05-07
This has been my first experience with ubuntu.  Which I am using at the suggestion of a good friend of mine.  Coming from windows and Mac (I haven't run linux on my desktop since 2002).   I find myself basically happy with unity as a GUI.  I do wish they would keep some of the menu options like "applications" in the unity GUI vs gnome.  Somewhat similar to Mac os x.  So you have the "dock" but also the menus from gnome.  I do understand the idea of search instead of a list of apps, but that feature is rarely used in mac os x by users so making it the primary method of finding apps takes some getting use to.  Or perhaps a setup more similar to android phones with an applications button that will show all available apps.  A bit simplistic, but it works.

Past those comments, I have been impressed with ubuntu and will continue to use it for my primary os.

---

### Post by mc4man on 2011-05-07
> So you have the "dock" but also the menus from gnome.
You can currently add any menu(s) you wish to the unity launcher. 
They will be more accessible and quicker to execute than what was/is available thru the default gnome menus as seen in Classic.

What changes will happen to the launcher in 11.10 I don't know - hopefully they won't change too much in that regard or screw up the left click on icons

---

### Post by Jedah on 2011-05-08
Some suggestions about Unity, after 1 week of use:

- The launch bar should be movable to any of the four edges of the screen.

- A windows task list should be available somewhere in order to have a "mouse" way to change windows focus in parallel with Alt+Tab. This functionality should be removed from the Unity launcher. When I click there is should launch another instance of the application instead of giving focus to an already running instance. At least make it an option.

- When a window is maximized ,its main menu should be viewable at all times and the window caption should be displayed in the center of the top bar, after the application menu and only if it fits.

- Allow users to choose classic window menus, without any involvement of the top bar.

---

### Post by hawthornso23 on 2011-05-08
Configurability = number 1 proirity.

I'd like to see unity integrated with compiz properly so that all compiz effects can be used in conjunction with unity without crashing it.

I'd like to see the parts of unity separated into separate compiz plugins so that you can choose to have some aspects of it and choose alternatives for others. For example I like the new launcher, and I like the dash.  Not so keen on the new top panel and indicator area.

---

### Post by werewolves on 2011-05-08
> **hawthornso23 said:**
> I'd like to see the parts of unity separated into separate compiz plugins so that you can choose to have some aspects of it and choose alternatives for others.

Interesting idea, you should suggest this over at _[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")_.

---

### Post by CreativeReach on 2011-05-09
> **werewolves said:**
> Interesting idea, you should suggest this over at _[http://brainstorm.ubuntu.com/]("http://brainstorm.ubuntu.com/")_.

Its basically already set up this way but you don't have the option fore the old gnome menu, with out classic.

---

### Post by billio on 2011-05-09
I would like to see changes as follows. Bear in mind I am a desktop and laptop user mainly using a mouse.

1. Move it to the top of the screen. The reason for doing this is that it is much easier to scan and point to a horizontal array of icons than a vertical one.

2. The current Top Panel should be moved to the bottom of the screen, OR it should remain at the top and the Launcher should autohide, only being displayed when the mouse is at the top of the screen. The latter is preferred.

3. Icons on the Launcher should be fixable in position with the possibility of whitespace between groups of icons. This makes scanning and selection much easier. The Launcher Icons should have clear backgrounds, the current set of icons is difficult to resolve as they all have a squarish "button" shape. Avoiding a background button make icon art, colour and shape as visual triggers for recognition. At present colour and shape look to be similar across several icons.

4. The Launcher needs a better means of distinguishing open applications. I am not certain that this function should be combined with the launcher as it may be loading too much. I know Mac OS does this but I never bother with it. I prefer at the moment to have the open windows in a separate dock using AWN on the right hand side of the window. It is then much clearer what is open and also AWN uses better graphical cue to draw attention to something happening to a particular application.

5. A better means of accessing workspaces is required. The workspace switcher on the Launcher is not the answer. Currently I use three methods which are better: first use the middle mouse button to open the display of workspaces (as in Expo) or use the Gnome Panel workspace selector which gives and idea of what is open in each window. The point is that in both these cases a single click takes you to the right workspace. The third method is to select the open application/window from the AWN task bar which automatically moves one to the right workspace. It should be possible at least to label the workspaces.

6. It should be possible to install the Gnome Menu, or something similar in the Launcher, to allow the selection of software and other functions. This is by far the best way of selecting material because scanning a vertical sorted text list is the quickest way to select from a large ordered list. For me the most important point being that it is a selection by mouse movement and clicking without needing any keyboard input. I want to use the keyboard as little as possible.

7. Make the movement of a Windows main menu to the Top Panel an optional feature. I find it irritating that you have to see the main functions of an application by moving the focus to it when several applications are opne, which is often the case. I don't mind losing the small amount of vertical space this uses.

Looking further ahead, I think attention should be given to finding a means of making better use of the desktop as a means of presenting information to the user. Perhaps information form indicators in the top panel could be permanently displayed in a portion of the desktop. Perhaps some content should be user driven along the lines of the content of iGoogle home pages and similer.

Secondly, you could give more attention to the content of windows and how this might be broken out into a more useful interface form. For example many windows have lists - bookmarks, contacts, functions, word lists, wiki page names, special character input etc. - it would be useful if these could be held apart from the application and accessed from a single place on the desktop, for example at one edge, and the application loading when you select from one of its lists. This is way of switching the use of horizontal space in windows into vertical, hideable space on the desktop.

Thanks for the opportunity to comment.

---

### Post by tekstr1der on 2011-05-09
> **CreativeReach said:**
> A big problem in the unity launcher is that when I click on an Icon of a open window, it doesn't minimize.

> **srisharan said:**
> Yes, I agree.The icon in the launcher should have the ability to minimize windows.

This one bothers me a lot too. It's expected behavior from dock launchers.

There's a bug/opinion about that:
[https://bugs.launchpad.net/ayatana-design/+bug/733349](https://bugs.launchpad.net/ayatana-design/+bug/733349)

Also a possible scripted workaround on AskUbuntu:
[http://askubuntu.com/questions/36433/why-cant-i-use-the-unity-launcher-icon-to-minimize-applications-windows](http://askubuntu.com/questions/36433/why-cant-i-use-the-unity-launcher-icon-to-minimize-applications-windows)

---

### Post by CreativeReach on 2011-05-09
> **tekstr1der said:**
> This one bothers me a lot too. It's expected behavior from dock launchers.

There's a bug/opinion about that:
[https://bugs.launchpad.net/ayatana-design/+bug/733349](https://bugs.launchpad.net/ayatana-design/+bug/733349)

Also a possible scripted workaround on AskUbuntu:
[http://askubuntu.com/questions/36433/why-cant-i-use-the-unity-launcher-icon-to-minimize-applications-windows](http://askubuntu.com/questions/36433/why-cant-i-use-the-unity-launcher-icon-to-minimize-applications-windows)

They should issue a Natty update for this, instead of waiting until 11.10. Its like having a defective launcher.

---

### Post by Obnoticus on 2011-05-09
I don't know if anyone mentioned this, but it would be great to be able to minimize or completely hide the "Apps available for download" section in the apps menu and expand the "Installed Apps" section into 2 or more rows by default. I would imagine most people don't really care about some random suggested apps or packages that they have no use for clogging up space in the menu

---

### Post by cpatrick08 on 2011-05-10
how would you improve on unity it looks like a dock like awin,docky,etc go with gnome3 and the gnome-shell it is way better than unity

---

### Post by ManualSparrow on 2011-05-11
I think it would be an excellent idea to enable menus that only display while a designated button is being held down - for example, holding the Super/Windows key down could enable something like expose, and releasing it would just revert to the previous condition, which would help limit the problem of accidentally expose-ing then 'losing your place' in the windows. This is a pretty common feature in videogames, which, after all, are pretty much mini-OSes designed with a fast-paced 'workflow' in mind.

More on Expose:
It would be nice if your active window were focused/highlighted/centered automatically whenever Expose is enabled (via holding down Super). Flicking the mouse left/right/up/down or using the corresponding arrow keys would move the selection through the open windows until the user stops holding the key and returns to the desktop with the selection focused. In this way the traditional window switcher could be unified with Expose-like functionality.

At the same time, maybe you could throw launchers or Places bookmarks into the  mix and allow a customizable Super-menu.

---

### Post by CreativeReach on 2011-05-11
> **obnoticus said:**
> i don't know if anyone mentioned this, but it would be great to be able to minimize or completely hide the "apps available for download" section in the apps menu and expand the "installed apps" section into 2 or more rows by default. I would imagine most people don't really care about some random suggested apps or packages that they have no use for clogging up space in the menu

+1!!!

---

### Post by feydrutha on 2011-05-12
> **mgmiller said:**
> This exact fix is in the link I just posted.  It's a quick copy and paste into your terminal to implement it.

Adding the "Show Desktop" icon to the launcher as requested by the OP is also covered in the link I posted above.

Lots more neat stuff there, read through it all and have fun.

I have already set up a quicklist for my file manager launcher icon, as in the linked article. However, the places menu on the gnome-panel displays all of your nautilus places, which can be easily changed through the nautilus interface (drag-and-drop a folder into the bottom-left part of nautilus window). I think the quicklist should have the same behavior, and be available by default.

Actually I posted about this just a few minutes ago:
[http://ubuntuforums.org/showthread.php?t=1756360](http://ubuntuforums.org/showthread.php?t=1756360)

---

### Post by ndefontenay on 2011-05-12
Get the world clock map back on!

---

### Post by donkyhotay on 2011-05-12
> **Obnoticus said:**
> I don't know if anyone mentioned this, but it would be great to be able to minimize or completely hide the "Apps available for download" section in the apps menu and expand the "Installed Apps" section into 2 or more rows by default. I would imagine most people don't really care about some random suggested apps or packages that they have no use for clogging up space in the menu

another +1, I've suggested this in other posts. The default options we have now isn't really all that *bad* per se, but it's just annoying that I can't modify or change anything on it.

---

### Post by bonfire89 on 2011-05-14
> **azupan said:**
> [LIST=1]
[*]Top Panel autohide. Puhleeeze! It's the only thing that keeps me from switching to Unity right away. OK, I know it's menu in there, but most of the people don't use menus much theese days. Microsoft Office menus have been autohidden/hidden since 2007 I think, and it works just fine.
[/LIST]


This is the only reason I'm not using unity as well. And I don't think I ever will unless they do something about this.






I love how when I am running Chrome starting from the top of the monitor it goes: tabs, address bar, content. Nothing else. Till I can get this in unity I really don't see myself switching.

I don't know if that means making an autohide, integrating tabs into the top panel, or allowing me not to use a global menu... But whatever it is, I want it.

I would also like to see the Unity panel such that it doesn't expand.

---

### Post by mgmiller on 2011-05-14
> **bonfire89 said:**
> This is the only reason I'm not using unity as well. And I don't think I ever will unless they do something about this.

I love how when I am running Chrome starting from the top of the monitor it goes: tabs, address bar, content. Nothing else. Till I can get this in unity I really don't see myself switching.

I don't know if that means making an autohide, integrating tabs into the top panel, or allowing me not to use a global menu... But whatever it is, I want it.

I would also like to see the Unity panel such that it doesn't expand.

I know this works with Firefox.  Just hit F11 and you should get exactly what you are looking for.

---

### Post by NormanFLinux on 2011-05-16
I would like to see minimized windows displayed as a thumbnail or minimized icon so one can see at a glance what window is in the background.

---

### Post by CreativeReach on 2011-05-16
> **NormanFLinux said:**
> I would like to see minimized windows displayed as a thumbnail or minimized icon so one can see at a glance what window is in the background.

Just install the compiz settings manager, and turn on the windows previews, under extras.

---

### Post by NormanFLinux on 2011-05-16
I'm running Unity 2D.

---

### Post by athenroy on 2011-05-16
Maybe I missed this in a previous post, but one thing I noticed was everything in Unity seems to be "Left-hand" oriented, even the supplied themes and window controls.  For someone moving from Windows, this really seems awkward.  The launcher bar should be movable like the Windows task bar and the themes should offer more with standard Windows controls.  To tell you all the truth, I went back to the "Classic" desktop!  I remember several years ago they had a little program for Win XP which created a "launcher" similar to Unity, except you could move it around.  After the "newness" and "novelty" wore off, I removed it!  Wasn't worth the effort!  Fact is, I don't even think Unity is necessary, or it could be an installable option package for those who would like it. :)

---

### Post by macroshaft on 2011-05-16
> **athenroy said:**
> Maybe I missed this in a previous post, but one thing I noticed was everything in Unity seems to be "Left-hand" oriented, even the supplied themes and window controls.  For someone moving from Windows, this really seems awkward.  The launcher bar should be movable like the Windows task bar and the themes should offer more with standard Windows controls.  To tell you all the truth, I went back to the "Classic" desktop!  I remember several years ago they had a little program for Win XP which created a "launcher" similar to Unity, except you could move it around.  After the "newness" and "novelty" wore off, I removed it!  Wasn't worth the effort!  Fact is, I don't even think Unity is necessary, or it could be an installable option package for those who would like it. :)

Finally! something for the left handed by default! lol
Bare in mind unity in it's current form is only 6 months old. As I understand it the plan has always been to make it moveable but there simply wasn't time to do this in Natty. I did find what appeared to be a setting in compiz to do this but it doesn't seem to work.

---

### Post by TBABill on 2011-05-16
A choice of views on the dashboard. For example, when it says I have 81 applications installed and I'm just scrolling through them to find one I cannot remember the name of, having such huge icons looking at me just creates distraction when I could be more efficient with a "list view" with smaller icons (same icons, just smaller and listed instead of spread out, perhaps in 2-3 columns). 
 
That's a feature that could be easily made, but optional whether the user wants the larger default view or a smaller list view instead. And make it easy to change back and forth.
 
Also, a functional right click on the menu bar that lets any application launch another instance of that application (like Firefox can).

---

### Post by macroshaft on 2011-05-16
> **TBABill said:**
> A choice of views on the dashboard. For example, when it says I have 81 applications installed and I'm just scrolling through them to find one I cannot remember the name of, having such huge icons looking at me just creates distraction when I could be more efficient with a "list view" with smaller icons (same icons, just smaller and listed instead of spread out, perhaps in 2-3 columns). 
 
That's a feature that could be easily made, but optional whether the user wants the larger default view or a smaller list view instead. And make it easy to change back and forth.
 
Also, a functional right click on the menu bar that lets any application launch another instance of that application (like Firefox can).

Two of these features already exist, install the Compizconfig Settings Manager (CCSM), the option to reduce the size of the launcher icons is within the unity plugin. To reduce the number of installed applications you are viewing open the dash, click on 'more apps' then at the top right where it says 'all applications' is a replica of the original menu format so you can view just the games or just the internet applications.

---

### Post by NormanFLinux on 2011-05-16
I know how to move the buttons from left to right in the GNOME menu.

Does any one know how the global menu buttons can be moved from the left to the right? The look is inconsistent in Unity.

---

### Post by NCLI on 2011-05-18
> **NormanFLinux said:**
> I know how to move the buttons from left to right in the GNOME menu.

Does any one know how the global menu buttons can be moved from the left to the right? The look is inconsistent in Unity.

Nope, you can't. Maybe sometime in the future, but I doubt it.

---

### Post by cobolt01 on 2011-05-18
I had an idea that I thought I'd share. How about integrating the software center with the launcher? You could drag a program icon from the software center onto the launcher to install it. The icon can then fill up with a colour to create a progress bar. That would be user friendly :)

I also seriously dislike the hidden File, Edit etc. menus. It reminds me of Windows 7/Vista and I hate them, I hate them so much.

---

### Post by NormanFLinux on 2011-05-18
They're working on integrating the software center into the launcher. Its not an issue for me as I keep both Synaptic and Update Manager in the launcher.

The contextual search issue can be addressed by downloading cardapio and adding it to the launcher where it shows up, appropriately enough, as an Ubuntu icon. I find its much faster to scroll through the classic start menu to find what I'm looking for then typing in a box in the contextual menu to find what I need.

---

### Post by kansasnoob on 2011-05-18
The more I mess around with Unity the more I'm convinced that it simply won't work for me :(

I'll definitely stick with *ubuntu but I won't use the Unity DE :)

I'll take a look from time to time just to see what's changed, but IMHO Unity is simply not suitable for use in a casual desktop environment.

---

### Post by SushiR on 2011-05-18
> **kansasnoob said:**
> The more I mess around with Unity the more I'm convinced that it simply won't work for me :(

I'll definitely stick with *ubuntu but I won't use the Unity DE :)

I'll take a look from time to time just to see what's changed, but IMHO Unity is simply not suitable for use in a casual desktop environment.

Works fine here on a casual desktop environment... ;-)

---

### Post by kansasnoob on 2011-05-18
I consider "casual" being able to easily change between windows, apps, workspaces, etc.

Like I decide to check my mail, then maybe check the forums for recent activity, then check my bank account (I use a different web browser for that), and then I need to use a simple 'click-n-point' calculator.

With Unity at the very least it takes more clicks, but worst I quite often find myself lost :(

Seriously! If you're using an app in one workspace it seems to NOT be there when you return to that workspace. 

And even simple workspace management requires more clicks. This is the saddest regression I've ever seen.

Regardless I'll stick with Ubuntu, just not Unity.

---

### Post by NormanFLinux on 2011-05-18
I would like to see the classic start menu integrated into the contextual window and the user can decide at startup how he would like to search his computer. People do have different work habits after all.

---

### Post by Squonk07 on 2011-05-18
I'm sure some of you have already found this, but for those who suggested a sort of quick list/Places analog on the Home Folder icon, would something like this be what you're after?

[Web Upd8 11.04 Tweaks]("http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html")

(scroll down a ways until you see the heading "Missing a quick way...folders?")

Something like this, if it came standard and included more of the options from the original Places menu and was configurable, would work well for me. As it is, it's a good start and should pretty much be a no-brainer for Unity going forward.

---

### Post by Squonk07 on 2011-05-18
As for other things I'd like to see, I agree with some here that icons on the Launcher should minimize their respective programs. Also, something like Windows 7's window thumbnails should be implemented, allowing users to pick the window they want without having to click. I'm surprised at how much I found myself using that feature in 7 and how much I miss it in Ubuntu.

The more I use the global menus, the more I dislike them. I like chloroxmartini's idea to put a separate button on the title bar in order to expose menus but leave them out of the way by default. In theory the global menubar would seem a good idea, except that, as Ryan Paul of Ars Technica pointed out, Linux applications *aren't made* for a global menubar paradigm, whereas OS X ones (the obvious progenitor of the idea) *are*. That's why it feels so awkward to have them in Ubuntu.

Moving right along, the Launcher should be visible by default. I finally broke down after a week of battling with it and installed CCSM so I could fix the Launcher in place. The other options should be retained for those who want to maximize horizontal space (I have a 16:9 monitor, so 48 extra pixels of horizontal space is almost useless to me). All of this needs to be accessible by default, without forcing the user to have to install a complex settings program.

Finally, a small but nonetheless highly useful feature would be to allow interactivity on the Launcher icons. For example, the Empathy icon will display an overlay when I have a new message, but my Firefox/Nightly icon remains static, even if a message appears in a pinned tab or if a download* is occurring. I'd like some sort of indication for minimized windows that something needs my attention or else is progressing smoothly. Similarly I'd like something like this to overlay my Nautilus launcher when a file transfer is happening so I can switch to something else and still have persistent feedback on what's happening. If an error or crash occurs in a running, minimized program, I'd like a little "X" to overlay the icon so I can get to it when I'm ready. Finally, I'd like if the workspace icon would update in real time to show the layout of windows, like the Gnome applet used to. I suppose if you went beyond four workspaces you could have a mouseover window pop up (or appear on a right click).

*There's a [Firefox add-on]("https://addons.mozilla.org/en-US/firefox/addon/unityfox/") (click link) that displays an overlay showing download progress.

---

### Post by athenroy on 2011-05-18
Quite frankly, after trying it, I see no reason whatsoever to even have Unity!  Aside with messing around with some very early versions of Red Hat in the late 90s, I've been a Windows user and I have no problem using the Ubuntu Classic Desktop!  As I remember, one of the big advantages of Linux was supposed to be speed and simplicity.  I remember sometime around 2003 or 2004 I bought this little program for Win XP that added a similar launcher to XP.  Big difference was it wasn't as big and you could move it around.  It was novel at first but after about a month or so I un-installed it.  It wasn't worth the effort and I hardly ever used it.  Besides, it looks like a gimmick more than anything!  If you insist on keeping it, maybe you could move it to the bottom so it looked like Mac OS X!  Anyway, to me, I'd rather see more, good working drivers and software than Unity.  Sorry, but that is my opinion!

---

### Post by CreativeReach on 2011-05-19
Desktops are advancing, so must Ubuntu whether it be Unity or Gnome3.

But I do think Instead of unity 2d be the fallback, that the gnome3 fallback should be used in Ubuntu 11.10. That way we still have the classic like desktop.

---

### Post by Jordanbadangayon on 2011-05-19
they should improve the search in the dash... some of my folders and files are not searchable in dash...

---

### Post by Jordanbadangayon on 2011-05-19
> **RavensKrag said:**
> I'd like to see a better search system.  It'd be nice if all programs were tagged in some way, and the search could use that metadata to find programs that the user desires.  Some of this is already evident, as when you search for "photoshop," gimp shows up as a program which you can download.

It would be extra great if, in the spirit of open source, users could add on extra tags.  These new tags could then be used not only locally, but could be forwarded to some database managed by Canonical, so that all can benefit from a search experience more attuned to actual usage.
I agree... most applications in linux have names that do not really tell what they do... doing this would help people notice applications that they need.

---

### Post by zeroexcelcior on 2011-05-20
I've loved Ubuntu since I started using it (8.04) by recommendation from a friend. However, after "upgrading" to 11.04, I was so strongly dissatisfied with the changes that I made a forum account so that I may properly suggest future amendments.
I am somewhat relieved to see that I'm not alone in my dissatisfaction.

> 
awi:
I don't like Unity, I've been Ubuntu's fan, but for the first time since 2005, I'm looking for an alternative distro. I've finally had several former windows users to change to ubuntu, for development and now this change makes them wants to go back to windows. It's just not suitable for desktop.
> 
athenroy:
Maybe I missed this in a previous post, but one thing I noticed was everything in Unity seems to be "Left-hand" oriented, even the supplied themes and window controls. For someone moving from Windows, this really seems awkward. The launcher bar should be movable like the Windows task bar and the themes should offer more with standard Windows controls. To tell you all the truth, I went back to the "Classic" desktop! I remember several years ago they had a little program for Win XP which created a "launcher" similar to Unity, except you could move it around. After the "newness" and "novelty" wore off, I removed it! Wasn't worth the effort! Fact is, I don't even think Unity is necessary, or it could be an installable option package for those who would like it.
> 
kansasnoob:
The more I mess around with Unity the more I'm convinced that it simply won't work for me 

I'll definitely stick with *ubuntu but I won't use the Unity DE 

I'll take a look from time to time just to see what's changed, but IMHO Unity is simply not suitable for use in a casual desktop environment.
> 
athenroy:
Quite frankly, after trying it, I see no reason whatsoever to even have Unity! Aside with messing around with some very early versions of Red Hat in the late 90s, I've been a Windows user and I have no problem using the Ubuntu Classic Desktop! As I remember, one of the big advantages of Linux was supposed to be speed and simplicity. I remember sometime around 2003 or 2004 I bought this little program for Win XP that added a similar launcher to XP. Big difference was it wasn't as big and you could move it around. It was novel at first but after about a month or so I un-installed it. It wasn't worth the effort and I hardly ever used it. Besides, it looks like a gimmick more than anything! If you insist on keeping it, maybe you could move it to the bottom so it looked like Mac OS X! Anyway, to me, I'd rather see more, good working drivers and software than Unity. Sorry, but that is my opinion!

I strongly feel that the Unity interface is not ready for deployment. I understand that there are users who enjoy the revision and I believe that they're certainly entitled to use it, however there are also users who strongly dislike the new interface. I believe that keeping Unity as an option, either upon install or as another version, would be ideal and I urge the powers that are able to take this into consideration.

I am aware that disabling Unity and using the classic interface is an option in 11.04, but I feel the loss of stability and performance is unacceptable. I've since reverted back to 10.04 LTS.

---

### Post by Squonk07 on 2011-05-20
I didn't catch all those quotes the first time, and the "left-handed" one stood out to me. I think the reason they went with this design decision is because the right hand side of the desktop is already heavily populated with stuff, much of it likely hard-coded to appear on that side (e.g. system notifications, various menus whose names escape me at the moment). In addition, we've all built up years of muscle memory for the location of all that stuff, so even if it were freely movable, we'd all have to relearn the location. At least this is probably Canonical's rationale; take it for what it's worth (if I'm right, that is).

I also think the Unity layout was a long time coming--it's no accident, I think, that the close/maximize/minimize buttons were moved to the left side of title bars as early as Lucid. Take it or leave it, at least it's all pretty consistent (except for stranding the System Settings menu all the freakin' way on the other side of the panel).

I agree that it should still be configurable, though. It might mean a lot more development work, but it's one of those things that's going to grate on a lot of people until it's implemented, and better an official implementation than a cobbled together hack.

---

### Post by cariboo on 2011-05-20
Please keep the off topic post out of this thread, the thread title is **Improving Unity**.

If you want to post an opinion, there are plenty of threads in the [Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11")

---

### Post by kansasnoob on 2011-05-20
> **cariboo907 said:**
> Please keep the off topic post out of this thread, the thread title is **Improving Unity**.

If you want to post an opinion, there are plenty of threads in the [Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11")

Then my list would be as follows:

#1: Make it possible, and easy, to move and/or totally customize both the Launcher and the top panel. That includes being able to combine the two.

Reasons: 

With certain screens it may be more "space appropriate" to have the Launcher on the top or the bottom.

The top panel is worthless to me on a desktop due to my eyesight, if I could move it to the bottom I could almost make that work, if window and app management improved.

#2: Make it very, very easy to choose between global or non-global menus!

Reason:

I can't see well, having to point (mouse-over) in just the right place to display something, especially when that area is already cluttered, is problematic to say the least.

#3: Improve window/application management. What happened here anyway?

Reason:

I find this totally confusing. For instance, if I have the calculator open in the same workspace as my bank account in web browser A, but also have the calculator open in another workspace to calculate purchases I'm considering on a website that I'm browsing in web browser B, things turn into a complete and total freaking nightmare :mad:

#4: Display messages such as updates available, messages available, etc. until I choose to dismiss them! Actually display them where I wish for as long as I wish!

No reason needed, SABDFL poo-pooed that idea long ago. AFAIK that was the beginning of the "love it or leave it" attitude towards the Ubuntu iteration of the Gnome DE :(

#5: Make it easy to add/remove/move every item in the panel/Launcher just like we could in gnome 2. Yes, this should have likely been included in #1.

#6: Ditto what I said regarding the global menu for those silly new scrollbars. Make it easy to choose which type of scrollbar you want. I can hardly see the new scrollbar thingamajigs so to me they're the worst nuisance in the world!

How's that for a start?

---

### Post by kansasnoob on 2011-05-20
Thought of another, regarding the new workspace switcher, why have to click on the launcher icon which displays all four and then have to double-click the one you want?

Previously a single click on the workspace you wanted just worked :)

Still one more, and a big one!

Some of us are inclined to a mouse-centric experience. Why should we be FORCED to learn a keyboard-centric way of navigating?

And don't just say it's easier once you learn how.

---

### Post by seeker5528 on 2011-05-20
> **kansasnoob said:**
> Thought of another, regarding the new workspace switcher, why have to click on the launcher icon which displays all four and then have to double-click the one you want?

Hopefully that means there will be improvement along the way if you want to do something like.....

View your desktops.
Select a desktop.
Cycle through the windows on the selected desktop.
Drag one or more windows to one or more other desktops.
Then go to one of the other desktops.

Just a thought, could be wishful thinking on my part. 

Later, Seeker

---

### Post by kansasnoob on 2011-05-20
This exercise was not just a rant on my part. I can already see so many flaws in both Unity and Gnome Shell as DE's that I feel ranting about it is futile.

It's not much different at Fedora ;)

Over there some love the default gnome-shell on top of gnome3*. Here at Ubuntu some love Unity. I at least applaud Ubuntu for making Unity the default with an easy fall-back six months ahead of the switch to gnome3.

Clem over at Mint bragged about using gnome3 with gnome-panel and proved himself to be full of BS!

Based on recent comments from the Gnome devs who knows what will happen next :confused:

I'm somewhat strongly leaning towards Lubuntu ATM. I really find very few things it can't do that I want from a DE :D

---

### Post by NormanFLinux on 2011-05-20
I see a need to import GROWL to Linux. Its cool on Mac OSX and Windows.

We need a centralized notification system so we can catch up to speed quickly and I'd like to see Canonical developers work with GROWL to integrate it into Unity.

---

### Post by seeker5528 on 2011-05-20
> **NormanFLinux said:**
> We need a centralized notification system so we can catch up to speed quickly and I'd like to see Canonical developers work with GROWL to integrate it into Unity.

We have an open specification for system notification which different desktops and apps can choose to use or not.

[http://www.markshuttleworth.com/archives/347](http://www.markshuttleworth.com/archives/347)

Don't see what GROWL has to offer over this and it seems less likely that a solution developed on non-linux systems would grow to be more universally accepted by the Linux developer community than a solution developed within the Linux developer community that already has some significant support.

Later, Seeker

---

### Post by cariboo on 2011-05-20
Thanks kansasnoob, that's the type of posts that should be in this thread.

---

### Post by NormanFLinux on 2011-05-20
My point is the same notification system that works on all operating systems that looks and feels the same would help users to focus on what they need to do. A cross platform notification system is exactly what's needed. They're working on porting GROWL to Unix/Linux systems.

---

### Post by kansasnoob on 2011-05-21
> **cariboo907 said:**
> Thanks kansasnoob, that's the type of posts that should be in this thread.

Thanks for that comment :)

I'm honestly not just another Unity-flamer. It's simply that so much of Unity does not work for me that it's hard to even explain.

After posting here I decided to take a slightly different approach with the best of intentions:

[http://ubuntuforums.org/showthread.php?t=1763645](http://ubuntuforums.org/showthread.php?t=1763645)

That really blew up in my face :lolflag:

I largely put any serious focus on Unity on hold while I was focusing on ubiquity and I'm just now trying to get in the "fix Unity or convince Canonical to provide a pure Gnome3 version" mode.

It's very difficult to do because emotions are running so high. Those who love Unity basically tell those with problems either how to revert to classic or they demean them as inept, or even worse.

OTOH those who hate it actually say things like "it sucks" which accomplishes nothing. It's a bad situation, but I truly do see the need of Ubuntu making a decision between "gnome-shell" and something else.

Those who are not looking forward fail to even see the difference between obtaining a "classic" DE in Natty to the equivalent in Oneiric. 

We don't yet know what that will entail, but based on my playing around with gnome3 from ppa's, I can tell you it's going to be quite different.

So it really is reasonable to ask questions and try to figure out how to make different things work on an individual basis.

I've never seen so many downright ugly comments regarding a change in the time I've been using Ubuntu. Rather sad :(

---

### Post by Kivech on 2011-05-21
My biggest gripe with Unity is customisability, or the lack thereof.

I cannot add or change any items on the menu bar on top of the desktop. If I can, it has become too complicated compared to how easy it was in Gnome2.

I definitely want that back. Give us plugins that we can add with the click of a mouse and put in our bar, without hassle.

Also, give Unity themes, one way or another.

Anything that allows us to customise would be great. It is one of the huge benefits of Linux as opposed to Windows that we can customise. It would be a shame if with Unity that would be limited even more than it was in Gnome2 (which in my mind was too limited already).

So, customisation is key here.

---

### Post by kansasnoob on 2011-05-21
> **Kivech said:**
> My biggest gripe with Unity is customisability, or the lack thereof.

I cannot add or change any items on the menu bar on top of the desktop. If I can, it has become too complicated compared to how easy it was in Gnome2.

I definitely want that back. Give us plugins that we can add with the click of a mouse and put in our bar, without hassle.

Also, give Unity themes, one way or another.

Anything that allows us to customise would be great. It is one of the huge benefits of Linux as opposed to Windows that we can customise. It would be a shame if with Unity that would be limited even more than it was in Gnome2 (which in my mind was too limited already).

So, customisation is key here.

Some items can be added to the top "panel" but since the top panel is largely useless to me I haven't bothered to learn how.

But I think most of us agree that things need to be easy to customize. I loved how easy it was to customize the gnome-panels :)

---

### Post by Kivech on 2011-05-21
Actually, while thinking about it, there is one other very big gripe I have with Unity.

Clicking, click, clicking, click, and click again.... 

Too many clicks.

What I first could do with one or two clicks I now need to click 4 to 5 times to achieve. That is rubbish.
When I was taught to write commercial software (a loooong time ago) I was taught to make things accessible and easy to work with. Not cumbersome and clumsy.

Now I have to click 'Other programs', then click which listing I want, expand the listing and then click the application I want to launch.

First I just clicked the menu button, moused over the section I needed and clicked the application I wanted. That's going from 2 clicks to 4.

Rule number one in programming anything in my mind is, making it simple. So going from 2 to 4 clicks is a programming disaster by definition.
When it first could be done in two clicks, if you want to improve it, try to have it done in just one click. That would be moving in the right direction.

That's why those docks are so popular. One click, and you got what you want. That part of Unity is good (though all programs launch very slowly, there is a delay of several seconds at times, while with the Gnome2 menu it is practically instant).
So I definitely would not try to replace the menu bar with Unity, because in its current state it cannot compete with it.

Kansasnoob mentioned the workspace selector which is also an excellent example of this error.

I'm all in favour of nice looks and such, but then for the love of .... make it simple, effective and efficient. And most of all, fast.
At the state Unity is at right now, it is slower on my system than Vista. And that in my mind is really bad.

I personally switched to xfce, because there it seems that they did understand that functionality and flexibility is more important than fancy looks.
Now I have always liked Gnome, definitely do not like where Gnome3 is going and do like the Ubuntu initiative to come up with Unity. Really, I think the concept in itself is good. It just really needs some good loving to get it where it should be.

So aside from customisability, it really needs to be brought to the same level of user friendliness that Gnome2 has.

Also, the fact that some claim that it is more keyboard oriented is a tad retarded if you ask me. Next thing I know they will start asking me to start hooking up a typewriter from the 1920s to my PC, because that used to work so well and reliable. :shock: :P

I really find this nonsense. You want a keyboard oriented desktop environment, then make it console and server only. There you go, totally keyboard oriented. You do GUI, you work with the mouse. You don't want to do mouse, then don't do GUI. It really is that simple. To satisfy those that want to work mostly with the keyboard, give them key bindings to all actions, but creating less efficient menus for the sake of keyboard usability is beyond me. But at this point I'm not sure if this has actually been said by the developers. :confused:

I guess there are plenty of smart people working on Unity to work these issues out. And I do have hopes for the whole concept. But it really needs some work before it can properly compete with other desktops in my mind.

I am following your progress with the biggest curiosity though. ;)

---

### Post by mc4man on 2011-05-21
> kansasnoob >
So please just tell us what you can do with Unity or Gnome Shell that I can't do easier and faster with gnome 2, please

Not really worth comparing what I can do for me faster, better, easier ect. than you for yourself. Really doesn't matter one way or the other, just personal preference's and or working with what's available.

So taking 1 item - menus
For myself I find menus in the unity launcher more accessible, faster to execute, easier and quicker to customise and or maintain than the previous gnome panel menus.

I can categorise them as I please, populate with any combo of apps, apps with modified launch commands, locations -  local or otherwise, scripts and run commands, ect.
Obviously nothing that can't be done with the gnome panel - it's just better for me for all of the reasons previously stated.
(did file a wishlist on submenus off of the launcher, though probably not needed and would add that game changing extra click.

Another item - window lists
I can actually see how some may prefer the previous than the current scale window group picker.
Again here I have no issue with and like how it is currently set - certainly hope it isn't changed significantly unless it was to something superior.  
(and that doesn't mean window lists though it would be great if an alt. means to view and access was developed for those where scale doesn't suit their use case and or patience.

There was certainly some confusion and question during the natty dev as to what was to happen on the left click on active icons - I think they eventually got it pretty good. 

Though when I see you give this comment I wonder if you've really tried to understand how it works

> I find this totally confusing. For instance, if I have the calculator open in the same workspace as my bank account in web browser A, but also have the calculator open in another workspace to calculate purchases I'm considering on a website that I'm browsing in web browser B, things turn into a complete and total freaking nightmare
That scenario is the most basic, easiest use of the window picker - can't see what's confusing at all

On WS A an open browser & calc
On WS B an open browser & calc

If focus is on either one of the browser or calc windows then a single click on the respective app icons give you the picker window - pick one
If focus is not on the icon you click on then 1 click returns focus to the app chosen on current WS, a 2nd click, if desired does the above

(If you happen to be on WS C, (no browser or calc windows),  then a single click on either the browser or calc icon returns you to the last browser or calc window that had focus, a 2nd l. click, yet again gives you the picker window

There are tons of other scenarios - they all work very logically

As far as keyboard - hardly ever use here, only occasionally for ALt+F2 for command not in launcher menu and sometimes Crtl+Alt+ arrow keys (L,R or Down L.R to switch WS's (use rotate 1x4 here

---

### Post by bonzini on 2011-05-23
An interesting possibility with Unity was voiced awhile ago in Gnome Shell design principles but I think that principle has been largely ignored subsequently.

Lots and lots of us use laptops or even desktops with wide, short screens.

Lots and lots of the apps we use are not configured, nor even configurable, to deal with that screen geometry.

The absolute worst example of UI design in this context is the whole Microsoft Office ribbon thing.  Here we have a UI design which requires a significant amount of vertical space on vertically-challenged hardware.  Boo!

Close behind that is the Apple dock that chews up a couple of hundred valuable pixels at the bottom of the screen.

So, since Unity has already figured out that a UI on a wide (short) screen should have a vertical dock, what about applying this design principle further?

* fire up the applications menu, and look at those stupid big icons.  make them a reasonable size / geometry and we could see more than five apps without scrolling.

* great job on the global menu, but the suggestion to hide it when the live app isn't using it - not a bad thought.  might be hard to effectively manage vertical maximizing and transitions between apps.  or maybe, if it is too hard to get good integration between apps that use the global menu and those that don't, then do away with the global menu and give us the whole vertical screen back by putting the system tray / notificantion thing down the right side of the screen.

* someone in this thread made the wonderful comment that "menus aren't noise, they're information" (sorry for the weak paraphrase).  take this a step further as a design principle - maximize information density on the screen.  small icons by default, vertical maximize rather than full-screen maximize (short screens), positioning of menus, buttons, etc where they make sense (vertically for short screens).

* to those wishing for more and more alt-super-ctrl-meta-click options to reveal menus or other stuff, remember that this is actually NOT good UI design; it is rather a direct consequence of only having one button on the mouse and the subsequent recognition that quadruple clicking is hard to do.  most of us have two buttons, let's use them well.

My 2 ¢ worth

---

### Post by kansasnoob on 2011-05-23
Staying totally "on-track", can someone show me how to move the new top "panel" to the bottom?

I don't want to add an old "gnome-panel" or any other dock to the bottom. I want to move the new top panel to the bottom.

NOTE: I'm going to try a different approach to this, basically one baby step at a time :)

Due to age and failing eyesight I can sometimes be slow on the uptake.

---

### Post by RobertSwipe on 2011-05-23
Clearly there's a lot of comparison of Unity and Gnome (3) Shell, and I've now used both a bit. Not a lot, as time hasn't permitted.

I do find it surprising that Canonical decided to avoid Gnome Shell and spend a large amount of effort developing something that is not a million miles from GS. Their combined efforts could easily have produced something that actually delivered a better overall result.

For me at least, Unity does not work as well as Gnome Shell, for a few reasons:

1. The use of a common menu bar at the top of the screen for all apps is a disaster on a large 24" screen. I keep several app windows open, and the constant moving from one part of the screen back to the top to get to the app menu becomes quite frustrating and tiring over time. So much so that this is my main reason for rolling back to Classic.

2. The left hand panel should be movable to other sides of the screen as needed for the situation.

3. The use of icons in a scrollable list also becomes frustrating - I can recognise my most frequently used icons, and I can place these at the top (good). However, I have no idea what all the other icons mean without hovering over them to wait for the text panel to pop up. This makes it much slower to find what I'm looking for (a text search is also only useful when I know the name of what I'm looking for - new users are left isolated in this respect). Gnome Shell keeps names with each icon, allowing me to see immediately what something represents.

4. When an app is loaded, the icon gets a little marker against it. All well and good, except when the app is a few scrolls down in the list. Compare this with Gnome Shell which keeps a separate list of loaded apps - much more useful and easier to switch back. It would help if open apps were automatically moved to the top of the scrollable list.

4a. Opening a second instance of an app is not at all intuitive.

4b. Launching an app is a strange experience - there's no cursor indication that anything is happening, and quite often I've felt that my double-click didn't work, so try again. A change to the cursor in some way to indicate that the launch is taking place would fix this.

5. Move to the top left corner and click to get the overview screen. No click needed for the same task in Gnome Shell, just the movement. This is so much faster, for no apparent reason, since a click doesn't take long!

6. Access to the other desktops seems awkward in comparison to GS.

7. Out of the box, I'd love a simple and permanently visible way to:
   - clear apps back to the bare desktop.
   - access my home folder

There's a lot to like about Unity in a netbook environment, but right now, I'm sticking with 10.10 on all other PC's here to see how things pan out with the next 11.10, and whether a Gnome Shell version will be available as part of the shipment. 

Unity is fine for my netbook, where the screen size really only lets me see one app at a time. But in a desktop environment, it really doesn't cut the mustard. Right now, I'm not confident that it will ever be a good desktop environment - the single menu bar really does limit its usefulness for large screens.

I need to spend more time with both - when I can find more time!

---

### Post by Bazon on 2011-05-24
To make Unity better, **these regressions should be fixed:**

List of things which are less efficient compared to previous versions or not even possible any more in Unity:

* Grouping windows in contexts by using workspaces
Although workspaces are still there in Unity, they lost their function: Every window on every workspace is represented in the launcher. The launcher even lets you switch the workspace without intending it. You don’t even have a glue on which workspace you are on now, as this is not shown any more.
[https://bugs.launchpad.net/unity/+bug/683170](https://bugs.launchpad.net/unity/+bug/683170)
[https://bugs.launchpad.net/unity/+bug/689733](https://bugs.launchpad.net/unity/+bug/689733)

* Starting a window in e.g. 80% screen size
Before, a new window launched exactly the size you closed it last time. Now, when it was bigger than 75% Screen Size last time, the window is forced to open maximized. Whether you want it or not.
[https://bugs.launchpad.net/unity/+bug/754214](https://bugs.launchpad.net/unity/+bug/754214)
[https://bugs.launchpad.net/bugs/769085](https://bugs.launchpad.net/bugs/769085)

* Using menus in different windows
Requires one click more each time you change the window: FIRST click to focus the window, second to get to the menu. Before, focusing the window and accessing the menu was just one click.
(don’t know whether there is a launchpad bug about this)

* Selecting windows containing text documents
is now very difficult, because in the shiny exposé-like view you can’t read the content and the window title:
[https://bugs.launchpad.net/unity/+bug/734253](https://bugs.launchpad.net/unity/+bug/734253)

* Pasting in Alt+F2
worked before with middleclick paste, Ctrl+v or context menu and was very useful following tips from the internet. Doesn’t work any more:
[https://bugs.launchpad.net/unity/+bug/736222](https://bugs.launchpad.net/unity/+bug/736222)

* Quick look in a window and then minimize it again
Worked before with pressing the window switcher two times (show – minimize) and was very useful and a very common practices. Doesn’t work any more with the Unity launcher:
[https://bugs.launchpad.net/ayatana-design/+bug/733349](https://bugs.launchpad.net/ayatana-design/+bug/733349)

* Minimizing a background maximized window
Is more difficult than before, because that window has no controls: Normally, the window controls are in the top panel for maximized windows. But the top panel is now occupied by the window having focus. (Which is confusing by the way, as it looks like the menu belongs to the background maximized window)
[https://bugs.launchpad.net/unity/+bug/762277](https://bugs.launchpad.net/unity/+bug/762277)


*(I tried to post that on [mark's page as a comment](http://www.markshuttleworth.com/archives/671#comment-352713) about three weeks ago, but this comment is still awaiting moderation...)*

---

### Post by mc4man on 2011-05-24
> * Starting a window in e.g. 80% screen size
It's possible the max window function won't be in the next unity - the 75% was just picked as better than the orig. default of 60% - It (max win) did help fix 4 early bugs, which may or may not continue to be a factor and should be re-accessed


> Quick look in a window and then minimize it again
Testing the commit on that now, for most part works ok though does create even more possibilities (some seem confused with all the current ones

When the option to 'do not minimize' is set, *the default, it  also adds, changes things a bit, though mostly positively
( if the last window focused is minimized it may be un-minimized on left click depending on WS and focus
I like it, though it does exceed the 'plan'.., will keep here on natty where it's unlikely to ever be added, hope it gets merged

> * Selecting windows containing text documents
Can be improved a bit now by enabling the Scale Addons and text plugins

---

### Post by kansasnoob on 2011-06-03
I encountered a new annoyance while iso-testing. This is cross-posted in the Unity Mega-thread at the Cafe:

While performing iso-testing I do use the Unity DE, of course very little multi-tasking is involved - maybe I'll use the screenshot tool, a browser, and the installer at the same time - that's about it.

But I did encounter another annoyance while testing the Oneiric Alpha1 candidate. I use gedit quite a bit, and gedit docs extend to the left edge of the screen so when I move the mouse pointer to the left edge in order to copy-n-paste pre-typed commands the Launcher opens over the doc slowing production to a crawl :(

As an example I use this to change my screen resolution so I can see:

```
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900_60.00
xrandr --output VGA1 --mode 1440x900_60.00
```

If you paste that into a blank gedit doc you should see what I mean :)

---

### Post by mc4man on 2011-06-03
> so when I move the mouse pointer to the left edge ...
Try opening the unity plugin settings and disable the left edge reveal
(in ccsm just click on the green area to remove, or can be done in gconf-editor
```
gconftool-2 -s -t string  /apps/compiz-1/plugins/unityshell/screen0/options/launcher_reveal_edge  none
```

---

### Post by DinoT1985 on 2011-06-03
These are what I want to see;

- Previews of open windows when you hover on Launcher icons.

- No minimum size for setting Unity Launcher.

- Quicklists for all programs. Libre Office listing its packages, Home Folder listing Documents, Piuctures etc. 

- Wider choice of lenses and a Lenses category in Ubuntu Software Centre. 

- Various Unity themes and customisability. Changing background colour, glow light colour etc.

- Ability to change icon size in Dash, space/padding size in Dash and Dash search. I think its too big.

- Ability to sync the panel calendar to Google Calendar etc, adding events without the need of Evolution. 

- Kill command integrated in the Power button list.

- File search should look for all files, not just the recent ones.

- Fix the copy and paste ability in Dash.

- Ability to change Shortcuts in Dash.

- Add a hover light on Launcher.

---

### Post by kansasnoob on 2011-06-03
> **mc4man said:**
> Try opening the unity plugin settings and disable the left edge reveal
(in ccsm just click on the green area to remove, or can be done in gconf-editor
```
gconftool-2 -s -t string  /apps/compiz-1/plugins/unityshell/screen0/options/launcher_reveal_edge  none
```

But how would I then expose the launcher when I want to?

I imagine it's a key combo, which is OK, but it certainly breaks what's become a natural work flow.

Also remember I'm talking about testing the Live CD. How much modification should someone have to make once logged into the live desktop just to make it easily usable?

---

### Post by cariboo on 2011-06-03
You can set where you want reveal mode to activate in ccsm, see the screenshot.

---

### Post by gangov on 2011-06-03
I just want it to be faster. I don't know if this from the Linux itself or from Unity but when i click on the dash or when i start typing in it, it has some really small lagging time which is rather annoying ( By the way i have 2GB of DD3 RAM and 2 core Intel processor and a 256 MB video card....)  . Last i heard is that Wind@w$ 8 is gonna be asking for really really low system spec... So i think if we want to beat 'em the OS should really star minimizing it's system requirements.

---

### Post by mc4man on 2011-06-03
> But how would I then expose the launcher when I want to?
The default, (mouse), has and continues to be the upper left corner - this is irrespective of whether the the 'reveal' mode is set or not 
> 
How much modification should ...
If they choose to make left edge reveal enabled by default then not likely anyone's mind that would need to be changed will be ...

---

### Post by kansasnoob on 2011-06-05
> **cariboo907 said:**
> You can set where you want reveal mode to activate in ccsm, see the screenshot.

Thanks, a picture is worth a thousand words :)

What appears to work best for me is having only the BFB or extreme upper left trigger reveal. That may partly be because I don't see well.

---

### Post by NormanFLinux on 2011-06-05
Rolling Menu list like the old Menu so one can rapidly find a desired application. Add drag and drop support so one can just put it in the launcher.

---

### Post by ojdon on 2011-06-05
As a Tablet user I find Unity so frustrating to use on a touchscreen. For example those "overlay" scrollbars are just so fiddly you have to carefully hover over that thin little line.

Luckily Gnome-shell has a few interesting features for use Tablet users such as been able to scroll through the applications menu via finger scrolling, I'd love to see something similar done in Unity.

But for now, I'm a big supporter of Gnome-Shell on a tablet. It's pretty much perfect! :D

---

### Post by Starks on 2011-06-06
Until I can close windows from the expo. Unity is useless.

---

### Post by fjgaude on 2011-06-06
> **Starks said:**
> Until I can close windows from the expo. Unity is useless.

Pray tell, what do you mean by 'expo'.

I use all four desktops in my work, and fine the ability to click a Launcher icon, taking me to its desktop, fast, faster than any shell I've ever used.

---

### Post by seeker5528 on 2011-06-06
> **fjgaude said:**
> Pray tell, what do you mean by 'expo'.

Expo is the plug-in used for the workspace switcher.

If there is no close button for a window, there is no way to close it while in the expo view, which is currently the case for unmaximized windows, which I am assuming is a temporary situation.

If an app is full screen, the button should show on the top bar when the application has focus, so you can switch to a full screen window in the expo view and close it, which mostly seems to work, I do notice some times the buttons not showing up even when a window is maximized.

Apparently if you drag a window to the top of a desktop while in expo, not only does it not maximize, but you lose the ability to drag that window around and when you then go to that desktop the top of the window is covered by the top bar.

Later, Seeker

---

### Post by fjgaude on 2011-06-06
Okay, I see, but this issue is something that hasn't gotten into my way. Thanks for telling the story.

---

### Post by Starks on 2011-06-06
you've never had multiple documents or desired browser popups open at once?

unity can not deal with such situations.

you have to close each window one-by-one, collapsing the expo or alt-tabbing each time. you can't just x out multiple apps in a row from the expo like in gnome-shell.

---

### Post by fragos on 2011-06-07
> **Starks said:**
> you've never had multiple documents or desired browser popups open at once?

unity can not deal with such situations.

you have to close each window one-by-one, collapsing the expo or alt-tabbing each time. you can't just x out multiple apps in a row from the expo like in gnome-shell.

On a daily basis I have multiple HTML documents open for text editing while viewing the results in two browsers. At the same time I frequently have nautilus, gimp and filezilla open -- my personal site development mashup. Granted Unity isn't the same as Gnome shell but I still find it very workable and in some situations preferable to Gnome. Different doesn't mean impossible for me.

---

### Post by Peter09 on 2011-06-07
Has the idea been raised that when the Meta key is held down (exposing the launcher and numbering the Icons) the mouse focus is 'grabbed' and forced onto the launcher, allowing the user to select via the mouse as well as keyboard numbers.

This would mean only needing to use one hand on the keyboard in that mode and allowing the other to remain on the mouse or touchpad. Once the meta key is released the mouse returns to its original place and focus.

This would also assist users with large, or multiple, screens where getting to the launcher can mean a long movement of the mouse.

---

### Post by AntoineT on 2011-06-07
> **Starks said:**
> you've never had multiple documents or desired browser popups open at once?

unity can not deal with such situations.

you have to close each window one-by-one, collapsing the expo or alt-tabbing each time. you can't just x out multiple apps in a row from the expo like in gnome-shell.

Maybe I missed your point, but when I want to close multiple instances of an application at once, I just right-click on its icon in the launcher and left-click on "quit".

Edit: if you want to close some but not all instances of an application that might be open on different workspaces, right-clicking on its icon brings the scale view for that application, and you can then close selected instances by clicking on "x" in the global menu (granted, you have to use the arrow keys to give focus to the instance you want to close)

Antoine

---

### Post by fjgaude on 2011-06-07
> **Starks said:**
> you've never had multiple documents or desired browser popups open at once?

unity can not deal with such situations.

you have to close each window one-by-one, collapsing the expo or alt-tabbing each time. you can't just x out multiple apps in a row from the expo like in gnome-shell.

My work flow is such that this is not an issue. Notice my normal four-desktop arrangement. Right click on a desktop and I'm there. Click on an icon and on its desktop.

Thanks for your observations.

---

### Post by Omega The End on 2011-06-08
> **Starks said:**
> Until I can close windows from the expo. Unity is useless.
You should try middle clicking.

---

### Post by AntoineT on 2011-06-08
> **Omega The End said:**
> You should try middle clicking.

thanks for the tip!

Although I think that the "text", "scale addons" and "scale windows title filter" compiz plugins should be enabled by default, otherwise it is pretty difficult to distinguish between, say, different text documents while in scale mode.

---

### Post by Starks on 2011-06-08
> **Omega The End said:**
> You should try middle clicking.

Synaptics touchpads can't do this easily. You need to press both buttons at the same time or change an obscure setting to enable two-finger middle click on the pad area.

Also, middle clicking is not obvious as a solution.

---

### Post by Omega The End on 2011-06-08
> **Starks said:**
> Synaptics touchpads can't do this easily. You need to press both buttons at the same time or change an obscure setting to enable two-finger middle click on the pad area.

Also, middle clicking is not obvious as a solution.
I have a Synaptics touchpad myself, it just takes some getting used to. I agree that it's not too obvious.

---

### Post by seeker5528 on 2011-06-08
> **Omega The End said:**
> You should try middle clicking.

That works for scale not for expo. But seeing how the discussion has progressed, maybe that's what the OP was referring to?

I didn't know about the middle click for the scale plug-in, nice tip. 

Personally when dealing with windows of an individual app, switching to any individual window and closing it is a quick enough process that it never occurred to me to look for an even quicker way.

Later, Seeker

---

### Post by mc4man on 2011-06-08
> That works for scale not for ....
Also available in scale addons for keyboard

---

### Post by RedLeg217 on 2011-06-08
I don't know if these have already be said, but here I go:

1. Be able to move the dock, at least to the right side.  I keep bumping it when I want to hit the back button on my browser.  

2. Ability to remove the Workspace Switcher, Applications, and Files and Folders launchers.  There is some redundancy there and I find that I go through the main Ubuntu button (for lack of a better term) for my apps and through the Home folder icon for any files.  I also just hot-key to switch workspaces.  I understand people may like them, but it would be nice to have an option.

3. Be able to place items in the main panel.  I miss having the weather and Tomboy up there.

4. A show desktop icon or some other way to manage windows when you are in full window mode, like with a browser.

5. Icons for the usual "Applications, Places, System" list found in Classic Ubuntu, only in the dock.

There's some other stuff, but those are my strongest wishes right now.

---

### Post by Rifester on 2011-06-09
Indicator-Weather will put the weather back up in the panel for you.   It works well for me.  :)

---

### Post by RedLeg217 on 2011-06-09
> **Rifester said:**
> Indicator-Weather will put the weather back up in the panel for you.   It works well for me.  :)

Outstanding, thank you!

---

### Post by Rifester on 2011-06-09
You are welcome!

---

### Post by Hman242 on 2011-06-10
I've viewed this thread multiple times, but never posted in it. I might as well post this time.


[LIST=1]
[*]Customization
[*]The Menu
[/LIST]
These are the two things I think they should really try to focus on on the next release or two. The launcher should be as customizable as the themes are. It does fit alright with many themes, but it should still be customizable. Having a color and opacity slider in Unity plugin in CCSM would be great. The launcher and the panel should be movable as well.

The menu looks like it is optimized for tablets. It takes up most of the screen. Instead of using paragraphs to explain how I think it should look and you not really understand me, I made two mockup pictures([here]("http://img163.imageshack.us/img163/7456/screenshotzp.png") and [here]("http://img221.imageshack.us/img221/9744/screenshot1kis.png")).They are only mockups that I made quickly, so I'm not saying they should look *exactly *like them, only similar. I wasn't sure if the application lists should look like the main menu, so I didn't put them like that.

Some other, minor things I think should be changed:

[LIST]
[*]No more global menu, or only on maximized applications.
[*]If not above, have it showing all the time.
[*]Assuming there is still a global menu, add dark toolbars like the ones [here]("http://cdn.omgubuntu.co.uk/wp-content/uploads/2011/05/darktoolbars-r100_thumb.jpg").
[/LIST]

---

### Post by beew on 2011-06-11
> **Hman242 said:**
> 

The menu looks like it is optimized for tablets. It takes up most of the screen. Instead of using paragraphs to explain how I think it should look and you not really understand me, I made two mockup pictures([here]("http://img163.imageshack.us/img163/7456/screenshotzp.png") and [here]("http://img221.imageshack.us/img221/9744/screenshot1kis.png")).They are only mockups that I made quickly, so I'm not saying they should look *exactly *like them, only similar. I wasn't sure if the application lists should look like the main menu, so I didn't put them like that.


What do you think of these?

[http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher](http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher)
[http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray](http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray)

I like them, I prefer to be able to access the menu without opening the dash.

---

### Post by Hman242 on 2011-06-11
EDIT: This isn't the post you're looking for. Move along.

---

### Post by arpanaut on 2011-06-11
> **Hman242 said:**
> I like that first one. I have no idea why Ubuntu won't implement a nice, normal menu like that one as default.

I may be wrong but I think that in Unity and Gnome Shell the nested menu scheme is is one of the main things that they are trying to move away from, hence the awkwardness for those who are used to and expect this scheme.  

So, I would not expect them to return by default, as the removal is by design, one who desires the nested menu would have to implement such changes themselves. 

Personal Preferences, folks, I for example find that when I boot Lucid or Maverick these days the Preferences and Administration menus to be both ugly and awkward, I find everything that I need through the lenses, after over six mo. of using Unity I find it simple and fluid. (G-shell is another matter).  But that's just me, I can see why many are finding difficulty with the changes that have come recently, but again there are options and with some effort you can have what you want, just not by default.

This is a time of transition and you can go with the flow and allow the Devs to bring us changes and improvements, or you can "hack away" with the UI and achieve what you want now. I for one find Unity quite pleasing and am willing to give the Devs the benefit of doubt and time to bring things to full fruition.

---

### Post by beew on 2011-06-11
> **arpanaut said:**
> I may be wrong but I think that in Unity and Gnome Shell the nested menu scheme is is one of the main things that they are trying to move away from, hence the awkwardness for those who are used to and expect this scheme.  

So, I would not expect them to return by default, as the removal is by design, one who desires the nested menu would have to implement such changes themselves. 

Personal Preferences, folks, I for example find that when I boot Lucid or Maverick these days the Preferences and Administration menus to be both ugly and awkward, I find everything that I need through the lenses, after over six mo. of using Unity I find it simple and fluid. (G-shell is another matter).  But that's just me, I can see why many are finding difficulty with the changes that have come recently, but again there are options and with some effort you can have what you want, just not by default.

This is a time of transition and you can go with the flow and allow the Devs to bring us changes and improvements, or you can "hack away" with the UI and achieve what you want now. I for one find Unity quite pleasing and am willing to give the Devs the benefit of doubt and time to bring things to full fruition.

I really hate the insinuation that many don't like the new design  because they are "used to the old ways" or are "afraid of change". When  you sidestep the actual usability issues and go into speculative  psychology that basically shuts down all discussions. That high handed,  patronizing approach from Canonical and the fan boyz  turns me off more  than Unity itself, whatever its merits or short comings. 

What is the point of asking for feedbacks if all negative feedbacks are dismissed a priori and categorically on the ground that they are all due to irrational attachment to the old way? [I]Why not try to make a case why the new way is better instead? 

[/I]By this kind of logic bad design is **by definition **impossible, there are only stupid users who don't appreciate the greater wisdom of the devs.

It demonstrates an arrogance that is truly annoying, we know better than of you **should **want and if you don't want it it is because you have psychological issues.

Look, there are objective ways to measure how many mouse clicks does it  take to find and open an application  or how many mouse movements you have to make and how far the mouse has to travel to get to the menu if you have several applications opened. It has nothing to do with  psychology.

Hotkeys and keyboard are not user friendly and heavy reliance on those  is a  regression to pre Windows days. who the hell would want to  memorize a bunch of random key combo to do simple task efficiently  except geeks? Normal people have better use of their brains.

As for search, this is a way to work around the cumbersome lens and dash  system, not a proof of it effectiveness. If search is all you ever use  or need why going through great length to design the cartoon menu in the  first place? All you need is something like Synapse which sits  unobtrusively on the top panel and you would never need the dash.

Moreover. you may not remember the application's name or use a name  different from what the system recognizes. e.g right after installing  WINE, type in wine in the search box turned up nothing. The keyword is  "configure wine" so you need to search for "configure" instead. It was only after a few times of opening it that the system  remembered.

---

### Post by seeker5528 on 2011-06-11
> **beew said:**
> I really hate the insinuation that many don't like the new design  because they are "used to the old ways" or are "afraid of change".

If you read very many anti-unity posts, it doesn't seem like insinuation, it seems like fact. And the people complaining that the 500 genral discussion/rant threads that have been started about it have been merged into one thread and merging them into one must be part of some kind of conspiracy doesn't lessen that impression any.

>  When  you sidestep the actual usability issues and go into speculative  psychology that basically shuts down all discussions.

If people can describe what actually makes their issue a usability issue and not a personal preference, that can be discussed.

But even then there is still going to be some amount of stuff that seems more like preference than usability.

If you look at menus/menu organization, which has been brought up as a usability issue, some of us just don't understand how the menu organization in Gnome 2/Classic/Fallback 

[img]http://home.comcast.net/~seeker5528/Screenshot-Menu2.png[/img]

is any better than in Unity. Unity-2d at the moment since compiz seems borked on my system.

[img]http://home.comcast.net/~seeker5528/Screenshot-Menu3.png[/img]

Once you mouse over a category in the classic menu or select a category in Unity, they each have their advantages and drawbacks, but nothing that makes it seem to *me* like one is more or less usable than the other. I prefer the way Unity does it, but both seem equally usable to me.

People that can provide a good description and make a case for why something is a usability issue are less likely to be brushed aside, which is not to say everybody will accept what they say without posting some opposing view point, just that there will be more of a discussion.

If people don't provide a good description at the start and later can't or won't share information that provides more clarity when others try to figure out what their issue *really* is, it makes it hard to discuss.

Later, Seeker

---

### Post by beew on 2011-06-11
> **seeker5528 said:**
> 

If you look at menus/menu organization, which has been brought up as a usability issue, some of us just don't understand how the menu organization in Gnome 2/Classic/Fallback 


is any better than in Unity. Unity-2d at the moment since compiz seems borked on my system.




I don't use Unity 2d so I have no idea how it works, I use Unity 3d on both my 11.04 installations though, so I can tell you in spite of appearance the "menu" in Unity 3d and the "classic" style menu are quite different in  functions. When you click the classical menu a submenu opens up and you can see all the applications in a glance and just click to open it, so all together 3 clicks, no scrolling, no dash to take up 3/4 of the screen, no need to click "show more". It doesn't interrupt your work flow. With the Unity "menu" you click a category and open the dash, which rudely intrudes into the desktop by taking up 3/4 of screen space to the whole screen, interrupting whatever you are doing, then if you have installed a lot of applications not all of them will show and you have to click "show more" and then you have to scroll and wade through the icons to find the application and click. 

So how are they the same thing? Unity works faster only for the few applications you use all the time, in that case you can find them right the way because the system remembers them. But for those you can simply put them on the dock any way.

---

### Post by ronacc on 2011-06-11
You are quite right , many find unity quite usable and pleasing , others not so . I will try to state one of my reasons for preferring the gnome2 panels/menus to the way unity does things . I find the launcher esthetically unpleasing , also its placement is not what I would prefer , I dislike ANY dock on the side of my screen and am not a user of docks in general .I do not like the way "activities" takes up a large strip of the top left corner ( gnome-shell does this also) . This is where I place my close button and a minute overshoot on a maximized window causes disconcerting things to happen . I realize these are personal preferences but they are sufficient to prevent me from using unity .

---

### Post by beew on 2011-06-11
I like docks, I use a dock in 10.04 and 10.10, but the Cairo dock is so much more flexible and sophisticated comparing to Unity's offer and as others have said Unity is not flexible by design, so basically they want to impose their aesthetics on you and then get pissed off when being told that you don't like their design. Instead of acknowledging  that the user may actually have a point and know what he is talking about, the immediate reaction is defensiveness and insistence that their choice is more logical and better and you are irrational ("fear of change")if you disagree. That is quite insulting actually.

---

### Post by Hman242 on 2011-06-12
The new menu just takes up way to much space, while not really offering  much on the screen. There are only eight buttons on the menu and it fills the majority of it.  Why? That is a huge waste of space. That isn't optimized for a  desktop/laptop screen at all. They need to change it so it offers plenty  in the space given.
> **beew said:**
> I really hate the insinuation that many don't like  the new design  because they are "used to the old ways" or are "afraid  of change". 
I couldn't agree more.

I also don't like how the application lens and the drop-down menu in the main menu have all application categories, instead of only showing the ones that you have apps of.

---

### Post by jerrylamos on 2011-06-12
Ditto on entry #151 above.  System Applications comfortably lists lots more on the screen than the few huge big "Egyptian Hieroglyphs" scattered across the screen.  The "pictures" don't mean a thing to me and get in the way of reading the texts.  The Phoenicians knew what they were doing....

Jerry

---

### Post by dyltman on 2011-06-12
> **Hman242 said:**
> The new menu just takes up way to much space, while not really offering  much on the screen. There are only eight buttons on the menu and it fills the majority of it.  Why? That is a huge waste of space. That isn't optimized for a  desktop/laptop screen at all. They need to change it so it offers plenty  in the space given.

You can decrease the size of the dock if you want to.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
> **cntrational said:**
> Have a list of open windows pop up when you hover over an icon in the launcher, [similar to what Windows 7 does.]("http://media.arstechnica.com/images/windows7/Windows%20Taskbar%20Previews.png")
please don't that drives me crazy i prefer that feature the way it is in gnome 2 with compiz be nice if they worked when the app in minimized though

main things i would like to see in unity (aside from performance improvements) would be movable applets
i need to put my sensors and cpu scaling applets somewhere
[IMG]http://i54.tinypic.com/2z6v6zp.png[/IMG]
i prefer my close,minimize,maximize buttons on the right like windows though

to me the full-screen app menu is fine if it was just organized more like the gnome 2 menu (same categorizes)

i have used unity under 30 minutes for the record i am sticking with my lucid LTS for now

after thought:
would be cool if Oneiric Ocelot has a Ocelot theme (spotted panels, ocelot watermark in the full screen app menu, ocelot wallpaper, etc

---

### Post by ronacc on 2011-06-12
google ocelot wallpaper , you'll find a nice selection .

---

### Post by Hman242 on 2011-06-12
> **dyltman said:**
> You can decrease the size of the dock if you want to.
I'm talking about the menu, not the launcher.

---

### Post by danielbu on 2011-06-13
Drag and drop in the Unity panel. That's all I want.
And how do I configure the notifications?

---

### Post by SteveHillier on 2011-06-13
I don't know if this has been said.
I am beginning to dislike this Unity stuff.  It is holding back my productivity.
I am using a browser, ftp client, editors, and a number of nautilus windows.
I want to restore say my ftp client.  It is not at the bottom of the screen as I am used to but the Unity bar is not showing.
I click on the Ubuntu logo to restore Unity but it comes up in grey with the expanded menu showing.  I now have to click in the Unity bar to make it active.  Then I can click on the icon I want to restore.
4 clicks when one would do if the damn bar did not keep hiding itself.

Aaaarrrrggghhhhhh.:mad:

---

### Post by arpanaut on 2011-06-13
Don't click on the logo just move the pointer to the far left and up to the top. The launcher will reveal itself click on the icon you desire.

Install ccsm and configure the reveal mode as desired. other options are available in the Unity plugin in ccsm.
That should help a bit.  

Have you seen this:
[http://ubuntuforums.org/showthread.php?t=1742326](http://ubuntuforums.org/showthread.php?t=1742326)

---

### Post by DinoT1985 on 2011-06-14
> **Hman242 said:**
> I'm talking about the menu, not the launcher.
you mean Dash? they definitely need to allow size changes for icons and Dash itself.

---

### Post by Hman242 on 2011-06-14
EDIT: This is not the post you're looking for.

---

### Post by cariboo on 2011-06-15
Because of all the extra noise on the forums, the developers very rarely look here. They'll answer if there is a specific issue with a package they're working on, but the forum is the wrong place to offer feedback on over all design and implementation.

The various mailing lists and Launchpad bugs are better places to offer feedback.

---

### Post by DinoT1985 on 2011-06-15
> **Hman242 said:**
> No... I mean the launcher. You know, the bar on the left side of the screen?

Also, does anyone know if any of this will be viewed by any developers, or anyone of the sort?
Then the guy you quoted was correct. The icons can be resized.

on a 1440x900 res.
[http://s4.postimage.org/3zds10ogs/Workspace_1_003.png](http://s4.postimage.org/3zds10ogs/Workspace_1_003.png)

---

### Post by CreativeReach on 2011-06-15
They are really easy to resize in compiz, under unity plugin,then experimental.

---

### Post by SteveHillier on 2011-06-15
> **arpanaut said:**
> Don't click on the logo just move the pointer to the far left and up to the top. The launcher will reveal itself click on the icon you desire.

The point is that on my system simply hovering at the top left does not reveal the launcher.  A half greyed out launcher sort of half appears and immediately disappears if I try to move the cursor onto it.

---

### Post by cariboo on 2011-06-15
> **SteveHillier said:**
> The point is that on my system simply hovering at the top left does not reveal the launcher.  A half greyed out launcher sort of half appears and immediately disappears if I try to move the cursor onto it.

That's normal behavior if you don't but he mouse cursor right in the top left corner. You can also reveal the Launcher if you hold your mouse against the left side. You can change the settings using compiz-config settings manager, it's in the repositories.

---

### Post by Hman242 on 2011-06-16
> **DinoT1985 said:**
> Then the guy you quoted was correct. The icons can be resized.

on a 1440x900 res.
[http://s4.postimage.org/3zds10ogs/Workspace_1_003.png](http://s4.postimage.org/3zds10ogs/Workspace_1_003.png)
Sorry, I didn't mean to post that. I misread the quote and thought we were talking about something else. Yes, I meant the dash. I have a habit of calling it the menu. I don't want to be able to just change the icons and the size of the dash, I was suggestion a whole new dash layout. The current one is just way to unoptimized for any laptop/desktop screen.

---

### Post by SteveHillier on 2011-06-16
> **cariboo907 said:**
> That's normal behavior if you don't but he mouse cursor right in the top left corner. You can also reveal the Launcher if you hold your mouse against the left side. You can change the settings using compiz-config settings manager, it's in the repositories.

Thank you Cariboo for your help.  Yes I have managed to achieve what you have said in part (the holding the mouse on the left side I cannot achieve) but it was not easy.
I give you this thread [http://ubuntuforums.org/showthread.php?t=1747155]("http://ubuntuforums.org/showthread.php?t=1747155") in which I have dropped a screen shot of my set up I think you will see why.
I can if I am very slow and deliberate get to the very top left of the button but if I go one pixel over and the cursor moves to my left screen it all goes, and this is why holding the mouse to the left side doesn't work either.

---

### Post by cariboo on 2011-06-16
> **SteveHillier said:**
> Thank you Cariboo for your help.  Yes I have managed to achieve what you have said in part (the holding the mouse on the left side I cannot achieve) but it was not easy.
I give you this thread [http://ubuntuforums.org/showthread.php?t=1747155]("http://ubuntuforums.org/showthread.php?t=1747155") in which I have dropped a screen shot of my set up I think you will see why.
I can if I am very slow and deliberate get to the very top left of the button but if I go one pixel over and the cursor moves to my left screen it all goes, and this is why holding the mouse to the left side doesn't work either.

You can change where the panel is activated in compizconfig-settings manager, see the screen shot:

---

### Post by seeker5528 on 2011-06-16
> **cariboo907 said:**
> You can change where the panel is activated in compizconfig-settings manager, see the screen shot:

Did you try it? The reveal only works from the left for me, it can be the top or bottom corner, but if I set it to only the corners only the left edge of the corners work for me.

> **SteveHillier said:**
> I can if I am very slow and deliberate get to the very top left of the button but if I go one pixel over and the cursor moves to my left screen it all goes, and this is why holding the mouse to the left side doesn't work either.

If you want to keep the auto hide behavior enabled, using the keyboard to reveal the launcher is the other option, 'Alt'+'F1' works, or hold down the super key if that is more convenient or while holding down the super key hit one of the numbers or letters that appear on one of the launcher icons.

Later, Seeker

---

### Post by cariboo on 2011-06-17
It doesn't work for me either on my freshly installed netbook, or my week old desktop install. I created Bug #[lpbug]798525[/lpbug]

---

### Post by mc4man on 2011-06-17
> **cariboo907 said:**
> It doesn't work for me either on my freshly installed netbook, or my week old desktop install. I created Bug #[lpbug]798525[/lpbug]

The reveal, (left edge or left bottom corner) don't have a 'lock point', the only reason the the launcher stays exposed is because of 'cursor over launcher'

The default upper left area does contain a lock point (2x2 or 3x3 px. I forget (meaning 'lock' in relation to the slide/fade function

The default is launcher hide 1 sec after cursor leaves launcher or the BFG area  so you'd need to move quickly if reveal was elsewhere

---

### Post by cariboo on 2011-06-17
There are 8 different areas that you are supposed to be able to set to reveal the launcher, the only ones that work consistently on my system are top left, and left side. If things work propeerly, I should be able to change it to any of the sides or corners as set out in my screenshot from post [#169]("http://ubuntuforums.org/showpost.php?p=10947483&postcount=169")

Link to the [screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=195292&d=1308260582")

---

### Post by mc4man on 2011-06-17
> **cariboo907 said:**
> There are 8 different areas that you are supposed to be able to set to reveal the launcher, the only ones that work consistently on my system are top left, and left side. If things work propeerly, I should be able to change it to any of the sides or corners as set out in my screenshot from post [#169]("http://ubuntuforums.org/showpost.php?p=10947483&postcount=169")

Link to the [screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=195292&d=1308260582")
I understand that but if you for instance set right edge reveal you'd have a bit less than 1 sec to move the cursor over the launcher before it hid again 
(the launcher hide delay isn't configurable though it could be, likely the idea would run afoul of the 'design(team'

The one thing that comes is when left edge reveal is disabled there is a 1 px or so area to left of the launcher that is not considered 'cursor over launcher', so anyone that tends to keep cursor against the screen edge should leave l.edge enabled

The bottom left corner should work - the top left area is always active no matter what.

I believe the option's 'set' screen is just a generic compiz screen, not that it actually reflects what's available

---

### Post by Jacobonbuntu on 2011-06-17
Haha, this is funny (I am not being cynical, I really think it's funny).

When Unity was introduced, We all wrote extensive stories about "what I like...."/"what I don't like".....
Now we've done that, we will all move on to "what should be improved" -section which probably will be a 1:1 conversion of the first chapter.

I like this forum (seriously), we should make a movie some day\\:D/


sorry for the interuption, please continue....:)

---

### Post by seeker5528 on 2011-06-17
> **Jacobonbuntu said:**
> When Unity was introduced, We all wrote extensive stories about "what I like...."/"what I don't like".....
Now we've done that, we will all move on to "what should be improved" -section which probably will be a 1:1 conversion of the first chapter.

What's happening with Unity right now is really similar to what happened with Amarok when Amarok 2.0 was introduced.

Written from scratch, with some different ideas on what should be provided and how.

In that situation it's a given that initially there will be a bunch of complaints with no suggestions on how it could be improved just because it doesn't provide what people have been used to.

It's also a given that there will be people that complain because of what it doesn't do relative to what they are used to and make suggestions based on that without taking in to account what the priorities are relative to where the project is at in it's development or if their suggestions make sense relative to the way the new design works and what the goals of the developers are that led to the new design being introduced in the first place.

Once you get past that initial phase and you start to get more people that accept the situation for what it is, you start to get a better ratio of good suggestions versus random complaints and suggestions that don't fit the design.

That's not to say there won't still be plenty of arguments over what *does* make sense. That's just the nature of the game. :P

Later, Seeker

---

### Post by Jacobonbuntu on 2011-06-17
> **seeker5528 said:**
> What's happening with Unity right now is really similar to what happened with Amarok when Amarok 2.0 was introduced.

Written from scratch, with some different ideas on what should be provided and how.

In that situation it's a given that initially there will be a bunch of complaints with no suggestions on how it could be improved just because it doesn't provide what people have been used to.

It's also a given that there will be people that complain because of what it doesn't do relative to what they are used to and make suggestions based on that without taking in to account what the priorities are relative to where the project is at in it's development or if their suggestions make sense relative to the way the new design works and what the goals of the developers are that led to the new design being introduced in the first place.

Once you get past that initial phase and you start to get more people that accept the situation for what it is, you start to get a better ratio of good suggestions versus random complaints and suggestions that don't fit the design.

That's not to say there won't still be plenty of arguments over what *does* make sense. That's just the nature of the game. :P

Later, Seeker

You are absolutely right, and this section *is *actuallydifferent from the "first chapter"; it is just a funny situation that I pictured.

have a good time!
Jacob

---

### Post by Bazon on 2011-06-25
> **Bazon said:**
> 
* Quick look in a window and then minimize it again
Worked before with pressing the window switcher two times (show – minimize) and was very useful and a very common practices. Doesn’t work any more with the Unity launcher:
[https://bugs.launchpad.net/ayatana-design/+bug/733349](https://bugs.launchpad.net/ayatana-design/+bug/733349)


After various status changes and nearly 100 "affects me, too", this bug is now a "won't fix".
:-( :-( :-(

---

### Post by mc4man on 2011-06-25
> **Bazon said:**
> After various status changes and nearly 100 "affects me, too", this bug is now a "won't fix".
:-( :-( :-(

I believe you're referring to an issue that was addressed in a commit but the request to merge was rejected somewhat out of hand (not part of design
There was a request to reconsider - I haven't checked to see what's happened, if again rejected it's unfortunate, works quite well and would suit many users

(have been patching the unity-3.X to use for some time, redid that patch for unity4 which works fine here - whether unity4 will continue to be 'patchable' down the road is unknown
screen shows option (patch avail. for current unity3 or unity4 by request

---

### Post by SevenMachines on 2011-06-25
its a little disappointing that at least allowing access to some minor tweaks is a design decision. i've been using a couple of patches to allow changing the launcher hide delay time and disabling it hiding on 'activating' an icon. makes unity a much nicer thing for me just with a couple of small options. i'm sure others have their own little minor tweaks that make a big difference for them, just small things, changing the odd small default value and so on, it doesnt seem like a massive design violation to allow things like this.

---

### Post by CreativeReach on 2011-06-25
> **mc4man said:**
> I believe you're referring to an issue that was addressed in a commit but the request to merge was rejected somewhat out of hand (not part of design
There was a request to reconsider - I haven't checked to see what's happened, if again rejected it's unfortunate, works quite well and would suit many users
(have been patching the unity-3.X to use for some time, redid that patch for unity4 which works fine here - whether unity4 will continue to be 'patchable' down the road is unknown
screen shows option (patch avail. for current unity3 or unity4 by request

glad to see at least the option in Unity4!

---

### Post by JM68 on 2011-06-25
The best way to improve Unity is erase all the source code and dump the project. Unity is Ubuntu killer (read: not a killer application - The distro killer)

I've used Ubuntu since 6.04 and I've love it - until 11.04 game out.  I just hate Unity. There is no single thing what I liked. So next thing to do is waste the unity idea and go back to pure Gnome.

---

### Post by 23dornot23d on 2011-06-25
> 
The best way to improve Unity is erase all the source code and dump the  project. Unity is Ubuntu killer (read: not a killer application - The  distro killer)
Needs a white board .... they build bad on bad ..... it gets worse not better .....

If we need to use the keyboard .... what is the point in a Graphical User Interface ....

Might as well work from a terminal if all the commands are done without the need of a mouse.

Take away the dock on the left all that is left is compiz anyway ..... :confused:

Cairo-dock + blank desktop is faster easier to use ......... and takes up less resources.

Plus the dock actually moves resizes and allows different effects and icons .... plus detachable launchers too.

So how to improve UNITY ..... maybe the dock needs to be rigid and square blocks and not move .....

Hey you have it .... no need to change anything ......

---

### Post by seeker5528 on 2011-06-25
> **23dornot23d said:**
> If we need to use the keyboard .... what is the point in a Graphical User Interface ....

Just because there are some more obvious/discoverable ways to use the keyboard to increase efficiency doesn't mean you *have* to use the keyboard.

I don't use the keyboard that much for common desktop/window navigation.

Now that there is a search in the dash I find myself not only using that but using 'Alt'+'F2' to get a run box more than I have in the past, but often I'm just as likely to open a terminal window. 

I don't use these things because I necessarily *need* to, I just find the stuff that has always been quicker to use the keyboard is still quicker to use the keyboard, the stuff that has always shown up in the menu with a different name than the program name, still shows up in the menu with a different name than the program name, different programs that have commonly if not always shown up in the menu with the same name still show up in the menu with the same name, etc...  

> Might as well work from a terminal if all the commands are done without the need of a mouse.

Often it's quicker for me to open a terminal window, type a command, and use tab completion to help fill out the path to some file somewhere that I want to load.

That doesn't mean I don't want to have the option to open a file manager, browse to a file, then use 'Open' or 'Open With' to view files.

Even in Windows the command line is preferred some times for example ```
netsh int ip reset c:\windows\reset.log
netsh firewall reset
netsh winsock reset
```

compared to finding where you have to go in the GUI and hoping the theoretically equivalent GUI option actually accomplishes the same thing.

Later, Seeker

---

### Post by 23dornot23d on 2011-06-25
> 
Now that there is a search in the dash I find myself not only using that  but using 'Alt'+'F2' to get a run box more than I have in the past, but  often I'm just as likely to open a terminal window. 
Me too plus the use of .....  CTRL + ALT + T ...... ( for the Terminal )

ALT + F2 is good if it has not been changed to switch workspaces ......

I have had a couple of instances now  where its needed resetting to input commands .....

also 

***[ALT + K + Sysreq]("http://en.wikipedia.org/wiki/Magic_SysRq_key")***   ( to kill the X window .... )

Funny what  I have learned with the use of UNITY ......

---

### Post by doublewitt on 2011-06-25
> **JM68 said:**
> The best way to improve Unity is erase all the source code and dump the project. Unity is Ubuntu killer (read: not a killer application - The distro killer)

I've used Ubuntu since 6.04 and I've love it - until 11.04 game out.  I just hate Unity. There is no single thing what I liked. So next thing to do is waste the unity idea and go back to pure Gnome.

The most important thing worthy of discussion about Unity and the next release is to consider giving us the OPTION to turn it ON or OFF - give us the switch. The current "dictator" style is not the way to go. If you grant the OPTION to use Unity instead of IMPOSE it, you're in a safe zone, but when you FORCE the issue, you're in a danger zone.

Your desktop is YOUR world - not theirs. Their approach is a complete invasion of user privacy.

There is no better solution to anything (in the software world) than customization. Ofcourse some might disagree with that, but the truth is, we all have different ways to set up our desktop because we all have different needs, etc.

I don't need anybody forcing me to do things "their" way - what nonsense! And the truth is, is that UNITY is dis-uniting us.... many are leaving Ubuntu because of it...

There's nothing wrong with delving into new ideas & approaches - but geez, introducing it in dictator style is just pushing people away...

---

### Post by Alwimo on 2011-06-25
Interactions with the windows when you select a program from the launcher that has multiple windows open needs to improve. Being able to close a window from this view, like GNOME Shell allows, would greatly improve the feel of this aspect of Unity.

---

### Post by seeker5528 on 2011-06-25
> **doublewitt said:**
> The most important thing worthy of discussion about Unity and the next release is to consider giving us the OPTION to turn it ON or OFF - give us the switch. The current "dictator" style is not the way to go. If you grant the OPTION to use Unity instead of IMPOSE it, you're in a safe zone, but when you FORCE the issue, you're in a danger zone.

Sorry you have somebody standing over you, forcing you to use Unity.

I have several options available to me at login time, Gnome, Gnome Classic, Ubuntu, Ubuntu 2d, Lubuntu, Kubuntu, Fluxbox, etc..., nobody forcing me to choose one over another, all depending on what I started with and what I chose to install on a given machine.

Adding the Gnome desktop stuff to the default Ubuntu install, shouldn't be much of an ordeal, outside of the normal packaging/version issues when there are significant changes that affect groups of packages in the repositories.

Later, Seeker

---

### Post by cariboo on 2011-06-26
I agree with everything seeker5528 has said, the only thing Unity is doing, is maybe forcing you out of your comfort zone to learn new ways of doing things, and maybe actually learning how to use Ubuntu/Linux better.

---

### Post by beew on 2011-06-26
> **cariboo907 said:**
> I agree with everything seeker5528 has said, the only thing Unity is doing, is maybe forcing you out of your comfort zone to learn new ways of doing things, and maybe actually learning how to use Ubuntu/Linux better.
Enough of the mindless cheer leading. Yes it is out of many people's comfort zone but how is it better? People are talking about a very specific missing feature here, namely the inability to minimize windows with the launcher whereas other docks can do it easily.

Can you people actually address the specific usability issues raised instead of insinuating the critics are all suffering psychological issues ("fear of change" or something to that effect)? Most of these people have left the "comfort zone" of Windows to switch to Linux and care enough to file and initiate bug reports and feature requests so stop patronising them already, this is not the way to have a discussion.

Personally I don't hate Unity that much, with some customization and  third party tweaks (and am sure more will be coming, I don't even bother to file useless requests at launchpad seeing how they are shot down and dismissed every step of the way) it is actually pretty sweet, all my Natty installs run Unity instead of the Classic Desktop,  but it is the mindless cheerleading of Canonical employees/fanboyz /would be re-education camp guards that really turns me off.

---

### Post by JM68 on 2011-06-26
> **doublewitt said:**
> The most important thing worthy of discussion about Unity and the next release is to consider giving us the OPTION to turn it ON or OFF - give us the switch. The current "dictator" style is not the way to go. If you grant the OPTION to use Unity instead of IMPOSE it, you're in a safe zone, but when you FORCE the issue, you're in a danger zone.

Your desktop is YOUR world - not theirs. Their approach is a complete invasion of user privacy.

There is no better solution to anything (in the software world) than customization. Ofcourse some might disagree with that, but the truth is, we all have different ways to set up our desktop because we all have different needs, etc.

I don't need anybody forcing me to do things "their" way - what nonsense! And the truth is, is that UNITY is dis-uniting us.... many are leaving Ubuntu because of it...

There's nothing wrong with delving into new ideas & approaches - but geez, introducing it in dictator style is just pushing people away...

Oh - so true ! Unity lovers should do 2xUbuntu version and leave Gnome Ubuntu as it is in Gnome world. Forcing to use Unity just sucks. So far any of my Ubuntu user friends like it - they all hate it. I tryed to study and get used to it, but no luck. Unity is useles on big flat screens 22''- or bigger. I have 27'' screen and Unity is just totally mess. Global menu is totally useless idea. Thats something for small screens and tablets, but no way in any normal laptop or desktops.

But if thos is the way Ubuntu wants to work - Ubuntu is not for me and it's time to move on to new distro. Sadly I must say this but there is no other way. Ubuntu staff should figure out this fact fast or they will mess up the Ubuntu community for good. 11.10 without Unity default GDM please! Make it option but not default.

---

### Post by jerrylamos on 2011-06-26
> **JM68 said:**
>  Unity is useles on big flat screens 22''- or bigger. I have 27'' screen and Unity is just totally mess. Global menu is totally useless idea.

Well this is a netbook 1024x600 using Unity 2D perched on the breakfast table.  For what I do, internet browse news email health research, word processing, calc, sharing files over my home net, etc. I'm able to use Unity 2D.  Just got a notebook 1366x768 works O.K. too.  We don't do games.

Biggest screens I use are 1280x1024 and 1440x900.  I don't know what the usual screen size is out there for the prospective linux users.

Now there's a number of things I haven't figured out how to do with Unity 2D, I tackle them one at a time going back to Meerkat or Lynx.  And there's always the command line with help from "Ubuntu Tools" book.

I don't know what a "Global Menu" is.  I switch between full screen applications with Alt-Tab just like I always used to.

Oh, yes, I'm looking for OO bugs.  Right now I can't get network to share files with OO.  Some complaint about a "share list"?  I'm rebooting to Narwhal for that or email myself. Lightdm crashes too.

Biggest complaint on all the "Unity Ancient Hieroglyphics Picture Symbols" is they use up tons more screen space than actual alphabetically sorted names.  Information density is very very low.  Just like "Windoze" and "Apple".  We started with pc's in 1982, and on my son's and daughter's Mac's there's a lot of things my wife and I can't figure out how to do, distinctly worse than Unity 2D.

Should be all about choices.  I have Lynx, Meerkat, Narwhal, and Ocelot on my various test pc's so I use whatever.

On one pc I've got Slax, Fedora, Suse, Debian (yes it's a big hard drive) none of which I've used for months.  I've tried some other Ubuntu take-offs in the past.

Oh I forgot.  For quick internet access Tiny Core can't be beat among them.  It sits in a folder on one of the Ubuntu partitions and fires up fast running entirely within memory.

Jerry

---

### Post by cariboo on 2011-06-26
> **JM68 said:**
> Oh - so true ! Unity lovers should do 2xUbuntu version and leave Gnome Ubuntu as it is in Gnome world. Forcing to use Unity just sucks. So far any of my Ubuntu user friends like it - they all hate it. I tryed to study and get used to it, but no luck. Unity is useles on big flat screens 22''- or bigger. I have 27'' screen and Unity is just totally mess. Global menu is totally useless idea. Thats something for small screens and tablets, but no way in any normal laptop or desktops.

But if thos is the way Ubuntu wants to work - Ubuntu is not for me and it's time to move on to new distro. Sadly I must say this but there is no other way. Ubuntu staff should figure out this fact fast or they will mess up the Ubuntu community for good. 11.10 without Unity default GDM please! Make it option but not default.

Nobody is forcing you to use Unity, it is installed by default, but you can change it as soon as the installation process is finished. 

I'm not sure if you realize, but the two panel interface as you know it, is gone, gnome-shell fallback mode has replaced it.

The name of this thread is **Improving Unity** if you don't have suggestions to improve it, don't post in this thread. There are enough threads in the Cafe, where you can express your opinion. Could we please stay on topic.

---

### Post by kansasnoob on 2011-06-26
> **cariboo907 said:**
> Nobody is forcing you to use Unity, it is installed by default, but you can change it as soon as the installation process is finished. 

I'm not sure if you realize, but the two panel interface as you know it, is gone, **[COLOR="Red"]gnome-shell fallback mode has replaced it[/COLOR]**.

The name of this thread is **Improving Unity** if you don't have suggestions to improve it, don't post in this thread. There are enough threads in the Cafe, where you can express your opinion. Could we please stay on topic.

In some ways just saying, "gnome-shell fallback mode has replaced it", can be misleading. Neither classic or gnome-shell are available in Oneiric w/o installing an additional package :)

But I honestly wonder if we're doing right by everyone w/o a more thorough explanation of DE's available :confused:

I'm quite tied up ATM (problems, problems, problems) but every time I happen to look we're still besieged with the "I hate/love unity/gnome3/gnome-shell" comments and our answer is either to agree loudly, disagree loudly, or kill the thread :(

I'd think someone, obviously someone smarter than me, could come up with a "boiler plate" message regarding the DE's available:

Unity
Gnome-shell
Gnome-fallback
LXDE
Xfce
KDE
etc, etc............

And maybe each DE could hook to a link regarding that specific DE. Just a thought, I still love Ubuntu, but ATM Lubuntu is the better choice for me.

No need to stomp my feet, or scream and yell, and no need to apologize ............. Lubuntu is simply more intuitive to me ATM :)

---

### Post by cariboo on 2011-06-26
> **kansasnoob said:**
> In some ways just saying, "gnome-shell fallback mode has replaced it", can be misleading. Neither classic or gnome-shell are available in Oneiric w/o installing an additional package :)

But I honestly wonder if we're doing right by everyone w/o a more thorough explanation of DE's available :confused:

I'm quite tied up ATM (problems, problems, problems) but every time I happen to look we're still besieged with the "I hate/love unity/gnome3/gnome-shell" comments and our answer is either to agree loudly, disagree loudly, or kill the thread :(

I'd think someone, obviously someone smarter than me, could come up with a "boiler plate" message regarding the DE's available:

Unity
Gnome-shell
Gnome-fallback
LXDE
Xfce
KDE
etc, etc............

And maybe each DE could hook to a link regarding that specific DE. Just a thought, I still love Ubuntu, but ATM Lubuntu is the better choice for me.

No need to stomp my feet, or scream and yell, and no need to apologize ............. Lubuntu is simply more intuitive to me ATM :)

I'm of two minds on this one, on the one hand, many of the users don't like the amount of hand holding Ubuntu is doing, and on the other hand with the amount of new users trying Ubuntu, we should be telling them what other choices they have if they don't like Unity. My personal feeling is that most new users will either like Unity well enough to use it, or give up on Linux completely. There are way to many people out there that think Ubuntu=Linux.

I'll start a sticky in the next day or two with a few of the other desktop choices that are available, I'll leave it open so other can add their favorites to the list.

Quit apologizing for using Lubuntu, if it works better for you, by all means use it, it needs just as much testing as the other members of the Ubuntu family. We seem to spend way more time testing Ubuntu to the detrement of the others, Kubuntu, Xubuntu and Lubuntu need some loving too.

---

### Post by jerrylamos on 2011-06-27
> ...Lubuntu, if it works better for you, by all means use it, it needs just as much testing as the other members of the Ubuntu family. We seem to spend way more time testing Ubuntu to the detriment of the others, Kubuntu, Xubuntu and Lubuntu need some loving too.
Cariboo,  
I couldn't agree more.  Right now as a tester of a Ubuntu new development release as it comes out of the box as a new person might try it, so that's Unity.  My viewpoint is "Ordinary User" with internet browse including video, internet email, write, sharing files with my wife's Windoze (sharing is busted on OO right now), ...  She supports some websites with Dreamweaver etc. which are not available on Ubuntu. 

I haven't stopped to figure out how a new user would know to install flashplugin, samba, synaptic, ...

For the more experienced there are more choices such as you mention Lubuntu, Kubuntu, Xubuntu, (Gnome classic??), I don't know a thing about Gnome 3 whatever that is.  So an experienced user can boot up OO and then install whatever they prefer.  

As fewer things break - right now with daily build live a simple terminal command "df" or "cd" can crash lightdm with not even a crash report - I'll give a try for Lubuntu etc.  I was using it O.K. earlier when it had some rough corners.  

I just added a new notebook with amd64 so I'm trying that including how those restricted drivers install and what do they do, Broadcom wireless etc. 

For utility work like zsync I may boot Lucid Lynx (fast!) and since I've been on Ubuntu since Dapper Drake Beta (easy!) but then right back in to figuring out how do I use Unity to get something done.  Biggest rub is the lightdm crashes which I assume will get fixed?

The one thing I would like and am never likely to see is Unity without the pictures.  I can read.  I can use a keyboard and a mouse, I don't need "ugh me point" smeared touch screen.  With all the pictures gobbling up screen real estate there are very few applications listed per screenful.  But I have a choice, I'll give one of the other flavors a whirl.  Do note with Windoze and Mac I don't think I have choices and for me, Unity is easier than Windoze or Mac. 

Jerry

p.s. Biggest Ubuntu feature for me is the forums...

---

### Post by johnnybelfast on 2011-06-27
Fragmentation can be a good or a bad thing. To me the DE is just a sort of browser. Maybe a tour of various DE's would be a nice thing. I remember on windows there was a 'choose your browser' screen which was really good at informing even the most novice of users that there were alternatives available. Maybe a similar choose your DE screen could be included in Ubuntu, with detailed tours, reviews and pros and cons of each of the DE's available. Then the user can choose one (or more) based on his/her preference. This would have to be at run-time rather than wasting much needed space on the cd. If anyone wants to turn this into a project I'm more than willing to help.

---

### Post by PaulW2U on 2011-06-27
> **cariboo907 said:**
> We seem to spend way more time testing Ubuntu to the detrement of the others, Kubuntu, Xubuntu and Lubuntu need some loving too.

Quite. In the first three pages of threads in this forum I see just one thread specific to Lubuntu and one thread specific to Xubuntu, nothing specific to Kubuntu although some threads will of course apply to all versions of the Ubuntu family.

Anyway, this is off-topic. The thread is supposed to be about _improving_ Unity.

---

### Post by beew on 2011-06-27
> **jerrylamos said:**
> 
Biggest complaint on all the "Unity Ancient Hieroglyphics Picture Symbols" is they use up tons more screen space than actual alphabetically sorted names.  Information density is very very low.  Just like "Windoze" and "Apple".  We started with pc's in 1982, and on my son's and daughter's Mac's there's a lot of things my wife and I can't figure out how to do, distinctly worse than Unity 2D.


[http://www.ubuntu-corner.com/2011/06/classic-menu-in-unity-classicmenu-indicator-and-cardapio/](http://www.ubuntu-corner.com/2011/06/classic-menu-in-unity-classicmenu-indicator-and-cardapio/)

I doubt that making feature suggestions here or Launchpad would get you anywhere. Even simple and reasonable suggestions like adding minimizing function to the launcher got shot down (not because of technical infeasability or they have their plate too full, but somehow it runs against the "Unity experience") Canonical's attitude seems to be my way or the high way, and as a bonus you get lectured by the fanboyz that you think Unity needs "improvements" other than bug fixes because you are an old foggy too afraid of change.

 I am not even wasting my time. If you want to see improvements it is going to be from third party. 

Don't know if you mean Unity 2D or 3D, these work for Unity 3D . I am not sure why you spend so much time on Unity 2D. I have run Unity 3D on a 6 year old Dell D410 (all round crappy laptop) with no issue and it definitely runs faster than 10.04 and leaves XP (which is deleted now) in the dust.

---

### Post by kvv_1986 on 2011-06-27
> **beew said:**
> and as a bonus you get lectured by the fanboyz that you think Unity needs "improvements" other than bug fixes because you are an old foggy too afraid of change.


Hehe.. "Unity is the future of desktop computing!!11 Keep up with the trends oldie!!" And I am not even 25 yet. :p

> **cariboo907 said:**
> the only thing Unity is doing, is maybe forcing you out of your comfort zone to learn new ways of doing things, and maybe actually learning how to use Ubuntu/Linux better.
Please don't encourage people to use Unity by saying this. Unity is just a shell running on Ubuntu, and doesn't teach you to use Ubuntu or Linux(lol) better.


> **seeker5528 said:**
> Adding the Gnome desktop stuff to the default Ubuntu install, shouldn't be much of an ordeal, outside of the normal packaging/version issues when there are significant changes that affect groups of packages in the repositories.

I am currently running Fedora 15 with gnome fallback mode. Outside of the serious bugs and lack of applets it is very much similar (and in some cases better) than vanilla gnome 2. The bugs will be resolved and applets will start coming out. If you don't want to bother tweaking with gnome fallback mode yourself, you could always change to Linux Mint when it comes out.
Or move to xfce. No point in complaining about shift to cellphone desktops.

As for improvements in Unity, I have a lot of problems with the interface. Last I checked on Launchpad, other people had already reported the "bugs", but they were marked as low priority and "needs design", and barely saw any activity.

---

### Post by Jacobonbuntu on 2011-06-27
....I really tried to find out if these issues were mentioned before, but the thread is a bit messed up :-\", hard to read it/at all.... 

 here it is:
 In general I like the Unity- idea, nice and &#8220;sober&#8221;in the right way. I really like the cross-workspaces- kind of expo of the application windows, and some other nice features.
However, at this stage of development, a few inconsistencies and unfinished stuff should be taken care of, I believe.
 
[LIST]
[*]The system menu and the global menu of the running (top) application are kind of in each others way; if you are in the application's menu, there is no proper way to switch quickly to the system menu as far as I can see. I took care of it through Compiz (right-bottom =show desktop / left-bottom =show workspaces)
[*]for the same reason the &#8220;locations&#8221; menu of the system is not really quickly accessible if you are working in &#8220;fast-working&#8221;-mode. The nice &#8220;add bookmark&#8221; feature is a bit lost this way.
[*]This kind of entrances should not be placed in the top bar any more, for it is used by the global (application) menu. Instead, the functionality of the launcher bar should be made easily configurable. Adding buttons and modifying their functionality should be easy and intuitive, and having many various abilities.
[*]The lenses and the personal folder button should be protected against removal. Beginners don't know where to begin if these are removed by accident.
[*]There is a bit of an inconsistent functionality between the application lens and the files&folders lens; while the application lens is showing all there is on the computer (and even what is not/not yet 8)), by typing (part of)the name, typing the name of a document in the files&folders lens only shows..., yes what is it showing anyway? It should be configurable what it shows (as a result of typing) and where it looks.
[/LIST]
       The question for a *minimize application window* -functionality of the launcher buttons I do not understand; using the &#8220;-&#8221;at the window corner makes more sense to use; it is always at the same place of the window, unlike the launcher icon of the application.

---

### Post by kansasnoob on 2011-06-27
A quick bit of clarification before I return to cleaning up storm damage here:

1) I was not apologizing for using Lubuntu as an alternative, just pointing out that the use of any official Ubuntu derivative makes you a member of the Ubuntu community.

2) Even if you use an unofficial Ubuntu derivative or "respin", if it's based on Ubuntu, you're still part of the family.

3) Someone (likely a group of folks) need to find a super-smart transitional "diplomatic strategy" regarding the changes in both Gnome and Ubuntu!

I must get back to work ATM but IMO we should all work towards helping others with the transition rather than raising tensions ;)

Does that make sense?

---

### Post by kansasnoob on 2011-06-27
Dumb question:

This thread was originated by "Johnsie" on May 1st. When did he/she last post to this thread?

Has the originator of this thread passed along any of our suggestions?

What is Johnsie talking about lately:

[http://ubuntuforums.org/search.php?searchid=81727470](http://ubuntuforums.org/search.php?searchid=81727470)

Either kill this thread or explain why it still lives while others have been killed!

---

### Post by kansasnoob on 2011-06-27
Some questions are easily answered. I posted this "water cooler" question:

[Are those that dislike Unity being treated unfairly?]("http://ubuntuforums.org/showthread.php?t=1792063")

Not sure why the first poster found that link messed up, but I didn't even have time to respond :(

I'll try within the next week to address this issue at Ayatana ....... NOT the forum *[COLOR="Red"]resolution center[/COLOR]*!

There is no reason why reasonable people can't have open discussions around the water cooler regardless of their opinions. To suggest that any criticism of Unity is off limits is certainly less than "unifying"!

If that's the true position of Ubuntu then it's time to pursue LXDE in another environment, and that would make me very sad!

I've felt that I made many friends here and I'd hate to lose that connection :(

---

### Post by seeker5528 on 2011-06-27
> **kvv_1986 said:**
> If you don't want to bother tweaking with gnome fallback mode yourself, you could always change to Linux Mint when it comes out.

Never saw much point to Mint, but I never tried it either. 

I probably will skip the fallback. In Ubuntu I prefer Unity, in Debian I'm currently using Fluxbox+lxpanel, mutter+gnome-panel would probably be preferred, if they play well together when specified in a custom '~/.xsession', now that the bulk of stuff is in Debian unstable will have to try that combo again.

Later, Seeker

---

### Post by seeker5528 on 2011-06-27
> **Jacobonbuntu said:**
>  
[LIST]
[*]The system menu and the global menu of the running (top) application are kind of in each others way; if you are in the application's menu, there is no proper way to switch quickly to the system menu as far as I can see. 

That threw me for a minute because the global menu doesn't affect my ability to open the dash and go to 'more apps --> system' or to right click 'Applications' on the launcher panel and choose 'System'.

After reading it a few times, I'm assuming nautilus/desktop menu is what was intended by system menu. It would be nice to be able to always switch to this menu an back to the menu of the app in the foreground, not sure how easy that is to provide though since the desktop is always in the background, with no option to go global except to minimize all the apps on the current desktop or switch to another desktop where either all the apps are minimized or no apps are running.

Having the option to show the desktop was brought up before, don't know what the status of that is.

Later, Seeker

---

### Post by gexi on 2011-06-28
* **configurability** (which seems to be no.1 request);
i, for one, am using a different launcher, namely synapse, so i am not using dash and unity-launcher. thus, i want to be able to disable it. but also other things would be really good options: let me move the launcher to top/left/right/bottom; let me move and autohide the panel.


* **a better workspace solution**
now, what i really liked about the old panel-applet in gnome2 was, that it gave me instantaneous visual feedback on which workspace i'm right now, and what is running on other workspaces, without the need to trigger expo one way or the other. also you just needed to click one time to switch workspace.
maybe this can also be a configureable option: let me choose what i want to show on the panel without the need of the (not beginnerfriendly)-workaround of uninstalling single indicators.

---

### Post by Jacobonbuntu on 2011-06-28
> **seeker5528 said:**
>  After reading it a few times, I'm assuming nautilus/desktop menu is what was intended by system menu. It would be nice to be able to always switch to this menu an back to the menu of the app in the foreground, not sure how easy that is to provide though since the desktop is always in the background, with no option to go global except to minimize all the apps on the current desktop or switch to another desktop where either all the apps are minimized or no apps are running.

Having the option to show the desktop was brought up before, don't know what the status of that is.

Later, Seeker

Ah terrible, I indeed meant the nautilus/desktop menu. An old Mac-habbit (return to "finder"). As I said, my jargon is still poor....

---

### Post by cariboo on 2011-06-28
> **kansasnoob said:**
> Dumb question:

This thread was originated by "Johnsie" on May 1st. When did he/she last post to this thread?

Has the originator of this thread passed along any of our suggestions?

What is Johnsie talking about lately:

[http://ubuntuforums.org/search.php?searchid=81727470](http://ubuntuforums.org/search.php?searchid=81727470)

Either kill this thread or explain why it still lives while others have been killed!

Johnsie created a new username, that user was banned, and we haven't seen him since.

---

### Post by kansasnoob on 2011-06-28
> **cariboo907 said:**
> Johnsie created a new username, that user was banned, and we haven't seen him since.

So we're responding to a thread titled, "Improving Unity", and the odds of our comments bringing about any real change is pretty much nil :confused:

I seriously think this thread needs to be closed. OTOH if someone seriously intends to report "ways to improve Unity/Ubuntu" or suggest ways that we can each do that then a new thread can easily be started.

I'm buried with problems ATM that are in no way related to Ubuntu or even computers. And I seem to be taking 2 steps backward with every step forward :(

I even fear that I may not be available for the upcoming round of iso-testing. That would really bum me out.

Right now I'm just tired, and I'm perplexed about not even being able to use the "water-cooler" to have an open, honest discussion.

---

### Post by cariboo on 2011-06-29
Now that Natty has been out for a couple of months, you may be able to do what you want. Most of the reactionaries have gotten there say in, so you should now be able to have the conversation you want. 

The reason most threads get closed is because of infighting among a couple of members, that usually degenerate into name calling.

---

### Post by johnnybelfast on 2011-06-29
> Johnsie created a new username, that user was banned, and we haven't seen him since.     > So we're responding to a thread titled, "Improving Unity", and the odds  of our comments bringing about any real change is pretty much nil :confused:Hi, 
     I'm 'Johnsie' and I have been following this thread every day since its inception. There was an issue with my username and I am trying to get it resolved. I created a second account to give me some anonymity (without realising it's against the rules to have more than one account). Both were disabled instead of just the second one, so I haven't been able to log on or post anything. For me this has actually been a good thing because I was getting very frustrated by some of the negative discussions going on. I have however been reading this thread and passing some suggestions on. I work full time and can only do this in my spare time so I would be grateful if other could help with that passing on of ideas. 

**The purpose of this thread is more for looking at POSITIVE ways to make unity better. **I'm aware of the various heated threads/debates about unity, but as the OP I would appreciate that the nature of my thread be kept friendly and respectful. Alot of people have put alot of hard work into unity and the purpose of this thread is to help them, not for people to disrespect their work. I am not saying that anyone in this thread has been disrespectful, but I think it's important for those interested in unity to try and work together for something positive. I think this thread has been a good place for people to discuss improvements, but yes there are more official channels for getting things done. Anyone is free to take an idea or suggestion from this thread and push it into those channels.

Thanks.

John

---

### Post by jerrylamos on 2011-06-29
A big "positive" for me would be to have a choice of NO ICONS on the BFB apps and also on the Software Center.  With all the added room having real alphabetic names you could even have a brief few word description on the same line as the title of the app or software. 

These options have long been available ?for decades? on the view in folder descriptions - 

1. icons if you just have a few applications or programs or even pictures

2. multi column list if you have a lot

3. detailed list which I use mostly

Out Of The Box, Unity laid out for new pc users.

How about the same options that have been available "forever" on Folder View, for Unity Apps & Software Center (or Centre depending on your locale)?

Jerry

---

### Post by lucazade on 2011-06-29
> **jerrylamos said:**
> A big "positive" for me would be to have a choice of NO ICONS on the BFB apps and also on the Software Center.  With all the added room having real alphabetic names you could even have a brief few word description on the same line as the title of the app or software. 

These options have long been available ?for decades? on the view in folder descriptions - 

1. icons if you just have a few applications or programs or even pictures

2. multi column list if you have a lot

3. detailed list which I use mostly

Out Of The Box, Unity laid out for new pc users.

How about the same options that have been available "forever" on Folder View, for Unity Apps & Software Center (or Centre depending on your locale)?

Jerry

agree with you for detailed list.. I set this kind of view also in nautilus instead of icons.

---

### Post by kaldor on 2011-06-29
Can anyone tell me if there is a way to prevent the global menu from hiding in OO? If not, is it planned? This is one of the biggest usability issues I have with Unity. I hate stuff that hides; especially when it's for no reason.

---

### Post by lucazade on 2011-06-29
> **kaldor said:**
> Can anyone tell me if there is a way to prevent the global menu from hiding in OO? If not, is it planned? This is one of the biggest usability issues I have with Unity. I hate stuff that hides; especially when it's for no reason.

no way at the moment..  it is by design.

---

### Post by mgmiller on 2011-06-29
> **kaldor said:**
> Can anyone tell me if there is a way to prevent the global menu from hiding in OO? If not, is it planned? This is one of the biggest usability issues I have with Unity. I hate stuff that hides; especially when it's for no reason.

Take a look here for a possible solution:
[http://ubuntuguide.net/enable-global-menu-for-libreoffice-in-ubuntu-11-04-natty](http://ubuntuguide.net/enable-global-menu-for-libreoffice-in-ubuntu-11-04-natty)

I seem to remember reading somewhere that this might not be totally stable.  That's probably why it's not included by default yet.  I don't know.  I have not tried it myself yet.

:popcorn:

---

### Post by kaldor on 2011-06-29
> **mgmiller said:**
> Take a look here for a possible solution:
[http://ubuntuguide.net/enable-global-menu-for-libreoffice-in-ubuntu-11-04-natty](http://ubuntuguide.net/enable-global-menu-for-libreoffice-in-ubuntu-11-04-natty)

I seem to remember reading somewhere that this might not be totally stable.  That's probably why it's not included by default yet.  I don't know.  I have not tried it myself yet.

:popcorn:

Not the same as what I'm talking about. I'm talking about the silly "feature" where the menu only shows when you mouseover the top panel. Why is it hidden? It saves no space and creates extra work for the user, and hides it from people who are unfamiliar with how it works.

---

### Post by shadowninty on 2011-06-29
For the taskbar, I'd like the Dev team to take some ideas from windows; 
For Archive Managers or File Explorers there should be the ability to link to folders/archives 
There should be the ability to >Easily< resize or stick it 
There should be a preview of your open windows when hovering over an app icon 
There should be a show desktop icon (with peek too!) 
 
 
JMO of course!

---

### Post by mgmiller on 2011-06-30
> **kaldor said:**
> Not the same as what I'm talking about. I'm talking about the silly "feature" where the menu only shows when you mouseover the top panel. Why is it hidden? It saves no space and creates extra work for the user, and hides it from people who are unfamiliar with how it works.

I agree about the confusion for new users, but disagree about creating extra work.  I don't know why it's hidden by default and I know of no way to change that behavior.  

Have you tried the Alt key? it make it visible and allows you to keyboard control all the drop-downs.  The Gnome 2 panels simply had the menus visible at all times but worked exactly the same way.  Unity still does the same thing, it's just not obvious because you don't see the menus, so you forget they are there.  In both cases, Alt/F will bring up the File menu, for example, or moving the mouse up there will allow you to click on the File menu.  Same economy of motion for both the keyboard or mouse, just an (arguably) cleaner interface in Unity.  

It does require getting used to and I agree it can be confusing for a new user.  I happen to like Unity and have been using it for a while now, but I still sometimes forget the menu is up there for a second or 2.  

The one usage case where I find it a bit more of a stretch is when you have a small window open, like a terminal.  To get to the drop downs, they are much further away then they would be if they were in the title bar.  On the other hand, terminal is a keyboard centric window, so staying on the keyboard and using Alt/F, etc. works just as efficiently.

Perhaps hiding the drop down menus should be a user selectable feature, if only to avoid confusion in new users.

---

### Post by amano on 2011-06-30
What are the main improvements in Unity 4.0? I wonder why there haven't been any articles on OMG! Ubuntu! or Webupd8.

Or are all changes under the hood?

---

### Post by lucazade on 2011-06-30
> **amano said:**
> What are the main improvements in Unity 4.0? I wonder why there haven't been any articles on OMG! Ubuntu! or Webupd8.

Or are all changes under the hood?

this is the changelog
[https://launchpad.net/ubuntu/+source/unity/4.0.1-0ubuntu1](https://launchpad.net/ubuntu/+source/unity/4.0.1-0ubuntu1)

I believe it is mostly a gtk3 release and bug fixing, should be close to 3.8.x series for features atm.

---

### Post by hawthornso23 on 2011-06-30
> **lucazade said:**
> this is the changelog
[https://launchpad.net/ubuntu/+source/unity/4.0.1-0ubuntu1](https://launchpad.net/ubuntu/+source/unity/4.0.1-0ubuntu1)

I believe it is mostly a gtk3 release and bug fixing, should be close to 3.8.x series for features atm.

I think many were hoping for more change  than that. 

The chorus of complaints is annoying but it would be a terrible mistake to ignore it. It signals genuine unhappiness with basic design features. In particular the lack of customizability and the global menu are strongly disliked.

Of greater concern than the ones making all the noise are the large number of people who are silent but who are using ubuntu classic in 11.04. These people tried unity, didn't like it, and switched back to gnome2. If unity in 11.10 is basically the same and no gnome2 option is available these people are going to have a decision to make.

I predict we'll lose a large number of them.

---

### Post by johnnybelfast on 2011-07-01
To be fair moving to the new Gnome 3 and porting Unity over to that are pretty big tasks. One would assume that the priorities would be getting those working first and save any major feature changes to Unity for  Oneric +1. Yeah we might lose a few people in the meantime, but it's really important that things are working properly with the base software before we start to make major changes to Unity itself. The numbers we lose can easily be made up again in the future.

---

### Post by wgarcia on 2011-07-01
I agree with johnnybelfast. The main feature in Unity Oneiric is to be ported to GKT3. Once this is accomplished, I believe some cross fertilization can start with Gnome Shell, right now it is not possible because Unity is still GTK2.

---

