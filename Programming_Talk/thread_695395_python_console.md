---
title: "python console"
date: 2008-02-13
forum: Programming Talk
---

### Post by RawMustard on 2008-02-13
Is there anyway to execute another program from the python console and then have the python prompt return to do other things?

I've tried all the methods I could find in the docs and on the net. subprocess.Popen, os.system, spawn, you name it but none of the methods I've tried allow me to do this.  Perhaps I'm doing it all wrong?

A simple example would be to start mplayer /path/movie.mkv.  When I do os.system("mplayer /path/movie.mkv") I get all of mplayers output to my terminal and I don't want that :(

---

### Post by LaRoza on 2008-02-13
Can't you redirect the output to /dev/null?

---

### Post by RawMustard on 2008-02-13
All that does is remove the output, the prompt is still locked to mplayer :(

import os, subprocess as sub

os.system("mplayer /path/movie.mkv > /dev/null")
sub.Popen("/usr/bin/mplayer " + "/path/movie.mkv > /dev/null", shell=True)

I need something like os.system("mplayer /path/movie.mkv &")

There has to be a way in python to do it no?

I even tried passing it to another shell script to execute and still got mplayers output and no prompt :(

---

### Post by LaRoza on 2008-02-13
Could you try threading?

---

### Post by dwblas on 2008-02-13
You want threading.  On linux you can also run it in the background="&"
os.system("mplayer balh blah &") 
I just tried it and you may get some startup messages, but you can then continue to enter other commands on the console. > /dev/null should eliminate the messages if you don't want them.

---

