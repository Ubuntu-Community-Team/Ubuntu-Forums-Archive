---
title: "The best way to get help"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Pro-reason on 2008-09-18
I've answered a lot of questions on these forums, and I keep on seeing the same questions coming up.  A lot of time could be saved by the help-seeker providing a bit more info.

So, before posting your first question about *Mounting, Codecs, Installing Software, a Program Not Working, *or* Permissions*, read the appropriate section below.  It will help you get better free tech support.

Do not reply to this thread with a question.  Create a [new thread]("http://ubuntuforums.org/newthread.php?do=newthread&f=326") with your question instead.

[SIZE="5"]Mounting[/SIZE]

If you're having trouble mounting (i.e. accessing) your Windows partition, or a USB external drive, or your mp3 player, etc, then a lot of time can be saved by opening up a terminal from the application menu, and typing these commands one after another.  In fact, copying and pasting is probably an even better idea.

```

cat /etc/fstab
sudo fdisk -l
sudo blkid
mount

```

That will produce a whole load of info which probably won't mean much to you, but if you copy and paste it for us, we will probably instantly be able to know how to fix your problem.

When pasting stuff like that, do remember to use the **#** button on the formatting bar.  This will insert [noparse]```
...
```[/noparse] tags around the info, to make it easier for us to read.

If you ask your question without providing this info, we'll just ask you to provide it, so you might as well pre-empt us.


[SIZE="5"]Codecs[/SIZE]

You want all your media files from Windows to work perfectly?  

There's not much point in posting a question, because we'll just tell you to enable the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository, and then install the codecs.


[SIZE="5"]Installing software[/SIZE]

In the menus, there's  “*Add/remove*” or “*Add and remove applications*”.  You can use that.  A slightly more powerful tool is “*Synaptic*”, which you can also find in the menus.  Both of these allow you to do a keyword search for stuff you might want to install.  This is what we do on Ubuntu, rather than the Windows practice of surfing to a website and downloading installers.

Before asking whether a given program is available for Ubuntu, search for its name in *Synaptic* first.

Before asking whether there is a program that does a certain thing (e.g. that edits documents), search for it by using some sensible keywords (e.g. “word processor”) first.  Skim through the descriptions of the suggestions that come up until you find something good.

If the version provided by Ubuntu in *Synaptic* is not quite as up-to-date as some version you have found elsewhere, please just use the stable version provided by Ubuntu.

If you absolutely must install something you've found on some website, then bear in mind the following:
[LIST]
[*]seek, read and follow the instructions on the site;
[*]prefer a file ending in .deb over any other;
[*]if the version you want is a “tarball”, or mentions that “compiling” is necessary, please consider using something else, as such things are not for newbies;
[*]if you come to the forums for help with something you have downloaded from a website, please don't be stingy with the info; give us the URL that you got the thing from;
[*]Windows software is obviously not compatible with Ubuntu (if you really want to try to force it to work, then use Wine, and post any questions in the [Wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313")) and you should just use Ubuntu software instead (i.e. Firefox, not Internet Explorer).
[/LIST]

[SIZE="5"]Program not working[/SIZE]

If a program crashes or just doesn't start when you click on it, the first thing we are going to ask you to do is to run the program in a terminal instead of from the menus.

This means that, for example, instead of clicking on “*Firefox*” in the menus, you would click on “*Terminal*”, and then in that terminal type “*firefox*”.  That way, error messages will be dumped to the terminal, and you can copy and paste them on to the forum for us to see.  You might as well save time by doing this before you ask the question.

When pasting stuff like that, do remember to use the **#** button on the formatting bar.  This will insert [noparse]```
...
```[/noparse] tags around the info, to make it easier for us to read.

[SIZE="5"]Permissions[/SIZE]

If you can't do something to some file on your computer without the system complaining about “permissions”, then it's probably because you don't “own” the file.  You probably need to start the application in question as root.  For example, you'd go to the terminal and type “*gksu* gedit” or “*gksu* nautilus” or whatever, to open up the program you're using.  That program with then have no permission problems.  Don't over-use this.

---

### Post by Gannon8 on 2008-09-18
Rename thread to FAQ and we can add to it :popcorn: (I am eating some right now :) )

---

### Post by overdrank on 2008-09-18
Good info :) and take a look at the sticky's at the top of the forum page :KS

---

