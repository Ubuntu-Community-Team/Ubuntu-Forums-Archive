---
title: "[python] Subprocess.Popen(firefox) leaves an Orphan process"
date: 2010-10-05
forum: Programming Talk
---

### Post by pokerbirch on 2010-10-05
I have a Python script that does some process management. All is working fine except for when it launches Firefox. We can normally launch a process as none-blocking and then terminate() it when we are finished, however with FF, the parent process terminates as expected but leaves the main FF window open. I am assuming that the parent is a launch script and the FF window is a child process? Even when my Python script exits, the FF instance remains. To reproduce this:[PHP]from subprocess import Popen

url = 'http://google.com'
cmd = ['firefox', '-no-remote', '-P', 'default', url]
proc = Popen(cmd)
sleep(10)
proc.terminate()
print 'terminated??'
[/PHP]It appears that our Popen launches the script at /usr/bin/firefox.sh which in turn opens the binary at /usr/lib/firefox-3.6.10/firefox-bin (on my system). I've tried launching firefox-bin directly but it throws an error and becomes a Zombie in my process list. The only successful kludge so far is to launch FF via a Popen'd xterm and then .terminate() the xterm when done. Downsides are that
a) FF thinks it has crashed and always starts up with the "restore session" error page (can be disabled in about:config but I want to avoid special settings)
b) all output goes to the xterm rather than my python instance
c) the xterm is visible

There is very likely a simple solution to all this, however my brain has gone a bit fuzzy from all the Googling and document reading.

---

### Post by rnerwein on 2010-10-06
hi 
i'am a C-programmer and i'm not sure if it that same "situation" in phyton.
i saw this very often.
i think your problem is -> you ain't call pclose ( pclose is in C but i think it is the same in phyton).
with pclose you w'll get the return code of the child processes. 
this will get you rid of your zombie processes and you can ask for if the command was successful or not.
ciao

---

### Post by StephenF on 2010-10-06
The trouble here as I see it revolves around the fact that Firefox runs as a single process on any given X screen so if you had Firefox already running before you called subprocess.Popen you would just be asking for an extra Firefox window or tab, not a new process.

Try running more than one Firefox profile on a single X screen or the same profile on two and it will just refuse.

My advice would be to use a different browser or better yet try embedding a browser pane in your app.

---

