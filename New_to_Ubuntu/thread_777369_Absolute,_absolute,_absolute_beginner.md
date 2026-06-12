---
title: "Absolute, absolute, absolute beginner"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Kurys on 2008-05-01
Hi,  Being a Windows user, I am totally lost when looking at the main screen when this laptop finally boots up. I was given an old laptop with an old Ubuntu 4.10 Warthog OS.  I'm looking for a local linux users group because I need more guidance than you could reasonably give me in a question-answer format. But maybe you can clarify something basic.    How do I shut the computer down safely? In Windows of course there is that start button in the lower left corner of the screen. On this laptop there's an icon of a notepad and pencil which when highlighted says "Click here to restore hidden windows." I just don't recognize anything on this desktop window. I'll describe below if it helps.    Top toolbar on left has a footprint icon, then the words Application Computer, then the Mozilla Firefos icon, Evolution Groupware icon, then a Gnome help icon. Along right side shows icon saying No Wireless Devices, the battery icon, the volume icon.   Back to the bottom. I mentioned the notepad where the Windows start button usually is. Along the right side are 4 shaded boxes but with the first one darkened black. And then a trash bucket.    So at the moment all I can do is use the power button because I can't find any key combination or icon to shut it down.  Since I can't even get the basics started and don't have it on a network I can't even try out to see if it has internet available. 
K

---

### Post by wannadumpwindows on 2008-05-01
You can always open a terminal and type:

```
sudo shutdown now -h
```

It should be under Applications >> Accessories >> Terminal

---

### Post by Paqman on 2008-05-01
You shutdown icon should be top right. Little red square.

To install software go to Applications > Add/Remove
To customise your desktop go to System > Preferences > Appearance
The boxes at the bottom right are your virtual desktops. You have four to start with.

What else can we help with?

---

### Post by Kowalski_GT-R on 2008-05-01
type ```
sudo shutdown now -P
``` from a "terminal window" to shut down your comp.

Try the search feature of the forums, you'll find every answer you need: You've come to the right place for Ubuntu informations...;)

Welcome to the forums!:) I hope you'll make good use of your Ubuntu Laptop!

---

### Post by cartisdm on 2008-05-01
> **Kowalski_GT-R said:**
> 
Try the search feature of the forums, you'll find every answer you need: You've come to the right place for Ubuntu informations...;)


Or you could just view all threads started by me, I'm sure I've asked every possible question already haha:lolflag:

And yes, Welcome to the Forums!

---

### Post by ayenack on 2008-05-01
If I remember correctly the shutdown tab is under System at the bottom on the top tool bar. Also I think you should be able to add shutdown to either tool bar by right clicking on it and selecting add then scrolling down until you find Quit or Shutdown can't remember now.

BTW. Use.

**sudo shutdown now -P** (The -P stand for power off if you want to shutdown from terminal. If you need to reboot instead of shutdown use -r instead, which stands for reboot.)

Ask as many questions as you need that's what the forums are for ;)

---

### Post by howlingmadhowie on 2008-05-01
i thought the system menu has a shutdown option. have a look and see. if not, i think you can add icons to the toolbar by right clicking the toolbar and selecting add. then a window will open with available icons. one of them will be shutdown or stop or whatever it's called

---

### Post by mali2297 on 2008-05-01
It's a really old edition of Ubuntu that you got there, it will be difficult to give you direct instructions since a lot has changed. Click on the footprint etc and browse through the menus, there should be an option to logout/shutdown/exit/whatever somewhere.

---

### Post by MONODA on 2008-05-01
what are the specs for the laptop, maybe you should install a later version of ubuntu?

---

### Post by Cadmus on 2008-05-01
I do agree with the upgrade route, Ubuntu has matured a great deal even since I've started using it (and that was Feisty).

If your laptop is geting on a little bit you should try downloading and installing Xubuntu, which uses XFCE instead of Gnome. Gnome and XFCE are window managers, the part of the operating system that gives you a desktop. XFCE uses less RAM and CPU, but at the expense of some of the prettier features of Gnome.

