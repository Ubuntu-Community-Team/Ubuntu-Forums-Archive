---
title: "Shell script for use with Epson scanner"
date: 2010-06-03
forum: Programming Talk
---

### Post by kaibob on 2010-06-03
I wrote the following shell script for use with my flatbed scanner. The script generally works well, but one issue remains partially unresolved.

As written, the script loops until stopped, which allows me to use the scanner's start button to scan multiple documents. However, when I am finished scanning, or after a reasonable period of time, I want the script to exit. I have researched various alternatives, and the only one that seems workable is to use the timout utility from the Lucid repository. My scanning sessions typically last 2 or 3 minutes, so I set the script to exit after 10 minutes with the following command:

```
timeout 600 scriptname
```

This works but seems a kludge, and I wondered if there is a simpler solution that does not use the timeout utility? 

I did try creating a function that ran concurrently with the main body of the script. The function contained sleep 600 and then pkill scanimage and then pkill the script. Unfortunately, scanimage continued to run even when given time to execute with an additional sleep command. 

Thanks for the help.

```
#!/bin/bash

# Set target directory.
dir="/home/kaibob/autosave"

# Check to see if script is already running.
running=$(pgrep -f "scanimage -x")
if [ -n "$running" ] ; then
  notify-send --icon=info "Scanner Status:" "   Script already running!"
  exit 1
fi

# Loop until stopped
while true ; do

  # Set target file name. 
  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  # Scan document to temporary file in PNM format.
  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > /tmp/$$.pnm 

  # Convert PNM file to PDF file with Graphicsmagick. 
  if [ -f "/tmp/$$.pnm" ] ; then
    gm convert /tmp/$$.pnm "${dir}/${file}"
  else
    notify-send --icon=info "Scanner Status:" "   Document not created!"
    exit 1
  fi

done
```

---

### Post by jobix on 2010-06-04
How about adding a check something along these lines:

Inside the while loop, the file is scanned. Save this file to a temp file. Next time around in the while loop, another file is scanned. Now compare this file with the temp file from the earlier iteration. If they are equal, that means there's nothing more to be scanned. I can see this fail if there is too much time lapsed between scanning.

---

### Post by soltanis on 2010-06-04
Well, how I know it is python:

```

#!/usr/bin/env python
import subprocess, time
proc = subprocess.Popen(['/path/to/script'])
time.sleep(600)
if proc.poll() is None:
  proc.terminate()

```

/path/to/script needs to be an absolute path, that's the only drawback of using subprocess.

EDIT: and your script needs to be chmodded to be executable, and it needs a proper #! line in the header.

---

### Post by BoneKracker on 2010-06-04
misguided, hapless attempt deleted

see below

---

### Post by BoneKracker on 2010-06-04
A working, but inelegant solution deleted.

Edit: see below

---

### Post by BoneKracker on 2010-06-04
Okay, this is inspired by soltanis:

```
#!/bin/bash

[B]# how long to run (seconds)     TODO: make this a command-line option?
timeout=600[/B]

# Set target directory.
dir="/home/kaibob/autosave"

# Check to see if script is already running.
running=$(pgrep -f "scanimage -x")
if [ -n "$running" ] ; then
  notify-send --icon=info "Scanner Status:" "   Script already running!"
  exit 1
fi

[B]# subshell that sleeps for $timeout seconds
sleep $timeout &[/B]

**# Keep looping as long as subshell is alive**
while **$(ps -p  $! >/dev/null)**; do

  # Set target file name. 
  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  # Scan document to temporary file in PNM format.
  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > /tmp/$$.pnm 

  # Convert PNM file to PDF file with Graphicsmagick. 
  if [ -f "/tmp/$$.pnm" ] ; then
    gm convert /tmp/$$.pnm "${dir}/${file}"
  else
    notify-send --icon=info "Scanner Status:" "   Document not created!"
    exit 1
  fi

done
```

---

