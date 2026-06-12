---
title: "Best basic intro to Ubuntu needed"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by gertcher on 2012-11-16
I know my way around a computer. Built a number of them. Been using DOS, Windows 3, 3.1, 95, 98, XP, 7. Tried Ubuntu 10.something and dump it.

Currently using Ubuntu 12.10 on:
Samsung R730
4Gb Ram
Core i3 2.53 Ghz x4 core.

I am still using 3 other computers with a version of Windows on them, but hope to eventually have a version of Linux on all of them soon.

With all this past knowledge, with Linux it is worthless. I only found the command line a few weeks ago. Cannot make any sense of Linux command structure/language.  I understand 'c:' in DOS, but cannot find the Linux equivelent. Don't know what 'sudo' means. Cannot find a publication that will spell out in very simple terms what I can do with the Linux command line.

Sometimes I think Ubuntu is not polished enough, and some parts are definitely very clunky compared to the Windows equivalent. I find I need to meddle with code - defiantly not my strength - far too often.  I am trying hard to like Linux, but would much prefer it worked correctly all the time without my need to use a forum for every little tweak

Should go and wait for the next major upgrade, such as Ubuntu 14, or 16, or stay? Is there some real help I can get stuck into?  Would like to read it as a PDF, or an up to date book.

Thanks  Greg

---

