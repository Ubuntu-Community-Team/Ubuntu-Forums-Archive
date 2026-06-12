---
title: "How to Launch Gparted from Boot CD (Macbook Pro)?"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by linuxn00bface on 2012-08-06
Okay so I was one of the morons who got suckered into the Apple cult, and now I'm looking at a piece of crap made in China that cost an arm and a leg because it has a half-eaten apple in white on it... /rant

I got the boot CD to boot up on 10.6 with no problems, and it seems to be functional. Looks pretty damn slick and intuitive, I must say... I've been meaning to learn linux for some time. I disgress.

I followed the (incredibly) detailed and helpful instructions: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

However, this trips me up: "Once booted, you have a Ubuntu desktop. Start gparted (partitioning  tool) by navigating to System > Adminstration > Partition Editor"

There is literally no "System" , just System Settings, and inside it there is certainly no "Administration." When I search it in the Applications, it's there, but I can't launch it from there either. Where's it hiding?

Thanks :)

LNF

---

### Post by drs305 on 2012-08-06
Welcome to the Ubuntu forums.  :-)

If you are running 12.04 (there isn't a 10.6 ubuntu, if that's what you meant; or you could be using 10.04, or maybe it's an apple 10.6). Anyway, if you installed or are using Ubuntu 12.04, click the HOME/Dash button - it's the Ubuntu symbol at the top left corner of the screen. Type "gparted" and press enter.

You can also open it from a terminal with:
```
gksu gparted
```
To open a terminal press CTRL-ALT-t

---

### Post by audiomick on 2012-08-06
Hi.

Don't know what is going on there, but here is a way to start gparted that I think should work.

Can you start a terminal? It should be available in the applications menu. Bugger, I've forgotten what "Zubehör" is called in the English menu. That's the section where things like the calculator, the editor, the screen shot application and so on are. Might be "utilities".

Anyway, find the terminal and type
```
gksudo gparted
```

That should start it. On a normal install, you would get asked for your password. I don't think that happens in the live environment, as there is no password set.

---

### Post by ajgreeny on 2012-08-06
> **audiomick said:**
> Can you start a terminal? It should be available in the applications menu. Bugger, I've forgotten what "Zubehör" is called in the English menu. That's the section where things like the calculator, the editor, the screen shot application and so on are. Might be "utilities".
Just to save you worrying about this and not sleeping all night, the word you can't remember is "Accessories"

---

### Post by audiomick on 2012-08-06
Thanks AJ. ;)

---

### Post by linuxn00bface on 2012-08-07
Thanks guys! I can't believe how stupidly easy that was. There was some initial trouble and eye-bleeding Google searching during the partitioning and repartitioning parts, especially once I realized that since I was wanting to pretty much abandon my Mac, splitting 50/50 was a poor decision since I couldn't change it, so I had to redo everything. Surprisingly, my computer didn't explode, and Ubuntu is now set up with all my desired apps. Ubuntu FTW!

Now I'm just reading some intro docs, and holding my breath hoping I don't royally F something up with the command line... *knocks on wood*

---

### Post by TheGuyWithTheFace on 2012-08-07
Welcome to the forums! 

If you're worried about screwing things up with the terminal, you may find this to be of interest:
[http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

Also, I'm glad you got your problem solved, would you mind marking it solved to avoid confusion?

---

