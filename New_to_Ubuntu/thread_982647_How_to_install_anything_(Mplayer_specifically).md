---
title: "How to install anything (Mplayer specifically)"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by phillostrate on 2008-11-14
So I'm brand new to Ubuntu.  I've never used anything like this, and I'm finding it to be a little daunting.  I really like this OS, but what I don't understand is how to downloand and install programs.  I've used windows my entire life, which basically means I've always used a GUI.  If I wanted a media player I'd just download it, click on the icons and off I went.  If I needed codecs, I was prompted to download them and then they were automatically installed.

I understand that Ubuntu is not Windows.  There's more to it.  I'm okay with that.  I like to learn new things.  The problem is I'm not really finding help for seriously absolute beginners like myself.

For instance; I'm trying to get Mplayer.  There seems to be a lot of advice out there, but none of it really makes any sense to me.  Most of the time somebody just throws up a bunch of code as instructions.  I don't know what that means.  Do I need to download something, then type the code into the terminal?  Do I just type the code?  In my research I've found if you want a GUI for Mplayer you have to "build it", you'll also need to find a skin.  I'm really confused.  

So here's my request for anyone willing to take the time to help me learn how Linux works.  I'd like to download and install Mplayer.  I need step by step instructions.  Pretend you're talking to a child, since clearly I'm not bright enough to grasp this as a functioning adult.  Tell me what to download, and to where.  Tell me if I need to extract files, and to where.  Tell me to open the terminal and what to type, and what I should expect.

By this point it's probably clear to you that I really don't know what I'm doing.  But I feel like if I can learn to install Mplayer, it'll go a long way towards understanding how to install other programs.

So, any takers?  If not I guess I'll have to go buy stupid windows for hundreds of dollars, but I'd really rather learn this stuff.  It'd be cool to be knowledgeable about these things.  

Oh, incidentally... I do need that GUI for Mplayer.  I don't really understand why anyone wouldn't want that.  Anyway, thanks in advance for any help or advice, or direction to a useful site.  

-Phill

---

### Post by taurus on 2008-11-14
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by compnut41 on 2008-11-14
What you need to do is go under applications and chose Add/Remove applications at the bottom of the menu. When the window pops up there should be a box at the top that says "Supported Applications" use the drop menu to select all available applications. From this point you will have applications to download just check or uncheck the boxes and press Ok.

Good Luck

---

### Post by compnut41 on 2008-11-14
Ah man, dude ruin my fun with the website.

---

### Post by jimmy the saint on 2008-11-14
Things you need to understand.
Package management.  Rahther than surf the web looking for software to install that may or may not be what you need or bork your system, we have repositories.  repositories are like warehouses for packages (software) that your system can install as neccessary.  The easiest way to do this is to open synaptic (system>administration>synaptic package manager) and let it do the work for you.

Installing a package.
in the search box in synaptic type the name of the program you want.  MPLAYER.  look for an entry that says MPLAYER.  click the box to the left of it.  if it tells you it needs to install additional items, click ok.  When you are done selecting software, click on APPLY at the top.  It will automatically download and install your packages.

Then you can go into the application menu and enjoy MPLAYER.

Easy as pie and there was no need to surf around lookin for it!  In addition you can rest assured that all of the packages have been tested by the devs to be compatible with your system and are not virus, malware, spyware, crappy programming, or otherwise junk laden!!

linux is easier than it looks!!

feel free to ask more quetions!

---

### Post by luckis on 2008-11-14
Hi there! 
Welcome to the world of Linux!! :)
Since you have ubuntu you hardly need any commands in the terminal or shell to call things right! ( but when you start experimenting with the "shell" you 'll find out that it is your best friend)
To install Mplayer you 'll have to go to either : Applications --> Add/Remove
or
System --> Administration --> Synaptic Package Manager
then in the search box you write Mplayer and there you go, you ll have in front of you everything that is related to Mplayer including the skins!!
You check it and then you apply the changes...thats it! :)
Then there is the hard way (not recommended for new users) you download the sources, you extract them, then you change directory to the unpacked folder and then you use
**./configure &#8211;enable-gui &#8211;enable-menu ; make ; sudo make install**
if you don't want the gui you leave out the &#8211;enable-gui &#8211;enable-menu! :)
Hope it helps

---

### Post by doas777 on 2008-11-14
the psychocats tutorial linked above is your best resource for learning to install stuff the ubuntu way.

my advice is get used to issuing short commands in your terminal. it's not hard, and you'll pick it up quickly. you;ll find that many tutorials online use the command line, rather than GUI tools, just because it's easier to write, and it works more consistently (because everyone's terminal looks the same).

if I wanted to install mplayer, I would open a terminal and type:
```
sudo apt-get install mplayer
```

now, most of the tutorials of which you speak, expect you to paste their commands (code) into a terminal. this is usually safe, but be careful to look at the commands before you issue them. people can trick you into doing damaging things that way.

good luck,
franklin

---

### Post by andrew.46 on 2008-11-15
A big second for psychocats's pages :-). MPlayer is however a special case in that the Ubuntu repositories carry a version that is quite old and is by no means a *full* version, it has been reduced in stature for perceived legal problems of distribution.

  Andrew

---

