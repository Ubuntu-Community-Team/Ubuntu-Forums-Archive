---
title: "My first python program - A simple Metronome"
date: 2008-06-10
forum: Programming Talk
---

### Post by rlameiro on 2008-06-10
Well here I left the code of a simple metronome that I put together, made with the help of people in this forum (thanks strider1551 for the delay routine :)) who guide me to the choice of python.

well enough said I leave here the code, its very crude and lacks a better user interface, for now I want to make it work :). I have a problem, I only can stop the program with ctrl+c interrupt, if anyone can help and give some direction, it will be nice, (maybe using the letter "q" for quit.

Thanks everyone, it is a happy day :):guitar:

[PHP]#!usr/bin/python
# This is a simple metronome coded in Python, my first experience with python
# Any ideas, corrections and comments pleas email-me 
# ricardolameiro at y a h oo dot com (sorry, anti spam here)
#
#
# needs Python module  tkSnack  developed at KTH in Stockholm, Sweden
# free download: snack229-py.zip
# from: http://www.speech.kth.se/snack/
#
# This code is free, for any type of use, except commercial
# I assume I kind of GPL
# 
# (c) Ricardo Lameiro



import Tkinter
import tkSnack
import time

 
def playNote(freq, duration):
    """play a note of freq (hertz) for duration (seconds)"""
    snd = tkSnack.Sound()
    filt = tkSnack.Filter('generator', freq, 30000, 0.0, 'sine', int(11500*duration))
    snd.stop()
    snd.play(filter=filt, blocking=1)
 
def soundStop():
    """stop the sound the hard way"""
    try:
        root = root.destroy()
        filt = None
    except:
        pass
#insert Beat per minute routine
ubpm = raw_input('Insert BPM please: ')
#this transforms the bpm time, into a usable time delay var
bpm = 60.0 / int(ubpm) 
#this subtracts the time used by the sound beep, so the total delays is
# BPM = beeptime + delay
delay = bpm - 0.1

root = Tkinter.Tk()
tkSnack.initializeSnack(root)

tkSnack.audio.play_gain(80)
#delay routine
while True:
    playNote(880, 0.1)
    soundStop()
    time.sleep(delay)




root.withdraw()[/PHP]


every comment is welcomed
I tried to comment the less explicit things

---

### Post by bobbocanfly on 2008-06-10
Nice work for your first program. Got a couple of comments:

1 - The code/layout is quite messy, there is quite a lot of erratic whitespace/lack of whitespace around. Trust me, you will thank yourself in the future if you keep your code neat and tidy.

2 - The program crashes if you tell it to go over 600bpm. It might be an idea to limit that to prevent crashes

3 - It would be really cool if it took arguments from the command line. Instead of doing ```
ubpm = raw_input('Insert BPM please: ')
``` you could do ```
ubpm = sys.argv[0]
``` which would let you run the program as "./metronome.py 250". You would also need to import the sys module for this to work.

Other than that good job! Cant see any other problems with it.

---

### Post by rlameiro on 2008-06-11
Ok. After the ideas of bobbocanfly, I made some alterations to the code. About the looks of the code, I am a newbie starting now, don't have a teacher, just tutorials, e-books and one book, some help in this department is appreciated.

 I have still one doubt, How can I know if the timing(delay) its going correctly? I have eared of threads, but don't know what it is, any thougs in this is also appreciated.

And please say your opinion, even if it is hard :)

here is the code:


[PHP]#!usr/bin/python
# This is a simple metronome coded in Python, my first experience with python
# Any ideas, corrections and comments pleas email-me 
# ricardolameiro at y a h oo dot com (sorry, anti spam here)
#
#
# needs Python module  tkSnack  developed at KTH in Stockholm, Sweden
# free download: snack229-py.zip
# from: http://www.speech.kth.se/snack/
#
# This code is free, for any type of use, except commercial
# I assume I kind of GPL
# 
# (c) Ricardo Lameiro