### Post by kaibob on 2010-06-04
Thanks BoneKracker for the reply. I tried your suggested script and it did work, but not in a usable manner. What happens is that the script stops at the scanimage line waiting for me to press the scanner's start button. So, if I run the script, scan documents for say 2 minutes, and do nothing else, then the script never sees the while test and continues to run forever. If I instead wait 30 minutes and do a scan, then the script does the scan, sees the while test, and exits. 

I tried your earlier suggestion of putting the scan code in a function. Just for testing I used the following abbreviated script. This actually worked quite well, except that scanimage continued to run. I added a line to explicitly kill scanimage but that didn't work either (when run in a terminal window the output is "scanimage: received signal 15 ; scanimage: trying to stop scanner"). I suspect this has something to do with the scanner's interaction with the computer, which is beyond my knowledge level, but I'm going to spend some more time on this tomorrow. 

Thanks again for the help. I really appreciate it. 

```
#!/bin/bash

cd /home/kaibob/temp

scan () 
{ 
while true ; do

  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > xxx.pnm 

    gm convert xxx.pnm "${file}"

done
}

scan &
sleep 600
exit 0
```

---

### Post by ja660k on 2010-06-04
what about cron?
make your script run every 5 seconds?, 5 minutes?, 5 hours?

---

### Post by kaibob on 2010-06-04
> **soltanis said:**
> Well, how I know it is python:

```

#!/usr/bin/env python
import subprocess, time
proc = subprocess.Popen(['/path/to/script'])
time.sleep(600)
if proc.poll() is None:
  proc.terminate()

```

/path/to/script needs to be an absolute path, that's the only drawback of using subprocess.

EDIT: and your script needs to be chmodded to be executable, and it needs a proper #! line in the header.
Thanks soltanis for the reply. Your python script killed the shell script as desired, but it left scanimage running. I know nothing about python--is there a way to kill scanimage from within the python script as well? Thanks again.

---

### Post by saulgoode on 2010-06-04
It's been a while since I've had to do somesuch as this, but I think the following is correct:

```
#!/usr/bin/expect
set timeout 600
spawn scanimage
spawn scriptname
expect
```

---

