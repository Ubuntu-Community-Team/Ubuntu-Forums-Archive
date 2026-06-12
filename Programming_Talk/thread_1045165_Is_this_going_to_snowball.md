---
title: "Is this going to snowball?"
date: 2009-01-20
forum: Programming Talk
---

### Post by Dirjel on 2009-01-20
I wrote a bash script (my first ever) so that when I run Cave Story (doukutsu) it automatically turns on rejoystick so I can use my PS3 controller to play.  I wanted to change it a bit, though, so that it would disable my screensaver while doukutsu is running.  However, I want my screensaver to automatically kick back in after I quit the game, so I wrote another bash script for that, too.

Here's my setup.  I have a launcher on my panel that connects to this script:
```
#!/bin/bash

#kill any already-running instances of rejoystick,
#then turn it back on, since it doesn't like to double up.
	killall -9 rejoystick -q
	rejoystick -d
#turn off the screensaver
	gnome-screensaver-command -i &
#run the game
	doukutsu &
#launch the screensaver resuming script
	wait 15
	bash /home/dirjel/.bash_scripts/resume_screensaver.sh
```
This is my script to turn the screensaver back on:
```
#!/bin/bash

#Is Cave Story running?
	if [ "$( pidof doukutsu )" ]
#Yes? Wait a bit and check again
	then
	sleep 60
	bash /home/dirjel/.bash_scripts/resume_screensaver.sh
#No?  Turn the screensaver back on.
	else
	killall gnome-screensaver-command
	fi
```
Is this all going to work the way I want it to?  I want to be able to click on my launcher, turn on rejoystick, turn off the screensaver, play Cave Story, and have the computer check every 60 seconds on whether or not to turn the screensaver back on.  Now, I want to make sure also that it won't open another instance of the second script every time without closing the first one.  I'm pretty sure it'll go away on its own once it runs through, but I want to ask someone who knows what they're doing first.

If all this is good, then one more question.  It'll probably be okay to have a smaller interval for the sleep command in the second script, right?  It doesn't seem like it'd use up a whole lot of resources to run that command, but my computer is really old (it's a AMD Athlon 1800+), so I figure it's better to play it safe.

---

### Post by skoorbevad on 2009-01-24
You're going to have problems relaunching the script inside itself, I believe.  Consider a for loop:

```

#!/bin/bash
#

set -e

killall -9 rejoystick -q || { true; }
rejoystick -e || { echo "Can't launch rejoystick."; exit 1; }
gnome-screensaver-command -i 1>/dev/null &
doukutsu &

c=0
while [ $c < 1 ];
do
  sleep 60
  pidof doukutsu || { c=1; }
done

killall gnome-screensaver-command || { true; }

```

That should be close, correct any typos I made.

---

### Post by Dirjel on 2009-01-25
Sorry, but I don't understand that script at all >.>

I'm still super-new to all this, so I wouldn't recognize an error in that if it was looking me in the face.  The only familiar line in there I'm familiar enough with to recognize as a typo is the rejoystick -e.  I'm going to have to look over the rest of it, and I guess google it or something to find out what it does, and how it does it.

This'll probably be a good starting point for me, though.  Thanks.

---

### Post by eightmillion on 2009-01-25
> **Dirjel said:**
> Sorry, but I don't understand that script at all >.>

I'm still super-new to all this, so I wouldn't recognize an error in that if it was looking me in the face.  The only familiar line in there I'm familiar enough with to recognize as a typo is the rejoystick -e.  I'm going to have to look over the rest of it, and I guess google it or something to find out what it does, and how it does it.

This'll probably be a good starting point for me, though.  Thanks.

I think I can explain it for you

```

#!/bin/bash
#

set -e    # This makes it so that the script exits if any command fails

# This command kills rejoystick if it's already running. If it's not, the first part of the command
# will fail and make the script exit, but the double bars (||) means if the first part fails, execute 
# the second part "{ true; }". The second part is the shell builtin "true" that always returns a 
# successful exit status (0). This keeps the script from exiting even if the first command fails.

killall -9 rejoystick -q || { true; }  

# This command tries to start rejoystick, or if that fails, it echoes Can't launch rejoystick."
# and exits the script.

rejoystick -e || { echo "Can't launch rejoystick."; exit 1; }

# This command runs the gnome-screensaver-command -i in the background and redirect its standard output
# to /dev/null so that you don't see it and then starts doukutsu

gnome-screensaver-command -i 1>/dev/null &
doukutsu &

# This loop waits 60 seconds and the checks if doukutsu is still running. If doukutsu isn't running
# then the command "pidof doukutsu" will fail causing "c=1" to be executed which will make the loop
# not run on the next pass.

c=0
while [ $c < 1 ];
do
  sleep 60
  pidof doukutsu || { c=1; }
done

# This command just kills gnome-screensaver-command so that your screensaver is reenabled.
# The "|| { true; }" isn't really necessary unless you're using the exit status of this script 
# in another command or script.

killall gnome-screensaver-command || { true; }

```

---

