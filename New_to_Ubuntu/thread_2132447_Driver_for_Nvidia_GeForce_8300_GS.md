---
title: "Driver for Nvidia GeForce 8300 GS"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by Crossbow on 2013-04-04
I&#8217;ve been doing searches on &#8220;how to install a driver&#8221; but maybe what I&#8217;ve found just isn&#8217;t dumbed down enough for me. They seem to all assume the desired driver is an option in my Nvidia settings or in my package manager. 

After an Ubuntu update last November, I could no longer get the right resolution on my computer. I changed my driver from nvidia-current to nvidia-173, and that solved the problem, but then I couldn&#8217;t play &#8220;World of Warcraft.&#8221; Been working on that for months with no hope in sight in the &#8220;HOWTO: WoW with Wine&#8221; thread, so I finally GAVE UP and canceled my account... But I still want to know what the heck is going on with my driver! 

I was told that 173 is for an older GeForce, whatever that means. My graphics processor is **GeForce 8300 GS**. I went to Nvidia and it told me to download this: 
[B]
Linux Display Driver - x86[/B]
Version: 310.40 Certified

It downloaded to my home folder. I don&#8217;t know if that is where it should be but it didn&#8217;t give me options. 

So I have that... now what do I do with it? it is a .run file but nothing happens when I just try to run it. When I run it in terminal it says I need to be logged in as root but I don&#8217;t know what command to use. I don&#8217;t know much. Apt-get install NVIDIA-Linux-x86-310.40 , or NVIDIA-X86-310.40, or NVIDIA-86 all have the same result: 

```

E: Unable to locate package NVIDIA-Linux-x86-310.40
E: Couldn't find any package by regex 'NVIDIA-Linux-x86-310.40'

```

Synaptic doesn&#8217;t see it; maybe I don&#8217;t know how to look. 

Here&#8217;s what I&#8217;ve got right now: 

```
anna@anna-desktop:~$ lsmod | grep -i nvidia
nvidia               7098356  24 

anna@anna-desktop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86 [GeForce 8300 GS] [10de:0423] (rev a1)
	Subsystem: NVIDIA Corporation Device [10de:0494]
	Kernel driver in use: nvidia

```

And another odd little thing is that it sometimes seems to come &#8220;unstuck&#8221;. When I do this: 

```
anna@anna-desktop:~$ glxinfo | grep rendering
direct rendering: Yes

```

half the time it says no. I don&#8217;t know what that means or how important it is. I know it's needed for gaming but not what else if anything. Mainly the fact that it sometimes says "no" until I reinstall 173 tells me something just isn't right here.

---

### Post by MoebusNet on 2013-04-05
i think you misunderstood which NVidia driver you needed. It appears the 173 driver is the one for your video card:

