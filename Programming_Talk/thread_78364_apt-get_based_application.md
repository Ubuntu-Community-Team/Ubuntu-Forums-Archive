---
title: "apt-get based application"
date: 2005-10-18
forum: Programming Talk
---

### Post by wolphin on 2005-10-18
Hi,

I was just thinking - how many people have complained because their Linux box isn't connected to the internet, and they can't download the packages off another machine because they'll end up with dependancy problems? Well, I don't have enough experience as a programmer to work on it myself, but I've had an idea.

Ok, basically, there are two apps which go hand-in-hand. 

1. A checker system, which can be compiled on any Debian-based distro with ease (this is the one which will be used on the offline box), and which will include any dependencies it itself might need;
2. The downloader tool, to be used on a box which has internet access (this app would have to be available for both Linux and Windows).

The first app is the one you should use primarily. As I said, it should be simple to compile (possibly put in a Python script to do it for them), and then all it does is discover what's on your system - what programs, libraries, versions of those, and any other things it might need to know. That app will save this information into a file (XML?), which you then put onto a flash drive/floppy disk/data transfer device.

The idea is that you install the second app on the machine which has internet access (can be either a Linux or Windows box), and you plug in your device. You start up the second app, point it to the file on the device, and then (in a similar way to apt-get) you type in the program/library you want to download. It will find out what versions of what libraries and programs you have (from the file), and then will go onto the repositories (which one should be able to change as easily as /etc/apt/sources.list) to download the program/library you specified. Should that program have dependencies, it will also download them (bearing in mind that it would exclude any dependencies which you already have, as long as it is >= version needed). All these files would be downloaded to a specified folder, and once it's done you can copy that folder to your data device, plug that device back into your offline Linux box, and then just use 'dpkg -i' to install the downloaded .deb files!

So, what do you all think? I know it's a long-shot, but it could be an interesting project for a couple of bored programmers to work on... Please let me know if you do decide to do so!

-Wolphin

---

### Post by andyluo on 2005-10-18
i think it's great, i propose implement the download manager in Java. Any things i can help, pls contact me. My Email & MSN:andyluo197@hotmail.com

---

### Post by wolphin on 2005-10-19
Andy - thank you for replying! At least someone agrees with my idea... ;)

I thought it might be a good idea to base the downloading app on apt-get (which I think is written in C, but cannot check up right now) so that less work would need to be done on the repository bit, but if you think it would be a better idea to do it in Java then I guess we'd have to discuss it with any others willing to take up this project. :) And thanks for the offer!

If anyone else would be interested in developing this app, could you please either leave a post here or send me an email? I would really appreciate it, and I know the Ubuntu/Debian community would too. :)

-Wolphin

---

### Post by UbuWu on 2005-10-19
You might want to have a look at apt-zip which is a very basic implementation of what you describe, but it works. It would be nice to have a more advanced/gui tool for this though.

---

### Post by wolphin on 2005-10-19
UbuWu - thank you for letting me know about Apt-Zip! As I'm within a network which doesn't allow downloads, I am not able to view the source code, but from your description it sounds pretty much like the sort of thing I'm talking about - I just don't think it has the same functionality. Yet, the point of the one I described is to be as simple as possible - so that even the newest of Linux users will be able to run it and access its features with ease.

I just hope that enough people will offer their abilities so that we can all get this app up and running. :D

-Wolphin ;)

---

### Post by David Marrs on 2005-10-19
I don't quite follow you. Why do they have dependancy problems if they're downloading Ubuntu debs? Surely the location of the repository makes no difference?

---

### Post by wolphin on 2005-10-19
By dependancy problems I mean that they would be missing dependancies which are needed. eg. Downloading Kate without the Qt libs and its other dependancies - it just wouldn't work without them.

As for the repos - the reason I said they should be able to change the repository list is in case they wanted to add the "Universe" repository, or if they wanted w32codecs they could temporarily add the '*deb ftp://ftp.nerim.net/debian-marillat/ etch main*' repository. That is why I mentioned that the repos list should be easily changeable. (Please let me know if I haven't understood you properly, because I don't really follow what you said either! :))

---

### Post by LordHunter317 on 2005-10-20
First apt-zip does what you describe already, and it would be better to extend that.  

Moreover, you haven't thought this through.  After I download the packages, what do I use to install them?  

[QUOTE=wolphin]
1. A checker system, which can be compiled on any Debian-based distro with ease (this is the one which will be used on the offline box), and which will include any dependencies it itself might need;[/quote]Not required.  You have everything you need to know in the dpkg status information, and you should be reliant on that.