### Post by geirha on 2010-06-04
Have a look at [http://mywiki.wooledge.org/BashFAQ/068](http://mywiki.wooledge.org/BashFAQ/068)

---

### Post by kaibob on 2010-06-04
> **geirha said:**
> Have a look at [http://mywiki.wooledge.org/BashFAQ/068](http://mywiki.wooledge.org/BashFAQ/068)

Thanks for the link geirha. I've strung together some bits from this article:

> FIRST check whether the command you're running can't be told to timeout directly. The methods described here are "hacky" workarounds to force a command to terminate after a certain time has elapsed.... That said, there are two C programs that can do this: doalarm, and timeout.... If you can't or won't install one of these programs (which really should have been included with the basic core Unix utilities 30 years ago!), then the best you can do is an ugly hack like:...

The problem I could never resolve is getting scanimage to quit, and it doesn't have any option to timeout directly. My original script and scanimage both quit with the timeout command, so I guess I should be happy with that.

Thanks everyone for the responses. I greatly appreciate your help.

---

### Post by BoneKracker on 2010-06-04
> **kaibob said:**
> Thanks BoneKracker for the reply. I tried your suggested script and it did work, but not in a usable manner. What happens is that the script stops at the scanimage line waiting for me to press the scanner's start button. So, if I run the script, scan documents for say 2 minutes, and do nothing else, then the script never sees the while test and continues to run forever. If I instead wait 30 minutes and do a scan, then the script does the scan, sees the while test, and exits. 

I tried your earlier suggestion of putting the scan code in a function. Just for testing I used the following abbreviated script. This actually worked quite well, except that scanimage continued to run. I added a line to explicitly kill scanimage but that didn't work either (when run in a terminal window the output is "scanimage: received signal 15 ; scanimage: trying to stop scanner"). I suspect this has something to do with the scanner's interaction with the computer, which is beyond my knowledge level, but I'm going to spend some more time on this tomorrow. 

Thanks again for the help. I really appreciate it. 

```
#!/bin/bash

cd /home/kaibob/temp

scan () 
{ 
while true ; do

  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > xxx.pnm 

    gm convert xxx.pnm "${file}"

done
}

scan &
sleep 600
exit 0
```

That's a good refinement. (Of my "inelegant but working solution" :lol:).  I should have realized the final one (the one I didn't delete above) one wouldn't work -- I keep falling into the same trap of waiting for the button.  It's clear that the best solution puts the scanning in the subshell and the timing in the parent.  I think one alternative would be to use the new 'coproc' capability, but that it would be overkill.  Expect would work, but I think it's unnecessarily inefficient.  Try this first; how about this adaptation, which I think would employ sigkill instead of the default sigterm passed to the subshell.

```
#!/bin/bash

cd /home/kaibob/temp

scan () 
{ 
while true ; do

  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > xxx.pnm 

    gm convert xxx.pnm "${file}"

done
}

scan &
sleep 600[B]
kill -9 $![/B]
exit 0
```

---

### Post by kaibob on 2010-06-04
I tried the new version, and it did not even attempt to kill scanimage. I checked and found that $! was returning the PID of the shell script. I fixed that and found that the script did kill the existing scanimage process and that an entirely new scanimage process with a different PID was created. I don't know why this same behavior does not happen with the timeout command--perhaps it is because (as stated in the man page) the timeout command "is run in a separate POSIX process group so that the right thing happens with commands that spawn child processes."

So, I ended up where I started with this project, but I did learn quite a bit, which is always good. Many thanks.

---

### Post by BoneKracker on 2010-06-04
I think we can make it work by putting a 'trap' inside the subprocess loop. I'll get back to you.

---

### Post by lavinog on 2010-06-04
Why not use a time stamp and loop until time-timestamp > timeout time

Just curious, are you wanting to minimize the size of the scanned image?

---

### Post by kaibob on 2010-06-04
> **BoneKracker said:**
> I think we can make it work by putting a 'trap' inside the subprocess loop. I'll get back to you.
I think we might actually have a solution for this. After a little additional thought on your previous suggestion, and what it did, I modified the script to first kill the function and then kill scanimage. I have to do some more testing, but so far it seems to work fine. I'll let you know. 

```
#!/bin/bash

cd /home/kaibob/temp

scan () 
{ 
while true ; do

  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > xxx.pnm 

    gm convert xxx.pnm "${file}"

done
}

scan &
sleep 600
kill -9 $!
pkill -9 -f "scanimage"
exit 0
```

---

### Post by kaibob on 2010-06-04
> **lavinog said:**
> Why not use a time stamp and loop until time-timestamp > timeout time

Just curious, are you wanting to minimize the size of the scanned image?

The script loops and then stops at the scanimage command and, at that point, waits for me to press the start button on the scanner. So, if I scan for say 2 minutes and the timeout is 5 minutes, the script never times out.

---

### Post by lavinog on 2010-06-04
> **kaibob said:**
> The script loops and then stops at the scanimage command and, at that point, waits for me to press the start button on the scanner. So, if I scan for say 2 minutes and the timeout is 5 minutes, the script never times out.

Sorry, didn't see the wait for button command...I haven't tried that yet.

---

### Post by lavinog on 2010-06-04
```
#!/bin/bash

cd /home/kaibob/temp

scan () 
{ 
while true ; do

  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > xxx.pnm 

    

    gm convert xxx.pnm "${file}"


done
}

timeout=5
scan &
scanpid=$!

# loop multiple times while scanning occurs.
while true
do
 sleep 10

# count how many files have been created within the timeout time
# if the count is zero kill the scan function 
[[ "$(find -iname 'Scan*.pdf' -mmin -${timeout}|wc -l)" -eq "0" ]]&&{

 kill -9 $scanpid

 exit 0
}

done

```

---

### Post by BoneKracker on 2010-06-04
If you haven't completely given up on this, here's one last try at this without resorting to extra processes.  Unfortunately, I can't really test this stuff without hooking up a scanner.

This is like one I had deleted, with the scanning going on in the foreground and the timout elapsing in the background.  Like that example, the foreground loop continues as long as the background process is alive.

It seems like the main problem is that scanimage (with "wait for button") is not terminating when its parent process terminates.  So the difference here is that, before the timeout subprocess exits it will destroy the scanimage command's subprocess directly (with a ruthless 'SIGKILL').  I've also inserted a 1-second delay in the main loop, between scans, to prevent the main loop from issuing another scanimage command if the timeout subprocess just hasn't quite fully exited yet.  You may find that not to be necessary.

Ultimately, you'd want timeout to be a command-line option, which would be passed to the timeout function as a parameter.

```
#!/bin/bash

cd /home/kaibob/temp

function scan {

  file="Scan $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

  scanimage \
    -x 215.9 \
    -y 279.4 \
    --format=pnm \
    --mode Binary \
    --resolution 300 \
    --threshold 160 \
    --wait-for-button=yes \
    > xxx.pnm 

    gm convert xxx.pnm "${file}"

}

# timoute function aggressively kills scanimage before exiting
function timeout {
    sleep 600
    pkill -9 scanimage
}


# run timeout function in parallel in a subshell
timeout &
timeout_pid=$!

# keep looping as long as subshell is alive
while $(ps -p $timeout_pid >/dev/null); do

    scan
    sleep 1  # give subshell time to exit (may not be needed)

done
```

---

### Post by BoneKracker on 2010-06-04
> **lavinog said:**
> Sorry, didn't see the wait for button command...I haven't tried that yet.

Yeah.  Wait for button is the essence of the problem here.

---

### Post by BoneKracker on 2010-06-04
> **kaibob said:**
> The script loops and then stops at the scanimage command and, at that point, waits for me to press the start button on the scanner. So, if I scan for say 2 minutes and the timeout is 5 minutes, the script never times out.

This is funny.  You and I had some of the same ideas at the same time.  The last one I posted above was done in parallel with your last effort.  I think it might be slightly different, though, and might be worth a try.

---

### Post by lavinog on 2010-06-04
The code I posted uses:
```
[[ "$(find -iname 'Scan*.pdf' -mmin -${timeout}|wc -l)" -eq "0" ]]&&{
```
to determine if any activity has occured.

Using sleep 600 will cause the scanning to stop after 5 mins even if the user is still scanning.

---

### Post by lavinog on 2010-06-04
Ignore this, I wasn't thinking straight

---

### Post by BoneKracker on 2010-06-04
> **lavinog said:**
> The code I posted uses:
```
[[ "$(find -iname 'Scan*.pdf' -mmin -${timeout}|wc -l)" -eq "0" ]]&&{
```
to determine if any activity has occured.

Using sleep 600 will cause the scanning to stop after 5 mins even if the user is still scanning.

I like that idea better.  It's a bit different than the requirement he specified, but it makes sense.

However, at this point, I'm more interested in why we can't make what we were trying to do work.  I think what's been happening to him is that the 'scanimage' command (with the "wait for button" option) isn't terminating when it's parent process terminates.  Have you actually tested your script with scanimage, and is it able to terminate scanimage when it's waiting like that?

---

### Post by BoneKracker on 2010-06-04
> **lavinog said:**
> also I think this is an issue:
```

scan &
sleep 600
kill -9 $!

```
you are killing sleep not scan
you should assign $! to a variable then kill using that variable:

```

scan &
scanpid=$!
sleep 600
kill -9 $scanpid

```

Is that also the case in the last one I posted, which hasn't been tested (because there's now a "sleep 1" in the main loop?

I've make your suggested change, in case it is, assigning the pid immediately to a variable, and not using $! in the loop itself.

---

### Post by lavinog on 2010-06-04
> **BoneKracker said:**
> I like that idea better.  It's a bit different than the requirement he specified, but it makes sense.

However, at this point, I'm more interested in why we can't make what we were trying to do work.  I think what's been happening to him is that the 'scanimage' command (with the "wait for button" option) isn't terminating when it's parent process terminates.  Have you actually tested your script with scanimage, and is it able to terminate scanimage when it's waiting like that?

I see.  I don't have a scanner attached to this computer, but I replaced scanimage with sleep 9000 to simulate the same effect.
It looks like killing the function will not kill the child processes.

you could put scanimage in the background, store the pid in a temp file (like a callback) then issue a wait command inside the function.

Outside function you can use the temp pid file to kill the scanimage process.

Another way to go about this is to use another script file that does the scan loop, while the main script controls that script file...killing the scan script should kill the child processes.

---

### Post by kaibob on 2010-06-05
BoneKracker,

I have done some additional testing on the new script in my most recent post, and it works fine. I know you have spent significant time on this, and I wouldn't have gotten it working without your help. I am most appreciative.

Just for the sake of completeness, I have included the final version of the script below.

kaibob

```
#!/bin/sh

# Dash shell script.
# Scan lineart documents at 300 dpi.
# For use with Epson Perfection V30 scanner.

## SETTINGS ##

# Scanner ID as shown by lsusb utility.
device=04b8:0131

# Temp directory.
tempdir=/tmp/kscan

# Output directory.
outdir=/home/kaibob/autosave

# Timeout in seconds.
time=900

# Scanner threshold.
thresh=160

# Scan length in millimeters (297.18 mm maximum).
length=279.40

## FUNCTION ##

# Scan function.
scan () {

  # Loop until terminated.
  while true ; do

    # Scan document to temporary PNM file. 
    scanimage \
      -d epkowa \
      -x 215.9 \
      -y ${length} \
      --format=pnm \
      --mode Binary \
      --resolution 300 \
      --threshold ${thresh} \
      --wait-for-button=yes \
      > ${tempdir}/scan.pnm

    # Reset start file.
    > ${tempdir}/scan.start

    # Set output file name.
    file="Scan on $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

    # Convert PNM file to PDF file with graphicsmagick.
    gm convert ${tempdir}/scan.pnm "${outdir}/${file}"

  done
}

## MAIN ##

# Check scanner. 
if ! lsusb -d ${device} > /dev/null ; then
  notify-send --icon=error "Scanner Status:" "   Scanner not responding!"
  exit 1
fi

# Check script lock and create or reset start file for timout calculation.
if mkdir ${tempdir} 2> /dev/null ; then
  > ${tempdir}/scan.start
  notify-send --icon=info "Scanner Status:" "   Scanner starting!"
else
  > ${tempdir}/scan.start
  notify-send --icon=info \
    "Scanner Status:" "   Timeout reset to $((time / 60)) minutes!"
  exit 0
fi

# Call scan function.
scan &

# Timeout period.
until [ "$(date +%s)" -gt "$(($(date -r ${tempdir}/scan.start +%s) + ${time}))" ] ; do
  sleep 45
done

# Check for scanning activity before exit.
while [ -s /tmp/kscan/scan.pnm ] ; do
  sleep 45
done

# Kill scan function.
kill $!

# Kill scanimage program.
pkill scanimage
pkill -INT scanimage

# Notify of shell script exit.
notify-send --icon=info "Scanner Status:" "   Scanner closing!"

# Remove temporary directory.
rm -rf ${tempdir}

# End.
exit 0
```

---

### Post by BoneKracker on 2010-06-05
> **lavinog said:**
> I see.  I don't have a scanner attached to this computer, but I replaced scanimage with sleep 9000 to simulate the same effect.
It looks like killing the function will not kill the child processes.

you could put scanimage in the background, store the pid in a temp file (like a callback) then issue a wait command inside the function.

Outside function you can use the temp pid file to kill the scanimage process.

Another way to go about this is to use another script file that does the scan loop, while the main script controls that script file...killing the scan script should kill the child processes.

The problem seems to be that the scanimage command (with "wait for button") creates a sub-process that does not seem die normally.  Sigterm should kill it, but it doesn't happen.  That's based on his feedback from testing, and I can't confirm this myself, so I may be wrong about that conclusion.

So my last code was intended to explicitly terminate both both the scanimage command (with a kill -9) and then the loop.  But I haven't heard yet whether it's working or not.

It might be best to create a little test script that does nothing but issue the scanimage command (with the "wait for button"), then send the scanimage subprocess various signals to see what happens.  There are no signals documented in its man page.

At a minimum it ought to die when receiving SIGTERM (and, of course, SIGKILL).  If it SIGTERM works, then what I'm saying above is all barking up the wrong tree (and we should be able to terminate it normally in one fashion or another).

---

### Post by BoneKracker on 2010-06-05
> **kaibob said:**
> BoneKracker,

I have done some additional testing on the new script in my most recent post, and it works fine. I have run the script from a terminal window, and no errors are reported. I have also checked running processes with the ps command after the script times out to verify that the script and scanimage terminate properly. They do.

Excellent.  I'm glad it's working.

You and I simultaneously pursued the idea of explicitly terminating the scanimage command as well as the loop.  Mine is just a different approach to that.

Congratulations, and I'm glad we didn't have to give up. :)

