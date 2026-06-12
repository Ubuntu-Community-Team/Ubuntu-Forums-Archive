---
title: "HOWTO: Multimedia keys"
date: 2005-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by piedamaro on 2005-04-14
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
```, then edit this file adding the missing keysyms to the right keycodes (use xev to see the keycodes, read the file /usr/lib/X11/XKeysymDB to see which keysyms are available).

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

Woo, that was fast! ;)

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
This time you can stay under X ;) X keysyms are a sort of descriptive string like: XF86AudioMedia, XF86WWW etc. but we can't use random names. A list of X keysyms can be found in the file: /usr/lib/X11/XKeysymDB

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
Then you are going to add all the missing keysyms to this file: use xev to see which keycode to use, look in the file /usr/lib/X11/XKeysymDB to find keysym names, open the xmodmap.conf file and fill in the missing keysym using a name which makes sense (i.e. if you have a button with a calculator printed on it, use XF86Calculator as keysym).
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

### Post by wondering_jew on 2005-04-14
great info, i've been working (slowly) towards getting all the extra keys on my keyboards working, I guess now the only problem I have that hasn't been addressed is getting the scroll wheel on the keyboard to function. I have not been able to find any information on getting it to work, and even in a console i don't see any output when i press the button below the wheel (or scroll the wheel) and one or two others as well.

---

### Post by Sarojin on 2005-04-14
Don't forget to try hotkeys first.

SUPPORTED KEYBOARDS
       1.   Acer Airkey III Wireless keyboard

       2.   Microsoft Internet, Internet Pro, and Natural Pro

       3.   Memorex MX1998, MX2500 and MX3000 keyboard

       4.   SK-2500, SK-2501a, SK-2505, SK-2800c, SK-7100, SK-9925  USB  (par&#8208;
            tial)

       5.   Logitech cordless iTouch, Internet, Cordless Desktop keyboard

       6.   Chicony KBP-8993

       7.   Compaq KB-9963

       8.   Polypix

       9.   BTC 9000

       10.  Process MCK-800

            And more...

---

### Post by dejitarob on 2005-04-21
If hotkeys works, it is much easier. I used [this](http://ubuntuforums.org/showpost.php?p=39004&postcount=10), same keycodes worked on my inspiron 9300.

---

### Post by soupface on 2005-05-15
I found that the command xmodmap /etc/xmodmap.conf would not work if it was in the gdm/PostLogin/Default script (as in the last part of step 6 of the quick recipe above). I got it to work only after adding the command to the Gnome session startup programs (System &#8594; Preferences &#8594; Sessions).

---

### Post by Lionheart on 2005-06-04
I had to hunt for setkeycodes values that worked for the Logitech Cordless Desktop LX 700, because expected values did not work. :-?

For example,  to assign <I14> to e014, I thought I was supposed to check  /etc/X11/xkb/keycodes/xfree86 to find that <I14> = 148, then do "setkeycodes e014 148". But no, through long trials I determined that "setkeycodes e014 222" was what worked.

For what it's worth, here's a patch file of the changes I made to enable all the media keys on the LX 700.

---

### Post by Lionheart on 2005-06-06
A [comment in a Linux Gazette article](http://www.linuxgazette.com/node/9028#comment-932)  showed me how to find a correct X keycode for an e0xx scancode.

To find out what value to use for 'setkeycodes e01e', find out which entry in this conversion table (from drivers/char/keyboard.c) has the value 256 + 0x1e = 286:

> static unsigned short x86_keycodes[256] =
{ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31,
32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47,
48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63,
64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79,
80, 81, 82, 83, 84,118, 86, 87, 88,115,120,119,121,112,123, 92,
284,285,309,298,312, 91,327,328,329,331,333,335,336,337,338,339,
367,288,302,304,350, 89,334,326,267,126,268,269,125,347,348,349,
360,261,262,263,268,376,100,101,321,316,373,286,289,102,351,355,
103,104,105,275,287,279,306,106,274,107,294,364,358,363,362,361,
291,108,381,281,290,272,292,305,280, 99,112,257,258,359,113,114,
264,117,271,374,379,265,266, 93, 94, 95, 85,259,375,260, 90,116,
377,109,111,277,278,282,283,295,296,297,299,300,301,293,303,307,
308,310,313,314,315,317,318,319,320,357,322,323,324,325,276,330,
332,340,365,342,343,344,345,346,356,270,341,368,369,370,371,372 };

In this case, x86_keycodes[139] = 286, so 'setkeycodes e01e 139'. If you get a scan code with no corresponding entry in the table (like e011), then you must substitute an unassigned keycode.

---

### Post by adamb10 on 2005-07-06
[QUOTE=Lionheart]A [comment in a Linux Gazette article](http://www.linuxgazette.com/node/9028#comment-932)  showed me how to find a correct X keycode for an e0xx scancode.

To find out what value to use for 'setkeycodes e01e', find out which entry in this conversion table (from drivers/char/keyboard.c) has the value 256 + 0x1e = 286:



In this case, x86_keycodes[139] = 286, so 'setkeycodes e01e 139'. If you get a scan code with no corresponding entry in the table (like e011), then you must substitute an unassigned keycode.[/QUOTE]
 I have a MS Wireless Comfort Keyboard.  I have 5 favorite buttons that don't work but the rest do.

---

### Post by lassel on 2005-07-19
I also had trouble getting xmodmap.conf to load per the instructions above.
I put xmodmap /etc/xmodmap.conf in my gnome session startup commands as suggested. I hope that will work.

Here is my xmodmap.conf for inspiration:
```

