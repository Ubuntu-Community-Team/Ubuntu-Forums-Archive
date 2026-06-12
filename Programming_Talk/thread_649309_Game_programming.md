---
title: "Game programming"
date: 2007-12-24
forum: Programming Talk
---

### Post by Xealot on 2007-12-24
Hello ladies and gentlemen and merry Christmas to you all!

I need some advice, I want to make a 2d game. Ideally, It will be a RISK clone, based on the windows game Mission Risk ([Screenshot]("http://winsbydefault.com/screenshots/missionrisk.png")) 

Now,  I have NO experience with game development, at all. I have used SDL very briefly in school to create some simple 2d objects.
The thing is, Id like for my graphics to be integrated into a GTK window, much like the world map is inside the Windows form, I dont want a separate accelerated window that SDL makes..

I hope that made any sense :)

I have a bit of experience with programming in general, so learning should not be a problem at all, But I am in desperate need of pointers where to begin,

How I would go on about making these graphics in a GTK form and so forth. There will be no complex animation involved, I'd imagine the hardest part is finding out which country that gets selected when the user clicks with his mouse since the shape of the countries are irregular..

Any and all help I can get is welcome, also.. please dont flame me if I may have asked something stupid or obvious, If you find any guides you recommend reading I will be extremely grateful.

The languages I am capable of working with is Delphi and C#, but reading tutorials designed for C++ should not be a problem at all.

Thanks in advance,
 - Xealot

---

### Post by LaRoza on 2007-12-24
Python and PyGame are good alternatives that should be easily learned.

The language would be easier to work with. However, I never did such things as using graphics in programs, so I can't offer specific advice.

---

### Post by neko18 on 2007-12-24
You could use Python with PyGtk (package python-gtk2) and Python-Cairo (package python-cairo)

---

### Post by mike_g on 2007-12-24
> I'd imagine the hardest part is finding out which country that gets selected when the user clicks with his mouse since the shape of the countries are irregular..

That should not be too hard. You can make a mask (kind of invisible overlay on th map) that holds a country reference for each pixel on the map.

---

### Post by samjh on 2007-12-25
> **Xealot said:**
> Now,  I have NO experience with game development, at all. I have used SDL very briefly in school to create some simple 2d objects.
The thing is, Id like for my graphics to be integrated into a GTK window, much like the world map is inside the Windows form, I dont want a separate accelerated window that SDL makes..

...

How I would go on about making these graphics in a GTK form and so forth. There will be no complex animation involved, I'd imagine the hardest part is finding out which country that gets selected when the user clicks with his mouse since the shape of the countries are irregular..

...

The languages I am capable of working with is Delphi and C#, but reading tutorials designed for C++ should not be a problem at all.

Since you already know C#, try using Mono and GTK#.

You can install Monodevelop, an IDE for C# and Mono (includes GTK#), using this command:
```
sudo apt-get install monodevelop
```

Some Mono tutorials: [http://www.gotmono.com/docs/](http://www.gotmono.com/docs/)

Tao is a game-development framework for Mono: [http://www.mono-project.com/Tao](http://www.mono-project.com/Tao)

---

