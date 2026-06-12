---
title: "Absolutely Frustrated And Annoyed Newbie"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by Mist001 on 2012-09-06
Complete newbie here,  so here goes.  Specs: Toshiba Satelitte Pro A200,  Intel dual core 2.2Ghz proc,  2gb memory.

I installed the latest Ubuntu 12.04.1 LTS this morning.  It's _very_sluggish,  taking +30 seconds to respond to anything I do.  The CPU fan is spinning at full speed the entire time,  it just seems a very poor introduction to Linux.  That's the least of my problems though.

There is just a bar/panel running down to L/H side of the screen with various icons on it.  There is no start menu,  absolutely _no_ indication of how to start or run programs. As a result,  I've wasted a good 4 hours this morning trying to make it actually do something useful.  I have to tell you,  after reading all the Linux hype about how good it is,  I'm not impressed.  there is nothing to do unless I want to open some spreadsheet or something.

I want to run Testdisk.  It's installed on my system.  Why can't I find it,  why isn't there just a simple icon to click to make it run?  These are basic tasks which should be available straight out the box for any newbie.  As it stands,  there's no way that Ubuntu can be considered a serious replacement for Windows.

Thanks for reading my rant and if anyone can show me how to run Testdisk (or in fact,  any program) without terminals,  archaic pseudo-DOS commands and all this,  then I'll be quite happy.

Mist.

---

### Post by bodhi.zazen on 2012-09-06
> **Mist001 said:**
> Complete newbie here,  so here goes.  Specs: Toshiba Satelitte Pro A200,  Intel dual core 2.2Ghz proc,  2gb memory.

I installed the latest Ubuntu 12.04.1 LTS this morning.  It's _very_sluggish,  taking +30 seconds to respond to anything I do.  The CPU fan is spinning at full speed the entire time,  it just seems a very poor introduction to Linux.  That's the least of my problems though.

Then next time purchase a computer with Ubuntu pre-installed, then you can rant about how difficult it is to install windows.

You need to purchase Linux compatible hardware if you wish to run Linux, just as you need to purchase windows compatible hardware if you wish to run windows.

> There is just a bar/panel running down to L/H side of the screen with various icons on it.  There is no start menu,  absolutely _no_ indication of how to start or run programs. As a result,  I've wasted a good 4 hours this morning trying to make it actually do something useful.  I have to tell you,  after reading all the Linux hype about how good it is,  I'm not impressed.  there is nothing to do unless I want to open some spreadsheet or something.

I want to run Testdisk.  It's installed on my system.  Why can't I find it,  why isn't there just a simple icon to click to make it run?  These are basic tasks which should be available straight out the box for any newbie.  As it stands,  there's no way that Ubuntu can be considered a serious replacement for Windows.

Thanks for reading my rant and if anyone can show me how to run Testdisk (or in fact,  any program) without terminals,  archaic pseudo-DOS commands and all this,  then I'll be quite happy.

Mist.

testdisk is a command line tool on both windows and Linux.

