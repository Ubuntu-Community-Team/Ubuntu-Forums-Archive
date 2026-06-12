---
title: "What's the peaceful path to configuring 11.10's desktop ?"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by frogo on 2012-01-30
*I'm marking this as solved, although I don't think I have found peace yet. The path, for me at any rate, seems to be mostly in getting used to things and finding the tricks and tips... teher's a good number of links and ideas in this thread for getting started with it. Many thanks to all!*


Hello, 

i've installed 11.10 recently and the performance are ok enough compared to 10.04 on my machine that I'll stick with it. However, the desktop is starting to drive me mad and I can't quite get used to a few weird things after a few days. I don't mean to rant (too much) but it feels like I should have intuitions about how Windows may work those days and that really is not helpful. 

I don't want to revert to something that will grow unsupported and I  would really like to get the hang of how to live with this. I haven't been able to find straightforward ways of configuring the behavior and it's obvious I must be missing something. Any tutorial / documentation I find seems to lead to installing further things which all promise more struggles (Compiz?) and I haven't been able to find the right place for configuring the thing.

For the sake of illustration, and also on chances of fishing for kind nudges in the right way, here are some of the basic little things I'm struggling with:

- I can't really make my way through the Dash home. I'm not sure why it closes when I do, for example, Dash home --> More Apps --> Customization --> Appearance
- it's a struggle to resize windows
- it's a struggle to switch windows or instances of the same app (e.g. when I have 2 Firefox windows open, I struggle to get to the right one. 
- I can't find a way of opening more than one instance of an app (e.g. FireFox or terminal) across desktop spaces other than opening another window and dragging it to another space. But then, it's a struggle to switch between instances
- the left hand side MacOS like bar comes up when I don't want to --- e.g. when trying to hit the return arrow in Firefox --- or it doesn't come up, ot it doesn't react (e.g. it won't go to a running instance if i click on the icon)
- i can't find a way of force quitting an application --- e.g. skype
- is the absence of panel in the upper bar by design or have I missed a configuration option?

thanks for any suggestion that does not involve reinstalling a desktop app

best 
f

---

### Post by philinux on 2012-01-30
> **frogo said:**
> Hello, 

i've installed 11.10 recently and the performance are ok enough compared to 10.04 on my machine that I'll stick with it. However, the desktop is starting to drive me mad and I can't quite get used to a few weird things after a few days. I don't mean to rant (too much) but it feels like I should have intuitions about how Windows may work those days and that really is not helpful. 

I don't want to revert to something that will grow unsupported and I  would really like to get the hang of how to live with this. I haven't been able to find straightforward ways of configuring the behavior and it's obvious I must be missing something. Any tutorial / documentation I find seems to lead to installing further things which all promise more struggles (Compiz?) and I haven't been able to find the right place for configuring the thing.

For the sake of illustration, and also on chances of fishing for kind nudges in the right way, here are some of the basic little things I'm struggling with:

- I can't really make my way through the Dash home. I'm not sure why it closes when I do, for example, Dash home --> More Apps --> Customization --> Appearance
- it's a struggle to resize windows
- it's a struggle to switch windows or instances of the same app (e.g. when I have 2 Firefox windows open, I struggle to get to the right one. 
- I can't find a way of opening more than one instance of an app (e.g. FireFox or terminal) across desktop spaces other than opening another window and dragging it to another space. But then, it's a struggle to switch between instances
- the left hand side MacOS like bar comes up when I don't want to --- e.g. when trying to hit the return arrow in Firefox --- or it doesn't come up, ot it doesn't react (e.g. it won't go to a running instance if i click on the icon)
- i can't find a way of force quitting an application --- e.g. skype
- is the absence of panel in the upper bar by design or have I missed a configuration option?

thanks for any suggestion that does not involve reinstalling a desktop app

best 
f

Have a look at the links in my Sig. Try to pose one problem at once.

---

