---
title: "My Ubuntu Challenge, Tweak it!! But how?"
date: 2007-11-01
forum: Programming Talk
---

### Post by mohamad on 2007-11-01
Hi there,


The idea that Linux is open source, and that I can change EVERYTHING I want (i assume this is true, tell me if otherwise) excites me. But I don't really know how to do this. Let me explain. There are some issues I don't like about Ubuntu and gnome in particular. Now my goal is to change what I don't like to see if Linux is really that changeable/flexible.
I will list my problems and my ideas to solve them, but regarding every plan I have a question that u may want to answer. Or maybe u have a better idea, suits even better!
Here we go.



**1) Undo/Redo program**
When I delete/move/copy/rename in the gnome environment, the key combination ctrl+z, that supposed to undo the last performed action, as in Windows, does not work. Now I want to write a program (I know Java and bash), that listens to ctrl+z and when it is pressed, it will need to know the last performed action done. So my first question here is, is there a file or list somewhere that logs all the performed actions in the entire gnome like delete/move/copy/rename?



**2) Hide a Process**
I want Firefox to always be loaded in my memory due to a great speed to open a new Firefox window. I found the best performance result by just always letting a Firefox window open on my fourth workspace (where I don't see it). Now I want to hide this window, so I need a command that will hide a process from the display, but keep it running on the background. This must be possible as I now use Alltray to do the trick, by using "alltray --notray firefox". But I want to know the mechanics of this to
implement it in my own Java program. So the question is, is there a bash command that will hide a process by for example its process id from the display?



**3) Alias for Alt+F2**
I want to make a nautilus script that will lets say make an alias name of a file, so I can access it with Alt+F2 Run dialog. Now I know some of u will advise me to use Gnome launch box or Gnome-Do, but I want to use the original gnome run dialog since the others didn't really worked for me. I can edit the .bashrc file and add aliases there but that will not work for Alt+F2, only in the terminal. So, how can I make aliases somewhere that will work for the gnome run dialog, and now we are talking about it, can I add a bin folder that will be monitored by this run dialog so I can put my scripts there? (I really want the possibility to add multiple folders)



**4) Record commands of background actions **
I want to make a script that changes the folders icon into another, that is downloaded from the net. For instance from IMDB, so the folder icon becomes the cover of a movie. I surfed the net hours for this and didn't really find a way to do it in Gnome, I did however find a way for KDE. So this brings me to the most important question that will answer also all my future questions. When I make an action in gnome with my mouse and keyboard, everything, will it be done with commands in the background that I can record? For instance, when I make a new folder with a right mouse click, there must be a place where the command "mkdir ..." is being invoked, now my question is, can I monitor those actions? This way, everything I want to automate in gnome, I just do it first, record the commands and put it in a script, or is this just complete rubbish and no such thing is possible?



**5) Tweak in general, change want I want**
There are some things I want to disable in Gnome, like the never stopping message that I am in my nautilus script folder, like nautilus now and then makes a nautilus-debug-log.txt in my home dir, that the print icon doesn't hide automatically when the print is done and more. I can right click on the print icon and click "Hide", but can I not do this by command somehow? So I want to learn how to tweak Linux for such things. Where to look? How to start? Is er a good book that u may recommend me for this to learn how these things are done in Linux? Something I would really like to tweak is the gnome context menu, when I right click, I can choose to make a new folder, and under "New Document" I can make an empty file, now I want this "empty file" to be right under "make new folder" for faster access, since its the only one I use under "new document". This is just an example, but what I mean is that I want to know how these things are done, where the context menu is defined and if I can change these things easily. Where is THE place to look/be for tweaking Linux/gnome?


Thanks in regards,

---

### Post by LaRoza on 2007-11-01
> **mohamad said:**
> Hi there,
I will list my problems and my ideas to solve them, but regarding every plan I have a question that u may want to answer. Or maybe u have a better idea, suits even better!
Here we go.

**1) Undo/Redo program**

Where is THE place to look/be for tweaking Linux/gnome?

Thanks in regards,

0. You can't "undo" a delete/move/rename with Ctrl + Z. You can't do that in Windows either. You can recover files for the Trash if you want.

It looks like you shouldn't be using GNOME. It also sounds like you want GNOME to be reprogrammed, so try that. Get the source, and tweak it to your specs.

Getting the source would be the best way to tweak anything.

---

### Post by LaRoza on 2007-11-01
> **mohamad said:**
> Hi there,
There are some issues I don't like about Ubuntu and gnome in particular. Now my goal is to change what I don't like to see if Linux is really that changeable/flexible.


