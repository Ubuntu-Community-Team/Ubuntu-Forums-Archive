---
title: "How do I install Dreamweaver in Ubuntu?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by sprdave on 2008-07-17
I cannot install ANY software!! I am new.. only had Ubuntu for a week... I am just trying to experiment now... to learn my way around on it. I have all these "Orange Dots" with X's in them.

I think I installed Wine correct... but I cannot seem to figure out how to install software. All of my .exe files have an orange circle with an X.

Please help. 

Thanks,

Dave

---

### Post by aktiwers on 2008-07-18
You are aware that .exe files are made for Windows right?

This means that what you are trying to do, is pretty much the same as trying to play a Nintendo game in a Playstation. It wont work.

But off cause we have Wine, and it does work for lots of Windows apps anyways, but you should always try to find a native version or a native alternative to this application you want.
You could look here for native alternatives:
[http://www.osalt.com/](http://www.osalt.com/)

If you go to System => Administration => Synaptics Package Manager
There is a huge database with all kinds of apps you can install. Just "mark for install" and hit apply and it will download and install the software for you.

If you think this one is a little confusing there is a simpler one in Applications => Add/remove 

Now what software are you trying to install? :)

Welcome by the way

---

### Post by MobiusNZ on 2008-07-18
In linux we don't use exe files. Programs are marked in their properties as being executable or not.

I think you might be going the wrong way about installing programs... you don't generally run Windows apps on your linux box.

Use the Add/Remove Programs tool from the menu. There you have access to over 30000 programs that you can easily install.

---

### Post by RomeReactor on 2008-07-18
Hi. That means those files are marked as 'Unreadable' for your account. You need to change their permissions by making a folder (preferably in your home folder), moving all of the EXE files to it, then open a terminal (Applications->Accessories->Terminal) and changing directory to that folder:
```
cd NAME_OF_FOLDER
```
Then:
```
sudo chmod 777 ./*
```

You should be able to open them with Wine now.

---

### Post by maddog39 on 2008-07-18
> **RomeReactor said:**
> Hi. That means those files are marked as 'Unreadable' for your account. You need to change their permissions by making a folder (preferably in your home folder), moving all of the EXE files to it, then open a terminal (Applications->Accessories->Terminal) and changing directory to that folder:
```
cd NAME_OF_FOLDER
```Then:
```
sudo chmod 777 ./*
```You should be able to open them with Wine now.
If you would like to do that same thing but without the command line, then just Right Click > Properties > Permissions on the file(s) and on every drop down, select "Read and Write"

---

### Post by sprdave on 2008-07-18
Okay... Now I am really confused... I thought "WINE" was the program to "convert" so to speak... Windows programs to run in Linux.

I just want to simply install "Dreamweaver8 from the CD-Drive"

My main problem is "Access Denied" for everything I want to do on my system.

I will try the things mentioned here and see if I have any luck..
Thanks, Dave

---

### Post by RomeReactor on 2008-07-18
Wine doesn't convert windows programs to Linux; it provides a compatibility layer so they can run as if they were in windows, though with varying degrees of success.

EDIT: It looks like Dreamweaver 8 does [run very well]("http://appdb.winehq.org/appview.php?iVersionId=3482"). As aktiwers and MobiusNZ point out, you should try to find a native (Linux) alternative to the windows programs you want to install.

---

### Post by SunnyRabbiera on 2008-07-18
Wine is tricky, it will not always work 100% of the time.
Try different things out though, for newcomers you may want to try out crossover office, its not free but does a good job at what it does.

---

### Post by sprdave on 2008-07-18
Sorry  I still do not understand you directions above..

I created a folder called programs

Went to terminal typed in cd programs

No such file or directory

---

### Post by SunnyRabbiera on 2008-07-18
Well then dont worry about it, usually commands like that can be tetchy...
what version of wine do you have on your system if any?

---

### Post by RomeReactor on 2008-07-18
Try doing it as maddog39 said, from the file browser; if you can't modify the permissions, then try the terminal.

When using the terminal, make sure you spell the names correctly, as the terminal is case-sensitive. Where did you make the folder?

---

