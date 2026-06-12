---
title: "CPU jumps up to 100% usage then back down endlessly"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by randomnick on 2008-04-28
Running 8.04, this only started happening today, if I open the system monitor, the CPU performance graph looks similar to "saw teeth" CPU usage goes up and down endlessly. The process tab *never, ever* actually shows you what process/ thread is misbehaving (unlike windows, where you can *ALLWAYS* find the errant process).
the "top" command does not show what is eating my CPU either, If I can't figure this out, I will simply switch to a more stable distro. I'd rather not do that, so if anyone can tell me hoe else I might locate and kill this obnoxious process/ thread I would be grateful.

Thanks


By the way, I tried to search the forums, but the embedded search engine is next to useless (and the new Captcha is really annoying):mad:

---

### Post by nowshining on 2008-04-28
by default serveral processes autostart such as updatedb to update the contents on your computer for a faster search when using the locate command via CLI.

Top by default should show the one taking up the most CPU, the one with the most CPU usage hits the top - you may notice that the CPU doesn't show 100% but 0.3% or such, and you may have to wait a sec for it to pick up the process taking up that much cpu power.

---

### Post by randomnick on 2008-04-28
Thanks for the reply (despite my negativity of the original post, just frustrated) :)

Yeah, the thing is no process even shows up on top as ever using more than 12% while the others are using like .5, here are a couple of screen shots to show you what I mean;

[IMG]http://i59.photobucket.com/albums/g306/staceychandler/Screenshot-2-1.png[/IMG]

[IMG]http://i59.photobucket.com/albums/g306/staceychandler/Screenshot-1-1.png[/IMG]

---

### Post by nowshining on 2008-04-28
by the way on system monitor just hit the TAB/Title for CPU to re-order it by CPU % and of you can do the same on the other TABS by which I mean re-ordering them.

What's your Particular CPU?

and gnome-system.mo if I seen correctly is odd as user but I don't know what it is, and of course I run kubuntu, however top is installed by default on all ubuntu variants.

Try disabling the 3D effects and such if your using them and see if it continues.

---

### Post by randomnick on 2008-04-28
I reordered the applet to display by CPU usage, see screen shot below, (2.5ghz Pentium 4), and I still can't see what is causing the usage to spike endlessly. gnome-system.mo is gnome system monitor & 3-D effects are completely disabled. 

[IMG]http://i59.photobucket.com/albums/g306/staceychandler/Screenshot-3.png[/IMG]

This problem just began after todays updates, there were 11, but I didn't pay any particular attention as to what they were....I scanned through them briefly before applying, but nothing really jumped out at me...This is driving me crazy...I removed tracker & trackerd originally as that beta software was really buggy and was eating massive amounts of CPU but it was running great afterwards, using like 0 - 3% cpu usage at idle till today. I have tried rebooting a couple of times as well without improvement. Is there a more verbose way to view processes and sub threads?

---

### Post by arisystems on 2008-04-28
I have the same thing on a single core AMD 64 bit running 8.04 for AMD.  However, when the screen saver activates, it apparently settles down.  When I move the mouse and the desktop reappears, I get the same sawtooth processor activity as you see.  My initial thought was that it is gnome desktop related.  This same machine was running 7.10 and did not do this sawtooth performance. Since this is not a production machine, I didn't care too much for now. I do remember from AT&T System V days (1990's), too small of an interval skewed the performance itself.

---

### Post by spiderbatdad on 2008-04-28
I ma guessing it is firefox 3 beta misbehaving. Check the hidden folder in your home directory /.mozilla/firefox/something.default/urlclassifer3.sqlite for an enormous and growing file. This is a known bug...the present work around, I believe, is to use ff2.

---

### Post by randomnick on 2008-04-28
I checked the urlclassifier3.sqlite file and current size is 37.3 MB, which does seem a little large, but I am not sure what constitutes "normal" size, as I have never paid any attention to it before, is it possible that firefox 3 could be chewing up CPU cycles when it is not actively running? I get the sawtooth performance at idle, with nothing running...:confused:

---

### Post by nowshining on 2008-04-28
right click on a process and see if there is an option to view threads, etc..

However it might be in the prrefs in gnome-monitor as it's been about half a year since I last used gnome. :) and don't put too much on the P4 as it's week.

I have a 2.66ghz P4 cpu NOHT.

hmmm seems strange... as the CPU of the P4 will go up to 100% just on about every little thing and slow the rest down a bit before moving onto the next task..

However just using the system normally with no CPU intensive apps open should be fine.

Altho I do have A question tho? does the System seem slow?

