---
title: "[SOLVED] Without ethernet and wireless in Ubuntu Studio"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-07-09
Hi,
I just installed Ubuntu Studio on my HP vd9000 Laptop (Core 2 duo Intel 2.7) and I am without these 3 very basic components:

1) No Network Manager to be found
2) No working Ethernet Controller (I have an Intel 82573L or 8257BL Ethernet Controller - '3' or 'B' before the L, I can't tell which)
3) No wireless - Intel/Pro Wireless 3945AGB

These three are so inter-dependent. Usually, I can temporarily connect to the net by ethernet cable with a Lan connection directly to my modem and download all the stuff I need from Synaptic. 

Now I can't even do that. It doesn't work or either there's a setting I'm overlooking.  

I have transferred Deb files for Ndiswrapper 1.52 common and utilities through a flash drive and have installed them, but without Network Manager or the inf file, I'm still stuck. 

I appreciate any help on this. FYI, I did do an install of PCLOS Gnome a while back and used Ndiswrapper successfully for the 3945ABG, but the INF file was loaded as part of that OS.

Many Thanks for any help,...Frank B.

---

### Post by framinglory on 2008-07-09
You can download network manager manually here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
just select your version of ubuntu, and then find the package under network.

As for the wireless, there is a web page about it
[http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

edit: did a little reading, apparently the iwl3945 drivers are included by default in linux kernels at 2.6.24 and above, what is your kernel version?
use 
echo `uname -r` 
in the command line to find out, if you don't know already.

---

### Post by Brightbelt on 2008-07-10
Thanks Framinglory, I'm working on the things you mentioned. I'm having to boot in Vista to do the downloading etc.

Many Thanks, Frank B.

---

### Post by framinglory on 2008-07-10
glad to help! I don't know a whole lot about installing new kernels, but from the looks of it you just need to download the linux-i386 (assuming you're on an x86 system, not an x64) package, and the two dependencies listed for it and install the packages. Unfortunately i'm going on a trip tomorrow and won't be back for 5 days or so, so hopefully things go smoothly, but if not, i'm sure someone else can inform you how to get the kernel working and all. good luck!

