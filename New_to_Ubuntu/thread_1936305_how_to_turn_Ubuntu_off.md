---
title: "how to turn Ubuntu off?"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Grrruff on 2012-03-05
how do I turn the lousy thing off?
Currently the only way I can find it to press and hold the power button.  I see no handy off switch like old versions used.

Tearing my hair out over what should be simple things.

ARRRRRRRRG!

---

### Post by matt_symes on 2012-03-05
Hi

What version of *buntu are you using ? Ubuntu, Kubuntu, Xubuntu, Lubuntu ?

Which release are you using ? 10.04, 11.04, 11.10 ?

Kind regards

---

### Post by ubudog on 2012-03-05
If you press the power button once, not holding it down, a window *should* pop up with shutdown and hibernate options.

---

### Post by grahammechanical on 2012-03-05
Are you telling us that you have a join date of 2008 and you cannot work out that the cog icon at the extreme right of the top panel gives you a menu that includes Shutdown?

The first thing that I did when I installed 11.04 more than a year ago was to click everything insight and out of sight to see what it did.

Regards.

---

### Post by souravc83 on 2012-03-05
type on the terminal:

[HTML]sudo shutdown -h 1[/HTML]

---

### Post by Dreamer Fithp Apprentice on 2012-03-05
Or put that ^ in a launcher, make an "off" sign with gimp to use for the launcher icon and put in a panel if you use a panel or on your desktop if you use a desktop or you can right click on menu and edit menu if you have a menu and add the command as a menu entry. I'd bet if you look around a bit, you can probably find some command syntax that wouldn't require you to enter your password.

But about the lice, I dunno, you might try some insecticide.

---

### Post by daslinkard on 2012-03-05
I've been on Linux for about 60 days...you could also type into the terminal...or go to Google for quicker responses...personally I use the following...

> sudo shutdown -h now

---

### Post by kurt18947 on 2012-03-06
> **Grrruff said:**
> how do I turn the lousy thing off?
Currently the only way I can find it to press and hold the power button.  I see no handy off switch like old versions used.

Tearing my hair out over what should be simple things.

ARRRRRRRRG!

Not using a distro that defaults to gnome shell, are you?  Gnome shell does not include "off" or "restart" by default, only "suspend".  To get "off" requires placing the cursor over "suspend" the pressing the "alt" key as I recall.  Pretty silly, thank goodness there are extensions to restore normal power choices.

---

### Post by muteXe on 2012-03-06
I sympathise with OP. Sometimes I have to shutdown via the command line because my power-off button simply isn't there sometimes. Indeed, sometimes it's replaced with an 'm' symbol.
I don't have much of a problem with this, just saying that OP's not alone. Would be interesting to find out which version he or she is on (i'm 10.04 ubuntu).

---

### Post by Grenage on 2012-03-06
> **kurt18947 said:**
> Not using a distro that defaults to gnome shell, are you?  Gnome shell does not include "off" or "restart" by default, only "suspend".  To get "off" requires placing the cursor over "suspend" the pressing the "alt" key as I recall.  Pretty silly, thank goodness there are extensions to restore normal power choices.

Indeed; for the record Fedora does have a shutdown option by default (gnome shell).

---

### Post by NikTh on 2012-03-06
> **grahammechanical said:**
> Are you telling us that you have a join date of 2008 and you cannot work out that the cog icon at the extreme right of the top panel gives you a menu that includes Shutdown?

The first thing that I did when I installed 11.04 more than a year ago was to click everything insight and out of sight to see what it did.

Regards.

Hahaha , it reminds me ... Me. When for the first time installed gnome-shell. Search for the (hidden) shutdown button , did not work (not yield) . Hahah, after one year of use(ubuntu) , i felt like a noob .Finally Google search  did the trick :p

---

### Post by Script Warlock on 2012-03-06
excuse him that was the year of 8.04 gnome2 and now its gnome3 and unity.

---

### Post by Grrruff on 2012-03-06
To All:  Yes I joined this forum back in 2008.  Ubuntu did not have the compatiblity or tools I needed at that time.
I wiped the hard drive and forgot about it.  Recently a friend suggested I give it another try.
I wiped one of our old Windows machines and installed Ubuntu 11.10.  
Imagine my suprise when many of the intuitive buttons were missing.  
Unity??? 
Gahhhh!  Just booted for the second time this morning.  Now there is a Gear Icon at the top right.  Wasn't there before.
It has the shutdown option in the menu.  Soooo flakey.


ubudog:  Thanks.  That works.  Seems silly there is no button on screen to get there.
a lot of my PC's are buttoned up inside enclosures where getting to the physical power button is not easy.
(Harsh environment(s))

grahammechanical :  I have been clicking everywhere.  Not much happens.  
In fact some of the left hand toolbar buttons have gone black.

souravc83:  "sudo shutdown -h 1"?  There is no apparent terminal button either.

Dreamer:  My knowledge base is nil.  Is a launcher what the desktop refers to as a "Link"?
How do you manually create one?  I would love to know.  Menus?  I see no menus whatever.
(Going to ignore your comments about hygene. :))

