---
title: "[Python] Open a new terminal window"
date: 2009-10-01
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-01
Hey,

Ive been looking at the os modules, like execv and execl and system and popen, etc... but they weren't working like id want.

I'm basically building a "startup script"; which is something that when the computer is turned on this script is run, and will run other (separate) scripts from it. So heres how it would work:

###
os.open_my_process('"C:\windows\system32\cmd.exe" /K C:/Startup/MyScript1.py')
os.open_my_process('"C:\windows\system32\cmd.exe" /K C:/Startup/MyScript2.py')
os.open_my_process('"C:\windows\system32\cmd.exe" /K C:/Startup/MyScript3.py')
###

(Sorry for the windows process' i forget the path of the linux terminal xP)

After my script had run the "startup script" would close and MyScript[1-3].py would continue to run.

Thanks
~Cody Woolaver

---

### Post by j7%&lt;RmUg on 2009-10-01
Im a little confused, do you need help with the code, or do you need to know how to run one script from inside another?

---

### Post by Pyro.699 on 2009-10-01
I need to know how to run one script from within another, but in a seperate process. Not new thread, but an entirely new process window.

So with the example in the first post it would open 3 terminals, and in terminal 1, myscript1.py would be running, in terminal 2 myscript2.py, would be running and so on.

Thanks

---

### Post by j7%&lt;RmUg on 2009-10-01
Ok well can you post your code please.

---

### Post by Pyro.699 on 2009-10-01
There isnt any code yet ^^ its only going to be a 3 or 4 lined file, i dont know the proper code to use to open up a new window/process.

---

### Post by j7%&lt;RmUg on 2009-10-01
Well for what you want i can tell you right now its going to be atleast 10 lines.

EDIT: Why dont you just run multiple scripts at startup?

---

### Post by days_of_ruin on 2009-10-01
```
import subprocess

pid = subprocess.Popen(args=[
    "gnome-terminal", "--command=python test.py"]).pid
print pid   
```

Replace test.py with whatever python script you want.
Of course just repeat this for as many different scripts you 
want to run.

Just curious, why do you want these to be running in a terminal?

---

### Post by kumoshk on 2009-10-02
Hmm, it sounds to me like you want to know how to open a separate process from the terminal, and not necessarily from pure Python-code.

Here's an example of something like what I think you want in Linux:
gnome-terminal -e 'bash -c "./FileName; sleep 999999999d"'

Anyway, that'll open up a new gnome-terminal (even if you're in a gnome-terminal) and execute FileName and then it'll sleep (pause) for about a billion days. This new gnome-terminal will close by itself after all processes complete (so if you need to see the output, the sleep command might be useful).

If you're not familiar with Linux, you might want to know the following:
&#8226; ./fileName will execute fileName (provided it has correct permissions)
&#8226; A semicolon can be used to add additional commands to one line
&#8226; bash -c invokes BASH (a shell) to execute your commands

To open a new process from the command-line in Windows, just prepend the 'start' command to whatever you want to run: i.e. start python fileName.py (although I don't think this will open a terminal window for you).

With this knowledge you can just execute those terminal commands from Python (although they are OS-specific; I don't know what to tell you for Macintosh, but I imagine it's similar to Linux).

Does this help at all?

---