You might want to find existing programs before trying to completely alter an existing one.

Look into KDE, XFCE, Fluxbox, Window Maker, e17, and all the others.

---

### Post by CptPicard on 2007-11-01
Awww, don't be so harsh LaRoza. The guy is obviously just the typical noob who feels like recoding Gnome's VFS (or whatever it might require, I use KDE) is a one afternoon job for a (beginning?) Java(!) programmer... his ideas are not nearly as wild as those of he-we-do-not-speak-of. :)

Anyway mohamed, you're asking much... it's doable but would be a lot of work... wish you luck in your endeavours, and use the source, Luke...

EDIT: and even if there were such an event channel to eavesdrop on, your implementation strategies sound really fragile and especially the aliasing bit like a security hole waiting to happen. KDE has Katapult btw, it does what you're probably after. And the DCOP interface is quite scriptable too, let's you do at least similar things you seem to be interested in.

---

### Post by LaRoza on 2007-11-01
> **CptPicard said:**
> his ideas are not nearly as wild as those of he-we-do-not-speak-of. :)



You're right. Post amended.

---

### Post by Wybiral on 2007-11-01
> **CptPicard said:**
> his ideas are not nearly as wild as those of he-we-do-not-speak-of. :)

lol

---

### Post by mohamad on 2007-11-01
Hi Laroza,

I just want to know a few things. For example I wanted to know if gnome logs all file editing, like moving etc. I think its a reasonable question. Of course I can put it like this:

**Does gnome keep a log somewhere when u copy/paste/move or delete a file?**

But then I thought it would be better to explain why I want to know that.

The same goes for:

**Is there a bash command that can hide a process from the display?**
 
and so on for the other 3 things, but I only want to make my question more clear to  put it in the real context, why I really want to know it.

And in Windows XP u can actually undo all the actions delete/move/rename and copy. Try for yourself, ctrl+z will do the trick.

And finally, I don't see it as a double post because the other post almost a year ago helped me to the point that I can use alltray, like I sad. Thats why I wanted to know if there is a bash command, because that will be much faster than using alltray I think.

---

### Post by mohamad on 2007-11-01
> **CptPicard said:**
> Awww, don't be so harsh LaRoza. The guy is obviously just the typical noob who feels like recoding Gnome's VFS (or whatever it might require, I use KDE) is a one afternoon job for a (beginning?) Java(!) programmer... his ideas are not nearly as wild as those of he-we-do-not-speak-of. :)

Anyway mohamed, you're asking much... it's doable but would be a lot of work... wish you luck in your endeavours, and use the source, Luke...

EDIT: and even if there were such an event channel to eavesdrop on, your implementation strategies sound really fragile and especially the aliasing bit like a security hole waiting to happen. KDE has Katapult btw, it does what you're probably after. And the DCOP interface is quite scriptable too, let's you do at least similar things you seem to be interested in.


Allright, thanks, I will drop the alias thing and have a look at katapult. By the way, I am beginning to be curious about the he-we-do-not-speak-of. :)

---

### Post by CptPicard on 2007-11-01
> **Wybiral said:**
> lol

Well, calling out the loons by name gains you infraction points around here, so... just ask pmasiar :p

---

### Post by ssam on 2007-11-01
you get the source to any package using
```

apt-get source package-name

```
you will also need the build dependancies
```

sudo apt-get build-dep package-name

```
and some build tools
```

sudo apt-get install build-essential devscripts fakeroot

```
then you can make changes and build the package using
```

dpkg-buildpackage -rfakeroot

```
from within the package folder. that will make .deb files that you can install with
```

sudo dpkg -i package.deb

```

---

### Post by Wybiral on 2007-11-01
> **CptPicard said:**
> Well, calling out the loons by name gains you infraction points around here, so... just ask pmasiar :p

[-X

It's against the code of conduct to use any other members name anywhere on these forums, whether it be in a positive or negative light. For example, I'm not allowed to say "CptPicard is an awesome programmer, I would take his advice".

... I'll probably get an infraction for that, and you for mentioning pmasiar :) And maybe just for insinuating that other guy (the one with the awesome ideas).

BTW mohamad, not that I doubt your intentions, but access like this (reading keys and hiding processes) may be discouraged simply because they would allow people to easily write key-loggers / spyware. In fact, I would consider it a good thing if your system didn't allow it.

---

### Post by Ramses de Norre on 2007-11-01
**2) Hide a Process**
I think things like readahead and prelink might interest you, and if you really want you can replace the firefox binary with a script that determines whether it is the first firefox instance, and if so it can use window manager options to move it to the 4th workplace or something (assuming you've got a window manager with such capabilities)



**3) Alias for Alt+F2**
I'm not sure what you're after, just a global keybinding? That depends on your WM than, I'm not sure what exactely gnome supports but it has a keybinding dialog, I think.



