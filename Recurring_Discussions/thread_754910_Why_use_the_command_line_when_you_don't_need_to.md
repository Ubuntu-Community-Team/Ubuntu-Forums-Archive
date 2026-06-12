---
title: "Why use the command line when you don't need to?"
date: 2008-04-14
forum: Recurring Discussions
---

### Post by 50words on 2008-04-14
[This post on installing TrueCrypt 5.0](http://phorolinux.com/how-to-install-truecrypt-50-on-ubuntu-710-gutsy-gibbon.html) is a good example of what I mean.

Here is how you intall TrueCrypt 5.0 on Ubuntu: (1) download the appropriate binary from the website; (2) right-click on the file you downloaded and select "extract here;" and (3) open the folder that you just extracted and double-click on the .deb file inside it.

How in the world is typing all those commands (even with tab-complete) easier?

---

### Post by Nolander on 2008-04-14
Umm, not being rude, but are u serious???

Its a hole 3 line of code,

> (1) download the appropriate binary from the website; (2) right-click on the file you downloaded and select "extract here;" and (3) open the folder that you just extracted and double-click on the .deb file inside it.

yeah the above method is easy but so is using the command line...

And thing like installing apps through synaptics, u have to open it find the package the select install and hit apply. or u can go to the command line and use 'apt-get' or 'aptitude'. that way u dont need to wait for any programs to load...
~nolander

---

### Post by TeraDyne on 2008-04-14
Because the CLI is usually universal, while a GUI isn't. Some use KDE, some use GNOME, some use XFCE, and many others use simple window managers. It wouldn't be the same across them all.

---

### Post by LaRoza on 2008-04-14
> **50words said:**
> [This post on installing TrueCrypt 5.0](http://phorolinux.com/how-to-install-truecrypt-50-on-ubuntu-710-gutsy-gibbon.html) is a good example of what I mean.

Here is how you intall TrueCrypt 5.0 on Ubuntu: (1) download the appropriate binary from the website; (2) right-click on the file you downloaded and select "extract here;" and (3) open the folder that you just extracted and double-click on the .deb file inside it.

How in the world is typing all those commands (even with tab-complete) easier?

Your instructions didn't work on my end. 

Not everyone uses GNOME or KDE. 

I use mc as my file manager; no clicking involved, and wmii as my window manager.

---

### Post by paul101 on 2008-04-14
> **50words said:**
> How in the world is typing all those commands (even with tab-complete) easier?

you dont need to sit and type out the commands, just use control + shift + v to paste into the command terminal :)

---

### Post by LaRoza on 2008-04-14
> **paul101 said:**
> you dont need to sit and type out the commands, just use control + shift + v to paste into the command terminal :)

Or highlight and middle click ;)

---

### Post by 50words on 2008-04-14
If you read a Windows or Mac guide to installing the software, it would look like what I wrote.

What better way to tell new or potential users that Ubuntu is not for them by over-geeking even a simple .deb installation?

We all use Ubuntu, so everything is pretty much in the same place. (People running different configurations can probably figure out the CLI commands without help.) Instead of directing a new user to the terminal, tell them what to do in a way that is (1) familiar and (2) easy.

---

### Post by amauk on 2008-04-14
mainly because of consistency

Linux is highly modular, with the ability to have many different desktop environments, windows managers, and file managers

Plus there's remote management
You really don't want to be running GUI apps if your remoting into a server somewhere

The exact instructions for unpacking an archive using the GUI is going to be different across all these different environments

Better (in my opinion, anyway) to have one set of instructions for everybody - no matter what environment they personally use

---

### Post by 50words on 2008-04-14
> **LaRoza said:**
> Or highlight and middle click ;)

Or do what I said, which is still faster, especially since one of the commands was "navigate to the directory where you saved the tarball."

---

### Post by TeraDyne on 2008-04-14
> **50words said:**
> If you read a Windows or Mac guide to installing the software, it would look like what I wrote.

What better way to tell new or potential users that Ubuntu is not for them by over-geeking even a simple .deb installation?

We all use Ubuntu, so everything is pretty much in the same place. (People running different configurations can probably figure out the CLI commands without help.) Instead of directing a new user to the terminal, tell them what to do in a way that is (1) familiar and (2) easy.

Again, it's not that simple. People use different GUIs, but almost everyone uses the same CLI. Thus, almost everyone will be able to use the same instructions to install something from that CLI. That's not true on the GUI, were there is a lot of diversity.

---

### Post by LaRoza on 2008-04-14
> **50words said:**
> Or do what I said, which is still faster, especially since one of the commands was "navigate to the directory where you saved the tarball."

Is it?

Here is what I would have to do to follow your instructions.

[list]
[*] Install GNOME or KDE. ```
sudo aptitude install kde-core
```
[*] Log out and log in using KDE
[*] Get used to a new DE. Alt + Enter wouldn't open a terminal like it does in wmii, and Alt + p wouldn't allow me to start applications
[*] Find the tarball, but opening a window, instead of my usual quicker method
[/list]

The commands are universal (for the system they are for). If someone knows another way, they can do it. You seem to advocate giving the most restrictive and "simplest" instructions, instead of the most useful.

---

### Post by 50words on 2008-04-14
> **LaRoza said:**
> I use mc as my file manager; no clicking involved, and wmii as my window manager.

How many people using mc and wmii do you think need either set of instructions?

When it is just as easy to do something with the GUI, why not post the GUI commands for Ubuntu and Kubuntu, at least (or as well), since most Ubuntu users are using one or the other?

> **LaRoza said:**
> The commands are universal (for the system they are for). If someone knows another way, they can do it. You seem to advocate giving the most restrictive and "simplest" instructions, instead of the most useful.

Most useful for whom? Are we trying to welcome users from Windows and OSX, or scare them away? Are we trying to change the image of Linux as a geek's OS, or perpetuate it? I realize that for many advanced tasks it is easier to give instructions using the command line. But for simple tasks, why not give GUI instructions for the two most popular DEs and add the CLI commands for others?

Whenever a reviewer talks about how Linux still insists on doing things from a terminal, a chorus of users chime in talking about how you can do everything in a GUI in Ubuntu. But try finding a set of instructions for doing something with the GUI, and there isn't much. You do still have to use the command line all the time, if you want to make use of any of the "community help" that is available.

---

### Post by LaRoza on 2008-04-14
> **50words said:**
> How many people using mc and wmii do you think need either set of instructions?

When it is just as easy to do something with the GUI, why not post the GUI commands for Ubuntu and Kubuntu, at least (or as well), since most Ubuntu users are using one or the other?

Do I care how many others use it? Those instructions that you don't like will work for everyone, including me. Your instructions won't work for me.

