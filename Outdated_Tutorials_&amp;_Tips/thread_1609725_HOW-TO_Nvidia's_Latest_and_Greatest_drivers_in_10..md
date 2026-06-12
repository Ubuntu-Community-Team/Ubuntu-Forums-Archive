---
title: "HOW-TO: Nvidia's Latest and Greatest drivers in 10.10"
date: 2010-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by cwwilson721 on 2010-10-30
NOTE: In the following post, I substitute '<USER>' for my username. Use whatever you need to.

[SIZE="4"]***Do you have Ubuntu 10.10, with a Nvidia videocard, and want to install the latest drivers from Nvidia?***[/SIZE]

Maybe you have a shiny new 400 series Nvidia card in SLI. Or you need the latest features from Nvidia. Or a game you play is just too slow, and a driver update might fix it.

You look around, and find a solution, but...You're FRUSTRATED because the method you used for the drivers from Nvidia's website either results in:
[LIST]
[*]Low-graphics mode
[*]No X server at all (Just dumps you to a command line)
[*]Won't install because the Nouveau drivers are in the way, and Nvidia's installer fails?
[/LIST]

I was in the same boat earlier, but I figured out a rather simple way to fix these common issues.

Let me give you some background.

[SIZE="4"]***Myself***[/SIZE]

I started using Linux a LONG time ago. My first distro was Slackware 3.1. And I still use Slackware 13.1, almost 10+ years later.
 
I found I needed to figure out how to get 3d acceleration working on videocards/chips, and found that there were a TON of posts/forums/ideas, but they were spread all over the internet.

After alot of research, I put together [this post]("http://www.linuxquestions.org/questions/slackware-14/a-guide-enabling-3d-acceleration-in-x11-402003/") on another forum. So far, it has over 220,000 hits, and over 770 replies (as of October 30, 2010). I guess others are/were in the same boat as me, and appreciated the info in one spot.

[SIZE="4"]***The Other issues***[/SIZE]

I love Ubuntu. The ease of use right out of the box is amazing, and the ease of use after is mind-blowing.

However, with release 10.10, Ubuntu includes the Nouveau driver, which is fine for 2d, and some stuff. The Nvidia driver from their website can't remove this module, and the install fails. But if you want REAL 3d for gaming, etc, you gotta go with the Nvidia proprietary driver.

Ubuntu makes installing this VERY easy, using System > Administration > Additional Drivers, and choose the 'current' driver. You reboot, and you have a Nvidia driver installed.

HOWEVER, it's not the latest and greatest from Nvidia. If you have a newer Nvidia card, or just want the latest driver, it's in the 180 series right now (I think). And the latest from Nvidia is 260.19.12 (As of date of this post).

Trying to install this driver in 10.10, unfortunately, usually results in...Well, NOTHING. No X, no GUI, just a command propt blinking at you. Or, it won't install at all because it chokes on the Nouveau driver.

[SIZE="4"]***Solution***[/SIZE]

A few prerequisites:

[LIST]
[*]Have only one video type card in your system. A SLI setup is fine, but no Video Capture cards or Tuners. Really. It will foul things up BAD. Reinstall those later
[*]Get the latest Nvidia driver from [www.nvidia.com](www.nvidia.com). Go to the drivers section, and fill out the drop-down boxes. It will download the *run file you need.
[*]Remember where this file was saved. Mine, for example, is saved in /home/<USER>/Downloads
[/LIST]
Up to this point, there have been NO changes to your system All is as is was. After this, though, it WILL change. If you have issues, look for appropriate sction near end of post : [COLOR="Blue"]Restoring the system to pre-existing state[/COLOR]

