---
title: "Moving to Ubuntu, with trepidation"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Brewskie on 2008-04-24
I want to either switch over to Ubuntu, from Vista, or dual boot but I have some issues that I need answered.

I've been around puters since around 1983. So I've seen a lot of stuff come and go. I started out on a Univac 9030 mainframe (card readers and all), if that gives a reference point.

One of the biggest reasons I latched onto Windows was because of the lack of command line requirements. I know early versions of Windows had a lot of it (command-line stuff), but recent builds, like XP and Vista, using a command line interface is all but gone. After learning RPG, Fortran, COBOL, PhP, C++ and all, I would rather not deal with a system where I have to learn what amounts to a new language just to use it.

How much of Ubuntu is driven by input from a command line? Is it entirely graphical, or are there many commands that I'll have to learn? I know Ubuntu is driven by Linux (a command line based system), but how much of Linux is hidden by Ubuntu? I know that, up to Vista, all windows was was a graphical interface to DOS and I assume Ubuntu is the equivalent for Linux...is that a correct assumption?

I am running my own server for my sites using cPanel. But occasionally I have to telnet in to the box to do certain things. How much different is this Linux to my Apache/Cpanel set up?

My main uses of my computer is for gaming (like Crysis etc), working on my web sites (currently running Firefox 3.0b5 and Homesite for authoring), and PaintShopPro XII.

For gaming I want to network with my sons XP machine and their Xbox360. Using Vista has been a nightmare to do this in. How much easier is it under Ubuntu? This issue was really the final straw where I feel the need to dump Vista, and Microsoft.

Can I get games to run under Ubuntu? Or will I have to switch to Vista to play these games? I really haven't seen whether these games come with a Linux version though.

And all these flavors of Ubuntu. Like Kubuntu et al. It's rather confusing to figure out what each of them are for. Their strengths and weaknesses. I've looked at them, but it's still confusing to know which flavor would be good for me. I love graphical environments, a lot, so which is best to really show off a graphical interface?

I have had nothing but problems using my SoundBlaster Audigy2ZS under Vista. Is there a driver for this card in Ubuntu? What about volume settings and equalizers for this card?

Are there native Intel chipset drivers? What happens regarding this area?

What about when the time comes when I want to update the BIOS. Am I going to be forced to use a command line version of the updater?

My set up is below....does anyone see where I may have problems, knowing what I've said above, with this system?

Intel Quad Q6600 2.4ghz
Intel DG33TL Mainboard
2 gigs ram
GeForce 8500gt 256 mb
Soundblaster Audigy2 zs
About 200 gigs free on my C: drive
Westell VersaLink 327W modem,firewall,4 port router. Using the wired side, not wireless. Using onboard ethernet.

Even though I think DRM is just another variant of a trojan I am still addicted to the Windows environment and I am having a hard time giving it up.

Is Ubuntu ready for someone like me, who wants to stay away from command line interfaces?

Please, someone convince me to switch to Ubuntu from Windows.

Thanks for any and all comments!

PS....Did you know there is still a Univac Users Group? And that old Univac 9030 filled a small room. It's equivalent to today's computers? A Pentium 286 #-o

---

### Post by jaytek13 on 2008-04-24
That's a lot of questions. I'll address the first one, anyways.

In no way is Ubuntu to Linux as Vista is to DOS. Ubuntu doesn't hide anything from you, and actually requires you use the command line more than a lot of other distributions because unlike those other distributions Ubuntu doesn't have a GUI for absolutely everything imaginable. 

But even where the GUI does exist in Ubuntu, there is always a way to accomplish the same thing at the command line. 

There are a ton of commands, but only a few basics that you would need to learn to make your way around.

---

### Post by mrgooding on 2008-04-24
I've recently started dual booting too (vista and ubuntu). I've found the command line in Ubuntu to be a very powerful tool - many tasks can be accomplished via a GUI of some description, but the command line seems to give you a lot more power / flexibility in what you do. 

As a basic example, it's far easier to cut and paste commands (having first checked someone hasn't posted something harmful, of course) from the wealth of useful posts on these forums than to follow peoples instructions on using GUI interfaces, which can sometimes be a bit vague.

I've yet to get to grips with the more powerful features of the command line, but i'm sure soon i'll be using it more.

I hope this helps, and good luck - maybe try out the live CD before you make the leap!

---

### Post by Golem XIV on 2008-04-24
I thought I had my fill of CLI with DOS and I avoided using it in Windows if at all possible, but after fiddling with Ubuntu for a few months, I find myself typing in the terminal more often and not minding it.  While most of the stuff can be accessed through a GUI, sometimes it is simpler, faster and more efficient to just type it in.  There are lots of things that make your life easier while typing, autocomplete springs to mind.  For example, if I want to install a package foten it is quicker for me to open aterminal and type **sudo apt-get install foo** than to open Synaptic, wade through the list to find the package, select it and install it.  Not that Synaptic's interface is bad - you can search, filter, type etc. to find what you want - but still in many cases I prefer the terminal.

