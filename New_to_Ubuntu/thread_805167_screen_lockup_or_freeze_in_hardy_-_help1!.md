---
title: "screen lockup or freeze in hardy - help1!"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by jpartsch on 2008-05-23
I have a problem with the screen locking up or freezing at totally random times.  This seems similar to what some others have reported with certain wireless or graphics cards, but my hardware is different.  When it happens cursor doesn't move, keyboard won't respond in any way, hard drive is not working.  I can't do Ctrl+Alt+Backspace.  I must do a hard reboot.  I also posted in launchpad, but maybe I am just missing something really basic since I am new to Linux.  Can anyone HELP?!?!?!  I searched Google and specified the i830 driver in my xorg.conf file to no avail.  Here is my system setup:

Dell X200
Pentium IIIM @ 933MHz
256MB RAM @ 133MHz FSB
Intel 830MG chipset shared graphics
no wireless card.

Thanks!!!

---

### Post by Master Grah on 2008-05-23
Has this ever happened with a different OS? I know that a computer can freeze if it overheats...

---

### Post by HuntMike79 on 2008-05-23
> **Master Grah said:**
> Has this ever happened with a different OS? I know that a computer can freeze if it overheats...

I'm getting the exact same freezing... My computer isn't overheating at all (watercooled), and runs XP fine. It tends to freeze when running FireFox, any way this can be fixed?

---

### Post by ubuntu-freak on 2008-05-23
Does this happen if effects are disabled? Turn them off in System > Preferences > Appearance > Effects. Also, rebooting into recovery mode and typing "xfix" may cure the problem. Type "startx" after it's finished configuring your hardware to reach the login screen.
 
Nathan

---

### Post by DozeyUK on 2008-05-24
I have the exact same problem - total freeze and requiring a hard reboot (ALT+SysRq and REISUB doesn't work either).  I've tried EVERYTHING on these forums to try and fix it. Things like:

1) Trying ati / radeonhd / fglrx driver - still freezes
2) Using EnvyNG to install the drivers - still freezes
3) Disabling desktop effects - still freezes
4) Unplugging all USB hardware (except mouse and keyboard which i need...) - still freezes
5) Total re-install - still freezes
6) Manually building the latest stable linux kernel (2.6.25) - still freezes
7) Many many more suggestions on the forums that I've spent hours on...

I don't use wireless, so that's not an issue...My computer is plugged in with an Ethernet cable.

My important system specifications are:

Asus A8NE Motherboard
AMD Athlon 64 X2 Dual Core Processor 4800+
2GB Corsair Ram
ATI X1900XTX Graphics Card
2x 500GB SATA Hard drives (Western Digital)

The only time I haven't particularly noticed a crash is when using the VESA graphics driver, although I haven't stayed using it for too long as it was inbetween trying things out.

Last night I re-installed Hardy AGAIN and it was non stop freezing again...I was even in CTRL-F1 terminal and doing a chown on some files and it froze there too - at least it became totally non-responsive and I had to do a hard reboot. Might have been unrelated though.

This is nothing to do with an unstable computer system as I have Windows XP in dual boot and that works flawlessly...

I'm now in the process of re-installing GUTSY as that was pretty stable for me and worked well.

I seriously think someone, somewhere has totally screwed up with regards to Hardy and I'm very disappointed with it. I've been a big fan of Ubuntu since Dapper Drake and have been convincing loads of people to use it. Now I'm finding it embarrassing when I - a pretty tech savvy person - can't even get the new version of Ubuntu working on my machine.

Guess I'll keep Gutsy until Intrepid is out...

Dozey

---

### Post by DozeyUK on 2008-05-24
Hmm...after installing Gutsy again it was working fine. But after doing all the updates for it, it started freezing the same as Hardy...literally all the time making the system totally unusable.  Perhaps there's some piece of software that just totally screws the system under certain configurations?

I'm now back in Windows XP and it's working perfectly...

