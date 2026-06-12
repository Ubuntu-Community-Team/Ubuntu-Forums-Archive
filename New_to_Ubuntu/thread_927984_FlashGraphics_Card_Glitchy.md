---
title: "Flash/Graphics Card Glitchy"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by RussW210 on 2008-09-23
For some odd reason I can't play SuperTuxKart.  When it starts, the sound is choppy and the screen glitches.  As soon as I put my mouse over the window the screen goes completely black and the music completely stops.  A few seconds later after getting the mouse off the screen comes back on.

Anyone have an idea what this could be?  I also experience problems with a glitchy YouTube full-screen video (any video).  But I don't get problems with other website videos.

Is this a problem with my Graphics Card (I have an Accelerated ATI Driver installed), Flash (Version 9 installed), etc?

---

### Post by RussW210 on 2008-09-23
By the way, I am running Ubuntu Hardy and have Compiz Fusion installed with custom appearance settings.

---

### Post by CLomax on 2008-09-23
You need to turn off compiz graphics temporarily when playing games. Look for Compiz Fusion Icon in Add/Remove.

---

### Post by RussW210 on 2008-09-23
Is that absolutely necessary?  Also when you say "Look for Compiz Fusion Icon in Add/Remove" are you suggesting I remove Compiz Fusion?

I would rather keep Compiz and deal with not playing certain games.

---

### Post by Kain000 on 2008-09-23
Hes's right about disabling Compiz while gaming, it will give you the glitchy screens and mess with the sound nearly every time. 
You dont have to uninstall it, just turn it off while you game and back on afterward.  He's talking about an icon to use like a switch, but I dont know about any compiz icon, that may be easier, I just go into System>Pref>Appearance and under the effects tab I check no effects and that will take care of it.  Afterward when your done just re-check the custom box or whatever it was.   
Do you have a Nvidia card or ATI?  
hope this helps
-sean

---

### Post by LowSky on 2008-09-23
in add/remove or synaptic there is a program called compiz-fusion icon

when activated it will place an icon in your system tray so you can turn off and on Compiz

---

### Post by CLomax on 2008-09-23
Just a quick way of switching from Compiz to Metacity. If it doesn't help then it could suggest that there is another cause.

---

### Post by RussW210 on 2008-09-23
Thank you guys...

BTW I have a brand new Dell Inspiron 530 with ATI 2400 HD Graphics Card... I doubt it is a hardware failure.

From what I have heard, the driver has a hard time playing 3d games and doing compiz at the same time... I will have to look into turning Compiz on and off (hopefully it doesnt lose my settings).

I saw someone suggest you could create a script for certain applications so when I open a game it automatically turns off Compiz then when I close it automatically turns it on.  Does anyone know anything about that?

Is the compiz icon you are talking about installable by doing:

sudo apt-get install fusion-icon

Or is that something else?

---

### Post by CLomax on 2008-09-23
The command sounds about right, there should be a relevant launcher in *Applications -> System Tools*.

I haven't the foggiest as to how to write a script but thank you for mentioning that, I'll have a look at it.

---

### Post by Kain000 on 2008-09-23
> **RussW210 said:**
> \


I saw someone suggest you could create a script for certain applications so when I open a game it automatically turns off Compiz then when I close it automatically turns it on.  Does anyone know anything about that?




Ok so if you have compiz running then your ati drivers are working *working if you can call it that*  ATI hasnt been the most forthcoming with linux drivers.   ANyhoo so compiz works and thats ok, you may have glitches reguardless of compiz just because it's a ATI driver, but you should be reasonably able to play games.   so a turn compiz off start game script would look somthing like

```
#script for shutting down compiz and starting _____(game 'o' choice)
#!/bin/bash

kill (process Id of conky)
#insert the games command (most likely found in /usr/bin)
gamecommand

stop

```
Unfourtinally i am in class and will have to update this later.  I'll do some research because having to look up the process id of conky each time sorta takes more time than actually quiting it mannualy.

If anyone knows how to identify a process by name rather than ID (as id will change each time the program runs)

---

### Post by Kain000 on 2008-09-26
alright sorry i havnt gotten back to you on this, I've been sick.  so with the help of others in the forum we've come up with 
```
#!/bin/sh
metacity --replace wait &
uberpwnagegame wait
compiz --replace &
```


All in all It's problely eaiser to just either use the button or go into apearance and turn it off.

sorry dude.

---

### Post by CLomax on 2008-09-27
> **Kain000 said:**
> alright sorry i havnt gotten back to you on this, I've been sick.  so with the help of others in the forum we've come up with 
```
#!/bin/sh
metacity --replace wait &
uberpwnagegame wait
compiz --replace &
```


All in all It's problely eaiser to just either use the button or go into apearance and turn it off.

sorry dude.

Awesome, I'll give this a go. It'll surely be easier than using the icon to turn it off.

---

### Post by Kain000 on 2008-09-28
> **CLomax said:**
> Awesome, I'll give this a go. It'll surely be easier than using the icon to turn it off.

Hey, he wanted a script so I tried to give him a script.

---

