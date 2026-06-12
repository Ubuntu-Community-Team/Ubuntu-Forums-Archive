---
title: "Choosing between Kubuntu, Ubuntu, etc...."
date: 2012-01-13
forum: New to Ubuntu
---

### Post by Lars75 on 2012-01-13
I have seen a a few things mentioned. Kubuntu, Lubuntu, and Xbuntu. I have seen these names kicked around a bit. I have a few thoughts/questions.

1. My laptop is screaming fast. It is also a 64 bit system.  So not to worried about overtaxing it.

2. Are these (Kubuntu, Lubuntu, and Xbuntu) different OS from Ubuntu, or would they run in Ubuntu?

If I decided to run one of these would I have to uninstall Ubuntu? I can already boot to Windows 7 or Ubuntu. 

3. Which is fairly easy for a person with 0% Linux experience to use? I am not familiar with Gnome 2.3 or other older versions.  so I am kind of a blank slate.  While not Linux experienced, I have considerable Windows Experience.  Been using most version since Windows 95.   

4. I am looking for something stable, secure, easy to use/learn, and customize. I like to play Facebook Games, I like Libreoffice, and so far I love Linux. 

5.  I like the idea of administrating the other laptops from my desktop.  All the laptops we have now are Windows 7 or Vista.  I was thinking of a dual boot on all of the laptops.

6.  The OS I choose will go on all laptops.  My wife has an Acer netbook, and I installed and got Ubuntu running on that with no problem.

7.  I installed with Wubi.  However, if i decided to change OS I could do so.  I would do not want to format my computers because there are somethings my family likes to still use Windows for.  

8.  I prefer Chrome, but I love the Thunderbird mail set up.

8. Am I asking the right questions or are there other factors I need to consider.

---

### Post by nothingspecial on 2012-01-13
They are all Ubuntu with a different Desktop Environment. The underlying stuff is the same.

You can install in your current Ubuntu installation but I would recommend a fresh install of your choice simply because each version comes with it's own default applications and you will end up with lots of duplicates and things can get messy. But that is just my preference.

They are all easy to use.

If you have a screaming fast laptop you can try them all in a virtual machine.

They all work nicely together so you don't have to stick to one in your network. I use Ubuntu, Lubuntu and Xubuntu in mine.

You can dual boot with windows. Installing {Ku,Lu,Xu,U}buntu to a seperate partition. Wubi is great for trying Ubuntu but if you are going to be using it a lot you should do a full install to use your system to it's fullest potential.

You can use chrome and thunderbird with any of them.

---

### Post by drmrgd on 2012-01-13
I think it all comes down to a matter of taste.  As nothingspecial says, it's all Ubuntu  with a different desktop environment (DE).  So, basically all the nuts and bolts are the same with just different styles of design.  Some DEs have more bells and whistles, and some are lighter weight (which doesn't seem to be a factor for you).  Due to the way the DE is implemented, some interact with your hardware differently, which may cause some sluggishness and whatnot.  Some are more customizable than others.  Once you get a feel for how to work in Ubuntu (using the terminal, how to install applications, etc.), you'll find that Kubuntu, Xubuntu, Lubuntu, etc. are (almost, but technically not quite) just more decorative than anything.  

My recommendation is to try them all in a virtual environment to see what fits your style and needs a little more.  Once you've installed Ubuntu and tried the Unity DE, you could install Kubuntu-desktop (for example) to see how that one works and whether you like it or not.  Once again, as nothingspecial says, once you decide on one you like the best, a fresh install would be best to avoid duplication and redundant processes.  It's totally not a big deal if you don't.  It's just a little nicer if you do.  

Have fun exploring and playing with the different flavors of Ubuntu.  It's one of my favorite parts of the OS - being able to really tailor the system to fit me, rather than the other way around!

---

