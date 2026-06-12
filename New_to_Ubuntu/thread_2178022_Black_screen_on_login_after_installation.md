---
title: "Black screen on login after installation"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by giorgio3 on 2013-10-01
Hi,
I'm Giorgio a new italian user. I'm trying to install lubuntu 13.04 with the desktop installation on a Toshiba dynabook c9 that has a Pentium III and something like 756 mb of ram. It went everything fine untill, after rebooting, the screen became all black after log in. i really don't know what to do, i just tried reinstalling (delete ubuntu and reinstall) with no success.
Thank you for your help :)

---

### Post by poettone on 2013-10-01
Hello and welcome!

Its hard to say on this issue but I would guess at this point it's a conflict of sorts with the graphics driver for the system. 

You state after you login the screen goes black? Are you logging into a graphical interface or are you on the command line? If you are logging into a GUI I would say that X11 is having issues with the settings of your monitor (or your monitors limiatations) are being exceeded. 

when you reinstall, I would choose the lowest possible resolution you can and see if that helps. I know we all want to have the highest resolution possible but sometimes what is listed and what we choose is out of the range of our monitors capabilities. 

Try that and post back sceenshots of any errors etc.

Thanks

---

### Post by DuckHook on 2013-10-01
Hi giorgio3 and welcome to Lubuntu and the forums.

You have an extremely old laptop with a non-PAE CPU that will not run the latest kernel. You have a number of options:

1. Install a standalone non-PAE kernel available from the Ubuntu mini-iso. This will give you a bare-bones command line interface (CLI) version of Ubuntu, but at least it will install a kernel that works with your laptop.
2. After step 1 above, you can leave your laptop as a CLI machine and use it as a server. In many ways, this is the easiest and cleanest option because you won't need to wrestle with graphics drivers and your limited memory won't be a problem either. I use many of my old laptops in just this way, running them as backup servers, file and media servers, print servers, firewalls, routers, etc. None of these uses require a GUI and these otherwise obsolete laptops are revitalized and run like champs.
3. During the install process, you can also tell the mini-iso to install LXDE or a minimal Lubuntu desktop. I don't know how well Lubuntu will run on equipment as old as yours, but you can give it a try.
4. Install a different distro altogether that is designed to still support old equipment. I would recommend CrunchBang or PuppyLinux. They won't use the Ubuntu repositories, but they do have a good selecton of lightweight apps in their own repositories. I am not familiar with it, but you could also look into SliTaz. This would be the most painless solution because such distros should just install and run.

The instructions and links for downloading and installing the mini-iso are [here]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html"). Web Upd8 is a legitimate site that is wonderful for Ubuntu tips, tricks and options, but you can and should check them out thoroughly before downloading (standard security practice).

You will definitely not be able to run Ubuntu, but Lubuntu should be okay. The key is to install the non-PAE kernel as per the instructions.

Let us know how it goes, and Happy Lubuntuing!

Edit:

Ignore all of above! Read subsequent post from *walterorlin*

/Edit

---

### Post by walterorlin on 2013-10-02
I thought I read pentium 3 was had a pae flag or at least some did. I am not sure you have heard of nomodeset [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) which is a kernal boot parameter that should fix this.

---

### Post by DuckHook on 2013-10-02
> **walterorlin said:**
> I thought I read pentium 3 was had a pae flag...You are absolutely correct. My bad. I had confused OP's CPU with Pentium M. <sigh> Losing my grip and jumping to stupid conclusions in old age. :redface:

@OP

My long set of instructions in previous post is incorrect and you should ignore it. As *walterorlin* correctly points out, your processor is capable of running the latest kernel and your black screen is likely from another cause.> I am not sure you have heard of nomodeset [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) which is a kernal boot parameter that should fix this.Yes, I am quite familiar with it and have used it myself in some balky installs. Thanks for linking to an actually *useful* solution.

@OP

Please visit above thread.

---

### Post by giorgio3 on 2013-10-02
thanks all for replying.

in theory if nomodeset solution works, if i flag the nomodeset option and try to start lubuntu live without installation this should work i'm right?
however i'm going to try installing again with nomodeset and let you know
thanks

---

### Post by DuckHook on 2013-10-02
> **giorgio3 said:**
> ...if i flag the nomodeset option and try to start lubuntu live without installation this should work i'm right?Yes.> ...however i'm going to try installing again with nomodeset and let you know
thanksTry the Live version first. No point in wasting time if this doesn't work.

---

### Post by giorgio3 on 2013-10-03
ok, nomodeset doesn't work
after that i tried to follow something written here [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
in particular i stop at step 4 after that step 3 is "no" :)
step 4 is "no" too, but i don't know how to change gfx_modes

i add that i tried to do this stuff and see what would happen:
[COLOR=#000000]Another thing you can try is to drop down the the grub CLI (command line interface) via pressing "c" while in the grub menu... While you are in the Grub CLI, you can use it to test the variable setting, set them to other settings and to see what modes your video supports.-- instead changing things (hard edits) and rebooting to see if it worked... Just just "set" and "unset" viables to change your environment variable from the command line. Such as to set the screen resolution, you should set the variable $vbe_mode before loading vbe and/or gfxmterm (default mode is 0x101 i.e. 640x480 8bpp) Test your graphics... What I last said translates to [/COLOR]
[COLOR=#000000]Code:
  
 set gfxmode=640x480  
 load_video  
 insmod gfxterm[/COLOR]
[COLOR=#000000]From the CLI you could use [/COLOR]
[COLOR=#000000]Code:
  
 GRUB> echo $linux_gfx_mode[/COLOR]
[COLOR=#000000]to see what the video mode it is currently set to... It will most likely be set at "keep". If you then [/COLOR]
[COLOR=#000000]Code:
  
 echo $gfxmode[/COLOR]
[COLOR=#000000]it will most likely say "auto' which is the default. 


[/COLOR]but my $linux_gfx_mode is set to "text"
can this be the problem?

---

### Post by giorgio3 on 2013-10-04
i managed to solve my issue, at least trying it live
i added this to the end of command line (i pressed F6 and added manually)
[COLOR=#000000][FONT=Tahoma]i915.modeset=0 xforcevesa

i found it here: [/FONT][/COLOR][http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

the live session starded and worked fine, now i'm performing a fresh installation with this option, i hope i'm about to mark this thread as solved!!
edit: 
yeah!!! solved!!

---

### Post by mörgæs on 2013-10-04
Thanks for the attempt, but 'solved' is stated in Thread Tools.

If you use this flag people will be able to search for 'solved' in Advanced Search.

---

### Post by giorgio3 on 2013-10-04
thank you morgaes and sorry, i'm a noob, but a fast learner :)

---