---

### Post by wolphin on 2005-10-21
LordHunter - Thank you for your reply. I will take a look at apt-zip, but sadly cannot do so until later on today, so I'll have to get back to you on that. :)

> Moreover, you haven't thought this through. After I download the packages, what do I use to install them?I think something like 'apt-get install --dry-run xxxxx' might work, but again, I can't check that until later on today. If not, I guess it wouldn't be too hard to make a script which just 'sudo dpkg -i *.deb' everything. Correct? As I said - I'm only trying to put forward an idea. I haven't worked out all the little nooks and crannies yet.... ;)
> Not required. You have everything you need to know in the dpkg status information, and you should be reliant on that.Yes, I was also told this somewhere else, but thank you! IIRC, a 'more /var/lib/dpkg/status' will display the package list, but again, I'll have to check that up later.

So, is anyone interested in joining the project? I'm setting up a page for it soon, and I really do hope that it gets up and running in the future. :)

---

### Post by LordHunter317 on 2005-10-21
> **wolphin]I think something like 'apt-get install --dry-run xxxxx' might work, but again, I can't check that until later on today.[/quote]No, no.  I'm talking about after I return to my disconnected machine with all my packages, how do I install them in one command?

You haven't even considered that yet.

>  If not, I guess it wouldn't be too hard to make a script which just 'sudo dpkg -i *.deb' everything. Correct?Yes, but that won't work.

[quote] As I said - I'm only trying to put forward an idea. I haven't worked out all the little nooks and crannies yet....  said:**
> These aren't little though.  These are fundamental design concerns.

[quote]So, is anyone interested in joining the project? I'm setting up a page for it soon, and I really do hope that it gets up and running in the future. :)I really think you need to sit down and write a better design first before you start recruiting, or just ask for someone to do your design for you.  There's too many pieces missing here.

---

### Post by wolphin on 2005-10-21
[QUOTE=LordHunter317]No, no.  I'm talking about after I return to my disconnected machine with all my packages, how do I install them in one command?

You haven't even considered that yet.[/quote]I have considered it, actually. Why do you think I was talking about the dpkg -i *.deb and apt-get install --dry-run?

> Yes, but that won't work.Which is why I was asking if it was correct or not...and I've run a Python script which needed to work as root (and it did its job flawlessly), so I'm not quite sure *why* it wouldn't work.

> These aren't little though.  These are fundamental design concerns.I never said I was going to perfect the program's design by myself. I was putting forward an *idea* which I was hoping others could expand on, but it's fine if you want to criticise me instead. :)

> I really think you need to sit down and write a better design first before you start recruiting, or just ask for someone to do your design for you.  There's too many pieces missing here.Ok, I was just articulating on what could be quite a good and useful application. I was describing its bare-bones uses to give readers a rough idea of what I was talking about. I sincerely apologise if I have frustrated you by not putting enough detail, but it was only an outline of the app. If you want to speculate and add your own improvements, then please post constructively below.

I'm not trying to start an argument, I'd just like you to realise that I wasn't trying to supply every single last detail of the app. I was just giving the community an idea to expand on. I've given the few beginning strands - but I would really appreciate it if others could help me sow them all together.

---

### Post by LordHunter317 on 2005-10-21
[QUOTE=wolphin]Why do you think I was talking about the dpkg -i *.deb and apt-get install --dry-run?[/quote]Well, ok, you've considered.  But neither of those are even to the level of apt-zip.

> Which is why I was asking if it was correctNeither are.  apt-get --dry-run doesn't actually do anything, and dpkg -i *.deb will break in some dependency loop cases.  They're not necessarily common, but they do exist.

> I never said I was going to perfect the program's design by myself. I was putting forward an *idea* which I was hoping others could expand on, Well, I am, by pointing out it's flaws.  People may not like negative criticsm, but focusing on the negatives is often the best way to determine if a design is viable or not.

> Ok, I was just articulating on what could be quite a good and useful application.And here's the crux of the problem: you haven't described anything over and beyond what apt-zip already does.

> I was describing its bare-bones uses to give readers a rough idea of what I was talking about.Which is apt-zip.

> I sincerely apologise if I have frustrated you by not putting enough detail, but it was only an outline of the app.Yes, because you've described somethign that already exists.

> If you want to speculate and add your own improvements, then please post constructively below.No one can until you explain how this will be better than apt-zip.

> I'd just like you to realise that I wasn't trying to supply every single last detail of the app.That's fine.  A full design isn't needed, but you haven't given any design thus far that isn't already present in existing things.