### Post by mastablasta on 2012-01-13
> **Lars75 said:**
> 
2. Are these (Kubuntu, Lubuntu, and Xbuntu) different OS from Ubuntu, or would they run in Ubuntu?
THey are different desktop environments (DE) and they do things differently. for example default Ubuntu Uses GNOME under it. GNOME is known for it's simlicity of GUI (graphical user interface). by default Gnome uses Gnome shell. but this simplicity comes at a price as it also means some things are not included in GUI. additionally Gnome for example doens't need confirmaiton of option. it is all done seemlessly. while KDE (found in Kubuntu) for example will need you to always apply changes. KDE has more the look and feel of windows. especialyl with classic menu. However due to it's simlistic nature Gnome is much more suited for beginners.professional users/developers often use it as well. hence there is plenty gnome based (GTK) applications. which by the way can work on other DE as well.

> 
If I decided to run one of these would I have to uninstall Ubuntu? I can already boot to Windows 7 or Ubuntu. 
no. you can run them next to eachother (select which one on login) as it was sdaid if oyu install them next to it you might get applicaitons which duplicate funcitons. for example two network manager, two power manager etc. to me it is easier to test them via liveUSB. once i checked how they look and played arround a bit i uninstall form the USB and install a new one to play with it there.
> 
3. Which is fairly easy for a person with 0% Linux experience to use? I am not familiar with Gnome 2.3 or other older versions.  so I am kind of a blank slate.  While not Linux experienced, I have considerable Windows Experience.  Been using most version since Windows 95.   

first thing to do is forget about windows. Linux is not windows. they will tell you. it's something completely else. windows slowly evolved form desktop system into server like OS. actually they have server versions. Linux evolved frm server OS into desktop OS. so if you think the server way (for example the way things are done in the internet) that is much closer. it helped me.

Like i said the closest look and feel of windows you will find in KDE. However default Xubuntu, Lubuntu are also very easy to use. And can be easilly modified to look like windows. :-) Unity is also good interface. especially if you run the defaul programmes and use it mostly for surifng the internet and such.

> 
4. I am looking for something stable, secure, easy to use/learn, and customize. I like to play Facebook Games, I like Libreoffice, and so far I love Linux. 

Ubuntu is usually stable abotu a month or two after it goes out. LTS editions (next one comes out in April) tend to be a bit more polished. others are considered more experimental. but might work just fine. if for example next LTS version (12.04) works well you can just use it until it's end of life (which is after 5 years). lTS are also often used on servers.
for super stable Linux you would need Debian stable or Red Hat (CentOS is the free version i believe). but they have old applications. and old drivers (remember drivers in linux are often part of kernel). 

Ubuntu based distributions are very stable if you do only security updates.

> 
5.  I like the idea of administrating the other laptops from my desktop.  All the laptops we have now are Windows 7 or Vista.  I was thinking of a dual boot on all of the laptops.

Yeah but i think you can only administer them if they are in linux.
> 
6.  The OS I choose will go on all laptops.  My wife has an Acer netbook, and I installed and got Ubuntu running on that with no problem.

