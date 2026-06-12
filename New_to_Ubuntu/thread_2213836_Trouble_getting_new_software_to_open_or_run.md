---
title: "Trouble getting new software to open or run"
date: 2014-03-28
forum: New to Ubuntu
---

### Post by Rick_Smith on 2014-03-28
Hi,
I've been running Ubuntu 12.04, for about 6 weeks. I'm picking up as much of the CL as I can, have no reluctance to learn it. But here's the dilemma. About 70% of the new software I have downloaded, whether from the Ubuntu Software Center or otherwise, either does not open or run. Sometimes I can't even find it. I really don't know what to do about it. I was weaned on Windoze so I don't know diddly. I don't mind learning whatever I need to but I don't know where to go next. Do I master the CL? Is there something else I should study? I am at a loss. What do I need to teach myself to do what I need to in order to make the software open and run? My main goal is to know enough to make any software work that is available for Ubuntu. 

Thanks for your help. :P

---

### Post by Tristan_Williams on 2014-03-28
Almost every piece of software can be run by typing the respective command.
For instance, if you are wanting to run firefox from the command line, you would simply type "firefox"

There are better ways to do this for beginners though.
To run software the "normal" way, you will want to go to the "dash" (the icon in the top-left corner of the screen) and click on it.

Then you can use the search bar to search for any applications you have installed.

So you would search for "firefox" and click on the firefox icon that appears.

Quick tips on installing software on Ubuntu, or any other Linux Distro:
1. Dont download .exe files. These are designed to work on Windows. They don't work on Linux. It's like trying to get an English speaker to read Chinese.
2. There are always multiple ways to install something. Some common ways are: Software Center, Synaptic Package Manager, .deb files, source-code(for advanced users only)


And as for your question "Do I master the CL?"

Ubuntu is designed so that the user always has an alternative to using the command line. 
However; you will be sooooo much more productive if you learn everything you can about the command line. 
You have much more control over what happens when you use the command line. 

Try getting to know "apt-get" (the command line package manager. it helps you install software)
apt-get will be your best friend for fixing things when you break something (you will break things, I promise, and so does every other person who has every used Linux)

Which brings me to another good point.
Don't freak out if you break something. Stay calm. Take mental notes of what you were doing that caused it to break. If you can't solve the problem yourself, you always have the nice people here at Ubuntu Forums!

Any other questions?

---

### Post by Rick_Smith on 2014-03-28
Tristan,
yes you answered part of the question and the part you didn't answer was because I didn't formulate the question very well. My bad. :o)
I'd like get to know the CL better, I can use apt-get and some other simple commands. I use the CL whenever possible. I tried to download a theme from the Ubuntu repository and it worked partially. I went to remove using sudo apt-get remove (theme name) and it said there was no such file. Huh? Didn't show up in dash either. Pretty weird. I let it go. 

Let me give you a another specific incident that will further illuminate the original question. I downloaded a game, triplea, which is really a platform for several other games as well. It works fine. When I tried to download the rest of the games I get a 6 page error message. Which is just gobbledygook to me. Someone here said to put the file (a zip, btw) inside the original file and open it there. I think I did it but nothing changed. I was stumped and let it go. So I guess what I am asking is where do I look for info that goes beyond just using sudo apt-get. As I am sure you know there are all sorts of things that one can do to make a program work but I really don't know what they are. Is this something I will figure out as I learn more about CL? Understand I am not looking for a solution to a specific problem, although that wouldn't suck at all, but where to focus my attention to solve these sorts of problems. 

Don't think your answer wasn't beneficial, it was. And it is appreciated as well. Thanks.

---

### Post by Tristan_Williams on 2014-03-29
I will start by saying that everything I've learned (and I speak for probably 90% of the Linux community) I learned by searching google for information on every little thing.

If I wanted to know how to extract a .tar.bz2 archive, I would search "extract tar bz2 linux"

Some of the best sites to look for in googles results are:
- Ubuntu Forums
- Ask Ubuntu
- Linux Forums
- Anything that looks like it was well thought out.

Every time you run into a problem, want to know how to do something, want to know why something behaved the way it did, or anything else about Ubuntu or Linux in general, ask your questions on here.



Now tell me. Right now, what are the main things you want to learn how to do with the command line?
It could be anything, Extracting archives maybe. Alternatives to using apt-get and the software center. Making bash scripts. Anything you can think of?

I am also afraid I still didn't answer your question... Did I not? I am more than happy to add more details

---

### Post by Rick_Smith on 2014-03-29
First off let me thank you again for your assistance.

 Main goal right now is to download a program, game or whatever, and get it to run. It seems that many Linux programs have to be tweaked a bit and other than using apt-get to download I don't know much about using the command line (or anything else) to tweak it. If it doesn't run out of the box, I'm lost, don't even know where to start. All I really know is Windoze. I know almost nothing about using a Linux based system. Hope that helps.

