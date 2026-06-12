---
title: "Script to take  screenshot of a specific window"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by satman-ga on 2008-08-18
I've seen various posts with scripts to take screenshots, but I have yet to find a way to specify a window without actually selecting it. Is there a utility that I can pass window title and saved image filename/location to in order to take a shot of that window and save automatically?

---

### Post by Dill on 2008-08-18
I did some searching and came up with something that may work for you:

First, you have to install **imagemagick** from the repositories, which contains a command called **import**, which allows you to take a picture of any active window and save it as a file. You may want to read the man page on import for more information. So to start, open a Terminal and type this:

```
sudo apt-get install imagemagick
man import
```

You'll also need to use a program called **xwininfo**, which gives you a bunch of information about a given window, including what's called a "window ID". This is helpful in determining the window of which we're taking a screenshot. xwininfo should already be installed on your system.

I dashed up this shell script, which doesn't work completely. It's a start, though. Please note that I'm quite new to shell scripting and there are other, more experienced people here who may be of more help.

```
#!/bin/sh
echo "Enter the name of the window:"
read window
window_id=`xwininfo -name $window | awk '{print $4}' | grep -i 0x`
import -window $window_id $window.jpg
```

I mostly pieced this together from stuff I found from Google...

Line 1: #!/bin/sh 
Line 2: Prints "Enter the name of the window:"... just prompts the user for the name of the window
Line 3: Reads standard input and stores it in a variable called "window"
Line 4: Defines a variable called window_id -- basically, you can execute xwininfo with the *name* parameter and follow it by the name of the window (which in our case should be the variable we just created, $window); pass the output of that to an awk command (I've never used awk, but I think this gets the fourth element of an array, which prints a column of data from the output of *xwininfo -name $window*, and which contains our window ID; pass that output again to grep and look for the string '0x' (our window ID, by default, is a hexadecimal value, and should always begin with a 'Ox').
Line 5: The import command imports the window with the window ID window_id and stores it in a file called $window.jpg (hence, if you take a screenshot of Calculator, the file should be called Calculator.jpg.

Like I said before, this doesn't work completely, but I thought I'd post it anyway. I've gotten it to work for small programs like Calculator, Dictionary, Atomix... nothing like Firefox, gedit, etc. . If you try to do it for larger programs, you'll actually get an error of the following sort:

```
import: unable to read X window image `0x3200efb': Resource temporarily unavailable.
```

I think this arises from the fact that these programs actually yield multiple window IDs:

```
dill@LAMP:~$ xwininfo -tree -root | grep gedit | awk '{print $1}'
0x3000071
0x3000003
0x3000001
0x300001e

```

The script should also probably check user input in some way, and apply some sort of conditional for the case when the window name isn't valid:

```
dill@LAMP:~$ ./test.sh 
Enter the name of the window:
abc
xwininfo: error: No window with name abc exists!
import: missing an image filename `abc.jpg'.

```

So yeah, good luck! I'll try to work on the problem, too, but this should get you started. I've included all of the code below step-by-step, in case it helps:

```
sudo apt-get install imagemagick
touch window_capture.sh
```

Now open your favorite text editor and insert the following code:

```
#!/bin/sh
echo "Enter the name of the window:"
read window
window_id=`xwininfo -name $window | awk '{print $4}' | grep -i 0x`
import -window $window_id $window.jpg 
```

Now, just make sure your permissions are ok and you should be good to go...

```
chmod 755 window_capture.sh
./window_capture.sh
```

---

### Post by Dougie187 on 2008-08-18
If im not mistaken, you can simply hit Alt+PrintScreen and it will capture the active window.

---

### Post by nkri on 2008-08-18
Go to Applications>Accessories>Take Screenshot.

There should be a checkbox for "Active Window Only."

Click this, set the timer, then click OK.  It should take a shot of only the window you want.

Good luck!
-nkri

---

### Post by satman-ga on 2008-08-18
Thanks for all the help. I was having issues with trying to get the window id based on title because the the window I am interested in has a dynamic title. I could not find a way to use wildcards for the title using xwininfo.
I did find wmctrl which will generate a list of open windows. So, I used the following to get the ID.
```
sWinId=`wmctrl -l | grep <*partial_title>* | awk '{print $1}'`
```
I used this with import (thanks Dill) to get the screenshot and crop it accordingly. 
```
import -window $sWinId -crop 1390x960+5+80 <*filename*>
```
Unfortunately, I've hit another wall which I doubt can be avoided.

What I am trying to do is take a screenshot of a window periodically and then make that image my desktop background. Unfortunately, the window must be on the current workspace for this to work which defeats the purpose of what I am trying to accomplish. Perhaps there is an app available that emulates KDE's "Use program for background" function?

---

### Post by Dill on 2008-08-19
I messed around a bit more and may have addressed some of your concerns... here's the new code:

```
#!/bin/sh
echo "Enter the name of the window of which you'd like to take a screenshot:"
read window
wmctrl -a $window
window_id=`wmctrl -l | grep -i $window | awk '{print $1}'`
import -window $window_id -crop 1390x960+5+80 foo.jpg
gconftool -t string -s /desktop/gnome/background/picture_filename `pwd`/foo.jpg

```

*wmctrl -a $window* bring the focus to the window which you've named (and that's another question I had-- you said the title was dynamic, but is *part* of it static enough to where you could include it in your code. That is, instead of reading standard input, which would actually require you to do something, could you do...

```
window_id=`wmctrl -l | grep -i <window> | awk '{print $1}'`
```

I know you had something like that in your code above, but I wasn't sure if you wanted to name the window at the point at which you take the screenshot, or just plop part of the name in the code. Either way...)

I had to put the focus on the given window because of the issue you raised of different workspaces-- if the window of which you're taking a screenshot is in your current workspace, this code doesn't need to be there. *wmctrl* can get the window ID just fine and *import* can use the window ID to take the screenshot of the appropriate window.

However, if you're in workspace A and the window is in workspace B, you'll get this error, as we saw before:

```
import: unable to read X window image `0x022000d9': Resource temporarily unavailable.

```

I'm sure there's a way to fix this, so I'll keep searching.

*gconftool*, with the given parameters, sets foo.jpg as the background.

So the only hiccup I've run across is that *wmctrl* puts the focus on the screenshot window when it's doing it's work. I don't know if you're working in an environment where that shift of focus matters, but it would certainly be nice to let the script do its work in the background, eh?

If you want to do this at a given time, I bet including the script in your crontab would be the easiest way.

Hope this helps!

Cheers, 
Dylan

---

### Post by satman-ga on 2008-08-19
Thanks Dill. That all seems to work. I would prefer that it all occur in the background so that focus isn't shifted. I'll do some digging to see if there is a workaround to that.

---

