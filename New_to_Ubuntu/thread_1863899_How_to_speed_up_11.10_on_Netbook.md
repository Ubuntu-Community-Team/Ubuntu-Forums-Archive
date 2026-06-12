---
title: "How to speed up 11.10 on Netbook?"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by franklin_m on 2011-10-18
Hello,

Ever since I upgraded to 11.10 on my Dell Inspiron Mini 10V, Ubuntu has become exceedingly slow. Symptoms include:

- When right click item on panel at left, trash for example, to bring up empty trash option, when clicked on it nothing happens. Have to select it a second time, exact same process, before it works and empties trash. Not limited to trash, similar performance with other menus.

- Much slower than 10.xxx at opening windows and software of all types.

What stuff can I do to fix / increase performance?

Thanks

---

### Post by decoherence on 2011-10-18
Someone please correct me if I'm wrong, but if you went from 10.x to 11.10, then I think you've switched from classic gnome to unity.

Unity tries to make use of your graphics hardware to accelerate user interface elements. Most netbooks have weak graphics so this attempt at providing accelerated graphics might actually be slowing you down. You might have better luck using the classic gnome session (if that option is still available?) or Unity 2D (which I found was still slow... haven't used it lately, though) or switching to another desktop (openbox plus some kind of taskbar works well but requires a bit of know-how to set up.)

Disclaimer: I do not run Ubuntu anymore and all information is from memory.

---

### Post by 2F4U on 2011-10-18
> **decoherence said:**
> Someone please correct me if I'm wrong, but if you went from 10.x to 11.10, then I think you've switched from classic gnome to unity.

Unity tries to make use of your graphics hardware to accelerate user interface elements. Most netbooks have weak graphics so this attempt at providing accelerated graphics might actually be slowing you down. You might have better luck using the classic gnome session (if that option is still available?) or Unity 2D (which I found was still slow... haven't used it lately, though) or switching to another desktop (openbox plus some kind of taskbar works well but requires a bit of know-how to set up.)

Disclaimer: I do not run Ubuntu anymore and all information is from memory.

I think you are totally right. Ubuntu is not really suited for "underpowered" hardware and that is the reason why the netbook is slow (without knowing the hardware). I would suggest that the OP tries a different flavour of Ubuntu such as Xubuntu or Lubuntu.

---

### Post by amjjawad on 2011-10-18
The question must be: How to choose a better alternative that runs natively faster than Ubuntu 11.10? :)

I have many other alternatives for you but I'll through in your way what I'm using right now. One word. Lubuntu, period.

:)

---

### Post by decoherence on 2011-10-18
> **amjjawad said:**
> The question must be: How to choose a better alternative that runs natively faster than Ubuntu 11.10? :)

I have many other alternatives for you but I'll through in your way what I'm using right now. One word. Lubuntu, period.

:)

yeah, if i wanted to use ubuntu on a netbook, i'd probably go with lubuntu as well.

archbang runs really nicely on a netbook -- you can even enable compositing (cairo-compmgr) and it's still reasonably speedy.

---

### Post by decoherence on 2011-10-18
> **2F4U said:**
> I think you are totally right. Ubuntu is not really suited for "underpowered" hardware

I seem to recall that Unity was originally intended as a netbook interface? Wasn't the package 'ubuntu-netbook' or something at some point?

Well, anyway. Things change, obviously ;)

---

### Post by amjjawad on 2011-10-18
> **decoherence said:**
> yeah, if i wanted to use ubuntu on a netbook, i'd probably go with lubuntu as well.

archbang runs really nicely on a netbook -- you can even enable compositing (cairo-compmgr) and it's still reasonably speedy.

Hi :)

Sad but true. Everyone is looking at the latest hardware and it seems everyone is forgetting one simple fact that there are lots of old hardware which are "still" very much up and running, just need the right software to run it.

Luckily, there is Lubuntu and some other lightweight distributions but the other question is: for how long?

Never tried Arachbang but I do have it here with my CDs (I guess I have downloaded over 50 distros).

It happened once that I was looking for a distro which is independent and not based on Ubuntu. I found some nice stuff like antiX and SliTaz but the lack of GRUB2 support made me go some other direction.

I'm in love with lightweight Distros.

---

### Post by amjjawad on 2011-10-18
> **decoherence said:**
> I seem to recall that Unity was originally intended as a netbook interface? Wasn't the package 'ubuntu-netbook' or something at some point?

Well, anyway. Things change, obviously ;)

You are absolutely right. That was just the beginning. The beginning of the end :P

---

### Post by decoherence on 2011-10-20
> **amjjawad said:**
> Hi :)

Sad but true. Everyone is looking at the latest hardware and it seems everyone is forgetting one simple fact that there are lots of old hardware which are "still" very much up and running, just need the right software to run it.

Luckily, there is Lubuntu and some other lightweight distributions but the other question is: for how long?

