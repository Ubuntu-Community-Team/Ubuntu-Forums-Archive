---
title: "Bash script to load something every 1 minute"
date: 2018-09-20
forum: Programming Talk
---

### Post by webmiester on 2018-09-20
Will this work or will I eventually crash my machine?

I make a script called /home/user/loop.sh

#!/bin/bash
Sleep 60
echo this is going to loop &
home/user/loop.sh &
Exit 0

Thanks.  If I understand it right, the program should load itself then exit right?  So this will become an endless loop, but because there is an exit, it won't hog up my resources.  Is my concept correct?

---

### Post by spjackson on 2018-09-20
It is my understanding that your process will terminate when the script reaches 'exit 0'. When this happens, background processes get re-parented either to process 1 (init) or on current systemd platforms to the user's systemd process.

I think I recall that once upon a time, the re-parenting did not happen, which would lead to a stack of defunct processes. This may have been on some Unix flavours, not necessarily Linux. I would not bank on it being a portable approach. Is there a reason why you don't want to simply loop rather than respawning the script?

---

### Post by ajgreeny on 2018-09-20
Does this problem have any relationship to your other thread at [https://ubuntuforums.org/showthread.php?t=2401618&p=13802276#post13802276](https://ubuntuforums.org/showthread.php?t=2401618&p=13802276#post13802276) ?

---

### Post by webmiester on 2018-09-20
Yeah, there is a reason...  I actually don't know how to loop.  I've been looking for the bash counterpart of "goto" but I can't find it.  If you can show me how to loop, I appreciate it.

---

### Post by webmiester on 2018-09-20
Yes, it is related.  I'm looking at plan B.  Plan A was to keep relaunching the script with Cron.  Since that didn't work, my plan B was to keep relaunching it in a script that will start on bootup.

---

### Post by webmiester on 2018-09-20
There is actually a 3rd thread I made which is here:
[https://ubuntuforums.org/showthread.php?t=2401617](https://ubuntuforums.org/showthread.php?t=2401617)

You see, even if I do get it to work with Cron, the Cron file just doesn't exist with the guest user :(
So for plan A to work I have to get Cron to launch my script and I need it to work with the guest user.
In case any of these 2 conditions doesn't work, I have plan B which is to let a script reload my command every few minutes and load the script on bootup.  So this thread was for plan B

---

### Post by webmiester on 2018-09-20
> **spjackson said:**
> It is my understanding that your process will terminate when the script reaches 'exit 0'. When this happens, background processes get re-parented either to process 1 (init) or on current systemd platforms to the user's systemd process.

I think I recall that once upon a time, the re-parenting did not happen, which would lead to a stack of defunct processes. This may have been on some Unix flavours, not necessarily Linux. I would not bank on it being a portable approach. Is there a reason why you don't want to simply loop rather than respawning the script?

Yeah, I had a bit of concern there too.  Even if it works, it just doesn't feel like it was made cleanly or made well.

Yeah, umm I don't know how to loop.  If you could teach me,  I would appreciate it.

---

### Post by webmiester on 2018-09-20
> **ajgreeny said:**
> Does this problem have any relationship to your other thread at [https://ubuntuforums.org/showthread.php?t=2401618&p=13802276#post13802276](https://ubuntuforums.org/showthread.php?t=2401618&p=13802276#post13802276) ?

Yeah, I tried having Cron launch the script but it didn't work.  So plan B is to have a script keep relaunching my script.

I have a 3rd thread which is above which describes another problem I have with my plan A.  I haven't found a way to fix it yet.

---

### Post by spjackson on 2018-09-20
> **webmiester said:**
> Yeah, umm I don't know how to loop.  If you could teach me,  I would appreciate it.
A simple "forever" loop.
```

#!/bin/bash

while [ 0 ]
do
    sleep 10
    echo looping
done

```

---

### Post by webmiester on 2018-09-21
> **spjackson said:**
> A simple "forever" loop.
```

#!/bin/bash

while [ 0 ]
do
    sleep 10
    echo looping
done

```

Thank you so much.  After you mentioned looping, I looked it up too.  It is so much better.  I was able to make the system reload the command 99x instead of perpetually reloading.  I really want to thank you.

---

### Post by SeijiSensei on 2018-09-21
It's much easier to do this from cron.  Use "sudo crontab -e" to edit root's crontab and enter

```
* * * * * /path/to/your/script
```

That will run the script once every minute. Make sure the script is marked executable.

---

### Post by Skaperen on 2018-09-21
given your level of understanding the system and bash script programming i think it would be best for your posts to include a description of what you are trying to accomplish.

---

