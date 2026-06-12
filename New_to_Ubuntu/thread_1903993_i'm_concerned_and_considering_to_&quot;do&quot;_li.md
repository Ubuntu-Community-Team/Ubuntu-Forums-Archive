---
title: "i'm concerned and considering to &quot;do&quot; linux from scratch"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by il_maniscalco on 2012-01-03
ok, I installed ubuntu 11.10
unity appeared great, but soon I decided to install xfce (xubuntu environment) as I did not find the basic task in unity.
then I'm playing with ubuntu from a few days and I'm noticing some high, but have to say also some low.

the best thing is the speed, my laptop (a normal emachines 2gb laptop) is really happy as windows seven became an elephant in just few months (I can't say what happened when I launched a java application, unbearable).
i'm doing the usual tasks I did using windows xp and seven, but I'm find too, too many buggy applications, or just I'm not able to use them or to use the whole linux (it'd be normal I guess), or this kind of installation (xfce "over" unity) is buggy in itself.
sometimes window applications disappear and I can't recover them, i install some application and then they never launch, or they launch and it doesn't appear nothing.

so I'm worried as I was hoping that ubuntu was really a fast alternative to windows but I'm doubting it now after some enthusiastic begin.

and I was considering that to fully understand how to use linux the best approach would be "linux from scratch" and not ubuntu (I was hoping that I could join both the souls, window and shell commands here) because I feel lost and I don't know if I can guess the right route to fully and well learn this new (for me) operating system.

consider I have a small background on programming (and still learning) and am not totally "ignorant" and don't think I need the simplest thing findable as ubuntu could be, because I'm supposing ubuntu is greatly simple, but the cost is that it authomatize too much for me making me lazy.

I have to add one thing: I find in the net many guides, tutorial, but everytime i feel as they are mechanic and you can't full understand how things work. and man command seem to help but I don't think one can allow himself to "guess" what's the right command to do a particular task so googling is necessary.
I'm saying those thing like "ps aux | grep appName" to see if an application is running... I could find ps only googling or there's a way to do that research of knowledge offline? 

sorry for the (small) ranting, but I need some basic beginner suitable advice :)

---

