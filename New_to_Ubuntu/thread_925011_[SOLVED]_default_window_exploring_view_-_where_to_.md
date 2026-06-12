---
title: "[SOLVED] default window exploring view - where to set?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by lazylew on 2008-09-20
when I started using Ubuntu clicking "places" the Nautilus window was always split in a left pane with a main directory view and a right one with more details, like windows explorer

I don't know what happened but this view type is gone; it's all one main window which is very unpractical

I went over all settings and administration possibilities more than twice, but can't find where to reset this properly

---

### Post by TheUbGuy on 2008-09-20
Click on View, then check Side Pane.

---

### Post by lazylew on 2008-09-20
> **TheUbGuy said:**
> Click on View, then check Side Pane.
there's no "side pane" option...

---

### Post by TheUbGuy on 2008-09-20
Strange .... there is here,

What about pressing F9 ?

---

### Post by lazylew on 2008-09-20
> **TheUbGuy said:**
> Strange .... there is here,

What about pressing F9 ?
F9 + alt minimizes the window but just F9 does nothing

---

### Post by TheUbGuy on 2008-09-20
What options do you have under 'View'? What version of Ubuntu are your running?

---

### Post by drs305 on 2008-09-20
Open gconf editor and drill down to: 

/apps/nautilus/preferences/

There are settings for opening with the side pane there.


If you still can't see it, it's possible the panel has shrunk and is all the way to the left. Try clicking on the left border and dragging to the rigth - that may 'expose' the side panel.

---

### Post by lazylew on 2008-09-20
> **TheUbGuy said:**
> What options do you have under 'View'? What version of Ubuntu are your running?
stop (grayed out) - reload - reset view to defaults (doesn't do the trick) - show hidden files - arrange items - clean up by name (gray) - zoom in - zoom out - normal view - view as icons - view as list

---

### Post by lazylew on 2008-09-20
> **drs305 said:**
> Try running these commands from metacity (gconf-editor)...
before I do something stupid; that's typing commands in the terminal as sudo, right? (don't know metacity...)

---

### Post by drs305 on 2008-09-20
> **lazylew said:**
> before I do something stupid; that's typing commands in the terminal as sudo, right? (don't know metacity...)

I rewrote the previous entry to make you feel more comfortable. You open metacity in terminal with the command:
```
gconf-editor
```

Then you expand the categories to find the settings you are looking for. In this case, go to: apps > nautilus > preferences  

There are entries for side_pane_view  etc.

There are tick-boxes. If you don't know what a setting it, highlight it and an explanation of what the setting does appears in the lower right pane.

In that block, there are entries about if the nautilus side pane should appear and what it should look like. You don't need sudo since these will be effecting only your settings.

You did the right thing about asking before doing something. If you aren't sure it's better to get clarification first.

---

### Post by lazylew on 2008-09-20
> **drs305 said:**
> ...In that block, there are entries about if the nautilus side pane should appear and what it should look like...

thanks for the clarification

I did get as far as the gconf settings this time, but in >preferences>side pane view there's no tick box

instead there's the text (value) "nautilus tree sidebar"

double clicking it will let me change the value, but that's not it, right?
I guess I'm almost there :-)

---

### Post by drs305 on 2008-09-20
Below the side_pane_view NautilusPlacesSidebar entry there should be an entry for "start_with_sidebar". That should be ticked, and that should solve your problem.

The other setting to check would be 3 above that, sidebar_width. That should be set to something like 150 or so - definitely NOT '0' and it should definitely have some value in it. If it doesn't, add it by double clicking the blank area and then inserting a pixel value.

---

### Post by Mornedhel on 2008-09-20
> **drs305 said:**
> You open metacity in terminal with the command:
```
gconf-editor
```

Wha ?...

How what wha ?...

Why d'you call it "metacity" ?... Metacity is the Gnome default window manager. What does that have to do with the GConf editor ?...

I mean, everything you said looks correct, apart from calling gconf-editor "Metacity", but it's really a weird error to make, especially coming from someone with 2000+ posts here.

Edit: OK, worried for nothing.

---

### Post by TheUbGuy on 2008-09-20
This is what my settings look like, if it would help.

---

### Post by lazylew on 2008-09-20
start with sidebar was already ticked and side width was on 288

---

### Post by drs305 on 2008-09-20
lazylew,

If those settings are ticked I don't know why you aren't seeing the side pane. You could try uninstalling nautilus and then reinstalling it via synaptic - it won't hurt anything.


> **Mornedhel said:**
> Wha ?...

How what wha ?...

Why d'you call it "metacity" ?... Metacity is the Gnome default window manager. What does that have to do with the GConf editor ?...

I mean, everything you said looks correct, apart from calling gconf-editor "Metacity", but it's really a weird error to make, especially coming from someone with 2000+ posts here.

Mornedhel,

Just a slip. I was researching a gconf-editor metacity keybinding problem at the same time. It's the listing just above nautilus in the gconf list. Guess it was too early in the morning. Apologies.

---

### Post by Mornedhel on 2008-09-20
> **drs305 said:**
> Just a slip. I was researching a gconf-editor metacity keybinding problem at the same time. It's the listing just above nautilus in the gconf list. Guess it was too early in the morning. Apologies.

'K, guess I jumped the gun as well. I'm used to weird and incorrect advice being posted by newcomers who just had their problem solved, are eager to help others, and end up misquoting solutions ; this was just... well... while not dangerous at all, it *was* worrying.

---

### Post by lazylew on 2008-09-20
> **drs305 said:**
> lazylew,

If those settings are ticked I don't know why you aren't seeing the side pane. You could try uninstalling nautilus and then reinstalling it via synaptic - it won't hurt anything.
I did re-installation via synaptic and even restarted the computer.
Still the same...

Just to be sure: I open Nautilus by clicking Places and than Home Folder or Documents and such, correct? I do remember seeing the name Nautilus in the top bar in the past, but now it just says "documents" and the likes.

---

### Post by drs305 on 2008-09-20
If you haven't changed any of the default settings, it should be Nautilus that is opening. You can try opening it via a terminal and typing "nautilus" just to be sure. If you do this you can also check to see if there are any messages displayed in the terminal window when you enter it there. If any  errors are present they should be displayed.

---

### Post by lazylew on 2008-09-20
> **drs305 said:**
> If you haven't changed any of the default settings, it should be Nautilus that is opening. You can try opening it via a terminal and typing "nautilus" just to be sure...
Opening it that way gives the same view.
I also went back to synaptic to try with remove instead od reinstall.
It said I also needed to remove nautilus-cd-burner and -sendto and -share and -desktop, so I did.
When installing them again synaptic can't find any "nautilus-desktop".
Everything still looks the same...

---

### Post by lazylew on 2008-09-20
aha!
I read some more on browser and spatial mode and found something useful

right clicking on a folder gives me browser mode option :-)

now I still have to find how to set this as default view 
back to rtfm again ;-)

---

