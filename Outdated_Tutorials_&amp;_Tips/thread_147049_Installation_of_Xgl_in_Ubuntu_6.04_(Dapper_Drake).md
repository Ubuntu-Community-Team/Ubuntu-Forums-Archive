---
title: "Installation of Xgl in Ubuntu 6.04 (Dapper Drake)"
date: 2006-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by moma on 2006-03-19
[COLOR="Red"]This message and this guide is deprecated and old !
Look for other guides on the [Ubuntuforums.org]("http://www.ubuntuforums.org/showthread.php?t=148351") and [http://www.compiz.net/viewtopic.php?id=911]("http://www.compiz.net/viewtopic.php?id=911") [/COLOR]


------------------------------------------------------------
Hello all newbies,

[COLOR="Olive"]Automatic script that installs Xgl /Compiz in Ubuntu 6.04 TEST: [/COLOR]

I made a tiny script that automatically installs Xgl / Compiz with 3D-effects on your Ubuntu 6.04 PC.

Picture_1: [http://bildr.no/view/869.jpeg]("http://bildr.no/view/869")

Picture_2: [http://bildr.no/view/923.jpeg]("http://bildr.no/view/923")

Picture_3: [[img]http://bildr.no/thumb/1173.jpeg[/img]](http://bildr.no/view/1173) 

[COLOR="SeaGreen"]Other amazing [pictures...](http://www.lynucs.org/index.php?p=search&search_string=xgl&search_categ=screen)[/COLOR]


[COLOR="Red"]The absolute requirements are:[/COLOR]

[COLOR="Red"]1) [/COLOR] You must run Ubuntu 6.04 / 6.06 Dapper Drake (32 bits, development version). 
You can get Dapper from [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) or 
take the latest beta release: [http://www.ubuntu.com/testing/dapperbeta](http://www.ubuntu.com/testing/dapperbeta)

[COLOR="Red"]2) [/COLOR] Your machine has ATI or NVIDIAs graphic card.

[COLOR="Red"]3) [/COLOR] You run GNOME desktop.  The script will not work on Kubuntu/KDE !
-----------------------------------------------

[COLOR="Teal"]Using the script[/COLOR]
Prepare your finest test machine and 

[COLOR="Teal"]A)[/COLOR] Get the latest "inst_xgl.sh" script:
$ rm inst_xgl.sh 
$ wget [http://www.futuredesktop.org/dapper/inst_xgl.sh](http://www.futuredesktop.org/dapper/inst_xgl.sh) 

[COLOR="Teal"]B)[/COLOR] Run it like this:
$ sudo sh inst_xgl.sh 

[COLOR="Teal"]C)[/COLOR] It may ask you to reboot after it has upgraded the Linux-kernel.   Just reboot and re-run the script (step B).

[COLOR="Teal"]D)[/COLOR] Let the script terminate and read the final messages 1),  2) and 3).
Reboot again & dive into a your 3D-box.   Xgl /Compiz is quite an amazing thing.

[COLOR="Teal"]E)[/COLOR][COLOR="Red"] EDIT: About skydome plugins.[/COLOR] 
Because Ubuntuforums.org does not allow anonymous downloads (anymore?), you must download packages for Skydome-effects manually. Please read [this message...]("http://ubuntuforums.org/showthread.php?t=139265")

It requires you to download [this package...]("http://ubuntuforums.org/attachment.php?attachmentid=7191&d=1142630313") (login required).

Install all *.deb  packages BUT NOT the *kde* package. Remove the *kde* package before you 
$ sudo dpkg -i *.deb

BUT NOTE: [COLOR="DarkOrange"]You may safely drop & forget step E). Skydome plugin is NOT so important ![/COLOR]

[COLOR="Teal"]F)[/COLOR] Learn to use it.
Read the manual: [http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz) 

Learn to reconfigure your Compiz settings by using the 
$ gconf-editor
Browse to: Apps ->  Compiz -> ...

All Compiz-options are available in the menu selection !
Applications -> Accessories -> Gset-Compiz  

[COLOR="Red"]Muy importante massage:[/COLOR]
I cannot quarantee against any harm or damage caused by the code!  All I know it works here... .  Study the code if you wanna know more. 

I've testet the script with [COLOR="RoyalBlue"]ATI Radeon 9800[/COLOR] and [COLOR="RoyalBlue"]nVidia GeForce 6800 LE[/COLOR] graphic cards on 32-bits Ubuntu 6.04, AMD 3400+. The script will certainly not fix Xgl on all types of hw.
;) 