keycode 34 = bracketleft braceleft aring Aring
keycode 48 = quoteright quotedbl Ooblique
keycode 47 = semicolon colon ae AE
keycode 66 = Mode_switch

```

It disabled caps lock and makes it into a modifier key instead.
That allows me to type special characters by holding caps down as an extra "shift" key.

I am a developer and I prefer to use the US keyboard layout since all the wierd brackets that  you need is placed nicely there. Then I use the above xmodmap.conf for typing the danish letters æ/Æ, ø/Ø, å/Å with caps plus ;/:, '/", [/{. It may look wierd but on a physical danish keyboard this is where the letters are placed.

Hope that helps someone.

/Lasse

---

### Post by nickless on 2005-08-29
This is strange, "intell Deluxe excess keyboard" was avaiable as a layout under ubuntu, but now that I have changed to kubuntu it seems to have vanished :(

---

### Post by atilasendil on 2005-08-30
[FONT=Courier New]Thanks for all the info;

I finally got the Calculator button on my Microsoft keyboard :-)

and in case I might help someone : 

first in :
  *xmodmap.conf*
I entered :
  *keycode 161 = XF86Calculator*

as the last line of :
  *sudo gedit /etc/init.d/bootmisc.sh*
I wrote :
  *setkeycodes e016 161*


and in :
  *gconf-editor*
I have :
  apps - metacity - global_keybindings :
    *run_command_1     XF86Calculator*
  apps - metacity - global_keybindings :
    *command1        gcalctool*[/FONT]

---

### Post by rejser on 2005-09-01
Personally I used [http://www.linuxsa.org.au/pipermail/linuxsa/2003-November/062209.html](http://www.linuxsa.org.au/pipermail/linuxsa/2003-November/062209.html)

It's easier, the downside is, if I switch to enlightenment for example, the keys are gone

---

### Post by daller on 2005-12-02
I can't find "/usr/lib/X11/XKeysymDB" in order to see which keysym are available! 

Any ideas?

---

### Post by tehdaemon on 2005-12-07
It looks like Breezy put that file in /usr/share/X11/ not /usr/lib/X11/ 

I just did 'locate XKeysymDB' in a terminal :smile:

---

### Post by daller on 2005-12-07
It works now, thanks!

Is there a way to share this "work" with others having the same keyboards? (So that it gets auto-configured in dapper!)

...Just a basic missing feature!

---

### Post by daller on 2005-12-08
Well, not that fast!

when i rebooted, and ran "xmodmap /etc/xmodmap.conf" I can't get it to work! (no output, nothing!)

---

### Post by limit223 on 2005-12-11
.

---

### Post by limit223 on 2005-12-11
As I noticed many people were complaining by unmanging use of special multimedia keys of their keyboard under Kubuntu(KDE) I decided to adapt Gnome's how-to version to a short and easy KDE how-to version.

1.Assigning X keysyms
This time you can stay under X ;) X keysyms are a sort of descriptive string like: XF86AudioMedia, XF86WWW etc. but we can't use random names. A list of X keysyms can be found in the file: /usr/share/X11/XKeysymDB

Fire up a terminal and type:
```
xev
```

press a multimedia key. If you are lucky it has already a keysym binded to it, so the output of xev for that key will be something like this:

```
KeyRelease event, serial 28, synthetic NO, window 0x3200001,
root 0xb7, subw 0x0, time 137010761, (693,138), root:(705,256),
state 0x10, keycode 136 (keysym 0x1008ff27, XF86Forward), same_screen YES,
XLookupString gives 0 bytes:

