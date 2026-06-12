---
title: "Ubuntu Running In Virtual Box... now what?"
date: 2014-07-24
forum: New to Ubuntu
---

### Post by sam64 on 2014-07-24
I successfully installed the "Ubuntu 14.04 LTS" operating system as a VM in Virtual Box. I'm already able to run my Ubuntu VM and browse Firefox with it, but what else do I need to do to get started? I'm a little confused about what *connected to a server* means. 

What does connecting with an SSH Key mean? Since I've already got a full-fledged Ubuntu VM up and running in Virtual Box, Do I still need to choose an SSH Client?

How does one distinguish the following terminology: Terminal Application, SSH, Shell, etc.? 

What IDE or software am I supposed to use to start learning Linux hands-on?

---

### Post by TheFu on 2014-07-24
Learning Linux is like a learning a foreign language.  How to get where you want depends on your background and where you want to be.  Programmers will attack this differently from systems administrators and differently again for pure-end-users.

It takes time and exposure to learn.  A 5 minute Q/A session in person with your local LUG will answer these questions much quicker than we can here.

So - **what is your end-goal in learning linux?**

ssh is a remote access tool.  Remote could be around the world or just inside a different machine. ssh connections are used by systems administrators to secure remote CLI sessions, create secure tunnels between systems, and to run remote commands on a different system - including file transfers, backups, X-forwarding, .... etc.  If you never need to connect securely to another computer, there is no need for ssh.

 I love this question - something so simple, yet not clearly explained for anyone using alternate (non-UNIX) OSes.  ssh client?  Er ... I've been opening an xterm and typing *ssh -p 12345 userid@remote-host* for 20 yrs before learning about ~/.ssh/config that lets us type *ssh remote-host-alias* instead.  What other client would anyone need?  This isn't Windows (use putty from there).  Android has lots of ssh clients/servers too.  Don't forget that many tools use ssh automatically as a default - rdiff-backup, rsync, probably others that I don't know.

To learn terms, I'd recommend google and wikipedia.  Sometimes it just takes re-reading the explanations, since we all learn something new daily, the pieces will start to fit together over time.  
> 
How does one distinguish the following terminology: Terminal Application, SSH, Shell, etc.? 
For many people, there isn't any difference, so it really depends on context.  For example, 
"I use a terminal application to ssh into a remote system to run a shell there."  But most of the time I'd just use "ssh" and the other parts are assumed, not said.

IDEs are for programmers writing complex programs.  Most end-users have ZERO use for an IDE.  I use vim 95% of the time, not an IDE.  Often IDEs get in the way - I say this as a professional, cross-platform, software developer with 20+ yrs experience. The UNIX programming model normally just has 3 terminals 
a) editor
b) make/build tool
c) debugger
with "focus follows mouse" set, sliding the mouse between each window and doing an up-arrow to run the last command (usually "make") is very efficient.

So, where do you want to be with linux in 1, 5, 10, 20 yrs?  I started in 1993 and I'm still learning new things.

---

### Post by bigmonmulgrew on 2014-07-24
Took me a while to get used to ubuntu when I first started. The best thing I can suggest is that wherever possible use the same programs in windows as you do in ubuntu and the transition will be easier.

For example I used
Firefox - web
Thunderbird - email
open office - documents

So what programs do you use regularly in Windows, your first step is figuring out if they have a Linux version or what the alternative is.

---

### Post by sp40140 on 2014-07-24
+1 for TheFu..
to add a little about IDE. IDE: Integrated Development Environment. Ex. Eclipse. IDEs are applications (in broader terms like notepad or even MS office). The let you create things. You don't use IDE to learn Linux. You use IDE to learn to program / code (in different languages). And you can install IDE on linux / ubuntu.
So as TheFu said. Please provide context. What is your use case. What do you want out of Linux?

---

### Post by bulrush2 on 2014-07-26
You and I are in a similar position. While I'm familiar with doing linux as a user, I'm brand new to the admin portion. 