[http://www.nvidia.com/object/linux-display-ia32-173.14.31-driver](http://www.nvidia.com/object/linux-display-ia32-173.14.31-driver)

Look under the 'supported products' tab.

As far as the WOW issue, it may have more to do with WINE, not the video driver. Maybe the 'Gaming' forum would have advice.

EDIT: I gave you bad advice (sorry). The 8300GS card is listed as supported for the 310.40 driver. Apologies.

---

### Post by monkeybrain2012 on 2013-04-05
You can install the driver from the repository (say from synaptic) If you version of Ubuntui is before 12.10, you can install it by clicking "Additional Driver" if it doesn't popup itself to offer you a driver.

For 12.10 I think there is a tab in synaptic under Settings > Repository though I think "additional driver" is better because it alerts you when such drivers are availiable.

P.S. If you need "dumbing down" instructions I suggest you install from the repository instead of doing it manually from Nvidia download.

---

### Post by bogan on 2013-04-05
Hi!, **Crossbow**,

First, you do not need the nvidia-173 legacy driver, that is for video cards prior to the 6xxx series, but you need to remove it before installing the correct 304 or 310 driver.

If you want to use the NVIDIA.com downloaded driver do the following: Press 'Ctrl+Alt+F1' to get to a tty terminal prompt, login and enter password.```
sudo apt-get update # enter you password
sudo apt-get remove --purge nvidia-173
sudo apt-get remove --purge nvidia*
sudo apt-get install linux-headers-generic
uname -r # enter the output in the following CMD
sudo apt-get install linux-headers-'uname -i' # eg:".....linux-headers-3.5.0.27-generic"
sudo apt-get install dkms
cd /home/username/Downloads # or to whereever the nvidia file is downloaded
ls # this will check you are in the right place & you can check the correct filename
sudo service lightdm stop # to shut down the Xserver
sudo sh NVIDIA-Linux-x86-310.40.run --dkms
```You will probably get a 'Script falled' message and possibly other warnings, accept the offered continue path; navigate with the 'Tab' or arrow keys.
Then reboot.

If you need to return to the GUI, 'Ctrl+Alt+F7' will do that. 

If you need more detailed instructions see:[http://ubuntuforums.org/showthread.php?t=1743535&page=6](http://ubuntuforums.org/showthread.php?t=1743535&page=6) Post #1126
Or just ask.

Chao!, **bogan**.

---

### Post by Crossbow on 2013-04-05
Thanks guys! I will try purging 173 tomorrow. I don't know how I missed that "HOWTO" thread, since it seems to be tagged with everything I searched on. 

I have been trying to do this through synaptic, but there is no additional driver option in the repositories. 

Yes, 173 does work well enough for most things but there's something just not right about it or it wouldn't keep coming "unstuck." That's what I call it; I don't know what is technically happening. 

I'm pretty sure my gaming issue isn't a Wine problem because it started after an Nvidia change, not a Wine change. However, I did start my quest on "WoW with Wine" thread ([http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)) and they have not been able to help me, other than to tell me I've got the wrong driver. Hoefully, that is all I need.

Oh, and when I try to start the game I am booted all the way out to the OS login screen, and from what I've been able to find out through the magic of Google, that is definitely a driver problem.

---

### Post by monkeybrain2012 on 2013-04-05
> **Crossbow said:**
> 
I have been trying to do this through synaptic, but there is no additional driver option in the repositories. 

.

It should be already installed if you are on a version earlier than 12.10. Anyway if you already know the driver version you can just download in from the repository using synaptic (search for Nvidia 173, e.g)

---

### Post by Crossbow on 2013-04-07
> **monkeybrain2012 said:**
> It should be already installed if you are on a version earlier than 12.10. Anyway if you already know the driver version you can just download in from the repository using synaptic (search for Nvidia 173, e.g)

As I said i my original post, I have already download it it, I just can't install it. As I said in my reply to your post, it is not in the repository.

---

### Post by Crossbow on 2013-04-07
**Bogan,** can you advise me? 

Got this far:

```
sudo service lightdm stop # to shut down the Xserver
```

Now I've got the message, "Starting Timidity**ALSA midi emulation" and [OK]... then nothing.  I can't type anything in. Am I waiting for something?

PS. Tried rebooting and starting over. Same thing happened.

---

### Post by bogan on 2013-04-07
Hi!, **Crossbow,**

I am afraid I have no experience with Timidity or ALSA, I only know they are Sound/Audio programs. In any case as the message says [OK], it is probably the next thing that is causing the hang up.

One possibility is that you had an NVIDIA audio driver installed and it was deleted by: 'sudo apt-get remove --purge nvidia*' but it would be reinstalled on rebooting.

Did it give any response to 'Ctl+Alt+F7' or '...+ F1-6' ? or to other keystrokes ?

What happened when you rebooted after that ?

I would try rebooting, if you get to the GUI Log-in, do not login but:
**[ *X*] **Press: 'Ctl+Alt+F1' and login there: ```
cd /home/username/Downloads # or to Desktop or wherever the nvidia file is downloaded 
ls # this will check you are in the right place & you can check the correct filename
sudo service lightdm stop # to shut down the Xserver 
sudo sh NVIDIA-Linux-x86-310.40.run --dkms
```If that does not work: 
reboot to the Grub Menu,
 highlight the Ubuntu entry, 
press 'e' to get to edit script mode, 
scroll to the line that starts: "linux /boot", and 
across to " ro quiet splash" and 
change it to read " rw single text " and 
Press 'Ctrl+x' # to boot to a tty login prompt # note last messages if it hangs
login& enter password enter startx + 'Return' and note any error messages
then go to **[ *X*] **above.

Let us know how it goes.

If there are still problems, clarify what Computer/CPU you have, the Ubuntu dist. & version, and if Windows/Wubi or direct install.

Chao!, **bogan.**

---

### Post by Crossbow on 2013-04-07
Isn't there any way I can just download this to where Synaptic can see it? 

While I had the "timidity" message, it would not respond to any keystrokes. I had to turn off the computer. The first time I rebooted, everything ran like normal so I tried the procedure again but the same thing happened. Then I rebooted in recovery mode and tried it from root. After that I could not log in at all. I had to go back to root and tried it from there but just got the "could not open" message. I tried reinstalling Nvidia-current, could not log in. Tried installing Nvidia-173, then I could log in with no GUI. Logged in that way and installed 173 again, now it is up and running but still with 173 and not X86.  

I did some web-searching and found that the timidity hangup is a not-uncommon problem but no one knows what to do about it.

ETA:

OK, this time ctrl+alt+f1 for me to a command screen. However, it still wouldn't work. sudo service lightdm stop got me "uknown," and sudo sh blah blah blah got me "cannot open." I think that lightdm command may be wrong.

---

### Post by mansonfan78 on 2013-04-07
Try booting in text mode by editing the startup option as Bogan said.  Once your at the text mode prompt you do not need to enter the "stop lightdm" command because it isn't running.  Instead cd to the directory where the downloaded driver is (if it's just in your /home directory you're already there) and type "sudo sh NVIDIA-nameofdriver.run".  It should automatically remove any existing nvidia driver before installing.

---

### Post by monkeybrain2012 on 2013-04-07
> **Crossbow said:**
> Isn't there any way I can just download this to where Synaptic can see it? 



Look, just open synaptic and search for Nvidia 173, it is in the repo. YOU DON'T NEED TO DOWNLOAD ANYTHING FROM NVIDIA. I don't know why  bogan keeps telling you to download from Nvidia and install the .run file, it is a pain and if you are not experienced just don't do that.

---

### Post by mansonfan78 on 2013-04-07
The 173 driver doesn't do what he wants (WOW) the 310 driver will.  I have an 8400 gs (so it's basically the same card as his) and trust me the 310 driver is a huge improvement.

---

### Post by monkeybrain2012 on 2013-04-07
He can also install 310 from the repo, point is there is no need to download a .run file from Nvidia and go through the pain of trying to get it to work.

---

### Post by kuifje09 on 2013-04-07
> **mansonfan78 said:**
> The 173 driver doesn't do what he wants (WOW) the 310 driver will.  I have an 8400 gs (so it's basically the same card as his) and trust me the 310 driver is a huge improvement.