good. make sure to run it live (when bootign from live media - LIVEUSB, LIVECD - choose try it) before you install, so you can see if it all works as it should.
You can use this to create live USB: [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
> 
7.  I installed with Wubi.  However, if i decided to change OS I could do so.  I would do not want to format my computers because there are somethings my family likes to still use Windows for.  

Wubi is ment for testing and not soemthign very stable. to get linux you need about 25-30 GB of disk space and then create a dual boot.  only that empty space will be formated.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

> 
8.  I prefer Chrome, but I love the Thunderbird mail set up.

Chromium the opensource version of Chrome (chrome minus google ad reports) is in the software center. you can also install Chrome if you wish to do so. there are plenty other broswers out there as well. check out the software center.
> 
8. Am I asking the right questions or are there other factors I need to consider.

just  one thing - consider that there are plenty linux distributions. i would just like to say that it would be good to try a few. I would suggetst to try also Linux Mint. their main edition is based on Ubuntu but they developed (and are still developing) their own interface to latest Gnome which is similar in look to Windows. They also use some usefull tools and try to be very user friendly (for example codecs are installed by default, software manager marks importance of system updates with colour and number etc.). 

I use Kubuntu and Debian XFCE stable (for the old maschine old drivers are ok as are older programmes). 

in the end i would say do some testing, play arround with *live *(try it) versions. once you find something comfortable install...

---

### Post by Lars75 on 2012-01-13
Thank you everyone for the advise and input, I do appreciate it.  It seems like I did not even install Ubuntu properly, since I did not partition my drives first.

---

### Post by Lars75 on 2012-01-13
I want to make sure I got the process right before I start.  

1.  I want to partition my hard drive.  This can be done from Windows 7.  I have 154GB free, and I believe that 100GB is going to be plenty.  

2.  I need to find a full version of Ubuntu to install, and burn it to a CD.   

3.  I need to reboot my computer and install Ubuntu on the "new" drive that I created during the partition.

---

### Post by Ms. Daisy on 2012-01-13
Take a look here

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Lars75 on 2012-01-13
That is the site I am using.  Thank you.

---

### Post by Ms. Daisy on 2012-01-13
Sounds good- I was able to dual boot successfully following it.  Post back if you have any questions along the way.

---

### Post by Rainbow_Dash on 2012-01-13
> **Lars75 said:**
> I have seen a a few things mentioned. Kubuntu, Lubuntu, and Xbuntu. I have seen these names kicked around a bit. I have a few thoughts/questions.

1. My laptop is screaming fast. It is also a 64 bit system.  So not to worried about overtaxing it.

2. Are these (Kubuntu, Lubuntu, and Xbuntu) different OS from Ubuntu, or would they run in Ubuntu? **They come with different desktop environments (XFCE, KDE, and LXDE)**

If I decided to run one of these would I have to uninstall Ubuntu? I can already boot to Windows 7 or Ubuntu. **(nope, just log out then choose the environment by clicking on the little gear thingy at the login screen)**

3. Which is fairly easy for a person with 0% Linux experience to use? I am not familiar with Gnome 2.3 or other older versions.  so I am kind of a blank slate.  While not Linux experienced, I have considerable Windows Experience.  Been using most version since Windows 95. **XFCE is pretty basic, and I guess KDE is a lot like Windows. I personally like Gnome Shell and XFCE, and I'm not a fan of Unity**   

4. I am looking for something stable, secure, easy to use/learn, and customize. I like to play Facebook Games, I like Libreoffice, and so far I love Linux. **Always use what works best**

5.  I like the idea of administrating the other laptops from my desktop.  All the laptops we have now are Windows 7 or Vista.  I was thinking of a dual boot on all of the laptops. **That could work, just test their hardware with Live CDs**

6.  The OS I choose will go on all laptops.  My wife has an Acer netbook, and I installed and got Ubuntu running on that with no problem.

7.  I installed with Wubi.  However, if i decided to change OS I could do so.  I would do not want to format my computers because there are somethings my family likes to still use Windows for.  

8.  I prefer Chrome, but I love the Thunderbird mail set up.

8. Am I asking the right questions or are there other factors I need to consider.

Answered your questions above. Hopefully I didn't miss any bold tags. :D

---

### Post by Lars75 on 2012-01-13
I tried to get it to dual boot, but I did not get the "Boot Alongside Windows 7" option.  It kept making me angry.  So I formatted and installed Ubuntu 11.10.  

It will do all the things I need it to do, just not as pretty as I might like.  I will work with the other DEs as I get more experience.  So Windows is gone...forever.  I would like to thank all those who offered advice, input, and links.  They did help.  

I did save all my files to thumb drives before I formatted.

---

### Post by mastablasta on 2012-01-14
> **Lars75 said:**
> I tried to get it to dual boot, but I did not get the "Boot Alongside Windows 7" option.  It kept making me angry.  So I formatted and installed Ubuntu 11.10.  


That could happen if you had too many primary partitions (as it is often the case on preinstalled Win7 computer). you would need to change one into extended by backing u0p the data and reformating it, and then it sould work.

---