### Post by bluexrider on 2012-01-03
Oh my GOD! You just need to install something that works.....try [http://pinguyos.com/](http://pinguyos.com/)

---

### Post by QIII on 2012-01-03
It's generally easier for everyone to help you with one item at a time.  If you could pick a specific one for us to deal with in this thread, we can work on that.  Then start another thread for the next issue.

---

### Post by SoFl W on 2012-01-03
LFS is for advanced users who really want to torture, I mean fine tune their Linux experience.  We used it at work for a specific application on specific hardware and it was taking a lot of time.  The powers that be decided they didn't want to go in that direction.

As stated above, install a pre-built distro, you will have support.

---

### Post by KdotJ on 2012-01-03
Not to discourage you at all, but LFS is a different ball game. Its hardcore, really hardcore. By all means its great to try it, if you have the patience and skill and if you do I wish you the best of luck. i wouldn't recommend it to anyone who is new to linux, or even people who are "quite good". Maybe consider a simpler distort which still gives you control over the overall system, such as Arch, Slackware or Gentoo.. But still difficult in their own right. 

Good luck!

---

### Post by QIII on 2012-01-03
Back in the day we had to roll our own -- and quick help was scarce!

I'd not go back to that unless I wanted something really lean for a single purpose.

---

### Post by bluexrider on 2012-01-03
> **QIII said:**
> Back in the day we had to roll our own -- and quick help was scarce!

I'd not go back to that unless I wanted something really lean for a single purpose.
My brain hurts.................................! Just use pinguy or Linuxmint Katya

---

### Post by il_maniscalco on 2012-01-03
> **bluexrider said:**
> Oh my GOD! You just need to install something that works.....try [http://pinguyos.com/](http://pinguyos.com/)

sorry. are you saying that this overall is better (for me) than ubuntu stuff, or that MY ubuntu (as I mentioned 11.10 using xfce) fate is not work properly? what advantage I'd gain on that? consider that I normally install miriads (thousands) of application usually, will pinguOs let me do that?

(edited)

---

### Post by QIII on 2012-01-03
Rider is simply suggesting another distribution that you might find to be more to your liking.  I don't know what specific issues you have encountered with Ubuntu or how you got to them.

Trying to do Linux from scratch is really not necessary.

---

### Post by Learning Linux 2011 on 2012-01-03
Although a lot of people seem to be defending it, I think your problem is the new Unity interface.  I personally hate it, and like you (and MANY other people) find it difficult to use, even doing basic tasks.

I would strongly recommend going back to what is now called the "classic" environment.  There are directions as a "sticky" in the Absolute Beginner's section at the very top.

The classic desktop is much more intuitive for someone used to Windows who has been using computers for a long time.

Once you get back to the classic destop, you may want to purchase or download a book that better explains Linux and/or Ubuntu.  A book will be able to explain the details.  Linux is very much like Windows in a lot of ways, but there is a learning curve.  You will be able to figure things out. but like I say, you will probably need a tutorial.

---

### Post by 1clue on 2012-01-03
No matter what anybody else says, YOU are the only person who can decide which OS is best for you.  You've given us a couple lines about what matters to you in the few moments it took you to write your post, but at some other point you will undoubtedly realize you forgot something.

The way you worded the original post, I somehow think you're going to really eat this Linux stuff up.

If you want a minimal system, then try this approach:
[LIST=1]
[*]Install Ubuntu Server
[*]Install xorg and a window manager of your choice.
[*]Install only the apps you want.
[/LIST]

Now it's time to dispel some myths:
[LIST=1]
[*]The only way Linux is faster than anything else on any particular hardware is if it's running less complicated software than whatever other OS.
[*]If you load your desktop down with tons of widgets, it will be slow.
[*]Having an application installed but not in use unless you need it does NOT slow the system down overall.
[*]Ubuntu generally loads you up with widgets and turns a significant number of them on.
[/LIST]

If you get the hang of using Ubuntu-server and configuring what you want and it's still not doing it for you, then try something like LFS or maybe Gentoo.

Gentoo is my "other" favorite distro.  You literally compile every app installed on the hard drive.  You literally configure the system with compile options that make sense for you.  If you want to learn how Linux works, you could wind up on Gentoo or some other source-based distro.  A muscular processor and significant RAM is sort of a prerequisite if you're going to experiment with Gentoo.

---

### Post by JC Cheloven on 2012-01-03
As an attempt to answer the points in which yoy have been somehow specific:
> **il_maniscalco said:**
> 
but I'm find too, too many buggy applications, or just I'm not able to use them or to use the whole linux (it'd be normal I guess), or this kind of installation (xfce "over" unity) is buggy in itself.
You have to develop some "feeling" about what is convenient to use and what not. The packages (programs) are free software, often maintained by a small group of people, and occasionally fall in a "badly maintaned" state, or even become completly orphaned. They usually remain usable, but when the distribution updates something (qt libraries for example), the program may not work as expected, although it still compiles. To sum up: yep, not everything in the repos works as it should al the time.  

> 
sometimes window applications disappear and I can't recover them, i install some application and then they never launch, or they launch and it doesn't appear nothing.
People who uses ubuntu inspired by me, tell me similar cases lately. I myself experienced some magic "window app closing". This was not at all the case until 10.10. I'm even thinking about the possibility of a sabotage from the inside of gnu-linux-ubuntu, but perhaps it's only a consequence of the energy spent in developing new DEs. Also it has the sympthoms of randomness typical of a hardware incompatibility... dunno really. 

In any case, I don't see the point of building from scratch. Instead you could try another distro (say, fedora) to see if you have better luck with your issues.

EDIT: I'm not sure about blaming Unity for this either. I'm using LXDE lately and also experienced similar issues.

---

### Post by JC Cheloven on 2012-01-03
> **1clue said:**
> 
If you want a minimal system, then try this approach:
[LIST=1]
[*]Install Ubuntu Server
[*]Install xorg and a window manager of your choice.
[*]Install only the apps you want.
[/LIST]

A server install is not the best option for a desktop computer. Better to install a command-line system from an alternate desktop cd (any K-X-Ubuntu will do), and proceed from there. Please see
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by grahammechanical on 2012-01-03
I would recommend creating a few extra partitions and installing different versions of Ubuntu or different distributions for that matter and then multi-booting.

I think that people who install Ubuntu and then install the other desktop environments over the top of it are asking for trouble. If you want to try Xubuntu, then download the iso and install it. Do not try to get Ubuntu/Gnome/Unity looking like something else and then blame Ubuntu for the mess.

Regards.

---

### Post by Toafan on 2012-01-03
For the command line (not touching the other discussions), there are two options.     

One, you could try the virtual terminals.  There are 6 or 7 of them, press <ctrl>-<alt> and one of the "Function (<fn>) keys to switch between them.  Most of them will put you in command-line mode.  On (normal) Ubuntu , #7 is the graphics, and the first 6 fn keys get you other command lines.  It's different on other distros (fedora, for example, has the graphics on f2).  You'll need to log in with your normal username and password. 
   Otherwise, you could use a terminal window.  I use Guake to pull up a command line that takes up the whole screen.  The terminal program that comes with Ubuntu would work to.  These are almost exactly the same as the above, but you won't have to log in. 

You may also want a command-line tutorial.  I like linuxcommand.org.

--------
The single most useful command you can know is the "man" command.  When in doubt, you can use "man" to find out more about all sorts of things.  type ```
man man
``` at a command line to find out more.

---

### Post by 1clue on 2012-01-03
> **JC Cheloven said:**
> A server install is not the best option for a desktop computer. Better to install a command-line system from an alternate desktop cd (any K-X-Ubuntu will do), and proceed from there. Please see
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I never tried to imply that it WAS the best option.  It's a simple-to-master way to learn how Linux works, and to decide what sort of packages are necessary to make the system which fits you best.

IMO the best way to tweak an environment to your personal ideal is to use something like Gentoo.  It's also the best way to learn how Linux works, at least in a non-structured way.

> **grahammechanical said:**
> I would recommend creating a few extra partitions and installing different versions of Ubuntu or different distributions for that matter and then multi-booting.


Why not just use VMs?  That way you can run several at once.

> 
I think that people who install Ubuntu and then install the other desktop environments over the top of it are asking for trouble. If you want to try Xubuntu, then download the iso and install it. Do not try to get Ubuntu/Gnome/Unity looking like something else and then blame Ubuntu for the mess.

Regards.

I strongly disagree.  If you aren't careful you can get yourself into a bind, but there is no reason why you can't have several window managers configured and then switch between them by logging in as different users, or even as the same user.  It's been happening for years.

---

### Post by mastablasta on 2012-01-04
> **1clue said:**
> I never tried to imply that it WAS the best option. It's a simple-to-master way to learn how Linux works, and to decide what sort of packages are necessary to make the system which fits you best.
 
IMO the best way to tweak an environment to your personal ideal is to use something like Gentoo. It's also the best way to learn how Linux works, at least in a non-structured way.

Wouldn't it then be better to use mini iso?: 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Ubuntu from "scratch" :-)
then you can install only the things you need. for example don't need blutooth? don't install it. 
 
> 
I strongly disagree. If you aren't careful you can get yourself into a bind, but there is no reason why you can't have several window managers configured and then switch between them by logging in as different users, or even as the same user. It's been happening for years.
 
yes there is. if you just install desktop (for example Xubuntu desktop) and then swtich to it on start, you will end up with widgets and programmes doing same things. e.g. 2 network managers, 2 battery monitors... one will be left there from Gnome. they will use the system resources. which might be the thing that slowed down the OP's maschine.
> **JC Cheloven said:**
> 
People who uses ubuntu inspired by me, tell me similar cases lately. I myself experienced some magic "window app closing". This was not at all the case until 10.10. I'm even thinking about the possibility of a sabotage from the inside of gnu-linux-ubuntu, but perhaps it's only a consequence of the energy spent in developing new DEs. Also it has the sympthoms of randomness typical of a hardware incompatibility... dunno really. 
 
 
it might have something to do with new Gnome. 
 
I know some Gnome applications do that in KDE. They just shut off when you start them. usually you can get an error output if you run them from terminal. Other times nothing happens there either that would give a clue.

---

### Post by il_maniscalco on 2012-01-04
I would like to thank everyone answered, some of the tips are great and I consider this a warm welcome in this community :)
Now coming back to my issues.
I want to say to QIII that in effect, those few initial days I spent just to get the habits to Linux, exploiting my free vacations time.
I installed Chromium to surf (I'm a web-developer and I prefer it to Firefox, sorry :) ) and it works magnificently.
I also installed Eclipse and it works very well, and above all it's 10x faster than in my previous Windows 7 environment.
I installed VLC and it works as desired, I tried LibreOffice and is great. Also the PDF reader is fantastic and quick as hell!
What I noticed, is that this "huge" applications are nicely maintained and probably the case of bugs is in a long way reduced, as JC Cheloven remarked (or at least is what I imagine it means).

So what I'm still "battling" with?
Well my first "job" was setting up my Easycap DC60 analog capture (it was a casual task), in some way I had success but I am not satisfied as I just copied and pasted some command line mplayer string found googling, without really understanding what I was doing, in fact I tried to use VLC but I stopped myself soon as Windows VLC let me see all the capture video and audio hardware in the menu, while the linux version is asking you to insert the right command and although I figured it for the video, I didn't find the right one for audio. I'm sure that I'd solve it in some way but I don't find very useful just writing something in a mask and see if it works if I really can't handle what I'm doing, what's an ALSA driver or a OSS emulation or a SDL library and stuff like that...

Then I tried to install Jdownloader to download some MP3 from youtube, but it launched just the first time, than everytime I tried to launch I just noticed it impairs heavenly with my laptop temperature (the fan starts to complain) but see nothing. Again, I googled a bit and find some possible workaround (had no time to test it) but I don't think this is the right approach, I'd prefer to know why a thing is happening and what to do to prevent it.

Another thing, there's tvtime window (i tried it always for my video-capture activities) that disappears and I can't find the process, but if I tried to relaunch it, it is saying it's already running. Perhaps a bug but I want to be sure I'm not doing something wrong myself!

And then some general issues, why I can't easily add my applications to the desktop? Why my low-bar suddenly lost all of the links and shortcuts I put? And probably something I'm not remembering at the time.

Now a bit of detail as 1clue (rightly) told that I was a bit generic.

As I'm planning to use this system for general development and web development, it will be great to use a good LAMP setup plus some IDE (I'm currently programming in Java, PHP, Javascript and some C).
I tried GIMP as I'd like to see if it can substitute Photoshop for basic webdevelopment tasks as create backgrounds, buttons and layouts but still I didn't find the time to use it.

Thanks to Sofi W and KdotJ for the tips on LFS, I would have tried just for a learning purpose, as as you can imagine when one begins something new, maybe the most difficult and important part is choosing the best approach (in terms of quickness of learning and quality), and I heard that LFS, as Gentoo, Archie and Slackware are the best options in this case (not that I firmly believe in this, just some reading about) that is what in some extent 1clue said.
Really interesting your advice and I have to say that the Ubuntu Server distro was my first "touch" with linux at a course I'm following, where we played with lamp on a virtual machine environmente. This is quite interesting as I never considered to add a window environment to it and see if it was enough. Now I'll consider, above all because as I said, I'm planning to use LAMP extensively. But I feel that also mastablasta advice deserves consideration. I'm stressing that I don't particularly need a low-memory environment as my laptop is quite good (2 GB memory and dual core Intel-based processor), but I want a clean system and, you pointed it, adding what I really need from zero without too many dublicates and above all something that works good. And yes I already doubting the OS is not what is fast or slow in itself, but Linux seems to me better customizable than Windows above all windows7 and then I like the idea to choose everything (if possible) and although I was planning to seriously try Linux from years I was greatly satisfied from Windows XP but now that I'm seriously engaged to developing I think that seriously coupling it with linux and all the related stuff could be a good idea.

I want to confirm to LL2011 and farlander762 that Unity was initially impressing from a "graphical" point of view, but then I began wondering how to replace the left sidebar, to link a terminal to the sidebar, to change the order of the icons, to add the applications to the desktop, some other spare task that induced me to google for it and found a big criticism to unity that pushed me to try the XFCE (a bit reluctantly, as I was doubting that adding a new desktop environment was completely safe, as grahammechanical too is tipping). Now I'm considering to reinstall everything from scratch and in fact I still haven't setup nothing critical as I'm still in the process of understand what's the best environment to use.

Toafan, that was just the kind of practical advice I'm thirsty, I already started to read the linuxcommand.org site and I found it amazing and hope will put me in the right track with the shell :) And yes I was referring to the virtual terminal (or window terminal) like windows command at this time.

To grahammechanical I say that it was just the thing I was liking to avoid, for practical reasons, I simply don't want to trouble myself with partitioning and too many boot options as I'm sure that the soul would be always the same and at the end I don't feel I need to find the ideal distro for me at the moment, but just to easily handle linux as I easily handled windows. Than perhaps I will be encorauged to find the ideal distribution with my ideal environment and my ideal applications :) anyway thanks for the contribution.

This is my general thoughts on this.
Let me know if you have some tips and advice about. For sure I won't desist as I feel at this time is the right choice I can take (although there's always my windows 7 partition waiting for me at this time...).

---

### Post by KdotJ on 2012-01-04
> **1clue said:**
> 
I strongly disagree.  If you aren't careful you can get yourself into a bind, but there is no reason why you can't have several window managers configured and then switch between them by logging in as different users, or even as the same user.  It's been happening for years.

I'm with you on this. I've done this ever since I started properly using linux and have never had any issues at all. The only thing that annoys me slightly is having the application menus being clogged up programs from multiple DE bases.

---

### Post by 1clue on 2012-01-04
> **mastablasta said:**
> yes there is. if you just install desktop (for example Xubuntu desktop) and then swtich to it on start, you will end up with widgets and programmes doing same things. e.g. 2 network managers, 2 battery monitors... one will be left there from Gnome. they will use the system resources. which might be the thing that slowed down the OP's maschine.


Then there is something extremely broken with Xubuntu's default installation and they need to fix it.  Every time I've ever installed multiple window managers everything worked fine.  That said, I haven't done it on Ubuntu that I can recall, but it works fine on RedHat, Gentoo, Suse, Slackware and Debian.

The various window managers and desktop environments are designed to work around each other.  If you use the same desktop environment on multiple window managers, the only difference between them would be the level of interaction between the DE and the WM.

---

### Post by Toafan on 2012-01-04
> **il_maniscalco said:**
> 
And then some general issues, why I can't easily add my applications to the desktop? Why my low-bar suddenly lost all of the links and shortcuts I put? And probably something I'm not remembering at the time.

<snip><break>

I want to confirm to LL2011 and farlander762 that Unity was initially impressing from a "graphical" point of view, but then I began wondering how to replace the left sidebar, to link a terminal to the sidebar, to change the order of the icons, to add the applications to the desktop, some other spare task that induced me to google for it and found a big criticism to unity that pushed me to try the XFCE (a bit reluctantly, as I was doubting that adding a new desktop environment was completely safe, as grahammechanical too is tipping). Now I'm considering to reinstall everything from scratch and in fact I still haven't setup nothing critical as I'm still in the process of understand what's the best environment to use.


Not sure what you're talking about with "add applications to the desktop".  Putting launcher/shortcut links on the desktop, as is common on windows, maybe?  If so, That's what the launcher is supposed to be for (though this only helps you with Unity).  There are ways to ad launchers to the desktop (I've put custom ones there myself), but it's insanely more complicated.

The easiest way to add apps to the launcher is supposed to be dragging them there from the the dash (search view) -- just find them there, and drag them over.  I can't say whether it works from personal experience, though.
The second-easiest way is to right-click on a running app and select "keep in launcher".  Works as advertised.

None of the above helps you if Unity bombed on you, however...
Unity not coming up when you log in is a separate problem from it just disappearing/being gone.  This is large enough that I won't try to address it in this post :)

This may help with "link a terminal to the sidebar", as well - just add the terminal app, and then you can bring it up approximately at will.

Back to the apps, Gnome-2 (before unity and gnome-3) had something where you could add app shortcuts to the various bars and panels.  It wasn't as easy as the Launcher is supposed to be, but it wasn't to hard as you could select the item to add from the pulldown menu's list in the shortcut adder.  XFCE may have something similar, look in "add to panel".  (that's pretty much all I got on XFCE, though.)

---

### Post by bluexrider on 2012-01-04
> **il_maniscalco said:**
> sorry. are you saying that this overall is better (for me) than ubuntu stuff, or that MY ubuntu (as I mentioned 11.10 using xfce) fate is not work properly? what advantage I'd gain on that? consider that I normally install miriads (thousands) of application usually, will pinguOs let me do that?

(edited)
What I can tell you is this.  I have installed and used different distros which have included Ubuntu, Arch, Debian, Suse just to name a few. The ones that have impressed me the most because I did not have to screw around with configuration files or drivers were Pinguy and Linuxmint.

I like the 'out of the box' experience and if I want to add an app or delete something I can easily do it.

---

### Post by larrypg on 2012-01-04
Hello,

Just a thought...before you start distro hopping it might be a good idea to try and learn the one you are using (which ever it is).  Most of the things you have mentioned are quite easy to do or a few search query's would give you the answer.  If that does not work then a quick question in the forums can be very helpful.  

I am not sure the results will be much different if you only give another distro a few days to learn how an OS is to be used.

---

### Post by il_maniscalco on 2012-01-04
> **larrypg said:**
> Hello,

Just a thought...before you start distro hopping it might be a good idea to try and learn the one you are using (which ever it is).  Most of the things you have mentioned are quite easy to do or a few search query's would give you the answer.  If that does not work then a quick question in the forums can be very helpful.  

I am not sure the results will be much different if you only give another distro a few days to learn how an OS is to be used.

yes in fact, I'm actually deciding if reinstalling fresh without Unity (I'm sorry I'd like to try it later, maybe when I'll be more used with all the stuff), or going on with this ubuntu 11.10 and using xubuntu window manager... advices?