Are you so quick to exlude others for your own convenience?

---

### Post by chucky chuckaluck on 2008-04-14
universal instructions

open terminal, copy&paste

wget whatever...
sudo tar...
sudo dpkg -i blahblahblah


gui instructions

if you're using gnome, open firefox and go to blah, then go about a third of the way down the page and click on blah. select save blah to blah, etc. if you're using kde, once you've downloaded the blah, stay in konqueror and click on 'home'...oh, you use dolphin? well then...hang on, i'm getting to xfce (by the time you get thunar open on that old piece of junk, you'll have to download the new version anyway). etc.

---

### Post by bigbrovar on 2008-04-14
from my little experience with linux i have goetten to know that CLI is a very wonderful tool (if i can call it that) many a times i have broken my system and had to resort to the cmand line to fix it back .. while i have very limited knowledge of the commandline .. the little i know has really helped with get out of a lot of situations ... even though there might be a gui way of installation i always try to compile first . then if that doesnt work i would use synaptics ... some pple use ubuntu ..for me linux is a learning process .. and command line show u more about linux than u can ever get in GUI..

---

### Post by meborc on 2008-04-14
i agree with LaRoza

1) there are people, who would like to follow the howto using ssh or remote connection

2) there are way too many different combinations of DEs and FMs

3) I prefer cli for most of my system configuration as it is just way faster then using any other tool, for example - every time i do a reinstall, i need to install a couple of programs i now i will be using... instead of typing them into synaptic and searching and ticking and applying, i just type in "sudo apt-get install inkscape vlc ubuntu-restricted-extras nethack-console audacious" and so on, and hit enter... all installed with one command

---

### Post by notwen on 2008-04-14
Learning to depend on these .deb files will only limit you to the amount of software out there.  Learning to compile from source, is not that difficult of a thing and it opens up your choices abundantly.  Some apps are made on other distros and making a package for Debian is the least of their concerns.  

It's all about choice(w/ Linux there's way too many choices making way too many different unique situations), so if you prefer to not use CLI don't and users who want CLI will use it.  =]

---

### Post by manicman on 2008-04-14
I have Truecrypt installed on my server. It would be impossible for me to follow your instructions as i dont have a window manager installed.

---

### Post by Tomatz on 2008-04-14
But i'm using csh!

---

### Post by Tundro Walker on 2008-04-14
You can't automate GUI clicks, dude, without some complicated x/y tracking software.  

But you can easily create CLI scripts and schedule them to fire off using cron.

CLI is not for everyone, especially for those who don't prefer using it much.  But for the folks who do, or the ones who like to automate tasks, the CLI is preferable to GUI.

The same holds true in MS Windows, too, even though everyone thinks of it as a GUI-only.  You can script jobs using .bat files or .vbs / .js files through Windows Script Host, then easily schedule them through task scheduler.  It's a very easy way to schedule nightly defrags, virus scans, database compaction, report runs, etc.

---

### Post by YetAnotherNoob on 2008-04-14
> **50words said:**
> How in the world is typing all those commands (even with tab-complete) easier?

You 100% correct.  A set of command line instructions to install software is a alien proposition for most computer users. But you a not going to get much support for your argument on this forum. The majority of linux users thrive on their knowledge of obtuse terminal commands.

To be fair:
[LIST]
[*]Most software on Ubuntu does not require a command line and can be installed via the package managers. There is thousands of software packages available.
[*]Command lines are incredibly powerful once you learn them.
[/LIST]

---

### Post by ARhere on 2008-04-14
There is a fundamental problem that the pro-command line people are missing.  In order to argue that the command line is easier, the condition that the user must already be familiar with the commands must be present.  I think that is what the originator of this thread is trying to say.

_One of the_ reasons a GUI is popular is the ability to visually browse functions available to the user via icons, button, or other such labels in an attempt to make the systems use intuitive.

Think of [any device with lots of controls]("http://www.ohbaptist.com/soundboard.jpg").  Every function has a knob, button, or slider that is clearly labeled and in most cases aesthetically pleasing.  This allows the control to me more intuitive, verses stopping every time to read a manual or browse forums.  The later may be more correct, but is more time consuming and not fun to use.

Imagine if the same device I linked just had 10 generic switches representing 1,024 different functions.  _**Most_** people will not want to use it.

I would argue that if we want to see Linux to take more of the desktop market share, many basic functions across multiple GUI's need to be more uniform and standard.  I am not arguing to remove ones ability to change how the GUI functions, but the default should be uniform for some basic functions across multiple gui's.

-AR

---

### Post by Ioky on 2008-04-14
Why you use Icon when you don't need to?

---

### Post by LaRoza on 2008-04-14
> **YetAnotherNoob said:**
> You 100% correct.  A set of command line instructions to install software is a alien proposition for most computer users. But you a not going to get much support for your argument on this forum. The majority of linux users thrive on their knowledge of obtuse terminal commands.

To be fair:
[LIST]
[*]Most software on Ubuntu does not require a command line and can be installed via the package managers. There is thousands of software packages available.
[*]Command lines are incredibly powerful once you learn them.
[/LIST]

How else should they release it? If a site can assume a person is using GNOME or KDE, then they give the GUI instructions.

They are not obtuse commands, they are commands. Yes, we thrive on knowledge. What is the point of having features if you don't know how to use them?

---

### Post by gsmanners on 2008-04-14
Using a GUI is better if you aren't familiar with the way things work, but using the keyboard in general (for just about any application) is always faster if you're familiar with how to use it.

---

### Post by LaRoza on 2008-04-14
> **ARhere said:**
> There is a fundamental problem that the pro-command line people are missing.  In order to argue that the command line is easier, the condition that the user must already be familiar with the commands must be present.  I think that is what the originator of this thread is trying to say.


No, I do not think familiarity or ease of use is a factor in my position. It is the universal aspect. One should try to be universal, if they can't make assumptions about the users.

---

### Post by Tomatz on 2008-04-14
It is easier and less confusing to post commands on the forums for users to copy and paste. This causes obvious problems though (with the rm command especially).

At the end of the day would you prefer to follow a long confusing post. Or a short simple post?

---

### Post by days_of_ruin on 2008-04-14
You can copy and paste which is the easier then everything else.
Plus its faster and you always get error messages if there is an error.

---

### Post by YetAnotherNoob on 2008-04-14
> **LaRoza said:**
> No, I do not think familiarity or ease of use is a factor in my position. It is the universal aspect. One should try to be universal, if they can't make assumptions about the users.

The truth is linux requires a certain degree of CLI usage to do the more advanced tasks. GNOME/KDE etc only go so far.