if not it might be a bug with gnome-monitor as it does go high when just moving the gnome-windows as does the P4 CPU which is normal.

Also you could add the monitor applets to your taskbar for better monitoring.

---

### Post by nowshining on 2008-04-28
ah nore help from others with better help hopefully.

---

### Post by spiderbatdad on 2008-04-28
not sure either how trackerd (another pain imo) deals with all that stuff ff3 is collecting in that file. The aforementioned file is a problem. Normal size should be a few kb (i believe) You can read plenty about this bug on Launchpad or searching the forums...[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)

Maybe once indexing is all done...things will slow down...personally I like to stop tracker and remove it from startup programs.

---

### Post by randomnick on 2008-04-28
Yeah, trackerd is completely gone, I'll read into the bug. 
The system does not seem slow...Thanks for trying Nowshining :). I figured as a near last ditch attempt to correct the problem I would recompile the kernel, but that quit with errors I've never encountered as well;

```
root@gravitron:/usr/src/linux-headers-2.6.24-16# make menuconfig
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:32:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:97: error: expected specifier-qualifier-list before &#8216;chtype&#8217;
scripts/kconfig/lxdialog/dialog.h:187: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:194: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:196: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:197: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:198: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:199: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/dialog.h:201: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:31: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:59: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c:95: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
scripts/kconfig/lxdialog/checklist.c: In function &#8216;dialog_checklist&#8217;:
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;WINDOW&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: (Each undeclared identifier is reported only once
scripts/kconfig/lxdialog/checklist.c:116: error: for each function it appears in.)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;dialog&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: error: &#8216;list&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:116: warning: left-hand operand of comma expression has no effect
scripts/kconfig/lxdialog/checklist.c:129: warning: implicit declaration of function &#8216;getmaxy&#8217;
scripts/kconfig/lxdialog/checklist.c:129: error: &#8216;stdscr&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:130: error: &#8216;KEY_MAX&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:131: warning: implicit declaration of function &#8216;getmaxx&#8217;
scripts/kconfig/lxdialog/checklist.c:137: error: &#8216;COLS&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:138: error: &#8216;LINES&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:140: warning: implicit declaration of function &#8216;draw_shadow&#8217;
scripts/kconfig/lxdialog/checklist.c:142: warning: implicit declaration of function &#8216;newwin&#8217;
scripts/kconfig/lxdialog/checklist.c:143: warning: implicit declaration of function &#8216;keypad&#8217;
scripts/kconfig/lxdialog/checklist.c:143: error: &#8216;TRUE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of function &#8216;draw_box&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:146: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:147: warning: implicit declaration of function &#8216;wattrset&#8217;
scripts/kconfig/lxdialog/checklist.c:147: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:148: warning: implicit declaration of function &#8216;mvwaddch&#8217;
scripts/kconfig/lxdialog/checklist.c:150: warning: implicit declaration of function &#8216;waddch&#8217;
scripts/kconfig/lxdialog/checklist.c:151: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:154: warning: implicit declaration of function &#8216;print_title&#8217;
scripts/kconfig/lxdialog/checklist.c:156: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:157: warning: implicit declaration of function &#8216;print_autowrap&#8217;
scripts/kconfig/lxdialog/checklist.c:164: warning: implicit declaration of function &#8216;subwin&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:171: error: &#8216;struct dialog_color&#8217; has no member named &#8216;atr&#8217;
scripts/kconfig/lxdialog/checklist.c:189: warning: implicit declaration of function &#8216;print_item&#8217;
scripts/kconfig/lxdialog/checklist.c:192: warning: implicit declaration of function &#8216;print_arrows&#8217;
scripts/kconfig/lxdialog/checklist.c:195: warning: implicit declaration of function &#8216;print_buttons&#8217;
scripts/kconfig/lxdialog/checklist.c:197: warning: implicit declaration of function &#8216;wnoutrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of function &#8216;doupdate&#8217;
scripts/kconfig/lxdialog/checklist.c:202: warning: implicit declaration of function &#8216;wgetch&#8217;
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:210: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:220: error: &#8216;FALSE&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:221: warning: implicit declaration of function &#8216;scrollok&#8217;
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of function &#8216;wscrl&#8217;
scripts/kconfig/lxdialog/checklist.c:232: warning: implicit declaration of function &#8216;wrefresh&#8217;
scripts/kconfig/lxdialog/checklist.c:293: warning: implicit declaration of function &#8216;delwin&#8217;
scripts/kconfig/lxdialog/checklist.c:297: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:298: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
scripts/kconfig/lxdialog/checklist.c:310: warning: implicit declaration of function &#8216;on_key_esc&#8217;
scripts/kconfig/lxdialog/checklist.c:312: error: &#8216;KEY_RESIZE&#8217; undeclared (first use in this function)
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2
root@gravitron:
``` 

