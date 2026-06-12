---
title: "Big Question About Terminal (Command Line Interface)"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by DoctorVarney on 2012-07-09
Right, the only reason I'm here, using Linux is because I CAN.  UNIX was always that mystery hardcore guy whom I never expected to meet... until I discovered Linux with a GUI.  One day on Ubuntu and loving it so far.

But there's one big nag... SO many things are still done through the CLI of the Terminal.  Well, I didn't quite expect that - but In for a penny, in for a pound... I'm up for the challenge.  Why not?

So the BIG question is - putting it bluntly - you need to know a hell of a lot of technical stuff to work this thing....

MSDOS wasn't that hard, it just looked hard.  So what's a good formula for learning the commands?  Where is the best place to start learning, so I don't have to keep blindly copying & pasting commands?  I tend to enjoy stuff much more, when I get an understanding of it.  You know?

---

### Post by jmfal on 2012-07-09
Welcome to Ubuntu,

Read the stickies, theres a wealth of info on the terminal,

Write the commands on paper or paste in a file
google ubuntu foss commands, save and print out if you want

The best way to learn the terminal is to use it, and be comfortable using it.

---

### Post by Double.J on 2012-07-09
> **DoctorVarney said:**
> 
MSDOS wasn't that hard, it just looked hard. 

Bingo! and it's mostly the same here... the difference is that unix was huge in comparison to DOS, and likewise linux 30 years on has literally thousands of terminal programs... we're still a graphical system sitting on top of a cli one!

Basically there are stages to learning anything, and I think it's important to remember that there's basically commands that are common to all linux, and commands that are specific to distros. It'll vary a bit by what's installed on the system, but by and large you have the GNU userland tools, and the distro specific side of things - package management and the software you add.

My personal advice is to start with the real basics - learn to navigate, create folders (directories) delete them, see whats in folders.. you know the basic commands that let you hop around the *nix world.  There's a pretty good overview [here]("http://linuxcommand.org/learning_the_shell.php"), and this is relatively unix standard, there's loads of other resources around.

Once you're down with the basics of getting around and where everything is, I'd recommend the second thing to learn is your package management on that distro.. In ubuntu you can get the basics of this just by typing```
 man apt
``` to see the manual for that package, but you can get a lot more info from [ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Precise_Packages#Apt_and_Package_Basics").

Once you feel comfortable with binary (.deb) packages, next step has to be [compiling from source.]("http://www.tuxfiles.org/linuxhelp/softinstall.html") I'd recommend starting with something small such as htop - a very useful CLI system monitor, and it's in the repositories as back up!

cool so after all that you've got the basics down, it's just building up the skills - we're all still learning, no-one knows them all, just as you do something new you learn something new... it's a lot of fun! hopefully the links I've given you will have more than enough info, there's also a huge wealth of info from [IBM]("http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-1/"). 

It's really good that you want to learn some more - never get in the habbit of copying down commands you don't know what they do - it's very important in the terminal as many commands work on an input/output principle, so even just getting commands backwards can cause problems.

Other than that, I'd say just have fun with it... I still enjoy finding a new tool i didn't know was there! The only peice of advice I'd say is paramount is that "sudo" means make me administrator... you're going to see the "su" command a lot in online tutorials.. ubuntu disables the primary use of this command and uses "sudo" instead. However, to begin with try not using "sudo" ... if the command needs the special privilages, the system will tell you and it gives you a chance to double check :)

Hope it helps!

---

### Post by DoctorVarney on 2012-07-09
Brilliant!  Thank you, I really enjoyed reading your reply and have bookmarked that page.

---

### Post by cortman on 2012-07-09
What? No one has mentioned my sticky-turned-wiki? :P