Same for me, although I am at 11.10 ( kernel 3.X ) and a 7600GS  ( for one of my systems )

---

### Post by bogan on 2013-04-08
@>monkeybrain2012, You Posted:>  I don't know why  bogan keeps telling you to download from Nvidia and  install the .run file, it is a pain and if you are not experienced just  don't do that.I have not told Crossbow to do anything.

I have only answered his specific questions and tried to explain the difficulties he has asked about. If you re-read the earlier posts in this thread you will see that I prefaced my Post with:" if you want to use the nvidia.com download,".

You also Posted:> He can also install 310 from the repo*It would have been more useful if you explained how he could do that*. As both Synaptic and Additional drivers are notoriously non-informative as to the version referred to, in many cases you can not find out until after you have installed it.

@>Crossbow, Hi!,
The " unknown" instance status message you got in response to the service stop call was because Lightdm was not running, I included it because whether the Xserver was running or not, depended on which route to the terminal you used.

The " unable to run" message was probably because the NVIDIA-blah-blah.run file was not executable; you would need to either run: ```
sudo chmod a+x NVIDIA-Linux-x86.....run # make sure each time you get the file name correct
```or Right Click on the file, select Properties>Permissions,  tick the "Allow executing file as program" and close the window.

That, of course, is if you want to persevere and get the nvidia.com driver to install, despite the rather predjuiced contrary comments disguised as advice..

If you do not, then the correct package name for the 310 driver from 'normal' sources is "nvidia-experimental-310", and you also need: "nvidia-settings-experimental-310", but in my Synaptic, running 12.10, there is also listed: "nvidia-experimentel-310-dev", that is not what you want.

In Additional Drivers it is listed as: "Experimental NVIDIA binary Xorg driver, kernal module and VDPAU library" and you need to highlight it and read the text below to make sure it is the 310 version, and not 304 listed as the same.

If you use this route, make sure you remove any previously installed driver with a different package-name, before installing another.

Sorry it is not as 'dumbed-down' as perhaps you would like, but the other Posts involving other PPA's to get a non-'Experimental' would be even less dumb, if the Posters had bothered to read the Thread sub-title.

Chao!,** bogan.**

---

### Post by Crossbow on 2013-04-13
Well now I don't have. GUI at all. Tried going back to 173 but can still only log in as terminal.

---

### Post by Crossbow on 2013-04-13
Lightdm is failing to start.

---

### Post by Crossbow on 2013-04-13
Completely purged all drivers and installed 310 from root. logged in and fond no drivers installed. Managrd to get to synaptic and install 310. restarted, stuck at login screen.

I just wanted to do my taxes!!!

ps. I'm a she.

---

