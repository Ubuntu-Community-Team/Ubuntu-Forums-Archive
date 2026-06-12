---
title: "Development with Quickly"
date: 2011-07-16
forum: Programming Talk
---

### Post by Mr_Electric on 2011-07-16
Hi Everyone, 

I need help with creating an application in Ubuntu 11.04 Natty Narwhal. I am new to Ubuntu development and I'm trying to develop a GUI application that sends commands through terminal when a button is pressed. I did some research and found out that it can be accomplished through quickly but I need help on how it should be done. Can someone please direct me to a tutorial on how I can develop this app.



Thanks in advance, 
Mr_E

---

### Post by ubudog on 2011-07-16
Hmm... for beginners I would recommend C++ (QT).  To install QT, run the following commands in a terminal:
```
sudo apt-get install qtcreator libqt4-core
```

It has an easy to use drag and drop interface for creating the UI, and a very easy to learn syntax.

Please let me know if you have any questions.  :)

---

### Post by Mr_Electric on 2011-07-17
Thank You! I'll be sure to check it out and contact you if I have any other questions

---

### Post by ubudog on 2011-07-17
> **Mr_Electric said:**
> Thank You! I'll be sure to check it out and contact you if I have any other questions

No problem!  :-)

---

### Post by Mr_Electric on 2011-07-18
I downloaded QT and was messing around with it. I have successfully created a GUI but I think I need help connecting it with the main() c++ code (that I haven't written yet) and interfacing that to type commands into terminal.


Thanks Once Again,
Mr_E

---

### Post by Simian Man on 2011-07-18
C++ and QT is a horrible suggestion for what you want to do.  It is way too complicated.  It'd be like suggesting you use an industrial blowtorch to make some toast :).

A simpler way would be to use zenity which is a command that allows you to use simple GUIs from bash scripts.  If you only need something with a few GUI controls, zenity would suffice.  If you need something more, then you will need a full programming language, but even then I would recommend Python and Tkinter over C++/QT as the best option.

---

### Post by ubudog on 2011-07-18
> **Simian Man said:**
> C++ and QT is a horrible suggestion for what you want to do.  It is way too complicated.  It'd be like suggesting you use an industrial blowtorch to make some toast :).

A simpler way would be to use zenity which is a command that allows you to use simple GUIs from bash scripts.  If you only need something with a few GUI controls, zenity would suffice.  If you need something more, then you will need a full programming language, but even then I would recommend Python and Tkinter over C++/QT as the best option.

LOL, I suppose you are correct, it is a bit overkill for a small project.  I do second Python/TK, that's the first thing I learned.  Here is one of my projects you can download for some examples in Python/TK.

[http://guessie.sourceforge.net](http://guessie.sourceforge.net)
(make sure to get 1.0)

For Python/TK, you will need to install the python-tk package:
```
sudo apt-get install python-tk
```

---

### Post by TwoEars on 2011-07-18
> **Simian Man said:**
> C++ and QT is a horrible suggestion for what you want to do.  It is way too complicated.  It'd be like suggesting you use an industrial blowtorch to make some toast :).

A simpler way would be to use zenity which is a command that allows you to use simple GUIs from bash scripts.  If you only need something with a few GUI controls, zenity would suffice.  If you need something more, then you will need a full programming language, but even then I would recommend Python and Tkinter over C++/QT as the best option.

+1

@OP
Have you had any prior programming language experience?

---

### Post by Mr_Electric on 2011-07-18
Okay. Sounds Good, but I know a little C++. The only thing is,if I install the Python program. Then I'm going to need help writing python (I never really got it). I'm looking for somthing similar to Mac OS X's Automator where you can setup an "Ask for Conformation" and then link it to "Run Shell Script".

Thank you So Much,
Mr_E

---

### Post by TwoEars on 2011-07-18
> **Mr_Electric said:**
> Okay. Sounds Good, but I know a little C++. The only thing is,if I install the Python program. Then I'm going to need help writing python (I never really got it). I'm looking for somthing similar to Mac OS X's Automator where you can setup an "Ask for Conformation" and then link it to "Run Shell Script".

Thank you So Much,
Mr_E

Basically, you want a script with a GUI start up? If it needs root powers, you could always use gksu/beesu. Otherwise, Zenity + Bash will be more than enough for your needs.

---

### Post by Mr_Electric on 2011-07-18
I'll be sure to check it out!  :)

---

### Post by Mr_Electric on 2011-07-18
Thanks I'll be sure to check it out! :D

---

### Post by Mr_Electric on 2011-07-20
I did some research about Zenity and it seems helpful, but I need to write an application that *types* commands into terminal when a button is pressed. I need it to send it commands to my Arduino (programmable microcontroller [http://arduino.cc/](http://arduino.cc/)) through the screen terminal command to control some servos. I want to develop a clean GUI interface. 

Thanks Again
MR_E :o

---

### Post by ubudog on 2011-07-21
Here is something in Python (with TK) I made this morning, as an example.  It does what you want; it has a button, and when you click on it, it executes the command you put in the code.  So, to make it work for you, modify the main.py file, and change the "your command here" to whatever command you want to use.  Then, do:
```
python main.py
```

Hope this helps you learn a bit.  Enjoy, and let us know if you have any questions.  :-)

---

### Post by Mr_Electric on 2011-07-22
Thank You So Much. I am going to check it out now. Could you please tell me how to add more buttons (I need about 6). 


Thank You Soo Much

Mr_E

:)

---

### Post by Mr_Electric on 2011-07-22
Can you help me write the same code in C++ so I can attach it to the GUI I created with QT. 


Other than that it is exactly what I'm looking for

Mr_Electric

P.S How do you attach the GUI objects (buttons, sliders, ect) to the code?

---

### Post by TwoEars on 2011-07-22
> **Mr_Electric said:**
> Can you help me write the same code in C++ so I can attach it to the GUI I created with QT. 


Other than that it is exactly what I'm looking for

Mr_Electric

P.S How do you attach the GUI objects (buttons, sliders, ect) to the code?

No need. You can use Python.

Read here- [http://www.riverbankcomputing.com/static/Docs/PyQt4/html/](http://www.riverbankcomputing.com/static/Docs/PyQt4/html/)

---

### Post by ubudog on 2011-07-22
Nope, there is no need, you can do everything you want by modifying the main.py file.  Let's say you want to add a button.  You already have the "gobtn", so it would go something like this.  Put this one line below the gobtn code.  

```

secondbtn = Tkinter.Button(frame, text="My Second Button",command=mysecondcommand)
secondbtn.pack(side=BOTTOM)

```

You may want to modify the code a bit.  Also, you will want to create a command up where I put the "def gocommand():".  So the command would be like this:  (assuming you are still executing command line programs)

```
def mysecondcommand():
          os.system("commandlinecommand")
```

* replace "commandlinecommand" with the command line command, lol. 

Using this, you can create as many buttons as you want.  Let me know if you have any questions.

---

### Post by Mr_Electric on 2011-07-22
Thank You! The second line of code made Much clearer. I am going to try it out in a little bit (due to an unrelated problem, my hard drive failed and I had to reinstall it on a new one).
 Mr_E

---

### Post by ubudog on 2011-07-22
Sucks that your HD died, I know how you feel...

Well, let me know if you have any problems/questions.  :-)

---

### Post by Mr_Electric on 2011-07-22
Actually It is not so bad. I installed Ubuntu on a spare machine of mine and use it for developing and other fun. I do all my work on my laptop (Windows7/Mac OS 10.6) and my tower (Mac OS 10.4). Anyhow, once I finish developing the program, I am going to export it to a BeagleBoard([http://beagleboard.org/](http://beagleboard.org/)) running Natty with an Arduino([http://arduino.cc/](http://arduino.cc/)). My aim is to have an easy to use interface (the app on the BeagleBoard) that controls servos, motors, lights, ect remotely (using a wireless card and VNC). The Arduino will be the low level Microcontroller linked by the *screen* command in Terminal

Thank You SO Much.
I am going to work on the python code and I will get back to you if I need anymore help/

Mr_E  :mrgreen:

---

### Post by LemursDontExist on 2011-07-22
As an aside - have you considered interfacing with the arduino directly from python?  I've found that that's easy and clean.  Some [instructions]("http://www.arduino.cc/playground/Interfacing/Python").

---

### Post by ubudog on 2011-07-22
> **LemursDontExist said:**
> As an aside - have you considered interfacing with the arduino directly from python?  I've found that that's easy and clean.  Some [instructions]("http://www.arduino.cc/playground/Interfacing/Python").

Nice!

---

### Post by Mr_Electric on 2011-07-22
Hmmm. Not bad, though I still think Arduino and the *screen* command work well. As for the python code, It is exactly what I was looking for. 

I will post some pictures once my project is completed and I will contact you'll if I need anymore assistance.



Mr_E   :o

---

### Post by Mr_Electric on 2011-07-22
Is there a way to trigger the buttons using the Arrow Keys?

Thanks,
MR_E :(

---

### Post by Mr_Electric on 2011-07-22
I modified the code you gave me to one that has three buttons (you can see in the screenshot) so that it would configure the arduino (screen /dev/ttyACM0). I also added two other buttons for turning an led on and off. When I start up the code, I can click the configure button and it opens a screen session with the Arduino, but the Configure button is still highlighted, preventing me from sending the commands using the other two buttons. Can you please check my code and tell me what I did wrong?

---

### Post by ubudog on 2011-07-23
Hmm, I believe that's because the screen command is running, and it continues to run and doesn't stop.  Of course, you can't kill it, or the other buttons won't work...

I've modified the LED.py code to where I think it will work.  Make a backup of your current LED.py, and then download and replace it with this one.

---

### Post by Mr_Electric on 2011-07-23
Well now it clicks but I get a message in terminal that it needs to be connected to a terminal (check the screenshot). I modified the code so that is runs screen in the Root user (I unlocked that) mode but it still says that it needs to be connected to a terminal. I attached my modified LED2.py file.

Thank You SO Much
Mr_E :P

---

### Post by Mr_Electric on 2011-07-23
Here are the attachments. Sorry I forgot to upload them in my previous post ;)

---

### Post by ubudog on 2011-07-24
I modified it a bit, with something I found on Google.  Let me know how it goes.  :-)

---

### Post by Mr_Electric on 2011-07-25
Still not working. I tried it out but it says that it needs to be connected to a terminal (again) and it needs *suid root* to be run. Is there a way to just link the code to a terminal without the root? 

Thanks for all your help
MR_E

---

### Post by kalaharix on 2011-07-27
Hi

I don't understand why you are involving a terminal as an intermediary in your gui. /dev/ttyACM0 is a raw device and behaves like a file. You should be able to redirect output to the raw device. I must admit that I have not done this with USB but have used the method on both parallel (e.g. /dev/lp0) and serial devices.

My advice (admittedly untested) would be to create a simple text file containing "0011" (without parentheses). You should then be able to cat the file to the device with something like 'cat /home/Fred/Documents/ledOn.txt>/dev/ttyACM0' or whatever.

Once you can successfully test that from the terminal then your can use your os.system(same command) from within the gui.

---

### Post by Mr_Electric on 2011-07-27
Maybe that would work... The device (my arduino UNO) is using a virtual serial port which is named /ttyACM0. Could you please show me an example on how I could use your method?


Thanks, 
Mr_E

---

### Post by LemursDontExist on 2011-07-29
> **kalaharix said:**
> Hi
I don't understand why you are involving a terminal as an intermediary in your gui. /dev/ttyACM0 is a raw device and behaves like a file. You should be able to redirect output to the raw device. I must admit that I have not done this with USB but have used the method on both parallel (e.g. /dev/lp0) and serial devices.

This seems like a good time for another plug for just connecting to the device [directly in python]("http://www.arduino.cc/playground/Interfacing/Python").  Getting rid of all the intermediary stages would eliminate all the complexity.

---

### Post by Mr_Electric on 2011-07-29
Okay, so how would I do it?

---

### Post by LemursDontExist on 2011-07-29
If I understand right, you have the arduino connected as a serial device at /dev/ttyACM0, so the [instructions]("http://www.arduino.cc/playground/Interfacing/Python") I've linked above should apply pretty directly.

I believe pySerial is installed by default in Ubuntu if ```
import serial
``` works in python, you're good.  If not,
```
sudo apt-get install python-serial
``` should get it for you.

After that 
```
import serial
ser = serial.Serial('/dev/ttyACM0', 9600)
```

gets you a serial connection, and you can use it like any file object.  So

```
line = ser.readline()
ser.write("0011")
```

should, in turn, read a line of input from the Arduino and write "0011" to the it.

Withot more detail on exactly what you're doing it's hard to say more, but you can play around with it directly in the python interpreter and see what works.

---

### Post by Mr_Electric on 2011-07-31
The reason why I am trying to interface my arduino with a GUI so I can have an easy to use interface to control LEDs, Servos, ect. I am just a beginner and I have asked around a few places an gotten a lot of responses on how I can do it. I have been told that I can use quickly, QT, or just a python code but whatever method I use I just want to be able to get the job done. Can you please direct me (or tell me how) to get this done.

Thanks,
Mr_E

---

### Post by LemursDontExist on 2011-08-01
Sorry about the slow reply - life's been busy!

I looked at the code you've been working with, and it wasn't very clear to me what the manconfig function was for.  But here's a version that should at least let you control the leds directly. (assuming that your arduino is programmed to respond to "0011 " (are those spaces intentional - or a typo?), "0022"  by turning on (toggling?) leds 1 and 0 respectively).

```
#!/usr/bin/python
import Tkinter
from Tkconstants import *
import serial

tk = Tkinter.Tk()
tk.title("LED CONTROL")
ser = serial.Serial('/dev/ttyACM0', 9600)

def led1():
     ser.write("0011  ")

def led0():
     ser.write("0022")

frame = Tkinter.Frame(tk, relief=RIDGE, borderwidth=5)
frame.pack(fill=X, expand=1)
abtmain = Tkinter.Label(frame, text="Press a button below.")
abtmain.pack(fill=X, expand=1)

led1btn = Tkinter.Button(frame, text="LED ON",command=led1)
led1btn.pack(side=LEFT)

led0btn = Tkinter.Button(frame, text="LED OFF",command=led0)
led0btn.pack(side=RIGHT)

tk.mainloop()
```

---

### Post by Mr_Electric on 2011-08-01
Well actually the manual configuration (manconfig) button was to start the screen session with the arduino but now I see that it is not necessary. I originally wanted to put 0 and one but decided on 0011 so it would be four characters.

Thanks,
Mr_E :D

---

### Post by Mr_Electric on 2011-08-04
Thanks to all of you'll, I've finally been able to accomplish my task and get my problem solved.

Thanks again,
Mr_E

---

### Post by ubudog on 2011-08-04
Sounds good!

---

### Post by onizukal on 2012-01-12
Hey all 
 Sorry actually my question is little far from the main question but i use your good programmers code to my project and i got some problems caused by it . Actually i little bit modified the main.py as my project but the problem when i used it , main.py is just stop working . In my project i should make a gui for launching FFServer and also the same gui should be able to stop it but my problem is FFserver is starting as how i want but when it started main.py program is just becaming deactivating. i cant click on the other button that is gonna make stop the FFserver . But it is just GUI which is not clickable. When i click the command screen , it is working . I can stop the server by pressing CTRL + C . But the GUI is not working . Button just pressed and not released . 

[http://imageshack.us/photo/my-images/51/screenshotokv.png/](http://imageshack.us/photo/my-images/51/screenshotokv.png/)

I dont have much idea about python . Sorry for my novice status but if you help me , i can be gratefull . Thank you

---

