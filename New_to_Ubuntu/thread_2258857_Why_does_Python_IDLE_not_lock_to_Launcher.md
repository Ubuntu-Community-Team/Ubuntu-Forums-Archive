---
title: "Why does Python IDLE not lock to Launcher?"
date: 2014-12-31
forum: New to Ubuntu
---

### Post by renbri on 2014-12-31
If I open IDLE, either from the terminal or the Dash, the Python icon comes up on the launcher. But if I right click on it and select 'Lock to Launcher', it doesn't seem to work; i.e when I quit IDLE the icon on the launcher disappears. 
No big deal, since I can quickly access it via the Dash. It just seems odd. Am I missing something?

---

### Post by Maximilian_F._Blas on 2014-12-31
What version of Ubuntu do you use? and do you use a different flavor like kubuntu?

---

### Post by renbri on 2014-12-31
G'day Max, 
I'm on Ubuntu 14.04.1 LTS  (a raw beginner, I might add).

---

### Post by flaymond on 2014-12-31
Here the manual to help you -

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

Thanks

---

### Post by renbri on 2014-12-31
Mmm. Thanks for that, FC. I think it's a bit too involved for me at this stage. Rather than stuff up a working system, I'll content myself with opening IDLE via the Dash or the Terminal.
After all, my purpose is to learn some Python and I don't need the Launcher for that.
I just thought it strange that, when I right clicked on the Launcher icon, the option to lock it there was presented but didn't work.
Onwards and upwards.

---

### Post by flaymond on 2014-12-31
Why don't just pull it into your desktop?

---

### Post by raja.genupula on 2015-01-01
look like a bug to me , but wait for a while. If no proper response/answer then report a bug at launchpad.

---

### Post by jim82 on 2015-01-01
I'm new to both as well, but have had no problem locking it to the launcher. How did you install IDLE? Have you tried uninstall/reinstall?

---

### Post by flaymond on 2015-01-01
Well, if it not working, I think it's a bug..do you use the Ubuntu 14.10(Utopic Unicorn)?

---

### Post by buzzingrobot on 2015-01-01
If it creates a '.desktop' file in /usr/share/applications, or ~/.local/share/applications ('~' = your home folder) , then its icon should be retained in the Launcher.

---

### Post by renbri on 2015-01-02
Boffins and ubuntuphiles all, thank you. Via one gem or another of yours, I've got IDLE(using Python-2.7) on the Launcher, and even on the Desktop. I think the key ideas were uninstallation and reinstallation -which caused me to explore the Software Center a bit and eventually reinstall a version which stuck to the Launcher - and the tip about a '.desktop' file which caused me to look in /usr/share/applications, find the icon, copy it and paste it onto the desktop and bingo!
Now I'm wondering if I ought to be using Python3 but that's for later, I'm happy that I can now learn a bit about Python while I'm learning about Ubuntu.
I think the most daunting aspect is the seemingly haphazard taxonomy of packages and files and the sheer quantity of them This 'Dash' thing is all very well but it only invites you to launch an application or uninstall it; it doesn't tell you where it is! The command line is alluring although it presents one with so many ways to skin the cat. If I (tentatively) use a command like 'find' or 'locate' to look for the python package, I don't really know what the key file or list or sub-routine or 'package' is; I end up with  dozens of locations that contain the word 'python' and none of them seems to be especially significant.
I obviously need to do a lot more reading.
Meanwhile, stumbling and bumbling along is made a lot easier by the generous help available in this forum.
Thank you all again, and a happy 2015.

---

### Post by bab1 on 2015-01-02
> **renbri said:**
> ... Now I'm wondering if I ought to be using Python3 but that's for later, I'm happy that I can now learn a bit about Python while I'm learning about Ubuntu.

Both Python2 and Python3 are installed on Ubuntu these days.  If you use the command ***idle3*** you will get python3.  if you are just learning Python, why learn the old unsupported going forward version?  Just change your desktop file command to the later idle3 and have move on.  ;-)
> 
I think the most daunting aspect is the seemingly haphazard taxonomy of packages and files and the sheer quantity of them.

That is the ethos of Linux and open source in general.  Everyone has a better mousetrap.  
> 
This 'Dash' thing is all very well but it only invites you to launch an application or uninstall it; it doesn't tell you where it is!

As far as Dash is concerned; you don't need to know where the executable is.  Even from the command line you don't need to know.  
> 
The command line is alluring although it presents one with so many ways to skin the cat. If I (tentatively) use a command like 'find' or 'locate' to look for the python package, 
If you want to know where the executable is use the command: whereis (as in)```
whereis idle

whereis idle3
```...psssst, there in the same directory! > 
I don't really know what the key file or list or sub-routine or 'package' is; I end up with  dozens of locations that contain the word 'python' and none of them seems to be especially significant.  I obviously need to do a lot more reading.

The only thing that is significant is the executable for the application.  The rest is the supporting libraries or documentation (the man pages)

