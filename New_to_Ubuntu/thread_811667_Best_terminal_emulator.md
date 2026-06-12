---
title: "Best terminal emulator"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-29
What is the best terminal emulator?

---

### Post by kamitsukai on 2008-05-29
well i dont know about best but i like kde's yakuake :D

---

### Post by cristo-father on 2008-05-29
> **kamitsukai said:**
> well i dont know about best but i like kde's yakuake :D

why do you recommend it?

---

### Post by FuturePilot on 2008-05-29
I like the good old gnome-terminal

---

### Post by atomkarinca on 2008-05-29
I like xterm.

---

### Post by Joeb454 on 2008-05-29
I just stick with gnome-terminal. Works perfectly fine for what I use it for (which is quite a lot) :)

---

### Post by cristo-father on 2008-05-29
> **atomkarinca said:**
> I like xterm.

I have used it, the only things i don't like is the default type of letter
 ,the background is black and the letters are white.
Know how to change this?

---

### Post by Joeb454 on 2008-05-29
Can you not edit some sort of profile file?

I actually have my background black (semi-transparent) with light grey text :)

---

### Post by cristo-father on 2008-05-29
> **Joeb454 said:**
> Can you not edit some sort of profile file?

I actually have my background black (semi-transparent) with light grey text :)

Is that in gnome-terminal?
How do i install it?

---

### Post by Bigtime_Scrub on 2008-05-29
They all work the same for me so I don't get how one can be better than the other.

---

### Post by FuturePilot on 2008-05-29
> **cristo-father said:**
> I have used it, the only things i don't like is the default type of letter
 ,the background is black and the letters are white.
Know how to change this?

That's why I like gnome terminal. It's very easy to customize it. In gnome terminal do Edit&#8594;Current Profile.

---

### Post by cristo-father on 2008-05-29
> **Bigtime_Scrub said:**
> They all work the same for me so I don't get how one can be better than the other.

When i say better i mean has more options...is more configurable...

---

### Post by Inxsible on 2008-05-29
I like xfce4-terminal -- but that's only because I use Xubuntu ;-)

---

### Post by cristo-father on 2008-05-29
Does there exit one where we can press a key and it pops up or one where we 
can have 4 organized in squares... i am just getting some ideas.:)

---

### Post by Joeb454 on 2008-05-29
I have a shortcut for gnome-terminal - does that count? ;)

And there's tilda, which is a drop down terminal, though I believe it requires some sort of compositor :)

---

### Post by FuturePilot on 2008-05-29
> **Joeb454 said:**
> 

And there's tilda, which is a drop down terminal, though I believe it requires some sort of compositor :)

Nope, it can run without a compositor. Only if you want true transparency with it do you need a compositor. :)

---

### Post by cristo-father on 2008-05-29
How about one where when the process in question ends it pops up or shuts down or does another process?

---

### Post by mali2297 on 2008-05-29
> **cristo-father said:**
> I have used it, the only things i don't like is the default type of letter
 ,the background is black and the letters are white.
Know how to change this?

The configurations for xterm are set in the file **~/.Xdefaults**. You can also specify options in the command line. For example,
```

xterm -bg "white" -fg "black"

```
will open the terminal with black text on white background.

Personally, I use rxvt-unicode mostly. It is similar to xterm (also uses ~/.Xdefaults) but is somewhat lighter.

---

### Post by Joeb454 on 2008-05-29
> **FuturePilot said:**
> Nope, it can run without a compositor. Only if you want true transparency with it do you need a compositor. :)

I sit corrected :)

---

### Post by cristo-father on 2008-05-29
Installed gnome-terminal and liked it.:)

---

### Post by Joeb454 on 2008-05-29
Glad to hear it :)

---

### Post by Tomatz on 2008-05-29
I like gnome terminal. Its lightweight, functional, and starts in milliseconds (unlike konsole).

Plus you can bling it out easily ;)

---

### Post by cristo-father on 2008-05-29
> **Tomatz said:**
> I like gnome terminal. Its lightweight, functional, and starts in milliseconds (unlike konsole).

Plus you can bling it out easily ;)

How do you make it transparent?

---

### Post by Tomatz on 2008-05-29
> **cristo-father said:**
> How do you make it transparent?

Open gnome-terminal then:

*Edit, current profile, effects*

;)

---

### Post by llamakc on 2008-05-29
> **Joeb454 said:**
> I have a shortcut for gnome-terminal - does that count? ;)

And there's tilda, which is a drop down terminal, though I believe it requires some sort of compositor :)

Tilda is so sweet. It's my favorite one by far.

---

### Post by cristo-father on 2008-05-29
> **Tomatz said:**
> Open gnome-terminal then:

*Edit, current profile, effects*

;)
It doesn't work if i drag the bar to the left the background gets black.

---

### Post by gareth_005 on 2008-05-29
+1 for Tilda.

I setup mine to fill the desktop and transparent with no borders, then I press F12 to drop it and F12 to hide it.

---

### Post by cristo-father on 2008-05-29
> **gareth_005 said:**
> +1 for Tilda.

I setup mine to fill the desktop and transparent with no borders, then I press F12 to drop it and F12 to hide it.

I noticed i can configure various "tildas" how do i choose to edit 1 of the 
many i have?

---

### Post by Tomatz on 2008-05-29
> **cristo-father said:**
> It doesn't work if i drag the bar to the left the background gets black.


What graphics card/drivers are you using?

---

### Post by Joeb454 on 2008-05-29
For a truely transparent terminal, you'll need some sort of compositor enabled, such as compiz-fusion for it to work :)

---

### Post by gareth_005 on 2008-05-29
> **cristo-father said:**
> I noticed i can configure various "tildas" how do i choose to edit 1 of the 
many i have?

I don't think you can bind keys to a specific instance of Tilda, I only have one instance running but you can right-click to open a new tab and the tabs will then show.

In preference the last tab is keybindings, grab a key there and Tilda will show or hide when pressed.

---

### Post by Xerp on 2008-05-29
I think it kinda depends which terminal you're trying to emulate, though most everything handles VT100.

---

### Post by kaiju on 2008-06-24
> **mali2297 said:**
> Personally, I use rxvt-unicode mostly. It is similar to xterm (also uses ~/.Xdefaults) but is somewhat lighter.

sorry for being late here, but can someone please confirm this? i always thought xterm was the lightest there is, with everything else just having more bling...

---

### Post by _sphinx_ on 2008-06-24
I use konsole only because it has a facility of saving the profile and so I get the same tabs after opening that I have saved. But its launching takes more time as compared to gnome-terminal. I searched a lot to get the same facility in gnome-terminal but all in vain. If anybody knows, it would be a great help.

---

### Post by mali2297 on 2008-06-24
> **kaiju said:**
> sorry for being late here, but can someone please confirm this? i always thought xterm was the lightest there is, with everything else just having more bling...

I'm sure neither is the lightest. (There are also aterm, rxvt,...).

The thing with rxvt-unicode is that it can be run as a daemon with multiple terminal windows within the same process, thus saving memory. If you never use more than one terminal window, then xterm might be a slightly lighter alternative.

---

### Post by cariboo on 2008-06-24
To change the background transparency in gnome-terminal, right click anywhere in the terminal and select Profile-->Profile_Preferences, then click the background tab, select Transparent background and move the slider to suit your preferences

Jim

---