Sincerely
  Moma
  [http://www.futuredesktop.org/how2burn.html#Ubuntu](http://www.futuredesktop.org/how2burn.html#Ubuntu)
------------------------------------------------------------------------------------------
[I]
[COLOR="Green"]EDIT: My favourite keys are:

F12   (Press F12 and get an overview of your windows. Nice & smoooth)

CNTR + ALT + move and drag the mouse cursor along the desktop. Keep the left mouse-button down. 
or even better:
CNTR + ALT + move and drag the mouse cusror on the workspace-switcher or on the toolbar / menubar.  Keep the left mouse-button down.

CNTR + ALT + LEFT_ARROW  |  RIGHT_ARROW  (a very usefull and quick way to switch a workspace.  Just love it !)

CNTR + ALT + ARROW_DOWN  (show workspace list)

ALT + LEFT_MOUSE_CLICK on a window.  Drag the mouse.  (it will move the window)

ALT + RIGHT_MOUSE_CLICK on a window.  Drag the mouse.  (it will resize the window. Easier than painfully focusing at the edges)

ALT + MIDDLE_MOUSE_BUTTON  on a window.  (changes transparency of active window)
[/COLOR]
------------------------------------------------------------------------------------------

[COLOR="Purple"]Study these articles and video clips to get known with Xgl.
[http://www.novell.com/linux/xglrelease/](http://www.novell.com/linux/xglrelease/)
+
[http://www.atomicmpc.com.au/article.asp?SCID=22&CIID=35615](http://www.atomicmpc.com.au/article.asp?SCID=22&CIID=35615)
+
[http://www.freedesktop.org/~davidr/xgl-demo1.xvid.avi](http://www.freedesktop.org/~davidr/xgl-demo1.xvid.avi) [/I]
[/COLOR]
------------------------------------------------------------------------------------------
**!  !  !  ! **
[COLOR="Red"]Read this if you want more eye-candy effects using "xwinwrap" :[/COLOR]
[http://ubuntuforums.org/showthread.php?t=146533&highlight=xgl]("http://ubuntuforums.org/showthread.php?t=146533&highlight=xgl")

Try these screensavers:
$  ls -l  /usr/lib/xscreensaver/

The fish & whales screensaver is called "atlantis". I've seen it in Ubuntu 5.10 but it's not present in Dapper (AFAIK).

Guide: [http://forums.gentoo.org/viewtopic-t-444350.html](http://forums.gentoo.org/viewtopic-t-444350.html)

Compiz forum: [http://compiz.net/]("http://compiz.net/")

---

### Post by wbeck85 on 2006-03-23
You are truely a god among men. This script worked beautifully for me. Now, it did happen to completely reconfigure my computer, backdrop changed, new programs were installed, and old programs were removed, codecs switched around. It will take me a little  while to actually figure out what changed: all that apt-get business that was flying by in my terminal was not quite readable at such speeds....

But neverthe less, Xgl is literally just a ```
sudo sh inst_xgl.sh
``` away. Absolutely amazing. Abosolutely amazing.

And, oh, one other thing: someone should probably move this thread over to the dapper dev forum where it can get some views and further comments


Kudos! I love you.

---

### Post by prof_booty on 2006-03-23
Worked great for me too.  Had to install the restricted modules for my k7 kernel to start X, but after that everything is peachy.

However, when I apt-get update/apt-get upgrade with the new /etc/apt/sources.list, ubuntu gives me a new kernel and when I reboot I'm without all the hot graphics.  

Is the sources.list that is installed by this script going to get me all the security updates?  There's been a few over the past few days I've been holding off on, but don't want to bogart my phat new desktop.

Thanks for the great work.

---

### Post by RaptorRaider on 2006-03-23
Awesome.

Would you mind if I use this script (read: copy a large portion of the code) for a project of my own?
I'm thinking of making a Dapper CD which uses Xgl and Compiz by default.

Why is it also installing programs like Beagle, and much more?
I'd say this is more than just an Xgl script.

---

### Post by dg_w on 2006-03-24
I was so looking forward to this..
I downloaded the cd ..
Did a fresh install. changed or added nothing..
Ran the script, which seemed to give no errors,
Re booted and wWhen GDM starts it fails, the message is  GLX no loaded no compatable nvidia driver found ? 
I am running nvidia 5200 
Am I meant to have the lasted nvidia drivers installed first ?

I have tried to re-run the script etc but keep getting back to the same thing.. Startx will start gnome up ok but no compiz etc
Running compiz in a terminal gives    compiz.real: No composite extension

Any ideas please ,  the xorg driver in the nv one ?
What can I try to get this going I have been trying to get Xgl \ compiz all week :) 
Odd but gconf - apps does not have compiz in
it 

](*,) Thanks

---

### Post by ueluei on 2006-03-24
Hi, I some strange problems when I upgraded from Breezy to Dapper with the nVidia modules. I do not know if it has something to do with your problem. I posted in my blog the manual steps that I did to install Xgl+compiz:
[http://ueluei.blogspot.com/2006/03/xgl-on-ubuntu-for-nvidia-users.html]("http://ueluei.blogspot.com/2006/03/xgl-on-ubuntu-for-nvidia-users.html")
I hope it helps.

---

### Post by dg_w on 2006-03-24
Hi Thx for the reply ... Tried but no good
I am just starting again ... A fresh install of Dapper ... I will then apt-get udate and upgrade. Then try running that script again (this time not from with X ?)
Should I be using the nvidia or nv driver with xorg to get the Glx and compiz ?

I will let you know in 30 mins or so :) 

Thx

---

### Post by dg_w on 2006-03-24
No joy :(

Fresh install of dapper
Apt-get update upgrade dist-upgrade
This time I uncomment the Univese repos
All went all..
rebooted all ok

Ran the script, all seems to go ok..
Half way through reboot after the new kernel etc is installed
Run script again, finished, please reboot..

Same error, gdm will not start, error GLX cannot load no compatable nvidia driver found... So run startx gnome will then run fine (not glx etc)

Anyone else have the same issue, what steps did you take to instal the script ?

Thx ](*,)

---

### Post by moma on 2006-03-25
[QUOTE=RaptorRaider]Awesome.
Would you mind if I use this script (read: copy a large portion of the code) for a project of my own?  I'm thinking of making a Dapper CD which uses Xgl and Compiz by default.[/QUOTE]
Sorry for my delayed answer.
Of course, you can copy and modify / improve any part of the code. The script and all related files are completly free & open.  Study also the references (URLs) mensioned in the header section. [COLOR="Red"]You'll find all involved files [here...](http://home.online.no/~osmoma/dapper/)[/COLOR]  
Good luck.
[QUOTE=RaptorRaider]
Why is it also installing programs like Beagle, and much more?
I'd say this is more than just an Xgl script.[/QUOTE]
I had to install Xgl, Beagle, Firestarter, Gnomebaker and some other programs on several (=3) machines,  so I just retrieve those modules in inst_xgl.sh.  Maybe a useful move for a newbie, but not for all users.

[COLOR="RoyalBlue"]To user dg_w: [/COLOR]
Sorry that you didn't make it work.  Maybe best to wait till the final release of Ubuntu Dapper v6.06 (year=2006, month=june).   
BTW: Did you load "nvidia" driver in xorg.conf?
Check the URLs and guides mensioned in the header section of the script.

---

### Post by dg_w on 2006-03-25
Hi 
I just ran the script on another computer running an ATI card and it worked a dream,
The install on the nvidia machine did not run through the x config either ?

So I am doing to try it again monday ... To make sure nvidia not nv is being loaded ;P

Many thanks   .. I will let you know how it goes

---

### Post by z_diver on 2006-03-25
Wow, I used this script to fix a broken Xgl desktop that resulted from my unenlightened self attempt.  :D 

ATI All-in-Wonder 9600
Sony SDM-HX73 monitor
Dell SC400

---

### Post by dg_w on 2006-03-26
Can we set this sticky in howtos or something 
Very good for people wanting to try Xgl

---

### Post by Tommerz on 2006-03-26
I just ran this script and now x won't load... any tips for undoing the script? :confused:

---

### Post by dg_w on 2006-03-27
All the files that are changed are backed up in their respective directory..
Just rename back..
What video card do you have...
Is it GDM that will not start... If you login at the command prompt and type
startx does gnome work ?

---

### Post by moma on 2006-03-27
[QUOTE=dg_w]Hi 
I just ran the script on another computer running an ATI card and it worked a dream.  The install on the nvidia machine did not run through the x config either ?
So I am doing to try it again monday ... To make sure nvidia not nv is being loaded ;P[/QUOTE]

Hello dg_w,
I would like to have a colleague like you dg_w.  You never give up even there are errors in the script. Thanks a lot dg_w.  

The script was too eager to do "apt-get remove ... " so it also removed drivers for nvidia from the "/lib/modules" directory.   You can check wheather the "nvidia" driver is there:

$ find /lib/modules -name "*nvidia*"

/lib/modules/2.6.15-19-k7/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.15-19-k7/kernel/drivers/video/nvidia
/lib/modules/2.6.15-19-k7/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.15-19-k7/volatile/nvidia_legacy.ko
/lib/modules/2.6.15-19-k7/volatile/nvidia.ko       <--- THE DRIVER 
----------------

I have now fixed the script by commenting out some "apt-get remove...." statements.

Get a new version of the script and run it.

[COLOR="SeaGreen"]Love & a giant bear hug to all especially to dg_w.[/COLOR]

All the best,
  moma
--------------------------------------------------------------------------------------
[COLOR="DimGray"]PS. If you need to test some system related issues like modification of xorg.conf,  you can easily re-test and "re-start" your computer like this:

A) Invoke a TEXT-console by pressing CNTR + ALT + F1      (or any other F1...F6)

B) Goto run-level 1
$ sudo init 1
Run level 1 is a singe-user and maintenance mode. (study [run levels...]("http://en.wikipedia.org/wiki/Run_level"))
It will stop the Xserver,  remove all unnecessary processes and clean up the system.  However it will not unload modules or drivers  (modprobe -r).

C) Return to run-level 2.
# init 2
Run level 2 is a normal multiuser mode with network and graphical GUI.
(in Fedora/RedHat and Mandrake Linux you propably must say:  "init 3" or "init 5" )

This init 1 -> init 2 method is much better than rebooting a machine. Reboot takes time and it' too stressful for harddrives. But sometimes you cannot avoid rebooting,  e.g new kernel requires that.

This command reveals current runlevel
$ runlevel 
------------------------------------------------------

Of course, you can always restart the xserver (more leniently) by doing 
$ sudo /etc/init.d/gdm restart  (if GNOME)
or  
$ sudo /etc/init.d/kdm restart  (if KDE,  I assume)  [/COLOR]

[ lenient = not to be harsh]

---

### Post by Tommerz on 2006-03-27
[QUOTE=dg_w]All the files that are changed are backed up in their respective directory..
Just rename back..
What video card do you have...
Is it GDM that will not start... If you login at the command prompt and type
startx does gnome work ?[/QUOTE]

It's GDM that won't start, and if I run startx Gnome does not work either.

I have several backed up xorg.conf files in the directory, but they all contain Load "glx@".

I get the feeling it may be down to the installation of the ATI driver, as I wasn't using this before. I'm happy to post the contents of my xorg.conf file.

Any ideas?

[B]*Edit* Update
[/B]

I just managed to fix it myself. 

For those with a similar problem looking for a solution, I booted from cd into Damn Small Linux (Knoppix or Ubuntu live will work just as well) and then ran the following commands:

[QUOTE=dg_w]sudo mount /dev/hda2 /mnt/hda2
sudo chroot /mnt/hda2
sudo dpkg-reconfigure xserver-xorg[/QUOTE]

And then followed on screen instructions, auto detecting hardware, and ta-da I am now typing this from my Gnome desktop in Ubuntu. 

I think I'll leave glx till it's a bit easier + less risky to use.

---

### Post by dg_w on 2006-03-27
Re.Get a new version of the script and run it.

Great news ... I will give it a try tomorrow .. Just download it like before (at begining of post) and that will be a latest copy ?

Thx Moma

---

### Post by foundation on 2006-03-27
this script works on 6.06 too, though i had to comment out the distro_check part of it.

thankyou, i finally have xgl/compiz.

---

### Post by dg_w on 2006-03-28
Yep Moma thats fixed it ..
I tried a clean install today
Dapper 6.06 as it is now
After remming out the distro check section it all works as it should
Great job :-D 

How if at all is apt-get updates etc effected, guess we could just run the script again it there were issues

Thx

---

### Post by dg_w on 2006-03-28
Incidently..
If you are having issues running apps once you shitch over to the glx server

I got this from the main forums

sudo ln -s /etc/X11/rgb.txt /usr/lib/X11/rgb.txt
sudo ln -s /etc/X11/rgb.txt /usr/X11R6/lib/rgb.txt
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/rgb.txt

Restart

Should be all fine now :)

---

### Post by Owdy on 2006-04-01
That script also install bunch of wallpapers to home dir, Beagle desktop search and Firetstarter GUI. Beagle is full of bugs in Dapper. Why your script installs those no needed extras?? And why you dont say it does that in your post?

[https://launchpad.net/distros/ubuntu/+source/beagle/+bug/33341]("https://launchpad.net/distros/ubuntu/+source/beagle/+bug/33341")

---

### Post by RaptorRaider on 2006-04-01
Is it neccessary for ATI users to reconfigure xorg.conf manually?
Could you explain why?

Why install "transset" from the repositories when there is a plugin "transset" for Compiz?
Or is that exactly the same thing?

I must say again, that I find this script amazing.

---

### Post by philipacamaniac on 2006-04-01
OMG! ARE YOU KIDDING ME?

I went from zero to Linux-God-Machine in about 15 minutes. Hardware is ATI Radeon 9700 Pro, Via chipset, Athlon 1600+

And it works great! If this is the hardwork from Novell, I need to pay them money or something.

---

### Post by jmoney on 2006-04-02
Holly Cow! This script is amazing! I've tried installing everything myself and never completely succeded, but this script finally made it happen for me. 

Thans, dg_w!
dg_w for president!!!

ps: I have ati radeon 9800pro, athlon xp 2500+, 512mb.

---

### Post by kwaanens on 2006-04-03
I tried this script. 1. time I didn't succeed, and saw no difference after a reboot. So I just ran the script again. 
Now, it works, but there's a problem that made me have to remove the configuration:
After login, I can see the effects but the whole system freezes on at least 2 occasions: 
1. When I try with a window (file manager) to check out the effects, after a while the system freezes when I click the minimized file manager on the window list.
2. It crashes when I click the buttons to the right of the "Programs - Places - System" menus.

Oh well, at least I saw the effects on the screen for a little while.

Computer:
Inspiron 9300 with ATI x300 graph. card.

- Ketil

---

### Post by mgsfan on 2006-04-03
just ran it 5 minutes ago..reconfigured and rebooted...works great so far and this is with an ati x700

---

### Post by Owdy on 2006-04-03
[quote=kwaanens]I tried this script. 1. time I didn't succeed, and saw no difference after a reboot. So I just ran the script again. 
Now, it works, but there's a problem that made me have to remove the configuration:
After login, I can see the effects but the whole system freezes on at least 2 occasions: 
1. When I try with a window (file manager) to check out the effects, after a while the system freezes when I click the minimized file manager on the window list.
2. It crashes when I click the buttons to the right of the "Programs - Places - System" menus.

Oh well, at least I saw the effects on the screen for a little while.

Computer:
Inspiron 9300 with ATI x300 graph. card.

- Ketil[/quote] This script installs Beagle desktop search also (who knows why). Its buggy on Dapper and it could be freezing your system. Try unistall that.

[https://launchpad.net/distros/ubuntu/+source/beagle/+bug/33341]("https://launchpad.net/distros/ubuntu/+source/beagle/+bug/33341")


I also recommed latest cvs version, its more stable [http://ubuntuforums.org/showthread.php?t=148860](http://ubuntuforums.org/showthread.php?t=148860)

---

### Post by Al3xanR0 on 2006-04-04
Simply ingenious!

---

### Post by Toxicity999 on 2006-04-04
I didn't have the energy to read all these freakign endless pages... BUT you do of course realize this is the 5.10 preezy forum right? lol... hehe anyway thanks for this... I'll test it out on my Laptop when I get home, cookie coated in mustard for you!

---

### Post by kwaanens on 2006-04-04
[QUOTE=Owdy]This script installs Beagle desktop search also (who knows why). Its buggy on Dapper and it could be freezing your system. Try unistall that.[/QUOTE]

Beagle was already installed and running, so that's not the problem.

- Ketil

---

### Post by mgsfan on 2006-04-04
hmm one thing i noticed is I'm missing my shutdown/restart button/icons in the log off menu...actually missing alot lol..wondered how I could get them back..

---

### Post by Jefim on 2006-04-06
Hmmm... strange... Xgl loads, but compiz does not... And if I do a "compiz --replace blablabla_modules" my laptop becomes unusable (title bars go away and my keyboar starts functioning funny. I have an Acer 5021 laptop with Turion64 and ATI Radeon X700... Any suggestions why this script doen't work??..
By the way I'm using Dapper

---

### Post by aden on 2006-04-06
Everything was fine but on Gnome.. KDE runs soooo slooow, i just can't work on it. Someone know how to fix it?

---

### Post by cabber on 2006-04-07
I ran this on a new install with Dapper 6.06 and Nvida 6600 card and it worked:D A few questions:

How does one go about turning this on and off?

Are there plug ins or additional features?

Is there a way to update to the latest version?

---

### Post by lazyd2 on 2006-04-07
Thanks a million...it works perfect with my x600 ati. 

One question, why don't I have a "Shut Down" option and only "Log Out"?

---

### Post by krusbjorn on 2006-04-07
[QUOTE=cabber]Are there plug ins or additional features?

Is there a way to update to the latest version?[/QUOTE]

[http://wiki.ubuntu.com/compiz](http://wiki.ubuntu.com/compiz)

---

### Post by TrinitronX on 2006-04-07
[QUOTE=mgsfan]hmm one thing i noticed is I'm missing my shutdown/restart button/icons in the log off menu...actually missing alot lol..wondered how I could get them back..[/QUOTE]

Yeah... I really need these buttons too.... why are they removed?
Also, why did gdm's theme change?
the image doesn't work for my widescreen display running with resolution 1440x900... the edges are extended with repeating pixels rather than simply resizing the image... it looks like someone smeared the edges to the end of my display :P.

---

### Post by marwal on 2006-04-08
After running the script all works and except ALT-GR together with 9 and 0 which should give me closing straight and curly brackets but just gives 9 and 0 now. How do I fix this?

---

### Post by vms3120 on 2006-04-09
Great Script!!
workd like a charm.

One question though, when i login, and the splash screen is beig displayed, there is an image being shown behind it. How do i change that image. (the image being shown is in /usr/share/compiz/background.png)

I have tried searching for the file where it tells what image to display behind the splash, but have had no luck.

Any help would be great.

Thanks,

-V

---

### Post by Koniaku on 2006-04-09
i have a problem with my 9200 rv280 card 
x cannot see my card 
and even if i configure it manualy it won't work 
after i reboot it says that there are problem with x ...

---

### Post by z_diver on 2006-04-09
[QUOTE=mgsfan]hmm one thing i noticed is I'm missing my shutdown/restart button/icons in the log off menu...actually missing alot lol..wondered how I could get them back..[/QUOTE]

I'm having this issue to on my ATI (RV350) card but not on my Nvidia 5200 go.  Are the other people that are having this issue using ATI or Nvidia?  Also, are there people using ATI that are not experiencing this *minimized* logout screen. :rolleyes:

---

### Post by JoeMetal on 2006-04-10
Apparently the part that says "Try this guide first if you have a NVIDIA graphics card" was pretty important.  After about 2 hours of try to figure out why my display was all screwy I stumbled upon that.  And then after a quick edit to xorg.conf and a reboot, I finally got xgl up and running.  And let me just say that this is by far the coolest looking thing I have ever seen.

---

### Post by RaptorRaider on 2006-04-10
If enough people are interested, I'll make an "improved" version of this script.

There are several things which seem rather strange and unnecessary, and I think QuinnStorm's .deb's should be used.
Some things, like the installation of the fglrx driver, are done quite not-Ubuntu style.
Plus, I don't think splash-images should be changed and icons should be allowed to disappear.

---

### Post by binks on 2006-04-10
just amaying cheers pal althou im abit sea sick atm lol i love it

---

### Post by m4sterguru on 2006-04-10
well, i have a hp zd 8000 laptop, i installed ubuntu dapper drake fligth 6.06, with wine, cedega and crossover office, i run the script, have many problems, but i did many recovery boots, configure the xorg, and voilá, this is amazing!!! very nice work!!! but now cedega doesnt have opengl, any ideas?? i want to play!!!!:mrgreen:

---

### Post by tincbtrar on 2006-04-10
[QUOTE=kwaanens]I tried this script. 1. time I didn't succeed, and saw no difference after a reboot. So I just ran the script again. 
Now, it works, but there's a problem that made me have to remove the configuration:
After login, I can see the effects but the whole system freezes on at least 2 occasions: 
1. When I try with a window (file manager) to check out the effects, after a while the system freezes when I click the minimized file manager on the window list.
2. It crashes when I click the buttons to the right of the "Programs - Places - System" menus.

Oh well, at least I saw the effects on the screen for a little while.

Computer:
Inspiron 9300 with ATI x300 graph. card.

- Ketil[/QUOTE]

Hello Guys!

Im also having these problems.  Oddly enough...I also have an X300 ATI card.  Any suggestions?  I would really like to keep this going on my laptop.

Cheers for this script...I work and go to school fulltime and I barely have time to breathe these days.  Im truly appreciative of all of your work.  Its nice to see that the community is still alive and well.

Cheers.
Brian.

---

### Post by KagenoKaze on 2006-04-10
[QUOTE=kwaanens]I tried this script. 1. time I didn't succeed, and saw no difference after a reboot. So I just ran the script again. 
Now, it works, but there's a problem that made me have to remove the configuration:
After login, I can see the effects but the whole system freezes on at least 2 occasions: 
1. When I try with a window (file manager) to check out the effects, after a while the system freezes when I click the minimized file manager on the window list.
2. It crashes when I click the buttons to the right of the "Programs - Places - System" menus.

Oh well, at least I saw the effects on the screen for a little while.

Computer:
Inspiron 9300 with ATI x300 graph. card.

- Ketil[/QUOTE]

for people with the mobile ati's try this
[http://ubuntuforums.org/showthread.php?t=150854&highlight=x700+problem](http://ubuntuforums.org/showthread.php?t=150854&highlight=x700+problem)

A friend needed that in order to stop lockups
hope this helps
Kage

---

### Post by JediPottsy on 2006-04-11
ok i ran the script twice, my splash screen and background changed, but nothing happens. No compiz / xgl. :S

---

### Post by ghostzapper on 2006-04-11
Hi,

first of all thank you for this script, even though it didn't run as expected. 

Here's what happened:
Started the script, several packages were downloaded. Everything worked fine until the restart. Restarted the machine and finished the configuration. Another restart. Now the following happens:

I see the login screen and when i enter my login information i can see the  checkered Background of the X Server shortly, the login sound plays and then my sreen turns black with a mouse pointer on it. It seems to work underneath as the pointer changes, when i press CTRL & ALT & right mousebutton i.e. What could this be? Tried to run the script twice but same effect.

Machine is a Pentium 4 Dual Core 3GHz, 2GB Ram, ATI Radeon 9200 PRO. Dapper is Version 6.06.

Thanks in advance.

Ghostzapper

---

### Post by dragonfyre13 on 2006-04-11
Hey, thought I would let you know that I posted this on my site, so that you can tell me if you don't want it up there. Check it out, as I have cleaned up some of the syntax, and grammar, in addition to just messing with formatting a bit.

[http://www.dragonfyre13.com/TimWiki/InstallingXGLAndCompiz](http://www.dragonfyre13.com/TimWiki/InstallingXGLAndCompiz)

---

### Post by hoarythehedgehog2009 on 2006-04-11
[QUOTE=moma] You run GNOME desktop.  The script will not work on Kubuntu/KDE ![/QUOTE]

It's okay I will live without the wierd cube....:p

---

### Post by JediPottsy on 2006-04-11
How come i have funny key layout.
Both my .Xsession and xorg says .gb , not .no

---

### Post by massivevoid on 2006-04-15
Can't download the script.

EDIT- I checked on my other computer and I have the file (good thing I saved it). If someone else needs it, PM me if you do. :)

EDIT EDIT- Eh, I just tried to install it on another PC and it didn't work. I guess the sites on the script, where it gets the file, probably expired. :(

---

### Post by lazyd2 on 2006-04-16
[QUOTE=massivevoid]Can't download the script.

EDIT- I checked on my other computer and I have the file (good thing I saved it). If someone else needs it, PM me if you do. :)

EDIT EDIT- Eh, I just tried to install it on another PC and it didn't work. I guess the sites on the script, where it gets the file, probably expired. :([/QUOTE]
I checked it and it's running OK...

---

### Post by thunderduck3141 on 2006-04-18
this is the best
i have familyguy running as my background and everything is so gooy
amazing script
thanks a bunch:mrgreen:

---

### Post by cribbon on 2006-04-19
Woa! This just... works! =D> 
Thank you so much! 8)

---

### Post by jscat on 2006-04-22
Thanks, worked like a charm.!.  Ubuntu beta, Nvidia 7900GTX

---

### Post by adam.tropics on 2006-04-24
At last, since last dapper update this works for me, which given the low spec machine I am on is somewhat of a miracle. 

A question though, the gconf settings. Being on ATI I am having to run everything on screen1 as opposed to 0. How can I make the compiz plugin settings apply to screen1?

Ps. thanks for your efforts on this whole thing

Edit: Also, gdn doesn't start, everytime I reboot, x crashes, then if I log in, and do startx. everything is fine...go figure!!

---

### Post by darrellt on 2006-04-24
Hi

This sounds great but will it work with the 64bit Breezy?

Thanks in advance

---

### Post by adam.tropics on 2006-04-24
Why not give dapper a go and then go [here..]("http://www.ubuntuforums.org/showthread.php?t=133427&highlight=xgl+64").

---

### Post by whistl on 2006-04-24
I've read all the posts and replies, including the bit about the fix for the ATI X300 mobile chipset.

I'm using a dual-head configuration at work, horizontal layout (secondary screen is an external LCD to the right of the primary screen).  My primary screen is :0.0, my secondary is :0.1.  Obviously, the inst_xgl.sh wasn't intended to work for this configuration.   Any hints?

Xgl never gets started.  I found the lines that start Xgl are commented out in /etc/gdm/gdm.conf-custom.  Is that how it's supposed to be?  I looked at the inst_xgl.sh script, and it wgets this file exactly as-is.  Where does Xgl get started from?

Thanks in advance...

---

### Post by whistl on 2006-04-24
never mind, just found the posts that say it doesn't work yet...  :(

---

### Post by WijbrandSchaap on 2006-05-01
This script works great. Just made my neighbour, who's a mac-addict, faint in awe of my wobbly desktop. She's jealous! Yesss!
One thing, though: my tvtime program does funny things, like: freezing in a green goo-like snow. It worked perfectly before. Any Idea?

---

### Post by SuperMightyMo on 2006-05-01
Hey

Thanx, i really love this program, i coulnd't show it to anyone yet, i will tomorow. It's just great it was the easiest thing to install in a loong time.....

thanx

---

### Post by phaed on 2006-05-02
This is kind of a weird bug, and it probably doesn't have anything to do with your script, but it happens when I run your script too.

I recently did a fresh install of Dapper Beta 2.  Sometimes when I try to apt-get install several packages at once, it then starts REMOVING ubuntu-desktop.  I mean the whole thing.  I see it start removing gnome-panel, eog, etc.

I have to stop the process, then "dpkg --configure -a", then "apt-get install ubuntu-desktop" to get everything back.  Crazy, huh?  Anyway, that's what is preventing me from finishing running your script.

---

### Post by spidernik84 on 2006-05-05
Hi, i have to congratulate with you for your script: truly amazing.
But i would like to get back to the old 2d mode, coz I'm having some problems with my 3d apps and my gpu's fan's spinning like hell :)

Is there an easy way to get back to the old x? I read that someone said it's sufficient to rename the modified folders...but, how is it supposed to be done exactly? Thank u

---

### Post by jon_z on 2006-05-05
Ran script twice... Ubuntu boots up, Gnome starts, XGL does not be apparant to start because when I have had XGL load, the backdrop prior to the login screen is just black and white checkard, not the human theme..

ATI 9600 XT
dapper 6.06
2.6.15-21-k7 kernel

> jon@BlackBox:~$ Xgl

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

jon@BlackBox:~$compiz --help
Usage: compiz.real [--display DISPLAY] [--bg-image PNG] [--window-image PNG]
       [--refresh-rate RATE] [--fast-filter] [--test-mode] [--replace]
       [--sm-disable] [--sm-save-file] [--sm-client-id] [--help] [PLUGIN]...
jon@BlackBox:~$


Compiz and Xgl are both installed, just need to get them loading.
Any suggestions?

---

### Post by Hobbes on 2006-05-07
[QUOTE=phaed]This is kind of a weird bug, and it probably doesn't have anything to do with your script, but it happens when I run your script too.

I recently did a fresh install of Dapper Beta 2.  Sometimes when I try to apt-get install several packages at once, it then starts REMOVING ubuntu-desktop.  I mean the whole thing.  I see it start removing gnome-panel, eog, etc.

I have to stop the process, then "dpkg --configure -a", then "apt-get install ubuntu-desktop" to get everything back.  Crazy, huh?  Anyway, that's what is preventing me from finishing running your script.[/QUOTE]

Yea i just ran the script all the way through and then noticed that it completely removed everything under ubuntu-desktop, all icons, openoffice, metacity, gaim, gimp, evolution, etc. etc. all gone....

Luckily I was on a fresh (1 day old) install of dapper, so I can just redo everything, but man I DO NOT RECOMMEND this script to anyone who cares about their current packages or doesn't know what they are doing, LOL

---

### Post by Hobbes on 2006-05-08
*Update*

apt-got ubuntu-desktop back, few more packages, ran the script ~3 more times or so (making sure it never removed everything again), and voila, it is working.

So I will keep my statement that it is not recommended if you don't know what u are doing or care about ur current config, but if its a clean system or test system that you can risk losing, go for it b/c it may just work in the end. :)

---

### Post by pau on 2006-05-15
Hi all there,

Will this work on a graphics processor Intel 855GME?

Everybody's talking about nvdia and radeon but my 	
Fujitsu-Siemens Lifebook P7010 has an Intel 855GME...

The kororaa live cd with xgl worked well (almost, playing movies would stop X)

Thanks,

Pau

---

### Post by nero2150 on 2006-05-29
Great script 
Works fine on my rig x800 amd 3500+ 1gb fresh dapper 6.06 install
Only thing is i cant find compiz in  Application to configure though its been installed in synaptic. :-k 
Also how u get the change in opacity of windows to see the background :confused: 
Can anyone help? Plz

---

### Post by vishnu on 2006-05-30
Script ran fine.  However, nothing has changed.  I don't have the Desktop Effects icon in Gnome control center and "gnome-xgl-settings" is an unrecognised command from a terminal.  I got a new wallpaper and a Beagle shortcut on my desktop but nothing else.
I really want to give this a go but I can't see how to get it running after using the script.  I've tried running the script 3 times now.
Any thoughts?

---

### Post by anxean on 2006-05-30
Your script is very nice, I installed it everything works great I just have a few questions.

1. Whenever I open an application the window maximize and minimize animations (*you know the default black lined ones*) are real slowww, How can I turn them off?
2. When I use wobble and cube and such I get ugly tears.  Can I turn on Vertical Sync or Double Buffering?
3. The splash screen backround is all messed up, I cant tell what it reads but when I try to change it in art manager or looking in the login config it isnt there. How can I get rid of it or fix it.
 


Once again, your script is very nice! 8)

---

### Post by shanepardue on 2006-05-31
i can't imagine this xgl compiz thing would work with an old 700mhz crap machine would it? i may have to put ubuntu on my workhorse.

---

### Post by imjustabill on 2006-06-02
Be careful! I ran the script, rebooted, and nothing worked.  I had to revert to all of my old config files, and apt-get gnome-desktop to get most of my old programs back!!! For some reason, not only does it attempt to install Xgl, but it removes a good portion of your programs, and changes your theme and wallpaper!!!

---

### Post by sha_man on 2006-06-02
ok i just installed xgl+compiz with the script on dapper official release 6.06 ! It's cool!

Just:
[SIZE="4"][COLOR="Red"]I really don't appreciate every boot screen, wallpaper, theme, icons, etc... were **changed** and EVEN beagle was **installed** ! **Without a warning**!![/COLOR][/SIZE] :mad: :mad: :evil: 

**Can someone make a better one without those unnecesseray actions?**

---

### Post by jolan_jj on 2006-06-02
I've tried this script hoping to finally get Xgl and compiz to work. I've managed it  in Breezy and would like to have eyecandy in dapper, which is, so far, completely resistant to all tries to install compiz. Well, this script didn't install Xgl with compiz, but instead it removed my gdm, a bunch of applications and what not... I had to reinstall all from scratch... Just besides the things in previous post. Maybe i'm just having bad luck, but now i'm quite dissappointed and quite (to be honest) pissed off. Be warned...
:-?

---

### Post by darthvivi on 2006-06-02
I just installed the script...I'm guessing everything installed correctly but I have one problem...

Whenever I move windows, it lags and takes like 5 seconds to stop wobbling. However I think my computer is powerful enough to process that easily. I have an ATI Radeon 9600, and 1GB RAM. Also the Kororaa (sp?) Live CD had XGL and it ran fine on this computer. Any way to fix that?

Edit: I just disabled it. Even if it worked correctly it's kind of an annoying feature.

One other question, however: What is the super-key? Is it a key on my keyboard?

---

### Post by Omission on 2006-06-03
I installed this script and every appears to work, I'd tried manually to do this before and failed, so thanks for getting things to work :)

ATI 9800 PRO, 1 Gig Ram, 2.5ghz

Two issues was wondering anyone could help me with;

1) Window movements take a few seconds to 'settle', they move perfectly without lag but when they are placed they sort of take a while to.. well settle and display correctly.

2) When I minimize an application and then bring it back up from the tray it opens right at the bottom of my screen instead of in its last known location, this happens with all windows.

3) When i start an application i get a rather nasty black border than pounces at me and disappears when the window gets around to loading.

I apperciate this being beta (or alpha) software but as these things worked with the live CD i'm hoping its just a few config fixes.

Thanks

---

### Post by darknuala on 2006-06-03
After rebooting, I can't get back into X.  Instead, whenever I type startx i get this:  waiting for X server to shut down FreeFontPath:  FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

It tells me that everytime I try to get back into X.

HELP!

---

### Post by joshrobinson on 2006-06-03
this also screwed up my computers.. try at own risk

---

### Post by adam.tropics on 2006-06-03
[QUOTE=sha_man]ok i just installed xgl+compiz with the script on dapper official release 6.06 ! It's cool!

Just:
[SIZE="4"][COLOR="Red"]I really don't appreciate every boot screen, wallpaper, theme, icons, etc... were **changed** and EVEN beagle was **installed** ! **Without a warning**!![/COLOR][/SIZE] :mad: :mad: :evil: 

**Can someone make a better one without those unnecesseray actions?**[/QUOTE]

You really should read a bit further before diving head first in if you want room for credible criticism.

Page one, half way down, from the author:

> I had to install Xgl, Beagle, Firestarter, Gnomebaker and some other programs on several (=3) machines, so I just retrieve those modules in inst_xgl.sh. Maybe a useful move for a newbie, but not for all users.

---

### Post by lukesky on 2006-06-04
I tried the scripts with my ATI x700. It works well but I have two question for you:

1) Compiz don't have activate all effecs (for example water and bs don't show in active_plugins), how can enabled?

