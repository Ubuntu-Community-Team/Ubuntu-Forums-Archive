---
title: "HOWTO: Multimedia Keys"
date: 2005-01-22
forum: Outdated Tutorials &amp; Tips
---

### Post by piedamaro on 2005-01-22
*See also: [https://www.ubuntulinux.org/wiki/MultimediaKeys](https://www.ubuntulinux.org/wiki/MultimediaKeys)*

Do you have a keyboard with those neat multimedia buttons, but they don't work with linux? This mini-howto should help you.

***Quick recipe***
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

**A little background note:**
When you hit a key on your keyboard, the linux kernel generates a raw scancode for it (if it's assigned). Each scancode can be mapped to a keycode.
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

p.s.I tried to keep it short but I didn't succeed ;)

[I]CREDITS: 
* [The Linux keyboard and console HOWTO](http://tldp.org/HOWTO/Keyboard-and-Console-HOWTO.html) 
* The Net[/I]

---

### Post by Perfect Storm on 2005-01-22
Gonna try it. I got a super fanzy keyboard with loads of extra buttons. I let you know how it went :)

---

### Post by John McClane on 2005-01-22
Thanks!!! :mrgreen:

---

### Post by piedamaro on 2005-01-22
Hi John, welcome to Ubuntu Forums :)

---

### Post by piedamaro on 2005-01-28
Update:
* Added step 0
* Removed showkeys passage
* Fixed grammar errors and no more use of plural ;)
* Added credits

---

### Post by Hefezopf on 2005-03-04
Thanks for your great HowTo :-) I have a Microsoft Multimedia keyboard an now i can use all keys.

For a list of available keysyms I found the file /usr/lib/X11/XKeysymDB (about line 200). I think this is more complete than /etc/X11/xkb/symbols/inet.

---

### Post by kperkins on 2005-03-04
Thanks--this worked great on my gateway m520s laptop :D

---

### Post by Slalomsk8er on 2005-03-11
My keyboard is not outputing any hotkeycodes in tty1 but I got 4 of 8 keys to work with the gnome tool ?!

I am on a hp/compaq nx9010.
How about [http://sourceforge.net/projects/omke](http://sourceforge.net/projects/omke) as described by [http://www.freax.eu.org/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop#One-touch_buttons](http://www.freax.eu.org/wiki/index.php/Installing_RH9_on_a_Compaq_nx9010_laptop#One-touch_buttons) ?

---

### Post by piedamaro on 2005-03-14
You should see those keycodes with dmesg, if not I've read that some laptops use acpi to  handle multimedia keys. omke seems to be the right choice, but I never used it.

kperkins, Hefezopf, I'm glad it helped! :) (and thanks for the tip Hefezopf)

btw, I've just put the howto on ubuntuwiki.

---

### Post by Slalomsk8er on 2005-03-16
[QUOTE=piedamaro]You should see those keycodes with dmesg, if not I've read that some laptops use acpi to  handle multimedia keys. omke seems to be the right choice, but I never used it.[/QUOTE]
I have installed the nx9xxx.def file from [http://sourceforge.net/projects/omke](http://sourceforge.net/projects/omke) omnibook-2005-02-17.tar.gz to /usr/share/hotkeys (hotkeys deamon with OSD feature) and typed 
```
hotkeys -t nx9xxx
``` in GNOME Terminal. Now 4 of 8 keys work  (config is under /etc/hotkeys.conf) but the other 4 keys still do nothing :(

THis is what dmesg has to offer about keys:
```
atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
``` But I have 4 keys that are not working and this looks just like one.

This are the keys from the nx9xxx.def file:
<Email keycode="236"/> works
<WebBrowser keycode="178"/> works 
<Shell keycode="243"/> nogood
<ScreenSaver keycode="241"/> nogood
<Help keycode="240"/> nogood
<VolUp keycode="176" adj="1"/> works
<VolDown keycode="174" adj="1"/> works
<userdef keycode="160" command="aumix -vM">Sound muted</userdef> nogood

4 keys left to fix :( (lets compile omnibook-2005-02-17)

---

### Post by Magneto on 2005-03-22
great post Piedmaro

hey guess what distro im using it for...........Fedora Core 3 :)

---

### Post by Magneto on 2005-03-23
[QUOTE=Magneto]great post Piedmaro

hey guess what distro im using it for...........Fedora Core 3 :)[/QUOTE]
 for some reason the /etc/xmodmap.conf file is not being read  I only needed it for one key 

also xev did not have any keycode for my audio volume up down or mute keys - i did get a hex code within keyboard shortcuts so they do work but I couldn't build a 100% functional xmodmap.conf for this logitech cordless internet pro keyboard   - I have one media key that I tried to set up as a XF key as your guide stated and told gdm to see the xmodmap in etc but no joy
i had been trying to see how to modify or to verify which application was the default media player or modify entries in the gnome keyboard shortcut app as well but can't find the information
i changed a run_command and keybinding in gconf but it still will not work :| and the keyboard shorcuts app still sees a hex number rather than the XF86AudioMedia button that I added.

any ideas?

---

### Post by TjaBBe on 2005-03-23
Nice howto, although the volume buttons on my Dell Inspiron 8100 lapto give no reaction at all, I'm afraid they are broken, as all the other function buttons work great :(.

---

### Post by piedamaro on 2005-03-25
Thanks ;)

Magneto, make sure your /etc/X11/gdm/PostLogin/Default file is executable, and you have to use /etc/rc.local in place of /etc/init.d/bootmisc.sh (I'm afraid you already know that).
Oh, I'm still on fedora too, but just because I'm waiting for hoary to move all my stuff :)

TjaBBe, I read some laptops use acpi to handle some buttons, sorry I know very little about it since I don't own a laptop. (unfortunately :D)

---

### Post by audax321 on 2005-03-26
I got my volume buttons to work (they were just supported by the gnome keybinding app). But, I think they are adjusting the volume for the main speaker out channel on my sound card. I want the volume to control the headphone channel volume (like I have the volume control applet on the panel set up to do). Anyone know how to do this?

Thanks.

---

### Post by Magneto on 2005-03-26
For anyone having problems check out xbindkeys  its an app that will do all that piedmaro broke down but a little simpler

I couldnt get responses from some keys  that were usable using xev or dmesg  so this was a welcome workaround -


xbindkeys    check it out it is worth it- load it  through your init script like xmodmap 

thanks for putting me on the right track Piedmaro - i now use my Xf86AudioMedia key for xmms - ctl+XF86AudioMedia for gmplayer and shift+ for xine    and use aumix -v for the volume  

I went to back to FC3 for cert training and discovered all those bugs were gone :)  so I ditched gentoo and ubuntu on that box for it - still gentoo on my laptop and I will use Ubuntu Enterprise after april 6 but FC definitely improved - no more Dead Rat arguments :)

