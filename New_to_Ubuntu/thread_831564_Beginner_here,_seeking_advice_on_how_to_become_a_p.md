---
title: "Beginner here, seeking advice on how to become a pro."
date: 2008-06-16
forum: New to Ubuntu
---

### Post by broncbuster on 2008-06-16
Hello all,
I've just loaded Hairy Haggis 8.04 on my work laptop in place of windows.  I'm hoping that having it in my face for 8-10 hrs a day will force me to become more familiar and comfortable with Linux and eventually become a Linux Power User.  
I'm seeking advice from y'all on where I should start with my quest.  I'd like to become a terminal pro because I like - with windows - to use keyboard shortcuts and command prompts to do most of my tasks.  So I guess where I'm going with this is I'd like to know where you Linux Pro's started and what did you work on inside linux when you were a noob?  Should I be just using it casually until i need to install a new program, seeking help when i do?  Or should I start with simple terminal commands that could otherwise be accomplished with the mouse?  
Am I asking the wrong questions?  Are you confused as to what I want?  I'm sorry if you are.  Please just pretend that you don't even know what sudo really means or how to update a repository using the terminal and help me get proficient at Linux.

Steve

---

### Post by Daedal Dementia on 2008-06-16
look up unix programming and what not.

im not really familiar with anything but ubuntu.


but i'd say practice with installing stuff first via terminal.

use your terminal to reboot and turn off.

get the basics first. 


win to lin is a big jump. you have to learn to use tarballs and stuff. which is a pain if your used to a double click on an exe 

i suggest getting wine for sure.

start with deb files if you can instead of tars. (IMO)

cant really help much cuz im a linux novice.

---

### Post by jordanmthomas on 2008-06-16
I am definitely no pro, but I can tell you how to learn to be one.

If something interests you, read about it and play with it.  If you ever think, "I wonder if I can do this?"  that's your cue to look it up and do it.  Don't let lack of knowledge get in your way.  Screwing things up and then fixing them is the greatest way of learning.

Try doing things **without** reading guides first, and if (when) you fail then seek a howto / guide.  At that point, you'll at least be familiar with what the guide is talking about.

This probably isn't the right forum to post this, but whatever:  try out tons of distros.  Ubuntu is not the only one and each has its own merits.  I personally can't stand Ubuntu, so if I was to assume that Linux was Ubuntu I would be disappointed.  Knowing the ins and outs of several distros lets you see what they all have in common and what you should look for in foreign systems.

---

### Post by Daedal Dementia on 2008-06-16
i got ubuntu because it was free. and everyone was like "dude this rocks"

but i hear good of red hat and was thinking of trying puppy or chainsaw.

any suggestions?

---

### Post by broncbuster on 2008-06-16
You can reboot and shutdown from terminal?  HOw?  See how unfamiliar i am?  

Also, what's a tarball?

I have wine installed but it doesn't seem to be compatible with many of the win apps that i use or need to use.  

Also, once i've downloades a .deb file, how do i go about installing it via terminal?  

I have managed to install a .rar update using apt-get
I did: sudo apt-get install rar
But i'm not sure why it worked?  How did apt-get know where to find rar?  And what is apt-get and sudo for that matter?

---

### Post by jordanmthomas on 2008-06-16
> **Daedal Dementia said:**
> i got ubuntu because it was free. and everyone was like "dude this rocks"

but i hear good of red hat and was thinking of trying puppy or chainsaw.

any suggestions?

I always suggest Arch.  I think the fact that it's so simple makes it GREAT for learning on.  In terms of "difficulty" (though I hate that term) it's between Gentoo and Debian.  You don't have to compile stuff yourself but you'll probably want to edit config files for most of your programs since they pretty much leave them stock.

