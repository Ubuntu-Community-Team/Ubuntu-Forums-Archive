---
title: "Delete key not working"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by spacefreak86 on 2008-04-28
After updating to Hardy 8.04 from Gutsy, my delete key doesn't work - in any application. Does anyone know how to get it working again?

---

### Post by Officer Dibble on 2008-04-28
What type keyboard are you using? The more detail the better. :)

---

### Post by spacefreak86 on 2008-04-28
Acer Extensa 5620 laptop keyboard. I'm used to some reduced functionality with the hotkeys on the side (and besides, I don't even use them), but the delete key is getting annoying. Total there are 88 keys (including the Windows key), plus the 7 hotkeys on the left side.

---

### Post by spacefreak86 on 2008-04-29
Update: I had to boot into windows today and noticed that my delete key does work. So something is wrong with the configurations in Hardy. Only I've tried  sifting through the various keyboard formats in the keyboard configuration tool and nothing showed up. Anyone know what to try next?

---

### Post by lwvmobile on 2008-04-29
Just for fun:

Open a terminal and do a shift+del or ctrl+del combination and see if anything shows up.

for shift+del I get 2~ and for ctrl+del I get 5~

---

### Post by spacefreak86 on 2008-04-29
Nothing comes up at all on mine.

---

### Post by lwvmobile on 2008-04-29
Is your del key also usable as a function key? or part of the number set?

I must admit I really don't have a clue here, other than toggling on or off function and numlock and stuff like that.

---

### Post by unutbu on 2008-04-29
Open a terminal and type

```
xev
```
. You'll get a square window. Move your mouse into the window. Now press the delete key. 
Do you get any output in the terminal?

---

### Post by spacefreak86 on 2008-04-30
Here is the output you requested:

```
KeyRelease event, serial 30, synthetic NO, window 0x3a00001,
    root 0x59, subw 0x3a00002, time 10387038, (35,38), root:(41,67),
    state 0x0, keycode 242 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

---

### Post by T-Virus on 2008-04-30
I'm sure "XLookupString gives 0 bytes:" should give 1 byte, right?

---

### Post by spacefreak86 on 2008-04-30
Actually, the one that interests me is the one that says "keysym 0x0 No Symbol," as when I run down the side of my keyboard, it labels the "Home" key as Home, Pg Up as Prior, Pg Down as Next, Ins as Insert, etc etc. It is as though it has forgotten what to do when that key is pressed.

---

### Post by cartisdm on 2008-04-30
This might be too simple but always worth a shot, did you try System -> Preferences -> Keyboard then make sure you have your correct layout chosen?  It's possible it got switched somehow during the upgrade....

---

### Post by spacefreak86 on 2008-04-30
Gah, brain is too tired to think tonight. How do I go about that in Kubuntu? I tried looking through KControl for the keyboard layout and couldn't find it in there.

---

### Post by cartisdm on 2008-04-30
> **spacefreak86 said:**
> Gah, brain is too tired to think tonight. How do I go about that in Kubuntu? I tried looking through KControl for the keyboard layout and couldn't find it in there.

I don't really use kubuntu but try this:

```
$ systemsettings
```

then Regional & language --->  keyboard layout

Give that a shot

---

### Post by zombiepig on 2008-04-30
'tis this painful bug:
[https://bugs.launchpad.net/ubuntu/+bug/181057](https://bugs.launchpad.net/ubuntu/+bug/181057)

solution:

edit /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi

remove line 141, which reads 
"<append key="input.keymap.data" type="strlist">e053:bluetooth</append> <!-- Bluetooth (toggle) on-to-off -->"

save and restart
(it won't affect bluetooth btw). It's been fixed upstream, but not for hardy :(

---

### Post by spacefreak86 on 2008-04-30
Got it! My delete key works again! Thanks!

---

### Post by Bill magee on 2008-05-04
Zombiepig, I have been reading these posts and the posts over on bugs.launchpad.net. Nothing has worked sofar for my Acer 4720 with 88-89 key Acer "Finetouch" keyboard. Still no Delete key. Gaargh!

Cheers, Bill

---

### Post by Bill magee on 2008-05-04
I should mention that I am running gnome and Hardy.

I removed line 141 as you suggested.

xev returns keycode 107 on my board.

Also xmodmap -e "keycode 107 = Delete" has no effect. Nor keycode = 242

Hmm what to do?

---

### Post by unutbu on 2008-05-05
I don't know if I have a solution for you, but could you post the output of
```