---

### Post by Mlehliw on 2005-03-27
[QUOTE=audax321]I got my volume buttons to work (they were just supported by the gnome keybinding app). But, I think they are adjusting the volume for the main speaker out channel on my sound card. I want the volume to control the headphone channel volume (like I have the volume control applet on the panel set up to do). Anyone know how to do this?

Thanks.[/QUOTE]

I was having the same problems as you but I found a solution. Use metacity to set up the buttons and then use the following command to control your volume. 

amixer set headphone "level"

Where "level" is a absolute or relative value. The value ranges from 0-31 and to use a relative value just append a plus or minus sign to the end of the number. For example the commands I use are:

amixer set PCM 2+; amixer set PCM 2-

Then just use that for your global commands. I hope that helps.

---

### Post by audax321 on 2005-04-01
Not sure what went wrong, but I had all my keys set up and working. But after I rebooted they stopped working :(

I tried: xmodmap /etc/xmodmap.conf
but it didn't do anything and all my settings seem to be the same way as before I rebooted, any ideas?

Just checked and after I login it seems like the Default script in /etc/X11/gdm/PostLogin is not being run. But, xmodmap /etc/xmodmap.conf is not working either....

---

### Post by Mlehliw on 2005-04-03
[QUOTE=audax321]...problems...[/QUOTE]
After you run xmodmap does xev recognize your keys?

I had problems with my postlogin default script working. I ended up putting the command in my startup programs list with an order of 10.

This might cause your customized keyboard shortcuts to not work if your using that. It seems like it's horribly broken to me anyways. I just use metacity if I want to assign a shortcut.

---

### Post by wolfman on 2005-04-13
Hi just curious.. i may have to be able to enable the gnome shortcut keys working. However my question is :

Is there a way to get the LED indicator working?
There is a mute button on my laptop HP Pavillion zt3215AP (zt3000 series) with an led on it. In Window$ mode if it is pressed the mute is activated so it the LED on it. 

Is there a way to make it workable under Ubuntu?


Ubuntu rocks!

Regards,
Wolfman

---

### Post by wondering_jew on 2005-04-14
here's my stupid newbie question of the day. He gives an example of his own xmacro script but what I dont understand is where to create the script and how to use xmacro the documentation avaliable has been absolutely no help because it pretty much presuposes that you know things that I do not...

---

### Post by piedamaro on 2005-04-23
[QUOTE=wondering_jew]here's my stupid newbie question of the day. He gives an example of his own xmacro script but what I dont understand is where to create the script and how to use xmacro the documentation avaliable has been absolutely no help because it pretty much presuposes that you know things that I do not...[/QUOTE]
 This isn't a question ;)

xmacro reads from standard input, so a common syntax could be:

echo "<xmacro commands>" | xmacroplay :0

:0 is your $DISPLAY, because xmacro can be used to control remote hosts (screens) if you use <ip address>:0

---

### Post by Ninnghizidha on 2005-06-18
I tried this howto and it works perfect! awsome! Now i can use every singe multimedia-key on my keyboard ... i love it! :-)

