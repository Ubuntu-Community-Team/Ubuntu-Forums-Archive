---
title: "Ubuntu hardy questions"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by justinhj on 2008-04-26
I have a problem when I boot up after upgrading to Hardy from gutsy. The login screen is showing only the upper left quarter. I can still login and everything is fine afterwards.

Also, is there a way to skip the Ubuntu start up screen with the progress bar, and instead see the text scrolling showing me what is going on? That's one of things I used to prefer about Linux over Windows; you can actually see what it was doing if it goes wrong.

---

### Post by sam_delta on 2008-04-26
to remove the boot splash screen

first make a backup of your menu.lst file

```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

go into a terminal and type 

```
 gksudo gedit /boot/grub/menu.lst
```

find the "kernel line", if more than 1, the latest kernel, and remove the words "quiet splash" off the end of the line, save and boot screen is gone.

tell us how it goes
sam

---

### Post by frup on 2008-04-26
I have just one addition which always need to be pointed out and that is that sudo is for command line only apps and that gksudo is preferred for GUI apps. There is an important reason why but I never remember I just apply.

---

### Post by sam_delta on 2008-04-26
ight, thx for pointing that out frup, already edited my previous post

heres a brief explanation on sudo vs gksudo
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

sam

---

### Post by justinhj on 2008-04-26
Thanks guys. I've gotten rid of the splash screen, that's a lot better. 

I still have the very large ubuntu login screen. It looks like it's 4 times bigger than my screen. Once I login I'm fine. 

Also, I'm using compiz and emerald, and any saved session windows that open up when I begin don't have window decorations. I have to close and re-open them.

---

### Post by sam_delta on 2008-04-26
try this:

install simple-ccsm package (compiz advanced desktop settings) then, go into system>preferences>Advanced desktop effects settings

find the Window Decoration plug-in, you can use the top left filter to search for it.
click on "window decoration" to enter plugin settings and search for "Command:" in that line type "emerald --replace", instead of compiz-decorator

let us know if it works,
sam

---

### Post by justinhj on 2008-04-26
I should have mentioned I installed compiz-git, which would have to be removed to install simple-ccsm

---

### Post by justinhj on 2008-04-26
Trying to install ccsm removed compiz-git and now I'm kind of screwed. I followed the instructions at the start of this thread to reinstall it

[http://ubuntuforums.org/showthread.php?t=763829&highlight=compiz-git](http://ubuntuforums.org/showthread.php?t=763829&highlight=compiz-git)

But I have no window decoration now, and starting compiz-git fails.

Edit: I'm ok now, I just installed everything from the regular hardy packages and removed compiz-git.

---

### Post by justinhj on 2008-04-26
I found the window plugin you mentioned and I am using emerald --replace

---

### Post by darkoz on 2008-04-26
> **justinhj said:**
> 

I still have the very large ubuntu login screen. It looks like it's 4 times bigger than my screen. Once I login I'm fine. 



I had this same problem. It was because X was configured wrong for some reason. edit /etc/X11/xorg.conf with your editor of choice and find the "Screen" section. It will look similar to:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes	"1280x1024@60"	"1280x1024@50"	"1024x768@60"	"1024x768@50"
	EndSubSection
EndSection
```

All you need to do there is comment out the "Virtual" line like so:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GTS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
#		Virtual	2048	1536
		Modes	"1280x1024@60"	"1280x1024@50"	"1024x768@60"	"1024x768@50"
	EndSubSection
EndSection
```

That should fix your login problem.

---

