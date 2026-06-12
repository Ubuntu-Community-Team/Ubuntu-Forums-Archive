---
title: "Can't change my English keyboard layout after Lubuntu 14.04 install"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by cheapodonuts on 2014-05-07
Since a new Lutuntu install, I can't get back to whatever my English keyboard layout was before. I wanted to type something using the Unicode Hex code, but when I release Shift/Ctrl although the _u_ remains underscored, the hex keys are not activated. So when I type _u_2665, ( it's a little heart symbol ;) ) all I get is _u_"^^% even before I release the other keys. My shift key is obviously working, and ctrl also works for shortcuts. So what's going on? Is there some way to change layouts via the terminal?

---

### Post by Bashing-om on 2014-05-07
cheapodonuts; Hi !


See if these help at all.
Maybe take a look at :
```

cat /etc/default/keyboard

```
and change the default language ?
In my case the default:
> 
XKBLAYOUT="us"
 is for the United States 'us'.

Also one might play about with 'setxkbmap'.
For example:
```

setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ar

```
It's for Arabic, English- US switching using both Alt+Shift .
Another:
```

setxkbmap -option grp:ctrl_shift_toggle "us,il"

```
I used Ctrl_Shift and not Alt_Shift, because the latter was set too, and switched keyboard layouts not to interfere .

Off hand I do not know what the code is for the United Kingdom English ( en ??).
Once you find what works for you one can make it permanent by editing:
Copy the command at the end of your /home/user/.bashrc file. The file is hidden by default.
```

# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
    . /etc/bashrc
fi

# User specific aliases and functions

setxkbmap -layout "jp,ch(fr)" -option "grp:alt_shift_toggle"

```
as an example.
Log-out/in for the change to take effect.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cheapodonuts on 2014-05-07
Well!!! I have it working, but now I don't know if your suggestion has made a difference. :oops: :rolleyes:   I tried the first one, and found that now u underscores with ctrl/shift but I still see the "^^% appearing instead of 2665, but then it all vanishes when I release crl/shift and the typing cursor returns to the start.
  BUT, and it's a big butt ;), I just tried inputting the numerical elements with the number pad and it worked!! &#9829;!! And that's with NumLock turned off!! Another big but is that I have re-acquired the ¬ symbol, whatever it is, which was missing till now. (I've been using it on Youtube comments! ;¬)  )

So, thanx for your input Bashing my friend, even though I may not have been as bright as I could have been before the event. My problem is basically solved. 

Have a bunch of donuts!!

[[IMG]http://i81.photobucket.com/albums/j226/chashugh/500_Donuts_Coffee.jpg[/IMG]](http://s81.photobucket.com/user/chashugh/media/500_Donuts_Coffee.jpg.html)

---

### Post by Bashing-om on 2014-05-07
cheapodonuts; Hey,

Donuts are GooD.

Keyboards can be peculiar people when talking to the operating system. Sometimes again there is no telling what the operating system will relate back to the monitor.
Maybe these will help:
[http://forums.bodhilinux.com/index.php?/topic/286-toggle-between-two-keyboard-layouts/](http://forums.bodhilinux.com/index.php?/topic/286-toggle-between-two-keyboard-layouts/)
[http://crunchbanglinux.org/wiki/xev-determine_custom_keybindings](http://crunchbanglinux.org/wiki/xev-determine_custom_keybindings)

One might play with the tool 'xev'; to see raw xevents as you press keys.
terminal command:
```

xev

```
and maybe get an idea of what is not going on.

And to see the tty default settings:
```

stty -a

```
[INDENT][INDENT]just about the time I think I know
[INDENT][INDENT][INDENT]I get reminded how 
[INDENT][INDENT][INDENT]little I do know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cheapodonuts on 2014-05-08
> **Bashing-om said:**
> cheapodonuts; Hey,

Donuts are GooD.

Keyboards can be peculiar people when talking to the operating system. 

[INDENT][INDENT]just about the time I think I know[INDENT][INDENT][INDENT]I get reminded how[INDENT][INDENT][INDENT]little I do know
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Peculiar people? Have you seen my avatar? That's an actual photo of me!! In a suit and tie!!! With a hat! So if my keboard is finally doing what I need, it can be as peculiar as it likes! :) 
 But I'm ok with being a permanent noob. It means I can concentrate on my next donut.

---

### Post by Bashing-om on 2014-05-08
cheapodonuts; Hey,

No pictures of me, scares too many folks ! -> long haired, bearded Arkansa(w) ridge runner that I am.

Anyway, if the situation is now at a satisfactory condition;
Please mark this thread solved; aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.

And hey hey, learning this operating system continues a main focus in my life.

[INDENT][INDENT]it is
[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cheapodonuts on 2014-05-08
Oh yes, yup yup, solved it in a basic way. Keyboard reset to default.

---

### Post by Bashing-om on 2014-05-08
cheapodonuts; Humm,

Why did I not think of that ? maybe a lack of donuts !

[INDENT]cognitive powers have to come from somewhere
[/INDENT]

---

### Post by cheapodonuts on 2014-05-11
Cognitive Powers? Can I get that on a disk? ;)

---

