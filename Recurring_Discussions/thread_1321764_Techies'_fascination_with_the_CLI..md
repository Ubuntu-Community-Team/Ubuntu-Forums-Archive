---
title: "Techies' fascination with the CLI."
date: 2009-11-10
forum: Recurring Discussions
---

### Post by Marti68 on 2009-11-10
One of the Ubuntu Cafe I think.  Doesn't need a serious technical answer; more informed comment. ):P
 
What is the facination for Linux users with the CLI?
 
Answering "really powerful" won't help me understand.  What can you achieve that well written GUI can't?  GUI's have stood the test of time, are popular with many and make sence to  dyslectics; the main reason my partner considers my Ubuntu laptop an indulgence not a serious tool.
 
I recognise that I can copy lines of advice from here to a Terminal but I never remember anything so no advancement in my use of Ubuntu.  When I write handout for the office screen shots and a few words get read (sometimes)  An A4 page of text, however good, will be binned 19 time from 20.
 
So, what am I missing?  Why do you guys love it?[SIZE=1]
[/SIZE]

---

### Post by Tibuda on 2009-11-10
How does this makes your partner think that?

---

### Post by CharlesA on 2009-11-10
I am lazy and do most of my work with a GUI. (Webmin for admin of the different servers running on my machine)

However, if I need to remotely access my server it's easier (and faster) to just do whatever I need to from the terminal instead of starting the vnc server and doing it that way. It's nice to have access to the GUI if I need it.

For me, working at the terminal is easier for me for some things. Mounting partitons using fstab, changing ownership/permissions. Creating scripts.

---

### Post by snowpine on 2009-11-10
Many reasons, but I'll name just one: Ubuntu users can help Xubuntu/Kubuntu users. The GUI tools are different depending on your desktop environment, but the CLI tools are mostly the same.

---

### Post by wojox on 2009-11-10
The shell came before the gui. People are just use to it. I like to point and click, don't get me wrong. When you use a gui all your doing is secretly writing to the shell. 

Also when a problem occurs it's good to know you way around the command line. I use Ubuntu Server and it's all cli. Faster and less resources.

---

### Post by koleoptero on 2009-11-10
Imagine a programmer not having to bother with a graphical interface. Can you now imagine how refined and feature-full he can make that program with the same time it would take him to design a GUI? That's why it's powerful, and that's why at least I'm fascinated with terminal apps. Plus they use less resources, and tend to help me get things done more quickly.

---