import Tkinter
import tkSnack
import time
import sys

 
def playNote(freq, duration):
    """play a note of freq (hertz) for duration (seconds)"""
    snd = tkSnack.Sound()
    filt = tkSnack.Filter('generator', freq, 30000, 0.0, 'sine', int(11500*duration))
    snd.stop()
    snd.play(filter=filt, blocking=1)


 
def soundStop():
    """stop the sound the hard way"""
    try:
        root = root.destroy()
        filt = None
    except:
        pass



#insert Beat per minute routine
#comment if you whant to use raw inmput

ubpm = sys.argv[1]

#uncomment if want to use raw_imput

#ubpm = raw_input('Insert BPM please: ')

#protects for errors, maximum bpm is 300

Ubpm = int(ubpm)
if Ubpm > 300:
    BPM = 300

else :
    BPM = ubpm


	
#this transforms the bpm time, into a usable time delay var

bpm = 60.0 / int(BPM)

#this subtracts the time used by the sound beep, so the total delays is
# BPM = beeptime + delay

print bpm
delay = bpm - 0.1



root = Tkinter.Tk()
tkSnack.initializeSnack(root)

tkSnack.audio.play_gain(80)



#delay routine
while True:
    playNote(880, 0.1)
    soundStop()
    time.sleep(delay)




root.withdraw()[/PHP]
thanks for looking :guitar:

---

### Post by Uchiha_madara on 2008-06-11
Execuse me , But I need how to Compile The Files 

Of Python & C in Ubuntu hardy

---

### Post by rlameiro on 2008-06-11
Uchiha_madara I am sorry, but if you refer to my code, there is no C in it. About the rest, python is interpreted language, just type $python nameofprogram.py and it will run. About c I really dont know that, but I am sure that is plenti of tutorials out there to do that.

---

### Post by Can+~ on 2008-06-11
> **Uchiha_madara said:**
> Execuse me , But I need how to Compile The Files 

Of Python & C in Ubuntu hardy

python is "interpreted" (but it also compiles, automatically). Anyway, to run a python script on ubuntu type on the shell:

```
python myfolder/myscript.py
```

And for C and C++ you need build-essential, see the [tutorial]("http://ubuntuforums.org/showthread.php?t=689635")

---

### Post by Steveway on 2008-06-11
You should use:
#!usr/bin/env python
instead of:
#!usr/bin/python 
It's more compatible.
Also you could instead of uncommenting the raw_input line just add an if-statement that checks if ubpm is null. That way, you can use raw_input if no arguments are given or use the arguments if given.

---

### Post by rlameiro on 2008-06-11
OK, here is the code with the modifications.

I have a little question, the line
```
#!usr/bin/env python
```
is suposed to run the script directly from the shell correct?
```
./metronome.py
```

I do this but is not working even with the prior path, I am in ubuntu 8.04 some help here please.


[PHP]#!usr/bin/env python
# This is a simple metronome coded in Python, my first experience with python
# Any ideas, corrections and comments pleas email-me 
# ricardolameiro at y a h oo dot com (sorry, anti spam here)
#
#
# needs Python module  tkSnack  developed at KTH in Stockholm, Sweden
# free download: snack229-py.zip
# from: http://www.speech.kth.se/snack/
#
# This code is free, for any type of use, except commercial
# I assume a kind of GPL
# 
# copyright (c) Ricardo Lameiro 2008



import Tkinter
import tkSnack
import time
import sys

 
def playNote(freq, duration):
    """play a note of freq (hertz) for duration (seconds)"""
    snd = tkSnack.Sound()
    filt = tkSnack.Filter('generator', freq, 30000, 0.0, 'sine', int(11500*duration))
    snd.stop()
    snd.play(filter=filt, blocking=1)


 
def soundStop():
    """stop the sound the hard way"""
    try:
        root = root.destroy()
        filt = None
    except:
        pass



#insert Beat per minute routine

if len(sys.argv) == 1:
	ubpm = raw_input('Insert BPM please: ')
else:
	ubpm = sys.argv[1]



#protects for errors, maximum bpm is 300

