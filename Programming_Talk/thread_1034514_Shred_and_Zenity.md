---
title: "Shred and Zenity"
date: 2009-01-08
forum: Programming Talk
---

### Post by purpleacid on 2009-01-08
I've just started messing around with zenity. Using nautilus-actions and a bash script, I added a context menu option for the shred command. I modified the bash script I found on gnome-look for shred_file. Here is what I have so far:
```
file="$1"
zenity --question --title="Shred" --text="Are you sure you wish to shred $file?"
if [ "$?" = 1 ] ; then
	exit $?
else
	shred -f -v -u -z "$file" | tee >(zenity --progress --pulsate)
#	Uncomment to display finish notice as well as progress bar. 
#	zenity --info --text="$file: shredding complete."
fi

```
I'm trying to modify the script in the sense that the shred command will update the progress of the zenity bar as it does each of its 26 shredding phases. Here's an example verbose output of shred on a file. 
```
shred: shred.mp3: pass 1/26 (random)...
shred: shred.mp3: pass 2/26 (492492)...
shred: shred.mp3: pass 3/26 (dddddd)...
shred: shred.mp3: pass 4/26 (333333)...
shred: shred.mp3: pass 5/26 (555555)...
shred: shred.mp3: pass 6/26 (b6db6d)...
shred: shred.mp3: pass 7/26 (111111)...
shred: shred.mp3: pass 8/26 (222222)...
shred: shred.mp3: pass 9/26 (db6db6)...
shred: shred.mp3: pass 10/26 (777777)...
shred: shred.mp3: pass 11/26 (aaaaaa)...
shred: shred.mp3: pass 12/26 (249249)...
shred: shred.mp3: pass 13/26 (random)...
shred: shred.mp3: pass 14/26 (999999)...
shred: shred.mp3: pass 15/26 (ffffff)...
shred: shred.mp3: pass 16/26 (666666)...
shred: shred.mp3: pass 17/26 (eeeeee)...
shred: shred.mp3: pass 18/26 (000000)...
shred: shred.mp3: pass 19/26 (cccccc)...
shred: shred.mp3: pass 20/26 (bbbbbb)...
shred: shred.mp3: pass 21/26 (888888)...
shred: shred.mp3: pass 22/26 (444444)...
shred: shred.mp3: pass 23/26 (6db6db)...
shred: shred.mp3: pass 24/26 (924924)...
shred: shred.mp3: pass 25/26 (random)...
shred: shred.mp3: pass 26/26 (000000)...
shred: shred.mp3: removing
shred: shred.mp3: renamed to 000000000
shred: 000000000: renamed to 00000000
shred: 00000000: renamed to 0000000
shred: 0000000: renamed to 000000
shred: 000000: renamed to 00000
shred: 00000: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: shred.mp3: removed

```
I know that the zenity progress bar updates with progress updates from some type of echo. How can I route the output of shred and transform it so that it automatically tells shred to update the progress of the bar? I would like there to be 27 progress updates, 1 for each of the wipe phases and the final 100% progress update for the file being removed. I was thinking something along to lines of using sed to transform the standard output and using an if command but my programming skills are weak, haha. Any help would be appreciated guys! :D

Side note: I'm 6 months into my ubuntu install and loving it. I was a dedicated windows user before this, taking dips into linux distros just to give it a shot. I tried fedora, the old redhat distros, mandriva, archlinux, slackware, and a few others but ubuntu was the only one that stuck. Partially because of your awesome community :D

---

### Post by dcstar on 2009-01-08
> **purpleacid said:**
> I've just started messing around with zenity. Using nautilus-actions and a bash script, I added a context menu option for the shred command. I modified the bash script I found on gnome-look for shred_file. Here is what I have so far:
```
file="$1"
zenity --question --title="Shred" --text="Are you sure you wish to shred $file?"
if [ "$?" = 1 ] ; then
	exit $?
else
	shred -f -v -u -z "$file" | tee >(zenity --progress --pulsate)
#	Uncomment to display finish notice as well as progress bar. 
#	zenity --info --text="$file: shredding complete."
fi

```
........

What about:
```
shred -f -v -u -z "$file" | zenity --text-info --title "Shred Running" --width 500 --height 250

```

---

### Post by purpleacid on 2009-01-08
I know about the text-info command, I just wanted to use progress to make it look pretty, haha. I was just wondering if it could be done, thanks for your reply. If anyone knows how/if it is possible to use zenity's progress command with shred, it would be much appreciated.

---

### Post by mssever on 2009-01-08
This thread should be in Programming Talk, where you'll be more likely to get a good answer. I've requested that it be moved.

I'm sure that what you want to do is possible, but I don't know how to do it.

---

### Post by mvaldez on 2009-06-12
You can try something like this:

```

shred -f -u -z -v "$file" 2>&1 \
| awk '{ t=substr($0,match($0,"../..")+3,2); p=substr($0,match($0,"../.."),2); p=p*(100/(1+t)); if (p>0) print p; fflush(""); }' \
| zenity --progress --title="Shredding" --text="$file" --auto-close

```

But it may not work as expected, thanks to some clever design issue in GNU coreutils (shred is part of that package).

The first part is the call to shred, but here we redirect stderr to stdout because the shred messages are printed to stderr but for our command pipe we need stdout. Then we call AWK with an inline script. That script just extract the "xx/xx" string printed by shred, extract the total steps, the current step, then convert them to a 0-100 value and then print it. Each time shred output a line, the awk script output a number. So, it converts something like:
```

shred: x.txt: paso 1/26 (random)...
shred: x.txt: paso 2/26 (666666)...
shred: x.txt: paso 3/26 (249249)...
shred: x.txt: paso 4/26 (cccccc)...
shred: x.txt: paso 5/26 (111111)...

```

to something like:

```

3.7037
7.40741
11.1111
14.8148
18.5185

```



Then, at the end of the pipe is zenity, which just stays there receiving progress numbers until the script finishes.

Anyway, the main problem is that shred uses something called output buffering, to increase performance; it won't print anything unless its output buffer is filled or if it is printing to a terminal. So, when using a pipe, it thinks "yes, no user is reading this, the status can wait", and then the AWK script won't receive anything until the shred script has finished. The result is a progress bar that stays at zero and suddenly goes to 100 when shred has finished.

For some weird reason, sometimes it works as expected in my computer, but I really can't tell why.

In another note, shred cannot do recursive shredding. If you want that. An easy way is just to call "find" command with an "exec" predicate or "exec +". I wrote a script similar to yours, that it calls itself when it is asked to delete a directory to ask confirmation for all the found files, then deletes normally the empty directories.


Anyway, good luck. Hope this helps.


Regards,

MV

---