### Post by 2F4U on 2012-01-30
> - I can't really make my way through the Dash home. I'm not sure why it  closes when I do, for example, Dash home --> More Apps -->  Customization --> Appearance

If I do that, the Dash closes and the Appearance app starts. Is the behaviour on your system different? As far as I know, the Dash always closes once an application is started.

> is the absence of panel in the upper bar by design or have I missed a configuration option?

The big bar on the left acts as both a quick lauch bar and a task bar. Applications that are started receive a small arrow on the left of the icon. If you start a second instance, there is a second arrow on the left side of the icon.

---

### Post by cortman on 2012-01-30
+1 for thread title.

I understand Compiz has a couple plugins that allow you to edit Unity some.

I think what will decide which new style DE wins (i.e., Unity or Gnome shell) will depend on who bundles a quality GUI desktop configuration tool WITH the DE.
I don't want to rant either, and I know enough to be able to edit gnome-shell.css sheets and customize my DE to where I like it, but shipping a DE completely without any intuitive GUI configuration app borders on unacceptable, IMHO.
That said,  I use both Gnome shell and Unity (Gnome shell primarily), and I like different things about both of them. I also use Xubuntu on some machines, for a classic desktop.

---

### Post by frogo on 2012-01-30
> **philinux said:**
> Have a look at the links in my Sig. Try to pose one problem at once.

wow many thanks for these which but for one I had not yet come across... I installed MyUnity and used it for a couple of things, but that's not precisely as fine grained as i was hoping for, i guess. 

I guess too it will mostly be a matter of getting used to things.

[Rick Spencer’s Getting Started]("http://theravingrick.blogspot.com/2011/04/my-effort-at-writing-help-for-unity.html") from your first link is incredibly useful. e.g. Alt+Tab seems to help switching apps and across space, although we'll see with use and when tones of windows are opened everywhere..

I'll keep that thread open while I look more into things and then close to ask more specific question if they come up. 

many thks!

---

### Post by frogo on 2012-01-30
> **2F4U said:**
> If I do that, the Dash closes and the Appearance app starts. Is the behaviour on your system different? As far as I know, the Dash always closes once an application is started.


sorry, yes, that's exactly what it does. It's just that Appearance is a bit frustrating so you immediately want to go back to system.. I seem to be caught red handed with my WinXp intuitions on this one...

> The big bar on the left acts as both a quick lauch bar and a task bar. Applications that are started receive a small arrow on the left of the icon. If you start a second instance, there is a second arrow on the left side of the icon.

Hum, yeah, I managed to drop a terminal icon in there. Things seemed to be simpler only a week ago. Also, with unity I found it difficult to get to the right window when multiple ones are open. But the key seems to be exercising.

thanks for your help
f

---

### Post by philinux on 2012-01-30
> **frogo said:**
> wow many thanks for these which but for one I had not yet come across... I installed MyUnity and used it for a couple of things, but that's not precisely as fine grained as i was hoping for, i guess. 

I guess too it will mostly be a matter of getting used to things.

[Rick Spencer’s Getting Started]("http://theravingrick.blogspot.com/2011/04/my-effort-at-writing-help-for-unity.html") from your first link is incredibly useful. e.g. Alt+Tab seems to help switching apps and across space, although we'll see with use and when tones of windows are opened everywhere..

I'll keep that thread open while I look more into things and then close to ask more specific question if they come up. 

many thks!