If you've tried other distros this may let you know what you're getting into.
[http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

---

### Post by Daedal Dementia on 2008-06-17
using a window-ism

tar is like rar.

its compressed and encoded.

i dont know how other terminals work because im just experimenting with ubuntu.

but in ubuntu there is

```
sudo reboot
```

and

```
sudo halt
```

sudo has something to do with privalages. but i dont really know much more.


if i get more info i'll let you know.

sudo apt-get install will install alot

i think theres a list where specific programs for ubuntu are listed and it searchs the list or something along those lines

```
 sudo apt-get install vlc
```

installs vlc media player

so on.


ussually debs just install it. and you will have it. but im not sure. i plan on expanding my linux know how with other distros

---

### Post by wolfen69 on 2008-06-17
when i first started, i concentrated on learning the install process thoroughly, and getting everything set up correctly. it pays to know partitioning and formatting. now i can concentrate on the command line more, even though im still a gui lover at heart. i suggest googling for material to read, as it is very plentiful.

and as jordanmthomas said, trying out all the major and not so major distros will also teach you alot. get yourself a couple spare drives and go nuts. if you blow something up, who cares? just start over or fix it.

---

### Post by RiceMonster on 2008-06-17
Just a quick word of advice - man pages are your friend. If you ever want to know about a command or program, what it does, and what you can do with it type "man command".

---

### Post by jordanmthomas on 2008-06-17
> **broncbuster said:**
> You can reboot and shutdown from terminal?  HOw?  See how unfamiliar i am?  

Also, what's a tarball?

I have wine installed but it doesn't seem to be compatible with many of the win apps that i use or need to use.  

Also, once i've downloades a .deb file, how do i go about installing it via terminal?  

I have managed to install a .rar update using apt-get
I did: sudo apt-get install rar
But i'm not sure why it worked?  How did apt-get know where to find rar?  And what is apt-get and sudo for that matter?

Yes, you can do pretty much everything from a commandline.
```
man shutdown
``` is some good reading.  For example, 
```
shutdown -t 5 -r
``` **-r**eboot in 5 seconds **-t**ime

A tarball is sort of the equivalent of a zip file or rar file.  A tar itself doesn't do any compression, but turns multiple files into one file that is then compressed by programs like gzip or bzip2

```
sudo apt-get install rar
```
Let's analyze this a bit
sudo:  this gives your user root permission since your user doesn't have permission to write to where all your programs are stored.  See [this]("https://wiki.ubuntu.com/RootSudo") for more
apt-get:  This is the package manager.  It manages all of your installed programs
install:  An option given to apt-get telling it you want to install
rar:   The name of the package you're going to install.  

Basically, any time you want to know more about a program, you can run **man program**

---

### Post by sam_delta on 2008-06-17
there are ubuntu servers with almost any program youll every need, thus sayd the command "sudo apt-get install <name of program>" will download and install that program from ubuntu servers.

lets say you want to install firefox, you just type
"sudo apt-get install firefox" and it will download and install firefox.

the Graphical way to do this, is by going into aplications>Add/Remove software, and selecting the software you want to install/remove, again, if you mark a software for installation, it will download and install it from ubuntu servers

another way of installing packages is using synaptic, go into system>administration>synaptic package manager,,,, and you can also mark packages/software for installation there

sam

---

### Post by Daedal Dementia on 2008-06-17
> **jordanmthomas said:**
> I always suggest Arch.  I think the fact that it's so simple makes it GREAT for learning on.  In terms of "difficulty" (though I hate that term) it's between Gentoo and Debian.  You don't have to compile stuff yourself but you'll probably want to edit config files for most of your programs since they pretty much leave them stock.

If you've tried other distros this may let you know what you're getting into.
[http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

thanks, will take that into account. i picked ubuntu cuz it was there, didnt really no anything about linux at the time

---

### Post by rraj.be on 2008-06-17
Just see these links

```
[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

[ubuntuforums.org/showthread.php?t=801404]("ubuntuforums.org/showthread.php?t=801404")

[http://ubuntuforums.org/forumdisplay.php?f=100]("http://ubuntuforums.org/forumdisplay.php?f=100")

[monkeyblog.org/ubuntu/installing/]("monkeyblog.org/ubuntu/installing/")

[ubuntuforums.org/showthread.php?t=820040]("ubuntuforums.org/showthread.php?t=820040")

[https://help.ubuntu.com/8.04/switching/index.html]("https://help.ubuntu.com/8.04/switching/index.html")

[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")



```

The bigest tutorials


```
[[COLOR="Blue"]http://www.psychocats.net/ubuntu/[/COLOR]]("http://www.psychocats.net/ubuntu/")
```

---

### Post by ChameleonDave on 2008-06-17
> **broncbuster said:**
> You can reboot and shutdown from terminal?  HOw?  See how unfamiliar i am?  

Also, what's a tarball?

To become knowledgeable, look up everything you don't know.

For example, don't ask us what a tarball is, just go to Wikipedia and read the article on it.

---

### Post by jordanmthomas on 2008-06-17
> **ChameleonDave said:**
> To become knowledgeable, look up everything you don't know.

For example, don't ask us what a tarball is, just go to Wikipedia and read the article on it.

quoted for truth

---

### Post by madjr on 2008-06-17
to become a pro you need to help lots of noobs in the support forums.

As your post counts increase (beans) your experience will also increase.

the more you help, the more of an expert you become.

---

### Post by broncbuster on 2008-06-17
Wow, thanks for the info, y'all are prompt and very helpful.  I mean, dang...I'd never get this many responses on a windows forum (believe me, i've tried) in such a short time.  

I tried 
man rar
and got a whole long manual of the program just like you said.  It's awesome.  Thanks again.  

So lets say i've just downloaded a .deb file to my desktop and want to install it via the terminal.  How do I do this?  And, once it's installed, why is it that some programs don't show up on the gui applications menu? (I've installed .deb files via the gui).  Also, how do I run the newly installed program via terminal?  

what's gksudo?
What's su

---

### Post by broncbuster on 2008-06-17
> **ChameleonDave said:**
> To become knowledgeable, look up everything you don't know.

For example, don't ask us what a tarball is, just go to Wikipedia and read the article on it.

Point taken.  I'll try not to ask for definitions in the future.  I swear, there were 5 responses between when i read one and replied myself.  Crazy.

---

### Post by rraj.be on 2008-06-17
hers is page for su sudo gksudo difference

```
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")
```

If you swear you will search yourself to learn  Try all links give above in my post.

They will be useful to you.

For searching  solutions for your problem's .

There are countless ubuntu users and surely they should experienced the problem that you are facing and they might got solved solution in ubuntu forum's.

Here is a search engine to search ubuntu forums alone.

[[COLOR="Blue"]www.uboontu.com[/COLOR]]("www.uboontu.com")

Hope with good keywords you can get answer for every problem here.

---

### Post by kalesh7 on 2008-06-17
> **broncbuster said:**
> You can reboot and shutdown from terminal?  HOw?  See how unfamiliar i am?  

Also, what's a tarball?

I have wine installed but it doesn't seem to be compatible with many of the win apps that i use or need to use.  

Also, once i've downloades a .deb file, how do i go about installing it via terminal?  

I have managed to install a .rar update using apt-get
I did: sudo apt-get install rar
But i'm not sure why it worked?  How did apt-get know where to find rar?  And what is apt-get and sudo for that matter?

a tarball is a .tar.gz or .tar.bz2 file (similar to a zip file)

to extract a .tar.bz2 file use ```
tar xjvf filename.tar.bz2
```
and .tar.gz file ```
tar xzvf filename.tar.bz2
```
I'll let you explore further uses of tar command :)

installing a .deb is dead easy

```
sudo dpkg --install filename.deb
``` 
dpkg helps you install/uninstall packages(among other things) but it wont handle dependecies like apt-get 
check description of sudo below 

apt-get is a program that installs packages for you, programs are available in packages, some may have just one package while some may have more related packages, or dependencies, apt-get resolves dependecies itself and will tell you that so and so packages need to be installed, if its more than what you asked for, however it wont install related packages unless you ask it to.

packages are available in repositories, you don't have to go around looking for them, apt-get and sypnatic, aptitude and the like(all basically do the same thing) can look in your software sources, You can see and edit sources at System->administration->software sources (yes theres a command line but I don't remember it offhand, anyone?)

as for sudo there are many things you can do as a normal user, but installing and other administrative jobs is restricted to root only
by doing ```
sudo command
``` (replace command with whatever command you want to run) you are assuming full root access for that action and you have ultimate power to do anything. I would advice you to check what the command will do before using it in sudo, as there is nothing in linux preventing you from trashing your own system(I know I did it many times in early days)
 
you may be suprised to learn that many times your own pc will give you the answer far faster than these forums or the web for details of almost any command use
```
man command
```
Tip: when done reading hit q

---

### Post by ChameleonDave on 2008-06-17
> **broncbuster said:**
> 
what's gksudo?
What's su

You're still asking the wrong questions.  Just type "man gksudo" or "man su".  It works for nearly any command.  There are also Wikipedia articles.  See [http://en.wikipedia.org/wiki/Gksudo](http://en.wikipedia.org/wiki/Gksudo).

In essence, [RTFM]("http://en.wikipedia.org/wiki/RTFM").  ;-)

