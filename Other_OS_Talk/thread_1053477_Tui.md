---
title: "Tui?"
date: 2009-01-28
forum: Other OS Talk
---

### Post by metalf8801 on 2009-01-28
are there any Linux distributions that still use a TUI (text user interface)? I'm not talking about a command line interface but an interface with text menus

---

### Post by kk0sse54 on 2009-01-28
Tui as in this? 
[ATTACH]101335[/ATTACH]

---

### Post by jrusso2 on 2009-01-28
That picture so reminds me of some of the old shells they used to sell for DOS.

---

### Post by kk0sse54 on 2009-01-28
> **jrusso2 said:**
> That picture so reminds me of some of the old shells they used to sell for DOS.

It's a pic of FreeDOS :)

---

### Post by metalf8801 on 2009-01-28
> **C!oud said:**
> Tui as in this? 
[ATTACH]101335[/ATTACH]

No thats a full GUI isn't it?  What I'm thinking of is something like wonder plus which is what I used on my first computer a 286 ran DOS which my dad got in the late 80s.

---

### Post by zmjjmz on 2009-01-28
Look into twin --  it isn't a distro, it's more like X. I would recommend using gpm with it.

---

### Post by fistfullofroses on 2009-01-28
> **metalf8801 said:**
> No thats a full GUI isn't it?  What I'm thinking of is something like wonder plus which is what I used on my first computer a 286 ran DOS which my dad got in the late 80s.

look into INX, it uses a lot of NCurses.

---

### Post by K.Mandla on 2009-01-28
[dvtm]("http://www.brain-dump.org/projects/dvtm/") might also appeal to you.

---

### Post by sertse on 2009-01-28
+1 INX. It runs from console and has menus, making it pretty user friendly.

Hijacking, but I wish someone would make a gui version of dvtm... It was the only tiling "wm" I found easy to understand.

---

### Post by zmjjmz on 2009-01-28
> **sertse said:**
> +1 INX. It runs from console and has menus, making it pretty user friendly.

Hijacking, but I wish someone would make a gui version of dvtm... It was the only tiling "wm" I found easy to understand.

XMonad is basically the same thing >.>
(but graphically)

---

### Post by kk0sse54 on 2009-01-28
> **zmjjmz said:**
> XMonad is basically the same thing >.>

Xmonad is definetely not the same thing as dvtm. Xmonad is a tiling *window manager* while dvtm (dynamic virtual *terminal manager*)  is intended to bring tiling to the terminal.

---

### Post by cardinals_fan on 2009-01-28
> **C!oud said:**
> Xmonad is definetely not the same thing as dvtm. Xmonad is a tiling *window manager* while dvtm (dynamic virtual *terminal manager*)  is intended to bring tiling to the terminal.
Yes, but the poster in question was requesting a version of dvtm for graphical apps.

---

### Post by arvevans on 2009-01-29
Sort of tongue-in-cheek but try this:

[HTML]
#!/bin/sh
# tui Text Line Interface
#
clear
while true
        do
        echo -n "Enter a textual Command: "
        read junk
        echo <`$junk`
        done
[/HTML]

Is that what you wanted for a Text Line Interface?
_._

---

### Post by cammin on 2009-01-29
[http://en.wikipedia.org/wiki/Text_user_interface](http://en.wikipedia.org/wiki/Text_user_interface)

---

### Post by init1 on 2009-01-31
> **C!oud said:**
> Tui as in this? 
[ATTACH]101335[/ATTACH]
Technically, that's graphical

> **jrusso2 said:**
> That picture so reminds me of some of the old shells they used to sell for DOS.
Indeed, it's OpenGem. 

> **metalf8801 said:**
> No thats a full GUI isn't it?  What I'm thinking of is something like wonder plus which is what I used on my first computer a 286 ran DOS which my dad got in the late 80s.
Not really. There's Midnight Commander, but that's more of a file manager.

---