[Here's]("https://help.ubuntu.com/community/CommandLineResources") a big list of some of the best resources on the web about the CLI. It's in the signature, too, actually.

---

### Post by zwygart on 2012-07-09
As mentioned before a usefull command to learn what you are doing is man. man is a program that explains how to use the command. It's used often and even on the Internet you will sometimes just see the same thing as in the man page. 

so just type : man man 
and the fun begin.

---

### Post by mastablasta on 2012-07-10
> **DoctorVarney said:**
>  
So the BIG question is - putting it bluntly - you need to know a hell of a lot of technical stuff to work this thing....

 
a missconception becuase commands are given to do things in instructions. it is so because there are quite a few desktop environemnts. and each of them has things in different places. settings in Unity are not in the same place as settings in KDE (Kubuntu). yet if you type in (copy & paste them in) commands they are valid in both options. 
 
even for server (where command is usually used) you have distributions that porvide a nice GUI to administer them. So the use of ocmmand is limted. though they are powerfull. 
 
for more on commnands linuxcommand.org has a good free e-book available on linux commands (basic stuff mostly).
 
if you want to explore doing things via GUI have a look at the free Ubuntu manual (link in my signature).

---

### Post by Paqman on 2012-07-10
> **DoctorVarney said:**
> SO many things are still done through the CLI of the Terminal.

What are you exactly trying to learn? Administering a server or just using a desktop?

Server admin does require lots of CLI work, although there are tools like Webmin that can skirt around that to a degree.

Using your desktop shouldn't ever require the command line if you don't want to use it. The exception is troubleshooting problems, where a lot of the time people will send you back to the terminal. Often this is just because the people who are gripped up on Linux come from a server background, so that's the first place they go. I regularly see command line solutions given to newbs here when there's actually a perfectly good (or better!) GUI solution (eg: installing packages, extracting archives, etc). So just because someone gives CLI instructions doesn't mean there isn't a GUI solution too. If you want a GUI solution, ask for one specifically and someone should oblige.

---

### Post by mojo risin on 2012-07-10
I find that it is often quicker to do things via cli. :) I think the best commands are easy to remember (or the most useful commands) like lsusb for lsiting your usb devices, lspci, for your pci devices, and dmesg to list what came up since your computer started. also I like it for some programmes where I don't need a heavy GUI, like as an internet traffic monitor (bwm-ng)

---

### Post by DoctorVarney on 2012-07-10
Thank you.  Paqman, I like your answer.  To clarify, I'm from an art/ design background so the GUI is where I began my computing experience.  Back when I started, it behoved the user to know some basics of DOS for when things went wrong or you needed fundamental control over physical disk space.    I'm also one of those strange people who can actually type faster than point a mouse.  So even in Windows, keyboard shortcuts were kinda my thing.  Thus, when it came to HTML and CSS, you didn't have WYSIWG editors to begin with and when they *did* arrive (*in the form of Dreamweaver*) they were no substitute for knowing one's code, unless you didn't care (or know) that your code was bloated to high hell with software-specific babble.

Obviously, manual coding *within* a GUI and whizzing around a GUI by tapping keys CANNOT be compared with CLI commands!  But the point is, I know what I'm doing with Windows only through the GUI - because it was designed that way.  With Linux, a lot of advice I've received is in the form of CLI commands that I can only copy and paste in.  Until I understand it, I have no way of knowing what it is they've just advised me to do.  Whereas, with Windows, it's a different story.  You can see what you've done and why.  I would love to be at that stage with Linux some day.  I just don't know if I'll find the time, as my trade lies outside of computing...   All I know for now is that Linux is so far providing me with a more pleasant experience than Windows ever did.  And that's only two days!

Though, to follow up with some common sense, if it can ALL be done through the GUI, then I'll be more than happy to continue like this.

---