---

### Post by wolfen69 on 2008-06-17
> **broncbuster said:**
> 
So lets say i've just downloaded a .deb file to my desktop and want to install it via the terminal.

you would do
```
cd Desktop
``` which means change directory. then
```
sudo dpkg -i name_of_file.deb
``` that will install it.

that is just 1 way to do it.

---

### Post by kalesh7 on 2008-06-17
so many repsones while typing the reply lol.
anyway gksudo is same as sudo(see above) expect it allows you to enter your password in a graphical popup while sudo asks for it in the same command box (I prefer sudo)
and you don't want to use su, consider it depreciated and use sudo intead

---

### Post by broncbuster on 2008-06-17
> **ChameleonDave said:**
> You're still asking the wrong questions.  Just type "man gksudo" or "man su".  It works for nearly any command.  There are also Wikipedia articles.  See [http://en.wikipedia.org/wiki/Gksudo](http://en.wikipedia.org/wiki/Gksudo).

In essence, [RTFM]("http://en.wikipedia.org/wiki/RTFM").  ;-)

I know, but you all are so fast that the post telling me off for asking definitions was posted WHILE i was typing that reply.  

YOu all are amazing and helpful.  Thanks.  I think my brain is going to pop and i'm tired, so i'm going to bed and will work on what you taught me tomorrow and ask more questions!

