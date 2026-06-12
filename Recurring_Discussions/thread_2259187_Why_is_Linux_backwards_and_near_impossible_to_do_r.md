---
title: "Why is Linux backwards and near impossible to do real work on?"
date: 2015-01-02
forum: Recurring Discussions
---

### Post by Polorboy on 2015-01-02
I am attempting to install software provided by Xilinx (Vivado 2014, SDK, Peta-Linux SDK) and the only supported version of Linux which is free is Ubuntu.  I have attempted to install this software on: Arch Linux, Mint, Red Hat, CentOS, Fedora, and Ubuntu.  None of them are capable of installing the previously mentioned software without completely crashing during the process or after attempting to run said software.  Now, I have been using computers since DOS was an operating system.  I have used every version of Windows from 1.0 to Windows 8.  Not once did I ever run into this kind of complete failure of a product designed for an operating system to fail so miserably.  Luckily I have been running this in a VM and have not actually done any harm to my primary computer (happily running Windows 7 Ultimate).  For a long time I was under the impression that Linux was the OS that did things right, boy was I wrong.  I never had a real use for it until having to make use of this program by Xilinx.  The only "work" that any Linux operating system that I have attempted to use, and I am running out of distro's that I haven't tried, is to look at cat pictures online (<--- sarcasm, or, in other words, the only thing Linux seems to be good at is web browsing).  They can all do that pretty well... well if you can get the network interface to work... which is sketchy at best (doesn't always work in all distro's of Linux).  I have even used Backtrack as a working OS for a while but never found a reason to stick with it.  That, by far, was the best working Linux distribution I have tried.  Probably because it was written by a bunch of hackers who actually know what they are doing.  To clarify that I am not some half-wit who knows nothing of computers, I have my BS in Computer Science from the now recently acquired NYU Polytechnic School of Engineering, I also hold a patent on a novel method of network encryption, hence the need to work with Xilinx tools to design FPGA (Field-Programmable Gate Array).  I design Cryptographic microprocessors to secure network communications, among other things.  So, now that I have established that I actually know something about computers and how they are supposed to work, lets get down to business.  

Linux, and Ubuntu in this case, makes it impossible to run applications, period.  Trying to install the programs above I have to install them to a directory other than "home".  Now trying to do this by just running an installer, not going to happen since the Xilinx tools install to whatever directory it is currently sitting in.  Even if I move the installer files to the directory where I want them to install, using console and a whole lot of "sudo" commands (which is increasingly annoying) trying to run a install shell from there is also impossible, even when trying to run it from the console using a "sudo" command.  I get a error saying that I don't have permission.  Apparently the developers of Ubuntu also decided to remove the ability to actually switch to root using just the "su" command.  That would give users too much power and maybe actually let them use their computers for more than looking at pictures online.  As things currently stand just trying to edit a file is a hassle.  One cannot simple create a file from the GUI, everything must be done from the console.  Which makes me wonder, why on earth does any Linux distribution have a GUI, it doesn't make it any more usable and for the most part they look really bad.  Was the goal to make Linux GUI's as hard to use as possible?  Really, side bars, and floating task bars, and no real desktop to put icons on (not that they would be of any real use anyway).  For example, in Ubuntu, I can't get a simple list of programs that I have, I have to open what is essentially a giant start menu which fills my entire screen and primarily try's to sell me things.  Literally I mostly see icons to install programs that cost money... really??  Some Linux distributions I have used just boot to essentially a blank screen with a colored background and a bar on top that has the time, but that is it.  No ability to even right click to open a console, no way to open anything.  Apparently you need to auto-magically know some keyboard shortcut which opens a console so you can run something.  

I am pretty much fed up with Linux and want to get this horrible nightmare behind me.  I am pretty sure that after this I am going to go write my own Operating System.  I may have to do it for my FPGA design anyway.  For now I just need to run the Xilinx tools to do what is essentially a proof.  Proof that a FPGA design can send some traffic over a network.  

I know someone is going to say something to the effect of "why don't you just install "blah"" like I was supposed to automatically know about "blah", or someone will regurgitate some console command that consists of several acronyms that don't make any sense all because the person (I know who he is) who wrote Linux was lazy and didn't want to type out entire words, rather type random strings of characters which may or may not vaguely resemble the word or command they were trying to represent.