---

### Post by wolphin on 2005-10-21
[QUOTE=LordHunter317]Well, ok, you've considered.  But neither of those are even to the level of apt-zip.

Neither are.  apt-get --dry-run doesn't actually do anything, and dpkg -i *.deb will break in some dependency loop cases.  They're not necessarily common, but they do exist.[/quote]Well, in that case, I guess we'd have to code our own installer. :) I'm not trying to look for a simple way around things - I was just giving suggestions.

> Well, I am, by pointing out it's flaws.  People may not like negative criticsm, but focusing on the negatives is often the best way to determine if a design is viable or not.And I agree entirely, but I do not like blunt rudeness.

> And here's the crux of the problem: you haven't described anything over and beyond what apt-zip already does.Except of course, the fact that it is meant for users who are new to Linux (ie. simplicity) and has a GUI front-end, and that it is compatible with Windows (which means that dual-booters and those who are just trying Linux out can still download more software).

> Which is apt-zip.Which is not apt-zip.

> Yes, because you've described somethign that already exists.

No one can until you explain how this will be better than apt-zip.I have already explained, and I have not described something that already exists. I have described a vast makeover of something that already exists, and have decided to give it both more functionality and better ease-of-use.

> That's fine.  A full design isn't needed, but you haven't given any design thus far that isn't already present in existing things.I have...

---

### Post by LordHunter317 on 2005-10-21
[QUOTE=wolphin]Well, in that case, I guess we'd have to code our own installer. :)[/quote]No, you just feed them to apt-get install, without using --dry-run or any other magic.

Apt-zip may do something else slightly more intelligent, but I'm not sure, I'd have to look at the source.  I can't see any reason why, but I could be missing an edge case.

> And I agree entirely, but I do not like blunt rudeness.If I was trying to be rude, I'd make it clearn.  I'm not and am  sorry you think I am.  I'm simply being blunt because there isn't enough here to work with.

> Except of course, the fact that it is meant for users who are new to Linux (ie. simplicity) and has a GUI front-end, and that it is compatible with Windows (which means that dual-booters and those who are just trying Linux out can still download more software).I see mention of none of those things, besides the downloader needs to run on Windows.

Even still, that's not really enough to go on.  What should this GUI look like?  Should it support adding packages at the download host?

---

### Post by wolphin on 2005-10-21
[QUOTE=LordHunter317]No, you just feed them to apt-get install, without using --dry-run or any other magic.

Apt-zip may do something else slightly more intelligent, but I'm not sure, I'd have to look at the source.  I can't see any reason why, but I could be missing an edge case.[/quote]Hmmm...would it be possible to make a script which would automatically feed them to apt-get install? What about the order they are fed in? (Order is sometimes a problem.)

> If I was trying to be rude, I'd make it clearn.  I'm not and am  sorry you think I am.  I'm simply being blunt because there isn't enough here to work with.I take it back then, because now I see that the design of the app *has* improved just through this argument. :) And I know there isn't enough to work with - which is why I posted the idea here, because I'd like to build the project further. 

> I see mention of none of those things, besides the downloader needs to run on Windows.Really? Damn, I thought I made that pretty clear in my first post... oh well, yeah, that's basically the idea. :D

> Even still, that's not really enough to go on.  What should this GUI look like?  Should it support adding packages at the download host?I'm going to make a mockup of the app's design soon (please feel free to comment on it when I release it), but I cannot really describe the GUI. It would use the GTK+ libraries, and I can't really say much more than that at the moment. I'm sorry, I don't really undestand what you mean by your last question...could you please explain it?

---

### Post by wolphin on 2005-10-23
Please keep contributing to the ideas if you think of something, guys! :D

And I'd really appreciate it too if someone could answer my questions... ;)

---

### Post by doclivingston on 2005-10-23
For the purposes of this, "apt-get --print-uris -y install foo" will probably be more useful; what it does is print out the exact uri, size and md5sum of each of the files that need to be downloaded.


Once the files are available, there are two ways I can think of installing them:
1) "dpkg -i foo.deb bar.deb" and then "apt-get -f install"
2) putting the .deb files in /var/cache/apt/archive/, and then doing "apt-get install -y foo"

I would probably tend to go with (2), because if there are any problems it will refuse to install, whereas (1) may leave you with problems. Another advantage of (2) is that the files will stick around the same as they would have been with apt-get.

---

### Post by LordHunter317 on 2005-10-23
[QUOTE=doclivingston]
Once the files are available, there are two ways I can think of installing them:
1) "dpkg -i foo.deb bar.deb"[/quote]I already pointed out, **twice**, that this will not work.

