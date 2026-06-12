---
title: "Adventures in ubuntu - complete noob"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by alboy1975 on 2013-03-10
Hi guys I'm completely new to ubuntu/Linux, but I feel I can't call myself a true geek until I have Linux on at least one computer (I'm using an old Asus Aspire 2920 that has been gathering dust for years).  I've managed to install ubuntu 12.10 and the attached image shows how I have it set up:

[ATTACH=CONFIG]240025[/ATTACH]

  I would like to get it set up just the way I like it before looking into things further.  I would like ubuntu to boot up as shown in image but on panel 2 and 3 of the switcher I would like to have firefox fully open (panel 2) and Open Writer fully open on panel 3.  I know this will slow down boot, but should improve productivity once up and running.  Is this possible?

 I would also like to know where to find more out about the terminal.  Through the set up process I've deduced that “sudo” tells the teminal to do something, usually something like get-apt (get an application from a repository), or install  an application.  A common process would be something like this:
 
 
[LIST]
[*]sudo <connect to some repository> 
[*]sudo <update repository information> 
[*]sudo <get-apt <get application>> 
[*]sudo <install said application> 
[/LIST]
 
Basically what I'm asking is, can I have different programmes opening on different panels of the switcher at boot and where do I find out more about terminal and the basics of linux?

---

### Post by Christmas on 2013-03-10
I don't know about the panels, I'm using KDE. Google for something like "program autostart cairo dock" or "cairo dock config", I've personally never used it.

As for the terminal, a good place to start would be the [Wiki]("https://wiki.ubuntu.com/"). [Here]("https://help.ubuntu.com/community/UsingTheTerminal")'s a terminal introduction, and [this]("https://help.ubuntu.com/community/CommandLineResources") lists a lot of command-line related tutorials. Two places I always recommend to beginners when it comes to learning to work in the terminal are [tuXfiles]("http://www.tuxfiles.org/") and [LinuxCommand]("http://linuxcommand.org/"). Hope this helps, and keep in mind it's going to be fun, probably a little hard to grasp at first though. Have a look at [these]("http://www.psychocats.net/ubuntu/") tutorials too as an introduction to Ubuntu.

PS: sudo gives root privileges, meaning you can install and access files which are owned by the user root. You can read more about it on the Wiki page, [here]("https://help.ubuntu.com/community/RootSudo"). It's just a command, like so many others that you can type in a terminal. For example, type **ls /usr/bin** to see installed programs. Any of these programs can be run by typing their name in the terminal.

---

### Post by alboy1975 on 2013-03-10
cheers will 'av a look

---

### Post by Lightning Dragon on 2013-03-10
Hello,

To learn more about Ubuntu, the terminal, commands and the like please consider the following links;

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://www.amazon.com/s?ie=UTF8&field-keywords=Ubuntu&index=blended&link_code=qs&sourceid=Mozilla-search&tag=wwwcanoniccom-20](http://www.amazon.com/s?ie=UTF8&field-keywords=Ubuntu&index=blended&link_code=qs&sourceid=Mozilla-search&tag=wwwcanoniccom-20)
[http://www.webring.org/hub/linux?w=1440;rh=http%3A%2F%2Fwww.linuxnewbieguide.org%2F;rd=1](http://www.webring.org/hub/linux?w=1440;rh=http%3A%2F%2Fwww.linuxnewbieguide.org%2F;rd=1)
[http://freshtutorial.com/ubuntu-beginner-tutorial-interface/](http://freshtutorial.com/ubuntu-beginner-tutorial-interface/)

I am not entirely sure you can set it up, through "easy" options at least, to boot up on separate panels (workspaces). However, I have searched it up and a lot of people have asked the same question (assuming you mean 'workspaces') so hopefully the following can help you;

[http://askubuntu.com/questions/73822/startup-programs-in-particular-workspace](http://askubuntu.com/questions/73822/startup-programs-in-particular-workspace)
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
[http://ubuntuforums.org/showthread.php?t=903196](http://ubuntuforums.org/showthread.php?t=903196)

I hope this helps!

EDIT:

8 minutes too late; stupid connection. Well, I still hope it helps. :)

---

### Post by deadflowr on 2013-03-10
```
[COLOR=#000000]Through the set up process I've deduced that “sudo” tells the teminal to do something[/COLOR]
```

The sudo command allows you to run a command that needs administrator privileges.(root access) 
This is done when changes are being done to the system.
Not all commands will require this.
If you try running the command apt-get update, you'll get a permission denied warning. Throw in a sudo and that tells the system that you are allowed to do what you're trying to do.

Here's more on sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Read delightfully.

---

### Post by alboy1975 on 2013-03-10
Thanks guys.  Quite excited about ubuntu, had this laptop lying about for ages and after a few hours of fiddling around I have a fully funtioning computer, with word processing, email and everything else i'd need.  Also looks quite slick, pyso osx look

---

### Post by BlinkinCat on 2013-03-10
Hi,

The NewDocs link on my signature will provide the majority of Ubuntu Documentation.

Cheers - :)

---

### Post by Bashing-om on 2013-03-10
alboy1975;
+1 on NewDocs, will keep you occupied for an extended period !
[INDENT=2]
Welcome to ubuntu 

[/INDENT]

---

### Post by alboy1975 on 2013-03-10
hehe, joy

---

### Post by Gareth Edwards on 2013-03-10
As a fellow noob, I'm enjoying working through these basic lessons for terminal:

[http://cli.learncodethehardway.org/book/ex1.html](http://cli.learncodethehardway.org/book/ex1.html)

---

### Post by alboy1975 on 2013-03-11
[ATTACH=CONFIG]240054[/ATTACH]

I've made this cheat sheet from the terminal information on newdocs.  I wanted  to upload the spreadsheet, but was unable to.  If you fancy having a look and tell me what you think i'd appreciate it.  The information seems quite basic and I'm not sure where to go next.

---

### Post by Cheesemill on 2013-03-11
Some of your cd commands are wrong, they should be...
```
 cd /
```
Change to root directory.

```
cd ~
```
Change to $HOME directory

Although the last command is correct there is also a shorter version, just using cd by itself will change to your home directory.

The most useful command on a Linux system is the man command, it will show you the manual page for a specific command, for example...
```
man df
```
will show all of the available switches and their meanings for the df command (screenshot attached).

[[IMG]http://ompldr.org/taHE2NQ[/IMG]]("http://ompldr.org/vaHE2NQ")

Edit - Another good cheat sheet can be found [here]("http://files.fosswire.com/2007/08/fwunixref.pdf").

---

### Post by alboy1975 on 2013-03-11
[ATTACH=CONFIG]240056[/ATTACH]

this is what comes up when i do cd / and cd ~ respectively.  cd / takes me to the core files of ubuntu and cd ~ takes me to home, showing documents, pictures etc.  Is there something wrong with my setup?

---

### Post by Cheesemill on 2013-03-11
Your setup is fine.

Your cheat sheet, however, says the 'cd /' changes to your home directory and 'cd ~' changes to the root directory. This is the wrong way round.

---

### Post by alboy1975 on 2013-03-11
Must have been typo.  I'll use your cheatsheet anyway, seems more comprehensive.  Cheers mate.

---

### Post by Bashing-om on 2013-03-11
alboy1975; Good start to your adventure.
do in terminal :
```
man man
``` for a good read.[INDENT]
again, welcome to our world

[/INDENT]

---

### Post by alboy1975 on 2013-03-12
Think I might be the man.  I have managed to get firefox and thunderbird to launch in different workspaces at boot.  Here's how:

Using compizconfig/Place Window/Fixed window placement/windows with fixed viewport.  Under this you put the x and y plus the application you want to load (See below)

[ATTACH=CONFIG]240091[/ATTACH]

workspace1 = x1 y1
workspace2 = x1 y2
workspace3 = x2 y1
workspace4 = x2 y2

After this is done set application in Startup Applications.

NB: if you have firefox running I would advise disabling last session recovery - in url address line about:config <enter> - browser.sessionstore.resume_from_crash <false>.  By doing this, when you reboot firefire will not try and recover last session and will give your normal homepage.

---

### Post by Cheesemill on 2013-03-12
Another solution is to use the wmctrl command to play about with windows from the command line.

For example...
```
wmctrl -r "Firefox" -t 2
```
will move the Firefox window on to workspace number 2 (start counting at 0) - again, 'man wmctrl' is our best  friend.

You could write yourself a little script to manage starting up your applications, just open a text editor (gedit) and type (or copy/paste) the following...
```
#!/bin/sh

# Wait for 10 seconds to ensure the desktop is started
sleep 10

# Launch our require applications
firefox &
thunderbird &

# Wait another 5 seconds to ensure applications have started
sleep 5

# Move applications to the correct workspaces
wmctrl -r "Firefox" -t 1
wmctrl -r "Thunderbird" -t 2
```

Create a ~/bin directory and save the script in it as startupscript.sh

If you create a ~/bin directory, it is automatically added (once you've logged out and back in again) to the paths that your computer looks in when you type a command, so you can now type startupscript.sh whilst in any directory and your script will be run.

Make the script executable either by right-clicking on it and going to Properties > Permissions and checking the Execute box or you can use the terminal command...
```
chmod +x ~/bin/startupscript.sh
```

You can now just add the startupscript.sh command to your startup applications (just search the dash for the 'Startup Applications' application).

Probably not as quick as your method but I'm trying to introduce some of the things that can be done using the terminal - you did ask in the OP after all :)

[COLOR=#0000ff] [SIZE=1]PS - I don't think I've ever written a sentence with startup and application in 3 times each before.[/SIZE][/COLOR]

---

### Post by alboy1975 on 2013-03-12
indeed i did.  And thanks.

---

### Post by alboy1975 on 2013-03-12
script might be better, because somethings thunderbird doesn't connect to email server because computer is still connecting to wifi.  the sleep function could solve this problem.

---