### Post by 73ckn797 on 2012-11-16
Have a look here? [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by deadflowr on 2012-11-16
[http://ubuntu-manual.org/]("http://ubuntu-manual.org/")

---

### Post by Kevin McCready on 2012-11-16
It's definitely worth learning some basic commands for the terminal. Most useful for me is using bash history via:
ctrl-r
type the beginning of command you want
ctrl-r again until your command comes up

My system"

unetbootin  for making bootable linux USB stick
pdf reader = evince (not helpfully named Document Viewer)
clementine for recording off internet stream
jack for cd ripping 
libreoffice-writer (closer to Microsoft word functionality and much better than abiword or openoffice)
Dolphin as File Manager (file manager (PCManFM 0.9.9) is awful and slow (sorry guys)) 
smplayer (need to install PulseAudio Volume Control and then select Sound Recorder)
leafpad (brilliant little text editor for HUGE text files)
gnumeric (spreadsheet)
ibus-pinyin (for chinese - it needed tweaking)  not ipin sw
clipit (so that stuff cut to clipboard buffer is available after I quit the application)
fbreader for epub files
for my ctrl-alt-? keybindings I tweaked 
~/.config/openbox/lubuntu-rc.xml 
to add in the <keyboard> section: 
    <keybind key="C-A-[your shortcut key]">
      <action name="Execute">
        <command></command>
      </action>
    </keybind>

---

### Post by BertN45 on 2012-11-16
I has the same background as you. One of the things that is important is knowing the file structure of Linux. The root is the main directory of the partition and it contains the OS Folders and two other important folders "home" and "media". You go to it clicking "File System".

The folder home contains a directory/folder for each user. Unfortunately that user folder say "bert" is also called "Home" in the built-in file manager bookmarks/places. Many folders and files here are hidden and they contain the settings of the applications. Press CTRL+h if you want to see them. It is comparable with what windows is doing.

The other folder is "media" and that is were you can find the CDs/DVD/s and other partitions IF they are mounted. For instance /media/hp-data is my d: and /media/floppy my a: floppy drive. They are mounted at the moment you click them in the file manager or if you insert a CD/DVD/floppy. If you want to mount a partition (or a network drive) at boot time, you have to edit the file /etc/fstab. There are many examples to be found in the internet. Network Drives are mostly mounted in Home in the hidden folder ".gvs". They are easily connected using the file manager File->Connect to Server. There are some GUI based utilities to assist you, e.g Gigolo (using .gvs) or the Storage Device Manager (modifying /etc/fstab). 

Drives are indicated as sda, sdb etc. And the partitions on sda are sda1, sda2 etc. The SWAP partition is mostly sda5 and the logical partitions in the extended partition start with sda6. If a partition has no label it will be mounted as e.g: /media/sda2

You also have to realize that Linux is more stringent about security and consequently about file permissions and most of the time you will have to spend some extra time to find out how to mount a partition for all users of the system. 

Have fun.

---

### Post by 3rdalbum on 2012-11-17
I really have the opposite background to you. I'm a fairly long-time Linux user, who finds that they have to work with Windows occasionally, and I'm lost at each step.

Linux is pretty easy really, it's just different to Windows. I'm sure Windows is easy too, but I don't find it so.

If you're finding you have to use the terminal a lot then you're probably going about things the wrong way. What tasks are you trying to perform on the terminal?

"Sudo" is a lot less complicated than it seems. In all modern operating systems including Ubuntu, the regular user cannot make system-wide changes that would affect any other users of the computer. In Ubuntu, Mac OS X and Vista and above, you run as a regular user and can't make system-wide changes... unless you specifically run a program or command as administrator. In Linux, the administrator account is called "root", and you can elevate your privileges to "root" temporarily by use of Sudo.

A simple test for you. The "whoami" command simply tells you what user account the command was run as.

```
whoami
sudo whoami
```

The first will return your username. The second (the one with 'sudo') will return "root". If you put 'sudo' before any command, the command will be run as root and will be all-powerful.

My advice really is just to hang in there; you may also find benefit to join a Linux User Group or even just sit in on their meetings for a bit, and see what you pick up. We were all newbies once.

---

### Post by gertcher on 2012-11-19
Thanks to everyone's help so far.

> I really have the opposite background to you. ''''''''''''''''''''. What tasks are you trying to perform on the terminal?To be correct I am not trying to use the command line. I feel I am being driven to it because I cannot find a GUI to do the task I need. Because I do not understand how to use the command line I am getting know where and this is what is stopping me migrating Ubuntu across all my computers.

Currently theses are my major head aches:
I loaded 12.4 from a CD, eventually it worked perfectly, my wireless Network Connection (NC)was steady at 125Mb/s,and often went up to 145Mb/s. I upgraded - an auto procedure by Ubuntu - to 12.10. It went very smoothly and I did not see any malfunctions at all, and saw a few added and useful tweaks. Soon after I noticed my NC was down to 54Mb/s and often as low as 10Mb/s. Everything about my NC has been constant - location, equipment, method of use - all exactly the same as before the upgrade

So, since the upgrade I have been looking how to fix my NW speed unsuccessfully. You might say I need to update the drivers, I wish. In Windows it would  not be a problem, I cannot find any GUI software loaded or downloadable to do the job. Samsung don't list Linux drivers.

I use ThundrBird, I like it a lot, prefer it to Windows Outlook. What I hate is its lack of auto capitalisation at the start of a sentence, and its lack of auto spelling correction and replacement as I type.

I understand that Ubuntu is far more security enabled compared to Windows. I don't need it, don't want it, cannot switch it off. For instance, the computer starts up and does not ask for an ID, good. I go away for 15 minutes and have to log in when I get back. I start an internet cession and it flags for a password. I can clear it by pressing cancel, but I cannot get rid of the flag.

When I start up I arrive at the work space. How do I get anything to start automatically? I would like Chrome to start automatically.

Files. I have never seen anything so clunky, The shape and design of the icons, the font, the almost impossible method of renaming a folder, must have spent 1/2 an hour trying to get one folder to read what I called it. So far I have found it impossible to make the entire folder structure to display Details layout and keep it that way. The quicker I can dump this bit of software the better, but what to replace it with, and is it safe to do so?

I have read loads on the forum, because so often the members are experienced they talk about the command line solutions in a way I cannot follow, and no mention of a GUI. I have read so much, most of it of no use, this is way I crave for a PDF aimed at my level of competence. Just come to mind, I will look for a copy of the Idiots Guide to Ubuntu, if it exists.

Greg

---

### Post by gertcher on 2012-11-19
Thanks to everyone's help so far.

> I really have the opposite background to you. ''''''''''''''''''''. What tasks are you trying to perform on the terminal?To be correct I am not trying to use the command line. I feel I am being driven to it because I cannot find a GUI to do the task I need. Because I do not understand how to use the command line I am getting know where and this is what is stopping me migrating Ubuntu across all my computers.

Currently this is my major head ache:
I loaded 12.4 from a CD, eventually it worked perfectly, my wireless Network Connection (NC)was steady at 125Mb/s,and often went up to 145Mb/s. I upgraded - an auto procedure by Ubuntu - to 12.10. It went very smoothly and I did not see any malfunctions at all, and saw a few added and useful tweaks. Soon after I noticed my NC was down to 54Mb/s and often as low as 10Mb/s.

So, since the upgrade I have been looking how to fix my NW speed unsuccessfully. You might say I need to update the drivers, I wish. In Windows it would  not be a problem, I cannot find any GUI software loaded or downloadable to do the job. Samsung don't list Linux drivers.

I use ThundrBird, I like it a lot, prefer it to Windows Outlook. What I hate is its lack of auto capitalisation at the start of a sentence, and its lack of auto spelling correction and replacement as I type.

I understand that Ubuntu is far more security enabled compared to Windows. I don't need it, don't want it, cannot switch it off. For instance, the computer starts up and does not ask for an ID, good. I go away for 15 minutes and have to log in when I get back. I start an internet cession and it flags for a password. I can clear it by pressing cancel, but I cannot get rid of the flag.

When I start up I arrive at the work space. How do I get anything to start automatically? I would like Chrome to start automatically.

I have read loads on the forum, because so often the members are experienced they talk about the command line solutions in a way I cannot follow, and no mention of a GUI. I have read so much, most of it of no use, is way I crave for a PDF aimed at my level of competence. Just come to mind, I will look for a copy of the Idiots Guide to Ubuntu, if it exists.

Greg

PS.  I just typed [idiots guide to ubuntu]("https://www.google.co.uk/webhp?sourceid=chrome-instant&ie=UTF-8&ion=1#hl=en&sugexp=les%3Bernk_timediscountb&gs_nf=3&tok=L59OKPGXbyE9FLFK2hD3Bw&cp=22&gs_id=p&xhr=t&q=idiot's+guide+to+ubuntu&pf=p&newwindow=1&safe=off&sclient=psy-ab&oq=idiots+guide+to+ubuntu&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_cp.r_qf.&fp=5c955bf1b2fc6f4a&bpcl=38625945&ion=1&biw=1600&bih=814") and came up with loads of info including a PDF guide. I am not implying this forum lacks help, one of the links comes here, just my fixation on trying to get all help here, and my method of searching. I am still interested to read what the members here have to say, after all this is first hand experience and it is quick. After all, all I have gained from this search is a PDF, I still need help with the other tweaks

---

### Post by mlentink on 2012-11-19
Please read [this]("http://linux.oneandoneis2.org/LNW.htm"). It's enlightening.

---

### Post by saltydogcharlie on 2012-11-19
I have much the same background as you, and like you I used Ubuntu several times in the past with varying success.  This time I got serious because of Windows 8, and purchased a book in addition to free on line PDF manuals.  Too hard to follow along using PDF.   Ubuntu Made Easy by Rickford Grant with Phil Bull does a good job introducing you to the command line and various features of Ubuntu 12.04.  I did not see an updated version but I expect it will do just as well teaching you the basics.  You might want to install the stable release 12.04 version anyway instead of 12.10 for obvious reasons.

---

### Post by mastablasta on 2012-11-19
well the aforementioned Ubuntu manual is a place good start. another good free ebook is found on linuxcommand.org.
 
now lets go through your isses.
 
> **gertcher said:**
>  
To be correct I am not trying to use the command line. I feel I am being driven to it because I cannot find a GUI to do the task I need. Because I do not understand how to use the command line I am getting know where and this is what is stopping me migrating Ubuntu across all my computers.

usually there is a GUI. even on server where there is no GUI you mostly edit various files. it is good to remember that *everything* is a file in linux. it is also good to note that (unlike in windows) you can copy & paste the commands into terminal and also that all comands work independently of your desktop interface (there are plenty desktop environments aside form default Gnome: KDE, XFCE, LXDE, Openbox, icewm....). in shoprt same command that work on ubuntu will work on Lubuntu and same commands that work in debian are very likely to work in Ubuntu. so you may notice plenty solutions with command line.
 
> 
Currently theses are my major head aches:
I loaded 12.4 from a CD, eventually it worked perfectly, my wireless Network Connection (NC)was steady at 125Mb/s,and often went up to 145Mb/s. I upgraded - an auto procedure by Ubuntu - to 12.10. It went very smoothly and I did not see any malfunctions at all, and saw a few added and useful tweaks. Soon after I noticed my NC was down to 54Mb/s and often as low as 10Mb/s. Everything about my NC has been constant - location, equipment, method of use - all exactly the same as before the upgrade
 
So, since the upgrade I have been looking how to fix my NW speed unsuccessfully. You might say I need to update the drivers, I wish. In Windows it would not be a problem, I cannot find any GUI software loaded or downloadable to do the job. Samsung don't list Linux drivers.
While i do not know how to fix htisd (usually additional drivers should open if they are available) i would rather stay with 12.04 if it worked well. 12.04 is LTS release supported for 5 years. additioanlly you say finding drivers is not an issue in windows - but upgrading form 12.10 is same as upgrading form XP to windows 7 or Vista and we all knwo how that went on start.
 
if you do not use additional drivers (i.e. proprietary) then drivers are embedded in linux kernel. which means that upgrading only kernel might solve your issues (again if 12.04 worked why the urge to upgrade?). 
 
12.10 is also full of new many features (and bugs) and testing things so for stability go with LTS (if it works well).
 > 
I use ThundrBird, I like it a lot, prefer it to Windows Outlook. What I hate is its lack of auto capitalisation at the start of a sentence, and its lack of auto spelling correction and replacement as I type.
 
thunderbird has plenty of extensions available. you can have a look at those and maybe find what you want.
 
you can also find plenty of instructions online how to enable things or disable for example:
[http://email.about.com/od/mozillathunderbirdtips/qt/et_inline_spell.htm](http://email.about.com/od/mozillathunderbirdtips/qt/et_inline_spell.htm)
 
> 
I understand that Ubuntu is far more security enabled compared to Windows. I don't need it, don't want it, cannot switch it off. For instance, the computer starts up and does not ask for an ID, good. I go away for 15 minutes and have to log in when I get back. 
This can be disabled. it is of no use unless you are in office environment i agree.
> 
I start an internet cession and it flags for a password. I can clear it by pressing cancel, but I cannot get rid of the flag.
i am not sure how it's done in Ubutnu now (i use it's derivatives), but basically there is a keyring that holds all your passwords encrypted under one password. so to access you wi-fi you type in the keyring password and away it goes. this can also be disabled.
 > 
When I start up I arrive at the work space. How do I get anything to start automatically? I would like Chrome to start automatically.
 
you would add it into autostarting : [http://askubuntu.com/questions/155448/how-to-autostart-gui-application-cross-desktop](http://askubuntu.com/questions/155448/how-to-autostart-gui-application-cross-desktop)
 
.desktop file is basically desktop shortcut in windows terms
 > 
Files. I have never seen anything so clunky, The shape and design of the icons, the font, the almost impossible method of renaming a folder, must have spent 1/2 an hour trying to get one folder to read what I called it. So far I have found it impossible to make the entire folder structure to display Details layout and keep it that way. The quicker I can dump this bit of software the better, but what to replace it with, and is it safe to do so?
 
 
yes it is *safe*. there are plenty of various file managers out there. for example i use Dolphin (default in Kubuntu), there is also Krusader (like Windows total commander), there are many others out there...
 
shape and design is highly subjective topic. some like it some don't. uckilly there are plenty of themes available. amybe not so many or Gnome3/Unity, but for other desktop interfaces.... it's almost limitless. add to that you can customise them yourself. it's easy to make it look like windows 7 for example.
 
> 
I have read loads on the forum, because so often the members are experienced they talk about the command line solutions in a way I cannot follow, and no mention of a GUI. I have read so much, most of it of no use, this is way I crave for a PDF aimed at my level of competence. Just come to mind, I will look for a copy of the Idiots Guide to Ubuntu, if it exists.

 
see my note on command line above. read the manual (part after installation) that is full of pictures. community did a great job there. use google when you get stuck or simply ask here for a solution. i suggest creating separate threads for separate issues. people will home in with a solution faster.
 
and enjoy the experience of learning something new. over 90% of internet works on linux, over 70 of smartphones run it so something must be right with this OS, no? [ok desktop share leaves much to be desired but it's increasing...]

---

### Post by gertcher on 2012-11-19
Hello mastablasta

Thanks for a great reply.  I have to do some paying work over the next few days but will look into your answers very soon.

I know Linux almost runs the www and phone networks. Not sure but is Android a derivation of Linux?

When I upgraded to 12.10 I did so only because Ubuntu said it was the next big upgrade, don't remember it saying anything about it being buggy or unreliable.

If I down grade to 12.4 would it be best to start with a clean instal? Or can I reuse my 12.4 CD and it will wipe away the current install and leave my ThunderBird settings in place?

Thanks  Greg

---

### Post by gertcher on 2012-11-19
One of the features I really like in 12.10 is the ability to hide the navigation strip on the left, cannot do that in 12.4, although I did use an app with v10.0  that could do that and a lot more but I don't remember its name

The whole Linux experience reminds me of my coming to terms with my first computer, an Amstrad 8256. Several weeks of curses because the (then) damned thing would not respond to my logic, when in fact I would not yield to its logic. Guess who won?

The penny will drop with Linux, eventually, and I will be able to help others

---

### Post by avsprasad on 2012-12-12
I'm new to Ubuntu, but fortunately have a friend who's been using it for years and guided me. I wrote an article for chaps like myself who find this new environment confusing and at times painful. I wrote it as a Windows user moving to Ubuntu.

It addresses questions like how to add things to start up etc. I use Ubuntu 12.04 Precise Pangolin, which my friend told me is a stable/ long-term support release. Here's the article: [http://cypress.freeshell.org/temp/Ubuntu_Painlessly.html](http://cypress.freeshell.org/temp/Ubuntu_Painlessly.html)
Hope it helps.

---

### Post by Calinou on 2012-12-12
"You might want to install the stable release 12.04 version anyway instead of 12.10 for obvious reasons."

12.10 is stable too. 12.04 is just long-term support and its software is quite outdated already.

---

### Post by offgridguy on 2012-12-12
Lots of info in this thread re; terminal.

[http://ubuntuforums.org/showthread.php?t=2057339](http://ubuntuforums.org/showthread.php?t=2057339)

---

