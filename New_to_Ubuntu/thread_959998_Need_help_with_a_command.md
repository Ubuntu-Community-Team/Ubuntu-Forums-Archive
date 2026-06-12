---
title: "Need help with a command"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-10-27
I'm new to Ubuntu and commands. I have assigned a custom command (see below) that acts upon any rar file. Whenever I right-click on an rar file, I select "Open with "unrar"", and it extracts the archive (or partial archive) to my home directory. It works great. 

The only problem is, I want the archive (or partial archive) extracted to whatever directory the rar file is in, so I don't need to scroll down to find it in my home directory. 

How can I change the command below so that it will extract the archive (or partial archive - I don't always have all the parts) to whatever directory I happen to be working in? Or if I could extract it to my desktop, that would work for me too. Thanks.

```
unrar e -kb
```

---

### Post by ukera on 2008-10-27
no offence but some people need to learn to google.  you get faster damn responces then posting on forums..  here's the correct command with parameters..

[PHP]unrar <command> [-<switch 1> -<switch N>] archive [files...] [path...]

[/PHP]

---

### Post by ad_267 on 2008-10-27
Can't you just right click on the file and select "Extract here" to accomplish this?

---

### Post by ukera on 2008-10-27
seriously.. listen to the guy above.  if you want to move it.  drag and drop works perfectly fine..

---

### Post by stoogiebuncho on 2008-10-27
Ukera's mood seems to match the profile pic quite nicely. :)

---

### Post by WWSmith36 on 2008-10-27
I think the envirnoment variable you are looking for is $PWD

---

### Post by bobsmith2 on 2008-10-27
> **ad_267 said:**
> Can't you just right click on the file and select "Extract here" to accomplish this?

No. Not for partial files.

---

### Post by bobsmith2 on 2008-10-27
I haven't been able to change this command (unrar e -kb) so that it will force the output to the directory I'm in despite trying various switches and commands. WWSmith36, I tried using $PWD and couldn't get it to work (thanks for your suggestion). Maybe I missed the correct sequence or something. But shouldn't the "e" in the command (which means "extract files to current directory") force the output to the directory I'm in? Listing a specific path doesn't seem to work either. Perhaps this is related to the bug that prevents right clicking on the file and selecting "Extract here" to accomplish the extraction of partial archives:
[http://bugzilla.gnome.org/show_bug.cgi?id=504584]("http://bugzilla.gnome.org/show_bug.cgi?id=504584")

I'm OK with the way it works now... I'm just trying to learn and get it perfect. I find that by solving small, relatively insignificant issues, I build the skills to solve more serious ones down the road. If anyone knows, off the top of your head, how to write this command, I'd appreciate a point in the right direction. Thanks. 

To anyone who sees this (except ukera): PLEASE DO NOT READ WHAT FOLLOWS. I  don't want to waste anyone's time or offend any of you who do such a great job of helping those of us who are trying to abandon Windows. Thank you. 


--------------------------
 

Regarding ukera's hostile comments and erroneous advice...

> **ukera said:**
> no offence but some people need to learn to google.  you get faster damn responces then posting on forums..  here's the correct command with parameters..

[PHP]unrar <command> [-<switch 1> -<switch N>] archive [files...] [path...]

[/PHP]

This reply is completely useless. Before I describe why it's useless, I'll point out that this is actually the first time I have encountered a condescending, hostile, insulting (and erroneous) reply to a request for assistance on this forum. So my sincere thanks goes out to all the posters here who are so helpful to those of us who want to dump Windows, but are intimidated by Linux (especially the command line) and need some help to get started. There is one thing I have noticed on this forum, and it is also often true in life: Those who know the most are usually the kindest and most genuinely helpful, and those who know the least can usually be identified by their arrogance and their errors (uncommon here, I know, but there are a few).

Ukera... why would I say that your advice is useless (besides deliberately alienating new users)? First, you simply copied and pasted the command line parameters - which is easily obtained by typing the command (in this case, "unrar") into the terminal. Suggesting to a new user that  command line parameters should be obtained by using "google" isn't necessarily wrong, it's just clumsy, second-rate advice. The command line information you posted is available in literally 2 seconds via the terminal - that is the correct way to obtain such information. Obviously, I had already obtained that before posting my question; I just can't get it to work. But that's not the worst of your "advice":

> **ukera said:**
> seriously.. listen to the guy above...

Here's what the "guy above" said: "Can't you just right click on the file and select "Extract here" to accomplish this?"  The "guy" who posted that posed it as a question. He didn't know if he was correct, but he threw it out there, just in case it helped, and I appreciate his comment. Since this is a forum for the newest of the new ("Absolute Beginner Talk"), it's best not to assume that a questioner knows the basics. You, however, claimed to KNOW him to be correct, but you were wrong. You can't right click on the file and select "Extract here" to accomplish the extraction of partials, and I specifically referenced partials in my question. There's a bug that prevents it from working:
[http://bugzilla.gnome.org/show_bug.cgi?id=504584]("http://bugzilla.gnome.org/show_bug.cgi?id=504584")
Seriously, why would you post a snotty, hostile, useless comment when you are absolutely clueless about the topic? This is a smart group. When you feign knowledge you're probably going to be exposed. When someone displays gross ineptitude in the area of social skills, they should be especially careful not to display the same level of incompetence in their technical knowledge.

> **ukera said:**
> ...if you want to move it.  drag and drop works perfectly fine..

Really? Ubuntu has drag and drop? Pfft... Are you serious?  What? Do you think this is a Mac forum or something?  I could be wrong, but by the quality of your responses you appear to be a guy who uses Ubuntu as-is, right out of the box (not that there's anything wrong with that). You don't know much - I get that.

> **ukera said:**
> no offence but some people need to learn to google.  you get faster damn responces then posting on forums...

There's seldom a question posted on this forum that couldn't be answered by searching elsewhere, if one digs deep enough and long enough. The point is, people seeking assistance shouldn't be afraid to post here if they try, and fail, to find a solution. And they certainly shouldn't feel the need to justify a question to some lightweight who has absolutely no clue about the topic. Furthermore, I'm finding that there are plenty of questions posted here that NOBODY seems to be able to answer - perhaps this will end up being one of them - we'll see. And regarding the various guides that are as readily available as a Google search... most of the beginners' guides I've read are a rehash of the rather simple and obvious. Much of the rest presumes considerable pre-existing expertise. In other words, Ubuntu appears to be very user friendly for both grandmas and Linux pros. But it doesn't seem to be all that user friendly for that in-between crowd - Windows power-users who don't want to use Ubuntu as it exists out-of-the-box. The problem is, these are the folks who service the PCs of friends, business associates, and family. They are the ones who are in a position to convince other desktop users to make the switch to Linux (and with increasing numbers will come better proprietary hardware support, games, and all the rest). So when some sniveling, know-nothing tries to drive these folks away, the entire Linux movement is held back a bit. 

So... ukera, in the future, any questions I pose are not intended for you. Any question posed, henceforth, is directed to anyone in this community EXCEPT you. I'd suggest you add my name to all those sticky notes on your PC that list all those who would rather live with Windows for the rest of their lives than deal with a guy like you (and surely a guy like you must already have such a list going). Seriously... even if you KNEW the answer to a question (which is highly unlikely), I'd rather go without the information than get it from you. Some people have that effect on others.

---

### Post by ad_267 on 2008-10-27
Ok I think I understand your problem. Maybe the best way is to write your own script that will do this. Here's an example that I think does what you're after.

```
#!/bin/bash

# Get file path from input
FILE=$1

# Get directory of file and file name
DIRECTORY=`dirname "$FILE"`
FILENAME=`basename "$FILE"`

cd $DIRECTORY
unrar e -kb "$FILENAME"
```

You can save this in somewhere like ~/.scripts as myunrar for example and then for the custom command you can use /home/your_username/.scripts/myunrar

I don't think $PWD will work because it will probably run from your home directory and just give the full path to the application being run.

Another way of doing this would be to create a Nautilus script but I think this method is the easiest way to do it.

---

