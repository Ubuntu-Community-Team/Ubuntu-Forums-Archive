---
title: "Choppy full screen video"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by eggsbenedict on 2012-10-01
I'm using Ubuntu 12.04 LTS, and while using Ubuntu (unity 3d) full screen video playback is very choppy.  This includes, VLC, movie player, and to a lesser extent youtube videos.  However, not all video playback is choppy: smaller-sized or windowed videos run smoothly.  Even almost fully maximized videos in VLC play smoothly, but as soon as you make it 'full screen' there is significant choppiness.  Not unwatchable, but definitely not suited for serious video watching.  I usually have to switch to another OS to watch videos.

I dualboot with Windows 7, and it plays videos of all size smoothly.  Unity2d also sees no problems in fullscreen video playback.

I found this bug, but no solution is presented:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/961124](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/961124)

I am perfectly happy using Unity2d, but with the impending release of Ubuntu 12.10, I'm worried about my netbook's ability to stick with Ubuntu in future releases because of the dropped Unity 2d.

Here are some of my specs:
Ubuntu 12.04 LTS 64-bit
Memory: 3.6Gib
Processor: AMD Athlon(tm) Neo X2 Dual Core Processor L335 × 2 
Graphics: VESA: RS780M (using the ATI/AMD proprietary FGLRX driver).

I'm not sure if this is a driver issue (deactivating the driver makes no observable difference), or if my netbook just simply cannot handle unity3d (although, this is the only issue I've noticed related to its ability to handle unity3d graphics).

I've tried to search extensively regarding my question, so if there's a thread/solution somewhere that anyone knows about, I'd really appreciate it.

Thank you!

---

### Post by ranger1021994 on 2012-10-01
That is definitely your graphics card driver problem.
purge old config files
and reinstall fglrx



Check this :

[http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts](http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-drivers-in-12-04-lts)

---

### Post by eggsbenedict on 2012-10-01
Hi ranger, thank you for your reply!

I followed instructions in the site you suggested.  I got about halfway through the instructions when I could no longer proceed (with the patch).  

So, after following one of the links posted on that page ('Pavel' suggests a 12-6 [manual]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29") ) - and tremendous trial-and-error - I really messed up.  I'm not sure if it was the manual, or just me (probably me) but I got to the point that  I could no longer boot Unity3d (I was forced into unity 2d).  

I finally found my way to this [walkthrough]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").  I downloaded the latest driver for my card from ATI's website, and successfully followed all the steps and have a reinstalled fglrx driver.  However, I'm back to square one with choppy full screen video.

---

### Post by AndyOpie150 on 2012-10-01
Have you tried using gxine. I had the same problem that you described, so I tried different players figuring it was a codex problem (Don't know if this is you problem). Don't know for sure as I'm a linux newbie, but it fixed the problem when I used gxine.

Not to say this will fix your problem, but it is another option to consider.

PS: I'm using Gnome Classic desktop enviroment.

---

### Post by eggsbenedict on 2012-10-01
Thank you for your suggestion, AndyOpie.

I can report back that using gxine made no difference - full screen videos still suffer from choppiness.

I also realize that when I posted my specs, I did not update them with my new drivers/fglrx specs.

The ATI/AMD driver I installed was the most recent: amd-driver-installer-12.6-legacy-x86.86_64

And, I installed: fglrx 8.970

Don't know if this helps or not, but I figured I'd post it just in case.

---

### Post by AndyOpie150 on 2012-10-01
How was the video output on the old graphics driver? Sometimes newer is not better.

I'm just a linux newb, with just enough knowledge to either help or get in the way. If a linux oldster suggests something I would try that first and skip over me (unless you run out of options).

---

### Post by eggsbenedict on 2012-10-01
Hi Andy,

When you write "old driver" do you mean, my driver before I did all of the updates I detailed?  Or, ( I may be over thinking this) , is there some older Ubuntu driver I can access?

If you mean the one I had before I updated to the current (newest?) driver, truthfully, there is no noticeable difference.   All videos run smoothly when windowed, but choppy during full screen during Ubuntu (unity 3d).  In unity 2d all videos run smoothly, full screen, windowed, etc.

I'm content to use unity 2d for now, but because it seems my computer is capable of handling unity 3d's graphics (besides full screen video), I was hoping to get this sorted out so I could leave unity 2d behind for good, as Canonical seems to be doing. 

I do appreciate your help!  Talking with someone about things is always better than posting a question and receiving zero replies!

---

### Post by AndyOpie150 on 2012-10-01
Well..........Maybe someone will chime in with a better solution. I'm all eye's as I'm in the same boat as you.

---

### Post by eggsbenedict on 2012-10-07
Thank you, though AndyOpie.

I've continued to play around and  look for other solutions, but nothing yet.  Everything I've been able to  find keeps pointing me back to the tutorials I posted above.  Let's  hope a "veteran" comes along to help us out!

---

### Post by DuckHook on 2012-10-07
I'm no veteran, but the RS780M is an integrated video chipset on your Netbook motherboard that must share video RAM from the system RAM. The amount of video RAM is dependent on the motherboard manufacturer. In some Netbooks, it's possible to assign more system RAM to the video subsystem through a setting in the BIOS, but even if you do so, the fact will remain that you are using a video subsystem that is too weak for Unity 3D. I would recommend that you stick with Unity 2D. No point in trying to make this pony do the work of a horse.

---

### Post by eggsbenedict on 2012-10-07
Hi DuckHook, thank you for your response.  I was beginning to resign myself to that realization.  Like I said before, for now I'm happy to use ubuntu 12.04 unity 2d.  And because the LTS will be supported for the next 5 years, I don't HAVE to switch to the newer releases...but it is depressing that Ubuntu is becoming less user-friendly in regards to older systems or lower specc'd computers like mine!

---

