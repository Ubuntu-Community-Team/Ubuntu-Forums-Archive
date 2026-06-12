---
title: "GUI vs. CLI"
date: 2005-06-23
forum: Recurring Discussions
---

### Post by poofyhairguy on 2005-06-23
I'm just going to straight up ask the community on this one. Please beat me up and tear my logic apart- I'm posting this for that reason.

As many know I try my best to help out new Ubuntu users. Many of us do, and its a great thing. Often on this forum I will tell people commands to put in the command line to fix their problems. Recently I was told that this is not the best thing, as it scares away new ex-Window's users who associate "command line" with "Dos" (this ignores that fact that a big "feature" of longhorn will be a functional CLI). Azz, another moderator here is big on giving answers that fix problems through a graphical method if possible. Supposedly the Ubuntu developers themselves have set out a goal that "an Ubuntu user shouldn't need to touch the command line," but until they make a GUI tool for ndiswrapper (aka the hardest thing for a new user to do) I don't put much weight into their opinions on the matter.

 I personally tell greens commands because :

A. Instructions using a GUI require pages of screenshots with areas circled in gimp or whatever. Its harder to write a good way to work through the GUI...they are very intuitive to me so I leave out steps that my brain assumes. Anyone that has done tech support on Windows can tell you the problems here.

B. No one can mess up copy and pasting a command. You CAN mess up entering info in many dialog boxes in a GUI.

C. I kinda have this idea that greens need to get used to the way Linux does things. Many of the howtos on this forum require some work on the command line. It seems like unless someone set up the computer for you and all you do it make office docs and surf the internet you will one day have to face the command line (if only to run the program you just downloading in synaptic but a menu option wasn't added for it). Till now I've been of the opinion "they need to just get used to it early on.....its not like we have a YAST or something like that so command line work is inevitable." I mean....look at your grub menu....."safe mode" in Ubuntu is the command line.

D. When I first started with Linux I was afraid of the command line too...but now I think is is very powerful and I would hate to go without it. It doesn't have the negative connotation with me as it does with some people. If the betters I got my early advise from didn't force me to use the command line (by only helping me that way) I wouldn't be half the *NIX admin I am today. Now (after using Linux for less that a year) I can fix a Ubuntu computer from the command line.

E. The guide uses the command line so I want to be consistent.

F. There is no F

So...what do you guys think? Is pointing newbies to the command line a bad thing? If they are afraid of it should I be honest and tell them "the only Linux I know of that liberates itself from the command line is SUSE?" Should we make more guides to do things in a graphical way?  Will Ubuntu ever reach the lofty goal of "never needing the command line?"

---

### Post by sapo on 2005-06-23
I think you are working too much.. may i invite you to drink some beer and look at some women?

The command line scares new users.. but who the hell is going to teach them step by step how to click in endless buttons? not me...

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=sapo]I think you are working too much.. may i invite you to drink some beer and look at some women?[/QUOTE]

Thanks but I already have my favorite beer in the fridge and my girlfriend wouldn't like me oogling other women. 

> 
The command line scares new users.. but who the hell is going to teach them step by step how to click in endless buttons? not me...

Glad you can see me side of the story....I want to hear the other side though.

---

### Post by WildTangent on 2005-06-23
like you, i prefer the command line, because thats what i got used to. Ubuntu was my first distro, and when i went looking for help for things, i found the unnofficial guide, which of course is all commands. i find commands easy to do, so i use it. i think all new users should use commands when theyre available, how hard is it to explain a new user how to type something into a box? now try and get them to do the same thing with a GUI, its much harder, but for some reason they feel more secure doing it. i really dont understand how someone could fear a command line, especially since a large portion of new linux users havent used anything older than windows 9x in the past

-Wild

---

### Post by N'Jal on 2005-06-23
Technically i am a noob, i really don't know half of the things that you guys do, hell i don't even know what this ndiswrapper is, however, like yourself's i think the command line is a fine tool, all major OS's that i have seen use one, Mac has one, even repairing XP desktops requires knowledge of DOS *shudders*. I say technically because i have been using Linux for almost a year and a half now. So i know some things, and as i think down this path what graphical tool is there for fsck?

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=WildTangent]like you, i prefer the command line, because thats what i got used to. Ubuntu was my first distro, and when i went looking for help for things, i found the unnofficial guide, which of course is all commands. i find commands easy to do, so i use it. i think all new users should use commands when theyre available, how hard is it to explain a new user how to type something into a box? now try and get them to do the same thing with a GUI, its much harder, but for some reason they feel more secure doing it. i really dont understand how someone could fear a command line, especially since a large portion of new linux users havent used anything older than windows 9x in the past

-Wild[/QUOTE]


STOP FREAKING AGREEING WITH ME!!!!!


Just joking.

---

### Post by jimcooncat on 2005-06-23
> I mean....look at your grub menu....."safe mode" in Ubuntu is the command line.

Ha, ha. It's not so "safe" on my computer, anyway!

Other than that, I quite agree. I think another consistency improvement would be to specify full paths and an editor when asking them to edit a file, and don't assume they know when to sudo. 

```
sudo gedit /etc/fetchmailrc
```

not "edit the fetchmailrc file to include ..."

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=jimcooncat]
Other than that, I quite agree. I think another consistency improvement would be to specify full paths and an editor when asking them to edit a file, and don't assume they know when to sudo. [/QUOTE]

I usually do. I try to be good about that. That is a good rule. never just say "you need to edit this file with sudo." I give the command in quotes.

> ```
sudo gedit /etc/fetchmailrc
```


For graphical apps its better to use gksudo:

gksudo gedit

---

### Post by Xian on 2005-06-23
[QUOTE=poofyhairguy]So...what do you guys think? 
1.Is pointing newbies to the command line a bad thing? 
2.If they are afraid of it should I be honest and tell them "the only Linux I know of that liberates itself from the command line is SUSE?" 
3.Should we make more guides to do things in a graphical way?  
4.Will Ubuntu ever reach the lofty goal of "never needing the command line?"[/QUOTE]
*[My numbering]*

1. No. Knowledge is good. But knowledge should not be confusing.
We should not instruct users in a way that alienates them.
Is it better than a graphical alternative? For a new user probably not.

2. SuSE/Novell sends out excellent documented official subscription e-mails that instruct users (both new and established) on the many ways that their SuSE system can be managed, tweaked, and secured. They sometimes mention a GUI method if available in YaST, but by and large the examples are from the command line. The SuSE/Novell support website is filled with command line instructions and tutorials. 

My point being that sending a new user over to SuSE will not keep them from being presented with the command line as a method of system maintenance. I would argue that we do the same here, only we rely more upon that method since we have less GUI tools available.

Now, if Ubuntu did in theory have an equivalent amount of GUI tools and someone posted a question in the new user section at our forum, only to be answered with a series of commands and scripts for something that a YaST-like module could easily handle, then I'd say we were being negligent to the needs of our members. But this day has not yet arrived. 

However, a user should feel comfortable with their system. If they need to run another Linux other than Ubuntu to achieve this, then I would have no problem advising them of this and helping them to find a better fit. I know of no goal of Ubuntu which states that it wants to be the only choice of every Linux user. 

3. Yes, but we are quite short on GUI's at present. 

4. Of course it can be done. How many Windows users still use command prompts?

---

### Post by Takis on 2005-06-23
I'd say Linux without a command-line is a long, long way off, so till that time new users need to be introduced to it. It's a very scary thing in most cases so the earlier they get used to at least doing a couple of things here and there, the better. It doesn't have to be a throw in the deep end, it can just be splashing your feet in the water, as long as you realise that in the end, it's just water (or a command line).

On a side note, I'm getting pretty annoyed at Windows' auto-complete (TAB) feature. I'll type 'cd Proga<TAB>' and change into the directory, and the VERY NEXT THING I'll type is 'ls'! Every time!

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Xian]
1. No. Knowledge is good. But knowledge should not be confusing.
We should not instruct users in a way that alienates them.
Is it better than a graphical alternative? For a new user probably not.[/QUOTE]

My opinion is that it is better because "they need to get used to the command line early on to survive in Linuxland." I think its better in the long run. But I posted this to see other opinions.

> 
2. SuSE/Novell sends out excellent documented official subscription e-mails that instruct users (both new and established) on the many ways that their SuSE system can be managed, tweaked, and secured. They sometimes mention a GUI method if available in YaST, but by and large the examples are from the command line. The SuSE/Novell support website is filled with command line instructions and tutorials. 

My point being that sending a new user over to SuSE will not keep them from being presented with the command line as a method of system maintenance. I would argue that we do the same here, only we rely more upon that method since we have less GUI tools available.

My point was that the closest I have seen to the Window's way of a GUI for everything is SUSE. But you are correct....even SUSE needs some command line love every now and then. Of course, that just supports my thesis that new users need to suck it up and hit the command line.

> 
3. Yes, but we are quite short on GUI's at present. 

Very true.

---

### Post by sapo on 2005-06-23
[QUOTE=poofyhairguy]STOP FREAKING AGREEING WITH ME!!!!!


Just joking.[/QUOTE]

I agree! they should stop agreeing with you  :roll:

---

### Post by desdinova on 2005-06-23
Preaching to the converted I know but...

I think its a bad idea to associate the command line with "dos" or "hard" - shell scripting is a seriously cool tool in looking after your linux box, and I defy anyone to find a way to find an easier graphical tool to do some jobs (such as "list all the files whose name starts with d and have "elete" somewhere in the name")

The bash shell and its ilk are one of our greatest strengths, and i think when people get more and more confident with Linux they'll realise it offers so much strength and is a useful tool in the kit that is Linux.

In fact, I know several people who, once they learned the power of the shell, remarked to me its a wonder why Windows doesnt have one of similar power.

And of course Longhorn (or its successor it seems ;-) will get one in the shape o MSH, or Monad Shell. So if MS thinks its a good enough idea to copy, then that speaks volumes on its power.

---

### Post by poofyhairguy on 2005-06-23
Here is the official Ubuntu page that relates to this:

[http://udu.wiki.ubuntu.com/GraphicalConfigTools?highlight=%28MediumPriority%29](http://udu.wiki.ubuntu.com/GraphicalConfigTools?highlight=%28MediumPriority%29)

Makes me mad an ndiswrapper tool isn't even considered.

If there is anyone out there who wants to help Ubuntu and can program in some python....this is the way to go.

---

### Post by desdinova on 2005-06-23
What I find odd from that page is they talk about "stealing" from SuSE - when it wouldn't be - YaST is gpl so I can't see why it can't be forked off...

---

### Post by N'Jal on 2005-06-23
As i said i think they need to be introduced but it also helps if it's some really nifty trick that looks cool. The very first command i learned was the one that changes the command prompt dispay for that terminal session, it was good since you could do all sorts of stupid things with it that made me laugh. If you show the little quirks it's easier to learn.

See i am a dummy, i know nothing and that's exactally where i learned lots of the linux commands from a linux for dummies book....

```
PS1='Hello \u, what can I do for you today?'
```
That's what made me realise that the command line was not so scary

---

### Post by WildTangent on 2005-06-23
[QUOTE=poofyhairguy]STOP FREAKING AGREEING WITH ME!!!!![/QUOTE]
im not trying to suck up to you if thats what you think, just happen to have the same opinion :)

-Wild

---

### Post by Xian on 2005-06-23
[QUOTE=desdinova]What I find odd from that page is they talk about "stealing" from SuSE - when it wouldn't be - YaST is gpl so I can't see why it can't be forked off...[/QUOTE]
Especially when there is this: [Yast4Debian](http://yast4debian.alioth.debian.org/)

---

### Post by N'Jal on 2005-06-23
I'm sorry but i aint got a clue how to go about getting yast4debian working as last i checked it was still unstable

---

### Post by desdinova on 2005-06-23
[http://=http//yast4debian.alioth.debian.org/%7DYast4Debian](http://=http//yast4debian.alioth.debian.org/%7DYast4Debian)

Am I missing the joke here? Why redirect me to MS?

---

### Post by AgenT on 2005-06-23
[QUOTE=Xian]*[My numbering]*4. Of course it can be done. How many Windows users still use command prompts?[/QUOTE]

That's because Windows does not have a proper terminal. Window's "command prompt" is, at best, garbage. There is a reason why, what almost sounds like a joke, they are going to *try* and implement a more Linux-like terminal in the next version of Windows.

Right now, Windows may have a command prompt, but not a real terminal in any sense that other OS's have.

But there is a large number of people who would not dare touch the terminal because that is too difficult for them. This is true. But these same people would not touch any GUI tool either. Windows or Linux.

---

### Post by N'Jal on 2005-06-23
The origanal link works yet your points to MS that's not right...

---

### Post by desdinova on 2005-06-23
I think someone did a quick edit as the new link they've put in works.... ;-)

---

### Post by Xian on 2005-06-23
[QUOTE=N'Jal]I'm sorry but i aint got a clue how to go about getting yast4debian working as last i checked it was still unstable[/QUOTE]
Basically, it doesn't "work". The topic at hand was the GPL status of YaST and how it is being implemented by some devs at Debian. The individual modules which are applicable (including package management) are in the process of being ported. But it is not meant to be used on a desktop at this time.

---

### Post by Xian on 2005-06-23
[QUOTE=desdinova]I think someone did a quick edit as the new link they've put in works.... ;-)[/QUOTE]
The URL syntax was initially incorrect. Fixed.

---

### Post by carlc on 2005-06-23
[QUOTE=poofyhairguy]I'm just going to straight up ask the community on this one. Please beat me up and tear my logic apart- I'm posting this for that reason.

So...what do you guys think? Is pointing newbies to the command line a bad thing? If they are afraid of it should I be honest and tell them "the only Linux I know of that liberates itself from the command line is SUSE?" Should we make more guides to do things in a graphical way?  Will Ubuntu ever reach the lofty goal of "never needing the command line?"[/QUOTE]


I think pointing to the command line is a good thing. It does catch some off gaurd but I believe that is part of what seperates windows and linux users. However, people who give it a shot realize the value and learn something in the process.

It seems to be a common assumption that the linux community needs more windows users to switch over. I don't agree with this 100% but I do think this will happen little by little as the next generations because more tech savvy. I think the only thing lacking for linux is gaming. As the linux community grows, hopefully more games will be developed for both linux and windows.

---

### Post by Xian on 2005-06-23
You don't even need some widebody application like YaST to make the entry level more acceptable for users. Just look at how many members have found a great tool in bored2k's grubconf program. I point to it often when the question of reconfiguring grub arises. People genuinely find this to be an incredible asset.

---

### Post by az on 2005-06-23
Actually, it would be great if we gave out advice in both formats:  "Click on this and set that, or open a terminal and run this...."

Did you check to see if Breezy's network tool has a graphical interface for ndiswrapper?

I do not think that is going to be a big hurdle, since it can be fixed in the gnome network toool, it can be a wireless configuration applet, it could be a nautilus script....  It is easy for me to say, since I do not make my living writing code, but it is an easy thing to do.  

As for the command line, it is great that it is there, but at some point, there has to be a certain level of useability.  If we do not show how useable the system is, many people will shy away.  You have to aim for the lowest common denominator.

That being said, I hardly ever use anything other than mc (midnight commander) to poke around my filesystem. And there are about a dozen things I do on a daily basis that are command-line that have wonderful GUI alternatives.  It just is a choice.

Most other people, I think, would not chose to use them.  Maybe in a year or two, when I get a faster computer, I will avoid the command line too....

---

### Post by Leif on 2005-06-23
I think that for things where a GUI alternative is logical, this should be implemented. I love the CLI for what it's good at, but the alternative should exist for common tasks. Then again, since being able to accomplish all setup related stuff without ever touching the CLI is quite a bit into the future, it's a moot point. 

Since people have to use the CLI at some point or the other, might as well get used to it, and not pretend to have a useability level that isn't there.

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Leif]
Since people have to use the CLI at some point or the other, might as well get used to it, and not pretend to have a useability level that isn't there.[/QUOTE]

Ok. Thats like the base concept for me. I kinda feel bad about it, but if someone wants to install and use Ubuntu as a primary OS they have to know what "change your bios to boot from a cd" is and how to "open the terminal and copy and paste this command in there."

But I also care about image. A suggestion was floated to me to give two ways of doings things. I will happily tell people of synaptic and try to be a little more GUI friendly.

---

### Post by TravisNewman on 2005-06-23
I prefer telling users the command line because it gives them a greater understanding of the underlying system, and it's actually EASIER if you're paying attention. I've used many GUI apps in linux that don't work as well as their CLI counterparts (qtparted and gparted come to mind). The GUI essentially gets in the way of things.

Another reason that Windows users don't need to use the command line-- Windows is nowhere near as customizable. If you want to change your shell (somewhat equivalent to changing your DE in Linux) you have to do manual editing. If you want to change your icons (and I mean ALL icons) and you don't have a program that does it for you, you have to edit dll files. 

Essentially what I'm saying is that CLI will give new users better understanding of the system, and let them do things more efficiently in the long run

---

### Post by aragorn2909 on 2005-06-24
[QUOTE=panickedthumb]I prefer telling users the command line because it gives them a greater understanding of the underlying system, and it's actually EASIER if you're paying attention.... Essentially what I'm saying is that CLI will give new users better understanding of the system, and let them do things more efficiently in the long run[/QUOTE]

I grew up on Dos.  Command line does not frighten me, and I dont think it frightens alot of new users.  What does frighten them/us, is being handed a command like this (which I just pulled from the unofficial ubuntu guide at random):

sudo chown -R root:root /opt/rp-pppoe-3.5/

and offering NO explanation as to what that means.  Sure, I can follow directions, copy and paste, move on to the next command, but do I gain any more insight into my system because of it?  Have I learned Linux?  Sorry, but no.   Personally, I enjoy endless reading and googling to better understand my Linux box, but not everybody feels the same way.  CLI is an excellent tool (cannot be overstated), but absolutely needs to be accompanied with explanation.
My 2 cents.

---

### Post by Xian on 2005-06-24
It's like anything else: a good idea trumps all contenders. Take the threads we have regarding partition space issues. People boot to suddenly find that their 12GB root partition is almost completely full and they need help finding out where to look for the culprit.

Now, I've posted in some of these threads on how to use the various 'du' commands to uncover the problem and sooner or later it all gets worked out. In still other threads I've told the member to install the GUI tool Filelight, and use it to present a graphical space allocation model of their applicable partition or directory. 

I can easily say that the GUI tool wins this usefulness comparison. People just seem to have a much easier and rewarding time using the graphical model over command outputs. But I can also say that I've seen some other applications that tried to perform a similar function, and failed miserably because of a poorly designed interface.

So I'm just pointing out that not all GUI's are equally created, and that to just lump them all into a illustration with command sessions is not really getting at what the user experience might be like.

---

### Post by TravisNewman on 2005-06-24
I totally agree Xian-- with some things, GUI wins hands down. partition viewing, as you said, is much easier to understand with something like filelight.

If all gui's were bad, we'd still be using JUST the CLI with no X or Gnome or any of that. 

I always try to weigh the pros and cons with everything when giving users advice. It just usually leads to CLI

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=Xian]. In still other threads I've told the member to install the GUI tool Filelight, and use it to present a graphical space allocation model of their applicable partition or directory. [/QUOTE]


I was just wondering how to do that a few minutes ago....

thanks

---

### Post by Leif on 2005-06-24
[QUOTE=panickedthumb]I prefer telling users the command line because it gives them a greater understanding of the underlying system, and it's actually EASIER if you're paying attention. I've used many GUI apps in linux that don't work as well as their CLI counterparts (qtparted and gparted come to mind). The GUI essentially gets in the way of things.[/QUOTE]

It's easier to you, and to me too in most cases, true. But if you consider that for some people firing up a terminal may in itself present a huge difficulty, then GUI wins after all. I guess it's about trying to see it from their point of view. 

But are a couple of posts enough to make a generalization about what people want and start going through laborious "now click here... and here... and here..." explanations ?

---

### Post by eskaypey on 2005-06-24
It doesnt matter how you help people. For one problem there could be a number of  solutions. Its all depends on the person who trying to solve this problem. The one who really wants to get it working and understand it, will learn the command/gui steps and see what else he/she can use it for. 
Imagine you stand in the middle of the desert and you dont care who'll give you a lift, the person on the motorbike, the person on helicopter or car. You'll take the first choice offered.

---

### Post by TravisNewman on 2005-06-24
[QUOTE=Leif]It's easier to you, and to me too in most cases, true. But if you consider that for some people firing up a terminal may in itself present a huge difficulty, then GUI wins after all. I guess it's about trying to see it from their point of view. 

But are a couple of posts enough to make a generalization about what people want and start going through laborious "now click here... and here... and here..." explanations ?[/QUOTE]
 I'm saying that regardless of comfort level, copying and pasting a command and hitting enter is easier than cick here, click here, etc. Whether it's more understandable is up to the person explaining it.

---

### Post by UbuWu on 2005-06-24
For the moment I think it is fine to tell people to do things with the command line. But I hope in one of the next releases, you will NEVER have to use the command line to do anything a normal computer user would like to do. I can't remember the last time I used the command line in Windows... (only in dosbox  :razz:  )

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=UbuWu]But I hope in one of the next releases, you will NEVER have to use the command line to do anything a normal computer user would like to do. 
[/QUOTE]

Yeah...maybe in a few years the CLI will just be an option, not a necessaty.

---

### Post by eskaypey on 2005-06-24
>  [QUOTE]But I hope in one of the next releases, you will NEVER have to use the command line to do anything a normal computer user would like to do.Yeah...maybe in a few years the CLI will just be an option, not a necessaty.[/QUOTE]

Boo you! Maybe we'll just lock it up and make it Winduntu? hey?

 [-X

---

### Post by Leif on 2005-06-24
[QUOTE=eskaypey]Boo you! Maybe we'll just lock it up and make it Winduntu? hey?
[/QUOTE]

What does this have to do with Windows ? About locking up ? This is about ease of use, and if properly done, for a good number of people, GUIs are more useable than CLI. 

And whatever happened to Linux being about choice ? Nobody said we take out the CLI, but we create another option, the GUI. But no, Windows has it, so it *must* be evil !

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=eskaypey]Boo you! Maybe we'll just lock it up and make it Winduntu? hey?

 [-X[/QUOTE]


Boo me? I likem me synaptic....

---

### Post by az on 2005-06-24
"Yeah...maybe in a few years the CLI will just be an option, not a necessaty."

That's the way it was for some people with Warty, alot more in Hoary and hopefully most people in Breezy...

The point of useability not being there is valid - to a point.  There is much more useability than we talk about, and if you do not demand useability, you will never get it.

Again today, I picked up a computer trade paper and I found two instances of linux being mentioned.  Both times it was compared to mac and was seen as being aimed at a more technical user.  There is no reason for linux to be so elitist.

The more technical users have only a lot to gain by useability getting more and more evolved.  

No one is going to take away the command line.  For pete's sake!  That is how Unix works!

---

### Post by jimcooncat on 2005-06-24
Maybe I'm not looking hard enough, but it seems most "File Open" dialogs don't have a place where I can paste the full path of the file I want to open. This "only point and click" design slows me down to a crawl, as well as not having obvious, consistent keyboard shortcuts. 

Geesh, even Windows Common Dialogs have a text box to paste into, and you used to be able to navigate quite well with just the keyboard (well, back in the Windows 3.11 days).

Am I getting off-topic?

---

### Post by TravisNewman on 2005-06-24
yeah that's a little off topic, but I agree, gnome's file dialogs seem to be going backwards.

---

### Post by desdinova on 2005-06-24
[QUOTE=poofyhairguy]Yeah...maybe in a few years the CLI will just be an option, not a necessaty.[/QUOTE]

But the CLI has one obvious advantage

Example

I want the user to tell me how much discspace they have left.

GUI Way - Filelight

Console way - df -h

Which way is easiest to copy and paste in a reply?

---

### Post by timczer on 2005-06-24
I guess as I read these posts, it keeps coming back to an argument that shows up on a regular basis.  "Should LInux be easier for Windows users to migrate too?"  A graphical way of doing things is clearly what those users are used to.  Many, if not most computer users just want the thing to work.  When I used windows I wanted to open up my computer, load a few programs and get my work done and browse the web.  I think most people asking for help want to get to the fix as fast as possible, they probably don't care how it works (I just want to put gas in my car and go, I don't care what goes on in the engine to get there). 
That being said, I personally do enjoy learning things about computers, and finding new and better ways of doing things.  Copying and pasting command line instructions over time has given me knowledge about how things work and I am far more able now to tweak my system than I was when I first started.  On this I agree with aragorn2909, in that sometimes a little more explanation on what the commands are doing would be helpful.  I know I could google the command, or search it in the forums, or look for a man page, but if I am already following your post for instructions to do something, I am not likely to want to leave it to look for something else.  A few nuggets of what some commands do within the post would be helpful to all. (the chmod example is perfect as I see it often but am still not sure exactly what this is doing).

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=azz]
Again today, I picked up a computer trade paper and I found two instances of linux being mentioned.  Both times it was compared to mac and was seen as being aimed at a more technical user.  There is no reason for linux to be so elitist.
[/QUOTE]


Thats just the mainstream media's opinion. Linux will be elitist until it ships on a major PC maker's box (which is never if MS has its way).

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=desdinova]But the CLI has one obvious advantage

Example

I want the user to tell me how much discspace they have left.

GUI Way - Filelight

Console way - df -h

Which way is easiest to copy and paste in a reply?[/QUOTE]


Yeah....there are some advantages to the command line. Plus...the point of a more GUI future is kinda moot- I don't think Breezy is adding much in the way of GUI config tools.

---

### Post by az on 2005-06-24
[QUOTE=poofyhairguy]Thats just the mainstream media's opinion. Linux will be elitist until it ships on a major PC maker's box (which is never if MS has its way).[/QUOTE]


No, linux will be elitist until it stops being elitist.

Saying that tools to help you avoid the command line are making it into windows are wrong.  It is elitist in imposing a certain way of doing things on people that may not be what they want.  

Making the software _proprietary_ is turning it into windows,  And that has nothing to do with useability.

---

### Post by skoal on 2005-06-24
The CLI is for those of us who have very little time to do anything, yet enjoy spending more time than is necessary on such mundane tasks - all in the *hope* that "what we should be doing" will simply *faaaade* away...

\\//_

---

### Post by Leif on 2005-06-24
[QUOTE=skoal]The CLI is for those of us who have very little time to do anything, yet enjoy spending more time than is necessary on such mundane tasks - all in the *hope* that "what we should be doing" will simply *faaaade* away...
\\//_[/QUOTE]

s/Linux/The CLI  :razz:

---

### Post by desdinova on 2005-06-24
Wow, instant generalisation ;-)

Some of us are actually comfortable and reasonably proficient at the cli you know... I just don't see what the fuss is about, there's some sort of misconception around that graphical instantly equals better, when sometimes its a lot easier to do a find/grep/sed/awk type command line.

---

### Post by Leif on 2005-06-24
[QUOTE=desdinova]Wow, instant generalisation ;-)

Some of us are actually comfortable and reasonably proficient at the cli you know... I just don't see what the fuss is about, there's some sort of misconception around that graphical instantly equals better, when sometimes its a lot easier to do a find/grep/sed/awk type command line.[/QUOTE]

It's not that GUI is better, it's that having the choice of both GUI and CLI is better.

---

### Post by desdinova on 2005-06-24
[QUOTE=Leif]It's not that GUI is better, it's that having the choice of both GUI and CLI is better.[/QUOTE]

Oh I agree - hence the smiley ;-)

---

### Post by skoal on 2005-06-24
[QUOTE=Leif]It's not that GUI is better, it's that having the choice of both GUI and CLI is better.[/QUOTE]
Yes, sir! Exactly! Down here in Texas we got fire ant problems.  When I say "problems", I mean "carry your sleeping dog off to their mound and eat 'em" type problems.  Now, the *quick* and *easy* way of taking care of those little fire ants is with a can of gasoline and a match...but...I choose the sometimes *slower* (albeit much more satisfying) method - roasting random workers with a magnifying glass as they carry back pieces of "stomach exploding" cream of wheat to their queen.

It's all about choices...

...and...

...sweet sweet satisfaaaaaaaaction...

\\//_

---

### Post by Optimal Aurora on 2005-06-24
[QUOTE=poofyhairguy]I'm just going to straight up ask the community on this one. Please beat me up and tear my logic apart- I'm posting this for that reason.

As many know I try my best to help out new Ubuntu users. Many of us do, and its a great thing. Often on this forum I will tell people commands to put in the command line to fix their problems. Recently I was told that this is not the best thing, as it scares away new ex-Window's users who associate "command line" with "Dos" (this ignores that fact that a big "feature" of longhorn will be a functional CLI). Azz, another moderator here is big on giving answers that fix problems through a graphical method if possible. Supposedly the Ubuntu developers themselves have set out a goal that "an Ubuntu user shouldn't need to touch the command line," but until they make a GUI tool for ndiswrapper (aka the hardest thing for a new user to do) I don't put much weight into their opinions on the matter.[/QUOTE]

All other distros you have to do the same command-line thing too...

Back in Windows 3.1, you started windows by typing in 'win' in the c prompt... I learned to use the c prompt for a lot of things, however I dislike it... Although, I love programming, so for me personally, I rather use linux...

---

### Post by Optimal Aurora on 2005-06-24
Oh and by the way it is a whole lot easier to tell some one to open up a terminal (for me I have one sitting in my bottom gnome bar that looks like a dock from Mac OSX), than having to say go to System --> Administration --> Users and Groups, then open this...

---

### Post by Leif on 2005-06-24
[QUOTE=skoal]Yes, sir! Exactly! Down here in Texas we got fire ant problems.  When I say "problems", I mean "carry your sleeping dog off to their mound and eat 'em" type problems.  Now, the *quick* and *easy* way of taking care of those little fire ants is with a can of gasoline and a match...but...I choose the sometimes *slower* (albeit much more satisfying) method - roasting random workers with a magnifying glass as they carry back pieces of "stomach exploding" cream of wheat to their queen.

It's all about choices...

...and...

...sweet sweet satisfaaaaaaaaction...

\\//_[/QUOTE]

OK, excellent, so we need GUI, CLI, and at least two ways of killing ants. When all of this is done, ubuntu is gonna be AWESOME !

---

### Post by skoal on 2005-06-24
[QUOTE=Leif]OK, excellent, so we need GUI, CLI, and at least two ways of killing ants. When all of this is done, ubuntu is gonna be AWESOME ![/QUOTE]
Apparently, there's already more than 1 way to [uncover](http://www.ubuntuforums.org/showthread.php?t=43909) a 'moo' cow message with our package management tools.  This distro just keeps getting better by the day...

p.s. Is there any way I can get a GUI (not CLI) moo cow in Synaptic?  That CLI cow looks like it's been overmilked.  I want a GUI moo cow so that when you click it's cow bell dangling around it's neck, Christopher Walken's voice pipes through my speakers, "I got the feva for more packages, and the prescription is more cowbell."  Then you click the cowbell again and synaptic automagically reloads more hidden repositories...

\\//_

---

### Post by TristanMike on 2005-06-24
Hi, hope you don't mind if I comment,  :)  First I'd like to say thank you to Poofy and all of the great people here on the Ubuntu forums for all of your help to us neon green noobs.  I personally find it difficult to grasp the terminal, mainly because I've only first heard/experienced it within the past couple weeks.  

The only thing I'd like to say about the help given in command form, and to reiterate what "aragorn2909" said, that giving a command line to c/p is fine and dandy, being able to do it might be impossible to mess up(though I have managed to accomplish this task :-k ) but not understanding what it does really does put me no further ahead in my understanding of the terminal and how it/Linux works and thus a more effecient Linux user.  

There have been times when I have been searching for a solution to a problem and find a thread with it, but one that I don't understand at all and couldn't apply to fix my own problem.  Think about what people who don't know what "lol" or "brb" must think in their head.  People, like myself, don't know what all of the anacroynms and commands are for, and people who don't know, might not want to ask for fear of being laughed at or frustrating the nice people who help because they should have installed RUTE(wait, how do I....? just kidding).  

Perhaps there could be a small Legend at the bottom of the pages or at the sides giving a brief description of what some of the more basic commands do.  That way when someone posts either for help or in response, there is some sort of reference if needed.  Also I have found that when someone associates the command with the gui proceedure, it helps to better understand the terminal and its functions.  I only just found out the other day that apt-get was the exact same thing as synaptic.  This, of course, this is just from a really, really green computer guy.
TristanMike
(Edited to be more digestable.... ;-) )

---

### Post by Xian on 2005-06-24
[QUOTE=TristanMike]Also I have found that when someone associates the command with the gui proceedure, it helps to better understand the terminal and its functions.  I only just found out the other day that apt-get was the exact same thing as synaptic.  This, of course, this is just from a really, really green computer guy.[/QUOTE]
Yes, this is a good example of how the command line version of a GUI can really help to empower a user. There are just so many more functions that can be accomplished in Apt when it is better understood. 

You also might want to segment your paragraphs into more digestible portions. :)

---

### Post by az on 2005-06-24
"Will Ubuntu ever reach the lofty goal of "never needing the command line?"

Can I just know what this thread is really about?  If it is about the superiority of the command line, that depends on your use.  Yes, the goal is to avoid the command line as much as possible - this is a good thing.

If it is about whether or not we need more useability, well, that is a hot topic in linux these days.

If you look at the work that Seth Nichols is doing in Fedora with "interface design" and contrast that with the people who are saying that all we need is something that works, and not try to push linux to the forefront of GUI art-deco, you still get the point that a lot of people are looking into this in one way or another.  Canonical even commisioned a useability study on Hoary the day it came out

Is this a "Please stand up if you are a purist" thread?

---

### Post by aragorn2909 on 2005-06-25
[QUOTE=azz]"Will Ubuntu ever reach the lofty goal of "never needing the command line?"

Can I just know what this thread is really about?  If it is about the superiority of the command line, that depends on your use.  Yes, the goal is to avoid the command line as much as possible - this is a good thing.

If it is about whether or not we need more useability, well, that is a hot topic in linux these days.

Is this a "Please stand up if you are a purist" thread?[/QUOTE]

I must answer your first question with another question.  Does Ubuntu ever WANT to reach the "lofty goal"  of never needing the command line?  

Secondly, is this thread about the superiority of command line over gui or vice versa?  I don't think so.  Is the goal really to avoid the command line as much as possible?  I don't think so either.  My thought here is, why would Ubuntu users want to deny themselves this obviously powerful little tool?  I mean, even in XP, try pointing and clicking a Dos batch file.  Granted, I don't want to do things like burn DVD/CDs from the command line.  I don't want to move mp3s to my mp3 player from the command line.  I want drag and drop, point and click as much as the greenest of n00bs, but like my Mother says, a place for everything and everything in its place.  Does this make me a "purist"?  Hardly.  This makes me a person who wants to get as much "useability" out of my computer as I can.

I'll sit down now. ;-)

---

### Post by Brunellus on 2005-06-25
[QUOTE=aragorn2909]I must answer your first question with another question.  Does Ubuntu ever WANT to reach the "lofty goal"  of never needing the command line?  

Secondly, is this thread about the superiority of command line over gui or vice versa?  I don't think so.  Is the goal really to avoid the command line as much as possible?  I don't think so either.  My thought here is, why would Ubuntu users want to deny themselves this obviously powerful little tool?  I mean, even in XP, try pointing and clicking a Dos batch file.  Granted, I don't want to do things like burn DVD/CDs from the command line.  I don't want to move mp3s to my mp3 player from the command line.  I want drag and drop, point and click as much as the greenest of n00bs, but like my Mother says, a place for everything and everything in its place.  Does this make me a "purist"?  Hardly.  This makes me a person who wants to get as much "useability" out of my computer as I can.

I'll sit down now. ;-)[/QUOTE]
 n00bs (myself included) often want something that they can understand intuitively.  Merely being given black-magical incantations like ```
tar -xjvf foobar.tar
``` might solve their problems, but won't give them the sense that they can really do anything on their machines.

Of course, in a perfect world, they'd all STFU and learn the CLI, right?  Sure.  But this thread is about giving people a safety-net.

---

### Post by aragorn2909 on 2005-06-25
Exactly (almost) what I said in my previous post on this matter.  I'm sensing a common theme from the n00bs:
GUI = good
CLI = good (with explanation)

---

### Post by aysiu on 2005-06-25
Really, it comes down to choice. Ideally, no one should *need* the command-line or *need* GUI. No one should be denied either one. Right now, though, Ubuntu needs the command-line for a lot of basic functionality. I happen to like the command-line for certain things, but if people don't want to use it, they should have to. Right now, Windows has gone the other way. Sometimes I want to just open a DOS terminal and type a bunch of commands, but Windows XP won't let me do certain commands while the Windows desktop is running.

---

### Post by manicka on 2005-06-25
Since I first tried Linux 5-6 years ago I was attracted by using the command line to do things and found it refreshing after using GUI's for everything. I had never been a DOS person.

I still like GUI's for a lots of things (synaptic being one, although apt at the command line is slowly taking over) but the command line and manual editing config files is where it is at for me. 

Basically it's what brought me to Linux in the first place as I was bored in the GUI world of other os'. 

I really think that Ubuntu has the balance just right :D

---

### Post by The Producer on 2005-06-25
This shouldn't be a debate.

If your trying to get Windows users...simple...computer illterate people...people who could care less about "knowing all about their base system", creating GUI solutions shouldn't be something that's debated.  

I don't see how almost no one here can realize that.

Rarely do I see anyone here, or in any Linux forum, think about any of this from their POV.  All I see is "I this, I that, or we (we as in the faction of people who find learning more about computers interesting)".  And if you are not apart of "us", then your behind is going to have to learn until you are, regardless of what time that takes out of your life...when it can be done simplier on other systems.

And your dissappointed to see why people think Linux is elitist.

I understand that people are going to have to learn, or "get used to" the GUI, regardless of how "user friendly" it's designed, but in that process, don't force them to HAVE to learn the CLI.  It's overkill.  Don't take away their freedom to just sit down, simply install a few things, install a new device, and view multimedia without the annoyances of viruses, without having to open the CLI.  

I know it's completely possible to set up Ubuntu or any Linux version where this can be achieved, while maintaining the legendary stability and security that, before, only people who knew what they were doing could access.  And if other people want the power, they can use it, or go to another "untainted" distro.  If the developers think it can't be obtained, maybe they are the ones who need to learn.

I think the Linux community needs to quit forcing this "fundamentals" mess, and leave it only to the people who want to learn it.

---

### Post by skoal on 2005-06-25
[QUOTE=The Producer]I understand that people are going to have to learn, or "get used to" the GUI, regardless of how "user friendly" it's designed, but in that process, don't force them to HAVE to learn the CLI.  It's overkill.  Don't take away their freedom to just sit down, simply install a few things, install a new device, and view multimedia without the annoyances of viruses, without having to open the CLI.[/QUOTE]
In an ideal world, this would be the case on Ubuntu (or any Linux distro for that matter).  Unfortunately, in practice there are just so many utilities and open source tools out there (being developed all the time), the developers (or even those who use them) don't have the time to develop a GUI for it.  I don't understand how so many people fail to see that point.  That's not being elitist.  That's being *practical*.  What's the old saying about things freely given?  Don't bite the hand that feeds you...or better yet, help out and "cook" every once in a while...aka...learn GTK/QT and help the developer out.  His time is just as important as the next...

\\//_

---

### Post by az on 2005-06-25
[QUOTE=skoal]In an ideal world, this would be the case on Ubuntu (or any Linux distro for that matter).  Unfortunately, in practice there are just so many utilities and open source tools out there (being developed all the time), the developers (or even those who use them) don't have the time to develop a GUI for it.  I don't understand how so many people fail to see that point.  That's not being elitist.  That's being *practical*.  What's the old saying about things freely given?  Don't bite the hand that feeds you...or better yet, help out and "cook" every once in a while...aka...learn GTK/QT and help the developer out.  His time is just as important as the next...

\\//_[/QUOTE]


Uh, no.

The whole point of Ubuntu is to have a more useable system than you would get with Debian.  Canonical takes a subset of packages that are in debian and makes them useable for humans.  They take the time to develop a GUI for it.

You can use universe and you can use debian, but the goal of what ships in Ubuntu is to be useable by everybody.

---

### Post by aragorn2909 on 2005-06-25
[QUOTE=azz]but the goal of what ships in Ubuntu is to be useable by everybody.[/QUOTE]

But there is no reason that command line can't/isn't useable.  I find it both useable and useful.  What I see on these forums, and in this thread, is people's DEPENDANCE on gui.  Ubuntu/Linux has to be more "Windows-like", more "OS-X-like".  Nonsense.  Ubuntu has to be more Ubuntu-like.  This is where I agree whole-heartedly with aysiu

> Really, it comes down to choice. Ideally, no one should need the command-line or need GUI. No one should be denied either one.

---

### Post by skoal on 2005-06-25
[QUOTE=azz]The whole point of Ubuntu is to have a more useable system than you would get with Debian.  Canonical takes a subset of packages that are in debian and makes them useable for humans.  They take the time to develop a GUI for it.[/QUOTE]
I think that goes without saying, and that's probably why we all love Ubuntu. 

As poofyhairyguy stated in the very first post, "*Till now I've been of the opinion they need to just get used to it early on.....its not like we have a YAST or something like that so command line work is inevitable*."

He's absolutely correct.  I think that's a perfect illustration and the one which I was trying to stress, and more importantly, the one which all linux users should keep in mind.  What's so difficult in extrapolating that statement made by poofy, mixing in a dose of reality by my prior post, and applying it to other applications here on linux? What am I missing here?  Most people in this thread seem to be living "above the clouds".  Do I really need to point out and illustrate the many many GUI *gaps* left behind in most linux apps?  Unless I misunderstood poofy, I stand on his side of the "line", neither ideological nor phillosophical, just practical.

The ideological discussion is pointless^H^H^H^H^H^H^H^H^Hwhimsical.  To each his own - since by birthright, my choices are my own.

As for the phillosophical, so long as 1 wire extends from your USB or PS/2 port and connects to a flat piece of plastic with keys you rub your fingers on, there will always be a need for a CLI, so long as there's a need for a keyboard.  

\\//_

---

### Post by The Producer on 2005-06-25
Basicly, what i'm saying is that for doing basic or routine things, like installations, configuration, etc, there shouldn't be a need for a commandline at all.  And this can be done without copying OSX or Windows.  At least in Ubuntu. I'm not saying  to completely remove the thing.  But I guess i'm living in a fantasy world... :???: 

> What's the old saying about things freely given? Don't bite the hand that feeds you...

Your right.  You get what you pay for.  ;-)

> or better yet, help out and "cook" every once in a while...aka...learn GTK/QT and help the developer out

learn GTK/QT and help the developer out = "Why don't you do it yourself?"

No thanks.  Programming isn't my specialty, and i'm not really that interested in it.    In the past I never had a need for programming, but, I guess if I want to make any practical use out of Ubuntu for myself the simple people, I guess it's time to learn. Or just end it all and stick with Windows or OS X.

Linux (or even Ubuntu) isn't a prefered system for other people.  At least the developers for OS X and Windows don't ever tell me "if you want this feature, why don't you learn and do it yourself?", so I might as well advise people to stick it out with Windows or switch to OS X.  Open source gives the developers, the people I assume who love to program, a chance to really excel over proprietary systems, or, it gives them "freedom", but, I guess no one is taking full advantage of it.  So much for the "freedom".

If half of this had nothing to do with "pointless ideological discussion phillosophical reasons", then there shouldn't be any arguement as to trying develop more GUI functions in **Ubuntu Linux: Linux For Human Beings**.

> Really, it comes down to **choice**. Ideally, **no one should need the command-line** or **need GUI**. No one should be denied either one.

---

### Post by az on 2005-06-25
"Till now I've been of the opinion they need to just get used to it early on.....its not like we have a YAST or something like that so command line work is inevitable."

There are two problem with the above statement.

One:  Most people, when told that the way to solve their problem is to open up a command line and type more than four charaters will run away saying that this is a crap system.

Two:  I could never get Suse to install on a box, so I do not know what YAST can and cannot do.  But, Synaptic is able to take care of most of your configurationjust by selecting the package, hitting "package" in the menu and "configure..."  Other than that, the Gnome suite is there for that.
There is actually a 10x10 goal for Gnome.  That is, have gnome on ten percent of the desktops in the world by 2010.

---

### Post by weekend warrior on 2005-06-25
Well this looks like the debate du jour so I'm going to throw a spanner in the works  ;-)  with a very simple point that is seldom talked about in regard to CLI. Consider if you will the following basic CLI command:

adm-eah vees-rimshanah

This of course will make perfect sense to you. It's a very basic command! It shouldn't confuse anyone at all. What's that? You can't make out a word? Ah well, perhaps the problem is you don't speak Hebrew? Yes that's correct, if linux came from Israel this is what you would be up against when learning CLI. Now try to imagine what:

apt-get dist-upgrade

looks like to someone from let's say... India, with minimal or no English skills. It's often overlooked (in the English speaking community) that CLI is  basically English shorthand. What looks plain as day to a native English speaker is no where near as easy to decipher for a non-English speaker. 

Now consider that it is one of the goals of Ubuntu to be easily accessible to people in their native language. CLI does not in large measure meet this requirement. A translated GUI however does as it would allow an Indian user in this case to function without any difficulty at all. This is one of the clearest rationals for more GUI and less CLI.  


Have a look at [this thread](http://ubuntuforums.org/showthread.php?t=16377) for a real-life Indian example of this problem from our very own forums.

Ah and btw it's actually "Ad me'ah ve'esrim shanah!" and means "May you live to be 120!"  :smile:

---

### Post by poofyhairguy on 2005-06-25
[QUOTE=azz]
There are two problem with the above statement.

One:  Most people, when told that the way to solve their problem is to open up a command line and type more than four charaters will run away saying that this is a crap system.[/QUOTE]

Yeah...but my train of thought was:

"well...if all it takes is the command line to scare a person away, then honestly they might end up thinking Ubuntu is crap no matter what I do. Why waste my time?"

Its HARD to avoid the command line right now. I personally think that is necessary for at least 80%+ of Ubuntu users (maybe even more) to touch the command line at least once. Why not just get it out of the way?  As they say in the movies "separate the men from the boys." (no offense to female Ubuntu users...its an analogy) The whole thread was basically asking if my opinion is cruel and heartless...because I really think it isn't.

By the way- in reference to other posters- I'm all for developing new GUIs. Thats not what this is about. I like gtk2 GUIs, they are nice. The problem is that there are not enough now to pretend that we can get by with out them (by comparison I think that you almost can get by with all GUI in SUSE, its was a comparison). 

Ubuntu GUIs are not developing fast enough. The community has made more than the developers have.

And Azz...I have to call you on something. Ubuntu doesn't really add any new GUIs to Debian. Thats what things like Xandros and Libranet do.

---

### Post by TristanMike on 2005-06-26
[QUOTE=poofyhairguy]Yeah...but my train of thought was:

"well...if all it takes is the command line to scare a person away, then honestly they might end up thinking Ubuntu is crap no matter what I do. Why waste my time?"[/QUOTE]
First, there is no way I could see a person say Ubuntu is crap if they looked at it unless they were completely closed minded.  It looks great, feels great, similar to windows, and there's a bit of new learning that needs to be done but that's all, should you expect any different from something that's not Windows?  So I really don't think is the command line alone that scares people away, it's just different, and different can be scary, especially when windows has forced people out of the option of using it and thus learning commands.  Would you give keys to a car to somebody without making sure they new how to drive it in the first place?  I hope you get my analogy.  I mean, you have to admit that some of the commands are a little cryptic, especially to a noob like me.....tar zxvf ubuntu5.04.tar.gz <--What's that?(not really... :) )

I assume most of this comes from the "Absolute Beginner" Section of this forum, but we are Absolute beginners, have absolutely no idea on how to use these functions and a little help by the hand is VERY much appreiciated, I can say anyway.  Association is a very important tool, and if a person can assocate the commands with what they would see in a window, it helps in transition, I think.  Maybe the section should be divided into Absolute Beginner and Intermediate User, or something to help define the needs and experience of the user.  This is just my opinon from converting from Windows in this short while.
TristanMike

---

### Post by Retrix on 2005-06-26
Hopefully I can be of help to this lack of GUI problem. I have just been notified that my proposal for the Google Summer of Code contest has been accepted.

Basically that means that over the next few months, I will be working with Ubuntu to deliver more and better GUI tools for daily Ubuntu use as well as administration, maintenance and setup. I have a number of ideas already, but the more the better, so if you have any ideas that need to be implemented, please let me know.

I am in the middle of my exams at the moment, but as soon as they are done, I'll be getting cracking on improving Ubuntu for everyone.

-Sam Pohlenz

---

### Post by skoal on 2005-06-26
[QUOTE=azz]Canonical even commisioned a useability study on Hoary the day it came out[...][/QUOTE]
Hey azz, where is that study you mentioned? I'm very interested in reading their findings.  I googled around and could only come up with [this](http://www.lilax.net/textfiles/2005-05-14/ubuntu_gulev-slides.pdf) and [this old thread](http://mpt.net.nz/archive/2005/04/11/ubuntu), which we talked about somewhere ad nauseum, elsewhere in these forums.  Is there another one I missed?

Part of many Computer Science undergrad curriculum have entire courses devoted to this topic of "usability".  This was even offered on the graduate level waaaay back in the early 90's at my alma matter, which I elected not to take at the time.

I think Ubuntu (and the developers et al.) should be commended in their efforts to fill in those GUI *gaps*, which myself and others believe exist.  What other distro offers such "bounties" to their community at large?  I can't think of one.  What I personally find most promising about this distro and it's stated goals is the "consistent enforcable poilicies" which Ubuntu aims to achieve by closely integrating and tying together common Desktop and system level tasks under *one* unifying desktop, Gnome.  The only other distro which comes close to that is Linspire, IMO.  Enforceable is the applicable key word here.  It shouldn't be confused with "lack of choices" either.  In my estimation, enforceable means achieving prodcutivity and simplicity at the expense of knowledge (or as others may define it, "confusion"), in the name of consistency, for the sake of usability.  

Maybe an illustration will help provide some insight into *my* understanding of this thread, and the association of providing a CLI or GUI solution.  To all those fisherman and "cooks" out there, they understand what I mean when I say there's more than one way to clean a fish - however, some ways waste meat, others make a mess, and even still, others leave you bones.  In the aftermath, the "cook" only wishes to provide the filet, and for the "hungry" who asked for it, that's all they care to see (or ever asked for).  So, what's a "cook" supposed to do?  In my estimation, you provide the knife, display the guts, and hand him the filet.  If store bought fish on display in a bed of ice is all the "hungry" have time for, or ever cared for, what possessed them to take a "boat trip" with a "fisherman" in the first place?  Curiosity? Yes, for some.  How's the fisherman supposed to know?  I hope you understand the indirect analogy and the two *environments* I'm referring to.  That's in no way implying that the "fisherman" in his environment doesn't prefer (or use) store prepped filets either.  Even the "fisherman" has been "hungry" before too, and even he doesn't know how to clean every "fish".  But until such time when he can provide his own "store", that "fisherman" should teach others to be self-sufficient, and in time, "cook" for others.  Afterall, isn't that what the OSS community is about?

The bigger question for me, as an active participant in this community who enjoys helping others (and being helped myself), is what responsibility (if at all) do I have when faced with providing two equally viable solutions to a question.  CLI or GUI?...which is what I thought Poofyhairyguy was originally addressing by his post.  To some extent, the question is philosophical, but the only answers I can provide...are the practical.

\\//_

---

### Post by weekend warrior on 2005-06-26
I agree with highlighting the practical rather than philosophical aspect to this, which is why I chose that example of the language factor in CLI. For some users CLI isn't a practical (or desirable) solution and may never be so. In addition, if the goal of 10x10 is taken seriously, then the luxury of sluffing these users off, saying they can just go use a Mac if they can't accept CLI, no longer exists.

I think particularly for those like myself, whose computing journey began before the Macintosh or Windows existed and have plenty of typing under their fingers, or simply those who feel like fish in water around the CLI, this needs to be kept in mind. The type of assistance offered when both CLI and GUI solutions are available depends far less on the helper's own feelings on the matter and rather much more on the type of user you're helping, their *current* needs and their given background/situation.

---

### Post by az on 2005-06-26
"The bigger question for me, as an active participant in this community who enjoys helping others (and being helped myself), is what responsibility (if at all) do I have when faced with providing two equally viable solutions to a question. CLI or GUI?...which is what I thought Poofyhairyguy was originally addressing by his post. To some extent, the question is philosophical, but the only answers I can provide...are the practical."

*Bing*  You hit it right on the head.

I think you are doing users a bigger favor by emphasising the GUI solution.  I beleive that will reach the greater number of users and retain them by using the existing GUI solutions.

Others are saying that it is better in the long run to learn the command line.

I think poofy would be right if this were three years ago.  Back then, you probably could not avoid the command-line for much.  These days, I think more than fifty percent of Warty users could avoid it completely, and probably ninety percent of Hoary users can avoid it.
I can only image what Breezy will offer...  Things are really happening fast - I do not think it is realistic to say that users are going to _need_ the command line soon.

---

### Post by az on 2005-06-26
"And Azz...I have to call you on something. Ubuntu doesn't really add any new GUIs to Debian. Thats what things like Xandros and Libranet do."

Actually, gnome goes into Ubuntu before it gets into debian.  Most of the work the Canonical does goes upstream relative to debian.

This is unlike suse with YAST which is addon.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=azz]
Others are saying that it is better in the long run to learn the command line.

I think poofy would be right if this were three years ago.  Back then, you probably could not avoid the command-line for much.  These days, I think more than fifty percent of Warty users could avoid it completely, and probably ninety percent of Hoary users can avoid it.[/QUOTE]

Unless they need ndsiwrapper. Or to unmute their creative sound card.  Or to fix xserver settings. Or many more things.

I'm not so optimisitc about that after my time here on the forums. I believe that the only way a person could avoid the command line in Ubuntu is if some else sets up the computer for them.

> 
I can only image what Breezy will offer...  Things are really happening fast - I do not think it is realistic to say that users are going to _need_ the command line soon.

I personally didn't think that Hoary had amazing new GUIs that Warty didn't. As far as I can tell, the most needed GUI isn't going to be in Breezy (I could be wrong). 

This is a good thread though. I'm glad to get people's opinions. I think my resolve will be to create guides for the most common easy things you can do with a GUI, but tell people commands when its easier to compy and paste.

---

### Post by polo_step on 2005-06-26
[QUOTE=AgenT]That's because Windows does not have a proper terminal. Window's "command prompt" is, at best, garbage. [/QUOTE]
That's true.  The ability to cut & paste in Linux with the two-button click is very nice.

Still, if I have to actually WRITE a long command line, I'm in a certain amount of trouble, because I have bad eyesight and can't touchtype anyway.

I have seen processes described to new users in command line that would have been done faster and more foolproof by the GUI options that were described later on by other respondents.

Comand lines don't scare me -- I started out in CP/M and am used to the idea -- but GUIs are easier for me to see and work with in most cases.

People without my background find command lines totally threatening and "backward" when converting to Linux.

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=polo_step]
People without my background find command lines totally threatening and "backward" when converting to Linux.[/QUOTE]

Some of these same people will call it a feature when Longhorn can do that. You can never make everybody happy.

---

### Post by aysiu on 2005-06-26
[QUOTE=poofyhairguy]Some of these same people will call it a feature when Longhorn can do that. You can never make everybody happy.[/QUOTE]

It would be a feature if Longhorn had it. However, that doesn't mean there's no need to create a fully independent GUI for those who are most comfortable with it. For Ubuntu, having GUI for most of the tweaking would be a feature. For Windows, having a functional DOS within Windows would be a feature. The most fully-featured OS would be the one in which you could do almost everything you need to do in GUI, and in which you can also do everything via the command-line.

It shouldn't be an either/or situation. Both options should always be available. That's what's so great about dpkg right now. If people want to type *apt-get update* and *apt-get install someprogram*, they can do that. If they want to click on Synaptic Package Manager, Reload, Install, and Apply, they can also do that. Having the freedom to use both methods is the ultimate "feature."

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=aysiu]It would be a feature if Longhorn had it. However, that doesn't mean there's no need to create a fully independent GUI for those who are most comfortable with it. For Ubuntu, having GUI for most of the tweaking would be a feature. For Windows, having a functional DOS within Windows would be a feature. The most fully-featured OS would be the one in which you could do almost everything you need to do in GUI, and in which you can also do everything via the command-line.

It shouldn't be an either/or situation. Both options should always be available. That's what's so great about dpkg right now. If people want to type *apt-get update* and *apt-get install someprogram*, they can do that. If they want to click on Synaptic Package Manager, Reload, Install, and Apply, they can also do that. Having the freedom to use both methods is the ultimate "feature."[/QUOTE]

I agree it would be nice if we could have both....but I'm a practical man...we don't have both in many cases.  You can say that there SHOULD be a GUI way to do everything, but that attitude doesn't make a GUI ndiswrapper tool (or any GUI tool) magically appear. Only years of development do that.

Basically there are two kinds of new users in this regard: those that will use the command line and those that won't. Is it worth nursing those that won't use the command line when they would be more happy with Windows/OSX anyway? Should I spend the extra time helping them when they might just reinstall when they find out the truth- after a while you must use the command line in Ubuntu to do the neatest stuff.

Should I spend time on those people, or should I just say commands to weed out those people out so that I can spend more time helping these sorts of people?:

[http://www.ubuntuforums.org/showpost.php?p=229907&postcount=5](http://www.ubuntuforums.org/showpost.php?p=229907&postcount=5)

I quote:

> 
I have heard good things about Ubuntu and even if I was afraid of the command line I don't see the point in giving up at the first hurdle.


That sounds like a person that could be a happy Ubuntu user RIGHT NOW. Those people that NEED a GUI for every task to feel comfortable might not be happy with Ubuntu for another 3 or 4 releases.

I don't really care about the philosophical "is the GUI better." I think it is better in most cases. I prefer GUI tools. I like synaptic.

But I'm also a realist and I don't want to lead people along if in the long run Linux is not mature enough for them right NOW.

---

### Post by N'Jal on 2005-06-26
Shit this thread moved fast...

Personally it might have something to do with learning styles as well since there are people who need graphical aids when remembering things and others need to see the text written down to remember things, personally i like graphical aids however i find the command line very easy, i must be strange then o.O. 

But im sure you all understand the point i am trying to make, either you need graphical tool's or you prefer the command line to do most things, or you really don't give a toss and use what get's the job done quicker, sometimes if it's just a tweak of a setting that requires a long, somewhat hard to remember command to activate, i'll use a gui but if it's using apt i just use the command line.

---

### Post by sapo on 2005-06-26
[QUOTE=N'Jal]Shit this thread moved fast...

Personally it might have something to do with learning styles as well since there are people who need graphical aids when remembering things and others need to see the text written down to remember things, personally i like graphical aids however i find the command line very easy, i must be strange then o.O. 

But im sure you all understand the point i am trying to make, either you need graphical tool's or you prefer the command line to do most things, or you really don't give a toss and use what get's the job done quicker, sometimes if it's just a tweak of a setting that requires a long, somewhat hard to remember command to activate, i'll use a gui but if it's using apt i just use the command line.[/QUOTE]

the main problem is that people are used with windows...

if they all had started with dos and windows 3.1 as i did (it was the top os in that time) they wouldnt mind using the command line.

but they even dont know a the folders tree structure, how can the understand the cd command?  ](*,)

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=sapo]
if they all had started with dos and windows 3.1 as i did (it was the top os in that time) they wouldnt mind using the command line.
[/QUOTE]

Actually those people might be worse. As a former Dos user, I remember when I saw the command line's heavy use in Ubuntu I thought "geez...thats stuff the Window's world left behind years ago." (I was of course wrong about this).

If someone haw never seen it...the command line could be "a revolutionary way to do things."

---

### Post by az on 2005-06-26
[QUOTE=poofyhairguy]Unless they need ndsiwrapper. Or to unmute their creative sound card.  Or to fix xserver settings. Or many more things.

...


This is a good thread though. I'm glad to get people's opinions. I think my resolve will be to create guides for the most common easy things you can do with a GUI, but tell people commands when its easier to compy and paste.[/QUOTE]

If you cannot get onto the net(ndiswraper), or you cannot get into X(X server settings), you cannot cut and paste advice from the forums.  You have to print it out and type it in by hand,

A colleague of mine who has been using computers for twenty years himmed and hawed about making a boot floppy for knoppix for a whole week.  He had to use rawrite and type in a command with two arguments.

"I couldn't figure it out.  I just wasn't sure"

This was not to partition his drive or anything, but to make a floopy!  That demonstrates how you cannot rely on the command line solutions to retain new users.

As for the creative sound, that is a bug, no?   It is something that obviously needs to be fixed.  

If you are counting configuring advanced video card functionality, well, the only things that require 3d acceleration in the ubuntu base system are the bouncing cow screensavers.  That is how I justify that 90 percent of people do not need to use the command line.

And, as I understand (I may be wrong) the newest ATI (proprietary) drivers come with a GUI installer...

---

### Post by sapo on 2005-06-26
[QUOTE=poofyhairguy]Actually those people might be worse. As a former Dos user, I remember when I saw the command line's heavy use in Ubuntu I thought "geez...thats stuff the Window's world left behind years ago." (I was of course wrong about this).

If someone haw never seen it...the command line could be "a revolutionary way to do things."[/QUOTE]

hum.. thats kind of the oposite point of view.. i liked dos... and i really missed dos when using windows.. sometimes i wanted to delete all .jpg files in a folder.. or watch a batch script to do something  :roll: 

thats why i love linux.. the gui and command line are both powerfull!  :grin:

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=azz]If you cannot get onto the net(ndiswraper), or you cannot get into X(X server settings), you cannot cut and paste advice from the forums.  You have to print it out and type it in by hand,[/QUOTE]

Better than the GUI way....which is none. Thats kinda my point.


Eventually, in Ubuntu at the level it is now you will hit a wall where the only tools availible are command line tools. Some people might not make it that far...but I doubt it.

I can't wait for a GUI for everything. I like the way GTK stuff looks....

---

### Post by poofyhairguy on 2005-06-27
I just want to say I got what I wanted out of this thread. I have my answer. Its not the one I started with...but its close.

Thanks for the help.

---

### Post by Lasukie-kai on 2005-06-27
I read the first few posts of this thread, I'm not even going to bother with the rest. I'm sure its either gone way off topic, or into some sort of argument of Windows vs Linux.

I will now offer my two and a half cents.


If you think that the CLI is the future, drop Gnome, get one of the first versions of the Unix Kernal, and knock yourself out. Most of you would be lost without the current GUI functions, whether you admit it or not, even I am, and I've started on CLI Unix Kernals, so don't give me your whiney BS about it.

Secondly, where does it say CLI is a "Feature of windows longhorn" I'd just like to point out one very interesting point, CLI is a "feature" of every operating system in existence, because CLI is the only base-point interface with any kernal. 

On to the pathetic argument of "Oh its easier to tell newcomers to type into a box" yeah well, my friends, its just as easy for them to click a check box, argument is flawwed and invalid. Not to mention, Typo's. Linux's functions aren't exactly user friendly.

Now, a fully GUI interface yes, it is impossible, but look at Windows and OSX, they have a minimum of CLI elements, and on NT based cores  its only a DOS Shell, not the full DOS system, as in previous versions.

And need I remind you, Most people is using what operating system? Hint, its not Linux.


I love Ubuntu Linux as stability
I love Ubuntu Linux as "Most" of its community members
I love Ubuntu Linux as its potential

I switched back to  windows because:

It does what I want it to do, and nobody will do it in linux because their lazy/idealistic programmer fools

I can run applications easily

I can INSTALL applications easily

I don't have to spend three hours in a console getting what I need to get done, done.


I think a GUI is a damn good idea.

---

### Post by skoal on 2005-06-27
[QUOTE=Lasukie-kai]If you think that the CLI is the future[...][/QUOTE]
Didn't Dave try to shut down Hal with a keyboard, not a mouse.  What about Data trying to prevent a core breach on the Enterprise using a bridge panel?  Oh, and how about Bishop responding back home that the alien was safely "inside", chewing away at John Hurt's pancreas.

Until I see more futuristic movies using a mouse pointer, I'm still convinced that the CLI *is* the future...

but that's just me...hell, I still drive a '64 Impala 4 door sedan.

\\//_

---

### Post by Lasukie-kai on 2005-06-27
[QUOTE=skoal]Didn't Dave try to shut down Hal with a keyboard, not a mouse.  What about Data trying to prevent a core breach on the Enterprise using a bridge panel?  Oh, and how about Bishop responding back home that the alien was safely "inside", chewing away at John Hurt's pancreas. [/quote]

Movies made in the 70's and 80's, your a real genius Skoal, you just made another invalid point "Wow, outdated movies use CLI" And for the record, LCARS is a GUI, not CLI, its run by specific buttons not by a keyboard.

> 
Until I see more futuristic movies using a mouse pointer, I'm still convinced that the CLI *is* the future...

but that's just me...hell, I still drive a '64 Impala 4 door sedan.

\\//_


Would you like me to list several sci-fi movies involving GUI?

BTW, a 69 GT500 would destroy your impala four door.

---

### Post by skoal on 2005-06-27
well, I'll admit I'm a little outdated...no argument there.  Also, I'm quite sure you'd blow me away on your 69 GT5000.  When I ride, I like to ease back, flip on the AM radio, and watch the pretty girls smile.  That's how I roll...

I honestly don't know of any sci-fi movies that have used GUIs in them.  I know this is kinda off topic (maybe), but refresh my memory.  You're probably right, I just can't think of any at the moment. 

\\//_

---

### Post by az on 2005-06-27
Okay, this thead is heading off the deep end.  If it does not change directions, it will be locked. Otherwise, let's continue intellient conversation.

---

### Post by skoal on 2005-06-27
awww fiddlesticks and tarter sauce...

just 'pm' me Lasukie...

\\//_

---

### Post by Lasukie-kai on 2005-06-27
Any Star Trek movie after #6 use LCARS, and this is thus a GUI (the functions are buttons over an interface, not direct input, plus look at the bridge of the Enterprise-C-E and Voyager, DS9 and all other ships beyond Reliant Class.

Star Wars, even the 1970 films used HUI (Holographic User Interface) as a huge part Thats still graphical.

Andromeda (Series) Uses HUI and GUI interfaces also.

The Computer Stations in Macross 7 and Macross Plus (Animes) used GUI.


Gui is an interface overtop of an interface (Graphical) its run by Buttons, which can be Touch Pads or Icons, but still Representive over top of the Kernal Code (Graphics) 

Any movie or television series witch uses graphics as any form of intergral control unit is using GUI, regardless of the argument.

Secondly, many Sci-Fi movies don't use GUI for an incredibly simple reason, they can only use todays technology for sci-fi, they can't use tommorows technology yet, so their fundamentally representitive of what we can do now.


More Girls will look at a Cherry Red 69 GT500 with shavetop then a fourdoor Grandma Mobile ;)



EDIT: Sorry was Typing

---

### Post by skoal on 2005-06-27
[QUOTE=Lasukie-kai]More Girls will look at a Cherry Red 69 GT500 with shavetop then a fourdoor Grandma Mobile ;)[/QUOTE]
lmao. well said...touche!

\\//_

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=Lasukie-kai]
Secondly, where does it say CLI is a "Feature of windows longhorn" [/QUOTE]

Here:

[http://www.pro-networks.org/forum/viewstory.php?t=57485](http://www.pro-networks.org/forum/viewstory.php?t=57485)

> 
On to the pathetic argument of "Oh its easier to tell newcomers to type into a box" yeah well, my friends, its just as easy for them to click a check box, argument is flawwed and invalid. Not to mention, Typo's. Linux's functions aren't exactly user friendly. 

Its not easier to go down a list inputting info into every box than it is to copy and past on the command line. The GUI isn't always easier.

> Now, a fully GUI interface yes, it is impossible, but look at Windows and OSX, they have a minimum of CLI elements, and on NT based cores  its only a DOS Shell, not the full DOS system, as in previous versions. 

Actually OSX has a nice command line.

> And need I remind you, Most people is using what operating system? Hint, its not Linux. 

Just because something is popular doesn't mean its better. Britney Spears proved that.

> 
I switched back to  windows because:

I don't have to spend three hours in a console getting what I need to get done, done.

Thanks...you proved my point. People like you that won't accept that you must use a command line aren't going to be happy with Linux anyway (as it is NOW), so there is no point to try to tell you some things in the GUI if in the end you won't be happy and switch back to Windows anyway. I'd rather spend my time on a potential convert.

A few years ago I worked as a telemarketer selling long distance. Within three months I was the high seller. Why? Because instead of trying to convert every person I called....lying to them left and right like my coworkers did...I would ask the question at the beginning "I work for _____ company, are you a customer of ours?" If they weren't I would pratically hang up on them....I only tried to improve the service of those who were happy with my product as it was. By weeding out those that MIGHT not like my product, I got more customers in the elimited time I was trying...

Thats why I will continue to post command line fixes if they are easier to explain or do......if I scare people away then they would have been scared away at some point.

> 
I think a GUI is a damn good idea.

Me too...doesn't make them magically appear.

---

### Post by Arthemys on 2005-06-27
Quick input:

Matrix 2: Trinity used a terminal running SSH to shut down a power grid.

CLI is much more efficient for remote administration as it's easier to compress text than huge graphics. VNC / RDP vs. SSH

One of my many hats in my company is a Windows sysadmin. I had to recover an exchange database recently that shit the bed... MS's solution according to their official knowledge base was to enter into the CLI and type out some commands and run the database files through some CLI based MS apps. Albeit extremely slow and utterly painful, even MS still uses the CLI for some of the really down and dirty jobs. I'm kind of looking forward to the CLI in longhorn...

The CLI in 2000 and XP is greatly improved from their prior versions; such as tab for auto complete and using the up arrow to cycle through previous commands.

---

### Post by aysiu on 2005-06-27
If people want full GUI Linux, they should use Mepis. I haven't found a single thing in Mepis that *requires* the command-line. I've *used* the command-line in Mepis, but it's not necessary--not to enable extra repositories, not to have numlock turn on by default, not to have partitions appear on the desktop, not to browse folders as root.

The only time you might need to use the command-line in Mepis is to edit the /etc/fstab file or the /etc/X11/X86Free files.

I happen to like Ubuntu as much as I do Mepis. I'm just saying... if people like GUI so much, there exists a point-and-click Linux, and that's Mepis.

---

### Post by The Producer on 2005-06-27
Sad....

Well, I tried.

At least we have Windows/OSX.  Let's hope this Linux "movement", doesn't ruin those for the rest of us.

---

### Post by Lasukie-kai on 2005-06-27
[QUOTE=poofyhairguy]Here:

[http://www.pro-networks.org/forum/viewstory.php?t=57485](http://www.pro-networks.org/forum/viewstory.php?t=57485)

[/quote]

CLI is CLI either way you look at it, every OS has it, its not a FEATURE its a GIVEN regardless of how many easyfied functions are added.


> 
Its not easier to go down a list inputting info into every box than it is to copy and past on the command line. The GUI isn't always easier. 

Its not easier to type or cut and paste three lines of code, then double click. The CLI isent always easier.


> 
Actually OSX has a nice command line.


Actually you missed the point. I said Minimum of CLI elements, not that it lacked it completely, clean your glasses.


> 
Just because something is popular doesn't mean its better. Britney Spears proved that. 

No, but more people will listen.


> 
Thanks...you proved my point. People like you that won't accept that you must use a command line aren't going to be happy with Linux anyway (as it is NOW), so there is no point to try to tell you some things in the GUI if in the end you won't be happy and switch back to Windows anyway. I'd rather spend my time on a potential convert.

You reach a stalemate, without allowing leaniency who wants to convert? Essentially, thats a setup for a very big letdown.

> 
A few years ago I worked as a telemarketer selling long distance. Within three months I was the high seller. Why? Because instead of trying to convert every person I called....lying to them left and right like my coworkers did...I would ask the question at the beginning "I work for _____ company, are you a customer of ours?" If they weren't I would pratically hang up on them....I only tried to improve the service of those who were happy with my product as it was. By weeding out those that MIGHT not like my product, I got more customers in the elimited time I was trying... 

And in the market long run, you lost your company possibly a good chunk of market.


> 
Me too...doesn't make them magically appear.


Maybe if you actually tried instead of fearing change.

---

### Post by skoal on 2005-06-27
Whoa! This does sound like more of an ideological discussion.  I think what's important to keep in mind is that a lot of us here are simply raising the question so we can better understand how to help you get what you need, with only the tools we can provide at present, or are familiar with.

Ubuntu is far far ahead of the game than most distros in that respect.  Since most don't even consider such a thread important...

\\//_

---

### Post by Lasukie-kai on 2005-06-27
What I do: I'm a 3d Graphic Artist and Video Editor

What I need: 3d Moddelling tools that are easy to use, in a stable enviroment, animation editing tools that are also easy to use in a stable enviroment, post processing tools, paint tools, and visualization tools that are easy to use in a stable enviroment.

What I have for this: Windows 2k, and Windows XP

What Linux can offer me: Uneeded headache

What Windows can offer me: uneeded headache, but ease of use in a relatively stable enviroment



I'm a mouser, I gave up on keyboard commands for simple tasks years ago. Windows accomadates this. I hope one day linux will reach a consensus and accomadate it as well. After all, if linux is about freedom, its my freedom to hope that maybe it can appeal to more then closet programmers.



I don't want to sound Ideological, but everyone here must realize, Linux user base is small, smaller then both the major OS's out there. It is to my understanding Ubuntu wants to remedy this. Or is it Ubuntu: For CLI using Human Beings?

Neither Linux (any distro) Windows or MAc OSX is what I want or need, but I make do with what I can use, and by doing so, Linux loses a potential convert because the responses I (and others) get are "Learn how to program it myself"

I have a job to do, I can't just pick up a coding in Linux book and make myself apps. Thats a programmers job. But Linux programmers seem to be getting lazier and more fearfull of change lately.

One of us needs to be more open minded.

---

### Post by The Producer on 2005-06-28
> What I need: 3d Moddelling tools that are easy to use, in a stable enviroment, animation editing tools that are also easy to use in a stable enviroment, post processing tools, paint tools, and visualization tools that are easy to use in a stable enviroment.

What I have for this: Windows 2k, and Windows XP

What Linux can offer me: Uneeded headache

....

**I have a job to do, I can't just pick up a coding in Linux book and make myself apps. Thats a programmers job. But Linux programmers seem to be getting lazier and more fearfull of change lately.**

 

Thank you.

Thank you from another animator, who has been on the search for video editing solutions on Linux.

From what I experienced so far being with Linux...this isn't a system I would want to work on, or tell others to use.  It's not because of LINUX itself, it because of the attitude of some of the users and programmers.

And it's hard to avoid, due to the nature of Linux and the community, especially when your new.  And honestly, i'm beginning to become tired of it.

---

### Post by skoal on 2005-06-28
Gimp, blender, and even ImageMagick come to mind. 2 out 3 are all mighty fine GUI tools, and the last provides an easy alternative via the CLI to fill in the blanks the other two don't handle just as quick, or just don't handle at all.  Moreover, they're all *free*.

Each has it's own "learning curve", which is no different than picking up a CAD 3D tool on a Win box for the first time, and which you shell out $500 each for.  I guess I don't understand.  What do you want?  Manuals are there.  The software is there.  The only obstacle is time.  In the end, we're all here trying our best to minimize that learning curve (time spent) as best we can, with what we know.

What am I missing?

\\//_

---

### Post by The Producer on 2005-06-28
To be honest, those programs you mentioned just don't stack up, compared to Windows solutions.

Period.

And video editing...

And at least I just want get my work done, without having to find some "workaround" because the tool I want is not supported....or won't be supported because it's proprietary.  I can careless about supporting the open-source movement.  I just want to get stuff done, even if I have to pay money for it, because chances are, that $1500 I spend on Lightwave is going to help me reach that goal.

The same goes with Ubuntu.  I just want to get stuff done, installed and running, preferabily without having to type code into a black box, without having to take time out of what I want to do to create my own programs to satisfy that.  But it seems as if no one wants that to change, seeing from the responses in this thread.

I think everyone should really, really reconsider where they are trying to go with this.  From the way things are going, I think Linux for the most part should stay for the techinically inclided, because I know friends and family who would give up using computers entirely if this is what they had to deal with, just so that they wouldn't get anymore viruses and the such.

---

### Post by Arthemys on 2005-06-28
I really hate to sound spammy about this but... Novell is trying to change what linux is for at least the business world and get businesses interested at ideally converted. They're trying to have an image of professionalism behind linux so that they can make sales on the linux based products over their netware based products.

I'm not starting up a flame of "Novell is better because" I'm just providing some insight as my company... Multi-facetted as it is, is a channel partner of Novell... They realize the future of the linux platform, and are moving very fast in my opinion with their products. Though they still do not have a fully "smooth running" desktop OS yet, this will take some time as due to the nature of linux and open source.

What needs to be done is what most people are realizing now, that an agreement needs to take place on say... What X server to use or what package type to concentrate on for example, or what should be used for scanning available wireless networks. There's so many different aspects and uses for linux that turning it into a product like Windows (used by so many) will take a dedicated team of developers. Why do you think Novell and MS pay their developers? To make a solid product and agree on a standard.

Final example: One employee sends out emails in plain text with on signature, one sends out emails with HTML and images with a fancy signature, and the boss sends out plain text with a basic signature. From a client standpoint, if you're dealing with each employee, you'll notice the inconsistencies quickly. There needs to be an agreed upon standard for just about every aspect of linux. And that requires developer time.

---

### Post by aysiu on 2005-06-28
I don't think video editing software is what's going to win people over to Linux or Ubuntu. With GUI solutions, Linux is far more likely to get the email/internet/word process crowd, which is a far larger base.

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=Lasukie-kai]
Maybe if you actually tried instead of fearing change.[/QUOTE]

Ok. I'll bite. Show me that GUI ndiswrapper tool in Ubuntu. Show me the GUI Xserver reconfig tool. Show me the GUI fstab editor. These are the most popular basic jobs that pretty much have to be done using a command line in ubuntu. If anyone knows an easy to install GUI for these, I'll tell people to use them. Till then you miss my point.

---

### Post by RickSGM on 2005-06-28
Well, back to the subject.  I'm a total newbie to linux.  I tried installing other linux distributions, and was told about ubuntu.  
I like the command lines you give, for it helps to get the job done.  It's not going to kill anyone to go to terminal and copy and paste a command, or to even retype the command if viewing from another pc.  The help on the ubuntuguide.org and the help here has been great, and in my opinion, stands second to none.  I've used windows since 2000, and found some apps in windows that don't have as good help as ubuntu.
Keep the good work up!  \\:D/       =D>

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=The Producer]
The same goes with Ubuntu.  I just want to get stuff done, installed and running, preferabily without having to type code into a black box, without having to take time out of what I want to do to create my own programs to satisfy that.  But it seems as if no one wants that to change, seeing from the responses in this thread.[/QUOTE]

No one? Where is this majority that says they want no more GUI tools? I don't see any. 

Sure some people prefer the CLI, but most want to use a GUI. In many cases we don't have one. We might in a couple years when things are more developed, but for now many tasks are command line only. I think 90%+ percent of Ubuntu will like the GUI tools when they come. I might finally use my broadcom wireless card if a ndiswrapper tools comes down the pipe. I want these thing too. But we don't have them today, and to say anything else is not realistic.

> I think everyone should really, really reconsider where they are trying to go with this.  From the way things are going, I think Linux for the most part should stay for the techinically inclided, because I know friends and family who would give up using computers entirely if this is what they had to deal with, just so that they wouldn't get anymore viruses and the such.

I don't get it. What response did you want? "Its a crying shame we don't have more GUI tools and because you mention it we all are going to start cracking on new ones?" Thats not realistic. Some people do help fix this problem, our third party section has some GUI tools made by users. But there are still many gaps.

Do I wish they weren't there? Sure...but I'm not going to ignore it. I'm not going to lead people on and try to dupe them into not seeing the holes. 

This thread is getting out of hand. People are getting their feelings hurt because they think the community doesn't care for new GUIs. Thats so far from the truth. This thread didn't establish a conspiracy against GUIs. All it did was assess where we are AT THIS POINT IN TIME. We are at a place where we lack many GUI tools. Hopefully Azz is correct and it will get much better soon. I say two releases before the devs and the community fill up the biggest holes. Till then, I'm straight shooting with people when they need help.

---

### Post by poofyhairguy on 2005-06-28
Recently I have been getting some PMs that I ended this thread abruptly. I am posting this as a better explanation of my actions and to get across the point of the thread. 
 
I created this thread because I spend a large amount of time helping new users in the Beginner Forum. Recently I was told that it would be better if I would give directions to do tasks in a GUI along with the usual directions in command form- even if the GUI way is harder to explain and do. I thought about this to myself for a while and I decided personally that this was not the best thing to do- to "shelter" new users from the CLI- because I personally believed that eventually in Linux some CLI use is needed and I thought that I would be wasting my time with a person if all it took was some commands to make them run back to Windows (or OSX, whatever).

But I did not want to make this my official line without some peer review- so I posted a thread to understand my position better. In the course of this thread, I learned that I was wrong. My original position was flawed in the following ways:

1. As Azz pointed out, there might be a chance that some people can get by without using the CLI in Ubuntu if we help them in that goal. Maybe if there was a good graphical howto to explain how to add the extra repositories in synaptic a certain percentage of users might not need to use the CLI. I thought that eventually they would have to....but then I remember some people only have basic requirements when I comes to an OS. For these people I hope to make this guide soon, and I hope once its made it will be linked to when people ask "where is codecs/java."

2. Even if my original conclusion was correct and it is impossible to avoid the command line, I learned that it does take some time to get used to it. A person that I might scare off with a command early on could later be a CLI wizard once they get used to it. I was a little arrogant I guess, so I apologize and I hope to give GUI suggestions when I can.

Of course the command line still has its place and I will probably continue to give out some commands because of the low risk of error (and because sometimes its easier). But this thread showed me that some basic guidelines should be followed. I suggest that if you want to help out that you follow them as well:

1. Try to explain command when you can. Just giving commands teaches the user nothing, but if you explain them then maybe they might like the command line (and Ubuntu) more overall.

2. But sure to actually give the command. Instead of saying "you need to edit this file" say
" enter this command- sudo gedit /place to edit/." Don't assume that users can make original commands early on- more specific info is always better.

3. Give suggestions to fix things in the CLI AND the GUI if possible. Don't lean heavy on the command line if you can't.

All of this was a great learning experience for me (and I hope others). I thank all that participated.

Unfortunately this thread was getting less and less productive. Instead of helping us assess the viability of my hypothesis, some people wanted to turn this into a GUI vs. CLI thread. It seems that a few posters (who must have skimmed the thread instead of reading it) assumed that I was anti-GUI and assumed that the community was not sympathetic to the needs of those that prefer the GUI.  Somehow these posters got the impression that I or the community doesn't want new GUIs to be created, and began to chide Linux users for their OS's lack of GUIs.

That is not a productive or on topic tangent. From the way these posts were written (aka the way they didn't comment on the actual subject) it makes me believe that a few people who were disappointed with the lack of GUIs (for a while now) in Ubuntu saw the title of this thread and decided to voice their complaints despite the fact that these complaints didn't apply here. When we didn't all say "yeah Ubuntu sucks, we refuse to use it until its like XP and everything can be done in a GUI" (or something....I guess I don't know what response they really wanted and I don't really want to find out) these people got bent out of shape. This tangent began to bring down an otherwise productive thread, and I decided to close it so that the thread wouldn't morph into the unofficial place to bitch about the lack of GUIs in Ubuntu.

I'm sorry if I offended anyone in my path to test my hypothesis. I think my answer is more rounded now.

With this long explanation done, I will unlock the thread. If we can get back on topic there is some issues that we can discuss in reasonable terms. For example:

What is the best way to make a GUI guide? What areas of configuration really need GUIs, and what have other Linux's done to fill these gaps? In what areas do CLI command excel, and in what areas do GUI commands excel?

These are all on topic, productive stuff. I swear to God that if people try again to turn this into a "poofyhairguy or Ubuntu VS. GUIs" again I will lock the thread for good and that will be that . THAT IS NOT WHAT THIS THREAD IS ABOUT!!!! Thanks for your patience...it took my a while to write this up...now that I have been very clear I hope that we can continue as adults and discuss the issues at hand.

---

### Post by Takis on 2005-06-28
My turn:
Do we tell people we're helping to use the command line because that's what we're used to? I can't remember the last time I opened Kate, for example, and selected File->Open with the mouse (actually, I remember now, it was back when I started).
It certainly doesn't help that, in many cases, support answers involve editing root-owned files. From here it's a bit of a Catch-22: to avoid using the command-line, you could create an in-line shortcut so that you right-click a file and select "Edit as root" - which would help new Linux users, but at the same time can be understandably seen as a security no-no. How do we get around this? I don't know the best answer.

As a moot point, I seem to remember being told by one of my lecturers that the inventor of the mouse also created a second keyboard to be used in conjunction with it. It consisted of five keys which allowed a combination of 31 (2^5, minus the no-key-pressed combination for slightly obvious reasons) key combinations. This never took off because it was too hard for people to learn a second keyboard, let alone the first. The point is, though, that the mouse was never intended to be a stand-alone tool.

---

### Post by aysiu on 2005-06-28
Thanks for the clarification. I don't *think* I'm one of those people you're talking about, but I definitely misunderstood the original intent of the thread.

I'd say the best way to a guide is to have two columns for every task. Column one is the GUI way to do it. Column two is the CLI way to do it. Sometimes column one might be empty. Other times it might have something in it.

This may also be a good way for people to get to know the command-line, too. If the two (GUI and CLI) are placed side-by-side, people may make easier associations about "Oh, that's what Chmod does" or "That's what sudo gedit means."

---

### Post by aysiu on 2005-06-28
[QUOTE=Takis]My turn:
It certainly doesn't help that, in many cases, support answers involve editing root-owned files. From here it's a bit of a Catch-22: to avoid using the command-line, you could create an in-line shortcut so that you right-click a file and select "Edit as root" - which would help new Linux users, but at the same time can be understandably seen as a security no-no. How do we get around this? I don't know the best answer.
[/quote]
In Knoppix and Mepis (which is Knoppix-based), there's an icon for browse in super-user mode. I can't imagine it would be that difficult (of course, I'm not a programmer, so I wouldn't really know) to create a similar icon in Gnome. Right?

---

### Post by poofyhairguy on 2005-06-28
I'm glad I could clear things up. That was my intention.

[QUOTE=aysiu]
This may also be a good way for people to get to know the command-line, too. If the two (GUI and CLI) are placed side-by-side, people may make easier associations about "Oh, that's what Chmod does" or "That's what sudo gedit means."[/QUOTE]

Columns are hard to do on this forum (I know I have tried) but you point is excellent!! Maybe make the steps the same or something.

And now I always try to tell people when a GUI tools is a wrapper for a command . Such as synaptic and apt-get.

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=aysiu]In Knoppix and Mepis (which is Knoppix-based), there's an icon for browse in super-user mode. I can't imagine it would be that difficult (of course, I'm not a programmer, so I wouldn't really know) to create a similar icon in Gnome. Right?[/QUOTE]

Well...both of those have a root user, something we lack.

The way to make GUI things super user is to preface it with gksudo.

Is it as bad as the command line to tell poeple to put "gksudo something" in the run dialoge box?

---

### Post by aysiu on 2005-06-28
I don't know if it's as "bad" as the command-line. I suspect it isn't. What other choice do we have? I think if the GUI solution's available, that should be presented as an option; otherwise, you do what you can.

---

### Post by aysiu on 2005-06-28
[QUOTE=poofyhairguy]Well...both of those have a root user, something we lack.

The way to make GUI things super user is to preface it with gksudo.
[/QUOTE]

Actually, I just created a new launcher on my Ubuntu panel called "browse as root." I just right-clicked the panel, selected "Add to panel," then "Custom Application Launcher." I put "Browse as Root" as the name and "sudo nautilus" as the command. Of course, whenever I click the launcher, I'm prompted for the password, but that's as it should be.

If users could figure this simple procedure out, it'd make editing files a lot easier for the CLI-fearing. Editing /etc/apt/sources.list would mean simply navigating to there, copy and pasting an icon (for backup) and double-clicking it to get it to open for editing.

Of course, browsing as root... is dangerous--that's kind of the reason Ubuntu wants people to sudo everything, but it's also a lot less intimidating for some people.

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=aysiu]Actually, I just created a new launcher on my Ubuntu panel called "browse as root." I just right-clicked the panel, selected "Add to panel," then "Custom Application Launcher." I put "Browse as Root" as the name and "sudo nautilus" as the command. Of course, whenever I click the launcher, I'm prompted for the password, but that's as it should be.
[/QUOTE]


It should be gksudo....and I tell people to use it all the time....it is dangerous though,

---

### Post by poofyhairguy on 2005-07-04
I was just informed by a community developer the other day that a GUI ndiswrapper tool is being made. No promises it will be in Breezy...but at least someone is working on it.

If we add that tool....I could almost believe that Ubuntu doesn't need the CLI at all (for many people). If we have that tool, there is only one thing we lack.

If any developers are reading this: we need an xorg configuration tool. A way to edit xorg without touching a CLI. Now we have that dpkg-reconfigure deal...but that is no GUI.

SOOOO  many people have xorg problems. People that need to enable nvidia and ATI drivers have to touch the xorg file as it is. If we had an xorg tool that works...then I would say that maybe 50% or more users wouldn't need to touch the command line.

Another GUI tool that would be nice is a FSTAB editing tool. That would be nice for all the people that want to mount a window's partition. But the need for it is nowhere close to the need for an xorg and ndiswrapper tool.

I was very happy to hear about the ndiswrapper tool. As it is now (according to the many Linux related websites I read), Ubuntu is considered to be a medium hard distro. We might never be considered the easiest (distros like MEPIS that don't pay attention to the legalities of including codecs will always be ahead) but we could reach a point where it is as easy as it could be.

I guess that brings up the question- besides what I mentioned...what other GUI tools do we currently lack? What specific tasks?

---

### Post by Kyral on 2005-07-04
Time for my two cents :D

Personally, I love the CLI for most system admin things (editing conf files, moving stuff, etc) And I would ALWAYS prefer using apt-get over Synaptic (hell I removed Synaptic), 'cause I find it MUCH faster to do a "aptS (my alias for apt-cache search) <package>" and then do an "aptI (Guess) <package>"

But then again, I would be completely lost without my GUI. I need things like my GDesklets, my GAIM, my Firefox, my Azureus, etc.

So....the CLI will always be there for me, and the GUI. Its all about a balance :D

---

### Post by aysiu on 2005-07-04
[QUOTE=poofyhairguy]It should be gksudo....and I tell people to use it all the time....it is dangerous though,[/QUOTE] You know, when I type *gksudo* in the terminal, I get this error: "Missing command to run." Is that a program I have to install through Synaptic/apt-get?

---

### Post by codejunkie on 2005-07-05
[QUOTE=aysiu]You know, when I type *gksudo* in the terminal, I get this error: "Missing command to run." Is that a program I have to install through Synaptic/apt-get?[/QUOTE]

because it is a way to launch programs with root privileges not a command to be use separately example: ```
gksudo nautilus
``` opens nautilus file browser with root privileges  or ```
gksudo synaptic
``` opens synaptic package manager so if you just typed ```
gksudo
``` you would get that error because you did not specify the application to run with root privileges.

---

### Post by aysiu on 2005-07-05
How does *gksudo nautilus* differ from *sudo nautilus*? I've been using *sudo nautilus*, and it seems to work fine.

---

### Post by poofyhairguy on 2005-07-05
[QUOTE=aysiu]How does *gksudo nautilus* differ from *sudo nautilus*? I've been using *sudo nautilus*, and it seems to work fine.[/QUOTE]

Using regular sudo with graphic programs (except for gedit for some reason I recently discovered) might mess up your permissions file making it very hard to get back into Gnome after you log out.

I got bit by it...now I only use gksudo nautilus and everything else....

---

### Post by johnistpropaganda on 2005-07-05
An idea I haven't seen mentioned  is pointing begginers to a good book or three (please list some!).  I have found this to be invaluable, along with these forums (which are outstanding btw), and would potentially cut back on the number of reoccuring questions.  The two books I own, which aren't great, cover both GUI topics and command line essentials.

And I'd like to share a mildly interesting experience:
A friend of mine is dedicated Mac user.  When he showed me his new ibook, I decided to open up a terminal and see if it was true that bash commands would work in OSX. I typed the only one I could think of on the spot-"top" and he was amazed. "Dude, thats @#!%in' awsome! Show me more." I didn't know that many commands at the time (and still don't), so I told him to go find a good book on the subject.

Of course there is hardly a need for the CLI in OSX %99.9 of the time, but I have heard it said that to truly become a power user one needs to learn the command line.

Hopefully one day in the not-to-distant future the same will be said of Ubuntu.

Obi John Kinobi

---

### Post by Kvark on 2005-07-05
[QUOTE=aysiu]I'd say the best way to a guide is to have two columns for every task. Column one is the GUI way to do it. Column two is the CLI way to do it. Sometimes column one might be empty. Other times it might have something in it.

This may also be a good way for people to get to know the command-line, too. If the two (GUI and CLI) are placed side-by-side, people may make easier associations about "Oh, that's what Chmod does" or "That's what sudo gedit means."[/QUOTE]

This is a very good suggestion. Even if a new user would always use one of the ways, it is still best to have them both next to eachother. Because they explain eachother. If you see both ways to do it then you learn so much more then by seing one way. **This is a must have for ubuntuguide.org!**

For places where columns are hard to do, like the forum, add them after eachother. like:

> I got a problem!

> You need to do something.

[INDENT][COLOR=Sienna]CLI:[/COLOR]
smtg -dwyl /path/file[/INDENT]

-or-

[INDENT][COLOR=Sienna]GUI:[/COLOR]
menu -> something -> checkbox for opiton[/INDENT]

---

### Post by Sye d'Burns on 2005-07-05
[QUOTE=johnistpropaganda]An idea I haven't seen mentioned  is pointing begginers to a good book or three (please list some!).  I have found this to be invaluable, along with these forums (which are outstanding btw), and would potentially cut back on the number of reoccuring questions.  The two books I own, which aren't great, cover both GUI topics and command line essentials.[/QUOTE]

One of my favorite CLI tutorial sites has to be [LinuxCommand.](http://www.linuxcommand.org/index.php) It gives the CLI in small bite sized chunks. Very handy.

---

### Post by az on 2005-07-05
"OOOO many people have xorg problems. People that need to enable nvidia and ATI drivers have to touch the xorg file as it is. If we had an xorg tool that works...then I would say that maybe 50% or more users wouldn't need to touch the command line.

Another GUI tool that would be nice is a FSTAB editing tool. That would be nice for all the people that want to mount a window's partition. But the need for it is nowhere close to the need for an xorg and ndiswrapper tool."

Most people I know do not care about hardware acceleration.  So, Xorg is properly configured out-of-the-box.  What is not is a bug (like improper color depth or incorrect hardware detection).  As for the ATI acceleration, it is available out-of-the-box on most older ati cards.

The nvidia-glx package is improperly made and should have a debconf option which switches on (nvidia-glx-config enable) acceleration by default (why else would you be installing the package?)  That is a bug.  Perhaps someone with an Nvidia card can file that?
(bugzilla.ubuntu.com)
(yes, I mean you!)

You can add ftab entries when you install by adding the partitions to your partition table and assigning them mountpoints.  You just say "keep existing data".  This functionality is present and adequate, but will probably be better used in a graphical installation environment.  The hooks are there and you can use them already.
So, when you install, you tell the partitioner to add /windows to your fstab and keep existing data....





better than nothing....

---

### Post by aysiu on 2005-07-05
[QUOTE=Kvark]
For places where columns are hard to do, like the forum, add them after eachother. [/QUOTE] I like this idea better than my original columns proposal. Apart from the fact that columns are more difficult to do, they'd also appear rather imbalanced, as the command-line command would probably be one or two lines, whereas the GUI instructions would likely have a number of screenshots and a lot of descriptions. Ideally, the guide would start with the disclaimer, "We have CLI instructions for everything, and--where possible--we've put GUI instructions underneath. We hope that this will help users configure their Ubuntu installation in the way that best suits them, as well as help users understand the relationship between the command-line and the graphical user interface."

---

### Post by super on 2005-07-05
i think the command line is important to learn first. that way every thing will seem easy afterward. besides if your xserver screws up at least you can still get stuff done. thats why i always install command line programs like nano, links, etc just in case.

btw, this is the first time i've heard about that sudo problem with graphical apps, guess its gksudo from now on.

---

### Post by jr0 on 2005-07-08
I didn't have time to read the whole thread.. but I wanted to share some thoughts.

> "i think the command line is important to learn first"
"greens need to get used to the way Linux does things."
"I believe that is part of what seperates windows and linux users."
"All other distros you have to do the same command-line thing too..."


Maybe "the way Linux does things" is what makes it hard for greens to get into ANY distro, or keep them on their desktop?  The CLI is one big example, but there are other things like having to enter a "root" password any time you want to edit a text file or do some basic file managment.  People don't enjoy this. I'm willing to sacrifice security to not be prompted for a password 100 times per session.
AFAIK root accounts barely help anyway since attackers use buffer overruns to execute code when you run a program, after it has permission.  Also, I hope someday we can ditch synaptic and use something like autopackage.

I talk to lots of non-geeks about computers. Linux is still a "cult OS" too "hard to use"... I think these are major reasons.  The problem here is you are asking a bunch of Linux nerds (no offense! ;) ) whether we should abstract away from the CLI.  I know Linux folks swear by it, but you don't see windows users swearing by DOS nearly as much.  For someone switching to Linux, it takes WAY too much effort to learn all those weird commands. Yes friends, it DOES scare them back to windows or mac land.

> 
" I'm saying that regardless of comfort level, copying and pasting a command and hitting enter is easier than cick here, click here, etc."

I disagree fully.

> 
"I'd say Linux without a command-line is a long, long way off"

How so? Why couldn't someone write python or lua programs to command the commandline? If there's a bounty coming I may try it  :) 
In lua of course. 

> 
"I defy anyone to find a way to find an easier graphical tool to do some jobs (such as "list all the files whose name starts with d and have "elete" somewhere in the name")" 
But this example isn't something an average user needs on a regular basis.

...Send the flames...

---

### Post by poptones on 2005-07-08
* I'm willing to sacrifice security to not be prompted for a password 100 times per session.*

then log in as root - and don't complain about how much linux sucks when you blow up your desktop.

*AFAIK root accounts barely help anyway since attackers use buffer overruns to execute code when you run a program, after it has permission.*

Most buffer exploits like this only end with the attacker running at the same permission level as the person who initiated the attack. So if I send you a JPEG and you are running and unpatched libjpeg, my "attack" will only be running with whatever permissions YOU may have. 

Now, if you are logged in as root because you are too lazy to type a passsword a few times when doing administrative stuff...

*Also, I hope someday we can ditch synaptic and use something like autopackage.*

Why? In synaptic I type in a password one time and I can install anything. Is it really so "spooky" to have your computer verify that you actually WANT to change its core functionality? If you take your car to the shop do you want the mechanic to replace the engine without even bothering to ask if you want a new engine or telling you why you need a new engine? What if he decides he wants you to have these cool new tyres.. that only work up to 50MPH...

*I talk to lots of non-geeks about computers. Linux is still a "cult OS" too "hard to use"...*

If these are "non geeks" then they know nothing about computers, only perceptions from the media. I know a housewife near here who cannot get her head around the command line to save her soul, but she uses mandrake and has for a long time - and won't talk of going back to windows. She realizes she's lost when doing command line stuff, but also remembers how equally lost she was having a computer that was constantly sick with infections nad having to "wipe" everything every few months to reload.

* I think these are major reasons. The problem here is you are asking a bunch of Linux nerds (no offense! ) whether we should abstract away from the CLI. I know Linux folks swear by it, but you don't see windows users swearing by DOS nearly as much.*

That's because windows doesn't HAVE a command line. DOS is not like the linux command line in any substantive fashion. You simply cannot get the functionality from the windows command line you can get from linux, because windows applications are all "hidden" from it. In linux I can do nonlinear video editing right from the command line. In windows the best you can do is use the command line to launch a video editor program. 

*For someone switching to Linux, it takes WAY too much effort to learn all those weird commands. Yes friends, it DOES scare them back to windows or mac land.*

Ummm... Macs are now based on a *nix. That means they have command line interfaces as well. I guess you have not seen all those books for MAC users? The ones teaching them how to "tap the power" of that mean and scary command line?

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=azz]
better than nothing....[/QUOTE]

I agree.

---

### Post by jr0 on 2005-07-09
[QUOTE=poptones][i]"too lazy to type a passsword a few times when doing administrative stuff..."[/QUOTE]
Right. "Administrative" as in moving files around or editing a simple text file? No, I call this "everyday use". If I had to say, change video drivers or make sweeping changes to system files I might see the justification. But this is supposed to be MY computer. WTF is up with it asking for passes when I do such basic things? A big turnoff for windows users who BTW never have to enter passwords. 
[QUOTE=poptones][i]"..do you want the mechanic to replace the engine without even bothering to ask if you want a new engine or telling you why you need a new engine?"[/QUOTE]
That's how synapic works! Install one thing, and you end up installing 50 others for it to work. Then you get to manage all those packages.
It could be better.
[QUOTE=poptones][i]"I know a housewife near here...she uses mandrake and has for a long time - and won't talk of going back to windows.."[/QUOTE]
Wow! She's the adventurous type. Too bad she's married, a girl like this is a rare breed. Now lemme guess, her husband is a geek. Or she has a geeky friend who helps her when things go bad. Otherwise she'd have gone back to windows long ago, or to Mac if she likes trying "new things".
[QUOTE=poptones][i]"In windows the best you can do is use the command line to launch a video editor program. "[/QUOTE]
And be more productive since you'll have a more intuitive interface to the task at hand. Don't kid yourself man...things like video editing ARE easier with a GUI. Something's wrong if you disagree there. Do you also edit your 3D models on the commandline? I bet you do. :roll: 
[QUOTE=poptones][i]"Ummm... Macs are now based on a *nix"[/QUOTE]
Of course. And mac continues to kick Linux's ass all over the desktop. Why? Is it because Mac has a more developed GUI, while Linux still relies on the commandline? :-|

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=jr0]Right. "Administrative" as in moving files around or editing a simple text file? No, I call this "everyday use". If I had to say, change video drivers or make sweeping changes to system files I might see the justification. But this is supposed to be MY computer. WTF is up with it asking for passes when I do such basic things? A big turnoff for windows users who BTW never have to enter passwords. [/QUOTE]

Then make a root account and use it all the time. You can. Just please notice that this little "problem" or you part is the reason that Ubuntu is inherently safer than Windows. 90% of Windows security problems stem from the fact that most uses run as an admin all the time. Thats the only reason programs can install themselves and viruses can wreak shop.

This "turnoff" is because the alternative has too big of a trade off. The good multiuser system is THE BEST THING ABOUT DESKTOP LINUX!! 

This is not a behavior Ubuntu will ever emulate (or I'll buy a Mac...I swear it....its uses sudo too....notice how these two desktop platforms lack any spyware).

> That's how synapic works! Install one thing, and you end up installing 50 others for it to work. Then you get to manage all those packages.
It could be better.

A: It manages all the pacakges and dependancies...not you

B: There is no other way to do it in Linux. Unlike Windows or Mac the only common things are the kernels. EXE type things can work because EXEs in Windows assumes a lot of things are there. An EXE (or whatever) in Linux can't assume almost anything- do you use KDE or Gnome or something else? Do you have python or perl or neither installed? Do you have the version of another program needed by this program? An EXE in Linux could assume nothing - it would have to be at least the size of an install CD in order to package everything it might need. The package managers like synaptic make it all work. All autopackage does (or will do successfully) is make package managers easier to use....thats all that will ever be done.

> Wow! She's the adventurous type. Too bad she's married, a girl like this is a rare breed. Now lemme guess, her husband is a geek. Or she has a geeky friend who helps her when things go bad. Otherwise she'd have gone back to windows long ago, or to Mac if she likes trying "new things". 

Nothing wrong with that. I talked my sis into a powerbook after she didn't like Linux. Anything is better than a sudoless OS.

> And be more productive since you'll have a more intuitive interface to the task at hand. Don't kid yourself man...things like video editing ARE easier with a GUI. Something's wrong if you disagree there. Do you also edit your 3D models on the commandline? I bet you do. :roll: 

Not always. What if you need to edit 1000 files all the same way? A command line script is best for that. Use the best tool for the job if you can I say.

> Of course. And mac continues to kick Linux's ass all over the desktop. Why? Is it because Mac has a more developed GUI, while Linux still relies on the commandline? :-|

No...because Mac has a very small platform to develop for. Its like making games on a Gamecube versus making a game for a computer- they know exactly what the hardware is. So its a lot easier for them. OSX would run like crap (or at least as bad as Linux) if it had to run on every Dell in the world.

---

### Post by aysiu on 2005-07-09
[QUOTE=jr0]Right. "Administrative" as in moving files around or editing a simple text file? No, I call this "everyday use".[/quote] What are these "everyday" files you're moving around that require sudo or root privileges? I copy and paste files all the time and edit them without using sudo. The only files I need to edit (when I first install Linux) that need sudo are /etc/apt/sources.list, /etc/fstab, /etc/X11/xorg.conf. Other than that, *once things have been configured* I almost never need to sudo to edit files. What regular files do you need root privileges to edit? Please be specific.

>  That's how synapic works! Install one thing, and you end up installing 50 others for it to work. Then you get to manage all those packages. It could be better. Do you have dial-up? Is that what the problem is?

> Of course. And mac continues to kick Linux's ass all over the desktop. Why? Is it because Mac has a more developed GUI, while Linux still relies on the commandline? :-| Actually, Ubuntu relies on the command-line, and it doesn't even rely on it that heavily (except when you're first installing it). Have you used Mepis? Have you used Linspire? There are distributions out there that require almost no use or knowledge of the command-line at all. These distros are a lot like OS X in this respect. You can rely solely on GUI if you want, but if you want to "tinker under the hood" with some UNIX-like commands, you can do that as well.

---

### Post by poptones on 2005-07-09
> Right. "Administrative" as in moving files around or editing a simple text file? No, I call this "everyday use".

Dude... I can edit "one of those simple text files" and now your computer calls mine every time you log in and sends me your password. with any given windows machine attached to the internet it's all too easy to gain this power with a simple pushbutton attack. You really think it is a liability that a piece of software says "hey, this is a really critical file you are editing and it could screw up your system or compromise your security. Tell me the password so I at least know you are the person who SHOULD be changing this file?"

Again: if you really don't care, log in as root. This is a non-issue because it is so easily overcome. It's a stupid idea, but as you say it's YOUR COMPUTER to screw up - knock yourself out.

> A big turnoff for windows users who BTW never have to enter passwords.

Exactly. This is why we have spam. And why it is so easy for those who trade "illegal material" via p2p and usenet. If it weren't for those millions of easily owned windows machines sitting on phat pipes the internet would be a very, very different place.

> "..do you want the mechanic to replace the engine without even bothering to ask if you want a new engine or telling you why you need a new engine?"

That's how synapic works! Install one thing, and you end up installing 50 others for it to work. Then you get to manage all those packages.

Ummm.. no. I do not "manage all those packages," that's what synaptic is for. I don;t even think about those packages until I have to download them over my dialup connection. 

When I was using win2k, if I had to do a relaod it was easily two days before I could become productive again because **Windows was such a nightmare of dependancies** to install their "visual development tools." Apply this service pack, apply that installer patch - but wait, you can't do that until you install this other library patch. It was a tremendous pain in the ass, and if you have enver experienced this then you have never written code for windows.

Here is how I install the full development package in ubuntu: open synaptic, enter my password ONE TIME and **it resolves the dependanices for me and installs what I asked it to install** If synaptic "could be better" then windows is stuck in the stone age. 

> "I know a housewife near here...she uses mandrake and has for a long time - and won't talk of going back to windows.."

Wow! She's the adventurous type. Too bad she's married, a girl like this is a rare breed. Now lemme guess, her husband is a geek.

Bzzzzt. Her husband is a redneck who would throw the computer in the trash if he could. 

> Or she has a geeky friend who helps her when things go bad.

I installed linux for her. But I am also the one who was called when her windows install was so sickly that the machine couldn't even boot. It's been *months* now since she called me with a problem. 

> "In windows the best you can do is use the command line to launch a video editor program. "

And be more productive since you'll have a more intuitive interface to the task at hand. Don't kid yourself man...things like video editing ARE easier with a GUI. Something's wrong if you disagree there.

Aha! Thanks for taking the bait, my friend. If editing video with premiere is your idea of "productive" then you have obviously never had to deal with a large project. Do you think something like *Fight Club* is put together by a lone editor sitting at a premiere type workstation? Something like Premiere or Kino is fine for wedding videos where you have at most three cameras and the point is just to "remember the event." But with a larger project that type of software quickly proves completely unmanageable.

Being able to edit video from the command line means I can use all the tools at my disposal - grep, sed, awk, xml parsers and python and convert and layer and all those other tools that make linux so powerful. *Natural Born Killers* was a remarkable film at the time because of the massive number of edits. That was a decade ago now, and things haven't become any more subtle in Hollywood films. Care to guess what platform and what software most production houses use now for this sort of thing?

Editing a large production is done by cut sheets - textual timelines. It's how the pros do it. Those cut sheets may be generated by premiere type ionterfaces or they may not. When I want to make sure I get *this frame like this* and *that frame like that* I don't reach for a mouse - neither does anyone else who knows what they are doing.

> Do you also edit your 3D models on the commandline? I bet you do.

Ayup, I sure have. And why not? Those models are just big text files. Sed and awk and grep and eval - that's what they are for. When you want to do it the way everyone else does it you use the "easy" tools; when you want to do something no one else has done, *the only way to do it* is to head for the command line. 

> Of course. And mac continues to kick Linux's ass all over the desktop.

Obviously... you haven't  visited Hollywood in, like, five years... or ever?

---

### Post by jr0 on 2005-07-09
> "Then make a root account and use it all the time. You can."
I missed that part of my installation!  Linux is already inherently safer than windows since all the trojans and viri made for windows won't run. We also have antivirus products for Linux cropping up.

> "...multiuser system is THE BEST THING ABOUT DESKTOP LINUX!! "
Not for everyone. The interface is much more important than user managment. What good is it to be able to handle infinate users, when you're the only one who knows how to use the frickin' thing?! ;)

> "What are these "everyday" files you're moving around that require sudo or root privileges?" 
My grub backround. A simple .XPM image could not be copied from my home directory to boot/grub without me entering a password. I had to use the beloved commandline to actually get it done.

> Have you used Linspire? There are distributions out there that require almost no use or knowledge of the command-line at all. "
I tried them all (I'm on cable ) Ubuntu is the easiest. For me that is. I'm not saying Linux is terrible or I can't do work in Linux. I use it just fine. I just wouldn't recommend it to anyone as a replacement for windows, in any of it's current incarnations. 

> Dude... I can edit "one of those simple text files" and now your computer calls mine every time you log in and sends me your password.
Really? Somehow I doubt this. You're probably right though.. spam, p2p, usenet all stems from bad security in windows, and everyone running w1nd0wz is under control by l33t hackers. 

> "...I do not "manage all those packages," that's what synaptic is for"
What if a package is insecure? What if someone hacked my synaptic, or the update lists, to make it download all kinds of malware? How can I trust this thing that's always downloading odd files from the internet?

> "you have never written code for windows."
Oh I have, and I do. But I use GNU. I just unzip and go. It's free too! If you organize you're files and drivers you can be productive in hours after an install, not days. You just made me even happier not to use M$ software development products.  :-P 

>  "Aha! Thanks for taking the bait, my friend."
Ok, so you have you're gig going and find yourself more productive using a patchwork of odd programs and scripts. I don't think you can honestly speak for every user or studio for that matter. Besides, we aren't talking about removing the commandline entirely here. Just making it's power accessible for desktop users (people scared of a CLI).

> "I installed linux for her. "
Ha! Got ya. Why do rednecks get all the chicks!?

> "Ayup, I sure have. And why not? "
Man I hope you're kidding about the 3D. If not then damn...
You win the true geek award. From me to you  :wink: 

I must be confused. I thought Ubuntu was supposed to be "Linux for human beings", trying to bring "humanity to others" by making Linux actually useable by the everyman. I guess some people have different views... At this rate, I can just see the kids in Edubuntu class now "ok now jessie, type sudo su !oh wait! now enter the root password. Nope try again.. you do want to be able to save that text file, don't you?" "Next we're going to learn how to edit videos from the wonderful command line. Isn't this exciting, kids?!"  Hmmmm....

---

### Post by poptones on 2005-07-09
> Dude... I can edit "one of those simple text files" and now your computer calls mine every time you log in and sends me your password.

Really? Somehow I doubt this.

Then you **really** need to get some education before you are in a position to offer a meaningful critique of this stuff. I'm not telling you this to insult you and I damn sure have nothing to prove, but the arguments you are making are a bit.. uninformed. It reminds me of the story Charles Nelson Riley once told on a talk show about his terrible experience with a Mercedes. He had never had a car and didn't realize the need to put oil in the engine. You can imagine how the story ended.

*You're probably right though.. spam, p2p, usenet all stems from bad security in windows, and everyone running w1nd0wz is under control by l33t hackers.*

Actually, they are if they are not well protected. And that doesn't just mean by Norton and such. I have worked phone support, I have had people tell me about their computer that stays on 24/7 and connected to their cox cable account, and how it was getting worse and worse and then one day "poof" it magically fixed itself! I've actually had that sort of story relayed to me more than once.

Do you believe their computer fixed itself? A geek had stumbled upon their very vulnerable machine while looking for well connected machines to root for a proxy network, and wanted to make sure that machine stayed well connected. It's in **their interest** to keep such machines running too, you know - if a well connected and otherwise reliable machine becomes so bogged down it is unusable, that's one less proxy on their list.

Laugh all you like, it happens. Here's just one snippet of proof from a well known perl "guru." This is from a letter Chip Salzenberg sent to his boss, a client company called "Health Market Science."

> It has recently come to my attention that that HMS is continuing the illegal and immoral web harvesting operation that I brought to Rich Ferris's attention over a month ago, in a conversation including Tim McCune. HMS's continued harvesting operations are a threat to me legally, morally, and professionally. 

That HMS systematically collects data from web sites without the express permission of their owners is well known (inside HMS). Some web site operators are not pleased when (if) they figure out that their sites are being harvested. They sometimes respond by blocking the network addresses of the harvesting machines. This was a common problem in harvesting when I hired on to HMS in December of 2002. At that time, the accepted strategy for getting around such blocks was to obtain multiple web hosting accounts to act as proxies for HMS's harvesting systems. I did not then realize that knowingly bypassing blocks placed by web server operators was illegal. (As a result of other research, detailed below, I now know that has been illegal all along.)

As bad as HMS's past harvesting practice was, current practice is worse ... much worse. HMS has taken **a page from the spammer playbook** and is, deliberately and under management direction, **hijacking thousands of vulnerable machines all over the Internet, using them and their network bandwidth without the knowledge or permission of their owners as unwitting accomplices in HMS's data harvesting operation.**

I have confirmed these facts in conversations with several people with first-hand
knowledge, including Tim McCune and John Marquart. I asked Tim McCune about
HMS's proxy hijacking in the presence of Rich Ferris, a vice president of HMS and a
company founder. In that conversation, Tim McCune confirmed to Rich Ferris and me that proxy hijacking was standard practice. Shocked, I informed Tim and Rich that proxy hijacking is very illegal and immoral. They were unmoved. I also have witnesses for other conversations.


[And here's how such things can end](http://geeksunite.net/). 

No, wait.. it hasn't ended yet. That's really how bad it gets just at the start.

> "...I do not "manage all those packages," that's what synaptic is for"

What if a package is insecure? What if someone hacked my synaptic, or the update lists, to make it download all kinds of malware? How can I trust this thing that's always downloading odd files from the internet?

For one, you don't log in as root all the time. 

Which side of this are you on? Just yesterday you were bitching about all the security built into the desktop that gets in your way. **You said** you would give up security for convenience. And now you're worried about a system level app that is, in any reasonable system, protected via password?

That text file I mentioned? There's one simple example on [this wiki page](https://wiki.ubuntu.com/EncryptedFilesystemHowto). if you're using windows I don't even need to edit a text file. All I need to do is get **you** to click on an activex control that installs my own spyhook.dll. Now I can not only eavesdrop on your traffic, I can initiate connections, force downloads - whatever.

How do you know you can trust synaptic? Read that article on the wiki about securing your system with cryptography. There's a script there (I need to update) that will scour your system and generate an MD5 hash of every single system file. Schedule it to run every night and you'll get a report on every single file it finds altered.

---

### Post by jr0 on 2005-07-09
[QUOTE=poptones]"Which side of this are you on? Just yesterday you were bitching about all the security..[/QUOTE]
My point is that it's hard to put trust in what you don't understand. A new user has no idea what the 50 dependancies are that are being downloaded, where exactly they are downloading from, or if it's really secure. It's stupid to lock text files when he has to download tons of obscure files.  At least with windows we go to the developers site, grab an installer, and can usually install and run the program usually without needing to download "extras". No passes, and we know where we got the file(s). It feels like you have more control.

[QUOTE=poptones]"Then you really need to get some education before you are in a position to offer a meaningful critique of this stuff."[/QUOTE] I know enough thanks. You're lucky someone like me has the balls to come here and tell you this stuff instead of blindly agreeing with everything the community says.  I hope more people will be blunt about what sucks about Linux, so people can start fixing it.  :-| 

" ...bla bla... I will hack you with activex"
Trust me I worry about viruses. Just maybe not as much as some people. I plug holes and update what I can, and leave it at that. I don't lose sleep over it. One of the first things I block is activeX though.. come on now. :roll:  Anyway, if a true hacker wants in...nothing I can do will stop him and I accept this fact of life. 

Now can we bring this back on topic, plz ?

---

### Post by Leif on 2005-07-09
[QUOTE=jr0]
 I know enough thanks. You're lucky someone like me has the balls to come here and tell you this stuff instead of blindly agreeing with everything the community says.  I hope more people will be blunt about what sucks about Linux, so people can start fixing it.  :-| 
[/QUOTE]

Look, I'm going to put this simply : security will never go away. This is a good thing, even if you feel it is in the horribly arrogant I know what's best for you way. As others have said, go and login as root, but don't expect everyone else's security to be switched off by default because you had to type in your password to change the grub background, which of course we all do 20 times a day so the time saved is way worth it.

As for the having balls to complain... wow, bravo, because none of us have ever offered criticism. We all just mumble and nod our heads. You realize these are user forums right ? Not bugzilla. You want fixing, talk to developers, or better yet, do it yourself. 

[QUOTE=jr0]Anyway, if a true hacker wants in...nothing I can do will stop him and I accept this fact of life. [/QUOTE]

That's the best example of bad logic I've seen in a while ! Oooh, if a true thief wants to get into my door/car, he will, so I might just as well leave the door open.

---

### Post by brim4brim on 2005-07-09
[QUOTE=jr0]My point is that it's hard to put trust in what you don't understand. A new user has no idea what the 50 dependancies are that are being downloaded, where exactly they are downloading from, or if it's really secure. It's stupid to lock text files when he has to download tons of obscure files.  At least with windows we go to the developers site, grab an installer, and can usually install and run the program usually without needing to download "extras". No passes, and we know where we got the file(s). It feels like you have more control.

 I know enough thanks. You're lucky someone like me has the balls to come here and tell you this stuff instead of blindly agreeing with everything the community says.  I hope more people will be blunt about what sucks about Linux, so people can start fixing it.  :-| 

" ...bla bla... I will hack you with activex"
Trust me I worry about viruses. Just maybe not as much as some people. I plug holes and update what I can, and leave it at that. I don't lose sleep over it. One of the first things I block is activeX though.. come on now. :roll:  Anyway, if a true hacker wants in...nothing I can do will stop him and I accept this fact of life. 

Now can we bring this back on topic, plz ?[/QUOTE]
 To the guy who keeps saying he wants to use windows because it doesn't have to type root password everytime he does something.

Longhorn the new windows OS is taking this feature from Linux to make the new windows more secure.  They will also be using Unix like permissions!  Ms has realised that what they did was a security error and is the reason they have so many attacks from worms and such programs.

I think that a lot of Linux users including myself aren't aware beforehand if synaptic is overwriting or uninstalling libraries if it's entirely safe to proceed and if there is a way to find out what programs on a users system are currently using the packages that are about to be overwritten or uninstalled it would be very useful.  As far as I'm aware this is how synaptic works and when I see the following libraries will be uninstalled I'm not exactly sure it's safe to continue.

Also for installing nVidia and ATI drivers I thought they had pretty much eliminated the command line except for editing one of the config files to point to the new drivers and that this more of a distro dependant thing is it not which is why they can't make an entirely GUI installer.

Now to get back to does Ubuntu need GUI instructions for users the answer I believe is yes but not at the moment.  At the moment Ubuntu won't attract that audience so the current instructions are good enough and I've learned more about the command line using Ubuntu than any other distro I've tried because they are generally so command line dependant that with vague instructions that I give up and Ubuntus step by step guides work and give an idea of how the system works.

Also if GUI tools exist walkthroughs are generally not required because Gnome is pretty intuitive so users will generally find the options at the moment if they are there.  An example is adding extra sources to Synaptics which I worked out how to do on my own because it just made sense for the option to be there in Synaptic.  I didn't find it at first and checked Synaptics help and it says it somewhere in there about adding sources.  Users find the GUI option if it's there.  Command Line walkthroughs work for the moment providing they give a step by step instruction to the point where a user can just copy and paste without thinking if they so wish.  Users generally learn as they go but some just don't want to and want to get it working and that's it.

At the momen I think drivers, hardware problems in general and software not in synaptic is the only reason users use the command line and while here I'd like to suggest a program for make file programs where you can select the source directory and select where you want to install it and click the install button and the program should build and install it automatically and collect any needed libraries from Synaptic as neccessary.  If libraries required are not found in Synaptic then an error should be given to users asking them to download such and such a package or maybe a call back to Ubuntu so they know the library is needed by users.

As for drivers this is more the hardware manufacturers problem in that they don't provide drivers for Linux.  If they do sometimes there are errors and in this case the command line is okay because in windows you sometimes find that you have to go edit files aswell in hardware problems or just download the latest drivers.  There needs to be a way to install drivers without having to use command line similar to the .run packages ATI and nVidia drivers come in as that's pretty much perfect and I think more programs in general should be moving to the .run or firefox like installers.  Saying the open sourced programmers don't have the resources to put into making installers or GUI's  is crap in my opinion as there are thousands of programs for windows doing it right now that are free and made in spare time by individuals.  If there was an open source installer (I don't know if there is already) that allows you to just tell it where to install the files and thats it and to ask for root permissions if neccessary (e.g provide the password box).  Ubuntu can't really stop third party software from depending on the command line though.  As for user interface controls over command line, it takes maybe five to ten minutes to setup a user interface using the drag and drop tools so it's more of a it'll do attitude rather than the tools not existing or a time constraint for a project.

Anyway those are my opinions as a new comer to Linux and Ubuntu is the first Linux I've kept for so long and the one I've learnt most about the command line from.  One more thing though.  I've used Suse and Yast and personally see little that it offers that Ubuntu is missing although I could just be missing something.  Ubuntu also has the best hardware support I've ever come across in a Linux distribution and I've tried Novell's desktop Linux as I presumed it would have good hardware support but it detected virtually none of my Dell Latitude's D810 hardware.  Also tried Mepis but said it couldn't detect my CD Rom drive for some reason even though it read from it to start the installer then told me it couldn't detect it.  Anyway thanks to everyone working on the Ubuntu project and keep up the good work as this is by far the best Linux distribution I've tried.

---

### Post by poptones on 2005-07-09
> My point is that it's hard to put trust in what you don't understand.

And it's pretty obvious you don't understand much of either linux or windows. You make inconsistent arguments about "security" while talking up windows, then end it all with a shrug of the shoulders "oh well I am gonna get ow|/|zored anyway so what's the diff?"

> A new user has no idea what the 50 dependancies are that are being downloaded, where exactly they are downloading from, or if it's really secure.

Nor do they when they go to c|net and download crapware riddled with spies. if they did, they wouldn't do it. This is not a linux problem, it's an education problem. 

> It's stupid to lock text files when he has to download tons of obscure files.

No. You still do not seem to get that those TEXT FILES CONTROL YOUR SYSTEM. Linux is based on unix, and unix was "invented" on the notion that everything is text. A great many of the *features* of your system are provided via text files - perl and bash and python scripts. Alter one of them and you alter the core functionality of the machine.

> At least with windows we go to the developers site, grab an installer, and can usually install and run the program usually without needing to download "extras".

Only if you happen to be running the latest OS with the latest service pack and all the most recent patches. Otherwise you may very well be back in the boat with the rest trying to resolve some poorl documented dependancy. Only in windows you don't have a package manager to help you with this... it's google, the neighborhood geek, or give it up.

> No passes, and we know where we got the file(s). It feels like you have more control.

It's a complete illusion. If you are using windows **you have no control. Microsoft has control**. 

> I know enough thanks. You're lucky someone like me has the balls to come here and tell you this stuff

What 'stuff?" You think ANYTHING you said has not been raised 100 times before? Dude, it's ignorance. Sorry, but that's really all it comes down to. There has to be some way to secure a machine. This is no longer an option. If you think it is too much to expect that a user "confirm" before altering their machine, fine - let them run windows. But don't think the windows you run in five years is going to be like the one you are running now. The government simply will not allow it. Yes, I am saying the government will stop it. Right now Microsoft is doing a good job of blaming the bad guys for all this, but it's a cold hard fact all those vulnerable machines are enabling the easy distribution of copyrighted films and music, and hollywood won't have that. They are enabling the distribution of all sorts of pornography the church ladies won't tolerate, and that means folks like the good congressman from Florida are going to be beating down the doors in Redmond if this problem isn't fixed, and soon. That's what Lonhhorn and TCPA and all that other crap is about: plug up the holes Microsot created with Millions of machines running an operating system that wasn't even designed to be used on a network. 

You think it's too much trouble to type in your password when you want to add a program? Fine - run Longhorn when it comes out and let the two Washingtons **dictate for you** what your computer is *allowed* to do. Let's see how much you feel that security getting in your way when you can't even visit a webpage without first sticking a quarter in the slot.

---

### Post by poptones on 2005-07-09
> Users find the GUI option if it's there. Command Line walkthroughs work for the moment providing they give a step by step instruction to the point where a user can just copy and paste without thinking if they so wish. Users generally learn as they go but some just don't want to and want to get it working and that's it.

Actually, MOST of the stuff that is listed here as "step by step" so anyone could follow cut and paste could ALSO be done with scripts. Some of us have been working on this. Then you could just download the script, press return and let fly. In the case of things liek adding package repositories to synaptic, that could even be done from a weblink. But these things take time. right now ubuntu doesn't even have one of those smily happy GUI installers and I suspect you would agree that's a lot more important to making a good first impression than making it "click and run easy" to add a foreign repository to synaptic or encrypting your file system.

> At the momen I think drivers, hardware problems in general and software not in synaptic is the only reason users use the command line and while here I'd like to suggest a program for make file programs where you can select the source directory and select where you want to install it and click the install button and the program should build and install it automatically and collect any needed libraries from Synaptic as neccessary.

Here's the thing: much of that software isn't yet ready for prime time. I'm not saying this about ALL of it, but you have to remember this is a single point of distribution for a LOT of software. it takes manpower to compile all that software into the proper packages and set it up on the server. Think of that as a first step in the "filter" process: if it's not on the server, then it's not ready to be supported. There is just as much windows software like this, it's just slightly easier to distribute unfinished crap because the point and click microsoft tools make it easy to wrap up a dozen libraries in a single EXE. What efect that program is going to have on your system or your data is another matter. 

I do agree with you about the "these things will be removed." there needs to be a lot more detail paid t that because it does look scary, and you can hose certain features if you are not careful. Try to get rid of evolution server, for example, and you will end up with no desktop at all.. not a good thing. But if it is replacing evolution server and all the desktop files, then the old ones HAVE to be removed. Right now the system doesn't do a good enough job of figuring out what will be "lost" and what will simply be "replaced." It definitely needs to be better.

But before anyone jumps in about "that's why windows is better" consider this: those zip installers will happily **overwrite** your system files, and the actual *installers* have scripting capabilities that will also allow removal of files without replacement. And they aren't even required to tell you before doing it.

> Saying the open sourced programmers don't have the resources to put into making installers or GUI's is crap in my opinion as there are thousands of programs for windows doing it right now that are free and made in spare time by individuals. If there was an open source installer (I don't know if there is already) that allows you to just tell it where to install the files and thats it and to ask for root permissions if neccessary (e.g provide the password box).

You just described synaptic. That's what it does. It's built in already.

If you've ever been infected with several virii and called MS for support, I guarantee you have seen plenty of that command line. I have spoken with clients who had spent HOURS on the phone (some calls four hours or more!) while the technican walked them trough typing this and doing that, installing dlls and stripping out text from files and all sorts of crap when they could have just reinstalled windows from the ground up in the same amount of time. With linux it;'s even easier; I just keep a backup of my deb cache so I don't have to download 200MB of stuff again if I need to reload. It might take an hour to remember all the stuff I need after a reload, but with ubuntu you can be back up and running after a "major event" pretty quickly. Not that most folks will ever need to...

---

### Post by brim4brim on 2005-07-09
[QUOTE=poptones]Actually, MOST of the stuff that is listed here as "step by step" so anyone could follow cut and paste could ALSO be done with scripts. Some of us have been working on this. Then you could just download the script, press return and let fly. In the case of things liek adding package repositories to synaptic, that could even be done from a weblink. But these things take time. right now ubuntu doesn't even have one of those smily happy GUI installers and I suspect you would agree that's a lot more important to making a good first impression than making it "click and run easy" to add a foreign repository to synaptic or encrypting your file system.
[/QUOTE]

Well thats cool but what I'm saying is most of Ubuntu's users are willing to learn command line and most want to learn and this copy and paste allows us to see whats going on.  I agree that the tool your developing is much needed and will make my life easier and I look forward to it but I also think the main advantage of it will be to attract a less techy audience for Linux  which is where I think Ubuntu is trying to head and is where I'd like to see Linux head while sticking to it's open source and freely distributed roots which is why I choose Ubuntu and recommend Ubuntu to everyone who asks to try Linux.

> 
Here's the thing: much of that software isn't yet ready for prime time. I'm not saying this about ALL of it, but you have to remember this is a single point of distribution for a LOT of software. it takes manpower to compile all that software into the proper packages and set it up on the server. Think of that as a first step in the "filter" process: if it's not on the server, then it's not ready to be supported. There is just as much windows software like this, it's just slightly easier to distribute unfinished crap because the point and click microsoft tools make it easy to wrap up a dozen libraries in a single EXE. What efect that program is going to have on your system or your data is another matter. 


Okay I knew that was the general idea of Synaptic but I kinda like messing with other programs and I guess that anyone willing to do that is also willing to learn how to install using the command line which I've been doing aswell.  Your right about all the important and I suppose polished open source software is in Synaptic except Real Player for the reason that they won't let ye as I understand it.  I just finished installing it now and it wasn't the most fun I've ever had.  ](*,) 

> 
I do agree with you about the "these things will be removed." there needs to be a lot more detail paid t that because it does look scary, and you can hose certain features if you are not careful. Try to get rid of evolution server, for example, and you will end up with no desktop at all.. not a good thing. But if it is replacing evolution server and all the desktop files, then the old ones HAVE to be removed. Right now the system doesn't do a good enough job of figuring out what will be "lost" and what will simply be "replaced." It definitely needs to be better.

But before anyone jumps in about "that's why windows is better" consider this: those zip installers will happily **overwrite** your system files, and the actual *installers* have scripting capabilities that will also allow removal of files without replacement. And they aren't even required to tell you before doing it.


Well I'm glad ye are aware of the issue because in other Linux distro's I have actually disabled my front end unknowingly while installing a third party app that I didn't think would touch anything near the front end for the OS let alone completely disable it.  I havn't had any problems with Ubuntu yet but I can understand how it could turn other people off.  I've kinda started to get used to what libraries are important to the core of the OS and Gnome which makes me feel a lot safer about using the package manager.

Well anyway overall it seems you've got the plans to put it together for the future and I think we've answered the topic starters question that it's okay for the moment but that your tool that will allow automating the current step by step process guides is pretty much the future solution in helping users without making them use the command line or having people describe how to do it via GUI interface because I've had to do that with users and screen grab of lotus notes, go into paint paste, cut the part I wanted, high light the option they need to use and then paste it back into an email and send it to them isn't fun and seeing as this entire service is free I wouldn't expect them to do it and I hope the new tool works aswell as you've described.

---

### Post by N'Jal on 2005-07-09
Well a GUI installer will be featured in Breezy, so we are getting there.

>  I know enough thanks. You're lucky someone like me has the balls to come here and tell you this stuff 

You want ball's? Go away and come back once you have learned something, i don't think im the only one who doesn't actually know what point your trying to make. To me you come accross as rather arragant and ignorant, and your arguments do not help this discussion. If you have a valid point please make it more clear.

---

### Post by jr0 on 2005-07-09
> "because none of us have ever offered criticism. "
This is for you too N'jal. Most of you aren't new to Linux.  You haven't just switched over from Windows and you aren't having the experience most newbies will.  Things you overlook as "how Linux works" may be the things that make desktop users not even want to try Linux.  You're attitudes don't help people feel welcome to this wonder filled community. Linux for all, except if you offer advice on improving it that doesn't jibe with the elistists.  

My original point was, the command line does in fact scare off would-be new users. The FAQ does help, but it's not enough, and this is not the only thing scaring people off. 

> "At the moment Ubuntu won't attract that audience"
It's being touted as "Linux for humans", "the desktop Linux". From what I hear, no distro has ever recieved this attention.  Do we want to live up to this hype? Or should you change the name and slogan to something more fitting?

> "If you think it is too much to expect that a user "confirm" before altering their machine, fine - let them run windows. "
Maybe that's one reason they ARE? Maybe they want to be able to do whatever they want on their machine, without it holding them back?  There must be ways to keep the same security and reduce the hassle on the user.

> "Dude, it's ignorance"
On whose part? Seasoned Linux geeks, or newbies? If these things "have been raised 1000's of times". What's the old saying, lots of people can't be wrong.

> "And it's pretty obvious you don't understand much of either linux or windows." I'm talking about every new user, not just myself. THEY may not trust synaptic. THEY won't want to enter passes to do basic things.  In home systems I work on (because yes, I'm qualified to work on them) I never see multiple user accounts for Windows. Everyone wants to be a "root" user.  I think some of you are still in server land where we have to manage 1000 accounts. Not so on the desktop.

> "Only in windows you don't have a package manager to help you with this." "those zip installers will happily overwrite your system files"
There are rarely times when a program has unresolved dependancies in windows, and developers usually list them on their site.  Only poorly designed apps, hacker apps, or Microsoft's apps ever overwrite system files.  Most are self contained in a Program Files folder and get a Control Panel->Add or Remove Programs entry.  For someone who bashes people about lacking knowledge, you could do with some yourself my boy.

> "Synaptic" 
Not everything I need is in Synaptic, and not always the version I need. What do I do then? I like where autopackage is going. It can hopefully reduce that someday.

---

### Post by N'Jal on 2005-07-09
> Most of you aren't new to Linux.

I am, i just followed the learning curve, i don't claim to be an uber geek cos simply im not one. I've not even been using linux systems for much over a year.

Frankly i am doing my bit, i am a member of the doc's team, actually working on the command line part of it, this is where i am learning, i am also learning C, to perhaps further development of programs when i get good enough, but it's easy to say I have balls because i suggested this, go out and make a difference, you didn't see bob geldof say go organize a concert... he did it himself and look he made a difference, perhaps you will, so stand up and be counted don't just sit around telling people what to do.

Lead by example

---

### Post by aysiu on 2005-07-09
I, too, am new to Linux. I just come with an attitude ready to learn something.

And I still haven't heard valid critiques of Linspire or Mepis from Jr0. I happen to like Ubuntu better, but if you want to get away from the commandline and go full GUI, there are Linux options in that area.

And the splash.xpm.gz file is not an "everyday" file. Are you able to edit the Windows boot splash screen without administrator privileges? Do you even know how to edit the Windows boot splash screen?

---

### Post by garnertr on 2005-07-09
PoofyhairGuy,

When I see your icon in the messages, I know that your about to give useful information.

Myself, I could care less HOW the information is presented.  I think we are getting hung up on the idea of GUI and/or Command Line and that either one is the ONLY way to go and if your not using it then you are wrong and/or a dweeb...

Myself, I'd like to learn more of the command line; I find the screen shots w/ the command line instructions very useful and helpful, after all, I cannot messup something as simple as "uname" or "apt-get install xyz".

From my own observations, Linux ppl are so hung up on their world of this is the only way to do it, anything else is windows and therefore bad; which is not true (IMHO).

So, keep up the GREAT WORK, I look forward to your postings, keep them up, I'm learning from you; maybe I should say thank you more often, but I don't, but just so you know, this person THANKS YOU for your efforts!

---

### Post by garnertr on 2005-07-09
[QUOTE=Kyral]Time for my two cents :D

Personally, I love the CLI for most system admin things (editing conf files, moving stuff, etc) And I would ALWAYS prefer using apt-get over Synaptic (hell I removed Synaptic), 'cause I find it MUCH faster to do a "aptS (my alias for apt-cache search) <package>" and then do an "aptI (Guess) <package>"

But then again, I would be completely lost without my GUI. I need things like my GDesklets, my GAIM, my Firefox, my Azureus, etc.

So....the CLI will always be there for me, and the GUI. Its all about a balance :D[/QUOTE]


Kyral,

Great post, can you amplify how you got rid of Synapic and how you made an alias and such in GUI...

This is interesting and I'd like to learn more! :)

---

### Post by jr0 on 2005-07-09
Why do I need to critique Linspire or Mepis? Suddenly people value my opinion?  :???: I don't like either, and one is non-free.  No other distro calls itself "Linux for humans". I want to see Ubuntu/Kubuntu/Edubuntu live up to that.

[QUOTE=N'Jal]Lead by example[/QUOTE]
Ok, maybe I will! How do I get involved? Should I just start hacking up some GUI apps? But there's a problem, I hate python. If I could get Motif installed I'd be able to use the iup project from lua to make GUI apps very quickly.  I have a nice iup framework already in place. I tried to install Motif, but synaptic installs the wrong version (and there's no choice!) while openmotif is broken. Fox GUI toolkit might work, I haven't tried it.  There's also lua-Qt somewhere but I haven't tried this either. 

I just don't want to waste time on this if it won't be used... I do have other things I could/should be doing.  But I'd like to help Ubuntu become more approachable for the newbies (since nobody else wants to :roll: ).

---

### Post by aysiu on 2005-07-09
[QUOTE=jr0]Why do I need to critique Linspire or Mepis? Suddenly people value my opinion?  :???: I don't like either, and one is non-free.  No other distro calls itself "Linux for humans". I want to see Ubuntu/Kubuntu/Edubuntu live up to that.[/quote] Because you said this before: > I tried them all (I'm on cable ) Ubuntu is the easiest. For me that is. I'm not saying Linux is terrible or I can't do work in Linux. I use it just fine. I just wouldn't recommend it to anyone as a replacement for windows, in any of it's current incarnations. If you  say Linux isn't a good replacement for Windows in *any* of its current incarnations, you should be specific about why. I don't have to "value your opinion" to want to at least know why you have your opinions. Saying "I don't like either" isn't being specific. I happen to believe Linux *is* a good replacement for Windows, given certain assumptions: 1. people who allow large companies to pre-configure and pre-install Windows be forgiving of the fact that Linux, like any operating system, needs installing and needs configuring; and 2. people aren't using Windows-specific programs (yes, they do exist).

If someone just wants to check email, surf the internet, and do the occasional word processing, she or he would be perfectly fine with Linux as long as someone sets it up. And Windows *is* set up, whether you see the set up or not. Windows does not "just work" out of the box--I'm speaking as someone who actually has reinstalled Windows after having lost my "drivers and utilities" CD.

---

### Post by TravisNewman on 2005-07-09
jr0-- it's touted as Linux for Human Beings, it's touted as desktop Linux, but it's never touted as Linux with no learning curve. Imagine using a mac for years and switching to windows, or using linux for years and switching to windows, etc, etc. There will always be a learning curve, and different ways things will function.

---

### Post by jr0 on 2005-07-09
[QUOTE=aysiu]you should be specific about why.[/QUOTE]
I gave my reasons. The reliance on the CLI. The focus on multiuser security, even where there is just one user. Package managment.  I couldn't tell my sister to use Linux with a straight face. She can use windows just fine though. I might get her a Mac for christmas.

> "operating system, needs installing and needs configuring" 
"If someone just wants to check email, surf the internet, and do the occasional word processing, she or he would be perfectly fine with Linux as long as someone sets it up." But Linux, even Ubuntu takes a considerable amount of setting up to get close to the functionality you find in Windows/Mac. When something needs to be fixed/installed/upgraded someone always suggests the command line because that's currently the only way to do some things.  Human beings don't use alien commandline calls and won't want to leave the comfort of a GUI behind for a CLI.  :-|

---

### Post by aysiu on 2005-07-09
[QUOTE=jr0]I gave my reasons. The reliance on the CLI. The focus on multiuser security, even where there is just one user. Package managment.  I couldn't tell my sister to use Linux with a straight face. She can use windows just fine though. I might get her a Mac for christmas.[/QUOTE] I've never had to use the CLI in Mepis, not even to enable extra repositories, not even to browse as root (within my user account). And Linspire's default (even on its latest 5.0 release) is to make you one user, who is administrator (just like Windows). 

Still haven't heard any valid critiques of Linspire or Mepis. I recommend Mepis to everyone who's afraid of cutting and pasting some commands. To everyone else, I recommend Ubuntu. Sure, Linux isn't for everyone, but neither is Mac or Windows.

---

### Post by N'Jal on 2005-07-09
> Ok, maybe I will! How do I get involved? Should I just start hacking up some GUI apps? But there's a problem, I hate python. If I could get Motif installed I'd be able to use the iup project from lua to make GUI apps very quickly. I have a nice iup framework already in place. I tried to install Motif, but synaptic installs the wrong version (and there's no choice!) while openmotif is broken. Fox GUI toolkit might work, I haven't tried it. There's also lua-Qt somewhere but I haven't tried this either.

I'd suggest rolling your own... but that's a command line thing...*shrugs*

OR

Try another distro that has the laset versions

OR

Work with your chosen project to port the latest versions

OR

Use Windows/Mac/SkyOS (though i wouldn't reccomend the latter yet, it's still beta)

OR

Learn a new language/IDE (My first language was MS Visual BASIC, im now learning C)

Or

Work with the autopackage guy's to port it, i find autopackage to be very good

There's a few things for you to try.

> I do have other things I could/should be doing
Don't we all?

---

### Post by jr0 on 2005-07-09
[QUOTE=aysiu]Linspire's default (even on its latest 5.0 release) is to make you one user, who is administrator (just like Windows). [/QUOTE] Really? I didn't notice. I found it annoying to use. Did I mention it's not free? That you have to pay a subscription fee to download packages? No thanks.

> I recommend Mepis to everyone who's afraid of cutting and pasting some commands.  I've never had to use the CLI in Mepis.  I'll take another look at Mepis, but if this is true I hope Ubuntu devs will notice and consider adopting some of the same features.

---

### Post by aysiu on 2005-07-09
[QUOTE=jr0]Really? I didn't notice. I found it annoying to use. Did I mention it's not free? That you have to pay a subscription fee to download packages? No thanks.[/quote] Oh, I'm not saying Linspire isn't annoying to use, and I'm not saying it's free. I'm saying it is a good alternative to Windows (for some people), does not require CLI, and follows the one-user-as-administrator model.

>  I'll take another look at Mepis, but if this is true I hope Ubuntu devs will notice and consider adopting some of the same features. Part of it is Mepis including a lot of GUI stuff, part of it is KDE-stuff.

---

### Post by jr0 on 2005-07-09
Maybe Linspire is ok for some people but two strong points of Linux are the open source and free distribution aspects. You know, so it's not controlled by one company, and so you can give a disc to your friends/relatives and not worry about legality.

> part of it is KDE-stuff.
KDE is nice. I use Kubuntu.  ;-)

Guess I'm not alone in disliking password prompts.
[http://www.mepis.org/node/6330](http://www.mepis.org/node/6330)

---

### Post by poptones on 2005-07-09
> My original point was, the command line does in fact scare off would-be new users. The FAQ does help, but it's not enough, and this is not the only thing scaring people off. 

Redneck mom doesn;t seem to scared by it. She's glad it asks her - it tells her that something is going to happen that COULD screw up her machine, and she knows it's not going to do anything to screw itself up without asking her.

Fifth time the charm? If you don't like typing the password, log in as root. Make it your desktop. Live happy, die young.


> Maybe they want to be able to do whatever they want on their machine, without it holding them back?  There must be ways to keep the same security and reduce the hassle on the user.

if they want to do 'whatever they want" on their machine then they better learn to love linux, because Microsoft won't let them do that now. Someone has to be accountable for this, and if they are not willing to take on that very minimal responsibility then big brother will do it for them. the internet is a shared resource, a global community, and it is inevitable there will be laws and regulation to ensure people reasonable security while there. Some people will no doubt continue to walk around in ski masks, but the time is quickly coming when those who **provide** these ski masks - those users of hacked machines - will be regulated offline. They will be barred as "bad players" until they fix the problem. If they will not take on the minimal responsibility of doing for themselves then they will end up having to trust someone else - namely Microsoft - to do it for them. Then they wil be able to "do what they want" to their heart's content - just so long as they pay the monthly service fees and don't visit any of those "unsafe" sites big brother doesn't like.

>  I'm talking about every new user, not just myself. THEY may not trust synaptic. THEY won't want to enter passes to do basic things.[quote]

Ahh, those mythic "other people." Funny... none seem to be behind you.

[quote] In home systems I work on (because yes, I'm qualified to work on them) I never see multiple user accounts for Windows.

Then you do not work on many. I have dealt with literally hundreds of home users and a great many of them LOVE the "multiple desktops" functionality of XP. Mom has a desktop. Dad has a desktop. Sis has a desktop and mom dosn't have to look at either of them. 

"Those other people" do not seem to have a hard time dealing with the concept of user accounts. These are the ones who, by and large, also do not have machines infected to the gills with crap. IOW those who have learned better. 

As I said, this is not a windows/linux issue. It's an issue of education. And if you are not teaching your **clients** how to make use of these facilities and why it is important, **you are not doing your job.**

> There are rarely times when a program has unresolved dependancies in windows

Not a gamer I guess...

> and developers usually list them on their site.

And with ubuntu that's not even needed. If it's in synaptic it gets installed, no googling and no poring over the authors website FAQ.

>  Only poorly designed apps, hacker apps, or Microsoft's apps ever overwrite system files.

ROTFL. "Poorly designed apps, hacker apps, and Microsoft apps..."

Quite a community there.

> Not everything I need is in Synaptic, and not always the version I need. 

How do you know? If it's not in synaptic then you are trying to install unsupported software. If it's not in synaptic it's not there for a reason. So are you technically proficient enough to fix your system when unsupported software borks it? Are you certain it is not a "hostile app" that is just going to make your machine one more zombie for the whorde o spammers?

it seems to me the "freedom" you want is the "freedom" to bork your system without having to learn how to maintain or to fix it. That flew well when every desktop was an island - but this isn't that world any more. Like it or not, the days of freedom without responsibility are passed.

---

### Post by Leif on 2005-07-09
[QUOTE=jr0]This is for you too N'jal. Most of you aren't new to Linux.  You haven't just switched over from Windows and you aren't having the experience most newbies will.  Things you overlook as "how Linux works" may be the things that make desktop users not even want to try Linux.  You're attitudes don't help people feel welcome to this wonder filled community. Linux for all, except if you offer advice on improving it that doesn't jibe with the elistists.  [/QUOTE]

Wrong. I'm new to linux, I switched with ubuntu. Please drop the martyr act.

[QUOTE=jr0]
On whose part? Seasoned Linux geeks, or newbies? If these things "have been raised 1000's of times". What's the old saying, lots of people can't be wrong. [/QUOTE]

I'm a newbie, and I don't care if a million people complain about it, **you can't do away with user accounts like that**. If you want that, either login as root, or switch to another distro. And don't regurgitate that line about "oh isn't ubuntu for humans"; it is, but you can't make everyone happy, especially if what they're asking for is a bad idea.

---

### Post by jr0 on 2005-07-09
[QUOTE=poptones]"Ahh, those mythic "other people." Funny... none seem to be behind you."
"Redneck mom doesn;t seem to scared by it."[/QUOTE]
One example. How about the rest of the 90% of desktop users who don't or won't run Linux? The fact that Linux is on 3% or less of all desktops actually does put many behind me.  There is no viable, free, desktop Linux and people like you will keep it this way.  At some point you have to ask... "why?".  Why don't people like Linux? Does it smell? What's wrong with it? Can we fix it? Listen, if you live inside the box, you will also die there... don't forget that.

 You're right, maybe I will switch to a different distro.  Thanks for the insight.  :roll:

---

### Post by az on 2005-07-09
I hate it when users delete their posts and run away screaming.

What went wrong here?

---

### Post by poptones on 2005-07-09
> One example. How about the rest of the 90% of desktop users who don't or won't run Linux? The fact that Linux is on 3% or less of all desktops actually does put many behind me.

Not because you are too lazy to type a password. SEVEN times now: this is not a linux issue. XP has the same features and a great many windows users DO use them. 

> There is no viable, free, desktop Linux...

You can click your heels all you like, Dorothy, Oz ain't happening.

> and people like you will keep it this way.

People like me? People who contribute code and documentation? People like me who take the time to educate clients instead of telling them the same nonsense as the rest of the corporate world? 

> At some point you have to ask... "why?". Why don't people like Linux?

Some people, as you have so well demonstrated, simply don't like it because they have an agenda. They don't like it because it is a threat to their dogma.

> Yes there are problems with Synaptic and Ubuntu. You just ignore them, or you like them.

Bzzzt. I was just talking with someone in another discussion about the problems with synaptic. I was simply making the point that the arguments YOU were making were ill conceived. 

> OK... Now you work in IT AND you're a hotshot hollywood movie editor? Very ambitious. Oh and your a hacker too.

I am what I am (and I'm not popeye). What I do for money does not define who I am. But if you really want to know, yeah I have worked in Hollywood and elsewhere on production. I know what's relevant because I've been working with computer graphics systems more than a decade, I've even created teaching materials for college coursework. Is it really so hard for you to believe someone can have a scientific background, a reasonably high IQ, AND be artistically inclined? 

Want to know how I made contact with those "hundreds of clients?" I took a grunt job in a call center - a call center where I had **trained** new employees when it first opened up and then quit to pursue other interests. I went back because I *wanted* to work the phones - I never got the chance the first time when I was teaching everyone else how to do it. And it was a bomb of a job, too: I got paid to sit on the phone all day and direct clients to open source solutions. When the other techs were handing out generic PIN codes so customers could unlock their outdated CD copy of Office I was leading them to OpenOffice.org and freedom. And they loved it - I had one of the highest customer staisfaction scores in the shop. I got paid to "fight the man." 

**That's** "the kind of person" I am. I love to talk the talk, but nobody can say I don't walk the walk as well.

Now, let's see YOUR resume.

---

### Post by TravisNewman on 2005-07-09
*"And it was a bomb of a job, too: I got paid to sit on the phone all day and direct clients to open source solutions. When the other techs were handing out generic PIN codes so customers could unlock their outdated CD copy of Office I was leading them to OpenOffice.org and freedom. And they loved it - I had one of the highest customer staisfaction scores in the shop. I got paid to "fight the man.""*

That. Rocks. Hard. I wish I'd had the mind to do that back in my days of phone support for the university.

---

### Post by RickSGM on 2005-07-09
Quote from Poofyhairguy:
> Is pointing newbies to the command line a bad thing?  

1st:  I'm a newbie to linux.  Does the command line scare me?  NO!  This distribution is one of the best documented I have seen.  It don't make a hoot if I have to copy and paste a little on setup.  SOOO WHAT????

2nd:  If I'm doing something to the system, I dang well should have to do some passwords, to be safe and sure.  Hmmmm.  Unless I'm updating the system, for example, adding a package or updating the security updates, I don't have to do another password after login.  I'm not a big gamer, or anything like that, but most of mine is everyday common use of a computer.  Office, check emails, go googleing, maybe a quick 5 minute game or so.   Where's that bunch of times to type in the passwords in every day use?  

3rd:  I don't mind typing in passwords a couple of times to be more secure.  I'm not a genius or guru on computers either, just for the record.  Just an everyday user and learning.  

4th:  Sometimes, people can't be satisfied.  I say this poofy, I think you've done a heck of a good job.  The commands are good, accurate, and a lot of help.  I've had very few problems with the ubuntu.  Those I've had, I have found very good help.  Try digging through the microsoft help site a time or 2.  Yuck!!!!  I commend all the developers and ones that run the forum here, for they have to be great people.  Period.  You won't please everyone, but this is one happy camper.

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=jr0] At some point you have to ask... "why?"
[/QUOTE]

Its easy. Because if a company sells a PC that doesn't have Windows on it, they lose their OEM licencing for desktop PCs.

MS is the main choice, but that does not make it better. There are WAY more Windows PCs than OSX boxes, and OSX blows Windows out of the water.

Too many people confuse popularity with quality. They are not one and the same.

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=garnertr]PoofyhairGuy,

When I see your icon in the messages, I know that your about to give useful information.

Myself, I could care less HOW the information is presented.  I think we are getting hung up on the idea of GUI and/or Command Line and that either one is the ONLY way to go and if your not using it then you are wrong and/or a dweeb...

Myself, I'd like to learn more of the command line; I find the screen shots w/ the command line instructions very useful and helpful, after all, I cannot messup something as simple as "uname" or "apt-get install xyz".

From my own observations, Linux ppl are so hung up on their world of this is the only way to do it, anything else is windows and therefore bad; which is not true (IMHO).

So, keep up the GREAT WORK, I look forward to your postings, keep them up, I'm learning from you; maybe I should say thank you more often, but I don't, but just so you know, this person THANKS YOU for your efforts![/QUOTE]


Thanks. I try my best to help people and I will continue to do so. This motivates me more.

---

### Post by TravisNewman on 2005-07-10
RickSGM-- always good to read these kinds of posts. As poofy says, it's very motivating. Thanks very much!

---

### Post by Takis on 2005-07-10
[QUOTE=jr0]One example. How about the rest of the 90% of desktop users who don't or won't run Linux? The fact that Linux is on 3% or less of all desktops actually does put many behind me.  There is no viable, free, desktop Linux and people like you will keep it this way.[/QUOTE]

I'd say most of them are viable, but obviously that's subjective.

In any case, an observation like this leads me back to my usual argument: if Linux (or some FREE OS + major apps) were to be taught in schools in place of (Edit: or better yet, alongside) proprietary (read: Microsoft) software, I think OSS market penetration would soar. I have plans in a couple of years to try and do this where I live, too - if I can find a school that'll believe it's feasible.

---

### Post by aysiu on 2005-07-10
Schools are a great place to teach people Linux. Part of the problem is the vicious cycle that the Microsoft marketing machine has set up. Why teach Linux in schools if "everyone" uses Windows in the workplace? Why use Linux in the workplace if "all" the commercial software is written for Windows? Why write commercial software for Linux when "every" business and school is using Windows? See how Microsoft's dominance perpetuates itself? 

It's hard to get Linux into schools with that kind of starting point. I'd love it if schools started using Linux, though. Presumably, schools are about education. If that's the case, ideally, Mac OS X, Windows XP, and some form of Linux should be taught concurrently.

---

### Post by Takis on 2005-07-11
Well, where I live (Australian Capital Territory) people are pretty liberal, and the media is a real pack of piranhas if they judge something the government's doing to be unfair (e.g. endorsing a monopoly). Recently the media had a big speel about how public servants catching planes were all going with just one company, so the government had to turn around and say that public servants must catch 'the cheapest flight of the day', in order to encourage fair competition between airline companies.

I think it's possible to show the same sort of thing with Linux. I think in workplaces people use only Windows because that's what they've been taught, and it's definitely not worth the money to retrain them over to Linux or Mac or whatever. I think though that at least a couple of schools could be persuaded to run some OSS-based classes, which down the track would let companies and government departments implement something other than Windows.

Buuuut that's another topic. We're meant to be discussing the best way to help newbies, I think...  :smile:

---

### Post by aysiu on 2005-08-23
At the risk of inciting a flame war, I'd like to give my take on the term "user-friendly."

First things first: I think most Ubuntu users would agree that if we could have every single function and every single program and command accessible via both command-line *and* graphical user interface (GUI), that would be ideal. That's not the case, however.

I'd also like to mention right off the bat that I like Ubuntu because its general use is point-and-click, but its configuration usually needs the command-line in some way. There are other distributions out there that have graphical user interfaces for just about everything (I'd highly recommend Mepis for the GUI-dependent). If you think it's too bloated, use Mepis-LITE.

Last disclaimer: I'm not some freaky programmer who does *everything* from the command-line and thinks people who use GUI are wimps. I love GUI, and I use it just about every day. In fact, when I first started using Ubuntu, I was a bit turned off from having to use the command-line (I then went to Mepis), but after finding the [Ubuntu Guide](http://www.ubuntuguide.org), I learned to love it.

According to [Dictionary.com](http://dictionary.reference.com/search?r=2&q=user-friendly), *user-friendly* means "Easy to use or learn to use."

Seems like a simple enough definition. The word *easy* makes things complicated, though. There are different kinds of easy, as far as I can tell.

1. One kind of easy is labor easy--you do one step instead of three.
2. Another kind of easy is thinking easy--you don't have to think; you just do what you're told.
3. The last kind of easy is memory easy--you have to think, but you don't have to remember.

The need for GUI relies on the last kind of easy. At every decision point, you have to think about what you're trying to accomplish, where you have to look, and what's the most appropriate button to press. It's not heavy philosopher thinking, but you do have to pay attention. I can't tell you how many times I've accidentally clicked and ended up deleting files when I meant to copy them or clicking cancel when I meant to click OK.

The reason a lot of people think of GUI as "easy"--even if it's not labor easy (often you have to click many times) and it's not thinking easy (you have to pay attention)--is that GUI is memory easy. You don't have to memorize anything. Sometimes the hardest part of picking up a new "language" is its vocabulary. When people are new to an OS and already a little disoriented, the last thing they want to do is have to memorize cryptic commands (ls, cp, mv, make, make install, apt-get, gedit, sudo), especially if there seem to be many commands to memorize. This is why people are comfortable with GUI, even if it isn't easy in every way.

Another reason some people are more comfortable with GUI is bad typing. I've seen many times people saying they typed such-and-such into the console but got some funky error. What ended up being the problem? They had an extra space or comma where they shouldn't have had one. Or they forget to capitalize the X11 in /etc/X11/xorg.conf.

There are a good many reasons to embrace the command-line, though, particularly for Ubuntu beginners. The command line often cuts down on labor. Much as I love Synaptic (and, believe me, I love Synaptic), if you happen to know the exact name of the program you want to install, it's far easier to open a terminal and type *sudo aptitude install programname* than it is to open Synaptic, search for the program, mark it for installation, and apply changes. Okay, that's not the reason beginners should embrace the command-line. That's after you've already gotten familiar with stuff. I would say getting help over the internet (these forums or the Ubuntu Guide) is the reason to embrace the command-line. This is easy type #2: you don't have to think or even pay attention. Just copy and paste into the terminal whatever people tell you to type.

Sure, GUI might be easier if someone were helping you in person. She could say, "Click on that icon. No, that one. See that? Click on it." However, short of doing screenshots (which are time-consuming and bandwidth-consuming), it's very difficult to help someone GUI style over the internet. It is very easy to help someone by saying, "Here, just copy and paste whatever I typed here."

So what does "user-friendly" mean in practical terms? Well, first of all, GUI will always be friendlier to most new users because most new users come from Windows and have never installed Windows (keep in mind that most Windows installations until Vista were text-only). The familiar is friendly in one way. GUI also requires very little memorization.

If you know how to control-c (to copy) and control-shift-v (to paste), you might want to consider opening up a terminal. It may not seem friendly at first, but the terminal is willing to be a friend to any new Ubuntu user.

P.S. This is all about configuration stuff. Once you're all set up, you should need only GUI to download things, surf the internet, word process, image edit, etc.

---

### Post by poofyhairguy on 2005-08-23
Great manifesto. More good PR documentation. I clap.

I would like to add that there is a smaller chance of user error when someone is copying and pasting commands (no matter if they understand them or not) then when they are fumbling through GUIs.

---

### Post by WirelessMike on 2005-08-23
Agreed.  Point made, and made well!

---

### Post by caspar_wrede on 2005-08-23
I use the command line for almost everything. Sure I like eye-candy as much as everyone else, but think about these points:

1) It's extremely quick for one simple reason. With a mouse you have, say 4 or 5 degrees of freedom: one X dimension, one Y dimension and 3 or 4 buttons. WIth the keyboard you have 50  or so degrees of freedom (the number of keys on a keyboard). Just imagine typing text on a graphical keyboad with a mouse as opposed to typing text on a real physical keyboard. Which is quicker?

2) The really clever thing about the command line is that it inherently "logs" everything you do. You just need to scroll up or use the "history" command. The only way to do this with a GUI would be to make a video...

3) Scripting. To repeat a sequence of commands you simply bundle them together into a text file and then execute that. How would you do that with a GUI?



Think about it and then embrace the pure undliluted sexiness of the command-line. There are huge advantages to learning to use the command line.

Caspar.

---

### Post by Juergen on 2005-08-23
Probably not for real 'noobs' but after you reach the 'advanced user' state:
Don't forget the ability to script things.

For example, I have a script that burns my (daily, simple *.tgz, created with another script) backups to CD. It even determines if it has to start a new session.
I don't know of a way to automate this with any GUI for cdrecord (filenames change, since they have the date in it)

I probably sat 2hours before it worked, but now its 'memory easy' because I just have to start the script and don't have to remember all those options to mkisofs and cdrecord...

---

### Post by xequence on 2005-08-23
I do like sudo apt-get install ____________ very much, synaptic for me is if I need to search for something... But for most things I prefer the GUI. (Someone posted that mepis is more about GUI so I wanted to try it out, I only had 650 MB CDs and they needed 700 MB ones. Even mepis lite is 651 MB).

With the command line you dont need to learn how to use it. It is as easy as typing somehting in and clicking enter, and maybe putting the password in if you use sudo.

Let me use an example... Installing a .deb or .tar.gz file. I still have no idea how to do it nomatter how much I try. (No, I am not asking for help, this topic isnt about help :P Just an exemple). If I could just maybe right click and choose "install" and it would do everything for me, it would be great. In my opinion that would be easier then using different "sudo dpkg -i blah.deb" or whatever.

Anyway, my opinion aside, good article =P

And what I said doesent make any sense, sorry. I write something then change it then go all over it adding things and changing things. It often doesent make sense   ](*,) Then it edit it some more and the final post is rambling on about CNN and americans having cheap gas.

---

### Post by aysiu on 2005-08-23
[QUOTE=Juergen]Probably not for real 'noobs' but after you reach the 'advanced user' state:
Don't forget the ability to script things.[/QUOTE] I'm stil in the newbie phase, so I may hold off on the scripts until later. Good suggestion, though.

---

### Post by aysiu on 2005-08-23
[QUOTE=xequence]I do like sudo apt-get install ____________ very much, synaptic for me is if I need to search for something... But for most things I prefer the GUI. (Someone posted that mepis is more about GUI so I wanted to try it out, I only had 650 MB CDs and they needed 700 MB ones. Even mepis lite is 651 MB).

...

Let me use an example... Installing a .deb or .tar.gz file. I still have no idea how to do it nomatter how much I try. (No, I am not asking for help, this topic isnt about help :P Just an exemple). If I could just maybe right click and choose "install" and it would do everything for me, it would be great. In my opinion that would be easier then using different "sudo dpkg -i blah.deb" or whatever.[/QUOTE] You may just love Mepis, then. I know I did. Double-clicking the .deb files opens up KPackage (or Kynaptic--I forget which one) and prompts you for installation.

---

### Post by skoal on 2005-08-23
...pressing the envelope against his forehead, the great Carnack predicts an answer, "shell shock".

A hearty laughter to his side echoes forth, "HOOOH! HOOOOH! HOOOOOH!..."

Carnack slowly twists in his chair, cracks a smile to his assistant and slowly gestures to him this time, "sheLL.....................shocK......"

Although more subdued than the first, wry laughter from his assistant fades off this time, "HOOooh! hoooh! hoooo..."

Carnack wiggles his fingers and rips at the envelope.  With a quick blow and unravelling of the paper, he reads the question, "What do you call a one armed linux convert?"

\\//_

---

### Post by Brunellus on 2005-08-23
at the risk of sounding silly, I <3 the commandline!

In fact, a lot of my favorite things to do are commandline:

1) Running "top", and seeing what my computer is doing at that given moment.  Yeah, there are guis, but somehow I actually like top better.  Last night, I ran top on nosferatu (the family web/email computer in the kitchen) to find some weird process hoggint a lot of CPU time. I asked my dad what he had been doing, showed him the output of top, and, when he said he didn't recognize the process or what it might have come from, I killed it.  NO more sluggishness.  (actually, it was really bizarre, since he had already logged-out, and the process (soffice, I think) carried on without him.)

2) ssh-ing to nosferatu from my upstairs computer, so I can do maintenance while someone else surfs.

3) lynx.  just because it's badass, and a quick way to browse the web when I can't be bothered to do a graphical login.

4) apt.  Yes, from the commandline.  Synaptic is nice but seems SOOOOO slow compared to actual apt from the commandline.  I'll only fire up synaptic if I'm in a "gee, I wonder what's new down at the repo" mood.  If I want to install something, and I already know what I need, I just apt-get it.

---

### Post by Brunellus on 2005-08-23
[QUOTE=skoal]...pressing the envelope against his forehead, the great Carnack predicts an answer, "shell shock".

A hearty laughter to his side echoes forth, "HOOOH! HOOOOH! HOOOOOH!..."

Carnack slowly twists in his chair, cracks a smile to his assistant and slowly gestures to him this time, "sheLL.....................shocK......"

Although more subdued than the first, wry laughter from his assistant fades off this time, "HOOooh! hoooh! hoooo..."

Carnack wiggles his fingers and rips at the envelope.  With a quick blow and unravelling of the paper, he reads the question, "What do you call a one armed linux convert?"

\\//_[/QUOTE]
 HOH HO HO. 

YOU ARE CORRECT, SIR!

Johnny Carson.  *sigh*  now that was good TV.

---

### Post by Kvark on 2005-08-23
Yeah, the command line is kinda user friendly, in a way, uhh, what I mean is...

Something is user friendly if it fills one or both of these conditions:
1. It has only a small learning curve.
2. It requires only a small investment of time and effort.

The command line doesn't fill condition 1 so most people think it is complicated. But it often fills condition 2 very well so it is user friendly in a way.



BTW. What I love the most about the command line is to type the first 3 letters of a program's name + tab + enter to start it. The only GUI thing that is as fast as that is shortcuts on the panels, which I have for my favourites. But for all other programs navigating the menu would take ages longer. Only thing missing is a keyboard shortcut to focus the mini commander panel applet.

---

### Post by xequence on 2005-08-23
[QUOTE=aysiu]You may just love Mepis, then. I know I did. Double-clicking the .deb files opens up KPackage (or Kynaptic--I forget which one) and prompts you for installation.[/QUOTE]

Yea, I hope I can find a 700 MB cd. The community doesent looks as good... Mepislovers.org had 27 users online while ubuntuforums had 600.

They had a topic on the site "Mepis vs ubuntu". It was so biased! They were lying about ubuntu and stuff o.O Atleast on this site people arnt afraid to say if they like other distros :)

---

### Post by aysiu on 2005-08-23
[QUOTE=xequence]Yea, I hope I can find a 700 MB cd. The community doesent looks as good... Mepislovers.org had 27 users online while ubuntuforums had 600.

They had a topic on the site "Mepis vs ubuntu". It was so biased! They were lying about ubuntu and stuff o.O Atleast on this site people arnt afraid to say if they like other distros :)[/QUOTE] Yeah, the community here is one of the main reasons I switched to Ubuntu. Mepis's community's okay, but it's not that responsive or knowledgeable.

---

### Post by Kyral on 2005-08-23
I <3 the command line. I mean, the more I can do without moving the mouse the better, 'cause I'm lazy like that. Its even more user friendly when you have a keyboard shortcut to the terminal so you can hit it (Scroll Lock for me), do what you need to do, Alt+F4 it, then Alt+Tab back to whatever you were doing :D

---

### Post by aysiu on 2005-08-23
[QUOTE=Kyral]Its even more user friendly when you have a keyboard shortcut to the terminal so you can hit it (Scroll Lock for me), do what you need to do, Alt+F4 it, then Alt+Tab back to whatever you were doing :D[/QUOTE] Yeah, my keyboard shortcut is Control-Alt-T (for "Terminal").

---

### Post by Brunellus on 2005-08-24
[QUOTE=Kyral]I <3 the command line. I mean, the more I can do without moving the mouse the better, 'cause I'm lazy like that. Its even more user friendly when you have a keyboard shortcut to the terminal so you can hit it (Scroll Lock for me), do what you need to do, Alt+F4 it, then Alt+Tab back to whatever you were doing :D[/QUOTE]

ctrl-alt-F($whatever) gets me to the virtual console.  ctrl-alt-f7 brings me back to my X session.  I've learned to love this feature--even though I orginally discovered it by mistake.

I have to remember to go back to X when I use the virtual console on my mother's machine, because she freaks out when she sees it.

---

### Post by jpkotta on 2005-09-07
Hooray for the [CLI](http://en.wikipedia.org/wiki/In_the_Beginning...Was_the_Command_Line).  I used to use DOS terminals and write .bat files in windows, but only when I wanted to automate something or the program was CLI-only.  Then I tried Unix and found a Real CLI and scripting, and never looked back.  

Once you're forced to use a CLI (like I was at a job) you get good at it, you get past the steep part of the learning curve, and you realize it's not outdated or inferior.  The fact is, NOT EVERYTHING NEEDS A GUI.  Some tasks are better suited to CLIs, just as some are better suited to GUIs.  

On user friendliness: Why are emacs and vi so popular amongst Unix users?  They are certainly hard to learn (especially vi).  But past a certain point, investment pays off and they become easier to use than, say, nano.  The same applies to the command line.  Well-designed GUIs are "easy" only because you can use them without reading a man page first.  Personally, I think GUIs should really only be used for one-time tasks such as installation (Ubuntu's installer is graphical enough) and configuration, and for inherently graphical tasks, such as image editing and web browsing.  CLI is for routine stuff like copying files and starting applications.

---

### Post by BoyOfDestiny on 2005-09-07
Gotta agree. 

It always mystifies me how some people complain about using the GUI, since you ALWAYS have the option of using commandline.

As somone who naviagted DOS while my age was still single digit, I enjoy navigating through command line. Being able to drag-drop long file/folder names from nautilus is a plus... 

Haven't done any fancy scripts, just the commands I'd type to download zsnes from cvs and compile...

If someone know hows to make it return "" (for cvs anonymous pass...echo?). That would be great to know. :)

P.S & RANT command line does suck in windows server 2003. No F3 (as even DOS has had since as long I can remember), no up, no tab, and longfilename support blows... in that environment making .bat's is annoying, if you run by double clicking the batch file... command prompt dissapears... so you have to navigate manually without the features that make it a joy in linux...

---

### Post by GreyFox503 on 2005-09-07
Just the other day on slashdot, this article was posted about GUIs:

[http://slashdot.org/article.pl?sid=05/09/06/1521252&tid=189](http://slashdot.org/article.pl?sid=05/09/06/1521252&tid=189)

It makes some good observations, mainly about how GUI is good for beginners to learn all the functions of a piece of software, but after a few hours, the interface just begins to get in your way when you *know* what you want to do, but you have to go through several screens to accomplish it.

---

### Post by Rovenhot on 2005-10-17
GUIs are considerably easier for beginners (I started using a (decrepid) Mac when I was 2 yrs. old).  Also, though, they are best for the millions of casual computer users who would prefer to get started right away.  If a Linux dev-team's goal is to be user-friendly to a large user base, (which seems to be the case of Ubuntu, according to the about page) its GUI, must thus, IMO, have access to everything necessary for normal use, i.e. front-ends to CLI utilities.  From what I've heard, Ubuntu is not quite at the point of total GUI accessibility (although I haven't used Ubuntu yet, so feel free to challenge that).  For those many who don't mind taking some time to learn a shell, beacuse it offers what they need faster (as I have learned), the CLI is great, but the GUI must have most of those features, with a shallow learning curve.

The reason I bring this up is that Linux is by far more secure and less bloated and convoluted than Windows, and that since it runs on the most widely available architecture, x86, it makes a good alternative.  However, many people don't move to Linux because it isn't as easy to use (from their perspective; I personally like the CLI).  If Linux (any distro) was more attractive, the internet would generally become more secure, which I think is an important goal, with the increasing number of internet-based scams.

---

### Post by Stormy Eyes on 2005-10-17
I think this should be made sticky.

---

### Post by aysiu on 2005-10-17
[QUOTE=Rovenhot]
However, many people don't move to Linux because it isn't as easy to use (from their perspective; I personally like the CLI).  If Linux (any distro) was more attractive, the internet would generally become more secure, which I think is an important goal, with the increasing number of internet-based scams.[/QUOTE] If that's the case, they should use Mepis or Linspire until Ubuntu makes a few more post-install configuration items all GUI. As it is now, Ubuntu's all GUI for use and somewhat CLI for setup and installation.

---

### Post by Lovechild on 2005-10-17
lay off the crack pipe please, cli is in no way more user friendly than GNOME - try doing every day tasks for the average joe in cli, browse the web, check email, etc.

betterdesktop.org pretty much makes this clear, we need to draw on the brains spatial reconistion not abitrary command names to convey information.

---

### Post by Stormy Eyes on 2005-10-17
[QUOTE=Lovechild]lay off the crack pipe please, cli is in no way more user friendly than GNOME - try doing every day tasks for the average joe in cli, browse the web, check email, etc.[/QUOTE]

Tourette's or not, I don't agree with telling somebody who's made a good argument to "lay off the crack pipe" just because you don't agree with him.

---

### Post by Rovenhot on 2005-10-17
[QUOTE=aysiu]If that's the case, they should use Mepis or Linspire until Ubuntu makes a few more post-install configuration items all GUI. As it is now, Ubuntu's all GUI for use and somewhat CLI for setup and installation.[/QUOTE]

If installation is the only problem, then [Easy Ubuntu]("http://www.ubuntuforums.org/showthread.php?t=64629"), which I've just found, will fix that.

---

### Post by aysiu on 2005-10-17
[QUOTE=Lovechild]lay off the crack pipe please, cli is in no way more user friendly than GNOME - try doing every day tasks for the average joe in cli, browse the web, check email, etc.[/QUOTE] Please point out to me where in the original post I mentioned anything about using the commandline to browse the web or check email. Thanks.

---

### Post by Lovechild on 2005-10-17
[QUOTE=aysiu]Please point out to me where in the original post I mentioned anything about using the commandline to browse the web or check email. Thanks.[/QUOTE]

You did call it userfriendly, which does indicate that your level is quite a bit above the average user - it might be more functional to you which is COMPLETELY different than userfriendly.

I use the commandline as well for some purposes and having used Linux for well over 7½ years I've grown accustomed to some of the commands - but the command userfriendly - hell no, it's not translated, many commands are based on abbrivations of english words and man pages are horribly complicated if at all discoverable by your average user.

Now had you said that the command line made you more productive or it was more functional for you, I wouldn't have made any comment, but I care deeply about usability and HCI issues. In fact most of what I contribute within the community is related to these observations on basic human interaction and use. I use the GUI because I like the usability that GNOME offers in abstracting away hard to do things in my every day life, ripping a cd is one click, typing up a document with stylings is simple in Abiword, browsing the web and reading my email is equally common and easy to do tasks for me. Now I have had days in my life of telnetting to the smtp server and firing off commands to send mails, it was.. somewhat pointless but never the less kinda cute.

It's not that I find cli pointless, but I don't want the average user to have to rely on it - it's a powerful tool for power users, but as for usability, it's very low on the scale. 

* In a stroke of deep irony, advocating the use of GUI's - my trackball started randomly moving around and clicking stuff - I guess it's dying from old age - I apologise for any odd stuff this might have caused, however it did teach me to navigate the forum using only keyboard commands for which the admins must get my praise as it works beautifully *

---

### Post by majikstreet on 2005-10-17
asyiu, there should be a forum for only your posts :)

I <3 the command line also. You want to install gdesklets? sudo apt-get install gdesklets

Now, you call that hard?  I learned commands by using them. I didn't sit there reading through miles of "command line help" documents, I just learned them as I went. People told me to do "ps -aux" and I did it. Later I learned more.

The greatest invention for the command line is "man". But, sadly, it is only useful if someone from the program wrote a good documentation. It's even better if they made it short, consice, and to the point.

The first distrobution I installed was Debian, which gave me a nice command line. Only problem was that I didn't know much about linux!

I believe that people should start with a gui, and familarize themselves with the terminal as they go along.

If I had never known how to use mount, cp, ls, cd, and other basic commands, I would never have been able to get X.org working. Imagine that! Then what would I have done, re-installed windows.

When you come from a Windows world, you don't know how to use the command line. If you are a little more advanced, maybe you know how to use ipconfig. 

-m

EDIT:
[QUOTE=Stormy Eyes]Tourette's or not, I don't agree with telling somebody who's made a good argument to "lay off the crack pipe" just because you don't agree with him.[/QUOTE]
I really agree here, you shouldn't talk like that. 

And to think that you, Lovechild, PMed me about an inappropriate comment, when _you_ are making inappropriate commends yourself! What has this world come to?

EDIT2:
Oh, and as far as I know, Tourette's syndrome does not make people make inappropriate comments. It makes people twitch and have "tics". While I understand that you have a medical condition, you can not use it as an excuse. [http://www.mentalhealth.com/book/p40-gtor.html](http://www.mentalhealth.com/book/p40-gtor.html)

I will tell you that I have a case of depression. I have felt suicidal at times. I have (used to be major) anger problems. I do not use these issues as an excuse for how I treat others. While I may say that I got angry and couldn't control myself, I will still apologize.

I am typing this calmly, I am not angry right now. I am not the type of person that types furiously at these type of comments.

And by the way, just because a person views differently than you doesn't mean that they are smoking crack. 

Our world embraces difference.

---

### Post by Goober on 2005-10-17
I like the Command Line as well over GUI.  For me its mostly that GUI reminds me of Windows a bit too much, and the Command Line seems more, well, it just feels better, I can't explain it more then that.  I generally use Synpatic to search for a program name, then use the Command Line to type it in.

Although, with the Command Line, it can get tricky when swtiching folders and all that when you are trying to install more complicated programs.

---

### Post by Rovenhot on 2005-10-17
Ignoring the last post, since someone doesn't know what we're discussing, I'd like to make a point on the side:

[QUOTE=majikstreet]Oh, and as far as I know, Tourette's syndrome does not make people make inappropriate comments. It makes people twitch and have "tics". While I understand that you have a medical condition, you can not use it as an excuse. [http://www.mentalhealth.com/book/p40-gtor.html](http://www.mentalhealth.com/book/p40-gtor.html)[/QUOTE]

I visited the link, as well as other medical sites, and discovered that Tourette's Disorder does in fact have several symptoms similar to OCD, ADD, and depression.  It is reasonable for Lovechild to say that because of the disorder, the post may sound offensive. However, I would encourage him/her to try to refrain from using potentially attacking language.

---

### Post by Lovechild on 2005-10-17
[QUOTE=majikstreet]
Oh, and as far as I know, Tourette's syndrome does not make people make inappropriate comments. It makes people twitch and have "tics". While I understand that you have a medical condition, you can not use it as an excuse. [http://www.mentalhealth.com/book/p40-gtor.html](http://www.mentalhealth.com/book/p40-gtor.html)

I will tell you that I have a case of depression. I have felt suicidal at times. I have (used to be major) anger problems. I do not use these issues as an excuse for how I treat others. While I may say that I got angry and couldn't control myself, I will still apologize.

I am typing this calmly, I am not angry right now. I am not the type of person that types furiously at these type of comments.

And by the way, just because a person views differently than you doesn't mean that they are smoking crack. 

Our world embraces difference.[/QUOTE]

Being very very calm here, but it's one thing to make a baseless uneducated claim on usability (for which I referer to my earlier post) it's an entirely different thing however to make an uneducated statement on my medical condition:

Tourette's comes in 3 types muscular tics (the twitching you mention), Vocal tics (the profanity for which the illness is famous in pop culture) and various possible side illnesses like depression, ADD/ADHD, these would be actual chemical, and treatable imbalances in the brain where the previous two aren't really directly treatable aside brain surgery (for which I'm not a candidate currently).

Now the thing that causes the vocal tics, and thus also the thing that makes me unable to at all times account for what I type, is a mental shortcircuit in thinking a thing and getting it out - there is no concern as to conquences such as hurting other people or being socially unacceptable - it sorta just has to come out, think of this as the mental unease you might get if you think you left the stove on and you are compeled to go back and check, sort of OCD'ish, the same kind of unease is present if one tries to subdue the muscular tics btw. life just doesn't feel right untill it's done - I've gone back and read a lot of the stuff I've written and if you'll notice it my posts often contain edits because I have to go back and.. reevaluate certain statements, maybe type them up in a more friendly tone. 

Now did I mean literally that the parent poster was smoking crack, no of course not, smoking crack is quite a common way of stating - you're wrong and you know it. I happen to have years of experience in usability and what was presented as usability was about functionality (which I don't disagree with at all, again see my earlier post). It is an area of computing I care deeply about and I don't want misrepresented, that is why I posted - not because I somehow have a personal problem with the person in question.

Now if anyone has a problem with my way of doing things, I would strongly encourage my account to be deleted because I am physically unable to change, I'm sorry that is the hand I was dealt by genetics - I am sick, I suffer from all 3 types of Tourette's, it is not a happy life - I get thrown out of busses for being rude to the elderly and just a small one of my problems - how easy do you think it is to get a job when you get the uncontrollable urge to call your boss a piss ant during the interview? 
The very least of my problems is what people on a forum online think about me, I'm open about my condition because I know at some point no matter how hard I try, things like this will happen - I'm getting quite used to explaining this - it's hurtful on a personal level to admit ones flaws and to be put in a position like this but that is my life and no matter how much medical treatment I get or cognative thearpy I undergo little will change, all I can offer is what I do right now, add a disclaimer to my signature.
When you get to know me I'm said to be a fairly pleasant person (dunno about that one, you'd have to ask my friends - one of them who actually does do heavy amounts of drugs, and lemme tell you I don't recommend it, cli or no cli..). 

Don't you think I would love to be friendly and well liked?

---

### Post by majikstreet on 2005-10-17
Alright,
sorry. 

And, I got you confused with someone else with PMing me.

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=Lovechild]
It's not that I find cli pointless, but I don't want the average user to have to rely on it - it's a powerful tool for power users, but as for usability, it's very low on the scale. 
[/QUOTE]

Tell that to me a year ago when I did magic stuff with my brand new (and first tried) Linux install by copy and pasting commands from google. In Ubuntu whole things that could take 100 or so clicks to install in Windows can be install with a single apt-get command copied from the guide.

You are correct its harder to learn the command line, but its not harder to use. In fact, its easier in some cases. For example:

Last night I had a friend of mine who needed help with a Linux box I set up. Her gdesklets were acting up and needed to be reinstalled. I started to try to tell her how to do it in Synaptic, but then instead I said "open up a terminal by click here" and " copy this into the terminal" then I gave her the apt-get reinstall line. Worked like a charm. She didn't know what the heck happened, but Synaptic is way over her head too. All she knows is that her desktlets work.

In the perfect world in which the Gnome developers live maybe situations like this should happen. Gdesklets should just work and not need to be reinstalled. But in the real world the command line is a great way for a new user to use the wisdom of the Linux super wizards without having to learn a bunch of GUIs that will just be used once. Instead its as easy as copying commands.

---

### Post by Rovenhot on 2005-10-17
You are missing the point.  The idea of ubuntu and many other distros is to give the user control, and if the user has to copy and paste a cryptic sentence to the command line that a techie gave him then the control is lost.  A GUI, for an inexperienced computer user, gives him control because he knows exactly what he's doing by clicking the install button. (btw, installing something on windows is an inappropriate example...sometimes i think M$ wants to rid you of your spare time)

EDIT:
Such situations as those you described below only happen when the user fails to see the intuitive nature of the GUI, in which case you should tell them how to do it in the GUI so that they can do it again if they have to.  Most people are more comfortable with GUIs, and will remember how to do something in the GUI if you tell them, more easily than they will remember a Linux command.  Then, if it isn't the user's fault, it's the GUI's, in which case it should be redesigned.

---

### Post by poofyhairguy on 2005-10-17
[QUOTE=Rovenhot]You are missing the point.  The idea of ubuntu and many other distros is to give the user control, and if the user has to copy and paste a cryptic sentence to the command line that a techie gave him then the control is lost.  [/QUOTE]

Not really. The user controls what command to copy and paste. At that level its more about how much you trust your source rather than what techinical knowledge you have. If I read the Ubuntu guide and it says to type in a line to get a desired effect, I have the control to copy and paste that line in there and get the effect. I control what features I add from that guide by what things I copy and paste. The Guide has thought about going to a screenshot GUI guide before, and it was mentioned that copying and pasting commands has a lower error rate (and less bandwidth costs). Does it give control in the stand point of "I know what that lines means in a broader sense?" No, but neither do GUIs.

Like lets say I set up a wireless network with the UBuntu Networking tool (which has the same options similar tools in other OSes have). What's DHCP? Whats a Subnet mask? Whats a gateway address? Whats a static IP? In the case of Ubuntu's GUI networking tool the blanks and choices given by the GUI are no less cryptic than command line commands. Thats becasue computers are complicated machines. A great GUI could be no better -those are the best terms for those techinical things. The best a good GUI can do is have sane defaults, and an OS does not need a GUI to do that. For my friend, being walked through synaptic is just as confusing as copying and pasting in the terminal when I can only help with AIM. For her it was more user friendly to copy and paste the command.

User friendly does not mean that low knowledge users can magically have all the abilities an experianced user has. No GUI on any OS is 100% easy for a non techinical person to understand. User friendly means it does not fight users when they try to expand their skills. It is friendly to them, and increases their knowledge.

 And note I did not say techinical skills- those are over rated. Sometimes a better skill is to know what words to put in google to get that one page with an awesome list of commands that I can copy and paste and get things working. Thats an important skill too. Yet it can be applied to more things than learning how a single GUI app in one version of one OS lets you do blank. So more people might come in with knowledge of how to search google (and there by get a cryptic command to copy and make things work), then knowledge of what desktop metaphor will help you with you problem, what menu the tool you are needing is under, what tab inside what GUI is needed to get this thing to work. Even the best GUI tools in existance are harder to use than google for a webaholic.


> 
A GUI, for an inexperienced computer user, gives him control because he knows exactly what he's doing by clicking the install button. 

Not really. What if the button is hidden by a cryptic term? To use my earlier example of networking, where is the GUI button that says "just connect to my wireless box as it came when I bought it?" Its not there. The GUI task to do that is to mess with the terms DHCP and Static IP. 

Only in a magical world do GUI make it so users know what they are doing. Experiance and knowledge makes it so they know what they were doing. Even the best GUIs have to have some nerdiness to work (my sister's Apple had a networking tool that still had the dreaded DHCP option). GUIs are not always easier than copying something from a trusted source in the real world.

---

### Post by aysiu on 2005-10-17
I think a couple of people have missed the point here.
Originally all I was saying is that there are different kinds of user-friendliness, and that sometimes the command-line is more user-friendly; sometimes GUI is. They're different tools for different tasks. Ideally, you can have every tool for every task and be able to choose which one you use.

Use whatever works for you--that's the Linux way.

---

### Post by poptones on 2005-10-17
play all my kate bush
slideshow my favorites from ATK
email [email]joe@joeshouse.net[/email] from [email]jim@thisisnotmydomain.com[/email]
list 50 most recent downloads
show all active torrents

In the very simple case of "play all my kate bush" I have to either:
open muine
select each album
add each to a playlist
hit "play"

or...

open xmms
open nautilus
open music folder in nautilus
open kate bush folder in nautilus
drag kate bush folder to xmms
hit play

I can't be the only person who is sick of having to constantly "locate" files, open a folder view and then select the actions with a mouse. I've become really, really adept at making FOR EACH loops on the command line because it's quicker than nautilus, but why should this power be limited to "power users" who groove on geek?

The command line IS the more efficient and powerful way to do things. Problem is, the legacy CLI isn't user friendly. Rather than trying to figure out how to cram more buttons on the dashboard, we need to be making the computer better able to understand simple typed requests.

Edit: BTW, the whole "just work" thing is true, but there are reasonable limits. If I want to send someone an email and I have an email client installed it should "just work" every time I want to send an email. but to say something like gdesklets should just be magically installed and "just work" is no more reasonable than saying my car should have new cylinder heads because I will it, or should have a custom paintjob because I waved a magic wand at it. It would be cool if the car *could* do those things, but to expect those things is foolish. Likewise, 8adding functionality* to a machine - even a computer - is not something that one can reasonably expect to "just work" every time. You cannot even get that sort of reliability when plugging together off the shelf consumer electronic equipment with RCa cables.

---

### Post by Rovenhot on 2005-10-17
After a few minutes' self-debate...

aysiu is right.  The best Linux can do is give different options for doing the same task (hmm...sounds like Mac) and let the user decide.  If the user needs help due to configuration confusion, I suppose cut-and-paste is fine.

---

### Post by Brunellus on 2005-10-18
[QUOTE=poptones]

The command line IS the more efficient and powerful way to do things. Problem is, the legacy CLI isn't user friendly. Rather than trying to figure out how to cram more buttons on the dashboard, we need to be making the computer better able to understand simple typed requests.
[/QUOTE]

"you are in a maze of twisty tunnels, all alike."

---

### Post by bootlinux on 2005-11-10
Most people will pick the easy way when given a choice. User friendly is what made windows number one. When I drive my car I just want it to start and go and most folks I know feel the same about there computers. When I'm on my computer I like to change and tweak the settings because it's an enjoyable hobby for me and not job related. Still I find myself going the easy route by copy and pasting on the command line. I make too many typing errors. I'm sure if I were more proficient with commands I would prefer it over GUI as it would be easier and quicker. 
I am learning but for now I can understand the newbie's frustration with command lines. I haven't encountered this sense the old DOS days of Windows 3.1. What we have is top notch but if We want Windows converters then it will need to be easy as well. I don't see why folks can't have GUI if it works for them. There should be some good GUI tutorials for them.
I'll keep learning the command line though it has more power and flexiablity.

---

### Post by aysiu on 2005-11-10
[QUOTE=bootlinux]I don't see why folks can't have GUI if it works for them. There should be some good GUI tutorials for them.
I'll keep learning the command line though it has more power and flexiablity.[/QUOTE] Read [this](http://www.ubuntuforums.org/showthread.php?t=59334)

---

### Post by Tulip on 2005-11-16
Newbie point of view. I find the command line a scary thing, although I do appreciate its advantages - I love a quick fix as much as the next person. When I dont understand what Im actually typing or pasting (most of it so far), I worry that I'm entering the equivalent of format c:. 

The questions that go through my mind are - have I entered the correct advice, was it out of date, what the hell does that jargon mean, why do they assume I know how to do that, was there a better solution 3 pages along, should I enter that better command when I eventually find it or will that stuff up the original thing I entered, where the hell did that command just go and what did it actually do and so on. Personally I won't be comfortable using it until I actually understand what I'm entering. 

I think you could probably multiply these feelings of unease a few times more with someone who isn't familiar with computery geekery stuff.

---

### Post by aysiu on 2005-11-16
Tulip, I can definitely sympathize with that nervous mindset. That's why you should always back up your work. **I** get nervous now when I read people's posts that say, "Yeah, I want to install Ubuntu and do a dual boot, but I can't back up the ten years' worth of files that I have that are super-important to me. Can I do it without losing my work?"

The answer, of course, is that if you know what you're doing, you probably won't lose you're work, but you're an idiot if you don't back up everything before repartitioning or installing a new operating system. Actually, you're an idiot if you don't back up stuff on a regular basis anyway.

No one's here's going to deliberately tell you to type in the equivalent of ```
format c:
``` They may tell you to do something (well-intentioned) that screws something up, though, either because they misdiagnosed the problem, you misrepresented the problem, or you typed in something wrong, or they don't know what the hell they're talking about.

Bottom line: back up your work.

That said, you can always ask questions. I tell people stuff like, > Type this in a termianl ```
sudo fdisk -l
``` It's funny, but I've never had anyone question me on it. *sudo* is the root command--it gives you the power to really screw up your computer, and *fdisk* sounds a lot like *format disk*. However, ```
sudo fdisk -l
``` simply lists your partitions. It's harmless. You can always ask, though, and you can Google commands people give you, too.

---

### Post by Takis on 2005-11-16
[QUOTE=aysiu]No one's here's going to deliberately tell you to type in the equivalent of ```
format c:
```[/QUOTE]
We hope. It is, however, entirely possible that some git will answer with some equivalent of 'rm -fr /' (almost as bad as 'format c:\') just for fun. Good practice is to read the man page, even briefly, on a new command you're about to run (to read a man-page, run ```
man <command name>
```for example, ```
man rm
``` will show you that rm means remove, so you'd be wary of using its powers.)
Alternatively, you may like to not act on advice given for a day or so, to give posts time to be moderated (or at least viewed by others) and bad advice will be commented on.

---

### Post by aysiu on 2005-11-16
[QUOTE=Takis]We hope. It is, however, entirely possible that some git will answer with some equivalent of 'rm -fr /' (almost as bad as 'format c:\') just for fun.[/QUOTE] Possible, yes. Of course, it's possible. It hasn't happened, though, ever, according to [this Google search](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%22rm+-rf+%2F%22&btnG=Google+Search). Your advice is good advice, though (man pages and waiting).

---

### Post by Brunellus on 2005-11-16
[QUOTE=aysiu]No one's here's going to deliberately tell you to type in the equivalent of ```
format c:
```[/QUOTE]

Back when I was a newbie, someone the community of another distro *which Shall Remain Nameless* conned me into deleting the contents of my home directory.

Boy was I ever mad when I found out.

---

### Post by linkunderscore on 2005-11-17
[QUOTE=Brunellus]Back when I was a newbie, someone the community of another distro *which Shall Remain Nameless* conned me into deleting the contents of my home directory.

Boy was I ever mad when I found out.[/QUOTE]

BSD would be my guess ^^ ? 



I am a relatively new user to linux, and I find myself more inclined to do things via command line than gui. Sometimes command line is just ALOT easier---I never thought that this could/would be the case. I was pretty timid with command line use at first, but I really really like being able to use it. I think that this is one thing that windows lacks. I enjoy learning command line and I hope that these forums continue to explain problems, issues, HowTo's, etc via command line. 

It makes it incredibly easy to follow. And like you said, it IS really hard to $@%! up copy and paste.

---

### Post by RawMustard on 2005-11-17
[QUOTE=linkunderscore]
I was pretty timid with command line use at first, but I really really like being able to use it. I think that this is one thing that windows lacks.[/QUOTE]

Exactly, this is a power feature of linux and something windows can only dream of achieving, we should be trumping this up everywhere possible.  People shouldn't think it's scary for new users.  describing 100 steps in a gui when the same could be achieved by typing 3 words, is something newbies will begin to appreciate.

That's not to say GUI's aren't needed, new users find it much easier to discover things in a GUI than a terminal and this is where linux is lacking!

---

### Post by Malphas on 2005-11-17
[QUOTE=aragorn2909]I must answer your first question with another question.  Does Ubuntu ever WANT to reach the "lofty goal"  of never needing the command line?[/QUOTE]
Of course.  That way people have the choice of how to use their computer.  People who're saying that they don't ever want Ubuntu to reach this goal are also saying then that they want to force users to do things in a certain way - the way they think is best.  To me this seems to go against what Ubuntu - and even Linux in general - is about.

---

### Post by Stormy Eyes on 2005-11-17
I agree with **poofyhairguy**: newbies should be introduced to the command line as soon as possible, and giving them commands to copy and paste into the terminal (with appropriate explanation) is IMHO a gentle introduction to the true face of Linux. 

I'll admit that I'm somewhat old-school; when I first got into Linux, KDE 1.x was considered hot stuff. I am used to doing all configuration work (and most of my file management!) through the shell and with a text editor. It makes sense to me to get under the hood and tell the machine exactly what to do instead of clicking about a GUI that might not do exactly what I've got in mind.

---

### Post by Kuolio on 2005-11-17
This is bit offtopic, but gotta say this..

[QUOTE=poofyhairguy]
... but until they make a GUI tool for ndiswrapper (aka the hardest thing for a new user to do) I don't put much weight into their opinions on the matter.
[/QUOTE]

Hope you are familiar with these packages:

ndisgtk
ndiswrapperutils
ndiswrapper-source

because right after installing them via Synaptic, I have had GUI for ndiswrapper. Or atleast I have been able to install windows drivers for my wireless using a GUI tool.

The Windows Wireless Drivers Tool is integrated well (after installing them packages) on the gnome panel, "System" and there "Settings" right after "Synaptic Packages Manager" (im not sure what those places/menunames are in english, as im using different language). Using this tool has been simple and very effective: my wlan is working with 4 clicks with da mouse.

---

### Post by aysiu on 2005-11-17
[QUOTE=Stormy Eyes]newbies should be introduced to the command line as soon as possible, and giving them commands to copy and paste into the terminal (with appropriate explanation) is IMHO a gentle introduction to the true face of Linux.[/QUOTE] I agree that newbies should be introduced to the command-line as soon as possible but for more pragmatic reasons--it's simply easier to say "copy and paste this command" than to try to describe clicking actions ("yeah, see that menu? Click on the second button that says *cancel*, then another window will come up...").

I was deathly afraid of the command-line (for some strange reason) when I started using Linux. It took me a good month to warm up to it. If someone had merely explained to me, "You can do it with point-and-click, but it's easier to copy and paste commands," I'd probably have started liking it earlier.

---

### Post by Stormy Eyes on 2005-11-17
[QUOTE=aysiu]I agree that newbies should be introduced to the command-line as soon as possible but for more pragmatic reasons--it's simply easier to say "copy and paste this command" than to try to describe clicking actions ("yeah, see that menu? Click on the second button that says *cancel*, then another window will come up...").[/QUOTE]

I thought I'd try to use a justification that wasn't utterly selfish for once. But I do sometimes tell my wife, when she wants to fiddle with something, "The GUI for that is here if you want it, but it's easier to do the job with a few commands." Sometimes she goes for the GUI, and sometimes she goes for the terminal. I saw her reading my Custom X Session howto the other day and fiddling about.

---

### Post by ssam on 2005-11-17
i think it would be a good goal to make ubuntu so that you could do everything from the gui.

do you browse the web with wget?

do you disable gdm and use startx to start x?

are you still using mutt for email?

if not why not? and why should you have to use vim to configure your network?

---

### Post by endersshadow on 2005-11-17
[QUOTE=ssam]i think it would be a good goal to make ubuntu so that you could do everything from the gui.

do you browse the web with wget?

do you disable gdm and use startx to start x?

are you still using mutt for email?

if not why not? and why should you have to use vim to configure your network?[/QUOTE]

Quite honestly, I have not found one task that I wanted to do that I couldn't with GUI, and I do a lot of fiddling.  I use CLI a lot, definitely, but that's because my introduction to Linux was remote access to a Fedora Core server with no GUI.  Just got used to the CLI.  It's quicker a lot of the times.

Sometimes a GUI is better (Firefox instead of wget, for example).  But when it comes down to writing a tutorial and troubleshooting problems, explaining it in terms of CLI is just easier and leaves less room for error.  I've found myself copying and pasting commands even though I know full well what they do and I'm not afraid of the CLI.

In short, rock on poofyhairyguy.  Rock on.

---

### Post by Brunellus on 2005-11-17
[QUOTE=ssam]i think it would be a good goal to make ubuntu so that you could do everything from the gui.

do you browse the web with wget?

do you disable gdm and use startx to start x?

are you still using mutt for email?

if not why not? and why should you have to use vim to configure your network?[/QUOTE]
...yeah.  but I still use slrn for newsgroups, and the default editor is vim.  

Let there be GUIs.  Just don't *compel* me to use them all the time.

---

### Post by Stormy Eyes on 2005-11-17
[QUOTE=ssam]do you browse the web with wget?[/quote]

I use wget to download ISO images and other big files.

[QUOTE=ssam]do you disable gdm and use startx to start x?[/quote]

As a matter of fact, I do.

[QUOTE=ssam]are you still using mutt for email?[/quote]

No, I use Sylpheed. Evolution is overkill for my needs.

[QUOTE=ssam]if not why not? and why should you have to use vim to configure your network?[/QUOTE]

Why shouldn't I? I use Vim for just about everything else.

---

### Post by egon spengler on 2005-11-17
[QUOTE=ssam]i think it would be a good goal to make ubuntu so that you could do everything from the gui.

do you browse the web with wget?

do you disable gdm and use startx to start x?

are you still using mutt for email?

if not why not? and why should you have to use vim to configure your network?[/QUOTE]


You're arguing against a point that nobody has made. There are no calls for the complete removal of all gui elements from ubuntu. The whole thread is solely (or at least was intentioned to be) about whether or not offering cli commands when helping people fix problems is a good or a bad idea

---

### Post by poofyhairguy on 2005-11-17
[QUOTE=Kuolio]This is bit offtopic, but gotta say this..



Hope you are familiar with these packages:

ndisgtk
ndiswrapperutils
ndiswrapper-source

because right after installing them via Synaptic, I have had GUI for ndiswrapper. Or atleast I have been able to install windows drivers for my wireless using a GUI tool.

The Windows Wireless Drivers Tool is integrated well (after installing them packages) on the gnome panel, "System" and there "Settings" right after "Synaptic Packages Manager" (im not sure what those places/menunames are in english, as im using different language). Using this tool has been simple and very effective: my wlan is working with 4 clicks with da mouse.[/QUOTE]

I helped test this tool and cheered the day it entered the universe. But it did not exist when this thread started.

---

### Post by endersshadow on 2005-11-17
When somebody tries to be helpful and makes somebody aware of their own work, I laugh.  Thank you for that.

---

### Post by canuck45 on 2005-11-25
I am a new user and so far I have 'fixed' my messups by following the command line prompts one of the gurus supplied.  This includes adding programs and undoing a real mess more than once.  I installed realplayer by command line, is there a GUI way to do it.  I had to create a ln -s in my mozilla plugin directory.  Its actually starting to make sense.

Keep the command lines coming provided its less than a full book of instructions.  Just glad my printer autodetected with no problem (lexmark) and I can print the instructions people give.

---

### Post by Malphas on 2005-11-25
If a user is asking a question that can be resolved via the GUI alone then that should be the preferred method to explain to them, in my opinion.  It may well be faster and easier for them to simply copy/paste something into the CLI but if they don't understand what it is they've posted then they've learned nothing and are no wiser than they were before; if they have to do something via the GUI then they should become slightly more familiar with the procedure and at least learn something subconsciously.

I agree that new users should attempt to get to grips with the basics of the command line but it takes a deliberate effort to do so and they're not going to learn anything by simply pasting text.

And of course if users get into the habit of copy/pasting anything anyone on the Internet tells them to, it's a disaster waiting to happen.

---

### Post by aysiu on 2005-11-25
[QUOTE=Malphas]
I agree that new users should attempt to get to grips with the basics of the command line but it takes a deliberate effort to do so and they're not going to learn anything by simply pasting text.[/quote] That may be true by and large--I don't know. For me, it wasn't, though. Maybe I'm a freak, but I learned by copying and pasting. First I just want to know what the motions are. Once I go through the motions enough, bit by bit, I understand things more.

> 
And of course if users get into the habit of copy/pasting anything anyone on the Internet tells them to, it's a disaster waiting to happen. Same for anything, though. Any time you ask strangers on an online forum for help, you risk borking your system. What's the difference of copying and pasting a command you don't know and clicking through some dialogues you don't know?

---

### Post by Malphas on 2005-11-25
[QUOTE=aysiu] Same for anything, though. Any time you ask strangers on an online forum for help, you risk borking your system. What's the difference of copying and pasting a command you don't know and clicking through some dialogues you don't know?[/QUOTE]
No, there's a clear difference between copying and pasting something that you don't understand and going through a series of dialogues and confirmation screens.  To suggest otherwise is nonsense.

---

### Post by aysiu on 2005-11-25
[QUOTE=Malphas]No, there's a clear difference between copying and pasting something that you don't understand and going through a series of dialogues and confirmation screens.  To suggest otherwise is nonsense.[/QUOTE] Touche. Nevertheless, I'm going to stick to giving people commands. If you want to explain point and click instructions, go ahead.

I've never seen anyone on these forums intentionally give damaging instructions to a newbie asking for help. If you or anyone else does so just to prove a point, I'll do everything in my power to get the offending party banned from these forums. Otherwise, everything's going just fine as it is.

If people are really paranoid, they shouldn't blindly be copying and pasting in the first place. They should, as people have suggested earlier in this thread...

1. Be asking the meaning of commands they don't understand.
2. Wait to see if other forum members respond and say, "Don't do that! That will erase your entire hard drive."

I see no reason, though, to disrupt the trust that has been honored so far as these forums have been active. People who don't have common sense will mess up anyway.

Fortunately, most commands (cryptic as they may seem to the uninitiated) give you a general sense of what they do. *mkdir* **m**a**k**es a **dir**ectory. *apt-get install programname* installs programname.

---

### Post by Malphas on 2005-11-25
[QUOTE=aysiu]Touche. Nevertheless, I'm going to stick to giving people commands.[/QUOTE]
I wasn't telling you to do otherwise, frankly I don't really care, this thread is asking for people's opinions on the matter which is why I posted mine.

[QUOTE=aysiu]I've never seen anyone on these forums intentionally give damaging instructions to a newbie asking for help. If you or anyone else does so just to prove a point, I'll do everything in my power to get the offending party banned from these forums. Otherwise, everything's going just fine as it is.[/QUOTE]
My point was that it's bad practice to encourage people to just copy/paste commands, and just because no-one intentionally gives bad advice here doesn't mean it won't happen elsewhere.  Besides, supposing it did happen here, banning the individual would be too little too late considering the damage would have already been done, it's hardly relevant.  And really, this wasn't even my main point, just a sidenote.

[QUOTE=aysiu]If people are really paranoid, they shouldn't blindly be copying and pasting in the first place.[/QUOTE]
I can't quite make sense of this bizarre statement, it's the people that aren't paranoid that are vulnerable, and what difference does it make whether someone is paranoid or not anyway?  You're not more likely to be given bad advice because you're paranoid.

---

### Post by aysiu on 2005-11-25
[QUOTE=Malphas]
I can't quite make sense of this bizarre statement, it's the people that aren't paranoid that are vulnerable, and what difference does it make whether someone is paranoid or not anyway?  You're not more likely to be given bad advice because you're paranoid.[/QUOTE] My point was that things work out as they work out. People who are paranoid will make sure they do not get misled into mischief. People who are blindly trusting always leave that option open to be misled.

There are only two points to argue: one is what the user should do, and the other is what the person helping should do.

The user will do what she does. If she's the skeptical/careful sort, she'll be skeptical and careful. If she's the trusting/careless sort, she'll be trusting and careless.

The person helping will also do what she does--give good advice or bad advice. It doesn't matter whether it's a command or set of point-and-click instructions. The only people who need to change are 1. the naive user and 2. the malicious helper. The naive user won't change because she is, by nature, naive. The malicious helper won't change because she is, by nature, malicious.

To have careful users and benevolent helpers argue about means of giving instructions doesn't change anything.

---

### Post by Malphas on 2005-11-25
Well there's more points to it than that.  Like I said that was more of a sidenote than anything else, my main point was that users are (in my opinion) less likely to learn anything by simply copying and pasting.  There's also the issue raised at the beginning, that telling a new user who's never used a CLI to start typing commands may feel alienated, although personally I don't have particularly strong feelings over this either way, I've never been bothered by the command line, but then I had used computers for a while before I ever saw a GUI.

---

### Post by Xian on 2005-11-26
This is not a cut and dry issue. It really depends a lot on the user, and what is best for them is not always so obvious to ascertain. For example, if a member started a thread saying that they wanted to create a new partition, and had used something like PM8 at work but didn't know that much about Linux, then I might direct them to the gparted application since that would be more in their realm of experience.

However, by doing this instead of giving them a set of commands they could just copy/paste, there is also the possibility they will make more errors by navigating through the GUI tool, and clicking the wrong option or action. A better guideline might be to asses the risk, and then offer some comments when using the command line method so they will gain understanding as they proceed with their task.

Based solely on personal experience, it is my opinion that there is overall less chance of making a mistake by copy/pasting sets of commands than from using most GUI tools which are currently available. Generally, if there is a problem with the command instruction it will just fail to execute, with no harm being done to the system. A few wrong steps in a GUI tool can be more damaging since it will execute any instruction that appears on the menu.

---

### Post by Sirin on 2006-01-24
I try to get people that are DONE with Windows to switch to Linux, but they are scared of the damned command-line which will always be the "key feature of Linux". This is the age of the GUI. Linux has not made that much progression for ease of use to the home user. While you Ubuntu fanboys are gonna hate me saying this, why can't we use a GUI as the primary function and use the CL as the secondary? Java's really hard to install, and for the home user, the best thing to do is "keep a Linux geek around". Why won't we be the revolutionary distro and drop the need of a Linux geek with you? Linspire's done it. Ubuntu is aimed for the home/server user. If a home user just wants to run a desktop, we need to give them the freedom of using it without forcing them to use the command line 80% of the time? The command line might be easy for many people here, but for starters, it's hard as hell, especially for the people who missed out on the DOS generation. People don't want to spend 95% of their time learning Linux, but USING it. Look at WIndows, you don't need to use their command line except for converting FAT partitions to NTFS. I know you think Windows or Mac sucks, but look how they turned to the GUI. The answer to most questions related to ease-of-use on these forums are 

> LInux is not WIndows.

Does this mean that as long as LInux is not Windows, it will never be easy? We need change. We need to STAND OUT from those "other" distributions. It's good to be different, right? In fact, we should make ease-of-use and user friendliness our first priority. Britney Spears doesn't know how to compile from source. Why should we be forced to use a command line? Nothing has much changed during this decade, but hopefully Ubuntu can make a good change. Include a GUI installer, a GUI way of doing what we could only do with the Command Line. Do you think we need change, or should we keep it the way that it is now?

---

### Post by Vlammetje on 2006-01-24
we should keep it the way it is now.

the fact that the command line is **perceived** to be this 'ugely incomprehensive complicated thing that you will never master', does not mean that it actually **is**.

In fact, I think anybody wanting to use linux should learn to use it well, and I think learning the command line (as I myself am doing bit by bit) is a vital part in that.

Finally. just because there's no GUI does **not** mean something isn't **easy**. These two just aren't synonymous. People need to learn that too. It's all part of the process imho.

---

### Post by SlugO on 2006-01-24
Like the catchphrase "Humanity to others" says, Ubuntu is already aimed to be easy to use for everyone, beginners included. And it has succeeded pretty well.

And I find it hard to believe that most beginners would need many programs that aren't already in the repositories. Where did you get the idea that most programs need to be compiled in Ubuntu?

So I'd say no, don't change the course Ubuntu. Keep going in the good, easy-to-use direction that you're already headed to.

---

### Post by BSDFreak on 2006-01-24
[quote=Sirin]I try to get people that are DONE with Windows to switch to Linux, but they are scared of the damned command-line which will always be the "key feature of Linux". This is the age of the GUI. Linux has not made that much progression for ease of use to the home user. While you Ubuntu fanboys are gonna hate me saying this, why can't we use a GUI as the primary function and use the CL as the secondary? Java's really hard to install, and for the home user, the best thing to do is "keep a Linux geek around". Why won't we be the revolutionary distro and drop the need of a Linux geek with you? Linspire's done it. Ubuntu is aimed for the home/server user. If a home user just wants to run a desktop, we need to give them the freedom of using it without forcing them to use the command line 80% of the time? The command line might be easy for many people here, but for starters, it's hard as hell, especially for the people who missed out on the DOS generation. People don't want to spend 95% of their time learning Linux, but USING it. Look at WIndows, you don't need to use their command line except for converting FAT partitions to NTFS. I know you think Windows or Mac sucks, but look how they turned to the GUI. The answer to most questions related to ease-of-use on these forums are [/QUOTE]

So use Windows, seriously NOBODY CARES!

> Does this mean that as long as LInux is not Windows, it will never be easy? We need change. We need to STAND OUT from those "other" distributions. It's good to be different, right? In fact, we should make ease-of-use and user friendliness our first priority. Britney Spears doesn't know how to compile from source. Why should we be forced to use a command line? Nothing has much changed during this decade, but hopefully Ubuntu can make a good change. Include a GUI installer, a GUI way of doing what we could only do with the Command Line. Do you think we need change, or should we keep it the way that it is now?

It means that Linux isn't Windows, it does not aim to replace windows for anyone, it's an alternative, some think it is better, they use it, some think Windows is better, they use Windows. 

Britney Spears would contribute SO much to the FOSS community, right? She'd help others with their setups, report bugs and contribute patches, DAMN, we can't lose her or those like her, FOSS will surely suffer if we do.

That last part was sarcasm if you didn't catch it.

Read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Stormy Eyes on 2006-01-24
Oh, jeez, not this nonsense again.

---

### Post by mstlyevil on 2006-01-24
So I guess Automatix is not good enough for you. A new user can get Ubuntu up and running with everything they would want and need with only copying and pasting two commands in the command line. After Automatix is installed they will have the GUI based installer for Multimedia, DVD, Codecs, P2P, Java, Flash and the latest Firefox and Open Office. Even the sources list is taken care of by Automatix. Anything else they need is available by Synaptic and the Add Programs utility. These things already exist yet there are **still** complaints about the command line. Also some things are done better by the command line so learning a little bit about it is actually a way to make the operating system easier to use.

If that is still too hard for them then they need to stick with Windows or buy Linspire or Xandros since everything is already done for them at install. Linux is not for everyone and most computer users are still better off using something else.

---

### Post by Gustav on 2006-01-24
I don't see the downside in that Linux should be easy to use.

Ease of use is a GOOD thing. I use the terminal all the time and I love it but I still think it is good if it's possible to do the stuff I do in the terminal via some sort of GUI.

There is no need to do stuff as they do in windows but I still think GUI is the way to the future :rolleyes:

---

### Post by aysiu on 2006-01-24
> **Sirin]I try to get people that are DONE with Windows to switch to Linux, but they are scared of the damned command-line which will always be the "key feature of Linux".[/quote] It's a key feature in Linux, but I don't remember every needing to use it in Mepis, PCLinuxOS, or Linspire. Minimally in Blag. 

> This is the age of the GUI. Linux has not made that much progression for ease of use to the home user. I would heartily disagree with this. In 2004, I tried Linux and couldn't use it at all. Package managers weren't in widespread use and documentation on them was scant. Hotplugging and automounting were almost non-existent. Now, just about every distribution uses some version of Apt or Yum, and they all detect USB and other media. 

> While you Ubuntu fanboys are gonna hate me saying this, why can't we use a GUI as the primary function and use the CL as the secondary? Because that's how Ubuntu is. Easy to use, more involved to set up. If you want all GUI, go for the aforementioned distros. I'd highly recommend PCLinuxOS and Mepis. 

> Java's really hard to install, and for the home user, the best thing to do is "keep a Linux geek around". I can assure you most Windows users I know can't install Java in Windows either. 

> Why won't we be the revolutionary distro and drop the need of a Linux geek with you? Linspire's done it. So let Linspire keep doing it. I think Ubuntu is an intermediate distro, and I get angry when people say, "Ubuntu's the best newbie distro." No, it isn't. Absolute newbies like it all GUI, as you say. However, there are distros that do that for you and that come with all sorts of proprietary codecs. That's not what Ubuntu's about. It's about free, and that usually means doing a bit of configuring yourself. 

> Ubuntu is aimed for the home/server user. If a home user just wants to run a desktop, we need to give them the freedom of using it without forcing them to use the command line 80% of the time? That's only in the setup, not in the use.

> The command line might be easy for many people here, but for starters, it's hard as hell, especially for the people who missed out on the DOS generation. It's not hard as hell. You copy and paste commands. For an operating system that has its largest support mechanism as online help, Ubuntu's command-line is essential. I'll give you an example. Let's say someone wants to install Thunderbird.

**GUI instructions**: Go to System > Administration > Synaptic Package Manager. Type in your password. Then click Reload. Then click Search. Search for the word *thunderbird*. Mozilla-Thunderbird should show up in the results. Right-click it and mark it for installation. Then click Apply.

**CLI instructions**: Go to Applications > Accessories > Terminal. Type ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
``` Your password is your user password.

See how much easier it is? In fact, once you get used to receiving command-line instructions, all you need is ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
``` The terminal will always be in the same place, but the GUI app won't (one time it'll be System > Administration > Synaptic Package Manager said:**
> People don't want to spend 95% of their time learning Linux, but USING it. The same could be said of any operating system, and this has nothing to do with the *design* of the Linux software. The problem is really (as I've stated thousands of times in these forums) that Windows comes **preinstalled** and **preconfigured**. If Windows users had to install their own operating systems, you know what they'd do? They'd call the Geek Squad. In fact, a lot of Windows users call the Geek Squad anyway. 

> Look at WIndows, you don't need to use their command line except for converting FAT partitions to NTFS. Yes, and see how many Windows users *still* don't know how to get basic functionality of their computers.

> We need to STAND OUT from those "other" distributions. We already do. Ubuntu has the best support and ships CDs for free. What makes Ubuntu my top choice is the support on these forums. That's the major reason I'm using it. Best Linux distro out of the box...? I'd probably say Mepis. But when I went to Mepis Lovers for help, no one could answer my questions. The questions got answered here... at the Ubuntu Forums. 

> Britney Spears doesn't know how to compile from source. Why should we be forced to use a command line? I don't know how to compile from source, either, and I bet Britney's a lot like me: email, internet, music, a little word processing. That's it.

> Do you think we need change, or should we keep it the way that it is now? I think it doesn't matter what you say. The Ubuntu developers are working hard as it is. Do you want to contribute money, code, HowTos? Or are you just going to whine? No one is saying, "Yeah, let's not improve anything."

By the way, your poll doesn't have an option that fits my opinion.

---

### Post by christhemonkey on 2006-01-24
I started off doing everything with GUI, but then wanted to learn how to use the terminal, so now dont really use GUI much at all!

---

### Post by BSDFreak on 2006-01-24
[quote=Stormy Eyes]Oh, jeez, not this nonsense again.[/quote]

It never ends...

There should be a sticky for this and all other threads should be merged into it for a month, after that time everyone who posts about it in another thread should be banned for a week.

---

### Post by fuscia on 2006-01-24
it *is* harder to pretend you're cool if just any retard can use it. i say **** 'em and make 9wm the default window manager.

---

### Post by Stormy Eyes on 2006-01-24
[QUOTE=fuscia]it *is* harder to pretend you're cool if just any retard can use it. i say **** 'em and make 9wm the default window manager.[/QUOTE]

You wimp. I say we make 'em install X manually, and use tcsh as the default shell!

---

### Post by aysiu on 2006-01-24
[QUOTE=BSDFreak]
There should be a sticky for this[/QUOTE] I wrote two threads that got stickied that address this issue, one in the Absolute Beginner forums, one in Community Chat.

The stickies aren't an effective deterent.

Bottom line, though: complaining just helps you blow off steam. There are only a few ways you can make Linux better, and the OP didn't do any of them in this thread:

1. Contribute code
2. File bug reports
3. Donate money
4. Contribute documentation
5. Help others learn to install and use Linux

There is no #6... whining.

---

### Post by Vlammetje on 2006-01-24
I'd like another option added to the poll: we do not need GUI for everything. A small dosis of command line is good for you!

---

### Post by tufkakf on 2006-01-24
Linux is userfriendly already, it's just picky about its friends.

---

### Post by BSDFreak on 2006-01-24
[quote=aysiu]I wrote two threads that got stickied that address this issue, one in the Absolute Beginner forums, one in Community Chat.

The stickies aren't an effective deterent.

Bottom line, though: complaining just helps you blow off steam. There are only a few ways you can make Linux better, and the OP didn't do any of them in this thread:

1. Contribute code
2. File bug reports
3. Donate money
4. Contribute documentation
5. Help others learn to install and use Linux

There is no #6... whining.[/quote]

That is too long to put in my sig, otherwise i would.

*applause*

---

### Post by BSDFreak on 2006-01-24
[quote=Stormy Eyes]You wimp. I say we make 'em install X manually, and use tcsh as the default shell![/quote]

ummm... what?

Is installing X hard and what is wrong with tcsh, it's a pretty fscking great shell.

---

### Post by tufkakf on 2006-01-24
[QUOTE=aysiu] complaining just helps you blow off steam. 
[/QUOTE]
And though the original post doesn't make much sense to me, to put it mildly, there's nothing wrong with blowing of steam.

[QUOTE=aysiu] 
There are only a few ways you can make Linux better, and the OP didn't do any of them in this thread[/QUOTE]
And the funny thing is, he doesn't have to, so...

---

### Post by Stormy Eyes on 2006-01-24
[QUOTE=BSDFreak]Is installing X hard and what is wrong with tcsh, it's a pretty fscking great shell.[/QUOTE]

I'm trying to think like a CLI-phobic Ex-Windows user who thinks everything should work like magic. It's not easy, so please cut me some slack.

---

### Post by fuscia on 2006-01-24
[QUOTE=Stormy Eyes]You wimp. I say we make 'em install X manually, and use tcsh as the default shell![/QUOTE]

**** that! make 'em imagine what X would look like. oh wait...no monitor. they have to remember what they entered into the console. all you need then is an old typewriter and some file cards.

---

### Post by tufkakf on 2006-01-24
Whoa, you guys are sssooooooooooooo 1333333333337!!!!11

Wow! *shudders*

---

### Post by mstlyevil on 2006-01-24
[QUOTE=BSDFreak]That is too long to put in my sig, otherwise i would.

*applause*[/QUOTE]

Will my new sig work?

---

### Post by mstlyevil on 2006-01-24
[QUOTE=fuscia]**** that! make 'em imagine what X would look like. oh wait...no monitor. they have to remember what they entered into the console. all you need then is an old typewriter and some file cards.[/QUOTE]

Ok it's official, you are the forum comedian. Keep it up and I will continue laughing hysterically

---

### Post by BSDFreak on 2006-01-24
[quote=Stormy Eyes]I'm trying to think like a CLI-phobic Ex-Windows user who thinks everything should work like magic. It's not easy, so please cut me some slack.[/quote]

Oh...

Ok... 

:D

---

### Post by BSDFreak on 2006-01-24
[quote=mstlyevil]Will my new sig work?[/quote]

Nice, i'd give credit where credit is due though. ;)

---

### Post by BSDFreak on 2006-01-24
[quote=fuscia]**** that! make 'em imagine what X would look like. oh wait...no monitor. they have to remember what they entered into the console. all you need then is an old typewriter and some file cards.[/quote]

Typewriter? Yeah, sure, make it USER FRIENDLY... a needle and some paper will suffice, they can punch readable assembly with that.

---

### Post by ardchoille on 2006-01-24
[QUOTE=Vlammetje]we should keep it the way it is now.

the fact that the command line is **perceived** to be this 'ugely incomprehensive complicated thing that you will never master', does not mean that it actually **is**.

In fact, I think anybody wanting to use linux should learn to use it well, and I think learning the command line (as I myself am doing bit by bit) is a vital part in that.

Finally. just because there's no GUI does **not** mean something isn't **easy**. These two just aren't synonymous. People need to learn that too. It's all part of the process imho.[/QUOTE]
Agreed, the command line is fast and powerful. In my opinion, if the user isn't using the command line at all then they are only benefitting from a fraction of the power of their distro.

I started out on KDE and avoided the command line like the plague, that was years ago. Today the only gui's I use are Firefox (can't figure out how to view graphics and flash in cli) and Evolution (haven't found a full PIM that is cli only). I do everything else on command line because it is fast and powerful. It took a bit of learning, yes, but doesn't everything?

Creating a gui for every single command line app would only add bloat to a distro - not to mention adding more reasons for something to go wrong and break.

So, make all the changes you want.. but don't take away my command line.

---

### Post by mstlyevil on 2006-01-24
[QUOTE=BSDFreak]Nice, i'd give credit where credit is due though. ;)[/QUOTE]

I tried but I ran out of charecters. I'll just say thank you to Asiyu here and hope hye approves. :)

---

### Post by aysiu on 2006-01-24
[QUOTE=mstlyevil]I tried but I ran out of charecters. I'll just say thank you to Asiyu here and hope hye approves. :)[/QUOTE] It's cool.

---

### Post by prizrak on 2006-01-24
The age of GUI? ROFL!!! HAHAHA!!!!! OMGWTFBBQ!!!!!!!!!!!!!!!!
Sorry, I HAD TO crack up about that. 
If it is the age of GUI then could someone explain to me, why Windows Vista is getting a new CLI shell? Why did MS (who are obviously doing very well on the OS market) decide that their OS needs a more powerful shell? Was it not because the users WANT a powerful tool such as a CLI? 
Oh and Ubuntu is very easy to use, I don't use the CLI at all on it unless I need to kill an unresponsive app (and only cause I'm too lazy to open up system monitor).
Another thing I cannot comperehend is why do people view having to learn how to use a computer a bad thing? I had to learn how to drive, and I also had to learn certain things about my car just for normal day to day operation. I needed to know what my recommended tire pressure is, what kind of tires to put on it, how often to change the oil and coolant. I also had to find the brand of gas that I prefer (that one is not as critical to "normal" people). 
Why is it different for computers? Even the most "natural" skills have to be learned at some point such as eating and speaking, something as involved as IT is expected to take some time.

---

### Post by public_void on 2006-01-24
> So, make all the changes you want.. but don't take away my command line.

Agreed. I love my command line to. Sometimes I can't be doing with a GUI just to navigate to some Directory far away (e.g. Windows My Documents) only to read a text file. I'm even lazy enough to open firefox from the CLI if I've finished doing sometime. IMO the CLI is the best thing about Linux, I'm surprised I lived without it in Windows.

---

### Post by Stormy Eyes on 2006-01-24
[QUOTE=prizrak]Why did MS (who are obviously doing very well on the OS market) decide that their OS needs a more powerful shell? Was it not because the users WANT a powerful tool such as a CLI? [/QUOTE]

It's because I blackmailed Ballmer. I've got pictures of him kissing the Devil's arse and threatened to sell them to the New York Times. Frankly, I thought Satan had higher standards.

---

### Post by awakatanka on 2006-01-24
Why can't it be simple best of both worlds? Theusers that are CLI junkies uses there CLI fingers and those that like a GUI more use the GUI.

Stupid resistance from some users, where the heck you are scared for? Nobody saying that it needs to be a windows clone but just add somethings to make it simple for somethings.

Using linux for some months now and i know my way around a bit now, but still hate CLI work for a lot of things it can be easier.

[http://www.kde-apps.org/content/show.php?content=17183](http://www.kde-apps.org/content/show.php?content=17183)

Something like that makes it a bit easier for some users. I want to save my fingers so they are soft and i can use them gently on my girl.

---

### Post by egon spengler on 2006-01-24
I'm not gonna bother reading this entire thread, just glancing at the stupidly biased poll options I can tell that this is another pointless and asinine thread. Then as I was clicking on quick reply I noticed **My posts are 100% useless! Guaranteed!** in the OP's sig and it all fell into place

---

### Post by egon spengler on 2006-01-24
[QUOTE=awakatanka]Why can't it be simple best of both worlds? Theusers that are CLI junkies uses there CLI fingers and those that like a GUI more use the GUI.

Stupid resistance from some users, where the heck you are scared for? Nobody saying that it needs to be a windows clone but just add somethings to make it simple for somethings.

Using linux for some months now and i know my way around a bit now, but still hate CLI work for a lot of things it can be easier.

[http://www.kde-apps.org/content/show.php?content=17183](http://www.kde-apps.org/content/show.php?content=17183)

Something like that makes it a bit easier for some users. I want to save my fingers so they are soft and i can use them gently on my girl.[/QUOTE]

This has surely been mentioned already but if you want to use Linux but with no cli then use mepis or pclinuxos. There are different distributions of Linux with different intentions, for example KnoppixSE has different intention to Arch which has different intentions to Puppy. If you want a purely cli distro then there are those who intend to fulfil that need. Use them. If for whatever reason you can't use mepis or pclinuxos then use Windows. If for whatever reason you can't use Windows then I don't know how to advise you further, I guess either stop using computers or stop whining

---

### Post by prizrak on 2006-01-24
[QUOTE=awakatanka]Why can't it be simple best of both worlds? Theusers that are CLI junkies uses there CLI fingers and those that like a GUI more use the GUI.

Stupid resistance from some users, where the heck you are scared for? Nobody saying that it needs to be a windows clone but just add somethings to make it simple for somethings.

Using linux for some months now and i know my way around a bit now, but still hate CLI work for a lot of things it can be easier.

[http://www.kde-apps.org/content/show.php?content=17183](http://www.kde-apps.org/content/show.php?content=17183)

Something like that makes it a bit easier for some users. I want to save my fingers so they are soft and i can use them gently on my girl.[/QUOTE]
See this is just the thing, I agree with ease of use (which GUI doesn't guarantee, try Xine-ui for an illustration) but sweeping posts like the OP's are useless. "Make Ubuntu easier with GUI". What exactly is hard? What doesn't have a GUI? How would you design the said GUI? If there is somekind of a hard to use interface to it already what is hard about it? 
Now I would agree to a post such as "Wireless w/ WPA is pretty difficult to set up and maintain because it is all CLI driven and the documentation for wpa_supplicant is crap" because I have experienced that and it really is difficult. The wpa_cli interface makes damn near no sense to someone who doesn't know much about WPA, and the GUI program is not included in the version that comes in the repos for some random reason. There is also no easy way to create network profiles (makes it a PITA if you are on a diff network than your main one). This would be an example of a well thought out complaint with some ideas. From what I hear Dapper will take care of those problems though so it's all good.

---

### Post by bloodborne on 2006-01-24
Linux is not Windows, and I embrace this fact as a long time Windows user, recent Linux convert. The biggest thing that makes it different for me is how Linux is completely devoted to spreading the ideas of free software and community, whereas MS is a corporation and their bottom-line always comes first. 

Honestly, the CLI isn't that scary (at least it wasn't for me), and I enjoy learning a little more about it everyday. Still, many of the commands are arcane to me and I usually just copy-paste instructions from the forum and nod my head.

---

### Post by matthew on 2006-01-24
There is no item worthy of my vote in the extremely biased poll options. 

I don't think Linux is all that difficult to learn for someone who is interested in doing so--you certainly DON'T have to "take time to read a 1,300 page book" to do so. You just have to want to, be interested, be willing to ask or look for help.

That said, I don't think we need to change an operating system to please an audience. If you build a good operating system an audience will come. If some don't like it I would kindly and politely suggest other options that might be more suited to their sensibilities. 

It's presumptious to come into a community and say, "You know what you need to do to attract more people like me?" My initial response is, "Please tell me so I can avoid doing so."

---

### Post by xequence on 2006-01-24
Ubuntu isnt hard.

You had to learn things to start using windows remember way back when? Same with linux.

---

### Post by skull_leader on 2006-01-24
I voted that Linux needs big changes, not because it isn't good enough right now, but because AFAIK that's what Linux is about. 

Ubuntu should definately keep striving for user-friendliness, but that doesn't mean they're not doing a good job already. As it stands, Ubuntu has more bases covered in it's "Add Applications" button than a Windows system with Office 2005, Norton, and any other general user CDs. It's just that improvement is the name of the project (actually the name is Humanity, but you know...:p ). Even if Ubuntu became easier to learn and use than Windows or MacOS, it still wouldn't be be time to stop working on it.

What people are probably getting into the most disagreement with is how exactly to go about doing it. More GUI shouldn't mean less CLI options, that's definately for sure.

---

### Post by matthew on 2006-01-24
[quote=skull_leader]I voted that Linux needs big changes, not because it isn't good enough right now, but because AFAIK that's what Linux is about. 

Ubuntu should definately keep striving for user-friendliness, but that doesn't mean they're not doing a good job already. As it stands, Ubuntu has more bases covered in it's "Add Applications" button than a Windows system with Office 2005, Norton, and any other general user CDs. It's just that improvement is the name of the project (actually the name is Humanity, but you know...:p ). Even if Ubuntu became easier to learn and use than Windows or MacOS, it still wouldn't be be time to stop working on it.

What people are probably getting into the most disagreement with is how exactly to go about doing it. More GUI shouldn't mean less CLI options, that's definately for sure.[/quote]Your attitude is definitely not what I was referring to in my mild-rant. I agree...in fact, I would say just about everything can be improved, not just in Linux. The definition of "improvement" is what I have such a strong reaction to. I always want to make my hardware do more cool stuff and do it in ways that are increasingly more convenient...that doesn't necessarily mean we need a CLI vs GUI battle. Both serve their purposes and there are times I would choose one over the other and the one I choose is not the same for every task.

---

### Post by Sirin on 2006-01-24
[QUOTE=prizrak]See this is just the thing, I agree with ease of use (which GUI doesn't guarantee, try Xine-ui for an illustration) but sweeping posts like the OP's are useless. "Make Ubuntu easier with GUI". What exactly is hard? What doesn't have a GUI? [/QUOTE]

Actually, I meant adding things that you can ONLY do on a CLI to the GUI. You can't double-click on a DEB file to install anything like you can do with RPMs. You HAVE to use the command line. Sure Synaptic and Adept may be the easiest installation client (behind Linspire's CNR IMO), but what about files that **aren't** in the repositories? 

[Quote=egon spengler]I'm not gonna bother reading this entire thread, just glancing at the stupidly biased poll options I can tell that this is another pointless and asinine thread. Then as I was clicking on quick reply I noticed **My posts are 100% useless! Guaranteed!** in the OP's sig and it all fell into place[/quote]

It seems that you have never heard of humor.
> 
*hu·mor (hy&#363;'m&#601;r)* pronunciation
*n.*

The quality that makes something laughable or amusing; funniness;

---

### Post by greenway on 2006-01-24
The CL is the key feature of Linux and of pretty much every decent distro out there, take it away (or take it from it's prominent position) and Linux users will start looking for another OS/distro.

Linux is for Linux users... If you want to use it, take the effort of becoming one and it will pay off in the end...

---

### Post by Sp@z on 2006-01-24
Well I cant see that this is a USELESS thread...and there are so many before it, but I am rather new to the forums and never seen them.......so it is a first for me and other n00bs I suppose, but hey you guys started the flame war, not me.......Ubuntu is pretty easy as it is.I despise the command line only because I fear the unknown, in time I will either learn it or go back to windows. Linux can still be linux, even if it starts looking like winndows, I use Linux for secruity and Windoze will NEVER have that.....

---

### Post by aysiu on 2006-01-24
[QUOTE=Sirin]Actually, I meant adding things that you can ONLY do on a CLI to the GUI. You can't double-click on a DEB file to install anything like you can do with RPMs. You HAVE to use the command line.[/quote] So use Mepis. In Mepis, you click on a .deb and it opens up KPackage, which installs the .deb. > Sure Synaptic and Adept may be the easiest installation client (behind Linspire's CNR IMO), but what about files that **aren't** in the repositories? For the most part, only Windows power users care about such things. The repositories suit the needs of most users (like me) who just want to do ordinary things--listen to music, play dumb games (Tetris and such), surf the internet, email, and do light word processing.

Ordinary users do not install operating systems. As a matter of fact, they rarely install software; and when they do, they do not always want the latest versions. I don't see any of my co-workers who have Firefox 1.0.2 clamoring for version 1.5. In fact, they don't even know there is a new version.

You want Linux to cater to Windows power users who have **sophisticated needs** and **low skills/ desire to learn**. Well, that's not where it's at. Either dumb down your needs or spruce up your skills. It's not that hard to copy and paste a few commands.

---

### Post by fuscia on 2006-01-25
[QUOTE=BSDFreak]Typewriter? Yeah, sure, make it USER FRIENDLY... a needle and some paper will suffice, they can punch readable assembly with that.[/QUOTE]

**** all that shit! let's go pure old school...

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxbc.jpg[/IMG]

---

### Post by Sirin on 2006-01-25
> **aysiu]So use Mepis. In Mepis, you click on a .deb and it opens up KPackage, which installs the .deb.[/quote]

Look at this. So I have to get a whole new distribution just to install something easily? There are distributions everywhere. Why do people have to install distributions that meets their needs? "Linspire has something that you need that isn't in Fedora, but Fedora has something that you need that isn't in Linspire." Why do people need to switch entire OSes just to get 1 new thing? I mean, isn't there one distro for everything? Sometimes people don't like switching from one distro to another. For example, why should people start off with a "beginner" distro and then switching to an "intermediate" distro? If I were advised to start off with a Mac before going to Linux for PPC, I'd probaly just stick with the Mac because of it's ease of use. Isn't Ubuntu for home users? Why don't we make it "easy" for home users? Besides, it doesn't say in the minimum requirements that a Linux geek is required. My sister and mother had me come help them 69% of the time they used Ubuntu. For Windows, 20% of the time. For Mac OS X which is based on UNIX, only **5%**, and that was showing them how to get used to the Mac enviroment. We need to reduce that need of support to at most 30%. We can start by focusing on the home user. Linspire may be the easiest distro, but I'm sure as hell not paying USD$100. Linus Torvalds aimed Minix (Early codename for the now-called Linux) for the **DESKTOP**. Why can't Linux be for the desktop, and for the people who just plain want simplicity? To many (not me however, but many others besides me), Linux is just a time portal to the DOS days.

> For the most part, only Windows power users care about such things. The repositories suit the needs of most users (like me) who just want to do ordinary things--listen to music, play dumb games (Tetris and such), surf the internet, email, and do light word processing.

Maybe a user was familiar with Opera when they were using WIndows and were told that it was also for Linux. Opera isn't in the repos. Now they have to learn the unfamiliar Firefox enviroment.

[quote]
Ordinary users do not install operating systems. As a matter of fact, they rarely install software said:**
> 

If they don't install operating systems, then they didn't install Ubuntu.

[quote]
You want Linux to cater to Windows power users who have **sophisticated needs** and **low skills/ desire to learn**. Well, that's not where it's at. Either dumb down your needs or spruce up your skills. It's not that hard to copy and paste a few commands.

I've been with Linux and it's CLI for some time now. Windows power users who switch to Ubuntu do take time to learn the command line if they want to use Linux. We're talking about the "I have never used the Windows command line before and I'm tired of viruses, spyware and updating WIndows. I want to have an easy to use desktop that doesn't take a geek to install software" group. Sure, it isn't hard to copy and paste a "few" commands, but what happens when you find out you'll be "copying and pasting" for the whole time you use Ubuntu just to install things? Why couldn't it be as easy as double-clicking and following a simple Wizard like WIndows, or dragging and dropping into your apps folder like Mac? Why do you have to use the command line for 50% of things used in Linux? The only valid explanation was, "Linux is not WIndows". Linux was out at the time Windows NT debuted. Look at how easy it is now with XP. In 2001, Apple switched to UNIX, and look how far they got. Sure, they have a command line, but you were never **forced** to use it.

---

### Post by mstlyevil on 2006-01-25
[QUOTE=Sirin]I've been with Linux and it's CLI for some time now. Windows power users who switch to Ubuntu do take time to learn the command line if they want to use Linux. We're talking about the "I have never used the Windows command line before and I'm tired of viruses, spyware and updating WIndows. I want to have an easy to use desktop that doesn't take a geek to install software" group. Sure, it isn't hard to copy and paste a "few" commands, but what happens when you find out you'll be "copying and pasting" for the whole time you use Ubuntu just to install things? Why couldn't it be as easy as double-clicking and following a simple Wizard like WIndows, or dragging and dropping into your apps folder like Mac? Why do you have to use the command line for 50% of things used in Linux? The only valid explanation was, "Linux is not WIndows". Linux was out at the time Windows NT debuted. Look at how easy it is now with XP. In 2001, Apple switched to UNIX, and look how far they got. Sure, they have a command line, but you were never **forced** to use it.[/QUOTE]

Automatix takes care of most of the issues you are talking about. Except for wireless support I can see no reason for a new person to touch the command line in Ubuntu once they install Automatix. Most new users do basic things with their computers like E-Mail, Web surfing, sharing photos, downloading music and simple games. Automatix configures a Ubuntu install automatically through a GUI based installer just for these things. My point in my previous post (which has obviously been ignored.) is that people are already working on this and the application already exist. You still have failed to show us how it is not easy for a new Ubuntu user to install all of these apps without extensive use of the CLI. Ubuntu can not come with many of these thing out of the box for legal reasons. What I am gathering from your post is that you want all these thing already enabled at install. This is not going to happen because then Ubuntu would have to charge to pay the license fees for the propietary software. That would include if they enabled the downloading and instalation of these packages through the repos by default.

You need to be more specific on what programs and packages that are not covered under Automatix and Synaptic that require the CLI to install. Otherwise I believe the GUI based application you keep talking about already exist.

---

### Post by Iandefor on 2006-01-25
Meh... I voted that Linux needs big changes. But I don't really care about the rest of that option. Linux simply needs to change such that it gets more mindshare, imho (not necessarily convert users... just let them know about other options than Windows). But that doesn't necessarily mean making it more "user-friendly", as you put it. Linux is user-friendly already. The big stumbling block a lot of people have moving to Linux from Windows is the use of two different user interfaces. Anyone who uses the CLI for a little will realize it's not at all difficult; just because it works on a different principle than the GUI doesn't make it difficult.

Someone mentioned Automatix earlier; Automatix is a godsend, but for a new user, they're not necessarily going to be in a position to know about it. Just a thought.

---

### Post by Sirin on 2006-01-25
Nevermind.

---

### Post by midwinter on 2006-01-25
I'd look to another distro rather than trying to change this one.  That's what i'm doing as Ubuntu is a little TOO 'user friendly' for my tastes.  However, I do think Ubuntu is heading in the direction you want so I wouldn't concern yourself too much...

---

### Post by tufkakf on 2006-01-25
[QUOTE=aysiu]So use Mepis. In Mepis, you click on a .deb and it opens up KPackage, which installs the .deb.  
[/QUOTE]
Hm, or why not simply acknowledge that this is something missing from Ubuntu? After all, that's what the ubuntu devs did and that's what will bring us gdebi in dapper. 

[QUOTE=aysiu]
For the most part, only Windows power users care about such things. [/QUOTE]
Bull, I don't even use Windows and I care about such things. Why, because I want my OS to be as efficient as possible. Did it ever occur to you that there are debs for ubuntu out there that are not in the repositories and that require you to install them with dpkg -i and then installing their deps manually (or most of the time simply using apt-get -f install)?
Could you tell me one reason why having a tool that does this in a more convenient way for me should be considered a bad thing?

---

### Post by awakatanka on 2006-01-25
> This has surely been mentioned already but if you want to use **Linux but with no cli** then use mepis or pclinuxos. There are different distributions of Linux with different intentions, for example KnoppixSE has different intention to Arch which has different intentions to Puppy. If you want a purely cli distro then there are those who intend to fulfil that need. Use them. If for whatever reason you can't use mepis or pclinuxos then use Windows. If for whatever reason you can't use Windows then I don't know how to advise you further,** I guess either stop using computers or stop whining**

For those people that say use mepis, pclinuxos our linspire they still have needs for CLI Commands if needed, CLI can be a powerfull tool but some task are faster and easier with a GUI. Nobody saying that CLI has to be removed but they say sometasks can be done with GUI also. Its simply not true that no distro can do it without cli. So don't say they don't have CLI

[http://forum.linspire.com/viewtopic.php?t=418818&sid=d822e4189c600e1e9d48f6f17b559da7](http://forum.linspire.com/viewtopic.php?t=418818&sid=d822e4189c600e1e9d48f6f17b559da7)
[http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=4939&forum=9](http://www.mepislovers.org/modules/newbb/viewtopic.php?topic_id=4939&forum=9)
[http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=8230&forum=57](http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=8230&forum=57)

Whining so if some one has some critics he whine's? So nobody may have a opinion only you may have?

> Ubuntu is a complete Linux-based operating system, freely available with both community and professional support. It is developed by a large community and we invite you to participate too!

**The Ubuntu community is built on the ideas enshrined in the Ubuntu Manifesto: that software should be available free of charge, that software tools should be usable by people in their local language and despite any disabilities, and that people should have the freedom to customise and alter their software in whatever way they see fit.**

These freedoms make Ubuntu fundamentally different from traditional proprietary software: not only are the tools you need available free of charge, you have the right to modify your software until it works the way you want it to

It says everyone is free to share there idea's and make it usable for everyone, Stop kicking people away to windows our other distro's and make ubuntu a distro they also can use. With both options CLI and GUI for tasks that can be done in GUI. People can make there own choose what they prevere.

---

### Post by egon spengler on 2006-01-25
[QUOTE=Sirin]It seems that you have never heard of humor.[/QUOTE]

Of course I have. It just wasn't funny. That said it is true that many a true word is spoken in jest

[QUOTE=awakatanka]For those people that say use mepis, pclinuxos our linspire they still have needs for CLI Commands if needed, CLI can be a powerfull tool but some task are faster and easier with a GUI. Nobody saying that CLI has to be removed but they say sometasks can be done with GUI also. Its simply not true that no distro can do it without cli. So don't say they don't have CLI[/QUOTE]

Guess what, in Windows that well known barometer of user friendlyness there are also some things that have to be done at the command prompt, in fact there are also some things that have to be done (or at least are 10x easier to do) through typing into the run box. OMG!!111 TYPING???!!! THAT SUXORZ. If you use a computer you *may* have to touch the keyboard at some point, I'm sorry to break it to you.

[QUOTE=awakatanka]Whining so if some one has some critics he whine's? So nobody may have a opinion only you may have?[/QUOTE]

That's not quite what I said though is it? I didn't say that voicing an opinion is  whining what I said is that if ubuntu doesn't meet your needs then why stick with it? I can safely say that I wouldn't persevere with it if I didn't find it could do all that I need. There are plenty of other OSes out there, switch to one that is better for you. What you need to bear in mind though is that no OS is perfect, as the saying goes you can't please all of the people all of the time, at some point if no OS on earth meets your needs then you are going to have to suck it up and get on with life. At some point you may have to compromise (life is full of compromise my friend) and just accept that whatever OS you settle on is the best (or least terrible) you can get. That would be the point where I would say it's time to stop whining and just make the best of it.

[QUOTE=awakatanka]It says everyone is free to share there idea's and make it usable for everyone, Stop kicking people away to windows our other distro's and make ubuntu a distro they also can use. With both options CLI and GUI for tasks that can be done in GUI. People can make there own choose what they prevere.[/QUOTE]

The fact remains, if you are the type of user that mepis and pclinux are aiming to cater for then you may well be best suited using one of those two distros. You say stop kicking people away but at the same time you need to realise that ubuntu has it's own particular aims and ideals (I don't know what they are but I know it has them) and it can't be all things to all people. In light of that recommending to people that they try something that tries harder to meet their needs isn't really that off key is it? Actually one thing I do know abuot ubuntu is that they aim to promote libre software, meanwhile the #1 complaint is that there is no built in mp3 support. What do you sugggest that do at this impasse?

a) stick to their ideals
b) throw away their ideals because ubuntu has to be all things for all people

---

### Post by tufkakf on 2006-01-25
[QUOTE=egon spengler]
Guess what, in Windows that well known barometer of user friendlyness there are also some things that have to be done at the command prompt, in fact there are also some things that have to be done (or at least are 10x easier to do) through typing into the run box. OMG!!111 TYPING???!!! THAT SUXORZ. If you use a computer you *may* have to touch the keyboard at some point, I'm sorry to break it to you.
[/QUOTE]
First off, I really don't think Windows is very userfriendly, at least not to this particular user here.
Second, the poster you answered to didn't claim that the CLI sux, what he pointed was that other distros provide gui tools for tasks that ubuntu doesn't provide gui tools for. Now pointing out that there are also things in Windows you have to do from the command prompt doesn't change this simple fact and writing in caps and 1337 speak doesn't either, so what exactly is your point here?

[QUOTE=egon spengler]
That's not quite what I said though is it? I didn't say that voicing an opinion is  whining what I said is that if ubuntu doesn't meet your needs then why stick with it? 
[/QUOTE]
So, how about people who like ubuntu, whos needs are met by ubuntu most of the time, but who still think that there are areas where ubuntu could and should improve? Did it ever occur to you that people point out shortcomings of ubuntu not because they don't like, but because they like it and want it to improve?

[QUOTE=egon spengler]
I can safely say that I wouldn't persevere with it if I didn't find it could do all that I need. There are plenty of other OSes out there, switch to one that is better for you. What you need to bear in mind though is that no OS is perfect, as the saying goes you can't please all of the people all of the time, at some point if no OS on earth meets your needs then you are going to have to suck it up and get on with life. At some point you may have to compromise (life is full of compromise my friend) and just accept that whatever OS you settle on is the best (or least terrible) you can get. That would be the point where I would say it's time to stop whining and just make the best of it.
[/QUOTE]
Why do you insist on accusing every one who voices something critical about Ubuntu of whining? And why do you think Linux in general and Ubuntu is improving? Hint, it's not because people simply accept what's there.

[QUOTE=egon spengler]
The fact remains, if you are the type of user that mepis and pclinux are aiming to cater for then you may well be best suited using one of those two distros. You say stop kicking people away but at the same time you need to realise that ubuntu has it's own particular aims and ideals (I don't know what they are but I know it has them) and it can't be all things to all people. In light of that recommending to people that they try something that tries harder to meet their needs isn't really that off key is it? 
[/QUOTE]
Pointing out to people that other distributions might at the moment be a better choice for them certainly is a good thing, but telling people who want to improve Ubuntu to get lost is.
And mentioning Ubuntu's aims and ideals while admitting that you don't know what they are but at the same time using them to shut up critics really isn't all that convincing.

[QUOTE=egon spengler]
Actually one thing I do know abuot ubuntu is that they aim to promote libre software, meanwhile the #1 complaint is that there is no built in mp3 support. What do you sugggest that do at this impasse?
[/QUOTE]
Oh, there probably isn't all that much Ubuntu devs can do about it. However, that of course doesn't mean that there aren't other areas where Ubuntu can and should improve, does it?
And btw., the codecs fluendo wants to provide in the future could improve the situation significantly.

[QUOTE=egon spengler]
a) stick to their ideals
b) throw away their ideals because ubuntu has to be all things for all people[/QUOTE]
Blah. Nobody talked about throwing away ideals.

---

### Post by awakatanka on 2006-01-25
> 
Guess what, in Windows that well known barometer of user friendlyness there are also some things that have to be done at the command prompt, in fact there are also some things that have to be done (or at least are 10x easier to do) through typing into the run box. OMG!!111 TYPING???!!! THAT SUXORZ. If you use a computer you *may* have to touch the keyboard at some point, I'm sorry to break it to you.  Tell me when? I never ever have to use the commandline in windows, only in there early versions i had to use it, in windows xp desktop version i never had to use the command. We talkink about desktop version and not server versions. And i don't say you never have to use only give the option for users that want it and if it can be done with a gui.


> 
That's not quite what I said though is it? I didn't say that voicing an opinion is  whining what I said is that if ubuntu doesn't meet your needs then why stick with it? I can safely say that I wouldn't persevere with it if I didn't find it could do all that I need. There are plenty of other OSes out there, switch to one that is better for you. What you need to bear in mind though is that no OS is perfect, as the saying goes you can't please all of the people all of the time, at some point if no OS on earth meets your needs then you are going to have to suck it up and get on with life. At some point you may have to compromise (life is full of compromise my friend) and just accept that whatever OS you settle on is the best (or least terrible) you can get. That would be the point where I would say it's time to stop whining and just make the best of it. No OS is prefect true but it can be as easy as possible for users that don't know as much as you and i.


> 
The fact remains, if you are the type of user that mepis and pclinux are aiming to cater for then you may well be best suited using one of those two distros. You say stop kicking people away but at the same time you need to realise that ubuntu has it's own particular aims and ideals (I don't know what they are but I know it has them) and it can't be all things to all people. In light of that recommending to people that they try something that tries harder to meet their needs isn't really that off key is it? Actually one thing I do know abuot ubuntu is that they aim to promote libre software, meanwhile the #1 complaint is that there is no built in mp3 support. What do you sugggest that do at this impasse?
So people can't discuss about things they like to be added to the distro? Without user input it      wouldbe hard to know the users want. And this isn't the place for input but its the place to discuss it and find users that think the same.

> Ideas and Feedback

Help steer the direction we take Ubuntu, by describing your vision and ideas for a better server and desktop OS and application stack.

    *

      Participate in discussions and brainstorming on the Ubuntu Wiki where we work on the fastest-moving documents before they are ready for publication on the main web site.
    *

      Add your ideas to the Idea Pool for features you'd like to see in Ubuntu, products, marketing suggestions or any other ideas you'd like to add here.

Remember, in the open source world, code counts more than talk so try to find friends or link up with people who can help turn your vision into reality, or start cutting the code yourself if that's your line of interest.


The discussion isn't about mp3 our other codecs but about user friendlyness on somethings

---

### Post by egon spengler on 2006-01-25
[QUOTE=tufkakf]First off, I really don't think Windows is very userfriendly, at least not to this particular user here.
Second, the poster you answered to didn't claim that the CLI sux, what he pointed was that other distros provide gui tools for tasks that ubuntu doesn't provide gui tools for. Now pointing out that there are also things in Windows you have to do from the command prompt doesn't change this simple fact and writing in caps and 1337 speak doesn't either, so what exactly is your point here?[/QUOTE]

Actually what he said was that no distro escapes having to use the cli. My response was that touching the keyboard is an unavoidable consequence of using a computer. It seems to be uniquely an expectation of Linux that you never have to touch the keys under any circumstances. If you use Windows and large avi files are not previewing corretly and you have to unregister a dll through the prompt or the run box I doubt that inspires waves of criticism. In Windows there are many registry hacks/fixes to improve/modify performance, I don't really recall ever hearing Windows get criticised for that (I mean the actual having to type, I hear them get criticised for implementing the registry). Sometimes you may have to use the keyboard of your computer, if that is an issue for someone then I don't think that ubuntu is the distro best suited for them. Personally I think it is a tremendous urban myth that ubuntu is newbie friendly, look how many people are disapointed and frustrated with ubuntu, I think we would be doing everyone a favour if we directed new users and users who prefer gui as much as possible towards a distro that at least *tries* to cater for them. Honestly I think ubuntu doesn't even seem to try to be especially newbie friendly, as you say yourself ubuntu is missing many common gui tools of other distros. It doesn't seem to be their priority to move in this direction. And if it IS their priority then they are doing a woeful job

[QUOTE=tufkakf]Why do you insist on accusing every one who voices something critical about Ubuntu of whining? And why do you think Linux in general and Ubuntu is improving? Hint, it's not because people simply accept what's there.[/QUOTE]

Goodness, let me try restating it again. It's not whining to say that you don't like certain things about ubuntu. What I was saying is that if it does not work for you then try something else, if nothing on the planet meets your demands then at that point you may well have to say "oh well, this is as good as it gets"


[QUOTE=tufkakf]Pointing out to people that other distributions might at the moment be a better choice for them certainly is a good thing, but telling people who want to improve Ubuntu to get lost is.[/QUOTE]

And I told who to get lost? I'm telling people the same thing that I would tell myself, if ubuntu didn't work for me then I wouldn't persevere with it. What possible reason other than masochism is there to do that?


[QUOTE=tufkakf]And mentioning Ubuntu's aims and ideals while admitting that you don't know what they are but at the same time using them to shut up critics really isn't all that convincing. 

Nobody talked about throwing away ideals.[/QUOTE]

It was an example my friend of how if distro a has decided it wants to aim for a specific goal should they not be allowed to continue in that vein? If i start demanding that KnoppixSE ditch flux box for e17 is that a valid request on my part or should the makers of a distribution not be allowed to have the final say over which direction they move in? Of course listen to user feedback but I personally I don't feel that developers of a particular distro are ultimately obligated to put user feedback before whatever their own goals for their distribution are

---

### Post by egon spengler on 2006-01-25
[QUOTE=awakatanka]No OS is prefect true but it can be as easy as possible for users that don't know as much as you and i.[/QUOTE]

Of course every OS *can* be as easy as possible for users who are not interested in learning too much about the OS. What I am asking though is it the responsibility of *every* OS to try and make themselves as easy as possible? I know that Arch, Gentoo and LFS aren't designed to be especially userfriendly for those new to Linux, I would argue that it is the perrogative of the developers to continue in that vein. Personally I would never recommend ubuntu to anyone as a newbie distro because although I'm new to Linux and found it easy to get to grips with, from these forums I see that not everyone had the same experience.

[QUOTE=awakatanka]So people can't discuss about things they like to be added to the distro? Without user input it wouldbe hard to know the users want. And this isn't the place for input but its the place to discuss it and find users that think the same.

The discussion isn't about mp3 our other codecs but about user friendlyness on somethings[/QUOTE]

Of course user feedback is vital, really though look at the options in this thread, was it a "ubuntu needs improvement here, here and there" thread or a "ubuntu is completely wrong and only a fool disagrees" thread? C'mon man, you don't need to read a 1,300 page manual to use ubuntu and you don't need a Linux nerd to guide you through every stage of using it. 

As far as the mp3 thing, it was an example. I was asking you whether in all instances the developers should be forced to bow to popular demand or whether they might be permitted to make the distro as they see fit. To be honest I doubt you didn't understand exactly what I meant

---

### Post by Arktis on 2006-01-25
All this amounts to is whining about having to use the CLI.  I will now state some stunningly obvious things in the hopes of ending this whole ridiculous set of ideas.  I will certainly fail at erradicating this plague of illogic...

A CLI and a GUI are merely two different ways of interacting with your computer.  The CLI is far more efficient for many things as long as you understand what you're doing, how things work, what commands to use and how to use them.  The CLI is *not* outdated or inferiror to a GUI.

But a GUI tool is easier, right?  There's not really any learning needed except for what to click on and in what order.  So it's automaticly better somehow.  So now a GUI should be used for everything so that nobody ever has to touch the CLI...   Doesn't this seem like a negative trend in thought?

And one more thing: I'm not a die-hard Linux CLI zealot.  I'm a Gnome user.  I like my simple GUI.  I just happen to also recognize the advantages of the CLI and like to make use of it, too.  Just not for everything.  Just as I think that **[color=red]A GUI SHOULD NOT BE USED FOR EVERYTHING[/color]**.

But in the end, if people wish to do less learning and less thinking and demand ways to empower them to that end, you can't stop them.  Let them shoot themselves in the foot.

---

### Post by Vlammetje on 2006-01-25
[QUOTE=awakatanka]Tell me when?[/QUOTE]

Things like a tracert or ping for example

---

### Post by kenweill on 2006-01-25
I guess it would be much easier of Ubuntu Wiki will be included the the distribution. So that offline users as well can have a solutions to their problem when they have no internet connection.
Like Windows, it has comprehensive help files. It even have a troubleshooting guide.
What I like most with Windows is, if you are offline, and you have a problem, help is always available from the start menu. But in Ubuntu, don't have one. Or haven't found one. I still need to be online and post the forum or search the problem to the internet.

---

### Post by egon spengler on 2006-01-25
[QUOTE=kenweill]I guess it would be much easier of Ubuntu Wiki will be included the the distribution. So that offline users as well can have a solutions to their problem when they have no internet connection.
Like Windows, it has comprehensive help files. It even have a troubleshooting guide.
What I like most with Windows is, if you are offline, and you have a problem, help is always available from the start menu. But in Ubuntu, don't have one. Or haven't found one. I still need to be online and post the forum or search the problem to the internet.[/QUOTE]

I think better documentation in the distro would help. One problem though, it seems to me (I've only seen breezy actually get released) that after a release the documentation for the new release builds up over the next few months and so at the time of release there might not be any version specific wiki content. Of course a lot of the stuff from previous versions will still work though

---

### Post by tufkakf on 2006-01-25
[QUOTE=Arktis] The CLI is *not* outdated or inferiror to a GUI.
[/QUOTE]
And nobody said it was. Strawman, meet Arktis. Arktis, meet Strawman.

[QUOTE=Arktis]
But in the end, if people wish to do less learning and less thinking and demand ways to empower them to that end, you can't stop them.  Let them shoot themselves in the foot.[/QUOTE]
Believe it or not, but providing tools that make things easier is kind of the idea behind computers. And learning in and of itself isn't a merit, if this learning is required because something that could also be achieved much easier has to be done in a complicated, non-obvious way.

---

### Post by Sirin on 2006-01-25
[QUOTE=kenweill]I guess it would be much easier of Ubuntu Wiki will be included the the distribution. So that offline users as well can have a solutions to their problem when they have no internet connection.
Like Windows, it has comprehensive help files. It even have a troubleshooting guide.
What I like most with Windows is, if you are offline, and you have a problem, help is always available from the start menu. But in Ubuntu, don't have one. Or haven't found one. I still need to be online and post the forum or search the problem to the internet.[/QUOTE]

And Windows XP also comes with a [Booklet](http://www.spartantech.com/img/productpics/WINXP%20Pro%20Booklet%20cvr%20w_CD.jpg) that shows you how to use it before you actually use it. With Ubuntu, you have to USE it to learn it. Why doesn't Ubuntu come with booklets? :(

---

### Post by midwinter on 2006-01-25
[QUOTE=Sirin]Why doesn't Ubuntu come with booklets? :([/QUOTE]

Maybe because it's free.  I think it's incredible that they even send out free cds.  

Ubuntu comes with help files by the way... (System - Help).  Lots of man files too ;)

---

### Post by fuscia on 2006-01-25
something just occured to me...aren't macs pretty much unix with a gui for retards?

---

### Post by Sirin on 2006-01-25
[QUOTE=fuscia]something just occured to me...aren't macs pretty much unix with a gui for retards?[/QUOTE]

Retards? No. If it were for the mentally challenged, there would be a "click here, now click here, oops, don't forget to click here!" voice bugging you every 0.1 nanoseconds.

---

### Post by Iandefor on 2006-01-25
[quote=fuscia]something just occured to me...aren't macs pretty much unix with a gui for retards?[/quote] Essentially. It uses a POSIX-compliant kernel. It also uses Aqua... which, in my experience, is liked primarily by technophobes.

---

### Post by aysiu on 2006-01-25
I think some people are missing the point.

I'm not denying that Ubuntu can improve. Not only *can* it improve--it's *constantly* improving.

I do believe wholeheartedly, though, that **this thread does not help Ubuntu improve**. Its "criticisms" are really just whining--which, as I stated earlier, is fine if you just want to blow off steam and vent a little.

If you want to **make a difference**, starting a thread proclaiming, "Ubuntu needs to do this, this, and this" doesn't help.

These things help, and I believe I stated them before, but a few people weren't paying attention, so I'll state them again:

1. File a bug report.
2. Donate money.
3. Contribute documentation.
4. Help new users.
5. Improve the code yourself (be a developer).

If you're not doing one of those five things, then you're not really helping to improve Ubuntu, are you? That's the bottom line.

And it really isn't that big a deal to switch to another distro. I used to distro swap all the time. I ended up trying about twelve or fourteen different distros just for fun. It's not that big a deal. Copy over a few hidden directories in your /home folder, and it's pretty much the same thing.

---

### Post by prizrak on 2006-01-25
> Linus Torvalds aimed Minix (Early codename for the now-called Linux) for the DESKTOP.
I suggest learning before saying things. Minix was created by AST (Andrew S. Tenenbaum) as a teaching aid to his Computer Science students. It was a microkernel OS that had nothing to do with Linux. Linus created Linux because he wasn't satisfied with Minix's functionality, while it's true that he wrote it on a desktop (a 386 if I remember correctly) he never had any intentions for it. He wanted to create a POSIX compliant kernel and he did. He posted it to the net just for the hell of it. He never thought it was gonna get big. 
--Source: Just For Fun

We acknowledge that there are things that are missing from Ubuntu. The thing is that at the moment the stabel release is Breezy that lacks certain things people might want. Dapper will include alot of new stuff including double clicking to install .debs and autopackage (from what I hear). If people are willing to wait for Dapper there is little reason to bitch about Ubuntu not having certain stuff because Breezy won't be updated and Dapper will most likely include things that are wanted. If you are not willing to wait then a different distro would be better.

---

### Post by tufkakf on 2006-01-25
[QUOTE=aysiu]
If you want to **make a difference**, starting a thread proclaiming, "Ubuntu needs to do this, this, and this" doesn't help.
[/QUOTE]
Could you show me exactly where someone said it would?
Could you point out to me where exactly I can find the rule that threads like this have to help?
Can you tell me how a thread whining about windows users does fit into this picture? How does it improve Ubuntu exactly?

Thanks.

---

### Post by earobinson on 2006-01-25
my vote for my gui because ubuntu is "linux for human beings" so anyone should be able to use it.

---

### Post by BSDFreak on 2006-01-25
[quote=fuscia]**** all that shit! let's go pure old school...

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxbc.jpg[/IMG][/quote]

[IMG]http://asp.budo-fitness.se/img/upload/2336.jpg[/IMG]

---

### Post by BSDFreak on 2006-01-25
[quote=earobinson]my vote for my gui because ubuntu is "linux for human beings" so anyone should be able to use it.[/quote]

Seriously, if ubuntu is "linux for human beings" then what is Slackware or SuSe? Linux for aliens and cats and dogs?

I think the meme is stupid.

---

### Post by BSDFreak on 2006-01-25
[quote=fuscia]something just occured to me...aren't macs pretty much unix with a gui for retards?[/quote]

Based on FreeBSD with the Darwin additions.

It's so much *nix that you could run tcsh on it natievely. ;)

---

### Post by BSDFreak on 2006-01-25
[quote=Iandefor]Essentially. It uses a POSIX-compliant kernel. It also uses Aqua... which, in my experience, is liked primarily by technophobes.[/quote]

Aqua is the damn theme, nothing more, the engine is still Darwin.

You don't change the OS much by switching from Plastik to baghira in KDE and you could use both with Darwin.

It's a mach implementation of the 4.4BSD kernel, somewhat customized.

---

### Post by BSDFreak on 2006-01-25
[quote=prizrak]I suggest learning before saying things. Minix was created by AST (Andrew S. Tenenbaum) as a teaching aid to his Computer Science students. It was a microkernel OS that had nothing to do with Linux. Linus created Linux because he wasn't satisfied with Minix's functionality, while it's true that he wrote it on a desktop (a 386 if I remember correctly) he never had any intentions for it. He wanted to create a POSIX compliant kernel and he did. He posted it to the net just for the hell of it. He never thought it was gonna get big. 
--Source: Just For Fun[/QUOTE]

It's mostly correct so i'll let it slide with a comment that Linus didn't "want to creat a POSIX compliant kernel" his aim was to create a kernel that was modular, not neccessarily POSIX compliant (and if you take the time to look at the earlier versions of the kernel you'll realize that it was not POSIX compliant) and as his work gained rep he was approached by the FSF.

He really didn't want to release it under the GPL though, but he did, and as it stands now it will forever be free since even if it's CS'd there will be a forked FOSS version.

Take a look at XFree86 for references of how well restrictions to licences do with FOSS support.

The minix kernel isn't all shitty though, it's a fsckload better than anything GNU has managed to produce for a kernel (the hurd is a joke at best).

I think i'm getting a tad carried away here, i just had a strange discussion with some FSF communists so you'll have to excuse me. :D

---

### Post by tufkakf on 2006-01-25
[QUOTE=BSDFreak]
I think i'm getting a tad carried away here, i just had a strange discussion with some FSF communists so you'll have to excuse me. :D[/QUOTE]
No, I won't. Calling people communists to insult them is not only stupid, but also shows that in the case of the FSF you don't know flying shit about what you talking about, as do your uninformed ramblings about hurd, minix and linux.

Stop emberassing yourself!

---

### Post by commodore on 2006-01-25
GUI is anal sex.

---

### Post by aysiu on 2006-01-25
[QUOTE=tufkakf]Could you show me exactly where someone said it would?[/quote] The very fact that people are arguing (multiple times) that Ubuntu needs to do certain things and asking "Why can't Ubuntu do X, Y, and Z?" multiple times in multiple posts indicates a sense of trying to make a difference. One post that says, "Geez, I wish Ubuntu would do X, Y, and Z" that's followed up later with, "Yeah, I was just venting. I know I'm not making a difference" wasn't what I saw at all.

> 
Could you point out to me where exactly I can find the rule that threads like this have to help? They don't. I just want whiners to acknowledge they're whining.

> Can you tell me how a thread whining about windows users does fit into this picture? How does it improve Ubuntu exactly? It doesn't. But it doesn't claim to either. This thread has the appearance of wanting to make change.

---

### Post by tufkakf on 2006-01-25
[QUOTE=aysiu]This thread has the appearance of wanting to make change.[/QUOTE]
Nope. You want it to have this appearance in order to be able to insult all the people around you and feel oh so leet and enlightend.

---

### Post by BSDFreak on 2006-01-25
[quote=tufkakf]No, I won't. Calling people communists to insult them is not only stupid, but also shows that in the case of the FSF you don't know flying shit about what you talking about, as do your uninformed ramblings about hurd, minix and linux.

Stop emberassing yourself![/quote]

You are a complete and utter idiot, THEY called themselves FSF communists.

I know who you were before you were banned.

The hurd is a joke, minix is a better kernrel than the hurd will ever be and Linux was not intended to be FOSS, you can bleat all you like but that is the way it si even if you don't believe it.

---

### Post by BSDFreak on 2006-01-25
Hi [AMD64_N_Linux]("http://ubuntuforums.org/member.php?u=6019"), bye tufkakf.

---

### Post by barbarian on 2006-01-25
it may be complecated for me, but it should be more friendly to hardware, especially to notebooks.. IMHO :rolleyes:

---

### Post by tufkakf on 2006-01-25
[QUOTE=BSDFreak]You are a complete and utter idiot, THEY called themselves FSF communists.
[/QUOTE]
Sure, of course they did...

[QUOTE=BSDFreak]
I know who you were before you were banned.
[/QUOTE]
You do? That's amazing, as I was never banned.

[QUOTE=BSDFreak]
The hurd is a joke, minix is a better kernrel than the hurd will ever be and Linux was not intended to be FOSS, you can bleat all you like but that is the way it si even if you don't believe it.[/QUOTE]
Blah....

---

### Post by FLeiXiuS on 2006-01-25
This is a warning message for users who are participating in this thread.

Please do not continue to flame other users with random insults.  It's prohibited and against our policies.  

Further continuation of these insults will result in this thread being locked and or other actions neccessary.

---

### Post by barbarian on 2006-01-25
it maybe complecated for me, but it should be more friendly for hardware, espessially for notebooks.. imo :rolleyes:

---

### Post by manicka on 2006-01-25
The tone of some of the posts in this thread are against the forum guidelines. 

Please heed FLeiXiuS' warning and play nice.

---

### Post by KiwiNZ on 2006-01-25
[quote=FLeiXiuS]This is a warning message for users who are participating in this thread.

Please do not continue to flame other users with random insults.  It's prohibited and against our policies.  

Further continuation of these insults will result in this thread being locked and or other actions neccessary.[/quote]

What Fleix said . 
I have my padlocks armed and ready

---

### Post by Iandefor on 2006-01-25
[QUOTE=BSDFreak]Aqua is the damn theme, nothing more, the engine is still Darwin.

You don't change the OS much by switching from Plastik to baghira in KDE and you could use both with Darwin.

It's a mach implementation of the 4.4BSD kernel, somewhat customized.[/QUOTE] Might I ask whence the hostility arises?

AFAIK, Aqua is the graphics engine in the sense of GTK or QT.

I never said you couldn't use Plastik or Baghira in KDE on Darwin. I said OS X uses Aqua, which is Apple's proprietary graphics engine. There's a difference between a theme and a graphics engine.

 [QUOTE=KiwiNZ]I have my padlocks armed and ready[/QUOTE] Good man. This thread is getting a wee bit nasty.

---

### Post by awakatanka on 2006-01-25
[QUOTE=Vlammetje]Things like a tracert or ping for example[/QUOTE]
For ping i use pingplotter it gives a much better report over a biggertime then the simple ping from command.

For tracert i use also a gui based prg also because it gives me a better report.

Sure those commands are easy to use but if there is a gui version that gives more options i'm going to try and use it.

damn i need a service menu so if i'm browsing i do right click and select tracert our ping for the site i browse on.

Some are GUI junks some are CLI junks and both can work greatly together in a OS.

:p

Also why people using KDE our GNOME if they can do the same in CLI, why they use openoffice if wp5.1 can do the job to? There even browser for CLI. Lets all go back to CLI and type youre fingers blue.

---

### Post by Arktis on 2006-01-26
[QUOTE=tufkakf]And nobody said it was. Strawman, meet Arktis. Arktis, meet Strawman.[/quote]
Oh?  What about:
[quote=Sirin]This is the age of the GUI.[/quote]
[quote=Gustav]There is no need to do stuff as they do in windows but I still think GUI is the way to the future[/quote]
Hmm, sounds like it to me.  And who's this strawman?  Was that an insult?  Are you trying to make some obscure reference about my brain?  I know this may be a futile request, but please don't flame... I read your other posts and it seems you have a tendancy to do this.

[QUOTE=tufkakf]Believe it or not, but providing tools that make things easier is kind of the idea behind computers. And learning in and of itself isn't a merit, if this learning is required because something that could also be achieved much easier has to be done in a complicated, non-obvious way.[/QUOTE]
Yes, just like as a child, you have to learn how to go potty, feed yourself, and how to have good manners.  Should little kids have servants that do all this stuff for them?  No.  Thinking and learning are good things.  It's part of life.  Computers should not become servants that do all of our thinking for us.

---

### Post by tufkakf on 2006-01-26
[QUOTE=Arktis]
Hmm, sounds like it to me.  And who's this strawman?  Was that an insult?  Are you trying to make some obscure reference about my brain?  I know this may be a futile request, but please don't flame... I read your other posts and it seems you have a tendancy to do this.
[/QUOTE]
Calm down. I wasn't insulting you, it was a reference to your way of arguing:
[http://en.wikipedia.org/wiki/Strawman#In_logic_and_rhetoric](http://en.wikipedia.org/wiki/Strawman#In_logic_and_rhetoric)

[QUOTE=Arktis]
Yes, just like as a child, you have to learn how to go potty, feed yourself, and how to have good manners.  Should little kids have servants that do all this stuff for them?  No.  Thinking and learning are good things.  It's part of life.  Computers should not become servants that do all of our thinking for us.[/QUOTE]
See above, or should I say: Oops, you did it again?

---

### Post by Arktis on 2006-01-26
No, I don't think you should.  I do think you're quibbling over trivial things in an attempt to bait me, though.  Stick to the discussion, please.  Here, I'll take the extra step and further clarify the point of my last two posts.

Easy = Less thought and knowlegde required.  I am asserting that this is overall a bad thing.  I call it ignorance.  Remove the ignorance, use the command line, and you're more efficient.  Simple.

---

### Post by tufkakf on 2006-01-26
[QUOTE=Arktis]No, I don't think you should.  I do think you're quibbling over trivial things in an attempt to bait me, though.
[/QUOTE]
Nope, I'm simply pointing out false arguments.

[QUOTE=Arktis]
Easy = Less thought and knowlegde required.  I am asserting that this is overall a bad thing.  I call it ignorance.  Remove the ignorance, use the command line, and you're more efficient.  Simple.[/QUOTE]
And as I pointed out, your assertion is wrong if you gain nothing from learning something that could also be done easier.
Btw., if this is your opinion, why don't you use LFS?
You'll certainly have to learn more things there than you have to when running Ubuntu, whose claim to fame is that it just works.

---

### Post by egon spengler on 2006-01-26
[QUOTE=awakatanka]Also why people using KDE our GNOME if they can do the same in CLI, why they use openoffice if wp5.1 can do the job to? There even browser for CLI. Lets all go back to CLI and type youre fingers blue.[/QUOTE]

You keep making reference to wear on tear on the digits and while I'm sure that you are not seriousy putting that forward as the main thrust of your argument I have to wonder how you operate your mouse. It's not with your fingers is it? 

Also, it's an interesting change in soceity that people even half jokingly regard typing on a keyboard as some form of arduos task that takes a herculean effort. I started out in life performing hard physical labour to earn a crust, my father spent his entire working life performing hard physical labour as did my grandfather before him. Again, I know that you are only being half serious, it's just interesting to me to see the Jetsons prophecy come true and men regard pushing buttons as hard work

---

### Post by awakatanka on 2006-01-26
[QUOTE=egon spengler]You keep making reference to wear on tear on the digits and while I'm sure that you are not seriousy putting that forward as the main thrust of your argument I have to wonder how you operate your mouse. It's not with your fingers is it? 

Also, it's an interesting change in soceity that people even half jokingly regard typing on a keyboard as some form of arduos task that takes a herculean effort. I started out in life performing hard physical labour to earn a crust, my father spent his entire working life performing hard physical labour as did my grandfather before him. Again, I know that you are only being half serious, it's just interesting to me to see the Jetsons prophecy come true and men regard pushing buttons as hard work[/QUOTE]
hehe i'm joking yes, but i find it strange there is so much strugle to something that adds some little thing that make life easier for some users that like GUI more then CLI. Nobody is saying that CLI has to be removed but they just say add something gui based for some simple task that are easier with gui. Now dapper will have some improvements on.

If i could program i would make something that made my life easier with some CLI things.

Its funny that people are against it but still use a GUI based OS, all the things they use have made there life easier and if they realy against simplify things they would only use CLI because all things they do can be done from CLI to.

I'm still basicly use the same things as i used in my dos time, so why i still use windows/gui?

---

### Post by Arktis on 2006-01-26
[quote=tufkakf]And as I pointed out, your assertion is wrong if you gain nothing from learning something that could also be done easier.[/QUOTE]Easier does not mean more efficient.  The CLI is more efficient for many tasks than a GUI.  That's gaining something useful by learning.  It's also better to learn something other than point and click.  The brain is a muscle, you know.

[quote=tufkakf]Btw., if this is your opinion, why don't you use LFS?
You'll certainly have to learn more things there than you have to when running Ubuntu, whose claim to fame is that it just works.[/QUOTE]
Say hi to stickman for me.

Anyways, I don't use LFS because I would essentially be on my own there.  I wouldn't have this big support base that I have now with ubuntu.  I'm not ready for that.  Yet.

---

### Post by Virogenesis on 2006-01-26
a Gui interface can only do so much a user should not be masked just by a gui sure guis are ace I'd prefer a installer with a interface I'd also like to be able to config certain things but I do also understand linux uses config files and well to get the most of your experience its a must to have basic command line knowlege.

eg: xserver crashes what do you do?
Well I'd start up a virtual console by pressed ctrl + alt + F1 log in kill the problem logout then press alt + F7 should then be sorted.

Things like that cannot be done with a gui to put your trust in a gui is a common mistake and it will make you lazy.

Gui + Cmd.... don't just focus on a gui

---

### Post by tufkakf on 2006-01-26
[QUOTE=Arktis]Easier does not mean more efficient.  The CLI is more efficient for many tasks than a GUI.  That's gaining something useful by learning.  It's also better to learn something other than point and click. [/QUOTE]
What did this poor strawman do to you?
I did not say that easier == more efficient.
I did not say that the CLI isn't more efficient for many tasks.
What I did say and what I'll now repeat for the third time in the hope that you might eventually answer the actual point I'm making is, that learning has no merrit if you don't gain anything by learning. If you just have to learn something because it is badly implemented.

[QUOTE=Arktis]
The brain is a muscle, you know.
[/QUOTE]
Talk about flamebaiting.

[QUOTE=Arktis]
Say hi to stickman for me.

Anyways, I don't use LFS because I would essentially be on my own there.  I wouldn't have this big support base that I have now with ubuntu.  I'm not ready for that.  Yet.[/QUOTE]
I assume you mean strawman, not stickman.
Anyway, it's not a strawman argument, but a honest question, because using Ubuntu goes contrary to what you proclaim otherwise. And don't worry, you wouldn't be alone with LFS, if anything they have great documentation.

---

### Post by Stormy Eyes on 2006-01-26
[QUOTE=awakatanka]Also why people using KDE our GNOME if they can do the same in CLI, why they use openoffice if wp5.1 can do the job to?[/QUOTE]

Dude, if I could get WP5.1 working under Linux, you can bet your bollocks I'd be using it instead of OpenOffice. WP5.1 rocked like an army of coked up ninja.

---

### Post by egon spengler on 2006-01-26
[QUOTE=awakatanka]Its funny that people are against it but still use a GUI based OS, all the things they use have made there life easier and if they realy against simplify things they would only use CLI because all things they do can be done from CLI to.[/QUOTE]

I don't think that anyone is *against* the gui, if you can find a quote of someone who is against the whole concept of a gui then I would consider them to be incredibly foolish. It's like this though, the whole tone of the thread was set by the stupid options of the poll which basically set out shop as "I say more gui elements are needed and only fools disagree". I don't think anyone is hoping to have all traces of gui stripped from ubuntu, I'm sure that everyone here logs in to x, I think it's a question of differing opinion as to where the emphasis of development should be. Some might believe that the number one priority has to be to make everything controllable from a gui, other people think that it is not the most pressing issue needing development.  I think it's a bit of a stretch to deduce from people saying "making everything gui is not the most important thing" that the people in question want to do away with all gui elements.

I think really we need some sort of official statement to put an end to this debate, is ubuntu officially trying to become a mepis like distribution that attempts to create a gui for every possible thing (and if they are then they are failing miserably, nobody would be able to argue that) or not. 

btw, something else you need to bear in mind is that easier is a very relative term, before I used the cli I found the idea that people manage files from it mildly absurd, I thought it was purely the empty rhetoric of the type of super boffins who proudly boast of writing all html code in windows notepad. Guess what though, it often IS easier to use the cli. I would wager that most people who have given a fair chance to both would agree that with tab complete the VAST majority of moving and copying files is quicker than dragging in a file manager (I haven't used gnome in a long time but is it still the case that dragging a file onto the task manager doesn't activate the window?). I think that a lot of people instantly assume that gui is easier because it's what they are used to, I know I made that same mistake

---

### Post by awakatanka on 2006-01-26
[QUOTE=Stormy Eyes]Dude, if I could get WP5.1 working under Linux, you can bet your bollocks I'd be using it instead of OpenOffice. WP5.1 rocked like an army of coked up ninja.[/QUOTE]
There still troubles then to get it working under linux? There should be some good emulators for dos by now.

Some had it running 10 years ago, slackware had a special keymap for it. But thats info i have found on google ;)

---

### Post by awakatanka on 2006-01-26
[QUOTE=egon spengler]I don't think that anyone is *against* the gui, if you can find a quote of someone who is against the whole concept of a gui then I would consider them to be incredibly foolish. It's like this though, the whole tone of the thread was set by the stupid options of the poll which basically set out shop as "I say more gui elements are needed and only fools disagree". I don't think anyone is hoping to have all traces of gui stripped from ubuntu, I'm sure that everyone here logs in to x, I think it's a question of differing opinion as to where the emphasis of development should be. Some might believe that the number one priority has to be to make everything controllable from a gui, other people think that it is not the most pressing issue needing development.  I think it's a bit of a stretch to deduce from people saying "making everything gui is not the most important thing" that the people in question want to do away with all gui elements.

I think really we need some sort of official statement to put an end to this debate, is ubuntu officially trying to become a mepis like distribution that attempts to create a gui for every possible thing (and if they are then they are failing miserably, nobody would be able to argue that) or not. 

btw, something else you need to bear in mind is that easier is a very relative term, before I used the cli I found the idea that people manage files from it mildly absurd, I thought it was purely the empty rhetoric of the type of super boffins who proudly boast of writing all html code in windows notepad. Guess what though, it often IS easier to use the cli. I would wager that most people who have given a fair chance to both would agree that with tab complete the VAST majority of moving and copying files is quicker than dragging in a file manager (I haven't used gnome in a long time but is it still the case that dragging a file onto the task manager doesn't activate the window?). I think that a lot of people instantly assume that gui is easier because it's what they are used to, I know I made that same mistake[/QUOTE]
Back in the dos days the first thing people did was installing Norton commander our that other prg i forget the name of, Most people always choose to simplify things for themself even if it will give them more work at the end, they used had the feeling it worked fatser for them. I agree that lots of things is better if you are used to CLI and want to give some effort in trying to learn it, but lots of people are to lazy to do that and for those people should be the option to use a gui because they have the feeling it is easier for **them**. I for one hate some tasks i have to do in cli.

Youre copy example is maybe valid for you but most just will do a drag drop our a control -c control-v. As long if they have a choose its a goodthing. They can exsist together.

I know i give examples in the extreme but the gui is there because it made live easier and some little improvements will make live easier for some lazy/not knowing our not eductated people.

And this kind of topics will always be posted by windows users that are trying our are converted to linux. If these kind of topics wouldn't be posted then it could mean 2 things : 1 the distro is to difficult our 2 its perfect. ;)

---

### Post by Stormy Eyes on 2006-01-26
[QUOTE=awakatanka]There still troubles then to get it working under linux? There should be some good emulators for dos by now.[/QUOTE]

I don't think DOS emulators play nicely with CUPS. What good is a word processor if you can't print out what you've written?

---

### Post by BSDFreak on 2006-01-26
[quote=Iandefor]Might I ask whence the hostility arises?

AFAIK, Aqua is the graphics engine in the sense of GTK or QT.[/QUOTE]

No, do a search for Quartz since i'm not up to educating you on the matter.

> I never said you couldn't use Plastik or Baghira in KDE on Darwin. I said OS X uses Aqua, which is Apple's proprietary graphics engine. There's a difference between a theme and a graphics engine.

Aqua isn't a graphics engine, it's a theme as Baghira or Plastik is a theme, they prefer to call it interface but it's still all it is.

---

### Post by Sirin on 2006-01-26
[QUOTE=commodore]GUI is anal sex.[/QUOTE]

Hey, if it wasn't for the GUI, the mouse would never exist. 

People, I'm not saying "take out the CLI", leave it in. But don't involve it so much that new users will have to read a 1,000 page book just to learn it. If it's supposed to be better than Windows, then why should it be harder? I like using the command line, but grandmothers won't. Unlike Windows or Mac OS, or RPM-based systems, you can't install any applications from CDs. Your only hope is to use "the internet". Now, what if they have 28k dial-up? They can't expect to install 58MB worth of apps just to do something. Why is the only way to install something that isn't in the repositories is to use dpkg? Why not just double-click something to install? Is this because "it's too easy", or "that's the Windows way of doing it"? You wouldn't expect very lazy people to use the command line using advanced UNIX commands, right?  

Also, we need easy GUI installers. In my opinion, Fedora Core 1's Installer is better than Ubuntu's installer. Fedora's installer lets you choose which apps you like, which apps you may want to keep out. 

And BTW, why are you saying that "GUI-People" need to go back to Windows? That would contradict the reason that we came here in the first place. "If you don't want to use the command line, go back your crashy spyare Windows world." What the hell is that? We came to Ubuntu because we wanted stability, security, and most of all, non-costliness. Telling somebody to go to another distro is like telling them to "get the hell out of Ubuntu". If you want people that want ease-of-use to go to another distro, then why are you converting users from windows to Ubuntu in the first place? You wouldn't expect them to know how to work Ubuntu in the first place, no? If you want to know why I'm saying this, is because I'm tired of having to help them use Ubuntu every single time they use it. When I tell them how to use dpkg to install something, at the end, they say "huh? :confused:". That's one of the reasons why we should make Ubuntu for novice users also. Most Windows users are most likely to switch to Mac OS X than Linux. Why? It's not FUD, it's a fact: Linux is not for the "what's an OS?" people. They only reaso why they would want to install Linux, is because "it is free". Very few people would want to pay for Linux if they found out that it was free. Just because Ubuntu is free, doesn't mean that there has to be sacrifices. Take a look at Firefox and Thunderbird, and look how better they are than the commercial "Internet Explorer and Outlook". ;)

Oh, and I'm not whining, I'm giving out suggestions. But it seems like some people here don't like suggestions, eh? ;)

---

### Post by GeneralZod on 2006-01-26
[QUOTE=Sirin]Why is the only way to install something that isn't in the repositories is to use dpkg? Why not just double-click something to install? Is this because "it's too easy", or "that's the Windows way of doing it"? [/QUOTE]

It really depends on whether that thing has been specifically compiled for your system.  If it has, then I'm not really sure why there isn't a simple GUI wrapper for dpkg yet - I guess no one has considered it a priority and volunteered to write one :confused: I agree that one would make things easier.  Don't other distros have something like this, called KPackage or something...?

If you're not referring to .debs that have been compiled especially for your Ubuntu version - like in Windows, where a single .exe will work pretty much independent of what version of Windows you have - it's because the technical challenges are pretty great and unpleasant trade-offs would have to be made (for example - stagnation of libraries/ toolkits or unnecessarily bloated apps).

---

### Post by gabbman on 2006-01-26
After 5 years of waiting for linux to become 100% GUI, I am seriously looking at the sexy iMac G5.

---

### Post by Sirin on 2006-01-26
[QUOTE=gabbman]After 5 years of waiting for linux to become 100% GUI, I am seriously looking at the sexy iMac G5.[/QUOTE]

Actually, it's best if you get the Intel version, since you can also run PPC apps (with a very small slowdown) using Rosetta. ;)

---

### Post by Stormy Eyes on 2006-01-26
[QUOTE=gabbman]After 5 years of waiting for linux to become 100% GUI, I am seriously looking at the sexy iMac G5.[/QUOTE]

Have fun. Personally, I *like* using the command line, and would refuse to use any Linux distribution that became so much like Windows that it either did not include a shell or included a crippled shell.

---

### Post by Sirin on 2006-01-26
[QUOTE=Stormy Eyes]Have fun. Personally, I *like* using the command line, and would refuse to use any Linux distribution that became so much like Windows that it either did not include a shell or included a crippled shell.[/QUOTE]

We don't want to take out the CLI, but we want to make it so there are GUI frontends. Like a GUI frontend to dpkg. :)

---

### Post by Stormy Eyes on 2006-01-26
[QUOTE=Sirin]We don't want to take out the CLI, but we want to make it so there are GUI frontends. Like a GUI frontend to dpkg. :)[/QUOTE]

Fine, as long as I don't have to use it. If I wanted to maintain my system with a GUI, I'd still be using Windows.

---

### Post by gabbman on 2006-01-26
That's the plan, thanks.

---

### Post by tufkakf on 2006-01-26
[QUOTE=gabbman]After 5 years of waiting for linux to become 100% GUI, I am seriously looking at the sexy iMac G5.[/QUOTE]
Just being curious, but what are the things you do that require using the CLI on distributions like, for example, Suse?

---

### Post by Sirin on 2006-01-26
[QUOTE=tufkakf]Just being curious, but what are the things you do that require using the CLI on distributions like, for example, Suse?[/QUOTE]

Mostly running su and sudo. But KDE has eliminated that, so if you're using GNOME or anything else, then you're stuck with it.

---

### Post by Stormy Eyes on 2006-01-26
[QUOTE=Sirin]Mostly running su and sudo. But KDE has eliminated that, so if you're using GNOME or anything else, then you're stuck with it.[/QUOTE]

**sudo apt-get install** gksu gives a GTK wrapper to su and sudo.

---

### Post by Sirin on 2006-01-26
EDIT: Nvm.

---

### Post by prizrak on 2006-01-26
[QUOTE=Sirin]We don't want to take out the CLI, but we want to make it so there are GUI frontends. Like a GUI frontend to dpkg. :)[/QUOTE]
The GUI frontend to dpkg is comming in Dapper, the reason there wasn't one before (that was discussed in another thread) was because the devs didn't find one that suited their needs. The Dapper one will work with apt-get to install the dependancies needed for your .deb 
Also Ubuntu is a broadband distro, it has been mentioned before. People on dial up are pretty much out of luck, but that's a trade off for having a single CD as opposed to multiple disks. One reason I can think of for not having all the GUI sexiness is because Ubuntu is pretty young and was mostly geared towards making it as developed as possible and work on as much hardware as possible. Now that it's pretty stable the devs can start adding on non essential stuff (which I'm sorry to say GUI tools for random sys admin work are). 
The reason many people advise to switch distros is because there are distros that already offer something you might want, while Ubuntu might or might not offer it in X months when the new release comes. There are also things like overall philosophy, like not including proprietary codecs out of the box so if that's someone issue they might want a different distro. For now I'd say wait for Dapper see what kind of goodies we get with that when it hits final, hopefully it will address all the issues people have. :)

---

### Post by Iandefor on 2006-01-26
[quote=BSDfreak]Do a search for Quartz.[/quote] Researching into Quartz proved me wrong. My bad.

> 
Aqua isn't a graphics engine, it's a theme as Baghira or Plastik is a theme, they prefer to call it interface but it's still all it is. Okay.

> 
No, do a search for Quartz since i'm not up to educating you on the matter.
 As if "educating" me would be some kind of Herculean task? You imply a good deal in that statement, friend. Watch your tongue or don't use it. It really isn't worth my time to read condescending and hostile messages posted by some thersitical pedant.

---

### Post by Mr. Picklesworth on 2006-01-29
I think that the command line should stay (obviously) and remain commonly used, but there's really no reason it couldn't be made a bit more friendly.
For example, a menu beside the input thing containing commonly used commands organized into groups wouldn't be hard to do but would be extremely helpful.

---

### Post by prizrak on 2006-01-29
[QUOTE=Mr. Picklesworth]I think that the command line should stay (obviously) and remain commonly used, but there's really no reason it couldn't be made a bit more friendly.
For example, a menu beside the input thing containing commonly used commands organized into groups wouldn't be hard to do but would be extremely helpful.[/QUOTE]
There is no need for that. When using CLI you either will know what to type in, or will copy paste commands that someone who knows what they are doing. The biggest thing here is that many people don't know of GUI tools for certain things, because on the forums you gonna get CLI commands that are easy to copy-paste into the terminal rather than follow System>Administration>Device Manager>bring dat *ss up>turn it around. You get the picture ;)

---

### Post by BobSongs on 2006-02-21
My first, and as of yet, [only tutorial]("http://www.ubuntuforums.org/showthread.php?t=105703") involves the command line.

And I'm a newbie myself.

I have dabbled in Linux for many years, curious about this free O/S. I never quite understood it seeing I was becoming more and more entrenched in Windows thinking. I couldn't seem to let go of Windows and so many of my friends were in need of help. I figured I'd keep up with Redmond's architecture. True: my beginnings were in DOS. So perhaps I'm biased towards the command line.

Some people will wish to learn more about their systems. Copying and pasting commands will do precious little to teach anyone anything, imho. But in some cases walking a person through what to click isn't any more educational. It depends on the person you're helping. Those who seek a quick fix will copy/paste or click their way out of a problem and then carry on.

In recent years Linux has become more useable without the command line. And some Linux users manage to dodge its use. But those who are desperate to alleviate a system problem will do what it takes to get the job done. My tutorial was designed for the complete Windows-crossover newbie. I was more careful in how it was written; the ideas had to be thought out. But the accolades are proof I did what folks need.

Use of the Terminal/command-line will *not* frighten away new users if we carefully/accurately point out what to do. It goes without saying that a user who is too terrified of the Terminal should seriously reconsider using Linux, and we cannot remove fear from those who are determined to be frightened away.

I don't want all Windows users to switch over to Linux. Just those who have come to the conclusion Windows isn't as satisfying or secure as they thought it would be.

Linux != Windows. We can make our tutorials/responses more friendly, but that's about all. This is what I tried to do. Take the new user's hand and hold it. That can be done in many ways. Clarity might well dispell fear. I personally dislike HOWTOs that assume 10 years of Linux command line experience. I can tolerate being told where the Terminal is situated (Applications > Accessories > Terminal) even though I have its icon in my top panel.

I know this is an old thread, probably not worth reviving. But I wanted to toss in my two cents worth.

---

### Post by Kerberos on 2006-02-21
Slightly off topic but why is DOS looked down upon with derision, yet the Linux CLI is looked upon as being an essential tool (to the point that many functions are only achievable through it)?

Also whoever said that your less likely to make dangerous mistakes with the CLI (such as in partitioning)
```
rm -rf / temp
```
I'd say the CLI gives much, much more chance of fatal errors.

---

### Post by ygarl on 2006-02-21
[QUOTE=poofyhairguy]I'm just going to straight up ask the community on this one. Please beat me up and tear my logic apart- I'm posting this for that reason.

As many know I try my best to help out new Ubuntu users. Many of us do, and its a great thing. Often on this forum I will tell people commands to put in the command line to fix their problems. Recently I was told that this is not the best thing, as it scares away new ex-Window's users who associate "command line" with "Dos" (this ignores that fact that a big "feature" of longhorn will be a functional CLI). Azz, another moderator here is big on giving answers that fix problems through a graphical method if possible. Supposedly the Ubuntu developers themselves have set out a goal that "an Ubuntu user shouldn't need to touch the command line," but until they make a GUI tool for ndiswrapper (aka the hardest thing for a new user to do) I don't put much weight into their opinions on the matter.

 I personally tell greens commands because :

A. Instructions using a GUI require pages of screenshots with areas circled in gimp or whatever. Its harder to write a good way to work through the GUI...they are very intuitive to me so I leave out steps that my brain assumes. Anyone that has done tech support on Windows can tell you the problems here.

B. No one can mess up copy and pasting a command. You CAN mess up entering info in many dialog boxes in a GUI.

C. I kinda have this idea that greens need to get used to the way Linux does things. Many of the howtos on this forum require some work on the command line. It seems like unless someone set up the computer for you and all you do it make office docs and surf the internet you will one day have to face the command line (if only to run the program you just downloading in synaptic but a menu option wasn't added for it). Till now I've been of the opinion "they need to just get used to it early on.....its not like we have a YAST or something like that so command line work is inevitable." I mean....look at your grub menu....."safe mode" in Ubuntu is the command line.

D. When I first started with Linux I was afraid of the command line too...but now I think is is very powerful and I would hate to go without it. It doesn't have the negative connotation with me as it does with some people. If the betters I got my early advise from didn't force me to use the command line (by only helping me that way) I wouldn't be half the *NIX admin I am today. Now (after using Linux for less that a year) I can fix a Ubuntu computer from the command line.

E. The guide uses the command line so I want to be consistent.

F. There is no F

So...what do you guys think? Is pointing newbies to the command line a bad thing? If they are afraid of it should I be honest and tell them "the only Linux I know of that liberates itself from the command line is SUSE?" Should we make more guides to do things in a graphical way?  Will Ubuntu ever reach the lofty goal of "never needing the command line?"[/QUOTE]

You are correct. Command Line is by FAR the best way to learn Linux and to do things on Ubuntu. Errors are MUCH clearer and it generally just runs better when doing 'big' things. People are less likely to be scared by compiling programs, etc if they have a grasp of the Terminal.

Carry on...
Good work.

---

### Post by BoyOfDestiny on 2006-02-21
[QUOTE=Kerberos]Slightly off topic but why is DOS looked down upon with derision, yet the Linux CLI is looked upon as being an essential tool (to the point that many functions are only achievable through it)?

Also whoever said that your less likely to make dangerous mistakes with the CLI (such as in partitioning)
```
rm -rf / temp
```
I'd say the CLI gives much, much more chance of fatal errors.[/QUOTE]

I'm a fan of DOS, well it's games anyway... CLI is just that... A Command Line Interface. 
DOS, Disk Operating System... was just that. It had memory limits (that were somewhat overcome with protected mem etc), it wasn't multi user, and was basically the foundation windows ran upon until 2000/XP. 

Anyway, it'd be comparing very different things. As for commandline being dangerous, depends on the user. At least they can't accidently click something... =) It's worth mentioning that front-end can be written for ANY command (correct me if I'm wrong).

---

### Post by Kerberos on 2006-02-21
[QUOTE=BoyOfDestiny]I'm a fan of DOS, well it's games anyway... CLI is just that... A Command Line Interface. 
DOS, Disk Operating System... was just that. It had memory limits (that were somewhat overcome with protected mem etc), it wasn't multi user, and was basically the foundation windows ran upon until 2000/XP. 

Anyway, it'd be comparing very different things. As for commandline being dangerous, depends on the user. At least they can't accidently click something... =) It's worth mentioning that front-end can be written for ANY command (correct me if I'm wrong).[/QUOTE]
I am very well aware of what DOS is, hence my comment on why it still gets sarky comments from people who really should know better and who rabidly promote Linux CLI's - its just a bit of a double standard.

Being able to accidentally click something dangerous is not a justification for the superiority of a CLI (Try typing in my mis-typed RM code, I dare ya! ;)) its more a symptom of a bad GUI.

The reason I dont like CLI's is discoverability.  If you have a GUI and you need to do something (configure a network controller for example) you could probably figure it out pretty easily provided you understand what it is you want to do.  IP, DNS, Gateway etc are all easy to find and fill in boxes.  In a CLI environment there is _no way of knowing_ how to do it unless you either a: already know or b: have a howto which means you will be required to search the web for documentation and try to figure out syntax rather than just getting on with the job at hand.

GUI's are about communicating with users through the use of metaphors, using icons, windows, double clicking and dragging so that they can spend more time using the application rather than *learning* how to use the underlying operating system - which is fine if your a Linux fan but if you just want to get something done in a short amount of time its not - the operating system should stay out of your way.  

The CLI is just a blinking cursor, there isn't really any 'figuring it out' possible and everything has to either be taught or learned with a much, much greater burden of knowlege required on the users part to be as competant with it as with a GUI and most of the time they are just copying it verbatim from printouts or websites without actually understanding what it is they are doing - so why not just make an icon for it?

Only an idiot would argue to remove the CLI, it has a place and is indespensible in quite a lot of scenarios but if a GUI method of doing the same thing can be introduced, it should.

---

### Post by aysiu on 2006-02-21
They each serve their own purpose.

As Kerberos has pointed out, GUIs have discoverability.

The advantage of the CLI is the ability to quickly give instructions that can be copied and pasted and find out errors from other users who have copied and pasted those.

It takes me *a lot* longer to walk a new user through a process using screenshots than commands, and since the internet is the medium by which most Ubuntu users get help, I think we should all recognize the strengths of the command-line when it comes to giving help to new users.

Well, you can read more about my thoughts [here](http://www.ubuntuforums.org/showthread.php?t=59334).

---

### Post by briancurtin on 2006-02-21
to me, its all about the command line. i try to use it as much as possible, and try to answer questions with command-line-oriented answers. i use Arch now, where not being afraid to use the command line is kind of a prerequisite, and i like it a lot.

---

### Post by joflow on 2006-02-21
I have never been able to get into the command line.

Everyone says its so powerful but I'm unable to see it.  Can someone tell me how they use the commandline on a day to day basis (examples beyond simple moving, copying, etc of files)?

Can someone also give me some good examples of how bash scripting is useful.  I don't need to see any code, I just want to know what it could potentially do so I can determine if its worth learning.

---

### Post by K.Mandla on 2006-02-21
Personally, I have a problem with point F.

I find the command line expedient, but cryptic. There are things I prefer to do with a GUI (moving files and folders is an example), but there are other things that seem more natural in the command line.

Is it acceptable to say, "Give directions both ways?"

Of course, now having said that, I realize when I give help, I give command lines. ... :rolleyes:

---

### Post by aysiu on 2006-02-21
[quote=joflow]Everyone says its so powerful but I'm unable to see it. Can someone tell me how they use the commandline on a day to day basis (examples beyond simple moving, copying, etc of files)?[/quote] Sure. Take, for example, this [HowTo I wrote on removing Kubuntu.](http://www.ubuntuforums.org/showthread.php?t=96048) With one command copied and pasted into the terminal, you can remove a full set of applications. That same thing would take at least ten minutes (if not more) to do in Synaptic Package Manager.

[QUOTE=K.Mandla]
Is it acceptable to say, "Give directions both ways?"[/QUOTE] You can give directions however *you* want, but it always takes me longer to give directions for GUI than command-line. Occasionally, if someone *really* has a hard time understanding something, I'll do a screenshot and circle in red the appropriate button to push, but usually I'll just say, "copy and paste this command."

---

### Post by mstlyevil on 2006-02-21
Make no mistake about it, this is a command line oriented support board and distro. You can get by using the GUI for most things but to unlock the true potential of this operating system it is going to take the CLI. I was a little uneasy about the command line at first. I either just copied and pasted the commands without trying to learn what they actually were or I tried to find work arounds using the GUI as much as possible. (Actually, I still copy and paste a lot of times not because I don't know what the command is but that I get too lazy to type it.) Over the last few months I have decided to become more familiar with the CLI because I have found it to be actually easier and more efficient than relying on the GUI. You can do so many things in less time and with less hastle it gets you back to using your computer instead of working on it for hours on end trying to do the same thing in the GUI.

If a person does not want to use the CLI but still wants to use Linux, I see no problem with that. Suse can be set up and used by the average user without ever using the command line because of YAST. Ubuntu on the other hand is a distro I would not recommend to those people because you just can not get around the CLI. If someone wants to use Ubuntu, I believe it is best if they learn the basics of the CLI and some basic commands.

---

### Post by Arc Owner on 2006-02-21
I personally like the command line, and use it more than the package manager. Once you understand the basic commands, its not really that hard. If new users aren't willing to learn the command line, then they probably shouldn't be using linux.

---

### Post by xequence on 2006-02-21
I dont see how the command line is so powerful. You have to type something that you could just click to do.

For example, copying a file. Youd have to type some long drawn out command, or you could right click, copy, paste somewhere else.

Yes, its easier to tell them how to do command line things, and the command line can be good for old computers, but this isnt the 1980's (or 1990's, in the case of linux).

---

### Post by aysiu on 2006-02-21
[QUOTE=xequence]I dont see how the command line is so powerful. You have to type something that you could just click to do.[/quote] Well, sometimes, it's faster and easier to type something than to "just click" something.

Just look at apt-get and Synaptic. If I want to fire up Synaptic GUI-style, I click on System > Administration > Synaptic Package Manager. Then I click the Reload button. Then, I do a search for the application name. Then I right-click it to mark it for installation. Then I click Apply to apply the changes. That's a lot of clicking, not to mention the time it takes the GUI to load (even with my 512 MB of RAM), which isn't that long... but it's longer than it takes the terminal to load.

In the terminal, I just fire up the terminal with my keyboard shortcut and type ```
sudo apt-get update
sudo apt-get install packagename
```

Oh, and you might have missed part of my previous post: [quote=me]Take, for example, this [HowTo I wrote on removing Kubuntu.](http://www.ubuntuforums.org/showthread.php?t=96048) With one command copied and pasted into the terminal, you can remove a full set of applications. That same thing would take at least ten minutes (if not more) to do in Synaptic Package Manager.[/quote]

---

### Post by mstlyevil on 2006-02-21
[QUOTE=xequence]I dont see how the command line is so powerful. You have to type something that you could just click to do.

For example, copying a file. Youd have to type some long drawn out command, or you could right click, copy, paste somewhere else.

Yes, its easier to tell them how to do command line things, and the command line can be good for old computers, but this isnt the 1980's (or 1990's, in the case of linux).[/QUOTE]

MSFT and most system admins happen to disagree with you on this one. Vista is going to ship with a new Unix style shell for that very reason. Also you can do task in a fraction of the time it takes to navigate the GUI. For example If you want to move a large number of files to different folders you have to go back in forth in the different folders and copy and paste each file. Doing it by the command line only takes a few commands to get the exact same job done but in a lot less time. As aysiu stated earlier you would have to remove each package seperately to remove KDE in synaptic when that can be accomplished by just two commands. That is what makes using the shell so powerfull.

---

### Post by Sheinar on 2006-02-21
[QUOTE=xequence]For example, copying a file. Youd have to type some long drawn out command, or you could right click, copy, paste somewhere else.[/QUOTE]
"cp file /newplace/" is some long drawn out command?

I find it much faster using the command-line to copy/paste than to go through a GUI.

---

### Post by poofyhairguy on 2006-02-21
Wow what an old thread.

---

### Post by gw90se on 2006-02-21
> Wow what an old thread.

Ah, but still a good and valid one. i like learning the command line way. I feel more in control then click and something happens in the background.

---

### Post by prizrak on 2006-02-21
I actually started a newer thread not too long ago. The thing I think most people don't realize is that there are ways of doing things via a GUI. It is just that people like to set up their graphical environments in a different way. As defaults we already have Ubuntu, Kubuntu, and even Xubuntu (not to mention Edubuntu). So it is a lot of guess work to know what the user's GUI is looking like at the moment (hell I get bored of mine every few months so I change it around). The CLI however works in a very predictable way, every command will work the way we expect it to. (Cept gedit wouldn't be a default in KDE, or XFCE). It is also SO MUCH EASIER to copy paste commands rather than look through menus. I like the GUI way of doing things myself, I believe Ubuntu is missing a few I would call key but I must say that since Automatix came out most users will not touch the CLI more than once (required toget Automatix dled).

---

### Post by xequence on 2006-02-21
> cp file /newplace/

I assume it is longer... Like "cp /usr/home/patrick/desktop/The Eagles - The Last Resort.mp3 /usr/home/patrick/music" ;)

> For example If you want to move a large number of files to different folders you have to go back in forth in the different folders and copy and paste each file.

Ctrl + A, Ctrl + whatever it is to cut, Ctrl + V

But one thing (there are others, but I feel overall the GUI beats it in a majority) the command line is good for in my opinion: A server. When the server is running you dont want a GUI taking up RAM and stuff, as it is just wasting it. Thats why if what ive heard about windows server, where it is always in a GUI, it is worthless as a server :P

> In the terminal, I just fire up the terminal with my keyboard shortcut and type 

That is one of the times where the command line is better. I like that the terminal comes up fast and I can install something like that.

But I fell it is a minority of the times that the terminal can beat a GUI :)

---

### Post by mstlyevil on 2006-02-21
[QUOTE=xequence]I assume it is longer... Like "cp /usr/home/patrick/desktop/The Eagles - The Last Resort.mp3 /usr/home/patrick/music" ;)



Ctrl + A, Ctrl + whatever it is to cut, Ctrl + V

But one thing (there are others, but I feel overall the GUI beats it in a majority) the command line is good for in my opinion: A server. When the server is running you dont want a GUI taking up RAM and stuff, as it is just wasting it. Thats why if what ive heard about windows server, where it is always in a GUI, it is worthless as a server :P



That is one of the times where the command line is better. I like that the terminal comes up fast and I can install something like that.

But I fell it is a minority of the times that the terminal can beat a GUI :)[/QUOTE]

You just need to get that new computer bought so you can install Ubuntu and play around with the command line more. I believe you will come around after that. :)

---

### Post by aysiu on 2006-02-21
[QUOTE=xequence]
But I fell it is a minority of the times that the terminal can beat a GUI :)[/QUOTE] I think it depends on the user and the user's primary tasks. For me, you're right--*most* of the tasks I perform are GUI ones, mainly because I use Ubuntu for Firefox and Thunderbird and not a whole lot else.

---

### Post by Rev. Nathan on 2006-02-21
No!

I came to ubuntu as a newbie, and had not used a command line since it actually did something in Windows (Win 98SE, DOS commands). Getting reaquinted with the command line was something I really needed. It really taught me automating certain processes won't make me learn anything.

Although I do enjoy Automatix :D

---

### Post by xequence on 2006-02-21
> You just need to get that new computer bought so you can install Ubuntu and play around with the command line more. I believe you will come around after that. 

I _really_ hope I can get it soon, but I am just so bad at accually doing anything! Ill think it over a hundred times, then fifty more times just to be sure, then hope I will accually go do it sometime soon.

> I think it depends on the user and the user's primary tasks. For me, you're right--most of the tasks I perform are GUI ones, mainly because I use Ubuntu for Firefox and Thunderbird and not a whole lot else.

Yes, youre right. It depends on the user and their tasks. I would be more efficient with the GUI then terminal for most things because thats what I like. Someone else might be more efficient with the terminal because it is what they like.

> (Win 98SE, DOS commands). 

The only DOS command I know is:

format c:

---

### Post by Rev. Nathan on 2006-02-21
[QUOTE=xequence]The only DOS command I know is:

format c:[/QUOTE]
There are a few good ones. cd is the same, but cd .. is cd \, and so on. I found that suprisingly UNIX was easier then DOS; a terminal that came before DOS!

BTW Formatting of harddrives were disabled in the NT-based versions of Windows (2000, Server, XP, NT, ME) (You could only format a floppy, which the GUI was more detailed for doing that)

---

### Post by BoyOfDestiny on 2006-02-22
[QUOTE=Kerberos]I am very well aware of what DOS is, hence my comment on why it still gets sarky comments from people who really should know better and who rabidly promote Linux CLI's - its just a bit of a double standard.

Being able to accidentally click something dangerous is not a justification for the superiority of a CLI (Try typing in my mis-typed RM code, I dare ya! ;)) its more a symptom of a bad GUI.

The reason I dont like CLI's is discoverability.  If you have a GUI and you need to do something (configure a network controller for example) you could probably figure it out pretty easily provided you understand what it is you want to do.  IP, DNS, Gateway etc are all easy to find and fill in boxes.  In a CLI environment there is _no way of knowing_ how to do it unless you either a: already know or b: have a howto which means you will be required to search the web for documentation and try to figure out syntax rather than just getting on with the job at hand.

GUI's are about communicating with users through the use of metaphors, using icons, windows, double clicking and dragging so that they can spend more time using the application rather than *learning* how to use the underlying operating system - which is fine if your a Linux fan but if you just want to get something done in a short amount of time its not - the operating system should stay out of your way.  

The CLI is just a blinking cursor, there isn't really any 'figuring it out' possible and everything has to either be taught or learned with a much, much greater burden of knowlege required on the users part to be as competant with it as with a GUI and most of the time they are just copying it verbatim from printouts or websites without actually understanding what it is they are doing - so why not just make an icon for it?

Only an idiot would argue to remove the CLI, it has a place and is indespensible in quite a lot of scenarios but if a GUI method of doing the same thing can be introduced, it should.[/QUOTE]

Agreed, sorry if I misunderstood about the DOS thing. Anyway, in terms of the network thing, I fall into that category. However, a user that isn't a novice like me, and has learned to use these commands can work at lower level (meaning without the abstraction that the gui is). More control, more power, but greater learning curve. 

I definitely like having both gui and commandline (sometimes I can get things done a lot faster that way, and feel cool ;) ) Heck I've even used them together, where I want to do a recursive permission change on a folder (before I knew about tab completion) and dragged the folder from nautilus into the terminal, and just put it in single quotes... Funny I know, but I'm learning :)

---

### Post by Gavin JC on 2006-02-22
I don't really understand why this is such an issue... If there are more GUI's made for using the OS does it mean that those who want to can't still use the command line?

Cheers, Gavin C.

---

### Post by mstlyevil on 2006-02-22
[QUOTE=poofyhairguy]Wow what an old thread.[/QUOTE]

You ought to know, you started it. :-D

---

### Post by Bandit on 2006-02-22
You know the command line does scare many new users. Soon as many here about the CLI they think that linux is inferior to winders. 
[rant]
But you know what. I hate f'n windows users. Each one thinks s/he is a freaking guru at the damn pc cause they know how to install shit..
[/rant]
I say tell them the easiest way, via it CLI or GUI. IF they dont like it, stuff it. They can go back to windows.. One day they will be back..

---

### Post by Deaf_Head on 2006-02-22
[QUOTE=Stormy Eyes]Oh, jeez, not this nonsense again.[/QUOTE]


lol,

---

### Post by BobSongs on 2006-02-22
I'm glad I scared up this ol' thread. ;)

The command line offers up several eye-opening error outputs when something goes wrong. I adjusted my system based on the error outputs the printer drivers were producing. Once done they installed perfectly.

DOS of days gone by was affectionately known among my Linux friends as "Unix's retarted younger brother". I don't believe the CLI under XP could be considered such and the new CLI under Vista will incorporate Microsoft's SFU (Windows Services for Unix). So it seems all roads are leading to a Unix command-line, be it in Linux, MacO/S or Windows.

The command-line may not be useful for the GUI user in terms of copying files. And basic usage of an O/S generally involves little more than that. Where the CLI is most powerful is for compiling downloaded programs and running Linux binaries. Each time I read through a Linux forum I'm encouraged to try more and more oddly named CLI commands to perform some nifty tasks. *nix was pretty much built up from the command-line so just about any tool you need to fine-tune the system is there at one's fingertips, or pick out a data needle from a proverbial haystack of information.

But this doesn't answer the question about what to do with new users who feel intimidated. I personally believe those who want more from their system will press forwards. The CLI may be a handy excuses to those unwilling to take the time/risk to learn Linux. But we should fret about this. Braver individuals will find themselves rewarded by solved problems when the commands are copied, pasted and entered into the system. Their early attempts will prove successful and their fears dispelled.

Keep up the tutorials with the CLI. Ensure that your grandmother can do the tutorial if carefully followed: leave nothing to chance. Ubuntu is Linux for Humans. UbuntuForums is help for humans. :D

---

### Post by weng on 2006-02-22
i was trying to install gimp-print such taht I can print on my epson stylus 780 printer and read the instruction to use the "make" command but when I did so  gave me an error that make is unknown command.  what should i do?

---

### Post by IYY on 2006-02-22
I love the command line.

---

### Post by poofyhairguy on 2006-02-23
[QUOTE=weng]i was trying to install gimp-print such taht I can print on my epson stylus 780 printer and read the instruction to use the "make" command but when I did so  gave me an error that make is unknown command.  what should i do?[/QUOTE]


Don't install it that way. Thats compiling it from scratch. Do that when there are no other options. Gimp-print exists in the repositories. Use this command to get it:

> sudo apt-get install gimp-print 

---

### Post by Leo_01 on 2006-02-23
I am standing on both side of the fence...
I really like using the command line but for most users it really don't matter.
It is powerful at times but sometimes when you are working for 7 hours on a project in linux what you want is really to point and click.

---

### Post by Kerberos on 2006-02-23
[QUOTE=Leo_01]I am standing on both side of the fence...
I really like using the command line but for most users it really don't matter.
It is powerful at times but sometimes when you are working for 7 hours on a project in linux what you want is really to point and click.[/QUOTE]
I find it sad that there is such a resistance to GUI tools under the belief that having them will somehow diminish the power of the CLI.  I would like a situation where you could use it if you wanted, but could get away with not touching it if you didn't want to.  At the moment it seems like 'our way or the highway'.  I find myself using the CLI a lot more than I'd like and I really don't like having to search blogs + man pages for something that should be obvious through a GUI - people argue against being able to double click .deb's (and you still can't) as 'you can do it in the CLI'.  Its ridiculous.

---

### Post by DrFunkenstein on 2006-02-23
[QUOTE=Kerberos]I find it sad that there is such a resistance to GUI tools under the belief that having them will somehow diminish the power of the CLI.  
[/quote]
I don't think there really is. At least not with those people who actually matter, that is, those responsible for the big distributions and those actually working on the various desktop environments.

[QUOTE=Kerberos]
I would like a situation where you could use it if you wanted, but could get away with not touching it if you didn't want to.  At the moment it seems like 'our way or the highway'.
[/quote]
I absolutely agree. However, I think if you use distros that offer more graphical setup tools, like Suse or Mandriva for example, you'll find that a situation like the one you are looking for is already pretty much a reality.

[QUOTE=Kerberos]
I find myself using the CLI a lot more than I'd like and I really don't like having to search blogs + man pages for something that should be obvious through a GUI - people argue against being able to double click .deb's (and you still can't) as 'you can do it in the CLI'.  Its ridiculous.[/QUOTE]
I agree. But then again, nobody really argued that having a graphical app for this in Ubuntu was somehow evil. There just wasn't a program that really did this in a sane way until now. In Dapper however there'll be gdebi, which does exactly what you describe. And again, using other distros you'd already have this kind of functionality anyway.

---

### Post by Leo_01 on 2006-02-23
I would actually prefer working in GUI...
it seems so much easier for a new linux user to work with...(most new users are only know a small bit of commands)

---

### Post by joflow on 2006-02-23
[QUOTE=aysiu]Sure. Take, for example, this [HowTo I wrote on removing Kubuntu.](http://www.ubuntuforums.org/showthread.php?t=96048) With one command copied and pasted into the terminal, you can remove a full set of applications. That same thing would take at least ten minutes (if not more) to do in Synaptic Package Manager.

 You can give directions however *you* want, but it always takes me longer to give directions for GUI than command-line. Occasionally, if someone *really* has a hard time understanding something, I'll do a screenshot and circle in red the appropriate button to push, but usually I'll just say, "copy and paste this command."[/QUOTE]

I agree that using apt-get via the commandline is way faster and 100% better then via synaptic.  I always use apt-get when I know what program I need.  I only use "add programs" when looking for new programs I may not be familiar with.


I guess I was looking for a really advanced example that has a big "wow" factor.  Maybe all the "all powerful cli" talk has got me expecting a little too much.

Maybe you can help me with this though.  I also heard talk of vim being really powerful.  From what I understand, its just an text editor with a cli.  I don't understand how this can be that great but thats probably just the result of my "windows way" line of thought.  Are you familiar with this program and why its considered so powerful?

---

### Post by somuchfortheafter on 2006-02-23
once you learn the shortcuts you do not have to move your hands from the keyboard so it makes it faster in that sense. I'm just a casual user though so I am not familiar with the more advanced features of vim

---

### Post by Brunellus on 2006-02-23
vi versus emacs is a great holy war.  I like vim, because I can keep my hands down on the home row of keys and move very quickly.

---

### Post by Takis on 2006-02-24
[QUOTE=Brunellus]vi versus emacs is a great holy war.  I like vim, because I can keep my hands down on the home row of keys and move very quickly.[/QUOTE]
Oh let's not get started on vi vs emacs again. You may as well start up a debate about left vs right...

---

### Post by BobSongs on 2006-02-25
lol!!

---

### Post by BobSongs on 2006-02-25
A simple area where the command line is fun is in changing file permissions and owner of files. I transfer lots of stuff out of my Windows partitions. I use Nautilus with root permissions to graphically pick and choose what I want to keep.

However it all ends up in my documents folder with few permissions and all owned by root. Do you have **any** idea how long it takes to change all those permissions and owners? Gah!!

But at the command prompt I just type:```
cd Documents
sudo chmod 740 -R *
sudo chown bob:bob -R *
```and it's done. I will argue tooth and nail for GUI, guys. But when I see how fast this changes the file permissions for all my photos and sound files and art work... it's an open and shut case.

True. Moving files one at a time in the CLI might be fun for some people. Not me. But changing file permission? CLI all the way.

---

### Post by red_Marvin on 2006-02-25
As someone who has used DOS on several low-end computers at home,
I feel quite at $HOME (:p) with the linux cli, but I can see how other new users could
be scared away, however my opinion is that a user who keeps his/her mind open
and doesn't run away from every obstacle, is the one that has best chanses of
succeeding anyway.

---

### Post by aysiu on 2006-03-21
I'm currently at a users' conference for the database our school uses, and one of the workshops was on GUI (currently most schools that use this database are using terminal mode, but they'll be forced to use GUI for the next release).

People are *very* resistant to GUI because the rendering time is slow, and they have to use the mouse for certain things (and the mouse is slow). There's no way to jump to a field--you either have to tab to get there (which can be *many* tabs) or use your mouse to click into the field.

This has taught me a few things:

1. People use what they're used to. It doesn't matter how "friendly," "pretty," or "easy" things are. Familiarity is always "better" for people than the unfamiliar.

2. Using the keyboard is almost always faster, and when it comes to productivity, faster is always better than "good looks" or "discoverability," especially in the workplace.

The workshop basically started with the presenter trying to say that the new GUI interface should be easy to use for users already familiar with Windows and look how pretty it is...

Very soon afterwards, people began asking questions (quite angrily, actually): How can I do this in GUI? What's the keyboard shortcut for such-and-such? How can I get the GUI to be faster? Sometimes people will type faster than the screen can receive the input in GUI... how can we deal with that?

The bottom line for schools, corporations, any workplace that's dependent on productivity is... productivity--efficiency, speed, accuracy. GUI isn't the be-all and end-all of the user experience. Maybe it is if you're playing around at home, but at work people just want to get things done... and fast.

---

### Post by Jucato on 2006-03-21
1. I agree. Behavior, habits, and customs have a big effect in what you use, not only in computers but in real life as well. If you were raised in a GUI world, a CLI is scary. If you were taught how to do things in a CLI, a GUI would be too cumbersome. It's just how our brain is wired. Nevertheless, change can sometimes be a good thing. In learning how to use both a GUI and a CLI, you become flexible in whatever situation.

2. That depends. If you're a slow typist or have a not so good memory, a pure CLI would be a nightmare for you. Also, there are some things best done in either interface. though a CLI has it's power, it also has it's limitation. a GUI provides a visual, and perhaps more understable, representation of the structure of your filesystem. also, a GUI allows you to easily copy/move files embedded within layers and layers of folders to another folder (try typing sudo cp ~/username/folder1/folder2/folder3/folder4 /etc/folder1/folder2... :D). But then, if GUI features/options are hidden within so many menus, it will be cumbersome as well.

Personally, until the day comes when I can actually use a touchscreen monitor and type on the monitor itself, I will always love using the keyboard. Contrary to what others think, I find typing in commands in the terminal to be more sci-fi/hi-tech than always using the GUI. :D

---

### Post by Kerberos on 2006-03-21
The CLI is inferior to the GUI when it comes to usability.  This is an unavoidable fact.  Your personal preference may be for the CLI but trying to brand it as 'easy to use' is, to be honest, complete nonsense and shows a lack of understanding of modern computer systems and their users.

A: You need to know a commands name before you can use it.  None are particularly guessable and you won't know what commands you need to know, or what is more appropriate to the task at hand unless you read lots of documentation first.

B: You need to know a commands syntax before you can use it.  This varies wildly from command to command, with different switches to do different things (some not obvious, poorly documented, not documented).  But again you need to wade through documentation before you can actually do anything.

C: It takes much longer to get used to the CLI paradigm, and things like paths, absolute paths, switches, pipes etc.  People can get the hang of icons, double clicking etc, but getting into the CLI mindset is much, much harder than using a GUI with automation.

D: If you don't have internet, or are trying to get internet working then your pretty screwed unless you have a book or a manual on hand.  And you won't know to look at the man pages unless someone tells you they are there.

Compared to the GUI where the goal is to provide the user with options in a logical and consistant way so that they can easily figure out what they are doing, whats achievable and what they can do.  There are many examples of bad GUI design that are held up as examples of why CLI's are superior, but usually all what they prove is some people dont understand interface design.  Usually clippy is dragged out (who hasn't been present in office for a serious amount of time) as a strawman argument as to why GUI's suck, but its actually clippy that sucks, not GUI's.

The goal of a truly usable system is it can be operated without documentation.  A CLI system **cannot** be operated without massive quantites of documentation that the user is required to read all of at least once.  Sure, its faster, more flexible, more powerful, more interesting but it is anything but user friendly.

I find people that hark on about how CLI is 'easy' and how vi and emacs are 'the only editors' are really only trying to impress people with how clever they are.

---

### Post by Stormy Eyes on 2006-03-21
[QUOTE=Kerberos]The goal of a truly usable system is it can be operated without documentation.[/QUOTE]

I suspect that any system complex enough to be *worth* using is probably going to need a manual. For Hell's sake, even Nintendo consoles come with a user's manual.

---

### Post by Kerberos on 2006-03-21
[QUOTE=Stormy Eyes]I suspect that any system complex enough to be *worth* using is probably going to need a manual. For Hell's sake, even Nintendo consoles come with a user's manual.[/QUOTE]
My toaster came with a manual.  The fact that I didn't need to bother reading it to figure out how the aforementioned toaster works is the point.

---

### Post by mcduck on 2006-03-21
[QUOTE=Kerberos]The CLI is inferior to the GUI when it comes to usability.  This is an unavoidable fact.  Your personal preference may be for the CLI but trying to brand it as 'easy to use' is, to be honest, complete nonsense and shows a lack of understanding of modern computer systems and their users.....
[/QUOTE]
You are now confusing 'easy to learn' with 'easy to use' :)

---

### Post by aysiu on 2006-03-21
Kerberos, I think I went over in my first post in quite a bit of detail the different types of "easy" there are.

The only "easy" you seem to really care about is the "easy" you don't need to memorize that's "discoverable." That's a valid concern, but it is *not* the only concern.

You learn something once... maybe twice, but you may use it a million times, especially in a work setting, where so often you do the same job over and over and over again.

In the workplace, people are mainly concerned with productivity--how much they can get done the fastest and with the fewest number of steps. If they can *also* learn how to do it quickly and without much instruction, they'll be happy about that, too, but efficiency is the #1 priority, not the intuitiveness of how discoverable the interface is.

---

### Post by joflow on 2006-03-21
CLI is "user-friendly" for advanced users in the sense that its fast (I guess).

The CLI is not "user-friendly" for new/casual users because it has a higher learning curve.

Someone remotely familiar with windows can probably figure their way around Gnome without much assistance.

But being a DOS expert isn't going to help you with BASH unless you have a list of commands handy.

I would like to use the CLI more but I don't know what its capable of.  Everyone seems to talk about using the CLI for apt and dpkg.  Thats great (I use apt almost exclusively unless I dont know what the package name is) but I don't sit around installing programs all day.  What else can it do (other then copy,move,delete files)?  Examples like the one posted here regarding burning daily backups would be useful.  I really want to learn the CLI, I just need a reason to learn it.

---

### Post by Brunellus on 2006-03-21
the commandline is handy for a lot of stuff.  editing textfiles in vim or nano is a lot faster than doing the same in gedit, for instance.  

also, it's great for trudging through log files.  cat, grep, pipes, and redirects are your friends.

Oh, and various command-line utilities.  my favorite is rsync, which synchronizes two directories (usually used to back up files to a remote host.  I use it to sync my music to my mp3 player).

I knew DOS.  it's taken me a while to get comfy with bash, but now that I've used bash, I wonder where it's been all my life.  I really like it.

---

### Post by joflow on 2006-03-21
[QUOTE=Brunellus]the commandline is handy for a lot of stuff.  editing textfiles in vim or nano is a lot faster than doing the same in gedit, for instance.  

also, it's great for trudging through log files.  cat, grep, pipes, and redirects are your friends.

Oh, and various command-line utilities.  my favorite is rsync, which synchronizes two directories (usually used to back up files to a remote host.  I use it to sync my music to my mp3 player).

I knew DOS.  it's taken me a while to get comfy with bash, but now that I've used bash, I wonder where it's been all my life.  I really like it.[/QUOTE]

Say I have a MythTV backend...

Could I use BASH to go through the mysql database that is holding the "season pass" shows I recorded and then go through the TV listings and find similar shows based on some criteria (say if I record Law and Order, it finds other legal dramas) and then add them to the recording queue similar to Tivo's recommond a show type feature.

rsync seems like it would useful in a script when I get my mythtv backend/samba file server up and running.

---

### Post by mcduck on 2006-03-21
I do most of my everyday image-editing with CLI. Most of the time I use CLI app to play my music. I sometimes surf the web with CLI (links). I'd like to learn to use vim better because it seems to be very poverful and fast way to edit text file. And sometimes I even use CLI to play some videos, just to show my friends that you can do pretty much anything with command line :)

The question is what you can't do with CLI ;)

And yes, knowing DOS has helped me with bash. The commands are different, but the basic idea is the same. (and 'dir' even worked, altough I soon learned to use 'ls' instead to get nice colors) Just like knowing Gnome or Windows or any other GUI helps you to learn to use other GUI's, as you already know about mouse and pointing and clicking things, dropdown menus and such :)

---

### Post by Jucato on 2006-03-21
You can edit images in CLI? wow! how?

Well, you can't play graphical games in a CLI. :D

---

### Post by mcduck on 2006-03-22
[QUOTE=Fenyx]You can edit images in CLI? wow! how?

Well, you can't play graphical games in a CLI. :D[/QUOTE]
no, but you can play text games in CLI :)

The image editing app is 'ImageMagick'. If you want to give it a try, it's in repositories, and here are some nice guides to using it: [http://www.cit.gu.edu.au/~anthony/graphics/imagick6/]("http://www.cit.gu.edu.au/~anthony/graphics/imagick6/")
It's the fastes way to do some quick image resizing, combining images together or compressing them for web use. And it's even better if there are lots of images to resize. And it can do lot mor than that. :)

In short, running 'convert image.png -resize 640x480 -quality 86 image.jpg' is faster than opening any image editor and using it to resize the image and save it as jpg with 86% quality :) And if you have hundreds of images, you can just make a nice script to do this for them all, and go have a cup of coffee while your computer is doing the work for you  :D

---

### Post by BoyOfDestiny on 2006-03-22
[QUOTE=Fenyx]You can edit images in CLI? wow! how?

Well, you can't play graphical games in a CLI. :D[/QUOTE]

Or can you... The answer is maybe, if it can use libcaca or aalib (SDL has support for these). Google textmode quake. 

I have tried it with videos though, try 

mplayer -vo libcaca blahblah.avi

Anyway, you might need to install libcaca and mplayer of course...

Cheers!

---

### Post by Zeroangel on 2006-03-22
I'm a GUI guy myself, having started out on Windows (only using CLI for things like ping and netstat and restoring broken systems). CLI is nice because I am a fast typer and can do things like symlink two folders from far away directories simply by typing that without having to open a nautilus session, open a root nautilus session, navigate to the directories in both folders, right click to create a symbolic link, copy it over, rename it. Same with move and rename operations. As well things like opening a file like /etc/X11/xorg.conf when you only have your web browser open and you want to edit that file RIGHT NOW without having to gksudo nautilus and navigate through the directory structure.

Even if dapper could do everything instantly, I still think GUI would be too slow for some of those operations. So my vote is CLI is fast (and thus becomes user-friendly) in many cases, once you begin to learn things. To me it's like the difference between walking somewhere (GUI) and teleporting there (CLI). With a CLI, you would need to know the precise coordinates, but damn, it is just so cool to just teleport places (metaphorically speaking).

For me, the thing that sold me over to CLI was the tilda dropdown terminal. All I have to do is hit Ctrl+F12 and boom, a CLI drops down, I can execute a command, hit Ctrl+F12 again and it hides itself. Till the next time I need it. :)

---

### Post by 3rdalbum on 2006-03-22
When I started using Ubuntu, I thought "Oh, a command line... how archaic". Now I use the command line all the time (sometimes 'cos there's no other way to do xyz, sometimes for the speed).

However, what I'd really like would be to solve Bug #1 and get all my friends to use Ubuntu. I can manage with a command line, but I know that my barely-computer-literate friends wouldn't cope with it. Heck, one of them didn't know she could download programs to remove the spyware from her machine.

How is someone like that going to use a command line? How are they going to think of doing "man xyz" and reading the documentation to find out how to run a particular program? How are they going to think of doing "gksudo nautilus" to install RealPlayer into a conveniant place? How are they going to figure out what all the folders in the file system mean and do?

The CLI is user-friendly to someone who has picked up how to use it. It's even user-friendly to me, kinda. But to the average person, it's way out of their reach.

---

### Post by fuscia on 2006-03-22
[quote=aysiu]Sure, GUI might be easier if someone were helping you in person. She could say, "Click on that icon. No, that one. See that? Click on it." However, short of doing screenshots (which are time-consuming and bandwidth-consuming), it's very difficult to help someone GUI style over the internet. It is very easy to help someone by saying, "Here, just copy and paste whatever I typed here.[/quote]

i wish i had realized this in the beginning. so much of my early difficulty came in not realizing that i could just copy&paste solutions into the terminal. in this example, cl is *more* user friendly than a gui.

---

### Post by Danni on 2006-03-25
From yesterday, I decided I loved the command line.

I grumbled in another topic about the stupid restrictions my college has put on its network. Yesterday, I decided to try something- I set up SSH on my computer using port 21 (which I knew the college didn't block), downloaded Putty at college, logged into my computer... and I could do anything I wanted to do (which was use messengers and IRC chat, and play TW2002).

I just need to find a CLI web browser, and I'll be able to do everything I want. I even added a new user account to my pc using the command line- adduser was very easy :)

ETA: Just found w3m- it's perfect :)

---

### Post by Stormy Eyes on 2006-03-25
[QUOTE=3rdalbum]How is someone like that going to use a command line? How are they going to think of doing "man xyz" and reading the documentation to find out how to run a particular program?[/QUOTE]

If you're going to persuade your friends to try Linux, then it's *your* responsibility to remind them to RTFM and show them where TFM is and how to get to it. I didn't just give my wife a Linux box when she moved in with me; I sat down with her and showed her around so that she'd know the basics. Sometimes she asks me for help, but most of the time she'll RTFM and figure it out herself -- and then she'll tell me about her problem and how she solved it.

---

### Post by mips on 2006-03-25
If you want to make the command line even simpler then borrow some ideas from Cisco's IOS cli.

I like the fact that you can type "in?" and it shows you all commands starting with "in". It will also autocomplete a abbreviated command if you hit TAB. Also provides a list of all possibilities when you put a ? after a command. Really nice imho.

---

### Post by aysiu on 2006-03-25
[QUOTE=mips]If you want to make the command line even simpler then borrow some ideas from Cisco's IOS cli.

I like the fact that you can type "in?" and it shows you all commands starting with "in". It will also autocomplete a abbreviated command if you hit TAB. Also provides a list of all possibilities when you put a ? after a command. Really nice imho.[/QUOTE] Doesn't this already happen in Ubuntu? ```
in
in                        infotocap                 installkernel
includeres                init                      install-keymap
info                      insmod                    install-language-locales
infobrowser               install                   install-sgmlcatalog
infocmp                   install-docs              instmodsh
infokey                   install-info              invoke-rc.d
```

---

### Post by mips on 2006-03-25
```

user@obelix:~$ in?
bash: in?: command not found

```

How would one do achieve the same result ?

---

### Post by aysiu on 2006-03-25
[QUOTE=mips]```

user@obelix:~$ in?
bash: in?: command not found

```

How would one do achieve the same result ?[/QUOTE] Type *in* and press **Tab** twice.

---

### Post by mips on 2006-03-25
Thanks. Not used to pressing TAB twice, only once in IOS

---

### Post by kabus on 2006-03-25
You can get the same result by hitting Tab only oncce if you put
```

set show-all-if-ambiguous on
```

in your ~/.inputrc.

---

### Post by mstlyevil on 2006-03-25
[QUOTE=aysiu]Type *in* and press **Tab** twice.[/QUOTE]


That is awesome. I just learned something new.

---

### Post by 3rdalbum on 2006-03-26
[QUOTE=Stormy Eyes]If you're going to persuade your friends to try Linux, then it's *your* responsibility to remind them to RTFM and show them where TFM is and how to get to it. I didn't just give my wife a Linux box when she moved in with me; I sat down with her and showed her around so that she'd know the basics. Sometimes she asks me for help, but most of the time she'll RTFM and figure it out herself -- and then she'll tell me about her problem and how she solved it.[/QUOTE]

Oh yes, I agree. But these friends of mine haven't been taught how to use a computer, they've just been taught how to surf the net and send IMs. Those are tasks that don't require TFM. How can you fight that? These 'net friends would prefer not to perform a task than have to read something to do it.

Yeah, sure, you can say that when GNU/Linux matures, it'll start to cater for these people. But preparations for dumbasses to migrate have to start now.

---

### Post by Wolki on 2006-03-27
[QUOTE=mstlyevil]That is awesome. I just learned something new.[/QUOTE]

It gets even better if you enable bash completion - not only will you be able to autocomplete commands ans files, but also arguments - for example, stuff to install with apt-get. Great if you don't know the exact name.

To enable it, uncomment the following section in your ~/.bashrc:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

---

### Post by Stormy Eyes on 2006-03-27
[QUOTE=3rdalbum]Yeah, sure, you can say that when GNU/Linux matures, it'll start to cater for these people. But preparations for dumbasses to migrate have to start now.[/QUOTE]

Why encourage the "dumbasses" to migrate? Believe me, if I thought my wife was *that* kind of user, then I wouldn't have given her a Linux box. I'd have just given her a Dell, done my best to lock it down, and be done with it.

Then again, I probably wouldn't have married her in the first place.

---

### Post by davidmoore83 on 2006-03-30
sorry i haven't read the 13 pages - i yawned after the first post ;)

I just wanted to say your poll is crap. Your options kind of suck. I am an OS X user as well as Ubuntu. I use CLI in OSX as it rocks! So no i haven't gone to OSX because i hate CLI quite the oppostie i went to it for CLI and its Darwin core but also has a GUI on top for other things.

As for your original post - I appreciate where your coming from but NO ubuntu shouldnt change. If you like GUIs etc then stay with windows. No one here cares if you do or not - we don't judge..... an individuals OS is an individuals choice END OF STORY.

---

### Post by Caligula on 2006-04-28
Where do you spend most of your time? using the terminal or the GUI?

Personally I'm currently using the terminal more, I think...

---

### Post by Kimm on 2006-04-28
Even though I use the terminal alot (terminal emulator that is), but I have to say that I use a GUI most of the time.

---

### Post by endersshadow on 2006-04-28
I let this puppy boot right into Gnome...so I'm all GUI.  Of course, I almost always have a terminal open, but I use Firefox, Gaim, and Sylpheed the most...and those are GUI...so there's my pick :)

---

### Post by BoyOfDestiny on 2006-04-28
Hmm I couldn't really vote since I'm not sure. I use terminal for updating, compiling and installing software, using wget, navigating, messing with xorg (although I usually launch gedit unless I'm in trouble, then nano it is), etc. Sometimes for fun I'll use top, bb, links2, pkill a naughty app, etc.

I use gnome... So I use gedit, network manager on my laptop, firefox, gimp, gaim, zsnes, nautilus, the nautilus burner, synaptic, etc...

I think both are useful, some tasks I prefer/or feel like using terminal. Others I just use point and click.

CLI is like finding an old friend, with tab completion and all the useful utils (some which may or may not have front-ends) what can I say, it rocks.

Gnome itself is simple and clean, a breathe of fresh air after ditching windows. I can fall back on the terminal to accomplish things that gnome won't/can't yet let me do. :)

---

### Post by transactionlogfiller on 2006-04-28
CLI 90% of the time when I'm at work. When at home I'm either using firefox or vlc, in between apt-get upgradeing, so I probably use the GUI more.

---

### Post by helpme on 2006-04-28
Neither.
I interact with my box through sheer willpower.

---

### Post by BWF89 on 2006-04-28
Gui

---

### Post by Kvark on 2006-04-28
GUI programs take up most of my time but I always keep a CLI window open and use it pretty often.

---

### Post by ssam on 2006-04-28
i like a bit of bash/python scripting.

for day to day admin, i think it should be possible to do everything with the gui. unfortunatly some of the guis don't have all the options i need, or are too slow, so i sometimes fall back to cli.

---

### Post by aysiu on 2006-04-28
It depends on what I'm doing. For example, if I know I need a file from the internet and know the exact address, I'd rather *wget* than fire up my web browser and navigate to it. Most of the time, though, I point-and-click.

---

### Post by unbuntu on 2006-04-28
[QUOTE=aysiu]It depends on what I'm doing. For example, if I know I need a file from the internet and know the exact address, I'd rather *wget* than fire up my web browser and navigate to it. Most of the time, though, I point-and-click.[/QUOTE]

exactly

---

### Post by Ensnared on 2006-04-28
My choice isn't among the options.

I spend all my time in the GUI using several CLI windows.

---

### Post by Christmas on 2006-04-28
I use the GUI most of the time. Gaim, Firefox (or Epiphany), X-Chat (omg I had such a terrible experience with BitchX... I was CTCP-ing an entire channel without even knowing it, that lead it to a ban), Synaptic, TVtime (btw there was this funny TV program running in the console and the "image" was created from letters and signs, interesting program but not quite useful since the quality was very bad), XMMS. So as you can see all is GUI.

I use the terminal for commands like "dpkg", sometimes because it's faster even with "apt-get" otherwise I prefer Synaptic. For editing txt files I use Gedit but when I'm in terminal it's faster to use Nano. I can't remember other tasks that I use terminal for, but there are some more. I prefer GUI but I don't blame CLI, not at all. I came from the Windows world so this is probably why I am used to GUI.

---

### Post by super on 2006-04-28
i would say gui if only because when i use the cli its almost always while i'm in gnome or e17.

but as already mentioned, it depends what i'm doing. it's much easier (for me) to learn a program by poking around the gui than it is to learn by reading the man pages. but if i know what i'm doing and how to do it, then the cli is faster by far.

---

### Post by Matchless on 2006-05-07
Hi,
   Something that really has me wondering is why all howto's, wikkis and help in 99.9% of cases give only the command line solution instead of the method using the Ubuntu application GUI?
This is very well for a user whose hobby is linux, but can be off-putting to a new user who wants linux as a tool. When, say, advising on installing a program, advising on how to use Synaptic to enable the repositories and install the application makes more sense to me imho than advising a newbie on how to apt-get.
Thoughts on this, but no flames please!

---

### Post by ubuntu27 on 2006-05-07
I also asked myself that question too!

Maybe we should provide both solution in GUI and Terminal...

No, that will occupy too much space (bandwidth) and will take more time. 



I think that providing answer on how to do things using the terminal is a good thing since it will give the end user a sense of familiarization. I mean there will be crucial times when you absolutely will have to touch the terminal. The user should feel confortable to use the terminal from the beguining.


And besides the fact that if we show then only solutions with GUI, the new user coming from a OS that uses GUI for everything [Like Windows], the user will feel that everything should have a GUI which is not true.



That's my $100 ;)  [2 cents? nah! that's too cheap! :P ]

---

### Post by Kvark on 2006-05-07
It is easier to type the exact commands then to type "click on that round looking icon and then click on the thrid button in the window that opens and then click on then click on that thing to the left...". If howtos would use the GUI way then they should be graphical videos showing where to click and that would take too much bandwidth. Since we're stuck with text howtos due to bandwidth it's best to use the text interface. Also commands can often be copy pasted from the howto to the terminal, you can't copy paste clicks.

---

### Post by Omnios on 2006-05-07
It boils down to the difficulty and time needed to explain how to explain something graphicaly. Also making a graphical how to takes a long time compared to a terminal based solution. Needless to say it is less time consumming and more accurate to give a terminal based solution than try to explain it graphicaly. Though I di manage to make one graphical how to but it is on something very basic and simple. In my signature, Adding Repositories Graphicly.

---

### Post by mips on 2006-05-07
We choose to use the cli not because it easy but because it is hard...

Think it is quiker to do a howto with the cli than do window captures for those making the howto. The reader on the other hand might experience the opposite.

---

### Post by zenwhen on 2006-05-07
It is much harder to read directions about clicking in certain places than it is to copy and paste commands into a box.

---

### Post by aysiu on 2006-05-07
I think it's best for someone to see something like this first...
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

... and then see something like this second...
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

My guide (the second link) is less likely to end with an error on the user end (just copy and paste commands), and if it does bring up an error, the error will probably give you more information (oftentimes, with graphical programs, when they fail, the window simply disappears or crashes) about what went wrong.

It also, as others have mentioned, uses less bandwidth, and my web host doesn't give me a whole lot for pictures, considering the kind of traffic my site gets.

My guide is more intimidating to newcomers, though. Screenshots make new users feel more comfortable. It doesn't mean the instructions are easy or less prone to error.

The worst part about screenshots is that they just don't work sometimes. Someone may think, "Hey, that guide had this dialogue pop up after that last step. I don't have that dialogue." Or they may be using Adept instead of Synaptic and get confused. Terminal commands are the same in XFCE, KDE, Gnome, IceWM, Fluxbox, Blackbox, Enlightenment...

Graphical tools vary greatly depending on the environment.

In summary:

**Commands:** Consistency, less error, more feedback, less bandwidth, less time to explain, more intimidation

**Screenshots:** Inconsistency, more room for error, less feedback, more bandwidth, more explanations, less intimidation

---

### Post by Parkotron on 2006-05-07
I think compatability across the different desktop environments is the biggest reason, although all the above mentioned reasons are valid.

---

### Post by mike998 on 2006-05-07
[QUOTE=Parkotron]I think compatability across the different desktop environments is the biggest reason, although all the above mentioned reasons are valid.[/QUOTE]

You beat me to it.

I use XFCE, someone else might use KDE, Gnome, Fluxbox or some other Desktop Enviroment.
Going to the basics is what can help a greater percentage of users.  The basics are the CLI.  Like it or lump it, the CLI is the common feature.  It's scary at first but when you get used to it, it gets easier.  (A no-duh! on that one, please!)

---

### Post by Sutekh on 2006-05-07
I think learning to do a process from the command line gives you a greater understanding of how the corresponding GUI works.  Just clicking here and there is a slower, less effective approach to learning in my opinion.  

The better I learn how a process works, the less likely I am to make errors.

---

### Post by briancurtin on 2006-05-07
everyone wants the easy way out these days, as opposed to the efficient way.

---

### Post by fuscia on 2006-05-07
not only is it easier and more efficient for the person being helped, it's a lot easier for the helper to provide a couple of lines of text as opposed to coming up with pics of the various panels of gui. something that has eight lines might involve eight different pics. that means the helper has to take screenshots of all of them and then upload them and that's assuming the helper has the same DE/wm. if not, the helper has to install the same DE...etc., etc.. that's asking a bit much.

---

### Post by PrimoTurbo on 2006-05-07
I think Ubuntu needs to make sure that everything that can be done with the terminal can be done using the GUI. The terminal can only be mastered through trial and error and lot’s of time spent reading, while the GUI is a lot more simple especially if it’s designed with simplicity at hand.

One problem I have is that editing xorg.conf or installing a driver for my video card will often mess up my GUI and I’m stuck at terminal trying to figure out how to do stuff. Why is this happening? You should never be left with just a terminal, boot into a simple desktop if all else fails and let the user fix what they need. Editing text files is a waste of time because text files don’t explain anything, make programs and offer GUI solutions with explanations. Having to restore backups or edit files in text mode is a lot of time wasted when the same can be done with 2 clicks.

I think the terminal was a great tool, but Linux should be able to exist with out it since Linux is supposed to be about choice..

***A picture is worth a thousand words...***

---

### Post by PrimoTurbo on 2006-05-07
[QUOTE=fuscia]not only is it easier and more efficient for the person being helped, it's a lot easier for the helper to provide a couple of lines of text as opposed to coming up with pics of the various panels of gui. something that has eight lines might involve eight different pics. that means the helper has to take screenshots of all of them and then upload them and that's assuming the helper has the same DE/wm. if not, the helper has to install the same DE...etc., etc.. that's asking a bit much.[/QUOTE]

If you made everything into GUI, people will be able to use the system after a few hours of use. The terminal is impossible to learn with out reading about all the commands, look at Ubuntu forums. Look how many how-to's are there, one for each program. People waste a lot of time explaing all this stuff. It can easily be done with the GUI.

Downloadable executables should also be used, only the stable stuff should be added to the repos. Dependies should be found by ubuntu and installed when needed for the specific executable.

---

### Post by briancurtin on 2006-05-07
the terminal does not need to be mastered through trial and error. actually, if anything, the GUI is more trial and error. you just click on buttons till shit works.

in your case, theres a reason why some upgrades should be done with X down and at the command line. a bunch of distros ask you to step away from the GUI (no matter what you choose) to upgrade X and some other things.

---

### Post by fuscia on 2006-05-07
[QUOTE=PrimoTurbo]If you made everything into GUI...[/QUOTE]

that hasn't happened yet.

---

### Post by briancurtin on 2006-05-07
[QUOTE=PrimoTurbo]If you made everything into GUI, people will be able to use the system after a few hours of use. The terminal is impossible to learn with out reading about all the commands, look at Ubuntu forums. Look how many how-to's are there, one for each program. People waste a lot of time explaing all this stuff. It can easily be done with the GUI.

Downloadable executables should also be used, only the stable stuff should be added to the repos. Dependies should be found by ubuntu and installed when needed for the specific executable.[/QUOTE]
if people are that lazy and completely dependent on a GUI, dont use linux. seriously.

---

### Post by PrimoTurbo on 2006-05-07
Why shouldn't I use linux if I don't like the terminal? Yeah I know it's mainly about the terminal, but really what's the use for it if GUI can be more simple, efficient and easier to learn. Plus it will give more exposure for Linux. I think ubuntu is a new type of Linux, the old Linux distro's have always failed because they don't provide a complete GUI alternative. I think Ubuntu needs to expand into this direction, it should be allowed to. 

Linux can do GUI if it's designed to do so! Look what OSX did with Unix. Simple = better, Terminal can be an option for the people who need it/want it.

---

### Post by briancurtin on 2006-05-07
GUI is not more efficient

---

### Post by PrimoTurbo on 2006-05-07
[QUOTE=briancurtin]the terminal does not need to be mastered through trial and error. actually, if anything, the GUI is more trial and error. you just click on buttons till shit works.[/QUOTE]

GUI is a lot easier for trial and error! But there is clearly more trial and error with using Terminal, you have to configure text files for christ sake's. You can type something wrong, for example instead of fglrx you may type fgrlx and bam your video doesn't work. There is no reason to waste time with how-to's if you have a simple GUI solution.

If you argue Linux is about learning about the system, then you should force everyone to compile everything. All people do know is copy and paste all the how-to's, nearly blindly. Untill something doesn't work and they need to find fix.

---

### Post by PrimoTurbo on 2006-05-07
[QUOTE=briancurtin]GUI is not more efficient[/QUOTE]

Clearly it is, it's easier to click a button that does something complex then to look up the specific string. Even if you know Linux don't tell me you don't check for stuff up for specific complex operation which GUI can do with 1 click.

---

### Post by PrimoTurbo on 2006-05-07
If ubuntu really is for human beings then it should be simple, the majority of humans are not educated enough to use computers!

Also the terminal is based on ENGLISH, not everyone speaks it! GUI can easily be translated and the visual can stay the same. It's easier for humans.

Commands are hard to remember you will at some point need to refer to something, GUI doesn't need you to remember a lot of information it will show you what you need to do or explain it in simple terms. Then all you have to do is select the option you need.

Linux should not be all technical, if people want to know how stuff works it's their choice Linux will always be open they should not be prevented. But learning will take a lot of time and it's very hard to learn. Many people will not be able to grasp this, they just want to do something specific like check the news or check the weather or watch a movie or listen to music. They don't want to be bombed by all the technical stuff. Simplicity is the key here!

---

### Post by Sheinar on 2006-05-07
[QUOTE=PrimoTurbo]the majority of humans are not educated enough to use computers![/QUOTE]
Then they shouldn't be using computers until they're educated.

---

### Post by briancurtin on 2006-05-07
[QUOTE=PrimoTurbo]you have to configure text files for christ sake's.[/QUOTE]
oh heavens no. configuring text files is just so hard! linux is not for you.

---

### Post by briancurtin on 2006-05-07
[QUOTE=PrimoTurbo]Clearly it is, it's easier to click a button that does something complex then to look up the specific string. Even if you know Linux don't tell me you don't check for stuff up for specific complex operation which GUI can do with 1 click.[/QUOTE]
no, im saying you are wrong, and it has been shown several times that typing is more effective than GUIs. i cant remember any of the studies done off the top of my head, but they have been done. my dad used to reference one from when he worked at bell labs in the late 80s and it was passed around there

also, using the keyboard is also shown to be healthier. the more you use the mouse, the greater the chance you will run into RSI or whatever, carpal tunnel. thats not really a striking issue to be brought to this, but its worth mentioning.

---

### Post by fuscia on 2006-05-07
even if one were to agree that GUIs are more retard proof, that doesn't make it any easier to help someone with a problem. refering to a GUI still requires all the effort to make screenshots. how would you expect someone who only uses openbox to help someone who only uses KDE?

---

### Post by Sheinar on 2006-05-07
[QUOTE=fuscia]even if one were to agree that GUIs are more retard proof, that doesn't make it any easier to help someone with a problem. refering to a GUI still requires all the effort to make screenshots. how would you expect someone who only uses openbox to help someone who only uses KDE?[/QUOTE]
Because if you're going to help someone out, you must have every desktop environment available installed and then make guides for every single one of them. Durr.

---

### Post by fuscia on 2006-05-07
[IMG]http://img.photobucket.com/albums/v342/unknownentity/echo.jpg[/IMG]

---

### Post by fuscia on 2006-05-07
[quote=Primo]The same way people have different How-To's for Gnome & Kubuntu. Setup a wiki let people do it! But we are talking about Ubuntu here, Ubuntu is Gnome based! So only 1 is fine.[/quote]

one *isn't* fine, not if you have a whole bunch of people using different GUIs. if you want all the help to be GUI based, then you have to address all the GUIs. the commandline can do this now.

---

### Post by Omnios on 2006-05-07
Both Gui and terminal have there virtues, On one hand you have people who can't type well yet and the other you have people who can't follow simple directions. Either way there is going to be difficulties. Needless to say things are leaning towards terminal based commands right now, though I am seeing more and more phraphical stuff (KDE anyone). From what I hear outside of Ubuntu KDE is getting real popular.

---

### Post by Sutekh on 2006-05-07
KDE has always been the more popular desktop environment.  Ubuntu is an exception.

---

### Post by PrimoTurbo on 2006-05-07
[QUOTE=fuscia]one *isn't* fine, not if you have a whole bunch of people using different GUIs. if you want all the help to be GUI based, then you have to address all the GUIs. the commandline can do this now.[/QUOTE]

The current Ubuntu How-To's are not made for anything besides Gnome, they might work in some cases but in most it needs to be adjusted. For example adding shortcuts to a panel. But really we are talking about Ubuntu not Kubuntu here. This is Ubuntu Cafe...

Anyways your picture is a poor example of GUI, it's more like.

More like

[img]http://www.barringtonstoke.co.uk/images/help/mac_display.gif[/img]
vs
[img]http://shweps.free.fr/minislack_howto_html/minislack_howto_files/image076.jpg[/img]

Tell me what's easier, simpler, faster and more efficent?

Just because you are more used to Terminal in Linux doesn't mean that it's better. The Terminal should always be avaliable for the people who want to use it. Ubuntu is not like other Linux distro's clearly it's for beginers but still packs a lot of power. Ubuntu needs to embrace GUI and I have a feeling it will with each release! If you are crazy about configuration using text go use Gentoo it's made for people like you! If you want to use Ubuntu then use it? What is your problem with expanding the GUI? Why can't Linux be easier while still having power?

---

### Post by PrimoTurbo on 2006-05-07
[QUOTE=Omnios]Both Gui and terminal have there virtues, On one hand you have people who can't type well yet and the other you have people who can't follow simple directions. Either way there is going to be difficulties. Needless to say things are leaning towards terminal based commands right now, though I am seeing more and more phraphical stuff (KDE anyone). From what I hear outside of Ubuntu KDE is getting real popular.[/QUOTE]

The question is, why is direction even needed? Why can't the GUI be made so simple that as soon as you test it for 30 minutes you know how to use the computer. You can easily install, update, etc...Ubuntu already can do this better then any other distro I've seen. The problem is that not everything can be done from GUI. I want to install all drivers from GUI, I don't want to mess with settings or back up text files. I simply want to add 3d support, if it doesn't work then it let's me try a different set of drivers. It doesn't break, the GUI should always be there.

---

### Post by Sheinar on 2006-05-07
[QUOTE=PrimoTurbo]Right, so you shouldn't be using a computer until you know exactly how it works and what each part is doing? If someone needs to check their email and read a message someone sent them, they shouldn't need to know anything about computers.[/QUOTE]
Er, no, when did I say anything about needing to know exactly how it works and what each part is doing? But yes, if you're going to use a computer, you should at least have basic knowledge. Should we made a Fisher Price-like UI for these people who wish to use computers but don't want to even understand the very vitals to using one?

---

### Post by PrimoTurbo on 2006-05-07
Yes you should make it simple and logical if that's what you mean. Why do you deliberate want a difficult and confusing computer interface? Linux is able to do this, this is why Linux is so great.

---

### Post by briancurtin on 2006-05-07
[QUOTE=PrimoTurbo]Typing is more effective than GUI? Yeah maybe for executing a single command! But how can you possibly remember everything? YOU CAN’T!!! You have to refer back and forth for certain things, GUI is visual and you don’t need to find a command for something in order to enable something. You dad used to reference something? Your dad was full of crap or he didn't know what he was talking about or maybe it was something that only applied to the technolodgy of the 80s where GUI was nearly non existent!!! But yeah show me some recent studies that show that the terminal is more efficent then GUI![/QUOTE]
please learn how to read. you are mixing up two separate things. my *opinion* is that the command line is more *efficient*. that has nothing at all to do with the health issue i touched on lightly.

do you use the mouse a lot? RSI will probably come to you. studies have shown, and people on this board and every other board i have ever read, will agree that the less you can use the keyboard - the better you will be in the long run. i believe we have had a few debates on this, and the general consensus from some of the "elders" of the computing world was "use the keyboard as much as possible, dont touch the mouse." i had a professor who has pretty bad RSI in her right wrist...guess why - using the mouse all the time, clicking on buttons, etc. also, my father was not and is not full of crap. get to know some people who have been around in computing and you will hear the same thing. for people like yourself, wiping your *** should be done by a GUI. for people who show that they have some sort of skill, or would like to obtain some sort of skill, and would prefer a more efficient way to do things, they will continue to (and start to, for those that havent begun) make use of the command line interface.

---

### Post by PrimoTurbo on 2006-05-07
[QUOTE=Sheinar]But yes, if you're going to use a computer, you should at least have basic knowledge.[/QUOTE]

Basic knowledge is historically dialectical, if you make the GUI smart then all the person will need to know about Basic knowledge is how to press the on button and how to use the keyboard and mouse! 30-50 years ago you would need to know how to program just to use a computer..That would of been basic knowledge.

What I think you mean is that you want people to know how computers work, but this is stupid because it's far too difficult, all we grasp is the basics. Computers become more and more complex you can never know how everything really works!

---

### Post by PrimoTurbo on 2006-05-07
[QUOTE=briancurtin]do you use the mouse a lot? RSI will probably come to you. studies have shown.[/QUOTE]

LET'S SEE THE STUDIES!!! FFS...

Studies have shown that people who claim studies have shown with out showing the studies are making up such studies!

---

### Post by PrimoTurbo on 2006-05-07
Read this:

[http://cm.bell-labs.com/wiki/plan9/Mouse_vs._keyboard/index.html](http://cm.bell-labs.com/wiki/plan9/Mouse_vs._keyboard/index.html)

> Perhaps the most common frustration experienced by Unix users when trying Plan 9 is that they have to use the mouse more.

The most common complaint is that using the mouse is slow compared with cursoring around, whether via arrow keys or via hjkl (in vi, etc.). This simply isn't true. The mouse seems slow but is actually faster: 

---

### Post by fuscia on 2006-05-08
[QUOTE=PrimoTurbo]But really we are talking about Ubuntu not Kubuntu here. This is Ubuntu Cafe...[/quote]

i have ubuntu installed and i use kde and openbox. look through the ubuntu cafe and you'll see that a lot of people who have ubuntu installed are using DE/wms other than gnome. if you can find a GUI based how-to on synaptic, you can go in there and see all sorts of window managers available to ubuntu users.

---

### Post by PrimoTurbo on 2006-05-08
[QUOTE=briancurtin]look it up on google, jackass. i told you they exist, if you want to see them, go for it.

also, plan 9 is not associated with my dad did, so dont prove yourself to be anymore stupid by claiming he was associated with that.

im done with this thread. people who know, know. those who dont, will know soon enough.[/QUOTE]

Your Dad and Plan 9? You didn't even read it, check the links. It basicly proves that keyboard doesn't mean more efficient. There are some lengthy information about keyboard shortcuts and such. What this also means is that terminal is not more efficient like you claim, despite what you say. Maybe it's more efficient for you because you don't know how to use the mouse? Maybe you have mouseophobia because of what your Dad told you based on some study that you cannot provide a reference to. 

If you are going to try to prove something you might want to provide a reference. Especially in a lengthy argument..."look it up on google, jackass" doesn't cut it and resorting to flames won't help you prove your point.

Let's see the studies...

---

### Post by PrimoTurbo on 2006-05-08
[QUOTE=fuscia]i have ubuntu installed and i use kde and openbox. look through the ubuntu cafe and you'll see that a lot of people who have ubuntu installed are using DE/wms other than gnome. if you can find a GUI based how-to on synaptic, you can go in there and see all sorts of window managers available to ubuntu users.[/QUOTE]

Fair enough, but like I said before a wiki would sort this.

---

### Post by aysiu on 2006-05-08
Just to get people back on track, the original question asked why HowTos and the Wiki give command-line instruction.

We shouldn't be arguing about whether or not there should exist GUI frontends for terminal tasks. I think everyone agrees that for every task, you should be able to do it via terminal *and* GUI--you should always have a choice.

I believe that the same is true for instructions: **ideally**, there should be both point-and-click *and* command-line instructions.

To those who are so adamant about there being more point-and-click instructions, put your money where your mouth is. Instead of wasting your time arguing here that there *should* exist more screenshot tutorials, make one.

I'm impressed with this person:
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

I'm not impressed with people who just think there *should* be graphical tutorials... and then don't create any.

---

### Post by PrimoTurbo on 2006-05-08
I agree with aysiu.

---

### Post by fuscia on 2006-05-08
the mouse is definitely faster in my case. i can't type for ****.

---

### Post by kabus on 2006-05-08
> If ubuntu really is for human beings...
...Linux is supposed to be about choice..

The two stupidest non-arguments that make the rounds on these forums raise their ugly heads again...

> 
the majority of humans are not educated enough to use computers!

It always amazes me how the proponents of 'easy gui tools', 'usability', or whatever this weeks buzzword is manage to insult the intelligence of the people they intend speak for, but that's beside point here...
The howtos that are the topic of this thread actually have very little to do with *using* a computer, they usually deal with system administration. Being your own administrator naturally involves some learning, no matter what type of interface you are using. As mentioned several times in this thread there are practical reasons for giving CLI instructions.

---

### Post by mostwanted on 2006-05-08
I would like to remind everyone to speak in a nice way to one another, we don't need this name-calling on our forum. Do yourself a favour and think about what you're writing before you post it - you will be surprised how often an insult can be substituted with a smiley while the original post retains its meaning. Help conserve the great atmosphere of these boards.

---

### Post by helpme on 2006-05-08
*Sigh*
Why do threads like this always have to turn into flamefests with  pseudo 1337 haX0rs, who tell everyone that the command line is more efficient, because they are able to type apt-get into a terminal, that everyone has to do it their way and that everyone who disagrees shouldn't be using linux.
This is of course especially funny on the ubuntuforums, as Ubuntu strives to be as easy to use and as accessible as possible for everyone and it of course is a slap in the face for all those great developers spending their time and talent on making Linux easier to use.

About the original subject:
I think most of the arguments have already been made, but just to add my 5 cents:
- Command line instructions are easier to write.
- They are cross DE.
- They might even be easier to follow, as copy and past is possible.

---

### Post by Kvark on 2006-05-08
Wow, what a load of junk this thread turned into!

I think everyone agrees that both GUI and CLI should be available. What is the point in arguing which interface is supperior if you all agree that both should be available anyway?

The only real answer to the "which is supperior" question is that it depends on the task. For writing a letter typing is more efficient then pointing and clicking. For drawing an image it's the other way around.

---

### Post by benplaut on 2006-05-08
first of all, (as always), ayisu is perfectly right - if you know enough, do it yourself.

We're all pretty much feeding the troll ATM, and i'd like to say i don't agree with what PrimoTurbo has said - 

here's my opinion:
You can't make a valid argument unless you understand both sides of an issue. Sure, use all the GUI apps you want, but spend a week with Ion and xterms - then you can argue all you want about how much it sucked.

I really hated terminals when i started out, but have learned that typing a single cp command (when using tab completion, of course) takes a fraction of the time to would take to open up a Nautilus or two and copy a file manually.

Both have their place.  If you're exploring, gui fits better (imo). Anything that takes 20 clicks in a gui can usually be accomplished in 5 seconds worth of typing in the terminal.

/heavily biased,
ben

---

### Post by PrimoTurbo on 2006-05-08
All I said was that GUI should be able to do what Terminal can and people started jumping on me claiming that typing is better for you and all sorts of crap. I wasn't trolling, I was trying to get my viewpoint out.

Anyways I don't care anymore, the community is obviously biased and I won't change any opinions or prove anything I'll be called a jackass and flamed.

This is probally why the AlternativeOS™ community is so seperated on many issues, Gnome/KDE, Distros, Linux/BSD, etc.

---

### Post by helpme on 2006-05-08
[QUOTE=PrimoTurbo]
Anyways I don't care anymore, the community is obviously biased and I won't change any opinions or prove anything I'll be called a jackass and flamed.
[/QUOTE]
I can understand your frustrations, however I don't think it's fair to take the behavior (or lack thereof) of one or two people to be indicative of the community as a whole (whatever this community is supposed to be anyway).

---

### Post by mips on 2006-05-08
[QUOTE=PrimoTurbo]Anyways I don't care anymore, the community is obviously biased and I won't change any opinions or prove anything I'll be called a jackass and flamed.
[/QUOTE]

Don't worry about it, let them be. It's most geek driven ;)

I'm pretty comfortable with the cli and can see it's advantages. I do however think guides for newbies should have both gui & cli. When I moved to linux the cli scared the shit outta me, I was very comfortable with the gui as it made a whole lot more sense to me than all these funny commands.

---

### Post by fuscia on 2006-05-08
i'm not sure about this, but right now, i am under the impression that everything that can be done in linux can be done using the cl. that's not true of the GUI.

while there may be some things that can be taken care of more simply through the use of a GUI (ndisgtk, for instance), there are other things where a GUI would make more work, like *sudo deborphan | xargs sudo apt-get -y remove --purge*, for example. is there a way to do that as simply using a GUI? is it true of all GUIs? 

on an old piece of crapola, lots of GUI is too resource consuming. one of the advantages of linux is that is can give new life to a machine that could never run the latest offerings from windows and apple.

using a well tested text based solution to a problem is as simple as copying from one window and pasting on another. less real estate is used in both cases. when using a GUI solution, the more steps there are to that solution, the more likely one will end up with tons of windows open all over the place. and the more complicated the solution, the more effort is required by the person providing the solution. as one who has received far more help than he has given, i want the process of helping me to put as little strain as possible on those who help me.

---

### Post by egon spengler on 2006-05-08
[QUOTE=PrimoTurbo]All I said was that GUI should be able to do what Terminal can and people started jumping on me claiming that typing is better for you and all sorts of crap. I wasn't trolling, I was trying to get my viewpoint out.

Anyways I don't care anymore, the community is obviously biased and I won't change any opinions or prove anything I'll be called a jackass and flamed.

This is probally why the AlternativeOS™ community is so seperated on many issues, Gnome/KDE, Distros, Linux/BSD, etc.[/QUOTE]

To be fair you was using an extremely biased argument yourself, of course clicking a button to select 1280x1024 is easier than editing xorg.conf. But then you don't need to edit xorg.conf to set your resolution

---

### Post by PrimoTurbo on 2006-05-08
That was just an example, for example I need to edit my xorg to change my resolution and refresh rate for my login as it defaults to 70Hz..

---

### Post by TeeAhr1 on 2006-05-08
(haven't read the whole thread, I may be repeating someone else)

The obvious reason: There's a million different desktop environments, each with their own GUI tools.  There's only one BASH.

EDIT: Should have figured a dozen people beat me to the punch ;-)
EDIT/ADD: Enough with the flamewars.  Slashdot's down the hall.

---

### Post by Stormy Eyes on 2006-05-08
[QUOTE=Matchless]Something that really has me wondering is why all howto's, wikkis and help in 99.9% of cases give only the command line solution instead of the method using the Ubuntu application GUI?[/QUOTE]

If you give GUI-oriented instructions, you have to make screenshots and host them somewhere. You also have to deal with the possibility that their GUI isn't configured the same as yours, or that they might be using KDE while you're using GNOME, etc.

Writing GUI-oriented instructions takes more time, and there's more room for misunderstandings. If I give you a set of commands, all you have to do is copy and paste them.

---

### Post by Omnios on 2006-05-08
Um one bonus command line can be done from recovery mode so if you are ever locked out of the GUI command line skills can come in handy.

---

### Post by aysiu on 2006-05-08
I don't see what the point of arguing about this is.

Really.

Most documentation (on the Wiki, in the HowTo section, etc.) is created by users--volunteers. That's right... users just like you and me.

If you want to create better documentation or different documentation, create it. No one's stopping you. You can't demand that other volunteers create documentation the way you want it.

If you strongly believe in graphical instructions, create them. If you don't believe in it that strongly, then deal with the command-line ones.

---

### Post by mike998 on 2006-05-08
I am finding myself frustrated after having read through this thread.

PrimoTurbo has issues with Gnome and Ubuntu - look at his [sig]("http://img182.imageshack.us/img182/6936/ubuntu5jw.jpg") to see that.  That plus his aggressive attitude towards everyone who prefers to use the CLI or has a valid reason for it.

I totally understand his frustrations, but as has been said numerous times before in this thread - If you want something and nobody else is doing it, do it yourself.  I have written how-tos (using the CLI) because I found something cool, or there wasn't a how-to for something I wanted.  It makes me feel good that I am contributing and helping people rather than moaning and crying.

> Thoughts on this, but no flames please!

FIRST POST in the thread!:D

---

### Post by confused57 on 2006-05-08
I think most people starting out with Linux are experienced with windows, where most everything can be done "point and click", executing a few .exe files to install, etc.  GUI "howto's" would be more user friendly to newbies, but I understand the limitations: bandwith, confusion with exactly where to point & click, screenshots,etc.  Using CLI instructions may frustrate new users, but someone serious about using Linux will read, study, and learn as much as they can about the Linux file systems in order to get the most out of their system.

The more GUI friendly Linux is, the more converts there will be; but, that goes back to the statement "Linux is not Windows", so someone expecting it to be like windows should stick with windows.  If they want a distro that's more point and click, try SimplyMepis or PCLinuxOS(or pay for Linspire, Redhat,etc).

I've used windows for years, Linux for only 5 months; but I'm learning how powerful the CLI is and how much easier it is to use for configuring your system & repairing, just try messing around with the registry in windows.

Just my few cents worth....

---

### Post by Stormy Eyes on 2006-05-08
[QUOTE=aysiu]You can't demand that other volunteers create documentation the way you want it.[/QUOTE]

Actually, you *can*, but there are consequences if you do. :evil:

---

### Post by Stormy Eyes on 2006-05-08
[QUOTE=PrimoTurbo]I think the terminal was a great tool, but Linux should be able to exist with out it since Linux is supposed to be about choice..[/QUOTE]

Here's your choice: either implement it yourself, or stop looking gift horses in the mouth.

---

### Post by Omnios on 2006-05-08
Personally I am on a dissability and have a lot of time on my hands. I have writen one graphical how to with app pics. I have writen quite a few short how to's and links pages. This takes time and not eveyone is in the same position as me and they do not have a lot of time on there hands. Needless to say The graphical how to took me about an hour writing it in terminal how to would have taken about 10 min. Also how to's take more than opening the Reply to thread window and typing away. You have to research and refresh on material that your not shure on becuase you have to try to be accurate as possible. Even link pages its good to write a description of the web links not just putting a jumble of links together and then you have to test the links. 

 This all takes time and describing how to use the terminal has the advantage over taking screen shots, editing them, posting them in art work and finaly putting it all together in a how to. I think more graphical how to would be a good thing but dought that you are going to see a lot of them.

---

### Post by Reshin on 2006-05-09
The looks on peoples faces, when I showed them [this page]("https://wiki.ubuntu.com/FirefoxNewVersion"): priceless!

---

### Post by fuscia on 2006-05-09
[QUOTE=Reshin]The looks on peoples faces, when I showed them [this page]("https://wiki.ubuntu.com/FirefoxNewVersion"): priceless![/QUOTE]

i'm sure my face, when i first saw that page, was also priceless. i'm but a humble end user. ten minutes later, though, i had on a different face as i was browsing merrily with my new version of firefox. as far as i know, there is no way to do all that using a gui.

---

### Post by Stormy Eyes on 2006-05-09
[QUOTE=fuscia]i'm sure my face, when i first saw that page, was also priceless. i'm but a humble end user. ten minutes later, though, i had on a different face as i was browsing merrily with my new version of firefox. as far as i know, there is no way to do all that using a gui.[/QUOTE]

Unfortunately for some people, there isn't. To be honest, the command line *is* a power user's tool. I think that it's in Linux's best interest to have as high a ratio of power users to "normal" users as possible.

---

### Post by jethro10 on 2006-05-09
[QUOTE=Omnios]It boils down to the difficulty and time needed to explain how to explain something graphicaly. Also making a graphical how to takes a long time compared to a terminal based solution.........[/QUOTE]

Windows Help forums get by.
As long as Help, which by definition is mostly for newbies, does not go graphical, linux will remain 'difficult' in most non linux users minds.

Jeff

---

### Post by fuscia on 2006-05-09
[QUOTE=Stormy Eyes]Unfortunately for some people, there isn't. To be honest, the command line *is* a power user's tool. I think that it's in Linux's best interest to have as high a ratio of power users to "normal" users as possible.[/QUOTE]

it can also be a retard's tool, though. it's like legs - some can run with the gazelles while others can walk into a tree. something for everyone.

---

### Post by nocturn on 2006-05-09
[QUOTE=PrimoTurbo] All people do know is copy and paste all the how-to's, nearly blindly. Untill something doesn't work and they need to find fix.[/QUOTE]

I'm on these forums most of the day from work.  I can walk you through most stuff using commands without being at my own computer.  But I do not know by heart which buttons to click to do something.

That's why I default to advising stuff like aptitude install mplayer instead of click menu1 > submenu2 > synaptic > search > ...

Also, the CLI is much more powerfull, I can give you a single command to resize all JPG's in a directory (or muliple directories), I cannot do that for a GUI (other then opening each seperate file and clicking some options I do not know by heart either).

---

### Post by nocturn on 2006-05-09
[QUOTE=PrimoTurbo]Clearly it is, it's easier to click a button that does something complex then to look up the specific string. Even if you know Linux don't tell me you don't check for stuff up for specific complex operation which GUI can do with 1 click.[/QUOTE]

I disagree.  GUI's are fine for straight-forward, predictable operations.  They do not scale well beyond that and it is difficult to get two GUI porgrams to work together.

Take find for example, it has many options and allows you to run a command for each hit.  This is not present in the GUI and even if it were, it would be hard to parse the output of GUI find to another program.

---

### Post by Omnios on 2006-05-09
One inportant aspect of command line as you read the forum and solve problems with terminal you also learn how to use it. Though GUI how to's might be fairly easy and good, a lot of people will miss this terminal crash course which may cause problems later on. Another aspect that is holding me back from making a Configuration Editor how to right now is that taking a screen shot with prt Sc will not work while you have a menu open which is a serious drawback. But anyways I think this will be my next project.

---

### Post by nocturn on 2006-05-09
[QUOTE=PrimoTurbo]
Also the terminal is based on ENGLISH, not everyone speaks it! GUI can easily be translated and the visual can stay the same. It's easier for humans.
[/QUOTE]

Yes, but when I try to help you over the forum in the GUI way, I will still recommend you click System -> Add/remove programs -> search -> apply.

Keep in mind that this thread is not about the lack of GUI tools in Ubuntu, which I believe covers nearly every configuration task.  
The question was why a lot of howto's and post revert to commands when there are GUI tools available.

One answer is that a lot of the users helping out here are more used to the CLI as that is what they use most, so when asked for help, they will offer the knowledge they have at hand.

---

### Post by nocturn on 2006-05-09
[QUOTE=briancurtin]oh heavens no. configuring text files is just so hard! linux is not for you.[/QUOTE]

If users do not want to configure text files, they shouldn't have too.  That's clearly one of the goals of Ubuntu.

This is a seperate issue however from the advice given by forum members, who will default to what they are used too (which is in their right, you're trying to help).

---

### Post by Stormy Eyes on 2006-05-09
[QUOTE=nocturn]One answer is that a lot of the users helping out here are more used to the CLI as that is what they use most, so when asked for help, they will offer the knowledge they have at hand.[/QUOTE]

Also, when I am in the mood to help, I can help more people faster if I provide CLI-oriented help than if I waste time taking screenshots.

---

### Post by nocturn on 2006-05-09
[QUOTE=PrimoTurbo]That was just an example, for example I need to edit my xorg to change my resolution and refresh rate for my login as it defaults to 70Hz..[/QUOTE]

You are right in that it is probably the most comfortable way for you to do this, and the lack of a good GUI to configure X is one of the biggest holes in modern Linux distros (sax from SuSE is reasonable).
For setting a screen resolution, even I may turn to using a GUI.

But for many instances, I find the CLI more comfortable, be it biased or not, it's what I'm used to.  When someone gets into trouble and I want to help them out,  I will give them the best advice I know, which often involves command lines.

That said, I 100% agree that there should be a GUI available for everything, but as far as advice on the forums is concerned, the user helping someone out is free to choose the method.

---

### Post by aysiu on 2006-05-09
[QUOTE=Omnios]Another aspect that is holding me back from making a Configuration Editor how to right now is that taking a screen shot with prt Sc will not work while you have a menu open which is a serious drawback. But anyways I think this will be my next project.[/QUOTE] You can do this with a time delay. KSnapshot has this functionality built into it in the GUI. For Gnome's screenshot utility, you need the command-line to delay it: ```
gnome-screenshot --delay 5
``` After you type in that command, you have five seconds to get that menu open.

[quote=PrimoTurbo]
Also the terminal is based on ENGLISH, not everyone speaks it! GUI can easily be translated and the visual can stay the same. It's easier for humans.[/quote] This is why we have multiple Ubuntu Forums. This one is for English-speaking people. English doesn't have to be your native language, but you have to understand English. There are also French forums and other language forums for Ubuntu.

---

### Post by fuscia on 2006-05-09
what's the reason not to use the cl? can't copy&paste? uh...what else?

---

### Post by aysiu on 2006-05-09
[QUOTE=fuscia]what's the reason not to use the cl? can't copy&paste? uh...what else?[/QUOTE] As a relatively new user myself (two weeks until my one-year Ubuntu anniversary), I can attest to the terminal being intimidating at first. Though, now that I'm more comfortable with it, I can't understand why. Someone tells you to type something... you type it. Or, better yet, you copy and paste it. Why is that intimidating?

It's hard for me to rationalize it in retrospect, but I was deathly afraid of the command-line when I first started using Linux.

---

### Post by BoyOfDestiny on 2006-05-09
[QUOTE=fuscia]what's the reason not to use the cl? can't copy&paste? uh...what else?[/QUOTE]

No idea... To be honest it's been a joy for me to edit settings in a text file. It's actually human readable. Usually removing a # or changing a value is great (usually comments above contain the info you need), and I can keep some settings in home (not just /etc) so it survives a new install (like which audio in tvtime uses for the internal audio connection). 

If the editing was mysteriously changing a byte in a file, that is less fun. Also, I think it's easier for someone to make a gui frontend for something human readable vs a mysterious binary config file...

Anyway, I think we are going in the right direction. All the cli stuff and human readable textfiles rock. However, I think there are some users that should never have to deal with it. As we get more things out of the box, and more apps start appearing (I have a feeling an xorg gui app will show up soon, maybe auto compilers like autodeb). 

If you guys are in Dapper take a look at System -> Administration -> Software Properties, allows easy config of the update manager and what repos are enabled.
Applications -> Add/Remove, perfect for the average user IMHO. Almost no learning curve.

So ideally, we'll end up with 2 sets of how-to's for most things. The quick cli (maybe even bash scripts ;) ) and gui how-to for specific apps / desktop environments.

I would definitely be sad if we went the windows route (ok no flames on this), where they went out of their way to "hide" command line. If you want to automate something, you have to get some app that lets you record mouse clicks, highlight certain windows by title, etc. An overall iffy pain in the ***. As for windows server 2003 (what I used to use), no tab completion by default, having to use ~1 for long filenames, just a painful experience.

---

### Post by aysiu on 2006-05-09
[QUOTE=BoyOfDestiny]
So ideally, we'll end up with 2 sets of how-to's for most things. The quick cli (maybe even bash scripts ;) ) and gui how-to for specific apps / desktop environments.[/QUOTE] Yes, ideally. But things don't happen based on what's ideal. Things happen when people make them happen.

For those who want to make the GUI tutorials, go for it. I applaud efforts like this:
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

---

### Post by tseliot on 2006-05-09
[QUOTE=Matchless]Hi,
   Something that really has me wondering is why all howto's, wikkis and help in 99.9% of cases give only the command line solution instead of the method using the Ubuntu application GUI?[/QUOTE]
Isn't the principle of "copying and pasting" commands easy enough?

And BTW in that way you can also know what happens under the hood and learn something.

The GUI way is easy to do but much longer to explain. Oh, and if your Xserver doesn't work (or you don't use it) the GUI way is not an option.

Just my 2 cents.

---

### Post by matthinckley on 2006-05-09
Wow this thread is interesting...

I like the cli how-to's.. gives me a chance to use the utterly awesome highlight and middle-click paste that I'm always trying to use at work on my windows pc...

Also, I think it is awesome that no matter what problem I'm having, program I want to install, option I want to change, whatever.. I can open this one little window on my desktop and make changes to *anything* on my computer.. wow this one little program that opens less than two seconds after I click on the icon sure does do a lot... 

If I didn't have this little program I would spend a lot more time searching through menus and window tabs, and most of the time I don't know what the thing I'm looking for is actually called.

Also, on a side note, almost every config file I've edited has had great comments explaining exactly what each option did, and the ones that didn't had explanations either in the man pages or on a wiki.

just my 2 cents..

Matt

---

### Post by Dr_Deadmeat on 2006-06-08
I preffer to use the terminal than GUI to most things... I'd even started to use wget instead of clicking on links to download things that are to be installed

F.X
```

sudo wget http://www.<thewebsitewearetodownloadfrom/nameoffile>.deb.com && sudo dpkg -i <nameoffile>.deb

```
I love that way to install applications that are not in the standard repos, and I have just started with C++, and g++ is much better than VB I think =P

---

### Post by zolookas on 2006-06-13
I'm not (k/x/ed)Ubuntu user, i'm Archlinux user, but i come here to see how's no #1 Desktop distro is doing. I've noticed that almost every thread has linux console commands such as:
```
wget http://www.example.com/package.deb
```
Why we can't say: "just save this file by right clicking this url?: [http://www.example.com/package.deb](http://www.example.com/package.deb)"

And instead of
```
dpkg -i package.deb
```
double click it and press install.

I mean 70-90% of things can be done using GUI. Synaptic can add your line to /etc/apt/sources.list and "apt-get update" your sources. Also Add/Remove can install many applications beginner friendly way.

Newbies are extremely uncomfortable typing command after command into theyr "terminal" window. Most of the time they don't know that they are doing and starting to think that linux is only for geeks who can do that "command line stuff" every day.

---

### Post by uzi09 on 2006-06-13
1) the command line for linux is an integral part, so you should really get to know it every oppertunity you get.
2) instead of having to sit down and explain where things are in a gui, it is much easier to just tell them to copy/paste a line into the shell and hit enter.
give it a try sometime, try going through the questions and describe what to do using gui only. as easy as using a gui really is, it's easier and less complex to just type (or even copy/paste) commands that someone more experienced provides into a terminal and hitting enter.

for the whole "wget" thing, it could really be done either way, but since people are already working out of the terminal, we (or at least I) just provide the wget format.

---

### Post by glinsvad on 2006-06-13
> 
just save this file by right clicking this url?

What are you - a Windows-user? I kid ;)

I agree with uzi09, primarily because the commands "wget this" and "dpkg -i that" is quite easier than "go to this url, click save as, select some path, open the path, doubleclick this file, click install". Especially when two terminal commands are run subsequently, you are ensured that the user saves and retrieves files from the same path (when using relative paths for filenames of course).

An added bonus is that whenever something spoils your fun, the terminal outputs error information which the user can copy/paste back into the forum. The alternative, i.e. explanations such as "this program said that when I click those things", involves lengthier and somewhat tedious descriptions.

---

### Post by uzi09 on 2006-06-13
you gotta understand...we computer people are a lazy bunch ;)

---

### Post by echo $USER on 2006-06-13
I agree w/ uzi.

---

### Post by zolookas on 2006-06-13
I know command line can save so much time, i've personaly have yakuake on my kde to do updating, files editing, daemons, etc., but i see so much newbies that hate command line like "Oh, man, everything was alright until i've had to enter that command line" and etc. so i just can take it anymore.

---

### Post by angkor on 2006-06-13
[http://www.ubuntuforums.org/showthread.php?t=59334](http://www.ubuntuforums.org/showthread.php?t=59334)

Aysiu's thread reflected my view on the topic quite well.

Think this thread needs to be moved to the cafe or the forum site discussion btw.

---

### Post by grsing on 2006-06-13
It's more precise and easier to describe using terminal commands.  As long as no one makes a typo, exactly what is supposed to happen will happen.  With GUI, you have to describe the buttons and all that.  Plus, as others said, the terminal is part of *nix, people may as well start learning it.

---

### Post by matthew on 2006-06-13
[quote=angkor]Think this thread needs to be moved to the cafe or the forum site discussion btw.[/quote]I agree. Since it is mainly directed at forum users and not the administration I'll put it in the cafe.

---

### Post by blackjack6.21.91 on 2006-06-13
Comprendo.  I agree with this guy.  By showing users what they are actually doing as opposed to just having them paste crap into the command line (everyone can do that), they might actually be learning things, as well as (at least for long time Windows users) having a more comfortable experience.

---

### Post by richbarna on 2006-06-13
Maybe it should be half and half, a bit of give and take ?
We show the new users what to copy and paste so that they can get things working quickly. Then they can do their bit by looking up the commands and READING a bit to help themselves.
That's what I did.
We are all here to help eachother, but we shouldn't forget how to help ourselves.
How many times a week do you see repeated questions because the person can't be bothered to do a forum search ?
Or a simple question that could be found easily on Google.
I am the first person to walk new users through processes, but there has to be some give and take too.

---

### Post by bonzodog on 2006-06-13
For those of you using dapper, the double click and install thing has already happened. There is now a program called gdebi in dapper, which does precisely this. Only thing at the moment though is it does not fetch dependencies, and is merely a point and click front end to dpkg.

---

### Post by Dr. Nick on 2006-06-13
What I do is tell people command line stuff and sort of explan it. Their are 3 different gui distros of ubuntu (gnome, kde, and xfce) It would get very old if you told someone to open synaptic and they came back with "where is it" and you said system - administration, then they responded I only have the "K" Menu

At this point you realize they are not in gnome , but kde. Then you tell them how to use adept.

I know their are subforums to help some of this, But the Absoulte beginner section has no distinctions, And not all users put thier distro in their profile, even if they did it would still be a pain to check each time.

If I see a user specifically mention a gnome question that a gui can solve then I tell the gui method.

Plus learning some basic command line helps when you screw up X :)

---

### Post by poofyhairguy on 2006-06-14
Ok, I have been away from the forums for a few months (I needed time to graduate from college and learn OSX) but this thread has brought me back into the fold. Why?

Because I 100% disagree.

Those helping people learn Linux SHOULD NOT hide the command line. It is not disgraceful or hard. Its just intimidating.

Well....honestly this issue is not completely black or white. There are some people who should probably never see the command line. People like my mother who just uses Ubuntu to browse the web, pound out some documents, etc. are in that group. Yet the default install does not serve these people (lets be honest- Ubuntu without closed media codecs is worthless to most home users) as it is. For them this like EasyUbuntu and Automatix should be used, and quite honestly I believe that in most of these cases that whoever did the hard job of installing the OS for them needs to do the command line work to set up Automatix too. 

But these people are not the issue at hand.

The people who many want to hide the command line from is middle of the road windows users. These people have some sort of computer knowledge (heck, they installed Ubuntu and got past the partitioner) but they are used to a Windows World where EVERYTHING is done by the command line.

Often when people talk about hiding the command line its to hide it from these users. I have heard all the reasons-- it makes them more comfortable, they see the command line as a hold over from the primative DOS days, etc. Yet I don't think any of them are good enough.

We HARM middle of the road Windows converts when we hide the command line early on. Why? Because we put forth a false premise- that you can survive on the Linux desktop at a high level without the command line.

Its simply not true.

Sure nowadays that middle of the road user might get all the codecs set up within a GUI and they might install some basic apps needed as well.

But as soon as they want to do something harder than people like my mom would want to do, they WILL hit the command line wall. The day they buy that new video card and want XGL, or they want to emulate a Playstation game, or the time they want to set up their multibutton mouse they WILL HAVE TO use the command line. Many of the tasks that middle of the road Windows users want to do have no GUI ways to do them (or at least not decent GUI ways to do them) in Linuxland.

Thats a fact of life right now. We do them no service by hiding that fact. I'd rather these middle of the road users are hit with the knowledge DAY ONE that they HAVE TO use the command line to do some things in Linux rather then have them believe that there is a GUI for everything only to be shocked a week or a month in when they find something they want to do that requires some terminal hacking.

In Windowsland there is no decent command line. Developers cannot even make that an option. In Linuxland when a new feature is added it is done in command line FIRST usually, with GUIs later covering this command line program. Sometimes these GUIs are never made. So in the end you are stuck with a system where eventually you will at least have to copy and paste some commands if you have a lot of demands.

New middle of the road users need to know this off the bat. If they don't like it they need to stick with Windows. We can't save the whole world. And hype and deception does not make Linux something it is not (a system where you never need the command line for 99% of stuff).

Linux/Ubuntu is what it is. For many it can increase the quality of their life and we should help them if that is the case. But lets no pretend its something its not to avoid scaring middle of the road Windows users away. Thats how you create the super trolls in the Linux world- you lie to them....

Time to be honest- if you are going to use Ubuntu for much more than the defaults then you will be on the command line eventually! Its a fact of life that is not bad, just different.

Here is my other thread on the subject:

[http://www.ubuntuforums.org/showthread.php?t=43911](http://www.ubuntuforums.org/showthread.php?t=43911)

---

### Post by aysiu on 2006-06-14
What I don't get is the idea that the command-line is primitive.

If anything, it's more sophisticated. It's language. Point-and-click is not a language--it's very similar to the inarticulate gesturing our foreparents used to do to "communicate."

When you can't be bothered to learn a new language, that's often what you do. You cross your legs and jump up and down to indicate a need to go to the bathroom because you don't know how to sound out a coherent sentence in Chinese or Swahili.

Same thing here--to most of us ex-Windows users, Linux is a foreign language. Many times, it's comfortable or more convenient to use the GUI, just as in real life, sometimes I give people the thumbs-up, the OK sign, or the middle finger rather than articulate a sentence.

Still, using the command-line isn't primitive. It's often more sophisticated, just as spoken and written human languages are sophisticated.

I have to agree with Poofyhairyguy on this. There are basically three types of Linux users:

1. Users-only with basic needs. Didn't install Linux themselves--someone else did it for them.
2. ex-Windows power users with sophisticated needs and very little command-line experience.
3. Experiences Linux users with a lot of command-line experience.

Group #1 doesn't need to see the command-line ever, but it's also very unlikely to contain people who would sign up for forum help, anyway.
Group #2, as Poofyhairyguy points out, has sophisticated needs and will, at some point, need to use the command-line for whatever reason.
Group #3 uses it anyway.

---

### Post by AndyCooll on 2006-06-14
I too disagree with the "improvement" suggestion and find myself siding with poofyhairguy and aysiu.

I certainly would not consider myself a command line person. Where possible the gui is for me. However, there are times when the command line "just works". I like Ubuntu precisely because it is a good mix between the two. The gui for most things, but the command line for when you want to delve deeper.

:cool:

---

### Post by angkor on 2006-06-15
[QUOTE=poofyhairguy]Ok, I have been away from the forums for a few months (I needed time to graduate from college and learn OSX) but this thread has brought me back into the fold. [/QUOTE]

Welcome back, Poof. :) With a great post I agree with I might add.

---

### Post by skull_leader on 2006-06-15
Another reason why you'd use wget instead of downloading from a brower is that you can resume a download from wget if you get interrupted, whereas on a browser you'd have to start from the begining. 

I don't know if this is still true on the new Firefox, but it's probably a safer bet to use wget.

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=skull_leader]Another reason why you'd use wget instead of downloading from a brower is that you can resume a download from wget if you get interrupted, whereas on a browser you'd have to start from the begining. 
[/QUOTE]

I didn't know that. Neat!

---

### Post by egon spengler on 2006-06-15
I find it hard to believe that an Arch user is complaining about a lack of GUI tools in ubuntu. Using Arch must be a constant torment for the poor guy

---

### Post by aysiu on 2006-06-15
I think *wget* is just faster if you know the web address. Launching a browsing, typing in the address, and then confirming the download and placement of the download file is too much of a process.

---

### Post by zolookas on 2006-06-16
[QUOTE=egon spengler]Using Arch must be a constant torment for the poor guy[/QUOTE]

Actually not. I use command line everytime (currently two yakuake tabs localhost and ssh) and i don't need gui tools, but i'm talking about newbies, i'm tired of "command line is too hard" comments. If you visit digg.com linux/unix section, osnews.com then you probably know if there's a discussion about linux on the desktop, it's almost 100% i'll find comment like: "only geeks capable using command line, i was forced to use it when i tried ubuntu, i'll stick with windows and etc."

---

### Post by Macchi on 2006-06-16
Command Line Interfaces are good for technical users and developers.
Graphical interfaces are good for most other human beings using computers, including Linux and particularly Ubuntu!







There are different types of users with different levels of skills and different goals while using their favorite personal computer brand and favorite software. The great majority of users have other interests and needs in life than learning the specific technological details behind how computers work. They simply want to USE the computer to achieve very specific goals. 

I think it would be very nice if Linux and Ubuntu manages to fulfill the basic computing needs for most users in the market. Remember: Linux for Human Beings.

Yesterday, while speaking about Linux to a computer technician he reminded me that most of his customers are still learning the basics of using a computer. Their questions are: "What is a right-click?",  "What is a file?", "How do I know the email was sent?". Their perception is that Linux requires learning too complicated things that will not be useful in their daily life.

If you go to a restaurant and ask for a certain dish because you are hungry then you probably don't want to hear a lesson from the chef on how to prepare that particular dish. If you are hungry you prioritize your food first. Eventually you might develop a wish to learn how to prepare your favorite dishes. In the long run it is better to learn how to cook that to give food,  we know that. But for using a computer you don't have to know how it works!

I am sorry to jump into this discussion but I am still surprised to see people talking about command line interfaces and trying to impose them to average computer users, today in year 2006. I could accept that for twenty five years ago when cheap hardware could not deliver the power required for graphical user interfaces and when you needed a masters degree to send an email. 

All this CLI-talk reminds me of the story behind the Xerox PARC and how their amazing research results could be ignored. Command line interfaces were really much more powerful at that time.

---

### Post by aysiu on 2006-06-16
Macchi, if there were a graphical user interface for every single thing intermediate users wanted to do, then you would be correct.

But, as Poofyhairyguy points out, right now most of the people who migrate to Linux are people with more complicated needs than your average user. My mom won't be configuring XGL, but a lot of new Ubuntu users will want to. If you give them the impression they won't need the command-line, it's kind of a bait and switch, isn't it?

I would say you don't need the command-line ever if...

1. You have someone else install and configure Ubuntu for you.
2. You have very simple needs (email, web browsing, light word processing, photo organizing, music listening, some website design, silly games like Gnometris).

If you want to get more complicated than that, roll up your sleeves. Ubuntu is not a restaurant, unless you're going to hire someone to cook for you.

Your analogy doesn't really apply, though. Using the command-line does not make me a programmer. I don't write Ubuntu or its programs. The command-line helps me *use* Ubuntu, just as a graphical interface does. A more appropriate analogy would be people eating with their hands who then have to learn how to eat with forks, knives, spoons, and chopsticks.

---

### Post by zolookas on 2006-06-30
[QUOTE=aysiu]Macchi, if there were a graphical user interface for every single thing intermediate users wanted to do, then you would be correct.[/QUOTE]



Of course you can't do everything using gui. Knowing command line is very useful, but do you expect people to learn command line by pasting things? Maybe, if they are very curious.



[QUOTE=aysiu]But, as Poofyhairyguy points out, right now most of the people who migrate to Linux are people with more complicated needs than your average user. My mom won't be configuring XGL, but a lot of new Ubuntu users will want to. If you give them the impression they won't need the command-line, it's kind of a bait and switch, isn't it?[/QUOTE]



You mom may buy SLED and enable xgl by selecting Desktop Effects in control panel without editing a single file.



[QUOTE=aysiu]silly games like Gnometris.[/QUOTE]



Or buy cedega and play half life 2 after double clicking .deb file.



[QUOTE=poofyhairguy]Yet the default install does not serve these people (lets be honest- Ubuntu without closed media codecs is worthless to most home users) as it is. For them this like EasyUbuntu and Automatix should be used, and quite honestly I believe that in most of these cases that whoever did the hard job of installing the OS for them needs to do the command line work to set up Automatix too.[/QUOTE]



I'm not a Ubuntu Master Roaster, but i think i'm the only one here who knows that you can install xine/gstreamer plugins, flash, java using Add/Remove.

Just think why people are going to buy Novell SLED 10.

---

### Post by aysiu on 2006-07-01
[QUOTE=zolookas]Of course you can't do everything using gui. Knowing command line is very useful, but do you expect people to learn command line by pasting things? Maybe, if they are very curious.[/quote] I did.

Seriously, that's how I learned the command-line, by copying and pasting commands. How else do you learn them?

> You mom may buy SLED and enable xgl by selecting Desktop Effects in control panel without editing a single file. We're talking specifically about Ubuntu, not SuSE.

---

### Post by H.E. Pennypacker on 2006-07-04
I am glad someone else already posted this, because I was planning to post a thread just like this.  Furthermore, I am glad that the original poster (known as "OP") has come forward, despite his allegiance to the command line.  It is whistle-blowers like him who will improve Linux for the sake of the greater good, because most hardline Terminal users refuse to accept change, even if such a change means greater use of Linux in this world.

I wholeheartedly agree that most users need help in figuring out that Linux is not a text-based operating system.  All that copying and pasting makes them think there is no GUI alternative, and that every little thing done in a Linux distro requires use of the command line.  If downloading something is done via the command line, how are they going to listen to music?  They'll never know they can always use a browser, because no one points it out.

It is all about reputation.  Currently, Linux has a reputation for demanding more of its users, when it shouldn't.  The truth is that Linux does not demand knowledge of the unseen and unheard of (the complicated stuff) in many cases.  It's just that many Linux users give Linux converts the impression that they need to know the secrets of this world before they can watch a movie (watching a movie does not require the terminal, but playing around with gstreamer or something can require the terminal), download stuff, etc.

People like aysiu will tell you that you learn from using the Terminal.  I learned from the copying and pasting only because I have the time and interest.  If it wasn't for that interest, I would have never bothered paying attention to what's going on.  Even today, I still don't pay attention at times, and let the command line do what it is supposed to do.

My experience with the Terminal is that it spews out more cryptic errors than the GUI.  Yes, *I* am doing something wrong, but I can tell you those errors are a lot more understandable when it comes from GUI.

OP, thank you for your courage.  The number of aysius (the poster who publicly shares his love for the terminal) will start dwindling as more people like me start using Ubuntu, because as long as people like me are around, Linux will become easier to use day by day.

---

### Post by aysiu on 2006-07-04
I don't see why you're trying to paint me as some kind of command-line Nazi.

I agree in part with the original post-er's general idea--people *do* need to know that the majority of tasks *can* be accomplished through GUI. In fact, I've argued this point numerous times when people have said, "Oh, yeah, everything has to be done with commands." No. I can't think of a single thing I do on my Ubuntu computer that *requires* the command-line.

The point that Poofyhairyguy brought up, and which I also agree with, is that most of the people who migrate to Ubuntu are *not* the mythical "Joe Sixpack," "grandma," or other archetypal incompetent, computer illiterate user.

Most of the people who migrate to Ubuntu have very sophisticated needs and will, at one time or another, need to use the command-line for the 10% of tasks that require it.

You have to paint a balanced picture. On the one hand, the command-line is not required for most things in Ubuntu. On the other hand, you can't sell Ubuntu as totally not needing the command-line at all--that lures people in with false promises, especially power users who want cutting edge software, obscure software, and very special graphical effects.

Now, to go a little off-topic, I don't see what's so wrong about publicly declaring my love for the terminal. Am I a gay man in the 19th century? Am I a feminist in 1950s America? That really has nothing to do with this argument at all.

Also, I will continue to give both GUI and terminal instructions to new users, as appropriate to the situation. There are benefits to both, especially in a text-based forum. When we move to VNC-based support with VOIP guidance, maybe we'll go 100% GUI in instructions.

Finally, you'd be hard-pressed to find a forum member who has uploaded as many screenshots or created as many graphical tutorials as I have.

---

### Post by briancurtin on 2006-07-04
[QUOTE=egon spengler]I find it hard to believe that an Arch user is complaining about a lack of GUI tools in ubuntu. Using Arch must be a constant torment for the poor guy[/QUOTE]
i love arch because you have to use the CLI, unless someone else installs it for you and does everything while you are away from your desk.

---

### Post by atoponce on 2006-07-05
I am going to weigh in my $.02 here.

I know I don't speak for everyone, and I certainly am not trying to impose some sort of philosophy by any means.  However, I firmly believe that the terminal is far superior to many aspects that the GUI can bring to the table.  Aside from flags, options, aliases, scripts, and about a million other things that make the terminal great, the number 1 reason it is superior is sheer speed.

What does this mean?  First, it means that I can do just about anything I please with the terminal and my keyboard, and I can do it twice as fast as anyone with a mouse.  Web browsing, mp3 playback, email, document creation and even photo manipulation.  Second, nothing is more annoying to me than using the keyboard and then picking up the mouse just for a couple focused clicks then going back to the keyboard.  For example, spreadsheets.

Again, though, I am not trying to impose solely using the terminal.  They both have their place.  It's just that nothing beats keyboard shortcuts and the terminal for both the 1337 and the n00b.

---

### Post by Dr. Nick on 2006-07-05
I may have mentioned this before, but I feel it bears repeating. I use the gui for alot of day to day activites, but for helping users configure their hardware I feel that the command line is king. In a bad situation  a new linux install may not have a GUI, If xorg doesnt get configured properly for some reason then GUI instructions are useless. Even if a new install gets a full GUI, If all a user knows is gui then they are in a tough spot should something cause X to fail.

I have started a little page that I hope will help those willing to learn. I have used the "bad" expierences I have had from other distros forums (not here) as a guide to make my advice better.
When I first got into linux I mindlessly copied/pasted. I made this page to explain to those willing to learn what the commands I recommend are used for,

[http://www.geocities.com/aebcoat/commoncommands.html](http://www.geocities.com/aebcoat/commoncommands.html)

That link should remain in my signature for a long time to come, and as time progresses I hope to make it even more helpful.

---

### Post by kabus on 2006-07-05
[QUOTE=H.E. Pennypacker]because as long as people like me are around, Linux will become easier to use day by day.[/QUOTE]

By magic, I assume.

---

### Post by angkor on 2006-07-05
[QUOTE=H.E. Pennypacker]The number of aysius (the poster who publicly shares his love for the terminal) will start dwindling as more people like me start using Ubuntu, because as long as people like me are around, Linux will become easier to use day by day.[/QUOTE]

Put your money where your mouth is H.E. Pennypacker. 

If you knew what you were talking about, you'd know that Aysiu single-handedly has made Ubuntu easier for *a lot of* new users both on this forum and on his website. What have you done so far to achieve that?

If the number of Aysiu's will dwindle (sadly there is only one) ubuntu will be more difficult for many new users. Can the same be said if the number of pennypackers will dwindle?

I'll value your opinion more when *you* come up with a website like [this]("http://www.psychocats.net/ubuntu/index.php"), and every howto had a  gui counterpart of course.

---

### Post by adam.tropics on 2006-07-05
I think quite apart from the previously mentioned benefits of the terminal for experienced users, new users in Ubuntu or any other distro, benefit from picking up on some of the basic 'workings' of Linux. Even if they are copy and pasting, over a short time, basic things for example the file system become far clearer. They figure out more of the 'why' things are done in a certain way and this knowlege will serve them well later, and enable them in turn to help the next guy more effectively.

Don't get me wrong, I want things to be straightforward for new users, and I think some of the gui based applications are excellent, but I also think people need to remember we are not trying to be, copy, or 'beat' other OS's. We are just another choice. A good one, but a choice, and like all worthwhile choices in life, Linux needs to be approached with an open mind, and recognition that the differences are going to mean at least a slight learning curve.

---

### Post by Dr. Nick on 2006-07-05
One thing about command line which I havent seen mentioned is this.

Most of the command line is universal, no matter what desktop enviroment, we know this, **But more importantly is its nearly universal betweeen distributions**.

I started out linux back in mandrake 8, I also have used

Mandrake/Mandriva 9, 9.1, 9.2, 10 .....
Suse 9, 10
Redhat8/ Many of the fedora cores
Debian Woody/Sid
Ubuntu warty, hoary, breezy, dapper
And a few others

What I am trying to say here is that when I needed   to configure something in suse, I didnt have to look for the option in a gui since I knew how to do it with a command line, just like I learned in mandrake.

Their used to be alot more differences in the GUI tools of various distributions so knowledge of command line for simple task was a real timesaver. This isnt as much a case today, but still is on occasion. If you learn how to do everything with a  GUI on ubuntu, and have no basic command line knowledge then you may be lost for a few minutes if you go to a machine running fedora, or if you choose to install fedore yourself for fun.

---

### Post by Iandefor on 2006-07-05
[quote=zolookas]Of course you can't do everything using gui. Knowing command line is very useful, but do you expect people to learn command line by pasting things? Maybe, if they are very curious.[/quote][quote=aysiu]I did.
Seriously, that's how I learned the command-line, by copying and pasting commands. How else do you learn them?[/quote] The both of you are right to some extent, imho. For example- I learned how to use the CLI (and still am learning) by copying and pasting commands... and then reading the man page for that command, and working out what the arguments mean. I can also infer things from the command itself (IE, I see an option called --br 192 and I'm asking how to encode ogg vorbis audio at 192 kb/s, I can reasonably assume that --br is the argument that sets bitrate). But it was because I was actively interested in learning how to use it proficiently that I even bothered to read the documentation. If I didn't care, I could have just stuck with copying and pasting commands without needing to understand their meaning.

I learned by doing... and having interest in learning (But it doesn't take much).

---

### Post by egon spengler on 2006-07-05
[QUOTE=H.E. Pennypacker]OP, thank you for your courage.  The number of aysius (the poster who publicly shares his love for the terminal) will start dwindling as more people like me start using Ubuntu, because as long as people like me are around, Linux will become easier to use day by day.[/QUOTE]

Well that is a very grand statement, what exactly is it that you are contributing? Really I feel this whole thread is waste. People on this forum volunteer their time and help. If someone doesn't want to accept that help because they don't like/understand the format it is offered in then they have the right to decline that assistance and look elsewhere, either in terms of avenue of support or choice of computing platform. Personally I seldom post help because I honestly don't care that much. It does strike me as a bit rich though when peole with probably less than 100 posts between them feel to admonish people who have spent 100s of hours on here volunteering their time because they "aren't offering help correctly"

Maybe you should actually contribute something yourself first and lead by example before you start telling other people their efforts are wrong

Btw, why it is that you phrase your whole post as if you were part of some counter movement to overthrow a government? 

"Thanks to the bravery of these courageous whistleblowers we will be able to continute the struggle to one day free ourselves from the oppressive reigns of one aysiu. Forward comrades"

---

### Post by aysiu on 2006-07-05
There are those who whine and those who act.

I have nothing but respect for the author of this tutorial:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

On the other hand, I have very little respect for those who complain about volunteer efforts or demand things they themselves rarely (if ever) contribute.

Maybe the number of aysius will dwindle (currently only one at last count--maybe "we" will dwindle to .5 or 0). I don't see how that will help Linux become easier, but maybe H.E. Pennypacker is in the middle of creating an elaborate screenshot tutorial... after all those do take a lot of time to put together.

---

### Post by aysiu on 2006-07-05
*wget* I've found just about always to be faster if you know the exact web address you're looking for.

It's a bit like being in a taxi--"Take me to the corner of Memorial Drive and JFK!" instead of just aimlessly wandering around until you find the bridge you're looking for...

---

### Post by Metacarpal on 2006-08-04
Hi aysiu,

I was contemplating posting in the Cafe asking why, in the "Absolute Beginner Talk" forum, people constantly reference command-line code to folks who are making their first step into Linux.  Whenever I see someone give command-line code for a task that can be done through Ubuntu's GUIs, I always stared in shock.  I figure people who migrate from Windows aren't usually ready for all that right off the bat.

But, as I prefer to do (and really, really wish more people did!), before posting I ran a search, and I found a this thread.  (What? A helpful and informative thread by aysiu? What a shock! ;))  And I gave it a read-through.  Okay, so I skipped about three pages of replies, but I got the gist of it.

And while I do still think that if one can give short'n'sweet directions to GUIfy a process, I like to do that so as not to scare away the timid newbies, your post did show a lot of merit for early teaching of command-line that I hadn't previously considered.

Your strongest argument in my view?  You can't copy'n'paste GUI.  I read that and just thought, duh - why didn't I think of that?  (The bit about aptitude being mercifully quicker than Synaptic when you know the file name is good, too.  :) )

So, yeah.  Thanks for helping me see the point of the other side of the issue.  Also, thanks for saving me from starting a flame war of my own. :D  But I'll still provide GUI instructions as best I can for those who panic at command-line code.

Now if we can just get the responders to stop assuming people know that the code goes in Terminal, what that is, and where to find it...

---

### Post by aysiu on 2006-08-04
I still give GUI instructions from time to time, depending on the situation. I've uploaded a *lot* of screenshots to this forum!

---

### Post by eternalsword on 2006-08-17
I'm pretty noob myself only been using Ubuntu for a month, but after doing some edgy upgrades - needed some libs for gaim2 and some other non-default programs - nautilus, more specifically bonobo begins consuming high cpu.  So I've resorted to using the terminal.  I must tell you, I'm beginning to love it.  It's faster to navigate to directories if you know the whole path.  I have several folders I frequent.  In nautilus, I would open it, then I would have to click on the correct tree entry and then subsequently find and double click the correct folders.  In the terminal with zsh and correct settings, I can do cd /m tab /s tab x1 for sda1 x2 for sda3 and x3 for sdb1 and then /down tab to get to my download folders in each of my partitions.  It's so much faster.  And then I've been learning about grep and find.  They are invaluable, learn them.  Try in nautilus to find that one zip file in in a folder with hundreds of files and you've forgotten the name but you know its there.  in the terminal ls | grep .zip and bam you've found it.  or even better if you forgot where you put a file and you know it's name, you can do find / -name "file.ext"  and it will list all entries in everything mounted, might take some time, but it's a helluva lot faster than manually searching in nautilus.

and as far as scripting goes, I love it.  I've already written a script to change wallpapers and loaded it as a cron job to do it every hour  and I've written scripts to allow zsh to autocomplete for example if I type aviplay it will tab autocomplete all .avi files.  aviplay is just a simple script calling gmplayer.  and I have one for mkv and ogm that adds subtitle and audio parameters gmplayer -alang jpn -sid 0  which saves me from using the gui to change it, which doesn't always work anyways.

sorry it's so long, I'm just excited about learning Ubuntu and all the underlying features, including scripting and using the terminal more efficiently.

---

### Post by zugu on 2006-08-17
I agree with aysiu. People should have the choice: GUI or command-line.
The problem is, many GUIs are either unusable, plain ugly, in alpha stage or non-existent. The command-line will always be there, while the GUIs can be more than one for the same application, are scattered around the net, each one providing "its way" of doing things (not necessarily a bad thing - it's just that a newb might get lost).

Now I don't say the command-line is obsolete. It's not. it's also a powerful means of achieving things IF you have the knowledge. You achieve this knowledge by reading the man page, the readme, a wiki on the web or whatever. However, I prefer a good GUI - I might not need to read the manual, because there's a great chance of me finding out how to achieve my task by just looking at the screen. If the GUI is a good GUI, I'll eventually find out what I need to click in a matter of seconds.

Someone else complained about being harder to navigate to a directory in a GUI. We all know the human mind is much more prone to respond easier to visual stimuli (I hope this is the plural form) than to command-lines. In the command line, I have to create a visual map of the directory structure, find my current position in that structure, find the directory where I want to go, eventually I need to find out the relative path to where I want to go (sometimes it might be easier to use the absolute path), write it down - all this in order to change the current directory.
In a GUI file manager I already have a visual path to where in the dir structure I am. Going to the parent dir it's just a click away, instead of typing "cd ..". So it's less time spent thinking for me, more time for me to be productive. Or for leisure.

If it's harder for you to use a GUI to navigate a file hierarchy, it's not that the command-line way it's easier, it means the GUI is improperly designed.

Back to where I began my rant, I wish to point out that the developers usually do not give a shit about the visual interfaces. They don't care, it's their product and they might feel more comfortable in it. Or they could use the plain old saying: "We're programmers, not GUI designers!" - very true in many cases.

As much as a Microsoft hater that I am, I have to see that they raised the standard with Windows 95, the first operating system to have a usable GUI. They had the insight to see that GUIs are the gateway to mainstream (please, don't say things like "Linux is not trying to get into mainstream" or such, it's pretty obvious it's trying to get there).

We could argue that the command-line is archaic. What does "archaic" mean? AFAIK, it's something that appeared/was created/used to exist in the past. We still have it today, and we can say that it's archaic, because it dates since ... I don't know, the day UNIX was created? Someone tried not to associate the word "archaic" with the command-line, as if this would diminish it's value, or contribute in a way to newbies aversion to it. Well, believe me, there's nothing wrong with a piece of software being archaic, as long as we use it today with good results. And yes, it's a turn off for newbs.

And the final point of my rant: I am tired of running things from the command-line, only to see why app XYZ crashed. Or why it's not starting anymore (this is because GNOME really is made for idiots - it's verbosity level is close to zero). I am tired of people saying that it's easier to navigate within lynx than in Firefox. I am tired of people bashing Linux distros that make things simpler for people. If you like the command-line, fine. But don't deny others' right to use GUI exclusively (although quite impossible these days). And yes, GNOME is a good desktop enviroment, except it needs some major revisions.

End rant.

---

### Post by aysiu on 2006-08-17
Just for the record, eternalsword said *faster*, not *easier* (regarding terminal navigation v. Nautilus).

---

### Post by eternalsword on 2006-08-17
> **aysiu said:**
> Just for the record, eternalsword said *faster*, not *easier* (regarding terminal navigation v. Nautilus).

Yep, easier and faster don't always go hand in hand.  For some things I choose easier over faster like running an Xserver for example, it's not that it's impossible to do the things I do without it and I could definitely compile/do cpu intensive tasks faster, but I like my Gnome :)  And as I noted earlier, I like the terminal for it being faster.

---

### Post by slimdog360 on 2006-08-17
I recon the command line is user friendly if you know how to use it. When i first started out, my god I didnt know what was going on. sudo this, apt-get that, it was quite confusing. 
It started to get easier with time though I really had to force myself to use it.

---

### Post by egon spengler on 2006-08-17
> **zugu said:**
> Someone else complained about being harder to navigate to a directory in a GUI. We all know the human mind is much more prone to respond easier to visual stimuli (I hope this is the plural form) than to command-lines. In the command line, I have to create a visual map of the directory structure, find my current position in that structure, find the directory where I want to go, eventually I need to find out the relative path to where I want to go (sometimes it might be easier to use the absolute path), write it down - all this in order to change the current directory.
In a GUI file manager I already have a visual path to where in the dir structure I am. Going to the parent dir it's just a click away, instead of typing "cd ..". So it's less time spent thinking for me, more time for me to be productive. Or for leisure.

If it's harder for you to use a GUI to navigate a file hierarchy, it's not that the command-line way it's easier, it means the GUI is improperly designed.

No.

---

### Post by ubuntu_demon on 2006-08-17
aysiu : great article!

"sudo apt-get programname"
Should be (without typing the $) :
```

$sudo apt-get install *programname*
$sudo aptitude install *programname*

```

---

### Post by aysiu on 2006-08-17
Thanks for the note. I've updated the first post accordingly.

---

### Post by ubuntu_demon on 2006-08-17
> **aysiu said:**
> Thanks for the note. I've updated the first post accordingly.
no problem :)

I have blogged about this thread (which is also on the planet now) :
[http://ubuntudemon.wordpress.com/2006/08/17/why-i-think-the-command-line-is-user-friendly/](http://ubuntudemon.wordpress.com/2006/08/17/why-i-think-the-command-line-is-user-friendly/)

---

### Post by CameronCalver on 2006-09-04
Ok this is my say in the [SIZE="3"]&#8734;[/SIZE] argument 
firsly when i new nothing about ubuntu or linux and i didnt even no what all these commnands people are giving me i was a bit confused but after about 2 minutes i figured it out and i thought it was great i did not no my way around ubuntu at all but i still could do lots of things with those little commands people were giving me so i think cli is good for an extent but i think the new people to ubuntu should ask 
how do i get into this graphicly if they want so they know how to get into them and that makes it there choice to get around

---

### Post by 3rdalbum on 2006-09-04
I once tried to give graphical instructions for some task in Ubuntu... and I ended off actually causing a problem :-)

Sometimes the CLI is quicker, especially if you run Fish and have autocompletion at your fingertips. Sometimes it's easier to remember exactly how it's done in the CLI versus the GUI ("Was that button labelled "Advanced" or "Properties"?"). Sometimes, specific things can only be done in the terminal - scheduling jobs with at or batch is the first example that comes to mind, but there are definately loads of others that even I use.

If I'm compiling a program, and it complains about dependancies, rather than fire up Synaptic and wait for it to build a dependency tree, then do a search for the exact name of the thing I need, I just go to Fish and type "sudo apt-get install libfoo", press Tab twice, and I'll be told about libfoobar, libfoobar0, libfoobar-dev, etc. Much, much, MUCH quicker.

---

### Post by qpieus on 2006-09-04
> **poofyhairguy said:**
> 
1. Is pointing newbies to the command line a bad thing?
2. If they are afraid of it should I be honest and tell them "the only Linux I know of that liberates itself from the command line is SUSE?"
3. Should we make more guides to do things in a graphical way?
4. Will Ubuntu ever reach the lofty goal of "never needing the command line?"
1. No, that's what makes learning to use linux fun. I'm a new user (about 4 months) and using the command line to do stuff seemed strange at first, but it didn't take me long to realize that you can do some things faster and easier that way. Newbies need to do a little learning.
2. I don't have a problem with telling people that. If someone is so deathly afraid of the CL, then they need a distro that uses the CL less or not at all.
3. That's probably a good idea, in order to bring in more new users. But I know that'll take lots of additional time to create such guides.
4. No, but I wouldn't want it to. The CL is what makes linux different and interesting for me. If you want gui only, go with suse or linspire or something like that.

---

### Post by argie on 2006-09-04
I think the * makes the CLI all powerful. Can you imagine having to rename a set of files to a different extension through the GUI? (don't ask why)

Btw, CameronCalver
> "Error Keyboard Failure Press F1 to continue or DEL to enter setup
I got just this error the other day when shifting house, the keyboard wasn't plugged in and I got "Keyboard not detected Press F1 to continue DEL to enter BIOS setup".

---

### Post by aysiu on 2006-09-04
> **argie said:**
> I think the * makes the CLI all powerful. Can you imagine having to rename a set of files to a different extension through the GUI? (don't ask why) Sure--I just use KRename.

---

### Post by prizrak on 2006-09-04
> 4. No, but I wouldn't want it to. The CL is what makes linux different and interesting for me. If you want gui only, go with suse or linspire or something like that.
Actually it's already at a point where you don't NEED to use the CLI. On my old laptop Dapper worked out of the box. I only had to add the Automatix repo to it to make all the extra stuff work. However that can also be done graphically (that's the way I did it).

---

### Post by jISh on 2006-09-04
I always tell new people instructions using the command line. It's so much more efficient and customizable. 

Anybody who wants to get the most out of their system should embrace the command line.

---

### Post by taurus on 2006-09-04
It's always going to be a command line for me because you can do soooooooooo much more with it.  Who needs all the happy finger clicking thing!  :twisted:

---

### Post by Note360 on 2006-09-04
I their any way to get fish syntax highlighting in zsh or a right prompt in fish?

---

### Post by aysiu on 2006-12-03
I read this a lot, and I think it's common misperception, but I want to know what the real deal is.

Oftentimes people say, "Oh, you need to use the terminal for too many things. There aren't enough GUI frontends." Well, I'll be the first to admit that Ubuntu could certainly use a graphical way to reinstall Grub or a 100% reliable way to mount partitions with the correct permissions using the GUI and not editing the /etc/fstab file (by the way, Mepis does both of these things and has for years, so it's not a *Linux* problem--it's a *Ubuntu* one).

Seriously, though, how many things can really be done **only** in the terminal? I'm not talking about people *preferring* the terminal. After all, I think terminal commands are the most efficient and productive ways to help new users over a text-based online forum. I'm talking about tasks that can **only** be done in the terminal--there is no GUI option.

Can people help me compile a list of these?

Here's a start:

-- Restore Grub to the MBR
-- Reliably mount new partitions with the correct permissions
-- Fix a broken X server

Any others?

**Edit**: Additions to the list...

-- configuring/setting up postfix and DNS
-- Apache configuration
-- Universal internet connection proxy configuration for all kinds of applications including but not restricted to web browsers, apt, wget etc.
-- switching Usplashes
-- configuring xen
-- setting up ADSL
-- Configuring screen resolution (in many cases)
-- Dual screen setup

---

### Post by dbbolton on 2006-12-03
transcode ?

[http://www.ubuntuforums.org/showthread.php?t=307065](http://www.ubuntuforums.org/showthread.php?t=307065)

---

### Post by Ramses de Norre on 2006-12-03
How would you fix a broken X server with a GUI?:-k 

And personally I don't think there should be GUIs for everything.. Most people never need to reinstall grub and if you make a GUI for every small task ubuntu would become a little overloaded I think.

But other stuff like fstab editing could certainly require a GUI for a lot of people...

---

### Post by po0f on 2006-12-03
For new users, having to go to the command line may be a little scary and seem a little archaic at first, but hopefully they will get used to it as it is a very efficient way of getting stuff done.

That said, I think Ubuntu has the right mix of GUI-to-command line: the user isn't required to use it *all* the time, but it is a necessity in certain situations.  They will be better off for it.  And as you said, there are other distributions if they think even this is too much.  :)

> **aysiu]Restore Grub to the MBR[/quote]
I believe there is a program that does this along with other basic GRUB editing, but I don't recall if it is in the repos or not.
[quote=aysiu]Reliably mount new partitions with the correct permissions[/quote]
Does Gedit count as a GUI?   said:**
> Fix a broken X server
This is the only situation where you *have* to go to the command line, because the "GUI" isn't working at all.  Then again, you could boot a live CD and fix it after correctly mounting your partitions.

---

### Post by Polygon on 2006-12-03
techinally you could boot up into "failsafe" mode which uses a known working xorg.conf in case you bork yours up, but actually reparing the broken one on the other hand

these things could easily be done by someone who knows about these things and can just make a gui frontend for it. From what ive heard, making the GUI is the easiest part.

but the grub one is a must. the first time i tried to restore grub i ended up screwing something up and ubuntu wouldent boot, cause of that awful tutorial of going through the install cd and mounting the partitions and then skipping ahead a few steps and... ugg

but the grub-install command is much easier.

---

### Post by The Noble on 2006-12-03
I wouldn't count *Fixing* X server as one of those options, as when x breaks you won't have a gui in the first place. I'm assume you mean modifying X instead. I haven't used Suse or Fedora successfuly yet, but I have heard that they have a nice set of GUI tools to modify X; is it possible to port them over to Ubuntu?

---

### Post by atoponce on 2006-12-03
aysiu-

You've hit the nail on the head, as usual.  There needs to be some graphical frontends for a good deal of configuring certain aspects with Ubuntu and Linux.

However, I don't mean to confuse preference with need, but I personally think that avoiding the terminal on a GNU/Linux distro does more harm than good.  So, maybe there's a reason there aren't GUI frontends to these means.

---

### Post by IYY on 2006-12-03
I believe that many distributions don't offer command line solutions in some places where such solutions are needed, but I do agree that there are some places where a GUI could be helpful. Configuring X is such a case. Mounting Windows and other Linux partitions is another.

---

### Post by aysiu on 2006-12-03
No, I don't consider using Gedit to edit a text configuration file a graphical configuration tool, although it technically is.

Editing with *nano* is not that different from editing with Gedit. I'm talking about strictly point-and-click.

I agree with you, atoponce, that avoiding the terminal is bad. I'm just trying to determine exactly how **dependent** we are on the terminal as opposed to how much we choose to use it.

I even wrote an ode to the terminal in this thread: [Why I think the command-line is user-friendly...](http://ubuntuforums.org/showthread.php?t=59334&highlight=why+terminal+user-friendly)

So, so far nothing has been added to the original list? Configure broken X, restore Grub to the MBR (if you do find a totally point-and-click Ubuntu solution, please let me know and link to it), and (in certain cases) mounting partitions.

---

### Post by TLE on 2006-12-03
Well it sort in the same ballpark.
- Configure and test X
[Edit]
I believe that about 80% of the times you end up with a broken X it is because you are trying meddle your way through some sort of configuration. Therefore I regard it is as an absolute necessity to have a GUI way to configure AND test an X configuration. I myself love this big toy that is Linux, and every time I install a new distribution is a little party, except from when I want to setup my X the way I want it, that always gets me and I end up passed up under the table, metaphorically speaking ;)

---

### Post by atoponce on 2006-12-03
Add configuring/setting up postfix and DNS to the list.

---

### Post by aysiu on 2006-12-03
> **atoponce said:**
> Add configuring/setting up postfix and DNS to the list.
Will do.

---

### Post by jbtito03 on 2006-12-03
Hi guys..

As from my point of view... okey... gui-s are nice and all but... things like GRUB, FSTAB, etc. should stay in terminal only.

Why?

Cause people who use this stuff know how to handle it in the terminal and if someone wants to mess it up has to go to the forum or wiki or whatever and take a look at what GRUB is, what FSTAB is, etc. and then learn how to modify it. 

For the end end end user (office scretary) it is not neccesary as she will call the sys admin to fix thing (does not matter which system). 

For all others - if you know how to use your GNU/Linux from the terminal it is good for you and you may teach others how to do stuff. Educate your self people cause you are in control of the maschine and dont let the maschine be in control of you :D

GUIs are many times just supporting our lasyness - i am not saying that they are not very practicall for some things like whatching movies, listening to audio, editing text, etc. 

But stuff like sys administration should be left to experts who know what they are doing and not wannabe GUI admins - at the end, linux is not WINDOZE. Please accept that :D


Cheers...

JB

---

### Post by aysiu on 2006-12-03
Please understand, JB--I'm not advocating removing the terminal or saying people should always prefer the GUI. I'm just trying to compile a list of tasks that **require** you to use the terminal, whether you like it or not.

---

### Post by jbtito03 on 2006-12-03
heheh...

No, i really understand your point. And sure, if there are guis people will eventually use them. But all i am sayig is, that these GUIS may do more damage (especially from the educational point of view and the "system going into garbage" view) then good. And ok, if there will be guis, they should not be preinstalled but seperated and instalable thru apt for admins if they want to. 

This is just my point of view as i am working a lot with youg people in my local youth center (ok, i am young also:)) and i know that they get easily lasy if you give them the chance to get lasy in their head :D That is of course not good for their developement cause they do not know how things work or why they do so and because of that they do not evolve as they could. What i am saying is that for example windoze is making their users "stupid" and that is mostly thru GUIs and closed source.

At the end, when i started with internet 10 years ago and discowered linux i wanted everything done at the moment whithout asking why and how. I buzzed my friend to make it for me and at one point he sead "I know how to make it and i know why it works. I figured out fo myself and the best thing for you is that you figure it out the same way as i did.". At that time i called him egocentric, moron or whatever but now looking back i can just say THANK YOU! If it wasnt for him, i would just click and click and would never know as much as i know (and it is not a ot but it is a good foundation for further understanding and learning).


So these are my concerns and i am repeating - this is only my point of view :D

Cheers

JB

---

### Post by jamyskis on 2006-12-03
> **jbtito03 said:**
> heheh...

No, i really understand your point. And sure, if there are guis people will eventually use them. But all i am sayig is, that these GUIS may do more damage (especially from the educational point of view and the "system going into garbage" view) then good. And ok, if there will be guis, they should not be preinstalled but seperated and instalable thru apt for admins if they want to. 

This is just my point of view as i am working a lot with youg people in my local youth center (ok, i am young also:)) and i know that they get easily lasy if you give them the chance to get lasy in their head :D That is of course not good for their developement cause they do not know how things work or why they do so and because of that they do not evolve as they could. What i am saying is that for example windoze is making their users "stupid" and that is mostly thru GUIs and closed source.

At the end, when i started with internet 10 years ago and discowered linux i wanted everything done at the moment whithout asking why and how. I buzzed my friend to make it for me and at one point he sead "I know how to make it and i know why it works. I figured out fo myself and the best thing for you is that you figure it out the same way as i did.". At that time i called him egocentric, moron or whatever but now looking back i can just say THANK YOU! If it wasnt for him, i would just click and click and would never know as much as i know (and it is not a ot but it is a good foundation for further understanding and learning).


So these are my concerns and i am repeating - this is only my point of view :D

Cheers

JB

I understand this point of view, but it seems to be more the Slackware way of thinking - to be perfectly blunt, it's taking the attitude that if you're not prepared to learn to use the command line, don't bother with Linux. The goal of Ubuntu is "Linux for human beings" and most human beings want a desktop That Just Works (TM). I would think it great if everyone knew how to configure an X server using nano (or in my case vim) but some people just don't have the time to learn, some just aren't technically inclined. Remember - Ubuntu is for everyone, not just techheads and not those who want to become techheads. It's all about choice - if you want to modify your config files by hand, that's fine by the rest of us.

A propos the X server configuration - there needs to be a GUI to configure it - perhaps to enable GLX extensions and select the driver used manually, for instance. Of course, there needs to be a fallback ncurses GUI just in case you're reliant on the GUI to configure X.

Also - and this has been screaming out for a proper GTK2 GUI for ages - DSL configuration. I know now that sudo pppoeconf is used for configuring broadband connections (otherwise I wouldn't be writing this :mrgreen:), but it took me hours to find this out when I first moved to Ubuntu. Given that 80%-90% of users are probably on some kind of DSL, and many won't have this patience, I think DSL needs to be more easily configurable.

---

### Post by TLE on 2006-12-03
> **jbtito03 said:**
> 
So these are my concerns and i am repeating - this is only my point of view :D
...

I respect your point of view but I don't share it.

Not everyone is interested in learning a lot about the inner workings of their computer and their OS, but are still forced to administrate their own private computer because they don't have a personal friend/Linux guru to set it up for them.
Then is Linux not for them ???

What I said in my last post about X configurations might even apply more generally, I believe that definitely more then half of the "broken system" posts in this forum are due to self inflicted configuration issues, and so for that part I believe that with the right kind of GUI's, we might actually have fewer broken systems on out hands. Obviously the Windows ones are the other extreme, and I do agree, that they don't teach the users anything, but I do think it is possibly to make ones that are better at that.

Furthermore, I think that GUI's have a significant quality that is hard to ignore. They make information and options available and visible. Meaning that in a GUI you can make options available to the user, without asking him to dig through large quantities of documentation (of varying quality) while still informing him what it does.

Regards TLE
[EDIT] jamyskis LOL two persones one thought

---

### Post by Old Pink on 2006-12-03
I love the terminal, I do most things in it. :) 

"Linux for Human Beings" remember? Not "Linux for Idiots" - most people can use a terminal should they do a quick google search. Seriously, stop dumbing things down further than needed.

---

### Post by AndyCooll on 2006-12-03
A GUI for compiling stuff from source.

Many may consider compiling apps from source to be for the more advanced. However I've seen plenty of threads on these boards posted by newbies who've found an app they want on Sourceforge or somewhere similar and are struggling to install it because it needs compiling.

:cool:

---

### Post by jbtito03 on 2006-12-03
Okey okey...

It may be that i really am one that thinks in the sense of "slackware" but actually really enjoy GUI. The most fun i had was with the installation of Gentoo and the installation of freeBSD from two floppys and then over the net :D But that is really me... cause i like it - it makes me happy when i manage to make the sys working even with the hardest scenario - and i like to compile thing - not to programm... cause i dunno how, never learned it. But i never close any options and if there is no GUI i just make it the terminal way. I am not happy until it works :D So that is why i think the way i think. I know that this is good for me cause i live only one life (as far as i know) and the more i know the more i am :P 

About the line that people who dont know how to use linux in terminal should not use it at all - never sead that, just sead that they should call sys admin or look it up on the net. There is mostly a solution for every problem, that needs only a small amount of time. But thru that process u get knowlege and at the end you are proud of yourself cause "YOU DID IT!(TM)" :D 


So........ about missing guis - hmm.. none i miss.. :D maybe for 3d acceleration? 

Have fun people... ;) 

JB

---

### Post by jamyskis on 2006-12-03
> **AndyCooll said:**
> A GUI for compiling stuff from source.

Many may consider compiling apps from source to be for the more advanced. However I've seen plenty of threads on these boards posted by newbies who've found an app they want on Sourceforge or somewhere similar and are struggling to install it because it needs compiling.

:cool:

I've been playing with this idea for a while now. Since most compilations are simply a case of ./configure - make - make install, there's no reason why a GUI couldn't do this job nicely. Advanced features of the GUI could also cater for the various parameters that can be passed to the configure scripts and makefiles too.

---

### Post by PrinceArithon on 2006-12-03
My belief is that the Terminal makes you the Lord of your whole computer.  Too many times things fail in GUI, at least in the terminal you know you control the world.  When Windows outed DOS from it's system Windows lost a lot of power.  At least in my opinion.

---

### Post by atoponce on 2006-12-03
You know, adding Apache configuration needs to be added to that list.  Adding new websites and modules, unless you know what you are doing, is a pain in the rear.  Especially, if dealing with sub-domains.  MySQL has a gui frontend, PHP doesn't really need one, but Apache to finish off the LAMP stack is needed.

---

### Post by PriceChild on 2006-12-03
btw there's a high priority spec for feisty called "Bulletproof X".

Basically If your xorg.conf is wrong, it should default to basic drivers to give you some sort of X. This could allow you to use a xorg.conf gui tool.

---

### Post by aysiu on 2006-12-03
> **PriceChild said:**
> btw there's a high priority spec for feisty called "Bulletproof X".

Basically If your xorg.conf is wrong, it should default to basic drivers to give you some sort of X. This could allow you to use a xorg.conf gui tool.
That sounds great, PriceChild. I'm looking forward to seeing that.

---

### Post by PriceChild on 2006-12-03
[https://blueprints.launchpad.net/distros/ubuntu/+spec/bullet-proof-x](https://blueprints.launchpad.net/distros/ubuntu/+spec/bullet-proof-x)

There we go :)

---

### Post by PriceChild on 2006-12-03
Oh and you guys may like to see this:

[https://blueprints.launchpad.net/distros/ubuntu/+spec/xorg-config-ui](https://blueprints.launchpad.net/distros/ubuntu/+spec/xorg-config-ui)

Its been deferred from feisty though... maybe 7.10 hey?

---

### Post by smoker on 2006-12-03
hi,

i dont see the problem with having a gui for everything possible. i use the terminal cause i have to, but i would rather be surfing the net or learning something more appealing to me, than spending my time scouring forums and reading man pages to find this and that command for whatever!

fair enough, use the terminal all you want, if you want, but given the choice, i'll take the point and click route.

---

### Post by atoponce on 2006-12-03
I just can't imagine separating the terminal from the operating system.  Linux and Unix both are just too ingrained with it.  I hope they don't separate.

---

### Post by 23meg on 2006-12-03
> **PriceChild said:**
> Oh and you guys may like to see this:

[https://blueprints.launchpad.net/distros/ubuntu/+spec/xorg-config-ui](https://blueprints.launchpad.net/distros/ubuntu/+spec/xorg-config-ui)

Its been deferred from feisty though... maybe 7.10 hey?
Feisty + 1 will be using Xorg 7.3, which will detect X configuration via HAL and probably won't even require an xorg.conf, so making such a tool as a frontend for xorg.conf right now isn't really needed, especially given the existence of the bulletproof X spec.

---

### Post by nalmeth on 2006-12-03
I agree with the posted GUI-less tasks, except if someone really needed a GUI to compile from source, there is kconfigure:
[http://kconfigure.sourceforge.net/](http://kconfigure.sourceforge.net/)

/etc/fstab is the biggest one I think.

---

### Post by Peepsalot on 2006-12-03
Is there any GUI interface for the Linux man pages?

---

### Post by aysiu on 2006-12-03
> **Peepsalot said:**
> Is there any GUI interface for the Linux man pages?
Yeah. It's called a web browser.

Do a google search for ```
man apt-get
``` for example.

---

### Post by aysiu on 2006-12-03
> **nalmeth said:**
> I agree with the posted GUI-less tasks, except if someone really needed a GUI to compile from source, there is kconfigure:
[http://kconfigure.sourceforge.net/](http://kconfigure.sourceforge.net/)

/etc/fstab is the biggest one I think.
Oh, I'll take it off the list, then, I guess.

---

### Post by Peepsalot on 2006-12-03
> **aysiu said:**
> Yeah. It's called a web browser.

Do a google search for ```
man apt-get
``` for example.
Unacceptable.  What if I need to read the manual to learn how to fix my broken internet connection.

---

### Post by aysiu on 2006-12-03
> **Peepsalot said:**
> Unacceptable.  What if I need to read the manual to learn how to fix my broken internet connection.
Well, considering the *man* page is to help you use the terminal, you'd end up having to use the terminal anyway, wouldn't you? Nevertheless, I'll add it to the list.

---

### Post by 23meg on 2006-12-03
> **Peepsalot said:**
> Is there any GUI interface for the Linux man pages?System / Help / System Documentation / Manual Pages.

---

### Post by Peepsalot on 2006-12-03
> **23meg said:**
> System / Help / System Documentation / Manual Pages.
Hey cool!

> **aysiu said:**
> Well, considering the *man* page is to help you use the terminal, you'd end up having to use the terminal anyway, wouldn't you?
Well, yes, but it's nicer to read the manual with GUI fonts. ;)
Edit: Oh, and it's all categorized and everything.  I like this.

Anyone know how I could make a link directly to a particular help page from my desktop?

---

### Post by cleverselfreferentialname on 2006-12-03
Before I came to Linux, my thought was "Well, there are GUIs for everything anyway, right? I don't really _need_ to use the command line."

But I did. Initially, I tried using it for as few tasks as possible.

I am very glad now that Ubuntu made me use the command line a little, because, otherwise, I never would have learned about the filesystem structure. I would be totally GUI-dependent. And I certainly wouldn't be getting interested in software development now. So, I'd say, no. Ubuntu isn't too dependent on the terminal.

Although I really would like an apache configuration GUI. :)

---

### Post by 23meg on 2006-12-03
> **Peepsalot said:**
> 

Well, yes, but it's nicer to read the manual with GUI fonts. ;)
Then you'll like the fact that you can type in the Yelp search box exactly what you'd type to reach a command man page: *"man app-name"*.

---

### Post by fuscia on 2006-12-03
i don't remember the last time i had to actually use the terminal, other than installing something when i was too lazy to open synaptic.

---

### Post by arnieboy on 2006-12-03
Universal internet connection proxy configuration for all kinds of applications including but not restricted to web browsers, apt, wget etc.
A lot of effort has gone into writing documentation for the same and most of it is far from perfect.

---

### Post by Peepsalot on 2006-12-03
> **Peepsalot said:**
> Anyone know how I could make a link directly to a particular help page from my desktop?

Well I just figured it out, so I'm going to answer my own question in case anyone is interested.  When you find the help page you want to make a shortcut to, you can right click and "Copy link location".  Then just make a launcher that calls yelp with that link pasted afterwards.

I put this launcher on my desktop:
```
yelp x-yelp-toc:Man
```

---

### Post by kevinlyfellow on 2006-12-03
First I'd like to compliment the author of the original post for finding a way to explain why command-line is user friendly.  I don't believe that the command line is always user-friendly, but it definitely can be.

Most of the replies to the article that I have read seem to concentrate on learning.  Sit somebody down at a computer with only cli, and they won't know what to do.  But, if you stuck someone without computer experience on a gui, they probably could experiment enough to figure it out.

There is a command that I found out about 2 years after I started linux called apropos, which helps you search through the descriptions of man pages.  If a person is given this command, then it is possible that he/she could actually be able to explore enough to figure out some of the basic commands and be able to read some of the man pages (come on people, most of the man pages really aren't that hard to skim through).  This makes the learning curve a lot less steep.  I believe that the most important thing to using a computer is the exploration, and command-line has some tools to help explore, but there is nothing for someone who knows nothing.

In terms of usability, command line almost always wins out when working with many files, and is very useful in many other situations.  Gui's are useful for looking through long lists of things (synaptic is much better than deselect) and graphics (obviously) and many more things.  But since the question is not about usability, we need to think about what the right tool for the job is.  I wouldn't object to the idea that they are both friendly, depending on the job, if we were to take user-friendly to mean it is easy to use.

Another interesting thought that I have is if the majority of people use linux.  Learning would not be such an issue.  Linux really is about community and helping others out.  Command line may become an easy thing to use because it would be a common "tool" that everyone is used to and if you need to know a command, maybe your neighbor knows or a friend.  I think that it would become natural for many of us to use it.

I once found a site on the internet that compared a gui to a picture book and command line to normal book.  This whole issue may be as simple as knowing that the picture book is good at one stage of learning and the book is good for the next stage, but both are good and helpful for literacy.

I know I'm posting late in the thread, but I hope I added something for someone.

---

### Post by jamyskis on 2006-12-03
> **atoponce said:**
> I just can't imagine separating the terminal from the operating system.  Linux and Unix both are just too ingrained with it.  I hope they don't separate.

This is a common theme that keeps getting repeated. Nobody is talking about seperating the terminal from the OS - all we're discussing is providing an extra interface possibility between the GUI and the terminal.

---

### Post by aysiu on 2006-12-03
Sounds as if you got it, kevinlyfellow. Some people are just too tied to the GUI or CLI to realize they both have value.

---

### Post by Peepsalot on 2006-12-03
lol, yeah it's funny when people always bring that up.  Like every time a GUI program is written, some command line application is removed from the face of the earth.

---

### Post by darkhatter on 2006-12-03
> **Polygon said:**
> techinally you could boot up into "failsafe" mode which uses a known working xorg.conf in case you bork yours up, but actually reparing the broken one on the other hand

these things could easily be done by someone who knows about these things and can just make a gui frontend for it. From what ive heard, making the GUI is the easiest part.

but the grub one is a must. the first time i tried to restore grub i ended up screwing something up and ubuntu wouldent boot, cause of that awful tutorial of going through the install cd and mounting the partitions and then skipping ahead a few steps and... ugg

but the grub-install command is much easier.

when it fails, it could restart the gui using the vesa driver then let you configure options using a tool kind of like sax from suse

---

### Post by atoponce on 2006-12-03
> **jamyskis said:**
> This is a common theme that keeps getting repeated. Nobody is talking about seperating the terminal from the OS - all we're discussing is providing an extra interface possibility between the GUI and the terminal.

I am aware of that.  Thank you for the clarification.  However, without fail, these conversations always end up about replacing the terminal with some GUI frondend, as the terminal is archaic and cryptic.  I just hope that never happens.  EVER!

---

### Post by ciscosurfer on 2006-12-03
> **TLE said:**
> Well it sort in the same ballpark.
- Configure and test X
[Edit]
I believe that about 80% of the times you end up with a broken X it is because you are trying meddle your way through some sort of configuration. Therefore I regard it is as an absolute necessity to have a GUI way to configure AND test an X configuration. I myself love this big toy that is Linux, and every time I install a new distribution is a little party, except from when I want to setup my X the way I want it, that always gets me and I end up passed up under the table, metaphorically speaking ;)This would certainly be nice (the testing part).  Perhaps some dev could incorporate an xnest into the commands to test the config after you're done pointing and clicking in a GUI.

--And doesn't dpkg-reconfigure xserver-xorg count as a way of reconfiguring your xorg.conf when it gets botched?  Perhaps creating some kind of front-end for this would be nice, but if you're GUI botched, how ya going to get this working?  I suppose in Recovery mode.  There I go answering my own questions again. *shakes head*

---

### Post by aysiu on 2006-12-03
> **ciscosurfer said:**
> This would certainly be nice (the testing part).  Perhaps some dev could incorporate an xnest into the commands to test the config after you're done pointing and clicking in a GUI.

--And doesn't dpkg-reconfigure xserver-xorg count as a way of reconfiguring your xorg.conf when it gets botched?
Yes, but you have to know the command ```
sudo dpkg-reconfigure xserver-xorg
``` which is a terminal command.

---

### Post by ciscosurfer on 2006-12-03
> **23meg said:**
> System / Help / System Documentation / Manual Pages.I love this answer because so often people neglect to use the docs that come with their distro.  Ubuntu has good docs. :KS  Except this doesn't take into account apps that you've added after the initial install ;-(

---

### Post by ciscosurfer on 2006-12-03
> **aysiu said:**
> Yes, but you have to know the command ```
sudo dpkg-reconfigure xserver-xorg
``` which is a terminal command.Right, which is why I suggested a gui front-end for it after I wrote that (I probably was editing my post as you were typing in yours...sorry)

---

### Post by ciscosurfer on 2006-12-03
> **Peepsalot said:**
> Well I just figured it out, so I'm going to answer my own question in case anyone is interested.  When you find the help page you want to make a shortcut to, you can right click and "Copy link location".  Then just make a launcher that calls yelp with that link pasted afterwards.

I put this launcher on my desktop:
```
yelp x-yelp-toc:Man
```That command does nothing for me.  

My links look like this: 
yelp file:///usr/share/gnome/help/user-guide/C/user-guide.xml#gospanel-566
and
yelp man:/usr/share/man/man5/apt.conf.5.gz

---

### Post by Johnsie on 2006-12-04
In answer to the topic, yes. It has gotten better since dapper though. Terminal should always be available as an option but in this day and age a lot of people want intuitive interfaces that are easy to use. Point and click stuff is easier for new people to understand.

---

### Post by Peepsalot on 2006-12-04
> **ciscosurfer said:**
> That command does nothing for me.  

My links look like this: 
yelp file:///usr/share/gnome/help/user-guide/C/user-guide.xml#gospanel-566
and
yelp man:/usr/share/man/man5/apt.conf.5.gz
Yeah, I can't quite figure it out.  I realized after I posted that, for some reason it only works if I already have another yelp window open.

---

### Post by sawjew on 2006-12-04
A samba configuration gui would be great, just for things such as setting security to user or share and adding samba users and passwords.  

Another gui tool I have installed and think is great is the usplash switcher.  If we have a graphical boot a graphical way to configure it makes sense.

---

### Post by aysiu on 2006-12-04
Isn't *smb4k* a GUI configuration for Samba?

You're right about the USplash switcher, though.

---

### Post by sawjew on 2006-12-04
smb4k is a kde app and brings in nearly all of kde to install it.  I have used it before in suse and simply mepis but I prefer not to have too many kde libraries and apps just to keep the clutter down.

---

### Post by luca.b on 2006-12-04
smb4k isn't a Samba configuration tool, but instead a Samba network browsing and mounting application.

---

### Post by 3rdalbum on 2006-12-04
I don't think there's a GUI frontend for Xen.

An Apache frontend would be great too - especially if it could somehow tell you the current status of the server.

Also, a decent GUI-based Live CD installer would be good too. Like the Alternate CD installer, but written in GTK.

---

### Post by 23meg on 2006-12-04
> **ciscosurfer said:**
> I love this answer because so often people neglect to use the docs that come with their distro.  Ubuntu has good docs. :KS  Except this doesn't take into account apps that you've added after the initial install ;-(It does; just type *"man app-name"* in the search box. New apps just aren't added to the list; you can still view their man pages.

---

### Post by jbtito03 on 2006-12-04
Hi all...

U have a nice program/GUI for your system, cluster, network and servers called WEBMIN. It uses a stand alone server and is PERFECT for remote or local sys administartion including apache, samba, mysql, etc.

check it out:

[http://www.webmin.com/]("http://www.webmin.com/")


Cheers... 


JB

---

### Post by Carrots171 on 2006-12-04
You need the terminal in Ubuntu to set up an ADSL internet connection. 

SuSE and Mandriva have graphical configuration tools for ADSL and cable connections, and standalone graphical configuration tools do exist; there's one called RP-PPPOE for PPPOE connections.

---

### Post by atoponce on 2006-12-04
> **3rdalbum said:**
> Also, a decent GUI-based Live CD installer would be good too. Like the Alternate CD installer, but written in GTK.

I'm going to play Devil's Advocate here, but I don't see the need for a GUI-based installer.  What different options are there with a GUI-based from a text-based?  The only difference I see is using your mouse instead of the keyboard.  The options are exactly the same.

---

### Post by super breadfish on 2006-12-04
I wouldn't say Ubuntu is overly dependent on the terminal. As long as there is good documentation behind it Ubuntu can be as dependent as it likes and things should work out fine for even the newest user.
This is the thing I think Ubuntu should focus on. I'm still a fairly new user, and I've spent plenty of time reading through how tos and help files most of which use the command line. The vast majority of them read a bit like this:

Open Terminal. Enter this. Then this. And this. Done.

The problem is that while it gets things to work quickly, it doesn't teach the user anything. It's just a list of instructions that the user follows and then forgets about. There is rarely ever explanation of what these commands do. Users may use the same commands in several different guides, but never learn how to use them on their own through them.
I'm not saying each document needs a lengthy essay on the inner workings of apt-get, but just a few words about what the commands do and how they work would help a lot of people get to know the command line. Not only would it make things seem a little less scary, but it also helps to build up knowledge of the command line, so there is less dependence of GUIs for new users.

---

### Post by Brunellus on 2006-12-04
> **super breadfish said:**
> I wouldn't say Ubuntu is overly dependent on the terminal. As long as there is good documentation behind it Ubuntu can be as dependent as it likes and things should work out fine for even the newest user.
This is the thing I think Ubuntu should focus on. I'm still a fairly new user, and I've spent plenty of time reading through how tos and help files most of which use the command line. The vast majority of them read a bit like this:

Open Terminal. Enter this. Then this. And this. Done.

The problem is that while it gets things to work quickly, it doesn't teach the user anything. It's just a list of instructions that the user follows and then forgets about. There is rarely ever explanation of what these commands do. Users may use the same commands in several different guides, but never learn how to use them on their own through them.
I'm not saying each document needs a lengthy essay on the inner workings of apt-get, but just a few words about what the commands do and how they work would help a lot of people get to know the command line. Not only would it make things seem a little less scary, but it also helps to build up knowledge of the command line, so there is less dependence of GUIs for new users.
we do things this way because most users really couldn't give a darn how the command line works.  They want a working system, they want it NOW, or they're going to declare that LINUX ISN'T READY FOR THE DESKTOP.  

So yes, we'll send them the magic spells and incantations to get things up and running.  It's a LOT easier on those of us giving support to have them paste in a command that works, rather than waste time and effort talking them through a GUI.

---

### Post by aysiu on 2006-12-04
[quote=super breadfish]The problem is that while it gets things to work quickly, it doesn't teach the user anything. It's just a list of instructions that the user follows and then forgets about. There is rarely ever explanation of what these commands do. Users may use the same commands in several different guides, but never learn how to use them on their own through them.[/quote] I disagree entirely.

I was scared of the terminal when I first tried Ubuntu. That's what sent me off to Mepis for a month before returning to Ubuntu (and sticking with it for more than a year and half and counting).

How did I learn terminal commands? By copying and pasting them from [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

That's how I learned them. Sure, if I asked, people took the time to explain them to me, but I mainly learned by doing. If you type in ```
sudo apt-get install *nameofprogram*
``` and that installs the program, you quickly learn that *apt-get install* installs programs. *apt-get* doesn't stand for anything. That's all it is.

As Brunellus points out, most people just want something fixed. But if you *do* have questions about "What does this command mean?" forum members are usually more than happy to explain the meanings of those commands.

---

### Post by ciscosurfer on 2006-12-04
> **23meg said:**
> It does; just type *"man app-name"* in the search box. New apps just aren't added to the list; you can still view their man pages.By golly, you're correct.  Thanks for the tip!

---

### Post by ciscosurfer on 2006-12-04
> **super breadfish said:**
> I wouldn't say Ubuntu is overly dependent on the terminal. As long as there is good documentation behind it Ubuntu can be as dependent as it likes and things should work out fine for even the newest user.
This is the thing I think Ubuntu should focus on. I'm still a fairly new user, and I've spent plenty of time reading through how tos and help files most of which use the command line. The vast majority of them read a bit like this:

Open Terminal. Enter this. Then this. And this. Done.

The problem is that while it gets things to work quickly, it doesn't teach the user anything. It's just a list of instructions that the user follows and then forgets about. There is rarely ever explanation of what these commands do. Users may use the same commands in several different guides, but never learn how to use them on their own through them.
I'm not saying each document needs a lengthy essay on the inner workings of apt-get, but just a few words about what the commands do and how they work would help a lot of people get to know the command line. Not only would it make things seem a little less scary, but it also helps to build up knowledge of the command line, so there is less dependence of GUIs for new users.So often people forget about [this sticky post]("http://ubuntuforums.org/showthread.php?t=232059").  In addition, help is in mass abundance (was that redundant?) on the fourms, so help is never more than a click away.

---

### Post by Rede on 2006-12-04
The biggest thing is reliability. I know that there are GUIs out there for some things, but I can't count on them. ie. I use Kubuntu and used the system settings to update the xorg.conf because I was feeling lazy... but it fubared my xorg.conf and I had to manually fix it. Moreover, it didn't give me all the resolutions my monitor supported (including the native resolution of 1366x768) and took 5-10 minutes to get it working. 

Basically, I'd like reliability. As much as I hate using Windows, I have to admit that it is nice to be able to change my resolution and have it just work, without fighting for 5-10 minutes with xorg.conf, modelines, and whatnot. It also makes me look dumb when I just finish advocating linux to my roommates only to have them watch me spend more than 5+ minutes and be dropped to a commmand line in Kubuntu completing a task that takes 10 seconds in Windows.

But more on topic... a New Hardware/Universal Device Driver Installation gui would be useful. It could be something similar to providing a .inf file in Windows and having it take care of everything for you.

---

### Post by daynah on 2006-12-04
everything I've wanted to do in ubuntu I've been able to do in except when the ATI driver messed up. And... really... there wasn't a way to do that in gui 'cause how do you have a gui when you don't have a video card?

I think people think you have to do more stuff in terminal than you have to (like editing repos and apt-get) because that's just how we offer help online; it's an easier way to offer help. Unfortunately, people don't realise that it's such an easier way to offer and receive help.

---

### Post by aysiu on 2006-12-04
> **daynah said:**
> 
I think people think you have to do more stuff in terminal than you have to (like editing repos and apt-get) because that's just how we offer help online; it's an easier way to offer help. Unfortunately, people don't realise that it's such an easier way to offer and receive help. Exactly my point in creating this thread.

I'm trying to isolate exactly what **needs** the terminal, as opposed to tasks we **prefer** to use the terminal for.

---

### Post by omns on 2006-12-04
.

---

### Post by insane_alien on 2006-12-04
as long as the terminal never loses functionality like the crippled shell MSDOS became i'll be happy with ubuntu.

---

### Post by ciscosurfer on 2006-12-04
> **insane_alien said:**
> as long as the terminal never loses functionality like the crippled shell MSDOS became i'll be happy with ubuntu.The DOS shell is still used heavily and widely by Admins -- it's feature-set is quite extensive for administering servers, etc.

---

### Post by Peti29 on 2006-12-05
I'm absolutely new to Ubuntu (and more or less to Linux also) however I work as a programmer.
So maybe you're interested how someone just switching from Windows sees things. (I'm intended to drop a "first impressions" post later, but now for the question: )
- In my opinion Ubuntu really needed a GUI for setting up DSL connection (as mentioned before by others). That is because when you're finally connected you may easily find answers to your problems searching the net, but until that you are on your own. Fortunately Ubuntu has a rather good built in help documentation so it didn't take long to find 'pppoeconf'. Still it was a bit confusing having GUI for proxi settings, modem config, etc. and not having one for DSL setup.
- Also some graphical command (maybe put in the panel) to connect/disconnect would be nice. I've created "shortcuts" for this task on my desktop: text files consisting merely of '#!/bin/bash pon dsl-provider' and 'poff -a' similarly. (I also missed the little icon from the task bar indicating my online status, but then I found Network Monitor :))

---

### Post by TitanKing on 2006-12-05
I love the terminal, what would Linux be without it! I remotely control all my servers through SSH, the terminal is much faster. And much easier to get a noob up and running faster, sinply paste the commands.

The Terminal ROCKS !

---

### Post by Brunellus on 2006-12-05
> **Peti29 said:**
> I'm absolutely new to Ubuntu (and more or less to Linux also) however I work as a programmer.
So maybe you're interested how someone just switching from Windows sees things. (I'm intended to drop a "first impressions" post later, but now for the question: )
- In my opinion Ubuntu really needed a GUI for setting up DSL connection (as mentioned before by others). That is because when you're finally connected you may easily find answers to your problems searching the net, but until that you are on your own. Fortunately Ubuntu has a rather good built in help documentation so it didn't take long to find 'pppoeconf'. Still it was a bit confusing having GUI for proxi settings, modem config, etc. and not having one for DSL setup.
- Also some graphical command (maybe put in the panel) to connect/disconnect would be nice. I've created "shortcuts" for this task on my desktop: text files consisting merely of '#!/bin/bash pon dsl-provider' and 'poff -a' similarly. (I also missed the little icon from the task bar indicating my online status, but then I found Network Monitor :))
Pet Peeve:  they're "launchers," not "shortcuts."  

I hate "shortcut," since MSFT have used the term very loosely in the past to refer to any or all of:

* Hypertext links
* URLs
* Bookmarked URLs
* Launchers
* Quasi-symbolic links

(I may have forgotten a few)

As such, the term is enormously unhelpful, and I find myself constantly having to ask users what they mean by the word.

---

### Post by jamyskis on 2006-12-05
> **Peti29 said:**
> - In my opinion Ubuntu really needed a GUI for setting up DSL connection (as mentioned before by others). That is because when you're finally connected you may easily find answers to your problems searching the net, but until that you are on your own. Fortunately Ubuntu has a rather good built in help documentation so it didn't take long to find 'pppoeconf'. Still it was a bit confusing having GUI for proxi settings, modem config, etc. and not having one for DSL setup.


Actually the rather humorous irony of this struck me a while back. I actually found pppoeconf through ubuntuforums.org - but only because I still had my Windows partition. What happens if a user replaces his or her entire Windows partition and can't find the DSL configuration tool though? Consider the conundrum of a user who relies on mailing lists and internet forums to get his internet connection working... :mrgreen:

---

### Post by mushroom on 2006-12-05
Mounting another internal drive permanently, switching Usplashes and maybe ADSL configuration (it automatically worked on my system) are the only things that really need a GUI function; external drives are usually automatically detected and you're given an option to mount it. The other proposed operations are advanced enough that someone with the intentions of doing those things shouldn't be frightened by a terminal.

---

### Post by sawjew on 2006-12-05
Another gui tool I think is essential is a graphical disk formatter for flash drives and dvd-ram or other removable drives.  We have the floppy formatter we need something similar, particularly for flash drives, so we can just right click and select format.

---

### Post by aysiu on 2006-12-05
> **sawjew said:**
> Another gui tool I think is essential is a graphical disk formatter for flash drives and dvd-ram or other removable drives.  We have the floppy formatter we need something similar, particularly for flash drives, so we can just right click and select format.
It's called GParted.

---

### Post by TLE on 2006-12-05
> **mushroom said:**
> Mounting another internal drive permanently, switching Usplashes and maybe ADSL configuration (it automatically worked on my system) are the only things that really need a GUI function; external drives are usually automatically detected and you're given an option to mount it. The other proposed operations are advanced enough that someone with the intentions of doing those things shouldn't be frightened by a terminal.

Setting up resolutions for your flat screen?
Configuring a dualview setup ? (This is actually done without a hickup in windows and is a major pain in Linux)

---

### Post by sawjew on 2006-12-05
> **aysiu said:**
> It's called GParted.

Gparted doesn't work for dvd-ram disks and I still think it should be available on right click.

---

### Post by imhdd on 2006-12-05
> **GrantG said:**
> I believe that ubuntu has the balance just about right. As a distro it attracts newbies and experienced users alike. It must be doing something right :)

(NOTE: aysiu, this may be a little off your original topic but it seems to fit the current drift.)

I also think Ubuntu has it about right. My situation is this: I repair and build computers for people who can't afford to pay for the services. These are hard working people usually with children and low paying jobs or older folks living on Social Security. They can't afford the cost of Microsoft products and I certainly can't afford to donate the cost of an operating system for the computers I service. The main impediment to my work for the past few years is the cost of MS Windows. And it's getting worse with Vista.

What I need in an operating system is simplicity, basic functionality, a lot of help, and low cost. Ubuntu fits that description better than any distribution I've tried. I'm almost to the position of being able to install Ubuntu and give a short course in how to use it - all by point and click. The idea of any of my 'clients' using a command line is beyond imagination. And the idea of me being able to use the command line for more than the most basic functions is also out of reach at this time (I'm working on it).

My friends, there are millions and millions of 'clients' just like mine all around the world. Their goal isn't to become a geek; but they are awed when you help them point and click their way through a simple Google search. 

Fortunately, Ubuntu is well on it's way to becoming the best of both worlds. The Terminal for those so inclined, and the simplicity of point and click for those who need it. 

Thanks to all the Ubuntu community for all the help. Without it I wouldn't see any way to continue helping others with computers. AYSIU and ARNIEBOY are just two of my heros. Wish I could name them all.
imhdd

---

### Post by mushroom on 2006-12-05
> Setting up resolutions for your flat screen?
Configuring a dualview setup ? (This is actually done without a hickup in windows and is a major pain in Linux)

With NVIDIA, this is provided in their configuration utility. Of course, not everyone has NVIDIA, and there really should be a better integrated configuration utility (as far as Gnome goes, KDE does pretty well). So, yeah, I agree with you in that respect.

---

### Post by xhaan on 2006-12-06
I don't think it's too dependednt.
It isn't very often that I HAVE to use the terminal, I use it because I like it.

---

### Post by FyreBrand on 2006-12-06
The only two times I absolutely wished I had a gui interface was to reinstall grub and to reconfigure xorg.  

For Xorg - The ncurses type of interface (if that's what it is) is okay,  but when I think of an interface for reconfiguring the the xserver I think an application that have a document file that helps me choose the proper options and settings.  Learning to configure this is a bear and I still suck at it.

For Grub - I would envision this utility to be on a live CD.  Obviously if grub isn't working booting to Kubuntu doesn't work very well.  When I reinstalled Windows for IIS/PHP it did the obligatory bootloader over-write.  I wrote the grub reinstall steps down but I messed it up bad and ended up having to reinstall Kubuntu.  Even a Windows utility would be nice where you can install grub to the MBR or boot partition and have it point to your Linux partition where the rest of the grub files are.  I guess that's a little bit much though, eh?  hehe.

---

### Post by aysiu on 2006-12-06
> **FyreBrand said:**
> 
For Grub - I would envision this utility to be on a live CD.  Obviously if grub isn't working booting to Kubuntu doesn't work very well.  When I reinstalled Windows for IIS/PHP it did the obligatory bootloader over-write.  I wrote the grub reinstall steps down but I messed it up bad and ended up having to reinstall Kubuntu.  Even a Windows utility would be nice where you can install grub to the MBR or boot partition and have it point to your Linux partition where the rest of the grub files are.  I guess that's a little bit much though, eh?  hehe. Not really, since Mepis has had this feature for at least two years. Mepis features KDE (just as Kubuntu does) and is now based on Ubuntu, so you may want to check it out, since you use Kubuntu.

---

### Post by qalimas on 2006-12-06
> **TLE said:**
> Setting up resolutions for your flat screen?
Configuring a dualview setup ? (This is actually done without a hickup in windows and is a major pain in Linux)

In KDE, it was all point-and-click configuration for my twin view, took about 2 minutes...

---

### Post by Radiolad on 2006-12-09
I totally agree with the need for GUI. The whole business of 'command line' is a great turn off to me and I'm sure many others. I like Ubuntu but it's like a maze that is easy to get lost in :-k
I'm a 'windows' person and GUI is sooooo much friendlier. 
The Ubuntu developers must realize (replies from any are welcome)  that this is 2006 and not 1986.
  Those are my thoughts for what they are worth :rolleyes:        Radiolad.

---

### Post by loell on 2006-12-09
> **Radiolad said:**
> I totally agree with the need for GUI. The whole business of 'command line' is a great turn off to me and I'm sure many others. I like Ubuntu but it's like a maze that is easy to get lost in :-k
I'm a 'windows' person and GUI is sooooo much friendlier. 
The Ubuntu developers must realize (replies from any are welcome)  that this is 2006 and not 1986.
  Those are my thoughts for what they are worth :rolleyes:        Radiolad.

could you be more specific? the need for gui of what particularly?

ubuntu developers had made many realizations in just a short span of time.
and they are doing a great job even if many of them are just voluntary.

---

### Post by Fatec on 2006-12-11
> **mtron said:**
> well i also tested the last suse release... the updater was not working AT ALL. It took them some months to fix it. The priority for Novell is the business distro, not the Opensuse one, that's the main advantage of ubuntu, everyone gets the same product (real open source spirit)

next is the debian base ubuntu uses. It's just the best package managing system, and the repositories are enormous. Yast and all the other tools just don't play in the same league.

For me it's not a big problem that configuration is done via the terminal. In many cases, no in basically all cases, the documentation for ubuntu & debian is perfect, and easy to reproduce. 

You configure your system only once, so it shouldn't be a priority for ubuntu devs to make a gui configuration for everything.

The update system was broken in RC2 of opensuse...it is fixed in the final release (as far as i can tell, tho 912 updates to download..that was a pain)

I agree suse is ALOT easier to use than ubuntu...and has alot more gui interfaces (which admittedly i love, sometimes i just dont feel like using the command line, infact, if ive had a long day, i hate doing so and just boot into xp)

Wether linux users admit it or not, doing things by the command line isnt the best way to get people to use linux, id prefer it if linux was all gui BUT still had the option to use command lines for more advanced users (or ppl who prefer using it).

Admit it..simple *click, install, done, now go play* is better than using the terminal.

I find suse alot faster than ubuntu (suprisingly) and the default desktops are quite nice (admittedly, again, i hate ubuntus *poo* stain brown (lol)...although love ubuntu overall)

i just enjoy using my pc..ya know?...i dont wanna play around with command lines for half an hour to install something, i want a gui...as many users do...and thats why windows dominates the market. yes, windows sucks..it has many problems..but its EASY!

and smart, or not, easier is better.

---

### Post by Fatec on 2006-12-11
> **mtron said:**
> well i also tested the last suse release... the updater was not working AT ALL. It took them some months to fix it. The priority for Novell is the business distro, not the Opensuse one, that's the main advantage of ubuntu, everyone gets the same product (real open source spirit)

next is the debian base ubuntu uses. It's just the best package managing system, and the repositories are enormous. Yast and all the other tools just don't play in the same league.

For me it's not a big problem that configuration is done via the terminal. In many cases, no in basically all cases, the documentation for ubuntu & debian is perfect, and easy to reproduce. 

You configure your system only once, so it shouldn't be a priority for ubuntu devs to make a gui configuration for everything.

The update system was broken in RC2 of opensuse...it is fixed in the final release (as far as i can tell, tho 912 updates to download..that was a pain)

I agree suse is ALOT easier to use than ubuntu...and has alot more gui interfaces (which admittedly i love, sometimes i just dont feel like using the command line, infact, if ive had a long day, i hate doing so and just boot into xp)

Wether linux users admit it or not, doing things by the command line isnt the best way to get people to use linux, id prefer it if linux was all gui BUT still had the option to use command lines for more advanced users (or ppl who prefer using it).

Admit it..simple *click, install, done, now go play* is better than using the terminal.

I find suse alot faster than ubuntu (suprisingly) and the default desktops are quite nice (admittedly, again, i hate ubuntus *poo* stain brown (lol)...although love ubuntu overall)

i just enjoy using my pc..ya know?...i dont wanna play around with command lines for half an hour to install something, i want a gui...as many users do...and thats why windows dominates the market. yes, windows sucks..it has many problems..but its EASY!

and smart, or not, easier is better.

---

### Post by mjpoetic on 2006-12-11
No offense, but Windows creates idiots (sort of like AOL did with internet users).  There are at least a handful of distros that I have used that use a GUI for a lot of things.  But seriously though...how hard is it to come onto these forums and follow a simple HOWTO?  Anyway, to each his/her own.

---

### Post by Fatec on 2006-12-11
> **mjpoetic said:**
> No offense, but Windows creates idiots (sort of like AOL did with internet users).  There are at least a handful of distros that I have used that use a GUI for a lot of things.  But seriously though...how hard is it to come onto these forums and follow a simple HOWTO?  Anyway, to each his/her own.

Simple? well..yes and no..alot of the howtos on here are wrong/out of date...or simply badly typed out.

i dont mind doing howtos, dont get me wrong..but as i said, after a long day of work, you dont want to go through a howto and hope it works..u want simpleness so you can enjoy urself, so yea, each to their own.

---

### Post by kazuya on 2006-12-11
I could never leave from the current Ubuntu to OpenSuse. Ubuntu is just easier to manage and work with than Suse for me. I too was like the typical window user who preferred gui over CLI.

Now I use both CLI and gui. The howto guides make using CLI ridiculously easy to follow and learn. The instructions are ridiculously easy to follow. Moreover, what Ubuntu is great at is giving user the power to change or control the look of their gui from a gui and from the commandline.

Package manager is near unparallel as is typical of Debian-based distros. The forum here is the best for answering questions and having fun.

With Ubuntu, everything just works while allowing user to totally reconfigure system, while in SUSE it seems to glitter in the beginning and works also sometimes for user not seeking to revamp the system to use many other window managers.

Working at the CLI is a one time thing for me until perhaps, the next major release. And while the CLI is in work, you can do many other things like watching video, typing email, etc, etc, burning DVD, changing an icon, .. So I do not understand where the theme of no time for CLI comes in. Would user rather not even see the CLI at all ever. That would be a mistake, because GUI use alone is limiting to creativity and development. For all those gui functions, there are CLI codes at work. SOme are worth seeing and some are not. This is why we need both. If you want your distro or OS to simply put you at the GUI with no way of changing to your personal liking and ultimately sharing with other users, but prefer a company to give you options of what you call eye-candy, then go for it.

This is not what a distro should be for me. Use the CLI long enough and you may start to prefer it to some of the gui equivalents. 
Also, once spoiled by the beauty of Ubuntu's adaptation of gui and CLI, it would be hard to be gone to SUSE for long.

I like many distros, and they all have their strengths. But for me, Ubuntu supplants SUSE's use and more. So I'll stick to Ubuntu over SUSE.

---

### Post by kazuya on 2006-12-11
I could never leave from the current Ubuntu to OpenSuse. Ubuntu is just easier to manage and work with than Suse for me. I too was like the typical window user who preferred gui over CLI.

Now I use both CLI and gui. The howto guides make using CLI ridiculously easy to follow and learn. The instructions are ridiculously easy to follow. Moreover, what Ubuntu is great at is giving user the power to change or control the look of their gui from a gui and from the commandline.

Package manager is near unparallel as is typical of Debian-based distros. The forum here is the best for answering questions and having fun.

With Ubuntu, everything just works while allowing user to totally reconfigure system, while in SUSE it seems to glitter in the beginning and works also sometimes for user not seeking to revamp the system to use many other window managers.

Working at the CLI is a one time thing for me until perhaps, the next major release. And while the CLI is in work, you can do many other things like watching video, typing email, etc, etc, burning DVD, changing an icon, .. So I do not understand where the theme of no time for CLI comes in. Would user rather not even see the CLI at all ever. That would be a mistake, because GUI use alone is limiting to creativity and development. For all those gui functions, there are CLI codes at work. SOme are worth seeing and some are not. This is why we need both. If you want your distro or OS to simply put you at the GUI with no way of changing to your personal liking and ultimately sharing with other users, but prefer a company to give you options of what you call eye-candy, then go for it.

This is not what a distro should be for me. Use the CLI long enough and you may start to prefer it to some of the gui equivalents. 
Also, once spoiled by the beauty of Ubuntu's adaptation of gui and CLI, it would be hard to be gone to SUSE for long.

I like many distros, and they all have their strengths. But for me, Ubuntu supplants SUSE's use and more. So I'll stick to Ubuntu over SUSE.

---

### Post by dvarsam on 2006-12-12
Hello!

I thought I should come in & drop my few cents...

> **mjpoetic said:**
> How will you get Suse then?
The .iso is about 3.7 GBs whereas Ubuntu 6.10 is only in the 600s (in MBs).

Is this considered an argument?
We nowadays have fast ADSL connections (except maybe underdeveloped countries)!
In the Future things will be faster!

[quote=mjpoetic]That's what I love about linux in general...you can use the distro that best suits your needs.
...This forum is why I love Ubuntu so much.
I never used to get much help from the Suse based forums (when I used Suse).[/quote]

Honest & fair view!

[quote=Radiolad]I totally agree with the need for GUI.
The whole business of 'command line'...
I'm a 'windows' person and GUI is sooooo much friendlier.
The Ubuntu developers must realize (replies from any are welcome) that this is 2006 and not 1986.[/quote]

Yes, we need more GUIs!

[quote=loell]...Could you be more specific? the need for GUI of what particularly?[/quote]

It is so hard to think of some examples?

1. How about a GUI for Samba Configuration?
2. How about a GUI for NFS Configuration?

OR

3. A step-by-step Wizard to help you setup the above!

4. How about .deb files for Tapioca?
5. How about easy installation of codecs?

[quote=Iandefor]That's some pretty strong language for something so simple as using what's best for you.[/quote]

Simple Truth here!
No need to be "fanatic" with Ubuntu & _intentionally_ dish Suse...
However, when I _pay_ for a distro such as MS Windows & get all these viruses, I am sorry but I would dish it too! :)
It is good that OpenSuse is free to try for those interested to buy a Full version. At least, you are offered to tryout & if you don't like, no need to make fuss about it... You didn't pay for it in the first place!

[quote=sakis]Were can i find a step by step how-to similar to [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for opensuse? I found this [http://en.opensuse.org/Restricted_Formats](http://en.opensuse.org/Restricted_Formats) but it says nothing and has no links, since there are legal issues![/quote]

Don't forget that Novell is a company oriented towards profit!
And I don't think that Suse is a very profitable product up to now...
Maybe in the near future it going to be considered a gold mine!
But not for now, it is still too early...
So, don't expect too much organizing from their side.

[quote=mtron]...next is the debian base ubuntu uses.
It's just the best package managing system & the repositories are enormous. Yast and all the other tools just don't play in the same league.[/quote]

Simple Truth!
I wish Suse had adopted ".deb" package management...
What a change would that be (huge progress for all the Linux community!).
But don't forget that Suse now suggests adoption of Ext3 Filesystem instead of ReiserFS (that is a big improvement!).
It is a step towards "unity" across all Linux Distros!
I guess Linux "unity" in adoption of ".deb" format or ".rpm" format should be the next step...
It would help the Linux community move forward faster!!!
And also "unity" with Terminal Commands!
It would be nice if Terminal Commands were the same across all Linux Distros.

[quote=fatec]I agree Suse is a LOT easier to use than Ubuntu...and has a lot more GUI interfaces (which admittedly i love, sometimes I just don't feel like using the command line, in fact, if Ive had a long day, I hate doing so and just boot into XP)
Whether Linux users admit it or not, doing things by the command line isn't the best way to get people to use Linux, id prefer it if Linux was all GUI BUT still had the option to use command lines for more advanced users (or ppl who prefer using it).
Admit it..simple *click, install, done, now go play* is better than using the terminal.[/quote]

Simple Truth!
I especially like this part:
[quote=fatec]I just don't feel like using the command line, in fact, if Ive had a long day, I hate doing so and just boot into XP)[/quote]

Dear Ubuntu Programmers, please concentrate to make our lives easier please!

[quote=mjpoetic]No offense, but Windows creates idiots (sort of like AOL did with Internet users).
...But seriously though...how hard is it to come onto these forums & follow a simple HOWTO?[/quote]

What an argument...
So you are suggesting that Terminal is better...
Are you _serious_ man?
It would have been better to admit "I am fanatically biased towards my Ubuntu compared to any other Distros (whether it is Windows, Linux or else...".

And if you want to talk about HowTos:

Please help me in these:

1. [http://www.ubuntuforums.org/showthread.php?t=312968](http://www.ubuntuforums.org/showthread.php?t=312968)
OR
2. [http://www.ubuntuforums.org/showthread.php?t=311687](http://www.ubuntuforums.org/showthread.php?t=311687)

On above #1, I have followed every HowTo.
On above #2, a HowTo does not exist!

[quote=fatec]...a lot of the Howtos on here are wrong/out of date...or simply badly typed out.[/quote]

Simple Truth!!!

[quote=jbtito03]...And these forums RULE!
The best I have ever seen...
I have never participated as much on forums as i am now.

And about Distros - as long as it is free software - if it works for you go for it.
By free software I mean free as in freedom.[/quote]

True!
Ubuntu Forums are the best Linux Forums out there!
It might be also considered even as the best Forums out there!
... cause I haven't seen any Windows Forums out there...
I really wonder: Are there any Windows Forums out there as good as this one?

And one more thing:
The Forum Staff here care of _your_ opinions & suggestions of improvement...
I have seen this happening...
In the near future I also hope to see this implemented too:

[http://www.ubuntuforums.org/showthread.php?t=311358](http://www.ubuntuforums.org/showthread.php?t=311358)

Thanks.

---

### Post by dvarsam on 2006-12-12
Hello!

I thought I should come in & drop my few cents...

> **mjpoetic said:**
> How will you get Suse then?
The .iso is about 3.7 GBs whereas Ubuntu 6.10 is only in the 600s (in MBs).

Is this considered an argument?
We nowadays have fast ADSL connections (except maybe underdeveloped countries)!
In the Future things will be faster!

[quote=mjpoetic]That's what I love about linux in general...you can use the distro that best suits your needs.
...This forum is why I love Ubuntu so much.
I never used to get much help from the Suse based forums (when I used Suse).[/quote]

Honest & fair view!

[quote=Radiolad]I totally agree with the need for GUI.
The whole business of 'command line'...
I'm a 'windows' person and GUI is sooooo much friendlier.
The Ubuntu developers must realize (replies from any are welcome) that this is 2006 and not 1986.[/quote]

Yes, we need more GUIs!

[quote=loell]...Could you be more specific? the need for GUI of what particularly?[/quote]

It is so hard to think of some examples?

1. How about a GUI for Samba Configuration?
2. How about a GUI for NFS Configuration?

OR

3. A step-by-step Wizard to help you setup the above!

4. How about .deb files for Tapioca?
5. How about easy installation of codecs?

[quote=Iandefor]That's some pretty strong language for something so simple as using what's best for you.[/quote]

Simple Truth here!
No need to be "fanatic" with Ubuntu & _intentionally_ dish Suse...
However, when I _pay_ for a distro such as MS Windows & get all these viruses, I am sorry but I would dish it too! :)
It is good that OpenSuse is free to try for those interested to buy a Full version. At least, you are offered to tryout & if you don't like, no need to make fuss about it... You didn't pay for it in the first place!

[quote=sakis]Were can i find a step by step how-to similar to [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for opensuse? I found this [http://en.opensuse.org/Restricted_Formats](http://en.opensuse.org/Restricted_Formats) but it says nothing and has no links, since there are legal issues![/quote]

Don't forget that Novell is a company oriented towards profit!
And I don't think that Suse is a very profitable product up to now...
Maybe in the near future it going to be considered a gold mine!
But not for now, it is still too early...
So, don't expect too much organizing from their side.

[quote=mtron]...next is the debian base ubuntu uses.
It's just the best package managing system & the repositories are enormous. Yast and all the other tools just don't play in the same league.[/quote]

Simple Truth!
I wish Suse had adopted ".deb" package management...
What a change would that be (huge progress for all the Linux community!).
But don't forget that Suse now suggests adoption of Ext3 Filesystem instead of ReiserFS (that is a big improvement!).
It is a step towards "unity" across all Linux Distros!
I guess Linux "unity" in adoption of ".deb" format or ".rpm" format should be the next step...
It would help the Linux community move forward faster!!!
And also "unity" with Terminal Commands!
It would be nice if Terminal Commands were the same across all Linux Distros.

[quote=fatec]I agree Suse is a LOT easier to use than Ubuntu...and has a lot more GUI interfaces (which admittedly i love, sometimes I just don't feel like using the command line, in fact, if Ive had a long day, I hate doing so and just boot into XP)
Whether Linux users admit it or not, doing things by the command line isn't the best way to get people to use Linux, id prefer it if Linux was all GUI BUT still had the option to use command lines for more advanced users (or ppl who prefer using it).
Admit it..simple *click, install, done, now go play* is better than using the terminal.[/quote]

Simple Truth!
I especially like this part:
[quote=fatec]I just don't feel like using the command line, in fact, if Ive had a long day, I hate doing so and just boot into XP)[/quote]

Dear Ubuntu Programmers, please concentrate to make our lives easier please!

[quote=mjpoetic]No offense, but Windows creates idiots (sort of like AOL did with Internet users).
...But seriously though...how hard is it to come onto these forums & follow a simple HOWTO?[/quote]

What an argument...
So you are suggesting that Terminal is better...
Are you _serious_ man?
It would have been better to admit "I am fanatically biased towards my Ubuntu compared to any other Distros (whether it is Windows, Linux or else...".

And if you want to talk about HowTos:

Please help me in these:

1. [http://www.ubuntuforums.org/showthread.php?t=312968](http://www.ubuntuforums.org/showthread.php?t=312968)
OR
2. [http://www.ubuntuforums.org/showthread.php?t=311687](http://www.ubuntuforums.org/showthread.php?t=311687)

On above #1, I have followed every HowTo.
On above #2, a HowTo does not exist!

[quote=fatec]...a lot of the Howtos on here are wrong/out of date...or simply badly typed out.[/quote]

Simple Truth!!!

[quote=jbtito03]...And these forums RULE!
The best I have ever seen...
I have never participated as much on forums as i am now.

And about Distros - as long as it is free software - if it works for you go for it.
By free software I mean free as in freedom.[/quote]

True!
Ubuntu Forums are the best Linux Forums out there!
It might be also considered even as the best Forums out there!
... cause I haven't seen any Windows Forums out there...
I really wonder: Are there any Windows Forums out there as good as this one?

And one more thing:
The Forum Staff here care of _your_ opinions & suggestions of improvement...
I have seen this happening...
In the near future I also hope to see this implemented too:

[http://www.ubuntuforums.org/showthread.php?t=311358](http://www.ubuntuforums.org/showthread.php?t=311358)

Thanks.

---

### Post by mjpoetic on 2006-12-12
> **loell said:**
> what a rant :p
Heh heh...I second that!!  dvarsam, you need an extra 20 on your Bean Count for that one.  Your points are well taken though.  ;)  Now here's my rant response. :p

> We nowadays have fast ADSL connections (except maybe underdeveloped countries)!
In the Future things will be faster!Believe it or not...I live in the United States and in South Florida at that (*cough* **GO HEAT!** *cough*) AND there are people still on dial up.

>  So you are suggesting that Terminal is better...
Are you _serious_ man?No, I am not suggesting that the terminal is better.  I like GUIs...but I just don't find using the terminal such a big task as some make it out to be.  Also, Windows does create idiots...sort of like calculators used for simple calculations.

> It would have been better to admit "I am fanatically biased towards my Ubuntu compared to any other Distros (whether it is Windows, Linux or else...".Are *you *serious man?  How can you draw that conclusion?  Seriously, how?  I am not loyal to any software.  I am loyal to the ideas that Ubuntu promotes (i.e., "Linux for Human beings").  So if something else better for me came along, I would hop on that (as a matter of fact, I installed the new Suse just to see if it was better for my desktop PC).

I was just trying to say that these forums are the best.  Hands down!!

>  And if you want to talk about HowTos...Ok, you got me there.  Howtos don't always work.  Then again, if they always did...people may not learn how to do things on their own.

Again, it's all you're choice what you want to do with your PC.  As long as Windows isn't the choice ;) ...just kidding.

---

### Post by mjpoetic on 2006-12-12
> **loell said:**
> what a rant :p
Heh heh...I second that!!  dvarsam, you need an extra 20 on your Bean Count for that one.  Your points are well taken though.  ;)  Now here's my rant response. :p

> We nowadays have fast ADSL connections (except maybe underdeveloped countries)!
In the Future things will be faster!Believe it or not...I live in the United States and in South Florida at that (*cough* **GO HEAT!** *cough*) AND there are people still on dial up.

>  So you are suggesting that Terminal is better...
Are you _serious_ man?No, I am not suggesting that the terminal is better.  I like GUIs...but I just don't find using the terminal such a big task as some make it out to be.  Also, Windows does create idiots...sort of like calculators used for simple calculations.

> It would have been better to admit "I am fanatically biased towards my Ubuntu compared to any other Distros (whether it is Windows, Linux or else...".Are *you *serious man?  How can you draw that conclusion?  Seriously, how?  I am not loyal to any software.  I am loyal to the ideas that Ubuntu promotes (i.e., "Linux for Human beings").  So if something else better for me came along, I would hop on that (as a matter of fact, I installed the new Suse just to see if it was better for my desktop PC).

I was just trying to say that these forums are the best.  Hands down!!

>  And if you want to talk about HowTos...Ok, you got me there.  Howtos don't always work.  Then again, if they always did...people may not learn how to do things on their own.

Again, it's all you're choice what you want to do with your PC.  As long as Windows isn't the choice ;) ...just kidding.

---

### Post by Hendrixski on 2006-12-12
The terminal is a powerful tool, perhaps too powerful for day to day use, but we can't take it away or else how will we do power-user tasks?  Sometimes It's easier to write a script than to do 100 mouse clicks.

Windows found this out the hard way, they're re-introducing the command line in Vista... and of course wrote a bloated and bug prone interface for it that had a virus written for it 10 days after he Vista Alpha was released.

As for SuSe, I'm interested to try it myself.  I just really don't like having to wait hours to download gigs of stuff.  And I test stuff out on virtual machines, so it takes that much longer to install.  Maybe some day when I'm not lazy.

---

### Post by Hendrixski on 2006-12-12
The terminal is a powerful tool, perhaps too powerful for day to day use, but we can't take it away or else how will we do power-user tasks?  Sometimes It's easier to write a script than to do 100 mouse clicks.

Windows found this out the hard way, they're re-introducing the command line in Vista... and of course wrote a bloated and bug prone interface for it that had a virus written for it 10 days after he Vista Alpha was released.

As for SuSe, I'm interested to try it myself.  I just really don't like having to wait hours to download gigs of stuff.  And I test stuff out on virtual machines, so it takes that much longer to install.  Maybe some day when I'm not lazy.

---

### Post by dvarsam on 2006-12-12
Hello & thanks for your reply!

[QUOTE=mjpoetic]Now here's my rant response.[/quote]

What does the word "rant" mean?

> Believe it or not...I live in the United States and in South Florida at that (*cough* **GO HEAT!** *cough*) AND there are people still on dial up.

I believe you!
Hopefully if the Bush administration had tried to focus more on providing better services to his people, things would be much better for the American people...
Instead the Bush administration only cares on how to produce more weapons & throw them on somebody else's heads...:)

> Are *you *serious man?  How can you draw that conclusion?  Seriously, how?  I am not loyal to any software.
I am loyal to the ideas that Ubuntu promotes (i.e., "Linux for Human beings").

Ok, no hard feelings then!
But let us all admit, that  we "see" many biased posts in these forums too!
So, it seems that you have straightened things out now!

> So if something else better for me came along, I would hop on that (as a matter of fact, I installed the new Suse just to see if it was better for my desktop PC).

Honest & True!
I haven't done this yet, as it takes forever to download...

> I was just trying to say that these forums are the best.  Hands down!!

Clearly stated!
And true too!

[quote=mjpoetic]Ok, you got me there.  **Howtos** don't always work.  Then again, if they always did...people may not learn how to do things on their own.[/quote]

I hope you are NOT proposing to create HowTos which give users wrong directions, so that they can't do easily what they want _unless_ they become _true_ pros on the thing they are trying to put to work...
Cause in this case, I disagree totally!!!
We don't want the HowTo directions to be tricky & wrong, just to get the users more educated here...
**Are the users trying to solve a HowTo puzzle/riddle or is the HowTo suppose to provide a step-by-step method to make their PCs work the easiest possible way?**

> Again, it's all you're choice what you want to do with your PC.
As long as Windows isn't the choice ;) ...just kidding.

Well. if Windows were designed better, with no viruses & stuff, I wouldn't mind using them...
But even with a WindowsXP SP2 & all updates installed, bundled with subscription to an Antivirus Software & me keeping getting viruses, I am sorry, but:

**I hate Windows**, and
**I will be biased towards Linux as long as they are safer!!!**

Does this make you feel better? :)
I have nothing against Windows, but it is just that Windows is NOT safe for _anybody_ to use...
Powerful statement but True!!!
I always have troubles with it...
OS wise - not Program-wise.
However in Linux we have a fantastic OS, but the rest of the programs are primitive (& many non functional)...
So, supporting Linux is one thing!
But whether I will support Ubuntu Linux or Suse Linux or whatever else Linux depends on who is going to create the best Linux overall...

Thanks.

---

### Post by dvarsam on 2006-12-12
Hello & thanks for your reply!

[QUOTE=mjpoetic]Now here's my rant response.[/quote]

What does the word "rant" mean?

> Believe it or not...I live in the United States and in South Florida at that (*cough* **GO HEAT!** *cough*) AND there are people still on dial up.

I believe you!
Hopefully if the Bush administration had tried to focus more on providing better services to his people, things would be much better for the American people...
Instead the Bush administration only cares on how to produce more weapons & throw them on somebody else's heads...:)

> Are *you *serious man?  How can you draw that conclusion?  Seriously, how?  I am not loyal to any software.
I am loyal to the ideas that Ubuntu promotes (i.e., "Linux for Human beings").

Ok, no hard feelings then!
But let us all admit, that  we "see" many biased posts in these forums too!
So, it seems that you have straightened things out now!

> So if something else better for me came along, I would hop on that (as a matter of fact, I installed the new Suse just to see if it was better for my desktop PC).

Honest & True!
I haven't done this yet, as it takes forever to download...

> I was just trying to say that these forums are the best.  Hands down!!

Clearly stated!
And true too!

[quote=mjpoetic]Ok, you got me there.  **Howtos** don't always work.  Then again, if they always did...people may not learn how to do things on their own.[/quote]

I hope you are NOT proposing to create HowTos which give users wrong directions, so that they can't do easily what they want _unless_ they become _true_ pros on the thing they are trying to put to work...
Cause in this case, I disagree totally!!!
We don't want the HowTo directions to be tricky & wrong, just to get the users more educated here...
**Are the users trying to solve a HowTo puzzle/riddle or is the HowTo suppose to provide a step-by-step method to make their PCs work the easiest possible way?**

> Again, it's all you're choice what you want to do with your PC.
As long as Windows isn't the choice ;) ...just kidding.

Well. if Windows were designed better, with no viruses & stuff, I wouldn't mind using them...
But even with a WindowsXP SP2 & all updates installed, bundled with subscription to an Antivirus Software & me keeping getting viruses, I am sorry, but:

**I hate Windows**, and
**I will be biased towards Linux as long as they are safer!!!**

Does this make you feel better? :)
I have nothing against Windows, but it is just that Windows is NOT safe for _anybody_ to use...
Powerful statement but True!!!
I always have troubles with it...
OS wise - not Program-wise.
However in Linux we have a fantastic OS, but the rest of the programs are primitive (& many non functional)...
So, supporting Linux is one thing!
But whether I will support Ubuntu Linux or Suse Linux or whatever else Linux depends on who is going to create the best Linux overall...

Thanks.

---

### Post by seijuro on 2006-12-12
Anyone who doesn't type with two fingers knows that the command line is much better than point and click for many(obviously not all) tasks this is why any distro worth its salt will never have everything guied. Case and point how many times can you open a terminal and type sudo aptitude install xxxx before someone can point and click open synaptic then point and click their way to the package then point and click to install?

---

### Post by dvarsam on 2006-12-12
Hello!

[QUOTE=seijuro]Anyone who doesn't type with two fingers knows that the command line is much better than point and click for many(obviously not all) tasks this is why any distro worth its salt will never have everything GUIed. 

Case & point how many times can you open a terminal and type sudo aptitude install xxxx before someone can point and click open synaptic then point and click their way to the package then point and click to install?[/QUOTE]

I guess that the Terminal is always better, when doing in from the GUI does not work...

_Example_:

1. Try to create a Folder Share from the Menu (e.g. by using "System\Administration\Shared Folders")

2. Then, using the Terminal, locate the file where the Shared Folders "line" is listed, change it from line 3 to line 15 & also change the Shared Folder (e.g. from Terminal: change the Shared Folder from "\home\dimitris" to \home\dimitris\Desktop"), save changes, & then,

3. Try to remove the Folder Share from the Menu (e.g. by using "System\Administration\Shared Folders")...

IF you manage to successfully remove a Shared Folder this way, I will owe you a bottle of Shampagne!!!

**IS this the reason why using a Terminal is better?**

Because the GUI doesn't work?
If this is why, then HANDS DOWN - you win!

Thanks.

---

### Post by BarfBag on 2006-12-12
The people I've introduced to Ubuntu have found the terminal interesting.  As long as I walk them through it (sending commands through Gaim), they don't mind at all.

I think there should be more frontends for newbies.  You guys ever seen the Mepis OS Center?  It's amazing!  With a click of a button, you can do things like reinstall grub, repair xorg, install your graphics driver, etc.  They should take inspiration from that.

But for me - long live command line!

---

### Post by aysiu on 2006-12-12
Maybe I should say this for the hundredth time.

The command-line is a type of tool. The graphical user interface is another type of tool. If you want to liken it to real life, it's like the difference between speaking and gesturing. Sometimes in life, you can convey things a lot more efficiently with a gesture (the nod of your head, the sticking up of a finger, a simple smile). Other times, you can convey things more efficiently with spoken or written language ("I'd like to order the mushroom and cheese omelette with Swiss cheese and wheat toast. Can I substitute in mashed potatoes for the home fries?").

You would be hardpressed to go through life gesturing entirely (unless, of course, you were deaf, but even then you have to learn sign language, which is just as complex as spoken language--it's just not audible). Likewise, your life would be extremely boring if you had to talk all the time or write all the time--you might as well be paralyzed from the neck down!

So ideally, you'd have both.

Most people can both speak and gesture. So most people on computers should be able to use commands and mouse points and clicks. If every task had both options available, you could pick and choose which you'd like to use. Then everybody would be happy.

Read more here:
[Why I think the command-line is user-friendly...](http://ubuntuforums.org/showthread.php?t=59334&highlight=command-line+user-friendly)

---

### Post by wrycatcher on 2006-12-12
> **aysiu said:**
> If you want to liken it to real life, it's like the difference between speaking and gesturing. 

I have to agree with you 100%, they are two different ways of accomplishing the same end goals.  Can I offer up a second analogy?

The relationship between command-line and GUI application is similar to the relationship between assembly language and C.  Yes, we can write *assembly* code, and while powerful and complete in what it can do, it's also more machine-like and less human-like.  C is built basically to sit *on top of* assembly.  It provides us a different way to speak to communicate to the computer, even though it still results in assembly code.

So there you go, two layered ways of speaking.  Both will accomplish the same thing, but sometimes using assembly to do a simple program is quicker and more efficient.  If the program is larger or more complex (or the user is not familiar with assembly), then C becomes a tool by which the assembler code is an invisible intermediate product.

Does this sound about right?

---

### Post by coder_ on 2006-12-12
No!  The terminal is GOOD!

---

### Post by tbroderick on 2006-12-12
> **coder_ said:**
> No!  The terminal is GOOD!


I concur. If anything, it's too dependent on X. There should be more ncurses or dialog GUI's.

---

### Post by jdhore on 2006-12-12
i honestly think GUI and CLI have their places...my dad (a noob) who runs Ubuntu would never install apps via "apt-get install thunderbird", he'd use Synaptic...i find the CLI a lot easier for some stuff...but there was a time (no less than 5 years ago) where i was almost afraid of CLI...but now i embrace it and i do a lot of stuff in it

---

### Post by rocknrolf77 on 2006-12-14
> **dvarsam said:**
> 

True!
Ubuntu Forums are the best Linux Forums out there!
It might be also considered even as the best Forums out there!
... cause I haven't seen any Windows Forums out there...
I really wonder: Are there any Windows Forums out there as good as this one?


Here is a nice forum/help site for windows users. (The name of the site, suits windows perfectly) :) [http://www.annoyances.org/]("http://www.annoyances.org/") :D

---

### Post by buuntuu! on 2006-12-18
hello everybody!
i am into linux only for a few weeks now and have not worked a lot up to now, but a friend of mine is a crack, so i've seen how work is done with the command line. i am absolutely convinced that newbs like me need to get to grips with the cli.here's why:

1. yes, the command line is INTIMIDATING, but
2. just like a good horror movie, it frightens but FASCINATES as well! it is wonderful to type a command and see what you are doing rather than clicking your index finger off!
3. you get to understand your OS as you look "behind the scenes" of the gui
4. the gui forces you into a certain path and if you encounter problems you have no cue how to solve them. just take a look at all the forums: "ti can't find the button that does this and that" is quite common a question!

so, as a newbie i hope to see more cli- guides out there!
by the way, anybody got any links to basic command line howto's?:rolleyes: 

regards
buuntuu!

---

### Post by Patrick-Ruff on 2006-12-18
> **poofyhairguy said:**
> Here is the official Ubuntu page that relates to this:

[http://udu.wiki.ubuntu.com/GraphicalConfigTools?highlight=%28MediumPriority%29](http://udu.wiki.ubuntu.com/GraphicalConfigTools?highlight=%28MediumPriority%29)

Makes me mad an ndiswrapper tool isn't even considered.

If there is anyone out there who wants to help Ubuntu and can program in some python....this is the way to go.

I'm learning C now, but I'm pretty sure either C++ or Python are next. so you may see my face in the future programming a bunch of programs for ubuntu. however, I favor the command line moreso then the GUI. but if it's going to have a GUI, it's going to be damn functional, I hate unusable GUI's . . . worst thing ever.

---

### Post by sweemeng on 2006-12-18
if the xserver is down for some reason, such as a botched upgrade

CLI is the only thing you can depends on

---

### Post by aysiu on 2006-12-18
> **sweemeng said:**
> if the xserver is down for some reason, such as a botched upgrade

CLI is the only thing you can depends on
Presumably Feisty Fawn is going to implement something called "Bulletproof X," so that that will never happen again.

---

### Post by misha680 on 2006-12-23
What I've noticed about the terminal vs GUI is that for a lot of things there already _is_ a GUI way of doing it, but on the forums and HOWTOs it is usually the command-line way that is listed. I think that perhaps is the _power_ of the command line, as it is very easy to transmit the information, but maybe we should have more "point and click" resources for people to do things (for example, even in Dapper, you _never_ have to edit sources.list to add repos if you don't want to, or installing packages can always be done through Synaptic, but people always put the command-line way, although I think it is definitely easier to get across).

Anyway, just my two cents, as it took me a while to figure out some of the things can be done graphically that I was doing through the command line. Also GNOME just has so many different things everywhere that it's kind of overwhelming at first to figure out where graphical things are (I remmeber it took me forever to figure out when there is a dropdown with folders listed that the little icon next to it would let you select folders that weren't in the dropdown, or am I getting confused with Mac OS now...)

Misha

---

### Post by dbbolton on 2006-12-23
i can't blieve this thread is still going. maybe it is ...

---

### Post by richieboy on 2006-12-28
i just found this post searching for vim info.  i'm a newbie and i freaking LOVE the cli.  i even set my computer up to boot into the command line.  i hope ubuntu developers never get rid of it.  i don't even play gui games anymore; i'm hooked on hack (it's part of the bsd games package).  these are just my two cents.
rich

---

### Post by kd7swh on 2007-01-05
I think the terminal is very important. Most of the applications that I use have GUI(s) but sometimes I don't use them because it is faster not to. On the other hand, I have some apps that I would love to see GUI(s) for. 

I think it would be a good move to cut down on the dependencies that programs have for X and give users more options when it comes to user interfacing.  People who are new to linux like GUI(s), but I think everyone should learn bash. :)

---

### Post by maddog39 on 2007-01-05
I certainly dont think its too dependent on the terminal, compared to alot of other distros. Although I think that it also really needs alot mor GUI's and or improvements to the current GUI implementations for all those noobs out there, trying to get away from windows. :)

---

### Post by Sef on 2007-01-06
Oops.  Posted in wrong place.

---

### Post by Sef on 2007-01-06
> What does the word "rant" mean?

From [Dictionary.com]("http://dictionary.reference.com/search?q=rant")

1. a loud bombastic declamation expressed with strong emotion [syn: harangue]
2. pompous or pretentious talk or writing

---

### Post by Fnordle on 2007-01-06
The problem is everything is easy when you know how.  The great thing about a good GUI is you do not need to read HOWTO's and Docs to know how, you can figure it out from the information presented.  There is no possible way you can 'figure things out' in a CLI, you need to read/learn everything.  If someone doesn't know about | more, alien, mount, mkdir or any of the other myriad of commands then they are not going to be able to figure them out.

A good GUI allows people to use a computer without learning a large amount of prerequisite information.  The key feature of a GUI is it can be intuitive, you can sit down and get started right away.  With a CLI you need to grasp the whole concept and know the majority of the commands before you can be useful.  The whole point of a GUI is to make things easier for users - if this wasn't the case everyone whould still be on CLI's.

The reason the CLI is 'easier' in a lot of cases is because the GUI is so badly made, not because it's an inherently better way of doing things!

---

### Post by wersdaluv on 2007-01-06
Personally, as a newb, I don't find the command-line user-friendly. It's hard for me to do stuff without knowing the philosophy behind and for me, it's hard to memorize stuff. I don't know what those codes mean so for me, they don't make sense and that's what makes it hard to memorize. Also, it's hard for me to improvise the codes I need to enter because I just copied and pasted codes without knowing what they stand for. There may be guides but it's hard for me to understand. I'm not good at reading stuff for a long time so it's hard for me to comprehend instructions in text on how I can use the command-line.

Maybe, what we newbies need is a "Navigating the Terminal" movie/screencasts which tells it all about the command-line from the most basic tasks to the hardest tasks. I went to ubuntuclips.org and it's nice but there are still many things missing.

---

### Post by Solver on 2007-01-06
Great original post.

The ease of command-line can not be underestimated when providing support. I often help people with their PCs (Windows, since that's what they use). I always hate it when someone calls me and requires phone support. The problem is, the vast majority of users can't explain what's going on - the ones who can are usually competent enough to fix many problems themselves.

Over the phone, you hear something to the extent of "Uh... there's this box... I see icons. File. Extract. What do I press?" It takes a long time just to understand what the user is trying to do and what's on his screen. Then, of course, to give detailed instructions, you have to remember exactly what the program looks like, or have it immediately available. That ticks me off to no end. With a command-line, support IS easier - you can simply tell the user what to type, and the user can read you the output.

---

### Post by Mr. Picklesworth on 2007-01-06
Solver: You think that's bad, try "The hourglass doesn't appear!" :(

Today's GUIs have a few problems that make stuff difficult for casual users and for the people that help said casual users. For some reason they have gone by practically unnoticed, but they are glaring errors in ease of use.

-Window titles don't seem to work. There are some users who notice them, but as Solver said, some people describe problems based on a few buttons and when you ask them what program they are running they're confused. This is probably because they rarely launch programs themselves; they open automatically from the file manager based on file associations.
This means: They do not know what the file manager is called, or even that it is a file manager (I have to describe it as My Computer, which sucks).
There are a select few, like the word processor and the web browser, and that makes sense. I launch most stuff other than that from the file manager, too.
The idea here, I think, is that certain users don't understand that Files come in many different shapes and sizes. Some are Zipped and have to be unzipped, some are videos and some are text files. They just see the program being opened to view the file as a single program (the operating system) showing the file. Makes sense, but it means they don't associate anything.

-Window menus don't work. The number of people that are ignorant of the Options window in practically every program existent is very depressing. Same goes for Help, which folks seem to ignore on the believe that Help is not helpful (even though, for the most part, it is!). In fact, my experience with buffoons using computers has told me that they only recognize the File menu, and then only Save. Not very useful, as that then has them unaware of where things are and seemingly unwilling to find out.
This is rare, but it does happen; it seems that the user needs to be SHOWN the menu by another human before they can see it.

-Tabs suffer the same as menus, sadly. Get your granny to use a tabbed web browser. Does she use tabs? Does she *see* tabs? I've noticed a horrifying trend, where people actually do not notice them and when they see a browser with 100 tabs open they still only believe that there is a single page being viewed.

-Start pages, pop-up message boxes, warnings... If that person who does not see the tabs in Firefox was to actually read the start page which has a very nice arrow cleverly pointing at A TAB, he would know about the existence of them. It doesn't happen; the start page is ignored, because it is scary documentation. (After all, one's native language is so much more scary than an unknown computer program).
Message boxes / warnings. I recently encountered this one (in Windows, but it could be Ubuntu), where the default mail program had changed to Outlook. (This actually put me over the edge and got everything switched from "Outlook Express - Stone Age Edition" to Thunderbird). Upon opening Outlook, its helpful first run "Hi, welcome. Do you want to import your old data from Outlook Express?" wizard was too much for them. They wanted to use the old mail program (Outlook Express). The solution was to try opening "EMail" *again*, but this time with the thought in their mind to "OPEN THE OLD ONE". Unfortunately, computers don't read minds - even if you try 10, 20 times; They just don't. This is all with a bunch of instances of the wizard already visible, mind you. I've never seen these people multitasking before, so I was quite pleased until I realized...
They were finally trying to stop the wizard by hitting Cancel. When they hit cancel, a message box came up which says, in summary, "Are you sure you want to cancel?". They, of course, didn't think to read this message and thus pressed "No", returning them to the wizard. They then decided to get my help under the claim that "The stupid thing won't go away!". I open it, read the message, and hit YES, and it goes away. (20 more to go).
The same thing happens everywhere; people consider message boxes / alert boxes to be annoyances, so they either do not read them or only read their titles and the options given.

-Tooltips? Toolbars rely on either amazing artwork or people realizing tooltips. There seem very few people who recognize these things as a common GUI convention.


Okay, so that kind of sucks...

We can't just have a big glowing border around important things like /READ THIS MESSAGE/, but something needs to be done so that file management is either more transparent (for example, no big archive GUI; just have GNOME say "this is an archive. Do you want me to extract it?") or so that every program's true identity is made as clear as day.
A very big first-run help program needs to be devised which can teach people these things, like what window titles are and the act of reading help files. (As soon as someone dares to do it once, they'll learn that it's not actually that bad).

Hm... Search in menus? What if Gnome put an little search box beside every window menu and toolbar, so you could search for menu items? That would be helpful, because then instead of guiding people through convoluted menus you could just tell them to type Options in the box. (And hit Enter; yes, Enter).



So yah, I see where people are coming from with the problems of GUIs. There is a lot of usability stuff being ignored here!
GUIs are more like Find Waldo than actual user interfaces, and that needs to be addressed.
GUIs are, most of the time, terribly designed but that is not the OS's fault; it is the fault of other developers. However, I think that some changes in the window manager can really change that. Search boxes; more obvious menus; message boxes that look different, thus not being recognized as "those annoying pop-ups, it must be an advertisement!" (Maybe a timer to hit buttons on the important ones would be good?).


Anyway,
links -g FTW!

---

### Post by Jasper84 on 2007-01-12
"if you happen to know the exact name of the program you want to install, it's far easier to open a terminal and type sudo aptitude install programname"
Even if you dont know the exact name, just guess a part of the name and sudo sudo aptitude search <name part>. Can ofcourse also search the net for it. I never touch aptitude anymore since i knew this.
sudo apt-get install is quicker then sudo aptitude install, but if an install fails, try the latter. BTW too bad sudo apt-get search doesnt exist, which seems like a potential source of confusion.
I like Ubuntu (Linux) a lot better then windows, in part because of the command line.

---

### Post by msimon1960 on 2007-01-15
I disagree 110% with the pro commandline arguement.

In fact I'd go so far to say that the single greatest concept keeping Ubuntu from greatness is the existence of the command line.

If you really wanted to sharpen Ubuntu up -- I mean really create a stable, robust OS the next step would be to eliminate the command line.  Sacriledge you say!

1. Complaints about GUI's are complaints about bad GUI's.  Look at SAMBA gnome vs. SAMBA KDE as known in 6.10.  Big difference in useabilty (neither works of course but Edgy KDE is at least logically laid out.

2. The documentation for any modern OS is encyclopedic.  It's not reasonable to expect more than a fanatic few to actually know how all the pieces fit together.

3. It's intellectually lazy -- got a problem? -- slap on a back door fix!  Good for you but a slap in the face to every other user.  I'd go so far to say that it is anti-community and contrary to the philosophy of Ubuntu.  Chop the command line and the GUI's in Ubuntu would improve exponentially.

Just a counter argument from someone who started out with a Sinclair and has laid hands on nearly every PC platform since then.

Matt.

---

### Post by Sean Heron on 2007-02-03
Quote: Or they forget to capitalize the X11 in /etc/X11/xorg.conf.

Thank you, thank, you, thats why I couldn´t open it! I am falling to my knees in front of you :D.

---

### Post by runningwithscissors on 2007-02-03
> **msimon1960 said:**
> I disagree 110% with the pro commandline arguement.

In fact I'd go so far to say that the single greatest concept keeping Ubuntu from greatness is the existence of the command line.

If you really wanted to sharpen Ubuntu up -- I mean really create a stable, robust OS the next step would be to eliminate the command line.  Sacriledge you say!

Sacrilege indeed. Ubuntu may do as it pleases. I can safely say that the command line is here to stay with Linux. Or any sane OS, for that matter.

> **msimon1960 said:**
> 2. The documentation for any modern OS is encyclopedic.  It's not reasonable to expect more than a fanatic few to actually know how all the pieces fit together.
And you don't need to know how the pieces fit together. You only need to know what to type or what to click on.

> **msimon1960 said:**
> 3. It's intellectually lazy -- got a problem? -- slap on a back door fix!  Good for you but a slap in the face to every other user.
Eh? What do back door fixes have to do with command line tools?

> **msimon1960 said:**
> I'd go so far to say that it is anti-community and contrary to the philosophy of Ubuntu.  Chop the command line and the GUI's in Ubuntu would improve exponentially.
In fact it would be more generous to include both graphical interfaces _and_ text-based tools. ;)

> Just a counter argument from someone who started out with a Sinclair and has laid hands on nearly every PC platform since then.
Well, maybe then you should have tried command line tools on them a bit more. Their usefulness is undeniable.

---

### Post by Rui Pais on 2007-02-03
> **Jasper84 said:**
> "if you happen to know the exact name of the program you want to install, it's far easier to open a terminal and type sudo aptitude install programname"
Even if you dont know the exact name, just guess a part of the name and sudo sudo aptitude search <name part>. Can ofcourse also search the net for it. I never touch aptitude anymore since i knew this.
sudo apt-get install is quicker then sudo aptitude install, but if an install fails, try the latter. BTW too bad sudo apt-get search doesnt exist, which seems like a potential source of confusion.
I like Ubuntu (Linux) a lot better then windows, in part because of the command line.

in fact if you know only a small hint of the name of what you want to install you don't need to do a search first. 
Simply type:
sudo apt-get install <first_letters_of_app_name>+[TAB] 
or 
sudo aptitude install <first_letters_of_app_name>+[TAB]

bash completion will complete the name or list the availables for for the letters you give.

it's even simpler. :)

---

### Post by awakatanka on 2007-02-03
CLI is powerfull tool but not userfriendly for new people.

On the internet its indeed easy to copy paste a command but the user still didn't learn anything, He have to learn zillions of commands and syntax. People easly remember a point click thing, but forget commands very fast if you have zillions of commands.

Try to work on a phone costumer supportdesk, try to tell people to type a command you have to spell every letter and still the type it wrong. Try to explain it in a point and click manner and it almost always goes in the rightway. Even if the command is faster the point and click way is much faster on a phone.

If i put my girl behind the cli and ask here to download something from a site she  can't do it then.  If i put here behind a OS gui she doesn't know see will find the browser to download that file.

Learning X number of commands isn't userfriendly.

---

### Post by Adamant1988 on 2007-02-03
A command line with cut-paste options, easily copiable text, and so forth would be tech-supports DREAM, and allow for quick and easy fixes to problems. 
Scenario 1:
User: "My graphics are screwing up on games"
Tech Supportguy: Ok, now try to get to your control panel, then find your graphics options, and look for this button, make sure that's checked..." 

Scenario 2:
User: "My graphics aren't displaying games right"
Techsupportguy: "Ok, open your Console (or command line) and type this *insert code here* 
User: Ok, this is what I got from that *copy and paste*
Techsupportguy: "Great, just copy and paste this into your command line and things should be working for you "*code*"


I'll take door #2 Bob.

---

### Post by aysiu on 2007-02-03
> **awakatanka said:**
> 
Try to work on a phone costumer supportdesk, try to tell people to type a command you have to spell every letter and still the type it wrong. Try to explain it in a point and click manner and it almost always goes in the rightway. Even if the command is faster the point and click way is much faster on a phone. Uh, having done a form of phone support before, I can say this is absolutely untrue. Trying to describe what to click on and having the person on the other end try to describe what appears next is like some Woody Allen version of abstract art criticism. It's very painful.

In almost all cases, phone support and online support are better done with commands.

Here's a very simple scenario: you're trying to troubleshoot for a Windows user and want a screenshot emailed to you. You ask the person to press Alt-PrtScrn. Then you want her to paste it into an MS Paint document and save that.

**Scenario 1**:
Can you click the Start Menu?
What's the Start Menu?
It's that thing in the lower left-hand corner. It's probably a green button. It says *Start* in white.
Oh, that one.
Yes. Then go to *All Programs*.
*All Programs*... let me see. Okay.
Then go to *Accessories*
Where's *Accessories*?
It's probably at the top somewhere.
There are a lot of things here. The menu opened up about three times.
Well, it may be in alphabetical order, so try to look on the first part of the menu at the top somewhere.
Oh, I found it.
When you click on *Accessories*, do you see something like *Paint* or *Microsoft Paint*?
No.
You don't?
No.
Hm.
Well, maybe we can find it somewhere in C:\ It really should be there unless you accidentally deleted the shortcut somehow.
What's C:\? What's a shortcut?
...

**Scenario 2**
Hold down the Windows key and press R
What's the Windows key?
It's two keys to the left of your space bar.
Okay. I Pressed it.
Hold it down and press R at the same time. Then let go of both keys. A little dialogue box should appear.
Okay.
In that dialogue box, type m s p a i n t
m s p a i n t
Yes, it's basically m s and then the word *paint*
Okay.
Then press Enter

See how much easier the second scenario was? I've done this in real life because I work in a place that has two campuses, and I've actually tried to walk people (over the phone)  through doing things in Windows on the other part of our office. I've always found it faster and easier to do things with the Run dialogue, typing, and keyboard shortcuts than to try to click navigate through things.

Another example: We have a shared file server where anyone in our office can dump stuff to edit and share with one another. One person in our office lost her shortcut to it and had trouble finding it again. She had written down steps to finding it--something about going to My Network Places and then clicking on some icon. Problem was the icon wasn't there. She was really frustrated because the person on the other end kept insisting the icon would be there, and she just couldn't find the icon. So what made the difference? I found out the IP address of the file server and asked her to type two backslashes and then a bunch of numbers. There was the file server.

Typing is more straightforward for **support** than pointing and clicking. Pointing and clicking may be more straightforward for use when you're alone (as you can discover things), but if someone else is supporting you, it suddenly becomes an electronic game of charades to try and do something simple. Why play charades when you can just cheat and tell someone what to type?

---

### Post by awakatanka on 2007-02-03
> **aysiu said:**
> Uh, having done a form of phone support before, I can say this is absolutely untrue. Trying to describe what to click on and having the person on the other end try to describe what appears next is like some Woody Allen version of abstract art criticism. It's very painful.

In almost all cases, phone support and online support are better done with commands.

Here's a very simple scenario: you're trying to troubleshoot for a Windows user and want a screenshot emailed to you. You ask the person to press Alt-PrtScrn. Then you want her to paste it into an MS Paint document and save that.

**Scenario 1**:
Can you click the Start Menu?
What's the Start Menu?
It's that thing in the lower left-hand corner. It's probably a green button. It says *Start* in white.
Oh, that one.
Yes. Then go to *All Programs*.
*All Programs*... let me see. Okay.
Then go to *Accessories*
Where's *Accessories*?
It's probably at the top somewhere.
There are a lot of things here. The menu opened up about three times.
Well, it may be in alphabetical order, so try to look on the first part of the menu at the top somewhere.
Oh, I found it.
When you click on *Accessories*, do you see something like *Paint* or *Microsoft Paint*?
No.
You don't?
No.
Hm.
Well, maybe we can find it somewhere in C:\ It really should be there unless you accidentally deleted the shortcut somehow.
What's C:\? What's a shortcut?
...

**Scenario 2**
Hold down the Windows key and press R
What's the Windows key?
It's two keys to the left of your space bar.
Okay. I Pressed it.
Hold it down and press R at the same time. Then let go of both keys. A little dialogue box should appear.
Okay.
In that dialogue box, type m s p a i n t
m s p a i n t
Yes, it's basically m s and then the word *paint*
Okay.
Then press Enter

See how much easier the second scenario was? I've done this in real life because I work in a place that has two campuses, and I've actually tried to walk people (over the phone)  through doing things in Windows on the other part of our office. I've always found it faster and easier to do things with the Run dialogue, typing, and keyboard shortcuts than to try to click navigate through things.

Another example: We have a shared file server where anyone in our office can dump stuff to edit and share with one another. One person in our office lost her shortcut to it and had trouble finding it again. She had written down steps to finding it--something about going to My Network Places and then clicking on some icon. Problem was the icon wasn't there. She was really frustrated because the person on the other end kept insisting the icon would be there, and she just couldn't find the icon. So what made the difference? I found out the IP address of the file server and asked her to type two backslashes and then a bunch of numbers. There was the file server.

Typing is more straightforward for **support** than pointing and clicking. Pointing and clicking may be more straightforward for use when you're alone (as you can discover things), but if someone else is supporting you, it suddenly becomes an electronic game of charades to try and do something simple. Why play charades when you can just cheat and tell someone what to type? Doing phone support atm in my spare time and with users that working already with windows i don't have the same experience as you have.  Before i have told a person to type ncpa.cpl i have already pointed him to networking. Some persons its easier to let them type and other persons its easier to point and click. If you have to do support for linux you have to tell them to **sudo apt-get install prgname** And the experience i have in the phone support its easier to let them point click in adept. Got persons from 20 to 80+ on the phone and with the older people its realy much easier to point click. But 1st of all you have to know what kind of person you got on the phone. 

But different people different experiences.


Btw email a screenshot is simple to explain prntscreen and open email prg and ctrl-v our right click paste in windows

Edit: Working for DSL provider company only supporting windows.

---

### Post by aysiu on 2007-02-03
You're absolutely right. It depends on the user. People who aren't comfortable typing or who are prone to typos will have difficulty with commands.

That said, I wasn't able to do the Control-V into an email. Is that an Outlook thing? We use Thunderbird at work. Out tech department won't let us use Outlook.

---

### Post by awakatanka on 2007-02-03
> **aysiu said:**
> You're absolutely right. It depends on the user. People who aren't comfortable typing or who are prone to typos will have difficulty with commands.

That said, I wasn't able to do the Control-V into an email. Is that an Outlook thing? We use Thunderbird at work. Out tech department won't let us use Outlook.
Its indeed an outlook thing.  Thats also the negative side from the place where i do support we only support MS things every other prg the user uses doesn't get support.

I'm also doing much CLI things in linux, but in the beginning i was confused and called all kind of names to my pc because i didn't understand the commands ( still do sometimes, because there so many commands ). In windows i use also  commands more now. GUI only OS will not work you need CLI sometimes to recover the stupid mistakes.

---

### Post by Gerard Barberi on 2007-02-03
The Control-V does work in Thunderbird; I've used it before.  And I definitely agree that it is sometimes a lot easier to use shortcut keys and commands when troubleshooting over the phone.  Usually I start with the graphical way, but as soon as I get some confused responses I go to the keyboard.  Course, also when I do it the graphical way, I have to be sitting in front of windows because I have a hard time visualizing it (I'm on Ubuntu most of my PC time.  Windows is for work :) ).  

Personally, I like the command line because I don't like switching between mouse and keyboard a lot.

Mostly, I'd rather ssh to my box at home (from work, school) then remote desktop into it.  Ten times faster, much less bandwidth.

I did install NoMachine server for remote graphical if I need it.

---

### Post by aysiu on 2007-02-03
Am I missing something, then? I just tried it in Thunderbird and Windows and.. nothing.

Let me make sure I've got this straight. You press Alt-PrntScrn, open up Thunderbird, press Control-N to make a new message, and then Control-V to paste, right? If I do that, nothing pastes in. What am I missing?

---

### Post by Gerard Barberi on 2007-02-03
> **aysiu said:**
> Am I missing something, then? I just tried it in Thunderbird and Windows and.. nothing.

Let me make sure I've got this straight. You press Alt-PrntScrn, open up Thunderbird, press Control-N to make a new message, and then Control-V to paste, right? If I do that, nothing pastes in. What am I missing?

Thunderbird, Windows, Key combos... All the same.

Very Wierd.

See Attached Screenshot

EDIT:  Unless you left the cursor in the "to" field and didn't move it to the "Body" section

---

### Post by aysiu on 2007-02-03
I wonder why it's not working for me. I tried clicking into the body part, but still no go.

---

### Post by Gerard Barberi on 2007-02-03
> **aysiu said:**
> I wonder why it's not working for me. I tried clicking into the body part, but still no go.

I don't get it; there's nothing special about my Windows.

---

### Post by aysiu on 2007-02-03
> **Gerard Barberi said:**
> I don't get it; there's nothing special about my Windows.
Well, right now I'm trying it on my Windows computer at home. I'll try it at work on Monday. Maybe there's something wrong with my Windows installation...

---

### Post by aysiu on 2007-02-15
I figured out what it was.

I have my settings not to compose in HTML (I prefer plain text).

I'll keep that in mind, though, the next time I want someone else to send me a screenshot! Most people send in HTML, after all.

---

### Post by .oops on 2007-02-18
By now I've read some posts around the forum, and the solutions to the problems presented always envolve typing something in the console (is this the correct term?). My question is, can't I just double-click a file to open it like I'd do in Windows?
Thanks.

---

### Post by mcduck on 2007-02-18
it depends on what file you are talking about ;)

Anyway, people like to give command line instructions because it's much easier, and you only need to copy them to a terminal so there's no much space for errors. Also CLI instructions don't depend on what desktop you are using and how you have configured it..

---

### Post by solar george on 2007-02-18
> the solutions to the problems presented always envolve typing something in the console (is this the correct term?)

Using the console (or terminal - it doesn't matter people know what you mean you could even call it 'that text thing, you know, you type commands in it') gives a lot more flexibility in what you can do + a lot of programs give output to the terminal (this can help work out what is wrong)

> My question is, can't I just double-click a file to open it like I'd do in Windows?

Yes you can, providing that you have permissions to, say edit it (if that was what you were trying to do). If you double click on something that you aren't allowed to you will just get an error message - and you will probably end up on the terminal to get access to it.

---

### Post by .oops on 2007-02-18
Thanks **mcduck** and **solar george**! :D

---

### Post by TheWizzard on 2007-02-18
read:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

---

### Post by solar george on 2007-02-18
I would add
```
$ apt-cache search *packagename*
```
to the list of useful commands.
It will search the list of installable packages for ones that contain *packagename*

---

### Post by aysiu on 2007-02-18
You type the commands in the terminal? Save yourself some time, concentration, and room for error: **copy and paste those commands**. Don't retype them.

Since this isn't really a support thread but more of a discussion about terminal v. CLI, I've merged it with a more appropriate discussion thread in the Cafe. And, as you can see from the posts in this thread, almost all tasks **can** be accomplished via point-and-click. But on a text-based forum where users cannot look over your shoulder and say, "See that icon? Click there. Now, click that," it's a lot more efficient to say, "Copy and paste this command into the terminal."

---

### Post by peanut butter on 2007-02-18
In suse there is something called Yast that does most of those things. I wish It was ported to ubuntu.
EDIT: Gcontrol does most of this, but needs to be extended with more capabilities.

---

### Post by Raffo on 2007-02-18
I like bash and I like using terminals, but I think ubuntu depends a lot from them. Expecially for noobs, this isn't so good..

---

### Post by ssam on 2007-02-18
there is a list at
[https://wiki.ubuntu.com/UbuntuDapperWhatStillNeedsAConsole](https://wiki.ubuntu.com/UbuntuDapperWhatStillNeedsAConsole)

---

### Post by aysiu on 2007-02-18
> **ssam said:**
> there is a list at
[https://wiki.ubuntu.com/UbuntuDapperWhatStillNeedsAConsole](https://wiki.ubuntu.com/UbuntuDapperWhatStillNeedsAConsole)
Thanks for the link, but that may be a little outdated, since it's about Dapper, not Edgy.

---

### Post by picpak on 2007-02-18
> Opening a file with superuser permissions

That's a big one. Why can't Nautilus check if you're root or not, and if not, provide a password prompt to edit the file? I mean really, even something as simple as:

```

if (! ls -la $NAUTILUS_SCRIPT_CURRENT_URI | grep root > /dev/null 2>&1); then
gksudo gedit $NAUTILUS_SCRIPT_CURRENT_URI
fi

```

---

### Post by pmj on 2007-02-18
> **picpak said:**
> That's a big one. Why can't Nautilus check if you're root or not, and if not, provide a password prompt to edit the file?Maybe you just want to look at a file, why should you need to enter your password for that? And what if the user isn't supposed to be editing the file, why shouldn't he at least be able to look at it if he has the permission to do so?

No, this functionality belongs in the program that opens the file. There is no reason a text editor for example couldn't ask you for the password when you try to save the file.

---

### Post by aysiu on 2007-02-18
> **picpak said:**
> That's a big one. Why can't Nautilus check if you're root or not, and if not, provide a password prompt to edit the file? I mean really, even something as simple as:

```

if (! ls -la $NAUTILUS_SCRIPT_CURRENT_URI | grep root > /dev/null 2>&1); then
gksudo gedit $NAUTILUS_SCRIPT_CURRENT_URI
fi

```
The idea was proposed before (for Dapper, actually):
[Nautilus and gksudo](http://ubuntuforums.org/showthread.php?t=82225)

Don't know if anything ever came of it...

---

### Post by aysiu on 2007-02-18
> **pmj said:**
> Maybe you just want to look at a file, why should you need to enter your password for that? And what if the user isn't supposed to be editing the file, why shouldn't he at least be able to look at it if he has the permission to do so?

No, this functionality belongs in the program that opens the file. There is no reason a text editor for example couldn't ask you for the password when you try to save the file.
Well, how about something sensible, then? You open it as read-only, but once you start making changes and want to save, Gedit (or Kate, or whatever editing program you're using) says "This is a system file. Are you sure you want to save the changes you've made?" If you answer *yes* and are a sudoer, you get a password prompt. If you answer *no*, no changes are made.

That makes a lot more sense to new users than simply saying you can't save it because you don't have permission.

---

### Post by picpak on 2007-02-18
> **aysiu said:**
> The idea was proposed before (for Dapper, actually):
[Nautilus and gksudo](http://ubuntuforums.org/showthread.php?t=82225)

Don't know if anything ever came of it...

Ahh, manicka's solution is way more elegant than mine. Thank you.

---

### Post by Rebajas on 2007-02-25
This might have been said already but I found using the command line to do simple things at the very beginning a godsend for when I eventually wanted to do more complex stuff.

The problem with GUI interfaces is finding the particular setting to do what you want - with the CLI you know exactly where it is, all you have to do is find the right command to punch in.

R.

---

### Post by Ob1 on 2007-02-27
In what environment do you finish tasks more quickly?

---

### Post by tbroderick on 2007-02-27
What task?

---

### Post by steven8 on 2007-02-27
At the moment, GUI, since I have to do research for everything I want to do with the CLI.

---

### Post by PatrickMay16 on 2007-02-27
Depends on the task.

For my weekly backup, I wrote a simple script that does it all for me, so all I have to do myself is copy the resulting folder containing a bunch of archives onto my zip disk. So the command line got that done quicker.

But some casual file management is far more natural for me to do with a GUI.

---

### Post by slayerboy on 2007-02-27
each task I do works best in either one depending on the task.  Not sure I understand what's up with this poll?

Obviously if I have the option I'm going to go with the gui option, but cli is faster, but not necessarily the quickest in some cases.  The same as gui.

---

### Post by aysiu on 2007-02-27
> **tbroderick said:**
> What task?
Yes, it greatly depends on the task. Having eight Ubuntu Forums threads open in separate tabs for answering one after the other? GUI. Installing ten packages through the package manager? CLI.

---

### Post by IYY on 2007-02-27
I voted CLI, but obviously not for every task...

I use the CLI to...

[LIST]
[*]Edit text files, programming, HTML (vi)
[*]Create documents (LaTeX)
[*]Check my e-mail (pine)
[*]Do batch operations on media (Imagemagick, sox, lame, oggenc)
[*]Perform system administration tasks (ifconfig, dhclient, adduser)
[*]Manage files (the shell)
[*]FTP, SSH, SVN
[/LIST]

I use the GUI to...
[LIST]
[*]Work with spreadsheets and presentations (OOffice and Gnumeric)
[*]Browse the web (firefox)
[*]Listen to music (banshee, beep)
[*]Edit images (Gimp)
[*]Chat (Gaim, XChat)
[*]Watch video (VLC)
[*]Record audio (Audacity)
[*]Burn CDs (GnomeBaker)
[*]Download torrents (Azureus)
[/LIST]

So, what do I use most often? The CLI, because most of what I do is, essentially, edit text files.

---

### Post by jdhore on 2007-02-27
I Use the CLI for a lot of stuff and whenever i'm working with files or editing stuff, i use the commandline...i really only use the GUI for 5 main things: Chat, Watching video, listening to music, browsing the web or torrenting.

---

### Post by jethro10 on 2007-02-27
> **steven8 said:**
> At the moment, GUI, since I have to do research for everything I want to do with the CLI.

This is totally the point.
Unless you become a regular hacker, it always will be.
J

---

### Post by tbroderick on 2007-02-27
> **jethro10 said:**
> This is totally the point.
Unless you become a regular hacker, it always will be.
J

I don't think so. It's not that hard to learn a few things.

---

### Post by steven8 on 2007-02-27
I need to make up a cheat sheet.  I don't use the commands every day, so I tend to forget.

---

### Post by OldTimeTech on 2007-02-27
It may not be that hard to learn a few things, but seems that when I'm in trouble and come to the forums for help, it's not the gui side that is used for help it's the cli side, so that means I need to learn, memorize and retain the cli side ;)

EDIT: I don't use OldTimeTech without having a reason....called age....LOL!!!

---

### Post by red_Marvin on 2007-02-27
cli:
Resetting our network after replugging a cable. (sudo ifdown eth0 && sudo ifup eth0)
Compiling stuff.
gui:
Writing stuff? gui
Browsing the net
Graphics/photo stuff

---

### Post by Crooksey on 2007-02-27
CLI, when I first started using Linux the X window system wasnt as good as it is now, so its sort ofhabbit.

---

### Post by AndyCooll on 2007-02-27
I voted GUI. However as has been pointed out, it depends on the task and also an individuals computer use.

Since I'm from a Windoze background where I only ever used a GUI I naturally lean towards GUI use. However the more I use Linux, the more I find that certain tasks can be done quicker user a CLI.

:cool:

---

### Post by fuscia on 2007-02-27
i have to look at the keys to type, so gui for me.

---

### Post by EdThaSlayer on 2007-02-27
GUI is easier for most tasks and I use my GUI more than I use my CLI. even like to edit text file using the GUI(Gedit anyone?) and I love my IDE(Geany and IDLE anyone?).  CLI is quite useful for the "underground" stuff. :)

---

### Post by Adamant1988 on 2007-02-27
I find I'm usually finished doing what I'm doing quicker when I'm doing it from the CLI.  But that requires knowledge of commands and such, the GUI gives me the ability to "guess" so if I'm in new territory the GUI might be faster.

---

### Post by doobit on 2007-02-27
I've found that there are a few CLI things I need to know to diagnose problems, so I've learned those. Also, since I do a lot of customization, there are a few CLI programs that I use all the time, and a few scripts that I need to modify constantly (like Grub's menu.lst, and CFdisk, for examples) I also have a few favorite CLI programs that I use just because they are fast, like elmo, and the alsa mixer.

---

### Post by GrimRazer on 2007-02-27
I use both :)

---

### Post by aysiu on 2007-02-27
> **jethro10 said:**
> This is totally the point.
Unless you become a regular hacker, it always will be.
J
I'm not a hacker or a programmer, but I use the CLI on a regular basis.

---

### Post by lamalex on 2007-02-27
CLI is definitely quicker IF you know what to do. GUI is much easier and sometimes just using a gui saves time in learning how to use CLI

---

### Post by aysiu on 2007-02-27
Here's one way to sum up the issue for me:

GUI - one-time events (not worth learning a command for) and graphics-heavy tasks (that involve needing to *see* the graphics

CLI - oft-repeated events (worth learning a command for) and batch tasks involving many files.

---

### Post by Sunflower1970 on 2007-02-27
For me, mainly GUI, but as I'm learning more I do find some tasks easier using CLI.

---

### Post by manmower on 2007-02-27
Depends highly on the task as some have mentioned. Package management is certainly one of those things I prefer to do from CLI. Others include changing permissions or moving/deleting files I need to be root for (much faster to sudo than to gksudo), and editing configuration files (I find all GUI text editors slow). I also like to not have X running when installing important updates.

---

### Post by kokuo on 2007-03-08
Hello.As a new linux user , I wish to ask that why linux world still insist on using old fashion terminal and commands?  Is the graphic interface not more handy and time-saving than terminal? Especially I want to learn the the reason of this terminal addiction.

---

### Post by Bachstelze on 2007-03-08
The GUI is far less handy and far more time-consuming than the terminal for most things. And there are also thing you can do only in the terminal.

The terminal is definitely not "old-fashioned". If you don't like it, I think Linux is not for you.

---

### Post by 23meg on 2007-03-08
> old fashion terminal and commands?

May I ask, just out of curiosity, what exactly makes you think they're old fashioned?

> Is the graphic interface not more handy and time-saving than terminal?

Not necessarily; it depends on the task. With most tasks I go through, I find that the CLI is faster. Try opening 25 image files, resizing and saving them in GIMP, and then try the same with Imagemagick; It would take at least five minutes to do it with GIMP, and at most thirty seconds or so in Imagemagick.

Another example, from [linuxcommand.org]("http://linuxcommand.org"):

> Why do you need to learn the command line anyway? Well, let me tell you a story. Not long ago we had a problem where I work. There was a shared drive on one of our file servers that kept getting full. I won't mention that this legacy operating system did not support user quotas; that's another story. But the server kept getting full and stopping people from working. One of the software engineers in our company spent the day writing a C++ program that would look through the directories of all the users and add up the space they were using and make a listing of the results. Since I am forced to use the legacy OS while I am on the job, I installed a version of the bash shell that works on it. When I heard about the problem, I realized I could do all the work this engineer had done with this single line:

```
du -s * | sort -nr > $HOME/space_report.txt
```

Graphical user interfaces (GUIs) are helpful for many tasks, but they are not good for all tasks. I have long felt that most computers today do not use electricity. They instead seem to be powered by the "pumping" motion of the mouse! Computers were supposed to free us from manual labor, but how many times have you performed some task you felt sure the computer should be able to do? You ended up doing the work by tediously working the mouse. Pointing and clicking, pointing and clicking.

> Especially I want to learn the the reason of this terminal addiction.

It's a smart and fast way of working that gets the job done.

---

### Post by 23meg on 2007-03-08
[QUOTE=HymnToLife]If you don't like it, I think Linux is not for you.[/QUOTE]I disagree. You can enjoy using many recent Linux based operating systems including Ubuntu without *having to* use a command interface.

---

### Post by era86 on 2007-03-08
I wouldn't say that Linux is not for him. Rather, it can be a learning experience.

The command line is far less time consuming because of the various tools available. For example, if you LEARN the right commands, something simple as moving files can be done in one line rather than a series of clicks and drags.

It's a matter of learning and getting used to. A pretty GUI doesn't hurt, but it definitely is not more handy than the terminal (in almost all respects).

---

### Post by kokuo on 2007-03-08
> **HymnToLife said:**
> The GUI is far less handy and far more time-consuming than the terminal for most things. And there are also thing you can do only in the terminal.

The terminal is definitely not "old-fashioned". If you don't like it, I think Linux is not for you.

I havent said I didnt like terminal. I just wanna learn the logic of terminal addiction?

Could you give a specific terminal example that is fast than GUI?

---

### Post by Shatrat on 2007-03-08
Another huge advantage to using the terminal for everything is that when you need help or are giving help over IRC or forums it's much easier to tell somebody 1 line to put into the terminal as opposed to "click on edit and go to options and click the advanced tab and twist the left nipple and then save as .xyz"

---

### Post by Bachstelze on 2007-03-08
Just to copy a file. In the terminal, you do :

```
cp /path/to/source /path/to/destination
```

While in the GUI, you need to :

-> Open your file manager
-> Browse to the dir where the source file is.
-> Right-click on it and choose Copy
-> Browse to the dir where you want to copy it to
-> Right-click and choose Paste

---

### Post by kokuo on 2007-03-08
> **23meg said:**
> May I ask, just out of curiosity, what exactly makes you think they're old fashioned?


Hello. Now it is just about logic. As you know everything goes around evolution, and related to terminal and gui debate, terminal history is older than GUI , in other words the GUI evolved from terminal exprience.  Mostly new ones  replace the old ones, if they are stronger as Darwin indicated. 

If we compare GUI based windows and terminal addicted Linux , the GUI based system is stronger according the market share.  Then a question tickles my brain. Why Linux geniuses insist on terminal rather than GUI ? Do not they fear  that GUI may  knock down the terminal based operating systems in the future? Why do not they strengthen linux with GUI style if the Gui systems are more succesful according to market shares?

And so much thanks for your terminal explanations above.

---

### Post by Bachstelze on 2007-03-08
You need to understand one essential thing :

**Linux is not, does not aim to be and never will be Windows !**

---

### Post by kokuo on 2007-03-08
> **HymnToLife said:**
> You need to understand one essential thing :

**Linux is not, does not aim to be and never will be Windows !**

Why does Linux not intend to reach all people around the world to share the free software advantages? Will linux be lonely cowboy?

---

### Post by melancholeric on 2007-03-08
> **kokuo said:**
> Why does Linux not intend to reach all people around the world to share the free software advantages? Will linux be lonely cowboy?

Do you think we're selling something?

---

### Post by Bachstelze on 2007-03-08
Not exactly. Linux is a volunteer effort, meaning that the people who make Linux make it firtsly to suit *their* needs. If other people want to use it, fine. If they don't, fine also.

*But*, the people who make Linux are people who like it the way it is, not people who don't.

---

### Post by benfindlay on 2007-03-08
I agree totally with HymnToLife here!

Speaking as someone who learned to use DOS before Windows 3.1 came along, I find there are still things that you need a DOS command prompt for that Windows will not do. Admittedly also these are very rare (like safe-mode command prompt to delete a file that Windows mistakenly thinks is in use)

The fact of the matter is. Linux uses the terminal because the majority of people that have used linux in the past have been used to it. As the needs develop, the Linux community develops too. This development can be seen by the creation of programs like automatix, or the fact that ndiswrapper now has a GUI to allow configuration (ndisgtk). In years gone by, a GUI config tool would have been unheard of. Times are changing, but a volunteer run effort will take more time to evolve because of it having less money, resources etc devoted to it. The likes of Mark Shuttleworth and Canonical realise the potential of alternatives to the status quo and are thankfully doing something about it!

Anyway, I'll get off my soap box now. 

P.S. kokuo, Darwin wasn't always correct! ;)

---

### Post by Motoxrdude on 2007-03-08
> **kokuo said:**
> Hello. Now it is just about logic. As you know everything goes around evolution, and related to terminal and gui debate, terminal history is older than GUI , in other words the GUI evolved from terminal exprience.  Mostly new ones  replace the old ones, if they are stronger as Darwin indicated. 

If we compare GUI based windows and terminal addicted Linux , the GUI based system is stronger according the market share.  Then a question tickles my brain. Why Linux geniuses insist on terminal rather than GUI ? Do not they fear  that GUI may  knock down the terminal based operating systems in the future? Why do not they strengthen linux with GUI style if the Gui systems are more succesful according to market shares?

And so much thanks for your terminal explanations above.

I'm sorry, but that is one of the most retarded things i have ever heard.
Ubuntu linux comes with a GUI, gnome. Plus, you can use KDE, XFCE, Fluxbox and more. The terminal is a ton faster then a gui and is a lot more flexible. 
Do you have a preconceived notion that ubuntu doesn't come with a gui? Because if you do, it does come with a gui as shown above. 

Now that i think about it, what OS doesn't have a terminal?

---

### Post by benfindlay on 2007-03-08
Market share also means squat. Just means they had better/more advertising! ;)

---

### Post by Bachstelze on 2007-03-08
And besides, free software is not about being the best option for everyone.

If you like it, you're free to use it. If you don't like it, you're free not to use it. That's what Free Software is all about :)

---

### Post by kokuo on 2007-03-08
> **benfindlay said:**
> I agree totally with HymnToLife here!

Speaking as someone who learned to use DOS before Windows 3.1 came along, I find there are still things that you need a DOS command prompt for that Windows will not do. Admittedly also these are very rare (like safe-mode command prompt to delete a file that Windows mistakenly thinks is in use)

The fact of the matter is. Linux uses the terminal because the majority of people that have used linux in the past have been used to it. As the needs develop, the Linux community develops too. This development can be seen by the development of programs like automatix, or the fact that ndiswrapper now has a GUI to allow configuration (ndisgtk). In years gone by, a GUI config tool would have been unheard of. Times are changing, but a volunteer run effort will take more time to evolve because of it having less money, resources etc devoted to it. The likes of Mark Shuttleworth and Canonical realise the potential of alternatives to the status quo and are thankfully doing something about it!

Anyway, I'll get off my soap box now. 

P.S. kokuo, Darwin wasn't always correct! ;)

Thanks a lot. This is a good explanation. So much times repeated , I just want to learn the logic of the case. Not want to blame Linux and linux users. But somepeople shouldnt be so egoistic . This is not true ; *Do love linux or do not cristise it*. For me according to nowadays conjuncture , linux must stay on a place which is  between current Linux and current windows. 


P.S. I dont want to have a religious war here  @benfindlay.

---

### Post by r4ik on 2007-03-08
> **HymnToLife said:**
> Not exactly. Linux is a volunteer effort, meaning that the people who make Linux make it firtsly to suit *their* needs. If other people want to use it, fine. If they don't, fine also.

*But*, the people who make Linux are people who like it the way it is, not people who don't.

I hate to disagree with you but i think Linux has grown beyond that stage.

---

### Post by Bachstelze on 2007-03-08
"Linux shoud do this, Linux should do that."

Not meaning to be rude but who do you think you are to tell thousands of developpers all around the world what they should do with their OS ? Would *you* work several hours a day for free on something you don't like ?

---

### Post by benfindlay on 2007-03-08
lol @ kokuo

Thant precisely why I got off the soap box! ;) I do understand why people don't like command lines, but its just the way things are. They may change, they may not. My personal opinion is that they will eventually.

Linux is forever growing, and hopefully will for years to come. But it still has a long way to go until adulthood!

---

### Post by Bachstelze on 2007-03-08
And when that day will come, I'll certainly have quit using it for long...

---

### Post by kokuo on 2007-03-08
> **HymnToLife said:**
> "Linux shoud do this, Linux should do that."

Not meaning to be rude but who do you think you are to tell thousands of developpers all around the world what they should do with their OS ? Would *you* work several hours a day for free on something you don't like ?

According to Open Source mentality, I am one to suggest developers. Because the open source softwares are strengthened and developed by eliminating the problems with collaborative work. I just suggested something because I am free to say that if I find it useful for Open source  and developers are free to disregard if it si not logical.

---

### Post by Bachstelze on 2007-03-08
Suggestions are of course very welcome but you should word them a bit differently than "you should do this and that", if you want them to be regarded positively, and not say something is "old-fashioned" just because it is not what *you* would like to see. If it's that way and not otherwise, it's usually for a reason :)

---

### Post by annda on 2007-03-08
```
Why do not they strengthen linux with GUI style if the Gui systems are more succesful according to market shares?
```

actually, some linux distributions (like ubuntu) ARE going down that road. they sport a lot of GUI interfaces/frontends to underlying programs.

however, i believe the keyword here is not marker share, but rather market niche. (and still, market is a bit awkward, since the products supplied by the linux community are targeted at serving users' needs rather than generating income).

you could as well as the question why off movies are ever made - most people don't want to see them and find them tedious at best and boring at worst. but there is a niche constituting of people who are extremely bored with popular action-packed blockbusters. i for one am bored by both.

i agree with HymnToLife and the opponents at the same time: you can use linux because you want a free-of-charge OS and still do anything you want to (opponents), or you can use linux because you want to do anything you want PERIOD - and the command line lets you do that (HymnToLife and me, among thousands others).

bottom line: if you just want things done, get a Mac. if you want to have a wide choice of tools, some of which will get things done, get windows. if you want to tell the tools of your choice what has to be done and how exactly, get linux. if you don't need to know and control what your computer is doing - linux is not the BEST choice for you. but it can be a VERY GOOD one, still.

but this is a rant and shouldn't be here - in ubuntu cafe maybe...

ps. i think we all have examples of why the "terminal addiction" pays off. sometimes it doesn't and we go for GUI. regardless, it's great to have the option.

---

### Post by r4ik on 2007-03-08
> **HymnToLife said:**
> "Linux shoud do this, Linux should do that."

Not meaning to be rude but who do you think you are to tell thousands of developpers all around the world what they should do with their OS ? Would *you* work several hours a day for free on something you don't like ?

Now dont get snappy please i am not telling  anybody anything.
I am only hoping devs have the drive to bring things they like to a bigger public.
Answering you're second question.
Nope.

---

### Post by Bachstelze on 2007-03-08
This wasn't directed at you but at kokuo, more precisely answering this :

> **kokuo said:**
> linux must stay on a place which is  between current Linux and current windows. 

---

### Post by r4ik on 2007-03-08
Oke i am out :)
Sorry.

---

### Post by taurus on 2007-03-08
Okay, I think this thread should go to Cafe now.

p.s.  Always terminal, baby...  ;)

---

### Post by igknighted on 2007-03-08
> **kokuo said:**
> Hello.As a new linux user , I wish to ask that why linux world still insist on using old fashion terminal and commands?  Is the graphic interface not more handy and time-saving than terminal? Especially I want to learn the the reason of this terminal addiction.

The terminal is high-tech, direct access to your computer.  This ability to get as close to the computer as possible is one of linux's biggest features.  It is different, and almost never necessary, but to have the option to use it is very powerful.  Most help you will get here will have the terminal way, as out of 10 computers each could have a different GUI to do the same task, while the CLI is always the same.  Also, copy/paste help for the terminal is very easy, while "click here, then there, nono, the other one" is very cumbersome.  You don't need to love the CLI to be a linux user, but if you avoid it at all costs you will miss out on part of what makes linux great.

---

### Post by ssam on 2007-03-08
the number of tasks on Ubuntu that require the CLI is dropping every release.

right now i think on a lot hardware you could install and run ubuntu with ever using the command line. unfortunatly most tutorial and howto writers show people a CLI method even when there is a perfectly good GUI method.

telling someone to do
```
sudo apt-get install inkscape
```
is quick and easy. but they will just come back tomorrow and ask you how to install something else.

if you told them to go to
Applications -> Add/Remove
and to search for 'vector graphics'
then they would be self sufficient.

i agree that the CLI is quick and precise, but you need to know exactly what you want to do.

Today I was copying tens gigabytes of data between several computers, a remote server, a workstation i was sat infront of, and a nearby raid server. having curl/wget, ssh/scp, rsync, etc were very useful, but this is not a typical user set up.

---

### Post by hizaguchi on 2007-03-08
A GUI will never be as fast or convenient as a terminal.  It's that simple.  This is because if you ever did make a GUI with all the power and capabilities of the command line, you'd need pages and pages of buttons and menus to do it all, and then you'd spend all day sifting through it looking for the right button.  So a GUI necessarily makes compromises for the sake of new user friendliness.  It sacrifices features and flexibility to become more manageable.  And that may be fine for new users who don't understand all that they're losing with a GUI, but fortunately they are not the ones who get to make the decisions about the future of open source software.  Open source software is developer, not market or new user, driven.  The terminal isn't going anywhere until we can just control the computer with our minds... and even that will work the same way because it'll probably require you to know the command you need to think to get what you want done.

Oh yeah, and have you ever used graphical applications remotely, through ssh?  The network at work gets so bogged down sometimes that even the command line is laggy.  If I had to do everything with a graphical tool, I'd actually have to go in to work! :shock:

---

### Post by 23meg on 2007-03-08
> **kokuo]Hello. Now it is just about logic. As you know everything goes around evolution, and related to terminal and gui debate, terminal history is older than GUI , in other words the GUI evolved from terminal exprience. Mostly new ones replace the old ones, if they are stronger as Darwin indicated.[/QUOTE]

The wheel is older than the jet engine said:**
> If we compare GUI based windows and terminal addicted Linux , the GUI based system is stronger according the market share. 

If we compare [Britney Spears]("http://en.wikipedia.org/wiki/Britney_Spears") to [Morrissey]("http://en.wikipedia.org/wiki/Morrissey"), Britney Spears is "stronger according to market share". Does that tell us anything about which is a "better" musician? 

If you take into account the millions of CLI operated Linux/BSD/Unix based web servers that make up perhaps more than half of the internet, however, the market share argument goes down as well.

Assuming you meant *desktop* market share, you'd have to have a well reasoned argument against the Commodore 64, which had no GUI, and which seventeen million people used, almost entirely in home and small business settings. It's still the best selling personal computer of all time. People were doing just fine with their keyboards and their blinking cursors before Xerox invented the GUI; actually, afterwards as well. If anything, the GUIization of computer culture somehow led to... OK, I won't go into that.

Market share means commercial success, no more, no less. I'm sure you can come up with many commercially unsuccessful products that have commercially successful counterparts which are inferior in comparison. 

[QUOTE=kokuo]Then a question tickles my brain. Why Linux geniuses insist on terminal rather than GUI ? Do not they fear that GUI may knock down the terminal based operating systems in the future? Why do not they strengthen linux with GUI style if the Gui systems are more succesful according to market shares?
[/QUOTE]

You seem to have the following dichotomy drummed in your mind:

Linux = CLI
Windows/Mac = GUI

Get rid of that first. Take a look at what GNOME, KDE, XFCE and others have realized in the GUI domain in far less time than Windows and Mac. Talk to a professional Windows system administrator and learn what they use to set up policies across a network of a hundred computers (hint: it starts with C).

And if anyone tells you that "product X is better because it has more market share", you can instantly assume they have no idea about both what that product is, and about how the economy around it works.

---

### Post by ncappel1 on 2007-03-10
I like to use the terminal for ftp transfers. i don't know why, but it works much better for me. im constantly uploading and downloading homework files and other random stuff. Maybe it's just the computers I use that are misconfigured, but using a regular window manager for ftp frequently makes me stop to log in again, or it won't let me put files where I want because of permissions. who knows why?

on another note, I once was using the terminal to do some ftp-ing at my school library, and a really good looking girl came over to use the computer next to mine, she asked what I was doing, and i explained about the terminal (which she had probably never known existed), and the conversation led into getting a date later that evening! 
All thanks to the terminal :)

---

### Post by zorkerz on 2007-03-10
The beauty i find with ubuntu is the ability to do most things either way you desire.  The CLI is quick, efficient, and clean where the GUI is visual, and possibly if designed well more intuitive, i would argue.  Both methods have there supporters. There are many tasks that i prefer to do one way or the other. Get me if im wrong but i think there are very few people left who use no GUI for any of their computing needs or addictions.  I think if you can do things either way that increases everyones choice and for me thats where ubuntu and linux based oses in general fly ahead.  Everyone wants to do things their own way and if that is allowed its a good start.

---

### Post by Tomosaur on 2007-03-10
> **ncappel1 said:**
> 
on another note, I once was using the terminal to do some ftp-ing at my school library, and a really good looking girl came over to use the computer next to mine, she asked what I was doing, and i explained about the terminal (which she had probably never known existed), and the conversation led into getting a date later that evening! 
All thanks to the terminal :)

The Internet Police want a word with you!

---

### Post by IYY on 2007-03-10
Where does the terminal shine?

[LIST]
[*]Automated procedures: it is very difficult to automate anything using a GUI, and would required highly specialized software. Suppose you wish to convert 1000 photos from BMP to JPG, quality 50%, and make them all +5 brighter. You could find some sort of a GUI program to do such an automated task, but I guarantee that it will be more difficult than the one line solution that is ImageMagick. Similar conversions can be made between sound files, data can be automatically extracted from text files, common system administration operations can be automated. All of that is not in the realm of the GUI.

[*]Speed of finding: In the CLI, if you know a way to do something, you can do it instantly, because of the brain's fast recall mechanisms. In the GUI, you have to search for the operation every time you want to do it. In a way, it's like figuring it out from the beginning. If there are many such operations, you will have a whole lot of menus to go through! Actually, for this reason Microsoft seems to be dropping the menu system in Vista and Office 2007, and replacing it with Ribbon-like GUIs. We'll see how well that works out, but it certainly won't be anywhere near the CLI's speed.

[*]Speed of operation and stability: If you are running a server, you don't want a heavy and unstable GUI sitting on top of it. The CLI shells are rock solid, and can run on even 486 machines while still leaving enough memory and CPU power to run web servers, routers or other software. Similarly, the CLI will pretty much never crash on you.

[*]Flexibility: If you were to build a GUI that can truly do *everything* that the CLI can do, it will be so cluttered and confusing that no one will be able to use it. The CLI allows you to do more, no doubt about it.

[*]Tradition: Windows changes its GUI with every release. Apple and Ubuntu change the GUI in even more often (because there are more releases). Individual applications change their graphical functionality, locations of menus, buttons, and other controls. With the GUI, the skills you learn today will be fairly obsolete in 5 years. The CLI skills people learned while using Unix in the **70's** is still every bit as useful today! Those very same skills are useful in every distribution of Linux, in every BSD, in every Unix (like Solaris), and even in Mac OS X! In fact, they are, and forever will remain useful in every mainstream operating system other than Windows.
[/LIST]

Is it all green fields and roses? No; there are places where the GUI clearly wins. Here are some examples of the GUI's advantages:

[LIST]
[*]Speed of finding (for novices): Just like the CLI is fast for an expert or intermediate user for finding an application, the GUI is fast for a novice for the same task. When you are a beginner in a particular CLI system, it will take long to find things and learn how to do them. When I sit at a GUI system, I can always figure out where things are fairly quickly and be instantly productive. So, even though you have to relearn how to do a task every time you do it, the GUI is useful for that first time user of a task or application. This is nice when there is a task that you only want to perform once, twice, or even 15 times. 

[*]Easier multitasking: The CLI can be used to do several things at once, even if you only have a single console window, but the GUI is obviously more intuitive for this particular task. System trays, docks, task lists, windows: these are all great metaphors to keep track of multiple tasks.

[*]Visual appeal: You use the computer so often, so it's nice to have a pretty screen with an artistic wallpaper and a clean theme to look at. Of course, some find the CLI to be attractive in its own way as well.

[*]Browsing the web: You can browse the web from the CLI, but obviously no one does this on a regular basis. Browsing the web is, by its very nature, a graphical operation and calls for a GUI.

[*]Other applications: Just like browsing the web, there are things that just have to be visual. Digital drawing, 3D modeling, CAD, etc.

[*]Games: CLI games can be fun, but obviously the GUI games are better.
[/LIST]

So, what's the best option? Obviously, it is to have a system that has both a solid GUI and a fully functional CLI, so that users can use either, or both. Guess what? This is exactly what Ubuntu has.

I usually log into a GUI, but have several terminal windows open. I use them to edit text and program code files (vi is much, much, much faster than any other text editing software), create documents (LaTeX is more powerful and elegant than traditional word processors), do some image manipulation (mostly conversions, and other batch applications), sound and video conversion, moving files around, FTP and SSH, system administration, etc. However, I also usually have Firefox open, as well as programs like The Gimp, Inkscape, a GUI music player (I could use a CLI method, but I like it better this way), etc.

EDIT: now that the threads have been merged, I voted for CLI, but I think that the polarization is silly. You should use the right tool for the job, and there is a time and place for everything. The reason for my vote is simply that I enjoy the CLI more than the GUI, and find it to be underrated. It's difficult to say which I use more, because even when I use the CLI I am running it in a terminal in a window manager, so in a sense it is a GUI.

---

### Post by 23meg on 2007-03-11
[QUOTE= IYY]
So, what's the best option? Obviously, it is to have a system that has both a solid GUI and a fully functional CLI, so that users can use either, or both. Guess what? This is exactly what Ubuntu has.[/QUOTE]

I'm sadly amazed at the piety and stubbornnes of people *defending* a certain position in the "GUI vs. CLI" debates, given that we have very advanced Free versions of both (GNOME, KDE, XFCE, BASH/DASH, etc.) at our disposal, and that they can work together. Actually, them working together is one of the greatest strengths of our platform for users keen on using their computers efficiently.

Improving the interaction and ways of coexistence of the two will make things even better. Projects such as [dragbox]("http://www.student.lu.se/~cif04usv/wiki/dragbox.html") are very inspiring in this regard.

I almost always find myself choosing a third way in "this or that" dichotomies, and the third way is often "both" or "neither". The subject at hand is no exception; I use both.

---

### Post by aysiu on 2007-03-11
It's probably about time we had a megathread on the terminal and the graphical user interface. Here are a couple of polls that got lost in the merger.

Here are some quick links to my two major lines of thought on the issue:
[Why I think the command-line is user-friendly...](http://ubuntuforums.org/showthread.php?p=315402#post315402)
[Is Ubuntu really too dependent on the terminal?](http://ubuntuforums.org/showthread.php?p=1840857#post1840857)

---

### Post by SunnyRabbiera on 2007-03-11
Its different strokes for diffrent folks, personally I like GUI apps as I personally find it easier then command line apps, learning command line is very intimidating even after I spent 4 years in a linux enviroment.
but then again this is why i like distros like ubuntu as you barely have to lay a finger on a terminal.

---

### Post by karellen on 2007-03-11
I like the cli, it's fast and gives me a feeling of control and things-done-the-way-I-want

---

### Post by maniacmusician on 2007-03-11
I probably spend more time with the GUI, simply because I'm running X.org :) Most of the apps I use are GUI apps, like firefox, amarok, konversation, etc. However, for certain tasks, the CLI is faster and more efficient, so I of course use that. But I wouldn't want to spend my internet browsing time with links2 or something.

Basically, whatever gets the job done.

As a side note, does anyone know where poofyhair guy dissappeared to?

---

### Post by euler_fan on 2007-03-11
For day to day work I spend most of my time in the GUI, but I have done work command line (editing conf files, installing software, working with a few programs, etc) and can get around the basic tasks I need to do. I would like to learn more about it and use it more, but at this time I find that if there is a program to be started from the command line, I end up adding a new icon to one of my menus to get at it more easily.

As I mentioned in passing above, I do use a CLI program regularly (R) and would not mind learning more of them, especially if the help files are good (and those for R tend to be great).

---

### Post by tbroderick on 2007-03-11
> **IYY said:**
> 
[LIST]
[*]Browsing the web: You can browse the web from the CLI, but obviously no one does this on a regular basis. Browsing the web is, by its very nature, a graphical operation and calls for a GUI.
[/LIST] 

Why is it obvious? I don't think browsing the net requires a GUI. Ads, flash, and unnecessarily large image sizes annoys the hell out of me; enter elinks. I would say my browser usage is 60/40 firefox/elinks, but elinks is gaining fast. I think CLI browsers have a great usage for browsing forums/message boards, news sites, blogs, torrent trackers, wiki, etc. I also love using it to view song titles at allmusic or cddb when tagging music, and if I need to see a particular image, I can just hit 'v' key on the IMG tag and it will open the image with feh.

---

### Post by Tomosaur on 2007-03-11
Elinks really is a great piece of kit. It's amazing how much crap it helps filter out. I don't want to see adverts, especially those annoying flash ones - elinks helps me get the job done very quickly. If you're only using the web to read stuff, then elinks is the way to go - the vast majority of images are totally pointless.

---

### Post by Quillz on 2007-03-11
I prefer a GUI.

---

### Post by FuturePilot on 2007-03-11
Let me begin by saying that I spend most of my time in the GUI but I do use the command line quite a bit.

At first I really didn't use the command line that much. But as my knowledge of Linux grew, I realized what a powerful tool it is. I think that new Linux users should get used to using the command line. At some point they're going to have to use it. They need to get used to it so when that time comes they won't be thrown into shock. There's certain things that you need the command line for. If you want Beryl, you're going to have to use the command line a little. So on and so on. The command line is what Linux is based on and I'm glad to see that it hasn't died out like DOS.

As for giving command line instructions to new Linux users: I think it's just easier. It's a lot faster to give them a little line of code they can copy and paste into the terminal than to give them a whole list of menus they have to go through.

I'm even beginning to use the command line more. Why just the other day I used it to move some files around. I wanted to move some images into the /usr/share/beryl directory. It's just faster to do that than through Nautilus.

---

### Post by 23meg on 2007-03-11
I too use CLI browsers quite often. A lot of the time, I'm just looking to grab a specific bit of information from the web, and in doing that, a quick, to the point environment without distractions helps (even more so at the times I'm already working in it). 

Another thing that helps is [surfraw]("http://surfraw.sourceforge.net/"), which is a CLI interface to various search engines and the like. Check it out if you're into text only browsing.

---

### Post by IYY on 2007-03-11
> Why is it obvious? I don't think browsing the net requires a GUI. Ads, flash, and unnecessarily large image sizes annoys the hell out of me; enter elinks. I would say my browser usage is 60/40 firefox/elinks, but elinks is gaining fast. I think CLI browsers have a great usage for browsing forums/message boards, news sites, blogs, torrent trackers, wiki, etc. I also love using it to view song titles at allmusic or cddb when tagging music, and if I need to see a particular image, I can just hit 'v' key on the IMG tag and it will open the image with feh.

I suppose that's a way of doing it, but the web is designed to be viewed in a graphical browser. You will be seeing more and more problems with your approach when Web 2.0 lifts off and many sites will be using AJAX that text-based browsers have trouble with. 

Of course, to each his own, but I would not even try to convince anyone to start browsing the web in elinks.

---

### Post by Tomosaur on 2007-03-12
> **IYY said:**
> I suppose that's a way of doing it, but the web is designed to be viewed in a graphical browser. You will be seeing more and more problems with your approach when Web 2.0 lifts off and many sites will be using AJAX that text-based browsers have trouble with. 

Of course, to each his own, but I would not even try to convince anyone to start browsing the web in elinks.

I dunno about that. It's certainly not true of 'traditional' websites. Most websites are still all about the content - they tell you something, provide information, opinions, news etc. There's no reason, other than aesthetics, why a graphical browser is 'required'. Some people just prefer to get the content, others like having the eye candy to go along with it. Sure, things like web-apps and forums make heavy use of graphics, but they still don't 'require' them. The problem is that browsers like elinks and other CLI based ones just simply do not have the features other browsers have, such as javascript, applets etc. Most things on the web are still not dependent on images and visual stuff - and could theoretically be made to work purely in text mode. Obviously, if you're using flickr, you need images, there's no way around it. Sites like Digg, or even this forum, do not 'require' images, they just depend heavily on features that text-based browsers simply do not have.

---

### Post by tigerpants on 2007-03-12
I like both.

---

### Post by ShadowVlican on 2007-03-12
GUI

been using GUI since Windows 3.1 and haven't looked back \\:D/ 

simply don't have the patience and time to memorize commands (and their many switches which differ for every command/program....)

GUI solves the problem by offering something visual so we don't have to know that "-vbr0 --vbr-new" stands for "highest quality variable bitrate using new algorithm"

it's ok to keep both.... but continually improving the GUI will kill off the fear people have of linux (whether you like it or not, command line is necessary in linux... that's a sad thing for it to be NECESSARY....)

---

### Post by tbroderick on 2007-03-12
> **Tomosaur said:**
> The problem is that browsers like elinks and other CLI based ones just simply do not have the features other browsers have, such as javascript, applets etc.

elinks does have javascript support. It just needs to be built against spidermonkey. The ubuntu binary is built without spidermonkey.

---

### Post by FyreBrand on 2007-03-12
I like the console.  I use it whenever I can.  If I don't know the terminal method for something or if I'm configuring KDE settings then I use the GUI.

I use the GUI more for applications like web browsing, word processing, etc.  I use the gui to write code (don't use VIM that often) but I use nano a lot to edit system config files.  The command line is fast and easy.  If I don't the CLI way then the gui is sometimes easier to use.  Whatever works.

---

### Post by solar george on 2007-03-12
> command line is necessary in linux... that's a sad thing for it to be NECESSARY.

Wrong.

That is if you mean **having** a command line and using it for advanced stuff, it means that if you try something and it doesn't work/breaks the gui you can mend it.


However if you mean having to resort to it to it to, say, configure wireless because the gui doesn't work it is unfortunate because it puts new users off but it doesn't make it impossibly difficult.

---

### Post by seijuro on 2007-03-12
> **poofyhairguy said:**
> STOP FREAKING AGREEING WITH ME!!!!!


Just joking.

Sorry I have to agree with you too. I consider myself an intermediate computer user in general and honestly I started out with far less user friendly distros and was not at all intimidated by the CLI I just don't buy the argument that gui is easier blah blah blah more familiar yes, easier not really. Most things can be done way faster in CLI than clicking through 15 flagin windows. I agree however that there should be the option for users to never touch the command line following one line of logic which is that linux is all about choice and personal preference well there are a lot of people the prefer NOT to use the CLI not even arguing which is better but which is "preferred". Personally I'll keep using my favorite do it all gui tool the console window. Also from my experience with new users I find it easier for most people to just give them a command they can copy past and hit enter rather than try to walk them through 15 pages of gui.

---

### Post by ndefontenay on 2007-04-03
When I consider this kind of issues, I like to put myself into somebody's else body and guess how it would look like from this perspective: My dad.

He knows computers for a long time but never really understood them. When he learns something painfully, he would stick to it for years and it's so hard to tell him that something new is better. I mean he played red alert for many years despite my efforts to show him starcraft...

So. My dad would be lost on a command line. I think we are appealing to people who knows where to get there information. They know who to turn to when they have a problem. We, Ubuntu user posting on this forum, know that there is an ubuntu community ready to help.
Some lucky dads might even go there because somebody who knows better told him where to look for solutions.

But for the noob, good but not enough, or not enough time to learn people (like my dad), they need something intuitive. This is the beauty and difficulty of the GUI.

You don't know anything about this new feature from you desktop. Yet, because the GUI allows you to hang around and discover new things (because you can see it), you will be able to get a little deeper, maybe configure a few things. If it's a really good GUI, you would know what to do without too much difficulties and if it's a good OS, your changes won't break your system or X.

I've voted  CLI. I mean it's so much simple to explain things through this but by doing so we deny the chance to a large amount of people to get to know Linux without asking someone.

We need to keep the CLI, we need to really improve the GUI and make something better than MAC OSX.

I'm in for print screens explanations of how to do things from GUI. It's needed.

---

### Post by Joneerickson on 2007-04-03
I installed Ubuntu last nite.  Then could not find only way to enter my PPPoE Info to hook to my ISP, so I had to reinstall Freespire in order to get to this Forum.

So I found the instructions under FAQs

#1
Open applications>Accessories> Terminal
_Terminal_  That means Command Line 
Command line is a Holdover from the beginning of Computers, when it was all **NERDS & GEEKS**

Was that a Space:confused:  guess not :(  start over
Opps- misspelled a word :(  Start over 
Opps- forgot the dash :(  Start over
Oh- *that one* was a Space :(  Start over [-o< 

I HATE COMMAND LINE

Whe are into GUI'ies,- Use your Mouse-, -Point and Click-,  Harry and Harriet Homeowner do not want to be sent to the Command line.  
Other Application Packages, like Freespire and Mepis have GUI'ies for this. 

So I will spend a half hour tonite reinstalling Ubuntu, and then another  hour trying to set up my Internet](*,)
**_I HATE COMMAND LINE_**

---

### Post by teaker1s on 2007-04-03
guess it will be a love hate relationship with linux then, learning something new is about taking at a reasonable pace and gathering skills-look at me I joined in 2005 and am still learning new tips and features:lolflag: 

Welcome to the forums

---

### Post by charles.g.moore on 2007-04-03
It's funny that all of the reasons you state for hating the command line boil down to your mistakes.

Was that a Space   ***I***  guess not  start over
Opps-   ***I***  misspelled a word  Start over 
Opps-   ***I***  forgot the dash  Start over
Oh-      ***I THOUGHT***  that one was a Space  Start over

---

### Post by christhemonkey on 2007-04-03
You do know you can just press the up arrow and change the one mistake you made?

No real need to start over...

---

### Post by jkeyes0 on 2007-04-03
I've used DSL before, and never had to use the OS to configure it (even in Windows). In one situation, the modem itself had a built-in webpage that allowed for the configuration (no, it wasn't a router, just a modem), and almost any router available on the market has a configuration webpage that can do this.

Alternately, if you want to manage it through your system, have you tried installing/using pppoeconf? Looking at my home system, it came preinstalled on Edgy, and I'm running it now. Try 
```
sudo pppoeconf
```
from a terminal

---

### Post by xopher on 2007-04-03
> Was that a Space guess not  start over
Opps- misspelled a word Start over
Opps- forgot the dash Start over
Oh- that one was a Space Start over 

Oh, and there's this thing we here in Finland call kopioi/liitä (copy/paste).

About the CLI, you'll learn to love it if you give it enough time. I was once a point-and-click sort of guy too, I still am, but I do use the terminal for quite a few things nowadays. It's just so fast, painless, and .. fast :) If you don't know what to do with it, then it's not though.

Bottom line, the terminal is a powerful feature when you get used to it, not a burden you are forced to struggle with.

---

### Post by jvc26 on 2007-04-03
Copy/paste into the command line is possibly the easiest thing ever with just highlight and middleclick, CLI is faster on the whole than using the GUI - Synaptic compared with a single CLI command. You get used to CLI very quickly, and to do many things you'll actually end up preferring it if you get used to it.
Il

---

### Post by insane_alien on 2007-04-03
the command line is incredibly useful even now in the world of GUI. anyway, the GUI's are really just frontends to the CLI. also, linux is pretty much the best for servers that would get little or no human interaction anyway so a GUI would just waste space. i like that i don't need to scroll through menus and sub menus and sub-sub-sub menus

---

### Post by justin whitaker on 2007-04-03
Reminds me of the Banditos in Blazing Saddles:

"GUI? We don't need no stinkin' GUI! Vamonos!"

:)

---

### Post by insane_alien on 2007-04-03
nobody needs anything other than the kernel and lynx :P

---

### Post by rolando2424 on 2007-04-03
I share the exact oposite feeling.

I LOVE THE COMMAND LINE :D

But I grew up using DOS, so I might be used to it.

---

### Post by garlik42 on 2007-04-03
I have been using computers since just after the fall of the Roman Empire, and back then we didn't even have a command line!! It was all switches and lights.

Tell you the truth, I miss the switches and lights ...

I love the command line, it allows for the finest and most absolute control over the entire system.

GUI's are OK (I write them all day at work ...) And if I find a Gui that does everything I need, then great, otherwise I can always string together 20 or 30 linux commands with pipes and redirects and do it from there.

But, everyone is certainly has there own opinion .....

---

### Post by tonyr1988 on 2007-04-03
1) Copy and paste commands. In fact, if you're reading what to do from a webpage, just select the text you want to copy, go over to your Terminal, click on it, and then push the middle mouse button (usually you press down on the scroll wheel). Tada!

2) Most people on the forums will tell you command-line methods of doing things because it's easier and (if you copy / paste) less prone to mistakes. For example, compare these:

> -Go to Places -> Home Folder.
-Right-click anywhere within that white space (where your files and folders will appear) and select "Show Hidden Files"
-Double-click on the folder named .some_app
-Double-click on the some_config.txt file and edit blah blah..

as opposed to

> -Go to Applications -> Accessories -> Terminal
-nano ~/.some_app/some_config.txt
-edit blah blah blah

---

### Post by mikewhatever on 2007-04-03
Actually, the command line is an interesting way of doing things for a Windows user. You may like it or not, but it is sure too soon to tell after 24 hours. You might like it after starting to have successes. I think expecting too much in too short a time is a general source of frustration for countless new Ubuntu users. Here is a nice thread for to relax and ponder on the meaning of the abbreviation OS
[http://ubuntuforums.org/showthread.php?t=63315&highlight=is+ubuntu+for+you](http://ubuntuforums.org/showthread.php?t=63315&highlight=is+ubuntu+for+you)

---

### Post by NT4usB on 2007-04-03
For those (like me) who can't seem to click the scroll wheel without scrolling it, Ctrl+Shift+v to paste in the CLI.
And, no one has mentioned Tab completion in this thread yet...

ed: or not...
I failed to notice this thread's been going since a kernel only made chicken.

---

### Post by aysiu on 2007-04-03
> **Joneerickson said:**
> I installed Ubuntu last nite.  Then could not find only way to enter my PPPoE Info to hook to my ISP, so I had to reinstall Freespire in order to get to this Forum. If you want help with your PPPoE, post a support thread where you ask for help. Since all you're doing is complaining, I'm moving your thread to the GUI vs. CLI discussion.

> Command line is a Holdover from the beginning of Computers, when it was all **NERDS & GEEKS**

Was that a Space:confused:  guess not :(  start over
Opps- misspelled a word :(  Start over 
Opps- forgot the dash :(  Start over
Oh- *that one* was a Space :(  Start over [-o< 

I HATE COMMAND LINE

Whe are into GUI'ies,- Use your Mouse-, -Point and Click-,  Harry and Harriet Homeowner do not want to be sent to the Command line.  
Other Application Packages, like Freespire and Mepis have GUI'ies for this. Since all you're doing is complaining, I'm moving your thread to the GUI vs. CLI discussion.

---

### Post by Brunellus on 2007-04-03
the CLI does what it does quickly and without fuss.  If you can't use it, consider this:

Can you sit down at an organ and play it well, never having learned it?  No?  Then the organ must be a terrible instrument, incapable of producing satisfactory results.

Of course, you could break down and learn how to play Bach.  But that might require understanding on your part.

I hope the command line never goes away.  I missed it in Windows.  Graphics come and go, windowing systems freeze and lock, but the terminal is extremely robust.

---

### Post by aysiu on 2007-04-03
I'm going to repeat what I've said many times before:

1. Ideally there should be both a GUI and CLI way to do *every* task. That way, you have the best of both worlds. If you prefer to use the GUI, you can use the GUI. If you prefer CLI, you can use CLI.

2. GUI and CLI are different sets of tools. Sometimes one tool is more efficient than another. I can hammer in a screw, but it'd take me a lot longer to get it in than using a screwdriver.

3. CLI is like a language. GUI is like gesturing (and not even sophisticated gesturing--like sign language). Think of every computing task as visiting a foreign country and ordering bread, asking where the bathroom is, etc. If you perform a task once, it's probably not worth it for you to figure out syntax/vocabulary and polish pronunciation. But if you perform a task daily for hours at a time, maybe you should invest some time in learning direct commands and sentences instead of madly gesturing that you want ten cinnamon buns to go and that you have to go relieve yourself at the nearest location (where is that?).

Right now in Ubuntu, we don't have GUIs for every single task, but people who criticize Ubuntu's terminal dependence often exaggerate how greatly Ubuntu depends on the terminal, often underestimate the benefits of the terminal, or often lump Ubuntu in with all Linux distros (including those that do not have the same level of terminal-dependence).

---

### Post by mech7 on 2007-04-03
CLI is that something from the 80ies :lolflag:

---

### Post by Brunellus on 2007-04-03
> **aysiu said:**
> I'm going to repeat what I've said many times before:

1. Ideally there should be both a GUI and CLI way to do *every* task. That way, you have the best of both worlds. If you prefer to use the GUI, you can use the GUI. If you prefer CLI, you can use CLI.

2. GUI and CLI are different sets of tools. Sometimes one tool is more efficient than another. I can hammer in a screw, but it'd take me a lot longer to get it in than using a screwdriver.

3. CLI is like a language. GUI is like gesturing (and not even sophisticated gesturing--like sign language). Think of every computing task as visiting a foreign country and ordering bread, asking where the bathroom is, etc. If you perform a task once, it's probably not worth it for you to figure out syntax/vocabulary and polish pronunciation. But if you perform a task daily for hours at a time, maybe you should invest same time to learn direct commands and sentences instead of madly gesturing that you want ten cinnamon buns to go and that you have to go relieve yourself at the nearest location (where is that?).

Right now in Ubuntu, we don't have GUIs for every single task, but people who criticize Ubuntu's terminal dependence often exaggerate how greatly Ubuntu depends on the terminal, often underestimate the benefits of the terminal, or often lump Ubuntu in with all Linux distros (including those that do not have the same level of terminal-dependence).
. . . or indeed, greater terminal-dependence.  Slackware, anybody?

---

### Post by Cloudy on 2007-04-03
I've grown to prefer CLI but I'd be lying if I said there weren't days I missed the simplicity of the GUI in Windows, etcetera. Then again, that's just me..

---

### Post by aysiu on 2007-04-03
> **mech7 said:**
> CLI is that something from the 80ies :lolflag:
And music is from B.C.E. Should we ditch that too?

Hey, walking is from eons ago. Let's drive cars everywhere.

Actually, the CLI is probably from the 1960s (or even before). Mice and pointing and clicking are from the 1980s.

Basic gesturing is certainly more primitive than spoken language.
Gesturing with a mouse is also more primitive than typed language.

You only replace a more sophisticated form of expression with a less sophisticated form if the time and energy put into learning the more sophisticated form is not worth the benefits reaped from learning the more sophisticated form (as in my example of visiting a foreign country once and then ordering some cinnamon buns).

Visit a country once, you may not even learn anything and just frantically point at stuff or speak your own native language and hope the locals can make out what you're saying. Visit the country twice, you might learn a few phrases from a phrase book. But if you're going to move to that country, you better be working towards fluency.

---

### Post by Cloudy on 2007-04-03
Must say, that's a pretty good analogy aysiu!

---

### Post by arbulus on 2007-04-03
Brunelleus and Aysiu are definitely spot on with this.  There are alot of users that come from Windows or Mac even that have used a GUI all their lives and aren't comfortable or knowledgeable about the CLI, but that doesn't diminish it's capability.  Just like they mentioned, it's not something that you're going to know how to do natively.  Even people who are just moving from Windows to Macs or vice versa have a difficult time adapting, and it's still just GUI.  The fact is that it's something you have to learn, and if you've decided to change your OS, that must mean that you are open to the idea of learning something new and the CLI is just another part of that.

When I first said to myself that I wanted to learn Linux, I didn't think of it in terms of the GUI.  I wanted to learn the CLI, the nuts and bolts of the system.  Not only did I feel like it would be a great advantage to me to learn a new OS, but also to feel like I intimately knew how the system worked.  And more than that, it just seemed cool.  You know, there's kind of this air of intrigue and mystique to being able to use a computer and do amazing things with no graphics on the screen, just simple (or complex) commands you type in.  Sure there are GUI ways to do many things is most Linux distros, but there are somethings that you have to do in the command line as well, and some distros divvy this up in different ways.  

But I've always looked at the GUI as sort of training wheels.  Since my initial purpose was to learn the CLI, that's what I've always focused on.  Whenever I've had a problem, I've always wanted to find both a CLI and GUI solution to it.  Now, don't get me wong, I enjoy GUI.  It's very nice to boot up my comp and see my nearly-totally-configurable desktop, and that's one thing I love about Linux: I can make my environment look how I want, and I really enjoy that since no other OS has that kind of capability.  But the aesthetics are just that: aesthetics.  The real key to learning Linux is learning to be comfortable in the CLI; and learning is exactly what you have to do.  You can't just pick it up today, having never used it, and expect to be fluent.  Just like you have to learn a new language, how to play an instrument, how to fly a plane, etc.  It's another thing you have to learn.  And the learning process has it's ups and downs.  You will probably at some point kill your system and have to reinstall because you typed a wrong key.  It has happend to me several times.  It happens to everyone.  that's just part of it.  But the frustrations you have make the successes so much sweeter.  Whenever I finally figure out something after a few hours of pulling my hair out, I feel like I just climbed a mountain.  It's a great joy to know you just figured it out, and that you didn't need the GUI to hold your hand to do it.

Sure, people used teletypes with acoustic couplers to connect to a mainframe at the university 30 years ago.  So what?  The fundamentals are still relevant.  Being able to communicate with your computer directly and fundamentally is one of the most powerful tools that we can have as users, and I hope that we never lose that tool.

---

### Post by userundefine on 2007-04-03
> **mech7 said:**
> CLI is that something from the 80ies :lolflag:
So is GNU.  Hell, UNIX is from the 70s.  So what are you saying?

I love the command line.  I *try* do everything I can from it except for the obvious GUI things like web browsing.  I use irssi for IRC.  Why run a large, clunky GUI program just for IRC?  I like Konversation and Xchat, but they're more hindrances when I want to get to the chat NOW.  If it's minimized, I have to go click to bring up the chat.  I want to stay at the keyboard as much as possible.  So, I run Yakuake, a KDE terminal that is always running in the background and displays/hides on keyboard shortcut.  Moreover, I run irssi in screen, and thus I have unlimited terminals through yakuake without having to create 'tabs' and navigate each with a click.

CLI is just so much faster, and I try to find ways to do less from a GUI and move those habitual actions into CLI.  For example, why load up a GUI prog to convert some flac files to another format?  I wanted to get oggs from some flacs.  So, I went cd dir && oggenc *.flac.  Done!  I use mplayer to stream and dump the contents of an RM file, then use mencoder to output the dumped file to an .avi in xvid.  I can't even imagine how I'd go about this through GUIs.

I'm not a CLI guru yet either.  I'm not much of a scripter, although I'd like to be, and I'm constantly learning stuff about bash (and vim, another staple of CLI).  CLI is a great strength of Linux, hardly a hindrance.

---

### Post by FyreBrand on 2007-04-04
> **Brunellus said:**
> **the CLI does what it does quickly and without fuss. ** If you can't use it, consider this:

Can you sit down at an organ and play it well, never having learned it?  No?  Then the organ must be a terrible instrument, incapable of producing satisfactory results.

Of course, you could break down and learn how to play Bach.  But that might require understanding on your part.

I hope the command line never goes away.  I missed it in Windows.  Graphics come and go, windowing systems freeze and lock, but the terminal is extremely robust.I highlighted the part that stood out to me.

This last week over spring break I had to get ready for my classes.  This meant two major changes for my system.  First I had to install Fedora for a networking and server class.  Next I had to install Visual Studio 2005 for a programming class and project.

I got the VS2005 installed.  MSDNAA gave us the "pro" edition.  The "Developer Edition" of SQL Server 2005 was really SQL 2005 Express Edition.  But it didn't have a front end to manage the database among other things.  So I had to install the SQL Express edition with advanced services.  This meant reconfiguring the whole damn SQL server.   I waded through Microsoft's MSDN site and found the answers to the toughest configuration questions (I guessed on the easy ones).  There were pages of instructions that had me clicking through menus and dialogue boxes.  Clickety click click click click click!  It was a gui nightmare and not easy.

I thought to myself if I was over in Kubuntu configuring Apache and MySQL I could do this whole damn thing in a few quick commands at the terminal.   For one thing I would have had to wonder what version I was using.  I could use the command line and get the straight answer right away.  Then I could tell it to load encryption and security modules.  I wouldn't have to click through endless windows only to find out that I don't have the option to install ssl anyway.

Sorry for a ramble and rant, but I am so glad there is a terminal to get things done.  It would be a nasty fight to take that away from me.

---

### Post by hanzomon4 on 2007-04-04
The command line was actually the thing that won me over when I made the switch. Basically I saw an OS-X ad with a transparent terminal and bam I fell in love...

Back to reality, learning to use the command line is not as difficult as it seems and the benefits that come with it's use are hardly obvious. One incident that showed me the power of the command line was when I needed to move all of my .m4p files to a one folder. I kept my itunes folder on a usb hard drive and when I moved to linux from xp I used this folder as my music library folder. Problem was music apps would get stuck trying to play the drm-ed files. I had about 40 drm-ed files all of which were in sub directories of the iTunes dir(iTunes/Artist/Album). Going through each folder with nautilus would have been a pain so I used the find command.

With the find command I was able to search all of the sub-directories of the iTunes dir and pluck all of the .m4p files to a separate dir outside of my music library(iTunes dir). The one command was this:  ```
find /path/ -iname "*m4p" -exec mv '{}' ~/music/ \;
```

[list][*]**find /path/** - tells find to search *path(ex. /media/usb/)[*]**-iname** - tells find to be case insensitive[*]"***m4p"** - tells find to find all files in the search path that end in "m4p"[*]**-exec mv** - tells find to execute mv on the found files[*]**'{}'** - represents the files found that are to be moved[*]**~/music/ \;** - tells mv were to move the files to and the "\;" at the end stops bash from expanding any symbols used by the shell(I think)[/list]

To be honest the only way to learn the command line is to actually need to use it. In my case digging down into tons of files with nautilus proved to be my line in the sand, thus I learned a better to accomplish the same task. Getting kicked out of X in the early days of compiz-quinn taught me how to be comfortable using the command line as a file manager. Testing feisty and losing synaptic for a few days taught me how to search for files using apt-cache and read descriptions of packages all from the command line. 

To summarize: Only through need will you grow...

---

### Post by FoolsGold on 2007-04-04
CLI, easily.

The GUI is nice when you don't quite know what you're looking for, you just run with it and see what happens. Once you know how things can be done with a terminal though, it's much quicker/more powerful.

---

### Post by slayerboy on 2007-04-04
> **wersdaluv said:**
> Studying the command-line takes so much effort. I have been using Linux for a while but I still am not used to the command-line. GUI does a lot of things and it does not require you to research as much as how you will research for the command line.

I only use the command-line whenever I am given a code to enter. I do not improvise. I do not use the command-line to rename, move files, or whatever.

It is also possible that, one day, people will not have to use the command-line or the codes that one has memorized are obsolete. I find it sort of a waste of time to memorize a lot of things that I could not be using one day. Also, I do not think that a code is universal. Maybe, different distros require different codes. 

They say that using the command-line can save you time. I say, maybe, studying those codes will take me more time because knowing those very advanced stuff means a lot of time in front of the manual.

Another thing that hinders me is the idea that you will have to research on codes before you use a terminal. Imagine if someone who has no experience with the command-line has to face a black screen (terminal) or a black screen in a window (terminal emulator). When I opened the terminal emulator, it did not come with a manual. There were some basic commands from the local Ubuntu documentation, but seeing them is not that easy for an inexperienced user and they are not complete and comprehensive enough for beginners. If a person who knows how to maximize technology faces the command-line without prior knowledge, what he will do is to RTFM or google. That's the way, but it also takes experience to realize that. 

If a tech savvy dude who is not familiar with the command-line googles for guides about it, he will still have a hard time seeking for comprehensive guides. Once he finds the best ones, he will still have to exert hours and hours reading it.

The good thing about the command-line is the idea that codes make life easier and faster, but I do not see it as a good enough reason for me to study the command-line.

Please help me decide whether or not I should study the command-line.

I have an open mind when it comes to this issue.

Take a look at the post that is right above yours in this thread:

> **FyreBrand said:**
> I highlighted the part that stood out to me.

This last week over spring break I had to get ready for my classes. This meant two major changes for my system. First I had to install Fedora for a networking and server class. Next I had to install Visual Studio 2005 for a programming class and project.

I got the VS2005 installed. MSDNAA gave us the "pro" edition. The "Developer Edition" of SQL Server 2005 was really SQL 2005 Express Edition. But it didn't have a front end to manage the database among other things. So I had to install the SQL Express edition with advanced services. This meant reconfiguring the whole damn SQL server. I waded through Microsoft's MSDN site and found the answers to the toughest configuration questions (I guessed on the easy ones). There were pages of instructions that had me clicking through menus and dialogue boxes. Clickety click click click click click! It was a gui nightmare and not easy.

I thought to myself if I was over in Kubuntu configuring Apache and MySQL I could do this whole damn thing in a few quick commands at the terminal. For one thing I would have had to wonder what version I was using. I could use the command line and get the straight answer right away. Then I could tell it to load encryption and security modules. I wouldn't have to click through endless windows only to find out that I don't have the option to install ssl anyway.

Sorry for a ramble and rant, but I am so glad there is a terminal to get things done. It would be a nasty fight to take that away from me.

Let me tell you why I favor the CLI over the GUI in some instances, and some others I favor the opposite.  If I'm trying to install or configure software in a GUI, it's a series of constant clicks.  If I am not familiar with the software and I look online for help, it's a constant flipping between the actual program and web browser or I have to print out the instructions, and even then I still might click the wrong thing.  This is fine for simple tasks.

But when I go search the forum or google on how to install drivers for my nvidia graphics card and just copy and paste the command into the terminal, it's almost insulting my intelligence.  But that is MUCH easier to type a command to execute a script that does several things and see output almost instantly if there were any errors.  Granted you could probably do this in a GUI, but it makes the file size to download that much bigger and bloated.  Copy and paste is really about all I know with the CLI, besides stuff like "ls -a, ls -l, cd, etc...etc...etc"  Don't be fooled when someone tells you to enter a command in the terminal.

And actually...I have to admit....without the GUI, you wouldn't really have copy and paste, so the GUi has +1 there.  But CLI does things much quicker, especially updating your system.  Not to mention it's easier to support someone when you can tell them exactly what to copy and paste, there's really no confusion there.:)

---

### Post by arbulus on 2007-04-04
Aysiu kinda beat me to it, and also relating back to my earlier post:  learning Linux is an interesting concept.  Where any of us to say to someone "I use Linux", it wouldn't make much sense to most people.  There are so many flavors of Linux that one has to be specific.  I use Ubuntu, Fedora, Red Hat, etc.  That's because things work differently between distros. Take an average new-comer to Ubuntu and drop them in the middle of Gentoo and they'd be lost.  But on an even more simple note, switch the Desktop Environment.  

Say you run Ubuntu with Gnome, but then you're put in front of a comp running Xubuntu with XFCE.  Or, a little further, you go from Ubuntu with Gnome to Ubuntu with Fluxbox.  Suddenly, you're in a completely new world.  Things don't appear the same way.  Menus are different, things function differently.  Now, it's still the same OS underneath, but your GUI is a completely new world.  How do you level the playing field between all of these variables?  The Command Line.  Your commands are going to be roughly the same.  Now granted, there are a few differences, such as Slackware's use of rc instead of init for application control, or the differnces with repositories between distros, but those things are a pittance compared to the other 99% of the commands that are the same.  If you were given a Gentoo CLI next to an Ubuntu CLI you could still type "mv ~/pictures/rome ~/pictures/vacation" on both machines and achieve the same result.  Conversely, if you had Gentoo with Fluxbox and Ubuntu with Gnome you'd have to seach around a bit to figure out exaclty what you needed to do in the GUI in order to do that on each one. 

My point is that GUI is superfluous.  It comes and goes.  Gnome, KDE, FVWM, Fluxbox - you have different worlds of UI here that require learning in each.  But there is a universal language that transcends all of that:  the CLI.  If you know the CLI, then you know Linux and Unix.  You become a power user that can be comfortable in any environment that you end up because you know how to ask the computer to do exactly what you want it to do without confusion.  Then, you can experiment with the "window dressing" that makes your experience more aestheticly pleasing, but can hold on to the knowledge that no matter what that aesthetic is, you can still get a job done.

---

### Post by eentonig on 2007-04-06
Apache and proxy can be done through webmin if I'm correct. So they can be removed from the list.

---

### Post by Brunellus on 2007-04-06
> **eentonig said:**
> Apache and proxy can be done through webmin if I'm correct. So they can be removed from the list.
Webmin's security has been a concern lately.  

A headless server, administered via the command line, accessed via ssh, simply has fewer things that can go wrong.

---

### Post by waxapple on 2007-05-09
I voted, then I was somewhat surprised to see GUI way out in front.

CLI all the way.

---

### Post by n0dl on 2007-05-09
World War III will be fought with ENIACs and Punch cards. Are you prepared?
I voted CLI by the way. I like X... But i use it because i can open 20 Xterminals at once...

---

### Post by tbroderick on 2007-05-10
> **n0dl said:**
> 
I voted CLI by the way. I like X... But i use it because i can open 20 Xterminals at once...

Have you tried screen? Great tool if you want 20 terminals open but don't want 20 separate windows.

---

### Post by PrimoTurbo on 2007-05-10
I think it's important to create a desktop that doesn't require the use of a terminal to accomplish all tasks, however at the same time a terminal should always by an option.

I think the problem with new users is that they have no idea what they are doing when using the terminal, instead of telling people to type up a command maybe explain clearly what the command does and how each part works. Perhaps there needs to be a New User guide provided after an install of Ubuntu that explains very clearly and easily some of the _**BASICS of a Linux desktop and command line**_.

---

### Post by Tundro Walker on 2007-05-10
This topic is way over-posted, so I doubt anyone will read this, but...

I think both the GUI and the CLI can use improvement.

1) I agree that CLI-phobes should have a GUI way to do things.  However, a GUI solution usually involves more overhead (windows, button clicking, etc) to do things then CLI.  But, it gives folks a nice, presentable way of doing things where they don't have to guess at what to type, or what options they have.  They can just explore the GUI and figure it out, w/o needing a manual on-hand.

2) I also agree that the CLI is more powerful.  But, I think it needs to be made even more powerful by using "intellisense" and such.  I know you can type a command, and hit TAB to see a list of possible ones to complete it with.  But, I think while you type, it should start auto-suggesting such to begin with, much like modern IDE's do today.  The CLI is powerful, but it's still pretty archaic.  I think modern-day ideas should be melded into it, like intellisense.

---

### Post by Brunellus on 2007-05-10
> **Tundro Walker said:**
> This topic is way over-posted, so I doubt anyone will read this, but...

I think both the GUI and the CLI can use improvement.

1) I agree that CLI-phobes should have a GUI way to do things.  However, a GUI solution usually involves more overhead (windows, button clicking, etc) to do things then CLI.  But, it gives folks a nice, presentable way of doing things where they don't have to guess at what to type, or what options they have.  They can just explore the GUI and figure it out, w/o needing a manual on-hand.

2) I also agree that the CLI is more powerful.  But, I think it needs to be made even more powerful by using "intellisense" and such.  I know you can type a command, and hit TAB to see a list of possible ones to complete it with.  But, I think while you type, it should start auto-suggesting such to begin with, much like modern IDE's do today.  The CLI is powerful, but it's still pretty archaic.  I think modern-day ideas should be melded into it, like intellisense.
God save me from a shell that is "smarter" than me.  I would be horrified to see the shell autocomplete things that I hadn't even typed yet.  

If you're interested in shells other than bash, you might want to check out [fish](http://en.wikipedia.org/wiki/Friendly_interactive_shell).  I haven't used it myself, however.  I stick with bash, since that's the Linux default.  I've used (*ever* so briefly) ch and tsch and busybox (which isn't really a shell).  But picking a shell is one of those things:  if you don't know how to use bash, you won't know to pick another shell.  If you know to pick another shell, you either have very specific needs or you already know bash...

---

### Post by goumples on 2007-05-10
> **Takis said:**
> I'd say Linux without a command-line is a long, long way off, so till that time new users need to be introduced to it. It's a very scary thing in most cases so the earlier they get used to at least doing a couple of things here and there, the better. It doesn't have to be a throw in the deep end, it can just be splashing your feet in the water, as long as you realise that in the end, it's just water (or a command line).

On a side note, I'm getting pretty annoyed at Windows' auto-complete (TAB) feature. I'll type 'cd Proga<TAB>' and change into the directory, and the VERY NEXT THING I'll type is 'ls'! Every time!

I perfer CLI to GUI when doing alot of things.. I suppose one day things will be so seemless that a command prompt will be redundant.. but not this day!!

---

### Post by rai4shu2 on 2007-05-10
I use Worker, but I wonder whether Midnight Commander counts as GUI or CLI.

---

### Post by hsweet on 2007-05-10
Beginners these days need a gui.  

Even for experienced folks, it's hard to remember all the switches and commands. (It would be nice to have a good, small handbook of some sort).  man lists all the dozens of switches but I would like to have a few simple examples at the top before all the screenfull of details.  I usually head to a web browser to find an example or 2 if I can't remember some command's syntax.

The cli can't be beat for automating stuff. And for when the gui misfires (I had a server's ip stuff set up gui-wise where the mask was reported incorectly by ifconfig.  The gui wouldn't fix it but the cli did) 

Maybe what is needed is something similar to w3schools.com where you can play with live examples of how to..... whatever without a gui.

enjoy the beer.

---

### Post by Foxmike on 2007-05-10
Well, as I love GNOME GUI, I must say that CLI is very fun to use once you get used to it.

Since I began with Linux (1 1/2 y ago with Breezy), I've never been afraid by command line instructions to copy/paste in terminal, though I would have sometimes appreciate a comment after each just to explain the action the command line is doing.  That way, it would have been a lot easyer to learn.  I actually try to do that as much as I can when helping someone.

As for the end, I found command line so fun that I decided to give Gentoo install (via stage3 tarball) a try...  Tho some people might call it masochism :roll:

---

### Post by johntkucz on 2007-05-29
hey poofy, brilliant initial post, love the detail.  laughing about the F.No F. multiple-answer.

---

### Post by johntkucz on 2007-05-29
plus the CLI just looks WAY cooler in action than dragging around windows, but it's good to have the GUI as a back up.

---

### Post by unrandomsam on 2007-05-30
> **Tundro Walker said:**
> This topic is way over-posted, so I doubt anyone will read this, but...

I think both the GUI and the CLI can use improvement.

1) I agree that CLI-phobes should have a GUI way to do things.  However, a GUI solution usually involves more overhead (windows, button clicking, etc) to do things then CLI.  But, it gives folks a nice, presentable way of doing things where they don't have to guess at what to type, or what options they have.  They can just explore the GUI and figure it out, w/o needing a manual on-hand.

2) I also agree that the CLI is more powerful.  But, I think it needs to be made even more powerful by using "intellisense" and such.  I know you can type a command, and hit TAB to see a list of possible ones to complete it with.  But, I think while you type, it should start auto-suggesting such to begin with, much like modern IDE's do today.  The CLI is powerful, but it's still pretty archaic.  I think modern-day ideas should be melded into it, like intellisense.

Try zsh

[http://grml.org/zsh/zsh-lovers.html](http://grml.org/zsh/zsh-lovers.html) (should get you started - you can set it up to make things much more intuitive than with bash)

---

### Post by stylofone on 2007-05-30
I've done a fair bit of training with computer users of all levels of experience, on text-based and GUI systems, and this is my take.

The GUI is the start and end of most people's computer experience. If Ubuntu does not encompass this reality, it will remain a niche system for geeks. The CLI looks to most people like a black hole, telling them nothing, mocking their ignorance. To use it you need to know the command and the options. A GUI can, for example, present the command, and all the options in a drop down box, with little hints that pop up on rollover. It's so much more useable to so many more people. 

Here's another example. I used to have a little windows program to list in a text file the contents of a directory. I used it to catalog discs. I replaced the whole program in linux with this command: 

ls -RCla /media/cdrom0> /home/stylofone/stuff/list.txt

Now, there's no way I have the patience to type that out every time, or remember it, or even remember the name of a script I include it in. So I made a panel icon for it. Now I just click that icon. One click! It's just so much more organic and easy once it's turned into a GUI element. I can tell my Mum and she'll remember it.

Yes, there are things the CLI can do very well. There are also things a GUI can do better, yet a GUI does not yet exist for them in linux. This OS is not finished! Give us GUIs!

I'm coming to this debate late, but it pops up very high in a google search, so I guess the thread is still alive and kicking.

---

### Post by Genecks on 2007-05-30
> **poofyhairguy said:**
> As many know I try my best to help out new Ubuntu users. Many of us do, and its a great thing. Often on this forum I will tell people commands to put in the command line to fix their problems. Recently I was told that this is not the best thing, as it scares away new ex-Window's users who associate "command line" with "Dos"

I started messing with computers in the days when a person needed to boot Windows from DOS. ^_^ I'm more comfortable with a command-line interface, as long as it does what I want it to do. Yet since the revolutionary days of Windows 95, when things became more graphical and complex, I've begun to use the GUI more often. I keep thinking of DOS whenever I play with bash, so I feel like it's a step in the past.

The only thing that made me walk away from Linux was the inability to use wireless Internet two years ago. However, I am now able to use my netgear, so there is little problem.

I don't like the idea of using CLI anymore, because GUI's were created to simplify everything. If I did use a CLI in later versions of windows, it was for two important things:

1) I could manipulate files and directories faster that way
2) I needed to use an old program

WIth the additional speed by today's computers, I can quickly move things in WIndows, so I don't have any large problems. GUIs were created to simplify actions that were done over and over and over again, by multiple, various users. I had all the commands of DOS memorized at one point in life. Yet, as the speed in personal computer began to rise, I could use the GUI faster than the CLI. Apparently, I'm going to reduce work and time needed, thus giving me more power as a user.

As I'm using Kubuntu more and more, I believe some GUIs would be in order. I'm starting to use some simple commands over and over again, and a GUI could easily take the place of these actions.

---

### Post by a12ctic on 2007-05-30
CLI apps are so much simpler. I don't like having to drag my mouse all over the place. For somethings I like a GUI (like a web browser, instant messager, or music player) but for thigns like encoding, moving files, renaming files, installing programs, etc, i prefer the command line by a long shot. I mean seriously, whats simpler than apt-get install x or if its not on apt just do wget *.deb
dpkg -i *.deb

---

### Post by aysiu on 2007-05-30
> **a12ctic said:**
> I don't like having to drag my mouse all over the place. Well-designed GUI apps have a full set of keyboard shortcuts.

---

### Post by Genecks on 2007-05-30
Ultimately, it's all about saving time. I'm sure if you could click on the program within a directory twice instead of having to type "apt-get," then you would reconsider the CLI.

> ]I'd say Linux without a command-line is a long, long way off, so till that time new users need to be introduced to it. It's a very scary thing in most cases so the earlier they get used to at least doing a couple of things here and there, the better. It doesn't have to be a throw in the deep end, it can just be splashing your feet in the water, as long as you realise that in the end, it's just water (or a command line).

I remember being in Best Buy, a electronics-retail store, over four years ago. The first thing I asked the person at Best Buy was this: Does it have MS-DOS?

Sure, command-line interfaces are still nice for typing out things and getting tasks accomplished. Typing "ping" in a CLI is faster than loading and using a program.

---

### Post by mrgnash on 2007-05-30
There is no 'VS.', the two are complimentary.

---

### Post by GrueTamer on 2007-05-30
As some people know, the CLI is my best friend, and I run a window manager that utilizes none of the pretty gui tools of Gnome, or of KDE.  These tools are still important, mind you, as they can save new users from terror (cmon, most people think that they'll mess up in a CLI more often than in a GUI), and can help users who don't know much of the CLI/are learning it a chance to still use their computer without much CLI knowledge/learn how the CLI works.

But knowing the CLI, even in this day of GUI dominance, is still one of the most important, if not THE most important, thing to learn, no matter how long it takes you.  If your X won't start, and you don't know how to do basic things in a CLI, your computer may have become useless.  It is for this very purpose that I have started compiling a lot of information about the CLI for my own knowledge, and so that I may better help users of ubuntu who need CLI help.

Even if the CLI scares you, the only way to gain dominance over the fear is to embrace it, even if it's bit by bit, every day for a few years.  Just open your mind and jump in, it's worth it :)

---

### Post by stylofone on 2007-05-31
The CLI is important you say, but important to who? The original point of this forum was how to help newcomers. Try to think of a casual computer user; I imagine how my parents would react if I tried to introduce them to Ubuntu. If they are forced to use the CLI, then I've failed. When it comes to their computer, they don't want to launch some self-improvement project that will take years, they want instant gratification. 

I guess what I'm saying is that we need to focus on CLI avoidance for people like my parents, and CLI enhancement for people like you and me. So yes, I agree with you that the CLI is great, in fact it's a mature and well-developed part of Linux... but I want to make the point that the advancement of the GUI is the real mountain to climb, it's not finished and it needs development.

> **GrueTamer said:**
> 

But knowing the CLI, even in this day of GUI dominance, is still one of the most important, if not THE most important, thing to learn, no matter how long it takes you.  If your X won't start, and you don't know how to do basic things in a CLI, your computer may have become useless.  It is for this very purpose that I have started compiling a lot of information about the CLI for my own knowledge, and so that I may better help users of ubuntu who need CLI help.

Even if the CLI scares you, the only way to gain dominance over the fear is to embrace it, even if it's bit by bit, every day for a few years.  Just open your mind and jump in, it's worth it :)

---

### Post by aysiu on 2007-05-31
> **stylofone said:**
> I guess what I'm saying is that we need to focus on CLI avoidance for people like my parents, and CLI enhancement for people like you and me. If you want to focus on CLI avoidance for your parents, fine. You can  help your parents in person.

For online help on a text-based forum, the CLI is the best, easiest, fastest, and most informative way to offer help to people experiencing problems. And most people on these forums are "people like you and me." They are not your parents or "casual users" as you call them.

In any case, you don't have to force new users to use the CLI to rip a CD or edit a photo, but if someone tells me "Synaptic Package Manager seems to launch, but then the window disappears right away," I have no idea how to help that person. If, instead, she posts the terminal output of the command ```
gksudo synaptic
``` I can better diagnose what's going on.

> The original point of this forum was how to help newcomers.  These are support forums, and the best way to give support (especially since some people use Kubuntu or Xubuntu) is through terminal commands.

In some cases, I'll post screenshots if I think they're appropriate for the problem at hand, but this is an online *forum*, and it's not that difficult to copy and paste commands (retyping is for the birds).

---

### Post by init1 on 2007-05-31
I use the xterm a lot, so I will go with CLI

---

### Post by Feba on 2007-05-31
I don't understand the command line, yet, but I definitely appreciate it more than the GUI, despite the fact that I'm practically dead without a GUI.

---

### Post by blackspyder on 2007-05-31
While I spend most of my time working with the GUI (as its just a little easier for me). i am not shy about opening up the command line and getting something done from there if the need arises. While Im still a N00B at the *nix commands I have books on essential  Linux commands and phrases. If the person helping me tells me to use the command line and gives me the command to use I look up each part of it in my little books so i can understand it and if I cant find it I'll ask after i do it.

Learning the command line is important even if you use windows. If explorer goes down because of a virus all you have is the command line left to run various anti-virus programs like HiJackThis so your not stuck in a reformat and reinstall motion.

---

### Post by ep2011 on 2007-05-31
I'm very similar to many others. I usually use guis (Gaim and firefox mostly). But if I need something such as moving files, deleting root files, editing root files, etc, I use nano and the Command Line. So much simplar (I acually used to run "gksudo nautilus" but I don't anymore).

Edit: I also ALWAYS use aptitude to install packages. (To search packages I use aptitude search *blah*)

---

### Post by Channic on 2007-05-31
I'm not a master at CLI, I forgot most of the basics. At least I can start with a bare linux system (arch, net-install debian, gentoo, etc) and get everything working from there. But when in GNOME I usually stick to the GUI program that I have. But then again when I get documentation I like to have it in command line for simple copy and pasting . . . so lazy here.

---

### Post by Celegorm on 2007-06-01
I suppose I use the GUI more, but I use the CLI a lot, especially for writing simple C programs or doing anything complicated. There are a lot of things that I'll do either in the GUI or CLI depending on my mood, like moving files or installing new packages. Plenty of things are easier or faster in the CLI, and some things that are easier in the GUI (like web browsing, have you ever tried to browse the web from a terminal?) and it's generally best to know ways to do the same thing in both.

The advantage of the GUI is that you usually don't need to know what you are doing in order to find out how to do at least the simple things, and so of course it's more comfortable for someone who is entirely new to linux (and doubly so for anyone who has only used a GUI in the past), but I definitely think that new users should be introduced to the CLI early on, so they will see that it doesn't bite ;)

---

### Post by tashmooclam on 2007-07-31
I believe that people will usually feel more safe using the GUI, because it seems that you can "cancel" anything you think may be likely to screw up something.

For example, I noticed that I like download manager GUI because I think it "knows" what I should and should not try to download.
I used the terminal a couple of times, entering the info given to me by a complete stranger. I crossed my fingers because I was afraid I had made some irreversible change to something.
Having just begun using Ubuntu, I have no idea if I can do more "damage" using the terminal or a GUI for something. 
GUIs are inherently more approachable by the new user. 
It's cool that the terminal is there however. Impress your friends! :cool:

---

### Post by userundefine on 2007-07-31
> **tashmooclam said:**
> I believe that people will usually feel more safe using the GUI, because it seems that you can "cancel" anything you think may be likely to screw up something.

For example, I noticed that I like download manager GUI because I think it "knows" what I should and should not try to download.
I used the terminal a couple of times, entering the info given to me by a complete stranger. I crossed my fingers because I was afraid I had made some irreversible change to something.
Having just begun using Ubuntu, I have no idea if I can do more "damage" using the terminal or a GUI for something. 
GUIs are inherently more approachable by the new user. 
It's cool that the terminal is there however. Impress your friends! :cool:
If you're worried about a command someone has given you, you should always **man *command*** and read what it actually does.

And CLI has a cancel button too.  It's Ctrl+C.  But you're right, you can do much more damage from CLI.

---

### Post by aysiu on 2007-07-31
> **userundefine said:**
> If you're worried about a command someone has given you, you should always **man *command*** and read what it actually does.

And CLI has a cancel button too.  It's Ctrl+C.  But you're right, you can do much more damage from CLI.
Or, if you're lazy, wait an hour or two before running it. If someone gives a bad command (with ill intent or not), it's very likely that another forum user will step in and say, "Hey, don't run that command."

---

### Post by TheeMahn2003 on 2007-08-06
In the past I have read and learned much from you, you are quite the Mahn of *nix especially when it comes to eyecandy.  I have used your howto for composite video, before any beryl, compiz or for that matter compiz-fusion, or whatever they decide to call it even existed...  I do have intentions of doing the exact thing that this topic is based upon.  In windows world called a mime type based application, I will make it happen, I do have priorities that I have to take care of first but none the less when I am done the terminal will be dead.  I personally like the terminal, but do not feel others should have to tolerate it.

I have written perhaps 100's of programs for windows, most utilising the API (advanced programming interface).  A simple task, or so I hope to create exactly what this post is here for.  I thought I would touch bases with you for testing purposes, for not just my version of Ubuntu but all.  Do you mind if I post code and scripts to your thread for testing?

I would like to know if anything has been started, one thing I have learned is do not re-create the wheel when it comes to programming.

Best regards,

TheeMahn

---

### Post by Kossilar on 2007-08-26
When I first installed Ubuntu, my videocard didn't work. So I had to download and install the driver from the commandline.

I was lucky because I had a second computer in the same room and used it to figure out how to do that. The experience helped me to become very familiar and comfortable with getting things done in this way and my Linux experience has been much improved as a result.

I think that Linux should never remove the command line entirely. However I think its also important to have simple, streamlined ways of taking care of simple problems.

---

### Post by RageOfOrder on 2007-08-26
Gentoo & Slackware user, I think you know which I use the most. :)

---

### Post by Omnios on 2007-08-26
Hi Poof. 

 Personally I kind of prefer both but this got me thinking. I hacked a few scripts and added open  terminal here.
```

#!/bin/bash
#
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal

``` 

 Anyways this got me to thinking about GUI and CLI and its integration. So kind of thinking it might be interesting to be able to add open terminal here etc to the GUI. I llso got thinking it might be interesting to have a CLI terminal that has some GUI linkit type features. So say you use the ls command and a bunch of files show up. Now with a linkit a user could click a file in the ls list and navigate to that file from doing so.

 I think there can be a lot of things done like this but one of the problems is getting interest of developers and posting it in community discussions will not do that. 

 Another interesting aspect of this could be a remote server control to make it easier to control than a normal terminal. 

 Um soft of like a terminal simplified browser program with a lot of abilities.

---

### Post by ubuntu27 on 2007-08-26
> **Omnios said:**
> Hi Poof. 

 Personally I kind of prefer both but this got me thinking. I hacked a few scripts and added open  terminal here.
```

#!/bin/bash
#
cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal

``` 

 Anyways this got me to thinking about GUI and CLI and its integration. So kind of thinking it might be interesting to be able to add open terminal here etc to the GUI. abilities.

This already can be done. Simply install nautilus-open-terminal from the repository.
```

sudo aptitude install nautilus-open-terminal
```

As for your idea about CLI and GUI integration, i like it. :)

---

### Post by flatwombat on 2007-08-26
I'm really surprised to see the current state of the Poll.  Approximately one third of the responders use the CLI more than Gui and this is in a distro that has been labeled by some as a 'new user' distro.  

To me, it shows that people who are attracted to linux like to get under the hood, no matter what the distro and don't mind learning coding in the process.  I suspect that even the 2/3rd. majority does open a terminal and do some typing from time to time. :)

---

### Post by rolando2424 on 2007-08-26
> **Omnios said:**
> 

 Anyways this got me to thinking about GUI and CLI and its integration. So kind of thinking it might be interesting to be able to add open terminal here etc to the GUI. I llso got thinking it might be interesting to have a CLI terminal that has some GUI linkit type features. So say you use the ls command and a bunch of files show up. Now with a linkit a user could click a file in the ls list and navigate to that file from doing so.

 I think there can be a lot of things done like this but one of the problems is getting interest of developers and posting it in community discussions will not do that. 

 Another interesting aspect of this could be a remote server control to make it easier to control than a normal terminal. 

 Um soft of like a terminal simplified browser program with a lot of abilities.

ah... Hotwire?

sudo apt-get install hotwire (I think...)

I can't remember if it has all those feature though.

---

### Post by thinsoldier on 2007-08-26
Most windows users I know have never even seen the  command line in windows.

The few that have used it to release/renew their ip address with ipconfig.

The thing about the few reasons why an average windows users would use the CLI is that in most cases it's fully explained to them what they're doing in the command line and commands like 'ipconfig' obviously mean that it has something to do with configuring your ip address. A few dozen calls to ISP tech support and most people eventually understand what an IP address is and it's importance to being able to "surf google"

People hopefully have at least a vague sense of what's going on when using a gui and it's more of a 'physical' process in that they can remember the 'directions' to a location and a goal.

Some seem to handle multiple steps in a gui better than in a cli where everything you see is some cryptic nick name or code word. GUI windows tend to have plain English titles and plain English menu items

Someone (like me) might ask:
"Why can't I save files on my windows drive?"
and get an answer like this:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy)

W T F ???
A brave person might be willing to try but there's a good chance that when it's all done they still have no clue what they just did or why/how it worked.

If anything you type in a CLI can be saved as a script file and made executable why don't people try just scripting up what will fix someone's problem and tell them to download and double click the file and all their troubles will go away. That's what most people really want.

---

### Post by aysiu on 2007-08-26
> **thinsoldier said:**
> 
Someone (like me) might ask:
"Why can't I save files on my windows drive?"
and get an answer like this:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy)

W T F ???
A brave person might be willing to try but there's a good chance that when it's all done they still have no clue what they just did or why/how it worked. That HowTo is a bit old.

This one is more up-to-date:
[Windows NTFS Partitions Read/write support made easy in Ubuntu Feisty](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by smartboyathome on 2007-08-27
I usually use the terminal for little things like installing programs that I already know the package name of (no need to waste time waiting for Synaptic to search for it). Other than my Python lessons, I don't use it all that often.

---

### Post by WeeWillyWacko on 2007-08-27
The basis of what you use boils down to how you were taught to use the computer. I know lots of folks who started on mainframes who think that the whole personal computer thing is a fad. I also know a number of *VERY* intelligent people who wouldn't be caught pointing and clicking. Ultimately, the human-computer interface has to make the next quantum leap. Neither remembering the entire command ref for Linux nor the exact sequence of stuff to point and click really get us where we need to be. I personally, point, click, kbd (shortcut), and command-line based on shortest path. Whatever method is fastest (and I can remember) is what I use.

---

### Post by DaveAK on 2007-08-27
Personally I hate using the mouse, it slows things down.  A good GUI to me would have to be easy to navigate using just the keyboard.  I want to know WHAT I'm doing, not just HOW to do it, and I think CLI helps with that.  As a newbie I'm having to learn a lot of stuff, and all these HOW-TOs with their commands are helping me to do that.  I'd like to learn alot more keyboard shortcuts to use from the desktop, they're fantastic time savers, I use them all the time in Windows.

ETA: Oh, and I vary rarely read an entire thread that's this long. :D  So ditto what WeeWillyWacko said. :)

---

### Post by g2g591 on 2007-08-27
I gotta agree, because once you learn the basics of the command line, you fix your system far more easily (like when you must reinstall windows and it takes over your mbr, or another distro uses their own boot menu)

---

### Post by extremenachos on 2007-08-27
so, I installed Ubuntu a few days ago, and other than tripping up my XP install, I'm really impressed with the professional quality of the OS. I've never used Linux before, so this being my first foray into using the terminal window, I really am struck at the unneeded complexity it brings.

I grew up with a Mac, switched to Windows during 98, so I never needed DOS. So why the heck do you need a terminal window in Linux? why can't I just double-click an installer and let it install the files where they belong? why doesn't Ubuntu come with a manual on how to work in the terminal, maybe a little tutorial or at least a crib sheet. 

Trying to get software to install in Ubuntu (i.e. flash player) is more frustrating than any problem I have ever dealt with in Windows. Honest to god! Seeing Linux using a terminal reminds me of how smug  MS-Dos users about their DOS skills. 

Can somebody please explain to me why Linux needs a terminal window before I give up on it all together!

---

### Post by Nekiruhs on 2007-08-27
This surprises you? Macs still have a terminal too you know. And a functional console was one of Vistas major selling points. Any reason Synaptic didn't work for you? Its under System > Administration > Synaptic Package Manager.

---

### Post by Seti on 2007-08-27
A terminal is a wonderful way for those of us that know how to execute commands directly using GNU utilities and talk directly to the linux kernel. Although you can do just about everything using the GUI in most modern linux distros, the CLI is still a very nice option to have. 
Nobody is telling you that you HAVE to use the terminal to do stuff. Over time, however, if you have any interest in learning how to do stuff in the terminal, you will find it very liberating, trust me.

---

### Post by picpak on 2007-08-27
> **extremenachos said:**
> Trying to get software to install in Ubuntu (i.e. flash player) is more frustrating than any problem I have ever dealt with in Windows. Honest to god! Seeing Linux using a terminal reminds me of how smug  MS-Dos users about their DOS skills.

[Installing Flash is easy](http://ubuntu.freehostia.com/guides/addremove/#flash).

We don't use the terminal for instructions because we're smug, it's because people use different desktop environments (Gnome, KDE, Xfce, etc) and doing so ensures that we support all of them. It's also quicker and less error-prone to copy and paste instructions than to point-and-click.

If you don't want to use the terminal for installing software, you can use System > Administration > Synaptic Package Manager or Applications > Add/Remove.

---

### Post by Paul820 on 2007-08-27
You don't need to use the terminal all the time, most software can be installed through synaptic, or clicking on a deb file. The terminal is a very powerful tool to communicate directly with the kernel. Here is a link to teach you some commands [http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

I'm not a expert on the terminal so some other guys/girls could tell more. Don't be put off by it, once you learn some of the commands it's very easy to use. I am learning it and i think it's really good.

---

### Post by Pancetilla on 2007-08-27
Why not?

I'm clumsy with the mouse, I prefer apt-getting. It is much faster and you have more control. My terminal starts automatically every time gnome starts.

---

### Post by Henry Rayker on 2007-08-27
CLI is an amazing tool that accomplishes things you could not possibly (without an ungodly amount of complexity) do in a GUI. Sure, installing things can be daunting, but once you learn that a vast majority of packages can be installed by:

cd /location/of/tar
tar -xvf nameoftar.tar.bz2
cd nameoftar
./configure
sudo make install

You will be fine.

---

### Post by stimpack on 2007-08-27
Linux shells are not comparable to DOS. Linux shells are insanely powerful in the right hands. They also better for batching and automating tasks than GUIs

However!, you don't need to do much in a shell if you dislike them. Most things have a GUI frontend.

For installing software, look at Synaptic in Ubuntu or Adept in Kubuntu.

---

### Post by 23meg on 2007-08-27
> so this being my first foray into using the terminal window, I really am struck at the unneeded complexity it brings.

If you find the complexity it brings unneeded for your needs, don't use it.

> why can't I just double-click an installer and let it install the files where they belong? 

You can. Try double clicking a deb file.

> why doesn't Ubuntu come with a manual on how to work in the terminal, maybe a little tutorial or at least a crib sheet. 


It does: System / Help And Support / Advanced Topics / Using the Command Line

> 
Trying to get software to install in Ubuntu (i.e. flash player) is more frustrating than any problem I have ever dealt with in Windows. Honest to god!

Beside the fact that you *can* install Flash in the exact same way as in Windows, many tasks are handled differently, since this is a different operating system. You'll have to do some unlearning and relearning.

> Seeing Linux using a terminal

Linux doesn't and can't use a terminal; you may choose to use it, or not to use it.

---

### Post by Dragonbite on 2007-08-27
I've gotten 99.9% of the functionality out of my Edubuntu without even touching the command line.  The only time(s) I have is more by choice than by necessity and the time it was necessary it wasn't Ubuntu or Linux, it was Cisco and their VPN client.  Since it isn't something in the repositories (I tried all the others, nothing worked) I was trapped by what Cisco gave me which was bare-minimum.

---

### Post by extremenachos on 2007-08-31
Well I'm glad to see so many responses to my thread. Thanks everyone, though it seems this forum is use to Linux bashers. 

I think my view of the command line is similar to the whole notion of 'elite Speak', its kind of a self-satisfying, self-congratulatory way of showing off your computer skills. Everyone who responded to this thread comments that you have more functionality, but didn't exactly note any specific gains from (excluding a vague reference to talking directly to the kernel). I think that this is a very telling observation.

I think the trouble here is that Linux/Ubuntu is going to need to dumb it down for the masses if we ever want to see a large enough number of PCs switching to Linux; Which is a good thing because that means that Microsoft will have to respond to the completion by not releasing crap like Vista.  the Add/Remove and Synaptic is a great idea, but I think the terminal needs to be completely removed from the picture.  


And the problem I was having with Flash was that it's not compatible with Ubuntu 64. 

but still, I'm completely impressed with Ubuntu.

---

### Post by fuscia on 2007-08-31
if you're having trouble with something, it's a lot easier to copy&paste a few commands into a terminal than to have the poor helper have to go through a whole pile of illustrations of gui solutions. all you're really experiencing now is unfamiliarity. once you realize how easy it is to enter commands someone else wrote, you'll appreciate the benefit.

---

### Post by toupeiro on 2007-08-31
I think its important to note for the sake of relevance, 

Linux is a Command Interpretor based operating system that happens to have a GUI.  Without the CLI, there would be no gnome, kde, or anything else.  This separation adds a dynamic that is pretty much lost in the windows world.  Sure, windows has a command prompt.  a linux OS IS a command prompt, gnome is a suite of X11 applications.

So, asking why Linux needs a terminal window is kind of like asking why windows needs a GUI. :)

Command line tools give you the added abilities of batch processing, stringing several completely independent commands together,  and very easy text input, output manipulation that can be cumbersome in a GUI.  also, when a GUI freezes, you have a completely separated layer to work on and fix your problems, most times without rebooting.  They also streamline and make efficient, tasks that do not require the overhead of a GUI interface, so the performance of command line tools are usually better and more resource efficient. 

We're in an age where routers and switches are configured by housewives and 10 year olds, and Jr. High Schoolers are coding in XML on their personal blogs...  I think dumbing down is the last thing needed.  Microsoft Windows vista is the result of what happens when you "dumb down" an operating system.  I invite you to use if if thats what you feel you need.

---

### Post by stmiller on 2007-08-31
Linux existed as a text-only operating system at first (the same as early MSDOS, and Unix).  So the fundamental roots of the operating system are ones that are completely text / command line based. It is on top of this base that we have nice desktop applications now. (Or you can still only have a text-based install of Linux!)

Early graphical 'X' windowing systems looked like this: (we've come a long way!)

[http://en.wikipedia.org/wiki/Image:X-Window-System.png](http://en.wikipedia.org/wiki/Image:X-Window-System.png)

---

### Post by Spr0k3t on 2007-08-31
> **extremenachos said:**
> And the problem I was having with Flash was that it's not compatible with Ubuntu 64.

There are two ways around this problem.

[list]
[*] 32bit browser with 32bit plugins
[*] 64bit browser with 32bit plugins using 64bit wrapper classes
[/list]

I prefer the later method; however flash is not extremely stable and can crash some times.  The result of this is flash will just not work.  The way to fix this is to close the browser and load it back up.

Installing 32bit flash with a 64bit browser.  I used Kilz install script and haven't had a problem outside of the above mentioned. ([http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924))

From what I've seen though, installing 32bit plugins (such as flash) is cake with the 32bit install.

As for Linux bashers... I'm fairly sure we've heard them all.  Feel free to stick around and ask any questions you may have.  If you want a particular application and don't know the linux counterpart for it, drop a note, as I'm sure someone may know of one.

---

### Post by Celegorm on 2007-08-31
> **extremenachos said:**
> I think my view of the command line is similar to the whole notion of 'elite Speak', its kind of a self-satisfying, self-congratulatory way of showing off your computer skills. Everyone who responded to this thread comments that you have more functionality, but didn't exactly note any specific gains from (excluding a vague reference to talking directly to the kernel). I think that this is a very telling observation.

Unlike leet speak, the terminal is actually vastly useful. I'm sure there are those who use it to brag about their skills, but personally, that's not something that ever even occured to me to brag about. In fact, one time I asked a mac using friend if he ever used the terminal in OS X and was surprised at his response "Oh no, I'm not *that* advanced a computer user." because it revealed his perspective of viewing terminal usage as something difficult or amazing that real experts and computer nerds do, whereas I view it as something common place that most linux users do. I suppose it was a bit misguided to think it likely that non-nerd mac users would use the terminal just because their OS is unix-based now, especially as most "normal" computer users (and even nerds) tend to be intimidated by the terminal if they've never used it before. Using a terminal is not actually that hard, once you've taken a little time to get used to it.

Being able to use the terminal whenever I want is actually one of my favorite things about linux, more so the longer I use it. I feel as if I have a lot more control over things when using a terminal, and that I better understand what is going on than I do when just clicking things in a GUI. In menus and control panels, you can only put so many options, but a CLI allows you tweak (using options) and combine things (using the pipe) in so many ways, and when something generates an error, the terminal often gives useful error messages, whereas a GUI application (unless you started it from a terminal) won't necessarily tell you what went wrong when it crashed or something went wrong. I'd explain more about why the terminal is so cool and useful, but I have a feeling this post would turn into more of a command line tutorial if I did so.

---

### Post by slavik on 2007-08-31
> **extremenachos said:**
> so, I installed Ubuntu a few days ago, and other than tripping up my XP install, I'm really impressed with the professional quality of the OS. I've never used Linux before, so this being my first foray into using the terminal window, I really am struck at the unneeded complexity it brings.

I grew up with a Mac, switched to Windows during 98, so I never needed DOS. So why the heck do you need a terminal window in Linux? why can't I just double-click an installer and let it install the files where they belong? why doesn't Ubuntu come with a manual on how to work in the terminal, maybe a little tutorial or at least a crib sheet. 

Trying to get software to install in Ubuntu (i.e. flash player) is more frustrating than any problem I have ever dealt with in Windows. Honest to god! Seeing Linux using a terminal reminds me of how smug  MS-Dos users about their DOS skills. 

Can somebody please explain to me why Linux needs a terminal window before I give up on it all together!

1. Right tool for the right job. There are things I can do in a terminal that will take ages to do in a GUI
for example(not, find syntax is most likely wrong):
find -atime 1 . | xargs rm #remove all files accesses a day or more in the past.

2. once you unpackage adobe's file, you have the choice of running the shell script without opening a terminal. but why are you doing that anyway? the repo should have flash-nonfree :)

here's another goody (in perl):
cat /etc/passwd | perl -ne `s/^(.*?)(?::.*?)+:(.*?):.*?$/print $1."\t".$2."\n"/e;` #print all users in the system and their home paths/directories

there are things I've seen done to archived ticker files that takes like 5-6 lines of shell commands that take 2 minutes to write out. and no extra space needed :) (besides the buffering of pipes)

---

### Post by Henry Rayker on 2007-08-31
> **extremenachos said:**
> Well I'm glad to see so many responses to my thread. Thanks everyone, though it seems this forum is use to Linux bashers. 

I think my view of the command line is similar to the whole notion of 'elite Speak', its kind of a self-satisfying, self-congratulatory way of showing off your computer skills. Everyone who responded to this thread comments that you have more functionality, but didn't exactly note any specific gains from (excluding a vague reference to talking directly to the kernel). I think that this is a very telling observation.

If you compare the command line to elite speak, you've obviously got a LOT to learn. First of all, there have been clear examples given as to what gains you get. For example, explaining how to do something via the command line is much easier than trying to explain something via the GUI (because there are so many completely different desktop environments). Telling someone to give you the results of "lsmod | grep sound" is a LOT easier than describing every single possible way that any desktop environment could give you to get to the hardware and separate the sound from that. By the way, that was a complex use of the CLI. First, lsmod shows the modules loaded in the kernel. The output of this is piped into grep which searches for the string "sound". The total command returns only the lsmod entries with the string "sound" contained in them. Is that harder than, say, describing every possible desktop environment's method?

The issue I explained above is partly due to the fact that Linux is, at its heart, very modular. Because it is so modular, people will and have made different desktop environments to suit their needs. Gnome, KDE, XFCE, E17, fluxbox, etc. all bring something unique to the table and excluding one in favor of another is just asking to have your head bitten off. The command line is universal, the command line is fast, and the command line is efficient.

I work in a silicon design center for a major semiconductor company. At least 50% of my work is all done within the command line or with a very simple text editor (I'm finally getting used to vim...recovering nano addict). The only other software I really use are layout and schematic suites, as well as a waveform viewer. Due to their graphical nature, they are obviously going to use a GUI, but most of the interface is with keyboard shortcuts. I hate to break it to you, but the ENTIRE group uses almost an identical set of apps. We don't do it because it is self-satisfying, we do it because it is faster and more efficient and more powerful. Sure, we may be outside of the mainstream, but honestly, life is SO much easier if you understand the command line.

Another very useful aspect of the command line is mixing it with perl. You would be shocked with the types of things you can do with a simple perl script (for example, re-encoding your entire music collection with a single command, or reformatting your music collection's titles...the possibilities are endless)

---

### Post by slavik on 2007-08-31
another thing I wrote in perl:
1. script to get all "seen" members in a windows domain/workgroup
2. parse the names given by #2 and find the computer's IP and MAC address

I work where we have to support over 500 Windows XP workstations. And we reimage them at least twice a year. The automation factor is a biggie because of the way we assign unique computer names and active directory accounts to every station, which also includes a way for the department handling the network to identify on their terms and we can map it to a real physical system instead of something on port xyz.

---

### Post by PartisanEntity on 2007-08-31
It's much easier to tell someone to type: cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup in the terminal than to say: "Click on the round thingy icon, oh you have a different icon set? Then move than file with the number on it, oh you don't have that?". :)

---

### Post by AndyCooll on 2007-08-31
I have come from a Windows background having never used the command line. I'm not a programmer either. And I too prefer to use a gui wherever possible. 

I've grown to appreciate the command line for the power, control and flexibility it can bring to your handling of your OS. I see it as being given an extra choice. I never need to use it if that were my preference. However there have been quite a few occasions where I've started a task using a gui and then switched to the command line because it was less complicated.

For instance, we have a couple of old laptops that when doing an update the update app seems to hang when putting in my admin password. Instead I just go to the command line and type "sudo apt-get upgrade" and the job's done.

In a more advanced mode, on the laptops I usually use XDMCP and login to my faster pc which is sitting in the loft. XDMCP is great for that, as it works as if I'm sat at the fast pc. The one downside is that XDMCP doesn't have the capability to send sound across the network. And I like Amarok. So to play music via Amarok using a remote machine, after I've logged in to my fast box I use the command line to ssh back in to the laptop I'm actually using and then type "amarok". This then opens up the Amarok gui on the remote desktop (which is now being sent across my network and displayed on this laptop) but is still playing the sound on the local machine. Since the "local machine"  just happens to be the laptop I'm actually using I've now got both gui and sound! 
There might be simpler ways of getting sound on a remote machine using XDMCP that I don't know about, but this works for me.

:cool:

---

### Post by aysiu on 2007-08-31
I've merged this with the GUI vs. CLI discussion thread.

---

### Post by Jason.TJ.Johnson on 2007-09-08
For Cliff Notes (Quick Summary) Scroll toward bottom of post.


I'm fairly new to Linux. I've been around since early Dapper and I've loved it ever since. Ubuntu has piqued my interest in Linux. I've installed  Redhat, Xandros, PCLinuxOS, Mandriva (back when it was called Mandrake), Fedora Core, OpenSUSE, among others. I've always stuck with Ubuntu, nothing quite like it.

I was born in 84, started using computers back when DOS was the major things. Playing DOS games on my floppy drive and see if I could max out my 400MB hard drive. Because of this, and the fact that I didn't have anything else to do during the summer, I've become really comfortable with DOS. When I migrated over to Ubuntu, one of the first things I learned about was the terminal, and not because I chose to, but evidently it's the preferred method to do things around here. There's our problem.

Don't get me wrong, I love the terminal, I use it every day. I can't remember the last time I actually ran synaptic package manager to install something. For new comers, the terminal and every command to retype to use it in is scary. You have to understand that these people are coming from an OS where the closest thing to DOS they've probably seen was a BSOD and the POST process. All people really want to do is point and click, and check the occasional "I agree" box. Synaptic Package Manager has come a LONG way to help solve this problem, and so has Automatix, regardless of how much it isn't supported. A lot of new users come here to get help, and some of the first things they see is "Ok, in the terminal type "sudo apt-get blah blah" and people start getting a bit worried. Once they find out what the terminal is, it gets even scarier. Once they type "sudo apt-get install update" and see all those lines of text, all hell breaks loose.

Gutsy is also coming a long way to help minimize the use of the terminal, but what I think we need to do as a community is find a way to avoid using the terminal to do simple tasks. People like progress bars, next, next, yes, next and ok. At first, I didn't even know you could copy and paste into the terminal. I use to sit here and retype log as commands and hope I don't make a typo and screw the entire system. Is there anyway to turn these terminal tutorials into scripts? I know that if you copy more than one line of terminal code the terminal is submit each line waiting for the other process to finish. There must be a way we can make a ".bat" file or something, where a person would paste all the commands into it and watch the terminal perform it step by step, or better yet, just watch a progress bar.

Sorry for the long, cluttered, unprofessional post. I only got about 20 minutes of sleep last night.




======
**SUMMARY**

To help new users stay, we should, as a community, keep from telling new users to use the terminal to do anything as much as we possibly can. Maybe even develop software that automates tutorials that uses the terminal.
======

---

### Post by Tomosaur on 2007-09-08
The terminal is really just one big scripting engine. It is entirely possible to just have the user download a script to do X task - but not all users have the same problems, and we need specific information from them to solve whatever problem they're having in many cases.

This topic comes up time and time again - and every time, we tell them the reason why we show them the terminal commands:

The terminal is uniform, the GUI is not. We don't know what your GUI is, we don't know if you've messed around with the menus, so on and so forth. It saves us time and effort to say:
```

sudo apt-get install build-essential

```

Than it is to say. "In your package manager (System > Administration > Synaptic Package Manager), type in your password, click the 'search' button, then type 'build-essential' and press 'ok'. Click the little box on the left of the 'build-essential' package, and click 'Install'. Click apply, and the software will download and install itself.

We don't really have time to keep typing the same stuff over and over again, posting screenshots or whatever. There are a million tutorials out there, and most questions of this nature have been asked, and answered, about a million times.

The simple truth is that people don't want to read, and barely ever use the forum search feature. With terminal commands, we can tell them what they need to know very quickly, and move on to the next person, while the user can simply copy and paste whatever the command is.

It's true that we need more GUI tools to do some tasks which users have trouble with frequently - and all we can say to that is that it's being worked on.

---

### Post by fdhdghdg on 2007-09-08
I think you are right (less terminal guides for the so called simple tasks) BUT most of these users are self-proclaimed computer experts already, probably the technical genius of their family. And they often try to install it on non-supported hardware, and they want the latest crap they just watched on youtube. So they find a bash script to do the job, eventually it breaks the system and the bitching and whining starts.

---

### Post by bigbearomaha on 2007-09-08
I have come to think of C/L operation as the "back door" way to get things done.

The C/L is no problem for me, I also come from DOS days and first started with early RedHat (5.1) and Mandrake, who pushed GUI as much as possible even then, but back then, that wasn't a lot.  I also learned on a big old mainframe running unix in high school, sitting at the good old terminal.

most  not all but most people age say 35 and under, have grown up the MS way, GUI all the way. or most of it.

Also, most people just USE a computer.  they want to read email, surf the web, do the checkbook, etc...

They have no desire or interest in working with or using what they think of as an "antiquated" method.

Geeks, hackers, techs, call us what you will, we have an interest to know how these things work
we not only want to get things done, we want to know how it's done and maybe, how we can make it work better.

Geeks ( I use the term respectfully, for  I fall smack dab into that classification) are very much the "minority" in the world of computer users.

There are many more "Joe average" users than there are geeks.

and it is the "joe average" users who demand a single,unified presentation of linux.  to simplify the instructions and make possible GUI solutions, because the GUI will be consistent then ( Thanks Bill)

As a tech and a small business network consultant, I make a point to know how to get around in many distros so that I can get a feel for which one will fit a certain clients needs best and I can then be best prepared to help them.

I don't expect or ask my clients ( joe averages by 90%) to know the C/L,  but no matter what they do to mess it up  (and oh lord are they good at that )  I know of a reliable "back door" to get in and fix it and make it "better".

Big Bear

---

### Post by 23meg on 2007-09-08
> 
To help new users stay, we should, as a community, keep from telling new users to use the terminal to do anything as much as we possibly can. Maybe even develop software that automates tutorials that uses the terminal.

Simply saying "select this line, open a terminal, middle-click and hit Enter" would go a long way in preventing the potential "terminal horror" that not all new users have. It's enough to make them feel, or tell them, that using the terminal to do things isn't compulsory, that it's simply the best way to give them help over the net.

---

### Post by aysiu on 2007-09-08
I'm appalled that people (with the exception of Recovery Mode, lack of an internet connection, or an X server crash) would ask new user to *type* a command. Typing will get the new user only frustrated... and likely to make a typo or forget about case sensitivity.

Copying and pasting is the way to go for terminal commands.

And if you want to know the benefits of recommending terminal commands, just read the thread I merged yours with.

We are a text-based support forum, so the support is text-based. If we were standing in the living room of everyone who had a problem, of course it'd be easier to say, "Click on that menu," etc.

---

### Post by bone2006 on 2007-09-13
I absolutely love Linux and made the switch and have been trying to install Linux on any system I get my hands on.

So I was at a friend's house who was having problems with his computer, so I suggested that he uses Linux.

I told him there's no viruses, no worrying about software with spyware, a system that runs faster with no antivirus taking up resources, more stable, better security and it's free. Plus I install swiftfox with opendns and he never saw his system run so fast, he was excited.

he wanted a dual boot system, which is what was setup, but he wanted the default operating system to be windows and if he wanted to get into linux he would select it when it boots up.  Easy enough.

So I open up the terminal type in sudo mouspad /boot/grub/menu.lst as the file come up.  What is that crap, your not telling me I have to start typing in commands in a black screen to use this system are you.  I told him no, but and that once this is setup he'll never have to touch it again.

But it has me thinking.  Most hardcore linux users prefer the command line, which I respect and understand, but if people are coming from Windows for desktop users, they aren't comfortable with opening up a terminal and typing in commands, they want 100% gui.

It makes me wonder, why aren't more things setup for ease of use for people who don't like to use the CLI?

I can gurantee that my friend wouldn't have flipped out if I would have just opened up a file manger, browsed to boot, then grub and then if I right clicked on the file and selected an option that says open in super user, he wouldn't have said a word.  He's used to editing file in windows, but he's never used the command prompt in windows.  

The look on his face was as if this is too geeky and he didn't want to learn/memorize commands.   The more and more I use the command line I absolutely use it.  But what's ironic is that people will tell you anything you can do in the gui, you can with the command line, yet it's not the opposite.

Almost 90% of the the "how to" here involve the command line, which is more than good enough for me, but I enjoy using computers and the command line.  Some of the people who I'm trying to get to use Linux aren't very computer savy.  The command line is beyond intimidating for them.  It's just very interesting that if we can do everything with the terminal then we should be able to do it with a gui as well, yet it seems that power users are more concern with themselves and other power users.

I honestly do believe a lot of windows users won't come to Linux until the day that the terminal can be used, but is not required. Maybe it's my ignorance, but out of the box I cannot accomplish a lot of tasks without the terminal.  I use the terminal every single day, but I just can't see a lot of people who use windows as a desktop use the terminal on a daily bases.

---

### Post by BigSilly on 2007-09-13
Well, I don't think it's "killing" Linux, as more and more are making the switch. But it's definitely a fair and accurate point otherwise: people just don't want to have to type commands in. Some old-timer PC users are willing to give it a shot and are a perhaps a bit more open minded, but there's no doubt the Windows generation doesn't want to use text based input.

Luckily with most modern day distros you don't really *have* to use it. It's a benefit if you can learn it, but not a complete necessity. Your mate should be fine.

---

### Post by Tomosaur on 2007-09-13
It's easier using the command line than the GUI - simple as that. Both for ease of support (the command line is - mostly - identical on every distribution of Linux, the GUI is not) and just general speed of use - the command line wins hands down.

While it'd be nice to have a GUI tool for everything, people do make too much of a big deal about using the command line. How often does it **need** to be used, seriously - and for the stuff you use it for, is it not true that you **could** do it using the GUI? Installing software? Synaptic. Editing files? Text editors. Configuring various parts of your system? Most common ones have GUI tools available.

So what we're left with is a handful of people who genuinely don't already have some GUI tool to do something, and a majority of people who have switched to using the command line for most things since it is so much faster and more flexible than clicking around on the screen. File management, editing files, system maintenance etc - they're ALL quicker on the command line - the only problem is learning the syntax, which is no different from learning which sequence of buttons to click.

The 90% of support requests which are solved by a command line solution could generally have been done using the GUI - but it's a pain in the backside telling someone how to navigate a GUI, especially if that person doesn't use the same desktop environment as you. Granted, there are quite a few problems which can ONLY be solved by using the command line - and all that can be said is that they're being worked on - eventually we'll have GUI tools for everything - not that it will matter, since it'll still be faster to use the CLI, and that is what many people will continue to do.

So no, I don't think the CLI is 'killing' Linux - particularly since Linux is still increasing in popularity despite the CLI still being widely used. What I DO think is that the more people watch The Matrix - the more they'll think using the command line for whatever purpose constitutes programming.

---

### Post by Nano Geek on 2007-09-13
> **BigSilly said:**
> Some old-timer PC users are willing to give it a shot and are a perhaps a bit more open minded, but there's no doubt the Windows generation doesn't want to use text based input.Hey, I'm young by most standards, and I can get along just fine in the command line just fine thank you very much. :)

But I disagree with the OP, nothing is killing Linux, and several people like the command line better for doing certain tasks, like opening files buried deep in the system.

Just remind your friend that Linux is not a better Windows. Although you don't have to run anti-virus or do defragments, it does have a learning-curve like anything else.

---

### Post by wersdaluv on 2007-09-13
I would not say that it is what is "killing" Linux. It could be what is making it hard for new users to switch to Linux.

---

### Post by mostwanted on 2007-09-13
> **bone2006 said:**
> I absolutely love Linux and made the switch and have been trying to install Linux on any system I get my hands on.

So I was at a friend's house who was having problems with his computer, so I suggested that he uses Linux.

I told him there's no viruses, no worrying about software with spyware, a system that runs faster with no antivirus taking up resources, more stable, better security and it's free. Plus I install swiftfox with opendns and he never saw his system run so fast, he was excited.

he wanted a dual boot system, which is what was setup, but he wanted the default operating system to be windows and if he wanted to get into linux he would select it when it boots up.  Easy enough.

**So I open up the terminal type in sudo mouspad /boot/grub/menu.lst as the file come up.  What is that crap, your not telling me I have to start typing in commands in a black screen to use this system are you. ** I told him no, but and that once this is setup he'll never have to touch it again.

But it has me thinking.  Most hardcore linux users prefer the command line, which I respect and understand, but if people are coming from Windows for desktop users, they aren't comfortable with opening up a terminal and typing in commands, they want 100% gui.

**It makes me wonder, why aren't more things setup for ease of use for people who don't like to use the CLI?**
I can gurantee that my friend wouldn't have flipped out if I would have just opened up a file manger, browsed to boot, then grub and then if I right clicked on the file and selected an option that says open in super user, he wouldn't have said a word.  He's used to editing file in windows, but he's never used the command prompt in windows.  

The look on his face was as if this is too geeky and he didn't want to learn/memorize commands.   The more and more I use the command line I absolutely use it.  But what's ironic is that people will tell you anything you can do in the gui, you can with the command line, yet it's not the opposite.

Almost 90% of the the "how to" here involve the command line, which is more than good enough for me, but I enjoy using computers and the command line.  Some of the people who I'm trying to get to use Linux aren't very computer savy.  The command line is beyond intimidating for them.  It's just very interesting that if we can do everything with the terminal then we should be able to do it with a gui as well, yet it seems that power users are more concern with themselves and other power users.

I honestly do believe a lot of windows users won't come to Linux until the day that the terminal can be used, but is not required. Maybe it's my ignorance, but out of the box I cannot accomplish a lot of tasks without the terminal.  I use the terminal every single day, but I just can't see a lot of people who use windows as a desktop use the terminal on a daily bases.

Compare having to use the terminal on Linux to change which OS to boot first vs. not being able to do that at all on Windows. I don't see any problem here.

---

### Post by LowSky on 2007-09-13
This issue doesn't occur with Mac users. Go to an Apple store and look at all the people who show up with their Macs so that a store technition can install their new programs or set up certain things most of them do not want to learn. That why each new version of OS/X becomes less terminal required. Most people gave up command lines with MS-DOS. From Windows 95 and on most people have not needed to know a Command line.

I really think Linux needs to be more GUI intensive in relations to letting a user select everything with a mouse cursor. Personally I like the terminal, I can actually see what is being done. With a GUI interface like windows instalations I have no idea what it is actually doing. On the flip side sometimes I just want thing to just click and work, and I think most people want this 99% of the time.

What I really want is a easy way to install software. I dont want to learn how to recompile a program originally designed for a rival linux version. I want it to install and put an icon into application menu or on my desktop.

---

### Post by blithen on 2007-09-13
> **BigSilly said:**
> Some old-timer PC users are willing to give it a shot and are a perhaps a bit more open minded, but there's no doubt the Windows generation doesn't want to use text based input.

I LOVE the Command Line.
Heck, my music player is there. (cmus)
And I'm 16. Now you didn't specify the age group. but if 16 happens to be in there, I defiantly would before the Command Line, over the GUI. :D
A lot faster. For the OPs example of 'sudo mouspad /boot/grub/menu.lst'
That's  a lot faster then using the GUI.
But I could use the GUI, just would take more time.

---

### Post by Eddie Wilson on 2007-09-13
All in all the command line doesn't have to be used. If you want to compare the distro with windows you also have to use the command line in windows to do certain things. You do not have to use the command line to edit the grub menu. Just tell the people that its there if they want to use it but that they don't have to. Myself I like the command line but I know a lot of people who don't. Most people after a while will start to explore the power of the command line and its use will  increase from  there.
Thanks, Eddie

---

### Post by notwen on 2007-09-13
If ppl don't want to acknowledge the CLI is present and running underneath their beloved GUI and are scared at the sight of it, then Linux may not be for them.  There are tons of alternatives to CLI, but what is alway going to be present should you need to do something manually and edit it, CLI is. =]  CLI is one of the major reasons I enjoy Linux.  Sure I'm all for Linux being a OS for users coming over from OSX or Windows, but they have to be open-minded enough to not be intimidated by the CLI.

---

### Post by aysiu on 2007-09-13
(I've merged this with the GUI v. CLI thread.)

*Showing* someone the command-line as a first introduction to Linux would certainly be a bad way to sell it to most users. *Using* the command-line because you personally prefer it or because you're helping someone in a text-based online forum is a different story.

The best way to do it would be to take the computer away, install and configure Ubuntu out of sight (the way OEMs would for Windows or Ubuntu) and then present it to your friend. "Here it is."

To be fair, though, you wouldn't edit the registry in front of someone as an introduction to Windows... or edit a .plist file in Mac OS X as an introduction to Mac.

---

### Post by nvteighen on 2007-09-13
I think the lack of CLI is dangerous and it's what has killed Windows... quite a paradox. In Win 3.x, if you had a problem, you could run to MS-DOS and solve it from there. In GNU/Linux, if X or GNOME or any GUI app makes something weird  (hey, it occurs), you can run into console and kill the problem down... In Windows 9x/Xp/Vista, when you have a problem, as the GUI is almost the system itself, you must reboot.

But also, there's another thing. Apologize me if I may sound a bit "elitistic", but IMHO people that know how to use CLI know better what a computer is and does: a machine designed to receive orders and perform them. You type "top" in Terminal (or any other command you like) and you get what you wanted...  People that only have used GUIs, are used to message boxes asking them for things (a computer telling the user what to do!... something in CLI almost doesn't exist), they usually don't understand commands, just know "where" it is located... and think that the prettier the GUI the better the OS (something MS exploits a lot, of course)...

Of course, there must be both: GUI and CLI, but you must give CLI total power. But only-GUI systems have made people a bit more ignorant on computing and, thus, less conscious of what you shouldn't do.

---

### Post by bone2006 on 2007-09-13
mostwanted you have a valid point.  Linux has so many advantages over windows and linux gives you the option to dual boot, now ubuntu even brings over your documents.  Windows just doesn't care about customers, while linux is customer driven since the customers are the users.

It would be nice though if every instructions could be done via a gui or maybe it can but the instructions are always using the command line.  It's not if I like  or love or hate the terminal I think having more users coming over to linux is good for the community and the more we can do via gui the more that will come over.

I've had friends try linux and go back and I believe somethings are ignorance about not being able to install this or run this program.

But I have a friend who is almost computer illiterate in my option.  He is now on the computer a lot, but he called me once for help on windows and I was telling him to copy and paste a file in a directory.  His words were, ok I'm right clicking on a file and a menu comes up, do I right click or left click on the menu to select the copy option..............I'm not kidding........... these little things we take or granted.  Linux and windows follow some basic fundamentals, which this guy really only uses a browser most of the time.

I've thought that linux would be better for him, better performance, firefox and he would be more secure and have a faster system.  But then I started to think I really don't want to be on the phone telling him to open up a terminal and type in sudo then this then that.  I'll probably spend 20 minutes telling him the word is sudo and not something else.  Yet I do believe it would be easier for him if there was just a program to open up and do a few steps.

I think the problem is that people feel that they like something that everybody should do it that way.  I love linux and I think everybody should use linux, but who am I kidding myself.  The terminal scares people and you can't even does

---

### Post by Tomosaur on 2007-09-13
> **bone2006 said:**
> 
I think the problem is that people feel that they like something that everybody should do it that way.  I love linux and I think everybody should use linux, but who am I kidding myself.  The terminal scares people and you can't even does

Well why should the GUI users tell us what to do? We know the benefits of using the CLI - if they don't, then that's their problem. As mentioned before - the stuff the vast majority of people use the CLI for **can be accomplished** using the GUI. There is very little which cannot. The GUI is just inefficient eye-candy for the most part, and while nobody's denying that it makes computers more friendly, it also slows those users down who know what they're doing and don't want to be hampered by clicking about when a single command would suffice.

We need both GUI and CLI, and this is what Linux has. The reason we tell everybody commands to perform some function is because telling them where to click is slow, prone to error, and just plain annoying - NOT because the task can't be done in the GUI.

---

### Post by nvteighen on 2007-09-13
Also, beware that to give GUI instructions for example in these forums is absolutely unpractical. When you give commands, you don't have to care what locale or desktop envorinment is the user using: CLI is a great lingua franca!

---

### Post by bigbearomaha on 2007-09-13
I originally posted this in response to a similar thread in Mint,  I think it fits here as well.


> The real question for me is,  why do people use computers? 
 
To get thing done.  to accomplish tasks and perform services that will likely assist getting a certain job done. 
 
What is an OS for?  for people to interact with the computer in able to perform said tasks and services. 
 
I don't think anyone would argue, one of the primary reasons windows is success is because it "tries" ( doesn't always succeed, but it tries ) to make those tasks and services as simple as possible. 
 
One could even go so far as to say, an OS's primary role is not just to provide interaction with the computer, but to facilitate that interaction. 
 
One of Windows greater failures is that it doesn't allow those people who need or want access to the "guts" of the machine or, to use the infamous auto reference, it locks the hood. " Sorry, you can't do that tune up yourself, got to have permission from the factory to do that. sucks to be you." 
 
Why, because many people have the interest to work on their own car or computer. to make it go faster, or pull more weight, or carry a heavier load, etc. 
 
Things that the people can learn to do that will save them money and make their car/computer customized to their specific needs. 
 
Now, do all people want to be a mechanic/tech just to have their car/computer "customized/optimized?Of course not. BUT , we want to know it is possible, because maybe, I have a neighbor who is mechanically inclined/computer oriented who might "trade me" He'll work on my car/computer and I'll frame up his new deck ( cuz I'm a framer/carpenter maybe). 
 
At least I know, even though I am not going to work on that computer myself, it can be done easier and cheaper than going back to the factory. 
 
SO. what do I want Linux, a computer OS to do? I want it to facilitate and help me, as easily and directly as possible, get my tasks/work done on it. 
 
I am willing to learn how to work with the computer, I just shouldn't have to be a tech to learn how to use a word processor. 
 
( note. I am one of those computer oriented people who likes to work on computers, but I know that there are many many more people who are exactly as I describe, my wife and kids among them. My clients are people who want to use a computer, not be the tech for it just to type letters or print images.) 
 
That's what I think people Use Linux, to have a better way to **use** a computer. How does this relate to the GUI/CLI issue?  both are interfaces.  and it's about choice and comfortability.

If you are comfortable with the idea of using C/L and feel it's more efficient for you and you don't think you need that much facilitation, by all means use the Command Line.

If you are more comfortable in a graphical presentation and prefer to have your user experience facilitated, the GUI is probably going to provide a better user experience for you.

There are those who have said that there should be no C/L, I strongly disagree with that as much as I disagree with not providing a "full-blown" GUI environment.  I think they are both of great value, even necessity.  people will choose the environment that allows them to be the most productive.

just my two cent, 
 
Big Bear

---

### Post by eentonig on 2007-09-13
The drive for a omni-present GUI is good. (Redundant in my opinion, but good)  Because it will allow noobs and housewifes to get to use the computer. But don't be fooled. Even with the best of best of GUIs, housewifes, noobs and bosses will always rely on some 'techie' to put the nuts and bolts together. 
Most of the calls I get from friends and family regarding their windows problems, they could easily solve themselve. If they were just brave enough to read those damn popups. 

People who are interested in evolving and growing, will get to know and appreciate the CLI. People who aren't interested, will be able to stick to the GUI and use their programs. And call their local 'techie' if anything extra needs to be done.

But in the rush for this full-blown, omnipotent, allmighty GUI... please don't canibalize the CLI. Or even text based configuration files.

In the old days (:mrgreen:) If I wanted to change something, I googled to find which was the name of the configuration file(s), opened it with vi or gedit and read the comments to find out what parameter I needed to alter to achieve my goal. A few weeks back, I tried the same for some gnome related thing (can't remember what is was). I found the file, opened it.... and couldn't figure out what to change, becasue comments were non-existing. That's a sad, sad road to go on. And if that's going to be the consequence of a GUI, I'd rather stick with CLI.

---

### Post by capink on 2007-09-14
I have not read all the posts in this thread. The point I want to add here is that I feel lucky I was introduced to linux at this time, when you still need to use the CLI. This made me discover the power of the command line. I still do most things using the GUI. But the command line is one of the reasons I prefer linux.

I think in the future, say two or three form now, new linux users will not hear about a thing called CLI. Everything will be done graphically and most of them will not be aware of the terminal. And that is why I feel lucky that I was introduced to linux now.

I hope that linux progams will be desinged with the same backend/forntend philosophy. Because that gives you the power of using the applications from the command line with all its power, and it also gives you the choice between multiple fontends that suit different needs. I hope that linux becoming mainstream will not take that away, this would make the applications just a replica of the windows programs, and it would take away form linux one of its most important strengths IMHO.

---

### Post by danny joe ritchie on 2007-09-14
I'm pretty much new too linux and I like the command line, all that pointing ,clicking and dragging crap in confusing!
 I never cared for Windows because of that garbage! I don't know why but I'd rather enter a couple of commands than to try and click my way thru a bunch of windows !

---

### Post by aysiu on 2007-11-26
The discussion appears to have picked up in [a new thread](http://ubuntuforums.org/showthread.php?t=623518).

---