### Post by kimda on 2012-07-10
When I started with Linux I read a lot about everything. I bought a book from O'Reilly Running Linux which is a great book which covers most basics. But you do not need a book like this because everything can be found on the web. Loads of free online manuals. ex. [https://help.ubuntu.com](https://help.ubuntu.com) 
[http://ubuntu-manual.org](http://ubuntu-manual.org) 

If I would start all over again I would start by installing Linux in a virtualmachine (vmware of virtualbox) or on a spare machine. Why? Because I would like to mess with it without having to worry about messing stuff up. The best way to learn is learning from your mistakes. With a virtualmachine you can easy restore or recover from mistakes you made and startover again.

---

### Post by HermanAB on 2012-07-10
FWIIW, the older Linux distributions have wizards for everything and the kitchen sink.  Eg, with Redhat/Fedora, Suse, Mandriva/Mageia/PCLOS you seldom, if ever, need to use the command line.  

Basically, on those systems, you only need to use Bash when you wax nostalgic about the good old bad old days of the prehistoric Linux command line...

---

### Post by sudo smith on 2012-07-11
My favorite website so far for learning terminal is lowfatlinux.com try it out.

---

### Post by nothingspecial on 2012-07-11
I wish I'd started with [[COLOR="Blue"]this bash guide[/COLOR]]("http://mywiki.wooledge.org/BashGuide")

---

### Post by DoctorVarney on 2012-07-11
All good advice, indeed.   Cheers!

---

### Post by GreatDanton on 2012-07-11
nothingspecial: +1 for that link. It's really good.

---

### Post by pe7er on 2012-07-14
When I install software using the command line, I document those commands in my own wiki: handy when you have to remove (or reinstall) it.
In my wiki I also added all the addons (+ direct link) I installed in Firefox/Chrome, so when I want to use Firefox/Chrome on some other PC, I can easily install my fav addons.

At the moment I am reading the book "Ubuntu Linux Toolbook - 1000+ commands for Ubuntu and Debian Power Users". 
IMHO this is the best command line book for Ubuntu/Debian I have found so far. You can find it in online shops or at eBay.

btw: having devices like the SheevaPlug (a mini Linux server that only works using the command line) makes it easier to learn the command line as you can't cheat using a GUI :)

---

### Post by JKyleOKC on 2012-07-14
While the "man" program, run from the terminal, is great, you might be more comfortable using "xman" which is a front end for "man" that displays in the GUI. I wrote a "how-to" for it which is at [http://ubuntuforums.org/showthread.php?t=1884501](http://ubuntuforums.org/showthread.php?t=1884501) if you want to give it a try.

I find it especially useful since I can have an xman window open, scrolled to the specific part of the information that I need, while using a separate terminal window to enter the command. I only wish that "xman" supported the clipboard so that I could copy an example out and paste it into my terminal window when needed...

---

### Post by Vaphell on 2012-07-14
> With Linux, a lot of advice I've received is in the form of CLI commands that I can only copy and paste in. **Until I understand it**, I have no way of knowing what it is they've just advised me to do.

look, you have found the solution ;-)
there is nothing preventing you from running <command> you see with *--help* parameter (which describes its function) or googling it... or even asking people who gave the advice to explain extensively what is supposed to happen when you run these lines.
Reading forums for cool tips, googling 'linux bash/ubuntu <put desired result here>' (eg 'linux bash sort file', 'linux bash substring', ...) help too, that's how i learned.

the other side of the coin:
[list][*] linux is not as uniform as win and mac and it's incredibly hard to describe the process when there are countless desktop configurations and customizations possible. CLI is the lowest common denominator and just works. Besides why bother with writing a page long paragraph when 3 lines of code do the job? What's worse, in case the recipient misunderstands the message in any place you have to write yet another paragraph.
[*] what if the user with a problem can't clearly describe it and can't give details of his config? Would you rather chat with him for 2 hours full of 'click this, click that' or say 'run this and paste the output so we know what we deal with and can make an attempt at fixing the problem'. Plain text is usually better than screenshots.
[*] GUI requires orders of magnitude more work from developers than text-based interface. Open source community doesn't have unlimited resources and the holes in GUI armor happen despite efforts targeted to close them.[/list]


There are many things CLI is so much better at than GUI it's not even funny :)

---

### Post by cortman on 2012-07-14
> **Vaphell said:**
> 
[LIST]
[*] linux is not as uniform as win and mac and it's incredibly hard to describe the process when there are countless desktop configurations and customizations possible. CLI is the lowest common denominator and just works.
[/LIST]


^^This is probably the single most important reason why we instruct people to use the CLI instead of a GUI. +1.

---

### Post by vasa1 on 2012-07-14
> **nothingspecial said:**
> I wish I'd started with [[COLOR="Blue"]this bash guide[/COLOR]]("http://mywiki.wooledge.org/BashGuide")
Nice!

---

### Post by ub07 on 2012-07-14
My advice would be to get a good reference book. Also, Google is your friend. Between the reference book and online resources you should be good to go.

It is a VERY good idea to document whatever you do so that if you have to do it again, you will know what you did. Also writing it out helps you to remember it.

---

### Post by coldraven on 2012-07-14
Hi, I use Tomboy notes to store useful commands that I find here or on the Web.
I think it must be smarter to use a one line command than have to download some huge program to do the same thing. For example Nokia Smart Suite is about 2GB when installed, but I can back-up my contacts with Gammu which is  three megabyte to install.
Yes, that is 3MB rather than 2GB!
Enjoy the world of Linux :)

---

