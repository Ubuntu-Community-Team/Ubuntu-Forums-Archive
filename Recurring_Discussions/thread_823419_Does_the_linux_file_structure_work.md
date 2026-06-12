---
title: "Does the linux file structure work?"
date: 2008-06-09
forum: Recurring Discussions
---

### Post by abhiroopb on 2008-06-09
I think its safe to say that most if not all users of this forum started of with some variation of windows and then at some point moved to linux.

In windows the file structure is something like this:

c:\[B]
Documents and Settings[/B] - user documents, funnily enough NOT that many settings![B]
Program Files[/B] - where any/all program data goes when you install something[B]
Windows[/B] - has all the system folders and registry entries, basically everything that makes the computer work

This is very simplistic but its what I learnt while using windows. Sure the windows folder has a messy hierarchy, impossible to find anything, etc! However, when you install something other than any settings entries (which may go in the registry), most of the data goes into the Program files folder.

Now for linux:

Under the / directory you have about 15 different folders. Some of them like /home, /media, /mnt, /tmp, /dev, /tmp, /opt, /boot provide very specific functions. However, you then have /bin, /etc, /lib, /sbin, /srv, /sys, /usr, and /var, which all seem to perform arcane and obscure tasks. To the untrained eye they could easily be the same folder. And its true, I've been using linux for a few years, and I have a vague idea of what goes on in the folders, but overall its more of a hindarance than anything else.

Mind you I'm not expert, I've never even compiled a kernel, but I have used linux and these are some of the problems I have found.

1. Lets say I install a program, if I do it with APT, or install a .deb package usually uninstalling it is a simple case of using apt-get or synaptic. However, when I compile a program from source (which is required by a lot of programs). I am left with a plethora of files spread out all over my hard drive. Why is this? Wouldn't it make more sense to have them all in one folder like in windows?

I know this isn't windows and I should use a different mindset but what is the benefit of spreading it out like this?

Deleting programs installed from source (unless checkinstall was used) is a MAJOR hassle, and after 2 years I have no idea what I installed when I first ran ubuntu.

2. Editing system folders seems "safe". What I mean by this is that in Windows, most people know not to touch anything that is under the WINDOWS directory, its taboo, you know if you touch something there something WILL break. In ubuntu editing, menu.lst, sources.list, xorg.conf can all be essential. However, editing some other files can cause MAJOR problems. True this is more about what you know, but still wouldn't it make more sense to have one folder which is practically off limits, which only the super-advanced user would ever need to access? 

What I was envisioning is something like this structure:

**/boot** - this is fine you need it!
**/dev** - again a useful place to put devices
**/home** - for all documents (NB: including program settings as it is easier to backup then)
**/media** - what is the point of /media AND /mnt??
**/proc** - this performs useful functions I've heard
**/tmp** - every filesystem needs this direcotry.

So there are the filesystem that are already there and all seem to perform useful functions. Now consolidating whats left:

**/programs** - any time a new program is installed, either from source, apt, or as a .deb package it should come here. No questions asked ALL the files are placed here. If this is deleted the program is basically wiped clean from the system. users can mess around with this as deleting one program may not harm the system. Although I guess dependencies is a problem, however, I am not totally sure how that is looked after now, so I will leave that to discussions from more experienced users.

**/system** - everything that is installed when the OS is FIRST installed. Most (if not ALL) users can stay away from this, except to edit the occasional menu.lst, etc.

And thats it!

What opinions do you guys have? I'm not saying we need to restructure the file system I just want a debate on this issue.

---

### Post by SunnyRabbiera on 2008-06-09
So you want the system file structure to be like windows then.

---

### Post by abhiroopb on 2008-06-09
Not really, more like a hybrid. And like I said I don't WANT it to be like anything. I just want to understand why there are folder like /etc, /lib, and /bin which to me seems like they serve the same purpose. And I want to understand why a simpler structure won't work.

---

### Post by SunnyRabbiera on 2008-06-09
Well for me the linux filesystem makes perfect sense, as its the unix filesystem at its core.
Its not that hard to figure out.

---

### Post by abhiroopb on 2008-06-09
Would you care to explain why it makes perfect sense?

---

### Post by Barrucadu on 2008-06-09
The reason for a separate /mnt and /media is that /media is for removable media, whereas /mnt is for 'permament' partitions.

---

### Post by SunnyRabbiera on 2008-06-09
Well come on, it doesnt take long to figure out:

/bin= binaries
/lib= libraries
/share= shared files
/user= the user directories
/tmp= temporary files
/media= hard drives
/opt= optional
/sys= system files...

If you cant handle more then C:/program files you are using the wrong OS

---

### Post by abhiroopb on 2008-06-09
I knew I'd strike a nerve with some of the more passionate users, but like I said this is merely a debate, I use ubuntu because it serves my purposes, and I like to be able to customize.

Still your explanation Sunny is something I already know. I know WHAT the folders are for, I want to know WHY they are the way it is.

> If you cant handle more then C:/program files you are using the wrong OS 
so you are saying that unless a system is not inherently complicated its useless?

like I said /media is fine as is /home and /tmp

explain to me what is the use of /share, /lib, /bin?

Thanks Barrucadu for clearing up difference between /mnt and /media, I actually already knew this from another thread, but again is there any point in having a different folder? Except perhaps to make it easier to keep track of whether something is permanent or temporary?

---

### Post by SunnyRabbiera on 2008-06-09
As I said the linux/unix filesystem is not complicated if you know it, even mac OSX has a similar file structure.
The /bin binary directory is where most applications are stored
the library /lib directory is where most of that applications core files are stored
the share directory is where shared files are, simple enough to understand there.
I feel the unix filesystem is great for what it does, it keeps the program files apart from the binaries so that if the libraries are corrupted somehow they are more easy to rectify.

---

### Post by abhiroopb on 2008-06-09
Again that all makes sense but like I said removing a program is very difficult this way. And what is the difference between an applications "core files" and the "application"? Which files are "shared"? How are program files kept apart from binaries if you say most applications are stored in the binary direcotry? Also what are the other folders like /usr for?

---

