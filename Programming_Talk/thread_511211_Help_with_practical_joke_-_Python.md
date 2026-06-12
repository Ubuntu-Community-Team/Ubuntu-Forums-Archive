---
title: "Help with practical joke - Python"
date: 2007-07-27
forum: Programming Talk
---

### Post by SomethingUniqueHere on 2007-07-27
Hey Guys, i was playing around with the python winsound module on my break and i figured out how to make the pc speaker play the riff from funky town.  Now i was thinking it would be hilarious to write a program and put it on a coworkers pc so everytime he hits the backspace button it plays the song (after 3 seconds so he'll probably never figure out whats causing it.)  Anyways, how do i go about coding something that will catch keystrokes?  

Also, i plan on recording this so if it turns out well it'll be on Youtube for all to see.  Link will be posted on this thread

---

### Post by tgm4883 on 2007-07-27
I'm not so sure I want to be helping someone record the keystrokes of a coworker...  Seems a little fishy to me.

---

### Post by Soybean on 2007-07-27
Also, catching keystrokes in an app that doesn't have focus is, by design, a "hard" thing to do. If you're really determined to do it that way, I'm sure it's possible. However, you could get a similar effect much more easily by having the sound play after random time intervals, or maybe even based on something like processor load, if you can find an easy way to read that in your script.

Just a thought. I don't know the details of creating a keylogger, but I know enough to suspect that it's more trouble than it's worth for a practical joke. ;)

---

### Post by Note360 on 2007-07-27
well technically your making a keylogger which is usually a type of virus. SO i am not sure if helping you is the best thing, but you could also make it play on boot up. Its still fishy but it works (run the program on bootup) you could technically put a nice little sleep in their so every 10 minutes it plays even better randomize the intervals.

---

### Post by rekahsoft on 2007-07-27
> **Note360 said:**
> well technically your making a keylogger which is usually a type of virus. SO i am not sure if helping you is the best thing, but you could also make it play on boot up. Its still fishy but it works (run the program on bootup) you could technically put a nice little sleep in their so every 10 minutes it plays even better randomize the intervals.

a keylogger is not a virus :P lol it is a nice utility :D that can help malicous hackers :S..but i agree that it is a little too much work to create that kind of functionality for a joke...you are better off to go with random time intervals ;)

---

### Post by smartbei on 2007-07-28
You will need the app to startup with windows, and lay in wait... No idea how that could be accomplished. You could try making a simple script that reads an already-made keylogger's (like this one: [http://www.kmint21.com/keylogger/](http://www.kmint21.com/keylogger/)) output and then plays the song. That might be a lot easier to do.

---

### Post by Note360 on 2007-07-28
the easiest yet is to do it as what i described though. I already tried it out :) using mpg321 as the music player though, but the basic idea to mine works and the randomized timing might be worse for the person using the computer than every time he hits backspace (because then he/she could jsut swithc to delete or insert(which sucks)).

---

### Post by SomethingUniqueHere on 2007-08-01
Getting keystrokes turned out to be extremely easy, for anyone interested look into PyHook.  I still have some issues, the terminal window pops up and is very suspicious looking and tips people off but it usually goes off one or twice before they figure it out.  Also, i tried using time.sleep(3) for my delay but every other time my function to play the song is called i get an error saying "must be integer"

Anyways, for anyone interested, here is the code:

```

import winsound
import pyHook
import pythoncom

def funkytown(event):                       #Play Funky Town
    if event.Key == 'Back':
        winsound.Beep(38, 3000)
        winsound.Beep(392, 100)            #Frequency (Hz), Duration(ms)
        winsound.Beep(38, 100)
        winsound.Beep(392, 100)
        winsound.Beep(38, 100)
        winsound.Beep(349, 100)
        winsound.Beep(38, 100)
        winsound.Beep(392, 300)
        winsound.Beep(38, 100)
        winsound.Beep(294, 300)
        winsound.Beep(38, 100)
        winsound.Beep(294, 100)
        winsound.Beep(38, 100)
        winsound.Beep(392, 100)
        winsound.Beep(38, 100)
        winsound.Beep(523, 100)
        winsound.Beep(38, 100)
        winsound.Beep(494, 100)  
        winsound.Beep(38, 100)
        winsound.Beep(392, 200)

hm = pyHook.HookManager()
hm.KeyDown = funkytown  
hm.HookKeyboard()
pythoncom.PumpMessages()    


```

pythoncom and pyhook are both on sourceforge - if you use it and make modifications please post your changes, consider this gpl'd

---

### Post by SomethingUniqueHere on 2007-08-01
Forgot to mention,  i used ```
 winsound.Beep(38, 3000)
``` instead of time.sleep cause of the error i was getting.  38hz isn't audible so i achieved the same effect.

---