---

### Post by kaibob on 2010-06-05
> **lavinog said:**
> The code I posted uses:
```
[[ "$(find -iname 'Scan*.pdf' -mmin -${timeout}|wc -l)" -eq "0" ]]&&{
```
to determine if any activity has occured.

Using sleep 600 will cause the scanning to stop after 5 mins even if the user is still scanning.
lavinog,

Thank you for your replies. I was so close to a solution that I concentrated on that and haven't had time to closely look at your suggestion. I am going to do that tomorrow.

The one significant flaw in my final script is that it mindlessly times out after a set period of time. A much better approach, as you suggest, is to time out a set number of minutes after the last scan is performed. Now that I have a working script, I should be able to adapt your suggested approach to my script. I use my scanner extensively, so this will be worthwhile. 

Thanks again. 

kaibob

---

### Post by kaibob on 2010-06-05
BoneKracker,

I tried your shell script in post 21, and it worked fine. I did a few test scans without issue, and the shell script and scanimage both terminated after the timeout period. Good work. 

I added a few enhancements to my script, including the modified timeout suggested by lavinog, and I have replaced my earlier script in post 29. As written, it will only work with an Epson V30 scanner, but it could be modified to work with some other scanners. 

Thanks again for the help. It's nice to have this one finished. 

kaibob