A 40 year old working mother of three probably is not interested in learning the universal CLI. They just want the apps.

"Show me the applications!"  (sorry that is a terrible joke).
:)

---

### Post by LaRoza on 2008-04-14
> **YetAnotherNoob said:**
> The truth is linux requires a certain degree of CLI usage to do the more advanced tasks. GNOME/KDE etc only go so far.

A 40 year old working mother of three probably is not interested in learning the universal CLI. They just want the apps.

"Show me the applications!"  (sorry that is a terrible joke).


System->Administration->Synaptic Package Manager

Search, click, apply.

Done.

For everything else, there are instructions that tell you what to do. If you can't follow detailed instructions...

---

### Post by chucky chuckaluck on 2008-04-14
> **ARhere said:**
> There is a fundamental problem that the pro-command line people are missing.  In order to argue that the command line is easier, the condition that the user must already be familiar with the commands must be present.  I think that is what the originator of this thread is trying to say.

when i first started, i didn't know anything. i just copy&pasted whatever people told me to.

---

### Post by LaRoza on 2008-04-14
> **chucky chuckaluck said:**
> when i first started, i didn't know anything. i just copy&pasted whatever people told me to.

Yeah. I do that still, if I trust the source. (Even if I do understand the commands, I don't need to think about it if the source is trusted)

---

### Post by kellemes on 2008-04-14
> **YetAnotherNoob said:**
> The truth is linux requires a certain degree of CLI usage to do the more advanced tasks. GNOME/KDE etc only go so far.

A 40 year old working mother of three probably is not interested in learning the universal CLI. They just want the apps.

"Show me the applications!"  (sorry that is a terrible joke).
:)

She probably isn't going to be interested in Truecrypt, let alone setting up a LAMP server.
She'll have all she needs without having to touch her keyboard, not counting typing and printing a shopping list that is..

---

### Post by Koori23 on 2008-04-14
I had a particular aversion to the command line when I started using Breezy. I also didn't appreciate how modular Linux is either. 

To this day, when installing themes or something, I never extract via the command line. I also use the "Extract Here" right click option. I only do that because I never remember the switch options. I need to use that more though.

Now, I hate icons and mice for the most part. I use XFCE and make full use of my "Windows" key or Super Key or whatever. Win + E = Thunar, Win +R =Run Win + I =Epiphany Win + m = Claws Mail and so on. 

Bash is similar. Instead of typing "sudo aptitude install" I type "Install". "Back" takes me back one folder in my directory, "hsh" takes me all the way back to my /home folder. 

"weather" typed into my terminal gives me the weather for the next 3 days and current conditions. I don't need to go to a website to get it. 

You CANNOT fire up Firefox and get the weather as quickly as I can using the GUI. The terminal is the most direct way to manipulate the system.

Since Linux is modular, you can create some serious shortcuts to make your life a lot easier. 

I don't lose sleep over the times I move stuff around using the GUI, but I do so love the ability to make my computer do EXACTLY what I want when I want without all the extra bloat.

---

### Post by popch on 2008-04-14
It is a common misconception that the GUI is more friendly for all or even most users.

Try giving someone direction over the phone, in the native language of the user, to a user who has used Windows for several years.

We just take it for granted that the user knows several terms and 'primitive' actions such as desktop, directory, folder, opening something, right clicking, double clicking. There are more users than you would believe who don't know one, more or all of those things. Yet they work reasonably well with their PCs.

Thus, the directions to 'move the attachment to the desktop, right click on the tarball' and some such might be answered by a helpless fit of giggling.

Or have you ever given instructions to the conscientious new user who then tried to take notes of what you were showing in the GUI? Only to get a call the very next morning because they could not follow the directions they had written down themselves?

That's why the IT support in many corporations love remotely accessing the users' desktops to bits. They do not have to walk the user through all the dialog boxes, wizards, tabs, buttons and inexplicable and unrecognizable icons.

We should stop perceiving the CLI as a disadvantage or even a problem when in fact it is a feature which enables even the rawest beginner to apply the advice and recipes given them by more knowledgable users.

---

### Post by Paqman on 2008-04-14
I have to agree with the OP. Falling back on the command line for extracting and installing a .deb is just silly. A non-techy user is unlikely to understand the instructions, and will just slavishly copy them in. And everybody else can use the CLI if they *really* want to. 

The GUI is a *feature*, not a bug! :)

---

### Post by LaRoza on 2008-04-14
> **Paqman said:**
> I have to agree with the OP. Falling back on the command line for extracting and installing a .deb is just silly. A non-techy user is unlikely to understand the instructions, and will just slavishly copy them in. And everybody else can use the CLI if they *really* want to. 

The GUI is a *feature*, not a bug! :)

The GUI is a feature, like you said. Not everyone has that particular feature...

---

### Post by aysiu on 2008-04-14
> **50words said:**
> If you read a Windows or Mac guide to installing the software, it would look like what I wrote. Yeah, but some guides to what you would think should be simple GUI tasks like showing hidden files or turning off search indexing require quite a bit of command-line, particularly for OS X.

