---
title: "i thought linux ubuntu 16.10 was better than windows 10 ??? lagging unimaginably"
date: 2017-02-05
forum: New to Ubuntu
---

### Post by jcleve72 on 2017-02-05
i purchased a HP Proliant DL380 G7 2X2.93GHz 64GB RAM and installed both ubuntu 16.04 and 16.10. They both have a horrid lagging problem.

I HAVE:

i. downloaded ccsm (CompizConfigManagerSettings) and unchecked the sync to vblank,

 ii. installed the solution ppa:vanvugt/compiz by Daniel van vugt. 

All to no avail. 

The mouse lags and when playing videos on mozilla youtube the sound is out of sync when using logitech usb headset. 

**HOWEVER** I also have an acer laptop and I can run ubuntu 16.10 from a bootable usb with no problems whatsoever (except possibly weaker wifi signal than when running from windows 10.)

Since I used the same ubuntu bootable usb on both the HP and Acer, there is something (hardware/driver) in/on the acer laptop that is different than the hp server that is causing this difference. 

How can I remedy this problem... i.e. remove the lag on the hp server?

---

### Post by &amp;KyT$0P# on 2017-02-05
Ubuntu with Unity desktop is quite graphics intensive.  So let's look at what graphics hardware you're dealing with.

According to [this]("http://h20564.www2.hpe.com/hpsc/doc/public/display?docLocale=en_US&docId=emr_na-c02215285#N10052"), your machine has a integrated AMD graphics card.  AMD graphics can be tricky in recent versions of Ubuntu.

Are you able to run a lighter flavor of Ubuntu, such as Xubuntu or Lubuntu?

---

### Post by QIII on 2017-02-05
That GPU is an actual ATI unit from before ATI was bought by AMD.  That thing is so old the only driver that will run it is the open source Radeon driver.  At best, its performance will be just enough to run a desktop.

---

### Post by jcleve72 on 2017-02-05
halogen 2, QIII

1. Thanks for your prompt response.
2. I apologize for my ignorance.
3. I will attempt to run Xubuntu or Lubuntu, however according to halogen2 that may not solve my problem??
4. What are my options? How can I get my server to behave like my acer? If the answer is impossible or infeasible, then is there a way that I can put a lightweight weight gui on it so that I can develop web applications?

-thanks so much 
john

X5570 -2.93 GHz Quad-Core

---

### Post by QIII on 2017-02-05
I don't have a GUI on my *headless* server and I develop web applications on it from my primary machine.  All of the files and the databases reside on the server.  I use SSH, use MySQL Workbench to remotely administer the databases and use Bluefish to modify the text files.  From my primary machine, I use a web browser pointed at the URL inside my LAN to check my work.

There's not even a monitor, keyboard or mouse attached to the server.  That server of yours has that wimpy GPU because some folks like at least some GUI for Windows servers.  But even then it can be the barest minimum.  You need nothing at all for Linux.

What I'm saying is that if what you have said is your intended purpose, there's really no need to fret about that ancient GPU.  You don't even need it.

---

### Post by jcleve72 on 2017-02-05
QIII,

1. thanks. Originally I tried headless, and tried remote login and a vnc client however the time and graphics rendering was horrible. so I decided to bite  the bullet and get a monitor, but then I ran into this problem.

Later I may ask you more details of how your system is set up for developing web apps. In particular ... " From my primary machine, I use a web browser pointed at the URL inside my LAN to check my work." Now I have to sleep. 

2. In the event that I wanted to get my server to perform like my acer, what would I need to do? New hardware ?? If so what is your recommendation or could you point me in the direction of my next step to accomplish this task?

most appreciative, john

---

### Post by QIII on 2017-02-05
Sleep well.  Others will be around to help if I'm not.

Just to give you something to think about.  Details later if someone does not beat me to it.

I live in Oregon.  My blog site is hosted on a machine in Seattle, Washington.  Although I use a CMS for the blog site to cut down on the amount of maintenance and design I need to do, I do make modifications from time to time.  Using the CP provided by the host is insecure and I won't do it.  Using the GUI tools provided by the CMS software over the web is dangerous and insecure and I don't do that.