Edited for this after thought, I think you did answer my question, when you made the suggestions in your last post. Google searches, asking questions here on the forums. I think that might be the best solution for now. Thanks again, very much appreciate you taking the time to help out.

---

### Post by buzzingrobot on 2014-03-29
Themes are not executable programs, so they won't show up in the Dash overview. 

To enable a theme, you need to install an additional tool. In 12.04, I believe it's "Ubuntu Tweak" (or maybe "MyUnity?).  It's "Unity Tweak Tool" in later releases.

Executable GUI programs correctly packaged for installation on Ubuntu will place an icon in the Dash overview.  You don't need to go looking for them.  Command line tools, scripts, etc., may not install that icon, but should be on your *Path* and executable by entering their name in a terminal window.

---

### Post by Rick_Smith on 2014-03-30
> **buzzingrobot said:**
> Themes are not executable programs, so they won't show up in the Dash overview. 

To enable a theme, you need to install an additional tool. In 12.04, I believe it's "Ubuntu Tweak" (or maybe "MyUnity?).  It's "Unity Tweak Tool" in later releases.

Executable GUI programs correctly packaged for installation on Ubuntu will place an icon in the Dash overview.  You don't need to go looking for them.  Command line tools, scripts, etc., may not install that icon, but should be on your *Path* and executable by entering their name in a terminal window.

Thank you, that is good to know. All of what you said is news to me. I've seen both MyUnity and the Tweak Tool. Not sure about some of what you said but I'll do the research and figure it out. You've pointed me in the direction so that should be good enough. Thanks again. I think we can call this solved.

---

### Post by buzzingrobot on 2014-03-30
The "Path" is, basically, a list of directories that is searched when you run a command in a terminal. The program that takes care of actually reading what you type on the command line, finding the command, and launching it, is the "shell". (There are different versions of shells.  In Linux, it's typically "Bash".) The shell looks down the list of directories in the path until it finds the right executable.

Applications, GUI and otherwise, are installed in a few standard directories that are in the path. So, the shell searches the path to find them. Properly constructed GUI apps in Linux also create what's called a ".desktop" file that's basically a data list that points to the app's icon, where it's executable file is located, etc. 

That's a very tiny bit of the "how".  Typically, it just works and users don't need to worry about it.

---

### Post by Rob Sayer on 2014-03-30
My 2 cents:

For linux novices it's better to stick to the standard ubuntu repositories.  They're based on the venerable Debian system and are the best repos around.  The ubuntu repos are one of the reasons ubuntu is best for newbies.

If you want to add repos in synaptic or software centre, just use the Canonical Partners at first.  Don't enable the backports there.  I'd only recommend them if you have a specific need for one, like I use for my wireless adapter in my netbook.

There isn't a whole lot you'll need that isn't in the repos, and the stuff there is beta tested.  It'll almost always work properly for the ubuntu version on your machine.

Adding external ppa's isn't as reliable, and in fact they can introduce malware.  There are trusted programs/ppa's like Handbrake and Chrome but new users don't necessarily know the difference.

For example, I wouldn't personally touch stuff like MyUnity and Ubuntu Tweak Tool with a 20 foot pole.  I don't use 3rd party skins for app software, let alone my OS desktop.  When you do an update you run a serious possibility that something isn't going to work properly anymore.  And it's going to be hard to fix.

If you're going to install from terminal using apt-get run this first:

```
sudo apt-get update
```

I actually hardly ever use the ubuntu software centre anymore.  I use Synaptic Package Manager most of the time.  If you don't have it already install it.  Synaptic may seem confusing until you get the concept but it's worth it.  It has a button to refresh sources (like apt-get update) and I always do that first.  It has search and a really good history log, which is probably my favorite thing.

There've been a lot of newbies here lately who think, as mentioned, that you're supposed to download .exe installer files in linux as in windoze.  Programs in linux do not self install.  That's done by the OS.

That may seem like a pain but it's a feature not a bug.  Unlike in windows, the permission levels actually *work* properly.  The main reason there aren't any linux viruses out there is that  a virus, like any other program, has to be installed.

In stupid Windows that just takes a click, which can be hijacked in the GUI.

In linux it requires a user who has administration privileges ... and in linux that actually *means* something ... to enter a password.  Which is why no linux user I know has an AV program running in the background.  There isn't much point infecting a host if it isn't going to spread it.

---

### Post by buzzingrobot on 2014-03-30
> **Rob Sayer said:**
>  I wouldn't personally touch stuff like MyUnity and Ubuntu Tweak Tool...

You're call, of course, but it's pretty annoying enabling a new theme without using a third-party tool since Unity doesn't provide its own theme-switcher. (Or font changing gizmo, for that matter.)  I think it's safe to use a third-party tool for those functions.

---

### Post by Rick_Smith on 2014-03-31
Wow, great info here and I appreciate everything. I'm taking notes on this stuff and checking out the things you all have mentioned. Ya'll are pretty cool for taking the time to respond and I will take your advice. Thanks a bunch..

---

