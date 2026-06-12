---
title: "Trying to make sense of keyboard --- pulling my hair"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by DDDa on 2012-11-09
Hi, I have two problems that may or may not be related, so I'll separate them properly. It's all about producing diacritics with the keyboard.

**I use Xubuntu 12.10, but I marked this question as "all variants" because I think that it applies to all.**

[SIZE="3"]**1- In the console (tty?)**[/SIZE]

I need to produce c-cedilla by typing ' followed by c. All other diacritics work fine.

I can solve this problem temporarily by using the command below and selecting the **br-latin1** layout ("Brazilian/BR-Latin1" in the list of choices):

```
sudo dpkg-reconfigure console-data
```

So, question 1: how do I persist that change across reboots? With dpkg-reconfigure, neither console-setup nor keyboard-configuration make any difference.

[SIZE="3"]**2- In X**[/SIZE]

[SIZE="3"]2.1- Removing diacritics[/SIZE]

I have the exact opposite problem: too many diacritics. While in the console the only and only thing that does not work is the c-cedilla, here I have too many diacritics.

Since my language is pt-BR, I have absolutely no need for &#341;, &#7765;, &#7743;, &#324;, &#314;, &#7729;, &#501;, &#7811;, &#7813;, &#7831;, &#472; or anything like that.

So, question 2: how do I remove the diacritics I don't need?

I've tried looking at /usr/share/X11/xkb, but no files there seem to map the key combinations. The reason I can't just ignore the unknown diacritics is because of point 2.2:

[SIZE="3"]2.2- Using auto-quotes for unknown dead key combinations (when using ' and ")[/SIZE]

The other problem regarding X is the lack of automatic quotes (single and double): while in the terminal I can type **'** followed by **t** to automatically put **'t**, this won't work in X.

Whenever I try that, X discards this impossible dead key combination (there is no t-acute). But instead of doing the least wasteful choice (producing 't and pretend I typed ', space, t), it just produces nothing at all.

I understand that the behavior is reasonable in Unicode. I'm just asking if I can configure (edit) this.

I am also guessing I can edit a dead key combination (see point 2.1) to fool the keyboard into thinking 't is a dead key combination produced with <dead-acute> <t>. So, anything work if I can edit the keymaps. I also want to edit to remove unused diacritics to make it work with, as an example, &#7743; (I want 'm instead of &#7743;).

Thank you.

---

### Post by DDDa on 2012-11-09
Wow! Nobody knows?

Well, just FYI, I managed to solve 1 (console mapping had all diacritics but not c-cedilla).

/etc/init/console-setup was trying to loadkeys /etc/console-setup/cached.kmap.gz. Therefore:

```
sudo install-keymap /usr/share/keymaps/i386/qwerty/br-latin1.kmap.gz

```

This creates a boottime.kmap.gz file in /etc/console. Now edit /etc/init/console-setup, look at the last line. Where it tries to read cached.kmap.gz, replace with the boottime.kmap.gz file just created (including the path, obviously).

Now the console part works.

**What you should NOT do:** :D

**- Erase /etc/console-setup folder or the cached.kmap.gz file. **

This will give you problems on boot: a message *"Setting up console font and keymap..."* (you will need to press enter to resume booting, it's a mess...). You'll need to install a package (I think it's the console-data package) to recreate the /etc/console-setup folder and its contents.

Run one the following dpkg-reconfigure stuff... console-data, console-common, console-something and keyboard-configuration. I don't even remember which one did the trick to restore the normal boot.

I didn't figure it out before fixing it (the break-fix-break-fix theory), so I recommend you not mess with it.

**- Edit KMAP in /etc/default/keyboard**

It didn't make a hell of a difference. Still not sure if that is related to problem 2.

So that's it. At least the problem 1 now is solved. I will keep listening in case someone pops here with a way to configure the X key mappings (problem 2).

Or maybe I will just learn to always press space when using quotes and double quotes. Xubuntu is just too good and it's worth it. But hopefully not needed.

---

### Post by squakie on 2012-11-10
I have no knowledge of your problem, but do try to remember it's a volunteer forum.  It's normal to wait 24 hours before bumping a thread - since you found the answer to one of your questions it's fine, but remember yours are very unusual questions, and regardless you can't expect someone to come up with an answer in 4 hours.

---

### Post by DDDa on 2012-11-10
> **squakie said:**
> I have no knowledge of your problem, but do try to remember it's a volunteer forum.  It's normal to wait 24 hours before bumping a thread - since you found the answer to one of your questions it's fine, but remember yours are very unusual questions, and regardless you can't expect someone to come up with an answer in 4 hours.

Absolutely. Don't worry, I'm familiar with forums and netiquette in general. I didn't really bump, I just updated the thread with a solution that I've found myself to one of those problems, as you said. [I'd *never* solve something I asked myself and not share the solution]("http://ubuntuforums.org/showthread.php?t=1497505").

About the first sentence, I meant what I said, so please don't take it as a demand (obviously unreasonable in a forum like this). I was indeed just surprised because, contrary to problem #2, I thought changing the key map in the console to enable c-cedilla was a common need. After all, it came disabled by default here, and considering c-cedilla is a fairly used character (pt, fr etc.), I imagined someone could possibly know. Don't read much in that. O:)

Thanks. Btw, if I find how to manage problem/customization #2, I'll definitely post it here.

---

### Post by squakie on 2012-11-11
> **DDDa said:**
> Absolutely. Don't worry, I'm familiar with forums and netiquette in general. I didn't really bump, I just updated the thread with a solution that I've found myself to one of those problems, as you said. [I'd *never* solve something I asked myself and not share the solution]("http://ubuntuforums.org/showthread.php?t=1497505").

About the first sentence, I meant what I said, so please don't take it as a demand (obviously unreasonable in a forum like this). I was indeed just surprised because, contrary to problem #2, I thought changing the key map in the console to enable c-cedilla was a common need. After all, it came disabled by default here, and considering c-cedilla is a fairly used character (pt, fr etc.), I imagined someone could possibly know. Don't read much in that. O:)

Thanks. Btw, if I find how to manage problem/customization #2, I'll definitely post it here.

Sorry I couldn't help you more, and I'm glad you took my comments in spirit instead of getting upset like some do!  Best of luck - I'm watching this thread because it's just another one of those things that is completely new to me and I sure need to learn

Have a good one! ;)

---

### Post by D_E_H0987 on 2012-11-12
> **DDDa said:**
> Hi, I have two problems that may or may not be related, so I'll separate them properly. It's all about producing diacritics with the keyboard.

**I use Xubuntu 12.10, but I marked this question as "all variants" because I think that it applies to all.**

[SIZE=3]**1- In the console (tty?)**[/SIZE]

I need to produce c-cedilla by typing ' followed by c. All other diacritics work fine.

I can solve this problem temporarily by using the command below and selecting the **br-latin1** layout ("Brazilian/BR-Latin1" in the list of choices):

```
sudo dpkg-reconfigure console-data
```So, question 1: how do I persist that change across reboots? With dpkg-reconfigure, neither console-setup nor keyboard-configuration make any difference.

[SIZE=3]**2- In X**[/SIZE]

[SIZE=3]2.1- Removing diacritics[/SIZE]

I have the exact opposite problem: too many diacritics. While in the console the only and only thing that does not work is the c-cedilla, here I have too many diacritics.

Since my language is pt-BR, I have absolutely no need for &#341;, &#7765;, &#7743;, &#324;, &#314;, &#7729;, &#501;, &#7811;, &#7813;, &#7831;, &#472; or anything like that.

So, question 2: how do I remove the diacritics I don't need?

I've tried looking at /usr/share/X11/xkb, but no files there seem to map the key combinations. The reason I can't just ignore the unknown diacritics is because of point 2.2:

[SIZE=3]2.2- Using auto-quotes for unknown dead key combinations (when using ' and ")[/SIZE]

The other problem regarding X is the lack of automatic quotes (single and double): while in the terminal I can type **'** followed by **t** to automatically put **'t**, this won't work in X.

Whenever I try that, X discards this impossible dead key combination (there is no t-acute). But instead of doing the least wasteful choice (producing 't and pretend I typed ', space, t), it just produces nothing at all.

I understand that the behavior is reasonable in Unicode. I'm just asking if I can configure (edit) this.

I am also guessing I can edit a dead key combination (see point 2.1) to fool the keyboard into thinking 't is a dead key combination produced with <dead-acute> <t>. So, anything work if I can edit the keymaps. I also want to edit to remove unused diacritics to make it work with, as an example, &#7743; (I want 'm instead of &#7743;).

Thank you.


Instead of taking parts out of an added character set, how about not adding the set and using an APP (KCharSelect, its on Ubuntu software center. Works fine on Unity.) to put in the extra characters.

Like this  &#7688;&#7689;&#7744;&#7745;

Anyway an idea, I hope it helps.

---

### Post by Impavidus on 2012-11-12
> **D_E_H0987 said:**
> Instead of taking parts out of an added character set, how about not adding the set and using an APP (KCharSelect, its on Ubuntu software center. Works fine on Unity.) to put in the extra characters.

Like this  &#7688;&#7689;&#7744;&#7745;

Anyway an idea, I hope it helps.
Those programs that allow you to select characters are rather cumbersome, especially if you have to enter a lot of them (like when you always type in a language that needs them). This user wants dead keys, which are far more convenient.

Actually, I've used dead keys in the past, put that gave a problem when I used a program that had the apostrophe as a keyboard shortcut. The only way to enter a series of apostrophies was typing alternating ' and space. Then I decided to switch to the compose key, which allows you to enter most accented characters in three keystrokes: compose, the accent and the character: compose+'+e -> é, compose+c+, -> ç, compose+C+C+C+P -> &#9773; (sorry, that one is too funny).

Configuration is unfortunately not very easy in xubuntu. Start from the terminal the tool xev. Type in the window it opens the key you want to use as compose key (assuming it's not present yet on your keyboard, just pick a random key you don't use anyway. I picked the one with the windows logo). In the terminal it will give you some key code (133 in my case). Now make in your home directory a file called ".xmodmap" with the contents```
keycode 133 = Multi_key
```(substituting your key code).

In settings > session > autostart you'll have to add ```
xmodmap ~/.xmodmap
``` and after your next login it will work. The list of possible codes can be found in /usr/share/X11/locale/some_locale/Compose or on the internet. You may actually be able to edit that file.

So far for an alternative for dead keys. I don't know how you can get rid of accented Ms and things like that while still using dead keys for your accents.

---

### Post by Peter Maunder on 2012-11-12
One way of typing ççççççççççÇÇÇÇÇ with an American keyboard is to define it as Canadian  and then choose the layout option France (Canada) Canadian Multilingual. This will remap the } ] keys to ç and Ç. You can ignore the other French accented characters.  

Essentially, this option adds French accents to an American keyboard layout.

The Control Centre > Keyboard applet makes it very easy to change keyboard languages and settings and try them out on the fly.

---

### Post by singedwings on 2012-11-12
I have an idea for a potential direction you could look into to solve problem 2. I do not know if it is practical or you have already thought of it. Could you not use/adjust the font that you use so that it interprets the keys that produce accents as normal letters???

---

### Post by DDDa on 2012-11-12
Thanks everyone for the attention, I really appreciate.

Let me ask something to start: for all you guys that speak french, spanish, italian, german and portuguese, don't you mind typing by accident things like &#7743; instead of 'm, or &#7719; instead of "h ? Really, I'm curious. :)

@singedwing: If I understand you right, I can't see how that is an option. Internally, the character would still be recognized as, e.g., n-acute (0x0144) instead of n (0x006E). Unless by "adjust the font" you mean something that will automatically translate *<dead_acute> <n>* to *'n* instead of *&#324;*.

@Peter Mauder: the console problem regarding the c-cedilla was already solved. Defining whatever keyboard in X (in this case, Canadian Multilingual) wasn't solving it, hence my problem #1. It looks to me like the console sources its mapping from a completely different place. I solved it changing the kmap.gz file to be loaded at /etc/init/console-setup, as said in msg #2. Again, changing the keyboard like you said had no effect *whatsoever*. It changes only inside X.

@Impavidus: thanks for the additional information. I didn't know them. But I still need to deactivate the unused diacritics by customizing key mappings inside X. That&#347; what I want to do.

@D_E_H0987: as I said to others, I need to remove diacritics, not find a more cumbersome way to enter them. I can already easily type Çç&#7743;íÿ. I can even type double diacritics like &#7759;. That's grave-tilde-o --- I didn't even know that existed! :P

Anyway... as I said, the closest I could find were the files under /usr/share/X11/locale/<folder>/Compose files. For example, under en_US.UTF-8, we can find these:

```
# <dead_acute> <M>                 	: "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<Multi_key> <acute> <M>          	: "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
<Multi_key> <apostrophe> <M>     	: "&#7742;"   U1E3E # LATIN CAPITAL LETTER M WITH ACUTE
# <dead_acute> <m>                 	: "&#7743;"   U1E3F # LATIN SMALL LETTER M WITH ACUTE
```

This is the most explicit thing I saw. You can clearly see that these files are responsible for defining how diacritics work. However, you can see that I commented the lines already, but I can still type &#7743; instead of 'm (the correct way for my pt_BR locale, which works fine in the console with the BR-Latin1 console kmap with loadkeys).

Much worse: changing that does not seem to make any difference, as you can see: &#7743;, &#7742;. I'm starting to suspect this needs some compilation (does it?), or something much worse still: Gnome/GTK/Xfce/whatever has its own way to handle it (like, lack of standardization among the graphical interface), but hopefully not. And I have defined the locale accordingly in the GUI, and I know it's working because it instantly changes the /etc/default/locale correctly.

I've tried doing something completely crazy with ~/.XCompose:

```
include "/usr/share/X11/locale/en_US.UTF-8/Compose"
<dead_acute> <C>	: "&#7742;"   U1E3E # 
<dead_acute> <c>	: "&#7743;"   U1E3F # 
```

Does not work. xmodmap does not recognize the commands (I think it expects key codes, not actual high level key combinations). ' with c and C still types ç and Ç. So, clearly not working (again: I already have c-cedilla. This is just a crazy example).

So that's it. As you can tell, I've tried looking at a lot of different files and combinations. Do you guys give up? I'm almost doing so.

Best regards.

---

### Post by singedwings on 2012-11-13
Yes 'will automatically translate <dead_acute> <n> to 'n instead of &#324;' is what I was suggesting. How to go about achieving it is beyond me. Keep trying though and good luck.

---

### Post by audiomick on 2012-11-13
> **DDDa said:**
> Let me ask something to start: for all you guys that speak ... german ..., don't you mind typing by accident things like &#7743; instead of 'm, or &#7719; instead of "h ? Really, I'm curious. :)


I'm an English speaker, but I live in Germany and use German market machines. That is a qwertz keyboard instead of qwerty. I just have to set the keyboard as a German one at the appropriate point during the install, and it works fine. The only unusual characters are ä ü ö ß, and they are all there where they are supposed to be. The é involves typing two keys, as does è. I don't even know how to do a cedilla, although I think it is possible. I know that is rubbing salt in the wound for you, but you did ask... ;)

---

### Post by DDDa on 2013-03-23
Nice, sometimes there is nothing like moving away from the problem, relaxing a bit and trying to solve it later. I finally solved this problem. I won't address the console because it's not that important to me anyway. The real issue was X.

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

Following those instructions, I set GTK_IM_MODULE variable in /etc/environment to "xim", and then suddenly editing the keycodes in my own ~/.XCompose suddenly started working. Now I can edit to include what I want (basically, §, which is also available as <compose><s><o>, but still..., and others), and also remove what I don't use.

Weird is: I definitely tried that page before, but I guess I messed with too many things before that in such a way that it didn't work. This is a new installation. :)

So that's it. Thanks everyone. A years long problem finally **completely** solved (not just solved but extensible and customizable).

---

