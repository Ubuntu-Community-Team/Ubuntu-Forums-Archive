---
title: "using &amp; to pass control back to terminal"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-10-16
When I open a file with the terminal, I can't use the terminal again until I close the file. And if I close the terminal it closes the file when I don't want it to.

I read that I could use "&" after the command. But it doesn't seem to work.

My terminal is LXTerminal 0.1.11 Terminal Emulator for the LXDE project. Copyright 2008-2011

---

### Post by The Cog on 2012-10-16
By open the file, I assume you mean you are launching some program to work on the file, e.g. "gedit whatever.txt"
in which case, this should do what you want:
```
nohup gedit whatever.txt > /dev/null &
```

---

### Post by Kevin McCready on 2012-10-16
thanks. yes that's what I wanted to do.

I just tried it a minute ago and it worked. But I still had to do a control-C to get control of the terminal again.

---

### Post by DuckHook on 2012-10-16
Please provide example of the way you use the "&".

---

### Post by Kevin McCready on 2012-10-17
nohup leafpad /home/k/Documents/proust.txt > /dev/null &

then the terminal says:

nohup: ignoring input and redirecting stderr to stdout

I've noticed that I can still do other commands in the terminal after that, but the prompt is suppressed and invisible until I do control-C

---

### Post by stinkeye on 2012-10-17
Using **& disown** allows me to get the terminal prompt back and not close 
the application when the terminal is closed.
Eg
```
gedit ~/.conkyrc & disown
```

---

### Post by NikTh on 2012-10-17
> **stinkeye said:**
> Using **& disown** allows me to get the terminal prompt back and not close
 
Me too . +1 , but maybe needs to use Ctrl+C after this command (if its a graphical app).

---

### Post by Kevin McCready on 2012-10-17
thanks
& disown  
worked for txt and image files!!!

---

### Post by The Cog on 2012-10-18
Thank you so much stinkeye. 
I have in the past tried a number of times to & a process and then disown it. like this:
xeyes & ; disown
xeyes & && disown
I never got it right. It's even easier than everything I tried.

---

