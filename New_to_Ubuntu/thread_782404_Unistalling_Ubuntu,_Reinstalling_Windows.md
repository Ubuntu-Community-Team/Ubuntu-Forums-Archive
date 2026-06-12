---
title: "Unistalling Ubuntu, Reinstalling Windows"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by joraffex on 2008-05-04
After about a week or so, I found that the Ubuntu lifestyle wasn't for me- so I'm reverting back to Windows.

So, I pop in the CD, and it tends to ignore the fact that I have a Windows XP Installation CD in there, and boots Ubuntu anyways.

I tried the MSDOS Diskette, and it doesn't boot from it, there's an error apparently. (I'll post it if you need it?)

I tried uninstalling Ubuntu by formatting the partition or whatever, and then it just gave me the GRUB 22 Error.

Yes, I've checked my BIOS and it the priority boot place is CD-ROM, then Floppy, then Hard drive.

So, i'm kind of stuck at this point.
Please ask if you need anymore information to help me with this. x -x;

Thanks.

---

### Post by UnknownFear on 2008-05-04
Hmm.. Trying going into the BIOS screen (DLETE key upon start-up) than change the boot to CD?

---

### Post by Vasto on 2008-05-04
You need to change your boot device settings from either the bios or sometimes there is a F key you can press. But the key varies

---

### Post by Oldsoldier2003 on 2008-05-04
> **joraffex said:**
> After about a week or so, I found that the Ubuntu lifestyle wasn't for me- so I'm reverting back to Windows.

So, I pop in the CD, and it tends to ignore the fact that I have a Windows XP Installation CD in there, and boots Ubuntu anyways.

I tried the MSDOS Diskette, and it doesn't boot from it, there's an error apparently. (I'll post it if you need it?)

I tried uninstalling Ubuntu by formatting the partition or whatever, and then it just gave me the GRUB 22 Error.

Yes, I've checked my BIOS and it the priority boot place is CD-ROM, then Floppy, then Hard drive.

So, i'm kind of stuck at this point.
Please ask if you need anymore information to help me with this. x -x;

Thanks.

its really wierd that your xp installation cd isnt being read. that has really nothing to do with grub. what you could do is make a bootable dos/win95 usb key and boot to it, run fdisk /mbr and then reboot. This should restore your windows bootloader.

---

### Post by lazyart on 2008-05-04
On many systems you can hit F8 and select a boot device without going into Setup.

Do you have multiple optical drives?  Did you try the CD in each of them?  Have you tried the CD in a different machine.

Thanks for trying ubuntu.  Sure wish your first question would have been about the OS itself, instead of how to get rid of it. :(

---

### Post by subzero316 on 2008-05-04
Try clearing the partitions using **GTPARTED**...

BTW switching back to the horrible windows....then you should ask for help in windows lovers forums(which is ofcourse a total suck up.)....I guess you love the blue screen and wanna see your system crash often....:lolflag:

---

### Post by futureal2032 on 2008-05-04
> **joraffex said:**
> After about a week or so, I found that the Ubuntu lifestyle wasn't for me- so I'm reverting back to Windows.

So, I pop in the CD, and it tends to ignore the fact that I have a Windows XP Installation CD in there, and boots Ubuntu anyways.

I tried the MSDOS Diskette, and it doesn't boot from it, there's an error apparently. (I'll post it if you need it?)

I tried uninstalling Ubuntu by formatting the partition or whatever, and then it just gave me the GRUB 22 Error.

Yes, I've checked my BIOS and it the priority boot place is CD-ROM, then Floppy, then Hard drive.

So, i'm kind of stuck at this point.
Please ask if you need anymore information to help me with this. x -x;

Thanks.
I dont know what Hard Drive u have (SATA or PATA) ..if u have PATA though ..u can boot from an old Win98 bootable floppy/CD and  
type fdisk /mbr to clean the mbr of the hard drive and then wipe out the partitions and reinstall windows.

another simple option is .. boot from "gparted" live cd. google for "download gparted live cd". and clean the hard drive and then proceed with Windows installation.

By the way try pressing F8 after the POST is over (i.e. after the bios detects everything and displays a information table).
On many mother boards pressing F8 give us a boot device menu which lets u select which device u want to boot from. it overrides bios boot settings. so from this u can boot into a cdrom.

Remember only trying to format will not do.u will have to create new partion table cleaning out whats already there. so u can install windows.

---

### Post by joraffex on 2008-05-04
I used GPARTED when I formatted the partition, but that doesn't work?

I've used the CD multiple times before for my other windows machine.

So I'll try the F8 thing, I'll post back with how that worked in a bit.

---

### Post by SunnyRabbiera on 2008-05-04
wait, how long have you spent with ubuntu?
certainly you cant expect to learn a new system in one day, if you needed help you should have asked...

---

### Post by joraffex on 2008-05-04
It really isn't my kind of thing, it relies too much on web help, from my experience this past week, the one thing I couldn't access on that computer. 

I'm just too familiar with Windows, and all it's security holes.

OKAY.
I got MSDOS to load,
and it has the A:/> now
what do I type in?

---

### Post by SunnyRabbiera on 2008-05-05
> **joraffex said:**
> It really isn't my kind of thing, it relies too much on web help, from my experience this past week, the one thing I couldn't access on that computer. 

I'm just too familiar with Windows, and all it's security holes.

OKAY.
I got MSDOS to load,
and it has the A:/> now
what do I type in?

well were you having internet issues?
if so you still could have just asked, that is what the linux community is for.
I know there is stuff to learn, but once you learn it things become second nature...
I mean in a few years XP is going to be gone, and vista is no help...

---

### Post by Unix_Slayer on 2008-05-05
Another lost soul on their way back to the Demon's Spawn.....


[IMG]http://www.egameaddiction.com/posticons/mslugshoot.gif[/IMG][IMG]http://www.egameaddiction.com/posticons/bomb.gif[/IMG]

---

### Post by Unix_Slayer on 2008-05-05
> **joraffex said:**
> It really isn't my kind of thing, it relies too much on web help, from my experience this past week, the one thing I couldn't access on that computer. 

I'm just too familiar with Windows, and all it's security holes.

OKAY.
I got MSDOS to load,
and it has the A:/> now
what do I type in?

A:/> Load Demons Spawn  [IMG]http://www.egameaddiction.com/posticons/freaked.gif[/IMG]

---

### Post by joraffex on 2008-05-05
I'm aware of the highly active forums, but I don't want to have to rely on taking this much time to solve my problems.

So, instead of trying to convince me to stick with Ubuntu, would you mind giving me a little direction to solve this dilemna?

---

### Post by joraffex on 2008-05-05
> **Enlitend said:**
> ```
format c: /s 
```
hope that works.

I got a "bad command or file name"

as well as for Unix_Slayer's

o -o

---

### Post by Enlitend on 2008-05-05
> **joraffex said:**
> I'm aware of the highly active forums, but I don't want to have to rely on taking this much time to solve my problems.

So, instead of trying to convince me to stick with Ubuntu, would you mind giving me a little direction to solve this dilemna?

hey nobody say starting something new is easy, you learn by bumping into problems and try to find answers. I just start it a month ago and I found out this community is where I belongs. I hope you give a second thought about it and good luck to you.

---

### Post by Unix_Slayer on 2008-05-05
Do a dir at the prompt and make sure there's something on that disc.

---

### Post by joraffex on 2008-05-05
> **Unix_Slayer said:**
> you can do a format c: with a -help. It will tell you the switches.

A:/>format c:

or

A:/>format -help

....still bad command or file

---

### Post by SunnyRabbiera on 2008-05-05
well we can do our best.
The thing is that the linux community in general is very help you if you give it a chance, you just cant magically gain knowledge on something you know little about.
We are here to help, in fact we can usually provide much better help then Microsoft will ever give you even with the most trained techie.
Patience is a virtue, sometimes learning things can be scary I know but its sometimes for the better.
Hey have you ever ridden a bike?
Played a sport?
Done anything that took you some time getting used to?
If we all had the attitude of giving things up before given the chance we would still be living in caves figuring out fire.

---

### Post by Unix_Slayer on 2008-05-05
> **joraffex said:**
> ....still bad command or file


A:/>dir


and tell me what you see.

---

### Post by Unix_Slayer on 2008-05-05
> **SunnyRabbiera said:**
> well we can do our best.
The thing is that the linux community in general is very help you if you give it a chance, you just cant magically gain knowledge on something you know little about.
We are here to help, in fact we can usually provide much better help then Microsoft will ever give you even with the most trained techie.
Patience is a virtue, sometimes learning things can be scary I know but its sometimes for the better.
Hey have you ever ridden a bike?
Played a sport?
Done anything that took you some time getting used to?
If we all had the attitude of giving things up before given the chance we would still be living in caves figuring out fire.


You are so damned right. Where would we be in this small world if we gave up!

[IMG]http://www.egameaddiction.com/posticons/msgen.gif[/IMG]

---

### Post by Unix_Slayer on 2008-05-05
> **joraffex said:**
> ....still bad command or file

How's that dir coming..... do you see anything?


A:/>dir


Read me some of the contents.

---

### Post by joraffex on 2008-05-05
I would really appreciate not having a lecture on this.
I'm aware of all this, but some things just don't appeal to people, and for me, ubuntu is one of them.

as for DIR-
Volume in dirve A has no label
Volume Serial number is 2A87-6CE1
Directory of A:/

EGA2 CPI 58870 06-08-00 5:00P
EGA3 CPI 58753 06-08-00 5:00P
EGA CPI 58870 06-08-00 5:00P
KeyB Com 21607 06-08-00 5:00p
Keyboard Sys 21607 06-08-00
Keybrd2 Sys 34566 06-08-00 5:00P
Keybrd3 Sys 31942 06-08-00 5:00p
Keybrd4 Sys 31633 06-08-00 5:00p
Mode Com 29237 06-08-00 5:00P
Command Com 93040 06-08-00 5:00P
Display Sys 17175 06-08-00 5:00P
Autoexec BAT 0 50-04-08 8:51P
Config Sys 0 05-04-08 8:51P
13 file(s) 448709 bytes
0 dir(s) 889344 bytes free

---

### Post by Unix_Slayer on 2008-05-05
> **joraffex said:**
> I would really appreciate not having a lecture on this.
I'm aware of all this, but some things just don't appeal to people, and for me, ubuntu is one of them.

as for DIR-
Volume in dirve A has no label
Volume Serial number is 2A87-6CE1
Directory of A:/

EGA2 CPI 58870 06-08-00 5:00P
EGA3 CPI 58753 06-08-00 5:00P
EGA CPI 58870 06-08-00 5:00P
KeyB Com 21607 06-08-00 5:00p
Keyboard Sys 21607 06-08-00
Keybrd2 Sys 34566 06-08-00 5:00P
Keybrd3 Sys 31942 06-08-00 5:00p
Keybrd4 Sys 31633 06-08-00 5:00p
Mode Com 29237 06-08-00 5:00P
Command Com 93040 06-08-00 5:00P
Display Sys 17175 06-08-00 5:00P
Autoexec BAT 0 50-04-08 8:51P
Config Sys 0 05-04-08 8:51P
13 file(s) 448709 bytes
0 dir(s) 889344 bytes free
  

That's not the full disc. Your looking for setup.exe or format.exe

[IMG]http://farm3.static.flickr.com/2192/2269658558_7636b58328_b.jpg[/IMG]

---

### Post by nowshining on 2008-05-05
did you get a question to press a key when starting the windows CD? if so did you press it?


Have you made sure the CD doesn't have any scratches, etc? or any damage at all, try it on anther computer to see if it still works?

By the way windows Needs the Net too u know to find answers/programs, etc. (& help). heck ubuntu/kubuntu/xubuntu, etc.. in its default stage is more useful without a net connection than windows ever was and ever will be.

---

### Post by joraffex on 2008-05-05
Hmm, well I made the diskette on my Windows XP Machine.

Format > Create MS-DOS Disk

Should I create a new one?
or is there something else I should try?

>It's a floppy.

---

### Post by nowshining on 2008-05-05
also do the following  before dong a dir

cd c:/

---

### Post by Unix_Slayer on 2008-05-05
Actually it should look like this  ====>>>>>>


[IMG]http://www.lurkhere.com/articles/images/FORMAT01.png[/IMG]

---

### Post by Unix_Slayer on 2008-05-05
> **joraffex said:**
> Hmm, well I made the diskette on my Windows XP Machine.

Format > Create MS-DOS Disk

Should I create a new one?
or is there something else I should try?

>It's a floppy.



Doesn't sound like a full disc. Every Winblows boot disc has a format.exe on it. At least the last time I looked.

---

### Post by nowshining on 2008-05-05
and oh! do you have a windows 98 disc laying around? if so boot up in ms-dos mode from it and then try a format if not then try cding into the win98 folder and then trying a format.

---

### Post by Unix_Slayer on 2008-05-05
> **nowshining said:**
> and oh! do you have a windows 98 disc laying around? if so boot up in ms-dos mode from it and then try a format if not then try cding into the win98 folder and then trying a format.

The Grub might of locked the disc somehow from formatting.

---

### Post by SunnyRabbiera on 2008-05-05
> **joraffex said:**
> I would really appreciate not having a lecture on this.
I'm aware of all this, but some things just don't appeal to people, and for me, ubuntu is one of them.


well no need to be rude, what exactly was your issue with ubuntu before you decided to call it quits?
How can we help if you dont tell us?
We can only help you if you ask, sure you may feel it odd to rely on people you never met but you take the same risk when using windows if you need to ask major tech support stuff.
Listen I can understand your frustration, this is something new, something different...
its not meant to be exactly like windows, heck no OS is like windows except windows.
Sure if you feel uncomfortable about asking for help on a web forum I can understand, after all none of us are paid here by some major corporation and we give you support out of the kindness of our hearts.
Never be afraid to ask for help, I know if you might be shy this is a hard concept but we will try our best.

---

### Post by Oldsoldier2003 on 2008-05-05
make a bootable disk and copy fdisk to it. the command you want is fdisk /mbr dont format.

---

### Post by Unix_Slayer on 2008-05-05
> **SunnyRabbiera said:**
> well no need to be rude, what exactly was your issue with ubuntu before you decided to call it quits?
How can we help if you dont tell us?
We can only help you if you ask, sure you may feel it odd to rely on people you never met but you take the same risk when using windows if you need to ask major tech support stuff.
Listen I can understand your frustration, this is something new, something different...
its not meant to be exactly like windows, heck no OS is like windows except windows.
Sure if you feel uncomfortable about asking for help on a web forum I can understand, after all none of us are paid here by some major corporation and we give you support out of the kindness of our hearts.
Never be afraid to ask for help, I know if you might be shy this is a hard concept but we will try our best.

I can see the problem..... some users are rudely vagrant sometimes. We all run into this everywhere we go in life.

---

### Post by joraffex on 2008-05-05
I feel like a compelte idiot now.

....
I booted up an older SP1 XP CD and it worked.
I looked at the SP2 disk and it had scratches, I guess I should turn off lights when I do this kind of stuff.

Will I still have to format Ubuntu off?
or will I have the option of doing so during installation for XP?

---

### Post by perlluver on 2008-05-05
> **joraffex said:**
> I feel like a compelte idiot now.

....
I booted up an older SP1 XP CD and it worked.
I looked at the SP2 disk and it had scratches, I guess I should turn off lights when I do this kind of stuff.

Will I still have to format Ubuntu off?
or will I have the option of doing so during installation for XP?

It should just offer to format and install Windows Xp, and it should take Ubuntu off.

---

### Post by SunnyRabbiera on 2008-05-05
> **joraffex said:**
> I feel like a compelte idiot now.

....
I booted up an older SP1 XP CD and it worked.
I looked at the SP2 disk and it had scratches, I guess I should turn off lights when I do this kind of stuff.

Will I still have to format Ubuntu off?
or will I have the option of doing so during installation for XP?

usually XP will take up your whole hard drive on its own, it might detect your ubuntu partition but it might overwrite it.

---

### Post by Unix_Slayer on 2008-05-05
Latest Infractions Received  ===>>>  Posting dangerous commands



See what I just did. I took a hit for you kid.  Beware people.... big brother is alive and well.

---

### Post by joraffex on 2008-05-05
I'm sorry if I'm offensive in anyway for uninstalling Ubuntu, at this point in time, I don't really want to put some patience into it.

I may consider going back one day, but for the convinience of the moment, I would like a familiar OS to appeal to my personal preference RIGHT NOW.

Knowing now how fast-paced and involved this forum is, I won't hesitate when I do decide to go back, SOME DAY.

---

### Post by perlluver on 2008-05-05
> **joraffex said:**
> I'm sorry if I'm offensive in anyway for uninstalling Ubuntu, at this point in time, I don't really want to put some patience into it.

I may consider going back one day, but for the convinience of the moment, I would like a familiar OS to appeal to my personal preference RIGHT NOW.

Knowing now how fast-paced and involved this forum is, I won't hesitate when I do decide to go back, SOME DAY.

You are always welcome back, or if you want you can always try another distro too.  The freedom of choice is great.

---

### Post by SunnyRabbiera on 2008-05-05
> **joraffex said:**
> I'm sorry if I'm offensive in anyway for uninstalling Ubuntu, at this point in time, I don't really want to put some patience into it.

I may consider going back one day, but for the convinience of the moment, I would like a familiar OS to appeal to my personal preference RIGHT NOW.

Knowing now how fast-paced and involved this forum is, I won't hesitate when I do decide to go back, SOME DAY.

well you can set up a dual boot you know, and dont be afraid to use the live CD as a testbed.
In what manner did you install ubuntu, did you use the live or did you use some other disk or by chance you got a computer with ubuntu pre installed?

and yes there are other versions of linux out there, if ubuntu was not your cup of tea you can look into others...

---

### Post by Unix_Slayer on 2008-05-05
I got an Infraction for dangerous commands. This is why it's hard to help people.

---

### Post by joraffex on 2008-05-05
At this point in time, and with the size of this old computer's HDD, I don't feel very comfortable performing a dualboot.

I may be getting another old computer soon, which I might test Ubuntu on again.

I installed it with the 7.04 live cd.

---

### Post by SunnyRabbiera on 2008-05-05
> **joraffex said:**
> At this point in time, and with the size of this old computer's HDD, I don't feel very comfortable performing a dualboot.

I may be getting another old computer soon, which I might test Ubuntu on again.

I installed it with the 7.04 live cd.

ah, well 7.04 is a bit dated, hardy is much better I assure you.
How big is your HD might I ask?
What sort of stuff do you do with your computer?

---

### Post by joraffex on 2008-05-05
20GB?

I don't really plan to do much, but I'm planning on using a computer in my bedroom for an.. 'arcade' kind of thing.

run emulators, stepmania, and the like through my television.

---

### Post by SunnyRabbiera on 2008-05-05
ah, well with space that small yeh a dualboot would be useless, especially with having to get the antivirus/antispyware/antiadware stuff onto it... and all those updates too.
But hey stick around on these forums nonetheless rather if you use ubuntu or not, if you have windows issues we can help there too, after all most of us are former windows users (me included)
we have a windows forum here:
[windows discussions]("http://ubuntuforums.org/forumdisplay.php?f=170")
be sure to post there if you have issues, we can probably help you pretty well.

---

### Post by Unix_Slayer on 2008-05-05
I apologize to anyone I might of injured for my post. I was only trying to help someone with the format command. Now I won't be able to post for two months. So much for actually trying to help another person. For now on I will mind my business. Sorry folks.....

---

### Post by Ludwig9 on 2008-05-18
joraffex, you have my complete sympathy. I am new to Ubuntu and have been having probably a lot of the same problems as you. I have been using computers for a long time but don't know anything about them outside of word processing. I love the idea of Linux, however, and am not ready to give up. I am very impressed by the willingness of people at this forum to help us neophytes (I got help here already in installing a driver for my printer) but at the same time am disappointed in the self-help documentation that is available with Linux and Ubuntu. People here need to keep in mind that before someone comes here with a question he has probably already spent hours trying to figure the problem out himself...without success. 
	For example, I have a file which was originally in MS Word (.doc) but now has been saved as .odt. I am  trying to put this file onto a 3.5 floppy disk. And I use the “Save as” function to do this. But each time I am told that there was a general import/export error in saving the file onto the floppy disk. The file or at least its name actually appears on the floppy disk but the file is empty. Is this because the floppy disk needs to be formatted for Linux? I find nothing about this issue in the help index. I'd appreciate it if someone would explain to me about how to use floppy disks in Linux.
	I also have a problem which is much more relevant to the subject of this thread. I originally intended to do a dual installation of Hardy onto my wife's discarded (because it worked so poorly) Dell Optiplex GX270. At the time of the installation this computer contained no personal files just Windows XP and MS Office. However I screwed up the dual installation, partly because I had not read all the relevant pages in Community Docs and partly because the screens that came up were not the same as appear there. In any case, I now have a machine with only Linux on it...so far as I can tell. I have checked in System/Administration/System Monitor and the whole hard drive seems to be given to Ubuntu 8.04. I would like to have a computer with both Linux and Windows on it, but I have the same problem as joraffex: the Windows re-installation disk does not now work. 
	Will you help me? I imagine I have to create a partition for Windows, but how? What else do I need to do to do a dual installation of Windows XP from inside Hardy? Of course, I could do what joraffex is doing: take off Ubuntu and put back Windows XP, and then I could again attempt a dual installation of Hardy, but I'd rather leave Hardy on.

---

### Post by Ludwig9 on 2008-05-18
In my previous post "general import/export error" should have been: "general input/output error." I have the same problem whether I try to save files to CD's or 3.5" floppies.

---

### Post by Unix_Slayer on 2008-05-19
> **Ludwig9 said:**
> In my previous post "general import/export error" should have been: "general input/output error." I have the same problem whether I try to save files to CD's or 3.5" floppies.

Make sure you have kfloppy installed. If not, you need to install it.

Sudo apt-get install kfloppy

---

### Post by softest bullet ever shot on 2008-05-19
> **SunnyRabbiera said:**
> well were you having internet issues?
if so you still could have just asked, that is what the linux community is for.
I know there is stuff to learn, but once you learn it things become second nature...
I mean in a few years XP is going to be gone, and vista is no help...

Everyone here is really friendly and offering to help, and that's great, but sometimes people just want to get an OS and go, and not have to do a Google every time they want to do something.  I see your point and it may be that Ubuntu is better in the long run; but I can see the poster's point as well.  

That's why I am doing the dual boot, but the person may be limited in HD space.  But with the dual boot, I can do my regular stuff in Windows, and do my playing around with Ubuntu.  

I just think it's important to understand where the poster is coming from.

---

### Post by Ludwig9 on 2008-05-21
> **Unix_Slayer said:**
> Make sure you have kfloppy installed. If not, you need to install it.

Sudo apt-get install kfloppy

I received the following response from Terminal when I gave it the command you suggested:

bash: Sudo: command not found

What next?

---

### Post by nicedude on 2008-05-21
Sad to see you gave up after a week takes more like a month to never want to go back to the dark sides OS. In my case since I had used MS garbage  since DOS 5.0 ( A good OS by the way for its time, and at the time I remember thinking how powerful it was LOL ). So as for me it took some time to begin to feel at home in Ubuntu but now only 3 months into this adventure you would have to pry my Ubuntu install disks from my cold dead hand to take them away, and I will never ever go back to Microsoft in my life as they are just plain greedy scum and I feel bad for all that are not wise enough to see them for what they truly are.

Good Luck with Vista and all its DRM garbage. As for me I think I will control my own equipment not the other way around.

PS someone has probably already told you how to solve your problem ( Not Microsoft of course but someone here ) but in case they have not, my advise would be to download a free copy of "dariks boot n nuke" and burn that to a cd & use it to wipe your disk completely as that will remove grub completely as well as every byte of data on the drive. Then you can install Microsoft's OS on your box 100% for sure.

---

### Post by SunnyRabbiera on 2008-05-21
well he did say that he might come back with better hardware, his hard drive is just too small for a dualboot so its either windows or ubuntu for him...

---

### Post by Maestro23 on 2008-05-21
> **Ludwig9 said:**
> I received the following response from Terminal when I gave it the command you suggested:

bash: Sudo: command not found

What next?

Linux is Case Sensitive.

> sudo apt-get install kfloppy

---

### Post by ubunu on 2008-05-21
I can empathise with the OP here and am slightly saddened at some of the needlessly harsh replies. I'm a new user too but with the fall back of dual boots on 3 machines so I can be a bit more relaxed about difficulties and shortcomings.

I'm as familiar as anybody regarding MS software as I earn my income from supporting and fixing it, like it or not XP is 'tuneable' and despite its many holes it would be balanced to recognise that some parts of it work very well indeed. For example being able to plug in external drives, memory sticks and accessing data - immediately, being able to just select a program such as VLC as the default player, inserting a workgroup name, sharing a folder and joining a network.

WZC, with all XP faults that bit certainly works! I won't describe what I had to go through to get a wireless connection, something that I do for clients (on XP/Vista) about 12 times per week.

My purpose in starting to learn Ubuntu is that I intend, at some point, to offer my clients an alternative to Vista or whatever nonsense they put out instead so I am looking at it from a less personal view and more from the point of view of far less experienced users. Presumably this is the target for the Ubuntu community?

Personally I can live with some of the shortcomings and I spend a large part of each day reading many posts here, sometimes I'll post questions but I have the luxury of 8 computers at home so nothing is critical for me.

Nevertheless, if manufacturers are to be cudgelled into providing better driver support then it will only be in response to increasing demand. The demand will only increase if sufficient numbers of typical, non-technically minded, users can experiment with the alternatives and frequently succeed.

Comments such as;

"BTW switching back to the horrible windows....then you should ask for help in windows lovers forums(which is ofcourse a total suck up.)....I guess you love the blue screen and wanna see your system crash often...."

Are counter-productive. There are many supportive Windows forums (ok, there needs to be) with people who are just as dedicated and supportive as many here. I haven't seen a blue screen on my network for about 4 years (faulty IDE ribbon cable) and I can't honestly remember the last time I had a crash. It's about balance.

Hardy Heron has come a vast distance since the last time I tried Ubuntu and I feel confident that my goal of offering, and being able to support, an alternative is not far off...but not quite yet.

I personally will see it through, I refuse to supply and/or install Vista to my clients and I just hope the next release of Ubuntu addresses some of the obviously difficult issues that are raised so frequently here.

I'm sure it will, in the meantime more balance, less venom and a bit more understanding of where Windows users are coming from. None of my clients are technically minded, if they were they wouldn't be paying me!

For it to work they need to be able to do the things they do. Simple.

No-one should be punished or belittled for failing to transit between point and click and the terminal window.

Well, that's what I think anyway

---

### Post by Ludwig9 on 2008-05-22
> **Maestro23 said:**
> Linux is Case Sensitive.
Ok, that's good to know, and thanks again for your help, but sudo was captitalized in your original post: "Sudo apt-get install kfloppy." I copied and pasted it into Terminal.
In any case the lower case version seems to have worked, and I have copied a test file onto a floppy in both .odt and .doc versions. 
My major complaint with Ubuntu so far is the inadequacy of the help index. For example, "floppy disk" is not there. There is nothing about foreign language keyboards and how to switch between the language keyboards. It shows you how to choose your default language, but, so far as I can see, it says nothing about how to use other language keyboards. I finally figured out how to do this, but info about this should be included in the help index.

---

### Post by Unix_Slayer on 2008-05-22
> **Ludwig9 said:**
> Ok, that's good to know, and thanks again for your help, but sudo was captitalized in your original post: "Sudo apt-get install kfloppy." I copied and pasted it into Terminal.
In any case the lower case version seems to have worked, and I have copied a test file onto a floppy in both .odt and .doc versions. 
My major complaint with Ubuntu so far is the inadequacy of the help index. For example, "floppy disk" is not there. There is nothing about foreign language keyboards and how to switch between the language keyboards. It shows you how to choose your default language, but, so far as I can see, it says nothing about how to use other language keyboards. I finally figured out how to do this, but info about this should be included in the help index.

My mistake.

---

### Post by Raccoon1400 on 2008-05-22
With windows CDs, you have a few seconds to hit any key to boot cd. If you turn on your computer, pop in the CD, it will give you a few seconds to boot cd, then boot default OS. Are you missing the timeout?

```
A:/> D: (to switch to CD, replace D with cd drive letter
D:/> dir (show contents of directory)
D:/> setup.exe(or whatever the sepup file is. Dir should show a setup file and other files)
```

Too bad you don't like linux. As you get to know it well, you would have found you could do more that windows would ever let you do.

---

### Post by ardvark71 on 2008-05-22
> **ubunu said:**
> I can empathise with the OP here and am slightly saddened at some of the needlessly harsh replies. I'm a new user too but with the fall back of dual boots on 3 machines so I can be a bit more relaxed about difficulties and shortcomings.

I'm as familiar as anybody regarding MS software as I earn my income from supporting and fixing it, like it or not XP is 'tuneable' and despite its many holes it would be balanced to recognise that some parts of it work very well indeed. For example being able to plug in external drives, memory sticks and accessing data - immediately, being able to just select a program such as VLC as the default player, inserting a workgroup name, sharing a folder and joining a network.

WZC, with all XP faults that bit certainly works! I won't describe what I had to go through to get a wireless connection, something that I do for clients (on XP/Vista) about 12 times per week.

My purpose in starting to learn Ubuntu is that I intend, at some point, to offer my clients an alternative to Vista or whatever nonsense they put out instead so I am looking at it from a less personal view and more from the point of view of far less experienced users. Presumably this is the target for the Ubuntu community?

Personally I can live with some of the shortcomings and I spend a large part of each day reading many posts here, sometimes I'll post questions but I have the luxury of 8 computers at home so nothing is critical for me.

Nevertheless, if manufacturers are to be cudgelled into providing better driver support then it will only be in response to increasing demand. The demand will only increase if sufficient numbers of typical, non-technically minded, users can experiment with the alternatives and frequently succeed.

Comments such as;

"BTW switching back to the horrible windows....then you should ask for help in windows lovers forums(which is ofcourse a total suck up.)....I guess you love the blue screen and wanna see your system crash often...."

Are counter-productive. There are many supportive Windows forums (ok, there needs to be) with people who are just as dedicated and supportive as many here. I haven't seen a blue screen on my network for about 4 years (faulty IDE ribbon cable) and I can't honestly remember the last time I had a crash. It's about balance.

Hardy Heron has come a vast distance since the last time I tried Ubuntu and I feel confident that my goal of offering, and being able to support, an alternative is not far off...but not quite yet.

I personally will see it through, I refuse to supply and/or install Vista to my clients and I just hope the next release of Ubuntu addresses some of the obviously difficult issues that are raised so frequently here.

I'm sure it will, in the meantime more balance, less venom and a bit more understanding of where Windows users are coming from. None of my clients are technically minded, if they were they wouldn't be paying me!

For it to work they need to be able to do the things they do. Simple.

No-one should be punished or belittled for failing to transit between point and click and the terminal window.

Well, that's what I think anyway

Excellent post! I couldn't agree more :KS

---