2) There is a graphics control panel to setting the xgl effects?

---

### Post by adam.tropics on 2006-06-04
You should go [here]("http://www.compiz.net/") and take a look around, you will find all the info you are after. Also, while it is pretty cool, be warned, the water plugin causes major cpu stress! 100% while it's running!

All the settings can be found:

main menu-->system tools-->configuration editor-->apps-->compiz

---

### Post by alfonz on 2006-06-04
This script worked like a charm for me. Thanks

I have one question that a few others have asked on this thread and that is 
How do I get back the restart/shutdown buttons back?

Any help will be great.


great job.

---

### Post by lukesky on 2006-06-04
I have the same problem: the buttons don't show!

Other question:

After installation of XGL the acceleration 3D of my Ati is Disable, why?

How can enable it?

---

### Post by volvoguy on 2006-06-04
I hate to be the guy that complains, but you should make it clear in  your first post that this doesn't just install xgl related stuff. Firestarter? Gnomebaker? Mono? Beagle? A kernel I don't want to run? Wallpapers from all over the web (that replace the one I have set)? Streamtuner/streamripper? 

Maybe I missed something stated in another thread or something, but the description and presentation of the purpose of this script is very misleading. So much has changed that I'm reformatting. 

This script may be the greatest thing in the world, and lots of people like it, but I think it's only fair that you detail what it's going to do when you claim that it's just for installing/configuring xgl. That task isn't very difficult. I thought I was getting a script to make my life a little easier. 

