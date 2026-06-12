---
title: "Need to remove virus off this computer"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by DaveMcC on 2013-06-10
I have here a multi-disk dual booting computer that got a virus via win8 auto up-dating "win8 is really really really crap" BUT, all I need it for is running my photo-editing program, nowt else. 

SSSSooooooooo, how do I scan and remove virus from computer

open terminal, type in,
sudo /derv /media/ run round the yard/ place a chicken in the oven/etc /

sudo /etc/dev/-r -i --bell --move=/home/<yourname>/infected /media/window/
sudo make the coffee/ media/windows in heat/ roll over
sudo /roll over lay down /let me in

Get the idea, typing in stuff like that makes no sense to me, don't under stand it, don't want to know

All I know IS, go to top left hand of screen, click on Places, just below Computer is my 4 drives

Dave

---

### Post by todorakiggg on 2013-06-10
I guess we need a bit more info to be able to help you? How do you know there is a virus? Some strange behaviour? Please elaborate...
Do you have antivirus on the Win8 part? I this this is the easiest way to remove it...

Once you remove the virus, I do recommend you to get rid of the dual boot situation (delete the Win part). After that install virtualbox and make yourself Windows VM.
It works pretty well and this how I solved my problem with Garmin Apps not supporting Linux. (I have Windows 7 VM with only those apps installed). Anything else is in Ubuntu :popcorn:
VM has no sudo rights, so even if you catch something in the VM, it won't do any harm to the rest of the machine.

---

