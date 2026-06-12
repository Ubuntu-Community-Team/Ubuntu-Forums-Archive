---
title: "The Computer That Time Forgot"
date: 2007-06-21
forum: Other OS Talk
---

### Post by @trophy on 2007-06-21
I have a Packard Bell Legend 300 CD ([here](http://www.tribalsmile.com/pbupgrade/before.html) is a similar pb) which I would like to do something useful with... the holy grail here would be to turn it into an internet + office capable machine.  

Here's the specs:
Proc:     Pentium 1 66MHz
RAM:    16MB
HDD:     450MB

The only two distros that I could find that sort of fit the bill were DSL and DeLi.  DSL wanted too much RAM, and DeLi installs beautifully but has some sort of issues with the network card and therefore konq-e crashes as soon as you try to access the interwebs.

Does anybody know of any other distros which might resurrect this dinosaur?

---

### Post by Titus A Duxass on 2007-06-21
Did you try Puppy (naff name but not a bad distro)?

You could try a server install of Puppy followed by a WM like openbox and some lightweight app's?

You'll be surprised at what you can do and it's a great way to learn a bit of Linux.

---

### Post by Metacarpal on 2007-06-21
According to their [requirements page]("http://www.slackware.com/install/sysreq.php"), Slackware just might run on that.

---

### Post by ThinkBuntu on 2007-06-21
There's always [Damn Small Linux]("http://www.damnsmalllinux.org/").

---

### Post by Titus A Duxass on 2007-06-21
> There's always Damn Small Linux. - He's tried that already dude (DSL = Damn Small Linux)

---

### Post by Rui Pais on 2007-06-21
With 16M Linux is almost uninstallable. And in practical terms not usable. 

Check ebay (or some site/shop with vintage) for a little more RAM. At least 4x that... (sometimes the trash can of neighbors, lol, or dead boxs of friend have nice stuff)

Another suggestion is check [http://www.menuetos.net](http://www.menuetos.net)

And a last idea (Thats my use for old boxs) install a minimal Linux (mini-iso of ubuntu is nice enough) install X and gdm and connect to your actual machine using xdmcp. Voila, a new terminal with the speed of your fast machine (if network is not slow) Nice for kids or several users at home :)

---

### Post by ThinkBuntu on 2007-06-21
> **Titus A Duxass said:**
> - He's tried that already dude (DSL = Damn Small Linux)

Oops. Didn't read the last paragraph. And I was about to recommend DeLi too! Try Puppy, or even GrafPup, which is Puppy with a bent for graphic design and what not.

---

### Post by ThinkBuntu on 2007-06-21
Also, don't forget that you could use older versions of distros from back when they were less hardware-hungry. For example, you may want to try Debian Woody or an earlier version.

---

### Post by timcredible on 2007-06-21
your only hope is pxes.  i'm not sure if it requires more than 16mb though, it might require 32mb.

---

### Post by @trophy on 2007-06-21
> **Rui Pais said:**
> With 16M Linux is almost uninstallable. And in practical terms not usable. 

Check ebay (or some site/shop with vintage) for a little more RAM. At least 4x that... (sometimes the trash can of neighbors, lol, or dead boxs of friend have nice stuff)

Another suggestion is check [http://www.menuetos.net](http://www.menuetos.net)

And a last idea (Thats my use for old boxs) install a minimal Linux (mini-iso of ubuntu is nice enough) install X and gdm and connect to your actual machine using xdmcp. Voila, a new terminal with the speed of your fast machine (if network is not slow) Nice for kids or several users at home :)



Almost, but not quite.  DeLi works just fine until you try to connect to the internet, then it crashes konqueror due to a hardware conflict that I can't resolve.  It includes IceWM, abiWord as an editor, a few games, etc... all of which run at pretty decent speed considering the box they're running on.  Not bad for 16MB of RAM!

Although searching for a distro has made me wonder why linux has become such bloatware lately.  You'd think there'd be some set of anal-retentive developers out there still coding as if every bit mattered...

---

### Post by Rui Pais on 2007-06-21
> **@trophy said:**
> Almost, but not quite.  DeLi works just fine until you try to connect to the internet, then it crashes konqueror due to a hardware conflict that I can't resolve.  It includes IceWM, abiWord as an editor, a few games, etc... all of which run at pretty decent speed considering the box they're running on.  Not bad for 16MB of RAM!

Although searching for a distro has made me wonder why linux has become such bloatware lately.  You'd think there'd be some set of anal-retentive developers out there still coding as if every bit mattered...

well, maybe i'm just a speed addicted :lol:
...my lower resources is 100MHz with 64M and its slow as hell (with RH7 the most stable i found to work there, a debian and a beatrix run it faster but video frozen)

If your computer has several users you can try connect you old box to the new one by network (cross cable or with a hub) and add to the /etc/X11/gdm/gdm.conf of DeLi:
```
1=Terminal -query xxx.xxx.xxx.xxx
```
under "[servers]" section where xxx...xxx would be the ip of the box you work normally.

---

### Post by tgalati4 on 2007-06-21
You can run DSL with the low-RAM option, but you won't get an Xserver with 16 MB.  I believe 24 MB is the minimum for a (slow) Xserver.  If you want to create a headless disk server, then you might get DSL to work in terminal mode.  I use DSL with 96 MB on a P1, 166 MHz machine and it's been up for 35 days and it currently handles one 250 GB drive.  I can add 3 more in the future.  I log in using ssh and I can even run VNC when I want to see what is going on using the DSL desktop.

Old memory modules are either cheap or expensive (depending on what type of memory it is).  Perhaps you can add some RAM and that would make DSL a viable option.  32 MB is usable, 64 MB is good, 128 MB and DSL will run completely in RAM (although it runs for me in 96 MB as well in RAM).

Good luck.  

Post your results when find a distro that works.

---

### Post by zero-9376 on 2007-06-21
i used vector linux on a 75MHz with orignally 32 mb ram, its based on slackware and was a pretty good intro to linux back then as it didnt have gui config for much, i switched to debian after learning to use the terminal only and now ubuntu (to 75Mhz PC is long since dead unfortunately)
so i havent looked at vector in some time but it was good when i used it.

---

### Post by ThinkBuntu on 2007-06-21
You may find this useful: [Meeting Minimum Hardware Requirements (Debian)]("http://www.us.debian.org/releases/stable/i386/ch03s04.html.en")

---

### Post by zach12 on 2007-06-21
Puppy linux barebones may do

---

### Post by smoker on 2007-06-21
> **@trophy said:**
> 
Does anybody know of any other distros which might resurrect this dinosaur?

you may find something here: [http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/)

best of luck

---

### Post by @trophy on 2007-06-21
> **tgalati4 said:**
> You can run DSL with the low-RAM option, but you won't get an Xserver with 16 MB.  I believe 24 MB is the minimum for a (slow) Xserver. 


Again... already been done.  DeLi uses tinyX to give you a really decent X server, and with IceWM running over it, everything is beautiful except for that damnable hardware conflict... 

:: shakes his fist at the Packard Bell gods and their proprietary hardware ::

To everybody in the thread though... thanks for the ideas... I might try puppy, but I think what I'm going to find is that I just need to switch out that nic for something that doesn't use the tulip drivers.  Even at that it's a longshot, because this PB has a peculiar setup: there's one ISA slot on the actual motherboard, and there's a daughterboard that plugs into that which has three ISA and two PCI slots on it, which my PCI generic nic and ISA sound-card/modem/game port monstrosity plug into.  The general consensus from IRC seems to be that I'm getting screwed by proprietary hardware and I am either going to have to manually reserve all resources used by the nic or (less likely to help) I can just switch the nic out to something that doesn't use the tulip drivers.  I'll let you all know what happens...

---

### Post by iamhugeinjapan on 2007-06-22
I appreciate that this is probably more of a "see if i can do it" hobby for you. But, for the price and effort of getting an alternative NIC/more RAM, you could just get a better old PC for really cheap or free. :)

---

