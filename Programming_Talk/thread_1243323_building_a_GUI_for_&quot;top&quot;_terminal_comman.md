---
title: "building a GUI for &quot;top&quot; terminal command"
date: 2009-08-18
forum: Programming Talk
---

### Post by dootzky on 2009-08-18
Hey guys,

I've been developing in various languages for over 10 years now, and lately I've been testing combination of Python+GTK, and I love it.

So, this is what I wanna do, and it would really be helpful to know if some of you did something like this previously, and/or does something like this already exists, etc:

[LIST]
[*]make a GTK user interface, with top 10 most CPU% usage (similar to terminal command "top")
[*]make it possible to right-click and say just "kill" any process on the list
[*]add optional filters, for processes which are perhaps not in the "top 10", so you could find, let's say, npviewer.bin, or amarok etc (that would basically be "ps -A | grep "xxx" ", right..)
[/LIST]

so.. what are your thoughts? :)
can this be done using Python and GTK?
can I somehow utilize command line results into my GUI?

thanks for your time, I hope I'll be able to create this proggy for all of us to use! :)

cheers,
dootzky

---

### Post by credobyte on 2009-08-18
> **dootzky said:**
> 

[LIST]
[*]make a GTK user interface, with top 10 most CPU% usage (similar to terminal command "top")
[*]make it possible to right-click and say just "kill" any process on the list
[/LIST]


System Monitor clone ?

---

### Post by pepperphd on 2009-08-18
I really can't answer your questions but I can suggest somewhere to look. Assuming you know C++, gnome System Monitor has in one way or another every feature you listed.

EDIT: Credobyte beat me to it.

---

### Post by bodyharvester on 2009-08-18
just because its already done doesnt mean you shouldnt do it. i started learning python to program my own games and will soon produce something similar to all the older games, e.g. sprites and pong replicas

the experience will help you in the future so go ahead and do it

---

### Post by nvteighen on 2009-08-18
Hm... but System Monitor has an issue you might resolve: it's too big... I mean, it does too much and with some bugs... for example, it oddly substracts some memory usage due to GNOME... (compare System Monitor's output to the free command's). Yup, this means that GNOME System Monitor is more accurate when it's run under KDE that in GNOME!

A lightweight and accurate GTK+ "top" would be really great.

---

### Post by Nevon on 2009-08-18
You can get the output of system commands using the subprocess module, and more specifically the call method. Using that you can pipe the usual stdout (standard terminal output) to your Python application and parse it there. However, you're going to run into problems when doing this if the command you're going to run takes any longer to complete than a second or two, you probably need to thread your application so that the system command is run in one thread, and the parsing and GUI is being run in another. If you don't, the GUI is going to freeze up.

---

### Post by credobyte on 2009-08-18
> **nvteighen said:**
> Hm... but System Monitor has an issue you might resolve: it's too big... I mean, it does too much and with some bugs... for example, it oddly substracts some memory usage due to GNOME... (compare System Monitor's output to the free command's). Yup, this means that GNOME System Monitor is more accurate when it's run under KDE that in GNOME!

A lightweight and accurate GTK+ "top" would be really great.

If it would be that *easy* to fix it, wouldn't it have been already done ( and I'm not against the idea by itself .. only *doing nothing* is useless ) ?

---

### Post by bodyharvester on 2009-08-18
> **credobyte said:**
> If it would be that *easy* to fix it, wouldn't it have been already done ( and I'm not against the idea by itself .. only *doing nothing* is useless ) ?


Linux is so secure because nobody gets "root" access as default. Windows has only recently figured that little security blunder out.:lolflag:

---

### Post by credobyte on 2009-08-18
> **bodyharvester said:**
> Linux is so secure because nobody gets "root" access as default. Windows has only recently figured that little security blunder out.:lolflag:
Really ? Default user is always in the list of sudoer's ( which is pretty much all you'll ever need ) 8-[

---

### Post by bodyharvester on 2009-08-18
> **credobyte said:**
> Really ? Default user is always in the list of sudoer's ( which is pretty much all you'll ever need ) 8-[

what i meant was i cant wreck ubuntu the way i did xp, although that may have been the virus's and stuff crawling around when i had it, it was tough to tell :p

if Windows had sudo, actually does win7 have it? my knowledge of windows slipped out of my head after i was adopted by ubuntu :)

---

### Post by pelle.k on 2009-08-18
> for example, it oddly substracts some memory usage due to GNOME... (compare System Monitor's output to the free command's)
Unless our setups differ on some point, i dont see whats wrong with gnome system monitor on my machine anyway.
Maybe you meant you want to see the memory usage with cached memory? I'm not sure thats very relevant, since it can be freed at any point in time (i.e. when it's necessary). But to each his own i guess :)

---

### Post by doas777 on 2009-08-18
> **credobyte said:**
> System Monitor clone ?
nah. presumably it would operate without signifigantly distorting the figures it attempts to show.
right now, gsm is taking up between 12 and 44% CPU on my amd64 dualcore, while measuring basically nothing.

---

### Post by johnl on 2009-08-18
Hi,

You can either use a library (libproc) or parse the contents of the /proc filesystem yourself to retrieve this info. 

Each running process has a folder in /proc in the form /proc/<pid>/ which contains a symlink to the program, the cmdline that program was started with, and anything else you want to know about that process.

---

### Post by slavik on 2009-08-18
One thing to keep in mind:

a single shared object (dynamic library) will be loaded into memory once for all programs that use it. So now you have a problem ... how do you count that memory when look at a list of processes? That's why there is a resident and virtual columns. :)

---

### Post by dootzky on 2009-08-19
Hi guys, it's good to see you all here so active and looking alive, that's cool! :)

Alright, so, yeah, basically, the task would be to create lightweight utility for monitoring and alerting you of CPU consuming processes, with option to kill it or restart it. So, yeah - basically a light GTK GUI for the "top" command, and the "kill process" option like the System Monitor has it now. 

I'll look into it this weekend, I can't promise anything, but Python should be easy and fun way to do this, so we'll just wait and see what's gonna happen from there. :) 

Oh, yes, I never really learned or loved threads (although I've used them many many times earlier), so that's one of the reasons I've moved on to web-development, using PHP and Python when needed ^_^ 

Thank you all for your help and insights, 
talk to you soon,
dootzky

---

