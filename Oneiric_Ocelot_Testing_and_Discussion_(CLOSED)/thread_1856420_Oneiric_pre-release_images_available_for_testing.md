---
title: "Oneiric pre-release images available for testing"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jibel on 2011-10-08
There was no RC candidates scheduled for Oneiric, but the images that are the trial run for the official images, were posted up on the [iso tracker]("http://iso.qa.ubuntu.com/") last night/today.

   The most recent language pack updates should now be included on those images rebuilt today as well.  They are now very close to what we'll be building as the formal candidate images on sunday/monday.   

**How You Can Help**

You can start syncing your ISOs, test any number of test cases you'd like, and report bugs. Test results will be tracked on [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)
 
The procedures for testing ISO images and reporting results are explained on [https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

You may have accounts on the tracker from last time. Please register if you are new to this.

Thank you very much for your help and happy testing!

---

### Post by BigSilly on 2011-10-08
Can anyone download these iso's and use them, or are these only for testing purposes?

---

### Post by jerrylamos on 2011-10-08
I'm not "In the know" but the main i386 and amd64 images look about like those on the Ubuntu Daily Build: 
[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)
using zsync is a good way to reduce the network load.

For all the variants the pre-release images should be better.

This is a netbook, Aspire one intel Atom.  I've tried "netbook" versions on it and see no advantage to just running the regular main i386 images.  On my notebook with amd64 chip, I still use i386 image because I've seen no advantage to the 64 bit stuff for my use.  Maybe someone can explain why it is a good idea to use the 64 bit.

Have fun.  

Oh, by the way, use test partitions.  5 GB might do, I use 10 GB partitions.

Jerry

---

### Post by BigSilly on 2011-10-08
Sorry I realise this is a dumb question, but I've installed one of these images today and am really happy with the general performance, barring a couple of bugs. If I keep this up to date can I keep this install or would you recommend installing the final release over this?

I only ask as I've never before installed a testing release. I simply couldn't wait to get my hands on Oneiric! :D  Thanks.

---

### Post by philinux on 2011-10-08
> **BigSilly said:**
> Sorry I realise this is a dumb question, but I've installed one of these images today and am really happy with the general performance, barring a couple of bugs. If I keep this up to date can I keep this install or would you recommend installing the final release over this?

I only ask as I've never before installed a testing release. I simply couldn't wait to get my hands on Oneiric! :D  Thanks.

Just keep it updated and that's it.

---

### Post by BigSilly on 2011-10-08
> **philinux said:**
> Just keep it updated and that's it.

Brilliant! Thanks for your reply. :)

Like I say I know it's a stupid question, but you have to be sure. I've never used a testing release. I've already submitted a couple of reports (well three all told). Fingers crossed this will be a truly great release.

---

### Post by kansasnoob on 2011-10-08
I'm having a horrible time :(

Look here from post #181 forward:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316?comments=all](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316?comments=all)

It's not only eating my lunch, **[COLOR="Red"]it's eating my hardware![/COLOR]**

Would SABDFL please send me a crate full of new optical drives :lolflag:

---

### Post by ELD on 2011-10-08
> **kansasnoob said:**
> I'm having a horrible time :(

Look here from post #181 forward:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316?comments=all](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316?comments=all)

It's not only eating my lunch, **[COLOR=Red]it's eating my hardware![/COLOR]**

Would SABDFL please send me a crate full of new optical drives :lolflag:
You need to invest in a USB stick friend ;)

---

### Post by kansasnoob on 2011-10-09
> **ELD said:**
> You need to invest in a USB stick friend ;)

I could use a USB stick, but that will hardly help squash that bug will it?

If we end up with a bunch of people complaining about broken optical drives it'll be a sad, sad thing :(

---

### Post by kansasnoob on 2011-10-09
I finally worked through the optical drive breakage thing, I hope:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316/comments/193](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316/comments/193)

Suffice it to say that having limited resources stinks ;)

---

