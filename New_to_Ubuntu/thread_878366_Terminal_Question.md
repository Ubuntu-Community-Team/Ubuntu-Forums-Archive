---
title: "Terminal Question"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by EnergySamus on 2008-08-02
Hi! 
I know that there is a way to open applications directly from the terminal, but how do you do it? I know that in a Mac you just type 'open' followed by the name of the application. I tried that already and it doesn't work (figures, doesn't it? :guitar:). 


Thanks!
EnergySamus

---

### Post by Joeb454 on 2008-08-02
Just type the name of the application :)

---

### Post by alzie on 2008-08-02
Try using Alt+F2 and click on run in terminal.

I hope this helps

---

### Post by perlluver on 2008-08-02
> **EnergySamus said:**
> Hi! 
I know that there is a way to open applications directly from the terminal, but how do you do it? I know that in a Mac you just type 'open' followed by the name of the application. I tried that already and it doesn't work (figures, doesn't it? :guitar:). 


Thanks!
EnergySamus

You normally just type in the name of the program.  For example amarok would open amarok, firefox will open firefox.

---

### Post by kk0sse54 on 2008-08-02
Just type the name of the application or if you don't want to open it through the terminal press alt + f2 to open the run dialog.

---

### Post by sharks on 2008-08-02
alt+f2 will open a run dialog box.

---

### Post by kk0sse54 on 2008-08-02
> **sharks said:**
> alt+f2 will open a run dialog box.

yes you are completely correct but I accidentally pressed four and wasn't paying attention which would instead close an application which is why I promptly changed it :oops:

---

### Post by Jimmyfj on 2008-08-02
Simple enough

Just open a terminal window and type the name of the program you which to laungh: nautilus will, ofcause launch the file browser Nautilus

---

### Post by rburkartjo on 2008-08-03
energy when you open an application in the terminal you should alway type
(space)&(space)exit this will insure that the terminal is closed if you dont do this sometimes if you close the terminal the program will also close.example to open vlc in terminal and then close the terminal and leave vlc open type vlc & exit. you can open more than one program at once by using the |. example firefox | vlc & exit will open firefox,vlc and then close the terminal/cheesemaker

---

### Post by Claus7 on 2008-08-03
Hello,

> **rburkartjo said:**
> -more or less-

Energy, when you open an application in the terminal you should always type :
name_of_the_application(space)&(space)exit 

This will insure that the terminal is closed. If you dont do this, sometimes if you close the terminal the program will also close.
For example if you want to open vlc in terminal and then close the terminal and leave vlc open, type vlc & exit. 
You can open more than one program at once by using the |. 
For example firefox | vlc & exit will open firefox,vlc and then close the terminal/cheesemaker

Very nice indeed. If I wanted to run an application in the backround and close the terminal, I didn't know that I had to type exit in the end, after the ampersand. So, I had to press enter in order to have user_name@machine-desktop:~$ prompt, and in between some few seconds to type exit, before the screen to be refreshed again by the data of the program. 

Regards!

---

### Post by ion072002 on 2008-08-03
one more thing: only applications in /usr/bin will start when you type their name in the terminal. for applications installed elsewhere, you need to type in the whole path

---

### Post by unutbu on 2008-08-03
Suppose you have a directory called bin in your home account and you put executables in there. To get the shell to look in bin when you run a command, you need to edit your PATH environment variable:

gedit ~/.profile
Add a line at the bottom that says

```
PATH=$PATH:$HOME/bin
export PATH
```

If you have other directories you'd like checked, just add them to the "PATH=$PATH:$HOME/bin" line, with each path separated by a colon (:).

The change will take effect after you logout and log back in.

To check your current PATH:
```

echo $PATH
```

---

### Post by Claus7 on 2008-08-03
Hello,

the order that someone declares the paths plays also a role. For example if we have two different commands with the same name in two different folders, that both belong to the path, the one that will be executed first, will be the one that is written first in the path. Just FYI.

Regards!

---

### Post by bodhi.zazen on 2008-08-03
to run an application independent of the terminal, so the application stays open when you close the terminal, use "nohup"

```
nohup application &
```

---

### Post by apoisonedapple on 2008-08-03
This is a super dumb question, and I pretty much installed everything using command line, but this is one thing I cannot figure out. It probably should have been the first thing I learned, but I am a little backarsewards.

I get an error message like this:

 firefox
/home/atropine/.themes/Hemoglobinus/gtk-2.0/panel.rc:30: Unable to locate image file in pixmap_path: "shadows/window-bg.png"
loaded md5.js
 and then all that comes up is a blinking cursor. How do I get another line back like YOURNAME@ BLAHBLAHBLAH ~ $ again?

Do I have to exit terminal? 

Vielen Dank!

---

### Post by Xiong Chiamiov on 2008-08-03
Ctrl+c is interrupt.

---

### Post by unutbu on 2008-08-03
apoisonedapple, 

```

Ctrl-Z   # stop the process that is hogging the terminal
```      

This will get you your prompt back, but will stop firefox. To resume firefox and allow you to use the terminal, then type

```

bg       # send the last process to the background
```

Alternatively, you can start firefox by typing
```

firefox &
```

---

