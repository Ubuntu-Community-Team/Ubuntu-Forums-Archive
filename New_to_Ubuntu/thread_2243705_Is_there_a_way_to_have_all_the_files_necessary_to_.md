---
title: "Is there a way to have all the files necessary to run an application be in one folder"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-10
Is there a way to have all the files necessary to run an application be in one folder? Similar to a "portable application" in Windows. Based on what I've read about uninstalling applications on Linux, it seems like a nightmare. "remove packagename" leaves behind config files and dependencies, "purge packagename" leaves behind config files in the home directory (and the config files can be anywhere, so it seems that I have to manually search the entire home folder to completely remove any traces of a program that I uninstalled. I know that these config files only take a trivial amount of space and don't affect the system's performance but they are redundant.

---

### Post by bapoumba on 2014-09-10
Purging a package should remove the config files from your system, not in your user environment. Here is a pretty good explanation : [http://unix.stackexchange.com/questions/38549/does-apt-get-purge-remove-config-files-stored-in-user-home-dir](http://unix.stackexchange.com/questions/38549/does-apt-get-purge-remove-config-files-stored-in-user-home-dir)
User configuration files are created by the application themselves when they are run, not by the package managers.

---

### Post by buzzingrobot on 2014-09-10
Yes, in theory, but...

Linux is architected around the concept of shared libraries. This means that multiple applications can rely on a given library while that library is only installed once.  Among other things, this makes updating much simpler and reliable since the package manager only needs to track one version of one library in a known, standard, location rather than track multiple versions in multiple non-standard locations.

Apps also rely on libraries being where they expect them to be.

Dependencies are not removed, then, because other packages are dependent on them. The complaints of the package manager can of course, be overridden and anything removed.  But, breakage will follow.

A 'purge' does not remove a user's config files because the user owns those files and may, in fact, intend to reinstall the package.

---

### Post by mcduck on 2014-09-10
It's possible, but it's also highly inefficient way of insatlling applications as you loose all the benefitts of being able to share same libraries and packages between all the programs that use them, thus wasting lots of disk space, and resulting in more complicated, larger, and slower downloads to update anything etc.

Some applications are distributed that way, most often games and third-party apps that aren't really using shared assets that well anyway, or depend on very specific versions and keeping them updated to support all the stuff from different distributions would be complicated. Even then many of the apps still create their setting directories in user's home, outside of the application install directory, to allow users to move the app around or reinstal & update without loosing all settings or game saves.

I'd really just recommend not worrying about the config fiels in user homes, in the worst case you'll probably waste a meagbyte or two of disk space if you never even think about them. And all the system-wide stuff & used dependencies can be easily cleaned aways with a few simple commands ran every now and then...

---

### Post by grahammechanical on 2014-09-10
Yes. If you use Microsoft Windows! Or has Windows changed to become more like Linux since I last used Windows 98?

apt-get will tell us if any packages are redundant and recommend using autoremove.

---

### Post by garycheng12 on 2014-09-11
autoremove removes orphaned packages that used to be installed as a dependency for other applications but aren't any longer. That doesn't mean they aren't in use. How can I be sure that running this command won't remove remove anything I use? What problems will autoremove create in terms of this?

---

### Post by whitesmith on 2014-09-11
The autoremove option only removes packages installed *as part of other packages that are no longer installed*. See [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto). The problem in making Linux look/feel/behave like the OS whose name I'm not supposed to mention is that Unix, Linux' predecessor, was originally architected for fun by a brilliant systems programmer from Bell Telephone Laboratories, whereas Windows was code salad tossed by some dudes from an always-rainy town in the Pacific Northwest who were in it for the dough. Big difference. Really, really big. On a serious note, the reference I supplied shows that apt-get clean could have undesirable consequences.

---

### Post by vasa1 on 2014-09-11
I haven't yet had problems with autoremove or clean. But then I'm very conservative. To my mind, clean only removes stuff in /var/cache/apt/archives

---

### Post by bapoumba on 2014-09-11
re: autoremove
Say you mistakingly removed a metapackage, one of the central ones, say ubuntu-desktop. Autoremove can lead to removing packages that came as dependencies of this metapackage, applications or packages essential to applications you intend to use or are using. When properly used, the package managers are very powerful (this is one of the things I like about Linux in general, and debian-based distributions in particular). But the end user can wreck their system not using them properly.

---

### Post by vasa1 on 2014-09-11
> **bapoumba said:**
> re: autoremove
Say you **mistakenly** removed a metapackage ... But the end user can wreck their system not using them **properly**.
Then nothing can be called "safe". These situations are picked up by people who then open several threads on the same topic. Then Google indexes these threads. Then bloggers, sockpuppets, and "tech" sites say Linux is unsafe :)