Kurt18947:  Where is this magical "Suspend" button?  Oh I see it showed up under the new gear button.

Thank You one and all.

---

### Post by squilookle on 2012-03-06
I've heard similar complaints about shutting down the Windows 8 previews. Might be a familiarity issue rather than a design issue. 

Bearing that in mind, I'm sure using the desktop for longer you will natually get the hang of it, and possibly looking at some tutorials on using the desktop might help you as well. :)

---

### Post by Dreamer Fithp Apprentice on 2012-03-09
> **Grrruff said:**
> To All:  Yes I joined this forum back in 2008.  Ubuntu did not have the compatiblity or tools I needed at that time.
I wiped the hard drive and forgot about it.  Recently a friend suggested I give it another try.
I wiped one of our old Windows machines and installed Ubuntu 11.10.  
  . . . 

I'll probably be chastised for saying it, because some of the mods here seem to regard any suggestion that the current default install is less than wonderful as even more taboo than discussing enabling the root account, **BUT - **
you might want to try returning the user interface to something more similar to what you used when you had Ubuntu before, without all the grandstanding glitz that was substituted for function. There are several ways to consider if that appeals to you:

1 - at the log in screen, use the little gear icon to the right of the password field to change the default session to "gnome classic, no effects". That type of session will be more familiar, and if you don't have a lot of scripts that used the old gnome 2 tools it can be tweaked into something fairly usable. I tried this approach for a couple of weeks and commented positively on it and included a screenshot of my desktop using it in post # 8 of this thread:
[http://ubuntuforums.org/showthread.php?t=1925542](http://ubuntuforums.org/showthread.php?t=1925542)

2 - install Mate, which is a new fork of gnome 2, and check that as your default session type. This is what I use now, when I'm using Oneiric instead of booting from my Maverick partition, and most likely what I will continue to use unless and until I abandon Ubuntu entirely. In the same thread cited above, in posts 12 & 13, I wrote about why I ultimately found Mate more satisfactory. Mainly because of better support for legacy scripts which may or may not apply to you. There are also differences in what themes are supported if that is important to you.

3 - Switch to Mint. It is a Ubuntu derivative more purely user driven and less slavishly devoted to the canonical Canonical path and has Mate in its official repository. I haven't tried it yet myself but I plan to. A lot of Mint users seem quite pleased with it.

4 - Install an older version. I still regard my Maverick as my dependable boot partition for getting real things done without distracting, time wasting surprises, although I am close to having Oneiric with Mate ready to replace it. Maverick was the last version with the traditional interface as the default. With older versions you will eventually get into the issue of unpatched vulnerabilities. Whether or not this is really significant of course depends on the details of how you use it. 

> **Grrruff said:**
> Dreamer:  My knowledge base is nil.  Is a launcher what the desktop refers to as a "Link"?
How do you manually create one?  I would love to know.  Menus?  I see no menus whatever.
 If by "THE desktop" you mean the current default Gnome 3 & Unity setup, I can't say for certain, as I was so repelled by the absurd awkwardness of that UI I didn't try to learn all of it's nomenclature.  Generally, I think of a link as something that might point to any kind of file, while a launcher specifically points to an executable program of some sort. In this case, since it would contain a simple command I guess it would be implicitly pointing to bash in the bin directory, probably via an environment variable specifying it as the default command interpreter. I'm not sure how you go about creating one in the default environment but on my Mate desktop I can create one by right clicking on the desktop and clicking "create launcher". On my Mate panel or on a Gnome 2 panel, you right click on the panel (with gnome 3 it's alt right click or control right click or something like that) and click "add to panel", then "custom application launcher" and then "add". Leave it set to "application" in the first field [As a side note, in doing this to make sure I tell you the right sequence, I see you can select "location" also - so my distinction between "launcher" and "link" seems less than perfect - someone else may wish to elaborate on that]. Then give it a name in the next field. In the example in question enter the command as given by souravc83 in the next field. In other cases you could use the browse button to browse to an executable program. The comment field and the icon are optional. If you want to change the icon click on it and navigate to a suitable mnemonic picture. Click "ok" and you're done.

As for the menus, I'm not sure you have any in the default UI. In any of the more traditional UIs you right click (in Gnome 3, Gnome classic panel, alt right click) on the menu (in what was the default until recently, the headings were "Applications, Places, System" or in a more compact menu it was just the round Ubuntu icon) and click "edit menu". The Mate devs don't have that quite working yet, so in Mate, you have to bring up a terminal and enter the command "mozo".  You'll get a graphical ap for editing the menu, part of which looks and works just like the one you use for launchers. You can add a command mozo to the applications menu with it so that next time you can edit the menu conveniently without having to remember the name of the menu editor ap.

I hope this is helpful.

---

### Post by d4m1r on 2012-03-09
> **grahammechanical said:**
> Are you telling us that you have a join date of 2008 and you cannot work out that the cog icon at the extreme right of the top panel gives you a menu that includes Shutdown?

The first thing that I did when I installed 11.04 more than a year ago was to click everything insight and out of sight to see what it did.

Regards.


Quoted for truth!

---

### Post by Dreamer Fithp Apprentice on 2012-03-13
> **Grrruff said:**
>  . . . "sudo shutdown -h 1"?  There is no apparent terminal button either. . . . 
Traditionally, control-alt-T would get you a terminal, not only when no button for one was apparent, but often even when the whole bloody GUI was acting flaky and ignoring your clicking. It seems in the latest "improved" version Canonical in their wisdom decided this was too great a power to entrust to lowly users and apparently disabled that by default. But you can turn it back on if you can figure out how to get to the gnome-keybinding-properties dialogue. At least I assume that is the right nomenclature. I use the Mate desktop and for me it's mate-keybinding-properties. If you ever get a terminal entering that string, that is "gnome-keybinding-properties" without the quotation marks should bring you to the right place. Or if you can get a menu its System,Preferences,KeyboardShortcuts. If you can't find a menu try relogging and before you log back in click the little gear to the left of the password box and select "gnome classic, no effects" to get a more trad desktop which I believe will have a menu. If not, try alt-right click on the top panel and add-to-panel,main-menu or something like that. When you get the keyboard shortcuts dialogue up you should be able to click "run a terminal" and assign any shortcut key combo that appeals to you. I suggest the trad control-alt-T because it is easy to remember and you will see it assumed in many how-tos on the web. Another way would be alt-F2 which will give you a field in which you can enter one command. Of course you can make the command "gnome-terminal" and then have a full terminal.

> **d4m1r said:**
> Quoted for truth! OP, explained that more than adequately. Perhaps you didn't read it.

---