xprop -root | grep XKB
```?

---

### Post by Bill magee on 2008-05-05
Here is the result:

xprop -root | grep XKB

CUT_BUFFER0(STRING) = "xprop -root | grep XKB"
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "acer_laptop", "us", "", ""

---

### Post by unutbu on 2008-05-05
It seems that in essence you've already tried this, but just to check that the xmodmap command stuck, you could try:

```
xmodmap -pke > xmodmap.conf
```
This will save your current keymap to xmodmap.conf.
Then look inside for the line 

```
keycode 107 = Delete
```

If not, add it. Then you can load the modified keymap back with

```
xmodmap xmodmap.conf
```

This info (and more) come from:

[http://wiki.linuxquestions.org/wiki/Configuring_keyboards](http://wiki.linuxquestions.org/wiki/Configuring_keyboards)
[http://www.ibb.net/~anne/keyboard.html](http://www.ibb.net/~anne/keyboard.html)

Hope this helps.

---

### Post by Bill magee on 2008-05-05
Hi Unutbu, thanks for your help. I am in Taiwan, which is why my responses are delayed.

Tried your suggestion. There is already a line keycode 107 = Delete in xmodmap.conf.

Just on a test, I altered the line keycode 106 = Insert to read keycode 106 = Delete. Now I have a functional delete key mapped to the insert key!

This is not optimal, but it is better than no delete key at all.

Wonder what is wrong with 107?

By the way, i mapped insert to 107, but it did not take effect.

Cheers,
Bill

---

### Post by Nikolay- on 2008-05-12
I had fixed this problem in the following way (Acer Extensa 5220):

1. Run xev and press 'Del' key. Look at the keycode. In my case it is 242;
2. Open file /etc/X11/xkb/keycodes/xfree86;
3. Replace line <DELE> = 107 with <DELE> = 242 (242 = keykode of 'Del' key in xev);
4. Replace line <I72> = 242 with <I72> = 107 (Don't even know why, but it doesn't work without this step...);
5. Save & Reboot

Now 'Del' key works.

---

### Post by silverferro on 2008-06-19
Hi,

I'm using Acer Extensa 5620. My delete key was not working after fresh install of ubuntu. I went to Systems->Preferences->Keyboard->Layout Tab and saw "Selected Layouts" which showed "USA". The radio button was not selected by default. I selected the radio button and Delete Key now works:guitar:

Hope this helps others too.

---

### Post by MSBF on 2008-07-02
I'm suffering this issue now. Was fine until last week. Did update the kernel. Running Gutsy. can still ctr-alt-del just not del.Go figure

---

### Post by dontiego on 2010-03-19
Hi!

I got the same symptoms.
xev sends me this when I press a:
```
KeyRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x1a6, subw 0x0, time 7255643, (-113,-107), root:(425,300),
    state 0x2010, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False
```


and this when I press Delete (?!?):

```
FocusOut event, serial 30, synthetic NO, window 0x2c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x2c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

Any clue? My Delete key seems very strange.

---

### Post by The_Eggert on 2011-04-05
> **dontiego said:**
> Hi!

I got the same symptoms.
xev sends me this when I press a:
```
KeyRelease event, serial 30, synthetic NO, window 0x2c00001,
    root 0x1a6, subw 0x0, time 7255643, (-113,-107), root:(425,300),
    state 0x2010, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False
```


and this when I press Delete (?!?):

```
FocusOut event, serial 30, synthetic NO, window 0x2c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x2c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

Any clue? My Delete key seems very strange.

I'm probably gonna get it for reviving  an old thread..
But nonetheless, I have the exact same symptoms  as the poster above me..Does anybody have any help with this..I have tried the other suggestions in this thread..
Or if no actual solution, does anybody know if I can reset my xmodmap.conf..?

---