**4) Record commands of background actions **
Not everything is done by commands, most programs that e.g. make new directories just call an intern instruction to do so (in java you make a new File and set it as a directory, c has the same capabilities). It'll be pretty hard to monitor that, but I think the fam daemon does something alike.



**5) Tweak in general, change want I want**
Most of gnome is written in c, if you want to change stuff you'll need to change the source, recompile it and build a new package. Beware though, gnome is a _huge_ application, it'll take you quite a while to get to know the source.


Although it is true that you can change whatever you want in open source applications, it certainly isn't easy, not to say that it is darn hard in most cases. Most programs have become what they are by years of development and bug fixing. If you really want to make a difference and code your own stuff, you'll need to get very proficient in programming and, for gnome, in c.

---

### Post by CptPicard on 2007-11-01
> **mohamad said:**
>  By the way, I am beginning to be curious about the he-we-do-not-speak-of. :)

Well if you insist... [Clicky]("http://ubuntuforums.org/search.php?do=finduser&u=356998"), at your own risk. Be warned, you will be exposed to one of the greatest visionary minds ever to grace the forum. :)

I wonder how that Novell purchase and "Stacks" application are coming along. :-k

---

### Post by LaRoza on 2007-11-01
> **mohamad said:**
> Hi Laroza,

I just want to know a few things. For example I wanted to know if gnome logs all file editing, like moving etc. I think its a reasonable question. Of course I can put it like this:

**Does gnome keep a log somewhere when u copy/paste/move or delete a file?**

But then I thought it would be better to explain why I want to know that.

The same goes for:

**Is there a bash command that can hide a process from the display?**
 
and so on for the other 3 things, but I only want to make my question more clear to  put it in the real context, why I really want to know it.

And in Windows XP u can actually undo all the actions delete/move/rename and copy. Try for yourself, ctrl+z will do the trick.

And finally, I don't see it as a double post because the other post almost a year ago helped me to the point that I can use alltray, like I sad. Thats why I wanted to know if there is a bash command, because that will be much faster than using alltray I think.

That is impossible, because not all such actions take place through GNOME. It is based on the file system, and it is a a journalling file system, if you are using EXT3.

I wouldn't want to be able to hide a process. If you find Firefox slow, use Opera (donning famesuit).

Really? I haven't used Windows XP in a while, and when I do, it is Vista. I don't want to talk about it, it is too painfull.

I didn't notice the date, and with your low number of total posts, it seemed like a recent post.

As to my reference to another member, you are better of not knowing, although it was funny in a sad sort of way. I realize you probably clicked that link by now, my condolences.

I hope to see you around on the forum, and the possible discussions later.

---

### Post by slavik on 2007-11-01
Don't forget that any file opening/creations/etc is a system call to the kernel. I am sure the kernel has hooks to monitor such things. :)

As for monitoring when you rename files, it should be pretty easy to get nautilus to write out the log of what it is doing (by tracking the GUI callback functions and changing them).

---

### Post by mohamad on 2007-11-02
> 
Don't forget that any file opening/creations/etc is a system call to the kernel. I am sure the kernel has hooks to monitor such things

Exactly, that was what I was thinking since I remembered this from college, that these actions are always a system call from within every program to the kernel (indirect). But if it is not logged by default, as I come to believe now after reading some previous threads, then I'll just put that idea out of my mind.

---

### Post by mohamad on 2007-11-02
> That is impossible, because not all such actions take place through GNOME. It is based on the file system, and it is a a journalling file system, if you are using EXT3.


Allright, I decided to leave that idea for what it is right now and I'm not itending to try it anymore.

> 
I wouldn't want to be able to hide a process. If you find Firefox slow, use Opera (donning famesuit).

But it is not really hiding the process, which you may seem dangerous. Thats not what I mean.  It's not like when I use "ps -A | grep firefox" that I dont see any process running while it is actually running (so really hiding it), I just wanted to run it in the background. Only preventing it to show itself on the desktop but in my process list, ofcourse it should be there. I dont know if this is what u find dangerous to the system, if it is, then let it rest and I'll be using alltray for know.


> As to my reference to another member, you are better of not knowing, although it was funny in a sad sort of way. I realize you probably clicked that link by now, my condolences.

I damn sure clicked that link, but it didnt took long to know what you all meant. It did surprise me however that a lot of people just kept replying and replying, maybe the power of ubuntu :D

