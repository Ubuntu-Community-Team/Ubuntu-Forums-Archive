---
title: "Trap Computer Shutdown Signal"
date: 2010-07-12
forum: Programming Talk
---

### Post by Penguin Guy on 2010-07-12
Hi! I've got a shell script that downloads and displays a [sunmap]("http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg") as the background every 60 seconds. The program reverts the background to the original when it ends by using a trap statement - everything works fine apart from when the script is ended by a computer shutdown, in which case the background is not reverted. This is part of a small Launchpad project and this issue is putting on hold a merge, so any help would be greatly appreciated.

[View File]("http://bazaar.launchpad.net/~codemonkeydevs/codemonkey/trunk/annotate/head:/earthwallpaper.sh_new") - [Download File]("http://bazaar.launchpad.net/~codemonkeydevs/codemonkey/trunk/download/head:/earthwallpaper.sh_ne-20100603132600-z2020xi4jj5slqog-1/earthwallpaper.sh_new") - [View Bug]("https://bugs.launchpad.net/codemonkey/+bug/589355")

Thanks!


_SOLVED_
Turns out trap doesn't work with loops, use the [FONT="Courier New"]wait[/FONT] statement to fix this.

---

### Post by trent.josephsen on 2010-07-12
I must be misunderstanding you.  If you're about to shut down the computer, why do you care whether it gets reverted or not?

---

### Post by Penguin Guy on 2010-07-12
> **trent.josephsen said:**
> If you're about to shut down the computer, why do you care whether it gets reverted or not?
Because when you next start the computer you'll have no wallpaper.

---

### Post by trent.josephsen on 2010-07-12
> **Penguin Guy said:**
> Because when you next start the computer you'll have no wallpaper.

Oh!  I set my wallpaper in .xinitrc, so that never even occurred to me.

Maybe SIGKILL?  But I would have expected SIGTERM to work.

---

### Post by Penguin Guy on 2010-07-12
> **trent.josephsen said:**
> Maybe SIGKILL?  But I would have expected SIGTERM to work.
I'm pretty sure you can't trap SIGKILL, but I'll give it a go anyway.

EDIT: Nope, that doesn't work either.

---

### Post by PaulM1985 on 2010-07-12
From searching the net it seems that SIGTERM should work.

However if it doesn't when the system shuts down rc.d scripts are called and maybe you could add something in there to notify your program.

Below is the link I plagiarised this information from :-) 

[http://stackoverflow.com/questions/2832376/how-to-detect-pending-system-shutdown-on-linux](http://stackoverflow.com/questions/2832376/how-to-detect-pending-system-shutdown-on-linux)

Hope it is of some help.

Paul

---

### Post by Penguin Guy on 2010-07-12
> **PaulM1985 said:**
> From searching the net it seems that SIGTERM should work.

However if it doesn't when the system shuts down rc.d scripts are called and maybe you could add something in there to notify your program.

Below is the link I plagiarised this information from :-) 

[http://stackoverflow.com/questions/2832376/how-to-detect-pending-system-shutdown-on-linux](http://stackoverflow.com/questions/2832376/how-to-detect-pending-system-shutdown-on-linux)

Hope it is of some help.

Paul
I'm already using SIGTERM, and rc.d scripts are really a bit advanced for this program. Are there any other possible suggestions?

---

### Post by trent.josephsen on 2010-07-12
> **Penguin Guy said:**
> I'm pretty sure you can't trap SIGKILL, but I'll give it a go anyway.

No, of course not.  I meant that perhaps your script is being sent KILL instead of TERM, even though TERM should end the script.  Sorry for miscommunicating.

---

### Post by Penguin Guy on 2010-07-12
> **trent.josephsen said:**
> I meant that perhaps your script is being sent KILL instead of TERM, even though TERM should end the script.
Looks like it is, but why?

---

### Post by ov3rcl0ck on 2010-07-12
Shell scripts are too high level to catch SIGTERM or SIGKILL. Maybe theres a way to do it, but I don't think trapping a signal will do it, seeing as the signal is sent to BASH/shell rather than your script. Unless BASH will relay this information to a shell script, which I don't think it does.

---

### Post by trent.josephsen on 2010-07-12
And kill -TERM works as you expect?  Does it behave the same way when you log out without shutting down, or does it continue running while you're logged out?

---

### Post by dwhitney67 on 2010-07-12
> **ov3rcl0ck said:**
> Shell scripts are too high level to catch SIGTERM or SIGKILL. Maybe theres a way to do it, but I don't think trapping a signal will do it, seeing as the signal is sent to BASH/shell rather than your script. Unless BASH will relay this information to a shell script, which I don't think it does.

Wrong!

Here's an example script where SIGTERM is caught:
```

#!/bin/bash


trap dothis SIGTERM


function dothis()
{
   echo "Revert to original wallpaper here."
   exit 0
}

while [ true ]
do
   sleep 2
done

```
Run this script, then after referencing the PID of the script, issue a SIGTERM signal to it with something like:
```

kill -15 <pid>

# or

kill -s SIGTERM <pid>

```
To get a list of all of the signals that are recognized by Bash, run ```

trap -l

```
Obviously, as mentioned earlier, SIGKILL cannot be intercepted.

---

### Post by Penguin Guy on 2010-07-13
On a suspicion I googled traps and loops and found this page: [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html)
It seems you need to add a [FONT="Courier New"]wait[/FONT] statement if you want traps to work with loops, now I know what exactly the problem is it should be easy to fix it, so I'll mark this thread [SOLVED].

Thanks for all the help!

---