What you may find a little confusing is that the menus are at the top by default.

When it comes to networking you're best off using a network cable in the first instance, as wireless brings its own problems and is best set up once you have a better handle on things.

Here's my top 3 "I wish I'd known that first" of Linux
[LIST=1]
[*]Programs come from package managers (like Synaptic) rather than downloading a file from the web
[*]Needing to use the terminal is never a failure, it's sometimes just the most elegant way of getting something done
[*]Files don't need extensions to work, but they often have them for convenicne
[/LIST]

Welcome to the forums and I hope we can help you out.

---

### Post by bodhi.zazen on 2008-05-01
> **Kurys said:**
> Hi,  Being a Windows user, I am totally lost when looking at the main screen when this laptop finally boots up. I was given an old laptop with an old Ubuntu 4.10 Warthog OS.  I'm looking for a local linux users group because I need more guidance than you could reasonably give me in a question-answer format. But maybe you can clarify something basic.    How do I shut the computer down safely? In Windows of course there is that start button in the lower left corner of the screen. On this laptop there's an icon of a notepad and pencil which when highlighted says "Click here to restore hidden windows." I just don't recognize anything on this desktop window. I'll describe below if it helps.    Top toolbar on left has a footprint icon, then the words Application Computer, then the Mozilla Firefos icon, Evolution Groupware icon, then a Gnome help icon. Along right side shows icon saying No Wireless Devices, the battery icon, the volume icon.   Back to the bottom. I mentioned the notepad where the Windows start button usually is. Along the right side are 4 shaded boxes but with the first one darkened black. And then a trash bucket.    So at the moment all I can do is use the power button because I can't find any key combination or icon to shut it down.  Since I can't even get the basics started and don't have it on a network I can't even try out to see if it has internet available. 
K

Wow, that is a very old version of Ubuntu. I suggest you install 8.04 or if you need a light weight OS try Puppy linux, Wolvix, Zenwalk or the fluxbox version of PCLinuxOS.

---

### Post by cartisdm on 2008-05-01
> **bodhi.zazen said:**
> Wow, that is a very old version of Ubuntu. I suggest you install 8.04 or if you need a light weight OS try Puppy linux, Wolvix, Zenwalk or the fluxbox version of PCLinuxOS.

+1 to Puppy linux and also give Xubuntu a shot.

Great thing about Puppy is you can run it as a liveCD and still save your sessions after a reboot  [Puppy Linux FAQs]("http://puppylinux.com/faq.htm")

---

### Post by Kowalski_GT-R on 2008-05-01
Hi Kurys,

I would have suggested a more recent version of Ubuntu myself.
I also understand that, coming from the Windows world, concepts like "distribution", "XFCE", "Xubuntu" or "Puppy" may not be obvious to you.

If you care to give up your laptop specs, people may point you to the best solution available. Ubuntu has come a long way since 4.10...

hope this helps,

Andre

---

### Post by drrwhistle3 on 2008-05-01
Just a quick message that you need to remember as I have recently been through this.  This community is superb!!  Ask them a question and they will respond before the hour is up.  The biggest thing to remember is a lot of the community have been doing this for a while and don't know your skill level.  Coming from XP - like myself - we know nothing.  If you don't undersatnd something ask again and be specific then they will ellaborate.  Don't make the mistake I did and thought I could fight through it and just get deeper into a hole.  NO QUESTION IS TOO DUMB _ ASK!!

Oh yeah and to quote:  sudo+linux+beer = disaster

---

### Post by Paqman on 2008-05-01
> **drrwhistle3 said:**
> 
Oh yeah and to quote:  sudo+linux+beer = disaster

