---
title: "Is this worth all the trouble??"
date: 2020-04-25
forum: New to Ubuntu
---

### Post by spondifereye on 2020-04-25
So, for the past 4-5 years I've been really wanting to get Ubuntu installed on my computer and never had any success.
Every few months I would get the urge to do it, but I usually start running into problems almost immediately.
Well today was the day again. I was sure that there had to be some way I could finally get Ubuntu running so I could just try using it for a while to see how I liked it.
Of course I start running into problems out of the gate. I spent about 6 hours restarting my computer, using different USB drives, using different mounting software, using different USB ports, changing settings in my bios back and forth before finally a miracle happened. For the first time ever I saw the Ubuntu loading screen.
Great! Here we go I thought. Nope. Now that I finally got into Ubuntu I had to navigate my way around in crisp 640x480 resolution. I wanted to change it, but there were no other options.
Then I had to try and figure out how the partitioning and installation worked (actually pretty confusing), since I didn't want to overwrite my windows drive. Got it all done!
Well, It didn't work out exactly as I planned, since I wanted it to be set up so I can select which OS I want to run at start up, but no problem I can figure that out next.
First things first though, I need to fix the resolution issue. After updating to the latest Nvidia drivers (i think), I restarted and got to the log in screen. Looks like a good resolution so I'm happy. But of course, everything has to be broken when I want to try and do anything related to Ubuntu. I get stuck in a log in loop.
I looked all over the internet and found posts about some file called .Xauthority but I was never able to find that on my computer.

Now after wasting my entire day again, I'm sitting here wondering if this is even worth all the trouble. On one hand I made it further then I ever have in the past, but on the other hand I'm pretty tired and really not impressed by my experience again.

Sorry about the long post, I just wanted to share my crappy luck somewhere, and hope maybe someone can help/encourage me here.
Thanks.

---

### Post by yancek on 2020-04-25
You haven't posted any information on your hardware.  Some of the problems you report may be due to the hardware you have and posting that info may lead someone who has been successful with that hardware to post helpful information.

You neglected to indicate which windows you are using.  Ubuntu has had a site up for years explaining how to dual boot with windows 10, if that's what you are using.  Have you read it, link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by DuckHook on 2020-04-25
Welcome to the forums, spondifereye.

Likewise, I'm sorry to hear about your problems.

Note, however, the following:

[LIST]
[*]Windows does not reside happily with alternate OSes on the same HDD. Ubuntu has to fool it into thinking that it is king of the castle and the only thing on the HDD. In other words, you are already starting out at a level of complexity that puts Ubuntu (and your own efforts to install it) at an unfair disadvantage.
[*]Drivers are an acknowledged bugbear in Linux. Most OEMs do not release open-source drivers for Linux, so most drivers are reversed engineered by dedicated gurus with little help from manufacturers. Those manufacturers who do cooperate tend to include proprietary blobs so that distros like Ubuntu cannot include them as a matter of course. Their installation must be left as a choice for the user so that *you* decide if you are willing to taint your kernel.
[*]If you've had problems in the past, why haven't you made use of the forums before? I assume, from your recent date of membership, that you are a first time visitor. We can't help you if you don't ask.
[*]I don't recommend that Windows users start off by trying a dual boot install off the bat. Run Ubuntu in a VM. Get used to the OS before jumping in with both feet.
[*]Windows users, and especially power users, are often their own worst enemies when moving to Ubuntu. Windows teaches all sorts of bad habits. For example: downloading apps/drivers/utilities willy nilly from unknown and untrusted sites. That's the silo business model at work in proprietary software and it's unavoidable. However, such practices are bound to get you into trouble with Ubuntu.
[*]I highly recommend that you read the link in my sig: *Linux Is Not Windows*. In the absence of proper expectations and preparation, you are guaranteed to be disappointed.
[*]After reading *Linux Is Not Windows* please explain why you wish to explore Ubuntu? Purely as a personal opinion (and notwithstanding that Mrs DuckHook happily uses Ubuntu exclusively with absolutely no knowledge of the command line), Linux is at heart a geek OS. If all you want to do is play games, or surf, or use standard commercial apps and software, there is not really much compelling reason to switch from Windows. On the other hand, if you wish to have the liberty to customize to your heart's content, or make use of power that Windows users can only dream of, or explore the guts of an OS without being stymed by hidden secrets, then Linux delivers in ways that Windows simply can't.
[/LIST]