Now, for the fun part:
[LIST]
[*]Install the Ubuntu Nvidia Driver. Really. It helps. And reboot when done.
[*]Next, open a terminal, and type: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.compiz 
```
[/LIST]
Okay? If you've done all that, now it's into the murky world of you NOT having a pretty GUI to look at for a little bit. Why? Because of Nouveau.

You might want to either print out the rest of these instructions, or memorize them, or have another computer with this how-to on it, because you can't read them if you don't have the browser up.
[LIST]
[*]Reboot the computer, and at the grub screen, select 'Repair Mode' for your kernel (If no grub menu, hold the 'space' bar after the Bios Screen. If it boots to Ubuntu GUI, you have to reinstall the Ubuntu Nvidia drivers, the uninstall them again, and try to get to repair)
[*]In the select box, choose "root user session"
[*]When the prompt comes up, type ```
cd /home/<USER>/Downloads
```or wherever you saved the *run file to
[*]Type ```
sh NV*run
``` 
[*]There are many ways this can go from here. If it says "answer 'no' will continue install" then answer 'no'. Otherwise, always select 'yes'
[*]Make sure you select 'yes' if you are using a 64bit driver and 64bit Ubuntu when it asks if you want to install the 32bit compatibility libraries.
[*]Answer 'Yes' for the xorg.conf question
[*]Type ```
mv /etc/X11/xorg.conf /etc/X11/xorg.Nvidia
cp /etc/X11/xorg.compiz /etc/X11/xorg.conf 
```
[/LIST]
Now, reboot, and all should be fine.

You may ask "Why the root prompt"? Because if you allow 'normal boot', the kernel will load the Nouveau driver/module, and you can't install the Nvidia driver.

REMEMBER: YOU MAY HAVE TO REINSTALL THE DRIVER AFTER A KERNEL UPDATE. Just boot to the root user prompt, and rerun the installer. But THIS time, choose 'No' for the xorg.conf setup.

[COLOR="Blue"][SIZE="4"]Restoring the system to pre-existing state[/SIZE][/COLOR]

If the above fails for whatever reason, get back to the root command prompt, cd to the directory you downloaded the *run file to, and type ```
sh *.run --uninstall
```
Reboot, and it should get you to a GUI. Low-graphics mode, maybe, but you can always install the Ubuntu Nvidia Drivers from Additional Hardware.

If you have any questions or issues, please feel free to ask. I check these forums all the time.

---

### Post by Josh1 on 2010-10-31
Hello,

I was having some issues with the latest driver from the nvidia website on my GTX470. I think(?) it's because nVidia deprecated openGL support or something because whenever I would try and run a wine game it would give me grief about direct3d9 or something..

So I installed the latest (260.19 I think?) nVidia drivers supplied by Ubuntu on Maverick abd it worked fine from that point on.

---

### Post by cwwilson721 on 2010-10-31
Maybe I should add this to the main thread:

On Nvidia's site (under Information when you select the driver), it states that soon it will NOT be shipping opengl, or other things (cuda, etc)with their drivers.

I'm not sure if Ubuntu 10.10 has a separate package for it...There IS a nvidia-glx-185, but not sure how that fits in...

However, after doing the steps I outlined above in post #1, and double-checking with glxinfo, I have opengl enabled and running.

```
~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_swap_control, GLX_EXT_texture_from_pixmap, GLX_ARB_create_context, 
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_multisample, 
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:

*Tons more text*

```
So, I don't know what issue you are talking about. opengl is good.

Having D3D issues in wine is a WHOLE 'nother matter. Ask/search the wine forum.

(BTW, WoW uses opengl in wine, and for me, runs faster/smoother than Win7)

Try to install the way I outlined.

---

### Post by Lvcoyote on 2010-10-31
I usually install the restricted drivers from Ubuntu, and afterwards just do it through a PPA.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

Works like a champ every time.....260.19.12 in a flash.....LOL

---

### Post by cwwilson721 on 2010-10-31
Nice to know how to install second-tier packages that are ALMOST Nvidia's latest and greatest. They are NOT 'Nvidia's Latest and Greatest' because the packagers have to wait for Nvidia to put out the drivers, and then package them. Since they are packaged by a third-party, it does not fit into this how-to.

 I, for one, will not install these packages, because I DON'T KNOW THE MAINTAINERS. I do, however, know Nvidia.

But it IS a nice shortcut, for those who wish to do this.

---

### Post by Lvcoyote on 2010-10-31
I agree with the trust issue, but in this particular case it does work very well. As does your method :)

---

### Post by spike_naples on 2010-11-20
> **Lvcoyote said:**
> I usually install the restricted drivers from Ubuntu, and afterwards just do it through a PPA.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
```

Works like a champ every time.....260.19.12 in a flash.....LOL

Hi, I have an ASUS K42JC laptop with Geforce 310M Cuda 1gb graphics and 4gb of RAM. I run on Ububtu 10.10 64-bit.

I was wondering if this "sudoing" of repositories is a failsafe method. I'm really frustrated with the Nvidia drivers as this is my 5th install of the OS in 2 weeks. I just cannot get it right. 

Also, will the 1st post be effective too? 

I'm barely a 3 year old Ubuntu user and am quite happy but with this release I am so frustrated and thinking of switching to Win7.

