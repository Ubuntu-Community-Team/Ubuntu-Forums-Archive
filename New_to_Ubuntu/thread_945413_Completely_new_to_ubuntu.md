---
title: "Completely new to ubuntu"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Optimus_Jazz on 2008-10-12
And have to say im liking it so far.Its my first time using a linux based OS and i dont know too much about it.I get the general idea of how to install software but some of the programs im running ( for example Amarok ) are quite slow,and the whole gui can be sluggish at best.

I have a compaq laptop,with and AMD Turion 64 processor and an ati graphics card.I know theyre not the best specs available but surely theyre strong enough to run a linux os?

Also is there anyway to edit the GUI in linux,like tweaking sounds from pidgin and changing the desktop folder colors etc?

cheers for any help.

---

### Post by forger on 2008-10-12
1) Which release/version of Ubuntu are you using? Ubuntu hardy heron 8.04.1?
2) Go to System > Administration > Hardware drivers if any drivers have to be checked and installed
3) Look at the output of this command in terminal (Applications > Accessories > Terminal):
```
lspci
```
Are there any devices listed under "Unknown device" ?
4) post the output of this command:
```
cat /etc/X11/xorg.conf
```
5) When you say sluggish what do you mean? Is it sluggish as in when you start Applications > Office > openoffice word processor and takes 5 minutes to load it?
6) How much RAM memory do you have? What's the speed of your processor?

These information will help out a lot in resolving your 'sluggish issue'.

---

### Post by Optimus_Jazz on 2008-10-12
1) Im using version 8.0.4.1 but i dont know anything about handy heron

2) All drivers are installed

3) No drivers are listed as an unknown device.

4) ```
Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

5) When im using Amarok for example,it takes about 10 secnds for the song to load into the player,and quite often the GUI of the player will turn grey and i have to force quit the application.

Also when i was using firefox earlier, it kept crashing and i had to restart it but i dont seem to be having that problem now.

6) I have 1 gb of ram

 When i type into Terminal: cat /proc/cpuinfo
 I get :


```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 36
model name	: AMD Turion(tm) 64 Mobile Technology ML-34
stepping	: 2
[COLOR="Red"]cpu MHz		: 1800.000[/COLOR]
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
bogomips	: 3585.64
clflush size	: 64

```

---

### Post by aeiah on 2008-10-12
yea something isnt quite right.. what happens when you launch amarok from the terminal? (by typing 'amarok' ) does it report any kind of error in there when you try and play a song etc? 

does the system monitor report anything chewing through memory, or your ram / cpu / swapfile usage being quite high? (menu > system > administration > system monitor )


it does seem like something's wrong. ive got an amd 3800 x2 and 1gb ram, and my system is pretty snappy.

---

### Post by Optimus_Jazz on 2008-10-12
When i typed amarok into the terminal to start it up but a few warnings were displayed

```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
[COLOR="Red"]kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ccd0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809ccd0 ): KAccel object already contains an action name "play_pause"[/COLOR]
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)