The very first error is apparently due to lack of ncurses, so;

```
root@gravitron:/usr/src/linux-headers-2.6.24-16# apt-get install ncurses 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ncurses is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ncurses has no installation candidate
root@gravitron:
```

Well so much for a kernel recompilation as a possible means of eliminating the issue:(, I'm open to ideas...

---

### Post by randomnick on 2008-04-29
OK, I've eliminated the FF3 bug as a possible source of my woes, I can't find anything relevant in /var/log, I'm running out of ideas here...

---

### Post by om1 on 2008-04-29
you could try installing htop it might show you more info?

```
sudo apt-get install htop
```

at least on my system it shows more info than top

---

### Post by randomnick on 2008-04-29
Awesome! htop at least allowed me to find what is going on (htop just earned itself a place among my essential add-ons), unfortunately its a bug;

Bug #189939 in python2.5 (Ubuntu)

[https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/189939]("https://bugs.launchpad.net/ubuntu/+source/python2.5/+bug/189939")

Although I have now unequivocally found the source of the problem (see screenshot), I do not see any given resolution at launchpad, or even the ability to consistently reproduce the failed retrace, I don't see this getting fixed any time soon, sigh.

To eliminate the issue I simply renamed usr/share/apport apport & apport-checkreport 
to #apport & #apport-checkreport, respectively. Which *did* eliminate the CPU spiking, but surely completely hosed something...

Well, I don't know if you can really call it a "fix" per se, If anyone has a feasible workaround, Please feel free to post it. I've wasted enough hours with the latest and greatest Ubuntu for a night.

[IMG]http://i59.photobucket.com/albums/g306/staceychandler/Screenshot-4.png[/IMG]

Thanks to all who posted.

---

### Post by jeluranni on 2008-04-29
I'm experiencing the same problem. CPU usage is high or 'sawtooth' and System Monitor and top don't provide any information about the errant process. I've turned off all the bling and other running programs and the problem is still occuring. Very frustrating!

---

### Post by randomnick on 2008-04-29
In a terminal;
```
sudo apt-get install htop
```

```
htop
```

and look for the  apport-checkreport  process to see if it's whats eating your CPU, if it is you are affected by the same Python bug. 
I can't really recommend the "fix" I used above, as to be perfectly honest I have no idea what root/system being unable to locate apport* is going to due to system stability / what else it may to break...

I've read through the wiki as to the use and implementation of apport* , which is crash reporting;

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

You think your system would be fine without it, However renaming and commenting out system files, often (usually) has broad unforeseen and undesirable consequences. 

If it *is* the same bug, please post, as I would be interested in knowing how many other users are going to encounter this. Based on the slim number of postings I could find, I kind of wrote it off as being centric to some of the off-the-wall fringe packages & dependencies I installed.

Good Luck

EDIT: If you are having this particular bug with apport wasting insane amount of CPU cycles, the best way to fix it is using Synaptic to completely remove all instances of apport*.

---

### Post by isparkes on 2008-04-29
I have noticed on my setup (upgraded from 7.10) that viewing the system monitor resource graphs causes the CPU usage to hit and stick at 100%. It appears that the resource monitor is new, sleek, pretty and a bit broken.

Don't know if you are having a similar thing.

Basically, I'm treating it as a minor niggle and not letting it get me down. It's like driving a car with a broken speedo - as long as things seem to be working fine while I look at the road, I don't look at the instruments...

What you could do is log the information to a file for a while and try to catch the rogue process. 

For example you could use something like this (I called it "monitor.sh"):

```
while true ;
do
  top -b -n 1 -H | head
  sleep 1
done
```

then let it run for a while on an otherwise idle machine:

```
ian@ian-desktop:~$ chmod 755 monitor.sh 
ian@ian-desktop:~$ ./monitor.sh 
```

You can watch the output to see if anything jumps out at you.

Dunno if it will help. Just hope it does.

Edit: someone else got there first and with better advice. I love/hate this forum... :)

---

### Post by nowshining on 2008-04-29
for the kernel, install libcurses :)

---

### Post by wawadave on 2008-04-29
I had this saw tooth in monitor as well. I had firefox open it had a utube page open but video was done. I closed that page saw tooth quit.

most likely unrelated. but noticed firefox running in your screen shot.

---

### Post by nowshining on 2008-04-29
htop does seem nicer, i'll change the alias to when I type top it will bring up htop. :)

---

