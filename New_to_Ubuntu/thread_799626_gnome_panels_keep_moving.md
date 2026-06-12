---
title: "gnome panels keep moving"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Zedzero on 2008-05-19
I'm using two gnome panels: one for tasklist and one for everything else.
I want both of them to be at the bottom of the screen, tasklist being at top.

But whenever i restart or logout/login, they randomly move. sometimes panel 1 is on top of the other, sometimes panel 2. (They are at the bottom of the screen as they should be, but wrong order). I guess whicever loads first gets the bottom place, and the other one places on top of it.

How can i correct this?

---

### Post by abhiroopb on 2008-05-19
Thats really odd. Which version of *buntu do you have? how many monitors do you have?

---

### Post by Zedzero on 2008-05-19
ubuntu 8.04 with all updates.
and only one monitor.

---

### Post by Zedzero on 2008-05-19
can anyone help please?
(shameless bump)

---

### Post by medya on 2008-09-06
me too I have the same problem in the year 2008 ! in ubuntu hardy heron .

---

### Post by medya on 2008-09-07
oops sorry I thought this posted was sent in 2006 .

---

### Post by ajcrm125 on 2008-11-03
Yep... same exact problem here.  Been driving me nutz.

---

### Post by cariboo on 2008-11-03
Have you tried right clicking on the panel and locking it?

If you right click anywhere on the panel you will see a selection on the menu called Allow Panel to Be Moved, click that then move the panel to where you want, then right click on the panel again and select Lock Panel Position.

Jim

---

### Post by S0m3th1ngw13rd on 2009-01-24
Same issue here, both panels are always reversed when I log back in.  They are locked when I log out, and when I log back in they are in reverse of what they were and unlocked. #-o

---

### Post by Macca1024 on 2009-03-13
I'm having the same trouble.  It's trivial, but really annoying.  The panel properties don't have anything to indicate a stacking order, so I suspect that stacking panels on top of each other might not be the intended usage.  In any case SOMETHING has to dictate which order they go in, I just wish I knew what it was. :(

---

### Post by Macca1024 on 2009-03-14
And within minutes of typing that, I decide to go have another look, and I think I've found it!  Looking in the configuration editor (under applications->system tools in the default menu) there's a key by the name of
"/apps/panel/general/toplevel_id_list" which lists the active panels.  I swapped the order of the panels in the list, and now they appear to show up how I want them.  :D

---

### Post by 73ckn797 on 2009-03-14
> **cariboo907 said:**
> Have you tried right clicking on the panel and locking it?

If you right click anywhere on the panel you will see a selection on the menu called Allow Panel to Be Moved, click that then move the panel to where you want, then right click on the panel again and select Lock Panel Position.

Jim

+1

You can configure panels however you wish and "save" the changes.

---

### Post by Macca1024 on 2009-03-15
Ok, I spoke too soon, my idea didn't actually fix it, as the next time I booted up they were back around the wrong way.

73ckn797, that's not really helping us, unfortunately.  Locking the panels makes sure that it remembers what orientation we're setting the panel to, but the trouble we're having is when we've got two (or more) panels with the same orientation.  It won't remember what order to stack them in against the screen edge. 

Gnome-panel must be using SOMETHING to determine which way it puts them (as it consistently puts them the way I don't want them) but I can't find any doco suggesting what that something is (possibly as this might be outside the intended usage of the panels?).

---

### Post by Berserker v7 on 2009-03-15
Just a bit of clarification... does the order change alternately every time or is it always that the panel you want to be above the other shows up below it?

---

### Post by Macca1024 on 2009-03-15
For me it's the second option.  Every time I start the computer up, the panels are in the reverse order that I want them.  I suppose I could just move everything on the top panel to the bottom one (and vice versa), but it's bugging me that I can't just tell them what order to sit in.

---

### Post by Berserker v7 on 2009-03-16
> **Macca1024 said:**
> For me it's the second option.  Every time I start the computer up, the panels are in the reverse order that I want them.  I suppose I could just move everything on the top panel to the bottom one (and vice versa), but it's bugging me that I can't just tell them what order to sit in.

Thats pretty much it then... just shift all items on top panel to bottom one and vice versa... one-time business, not much of a bother... why blame the system when such practically simple solutions exist? ;)

---

### Post by orethrius on 2009-03-16
> **Berserker v7 said:**
> Thats pretty much it then... just shift all items on top panel to bottom one and vice versa... one-time business, not much of a bother... why blame the system when such practically simple solutions exist? ;)
I'd imagine that'd be because there's apparently no drag-and-drop *simple* solution, where it does what you'd expect, and there's some variable somewhere that dictates this behaviour.

---

### Post by Eneerge on 2009-04-30
I've seemed to find a solution for this without creating a new panel.  In a configuration file, the bottom panel is loaded first, and then the top panel is loaded second, which makes it appear on the top everytime.  You can change the startup order by modifying ~/.gconf/apps/panel/general/%gconf.xml

What you need to modify is at the very bottom of the file.  Here is the bit you need to modify:
```

    <entry name="toplevel_id_list" mtime="1241080568" type="list" ltype="string">
        <li type="string">
            <stringvalue>bottom_panel_screen0</stringvalue>
        </li>
        <li type="string">
            <stringvalue>top_panel_screen0</stringvalue>
        </li>
    </entry>
</gconf>

```You need to modify this file so that it looks like this (starting after the "object_id_list" entry):
```

    <entry name="toplevel_id_list" mtime="1241080568" type="list" ltype="string">
        <li type="string">
            <stringvalue>top_panel_screen0</stringvalue>
        </li>
        <li type="string">
            <stringvalue>bottom_panel_screen0</stringvalue>
        </li>
    </entry>
</gconf>

```All you do is change the order so that the bottom_panel_screen0 entry is last instead of first.  This fixed the problem for me.

---

