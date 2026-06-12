---
title: "[SOLVED] How to repeat terminal commands at intervals?"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by pHreaksYcle on 2008-09-20
I want to repeat a wget line after a specific period of time. I went through man page for wget and found nothing like this. Any ideas? Thanks!

---

### Post by nisaky on 2008-09-20
Press up key, few times if needed

---

### Post by sayakb on 2008-09-20
Make a bash script for it:
At a terminal:
```
gedit script
```
Type in:
```
#!/bin/bash

while [ 1 ]; do
  echo <command>
  sleep 1
done
```

Replace echo line with the wget line. Set value of sleep in seconds.
Now exit gedit and at the terminal again:
```
chmod +x script
./script
```

---

### Post by pHreaksYcle on 2008-09-20
EDIT: Do I replace the WHOLE echo line or just the part in <>?

EDIT: Thank you!

---

### Post by acidsolution on 2008-09-20
you can have the entry of the script on the crontab

---

### Post by sayakb on 2008-09-20
If your problems have been addressed, please mark the thread as solved (Thread tools->Mark thread as 
solved) :)

---

### Post by pHreaksYcle on 2008-09-20
Do I replace the WHOLE echo line or just the part in <>?

---

### Post by Sinkingships7 on 2008-09-20
> **pHreaksYcle said:**
> Do I replace the WHOLE echo line or just the part in <>?

Replace the ```
<command>
``` including the '<>', with the command you want executed.

---

### Post by pHreaksYcle on 2008-09-20
./script: line 4: syntax error near unexpected token `newline'

---

### Post by sayakb on 2008-09-20
You need to replace the whole echo line.
For example, if you want to execute:
```
wget http://blahblah.com
```Then it should look like:
```

#!/bin/bash

while [ 1 ]; do
  wget [http://blahblah.com](http://blahblah.com) &
  sleep 1 
done
```

---

### Post by RequinB4 on 2008-09-20
Um, the above won't work, simply putting it in a while loop starts dl, waits for it to finish, and then starts downloading the whole thing again.  If you want to start wget download and then restart/continue downloading it after a certain time, you need:

(the last line is unnecessary I use it for debugging)

```
#!/bin/bash
echo "What is the URL?"
read url
wget $url &
sleep 6
killall wget
while [ 1 ] ; do
   wget -c $url &
   sleep 6
   killall wget
done
killall wget

```

That'll fix problems. (control c stops the script)

Edit: just re-read the OP, this might not be what you want.  Anyway, here it is.

---

### Post by pHreaksYcle on 2008-09-20
> Replace the
Code:

<command>

including the '<>', with the command you want executed.

Sorry! :P Thanks again!

---

### Post by pHreaksYcle on 2008-09-20
It works and works well! Thank you!

---

### Post by sayakb on 2008-09-20
Glad I could help! :)

---

### Post by lswb on 2008-09-20
If the "wait" and and "waitretry" options for wget aren't what you want, look at the man pages for "at"

Say you wanted the command "wget http://www.website.com/file" to run in 10 minutes,

at a terminal type 

at now + 5 min

the "at>" prompt will appear. Type your command here and press enter. You can keep adding commands as you like, when done adding commands type Ctrl-D

If you want this to be a recurring task take a look at cron and anacron.

---

### Post by pHreaksYcle on 2008-09-20
I'm using this format:

#!/bin/bash

while [ 1 ]; do
  wget [http://blahblah.com](http://blahblah.com) &
  sleep 1 
done

for my script. The problem is, it bogs my system down with like a million wget instance. Ideas? Thanks!

---

### Post by cariboo on 2008-09-20
Your script is going out and downloading whatever its that you are doing once every second. If you remeber from your first post the poster that suggested this script said to change the time to whatever you want in seconds.

> #!/bin/bash

while [ 1 ]; do
wget [http://blahblah.com](http://blahblah.com) &
sleep 1
done

Change the 1 in while [ 1 ]; do to the number of seconds you want to wait before your scripts runs again.

Jim

---

### Post by pHreaksYcle on 2008-09-20
EDIT: I am using the parameter --spider so it isn't actually downloading, just bumping the page for info. Quicker that way.
EDIT: I thought you changed the sleep value not the while value

I know, I did. In this case, I changed it to .1 :)

Any knowledge you have on how to kill the process when it's done, then restarting it, instead of just multiplying like rabbits?

Thanks!

---

### Post by sayakb on 2008-09-20
Add a **killall wget **above the [B]done:
[/B]#!/bin/bash

while [ 1 ]; do
  wget [http://blahblah.com]("http://blahblah.com/") &
  sleep 1 
killall wget
done

PS: Please do not open a new thread for similar topics. You could remove the SOLVED tag and continue asking in the previous one.

---

### Post by pHreaksYcle on 2008-09-20
EDIT: LinuxIsInnovation, do I have to change the while value in [ ] as well as the sleep value or no?

Sorry about that :P

Thanks again, once more your solution has pleased me!

---

### Post by sayakb on 2008-09-20
The value in [ ] is just a boolean flag signifying that the loop will go on indefinitely as the condition within [] is always true (ie. 1). It does not signify sleep time, or anything :)
So, no. You don't need to change that.

---

### Post by jpeddicord on 2008-09-20
Merged threads.

---

