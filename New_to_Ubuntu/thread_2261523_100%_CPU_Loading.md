---
title: "100% CPU Loading"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by David_R._Hassall on 2015-01-19
Dear Group,
I am just starting again on Linux and Ubuntu after a long absence.  I have a Gateway model MFATXNIN NMZ 300 CEL that has 
a 2GHz Intel Celeron processor, 1.256GB of memory, OS type is 32 bit, and a 39GB hard disk.  Yesterday I loaded UBUNTU 
14.04 into it and it was terribly slow. (My Raspberry Pi was operating faster)... Thinking I had maybe gotten a bad load I 
updated last night to 14.10 but this morning it was the same slow crawling operation.  I was able to download a system monitor
program and started it up.  Here is what it said.  CPU History is at 100% most of the time with only small excursions down. 
Memory and swap history 430.5 of 1.2GB, and network history only a few blips now and then.  I checked ACTIVE PROCESSES
and GNOME SYSTEM MONITOR  at 3% with flashes of XORG and COMPIZ to 100% from time to time.  LOAD AVERAGES 
1,5, 15 MINUTES were 1.61, 2.59, 2.53.  To me this shows that what is running shouldn't cause the CPU History to be at 
100%.  
I have no other program running that I can see but something is looping somewhere that is causing the 100% CPU Loading. 
Since I am very new to UBUNTU and Linux (Sorry guys and gals but I have been on Windows most of my life and I am trying
to wean my self off of it) I don't know what to do NEXT.  Does anybody have a clue what is going on?  Do I have to go and 
find another computer for UBUNTU?  Do I have a Virus? Is there a double program running?  
Any suggestions gratefully accepted.  

73 Dave WA5DJJ

---

### Post by Bashing-om on 2015-01-19
David_R._Hassall; Hi Welcome back .

Ok, the top of the line ubuntu takes some hosses to run, and for a good experience with this desk top one should have at least 2 gigs of ram.
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

May I suggest that you try Lubuntu :
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by JeQhdMD on 2015-01-19
Well, I checked this system's specs . . . it's just not going to run a current graphics intensive OS such as Ubuntu with the Unity desktop, or other distros that use KDE (Plasma), Gnome-3 (Cinnamon or Default Gnome).

Just a combo of outdated specs and low ram.

BUT . . the good news is it should run a distro that uses either the MATE desktop or XFCE just fine.   I would suggest you download Linux Mint 17.1 with the MATE desktop (not Cinnamon) and give it a try.

[http://blog.linuxmint.com/?p=2713](http://blog.linuxmint.com/?p=2713)

"edit:   just a note on bashing's recommendation:  while Lubuntu is definetely a solution, the default desktop is major "ooglai" . . . that is Orcan speech for butt-ugly.    For the lighter-weight desktops, "out of the box" Mate is best looking & functional but XFCE can be modified to look almost as good (in my humble opinion).

---

### Post by David_R._Hassall on 2015-01-20
Dear Bashing-om

Thanks for the hint...I downloaded LUBUNTU and installed it this afternoon and it is up running just fine... good speed etc.
spent some time configuring it tonight and I think it will do just fine.  I guess the other version was just too much for it..
and I didn't think it was that much of a HOG.   But LUBUNTU has a much more familiar feel to it as the screen looks very 
similar to my Raspberry Pi screen.  So, the learning curve isn't so great.    I really appreciate the help so quickly.  I was 
really frustrated.   
Take care and have fun... The Linux computer will get used on the BROADBAND HAMNET NETWORK tomorrow.
73 Dave WA5DJJ

---

### Post by David_R._Hassall on 2015-01-20
Dear jeQhdMD,

Thanks for the help.. I chose to put LUBUNTU in there instead but will keep Linux MINT 17.1 in mind for a 
try if this doesn't work.  I loaded it this afternoon and so far it is working very well.  Good speed and all the 
applications that I need to get started... So I am on the road... Thanks for your quick reply ... 
I really appreciate it as I was really frustrated with what I was getting...

Take care and have fun.
73 Dave WA5DJJ

---

### Post by mörgæs on 2015-01-20
Good, please mark the thread 'solved'.

---

### Post by Bashing-om on 2015-01-20
David_R._Hassall; Great !

Glad ya up and running . Pleased I was of some small help.

Do not be a stranger, and I wish
[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by NM5TF on 2015-01-20
Hi David,

I can second the motion to install Mint Mate 17.1...a little less resource intensive than Ubuntu with Unity

if you want to stay with Ubuntu, then go with Ubuntu 14.04 Mate.....it really brought my Wifes laptop back
to life....her laptop has similar specs as your machine does.....either Ubuntu Mate or Mint Mate will be
a good match for you...

welcome to the World of Linux....once you get comfortable, you'll wonder why you stayed with Windoze
for so long....

to mark this thread solved,, go to "Thread Tools" at top right of your 1st post & select SOLVED....

73 de NM5TF

---

### Post by David_R._Hassall on 2015-01-21
Dear NM5TF,
I think that I am going to be satisfied with LUBUNTU 14.1 that I have installed for now, but will keep the mint ideas in my back pocket for some other 
older hardware units that I am trying to revive as stopgap computer units to put on my Broadband HAMNET here in New Mexico until more suitable 
units can be found.   The reason I have stayed with WINDOWS so long is that there are not equivalent Linux programs to solve my technical problems
easily.  Maybe after I get used to it, I can also find similar solution in the open software.   Thanks for the hint and I will try to close this thread as 
solved.   Take care and have fun .. 73 Dave WA5DJJ

---

### Post by JeQhdMD on 2015-01-22
Well worth a look at . . . re finding Linux alterntives to many Windows only software.  Plus there are other methods to run Windows software in Linux (Virtual Box and WINE/PlayonLinux).

[http://alternativeto.net/](http://alternativeto.net/)

---

