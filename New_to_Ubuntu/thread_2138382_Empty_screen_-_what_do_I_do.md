---
title: "Empty screen - what do I do?"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by jrosado on 2013-04-23
I'm just installing the latest Ubuntu for the first time (alongside XP on a Sony Vaio laptop) and all I get is a sunset colored screen. I move the cursor around, press various keys, but nothing happens.

When I first tried to set it up, there were a few icons on the upper right, and I was able to get the wi-fi configured. But they're gone now.

Then I pressed each of the F-keys and with F4  I got a window with options: file, edit, view, go, etc., but that doesn't help.  On the view sub-menu, main toolbar and status bar are checked, but other than the desktop image, the screen is empty. The mouse works fine.

How do I get something that lets me do things?  How can I open a browser?  I'm in no-man's land limbo here.  Please help!

---

### Post by Bashing-om on 2013-04-23
jrosado; Hi Welcome to the forum.

Huh ?? Are you actually installed with ubuntu, or are you looking at ubuntu in the "try ubuntu" mode ?

Be advised that later versions of ubuntu's desktop environment is "unity". There are no default icons on the desktop; If one had made no changes to "unity", tools and applications are available from the launcher (left side of screen);
What might be happening (if you have installed ubuntu) is that the launcher is in "autohide" mode.
What results if you push your mouse cursor through the left side screen (keep pushing) or might be set to respond to the top left corner.

For additional advise, please advise us of what version of ubuntu you are installing;
What steps you are failing at;
what specifically results in what you are attempting;

At this point world be nice to know if you have indeed booted ubuntu up to and into the "try ubuntu" mode from the live install medium.
[INDENT=3]
we are here to help

[/INDENT]

---

### Post by jrosado on 2013-04-23
Thanks for the quick reply.

I *_installed_* Ubuntu 12.10 (and it said it updated automatically) along side of Windows XP on a laptop.  

When I move the mouse cursor to the far left and push it, nothing happens.  Same for any other edge or corner of the screen and every keystroke and combination I can think of.

When I first got it installed, there was no panel anywhere, but there were three or four very small black icons in the upper-right corner.  I was able to get the internet connection in and change the desktop to a blue scene, but that's all. Those little icons disappeared and there's nothing on the screen except the blue picture of a mountains and a lake (I think).  

I'd like to experiment and try the various goodies in Ubuntu, but nothing I do seems to help.

I'm not a new to IT. I've been working with  computers since the early 70s; Burroughs 7400 mainframes and up, then with the first personal machines, Radio Trash T80, Osborne and then the very first PC Jr. I've used every version of Windows since I alpha-tested the first Windows (v. 0.9) for MS, which required a bus mouse with a card installed in the maximum 640 Kb RAM machine.  But I've never played with modern Linux flavors.  I'm hoping to be a convert. 

With MS ending support for XP, I thought I'd give my old laptop, which gets used by guests mostly, new life with Ubuntu.  I'll be most grateful for words of wisdom to get my new installation working.

If not, should I try to reinstall 12.10 over the first try?

---

### Post by Bashing-om on 2013-04-24
jrosado;

With your background, you are a very welcome addition to our family. (I also started my journey back in the sixties on mainframes and too recall the trash 80 kindly).

