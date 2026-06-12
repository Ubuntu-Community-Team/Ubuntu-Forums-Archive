---
title: "GUI vs Terminal: your opinions?"
date: 2011-01-13
forum: Recurring Discussions
---

### Post by acplusplusprogrammer on 2011-01-13
Good morning everyone, 
this is NOT a problem but just a discussion and I want to get different people point of view. According to you what are the advantages of using the terminal compared with the GUI?

Since one week, when GRUB starts I enter in "Recovery Mode" and then "Switch to command line root with networking". After that, I stop the networking bounding and I get login shell, I put my username and password and I get all the 6 tty (from tty1 to tt6).
THEN
I just use the command line and I can say I can almost do everything:
- lynx, links2 to go on internet
- mc for file management
- cplay for music
- fbi for images
- fbgs for PDF
- nano for editing
- yacpi for temperature

and so on.

Now my questions are:
1) Why UBUNTU SERVER is given without GUI? Is there some specific reason?
2) Is Command Line Interface only safer? Faster? Or somehow better than GUI?
3) In 2011 is it really worth to learn to use at a good level the CLI? I know some things like renaming many files, moving many files it's much easier and faster with CLI, but is there someone who uses it?

OK, give me your opinion

---

### Post by Vaphell on 2011-01-13
1. server is not supposed to look nice, it needs to be fast, efficient and get the job done. Gui is an unnecessary bloat.
2. CLI has an advantage of being pretty much the same among releases, distro families or even whole linux world. Gui can be and is heavily customized so you can't make any assumptions. Also many CLI tools give you access to things that are simply not present in gui. It's also safer and more stable - more apps running = more attack vectors and more bugs.
3. CLI wins hands down when you need to perform any kind of repetitious tasks, bulk processing - you name it. Scripts are an extremely powerful tool and it's beneficial to be at least somewhat proficient. Of course it all depends on what is your usage profile - if you are a noobish user who from time to time only doubleclicks some mp3 or avi and has no desire to improve/squeeze more from his machine, then you don't have to bother, gui is good enough.

---

### Post by mixmaster on 2011-01-13
Both have their place.  You can do more or less anything you want from a command line IF you know how do get there in the first place.  If you don't, a blank box with a '$' in the top left corner is a little intimidating.

Personally I use the command line for most things but I'll fall back to the GUI if it is a new or unusual operation or if I feel the need for some handholding (GUIs frequently provide a level of sanity checking which is not present in the CLI).  

Case in point, I have a large directory full of videos.  I want to move them to subdirectories based on genre.  Fire up the file manager, click on all the action films and move then to the action subdir.  Repeat for western, drama, scifi, detective, etc.
However, if I have a directory tree full of mixed media files and I want to clean the mess up some other way (eg on the basis of media type) then using find and various wildcard combos from the command line will probably be much quicker.

---

### Post by acplusplusprogrammer on 2011-01-13
Vaphell,
so the point is that: "being simple and straightforward there are less bugs, so it's safer".
Actually I'm a newbie, I switched to Ubuntu only one year ago and in two months I will be running a server at my office. I'm not a computer scientist but an export specialist, anyhow that was the kind of stuff I wanted to know :)

Thank you for the answer.
Also to the second replyer

---

### Post by nemilar on 2011-01-13
The question "which is better, GUI or command line?" misses the mark.  They serve different purposes, and they are useful for different things.

For most day-to-day computer uses (email, media, office work (spreadsheets, word processing, etc..), web browsing, etc...) the GUI is clearly better.  I suppose an argument could be made for some things (e.g, mp3 playing without jukebox functionality), but it is overwhelmingly the case that a GUI is the proper way to perform these tasks.  There are of course still hold-outs from decades ago that will tell you vi and LaTeX is the proper way to format a document, but I think for the most part the world is in agreement that OpenOffice/Word/etc.. is the superior method.

That being said, there are certain tasks for which a command line is better suited.  While the GUI is good for productivity work, the command line is built for interacting with the computer directly.  By this I mean things like configuration, file system manipulation (moving, copying files according to a defined logic), and anything that is really more logical or technological in nature, as opposed to productivity work like email or word processing.

This helps to answer your first question - why doesn't Ubuntu Server come with a GUI?  The answer is simple: it doesn't need one.  You don't use Ubuntu Server for things like email, web browsing, word processing, or spreadsheets.  You use it to run services, which is something that is better controlled from the command line.  Adding a GUI is unnecessary.

