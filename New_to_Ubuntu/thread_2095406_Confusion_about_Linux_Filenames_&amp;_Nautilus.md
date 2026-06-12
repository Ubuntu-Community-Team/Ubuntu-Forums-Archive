---
title: "Confusion about Linux Filenames &amp; Nautilus"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by Iggy64 on 2012-12-16
I am fairly new to Linux, and have been experimenting with various desktop environments on top of Ubuntu, to see what DE feels most comfortable.  Most recently, I have tried Peppermint OS and Bodhi Linux.  While I like both of these environments, I find their file managers to be unsatisfactory.  I therefore installed Nautilus on each one.  In so doing, I learned that Nautilus brings along its own desktop environment, which causes problems for whatever other windowing system happens to be running.    I therefore looked for a way to run Nautilus without its desktop.  The cure was to use:  sudo nautilus --no-desktop.

When I looked for a way to do this through the menu, I discovered more interesting things.  When I use I file manager to look for the Nautilus launcher, I find two files with the same name!
/usr/share/applications/file
/usr/share/applications/file.
They are slightly different sizes.

When I open gedit (or leafpad) to edit them, they show up with different names:
/usr/share/applications/nautilus.desktop
/usr/share/applications/nautilus-home.desktop

In terminal, as root, I launched gedit and opened usr/shared/applications/nautilus.desktop.  I modified one line, changing nautilus %U to nautilus --no-desktop.  That seems to have solved the desktop clash problem.

Here are my noob questions:

How can the file system contain two files with the same name in the same directory?

Why do these files have different names when I look at them with a text editor, as opposed to when I look at them with a file manager?

What is the difference between nautilus.desktop and nautilus-home.desktop?

Which of these two needs to be modified (with --no-desktop) to prevent Nautilus from taking over the desktop?

I am trying to get the hang of Linux, but some of these things have been difficult for me to search out in the forums.

---

### Post by Morbius1 on 2012-12-16
>  How can the file system contain two files with the same name in the same directory?they aren't the same name as you found out. It only appears that way in Nautilus. Had you used a real file manager like XFE it would show both files with their full names including the file extension.
>  Why do these files have different names when I look at them with a text  editor, as opposed to when I look at them with a file manager?Not all file managers only ones like Nautilus. I read some where that it's becasue Nautilus "implements the XDG file specification". I have no idea what that means but I like to use file managers that show me what's actually there.

I have moved on to XFCE as my desktop environment and don't use Nautilus any longer but I suspect that you have to use the --no-desktop option on every occurrence in /usr/share/applications. XFCE's file manager - Thunar - is also afflicted with this malady of not showing the real name of things which is why I always install the XFE file manager for when I need to do important things.

---

### Post by Morbius1 on 2012-12-16
.

---

### Post by Iggy64 on 2012-12-16
Thanks, Morbius1, for the new perspective.

I had no idea that Nautilus was not a "real" file manager.  I seem to have tried them all over the last few months, and Nautilus seemed the only one that let me do all the things I like to do frequently:  

- See a tree view in left pane
-  Drag and drop files
- Search for files by name or by extension
- Safely remove USB drives

Most of the other FMs I tried do only maybe two of these things, so that I have to use a handful of tools instead of just one.

HOWEVER, if Nautilus is not going to show me the real names of files, it hardly seems worth using.  Not to mention all the trouble with it taking over the desktop.  Dolphin and Konqueror are close to providing what I need, but they bring along so much KDE baggage, they seem not worth it.  Thunar and PCMan seemed a bit lacking in features.

 So NOW what the heck do I do?  I will definitely take a look at XFE, as you mentioned.  I'm used to viewing, finding, and moving lots of files in Windows, including onto and off USB devices.  Perhaps XFE is the tool I need for Linux.  I will check it out.

Thanks!

---

### Post by jerome1232 on 2012-12-16
Here's a bit of discussion on this very topic.

[http://askubuntu.com/questions/17220/can-nautilus-display-a-desktop-file-by-its-real-name](http://askubuntu.com/questions/17220/can-nautilus-display-a-desktop-file-by-its-real-name)

---

### Post by Iggy64 on 2012-12-16
Thanks for that link.  I have to say, this sort of business makes Linux (well, maybe just Nautilus) rather uncomfortable to deal with.  I'm so used to a path/filename being an absolute identifier.  Now there are aliases.  Yikes.

I wonder how much this business goes on in Linux in general.

I still hope to find a file manager that does the things I listed in my OP, but if I can't, I may go with one that is close, then use Catfish or something similar for searches.  Seems a shame to have to run a second app for that, though.

---

### Post by jerome1232 on 2012-12-16
without getting into any debate this is just a special case scenario with .desktop files.

---

### Post by Iggy64 on 2012-12-17
Well, that's a good thing to know.  I'll have to do more exploring, to see if this happens with ALL desktop files, or just certain ones.

Much obliged for your help!

---

### Post by JKyleOKC on 2012-12-17
One thing you need to know as you become more familiar with this different file system: In all Linux distributions, not just *buntu, the "absolute path" isn't really a unique identifier for a file. The truly unique identifier is something called its "inode" which is a number that identifies the file's location in the filesystem, and an inode can have any number of different absolute paths leading to it! In everyday use all this is hidden behind the scenes, but you'll see references to "hard links" and "soft links" that deal with it. A soft or symbolic link is pretty much like a Windows shortcut; a hard link creates a different absolute path to the inode of its target. Deleting a soft link deletes its target; deleting a hard link simply removes the path it defines, but the target is still accessible unless this was the last link to its inode.

Very confusing, initially, but with familiarity it will make sense.

Another less-confusing major difference is that Linux does not use the file extension to identify the type of file; it uses identifying signatures at the start of each file, instead. The file extension may be used by individual applications, however.

The main thing to keep in mind is that this o/s is a very different beast from the one you already know, and many details are going to be quite different. Welcome to the fun!

---

### Post by Iggy64 on 2012-12-18
JKyleOKC --

Hey, that is some great information!  It explains a lot of my confusion.  Although I have read a few Linux "primers," I somehow failed to learn these fundamental differences from Windows.  Now that you have given me a few starter concepts and buzzwords, I can start digging into more of the basics.

For me, eventual total migration to Linux seems inevitable.  And I'm the sort that likes to understand as much of the big picture as I can, so I don't underutilize the operating system and so I don't get myself into trouble.

It was very kind of you to make time to steer me in the right direction.

Much obliged.

---

### Post by JKyleOKC on 2012-12-18
You're quite welcome! Ever since I first started messing with computers almost 50 years ago, I've been helped by hundreds of people I never met face to face. Along the way, I told one of them I had no idea how to repay his kindness. The reply took root with me: "Forget paying back. Pay forward by helping others whenever you get the chance." Ever since, I've tried to follow that advice.

Incidentally, those ".desktop" files that triggered your initial questions in this thread are the only exception of which I'm aware to the "Linux does not use the file extension" rule I mentioned. These files get special treatment by all file manager programs that comply with the specs set out by the Open Desktop group, and display the string following their "Name=" line, rather than the real filename. Since many different files can have the same "Name=" line in them, you get the confusing display in the file manager!

---

### Post by Iggy64 on 2012-12-18
I'm very pleased to be one of the recipients of your "pay forward" philosophy.  I hope that I will learn enough to be able to adopt that same policy.  That's a great story, and it makes me feel good to see folks helping one another like you do.

And that tip about the .desktop files is a huge help.  It clears a most of the confusion that prompted my original post.  

Now, I'm grateful for that confusion, because it led me to your little tutorial, which in turn gives me much more perspective on how Linux works.

Again, much obliged.

---

