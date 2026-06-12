---
title: "Switching windows or apps"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by frogo on 2012-02-07
Hello, 

(disclamer: as part of my getting used to Unity New Year resolution, I'm just fishing out for tips re. simple behavioral oddities that puzzle me. No big deal, no great distress, no axe to grind, I'm sorry I can't spend hours scouring the web for figuring out these and I presume the answers are quite straightforward to anybody more familiar with Unity than I am. Thanks for your understanding and any input. )

I still have a hard time managing my windows. I typically have to resize and place them so that they straddle each other in order to be able to quickly switch between them (in a click). 

The alternative ways of window switching I am aware of are:
1- Alt+Tab: brings up a bar, seems hierarchical with first level being running apps and if i wait a bit it digs into existing instances
2- using the lateral side bar

Ad 1. I can't get used to 1. It's confusing and brings up things that are not necessarily relevant. I don't think in terms of Apps but in terms of tasks and these tasks typically involve different instances of multiple apps. 

Ad 2. This is long winded. Also, it leads to some aggravation when multiple workspaces are used. 

Years ago, I had a Mac and you could set up the thing so that pointing to a corner would bring about all opened windows in a workspace. There is something similar to this in the way unity works (esp when using 2). But again, it's application oriented. Also, doing 2, you can left click on the space icon on the side bar, it shows the spaces. But then it's all cluttered or if you have a full screen window opened in a space, you can't figure out what else is there... 

To cut the chase: 

Is there a straightforward, convenient way of switching windows or apps i) within a single space and ii) across spaces?

Alternatively, what is the mental gymnastic I have to get used to in order to get used to the Unity way?

many thanks
f

---

### Post by ikt on 2012-02-07
> **frogo said:**
> Alternatively, what is the mental gymnastic I have to get used to in order to get used to the Unity way?