[COLOR="#0000FF"]**Edit:** Here is a [general guideline of the Linux file system]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").  It might help you to understand some of the directory layout.  Remember that this is just a guideline and some folks just don't understand (care) enough to follow it.[/COLOR]

---

### Post by renbri on 2015-01-03
I find your comments incisive and interesting, bab1. However, my aging synapses were a bit strained by some of it.
Of course, as an ex-windows slave, I expect an executable file to have a .exe extension but in this system I gather there can be various extensions or none at all; ergo, I will not recognise the key 'executable' by name and must assume that the 'whereis' command with no conditions or arguments will find only the executable. 
When I typed 'whereis idle', it returned  'idle: /usr/share/man/man2/idle.2.gz', which looked odd to me. I seem to associate .gz with a compressed file and I thought 'man' was a word reserved for the manual that explains everything else. Be that as it may, when I typed whereis idle3 it returned only ' idle3' (which I later discovered meant that I needed to install idle3). But when I entered 'locate idle3' it returned  '/usr/share/app-install/desktop/idle3: idle3.desktop' (even before I had installed idle3?)
Please don't trouble to explain all this; I'm only telling you because it didn't seem to quite square with your last comment and you might want to review it.
I shall take your advice and install the idle3 version. I presume this does not affect very much the way one writes the code although, since I'm barely past for and while loops, I needn't worry(?) 
Thanks for the link. Hooroo from down under.

---

### Post by bab1 on 2015-01-03
It should look like this  for idle```
 **whereis idle**

idle: /usr/bin/idle /usr/bin/X11/idle /usr/share/man/man1/idle.1.gz /usr/share/man/man2/idle.2.gz
bruce@malibu:~$ 

```

For idle3 it should look like this```
**whereis [COLOR="#FF0000"]idle3[/COLOR]**
idle3: /usr/bin/idle3 /usr/bin/X11/idle3 /usr/share/man/man1/idle3.1.gz

```

Whereis for python```
whereis python
python: /usr/bin/python2.7 /usr/bin/python /usr/bin/python3.2 /usr/bin/python2.7-config /usr/bin/python3.2mu /etc/python2.7 /etc/python /etc/python3.2 /usr/lib/python2.7 /usr/lib/python3.2 /usr/bin/X11/python2.7 /usr/bin/X11/python /usr/bin/X11/python3.2 /usr/bin/X11/python2.7-config /usr/bin/X11/python3.2mu /usr/local/lib/python2.7 /usr/local/lib/python3.2 /usr/include/python2.7_d /usr/include/python2.7 /usr/include/python3.2mu /usr/share/python /usr/share/man/man1/python.1.gz
```

Whereis python3```
whereis python3
python3: /usr/bin/python3 /usr/bin/python3.2 /usr/bin/python3.2mu /etc/python3 /etc/python3.2 /usr/lib/python3 /usr/lib/python3.2 /usr/bin/X11/python3 /usr/bin/X11/python3.2 /usr/bin/X11/python3.2mu /usr/local/lib/python3.2 /usr/include/python3.2mu /usr/share/python3 /usr/share/man/man1/python3.1.gz

```

The first entry is the executable (for python3 it is /usr/bin/python3).  This is the same directory that python and  idle and python3 and idle3 reside in.  To see the entire listing for that directory try this```
ls -l /usr/bin
```...if you want to limit the display to a certain pattern you can pipe the output to grep like this```
ls -l /usr/bin | grep python
```...this show only the listings with python in the name.  You can substitute the term idle for python and list that instead.

If you don't get this same type of output then something is not correct.  Python and python3 have coexisted on Ubuntu since 12.04.  

If you want you can post the output of ```
ls -l /usr/bin | grep python
```...and ```
ls -l /usr/bin | grep idle
```
Let's see if you can start with a stable correct environment.  Python is going to be enough to learn without the distractions that can come from a wounded OS install.

---

### Post by renbri on 2015-01-03
brian@brian-Inspiron-545s:~$ whereis idle
idle: /usr/share/man/man2/idle.2.gz
brian@brian-Inspiron-545s:~$ whereis idle3
idle3: /usr/bin/idle3 /usr/bin/X11/idle3 /usr/share/man/man1/idle3.1.gz
brian@brian-Inspiron-545s:~$ whereis python
python: /usr/bin/python3.4m /usr/bin/python /usr/bin/python2.7 /usr/bin/python3.4 /etc/python /etc/python2.7 /etc/python3.4 /usr/lib/python2.7 /usr/lib/python3.4 /usr/bin/X11/python3.4m /usr/bin/X11/python /usr/bin/X11/python2.7 /usr/bin/X11/python3.4 /usr/local/lib/python2.7 /usr/local/lib/python3.4 /usr/include/python2.7 /usr/share/python /usr/share/man/man1/python.1.gz
brian@brian-Inspiron-545s:~$ whereis python3
python3: /usr/bin/python3 /usr/bin/python3.4m /usr/bin/python3.4 /etc/python3 /etc/python3.4 /usr/lib/python3 /usr/lib/python3.4 /usr/bin/X11/python3 /usr/bin/X11/python3.4m /usr/bin/X11/python3.4 /usr/local/lib/python3.4 /usr/share/python3 /usr/share/man/man1/python3.1.gz
brian@brian-Inspiron-545s:~$ 


