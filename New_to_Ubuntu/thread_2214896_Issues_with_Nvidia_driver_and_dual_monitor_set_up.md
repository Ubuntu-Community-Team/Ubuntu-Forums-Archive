---
title: "Issues with Nvidia driver and dual monitor set up"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by JesseJones on 2014-04-03
I just installed Ubuntu 13.10 on my Lenovo Thinkpad T530.

Under Settings-->Details it states the Graphics device as Intel Ivybridge Mobil. I know my computer has an Nvidia card, I think it might be optimus. The problem I'm having is that my second monitor isn't working, after freshly installing Ubuntu the 2nd screen worked ut had some major issues with freezing and lag. I tried to find a solution via google and came across bumblebee, after installing bumblebee my computer stopped detecting my 2nd monitor at all and it still says Intel Ivybridge under System-->Details.

From what I understand there is an ongoing issues with Nvidia proprietary drivers. I really have tried my best to resolve the issue on my own. Following guides like this one: [http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/](http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/) however I was only able to get to:

wget [https://raw.github.com/liskin/patches/master/hacks/xserver-xorg-video-intel-2.18.0_virtual_crtc.patch](https://raw.github.com/liskin/patches/master/hacks/xserver-xorg-video-intel-2.18.0_virtual_crtc.patch)
patch -p1 < xserver-xorg-video-intel-2.18.0_virtual_crtc.patch

Before I got the error that the patch didn't exist and the next line just did nothing: sudo dpkg --install xserver-xorg-video-intel_2.17.0-1ubuntu4_amd64.deb  #(again, tab to autocomplete will let you avoid typing this long name)

I know I need to get the Nvida drivers however I've read a lot of reports where installing the Nvidia drivers breaks the Ubuntu Installation. 

Is there anyone who has had experience dealing with this issue that can walk me through getting my video drivers & 2nd monitor working?

---

### Post by 23dornot23d on 2014-04-03
We can try to get a little more information together that might lead to a better chance of setting it up ......

try this in a terminal to start with and post back what you get ........

> 
lspci -vmk | grep -A 8 -B 2 VGA




Also this may help to see if anything is already in place .......

> 
locate nvidia | grep ko



---

### Post by JesseJones on 2014-04-03
Device:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	3rd Gen Core processor Graphics Controller
SVendor:	Lenovo
SDevice:	Device 21f5
Rev:	09
Driver:	i915

Device:	00:14.0
--

Device:	01:00.0
Class:	VGA compatible controller
Vendor:	NVIDIA Corporation
Device:	GF108M [NVS 5400M]
Rev:	ff
ProgIf:	ff

Device:	02:00.0
Class:	System peripheral
Vendor:	Ricoh Co Ltd


---------------------------------------------------------------------------------------------------------------------------

/lib/modules/3.11.0-12-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
/lib/modules/3.11.0-12-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-18-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
/lib/modules/3.11.0-18-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.11.0-18-generic/updates/dkms/nvidia_304.ko
/var/lib/dkms/nvidia-304/304.88/3.11.0-18-generic/x86_64/module/nvidia_304.ko
/var/lib/dkms/nvidia-304/304.88/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia-304/304.88/build/nvidia.ko

---

### Post by 23dornot23d on 2014-04-03
The instructions that you followed were for 12.04 ......

> 
For guaranteed success, you should follow these instructions to the  letter. I&#8217;ve been able to successfully perform them multiple times on a  clean install of 12.04 x64 on my W520.


Things seem to have changed a little in 13.10 ......... but someone with the same setup as you that has solved this may be better than my own solutions

Which were for a Asus computer with optimus ..... but my routine is very similar to the one in the thread you followed .......

The first thing is to get some information into this thread to give some background on what we have here ........... then people can see if they have
similar setups ....... or people can do more searches for specific things .......

Hope this helps to get the thread moving - but I doubt my own solution would work for your setup reading the other threads - you may be able to
go into a different mode from the BIOS ..... discrete mode .......... but I know little about this as my computer does not seem to allow it.

Could see what else you can find out by using this command - which is used to check for Unity compatibility .... but may return some other useful information
for others to check out ..... as I found this link - but it reports back laggy graphics [http://askubuntu.com/questions/368541/laggy-graphics-after-upgrade-to-ubuntu-13-10](http://askubuntu.com/questions/368541/laggy-graphics-after-upgrade-to-ubuntu-13-10)

> 
**/usr/lib/nux/unity_support_test -p**


Did some more searching here - [https://www.google.co.uk/search?client=ubuntu&channel=fs&q=discrete+mode+t350+optimus&ie=utf-8&q=ubuntu+13.10+solved+discrete+mode+optimus](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=discrete+mode+t350+optimus&ie=utf-8&q=ubuntu+13.10+solved+discrete+mode+optimus)

---

### Post by JesseJones on 2014-04-03
Thanks for your time and help. I ran the command /usr/lib/nux/unity_support_test -p

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 9.2.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

I am running Gnome 3 as I don't care much for unity, if that makes any difference.

---

### Post by 23dornot23d on 2014-04-03
Have you tried running Nvidia-settings ?

if its not installed just do

**sudo apt-get install nvidia-settings**

Then run it .... its a graphical interface - but will only run if the nvidia drivers are installed and working.

if they are not - then bumblebee may need to be removed.

maybe you just need to run that and then set the xorg,conf from it .......... once the monitors are set up
and the xorg.conf saved ......... ( you probably only then need to go into discrete mode ) which will just use
the Nvidia graphics .......... just a thought .

Thing is if you end up at a black screen - do you know how to get to a terminal from it ..........
( as we may then need to remove bumblebee ......... and try to reboot again ......... )

options - but I do not want to leave you without a GUI .... 

Let me know if you are ok trying things out ......... as this is new ground .

List of things needed to be in place

__________________________________________________________________

From here is the routine to do it ......... but maybe print it off first ...........

( if anyone else is monitoring this thread - check it out too ) seems good to me ...
_________________________________________________________________


The nvidia drivers ... which you have already shown are in place
The discrete mode - which from what I can tell only uses the nvidia-graphics chip 
( the discrete part makes the computer ignore the intel chip from what I have read )

The bumblebee driver will be taking control at the moment though .... as the kernel is set to load it in
as far as I know - removing it will return control back to the nvidia module you have installed

sudo apt-get remove bumblebee

A reboot after removing bumblebee should let it boot into nvidia only ..... but your BIOS needs to be
altered to discrete - which may be a key press at boot to go into your setup screen to set this up.

Seems complicated but its not ......... as long as you do not end up with a black screen .... which
I think the second boot option will allow to go into low res graphics as a choice should it fail .....


(Then if it does to get back just re-install bumblebee again .... and you are back to where you started.)

sudo apt-get install bumblebee

But if it works then we should be able to run nvidia-settings and create a xorg.conf that works for both
monitors.

Now is also the time to choose if a better nvidia driver is available for your setup.

Upto you ...... we will be the only people to have succeeded looking at the solved cases on the web for this one.

This one seems to be saying they got it all working alright ..... when you read down the thread ............ askubuntu
But it was 2012 Feb - so its probably using 12.04 ....... which is the same thing I keep finding ... the older system
seems to work better ........ yet you would think they would have improved the drivers over time .....

[http://askubuntu.com/questions/107742/no-3d-support-on-lenovo-w520-with-nvidia-optimus](http://askubuntu.com/questions/107742/no-3d-support-on-lenovo-w520-with-nvidia-optimus)

Let me know if you get the Nvidia-settings screen to show up ........... and if possible post a screen shot of what
you see .........



Just seen that they have added the additional drivers again in 14.04 .... so it gives me hope ..... ( another 14 or so days and 14.04 is out ) 17 April
maybe some things with Monitors and Graphics will clear up then

[IMG]http://i.minus.com/ibv5lH3CddMoru.png[/IMG]



 ( Minus - is a good place to upload pics / screenshots to ) ..... [http://minus.com/](http://minus.com/)

---

