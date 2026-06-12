---
title: "Temperature  script"
date: 2009-12-23
forum: Programming Talk
---

### Post by OlyPerson on 2009-12-23
So I started using gnome-shell and there is no core temperature applet so I thought I'd make a script that did something like this.

Basically what I want is something that looks like
```
Your computer's temperature is 55 C
```
And that temperature would update every so many seconds.

I've actually never really done any bash scripting, so this will be hard for me.  I can make the output look like this:
```
--------------------------------
Your computer's temperature:
temperature:             56 C
temperature:             55 C
temperature:             55 C
^Z
[4]+  Stopped            
```
but I can't make the output of cat cat /proc/acpi/thermal_zone/TZ00/temperature only output "56 C" instead of the whole line.
I also don't know how to just update the line instead of printing out a new line.

Any help would be appreciated!
I plan on making this a project of mine so eventually I'd like to make it more advanced, maybe showing a little graph or something or some visual representation of the temperature (like htop has a visual representation of top's stuff).

Thanks again for any help.

---

### Post by andrewc6l on 2009-12-23
For the first part (just getting the temperature instead of the whole wad) try

cat /proc/acpi/thermal_zone/TZ00/temperature | sed 's/^.* //'

which says "replace everything from the start (^) up to the last space character (.* ) with nothing (//)".