[http://theappleblog.com/2007/04/30/quick-tip-showhide-hidden-files/](http://theappleblog.com/2007/04/30/quick-tip-showhide-hidden-files/)
[http://osxdaily.com/2007/03/22/how-to-completely-disable-spotlight/](http://osxdaily.com/2007/03/22/how-to-completely-disable-spotlight/)

> **ARhere said:**
> There is a fundamental problem that the pro-command line people are missing.  In order to argue that the command line is easier, the condition that the user must already be familiar with the commands must be present.  I think that is what the originator of this thread is trying to say. What you're saying would be true if you were talking about using commands no one is giving you, but the OP gave the specific example of a guide telling you how to do things. If you have a guide, you don't need to be familiar with the commands - you're spoonfed them already and just have to copy and paste.

---

### Post by Paqman on 2008-04-14
> **LaRoza said:**
> The GUI is a feature, like you said. Not everyone has that particular feature...

The people who don't aren't really the ones who need to be told how to install a .deb, though.

---

### Post by LaRoza on 2008-04-14
> **Paqman said:**
> The people who don't aren't really the ones who need to be told how to install a .deb, though.

The app in question is TrueCrypt 5.0, an app for encrypting hard disks.

This is hardly a basic desktop application. It is also likely to be useful for servers, which do not have GUI's. It isn't like it is giving the long way to install [Opera]("http://www.opera.com/"), as anyone running that has to have a GUI. TrueCrypt is likely to be run on systems without GUI's.

One of my computers is CLI only (it is an iBook, see my blog if you are interested). I installed everything I need through the repos, as usual. 

I may look like an advanced user right? My blog has images of my iBook, a CLI only computer, my desktop, which is using wmii and has three terminals open (one using Vim and showing a program I am writing, one using mc, a terminal file manager, and the other one is blank, but is used for compiling and running the program I am writing). Surely I am an advanced *nix hacker who knows everything and am being elitist about this thread right? No. I have never installed a .deb through the command line. In fact, the only .deb that I download and install is Opera. What if I wanted to use TrueCrypt? I would be lost. (Actually, I would google it and find it out quickly, but that is beside the point)

---

### Post by Paqman on 2008-04-14
> **LaRoza said:**
> The app in question is TrueCrypt 5.0, an app for encrypting hard disks.

This is hardly a basic desktop application. 
<snip>
TrueCrypt is likely to be run on systems without GUI's.

I disagree. One of Truecrypt's most popular features is its ability to encrypt a small container of data. It's extremely popular amongst home users wanting to secure sensitive personal info.

---

### Post by LaRoza on 2008-04-14
> **Paqman said:**
> I disagree. One of Truecrypt's most popular features is its ability to encrypt a small container of data. It's extremely popular amongst home users wanting to secure sensitive personal info.

You don't think it is useful for servers?

I said "likely" not "most likely".

---

### Post by ARhere on 2008-04-14
I am honestly surprised on the heavy discussion on this subject.  We need to stop arguing about finer details, take a step back, and look at the over-all issue.

I think we can all agree that the average computer user is more comfortable with a GUI then a command line.  If Ubuntu is going to continue to grow and challenge the desktop market, the GUI needs to be more integrated into basic functions.  People like my wife or mother are severely intimidated by command line and simply don't care to learn about the commands.

Details like _how_ this is done and how to deal with the different GUI structures is the task of engineers, not Grandmothers.  Until this philosophy is fully realized and adopted by the same people arguing against the post originator, Linux will never dominate the desktop.

-AR

---

### Post by Rinzwind on 2008-04-14
50words
1. Not always do you have access to a GUI. I have to log in into our clients systems using ssh and/or telnet. A GUI is out of the order there. 
If I do not know the CLI version of the programm to install or the action  to do I am at a loss.  

2. Nothing beats copy/paste when it comes to speed :) 

3. CLI commands can be saved into a text file. If I save those onto my harddisc I have everything I need in the smallest possible form. 

4. Sometimes you need to install software to fix something that you did and that screwed up login into a GUI. If I had instruction to go into system/administration/{something} how am I suppose to do that? 

5;. It's a lot easier to find CLI instructions than pictures on a forum. 

I bet I can type alot more things I consider to be helpfull when using CLI BUT it all comes down to whatever anyone feels comfortable with. 
Linux is about CHOICE.
You can choose to use CLI
You can choose to use a GUI.
You can choose to use a download and install a deb or whatever.

It's a LOT better to have a choice than to be forced to use a GUI or to be forced to always use a CLI!!! Having the option to have both is what makes Linux fun!! :)
I hope you can agree on that if nothing else :)

---

### Post by original_jamingrit on 2008-04-14
> **Tomatz said:**
> But i'm using csh!

lol.

> **ARhere said:**
> There is a fundamental problem that the pro-command line people are missing.  In order to argue that the command line is easier, the condition that the user must already be familiar with the commands must be present...
...This allows the control to me more intuitive, verses stopping every time to read a manual or browse forums.  The later may be more correct, but is more time consuming and not fun to use....

Intuitive interfaces are indeed important for users coming from a GUI background (not necessarily the same as users coming from a no-computer-at-all background).  But when you're following a set of instructions, is it that big of a deal?  Nobody's making you use the CLI for things you want to explore on your own (except man pages, type 'man man' in sometime...).

You have your GUI for your day to day activities, you should only need to use CLI when following someone's instructions.

And if the instructions aren't quite copy-and-paste-you're-done simple, then you could probably talk to someone here for help.  There's lots of beginner to intermediate users just waiting in the fora for an easy question to answer. [COLOR="White"] lol, I'm one of them.[/COLOR]

---

### Post by reyfer on 2008-04-14
> **YetAnotherNoob said:**
> The truth is linux requires a certain degree of CLI usage to do the more advanced tasks. GNOME/KDE etc only go so far.

A 40 year old working mother of three probably is not interested in learning the universal CLI. They just want the apps.

"Show me the applications!"  (sorry that is a terrible joke).
:)

Then my 80 years old grandma is exceptional, and so are her 15 friends on the same age group  that are learning linux with me at the community center here. Again, I just hate it when people assume things about others without knowing them. "The newbs want this, the newbs want that". Please, speak about "the friends I know said they want this or that" but don't put all newbs on the same level, because not all want the same things, and MOST of them in my experience are willing to learn.

---

### Post by smartboyathome on 2008-04-14
This has probably already been said, but I don't want to go through all those pages to see.

Anyway, I think that using the CLI is counter intuitive. End users have been taught that the CLI is bad, since both Mac and Windows try to eliminate it as much as possible. Yes, people might use other desktop environments, but how many beginners actually do? It is easier for people to understand stuff if they use a GUI. Whether it be KDE, GNOME, or XFCE, the instructions on the first post are universal. I know it is like alienating some hard core linux guys, but they can convert it to what they need. If Linux wants to succeed, they need to get out of this mindset that CLI is the way to go, the reason graphical environments were created was because they are easier for people to use than the CLI. Thats my $.02. :)

---

### Post by LaRoza on 2008-04-14
> **smartboyathome said:**
> This has probably already been said, but I don't want to go through all those pages to see.

Anyway, I think that using the CLI is counter intuitive. End users have been taught that the CLI is bad, since both Mac and Windows try to eliminate it as much as possible. Yes, people might use other desktop environments, but how many beginners actually do? It is easier for people to understand stuff if they use a GUI. Whether it be KDE, GNOME, or XFCE, the instructions on the first post are universal. I know it is like alienating some hard core linux guys, but they can convert it to what they need. If Linux wants to succeed, they need to get out of this mindset that CLI is the way to go, the reason graphical environments were created was because they are easier for people to use than the CLI. Thats my $.02. :)

They are not easier, they are more familiar. Did you know that tiling window managers were the standard before Mac OS (Windows actually got in a little trouble for having overlapping windows in the beginning)? Did you know the CLI was the standard interface and still is in many area?

Linux has succeeded, in the server market, where GUI's are not needed.

---

### Post by Paqman on 2008-04-14
> **LaRoza said:**
> You don't think it is useful for servers?

I said "likely" not "most likely".

But again, i'd venture that anyone running a server isn't likely to need their hand held installing Truecrypt. Or anything else for that matter.