[http://askubuntu.com/questions/36274/tips-and-tricks-for-unity](http://askubuntu.com/questions/36274/tips-and-tricks-for-unity)

[http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448](http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448)

I don't really have an issue moving between windows.

if I have 10 terminal windows open, 1 click on the terminal icon in the side bar will bring up the last terminal open, 2 clicks will bring up all terminal windows.

Or are you looking for super+w ?

Not sure I fully understand the issue.

---

### Post by Frogs Hair on 2012-02-07
Selecting the active icon from the launcher will will place the application selected on top in a single workspace .

If multiple workspaces are in use selecting the active icon from the launcher will open the workspace the application is being used in and place it in the forefront .

When selecting the workspace icon as an overview it is possible drag visible applications from one space to another. 

The Gnome Shell has an overview function similar to what you described . Moving the pointer to the top right corner or using the super key gives an overview of open applications in a workspace. Whichever application is selected in that space comes to forefront . You can add workspaces with a shell extension .

As with anything , use and practice make better not perfect .

---

### Post by frogo on 2012-02-07
> **ikt said:**
> [http://askubuntu.com/questions/36274/tips-and-tricks-for-unity](http://askubuntu.com/questions/36274/tips-and-tricks-for-unity)


I knew about this, but it's one of the things I haven't had time combing through yet :(

> **ikt said:**
> [http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448](http://blip.tv/jorge-castro/how-i-multitask-in-unity-5015448)


This is actually extremely enlightening. It shows in particular that the multitasking perspective underpinning Unity is very foreign to the way I work. From my standpoint, there's no multitasking in this vision. The idea of mapping a workspace to an app or type of app is just impractical and counterproductive and to my mind entirely defeats the purpose of a 'workspace' --- replaced with an 'appspace' so to speak. If I worked the way indicated in the video, I would need 3 or 4 machines. 

I don't mean to rant. It's actually very useful to realise this and shows I have to pay attention to getting the new gist, so I'm very grateful for the demo. 

> **ikt said:**
>  I don't really have an issue moving between windows.

if I have 10 terminal windows open, 1 click on the terminal icon in the side bar will bring up the last terminal open, 2 clicks will bring up all terminal windows.

Or are you looking for super+w ?


Well, probably yes. I'm really just discovering this so I'm not comfortable with it yet but i believe indeed that's the sort of stuff I need to train myself at using. That and I should probably define more keyboard shortcuts. 

> **ikt said:**
> Not sure I fully understand the issue.

For clarification, perhaps, I think the main issue is that Unity relies on tricks, shortcuts and intuitions that are entirely foreign to me. 

For the little story, while ubuntu has been a very productive system for my purpose, the consistent drawback has been that it does require to either invest a lot of time and energy into getting to grip with it and the way it works or, more often in my case, to just bite many bullets and live with workarounds that I don't understand and can't reapply. The main issue being that I'm quickly lost with computers... 

My impression just now is that up until recently I was mainly struggling in Ubuntu with installing and configuring things. This was already enough of a distraction. But Unity comes across as having brought that sort of distraction to the level of everyday use. Before it could take days to set things up, now things are smoother on the set up side, perhaps because I have my routines, but the user experience is really crippled.

I'm sure nobody cares about my thoughts on the matter and that's fine by me, just meant to clarify the general mindset here.

Very many thanks for your input
f

---

### Post by frogo on 2012-02-07
> **Frogs Hair said:**
> Selecting the active icon from the launcher will will place the application selected on top in a single workspace .

If multiple workspaces are in use selecting the active icon from the launcher will open the workspace the application is being used in and place it in the forefront .

I'm confused by the way it works when an app, say a terminal, is used in multiple workspaces. 

The behavior of 1 click seems to change depending on the number of instances opened, where they are opened and so on.

Example: 
- 2 terminals in workspace 1, 1 terminal in WS4
From WS1, 1 click on terminal icon (assume it's in the bar) brings up the 2 terminals in WS1 
From WS3, 1 click on terminal icon brings up the 2 terminals in WS1
From WS4, 1 click on terminal icon brings up the 3 terminals indiscriminately of the WS

- 2 terms in WS1, 2 terms in WS4
WS1 and WS4: Sometimes the terms in the active WS come up, sometimes it's all the terms in any WS (like 2 clicks)
WS2 and WS3: Sometimes one, sometimes both of either WS1's or WS2's terms, sometimes nothing at all (in that later case, you're in WS2, you click on the icon once, nothing happen, you double click on the icon, nothing happens...)

There's no telling what goes on, you get different results depending on the positions of the terms relative to other opened apps or even relative to each other. E.g. if WS4 is term1 on top then firefox then term 2 in the back, you get something different when clicking the term icon from WS3 than if both terms were on top).

This is just to emphasize that I'm quickly confused and typically can't find things easily or reliably, rarely different than random. 

> **Frogs Hair said:**
> When selecting the workspace icon as an overview it is possible drag visible applications from one space to another. 


Thanks for that, pretty handy.

> **Frogs Hair said:**
>  The Gnome Shell has an overview function similar to what you described . Moving the pointer to the top right corner or using the super key gives an overview of open applications in a workspace. Whichever application is selected in that space comes to forefront . You can add workspaces with a shell extension .


Is this in the context of the "**[B]Sticky:**[/B]                                      [COLOR=#980101]**[ubuntu]**[/COLOR]                          [Getting back to Classic Gnome in 11.10]("http://ubuntuforums.org/showthread.php?t=1859960") "  thread in this forum?

> **Frogs Hair said:**
>   As with anything , use and practice make better not perfect .

agreed! thanks for your help on the way :)

---

### Post by lechien73 on 2012-02-07
I have the Shift+Alt+Up combination, which shows all open windows in the current workspace, bound to the bottom left corner of the screen. So all I have to do is flick the mouse down there and the window picker starts up.

[LIST]
[*]To set this, open **CompizConfig Settings Manager**
[*]Then navigate to **Window Management -> Scale**
[*]Click **Bindings**
[*]Click the items with the monitor icon to set the window bindings for **Initiate Window Picker** or **Initiate Window Picker for all windows**
[/LIST]

Hope this helps.

---

### Post by philinux on 2012-02-07
See links in Sig. And also check out what's due in April.

 [http://ubuntuforums.org/showthread.php?t=1860102](http://ubuntuforums.org/showthread.php?t=1860102)

---

