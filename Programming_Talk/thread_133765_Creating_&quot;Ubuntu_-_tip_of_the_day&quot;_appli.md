---
title: "Creating &quot;Ubuntu - tip of the day&quot; application"
date: 2006-02-20
forum: Programming Talk
---

### Post by Garyu on 2006-02-20
Hey,

I want to make a "Tip of the day" application for Ubuntu. The thing is, I have never written anything for linux and in general my programming experience is limited. I have found and installed glade and anjuta, but it seems to me that this kind of thing ("Tip of the day"-applications) are quite common, and generally sticks to a certain design and appearance. 

What I wish for is a simple template for "Tip of the day" which I can just insert my information into, maybe even without a compile. What do you think would be the best approach for this? There should be room for different language translations as well. 

My aim is to make a general Ubuntu "Tip of the day" to be included in Dapper and help new users explore their new OS.

---

### Post by gord on 2006-02-20
bit late for dapper, but i would suggest python and wxpython or pygtk to handle the gui stuff to display. n then use xml or just a plain text file that you read to hold the 'tips'


allthough personally i can't stand those things and allways, allways check the disable box ;)

---

### Post by majikstreet on 2006-02-20
hmph. something that simple could probably be made in bash and then using zenity.. but don't ask me how lol.. my guess would be to take a file, use a certain syntax and make the different boxes, then have a bash program pick a random one, strip out the title and the actual tip, then output that into zenity..

but that's just me.

---

### Post by Plank117 on 2006-02-21
```

import javax.swing.*;

public class TipOfTheDay
{
     public static void main(String args[])
     {
           //Giant pile 'o tips goes here (use an array)
           //Tips like: "Did you know that bad things happen if you overwrite /usr/X11?," etc.
           //^ Sadly enough, I actually managed to do this once ^

           //random number generator grabs tip from giant array

           JOptionPane.showMessageDialog(null, tip);
           
           System.exit(0);
     }
}

```

Use Java, and it's just that simple...

---

### Post by Garyu on 2006-02-21
[QUOTE=Plank117]```

public class TipOfTheDay
{
     public static void main(String args[])
     {
           JOptionPane.showMessageDialog(null, tip);
           System.exit(0);
     }
}

```
Use Java, and it's just that simple...[/QUOTE]

Well, thank you for the tip, it lead to me finding Eclipse which seems to be a GREAT environment for java development. But when I try to run the above code a popup flashes by, without waiting for an OK or anything. So it doesn't work as well as I would hope. :cool:

---

### Post by Zeroangel on 2006-02-21
That's quite and ambitious project you are trying to start. Yeah, Tips would be useful for newbies. However there are 'problems' with the current help systems:

1) Tip of the day:  Popup windows are interpreted by most users (and i'm deflecting here) as annoyances that get in the way of actually using the machine. Tip windows, in their current form also hold very limited amounts of information.

2) Help Menu: Navigation takes too long, very clunky. It would be nice if the help menu included a global search feature (ie: Windows help), and even a side pane which allows you to navigate much faster (ie: KDE Help).

I believe it would be better if there was a popup window on first boot (with a 'don't show this again' checkbox) that provided help on getting started with Ubuntu. For example, installing programs, links to the forums and wikis. Maybe even a pointer to setup wizards such as EasyUbuntu.

---

### Post by sapo on 2006-02-21
I think i'd like better a quote of the day.. or the howto of the day.. or the joke of the day :P

---

### Post by Garyu on 2006-02-21
[QUOTE=majikstreet]hmph. something that simple could probably be made in bash and then using zenity.. but don't ask me how lol.. my guess would be to take a file, use a certain syntax and make the different boxes, then have a bash program pick a random one, strip out the title and the actual tip, then output that into zenity..

but that's just me.[/QUOTE]

Majik, this actually does the trick. :)
```
#!/bin/bash
#
# Ubuntu tips
#
# Displays a random "daily tip" in a dialog box when called
# Usage: "sh ubuntutips.sh < inputfilename"
#
# Author: Dan-Erik Lindberg (Garyu in the Ubuntu forums)
#

# Read a line from the file
while read line
do
	number=${line:0:6}
	if [ $number = 1 ] 
	then
		echo ${line:0:6}
		zenity --title "Ubuntu daily tip" --info --text "${line:7}"
	fi
done

exit 0
```
My input file looks like this now:
```
1      Installing and configuring samba will let you share files with MS Windows-based computers over a network.
2      You can use ssh (secure shell) to share files with other unix-based computers on your network.

```
Works great, looks good, and very very simple. I have no linux programming experience and I have hardly touched the command line previously other than to do an apt-get or two, but even I managed to write this script and make it work. Now all I have to do is figure out a way to randomize the row numbers so that different tips come up each time.

