---
title: "Who can drop few lines of code?Send you beer!"
date: 2009-08-22
forum: Programming Talk
---

### Post by realzippy on 2009-08-22
Ok,need some code:

that "presses Shift+F9" after given time and interpreted any next keyboard/mouse input as Shift+F9

thats all.

Will send you 2 bottles german beer,not that export stuff,wherever you live!

---

### Post by ArmenianLeader4 on 2009-08-22
In what application (ex. HTML, Python, Others) for what purpose (Malicious, otherwise), and, as a seemingly random question, is this for the rain function with Compiz? Because there are other ways to set that up.

Oh, and I don't want your beer.

---

### Post by pepperphd on 2009-08-22
There seems to be a Python library for this.

[http://www.daniweb.com/forums/thread139376.html](http://www.daniweb.com/forums/thread139376.html)

---

### Post by realzippy on 2009-08-22
> **ArmenianLeader4 said:**
> In what application (ex. HTML, Python, Others) for what purpose (Malicious, otherwise), and, as a seemingly random question, is this for the rain function with Compiz? Because there are other ways to set that up.

Oh, and I don't want your beer.

yep,randomly right....rainplugin as screensaver

---

### Post by realzippy on 2009-08-23
> **ArmenianLeader4 said:**
> In what application (ex. HTML, Python, Others) for what purpose (Malicious, otherwise), and, as a seemingly random question, is this for the rain function with Compiz? Because there are other ways to set that up.

Oh, and I don't want your beer.

No?
[http://en.wikipedia.org/wiki/Beerware](http://en.wikipedia.org/wiki/Beerware)


Can you tell me more about the other ways please?

---

### Post by Nevon on 2009-08-23
```
sudo apt-get install xautomation
```

```
#!/usr/bin/env bash

while [ 1 ]
do
    xte "keydown Shift_L"
    xte "key F9"
    xte "keyup Shift_L"
    sleep 60s # Change this for longer intervals
done
```

Now how about that beer?

---

### Post by realzippy on 2009-08-23
> **Nevon said:**
> ```
sudo apt-get install xautomation
```

```
#!/usr/bin/env bash

while [ 1 ]
do
    xte "keydown Shift_L"
    xte "key F9"
    xte "keyup Shift_L"
    sleep 60s # Change this for longer intervals
done
```

Now how about that beer?

Cannot test it til tuesday evening,not at my machine now.But made one mistake:
wanted it as compiz/rainplugin screensaver:

...that "presses Shift+F9" after given time [COLOR="Red"]of Mouse/Keyboard inactivity[/COLOR] and interpreted any next keyboard/mouse input as Shift+F9

Sorry,forgot that.Can this be done?
What beer you prefer?Dark and strong?Bavarian?Weissbier?

---

### Post by Nevon on 2009-08-23
> **realzippy said:**
> Cannot test it til tuesday evening,not at my machine now.But made one mistake:
wanted it as compiz/rainplugin screensaver:

...that "presses Shift+F9" after given time [COLOR="Red"]of Mouse/Keyboard inactivity[/COLOR] and interpreted any next keyboard/mouse input as Shift+F9

Sorry,forgot that.Can this be done?
What beer you prefer?Dark and strong?Bavarian?Weissbier?

I'm not sure I follow you. You want it to wait for you to stop moving your mouse, and once you do, a timer should start. At a certain interval, you want to simulate pressing Shift + F9. Once you move your mouse again, the timer should stop? 

And it can't be a standalone application, but it has to be somehow incorporated into compiz? 

The first part I might be able to handle, but there's no way I could work it into compiz.

---

### Post by realzippy on 2009-08-24
> **Nevon said:**
> I'm not sure I follow you. You want it to wait for you to stop moving your mouse, and once you do, a timer should start. At a certain interval, you want to simulate pressing Shift + F9. Once you move your mouse again, the timer should stop? 

And it can't be a standalone application, but it has to be somehow incorporated into compiz? 

The first part I might be able to handle, but there's no way I could work it into compiz.


I want to start rain plugin as screensaver (manually started and stopped by Shift+F9)....so the script should detect that there is no Keyboard/Mouse action for given time,start rain plugin,and stop it by any mouse/keyboard action.
It can be a stand-alone-application;thought to put the script somewhere in
/etc/init.d/ ?

---

### Post by kpkeerthi on 2009-08-24
> **Nevon said:**
> ```
sudo apt-get install xautomation
```
Now how about that beer?
Thanks for that. Never heard of this tool before. Might come handy sometime.

---

### Post by realzippy on 2009-08-28
bump

---

### Post by unutbu on 2009-08-28
realzippy, does this command activate your screensaver?
If it does, that might be a start toward a solution:

```
qdbus org.gnome.ScreenSaver / SetActive True
```

---

### Post by realzippy on 2009-08-29
> **unutbu said:**
> realzippy, does this command activate your screensaver?
If it does, that might be a start toward a solution:

```
qdbus org.gnome.ScreenSaver / SetActive True
```


YES!It does.....

---

### Post by unutbu on 2009-08-29
Wonderful. Now here's (maybe) the tricky part: What does this return
```

sleep 5; qdbus org.gnome.ScreenSaver / GetSessionIdleTime
```

Also, after the screensaver is activated, you want any keypress to have the same effect as pressing Shift+F9, correct? What does pressing Shift+F9 do?

---

### Post by realzippy on 2009-08-29
> **unutbu said:**
> Wonderful. Now here's (maybe) the tricky part: What does this return
```

sleep 5; qdbus org.gnome.ScreenSaver / GetSessionIdleTime
```

Also, after the screensaver is activated, you want any keypress to have the same effect as pressing Shift+F9, correct? What does pressing Shift+F9 do?

..it returns:  **0**



Shift+F9 starts/stops compiz rainplugin,which I wanted as screensaver:

"Ok,need some code:

that "presses Shift+F9" after given time of Mouse/Keyboard inactivity and interpreted any next keyboard/mouse input as Shift+F9"

---

### Post by unutbu on 2009-08-29
> ..it returns: 0

This is a show-stopper... at least until we find a way to coax the computer into telling us how long the X session has been idle.

PS. When you run
```

qdbus org.gnome.ScreenSaver / SetActive True
```

does the rain plugin start, or is your screen saver something else?

---

### Post by realzippy on 2009-08-29
> **unutbu said:**
> This is a show-stopper... at least until we find a way to coax the computer into telling us how long the X session has been idle.

PS. When you run
```

qdbus org.gnome.ScreenSaver / SetActive True
```

does the rain plugin start, or is your screen saver something else?


Default Gnome screensaver starts.
rain plugin needs shift+F9...
...sorry for delay,soccer....

---

### Post by unutbu on 2009-08-29
realzippy, Since compiz seems to crash my machine, I haven't been able to test this completely. 

[list]
[*] First install the build-essential, libxss-dev and xdotool packages.

[*]Then go to [http://ubuntuforums.org/showpost.php?p=7865664&postcount=2](http://ubuntuforums.org/showpost.php?p=7865664&postcount=2)
and copy stroyan's C program to xidle.c

Compile the program:
```

cc xidle.c -o xidle -lX11 -lXext -lXss
```

This will create the executable "xidle".
[*] Move the executable xidle to ~/bin, so the program will be in your PATH.
[*] Check that it works by running
```

sleep 5; xidle
```

You should get a number like 
```

4.962000 
```

in response.

[*] Now save this in ~/bin/idlerain.py

[PHP]
#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT,call
import os
import time

def get_idle_time():
    proc=Popen('xidle', shell=True, stdout=PIPE, )
    return float(proc.communicate()[0])

is_raining=False
sleep_seconds=1
max_idle=20
last_idle=0
rain_start_time=time.time()
while True:
    idle=get_idle_time()
    if is_raining:
        duration=time.time()-rain_start_time        
        if(is_raining and duration>1.5*sleep_seconds and
          idle<last_idle):
            is_raining=False
            os.system('xdotool key shift+F9')        
    else:
        if (last_idle<max_idle and max_idle<=idle):
            is_raining=True
            rain_start_time=time.time()
            os.system('xdotool key shift+F9')
    last_idle=idle
    time.sleep(sleep_seconds)
[/PHP]

[*]Make it executable:
```
chmod +x ~/bin/idlerain.py
```

[*]For now, try running it from the terminal. If it works to your liking, it can be set to run automatically when you log in. 

Run it by typing:
```

idlerain.py
```

Wait for 20 seconds. Then the rain should start. Press a key, and the rain should end.

Press Ctrl-C to stop the idlerain.py program.
[/list]

---

### Post by realzippy on 2009-08-30
Move the executable xidle to [COLOR="Red"]~[/COLOR]/bin, so the program will be in your PATH

Sorry for stupid question:
Is it really ~/bin,not /bin?

(do not have /bin folder in home directory.Should i create it?...if I move xidle to /bin instead of ~/bin,then **sleep 5; xidle** gives me a number like 4.962000,
otherwise "command not found"...????)

---

### Post by unutbu on 2009-08-30
No problem, realzippy.

~/bin is the same as /home/realzippy/bin (if your username is realzippy).
/bin is the system's /bin directory. (I don't recommend putting it in there.)

If you don't have a ~/bin directory, make one. Ubuntu is setup for you so that if you have a ~/bin directory, all executables are automatically "in your PATH". That means you can run them by name:
```

xidle
```

instead of by full path:
```

/home/realzippy/bin/xidle
```
It saves some typing.

PS. If you make a ~/bin directory, close your gnome-terminal and re-open it so your PATH will be updated.

---

### Post by realzippy on 2009-08-30
Ok,got that.
Rain does start (after 5 seconds),but it does not stop by keybord input
or mouse movement.When I stop script with ctrl+c,I got this:

kerzin@holzhaus:~$ idlerain.py
     ^CTraceback (most recent call last):
  File "/home/kerzin/bin/idlerain.py", line 18, in <module>
    time.sleep(sleep_seconds)  
KeyboardInterrupt
kerzin@holzhaus:~$

..and it still rains...

Edit: idlerain.py   :

#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT,call
import os
import time

def get_idle_time():
    proc=Popen('xidle', shell=True, stdout=PIPE, )
    return float(proc.communicate()[0])

sleep_seconds=1    
max_idle=5
last_idle=0
while True:
    idle=get_idle_time()
    if (last_idle<max_idle and max_idle<idle) or (idle<last_idle):
        os.system('xdotool key shift+F9')
    last_idle=idle
    time.sleep(sleep_seconds)

---

### Post by unutbu on 2009-08-30
Hm. Put this in ~/bin/test.py

[php]#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT,call
import os
import time

def get_idle_time():
    proc=Popen('xidle', shell=True, stdout=PIPE, )
    return float(proc.communicate()[0])

sleep_seconds=1    
max_idle=5
last_idle=0
while True:
    idle=get_idle_time()
    print(idle)
    if ((last_idle<max_idle and max_idle<=idle) or
        (idle<max_idle and max_idle<=last_idle)):
        print('Shift+F9')
    last_idle=idle
    time.sleep(sleep_seconds)
[/php]
Make it executable:

```
chmod +x ~/bin/test.py
```

And the run it:

```
test.py
```

Wait for >5 seconds, then move the mouse.

Do you see output like this:

```
% test.py
0.047
1.002
2.006
3.01
4.013
5.014
Shift+F9              <----   First Shift+F9 happens after 5 seconds
6.018
7.022
0.682
Shift+F9              <----   Mouse movement causes a Shift+F9
1.686
2.69
^CTraceback (most recent call last):
  File "/home/cyrano/pybin/idlerain.py", line 21, in <module>
    time.sleep(sleep_seconds)
KeyboardInterrupt
```

Note this program does not issue any real Shift+F9, it's just to see if the 
mechanics of the program are working.

---

### Post by realzippy on 2009-08-30
kerzin@holzhaus:~$ test.py
0.026
0.991
1.996
3.002
4.008
5.013
Shift+F9
6.018
7.024
8.029
0.002
Shift+F9
0.64
1.645
2.65
3.655
4.66
5.666
Shift+F9
6.671
0.005
Shift+F9
0.738
1.744
^CTraceback (most recent call last):
  File "/home/kerzin/bin/test.py", line 20, in <module>
    time.sleep(sleep_seconds)  
KeyboardInterrupt
kerzin@holzhaus:~$ 


Hm,that seems to work.Update: idlerain.py now stops by ctrl+c,no more rain...,but still not reacts on mouse/keyboard..

I set the max_idle in  idlerain.py to 20 (when compiz rainplugin is stopped by "manual" shift+F9,rain does not stop immediatly,it takes a few seconds til all drops are gone),and so I noticed that a really short mouse movement indeed stops the rain,moving the mouse a bit more,rain starts immediatly;like shift+F9 is "hit" twice by idlerain ...

**Also** just noticed (with max_idle in  idlerain.py to 20),that the script does start the rain,but also stops it...after 20 seconds it starts again and stops,and so on...
Edit: that seems not to be reproducible;sometimes it stops,sometimes not...


Did not think that it's so hard to do...my girlfriend likes the rainplugin and suggested it would be a nice screensaver for her desktop...thought it was easy because of the existing compiz screensaver (rotating cube,e.g.)....just thought to change a few lines in compiz screensaver plugin from "rotate cube" to "rain"...might be pretty naive..

---

### Post by unutbu on 2009-08-30
I fixed an error in the original idlerain.py. Try copying it again:
[http://ubuntuforums.org/showpost.php?p=7866714&postcount=18](http://ubuntuforums.org/showpost.php?p=7866714&postcount=18)

Does that work?

---

### Post by realzippy on 2009-08-30
No.
after 20 seconds rain starts and stops after 1 second...after 20 seconds it starts,stops..
and so on....

---

### Post by unutbu on 2009-08-30
> Did not think that it's so hard to do...my girlfriend likes the rainplugin and suggested it would be a nice screensaver for her desktop...thought it was easy because of the existing compiz screensaver (rotating cube,e.g.)....just thought to change a few lines in compiz screensaver plugin from "rotate cube" to "rain"...might be pretty naive..

realzippy, I think your intuition is right. 
I don't have compiz working on my machine, so I'm clueless about how it is configured.
Moreover, running a program (xidle) every second to check if the machine is idle does give me the feeling that this is ugly hackery. Perhaps I'm not the right chipmunk for the job!

Have you asked in the Absolute Beginner or General forum if there is a way to configure compiz to run the rain plug as screensaver? Or perhaps on the compiz forum? ([http://forum.compiz.org/](http://forum.compiz.org/))

---

### Post by realzippy on 2009-08-30
Yes,I asked for it in Desktop Environments(no reply,[http://ubuntuforums.org/showthread.php?t=1243554)](http://ubuntuforums.org/showthread.php?t=1243554)),so I thought Programming Talk would be right.
I searched the compiz forum (very first);somebody had asked for it,but did also get no reply...

"Moreover, running a program (xidle) every second to check if the machine is idle does give me the feeling that this is ugly hackery"

...do the default gnome screensavers check idle by another way?

Would not mind that ugly hackery,so my girlfriends quadCPU would have something to do at last... ;-)
Anyway it is no real essential problem not to have a rain screensaver,so I
feel kind of guilty for the time you spent.So,what about some beer?

---

### Post by unutbu on 2009-08-30
realzippy, yours has been a fun problem to work on. I'm puzzled why the program is misbehaving as it is. I'll think about it and post if I have any ideas.
> 
So,what about some beer?

Thanks for the offer. How about a virtual one for a virtual solution? :)

---

### Post by unutbu on 2009-08-30
I've modified idlerain.py so that it spits out some debugging information: [http://ubuntuforums.org/showpost.php?p=7866714&postcount=18](http://ubuntuforums.org/showpost.php?p=7866714&postcount=18)

Would you please run the program for about a minute and
mark in the output when the rain plugin starts and stops?

---

### Post by realzippy on 2009-08-31
First [this]("http://www.freakingnews.com/images/app_images/beer-mug.jpg") one....

kerzin@holzhaus:~$ idlerain.py
0.027
0.961
1.966
2.971
3.976
4.982
5.987
6.992
7.997
9.003
10.008
11.013
12.018
13.024
14.029
15.034
16.039
17.045
18.049999
19.055
20.059999
Shift+F9                  *Rain starts*
1.006
Shift+F9                  *Rain stops*
1.006
2.012
3.017
4.022
5.027
6.032
7.037
8.042
9.048
10.053
11.058
12.063
13.068
14.073
15.079
16.084
17.089001
18.094
19.1
20.105
Shift+F9                     *Rain starts*
1.006
Shift+F9                     *Rain stops*
1.008
2.013
3.018
4.023
5.029
6.034
7.039
8.045
9.05
10.055
11.06
12.066
13.071
14.076
15.081
16.086
17.091999
18.097
19.101999
20.108
Shift+F9                    *Rain starts*
1.006
Shift+F9                    *Rain stops*
1.007
2.013
3.02
^CTraceback (most recent call last):
  File "/home/kerzin/bin/idlerain.py", line 21, in <module>
    time.sleep(sleep_seconds)  
KeyboardInterrupt
            ----------------------------------------------

*sleep_seconds=1 causes shift+F9 after rain starts?This is sleep_seconds=5  :*

kerzin@holzhaus:~$ idlerain.py
0.024
4.969
9.979
14.988
19.997
25.006001                ***25 seconds**??  (max_idle=20;sleep_seconds=5)???*
Shift+F9                 *Rain starts*
5.008
Shift+F9                 *Rain stops*
0.005
0.117
^CTraceback (most recent call last):
  File "/home/kerzin/bin/idlerain.py", line 21, in <module>
    time.sleep(sleep_seconds)  
KeyboardInterrupt

---

### Post by unutbu on 2009-08-31
Ah, that beer hit the spot! I think I understand what the problem is now. Starting the rain plugin resets xidle to 0. How about try this modified version:

[http://ubuntuforums.org/showpost.php?p=7866714&postcount=18](http://ubuntuforums.org/showpost.php?p=7866714&postcount=18)

If it works, you can eliminate all the print statements. If it doesn't work, please post the output again.

---

### Post by realzippy on 2009-08-31
**Perfect**!

Unutbu,
that was awesome.In combination with kind of wet backround image its a fantastic screensaver.Too much ugly hacking to publish in the forum?I am shure a few more people would like it..

So if you don't bother getting small wooden box with bottle of rare beer,pm
me delivery address.Would be a pleasure to me.
Thank you for your patience and time!

---

### Post by Caleb.Robertson on 2010-07-03
I am trying to get this work on 10.04 but when I run Idlerain.py
```
leb@leb-laptop:~$ ~/bin/idlerain.py
/bin/sh: xidle: not found
Traceback (most recent call last):
  File "/home/leb/bin/idlerain.py", line 16, in <module>
    idle=get_idle_time()
  File "/home/leb/bin/idlerain.py", line 8, in get_idle_time
    return float(proc.communicate()[0])
ValueError: empty string for float()
leb@leb-laptop:~$ 

```When I run xidle, I get. 
```
leb@leb-laptop:~$ ~/bin/xidle
0.006000

```Any Help would be appreciated.

EDIT Never mind I got it. The error /bin/sh: xidle: not found should of told me to put the xidle in ~/bin/sh which made it work like a charm

---

### Post by papibe on 2013-02-08
Please don't reply on old threads. It is much better to create a new one. Feel free to link this one if you want.

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Thread Closed.

---

