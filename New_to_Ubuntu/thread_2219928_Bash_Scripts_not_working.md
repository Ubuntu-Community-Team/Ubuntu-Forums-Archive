---
title: "Bash Scripts not working"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by sarthak2 on 2014-04-26
I tried testing a small script by running from my home area:
#!/bin/bash
cd Downloads

I made it executable by chmod +x first_script
but when I tried running it with ./first_script, it didn't run

What am I missing here???

---

### Post by papibe on 2014-04-26
Hi sarthak2. Welcome to the forum ):P

It does work, but since scripts run on a different shell (one is created to interpret the particular script), when the script ends that shell is destroyed, and you go back to the one is running interactively on the command line.

You can confirm this by adding another command at the end like 'pwd', or even a 'ls', so you can 'see' that it is actually changing directories.

There are ways to run the script in the same interactive shell the command line is running. I remember a couple:

This:
```
. ./first_script
```
or this:
```
source ./first_script
```
Hope that helps. Let us know if you have more questions.
Regards.

---

### Post by monkeybrain20122 on 2014-04-26
What do you expect it to do? the command cd Desktop works in a terminal session so running it does nothing.
```
#!/bin/bash
gnome-terminal &&
cd Downloads
```

This will open a new terminal and cd into Desktop. Instead of running it in the terminal you can just right click it and choose run. You need to set up Natilus to run script though, open Nautilus, go to Files > Prefernces > Behaviour > Executable text file and choose "ask each time" (Edit > Preferences > ... in 14.04)

---

### Post by centaurusa on 2014-04-26
> **sarthak2 said:**
> I tried testing a small script by running from my home area:
#!/bin/bash
cd Downloads


Further to the suggestion to use another command to indicate that your script has completed, I often use "read" at the end of a script (see, for example, [http://linuxnorth.wordpress.com/2012/08/23/find-ing-files/](http://linuxnorth.wordpress.com/2012/08/23/find-ing-files/)) so that it effectively pauses before completing, and an echo command to positively indicate that the script has finished.  So, you could add:

echo "Shell command complete"
read

to your script.  The message will be displayed and you can close the terminal window.

---