Gaming may be a problem.  Windows games, especially recent releases, either will not work through Wine, will require a lot of tweaking to get them to run or will run poorly.  I would advise to double-boot with Vista/XP to be able to play.

As for the flavours question:  All these systems have the same Ubuntu "heart".  The difference is in the software package that comes with the standard installation.  For example, Kubuntu uses the KDE desktop manager instead of the standard Gnome, while Xubuntu uses the small-footprint Xfce desktop manager. Edubuntu is intended for educational purposes so it's software package is heavily geared towards this, and so on.

Hardware compatibility has improved a lot, especially now with the Hardy Heron release.  If you're concerned, download and burn the Desktop CD.  It can run as a "live" system, i.e. run from the CD without touching your Windows installation.  If you're happy with it, you can proceed to a full installation.  You can also run Ubuntu as a "windows application" through Wubi.

---

### Post by SDL on 2008-04-24
Regarding games, you can use software called Wine to run some of them. More information on which games run under Wine can be found here:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

This is a bit of a fiddle and only works well for a few Windows games unfortunately. I don't know first hand but it looks as though Crysis doesn't work under Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107)

There are a few commercial games that run natively on Linux such as the Quake games. There are also some really good open source games such as Nexuiz or Freeciv but if you're really keen on flashy graphics, I would recommend that you dual booted Vista for them. Wine is only a good option if you're really dedicated to not running Vista.

Regarding ease of use, I have no programming experience whatsoever and no real desire to gain any and have been using Ubuntu quite happily for a year or so. You wouldn't need to use the command line for everyday tasks but it can be very useful when you run into problems - I've found most of the help that the nice people on these forums give tends to be in the form of commands to put into the command line terminal.

The latest release of Ubuntu comes with Firefox 3.

As far as the main variants go, Ubuntu uses the Gnome desktop, Kubuntu uses KDE and Xubuntu uses Xfce. I think the only real differences between Ubuntu and Kubuntu are aesthetic. Xubuntu is supposed to be quicker and run on older machines. I've always been perfectly happy with regular Ubuntu but if you Google KDE, you might find that you prefer the look of Kubuntu.

---

### Post by kansasnoob on 2008-04-24
Just give the Live CD a test drive. If you're running a fairly new computer, say at least 1.5 G cpu w/ at least 1 Gb of RAM you can run it enough to find out if you love it or hate it.

Now, with 8.04, you can go one step further and run it inside Windows with Wubi.

And, a very basic dual boot is not that complicated. I did it and I'm not smart! Three ex-wives will vouch for that.

---

### Post by FuturePilot on 2008-04-24
As to the command line. For day to day use, you'll probably never need to touch the command line. The only time you will probably need to use it is if you need to configure something in the system, and even then, not all the time. There are quite a few GUIs to configure various things.

---

### Post by Joeb454 on 2008-04-24
I agree with FuturePilot, you'll hardly ever have to touch the CLI, but in time you may want to.

I use it more than I ever expected to now. Just because I can :D

---

### Post by FuturePilot on 2008-04-24
> **Joeb454 said:**
> I agree with FuturePilot, you'll hardly ever have to touch the CLI, but in time you may want to.

I use it more than I ever expected to now. Just because I can :D

Hehe, there's something about the command line that you get addicted to. I've become very comfortable using the command line. Maybe it's the cool transparency effect? :lol:

---

### Post by Brewskie on 2008-04-25
Well....I threw my hat in the ring and "tried" to install Ubuntu...and Kubuntu.

Too many errors to list right now.

The last try at installing I came to a GRUB> prompt. Whatever GRUB is.

Thanks, Ubuntu, for wasting 12 hours of my time.

Ubuntu = Epic Fail.

---

### Post by tango_ninja on 2008-04-26
GRUB is a bootloader....loads the OS and gives you options if you're dual-booting.

If you want some help in getting things to run properly give us some of the errors and we'll help get you up and running.

---

### Post by Brewskie on 2008-04-26
> **tango_ninja said:**
> GRUB is a bootloader....loads the OS and gives you options if you're dual-booting.

If you want some help in getting things to run properly give us some of the errors and we'll help get you up and running.

Thanks for your reply tango.

It's taking me a while to write it all down. I've tried three different ways to install. I only did not try the partition install...It seems to me that that was a good idea.

I'll post what happened when I'm done writing it up.

---