Never tried Arachbang but I do have it here with my CDs (I guess I have downloaded over 50 distros).

It happened once that I was looking for a distro which is independent and not based on Ubuntu. I found some nice stuff like antiX and SliTaz but the lack of GRUB2 support made me go some other direction.

I'm in love with lightweight Distros.

Me too! I wouldn't worry about them disappearing. As long as there is old hardware, someone will do a distro.

---

### Post by amjjawad on 2011-10-20
> **decoherence said:**
> As long as there is old hardware, someone will do a distro.

I really do hope that :)

---

### Post by wolfen69 on 2011-10-20
I suggest Lubuntu for a netbook. Much lighter and quicker.

---

### Post by dilantha2 on 2011-11-21
Sorry for disturbing all... My laptop has,

1Gb Ram DDR2, 
nVedia seperate VGA 512Mb, 
1.66Ghz core 2 duo processor,

it's getting crazily slow when I run my web browser and other apps. I have worked with old ubuntu editions(9.4, 9.10,10.4) well by using my Pentium 4 PC. I'm really worried about latest releases (10.10, 11.04, 11.10) 

please leave me ur ideas ... Thankx !!!

---

### Post by dFlyer on 2011-11-21
> **dilantha2 said:**
> Sorry for disturbing all... My laptop has,

1Gb Ram DDR2, 
nVedia seperate VGA 512Mb, 
1.66Ghz core 2 duo processor,

it's getting crazily slow when I run my web browser and other apps. I have worked with old ubuntu editions(9.4, 9.10,10.4) well by using my Pentium 4 PC. I'm really worried about latest releases (10.10, 11.04, 11.10) 

please leave me ur ideas ... Thankx !!!

Try installing more ram.

---

### Post by wolfen69 on 2011-11-21
> **dilantha2 said:**
> Sorry for disturbing all... My laptop has,

1Gb Ram DDR2, 
nVedia seperate VGA 512Mb, 
1.66Ghz core 2 duo processor,

it's getting crazily slow when I run my web browser and other apps. I have worked with old ubuntu editions(9.4, 9.10,10.4) well by using my Pentium 4 PC. I'm really worried about latest releases (10.10, 11.04, 11.10) 

please leave me ur ideas ... Thankx !!!

Lubuntu. I know it's almost cliche now, but it really does work well on "underpowered" machines. At least from *my* experience it does.

---

### Post by mikewhatever on 2011-11-21
Having tried Lubuntu on a notebook recently, I'd have to advise against it. Why? Well, in my case, these were the problems:

- the screen would dim, but not go off.
- the touchpad didn't work
- none of the volume, brightness, etc keys worked
- pressing the power button didn't do anything

Lubuntu would be a very good choice for an old desktop computer, but for a netbook, I'd suggest Ubuntu 11.10 with Unity-2d or 10.04 Netbook Remix.

---

### Post by Jacobonbuntu on 2011-11-22
.... I use Ubuntu on my desktops, tried Lubuntu on my netbook, but found it too "skinny" and a lot did not work well, as Mikewhatever said, Xubuntu works perfectly, and in my case definitely not slower than Lubuntu.

---

### Post by cariboo on 2011-11-22
The op can also install gnome-session-fallback, and have the classic two panel interface. Check out the gnome classic thread [here]("http://ubuntuforums.org/showthread.php?t=1873765").

---

### Post by viperdvman on 2011-11-22
back to what the OP was posting... well, if you're running the older Intel Atom N270 and 1GB RAM, you probably have the weaker Intel GMA graphics, Ubuntu with Unity is probably going to run slower. Now my netbook (an AMD Nile V105 with 2GB RAM and ATI Radeon HD 4250) runs Unity very well due to my slightly stronger CPU and much more powerful graphics [SIZE=1]*(Only the dual-core Atoms with NVidia ION 2 are better... and the dual-core C-series and E-series AMD's)*[/SIZE]. I don't know about the newer Intel Atom N450/455's with the Intel GMA 3150's, but I know they're more powerful than the ones typically running with the older N270's, but still. You could always look around on these forums for testimonials from people who run those netbooks. 

Either way, if you're running 1GB of RAM, it's always recommended that you replace it with a 2GB chip. That'll make any OS you're running on it that much better to run. RAM aside, I too agree with the others and say this: Try either Xubuntu or Lubuntu as they both run great on single-core Intel Atoms.

---

### Post by mastablasta on 2011-11-22
> **dilantha2 said:**
> Sorry for disturbing all... My laptop has,
 
1Gb Ram DDR2, 
nVedia seperate VGA 512Mb, 
1.66Ghz core 2 duo processor,
 
it's getting crazily slow when I run my web browser and other apps. I have worked with old ubuntu editions(9.4, 9.10,10.4) well by using my Pentium 4 PC. I'm really worried about latest releases (10.10, 11.04, 11.10) 
 
