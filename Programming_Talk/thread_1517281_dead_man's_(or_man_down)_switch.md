---
title: "dead man's (or man down) switch"
date: 2010-06-24
forum: Programming Talk
---

### Post by e-t on 2010-06-24
Hi all,

I regularly work after hours in an environment that has certain hazards and would like to make a software dead man's switch that can be run from terminal.

Basically I would like to do at login:
- Input name and contact number (details to be emailed when triggered)
- Time intervals for check in and response time (i.e. count down time)

And it also must be able to:
- Generate a random string that the person must type to show s/he's alive and responsive
- Allow for check in at anytime (i.e. well before count down begins), so that the person working in the area don't have to sit in front of the computer when time is nearly up.
- Make a regular sound when time it's time to check in to remind the person it's time to show their alive and well 
- Make a persistent alarm sound when response is not received within the count down time, so if there's anyone in the immediate vicinity, they can raise the alarm
- Email all relevant people name and contact number of the man down

If this info helps, I have fairly basic background in bash scripts... somewhere in between beginner and intermediate level scripting skills.

Can anyone help me with this?

Thanks in advance
ET

---

### Post by juancarlospaco on 2010-06-24
*I recommend Python since it seems complex for Bash only.*

it suppose to be mail based only?, or an Client/Server-like app ?

---

### Post by fiddler616 on 2010-06-24
> **juancarlospaco said:**
> [I]I recommend Python

Me too.

You've asked a rather vague question, and you can't expect us to suddenly spit out a program for you. So...
[LIST]
[*]Do you want links to good but concise Python tutorials?
[*]Do you want help with input? Sound? Time? String generation? Email? Threading/concurrency? A UI?
[*]Are you overwhelmed at the concept of *designing* this thing from scratch?
[/LIST]

---

### Post by e-t on 2010-06-24
It's mail based only for now.

As for scripting language... it doesn't bother me, but if it needs to be compiled OR it's not written in C or FORTRAN OR is not a Java binary I'm going to need (more detailed) instructions on how to use it...

---

### Post by e-t on 2010-06-24
> **fiddler616 said:**
> Me too.

You've asked a rather vague question, and you can't expect us to suddenly spit out a program for you. So...
[LIST]
[*]Do you want links to good but concise Python tutorials?
[*]Do you want help with input? Sound? Time? String generation? Email? Threading/concurrency? A UI?
[*]Are you overwhelmed at the concept of *designing* this thing from scratch?
[/LIST]

The last option... I have no idea where to start. Ideally I was hoping someone has started something that I could edit to my purposes...

Also, a GUI is not necessary... just something that prints on terminal type "some random string" at regularly intervals.

---

### Post by fiddler616 on 2010-06-24
> **e-t said:**
> It's mail based only for now.

As for scripting language... it doesn't bother me, but if it needs to be compiled OR it's not written in C or FORTRAN OR is not a Java binary I'm going to need (more detailed) instructions on how to use it...

If it's Python, you'll need the Python program. It's installed by default on most *nix distros (I forget if this includes MacOS), and is available from the Python web site for Windows. If you are on Windows, there's a program called PY2EXE which is exactly what it sounds like.

If installing Python is a major problem (maybe you don't have administrator access?), you can use Jython to compile Python into Java bytecode, and then use the Java Virtual Machine you said you had. But really, just installing Python is a lot easier.

---

### Post by fiddler616 on 2010-06-24
> **e-t said:**
> The last option... I have no idea where to start. Ideally I was hoping someone has started something that I could edit to my purposes...


Well, [your guess is as good as mine]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=dead+man's+switch+python"). You might be able to adapt [this]("http://www.deadmansswitch.net/") to your purposes (maybe have a buzzer sound when an email comes in from that website?). Otherwise, walk yourself through the steps systematically. Like so:

"Hmm, first I need the name, contact number, and time interval. Inputting those at a terminal should be fine, but if we abstract the input-getting a bit we can do fancy things like parse data from a text file later. Thus: 

[PHP]
import time
def get_input(prompt):
  return raw_input(prompt)
name = get_input("Name: ")
contact_number = get_input("Contact Number: ")
delay = get_input("Time Interval (minutes): ") * 60 #convert to seconds[/PHP]

Now we need to repeat the same thing over and over, pausing between each loop.

[PHP]
while True:
  time.sleep(delay)
[/PHP]

Now I need to generate a random string. I don't know how to do that. I'll just wrap it up in a function and come back to it later. Worst case scenario--I ask the people on UF PT.

[PHP]password = generate_string()[/PHP]

etcetera. Did that get you off on the right foot?


> Also, a GUI is not necessary... just something that prints on terminal type "some random string" at regularly intervals.
Ah, I didn't say "GUI", I said "UI". As far as I know--and this could be very wrong since I'll freely admit I don't grok threading and concurrency--using the default input prompt-- raw_input() or input() -- will mess up your timing since the code that triggers the dead man's switch cannot execute while your program is waiting for input. Again, someone may ninja in here and come up with some threading voodoo to fix that, but AFAIK that's not possible. Therefore, you'll need a slightly more robust way of getting input, which could come from any number of libraries--curses and ncurses help with creating a terminal-based UI, and then there's GUIs like Gtk+, wxPython, Qt, EasyGUI, etc. Note: curses/ncurses is a royal pain to use.

I have to go now, but I'll be back tomorrow morning if you have any more questions. I also expect that some other people will chime in between now and then and give you better help than I can :) .

---

### Post by e-t on 2010-06-24
Thanks fiddler!

I'll give it a shot in Python over the weekend(and a crash course in it while I'm at it...) and see what I can get.

