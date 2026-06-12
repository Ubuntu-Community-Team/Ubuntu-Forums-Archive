---
title: "How to personalise the greeting for your shell"
date: 2008-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by ChameleonDave on 2008-07-03
[FONT="Courier New"][B]
********************
****INTRODUCTION****
********************
[/B][/FONT]

I've been looking at Linux Mint, which sets up the shell so that you get a "fortune cookie" message in a speech bubble every time you open a terminal.  It seemed to me that the message was neither useful nor entertaining, and that the speech bubble took up too much room.

This got me thinking about other uses for the greeting.  Surely there is some other more useful bit of text that your terminal could greet you with?

So, I have compiled this list of suggestions for you.

To use any of them, first back up your profile by going to the command line (e.g. by opening a program such as Konsole, GNOME Terminal, XTerm or RXVT) and entering the following command:

```
sudo cp /etc/bash.bashrc  /etc/bash.bashrc.backup
```

Now, we want to add an extra line to the end of this file.  Do so like this:

```

sudo -s
echo "*fortune*" >> /etc/bash.bashrc
exit

```

The reason we're getting root access with "sudo -s" and exiting afterwards is that you can't use ">>" with a command that begins with "sudo".  Annoying, I know.

Alternatively, you can add the command to the end of the /etc/bash.bashrc file by opening it as root with your favourite text editor.  For example, like this:

```
sudo *nano* /etc/bash.bashrc
```

By all means, try out these commands in your terminal to see if you like them, before adding them to that file.

[FONT="Courier New"][B]
********************
*SUGGESTED COMMANDS*
********************[/B][/FONT]

OK, now for the suggested commands.  In the above example, I put "*fortune*" because it is commonly used, but I don't particularly recommend it.  Instead try...

```
echo "CARPE DIEM QVAM MINIMVM CREDVLA POSTERO"
```
Rather than some (often offensive) fortune-cookie "joke", have your shell greet you with some sort of text which is significant or motivational to you personally.

```
date
```
Simple, elegant and useful.  You get a reminder of the date and time when you log in.

```
ddate
```
Not so useful, but entertaining if you are a [Discordian]("http://en.wikipedia.org/wiki/Discordianism").

```
who
```
If you are in the habit of logging on to various sessions at once (perhaps a couple of TTY sessions for admin tasks), or if your spouse logs onto the same computer, having a list of current sessions printed when you open a shell can be a helpful reminder to deal with them before you shut down.

```
uptime
```
Some people are obsessed with their uptime as though it reflected their sexual prowess or something.  Such people will love to be briefly reminded of it each time they open a shell.  It also provides brief info about the time and the number of users logged on.

```
free -m
```
Perhaps you're always pushing the limits of your RAM.  This will remind you of how much you have left.

```
df -h | grep "^/dev/"
```
If your root partition is 95% full, you may want to know about it before things start to fail.  This will give you a list of all drives and their current usage.

```
ls
```
The simplest and one of the most obvious of all, this command will just tell you what non-hidden files are in your current directory, which will normally be your home directory at that point.  If you tend to keep it full of clutter, then this is no good for you.  However, some of us keep it very clean, so this command will be a list of those projects we are currently working on.  A useful reminder.


[FONT="Courier New"][B]
********************
***EMBELLISHMENTS***
********************[/B][/FONT]

Since I'm trying to urge simple and hopefully useful greetings, I don't recommend that you use the following commands, but I give details here because people love this sort of thing.  It is kind-of cool.

To install any of the following embellishments, just type "*sudo apt-get install*" and then its name.  For each one, I will use the example of "ls".

```
ls | cowsay
```

This will put the text in a speech bubble being said by a cow.  Really.

Put "cowthink" instead for it to be a thought bubble.

Add "-d" to the end to make the cow look dead; "-s" to make it look stoned; "-p" to make it look paranoid.

Add "-f" and then the name of a different graphic if you're bored of the cow.  Try "tux" or "sodomized".

Add "-n" to stop the text in the bubble from wrapping.

```
ls | figlet
```

Converts the output to an ASCII-art-style rendering of the outlines of the letters of the text.

```
ls | toilet
```

Converts the output to a blocky-looking ASCII-art-style rendering of the text.

*Toilet* is an improvement on *figlet*.  However, make sure you have *figlet* installed too, because *toilet* is able to take advantage of the fonts that come with *figlet*.

With either command, add "-f" and the name of a *figlet* font such as "banner", "big", "small", "block" or "digital".

With *toilet*, add "--gay" or "--metal" for nice colourful effects.

[FONT="Courier New"][B]
********************
*****THAT'S ALL*****
********************
[/B][/FONT]

I hope you've found this how-to helpful.

If you want to make the greeting come up for one user only, then read the comments about ~/.bashrc in this thread: [http://ubuntuforums.org/showthread.php?t=32076](http://ubuntuforums.org/showthread.php?t=32076)

Finally, here are two examples:

1)

```

ls -B | grep "\." | cowsay -f tux -n

```

...will output...

```

 __________________________
/ Cool_script.sh           \
| CV.odt                   |
| PhD_thesis.latex         |
\ Translation.zabw         /
 --------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

```

2)

```

date | toilet

```

...will output...

```

&#9600;&#9627;&#9624;&#9612;       &#9628;&#9624;  &#9628;   &#9630;&#9600;&#9622; &#9630;&#9600;&#9622;&#9630;&#9600;&#9622;  &#9612; &#9612;&#9630;&#9600;&#9622;  &#9612; &#9612;&#9630;&#9600;&#9622; &#9627;&#9600;&#9624;&#9630;&#9600;&#9622;&#9600;&#9627;&#9624; &#9630;&#9600;&#9622;&#9630;&#9600;&#9622;&#9630;&#9600;&#9622;&#9630;&#9600;&#9622;
 &#9612; &#9627;&#9600;&#9622;&#9612; &#9612;  &#9616;&#9612; &#9612;&#9616;    &#9604;&#9624;  &#9623;&#9624; &#9604;&#9624;&#9616;&#9612;&#9626;&#9604;&#9612; &#9623;&#9624;&#9616;&#9612;&#9626;&#9604;&#9612;&#9626;&#9604;&#9612; &#9625;&#9604; &#9626;&#9604;  &#9612;   &#9623;&#9624;&#9612;&#9630;&#9612;&#9612;&#9630;&#9612;&#9626;&#9604;&#9624;
 &#9612; &#9612; &#9612;&#9612; &#9612; &#9612;&#9616;&#9612; &#9612;&#9616;   &#9622; &#9612; &#9623;&#9624; &#9622; &#9612;&#9623;&#9622;  &#9612;&#9623;&#9624; &#9623;&#9622;  &#9612;&#9622; &#9612; &#9612;  &#9622; &#9612; &#9612;  &#9623;&#9624; &#9627; &#9612;&#9627; &#9612;&#9612; &#9612;
 &#9624; &#9624; &#9624;&#9629;&#9600;&#9624; &#9629;&#9624;&#9629;&#9600;&#9624; &#9624;  &#9629;&#9600;  &#9600;&#9600;&#9624;&#9629;&#9600; &#9629;&#9624;  &#9624;&#9600;&#9600;&#9624;&#9629;&#9624;  &#9624;&#9629;&#9600;  &#9600;&#9600;&#9624;&#9629;&#9600;  &#9624;  &#9600;&#9600;&#9624;&#9629;&#9600; &#9629;&#9600; &#9629;&#9600; 


```

Enjoy.

---

