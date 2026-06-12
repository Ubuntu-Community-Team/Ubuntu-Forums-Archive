---
title: "The shell way or the highway [long rant]"
date: 2009-11-10
forum: Recurring Discussions
---

### Post by BarisBlaq on 2009-11-10
This is a rant, and all and any responses are heartily encouraged, even if you will insult me, i'd really want to hear what you guys have to say, especially the veterans, if i may call them.

I've been using ubuntu as my prime os for about a year now, and i know i'm still a noob about it. I used to ask questions on the forums when i got stuck (and i still do), and generous people would show me how to do things, and I would be grateful.

Curiously, the solution was almost always something enclosed in <code>, involving running the terminal.

I am still afraid of the terminal.

I am 33, the first computer I had was a commodore 64, then came 128, and then I got an Amiga, and then a PC. Hell it was a 8088, and not a 8086 - woot!!

When windows 3.1 began to came out as the next big thing, it honestly seemed awkward to me. Finally a use for the mouse, good thing, but wtf? DOS is faster and more direct and more accurate.

We used to mock our friends who bought pcs with windows installed, because it was only a program, and in our wicked minds, if you couldn't install a program on a computer, you didn't deserve a computer. And to be fair, not everyone had a computer those days, at least not where I live.

Anyways, my apologies for going down memory lane. My point was, it took me a while to get accustomed to windows after dos.

Yet I'm still afraid of the terminal.

When a noob like meself asks a question on the forums, it will most likely get a response. The solution will most likely involve running some commands over the terminal. It will most likely solve the problem in hand. This is certainly a good thing.

But i keep recalling the old phrase - give a man a fish, you have fed him for today.. Teach a man to fish, and you have fed him for a lifetime.

Like i said, i been happily using ubuntu for about a year now, but every time i ask a question on the forums, and someone responds with "wget this and that" and "tar -xzwf" - i get the chills..

You are very welcome to point out that I haven't read the man pages about tar, but i am a lazy guy, and after a year of going solo on ubuntu, i still don't know what -xzfw means. I'm not even sure if i remember that right.

I do acknowledge the fact that guiding some helpless noob like me is far easier through a series of shell commands, compared to posting in screenshots- doing it the lame way.

It also ascertains a distinction among "classes" of ubuntu (or linux) users - if you know the shell, you're in.

If you are afraid of the shell (like meself, not because I now feel more comfortable with a graphic environment, but because I feel less comfortable with typing in commands i dont know what they mean) - well, dunno, you're afraid of the shell.

Basically what i mean to say is - when you provide a bunch of terminal commands to solve whatever the question is, you're not really helping, unless you explain what those commands do, and what the other options are.

Just me rant ..

Not sure if i could get my point through, but anyways, please do respond.. Ciao

---

### Post by alphaniner on 2009-11-10
> **BarisBlaq said:**
> If you are afraid of the shell (like meself, not because I now feel more comfortable with a graphic environment, but **because I feel less comfortable with typing in commands i dont know what they mean**) - well, dunno, you're afraid of the shell.


You *should be* afraid of typing in commands you don't understand.  But if you aren't gonna endeavour to understand what you are typing, you're right, you shouldn't be using the shell.  Or Linux, for the time being.

---

### Post by BarisBlaq on 2009-11-10
kk thx

---

### Post by doas777 on 2009-11-10
I can understand your feelings, and I support them to a certain extent.

the big problem is that of support.
we are here of our own free will answering peoples questions as we ask our own, primarily for fun. 

we have a thriving ecosystem with many options for any given problem. this however measn that most peoples boxes are not the same. they may run kde, or xfce, or gnome, or one of the many different desktop environments available, or even just a command shell. as such, the buttons and front-end applets are going to be different for all of us. the command line is the same however. if I tell you to open software center and search for pidgin, and you tell me that you are a kde user, then no one has gotten anywhere. if I tell you to open a terminal however, and enter 'sudo apt-get install pidgin' tehn I can be reasonably assured that that will work on any ubuntu-based system.

the other big one, is that I am too lazy to go to the trouble of installing software x, which I don't need, so that i can take screen shots of every click, crop and save them, annotate them, and then upload them, just so some person on the other side of the internet can avoid the cli. my advice is free (with no warentees) but it is not professionally polished. 

in fact I can't even tell you how to open synaptic with less typing than the shell line above (System -> Administration -> synaptic package manager). so now I have wasted my time, and your time, and given an incomplete answer to the query.

so no, it's not about elitism, or trendiness, or any thing but simple logistics.

btw, very few people think about what -xvfg mean, they are just always used when un-compressing stuff. what you are describing sound like instructions for compiling somthing. the problem is that most folks don;t care to navigate in a cli (go to the folder you downloaded the file to) so the poster is just giving instructions that eliminate that potentially sticky-wiket. wget downloads to the dir that the cli prompt points to, so it is always there waiting for the next command with no other action. the poster could have said "download this to a directory, then right click to extract. then open a terminal and navigate to whatever directory you download to (that ambiguity is teh problem here), and type 'sudo make && sudo make install'. 

most cli instructions are formulated so that you can just paste them straight into the terminal. there is just no way to do that with gui instructions.

good luck and have fun,

---

### Post by ratcheer on 2009-11-10
Heh heh. I remember when I first started working on UNIX and, to edit a simple text file, I would ftp it to my Windows machine, edit it with Notepad, then ftp it back to UNIX. Now, after almost 30 years UNIX experience, vi is probably my favorite editor of all.

So, I can understand your fear of the command line. It is powerful, but some people don't want the power. They want to be able to see what is going on at every step and be dead certain it is right before taking the next step. Whereas CLI people will add options and redirect and pipe and build up a single command that will do the whole thing quickly and efficiently.

It is just two ways of doing things. If you put your mind to it, you can learn to do it. But if you don't even want to do it....

Tim

---

### Post by issih on 2009-11-10
Strongly disagree with alphaniner...

For 99% of the things we advise people to use a terminal command for there is an equivalent, and equally valid gui method.

e.g. ```
apt-get install xxxxx
```

is equivalent to opening synaptic package manager (System-Administration-Synaptic) searching for the package xxxxx marking it for installation and hitting install.

```
chmod a+x filename
```

Open File manager, navigate to file, right click and open properties, then change permissions on the permissions tab to allow all users to execute the file.

No doubt there are other better examples, but those two popped to mind.

The reason people give advice using the CLI is indicated by the above...its less effort, and unfortunately the nature of a forum of people giving advice for free, is that people tend to revert to whatever is quickest and easiest for them...not what is definitively the most educational thing for the other person.

Nonetheless, if you are willing to investigate the system properly, you will find that you can achieve just about everything you need without ever opening a terminal window.

That being said, it is far easier to understand your system if you have a basic grasp of the command line, as its logic lies behind the way things like launchers work, along with lots of other bits of the system.

All in all, I agree with your rant within reason...it would be better if people always explained the cli command they present, and ideally explained the Gui method too, but in reality it won't happen...so I'm afraid you'll have to find out for yourself.

So search on google, read the man pages, and if necessary ask in the forum..someone will tell you what any given command does. In addition you can always ask if anyone knows of the gui equivalent...

