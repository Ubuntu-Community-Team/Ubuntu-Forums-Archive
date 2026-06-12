---
title: "Possible to change behaviour of the &quot;^&quot; key?"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by enaecore on 2013-06-22
Hello, 

I'm coming from (or dual-booting) Win 7 and trying to get into Ubuntu since last night, so i'm completely newbie. 

Overall it seems quite neat, of course i need to build a basic understanding first but i think i'll figure that out over time via trial and error..

Though i ran into a more or less annoying issue while chatting.

My first question (and yes, i know its a ridicoulus one) is, if it's possible to change the behaviour of the "^" key so that it appears twice if pressing it twice instead of having to press it four times.

I'd be thankful for help and looking forward to becoming part of this (as far as experienced/read in various forums) friendly and competent community 


enaecore


PS: I hope i'm in the right section, i didn't really know where to post this.

---

### Post by Impavidus on 2013-06-22
That sounds like your keyboard has been configuered so that ^ is a dead key. This means that when you hit it once nothing happens, when you hit it followed by a character that can have an accent circonflexe you get that character with the accent (ô, &#309;, ê et cetera). To type the character itself you have to hit it twice, to type it twice you need to hit it four times. [This](https://help.ubuntu.com/community/GtkDeadKeyTable) gives some details on dead key behaviour.

To solve your problem you can change your keyboard layout. Note that there are alternatives to dead keys, which I find easier to use (but that's just me).

---

### Post by enaecore on 2013-06-22
Thanks for your answer, i will look for those different layouts as soon as i'm at home. What do you mean by alternatives? Simply another key/-combination?

---

### Post by Impavidus on 2013-06-22
My favorite is the [compose key](https://help.ubuntu.com/community/ComposeKey).

---

### Post by rewyllys on 2013-06-22
> **Impavidus said:**
> My favorite is the [compose key]("https://help.ubuntu.com/community/ComposeKey").Some more information on using the compose key is in [this ]("http://ubuntuforums.org/showthread.php?t=1416999&highlight=characters+keyboard")[thread]("http://ubuntuforums.org/showthread.php?t=1416999&highlight=characters+keyboard").

---

### Post by enaecore on 2013-06-22
After reading those pages (if i understand right) i don't think they actually fit my issue. 
The ComposeKey is used to create special characters by typing certain keys after pressing/holding a certain key/key-combination (like CTRL+AltGr followed by eg. 123), or did i get it wrong? That actually seems to me being a higher effort than just pressing "^" multiple times. 

Maybe you got me wrong, what i want is to get "^^" by pressing "^" twice.

In Windows it is a dead key as well but it triggers itself, by what i mean the appearance of the first "^" is triggered by the second press, following that, the second press reveals the second "^". 
Any way to set it that way? If not or not without going too deep, i'll be fine without it since i don't want to mess around with my system as a complete newbie yet.  
(oh and btw, the keyboard layout is german)

nonetheless, thanks for your help so far!

---

### Post by Impavidus on 2013-06-23
The idea behind the compose key is that you can type something line **compose**,**^**,**g** to get **&#285;**, instead of the sequence [COLOR=#ff0000]**^**[/COLOR],**g** to get the same letter (red denoting dead keys), so that you can turn the [COLOR=#ff0000]**^**[/COLOR] key into the **^**, allowing you to type ^^ with just **^^**. This saves some keystrokes when typing the isolated characters, but requires some extra typing when you need the accents. What's best depends on the amount of accents you need. In german you need quite a lot of Umlauts of course, but maybe those umlauted characters are already present on your keyboard layout.

It may also be possible to configure your keyboard such that typing shift+^ produces **^** and shift+AltGr+^ produces [COLOR=#ff0000]**^**[/COLOR], or something similar, to have the dead key and the live key both available. Shift+{^,^} would give ^^, shift+AltGr+^,h would give &#293;, the expected result with dead keys.

I don't know of a way making it work the same way as windows, although I'm not really familiar with the internals of accent handling in keyboard input.

Dead keys, compose sequences, the windows way of handling dead keys etc. all have their advantages and disadvantages, I think.

---

