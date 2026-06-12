---
title: "Shell doesn't beep"
date: 2010-07-15
forum: Programming Talk
---

### Post by SteelCore on 2010-07-15
I'm trying to implement a simple timer in bash using:
```
me@mylaptop:~$ sleep 5; echo -e "Time's up\a"
```
but I can't hear the beep sound.
Thanks for your help

---

### Post by Nano Geek on 2010-07-15
It could be that the beeper is disabled. Have you checked your BIOS?
If you tell me what kind of computer you have I'd better be able to help you.

**Edit:** I don't know if it would help, but you could also try taking the \a out of the quotes. That could be causing the problem.

---

### Post by SteelCore on 2010-07-16
I have tried the following statements and they should be both valid according [this excellent book]("http://gd.tuwien.ac.at/linuxcommand.org/tlcl.php") I've been reading.
```
laptop:~$ sleep 3; echo -e "Time's up\a"
Time's up
laptop:~$ sleep 3; echo "Time's up" $'\a'
Time's 
```
As seen the code properly executes but I still can't hear a beep.
I'm using an LG (S1 Express Dual) laptop. I checked the BIOS settings but could not find anything to enable the beeper.

---

### Post by Yarui on 2010-07-16
Have you tried opening terminal and entering the command
```
alsamixer
```
then checking to see if the internal speaker is muted?  I think it is labeled something like "beep", but I can't remember for sure.  It's one of the ones at the end of the list and I remember it being fairly obvious that was what it was for.

---

### Post by SteelCore on 2010-07-16
I just checked 'alsamixer'. There is a setting for 'beep' and another for 'internal'. I tried them both, alone and together, but still no beep from the shell.
PS after raising the 'beep' level the system started to beep on shutdown.

---

### Post by SteelCore on 2010-07-16
I'm trying to make the Shell produce a timed beep sound.
```
me@my-laptop:~$ sleep 1; echo -e "Time's up\a"
Time's up
me@my-laptop:~$ sleep 1; echo "Time's up" $'\a'
Time's up 
me@my-laptop:~$ 
```
Although I've raised the 'beep' volume in alsamixer, both of the above lines failed to produce the beep.
Thank you for any help.

---

### Post by Xyro on 2010-07-16
Check your _/etc/modprobe.d/blacklist.conf_ for the line
```
blacklist pcspkr
```
if it is present, change it to
```
#blacklist pcspkr
```
and try your code again. If your pc speaker is not blacklisted, then your issue is elsewhere. Hope that helps.

---

### Post by SteelCore on 2010-07-16
Thanks for the reply. The pcspkr was blacklisted and I commented the line but still no sound from the code.

---

### Post by sisco311 on 2010-07-16
Load the module:
```
sudo modprobe pcspkr
```

---

### Post by Xyro on 2010-07-16
Sorry, I should have mentioned that you need to restart, or as sisco31 pointed out, just simply load the module that had been blacklisted.

---

### Post by SteelCore on 2010-07-16
I loaded the module with (sudo modprobe pcspkr) and restarted but still no beep upon executing the code.
BTW in case it is of any relevance my laptop does beep when shut down although I don't know whether that is the same speaker the Shell uses with \a

---

### Post by lisati on 2010-07-16
Threads merged

---

### Post by Xyro on 2010-07-16
Try this:

System -> Preferences -> Sound

On the "Sound" tab, ensure that the following are enabled:

- Play alerts and sound effects
- Play alert sound

** I hope things haven't changed too much in 10.04...

Run:

```

$ lsmod | grep pcspkr

```

... and make sure it comes up. Mine gives me:

```

xyro@Q6600:~$ lsmod | grep pcspkr
pcspkr                 11136  0 

```

Then try:

```

$ echo -e "\a"

```

---

### Post by SteelCore on 2010-07-16
> ** I hope things haven't changed too much in 10.04...
They actually did, a bit. Now there is the alert and output volumes and in my case they are both not muted.
The lsmod gave this
```
me@my-laptop:~$ lsmod | grep pcspkr
pcspkr                  1518  0 
```
Yet the code still can't produce a beep.
I've tried it on some friends' laptops and it properly worked. I might have a hardware prob somewhere (although my laptop beeps when shutting down). I have 10.04 and 9.10 on the same laptop and they both don't beep with that escape sequence.

---