---

### Post by BoneKracker on 2010-06-05
Thanks for testing mine; I wondered if it worked.

Now, what you really should do is generalize the script:

a) take timeout variable as a command-line option
b) support use of other scanners (or at least put the "hooks" in to be able to do so)

Then "publish" the script somewhere more "findable", like in a "tips and howtos" portion of the Ubuntu or other linux forums you participate in, your blog if you have one, or elsewhere such that people can find it.

This is low-level, grass-roots "open source" sharing, but it's frequently helpful to people.  Not that I'm even a "good" programmer or scripter, but [something I did like that once]("http://forums.gentoo.org/viewtopic-t-687956-highlight-singlepacket.html?sid=60b58f3f6d725c7d778d16d6482096d8") was used by a number of people until the ideas were eventually picked up and incorporated into a packaged product.

---

### Post by kaibob on 2010-06-07
BoneKracker,

I have been working to enhance and optimize my script, and I have included the final version in post 29. After a bit of testing, I will see if I am able to write up a how-to for the Tutorial & Tips forum. 

I was motivated to write this script because the existing scanner packages--including Image Scan, Xsane, and Simple Scan--either would not do what I wanted or required an inordinately large number of mouse clicks and setting changes before every scan. I suspect most people want a GUI, but I'm sure a few would be helped by a script such as mine. 