Hope you could help me or at least assure me that these steps specially the PPA thingie would work. I've Googled too much already and am just desperate.

Although I could survive, what I really want to do is play Regnum Online. Without the drivers I'm helpless. I've tried installing Regnum under Wine but some error prevents me from playing too.

Thanks.

---

### Post by Lvcoyote on 2010-11-20
I've used this method a few times now, worked every time for me so far.  I just used it again yesterday to get the new 260.19.21 drivers as well.  You should probably go to Nvidias's web site and look at the Readme for these drivers and make sure they support the graphics platform in your laptop before attempting to install.

---

### Post by spike_naples on 2010-11-20
> **Lvcoyote said:**
> I've used this method a few times now, worked every time for me so far.  I just used it again yesterday to get the new 260.19.21 drivers as well.  You should probably go to Nvidias's web site and look at the Readme for these drivers and make sure they support the graphics platform in your laptop before attempting to install.

Thanks Coyote. Forgive me for my hesitance and ignorance here too but I have a couple more questions:

1. So I just type those into a terminal and let it take its course?
2. No more terminal screens or printing out of instructions?

If so or anything further, I feel I can be comfortable with what you're saying here. 

I'm just really scared 'cause I got my Ubuntu 10.10 set up the way I want again and it took me alot of pains to get here.

---

### Post by cwwilson721 on 2010-11-20
The 1st post is the way the rest of the Linux World installs Nvidia drivers.

The repo method, tho it works, is NOT the topic of conversation here.

I can install the Nvidia drivers into Windows without the same effort, but this thread is NOT about "How to Install Nvidia's Drivers in Windows", nor is it entitled "How-to install Nvidia's Drivers using repos"

Please, STOP POSTING ABOUT REPOS YOU USE

This is a HOW-TO on Installing the Nvidia Drivers from Nvidia, not from repos

Thank You

---

### Post by Peaches491 on 2010-11-20
so i have a question. 

I'm running 10.10 on a HP laptop with an nVidia 7100m GPU. I recently downloaded the drivers and installed them without using the abive method. 

I usually just go into a virtual console, TTY 2 usually, and stop GDM. then i cd to my .run file and run it. i keep hitting yes until it tells me it worked, and voila, it does. 

i have a;ways had quite a strange problem though. I cannot see any of the virtual terminals! ctrl+alt F1-F6 do nothing. The screen just goes black. Then ctrl+alt F7 brings me back to Gnome. 

Any ideas?

---

### Post by Lvcoyote on 2010-11-20
Didn't mean to rain on your parade here, but the gentleman was merely looking for help as he is obviously new to Linux.  Providing a way past his frustration is all that was attempted.

Carry on.

> **cwwilson721 said:**
> The 1st post is the way the rest of the Linux World installs Nvidia drivers.

The repo method, tho it works, is NOT the topic of conversation here.

I can install the Nvidia drivers into Windows without the same effort, but this thread is NOT about "How to Install Nvidia's Drivers in Windows", nor is it entitled "How-to install Nvidia's Drivers using repos"

Please, STOP POSTING ABOUT REPOS YOU USE

This is a HOW-TO on Installing the Nvidia Drivers from Nvidia, not from repos

Thank You

---

### Post by cwwilson721 on 2010-11-20
I'm just bringing the post back to WHAT IT IS, not hijacked into a "How do I..." general Nvidia driver thread.

If you can't keep to the original topic, and issues WITH the original topic, start your own thread in the appropriate forum.

Now, some explanation about the ORIGINAL THREAD:

The reason I do the install the way I do is because, very soon, Nvidia is going to stop shipping opengl and vdpau with it's binary drivers.

So, installing the way I do, it lets the opengl, etc, still be up-to-date, and I get the fresh Nvidia drivers..Best of both worlds.

---

### Post by spike_naples on 2010-11-21
Thanks for the how-to CWWILSON. Sorry for being off-topic.

---