[Someone is supposed to have said something]("https://www.goodreads.com/quotes/942-two-things-are-infinite-the-universe-and-human-stupidity-and") about the infinity, the Universe and something else.

My question: can *anything* be called safe? "*So I'll just drill into a healthy tooth until I reach the pulp. That is unless, of course, you can tell me that it's safe*."

---

### Post by mc4man on 2014-09-11
> **bapoumba said:**
> re: autoremove
Say you mistakingly removed a metapackage, one of the central ones, say ubuntu-desktop. Autoremove can lead to removing packages that came as dependencies of this metapackage, 
That isn't an issue with any metapackage that's part of the default install (ex. ubuntu-desktop).
 As far as any user installed metapackage, never really looked, shouldn't be that hard to test..

In any event reading what is to happen before commiting is the best way to avoid problems.

---

### Post by buzzingrobot on 2014-09-12
That's why autoremove displays what's to be removed and requires confirmation. 

Packaging and dependency resolution schemes in Linux, as so much else, were written by developers to solve developer problems.  They assume a level of knowledge that's reasonable to expect in a developer, but not reasonable to expect in a run-of-the-mill user. 

Users typically do not know how packaging/dependency resolution works, and ought not to be expected to know. They will assume, incorrectly, that any option that's offered to them -- like autoremove -- is safe. 

I'd propose eliminating those autoremove prompts and requiring the function to be explicitly called. If packages are orphans and are not dependencies for anything on the system, better to just remove them automatically.

---

### Post by mcduck on 2014-09-12
it defintiely doesn't require *developer* levele of knowledge to deal with such tools. I doubt majority, or even a decent chuck, of Ubuntu users really are developers but just normal users and stills eem to handle this kind of stuff pretty well. :D

What comes to run-of-the-mill user, I wouldn't count anyone ho's even messing with comamnd-line apt-get into that category. And the nice easy-to-use GUI tools we have available for basic users are not offering to autoremove anything.

So it's more a case of those who are just starting to cross the gap between a basic GUI-tools-only desktop user and someone who knows the basics of the inner workings of their OS who might run into troubles with things like this. And even then there really are only a few situatons when autoremove might cause issues to someone who hasn't already been messing around with the system by insalling things from source or otherwise outside of the package management. Which, in my eyes, already moves them out of the "run-of-the-mill user" category.

Just like mc4man said, all of the default installed packages are marked as "manually installed" so autoremove will never touch them.

