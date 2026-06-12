---
title: "Configure 9-button mouse per-application"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by mathman316 on 2011-09-17
Hi,

Ubuntu (11.04) 1-month-old here :)

I'm looking for a way to configure my 9-button mouse (scroll/tilt wheel + 2 side buttons) to send custom keystrokes to each application.  For example, I'd like left/right tilt to map to Alt+Left and Alt+Right in Firefox, the two thumb buttons to map to Backspace and Enter in text editors, and the middle-click (2nd button) to map to <Super><Tab>, which I have set to one of the Compiz window effects.  (I know I can set a mouse button for this, but I'd like this to be the *default* which can be *overridden* in some applications, like Nautilus.)

I've seen **imwheel **advertised as the way to do this, though I haven't gotten my .imwheelrc file up and running yet.  I've also tried **btnx**, which recognized all 9 buttons and let me set keystrokes on the thumb buttons (among others), but what I really want is to *customize the keystrokes by application*.  Both imwheel and btnx at least recognize all my buttons.

Finally, I've seen references to editing the **xorg.conf** file, but this seems to mainly allow button remapping, not customizing per application.

So my questions are...

[LIST=1]
[*]Which of these (if any) will do what I want?
[*]Can you point me to some documentation (other than the [default imwheelrc file]("http://imwheel.sourceforge.net/imwheelrc"))?  I've read the [ManyButtonsMouseHowTo]("https://help.ubuntu.com/community/ManyButtonsMouseHowto"), which says:
> If you have installed the GNOME environment (default for Ubuntu) you *already* have the software needed to get the "6th" and "7th" mouse buttons working (forward/backward on most mice)!I gather that this means GDM will **recognize** the mouse events, which it does.  But how do I **configure** them?
[*]If imwheel is the answer, will it allow me to customize the wheel click (2nd button) also?  I can't discern from what I've read whether this is the case.
[/LIST]
Many thanks!

--mathman316

P.S.  I'm *very* impressed with Ubuntu.  This is my first install, dual-booting with Win XP, and everything with Ubuntu worked out of the box after a few re-boots of the computer.  Nice!

---

### Post by Enterpart on 2011-10-15
your looking for Easystroke

```
sudo apt get install easystroke
```located in Applications -> Universal Access

**Now configure Easystroke.**

In Easystroke go to Preferences Tab -> Method to show gestures ->
-> None
-> Uncheck "Show OSD"

and tick Autostart Easystroke

_**Next add all buttons up to 9**_

In Easystroke go to Preferences Tab -> Additional Buttons ->
-> Add -> click empty box -> Button 1 -> OK 

Repeat process to add the remainder 8 buttons.

[B]Now setup the interface for all the buttons - so you can easily add applications without having to add buttons. it will make more sense later.

[/B]In easystroke click *Add Action* -> (dont worry about the name yet) -> click Record Stroke -> now click button 6 of your mouse or any button -> It will promt up a message say yes.

whichever button you pressed it will show that button number in red with a forward arrow and a blue x over it.

repeat with each button. Now you should have all the buttons but without the keystrokes associated with them.

**Now add the application**

In Easystroke go to Actions Tab -> Add Application

(*Easystroke should get minimised at this point*)

click on the application that your going to set the buttons to work on.

When you have clicked add action a sub menu with all the buttons should be already set up.

**now to record the keystrokes for this application**

choose the button

-> Choose a name (if your using Alt+Left use the name "Back") ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press Alt and Left buttons together

**now repeat the process for the remaining buttons.**

Once your done with that Application.

**Repeat the whole process with adding another application.**

[B]Do not use mouse buttons 1 2 or 3 as the "Record Stroke since they are used already"

If you wanted to use button 4 and 5 (scroll up and down) for an application you can set that up in the application sub menu and not the default.
[/B]

**_*Easystroke is much more powerful than just recording keystrokes. You can use the buttons to enter commands like you would in terminal.*_**

**ANOTHER TIP**

***_add another 8 scroll wheels_***. yes you can do this like as follows 

For example say you wanted to control zoom level of page with scroll wheel do this

click *Add Action* -> 
-> for name choose "Zoom in" ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press CTRL and + buttons together
-> click Record Gesture -> now hold Left mouse button down and flick the scroll wheel up

you should see a red [COLOR=red]4[/COLOR], then 

click *Add Action* -> 
-> for name choose "Zoom out" ->
-> click Command -> and choose Key (Under Type Column) -> 
-> then press CTRL and - buttons together
-> click Record Gesture -> now hold Left mouse button down and flick the scroll wheel down

you should see a red [COLOR=red]5[/COLOR]


now hold down left mouse button and then use the scroll wheel up or down on the browser. It should zoom in and out.

**you can repeat to get another 7 scroll wheel by holding down any mouse  button instead of the Left to control say Brightness, volume toggle application...**


***_LAST TIP_***

you can **create 8 extra buttons** by click and hold to create another action for each of your buttons. by doing this..

In Easystroke click Advanced tab -> and tick "Timeout Gestures"

now go back to Actions Tab to create a another Action.

click *Add Action* -> 
-> for name choose "firefox" ->
-> click Command -> and choose Command (Under Type Column) -> 
-> then type "firefox" without the brackets
-> click Record Gesture -> now hold a mouse button (other than left mouse button AND HOLD IT FOR TWO SECONDS then let go.

click yes.

then when you hold down that button a firefox window should pop up? you dont have to use firefox it can be any command or keystrokes.

**you can Repeat the last tip to include other buttons if you wanted**

[COLOR=Red][B][I][U]You asked to Configure 9-button mouse per-application
I've given you 17 button mouse per application with another 8 scroll wheels.
[/U][/I][/B][/COLOR]
Peace

---

### Post by RedgeOnline on 2011-10-16
Very nice. I've been using btnx and easystroke, but I didn't know easystroke was this advanced.

Thanks for the tip!

---