### Post by aysiu on 2009-11-10
You may want to read this:
[GUI vs. CLI](http://ubuntuforums.org/showthread.php?t=167547)

---

### Post by Keyper7 on 2009-11-10
Are you going to question my "fascination" for moving the Gnome panel to the bottom, when my activities could be done with it in the top?

Are you going to question my "fascination" for my wallpaper when another wallpaper would be equally as easy on my eyes?

Are you going to question my "fascination" for my favorite food because other kinds of food would give me the exact same nutrients?

Are you going to question my "fascination" for my car's color because a car of a different color would work exactly the same.

See, when the mighty Flying Spaghetti Monster created mankind, he also gave us a little thing called "personal taste". And this "personal taste" thingie is kinda funny: it doesn't matter how you strongly you believe it to be the ultimate truth of mankind, it is not.

So, you see, there's a very easy explanation for your question. And it's basically: you and your partner are not Godlike-beings who dictate the course of mankind, and therefore no one is forced to agree that a CLI is better than a GUI just because you two think so.

And before you proceed with this "why you Linux users..." nonsense, let me just mention that a lot of Windows sysadmins [would not live without a CLI, either](http://en.wikipedia.org/wiki/Windows_PowerShell).

And a last note to your partner? Where did he take the idea that you *need* to use the CLI to use Ubuntu?

Yes, I'm bitter today. Bad mood.

---

### Post by doas777 on 2009-11-10
I'm down with either method, but if you are asking me for help, then I;m goning to give you cli commands, since I don;'t want to spend half an hour creating a click by click narrative with screenshots (that i have to crop annotate and upload), when I could have just said "open a terminal and paste 'sudo apt-get install ubuntu-restricted-extras'"

personally I switch depending on the task. gksu'ing gedit to open a config file is usually in cli than by gksuing nautilus, and then navigating to the file. that said, I use gedit because I find it easier to use than vi or nano. just go with what works for you.

---

### Post by dizee on 2009-11-10
The CLI is great but it annoys me when people give instructions with it straight away (I understand *why* but it's a bit intimidating for newbies and gives Linux a reputation for being more difficult than it actually is). Especially when there is a simple GUI tool to do the same thing (for example, adding software sources).

---

### Post by snowpine on 2009-11-10
> **dizee said:**
> The CLI is great but it annoys me when people give instructions with it straight away (I understand *why* but it's a bit intimidating for newbies and gives Linux a reputation for being more difficult than it actually is). Especially when there is a simple GUI tool to do the same thing (for example, adding software sources).

Copy, Paste, press Enter... it's not hard. :)

When I'm giving someone directions, I say "turn left on Main street"; I don't say "look for a sign that says 'Main Street,' put on your left turn signal, take your foot off the gas, apply pressure to the brakes, turn the steering wheel counter-clockwise..." In other words, when I help somebody on these forums, I assume they know how to open a terminal and use the copy and paste functions (or can type accurately). If it's an absolute beginner who has no idea what the terminal is, I am happy to explain, but I don't preface every posting with a disclaimer about what the CLI is and why I've chosen to use it.

---

### Post by doas777 on 2009-11-10
> **dizee said:**
> The CLI is great but it annoys me when people give instructions with it straight away (I understand *why* but it's a bit intimidating for newbies and gives Linux a reputation for being more difficult than it actually is). Especially when there is a simple GUI tool to do the same thing (for example, adding software sources).

I can understand that, but you will find far fewer people willing to take the time and trouble to help you if they can't respond to it with one command in less than 30 seconds. cropping and uploading screenshots is a real pain, and asking volunteers that are trying to help you to go to that extent is expecting a lot.

---

### Post by RiceMonster on 2009-11-10
> **dizee said:**
> The CLI is great but it annoys me when people give instructions with it straight away (I understand *why* but it's a bit intimidating for newbies and gives Linux a reputation for being more difficult than it actually is). Especially when there is a simple GUI tool to do the same thing (for example, adding software sources).

Not everyone is out to convert everyone and prove Linux is easy to use.

---

### Post by blur xc on 2009-11-10
Say, for example, you ask a question on the forums, and there are two ways of doing it.  The cli way, or the gui way-

cli way-
ping -c 10 192.68.1.1 

gui way
Go to system -> administration -> network settings .... etc....

cli way-
sudo fdisk -l

gui way-
I don't even know how to get hte same information from the gui

cli way- 
chmod -R g+w /home/shared

gui way-
Again, don't know how to do that in the gui

I dunno- I'm pulling examples out of my ***.  For each thing in the gui, you need to navigate through several menus, interfaces, sub menues, etc.., and even then, the information you need is might not all be shown.  In the cli, as long asy ou nkow the command, just type it in.  And once you learn some bash shortcuts, like ctrl+(left and right arrows) to skip by word, up arrow to repeat a command, !! to repeat last command, etc.., it just gets faster.  And I'm just a beginner...

BM

---

### Post by Tibuda on 2009-11-10
> **blur xc said:**
> cli way-
sudo fdisk -l

gui way-
I don't even know how to get hte same information from the gui
GParted?


> cli way- 
chmod -R g+w /home/shared

gui way-
Again, don't know how to do that in the gui
Nautilus and Thunar can edit permissions for files and folders, if you right-click the file and click "properties". I guess PCManFM, Dolphin and Konqueror can too.

---

### Post by NoaHall on 2009-11-10
I, personally, find the cli is much, much easier, and much, much more powerful. It's also a lot easier to tell someone how to fix something from the cli.

---

### Post by ZankerH on 2009-11-10
> **dizee said:**
> The CLI is great but it annoys me when people give instructions with it straight away (I understand *why* but it's a bit intimidating for newbies and gives Linux a reputation for being more difficult than it actually is). Especially when there is a simple GUI tool to do the same thing (for example, adding software sources).

How is it intimidating to open the terminal and paste what you're told to? 

Seriously, what the **** is it with people being "afraid" of the terminal? What's so damn scary about it? When I started using Linux (around 1998), almost everything was done with the terminal, and one of the first things I did after installing it was print out the bash and vim manuals. If more people did this today, and actually took some steps to learn the OS they want to use, we wouldn't be having half as much trouble with clueless new users.

---

### Post by blur xc on 2009-11-10
> **danielrmt said:**
> GParted?



Nautilus and Thunar can edit permissions for files and folders, if you right-click the file and click "properties". I guess PCManFM, Dolphin and Konqueror can too.

Can it do it recursively to all the files and subfolders of a given folder?  If it does, that's great, but ti's another gui to learn, where if I'm already at a command prompt (super+T on my computer), I can just do it in the time it takes a gui program to launch.

And in each of those examples I listed, you would need to dig through a few menus and launch a separate gui program for each job, where you can do them all in a few seconds from the same terminal window.

BM

---

### Post by RiceMonster on 2009-11-10
> **blur xc said:**
> Can it do it recursively to all the files and subfolders of a given folder?

I *think* you can. I'm pretty sure I did it once, though I pretty much never change permissions with a GUI.

---

### Post by doas777 on 2009-11-10
> **RiceMonster said:**
> I *think* you can. I'm pretty sure I did it once, though I pretty much never change permissions with a GUI.

there is a button to do it, but it very rarely works.
also usually when I change permissions i have to change the owner group, somthing that is almost impossible in most cases via a gui. I think i'm gonna write a frontend for chown to integrate with nautilus, as my first shot at oss coding.

---

### Post by Mornedhel on 2009-11-10
> **Marti68 said:**
> Answering "really powerful" won't help me understand.  What can you achieve that well written GUI can't?

It *is* really powerful... It's also faster. You get access to more low level functionality. You can automate stuff. You get more feedback on errors.

The most powerful file search utility (document indexing is a different matter) was, and still is, GNU find. No other search utility comes close to it. What would a well-written GUI to find be ? If you want it to be just as useful, you'll have to include all options, with text fields to enter arguments, checkboxes... basically just as much work to do as crafting a find invocation, and you don't get to pipe your results. How do you even pipe output from a GUI application to another ?

> **Marti68 said:**
> GUI's have stood the test of time, are popular with many and make sence to  dyslectics; the main reason my partner considers my Ubuntu laptop an indulgence not a serious tool.

Where did you get the idea that GUIs have stood the test of time ? Did you mean "the general concept of GUIs has stood the test of time" ? Then I'll have to contradict you. GUIs (as the general concept of "pretty pictures that make it easier to visualize what's going on in your computer") have been around for less time than the CLI has.

Don't GUIs change ? There was an uproar when the ribbon was introduced in Office. Gnome is currently undergoing a major GUI redesign; the command-line tools won't change.
 
Also, I don't know why people say that they can't remember commands and arguments in the terminal. You don't have to. All you have to remember is apropos and man. There's just as much remembering involved when dealing with GUIs, only you have to remember "go here, click this, check that, Apply, go to the menu there, etc." instead of "sudo foo --bar --baz". I have no idea if it's a matter of visual vs. textual memory, or whatever (if such a thing exists), but I for one think that there's less to remember in the CLI.

---

### Post by howlingmadhowie on 2009-11-10
what i like about the cli is that it's so incredibly powerful.  just today i was asked how many lines of code i'd programmed in the current project. i wonder how you'd do that from a gui? i imagine you'd have to open every file and count the numbers of words individually and then add them up.

the cli is enormously powerful.  i also find it clearer than a gui.  i just don't trust guis anymore, and i tend to check on the command line that a gui has done what it promised to do. a shell is also a programming language so you can write for-loops and stuff which would be impossible to do with a gui. i often find myself, for example, renaming and moving files according to a regular expression. i dunno any gui which allows that.

---

### Post by Tibuda on 2009-11-10
> **doas777 said:**
> there is a button to do it, but it very rarely works.
also usually when I change permissions i have to change the owner group, somthing that is almost impossible in most cases via a gui. I think i'm gonna write a frontend for chown to integrate with nautilus, as my first shot at oss coding.

Thunar doesn't have such button.

---

### Post by Chronon on 2009-11-10
Because with CLI programs you can easily write scripts that automate complex actions.  Instead of sitting at a spreadsheet program and importing delimited-text files one-by-one, selecting data ranges, choosing plot type, setting axis labels, etc. for like 10,000 files individually, I was able to write a script that did all of the processing without user intervention in about a day.

If I don't need any automation then GUI is great.  For repetitive tasks that I would like to automate nothing beats the CLI.

---

### Post by dizee on 2009-11-10
> **snowpine said:**
> Copy, Paste, press Enter... it's not hard. :)

I'm not saying the CLI is hard!! Just that it makes Linux *look* geeky and inaccessible. Especially when we have a nice GUI tool to do the same thing. I'm not anti-CLI, I like it. Just saying. ;)

---

### Post by koenn on 2009-11-10
> **Marti68 said:**
> O
Answering "really powerful" won't help me understand.  
it's really powerfull - meaning that

* it does simple things really fast - see that example of recusrively setting  permissions

* it makes complex things easy - eg say you want to search through a directory tree, find all files by a given criterium (ag a partial filename match), and do something with those files if an additinal criteria is true - something like: find all my .htm files, rename them to .html, and if they contain certain urls, replace those urls with other ones.

* it makes it easy to exactly repeat things effortlessly. Say you've configured 1 computer. And you have to do a 2nd one exactly like that. If you've written down all the commands you used on the 1st one, you can just run those again. No GUI I know of lets you do that. 

* It's programmable. If those repetitive things you have to do are not exactly identical, but differ a bit here and there, you can use variables, if-then-else constructions, and other programming constructs. So you can automate stuff that otherwise yopu'de have to do by hand, over and over again.

* all of that is just text, so it's easy to document it (for your self), or put it in a script (so you can execute them hands-free), and post them on forums to  help others

that's powerful.

---

### Post by Tibuda on 2009-11-10
> **dizee said:**
> I'm not saying the CLI is hard!! Just that it makes Linux *look* geeky and inaccessible. Especially when we have a nice GUI tool to do the same thing. I'm not anti-CLI, I like it. Just saying. ;)

Then just don't use it. In most cases you don't have to use it. Mac OS X also have a BASH terminal just like Ubuntu, and is considered a very friendly OS.

---

### Post by doas777 on 2009-11-10
> **danielrmt said:**
> Thunar doesn't have such button.
another example of how the CLI instructions can be easily transmitted via forums, but the gui instructions cannot, because we are using two differant DEs to perform the same task. the cli is exactly the same though.

---

### Post by blur xc on 2009-11-10
> **doas777 said:**
> another example of how the CLI instructions can be easily transmitted via forums, but the gui instructions cannot, because we are using two differant DEs to perform the same task. the cli is exactly the same though.

That's a good point.  I hadn't considered with the massive variety of DE's available, one set of gui instructions would only be good for one DE.  Then some poor guy looking for help w/ another DE would be up a creek...  

BM

---

### Post by doas777 on 2009-11-10
> **blur xc said:**
> That's a good point.  I hadn't considered with the massive variety of DE's available, one set of gui instructions would only be good for one DE.  Then some poor guy looking for help w/ another DE would be up a creek...  

BM

or even just older versions of the same distro. I'd be in trouble if I was following a gui guide for dapper or edgy on karmic. the cli still probably works the same though.

---

### Post by Marti68 on 2009-11-10
WOW! Thank you for so many considered replies and well informed replies

To anyone irritated by the question Please read this with a smile.  You remember the smile.  It's the opposite of the face some of you use when barely tolerating dumb newbies.

The point about the differing GUI's makes a lot of sense.  The impatience with newbies is a double edged sword.  Expecting to be spoon fed information is selfish and so offering help in a format that is efficient for the knowledgeable helper makes good sense.  It does, however, clash with an atmosphere of "selling" GPL and Linux to a wider audience; even translating the GPL principles to other industries.  That may not be the prime goal of many but would appear to be the approach of Cannonical et-al.

Personally speaking, I'm learning the system by purchasing/downloading manuals and guides.  I'm not saying it's right; just right for me.  May even attend one of the User Groups that populate London's pubs \\:D/ 

...and again, Thank you.

---

### Post by lykwydchykyn on 2009-11-10
Imagine an instant messenger program that did not allow you to use the keyboard.  Instead, you went through a point-and-click menu-driven interface to select common words and phrases to send to the other participant.  Not only would this be exceedingly tedious, but in all likelihood it would be unable to support anything but the most trite and meaningless conversations.

It might be useful if you needed to converse with someone who only understood a language that you didn't; then your selected greetings, queries and responses could be translated automatically.  But if you both understood a common language, simply typing in the conversation is much simpler.

The same is true when it comes to GUI vs. CLI; only in this case, you are communicating with the operating system, not a person.  If you don't speak the language, then the GUI tool may be your only option -- but just like the menu-driven IM program, it severly limits your interaction and can be tedious to use.  On the other hand, if you and the computer can speak a common language (BASH, ZSH, CSH, etc), you can communicate much more efficiently and with greater depth.

Check out this excellent (if quite old) article: [http://www.useit.com/papers/anti-mac.html](http://www.useit.com/papers/anti-mac.html)

---

### Post by blur xc on 2009-11-10
> **Marti68 said:**
> WOW! Thank you for so many considered replies and well informed replies

To anyone irritated by the question Please read this with a smile.  You remember the smile.  It's the opposite of the face some of you use when barely tolerating dumb newbies.

The point about the differing GUI's makes a lot of sense.  The impatience with newbies is a double edged sword.  Expecting to be spoon fed information is selfish and so offering help in a format that is efficient for the knowledgeable helper makes good sense.  It does, however, clash with an atmosphere of "selling" GPL and Linux to a wider audience; even translating the GPL principles to other industries.  That may not be the prime goal of many but would appear to be the approach of Cannonical et-al.

Personally speaking, I'm learning the system by purchasing/downloading manuals and guides.  I'm not saying it's right; just right for me.  May even attend one of the User Groups that populate London's pubs \\:D/ 

...and again, Thank you.


It helps that you didn't start out your original post with a, "The command line sucks and linux sucks because if it!!", tone...

I started out computing before there was such a thing as a gui..  Well, I guess the Macintosh did exist, bot noone used it.  Commodore 64/128, apple IIe, ibm clone 286/12 running dos 5.  So, to me, it's a bit of a welcome re-acquaintance.  

BM

---

### Post by issih on 2009-11-10
The CLI is an immensely powerful thing...and I've spent all day using various features of it to achieve lot of file management tasks that would have taken a lot longer via the gui.

But then I can say the same the other way round too...the two interfaces excel in different ways.

The one main down side to the cli is that it is not 'intuitive'. This is only true to an extent, in that once you know a fair bit about the cli it is pretty easy half the time to guess the right flag to use and if that fails parsing the man page for the little bit of info you need gets miles easier with a few years of practice..but that is the point, it does take practice.

Gui's actually take practice to learn to use too, the difference is, almost everyone has had that practice already. The other way in which gui's are more intuitive, is that generally, the plethora of steps (app launches, menu clicks etc) that lead to what you need, are (inevitably) a shorthand for the process you are performing, so that the user can see what the different steps are doing as they perform them.

Cli commands have this too, but only if you happen to know enough about how to break down the flags, and indeed already know the meaning of the different flags.. To this end a CLI command is inevitably confusing and looks like magic to a new user.

So...CLI, its incredibly powerful and much better than a gui for certain tasks, and is particularly efficient at communicating fixes through atext based medium.

Gui;s are also incredibly powerful and better than the cli for some tasks, and is particularly efficient at letting the user glean what is happening to their computer.

To this end I have long been an advocate of trying to provide gui answers, or at least carefully explained cli answers in the beginners forums.

Having said that, I have no doubt I have presented several undocumented cli solutions myself...people just don't have the time to behave in the ideal way every single time sadly.

---

### Post by doas777 on 2009-11-10
the cli is like everything else complicated. take it in the bites you can swallow, and after a while you'll be surprised how much you have learned. I certianly didn't start out as a command junkie...it just kinda happened.

---

### Post by MaxIBoy on 2009-11-10
The following story is written by Eric S. Raymond and the copyright belongs to him; however, the license permits me to quote it here.

> 
**Master  Foo Discourses on the Graphical User Interface**

One evening, Master  Foo and Nubi attended a gathering of programmers who had met to learn from each other.  One of the programmers asked Nubi to what school he and his master belonged. Upon being told they were followers of the Great Way of Unix, the programmer grew scornful.


&#8220;The command-line  tools of Unix are crude and backward,&#8221; he scoffed.  &#8220;Modern, properly  designed operating systems do everything through a graphical user interface.&#8221;


Master Foo said nothing, but pointed at the  moon.  A nearby dog began to bark at the master's hand.


&#8220;I  don't understand you!&#8221; said the programmer.


Master Foo  remained silent, and pointed at an image of the Buddha. Then he pointed at a window.


&#8220;What are you  trying to tell me?&#8221; asked the programmer.


Master Foo pointed at the programmer's head. Then he pointed at a rock.


&#8220;Why can't you make  yourself clear?&#8221; demanded the programmer.


Master Foo frowned thoughtfully, tapped the programmer twice on the nose, and dropped him in a nearby trashcan.


As the  programmer was attempting to extricate himself from the garbage, the dog wandered over and piddled on him.


At that  moment, the programmer achieved enlightenment.Source:
[http://catb.org/~esr/writings/unix-koans/gui-programmer.html]("http://catb.org/%7Eesr/writings/unix-koans/gui-programmer.html")

---

### Post by hoppipolla on 2009-11-10
It's very, very quick to use and also very accurate. It depends what mood I am in the extent to which I use it!

It can also be fantastic for fixing other people's machines, as you can just tell them what commands to input which can work out quicker than navigating menus and control panels! :)

---

### Post by doas777 on 2009-11-10
> **MaxIBoy said:**
> The following story is written by Eric S. Raymond and the copyright belongs to him; however, the license permits me to quote it here.

Source:
[http://catb.org/~esr/writings/unix-koans/gui-programmer.html]("http://catb.org/%7Eesr/writings/unix-koans/gui-programmer.html")

I love master foo, but the punchline to that one is a little weak.

---

### Post by alphaniner on 2009-11-11
> **Marti68 said:**
> the main reason my partner considers my Ubuntu laptop an indulgence not a serious tool.

From an administration perspective, the CLI is the serious tool whereas the GUI is the indulgence.  It's just that simple.

---

### Post by dasunst3r on 2009-11-11
I have no fascination with the CLI.  It was merely out of pragmatism that I would use it when it happens to be the easier method.

---

### Post by Chame_Wizard on 2009-11-11
-CLI is much better if 2 different drivers of graphic cards are total screw up(happened to me in June)

-You can fix/customize you entire system by a few commands(including downloading and install),if you know what you are doing.:popcorn:

It's wayy  better/more powerfull than M$ DOS/Power shell ****.

Heck it's one of the reason that the Internet services : mail,ftp,Usenet.TCP/IP,BBS were created with use of CLI apps(early 1970's).:popcorn:

---

