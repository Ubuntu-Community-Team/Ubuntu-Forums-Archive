---
title: "Game visuals  problem"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-06-15
hi,

  i have ubuntu 8.04 recently and i have installed "flightgear" game thru synaptic manager and installation went on fine. but when i opens flight gear to play a screen appears with  no menus there nothing there. all i can see black screen with with some pink and blue lights as it seems to be a runway in games hoping. also i can see the screeen keeps on flickering (as of a 40w tubelight) and after some time it landed to command terminal with a black background. what i did is rebooted pc using "sudo reboot" and uninstalled flightgear game at first.** moreover i have ATI graphics card only (with driver software working) and not nvidia**. will this make any difference while playing games. other than while gaming, happy with the way my PC is working. kindly help me in this. thanks in advance.

---

### Post by joshsmith on 2008-06-15
disable compiz, then run the game

ie press alt+f2 to bring up the run command (or do it in terminal)
run 
```

metacity --replace

```
to stop compiz
run the game
then run
```

compiz

```
to get compiz back after.

this is needed because if your graphics card isnt very good, running a 3d game and compiz is too much for it

---

### Post by mailtwogopal on 2008-06-15
> **joshsmith said:**
> disable compiz, then run the game

ie press alt+f2 to bring up the run command (or do it in terminal)
run 
```

metacity --replace

```
to stop compiz
run the game
then run
```

compiz

```
to get compiz back after.

this is needed because if your graphics card isnt very good, running a 3d game and compiz is too much for it

Hi,

 i did so and tried to play game. i herewith attach screenshot for ur (all) reference. now i entered "flightgear" game and i could nt see any menus in it. nothing in it. please help me. thanks in advance.

---

### Post by jam007 on 2008-06-16
Tip:
I found the Compiz Fusion in the program repository, Program->Add/remove programs under System tools. I installed it and placed it in autostart for my session. Now I can switch between Metacity and Compiz with a few clicks of the mouse if i want and avoid the flickering of games.

---

### Post by jam007 on 2008-06-16
Flightgear trouble solution from [http://ubuntuforums.org/archive/index.php/t-627314.html]("Ubuntu forums archive"):
> Hi

I don't know if you/anyone else is still having the same problem, but I found a solution to mine:

Start FG in the normal way. Select 'View' drop-down menu (one from the left- you may not be able to read the labels!) Select 'Rendering Options' (fourth choice) Uncheck 'Use Point Sprites for Runway Lights' (fourth check-box)

When you come to quit FG, do so by menu: File...Exit, rather than closing the window to save this setting.

I hope that this works for you, and you can enjoy FlightGear.

Charlie
This solution worked for me.

---

### Post by mailtwogopal on 2008-06-17
hi jamoo7,

 Sure i ll try and come back here.

---

### Post by mailtwogopal on 2008-06-17
> **jam007 said:**
> Flightgear trouble solution from [http://ubuntuforums.org/archive/index.php/t-627314.html]("Ubuntu forums archive"):

This solution worked for me.

hi,

 i was trying to do so. after entering flight gear i chose first left most  menu and clicked "fourth choice" but it doesn't open any option to uncheck as posted earlier. it still remains same. pls help.

---

### Post by jam007 on 2008-06-25
> **mailtwogopal said:**
> hi,

 i was trying to do so. after entering flight gear i chose first left most  menu and clicked "fourth choice" but it doesn't open any option to uncheck as posted earlier. it still remains same. pls help.
Second menu counting from the left, fourth choice

---