Sorry for being grumpy. </rant>

---

### Post by adam.tropics on 2006-06-05
lukesky,
> Other question:

After installation of XGL the acceleration 3D of my Ati is Disable, why?

I am afraid that 

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
```

is the current price paid for xgl. If you are in need of it for games etc, there are workaround on the compiz.net site.

volvoguy,

> I hate to be the guy that complains, but you should make it clear in your first post that this doesn't just install xgl related stuff. Firestarter? Gnomebaker? Mono? Beagle? A kernel I don't want to run? Wallpapers from all over the web (that replace the one I have set)? Streamtuner/streamripper?

Maybe I missed something stated in another thread or something, but the description and presentation of the purpose of this script is very misleading. So much has changed that I'm reformatting.

Whilst I accept that there is no mention of it in the first post, one would assume that knowing this is all very much testing software, you might at least have completed reading the whole first page,

[post #9]("http://ubuntuforums.org/showpost.php?p=859916&postcount=9")

Nothing personal, but a couple screensavers and backgrounds, a firewall, a search tool and a cd authoring tool hardly warrant formatting anything! Just uninstall whatever so badly offends you and all will be well.

I find myself reccomending this quite alot at the moment, but on a general note, if anyone is having problems setting up compiz/xgl, then really the best place to go read up for solutions is [http://www.compiz.net]("http://www.compiz.net") as that is the central point for most compiz development relevant to Dapper at the mo.

---

### Post by bobablob on 2006-06-05
First off, thanks for the script!

My installation went allright, but I'm having trouble getting a few of the plugins to work:  Wobbly is fine, and the cube effect when switching workspaces is active. A few others too. But the application switcher and the scale plugins...the only ones I really care about .... won't work.  Any ideas on what I might have to change?  Thanks.

---

### Post by Lee_I on 2006-06-05
I ran the script and everything worked great! However, upon rebooting later, I found that all the ffects or disabled. Yet, what's strange is XGL is still running as a process.


Another thing is that when it boots normally (which it does everytime you restart, the computer runs very slow. For example right now the screen is just showing me typing "Another thing"....so it's a little strange.

And just to clairify,normally means what it's like without XGL. I can reapply XGL by simply running the script again. However it is reset when you restart again =/

---

### Post by nicky75 on 2006-06-06
I had installed XGL e compiz by this method and works fine, but now all the games that use 3D acceleration and the games of xmame don't work. Is there a system to uninstall XGL and compiz that is installed by this script? Thanks!

---

### Post by WijbrandSchaap on 2006-06-06
I had something similar: my tvcard went green using compiz. I didn't as much solve the problem, but found a workaround: just create another user, assign 'standard session/no xgl' to this user en switch to this user to play your games. Your original user (with compiz) will remain active for receiving email, and you can ctrl+Alt+F7 and ctrl+Alt+F8 between the two.
This works for me. Hope it works for you.

---

### Post by QkEterror on 2006-06-06
[QUOTE=ghostzapper]Hi,

first of all thank you for this script, even though it didn't run as expected. 

Here's what happened:
Started the script, several packages were downloaded. Everything worked fine until the restart. Restarted the machine and finished the configuration. Another restart. Now the following happens:

I see the login screen and when i enter my login information i can see the  checkered Background of the X Server shortly, the login sound plays and then my sreen turns black with a mouse pointer on it. It seems to work underneath as the pointer changes, when i press CTRL & ALT & right mousebutton i.e. What could this be? Tried to run the script twice but same effect.

Machine is a Pentium 4 Dual Core 3GHz, 2GB Ram, ATI Radeon 9200 PRO. Dapper is Version 6.06.

Thanks in advance.

Ghostzapper[/QUOTE]
I have the same problem. Does anyone know what the problem could be? I would really like it to work. TNX

---

### Post by mhafren on 2006-06-06
Hi everybody.
The script worked (almost) like a charm. Xgl/Compiz running fine here, however I too lost the shutdown and restart icons. The thing I would like a solution to is my terminal won't start from my shortcut anymore. I've become so used to starting my terminal with <Control><Shift>t but that doesn't work anymore after installing xgl/compiz. And before you ask I have checked the keyboard shortcut settings and they are alright. Any ideas?
Thanks for the script.

---

### Post by nicky75 on 2006-06-06
[QUOTE=WijbrandSchaap]I had something similar: my tvcard went green using compiz. I didn't as much solve the problem, but found a workaround: just create another user, assign 'standard session/no xgl' to this user en switch to this user to play your games. Your original user (with compiz) will remain active for receiving email, and you can ctrl+Alt+F7 and ctrl+Alt+F8 between the two.
This works for me. Hope it works for you.[/QUOTE]

THANK YOU!! :D

---

### Post by RAF2 on 2006-06-06
Hi!

I downloaded and installed this script. It is a wonder! I really liked it. :)

Only two little problems:

1- I lost my restart and shutdown buttons. How can I get them back?

2- This one happened after I installed the Skydome plugin (step E): The windows now don't have the top-right corner buttons (minimize, maximize and close) anymore. How can I get them showing up again?

***EDIT**: Nevermind about the second question, I fixed it, I had installed the Ubuntu's .deb instead of Gnome's .deb. :)*


Thanks.

---

### Post by mrazster on 2006-06-07
Got a little n00bish question fellas...it says int the first post that the script will do this:

> C) It may ask you to reboot after it has upgraded the Linux-kernel. Just reboot and re-run the script (step B).

I've just installed Dapper and custom compiled the 2.6.16.19 kernel....will this script somehow interfer or do anything to my current kernel?

---

### Post by dvader on 2006-06-07
I've installed Dapper 606 after the final release .  Used the script for xgl , have the nvidia driver installed , and using the gnome desktop     The script worked as indicated in the original text .  Machine boots up , and the only problem is Xgl isnt working .. Using the keys in the Ubuntu and Suse How to's .  Where do I start looking for a problems

Dvader

Thanks

---

### Post by SuperMightyMo on 2006-06-08
Hey

Is this script ofline or something, i keep getting a 404 error, it worked for me the first time and now i can't use it anymore.

---

### Post by acidjedi on 2006-06-09
I'm getting 404 error as well, and I really want this!

---

### Post by Biggie on 2006-06-10
the same here
anyone got this file downloaded ? can he/she share it with us please ?

---

### Post by Sirkent on 2006-06-10
The author of this thread has edited the first post to say:
> This message and this guide is deprecated and old !
Look for other guides on the Ubuntuforums.org or [http://compiz.net](http://compiz.net) 

The file is still there, but renamed and with a section that prevents the script from running. This is just as well as the script no longer appears to work properly (on a vanilla Dapper installation).

So it looks like you'll have to follow one of the other guides. One which is reliable, quick to do and easy to reverse but not necessarily the best way of doing things is [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)

Good luck!

---

### Post by Biggie on 2006-06-10
hm it looks fine, i will try id tonight, thanx :)
the reasons i was asking for that file were that im total linux noob and only this guide worked for me :)

---

### Post by Biggie on 2006-06-12
oh damn, doesnt work here ( is it possible that it causes fact im running mobile ati 9700 ? ) like every guide i have tried so far (except this one but i cant get the file again )
im pissed off, totally :(

---

### Post by adam.tropics on 2006-06-12
[QUOTE=Biggie]oh damn, doesnt work here ( is it possible that it causes fact im running mobile ati 9700 ? ) like every guide i have tried so far (except this one but i cant get the file again )
im pissed off, totally :([/QUOTE]
 [This guy]("http://www.compiz.net/viewtopic.php?id=266"), post 5 managed it with the same video card. He used method [2 here]("http://www.compiz.net/viewtopic.php?id=389").

---

### Post by Ra211 on 2006-06-12
Those who still require an automated installation of Xgl and Compiz should check out [this]("http://ubuntuforums.org/showthread.php?p=1128751") thread.

That script was originally based on the script from this topic, but is much better. It installs Xgl and Compiz in a similar way to "method 2" posted above.

---

### Post by Biggie on 2006-06-12
hm thanx guys, im going to try that first one that adam has posted
but before i do so, is there any app that can make a image of disk (something like ghost for windows) ? if it is i'd be pleased

---

### Post by BayGuy27 on 2006-06-12
I cannot find a copy of the "inst_xgl" script. I can only find inst_xgl.sh.OLD at [http://www.futuredesktop.org/dapper/](http://www.futuredesktop.org/dapper/).

I tried renaming the file and running the script, but I am getting "Developers notice:
This script is old and currently under maintenance !"

Can anyone paste a working copy??? Thanks,

Dave

---

### Post by Slicedbread on 2006-06-12
Try this one[http://www.ubuntuforums.org/showthread.php?t=194993]("http://www.ubuntuforums.org/showthread.php?t=194993")

---

### Post by BayGuy27 on 2006-06-12
Thanks for the link, however I tried that script before this one. I recieved the following message in terminal:

---------------------------------------------
dave@ubuntu:~/Desktop$ sudo sh Ra211.sh
Checking Linux distribution and version. Expecting to see Ubuntu Linux 6.06 (LTS).

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06 LTS"


Error:
dave@ubuntu:~/Desktop$
----------------------------------------------

There is actually no error listed next to the word. Not sure what would be causing this either.

---

### Post by cobbweb on 2006-06-13
sudo wget [http://www.futuredesktop.org/dapper/inst_xgl.sh](http://www.futuredesktop.org/dapper/inst_xgl.sh)
--17:40:00--  [http://www.futuredesktop.org/dapper/inst_xgl.sh](http://www.futuredesktop.org/dapper/inst_xgl.sh)
           => `inst_xgl.sh'