---

### Post by JKyleOKC on 2012-01-04
> **il_maniscalco said:**
> yes in fact, I'm actually deciding if reinstalling fresh without Unity (I'm sorry I'd like to try it later, maybe when I'll be more used with all the stuff), or going on with this ubuntu 11.10 and using xubuntu window manager... advices?If you're considering reinstallation, my recommendation would be to install Xubuntu 11.10 rather than adding XFCE to Ubuntu 11.10. The Xubuntu version will have the same kernel and drivers, but the other stuff will be limited to the XFCE libraries, and the actual GUI will be that of XFCE.

I've been using Xubuntu for several years and find it to be much less bloated than the main Ubuntu releases. Of course, what constitutes "bloat" is in the mind of the user and will vary from one person to the next, but I've found the utilities that come in Xubuntu to be adequate for most of my needs. The one place where they come up short is in networking to Windows systems, but fortunately that's no longer a major issue for me. My Windows needs are met by using VirtualBox and creating special-purpose WinXP and Win2K virtual machines as needed (such as for running my income tax software each April).

LFS sounds rather inviting as a way to learn from the bottom up, but unless you're quite comfortable working at the assembly-language level, it'll have you banging your head against the wall. High-level languages have spoiled most of us over the past dozen years or so... Most of the code used in LFS is actually in C, but it's very low-level C and debugging requires you to think like the machine. Just download the source files for any part of the kernel, and you'll see what I mean!

