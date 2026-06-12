---
title: "Still don't get the point of sudo"
date: 2010-05-31
forum: Recurring Discussions
---

### Post by rather on 2010-05-31
I installed Ubuntu (lucid) today and so far it's been an excellent experience. Installing stuff is a breeze with Synaptic or apt-get in Terminal. And after going through loads of (really) crap Music players, I finally found something reminiscent of Winamp (Qmmp). It's fast and the learning curve is not big at all. However, I realised things were a bit of a drag when working with things in the filesystem.

For example, I installed something I pretty much immediately decided I didn't like. It had gone in /usr/lib (which seems like the equivalent of Windows' "Program Files" - is that right?) but I wasn't able to shift-delete it (rather than send to trash). The solutions seemed to me to be:

- sudo nautilus /usr/lib and then shift-delete the dir
- sudo rm -r /usr/lib/<the_directory>

The same again happened when I wanted to edit a really unimportant file for Qmmp in gedit, but was only able to open it read-only (because it's in /usr/lib). Again, I had to open a Terminal, then do sudo gedit <path_to_file>, and only then was I able to make changes and save them. How would I have been able to do this without Terminal, just using the GUI?

Considering that Linux is supposed to give a user more control over the operating system, this is a bit of a drag. In Windows there is no such thing and doing shift-delete on things will not stop you from deleting things. I can appreciate the need to go via sudo if I was editing terribly important things, like the fstab file, but surely not a few files related to a simple program like Qmmp.

I'm not whining here, more wanting to find an explanation for this apparent restrictiveness (Windows is supposed to be the nanny-state OS). Anything beyond the simplest things requires having to open Terminal and typing something prefixed with sudo!

I also don't get how sudo gives me temporary access as root, if the password sudo asks me to type in is MY password (I've read that the root doesn't have one). Seems pretty contradictory.

Any explanations are most gratefully received.

---

### Post by Dayofswords on 2010-05-31
Bob logged in as root(if this were defualt):
Bob is looking at his filesystem, it's odd, no C:. crazy things
bob is thirsty, he goes off to get a soda. jake, age 4 comes to the computer and starts playing with the key board and mouse.

smash, bang
hit, click.

bob comes back an notices the windows showing "/" is blank. he swears there were things, but he goes on his way.... but wait, where the programs in his application menu, what's this weird box that popped up with boxes instead of text. the computer just froze!!

Bob is screwed.





Bob logged in as a user with sudo(if this were defualt):
Bob is looking at his filesystem, it's odd, no C:. crazy things
bob is thirsty, he goes off to get a soda. jake, age 4 comes to the computer and starts playing with the key board and mouse.

smash, bang
hit, click.

bob comes back and noticed his window had moved somewhat and there is a permission error. wonder what happened, he closes it and thinks nothing more of it. he opens firefox and notices that in the news a local woman has found an old mining shaft, wow he thinks, could be gold or something.

bob is fine.

---

### Post by CharlesA on 2010-05-31
Package managers are your friends.

You don't just *delete* a directory that was created when a package was installed, you remove that package if you aren't using it any more.

+1 to dayofswords.

---

### Post by rather on 2010-05-31
But it wasn't a package. It was an equaliser plugin for Rhythmbox, which was already installed. This plugin doesn't exist in the repository and I had to extract it from a tar.gz into the /usr/lib/rhythmbox directory manually.

Thanks for the analogy, Dayofswords. Let's suppose I don't have a 4 year-old kid and I am the only one who will use this machine. Are there any other  situations besides the one you describe that sudo is supposed to protect  you from?

---

### Post by lisati on 2010-05-31
While it might not answer your specific question, you can find some background information here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MCVenom on 2010-05-31
> **rather said:**
> But it wasn't a package. It was an equaliser plugin for Rhythmbox, which was already installed. This plugin doesn't exist in the repository and I had to extract it from a tar.gz into the /usr/lib/rhythmbox directory manually.

Thanks for the analogy, Dayofswords. Let's suppose I don't have a 4 year-old kid and I am the only one who will use this machine. Are there any other  situations besides the one you describe that sudo is supposed to protect  you from?
Malware. Malware for Linux is rare, but it happens -- and when it does, it isn't a good idea to just give it root access like that.

There's absolutely no good reason IMO to do day-to-day computing as a root user. Just leave root as is and stick with sudo; trust me, it'll benefit you in the long run.

---

### Post by lovinglinux on 2010-05-31
> **rather said:**
> Are there any other  situations besides the one you describe that sudo is supposed to protect  you from?

Sudo protects you not only from accidental deletion, but prevents applications that shouldn't be installing things and modifying system files to do so. Let's say you visit a site with some malware script, if it wasn't for sudo, the site would be able to do whatever it wants, because Firefox has total access to your system, except when sudo is required. BTW, use [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/).

---

### Post by Agent ME on 2010-05-31
One of the differences between common installs of Windows and Linux is that on Linux, the use of the root/admin account is heavily discouraged except where it's needed.

Imagine that there's an exploit in your web browser used on a site you visit. If you're on the root account, then the malicious software has root and can take complete control of your system, and it can even take steps to make itself invisible. If you're on a normal account, then the malicious software can only affect the current user. The other users of the system are unaffected; an admin account can be used to go in and remove the virus (or just delete the entire user account and create a new one for the user).

Running as a normal user account also forces the user to keep their files in his own home directory and separate from the system directories.

---

### Post by Lucky. on 2010-05-31
I use and strongly recommend sudo and gksudo, but I'll be the antagonist just for the sake of arguing.

Being new to linux can be challenging/frustrating because the initial immersion often means testing out a TON of software - and sometimes that software isn't in the repositories.  Using sudo nonstop can be annoying, and it's hardly worth it if you're just going to junk up your system and reformat it later.  It's particularly annoying when you forget to use it on some install/maintenance script that installs halfway into your user directory - then fails out when it tries to write the rest to a system directory.  Then the uninstall fails as well because it was never installed correctly, and you have a junked up system.  Gah!

Troubleshooting can be even worse because security is an extra variable and the error messages can be atrocious.  You forget to type "sudo" one time, and you get some wacky error message like "Error code #403 - cannot complete task."  The next thing you know you're spending 2 hours installing extra random packages, editing tons of files, hitting up forums, chasing a bunch of different fixit directions...but in the end it was just something as simple as "sudo".

Consider the above posts your warning, but!  If you're warming up to the system and understand the risks, it's always possible to enable the root account.  Test out that software - write down the correct configurations, fixes, and workarounds.  Do your "damage", get acquainted with the software, and take notes.  Understand that you have significantly less security, and treat your system as such.  When you give it a second go around (reformat, clean upgrade to new system, different distro), try to play by the rules.  After you know what you're doing, you'll find yourself typing sudo a lot less.

Oh yeah, there's also "sudo su" or "sudo -i" to keep your privileges elevated for a while.  So instead of:

```

sudo do this
sudo do that
sudo do some more
sudo holy smokes more and more

```

You can just type:

```

sudo su
do this
do that
do some more
holy smokes more and more
exit   (to return to your standard prompt)

```

> I also don't get how sudo gives me temporary access as root, if the password sudo asks me to type in is MY password (I've read that the root doesn't have one). Seems pretty contradictory.

This had me wondering the same thing when I started.  It ends up that the first user account created belongs to an admin group.  If you create a few more user accounts, sudo won't work on any of them unless you add them to the admin group.  So sudo won't work for anybody if they use their password...they still have to be an admin.

I've heard that sudo is different than plain root access in terms of logging.  Imagine you had 3 administrators running your computer/server.  If they all knew the root password and started doing damage, nobody would know who's responsible.  However with sudo, even though it gives you root privileges, it still records the user that made changes to the system in various log files.  That's what I've heard at least, never tested/verified it.

---

### Post by holocene on 2010-06-01
Ubuntu is great, but I think I would prefer having the option of ordinary root access, in a "supported" way.

I say that after having many systems that had traditional root accounts.

---

### Post by ankspo71 on 2010-06-01
Hi Rather,
If you need an equalizer, try this link:
[http://174.121.47.78/linux-tutorials/954-add-equalizer-for-pulse-audio-in-ubuntu-lucid-lynx](http://174.121.47.78/linux-tutorials/954-add-equalizer-for-pulse-audio-in-ubuntu-lucid-lynx)
It's a system wide graphical equalizer for PulseAudio.
I'm using it now in Kubuntu. It's better than the rhythmbox EQ, but you didn't hear that from me :P

---

### Post by MCVenom on 2010-06-01
> **holocene said:**
> Ubuntu is great, but I think I would prefer having the option of ordinary root access, in a "supported" way.

I say that after having many systems that had traditional root accounts.
I humbly disagree -- don't want us to end up with everyone running a root account for day to day tasks. Windows was kind enough to show us the infinite amount of problems that causes :P

---

### Post by Rubi1200 on 2010-06-01
> **BlackOtaku said:**
> I humbly disagree -- don't want us to end up with everyone running a root account for day to day tasks. Windows was kind enough to show us the infinite amount of problems that causes :P

+1 and then some!!

I am a little surprised, even shocked, at the number of posts found here on the forums regarding the use of root/sudo. These posts range in tone from simple misunderstanding of the concept (understandable for those completely new to Linux) to outrageous complaints (from those who, in my opinion, should know better) that sudo interferes with the ability of the user to run their system. 

I hope that new, as well as more experienced, users will read and follow the advice posted by those in the know on these forums and realize that Sudo=Real and Tangible Computer Security.

---

### Post by Simian Man on 2010-06-01
> **holocene said:**
> Ubuntu is great, but I think I would prefer having the option of ordinary root access, in a "supported" way.

I say that after having many systems that had traditional root accounts.

You can just unlock the root account and use it the way you would on any other Unix system.  There isn't really anything in that to "support".  That was always my very first step after installation when I had Ubuntu.

---

### Post by mkvnmtr on 2010-06-01
It is funny how we all have our own idea about what works best.After using sudo in Ubuntu I have recently done a couple of Debian installs and left the root account unenabled and use sudo. You can do it any way you like and get the same results.

---

### Post by cariboo on 2010-06-01
The forum policy is more about not advising a new user to log in graphically as root. We really have no opinion one way or the other if a user wants to enable the root account. The RootSudo documentation even tells you how to do it.

Personally I haven't found any reason to enable the root account, as sudo -i gives me a root shell, and allows me to do anything I need or want to do.

I believe it is more a matter of habit than anything else. I recently set up a system with Debian stable, I set up the root account, but don't use it. I'm so used to using sudo, that anytime I have to any administrative tasks my fingers automatically start typing sudo without even thinking about it.

---

### Post by SunnyRabbiera on 2010-06-01
A eay way to edit the core files without command line is to install nautilus-gksu

After installation and a log out you can now right click on the folders/files you want and select "open as administrator"

---

### Post by RiceMonster on 2010-06-01
> **Simian Man said:**
> You can just unlock the root account and use it the way you would on any other Unix system.  There isn't really anything in that to "support".  That was always my very first step after installation when I had Ubuntu.

Since sudo access is granted to everything, you can even log in as root without unlocking the root account with ease, by doing sudo -i, sudo sh, sudo bash, sudo su, etc. That's really the reason why I think it makes more sense to use a root account, because even if you disable those commands to a user with access to everything via sudo, they can just copy or rename su or any shell. (Note: If I'm not allowed to post that, then it's fine if a mod removes it from my post).

I personally only see a use for sudo if you want to grant root access for *specific* programs, which it was designed for.

---

### Post by juancarlospaco on 2010-06-01
**Sudo is not for Graphical Applications!!!**

---

### Post by WinterRain on 2010-06-01
> **holocene said:**
> Ubuntu is great, but **I think I would prefer having the option of ordinary root access**, in a "supported" way.

I say that after having many systems that had traditional root accounts.

Doing *sudo -i* in ubuntu is the same as *su* to become root. There you go.

---

### Post by aysiu on 2010-06-01
> **rather said:**
> 
- sudo nautilus /usr/lib and then shift-delete the dir Really should be ```
gksudo nautilus
```

> How would I have been able to do this without Terminal, just using the GUI? Well, there are a number of ways. First, you can create a keyboard shortcut or launcher for the command ```
gksudo nautilus
``` You can also use Synaptic Package Manager or Ubuntu Software Center to install the *nautilus-gksu* package, which allows you a right-click "Edit as root" option.

Really, though, this is [a bug that was reported years ago](https://bugs.launchpad.net/nautilus/+bug/12154) and unfortunately labeled as a "wishlist" item.

**The way it is now:** you try to edit a system file and get permission denied, even if you are a sudoer.

**The way it should be:** you try to edit a system file, and you get prompted (if you're a sudoer) for your sudo password to authenticate and have the option to authenticate or cancel the action, or you get an access denied message (if you are not a sudoer).

> 
I also don't get how sudo gives me temporary access as root, if the password sudo asks me to type in is MY password (I've read that the root doesn't have one). Seems pretty contradictory. What it does is provide an extra layer of protection for system files. Ever had a Windows malware problem or seen someone with one? Not easy to clean up. That's because Windows malware takes advantage of the fact that almost all Windows users operate as administrator all the time, and so it infects all the Windows system files, so the only real effective way to clean up the malware is to reinstall Windows, not just create a new user account.

Before you *sudo* something you are operating effectively as a limited user account. When you do *sudo* something, you aren't escalating privilege of your entire account but just for that one action. Now, Ubuntu does have a *sudo* timeout of either 5 or 15 minutes (I forget which), which means theoretically if you had executed *gksudo nautilus* and then you visited some website that took advantage of an unpatched Firefox flaw that allowed it to run arbitrary code and it decided to run *gksudo* some malicious script, then your computer could be compromised fully.

But without that timeout, you get that annoying password prompt every single time you want to modify a system file or setting in some way.

There is always a balance to be had between security and convenience. You get a little security with *sudo* and a little convenience with the *sudo* timeout.

---

### Post by SushiR on 2010-06-01
Don't know if someone has posted this link? 
[http://www.sudo.ws/sudo/sample.sudoers](http://www.sudo.ws/sudo/sample.sudoers)
It's an interesting read...

---

### Post by WinterRain on 2010-06-01
> **aysiu said:**
> 
**The way it is now:** you try to edit a system file and get permission denied, even if you are a sudoer.


Works for me.

---

### Post by t.rei on 2010-06-01
> **aysiu said:**
> 
**The way it should be:** you try to edit a system file, and you get prompted (if you're a sudoer) for your sudo password to authenticate and have the option to authenticate or cancel the action, or you get an access denied message (if you are not a sudoer).


This, really.

As someone currently actively engaged in studies concerning usability of security mechanisms.

---

### Post by RiceMonster on 2010-06-01
> **WinterRain said:**
> Works for me.

I think aysiu mean if you were to do something like "vim /etc/fstab" without using sudo, you'll get permission denied.

---

### Post by holocene on 2010-06-01
To those who thought I was campaigning or suggesting that the Ubuntu user community  switch to using a root account for day to day stuff, I was NOT. I don't run day to day as root any system; Windows, BSD, Linux and of course not Ubuntu. I advise my Windows people to switch their admin accounts to a limited  account, and setup a new admin account, then set passwords on all accounts. 

What I was trying to say in my usually unclear manner :redface:, is that once a person has used a Linux or *BSD system for years on and off, like me,  with a root account, that "habit" is hard to break. 

Now, even sudo did allow me to do a sudo rm -R /etc instead of sudo rm -R /media/backupdrive/etc in my rsync testing. (This was not readily fixable but luckily my home directory was fully backed up so I did not lose those files after re-install.) 

Anyway, I support Ubuntu's efforts to bring Linux to more people, and appreciate the efforts the developer make to protect users from themselves.

Best Regards to all
Steve.

---

### Post by aysiu on 2010-06-01
> **RiceMonster said:**
> I think aysiu mean if you were to do something like "vim /etc/fstab" without using sudo, you'll get permission denied.
Or something like this:

A user wants to make an icon set available to all users, so she wants to drag it to /usr/share/icons

This is what happens now. You get permission denied and the wonderful options of *cancel* or *skip* (neither of which does anything useful). You then have to close one Nautilus window and then launch *gksudo nautilus* and then navigate back to /usr/share/icons and drag the theme in there again. Annoying.

Instead of *cancel* and *skip* it should be *cancel* and a password authentication if the user trying to drag the icon folder in there is in the *admin* group.

---

### Post by rather on 2010-06-01
[quote=aysiu]Well, there are a number of ways. (...)[/quote]
Thank you, aysiu, this is the most helpful post (#21) in the thread.

I feel a little more enlightened now. I'm still surprised by the whole idea of how this works. It either involves a lot of extra typing in the command-line (to circumvent GUI restrictions) or the installation of extra things that really are beyond the average user.

---

### Post by aysiu on 2010-06-01
> **rather said:**
> Thank you, aysiu, this is the most helpful post (#21) in the thread.

I feel a little more enlightened now. I'm still surprised by the whole idea of how this works. It either involves a lot of extra typing in the command-line (to circumvent GUI restrictions) or the installation of extra things that really are beyond the average user.
We're certainly not in an ideal situation right now.

My best advice is to just create a keyboard shortcut for ```
gksudo nautilus
``` It does involve pasting that one bit of code into System > Preferences > Keyboard Shortcuts > Add, but after you do that you won't have to see the terminal again to modify system files.

---

### Post by MCVenom on 2010-06-01
> **aysiu said:**
> **The way it should be:** you try to edit a system file, and you get prompted (if you're a sudoer) for your sudo password to authenticate and have the option to authenticate or cancel the action, or you get an access denied message (if you are not a sudoer).

I wholeheartedly agree with this, Linux Mint has long had the nautilus-gksu package (which I finally found the name of through this thread, thanks :)), and I've wondered why it isn't included by default in Ubuntu.

---

### Post by Mr. Picklesworth on 2010-06-01
To clarify one thing, there is an effort to kill sudo on the desktop. sudo elevates an entire process to run as root. It is great on the command line interface, since the commands we run there are all tiny applications that do one thing well. It is not so great on the desktop, where an application is dealing with a complex GUI and doing all sorts of file manipulation outside of the one little bit of functionality you needed to run it as root for.

The solution being gradually implemented is PolicyKit. You can see PolicyKit in action with a few of the configuration dialogs that have Unlock buttons, and in Software Centre when you install software. There are MANY differences with its approach, but some important ones are that security is controlled in a much more fine-grained way, only the one operation within an application gets escalated privileges (and only specific privileges, instead of the whole deal!), and applications talk to PolicyKit for themselves.

---

### Post by aysiu on 2010-06-01
> **Mr. Picklesworth said:**
> 
The solution being gradually implemented is PolicyKit. You can see PolicyKit in action with a few of the configuration dialogs that have Unlock buttons, and in Software Centre when you install software. There are MANY differences with its approach, but some important ones are that security is controlled in a much more fine-grained way, only the one operation within an application gets escalated privileges (and only specific privileges, instead of the whole deal!), and applications talk to PolicyKit for themselves. I'm not sure if PolicyKit can be made to do this, but what I suggested earlier in the thread (in line with the several-years-old unfixed bug report I linked to) would seem to be in line with that sort of approach.

Instead of launching ```
gksudo nautilus
``` or using *nautilus-gksu* to launch an entire instance of Nautilus as root just to copy or delete some files, you could have a temporary escalation of only the action you intended to do (so if you're copying icons to /usr/share/icons, instead of having the entire instance of Nautilus run as root, you would have only the copy action itself run as root).

---

### Post by Chame_Wizard on 2010-06-01
@OP
[IMG]http://geniushackers.com/blog/wp-content/uploads/2009/06/filesystemhierarchyhb8.jpg[/IMG]

---

### Post by rather on 2010-06-01
Thanks Chame, that's very useful. I also found this: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by lisati on 2010-06-01
In the three years I've been using Ubuntu, I have **never** needed to enable direct access to the root account. Every time I've needed superuser privileges on my main admin account, using sudo/gksudo has been adequate.

---

### Post by rookcifer on 2010-06-01
> **rather said:**
> 
For example, I installed something I pretty much immediately decided I didn't like. It had gone in /usr/lib (which seems like the equivalent of Windows' "Program Files" - is that right?) but I wasn't able to shift-delete it (rather than send to trash). The solutions seemed to me to be:



No, /usr/lib is not the equivalent of "Program Files" in Windows.  The equivalent of that would be /bin or /usr/bin.  /usr/lib is where libraries go (a library is a collection of programming language helper files, for a lack of a better term).  /usr/lib (and /lib) also contains a lot of .so files which is the equivalent of .dll files on Windows.

---

### Post by 3rdalbum on 2010-06-02
> **aysiu said:**
> I'm not sure if PolicyKit can be made to do this, but what I suggested earlier in the thread (in line with the several-years-old unfixed bug report I linked to) would seem to be in line with that sort of approach.

Instead of launching ```
gksudo nautilus
``` or using *nautilus-gksu* to launch an entire instance of Nautilus as root just to copy or delete some files, you could have a temporary escalation of only the action you intended to do (so if you're copying icons to /usr/share/icons, instead of having the entire instance of Nautilus run as root, you would have only the copy action itself run as root).

Policykit can do this, but Nautilus would need to be updated to allow this. Unfortunately, Gnome developers have been promising this for a long time but have not delivered. I'd like to see the Nautilus Elementary project implement Policykit in the file browser, but I don't think they'd bother as it wouldn't help make Nautilus look like Finder.

---

### Post by murderslastcrow on 2010-06-02
I never knew you could use the root account! D: Lol, it's difficult enough that I've never ended up doing it. Probably not that difficult, but I've never found any reason to do so. Even with really complicated remote server setups and stuff.

---

### Post by rather on 2010-06-02
> **rookcifer said:**
> No, /usr/lib is not the equivalent of "Program Files" in Windows.  The equivalent of that would be /bin or /usr/bin.  /usr/lib is where libraries go (a library is a collection of programming language helper files, for a lack of a better term).  /usr/lib (and /lib) also contains a lot of .so files which is the equivalent of .dll files on Windows.

So when I untar a simple program, should it be stored in a folder of its own in /usr/bin/? For example, I just did this with [WhatPulse](http://whatpulse.org). Is this the "done" thing?

---

### Post by aysiu on 2010-06-02
> **rather said:**
> So when I untar a simple program, should it be stored in a folder of its own in /usr/bin/? For example, I just did this with [WhatPulse](http://whatpulse.org). Is this the "done" thing?
It doesn't really matter where you put it. I tend to put such things in the /opt or /usr/local/bin directory.

---

### Post by toupeiro on 2010-06-02
Sudo going away on the desktop is a dumb idea.  Using sudo properly is a better idea.  make sudo run as different user accounts, it doesn't HAVE to elevate to root, its just implemented that way.  Sudo -U ftw.

---

### Post by Mr. Picklesworth on 2010-06-02
> **toupeiro said:**
> Sudo going away on the desktop is a dumb idea.  Using sudo properly is a better idea.  make sudo run as different user accounts, it doesn't HAVE to elevate to root, its just implemented that way.  Sudo -U ftw.

Sure, but you're still providing an entire process with privileges that only a small portion of that process needs. And on the desktop, it's particularly easy for one process to control another.

---

### Post by Rubi1200 on 2010-06-03
> **lisati said:**
> In the three years I've been using Ubuntu, I have **never** needed to enable direct access to the root account. Every time I've needed superuser privileges on my main admin account, using sudo/gksudo has been adequate.

This is what I don't understand regarding these root/sudo discussions:

As lisati points out: "I have **never** needed to enable direct access to the root account."

Why are people seemingly dissatisfied with the security model implemented on Ubuntu?

Why does it seem that there is a burning NEED to use/enable the root account?

Personally, I have no desire to enable the root account (tried it on PCLOS once and it just caused problems). I am satisfied that I can accomplish ANY task in Ubuntu by using sudo/gksudo.

---

### Post by rather on 2010-06-03
> **Rubi1200 said:**
>  I am satisfied that I can accomplish ANY task in Ubuntu by using sudo/gksudo.

Then it seems like Ubuntu needs to decide whether it's going to try to cater for the average non computer-literate Windows user or only for the nerds that are happy to use the command line.

Using Terminal is scary (and exciting) enough, and typing stuff you don't really understand (even simple things like gksudo nautilus -- it's hard to even *know* the "explorer" is called Nautilus without going to Help > About) is a major hurdle for the newbie.

Once you know about it and understand it, it's fine, but it's enough to scare people into returning back to Windows, where all you have to do is click things. At the moment it seems like lots of (even relatively simple tasks) are nigh on impossible to achieve without at having to have visited the command line at least once.

---

### Post by Rubi1200 on 2010-06-03
> **rather said:**
> Then it seems like Ubuntu needs to decide whether it's going to try to cater for the average non computer-literate Windows user or only for the nerds that are happy to use the command line.

Using Terminal is scary (and exciting) enough, and typing stuff you don't really understand (even simple things like gksudo nautilus -- it's hard to even *know* the "explorer" is called Nautilus without going to Help > About) is a major hurdle for the newbie.

Once you know about it and understand it, it's fine, but it's enough to scare people into returning back to Windows, where all you have to do is click things. At the moment it seems like lots of (even relatively simple tasks) are nigh on impossible to achieve without at having to have visited the command line at least once.

Although I understand and empathize with your viewpoint (I have only been using Ubuntu for 2 months), I have to respectfully disagree with your statement that Ubuntu should be more like Windows. 

And that is exactly the mistake that new users make; they come to Ubuntu expecting, even demanding, that it be just like Windows and yet not be Windows. But Linux is not Windows and never will be (I hope).

When I first started playing around with Linux in about 2005/2006 there were certain distros that were command line only (some still exist).

Linux has made huge leaps and bounds in the last few years in terms of user friendliness. Nowadays, many, many functions are point and click. 

Could it be made more friendly, could more programs use a graphical interface? Probably.

However, at the end of the day, certain actions will require learning the terminal and bash commands.

The best suggestion I can offer is to read as much as you can and to deepen the Linux experience slowly but surely. 

If you can browse the web, listen to music, open files etc. then you are already an Ubuntu user.

The rest of it will come with time: nobody is a Linux guru after a few days, weeks, or months.

Finally, I have to say that, at least in my experience, learning Linux involves being willing to also unlearn a lot of Windows habits.

Good luck!

:)

---

### Post by aysiu on 2010-06-03
> **rather said:**
> Then it seems like Ubuntu needs to decide whether it's going to try to cater for the average non computer-literate Windows user or only for the nerds that are happy to use the command line. That has **nothing** to do with using *sudo* instead of root, though.

Mac OS X also uses *sudo* instead of root, but no one accuses Apple of catering to only power users.

It has more to do with the implementation of it. As I said before, if someone drags a file to a root-owned folder, there has to be an authentication prompt (using *sudo*) instead of just a "permission denied" message.

---

### Post by RiceMonster on 2010-06-03
> **aysiu said:**
> It has more to do with the implementation of it. As I said before, if someone drags a file to a root-owned folder, there has to be an authentication prompt (using *sudo*) instead of just a "permission denied" message.

I agree. It really shouldn't be hard to add to nautilus with PolicyKit, should it?

---

### Post by Simian Man on 2010-06-03
> **Rubi1200 said:**
> This is what I don't understand regarding these root/sudo discussions:

As lisati points out: "I have **never** needed to enable direct access to the root account."

Of course nobody *needs* to enable the root account.  Likewise nobody *needs* to use sudo.  It's a matter of preference.  I just prefer to use the root account because it's the way that every other Unix system has worked for decades.  Other people prefer sudo and that's fine.

> **Rubi1200 said:**
> Personally, I have no desire to enable the root account (tried it on PCLOS once and it just caused problems). I am satisfied that I can accomplish ANY task in Ubuntu by using sudo/gksudo.
That's pretty funny because PCLinuxOS (like just about every other non-Ubuntu distro) comes with an enabled root account.


> **Rubi1200 said:**
> And that is exactly the mistake that new users make; they come to Ubuntu expecting, even demanding, that it be just like Windows and yet not be Windows. But Linux is not Windows and never will be (I hope).
That's also pretty funny because, for an end-user, the Ubuntu security model is more closely related to that of Windows than to traditional Linux.  Both are reasonable security-wise, it's just funny.

---

### Post by sisco311 on 2010-06-03
> **Simian Man said:**
> Of course nobody *needs* to enable the root account.  Likewise nobody *needs* to use sudo.  It's a matter of preference.  I just prefer to use the root account because it's the way that every other Unix system has worked for decades.  Other people prefer sudo and that's fine.


I was always wondering how do people use the root account?

Do you login as root via the GUI and/or CLI?

---

### Post by RiceMonster on 2010-06-03
> **sisco311 said:**
> I was always wondering how do people use the root account?

Do you login as root via the GUI and/or CLI?

You log in via the cli, just by typing "su". If you want to run grapphical applications, you can use gksu or kdesu. In many cases, the programs will also handle that for you with PolicyKit, and you'll just get promoted for your root password (kind of like when you get promoted for your own password in Ubuntu).\

Give a distro other than Ubuntu a try if you want to see it for yourself (or you could always unlock the root account on Ubuntu, if you wanted).

---

### Post by toupeiro on 2010-06-03
> **Mr. Picklesworth said:**
> Sure, but you're still providing an entire process with privileges that only a small portion of that process needs. And on the desktop, it's particularly easy for one process to control another.

Um, ok so you're saying that if, for example, the process will elevate to the bin, or nobody,  user account rather than the root user account that the risk is the same?  If UNIX teaches us anything, hopefully its that sometimes the most straightforward methods of security are the best.  Introducing a new mechanism oftentimes does more harm than good by having more area to exploit.  If a new mechanism is truly warranted, thats one thing, but in this case I struggle with that being true.  I'm not saying sudo and UNIX security in general is bulletproof, but I am saying that with minimal hardening, its more secure than most OSes out there.  Linux doesn't have to be any different.

Sudo is more than secure enough when used properly.  Ubuntu likes to reinvent wheels rather than make sure they're being built well.  This is another prime example.  Sudo can be very efficient **and** secure when its used properly.  Ubuntu chose to use it in a way to make things easy, not make things more secure.  That's not sudo's fault.

sudo -r and -t will also allow sudo to use SELinux role and typecontexts, which is even more secure yet.

---

### Post by sisco311 on 2010-06-03
> **RiceMonster said:**
> You log in via the cli, just by typing "su". If you want to run grapphical applications, you can use gksu or kdesu. In many cases, the programs will also handle that for you with PolicyKit, and you'll just get promoted for your root password (kind of like when you get promoted for your own password in Ubuntu).\

Give a distro other than Ubuntu a try if you want to see it for yourself (or you could always unlock the root account on Ubuntu, if you wanted).

I know that. :)

Never mind, it was a stupid question anyway. You can use the root password to authenticate yourself as root via su and policykit and login in directly as root in virtual console. So basically, one could use the root password instead of an "admin" password.

---

### Post by Barrucadu on 2010-06-03
> **rather said:**
> So when I untar a simple program, should it be stored in a folder of its own in /usr/bin/? For example, I just did this with [WhatPulse](http://whatpulse.org). Is this the "done" thing?

It gets spread out all over the place. Binaries go in /usr/bin, data goes in /usr/share, libraries go in /usr/lib, manpages go in /usr/man&#8230;

---

### Post by Mr. Picklesworth on 2010-06-03
> **toupeiro said:**
> Um, ok so you're saying that if, for example, the process will elevate to the bin, or nobody,  user account rather than the root user account that the risk is the same?  If UNIX teaches us anything, hopefully its that sometimes the most straightforward methods of security are the best.  Introducing a new mechanism oftentimes does more harm than good by having more area to exploit.  If a new mechanism is truly warranted, thats one thing, but in this case I struggle with that being true.  I'm not saying sudo and UNIX security in general is bulletproof, but I am saying that with minimal hardening, its more secure than most OSes out there.  Linux doesn't have to be any different.

Sudo is more than secure enough when used properly.  Ubuntu likes to reinvent wheels rather than make sure they're being built well.  This is another prime example.  Sudo can be very efficient **and** secure when its used properly.  Ubuntu chose to use it in a way to make things easy, not make things more secure.  That's not sudo's fault.

sudo -r and -t will also allow sudo to use SELinux role and typecontexts, which is even more secure yet.

My point is that you're still providing the privilege associated with that user to a huge swath of code which doesn't need that privilege. It isn't a security threat on its own, but it *is* asking for trouble.

Picture an application which runs (as root) libjpeg, libxml, the entire GTK+ library and all of its dependencies. It ultimately does the bidding of any client that is sending it commands via the X server, or any code that is executed through an attack to any of those dependencies&#8230; where the only thing that actually needed the privilege was a few file operations.

It's the same reason user accounts are unprivileged by default.

I didn't know about the -r and -t switches, though. That is cool! Thanks :)

---

### Post by SushiR on 2010-06-03
Sudo is very capable in a multi-user environment. It can grant certain users access to certain commands, while others are not allowed to access them. Sudo can do even more. Just have a look at the link I've posted. I think sudo is a very good security solution.

---

### Post by piousp on 2010-06-03
> **sisco311 said:**
> I was always wondering how do people use the root account?

Do you login as root via the GUI and/or CLI?

You can login as root (via gui, say gdm, kdm, whatever) in other distros.

---

### Post by sisco311 on 2010-06-03
> **piousp said:**
> You can login as root (via gui, say gdm, kdm, whatever) in other distros.

Is that a default setting in any modern linux distro? In fedora and arch root login via the GUI is denied by default.

---

### Post by piousp on 2010-06-03
> **sisco311 said:**
> Is that a default setting in any modern linux distro? In fedora and arch root login via the GUI is denied by default.

I dont remember exactly which distro i was trying (suse? mandriva?) but it was last year.
But yeah, i dont think its a good idea to have that option

---

### Post by Legendary_Bibo on 2010-06-03
> **aysiu said:**
> We're certainly not in an ideal situation right now.

My best advice is to just create a keyboard shortcut for ```
gksudo nautilus
``` It does involve pasting that one bit of code into System > Preferences > Keyboard Shortcuts > Add, but after you do that you won't have to see the terminal again to modify system files.
I've been reading through this and that was actually a useful command and way of going about it, thanks!

---

### Post by Ebere on 2010-06-03
I agree with aysiu.


I don't think getting rid of sudo is a good idea.

However... 


If nothing else, I am a patient man. When it comes to the computer, it takes a lot to get me frustrated.

Having said that, I got very frustrated, the first three weeks or so, that I was trying out linux distros.

If I got as frustrated as I did, then I know a great deal of people get frustrated enough just to walk away and go back to windows.



That frustration came primarily from two things.

*Having absolutely no idea WHAT I needed, let alone WHY.  And all the learning that went along with just getting a system up and running enough to keep me going for a bit. (Until I could then learn enough more, to put together a system that I would be more happy with.)

*And... Having to -constantly- be putting in my password. And -still- not being able to do some things until I learned how to do root.


sudo and putting in the password is not too bad, as long as it is made a bit simpler. 

For instance, as aysiu has suggested... Instead of making people jump through all kinds of hoops just to change the permissions on a file... Let there be an option to change the permissions just by putting in the password.

Right click on a file >Choose "Change permissions" as an option. >Be asked for password. >done. Change the permissions. >Lose the change permissions, option, after about 5 minutes.

---

### Post by Shining Arcanine on 2010-06-03
> **Dayofswords said:**
> Bob logged in as root(if this were defualt):
Bob is looking at his filesystem, it's odd, no C:. crazy things
bob is thirsty, he goes off to get a soda. jake, age 4 comes to the computer and starts playing with the key board and mouse.

smash, bang
hit, click.

bob comes back an notices the windows showing "/" is blank. he swears there were things, but he goes on his way.... but wait, where the programs in his application menu, what's this weird box that popped up with boxes instead of text. the computer just froze!!

Bob is screwed.





Bob logged in as a user with sudo(if this were defualt):
Bob is looking at his filesystem, it's odd, no C:. crazy things
bob is thirsty, he goes off to get a soda. jake, age 4 comes to the computer and starts playing with the key board and mouse.

smash, bang
hit, click.

bob comes back and noticed his window had moved somewhat and there is a permission error. wonder what happened, he closes it and thinks nothing more of it. he opens firefox and notices that in the news a local woman has found an old mining shaft, wow he thinks, could be gold or something.

bob is fine.

Why did Bob not hit Ctrl+Alt+L before he left his system?


> **sisco311 said:**
> Is that a default setting in any modern linux distro? In fedora and arch root login via the GUI is denied by default.

Logging into root via a console/terminal and logging into root via a desktop manager are two different things. Usually starting a desktop environment as root is considered a bad idea.

The way you usually should use root is in a terminal window.

> **Ebere said:**
> I agree with aysiu.


I don't think getting rid of sudo is a good idea.

However... 


If nothing else, I am a patient man. When it comes to the computer, it takes a lot to get me frustrated.

Having said that, I got very frustrated, the first three weeks or so, that I was trying out linux distros.

If I got as frustrated as I did, then I know a great deal of people get frustrated enough just to walk away and go back to windows.



That frustration came primarily from two things.

*Having absolutely no idea WHAT I needed, let alone WHY.  And all the learning that went along with just getting a system up and running enough to keep me going for a bit. (Until I could then learn enough more, to put together a system that I would be more happy with.)

*And... Having to -constantly- be putting in my password. And -still- not being able to do some things until I learned how to do root.


sudo and putting in the password is not too bad, as long as it is made a bit simpler. 

For instance, as aysiu has suggested... Instead of making people jump through all kinds of hoops just to change the permissions on a file... Let there be an option to change the permissions just by putting in the password.

Right click on a file >Choose "Change permissions" as an option. >Be asked for password. >done. Change the permissions. >Lose the change permissions, option, after about 5 minutes.

Gentoo Linux uses su instead of sudo by default and things work well on it. There is no need to require sudo to do things as root on Ubuntu, although considering Ubuntu's target audience (the Windows crowd), it might not be a good idea to give them su by default. They will likely abuse it by using it all the time, in which case, watch the complaints flow as they do things like [COLOR="Green"]rm -rf / tmp/*[/COLOR]. Note that the space in the directory path is intentional. You can do that with sudo too, but the point is that you might have some files you want to delete that you do not need root privileges to delete, but you would be logged onto the system as root anyway, so if you mistype your delete command, you could have severe consequences.

---

### Post by ericmc783 on 2010-06-05
The main benefit of using sudo:

Every cracker trying to brute-force their way into your linux PC will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are. Since the root account password is locked (by default, when using sudo) this attack becomes essentially meaningless, since there is no password to crack or guess in the first place. 

As described here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2010-06-05
> **ericmc783 said:**
> 
Every cracker trying to brute-force their way into your linux PC will know it has an account named root and will try that first. They don't just know there is an account named root. They also know the privileges that account has--all privileges.

---

### Post by Shining Arcanine on 2010-06-05
> **ericmc783 said:**
> The main benefit of using sudo:

Every cracker trying to brute-force their way into your linux PC will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are. Since the root account password is locked (by default, when using sudo) this attack becomes essentially meaningless, since there is no password to crack or guess in the first place. 

As described here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

How will they target the account to try to crack its password? Will they try SSH? I think just about all SSH configurations are designed to disallow remote root logins, so any root access would need to be obtained by first logging into a regular user account and then running either su or sudo. Because of this, there really is no real security benefit to using one over the other.

---