-----------

But .. i forgot to map those two windows-keys next to my space-key ;-)  ... and i can't find a way to "rechange" the configuration i made ...

This is what i did till now: i changed to xmodmap.conf again, and added the symbols for the two windowskeys. Afterward i copied the xmodmap to /etc and rebooted... but it doenst seem to work .. i still use the keymap without those windows-keys (but with all other multimediakeys)... so i tried to give the file a new name, and changed the postLogin/Default-File too .. but i still didn't work.

If i enter "xmodmap /etc/xmodmap.conf" manually it works like a charm and i get symbols for the two windowskeys ...

Any suggestions?

Ninnghizidha.

---

### Post by piedamaro on 2005-06-22
Some gentle guy on the wiki pointed out that gnome may overwrite xmodmap at startup  (it uses xkb), son try to move your xmodmap.conf file to ~/.xmodmap and see if it works. :)

---

### Post by mbwardle on 2005-07-23
In the current release of Ubuntu (Hoary), the multimedia keys seem to work provided you have selected your specific keyboard model in System->Preferences->Keyboard->Layouts.

You might also need to ensure that:
[list]
[*]you are using the X11R7 kbd driver in xorg.conf
[*]you do not have any custom Xkb settings in xorg.conf
[*]you do not have any custom setkeycodes settings in your startup scripts
[/list]

There is a similar problem with atkbd.c messages in the system kernel logs (dmesg) regarding scancodes e059 and e001.  These scancodes seem to occur because of ACPI power savings messages that newer wireless keyboards send to the system.  They do not correspond to any key.

I made these errors go away by adding
```
setkeycodes e059 120
setkeycodes e001 121

```to my system startup scripts in a way similar to the way suggested elsewhere in this thread.  I called the script /etc/init.d/powerkeys and made a symlink in /etc/rcS.d/S06powerkeys.

There is also a bug to fix this properly for the next release of Ubuntu (Breezy) at [http://bugzilla.ubuntu.com/show_bug.cgi?id=8739](http://bugzilla.ubuntu.com/show_bug.cgi?id=8739).

---

### Post by Apunkt on 2006-01-20
Hi,

i have a question regarding the use of multimedia keys of external keyboards plugged into a notebookdockingstation. i have got a HP NC6000 Notebook with ubuntu breezy badger 2.6.8-10 . 
i would like to control the volume coming out from the jack of the dockingstation. This is the "pcm-channel" which should be controlled with the multimedia keys of my logitech keyboard. Now the keys work fine with the master-channel which controls the volume of headphone-jack on the notebook itself. 

i looked at XKeysymDB but i didnt find any pcm-volume-up/down. Neither do i know how to tell the gnome-mixer-applet how to switch headphonejack and dockingstationjack for master-channel control. Has anyone an idea ?
Thank you a lot.

Arvid
Greetings from snowy L&#252;beck, Germany.

---

### Post by Apunkt on 2006-01-20
Found a solution: 
[http://www.ubuntuforums.org/archive/index.php/t-79717.html](http://www.ubuntuforums.org/archive/index.php/t-79717.html)

Thanks to the Ubuntu-Forum...
Great.

---

### Post by ymget on 2007-05-09
Thank you very much for this tutorial.

The only thing missing, which I still need help with is the scroll wheel on my Microsoft Office Keyboard.  Although Ubuntu thinks it is compatible with this keyboard, it isn't and I needed to program it manually.

However no one has been able to advise me about the scroll wheel.  Can you help?

Thanks

---

### Post by Am3ndment on 2007-10-19
Hey,

dmesg doesnt return anything when i hit my multimedia keys. I would use omke but i have no idea how to install it. (Damn newbies!) I have Acer Aspire 3694WMLi.

Thanks.

---

### Post by chapapa on 2007-10-21
Hi people. 

First of all, I'm an absolute newbie to linux. So please be gentle..:)

I've just recently installed Gutsy Gibbon and couldn't get my multimedia keyboard to work. It's a Samsung SEM-M2A, which looks exactly like SDM4500P. I've tried changing my keyboard model under Keyboard Preferences to SDM4500P, but the multimedia keys doesn't seem to work. When I use the Keyboard Shortcuts to assign shortcuts using my multimedia keys, pressing any of the multimedia keys will give me a SuperL. I've used keytouch and lineak, also doesn't seem to work.

When I use XEV to check the keycodes, it seems my multimedia keys are already somehow mapped. For example, when I press my "screen saver" key on my keyboard, it's actually sending the Ctrl+b command. Other multimedia buttons seems to be sending Ctrl-[whatever]. When I enter real console (ctrl+alt+F1), pressing my multimedia keys results in system beeps.


Any idea on how to get my multimedia keys working? Thanks in advance. :)

---

