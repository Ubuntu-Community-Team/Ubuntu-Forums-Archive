---
title: "a shell script question"
date: 2010-09-26
forum: Programming Talk
---

### Post by nubalci on 2010-09-26
Hi,
When I type
synclient TouchPadOff=1
this disables touchpad.
But if I put the following two lines in a script file as follows:
#!/bin/bash
synclient TouchPadOff=1
it doesn't work (just no effect). What may be the problem, and what do you think would solve it?
Thank you.

---

### Post by cavh on 2010-09-26
Is the script executable?

```
chmod u+x /path/to/your/script
```

If the path is outside of your home folder, you may need to sudo it:

```
sudo chmod u+x /path/to/your/script
```

---

### Post by nubalci on 2010-09-26
> **cavh said:**
> Is the script executable?

```
chmod u+x /path/to/your/script
```

If the path is outside of your home folder, you may need to sudo it:

```
sudo chmod u+x /path/to/your/script
```

Yes, it is executable and on the path. It runs without error. It just doesn't work, whereas if I type what's in the script  in the terminal box it works.

---

### Post by amauk on 2010-09-26
sounds like a permissions problem
Are you running the script as root, or as a normal user?

I don't own a laptop, but it seems unlikely that unprivileged users could disable a piece of hardware

---

### Post by nubalci on 2010-09-26
> **amauk said:**
> sounds like a permissions problem
Are you running the script as root, or as a normal user?

I don't own a laptop, but it seems unlikely that unprivileged users could disable a piece of hardware

I don't dispute what you say, but no, I don't sudo, and it just works. I started to think that it is some sort of timing issue. I just hope it isn't something more serious. The reason is that if you run the script enough many times (3 or 4 maybe) it eventually works. And I also discovered that sometimes this may be needed when one directly works at the terminal box, too. So, I don't know for sure, but it looks like some messages are not making it to some sort of queue.

---

### Post by amauk on 2010-09-26
> **nubalci said:**
> I don't dispute what you say, but no, I don't sudo, and it just works. I started to think that it is some sort of timing issue. I just hope it isn't something more serious. The reason is that if you run the script enough many times (3 or 4 maybe) it eventually works. And I also discovered that sometimes this may be needed when one directly works at the terminal box, too. So, I don't know for sure, but it looks like some messages are not making it to some sort of queue.

Well, again no experience with laptop touchpads
but you could do something like this
(assuming that synclient exits 0 on success)

```
#!/bin/bash

COUNTER=0
synclient TouchPadOff=1

while [ "$?" -ne 0 ] && [ "$COUNTER" -lt 10 ]; do
    sleep 1
    synclient TouchPadOff=1
    COUNTER=$(expr "$COUNTER" + 1)
done
```

This will run synclient until either success or 10 failures

---

### Post by phrostbyte on 2010-09-26
Do you plan on running this script at startup?

---

### Post by nubalci on 2010-09-26
> **phrostbyte said:**
> Do you plan on running this script at startup?

No, I will run the script, or just type in the command when the touchpad becomes a nuisance. Not at startup.

My first impression was that it had something to do with script file / direct typing, but sure enough this seems not to be the case after trying it many times. The same anomaly can be observed in both cases. It nay have something to do how synclient works, not sure...

---

### Post by Some Penguin on 2010-09-27
What did you name the script, and how are you running it?

---

### Post by Geek10 on 2010-09-27
Hi nubalci,

Would you mind posting your whole shell script? You see, I'm possibly going to need one for the first time myself (for some other bit of code).

And whether you consent or not to posting it, were there any particularly helpful resources on writing your shell script code? I'm only a beginner at Unix coding, so anything would be gratefully received!!:-?

Thanks

---

### Post by pbrane on 2010-09-27
try **/usr/bin/synclient**. you probably need to path in a shell script.

---

### Post by donwinchell on 2010-10-24
I have looked, and looked, can someone please tell me the purpose of the

#!/bin/bash    .. ?
 
line at the beginning of a script. - I have found it is not actually needed.

another one

sometime it seems necessary to put  ./  in front of a script to get it to run and sometimes it does not seem necessary   what is the ./ about ?

and what is .sh at the end?  does it DO anything or just identify the file as a script?
(and yes, I AM making scripts executable)


I have been building and using scripts for a while (a year?) and they work and do useful things for me, but every time I build a new one I seem to have to struggle with these issues.  nothing critical here, just some quandaries.  Any one with some knowledge and spare time to answer this would be greatly appricieated.

thanks.

---

### Post by Vox754 on 2010-10-24
> **donwinchell said:**
> I have looked, and looked, can someone please tell me the purpose of the

#!/bin/bash    .. ?
 
line at the beginning of a script. - I have found it is not actually needed.

That line is called a "shebang". You can read for more information by searching for that term on the Internet.
It defines an interpreter with which to run the script.

You can run a script explicitly by using its interpreter:
```

bash   file.sh
perl   file.pl
tclsh  file.tcl
python file.py

```
But if you include the shebang, the system will use the appropriate interpreter automatically.

Respectively
```

#!/bin/bash
#!/usr/bin/perl
#!/usr/bin/tclsh
#!/usr/bin/python

```
will allow you to call
```

file.sh
file.pl
file.tcl
file.py

```

> 
another one

sometime it seems necessary to put  ./  in front of a script to get it to run and sometimes it does not seem necessary   what is the ./ about ?

For security purposes, an executable (including a script) will be run only if it is in a directory listed by the $PATH variable.
```

echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Additionally you can run the executable giving its path, either the full path or a relative path.
```

/opt/program/bin/executable
../dir/bin/executable

```

By using "./executable" you are giving the path of the executable in the current directory, which is simply the dot "."

> 
and what is .sh at the end?  does it DO anything or just identify the file as a script?
(and yes, I AM making scripts executable)

A file extension, such as ".sh", is not needed in Linux at all. It is only for the convenience of the user. Many scripts are given with an extension to identify them, but others are not. This gives the impression that they are binaries, when in fact they are not. However, this distinction is not necessary. The only requirement is that it must be able to execute.

For example, the command "firefox", is not a binary executable, it's just a shell script which sets up some options and thens calls the real executable.
```

file /usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.11/firefox.sh'

file /usr/lib/firefox-3.6.11/firefox.sh 
/usr/lib/firefox-3.6.11/firefox.sh: POSIX shell script text executable

```

> 
I have been building and using scripts for a while (a year?) and they work and do useful things for me, but every time I build a new one I seem to have to struggle with these issues.  nothing critical here, just some quandaries.  Any one with some knowledge and spare time to answer this would be greatly appricieated.

thanks.
I am surprised that you have been writing scripts for a while and do not know the basics.

---

### Post by donwinchell on 2010-10-24
thanks for your kind explanations.
I guess the reason I have never learned the basics is that my objective has not been to learn to write scripts but just to accomplish some other business objective.
I appreciate your time and explanations.

---