P.S. as a general rule for nearly all archives I just right click and select to decompress them (can't remember the exact menu item - but its pretty obvious). It is very rare that I use tar -xvzf, in which, by the way, the xvz and f flags mean eXtract, Verbose logging, unZip, from File.

---

### Post by WinterWeaver on 2009-11-10
this thread should really be in the testimonials section =/

---

### Post by wojox on 2009-11-10
You don't always know what flavor of Ubuntu a person is using so you don't know what gui to tell them. Different stuff in Kubuntu than Ubuntu. The terminal always works for any version.

---

### Post by coffeecat on 2009-11-10
> **issih said:**
> Strongly disagree with alphaniner...

For 99% of the things we advise people to use a terminal command for there is an equivalent, and equally valid gui method.

+1

I'm not afraid of the terminal - I ran Gentoo as my main OS for 18 months - but it makes me despair when I see people respond to support requests with a load of terminal gibberish that could be implemented with a couple of mouse clicks. Sometimes the GUI is **quicker**.

---

### Post by mr_steve on 2009-11-10
Definitely 99% of the time I tell someone to run a command in the terminal it is because it's the best way to have them do exactly what needs to be done, and get exactly the right information back from them. Rather than trying to describe to them what they should click on, what part of the screen they should copy and paste, etc. I'd definitely rather tell someone to "sudo apt-get install blah" rather than have them clicking around starting synaptic, searching for the right package, marking it for installation, installing, etc.

I even do this for Windows users. If I want someone to check their IP address for example, I still find it much easier to have them open the command prompt and run ipconfig, rather than fiddling around with the control panels.

---

### Post by snowpine on 2009-11-10
Good points above; I agree with many of the other posters. But there's one thing that hasn't been mentioned yet about the terminal:

It is easier *for the person being helped* to attempt a CLI solution, because if error messages arise, they can simply cut and paste to the forum. 

If I give you instructions for installing something in Synaptic, but it doesn't work, you have to take a screenshot and figure out how to post it to the forums.

If I give you a terminal command, and it generates errors, cut & paste and the people here on the forums can help you, instead of guessing. 

"I tried installing wine but I got some error" is an all too common type of post on the forums. :( "Here is the terminal output when I try to install wine" will get you a much more helpful response. :)

---

### Post by mick55 on 2009-11-10
Hi BarisBlaq
> you're not really helping, unless you explain what those commands doIf someone takes the time to analyze your problem, then
troubleshoot it, then provide a solution, you should
be grateful, not annoyed that they didn't explain it.

When you use the GUI does anyone explain what commands
were invoked by all that pointing and clicking?

As others have stated, with all the different flavors of Ubuntu/Linux
the CLI is the only constant.

BarisBlaq the only person who can stop you gaining knowledge is you.
Otherwise i suggest you change your nickname to "Spoonfed"

mick

---

### Post by yknivag on 2009-11-10
> **BarisBlaq said:**
> Basically what i mean to say is - when you provide a bunch of terminal commands to solve whatever the question is, you're not really helping, unless you explain what those commands do, and what the other options are.

I think this is the crux of the problem.

I too give advice in the form of terminal commands because, as others have said already, they are (for the most part) desktop-agnostic and work for all users.

However, I do think that the OP makes a very valid point and that, especially when dealing with new(er) users there is much to be gained by taking the extra time to explain the command.

This needn't mean typing out the man page, but could simply be a sentence stating what it will do.

This is especially important in three cases I believe:

1. When requesting people post output for diagnostic purposes. Eg "post the output of ipconfig", say "the command ipconfig will list the current network configuration, post the output of it here so we can review it with you."  Then when offering advise based on that output, explain where in the output the useful information was.  This helps the poster to be able to diagnose the issue for themselves next time.

2. When requesting a user runs a command that makes a change to the system. Rather than saying "run xxxxx to fix your issue." say "running xxxxx with do yyyy and this will fix your issue.  If it doesn't work you can undo it by running zzzzz".

3. When giving complex command strings where the output of one is piped to another etc.  Taking the time to break this down and explain each section again gives the OP of a thread the chance to learn how the command works and how similar commands may be structured for other purposes.

I appreciate that it's extra work and that sometimes it can appear patronising, but as the OP of this thread says: "give a man a fish and you feed him for today, give him a rod and you let him feed himself" and by extension become part of the community to help others.

---

### Post by yknivag on 2009-11-10
> **mick55 said:**
> If someone takes the time to analyze your problem, then
troubleshoot it, then provide a solution, you should
be grateful, not annoyed that they didn't explain it.

I disagree, if that person doesn't take the time to explain how they analyzed, troubleshooted and solved the problem then all they have done is solve that one specific problem.

Taking the extra time to show how it was solved means that should the person encounter a similar problem in future (either themselves or from another user on the forums) they will be able to help themselves or that other new user.

The only way that the community will nurture the next generation of those trouble-shooters is to explain how it's done.

---

### Post by snowpine on 2009-11-10
I'll teach a man to fish if he shows interest in getting his feet wet.

I'm not going to waste more than 15 seconds (sudo apt-get install flashplugin-installer) on "How do I install Flash???"

Google is a much better fisherman than I could ever hope to be. :)

---

### Post by issih on 2009-11-10
The problem with cli commands is that for most users it is the equivalent of just presenting them with a fish...ready filleted and steamed.

An explanation of that cli command is like passing them a book on fishing and a recipe...perfect if you want to know all the little details, but somewhat overwhelming for a first stab.

A gui method explanation is like letting them watch as you catch the fish with the rod...gut it and then cook it.

They certainly won't be an expert in any of the steps after having seen that...but they could take a stab at most of them.

New users learn more from a gui than a cli methodology, at least until they have a decent feel for how the cli works.

Having said all that, I fully own up to being too lazy to properly explain sometimes...it is just human nature.

---

### Post by krakenfury on 2009-11-10
Like you I have used Ubuntu for about a year and until about a month ago, I wasn't using the terminal unless I had to.  I wanted to learn, I just didn't know how to teach myself, and I wasn't just picking it up through the forums.  I'm not completely comfortable with the terminal yet, but I am learning how to use it.

I can't believe no one has posted this yet:

[http://www.linux.org/lessons/beginner/index.html](http://www.linux.org/lessons/beginner/index.html)

AWESOME.  I'm going through this lesson by lesson and my fear of the terminal has disappeared.  I'm not completely proficient at it, but I'm getting better.  I do things from the terminal now just to get used to using it.  Just basic stuff like mv, mkdir, cp, rm, rmdir, all my updates, new packages.  Also info stuff like ls, grep, whatis, whereis, piping, less, more... These lessons ease you into the terminal at the perfect angle.  It's painless, trust me.

---

### Post by mick55 on 2009-11-10
Hi yknivag

> Taking the extra time to show how it was solved means that should the person encounter a similar problem in future (either themselves or from another user on the forums) they will be able to help themselves or that other new user.

The only way that the community will nurture the next generation of those trouble-shooters is to explain how it's done.     Show me one post on this forum where anyone does that.

People want their system to work, most don't give a rat's *ss
about how you deduced their problem.

Also the answers here are not empirical.
Most of the time we don't know what's going on and we throw
out suggestions.Look how many posts say"Try this" or 
"run this command and post the output"

If I had to explain my reasoning behind every suggestion i give
i would stop being a contributor.No one has that kind of time.
This isn't a job.

I believe the onus for learning to be on the student 
not the teacher.

Look at things from a real world viewpoint.

When a Doctor gives you a prescription, do you expect him
to tell you how he arrived at that diagnosis?
Of course not.

This is no different.

cheers
mick

---

### Post by blueridgedog on 2009-11-10
My .02:

The CLI is Linux.  As a Linux user, I can have any number of window managers and desktop environments.  I can not give instructions that assume you have xfce, when in fact you have gnome, or KDE.  In the future, you will use a different window manager and you will rely on your command line skills.  

In giving commands, we are in fact trying to teach you to fish.  The graphical tools are overlays on top of a rich and functional base that is the foundation and heritage of the OS.  We are teaching the core when we give commands.  Yes, that assumes we explain them and I sometimes forget to do so.  

Secondly, there are people who are here for help and there are people that are here for learning.  Some people just want problem X solved.  If I can help ten people with efficient commands and links to other posts or websites or one person with hand crafted replies detailing what each command consists of (or long posts of click this then that and look for this and the other thing), I will opt for the ten.  I try and give enough detail to be informative and helpful, and the opportunity always exists to ask for more information.  If I have helped you and you want to learn more, fantastic.  

Finally, I have used Linux since 1994 and when I have a problem, I am using a terminal to solve the problem.  I can only teach what I know.  The GUI is in a state of flux and as stated above, not standard from user to user.  Solutions that require a GUI can not be implemented in many recovery situations.

---

### Post by mick55 on 2009-11-10
Blueridgedog you hit the nail on the head.

Here's a scenario for you.

Complete noob needs to compile from source.
Walking them through this is going to be extremely 
difficult due to lack of familiarity with the CLI.
If we can accomplish this daunting task we are all happy.
Now, imagine having to explain to the noob exactly what all 
those commands mean and what they do

Hey, be my guest and explain them all to a noob

# **tar xvzf package.tar.gz** (or **tar xvjf package.tar.bz2**)
        # **cd package**
        # **./configure**
        # **make**
        # **make install**


My point is when the student is ready the teacher will appear.

peace
mick

---

### Post by doas777 on 2009-11-10
> **mick55 said:**
> 
My point is when the student is ready the teacher will appear.


very sage. I've been in IT for a while now, and gave linux a try several times over the years, but was never successful with it. then in '07, I tried feisty, and lo and behold, for the first time, **i was ready for linux, and linux was ready for me**. the rest is history.

---

### Post by benj1 on 2009-11-10
well i can't speak for anyone else, but if someone asked i would be happy to give a breakdown of a command.

im not about to go into a big indepth explanation if i don't know the other person, i dont know how much they know or anything, theres no point going into a long winded explanation of 'cp' if the OP already knows what it is, if they don't and they ask i will explain.

---

### Post by mick55 on 2009-11-10
Right on Benj1

> theres no point going into a long winded explanation of 'cp' if the OP already knows what it is, if they don't and they ask i will explain.The Middle Way.

I think this is very sensible and should satisfy both sides.

The student has to exhibit a willingness to learn.

peace
mick

---

### Post by Mornedhel on 2009-11-11
> **BarisBlaq said:**
> But i keep recalling the old phrase - give a man a fish, you have fed him for today.. Teach a man to fish, and you have fed him for a lifetime.

Like i said, i been happily using ubuntu for about a year now, but every time i ask a question on the forums, and someone responds with "wget this and that" and "tar -xzwf" - i get the chills..

You are very welcome to point out that I haven't read the man pages about tar, but i am a lazy guy, and after a year of going solo on ubuntu, i still don't know what -xzfw means. I'm not even sure if i remember that right.

Sorry, can't help you there. You say you want to learn, but that you are lazy. We can't help you be not lazy.

If you ask a question on the forums and don't understand the answer, make the effort of asking the seriouser-sounding posters what the commands mean. There are some who will launch one-shot answers and never come back to the thread (never mind if the problem has already been solved and the answer posted by someone else).

Identify those who answer in a bit more detail and ask them questions. Most of the time those posters don't explain because few newcomers actually want to understand; some even point out that they don't want explanations, just "tell me what to write". I for one will be happy to explain my answer. Before asking questions, though, there is something else you should do:

You say you don't read the man pages. Read them. They contain documentation. Documentation explains what things do.

Finally, I'll refer you to this piece of advice, written by Eric S. Raymond, who is kind of a big name in the FOSS community : [How To Ask Questions the Smart Way](http://linuxmafia.com/faq/Essays/smart-questions.html). It's rather long, but worth reading.

---

### Post by alphaniner on 2009-11-11
> [Y]ou're not really helping, unless you explain what those commands do, and what the other options are.

I stand by my opinion that this is not an attitude appropriate for someone who would be a Linux administrator.  Because that's what we all are, to some extent or another.

People who demand to be spoon fed are doing a disservice to the whole community.  Especially when you consider the volume of threads that could have been avoided by some quality time with Google, or a forum search.

---

### Post by bonfire89 on 2009-11-11
> **BarisBlaq said:**
>  i still don't know what -xzfw means. I'm not even sure if i remember that right.


I'm at least 2 years in... and I totally agree with you haha


> **BarisBlaq said:**
> 
Basically what i mean to say is - when you provide a bunch of terminal commands to solve whatever the question is, you're not really helping, unless you explain what those commands do, and what the other options are.


this is true.




I'm only starting now to think on my own, looking up man pages, doing my own commands that weren't explicitly told to me.. but even then.. I can't think for myself too much yet.

---

### Post by dmizer on 2009-11-11
> **bonfire89 said:**
> I'm at least 2 years in... and I totally agree with you haha

At the risk of posting an RTFM post, there are usually helps for these kind of things. A simple: tar --help command tells you what each of the options mean:
```
-x, --extract, --get       extract files from an archive
-z, --gzip, --gunzip, --ungzip   filter the archive through gzip
-f, --file=ARCHIVE         use archive file or device ARCHIVE
-w, --interactive, --confirmation
                             ask for confirmation for every action
```

Sometimes the manuals are so cryptic they may as well have not been written, but this is not always the case so it's worth a look if you get stuck.

---

### Post by benj1 on 2009-11-11
i can never remember the tar commands, i just use this in my ~/.bashrc

```

function extract()       # Handy Extract Program.
{
     if [ -f $1 ] ; then
         case $1 in
              *.tar.bz2)   tar xvjf $1     ;;
              *.tar.gz)    tar xvzf $1     ;;
              *.bz2)       bunzip2 $1      ;;
              *.rar)       unrar x $1      ;;
              *.gz)        gunzip $1       ;;
              *.tar)       tar xvf $1      ;;
              *.tbz2)      tar xvjf $1     ;;
              *.tgz)       tar xvzf $1     ;;
              *.zip)       unzip $1        ;;
              *.Z)         uncompress $1   ;;
              *.7z)        7z x $1         ;;
              *)           echo "'$1' cannot be extracted via >extract<" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

```

---

### Post by issih on 2009-11-11
> **alphaniner said:**
> I stand by my opinion that this is not an attitude appropriate for someone who would be a Linux administrator.  Because that's what we all are, to some extent or another.

People who demand to be spoon fed are doing a disservice to the whole community.  Especially when you consider the volume of threads that could have been avoided by some quality time with Google, or a forum search.

If you take the position that linux should only ever be for those that have a good, clear understanding of its technical guts and can therefore contribute back into the community in what might be termed a "meaningful" way, then that attitude is fine.

For a distro like Ubuntu however it is not acceptable. Ubuntu is aiming to be "for human beings" to be for the masses, and bug #1 is all about increasing market share. Those of us who are strong technical users with a good understanding of computing/cli/programming etc will NEVER be the majority, and consequently we will never further the aims of the disto if we adopt that kind of attitude.

We have to be aiming to make it as easy as possible for users who are never going to write code/scripts/hack drivers etc to get around the system and understand what is happening as much as they can...and this must happen on their terms not ours, or we will remain entirely stuck at the margins.

Now there are plenty who will argue that those aims are wrong and that the nature of OSS requires its users to be technical and engaged in order to be a useful and therefore welcome member of the community...I can't be bothered having that argument again, because the views on both sides tend to be intractable. Regardless of that however, for this distro, the decision has been made to go for the mass market, and that requires that we cater to those who are less technically able, and do so in the way that helps them learn the most that they can, so that they actually feel that they have some understanding of their computer.

The current system where undocumented cli responses prevail has lots of reasons behind it (many of them good) but it is fundamentally holding back the aims of the distro, and I personally think that those who run this forum should endeavour to find some form of solution - not that an easy one seems to actually exist.

---

### Post by blueridgedog on 2009-11-11
> **issih said:**
> 
The current system where undocumented cli responses prevail has lots of reasons behind it (many of them good) but it is fundamentally holding back the aims of the distro, and I personally think that those who run this forum should endeavour to find some form of solution - not that an easy one seems to actually exist.

As long as the window manager you select is variable and the medium of support is text based, support will gravitate to the command line.  I suggest that perhaps we could use graphical support methods in the absolute beginners forum, but it is hard to answer a meaningful number of questions as a volunteer without using the tools that we actually use ourselves.  

Can you imagine asking for a description of what is seen when gparted (or knowing that they have palimpsest) is run versus asking for the output of "sudo fdisk -l"?  I do agree that it is a hurdle we have to get over, but I see no way over it easily without the people trying to field a few questions each day here having vertial images of multiple releases and multiple window managers.

---

### Post by t0p on 2009-11-11
> **BarisBlaq said:**
> .
Yet I'm still afraid of the terminal.

When a noob like meself asks a question on the forums, it will most likely get a response. The solution will most likely involve running some commands over the terminal. It will most likely solve the problem in hand. This is certainly a good thing.

But i keep recalling the old phrase - give a man a fish, you have fed him for today.. Teach a man to fish, and you have fed him for a lifetime.

Like i said, i been happily using ubuntu for about a year now, but every time i ask a question on the forums, and someone responds with "wget this and that" and "tar -xzwf" - i get the chills..

You are very welcome to point out that I haven't read the man pages about tar, but i am a lazy guy, and after a year of going solo on ubuntu, i still don't know what -xzfw means. I'm not even sure if i remember that right.

I do acknowledge the fact that guiding some helpless noob like me is far easier through a series of shell commands, compared to posting in screenshots- doing it the lame way.

It also ascertains a distinction among "classes" of ubuntu (or linux) users - if you know the shell, you're in.

If you are afraid of the shell (like meself, not because I now feel more comfortable with a graphic environment, but because I feel less comfortable with typing in commands i dont know what they mean) - well, dunno, you're afraid of the shell.

Basically what i mean to say is - when you provide a bunch of terminal commands to solve whatever the question is, you're not really helping, unless you explain what those commands do, and what the other options are.


So when someone tells you to run such-and-such a command... don't do it.  Instead, look up that command's manpage.  Don't run the command until you are sure you know what you are doing.  The manpages are installed on your computer.  What's the problem?

Do you really expect, when you ask for help, that someone is going to take you by the little hand and teach you the intricasies of the subject?  Do you really expect volunteers on a volunteer forum to go into such detail?

You ask for help, you get help.  You want to know more, the manpages and Google are your friends.

Sheesh.

---

### Post by yknivag on 2009-11-11
> **mick55 said:**
> Hi yknivag

Show me one post on this forum where anyone does that.

<snip>

If I had to explain my reasoning behind every suggestion i give
i would stop being a contributor.No one has that kind of time.
This isn't a job.

And (in my personal view) therein lies the problem.  Why do we have so many duplicate posts? So many people who post the same thing after each upgrade and are told to blindly run the same commands.  If they were told what they do then they stand a chance of doing it again on their own.

How much more time does it take to provide a one line explanation of what the command does?

> **mick55 said:**
> When a Doctor gives you a prescription, do you expect him
to tell you how he arrived at that diagnosis?
Of course not.

Of course not.  I know what diagnosis he did! I was there being prodded and poked whilst he was doing it!

> **mick55 said:**
> Blueridgedog you hit the nail on the head.

Here's a scenario for you.

Complete noob needs to compile from source.
Walking them through this is going to be extremely 
difficult due to lack of familiarity with the CLI.
If we can accomplish this daunting task we are all happy.
Now, imagine having to explain to the noob exactly what all 
those commands mean and what they do

Hey, be my guest and explain them all to a noob

# **tar xvzf package.tar.gz** (or **tar xvjf package.tar.bz2**)
        # **cd package**
        # **./configure**
        # **make**
        # **make install**

Quite easily as follows:

> First unzip and unpack the tarball with ```
tar xvzf package.tar.gz
``` then change directory to the package ```
cd package
``` and run the following three commands which configure, compile and install the package. ```
./configure
make
make install
```
It is worth pointing out that this process will work with any such package downloaded.

I really don't see how that takes that much longer or removes the opportunity to help others.

---

### Post by SunnyRabbiera on 2009-11-11
To be honest the terminal is becoming less needed as time goes on in linux, but people will always give out terminal tutorials no matter what in linux as they try to play neutral.

---

### Post by yknivag on 2009-11-11
The other advantage of explaining (however briefly) what is happening also helps those people searching forums before posting their own thread to find something which answers their question.  Or something which answers a question very similar to theirs with enough information for them to be able to work out a solution.

A good thread should not just serve the OP but those reading it with the same issue.  This also serves to reduce the number of repeat requests for the same problem.

It's all well telling people to search before posting (which means we all have to repeat ourselves less) but if the answers given are too brief to be of use to them then they will post again anyway.

I'm not suggesting anyone should shy away from CLI solutions - quite the opposite. Just suggesting that a few seconds invested now may reduce many hours of repeating oneself in infinite threads to come.

---

### Post by alphaniner on 2009-11-11
> **issih said:**
> If you take the position that linux should only ever be for those that have a good, clear understanding of its technical guts

This isn't the point I intended to make.  I certainly think Linux should be *usable* by anyone and everyone.  But using and *administering* are different things.

And it isn't even necessarily a matter of knowledge or understanding, but rather initiative.  The OP admitted he is *too lazy to even check a man page*.  Such a person should **not be administering an OS**, Linux or otherwise.

---

### Post by snowpine on 2009-11-11
Aaaand in the time we all took writing this thread, we could have helped 36 noobs with their problems. :)

