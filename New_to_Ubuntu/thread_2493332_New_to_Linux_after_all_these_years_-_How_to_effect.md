---
title: "New to Linux after all these years - How to effectively find help?"
date: 2023-12-11
forum: New to Ubuntu
---

### Post by r9an on 2023-12-11
Greetings.  After dragging my feet for the past 20 years, I've plunged into using an Ubuntu server.

Of course I have read hundreds of pages of documentation both in the past and present.  I tend to hit a roadblock at every single turn, then spend days trying to get past it.  Lather, rinse, repeat.

I have successfully achieved some of the primary goals, but have ground to a halt yet again.

What do you find helpful when you just can't find the answer?

For example, I installed auditd and configured a watch for a particular command.  I gave it a key name and have verified it is writing logs. 

I tried aureport -k customkeyname thinking it would output instances of my custom made key.
The result is: Unimplemented option

Ugh.

It feels like I am lost without a compass.  Does this mean I don't understand option -k properly?  Does it mean option -k just isn't included in my aureport executable?  Have I incorrectly defined the rules in the config file?

When you find yourself in a similar situation, how do you find the tools to get yourself un-stuck?

---

### Post by TheFu on 2023-12-11
Learning Linux is like learning a different language with completely different grammar.  

Experts with non-Unix OSes often think those skills transfer - and they do for some hardware-specific things, but not for how the OS works deep inside.  

This leads to frustration because they come from 1-company making the rules to 10,000 little projects doing their own things, not always coordinated. It can be frustrating.  However, it is frustrating for people used to Linux to try to use OSes that are controlled by a single company too. No choices.  Linux usually has 3 if not 500 choice for any specific need.  Sadly, sometimes there are zero choices too. That's life.

Ok, so first, Linux skills build on each other.  Trying to perform intermediate or expert-level skills when you are a beginner is very difficult. Think of it like learning to compete in Olympic hurdles when you are a newborn and cannot lift your head yet.  There are mandatory steps that must be learned, perhaps mastered, before you are anywhere near ready to attempt the hurdles.  
[LIST=1]
[*]roll over
[*]get on all fours
[*]crawl
[*]stand
[*]stand and wobble
[*]walk
[*]walk faster
[*]jog 
[*]run
[*]sprint, and finally, 
[*]consider trying hurdles.
[/LIST]
There aren't any shortcuts.  Linux is the same way.  Start with the basics. That usually means using a simplistic desktop for 6 months to 3 yrs before attempting anything "server" related. Obviously, passion for learning and aptitude can drastically shorten the time.  Using a Linux desktop 10 hrs a day will help, provided you don't just point-n-click.  Linux servers don't have any GUI, so rather than doing things with a mouse, seek out how to accomplish things from a terminal.  Learn to make your chosen shell program your bitch. Make it work for you.  

For good, basic, everyone-should-know-this knowledge, work through the first 250 pgs of this books: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  This will take 2-6 weeks, if you are consistent and concentrate. Only then will you have the basic skills for google answers to be safe.

When using google, include the OS and release in your searches for answers.  For Ubuntu, when you are new, prefer answers from domains that have "ubuntu" in their domain name.  There are a few other "trusted sites" that don't have ubuntu in their names, but the vast majority shouldn't be trusted to provide steps for working, secure, setups of XYZ.  For Ubuntu stuff, always start with 
a) the manpages already installed on your system - learn to read manpages. This is the expected, default, documentation for all server things. 
b) the help.ubuntu.com website which holds the "official" documentation

Don't skip learning file permissions.  In the Unix architecture, there are 2 types of things - files and processes.  The only thing that is a process is a running program. Everything - -EVERYTHING else is a file and control by file permissions.  This is the core of all Unix system security - doesn't matter if this is Linux, Unix, MacOS, BSD, iOS, Android, whatever.  They are all Unix-like and file permissions are the core security model.  If you don't have permissions understood now, stop.  Spend 45 minutes of deep concentration to learn them.  Around 30 minutes in, that proverbial light bulb should go off in your head with as a sign of understanding. Spend 15 more minutes validating you truly understand.

Did I mention using Linux 10 hrs a day?  Do that.  It matters.

Learning how to accomplish things in Unix (Linux is basically Unix) requires thinking different.  These links might be helpful: 
[https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)
[https://linux.oneandoneis2.org/LNW.htm](https://linux.oneandoneis2.org/LNW.htm) Linux isn't Windows

Join a LUG - Linux Users Group.  These are in most medium to large cities worldwide. There are also some virtual LUGs that meet through video chat.  Sometimes a 30 second chat face to face can drastically help understanding when 20 pages of reading isn't working.  If you want to become a priest, you need to spend some time in the monastery, right?   Hang out with Linux people.  We are all sorts. Many of us like beer, so that usually is a good "in" to the group.  A LUG in my area meets at a pub/tavern.

And you've probably come across a few a-holes. Linux has their share.  Ignore them.  Most people really just want to help and save you the problems they encountered when they were at a similar stage.

In these forums, there are tens of thousands of questions, many with answers and many with some back and forth leading to a solution.  All our systems are just a tiny bit different, so what might seem to be an easy question usually isn't. There are many options. People helping don't want to assume something that isn't true, so they ask more questions.

In MS-Windows, there is basically 1 file system. Everyone uses it.  In Linux, there are 4 popular file systems and 3 volume management tools.  This means that any questions related to storage are never trivial, since the way your system is setup is specialized by choices you made during the install.  If we assume the wrong things, data loss will happen.

Always remember that Linux doesn't know if your commands are stupid or genius, so if they are possible, they are allowed. No net to protect you.  If you want to shoot yourself in the head, chest or foot and it is possible, it will be allowed.  It is a philosophical choice in the design of Unix.  Other OSes don't have that same idea.

So, I've never used auditd, but I've only been a Linux/Unix admin for 30 yrs.  I suspect whatever it is you are doing isn't the best answer, but you could be a genius. Can't tell.

---

### Post by Holger_Gehrke on 2023-12-11
Of course, the man-pages are what you look at first (in this case: the '-k' option to aureport doesn't take additional arguments; 'aureport -k' should - if I read this right - generate a report on defined keys and possibly a summary of how many events are logged for which key). If the man pages leave me lost in details, a look in /usr/share/doc/ is the next step. A lot of programs install additional documentation there. In the case of auditd this gets me at least a big heap of examples ... not what I was looking for, but might be useful for seeing how it's done right ... The step after that is usually 'apt show package' (in this case:'apt show auditd') to find the homepage of the program. So then I visit the homepage of the program and look for an overview of the program and it's use. If I don't find anything useful there, I often try the Arch wiki. And there I found the hint you were probably looking for in this case: 'ausearch -k keyname' shows the log entries generated with this key. If I was still looking, I'd try searching for various keywords (in this case I tried 'Linux Auditing System' and got several good hits at redhat.com, which sounds right since that's were auditd is being developed).

Holger

---

### Post by r9an on 2023-12-12
Thank you for a thoughtful, thorough, and well-written reply.  You've brought up some great reminders as well as new items.

To a friend, I described Linux as being like a Saturn V rocket built from an erector set and lacking the buttons and switches.  You can customize it however you  like by twisting wires together, but you have to learn bits and pieces of the roles of each of the  engineers who designed that thing.  Want to vector the rocket?  Then  you have to learn how to control the engine gimbal system.  Don't want  one side of the service module to overheat?  Then you have to learn how  to manually fire the thrusters to cause a slow rotation of the ship.

---

