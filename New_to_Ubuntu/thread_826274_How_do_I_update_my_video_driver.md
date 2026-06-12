---
title: "How do I update my video driver?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by kanati on 2008-06-11
Hi,
   I've got Ubuntu 8.04 running off a GeForce 8800GT.  The driver that was installed by default was version 169.12, the same driver currently in the repositories.  Unfortunately Compiz-Fusion is a little sluggish at the moment (especially with the window effects), it runs smoother on the Intel X3100 in my laptop.  Apparently the new version of the driver, 173.14.05, has a bunch of performance fixes for the 8000 series graphics cards.  I've downloaded the driver from the Nvidia website but I haven't a clue how to go about installing it.  According to the Nvidia howto I have to disable X, and then change the run level so that X doesn't restart on the next boot.  Problem is, I don't what that means:(.  Can anyone give me a hand?

---

### Post by gr4nf on 2008-06-11
Here is what you do:
```

sudo mv /etc/rc3.d/S10xserver-xorg-input-wacom /etc/rc3.d/K10xserver-xorg-input-wacom
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K30gdm

```
this will make it so that X doesnt start on boot. Install the driver afterwards. You will have nothing but a command line. Do you have another computer that you can get support from while using the other? if not, then you may not want to do this, as it will require CLI knowledge.

---

### Post by Victormd on 2008-06-11
Or you can see if envyng has the updated driver and install from there...

---

### Post by overdrank on 2008-06-11
> **kanati said:**
> Hi,
   I've got Ubuntu 8.04 running off a GeForce 8800GT.  The driver that was installed by default was version 169.12, the same driver currently in the repositories.  Unfortunately Compiz-Fusion is a little sluggish at the moment (especially with the window effects), it runs smoother on the Intel X3100 in my laptop.  Apparently the new version of the driver, 173.14.05, has a bunch of performance fixes for the 8000 series graphics cards.  I've downloaded the driver from the Nvidia website but I haven't a clue how to go about installing it.  According to the Nvidia howto I have to disable X, and then change the run level so that X doesn't restart on the next boot.  Problem is, I don't what that means:(.  Can anyone give me a hand?

Hi and use the ctrl, alt, F1 keys and this will bring you to the terminal. The login and change directory to where the file is located. If it on your desktop then ```
cd ~/Desktop
``` then you can stop x with the command
```
sudo /etc/init.d/gdm stop
``` then enter the command
```
sudo sh "name of the file"
``` then enter. When complete you can use the command to start x. ```
sudo /etc/init.d/gdm start
```

---

### Post by Joeb454 on 2008-06-11
I think overdranks method would work just fine (unless you have to reboot during the install, in which case you would need to change some run level options :))

---

### Post by kanati on 2008-06-11
Thanks for the help so far.  So I started the installer, but I got the following error message:

"error: you do not appear to have libc header files installed on your system. please install your distribution's libc development package". 

 Any ideas?

---

### Post by Joeb454 on 2008-06-11
```
sudo apt-get install build-essential libc6.1-dev
``` That should work :) The 1st part is just to make sure you have the required stuff for compiling anything (in case you need to)

---

### Post by kanati on 2008-06-11
okay, I tried that and it pointed me to a package called linux-libc-dev instead, it claims that libc6.1-dev no longer exists

---

### Post by Joeb454 on 2008-06-11
Did you try installing linux-libc-dev instead?

---

### Post by kanati on 2008-06-11
yep, I typed "sudo apt-get install build-essential linux-libc-dev", it then did a whole bunch of things so I assume that means it worked

---

### Post by aktiwers on 2008-06-11
Hi

Do like this  to install the newest version Manually.
1.) First install some libs and compiling tools:
 ```
sudo aptitude install libc6 libc6-dev
``````
sudo aptitude install build-essential linux-headers-$(uname -r);
```2.) Now Log out.

3.) Hit CTRL+ALT+F1 and login.

