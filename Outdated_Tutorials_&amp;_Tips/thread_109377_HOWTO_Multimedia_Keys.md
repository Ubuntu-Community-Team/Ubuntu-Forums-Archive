---
title: "HOWTO: Multimedia Keys"
date: 2005-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by piedamaro on 2005-12-28
*See also: [https://www.ubuntulinux.org/wiki/MultimediaKeys](https://www.ubuntulinux.org/wiki/MultimediaKeys)*

Do you have a keyboard with those neat multimedia buttons, but they don't work with linux? This mini-howto should help you.

**Keyboard Shortcuts Editor**
In Ubuntu 5.10 (Breezy Badger) and Ubuntu 5.04 (Hoary Hedgehog) please go to System menu - Preferences - Keyboard Shortcuts to find the keyboard shortcut editor. Many of the common multimedia & control keys should be pre-defined, and if they aren't you should be able to assign functions to them through Keyboard Shortcuts very easily.

If that doesn't work, please read on.

You can also use keyTouch ([WWW] [http://keytouch.sf.net/](http://keytouch.sf.net/). KeyTouch is a program which allows you to easily configure the extra function keys of your keyboard. It is the first and only program of its kind that works perfectly together with kernel 2.6. If your keyboard is not supported yet, you can easily get it supported. You can do this by using keytouch-editor (documentation: [WWW] [http://keytouch.sourceforge.net/keytouch_editor/)](http://keytouch.sourceforge.net/keytouch_editor/)).

Another autosetup program found at [WWW] [http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)

failing that 

**[SIZE="3"]*Quick recipe*[/SIZE]**
**0.** See if your key works with gnome-keybinding-properties, it's under the menu: Desktop/Preferences/Keyboard Shortcuts. If it doesnt' work,

**1.** Go to a real console and press your multimedia keys one by one.

**2.** Look at the console output to discover which scancodes are generated, you should see something like this:
> atkbd.c: Unknown key pressed (translated set 2, code 0x9e on isa0060/serio0).
atkbd.c: Use 'setkeycodes e01e <keycode>' to make it known.
you should find the same information with:
```
dmesg
```
**3.** Use setkeycodes to set your keycodes as suggested. (but first use dumpkeys to see which keycodes are free to use). 

**4.** Put those commands in /etc/init.d/bootmisc.sh

**5.** Open an X terminal:
```
xmodmap -pke > xmodmap.conf
```, then edit this file adding the missing keysyms to the right keycodes (use xev to see the keycodes, read the file /usr/share/X11/XKeysymDB to see which keysyms are available).

**6.** From the same terminal:
```
sudo cp xmodmap.conf /etc
cd /etc/X11/gdm/PostLogin
sudo cp Default.sample Default
```
then open the file /etc/X11/gdm/PostLogin/Default with your editor of choice and add this line to it:
```
xmodmap /etc/xmodmap.conf
```
**7.** Use gnome keybindings or metacity keybindings to bind actions to your fresh configured keys.

Woo, that was fast!

**[SIZE="3"]In-depth Instructions[/SIZE]**
A little background note: when you hit a key on your keyboard, the linux kernel generates a raw scancode for it (if it's assigned). Each scancode can be mapped to a keycode.
This is at _kernel_ level. 
X has a (quasi) total independent way of mapping keys: X reads the kernel keycode table at startup, then map the keycode to its _independent_ keycode table (it's the same as the kernel keycodes but different :)). Then each keycode can be mapped to a keysym, i.e. a string which represent a key or suggest an action.
Thus to have our keys fully functional, they need a kernel scancode/keycode plus a X keycode/keysym. 
It could seem weird, and it is, but X developers have their reason to keep a separate keyboard mapping from the kernel. 
It's not difficult at all, it's only a quite tedious procedure.

**0.Use gnome-keybinding-properties:** 
Try to see if your key works with gnome-keybinding-properties, it's under the menu: Desktop/Preferences/Keyboard Shortcuts. 
If it doesnt' work, or if gnome-keybinding-properties doesn't have a nice default action for your key, you have read the whole howto ;)

**1.Assigning kernel keycodes:** 
We are trying to see which keys have already a kernel scancode/keycode and which don't.
Go to a **real console** by pressing <ctrl><alt>F1.
Now if you press your multimedia keys one by one, you should see an output message like this:
> atkbd.c: Unknown key pressed (translated set 2, code 0x9e on isa0060/serio0).
atkbd.c: Use 'setkeycodes e01e <keycode>' to make it known.
The same informations can be found typing:
```
dmesg
```
This is all you need, but before assigning the missing keycode, you need to check which keycodes are available, to avoid conflicts.
Type:
```
dumpkeys
```
The command returns a list of used scancodes. Just pick the ones without an unassigned keycode (usually from 120 to 255).
Now you know: 
1.which keys have missing keycodes
2.how to map the missing scancode/keycode to make it known
3.which keycodes are available to use

So it's time to actually set up these codes, type:
```
setkeycodes e01e 120
```
where e01e is the scancode suggested in dmesg, and 120 is a free keycode you have to choose.
Repeat this passage for all your keys which don't generate a scancode/keycode.
If you want these commands executed at system startup (you want it), add all those setkeycodes statements at the end of the file /etc/init.d/bootmisc.sh.

Now that you have all your kernel scancodes well generated, move on to:

**2.Assigning X keysyms** 
This time you can stay under X ;) X keysyms are a sort of descriptive string like: XF86AudioMedia, XF86WWW etc. but we can't use random names. A list of X keysyms can be found in the file: /usr/share/X11/XKeysymDB

Fire up a terminal and type:
```
xev
```
press a multimedia key. If you are lucky it has already a keysym binded to it, so the output of xev for that key will be something like this:
> KeyRelease event, serial 28, synthetic NO, window 0x3200001,
    root 0xb7, subw 0x0, time 137010761, (693,138), root:(705,256),
    state 0x10, keycode 136 (keysym 0x1008ff27, XF86Forward), same_screen YES,
    XLookupString gives 0 bytes:
The third row is the one of interest: it says that you have a keycode for that key (136) as well as keysym (XF86Forward).
If you have a keysym then it's all good, you can use that string to represent your key and use gnome keybindings or metacity keybindings to bind the relevant action to it. (See below). 
But probably, you'll find that the key doesn't have any keysym assigned to it, like this:
> KeyRelease event, serial 28, synthetic NO, window 0x3200001,
    root 0xb7, subw 0x0, time 137355697, (401,146), root:(413,264),
    state 0x10, keycode 136 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
In this case you have to assign oyur keysym to the relevant keycode (136) (it doesn't match the kernel keycode for that keys, but it doesn't matter, it's by design). 
This is done with xmodmap.
First, create a file with your current X keyboard map, in a terminal type:
```
xmodmap -pke > xmodmap.conf
```
Then you are going to add all the missing keysyms to this file: use xev to see which keycode to use, look in the file /usr/share/X11/XKeysymDB to find keysym names, open the xmodmap.conf file and fill in the missing keysym using a name which makes sense (i.e. if you have a button with a calculator printed on it, use XF86Calculator as keysym).
Repeat this passage for all your multimedia keys.
When finished, you can apply the changes with:
```
xmodmap xmodmap.conf
```
Now you want to load your new xmodmap.conf when X starts. I've found that the better way is to put the command in the PostLogin script of gdm. (if you use gdm, of course ;))
Type:
```
sudo cp xmodmap.conf /etc/xmodmap.conf
cd /etc/X11/gdm/PostLogin
sudo cp Default.sample Default
```
Now open the Default file with your favourite editor and at the end of it add this line:
```
xmodmap /etc/xmodmap.conf
```
This way you should have all your scancodes/keycodes/keysyms assigned at system and X startup.
Now you can make something useful with them like:

**3.Using gnome keybindings or metacity to bind commands to keys**
First, try to bind keys with gnome-keybinding-property: it's quicker and it has some nice default action, so launch it from the terminal or from the menu.
The utility is self-explanatory, but probabily you'll find that some actions don't work (like sleep for example), or they do the wrong thing, or there is no suitable action at all for your key.
You can address those problems using metacity to bind keys to commands which is a lot more flexible.
Open a terminal and type:```
gconf-editor
```
or launch it from the menu under Applications/System Tools/Configuration Editor.
Go under apps/metacity in gconf-editor. You will see 2 rows (among others):
global_keybindings and keybinding_commands.
If you click on "global_keybindings", on the right pane you'll find some entry for commands, like:
run_command_1, run_command_2, etc.
These have to be filled up with the relevant keysym for your key (like: XF86Play, XF86MyComputer, etc. use xev to see).
Then you can assign the matching command (or script) on the other row, under "keybinding_commands". 
You have a lot of useful command at your disposal like:
totem --fullscreen or rhythmbox --next etc. 
Use the command line help of those applications to discover which parameters are available, e.g. totem --help or rhythmbox --help etc.
For firefox take a look here:[http://www.mozilla.org/unix/remote.html](http://www.mozilla.org/unix/remote.html) 

**4.Additional hints**
The actions you want to execute after a key press are limited only by fantasy: bash provides a very powerful scripting language and with hundreds of useful programs out there, there is virtually no limit.
For example an app you may find useful is xmacro (sudo apt-get install xmacro): it let you play a mouse or a keyboard macro with a command. I've used it to bind my Forward and Back multimedia keys to <Alt>Right and <Alt>Left respectively: this way I can control forward and back in epiphany which doesn't provide a command line option for this task. (it works with every app which takes <Alt>Right and <Alt>Left shortcuts). This is my xmacro script:
```
case "$1" in

forward)
sleep .3
echo -e "KeyStrPress Alt_L \n
        KeyStrPress Right \n
        KeyStrRelease Right \n
        KeyStrRelease Alt_L" | xmacroplay :0 ;;

backward)
sleep .3
echo -e "KeyStrPress Alt_L \n
        KeyStrPress Left \n
        KeyStrRelease Left \n
        KeyStrRelease Alt_L" | xmacroplay :0  ;;
esac

exit 0
```
Another hint is that if you have a sleep key, and it doesn't work with gnome-keybinding-properties, you can use it at least to shut off your monitor:
just assign it to the command:
```
xset dpms force off
```
with metacity.

If you have a scroll wheel on your keyboard, you can even assign a keybinding to the button under the wheel! Assign it to the "Return" keysym, it will act like a return key.

That's all!

p.s. I tried to keep it short but I didn't succeed ;)

[I]CREDITS: 
* [The Linux keyboard and console HOWTO](http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO.html) 
* The Net[/I]

---

### Post by mlalkaka on 2006-06-05
Hello,

Thank you for writing this Mutlimedia Keyboard How-To. It has been the only How-To that has gotten my multimedia keyboard working under Linux.

However, I am still having some problems: certain keys, which are meant to have different functions, are reporting the same kernel scancode. For example, the "Finance" key is returning the same scancode as the right "Windows" key (Super_R). Here's the output of the command "showkey -s", with some comments (on lines beginning with '#'):
```

# Output when "Finance" key is pressed/released:
0xe0 0x5c 0xe0 0xdc
# Output when the right "Windows" key (Super_R) is pressed/released:
0xe0 0x5c 0xe0 0xdc

```
(The key-press scancode is "0xe0 0x5c" and the key-release scancode is "0xe0 0xdc")

I tried this exact same keyboard on the exact same computer under MS Windows. The two keys are detected as different keys under MS Windows, so it can't be a hardware malfunction -- there must be some distinguishable property being sent by the keyboard controller (am I right?).

There is only one difference that I was able to notice. When I press and hold the "Finance" before releasing it, the output of "showkey -s" is the same as above: "0xe0 0x5c 0xe0 0xdc" (the key-press code is not repeated). However, when I press and hold the right "Windows" key (Super_R) before releasing it, the output of "showkey -s" is "0xe0 0x5c 0xe0 0x5c 0xe0 0x5c 0xe0 0x5c ... 0xe0 0xdc" (the key-press scancode is repeated multiple times).

Another thing that may be of importance is that the command "kbd_mode" reports that my keyboard is in ASCII (XLATE) mode, not in UTF-8 (UNICODE) mode. Could this be causing problems? My keyboard is a Multimedia keyboard, but the standard keys have a standard US keyboard layout.

I would appreciate any help that I can get. Thanks.

---

### Post by jetpeach on 2006-06-07
I tried to run kbd_mode to tell you what mode my multimedia keyboard is in, but in KDE's konsole I just got the error "Couldnt get a file descriptor referring to the console".  I tried it in a "real" console (ctrl-alt-f2) and it said I was in ascii, but that might be expected in that terminal.

this multimedia junk is a mess - I want to help develop the Keytouch program because I see it as the solution to much of this madness, but I can't even figure out how to access the source using cvs... hopefully KDE will build in a nice solution in KDE4 :)

---

### Post by mlalkaka on 2006-06-07
[quote=jetpeach]
I tried to run kbd_mode to tell you what mode my multimedia keyboard is in, but in KDE's konsole I just got the error "Couldnt get a file descriptor referring to the console".  I tried it in a "real" console (ctrl-alt-f2) and it said I was in ascii, but that might be expected in that terminal.
[/quote]

Thanks for the help, but I'm beginning to think that the keyboard mode doesn't matter as long as it is ASCII or UNICODE.

[quote=jetpeach]
this multimedia junk is a mess - I want to help develop the Keytouch program because I see it as the solution to much of this madness, but I can't even figure out how to access the source using cvs... hopefully KDE will build in a nice solution in KDE4 :)
[/quote]

Unfortunately, after some more research, I've come to the conclusion that this problem is at the kernel level. Therefore, there is nothing that Keytouch or any other program like it (even one provided by KDE) can do to solve it. The only solution is to fix the problem at the kernel level.

---

### Post by dfreer on 2007-09-02
Thanks! I'm about halfway through, just need to create a bash script to set my xmodmap upon boot (Didn't find a /etc/X11/gdm/PostLogin, so I'm just adding a bash script to my session login).

---

### Post by dark_religion on 2009-11-13
use keyboard shortcuts editor.

---

### Post by marean on 2010-01-05
Hi I'm trying to get this done with the multimedia keys on my laptop which is a no-name (myria) and when I go to a terminal and press one of the hot keys nothing happens. Any suggestions?

---

### Post by PantherX on 2010-01-13
Ok, so here's the million dollar question...

I have the keys.  They work.  Unfortunately I'd like to be able to control the volume and/or mute keys when the machine is locked... either this is going to be impossible or very simple.  Anyone?

---