Steve

---

### Post by broncbuster on 2008-06-17
One last question for tonight...

Is there a way to create a shortcut key for terminal?  I'm so used to windows' Windows+R for the run dialog box that it'd be nice to have the same keystroke for terminal.

---

### Post by Daedal Dementia on 2008-06-17
i got "tilda" from the ubuntu applications list. you run it once everytime you boot. and you can set a keybaord short cut to hide it or display it. pretty dope if i say so myself.

hope it somewhat helps.

---

### Post by jordanmthomas on 2008-06-17
Alt + F2 is the same as windows + r in windows

Also, there's tons of ways to bind keys to do whatever you want.
xbindkeys, etc

---

### Post by ibuclaw on 2008-06-17
Two ways you can acheive this:

1) Press **Alt+F2** to open up GNOME's run application box.
Type in
```
gnome-terminal
```
in the text box and press ENTER.

2) Install Tilda.
```
sudo apt-get install tilda
```
Tilda is a Quake-Style interface for the gnome-terminal that lets you open it with a touch of a keystroke, for example, **F12** key.

[EDIT]
Oops, you guys beat me to it...

/me sighs.
+1 to my post count though!!! :D

Regards
Iain

---

### Post by hyper_ch on 2008-06-17
how to become a pro?

Just use it... you will run into limitations of your knowledge and then do research to solve them... that way you learn and progress.

Also have a read here in the forums. It is very active and you can learn a lot here...

---

### Post by Ripfox on 2008-06-17
hairy haggis...:lolflag:

---

### Post by kalesh7 on 2008-06-17
also browse these forums(and/or other linux forums) and look at general problem members are having and try to figure out what you would do if you had the same problem. often this will give you insight to lots of things you may not have otherwise.

---

### Post by broncbuster on 2008-06-17
Ok, i've been doing research and i now have my laptop setup with everything i need on it for work on the road, namely I've got my sprint aircard 595 working thanks to Michael at pbandjelly.org.  And I've got virtualbox running so that i can run my logmeinrescue in internet explorer.  

How do I set the terminal command 
pon cdma
to run at startup so that every time i launch linux i dont have to open the terminal to get my sprint card running?

---

### Post by rraj.be on 2008-06-17
To run a command in start up you can use session's in 
```

System --> Preference --> session's.

```

just click on ADD button. A pop up window will open like in thumbnail and fill it up.

You can add your command as i did in the thumbnails.


Here i used the command wvdial for example.

You can use your own custom command.

pon cdma

---

### Post by scotcella on 2008-06-17
My advice...

Learn one thing at a time and learn it good.. then learn something new. It's bad when you "learn" something and you have forgotten a week later.

Document, Document and Document!!!
Make sure you have written/bookmarked what you've learnt for later reference. Nothing worst than trying to find something you can't remember where it was.

p.s. I've even bookmarked page three there was some information i want to refer back to later!

---

### Post by broncbuster on 2008-06-17
> **rraj.be said:**
> To run a command in start up you can use session's in 
```

System --> Preference --> session's.

```

just click on ADD button. A pop up window will open like in thumbnail and fill it up.

You can add your command as i did in the thumbnails.


Here i used the command wvdial for example.

You can use your own custom command.

pon cdma

Thanks, it works great.  Only problem with it now is that everytime i reboot the OS and launch firefox, it starts in offline mode.  Not sure why.

Also, when I tried to install a .deb package I tried this:
```
cd desktop
```
But it didn't get me anywhere, got an invalid location error or something.
Then I tried to just:
```
sudo dpkg install *filename*.deb
```
Hoping that it would just get it right, but it didn't.  If I don't specify a directory with the "cd" command, where does linux assume the files are located?

---

### Post by kalesh7 on 2008-06-17
> **broncbuster said:**
> Thanks, it works great.  Only problem with it now is that everytime i reboot the OS and launch firefox, it starts in offline mode.  Not sure why.

Also, when I tried to install a .deb package I tried this:
```
cd desktop
```
But it didn't get me anywhere, got an invalid location error or something.
Then I tried to just:
```
sudo dpkg install *filename*.deb
```
Hoping that it would just get it right, but it didn't.  If I don't specify a directory with the "cd" command, where does linux assume the files are located?

