---
title: "My computer stops"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ozbolt on 2008-06-06
Greetings from Slovenia

I have a problem and I haven't got a reply on our local forums so there could be the right place to ask you.
It is about games: I often plays Nexuiz and Urban Terror but when I play it for more then 15 minutes or after 15 inutes of play my computer stops. My mouse is unable to move although the game is still running and also keyboard is locked. I have to restart my computer to get to GNOME. Second problem I have is with anability finding good car game becouse raplacement for CoD4 is UrbanTerror and for UT2004 is Nexuiz and others but I can't find any LINUX race game. I have tried installed Trackmania forever on wine but it doesn't go.
 My specs:
- AMD 2600+ (no OC becouse i am getting new comp in a few days)
- ATI X1600PRO
- 1 GB ram
- Ubuntu 8.04 with all updates

Thank you all fr help and plese dont be mad about my writting - I am from Slovene (close to Italy or Austria - both geografically and development) and I am ''only'' 16.

---

### Post by Joeb454 on 2008-06-06
Do you have Compiz running?

System > Preferences > Appearance

Try setting Desktop Effects to "None"

---

### Post by wpshooter on 2008-06-06
Does the computer stop/hang if you are not using this game ?

If it does, then perhaps you have an overheating problem.

---

### Post by ozbolt on 2008-06-06
If it is heeting problem how can I recognize it? Any program (with GUI) can recognize it?
Yes I have compiz on (best thing ever made in LINUX)
Yes it only happens in playing games.

Any suggestions?

---

### Post by 3rdalbum on 2008-06-06
If you have a screensaver set to run, turn it off.

For racing games, try Vdrift or Torcs. If you're a car racing fanatic, those won't be good enough games unfortunately.

---

### Post by Joeb454 on 2008-06-06
> **ozbolt said:**
> 
Yes I have compiz on (best thing ever made in LINUX)
Yes it only happens in playing games.

Any suggestions?

Turn Compiz off, as I suggested above, does it still happen?

---

### Post by 3rdalbum on 2008-06-06
> **ozbolt said:**
> If it is heeting problem how can I recognize it? Any program (with GUI) can recognize it?

You said the game keeps running and that the keyboard and mouse just don't respond. If that's the case, it's not overheating. An overheating issue will freeze the whole computer.

If you do suspect overheating, you can install the "lm-sensors" package, and then use the "sensors" command in the terminal to bring up a list of temperatures and fan speeds that are present in each part of your computer. Once lm-sensors is installed, you can add the Sensors Applet to your Gnome panel anyway to get constant readouts of your temperatures.

---

### Post by ozbolt on 2008-06-06
Thanks all. Damn you are quick.
Do I have to go through all compiz options and turning it off or is there a way to turn them all (marked) on or off?
I am currently installing games TNX.
BTW: I am writting in newbies forum so as you see I am a begginer and I don't know how to install/run sensors. Maybe sudo apt-get install im-sensor?

---

### Post by Joeb454 on 2008-06-06
Just change "Desktop Effects" to none. I think there is a "Compiz-Switcher" which sits in your panel and turns it on and off for you :)

---

### Post by ozbolt on 2008-06-06
Thanks this is what was wrong.
By the way is there any way to get vdrift in a DEB package?

---

### Post by ozbolt on 2008-06-06
Only one more problem:
I turn off compiz with turning it off but when I put it bet in to ''normal'' mode it gets back in default settings and not in those setting I use usually. Is there way to change default settings or somethinge?

---

