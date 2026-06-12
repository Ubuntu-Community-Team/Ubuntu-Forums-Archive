---
title: "UBUNTU / Windows"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by Faan on 2012-01-20
I have been using UBUNTU now for more that a year and it is running smoothly.  Right in  the beginning I battled quite a lot, but came right slowly.

it is also important to say that I use the PC to do some other work and do not have the time to go in detail in my research into a problem I might experience.

Originally it was possible for me to switch between UBUNTU and Windows.  Something went wrong and I had to install everything again, but this time could not switch any more.  Much of the work I had om my PC was lost.  I have 2 hard drives of 80gb each on the PC.  The one drive is partitioned and I think UBUNTU is on one partition. 
 
I also installed Virtual Box in order to be able to use Windows and associated programs.  However when I use this the PC becomes very slow to such an extent that I rather close VB in order to carry on with my work.  I thought of doing away with the partitioning, but do not know how and do not want to experiment and loose everything again.

I also have a few programs which require a Windows OS and because of this cannot use them on this particular PC, but have to go to my laptop every time I need to do something.

What I am trying to say with all of this is that I am not far from the point of taking a decision to do away with UBUNTU and switch back to Windows.
Is there someone who can convince me otherwise?

---

### Post by _0R10N on 2012-01-20
Well, there's no such thing as trying to convince you. You should convince yourself of what is more appropiate to you, based on your needs. So, if you need to run apps Windows specific and you aren't able to run it using wine, then it's clear which path you should take.

I'm with you in what respects to having only one OS installed in your system. Years ago I chose Linux (Fedora first, and Ubuntu later on).

I would also recommend you to think about what took you to install Ubuntu in the first place.

regards!

---

### Post by Zill on 2012-01-20
> **Faan said:**
> ...Much of the work I had om my PC was lost...
I am sorry about the problems you have experienced but the best advice I can give is to *always* ensure you have good backups.  Computer parts can, and do, fail.  Similarly, software bugs always exist that, along with simple "finger trouble" *can* cause loss of data.  So, if the worst comes to the worst with good backups you can always get everything back.
> **Faan said:**
> ...I also have a few programs which require a Windows OS...
If these programs do not run under wine then you either need to dual boot or run a virtual machine.  You do not seem to be happy with Ubuntu and therefore if you *really* prefer to stick to Windows then this is perhaps your best option.

Personally, I have no need for *any* Windows programs and so have been happily using Linux-only systems for around six years now.  However, my advice is to use what works for you - Ubuntu is not always best for everyone.

---

### Post by mastablasta on 2012-01-20
there are many great linux alternatives to windows specific applicaitons. some are better than windows counterpart. however not all applicaitons have alternatives. So if you use mostly only windows based applicaitons then use windows.
 
as i see the biggest problem are games and certain specific software that was designed to run on windows only.

---

### Post by Mark Phelps on 2012-01-20
> **Faan said:**
> What I am trying to say with all of this is that I am not far from the point of taking a decision to do away with UBUNTU and switch back to Windows.
Is there someone who can convince me otherwise?

I don't believe in trying to convince folks either way.

You need to do what works best for you -- and the more you have to rely on specific Windows-only apps on a daily basis, the more difficult it will be to switch to something else and abandon Windows.

Only you can decide if the effort needed to switch is worth it.

---

### Post by Faan on 2012-01-23
Thanks very much for all the feedback.

The idea with the post was not not get someone to try and convince me either way.

I cannot remember when I last played a game on the PC.  I use the machine for work purposes and I think that is for about 80% of the time.

I have one particular program which I use fairly often and that requires a  Windows OS and I took it up with the developer and the reply was that they are doing much more important work at present to be concerned about linux.  I am probably the only one out of 2000 users requiring a linux capability.

I have noticed you guys refer to wine and I see I have it installed, but I have no idea what it is for or how it works. Secondly I am concerned that I try to use it and "blow-up" everything.  Is there a difference between wine and virtual box?

I would prefer to remain on UBUNTU, but I lack the knowledge to be able to help myself when I get stuck with a particular problem.

About a year ago I posted on the forum about me not being able to send faxes from my PC as I could previously - I still cannot do it. The replies were fairly technical and I just could not resolve the problem.