---

### Post by wolphin on 2005-10-23
doclivingston - Thank you very much for that tip about 'apt-get --print-uris -y install foo'. The only flaw is that how would apt-get know the URIs of a package which was in the Universe repositories, for example. As this does not come standard with the distro, you'd need to run an 'apt-get update' to get the URIs, and this would create a flaw in our app. I think that we could possibly translate and implement some of the code used for that command into the second application (the one with internet access), and then just download the files from the URIs received.

The first would also have a change because it'd need to put the .deb files in /var/cache/apt/archive/ (once the device had been plugged into the offline computer again), and then do 'apt-get install -y var'. - As you kindly pointed out, doclivingston.

I have made a mockup of the design - bear in mind that I haven't spent as much time on this as I'd have liked to, but it does show the basic layout. There will be more graphics, the black squares will be replaced with the appropriate icons, and it will generally look and feel much better. :) [Click here to view the mockup](http://linux.wolphination.com/hyper-get.jpg).

I have also had another idea for a feature we could include in it - support for proxies. I'm not sure if apt-zip supports them, but it'd be great if we could add funcionality with proxy servers to the app (once it's up, which I'm hoping it will be soon! :D).

Thank you for all your comments, and as always, please keep them coming. ;)

---

### Post by UbuWu on 2005-10-23
A graphical installer for deb's is already planned. Read this mailing list post and its follow ups:
[http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012162.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-October/012162.html)

---

### Post by wolphin on 2005-10-23
UbuWu - thank you for that link! While it *is* a graphical installer for .deb files, it isn't the application I'm talking about. The idea I've put forward (if you've been reading the thread) is that you can get packages to an offline computer using another computer with internet access. The other features have already been mentioned, so I won't repeat those, but I guess none of us have come to a conclusion how the .debs will be installed in the end. LordHunter, I'm looking at you for answers :)

Wu- thanks again for that link! It was an interesting read!

---

### Post by LordHunter317 on 2005-10-23
The eaiest way is to dump them in Apt's archive, feed it new package lists, and then a set of fixed commands.   This would all be (presumably) simulated on the download host first.

---

### Post by UbuWu on 2005-10-23
[QUOTE=wolphin] but I guess none of us have come to a conclusion how the .debs will be installed in the end. 
[/QUOTE]

Installing them is not hard, either wait for the mentioned deb installer to be ready or use dpkg-scanpackages to create a local repository (dpkg-scanpackages ./ /dev/null | gzip > Packages.gz) and use apt-get.

---

### Post by UbuWu on 2005-10-23
One idea I thought of today is to implement this on the server side. That way a lot of the problems (most importantly the OS people are using) could be circumvented. 

How this would work:
You enter the name of a program you want to install on a website, and then it will give links to all files you need to download which aren't included on a standard installation and add a packages.gz as well. 
Preferably it would give you a download link to a compressed file containing all the needed packages, but that would need more power from the server.
If you then come home, you only have to add the source as a local repository and install.
And as a bonus, this could all be integrated to packages.ubuntu.com

What do you think of this idea?

---

### Post by wolphin on 2005-10-24
LordHunter - presuming we did it that way, then it would indeed be done on the download host. Once the packages have been downoaded and put onto the drive by the second app, they are plugged into box #1. You then start up the first app, and select the 'Install' tab. From there, you link to your removable drive and presto, your work is done. :)

UbuWu - I think it would be better to do it doclivingston's way, because not only does it look much cleaner, but you don't have to go creating local repositories and stuff. ;) About the idea - I've also thought of that, or at least a server-side Perl script or something to help you download packages AND dependancies. Oh well...as it doesn't exist, it means let's carry on brainstorming this. Hehe!