### Post by mansonfan78 on 2013-04-14
Okay, try this: reboot into recovery console and select "repair broken packages".

---

### Post by Crossbow on 2013-04-21
Fix broken packages does nothing. I gave up and went back to 173.

Then today I decided to go to Ubuntu 12.10. Rebooted after upgrade and now all I have is a flashing cursor. I can't ebnen type. logged into recovery as root. found that now uname -r is 3.2.0-40-generic. Tried to install headers for that. PACKAGE NOT FOUND. tried with my previous uname, again PACKAGE NOT FOUND. It says linux-headers-generic is the most current version. Update returned unable to resolve ARCHIVE.CANONICAL.COM and US.UBUNTU.SECURITY.COM or something like that. Typing this on my phone.

Edited: Uname is 3.2.0-40-generic. Previously was 3.2.0-39-generic. Evidently with 12.10 it should be 3.5.0-something?

---

### Post by bogan on 2013-04-22
Hi!, **Crossbow, **

If uname -r gives: '3.2.0-xx-generic' that is 12.04. But you quoted: "3.2.0-generic", without the '-xx', which would give you the 'not found'.

12.10 should give you: 3.5.0-17 or up to -27 if updated.

There looks to be something badly wrong with your installation; did you format the partition before installing 12.10 ?  or did you install, over the top of whatever was there ??  or was it an upgrade ??

You could try: ```
sudo apt-get update
sudo apt-get install -f
dpkg-reconfigure -a
``` If you can get to a TTY or terminal, and note any errors. Though that would be much the same as 'Fix broken packages'.


Otherwise it looks like another format and reinstall.

Chao!,** bogan.**

---

### Post by Crossbow on 2013-04-26
> If uname -r gives: '3.2.0-xx-generic' that is 12.04. But you quoted: "3.2.0-generic", without the '-xx', which would give you the 'not found'.

That is just my typing error. I wrote that on my phone which sucks for typing. It was 3.2.0-40.

> 12.10 should give you: 3.5.0-17 or up to -27 if updated.

OK, this is probably key to the problem. It gave me a list of options, all beginning with **3.5.0**, so I checked uname again and it was definitley **3.2.0-40**. So was it, like, partially upgraded?

I will try those commands next time I am on. I can log in as root through the grub menu; that is the only access I have to the system at all right now. 

Thanks!

---

### Post by acimmarusti on 2013-05-01
Hi there,

Just wanted to say that I have a computer with the same card NVIDIA 8300GS and I have the same problem None of the newer binary drivers work (304.xx, 310.xx nor even 313.xx). It appears this started happening after the driver 285.xx. . I've submitted the appropriate bug reports:

[http://bugs.debian.org/686277](http://bugs.debian.org/686277)
[http://www.nvnews.net/vbulletin/showthread.php?t=177566](http://www.nvnews.net/vbulletin/showthread.php?t=177566)

And sent an email to nvidia which the acknowledged but have fallen silent for months now.
So there are only 2 alternatives now, using nouveau (which works fine, but has poor performance) or using legacy 173.xx nvidia driver which also won't be so good on the performance front.
Maybe if we make enough noise, nvidia will notice this and fix it: 

[email]pgriffais@nvidia.com[/email] (this is the email of the NVIDIA guy that answered he was going to work on this....back in September 2012...)
[email]linux-bugs@nvidia.com[/email]

---

### Post by acimmarusti on 2013-05-01
Sorry for double post...

---

### Post by mansonfan78 on 2013-05-01
Can you download an older driver from Nvidia, something before 285 but after 173?  Maybe that will work.

---

### Post by acimmarusti on 2013-05-01
> **mansonfan78 said:**
> Can you download an older driver from Nvidia, something before 285 but after 173?  Maybe that will work.

I tried doing this from NVIDIA, but they don't keep such old versions.

Debian squeeze has 195.xx which worked perfectly on the computer, but even that is pretty old. Debian snapshots should have some newer version.... mmm that could work... but that wouldn't help Crossbow much.

---

### Post by mansonfan78 on 2013-05-01
I uploaded an old 270 driver to my (gasp!) Windows Skydrive:  [https://skydrive.live.com/redir?resid=7830F27E51DC51AC!157&authkey=!AAMNIEQoYuWxk-U ]("https://skydrive.live.com/redir?resid=7830F27E51DC51AC!157&authkey=!AAMNIEQoYuWxk-U")

If that doesn't work I can upload to Ubuntu One, although I've never used that before.

---

### Post by mansonfan78 on 2013-05-01
Okay, here's the same file on Ubuntu One:  [http://ubuntuone.com/3htREekOAgmOrL1Vh6aHGg](http://ubuntuone.com/3htREekOAgmOrL1Vh6aHGg)

---

### Post by acimmarusti on 2013-05-02
Thanks, but I actually found the latest binary driver from NVIDIA claimed to work on the 8300 GS:

For 64 bits:
[ftp://download.nvidia.com/XFree86/Linux-x86_64/290.06/](ftp://download.nvidia.com/XFree86/Linux-x86_64/290.06/)

For 32 bits:
[ftp://download.nvidia.com/XFree86/Linux-x86/290.06/](ftp://download.nvidia.com/XFree86/Linux-x86/290.06/)

These drivers were released back in November 2011. I'm unsure the provide support for kernels 3.2+
Hope this helps others

---

### Post by acimmarusti on 2013-05-02
I just tested and it didn't work. These version do not support Xorg server version 1.12 found in Debian wheezy and Ubuntu precise.

---

### Post by bab1 on 2013-05-02
> **acimmarusti said:**
> I just tested and it didn't work. These version do not support Xorg server version 1.12 found in Debian wheezy and Ubuntu precise.

As you can see this is not just a Nvidia driver and card issue.  Xorg was updated and the driver is not compatible with Xorg.  For a while Nvidia didn't even know what to do.  In the end I believe they have not revised any of the older drivers to support the Latest x-server.  The choices appear to be use an earlier version of the OS or get a later Nvida video card.  I have this same issue on one of my machines, so I have just not used it for the time being.  Hopefully the open source drivers will work someday.  There are other things that can go wrong.  I have one host that has no TTY's (F1 -F6) so I have no console.  The PTTY terminal does work of course, but it's of no use if you have a black screen staring back at you.

---

### Post by Crossbow on 2013-05-04
I am happy to go back to Ubuntu 12.4 but I don't know how to do that in terminal.

---

### Post by Crossbow on 2013-05-04
Results of update.

 [IMG]http://img.photobucket.com/albums/v97/Crossbow/2013-05-04145606_zps26bdb7f9.jpg[/IMG]

---

### Post by mansonfan78 on 2013-05-05
Unfortunately, you can't do a downgrade.  You would have to do a fresh install of 12.04 from a live cd.  If you do that, when installing don't let it automatically download updates, just install what's on the cd.  Then after you reboot into your installed os, open synaptic and find "xserver-xorg-core" and "xserver-xorg-common" and version-lock them (since newer versions of them seem to be causing problems).  Then you can update and later install an older Nvidia driver such as what acimmarusti posted.  This is just a suggestion, maybe somebody else has a better idea.

---

### Post by bab1 on 2013-05-05
> **Crossbow said:**
> Results of update.

The image shows a temporary  DNS failure.  The repos are available.  This has nothing to do with the topic of this thread.

---

### Post by bab1 on 2013-05-05
> **mansonfan78 said:**
> Unfortunately, you can't do a downgrade.  You would have to do a fresh install of 12.04 from a live cd.  If you do that, when installing don't let it automatically download updates, just install what's on the cd.  Then after you reboot into your installed os, open synaptic and find "xserver-xorg-core" and "xserver-xorg-common" and version-lock them (since newer versions of them seem to be causing problems).  Then you can update and later install an older Nvidia driver such as what acimmarusti posted.  This is just a suggestion, maybe somebody else has a better idea.

It's a little more complex than that.  The latest download of 12.04 Ubuntu is 12.04.4.  The updates are allready in the download.  If you could get copy of 12.04.2 then one might have some success.  I'm running 12.04.2 with some success.  ```

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7300 SE/7200 GS/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.48

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

The choice of which X-server is up to the distro developers.  I believe Xubuntu 12.04 and Lubuntu 12.04 both use the earlier version of X-server.  Debian Squeeze also uses Gnome2.  You can let them update normally as their standard package is the earlier X version.  Of course, if you install a package the uses Gnome GTK3 dependencies you will have the same situation as we have now Ubuntu 12.04/12.10/13.04.

This is where I stand.  I know that Nvidia is not willing to accommodate an older video card, but I will wait to see how stable the newer drivers are with Gnome/Unity before I buy a newer video card for 12.05 Ubuntu and beyond.  At least my combination of video card/Linux distro/Nividia driver works for Gnome3.  I just have no TTY's (consoles f1 - f6) or 3D.  :-(

---

### Post by Crossbow on 2013-05-05
Uh... since I don't have a GUI and can't connect to the internet through root, burning an install disc isn't an option. Until I fix whatever is going on in that image, I am at a standstill.

---