(basically if you want to remove all command line tools and options that might let soemone using them without doing basic research first to break their system, you'd pretty much have to remove most of the operating system functionality. I'd say the limit where this level of protecting beginner users ends is between graphical tools and the command line. I've at least twice in my time on these forums seen a new user demanding that the "rm" command should be removed because a new user used to desktop tools might not know that it will actually permanantly delete files instead of just sending them to a waste basket, for example. I bet operating system without the capability to ever remove any file would work really well... ;))

---

### Post by buzzingrobot on 2014-09-12
However we might define "run of the mill user" (not really a useful exercise) no package manager option should be presented to any user, of any skill level, at anytime, that could result in the removal of packages required by the system or by other currently installed packages unless that *specific*warning is also displayed:  What will removed and what dependent packages will be left in a disfunctional state.

Using autoremove can break a system. Removing the dependencies installed/created by a large metapackage can break a system.  They should not, ever. Deletion of packages that are current dependencies of other installed packages should not be a possibility with autoremove or when removing a metapackage.

---

### Post by oldfred on 2014-09-12
> I've at least twice in my time on these forums seen a new user demanding  that the "rm" command should be removed because a new user used to  desktop tools might not know that it will actually permanantly delete  files instead of just sending them to a waste basket, for example.

That is easy to do for simple cases.
       [http://ubuntuforums.org/showthread.php?t=623656](http://ubuntuforums.org/showthread.php?t=623656)
alias rm='mv --target-directory ~/.Trash'
The above alias command just causes 'mv' to be run instead of 'rm'. The only problem with this is the command will overwrite files with duplicate names. And even that may have some issues, see thread.

---

### Post by mcduck on 2014-09-12
Sure, it's easy to set up if you want to. As it is easy to configure apt-get to not suggest autoremoving stuff or just not use it. The point was *should it be done by default for every user*, and should similar protections be added to every (or at least all the commonly used) comamnd-line tools that might allow someone to shoot themselves in the foot if they use the tools without checking what the tool does and how it's used first?

(and those people were indeed demaning moving the rm command and functionality, not a fix to make it move things to trash. Since you'll still need some way to run the rm without such protection to be able to empty the trash occasionally, and I'm sure someone would then manage to use that override to delete some important personal file... :D)

---

### Post by buzzingrobot on 2014-09-12
> **mcduck said:**
>  As it is easy to configure apt-get to not suggest autoremoving stuff or just not use it. The point was *should it be done by default for every user*, and should similar protections be added to every (or at least all the commonly used) comamnd-line tools that might allow someone to shoot themselves in the foot if they use the tools without checking what the tool does and how it's used first?



Package managers, whether controlled by GUI or command line, should not remove packages other installed packages are currently dependent on  without an explicit and specific warning. Simply listing packages with a generic warning that their removal might be harmful is insufficient. No user -- skilled or not -- knows the dependency chains that exist in his or her system.

---

### Post by mcduck on 2014-09-12
That's the thing, they don't. apt-get autoremove *will not* remove a package as long as any other package still depends on it, and neither will it remove any of the stuff that would break your system (since everything installed by default is marked as "manually installed" and thus is not touched by autoremove.

What comes to possibly breakign something the user has manually installed outside of the package managent, there's obviously no way the package management *could* then know what the software might require or that even exists in the first place. However when one has been able to instal something outside of the packae amangement in the first place I think it would be safe to assume the user has at least some level of knowledge abut what he has done. (And to add to that, any package the user would have added to to get the third-party software workign would already be "manually installed" so autoremove wouldnät remove it. So we are really left with the situation where, while istallign something from source code, already knew that a required package was already installed and therefore didn't even try to manulaly install it (as even trying to install already existing package would mark it as "manually installed"). While it sure is possible, it really doesn't sound too likely to happen, especially since it would require the user to at the same time to be skilled enough to manually install software outside of the package management *and* at the same time not understand basic package management or rember what the packages he had to install to get the manually installed program working.

---

### Post by buzzingrobot on 2014-09-12
> **mcduck said:**
> That's the thing, they don't. apt-get autoremove *will not* remove a package as long as any other package still depends on it, and neither will it remove any of the stuff that would break your system (since everything installed by default is marked as "manually installed" and thus is not touched by autoremove.



That has not been my experience.

I've seen autoremove break a system by deleting repository packages installed by the package manager. I've seen deletion of a large metapackage, e.g., kde-full, break a system by removing packages installed before that metapackage was installed.

I'm not arguing that the behavior of either should be altered.  I'm arguing that explicit and specific warnings should be given, not generic warnings and suggestions that something bad *might* happen.

If that was done, then wondering about certain scenarios when something could or could not happen would not be needed. Users would not be expected to know, for example, that removing a non-repo package would cause breakage. The tool would tell them if it that were the case. (Users ought not to be expected to know how a package manager works, much less all its problematic edge cases.)

---

### Post by mcduck on 2014-09-12
Well, I don't think there' any way an explicit and specific warning could possibly be created in many of the situations where autoremove could break something, as they pretty much depend on the package management not knowing about some third-party software, or not being able to figure out what the user really wants. So at the best you'd just, instead of a list telling you that it's going to remove x packages, end with a blinking red text  saying that it's going to remove x packages, please, really, read through them and only clcik yes if you are absolutely sure you want to do this...

Basically, if the package management has any reason to expect that you might want to keep a package around, it's already excluding it from being automatically removed. (Of course you could make it print a reverse-dependency list of every package it would remove, but that would just mean that the user would have even longer list of packages to read through before deciding if they click "yes" or "no").

---

### Post by buzzingrobot on 2014-09-12
You're assuming that third-party packages are always unknown to the package manager.  If the package manager is used to install a package, it knows about it.

The package manager's job is to know the dependencies.  It could list the dependencies of every package an autoremove would delete. It obviously isn't telepathic.  But, it also  has the info needed to warn, for example, that it is about to remove the video driver currently in use.

Ditto removal of a meta-package, which, as I've said, in my experience can remove packages installed prior to the installation of the meta-package.

---

### Post by mcduck on 2014-09-12
listing dependencies wouldn't work, you'd need *reverse-dependencies*, meaning all the packages that depend on the ones you are removing, plus all the packages depending on them, and so on. That will quicly create a very long list of package names for the user to read through, even if you only list the reverse-dependencies that are actaully installed... And then it would *still* rely on the user actually reading though them all and knowing if any of them is somethinghe needs to keep around.

And in the case you mentioned that wouldn't really help, since autoremove won't break any dependencies in the first place, all the reverse dependencies that you have installed would already be in the list of packages apt-get suggests for removing...

---

### Post by buzzingrobot on 2014-09-12
Yes, it could be a long list of dependencies that would be removed, which is all the more reason why autoremove should not do it at all.

Focusing on dependency issues and what, by the book, autoremove should and should not do, obscures the reality that it can remove packages whose removal will break a system. It should either not do that (my preference) or explicitly warn users.

The problem of meta-package deletion removing packages it did not install is equally egregious.

---