4.) Download the latest driver:
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/NVIDIA-Linux-x86-173.14.05-pkg1.run
```5.) Stop GDM (this is required for the installer to run):
```
sudo /etc/init.d/gdm stop
```6.) Make the downloaded file executable:
```
sudo chmod +x NVIDIA-Linux-x86-173.14.05-pkg1.run
```7.) And then run the file:
```
sudo ./NVIDIA-Linux-x86-173.14.05-pkg1.run
```8.)After that reboot the computer
```
sudo reboot
```You should now have the latest drivers

---

### Post by kanati on 2008-06-11
so I should hopefully be set to continue, but I just want to clarify a few things first:  from what I can tell this is the order I should do things in...

1.ctrl, alt, F1 keys to get to the CLI
2.Navigate to desktop [cd ~/Desktop]
3.Stop X [sudo /etc/init.d/gdm stop]
4.Start installer [sudo sh ...]
5.Stop X from starting on the next boot 
[sudo mv /etc/rc3.d/S10xserver-xorg-input-wacom /etc/rc3.d/K10xserver-xorg-input-wacom
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K30gdm]
6.Restart the computer (how do I do this from the CLI)
7. Once the computer is restarted and the driver is fully installed, restart X using [sudo /etc/init.d/gdm start]

Is that right? Thanks for all the help so far.

---

### Post by kanati on 2008-06-11
thanks aktiwers, didn't see that till after I submited my last post

---

### Post by aktiwers on 2008-06-11
It will be enough to do like I did.. why stop X from starting next boot?

You could also download the driver manually with here:
[http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html)

Instead of step 4 in my guide, then just remember to save the file in your home folder.

---

### Post by kanati on 2008-06-11
huh, so the command to reboot is sudo reboot...

the hardest part about unix is realizing just how simple it really is

---

### Post by Joeb454 on 2008-06-11
To restart your computer - ```
sudo shutdown -r now
``` Will shut it down immediately, then restart it :)

---

### Post by kanati on 2008-06-11
> **aktiwers said:**
> It will be enough to do like I did.. why stop X from starting next boot?

You could also download the driver manually with here:
[http://www.nvidia.com/object/linux_display_ia32_173.14.05.html](http://www.nvidia.com/object/linux_display_ia32_173.14.05.html)

Instead of step 4 in my guide, then just remember to save the file in your home folder.

The readme on the NVIDIA website said to stop X on the next boot, not sure why :confused:

---

### Post by aktiwers on 2008-06-11
Don't worry about it.. I have done it this  tons of time.. my guess is that nvidia is wrong :D
Probably because the installer needs X to be closed (it will be closed with GDM in step 5)

---

### Post by kanati on 2008-06-11
hmmm, I followed your instructions, it installed completely and I rebooted my system, but now it's in low graphics mode.  any idea what  went wrong?

---

### Post by aktiwers on 2008-06-11
Did you run those "disable X" commands you read about in the ReadMe?
Because I don't know those commands..

Can you post the output of:
```
lspci | grep -i vga
```

---

### Post by kanati on 2008-06-11
i just ran exactly what you had in your earlier post

and

"04:00.0 VGA compatible controller: nVidia Corporation GeForce 8800gt (rev a2)"

---

### Post by kanati on 2008-06-11
I just tried launching the Nvidia-settings server, and it gave me this message:  'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

but...

under Hardware Drivers the NVIDIA accelerated graphics driver is checked and in use

any idea what's up?

---

### Post by aktiwers on 2008-06-11
Okay try running:
```
sudo nvidia-xconfig
```

And restart X afterwords (CTRL+ALT+BACKSPACE)

---

### Post by aktiwers on 2008-06-11
If this doesn't fix it, I think we might need to remove the old drivers. Normally the installer just overwrites them though..

Let me know how it's working out for you so fare .

---

### Post by nhasian on 2008-06-11
yes i noticed this as well.  How do you see what nvidia driver version I have installed?  I'm using the proprietary drivers not the free ones and I have checked in the add/remove applications "NVidia binary X.Org driver ('new' driver)"

those instructions look pretty complicated.  what are the odds a new version will be available in the repository sooner or later?

> **kanati said:**
> The driver that was installed by default was version 169.12, the same driver currently in the repositories.  Unfortunately Compiz-Fusion is a little sluggish at the moment

---

### Post by aktiwers on 2008-06-11
> **nhasian said:**
> yes i noticed this as well.  How do you see what nvidia driver version I have installed?  I'm using the proprietary drivers not the free ones and I have checked in the add/remove applications "NVidia binary X.Org driver ('new' driver)"

those instructions look pretty complicated.  what are the odds a new version will be available in the repository sooner or later?

This is how you check your version:
```
cat /proc/driver/nvidia/version
```

But really its not very complicated..  It's installing the tools needed and then downloading a file. Then the installer requires you to close X and so you do.

It's not as complicated as it might look. But I am off to bed now.. let us know how everything goes.

---

### Post by nhasian on 2008-06-11
crap the same thing happened to me.  after following the instructions when ubuntu starts it says "Ubuntu is running in low-graphics mode"

the only thing i can think of is the last step of the driver installation tool said it needed to make changes to the x config or something and it said it backed up the original.  

so i'm stuck in low res mode, i cant get back to high res glory.  Here's the output of: 

> lspci | grep -i vga

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)

and the output of:  > cat /proc/driver/nvidia/version

NVRM version: NVIDIA Linux x86 Kernel Module  71.86.04  Mon Jan 21 11:22:18 PST 2008
GCC version:  gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)


> **kanati said:**
> hmmm, I followed your instructions, it installed completely and I rebooted my system, but now it's in low graphics mode.  any idea what  went wrong?

---

### Post by kanati on 2008-06-12
I booted into safeboot and selected the repair X option.  That got me out of low graphics mode.  Then I tried to re-enable the restricted driver, which messed it up pretty badly (the image on the screen was completely garbled).  So I just finished reformatting Ubuntu (I hadn't done much on it yet anyways).  

So now I have a completely clean install, I haven't enabled the restricted NVIDIA driver yet.  Should I try the same thing again and see if it works this time?  Or is there another way that might be better?

I don't mind reformatting this thing over and over till I get it right.  It's all part of the learning process :D

---

### Post by kanati on 2008-06-12
And just so you know where I stand:

```
dan@dan-desktop:~$ lspci | grep -i vga 
04:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
dan@dan-desktop:~$ cat /proc/driver/nvidia/version
cat: /proc/driver/nvidia/version: No such file or directory
dan@dan-desktop:~$ 
```

---

### Post by aktiwers on 2008-06-12
I would go for it! 
But I am getting afraid that it could be due to your video card. I have never installed drivers for such new cards. But I really doubt this should be the issue. 

Try it out and let us know how it goes :)

Nhasian:
Did you get any errors while installing the downloaded drivers?

---

### Post by kanati on 2008-06-12
```
dan@dan-desktop:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.05  Mon May 19 00:06:12 PDT 2008
GCC version:  gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
```

:D worked like a charm this time!

Thanks for all the help!

---

### Post by aktiwers on 2008-06-12
Great !
And welcome to Ubuntu by the way.

Remember to ask if you have any other questions :)

---

### Post by kanati on 2008-06-12
Unfortunately I jumped to conclusions.  After installing the video driver I ran the Ubuntu update program, it installed 160 updates and then when I restarted I was back to low graphics mode.  I'm thinking that this new driver is not compatible with one of the updates, any idea which one that could be?

I've reformatted and reinstalled again, this time I'm going to install the driver and then reboot my computer a bunch of times to make sure the driver is working properly, if that all works then hopefully someone can help me determine which updates to avoid.

---

### Post by philinux on 2008-06-12
I was just about to post this.

Any kernel update will mean you have to reinstall the driver now.

I'm guessing you've got the proposed repo ticked, Bad idea as new kernel family keeps popping up.

---

### Post by philinux on 2008-06-12
You need to follow the end of this guide from

Starcannon

You wont need step 10 as you've already done this.

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.

---

### Post by kanati on 2008-06-12
Okay, so I should run the updates first then?  

And when I'm asked to reconfigure X I should say no as opposed to yes right?

> I'm guessing you've got the proposed repo ticked, Bad idea as new kernel family keeps popping up. 
I'm not sure what you mean by that.

---

### Post by kanati on 2008-06-12
Just to let you know where I am at the moment.  I've just reinstalled Ubuntu, so as of right now I've done absolutely nothing except use firefox.

---

### Post by philinux on 2008-06-12
Does the nvidia driver work at the moment or not?

sorry just read you thread again,

Clean install no Hardware Drivers installed correct.

---

### Post by kanati on 2008-06-12
At the moment I'm not using it.  Or at least under System>Administration>Hardware Drivers the NVIDIA accelerated graphics driver is not in use.  I know that driver works, but it's the older 169.12 version and I want to be using the 173.14.05 driver because (according to NVIDIA at least) it has a number of performance fixes for the 8000 generation video cards.


Sorry if I sound like I don't really know what I'm doing. I'm still at the bottom of the Linux learning curve.

---

### Post by kanati on 2008-06-12
yep, nothing but what was on the disk

---

### Post by philinux on 2008-06-12
[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

Well if you follow this guide you should get the 173.14.05 then.
This is what i did and all fine. Except if there is a kernel update. Then the driver needs to recompiled against the new kernel. That is the downside.

I think the only thing extra you'll need is nvidia-settings after you've got the drive installed.

---

### Post by sdennie on 2008-06-12
I would install the nvidia drivers from the nvidia site as people have recommended above.  To prevent them from being clobbered every time you reboot, follow the instructions in this post: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2)

---

### Post by kanati on 2008-06-12
Okay, so I should install the updates first then, so that the driver can recompile itself against the new kernel?

---

### Post by nhasian on 2008-06-12
Thankfully i didnt need to do any reinstalling.  I've been using Ubuntu as my primary desktop since hardy heron came out and i've got all my apps and settings just right :)

I followed Starcannon's guide from beginning to end and to my pleasant surprise i saw the nvidia logo appear as x-Windows started.  woot!

now when i type cat /proc/driver/nvidia/version i get:

NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.05  Mon May 19 00:06:12 PDT 2008


If i understand this correctly, if i update my kernel in the future i would need to compile a new module right?  so would I simply run:

```
sudo nvidia-installer --update
```




> **aktiwers said:**
> Nhasian:
Did you get any errors while installing the downloaded drivers?

---

### Post by philinux on 2008-06-12
> Okay, so I should install the updates first then, so that the driver can recompile itself against the new kernel?

Correct, however I got my driver from Nvidia website. It still gets clobbered with a kernel update.

The only way to avoid this is to install the older driver from the repo.

---

### Post by philinux on 2008-06-12
> **nhasian said:**
> 


If i understand this correctly, if i update my kernel in the future i would need to compile a new module right?  so would I simply run:

```
sudo nvidia-installer --update
```

This sounds good. I'll try it after kernel ....19 comes through.

---

### Post by philinux on 2008-06-12
Eh thats good.

Try 

man nvidia-installer

---

