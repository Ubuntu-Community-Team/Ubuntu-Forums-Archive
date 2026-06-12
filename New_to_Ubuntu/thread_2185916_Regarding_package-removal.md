---
title: "Regarding package-removal"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by nLpPyXR on 2013-11-04
Hello again, I'll probably be making a ton of threads asking about things nobody really cares about due to being prone to poking around a bit. On that note, I'm a recent full-time convert to Lubuntu 13.10 from Windows XP and testing several Linux distros for weeks.

Back in M$-Win, I had a file-shredder called CCleaner which allowed one to free space via overwriting "deleted" data and turning it into actual free space; thing is, certain programs were never removed entirely from you system unless you paid attention. By that I mean, even after going to your Control Panel, removing the program, and deleting the corresponding folder in the "Program Files" directory, there were still traces of whatever you got rid of in %appdata% for example.

Now here's my first question, does (L)Ubuntu **truly** remove a package and all related data when you tell it to? or are there hidden corners where breadcrumbs fall and you have to manually sweep them out of the HDD?

Furthermore, is a file-shredder something a (L)Ubuntu user might want? and if so, are there any available?

---

### Post by Bashing-om on 2013-11-04
nLpPyXR;

Package removal: answer -> yes and no. If one wants a package completely removed one must explicitly tell the system to do so, the system assumes you may have a reason to hang onto customized config files. To remove all files .. in the GUI methods choose to "completely remove"; command line is to use the option "--purge".

File shedder, nope as it serves no purpose as in linux (inodes) when a file is removed it is gone gone, and that space is immediately available to be used. References to that data has been unlinked.

