---
title: "Need help configuring mouse buttons on Cyborg RAT3"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by huggs on 2011-12-02
I have bought a Cyborg RAT3 mouse, and as soon as I plugged it in, it didn't function correctly. The left-click button would only work after pressing the mode button, then for it to work again, I had to press the mode button again. The scroll wheel button (click the wheel down) only half-worked, and the forward and back buttons on the side of the mouse didn't work.

So I googled it, and it turns out that these type of problems are pretty common with the RAT mice. The solution that I ended up going with was to add:
```
Section "InputClass"
Identifier "Mouse Remap"
MatchProduct "Saitek Cyborg R.A.T.3 Mouse"
MatchDevicePath "/dev/input/event*"
Option "ButtonMapping" "1 2 3 4 5 0 0 0 0 0 0 0 0 0 0 0 0"
EndSection
```to x11.conf

Now the buttons work correctly, except for the forward and back buttons on the side of the mouse and the mode button. None of these three seem to do anything at all.
The last mouse I had, the back and forward buttons just worked without having to be configured in any way, so I have not had any experience in configuring mouse keymapping.

Edit:
Okay so...
i entered 'xorg list' in terminal and got:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Saitek Cyborg R.A.T.3 Mouse                 id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; sonixb                                      id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
```and then I entered 'xinput query-state 9' and it returned:
```
2 classes :
ButtonClass
    button[1]=up
    button[2]=up
    button[3]=up
    button[4]=up
    button[5]=up
    button[6]=up
    button[7]=up
    button[8]=up
    button[9]=up
    button[10]=down
    button[11]=up
    button[12]=up
    button[13]=up
    button[14]=up
    button[15]=up
    button[16]=up
    button[17]=up
    button[18]=up
ValuatorClass Mode=Relative Proximity=In
    valuator[0]=787
    valuator[1]=567
```

It turns out button 8 is the 'back' button, and button 9 is 'forward'.
I added 8 and 9 to the xorg.conf 'buttonmapping' line.
Now my forward and back buttons work perfectly. :razz:

The mode button on this mouse has a color-changing led light that when pressed, cycles through three different colors for its three different modes:
in 'mode red', button 10 is down
in 'mode blue', button 11 is down
in 'mode purple', button 12 is down

maybe I won't be able to use the mode button, huh?
What could I use it for? 
Like to toggle between 3 different 'always pressed' buttons...
Could I somehow make it so that 
when 10 is down, nothing is different, 
when 11 is down, Ctrl and Alt are pressed,
and when 12 is down, Ctrl and Super (Windows) are pressed ?
Is there something even better that I could use this mode button for that I've not imagined?
Anybody know how I'd go making the mode button do some cool tricks besides just changing colors when pressed?

---

### Post by huggs on 2011-12-03
Bump, hoping somebody can tell me how to assign actions to mouse buttons.
I would like to get the mode button to be useful, maybe somebody has ideas for good a good use for being able to cycle through three always-pressed buttons?

---

### Post by huggs on 2012-03-05
buuuuuuuuump :P

---

### Post by stinkeye on 2012-03-05
If your buttons are recognized, try easystroke to assign keystrokes to mouse buttons.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10495426&postcount=11[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11")

---

