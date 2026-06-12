---
title: "Problem with Using Python Subprocess in Windows"
date: 2009-08-28
forum: Programming Talk
---

### Post by mcland on 2009-08-28
Hi,

I'm trying to run a program in Windows with the subprocess.Popen function.  This for a testing script at work so the program may or may not complete successfully.  If it does not complete sucessfully a dialog box pops up with the error and a button to click ok.  This program needs to be hands off so I don't want to have to get up and click enter (plus it will make the program output wrong).  

What I'm trying to do is have a timer and then terminate my program at the end.  However, python wants to make my program run to completion before it calls the timer.  Is there any way around this?  Here's the basics of what my code looks like:
 
[php]
import subprocess, time

def runFile(self, fileName, runOptions):
    command=fileName+ " " + runOptions

    process=subprocess.Popen(command, stdin=subprocess.PIPE,  stdout=subprocess.PIPE)

    time.sleep(1800) #sleep for 30 minutes
    p.communicate()

    #check to see if program completes
    if p.returncode==NONE:
        p.terminate()
        complete=0
    else:
        complete=1
[/php]

I know this is sort of an obscure problem, but suggestions on the matter would be greatly appreciated.

---