### Post by tango_ninja on 2008-04-26
Sounds good. Another thing to try might be to run the liveCD (Ubuntu contained on cd) and see if that works well on your computer. This will also give you the ability to play around and see if you like the gui.

---

### Post by Paqman on 2008-04-26
> **Brewskie said:**
> 
How much of Ubuntu is driven by input from a command line?

Depends what you're doing. Most users only ever touch the command line to edit system files. If all your hardware works correctly you might not ever have to do that.

> 
I am running my own server for my sites using cPanel. But occasionally I have to telnet in to the box to do certain things. How much different is this Linux to my Apache/Cpanel set up?

That's a fair analogy. cPanel is GUI that drives the underlying CLI system you see through telnet. Sometimes it's better to go straight to the CLI.

> 
My main uses of my computer is for gaming (like Crysis etc), working on my web sites (currently running Firefox 3.0b5 and Homesite for authoring), and PaintShopPro XII.

Gaming is an issue. Very few games work well through Wine. I'd say keep a Windows install on your box and reboot to play games. I'd also say make that Windows XP, not Vista (unless you have to have DX10)
For web design Kompozer is probably the best html editor. It's a lot like Dreamweaver, really. The default image manipulation package is GIMP, which you might have used on Windows. Some people hate it's guts. I like it, personally.

> 
And all these flavors of Ubuntu.

The only difference between them is the desktop. Under th hood they're all the same. You can even install all three desktops and switch whenever you feel. So which one you start with doens't really matter.

> 
Are there native Intel chipset drivers? What happens regarding this area?

Intel is extremely well supported. You won't even need drivers. It'll just work.

> 
What about when the time comes when I want to update the BIOS. Am I going to be forced to use a command line version of the updater?

Either use your Windows update tool, or do it the old-fashioned way, I guess.

> 
Is Ubuntu ready for someone like me, who wants to stay away from command line interfaces?

Absolutely. Have a go!

---

### Post by jakupl on 2008-04-26
Don't give up. I bet that even if your problems seem pretty bad for you right now... it won't take so much hassle to fix.
Just tell us what your problems are, and what computer you are running.

---

### Post by 3rdalbum on 2008-04-26
On Asus motherboards, BIOS updates can be done directly from the BIOS (no operating system required).

---

### Post by pbpersson on 2008-04-26
I hate, hate, hate the command line.  Never use it, never want to go near it......I think it is SOOO 20th century  ;)

However, when Ubuntu is totally messed up to the point where in Windows you would just format the hard drive and re-install Windows, the people on this forum have given me some magical command line stuff and it fixes everything.

So.....the command line does have a place in my world but I stay away from it as much as I can.  :)

---

### Post by Ptero-4 on 2008-09-28
My advice. Try and install ubuntu on that box and keep the wintendo only for your games (that's what wintendo is for anyway).

---

### Post by steveneddy on 2008-09-28
Just install it and see how you do.

Might as well just jump right in.

8 million plus users can't be wrong.

---

### Post by Keymaster on 2008-10-09
I was reluctant to start using Ubuntu, because I didn't want to take the time to learn a new operating system, but after a year now, I use the command line more often then not. In fact I have my ubuntu install setup so the GUI doesn't load on startup, and I get a CLI first, and can start it if I want/need it.  My coworkers think I'm crazy for this, but CLI tends to be very powerful.  I also have Ubuntu on my families PC, and even my most computer illiterate family members use it more than the Windows side (yes it is dual boot).  In fact I haven't seen Windows on the screen in months :)  The GUI tends to allow most of the tasks to be done now if you want to avoid CLI.  If you install webmin ([www.webmin.com](www.webmin.com)) you can even use a web interface in firefox for the more advanced CLI only tasks.  It helped me a lot when I was first starting out.  Now I manage almost 2000 linux systems, and I rarely have to touch them.  Good luck, and happy M$ free computing ;)

---

### Post by jerome1232 on 2008-10-09
> **Ptero-4 said:**
> My advice. Try and install ubuntu on that box and keep the wintendo only for your games (that's what wintendo is for anyway).

wintendo, jerome1232 chuckles to himself


I just find it funny because that's all I use Windows for, is games.

---

### Post by Therion on 2008-10-09
I'm going to take a slightly different tack here, mainly because I'm not into convincing people to adopt Linux. If you want switch over, great -- welcome aboard! But I'm not going to try and *convince* you it's something you should do... You'll need to come to that conclusion all by yourself.  When and if you do, I'll be happy to lend any assistance I can with your transition.

So, all that being said... My question is why, exactly, do you want to switch from Windows to Linux?  Further, what do you want from Linux or Ubuntu in particular?  And what are you expecting from it?

---

