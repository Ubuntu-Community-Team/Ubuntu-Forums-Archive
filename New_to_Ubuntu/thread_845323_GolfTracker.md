---
title: "GolfTracker"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by cartisdm on 2008-06-30
I found this program online earlier today but I'm having trouble opening it up.

[http://www.golftracker.org/index.php?n=Main.Download](http://www.golftracker.org/index.php?n=Main.Download)

I download the .deb and it seems to install just fine but when I try to open it nothing happens.  The taskbar shows "Starting Golftracker" then it goes away after about 5 seconds.  The requirements are as follows:

>= Python 2.4
>= GTK 2.8
>= PyGTK 2.8

How can I tell what version of those I have? Maybe that is the problem...

---

### Post by Metaleks on 2008-06-30
If it installed, then all of those dependencies were satisfied. Meaning, you had everything that was required for the program to install and run. As a side note, I'm not too sure about the rest but I know that the latest version of Python is 2.5, and that it's included in Ubuntu. So don't worry.

As for why it's not starting. How exactly are you starting it? I would suggest opening up the Run Application menu (alt + F2), and typing "golf" and see if the autocomplete finds the program. If so, enter it and run it.

And if that still doesn't work, check out the manual (if there is one). And if that STILL doesn't work, you're going to have to compile the program yourself. That will do the trick.

---

### Post by cartisdm on 2008-06-30
I was starting it by selected it from the Applications menu.  I tried using the Run Application (alt+F2) and it did autocomplete golftracker but nothing happened when I tried to run it (I also tried Run in Terminal, but that didn't do anything either)

Any other ideas?

---

### Post by Metaleks on 2008-06-30
One last thing before we go for the sure all-in method. I'm assuming that when you say "run in terminal" that you chose the option "run in terminal" when it was presented to you. And still nothing happened? This leads me to believe that the program is silent on a crash. So, we will do one last thing before we compile it.

Open up your terminal, and just type:
```
golftracker
```
Wait a while, and post the output here.

---

### Post by cartisdm on 2008-06-30
From entry "golftracker"

```
Traceback (most recent call last):
  File "/usr/local/bin/golftracker", line 21, in <module>
    import GolfTracker.main
ImportError: No module named GolfTracker.main

```

FYI, if we go the compiling route....I'm going to need some pretty idiot proof directions...

---

### Post by Metaleks on 2008-06-30
That's odd. I think it's just a naming issue in the code.

Try this before suggesting the thing below: Go into your terminal and do:
```
cd /usr/local/bin/golftracker
```
```
sudo nano golftracker.py
```
And then change *import GolfTracker.main* to just *import main*. Then get out of nano (ctrl + x) and do:
```
cd GolfTracker
```
After, do:
```
sudo cp * /usr/local/bin/golftracker
```
Then
```
cd ..
```
And then:
```
sudo rm -rf GolfTracker
```
Then try running it! This is a long shot, and I've never done a fix like this, but it's worth a try. For some reason, the main file isn't importing the code. All I did above was change the src to the same directory. I doubt it's a Python issue, but something is definitely weird. The original import statement seems fine. I also don't have GolfTracker on my system, so I'm kinda doing it blind. If that doesn't work, proceed with the below.

Purge golftracker. Get rid of it completely, we're going to compile it.

Download the source. I'm assuming it's going to be in your home directory. Open up your terminal and type:
```
tar -zxvf golftracker*
```
Then:
```
golftracker*
```
Once you've done that, do:
```
./configure
```
Wait for that to finish, and then:
```
make
```
And finally:
```
make install
```
If you get no errors, you have successfully compiled golftracker for your system. Then start it how you normally would. It should work now.

---

### Post by cartisdm on 2008-06-30
I still wasn't able to start the program with the first set of instructions.  On the second set I can't get past

```
 golftracker* 
```

I get the following output
```
dan@dan-laptop:~$ golftracker*
bash: golftracker-0.6.4: command not found

```

---

### Post by cartisdm on 2008-06-30
Got it!  The instructions you gave me worked, but I ran into a few errors.  

I needed to install pygtk-2.0
```
sudo apt-get install python-gtk2-dev
```

And I installed build-essential package
```
sudo apt-get install build-essential
```

Other than that I had to think for myself a few times because I kept getting permission denied.  Works though!!

---

### Post by Metaleks on 2008-07-01
Ah, sorry! Wasn't thinking clearly, I forgot a few sudos in there, and the build-dependencies. How awful, I even told you compile without them! In any case, I'm glad you got it working :)

---