edit: found a web page with an article about installing a kernel in ubuntu,
[http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_kernel](http://beginlinux.com/index.php/desktop_training/ubuntu/ubfile_m/ub_kernel)
it assumes you have internet and all that, so not too useful to follow, but does show what packages you need and all. looks like what i said earlier in this post is right, just install the dependencies listed on the packages.ubuntu page, the kernel itself, reboot, and it should be in the 2.6.24 kernel. use echo `uname -r` to confirm this. also, (i just found this out a bit ago) the little tick marks around uname, they're the tick marks located on the key usually next to the 1 key, that has a tilde when holding shift (~).

---

### Post by Brightbelt on 2008-07-10
It's a little confusing finding the dependencies - one I know already because it got spouted out to me in Ubuntu...So I had to go back to Vista, blah blah blah.

It'll work hopefully. Thanks again, Frank B.

---

### Post by framinglory on 2008-07-10
yeah it is a little confusing at first. When you click on a package name from the list, you should get a new page that has a key at the top, and a list of new packages below it. All of those packages with a red circle next to their name are dependencies, you'll want to download and install those.
I attached a picture with the dependencies of a package highlighted, if that helps at all.

---

### Post by Brightbelt on 2008-07-10
Again, Thanks! It's late and I'm tired and I wasn't noticing the red-dot system. 
  Thanks, Frank B.

---

### Post by framinglory on 2008-07-10
glad to help! :)
as for the wired ethernet controller, a quick google search seems to appear that it is 82573L.
[http://hardware4linux.info/component/14239](http://hardware4linux.info/component/14239) - that is a page with information about the hardware related to linux, says the module required is e1000.
[http://hardware4linux.info/module/e1000/](http://hardware4linux.info/module/e1000/) -that is the page about e1000
 Type lsmod | grep "e1000"
into a terminal to see if it is loaded. If it is, it will show up. If not, nothing will happen. If it does not show up, try modprobe e1000 . It seems from a few searches that e1000 is installed by default, but not necessary loaded, but if you get an error about it not existing, here is a link to the source-
[http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835&release_id=611169](http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835&release_id=611169)
and finally, here is a slightly older page about trying to install e1000 module, it may be of some use-
[http://ubuntuforums.org/showthread.php?t=171790](http://ubuntuforums.org/showthread.php?t=171790)

---

### Post by Brightbelt on 2008-07-10
[Warning: RANT FOLLOWS] Wow. Not to sound like a jerk, but this is crazy - it's a Christmas tree full of dependencies,...just for (1) one program.

To install all of these, I'd have to cover my Vista desktop just to download all of them. 

I know we're here to learn and I'm not afraid of the command line either, but this is where I think Linux sometimes falls short.

If my Synaptic were working and I could install this program with one choice in Synaptic, with Synaptic handling all the dependencies for me, I'd do it. 

So why should anyone have to go online and sift through several pages of dependencies and have to download 12+ individual Deb programs just because they can't use Synaptic ? 

Of course they recommend using Synaptic in these pages and if I were online in Ubuntu Studio I would. [End RANT]

I'll see if I have the time later to do all those dependencies.

Many Thanks for helping,...Frank B.

---

### Post by framinglory on 2008-07-10
are you talking about dependencies for the network manager? I'm sorry, I didn't realize it had so many! I noticed you made another thread about downloading just the program from synaptic and not installing it. If you download them that way, check to make sure it gets all the dependencies you really need (as if there are already installed dependencies i don't think it reinstalls them)

If you get the kernel working first, you can use the wireless from the commandline, this guide [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking) provides a way to have it connect to your wireless automatically through the /etc/network/interfaces. 

This guide (it's for arch linux, but the wireless tools commands are still the same) will show you how to use the command to tell your wireless card what to connect to
[http://wiki.archlinux.org/index.php/Wireless#wireless_tools](http://wiki.archlinux.org/index.php/Wireless#wireless_tools)

Edit: you could also try what i mentioned above to get your wired ethernet working, and then install network manager that way, if you want to avoid trying to set your wireless through the command line

Unfortunately I have to go now, and won't be able to check the forums for about 5 days or so. Hopefully you get everything working, and, if not, i'm sure someone else around will help you. If things still aren't working by early next week feel free to send me a private message, and i'll see what i can do, but things should be working way before then. Good luck!

---

### Post by Brightbelt on 2008-07-10
Many Thanks Framinglory for all your help. I made a decision to go back to regular Ubuntu (Not Studio) because everything pretty much works there. 

I do plan to experiment more with digital audio recording in Linux but I can install what I need in regular Ubuntu. My wireless works there right out of the box. 

I see how much wisdom there is now in the 2 applications rule: "If 2 or more applications/systems don't work, you may need to try a different distro."

Again, I appreciate all the attention you gave to this. Referring to the other thread, I did burn a CD of archived Deb downloads (including Network Manager) and installed them, but I ended up with broken packages among other things...

That may have been due to other things I had already tried to install or bits of network manager already floating around in my system. 

It began to feel so complicated to solve all that mess that I threw my hands up in surrender.

Again, Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-07-11
Well, it seems I found a back-handed solution to ALL of this!! Quite by accident really. 

As I implied above, I went ahead and installed regular Ubuntu and everything works: sound, wireless, ethernet etc. Then I thought 'What if I upgrade to Studio from within Hardy - I might be able to keep all the working parts'. 

What I did was discover that ALL of the Ubuntu Studio applications are available from the Synaptic Package Manager - just search 'Ubuntu Studio' and all the apps are there, listed like  'ubuntu-studio-audio', 'ubuntu-studio-video' etc. 

So I have everything installed that I need AND I still have all the original Ubuntu functionality: wireless that works, ethernet, graphics, etc. 

From reading other posts about this, I've read that some systems will hold together fine through this install, but some systems won't. This means that on another system, one might possibly inherit all the same old Studio problems again.

Many Thanks, Frank B.

---