### Post by SunnyRabbiera on 2008-06-09
as I said /usr directory is for users, this is a common directory in unix filesystems...
unix is a multiuser OS by default, the /usr /lib and /shared directories are all important in keeping the files separate and secure.
Really if you need to complain you will find the OSX filesystem no different.
[http://osxdaily.com/2007/03/30/mac-os-x-directory-structure-explained/#comment-31862]("http://osxdaily.com/2007/03/30/mac-os-x-directory-structure-explained/#comment-31862")

Only windows has the type of file system you request, and trust me its file structure is a part of its issues...
But not everything is as well organized in windows too you know, there isnt just C/program files, there is crap in application data, the windows directory too.

---

### Post by abhiroopb on 2008-06-09
I am not complaining!!!! Why do you keep assuming that I am complaining? I am happy with Ubuntu (again I've said it!). And I don't care what Mac OSX users, what difference does it make with my question here.

And I don't care that windows has problems (thats not why I am here). 

All i want to know is why is the file structure of linus designed the way it is. So far you've just said that it is to keep things separate and secure. How does that work? Couldn't I just as easily delete it? and I though /home was for users what is there in /usr anyway?

---

### Post by SunnyRabbiera on 2008-06-09
Again we talk about linux and unix filesytems here...
there is a big difference between /home and /usr
the home directory is assigned to its respectable owner, but the usr directory is something else.
there is the root folder directories such as /bin and /sbin, these are seperated from the main binaries as they are improtant to the OS.
the /usr directory contains files that ALL users will use in some shape or manner and dont need root accounts to access.
[and here we have another page explaining things]("http://www.freeos.com/articles/3102/")

---

### Post by SupaSonic on 2008-06-09
I'm with abhiroopb on this. It doesn't really bother me, but I don't know what's going on in these folders as well. And the suggestion that if I don't know this I should use Windows is stupid. The way / organized is NOT intuitive, and I believe this is the point the OP is making. For instance we have /bin, /usr/bin and /usr/sbin. Now I'm sure there are perfectly justified reasons for this, but it still might puzzle somebody more curious than me.

As for installing programs from source, I use checkinstall to make debs from source and install them. At least I can uninstall those debs later, albeit checkinstall has its own issues.

---

### Post by master5o1 on 2008-06-09
I believe /usr has nothing to do with users but actually unix system resources. I may be wrong.

---

### Post by ThrobbingBrain66 on 2008-06-09
Here is the Unix Filesystem Hierarchy Standard.  It's quite long, but I believe you'll find your answers.

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by abhiroopb on 2008-06-09
So if sbin and bin perform similar functions can they not be one directory? My issue isn't even that its not intuitive, because I guess if you want to mess around with it thats your problem. My question is there still a genuine need? I mean I'm sure that this sharing lib files or whatever made sense when disk space was limited, but does that still apply? Why not package each program with all the required dependencies? Make  it one package with everything.

---

### Post by OoooMatron on 2008-06-09
@abhiroopb

I also agree with you on the points you make.

It's near impossible to fully track a program that has been installed and you can never fully tidy up your files with confidence after manually removing. How can you know where it's all installed?? Why doesn't it have it's own folder with all the files in it? Beats me. It's like the old windows days when files could literally be placed anywhere.

I'd like a single directory per program to understand what was put there. Much easier.

---

### Post by SunnyRabbiera on 2008-06-09
because linux does not use binary installers, and if there was a installer file like that on windows it will be too big.
as for your question, yes its better to have sbin and bin separate, that way if normal binaries become corrupted they wont infect key files.

> **OoooMatron said:**
> @abhiroopb

I also agree with you on the points you make.

It's near impossible to fully track a program that has been installed and you can never fully tidy up your files with confidence after manually removing. How can you know where it's all installed?? Why doesn't it have it's own folder with all the files in it? Beats me. It's like the old windows days when files could literally be placed anywhere.

I'd like a single directory per program to understand what was put there. Much easier.

again, if you want a filesystem like this use windows...

---

### Post by abhiroopb on 2008-06-09
Its clear that newer users are finding it a hassle as Oooo points out. But again to reiterate I'm sure as I become a more advanced user I will see that there are justifiable reasons. I guess I'll read the links to figure out what those reasons are!

---

### Post by SunnyRabbiera on 2008-06-09
It all goes back to unix, heck even windows has a unix like filesystem now in vista.

---

### Post by abhiroopb on 2008-06-09
But thats what I'm saying. I'm no expert but wasn't Unix written for computers that were vastly inferior to what we are using today? I mean perhaps the way it was structured was so as to conserve space.

---

### Post by SupaSonic on 2008-06-09
> **OoooMatron said:**
> 
I'd like a single directory per program to understand what was put there. Much easier.

It's a double edged sword. Users might start seriously messing up their system with this. At least the way it currently is everything seems to work. So I'd say the devs know exactly where everything should go.

---

### Post by abhiroopb on 2008-06-09
I disagree. Although there is the old age if it ain't broke don't fix it like I identified originally there can be problems as it currently stands. If there is a single directory per program deleting  a directory means I potentially comprimise one program. As it stands now I don't delete a directory i delete some obscurely named file which for all I know is what keeps my speakers working!

---

### Post by SunnyRabbiera on 2008-06-09
> **abhiroopb said:**
> But thats what I'm saying. I'm no expert but wasn't Unix written for computers that were vastly inferior to what we are using today? I mean perhaps the way it was structured was so as to conserve space.

Yes that is probably a part of the reason, even DOS had something like our filesystem at some point.
But Unix in its original form was never targeted at desktop users, it was for servers.
On servers its not a good idea to have root files mixed in with user files, this is where the windows issues come in at.
Unix in its original form was the pinnacle of security thanks to its directory being different then most others, if an attack happened on the user level the core could still function like nothing happened.

---

### Post by Flimm on 2008-06-09
Windows is not half as simple as you made it out to be.
> **abhiroopb said:**
> 
In windows the file structure is something like this:
c:\[B]
Documents and Settings[/B] - user documents, funnily enough NOT that many settings![B]
Program Files[/B] - where any/all program data goes when you install something[B]
Windows[/B] - has all the system folders and registry entries, basically everything that makes the computer workSorry, that's wrong. Lots of settings get installed in Documents and Settings, let's see, in Windows XP, you have the Local Settings and Application Data folders, Local Settings stores IE's cache, whereas Application Data stores Opera's cache. I'm pretty sure there's the user registry file under Documents and Settings as well.
Program Files: not just for program files, but also for user files. This is mainly because Windows historically did not have a strong ownership and permission structure like Linux, and so a lot of programs stored their user information in Program Files. Opera, if you install it in single user mode, will put bookmarks and cache in there.
Windows: this contains much more than just the basic necessities to make this system work, this contains system32's dll hell, which means program files end up in both Program Files and Windows.

> 1. Lets say I install a program, if I do it with APT, or install a .deb package usually uninstalling it is a simple case of using apt-get or synaptic. However, when I compile a program from source (which is required by a lot of programs). I am left with a plethora of files spread out all over my hard drive. Why is this? Wouldn't it make more sense to have them all in one folder like in windows?

I know this isn't windows and I should use a different mindset but what is the benefit of spreading it out like this?
 When you install programs in Windows, files are spread out across the entire filesystem. Only stand-alone .exe's don't do this. Try searching for stand-alone's and you'll find out there are quite rare on the Windows side. Why do you think setup.exe's are necessary? It's in order to spread out files!

Windows tries to hide how complicated it really is by only providing three folders. Ubuntu tries to hide how complicated it really is by only showing a two folders: the home folder and the /media folder, and by always, always insisting on debs and the repository. Compiling from source was never meant for humans.

---

### Post by abhiroopb on 2008-06-09
Again like I said I wasn't sure about windows. In any case my comparison with windows was only to get this discussion started. I don't care how Mac OSX or Windows works. I was clearly wrong and I accept that. What I am trying to understand is why is Linux so convoluted? 

As Sunny points out Unix was designed for servers and so for security. Is this why it is the way it is currently? So the entire basis of linux is based on something that was originally designed for servers? Sure its safe, which is very important, but is it practical any more?

---

### Post by bogoliubov on 2008-06-09
But in OS X, the applications are usually kept in a single folder. Sure, some applications has to be installed using Fink or Darwinports, but the applications that are made for OS X are each kept in a separate folder. 

What is bad about this? I'd still like to have APT since it's very good, but to me the file structure of Linux is a bit strange and I agree that some parts seem unnessecary.

---

### Post by joninkrakow on 2008-06-09
> **abhiroopb said:**
> I am not complaining!!!! Why do you keep assuming that I am complaining? I am happy with Ubuntu (again I've said it!). And I don't care what Mac OSX users, what difference does it make with my question here.

And I don't care that windows has problems (thats not why I am here). 

All i want to know is why is the file structure of linus designed the way it is. So far you've just said that it is to keep things separate and secure. How does that work? Couldn't I just as easily delete it? and I though /home was for users what is there in /usr anyway?

The file structure is "flatter" than Windows... That's all. If you open your Windows folder, you will find a complex array of directories, and none of it makes _any_ sense to my eye. I've played a lot with Win 3, and a bit with Win 95, and less with Win 98 and 2000, and haven't even looked at XP, but every iteration, this structure got more complex and inscrutable--like you said--"smart" users don't touch it. 


However, the Unix directory structure is flatter, and much less inscrutable. In fact, it's very logical--if you know the logic. Yes, it is arbitrary, but, but it is also logical.

Others have mentioned the logic of the structure, but maybe a couple points would be helpful.

any folder named "bin" is where the main executable, binary code goes. "Share" is where shared libraries go. include is for compiling--at least in my experience(I understand include less than the others). etc. is for various configuration files. 

All of these things are shared between applications, so, for instance, if you use multiple windows managers, they all know where to look for things. All the programs do, too. 

Now, when it comes to the usr folder it's a bit different. BTW, usr is _not_ short for "user". That is the "home" folder's task. That's where all your personal files go, and the only place a user should think of putting things and looking. The system should take care of putting things in the other places, or, if you like using the command line to configure, to navigate that to manually configure things.

Now, the top level folders (/bin;/mnt:/dev;/opt;/etc, etc) are for the lowest level system items. Typically, other than X11 stuff, they all should be for use before you start X. It's all the real nitty-gritty stuff. For instance, your super basic command line tools will be in /bin and /sbin.

The real fun in Linux begins when you go into the /usr directory structure. Now, usr (Unix System Resources? or Uniform System Resource? I forget the exact acronym, but it's something like one of these--Google(R) it.) contains all the goodies that you need to make your copy of Unix yours. Oddly, I believe that Ubuntu kind of breaks a bit of Unix pattern in usr, because it puts the bulk of its binaries and such in /usr/bin, rather than /usr/local/bin, and all the libraries, etc. also go in /usr/ rather than /usr/local. I'm not really sure why, but in any case, it helps me, because when I compile something from scratch, I put it into /usr/local, which is almost empty except for my own mucking around, so I really can't complain. :-)

However, another place to put your own "creations" is the /opt folder at root. It is "optional" you know. ;-) 

So, as I said, there is logic--just not the Windows logic. Yes, Linux could (and Ubuntu, in particular could) create a "System" folder, and drop all of these into it--and, in fact, if you were savvy enough, you could do it yourself! But that would take away the simplicity and "flatness" that the directory structure has now. 

Personally, I'm quite happy with the way things are.

(For the record, when I upgraded my Mac to OS X, I made all invisible files and folders visible, and began to explore what it was all about--that's when and where I learned all this stuff--however, my understanding has vastly deepened since installing Ubuntu, and beginning to actually compile from source! If you really want to begin to understand the whys and hows, I heartily recommend trying to compile some things from source--it will help you immensely.)

-Jon

---

### Post by SunnyRabbiera on 2008-06-09
> **bogoliubov said:**
> But in OS X, the applications are usually kept in a single folder. Sure, some applications has to be installed using Fink or Darwinports, but the applications that are made for OS X are each kept in a separate folder. /QUOTE]

Well OSX still has some characteristics as linux does, it probably has its own share of unusual directories too.

[QUOTE=abhiroopb;5147831]What I am trying to understand is why is Linux so convoluted? 

As Sunny points out Unix was designed for servers and so for security. Is this why it is the way it is currently? So the entire basis of linux is based on something that was originally designed for servers? Sure its safe, which is very important, but is it practical any more?

Linux may seem convoluted, but its less convoluted if you know how it works.
Now as for the unix debate, yes it holds many standards that may seem out of date or impractical to people... but we are talking about a OS that is older then DOS, in fact UNIX is probably the oldest OS that is still in wide use today in some shape or form and that includes linux.
It is what works that matters here, and the unix standard is a good standard to live by.

---

### Post by joninkrakow on 2008-06-09
> **bogoliubov said:**
> But in OS X, the applications are usually kept in a single folder. Sure, some applications has to be installed using Fink or Darwinports, but the applications that are made for OS X are each kept in a separate 

But do you know what's inside each app? Pop one open some time. Often, (esp. open source apps, and ports from Unix) they contain the entire /usr structure inside them! /usr/bin /usr/share /usr/lib, etc! Granted, not all are like this, and even if they aren't just like this, there is a rather complex folder structure inside for the various resources! What is really funny is that sometimes, they contain duplicates of resources that, if OS X duplicated completely the Unix structure, they would not need. 

Granted, it does simplify things for the average end-user. He simply drops the app from the disk image to the Applications folder, but there is a lot of duplication and triplication, etc. of resources. Mac apps can get rather big because of this. 

-Jon

---

### Post by Ebuntor on 2008-06-09
> **joninkrakow said:**
> The file structure is "flatter" than Windows... That's all. If you open your Windows folder, you will find a complex array of directories, and none of it makes _any_ sense to my eye. I've played a lot with Win 3, and a bit with Win 95, and less with Win 98 and 2000, and haven't even looked at XP, but every iteration, this structure got more complex and inscrutable--like you said--"smart" users don't touch it. 


However, the Unix directory structure is flatter, and much less inscrutable. In fact, it's very logical--if you know the logic. Yes, it is arbitrary, but, but it is also logical.

Others have mentioned the logic of the structure, but maybe a couple points would be helpful.

any folder named "bin" is where the main executable, binary code goes. "Share" is where shared libraries go. include is for compiling--at least in my experience(I understand include less than the others). etc. is for various configuration files. 

All of these things are shared between applications, so, for instance, if you use multiple windows managers, they all know where to look for things. All the programs do, too. 

Now, when it comes to the usr folder it's a bit different. BTW, usr is _not_ short for "user". That is the "home" folder's task. That's where all your personal files go, and the only place a user should think of putting things and looking. The system should take care of putting things in the other places, or, if you like using the command line to configure, to navigate that to manually configure things.

Now, the top level folders (/bin;/mnt:/dev;/opt;/etc, etc) are for the lowest level system items. Typically, other than X11 stuff, they all should be for use before you start X. It's all the real nitty-gritty stuff. For instance, your super basic command line tools will be in /bin and /sbin.

The real fun in Linux begins when you go into the /usr directory structure. Now, usr (Unix System Resources? or Uniform System Resource? I forget the exact acronym, but it's something like one of these--Google(R) it.) contains all the goodies that you need to make your copy of Unix yours. Oddly, I believe that Ubuntu kind of breaks a bit of Unix pattern in usr, because it puts the bulk of its binaries and such in /usr/bin, rather than /usr/local/bin, and all the libraries, etc. also go in /usr/ rather than /usr/local. I'm not really sure why, but in any case, it helps me, because when I compile something from scratch, I put it into /usr/local, which is almost empty except for my own mucking around, so I really can't complain. :-)

However, another place to put your own "creations" is the /opt folder at root. It is "optional" you know. ;-) 

So, as I said, there is logic--just not the Windows logic. Yes, Linux could (and Ubuntu, in particular could) create a "System" folder, and drop all of these into it--and, in fact, if you were savvy enough, you could do it yourself! But that would take away the simplicity and "flatness" that the directory structure has now. 

Personally, I'm quite happy with the way things are.

(For the record, when I upgraded my Mac to OS X, I made all invisible files and folders visible, and began to explore what it was all about--that's when and where I learned all this stuff--however, my understanding has vastly deepened since installing Ubuntu, and beginning to actually compile from source! If you really want to begin to understand the whys and hows, I heartily recommend trying to compile some things from source--it will help you immensely.)

-Jon

Excellent post joninkrakow, answered all my questions, thanks. :)

---

### Post by bogoliubov on 2008-06-09
> 
It is what works that matters here, and the unix standard is a good standard to live by.

Yes, I'm sure you're right. But doesn't OS X also follow this standard, at least to some extent? I mean, the way of storing application files is quite transparent in OS X, at least compared to Linux. I'm sure there is a perfect reason divide stuff into /bin , /usr/bin , /usr/local/bin and so on, but there are also good reasons to install files under /Applications as in OS X!

---

### Post by Alasdair on 2008-06-09
There is a nice image showing the unix file structure [here]("http://www.secguru.com/files/linux_file_structure.jpg") 

The /usr subtree does in fact stand for user and not unix system resources, which is a popular backronym/urban myth. It's for things that are installed by a user, rather than what is shipped by the distribution. Supposedly the reason for this is so you can boot into a single user rescue mode without /usr in order to recover you system, which seems somewhat arcane and pointless in these days of fancy liveCD's. However keeping a distinction between 'core' files and user installed files in not a bad idea in itself. 

The OP may be interested in the GoboLinux distrobution, which does pretty much what he describes with the filesystem. See:
[http://www.gobolinux.org/?page=doc/articles/clueless](http://www.gobolinux.org/?page=doc/articles/clueless)

---

### Post by jespdj on 2008-06-09
> **SunnyRabbiera said:**
> It all goes back to unix, heck even windows has a unix like filesystem now in vista.
Really? In what way? The filesystem structure in Vista doesn't look anything like a Unix-like filesystem, and isn't that much different from previous Windows versions.

---

### Post by geoken on 2008-06-09
> **joninkrakow said:**
> 

Granted, it does simplify things for the average end-user. He simply drops the app from the disk image to the Applications folder, but there is a lot of duplication and triplication, etc. of resources. Mac apps can get rather big because of this. 

-Jon
 On the flipside, I'm sure most average linux users have a boatload of orphaned libraries on their system. Half of the .py files on my system are probably for apps that I've tried, but have since uninstalled. 

I just deleted a massive chunk of files that were brought in when I tried out Amarok 2. I wouldn't even have thought to check after doing a 'complete' removal in synaptic had I not recieved a message from the update manager asking me to update this file (IIRC, it was well over 10mb).

I think it would be interesting to do some actual research into this. Basically taking snapshots of a bunch of OS X installs, comparing them to a bunch of Linux installs and seeing if duplicated libraries out number orphaned libraries (in terms of memory used).

---

### Post by regomodo on 2008-06-09
i think the filestructure is fairly self-evident and fine. I have one confusion however, i'm not too certain what the differences between /usr/sbin and /usr/bin,  /bin and /Usr/bin, etc are

---

### Post by tuebinger on 2008-06-09
It works for me.

---

### Post by Luke has no name on 2008-06-09
The differences between /bin, /sbin, /usr, /usr/local, still confuse me.

The BSD structure is cleaner, and all software has a predictable folder for config files, local files, etc. Linux has these sorts of things all over the place.

From "FreeBSD 6 Unleashed":

> 
There are some important differences between the FreeBSD directory structure and that of similar operating systems, such as Linux. FreeBSD's structure is tightly controlled, and the clearest rule is this: *Anything installed by the administrator goes into the directory structure under /usr/local.* Although other systems might allow user-installed programs the freedom to install files wherever they want, FreeBSD maintains strict structural guidelines in its ported programs and packages to ensure that all your own installed files are kept inside the /usr/local structure.

 Although a program might, by default, put its libraries in /var/lib and its configuration files into /etc, FreeBSD patches (modifies) the installation scripts so that the files would go into /usr/local/lib and /usr/local/etc, respectively. In fact, all configuration files for any software you might install will go into /usr/local/etc. If the program installs a startup script to be launched on boot, the script is placed in /usr/local/etc/rc.d. Anything in that directory is run at boot time, after the scripts in the analogous /etc/rc.d (the base system's startup scripts) are run.

I do not know how much Ubuntu enforces this standard of consistency. Linux as a whole certainly doesn't.

---

### Post by K.Mandla on 2008-06-09
Moved to Recurring Discussions.

---

### Post by quinnten83 on 2008-06-09
> **abhiroopb said:**
> So if sbin and bin perform similar functions can they not be one directory? My issue isn't even that its not intuitive, because I guess if you want to mess around with it thats your problem. My question is there still a genuine need? I mean I'm sure that this sharing lib files or whatever made sense when disk space was limited, but does that still apply? Why not package each program with all the required dependencies? Make  it one package with everything.

Actually there isn't always a need anymore.
Some of these systems are legacy.

---

### Post by SunnyRabbiera on 2008-06-09
> **quinnten83 said:**
> Actually there isn't always a need anymore.
Some of these systems are legacy.

yes but those legacy files are good for servers.

---

### Post by abhiroopb on 2008-06-09
is that why linux is not ready for the desktop?

---

### Post by smartboyathome on 2008-06-09
I have a project this summer to "customize" my filesystem structure using Gobohide (from Gobolinux) and symlinks. With this meathod, you should be able to make the file system to be layed out however you want.

---

### Post by joninkrakow on 2008-06-09
> **geoken said:**
> On the flipside, I'm sure most average linux users have a boatload of orphaned libraries on their system. Half of the .py files on my system are probably for apps that I've tried, but have since uninstalled. 

I think it would be interesting to do some actual research into this. Basically taking snapshots of a bunch of OS X installs, comparing them to a bunch of Linux installs and seeing if duplicated libraries out number orphaned libraries (in terms of memory used).

Good point. On the other hand, while setting up my Dell box, I discovered the apt-get autoremove command. It seems to remeove extra dependencies that were added when I installed the software. It seems to work so far--at least, the packages I've removed shortly after installing them. I wonder how well apt or aptitude are at removing such dependencies.

-Jon

---

### Post by Luke has no name on 2008-06-09
> **SunnyRabbiera said:**
> yes but those legacy files are good for servers.

While legacy software support can be useful, we should not always stick to the old way for the sake of back support. Look at the people complaining about how bloated Windows is because of its binary compatability with software as old as Windows 95!

---

### Post by the yawner on 2008-06-09
Okay. I've been skirting over this little detail about Linux (and Unix in general) for a while. But so far, here's what I understand about the perks of this type of system

- Common libraries can be shared by multiple applications which equate to lesser resources/duplications.
- Files are grouped to easily enforce user restrictions (like how only root may modify /root etc).
- Directories (even the system directories) can be mounted on separate partitions. Thus I can keep my /home or my /var/www/ on a separate partition/disk which was something I wished I could do with my XP because it's easier to control and monitor my diskspace this way. I can also upgrade (or possibly delete) the core components and keep my personal data.

---

### Post by SunnyRabbiera on 2008-06-09
> **abhiroopb said:**
> is that why linux is not ready for the desktop?

That is a manner of a opinion sir.
Me I say linux is more then ready for the desktop, its the desktop that is not ready for linux...

---

### Post by aaaantoine on 2008-06-09
> **abhiroopb said:**
> I think its safe to say that most if not all users of this forum started of with some variation of windows and then at some point moved to linux.

In windows the file structure is something like this:

c:\[B]
Documents and Settings[/B] - user documents, funnily enough NOT that many settings![B]
By the way, in Vista, this has been changed to the much more palatable C:\**Users**.

> Deleting programs installed from source (unless checkinstall was used) is a MAJOR hassle....
```
sudo make uninstall
```

It may or may not work, but it's better than trying to manually find and delete files.  For best results, I'd keep a copy of the source code of your current software version handy.  And, I also recommend running this (using the older source) before installing a newer version.

---

### Post by miggols99 on 2008-06-09
Maybe you should have a look at [GoboLinux](http://www.gobolinux.org/) if you're uncomfortable with the Linux directory structure.

Anyway, the Windows file structure is a lot more complicated IMO. Like where can I find my settings in Documents and Settings? In Linux, just look at the hidden files in your home folder. I can never find anything in the /windows directory, the names are so confusing...maybe they wanted to stop people fiddling around in there? ;)

---

### Post by original_jamingrit on 2008-06-09
It's also useful to keep things seperate, so you can have different things on different partitions.  You could have the root directory on one partition, /usr/local on another (/usr/local is where manually installed programs normally go) /home on a seperate partition.  This offers benefits in preventing fragmentation or corruption from affecting an entire hard disk, just parts of it.

Also, it's helpful for groups and permissions in the same way.

It's simple, for people who work with the filesystem a lot on a regular basis.  But a dabbler might make an interesting project of rearranging the filesystem.

---

### Post by aysiu on 2008-06-09
Do you also do mods to your toaster and complain that the wiring inside doesn't make sense to the uninitiated in toaster repair?

Then why do you compile your own software and then complain that the file structure doesn't make sense to the uninitiated in *nix systems?

I've used Windows, Mac, and Ubuntu, and I don't really care to get to know the "guts" of any of those systems. I don't care about the .dlls and libs. I don't care about the .plists, registry keys, or config files. I just want to play my music, organize my photos, surf the web, and check my email. Guess what folder I always access to do those things? C:\Documents and Settings\*username* or /Users/*username* or /home/*username*

In Windows, I double-click a setup wizard, and I don't care where it installs all the .dlls and other stuff to make the program work. I just want my launcher in the Start Menu. In Mac, I drag the application icon to the Applications folder. I don't care what other stuff makes the program work. I just want Spotlight or Quicksilver to be able to find the program when I need to launch it. In Ubuntu, I use Synaptic Package Manager to look for and install or remove software, and I don't care what directories the programs get installed to as long as their is a launcher in the menus (or, barring that, I can launch it from the command line with the name of the program).

The only shortcoming I see is a lack of .desktop files for some applications, and this has nothing to do with the filesystem hierarchy. This is about packaging software properly. The software maintainer should include a .desktop file so that the user doesn't have to know the command to launch the program. 9 times out of 10, though, if you're missing a launcher, you can find the command in /usr/bin or can just type the command after Alt-F2.

---

### Post by abhiroopb on 2008-06-09
If it works for you thats great. One of my most major concerns is that installing (and then removing) programs from source is a pain because of how the files get spread around (unless there is an uninstall script). 

Also there is the case of dependencies, temp files, and other junk building up. Do you know that every time you install an app through synaptic the package remains in var/cache/apt? I only recently realised this and managed to free up 3GB of space by deleting the files in that folder!!

---

### Post by aysiu on 2008-06-09
I don't understand why you want to compile apps from source and then complain about the file structure.

If it's that big a deal to you, use [Checkinstall](https://help.ubuntu.com/community/CheckInstall).

As for your Synaptic problem, go to Settings > Preferences > Files

There you can choose to delete packages right after installation or delete the files manually.

---

### Post by abhiroopb on 2008-06-09
I complain about compiling apps from source and the file structure because many apps require compiling from source. And it is only recently that I discovered checkinstall. Anyway thats besides the point. This discussion is about why the file structure is the way it is. If you don't care about how it works or why it works the way it does then this is obviously not the place for you to debate the issue. I too am just a user, I want a system that can play music, videos, where I can surf the web and send e-mails and write essays. But I want to learn about the system and how it works. I have been doing that slowly. Already on this forum there is a conflict between simply the meaning of /usr!

I looked at GoboLinux and a LOT of what they say makes sense, a big reason behind the way linux is structured this way is because it was always this way. True there are clearly good reasons why it is like that, but still it seems as though such a file structure is used because thats the way it was always done!

---

### Post by aysiu on 2008-06-09
Instead of lobbying to "improve" the file structure, why don't you lobby to have these "many" apps that need to be compiled from source properly packaged as .deb files?

I've used Ubuntu for three years, and I've never encountered an application I wanted to use that I had to compile from source.

---

### Post by smbm on 2008-06-09
> Does the linux file structure work?

Clearly it does.

---

### Post by abhiroopb on 2008-06-09
The latest pidgin needs to be compiled from source. The one in the repos is a few months old I believe. Again the issue isn't being able to insall apps so much as WHY is it the way it is? Is there any perceived benefit? I mean what you are implying is that the file structure is just the way it is, so its better to change everything around it. Isn't that the windows philosophy? And why every new iteration gets more bloated? Of course it isn't feasible to start from scratch every time, but using the argument that we should change the ecosystem of applications seems a lit illogical.

---

### Post by aysiu on 2008-06-09
No, I'm not arguing that we shouldn't change it because it "is just the way it is." I'm arguing that it works, and you are blaming the file structure for problems that have nothing to do with the file structure (lack of packaging for certain applications).

I haven't seen any additional bloat in the file structure. Can you explain what you mean by that? Maybe give some examples?

And God forbid you should have to use a version of Pidgin that's a few months old.

---

### Post by John.Michael.Kane on 2008-06-09
> **abhiroopb said:**
> The latest pidgin needs to be compiled from source. The one in the repos is a few months old I believe. Again the issue isn't being able to insall apps so much as WHY is it the way it is? Is there any perceived benefit? I mean what you are implying is that the file structure is just the way it is, so its better to change everything around it. Isn't that the windows philosophy? And why every new iteration gets more bloated? Of course it isn't feasible to start from scratch every time, but using the argument that we should change the ecosystem of applications seems a lit illogical.

The latest pidgin does not need to be compiled. A perfectly good deb is available from the get deb website, and while your issue may not be about the installation of applications. Yous questions regarding file structures will inevitably lead to the discussion of applications, and where they are installed. 

Reason is in order for you to understand the structure fully eg: not from an end user only perspective you will have to understand what is installed, where it is installed, and why.

You cannot simply ask does file system structure xyz work without asking why does xyz app, driver, lib etc is put there.

You also have to remember you are talking about a file system structure etc that dates back to before there were home users. So in theory the file structure we as homes users, are using was at one time built for use on big iron.

Also, as stated there are numerous benefits most of which go unseen by the home user, unless that home-user chooses to take the initiative to understand why their system is set the way it is. 

Regarding your question. Does the file structure work? Answer: Depends on whom you ask, and how the particular system in question is set up. 

IMHO the file structure, as it is works fine, and like anything new one must get use to the way it works.

---

### Post by Polygon on 2008-06-09
mac uses the same file structure that unix and linux does, but somehow they hide it from the end user. All you see are desktop, documents, movies, music, favorites, library...etc Maybe that is what the OP is wanting? It would be the best of both worlds....logical for the person who doesnt really want to tinker but the file system is THERE for the people who do.

there was also a linux distro that tried to do something like that using symlinks. I forget what it is called however.

---

### Post by aysiu on 2008-06-09
> **Polygon said:**
> mac uses the same file structure that unix and linux does, but somehow they hide it from the end user. All you see are desktop, documents, movies, music, favorites, library...etc Maybe that is what the OP is wanting? It would be the best of both worlds....logical for the person who doesnt really want to tinker but the file system is THERE for the people who do.

there was also a linux distro that tried to do something like that using symlinks. I forget what it is called however.
I could be down with that, but I think most people here would be against hiding the file structure. I really like what Apple did with that. /Users makes far more sense than /home, for example. Not sure I dig /Volumes instead of /media, though.

---

### Post by geoken on 2008-06-09
> **aysiu said:**
> 

I've used Ubuntu for three years, and I've never encountered an application I wanted to use that I had to compile from source.

Then you're lucky. 

The most recent things I can remember are Buzztard, and some libraries for exaile plugins to try and get music on to my mp3 player. 

Also, the desire to install the latest versions of software isn't always based on the need to be cutting edge. Many times the newest versions have needed functionality to the point where the app would be useless to you had that functionality been absent.

---

### Post by cardinals_fan on 2008-06-09
> **geoken said:**
> Then you're lucky. 

The most recent things I can remember are Buzztard, and some libraries for exaile plugins to try and get music on to my mp3 player. 

Also, the desire to install the latest versions of software isn't always based on the need to be cutting edge. Many times the newest versions have needed functionality to the point where the app would be useless to you had that functionality been absent.
Make your own packages :popcorn:

---

### Post by smartboyathome on 2008-06-09
I think that the file system structure *could* use an update. I think that having one folder for one application can lead to the potetional to be able to install packages from source/rpm/etc and then be able to detect it in the package manager with a remove option. It could be done with the Gobohide patch + userland app. Of course, like in everything, there are conservatives which don't like this, and like all new ideas, it isn't precieved well. That is why the users have to impliment it before it is adopted.

---

### Post by abhiroopb on 2008-06-10
Yes I think that is the main problem. Meaning no disrespect, but reading the first few posts it was apparent that many users just dismissed my thoughts as a rambling "n00b". Again I stress I am not "lobbying" for change. This is more of a "fact finding" mission. I merely want to understand why it is designed the way it is. Clearly it is old. No-one can deny that. A few of the reasons I have identified why it is the way it is (please correct me, or add to it):

1. Better legacy support for servers, which is what Unix was originally targetted towards.

2. Better security by keeping core system files separate (still don't understand how this works, and would like more information. A few people mentioned that core files are kept separate, I personally don't see how this happens as clearly files are spread out and kept together. Again need clarification).

3. Easier to manage, partitioning a drive and leaving certain folders on a different drive.

4. Better resource management as library files don't have to be duplicated.

5. Files are grouped to easily enforce user restrictions (like how only root may modify /root etc). (thanks to yawner)

The 5 points I identified above also seem a little silly today. 

1 is completely useless for desktop use. 

2 I don't really understand because on the one hand someone mentioned that the "core" is kept secure even if other files are damaged. How can this be the case if everything seems to be kept together but separate (at the same time!). 

3 I guess is fine if thats what you want to do, however, I doubt most ordinary users would want to partition more than /home, and perhaps /boot. Agreed that messing with the file system is not something average users would do anyway. So that is something I can accept as potentially useful. 

4 do we really need to conserve resources nowadays? I mean sure if you have a 10-40gb HD then resources might be a problem but today 100gb hard drives are pretty much standard. Perhaps that why the Mac method makes sense where each application basically has its own file structure with copies of every single library. Agreed this is unnecessary duplication but when each file is about 10kb does it really matter that much? Plus now if I were to delete a lib file or something I may destroy 10 different apps, on the other hand in Mac I destroy only that one app. I think better resource management, while always sounding good, does not really apply in todays world.

5 this I think is possibly the best argument. But then again I don&#8217;t see why changing the structure could not still allow this!


I suppose it is much easier to compare file structures and say, hey look windows is much worse, because although on the surface it is made to look simple it is actually very complicated. Fair point but comparing is a very dubious way of proving something is good (just look at the Mac v PC ads!) 

I am a linux user so clearly I find it superior and more user friendly than windows. But what I like about windows is how there is a Windows folder, which for all intents and purposes I can ALWAYS stay away from. No need to edit anything there or delete anything, as 99% of the time it will break my system. I know it is relatively safe to mess around with anything else I want. That is kind of the functionality I am leaning towards. For example there are about 4 different bin and opt folders in various directories and sub-directories. I know bin files are important but in which folders are they say relatively unimportant. Again these issues become a little confusing.

---

### Post by cardinals_fan on 2008-06-10
Read [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by abhiroopb on 2008-06-10
Case in point (age of the article):

Copyright © 1994-2004 Daniel Quinlan

Copyright © 2001-2004 Paul 'Rusty' Russell

Copyright © 2003-2004 Christopher Yeoh

---

### Post by cardinals_fan on 2008-06-10
> **abhiroopb said:**
> Case in point (age of the article):

Copyright © 1994-2004 Daniel Quinlan

Copyright © 2001-2004 Paul 'Rusty' Russell

Copyright © 2003-2004 Christopher Yeoh
So?

---

### Post by abhiroopb on 2008-06-10
Well one of the points I was making is that this is a very old file system that essentially has evolved but not significantly changed to accommodate newer hardware.

---

### Post by John.Michael.Kane on 2008-06-10
> **abhiroopb said:**
> Well one of the points I was making is that this is a very old file system that essentially has evolved but not significantly changed to accommodate newer hardware.

The file structure is not going to change, unless.

1) You make a valid point for it to be changed, and bring said point to the developers of the file system/structure.

2) You Re-write the file system/structure yourself to work how you want.

It seems you are failing to understand that those who work with, and built the file structure in question do not see it as broken, and if they did they would have most likely fixed it a long time ago being you are talking about a system/structure over 30 years old.

Another point is that you would get the same file structure for the most part if you was running a windows desktop or a windows server. Windows does not offer two types of file systems/structure, Which it seems is what you are seeking.

At the end of the day. The notion that a desktop user should have a desktop type file system vs what has been the norm for UNIX/Linux etc for over 30+ years is going to be a hard sell.

---

### Post by cardinals_fan on 2008-06-10
> **abhiroopb said:**
> Well one of the points I was making is that this is a very old file system that essentially has evolved but not significantly changed to accommodate newer hardware.
That article is very helpful in explaining why things are placed where they are in the filesystem.  I find the UNIX filesystem very helpful because I can always find what I'm looking for.

---

### Post by phrostbyte on 2008-06-10
> **abhiroopb said:**
> But thats what I'm saying. I'm no expert but wasn't Unix written for computers that were vastly inferior to what we are using today? I mean perhaps the way it was structured was so as to conserve space.

You are right. One reason directory names in Unix are so small is typing huge amounts of text on a teletype was cumbersome, so that is why we have /etc /dev instead of /Configuration or /Devices

:(

Mac OS X has in interesting solution to this problem, remember OS X is Unix so it still retains the standard Unix file system hierarchy. It just hides it from people who aren't explicitly looking for it.

---

### Post by cardinals_fan on 2008-06-10
> **phrostbyte said:**
> You are right. One reason directory names in Unix are so small is typing huge amounts of text on a teletype was cumbersome, so that is why we have /etc /dev instead of /Configuration or /Devices

:(
I do most of my file management through the command line.  Capitalized and lengthy folder names are a pain in the neck to type, even with tab completion.

---

### Post by Polygon on 2008-06-10
but hardware is handled at the kernel level, it has nothing to do with the filesystem.

---

### Post by saulgoode on 2008-06-10
> **smartboyathome said:**
> I think that the file system structure *could* use an update. I think that having one folder for one application can lead to the potetional to be able to install packages from source/rpm/etc and then be able to detect it in the package manager with a remove option. It could be done with the Gobohide patch + userland app. Of course, like in everything, there are conservatives which don't like this, and like all new ideas, it isn't precieved well. That is why the users have to impliment it before it is adopted.

[http://savannah.gnu.org/projects/stow]("http://savannah.gnu.org/projects/stow")

---

### Post by smartboyathome on 2008-06-11
> **cardinals_fan said:**
> I do most of my file management through the command line.  Capitalized and lengthy folder names are a pain in the neck to type, even with tab completion.

Though Ubuntu isn't aiming to use the command line, it is aiming to get rid of the need to use the command line. So this argument isn't valid imo.

> **saulgoode said:**
> [http://savannah.gnu.org/projects/stow]("http://savannah.gnu.org/projects/stow")

Not what I meant, they should actually be organized, not made to look like they are organized.

---

### Post by inportb on 2008-06-11
> **abhiroopb said:**
> Mind you I'm not expert, I've never even compiled a kernel, but I have used linux and these are some of the problems I have found.

1. Lets say I install a program, if I do it with APT, or install a .deb package usually uninstalling it is a simple case of using apt-get or synaptic. However, when I compile a program from source (which is required by a lot of programs). I am left with a plethora of files spread out all over my hard drive. Why is this? Wouldn't it make more sense to have them all in one folder like in windows?

Are you saying that this does not happen when you compile programs from sources on Windows?

---

### Post by abhiroopb on 2008-06-11
I have never EVER had to compile a program from source in windows, however, it is a very frequent feature in ubuntu. I don't mind but I would like to not have files spread out like that.

I think the problem is that while its true that the current system works, I think users are thinking along the lines of if it ain't broke don't fix it. Fair enough.

But look at it this way. The file system is clearly old, everyone here agrees about that. Lets say you were using a computer for years with windows. To be honest it gets everything done, and it does everything pretty well. Major downsides are viruses, etc. Lets not get into that, for all intents and purposes XP is a decent operating system, that certainly has more market share than Linux. Now if you were told that there is something out there potentially better, and more stable what would you say? Most people will stick to windows, and I can see a lot of head shaking but I'm sure most ubuntu users at some point were converted and until they were converted they saw that XP was flawed yet used it simply because they were used to it. The same thing I think is happening here, agreed the system works, agreed it is a good standard. But there is potential for it to be better, and that is all I am trying to say. A number of reasons why the system is the way it is is to incorporate legacy systems, something which in my mind seems flawed.

---

### Post by inportb on 2008-06-11
> **abhiroopb said:**
> I have never EVER had to compile a program from source in windows, however, it is a very frequent feature in ubuntu. I don't mind but I would like to not have files spread out like that.

Like what? I like to keep my sources in their own directories, and I haven't had trouble with neatness. And from experience, it's exactly the same on Windows.

Building from source is a "frequent feature" of Ubuntu because the culture encourages hacking code. One can as frequently and as easily compile stuff on Windows.

---

### Post by cardinals_fan on 2008-06-11
> **smartboyathome said:**
> Though Ubuntu isn't aiming to use the command line, it is aiming to get rid of the need to use the command line. So this argument isn't valid imo.

Can Ubuntu change the file structure itself?  :popcorn:

---

### Post by stchman on 2008-06-11
If you never build apps from source then the file system organization is irrelevant.

I am only concerned with a few directories.

/home
/opt
/var
/usr
/etc

I do agree that there should be a universal standard in which applications are built.  It would also be nice to have apt log the apps built so that they may be un-installed via Synaptic.

---

### Post by NTolerance on 2008-06-11
> **cardinals_fan said:**
> I do most of my file management through the command line.  Capitalized and lengthy folder names are a pain in the neck to type, even with tab completion.

I really like the concept of no caps and no spaces in the filesystem.  So many things break in Windows due to the spaces in "Documents and Settings" and "Program Files".

---

### Post by smartboyathome on 2008-06-11
> **cardinals_fan said:**
> Can Ubuntu change the file structure itself?

Sure it can. Just use the Gobohide patches + user time app to hide the symlinks to the old file structure.  :popcorn:

---

### Post by cardinals_fan on 2008-06-11
> **smartboyathome said:**
> Sure it can. Just use the Gobohide patches + user time app to hide the symlinks to the old file structure.  :popcorn:
I was thinking of Gobo when I posted that ;)

Hiding the real structure is OK with me.  I use Slackware anyway, and if it makes Ubuntu friendlier for new users, so be it :)

---

### Post by ad_267 on 2008-06-11
> **Polygon said:**
> but hardware is handled at the kernel level, it has nothing to do with the filesystem.

Have you had a look in /dev or /sys recently?

I personally think the file structure makes a lot of sense after using Linux for only a short time. A lot of people have already posted very valid reasons for why it is the way it is and why it is good to keep it that way.

---

### Post by bomanizer on 2008-06-13
I'm with those people, who say that the normal user should only "see", for example, /home and /media.

Knowledge beyond that is pointless for a desktop user, who is not installing apps or maintaining the system. That's for the admin to worry about.

The situation is of course completely different if those above mentioned persons are the one and the same :) ...like most of us here.

That's what you get when you have basically the same system design used as a desktop and as a server.

---

### Post by Inferied on 2008-06-14
A /programs folder would be awesome... Imagine being able to delete xorg with one click. xD

---

### Post by abhiroopb on 2008-06-14
If you're being sarcastic: you can delete the xorg.conf anyway! and you can do rm -rf / at any point!

---

### Post by magnus0 on 2008-06-17
> **abhiroopb said:**
> 
**/programs** - any time a new program is installed, either from source, apt, or as a .deb package it should come here. No questions asked ALL the files are placed here. If this is deleted the program is basically wiped clean from the system. users can mess around with this as deleting one program may not harm the system. Although I guess dependencies is a problem, however, I am not totally sure how that is looked after now, so I will leave that to discussions from more experienced users.

**/system** - everything that is installed when the OS is FIRST installed. Most (if not ALL) users can stay away from this, except to edit the occasional menu.lst, etc.

And thats it!


It would be well organized. I think it they should put this into Ibex!

What I think should be:

/system - all system file

/programs - all packages, that are installed. this should include programs from source code too.

/username - documents, music, pictures etc.

/media - removable drives etc.

---

### Post by Tom Mann on 2008-06-17
Why would we change something that's not broken - Linux takes pride in being able to pick up a new version and not have to learn where everything else again - a situation a lot of home owners and businesses are suffering with XP/Vista at the moment. Have heart that once you've learned it once you'll never have to do it again :KS

---

### Post by odiseo77 on 2008-06-17
I'm happy and comfortable with the way the Linux file structure is, although I must admit I don't completely understand it. I have a vague idea of what are directories like /proc or /var -well, I know /proc has something to do with processes and hardware, and /var with variable files, etc., but since I don't use them too much, I'm not very familiar with their purpose. However, as far as my knowledge about the Linux file system structure goes, I'm comfortable with the way things are, as I said before (I mean, what I know about it serves to my needs and purposes).

I don't know if this distro has been mentioned here (probably it has), but for those looking for an alternative file system structure, [GoboLinux]("http://www.gobolinux.org/") might be interesting (as for me, I haven't used it, but I don't feel comfortable with this "/Programs" directory thing; it just reminds me too much of PC-BSD and Windows, which I don't like).

---

### Post by abhiroopb on 2008-06-17
I agree with the theory that if it ain't broke don't fix it, but as odiseo points out the reason /Programs seems like a bad idea is becauase it reminds him too much off Windows. Is that really a fair argument? I mean sure Windows has flaws, numerous flaws, but at the same time its dominating marketshare, clearly they must be doing something right.

---

### Post by ad_267 on 2008-06-17
> **abhiroopb said:**
> I agree with the theory that if it ain't broke don't fix it, but as odiseo points out the reason /Programs seems like a bad idea is becauase it reminds him too much off Windows. Is that really a fair argument? I mean sure Windows has flaws, numerous flaws, but at the same time its dominating marketshare, clearly they must be doing something right.

I think what they are doing right is their business and marketing, not the actual software. And a /programs doesn't really fit in at all with how the Linux file structure works. The /usr directory or /usr/local is probably closest to a /programs directory.

---

### Post by savagenator on 2008-06-17
has
[http://www.gobolinux.org/](http://www.gobolinux.org/)
been said yet? if not, its basically exactly what the OP had wanted...

---

### Post by odiseo77 on 2008-06-17
> **abhiroopb said:**
> I agree with the theory that if it ain't broke don't fix it, but as odiseo points out the reason /Programs seems like a bad idea is becauase it reminds him too much off Windows. Is that really a fair argument? I mean sure Windows has flaws, numerous flaws, but at the same time its dominating marketshare, clearly they must be doing something right.

Well, on one hand, I simply don't feel comfortable with it (I've been using Linux almost exclusively for years), and on the other hand, suppose you have to compile and install some software that is not available for GoboLinux; in this case it would probably create a /usr/bin directory -in case it's not there- so, some binaries would be inside /Programs, and others would be inside /usr/bin, so, IMO, it would be a complete mess and confusion (although, since I haven't used GoboLinux, I don't know if it has a way of handling these situations, and how).

---

### Post by savagenator on 2008-06-17
i think people are taking this too far. Gobolinux simply keeps everything in seperate files. I dont user it, but it can be useful for very Mac-like usage: delete a program by dragging its file into the trash, whole folder dissapears. 

so in a way, its more intuitive, but there may be security flaws in it too (can't think of any though) and performance decrease (dont see any evidence for this though)

---

### Post by richrock on 2008-06-18
Can you actually 'accidentaly' delete one of these core folders?  Unless you are logged in as root (a VERY BAD IDEA) then I would say no.  (Mind you, I've not tried this).  This thread seems to have missed the very core of it's files/folder structures, and that is permissions.  Surely these permissions allow you some protection over the folders and whatever their purpose is.  I could go onto my windows box at work and delete a couple of core dll's without anything more than a 'Are you sure?', yet in linux (and unix) I would be scolded and told 'You must be root' or 'You must have administrator privileges'.

To me, the file structures of both XP and Linux are clear and methodical.  No need for change.  Surely the linux model is optimised for speed of access, as everything is exactly where it should be.

my tuppence worth.

Rich

---

### Post by oasmar1 on 2008-06-20
abhiroopb, I think you are right, I think the reason that they do not want to do it is because it would be too similar to windows, even though it would probably be better.
It seems that this "ego" thing is holding back Linux. Another example is that because Windows and Mac have both used a metallic/glass styled theme Linux should not use one. 
I think more of the advanced Linux users take pride in knowing that they are different to everyone else.

---

### Post by joninkrakow on 2008-06-20
> **oasmar1 said:**
> abhiroopb, I think you are right, I think the reason that they do not want to do it is because it would be too similar to windows, even though it would probably be better.
It seems that this "ego" thing is holding back Linux. Another example is that because Windows and Mac have both used a metallic/glass styled theme Linux should not use one. 
I think more of the advanced Linux users take pride in knowing that they are different to everyone else.

I think that's being a bit harsh. I'm a big Mac fan (cut me and I bleed 6 colors--I go that far back, and then some), and I've come to be a fan of Linux, but I've never liked the Windows folder/directory structure. It is not logical. It has one "benefit" over *nix, namely that there is a top-level folder "Windows" or whatever it's called today, under which all the mess exists. Linux puts it on the top level, and doesn't hide it. How's that worse? The *nix directory structure is organized and logical--even if you or someone else doesn't understand that logic. Sure, there are other ways of doing things, but then, there are tradeoffs. On the Mac, for instance, each app can grow to hundreds of megabytes, containing redundant files. On Windows, and Linux, dependencies can be shared, but also broken. Take your pick. 

In other words, if Linux were to change, it would only be for one reason--simply to imitate another system's way of doing things, not because it would dramatically improve how it works. Since such is the case, it makes no sense to make these changes--at least to me--as it done, simply to be the "same" rather than for any real benefits. That's how I sees it.

-Jon

---

### Post by starcannon on 2008-06-20
A beautiful thing about linux is, that if you don't like the way something is, you have every tool required to make it your own.

You could feasibly rename everything in the file system to "make sense", pretty much might require building a distro from the ground up, but its definitely possible.

One could also do a little linking if its strictly a cosmetic condition, build a link to /bin and name the link /Programs.

I'm also uncertain where the idea that windows doesn't spread files everywhere came from, but all said and done programs and operating systems do things in similar ways across all platforms, commonly used library files are stored where other programs that may need them can find them, increasing performance and minimizing space. Don't need glibc to exist in every folder of ever program that would use it, so it lives in a folder that anything that needs it can call on to get it. Uninstalling again not so rough, and in my opinion Linux is the easiest to uninstall, most programs packaged, blobbed, or compiled have an uninstaller of some sort, once thats done, its uninstalled, unlike windows where after you uninstall the program you then have to comb through directories and registries to clean out all the junk that gets left behind.

Anyway, I'd say give the Linux file structure a chance, spend some time looking through it, get a feel for it, and in no time you may find your self asking why anyone would do it any other way, worked for me.

Just my 2cents on the subject, and at the rate of inflation I probably owe someone an apology.

---

### Post by aysiu on 2008-06-20
> **starcannon said:**
> 
I'm also uncertain where the idea that windows doesn't spread files everywhere came from It gives you that illusion, anyway. I still remember years ago, when I knew very little about computers, I thought I could just copy the C:\Program Files\*nameofprogram* folder from one computer to another computer and keep the program without reinstalling it. Didn't work, of course. There are registry settings and .dlls everywhere.

---

### Post by smartboyathome on 2008-06-22
With Gobolinux, you actually could, but IMO there are other problems I have with it which make me repulsed by it. Right now I am trying to get my Arch Linux tricked out with Gobohide so that I can get everything the way I want it. Good thing I *did* install Gobolinux, it gave me its file system as a template. :D

---

### Post by abhiroopb on 2008-07-17
This article on DIGG.com has had a lot of discussion about windows/linux file systems, some of the points (from both sides) are interesting:

[http://digg.com/linux_unix/Windows_Now_Open_Source](http://digg.com/linux_unix/Windows_Now_Open_Source)

---

### Post by worksofcraft on 2010-08-01
Personally I think Windows file system is an abominable mess and the Unix FSH a well thought out and logically intelligent design.

My first gripe about Windows is that they fail to grasp the importance of separating read-only from read-write branches in their file hyrarchy.

Now if ALL your programs and executables were on read only drives (except when deliberately installing or upgrading), then you would be safe from viruses, you would probably never have to defragment and you could even run directly from read only media.

I agree that things like /mnt and /media could be merged but there are so many other things wrong with the Microsoft way... I fail to see how it could inspire any kind of reorganization :shock:

---

### Post by cariboo on 2010-08-01
@worksofcraft

Check the date of the post above yours. I don't think there is really any need to bring a 2 year old thread back to life. Closed.

---

