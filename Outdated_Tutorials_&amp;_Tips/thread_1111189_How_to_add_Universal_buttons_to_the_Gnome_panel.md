---
title: "How to add Universal buttons to the Gnome panel"
date: 2009-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by roblloyd on 2009-03-30
So, in my attempts to integrate a wiimote into the gnome desktop, I have found a way to create universal close, resize, maximise...well any button you want. It's all to do with simulating button presses.

First, I should explain. I have decided to use the program [maximus]("http://packages.ubuntu.com/intrepid/gnome/maximus") to make all new windows open maximised. It's a trick I learned from [Ubuntu netbook remix]("http://www.canonical.com/projects/ubuntu/unr"). However, maximus also removes the titlebar from a window. So you need to replace them with something.

My solution was to use the program [xautomation]("http://hoopajoo.net/projects/xautomation.html").

xautomation:
[INDENT]Control X from the command line for scripts, and do "visual scraping" to find things on the screen. The control interface allows mouse movement, clicking, button up/down, key up/down, etc.[/INDENT]

All you need to do to make one of these buttons is add a custom application launcher to the panel. To do this, right click on a panel of your choice and select 'Add to Panel...'. After this select 'custom application launcher' and fill in the details. To get you started, here are a few commands that close, unmaximise and minimise the window you are working in.

Close

```
xte 'keydown Alt_L' 'keydown F4' 'keyup F4' 'keyup Alt_L'
```

Unmaximise

```
xte 'keydown Alt_L' 'keydown F5' 'keyup F5' 'keyup Alt_L'
```

Minimise

```
xte 'keydown Alt_L' 'keydown F9' 'keyup F9' 'keyup Alt_L'
```

Below is a screenshot of my desktop. The buttons can be seen in the top panel on the right hand side.

If anyone has any other ideas on how to integrate a wiimote into the gnome desktop as a pointing device, I'd love to hear them, Either here, or on my blog: [http://wellithinkitscool.blogspot.com]("http://wellithinkitscool.blogspot.com")

Inabit,

Rob

---