The point of discussion here is how appropriate the instructions were. Given that the instructions were posted on a website, I think we can be daring and leap to the assumption that anyone reading them is likely to be running a graphical environment. I think we can also assume that they aren't familiar with installing new toys in Linux, or else they wouldn't be looking for this information in the first place. 

Bottom line: this was info that would only be helpful for newbies, but it wasn't written in a newbie-friendly way. No gold star for Phorolinux.

---

### Post by Tundro Walker on 2008-04-14
There should be a rule that all the pro-CLI folks have to make their rebuttal posts in threads like these by only using a non-GUI, CLI web browser.  Wasn't there someone making a thread the other day using "links" (not lynx) or something?  It may not be practical, but it sure would be funny.

---

### Post by LaRoza on 2008-04-14
> **Tundro Walker said:**
> There should be a rule that all the pro-CLI folks have to make their rebuttal posts in threads like these by only using a non-GUI, CLI web browser.  Wasn't there someone making a thread the other day using "links" (not lynx) or something?  It may not be practical, but it sure would be funny.

Unlike some people, people familiar with the CLI, are not afraid to use more than one interface.

CLI is just another interface, just like a GUI.

I have made many posts with Lynx and links2, I just don't advertise it.

I am not against GUI development, however, I am against those that want everything down "their" way. TrueCrypt had very good instructions on how to install, that would work on any Ubuntu setup, whether it be the default, high customized, server, base install, etc. But some people feel the instructions should follow only the way they want it, not for other people.

Perhaps I will post instructions for GUI's, instead of terminal commands, however, I will do it the way **I** do it. I use wmii, anyone else not using it is stuck, but that isn't my problem.

No one comes out on this forum with a thread despairing at all the GUI solutions. I never feel a need to post and say the Ubuntu installer is a mess, and RAM hungry and the alternative disk is the best installer and that all the guides should go by that interface. Why do others feel a need to complain about the most universal solution to many problems?

---

### Post by aysiu on 2008-04-14
I think it's a false dichotomy to characterize people as being either pro-CLI or pro-GUI. A lot of people here who appear to be "pro-CLI" may just be tolerant of CLI or not have much of a preference either way, but they just don't understand why some people find the CLI so offensive that a thread must be created in protest of a simple tutorial asking you to copy and paste three commands.

I tend to make my Psychocats tutorials screenshot-heavy, but I do not take offense to or object to CLI-based tutorials. CLI and GUI are just different approaches, different tools to accomplish the same tasks.

---

### Post by Tomatz on 2008-04-14
> **aysiu said:**
> I think it's a false dichotomy to characterize people as being either pro-CLI or pro-GUI. A lot of people here who appear to be "pro-CLI" may just be tolerant of CLI or not have much of a preference either way, but they just don't understand why some people find the CLI so offensive that a thread must be created in protest of a simple tutorial asking you to copy and paste three commands.

I tend to make my Psychocats tutorials screenshot-heavy, but I do not take offense to or object to CLI-based tutorials. CLI and GUI are just different approaches, different tools to accomplish the same tasks.

+1

Both are powerful tools with their own advantages and disadvantages.

---

### Post by Gen2ly on 2008-04-14
In the past, I avoided the command line like the black death.  I had the unfortunate experience of destroying a Windows install back in the day.  I find myself using both the command line and GUI nearly equally.  I think the main argument for gurus is that the command line provides more arguments.

---

### Post by Triggerhapp on 2008-04-14
> **Paqman said:**
> But again, i'd venture that anyone running a server isn't likely to need their hand held installing Truecrypt. Or anything else for that matter.

Take that back! The first real experience I had with Linux was creating my own webserver, where I had so little experience I set up apache with https: and php from SOURCE.
If I'd known to look somewhere other than the download page at the time I'd have known i could use a package manager.
I got it working after 3 months of work on it, suprisingly. I still feel proud of that :P

---

### Post by pjkoczan on 2008-04-14
GUIs are notoriously rigid, task-based, and isolated. A GUI does one thing or one limited set of things very well, but it has little to no knowledge of what else is being done on that system, and problems can happen if configs aren't in the exact format said GUI expects. I've had a number of GUIs do very unexpected things with hand-edited config files that were "correct" according to the CLI version of the software.

The other fundamental issue with a GUI is that there's almost no way to connect it to other programs, unless I pipe output to another program, but that requires the CLI, and the program to print meaningful output. A GUI is just a program, but the CLI is also an infrastructure to tie programs together and make them do very interesting things. I can automate tasks, filter output, and even run multiple instances of a program with a minimal effort (show me where I can do for loops and pipes in a GUI). Honestly, saying a GUI is better than a CLI is like saying that your graphing calculator is better than trigonometry. They each have their place, and I couldn't imagine my computing experiences lacking one or the other.

So, can we please stop with all the hate?

---

### Post by 50words on 2008-04-14
I am not opposed to the CLI, or even to CLI-based tutorials. What seemed rather silly to me about that particular tutorial (and many like it) is that the instructions are just as easy to give for one of the three main Ubuntu GUIs.

After all, this is an Ubuntu forum. If you are using something else, you are not really running the OS these forums serve, and the instructions in that tutorial (for installing TrueCrypt in Ubuntu 7.10, not Epiphany, wmii, BlackBox, or whatever) were not for you.

I don't oppose the CLI. I just think it is silly to insist on using the CLI when the GUI is just as easy or easier, especially when the tutorial you are writing is for a GUI DE.

It is similarly silly to tell newbies to use Synaptic when the Add/Remove Programs is front and center and obvious.

---

### Post by aysiu on 2008-04-14
I don't really think it's silly, but it's not really the approach I would take. As I said before, I try to make my tutorials screenshot-heavy. Nevertheless, the CLI isn't really that scary if you emphasize that people can copy and paste (instead of retyping).

---

### Post by LaRoza on 2008-04-14
> **50words said:**
> 
After all, this is an Ubuntu forum. If you are using something else, you are not really running the OS these forums serve, and the instructions in that tutorial (for installing TrueCrypt in Ubuntu 7.10, not Epiphany, wmii, BlackBox, or whatever) were not for you.

I use Ubuntu, and all the software that I typically use (except Opera) is in the official Ubuntu repositories.

The official Ubuntu install disks have options for installing a server, a command line system, and a desktop. 2/3 of the options are CLI only systems.

The official Ubuntu versions:

Edubuntu
Gobuntu
Kubuntu
Xubuntu,
Mythbuntu
Ubuntu Studio
Ubuntu JeOS 
Ubuntu Mobile

And the instructions in that tutorial were for all Ubuntu variants.

---