Very sad :(

Dozey

---

### Post by DozeyUK on 2008-05-24
Well...re-installed Hardy - this time back as 32bit (I was using 64bit before) and the Live CD worked fine...as it always does...but when I get into the installed version and all I do is install the fglrx drivers using synaptic, it starts freezing very frequently again.  I didn't install any other updates and this is what happens...this is just truly awful. I seriously can't do anything with Ubuntu as it just constantly crashes, requiring a hard shutdown / reboot.

Seems I'll be either finding a different Linux OS or going back to Windows until Ubuntu is fixed. Windows XP just works absolutely amazingly compared to this...and trust me, it's hard for me to admit that.

Dozey

---

### Post by HuntMike79 on 2008-05-24
I forgot to mention, I'm running Ubuntu within an NTFS partition, could this be the cause of the freezes?

I'll try a clean install first...
EDIT:
> **reassuringlyoffensive said:**
> Does this happen if effects are disabled? Turn them off in System > Preferences > Appearance > Effects. 
Ok, I've tried disabling the effects and it has now stopped freezing...

So I'm guessing this is GFX card related?

I'm wondering what's the best way of getting the effects to work again, with no freezes...

EDIT2: Just had it crash again, with effects disbled... :( So I guess it's not that.

---

### Post by doktormiod on 2008-05-25
Hi, I have the same problem with hardy - it freezes randomly. I read somewhere that this might be problem with wireless drivers/devices but i do not even have one :/
I've tried other solutions found on this forum but nothing works.
I have ATI and use fglrx, with compiz on or off it still locks-up. kernel -rt didn't help either, same with uninstalling powernowd. And I think it's not connected with firefox becouse sometimes hardy freezes only a few seconds after booting when i didn't run any program :/
Upgrading kernel to 2.6.25 may be a solution, unfortunately i'm too lame to compile it on my own.

---

### Post by h4mx0r on 2008-05-25
Anyone here having freezing issues and not using an ATI card?... If you do have an ATI card and are experiencing it please try using the opensource driver or compile the latest driver from ati. Are you using some sort of crossfire/sli stuff?

---

### Post by doktormiod on 2008-05-25
I'm not using crossfire, I got just 1 x1800gto. I didn't try to change drivers becouse in other thread i read this happens also to people with nVidia. I hope this bug will be fixed soon, couse for me changing drivers/disabling compiz is not a solution, it's just avoiding the problem. I appreciate your help though, thanks.

---

### Post by DozeyUK on 2008-05-25
I just have a single x1900XTX as well.  I tried the "ati" drivers and they cause a freeze as well.  I attempted to get the "radeonhd" drivers to work as well, but that resulted in a blank screen and I just couldn't get them to work at all. Used EnvyNG to install the latest ATI FGLRX drivers...but still freezes.

As for the 2.6.25 kernel, I used some automated program (forget the name now) to ease with installation of this...however even after waiting ages for it to build etc...it still had the freezing problem for me.

Dozey

---

### Post by wariskampar on 2008-05-25
Hello, I also experienced this problem when I first migrate to Ubuntu. But since 2 days ago, my sys never freeze again. Maybe Ubuntu self-heal itself:). Anyway, will monitor this thread for future reference

---

### Post by geekATlarge on 2008-05-25
I've just fixed a similar problem on my system. Look at: [Failed to initialized HAL, can't mount USB, log-out icon locks-ups]("http://http://ubuntuforums.org/showthread.php?t=806813")

---

### Post by HuntMike79 on 2008-05-25
I forgot to mention my GFX card is a ATI x800 gto.

I plan to upgrade to a 7800gt once I get my watercooling overhaulled...

I really hope changing over to an NV card will fix this as I also plan to run dual displays...

I'll check out that USB link thing tho...

---

### Post by doktormiod on 2008-05-25
I will look into this USB and HAL thing becouse i have similar problem on hardy. It doesn't mount dvd/cd or other partitions, i have to do it manually so i suppose it's HAL problem?

---