there are two problems there
1) its not desktop but Desktop (windows wont complain of such thing but linux will case is important

2) you are in incorrect directory when doing ```
sudo dpkg install *filename*.deb
```

there is no "directory assumtion" the directory is your working directory which happens to be your home directory when you start terminal (/home/username/ so you need to cd Desktop if files are on desktop.

---

### Post by RequinB4 on 2008-06-18
> **broncbuster said:**
> Thanks, it works great.  Only problem with it now is that everytime i reboot the OS and launch firefox, it starts in offline mode.  Not sure why.

Also, when I tried to install a .deb package I tried this:
```
cd desktop
```
But it didn't get me anywhere, got an invalid location error or something.
Then I tried to just:
```
sudo dpkg install *filename*.deb
```
Hoping that it would just get it right, but it didn't.  If I don't specify a directory with the "cd" command, where does linux assume the files are located?

also note that these instructions assume you downloaded the .deb onto your Desktop (which is located in /home/USER/Desktop where USER is your username). 

Probably not important - Some tidbit about syntax to help explain what is going on in the terminal - the character "~" means /home/USER/ where USER is your username.  It's your user "home" directory - because that's where you're going to put all the files you'll be working with that aren't configuration files etc that you don't have the permission to mess with by default.  So when you open the terminal, it automatically starts with the "~" location, so doing
```

cd Desktop

```

moves you from ~ to ~/Desktop

 I could go on about the details of how the filesystem works but I don't want to bore.

Also, there are some useful links in my signature.

---

### Post by broncbuster on 2008-06-18
THanks, that clears up a lot.  HOw does one uninstall a program via the terminal.  I"ve searched and found lots of articles on how tin install programs, but how do you uninstall?  I've tried:

```
man uninstall
man delete
man remove
```
with no luck

---

### Post by broncbuster on 2008-06-18
THanks, that clears up a lot.  HOw does one uninstall a program via the terminal.  I"ve searched and found lots of articles on how tin install programs, but how do you uninstall?  I've tried:

```
man uninstall
man delete
man remove
```
with no luck

---

### Post by Joeb454 on 2008-06-18
If you installed it from the repo's you can run ```
sudo apt-get remove <package>
``` Where <package> is the package name, lets say for example it's the flash plugin, you would run ```
sudo apt-get remove flashplugin-nonfree
``` Hope that helps :)

---

### Post by MasterSander on 2008-06-18
To uninstall a deb package:

```
sudo dpkg -r <package name>
```

and for the repositories

```
sudo apt-get remove <package name>
```

---

### Post by MasterSander on 2008-06-18
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

This was also very handy to me when I began with ubuntu.

---

### Post by broncbuster on 2008-06-18
Thanks.  Just what I was looking for.  

Next, when i connect a flash drive to the computer, i want to connect to it and manage it via terminal.  I can't seem to find where the directory is that hosts my flash drive.  When I go to places, it shows FLASH DRIVE, but i cannot find it in terminal with 'cd' function.  Please help

---

### Post by Joeb454 on 2008-06-18
Try ```
cd /media
ls
``` It'll most likely be in there somewhere :)

---

### Post by cmnorton on 2008-06-18
... and don't forget to install build-essential.

That will accomplish a few things such as getting you used to working in an X-term, and will get you a compiler, so you can start playing around.

1) Go to an X-term (command line)

2) Enter sudo apt-get -y install build-essential

Answer the password prompt with the password of the user that just issued the apt-get command, if that user installed the system. I am assuming you installed the system, so use your password. This runs apt-get as root.

---

### Post by broncbuster on 2008-06-24
How do you detach a program from the terminal.  for example...I want to run firefox from the terminal but I don't want that terminal to be tied up with firefox.  HOw do I do this?

Steve

---

### Post by sdennie on 2008-06-24
You can use:

```

disown

```

To uncouple the last background process from the current shell or

```

disown -a

```

To uncouple all the shells background processes.  This assumes you've started firefox like this:

```

firefox &

```

Or you started it normally, hit Ctrl-Z in the terminal and then typed:

```

bg

```

---

### Post by jordanmthomas on 2008-06-24
> **vor said:**
> You can use:

```

disown

```

To uncouple the last background process from the current shell or

```

disown -a

```

To uncouple all the shells background processes.  This assumes you've started firefox like this:

```

firefox &

```

Or you started it normally, hit Ctrl-Z in the terminal and then typed:

```

bg

```

To add to that, 
```
nohup program &
```
will also work

---

