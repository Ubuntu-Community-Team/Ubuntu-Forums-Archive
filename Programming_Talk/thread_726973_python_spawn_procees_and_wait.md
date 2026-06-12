---
title: "python spawn procees and wait"
date: 2008-03-17
forum: Programming Talk
---

### Post by themusicwave on 2008-03-17
Hey everyone,

I have a python question for you.

Basically I am making a script that calls lots of installers and scripts to install a system(On Windows XP....)

Anyways, the problem I am having is that some of the scripts depend on the previous one to create directories and such.  If they run before the previous installer/script finishes then they will crash.

For instance I call an installer for an application, then I call an update script for it.  The problem is the update runs in the middle of the install, causing a crash because the file it wants to update isn't there yet.

Here is my run process function.  I want it to run a new process and then wait for it to complete.  It isn't waiting...

[PHP]
#Runs a windows command specified by cmd with args does not
#return until command finishes
def runProcess(cmd,args):
    
    try:
       #Run the command
        result =os.spawnv(os.P_WAIT, cmd,args)

        #Wait a bit just to ensure it finished up
        time.sleep(25)
        return 0
    except OSError, message:
        print message
        return -1

[/PHP]

So what am I doing wrong and what should I be doing?  I though that os.P_WAIT told the script to wait until it finished running....

---

### Post by imdano on 2008-03-17
os.P_WAIT will make the program block until the command that it executed returns.  It's possible the command you're executing forks off into the background or just calls another separate process, so that it returns right away, but the execution continues elsewhere.

---

### Post by themusicwave on 2008-03-17
I was thinking the same thing...I just wanted to see if anyone else would confirm it.

Other than adding a nice long time.sleep sequence between the commands, can anyone think of another way to tell when it finishes?

The problem is this particular command needs user intervention.  So, the time it takes to complete for real depends on the user.  If the user doesn't notice this it could take them 5 minutes to click Next....

---

### Post by mssever on 2008-03-17
It seems to me that the best thing would be some kind of IPC. Have the spawned process notify its caller at the proper time--perhaps through a socket, or signals, or whatever you can dream up.

NOTE: I know absolutely nothing about programming in a Windows environment.

---

### Post by imdano on 2008-03-17
If IPC isn't an option (I'm assuming you didn't write the installer/scripts you're calling?) you could maybe try sleeping for a while, checking for some file or directory that you know is created by the installer you're waiting for, and if it doesn't exist yet, go back to sleep.  Keep doing that until you find the file/directory.  This is pretty sloppy though (can you be sure of when during the install process the file/directory is created, or the path for the file/directory?)

edit: Another possibility is that maybe the process you're calling provides the pid (maybe on stdout?) of the process it calls before it closes?  If it did, you could use that to determine if/when the process exits.

---

### Post by themusicwave on 2008-03-17
> **imdano said:**
> If IPC isn't an option (I'm assuming you didn't write the installer/scripts you're calling?) you could maybe try sleeping for a while, checking for some file or directory that you know is created by the installer you're waiting for, and if it doesn't exist yet, go back to sleep.  Keep doing that until you find the file/directory.  This is pretty sloppy though (can you be sure of when during the install process the file/directory is created, or the path for the file/directory?)

edit: Another possibility is that maybe the process you're calling provides the pid (maybe on stdout?) of the process it calls before it closes?  If it did, you could use that to determine if/when the process exits.

I did not create most of the installers or scripts I am calling.  Essentially I am gluing together a bunch of 3rd party installers.  In between installers I do configuration routines.  Had I written the installers IPC would be the way to go.

I like your idea to check for the file/directory I need before running.  This would most likely do the trick.  I was thinking about all this stuff like trying to get th pid and watch for it and stuff.  But your idea is much much simpler.  Thanks!

I think what I will do is have the update script wait until either the file is ready or it times out.  This will prevent a deadlock in case the previous step failed.

No the question is what to make the timeout...chances of a failure are low, but it should be anticipated.  Maybe a 15 minute timeout.  The install usually takes about 5 minutes.

Thanks for the good idea!

---

### Post by mssever on 2008-03-17
Just to gum up the works a bit, what happens if the phone rings right after the user starts the script, so the user doesn't see the other process' dialog until after your script times out?

Perhaps before timing out, you should prompt the user.

---

### Post by themusicwave on 2008-03-17
> **mssever said:**
> Just to gum up the works a bit, what happens if the phone rings right after the user starts the script, so the user doesn't see the other process' dialog until after your script times out?

Perhaps before timing out, you should prompt the user.

Good point,  I'll popup a tkMessagebox before I time it out.

---

