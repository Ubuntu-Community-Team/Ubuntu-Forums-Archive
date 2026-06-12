---
title: "Lubuntu not working fully  (what linux ever does? )"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by thevenerable2 on 2014-04-12
Please can somebody help me get at least one linux distro working for me for just once in my life?

I have had 'reasonable' success with Lubuntu, as its pretty much the only one that wouldn't hang during the instalation process.

It would be great if my function keys worked though so I can adjust the screen brightness.
It would also be useful to download skype, but i cant find it.

please help or i may just have to give up on linux forever.

p.s.
please don't give difficult instructions like  'get the grub or go to sudo'
I have no idea and just want to simple use my computer without having to learn a new language.
If this isnt possible in linux, then i will have to stay with windows for sure (im happy to do that, but its not ideal for slow netbooks)
I just thought i'd get a faster experience on my netbook with linux,,,, but cant even get it up and running... pretty much the same story every time give it another try, year in, year out.

Thanks

---

### Post by sandyd on 2014-04-12
> **thevenerable2 said:**
> Please can somebody help me get at least one linux distro working for me for just once in my life?

I have had 'reasonable' success with Lubuntu, as its pretty much the only one that wouldn't hang during the instalation process.

It would be great if my function keys worked though so I can adjust the screen brightness.
It would also be useful to download skype, but i cant find it.

please help or i may just have to give up on linux forever.

p.s.
please don't give difficult instructions like  'get the grub or go to sudo'
I have no idea and just want to simple use my computer without having to learn a new language.
If this isnt possible in linux, then i will have to stay with windows for sure (im happy to do that, but its not ideal for slow netbooks)
I just thought i'd get a faster experience on my netbook with linux,,,, but cant even get it up and running... pretty much the same story every time give it another try, year in, year out.

Thanks
Try the below

Run in a terminal
```

gksu gedit /etc/default/grub
```
Edit the GRUB_CMDLINE_LINUX_DEFAULT line so that it looks like below and save, then close the window
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```

Run
```

sudo update-grub
``` (your password wont show up, but its being entered)

Reboot, and your function keys for brightness should be working.

---

### Post by buzzingrobot on 2014-04-12
I don't use Skype, but it shows up in a search of the Ubuntu repos.

---

### Post by sudodus on 2014-04-12
> **thevenerable2 said:**
> 
It would also be useful to download skype, but i cant find it.

please help or i may just have to give up on linux forever.


You can install Skype either from the ***Lubuntu Software Center*** or from ***Synaptic*** (programs with graphical user interface) or from the command line in a terminal window

```
sudo apt-get install skype
```

---

### Post by thevenerable2 on 2014-04-12
thanks

but how do i edit the grub line?
how do i save?

---

### Post by thevenerable2 on 2014-04-12
i thnk i installed skype.. i can see it in synaptics package manager when i do a search
but i have no idea where to find the icon to open it?
this is a crazy system

I still have no brightness funcionality when i tried your directions
parhaps you can be a bit clearer, something didnt work.

after rebootoing i did notice that my keyboard layout has changed back to us when i wanted english.

thanks for the help,
my god this linux is shoddy

---

### Post by sudodus on 2014-04-12
Lubuntu has the text editor ***leafpad*** where standard Ubuntu has ***gedit***, so use this command line to start the editor

```
gksu leafpad /etc/default/grub
```

and edit 'as usual' with the mouse, arrow keys, text keys etc. Save with ***ctrl + s*** or use the dropdown menu (File -- Save).

Otherwise you can follow *sandyd*'s advice in post #2.

---

### Post by buzzingrobot on 2014-04-12
> **thevenerable2 said:**
> i thnk i installed skype.. i can see it in synaptics package manager when i do a search
but i have no idea where to find the icon to open it?
this is a crazy system



Synaptics is a program that is used to install software hosted in the Ubuntu servers, aka repositories.  It displays a list of all the packages available in those repos. If you have installed Skype, Synaptics will display a checkmark to the left of its entry.

Once programs are installed, they should be listed in the menu. Linux programs typically do not populate the desktop with icons when they are installed.

---

### Post by thevenerable2 on 2014-04-12
> **sudodus said:**
> Lubuntu has the text editor ***leafpad*** where standard Ubuntu has ***gedit***, so use this command line to start the editor

```
gksu leafpad /etc/default/grub
```

and edit 'as usual' with the mouse, arrow keys, text keys etc. Save with ***ctrl + s*** or use the dropdown menu (File -- Save).

Otherwise you can follow *sandyd*'s advice in post #2.


but i dont know exactly what where and how im supposed to edit

please give a step by step guide


anyway.. to be honest, and dont mean to sound ungreatful,
but i was going to try to find a fast , and easy to use linux distro, then put it on my dad's netbook also.

but just looking at the linux version of skype now its downloaded, its not good, and is more confusing than the standard skype.
All these 'my mum using linux' videos must be fixed.
My mother and father would be completely lost on here, as i almost am.

I dont mean to be ungreatful i just dont know what to do,,
i keep trying to come back to linux and i keep getting frustrated and dissapointed.
The only thing it seems to do well is run a web browswer nice and fast.

sorry.. but im at my wits end with this again

thanks for the help
and hopefully it wont contain even more confusing answers :(

good news is i found skype, bad news is i have no mic
please help with that too

i guess setting up linux as a full os is an impossible dream, but maybe i can have it on my netbook as a fast system, but it MUST be able to do simple things like brightness adjust, mic, uk keyboard etc..
these are just so standard i cant beleive it has so much trouble?

---

### Post by sudodus on 2014-04-12
> **sandyd said:**
> Try the below
```

gksu gedit /etc/default/grub
```
Edit the GRUB_CMDLINE_LINUX_DEFAULT line so that it looks like below and save, then close the window
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#ff0000]acpi_osi=Linux[/COLOR]"
```
Do this edit: Identify the line and add the red text.> 
Run
```

sudo update-grub
``` (your password wont show up, but its being entered)

