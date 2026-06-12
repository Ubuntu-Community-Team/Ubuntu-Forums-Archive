---
title: "System Screwed"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by the_doc on 2008-06-11
I've just taken delivery of a new Dell Inspiron 1525n preloaded with Gutsy, and everything was fine.

I went into Synaptic and installed the latest gcc, went to a terminal dumped the version number and still got the old version.

I then removed the old version then restarted (don't ask me why!), and now I can't even get a desktop or even startx from the prompt.

Any ideas apart from a bullet to the head?!


Thanks!

---

### Post by decoherence on 2008-06-11
Huh.

So I take it you're dumped at a command line. Any experience with that?

You say you can't even so startx. What gets logged to /var/log/Xorg.0.log. This command should pull out anything interesting.

```
cat /var/log/Xorg.0.log | grep -E "(EE)|(WW)"
```

posting the results of that might give us a better idea of why startx doesn't work.

Too get gcc back, are you still online? try ```
ping www.ubuntu.com
```

If you're still online try running these commands ```
sudo apt-get update
sudo apt-get -f install
sudo apt-get install gcc
```

---

### Post by the_doc on 2008-06-11
I appreciate your reply.

I can try and ftp the contents of that log file if you like, but it basically says:

(WW) AIGLX: 3D driver claims not to support visual 0x23
(WW) AIGLX: 3D driver claims not to support visual 0x24
(WW) AIGLX: 3D driver claims not to support visual 0x25
(WW) AIGLX: 3D driver claims not to support visual 0x26
(WW) AIGLX: 3D driver claims not to support visual 0x27
(WW) AIGLX: 3D driver claims not to support visual 0x28

etc

(EE) intel(0): I830 vblank Pipe Setup Fialed 0
(EE) intel(0): I830 vblank Pipe Setup Fialed 0
(EE) intel(0): I830 vblank Pipe Setup Fialed 0

I tried to re-install gcc as you directed but I was told that I already had the latest version.

When I try startx I get a message that xauth is creating a new authority, then a message stating /etc/X11/X is not executable so something is giving up, then xinit says Connection refused then no such process.

Joy.

---

### Post by JoshuaRL on 2008-06-11
Well, if you're in the recovery console you'll need to log in first to startx.

---

### Post by the_doc on 2008-06-11
Yeah, I first log in then try to run startx.

---

### Post by gr4nf on 2008-06-11
try "CTRL+ALT+F7"

---

### Post by the_doc on 2008-06-11
From where, when logged into recovery mode?

---

### Post by decoherence on 2008-06-11
> **the_doc said:**
> I appreciate your reply.

I can try and ftp the contents of that log file if you like, but it basically says:


I wrote a post a while back on repairing X from the console. I used it to fix a different problem, but the commands are just a generic way to get X running.

[http://ubuntuforums.org/showthread.php?t=796322](http://ubuntuforums.org/showthread.php?t=796322)

All you need to worry about are the CODE parts. Just type 'em in same as those other commands.

---

### Post by the_doc on 2008-06-11
nvidia-xconfig

command not found.  I'm not sure nvidia is even the problem?

---

### Post by Inxsible on 2008-06-11
Try to reset your xorg.conf by this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` See if that works and gets you to X. Once in you can re-enable the nVidia drivers.

---

### Post by the_doc on 2008-06-11
I can now get as far as a blank screen with a mouse cursor in the middle?!

Thanks agian for all your help.

---

### Post by decoherence on 2008-06-11
> **the_doc said:**
> nvidia-xconfig

command not found.  I'm not sure nvidia is even the problem?

Oops! I should've checked my post better. My fault!

Anybody know the ati equivalent of nvidia-xconfig or if it is necessary?

If you ignore the error and run through the rest of the commands, does it work? If not, does any of the output from the previous "cat /var/log/Xorg.blah blah blah" change?

---

### Post by decoherence on 2008-06-11
> **the_doc said:**
> I can now get as far as a blank screen with a mouse cursor in the middle?!


Is this when you run startx, the last command from my other post (/etc/init.d/gdm start) or after a reboot?

We're making progress!

---

### Post by the_doc on 2008-06-11
After reboot and log on, then startx.


"cat /var/log/Xorg.blah blah blah" yeilds the same output.

---

### Post by Inxsible on 2008-06-11
> **the_doc said:**
> I can now get as far as a blank screen with a mouse cursor in the middle?!

Thanks agian for all your help.how did you get here? using dpkg-reconfigure or using decoherence's method? Please be specific so we know where you are at.

Getting a mouse pointer, means X has already started...although there is something that is still wrong since you can't see your desktop yet.....

---

### Post by the_doc on 2008-06-11
Sorry for the ambiguity. I followed decoherence's method (or most of it!), and now when I run startx I get the blank screen and cursor.

---

### Post by the_doc on 2008-06-11
Please don't interpret this as a sign of impatience or ingratitude for your help, but as this is a new laptop with zero user data to loose, I decided to do a factory restore (which I didn't know I could do).

I would like to thank the individuals that attempted to help me solve this poblem though!

---

### Post by Inxsible on 2008-06-11
> **the_doc said:**
> Please don't interpret this as a sign of impatience or ingratitude for your help, but as this is a new laptop with zero user data to loose, I decided to do a factory restore (which I didn't know I could do).

I would like to thank the individuals that attempted to help me solve this poblem though!Ouch !!

Factory restore would have given you only Windows right? So will you be installing Ubuntu all over again?

---

### Post by the_doc on 2008-06-11
No, it's preloaded with Ubuntu Gutsy with some kind of restrore partition.  I'm back to where I was this morning (when it was delivered!) with no CD needed!

---

### Post by the_doc on 2008-06-11
I know this is a bit of a stupid question, because if the causes where clear the answer would have been too, but....

What or who are the usual suspects for this kind of problem, I can't believe it was a GCC package install?!

---

### Post by decoherence on 2008-06-12
Glad to hear you're back up and running! Sorry for abandoning the thread -- i have a long commute home.

Anyway, the usual suspect when this happens is a binary video card driver. The way to confirm this is to configure X to use an open source driver, which is what running X --configure does.

The screen with the little X pointer on it is the x server running without any programs. When you typed startx, it couldn't read the file with information that tells it what programs to launch on startup, either because the file isn't there or another problem.

I would've been curious to see what running sudo /etc/init.d/gdm start would've done after your reboot but no matter. The important thing is you have a working computer again! :)

---

### Post by the_doc on 2008-06-12
decoherence, thanks again for your help and information!  

So would you recommend I switch to an open source driver?  I will use the laptop pretty much exlusively for programming and maybe watching the occasional DVD, I certainly don't need major graphics.  The graphics is onboard if that makes any difference.

---

### Post by decoherence on 2008-06-12
Well, it's ATI graphics, right? I don't have much experience with ATI anymore but as a general rule,

use the open source driver if you don't care about 3D acceleration or if the binary driver doesn't work properly, or if you're religious about things being open source. 

use ATI's binary driver for best performance, 3D and desktop effects. Also, if you find DVD playback sucks with the open source driver, switch to the binary one.

I generally use the binary nvidia driver until a kernel update breaks it. Then I switch to the open source driver and forget about it until I find I need fast openGL (usually for blender) then I run through those commands in my other post and it's back to the races. So it doesn't make a huge difference... it just depends on what you're using it for.

---

### Post by the_doc on 2008-06-12
Thanks again decoherence, you've taught me a few things over the course of this thread!

---

