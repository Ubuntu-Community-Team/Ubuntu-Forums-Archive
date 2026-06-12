---
title: "german keyboard wiht french shortcuts?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by benste on 2008-05-16
Hy,
I'm using Ubuntu 8.04 with a german keyboard, but I often haveto write french things for school. Some keys like é ô are aviable via shortcuts - multiple keys. Is there a way to create a short cut for the C with the s under it? Something like "mod5+C" (Mod5 is called ALT Gr in germany)

---

### Post by pytheas22 on 2008-05-16
You could try US international with dead keys.  I think it's close to German, but it can still make accented characters for most languages easily, e.g.:

right alt + s = ß
right alt + , = ç
" + a = ä
' + E = É
" + [space] = "

I started using this while I was living in France with my American laptop (I am American); I do work in French, German and English.  This layout works best for me.  The only downfall is that you have to press the space bar to get " ' and so on.

If this doesn't work for you, you can try out different layouts using the System>Preferences>Keyboard utility.  I looked and didn't see an option under German layouts that allows ç, which is why I suggest US international with dead keys as the best option, but maybe you can find something better.

---

### Post by benste on 2008-05-17
if I would use US keyboard my normal printed signs would be wrong or?
like Y and Z anre changed  and ? isn't aviable via shift+ß
or?
-> is there no way to add some shortcuts -> like compiz effects - <super>+tab = Window switcher?

---

### Post by pytheas22 on 2008-05-17
[xkeycaps]("http://www.jwz.org/xkeycaps/") might be a better solution to what you're trying to do.  It can be installed through Synaptic.

I read about it at [http://sudan.ubuntuforums.com/showthread.php?t=515945](http://sudan.ubuntuforums.com/showthread.php?t=515945).

---

### Post by hvw on 2008-05-17
Easy! All you need is change you current layout manually. List all layouts (only xorg, not SCIM):
vm@vm-desktop:~$ ls /etc/X11/xkb/symbols/
Your currently using layout is:
vm@vm-desktop:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
[INDENT]OR[/INDENT]
vm@vm-desktop:~$ xprop -root | grep XKB
The easiest way is to use your current layout with current variant:
[INDENT]_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us,ru", ",winkeys", "grp:lwin_toggle"[/INDENT]
My configuration is 'us' with default variant (empty) and 'winkeys' as the variant for 'ru' layout. It rather difficult to create another variant for existing layout. But you can choose those chemin: 
[http://www.linux.com/articles/113715]("http://www.linux.com/articles/113715")
Back up you current layout:
vm@vm-desktop:~$ cp /etc/X11/xkb/symbols/ge ~/change.layout/ge.layout(backup)
Than you can copy french layout for desired symbols:
vm@vm-desktop:~$ cp /etc/X11/xkb/symbols/fr ~/change.layout/fr.layout(backup)
Find variant that you are desire and make it default. You can use mine as example (i just replaced 'us' with edited 'fr' one where i've changed default variant).

---

### Post by benste on 2008-05-17
Thank you all, but I found an easier solution.
Following the xkeycaps links I read about the gnome-tool for keyboard seings (I'll atach a screenshot)

ç and all other keys are already linked to the layout (only not printed to my keyboard) now I now about first secound and third level access like 1, ! and ¹ but how can I acess the fourth level ? 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=70489&stc=1&d=1211055004[/IMG]

---

### Post by hvw on 2008-05-17
If you mean the symbol in upper-right corner you should press <key>+Alt+Shift.
Is there are dead_grave (`), dead_acute(´), dead_circumflex (^), œ, Œ symbols? I can't see all of them.

---

### Post by benste on 2008-05-17
it's AltGr (here Iso_L) + shift + key

> Is there are dead_grave (`), is right of ß and ?
>  dead_acute(´),  also there only with shift
> dead_circumflex (^), left of the one
>  œAltGr + A
>  Œ  seems not to be attached or is it © ?

---

### Post by hvw on 2008-05-17
Actually, i can't type 'œŒ' (is not the same 'Ææ') and when i press Shift+Alt<same key for '`' and '´'> it makes only cedilla (ç&#281;) not '^'! (with different key codes). That's for default german keyborad.

---

### Post by hvw on 2008-05-17
I've found at last dead_circumflex! But what does it mean ('seems not to be attached or is it © ?') What attachement?

---

### Post by benste on 2008-05-19
Sorry  i didn't meen attach --> replace it with "linked to key" or so

Did you look in your own keyboard settings? there  should also be an russian keyboard aviable
+ the gnome tool which is preinstalled also shows which key is currently pressed

---

