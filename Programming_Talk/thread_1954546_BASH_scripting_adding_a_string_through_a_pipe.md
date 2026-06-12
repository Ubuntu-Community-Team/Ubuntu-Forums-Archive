---
title: "BASH scripting: adding a string through a pipe"
date: 2012-04-08
forum: Programming Talk
---

### Post by oferst on 2012-04-08
Hello, newbie here :)

I have homework to do about BASH scripting and I need your help with something.

let's say I have a directory named "logs" and inside I have files, which among them there files named "n.testInOut.log" where 'n' is a number, starting from 1.

I have to do the next, all in 1 line, without using ; once (which means using a pipe):
of all the files in the log directory that end with inout.log I have to print the name of the file that was last modified, including the name of the directory it's in (in this case is 'logs').

for example:
if 1.inout.log was last modified I should get the next output:
```
logs/1.inout.log
```now there's this solution I thought of (I run the script from the parent directory of 'logs' directory):
```
ls -ltR logs | grep inout.log | head -1 | cut -c47-
```but I don't know hot to get the directory to be printed too.

Your help will be much appreciated, please!

---

### Post by The Cog on 2012-04-08
How about passing your output through sed and replacing the start of the line with "logs/"? Somehow, that feels like a cheap cheat to me, but it will give you the required output.

It might actually be better to use awk than your current approach, but I have to admit that I haven't learned any awk so I can't be sure on that.

---

### Post by Vaphell on 2012-04-08
is logs a flat dir or do you need to go recursive? if it's flat, you don't need -R.
You don't need -l too - you don't care about details, only the order matters and that is taken care of by -t.

also you don't have to ls | grep when you can use builtin shell glob in ls (eg logs/*inout.log)

---

### Post by oferst on 2012-04-08
Alright, thanks Vaphell :)

---

### Post by sisco311 on 2012-04-08
I'd use GNU find & GNU sort 

Check out BashFAQ 003 (link in my signature).

---