> [COLOR=#000000]What does connecting with an SSH Key mean? Since I've already got a full-fledged Ubuntu VM up and running in Virtual Box, Do I still need to choose an SSH Client?[/COLOR]


You, as a user, can connect to a server via a terminal. A terminal can connect to the server in several different ways: Telnet, rsh (remote shell), ssh (secure shell), openssh (a brand of secure shell), rlogin (remote login), and some other methods. They each have their pros and cons. A "terminal application" is simply software that pretends to be a terminal. 

Back in the day, terminals were hardware boxes, like a dumb computer. They only handled display and communication of information, not actual computations. Now we have software to emulate the "dumb terminals". 

For OpenSSH,  you can login one way, with just a password, which has a security vulnerability. Or put a physical key on the server (and linked to your user) and on your client (Windows PC). This makes it more secure, but for practicing on a VM on your own PC, is not really needed. 

> [COLOR=#000000]How does one distinguish the following terminology: Terminal Application, SSH, Shell, etc.? [/COLOR]

When you login to a unix server as a terminal, the server has a config file and runs a command line shell, like csh or bash (more popular and powerful). From there, the server might run your GUI desktop, but the GUI is driven by X windows. Notice there are many layers to this. Understanding the layers and how they relate to each other is important. 

> [COLOR=#000000]What IDE or software am I supposed to use to start learning Linux hands-on?
[/COLOR]

You can install Ubuntu under Windows using [VirtualBox]("https://www.virtualbox.org/") without having to do a dual boot. The virtual machine, created and managed by VirtualBox keeps your Windows installation safe. I'm sure they have free VM software for Macs too. Install the Ubuntu server as a VM and practice away.

---

### Post by sam64 on 2014-07-26
> **TheFu said:**
> 
So - **what is your end-goal in learning linux?**

I want to gain a basic understanding of how to use Linux, so I can learn Kali Linux. I'm want to be a penetration tester for a career after I graduate.  

> **TheFu said:**
> 
If you never need to connect securely to another computer, there is no need for ssh.

I guess I misunderstood what ssh is for. I will need to connect to other computers eventually, but I don't see myself ready to do that until I get some Kali Linux experience first.  

> **TheFu said:**
> 
IDEs are for programmers writing complex programs.  Most end-users have ZERO use for an IDE.  I use vim 95% of the time, not an IDE.  Often IDEs get in the way - I say this as a professional, cross-platform, software developer with 20+ yrs experience.

Interesting. I remember using vim in my Agile Programming class 9 months ago, as well as git hub. I would say vim is close I'm looking for (I just have no idea what it is called on an Ubuntu OS)?

I'm also trying to figure out what little project I should do to get started. Just reading explanations on what commands there are and what they do isn't enough to help me figure out how to get started. 

Give me good first assignment chief:biggrin:

---

### Post by TheFu on 2014-07-27
So first thing - asking how to break into systems (even legally) on these forums will get you banned.  Mentioning "kali" is probably to be avoided here.

Ok - that clarifies exactly what you want.  I'm part of the [DC404 group]("http://dc404.org/") - many are at DefCon right now.  Actually gave a presentation there a few months ago. ;) I'm also part of the [OWASP group]("https://www.owasp.org/") here, which is more about securing webapps than breaking in. For me, Kali is too non-secure to be used for anything. It is meant for a specific purpose, but it is NOT very secure itself.  Find your local defcon group - go to the meetings.  Sign up for the "offensive security" club at your local college/university.  Participate in CTF competitions. Many are virtual - H3 is coming up at GA-Tech - get your team together.

Regardless, you need to learn Linux/UNIX without all the point-n-click stuff to be effective as a pen-tester.  Most of the tools do not have a GUI and even if they do, the GUI is only 20% of what you need in your testing.  It is part of the UNIX philosophy - make a CLI program do amazing things, then add a GUI over it for the masses. I haven't seen any GUI that can do all the things the CLI programs do. It is a good place to start, but not enough to be a pro. 

You might want to follow IronGeek - he posts videos from cons all the time.

The shortest way that I know to gain Linux knowledge is by picking up an LPIC book and working through it page by page. This is more of what a server administrator needs to know, but the CLI knowledge overlap is so much that hardly anything will be wasted.  Definitely learn about UNIX file permissions and directory permissions - this is critical to security and penetration testing.  I've been learning Linux since 1993 - think I know 10% of it now. ;)

To learn about the commands - RTFM.  **man man**  There are thousands and thousands of commands. What they are and what they do are already on your system. RTFM.  If you've tried something, read the manpage and it didn't work, post the command you tried, what you expected and what it did here - someone can probably help.

Oh - and you NEED to know ssh.  How else will you setup a cheap server at Chicago VPS (the cheapest) to launch approved tests from?  Pretty much everyone in the DefCon world does this.

This part of IT security is one of the only growing fields that I'm positive will keep growing.

What the DC guys here taught me was never let Windows on a untrusted network and definitely never let it access the internet in general - just extremely specific places like MS-patch servers.

---

### Post by sam64 on 2014-07-27
> **TheFu said:**
> 
The shortest way that I know to gain Linux knowledge is by picking up an LPIC book and working through it page by page. 

Is this a good book:
[http://www.amazon.com/LPIC-1-Linux-Professional-Institute-Certification/dp/1118495632/ref=sr_1_1?s=books&ie=UTF8&qid=1406490321&sr=1-1&keywords=LPIC](http://www.amazon.com/LPIC-1-Linux-Professional-Institute-Certification/dp/1118495632/ref=sr_1_1?s=books&ie=UTF8&qid=1406490321&sr=1-1&keywords=LPIC)

Also, why do you use VIM over PuTTY? How great of a disadvantage will I have if I Use Linux on a Windows VM instead of a Ubuntu VM?

---

### Post by TheFu on 2014-07-27
> **sam64 said:**
> Is this a good book:
[http://www.amazon.com/LPIC-1-Linux-Professional-Institute-Certification/dp/1118495632/ref=sr_1_1?s=books&ie=UTF8&qid=1406490321&sr=1-1&keywords=LPIC](http://www.amazon.com/LPIC-1-Linux-Professional-Institute-Certification/dp/1118495632/ref=sr_1_1?s=books&ie=UTF8&qid=1406490321&sr=1-1&keywords=LPIC)

Also, why do you use VIM over PuTTY? How great of a disadvantage will I have if I Use Linux on a Windows VM instead of a Ubuntu VM?

I don't know about any specific books for this - I'm old and learned Linux before there were books. Sorry. I have an LPIC book which is out of date, but still useful to see and the old commands probably still work. That is the nature of CLI/shell Linux - the old way tends to work for 5-30 yrs, even if the GUI changes completely.

I don't use putty very often (since I don't use Windows much) - I use vim all the time from whatever machine I'm sitting behind and ssh into different systems (local and around the world) and run vim on those as needed.  vim is just a text editor, nothing more. 

There are pros and cons to using or not using a VM = virtual machine.  I prefer VMs over wasting hardware for a single purpose.  I dislike dual, triple, quad-booting since only 1 of the operating systems can be used at a time doing it that way. With a VM, I can use all of them concurrently and it doesn't require rebooting the main OS on the computer to use a different OS.  For me, that is a huge convenience.

---

### Post by sam64 on 2014-07-27
> **TheFu said:**
> With a VM, I can use all of them concurrently and it doesn't require rebooting the main OS on the computer to use a different OS.  For me, that is a huge convenience.

Do you know how to copy and paste content from the host to the VM? My new Ubuntu VM is nice and everything, but I don't really have anything to play around with in its directories. Is there some type of converter that can convert copied content from a Windows OS to be compatible on a Linux OS?

---

### Post by TheFu on 2014-07-28
> **sam64 said:**
> Do you know how to copy and paste content from the host to the VM? My new Ubuntu VM is nice and everything, but I don't really have anything to play around with in its directories. Is there some type of converter that can convert copied content from a Windows OS to be compatible on a Linux OS?

How would you copy/paste between any to systems on a network? The answer is the same for VMs. 
Or [https://forums.virtualbox.org/viewtopic.php?t=15868](https://forums.virtualbox.org/viewtopic.php?t=15868) is another way, but much more limited, since it only works between the hostOS and the guestOS.  I prefer using the normal network sharing method, since that works for all machines on the subnet too.

I don't understand why any conversion from content on Windows to Linux is needed.  HTML is HTML.  ODF is ODF. mp4 is mp4, mp3 is mp3, ogv is ogv, text is text  - if you need to remove the CRLF and just have LF, any editor can do that or there is a dos2unix or unix2dos utility - I haven't needed that in years and years.  For productivity-style apps, try libreoffice - it opens most MS-office datafiles.  

Is there a specific data file type that you need to convert?

---