To the situation at hand, getting you up on 'buntu ->
How old is the desktop ? Now-a-days ubuntu in particular has become resource hungry; and requires a processor greater than or equal to the pentium 4 and a hefty graphics card; See these documentations:
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
[http://askubuntu.com/questions/206364/what-are-the-system-requirements-of-ubuntu-12-10-can-i-install-ubuntu-on-my-sys](http://askubuntu.com/questions/206364/what-are-the-system-requirements-of-ubuntu-12-10-can-i-install-ubuntu-on-my-sys) A google search with the term "12.10 ubuntu requirements" will produce good results.

Let me say that in the event there is not the hosses on the lappie to run "ubuntu" there are lighter versions available that will perform admirably on older hardware.

Let's work on getting you up on ubuntu:
Can you boot up the liveDVD to the "try ubuntu" mode ?
If you can, then we want the processor and graphics card/display info: From the liveDVD, key combo ctl+alt+t gives a command line interface (terminal);
Post back the results of terminal commands:
```
 cat /proc/cpuinfo
sudo lshw -C display
lspci -nnk | grep -iA3 vga
```
"sudo" == Super User DO" to gain administrative authority

What else can I say ? We want you up on 'buntu and;[INDENT=2]
one step at a time will get you there

[/INDENT]

---

### Post by jrosado on 2013-04-24
Thanks very much for the reply.  I'm most appreciative with the very quality of assistance.  This forum
reminds of how good it was when we first began with computing.

I used the disc to enter the [COLOR=#008080]Try Ubuntu[/COLOR] mode and, other than the wallpaper and the four small black icons 
in the upper right corner, got a totally empty screen. Those icons disappeared soon after.

I was able to enter the three command lines you gave me.  There was quite a lot of data in the results
so I took photos of them with my iPod Touch.  The resolution isn't great, but you should be able to read the
results.

I'm not sure how to send these to you or post them in a reply.  The image option here asks for a URL
(I'm used to browsing for the location on my machine for other forums).   Is there a way to post these directly or
email these to you?  

As a last resort, I could temporarily upload them to a private directory on my website [heart.kumu.org]("http://heart.kumu org") .

Mahalo nui loa and aloha from Hawaii.  (Many thanks and ...)

---

### Post by Bashing-om on 2013-04-24
jrosado;

Let me re-boot into the liveCD and do some testing for a simpler method to access this forum and copy/paste the output from the requested commands.[INDENT=2]i'll be back

[/INDENT]

---

### Post by Bashing-om on 2013-04-24
jrosado;

I am Back---Found I do not have the skills presently to implement what I had in mind (this system is a life long learning process !)//

But, OK... let's try this to get you to a useable GUI desk top on the liveCD:
Boot the liveCD and at the purple splash screen depress the shift key -> language screen; escape key to accept the default -> Boot options screen;
In the boot options screen; f6 key for additional boot options, choose (arrow key) "nomodeset" and space to accept then escape key to exit;
Press the enter key to continue the boot process, hopefully to the GUI desk top.

The "nomodeset" option disables kernel mode setting, and forces a lower level driver "vesa" to load.
Not knowing what graphics card you have installed, "nomodeset" may not work, else try the other available options in the menu.

Please to advise if you are able to boot to a useable desk top at this time before we proceed on.
[INDENT=2]
small steps, starting a long journey
[/INDENT]

---

### Post by jrosado on 2013-04-25
I probably jumped the gun, but in my experience, when things go sour as they have in this situation, I've found that re-installing often solves the problem.  I went ahead (before you replied) and deleted the partition that Ubuntu was in and will be installing it from scratch.  

If the same situation occurs again, I'll follow your steps. I'll report back to you around mid-morning Hawaii time.

Also, I put the Ubuntu disc in my 64-bit dual core desktop (Windows 7 Ultimate).  Everything went perfectly fine, I accessed Firefox and g-mail using the trial setup and was very pleasantly impressed with how quickly and cleanly things happened.  I plan to eventually install it on the desktop, but I'd like to learn how to change the boot order first (until I learn more about the commands and applications, I want the default boot to be my usual setup).

---

### Post by Bashing-om on 2013-04-25
jrosado;

You'll not find me faulting attempting to establish a firm foundation from which to work from.

I have been around for a long time, played with a number of operating systems ( I presently have 3 installed onto this box ), and I find ubuntu is my operating system of choice -> kernel, modularity, support, documentation, and superb package management.

When you are ready to proceed, we are here to assist. In this respect, keep in mind; on this forum there is no such thing as a dumb question.
[INDENT=3]keep'n on keeping on

[/INDENT]

---

### Post by jrosado on 2013-04-25
Again, thanks for the friendly support.  Learning a new OS is always a challenge, especially when one has passed 3/4 of a century.

The news is not good.  I attempted to install Upuntu 12.10 along side of XP on the laptop and it looked as though everything was progressing fine (it didn't ask me about partitioning, but used the partition that it created yesterday). The progress bar was at the very end when the screen went black and white text appeared. 

It started out                  [ 1673.662424]   Kernel panic: not syncing: attempted to kill initl 
__then 18 lines of code
 and ended:                    [ 1673.665388]  panic occurred, switching back to text console

Then the machine froze.  No input changed anything.

When I shut down and rebooted into Ubuntu, I got a dead screen with no cursor movement. Booting into XP is OK.

I think this must be a problem with my laptop, a 7 year old Pentium4 with 1G of RAM, VGA Radeon graphics.

Is there a less demanding version of Ubuntu that I might be able to use on this machine?

---

### Post by Bashing-om on 2013-04-25
jrosado;
Pentium 4 : IF that processor is pae and sse2 enabled(more about that later) with 1gig of ram should run ubuntu fairly decently. That said, lubuntu will be faster.

But for now let us work on getting you up on ubuntu: The starting point is booting up with the liveCD; Looking about for what we are working with and then installing making the discovered corrections.

Boot the liveCD with the "nomodeset" option as advised earlier, and we will go from there.
[INDENT=2]
step'n on out

[/INDENT]

---

### Post by mörgæs on 2013-04-25
All Pentium 4's have PAE so there is no problem here, but you will never get a decent performance with Ubuntu. Lubuntu 13.04 is the way to go.

---

### Post by jrosado on 2013-04-26
After doing some more reading about Ubuntu (if all else fails, read the directions), I found out about Lubuntu and Xubuntu.  It seemed likely that a lighter version might work on this older laptop.

The trial of **Xubuntu 13.04** worked perfectly and I've just installed the regular version on the partition that 12.10 was in.  While this flavor isn't as elegant as 12.10, it will do what I wanted for the laptop.  Now I can let guests go online and get their mail without messing with the XP I have on it.  Eventually, when I learn more how to speak Ubuntu, I'll delete XP and expand the Ubuntu partition to the full drive.

I'll be installing Ubuntu 12.10 on my desktop (the trial version worked fine).

Thanks very much for all the support and the very friendly atmosphere. 

I'm sure I'll have questions and problems as I progress, so as *The Terminator* says, "I'll be baaaack!"

---

### Post by Bashing-om on 2013-04-27
jrosado;

You do well.

As well as the system help files here is a good source of beginners documentation:
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)
and the link in my signature for answers to many many frequently encountered situations/conditions.[INDENT=2]
Happy 'buntu'n !!

[/INDENT]

---

