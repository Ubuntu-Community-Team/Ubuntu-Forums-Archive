---
title: "Unity Launcher Icons"
date: 2012-01-16
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-16
In 11.10 Official Documentation, I read here:
 [https://help.ubuntu.com/11.10/ubuntu-help/shell-apps-favorites.html](https://help.ubuntu.com/11.10/ubuntu-help/shell-apps-favorites.html)
that: > The launcher icon order can be changed by dragging an icon off of the launcher, and then back onto it in the desired location.
& here:
 [https://help.ubuntu.com/11.10/ubuntu-help/unity-launcher-change-size.html](https://help.ubuntu.com/11.10/ubuntu-help/unity-launcher-change-size.html)
that I can change size of the icons using CompizConfig Settings Manager.

Neither of these seems to work for me, with 11.10 kernel 3.0.0-14

Am I missing something or do they really just not work?

Thanks!

---

### Post by tersogar on 2012-01-16
Also you re size the icons using myunity.

---

### Post by Frogs Hair on 2012-01-16
The second link describes a method for Unity 3D and if you are using 2D try MyUnity as suggested above .
[http://maketecheasier.com/tweak-ubuntu-unity-desktop-with-myunity/2011/12/22](http://maketecheasier.com/tweak-ubuntu-unity-desktop-with-myunity/2011/12/22)

---

### Post by 2CV67 on 2012-01-19
I still don't know if resizing & re-ordering of ikons is supposed to work or not, without MyUnity?

Anyway - I am interested in trying MyUnity, but not sure how to get there.

When I follow leads, I usually get pointed at the MyUnity PPA, but when I tried to apply that in terminal, I got a warning message pointing me to launchpad  [https://launchpad.net/~myunity/+archive/ppa](https://launchpad.net/~myunity/+archive/ppa)
and there I find the same warning:
> This PPA contains backports for Ubuntu Stable Releases (11.04/Oneiric and 10.10/Natty). If you are using Precise (the current development release, which in time will become 11.10), please don't use this PPA: MyUnity is already availble from Ubuntu Archive through Ubuntu Software Center.

That seems to suggest I should be able to find MyUnity in Software Center in 11.10 (doesn't it?) but I looked there & in Synaptic and found nothing.

I don't understand the reference to "Ubuntu Archive" in Software Center either...

Thanks for some Dummy-level help!

---

### Post by 2CV67 on 2012-01-19
In the meantime, I discovered these instructions for re-ordering icons using GConf-editor:
[http://www.liberiangeek.net/2011/04/add-favorite-applications-ubuntu-launcher-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/add-favorite-applications-ubuntu-launcher-11-04-natty-narwhal/)

So I installed GConf-editor & followed the instructions to > desktop > unity-2d > launcher > favorites > Edit Key...

But the list in there is the list of Default Keys for a new desk, not the list I have now.

Is that how it should be, or should it show my current setup?
Is it likely to work?
Or do I have to remove all my icons & carefully put them back in the right order every time I want to change??

Why is this simple job so ***** difficult?

---

### Post by 2CV67 on 2012-01-19
OK - I found the answer here:
[http://askubuntu.com/questions/39805/is-there-an-easy-way-to-rearrange-the-icons-in-unity-launcher](http://askubuntu.com/questions/39805/is-there-an-easy-way-to-rearrange-the-icons-in-unity-launcher)

All the first & main contributions show dragging the icons off the launcher & back again, just like all the instructions say.
This does not work for me.

A couple of contributions at the bottom say:

> You can also control-drag the icons in the launcher straight up or down instead of dragging out and then back in.

&

> In Ubuntu 11.10, dragging to the right didn't work for me. When I click an icon and hold the mouse button down for one second without moving the mouse, the icon drops down a few pixels. After that, I can drag it up or down the list to change its position.

Both those work perfectly for me.

Call this [SOLVED] now - but what a lot of wasted time & effort...

---

### Post by 2CV67 on 2012-01-19
Back on the question of how to change Launcher Icon size, I did a lot more searching.

Here are a couple of related questions from Ask Ubuntu:
[http://askubuntu.com/questions/66543/change-icon-size-in-unity-2d-launcher](http://askubuntu.com/questions/66543/change-icon-size-in-unity-2d-launcher)
[http://askubuntu.com/questions/73107/unable-to-change-the-launcher-icon-size](http://askubuntu.com/questions/73107/unable-to-change-the-launcher-icon-size)

Some Questions & Answers from Unity 2D Launchpad:
[https://answers.launchpad.net/unity-2d/+question/141757](https://answers.launchpad.net/unity-2d/+question/141757)
[https://answers.launchpad.net/unity-2d/+question/158873](https://answers.launchpad.net/unity-2d/+question/158873)
[https://answers.launchpad.net/unity-2d/+question/175008](https://answers.launchpad.net/unity-2d/+question/175008)

A Confirmed Bug Report:
[https://bugs.launchpad.net/unity-2d/+bug/789638](https://bugs.launchpad.net/unity-2d/+bug/789638)

All of that leaves me thinking it is probably impossible to change icon size in 2D.
But I am not certain.
Nor is it clear whether a fix is ever likely.

Anyway, disregarding the warnings on the MyUnity site, I added thier PPA & installed MyUnity 2.0.0

With it, I am able to put a trash can on my desktop, but not change anything about icon size or appearance.

Are you guys who recommend MyUnity actually seeing it work on 2D?
If so - how?

Thanks!

---

### Post by tersogar on 2012-01-19
With this ppa,

[B]ppa:myunity/ppa

[/B]I´m able to change the size of unity as a hole, transparency and also it has options regarding hiding.

---

### Post by Hylas de Niall on 2012-01-19
Yep. MyUnity all the way :)
I think their indicating its availability in SC is a typo, you do need to add their ppa for 11.10, but i believe it will be in the SC for 12.04.

---

### Post by tersogar on 2012-01-19
Here you can see Unity in 3d much smaller. Hope this help.

---

### Post by 2CV67 on 2012-01-19
Thanks.

I used the same PPA.

I have the same controls available, including Dimensioning for the icons from 32 to 64.

But it does not work.

I am not interested in the fancy stuff about transparency etc.
I just want smaller icons.
I am using 2D.

1. Do you have 2D (not 3D)?
2. With 2D, can you really change icon size?

Thanks!

---

### Post by tersogar on 2012-01-19
> **2CV67 said:**
> Thanks.

I used the same PPA.

I have the same controls available, including Dimensioning for the icons from 32 to 64.

But it does not work.

I am not interested in the fancy stuff about transparency etc.
I just want smaller icons.
I am using 2D.

1. Do you have 2D (not 3D)?
2. With 2D, can you really change icon size?

Thanks!

I´m using 3D. But in 2D it did not work.

---

### Post by 2CV67 on 2012-01-19
Thanks!

I only recently discovered that 2D was critical.

I have now specified that in my signature.

---

### Post by 2CV67 on 2012-01-21
I have given up & gone back to Gnome Classic...

It's great!

---

### Post by tersogar on 2012-01-21
I try the XFCE desktop which is just a click away in the software center and is very nice and reponsive.

---

### Post by summoness on 2012-03-16
The icon size can be changed using "Ubuntu Tweak" under Unity Settings. There are many other options for compiz,theme,and others as well. I consider it a must have for Ubuntu. I am currently running Ubuntu 11.10

---

