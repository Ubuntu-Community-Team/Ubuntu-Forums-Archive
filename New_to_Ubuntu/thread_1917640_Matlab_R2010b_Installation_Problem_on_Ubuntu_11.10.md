---
title: "Matlab R2010b Installation Problem on Ubuntu 11.10"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Aoenen on 2012-01-30
Hello, I have a problem about installing Matlab on Ubuntu 11.10 64bit . Also I must add that I am the ultimate newbie, so no knowledge about UNIX systems or coding.

I am trying to follow the instructions here

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

First of all, I am using an ISO mounted with Furius ISO Mount, and when I mount, the app creates a folder called "MATHWORKS_R2010B_iso" at Home directory.

But when [FONT=monospace]I type "[/FONT]sudo /MATHWORKS_R2010B_iso/install" following message appears
"sudo: MATHWORKS_R2010B_iso/install: command not found"

I tried [FONT=monospace]"[/FONT]sudo sh /MATHWORKS_R2010B_iso/install"
And the outcome: "sh: Can't open /MATHWORKS_R2010B_iso/install"

I also tried change directory (cd) to enter "MATHWORKS_R2010B_iso", no problem in that, also shows the "install" on dir, but still it says "can't open".

When I manually click-run on "install", MATLAB setup does not allow installing the software in default dir "usr/local" because of permission problem, most probably because of not being able start with sudo. I said "nevermind", I decided to install Matlab in Home directory, but this time, after the activation is done successfully and launch the software, just the welcoming screen appears then nothing happens. I searched the web about this, and found out that this happens because of license app not starting and the solution is installing MATLAB in default directory, usr/local.

Any help about installing it in default directory is intensely appreciated.

Thanks in advance :)

---

### Post by chipbuster on 2012-01-30
Huh. Well first off,

> 
sudo /MATHWORKS_R2010B_iso/install
will point the shell at a folder in /. Is your folder mounted to the root directory? If not, that might explain why its not finding it. (Basically, I suspect your command is slightly garbled)

If the mathworks folder is in the home directory like you said, go ahead and try >  sudo ~/MATHWORKS_R2010B_iso/install  The tilde (~) at the beginning will point it at the MATHWORKS folder located inside your home.

Also, to run a GUI file browser as root, you can use "gksudo nautilus"

I'm honestly not too familiar with the Matlab program or installs, so I'm afraid I can't help you much more than that.

---

### Post by Aoenen on 2012-01-30
Thanks for the comment, but sadly tilde didn't work.

I am sure that unpacked iso is located in Home Directory (also checked from properties). I also tried manually copy files to a folder in Home dir, still not working. It says
"install: missing file operand"

Also couldnt perform "gksudo nautilus" as well, got an error message because of having no rights on root directory. I defined a password for root, but it didn't ask me for a password on both process to unlock the edit rights.

Maybe I need to reinstall Ubuntu, I really got lost in this :)

---

### Post by chipbuster on 2012-01-30
Hm. Missing file operand. Is there a readme that came with that software?

Also, are you currently the only user on the system? Your first account should come installed with sudo priviledges, and you use your own (personal) password for gksudo. You use the root password for gksu.

> I defined a password for root, but it didn't ask me for a password on both process to unlock the edit rights.

I don't understand what you're saying here. It didn't ask you for a password on what?

Sorry for my slow responses x)

---

### Post by Aoenen on 2012-01-30
In its installation guide, the only info about installing it on Linux is as follows, and I already did all of them.


[LIST]
[*][COLOR=RoyalBlue]**Linux ** &#8212; Insert the DVD into the DVD drive connected to your system and execute the following command:[/COLOR]
[COLOR=RoyalBlue]/*path_to_dvd*/install &[/COLOR]
[*][COLOR=RoyalBlue]If you are installing from downloaded files, extract the installer from the archive file and execute the installer command:[/COLOR]
[COLOR=RoyalBlue]./install[/COLOR]
[*][COLOR=RoyalBlue][/COLOR][COLOR=RoyalBlue]Depending on how your system is configured, you might have to mount the DVD first. Make sure you mount it with execute permissions, as in the following example. Note that the name of the DVD drive might be different on your system.[/COLOR]
[COLOR=RoyalBlue]mount -o exec  /media/cdrom0 [/COLOR]
[/LIST]


Yes I am the only user and when I tried to run ""gksudo nautilus", the terminal didn't ask for the root password (I have defined before), and just reported not being able to perform this task because of not having enough user privileges. That's what I tried to express. Sorry I know I act and talk like a 1st grader with an empty mind, but really I just have to install Matlab and run on Ubuntu.


Thank you for your patience :)

---

### Post by chipbuster on 2012-02-01
Wow. So uh...I could have sworn that I checked this yesterday >.>

No worries about descriptions, its really hard to describe things over the internet as it is, and even  harder when you don't know what to look for (which is generally why you post on forums)

I honestly don't know what to do. Are you using <TAB> completion on the shell? That prevents any typing errors from taking place (to use it, type out a couple characters of the file and hit TAB, the shell will complete as much as it can)

If you are, all I can say is try to burn to a disc or download some other files. Hopefully someone else knows what's going on:I'm not exactly a Linux guru.

---

### Post by Aoenen on 2012-02-03
Ok, thanks anyway, I think I'm going to try with another copy :)

---

### Post by Aoenen on 2012-02-05
I tried with R2011a version, still same problem. Is there anyone else to help me override Ubuntu's security so I can install properly? :)

---

### Post by cheatos on 2012-02-05
Hi,

have you mounted the iso correctly?
I had the same problem with Mathematica, you first need to mount the iso before you can access the filesystem.

Somehow it can't be done by just using Archive Manager, you'll need to type something as follows:
```

sudo mkdir /mnt/disk
sudo mount -o loop disk1.iso /mnt/disk/
```

and then you can ls to the directory /mnt/disk/ where you should find the installer.

Hope this will work for Matlab, too, if yes, please let me know, as I also have a MATLAB CD at home ;)

---

### Post by Aoenen on 2012-02-05
> **cheatos said:**
> Hi,

have you mounted the iso correctly?
I had the same problem with Mathematica, you first need to mount the iso before you can access the filesystem.

Somehow it can't be done by just using Archive Manager, you'll need to type something as follows:
```

sudo mkdir /mnt/disk
sudo mount -o loop disk1.iso /mnt/disk/
```and then you can ls to the directory /mnt/disk/ where you should find the installer.

Hope this will work for Matlab, too, if yes, please let me know, as I also have a MATLAB CD at home ;)

Recently I've found a blog page about an older version, suggesting somewhat close to your solution, and actually it worked, If anyone interested in here's the link
[URL="http://thameera.wordpress.com/2010/10/21/installing-matlab-2008a-on-ubuntu-10-10/"]
http://thameera.wordpress.com/2010/10/21/installing-matlab-2008a-on-ubuntu-10-10/[/URL]

I followed the steps both for Matlab 2010b and 2011a to check, works fine for both of them.

Thank you guys for your help.

---

