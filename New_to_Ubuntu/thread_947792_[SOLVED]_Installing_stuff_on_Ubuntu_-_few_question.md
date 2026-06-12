---
title: "[SOLVED] Installing stuff on Ubuntu - few questions"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by mogsmar5 on 2008-10-14
These are a number of questions all related to installing stuff. I need to clear a few things up! Please feel free to answer all or just a few questions - there are a lot here! (Sorry if this is a lot to read :D)

I know the basics on installing things on Ubuntu (is this correct?): Programs are installed through packages, usually .deb but occasionally .bin files, or are compiled from source, and are downloaded either as files from websites (or ftp servers) or from repositories, and you add repositories to increase the number of packages available to your package manager. 
My first question is what actually happens when you install something on Ubuntu/Linux? I know on Windows, files are usually copied to C:\Program Files, keys are added in the registry, win.ini etc. What happens in Ubuntu? Is there a registry, or a program files, or can programs be installed anywhere?

Secondly, I would like to know the difference between installing something on Ubuntu or just 'running' it. When I run Vuze I run it from a script in a folder of file; I haven't found a way to actually 'install' it so it is available to the whole system. Or are things not actually installed at all, just added to menus?

Thirdly, what is a package name? When you type something into apt-get, like frozen-bubble or whatever, what stops there from being a conflicting package in a repository you have added with the same name? How do you find out the package name of a package that you have downloaded from a website so you can remove it with apt-get remove?

Thanks in advance!

---

### Post by OutOfReach on 2008-10-14
I'm not excellent at explaining things, so bare with me. :)

In Ubuntu there is no registery, that's a Windows only thing. When you 'install' something in Ubuntu, all your doing really is copying files (from the .deb) to various locations, mostly places like /usr/bin or /usr/share, etc.. I think in GDebi (the GUI used to install DEBs) it lists the files that the package will install.

When you run something, you just run it. Installing is when you copy the files (from the package) to different locations (like stated above) and running it, making the program 'installed'. 

Sorry I can't answer that.

---

### Post by MaxIBoy on 2008-10-14
The really basic, system-critical programs are installed to /bin and /sbin. Programs you add later are installed to /usr.

Put any script you want accessible to the whole system in /usr/bin, then manually add the launcher to the menu if you want (right-click the menu and hit "edit.") 


There's no registry in Linux, thank goodness. That's one of the worst parts of Windows.

---

### Post by aysiu on 2008-10-14
A really quick way to answer your own question: ```
sudo apt-get install *nameofpackage*
sudo updatedb
locate *nameofpackage*
``` then look at the results.

---

### Post by SteveNorman on 2008-10-14
when you download something it does not automatically install. It is simply another file on your computer, I download all my stuff to the desktop so I can find it. Then I move it to wherever it needs to be, then I unpack it and make it executable.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

there used to ba a great tutorial by monkeyblog,,but forces beyond our control seemed to have killed it. If anyone has a copy it would be useful here

---

### Post by porchrat on 2008-10-14
Good God SteveNorman what the heck is that avatar!!  No matter which way I point the screen it keeps staring at me!!

---

### Post by mkrahmeh on 2008-10-14
> My first question is what actually happens when you install something on Ubuntu/Linux? I know on Windows, files are usually copied to C:\Program Files, keys are added in the registry, win.ini etc. What happens in Ubuntu? Is there a registry, or a program files, or can programs be installed anywhere?

i think the posts above answer this one, no registry in linux, files are copied to various designated locations to work properly..to learn more, search the net, lot of tutorials you can find like this one
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html")

> Secondly, I would like to know the difference between installing something on Ubuntu or just 'running' it
when you install a program, there is an executable accompanied with the process, which usually depends on the files copied earlier..
any file can be made executable in linux actually, as long as there is something to be executed..shell scripts for example, but if a file has nothing to be executed, the system will simply display an error msg.
you can make any file executable by changing its mode for the owner, group, or others.

> Thirdly, what is a package name? How do you find out the package name of a package that you have downloaded from a website so you can remove it with apt-get remove?
the downloaded package is a file used for installing the program, but to remove the program, you dont use the package name, just the program name itself..
here are some useful command lines that I use frequently
```
apt-cache show *program-name*
```
displays information about program like its description and its status 
another one to report the status of a specific package/program
```
dpkg -s *program-name*
```
if you are in doubt about the program's name, you can use 
```
apropos *any_keyword_related_to_the_program's_function*
```

---

### Post by SteveNorman on 2008-10-14
> **porchrat said:**
> Good God SteveNorman what the heck is that avatar!!  No matter which way I point the screen it keeps staring at me!!

its a dumbo octopus. they live in the deepest parts of the ocean

---

