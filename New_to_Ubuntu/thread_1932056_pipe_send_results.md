---
title: "pipe send results"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-02-26
I'm trying to pipe results of a command to a file called t.
Tried
modprobe -l |t
I also tried
modprobe -l |nano t

No luck. Seems that t doesn't exist in my directory even after I do "nano t" and save it. But I didn't think I'd have to create t first. Maybe I need to learn what "pipe" is and what it can do.

Would appreciate knowing what I'm doing wrong.

---

### Post by sudodus on 2012-02-26
> **Kevin McCready said:**
> I'm trying to pipe results of a command to a file called t.
Tried
modprobe -l |t
I also tried
modprobe -l |nano t

No luck. Seems that t doesn't exist in my directory even after I do "nano t" and save it. But I didn't think I'd have to create t first. Maybe I need to learn what "pipe" is and what it can do.

Would appreciate knowing what I'm doing wrong.
You redirect to a file with >
for example
```
echo 'Hello World' > hello.txt
```
and you pipe to another program with |
for example ```
df | grep /$
```

so try ```
modprobe -l > t
```

---

### Post by papibe on 2012-02-26
I believe your trying to 'redirect' the output of a command?

Try this:
```
modprobe -l > file
```
Then the result of the command will be on the file 'file'.

Is that what you need?
Regards.

EDIT: sudodus got it first.

---

### Post by Kevin McCready on 2012-02-26
thanks guys. that worked.

but when I got tricky and tried
modprobe -l > t|nano t
I got a message which said
Received SIGHUP or SIGTERM

BTW it overwrites t without asking. Guess I'll have to learn to be careful with that.

---

### Post by Lisiano on 2012-02-26
If you wish to open t in nano right after you redirected the output, you need to do an && or an ; instead of a pipe, as others said, pipes send output from one command, to another.
So to do what you want
```
modprobe -l > t; nano t
```
Also it seems to me you just want to view the output of modprobe without scrolling up and down in your terminal, try using this instead if that is what you want
```
modprobe -l | less
```

EDIT: Here is a list of what does what,
> - Redirect and overwrite
>> - Redirect and append to the end
| - Pipe the output to another command
|| - Do if the exit code is False (If the program fails)
&& - Do if the exit code is True (If the program succeeds)
& - Do it in the background and execute the next command right away.
; - Delimiter, means it's the same if you typed the commands on different lines.

---

### Post by sudodus on 2012-02-26
> **Kevin McCready said:**
> thanks guys. that worked.

but when I got tricky and tried
modprobe -l > t|nano t
I got a message which said
Received SIGHUP or SIGTERM

BTW it overwrites t without asking. Guess I'll have to learn to be careful with that.
You can pipe into less (a file viewer)
```
modprobe -l | less
```
but I would not try to pipe into an editor. A good example is to list the hardware
```
gksudo lshw | less
``` or the persistent alternative
```
gksudo lshw > lshw.txt
```

And yes > overwrites, while >> appends.
Try
```
echo 'line 1' > lines.txt
echo 'line 2' >> lines.txt
```

---

### Post by papibe on 2012-02-26
> **Kevin McCready said:**
> modprobe -l > t|nano t
If you want to edit the file immediately after creating it, do this:
```
modprobe -l > t; nano t
```
Or try this if you want to see the output of modprobe page by page:
```
modprobe -l | less
```
Pressing space will go to the next page, and 'q' will get you back to the command line. Note that none file is created.

> **Kevin McCready said:**
> BTW it overwrites t without asking. Guess I'll have to learn to be careful with that.
Indeed.

Hope it helps.
Regards.

EDIT: again, sudodus was faster :-)

---

### Post by Kevin McCready on 2012-02-26
Wow guys. This is awesome. I've learned more in the last five minutes from you than about 2 weeks of reading manuals. 
"Info >" didn't seem to do it.

Actually what I'm trying to do is make my mouse left-handed each time I boot (in LXDE each time I boot I have to change it over).

So I was trying to find out how the mouse worked and wanted to search for "mouse" in the kernel modules.

I've now learnt to do
modprobe -l | grep mouse

and get a few results. Can I now pick a kernel file and change right-handed mouse to left-handed mouse?

---

### Post by Lisiano on 2012-02-26
Take a look here, this will be easier
[http://forum.lxde.org/viewtopic.php?t=192&f=8](http://forum.lxde.org/viewtopic.php?t=192&f=8)

Or add this as a startup script
```
#!/bin/bash
xmodmap -e "pointer = 3 2 1"
```

@papibe @sudodus I was faster the 2nd time and this time ;P!

---

