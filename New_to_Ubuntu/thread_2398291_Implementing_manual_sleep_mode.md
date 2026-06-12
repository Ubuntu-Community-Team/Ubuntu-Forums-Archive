---
title: "Implementing manual sleep mode ?"
date: 2018-08-09
forum: New to Ubuntu
---

### Post by Innernet on 2018-08-09
Hi.
The rightmost two icons at top do the same -the arrow down and the on/off symbol- (Why two?)  How to add a 'go to sleep' option somewhere there ?

The settings/tweaks are set for sleep at laptop lid closing; and to sleep at power button press; but the latter is not happening.  Just the screen goes black, but the laptop gets hot anyway, as being fully on.  
Closing the lid on the laptop used on desk is undesired as deteriorates the hinged wiring in few months; as already happened.

---

### Post by bodhin2 on 2018-08-10
[FONT=Trebuchet MS, sans-serif]suspendbutton - command: sudo apt installgnome-shell-extension-suspend-button[/FONT]

---

### Post by Innernet on 2018-08-10
:(

```
externet@externet-Presario-CQ57-Notebook-PC:~$ sudo apt installgnome-shell-extension-suspend-button
[sudo] password for externet: 
E: Invalid operation installgnome-shell-extension-suspend-button
```

---

### Post by bodhin2 on 2018-08-10
sorry busy - my copy paste did not work right

[COLOR=#000000][FONT=&quot]sudo apt install gnome-shell-extension-suspend-button

try that - a space between the install and gnome is needed from my notes.  sorry about that[/FONT][/COLOR]

---

### Post by Innernet on 2018-08-10
Thank you.
Went well on the terminal, but does not show as selection for the on/off icon.

---

### Post by bodhin2 on 2018-08-10
install tweak tool and then go into extensions and turn on suspend

---

### Post by bodhin2 on 2018-08-10
p.s. you can find tweak tool in the software store.

---

### Post by Innernet on 2018-08-10
Thanks.  
Tweak tool was already installed.

Tweaks ---> 'Extensions' does not have the 'suspend' selection;  'Power' has it, and was already on.

---

### Post by bodhin2 on 2018-08-10
try restarting your computer
extensions suspend button.  may check the settings nest to the button - i believe there is something to the left of the button.


it shows up in my extension list - have maybe four listed.

---

### Post by Innernet on 2018-08-10
Thanks, bodhin2.  Good guidance.
 Restarting resulted in the 'suspend' option shown.

---

### Post by bodhin2 on 2018-08-10
great!   not all things loaded need to be restarted i guess; but i remembered that i had to do that with someone else's help.   sorry i forgot at the time.  enjoy!

---

