---
title: "Script if then?"
date: 2005-05-06
forum: Programming Talk
---

### Post by DarkGreen16 on 2005-05-06
Is it possible to make a script so that when its run once it will do x and then when its run again it will do y?

Like if I wanted to set it so whenever i ran ff the first time it would run firefox but if i typed ff again it would killall firefox?

any idea on how to do something like this?

---

### Post by Merc248 on 2005-05-06
[QUOTE=DarkGreen16]Is it possible to make a script so that when its run once it will do x and then when its run again it will do y?

Like if I wanted to set it so whenever i ran ff the first time it would run firefox but if i typed ff again it would killall firefox?

any idea on how to do something like this?[/QUOTE]
 Hmm.  Well, I'm not entirely sure exactly how you would do it, but I'd imagine that you could have a separate file that has a value that switches between two things, and then reading that file every time you execute, which does whatever appropriate action (and then switching that value in the file to the opposite value).

---

### Post by mendicant on 2005-05-06
You could follow the init script mechanism, and put a file in /tmp/run/ff.pid, check if the file and process exists, and if so, do the killall.  Note that it may be a bad idea to have a single command that does two opposing things (the init scripts do this, but they require an argument--effectively, two different commands).  Of course, it depends on what you want to do, but you are probably better off having ffs and ffk, for instance.

---

### Post by ssam on 2005-05-06
would this work
```
#!/bin/bash
killall firefox || firefox &
```

the || is the logical OR operatior.

it first tries to killall firefox, if that fails it starts firefox

the & on the end backgrounds firefox, you may or may not want that

have you read the advanced bash scripting guide [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

it is not as scary as it sounds, and has lot of useful snippits of script.

---

### Post by LordHunter317 on 2005-05-06
[center][left] [left][QUOTE=mendicant]You could follow the init script mechanism, and put a file in /tmp/run/ff.pid,[/quote]They put the file in /var/run.


>  check if the file and process exists, and if so, do the killall. Note that it may be a bad idea to have a single command that does two opposing things (the init scripts do this, but they require an argument--effectively, two different commands).Yes, it's a very bad idea.  In fact, I'd go as far to say it's a retarded one.

Commands should generally be deterministic in nature: given the same input to a command, I should expect the same output everytime.

A command that does different things based on prior state is confusing to a user.  


> Of course, it depends on what you want to do, but you are probably better off having ffs and ffk, for instance.Inarguably yes.
[/left]
 [/center][/left]

---

### Post by LordHunter317 on 2005-05-06
[QUOTE=ssam]would this work
```
#!/bin/bash
killall firefox || firefox &
```[/quote]Actually, it wouldn't work on Ubuntu.  Unless they've changed something from debian, you'd have to do:```
#!/bin/sh
killall firefox-bin || firefox &
```and even then, you're not really guaranteed that script will do what you want.  You'd need something more complicated to ensure firefox will properly exit and you'll only start firefox when one was killed, you only kill the right process, etc.

The idea is right though.  I'm not sure it's the best implementation though.

---

### Post by ssam on 2005-05-06
oops yes, for got that /usr/bin/firefox is just a big bash script that set up some stuff and runs /usr/lib/mozilla-firefox/firefox-bin

```
#!/bin/sh
killall firefox-bin || firefox &
```

does seem to work for me.

there should only be one instance of firefox-bin, because /usr/bin/firefox send any new request to the existing instance of firefox-bin.

maybe it is worth having a look through /usr/bin/firefox to see if it has any useful functions to help solve this problem.

maybe there is a friendlier signal that can be sent to firefox to make it exit cleanly.

what is the reason for needing this DarkGreen16 ? are you just using firefox as an example?

---

### Post by LordHunter317 on 2005-05-06
> **ssam]there should only be one instance of firefox-bin, because /usr/bin/firefox send any new request to the existing instance of firefox-bin.[/quote]Firefox supports profiles, and as such, you can have multiple instances of firefox running.  

Sure /usr/bin/firefox won't easily give you that, or if it will, I don't know how to do it said:**
> maybe there is a friendlier signal that can be sent to firefox to make it exit cleanly.SIGTERM makes it exit just fine, unless it's hung, and then what can you do?

---

### Post by mendicant on 2005-05-06
[QUOTE=LordHunter317]They put the file in /var/run.
[/QUOTE]

Right, but users can't so I modified it a bit--perhaps I should have said "follow (in spirit)".

> 
A command that does different things based on prior state is confusing to a user.  


If there's only a single user using this script, then go ahead.  I wouldn't personally do it because I think it is a bad idea, but there's no harm in letting people try things out for themselves.

---

### Post by DarkGreen16 on 2005-05-07
Sorry I should have used a real example for this instead of firefox because im not sure if the firefox-bin would apply to what im trying to do.

Basically i'm trying to bind a key that will turn the LCD backlight off...using a program I am able to do this (dpms)

So when I do dpms off it turns the backlight off when I do dpms on it turns it on...there may be an easier way to do this and im pretty sure there is considering i recently found a lid.sh script that turns my backlight off when I close the lid.

I come from a world of windows where I even programmed in VB some.

In vb it would be very easy just If dpms = on then dpms = off else dpms = on end if

Now that i know ubuntu is capable of turning off my backlight without any extra programs it would be nice to figure out how to turn it off and back on with one button.

---

