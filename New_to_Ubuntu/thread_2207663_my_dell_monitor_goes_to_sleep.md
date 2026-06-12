---
title: "my dell monitor goes to sleep"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by darinb6-w on 2014-02-24
I am on 12.04 a dell 24" flat screen monitor. 
I unplugged the screen by kicking the plug. 
Now it goes to sleep even though power management is set to never. 
I was given this script to keep it from going to sleep:
xset -dpms;xset s off
when I put that in terminal or run it as a .sh as follows:
#!/bin/bash
xset -dpms;xset s off
It works...I can watch movies with out my monitor going to sleep.
I have the .sh in my home folder and checked allow executing file as program. 
then added it to my startup applications. 
but is does not work. 
How can i get this .sh to run at boot or at login?

---

### Post by papibe on 2014-02-24
Hi darinb6-w.

Are you sure it is suspending? May be it's just the monitor turning off.

There's another setting that turn off the monitor (no suspend). It is in 'Brightness and Lock'.

Hope it helps. Let us know if that helped.
Regards.

---

### Post by darinb6-w on 2014-02-24
brightness and lock? 

is that on the dell monitor. menu on the monitor or in the operating system power management part or screensaver part?

---

### Post by hebrewofyhwh on 2014-02-24
Ok, I am a new user of Ubunto 12.04 Precise Pangolin but I may be able to clarify where brightness and lock is. I found it in system settings, and then the "personal" section at the top of the screen. The button is at the top right corner of the main desk top screen.

---

### Post by kostkon on 2014-02-24
> **darinb6-w said:**
> brightness and lock? 

is that on the dell monitor. menu on the monitor or in the operating system power management part or screensaver part?
Monitors have their own power management settings. Press the menu button of your monitor to bring up the OSD and then go from there.

You could also unplug your vga cable from both ends and plug it back making sure that it is attached firmly to the ports (_turn off_ both your monitor and computer before attempting that, especially if it is a desktop pc).

Hope that helps.

---

### Post by darinb6-w on 2014-02-25
ok it is not turning off the monitor since moving the mouse turns it back on. 
I did the unplug and reseat the hdmi plug this morning. 
I have not been away from the pc yet or watched a movie to see if it goes to sleep. i do not see anything in the monitor menu itself that stops it from going to sleep. i did once see writing in the middle of the screen that said it is going to sleep. I don't remember what it said exactly because it was brief and i was not expecting it. it only happens while watching a movie where the mouse is not used for a long period. or i walk away from the pc for some time. this is very anoying this never happened before I kicked out the power plug. I am hoping moving to 14.04lts will solve it. if we can't fix it first. Also the command in a .sh file i put in above works...I just can't get it to load on boot up or log in.

---

### Post by papibe on 2014-02-25
Open 'System Settings', then click on 'Brightness and Lock', and select 'Never' for the field 'Turn screen off when inactive'.

Let us know if that helped.
Regards.

---

### Post by darinb6-w on 2014-02-27
none of the above suggestions worked. The .sh file I listed above works but only if I run it. any way to get this .sh to run at log in? i have it in my home folder and made it allow executing file as program...  and then added it to my startup app list, but it doesn't seem to work.

---