### Post by 50words on 2008-04-14
> **LaRoza said:**
> I use Ubuntu, and all the software that I typically use (except Opera) is in the official Ubuntu repositories.

The official Ubuntu install disks have options for installing a server, a command line system, and a desktop. 2/3 of the options are CLI only systems.

The official Ubuntu versions:

Edubuntu
Gobuntu
Kubuntu
Xubuntu,
Mythbuntu
Ubuntu Studio
Ubuntu JeOS 
Ubuntu Mobile

And the instructions in that tutorial were for all Ubuntu variants.

Which of those options do new users opt for, do you think?

---

### Post by akiratheoni on 2008-04-14
> **Tundro Walker said:**
> There should be a rule that all the pro-CLI folks have to make their rebuttal posts in threads like these by only using a non-GUI, CLI web browser.  Wasn't there someone making a thread the other day using "links" (not lynx) or something?  It may not be practical, but it sure would be funny.

This is just so wrong on so many levels. I use the CLI AND the GUI. Does that mean I'm pro-CLI and I should use CLI only applications? NO! It's called using both interfaces. If that was supposed to be a joke, I didn't find it funny. At all.

---

### Post by aysiu on 2008-04-14
> **50words said:**
> Which of those options do new users opt for, do you think?
I'd say Ubuntu (oddly left off the list), Edubuntu, Kubuntu, or Xubuntu.

---

### Post by 50words on 2008-04-14
I would agree, which is why I think those who write helpful tutorials should include GUI instructions for the GUI-based Ubuntu distros, or at least the GUI-based distro the writer uses, in addition to the CLI "shorthand."

It can only make Ubuntu more inviting and less imposing for new users.

---

### Post by LaRoza on 2008-04-14
> **50words said:**
> Which of those options do new users opt for, do you think?

Why should I care about that?

Most computers sold have Windows, does that mean all tutorials and products should be aimed at the latest Windows?

---

### Post by aysiu on 2008-04-14
> **LaRoza said:**
> Why should I care about that?

Most computers sold have Windows, does that mean all tutorials and products should be aimed at the latest Windows?
Actually, a lot of tutorials and products are aimed at Windows for that very reason.

---

### Post by p_quarles on 2008-04-14
> **50words said:**
> IAfter all, this is an Ubuntu forum. If you are using something else, you are not really running the OS these forums serve, and the instructions in that tutorial (for installing TrueCrypt in Ubuntu 7.10, not Epiphany, wmii, BlackBox, or whatever) were not for you.
The forum provides support for software found in the repositories, which includes many window managers other than Metacity, KWin and Compiz. It also most certainly includes various shell environments, including Bash and Dash. 

As I've pointed out in several of the other threads dedicated to this particular recurring discussion, I like to be able to verify the instructions I give to people. Since I don't use GNOME, it would be rather difficult for me to ensure that I was giving accurate advice for using the interfaces it provides. 

Frankly, I think those wanting instructions for a particular interface should specify that interface when asking for help. That isn't difficult, and there are almost always people willing to tailor their directions to individual questions.

---

### Post by cardinals_fan on 2008-04-14
> **50words said:**
> If you read a Windows or Mac guide to installing the software, it would look like what I wrote.

And we want to use ten step wizards to install everything?  I'll take the terminal any day over a wizard...

---

### Post by aysiu on 2008-04-14
> **cardinals_fan said:**
> And we want to use ten step wizards to install everything?  I'll take the terminal any day over a wizard...
With one command, I can install about ten different programs. I wish I could do that on Windows and Mac.

---

### Post by cardinals_fan on 2008-04-14
> **aysiu said:**
> With one command, I can install about ten different programs. I wish I could do that on Windows and Mac.
True.  I've always been surprised to hear people wishing for Windows-type software installation - I hate wizards!

---

### Post by LaRoza on 2008-04-14
> **cardinals_fan said:**
> True.  I've always been surprised to hear people wishing for Windows-type software installation - I hate wizards!

Press OK if you hate Wizards, cancel if you don't.

---

### Post by SunnyRabbiera on 2008-04-14
For me I still feel that the command line should fade into the background like it did on OSX and windows.
If linux wishes to compete with the other OS as a desktop OS it must get away from the terminal and have more GUI tools.

---

### Post by LaRoza on 2008-04-14
> **SunnyRabbiera said:**
> For me I still feel that the command line should fade into the background like it did on OSX and windows.
If linux wishes to compete with the other OS as a desktop OS it must get away from the terminal and have more GUI tools.

It is in the background on desktop installations. The only time I can think of when one needs to use the cli is if the GUI is broken.

Some distros don't even have an easy way to get a terminal.

---

### Post by SunnyRabbiera on 2008-04-14
Yeh but it still called upon once in a while, but thats why I stick with linux is there is always progress.

---

### Post by qamelian on 2008-04-14
> **Paqman said:**
> But again, i'd venture that anyone running a server isn't likely to need their hand held installing Truecrypt. Or anything else for that matter.

You'd be wrong. Just search these forums, for example, and see how many folks have posted about wanting to set up a server of one kind or another and having no clue about the finer points and often being unpleasantly surprised that the server edition of Ubuntu is gui-less. Lack of experience is not always a deterrent. In fact, it's often the motivation for many people to jump in at the deep end to see just what they can accomplish.

---

### Post by aimran on 2008-04-14
> **SunnyRabbiera said:**
> Yeh but it still called upon once in a while, but thats why I stick with linux is there is always progress.

Once in a while is not as often as you'd think it is. Assuming Ubuntu with all the bells, whistles, and drivers work fine on an installation then there would be no need for the terminal after that innit? Assuming of course you are the browse/music type and won't install a LAMP server or try to get WINE up.

---

### Post by 50words on 2008-04-14
> **aimran said:**
> Once in a while is not as often as you'd think it is. Assuming Ubuntu with all the bells, whistles, and drivers work fine on an installation then there would be no need for the terminal after that innit? Assuming of course you are the browse/music type and won't install a LAMP server or try to get WINE up.

I need a terminal for WINE? Someone probably should have told me; I just installed it from Add/Remove Programs

I have almost forgotten the terminal is there. Ubuntu runs perfectly on my Thinkpad, and I haven't used the terminal for anything in months. I only remembered it was there when setting up a new Gateway with Ubuntu as a media center.

---

### Post by ghostdog74 on 2008-04-14
its amazing how people can argue about the slightest and insignificant things. there more important and meaningful things to do in life than this.

---

### Post by LaRoza on 2008-04-14
> **ghostdog74 said:**
> its amazing how people can argue about the slightest and insignificant things. there more important and meaningful things to do in life than this.

$cat life | forums

---