Apart from trying to get the Xilinx programs to install, I also need to access a network share which contain the design files I need for the Xilinx tools.  Much to the horror to some of the users here, the network share is on a Windows Server 2012 R2 which has been running in my home office for at least a year without any issues whatsoever.   I need to access the share from within VMWare Workstation version 9.  I enabled shared folders for Ubuntu but again someone, either Ubuntu developers or VMWare developers, broke the file sharing ability.  VMWare says on their site that it will be fixed in a upcoming patch, that was over two years ago and it is still broken.  

So, if anyone was able to wade through my general discontent with Linux and growing hatred for this operating system and still wants to offer advice I would gladly accept it.  As long as it is actually helpful advice.  I am not getting any error other than insufficient permissions, absolutely nothing happens, or the OS just crashed and reboots.  The Xilinx software mentioned above should be free to anyone, you would just need to make an account on Xilinx site to download it.  If someone wants to attempt to install the program and let me know if they are able to or not, that would also be helpful.  I asked for help on Xilinx forums and got nothing.  Apparently the support on Xilinx site consists of outsourced help who can only read from pre-scripted responses and post them (you know what I mean, think Dell customer service...).  They only offer real support to customers who are significantly large companies that spend several hundreds of thousands of dollars on their products.  I also asked for help on VMWare forums and got no response regarding accessing network shares from within VMWare workstation 9.  Other Linux forums I have asked for help on have responded to me with general contempt and are appalled that I did not exit the womb with a keyboard in my hands and already coding/debugging for Linux with a vast user base.  I should automatically know everything there is to know about Linux, the Kernel and other inner workings of Linux and be able to just write my own program to fix all the problems with Linux.  If that is going to be your response, just keep it to yourself.  I don't need the elitist answer.

I am open to anyone who can actually show me a real valid reason to use Linux that makes it possible to do real valid work on a day to day basis.  Though I don't think I am going to see anything so vastly different (let alone easier to use) than Windows that would make me want to change.  Look at the recently discovered Bash bug, that has been sitting there for nearly 20 years and only now was it discovered. The heart bleed bug, that was due to open source code that had problems that a freshman in college would do.  

If you don't know what the error was, it was a conditional statement (if) followed by two lines of code to do something based on the conditional statement.  Since they were not using {} to encapsulate their conditional statements, the default behavior is to consider the singular following line of code to be associated with the preceding conditional statement.  Since they did not use {} and the conditional was followed by two lines of code that did something, the second line was always executed.  There were two ways to fix this, the proper way to use {} to encapsulate all conditional statements and their associated lines of code, or the lazy way and put another conditional statement before the second line of code that was executed.  Either way was easy to do.  The primary reason this was missed was because the code was written in a text editor without syntax checking of any kind.  Even in Windows, using Visual Studio, it would have given a warning that the line of code would always be executed and given the developer a "are you sure you want to do this" check.  That error would have caused me to fail my programming classes.  

What else is going to pop up.  At least Windows has been through the gauntlet and come out the other side.  You would be very hard pressed to show me how Linux is more secure than Windows, especially since my specialty is in computer security and ethical hacking.

---

### Post by Bucky Ball on 2015-01-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. If you want help with a specific issue, please post in the appropriate forum section. One support request per thread is prefered. Thanks and good luck.

---

### Post by CantankRus on 2015-01-02
Your rant is entirely to long to read but you may find this link useful.
[**_[COLOR="#B22222"]Linux is Not Windows[/COLOR]_**]("http://linux.oneandoneis2.org/LNW.htm")

>  I am pretty sure that after this I am going to go write my own Operating System.
Good luck with that. :rolleyes:

---

### Post by davidchute26 on 2015-01-02
Don't mind me :popcorn:

---

### Post by Polorboy on 2015-01-02
Yup... got a "not going to help because..." and a TL:DR response already.  Not surprised.

1) Thanks mod... you response wasn't helpful in anywhatsoever.  The least you could have done is let me know which is the appropriate forum.  Apparently that is also too hard.

2) CantankRus, had you read my post you would understand that I know quite well that Linux is not Windows, probably better than you do.

---

### Post by CantankRus on 2015-01-02
> **Polorboy said:**
> Yup... got a "not going to help because..." and a TL:DR response already.  Not surprised.

1) Thanks mod... you response wasn't helpful in anywhatsoever.  The least you could have done is let me know which is the appropriate forum.  Apparently that is also too hard.

2) CantankRus, had you read my post you would understand that I know quite well that Linux is not Windows, probably better than you do.

Well turn off whinge mode and succinctly describe what help you require from any of the linux users who frequent this forum.

---

### Post by lisati on 2015-01-02
Thread closed for staff review.

---

### Post by Elfy on 2015-01-03
and there's no reason for it to re-open either

---