Reboot, and your function keys for brightness should be working.

> **thevenerable2 said:**
> but i dont know exactly what where and how im supposed to edit

please give a step by step guide

and hopefully it wont contain even more confusing answers :(

good news is i found skype, bad news is i have no mic
please help with that too

i guess setting up linux as a full os is an impossible dream, but maybe i can have it on my netbook as a fast system, but it MUST be able to do simple things like brightness adjust, mic, uk keyboard etc..
these are just so standard i cant beleive it has so much trouble?

What do you mean you have no mic? Do you mean that the mic is not recognized by Lubuntu? In that case I suggest that you install
***pulseaudio*** and ***pavucontrol***, and use pavucontrol (a program with a graphical user interface) to identify the microphone and tweak the settings so that it works properly.

You can install pulseaudio and pavucontrol with the same tool as you installed skype.

-o-

Many people are happy using linux; there is a threshold, or steep learning curve in the beginning, but soon things will be familiar and quite easy to perform. Finally, you must remember that linux is free, so there are no huge economic  resources for polishing the software like in Windows and MacOs.

Don't give up, continue trying, but if you find after trying hard, that  you want to return to Windows, it is also OK. After all, most people use  Windows in desktop and laptop computers.

---

### Post by thevenerable2 on 2014-04-12
but what is a grub command line?
how do i find it?how do i see it?

then maybe i can edit it

the only thing i can think of is just to paste all of what you said into the terminal
but that doesnt involve editing anything
it makes no sense to me. i need to know where to look in the first place so i can edit it

thanks

---

### Post by sudodus on 2014-04-12
Start a ***terminal window*** (you find it in the menu ***Accessories***). Write (or copy and paste) the following line. Finish with the Enter key.

```
gksu leafpad /etc/default/grub
```

Edit: /etc/default/grub is a file with lines. Leafpad is an editor (a simple kind of word processor).

Identify the line according to sandyd's and my previous posts (the line where to add the red text)

---

### Post by thevenerable2 on 2014-04-12
i did that

and then i dont get anything to edit
so where do i go to edit?
i dont get any lines come up to edit.

sorry, but this is TERRIBLE.
how can anyone get on with this
and even when they do get it working, the software is awful, if skype is anything to  go by.

seriously, is this a joke?

whats the appeal of this nightmare?

thanks

---

### Post by sudodus on 2014-04-12
Sorry that we could not help you.

Maybe you can get hands on help by a friend, relative or colleague to get started with linux. Otherwise, I am afraid that you have to go back to Windows.

---

### Post by 23dornot23d on 2014-04-12
How anyone can help you here is beyond my own understanding now .........

Here is a non confusing answer - its about the use of applications on any system where they are using
 technology - with multiple items all having to be set up properly and exactly right for each users systems 

No matter whether it be Linux Windows or Mac ( The hardware used ....... so what are you using ? )

ONE COMMAND NO CONFUSION 

**lspci -v**

It will give us back some information about the hardware - the computer you are using - because that in itself can make a big
difference with any answers you get back - go to Windows and just say keyboard - brightness - skype have problems - and 
fail  to give them any information on what keyboard it is that you use - what  computer it is that you use ..... and what communications
do you use  - modem - wireless - etho ......  what graphics card do you use Nvidia /  Amd / Intel ........ all factors and all need to work
right to get all the things you need in Skype working properly ..........

Sound - Video - Graphics - Communications are all part of Skype

It does not always run right on every system and especially not the one you keep saying you can just go back
to and it will work .......... [https://www.google.co.uk/search?q=windows+skype+problems](https://www.google.co.uk/search?q=windows+skype+problems)

> 
brightness adjust, mic, uk keyboard etc..
these are just so standard i cant beleive it has so much trouble?



They are not standard problems ....... and if they were there would be one standard answer for every computer 
and I am afraid computing is not like that as there are many different computers and setups.

You could be using a pentium 3 for all we know ( as you have not even stated what computer it is yet you are trying to set up )

Even on a a Windows Help Forum ..... they would need to know specifics about you keyboard ...... then they would
most  probably refer you back to the manufacturer of the keyboard - some for  specialized drivers -  [https://www.google.co.uk/search?q=windows+keyboard+problems&btnG=Search](https://www.google.co.uk/search?q=windows+keyboard+problems&btnG=Search)


They are not standard problems ......... but if you want to get proper help ...... start by being less hot and cold

( Thanks but no thanks ) ....... seems to be what I have got from nearly every one of the posts you have submitted so far.

Yet you now have skype ........ and setting of the other things you need are not stopping you from using your system.


The mic one is probably an easy answer once you go put the question forward in the Multimedia section ..........

I am actually very surprised people have stuck with you through this ........ takes some doing when every answer gets a bad
response back .....

---

### Post by thevenerable2 on 2014-04-12
i managed to get the file pad open and edited it, then restarted but the keyboard still wont work when using the fn keys.

i have a samsung nc10 netbook

and im not DUMB
I can use windows xp and 7 totally fine

How is it i can never get on with linux?
I'm not biased, i just like to use what works

Please feel free not to help me if you think im being unreasonable by stating how ridiculous linux can be.

I'm not a windows or linux fanboy

id actually rather use linux if it worked and was productive
but it doesnt work without insane tweaking and isnt productive due to lack of support.

sorry but that seems the truth to me.

Thanks

---

### Post by 23dornot23d on 2014-04-12
duplicate ..... so removed ......

---

### Post by 23dornot23d on 2014-04-12
Your initial question was this ..........


> It would be great if my function keys worked though so I can adjust the screen brightness.

 It would also be useful to download skype, but i cant find it.


  
 

 You asked 3 questions here &#8230;.......
 

 Skype &#8230;....... you now have skype working 

( but your mic needs sorting &#8230;.. might just be the case of adjust in a slider in volume controls as often mic is set low &#8230;...... )



 Keyboard setup &#8211; the keyboard setup is in System Settings as with windows &#8211; but is your keyboard a standard 
keyboard how many keys and which function keys are standard on every other keyboard you know.

 

 Screen brightness &#8230;....... can work easily but depending on the computer &#8230;...... samsung nc10 netbook

> 
I'm not a windows or linux fanboy


  
It bother no one in the slightest ........ no one will even attempt to try to change them ......

Sort a  problems out ...... no matter how bad customers react ......... they cannot help that ........ some were not 
always as proficient as others and we can deal with that .... not saying of course that you have no idea what you are doing.

> 
I have no idea and just want to simple use my computer without having to learn a new language.


You are not going to learn a new language - all you had to do was follow instructions .......

Think you managed one so far and you now have Skype ........ simple as that ..........

> 
id actually rather use linux if it worked and was productive


People are either productive or non productive ......... computers just do as they are told to do ......... and that requires them
to have commands to get them to do things .

Think you may have managed to give your own computer one command so far ........ and that seems to have got one problem one almost solved.

So .......... lets deal with one problem at a time ..........

The mic adjustment - what have you looked at and have you adjusted anything - to get this working .......

Type this in a terminal please .......... maybe you missed that one simple non confusing request .........
or is there a problem with how things get input - rather than the computer itself .........

**lspci -v**

Seeing that you are having problems entering the commands - let me go search on all the specifications
for your notebook and we will do this the hard way ............

I will ask you to type something into a terminal - and you will not bother ............. seems a pointless exercise to me.

> 
No matter whether it be Linux Windows or Mac ( The hardware used ....... so what are you using ? )

ONE COMMAND NO CONFUSION 

**lspci -v**


---

### Post by buzzingrobot on 2014-04-12
> **thevenerable2 said:**
> i did that

and then i dont get anything to edit
so where do i go to edit?
i dont get any lines come up to edit.


Leafpad is a text editor, analagous to Notepad on Windows. "Grub", as used here, is a text file. It is a configuration file for the bootloader.  The changes you were given alter the way the Linux kernel works.  That file is located in the "default" directory of the "/etc" /directory.  gksu is a small program used to give you temporary root user privileges, analagous to administrator privileges on Windows.

The line provided to you simply opens that text file in that texxt editor, with gksu first prompting you for a password.

Perhaps you have never used a text editor.  If so, it would be prudent to practice a bit.

> ...if skype is anything to  go by.

Skype is a Microsoft product.

> ...seriously, is this a joke? 

No.  Millions of people happily use Linux every day.

---

### Post by thevenerable2 on 2014-04-12
i was trying to address the other problems first.

i cant deal with everything at once.

please stop giving me a hard time becasue linux is so confusing to use.
yes i have skype, but its a very crap version of skype, thats not very rewarding when even success is greeted with shoddyness.
I'm not even trying to be ungreatful, just trying to explain the source of my dissapointment and lack of enthusiasm towards linux.

I think you all know i have a point if you are honest.

I typred it in the teminal and got this:

00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
    Subsystem: Samsung Electronics Co Ltd Device ca00
    Flags: medium devsel, IRQ 5
    I/O ports at 18a0 [size=32]

02:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Askey Computer Corp. Device 7131
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
    Subsystem: Samsung Electronics Co Ltd Device ca00
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 2000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2


thanks

---

### Post by gifford on 2014-04-12
Thanks for indicating what you are trying to get Linux to work on.
When seeking advice or help it is important to indicate what type of hardware you are trying to install or work with. Your issues would have been addressed sooner with more appropriate advice had you provided the hardware you are working with.
As for the nc10, my understanding that it uses an intel atom chip, is this correct? It also has 1 gb of memory?

As you must be aware, netbooks are on the low end of computer components and require a "light" version of any operating system. Windows 8 will not run on it and I am not sure if windows 7 will.
Here is a link that may help: [http://askubuntu.com/questions/357112/which-ubuntu-derivative-for-my-netbook](http://askubuntu.com/questions/357112/which-ubuntu-derivative-for-my-netbook)

One of the suggestions is Elementary OS, a light and fast Linux OS.

---

### Post by thevenerable2 on 2014-04-12
'skype is a microsoft product'

I dont care if its made by linux, microsoft or acorn, i want productivity and functionality.
U dont care for skype too much myself, but its used by millions of people
so if i cant get a usable version of skype, what good is that?

fanboy mentality

---

### Post by monkeybrain20122 on 2014-04-12
> **gifford said:**
> 

One of the suggestions is Elementary OS, a light and fast Linux OS.

Let's not confuse OP more with Elementary OS when s/he is trying to get lubuntu working. OK? :)

---

### Post by thevenerable2 on 2014-04-12
Thanks

Yes, Its intel atom with 1gb

it runs xp ok, and windows 7 a bit slowly, but its not too bad.

Linux would be ideal for it, but i cant find any os's that work so well with it.

I can download elementary os, but will it even install|? as most linux os's i tried hung during instalation via netbootin usb

plus will it need mass tweaking to get working properly?

thanks

---

### Post by buzzingrobot on 2014-04-12
Gifford is correct. You have minimal hardware for any contemporary OS.  Part of your frustration, beyond inexperience with the software, may well be due to inadequate hardware.

---

### Post by monkeybrain20122 on 2014-04-12
Skype works on all my linux installations out of the box. But with lubuntu there is this little thing, sound is turned off sometimes so check the volume icon on the lower right hand corner and see if it is actually on.

---

### Post by buzzingrobot on 2014-04-12
Elementary is rather polished out of the box.  USB booting problems are often caused by either a faulty burn of the ISO image, or issues revolving around the video hardware.

---

### Post by thevenerable2 on 2014-04-12
thats the point:
'innadequate hardware' is supposed to be solved by lightwieght os's right?

And the hanging while installing.. ive no idea why
i made about 5 different usb os's with unetbootin, and only one would install beyond the test instalation.

another reason why this 'simple' linux is just so frustrating.. its never as simple as people pretend it is.

and thats not my fault
i ran netbootin, followed the simple instructions.,.. and it didnt work
how is that down to me?

i tried linux mint about 3 times, it would hang near the end of the instalation
same with crunch bang, linux lite, and i think another one that i forgot now.

---

### Post by monkeybrain20122 on 2014-04-12
Your netbook appears to be a problematic one with crappy Linux support. google it and ubuntu and it will turn up a lot of hits.

One recommended solution is to upgrade/install with this ppa which is set up to fix a variety of samsung netbook issues.
[https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa)

More info about the ppa and how to use it (outdated but maybe good for some background, there is only one package for saucy)
[http://www.voria.org/forum/viewtopic.php?t=296](http://www.voria.org/forum/viewtopic.php?t=296)

---

### Post by thevenerable2 on 2014-04-12
i must be unlucky then, as my other netbook had 'crappy' linux support too..
so did my desktop for that matter  ...hmm

anyway, thanks very much for the link

I'll try to figure out how to use it

---

### Post by thevenerable2 on 2014-04-12
what a surpise..
ppa's, its a long drawn out process again..
and for how much gain?

god bless linux

---

### Post by monkeybrain20122 on 2014-04-12
give the models and specs for the others ones too. It is possible that you are indeed very unlucky and I am extremely lucky. Put ubuntu on random machines and it always works out of the box mostly.

---

### Post by 23dornot23d on 2014-04-12
If it is possible we could try to ensure that your system actually got installed ok ..... as that may be adding to the confusions
you are experiencing ... especially if this has happened a few times already .

Did you do the installs onto each system using the same method and same usb - and are they all playing up !!!!

> 
i must be unlucky then, as my other netbook had 'crappy' linux support too..
so did my desktop for that matter  ...hmm



Might be worth us just making sure that your lxde is all uptodate and installed with some items that can maybe help
you get it working better ...... the PPA may be a good way ....... but would it not be at least best to see if you
installed it all ok and that it is uptodate on the current version that you are running ..........


Can you give us back the information from typing df into a terminal please ..... just to see what space you have for Linux
another simple command - but each one lets us know things about what we are dealing with here ...... as we are working 
with little knowledge of what you are actually seeing ...... and I doubt you can get screen shots onto here ......

So we need to do some small terminal commands ........... and you did the lspci -v one ( but only gave us a small portion of it
back )

But for now - just let us see how much space you are working in - so we know we will not run out of room should we ask
you to add or update the computer .........

Type this in a terminal and paste back the results please. (DF lowercase)

**df**

---

### Post by buzzingrobot on 2014-04-12
> **thevenerable2 said:**
> thats the point:
'innadequate hardware' is supposed to be solved by lightwieght os's right? 

Ubuntu, as well as Linux in general, is not intended to be an especially lightweight OS. Lubuntu is lighter to a degree. One GB of RAM is limiting.

> 

And the hanging while installing.. ive no idea why
i made about 5 different usb os's with unetbootin, and only one would install beyond the test instalation.



I've no idea either because you have been rather parsimonious with information, frankly.
Perhaps because the ISO image was faulty?  Did you verify the checksum?  

The instructions linked to here ([http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)) are provided by Ubuntu.


> 
how is that down to me?


No one has said it is.

>  i tried linux mint about 3 times, it would hang near the end of the instalation
same with crunch bang, linux lite, and i think another one that i forgot now.

Many people install and use each of those distributions without the issues you have, but very likely not on your hardware. You should search for reports from people who have installed Linux on the same hardware. if they have been successful, they may provide the detailed instructions you seem to be looking for.

---

### Post by buzzingrobot on 2014-04-12
BTW, feeding "NC10 Ubuntu" to Google returns 120,000 hits.  The first page has several reports on successful installations.

---

### Post by monkeybrain20122 on 2014-04-12
> **thevenerable2 said:**
> 
i have a samsung nc10 netbook

and im not DUMB
I can use windows xp and 7 totally fine

How is it i can never get on with linux?


You paid Samsung to put Windows xp and 7 there, they'd better work. If you pay enough (e.g system76) someone can put Ubuntu on your machine and do all the testing and optimization to ensure everything works too.

---

### Post by thevenerable2 on 2014-04-12
here is the 'df' result:
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      152682596 2422672 142481008   2% /
none                   4       0         4   0% /sys/fs/cgroup
udev              498976       4    498972   1% /dev
tmpfs             101532    1024    100508   2% /run
none                5120       0      5120   0% /run/lock
none              507656       0    507656   0% /run/shm
none              102400      16    102384   1% /run/user


As for the failed installs before, they were all downloaded from official linux sources, and they failed. so i dont know.

Lubuntu worked everytime i tried to install it - well, it installed, but obviosuly doesnt work so well otherwise i wouldnt be here.

If it involves extensive troubleshooting to get one of these distros working, then in my opinion its not worth it, as the end result is not better than windows. Faster and more stable in some areas maybe, but very very limited in others.
\with this in mind, if this is going to be a huge and complicated project just to get some basic functionality here, then i dont think its worth it, theres not enough to gain.

i was hoping for a few download links, a few mouse clicks, and we're done.
This is how linux is presented these days, but it doesnt deliver i guess.

thanks for the help all, i personally cannot be bothered to trawl through the internet just to get an os workin when i can just stick windows back in.

No thats not ungreatful, just practical.

thanks

---

### Post by thevenerable2 on 2014-04-12
By the way, my other netbook was a hp mini210
i remember all sorts of problems trying linux on that a few years ago
and my desktop, im not surem but i remember trying ubuntu once or twice, and ended up running a virtual xp in it most of the time just to get things done.

what can i say.

Those 'ppa' files are not made for lubuntu, and im very confused how to use them and what to choose anyway.

---

### Post by 23dornot23d on 2014-04-12
Do that again ........ just add a space and -a to it

**df -a**

---

### Post by thevenerable2 on 2014-04-12
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      152682596 2424180 142479500   2% /
proc                   0       0         0    - /proc
sysfs                  0       0         0    - /sys
none                   4       0         4   0% /sys/fs/cgroup
none                   0       0         0    - /sys/fs/fuse/connections
none                   0       0         0    - /sys/kernel/debug
none                   0       0         0    - /sys/kernel/security
udev              498976       4    498972   1% /dev
devpts                 0       0         0    - /dev/pts
tmpfs             101532    1028    100504   2% /run
none                5120       0      5120   0% /run/lock
none              507656       0    507656   0% /run/shm
none              102400      16    102384   1% /run/user
none                   0       0         0    - /sys/fs/pstore
systemd                0       0         0    - /sys/fs/cgroup/systemd
gvfsd-fuse             0       0         0    - /run/user/1000/gvfs


thats what i got this time

---

### Post by 23dornot23d on 2014-04-12
Ok good .... we have plenty of space

Lets start with a update of the packages list - simple commands ..... we could do a lot at a time but I will
try to keep this simple so no confusion occurs .... 2 commands this time - the first will give a lot of out put
and take a few seconds to complete ..... it just updates the packages lists .... makes sure if we do download
anything that it is the latest in the repositories at this moment in time .........

**sudo apt-get update**

Second command adds a more user friendly package installer that checks for dependency problems 
as it goes along ........

**sudo apt-get install aptitude**

---

### Post by buzzingrobot on 2014-04-12
> **thevenerable2 said:**
> here is the 'df' result:
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      152682596 2422672 142481008   2% /
none                   4       0         4   0% /sys/fs/cgroup
udev              498976       4    498972   1% /dev
tmpfs             101532    1024    100508   2% /run
none                5120       0      5120   0% /run/lock
none              507656       0    507656   0% /run/shm
none              102400      16    102384   1% /run/user


Seems pretty typical for a fresh install. What are you intending to illustrate, though?

> As for the failed installs before, they were all downloaded from official linux sources, and they failed. so i dont know.

Images are sometimes faulty due to network glitches during their download.  Hence, the use of the checksums.

Problems with USB quality are also not unknown.

> If it involves extensive troubleshooting to get one of these distros working, then in my opinion its not worth it...

It's your call.  If you want dead-simple tools and problems that can be resolved with a single mouse click, or by step-by-step copy-and-paste directions provided by others, perhaps you should look elsewhere.  

> i was hoping for a few download links, a few mouse clicks, and we're done.

Many, many people have that experience. As mentioned, the unique factor here is your 6-year-old hardware.  Every one of the distributions you say failed for you are easily installed and used every day across the planet.  If you are not willing to research problems associated with your specific hardware, not Linux, it is unlikely anyone else will.

---

### Post by 23dornot23d on 2014-04-12
> 
Seems pretty typical for a fresh install. What are you intending to illustrate, though?



I am going to give the user some options ........ and also am going to show them - that there are other lightweight choices

as they seem not too happy at the moment ..........

I hope to make them happy .....

That may be a challenge - but am willing to take the risk if the USER is too ........ ;)

They have only used up 2% of their drive and its as good a time as any to find out what Linux is and what
it can do .......... ( I may show them a lot - if they are willing - or I can go make some supper and call it a night )

The system settings and the sound ...... are usually easy to find and to alter ...... but looking for
ways to give them some new tools ...... xcfe4 may be one way ....... it also ensures a fresh clean
install from the repos of a fully uptodate system ........

Start on a good base ..........

( or we will be here a long time working out what the USER did get to install properly .... and I do not like guessing games. )

If I do this on my own system as the user does it on theirs - I can see the results and compare - what is going on - also
it will give a choice that the user does not have at the moment ......... it too may get the same result back - then I know its
a Linux thing ...... and the User really does only want to go back to using windows ....... sometimes it takes a lot for people to
understand how much control we have over the system and how many different systems / desktops work on here.

Some a lot more suitable for different setups than others ......... and I think I have tried them all ....... at one time or another.
Thing is we are limited with a small computer ( so few options to start with ) .

Why do you fancy going through it with them ....... to sort the last 2 problems .....
if the mic can be fixed with moving a slider then that is a easy one .....

Installing xfce4 may just give everything the user needs ........ and we are also sure its a clean setup of it ...........

---

### Post by thevenerable2 on 2014-04-12
> **23dornot23d said:**
> Ok good .... we have plenty of space

Lets start with a update of the packages list - simple commands ..... we could do a lot at a time but I will
try to keep this simple so no confusion occurs .... 2 commands this time - the first will give a lot of out put
and take a few seconds to complete ..... it just updates the packages lists .... makes sure if we do download
anything that it is the latest in the repositories at this moment in time .........

**sudo apt-get update**

Second command adds a more user friendly package installer that checks for dependency problems 
as it goes along ........

**sudo apt-get install aptitude**


they are done
im not sure what they did, but they seemed to do something

---

### Post by 23dornot23d on 2014-04-12
Ok do not know if you read my last post ...... but I want to make sure you have a clean base to work from

We are going to install xfce4 if you are happy to do that ........ it gives you another choice of desktop 

But it also gives me confidence that everything is installed FRESH / CLEAN ...... 

Then we can see if your sounds settings clear up for the mic ......... still working on the second problem
but I want to sort it from a clean system ....

LXDE will still remain ....... and you may be able to swap from one desktop to the other when we have finished
to see if you like one more than the other one ...... but there are some tools we can load up too that may
make things a lot easier for us to work with ............ hope that helps and the command is ..........

**sudo aptitude install xfce4**

if you want to go this way .......... we can then make sure we both do the same things as I have just fresh installed it on
my own system too .........

> 

-K53SV:~$ sudo aptitude install xfce4
The following NEW packages will be installed:
  desktop-base{a} gtk2-engines-xfce{a} libxfce4ui-utils{a} orage{a} 
  tango-icon-theme{a} xfce4 xfce4-appfinder{a} xfce4-mixer{a} 
  xfce4-notifyd{a} xfce4-session{a} xfce4-settings{a} xfce4-volumed{a} 
  xfdesktop4{a} xfdesktop4-data{a} xfwm4{a} 
0 packages upgraded, 15 newly installed, 0 to remove and 654 not upgraded.
Need to get 10.7 MB of archives. After unpacking 37.6 MB will be used.
Do you want to continue? [Y/n/?] y



You may notice there are a few tools that get installed in there that we can use ........ 
volume and mixer and settings

and they all will be clean fresh straight out of the updated repos box ...... and hopefully then we will
NOT be doing any guesswork ........

You may see the mic like in this picture on it too ..... but we will see some information ........ on it 

[http://commons.wikimedia.org/wiki/File:Xfce4-mixer.png](http://commons.wikimedia.org/wiki/File:Xfce4-mixer.png)

Picture source above .......

[IMG]http://upload.wikimedia.org/wikipedia/commons/c/c9/Xfce4-mixer.png[/IMG]

---

### Post by buzzingrobot on 2014-04-12
> **23dornot23d said:**
> I am going to give the user some options ........ and also am going to show them - that there are other lightweight choices

as they seem not too happy at the moment ..........

I hope to make them happy .....

That may be a challenge - but am willing to take the risk if the USER is too ........ ;) 

Sorry, I missed that.  The OP also should understand that, by focusing on minimal resource impact, Lubuntu inevitably sacrifices some usability.

Martin Wimpress, who handles Mate for Arch, did a study of so-called light desktops in Linux, expecting Mate to do well. ([http://planet.mate-desktop.org/](http://planet.mate-desktop.org/)). He tested on Arch, not Ubuntu.  But,  LXDE, Lubuntu's desktop, came in first, followed by Enlightenment, and then XFCE and Mate.  The difference in memory usage was less than 40 megs. That's one reason I think application choice has more impact on resource use than anything else.

---

### Post by thevenerable2 on 2014-04-12
> **23dornot23d said:**
> Ok do not know if you read my last post ...... but I want to make sure you have a clean base to work from

We are going to install xfce4 if you are happy to do that ........ it gives you another choice of desktop 

But it also gives me confidence that everything is installed FRESH / CLEAN ...... 

Then we can see if your sounds settings clear up for the mic ......... still working on the second problem
but I want to sort it from a clean system ....

LXDE will still remain ....... and you may be able to swap from one desktop to the other when we have finished
to see if you like one more than the other one ...... but there are some tools we can load up too that may
make things a lot easier for us to work with ............ hope that helps and the command is ..........

**sudo aptitude install xfce4**

if you want to go this way .......... we can then make sure we both do the same things as I have just fresh installed it on
my own system too .........



You may notice there are a few tools that get installed in there that we can use ........ 
volume and mixer and settings

and they all will be clean fresh straight out of the updated repos box ...... and hopefully then we will
NOT be doing any guesswork ........

You may see the mic like in this picture on it too ..... but we will see some information ........ on it 

[http://commons.wikimedia.org/wiki/File:Xfce4-mixer.png](http://commons.wikimedia.org/wiki/File:Xfce4-mixer.png)

Picture source above .......

[IMG]http://upload.wikimedia.org/wikipedia/commons/c/c9/Xfce4-mixer.png[/IMG]


i ran the terminal command
amd pressed yes when prompted
it installed some things
ive no idea what or how to open them though
i cant see any picture pop up like you show here thats for sure

thanks

---

### Post by 23dornot23d on 2014-04-12
Now logout and choose xfce4 in your login ....... selection listing ........

Then login and choose >>>>  **default panel**

it sets up as it goes into it ........ its a fresh desktop .......


Even in LXDE now you should be able to use this command .... but we will do it in XFCE4 first to see if you like it any better

**xfce4-mixer**

---

### Post by thevenerable2 on 2014-04-12
i logged out, then logged in
it gave no options to log in to any new desktop
just asked for my password as normal

---

### Post by 23dornot23d on 2014-04-12
There is a symbol to the right of the username or top right that you pick 

 .... to change desktop - to the right of the  username .....



But seeing you are back here ..... just do

**xfce4-mixer**

---

### Post by jbaerboc on 2014-04-12
This is just my two cents worth...but...lighter desktops such as XFCE or the one on Lubuntu tend to be light on resources but also light on easy to follow options. For example it's simple as pie to install/find anything in Ubuntu main edition [hit the super key and type what you're looking for], It's also relatively easy to find things in Kubuntu [KDE Desktop] although it has more options to do everything than any other DM I've seen so far. I don't know exactly what your 6 year old hardware consists of but might want to try a more mainstream Linux such as your basic Ubuntu, or if you want to install and have everything work with next to no configuration you can try Linux Mint. There are also distributiong which claim to be the best "like windows" experience out there. Zorin OS is an example of one of them if memory serves. 

In the end just keep in mind that Linux gives you TONS of options as far as distributions go and sometimes it just takes trying some of them out to know which one fits you and your hardware best. 

I do understand your frustration though as I could never get Ubuntu 13.10 to work on my computer, neither live disk or installer. But I'm typing this from the 14.04 Beta 2 with no issues and it's running smooth as butter.

I guess what I'm saying is don't let your experience with one or even two attempts at a Linux distribution install color your overall opinion of it. My wife uses Linux Mint Cinnamon Edition on her computer with no problems and all she's ever used is Windows. My 4 year old daughter uses both my and my wife's computers for various things as well [although she has no pre-concieved Windows thoughts in her head haha].

Thanks for reading my ramblings ;-) and good luck in your adventures!

---

### Post by thevenerable2 on 2014-04-12
ok.. i got some kind of mixer when i put that in
not a desktop change

im not sure what we are trying to acheive here but im confused already

---

### Post by thevenerable2 on 2014-04-12
sorry to say, but your 4 year old would be able to do a lot more things on windows.

but at least linux keeps her on her toes more i guess

---

### Post by 23dornot23d on 2014-04-12
Lots of options - but we are finding some to suit the user hardware and 1 gig memory low spec computer

> 
Yes, Its intel atom with 1gb

it runs xp ok, and windows 7 a bit slowly, but its not too bad.

Linux would be ideal for it, but i cant find any os's that work so well with it.


Will show the user the others too if they want to ...... and we can see how they perform

But my first quest is 3 questions we started with ..........

and the way I solve them is on a good clean light weight and easy to install system ....... that can be removed just
as quickly and easily if the applications I wanted solve these few problems.

But am also giving the USER choice ..... something they do not realise they have yet ....... 

We can show all the other things once we know the computer is loaded up and ready to go with a good install of apps.

Should be close to the end now ..........







Well you did not manage to log out and find the other desktop .......... 

its a button press - change next to the username ... usually .......

______________________________

But where is the mic setting showing on the shot and did you try raising the sliders ...........

---

### Post by thevenerable2 on 2014-04-12
i managed to change the desktop. it looks much better and the fn buttons work now

but the two taskbars (one on top, one on bottom) wont dissapear when i open a webpage so my viewing space is very small.( im on a netbook so need full screen space)

as for the mic control, no luck
it only has one slider - master

---

### Post by 23dornot23d on 2014-04-12
Good we are getting somewhere .............

give me a minute to move into xfce4 ....... 


Do a reboot now while I swap systems ...... just to make sure it goes in again ...... might pick more things
up too on the way in ........

---

### Post by buzzingrobot on 2014-04-12
If you right click on an XFCE panel (what you called the "taskbars"), select "Panel" and then "Panel Preferences", you should see an option to "Automatically show and hide the panel".

If you like XFCE, you might want to look at the Ubuntu derivative based on it, Xubuntu.

I'm currently using Xubuntu 14.04.  The mixer wasn't available until I enabled "Indicator Sound" as a startup application,, logged in and out, and then clicked on the volume indicator that appeared in the panel.  Access to the microphone on this Thinkpad was then available from the "Input Devices" tab.

---

### Post by 23dornot23d on 2014-04-12
As Buzzingrobot says too   see above as more text was added to explain the sound  ...    ^^^^^^

> 
If you right click on an XFCE top panel (what you called the "taskbars"),  select "Panel" and then "Panel Preferences", you should see an option to  "Automatically show and hide the panel".


Also right click on bottom dock there are sliders to change its height in pixels ... might also help you ..... as small screens need all the room they can get


What if anything changed  .....  ?

---

### Post by thevenerable2 on 2014-04-12
Thanks
i got rid of the top task bar but definately cant find any sliders or way to get rid of the thick bottom one

i have been prompted to install lots of updates upon restarting
apart from that i dont think anyhthing changed
still only one slider option in the audio mixer

---

### Post by 23dornot23d on 2014-04-12
Did you install the updates ?

[B]sudo aptitude safe-upgrade

[/B]is a command I use - but give me back the list of things it says its going to do.

Answer no .... if it threatens to remove anything ...... and quit out of it ......

But post the list of options or upgrades it gives back as then we may be able to work out more
about what happened before.

as regards the dock look one the dock settings ..... might need to click low down on the edges of it to get the menu up
there is also a link here to customization for afterwards if you stick with it 
[http://www.everydaylinuxuser.com/2012/11/xubuntu-1210-day-2-customise-desktop.html](http://www.everydaylinuxuser.com/2012/11/xubuntu-1210-day-2-customise-desktop.html)

---

### Post by thevenerable2 on 2014-04-12
sorry, i already started installing the, aages ago

---

### Post by 23dornot23d on 2014-04-12
Ok no problem ...... might be interesting seeing what it is installing though ..... if you can list its output

---

### Post by buzzingrobot on 2014-04-12
> **thevenerable2 said:**
> Thanks
i got rid of the top task bar but definately cant find any sliders or way to get rid of the thick bottom one


still only one slider option in the audio mixer

If "thick bottom line" means the bottom panel, then, as I explained, you can set it to "automatically show and hide".  I.e., the panel will hide when you move a wndow near it, and reappear when you move that window away.

When I click the volume control icon in the panel here, one of the things I see is "Sound settings...".  Clicking that opens the mixer (aka sound settings), on which is a tab for "Input Devices" which includes "Internal Microphone".

---

### Post by thevenerable2 on 2014-04-12
when its finished i will, if you tell me how

i managed to shrink the bottom task bar, but its still not much good.
if there is no way to hide it then i think i'd rather do away with it
edit.. no problem, i managed to auto hide it now
much better

---

### Post by monkeybrain20122 on 2014-04-12
You need pulse audio volume control for the mic problem. 
```
sudo apt-get install pavucontrol

```
With it you can see the input/output playback streams on every audio program in use (e.g skype when you try to make a test call) as well as options for build-in-audio, sometimes just changing the option for the build-in-audio tab will fix the sound problem.

---

### Post by buzzingrobot on 2014-04-12
> **thevenerable2 said:**
> 

i managed to shrink the bottom task bar, but its still not much good.
if there is no way to hide it then i think i'd rather do away with it

I've explaiined how to make a panel temporarily hide.

If you delete both panels, you will be without access to the applets and icons that reside in the panels.

---

### Post by 23dornot23d on 2014-04-12
The OP has managed to autohide both now ...... and this is a quick moving thread ...... good answers and the OP needs to
go back through them to make sure nothing gets missed out .......

**sudo apt-get install pavucontrol**

Will then carry on .......

```

sudo apt-get install pavucontrolK53SV:~$ **sudo apt-get install pavucontrol**
[sudo] password for keith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-19 linux-headers-3.13.0-19-generic
  linux-image-3.13.0-19-generic linux-image-extra-3.13.0-19-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  pavucontrol
0 to upgrade, 1 to newly install, 0 to remove and 654 not to upgrade.
Need to get 116 kB of archives.
After this operation, 1,041 kB of additional disk space will be used.
Get:1 [http://ubuntu.mirrors.uk2.net/ubuntu/](http://ubuntu.mirrors.uk2.net/ubuntu/) trusty/universe pavucontrol amd64 2.0-2 [116 kB]
Fetched 116 kB in 0s (279 kB/s)     
Selecting previously unselected package pavucontrol.
(Reading database ... 403623 files and directories currently installed.)
Preparing to unpack .../pavucontrol_2.0-2_amd64.deb ...
Unpacking pavucontrol (2.0-2) ...
Processing triggers for man-db (2.6.6-1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140408-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Setting up pavucontrol (2.0-2) ...
Processing triggers for menu (2.1.46ubuntu1) ...



```

Then run it pavucontrol

K53SV:~$  pavucontrol

---

### Post by thevenerable2 on 2014-04-12
ok
thanks for the help

i have to go to bed now

as for the new audio progrqamme, i dontr know how to use it, i had a look but cant see any way to test the mic or configure it still.


thanks for the time

---

### Post by 23dornot23d on 2014-04-12
It should come up like this once setup properly ..... we will do this
some other time ...... great job ..... and well done sticking with it .......

  we can show you some more things ..... and hopefully you will get everything
running you need to .... then we can customize things .......

Which is what Linux allows more than any other system  ........

[IMG]http://i.minus.com/ibd7DNTCTkYl9p.jpg[/IMG]

Stick with it - but until another time ...... just keep working at one
problem at  a time ......

You will see that most of them go away - and its when they have done
then the system you have will be your own unique system that works 
fast and efficiently .... with what you want to see on the screen at
any one time ...... there are other docks too .......

But your own system may be limited to what effects can work on it ......

_____________________________________________________________

Just so we know - and can you confirm  .... the function keys now work ..... ( from what you said last ) .

and skype works ...... except the mic ....... did not function ...... ( which should be sorted soon in these settings see post #65 ) .

> 
It would be great if my function keys worked though so I can adjust the screen brightness.
It would also be useful to download skype, but i cant find it.


and a system that works  ....  ( tick in the box for that too )  ... as xfce4 is a complete fresh install with all the updates.
and a autohide for panel and dock ........ setup so when browsing they pop out of the way.

---

### Post by thevenerable2 on 2014-04-13
Yes thanks.
I can confirm that the mic is working now also.

The whole os is more functional now.
Its not as polished as windows 7, but is mucf faster on the netbook

---

### Post by 23dornot23d on 2014-04-13
Good to hear that .... 

if you want something more polished ........ try this command now 

```
sudo aptitude install e17
```

and show me what you get back ........ please ........ e17 always installs against everything
else on my systems ........ and is my backup desktop ........ but its quite polished now.
as you will see - we can run different desktops - but choice again ......

xfce4 - e17 - lxde .......... all different environments to work within ........ 

upto you - but if your happy with what you have then - its maybe just a case of marking
this thread as solved .....

This is the Desktop Environments part of Ubuntu Forum

[http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

 and it will be better opening a
new thread in there - should you want to customize anything within any desktop
you load up ......... people tend to scan the individual parts of the Forum for things
they believe they might be able to help with ...... customization is not my speciality
as I like fast and efficient systems ....... but depending on the computer.

I run another desktop that looks a little more like windows 7 but is called kde - but
it may be too much for you as you onlu have 1 gig of mem .... and with a browser
running on mine it can be hovering between 700 meg to 1000 meg depending on
what I have open at any one time ...... something else to look at though.

Check on You-tube for names .......... here are a few desktops - I would
say that is in a order of resources needed .... the further down the slower
the computer may run ......... depends a lot on how they get set up though
compiz is either the one thing that takes users into another world or
it slows the computer down to such an extent is like a tortoise.

Awesome ( very basic ) but least resources needed IMHO
E17 ( reasonably polished ) very lightweight - odd functionality at times on the desktop
XFCE4 ( lots of apps - light weight too ) - good functionality - easy to use desktop too
Gnome-Flashback - ( was a very popular setup ) lots of apps ...
Gnome-shell ( took over from above when Gnome3 was introduced ) - can be set up for efficient working
KDE ( powerful and very heavy on resources ) - but I like this and tend to work in it a lot .....
Unity ( was introduced when Gnome3 came out ) - think it was based at serving programmers - lots of keyboard input 
but has improved considerably since launch ...... resources - needs compiz ..... can be more demanding dependant on
how the user sets it up though ......

Things that can be added to most of them - other docks

Docky ( is ok but not as polished as the next one )
Cairo-dock ( this I use all the time - very handy - but can be resource hungry too )

---

### Post by SuperFreak on 2014-04-13
I find this use of ..... throughout posts very distracting and difficult to read. Nothing personal

---

### Post by 23dornot23d on 2014-04-13
Well its always there to improve - just like linux programs ...... we all have our own ways and I am
afraid this ..... is mine ....... cannot be any different to what I am otherwise you would not know it
was me. 
But feel free to re-write anything ..... rarely take anything to heart .

Like pointing out speech impediments to people .... they maybe listen and try ..... to change

Its my way and my education or lack of it probably shows through - but I am afraid that
is the way I am - take it or leave it ...... no offence intended.

---

### Post by oldos2er on 2014-04-14
Thread is going off topic, closed.

---

