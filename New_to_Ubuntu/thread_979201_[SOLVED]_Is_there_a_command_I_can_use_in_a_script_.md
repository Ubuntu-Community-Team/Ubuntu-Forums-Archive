---
title: "[SOLVED] Is there a command I can use in a script to make the PC speaker beep?"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by diablo75 on 2008-11-11
I'm making a bash script.  I have a count down at the end of it that goes like this:

```
echo "All software has been installed.  The system will reboot in 10 seconds" ## Displays the quoted message on screen
sleep 1; ##pauses the script for 1 second
echo "Restarting in 9 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 8 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 7 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 6 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 5 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 4 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 3 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 2 seconds.  Press CTRL-C to cancel"
sleep 1;
echo "Rebooting in 1 second..  Press CTRL-C to cancel"
sleep 1;
init 6 ## reboots the computer
```

I'd like to add in some beeps to go with each echo.

Thanks!

---

### Post by nhasian on 2008-11-11
how about the *speaker-test* command?

---

### Post by kaibob on 2008-11-11
There's a utility in the repo's called beep. I just tried it, and it does what it says it does. 

From the man page:

> beep allows the user to control  the  pc-speaker  with  precision,
       allowing  different sounds to indicate different events.  While it
       can be run quite happily on the command line, it&#8217;s intended  place
       of residence is within shell/perl scripts, notifying the user when
       something interesting occurs.  Of course,  it  has  no  notion  of
       what&#8217;s interesting, but it&#8217;s real good at that notifying part.

       All  options  have default values, meaning that just typing &#8217;beep&#8217;
       will work.  If an option is specified more than once on  the  com&#8208;
       mand  line,  subsequent  options  override their predecessors.  So
      &#8217;beep -f 200 -f 300&#8217; will beep at 300Hz.


---

### Post by sisco311 on 2008-11-11
try:
```
echo -e '\a'
```

or the *beep* command.

```
sudo aptitude install beep
```

---

### Post by diablo75 on 2008-11-11
> **kaibob said:**
> There's a utility in the repo's called beep. I just tried it, and it does what it says it does. 

This works.  Thanks!

---

### Post by diablo75 on 2008-11-11
> **sisco311 said:**
> try:
```
echo -e '\a'
```



Actually this works better for me because I don't have to install anything.  Thanks!

---