---

### Post by lykwydchykyn on 2009-11-11
> **snowpine said:**
> Aaaand in the time we all took writing this thread, we could have helped 36 noobs with their problems. :)

Yes, but we could only have helped so many by using CLI commands, the practice of which is apparently "holding linux back".  So, by not helping noobs, we've been allowing Linux to move forward.

Or, something like that. :confused:

---

### Post by benj1 on 2009-11-11
> **issih said:**
> 
For a distro like Ubuntu however it is not acceptable. Ubuntu is aiming to be "for human beings" to be for the masses, and bug #1 is all about increasing market share. Those of us who are strong technical users with a good understanding of computing/cli/programming etc will NEVER be the majority, and consequently we will never further the aims of the disto if we adopt that kind of attitude.

We have to be aiming to make it as easy as possible for users who are never going to write code/scripts/hack drivers etc to get around the system and understand what is happening as much as they can...and this must happen on their terms not ours, or we will remain entirely stuck at the margins.

Now there are plenty who will argue that those aims are wrong and that the nature of OSS requires its users to be technical and engaged in order to be a useful and therefore welcome member of the community...I can't be bothered having that argument again, because the views on both sides tend to be intractable. Regardless of that however, for this distro, the decision has been made to go for the mass market, and that requires that we cater to those who are less technically able, and do so in the way that helps them learn the most that they can, so that they actually feel that they have some understanding of their computer.

The current system where undocumented cli responses prevail has lots of reasons behind it (many of them good) but it is fundamentally holding back the aims of the distro, and I personally think that those who run this forum should endeavour to find some form of solution - not that an easy one seems to actually exist.
I have to disagree, everybody here is volunteering their time, neither the forum staff, canonical or newbies can demand that we spoon feed people, if they want that then they can pay for support.


[QUOTE=snowpine]
Aaaand in the time we all took writing this thread, we could have helped 36 noobs with their problems. 
[/QUOTE]
true I would defend it tho, because i don't come here purely to help newbs, yes i will when i come across a post but im sure i would probably visit less if it were just a purely technical forum.

---

### Post by issih on 2009-11-11
> **lykwydchykyn said:**
> Yes, but we could only have helped so many by using CLI commands, the practice of which is apparently "holding linux back".  So, by not helping noobs, we've been allowing Linux to move forward.

Or, something like that. :confused:

Thats just silly.... I started out by saying that the best response for a user is to investigate and to ask things if they want to know...

But its a double edged sword.. if there is a best practice for new users, then there is also a best practice for those of us that offer help.

Clearly any help is better than no help, but I am trying to point out that the OP has a point in criticising the use of undocumented CLI commands. It is inevitable that it will happen, and I have owned up to doing it myself. Nonetheless people should think about the reasons why it might not be the optimal way to solve problems.

Oh and I said it was "holding back the aims of the distro" if you use quotation marks you should actually quote things :)

As for benj1's comments.. I actually entirely agree, there is no onus on anyone to offer anything, as we do it out of kindness, but if you want to help people, then helping them in the way that helps them the most is better than helping them in the way that is easiest for you.

If the extra time that takes makes it not worth your while, then its entirely up to you to decide to do it the quick way, or indeed to choose not to do it at all.

Nonetheless we should think about the shortcuts we take and the impact that they have.....

P.S. By alphaniners logic the vast majority of windows users shouldn't be administering their pcs....and yet they are. That is the fundamental point, there are millions upon millions of people who are administering their pcs without having half the knowledge that ideally they should have to be doing that job. If ubuntu wants to be a large market share distro (which is its stated aim), it has to cater for them, because they are not going to suddenly develop those skills overnight just because they download an iso.

---

### Post by benj1 on 2009-11-11
> **issih said:**
> 
P.S. By alphaniners logic the vast majority of windows users shouldn't be administering their pcs....and yet they are. That is the fundamental point, there are millions upon millions of people who are administering their pcs without having half the knowledge that ideally they should have to be doing that job. If ubuntu wants to be a large market share distro (which is its stated aim), it has to cater for them, because they are not going to suddenly develop those skills overnight just because they download an iso.

does that mean we should aim to keep them ignorant, a la windows ? ;)

---

### Post by issih on 2009-11-11
> **benj1 said:**
> does that mean we should aim to keep them ignorant, a la windows ? ;)

I think my previous posts explain my position there quite clearly..I am the one advocating explaining things after all :)

In all honesty though... in any scenario where Ubuntu manages to wrestle lets say 5% of the market share away from its competitors, there will be a massive jump in the number of users who are very wary of their computer, and have little to no knowledge of how it works. That is a direct and inevitable side effect of increased market share, and the ways of dealing with that populous must be considered now, both within the OS itself and within the wider community...

I don't really expect that to happen anytime soon though...

---

### Post by alphaniner on 2009-11-11
> **issih said:**
> P.S. By alphaniners logic the vast majority of windows users shouldn't be administering their pcs....and yet they are. That is the fundamental point, there are millions upon millions of people who are administering their pcs without having half the knowledge that ideally they should have to be doing that job. If ubuntu wants to be a large market share distro (which is its stated aim), it has to cater for them, because they are not going to suddenly develop those skills overnight just because they download an iso.

Yes, you have my logic correct.  And the logic seems to be followed in most realms of human activity.  I'm reminded of the first time I tried to change my brakes and frakked up.  I took it to the mechanic and he told me that if I hadn't been friends with the owner of the shop, he would have laughed at me and sent me on my way.  The point was, either **learn to do it right** or don't do it at all.  Point taken.  Being a stubborn cheapskate, I chose the former.

There are consequences from all those people who are [poorly] administering their Windows machines.  And I don't believe it's possible to achieve the so-called advantages of Windows, without also picking up many of the disadvantages.  Not to mention the shady business practices...

Every thing has a price, even Linux.  A signature I once saw here put it best, "Linux is only free if your time is worth nothing."  People who aren't prepared to pay the price in time and effort have the option of paying the meagre price for a commercially supported product *a la* System76.

If creating more system administrators who know next to nothing about the system they are administering is a goal of Ubuntu, then I guess I should get out while I can.

---

### Post by benj1 on 2009-11-11
> **alphaniner said:**
>  And I don't believe it's possible to achieve the so-called advantages of Windows...

remind me what they are again ?
> 
Every thing has a price, even Linux.  A signature I once saw here put it best, "Linux is only free if your time is worth nothing."  People who aren't prepared to pay the price in time and effort have the option of paying the meagre price for a commercially supported product.
+1

---

### Post by mick55 on 2009-11-11
Where is the OP?

I smell a Troll.

---

### Post by mdshann on 2009-11-11
One of the problems with a lot of users is they just don't care how things work. The same thing happens day in and day out where I work, people bring me their computers and I fix them and when they come to pick them up the vast majority of them don't even want to know how I fixed it, let alone try to understand when I attempt to explain it to them. The same thing happens when you take your car to the shop. The mechanic fixes it and you pick it up and go on your way happy that you can drive to work without taking the bus again. Now I know that there are exceptions and some people genuinely do want to have an understanding of what is happening under the hood, what the problem was, and how it was fixed but most people simply want their stuff to work. Most people are not like that though. This is why when people reply to forum posts most will give you a CLI command to run to fix your problem without explaining what is done because that is what most people expect, someone to tell them exactly how to fix the problem or to do it for them so that they don't have to take the time to understand. 

Now being that most of us here are probably fairly technical people or at least understand that our computers are not magic fairy boxes or something, I do think it is important that people explain things to others. That said I think that the default response to a question should simply be the fix, followed by an explanation if the OP asks for it. This I think is a whole lot less insulting and makes things go quicker than if the 'helper' writes a 3 paragraph long post explaining how the problem was fixed every time someone asks a question.

---

### Post by lykwydchykyn on 2009-11-11
> **issih said:**
> Thats just silly....

Yes... it is.  I was misquoting you and being silly.  :) Come on, it was funny.

^_^

---

### Post by 3rdalbum on 2009-11-11
> **BarisBlaq said:**
> Basically what i mean to say is - when you provide a bunch of terminal commands to solve whatever the question is, you're not really helping, unless you explain what those commands do, and what the other options are.

That's true. Explaining the options is a very good thing. I'm not sure I could explain what the other options are; it's a bit outside the scope of the thread and can lead to confusion.

I personally always say "Open Synaptic Package Manager and hit the Reload button" instead of "Run sudo apt-get update" (unless the poster is running without a GUI).

Wget is just a program that reliably downloads files from the Internet; you can use Firefox to download whatever file too, but Wget makes sure that you've got the whole file.

Instead of using 'tar' on the command line, you can just open the archive in File Roller. I've only used the 'tar' command once EVER and I can't remember what options it takes; I've always just used File Roller or some other archiving GUI.

---

### Post by utnubuuser on 2009-11-12
Wake up Neo_ _ _ __ _ _ _   ...the matrix has you!!!

---

### Post by zephyrblade on 2009-11-12
Could someone please post a video summary of this thread on youtube, and provide me the link? I would really like to learn more about it, but I really can't be bothered reading words ...

