---
title: "Starting python script inSessions?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by wyhog on 2008-05-18
I have a program I want to run each time I log on (boot). I wrote it in java and I went to System/Preferences/Sessions and added a Startup item for it. It works. I unchecked that Startup and tried the following.

I re-wrote the program in python. The program runs fine when I double-click on it in Nautilus or start a terminal and type 
python dev/remind.py
But I cannot figure out how to get it to run at boot (log in) time? I went to System/Preferences/Sessions and created a Startup item. I tried:
python remind.py
python dev/remind.py
python /home/myself/dev/remind.py
remind.py
dev/remind.py
/home/dev/remind.py

None of them work. 
The file has Permissions checked to allow execution.
I put #!/usr/bin/python as the first line of the program. I removed that line. Doesn't make any difference one way or the other.
I tried several other .py programs I have that run fine when double-clicked in Nautilus but will not autostart in Sessions. How the heck do you run a python script/program at startup?

I am using Ubuntu 8.04

Wyhog

---

### Post by sam_delta on 2008-05-18
EDIT - (had wrong location)

try adding it to /etc/init.d

then update the scripting with

sudo update-rc.d something.py defaults

i duno if it works with python scripts but it does with shell scripts

sam

---

### Post by jordanmthomas on 2008-05-18
1.  Make sure python is in fact installed at /usr/bin/python with
```
which python
```
2.  Make sure /home/myself/dev/remind.py is in fact the path to the script
3.  ```
chmod o+x /home/myself/dev/remind.py
```
    make sure you (the owner) can execute it
4.  Add the command /home/myself/dev/remind.py to the sessions menu

Is this something that outputs to a console or does it pop up a window?  If it's just a console application, you'll need to tell a terminal to run it, which is also possible.

Hopefully one of these steps will fix what's wrong.

---

### Post by sam_delta on 2008-05-18
you can also add the shell command to start the script (python script.py) in the /etc/rc.local and it will be executed each boot up

just type 
```
 gksudo gedit /etc/rc.local
```

and add to the file the command you want to execute @startup (ej add "python myscript.py")

sam

---

### Post by jordanmthomas on 2008-05-18
> **sam_delta said:**
> you can also add the shell command to start the script (python script.py) in the /etc/rc.local and it will be executed each boot up

just type 
```
 gksudo gedit /etc/rc.local
```

and add to the file the command you want to execute @startup

sam

He wants it at each login though, not just at boot.

---

### Post by sam_delta on 2008-05-18
> **jordanmthomas said:**
> He wants it at each login though, not just at boot.

my bad then, i misunderstood because of what he sayd 

"I have a program I want to run each time I log on (boot)"

my bad, was a misunderstanding

sam

---

### Post by jordanmthomas on 2008-05-18
> **sam_delta said:**
> my bad then, i misunderstood because of what he sayd 

"I have a program I want to run each time I log on (boot)"

my bad, was a misunderstanding

sam

No worries, your solution might be acceptable too.

---

### Post by wyhog on 2008-05-18
>Make sure python is in fact installed at /usr/bin/python with which python.

Yes it is.

>Make sure /home/myself/dev/remind.py is in fact the path to the script.

It is. In fact I when setting up the Sessions Startup link I used the Browse button and navigated to the program so I know the path is correct without any spelling errors.

>make sure you (the owner) can execute it

Yes I can. I said in my original post that I can execute it via double clicking in Nautilus or by starting it in a terminal.

>Is this something that outputs to a console or does it pop up a window?

It opens a TK window.

>He wants it at each login though, not just at boot.

It is a python/tk program. I probably should have mentioned that in my first post. Sorry. I am wondering if that tk windows part is the problem?

To me boot and login are about the same thing because I always turn the computer off when not in use and it is set up to auto loggin when power is re-applied to it. 

I will try editing the /etc/rc.local file as suggested. Will that work since the program uses tk windows and thus needs X windows up and running first? 

But it seems like I should be able to launch a python/tk program via Sessions?

Wyhog

---

### Post by wyhog on 2008-05-18
I tried the rc.local thing. It doesn't work either.

The problem seems to be the python program's tk window? I wrote a short test python program that does nothing but create a text file and write a line of text to it. 

fout = open('/home/myself/test/test45.txt', 'w')
fout.write('Some test text for a non tk window python program to write.')
fout.close()

I then created a Sessions Startup item for this program using:
python /home/myself/test/test45.py
That program does run when I reboot. I know that because the file it creates is there when I check for it after booting. I can delete that file then reboot and each time the file is back. So it is working.

So now the question is; Does anyone know how to run a tk/python program at boot or login? If no one knows how I guess I'll have to go back to using the java version because it will run ok each boot/login.

Thanks for the suggestions though.

Wyhog

---

### Post by wyhog on 2008-05-19
>
[B]#!/bin/bash

sleep 60
exec /home/me/myprog.py[/B]
>


Wow! That works. Starting the "delay" shell script in Sessions instead of directly starting the python/tk program in Sessions works. It will now run my program at startup. Well a few seconds after startup. 

Thank you, VOR.

I still think the fact that Ubuntu will not run a python/tk or a pythom/gtk program directly from Sessions without this delay work-around is a bug though.

Wyaak

---

