---
title: "Noob needs brief help with shell scripting. *shows shame*"
date: 2008-10-17
forum: Programming Talk
---

### Post by AreonEpta on 2008-10-17
My script doesn't work. I'm trying to find out why by reading tutes and FAQs but to no avail. I'm trying to make it so that I can turn on and off power saves tunes when I want to. The script keeps returning errors.

My shell script, saved as "powermanage" and then chmod 755'd:
```
#/bin/bash
clear
if /sys/devices/system/cpu/sched_mc_power_savings=0 ; then
    echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
elif /sys/devices/system/cpu/sched_mc_power_savings=1
    echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
fi
```My error:
```
~/Desktop$ ./powermanage
./powermanage: line 5: syntax error near unexpected token `else'
./powermanage: line 5: `else'
```
HALP!

---

### Post by mcai8sh4 on 2008-10-17
Not sure if this helps, but I'm sure someone in the know will sort this for you.
Have you tried adding " ; then" to the end of you 'elif' line?

eg : elif /sys/devices/system/cpu/sched_mc_power_savings=1; then

Regards

Steve

edit : this has helped me alot in the past could of weeks
[http://www.tldp.org/LDP/abs/abs-guide.pdf](http://www.tldp.org/LDP/abs/abs-guide.pdf)

---

### Post by AreonEpta on 2008-10-17
That fixed that. Now I'm getting:
```
~/Desktop$ ./powermanage
./powermanage: line 3: /sys/devices/system/cpu/sched_mc_power_savings=0: No such file or directory
./powermanage: line 5: /sys/devices/system/cpu/sched_mc_power_savings=1: No such file or directory
```

---

### Post by mcai8sh4 on 2008-10-17
when you change dir to "/sys/devices/system/cpu/" are those files there?
Surely having a filename with '=0' or '=1' at the end is wrong.

I'm only guessing but I think your confused as to what your script is trying to do.
The way I see it you are writing '0' into a file (with '=0' at the end of the file name). For this to work the file would have to exist. But It sounds wrong to me.

Sorry If I've misunderstood, but I don't really know what your trying to do.

edit : have a look at this - might assist you...
[http://ubuntuforums.org/showthread.php?t=908264](http://ubuntuforums.org/showthread.php?t=908264)

-s

---

### Post by AreonEpta on 2008-10-17
I'm trying to check if the file = 1, if so then write 0 into the file. If not then write 1 into the file.

---

### Post by mcai8sh4 on 2008-10-17
ok I see what you're trying to do.
As mentioned in my edit [http://ubuntuforums.org/showthread.php?t=908264](http://ubuntuforums.org/showthread.php?t=908264) might point you in the right direction.

I not great with scripts, I usually have to rewrite mine a few times before I get them right, but if I can help you, I may learn somthing as well :)

For your If statement I would imagine youd have to compare the contents of the file - something along the lines of

```
if  [ "$(cat /sys/devices/system/cpu/sched_mc_power_savings" = "0" ]; then
```

the speech marks may be wrong, I always confuse between handling number or strings, but the line above compares the CONTENTS of the file with the value (char?) 0

---

### Post by mssever on 2008-10-17
> **mcai8sh4 said:**
> For your If statement I would imagine youd have to compare the contents of the file - something along the lines ofCorrection:

```
if  [[ "$(cat /sys/devices/system/cpu/sched_mc_power_savings)" = 0 ]]; then
```

---

### Post by AreonEpta on 2008-10-17
Thank you both so much. It's working great now. I really appreciate the help. I'd love it if you could point me towards a place where I could learn to understand some of the syntax you both used. I've yet to check out that link in your edit, but I'm about to; that may be just what I need.
 
THANKS AGAIN!

---

### Post by mssever on 2008-10-17
> **AreonEpta said:**
> I'd love it if you could point me towards a place where I could learn to understand some of the syntax you both used.
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Don't let the name fool you. It includes the basics, as well as the advanced stuff.

---

### Post by AreonEpta on 2008-10-18
Thanks mssever. That'll do it.

---

### Post by AreonEpta on 2008-10-18
Okay. So more troubles...

```
#/bin/bash
if  [[ "$(cat /sys/devices/system/cpu/sched_mc_power_savings)" = 0 ]]; then
    sudo echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
    echo "***Powersave Mode active***"
elif  [[ "$(cat /sys/devices/system/cpu/sched_mc_power_savings)" = 1 ]]; then
    sudo echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
    echo "***Performance Mode active***"
fi
```returns...

```
./powermanage: line 3: /sys/devices/system/cpu/sched_mc_power_savings: Permission denied

```

Also, when I go to enter it in Terminal, I get a bash error...
```
bash: /sys/devices/system/cpu/sched_mc_power_savings: Permission denied
```

And then when I go to open it in Text Editor I get...
> Could not open the file /sys/devices/system/cpu/sched_mc_power_savings.
Unexpected error: No such device

Any ideas?

---

### Post by mcai8sh4 on 2008-10-18
glad you're moving on (and thanks to mssever for correcting me - I'm always getting my syntax wrong).

Not sure on the best way to give you permission (run the script as root? maybe)
If I think of anything I'll let yuo know.

---

### Post by AreonEpta on 2008-10-18
> **mcai8sh4 said:**
> glad you're moving on (and thanks to mssever for correcting me - I'm always getting my syntax wrong).
 
Not sure on the best way to give you permission (run the script as root? maybe)
If I think of anything I'll let yuo know.
 
So, then...?
```
~$ sudo ./powermanage
```
 
Like that? I'm at work now, and obviously enough, we use winders here. I'll check and see if that does it when I get home.

---

### Post by mssever on 2008-10-18
> **AreonEpta said:**
> ```
#/bin/bash
if  [[ "$(cat /sys/devices/system/cpu/sched_mc_power_savings)" = 0 ]]; then
    sudo echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
    echo "***Powersave Mode active***"
elif  [[ "$(cat /sys/devices/system/cpu/sched_mc_power_savings)" = 1 ]]; then
    sudo echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
    echo "***Performance Mode active***"
fi
```returns...

```
./powermanage: line 3: /sys/devices/system/cpu/sched_mc_power_savings: Permission denied

```
A quirk of sudo is that it only applies to a single process, so redirection loses its privileges. So, something like this would work: ```
echo 1 | sudo tee /sys/devices/system/cpu/sched_mc_power_savings
```
> **AreonEpta said:**
> So, then...?
```
~$ sudo ./powermanage
```Like that?
That will work as well. Of course, it'll mean that your entire script will run as root (and you won't need to use sudo at all within the script).

As to which approach is better, it's a bit of a tossup. On the one hand, it's best to have as little as possible running as root, which would favor the first solution. On the other hand, calling the entire script with sudo serves to alert the user that the script uses root privileges, which wouldn't always happen otherwise (for example, if sudo didn't need to prompt for a password). So you'll have to decide which you think is best.

---

### Post by AreonEpta on 2008-10-19
Thanks. I'll give that a try when I get off work.

---

