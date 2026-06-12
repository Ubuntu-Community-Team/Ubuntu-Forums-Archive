---
title: "EasyHOWTO Remap the Keypad"
date: 2007-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by BigJules on 2007-11-25
Tested on Dapper and Feisty i386

**Purpose**
If you work as a writer then you’ll be a touch-typewriter and probably are irritated by the need to tear the eyes away from the screen to locate first the control key then the appropriate other key to move about the document. This little tweak converts the useless keypad to the right of the keyboard to a one key coarse navigator.

**How it works**
For those with the time and interest there are probably more elegant methods in deep geekery to achieve the same thing but this is intended as a rapid and workable solution that has no discernible performance hit on a modern system. 
The principle is to have the keypad remapped from its duplication of main keys to generating appropriate common keystrokes: Ctrl-arrow-up to go back one paragraph, Ctrl-end to go to the end of the document etc. 

To achieve this we will need **xmacro** (a simple utility to record and play back mouse and keyboard events for X11) and/or** xbindkeys** (links commands to keys under X), both in the Ubuntu repositories and well worth exploring further.
```
sudo apt-get install xmacro xbindkeys
```
There are two stages: first write a simple bash script that tells **xmacro** to play a sequence to emit the required keystrokes; then second, tell Ubuntu which key you wish to do this. 
After installing **xmacro** you will of course want to create a hidden directory ~/.xmacro to hold your scripts. 

**Stage One**: write a script
This is not the place for a tutorial on **xmacro**, but each script is in exactly the same format so I’ll simply give one. This is for example to make the Keypad “4” key generate a Ctrl-left arrow for moving left one word and will be called for convenience after the key, KP_4.sh

```
#! /bin/bash 
# Move left a word (Ctrl-left arrow):
sleep .07 
echo KeyStrPress Control_L KeyStrPress Left KeyStrRelease Left KeyStrRelease Control_L | xmacroplay "$DISPLAY"
```

I have no idea why the beast needs to sleep first, but take my word for it, the magic spell will not work without it. Start with a value of 1 second and work down until it stalls - I find the 70 milliseconds above works fine on my Dual Core Centrino and is undetectable in practice.
The echo pipes a command sequence to **xmacroplay** which sends the desired keystrokes to the X display. 

**Stage Two**: bind the shortcut key to the script
**Method 1:** A quick way is simply to use the **Gconf** configuration editor in Applications > System tools. In apps > Metacity > keybinding_commands enter the complete path of each script into command_1 to _12 in any order. 

Next go to global_keybindings and associate each command_n with your shortcut key. Note: it is essential to use the correct name value for the keysym. If in doubt```
 xmodmap -pke > list_of_key_names
``` will provide them. Gconf can only map 12 keys, so if you want more, try the next method. 

In this example command_1 is simply ~/.xmacro/KP_4.sh and the global keybinding for run_command_1 is made KP_4 (the keysym)

**Method 2: **This uses **xbindkeys**. After installing, there will be a data file ~/.xbindkeysrc to take the bindings. Add a line for each key. The syntax is easy: *A command, then the key to use to invoke it.* 

Using the same example:
```
# Move left a word (Ctrl-left arrow): 
"bash ~/.xmacro/KP_4.sh"
  KP_4
```
Don’t forget to invoke **xbindkeys** at boot (System > Preferences > Sessions > Startup) 

That’s all folks!

**Hints on key assignments:** I’ve used the following layout as it evolved with usage (I’m an author and have seen my share of acres of text):

[LIST]
[*]Bottom three (Ins, Del, Enter) = copy, cut, paste = Ctrl-c, Ctrl-x, Ctrl-v
[*]Left & right arrows = by word back and forward = Ctrl-left, Ctrl-right
[*]Up & down arrows = by paragraph back and forward = Ctrl-up, Ctrl-down
[*]Home = beginning of document = Ctrl-Home
[*]End = end of document = Ctrl-end
[*]PgUp = select all = Ctrl-a
[*]PgDn = minimise current window (= System > Preferences > Keyboard Shortcuts > Windows management > “minimise window”)
[*]Centre key = save = Ctrl-S
[*]Top four = move to corresponding position workspace 1-4  (= Keyboard Shortcuts again)
[/LIST]

The productivity payoff is deceptive but very real. Every Ctrl-*xxx* in the old way needs the eye to quit the screen to find the Ctrl then locate the other key anywhere on the keyboard and then look back to the screen. Having a single key and they grouped together makes the movement instinctive and there is little need then to take the eyes off the screen and the creative thoughts can roll on unchecked.
[B]
Note[/B]: of course re-mapping is possible on any key, limited only by the imagination. I use the Windows (Super) keys as forward & back in Firefox for instance. And by using a script any single command or whole string of commands can be assigned to a key. 
Mine is a standard 105 key device but as xbindkeys optionally takes straight keycodes then only a little extra work will soon have a mulitmedia keyboard playing tunes. The same thing with multi-button mice; using** xev** and so on will reveal the button code which will invoke a script in the same way as a keycode.

**Extra tip!**
You are not limited to keystrokes – **xmacro** can play back mouse events! Therefore I have mapped the big fat ‘+’ key on the keypad to fake a mouse double-click. This gives you the ability to perform hi-precision d/clicks by removing the need to shift your grip on the rodent. Simply hover the mouse over the exact point you want to execute while covering the keypad ‘+’ key and when totally satisfied hit the key, not the mouse. Perfect for Gimping! \\:D/

---