### Post by mastablasta on 2013-06-10
have a look at this: [http://www.liberiangeek.net/2012/04/list-of-free-antivirus-software-for-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/list-of-free-antivirus-software-for-ubuntu-12-04-precise-pangolin/)

ofcourse you can copy paste the commands. no need to type them.

mostly they are command line programmes as they are usually run on mail servers and such to scan emails going to windows users.

a few other otpions to consider:
- some AV have so called system rescue disks that will boto and scan infected mashcine. the only way to remove a root kit for example is via such a disk.
- use a web scan on the NTFS partition (some AV have web based scans of your disk). ofcourse if you have unlimited broadband it shouldn't be an issue.

---

### Post by DaveMcC on 2013-06-10
> **todorakiggg said:**
> I guess we need a bit more info to be able to help you? How do you know there is a virus? Some strange behaviour? Please elaborate...
Do you have antivirus on the Win8 part? I this this is the easiest way to remove it...

Once you remove the virus, I do recommend you to get rid of the dual boot situation (delete the Win part). After that install virtualbox and make yourself Windows VM.
It works pretty well and this how I solved my problem with Garmin Apps not supporting Linux. (I have Windows 7 VM with only those apps installed). Anything else is in Ubuntu :popcorn:
VM has no sudo rights, so even if you catch something in the VM, it won't do any harm to the rest of the machine.

**Some strange behaviour**?
Yes, strange behaviour........ in ubuntu, when I minamize "not X off" any thing, >example what I am running now Firefox,< it disapears and has to be restarted, if I have lets say 10 tabs open, all 10tabs disapear, with no warning from Firefox about closing tabs
**Please elaborate...**

Antivirus on win8, "Pirate copy" ?? what do you think............

**I do recommend you to get rid of the dual boot situation (delete the Win part).** err NO, I would rather delete ubuntu and cut the wire going to the router
I do not go on the internet via windows have deleted "as best I can" any way of doing such a stupid thing

As for "**virtualbox**"  that is way over my head, don't know. don't want to know

Dave

> **mastablasta said:**
> have a look at this: [http://www.liberiangeek.net/2012/04/list-of-free-antivirus-software-for-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/list-of-free-antivirus-software-for-ubuntu-12-04-precise-pangolin/)

ofcourse you can copy paste the commands. no need to type them.



ctrl C and ctrl V don't work ???

---

### Post by ohnonot on 2013-06-10
> **DaveMcC said:**
> sudo /derv /media/ run round the yard/ place a chicken in the oven/etc /
sudo /etc/dev/-r -i --bell --move=/home/<yourname>/infected /media/window/
sudo make the coffee/ media/windows in heat/ roll over
sudo /roll over lay down /let me in

Get the idea, typing in stuff like that makes no sense to me, don't under stand it, don't want to know
neither do i understand. if you can't tell us what's going on we can't help you.

---

### Post by DaveMcC on 2013-06-10
> **mastablasta said:**
> have a look at this: [http://www.liberiangeek.net/2012/04/list-of-free-antivirus-software-for-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/list-of-free-antivirus-software-for-ubuntu-12-04-precise-pangolin/)



Took a look, that is greek
Nothing to me

> **ohnonot said:**
> neither do i understand. if you can't tell us what's going on we can't help you.

computer not working, as it was a week ago, now must have virus

???????????????????????????????????????????????????????

Dave

Did I say what version of this I am running,

It's release 10.10 (maverick)

---

### Post by Impavidus on 2013-06-10
> **DaveMcC said:**
> **Some strange behaviour**?
Yes, strange behaviour........ in ubuntu, when I minamize "not X off" any thing, >example what I am running now Firefox,< it disapears and has to be restarted, if I have lets say 10 tabs open, all 10tabs disapear, with no warning from Firefox about closing tabs
You would need a very sophisticated virus that can damage Linux in subtle ways whilst running in Windows. Most likely this problem is unrelated to anything in Windows. Your Firefox may still be running after clicking the "-", but for some reason the button doesn't appear on the panel. (10.10 still worked with the panel with buttons, right?)
> 
**Please elaborate...**

Antivirus on win8, "Pirate copy" ?? what do you think............
We do not recommend pirated copies of software. If you don't want to pay for Windows, use Linux instead.> 
**I do recommend you to get rid of the dual boot situation (delete the Win part).** err NO, I would rather delete ubuntu and cut the wire going to the router
I do not go on the internet via windows have deleted "as best I can" any way of doing such a stupid thing

As for "**virtualbox**"  that is way over my head, don't know. don't want to know

DaveDual booting works fine for most. Virtual machines need quite a bit of memory.

> **DaveMcC said:**
> ctrl C and ctrl V don't work ???Use ctrl-shift-v to paste in a terminal. Alternatively, select and click with the middle mouse button.

> **DaveMcC said:**
> Did I say what version of this I am running,

It's release 10.10 (maverick)

10.10 is old and has been unsupported for over a year.

---

### Post by mastablasta on 2013-06-10
> **DaveMcC said:**
> **Some strange behaviour**?
Yes, strange behaviour........ in ubuntu, when I minamize "not X off" any thing, >example what I am running now Firefox,< it disapears and has to be restarted, if I have lets say 10 tabs open, all 10tabs disapear, with no warning from Firefox about closing tabs

firefox warns you the first time if you accidentaly tick not to warn oyu in the future then it will not warn you when you close it. this is not a behaviour of virus or malware. virus or malware will stay hidden and give you data to attacker. rarely they show themselves to you (mostly if they are an extorsion scheme).

in linux the easiest way to see if programme is really off is to run ```
top
``` command (or system resoruce manager or something like that).

> 
**Please elaborate...**

Antivirus on win8, "Pirate copy" ?? what do you think............

i wouldn't pirate an OS. back in 90's it was a different scene...
[/QUOTE]
As for "**virtualbox**" that is way over my head, don't know. don't want to know
[/QUOTE]
Actually virtual box is motly clicking next next next, then boting the cd and performs the os install... for example instaling ubuntu inside virtual box:[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
> **DaveMcC said:**
> ctrl C and ctrl V don't work ???
no they don't. i think in terminal it's shift+crtl+c and shift+crtl+v (not sure though as it's been a while since i was ini terminal). in any case right click in terminal and then click paste (or copy) in the menu. that one definatelly works ;-)

---

### Post by 3rdalbum on 2013-06-10
From the description you gave, it doesn't sound like a virus at all.

A virus wouldn't cause programs to randomly close. Viruses these days try to prevent the user from discovering them. Causing random crashes and odd behaviour is counterproductive for any virus made in the last ten years.

For anyone reading this thread later, who is experiencing real malware symptoms ("virus scans", browser toolbars, website hijacks and messages pretending to be from the FBI) you are better off using Windows-based anti-malware tools. If that is not possible, some websites will tell you what files are associated with your malware, and you can use Ubuntu to manually remove these files.

---

### Post by DaveMcC on 2013-06-10
> **3rdalbum said:**
> From the description you gave, it doesn't sound like a virus at all..

You may be right, read on.................

> **3rdalbum said:**
> 

A virus wouldn't cause programs to randomly close. Viruses these days try to prevent the user from discovering them. Causing random crashes and odd behaviour is counterproductive for any virus made in the last ten years.
.

Program does NOT randomly close, it when I click on ( - ) bar the page firefox, notepad gedit, google earth or Stellarium Planetarium, ( and that is all the programs I ever use ) down to the bottom grey task bar, which is no longer there ??
It was there this time last week

> **3rdalbum said:**
> 
For anyone reading this thread later, who is experiencing real malware symptoms ("virus scans", browser toolbars, website hijacks and messages pretending to be from the FBI) you are better off using Windows-based anti-malware tools. If that is not possible, some websites will tell you what files are associated with your malware, and you can use Ubuntu to manually remove these files.
So, what I thought was a virus, is in fact a missing panel where programs minimise to.
If, IF that is the case, then how do I get it back ??
Dave

---

### Post by dino99 on 2013-06-10
> **DaveMcC said:**
> 

So, what I thought was a virus, is in fact a missing panel where programs minimise to.
If, IF that is the case, then how do I get it back ??
Dave

if you have met such trouble, i suppose its due to your own weird tweaking; so if you want to get back a genuine installation, then erase that one and replace it by a fresh one.:lolflag:

---

### Post by BBQdave on 2013-06-10
If you have hardware that runs Windows 8, I offer you might want to consider updating to a current Ubuntu system. Ubuntu Unity 12.04LTS running smooth and solid here :)

---

### Post by DaveMcC on 2013-06-10
> **mastablasta said:**
> firefox warns you the first time if you accidentaly tick not to warn oyu in the future then it will not warn you when you close it. this is not a behaviour of virus or malware. virus or malware will stay hidden and give you data to attacker. rarely they show themselves to you (mostly if they are an extorsion scheme). 
that box has never been ticked or unticked, think I am getting to the bottom of this ?? haha he said hopefully, please bear in mind I am thick, artise, but thick........

> **mastablasta said:**
> 
in linux the easiest way to see if programme is really off is to run ```
top
``` command (or system resoruce manager or something like that).

Ran that, 2 user's Tasks 176, 174 sleeping ran it again now 3 users, clicked on the ( - ) thing and reran for the third time terminal code top and got 4 users
Every time I click on the ( - ) it disapears into the bottom right hand corner, never to be seen again

> **mastablasta said:**
> 
i wouldn't pirate an OS. back in 90's it was a different scene...

When you work with a high end camera, shooting in RAW, the only soft ware to use is "with me" is Nikon's own RAW editing software which is win / mac only View NX2, then if needed finish off in your chosen photo-editing software, hence win8 for testing, 
It is getting wiped shortly for testing ubuntu 13.............

> **mastablasta said:**
> 

[QUOTE=mastablasta;12685171]
Actually virtual box is motly clicking next next next, then boting the cd and performs the os install... for example instaling ubuntu inside virtual box:[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

no they don't. i think in terminal it's shift+crtl+c and shift+crtl+v (not sure though as it's been a while since i was ini terminal). in any case right click in terminal and then click paste (or copy) in the menu. that one definatelly works ;-)
Top bit is still over my head, have the computer set up the way I want it to run, like for the last ??? years untoched
The bottom bit about the shift+crtl+c and shift+crtl+v, why must it be different from every thing else ???????

> **BBQdave said:**
> If you have hardware that runs Windows 8, I offer you might want to consider updating to a current Ubuntu system. Ubuntu Unity 12.04LTS running smooth and solid here :)

Only for a missing bottom bar, ubuntu 10.10 is running smooth and solid here, besides that thing running down the side of the screen looks like office97 app bar, NO, not hardware, but software that runs on win8

> **mastablasta said:**
> firefox warns you the first time if you accidentaly tick not to warn oyu in the future then it will not warn you when you close it. this is not a behaviour of virus or malware. virus or malware will stay hidden and give you data to attacker. rarely they show themselves to you (mostly if they are an extorsion scheme).

in linux the easiest way to see if programme is really off is to run ```
top
``` command (or system resoruce manager or something like that).
;-)

Have just ran that command again
i have 5 users
tasks 185
1 running
184 sleeping

> **mastablasta said:**
> firefox warns you the first time if you accidentaly tick not to warn oyu in the future then it will not warn you when you close it. this is not a behaviour of virus or malware. virus or malware will stay hidden and give you data to attacker. rarely they show themselves to you (mostly if they are an extorsion scheme).

in linux the easiest way to see if programme is really off is to run ```
top
``` command (or system resoruce manager or something like that).


Just before I sign off and get back to work,,,,,,,,,and as I have 2 tabs running I ( X )

You are about to close 2 tabs.  Are you sure you want to continue ?
[ ] Warn me when I attempt to close multile tabs

I knew I never nchecked that wee box

Dave

---

### Post by mastablasta on 2013-06-11
so it seems to me (accoridng to previous posts) that you've accidentaly removed the bottom panel. try this: [http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/](http://helpdeskgeek.com/linux-tips/easily-restore-the-default-gnome-panels-in-ubuntu/)

If you really like panels and you want to go with latest Ubutnu then you should try Xubuntu or install Mate desktop. or maybe Kubuntu (my favourite).

> **DaveMcC said:**
> 
Ran that, 2 user's Tasks 176, 174 sleeping ran it again now 3 users, clicked on the ( - ) thing and reran for the third time terminal code top and got 4 users
Every time I click on the ( - ) it disapears into the bottom right hand corner, never to be seen again

yeah users means user processes. root is system process. you can mark it and post it here using code tags (the # icon). 

> 
When you work with a high end camera, shooting in RAW, the only soft ware to use is "with me" is Nikon's own RAW editing software which is win / mac only View NX2, then if needed finish off in your chosen photo-editing software, hence win8 for testing, 
It is getting wiped shortly for testing ubuntu 13.............
I understand your need to use windows. there is nothing wrong with that. but do not use pirated windows or any other OS. these updates they send are important. not just for security but also for stability. i use windows my self on some maschines because i need some windows only software. too bad they do not make all software for linux as well, huh?

> **DaveMcC said:**
> Just before I sign off and get back to work,,,,,,,,,and as I have 2 tabs running I ( X )

You are about to close 2 tabs. Are you sure you want to continue ?
[ ] Warn me when I attempt to close multile tabs

I knew I never nchecked that wee box

Dave


ok so missing bottom bar is the only issue left ?

---

### Post by 3rdalbum on 2013-06-11
I see now. You're using 10.10?

It's well and truly not supported anymore, so you REALLY should upgrade to 12.04 or later, but I might be able to remember enough about 10.10 to help.

Right-click a blank area of the top panel and choose Properties. Change the number of panels to 2 (there might be an Add Panel button, not sure). Close the window and drag the new panel to the bottom or wherever you want it.

Now you need to add an item to the panel. Right click the new panel and choose "Add to Panel..."  and click the Window Selector item in the window that appears. Now click Add and then Close, and you are done.

---

### Post by dyanpul on 2013-06-17
Reinstall your OS dude, instant fix... or upgrade to Pangolin. I will try to upgrade tonight form lynx to pangolin though... ;)

---