The mockup was a quick sketch of what the first app would look like, by the way. It still needs to be heavily modified (and will be, with time), and I haven't produced one of the second (and won't unless you want me to). I was just wondering - you know the second application is meant to run on both Windows and Linux? Well, there are loads of GTK+ toolkits available for Windows (like [this](http://gladewin32.sourceforge.net/) port of Glade), so if we did the Linux version with Glade and supplied the Windows one *with* the Glade toolkit, would there need to be any modifications to the source? I'm just trying to think ahead here...

On a brighter note, I will probably be getting the result of my project submission to Sourceforge today - let's hope they accept it. :D

---

### Post by doclivingston on 2005-10-24
[QUOTE=UbuWu]You enter the name of a program you want to install on a website, and then it will give links to all files you need to download which aren't included on a standard installation and add a packages.gz as well. 
Preferably it would give you a download link to a compressed file containing all the needed packages, but that would need more power from the server.
If you then come home, you only have to add the source as a local repository and install.
And as a bonus, this could all be integrated to packages.ubuntu.com[/QUOTE]

The biggest problem I can see, is that it would make you download packages that you already have, but aren't seeded into the standard installation.

That would be particularly a problem because they could be using stock Ubuntu, Kubunu, Edubuntu or something else - so you can't even be sure what "standard" packages they have installed.

---

### Post by UbuWu on 2005-10-24
[QUOTE=doclivingston]
That would be particularly a problem because they could be using stock Ubuntu, Kubunu, Edubuntu or something else - so you can't even be sure what "standard" packages they have installed.[/QUOTE]

You could select that on the webpage.

---

### Post by wolphin on 2005-10-24
Although this isn't strictly what this thread is meant to be talking about (hehe!), that would still leave the problem of the server-side script not 'knowing' what packages your computer has. Let's say an app called 'Johnapp' depends on 'libben 1.8.5', and then you try to download another app which also depends on 'libben', but only supports version 1.9.2. This would mean that you'd end up with some complicated dependancy problems, which would not be fun to solve (especially for a newbie). :)

I still haven't heard back from Sourceforge, but I'm hoping they'll review this app soon enough. :)

---

### Post by wolphin on 2005-10-24
PROJECT ACCEPTED BY SOURCEFORGE! Now, we can get down to rounding off the design and then coding it. Remember, if you'd like to support this project, then please either post here or send me a PM/email. I will be setting up some forums on my subdomain soon for discussions of the project, and I hope some of you will be kind enough to join and participate in the discussion. :)

---

### Post by wolphin on 2005-10-28
Sorry to triple post everybody, but I just have an announcement to make. Two developers have already signed up, which leaves me still looking for around 3-4 more. Both those developers (namely Rohan and Eran, some charming people) are going to work on the Windows side of the second application. This means that I'm still looking for GTK+/GNOME/Glade developers. I myself am learning the interface, but am nowhere near experienced enough to take on such a huge task.

If you are a GNOME/Glade developer in C and you are looking to get your hands dirty or just have some fun, then please consider joining this project. You must know C and be able to use the GTK+ toolkit (with Glade/Anjuta, etc...). Please think about it, because it'll be an interesting project to work on. Thank you.

Max

---

### Post by p1r0 on 2005-11-02
I find your project really iteresting and I'm a C/C++ programmer.
Unfortunatelly I'm new to Linux but I would love to join the project or at leat help in some way.
I guess I don't meet the qualifications for this project but at leat I want to express my support.

If there's any way I can help please let me know.

p1r0

MSN: [email]pyro@bluebottle.com[/email]
MAIL: [email]lucifers.preacher@gmail.com[/email]

---

### Post by VaioLord on 2005-11-02
I love this idea as a newbie to Unbutu I can tell you the my only complaint (issues) are with apt-get.  

The think that I strongly recommend is what ever you do make it usable from a FlashDrive (along the idea of Portable Firefox) so people can use it anywhere even in Internet Cafes or Businesses that do not allow programs to be installed.

---

### Post by wolphin on 2005-11-02
p1r0: Hi! Thank you for showing your interest in this app, as it is definitely appreciated! Even if you're new to Linux, I think that you could play a part in the coding of the first application if you would like to. I'm not quite sure yet what toolkit we're going to be using for the first application, but I'm guessing it's going to be [Glade](http://glade.gnome.org). I think Anjuta can be used to code C apps using Glade, but I'm not much of a programmer myself (yet!) - although I'm sure that others will know! ;)

VaioLord - that is a brilliant idea! Although I guess they could just install it *onto* the flash drive, but I'll ask the other developers to see what they think of it! ;) Thanks for the heads up!

I'm not sure if I mentioned it, but I may also be looking for a Java or a Python developer or two - but I will inform you all tomorrow. :)

---

### Post by p1r0 on 2005-11-11
I would defnitely like to be a part of this project...
Just tell me what to do :D 


p1r0

---

### Post by hammer v2 on 2007-08-21
Hey wolphin,
How you going on that apt program? I'm working a simple script to go with apt-on CD, insert CD, double click on setup and away it goes, no internet required. Anyway, I guess I'm just trying to let everyone know what I'm doing, you can find a detailed description here,

[http://ubuntuforums.org/showthread.php?p=3231019#post3231019](http://ubuntuforums.org/showthread.php?p=3231019#post3231019)

cheers!
H.

---

