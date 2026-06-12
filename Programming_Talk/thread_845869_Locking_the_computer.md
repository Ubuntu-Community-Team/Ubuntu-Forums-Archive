---
title: "Locking the computer"
date: 2008-07-01
forum: Programming Talk
---

### Post by brynjarh on 2008-07-01
I wasn't sure where to put this but I hope this is the right place.

Anyway I spend way to much time in the computer and I want to only use it 3-4 days of the week, so it would go something like Mon-Wed-Fri-Sun-Tue-Thu-Sat-Mon.. and so on.

But I also want to enforce that behavior by locking down my computer on the appropriate days, I can see two main ways of doing that, one would be to change GDM so that you can't enter in user name and password for those days, the other would be to make upstart not initialize the operating system on those days (it's upstart that does that isn't it?).

I like the latter since it's harder to get passed it(I think) and probably easier to implement.

But I'm not completely sure how to configure or change upstart in this way, what should I be looking at to implement this? I don't understand how upstart works but I could imagine it going something like this:

Normally upstart runs a series of jobs, I could add a job that would be executed first which checks the date and then decides if the remainder of jobs should be executed or not.

I'm not sure if upstart works this way but if it does, how would I go about doing that or some alternative that does approximately the same thing?

*EDIT*
The solution is in my second post (post 3).

---

### Post by LaRoza on 2008-07-01
Unplug it :-)

There is no way to reliably prevent a computer from running (even with a BIOS password) without restricting access to the computer physically, or making it incapable of operating.

---

### Post by brynjarh on 2008-07-01
Well it doesn't have to be completely reliable, just doesn't start except I do something to get around it, making initialization day specific sounds to me like a good way to go about that.

According to [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto) the scripts in /etc/rcS.d are the first to be executed, and they all start with S01.., S02.., S03.. so I guess the numbers there set the order, now all I need to do is learn bash scripting and disable initialization on specific days, or at least I hope that it's that simple.

*EDIT*
Okay so I've created a little script just to test if I'm on the right track, it goes something likes this:

```
#!/bin/bash
echo "test" > test.txt
date=$(date); 
weekday=${date:0:3};
if [ $weekday = "Sun" ]; then
	echo "Lock" > alienmother.txt
fi

if [ $weekday = "Mon" ]; then
	echo "Open" > alienmother.txt
fi

if [ $weekday = "Tue" ]; then
	echo "Lock" > alienmother.txt
fi

if [ $weekday = "Wed" ]; then
	echo "Open" > alienmother.txt
fi

if [ $weekday = "Thu" ]; then
	echo "Lock" > alienmother.txt
fi

if [ $weekday = "Fri" ]; then
	echo "Open" > alienmother.txt
fi

if [ $weekday = "Sat" ]; then
	echo "Lock" > alienmother.txt
fi
```

Put it in /etc/rcS.d under the name of S01aa.sh (-rwxr-xr-x 1 root root) and rebooted, but no file was created, what am I missing here?

*EDIT*

I'm working partially blindly cause I don't really understand how init works, but I guess this is me trying to figure out how it works.. anyway I've tried something else now which did not work either.

I moved the file to /etc/init.d , installed sysvconfig, executed that and selected Enable/Disable, saw my script in that list there and enabled it, rebooted but nothing happend.

what am I missing?

*EDIT*

On further inspection it seams to work, only the test.txt file wasn't created in /etc/init.d but at / , now I just need to make the script disrupt the initialization somehow.

*EDIT*
Just one problem left and I'll be able to do this, there seams to be a problem with the script only when executed in the bootup process, it works perfectly when I'm already logged in and do "bash test1.sh" but everything below "weekday=${date:0:3};" doesn't work on bootup, any suggestions on why that is and how I can fix it?

*EDIT*
Okay I looked at what was happening while I was booting up and I saw what went wrong, though I'm not sure how to copy it, anyway I know how to produce a very similar error, when I run the script using bash everything goes fine but when I run it using sh I get this error: test1.sh: 3: Bad substitution

So on bootup Ubuntu uses sh, not bash, now I just need to figure out how to change the script from bash to sh, or someone here could do it for me before I figure it out?

*EDIT*
Figured it out, weekday=${date:0:3}; apparently doesn't work with sh, so I removed it and changed date=$(date) to date=$(date +%u) and used just that, and used poweroff to shut down the computer on the appropriate days so to make it "impossible" to use the computer on those days.

---

### Post by pmasiar on 2008-07-01
It's waste of time to use technological solution for social problems.

Correct me if i am wrong, but IIUC you want to program PC to enforce limit on you PC use - to support your weak will? Better is to reward yourself with compliance.

Techno solution: Set a cron job which will shut computer down on certain days :-)

---

### Post by brynjarh on 2008-07-01
> **pmasiar said:**
> It's waste of time to use technological solution for social problems.

Correct me if i am wrong, but IIUC you want to program PC to enforce limit on you PC use - to support your weak will? Better is to reward yourself with compliance.

Techno solution: Set a cron job which will shut computer down on certain days :-)

the cron job thing seams way simpler... but it's not really a technological solution but a technological supplement with the social solution :D,

---

