---
title: "Run script when device is attached"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by swardi19 on 2012-03-25
Hello all.  I am a beginner to Ubuntu and I have ran into a problem that I have spent days trying to find a solution to and nothing is working.  The problem that I am trying to fix is getting UDEV to run a script I have created once an external usb drive is attached.    

I have tested my UDEV rule with a sample script and it works fine as long as I redirect the output to a file...for example: echo "UDEV Test" >> results.txt
If I do not redirect the output and try to get the message to print to the screen I get nothing.  

Both methods produce the following message:

[sde] No Caching mode page present
[sde] Assuming drive cache: write through
[sde] No Caching mode page present
[sde] Assuming drive cache: write through
[sde] No Caching mode page present
[sde] Assuming drive cache: write through

At this point the Ubuntu cursor hangs up (cursor is blinking on a blank line, not reset at root@ubuntu:~#) and I am forced to hit enter or ctrl + c to return to the command line.  My theory is because the cursor never returns to the command line after this message is displayed, output cannot be displayed to the screen, thus the execution is never completed.  The redirection to a file works because all actions are taking place "behind the scenes" so to speak.

My question to you all is, how would I go about solving this problem.  Can I clear this cache message to where its never displayed to the screen?  Is there a way, in my script, to return to the command line even after this cache message is displayed?  I'm out of ideas and wanted to solve this problem myself but I am getting nowhere.  Sorry if my terminology is off, I did the best I could at describing the problem. Thanks in advance for any responses.

Stephen

---

### Post by matt_symes on 2012-03-25
Hi

I would start by posting your udev rule and your script here between code tags. 

Post them between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

> Can I clear this cache message to where its never displayed to the screen?

Pipe into /dev/null ?

> My question to you all is, how would I go about solving this problem.

Maybe it's todays hot sun (been lovely in England for a change) but i don't really understand what the problem is :D

What is the script supposed to do ? How are you calling your script ? Is udev not calling it ?

Kind regards

---

### Post by swardi19 on 2012-03-25
The udev rule I am using is
```
SUBSYSTEMS=="usb", KERNEL=="sd??", ACTION=="add", RUN+="/usr/local/bin/usb"
```My usb script consists of
```
#!/bin/sh
cd /usr/local/bin
echo "UDEV Test"
echo "UDEV Test >> udevtest
```My goal is to get "UDEV Test" to print to the screen and it will not do that because of the reasons I listed in my original post.  I added the redirection line in the script just to test my UDEV rule, which works fine.  Every time I connect a usb drive, "UDEV Test" gets written to file udevtest. 

Thanks for the response.

---

### Post by matt_symes on 2012-03-26
Hi

You can redirect the text to a tty or a pts in the /dev folder.

Kind regards

---