### Post by aysiu on 2008-07-18
As others have stated, the ideal solution is to look for a *Linux native* program:
[http://www.osalt.com/dreamweaver](http://www.osalt.com/dreamweaver)

Learn here how to install *Linux native* programs:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you still want to go through the tedious process of setting up Dreamweaver (a *Windows native* program) through Wine, this may help you:
[http://maketecheasier.com/how-to-install-dreamweaver-cs3-in-ubuntu-hardy/2008/06/20](http://maketecheasier.com/how-to-install-dreamweaver-cs3-in-ubuntu-hardy/2008/06/20)

---

### Post by sprdave on 2008-07-18
Tell You what I am going to READ cover to cover the following books I have access to then come back here...

Linux Bible
A Practical Guide to Ubuntu Linux®
The Official Ubuntu Book, Third Edition
Ubuntu Unleashed 2008 Edition: Covering 8.04 and 8.10, Fourth Edition

I am not getting anywhere by just hacking away. I am not a stupid person... I have my MCSE, A+, and Network+. Plus five years of Web Development with SharePoint, ASP,NET and C#.
I just have never seen Linux until this week...

BTW  I have version 1.0 of WINE

---

### Post by aysiu on 2008-07-18
Read the three links I posted instead.

It'll take less time.

And it'll actually solve your problem.

I doubt any of those books will help you install Dreamweaver using Wine.

---

### Post by SunnyRabbiera on 2008-07-18
Well sometimes hacking away can be helpful though in learning.
Now as for dreamweaver8 there is a handy application called wine doors you can try for that, you can find it here:
[http://www.getdeb.net/](http://www.getdeb.net/)
search for wine

---

### Post by sprdave on 2008-07-18
Okay... Thanks everyone for the advice tonight...  I still have not figured out the permission issue on my new Ubuntu setup. I cannot even access the file(s) with orange dots to figure out how to change the permissions on them.

Seem like they all are owned by root. Last night I opened Nautilus and added some sub-folders to /var/www so I could run some examples from a .PHP book.

But my system seems plauged with orange dots and "Access Denied" "you are not the owner"  blah blah..

---

### Post by SunnyRabbiera on 2008-07-18
if the files are owned by root try sudo in a command line terminal...

---

### Post by sprdave on 2008-07-18
Okay will do..

---

### Post by SunnyRabbiera on 2008-07-18
just keep trying, dont give up...
I am sure the answer to your issue might pop up.

---

### Post by sprdave on 2008-07-18
Thanks!  I do not give up on things... but it seems like it is a lot harder for me to learn things than others... I just do not know where to start... There are billions of Websites and articles for Linux and Ubuntu.. 

I feel like there is no beginning or ending.. I like step one, step two.. approach to things.. 

How can I build on each step when I do not know what to do for my first??  *LOL*

---

### Post by SunnyRabbiera on 2008-07-18
Well lucky for you ubuntu is one of the easiest distributions of linux to use, the initial hurdles can be a pain but once you get past them they will become second nature.
Now do you really really need dreamweaver if it doesn't work?
there are a few alternatives to it in linux like kompozer for starters.

---

### Post by gandaran on 2008-07-18
> **sprdave said:**
> Okay... Thanks everyone for the advice tonight...  I still have not figured out the permission issue on my new Ubuntu setup. I cannot even access the file(s) with orange dots to figure out how to change the permissions on them.

Seem like they all are owned by root. Last night I opened Nautilus and added some sub-folders to /var/www so I could run some examples from a .PHP book.

But my system seems plauged with orange dots and "Access Denied" "you are not the owner"  blah blah..

do you have more than one user account?
the blocked files could also be due to the way you burn the cd, maybe one of those folders or the cd as a user-name.
I have had problems with pen drives, where the owner just changed the drive name to say 'john' all the files where blocked.

try downloading dreamweaver 8 here [http://w13.easy-share.com/1191762.html](http://w13.easy-share.com/1191762.html) just enter the code and click the download tab.

dreanweaver 8 works fine in wine, I believe its the only version that does work.

---

### Post by aysiu on 2008-07-18
This may help you out:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aktiwers on 2008-07-18
Try out Wine-Doors
[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

It will download and install some Windows apps for you and configure them with wine so they work, including Dreamweaver. I am not sure what version though.

---

### Post by nikgare on 2008-07-18
<snip>
Sorry, posted to wrong thread

---

