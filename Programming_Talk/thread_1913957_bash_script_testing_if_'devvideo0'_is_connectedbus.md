---
title: "bash script testing if '/dev/video0' is connected/busy"
date: 2012-01-23
forum: Programming Talk
---

### Post by SoFl W on 2012-01-23
I am trying to improve on my bash script I wrote for my webcam.  Currently the script runs fswebcam takes on picture and uses ncftpput to upload it to a server.  Cron calls the script every half hour.  
I would like to improve on the script for error handling.  I have it set so if a new image file doesn't exist it uploads an image file that says "camera offline"  That works, but I would like to check and see if /dev/video0 is available before running the script, if not upload the offline place holder picture. 
 I want to add some code to check if the camera is connected /dev/video0 and if the camera is used by another program.  
When I try searches they all seem to check if file systems are mounted but nothing for another device.
What is the correct "if [ /dev/video0' ] then" for a bash script?  Is there a way for bash to test if a device is connect and/or in use by another program?

---

### Post by sisco311 on 2012-01-24
If the webcam isn't connected, then the character device (/dev/video0) doesn't exits. You can use an if statement and the test command (or the [[ compound command) to check if the file exists and it's a character special. See:
```
help test
help [
help [[

```
and [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

```
if [ -c /dev/video0 ]; then
    printf '%s\n' "webcam connected"
fi
```

Or, you could use fuser or lsof to check if a process is using the file or not:
```
if fuser -v /dev/video0 > /dev/null 2>&1; then
    printf '%s\n' "device in use"
else
    printf '%s\n' "device available"
fi
```

But, fswebcam should also throw an error if the device is not available. So, I'd try something like:
```

if fswebcam [OPTIONS] pic.png > /dev/null 2>&1; then
    pic="pic.png"
else
    pic="camera offline.png"
fi

ncftpput [OPTIONS] "$pic" || {printf '%s\n' "$0: error - cannot upload picture"; exit 1;} 1>&2
```

---

### Post by SoFl W on 2012-01-25
Thank you.  
fswebcam does give an error but if cron runs the script I will not see it.  The script I wrote does upload an "off-line" image if the camera can not be accessed.  (busy or unplugged)
The script is called by cron and if the camera is not connect or busy there is no reason to run the rest of the script.  The script works currently but I thought maybe it could be written another way.   (all scripts could be written several ways) 

I noticed that
if fuser -v /dev/video0 > /dev/null 2>&1; then     printf '%s\n' "device in use" else     printf '%s\n' "device available" fi
will print "device available" if it is plugged in or not.  If it is in use it does print it is in use.

Looking over my scripts from yesterday I noticed my biggest problem on why the scripts were not working.  For some reason I was using "/dec/video0" instead of "/dev/video0", when I wrote a new script I didn't retype the line, I just copied and pasted the error.  No wonder it never worked.   (hangs head in shame)

Thank you for your help.  For now I will use my original script as fswebcam fails gracefully if the camera is not available.  

[FONT=monospace] [/FONT]

---

