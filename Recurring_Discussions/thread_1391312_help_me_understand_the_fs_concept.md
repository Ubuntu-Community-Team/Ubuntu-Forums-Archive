---
title: "help me understand the fs concept"
date: 2010-01-26
forum: Recurring Discussions
---

### Post by degarb on 2010-01-26
The file system in windows can be summed up:

my computer> drives> windows dir + Program files + docs and settings

One paragraph.

Can anyone sum up the linux file system in a paragraph?  Makes no sense.

I cannot find anything.  No a single program with a browser.

---

### Post by hhlp on 2010-01-26
gnome menu + places + personal folder + (open nautilus) in the left your folder in the right your disk

---

### Post by adam814 on 2010-01-26
Applications are usually installed in /usr/bin or /usr/local/bin.  Games are sometimes installed in /usr/games.  Crucial system utilities are installed in /bin (since /usr may be a separate partition, but /bin traditionally isn't).  Programs that usually need to run as root are installed in /sbin or /usr/sbin.

All of those directories and more are likely in your $PATH, so if you're looking for a specific program you've installed you could do this:
```
which ps
```This would tell you the location of the executable for ps your shell would use.

---

### Post by J V on 2010-01-26
In one paragraph?

everything starts at / Other partitions can be mounted in folders, so your HDs are probably at /mnt/drivename  /home is probably the only place you need to know about, where all your settings etc are kept, and /tmp is very usefull for downloading flash videos etc...

---

### Post by oldos2er on 2010-01-26
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by bodhi.zazen on 2010-01-26
[IMG]http://geniushackers.com/blog/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/IMG]

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by beany1 on 2010-01-26
> **degarb said:**
> The file system in windows can be summed up:

my computer> drives> windows dir + Program files + docs and settings

One paragraph.

Can anyone sum up the linux file system in a paragraph?  Makes no sense.

I cannot find anything.  No a single program with a browser.

Gotta agree! wtf? its like confusing, and then the different linux setups, like the post above saying stuff is mounted from /mnt/hddname, erm, nope not on myn its /media/hddname,  lol we need a simple explanation of the file system, please, as the guides on linux fs, require a degree, and a brain

---

### Post by theozzlives on 2010-01-26
Windows is not easy. It installs crap all through your system & registry! If you've been using your computer long enough, you could have garbage from 10 years ago from programs that are long since gone!

---

### Post by beany1 on 2010-01-26
ergh, trust me to shout out just after a great post, cheers bodhi.zazen, awesome find!

---

### Post by degarb on 2010-01-26
> **theozzlives said:**
> Windows is not easy. It installs crap all through your system & registry! If you've been using your computer long enough, you could have garbage from 10 years ago from programs that are long since gone!


I half agree.  I always find programs that rely on ini files rather than registry or doc and settings.   ini files should be piped into the exe via the command line, depending on shortcut.  So profiles can be done without docs and setting or registry.  I love the programs that have withstood test of time like xnews that simply work, no matter what version of windows.

I was saddened to find that linux requires installers and you cant just download a zip and extract it to any drive and run.

What I was horrified to learn was vector linux was said to require reinstall of all your programs on upgrade.  I have no idea of partitions in ubuntu, right now, since this seems pretty well hidden.

Now, with such a restrictive file system,  how does one take advantage of adding a second hard drive to move out the swap file, i mean partition, and many of the installed programs?

---

### Post by adam814 on 2010-01-26
Would you really prefer a Linux from tarball like that?  The point of an installer is so that you can configure your system how you want it.  Not everyone has the same space requirements or wants all the same apps or partitioning layout.

I'm not all that familiar with VectorLinux.  From what I can see on their website it seems like it's intended for people who want to more or less build their own system from a minimal install.  As such it may not be geared for user-friendliness.  You might be better off with a distro that is rather than going through an upgrade followed by manually re-installing everything.

I'm not sure what you mean by a restrictive file system.  The FHS is a suggestion, nobody's enforcing it on your machine if you'd rather do it another way.  It's just how things are conventionally done to keep admins sane.

---

### Post by audiomick on 2010-01-26
I find the linux file system as simple as it could possibly be. The post from bohdi.zazen is great. One should recognise the difference between the principle and the "way things are done".

The principle is, it is like a tree or a pyramid. There is a folder at the base (peak). That is /. Inside that, there are other folders. Inside them there are more folders, and so on. And that is really all there is to it.

The "way things are done" is that conventions have developed that in the first level below / there are certain folders, and certain things are put in each of them. Learning what is where requires a certain amount of effort, sure, but that applies to any concept.

You can in fact mount a partition anywhere you like in the file system; once again, there are conventions about where automatic functions do this.

@degarb: you can in fact put an executable program anywhere you like in a linux file system and run it from there. All you have to do is start it with the path and the name of the program. The simplest example is a script as a .txt file which is marked in  the permissions of the file as executable. 
Enter
```
/path/to/file nameofthefile
```
in a terminal, and it will run, no matter where it is.

The installer, by which I assume you mean apt/synaptic simply knows where the programs are kept by convention, takes care of dependencies, and makes sure that the systems update mechanismus knows that the program is there and needs updating when an update is to be had.

---

### Post by oldos2er on 2010-01-26
> **degarb said:**
> I was saddened to find that linux requires installers and you cant just download a zip and extract it to any drive and run.

You can install software this way if you prefer, and if the apps you want are packaged as ready-to-run binaries. Some apps e.g. Flock, Thunderbird, and Firefox are available in this form. But using Ubuntu's package manager to install and keep apps up-to-date is much easier to deal with, in my opinion.

Vector Linux is a dumbed-down (if you'll forgive the expression) version of Slackware. It's been awhile since I ran it, but I don't recall the limitation you mentioned.

You have the freedom to use the package manager, run ready-to-run binaries, or compile source code--or mix and match all of the above. I don't see how this is restrictive or what it has to do with the file system, or partitions.

---

### Post by 3rdalbum on 2010-01-26
What really does any casual user need to know about the filesystem? Devices are mounted in /media. Your home directory is in a subfolder in /home. Temporary files are in /tmp. Network shares that you mount in Gnome are mounted in ".gvfs" in your home directory. Programs can be run by typing their name.

---

### Post by cascade9 on 2010-01-26
Nice pic bodhi.zazen. Useful, saved, thanks ;) 

> **degarb said:**
> The file system in windows can be summed up:

my computer> drives> windows dir + Program files + docs and settings

One paragraph.

Can anyone sum up the linux file system in a paragraph?  Makes no sense.


Thats a convention, not a hard fact. You can install program files onto a different drive to the windows drive (I know of several people are using C: for windows, but  install everything to D:  ). Docs and settings can be on a different drive to windows or the program installation drive. 

The linux file system makes much more sense IMO. Even if it does have some confusion about where, exactly, you should mount the 'extra' partitions past /root and /home.

---

