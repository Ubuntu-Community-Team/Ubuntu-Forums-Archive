---
title: "Noob here - System files help."
date: 2012-03-20
forum: New to Ubuntu
---

### Post by ec8civic on 2012-03-20
Guys, 

I need some help with the mayor system files of ubuntu where they reside and what do they do. I can seem to track the info anywhere around. 

Thanks in advance,

EC8.

---

### Post by lechien73 on 2012-03-20
Hi and welcome to the forums,

Your question is a bit broad, so I'll try break it down. If you need more information, feel free to ask :)

1. Boot files

Ubuntu uses files in the /boot directory to boot up, as well as the system image files initrd.img and vmlinuz in the root directory.

2. Configuration files

Most critical config files reside in the /etc directory. Some of the more important ones would be in /etc/init.d/, which are startup scripts.

3. System utilities

Many of the executable system utilities (such as fdisk, fsck etc.) live in /sbin

I hope this helps :)

---

### Post by ec8civic on 2012-03-20
lechien that is definitely the right direction.

So as boot files go is it only these 2 that are required?

And for the config files, startup scripts to load what data?

Understand i might be vague but thats probably due to me not knowing what i want exactly :lolflag:

---

### Post by MG&amp;TL on 2012-03-20
[http://linuxcommand.org/lts0040.php](http://linuxcommand.org/lts0040.php)

Is quite helpful. /etc/init.d/ and upstart load stuff that's needed for other stuff and prepare things.

---

### Post by ec8civic on 2012-03-20
thats quite helpfull thanks guys.

I still cant understand whats exactly the difference between vmlinuz and initrd.img. 

Since to my understanding these are boot kernel image files, or am i incorrect?

---

### Post by JKyleOKC on 2012-03-20
> **ec8civic said:**
> I still cant understand whats exactly the difference between vmlinuz and initrd.img. 

Since to my understanding these are boot kernel image files, or am i incorrect?Here's an abbreviated version of what happens when you turn the power on after the machine has been shut down for a while:

First, code in the BIOS chip on the motherboard gets loaded into memory automatically and begins running. Next, the Power-On Self Test (POST) code checks all of the hardware to make certain it's working. In the process it clears all of the RAM space except the very small part it's using to run the POST.

When the POST completes, the BIOS code then begins loading the operating system code into memory. This becomes a "chicken-or-egg" situation, since loading the code requires code to already be there and the BIOS chip isn't large enough to hold all of the necessary code. The solution, in most Linux distributions, is to create a pseudo-disk in RAM, and load it with an abbreviated copy of the system that has all the things needed to load the full system, but nothing else (such as a normal user interface or keyboard drivers). That abbreviated copy is the "initrd.img" file, the INITial RamDisk IMaGe. Once it's loaded, control goes over to it, and it begins loading the actual full system from the "vmlinuz" file. While all this is going on, you see only the splash screen (but you can edit GRUB's actions to see play-by-play reports of it all, if you want to).

When the full system is all loaded, control goes to the "init" process, which sets up the console and virtual terminals, loads the window manager and display code, and lets you log in. The init process continues to run in the background until you shut down the machine, allowing the system to do its work more or less invisibly.

You can view the log of all this by firing up a text editor and looking at /var/log/syslog. This file records each significant event -- and gets huge in a hurry.

I hope this helps answer your question, but it will probably prompt many more. Welcome to this wild and wonderful world!

---

### Post by ec8civic on 2012-03-20
Kyle thats awesome. Very nice explanation and indeed very helpful. Definitely more questions will pop up lol.

Thanks for taking the time m8.

---

### Post by matt_symes on 2012-03-20
Hi

If you want to know where a packages files are installed you can use this

```
dpkg -L <package_name>
```

Here's an example.

```
matthew@matthew-Aspire-7540:~$ dpkg -L htop
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/htop
/usr/share/doc/htop/AUTHORS
/usr/share/doc/htop/copyright
/usr/share/doc/htop/README
/usr/share/doc/htop/changelog.Debian.gz
/usr/share/pixmaps
/usr/share/pixmaps/htop.png
/usr/share/menu
/usr/share/menu/htop
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/htop.1.gz
/usr/share/applications
/usr/share/applications/htop.desktop
/usr/bin
/usr/bin/htop
matthew@matthew-Aspire-7540:~$ 
```

You can see where an installed packages files are in the filling system.

Kind regards

---

### Post by mal1958 on 2012-03-20
Welcome to the forum.
  While this post has nothing to do with your prob, I thought to let you know a couple of things.

 1.  The term Noob, in most forum enviorns is an insult to one.  Meaning more of a new person and unwilling to learn, or pest, or ignorant new person.  The better term to use, especially toward yourself, is Newbie. That has more positive conotations to it and is not an insulting term.

 2.  When you do log on and ask for help, give us as much detail as possible.  If you are having a prob with your hardware and Ubuntu, then include all system specs in your post.  Trust me, that info will help 'us' help you.  the info should also include the flavor of Ubuntu you are using and the version of it.  As I don't think that a possible solution for a problem in Version 8.10 would be helpful to version 10.04.

 3. When you have found the answer to your inquiry, to to your post, use the "thread Tools" in the upper right of the message screen and mark your post solved.  That helps all of the people who may have a similar prob (with similar stats) find the post easier and maybe get their system up a lot faster.

   Again, I say welcome to the forum, and to the finest distro of Linux I know of.

---

### Post by ec8civic on 2012-03-21
matt_ noted with thanks, although I don't feel confident going through the terminal at this point, im still verifying if the Ubuntu has really become that easy to use. At this point im still finding it difficult especially to get software installed (ie. not that easy)

mal1958: i dont have a specific problem, its more of getting to know the innards more than a problem.

Noted re noob.

---

### Post by Rodney9 on 2012-03-21
Guide to Ubuntu Oneiric version 11.10

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

The Software Centre is the easiest way to install software

[http://www.ubuntu.com/ubuntu/feature...oftware-centre](http://www.ubuntu.com/ubuntu/feature...oftware-centre)

Linux is Not Windows

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Free PDF book on Linux Commands

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Rodney
_________

---

### Post by JKyleOKC on 2012-03-21
> **ec8civic said:**
> im still verifying if the Ubuntu has really become that easy to use. At this point im still finding it difficult especially to get software installed (ie. not that easy).Something I don't think anyone has pointed out to you yet: Most of the generic "how to use Linux" books and articles you'll find describe the SysV variant made popular by the Red Hat distribution and others based on Red Hat, while Ubuntu is based on the Debian distribution. The Debian distribution differs greatly from the Red Hat version in many respects.

The result is that quite a bit of information you'll come across is incorrect for Debian-based systems. One of these major differences is the installation of software!

Both systems use "packages" but the package formats are somewhat different. Our packages normally come as files with names ending in ".deb" while the other package files usually end in ".rpm" (Redhat Package Manager). You'll also find references to compiling programs from source files; while it can be done, it can also become complicated. Packages that you find through the Software Center or through Synaptic have already been optimized for Ubuntu. Those that you compile from source are untested and can give you problems ranging from needing small tweaks up to causing major system damage, so it's best to avoid doing so until you've gotten lots of experience and can troubleshoot any problems that arise.

Another point of difference is the startup process. Both Red Hat and Debian originally used a sequence developed at Berkeley which loaded the system from disk sequentially, and determined the sequence stages by "runlevels." However the sequences differ; older books will tell you that the graphic windows are at runlevel 5 and the command line at runlevel 3. This is true in the Red Hat version, but for Debian (and thus for us) everything is at runlevel 2. I see questions about this quite frequently!

It's not very meaningful any more, in any event, because the Berkeley sequence is being replaced by a different technique called Upstart, which allows faster booting and overcomes several problems inherent in the original approach. This is just a "heads up" to let you know there's a lot of information out there which may be obsolete and in many cases does not apply to Ubuntu installations.

For most folk, the various flavors of Ubuntu really are that easy to use. You will see many messages here from people who are running into problems, but you'll also see that many of those problems are due to the amount of incorrect information floating around and only a few are really serious. Don't be afraid to ask here; we'll give you all the help that we can!

---

### Post by mal1958 on 2012-03-21
> **ec8civic said:**
> 
mal1958: i dont have a specific problem, its more of getting to know the innards more than a problem.
Noted re noob.

That's OK just wanted to let you know for future reference.  And believe me, there will be future times here :lolflag:  But all in all, the Ubuntu system is the best I have run into, and the community is the friendliest there is...

---

### Post by ec8civic on 2012-03-22
Wow guys i must say i am truly surprised by the amount of support i am receiving.

Re .deb vs .rpm - i have already encountered this and wasn't sure what to make of it to say the truth, glad u shed some light there.

wow i just realised that my installation problems where due to .rpm vs .deb vs tgz. downloaded .deb and its as easy a 1.2.3. through the software centre.

Once again a super thanks to all of ya.

edit: lol not realy 1.2.3 i did manage to run the installer for the splunk (its a network diagnostic tool splunkdotcom) but i have no clue how to start the software, its not like an icon is created on the desktop as in Win lol.

edit 2: got the thing running, error but its prolly from the app side from my understanding.

---

### Post by JKyleOKC on 2012-03-22
I'm not familiar with splunk, but you can open a Terminal window and type the command "which splunk" to find out the full path to the program, and then type in that full path as a command to launch it. The "which" command does a search for the command named as its argument, and if found, reports its full path. If not found, nothing is reported, not even an error message.

One major, and often puzzling, difference between Linux and Windows lies in the way they locate executable files. In Windows, the system searches for the program first in the current folder, and uses the PATH environment variable only if it's not found in the current folder. However, Linux looks first exactly where you tell it in the command; if you don't specify a full path, it will search the directories listed in PATH, but never will look in the current one (unless it's one of those listed in PATH). To run a file in the current directory you have to prefix its name with "./" to make the system look "here" rather than in PATH.

This is part of the security improvement; it makes it a bit more difficult for malware to get executed after it invades your system, since most of the directories listed in PATH require "root" access to write anything into them. It's not foolproof, since you can edit PATH to add a non-system directory to it, but every little bit helps...

If you post the full response of "splunk" here, we may be able to offer some hints of what is going wrong. And if you tell us what it's supposed to do, we may be able to suggest something from the Software Centre that does the same things.

---

### Post by ec8civic on 2012-03-22
i had actually already managed to get through the problem, needed further rights, used the sudo.

im getting a hang of this :)

Once again kyle a super thanks for time dedicated.

ow btw this 'splunk' thing is a network diagnostics utility.

---

### Post by nothingspecial on 2012-03-22
Some excellent stuff in this thread :D

:popcorn:

---

### Post by JKyleOKC on 2012-03-22
> **ec8civic said:**
> i had actually already managed to get through the problem, needed further rights, used the sudo.

im getting a hang of this :)

Once again kyle a super thanks for time dedicated.

ow btw this 'splunk' thing is a network diagnostics utility.Getting direct raw access to the network cards/interfaces requires root access via sudo. I have to do that when running wireshark to diagnose my network problems. So far, the combination of ping and wireshark have sufficed to do all my network troubleshooting, together with searching the forums for guides to help in a few cases.

---

### Post by mal1958 on 2012-03-23
@ ec8civic:

The support and help that surprised you so much is the key of this system.  And you will find as you learn about Ubuntu, and/or any other flavor or distro, that you will have a drive and will to share your knowledge and experience to help the 'next' generation of users.  That is what fueled the whole movement from word one.  and that is why a community driven OS will, eventually, out perform any corporate driven one.  Bugs are killed quicker, problems solved faster, and the knowledge is passed on.  Where'as the Corporate driven ones must go through a committee, then coders work on a fix and test it, then, maybe, it is released as a patch.  Again, I say welcome to the community and ask all the questions you want.  It is how we learn.

---