```
The third row is the one of interest: it says that you have a keycode for that key (136) as well as keysym (XF86Forward).
If you have a keysym then it's all good, you can use that string to represent your key and use gnome keybindings or metacity keybindings to bind the relevant action to it

In this case you have to assign oyur keysym to the relevant keycode (136) (it doesn't match the kernel keycode for that keys, but it doesn't matter, it's by design).
This is done with xmodmap.
First, create a file with your current X keyboard map, in a terminal type:

```
xmodmap -pke > xmodmap.conf
```

Then you are going to add all the missing keysyms to this file: use xev to see which keycode to use, look in the file /usr/share/X11/XKeysymDB to find keysym names, open the xmodmap.conf file and fill in the missing keysym using a name which makes sense (i.e. if you have a button with a calculator printed on it, use XF86AudioPlay as keysym).
Repeat this passage for all your multimedia keys.
When finished, you can apply the changes with:

```
xmodmap xmodmap.conf
```

Now you want to load your new xmodmap.conf when X starts. I've found that the better way is to put the command in the ~/.kde/Autostart directory in the case of using KDE

```
sudo cp xmodmap.conf /etc/xmodmap.conf
echo 'xmodmap /etc/xmodmap.conf' > ~/.kde/Autostart/shortcutkeyset
```

2.Using KDE khotkeys to bind commands to keys

Open a terminal and type:

```
kcmshell khotkeys
```


Go under Menu Editor entries left panel 
-  New Action - name it on the right side of panel AudioPlay - choose Action type: Keyboard Shortcut -> Command/URL (simple) 
                                                                         -click Keyboard Shortcut tab- press the (multimedia)key desired to open the audio player( notice that once pressed the key you'll have it displayed with its keysym name: in my example XF86AudioPlay)
                                                                         - click Command/URL Settings -type a command as: amarok -p (or any other player command with option of play that you want to be triggered by this key).
Apply

...and you are done with just one key..
Repeat step 2 with New Action for all of your special keys that you assinged in step 1..of course defining different commands as you desire.


Note: All above was tested in Breezy version...I didn't want actually open another thread in right spot of forum just because I thought is better this way in keeping the right of author of this how-to. :)

Hope this post will help you.

---

### Post by teaker1s on 2005-12-11
if you just want the keys recognised by kernel script in init.d and update rc.d are enough

---

### Post by niviche on 2006-01-08
Hello,

This tutorial helped me, but I still have two questions:

First:
> 
Now you want to load your new xmodmap.conf when X starts. I've found that the better way is to put the command in the ~/.kde/Autostart directory in the case of using KDE
Code:
sudo cp xmodmap.conf /etc/xmodmap.conf
echo 'xmodmap /etc/xmodmap.conf' > ~/.kde/Autostart/shortcutkeyset


This doesn't start Xmodmap at startup for me, but just shows me a text file in Kate with "'xmodmap /etc/xmodmap.conf" in it.

Second:
I have a few keys that do not show anything at all, even in a real console. And typing "dmesg" gives me a lot of information, which I do not know how to read. Is there another way to get the codes for the keys that do not have a link yet?

Thank you.

---

### Post by niviche on 2006-01-08
I solved the problem with the keys that do not have a scancode. A good HOWTO about this can be found at [http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=5224&forum=18](http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=5224&forum=18)

However, still no luck to get Xmodmap launched at startup.

Moreover, if I dare ask one more question, what's the command line for "log out"? I would like one of the keys on my keyboard to fire the End Session (the one with the log out / reboot... options) of KDE.

---

### Post by louis_nichols on 2006-01-09
I'm puzzled by one thing. When I installed Ubuntu, the multimedia keys worked perfectly out-of-the-box. Now I did a fresh install of kubuntu and they don't work anymore. What's the explanation? Is it some package that does this? I'd hate to have to use any method to manually configure each and every one of the keys.

---

### Post by piedamaro on 2006-01-09
Probably you need to make the script executable, with:
chmod +x ~/.kde/Autostart/shortcutkeyset

Try dmesg |grep atkbd

For the log out in kde there should be something in kde controol panel.

---

### Post by limit223 on 2006-01-12
[QUOTE=niviche]I solved the problem with the keys that do not have a scancode. A good HOWTO about this can be found at [http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=5224&forum=18](http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=5224&forum=18)

However, still no luck to get Xmodmap launched at startup.

Moreover, if I dare ask one more question, what's the command line for "log out"? I would like one of the keys on my keyboard to fire the End Session (the one with the log out / reboot... options) of KDE.[/QUOTE]

Piedamaro, suggested the right thing: make ~/.kde/Autostart/shortcutkeyset executable and you'll be ok.
To End Session and not only there is a very nice tool in KDE called: kshutdown with lots of features. Then just:

sudo apt-get install kshutdown

and then in the command Url of the key do: 
kshutdown -l                                <--- for ending session

[QUOTE=louis_nichols]
I'm puzzled by one thing. When I installed Ubuntu, the multimedia keys worked perfectly out-of-the-box. Now I did a fresh install of kubuntu and they don't work anymore. What's the explanation? Is it some package that does this? I'd hate to have to use any method to manually configure each and every one of the keys.[/QUOTE]

Did you try to find out your keyboard layout in :
Kcontrol - Regional & Accessibility - Keyboard Layout - Layout tab: check Enable keyboard layouts: **Keyboard model**    ? Is it in the list? Can you select it and don't forget to click Apply button...

---

### Post by jsteve54302 on 2006-01-17
Piedamaro (and those reading this thread), please note - the link to keytouch seems to be broken - the href attribute of the <h> tag seems to have an lparens ")" at the end, causing the link to fail.  Pasting the text of the link without ")" does work.

Hope this helps.

---

### Post by jsteve54302 on 2006-01-17
[QUOTE=niviche]Hello,

> Code:
sudo cp xmodmap.conf /etc/xmodmap.conf
echo 'xmodmap /etc/xmodmap.conf' > ~/.kde/Autostart/shortcutkeyset


This doesn't start Xmodmap at startup for me, but just shows me a text file in Kate with "'xmodmap /etc/xmodmap.conf" in it.

[/QUOTE]

In the echo line, make sure you use backquotes (below the tilde~).  They cause whatever is inside to be executed and the standard output sent to the next pipe, whereas forward quotes (below the dquote") simply send it to the next pipe in the command (I think - it's been a while since I did much work at a *nix command shell, but it worked for me, or would have had I created the xmodmap file first).

---

### Post by piedamaro on 2006-01-21
[QUOTE=jsteve54302]Piedamaro (and those reading this thread), please note - the link to keytouch seems to be broken - the href attribute of the <h> tag seems to have an lparens ")" at the end, causing the link to fail.  Pasting the text of the link without ")" does work.

Hope this helps.[/QUOTE]
Thanks :)

---

### Post by sup on 2006-02-12
Hi, first, thank you for nice howto. It worked for me. Somehow.

Several issues:
1) /etc/X11/gdm/PostLogin/Default thing does not work for me as well as for some others, placing a command in sessions startup overcomes this, but maybe it could be changed in the howto?
2)The configuration does not survive reboot (which is a real pain in the ***:evil: ). Values in gconf>appc>metacity stay as well as values in system>preferences>keyboard shortcuts, but they do not work. I must manually reassign them in order to make them work. (i.e. click on action, press backspace. click on it again and press the desired key in keyboard shortcuts, it is just the same with gconf). I searched the forum and found that I am not alone with this problem, any ideas about it? 
Following line appears in $HOME/.Xsession-errors
```
Window manager warning: "XF86AudioStop
" found in configuration database is not a valid value for keybinding "run_command_7"

