---
title: "Script for recognising strings in a logfile"
date: 2006-04-10
forum: Programming Talk
---

### Post by draenor on 2006-04-10
Hi, 

I want to either make or preferably find (I'm guessing someone else already thought of this) a program/script to constatly read from a log (just like root-tail) and display it's result whenever the text matches a certain string. 

Example
I want to 'listen to' /var/log/auth.log and whenever the mask IP shows up in a line, have the program/script warn me. This way I can keep track of whenever someone is trying to SSH into my server. 

I'm hoping there's already a program that does this, but I've been unable to find one, but if there's not, what are the main sugestiones of the layout to my program ? I've not written 100 bash scripts, and I don't know perl/ruby, but I've got some c experience. 
I'm thinking of perhaps having a script run by crond which tails the log every few seconds or so and the has some kind of sctring-recognising mechanism, does this sound like a good idea ? It sounds like a bash-script to me, but let me know of your opinion. 

Thanks in advance.

---

### Post by ubernoob on 2006-04-10
it is easier than you think :)
```
tail /var/log/auth.log -f | grep "Failed password"
```

---

### Post by draenor on 2006-04-11
Indeed that's a good solution. I need to take it one step further though ..
It seems as I need to use --line-buffered to get any output at all to cut -b ....

The following is what I had in mind, but it doesn't produce any output in text.log
```
tail -f /var/log/auth.log -n 12 | grep ssh --line-buffered | cut -b 39- >> text.log
```

However, this produces direct text to standard out
```
tail -f /var/log/auth.log -n 12 | grep ssh --line-buffered | cut -b 39-
```

Why doesn't the program redirect the data to text.log? Text.log remains empty troughout several ssh attemps which should generate data in auth.log. I've heard some hints about the buffer that it doesn't redirect until it's full. But  I haven't found any way to control cut's buffer or decrease it.



The reason I'm doing this at all is so that I will generate my own log with short but precise rows containing data on SSH attemps to my computer. 
My next step is root-tail text.log and display it on the background. I've tried to use grep/cut directly with root-tail but it doesn't seem to work, as it needs to gather data all the time as the file expands.

---

### Post by thumper on 2006-04-11
Just an interesting point - have you tried **tee** instead of **>>**?

You might find that the buffering is handled differently.  The >> I think is handled by the shell / terminal whereas using tee should get it to the file soonest :)

---

### Post by draenor on 2006-04-11
Yeah, I tried tee as well. I got the same result. It seems to be stuck in the buffer until the buffer is full or something like that. 

Either way, made a way around the problem, and wrote a daemon who updates the log every five seconds, then I just root-tail that log to put the contents on my desktop. Great way to constantly be aware of anyone SSH:ing to your computer.

---

