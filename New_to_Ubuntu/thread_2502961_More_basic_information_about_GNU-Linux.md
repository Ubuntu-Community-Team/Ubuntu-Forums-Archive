---
title: "More basic information about GNU-Linux"
date: 2024-12-08
forum: New to Ubuntu
---

### Post by jero2020 on 2024-12-08
Hi all!

I´m glad to be here, I hope my question could help anybody more than only me.

I´m an absolute begginer in GNU-Linunx world. I come from Windows where I manage to, mostly, be useful for me for many decades. Now than I´ve started with the Ubuntu World, I realized that word "useful" has become "I have no idea about the functioning of any SO".
So here I am, I´ve taken a huge 56 videos tutorial for zero-knowledge-in-Linux as a student, more than 60 pages of annotations: 1 week, full, time for studying...from the basic hardware and software structure to gedit, XE and Vi. I thought than I´ve learnt more than a few, so I tried myself for the first time: mi job partner sent me a very simple software for monitoring USB-serial port communications. I´m not going to write all my problems until I managed to make it run.
Of course, all of this was made by Terminal sessions. I visit many many pages, copy-paste code...but I still don´t a bit more than nothing about what I´m doing. What I´ve bloody learnt from this particular software is that you have to unpack it, create a directory for your where you´ll download your software, add the path to this directory to the binariy system file giving the propper command options (if not, when you restart a new Terminal and call your software you´ll take a nice clap "unknown command" on your face) and then, you´ll finally are able  to run it. Yeeeha!!...nop! I need a driver and it seems than... I have to edit a script and make it run!! (make files).
What a Quijote just for an introduction I´ve wrote! sorry. I suppose the smart people of this forum would inmediately recognize my problem: I´m missing the very basics. In fact, I asked in another forum about how to install and run modpoll (this is the name of the sotfware) and i get another slap, this time was a person how told me how massive my ignorance was, at the same time that recommend me type this in my terminal: man bash...
Well, I believe my question is even before that: where can I find enough documentation and learn by my self for answering the question: what is bash useful for? That means every is below bash. I have to learn how Linux is struturated. Where do I must begin? If I had to take high school books, I´ll do it, I´m not afraid of!. But the whole concept in a summary would be a nice beggining.

Thank you all and have a nice day

---

### Post by grahammechanical on 2024-12-08
I cannot answer your question. I joined Ubuntu Forums in 2010. I started using Ubuntu 3 or 4 years earlier. I chose Ubuntu because it had a recommendation as an operating system for ordinary people. A person did not need to be Linux geek or nurd to use Ubuntu. I have not been fooled. I still consider myself an ordinary user even though I am more experienced and educated than when I first installed Ubuntu.

You probably have more knowledge of the task you were set at work than I do. We have a Code of Conduct. We do not have to sign it to use Ubuntu but signing the Ubuntu Code of Conduct is required to give support and help on Ubuntu Forums. That Code says, among other things, Be Considerate; Be Respectful.