For overwriting, you'll probably want to look into ANSI/VT-100 terminal commands. Here's a link:
[http://ascii-table.com/ansi-escape-sequences.php](http://ascii-table.com/ansi-escape-sequences.php). Actually, you might decide to use something more than bash - C has curses for full-screen programs, and other languages often interface to curses.

---

### Post by ib.lundgren on 2009-12-23
If you intend to make it more advanced later on I would suggest doing it in python and not bash.

This little snippet will get and print your temp:
[PHP]
# [-5:-2] basically means as the first 3 of the last 5 characters in
# temperature:             56 C

with file("/proc/acpi/thermal_zone/TZ00/temperature") as f:
	print f.readline()[-5:-2][/PHP]

Check out python-daemon [http://pypi.python.org/pypi/python-daemon](http://pypi.python.org/pypi/python-daemon) too.

---

### Post by OlyPerson on 2009-12-23
> **ib.lundgren said:**
> If you intend to make it more advanced later on I would suggest doing it in python and not bash.

This little snippet will get and print your temp:
[PHP]
# [-5:-2] basically means as the first 3 of the last 5 characters in
# temperature:             56 C

with file("/proc/acpi/thermal_zone/TZ00/temperature") as f:
	print f.readline()[-5:-2][/PHP]

Check out python-daemon [http://pypi.python.org/pypi/python-daemon](http://pypi.python.org/pypi/python-daemon) too.

What would the advantage of using python over bash be?  I'm unfamiliar with python but from what I know of it I guess it's supposed to be easy to learn, right?

---

### Post by Can+~ on 2009-12-23
> **OlyPerson said:**
> What would the advantage of using python over bash be?  I'm unfamiliar with python but from what I know of it I guess it's supposed to be easy to learn, right?

I would say that, yes.

Bash scripting is also easy if you stick with the basics, but it gets rather complicated, since it has the idea of being minimal in terms of syntax, so there's quite a lot of syntax to remember.

---

### Post by geirha on 2009-12-23
Maybe you want something like this?
```

while read _ temp < /proc/acpi/thermal_zone/TZ00/temperature; do
    printf "Your computer's temperature is %5s\r" "$temp"
    sleep 1
done

```

The '\r' (carriage return) returns the cursor to the start of the line, so it will simply overwrite the same line over and over.

For learning bash-scripting, I recommend this guide: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by OlyPerson on 2009-12-23
Ok, so I've got a basic script here that shows the current temp, average temp, and the time elapsed since I started the recording.
```
#! /usr/bin/python
# Outputs temperature in 2 second intervals

import time

interval = 2 			# Interval of time between updates (in seconds).
updates = 0				# Total times updated.
total_temp = 0
time_elapsed = 0

print "Current  |   Average  |  Elapsed"

while 1==1:
	with file("/proc/acpi/thermal_zone/TZ00/temperature") as f: 
		temp = int(f.readline()[-5:-2])

	total_temp += temp
	updates += 1
	average_temp = total_temp / updates
	time_elapsed += interval

	print "   " + str(temp) + "          " + str(average_temp) + "         " + str(time_elapsed) + " sec"
	time.sleep(interval)
```

Works how I expect it to, but I'd like it to update the number not print out a new line each time, so should I look into what andrewc6l talked about or something different with python?

And also, is making a GUI easy in python?

---

### Post by OlyPerson on 2009-12-23
Ok never mind the updating, I got it using sys.stdout.write() and sys.stdout.flush().

But now I have a couple other questions regarding that and something else.  Does anyone know how to do either of the following:


1) When you want to flush multiple lines, how do you do this?  Right now the output looks like:
```
--------------------------------
Current  |   Average  |  Elapsed
--------------------------------
   56    |     56.0     |   2 sec
   56    |     56.0     |   4 sec
   56    |     56.0     |   6 sec
   56    |     56.0     |   8 sec
   56    |     56.0     |   10 sec
|||||||||||||||||||||||||||||||||^Z
[16]+  Stopped                 python temp.py

```
Where the |||| is supposed to be a graph representing temperature that updates, and so do the numbers.  The bar gets flushed each time but the numbers don't.


2) How do I print something so that it always lines up correctly?  Here's what I'm talking about:
```
--------------------------------
Current  |   Average  |  Elapsed
--------------------------------
   56    |     56.0     |   2 sec
   56    |     56.0     |   4 sec
   57    |     56.33     |   6 sec
   57    |     56.5     |   8 sec|
   56    |     56.4     |   10 sec
   56    |     56.33     |   12 sec
|||||||||||||||||||||||||||||||||^Z
[18]+  Stopped                 python temp.py

```
See how the |'s don't line up? I want them to line up even when it's 56.0 or 56.33.  And yes I could also make it be like XX.YY but I was wondering how to make them always spaced right without that.

Thank you to anyone who can help again!

---

### Post by kwyto on 2009-12-23
look into formatting output in python,
[http://docs.python.org/tutorial/inputoutput.html](http://docs.python.org/tutorial/inputoutput.html) , this should help.

---

### Post by OlyPerson on 2009-12-24
> **kwyto said:**
> look into formatting output in python,
[http://docs.python.org/tutorial/inputoutput.html](http://docs.python.org/tutorial/inputoutput.html) , this should help.

Thank you!  That helped out quite a bit, I got the formating to look pretty much how I like, at least with one line.
```
---------------------------------
Current  |   Average  |  Elapsed
---------------------------------
   57         56.50        28    ||||||||||||||||||||||||||||||||||                |
```

I still can't figure out how to have more than one line that updates.  My output bit looks like this:
```
sys.stdout.write("\r" + '{0:5} {1:13.2f} {2:9}    {3:50}{4}'.format(temp, average_temp, time_elapsed, bar, "|"))
sys.stdout.flush()
```

I would think doing two lines would look like:

```
sys.stdout.write("\r" + '{0:5} {1:13.2f} {2:9}    {3:50}{4}'.format(temp, average_temp, time_elapsed, bar, "|"))
sys.stdout.flush()
sys.stdout.write("\rhello")
sys.stdout.flush()
```
But that doesn't work and I still can't find any documentation on it :(  What I want the output to look like is:
```
---------------------------------
Current  |   Average  |  Elapsed
---------------------------------
   57         56.50        28    ||||||||||||||||||||||||||||||||||                |
Cpu speed: 800.0 MHz
```

---

### Post by geirha on 2009-12-24
Well, you can send ansi escapes to move the cursor back up to line x and such, but you might as well learn curses which abstracts that away. [http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

---

### Post by OlyPerson on 2009-12-25
> **geirha said:**
> Well, you can send ansi escapes to move the cursor back up to line x and such, but you might as well learn curses which abstracts that away. [http://docs.python.org/library/curses.html](http://docs.python.org/library/curses.html)

Thank you very much for that!  I've been playing with it for a bit now, and more or less get the gist of it except for what is going on with colors.

When I use an if statement to determine the color of the text I want to show, the lines mess up when the color changes.  Look at the attached screenshot to see what I mean.

Here's the bit of code I'm talking about that seems to mess up:
```
if curses.has_colors():

	# Change the color of the graph it is above about 60 C to red
	if num_bars > 34:
		curses.init_pair(1, curses.COLOR_RED, -1)
	else:
		curses.init_pair(1, curses.COLOR_GREEN, -1)

	# Print it out the numeric statistics
	screen.addstr(4, 4, str(temp))				# Current temperature
	screen.addstr(4, 16, str(average_temp))			# The average temperature
	screen.addstr(4, 30, str(time_elapsed))			# Time elapsed since initiation

	# Print out the graph
	screen.addstr(5, 2, "-"*49)				# Space filler
	screen.addstr(5, 50, "|")				# The | at the end
	screen.addstr(5, 2, bars, curses.color_pair(1))		# The important part that actually changes
	
screen.refresh()	
```

Thanks if anyone knows why those lines are messing up :confused:

---

