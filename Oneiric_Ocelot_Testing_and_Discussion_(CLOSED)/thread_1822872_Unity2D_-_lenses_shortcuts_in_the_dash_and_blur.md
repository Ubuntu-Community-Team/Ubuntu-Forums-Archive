---
title: "Unity2D - lenses shortcuts in the dash and blur"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-08-11
Some little changes in Unity2D available in daily ppa.

Lenses shortcuts are no more present in launcher (left sidebar) because are available in main page of Dash. It seems a better place, althought it still needs some polishing.

Blur effect for the dash now is available even in a 3D compositor (metacity or compiz) is not enabled. Nicer and help readability.

note: don't know if lenses were already moved also in Unity-3D version, can't test it now.

---

### Post by Framli on 2011-08-11
It will be available soon in U3D.

---

### Post by godhika on 2011-08-11
Should be in trunk - at least according to changelog. But in my build there seems the be missing something (can't open any lenses, not even application or places). But the new dash-blur thingy is awesome -hard to describe one has to see it themselve (i guess there ll be alot of complaints about it looking to much like aero or that one should go for stability first before looks, but hey)

---

### Post by x-shaney-x on 2011-08-11
Well CCSM has an option to enable dash blur, I suspect this may become a default at some point.

I'm wanting to see the 2d version for myself though.  How long does it normally take the oneiric repo to catch up with the daily?

---

### Post by godhika on 2011-08-11
Well, the current das blur is static - the one implemented in trunk is either static or dynamic. also the the tint of the dash isn't almost black anymore but is now lighter and dependent on the median wallpaper color. That means if your wallpaper is mostly red, the dash is colored in some transparent red, and so on. sorry for no screenshots as i deleted my built of unity in anticipation of todays official release ;)

---

### Post by x-shaney-x on 2011-08-11
I've only recently been testing oneiric.  Is unity still a Thursday thing as it was in Natty then?
Also, where is the best place to keep up with unity (2D and 3D) developments and discussions regarding features (such as whether the 2D launcher will be resizeable at any point and whether we will get the battery indicator back)?

I don't want to go to the extent of installing a daily repo but would like to keep up :)

---

### Post by godhika on 2011-08-11
ok just recompiled and took screenshots for your viewing pleasure - note the different tint of the dash depending on the wallpaper

---

### Post by x-shaney-x on 2011-08-11
Mmm.  Looks nice.  Not sure about the dash icon moving to the panel though.
Suppose it DOES make it more obvious that it does something though.

What does the "home" icon at the bottom do?

---

### Post by zekopeko on 2011-08-11
> **godhika said:**
> ok just recompiled and took screenshots for your viewing pleasure - note the different tint of the dash depending on the wallpaper

They removed the Ubuntu button. I wonder what they will do with the extra space.

---

### Post by zekopeko on 2011-08-11
> **x-shaney-x said:**
> Mmm.  Looks nice.  Not sure about the dash icon moving to the panel though.
Suppose it DOES make it more obvious that it does something though.

What does the "home" icon at the bottom do?

It probably leads to the default dash. If you look at lucazade's screenshot you will see that the Applications and Files&folders is next to the home icon.

---

### Post by x-shaney-x on 2011-08-11
> **zekopeko said:**
> They removed the Ubuntu button. I wonder what they will do with the extra space.

My guess is they will move the window control buttons to where the icon used to be and bring the titles/menus in line with the corners of the windows when maximized.

Maybe that means they will make the menu permanent instead of peekaboo, with a little more space to include window title AND menu on the panel?

---

### Post by godhika on 2011-08-11
> **zekopeko said:**
> It probably leads to the default dash. If you look at lucazade's screenshot you will see that the Applications and Files&folders is next to the home icon.

Yep i guess that is how it is supposed to work - mind that lucazades screenshot is unity-2d while mine are unity 3d. but as there has some changes in unity behind the scenes i couldn't manage to get built a fully working unity-3d. I hope the package released later today for FF will be working as intended.

---

### Post by x-shaney-x on 2011-08-11
Argh!  Well I was looking forward to seeing the new style unity in action but I have to say, it looks awful to me.

It may well be better in a scientific and usability tests way but the way I use unity it is not good.

I have the launcher showing always and most windows fully maximized and it just looks, well... naff.  

I'll keep waiting though and see what they come up with.

---

### Post by x-shaney-x on 2011-08-11
I've also come across another issue...

I have not been a heavy unity user in recent times but have used it enough to automatically send the mouse to the top left corner for the dash button.

Well of course, that corner icon is now the window close button so I reckon people are going to be doing a lot of accidental app closing til they get used to it.

---

### Post by MacUntu on 2011-08-11
> **x-shaney-x said:**
> I've also come across another issue...

I have not been a heavy unity user in recent times but have used it enough to automatically send the mouse to the top left corner for the dash button.

Well of course, that corner icon is now the window close button so I reckon people are going to be doing a lot of accidental app closing til they get used to it.

:D

[http://ubuntuforums.org/showpost.php?p=11126772&postcount=5](http://ubuntuforums.org/showpost.php?p=11126772&postcount=5)

I sure hope that will change.

---

### Post by mc4man on 2011-08-11
> **lucazade said:**
> Some little changes in Unity2D available in daily ppa.

Lenses shortcuts are no more present in launcher (left sidebar) because are available in main page of Dash. It seems a better place, althought it still needs some polishing.

Blur effect for the dash now is available even in a 3D compositor (metacity or compiz) is not enabled. Nicer and help readability.

note: don't know if lenses were already moved also in Unity-3D version, can't test it now.
It certainly is now available in unity, the big difference is it looks good in unity-2d, in unity it ranges from ok to a bit of a joke depending on the desktop background and or any windows open on the desktop
(atm it also kills using a transparent panel but that could be just a temp thing

Edit: the more I use the dash with some desktop backgrounds and the various searches it generally feels like a headache waiting to happen
Very ill conceived

---

### Post by x-shaney-x on 2011-08-12
I agree.  I though the lens blur would look awesome on 3D but it looks a bit weird.
Can't explain it, just one of those things that doesn't feel right but you don't know why.

The lens is much better in 2D though but what have they done to that menubar?

If a window is not maximised, the window title is at the very left of the panel.
If you then maximize the window, the window control buttons appear and the window title jumps across a bit and it all looks very messy.

Not only that, the window title buttons are slightly wider than the panel so everything just looks out of sync.
I can't imagine that the current version is going to be anything like this come October though, least I hope not.

---

### Post by lucazade on 2011-08-12
Without looking at final design specs of Unity it is difficult to say if some stuff is temporary or propaedeutic to some other steps.
The same is for code, some things that look weird at the moment landed, probably, also to inject new methods and technologies under the hood but the appearance is not necessarily the final one.
Said that I find the blur in unity-2d quite useful, also using different kind of backgrounds, it remains always readable. Can't say anything about 3d version at the moment, I can only look at the screenshots.

---

### Post by mc4man on 2011-08-12
The dash itself is much improved, particularly the 'refined search section' (screen
Other than that I can't see the sense in the blur and extending into the unity panel (I've no reason to interact with the indicators while a lens is open
So absolutely don't like the look, the 3d effect on icons and  if there is a white window open underneath it goes from bad to worse
There will be changes, to what extent we'll see..
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824916](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824916)

Edit - 2nd shot - while not as bad as in bug, another example

---

### Post by lucazade on 2011-08-12
> **mc4man said:**
> The dash itself is much improved, particularly the 'refined search section' (screen
Other than that I can't see the sense in the blur and extending into the unity panel (I've no reason to interact with the indicators while a lens is open
So absolutely don't like the look, the 3d effect on icons and  if there is a white window open underneath it goes from bad to worse
There will be changes, to what extent we'll see..
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824916](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/824916)

Edit - 2nd shot - while not as bad as in bug, another example

ok, now I can see the issue clearly.. in the 2d version is not present, at least at the moment.
going to subscribe to bug report.. we'll see

---

### Post by x-shaney-x on 2011-08-12
Well today it still doesn't look any better lol.

I suppose it is understandable things are going to look a little strange after what is, after all, the biggest change to unity since it was first seen really.

Thing is, up until yesterday I had been using unity 2D Oneiric as my main OS (won't use 3D cos of the 3 finger tap problem) but I cannot bring myself to use it at the moment.

I have switched to using Natty, not because of any kind of instabilities in Oneiric but because I just keep being distracted by the placement of the menus and window buttons now.
It's like, I'm trying to read a web page but my eyes keep drifting up to the top left corner :)

---

### Post by mc4man on 2011-08-12
Another related minor issue in 3d ATM is if one uses a transparent panel it's now picking up on the dash tint and using that instead of being 100% trans.
It varies from completely to just the indicators area.

Myself hope this is fixed, but I try not to get too attached to anything in 'experimental' based on something said in a bug I had in natty & is a reasonable position - 
> some experimental settings will remain.
We have already seen cases where such settings resulted in additional
bugs, so we will remove experimental settings when the experiment is
over and we have an answer. We will not keep code paths around just
because somebody likes that option - if we did, the code would get
bloated and buggy and slow.

---

### Post by x-shaney-x on 2011-08-12
*Double post

---

### Post by x-shaney-x on 2011-08-12
Picking up the dash hint may be by design (though obviously not where it is only partially working.
I haven't used OS X recently but if I remember correctly, the design idea for the transparent menubar was to take hints from the desktop wallpaper colours to ensure everything was easily readable so I'm thinking it could be the same thing.
Pure speculation, of course :)

If the blur on the panel and dash become permanent, I should hope they will add the blur to any transparency in the launcher though or it will look odd.

I wish I could find some sort of design discussion on the new panel layout.
In my mind, when windows are maximized everything should line up with the window to look like part of the window but I don't see any consistent way of doing this.
Currently, it will work that way if the panel is set to autohide or dodge but looks very wrong if the panel is always shown, with the buttons and window titles/menus being offset from the window.

It may make more sense for the launcher to go all the way to the top of the screen area, so on autohide and dodge, the window buttons and menus slide with the launcher (if you get what I mean), meaning they will always line up with the window when maximized.

---

### Post by mc4man on 2011-08-15
Even though Ot - I guess the 'experiment' is somewhat over - the experimental tab has been removed and only one option is still labeled as such.
What's interesting is now all the options are presented without comment or useful tooltips, many just mode values

---