---

### Post by Mornedhel on 2009-11-12
> **issih said:**
> In all honesty though... in any scenario where Ubuntu manages to wrestle lets say 5% of the market share away from its competitors, **there will be a massive jump in the number of users who are very wary of their computer, and have little to no knowledge of how it works**. That is a direct and inevitable side effect of increased market share, and the ways of dealing with that populous must be considered now, both within the OS itself and within the wider community...

Wake up!

This has already happened. Were you around before Ubuntu? Any idea what being a hacker really means? (meant?)

The current Ubuntu culture is already one of spoonfeeding. I just googled "tar xvzf" and the first result was relevant and answered the OP's questions. Some questions have been asked over and over again in the forum, because no one bothers to search the same forum in case someone has had the same issue. Some newcomers actually ask you not to provide the explanations because they don't care. The stickies alone, if every user was forced to check them before asking away, would probably reduce the traffic on Beginners by 50% by themselves.

I used to explain commands in the Beginners section. I don't do that anymore unless the newbie really shows a commitment to understand what we're talking about. Otherwise you get told "I'm not a programmer, Ubuntu isn't ready for the mainstream if you need to do it in the terminal, I don't have time for this, I'm going back to Windows".

---

### Post by issih on 2009-11-12
> **Mornedhel said:**
> Wake up!

This has already happened. Were you around before Ubuntu? Any idea what being a hacker really means? (meant?)

The current Ubuntu culture is already one of spoonfeeding. I just googled "tar xvzf" and the first result was relevant and answered the OP's questions. Some questions have been asked over and over again in the forum, because no one bothers to search the same forum in case someone has had the same issue. Some newcomers actually ask you not to provide the explanations because they don't care. The stickies alone, if every user was forced to check them before asking away, would probably reduce the traffic on Beginners by 50% by themselves.

I used to explain commands in the Beginners section. I don't do that anymore unless the newbie really shows a commitment to understand what we're talking about. Otherwise you get told "I'm not a programmer, Ubuntu isn't ready for the mainstream if you need to do it in the terminal, I don't have time for this, I'm going back to Windows".

Last thing I can be bothered with in this thread as the standard intractable positions have been reached.

Undocumented cli commands lend themselves to people asking the questions again and again...because they have a similar problem, but are not sure what the command posted for the similar fix did, so they have no clue if it is truly relevant to their current issue.

Could they google it and learn? yes of course they could, but you are expecting ideal behaviour, from people who in some cases have no idea what even the basic syntax of the command line is, and for whom reading a man page is like trying to read chinese (unless of course they are chinese :)).

A passenger wants to catch a train....but the train station has no timetables, no departure board...nothing at all that the passenger recognises so they ask a nearby guard. The guard says that the train goes from platform 6, but there are no platform numbers, so the passenger goes to another guard and asks where platform 6 is.

Eventually they walk down some stairs to find a completely black train with no markings at all, nothing to indicate where it is going. So the passenger panics a bit, and eventually asks once more and is informed that yes, this is the train you want.

Now, if the first guard had pointed out that the kiosk stocks free infra-red glasses, and that all the signposts are visible if you are wearing them.....

Sometimes the simple answer to a question is the wrong thing to do...

and I'm out :) have fun

---

### Post by benj1 on 2009-11-12
> **issih said:**
> 
A passenger wants to catch a train....but the train station has no timetables, no departure board...nothing at all that the passenger recognises so they ask a nearby guard. The guard says that the train goes from platform 6, but there are no platform numbers, so the passenger goes to another guard and asks where platform 6 is.

Eventually they walk down some stairs to find a completely black train with no markings at all, nothing to indicate where it is going. So the passenger panics a bit, and eventually asks once more and is informed that yes, this is the train you want.

Now, if the first guard had pointed out that the kiosk stocks free infra-red glasses, and that all the signposts are visible if you are wearing them.....

your analogy is flawed, first this suggests we are making things harder than the need to be, second it suggests that googling isn't an obvious first step to solving a problem.

---

### Post by issih on 2009-11-12
Nope...I'm suggesting that things are only easy to understand if you have cleared the initial knowledge jump necessary to understand how to understand them...that is exactly analagous.

As for googling, its an obvious first step for you and me, but you know as well as I do that a huge number of people do not do it, once again you are expecting ideal behaviour...and that is not realistic.

Finally the simple fact is that people who have an issue with ubuntu and have already found this forum think they have already reached the place to get help...they have done their googling, and found what looks to be a good place to ask questions...and they do, without really thinking about it. They don't know that the forum's very nature and linux's quirks will conspire to mean that the help they get will tend to be in an alien form, and generally very terse.

This is how the vast majority of people work, they get stuck, they ask someone else. You and I know how to use google to find the answers to technical issues, its easy, because we have already cleared that initial level of understanding that makes everything else understandable..not everyone has, and the current system tends to perpetuate the situation.

and with that...I really am done

Bye thread :)

---

### Post by alphaniner on 2009-11-12
> **issih said:**
> As for googling... you are expecting ideal behaviour...and that is not realistic.

Yes, much like expecting people to put on pants, or fuel up their cars, is idealistic and unrealistic.

People shouldn't have to develop a whole new skill set just to *use* a computer, sure.  But installing, configuring, and administering an OS is much more than just using a computer.  The fact that Windows has somewhat blurred the line between these activities is not something to be emulated.  And expecting to attain all of the 'Windows good' without any of the 'Windows bad' is a most sinister bit of idealism.

---

### Post by blur xc on 2009-11-12
> **BarisBlaq said:**
> Basically what i mean to say is - when you provide a bunch of terminal commands to solve whatever the question is, you're not really helping, unless you explain what those commands do, and what the other options are.


I agree...  I've been in the same boat, except I've been working hard to get comfortable with the CLI.  One big help has been to read as many Linux CLI books as I can get my hands on.

Here's an example I ran across today:
> **sudo apt-get install lamp-server^**

last character is magical, don't forget it. Taken from  this thread:  [http://ubuntuforums.org/showpost.php?p=8293134&postcount=7](http://ubuntuforums.org/showpost.php?p=8293134&postcount=7)

Why is that last character magical???  Seriously, why say it's magical but not say why?

BM

---

### Post by alphaniner on 2009-11-12
> **blur xc said:**
> Why is that last character magical???  Seriously, why say it's magical but not say why?

I'd guess it has something to do with the fact that **lamp-server** isn't actually a package.  But I agree, that's the kind of thing that ought to be explained.

---

### Post by hoppipolla on 2009-11-12
I dunno man, it's quick and easy and makes fixing people's OSs a breeze...

I don't mind if people don't want to learn to use the terminal or whatever that's totally cool, and if they don't want me to use it to fix their machines then I guess I won't, but... it's just very, very powerful. It's up to you though, Ubuntu does have a LOT of UI tools so you don't have to go into terminal too much if you don't want to :)

---

### Post by hoppipolla on 2009-11-12
> **alphaniner said:**
> I'd guess it has something to do with the fact that **lamp-server** isn't actually a package.  But I agree, that's the kind of thing that ought to be explained.

oh, I actually don't understand that either, but I would probably just smile and nod if someone told me to put it in (but then ask about it so I learn :) )

So... what does it do? O.O

---

### Post by alphaniner on 2009-11-12
I am doing my darndest to find out.  I'm quite certain it isn't explained in the apt-get man page, or any of the **apt-doc** stuff.

---

### Post by aysiu on 2009-11-12
If someone asks for help with a common task, I will usually give point-and-click instructions.

If it's a problem that needs troubleshooting, there probably isn't a catch-all solution. It needs to be approached on a case-by-case basis anyway, so there is no "teaching a woman to fish" in those situations.

If someone has a problem, I say "Paste these commands into the terminal and paste the output back here" and then "Paste this command in."

If that solves the problem, I get a thank-you and the OP is happy.

> **benj1 said:**
> well i can't speak for anyone else, but if someone asked i would be happy to give a breakdown of a command And I have had a few rare occasions in which someone says "That was great. Can you explain what that command did?" and I'm more than happy to explain.

Most people don't care, though.

---

### Post by MaxIBoy on 2009-11-12
My policy is that I always give instructions for the CLI, but I explain anything which isn't totally obvious. I also have a small yet growing collection of canned answers to frequently asked questions, or canned explanations of frequently used commands. (Especially sudo! That one gets used a lot.) I do try to figure out how much of that information someone doesn't already know judging by their posts.

I would encourage others to do the same.

---

### Post by Mornedhel on 2009-11-13
> **hoppipolla said:**
> oh, I actually don't understand that either, but I would probably just smile and nod if someone told me to put it in (but then ask about it so I learn :) )

So... what does it do? O.O

Explanation required? Explanation follows.

lamp-server is a tasksel task. See tasksel --list-tasks to get a list of common tasks. Tasks are package selections that implement a particular functionality, in our case a linux-apache-mysql-php server. See tasksel --task-desc <taskname> to get a short description of the task. See tasksel --task-packages to get a list of packages belonging to the task.

apt-get install taskname^ is the same as tasksel install taskname.

---

### Post by alphaniner on 2009-11-13
> **Mornedhel said:**
> Explanation required? Explanation follows.

Thanks.

---

### Post by scorp123 on 2009-11-13
> **blur xc said:**
>  Why is that last character magical?? No idea. Until 5 minutes ago when I simply tried out what would happen :D