Alternatively, if someone knows how to play a sound file and email from Fortran, I'm fairly sure I can do the rest... Something like Call System(play sound file)? Google didn't produce anything (I found) useful when I did a search a while ago...

---

### Post by fiddler616 on 2010-06-24
I'm in a rush, but here:

Learn Python's syntax and general features quickly: [http://www.korokithakis.net/tutorials/python](http://www.korokithakis.net/tutorials/python)

A bit more in depth about how stuff works, but doesn't talk about the standard lib: [http://www.ibiblio.org/swaroopch/byteofpython/read/](http://www.ibiblio.org/swaroopch/byteofpython/read/)

Standard lib: [http://docs.python.org/library/index.html](http://docs.python.org/library/index.html)


Read the first one, use the second to put back together any pieces of your brain that got exploded, use the third for time, sound, etc. Actually, for sound and email it might be more efficient to Google around and find some code to copy and paste. Actually for email there's a good example at the bottom of the IMAP, POP3 and SMTP pages in the Python API.

---

### Post by juancarlospaco on 2010-06-25
> **fiddler616 said:**
> 
Ah, I didn't say "GUI", I said "UI". As far as I know--and this could be very wrong since I'll freely admit I don't grok threading and concurrency--using the default input prompt-- raw_input() or input() -- will mess up your timing since the code that triggers the dead man's switch cannot execute while your program is waiting for input. Again, someone may ninja in here and come up with some threading voodoo to fix that, but AFAIK that's not possible. Therefore, you'll need a slightly more robust way of getting input, which could come from any number of libraries--curses and ncurses help with creating a terminal-based UI, and then there's GUIs like Gtk+, wxPython, Qt, EasyGUI, etc. Note: curses/ncurses is a royal pain to use.


**I recommend Tkinter**,
the Built-In Python GUI, since is not complex as QT4.x and such.

This is a working example of the app:

[IMG]http://img130.imageshack.us/img130/7239/tempeo.jpg[/IMG]

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Licence = GPL v3
try:
    import psyco  # Speed Up if avaliable
    psyco.full()
except ImportError:
    print(" No PYTHON-PSYCO avaliable, this application will run slower... ")
    pass
import os
# Python 2 / 3 Compatibility
try:
    from Tkinter import *  # Python2
except ImportError:
    from tkinter import *  # Python3
root = tk.Tk(className='Dead Mans Switch')
root.wm_attributes("-alpha", 1)
root.focus()
try:
    root.wm_iconbitmap('@'+'/path/to/iconfile/icon.xbm') # Put here app icon .XBM format
except TclError:
    print(" ERROR: Icon File not found... ")
    pass
[COLOR="Blue"]#
# Modifications starting from here...
#[/COLOR]
mylabel = Label(root, text=' Press a button to continue ')
mylabel.pack()
#
def CommX():
    os.system('sh /path/to/bash/script1.sh') # Put here the bash script
button1 = Button(root, text='execute command X', command = CommX )
button1.pack()
#
def CommY():
    os.system('sh /path/to/another/bash/script2.sh') # Put here the bash script
button1 = Button(root, text='execute command Y', command = CommY )
button1.pack()
#
def CommZ():
    os.system('sh /path/to/just/another/bash/script3.sh') # Put here the bash script
button1 = Button(root, text='execute command Z', command = CommZ )
button1.pack()
[COLOR="Blue"]#
# Repeat the 4 lines of above ^, as many commands/buttons you need.
#[/COLOR]
root.mainloop()

```

paste into a text editor, save with .py extension,
check that you hace [Tk installed]("apt:/python-tk"), run it from Terminal:
**python file.py**

---

### Post by wmcbrine on 2010-06-25
```
def generate_string():
    return '4 8 15 16 23 42'
```

---

### Post by nrs on 2010-06-25
offtopic: what do you do? sounds interesting. 
ontopic: why not a simple "are you alive? y/n"
that + email is a trivial task in python or even bash.

---

### Post by KdotJ on 2010-06-25
> **nrs said:**
> offtopic: what do you do? sounds interesting.

lol I'm curious too...
My boss never checks if I'm dead or not :(

---

### Post by e-t on 2010-06-25
> **nrs said:**
> offtopic: what do you do? sounds interesting. 
ontopic: why not a simple "are you alive? y/n"
that + email is a trivial task in python or even bash.

I work in a lab that has high voltage, gas, cryogenics and chemical hazards and the walls of the lab are purposely made so that mobiles/wifi don't work. Our current after hours system is to call someone regularly when working alone, to make sure we're OK and we don't sound sluggish/tired. Being human, people forget their meant to call regularly, the guy working at the lab goes to the toilet and can't answer the lab phone and suddenly emergency services are breaking in to see if everything is OK...

As for the a simple "are you alive? y/n", I was hoping that this program could ask a person to perform a simple task within a time limit to see if they're tired or not... it won't stop the person from working but at least they're aware it may be time to go home...

It's not going to replace the phone system completely (yet), the phone will still ring the first time to ensure someone is checking their emails and the last time letting them know they can move away from their computers, but at least the program will perform the routine task of checking regularly and testing if the person should be still there or not...

---

### Post by Reiger on 2010-06-25
You could select two, random two digit numbers and ask people to multiply them. This is a small-ish problem with simple correct answer (and answer which people can figure out even if, for instance, they suffer from impaired vision or hearing).

So something like this:
```

"Please solve for x in the following equation: x = 23 * 68; x = "

```

The additional benefit is that these type of questions test the basic cognitive skills which are indicative of whether someone's brain is in a state of “normal working-order”. 

The downside is that some people simply don't seem to have the cognitive skills to solve simple math like that, you might want to check that first.

---

### Post by crush304 on 2010-06-25
if someone's life is at stake, it would be worth paying someone who knows what they are doing to make the program for you

---

### Post by soltanis on 2010-06-26
Coooooooool

By the way, there has got to be some kind of professional thing that can do this for you. I wouldn't rely on your computers to save someone's life. When you've got something like this at stake, you should really have some kind of separate, dedicated system for doing things like check in and contacting emergency services. Things like big red buttons on walls.

---

### Post by e-t on 2010-06-26
> **soltanis said:**
> Coooooooool

By the way, there has got to be some kind of professional thing that can do this for you. I wouldn't rely on your computers to save someone's life. When you've got something like this at stake, you should really have some kind of separate, dedicated system for doing things like check in and contacting emergency services. Things like big red buttons on walls.

There are professional equipments for this task. There are devices which are essentially walkie-talkies which have an accelerometer so they know if your standing up or lying down. An alarm is triggered if you've been lying down too long.

The situation here, however, is a little complicated... The mentioned system above can implemented but there are practical reasons (which I shouldn't go into the details off...) not to implement them anytime soon.

The phone/email system is just a temporary system for now.

---

### Post by lavinog on 2010-06-26
Would a motion sensor work?
If no movement is detected for X mins, the system should make an audible warning, and all the user needs to do is wave at the sensor.  This way the user doesn't get distracted from their work to answer a computer question, and the required movement may help keep their blood pumping.
If they don't respond to the warning, then trigger the alarm.

---

### Post by juancarlospaco on 2010-06-26
> **lavinog said:**
> Would a motion sensor work?
If no movement is detected for X mins, the system should make an audible warning,

There are really BIG walls on the place OP said, audible warning not an Option i think.

---

### Post by new_tolinux on 2010-06-26
I think lavinog meant an audible warning to the person who is there. Some kind of warning like "there was no motion in the last x minutes, please move if you're still alive".
That should have nothing to do with the thickness of the wall, since the sound should be in the same room as the user is.

---

### Post by memilanuk on 2010-06-28
Personally... if its that important, I think it needs to be hard-wired i.e. electro-mechanical triggered system where timer sets off a (really obnoxious) alarm internal to the space, and personnel have 'x' amount of time to respond and silence/reset the alarm before it triggers a dialer to emergency services.  Just like 'e-stops' on many systems cannot be software, but must be physical devices for safety/reliability reasons, I think that would be the way to go if you really want this to be serious.  Yes, physical parts wear out and/or fail - but in my experience, far less frequently than computers systems barf, lock-up, or just otherwise do weird $hit other than what they were intended to do.  Granted, you pay dearly for high-quality parts designed for use in such systems...

---