### Post by qazwsx on 2008-04-15
> **50words said:**
> I need a terminal for WINE? Someone probably should have told me; I just installed it from Add/Remove Programs


Actually you need to use terminal in order to run properly wine. Unless you create script (it is quite funny that there is no need to run terminal emulator window to do that. Just do it well once with text editor :lolflag:) that does the same executing job for you. Just check out WineHQ Frequently Asked Questions how to run Windows executables properly ;)

---

### Post by ghostdog74 on 2008-04-15
> **LaRoza said:**
> $cat life | forums

#more life.txt 
poverty
global warming
stagflation
war

---

### Post by Tuxoid on 2008-04-15
> **TeraDyne said:**
> Again, it's not that simple. People use different GUIs, but almost everyone uses the same CLI. Thus, almost everyone will be able to use the same instructions to install something from that CLI. That's not true on the GUI, were there is a lot of diversity.

I believe it is simpler than it seems to have new users receive GUI assistance. In my opinion, this issue could be very easily solved if there were sub-forums in the "Desktop Environments" section pointing to Ubuntu, Kubuntu, and Xubuntu. Yes, the command-line is basically consolidated on Linux; that doesn't mean new users won't pass judgment on using it. 

I feel that opting for giving help, to new users, at the command-line down-plays what I personally believe makes Linux a superior platform. Sure, some things require command-line help; most don't. Yes, the command-line is more resource-efficient; most new users won't notice and/or believe the GUI is efficient enough. IMO, I don't believe it's fair that new users should have to tell potential helpers, "I'm running Kubuntu", or "I'm running Xubuntu" etc...

There is an advantage to Linux has to having multiple DEs, as opposed to a consolidated Desktop. That advantage is the ability to have a choice. If you were to ask one of your windows using friends, "Name some elements of Microsoft Windows", I believe they would associate the concept with only the GUI (i.e. the Start Menu, Control Panel, Internet Explorer). They most likely would not mention low-level components like, the ntkernel, NTLDR, BOOT.INI.

The thing is, it's those low-level components that make the GUI run. Most of all, they allow for the use of drivers to operate hardware components. Let's say, you could slap on another GUI onto windows, gave it to a friend. They wouldn't know it was windows. They'd think it was as entirely different OS. Even though they would think it was totally different; you'd know it would be mostly the same.

It would support the same hardware, boot the same, still be under the same kernel.

What I am hopefully pointing out, is that with Linux we have a very important solution to a long-going computer problem. That problem is a common platform for hardware support. At the end of the day, the average user, the person who wants to get their work done, doesn't care how technically advanced their OS is. They just want it to work their hardware and to have good software. The kernel will take care of their hardware.

Past that, any desktop can exist to aid the user without breaking the support of hardware. The desktop is what most users will recognize. Most users will never see the kernel. What matters is that even though they may never see the kernel, that kernel will allow them to see the desktop, surf the internet, play music, write office documents, etc... It all begins at the kernel. Without a kernel, an Operating System cannot exist, hardware cannot reach its full operating potential, and a computer is effectively a waste. 

The problem of most Operating Systems today is a complete  forced cohesion between everything. That hypothetical idea I mentioned earlier is possible in Windows; just not easy enough to be practical. That way, Microsoft controls how you operate Windows. This is the same case with OS X. This means that Apple and Microsoft effectively control the support for hardware and software through market share for what most users see as a GUI. Windows Explorer and the Aqua Interface could be developed for the X Window System with Linux running under it, and no user would ever notice that it was an entirely different OS just as long as the hardware and software support was all there. 

Yet Microsoft and Apple control more than what the user actually cares about. The user cares about the GUI, and the hardware support. They don't care about the kernel, the boot loader, or any nerdy stuff. Gnome, KDE, or XFCE are capable of offering the GUI (the component that users care about), while the Linux kernel supplies the crucial hardware support.

Making entirely new Operating Systems from scratch is re-inventing the wheel when most users only care about the GUI.

---

### Post by LaRoza on 2008-04-15
> **ghostdog74 said:**
> #more life.txt 
poverty
global warming
stagflation
war

$mv life.txt /dev/null

---

### Post by Riffer on 2008-04-15
As a long time GUI guy all I can say is Thank God for the command line.  I would not like to see it gone, more then once it has rescued me from my own foolishness.  

For the average user the GUI for Ubuntu is great, intuitive and easy to to navigate and they don't have to use the command line.  But as people learn and want to try different setups and other things from the norm, the command line is a very powerful tool.

There is room on Ubuntu (linux) for both.  And I would encourage noob's to use both.

---

### Post by cardinals_fan on 2008-04-15
> **Tuxoid said:**
> I believe it is simpler than it seems to have new users receive GUI assistance. In my opinion, this issue could be very easily solved if there were sub-forums in the "Desktop Environments" section pointing to Ubuntu, Kubuntu, and Xubuntu. Yes, the command-line is basically consolidated on Linux; that doesn't mean new users won't pass judgment on using it. 

I feel that opting for giving help, to new users, at the command-line down-plays what I personally believe makes Linux a superior platform. Sure, some things require command-line help; most don't. Yes, the command-line is more resource-efficient; most new users won't notice and/or believe the GUI is efficient enough. IMO, I don't believe it's fair that new users should have to tell potential helpers, "I'm running Kubuntu", or "I'm running Xubuntu" etc...

Efficiency cuts both ways - I have a busy life and only a limited amount of time in which to help others.  If I have to spend longer replying to a post, I will reply to fewer.  Simple as that.

I haven't used Linux for very long myself (~1.5 years), but I picked up the command line naturally.  Yes, it takes time to learn - but maybe it's something worth learning...

---

### Post by macogw on 2008-04-15
> **smartboyathome said:**
> This has probably already been said, but I don't want to go through all those pages to see.

Anyway, I think that using the CLI is counter intuitive. End users have been taught that the CLI is bad, since both Mac and Windows try to eliminate it as much as possible. Yes, people might use other desktop environments, but how many beginners actually do? It is easier for people to understand stuff if they use a GUI. Whether it be KDE, GNOME, or XFCE, the instructions on the first post are universal. I know it is like alienating some hard core linux guys, but they can convert it to what they need. If Linux wants to succeed, they need to get out of this mindset that CLI is the way to go, the reason graphical environments were created was because they are easier for people to use than the CLI. Thats my $.02. :)
The CLI's not really counterintuitive.  It's just talking to the computer.  Using a GUI is like miming.

---

### Post by popch on 2008-04-16
Actually, I shouldn't have responded to this thread at all since I don't use the command line when I don't need to. 

There are times when I need to. Then I do. Otherwise I don't.

---

