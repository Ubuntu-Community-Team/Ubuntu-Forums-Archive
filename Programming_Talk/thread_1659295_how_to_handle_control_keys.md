---
title: "how to handle control keys"
date: 2011-01-03
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-03
I always took it for granted that when I press Ctrl-C the keyboard generates a control code. (In this case to kill the current process) However programming with Gtk I get a GdkEventKey event and the translated keycode it gives me does not reflect the control key being pressed. I mean it's just a plain old "c" character decimal 99, hex 63.. being inserted in my text buffer which isn't really what I wanted when pressing Ctrl-C.

My first impulse was to test the event "state" flags for either control key being pressed and then convert the code myself, but then I wonder be that the right thing to do?

SO just a quick question: Does anyone know what behavior is expected from foreign keyboards with non Latin alphabets? How do people in those locales for instance generate a control-C? :confused:

---

### Post by worksofcraft on 2011-01-04
I mean like should 
Ctrl+Arabic_hamzaonwaw supposed to generate a control C interrupt?

Well I change to Hebrew keyboard and press the key in same position:
Ctrl + hebrew_bet...
hum isn't that the "B" in their alphabet?

Ok I'll try control D instead...

key_press_event=3298=hebrew_gimel
...
key_press_event=1514=Arabic_yeh
translated keyval=5EA, E->keyval=5EA


with Ctrl are those supposed to give the user an end of file?
It doesn't look like anyone knows :(

Meh perhaps I'll set a new standard... Chrissy's international keyboard drivers now with added go faster stripes :P

---

### Post by worksofcraft on 2011-01-04
Anyway... so I been reading about keyboards.
Aparently there are 8 different modifier keys supported by X11... so that would allow up to 256 different codes per key!

Then there is a truly imaginative algorithm by none less than the Unicode consortium to swap symbols round based on a "current directionality"

Also I spotted this [slightly larger than usual keyboard]("http://en.wikipedia.org/wiki/File:Large_chinese_keyboard.jpg") design...

So I decided it's high time to actually try to rationalize what happens with keyboard input. Anyone who is genuinely interested can check back here for my usual lucid insights.. and welcome to contribute with theirs ;P

---

### Post by worksofcraft on 2011-01-05
"... holding down the Control key while pressing another key zeros the ms 2 bits of the 7 bits in the generated ASCII character"

Indeed there are 32 possible control codes and so we need more than just the letters on the keyboard to generate them. IMO every keyboard (Yes, even foreign ones :shock: ) need to have the capability to produce them all. OTOH there is no need to be able to combine control with any other modifier... Ctrl-Alt-Del while pecking your middle mouse button with your left nostril is not a concept I'm going to entertain: I simply propose that the control codes be associated with fixed keyboard positions regardless of what symbol is engraved on each key and that it overrides and excludes any other modifier.

Kewl that was easy :)

Now on to the shift and Caps lock keys..
Non-Latin alphabets don't have upper and lower case, but they they do have other things like:
"Arabic letter can be represented in four positional forms: initial, median, final or isolated"

Amazingly in Arabic they don't need any modifiers to do all this as apparently it is all done by contextual analysis that also implements the ligatures that are wanted. Similarly Chinese don't have upper or lower case, so there is nothing to suggest we need to support shift keys for anything other than Latin keyboards.

Phew that was easy too :)

Then there is Alt keys. Alt keys are used to choose between alternate sets of characters... like on my keyboard you can make all sorts of foreign squiggles by pressing the alt key and this can be combined with a shift key to get yet more foreign squiggels!

So what does "Alt" actually mean :confused:

Well basically human brains can operate in multi-lingual mode, switching between Alien and English :KS Thus alt serves to provide alternative character sets on the same keyboard.

Now one innovation that doesn't seem to have occurred to the implementors of keyboard drivers would be an Alt-Lock key so that even foreign people don't have to keep one finger on that alt key the whole time while typing in their native language.

Luckily now that I'm on the job that can be remedied :popcorn:

---

### Post by nvteighen on 2011-01-05
IIRC, and if I understand what you're talking about, GTK+ disables the signals for control keys so that a keystroke system can be implemented for applications without having the user doing all the POSIX signals API magic.

But this isn't GTK+-specific. Signal supressing or overriding is used extensively in ncurses to avoid someone hitting Ctrl-C and ruin the terminal (by not gracefully resetting it via endwin()).

Look at man 3 signal if you want to handle signals manually.

---

### Post by worksofcraft on 2011-01-05
> **nvteighen said:**
> IIRC, and if I understand what you're talking about, GTK+ disables the signals for control keys so that a keystroke system can be implemented for applications without having the user doing all the POSIX signals API magic.