Here's what I got. It all looks similar to your specification except for the whereis idle, which is reduced to your first segment.
I've now got idle3 on the desktop and on the Launcher(where it tells me it's using the Python 3.4.0 shell). Belt and braces I know but I'm green and unsteady.
It seems to be working okay. Do I need to go a-piping and a-grepping or can you now give me the nod?
(It would be nice to recover the feeling that I know what I'm trying to do!)
Thanks in advance

---

### Post by bab1 on 2015-01-03
> **renbri said:**
> 
```
brian@brian-Inspiron-545s:~$ whereis idle
idle: /usr/share/man/man2/idle.2.gz
```

Looks like idle is not installed, but the man pages are.  Did you un-install idle? 
> 
```
brian@brian-Inspiron-545s:~$ whereis idle3
idle3: /usr/bin/idle3 /usr/bin/X11/idle3 /usr/share/man/man1/idle3.1.gz
```

Here we show idle3 and its gui configuration plus man the pages.
> 
```
brian@brian-Inspiron-545s:~$ whereis python
python: /usr/bin/python3.4m /usr/bin/python /usr/bin/python2.7 /usr/bin/python3.4 /etc/python /etc/python2.7 /etc/python3.4 /usr/lib/python2.7 /usr/lib/python3.4 /usr/bin/X11/python3.4m /usr/bin/X11/python /usr/bin/X11/python2.7 /usr/bin/X11/python3.4 /usr/local/lib/python2.7 /usr/local/lib/python3.4 /usr/include/python2.7 /usr/share/python /usr/share/man/man1/python.1.gz
```
This is listing both Python 2 and 3 > 
```
brian@brian-Inspiron-545s:~$ whereis python3
python3: /usr/bin/python3 /usr/bin/python3.4m /usr/bin/python3.4 /etc/python3 /etc/python3.4 /usr/lib/python3 /usr/lib/python3.4 /usr/bin/X11/python3 /usr/bin/X11/python3.4m /usr/bin/X11/python3.4 /usr/local/lib/python3.4 /usr/share/python3 /usr/share/man/man1/python3.1.gz
```
This is listing only Python3>  

Here's what I got. It all looks similar to your specification except for the whereis idle, which is reduced to your first segment.

I've now got idle3 on the desktop and on the Launcher(where it tells me it's using the Python 3.4.0 shell). Belt and braces I know but I'm green and unsteady.
It seems to be working okay. Do I need to go a-piping and a-grepping or can you now give me the nod?
(It would be nice to recover the feeling that I know what I'm trying to do!)
Thanks in advance
If you are only going to learn Python3 and use idle3 then you are good right here.  The only thing that appears to be missing is the idle IDE.  IMHO I'd just go with what you have right now.  The OS uses both python2 and Python3 for various applications but that's no concern you need worry about.

One more lesson -- To keep the formatted fixed width text from the terminal output you should post the output between the [noparse]```
 
```[/noparse] blocks.  This can be done by first clicking on the [SIZE=4]**#**[/SIZE] icon at the top of the *Advanced Reply* editor and pasting the text between the blocks.  This helps maintain the readability.

It looks like you're ready to start your Python3 coding adventures.  Good luck!

---

### Post by Topsiho on 2015-01-03
Python2 (or Python) and Python3 are not so different afterall. Many Python scripts in Ubuntu are still in Python, but more and more are in Python3 or moved to Python3, which is the future. If you learn Python, you should IMHO learn Python3.
Python3 is easier than Python, as you can see:

python:  6/4
1   <= integer arithmetic

python3: 6/4
1.5

The print statement is different:

python: print 'python is great'    <===  print is a statement

python3: print('python3 is greater')   <===  print is a function, and the parameters must be between round brackets.

Further, in Python3, python is cleaned up from a lot of historically accumulated eh, I don't want to say "rubbish", but Python contains a lot of noise, which is removed in Python3.

I only mentioned a few differences, the most apparent ones.

Python3 is easier to learn, AND it is the future.

Topsiho

---

### Post by renbri on 2015-01-03
Brilliant.  Thanks to all the help I've had here, I think I'm finally off and running. 
I'm glad you mentioned that print function, T. I discovered that by trial and error and thought I must have lost a few more neurons.
I suppose that, having opted for the newer system, I'll have to be wary when consulting the odd Python text from, say, the library, 
although it sounds like this won't be too much of a problem. 
I've just discovered   [https://wiki.python.org/moin/Python2orPython3](https://wiki.python.org/moin/Python2orPython3) which should help to keep me on track.
Many thanks yet again.
What a forum!
If I had a couple of wet fish I'd do a little dance.
Hooroo

---