---

### Post by ericchenry on 2011-01-13
I agree with nemilar and mixmaster, it really depends on the job at hand. If I am doing document editing or browsing the internet as a time sink, then the GUI is by far the better way.  However, if I am studying (Python, though not enough to call myself a student yet), then I prefer to work out of the CLI because for me, it is quicker, and when all I see is screens full of text, it is less distracting.

---

### Post by dmizer on 2011-01-13
> **acplusplusprogrammer said:**
> 1) Why UBUNTU SERVER is given without GUI? Is there some specific reason?
2) Is Command Line Interface only safer? Faster? Or somehow better than GUI?
3) In 2011 is it really worth to learn to use at a good level the CLI? I know some things like renaming many files, moving many files it's much easier and faster with CLI, but is there someone who uses it?

As to questions 1 and 2, the biggest reason for using a CLI only install for servers is that the GUI has tons more resources and daemons connected to a variety of ports and doing untold number of things. The more processes you have running, the more likely one of those running processes will have a hole through which your server could be compromised. If you have an internet facing server, you want to minimize your profile by minimizing the number of resources available to be compromised.

As to question 3, if you are interested in server administration of any kind (including Windows), then learning the CLI is a good idea. It can also (as you've observed) make your Linux experience much easier.

---

### Post by Aquix on 2011-01-13
They both have their place. I use a dock for most things like firefox, deluge, musicplayer, video and such. But then again it's very nice to hit F1 and have tilda bring up a fullscreen terminal window with a background image, and having 100 aliases I can do things very quickly. And aliases for scripts I make myself is very powerful and have no limit to what one can do.

One of the reasons I really like linux. You can have the best of both worlds.

---

### Post by acplusplusprogrammer on 2011-01-13
Ok,
well then. It's worth to learn the CLI very well. In two months I will set up my server and I want it to be safe! Anyhow as soon as I will be 100% operative I'll try to post something like a little guide (a collection of tools and how to use them) for people who want to be 100% terminal :p

---

### Post by medic2000 on 2011-01-13
For server i suggest you the Debian stable release. And of course the lesser applications the lesser security threats or bugs.

---

### Post by themarker0 on 2011-01-13
For server, CLI minus for SLAMPP, i found it great.

---

### Post by ilovelinux33467 on 2011-01-13
All my servers are text installs because GUI uses up system resources and because my servers are headless (only connected with network cable and power cable) there is really no point for GUI.

All my desktops and laptops are graphical and run KDE.

---

### Post by sevensevenone on 2013-03-09
Someone once said, "GUI makes simple tasks easy, CLI makes complex tasks posable." Now I'm not sure where I read/hurd that (maybe in the doc. Revolution OS) but each have their place, for newbs like me, the GUI is how I use the a computer, but the CLI is how I have fun with it. That being said, I'm hoping that ether someone will make a GUI program that helps people like me learn the fun stuff "easer" to learn.

---

### Post by MadmanRB on 2013-03-09
Its always been my belief that all CLI tools should have a GUI, after all GUI is what most non techie users operate.
Sure the command line is great and useful, but to the new user intimidating and downright confusing.

---

### Post by ibjsb4 on 2013-03-10
Hay again Pink Pony Lady :)

I think you said it all.  

I answer a lot of post and when I do, its usually in cli command.  Thats the language all flavors have in common and makes it easy to help.  But when Im just doing my own thing, its point and click.  Sooooo much easier and I just love easy :)

---

### Post by MadmanRB on 2013-03-10
I am a guy actually, I am a Brony you see.

---

### Post by ibjsb4 on 2013-03-10
Should of stuck with pink pony person..:roll: oops

---

### Post by cariboo on 2013-03-10
This is really an old thread, that should be closed, but seeing as it is back to the top of the page, I'll leave it open, to see if it helps anyone.

---

### Post by DVD-R on 2013-03-13
I have Ubuntu 9.04 server and 12.04 server.
Even when I'm in a GUI oriented system I switch over to the CLI interface to do stuff there instead of using a GUI terminal.
One can have both the GUI session as well as multiple CLI sessions going at once if one likes.
LINUX ROCKS!!!!

It would be cool if there were more CLI web apps, search engines, and file managers.
But I suspect there isn't much demand for those at this point.

---