Enter the "--simulate" parameter for apt-get ...

```
> sudo apt-get --simulate install lamp-server^

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwrap0 is already the newest version.
libmysqlclient15off is already the newest version.
mysql-server-core-5.0 is already the newest version.
tcpd is already the newest version.
ssl-cert is already the newest version.
libpq5 is already the newest version.
mysql-common is already the newest version.
libwrap0 is already the newest version.
libmysqlclient15off is already the newest version.
mysql-server-core-5.0 is already the newest version.
tcpd is already the newest version.
ssl-cert is already the newest version.
libpq5 is already the newest version.
mysql-common is already the newest version.
The following extra packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl
  libplrpc-perl mysql-client-5.0 mysql-server mysql-server-5.0 php5-common php5-mysql
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom php-pear dbishell libipc-sharedcache-perl mysql-doc-5.0 tinyca
The following NEW packages will be installed
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl
  libplrpc-perl mysql-client-5.0 mysql-server mysql-server-5.0 php5-common php5-mysql
0 upgraded, 17 newly installed, 0 to remove and 0 not upgraded.
Inst libnet-daemon-perl (0.43-1 Ubuntu:9.04/jaunty)
Inst libplrpc-perl (0.2020-1 Ubuntu:9.04/jaunty)
Inst libdbi-perl (1.607-1 Ubuntu:9.04/jaunty)
Inst libdbd-mysql-perl (4.008-1 Ubuntu:9.04/jaunty)
Inst mysql-client-5.0 (5.1.30really5.0.75-0ubuntu10.2 Ubuntu:9.04/jaunty-updates)
Inst mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2 Ubuntu:9.04/jaunty-updates)
Inst libapr1 (1.2.12-5ubuntu0.1 Ubuntu:9.04/jaunty-updates)
Inst libaprutil1 (1.2.12+dfsg-8ubuntu0.3 Ubuntu:9.04/jaunty-updates)
Inst apache2-utils (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Inst apache2.2-common (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Inst apache2-mpm-prefork (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Inst apache2 (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Inst php5-common (5.2.6.dfsg.1-3ubuntu4.2 Ubuntu:9.04/jaunty-updates)
Inst libapache2-mod-php5 (5.2.6.dfsg.1-3ubuntu4.2 Ubuntu:9.04/jaunty-updates)
Inst libhtml-template-perl (2.9-1 Ubuntu:9.04/jaunty)
Inst mysql-server (5.1.30really5.0.75-0ubuntu10.2 Ubuntu:9.04/jaunty-updates)
Inst php5-mysql (5.2.6.dfsg.1-3ubuntu4.2 Ubuntu:9.04/jaunty-updates)
Conf libnet-daemon-perl (0.43-1 Ubuntu:9.04/jaunty)
Conf libplrpc-perl (0.2020-1 Ubuntu:9.04/jaunty)
Conf libdbi-perl (1.607-1 Ubuntu:9.04/jaunty)
Conf libdbd-mysql-perl (4.008-1 Ubuntu:9.04/jaunty)
Conf mysql-client-5.0 (5.1.30really5.0.75-0ubuntu10.2 Ubuntu:9.04/jaunty-updates)
Conf mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2 Ubuntu:9.04/jaunty-updates)
Conf libapr1 (1.2.12-5ubuntu0.1 Ubuntu:9.04/jaunty-updates)
Conf libaprutil1 (1.2.12+dfsg-8ubuntu0.3 Ubuntu:9.04/jaunty-updates)
Conf apache2-utils (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Conf apache2.2-common (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Conf apache2-mpm-prefork (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Conf apache2 (2.2.11-2ubuntu2.3 Ubuntu:9.04/jaunty-updates)
Conf php5-common (5.2.6.dfsg.1-3ubuntu4.2 Ubuntu:9.04/jaunty-updates)
Conf libapache2-mod-php5 (5.2.6.dfsg.1-3ubuntu4.2 Ubuntu:9.04/jaunty-updates)
Conf libhtml-template-perl (2.9-1 Ubuntu:9.04/jaunty)
Conf mysql-server (5.1.30really5.0.75-0ubuntu10.2 Ubuntu:9.04/jaunty-updates)
Conf php5-mysql (5.2.6.dfsg.1-3ubuntu4.2 Ubuntu:9.04/jaunty-updates)
```


> **blur xc said:**
>  Seriously, why say it's magical  Because there is no package with that name "lamp-server" ... and yet this syntax manages to pull in all the dependencies. So yes, it is "magical". So as of writing this line I have no clue why this works ... but it does work. For me that would be the more important part.


> **blur xc said:**
>  but not say why? 5 minutes into writing an answer for you and I found the answer to this question. Simply by reading the manual of "apt-get".

Quote from there:
> If no package matches the given expression and the expression contains one of ´.´, ´?´ or ´*´ then it is assumed to be a POSIX regular expression, and it is applied to all package names in the database. Any matches are then installed (or removed). Note that matching is done by substring so ´lo.*´ matches ´how-lo´ and ´lowest´. If this is undesired, anchor the regular expression with a ´^´ or ´$´ character, or create a more specific regular expression. 

RTFM is the key ;)

So what it does obviously: The above command does not tell "apt" to install a certain package (there is no such package with such a name) but instead feeds it with a UNIX-style regular expression and as consequence "apt" pulls in all the packages that have anything to do with "lamp-server"

Looking e.g. at the "apache2.2-common" package via "apt-cache show" we can see that there is a field "Tasks:" where the string "lamp-server" occurs.

> > apt-cache show apache2.2-common

Package: apache2.2-common
Priority: optional
Section: web
Installed-Size: 3764
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: amd64
Source: apache2
Version: 2.2.11-2ubuntu2.3
Replaces: apache2-common
Depends: libapr1, libaprutil1, libc6 (>= 2.4), libssl0.9.8 (>= 0.9.8f-5), libuuid1 (>= 1.05), zlib1g (>= 1:1.1.4), apache2-utils, net-tools, libmagic1, mime-support, lsb-base, procps, perl
Recommends: ssl-cert
Suggests: www-browser, apache2-doc, apache2-suexec | apache2-suexec-custom, ufw
Conflicts: apache2-common, libapache2-mod-mime-xattr (<= 0.3-2), libapache2-mod-mono (<= 1.1.17-3), libapache2-mod-php4 (<= 4:4.4.4-2), libapache2-mod-php5 (<= 5.1.6-3), libapache2-mod-proxy-html (<= 2.4.3-2), libapache2-mod-scgi (<= 1.11-1), libapache2-mod-speedycgi (<= 2.22-3), libapache2-modxslt (<= 2005072700-1), libapache2-redirtoservername (<= 0.1-1), libapache2-webauth (<= 3.5.3-1), libapache2-webkdc (<= 3.5.3-1)
Filename: pool/main/a/apache2/apache2.2-common_2.2.11-2ubuntu2.3_amd64.deb
Size: 826734
MD5sum: 43e74c7cd838b664bdea97072f6b295f
SHA1: e184716ab5a8dd4875efdea841c46cffef355ee0
SHA256: 67fe404b496aaa4de6c0fbb0301cb3878d15025fa1dd495530e0b0217b004298
Description: Apache HTTP Server common files
 The Apache Software Foundation's goal is to build a secure, efficient and
 extensible HTTP server as standards-compliant open source software. The
 result has long been the number one web server on the Internet.
 .
 This package contains all the standard apache2 modules, including SSL support.
 However, it does *not* include the server itself; for this you need to
 install one of the apache2-mpm-* packages, such as worker or prefork.