---

### Post by CptPicard on 2007-11-02
> **mohamad said:**
> Only preventing it to show itself on the desktop but in my process list, ofcourse it should be there. I dont know if this is what u find dangerous to the system, if it is, then let it rest and I'll be using alltray for know.

Mind you, Firefox fills up your RAM anyway if you leave it running for days on end... I find myself killing the process off on a regular basis because of this.

> It did surprise me however that a lot of people just kept replying and replying, maybe the power of ubuntu :D

It's a bit like you can't help staring at a car wreck, you know? And there *was* a definite entertainment value to it... ;)

---

### Post by mohamad on 2007-11-02
> **Ramses de Norre said:**
> **2) Hide a Process**
I think things like readahead and prelink might interest you, and if you really want you can replace the firefox binary with a script that determines whether it is the first firefox instance, and if so it can use window manager options to move it to the 4th workplace or something (assuming you've got a window manager with such capabilities)


I got prelink, dont know readahead but I dont know if it can run with prelink all together. I look it up thanks.
Yes that is what I am doing right know, changed /usr/bin/firefox that will check for an allready running instance and if not, open it with "alltray firefox" But then I get a firefox tray icon so I use "alltray --notray firefox". I disabled session restore because ending firefox will like this always be a kill (thats the reason I want something different).


> 
**3) Alias for Alt+F2**
I'm not sure what you're after, just a global keybinding? That depends on your WM than, I'm not sure what exactely gnome supports but it has a keybinding dialog, I think.


If I have a text file in say /home/username/docs/test. I can put the location in ~/.bashrc as an alias (using a nautilus script) like this:

```
alias open_test='gedit ~/docs/test'
```

So when I open a terminal window and type "open_test", then the text file would open. But in a run dialog, Alt+F2, it wont work. So my question was, is there a file (like ~/.bashrc for the terminal) that I can put aliases in, but the aliases would also work fot the run dialog, when pressed Alt+F2 (in my case).




> 
**4) Record commands of background actions **
Not everything is done by commands, most programs that e.g. make new directories just call an intern instruction to do so (in java you make a new File and set it as a directory, c has the same capabilities). It'll be pretty hard to monitor that, but I think the fam daemon does something alike.


I'll look at fam thanks, but I think I will rest this case for now and just hope gnome developers implement this feature someday, I'm really used to it and used it constantly in windows, but then it is my way of using the PC, always deleting and moving and then undeleting and removing etc, maybe I should try to change that first :P

> 
**5) Tweak in general, change want I want**
Most of gnome is written in c, if you want to change stuff you'll need to change the source, recompile it and build a new package. Beware though, gnome is a _huge_ application, it'll take you quite a while to get to know the source.


Although it is true that you can change whatever you want in open source applications, it certainly isn't easy, not to say that it is darn hard in most cases. Most programs have become what they are by years of development and bug fixing. If you really want to make a difference and code your own stuff, you'll need to get very proficient in programming and, for gnome, in c.

Indeed and I never intended to change the gnome source, I was only wondering if there is like a mega gnome config file that I can change like with gconf-editor, but then for everything. If there isnt such a thing, and something tells me there isnt, then no way changing the gnome source code is not what I want.

---

### Post by Tomosaur on 2007-11-02
If you want the undo features and all that kind of thing - you might want to check out KDE, which supports it.

It is definitely possible, it's just that te Gnome devs try to keep feature creep to a minimum. Perhaps if you implemented it in an elegant way, it could get merged into the main development trunk, but I wouldn't count on it. They're pretty conservative when it comes to adding new stuff.

---

### Post by pmasiar on 2007-11-02
> **CptPicard said:**
> Mind you, Firefox fills up your RAM anyway if you leave it running for days on end... I find myself killing the process off on a regular basis because of this.

FF fills memory with cached page history, with tabs etc it eats memory like there is no tomorrow. They have setting to disable that "misfeature", but with the SessionManager plugin, you can just save session and restart FF. It is a waste of CPU cycles but simpler than learning how to do it the right way. :-)

When reading about it, I learned new word: "pessimization" is an optimization gone wrong :-)

to OP: My first impression from your ideas was just a uninhibited visionary like he-who-cannot-be-named, but looks like you realize you are into months and possibly years of learning and reading the code to be able to implement all your ideas.

With software, everything is possible, it "just a matter of simple programming" :-)  Possibly man-years of it, of course, and as as mentioned before, some features might be bad idea - but nobody can prevent you to learn Gnome/KDE guts and implement it on your system, even it it will not be included upstream. If you don't have time now, you can always do it when you retire :-)

---

