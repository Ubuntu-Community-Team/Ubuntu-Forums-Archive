---
title: "Help with Update/Change Applications Menu"
date: 2023-04-07
forum: New to Ubuntu
---

### Post by knighthammer2 on 2023-04-07
Greetings,

I am at the point I need some help. I've been messing around with this problem for almost two weeks.

Frist off, I am relatively new to Linux. I've tinkered before, I never got super serious about it.

I decided to throw a flavor of Linux on my laptop but I've been having a major issue trying to transition myself over.

I want to be able to setup the Applications Menu using *MY* sorting methodology. I understand that Ubuntu/Linux tends to have universal categories the community has setup over years.

I've played with Arc Menu, Cinnamon Menu, Libtre Menu, Edit Menu and what not.

I came pretty close to getting what I wanted through Cinnamon Menu and Libtre Menu (as the editor) but Flatpaks threw me for a massive curve ball.

What I'd like is STRAIGHT FORWARD way to just make a menu structure and dump the corresponding .desktop files in there and "go".

I'm not dedicated to any flavor of Ubuntu atm and don't mind reformating / changing desktops. As long as I can get the directory structure I want, I am game for anything at this point.

Suggestions?

---

### Post by ne29914 on 2023-04-07
You need to understand how the Applications Menu works.
There's no "menu file" containing the menu items on your system. The Application Menu is built new every time the user logs in.
The .desktop files are scanned for their "categories" entry and the menu points placed in the menu according to that.
Here's a basic list:
[https://specifications.freedesktop.org/menu-spec/latest/apa.html](https://specifications.freedesktop.org/menu-spec/latest/apa.html)

---

### Post by MAFoElffen on 2023-04-08
A good read that explains more on creating and editing custom menu entries: [https://www.makeuseof.com/create-taskbar-and-menu-entries-for-linux-apps/](https://www.makeuseof.com/create-taskbar-and-menu-entries-for-linux-apps/)

---

### Post by him610 on 2023-04-11
> I want to be able to setup the Applications Menu using *MY* sorting methodology.
Does this look anything like what you are trying to do?

[https://imgur.com/XjYCdWs.png]("https://imgur.com/XjYCdWs.png")

The left most list is the different groupings. The list on the right shows the widgets that represent the applications I use most often. The order of listing can be arranged in any order you want. The *buntu flavor is Xubuntu - lightweight, yet highly configurable.

---