As mentioned I think that UBUNTU is on a partition of one hard drive together with windows. As mentioned I have two hard drives and would prefer to have the OS on the two separate hard drives (80gb ea) so that I have more space on a particular drive. The drive on which UBUNTU is is getting full & I just do not know how to go about doing it.

As I mentioned to someone this morning I have work to do and do not have the time to use two or three hours every time to try and sort out what the best OS and accompanied programs are to try and resolve a particular technical problem.

---

### Post by Basher101 on 2012-01-23
i see your concerns..

wine is not virtualbox, it just allows you to install and run windows programs and .exe files in a linux environment. I have yet to see someone bust their system using wine...

to help you with your partitions, can you install Gparted, run it and make a screenshot from your partition setup? It will display your first hard drive by default, to make a screenshot of the other one you must click the small tab at the top right that says "/dev/sd[COLOR="Red"]a[/COLOR]" or "/dev/hd[COLOR="red"]a[/COLOR]" and choose "/dev/sd[COLOR="red"]b[/COLOR]" or "/dev/hd[COLOR="red"]b[/COLOR]" respectiveley. Do not worry if its sda or hda, the device names vary from system to system. Just choose the one with "b" at the end and it will show you your second hard drive (if you have no usb sticks connected). Make screenshots of both hard drives' partition setup and post them here.

regards

---

### Post by mastablasta on 2012-01-23
> **Faan said:**
> I have noticed you guys refer to wine and I see I have it installed, but I have no idea what it is for or how it works. Secondly I am concerned that I try to use it and "blow-up" everything. Is there a difference between wine and virtual box?
 .
 
wine is not an emulator. :-)
 
it adds reverse engineered windows libraries so you can use windows programmes in linux. you install porgrammes by 
wine [*programme]*
 
or you can type wine in terminal and then press space and just click on install.exe file drag it to terminal and drop it there. it will then install it. if all goes well that is. not all windows progs work in Linux. anyway if all goes well you will get an icon that launches the programme.
 
you could give it a try. programme would install and work only in wine. i doubt you could blow anything up with it. unless the programme is designed to remotely trigger something ;-)

---

### Post by grahammechanical on 2012-01-23
What was it that went wrong? Was it with Windows? Or was it with Ubuntu?

And if you are really so busy that you do not have the time to solve issues, then I am just too busy to offer a solution.

Regards.

---

### Post by Faan on 2012-01-23
I will try and reply as I go along.
the screenshots:

/home/faan/Desktop/Screenshot-1.png

and the 2nd:
/home/faan/Desktop/Screenshot.png

When I installed UBUNTU the 1st time everything went well.  When I booted up I was given the choice of going to windows or ubuntu.  When I wanted to go to the other one I just had to log out of the one and log into the other.  Then it started going slower and not always showing the full screen.  Then one morning when I booted up just no screen whatsoever.  As I do not know any one nearby  I could not phone for help. The person I go when there was a windows problem does not anything about ubuntu.  He has an internet cafe and sells and repair hardware and does a very good job.

mastablasta I am afraid, if you are prepared. you have to tell me about wine in plain English again.  Are you saying I have to open wine and then install whatever windows programme I need through wine or should I install and then run it through wine?

---

### Post by Faan on 2012-01-23
I thought the screenshots would show, but obviously not.  What do I have to do?

---

### Post by Basher101 on 2012-01-23
at the bottom where you write a post, there is a button called "manage attachments". its pretty self-explaining from there

---

### Post by Faan on 2012-01-23
I hope it works.

---

### Post by Paddy Landau on 2012-01-23
Faan, I think rather than anyone try to convince you of something, what you really need is a solution to your problem.

[LIST]
[*]You cannot use Virtual Box, as you have explained, because your computer is not powerful enough to run both Windows and Ubuntu at the same time (you really need 64-bit Ubuntu and at least 6Gb RAM on a modern computer). Dual-boot would be a far better option.
[/LIST]

[LIST]
[*]If you wish to retain dual-boot Windows and Ubuntu, start a new thread asking for help to resurrect your computer with that.
[/LIST]

[LIST]
[*]If you wish to try Wine, I strongly recommend that you use [PlayOnLinux]("http://www.playonlinux.com/") instead (you can install it from the Ubuntu Software Centre). Wine is quite complicated to set up, but PlayOnLinux is a front-end for Wine that hides its complexity. I use a Windows program on Wine, even though I have no idea how to use Wine, because I use PlayOnLinx to set it up for me.