```

I can shortcut this with xbindkeys, but it is not as neat as your way, if it only worked properly:-(

---

### Post by piedamaro on 2006-02-16
It seems that 
xmodmap xmodmap.conf
didn't work somehow. Be sure it contains some sane values and get launched at startup before gnome starts. 
That's why I used gdm to load it but as I understand it desn't work for everybody...I should update this howto ;)

---

### Post by LensCap on 2006-09-03
If a real console doesn't pick up my multimedia keypresses, is that the end of the road?  I never really had any use for them before, but after helping someone out with there's I thought I'd at least try.

---

### Post by Burningorc on 2006-09-23
Hi there folks, 

I am a complete Ubuntu noob, I had a set of 5.04 disks that a lecturer at uni gave me. (lit major, hence noob) and yesterday after finally becomeing aggrivated enough with windows and the inability to get rid of a couple of virus short of siping it and starting from scratch I figured I would give Ubuntu a try. In a word; awesome!

My only complaint was my new fancy (read $15aus) logitech keyboard's media buttons didn't work, now they do. Thanks alot to piedamaro for starting the thread (and solving my problem in the first three lines) and everyone else for helping others with their problems, the Ubuntu community rocks!

Thanks alot

---

### Post by stansb on 2007-05-11
If anyone is having the problem where xev doesn't show info on multimedia keypresses (ie. all zeros), one thing to try is disabling legacy USB support in your BIOS and retrying the keytouch approach mentioned at the top of this thread.  There was a posting suggesting this found here: [http://preview.tinyurl.com/3ysf85](http://preview.tinyurl.com/3ysf85)
Apparently the latest kenel possible has issues with USB.  I wish I'd found that posting a week ago.   It worked for me.

---

### Post by Tanay on 2007-11-26
Hello to all...
I recently upgraded from 7.04 to 7.10...
The multimedia keys volume up/down and the mute are not functioning in my keyboard. In 7.04, they worked out-of-the-box. Rest all the keys like Media, www, Play/Pause, etc. are working fine. I tried KeyTouch too, but that didn't help.
How should I rectify the problem?

---

### Post by eladamri on 2007-11-28
I have an issue with Keytouch that I am having a really difficult time with. The problem is that Keytouch does its job too well.

I want Keytouch to work for my mutimedia keys (play-pause, stop, previous, next) which it does, but I want other actions--specifically the volume up and down--to be handled by Gnome as if Keytouch were not installed. The default command for Keytouch is through amixer, but even if I change that I cannot make Keytouch not handle the volume keys.

For my life I cannot seem to make this happen. I also tried Hotkeys, which I have used in the past, but it has the same problem. It will control everything or nothing.

Please let me know if you have a solution to this.

---