But this isn't GTK+-specific. Signal supressing or overriding is used extensively in ncurses to avoid someone hitting Ctrl-C and ruin the terminal (by not gracefully resetting it via endwin()).

Look at man 3 signal if you want to handle signals manually.

I don't so much *want* to process the control keys... you see I'm back onto my bidirectional terminal emulator project (having finished that other malarkey now) and so... say I get a key event that identifies itself as Ctrl+Arabic_hamzaonwaw... 

That happens to be where on a Qwerty keyboard the "C" would be so I'm wondering should I generate an interrupt signal to the slave process, or insert an ASCII 03 into it's input stream... or something completely different? Shrugs - IDK :confused:

---

### Post by trent.josephsen on 2011-01-05
> **worksofcraft said:**
> I always took it for granted that when I press Ctrl-C the keyboard generates a control code.
True.  But the running process never sees Ctrl-C (or Ctrl-D, Ctrl-Z or any other special combinations).  Instead, that combination triggers code in the terminal that sends a signal to the child process.  Ctrl-C generates SIGTERM.  Ctrl-Z generates SIGSTOP, I think.  Ctrl-D doesn't generate a signal, but terminates the program's input stream.  These key combinations aren't detected or interpreted by the program.  (To insert a control sequence into an input stream, you can use Ctrl-V; observe that inserting a ^D into a stream doesn't terminate it.)

Some frameworks, like ncurses, can request that the said keystrokes be passed in to be interpreted as ordinary input, which is why (for example) in Vim, Ctrl-C escapes Input mode instead of terminating the program.  But if you do that you have to interpret special keystrokes yourself.  That's what you're seeing here: Gtk overrides the terminal's mechanism and passes the keys pressed straight into your program, where you haven't tried to capture or do anything with them.

To send a signal to a running process, use kill(1); I'm not familiar with the proper techniques for capturing keypresses in Gtk, so perhaps someone else can illuminate that issue.

---

### Post by Arndt on 2011-01-05
> **trent.josephsen said:**
> True.  But the running process never sees Ctrl-C (or Ctrl-D, Ctrl-Z or any other special combinations).  Instead, that combination triggers code in the terminal that sends a signal to the child process.  Ctrl-C generates SIGTERM.  Ctrl-Z generates SIGSTOP, I think.  Ctrl-D doesn't generate a signal, but terminates the program's input stream.  These key combinations aren't detected or interpreted by the program.  (To insert a control sequence into an input stream, you can use Ctrl-V; observe that inserting a ^D into a stream doesn't terminate it.)

Some frameworks, like ncurses, can request that the said keystrokes be passed in to be interpreted as ordinary input, which is why (for example) in Vim, Ctrl-C escapes Input mode instead of terminating the program.  But if you do that you have to interpret special keystrokes yourself.  That's what you're seeing here: Gtk overrides the terminal's mechanism and passes the keys pressed straight into your program, where you haven't tried to capture or do anything with them.

To send a signal to a running process, use kill(1); I'm not familiar with the proper techniques for capturing keypresses in Gtk, so perhaps someone else can illuminate that issue.

And if you want to see (or change) what key strokes generate what signals in the terminal, use the program 'stty'.

---

### Post by Arndt on 2011-01-05
> **worksofcraft said:**
> 

Non-Latin alphabets don't have upper and lower case, but they they do have other things like:
"Arabic letter can be represented in four positional forms: initial, median, final or isolated"

Amazingly in Arabic they don't need any modifiers to do all this as apparently it is all done by contextual analysis that also implements the ligatures that are wanted. Similarly Chinese don't have upper or lower case, so there is nothing to suggest we need to support shift keys for anything other than Latin keyboards.


If you include Greek, Cyrillic, Georgian and Armenian in Latin, yes.

> 

Then there is Alt keys. Alt keys are used to choose between alternate sets of characters... like on my keyboard you can make all sorts of foreign squiggles by pressing the alt key and this can be combined with a shift key to get yet more foreign squiggels!

So what does "Alt" actually mean :confused:

Well basically human brains can operate in multi-lingual mode, switching between Alien and English :KS Thus alt serves to provide alternative character sets on the same keyboard.


Personally, I most often use Alt not for alternate sets of characters, but to obtain for example accented letters, like é.

> 
Now one innovation that doesn't seem to have occurred to the implementors of keyboard drivers would be an Alt-Lock key so that even foreign people don't have to keep one finger on that alt key the whole time while typing in their native language.



Perhaps, but I think the usual mode of operation is that they switch to their own language with some key combination, and then type without holding down Alt.

Besides, you may find the 'xev' program useful.

---