Glad to help. You can see how things are shaping up for 12.04 by following here. [http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

---

### Post by trikster_x on 2012-01-30
> **frogo said:**
> 
- I can't really make my way through the Dash home. I'm not sure why it closes when I do, for example, Dash home --> More Apps --> Customization --> Appearance
If the Dash closes and the appearance window opens, then it is functioning normally. If you want to return to the system settings menu, the upper left portion of the appearances window has a button to do just that, without opening the dash again.
> - it's a struggle to resize windows
In what way is it a struggle? Granted windows don't have a border, but moving the mouse to the corner of a window allows you to drag-resize. Move the title bar to the top border of the desktop and it auto-maximizes. Grab the top border and pull down auto-restores.
> - it's a struggle to switch windows or instances of the same app (e.g. when I have 2 Firefox windows open, I struggle to get to the right one.
Biggest drawback to Unity IMO. Unfortunately there is not a lot to be done about this, other than clicking on the app icon to bring up the window switcher and trying to get the right one from there.
> - I can't find a way of opening more than one instance of an app (e.g. FireFox or terminal) across desktop spaces other than opening another window and dragging it to another space. But then, it's a struggle to switch between instances
The only other way to do this is to move to the desktop you want the window on and open it from there.
> - the left hand side MacOS like bar comes up when I don't want to --- e.g. when trying to hit the return arrow in Firefox --- or it doesn't come up, ot it doesn't react (e.g. it won't go to a running instance if i click on the icon)
Unfortunately, this is due to the layout of the firefox window. I suggest you try chromium, since the tab bar is at the top of the window, with all the controls underneath that. As far as not switching to the right application, I've had this behavior caused by setting a window to "always on top" as well as a couple compiz plugins that weren't upgraded. There doesn't seem to be a workaround for the always on top bug.
> - i can't find a way of force quitting an application --- e.g. skype
You can open system monitor by starting the dash and typing "sys" in the search bar(should be one of the first apps to come up). From my experience, the only way to stop Skype running is to right click on the application listing and use the "kill process" option. Simply ending it does not stop Skype. Alternately, if you know the name of the program you can type in a terminal window "pkill *appname*"(i.e. pkill skype)
> - is the absence of panel in the upper bar by design or have I missed a configuration option?
It's by design. The upper bar is now reserved for the title bar menus of the application that currently has focus, along with the notification system.

---

### Post by shizz on 2012-01-30
> **trikster_x said:**
> 
In what way is it a struggle? Granted windows don't have a border, but moving the mouse to the corner of a window allows you to drag-resize. Move the title bar to the top border of the desktop and it auto-maximizes. Grab the top border and pull down auto-restores.



I think I know what he means by it being a struggle to resize windows. I often find it hard to get the cursor in the exact place to resize them. There doesn't seem to be many pixels given to this task. Its hit or miss a couple of times before you get it right. At least for me anyway. I'd like if there was a bigger area to grab on to.

---

### Post by MG&amp;TL on 2012-01-30
> **shizz said:**
> I think I know what he means by it being a struggle to resize windows. I often find it hard to get the cursor in the exact place to resize them. There doesn't seem to be many pixels given to this task. Its hit or miss a couple of times before you get it right. At least for me anyway. I'd like if there was a bigger area to grab on to.

I think to be fair, gnome2 had this too.

@OP-you say making your way to an app is difficult via the dash. I'm not trying to patronise you here (I didn't realise myself), but you HAVE realised you can just type 'appearance' and it will appear?

12.04 is a lot more (easily) customisable than previous releases.

---

### Post by trikster_x on 2012-01-30
> **shizz said:**
> I think I know what he means by it being a struggle to resize windows. I often find it hard to get the cursor in the exact place to resize them. There doesn't seem to be many pixels given to this task. Its hit or miss a couple of times before you get it right. At least for me anyway. I'd like if there was a bigger area to grab on to.

I have found that the bottom right corner of the window has a larger area dedicated to this task.

---

### Post by frogo on 2012-01-30
> **MG&TL said:**
> I think to be fair, gnome2 had this too.


(i may be unfair, but I'm not trying to measure up one against the other.) 

I've got two, three-ish issues with window sizes.

i) by default many apps open with a full screen window. Ok, I can go on the application bar and hit the little square because I can't seem to be able do otherwise (yet?)... 

