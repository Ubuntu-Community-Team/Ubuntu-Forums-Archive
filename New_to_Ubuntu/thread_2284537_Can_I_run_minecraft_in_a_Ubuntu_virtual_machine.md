---
title: "Can I run minecraft in a Ubuntu virtual machine?"
date: 2015-06-30
forum: New to Ubuntu
---

### Post by dellboy56 on 2015-06-30
Hi I'm testing out Ubuntu on virtualbox
my Host os is windows 8.1 the guest so is Ubuntu [latest version]
i was wondering will minecraft be able to run in Ubuntu on my HP laptop that I'm using cause when I start it takes a few miniutes to load when I click play its slow as to load I'm installed java etc but I can't play and I'm done tweaks to my stuff like installing things that make my guest os on it slow or something i changed from Ubuntu desktop to a low one thst doesn't use so much memory cause when I fresh installed Ubuntu it lagged so much so I was wondering would you guys help me out if minecraft can run on my guest os by the way my processor is a intel core i3 ill tell you some more details when you guys reply back to me I'll give you the specs etc thanks :)

---

### Post by mastablasta on 2015-06-30
why not run Minecraft on Windows? virtualisation needs power from the CPU and plenty of RAM. running games inside such OS will need even more power.

if you are asking if Minecraft can run well in Linux - yes it can.

---

### Post by dellboy56 on 2015-06-30
I'm testing these things out cause I was thinking of running minecraft from Ubuntu on it but the problem is that it lags etc i need to fix that to play it after that I want to install a server also on it my host is a 64bit but I installed the 32 bit Ubuntu but stil I wanna play mc without no lag in Ubuntu itself

---

### Post by Bucky Ball on 2015-06-30
Welcome. Virtual machines are not ideal for games. The main question is: how much RAM have you got and how much have you allocated to the virtual machine? If you've given it 512Mb of RAM, you don't have a hope. :)

PS: I have changed the title of the thread to match the support request you're actually making. When posting please be specific. If you are not using Ubuntu, but another flavour, please find out and let us know. These things are important. When posting, give all the information you can straight up for faster response and support. Thanks and good luck.

---

### Post by dellboy56 on 2015-06-30
Ok so my base computer  has 4gig of ram installed on it the minimal virtualbox says 512 for Linux Ubuntu and 8gb for hard drive but as you know I'm testing this out so if I was to put more ram instead of 512 it would work right?

---

### Post by mastablasta on 2015-06-30
> **dellboy56 said:**
> Ok so my base computer  has 4gig of ram installed on it the minimal virtualbox says 512 for Linux Ubuntu and 8gb for hard drive but as you know I'm testing this out so if I was to put more ram instead of 512 it would work right?

try pumping 2 GB in vbox ram.

disk is low but should be ok as login as you don't install too many things.

to run server you probably do not need a desktop which will significantly reduce the CPU usage, RAM usage as well as GPU usage. for example by default Ubuntu 32 bit should use about 400 MB of RAm when idle and after boot. Ubutnu server will use about 80 MB if I remember correctly. installing from minimal (barebones) iso it will use even less. 

default Ubuntu Unity uses hardware graphics acceleration to draw windows. which is why a well supported GPU card is a must to use the  desktop well. While you are using virtual GPU which only you know how much ram you added to it. default is 12 MB. see what kind of win8 experience you would get at 12 MB GPU from the 1995 :-) I doubt it would run well. LXDE and XFCE do not use hardware acceleration so they do not look as pretty. same goes for mate and various widnows managers. ToriOS uses jwm and ends up with about 60 MB ram usage on boot and can run on VESA card probably..

still - Minecraft runs fluently on Linux (if you install Linux on disk). it is used on raspberry pi to teach kids.
it runs on java so it doesn't matter which OS you use. in fact you can just move the windows version to Linux change the ending in .exe file to .jar if I remember correctly and it will just work.

---

### Post by ajgreeny on 2015-06-30
> **dellboy56 said:**
> Ok so my base computer  has 4gig of ram installed on it the minimal virtualbox says 512 for Linux Ubuntu and 8gb for hard drive but as you know I'm testing this out so if I was to put more ram instead of 512 it would work right?
I'm a bit surprised that you can get Ubuntu (with unity DE?) running very well with only 512 MB ram for the VM; I have a VM of Ubuntu running very well with 4GB out of my 8GB ram on a Xubuntu 14.04 host.  What memory did you set for the graphics of the VM? The maximum is only 128MB which for most games is woefully lacking.

Go to the virtual machine settings in VBox when the guest is powered-off and change the alocated ram to 2GB and if necessary raise the video memory all the way to 128MB; you may find that makes a lot of difference, though for games, I'm afraid it may still be inadequate.

---

### Post by dellboy56 on 2015-06-30
Ok I'll give it a shot Mastablastar by the way when u said two gig of ram does that mean I completely have to reinstall again from virtualbox or can I like do something else ?

---

### Post by Bucky Ball on 2015-06-30
> **dellboy56 said:**
> ... does that mean I completely have to reinstall again from virtualbox or can I like do something else ?

No. ajgreeny gave clear instructions on how to do this. Switch off/shutdown the Ubuntu VM, change the RAM setting in VBox to 2Gb for that machine, change the graphics memory amount, launch the VM.

As I mentioned earlier and ajgreeny has reiterated, doubt you'll get far with this. Gaming in a virtual machine is not ideal. Better to just use Windows if it is a Win game or perhaps even Wine, but I know nothing about Wine.

---

### Post by dellboy56 on 2015-06-30
I'll private message you tomorrow as I'm gonna do some more work on it tomorrow aswell so I can give you info about the vm cause i find Ubuntu so easier lol it looks a bit like mac except linux is free etc

---

### Post by dellboy56 on 2015-06-30
I'm heard wine is good cause you can like run games that Linux can't support from windows I'll give that a crack aswell

---

### Post by Bucky Ball on 2015-06-30
Please keep it on the forum. PM support is highly discouraged and staff and the majority of users don't give it (and some members will report requests for PM support). Share with the community for the community's benefit and input please. 

You have had changing the settings explained to you twice on this thread. Follow the instructions and tell us how you go. Thanks.

---

### Post by mastablasta on 2015-06-30
> **dellboy56 said:**
> I'm heard wine is good cause you can like run games that Linux can't support from windows I'll give that a crack aswell

wine is another kind of virtualisation, but not really. it adds a layer that basically tricks the windows program into thinking they are running on windows. it is not perfect and only a few games run really well on it. mostly older ones. anything below rating Gold on their appdb website is not worth the trouble.: [https://appdb.winehq.org/](https://appdb.winehq.org/)

---

### Post by Bucky Ball on 2015-06-30
There is a forum section devoted to Wine issues. Post a new thread there if you have any. Personally, better to install Windows in a dual-boot IMHO. A few things work great in Wine, some average, many not at all.

---

