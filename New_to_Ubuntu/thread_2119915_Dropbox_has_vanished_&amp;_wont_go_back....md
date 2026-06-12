---
title: "Dropbox has vanished &amp; wont go back..."
date: 2013-02-25
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2013-02-25
Dropbox has vanished from my Ubuntu install.

It was here a week or so ago that i noticed (I have stopped using Ubuntu lately as Graphic drivers don’t work properly in full screen (another post here still to be solved) so back to dual boot XP).

Anyway, just went to get some files out Dropbox on here , and noticed they were not in the Folder. So i went to the HUD, and typed dropbox. It found all the  files & folders that used to be synced, BUT the Dropbox program has gone.

I just tried to re-install it and just got the following.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nautilus-dropbox : Depends: dropbox but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

No idea how this has happened.
Any ideas of what has happened and how i can correct it.
Many Thanks..... :D

---

### Post by wojox on 2013-02-25
Have you tried: 
```
sudo dpkg --configure -a
```
```
sudo apt-get install -f
```

---

### Post by MadMonkey1966 on 2013-02-25
> **wojox said:**
> Have you tried: 
```
sudo dpkg --configure -a
``````
sudo apt-get install -f
```

thanks for the quick reply :P
i am not very good with terminal (trying to learn)

i tried them and got this back

