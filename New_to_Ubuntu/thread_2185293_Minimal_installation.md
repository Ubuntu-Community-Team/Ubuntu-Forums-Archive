---
title: "Minimal installation"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by Jeffrey Martin on 2013-11-01
I just built a new performance PC and i've been testing Ubuntu the last two weeks, i've familiarized myself with most things and am becoming proficient with the terminal.

Now, my main gripes with Ubuntu are:

[LIST]
[*]Painfully obvious privacy concerns (example: recording keystroked in dash, zeigeist) that you need to opt-out on - Stil don't feel comfortable after opt-out
[*]Pre-installed applications/software (bloat)
[*]Seemingly forced "cloud"/online integration
[/LIST]


I like distros like Arch, where you can choose exactly what gets installed and what software i want -- even the look of the desktop, but it's too advanced for me now.
So i did a minimal install (mini.iso) and installed the ubuntu-desktop package (no recommends), so here are some questions:


[LIST=1]
[*]I'm still experimenting which desktop enviroment i want to use (Currently trying gnome-shell (gnome3)) -- Is it possible to install ubuntu-desktop package ontop of my minimal without unity and manually install a desktop environment of choice?
[*]When using ubuntu-desktop package, or manually installing things, what should i look out for? Are there any privacy / security risks when not installing certain things? Example: I already noticed with the ubuntu-desktop the privacy window is not installed (that you would find on full install)
[/LIST]