Coversely, [sudo+sandwich = win!](http://xkcd.com/149/)

---

### Post by Kurys on 2008-05-01
Hi all, Thanks so far.  Didn't expect this so quick.  Okay, let's start.  This laptop is an HP Omnibook XE2 433celeron w/192MB Ram and 4.8G HDD.  Sounds like maybe I should try to get that Puppy Linux on it.  Thing is my internet access is only through this regular computer and not the laptop.  I don't even know if the floppy, CD or USB ports work, but probably at least one of them does.  So how big is this Puppy Linux and once I have it in a floppy, CD or flash, is it self explanatory to overwrite the Ubuntu 4.10 or so I need to reformat first---and I don't know how to do that either.

---

### Post by Kowalski_GT-R on 2008-05-01
mmmhhh.....no internet is bad. No spare connections from your modem?

I'd like to state one less obvious aspect here. It all depends on 

a) how much time you have
b) how much fun you're having :)
c) whether Ubuntu 4.10 is not achieving its goals

I'm far from expert, and would stick to an Ubuntu-based distro mainly for practicality:
here:
[UbuntuLite]("http://ubuntulite.tuxfamily.org/") --> 7 days to go for vers. 0.8, roll on!!
[Fluxbuntu]("http://fluxbuntu.org/js.html")

these should fit your laptop. May I ask what do you plan to use it for? Office? Media? Browsing?

anyway, have a look here: [Distrowatch]("http://distrowatch.com/search.php?category=Old+computers&origin=All&basedon=All&desktop=All&architecture=i386&status=Active")

or better here:
[Operating systems for really, really old computers]("http://ubuntuforums.org/showthread.php?t=575456")

ciao,

Andre

---

### Post by Kurys on 2008-05-01
No internet connection because I'm on a business network (Cat5).  And anyway, there doesn't seem to be any kind of menu or anyway I can instruct the laptop to do anything.  That's why in the beginning I asked about shutting down.  There's just nothing recognizable.

All I intend to do with this laptop is internet browsing, e-mail and basic office typing or spreadsheet.  Nothing heavy.

---

### Post by ayenack on 2008-05-01
> **drrwhistle3 said:**
> 

Oh yeah and to quote:  sudo+linux+beer = disaster

drrwhistle3:LOL

---

### Post by forumache on 2008-05-01
> **Kurys said:**
> No internet connection because I'm on a business network (Cat5).  And anyway, there doesn't seem to be any kind of menu or anyway I can instruct the laptop to do anything.  That's why in the beginning I asked about shutting down.  There's just nothing recognizable.

All I intend to do with this laptop is internet browsing, e-mail and basic office typing or spreadsheet.  Nothing heavy.

OK, now you say there is no kind of menu. But before you described some Application menu, Mozilla Firefox and Evolution Groupware icons...

Use Firefox for internet browsing.
Use Evolution for email (if you don't have/wanna use web based email gmail, hotmail, yahoo)

Start Firefox and see if you can browse.

Good luck.

---

### Post by mali2297 on 2008-05-01
> **Kurys said:**
> No internet connection because I'm on a business network (Cat5).  And anyway, there doesn't seem to be any kind of menu or anyway I can instruct the laptop to do anything.  That's why in the beginning I asked about shutting down.  There's just nothing recognizable.

All I intend to do with this laptop is internet browsing, e-mail and basic office typing or spreadsheet.  Nothing heavy.

Don't you see any menus when you click on the footprint icon, Application or Computer?

You intend to browse the web, does that mean that you eventually will have an internet connection?

---

### Post by cartisdm on 2008-05-01
> **Kurys said:**
> I don't even know if the floppy, CD or USB ports work, but probably at least one of them does.  So how big is this Puppy Linux and once I have it in a floppy, CD or flash, is it self explanatory to overwrite the Ubuntu 4.10 or so I need to reformat first---and I don't know how to do that either.

It's only about 50-90MB, depends on which one you grab.  Can easily be thrown on a USB drive.

In all reality you don't need do anything at all, just boot from the CD (or whatever you put Puppy on).  Check out Puppy Linux's FAQ page for how it works in regards to saving it's liveCD session.  You won't need to format or anything but if you decide you like it, it might be worth clearing up the space on the harddrive since you said it's like 4gbs.

---