Resolving [www.futuredesktop.org](www.futuredesktop.org)... 193.201.35.91
Connecting to www.futuredesktop.org|193.201.35.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:40:01 ERROR 404: Not Found.



I try to download it but don't work... any reason why? Is it not there anymore??

---

### Post by KilL_MaSTeR on 2006-06-30
[QUOTE=cobbweb]sudo wget [http://www.futuredesktop.org/dapper/inst_xgl.sh](http://www.futuredesktop.org/dapper/inst_xgl.sh)
--17:40:00--  [http://www.futuredesktop.org/dapper/inst_xgl.sh](http://www.futuredesktop.org/dapper/inst_xgl.sh)
           => `inst_xgl.sh'
Resolving [www.futuredesktop.org](www.futuredesktop.org)... 193.201.35.91
Connecting to www.futuredesktop.org|193.201.35.91|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:40:01 ERROR 404: Not Found.



I try to download it but don't work... any reason why? Is it not there anymore??[/QUOTE]
same here...does anyone have another link?
or maybe send it by mail?

---

### Post by givré on 2006-06-30
Did you see the message on top?

[I]This message and this guide is deprecated and old !
Look for other guides on the Ubuntuforums.org or [http://compiz.net](http://compiz.net)[/I]

Try that [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

---

### Post by Drakx on 2006-07-19
thanks

---

### Post by balki2005 on 2006-08-27
hello,

I tried the script  and works  fine,  only I don't find any program to configure it under applications neither system ???

and when I want to  start a program  it's  very slow ...  ones  started it's ok ?

who  can help  me finetune it ?

thanks in advance,


balki2005

---

### Post by Sweet Spot on 2006-09-06
Just a couple things before I go further w/Xgl & Compiz etc...  I've been doing some reading/research, and am probably far from done because I still have lots of questions, but what I need to know doesn't require researching on the same path as I have been. So, the question is:

The script found on the first page of this thread... Is it considered the easiest and most up to date way to install Xgl/compiz ?  My situation is that I have a fairly fresh Ubuntu install, and used Automatix to install my Nvidia card (Gforce 2 MX 400). Other than that, I"m not sure of what to ask in regards to what info I need to know etc... 

Doug

---