### Post by _duncan_ on 2011-10-09
I had one of my optical drives damaged because of this a few releases ago. Fortunately GRUB 2 allows loop mounting of downloaded .iso files directly, so I never have to burn to an optical disc to run a live CD since then.

---

### Post by ventrical on 2011-10-09
> **_duncan_ said:**
> I had one of my optical drives damaged because of this a few releases ago. Fortunately GRUB 2 allows loop mounting of downloaded .iso files directly, so I never have to burn to an optical disc to run a live CD since then.


How would we accomplish this . ? Could you put it up in simple steps?

---

### Post by effenberg0x0 on 2011-10-09
I've read a recent bug report in which the ODD was opening/closing automatically and too fast. Don't know if people tried to hold it and got it jammed, or if the media was partially inserted and touched the lenses. I'm interested in the details too (can't find the bug report in my browser history).

Regards,
Effenberg

---

### Post by chazinams on 2011-10-09
I'm running Unity-2d, fully up to date, and it is really slow. Aw, man, is it slow. Opening the Dash takes a few seconds. Typing like in Writer, or Firefox,  takes a few seconds for letters to appear after you type them.  Everything is just so slow.

It's been like this since I installed it (Beta-2). I assumed it was cause it was Beta and that it would gradually improve, but it hasn't. Frankly if the final release is as slow as it is now, I'm not going to be able to use it.

---

### Post by effenberg0x0 on 2011-10-09
> **chazinams said:**
> I'm running Unity-2d, fully up to date, and it is really slow. Aw, man, is it slow. Opening the Dash takes a few seconds. Typing like in Writer, or Firefox,  takes a few seconds for letters to appear after you type them.  Everything is just so slow.

It's been like this since I installed it (Beta-2). I assumed it was cause it was Beta and that it would gradually improve, but it hasn't. Frankly if the final release is as slow as it is now, I'm not going to be able to use it.

Unless you're running a very old hardware, there's something else going on. What are your specs? Whats your video card brand) ATI, Nvidia, etc)?

Regards,
Effenberg

---

### Post by chazinams on 2011-10-09
It's old hardware, but 10.04 runs great on it.

I got a pent4, geforce from Nvidia, 512ram.

---

### Post by _duncan_ on 2011-10-09
> **ventrical said:**
> How would we accomplish this . ? Could you put it up in simple steps?