ian@ian-System-Product-Name:~$ sudo dpkg --configure -a
[sudo] password for ian: 
ian@ian-System-Product-Name:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic-pae blender-openshadinglanguage-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
W: Duplicate sources.list entry [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ian@ian-System-Product-Name:~$ 

Does that help ?

---

### Post by audiomick on 2013-02-25
This is odd, and might explain why dropbox was messing up.

> **MadMonkey1966 said:**
> 
W: Duplicate sources.list entry [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages)

 
Did you do this yet?
> 
W: You may want to run apt-get update to correct these problems



That means do
> sudo apt-get update

The command refreshes the list of packages. You could follow it with
> sudo apt-get upgrade

which ensures that all installed packages are at the newest version. It does not do a version upgrade of the OS.

---

### Post by MadMonkey1966 on 2013-02-25
> **audiomick said:**
> This is odd, and might explain why dropbox was messing up.


 
Did you do this yet?



That means do


The command refreshes the list of packages. You could follow it with


which ensures that all installed packages are at the newest version. It does not do a version upgrade of the OS.

Thanks for the help Mick :D

I ran them yesterday to see if it would help with my Graphic problem i had, but run them now for you lol

ian@ian-System-Product-Name:~$  sudo apt-get update 
***** all normal stuff and ended with *****

Reading package lists... Done
W: Duplicate sources.list entry [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

ian@ian-System-Product-Name:~$  sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  blender-codecs-ffmpeg1.0 libdrm-intel1 libdrm-nouveau1a libdrm-nouveau2 libdrm-radeon1 libdrm2 libopenimageio1.1
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,879 kB of archives.
After this operation, 27.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) precise/main libdrm2 i386 2.4.42~precise~ppa2 [26.9 kB]
Get:2 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) precise/main libdrm-intel1 i386 2.4.42~precise~ppa2 [64.0 kB]
Get:3 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) precise/main libdrm-nouveau1a i386 2.4.42~precise~ppa2 [14.8 kB]
Get:4 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) precise/main libdrm-nouveau2 i386 2.4.42~precise~ppa2 [16.8 kB]
Get:5 [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/) precise/main libdrm-radeon1 i386 2.4.42~precise~ppa2 [25.2 kB]
Get:6 [http://ppa.launchpad.net/irie/blender/ubuntu/](http://ppa.launchpad.net/irie/blender/ubuntu/) precise/main blender-codecs-ffmpeg1.0 i386 1.0.4-0irie1~precise1 [4,271 kB]
Get:7 [http://ppa.launchpad.net/irie/blender/ubuntu/](http://ppa.launchpad.net/irie/blender/ubuntu/) precise/main libopenimageio1.1 i386 1.1.7-0irie1~precise1 [1,460 kB]
Fetched 5,879 kB in 4s (1,396 kB/s)          
(Reading database ... 224696 files and directories currently installed.)
Preparing to replace libdrm2 2.4.42~precise~ppa1 (using .../libdrm2_2.4.42~precise~ppa2_i386.deb) ...
Unpacking replacement libdrm2 ...
Preparing to replace libdrm-intel1 2.4.42~precise~ppa1 (using .../libdrm-intel1_2.4.42~precise~ppa2_i386.deb) ...
Unpacking replacement libdrm-intel1 ...
Preparing to replace libdrm-nouveau1a 2.4.39-0ubuntu1 (using .../libdrm-nouveau1a_2.4.42~precise~ppa2_i386.deb) ...
Unpacking replacement libdrm-nouveau1a ...
Preparing to replace libdrm-nouveau2 2.4.39-0ubuntu1 (using .../libdrm-nouveau2_2.4.42~precise~ppa2_i386.deb) ...
Unpacking replacement libdrm-nouveau2 ...
Preparing to replace libdrm-radeon1 2.4.42~precise~ppa1 (using .../libdrm-radeon1_2.4.42~precise~ppa2_i386.deb) ...
Unpacking replacement libdrm-radeon1 ...
Preparing to replace blender-codecs-ffmpeg1.0 1.0.3-0irie1~precise1 (using .../blender-codecs-ffmpeg1.0_1.0.4-0irie1~precise1_i386.deb) ...
Unpacking replacement blender-codecs-ffmpeg1.0 ...
Preparing to replace libopenimageio1.1 1.1.5-0irie2~precise1 (using .../libopenimageio1.1_1.1.7-0irie1~precise1_i386.deb) ...
Unpacking replacement libopenimageio1.1 ...
Setting up libdrm2 (2.4.42~precise~ppa2) ...
Setting up libdrm-intel1 (2.4.42~precise~ppa2) ...
Setting up libdrm-nouveau1a (2.4.42~precise~ppa2) ...
Setting up libdrm-nouveau2 (2.4.42~precise~ppa2) ...
Setting up libdrm-radeon1 (2.4.42~precise~ppa2) ...
Setting up blender-codecs-ffmpeg1.0 (1.0.4-0irie1~precise1) ...
Setting up libopenimageio1.1 (1.1.7-0irie1~precise1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ian@ian-System-Product-Name:~$

---

### Post by audiomick on 2013-02-25
Ok, the upgrade on looks good, but it seems there is still that duplicate entry.


Wait a bit, I'm going to put dropbox on here to see what should be in the sources list. I'll be back shortly.

---

### Post by audiomick on 2013-02-25
Hmm, puzzled now.

How did you install dropbox, actually? Is it in the software centre on newer Ubuntu versions (it is not on this 10.10 install...), or did you set up a PPA for it or what?

---

### Post by MadMonkey1966 on 2013-02-25
> **audiomick said:**
> Hmm, puzzled now.

How did you install dropbox, actually? Is it in the software centre on newer Ubuntu versions (it is not on this 10.10 install...), or did you set up a PPA for it or what?

Ahhh Dropbox, when i tried to install from Software Centre it came up with an issue, and suggested going somewhere...(cant think now)...on that page i had to type something into Terminal and install it that way (this was ages ago so can not exactly remember)...but it ran fine after that....well, i thought it was running fine...i guess there is a major problem somewhere.

---

### Post by audiomick on 2013-02-25
Ok, it sounds like you installed a PPA for it.

What your system is complaining about is duplicate entries in the sources list file. I am pretty sure it is ok to edit that by hand, so here is what you could try, if you're up for it.

Do
```
sudo gedit /etc/apt/sources.list
```

You will be asked for your password, but I think you are already familiar with sudo.

What that does is open the file sources.list which is in the directory /etc/apt in the editor gedit with root privileges. 

It will look something like this
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://de.archive.ubuntu.com/ubuntu/ maverick universe
deb http://de.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://de.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

What you have to do is go through that looking for two entries that are the same. According to your error message, the entry will be something like
```
http://linux.dropbox.com/ubuntu/ precise/main i386 Packages 
```
It is possible that the two entries will not be in the same place in the file.

When you have found them, you need to disable one of them. You could just delete it, but I am always nervous about deleting stuff out of what is effectively a system file. I would put a # at the start of the line to comment it out, and add a comment that this is the line I have changed. It would then look something like this

```
# this is what I changed to remove the duplicate entry
#deb http://linux.dropbox.com/ubuntu/ precise/main i386 Packages 
```

Save and exit the editor, then do
```
sudo apt-get update
```
again and see what happens.

If that hasn't fixed it, go back and reverse the changes in that file.

If it has fixed it, you might want to go in and really remove the entry you commented out.

---

### Post by MadMonkey1966 on 2013-02-25
Thanks for that Michael :P

Tried that, BUT the only mention i can find of dropbox in the file is here:

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main
deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main

and most entries in the entire file have 2 entries like that. Is that the one you mean ?

---

### Post by audiomick on 2013-02-25
No, that isn't a duplication. As far as I know, one of those will be for the package, and one for the source code. Shouldn't be a problem, anyway.

Ok, I think what I would do at this point is remove everything from dropbox off the system and try and start again.

I guess the first thing would be to move everything out of the dropbox directory on the computer. I'm guessing a bit here, so I don't know what might happen to it.

This is going to, assuming it works, means setting up dropbox on the computer again, but since it is broken I don't see that as a problem.

I would try the command
```
sudo apt-get purge dropbox
```

Assuming that is the right name for the package, this should remove any installation of dropbox and any config files or what ever.

Alternatively, you could try looking for dropbox in the software centre and removing it from there.

The next thing is to remove the source from the package source list in the software center.

Once the system believes it is no longer installed, you could either follow the info here
[http://askubuntu.com/questions/126198/how-to-install-dropbox]("http://askubuntu.com/questions/126198/how-to-install-dropbox")

to set up the repository again, or go to here
[https://www.dropbox.com/install?os=lnx]("https://www.dropbox.com/install?os=lnx")
and install it from the .deb without setting up a package source for it.
If you click on the appropriate (64 bit or 32 bit) Ubuntu link on that page, your download manager should offer you the option "open with software centre" which will start the install process.

---

### Post by MadMonkey1966 on 2013-02-25
Yep, that is the only mention in the file i opened of dropbox (i even used search in case i missed it lol)

okay, i ran that and got this:

ian@ian-System-Product-Name:~$ sudo apt-get purge dropbox
[sudo] password for ian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic-pae blender-openshadinglanguage-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  dropbox*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 224695 files and directories currently installed.)
Removing dropbox ...
Purging configuration files for dropbox ...

The actual Dropbox shared folder that Dropbox creates to put your files in stayed so i deleted that on its own.

I will now try and re-install it...will let you know :)

---

### Post by audiomick on 2013-02-25
Ok, I'll keep an eye out.

Incidentally, did you see this?

> **MadMonkey1966 said:**
> 
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic-pae blender-openshadinglanguage-data
Use 'apt-get autoremove' to remove them....


The package management system found a bit of detritus lying around. It's not critical, but it's not a bad idea to run the autoremove command to clean it up.

```
sudo apt-get autoremove
```

Good luck with the re-install.

---

### Post by MadMonkey1966 on 2013-02-25
Yep, i just run that thanks, have to take note of that command  :)

Also, just to say, when i type dropbox in the HUD, it still shows me my Home folder, but i can not see anything to do with dropbox (even when showing hidden files).

Anyway, let have a go at putting dropbox back on, will get back to you, and thanks for your time :)

---

### Post by MadMonkey1966 on 2013-02-25
okay: followed this on that link you gave me.


[LIST]
[*]Add Dropbox’s repository key
[/LIST]
  sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
  
[LIST]
[*]Add Dropbox’s repository
[/LIST]
  sudo add-apt-repository "deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) $(lsb_release -sc) main"
  
[LIST]
[*]update and install Dropbox
[/LIST]
  sudo apt-get update && sudo apt-get install nautilus-dropbox
  
The first 2 seem to run fine, but after running update & install dropbox, i got all the normal text followed by this at the end again:

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nautilus-dropbox : Depends: dropbox but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

hmmmm this is bugging me now.....im thinking of re-installing Ubuntu, would that solve my problem ??

---

### Post by audiomick on 2013-02-25
> **MadMonkey1966 said:**
> ... have to take note of that command 

Better than that, take note of man. Brings up a manual page for a command.

```
man apt-get
```
for instance, will give you a page listing all the options for apt-get including apt-get autoremove and all the others that have turned up in this thread.

---

### Post by MadMonkey1966 on 2013-02-25
ok, got the man one as well now :)