---

### Post by TheFu on 2020-04-25
For people unfamiliar with Unix, there is a steep learning curve for any Unix-like OS.  

For those people, it is best to find a LUG - Linux Users Group - and get 1-on-1 help, in person
or
buy a computer with Ubuntu pre-installed just like most of the world does with MS-Windows.

imho, the best way to get over the initial learning curve is to use a virtual machine installation for the first 6 months or so.  VMs bypass any major HW issues because only virtual hardware is seen.  Most people going this route, use virtualbox if they are running Windows as their hostOS. This is the low risk way to try any linux since the storage is pre-allocated and won't touch any existing boot setup.  The GPU drivers have nothing to do with the physical GPU is the system - everything is virtual.

The 20.04 release notes explain some of the caveats about using nvidia GPUs.  [https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

---

### Post by spondifereye on 2020-04-25
> **yancek said:**
> You haven't posted any information on your hardware.  Some of the problems you report may be due to the hardware you have and posting that info may lead someone who has been successful with that hardware to post helpful information.

You neglected to indicate which windows you are using.  Ubuntu has had a site up for years explaining how to dual boot with windows 10, if that's what you are using.  Have you read it, link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

My bad.

Windows 10 64-bit
Asus x-570i Motherboard
Ryzen 9 3900x
GTX 1080
32gb Corsair ram

The HD I have installed Ubuntu on is an old corsair 400gb ssd.

I have read through that link, that was what I was following to install.


> **DuckHook said:**
> Welcome to the forums, spondifereye.

Likewise, I'm sorry to hear about your problems.

Note, however, the following:

[LIST]
[*]Windows does not reside happily with alternate OSes on the same HDD. Ubuntu has to fool it into thinking that it is king of the castle and the only thing on the HDD. In other words, you are already starting out at a level of complexity that puts Ubuntu (and your own efforts to install it) at an unfair disadvantage. 
[*]Drivers are an acknowledged bugbear in Linux. Most OEMs do not release open-source drivers for Linux, so most drivers are reversed engineered by dedicated gurus with little help from manufacturers. Those manufacturers who do cooperate tend to include proprietary blobs so that distros like Ubuntu cannot include them as a matter of course. Their installation must be left as a choice for the user so that *you* decide if you are willing to taint your kernel. 
[*]If you've had problems in the past, why haven't you made use of the forums before? I assume, from your recent date of membership, that you are a first time visitor. We can't help you if you don't ask. 
[*]I don't recommend that Windows users start off by trying a dual boot install off the bat. Run Ubuntu in a VM. Get used to the OS before jumping in with both feet. 
[*]Windows users, and especially power users, are often their own worst enemies when moving to Ubuntu. Windows teaches all sorts of bad habits. For example: downloading apps/drivers/utilities willy nilly from unknown and untrusted sites. That's the silo business model at work in proprietary software and it's unavoidable. However, such practices are bound to get you into trouble with Ubuntu. 
[*]I highly recommend that you read the link in my sig: *Linux Is Not Windows*. In the absence of proper expectations and preparation, you are guaranteed to be disappointed. 
[*]After reading *Linux Is Not Windows* please explain why you wish to explore Ubuntu? Purely as a personal opinion (and notwithstanding that Mrs DuckHook happily uses Ubuntu exclusively with absolutely no knowledge of the command line), Linux is at heart a geek OS. If all you want to do is play games, or surf, or use standard commercial apps and software, there is not really much compelling reason to switch from Windows. On the other hand, if you wish to have the liberty to customize to your heart's content, or make use of power that Windows users can only dream of, or explore the guts of an OS without being stymed by hidden secrets, then Linux delivers in ways that Windows simply can't. 
[/LIST]


Actually I'm just a lowly 4th year CS student and I have used Ubuntu a bit. A few of my classes were done entirely in it so I do have some experience with Ubuntu, but mostly I know how to get my projects/assignments done and get out. I haven't had it installed on my own computer where I give it a fair chance so I'd like to do that.

Mainly I want to practice programming in a linux environment, and play around to see what I can do with the OS. I always hear that you can customize and do lots of fun things with it and I'd like to see exactly what they mean by that.

I'd really like to get away from windows tbh. Unfortunately I can't separate completely since I do like playing games and stuff and I know Linux isn't quite there yet on that front. But I'm really just sick of doing a fresh install of Windows and having my computer full of all the junk software I don't want. I have to spend hours after every clean install just to turn off all the garbage settings that get auto-enabled, and uninstalling all the stuff I don't want. Not to mention that some of it can't be uninstalled and will just reinstall itself if you try.

---

### Post by spondifereye on 2020-04-25
> **TheFu said:**
> For people unfamiliar with Unix, there is a steep learning curve for any Unix-like OS.  

For those people, it is best to find a LUG - Linux Users Group - and get 1-on-1 help, in person
or
buy a computer with Ubuntu pre-installed just like most of the world does with MS-Windows.

imho, the best way to get over the initial learning curve is to use a virtual machine installation for the first 6 months or so.  VMs bypass any major HW issues because only virtual hardware is seen.  Most people going this route, use virtualbox if they are running Windows as their hostOS. This is the low risk way to try any linux since the storage is pre-allocated and won't touch any existing boot setup.  The GPU drivers have nothing to do with the physical GPU is the system - everything is virtual.

The 20.04 release notes explain some of the caveats about using nvidia GPUs.  [https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

I hadn't seen the release notes. Looks like that nvidia auto-login bug might be my problem.

---

### Post by rbmorse on 2020-04-25
You can recover from the auto login bug fairly easily.  Boot to the password dialog, but rather than entering a password press and hold the <ctrl><alt><F3> keys in sequence. This opens a terminal.  Login with your user credentials.  At the prompt (blinking underline)  run the command:

```
sudo apt install lightdm
```

at some point you will be asked to chose between gdm3 and lightdm.   Chose lightdm and press the <tab> key to move the cursor to the OK box and <enter>.  When the installation is finished reboot the machine:

```
sudo reboot -n
```

The login should now accept your password.  

Once you're running, open settings, go to user, go to your user and deselect the option to log in automatically. 

If for some reason you don't want to use lightdm and return to gdm3, you can rerun the setting from the console with the command:

```
sudo dpkg-reconfigure lightdm
```

and select gdm3 when prompted.  Reboot the system to make the change effective.

---

### Post by TheFu on 2020-04-25
> **spondifereye said:**
> I hadn't seen the release notes. Looks like that nvidia auto-login bug might be my problem.

Using auto-login is a bad habit to start.  Don't.  No job will allow that and at some place you will be fired for leaving your workstation unlocked to visit the toilet.

---

### Post by spondifereye on 2020-04-25
> **rbmorse said:**
> You can recover from the auto login bug fairly easily.  Boot to the password dialog, but rather than entering a password press and hold the <ctrl><alt><F3> keys in sequence. This opens a terminal.  Login with your user credentials.  At the prompt (blinking underline)  run the command:

```
sudo apt install lightdm
```

at some point you will be asked to chose between gdm3 and lightdm.   Chose lightdm and press the <tab> hkey to move the cursor to the OK box and <enter>.  When the installation is finished reboot the machine:

```
sudo reboot -n
```

The login should now accept your password.  

Once you're running open settings, go to user, go to your user and deselect the option to log in automatically. 

If for some reason you don't want to use lightdm and return to gdm3 you can rerun the setting from the console with the command:

```
sudo dpkg-reconfigure lightdm
```

and select gdm3 when prompted.  Reboot the system to make the change effective.

Great! That worked and I'm finally logged in! Thanks a lot.

---

