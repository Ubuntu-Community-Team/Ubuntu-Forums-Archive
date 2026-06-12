---
title: "Setting Up Pixxo Gaming Mouse"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by Jaybyrrd on 2011-09-26
I have been googling, and trying to understand what to do in order to set my mouse up correctly, and nothing seems to work. I have a Pixxo G235U Gaming Mouse, only two side buttons, and have reverted back to my original xorg.conf file simply because I have no clue what is right or wrong anymore. <-- Confused much, and so I now humbly turn to this community for help. Also imwheel continues to give me this info when ever I use the command: 
```
imwheel -c
```

It Returns:

```

jaybyrd@Jaybyrd:~$ imwheel -c
INFO: imwheel started (pid=7368)
jaybyrd@Jaybyrd:~$ Configuration terminated by signal 11

```

Not sure what that means either as googling the issue provides no help. Please help me. I do know that the Name and Handler for my mouse are as follows:

```

N: Name="KMEPC USB Full Speed Gaming Mouse"
H: Handlers=mouse0 event4 

```

Issues, two side buttons do not work (understandable as I haven't correctly configured it as of yet) and scroll wheel randomly decides to stop the ability to scroll, however when I click on it I am still able to paste and such.

I know this is all really basic, and I am probably an idiot for not being able to figure this out, but I really want to:

One: Fix it.
Two: Learn from the process and help that you give.

Thanks a ton!

JayByrrd

Note: Currently my xorg.conf file looks as follows:

```

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by Jaybyrrd on 2011-09-26
Suggestions? Please, I see this has been viewed... But no one has really said anything. :(

---

### Post by Lisiano on 2011-09-26
People probably don't know how to solve it, that's why it has views, I'll give it a shot though.
Try installing xev```
sudo apt-get install x11-utils
```
Now run it by typing ```
xev
```
Hover your mouse over the white box that appears and notice how loads of information in the terminal starts passing by, not let's see if xev registers when you press your side buttons. For example my 1st side button (Button 8 as xev calls it)
```
ButtonPress event, serial 31, synthetic NO, window 0x5200001,
    root 0x15d, subw 0x0, time 343955265, (156,92), root:(158,947),
    state 0x0, **button 8**, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x5200001,
    root 0x15d, subw 0x0, time 343955401, (156,92), root:(158,947),
    state 0x0, **button 8**, same_screen YES

```
If it registers, you just have to configure applications using the button xev tells you.
If not, well we have a clue.

---

### Post by Jaybyrrd on 2011-09-26
Oh my God! It registers and reacts. Great. So now I should try to figure out how to program my mouse using xev?

---

### Post by Jaybyrrd on 2011-09-26
Wait ok time out, it does not register as a button, this is what I receive when I left click, versus my side button.

Left Click:
```
ButtonRelease event, serial 36, synthetic NO, window 0x5600001,
    root 0x15a, subw 0x0, time 182306625, (142,131), root:(143,184),
    state 0x110, button 1, same_screen YES

```

Side Button:
```
LeaveNotify event, serial 36, synthetic NO, window 0x5600001,
    root 0x15a, subw 0x0, time 182200913, (74,-1), root:(76,52),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus NO, state 16

EnterNotify event, serial 36, synthetic NO, window 0x5600001,
    root 0x15a, subw 0x0, time 182201009, (74,0), root:(76,53),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus NO, state 16

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  90  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  

```

Not sure how to handle it. However this is a working point right?

Also when I use my scroll wheel it returns:

```
KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  90  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


```

However I do know that after restart, it functions normally again, so I am going to restart the computer, and do the test immediately if the scroll wheel is working and post those results.

---

### Post by Jaybyrrd on 2011-09-26
Alright restarted, (and it did not take 10 minutes to restart, I began playing guitar haha).

Wheel is working fine, this is the new output for scroll up and down:

```
ButtonPress event, serial 36, synthetic NO, window 0x3e00001,
    root 0x15a, subw 0x0, time 465500, (133,98), root:(791,151),
    state 0x10, button 4, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0x15a, subw 0x0, time 465500, (133,98), root:(791,151),
    state 0x810, button 4, same_screen YES

ButtonPress event, serial 36, synthetic NO, window 0x3e00001,
    root 0x15a, subw 0x0, time 466156, (133,98), root:(791,151),
    state 0x10, button 5, same_screen YES

ButtonRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0x15a, subw 0x0, time 466156, (133,98), root:(791,151),
    state 0x1010, button 5, same_screen YES

```

And now the side buttons provide the following output.

```
ButtonPress event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x3c00002, time 667431, (29,31), root:(30,84),
    state 0x10, button 8, same_screen YES

EnterNotify event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x0, time 667431, (29,31), root:(30,84),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  90  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x3c00002, time 667569, (29,31), root:(30,84),
    state 0x10, button 8, same_screen YES

LeaveNotify event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x0, time 667569, (29,31), root:(30,84),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

ButtonPress event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x3c00002, time 668463, (29,31), root:(30,84),
    state 0x10, button 9, same_screen YES

EnterNotify event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x0, time 668463, (29,31), root:(30,84),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  90  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x3c00002, time 668691, (29,31), root:(30,84),
    state 0x10, button 9, same_screen YES

LeaveNotify event, serial 36, synthetic NO, window 0x3c00001,
    root 0x15a, subw 0x0, time 668691, (29,31), root:(30,84),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```

So now my next question I guess has become, how do I ensure that whatever caused my scroll wheel to stop working does not occur anymore?

Please give some feedback!

---

### Post by Jaybyrrd on 2011-09-26
Using these, I then created my xorg config entry, and it looks like this:

```
Section "InputDevice"
	Identifier	"KMEPC USB Full Speed Gaming Mouse"
	Driver		"mouse"
	Option		"Device"	"/dev/mouse"
	Option		"Protocol"	"Auto"
	Option		"Buttons"	"1 2 3 4 5 6 7 8"
	Option		"ZAxisMapping"	"5 6"
EndSection
```

Computer now recognizes the buttons, and the currently only move forward or backwards in terms of web pages, or folders. I would like to modify their function, but I bet that I can figure that out on my own. However I would still like help in preventive measures that cause the scroll wheel to not have a button number.

---

### Post by Jaybyrrd on 2011-09-26
Ok I feel like I am constantly posting on my own thread, and I hope this is not against the rules, this is all just a learning experience for myself, and whenever I hit a point where I am stuck, I post to update anyone who might want to help so that they know where I am at, and honestly it helps me get a better understanding. I saw a tutorial on how to use xbindkeys to change the function of mousebuttons, however it seems a bit over my head, and I don't understand fully because instead of describing the meaning of what I am typing it gives steps for certain os's (ubuntu not included) and only the MX100 mouse, so if someone could help and give me a walkthrough based on the info I have above, that would be nice! 

Thanks a ton!

---

### Post by Lisiano on 2011-09-27
Nice detective work!
Don't worry, posting updates is not against the rules unless you do it like every 2 minutes. What would you exactly want to bind the side buttons to? I quite like that it works as back/forward.

Also do you use Compiz?

---

### Post by Jaybyrrd on 2011-09-27
Thank you for the compliment. Yes I use Compiz, I want to bind the keys to basically do what alt-tab does, that way I can copy and paste anything I need to while doing research quickly. Since you mention Compiz I am going to go ahead and look for mouse options within it.

Aha! I am editing to add some findings! So under Compiz --> Commands, you can change Key Bindings, and assign button binds to commands! Therefor, one should be able to make the command alt-tab, and assign button number "x" to command number "x" right, about to try it! Any ideas on how it switches from button numbers to key mapping, or is there anyway other then restarting gdm to fix it?

---

### Post by Jaybyrrd on 2011-09-28
Ubuntu recognizes my Alt key as Mod5 for some reason, could someone give me an example command for the Compiz Commands. I assumed it would be just:

```
<Mod5>Tab
```
But there is no luck there. Thanks!

---

### Post by Jaybyrrd on 2011-09-28
Still no luck, I am going to try to figure out how to fix my keyboard config so it stops registering as Mod5 I suppose, Could anyone help me and throw me a bone?

---