Thanks again.

kaibob

~~~~~~

EDIT: June 4, 2011

I wrote a new version of this shell script and wanted to include it in the unlikely event that an Epson scanner user happened upon this thread. The script is self explanatory. The user does have to change the scanner ID, which is obtained by entering lsusb in a terminal window. 


```
#!/bin/bash

# TYPE:      Shell script.
# PURPOSE:   Scan lineart documents on Epson scanner.
# REQUIRES:  Bash 4.0, scanimage and imagemagick. 
# REVISED:   06.04.11.

## FUNCTION ##

# Start kscan function.
kscan () { 

# Set default scan values.
thresh=150
width=8.5
length=11.0

# Set output directory.
outdir=~/

# Set temporary file name.
tempfile=/tmp/kscan.$RANDOM.pnm

# Set counter.
count=1

# Set scanner ID as shown by lsusb utility.
device=04b8:0131

# Check scanner is ready. 
if ! lsusb -d ${device} > /dev/null ; then
  printf "%s\n\n" "SCAN MENU"
  printf "%s\n\n" "Scanner not responding!"
  read -n 1
  exit 1
fi

# Trap scanimage program and temp file on exit.
trap "pkill scanimage
      pkill -INT scanimage
      scanimage -d epkowa --dont-scan
      rm -f "${tempfile}"
      exit 0" EXIT

# Start menu loop.
while true ; do

# Menu header.
printf "%s\n\n" "SCAN MENU"
printf "%s\n" "1) threshold (${thresh})" "2) width (${width} inches)" \
              "3) length (${length} inches)"
printf "\n%s" "Enter # or other key to scan: "
read keypress

# Menu case statement. 
case "$keypress" in
  1 )
    printf "\n%s" "Threshold (100..150..200): "
    read thresh1
    thresh=${thresh1:-${thresh}}
    clear
    continue 1 
  ;;
  2 )
    printf "\n%s" "Width in inches to 8.5: " 
    read width1
    width="${width1:-${width}}"
    clear
    continue 1 
  ;;
  3 )
    printf "\n%s" "Length in inches to 11.7: " 
    read length1
    length="${length1:-${length}}"
    clear
    continue 1 
  ;;
  * ) 
    xx=$(awk 'BEGIN {printf "%.2f", '"${width}"'*25.4}')
    yy=$(awk 'BEGIN {printf "%.2f", '"${length}"'*25.4}')
    printf "\n%s\n\n" "Scanner ready!"
    break 1 
  ;;
esac

# End menu loop.
done

# Start scan loop.
while true ; do

# Scan document to temporary file. 
scanimage \
  -d epkowa \
  -x ${xx} \
  -y ${yy} \
  --mode Binary \
  --resolution 300 \
  --threshold ${thresh} \
  --format=pnm \
  --wait-for-button=yes \
  > "${tempfile}" 2> /dev/null

# Report scanimage error.
if (("$?" != 0)) ; then
  printf "%s\n" "Scanimage error!"
  read -n 1
  exit 1
fi

# Set output file name.
file="Scan on $(date +%m.%d.%y) at $(date +%H.%M.%S).pdf"

# Convert temporary file to PDF file.
convert "${tempfile}" "${outdir}/${file}" 2> /dev/null

# Report imagemagick error.
if (("$?" != 0)) ; then
  printf "%s\n" "Imagemagick error!"
  read -n 1
  exit 1
fi

# Report scan completed.
printf "%s\n" "${count}) Scan completed at $(date +%r)"
((count++))

# End scan loop.
done

# End kscan function.
}

## MAIN ##

# Kill kscan function if running.
pkill -f "bash -c kscan"

# Export function.
export -f kscan

# Run kscan function.
gnome-terminal --geometry=36x16+10+40 -t "Epson Scan" -x bash -c "kscan"

```

---

### Post by bapoumba on 2010-06-12
Thread Title edited, kaibob :)

---