please leave me ur ideas ... Thankx !!!
 
Kubuntu has a netbook plasma desktop as well (that is if you have a netbook and like these interfaces) I am not sure how much resources it uses as i never tried it but latest Kubuntu comes with low-fat package that can reduce the resources used even more.
 
I am running Kubuntu 10.10 with updated KDE on 1.3GB ram, old ATI 256 MB graphics card and cheap celeron E3300. It runs fine. 
 
You could also give Xubuntu a try. It will use about 130MB ram when idle (possibly less) and should give the old Gnome2.3 feel, but a bit improved. Latest versions came out really good. 10.04 LTS used a bit too much RAM.

---

### Post by I2k4 on 2011-11-22
Microsoft is going nuts because people won't move off XP, which runs better on netbooks and older systems than W7.  I'm wondering if Ubuntu 11.x is going through a "Vista phase" after developing an OS for looks and "friendliness" rather than reliable function and snappy performance.  I'm thinking 11.x may be one of those "disposable" iterations that one remembers as a failure.  (I also tried the Ubuntu 10.10 Netbook Unity and it ran like molasses.)  

When it came to installing on my little Acer netbook, after trying several of the 11.x series including Lubuntu, I went with Lubuntu 10.10 as an OS that feels "finished", runs very slickly, and is not part of this experimental next move.  I'll sit back with it and hope that by 13.x of so it will be time to move on.  

I'm also very impressed with Mint 10.10, which I learned about a little late - for my personal preferences, it's just as refined an OS, and better than Lubuntu for not preinstalling a lot of stuff I want to uninstall, to then install what I do want.

---

### Post by Paqman on 2011-11-22
> **mikewhatever said:**
> for a netbook, I'd suggest Ubuntu 11.10 with Unity-2d

+1

I run it on my old Eee PC, and it works very well.

---

### Post by viperdvman on 2011-11-24
I'm running Ubuntu 11.10 with Unity 3D on my EeePC *(the aforementioned AMD V105 w/ ATI Radeon HD 4250)* and it's running pretty flawlessly. Then again I'm running 2GB RAM and a powerful graphics chip. Not sure how it'd run on a single-core Atom w/ Intel GMA 3150 graphics.

---

### Post by amjjawad on 2011-11-27
> **dilantha2 said:**
> Sorry for disturbing all... My laptop has,

1Gb Ram DDR2, 
nVedia seperate VGA 512Mb, 
1.66Ghz core 2 duo processor,

it's getting crazily slow when I run my web browser and other apps. I have worked with old ubuntu editions(9.4, 9.10,10.4) well by using my Pentium 4 PC. I'm really worried about latest releases (10.10, 11.04, 11.10) 

please leave me ur ideas ... Thankx !!!

Hello and Welcome to Ubuntu Forum :)

It's recommended to start a new thread but it's ok.

Absolutely NO need to upgrade your Hardware and NO need to use OLD releases. There are 700 Linux Distributions, some are still active and some are not. I have tried many. I liked some and disliked the others. Out of all what I have tried, I recommend to use Lubuntu. However, you need to understand that Lubuntu may not be the best/prefect choice for you. For me, it's the prefect choice. I use it on P4 with 242MB RAM, P4 with 2GB RAM and Lenovo Core i5 2nd generation with 4GB RAM. Work perfectly like me.

For anything related to Lubuntu, please have a look here:
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Same link in my signature - Lubuntu One Stop Thread.

---

### Post by amjjawad on 2011-11-27
> **viperdvman said:**
> if you're running 1GB of RAM, it's always recommended that you replace it with a 2GB chip. 

> **Unused** RAM is wasted RAM.I read that somewhere in Arch's Website and I do love it :)

---

### Post by amjjawad on 2011-11-27
> **I2k4 said:**
> I'm also very impressed with Mint 10.10, which I learned about a little late - for my personal preferences, it's just as refined an OS, **and better than Lubuntu for not preinstalling a lot of stuff I want to uninstall, to then install what I do want**.

I'm afraid I didn't understand what do you mean?

Just for the record, Linux Mint LXDE is not lighter than Lubuntu. I'm writing that from experience.

---

### Post by balint777 on 2012-01-10
Im using unity3d on low a low specs netbook (1,6 atom, intel-gma), it actually is much faster than unity2d. Some tweaks i have figured out:
1. Install ccsm and disable v-syncing at opengl properties. It makes the interface render noticably faster.
2. Also you could set texture quality to low. It affects basically just the quality of exposé, but makes unity faster overall.
3. Type "top" into the shell and check for any buggy services. (I had upstart-udev-bridge running at 100% which turned out to have a workaround)

Luck!

---

### Post by QIII on 2012-01-10
Enlightenment 17 is a brilliantly light and fast DE.

---

### Post by m.alaa8 on 2012-01-19
Give gnome-shell a try
I've installed it on my Acer Aspire One and it's much faster than Unity

---