I have to say, I don't know what I was doing before I started playing with Ubuntu, but I have sure missed out before. I love this game. :cool:

EDIT: One small thing is missing though... That small checkbox where it should say "Don't display this ever again"...

---

### Post by Garyu on 2006-02-21
[QUOTE=Zeroangel]1) Tip of the day:  Popup windows are interpreted by most users (and i'm deflecting here) as annoyances that get in the way of actually using the machine. Tip windows, in their current form also hold very limited amounts of information.

I believe it would be better if there was a popup window on first boot (with a 'don't show this again' checkbox) that provided help on getting started with Ubuntu. For example, installing programs, links to the forums and wikis. Maybe even a pointer to setup wizards such as EasyUbuntu.[/QUOTE]

I know this is a potential annoyance, but if you can get a "Don't show again" checkbox as you mention, I think the usefulness of this for new users would overcome the annoyance of checking that box once and clicking OK.

A different approach would be to just include it as a panel applet by default. Easy to remove, easy to click once or twice or many times if you feel like being inspired. :cool:

---

### Post by heimo on 2006-02-21
[quote=Garyu] Now all I have to do is figure out a way to randomize the row numbers so that different tips come up each time.[/quote]

See this example:
[http://www.tldp.org/LDP/abs/html/randomvar.html#PICKCARD](http://www.tldp.org/LDP/abs/html/randomvar.html#PICKCARD)

---

### Post by soonindallas on 2006-02-21
[QUOTE=sapo]I think i'd like better a quote of the day.. or the howto of the day.. or the joke of the day :P[/QUOTE]

don't you have wanda ?

---

### Post by sapo on 2006-02-21
[QUOTE=soonindallas]don't you have wanda ?[/QUOTE]
What's that?

---

### Post by heimo on 2006-02-21
[quote=sapo]What's that?[/quote] Right click on panel->Add to panel->search fish->Add

Also try running *fortune *on command line.

---

### Post by UbuWu on 2006-02-21
Only thing that is still lacking is a fortune-ubuntu-hints package (there is a fortune-debian-hints package available from the repo's).

---

### Post by keyboardashtray on 2007-07-25
To revive an old thread here: is there an Ubuntu tip of the day program yet? I would love that - I was browsing Add/Remove and I saw one "KTip" for Kubuntu, but nothing for Ubuntu :(

---

### Post by Note360 on 2007-07-25
this is a good idea... However, we should redesign the idea of tip popups. I mean i hat them, even if the tips are good. ESPECIALLY in GIMP and if I had it in and OS I might consider dropping into a new OS (or distro for me).

What about a icon in the panel that whn clicked it will display a tip. Very few people will use it but it would be less annoying than popups and those that need it will get it. After that is implemented, implementing a basic help system (like man pages?) would be  the next step. THis help system would be easy to get around, maybe even running in the browser (Javascript, html/xml/plaintext this way it doesnt use apache. Unless you want to run it off a server on the net for general use, but then we would need mirrors).

I myself would enjoy working on the second one. Actually a browser one would be cool, because then just make a page that will pop up random tips in it and put a link somewhere maybe even suggest it for the main page?

---

### Post by keyboardashtray on 2007-07-25
Well a net based one would have the advantage of having a more flexible and up-to-date tip list. FAQ from forums, or wherever. I think it is easy enough to have a "Don't Show Tips" checkbox, and assuming it was gotten from the repos anyone who didn't want tips wouldn't install it in the first place. If it actually got to the point it was packaged with future Ubuntu, well then I guess the checkbox or uninstalling it would be an option. In a more advanced program, a general tip could have links to online documentation or help files, a sort of "more info" button. Tips could be little tidbits like console commands, customization options, and even definitions on common terms in Linux that a brand new user might not be familiar with.

---

### Post by AlexThomson_NZ on 2007-07-25
I think this is a great idea, and a pretty good/feasible first program too!

I like the fact that it can be extendable to be either Tips/Messages/Jokes/Quotes.  Would not be that keen on having to connect somewhere on the internet to get them, otherwise you have the headache of managing joke/message/etc repositories, making sure the links are active, competing sources, etc.  Just update the jokes/quotes/etc. with the program and let the automatic updater take care of it.

I think this would be a better solution that Wanda

---

