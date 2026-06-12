---
title: "It must be possible !"
date: 2012-09-02
forum: New to Ubuntu
---

### Post by pragmatic on 2012-09-02
Ok here is the problem ... I want to use movie player as a helper application on 12.04 but it's not in the list that is offered to me.  oddly enough brasero is!  How do I enable the helper application list to include other installed applications eg like the long list you get with windozy.  There is of course the "other" option proffered by the Ubuntu Gui but  following that just leads to being asked to open something in the file structure. My ideal preference would be a solution that allows me to choose myself what to use...  as it stands I don't have one !

I'm trying to access AV files from the net  it's at that point I get asked how I would like them dealt with.  simple really movie player !  lets hope someone out there has a simple answer ! Thanks.

---

### Post by MG&amp;TL on 2012-09-02
> **pragmatic said:**
> Ok here is the problem ... I want to use movie player as a helper application on 12.04 but it's not in the list that is offered to me.  oddly enough brasero is!  How do I enable the helper application list to include other installed applications eg like the long list you get with windozy.  There is of course the "other" option proffered by the Ubuntu Gui but  following that just leads to being asked to open something in the file structure. My ideal preference would be a solution that allows me to choose myself what to use...  as it stands I don't have one !

I'm trying to access AV files from the net  it's at that point I get asked how I would like them dealt with.  simple really movie player !  lets hope someone out there has a simple answer ! Thanks.

To avoid "the long list you get with windowzy", applications have to specifically say "we support these kinds of files" in a file somewhere. Totem (default movie player in ubuntu) for some reason hasn't. Feel free to file a bug if it's capable of playing these.

The 'other' option allows you to choose which application you want to use, specifically its location in the filesystem. :) Unfortunately, that's confusing for people new to a linux filesystem.  Unless much mistaken, you'll want to navigate to:

1. "Filesystem". Your Ubuntu filesystem, it'll be at the side somewhere normally.

2. Choose the "usr" folder from that.

3. Choose the "bin" folder from that.

4. Finally, choose the "totem" executable from that folder. You might want to type "t" to get to the t's in that folder, as Ubuntu has a **lot** of executables.

Hope that helps a bit. :)

---

### Post by pragmatic on 2012-09-02
Well I tried having a look in the file system at usr/bin  but what is the file in that directory that fires Movie Player up ?

I have it now thanks !

---

### Post by MG&amp;TL on 2012-09-02
> **MG&TL said:**
> 
4. Finally, choose the "totem" executable from that folder. You might want to type "t" to get to the t's in that folder, as Ubuntu has a **lot** of executables.


> **pragmatic said:**
> Well I tried having a look in the file system at usr/bin  but what is the file in that directory that fires Movie Player up ?

You want the "totem" file. :)

EDIT: Awesome, hope that helped. Remember to mark thread "solved"!

---

### Post by pragmatic on 2012-09-02
And another question arises out of the solution !  there is no option to make the above selection the default action as the option is grayed out    I can now open with Totem but I have to go select the ex file everytime .  this is just silly  how do we get a proper list into the options ?

I have a feeling that someone is going to suggest editing a text file dealing with mime types using the command line.

---

### Post by MG&amp;TL on 2012-09-02
> **pragmatic said:**
> And another question arises out of the solution !  there is no option to make the above selection the default action as the option is greyed out    I can now open with Totem but I have to go select the ex file everytime .  this is just silly  how do we get a proper list into the options ?

Odd. This really shouldn't happen, it worked great for me here last time I tried it. I confess I'm a bit stumped, the best I can suggest is that you report a bug: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) although I have no idea what package to put it against. (Don't be scared by the page, just use common sense and you'll be fine. Developers tend to bark, but not bite.)

---

### Post by pragmatic on 2012-09-02
I honestly think that users should have a long list of installed apps to choose from as it makes much more sense to anyone trying to use Ubuntu for Audio Visual purposes.  From my point of view the limiting of choice by default is daft and counter productive as it's making 12.04 about useless for me doing anything productive.  for example I may want to open a.pls file in a test editor or a music player but not brasero for sure.  I do realise that it's dangerous to give people choice when it comes to system settings on some occasions  but surely there has to be a way for the developers to make their user interface more user friendly !

---

### Post by MG&amp;TL on 2012-09-02
> **pragmatic said:**
> I honestly think that users should have a long list of installed apps to choose from as it makes much more sense to anyone trying to use Ubuntu for Audio Visual purposes.  From my point of view the limiting of choice by default is daft and counter productive as it's making 12.04 about useless for me doing anything productive.  for example I may want to open a.pls file in a test editor or a music player but not brasero for sure.  I do realise that it's dangerous to give people choice when it comes to system settings on some occasions  but surely there has to be a way for the developers to make their user interface more user friendly !

That's what bug reports are for. ;)

Seriously, developers don't read these forums (Well....okay, some do. But for the most part, they're too busy making amazing stuff!) , so the best way you can get your point across to them is by making a bug report. They **do** actually read those, and it will get assigned a priority depending on how important an external triager thinks it is. Hopefully it will then get fixed and put in the next release. Please consider doing that, it's one of the single best ways you can make Ubuntu better.

---

### Post by TheFu on 2012-09-02
> **pragmatic said:**
> I honestly think that users should have a long list of installed apps to choose from as it makes much more sense to anyone trying to use Ubuntu for Audio Visual purposes.  From my point of view the limiting of choice by default is daft and counter productive as it's making 12.04 about useless for me doing anything productive.  for example I may want to open a.pls file in a test editor or a music player but not brasero for sure.  I do realise that it's dangerous to give people choice when it comes to system settings on some occasions  but surely there has to be a way for the developers to make their user interface more user friendly !

Your view works for you, but not for everyone.  Too many choices is confusing to many users.  You may have found a bug too, I don't know.

If you'd like a long list of apps to choose, open a terminal and type this:
```
ls /usr/bin/
```
Enjoy, but I doubt that is really what you or any other user wants.

Yesterday I switched to VLC as the default app for all video file handling and it was trivial. Did it once and that was it. Totem is not the app for my needs - **sudo apt-get purge totem***

Linux is not Windows or OSX. It just isn't.  That doesn't mean that it is wrong, just that it is different.  To get the most out of linux, getting into the linux philosophy helps.  People that hang onto the philosophies from other OSes will always be frustrated by Linux.  

Linux requires a **thought shift** for the greater flexibility to be seen. Once that is discovered, **WOW,** you'll never go back to the other OSes. They are simply too limiting.  [http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) explains the differences a little better.

---