However....

Be aware that Wine is an imperfect solution. Some Windows programs work perfectly on Wine; some work with restrictions; and most do not work at all. Search [Wine's database]("http://appdb.winehq.org/") to check whether or not your program works (if it's not listed, it probably won't work).
[/LIST]

---

### Post by Basher101 on 2012-01-23
i would also suggest on trying to repair your dualboot. 

Looking at your partitions it looks like your windows is still intact. What is the output from ```
sudo update-grub
``` this command? this will read all bootable images on all devices (you should get 4 grub entries from ubuntu) 1. is ubuntu itself, 2. is ubuntu recovery, 3. and 4. are memtest. In the ideal scenario you should get a fith entry for windows...

---

### Post by Faan on 2012-01-23
> **Basher101 said:**
> i would also suggest on trying to repair your dualboot. 

Looking at your partitions it looks like your windows is still intact. What is the output from ```
sudo update-grub
``` this command? this will read all bootable images on all devices (you should get 4 grub entries from ubuntu) 1. is ubuntu itself, 2. is ubuntu recovery, 3. and 4. are memtest. In the ideal scenario you should get a fith entry for windows...


I found this: (I am not sure whether this is what you asked me to do)

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

I would be very happy if I could get the dual boot back again and will raise this question in a new thread.

I also downloaded the PlayOnLinux and will play around with it in the morning.

Thanks for all the help so far.

---

### Post by Basher101 on 2012-01-23
well it looks pretty simple to me...your Grub is full of older kernel images since you made alot of updates. As far as i know, grub has a limit of how many entries it displays. So all you have to do is uninstall all the older kernels and just re-update grub with the command and you should be able to boot windows again..

you should uninstall all the kernels with the Synaptic Package manager, once you run it simply type in the search box at the top the kernel versions you want to uninstall (one at a time) > 2.6.35-28 all installed kernels are marked with a green square to the left. Right click them and "mark for uninstallation". Once you marked all you want to get rid of, (**_do not delete the current one you are using!!!_** in your case it is the kernel version [COLOR="Red"]**2.6.38-13**[/COLOR]) click the small arrow at the top to apply.

then reuse ```
sudo update-grub
``` and you're done

---

### Post by Faan on 2012-01-24
Basher101, I did what you said and this is what it looks like now. I just hold thumbs when I reboot.
Thanks


Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

---

### Post by Faan on 2012-01-24
Reboot was successful, but have not tried Windows yet.

---

### Post by mastablasta on 2012-01-24
sweet! now post another thread in wine section of forums if you have difficulty with getting your application to work in Wine (or PlayonLinux). if you use play on linux things are a bit easier to set up.
 
but Wine is also not that difficult. it can just be overwhelming for newcommers and when specific settings need to be made on install.

---

### Post by Paddy Landau on 2012-01-24
> **Faan said:**
> ... will raise this question in a new thread.
If you post the link to the new thread here, we can know where to find it.

> **Faan said:**
> Reboot was successful, but have not tried Windows yet.
Great! If you feel this thread has run its course, please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Faan on 2012-01-25
When I boot up I am given the choice of either UBUNTU or Windows, but the last is very slow and I think a bit or more than a bit damaged.  Have not had time to attend to it.

---

### Post by ianp5a on 2012-01-25
Take a look a [PlayOnLinux.]("http://www.unixmen.com/install-ms-office2007-on-ubuntu-using-playonlinux/") This makes installing many Windows programs on Linux very easy.
I think it might use Wine in the background. But anyway I added MS Office and a few other windows programs very easily. They are installed as if they were ordinary Linux programs.

---

### Post by Faan on 2012-01-25
> **ianp5a said:**
> Take a look a [PlayOnLinux.]("http://www.unixmen.com/install-ms-office2007-on-ubuntu-using-playonlinux/") This makes installing many Windows programs on Linux very easy.
I think it might use Wine in the background. But anyway I added MS Office and a few other windows programs very easily. They are installed as if they were ordinary Linux programs.

I installed PlayOnLinux, but I am not sure how to go about installing MS software.  
Perhaps I should post this in a new thread which I did and it is here:

[http://ubuntuforums.org/showthread.php?p=11639005#post11639005](http://ubuntuforums.org/showthread.php?p=11639005#post11639005)

---