[https://ubuntu.com/community/ethos/code-of-conduct](https://ubuntu.com/community/ethos/code-of-conduct)

This forum is closing down and moving to Ubuntu Discourse. There will be a Code of Conduct there in addition to the Ubuntu Code of Conduct. Discussion is taking place right now.

[https://discourse.ubuntu.com/t/support-help-code-of-conduct/50460](https://discourse.ubuntu.com/t/support-help-code-of-conduct/50460)

I am sorry for the way you have been treated. 

May I make a suggestion? Put to one side your need (which is the same need a lot of us have) of becoming more knowledgeable of Linux and share with us your specific need regarding this task you are trying to carry out. We know nothing about it. What is modpoll? Where do you download it from?

In this way some of our more Linux experienced users may be able to give specific advice.

Regards

---

### Post by grahammechanical on 2024-12-08
I have just done an internet search. Are you talking about modpoll - a command line tool for polling modus registers? Installing that is scary. Especially as the developers do not seem to know about the existence of Linux.

If that is the software that you are trying to install then you will need Python installed. This should reassure you a little bit.

> Python is typically pre-installed on Ubuntu, particularly Python 3, as it's an essential part of the system for various tasks and applications.

[https://www.geeksforgeeks.org/how-to-install-python-in-ubuntu/](https://www.geeksforgeeks.org/how-to-install-python-in-ubuntu/)

Does anyone know how to check what version of Python is installed? Also I am making an assumption that you are using Ubuntu 24.04 LTS (Long Term Support). Please confirm the version of Ubuntu that you are using.

Regards

---

### Post by oldfred on 2024-12-08
It seems you have jumped into the deep end of the pool to learn to swim. That can work or you just drown. 
New users should just download programs from repository. Ubuntu checks and makes sure software is good. 

Bit more advanced is using a ppa where another user has done all the work of creating a working program.
With a ppa you have to trust that user/site is valid and has safe software.

Still more advanced is compiling your own software from code.
And then even writing your own code to create a program.

A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by yancek on 2024-12-08
Did you go through the process at the site at the link below to install on Ubuntu?

[https://www.modbusdriver.com/modpoll.html](https://www.modbusdriver.com/modpoll.html)

Did you do an online search for software to monitoring usb-serial port connections on Ubuntu?  You might find something a little easier to install and use.  The link below has some information.

[https://www.pragmaticlinux.com/2021/11/how-to-monitor-the-serial-port-in-linux/](https://www.pragmaticlinux.com/2021/11/how-to-monitor-the-serial-port-in-linux/)

>  That means every is below bash

No, it doesn't.  With regards to bash, an online search for what is bash should get you a lot of links with explanations such as the site at the link below.

 [https://opensource.com/resources/what-bash](https://opensource.com/resources/what-bash)

---

### Post by jero2020 on 2024-12-08
Thank you grahammechanical!

Did I write something wrong? Well, at least, it seems I´ve posted in the wrong place...sorry.
hey! You don´t have to apologize for that person! maybe my question was not posted properly...It doesn´t matter, somebody told there´s too selective people in Linux´s world.
My objetive is to work with Linux mostly the same as I´ve been working with Windows. Installing and running Modpoll is just an example on the (heavy) difficulties a Widows users must face when jumping to Linux but, as I´ve mentioned, this is just for Modpoll. The next missed step was try to install  the USB-Seriaport adapter driver that needs to edit a generic code and run it for install the driver: the make file...
As I´ve mentioned, my objetive is make linux my OS since my new job is closely related to communications, I´ve started to work with SCADA systems (Modpoll is commoly used by my boss for checking communications with field devices like sensors, PLC,...).
I know the proper answer my to my question is "go to high school" but maybe a book would be more available.
Linux is so different than I realized I have no idea of the functioning of any SO: why is neccessary for Linux to search any executable in just one directory? (it took me 1 week to understand this works like that). Why if I leave my terminal session and just restart another one, no changes seems to be made if you didn´t do it in a very special way, running commands as sudo, compromising your own system´s stability because you don´t know what you´re doing? Please, sudoers, this comment is not intended as a criticism of Linux, this means "I had no idea and I want to learn".
Yes, grahammechanical, I´m running Ubuntu 24.04 LTS. And, about Python, well, there´s some more story since, after some weird attemps, Terminal message told me, more or less, "if you want to run Python software better don´t make it through Terminal, you have to install and run the Python shell"...I´d really don´t remember but something about pip is not allowed but pipx yes... I myself am amazed at the technical vocabulary I had to learn to start doing something, because I didn't know how to do anything if I was taken out of the graphical environment. The problem is that, more soon than later I´ll need to reinstall Ubuntu beacause I´m breaking all meanwhile I learn......it seems I´m learning since Openoffice is working wrong from when I manually upgraded Python (Terminal told me not to do it due to phasing).
thanks so much, grahammechanical!!

---

### Post by jero2020 on 2024-12-08
Thanks so much, oldfred!!

Well, I need to be useful for a telecommunication engineer in my new job...I have a lot to study so better start from the very beggining (I have time and like it!). I know this is not simple, there´s no "for a child" explanation on why mostly all industrial servers are Linux based, why Linux normally talks as Master to Windows? I don´t care about Windows anymore, but where does it comes from this ability? How can I properly use my Ubuntu system?...I know the question is very generic but I´ve felt lost for one week, crashing every time, breaking my system...I even don´t remember wth I´d installed during that week, I even landed in a hackers web page (whaaaaaaaat???) which showed a method for just intalling Modpoll (I don´t don´t wanted it and I´m millions miles away from being a hacker!)

I´ll take a long time reading your proposed documentation and I thank you for share it. I hope not to ask too much.

Thank you all!

---

### Post by jero2020 on 2024-12-08
Wow yancek!!

I should ask you before! You´ve find the page I was looking for! I mean screen program suggestion from pragmaticlinux.com...
I´d tried modpoll from modbusdriver.com but, surely due to my zero-knowledge, I was not able to run it at the beggining. Three days later, the first time I got it (just luck), but when restarted the Terminal: where is modpoll?. 
Now, I managed to run properly another similar software (mbpoll) from command line. The problem was not how modpoll works but how to decompress-unpack-directory creation for software downloads-add directory path into system binary directory path and only then you can call modpoll. Thank  you very much yancek and thank you all: this community really answers!
Nice dreams!!

---

### Post by grahammechanical on 2024-12-08
@jero2020

One more thing

> The problem is that, more soon than later I´ll need to reinstall Ubuntu beacause I´m breaking all meanwhile I learn

I know what it is like to be in that position. I learnt how to dual boot two installs of Ubuntu. Then when I messed up one install with my attempts at self-education I still had a useful working installation of Ubuntu and I could just install over the messed up Ubuntu install.

Yes, it is learning all the time. By the way, I was saying that the way you were treated at those other sites was against the Ubuntu Code of Conduct. I was not referring to the way you asked the question. 

Regards

---

### Post by Bashing-om on 2024-12-08
Hello jero2020

+4 to grahammechanical's last.

I too was an experimenter - and came here from Windows - ... in that experimental stage I too broke my system many times. Now since I have learned it has been many years since last I broke my system beyond my patience and ability to repair :D

However - to this day I continue dual booting;
There is my daily driver - works station - that I do not mess about to break it
my alternate install for those experiments
a test bed install for just that - testing (new releases, support troubleshooting, and all)

All this - cheap insurance >

- you can bet --- the rain is going to come-

---

### Post by TheFu on 2024-12-09
Linux isn't Windows.  It took you a decade to learn Windows.  It will probably take about that long to learn Linux/Unix to the same level.

If you only speak English, from a typical English speaking country, and get dropped off in rural China, it will take some time to figure things out as you slowly learn a completely new language.  Learning Linux is like learning Mandarin.   Things that appear the same often are very different. Further, there are two very different cultures for each OS.

Things that seem odd to new users are often because they haven't yet learned the genius behind the "why" things are the way they are.

If you've ever seen a Unix-centric person, someone who has never used MS-Windows try to make sense of that OS, they get frustrated too.  Around 2010, I tried to use MacOS.  Within 3 weeks, I wanted to smash the Mac computer against a brick wall, it was so frustrating to me.  I'd had too many years with Linux and Unix that my expectations of flexibility just couldn't be met by MacOS or MS-Windows.


The other issues, I'll leave to others with more patience that I have to address, but one reference book worth getting is : [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) . It is a non-hassle download and starts from the beginning, building the next concept based on the prior concepts introduced.  With Unix/Linux knowledge, you can't jump into the middle of a complex task and see 1 screen with 5 checkboxes ... and an "OK" button to press.  You'll need all the knowledge necessary to get to that point first.  You didn't know how to do fractional math on day one of grade school.  You had to learn numbers, then addition and subtraction. The next year, you learned simple multiplication and division.  And the 3rd year of math, you were probably taught fraction, how to convert to decimal values and how to do "long division" of any numbers.   Don't expect to do *long division things* in Linux until you've mastered addition and subtraction.  It takes time.   The specific program you want to install isn't a standard program, so the installation isn't setup to be trivial for people new to Linux.  It probably follows a well used pattern from the 1990s, but for the last 25 yrs, most Linux systems have used a package manager for installs, that includes all the popular Linux distros.  

One last  thing ... if you are typing more than a few characters at a time inside a terminal, you are doing it wrong.  Most shells, including bash, support something called "tab completion".  It helps fill in programs, data files, and command options - effectively making it next to impossible to get "command not found" errors or the wrong spelling of command options, or point at a non-existent/misspelled input file.  Before you get too far, find a 2 minute video online about "tab completion" sometimes called "command completion" and watch it, practice using it on your system.  It will solve those issues.  Of course, if you enter an existing, but incorrect option or input filename, that's human error and still your fault, but at least it won't be misspelled. ;)

Anyway, good luck to you.  Unix/Linux is becoming more and more popular every day.  The permissions model it uses is the most popular in the world today. Effectively, there is only 1 OS that isn't based on Unix at the core. It happens to be very popular, but all your IoT devices and in telecom, Unix is king.  I worked wireline telecom for many years in the systems and network architecture team.  Get the fundamentals down ASAP.  Learn Unix permissions ASAP, not just the simple stuff for the more complex things. It will only help you.

---

### Post by bobunderwood99 on 2024-12-09
Another useful book:

[https://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1718500408](https://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1718500408)

---

### Post by him610 on 2024-12-09
You will find another useful book, *The Linux Command line by William Shotts,* by checking out the link under my signature. It can be downloaded in pdf format.

---