### Post by worksofcraft on 2011-01-05
> **trent.josephsen said:**
> ... that combination triggers code in the terminal that sends a signal to the child process..


Yes, trying to implement a terminal emulator it is exactly that logic I'm trying to fathom atm. Some control keys generate a signal or perform some other special action while others just insert a control code in the data stream.

Thinking about alternative keyboard layouts like Dvorak I now realize that it IS associated with the key engraving after all :shock: so it looks like I need a look up table that is dependent on the keyboard currently installed as this is not being handled by the X11 input modules.

> **trent.josephsen said:**
> 
Some frameworks, like ncurses, can request that the said keystrokes be passed in to be interpreted as ordinary input


My terminal emulator will have to provide this feature to ncurses so I'll have to find out how ncurses is requesting that.

> **Arndt said:**
> If you include Greek, Cyrillic, Georgian and Armenian in Latin, yes.


Of course.
Latin letters actually derive from the Greek ones as do those others so, would have been more correct talking about "Greek" alphabets I suppose but I'm not too bothered what we call them:

When it comes to implementing a terminal the issue is what to do with these modifiers. In principle, for shift we have two separate character sets: One selected when shift is inactive and the other when it is active. e.g. with shift active, instead of "a" I get "A" and instead of "1" I get "!". However here too is an issue: Caps Lock inverts the shift key for letter keys like "a/A" but NOT for other keys like "1/!"

Luckily it doesn't look like my terminal emulator needs to consider this Shift/CapsLock logic and also it doesn't look like I have to take account of Alt keys or special multi-media and other function keys. Even the swapping of keys depending on prevailing directionality doesn't look like it is going to be my problem as all that malarkey is being handled by Gtk/X11 keyboard input modules :)

So it's really just those control codes.

---

### Post by Reiger on 2011-01-05
> Thinking about alternative keyboard layouts like Dvorak I now realize that it IS associated with the key engraving after all  so it looks like I need a look up table that is dependent on the keyboard currently installed as this is not being handled by the X11 input modules.

Keyboards don't generate “character X pressed” events. They merely generate keycodes. The difference between keyboard layouts is hidden between the circuitry of the actual keyboard and the keyboard driver.

---

### Post by worksofcraft on 2011-01-05
> **Reiger said:**
> Keyboards don't generate “character X pressed” events. They merely generate keycodes. The difference between keyboard layouts is hidden between the circuitry of the actual keyboard and the keyboard driver.

I know that, but I not interface to keyboard hardware.
I'm writing a terminal emulator that runs under Gtk and needs to cooperate in a well behaved way with other desktop applications.

OTOH if I start messing about with the hardware directly then it might be intrusive to operation of system software like X11 :(

---

### Post by worksofcraft on 2011-01-09
Moving on from the Control Key issue...

Many languages need to use Gtk Input methods to compose characters from multiple key strokes, but that doesn't work at all for my program that is responding to key events... so presumable having an on_key_press_event signal handler can't be quite the right way to handle keyboard input in Gtk :(

Question is... what then? I've Googled high and low and the best I can come up with is an enigmatic [GtkIMContext]("http://library.gnome.org/devel/gtk/unstable/GtkIMContext.html") class...

I suppose I could try reverse engineering GtkEntry widget code or something like that, but just wondering if anyone knows of a half decent document on how to actually program using these input methods?

---

### Post by worksofcraft on 2011-01-10
> **worksofcraft said:**
> Moving on from the Control Key issue...

Many languages need to use Gtk Input methods to compose characters from multiple key strokes, but that doesn't work at all for my program that is responding to key events... so presumable having an on_key_press_event signal handler can't be quite the right way to handle keyboard input in Gtk :(

Question is... what then? I've Googled high and low and the best I can come up with is an enigmatic [GtkIMContext]("http://library.gnome.org/devel/gtk/unstable/GtkIMContext.html") class...

I suppose I could try reverse engineering GtkEntry widget code or something like that, but just wondering if anyone knows of a half decent document on how to actually program using these input methods?

update:

Hum... how **do** you mark a thread as "unsolvable" :confused:

Whatever... I've now had really serious attempt at getting to grips with supporting multi lingual input methods and the convoluted logic forced upon both text input and display by Unicode bidi-algorthm and it's pathological integration into Gtk I decided this particular project is not worth the effort. :P

p.s. Anyone know how to delete a project from Launchpad ?

---

### Post by nvteighen on 2011-01-10
> **worksofcraft said:**
> 
p.s. Anyone know how to delete a project from Launchpad ?

Ask it to be deleted here: 
[https://answers.launchpad.net/launchpad](https://answers.launchpad.net/launchpad)

---