ii) even when not in full screen and i need to resize a window I occasionally get stuck with what Shizz describes. Maybe it's not with everything, I'm not sure. But I can tell you that it can be extremely painful to try resizing a terminal window, especially if there is a window behind it... true it was occasionally the case before, but it seems to be a bit more dramatic now (honestly, I do swear each time, but I like swearing)... 

iii) (ish) I'm not sure about this one because I'm not entirely sure I understand what happens. Sometimes dragging a window around will bring it full screen (i guess I'm dragging it to the upper bar or something like that. It's worst when dragging a window across spaces. Sometimes I can drag it to another space, sometimes I can't and teh window is downsized to the border between spaces.

Now these can be seen as very minor annoyances, but I have a 13'' screen and have to switch between 4/5 apps whenever i  do anything with this machine. Sometimes that's 3 times such set up at the same time... so window mis- or weird behavior can be a real nerve breaker.  

> @OP-you say making your way to an app is difficult via the dash. I'm not trying to patronise you here (I didn't realise myself), but you HAVE realised you can just type 'appearance' and it will appear?
No offense taken, that's a fair point. I sorta intuit that it's one way of doing it, I think. But I'm not trained yet into finding apps this way (afraid I'm just backward.. I like to see what's there and where it is rather than trust to shoot for it). Also, I have to admit, I just don't care to remember the names of apps. 

> 12.04 is a lot more (easily) customisable than previous releases.Not there yet :) Have had a lot of troubles over the past 2 years to get a stable install on this machine but paradoxically I can't afford spending more than a day setting up the machine to a working condition... so even when it's less than pleasant, provided it does the job, I stick to it. I'll be with 11.10 for a while ... In fact the greatest thing in terms of upgrade this time around has been that I have been able to seamlessly access most of the data on the 10.10 partition after installing 11.10 alongside to it. First time ever this works so well, I don't know if it's a + of 11.10 or a - to me in my previous experiences..

cheers

---

### Post by frogo on 2012-01-30
> **trikster_x said:**
> I have found that the bottom right corner of the window has a larger area dedicated to this task.

Seems to work pretty well when the window has white space at the bottom. But it can be a bit tricky otherwise, as with the terminal where this area is not always grabbed easily and not well demarcated from the sliding bar. Also, it's not always the case that it's natural to resize by pointing at the bottom right corner... 

Admittedly, this is, overall, not very significant stuff. But that's more or less the point, one should not have to think of this and never have to spend several seconds trying to place a pointer to do window resizing. This aside, I might be a bit of a grump...

---

### Post by MG&amp;TL on 2012-01-30
1. I never said you were; just avoiding the possibility. :P About the maximised ones; this is quite hard to describe, but easy enough once you get the hang of it. For a maximised window, click the top bar, then drag downward. After a while, it will 'snap' out of maximised. Same with windows horizontally maximised (*aero-snap* style.) 

2. I think you'll get there eventually. GNOME3 is even more type-driven.

3. Oh, oops. :oops: I didn't mean "you should try this right now" - that's pretty dumb on a production machine, we seem to be at breakage point in the alphas. I meant "wait three months, and you should be a little better off"

---

### Post by trikster_x on 2012-01-30
> **frogo said:**
> Seems to work pretty well when the window has white space at the bottom. But it can be a bit tricky otherwise, as with the terminal where this area is not always grabbed easily and not well demarcated from the sliding bar. Also, it's not always the case that it's natural to resize by pointing at the bottom right corner... 

Admittedly, this is, overall, not very significant stuff. But that's more or less the point, one should not have to think of this and never have to spend several seconds trying to place a pointer to do window resizing. This aside, I might be a bit of a grump...

There is actually a plugin in the stock compiz package that allows a keybind for resizing windows. Default is set to alt+f8, but that is a bit unwieldy if you are using a mouse. You can get to all the settings for compiz by installing CCSM(compiz config settings manager), then edit the keybinds as you see fit. That should help with a couple things I think. I really wish Canonical would make that one of the default applications, since compiz is so heavily integrated now.

---