---

### Post by JC Cheloven on 2012-01-04
> **il_maniscalco said:**
> 
Toafan, that was just the kind of practical advice I'm thirsty, I already started to read the linuxcommand.org site (...)


Another one: [https://help.ubuntu.com/community](https://help.ubuntu.com/community)

The ubuntu community contributed documentation is a great source of knowledge, hints, and ideas. Just type in the search box something as "server gui", "firewire audio", "nvidia drivers", "server security", "low memory systems", or just a single word like "programming". 

I think you'll love it, as much as I do since I first found it ;)

---

### Post by corrytonapple on 2012-01-04
If you want Ubuntu support still, just use the Debian netinstaller.  I did the same, and had the same opinions (but not issues) as you have.  Look here:
[http://openubuntu.com/index.php/topic,1743.0.html](http://openubuntu.com/index.php/topic,1743.0.html)

More Clarification/to the point:
Get the Debian Netinstall image from here:
[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)
Get one of the first two images, but Bitorrent is preferred.  Don't bother with the whole business card image.  Install to the Ubuntu partition, it will wipe out all the old data.  Then, you get to a CLI.  Login as root.  Then type:
```
apt-get install sudo xorg xfce4 xfce-* xfdesktop4
```
then use
```
sudo apt-get iceweasel
```
Install more as you want.  We're here in the Open Ubuntu Forums in that thread if you want help.  Its hard to copy and summarize all that data right here.

---

### Post by Buntumatic on 2012-01-04
You can do LFS, just leave some space for experimenting when partitioning your hard drive for Ubuntu. This way you will have functioning system and every time you feel like it you can chroot into LFS and move forward with it.

---

### Post by 1clue on 2012-01-05
When you try these other distros for the first time, especially LFS or Gentoo, just set up a VM to try it on.  Then you always have your current distro fully functional and a completely disposable VM for testing.  It will let you know what the distro in question is about without trashing your current setup.

And then, when you decide to wipe for real, you can copy your VMs to an external drive along with your other files, wipe your drive and when you get it all back you still have all your VMs.

---

### Post by mastablasta on 2012-01-05
> **1clue said:**
> When you try these other distros for the first time, especially LFS or Gentoo, just set up a VM to try it on. Then you always have your current distro fully functional and a completely disposable VM for testing. It will let you know what the distro in question is about without trashing your current setup.
 
And then, when you decide to wipe for real, you can copy your VMs to an external drive along with your other files, wipe your drive and when you get it all back you still have all your VMs.
 
 
does it work good on 2GB ram and (probably) underpowered CPU and GPU?

---

### Post by 1clue on 2012-01-05
What are you going to do with it?

Personally I think that 2g RAM and a small processor isn't worth keeping in my house, but I develop software for a living and need to test on virtual machines.  Most of the VMs I use have less than 1g RAM allocated, but I use them for very limited purposes.  But I often have 2 or more VMs running simultaneously too.

For the most part, unless you actually allocate a CPU core to the VM, it won't suck much from your machine unless you're using it.  Also, if all you're doing is running the VM, then all the host is doing right now is its regularly scheduled background stuff and handling I/O for the guest.  There's a little bit of overhead associated with a VM but not that much.

**Edit:** You're definitely going to see a hit when using a VM from a small machine and small RAM, but it's probably manageable.

---

### Post by corrytonapple on 2012-01-05
I have high doubts a VM would work on that processor.
Full installs are much better, and just as easy really.

---

### Post by 1clue on 2012-01-05
I'm not sure about that processor specifically, but I started virtualization on a P4.  I don't think the OP's hardware is less capable than that.

On the other hand, virtualization has changed a lot since then, there very well could be something preventing modern virtualization from working.

---

### Post by JKyleOKC on 2012-01-06
> **mastablasta said:**
> does it work good on 2GB ram and (probably) underpowered CPU and GPU?I'm running a WinXP VM in VirtualBox 3 on a hyperthreaded P4 with 2 GB of RAM and it seems to be as responsive as a native WinXP installation would be. Of course, the host system is doing nothing except its VM support, most of the time. That installation is devoted to handling my Email and providing support for my photo scanner; I use a different box for everything else, and access the Email VM over my LAN.

I've run VMs on an AMD K6 CPU and 256 MB of RAM, but they were barely usable. With at least 2 GB of RAM and two or more cores, they're quite snappy.

---

### Post by cap10Ibraim on 2012-01-06
I'm currently using Scientific Linux 6.1 
to be honest just because it's based on RedHat Enterprise Linux and built by CERN and FermiLab
the media codecs are preinstalled and it's a very stable system

---

### Post by corrytonapple on 2012-01-06
I say we just wait for the OP to respond back with what he wants to do, and until then just wait.  He'll ask more questions if he needs to.

---

### Post by il_maniscalco on 2012-01-07
> **corrytonapple said:**
> I saw we just wait for the OP to respond back with what he wants to do, and until then just wait.  He'll ask more questions if he needs to.

eh I still don't know;
I'm quite satisfied with my current system (ubuntu 11.10 but using the old de) but I'm not stressing it in any way in the last few days, just some bare office activity and browsing.

One option I'm still considering is Ubuntu Server and a graphic interface of my choice, and also some distribution were quoted here.

At the time I have no further questions...

---