### Post by DZ* on 2010-11-23
The install script from nvidia.com is not Linux version specific and it supposedly overwrites some system files, or at least did that in the past ([https://www.redhat.com/archives/fedora-devel-list/2006-February/msg01178.html](https://www.redhat.com/archives/fedora-devel-list/2006-February/msg01178.html)). If that is still true, then one can't really "NVIDIA-***.run --uninstall" it properly. It may also mean that future OS upgrades have a potential to break the system.

---

### Post by cwwilson721 on 2010-11-25
> **DZ* said:**
> The install script from nvidia.com is not Linux version specific and it supposedly overwrites some system files, or at least did that in the past ([https://www.[COLOR="Red"]redhat[/COLOR].com/archives/[COLOR="red"]fedora[/COLOR]-devel-list/2006-February/msg01178.html](https://www.[COLOR="Red"]redhat[/COLOR].com/archives/[COLOR="red"]fedora[/COLOR]-devel-list/2006-February/msg01178.html)). If that is still true, then one can't really "NVIDIA-***.run --uninstall" it properly. It may also mean that future OS upgrades have a potential to break the system.Since that applies to the most patched/hacked 'linux' version out there, what do I care? Since this is Ubuntu, written FOR Ubuntu, and checked in Ubuntu, Fedora can rot.

I've done ALL steps as outlined above, and it works. In Ubuntu. And Gentoo. And Slackware. And most REAL linux distros.

Use Fedora/Redhat at your own (and your systems) risk.

---

### Post by DZ* on 2010-11-25
This has nothing to do with Fedora, and problems can occur in Debian/Ubuntu just as easily. Here is one example: 

[http://www.shatters.net/forum/viewtopic.php?f=2&t=13409](http://www.shatters.net/forum/viewtopic.php?f=2&t=13409)

This is also mentioned on Nouveau page:
&#8203;[http://nouveau.freedesktop.org/wiki/InstallNouveau](http://nouveau.freedesktop.org/wiki/InstallNouveau)
and in many other places.

The install script is oblivious to the type of OS on which it is running. This behavior creates a documented issue that system files and/or symlinks may get replaced/changed in the process. Once that happens, it might be impossible for the script to restore the system, for example, by backing up files/symlinks, because these could have changed due to system upgrades by the time you run uninstall.

---

### Post by cwwilson721 on 2010-11-26
Thus, the reasons why and EXACT steps I outlined to begin with.

If you listen to the voices in your head, and do as you wish, why are you reading this HOW-TO anyway?

IF you follow these steps, ALL steps are reversible in Ubuntu

IF you DO NOT, good luck.

---

### Post by OskarV on 2010-11-26
I'm having problems with these drivers

I always end up with:
No X server at all (Just dumps you to a command line)

and need to run Ubuntu in recovery with failure graphics mode.

I've installed the Nvidia drivers through System-admin-Aditional drivers. Had the same problem there.

Then I installed the driver from the Nvidia website. Same problem.

I uninstalled them but Nouveau doesn't work anymore.

So I followed your guide but the problem persists

Any ideas for a solution?

GPU is Nvidia 425M
on a new Asus N43JF laptop.

---

### Post by frankske on 2010-11-27
i have the same gpu sony vaio laptop nvidia 425 m.
the only driver thats work is this wget [http://uk.download.nvidia.com/XFree86/Linux-x86_64/256.53/NVIDIA-Linux-x86_64-256.53.run](http://uk.download.nvidia.com/XFree86/Linux-x86_64/256.53/NVIDIA-Linux-x86_64-256.53.run)
.
is not perfect but its going for now.

---

### Post by crownclown on 2010-12-19
Im using Nvidia Geforce 310M Cuda..
well the additional ask to install the nvidia grafix as it was re***mended.
but after i install it then when reboot.. it only blank screen..
it's been 5 times i format my partition to get back my ubuntu...
is there any way to get this done ?
im still new with ubuntu...:p

---

### Post by cwwilson721 on 2010-12-19
Since you are having issues, I would install the drivers from Ubuntu, from System > Administration > Additional Drivers.

---

### Post by vangop on 2010-12-20
> **cwwilson721 said:**
> Nice to know how to install second-tier packages that are ALMOST Nvidia's latest and greatest. They are NOT 'Nvidia's Latest and Greatest' because the packagers have to wait for Nvidia to put out the drivers, and then package them. Since they are packaged by a third-party, it does not fit into this how-to.

 I, for one, will not install these packages, because I DON'T KNOW THE MAINTAINERS. I do, however, know Nvidia.

But it IS a nice shortcut, for those who wish to do this.

Hi!
I have hp 8440p laptop with
```
$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation GT218 [NVS 3100M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```

I went to the nVidia site and couldn't find the nvs 3100 in the list of models. There's only nvs 300, but on the details page it doesn't list my card.
But if I enable the ppa I can upgrade.
Can you suggest how to find the driver, since I don't know much about the nvidia card families.

---