Homepage: [http://httpd.apache.org/](http://httpd.apache.org/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: lamp-server, edubuntu-server, edubuntu-ship-addon

Package: apache2.2-common
Priority: optional
Section: web
Installed-Size: 3760
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: amd64
Source: apache2
Version: 2.2.11-2ubuntu2
Replaces: apache2-common
Depends: libapr1, libaprutil1, libc6 (>= 2.4), libssl0.9.8 (>= 0.9.8f-5), libuuid1 (>= 1.05), zlib1g (>= 1:1.1.4), apache2-utils, net-tools, libmagic1, mime-support, lsb-base, procps, perl
Recommends: ssl-cert
Suggests: www-browser, apache2-doc, apache2-suexec | apache2-suexec-custom, ufw
Conflicts: apache2-common, libapache2-mod-mime-xattr (<= 0.3-2), libapache2-mod-mono (<= 1.1.17-3), libapache2-mod-php4 (<= 4:4.4.4-2), libapache2-mod-php5 (<= 5.1.6-3), libapache2-mod-proxy-html (<= 2.4.3-2), libapache2-mod-scgi (<= 1.11-1), libapache2-mod-speedycgi (<= 2.22-3), libapache2-modxslt (<= 2005072700-1), libapache2-redirtoservername (<= 0.1-1), libapache2-webauth (<= 3.5.3-1), libapache2-webkdc (<= 3.5.3-1)
Filename: pool/main/a/apache2/apache2.2-common_2.2.11-2ubuntu2_amd64.deb
Size: 824236
MD5sum: 9e6b6a2bd0d114b9e0d9a730d30f685a
SHA1: 153cbb56107fc85b370d1cae84b5a2fec9a5477b
SHA256: 2d0321307d9a2739cca16b9d02d42457d0268a437137d160f16d4823cc64cc76
Description: Apache HTTP Server common files
 The Apache Software Foundation's goal is to build a secure, efficient and
 extensible HTTP server as standards-compliant open source software. The
 result has long been the number one web server on the Internet.
 .
 This package contains all the standard apache2 modules, including SSL support.
 However, it does *not* include the server itself; for this you need to
 install one of the apache2-mpm-* packages, such as worker or prefork.
Homepage: [http://httpd.apache.org/](http://httpd.apache.org/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: **[COLOR="Red"]lamp-server[/COLOR]**, edubuntu-server, edubuntu-ship-addon 


As written above: Prior to responding to your posting I had no knowledge of this. Just proves that the information about anything on Linux is easy to find and anyone can find the explanation about any command if you just care to look into the manuals ;)

---

### Post by scorp123 on 2009-11-13
> **Mornedhel said:**
> Explanation required? Explanation follows. Oh LOL ... I missed page #7 and this posting.

Sorry for my redundant posting above then.

---

### Post by Mornedhel on 2009-11-13
> **scorp123 said:**
> No idea. Until 5 minutes ago when I simply tried out what would happen :D

[SNIP]

Oh LOL ... I missed page #7 and this posting.

Sorry for my redundant posting above then. 

Nice try about the regular expressions, but ^ in a regular expression actually means "anchor to the beginning of the line/string", as the manual says, so the regexp "foo" matches any name containing the string foo anywhere, while "^foo" matches any name beginning with foo.

"Note that matching is done by substring so ´lo.*´ matches ´how-lo´ and ´lowest´. If this is undesired, anchor the regular expression with a ´^´ or ´$´ character"

^ has no meaning when it is not at the beginning of the regular expression (*), so putting ^ at the end makes sense (sort of) as a special case to mean something entirely different. I'll agree with anyone who says that this is just weird and not well documented, though.

(*) I'm trying to simplify regular expressions so that anyone can understand what I'm talking about here, but I have a feeling I'm very bad at it. Anyway, regular expressions are not a topic a newcomer would come across unless {s,}he had very specific needs.

---

### Post by scorp123 on 2009-11-13
> **Mornedhel said:**
> Nice try about the regular expressions, but ^ in a regular expression actually means "anchor to the beginning of the line/string" True.

This also confused me. I am no RegExp guru but I definitely know as much. So that's why I got curious and took a look if the string "lamp-server" is contained somewhere in any of those packages ... and it is, in the "Tasks:" section.

The other explanation given about "tasksel" in one of the previous postings of course makes a lot more sense than my theory ...

But hey ... as I said: I had no knowledge of this before I tried. So with RTFM and "apt-cache show" I still got pretty close I dare say :D

---

### Post by Aviendha09 on 2009-11-13
Funny I should come accross this rant.

The other day I posted this [_thread_]("http://ubuntuforums.org/showthread.php?t=1312744")

I got stuck *because* I couldn't understand the instructions.

I got a little bit of feedback that helped me over the bump. Then I came back, with this:
> **Aviendha09 said:**
> Ok I followed the instructions and they worked! Phew! Learned something the hard way today!! Thx for the help....
eh...can someone break down the meaning of the first command to execute...  the one with the cat? It has all kinds of weird magic words I don't get (i.e.: 2>, ||, etc...) ?? 

I am really glad someone took the time to break it down for me. Spoonfed ? Babies grow, you know.

---

### Post by markbuntu on 2009-11-13
I do not like to use terminal and avoid it unless absolutely necesary. I was using terminals when they were actual terminals attached to mainframes, a big leap from the cardpunch machines but that was decades ago...

I operate on the premise that these people are coming from windows and the terminal is a very strange and dangerous place for them to go and they know it. You can often deduce what level of help people can actually grok by the nature of their question and the way the thread develops.

I usually only tell people to use a terminal if there is no other way and try to explain what each command does when I can. Sticking to guis also helps noobs to find there way around the desktop and its menu structure and find  many useful gui applications that lots of people put a lot of time and effort into. It also gets them more comfortable navigating in a strange new place.

apt-get may be faster and easier for you but telling someone to use Synaptic opens the entire repo to their curiosity and gives them a better idea of how the packaging system works and they learn how to find and get stuff. Send them to the log file viewer and they know where to look when trouble pops up.

It is not just the poster that learns but also all the lurkers, many of them are shy and will never post but read the forums in desparate searches for explanation. One well explained post can teach a lot of people far more than the contents would appear to.

---

### Post by lykwydchykyn on 2009-11-13
I guarantee that if someone **asks** for an explanation of a terminal command they'll get it.  Is it such a terrible thing to expect people to ask for information when they want it?  

Honestly, threads like this do more to discourage me from responding to help requests than they do to encourage me to craft better responses.  I imagine others feel the same.

---

### Post by scorp123 on 2009-11-14
> **lykwydchykyn said:**
>  Honestly, threads like this do more to discourage me from responding to help requests than they do to encourage me to craft better responses.  I imagine others feel the same. Bingo. You're 100% right with this.

---

### Post by CharlesA on 2009-11-14
> **Mornedhel said:**
> ...regular expressions...

Like this?

[IMG]http://imgs.xkcd.com/comics/regular_expressions.png[/IMG]

On topic... I guess I must not be a "normal" user, since if I hit a stumbling block and google isn't helping, I post here, but I'll still trying to figure out how to get whatever I am trying to do working. :p

---

### Post by vagrantrooper on 2009-11-14
An Ubuntu spokesperson was on the BBC website not long ago saying that users should never have to use the shell and type in code. and in the last 5 years this has become apparent.

Long gone are the days when using Linux meant being an command line geek.

---

### Post by as2000 on 2009-11-14
Linux only can be advanced if those that help also teach. If this scares most people that troll the boards and offer cli quick fixes without explanation, then you do no service to the community as a whole. I personally will not offer any help that I cannot explain since I am still learning myself. Linux is rapidly becoming my primary os and most of what I do, I admit, is through gui including seeking my way to do things. This is just a carryover from *windoze* and the newer Ubuntu releases make it more user friendly that way. Man pages are fine, but sometimes read like stereo instructions...:roll:

---

### Post by scorp123 on 2009-11-14
> **vagrantrooper said:**
>  Long gone are the days when using Linux meant being an command line geek. You don't have to be a command line geek to _[COLOR="Red"]**use**[/COLOR]_ Linux.

But **_[COLOR="Red"]fixing[/COLOR]_** it is a different thing. I fail to see what's wrong with the command line in ***that*** case. You don't have to know those commands. You can let the geeks figure it out for you. All you as a normal user need to do is to copy & paste the few lines of code the geeks give you .... So what's wrong with that? It's easy, it works, and it's more likely to save everyone's time so you the normal average Joe User can get your problem fixed and move on to actually use the system.

I'm a Linux user since 1996 ... those of you who claim that Linux is using the command line "too much" have no clue what they are talking about. Back in the mid-90's there was no automagical configuration of the GUI ... You had to write your own config files from scratch for everything. Want to browse the Internet? Fine. Find the sources of the "mosaic" browser and compile it yourself. Oh ... we didn't have package managers back then. They were not invented yet. So it meant the user himself had to figure out all the dependencies and what not. 

Those user complaining about the current state of Linux deserve to be sent back to those days ... I bet they would come back screaming. BTW, back then we had Windows 2 and Windows 3.x .... So Linux, which was from bottom to top a real 32-bit OS, was so insanely more powerful than this 16-bit Windows GUI Microsoft put on top of a 8-bit OS (= MS-DOS). That's why it was worth to spend time on Linux, even if it meant having to do a lot of stuff from scratch and by hand.

With the exception of a few distros such as "Linux from Scratch", Gentoo and Slackware I haven't seen any modern Linux distribution that would indeed force the user to use a command line for everday usage.

---

### Post by confused_user on 2009-11-14
most of us learned how to use linux before it was a viable desktop operating system.  You see, Linux has been around for a long time, long before Ubuntu.

I was forced to learn linux since my company used Solaris and SLES database servers and storage hosts.  THere was no decent desktop environment at the time so we all used the command line.  The comand line interface is present amongst many of the top used and best operating system around - Unix, Linux, BSD etc... not to mention Cisco OS and every other switch and router OS.  Fibre channel switches as so on and so on.

DEsktop GUI's are and have always been a secondary concern in IT and Networking.  

The people that you ask for help on here have learned how to get things done using commands line interfaces.  YOu ask for help, they tell you how to do something.

The beautiful thing about LInux is that if you dont like it, you can change it.  In fact UBuntu is one of the most useful operating systems for modifying and simplifying everyday tasks.

Get used to the fact that CLI's are the way these things work, GUI's are secondary.  If you cant accept that and learn it then go back to windows, i believe they cater for people that refuse to learn new things.

Once you get used to CLI then you'll find, as have countless others, that it is a more efficient and easier way of telling you computer what you want it to do.

To have an OS where i can use both CLI and GUI is perfect for me, i love it.

Stop whining and blaming everyone else and either help to change it or go and find a more suitable operating system for your needs.  nobody is forcing you to use linux.

THis is the last time i am ever going to read a "it's wrong to have to use a cli" thread

---

### Post by NoaHall on 2009-11-14
> **confused_user said:**
> words and so on

Solaris isn't linux-based.

---

### Post by confused_user on 2009-11-14
> **NoaHall said:**
> Solaris isn't linux-based.

indeed it is not.

are you just posting blatantly obvious facts at random or did you have something to say?

---

### Post by scorp123 on 2009-11-14
> **NoaHall said:**
> Solaris isn't linux-based. Can you please show me the portion where he claimed that??

Or maybe you're just a troll?

---

### Post by NoaHall on 2009-11-14
> I was forced to learn linux since my company used Solaris

Speaks for itself, don't you think.

---

### Post by confused_user on 2009-11-14
> **NoaHall said:**
> Speaks for itself, don't you think.

how about you include the next two words in that quote - then it can be taken into context and it makes sense.

In fact, why dont you just go away if you have nothing of value to add.

---

### Post by NoaHall on 2009-11-14
> **confused_user said:**
> how about you include the next two words in that quote - then it can be taken into context and it makes sense.

In fact, why dont you just go away if you have nothing of value to add.

That's no way to talk to someone. I was merely clearing it up for newbies who hadn't heard of Solaris.

---

### Post by confused_user on 2009-11-14
> **NoaHall said:**
> That's no way to talk to someone. I was merely clearing it up for newbies who hadn't heard of Solaris.

you misunderstood what was written, nobody said Solaris was linux.

---

### Post by NoaHall on 2009-11-14
> **confused_user said:**
> you misunderstood what was written, nobody said Solaris was linux.

No, you don't understand. You said it such a way that a newbie, who has not heard of Solaris, might think it is Linux-based. I was making sure that there were no misinformed newbies.

---

### Post by confused_user on 2009-11-14
ok NoaHall lets just agree to disagree.

back to the thread

i think people who are scared to use the terminal because they dont understand the commands they are inputing are quite right to be scared.  it shows intelligence.  however, each command can be looked up using another command - man

if your not sure what rm -rf will do then you type man rm and read.

I read a comment by another user that said "if you cant read simple documentation then you should not be using linux"

google is pretty good too.

only by learning about things that we do not understand will we begin to understand them.

---

### Post by hoppipolla on 2009-11-14
> **confused_user said:**
> you misunderstood what was written, nobody said Solaris was linux.

apart from you... lol

But yeah it was just a misunderstanding and I know that's not what you meant :) We should definitely get back on topic o.O


EDIT -- Actually wait no he didn't I just worked out SLES stands for SUSE Linux Enterprise Server... so whatchu talkin' bout Noah? xD

---

### Post by NoaHall on 2009-11-14
I know SLES is Linux based, but Solaris is NOT. That's what I'm talking about.

---

### Post by seeker5528 on 2009-11-14
> **vagrantrooper said:**
> An Ubuntu spokesperson was on the BBC website not long ago saying that users should never have to use the shell and type in code. and in the last 5 years this has become apparent.

They try to get you to believe that about Windows too, but that assumes everything works out of the box and you never have to troubleshoot.

And even on Windows there are plenty of instructions that have you type stuff in either because it is easier, faster, or the only way....

A couple of examples you might be asked to type in the run box.

%windir%/system32

services.msc

appwiz.cpl

A couple examples of command line things:

netsh int ip reset c:\reset.log
netsh firewall reset
netsh winsock reset

regsvr32 *some_file*
regsvr32 *Some_other_file*
regsvr32 *Yet_another_file*

From the Windows installation disk in the recovery console.

chkdsk /p

listsvc
disable *some_service*

cd ie7\spuninst
batch spuninst.txt

Definitely you see it more with Linux, but nobody is immune.:P

I never saw anything in the OP about the commands being undocumented, just the desire that when help is given a little more explanation be provided.

Of course you always have to ask yourself... To what extent is more information desirable and when does it just confuse the task at hand? 

If people refuse to use the command line no matter how simple the task, sometimes that is just tying both hands and one leg behind your back, when you try to help.

Later, Seeker

---

### Post by Jose Catre-Vandis on 2009-11-15
What is worse is when a noob poster replies to their own post with:
"Don't worry, I fixed it now" often accompanied with a "found the answer on another site/thread", with no indication of the resolution or any links, nor do they mark the thread solved.

The CLI answer is the best way to cover all variants. E.G. I do not use Gnome, so I don't have a clue "what to click and where". But I can offer CLI answers.

Personally, If I get a CLI answer to one of my problems, I will go and look it up, either before running it or after it has worked so that I understand, or I will ask the helpful poster how it works.

Linux is not Windows (how many times have we heard that!) and sometimes it is so much quicker and easier, and makes more sense to do things at the CLI.

---

### Post by cardinals_fan on 2009-11-15
I haven't been on this forum for a while.  There are just too many other things to do with my life to worry overly much about my computer, much less anyone else's.  But I think this actually gives me a better perspective for the so-called "average user", because I do view the computer as more of a means to an end than before.  I still read K.Mandla's excellent blog, which is how I ended up here.

I won't get into the ways in which CLI instructions can be superior - this issue has been covered over and over and over again.  Suffice it to say that there are concrete advantages.

The idea of explaining CLI solutions is nice on paper, but that is ultimately not the point of a forum.  The duplication of effort would be obscene, since many different questions are answerable with similar commands and explaining them all each time would be ridiculous.  This is why we have wikis and man pages.

I resent the idea that Googling for a solution is some sort of arcane art or unbearable punishment.  Like I said, I am no longer preoccupied with learning about my system - there are too many other things to do.  But instead of sitting around a forum for 15 minutes waiting for a solution that you will then whine about not understanding, try a very simple search.  The results might surprise you.  This is why I consider Let Me Google That For You a valuable support resource; it solves a problem while showing how it could have been solved with a search.

More importantly, learning to search through available information is a useful skill in almost any pursuit.

---

### Post by scorp123 on 2009-11-15
> **NoaHall said:**
> Speaks for itself, don't you think. You just misunderstood him, that's all. I too had to learn Linux because my employer used Solaris. That's no contradiction. Solaris --at least back then-- was running on super-expensive SPARC workstations. For a newb like me it was impossible to get one just to "play around". But we had PC's. They were cheap. And there was Linux. Free and gratis. So I was told to "play around" on those PC's with Linux. If I'd master that, they'd let me "play" with those expensive Solaris workstations. Yes, Solaris isn't based on Linux. But still ... once you know one UNIX-like OS --such as Linux-- finding your way around another UNIX-like OS --such as SUN's Solaris or HP's HP-UX-- isn't hard at all.

That's what he meant. Been there, done that myself too.

I still train my apprentices that way. First thing they learn to do on their very first day is to remove that OS abomination made in Redmond from the laptops we give them. You can't teach or learn real IT with Windoze. Seriously. You can't.

It doesn't take very long and we catch our apprentices distro-hopping. Ubuntu today, tomorrow OpenSUSE; Arch Linux and Debian after that, next week maybe even some *BSD. When that happens it's time to hand them some nice server and the Solaris 10 installer DVD ... 

Our current apprentice is now trying out "Linux from Scratch" and is in charge of our Solaris 10 "JumpStart" environment.

So the method works. Teach someone Linux and you'll maybe have a Solaris guru tomorrow.


> **NoaHall said:**
> I was making sure that there were no misinformed newbies. You could have included a quote or something ... Just a suggestion.

---

### Post by vocifer on 2009-11-25
> **vagrantrooper said:**
> An Ubuntu spokesperson was on the BBC website not long ago saying that users should never have to use the shell and type in code. and in the last 5 years this has become apparent.

Long gone are the days when using Linux meant being an command line geek.

Weird, the terminal is one of the things that made me stick with linux. I'd hate to see it drowned to the background.


first os I installed on my pc besides windows was ubuntu (7.04). at first ubuntu (gnome) was all awkward and unfamiliar.

(By the way I liked gnome BECAUSE it was nothing like windows, unlike KDE. Just saying, I read so many articles, posts, tutorials, ... where they explain how the lure windows users by making linux look like windows, and how they would not know the difference. I really don't get that, the difference is exactly what makes linux so appealing. It is what made me to give it a try.
Oh and I never dual booted, I don't get why people recommend that if you try to make the switch from windows to linux. You'll always go back to what's familiar ...)

Anyway, in all this time I have only posted one or two topics where I asked for help. On all other occasions I found solutions using google. It's remarkable how much you can find by explicitly typing the error message you get in google. Of course that does not work all the time. My point is, if you try a bit there is nearly always enough info on the web to solve your problem.

If you don't like typing in commands that you don't know (witch you should never do) it is often easy enough to get information on commands. just try --help and man every now and then. that's what I do when I don't have a clue what a command does (basically every time I see a new command, and often even with commands I know. for instance the tar -xfterdgkdoej thingy, though man page explains it clear enough :d).

I'm no where near as familiar with the command line as a lot of people around. Though nowadays I sometimes even find myself browsing documents with the terminal ... (I could think so many, more useful ways to use the terminal though :d) (btw this mostly happens when I'm trying to do something else on the command line)

actually to top this all of, when I see some tutorial, or help page, or anything that contains screen shots or mentions something like "click here and go to there fill in <something> in that field and click forward" I wont even give it a try. 
And I'm just using ubuntu as a means to an end. I mean I just need an operating system so I can work with my pc, and quite frankly that's all I'm interested in. All other benefits of using linux are added bonuses. (actually I have never felt the need to turn to any other os after the first few months of using ubuntu). If someone would come to be for help on ubuntu they better have backups made (just saying I don't know enough to actually help others out).


I think the reason I post this is because I often read or hear about users that are not keen on using the terminal. Users that look upon it as a demonic contraption that should be purged form ANY software (or agree with it at least on some level). Though I never came across any post of a simple user that has absolutely no problem with the command line. This sometimes surprises me. (of course it could be that I never read enough to actually come across such users)

---

### Post by vocifer on 2009-11-25
i

---