[[COLOR="Blue"]_ISO Booting with Grub 2_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1549847")

---

### Post by jbicha on 2011-10-09
Does ISO booting work in 11.10? I tried it earlier and had problems in the partition selection spot (it didn't want to install to the same disk as the ISO) but didn't get around to reporting a bug for it.

---

### Post by ventrical on 2011-10-09
> **_duncan_ said:**
> [[COLOR=Blue]_ISO Booting with Grub 2_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1549847")


Ok . great .. thanks !!

  Just want ot make one side note .. I always had a hard time getting a torrent .iso to  work properly. I always had to go to a non torrent site... yeah .. I pay for the bandwidth .. but I get as good solid .image.


Thank again.

---

### Post by ventrical on 2011-10-09
> **kansasnoob said:**
> I finally worked through the optical drive breakage thing, I hope:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316/comments/193](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316/comments/193)

Suffice it to say that having limited resources stinks ;)

I'm a hardware serviceman and I have seen this happen many times with  CD/DVDs, especially NEC !!. Pioneer .. not sure.

Overtime they loose calibration. Some have infrared switches. others resistive.. Cleaning IR eyes and the lens head help.

  If there is even a 'spec' of dust on the laser apeture it canlead to the exact anomolous behaviours described.

  If you want to test this .. take a high powered lens and examine you laser aperture - guaranteed 99% of the time you will find a spec or a film. Most heads are designed to shut down (or malfunction)  if there is side noise being deflected from foriegn objects on the lens.

*note*

Make sure CD-ROM drive os OFF! Do not examine laser apeture with laser is on !!

---

### Post by dmoconnell on 2011-10-09
> **ventrical said:**
> 
*note*

make sure cd-rom drive os off! Do not examine laser apeture with laser is on !!

aahhh the laser it burns!!!!! :D

---

### Post by effenberg0x0 on 2011-10-09
> **chazinams said:**
> It's old hardware, but 10.04 runs great on it.

I got a pent4, geforce from Nvidia, 512ram.

Yes, not a great hardware, but should work. I'll guess you're not up-to-date on your video setup, running indirect rendering, something like that.

You can check some information:

DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
DISPLAY=:0.0 glxinfo
`whereis nvidia-settings | awk 'BEGIN{FS=" "}{for(i=1;i<NF;i++) print $i}' | grep "/nvidia-settings"` --version

Please report back.

Effenberg

---

### Post by _duncan_ on 2011-10-09
> **jbicha said:**
> Does ISO booting work in 11.10? I tried it earlier and had problems in the partition selection spot (it didn't want to install to the same disk as the ISO) but didn't get around to reporting a bug for it.

I was able to install 11.10 beta2 to a spare partition as multi-boot with existing Natty install.

I also used to have problems when the iso image is on the same drive as the target install partition. But since I have several drives, I just move the iso file to another drive and make the appropriate changes to the custom grub menu entries.

---

### Post by Flymo on 2011-10-10
Not a lot of luck here.   Oneiric Beta 2 live CD fails to suspend and resume reliably on Compaq 300 (Celeron) Acer 5684 (T5600) and eMachines ER1401 (K325).  Also fell over twice.

These machines have all had Lucid running faultlessly for ages.:D

I keep trying to learn/like Unity, but it keeps being annoying and being obstructive, and some of the controls are now changed and suddenly I'm no longer feeling warm and fluffy about Ubuntu being Linux for Human Beings.
(Senior moments of the **.....cannot belieeeeeeve it!** flavour.)

Canonical is of course entitled to do whatever they wish with Ubuntu, but this clumsy interpretation of the (fairly obstructive) Gnome 3 is just not up to standard.  It's a retrograde step in  usability at the same time as the stability drop off on our hardware.

Oneiric looks like being the first Ubuntu since Breezy that we don't install. Mind you we had to wipe Natty for suspend/resume misbehaviour. :(

Do hope Unity is fixed (or abandoned?) before we have to migrate our posse of n00bs from Lucid to the next LTS.  In testing 100% of them said they disliked both Unity and Gnome 3.

---

### Post by chazinams on 2011-10-10
> **effenberg0x0 said:**
> Yes, not a great hardware, but should work. I'll guess you're not up-to-date on your video setup, running indirect rendering, something like that.

You can check some information:

DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
DISPLAY=:0.0 glxinfo
`whereis nvidia-settings | awk 'BEGIN{FS=" "}{for(i=1;i<NF;i++) print $i}' | grep "/nvidia-settings"` --version

Please report back.

Effenberg

I don't know what exactly you're asking me to do. I ran these in the Terminal

~$ DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
bash: /usr/lib/nux/unity_support_test: No such file or directory

~$ DISPLAY=:0.0 glxinfo
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils

~$ `whereis nvidia-settings | awk 'BEGIN{FS=" "}{for(i=1;i<NF;i++) print $i}' | grep "/nvidia-settings"` --version

--version: command not found

Sorry for my ignorance.

---

### Post by effenberg0x0 on 2011-10-10
unity_support_test can tell us whether yous system is OK for running Unity. Its part of the nux-tools package. You don't seem to have it installed. You can install it and run the command, like this:

```
sudo apt-get install nux-tools
DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
```glxinfo can also give us information on how your system supports OpenGL, which is essential for an accelerated desktop experience. You can get it and run it with:
```
sudo apt-get install mesa-utils
DISPLAY=:0.0 glxinfo | grep -i "direct rendering"
```The third line was to check whether you have nvidia-settings installed and what is its version. It probably don't survive a cut/paste with all the required characters. You can go to a console and run it like this.

```
/usr/bin/nvidia-settings --version
```Sometimes GL libs are not in the right place, or linked right. We can see that with this:
```
ls -lah /usr/lib32/libGL*
```With the output of these commands, we can begin to understand if there's anything wrong there, and if there's anything we can do to improve your desktop experience.

Regards,
Effenberg

---

### Post by MAFoElffen on 2011-10-10
I tested some of these yesterday. but noticed that on return to the ISO Testing Team today, that most of the ISO links are lined out and say that they are "rebuilding"...

Maybe they made some good changes this morning?  Will look again this afternoon and retest the daily.

---

### Post by kansasnoob on 2011-10-10
> **MAFoElffen said:**
> I tested some of these yesterday. but noticed that on return to the ISO Testing Team today, that most of the ISO links are lined out and say that they are "rebuilding"...

Maybe they made some good changes this morning?  Will look again this afternoon and retest the daily.

And most images are still "rebuilding" :)

Always look here:

[http://iso.qa.ubuntu.com/qatracker/](http://iso.qa.ubuntu.com/qatracker/)

And refresh often, it sometimes takes a while for all of the devs to get in sync ............. and I suspect that some internal testing is going on almost non-stop ;)

I've been iso-testing for quite a while and more than once I've begun testing an image only to find upon completing the test that a new build was already in progress.

IMHO things look pretty good. Most of the nastiest problems are taken care of - other than screensaver/power-management in gnome 3 - so I'm fairly certain that Oneiric will be released on time.

---

### Post by chazinams on 2011-10-11
> **effenberg0x0 said:**
> unity_support_test can tell us whether yous system is OK for running Unity. Its part of the nux-tools package. You don't seem to have it installed. You can install it and run the command, like this:

```
sudo apt-get install nux-tools
DISPLAY=:0.0 /usr/lib/nux/unity_support_test -p
```glxinfo can also give us information on how your system supports OpenGL, which is essential for an accelerated desktop experience. You can get it and run it with:
```
sudo apt-get install mesa-utils
DISPLAY=:0.0 glxinfo | grep -i "direct rendering"
```The third line was to check whether you have nvidia-settings installed and what is its version. It probably don't survive a cut/paste with all the required characters. You can go to a console and run it like this.

```
/usr/bin/nvidia-settings --version
```Sometimes GL libs are not in the right place, or linked right. We can see that with this:
```
ls -lah /usr/lib32/libGL*
```With the output of these commands, we can begin to understand if there's anything wrong there, and if there's anything we can do to improve your desktop experience.

Regards,
Effenberg

Thanks :=) (you are so knowledgeable)

I don't know what a console is.
Terminal = bash: /usr/bin/nvidia-settings: No such file or directory 
Alt+F2 = nothing happens


OpenGL vendor string:   Nouveau 
OpenGL renderer string: Mesa DRI nv20 x86/MMX/SSE2 
OpenGL version string:  1.2 Mesa 7.11 
 
Not software rendered:    yes 
Not blacklisted:          yes 
GLX fbconfig:             yes 
GLX texture from pixmap:  yes 
GL npot or rect textures: yes 
GL vertex program:        no 
GL fragment program:      no 
GL vertex buffer object:  yes 
GL framebuffer object:    yes 
GL version is 1.4+:       no 
 
Unity 3D supported:       no 

direct rendering: Yes 


ls -lah /usr/lib32/libGL* 
ls: cannot access /usr/lib32/libGL*: No such file or directory

---

### Post by ronacc on 2011-10-11
> **kansasnoob said:**
> I'm having a horrible time :(

Look here from post #181 forward:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316?comments=all](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316?comments=all)

It's not only eating my lunch, **[COLOR="Red"]it's eating my hardware![/COLOR]**

Would SABDFL please send me a crate full of new optical drives :lolflag:

october 10 amd64 .iso just got me , me-too'd and added comment .

---

