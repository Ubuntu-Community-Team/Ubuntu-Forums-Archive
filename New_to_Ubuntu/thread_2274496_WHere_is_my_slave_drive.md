---
title: "WHere is my slave drive?"
date: 2015-04-20
forum: New to Ubuntu
---

### Post by Southron on 2015-04-20
I've had linux for a couple weeks. I've used it about 15 hours mostly surfing. When I first installed it I was able to see my slave drive and its contents, but I cant now. I cant remember where I found it before but I've looked in Home and it isnt there.

can someone help me please (where can I find / navigate to my slave drive?

I have Ubuntu 12 ( I dont know how to find my version, but it is 12. something)

I've searched fotr this but just find answers about terminal. I dont need that just need to see and search, copy and paste etc to the innards of my slave drive like in windows. I was able to do this before

my main drive is all ubuntu, the secondary drive is windows. I just read another forum thread where someone expalined to the person asking where his slave drive was located he may not have permission to see another OS. But I saw it and everything in the drive previously.

---

### Post by dino99 on 2015-04-20
you have many ways to get it:
- from the file manager (nautilus): listed into the left pane
- from gparted or disk-utility
- from a terminal: sudo lshw -l

note that you can use a userfriendly tool called 'synaptic' to know about the packages/changelogs/...

---

### Post by Southron on 2015-04-20
Thanks. I searched for nautilus in the home window (sorry if that word is inappropriate here) and didnt find it but I saw my slave drive listed in the drop down search under location

I'm still learning how to install programs
I ran the terminal command above and got this

Hardware Lister (lshw) - B.02.15
usage: lshw [-format] [-options ...]
       lshw -version


	-version        print program version (B.02.15)


format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information


options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

It doesnt show my slave drive I dont think
I went to download synaptic and there are two ubuntu 12 versions. I can I tell my version?

---

### Post by yancek on 2015-04-20
I think you ran the suggested command incorrectly.  Copy and paste this and show the output:

```
sudo lshw -class disk
```

To find your specific version of Ubuntu, copy and paste the line below into a terminal:

cat /etc/issue

On Ubuntu 12.04, you should see output similar to this:  Ubuntu 12.04.2 LTS \n \l

---

### Post by grahammechanical on 2015-04-20
If you are using Ubuntu 12.04 then you should be seeing icons for drives/partitions in the Launcher. Also as previously suggested if we open the file manager it should list in the left panel of the application window all partitions. And this is the case for every flavour of Ubuntu.

Certainly, the home folder is not the place to look. It is possible to unlock icons from the Launcher. If that is what you have done then use the file manager to open the icon that represents the drive/partition that you are looking for  and when the application window opens an icon will appear in the Launcher. Right click the icon and select Lock to Launcher.

Also keep in mind that the drive will not be labelled d: drive or anything like the way that Windows labels drives. If this is a secondary drive it will be labelled sdb with a number for the partition number. For example, at this moment I am using an installation of Ubuntu in partition 7 of a second hard drive and it will be called sdb7.

Regards.

---

### Post by Southron on 2015-04-20
now my terminal is gone. which means I cant shut down my computer right? does it hurt linux to just hold the power button down until it turns off?

usually its listed in the recent files in Home, and when not I can search for it there. but now I search for it and it doesnt turn up.

I will pin it to the launcher now that I know to if you can help me find it.

---

### Post by Southron on 2015-04-20
is the file manager the file cabinet icon that says files?

It was in the home window and it isnt now and I search for it and it doesnt come up. just like the terminal

---

### Post by Geoffrey_Arndt on 2015-04-20
Yes - it used to be named "nautilus".   It is installed.  Just click on the dash icon (topmost icon in the launcher), and then enter the word files in search field.   You should also drag it to the launcher for future convenience.   You will see all your drives and devices in the left column of files.    When you click on a device or drive, it will be "mounted" and thereby available for files copy, move, etc.

PS:   just goto Youtube and watch 2 or 3 instruction videos on "Ubunty Unity" . . . . this desktop is super easy to use but you should do some minimal watching, reading (und so weiter) . . .

---

### Post by Southron on 2015-04-20
it doesnt turn up when I search for files. it shows the library folders (music, documents, etc ) and a photo 

It did this before with terminal not showing up and I cold rebooted the computer then it showed up again. I guess I will again. Does it hurt the OS like it does windows?

---

### Post by Geoffrey_Arndt on 2015-04-20
if you input the word "files" in the dash (a search program)  . . . it doesn't display a file cabinet at the left side of the search results?

---

### Post by Southron on 2015-04-21
> **Geoffrey_Arndt said:**
> if you input the word "files" in the dash (a search program)  . . . it doesn't display a file cabinet at the left side of the search results?


No in 12.4 the results appear as icons beneath the search bar. TO the left is the launcher (I think in ubuntu its called a launcher. its a vertical toolbar and the file manager icon doesnt show up in it

---

### Post by dino99 on 2015-04-21
> **Southron said:**
> No in 12.4 the results appear as icons beneath the search bar. TO the left is the launcher (I think in ubuntu its called a launcher. its a vertical toolbar and the file manager icon doesnt show up in it

fell free to be curious  :p
you should see a topbar with icons; click on them, one will propose to switch from icons displayed list, to text list; and other settings.
At the beginnings we feel lost because we are not used to that design; but then everything seems natural  ):P

---

### Post by Geoffrey_Arndt on 2015-04-22
OK Southron,

What happens when you click on the dash icon in the launcher, and then type "nautilus" in the search bar?   Do you see a file icon (below the search bar) that can be run upon clicking it . . . or just dragged over to the left into the launcher?    

Another way to check if "files/nautilus" is installed is to go to the Ubuntu Software Centre and in the search field, input "Nautilus".    If it is installed you will see a smallish green check-mark on the program icon.

Bottom line is . . . you almost certainly do have the file-manager installed (no matter what it's official name is now),  AND you therefore want to put it on the launcher.    For knowledgeable Windows OR Linux users, the File Manager program is one of only two or three programs you should always have running in the background, so you can do the common every-day kind of things you need to do (like copy, move, delete, backup files etc.)

---

### Post by Southron on 2015-04-22
> **Geoffrey_Arndt said:**
> OK Southron,

What happens when you click on the dash icon in the launcher, and then type "nautilus" in the search bar?   Do you see a file icon (below the search bar) that can be run upon clicking it . . . or just dragged over to the left into the launcher?    

Another way to check if "files/nautilus" is installed is to go to the Ubuntu Software Centre and in the search field, input "Nautilus".    If it is installed you will see a smallish green check-mark on the program icon.

Bottom line is . . . you almost certainly do have the file-manager installed (no matter what it's official name is now),  AND you therefore want to put it on the launcher.    For knowledgeable Windows OR Linux users, the File Manager program is one of only two or three programs you should always have running in the background, so you can do the common every-day kind of things you need to do (like copy, move, delete, backup files etc.)

"Sorry There is nothing that matches your search" is what I get when searching for "nautilus" from the Dash Home.
"File" turns up four folders (document and music) a picture and a text file. No file cabinet. 

But it used to as I remember seeing it and asking about it here

---

### Post by sammiev on 2015-04-22
You still must have the DVD/USB you used to install Ubuntu, if so boot from that device and see if all of your drives are listed there.

---

### Post by Geoffrey_Arndt on 2015-04-22
Also . . . . if somehow the Files program was uninstalled (by accident or whatever) . . . why not just go into the Ubuntu Software Center and install "Nautilus" again?    It should take maybe 20 seconds to do if you have a fast internet connection.   The files graphical display is the easiest way to see any/all secondary drives, usb sticks, flash cards, etc.

Again, Youtube is a great helper with linux and ubuntu in general . . . watch a view videos.   

Here are the names of a few (of many more) linux channels available on youtube:   

>  AJ Reissig,
>  InfinitelyGalactic,
>  Jay LaCroix,
>  Joe Collins,
>  Matthew Moore,
>  OhHeyItsLou
>  Run Level Zero

You might consider all the people and resources on the web to be "your local computer club" there in the Okies . . .

---

### Post by Southron on 2015-04-24
> **dino99 said:**
> fell free to be curious  :p
you should see a topbar with icons; click on them, one will propose to switch from icons displayed list, to text list; and other settings.
At the beginnings we feel lost because we are not used to that design; but then everything seems natural  ):P

Theres no top bar with icons just when I move my cursor to the top theres  file, edit, view, etc

---

### Post by Southron on 2015-04-24
> **sammiev said:**
> You still must have the DVD/USB you used to install Ubuntu, if so boot from that device and see if all of your drives are listed there.

Yes I just rebooted from the install cd and both the slave drive and the file manager was listed (I forgot to look for the terminal). But of course when I rebooted without the cd they were gone again. 

does that tell you anything?

---

### Post by sammiev on 2015-04-24
> **Southron said:**
> Yes I just rebooted from the install cd and both the slave drive and the file manager was listed (I forgot to look for the terminal). But of course when I rebooted without the cd they were gone again. 

does that tell you anything?

It tells me that possible the installation went south or and update. Did you add any other software from other sources?

---

### Post by Geoffrey_Arndt on 2015-04-24
> **Southron said:**
> Yes I just rebooted from the install cd and both the slave drive and the file manager was listed (I forgot to look for the terminal). But of course when I rebooted without the cd they were gone again. 

does that tell you anything?

Well . . . . try this . . . press these combo keys "ctrl+alt+T".    Do you get the Terminal window?   If so, type "nautilus" and enter.    What does it tell you?  What does it show you?

Do you know how to:

1.   attach thumbnails to your posts?

2.   install or remove programs?

Did you ever try to access the Ubuntu Software Center? . . . it can display all the programs you have installed.  (as can the dash if you know how to use it).

---

### Post by Geoffrey_Arndt on 2015-04-24
OK Southron . . . after re-reading ALL your posts, I finally have an idea of what's going on with your PC.

1.   So you got a used PC with Ubuntu CE on it - - and it is an older version (12.04 LTS),
2.   Seems likely that you tried to update the computer with the latest Ubuntu LTS version which is 14.04,
3.   The update did not work at all  . . . . there were too many changes made to standard Ubuntu in order to make Ubuntu CE (Christian Edition).  It is not able to be updated as a normal Ubuntu PC.

In short, the whole operating system is badly broken now (that's why none of our instructions work for you).    You will have to get a new DVD with Ubuntu 14.04 (or USB stick but that is harder so I suggest you use a DVD instead).

Probably it's even better if you get a lighter version of Linux like "Xubuntu" 14.04 (from the Xubuntu website) and try to install that OVER your existing Ubuntu CE.    Maybe the person who originally had that PC can help you.

Best of Luck . . . .

---

### Post by Southron on 2015-04-25
I tried to update software and the ubuntu version when I got a popup window for them, but they didnt work. I was going to do another thread for that problem.

The above was supposed to answer sammiev 's question below

"[COLOR=#000000]It tells me that possible the installation went south or and update. Did you add any other software from other sources?"[/COLOR]

---

### Post by Southron on 2015-04-25
> **Geoffrey_Arndt said:**
> Well . . . . try this . . . press these combo keys "ctrl+alt+T".    Do you get the Terminal window?   If so, type "nautilus" and enter.    What does it tell you?  What does it show you?

Do you know how to:

1.   attach thumbnails to your posts?

2.   install or remove programs?

Did you ever try to access the Ubuntu Software Center? . . . it can display all the programs you have installed.  (as can the dash if you know how to use it).

I read your most recent answer so maybe this doesnt apply (or just confirms your conclusion) but terminal does come up with the key shortcut and the window with the folder icons shows up as a result when I type "nautilus" and enter. no file manager

I know how to post attachments but having a hard time with installing programs

---

### Post by Southron on 2015-04-25
> **Geoffrey_Arndt said:**
> OK Southron . . . after re-reading ALL your posts, I finally have an idea of what's going on with your PC.


Probably it's even better if you get a lighter version of Linux like "Xubuntu" 14.04 (from the Xubuntu website) and try to install that OVER your existing Ubuntu CE.    Maybe the person who originally had that PC can help you.

Best of Luck . . . .

I just downloaded xubuntu 15.04 that was released two days ago. It fixed everything. 

thanks for all everyones help esp. Mr Arndt

---

### Post by Geoffrey_Arndt on 2015-04-25
Southron, glad it worked out for you!   You gave it the "old college try" . . . ):P

Now, it might be good to enhance your basic skills by reviewing some of the videos from Youtube . . . and for the short run, stick with installing software from only the official Ubuntu Software Center or using a program called "Synaptic" . . . which accesses the official software repositories.    Later you can add software from trusted "PPA's" (personal package archives) . . . but I wouldn't do that yet.

Good Luck and enjoy Linux!

---

### Post by Southron on 2015-04-26
I'm watching them now. I was so glad to get away from MS and now I'll be able to stay with linux

---