Housekeeping in 'buntu is light and if one watches disk usage - rarely needed
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```
and remove old unwanted kernels and headers pretty well does it.

[INDENT][INDENT]nothing to it, piece of cake
[/INDENT][/INDENT]

---

### Post by oldos2er on 2013-11-05
> **nLpPyXR said:**
>  does (L)Ubuntu **truly** remove a package and all related data when you tell it to? or are there hidden corners where breadcrumbs fall and you have to manually sweep them out of the HDD?

None of the package managers will touch data in the user's home folder, usually stored in "dot files" so-called because a "." prepends their file names, meaning they are hidden. You can see them in terminal with ```
ls -a
``` or in Nautilus with Ctrl-h. If you want these files and/or folders removed you will have to do it manually.

There's a *shred* command you can use in terminal, ```
man shred
``` for more info. If you're looking for something more than that, check out the package *secure-delete*.

---

### Post by newb85 on 2013-11-05
If you use the --purge option with apt-get remove, it will get rid of configuration files I'm the / directory.   Config files in your /home directory, however, are not automatically removed.

---

### Post by nLpPyXR on 2013-11-05
thank you all for your answers. One more question regarding the subject matter at hand:

Say I remove Startup Disk Creator, the XFCE Power Manager that comes with Lubuntu, or any other package via --purge or otherwise, is there any risk of screwing up my system due to removal of related packages other apps might still need/use?

I mean, how safe is it to kill stuff that comes as default (or not) with your install?

---

### Post by Bashing-om on 2013-11-05
nLpPyXR; YUK !

Tearing down is not recommended, as you have surmised there are dependency issues to deal with, removing a  application and the dependencies of one application will most often remove some other(s) application. This may have serious adverse impacts on the operating system at large.

Build up is the way to go ! Once you have some familiarity with linux, install the "core" (minimal install) and add the applications to this basic install as you require/want.

[INDENT][INDENT]building up can be a very comfortable fit
[/INDENT][/INDENT]

---

### Post by nLpPyXR on 2013-11-05
alright noted; once again thank you :)

---

### Post by oldos2er on 2013-11-05
> **nLpPyXR said:**
> Say I remove Startup Disk Creator, the XFCE Power Manager that comes with Lubuntu, or any other package via --purge or otherwise, is there any risk of screwing up my system due to removal of related packages other apps might still need/use?


I'm not familiar with the programs you mention, but sudo apt-get purge <package> should give you a list of packages to be removed, and will ask you to confirm. If I had to guess I'd say it's safe to remove the disk creator app, but removing power management could be problematic. To be sure, you should post the terminal output here and let us take a look at it before committing to anything.

---

### Post by newb85 on 2013-11-05
If another app uses a package, it is a dependency of that package.  If you use apt-get to remove that dependency, it will also use the app that uses it (and warn you first).

---

### Post by nLpPyXR on 2013-11-06
> **oldos2er said:**
> To be sure, you should post the terminal output here and let us take a look at it before committing to anything.

[http://pastebin.com/VVq8MHjC](http://pastebin.com/VVq8MHjC)

I'm guessing that "Lubuntu-Desktop" is rather important and shouldn't be removed... hmm, if only there was a way to make the power manager work properly; I can't seem to get it to not turn off my screen after 10 minutes of inactivity, and I tend to watch a lot of long videos.

---

### Post by ibjsb4 on 2013-11-06
> I'm guessing that "Lubuntu-Desktop" is rather important and shouldn't be removed

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

---

### Post by oldos2er on 2013-11-06
All the *buntu-desktop packages are [meta-packages]("https://help.ubuntu.com/community/MetaPackages") and can be safely removed, however if you plan on doing a version upgrade you will need to reinstall lubuntu-desktop first.

For configuring the power manager, there are some suggestions here: [http://ubuntuforums.org/showthread.php?t=1936683](http://ubuntuforums.org/showthread.php?t=1936683)

You really didn't need a pastebin for listing two packages.  :)  You can copy and paste terminal output into a post here, if it's really long enclose it in code tags.

---

### Post by nLpPyXR on 2013-11-06
> **ibjsb4 said:**
> [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

> **oldos2er said:**
> All the *buntu-desktop packages are [meta-packages]("https://help.ubuntu.com/community/MetaPackages") and can be safely removed, however if you plan on doing a version upgrade you will need to reinstall lubuntu-desktop first.

once again thank you :D

you know, the Ubuntu community alone should be a major selling point towards anyone thinking of making "the big switch".

Questions: what would sudo apt-mark manual lubuntu-desktop actually do? would it prevent the removal of the meta-package or allow me to upgrade without reinstalling lubuntu-desktop?

also, would reinstalling lubuntu-desktop reinstall all those things I'm trying to get rid of? for example the XFCE4-Power-Manager

> **oldos2er said:**
> You really didn't need a pastebin for listing two packages.  :)  You can copy and paste terminal output into a post here, if it's really long enclose it in code tags.

thanks, I'm just used to IRC-etiquette

---

### Post by fantab on 2013-11-06
If you don't like packages that come by default then you should consider using a [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD") and then build your *Buntu from there on. Install only what you need.

---

### Post by oldos2er on 2013-11-06
I'm not familiar with apt-mark, so I'll let someone else handle that.

---

### Post by newb85 on 2013-11-06
The three modes of apt-mark are markauto, unmarkauto, and showauto.  Using unmarkauto to mark it as manually installed will prevent its automatic removal as an unneeded dependency.

---

### Post by urapain on 2013-11-06
If you are using gui packge manager, "select mark for complete removal".  It will list alll the packages that will be removed and give you a chance to change your mind. Look throught the list of things to be removed and just clear the mark if for example a dependancy results in removing the entire desktop.

---

### Post by nLpPyXR on 2013-11-06
> **urapain said:**
> If you are using gui packge manager, "select mark for complete removal".  It will list alll the packages that will be removed and give you a chance to change your mind. Look throught the list of things to be removed and just clear the mark if for example a dependancy results in removing the entire desktop.

thanks but I'm trying to get a good grip of the terminal which is the bread and butter of any Linux distro, plus I already screwed up an Ubuntu install beyond repair by carelessly uninstalling via the Software Center, and I don't plan on doing that with my beloved fresh install of Lubuntu... specially now that it's the only OS on my machine.

> **newb85 said:**
> The three modes of apt-mark are markauto, unmarkauto, and showauto.  Using unmarkauto to mark it as manually installed will prevent its automatic removal as an unneeded dependency.

Actually the terminal says that command is deprecated and one should use sudo apt-mark manual [package] instead. Which I did and then purged the power manager, startup disk creator, pidgin, sylpheed and about three other packages... then I rebooted to see if any real damage had been done and thankfully everything's alright and working just as it did before I removed all that stuff.

I'd still like to know wether or not re-installing the lubuntu-desktop package for an upgrade would also bring back all those things I got rid of though...

---

### Post by oldos2er on 2013-11-07
apt-get has a "dry-run" option so you can see exactly what will occur without actually doing it. ```
sudo apt-get -s install --reinstall lubuntu desktop
``` You might want to pipe the output to a text file, because it might be rather large: ```
sudo apt-get -s install --reinstall lubuntu desktop > lubuntu_desktop.txt

nano lubuntu_desktop.txt
```

---

### Post by newb85 on 2013-11-07
> **nLpPyXR said:**
> Actually the terminal says that command is deprecated and one should use sudo apt-mark manual [package] instead. 

Oops! That's what I get for reading an outdated man page from online on a non-linux system.

---

### Post by nLpPyXR on 2013-11-07
> **oldos2er said:**
> apt-get has a "dry-run" option so you can see exactly what will occur without actually doing it. ```
sudo apt-get -s install --reinstall lubuntu desktop
``` You might want to pipe the output to a text file, because it might be rather large: ```
sudo apt-get -s install --reinstall lubuntu desktop > lubuntu_desktop.txt

nano lubuntu_desktop.txt
```

huh, isn't that handy? :D

thanks!

---

### Post by newb85 on 2013-11-08
> **nLpPyXR said:**
> huh, isn't that handy? :D

thanks!

Yup, and if you don't need to keep the output, you could also pipe the output to the less command, which is designed for displaying lengthy outputs in a scrollable, readable format in the terminal.

```
sudo apt-get -s install --reinstall lubuntu desktop | less
```

This way, you avoid creating a file you then need to delete, and you don't have to call nano/vi/gedit/...

Just another way of going about it...

---