```

Screen shot of system monitor :

[[IMG]http://img55.imageshack.us/img55/3412/screenshotsystemmonitoryr5.th.png[/IMG]](http://img55.imageshack.us/my.php?image=screenshotsystemmonitoryr5.png)[[IMG]http://img55.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Optimus_Jazz on 2008-10-12
bump

---

### Post by linux4life88 on 2008-10-12
To change the look of Ubuntu check out:

[http://gnome-look.org/](http://gnome-look.org/)
[http://art.gnome.org/](http://art.gnome.org/)

If you need help installing themes or what not just ask and I can help. Also on gnome look, go to GTK 2.0 to change theme and Icons to change the look of folders. If you need more information just ask.

---

### Post by steveneddy on 2008-10-12
A lot of your questions can be answered by checking out the links in my sig.

Welcome to Ubuntu.

---

### Post by OutOfReach on 2008-10-12
> **Optimus_Jazz said:**
> 

Also is there anyway to edit the GUI in linux,like tweaking sounds from pidgin and changing the desktop folder colors etc?

I think Pidgin supports sound themes, I am not completely sure.

As for changing themes (Window borders, panels, folder icons, etc)
They can be found here: [http://gnome-look.org/](http://gnome-look.org/)

Welcome. :)

---

### Post by Optimus_Jazz on 2008-10-13
Thanks guys this will keep me busy for the time being!:popcorn:

---

### Post by itix on 2008-10-13
I was wondering, are you perhaps using the default i386 version of ubuntu?
My little brother used that in the beginning on his 64-bit selfbuilt desktop (with some help from his 8 year old friend with dyslexia where I failed... Gah todays youth). He had the same problems as you describe.

If you're using the wrong architecture (i386 on a 64-bit processor, which your processor is), It will work, only not as good as is should

---

### Post by Drakkor on 2008-10-13
I looked at your screenshots,it seems that your cpu is running at or near max. I staarted mine via the terminal,and as you can see, it spiked breifly at 80% on one of the  processors (intel duo-core),but then quickly fell.
you could maybe try another player e.g. Exaile or Audacious ? :)

---

### Post by Optimus_Jazz on 2008-10-13
Im not too sure how to find this out because a friend basiaclly installed the whole thing for me,do i check this through terminal?

---

### Post by Drakkor on 2008-10-13
I need to add that I had most of the same errors in the terminal that you did, it still works fine,sometimes the terminal error don't mean much. :)

---

### Post by Bölvaður on 2008-10-13
That over usage of the cpu can be understood if it wasn't built past 3 years.... which I think it isn't, so there might be some program struggling in the background perhaps?

Follow the usage of all the processes to try to spot the evil one.

And I also noticed that you have way too high ram usage if you wasn't doing enything else than starting up amorok. It should be closer to 300 mb

---

### Post by itix on 2008-10-13
I have no idea how to do this via the terminal. You can however download a 64-bit .deb and see if the system rejects it.

[http://packages.ubuntu.com/dapper/libfox1.2c2](http://packages.ubuntu.com/dapper/libfox1.2c2)

Download the amd64 package from that link. Don't install it, just see if the package installer says "wrong architecture" or anything like that.

---

### Post by Optimus_Jazz on 2008-10-13
It wont let me download it,any time i click a link it goes to another page?

Amorak is running ok now as long as i dont have the GUI open in front of me.

Although i like linux there seems to be WAY too much fiddling to do to get up and running but i suppose its all a learning curve!

---

### Post by itix on 2008-10-13
It is, rest assured. I was a windows user just a year ago and installed a dual boot with windows and linux just for fun but found myself booting into linux more and more and eventually I just used windows for adding songs to my iPod. When I eventually found a replacement for that, I ditched windows and haven't used it (on any of my own computers at least) ever since.

My brother had really high cpu usage as well. Since your friend installed it, It might just be the architecture.

I've found an easier way to check architecture. Check the "about" in firefox. If it says linux i686 like mine does, then you have the wrong version...

[IMG]http://i33.tinypic.com/senmo1.png[/IMG]

---

### Post by Optimus_Jazz on 2008-10-13
indeed it does say  

Linux i686; en-US

Whats my net step?

---

### Post by itix on 2008-10-13
Grab a phone, call your friend and tell him he is an idiot, and have him install the amd64 version of ubuntu. You can of course install it yourself. It isn't too much trouble. Burn a cd with the amd64 version or use *unetbootin* to create an installable usb drive.

---

### Post by Optimus_Jazz on 2008-10-13
Well at least the problem is solved as far as why its so choppy!Thank you :D
Im going to give it a go installing it myself,but i have a question:

My hardrive was partitioned so now it has windows and ubuntu on it.
If i just pop in the disk with the version of ubuntu i need,will it install over the old version or create a new partition?

---

### Post by hyper_ch on 2008-10-13
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by itix on 2008-10-13
You'll be able to choose yourself. There is this program on the live CD that allow you to erase and modify partitions called Gparted. While in the live CD environment, it can be found under *system => administration => partition editor*. 

Just use that to delete your ubuntu partition and then go through the installer. When it comes to partition setup, there is an option called "install ubuntu on the largest continous free space". Ubuntu will automatically detect windows and add it to the boot list that you see when you start your computer.

Just make sure that it is the ubuntu partition you delete. Note things like size and stuff before you use the program. Do post on the forums if you have any problems. There are tons of expertise here :popcorn:

---

### Post by Optimus_Jazz on 2008-10-13
Thanks Itix youve been tons of help!
Will get around to this later tonight so will more than likely be on asking plenty of questions:lolflag:

---

### Post by itix on 2008-10-13
No probs :-D

---

