---
title: "Run Startup App after resuming from Suspend"
date: 2014-09-03
forum: New to Ubuntu
---

### Post by matt136 on 2014-09-03
Hello,

I am brand new to Ubuntu, and Linux in general.  I have been fair successful with searching online for how to do just about anything that i want to do, and most of that info has been found on this forum.  

I have come to a point that I am unable to accomplish what I am wanting to do just by searching the threads.  This started because my "two finger scroll" option in mouse/touchpad settings was disabled/greyed out.  I found a very helpful thread on how to manually enable it at [http://ubuntuforums.org/showthread.php?t=1559479](http://ubuntuforums.org/showthread.php?t=1559479)

So, i followed the directions on that post and i was able to make a text file that i named "TFS.run" (two finger scroll), and then i added it to my startup apps.  It works perfectly.  The only problem is if the computer gets suspended or even just logs me out due to inactivity, it disables it, and i have to manually run the lines through terminal to make them apply again.

I have found 2-3 different threads on how make a startup app run after wake up from suspend, but i can't figure it out.  I have my TFS.run file stored right in the home folder, if that would help to assist me in this.

Any help would be awesome!

Thanks,
Matt

---

### Post by Howl7 on 2014-09-03
Hi Matt, 

Scripts in the directory /etc/pm/sleep.d are run when the machine suspends and wakes up. If you place your code from this TFS.run file here with the proper formatting it should run when you come back from a suspend and fix at least part of your problem. Open up the text editor and copy this in:

```
#!/bin/bash
case $1 in
resume|thaw)
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient EmulateTwoFingerMinW=5
synclient EmulateTwoFingerMinZ=48
;;
esac

```
(I got the synclient commands from the thread you referenced.)

Save this as /etc/pm/sleep.d/05_TFS and run 
```
chmod +x /etc/pm/sleep.d/05_TFS
```
from the terminal to make it executable.

Now the commands you have to keep entering manually should run automatically. I hope this works for you.

---

### Post by matt136 on 2014-09-04
Hey Howl7

I'm definitely tracking with what you are saying to  do.  However, when i attempt to save the file as /etc/pm/sleep.d/05_TFS  it tells me that i do not have the permissions necessary to save the  file and to check that i typed the location correctly (I even browsed to  the location to make sure).  I tried to manually move the file  from the home location to the etc/pm/sleep.d location using: ```
sudo mv 05_TFS /etc/pm/sleep.d
``` 
Then i ran it, as you said, using: ```
chmod +x /etc/pm/sleep.d/05_TFS
```
Unfortunately, that didn't do it.  I still have to manually run the commands.  Obviously the only difference is how the file actually got placed in the sleep.d folder.

Any thoughts?

---

### Post by ThatBum on 2014-09-04
Edit the file at the location, [FONT=courier new]sudo gedit /etc/pm/sleep.d/05_TFS[/FONT][FONT=courier new] [/FONT]or whatever your text editor is.
[FONT=courier new][/FONT]Also the chmod needs sudo too since it's outside your home directory.

---

### Post by matt136 on 2014-09-04
Hmm, i still can't get this to work.  Not sure what i'm doing wrong here.  And to make matters more interesting, my original startup app is no longer running at original boot.  I'm not entirely sure at what point that actually stopped working though...  the original file is still in the same location and still in my startup apps.

---

### Post by matt136 on 2014-09-05
Ok,

I got the startup app working again, but I am still unable to get it to run after resuming from sleep.  Oh, and I looked at the suspend logs using ```
cat /var/log/pm-suspend.log
``` and 05_TFS is nowhere to be seen in the logs, as if it isn't running.  Any other thoughts?

Matt

---

### Post by Howl7 on 2014-09-06
Alright, 

I did some playing around with this on my machine and discovered the flaw. 05_TFS needs to be owned by root in order to run. To make this happen, open a terminal and do:
```
sudo chown root:root /etc/pm/sleep.d/05_TFS
```
It should work now.

---

### Post by matt136 on 2014-09-14
Somehow that kinda messed things up for me.  it definitely didn't do the trick, and it caused an issue with the appearance of my system.  Not really sure.  I was able to resolve that, but i think i am going ot give up on this for the time, unless anyone has any other suggestions.  edge scrolling works just fine... i just like the ability to scroll diagonally with two finger scroll.  

anyways... thanks for all the input!

---