### Post by original_jamingrit on 2008-04-16
awesome blog, start by typing 'ls'...
[http://thrind.xamai.ca/](http://thrind.xamai.ca/)

---

### Post by Tomatz on 2008-04-16
> **original_jamingrit said:**
> awesome blog, start by typing 'ls'...
[http://thrind.xamai.ca/](http://thrind.xamai.ca/)

That is cool :)

---

### Post by klange on 2008-04-17
[quote="Rootless Root"]One evening, Master Foo and Nubi attended a gathering of programmers who had met to learn from each other. One of the programmers asked Nubi to what school he and his master belonged. Upon being told they were followers of the Great Way of Unix, the programmer grew scornful.

“The command-line tools of Unix are crude and backward,” he scoffed. “Modern, properly designed operating systems do everything through a graphical user interface.”

Master Foo said nothing, but pointed at the moon. A nearby dog began to bark at the master's hand.

“I don't understand you!” said the programmer.

Master Foo remained silent, and pointed at an image of the Buddha. Then he pointed at a window.

“What are you trying to tell me?” asked the programmer.

Master Foo pointed at the programmer's head. Then he pointed at a rock.

“Why can't you make yourself clear?” demanded the programmer.

Master Foo frowned thoughtfully, tapped the programmer twice on the nose, and dropped him in a nearby trashcan.

As the programmer was attempting to extricate himself from the garbage, the dog wandered over and piddled on him.

At that moment, the programmer achieved enlightenment.[/quote]

And that is why I use the CLI.

---

### Post by cardinals_fan on 2008-04-17
> **WindowsSucks said:**
> And that is why I use the CLI.
Kind of similar to your response [over here]("http://ubuntuforums.org/showpost.php?p=4733431&postcount=28")... :)

---

### Post by otwr on 2008-04-18
> **original_jamingrit said:**
> awesome blog, start by typing 'ls'...
[http://thrind.xamai.ca/](http://thrind.xamai.ca/)

Thanks for the mention! That WordPress theme is my work. I'm a (K)Ubuntu user. And I seriously need some new person's input on this thing. I think maybe because I made that theme, people think I might be a little more command-line than I really am... yes, I use the terminal a lot, but when it gets down to the hardcore stuff like 'find' and 'wget' I am constantly prefixing those with 'man'. And really, the browser is a pretty hostile environment for doing text-mode stuff. If anyone here is a killer JavaScript/PHP duder, please check out [http://code.google.com/p/wordpress-cli](http://code.google.com/p/wordpress-cli) and get in touch.

---

### Post by seanc7 on 2008-04-18
As a technical writer I'm always writing installation instructions for my company's software. They have a Windows-based GUI product and a Unix-based CLI product.

From an instruction writing perspective it's much easier to write instructions for CLI.

For the GUI you need screen shots and detailed instructions that say "click here" or "select this", etc, etc... All those screen shots quickly increase the document file size and you get 30MB Word docs to explain installation on a particularly GUI intensive module.

For the CLI, just highlight the commands to run in some way, bold or italics. I've never had any CLI instruction documents go over 800KB.

---

### Post by Triggerhapp on 2008-04-18
> **otwr said:**
> I am constantly prefixing those with 'man'

Nothing wrong with that! I'll have a look at the link but I cant promise im that good :P

Edit : Ow. looking at it and noticing just how pety my little animated cyber pet php/javascript was compared :)

---

### Post by BatsotO on 2008-04-24
why? maybe just to lazy reaching my mouse.

---

### Post by Joeb454 on 2008-04-24
> **BatsotO said:**
> why? maybe just to lazy reaching my mouse.

That's why I have a keyboard shortcut for the terminal ;)

---

### Post by karellen on 2008-04-25
imho, using the command line when it's no need for it it's a little pretentious. there are areas when the cli is heavily needed, but the modern linux distro require less and less use of the command line for simple->medium tasks (exceptions being compiling new packages and so)

---

### Post by aysiu on 2008-04-25
> **karellen said:**
> imho, using the command line when it's no need for it it's a little pretentious. there are areas when the cli is heavily needed, but the modern linux distro require less and less use of the command line for simple->medium tasks (exceptions being compiling new packages and so)
Whether it's pretentious or not depends greatly on what you consider "a need for." For example, I don't *need* to use the command-line to install applications (I can use Synaptic or Add/Remove), but *apt-get* is faster for me, so I use it. It's not pretentious. It's just easier for me to ```
sudo apt-get update && sudo apt-get install filezilla audacity galeon thunderbird
``` than it is to Applications > Add/Remove and search and check off each program individually.

---

### Post by karellen on 2008-04-25
> **aysiu said:**
> Whether it's pretentious or not depends greatly on what you consider "a need for." For example, I don't *need* to use the command-line to install applications (I can use Synaptic or Add/Remove), but *apt-get* is faster for me, so I use it. It's not pretentious. It's just easier for me to ```
sudo apt-get update && sudo apt-get install filezilla audacity galeon thunderbird
``` than it is to Applications > Add/Remove and search and check off each program individually.

as 1001! other things, it all comes down to subjectivity...

---

### Post by p_quarles on 2008-04-25
> **karellen said:**
> imho, using the command line when it's no need for it it's a little pretentious.
How is that so? There are many benefits to using a shell app, even in cases where a GUI equivalent is available. I use the command line for many things that I could accomplish in other ways. File management, volume management, encryption, managing my wireless connections, killing runaway processes, monitoring network traffic, image format conversion, and session management, among other things. I also map my extended media keys to console based apps.

Reasons include lower resource footprints, finer-grained control (in many cases), and the fact that pointing devices do not have tab-complete. I don't think any of those reasons are pretentious.

---

### Post by jdix123 on 2008-04-25
I wish I'd had to learn both back when I was first learning about computers.  Would have made setting up a server a lot easier now that the need has come along.

Sure I could have just told my boss "I know we are a non-profit with a limited budget, but we need to buy a site license for thousands of dollars AND a separate server OS."  But I liked being able to say "Yes, I can set up a secure fileserver using a free download."

And I'm not exactly a n00b, but it sure helped having SOME background with a CLI when the need arose.  Guess where that background came from?  You got it, help from the forums installing software and configuring systems.

---

### Post by jaytek13 on 2008-04-25
I'm sure people have already pointed this out but I'll say it anyways...

It's quicker. GUI applications can be bloated and confusing. Options can be hard to find and often times GUI apps don't include everything that you might want to do. It might take some time to learn the CL commands but the long term benefits are overwhelming.

Otherwise, it just teaches you things about what's happening behind the scenes. Understanding how things work is really just such a boon for knowledge, both personally and career wise, that avoiding the CL would actually be detrimental.

---