But I certainly do not drive 250 miles to Seattle when I want to work on the site.

I can sit at my machine at home and do all that stuff.  Rather than the insecure stuff I use other, more secure, tools to make modifications -- to develop -- from here.  I do not have to be anywhere near the machine.  And I don't need a monitor attached to it.

In a similar fashion, the home server on my network where I do web development has no monitor, keyboard or mouse attached.  It's not near my desk.  I use the same exact secure tools (it's always best to stay in the habit of security even at home) to do development when I'm at home in exactly the same manner.

In neither case am I at all concerned about the graphics performance of the server.  It's zero.  What is important is the graphics performance of my primary computer on my desk, on which I use a web browser to view my work.

I also don't use anything as insecure as VNC or any remote desktop application at all.  I don't need to.  With Linux, you need to free yourself from the notion that you need a GUI on a server.  That's not a common approach in our world.

---

### Post by jcleve72 on 2017-02-05
Awake,but have to go to work in 7 minutes.

1. I am on board with the web development solution you outlined. Thanks 
2. If I wanted to try some rendering like with blender, how do I need to modify my setup? I know that I need to educate myself on specs e.g. gpu's etc I will start immediately. 
What do I need to buy ?

thanks in advance,  john

---

### Post by Geoffrey_Arndt on 2017-02-05
Lots of choices . . . can coordinate with Ubuntu supported _desktops, laptops and servers_.   Exceptional support & trouble ticket system:   [https://system76.com/](https://system76.com/)

---

### Post by Yellow Pasque on 2017-02-05
> How can I get my server to behave like my acer?

Install a graphics card that can do 3D and video decode acceleration.

> If I wanted to try some rendering like with blender, how do I need to modify my setup?

Install a very powerful graphics card that can do 3D.

---

### Post by The Cog on 2017-02-05
It sounds to me as though you want to use your DL380 as a graphics workstation rather than as a server. That being the case, the two things it is missing are a powerful graphics card, and something to muffle the sound of those fans. 
You need to check what size cards the DL380 will accept. Also, I read that DL380s have NO internal power cabling.

---

### Post by mastablasta on 2017-02-06
not just what will accept but also the power supply would need to handle it.

on the other hand for video encoding this machine could work but might need some GPU for reviewing the result maybe some cheap half size nVidia GPU. something like GT 620 would do.

but rendering is a whole different thing.

---

### Post by jcleve72 on 2017-02-11
I installed Centos 7 (server with a gui --gnome). It is functional ...
-----------------------------------------------------------------------------------------------------------------------

It would seem that a good graphics card will cost nearly as much as the machine ( machine cost  $350 + shipping etc ...) 

If I settle for just getting unity desktop (optimal choice) or gnome ... with no lag/sluggishness or racing cursors ... then I will be satisfied for now. Options ...

1. purchase a cheap/used (pci-express) Discrete nvidia, or amd GPU card (gleaned from postings)

2. [COLOR=#000000]  someone resolved a similar problem with AMD Radeon HD 6450 PCIe (The prices are acceptable on ebay ... below mastablasta suggests GT20 ...slightly more expensive) (gleaned from postings)

Is this valid?

Additional information needed to make determination for validity of purported solution(s): 

1.** Specs for  HP Proliant DL380 G7 X5570 64GB**  :   [/COLOR]https://www.hpe.com/h20195/v2/GetPDF.aspx/c04199811.pdf 

2.** Internal Cabling/ Wattage problem**:: [http://www.tech.proact.co.uk/hp/hp_proliant_dl380_g7_server.htm](http://www.tech.proact.co.uk/hp/hp_proliant_dl380_g7_server.htm), [https://community.hpe.com/t5/ProLiant-Servers-ML-DL-SL/DL380G7-and-150W-graphics-card-support/td-p/4734710](https://community.hpe.com/t5/ProLiant-Servers-ML-DL-SL/DL380G7-and-150W-graphics-card-support/td-p/4734710)

---------------------------------------------------------------------------------------------------------------------------------------------

I am in the process of deciphering this internal cabling/wattage problem ... so much to learn.

 thanx,  this community is so inspiring

john

---

### Post by TheFu on 2017-02-12
Sadly, buying a server to be used as a graphics workstation is seldom the best solution. Servers tend to be noisy, hot, waste lots of power and designed for a different purpose.  Servers tend to be about having lots and lots of threads and fast disk/network I/O. Their graphics subsystem tends to be very low-end.

I also do server development like QIII.  To me, the location of the "server" in the world really doesn't matter.  It can be the same machine or in Japan or Germany or South Africa. I use **ssh** for almost everything.  Right now I'm at home and connected to ... 8 other systems - through ssh.  The idea that we need to sit behind the "server" just doesn't exist and hasn't for 30+ years in the Unix world ... unless you must have direct access to the GPU to display stuff.  Then it is an effort to find a GPU that does what you want, fits into a slot the server has and can be powered, as required, by the GPU. In the old days, GPUs got their power from the PCI bus alone. As more powerful GPUs were demanded, more power connections were needed. Some GPUs have power from 3 different connections.

If it were me, I'd return the server ASAP (or sell it to someone else) and build my own **graphics workstation** around the GPU I required for the task. Different GPUs are best for different sorts of needs.  The requirements for a CAD system are different from those for a gaming machine or a Blender box.

However, since I don't know much about graphics workstations (had a CAD workstation a few years ago), I'd have to defer to someone in the business to learn what their best practices were.  Find someone doing what you want to do, who is also running the Linux distro you want to use, and follow their advice on hardware and setup.

Personal note - I touched a Win10 machine 4 days ago for the first time! And survived! ;) It was only for about 3 minutes, so my mind wasn't warped too much.  Hadn't seen win10 before.  Haven't ever touched a Win8/9 machine, so this was a big deal. I felt like Alice or Dorothy doing this. ;)

---

### Post by The Cog on 2017-02-12
If you are not wedded to running Unity (which is known as needing quite a lot of gpu power), perhaps a lighter GUI like Xubuntu (my choice) ior Lubuntu would work for you. I think that Unity needs 3D support which the others don't.
You could try a live CD as a first step in evaluating the other GUIs. Just remember that running from a CD/USB will be slow when "disk" access is needed, although that should be easy to distinguish from graphics sluggishness.

---

### Post by jcleve72 on 2017-02-16
Finally got qemu-kvm and vagrant/virtualbox working on my functional centos 7 gnome shell.

With qemu-kvm : Tried xubuntu (desktop works well) , Kubuntu (works amazingly well even though the desktop is perhaps overly sophisticated) , lubuntu ( very poor ), edubuntu (same as ubuntu ).

So in some sense this is resolved with the choice of kubuntu/xubuntu.

However one last attempt at a full solution.

At the HP forum I was told that. 

[COLOR=#000000][FONT=&quot]"The grahphics in the server uses the mga driver which should work fine with Ubuntu 16.x."

[/FONT][/COLOR][COLOR=#000000][FONT=&quot]1. I have downloaded from [https://launchpad.net/ubuntu/+source/xserver-xorg-video-mga/1:1.6.3-1build1](https://launchpad.net/ubuntu/+source/xserver-xorg-video-mga/1:1.6.3-1build1).  First option under downloads: [https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-video-mga_1.6.3.orig.tar.gz](https://launchpad.net/ubuntu/+archive/primary/+files/xserver-xorg-video-mga_1.6.3.orig.tar.gz)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Please advise on instructions. I have extracted the files, and looked through them ... but I cannot find instructions ...[/FONT][/COLOR]
one last attempt for ubuntu 16.10/centos7 server desktop without purchasing a card 
-john

---

### Post by mastablasta on 2017-02-16
can you not just install the package (sudo apt-get install xserver-xorg-video-mga) ?

otherwise you are after binary packages (.deb files in this case): [SIZE=2]https://launchpad.net/ubuntu/utopic/+package/xserver-xorg-video-mga
[/SIZE]
make sure you donwload the correct one and then use apt, apt-get or software center (or other method) to install them.

---