See - [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by coffeecat on 2012-09-06
> **Mist001 said:**
> 
There is just a bar/panel running down to L/H side of the screen with various icons on it.  There is no start menu,  absolutely _no_ indication of how to start or run programs. As a result,  I've wasted a good 4 hours this morning trying to make it actually do something useful.

That's the Unity desktop you are describing. It's different from what you are used to but just as usable, if not more so. For a guide, see the first link in my sig.

> **Mist001 said:**
> I want to run Testdisk.

Don't even try. Please don't, at least until you've told us what you are trying to achieve. As the links that bodhi.zazen has posted will tell you, testdisk is a tool for partition recovery. I really hope you are not in need of that.

---

### Post by vexorian on 2012-09-06
> There is just a bar/panel running down to L/H side of the screen with various icons on it. have you tried putting your mouse cursor above the one with the ubuntu logo and clicking it? (Akin to the windows logo that is in the start menu?). And the reason you can't find the programs you got "installed in your system" is that ubuntu is *another* system. In theory, you could install wine and run your programs from the windows disk. In theory. But you would first have to learn how to install new software (wine) and how to open your old disk (Somewhere around the personal folder thingy).

It is usually easier to install other programs in your Linux system. Than to try to find the windows ones.

---

### Post by deadflowr on 2012-09-06
Did you try clicking on any of the icons in the L/H side? They aren't just decorations, they're application launchers. Click the top icon to open up what is know as the dash. Dash is the Ubuntu equivalent of the start menu.
Here is the Ubuntu desktop guide for your reading pleasure:

[https://help.ubuntu.com/12.04/ubuntu-help/index.html]("https://help.ubuntu.com/12.04/ubuntu-help/index.html")

Unfortunatley sluggish response tend to be, but not isolated to, graphics card issues. Their is a chance your graphics card isn't Kosher with the stock open-source drivers, at which point you can try the proprietary drivers. To find out what card your system is using, open up a terminal(I know, a pain) type ctrl+t , then:

```
sudo lshw -C display
```

This should tell you what card you're using and from there point you in a direction of how to solve your vexing problem. If you really want help, post the info for others to see for more input.

---

### Post by sudodus on 2012-09-06
Welcome to the Ubuntu Forums,

Maybe you can get started after reading the pdf book at this link

[[COLOR="Red"]_https://leanpub.com/littleorangeubuntubook_[/COLOR]]("https://leanpub.com/littleorangeubuntubook")

There are many other ways to learn about Ubuntu. I suggest that you start reading that 'book', maybe browse the Ubuntu pages on the internet, and then ask one question each time in the Ubuntu Forums (one question per thread).

There are many people here to help. In the beginning we were all newbies ...

---

### Post by critin on 2012-09-06
> **Mist001 said:**
> Complete newbie here,  so here goes.  Specs: Toshiba Satelitte Pro A200,  Intel dual core 2.2Ghz proc,  2gb memory.

  it just seems a very poor introduction to Linux.  That's the least of my problems though.

There is just a bar/panel running down to L/H side of the screen with various icons on it.  There is no start menu,  absolutely _no_ indication of how to start or run programs. As a result,  I've wasted a good 4 hours this morning trying to make it actually do something useful.  I have to tell you,  after reading all the Linux hype about how good it is,  I'm not impressed.  there is nothing to do unless I want to open some spreadsheet or something.

I want to run Testdisk.  It's installed on my system.  Why can't I find it,  why isn't there just a simple icon to click to make it run?  These are basic tasks which should be available straight out the box for any newbie.  As it stands,  there's no way that Ubuntu can be considered a serious replacement for Windows.

Thanks for reading my rant and if anyone can show me how to run Testdisk (or in fact,  any program) without terminals,  archaic pseudo-DOS commands and all this,  then I'll be quite happy.

Mist.

This description sounds exactly like my win8!  (no start button, can't find programs) but just like win8 a user can get to these things with a little exploring. :)

Click the white round icon at the top of the LH bar, or just hit the windows logo key.  Search for anything and it will come up.  Explore and learn the system by clicking the icons at the bottom and right side.

Installing the xubuntu-desktop from Meta Packages-Universe in Synaptic Package manager will give you the menus you want.  You'd click the cog in right upper corner of log-in and choose xfce when logging in.

You'd need to install Synaptic from the Software Center.

You'll enjoy the system if you give it a chance.  Check some youtube reviews.

---

### Post by quequotion on 2012-09-06
**1.** Open a terminal [CRTL]+[ALT]+[T] 
**2.** Type **testdisk**
You'll have to consult the documentation [here]("http://www.cgsecurity.org/wiki/Running_TestDisk") for how to use it.

The rest of this post could still be useful to you in the future, as a guide for running usual programs.

> **Mist001 said:**
> Complete newbie here I really wish things were going better for you. Being lost and confused is a very bad feeling, and sometimes linux can leave new users feeling very lost and confused.

>  I installed the latest Ubuntu 12.04.1 LTS this morning.  It's _very_sluggish,  taking +30 seconds to respond to anything I do.  The CPU fan is spinning at full speed the entire time,  it just seems a very poor introduction to Linux.  That's the least of my problems though. I don't know your hardware specifically, but there are particular packages relating to Toshiba power management that you may have to install or reconfigure. I'm not well informed about them myself, as I haven't installed linux on a Toshiba lately, but I am aware that there has been some difficulty getting power management on these laptops to work out-of-the-box.

> There is just a bar/panel running down to L/H side of the screen with various icons on it.  There is no start menu,  absolutely _no_ indication of how to start or run programs. As a result,  I've wasted a good 4 hours this morning trying to make it actually do something useful.  I have to tell you,  after reading all the Linux hype about how good it is,  I'm not impressed.  there is nothing to do unless I want to open some spreadsheet or something.Welcome to Unity. There is no start menu. That *launcher* serves for what you know as startmenu, taskbar, and quicklauncher.

**[COLOR=RoyalBlue]1. [/COLOR]**Click the Ubuntu icon on the top of the launcher.

This will give you a list of recently used applications and files, which may be empty if you haven't done anything yet. You can type what you want in the text box across the top if you know the name (or nickname) of the program you want to run. *This can also be opened with the Windows key on your keyboard*.

**[COLOR=RoyalBlue]2. [/COLOR]**Type ***the name or nickname of a program you want to run***

If that doesn't help, look at at the bottom of this *lens*.  There should be four or five icons which will give you categories of things. The house gives you the home/recent items lens, the tools give you the applications lens, the page gives you the files lens, the music icon gives you the music lens, and the video icon gives you the video lens.

[COLOR=RoyalBlue]**3.**[/COLOR] Click the **Applications** lens.

 The list may seem shorter than you expect. Under the search box you will see again "**Recently Used**" and under that "**Installed**"** See # more results >** Click there to see more results. This should be the full list of applications installed on your system. This list is a jumble and it may be a long list. Look up at the top right corner of the lens. Click "**Filter Results**" to get categories you can click on to reduce the list. You may select multiple categories.

The next time you want to use ***insert name of program here***, in should be the first thing in the home lens.

> I want to run Testdisk.  It's installed on my system.  Why can't I find it,  why isn't there just a simple icon to click to make it run?  These are basic tasks which should be available straight out the box for any newbie.  As it stands,  there's no way that Ubuntu can be considered a serious replacement for Windows. Keep in mind you've spent years getting used to how windows works, and might have just as much trouble switching over to Mac or whatever else. True, Ubuntu cannot replace Windows (yet), but it can do just about everything Windows can do and it can do lots of things better.

It takes a getting used to, especially since Unity came into the picture.

> Thanks for reading my rant and if anyone can show me how to run Testdisk (or in fact,  any program) without terminals,  archaic pseudo-DOS commands and all this,  then I'll be quite happy. I've posted plenty of rants myself. I wish I could tell you that things are going to get easier, but the fact is that learning how to use the terminal will improve your experience a great deal. There's no customer service department for GNU/Linux; you'll often find yourself on your own with problems when they come up.

If you come to the right place and ask the right questions in the right way, you may get helpful advice from people who have more experience but keep in mind that they are more than likely volunteers.

---

### Post by quequotion on 2012-09-06
> **bodhi.zazen said:**
> You need to purchase Linux compatible hardware if you wish to run Linux The odds of finding Linux ***incompatible*** hardware are much lower than the chances of being ***lucky*** enough that all of your hardware is Windows compatible.

---

### Post by coffeecat on 2012-09-06
> **quequotion said:**
> Type "**Testdisk**"

@quequotion, please read posts #2 and '3. Testdisk is a command line utility for recovering lost or corrupted partitions and will not appear in the dash. My guess is that the OP is assuming that testdisk will fulfill some need of theirs without understanding what it is for.

---

### Post by Mark Phelps on 2012-09-06
Sorry you're having such a hard time ... but you've already discovered two important things about switching to Linux:

First, it is NOT Windows.  IF you expected a desktop like Win7, then you were undoubtedly surprised by the Unity desktop.  Not everyone likes it, like not everyone likes the new Win8 desktop.  At least with Ubuntu, you can switch desktops.

Second, modern PC hardware is built to work with MS Windows, and often requires special MS Windows drivers -- which Linux often does not have.  The Linux community has to play "catch up" while the developers write drivers for new hardware and new features.  That's what's happening with the power management problems with new processors.  It will get sorted out -- but it could take months for the driver updates to come out.

This is just the START of what's going to be different switching to Ubuntu.  If you're expecting a "clone" of Win7, you're only going to get more and more frustrated over time.

---

### Post by vexorian on 2012-09-06
^And if you want a win7 clone, you really should stick to windows 7. It is a terrible OS, but it is the best OS at being windows 7.

---

### Post by nothingspecial on 2012-09-06
If you want some help with a specific problem, start a new thread in the appropriate sub-forum with as much detail about your issue as you can. Include any errors you have and what you have tried already.

Closed.

---