How do i best design my partitions? As i understand some people prefer to make seperate partitions for /, swap, /home
My current setup is like this:[INDENT][COLOR=#ff8c00]/dev/sda1 - Windows 7 (for Adobe CC only)[/COLOR]
[COLOR=#0000ff]/dev/sda2 - 115 Gb (mount point "/")  -- Ubuntu[/COLOR]
[COLOR=#008000]/dev/sda3  extended[/COLOR][/INDENT]
[INDENT=2][COLOR=#008000]/dev/sda5 linux-swap[/COLOR][/INDENT]

I would like to know the benefits, and what the best partition design would be. I want to be flexible with reinstalls etc..

I'm also running 2x 3TB disks in Raid 1 (MDADM) for my data, so hopefully if i ever want to reinstall Ubuntu i can just easily rebuild the array in Mdadm, i don't know if the partition design of the OS will help with this?

Any advice you may have is very welcome. I want to perfect everything before i transfer my actual data to the system.

Jeff

---

### Post by newb85 on 2013-11-01
Your privacy concerns are valid, although really things like zeitgeist are there to target your search results more to you for convenience.  

Still, you could easily install Gnome on Ubuntu minimal.  You wouldn't need to mess with ubuntu-desktop.  Just 
```
sudo apt-get update
sudo apt-get install gnome
```
should do the trick.  (FYI, Gnome Activity Journal uses the same zeitgeist engine Unity uses.)

Starting with Ubuntu minimal will also remove unneeded applications, although I think you'll find they're not that difficult to remove from a default install.

As to "forced" cloud/online integration:
If you're talking about Ubuntu One, you don't have to use it, and you can easily remove the client and indicator from the system.
If you're talking about web search results in the Dash, they can be easily turned off.
If you're talking about the package management (installation and upgrades) being tied to the web, I'm afraid that's something you need with any distribution of Linux, unless you're planning to run your machine in a vacuum.

---

### Post by Jeffrey Martin on 2013-11-01
> **newb85 said:**
> Your privacy concerns are valid, although really things like zeitgeist are there to target your search results more to you for convenience.  

Still, you could easily install Gnome on Ubuntu minimal.  You wouldn't need to mess with ubuntu-desktop.  Just 
```
sudo apt-get update
sudo apt-get install gnome
```
should do the trick.  (FYI, Gnome Activity Journal uses the same zeitgeist engine Unity uses.)

Starting with Ubuntu minimal will also remove unneeded applications, although I think you'll find they're not that difficult to remove from a default install.

As to "forced" cloud/online integration:
If you're talking about Ubuntu One, you don't have to use it, and you can easily remove the client and indicator from the system.
If you're talking about web search results in the Dash, they can be easily turned off.
If you're talking about the package management (installation and upgrades) being tied to the web, I'm afraid that's something you need with any distribution of Linux, unless you're planning to run your machine in a vacuum.

Thank you. 

I already have Ubuntu minimal running, i'm just asking how to do it better. It's better to build up than it is to just uninstall things, i want to start clean.

I noticed the zeitgeist engine yes, i will research it more. I don't want my search results targeted. 

I'm talking about the first two points, i think theres a few other examples, but mainly those. I have turned them off. In the full install some things cannot easily be removed, so with minimal you don't get any of it. I did notice the unity dash is blank on minimal, but i'm using gnome-shell now and that does work nicely.

I look forward to hearing more advice  from people, but thank you once more!

---

### Post by deadflowr on 2013-11-01
> [COLOR=#000000] Is it possible to install ubuntu-desktop package ontop of my minimal without unity and manually install a desktop environment of choice?[/COLOR]

No.

unity is a needed dependency of the ubuntu-desktop.

But you can install all the other packages you want.
Here's what ubuntu-desktop includes
[http://packages.ubuntu.com/saucy/ubuntu-desktop](http://packages.ubuntu.com/saucy/ubuntu-desktop)

---

### Post by VMC on 2013-11-01
One of the first things I do is _**[remove zeitgeist]("http://linuxaria.com/howto/how-to-remove-zeitgeist-in-ubuntu-and-why")**_.

---

### Post by Jeffrey Martin on 2013-11-01
Yes i had already looked at what the ubuntu-desktop package contains :)

So basically it would be easier to select the things i want to install from the list (or leave out the ones i don't want), and go from there? -- So not install ubuntu-desktop but just manually install everything?

I assume going the route i just described would also not install zeitgeist? Or is this always installed (only removable)?

---

### Post by ian-weisser on 2013-11-02
> **Jeffrey Martin said:**
> I assume going the route i just described would also not install zeitgeist? Or is this always installed (only removable)?

Unity is designed to work with Zeitgeist. It's a vital component, like the transmission on an automobile.
Unity won't work well without it. You won't be able to use many of the Dash features.
You are unlikely to have much success trying to install Unity without Zeitgeist, nor trying to remove Zeitgeist from Unity.
The Linuxaria article is for Xubuntu, which does not use Unity.

---

### Post by Bucky Ball on 2013-11-02
If you installed ubuntu-desktop on a minimal install you are missing the point of a minimal install. You may as well have installed Ubuntu and not bothered with the mini.

The idea is to cut the dross and avoid bloat and unnecessary apps/packages. You get the kernel with the mini (NO default apps or any apps at all), then install a desktop environment. If you wanted Unity, then you should install Unity, NOT *buntu-desktop anything, and add the apps you want/need as you go.

If you haven't gone to far with it you might be better to do some planning and start again. I would. Choose your desktop environment and make a list of ONLY the packages you are going to use. Then you don't need to opt in or out of anything. You just don't put those things on in the first place. ;)

Who knows, a clean install of Xubuntu might be fine. It doesn't have all the stuff you talk of as default.

---

### Post by Jeffrey Martin on 2013-11-02
Thank you both.

I do plan to use gnome-shell and not Unity. Is zeitgeist only causing privacy concerns in the way they are implemented with Unity or is it present in gnome too?

> **Bucky Ball said:**
> If you installed ubuntu-desktop on a minimal install you are missing the point of a minimal install. You may as well have installed Ubuntu and not bothered with the mini.

The idea is to cut the dross and avoid bloat and unnecessary apps/packages. You get the kernel with the mini (NO default apps or any apps at all), then install a desktop environment. If you wanted Unity, then you should install Unity, NOT *buntu-desktop anything, and add the apps you want/need as you go.

If you haven't gone to far with it you might be better to do some planning and start again. I would. Choose your desktop environment and make a list of ONLY the packages you are going to use. Then you don't need to opt in or out of anything. You just don't put those things on in the first place. ;)

Who knows, a clean install of Xubuntu might be fine. It doesn't have all the stuff you talk of as default.

No - i do understand, i only installed ubuntu-desktop --no-install-recommends, which only installs the basic tools.

And i have every intention of reinstalling multiple times, as i said, i'm thoroughly testing everything before i transfer my actual data to the machine :)

Can anyone chime in on the partition design? Which is the best and allows for hassle free reinstalling? 

I will store all my data on my storage drive, but of course maybe some user/app data needs to be kept during reinstall? -- I am also running MDADM R1 on my storage drive.. Is that an issue when reinstalling?


Bucky, so to be clear: With the minimal install none of the issues i mentioned will be installed to the machine correct? So the dash functionality (keystroke tracking) / cloud integration / etc is only found in the full version...

---

### Post by ibjsb4 on 2013-11-02
> **Jeffrey Martin said:**
> Yes i had already looked at what the ubuntu-desktop package contains :)

So basically it would be easier to select the things i want to install from the list (or leave out the ones i don't want), and go from there? -- So not install ubuntu-desktop but just manually install everything?

I assume going the route i just described would also not install zeitgeist? Or is this always installed (only removable)?

One way I do it is use the mini iso and do a terminal only install.  Then add a display manager and the fallback-desktop with firefox, terminal, synaptic package manager and a file manager.  With this, you end up with a very plain, two panel desktop.  No zeitgeist, no compiz, no unity, nothing else.  After you have a terminal install, the command would be:
```

sudo apt-get install lightdm gnome-terminal synaptic firefox && sudo apt-get install --no-install-recommends gnome-session-flashback nautilus
```

I do not run 13.10, but I think that is the proper command for 13.10.

There is a 100 different ways to do this, this is just mine.  Here's some other ideas:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

---

### Post by Bucky Ball on 2013-11-02
Yep, there are a hundred(s) ways to do it. ;) All depends how you like your scrambled eggs. And the mini install gives you the kernel, you install EVERYTHING else, as suggested. The command that ibjsb4 supplies gives one selection of things to install. I opt for xfce4 as desktop manager and install only the apps I want/use. You would select your own, which is why testing a few out, making a list of what works for you, then doing the mini install is a good plan.

As for partitioning, there are a heap of ways to do that, too. I'll use my setup as an example. I have Win7 and its recovery (and another Win related one) and the rest of the drive is one big extended partition with all Ubuntu related partitions in that.

I always use the LTS as my main squeeze (at the moment, 12.04 LTS minimal install with xfce4 DE), so that is on one partition, and it's swap is there to, both inside the extended partition. Along with that I reserve two other partitions of 15Gb for 'playthings', interim releases or other distros I might want to fool about with. If they break, no matter, I have the LTS to fall back on. 

You can have your /home directory in / or a separate /home partition, but I have opted for this. I have a data partition which I'm essentially using as /home, but it's just not called that. When I do an install I let it create a /home directory inside /, as you do, then delete the directories inside /home - /Documents, /Video, etc. - and instead create symlinks to those directories, and others, which already exist on the data partition. Simple, and this means that all installs are accessing the same data, no duplicates.

Hope you can follow that. If not, just ask. Incidentally, once you have an install, if you have used a separate /home partition and have a swap, any new installs can use them both. Just make sure /home and /swap are ticked to 'use' but NOT ticked to 'Format'. To manually partition, when you get to the partitioning section of the install choose 'Something Else' and that will allow you to manually install and set it up as you like.

Hope that helps. BTW, you are doing the right thing by testing a few things out and making a plan rather than leaping in, creating a dog's breakfast and then spending a week trying to figure out how to fix it up again. ;)

---

### Post by newb85 on 2013-11-02
> **Jeffrey Martin said:**
> 
No - i do understand, i only installed ubuntu-desktop --no-install-recommends, which only installs the basic tools.

I'm not really sure what the point of this is.  If you're going to install gnome3 or a similar Desktop Environment, the basic tools will be automatically installed.

---

### Post by Jeffrey Martin on 2013-11-02
> **ibjsb4 said:**
> One way I do it is use the mini iso and do a terminal only install. Then add a display manager and the fallback-desktop with firefox, terminal, synaptic package manager and a file manager. With this, you end up with a very plain, two panel desktop. No zeitgeist, no compiz, no unity, nothing else. After you have a terminal install, the command would be:
```

sudo apt-get install lightdm gnome-terminal synaptic firefox && sudo apt-get install --no-install-recommends gnome-session-flashback nautilus
```

I do not run 13.10, but I think that is the proper command for 13.10.

There is a 100 different ways to do this, this is just mine. Here's some other ideas:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

I've been messing with various setups today and i noticed LightDM /w unity-greeter installs a whole load of unity dependencies if i am seeing it correctly. The lightdm-gtk-greeter doesn't seem to work well so far. Trying GDM now.

Can you explain the difference between gnome-session-flashback and gnome-session?  And it's supposed to be used in tandem with gnome-shell right? (if you want a GUI)

It *seems* that gnome-session-flashback doesn't work for me (black screen after login) --- whereas gnome-session does work

> **Bucky Ball said:**
> .
 @Bucky Ball
Thank you!

One thing confuses me slighty, with these reinstalls i have been opting "reuse partition" in the partitioner of the install. But on boot MDADM is still installed, (this is good) but i'm just curious why it remains installed as your basically doing a fresh install of mini....

Also, if i understand correctly, this reinstall method is the recommended method when you want to keep whatever is in your /home folder, but what happens when you want to first format the partition before reinstalling, i assume in that case you would want a seperate partition for /home correct?

I have even thought about dedicating an extra SSD to /home and also adding a NTFS partition to that to swap files between windows.. Then your files are completely seperate from the OS'es

I understand your symlink, so your /home resides in / but the actual data within is stored on a seperate partition. Why not just install the whole /home on that partition then?


> **newb85 said:**
> I'm not really sure what the point of this is. If you're going to install gnome3 or a similar Desktop Environment, the basic tools will be automatically installed.

Sorry, that was just my first attempt. I've done min installs today by just adding everything manually -- In any case the ubuntu-desktop without recommends is much slimmer than a normal install

---

### Post by deadflowr on 2013-11-02
> [COLOR=#000000]I understand your symlink, so your /home resides in / but the actual data within is stored on a seperate partition. Why not just install the whole /home on that partition then?[/COLOR]

The method of using symlinks and having home inside the / is the best way to do it for a machine with multiple operating systems.
A separate /home partition on machines with multiple oses can have problems, as the home directory contains user settings and configuration files, which can differ between OSes. Thus causing problems.

If your going to only run one OS, then having the /home in a different place is fine.

---

### Post by Jeffrey Martin on 2013-11-02
> **deadflowr said:**
> The method of using symlinks and having home inside the / is the best way to do it for a machine with multiple operating systems.
A separate /home partition on machines with multiple oses can have problems, as the home directory contains user settings and configuration files, which can differ between OSes. Thus causing problems.

If your going to only run one OS, then having the /home in a different place is fine.

Though i will not access my /home from Win. The only reason i have it installed at all is because i'm forced to in order to use Adobe CC. 
If i understand correctly, the problem would occur if Win tries to use the /home partition for its own files? Or?

What if you dedicate a drive to /home? A small SSD drive is really cheap nowadays!

---

### Post by deadflowr on 2013-11-02
I should clarify, by multiple OSes, I don't include Windows in that.
Windows can't read linux's file systems anyway.
By multiple OSes, I mean someone who has Ubuntu on one partition/disk and then Fedora or something else on another.
Trying to share the home directory in that case can be problematic.

But if you're only running one linux distro, then as stated before, a separate /home is fine.

---

### Post by ibjsb4 on 2013-11-02
> It *seems* that gnome-session-flashback doesn't work for me (black screen after login) --- whereas gnome-session does work

I think what you have is black panels, black on black.

Try to 'Alt + right click' where the top and bottom panels should be until you get a context menu allowing you to go to panel properties.  Then change the background color.

---

### Post by Jeffrey Martin on 2013-11-02
> **deadflowr said:**
> I should clarify, by multiple OSes, I don't include Windows in that.
Windows can't read linux's file systems anyway.
By multiple OSes, I mean someone who has Ubuntu on one partition/disk and then Fedora or something else on another.
Trying to share the home directory in that case can be problematic.

But if you're only running one linux distro, then as stated before, a separate /home is fine.

Thanks for the info.

> **ibjsb4 said:**
> I think what you have is black panels, black on black.

Try to 'Alt + right click' where the top and bottom panels should be until you get a context menu allowing you to go to panel properties.  Then change the background color.

I could try, but what is the difference between the two anyway? gnome-session-fallback vs gnome-session

---

### Post by ibjsb4 on 2013-11-02
> but what is the difference between the two anyway? gnome-session-fallback vs gnome-session 

Really don't know how 13.10 is set up to handle the different sessions.  The two gnome-sessions in 12.04 are set up to run with or without compiz window manager.

---

### Post by Bucky Ball on 2013-11-02
> **Jeffrey Martin said:**
> 

I understand your symlink, so your /home resides in / but the actual data within is stored on a seperate partition. Why not just install the whole /home on that partition then?

Ah ha. Because if the data partition you are linking your /home directory directories to is NTFS ... Windows can see everything in there, too! If it was a Ubuntu EXT* partition, Win has no idea what they are. ;)

And yes, this method is best for machines with multiple OSs. If you have just one OS, a separate /home partition is rule of thumb for mine. That way, install breaks, just kill it and reinstall without going anywhere near you /home partition (and if it is a different drive, you can take that out to be certain, but always backup first anyways ...).

Which all means that:

> **Jeffrey Martin said:**
> I have even thought about dedicating an extra SSD to /home and also adding a NTFS partition to that to swap files between windows. ... becomes redundant as you only need one NTFS /data partition, not /home (EXT*) and /data (NTFS), and,

> **Jeffrey Martin said:**
>  Then your files are completely seperate from the OS'es

... yes to that! Which, for mine, is a good thing and I wouldn't have it any other way, personally. But some might not have the space to do it that way, of course. ;)

---

### Post by Jeffrey Martin on 2013-11-02
> **Bucky Ball said:**
> Ah ha. Because if the data partition you are linking your /home directory directories to is NTFS ... Windows can see everything in there, too! If it was a Ubuntu EXT* partition, Win has no idea what they are. ;)

And yes, this method is best for machines with multiple OSs. If you have just one OS, a separate /home partition is rule of thumb for mine. That way, install breaks, just kill it and reinstall without going anywhere near you /home partition (and if it is a different drive, you can take that out to be certain, but always backup first anyways ...).


I don't want Win to read anything :P

Okay, i think it will make sense to seperate /home to a partition, but it can also be a seperate drive right? (EXT* ofc.) -- Also, i do understand the symlinks but this is if you want to work with multiple linux installations right? Can you point me to some material to read up on this, so i can find out exactly in what way the multiple installs will conflict the /home folder.

My best install thus far has been mini with these packages:
gnome-shell
gnome-terminal
gnome-session
gdm
nautilus
google-chrome

All installed with --no-install-recommends, if i did not append this then it would start installing alot of things from Unity (could also have been due to lightdm).
Could not get LightDM to work, atleast it would work but after login it would just be a blank screen, it would only work if more of Unity was installed, so i opted for GDM which is recommended with gnome-shell and it seems to work well.

One thing i still can't find out though is why MDADM remains active/installed throughout my reinstalls, is it included in mini.iso? I'm fine with it, just curious --- I'm running 2x 3TB data in RAID1 on mdadm..



> **Bucky Ball said:**
> 

... becomes redundant as you only need one NTFS /data partition, not /home (EXT*) and /data (NTFS), and,


Unsure what you mean here, where is /data? Are you saying there is already an NTFS partition by default?

What i was suggesting would be this: 
Add an extra 120GB SSD drive to PC, then create two partitions on it, one for /home EXT4 say 80GB and then the second NTFS 40GB, this then could be used to swap files between windows.
I know you can also mount the windows folder but i recently read somewhere that it's not recommended

Might not make sense though, since i could imagine that the files would write/read much faster if they are on the same SSD/disk as the OS is running on, but again, also not sure here..
I have a 256GB samsung PRO SSD but it's not really that much if you consider how much Adobe, Autodesk, Windows and various other stuff takesu p.

---

### Post by Bucky Ball on 2013-11-02
What I mean is that /data (example name) is the 40Gb NTFS windows swapping data partition you are talking about.

No, there is no NTFS partition by default. You create your 40Gb data partition. What I mean is:

* When you install Ubuntu, just let it put a /home directory inside /, not separate partition;
* Open the /home directory and delete the empty folders in there, Documents, Video, etc. (or you can just copy the lot onto the empty NTFS 40Gb partition you created earlier);
* DO NOT delete or copy over /lostfound or any hidden directories from /home (which you won't unless you click CTL+H to see them anyway);
* Create symlinks in the /home folder you have inside / which link to the directories you have copied/created on the NTFS 40Gb /data partition.

Voila. Now whatever you put into the directories while in Ubuntu, although they appear to be in your /home folder, will actually end up in the target directories on /data, an NTFS partition which can be read by Win or Ubuntu! ;)

With a minimal install you are not going to need much more than 15Gb partition (less actually, I have never used more than 15Gb for any install) so the rest you can just make as an NTFS partition to link your /home directories to, if that's how you wanted to go. You can always shrink the NTFS partition later if you want more small partitions for more installs.

Hope that helps and makes sense. ;)

No big deal mounting the Windows partition (you say folder but think you mean partition) but not much point, really. If you have the NTFS data partition, just put all personal Win stuff in there to so Ubuntu can access it.

---

### Post by newb85 on 2013-11-04
Bucky Ball's approach is pretty straight-forward and effective.

I've heard, though I've not experienced for myself, that making changes to files on a Windows partition (one with Windows installed) from Linux can cause problems.

---

### Post by Bucky Ball on 2013-11-04
> **newb85 said:**
> I've heard, though I've not experienced for myself, that making changes to files on a Windows partition (one with Windows installed) from Linux can cause problems.

You might be getting this mixed up with resizing the Windows partition with Linux tools, Gparted for instance. That's correct, don't do it. But the Win partition is an NTFS partition like any other when it comes to just looking at the files from Ubuntu. You can mount the partition and read and write to it without issue. Just don't fiddle with the system files, as you wouldn't while in Windows, and resize the partition the Win OS is on with Windows tools only. 

Rule of thumb for resizing partitions? Win tools for Windows partition, Linux tools for Linux partitions. ;)

---

### Post by Jeffrey Martin on 2013-11-04
Thanks again, i have spent time testing everything you mentioned and i have some new questions.

When placing /home on the NTFS partition (which Win can read), are you not risking -- in a worst case scenario -- that Win could corrupt data (virus, or something else..), Or fragmentation even?

So if i get it right "/" is only used for the system itself, any software you install etc, the user specific data (configurations) and media is going into "/home" by default. Now since i have dedicated drives for my data i imagine i will not put much in /home as any files placed there will most likely be temporary before i archive or delete them.
[LIST]
[*]How big should i make "/" partition, even if you start installing "heavier" software packages like blender, aptana, and other tools how much will you need?
[*]I can just delete the /home/.. folders i don't want to use right? I think i will only symlink and use /Desktop, /Downloads since i already have dedicated folders to movies/music/video/documents on my data drive.
[/LIST]

I would like to setup my "final" system over the next days, but i'd like to do what you did and have an extra partition to put an extra install of Ubuntu (or any other distro)  to mess around in, so i can keep my primary working installation completely clean.
How should i set up the partition here? Will any extra linux distro you install need it's own swap partition or can they all share one? (I have 16GB ram so i don't need much swap space) -- Should swap always be last in the partition scheme?:

[ATTACH=CONFIG]247558[/ATTACH]

I've sort of stuck /data and linux sandbox at the end i don't know where they are best placed.
Also note that i made /data 100GB (logical?), if you say the primary ubuntu will be very hard to go over 30GB even if you install heavy software apps, then i would rather have a large /data partition.
As i said i suspect my /home symlinks will take up very little space, but sometimes i need to move large volumes of data to work on in Windows.


Some misc questions:
Should i encrypt /home or my ubuntu install?
Logical partitions are always grouped as extended, does that make sense? I'm trying to understand how it works.

When i first did my windows install it made 3 win partitions, i think one boot, one primary and another misc. But then i reinstalled everything and setup an NTFS partition in gparted before installing windows, now Windows is only using 1 partition flagged as "boot". Strange?

---

### Post by Bucky Ball on 2013-11-04
To make it simple ...

Yes, /home DIRECTORY does exist in /. You just let it default there. So when you install programs all settings files go there, in the /home directory on /.

As you already have data drives/partitions, the job is made easy, because, for example, when you look in the /home directory inside / and see the /Documents folder (which will be empty after install), you simply delete that and create a symlink to the /Documents directory (or whatever you've called the folder where you keep your documents) which exists on your data drive. 

So your program settings exist in /home directory in / (and if you click CTL+H you'll see them) but the other folders are dummies (they have an arrow to signify they are links, not real folders, to the target folders, wherever they may be). Better example is probably /Videos, which is a default folder in /home. Delete that and instead create a symlink to your existing /video folder on the data drive. 

Incidentally, the /Desktop folder CANNOT be a symlink anyway and MUST remain in /home, whether it is a /home directory or partition. 

Clearer?

You probably don't need more than 20Gb for /, but maybe go for 30Gb because I am unsure how much a full Ubuntu install has swollen since I did one (was using Xubuntu but now use a minimal install which takes up less than 10Gb on a 15Gb drive). As you don't have personal data on /, you are not going to need a lot (probably 20Gb would be fine, but you could expand later if required).

Rule of thumb is to stick /swap at the end. Any other installs will happily use the same /swap (this also applies to /home if you had a separate /home partition, but you can just link to the existing folders, same as you're doing with this install). Mark the /swap partition to 'use' but NOT to format for further installs. 

/ (Ubuntu install) does not need to be on a primary partition. Everything but Windows can happily live on logicals inside an extended partition. For this, you make the rest of the drive an extended partition and create logical partitions inside this (you can do all this if you hit 'Something Else' during the partitioning section of the install and partition manually).

Symlinks contain nothing and are miniscule (I'm talking 24 bytes!).

Yes, that is strange about Windows using the one partition. If it works I suppose it's fine. I thought the other two were for recovery or some such.

As for Win corrupting data on the NTFS partition, that would have happened whether you were sharing the partition with Ubuntu or not. I personally have an EXT* which pretends to be /home to three installs at the moment and an NTFS /Misc which I share with Win (when I have to). You can mix and match for whatever suits, really. Make symlinks to whatever you need to and delete them if you don't want them later.

Okay, don't think I've missed anything but let me know if I have. Hope that helps. ;)

---

### Post by newb85 on 2013-11-04
> **Bucky Ball said:**
> You might be getting this mixed up with resizing the Windows partition with Linux tools, Gparted for instance.

No, I'm certain it was about files on Windows partitions, not the partitions themselves. But then, I don't know the credibility of the source.

---

### Post by Bucky Ball on 2013-11-04
Well, a Windows partition is NTFS, so that would apply to any NTFS partition, and it doesn't. Ubuntu quite happily reads, and writes to, NTFS (and FAT) partitions. ;)

---

### Post by verymadpip on 2013-11-04
Hi there.
Sorry to interject on this, but I've heard what newb85 has heard.
 IIRC  the "issue" seemed to be with related to* writing to* NTFS partitions.


If that's hogwash this is awesome news :D

Again, sorry for the hijack.

---

### Post by Jeffrey Martin on 2013-11-04
Thanks again, i'm learning alot from this.

I think i will not create symlinks to my data drive, i would rather access that manually. What i will do is keep Desktop, Downloads, Documents at minimum and delete the rest.

I am also using a minimal install, but yes, it's good to keep some headroom.

> **Bucky Ball said:**
> Rule of thumb is to stick /swap at the end. Any other installs will happily use the same /swap (this also applies to /home if you had a separate /home partition, but you can just link to the existing folders, same as you're doing with this install). Mark the /swap partition to 'use' but NOT to format for further installs. 


Alright, so then the question is, should the swap come after both linux partitions, yet before the /data? So:
Win7 -- Ubuntu -- Linux sandbox -- Swap -- /data    Or rather all the way at the end after /data?

Will check that setting, so far my swap has been formatted on every reinstall as seemingly required by the installer.

> **Bucky Ball said:**
> / (Ubuntu install) does not need to be on a primary partition. Everything but Windows can happily live on logicals inside an extended partition. For this, you make the rest of the drive an extended partition and create logical partitions inside this (you can do all this if you hit 'Something Else' during the partitioning section of the install and partition manually).

As far as i can tell you cannot manually create an extended partition, the swap is automatically logical and when i check it in gparted it's automatically grouped under "extended". So i assume the extended partition is automatically generated when you add logicals? 
Any difference if you make it primary anyway? Doesn't matter at all?


> **Bucky Ball said:**
> Yes, that is strange about Windows using the one partition. If it works I suppose it's fine. I thought the other two were for recovery or some such.

I thought so too but i really don't care what happens to my windows partition, as i said i'm only running it to use Adobe.

> **Bucky Ball said:**
> As for Win corrupting data on the NTFS partition, that would have happened whether you were sharing the partition with Ubuntu or not. I personally have an EXT* which pretends to be /home to three installs at the moment and an NTFS /Misc which I share with Win (when I have to). You can mix and match for whatever suits, really. Make symlinks to whatever you need to and delete them if you don't want them later.

OK, because so far we have been talking about a single NTFS partition /data which is shared by both ubuntu for /home and to exchange files with Windows. 

What i would rather do then, is just make that /data partition EXT4 (EXT4 is the most efficient right?) -- and then just mount the windows partition and put the files i need to exchange in the documents folder.
To be completely clear with you, i don't plan to store anything on the windows partition, it's only when i'm working on something, then i will archive it on my data drives from the Ubuntu install.

Would like to hear your thoughts on that.


Only thing you didn't mention was about encrypting (/home etc) which is asked in install, but thank you so much so far!!





> **newb85 said:**
> No, I'm certain it was about files on Windows partitions, not the partitions themselves. But then, I don't know the credibility of the source.
Aslong as only the Windows partition is affected and not the linux i don't care at all ;)

---

### Post by Bucky Ball on 2013-11-04
Minimal install? Mine is currently using just under 8Gb. You won't need more than 15Gb I shouldn't think. (I have never installed on a partition over 15Gb, even when I used full blown Ubuntu, but that was back in 10.04 from memory, or perhaps 8.04 ...

Extended partition will not be created automagically when you create logical drives. You need to do it manually. Just stick /swap at the end of the physical drive, after everything. This convention comes from when drives were slower: the fastest part of the drive is first partition - closest to the middle - slowest the outer edge, so you want the fast bit for data processing and the slow bit for the rarely used /swap, or in Windows, pagefile (yes, Windows does allow you to put the pagefile somewhere other than the Win install partition). Doesn't matter so much now but nice to keep it out of the way anyhow (and that is still the slowest part of the drive). 

Note: /swap is actually a linux-swap partition, doesn't matter if primary or logical. 

I assume the extended partition was there to start with. No diff making it primary but be aware, four primary partitions is the limit on one physical drive (EFI overcomes that of late, a Win thing, but I know nothing about it). Therefore, don't go above that to be safe.

Sure, you can keep documents in the Win documents folder, but one of the main ideas of keeping valuable personal folders elsewhere (another hard drive if possible and even more pertinent with Windows) is if the OS crashes it doesn't effect your personal files in anyway. They are safely away from the OS partition. If you need to reinstall for any reason and forgot to do that backup yesterday, then whatever you have stashed in /documents in Win (or /home/user/Documents in /) is gone. 

Encrypting /home? Can't help, sorry. Never used encryption (I'm the only person that uses the machine and know nothing about that, either).

PS: Choose 'Something Else' and manually partition, untick the 'Format' box next to /swap but set it to 'Use'.

---

### Post by Bucky Ball on 2013-11-05
Thought the attached pic might give you some ideas.

sda1 = Win boot stuff
sda2 = Win partition mounted in /media
sda3 = Extended partition. Most things there are self-explanatory via the labels and mount points, but;
sda5 = an old 10.10 I should get rid of (which was installed using sda6 as separate /home partition)
sda10 = Ready for a plaything install
sda6 = 10.10s /home partition, but I have the directories in the two 12.04 /home directories symlinked to the existing 10.10 /home directories in there
sda12 = My main mini install
sda11 = a partition ready for Linux From Scratch which has nothing on it yet
sda9 = the partition I use to share with Win

And that's just about it. Don't get confused about the two 12.04 installs symlinking to the 10.10 /home folders in sda6. That was for convenience and has nothing to do with your setup. You could use the /Misc (sda9) partition and link to that if you wanted. Whatever suits. 

PS: They are all using sda7 as /swap. Good luck.

---

### Post by Jeffrey Martin on 2013-11-16
Hi Bucky,

Thanks again for your insights. Sorry for the seemingly late reply but i've spent the time testing and reviewing things.

I even spent some time digging into GPT and UEFI but i went back to MBR in the end because it's just a bit too complex for what i want to do at this point.
The minimal CD doesn't allow for UEFI booting and that means it's installed in legacy and you have to go fix grub using boot-repair, which seems problematic.


So i'm setting up my final stuff now, will report when successful

Thanks again!

---

### Post by rumpek on 2014-02-08
> **ibjsb4 said:**
> One way I do it is use the mini iso and do a terminal only install.  Then add a display manager and the fallback-desktop with firefox, terminal, synaptic package manager and a file manager.  With this, you end up with a very plain, two panel desktop.  No zeitgeist, no compiz, no unity, nothing else.  After you have a terminal install, the command would be:
```

sudo apt-get install lightdm gnome-terminal synaptic firefox && sudo apt-get install --no-install-recommends gnome-session-flashback nautilus
```

I do not run 13.10, but I think that is the proper command for 13.10.

There is a 100 different ways to do this, this is just mine.  Here's some other ideas:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9)

Hi ibjsb4,

I downloaded 13.10 mini.iso and used your command string above, but it installs a lot of stuff which I think is part of lightdm, e.g. lots of account-facebook and other crap.

Also, after rebooting the OS, I get the lightdm login screen, but once I login nothing happens.

Are you still using the string above to create your minimal Ubuntu install and what if anything do you configure after installing those packages to make it work?

Thanks.

---

### Post by buzzingrobot on 2014-02-08
Zeitgeist has been around for a long time.  It's the Gnome approach to desktop search. By itself, it doesn't send local queries anywhere.

The tools that forward queries in Unity can easily be blocked/removed if someone wants to use Unity but avoid them.

Some non-Canonical code packaged for Ubuntu has dependencies on a couple of Unity libraries, so an over-zealous effort to remove all things Unity will break them. Those libs, for example, are present in Mint.

(Packages, like lightdm, have dependencies that will be pulled in if you install them. The alternative is to use a different package, with different dependencies, for the same task.)

---

### Post by ibjsb4 on 2014-02-08
> **rumpek said:**
> Hi ibjsb4,

I downloaded 13.10 mini.iso and used your command string above, but it installs a lot of stuff which I think is part of lightdm, e.g. lots of account-facebook and other crap.

Also, after rebooting the OS, I get the lightdm login screen, but once I login nothing happens.

Are you still using the string above to create your minimal Ubuntu install and what if anything do you configure after installing those packages to make it work?

Thanks.

Hi rumpek

Did flashback install?  I find this confusing in 13.10.  Seems to be called both flashback and fallback in 13.10.

[http://packages.ubuntu.com/saucy/gnome-session-fallback](http://packages.ubuntu.com/saucy/gnome-session-fallback)

Two other possibilities here.

#1  Its there, you just can't see it :)  This has happen to me in the pass, your screen is set to black on black.

Alt + Right-click on the top of the screen and see if a context menu will popup, allowing you to change the background color.

#2  Lightdm is not set to gnome-session-flashback or fallback (session name).  You may need to edit /etc/lightdm/lightdm.conf

[https://wiki.ubuntu.com/LightDM#Change_the_Default_Session](https://wiki.ubuntu.com/LightDM#Change_the_Default_Session)

Take a look @.conf first, changing it to the wrong session would be bad :)

And yes, lightdm is a large package (about 300M).  I used it here because this will cover all equipment.  You can also run without a display-manager using startx.  That will take up about 100M.

As for facebook showing up; this has not happen to me.  Did you sync the browser to another one?

---

