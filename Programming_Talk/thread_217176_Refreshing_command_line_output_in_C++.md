---
title: "Refreshing command line output in C++"
date: 2006-07-16
forum: Programming Talk
---

### Post by Randomskk on 2006-07-16
Hey
I'm making a C++ program, and after outputting some text (and getting some input), I want it to stay on one line where it shows a different message.
The program is related to parallel ports, basically I want this last line to say whether the input is high or low.
I've got the high/low code done, but I don't know how I can make the program loop and change the line each time it does so.

I could get it so that it keeps outputting the value, a new line, the value again etc but that'd flood the terminal, so I'm looking for something that just keeps the value on one line and updates just that line.

I can clear the whole screen with system("clear"); (although I don't know if that's the best way to do it :P), but no idea how to clear a single line.

How would I go about doing this?
(by the way, the program is at [http://randomskk.net/uploads/par/par.html](http://randomskk.net/uploads/par/par.html))

Thanks

---

### Post by thumper on 2006-07-16
I think this depends on how the terminal program interprets line endings, but I think that one way of doing this is to use a 'carriage return' without the 'line feed' in old typewriter speak.  Try '\r' instead of '\n' or endl.

In order to flush try ```
std::cout << "hello \r" << std::flush << "world";
```

---

### Post by Randomskk on 2006-07-16
Sweet, thanks. This works, although the cursor jumps all over the place. (check the code at [http://randomskk.net/uploads/par/par.html](http://randomskk.net/uploads/par/par.html))
I guess putting a wait in should stop the cursor jumping?
If so, what's the C++ to wait, say, 10ms?

---

### Post by Randomskk on 2006-07-16
Alright, I changed the code to only update it when the status changes, thus eliminating the blinking cursor problem.
[http://randomskk.net/uploads/par/par.html](http://randomskk.net/uploads/par/par.html)

Thanks for the help, that \r is what did it! :P

---

### Post by GeoMX on 2006-07-16
Thanks for sharing your code! I have one question tough, do you know how to avoid the need for root?

Regards,
JJ (Geo).

---

### Post by Randomskk on 2006-07-16
I do this:
$ g++ par.cpp
$ sudo ./a.out

However, you can also do this:
sudo chmod a+s a.out
Then, you can just do this:
./a.out
NOTE!!! The chmod a+s a.out command means a.out runs as root, no matter who runs it. A better idea would be u+s, then chown <username> <file>.
That way, only the person who owns the file can run it as root.

edit:
Oh, and out of interest, do you do stuff with LPT?
If so, I'm working towards one big project (with a GUI) for doing all sorts of fun things with it; watch out for it sometime on the HowTo section :P

---

### Post by GeoMX on 2006-07-16
Thanks for the quick reply!

Thanks for the comments, I already ran your code using sudo :). My question was towards enabling users without administration privileges to run it, or, how do non administrator users have access to the LPT port?

And yes, I'm really interested in some LPT stuff, I haven't done anything but I'm looking for information, code (and advice :)) for doing it on Linux (I've done some simple stuff in Windows).

Of course, I'll be looking forward to reading your HowTo (I'm checking wxWidgets as my possible GUI library).

Regards.

---

### Post by Randomskk on 2006-07-16
The "sudo chmod a+s a.out" will work nicely for letting any user run the program as root, thus having the rights to access the parallel port.

Seeing as you're interested, you may find this helpful:
[http://ubuntuforums.org/showthread.php?t=158265](http://ubuntuforums.org/showthread.php?t=158265)

I wrote it a while ago, it's a complete LPT control thing mainly using BASH scripts, and it's not that nice (which is why I'm re-doing the whole thing in C++ as I learn) but it works fairly well, you get two LEDs to alternate on new email, two on new RSS, and four to give you a CPU load status / HDD full status.
I've got instructions there for making the hardware and then using my BASH scripts.

By the way, if you use KDE, Qt Designer's pretty good for GUIs - although I guess if you use GNOME, something more like GTK+ or wxWidgets would be better.

---

### Post by GeoMX on 2006-07-16
> **Randomskk said:**
> 
Seeing as you're interested, you may find this helpful:
[http://ubuntuforums.org/showthread.php?t=158265](http://ubuntuforums.org/showthread.php?t=158265)

I wrote it a while ago, it's a complete LPT control thing mainly using BASH scripts, and it's not that nice (which is why I'm re-doing the whole thing in C++ as I learn) but it works fairly well, you get two LEDs to alternate on new email, two on new RSS, and four to give you a CPU load status / HDD full status.
I've got instructions there for making the hardware and then using my BASH scripts.

Thanks for the link, I'll have a look at those scripts, tough I'm more interested in C++ :). Also, the link you posted ([http://www.epanorama.net/circuits/parallel_output.html#input](http://www.epanorama.net/circuits/parallel_output.html#input)) seems to have lots of good information!

> **Randomskk said:**
> 
By the way, if you use KDE, Qt Designer's pretty good for GUIs - although I guess if you use GNOME, something more like GTK+ or wxWidgets would be better.
Yes, I'm using GNOME, I've been reading wxWidgets docs, I already created a small app for testing it, (but Qt Designer looks great!).

---

### Post by LordHunter317 on 2006-07-16
Instead of running the application as root, it's far smarter to change the permissions on the parallel port so users have access.  By default, permissions are given to anyone in the 'lp' group, but you'd probably want to change that.

---