### Post by immerohnegott on 2008-05-30
Having the same problem. Updated from Gutsy to Hardy over the intarweb and my old lappy started freezing nonstop (no CTRL+ALT+BACKSPACE, no Virtual Terminals, no CTRL+ALT+DEL - machine entirely unresponsive until hard reboot). Dealt with it for a couple weeks, trying to find a fix to no avail. Saw one post theorizing it was kernel related, so I tried a different kernel (attempted using -rt from Apt, to no avail and didn't have the time to manually build 2.6.25). Didn't help. Sooo, I downloaded the painfully huge Fedora 9 DVD and went to install only to discover copious amounts of graphical glitches and no way to switch from the "intel" driver to "i810" - it would kill X until i switched 'em back. Fed up with that and Fedora's package manager from hell, I decided to try a clean install of Hardy and everything seemed to go ok until I booted the machine up about twenty minutes ago and it locked up while I was out of the room.

WTF.

On the other hand, I haven't had a lick of trouble out of Ubuntu on either of my desktops - one being an older Pentium 4/Intel 865G-based machine, the other a P965/Pentium D/GeForce 7950. Both have been running solid, and I've tried various versions of hardy on the latter, including 32 and 64 bit versions of Ubuntu and Kubuntu, as well as 64-bit Ubuntu studio, with no trouble to speak of. 

Is this just a glitch centering around very specific hardware bits? I've tried a few other things as well  (different drivers, disabling compiz, running dpkg-reconfigure on xorg, etc) but nothing seems to work. 

Pertinent Specs (affected Laptop)
Dell Latitude c400
-Pentium III-M @ 1.2 gHz
-512mb PC-133 RAM (leet, I know)
-Intel 830M chipset/graphics
-ICH3? I THINK this is the southbridge. Maybe.
-Intel IPW2200 a/b/g wireless NIC

I just hope this gets sorted out soon.

---

### Post by DozeyUK on 2008-05-30
I'm still having this problem...I just keep hoping that all these updates I keep downloading are going to fix it...but they never do :(

For now I'm back to Windows XP.  I really can't stand it crashing so much in Ubuntu...it must be killing my hard disk :(

Dozey

---

### Post by wigglydiggly on 2008-05-30
Same problem here.  Hard locks at random times.  Reinstalled serveral times, all updates, compiz on/off no matter what just kept crashing.  Windows XP runs fine no problems there.  Installed gutsy no crashes since.  Funny thing is I have a laptop and another desktop with hardy installed and not a single problem.  But this desktop is one crash after another.

Asus A7V333
AMD 2600+ CPU
1.7 gigs ram
Nvidia 5200 pci

Nothing too new or non-standard with this computer.  Its hard to believe its hardware related, but maybe some combination of parts that just won't work with hardy.  Until someone smarter than me figures it out I'll just keep Gutsy.

---

### Post by abhilashreddym on 2008-05-31
Even my computer freezes up quite frequently. Even when i'm doing simple tasks like playing a video file or resizing a window. 
I have a fairly good laptop. A core duo T2300, with 512mb of RAM and a 40gig hard disk. It's integrated graphics though.

Ubuntu, please take care of this. Because it's very disconcerting to restart your computer every few minutes. I'm a new ubuntu user. You guys did a wonderful job. I love the operating system. But shouldn't you have tested it properly before releasing it? 

Please, please fix this. I don't want to go back to windows. :confused:

---

### Post by Snappo on 2008-05-31
I get this too my system crashes whilst using firefox, i d/c my wifi and it works again for another few minutes.

---

### Post by tomsen_san on 2008-06-01
> **DozeyUK said:**
> Well...re-installed Hardy - this time back as 32bit (I was using 64bit before) and the Live CD worked fine...as it always does...but when I get into the installed version and all I do is install the fglrx drivers using synaptic, it starts freezing very frequently again.  I didn't install any other updates and this is what happens...this is just truly awful. I seriously can't do anything with Ubuntu as it just constantly crashes, requiring a hard shutdown / reboot.

Seems I'll be either finding a different Linux OS or going back to Windows until Ubuntu is fixed. Windows XP just works absolutely amazingly compared to this...and trust me, it's hard for me to admit that.

Dozey

I am on 32-bits all the time and on the OSS graphics driver for my old Ati x800 GT. Since the upgrade the system freezes for me whenever I type morethan a couple of lines. Actually waiting for it right now ... it only occurs for me when I type something. I can browse and leave the system on as long as I want without freezes ... but this it's totally unusable.

I am on an Athlon 2600+, Ati X800GT, 1 GB mem, nForce2 board, worked solid for 7.10. no wifi, no special hardware

---

### Post by hansospina on 2008-06-10
I have the freeze problem since I updated to hardy, firefox freezes all the computer for like a minute or two then it allows me to work.

it is kind of strange, my freeze problem is related to some d site's, grails.org for example always give me a headache.

I tried to re-install firefox-2 on hardy and it works perfectlly, today i installed and update from ubuntu with firefox 3 RC1 and the problems continues with that version, for now i will continue to use firefox-2.

hope this bug can be solved, it's REALLY ugly.

---

### Post by Windsurfer619 on 2008-06-20
Same problem here. It doesn't have anything to do with Firefox though. No CTRL+ALT+BACKSPACE, no virtual terminals. Nothing. And just at completly random times.

Any fixes? At all?

---

### Post by wariskampar on 2008-06-20
In my experiences (several times with the latest was this morning), nothing will work (Alt+Prt Scn+R,E,I,S,U,B or Alt+F2 or Ctrl+Alt+Backspace or whatever). The only way is to Turn Off our pc/laptop manually. Maybe, i miss out something but this was i done

---

### Post by Maxei on 2008-06-23
Can you guys post the results of top, just to see if any process or program is using excessively the cpu time? I have seen reports that xorg may hog the cpu and freeze/crash the system.

---

### Post by ameseisch on 2008-06-25
I have had this very annoying issue with grails.ord as well. So far it is the only one that gives me a problem. The odd thing is it only happens on the laptop I use for work not my desktop at home (both run Hardy). It isn't specific to Firefox either, Opera has the same problem. my only guess is maybe it was a java plugin issue but moving to sun's java didn't help.

---