well i just looked in the software centre again, and it gave me the same error trying to install from there.

BUT, now this is interesting....there is another files above dropbox in there, called

Cloud synchronization engine - CLI and Nautilus extension

so i tried that, and it went through and looks to have installed dropbox.

It is syncing all my files right now so will let you know in a few minutes :)

---

### Post by MadMonkey1966 on 2013-02-25
Well, Mick, i do not know if this is good or bad, BUT all is well again.

That other file from the Software Center, ran fine and all files are synced. I have re-booted and all is still ok.

So if anyone wants any advice, do not use the main Dropbox install from the center as there seems to be an issue with it, but that other one ( Cloud synchronization engine - CLI and Nautilus extension) does the exact job.

Thanks for all you help Mick, your a star :)

p.s. If you are any good with graphics/drivers, have a look at my other Thread here. Someone was helping me but seems to have forgotten me.

Thanks again...Ian

---

### Post by audiomick on 2013-02-25
> **MadMonkey1966 said:**
> 
Thanks for all you help Mick, your a star :)



You're welcome...

---

### Post by MadMonkey1966 on 2013-02-25
> **audiomick said:**
> You're welcome...

Everything is running fine, but there is still an issue with this...

W: Duplicate sources.list entry [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I am not worried, as all is running ok , but would be nice to locate the problem sometime :)

Cheers \\:D/

---

### Post by audiomick on 2013-02-25
I would suggest starting a new thread on that, with a title that reflects the issue. Put a link in it to this thread, so that people can see what has been happening here.

I'm at a bit of a loss as to what is going on there. If there aren't duplicate entries in sources.list, then I don't really know what it is going on about.

You could go and have a look in /var/lib/apt/lists/ and see what you can find there. Maybe this
linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages
is in there twice, or maybe it has duplications in it. Have a look.

---

### Post by MadMonkey1966 on 2013-02-25
> **audiomick said:**
> I would suggest starting a new thread on that, with a title that reflects the issue. Put a link in it to this thread, so that people can see what has been happening here.

I'm at a bit of a loss as to what is going on there. If there aren't duplicate entries in sources.list, then I don't really know what it is going on about.

You could go and have a look in /var/lib/apt/lists/ and see what you can find there. Maybe this
linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages
is in there twice, or maybe it has duplications in it. Have a look.

thanks, i will do after i get my graphic one solved ;)

---