Ubpm = int(ubpm)
if Ubpm > 300:
	BPM = 300
else :
    BPM = ubpm



if BPM == 300:
	print "The maximum BPM is 300, using 300 BPM"
else:
	pass
	


#this transforms the bpm time, into a usable time delay var

bpm = 60.0 / int(BPM)



#this subtracts the time used by the sound beep, so the total delays is
# BPM = beeptime + delay

delay = bpm - 0.1



root = Tkinter.Tk()
tkSnack.initializeSnack(root)

tkSnack.audio.play_gain(80)



#delay routine

while True:
    playNote(880, 0.1)
    soundStop()
    time.sleep(delay)



root.withdraw()[/PHP]

---

### Post by Can+~ on 2008-06-11
[FONT="Courier New"]#!**[COLOR="Red"]/[/COLOR]**usr/bin/env python[/FONT]

And you should still run your application with "python myprogram.py", that way python can remake the .pyc files.

---

### Post by rlameiro on 2008-06-11
ok, I changed it, but is it possible to run the script just typing $./myprogram.py ???

I tried it and didn't worked

---

### Post by Can+~ on 2008-06-11
> **rlameiro said:**
> ok, I changed it, but is it possible to run the script just typing $./myprogram.py ???

I tried it and didn't worked

My guess is that it isn't executable:

```
chmod u+x myprogram.py
```

If this doesn't work, post the output of 

```
ls -l
```

---

### Post by rlameiro on 2008-06-11
Ok, I warned that I was a newbie... lol. Never passed my mind to chmod it... 
it is working perfect

thanks Can+~

---

### Post by pmasiar on 2008-06-11
Re: your license: GPL code is free to use as commercial. The only restriction is, if user  distributes changed code based on yours, has to share the code. Can sell the code (even yours) with no restrictions.

Python code is usually released under Python license, or even BSDv2

---

### Post by rlameiro on 2008-06-12
pmasiar, I just want the code to be open always, maybe commercial is not the most correct word, but don't want it to be LGPL, want it to be always open to everyone, even if they can sell it, (doubt on that :) lol) for now, I am just coding for fun, and trying to give back to the community :).

pmasiar thank you very much for your help on licenses.

---

### Post by rlameiro on 2008-06-12
Well, I was testing the metronome and I found that it is not working correctly on ubuntu. I tested it on Virtualbox - windowsXP and there it worked just fine. In ubuntu the program is slower than it should be, i tested it against a fisical metronome and it is slower. anyone can help me in this? I really don't know how to solve this....

---

### Post by rlameiro on 2008-06-13
*bump*

:)

---

### Post by bhilmers on 2012-07-06
> **rlameiro said:**
> In ubuntu the program is slower than it should be, i tested it against a fisical metronome and it is slower. anyone can help me in this? I really don't know how to solve this....Here is one solution, many years later, haha. I used this thread as a starting point from my own metronome program and ran into the same timing issues. The metronome would not stay in time.

After much research and experimentation, I decided to use something other than time.sleep(). Rather, I used time.time() to check the system timer and follow it. Below is an example of what I did. There is some slight jitter in the timing and a little re-syncing is needed for every pass. It works very well.

```
import time

bpm = 120
metronome_time = (60.0 / bpm)

# Get the system time.
target_time = time.time()

# Add the time between clicks to it.
projected_time = target_time + metronome_time

while True:
    if target_time > projected_time:
        print "Click"

        # Find out how much jitter you have for re-syncing.
        sync_time = target_time - projected_time

        # Compensate for the jitter.
        projected_time = target_time + metronome_time - sync_time

    else:
        target_time = time.time()
```

---

### Post by bhilmers on 2012-07-25
I discovered my timing solution above drives the CPU way up and eats up some memory too. So I put the metronome to sleep for a short period with every loop iteration and this brought the CPU usage down to hardly anything.

At the end of the if statement:
```
sleep(metronome_time - sync_time)
```

---

### Post by wildmanne39 on 2012-07-26
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