### Post by Dirjel on 2009-01-25
Alright, I think I understand now.  I'll probably go over some of the other scripts I've made and incorporate some of this stuff.

Thanks, both of you.

---

### Post by Dirjel on 2009-01-25
The script doesn't work for some reason.
```
dirjel@dirjel-comp:~$ bash -x /home/dirjel/.bash_scripts/cavestory.sh
+ set -e
+ killall -9 rejoystick -q
+ rejoystick -d
+ echo 'Can'\''t launch rejoystick.'
Can't launch rejoystick.
+ exit 1
dirjel@dirjel-comp:~$ pidof rejoystick
3383
```
It seems to think that rejoystick isn't working, but it's turning on and running just fine.  Should I just get rid of the set -e at the beginning?  The command "rejoystick -d" isn't failing, but it doesn't produce any response in the shell, afaik.  Is that why it keeps diying?

---

### Post by eightmillion on 2009-01-25
Try it like this:

```

#!/bin/bash
#

set -e

pkill -9 rejoystick || {  true; }
rejoystick -e || { echo "Can't launch rejoystick."; exit 1; }
gnome-screensaver-command -i 1>/dev/null &
doukutsu &

c=0
while [ $c < 1 ];
do
  sleep 60
  pidof doukutsu || { c=1; }
done

killall gnome-screensaver-command || { true; }

```

I have a feeling that rejoystick isn't getting killed, so when you try to start it again it fails.

---

### Post by Dirjel on 2009-01-25
No, that's not the problem.  It's possible to have multiple rejoystick daemons running at once, it just messes up your controller input.  That's why I ran pidof rejoystick after the script; I was checking to see if it was really turning on.  It was.

The command to launch the daemon is rejoystick -d, not rejoystick -e.  Is that a typo, or is it important to the script?

Finally, I tried commenting out the set -e bit, to see if the script worked.  It still failed once it hit the || { echo "Can't launch rejoystick."; exit 1; } part.  I commented that out too, and tried it.  This was the result:
```
dirjel@dirjel-comp:~$ bash -x /home/dirjel/.bash_scripts/cavestory.sh
+ killall -9 rejoystick -q
+ rejoystick -d
+ gnome-screensaver-command -i
+ doukutsu
+ c=0
+ '[' 0 ']'
/home/dirjel/.bash_scripts/cavestory.sh: line 29: 1: No such file or directory
+ killall gnome-screensaver-command
/home/dirjel/.bash_scripts/cavestory.sh: line 39:  3969 Terminated              gnome-screensaver-command -i > /dev/null
dirjel@dirjel-comp:~$ ln: creating symbolic link `/home/dirjel/.doukutsu/doukutsu': File exists
ln: creating symbolic link `/home/dirjel/.doukutsu/DoConfig.exe': File exists
ln: creating symbolic link `/home/dirjel/.doukutsu/data': File exists
ln: creating symbolic link `/home/dirjel/.doukutsu/doc': File exists

```
The game turned on, but after I let it sit for a while, the screensaver came on too.

It said it already killed the gnome-screensaver-command before the game even started.

---

### Post by eightmillion on 2009-01-25
I think you need to change "while [ $c < 1 ];" to "while [ $c -lt 1 ];" or "while [[ $c < 1 ]];".

Edit: To explain, bash sees < and is expecting a redirect and doesn't find a file "1". That's why you're getting "/home/dirjel/.bash_scripts/cavestory.sh: line 29: 1: No such file or directory"

---

### Post by Dirjel on 2009-01-25
> **eightmillion said:**
> I think you need to change "while [ $c < 1 ];" to "while [ $c -lt 1 ];" or "while [[ $c < 1 ]];".

Edit: To explain, bash sees < and is expecting a redirect and doesn't find a file "1". That's why you're getting "/home/dirjel/.bash_scripts/cavestory.sh: line 29: 1: No such file or directory"

[ $c -lt 1 ];
that worked.  Thanks for taking the time to explain all this to me.  I'm learning a lot.  Anyway, the script is now working, life is good.  Thanks a lot.

---

### Post by sisco311 on 2009-01-25
What's the point of the loop anyway?

Just don't run doukutsu in the backround:
```

doukutsu
killall blabla

```

or use wait:
```
doukutsu&
wait `pidof doukutsu`
killall blabla
```

---

### Post by Dirjel on 2009-01-25
> **sisco311 said:**
> What's the point of the loop anyway?

Just don't run doukutsu in the backround:
```

doukutsu
killall blabla

```
...

Way to overthink things, huh?  I'll just run that, then.  It'll be easier on the system, since I'm not computing totally unnecessary stuff.  Good call.

---

### Post by skoorbevad on 2009-01-26
Sorry for going AWOL on that one, guess I should have checked back in to see if it worked for you!  Thanks to the poster for the inline comments in my script, and sorry for the typos -- they always happen when I write one off the top of my head.

As far as backgrounding the program itself like the poster above suggests, I dunno.  That would work fine also, I was just assuming there was some reason it was being backgrounded (maybe for rejoystick's case or something -- I don't really know how that works).

Hope it's all working out.

---

