---
title: "How to lower cpu speed?"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by neo1691 on 2012-02-09
My processor have a very bad habit of getting heated up very frequently and then the fan blows like a tornado!!:p

So to cope up with that i had to go to advanced power settings and **reduce the maximum power state to 90%** instead of 100%.

[IMG]http://i.minus.com/iKR6XX1lgaVYk.jpg

I am going to format my whole system today, as i am affected with W32.Xpaj.B virus.. (a frest start :D) So yesterday just to give ubuntu v11.04 a try i installed it within windows and booted it, and the processor went crazy and got so heated up that windows had to shut itself down in order to save itself from any damages..

**_So my question is how can i reduce the same processor power state in ubuntu??_**


Also i am going to keep a separate partition of 50gb and will try to install ubuntu in that.. I have already tried that twice before but i messed up with that swap and /o or /r or /home thing.. 

So can anyone please would share any proper link regarding the same?? Something like [this]("http://www.ehacking.net/2011/06/how-to-install-backtrack-5-dual-boot.html") for backtrack?
or should i follow the same steps??

Thank you in advance!!

---

### Post by mörgæs on 2012-02-09
There are several reasons for overheating. First, please give a complete hardware description.

---

### Post by gbrowning on 2012-02-09
Slowing your computer may help but I would recommend trying a few other solutions.
1)  clean the dust out of your computer.
2) ensure there is plenty of air flow around your computer....if it is a laptop use it on a hard surface  e.g. not on a pillow on your lap, on a tray instead.
3) The fan is running but is it moving air?  Look at the computer an make certain the air is moving in a way that actually carries heat away from the cpu/memory/video-card.
4) Check that the fan/cooler is mounted properly to the CPU...be careful not to do anything that flexes the motherboard.
5) If all these things seem correct go to the store for "thermal paste", unmount the Fan/cooler (blow the dust out of it again while you can get to it from all angles) scrape all the thermal compound off the CPU and off the Fan, clean the mating surfaces, add new thermal compound just a little dab will do you, then re-mount the fan/cooler making sure no wires or cables interfere with the mechanism.

Light it up and go for a spin, this should work and your computer will still be at full speed.  Unless you are overclocked it is unlikely the speed of your CPU is the problem.

---

### Post by john1923 on 2012-02-09
Try right clicking your panel (Taskbar), then adding CPU frequency scaling monitor.

---

### Post by Mark Phelps on 2012-02-09
Reinstalling any recent version of Ubuntu is not going to address the overheating problem ... due to this bug:

[https://bugs.launchpad.net/ubuntu/+bug/901232]("https://bugs.launchpad.net/ubuntu/+bug/901232")

However, you might be able to make use of the following:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

### Post by neo1691 on 2012-02-09
Thanks everyone for their replies.. I just have repaired my laptop regarding the same and have tried every method listed by gbrowning!! 

My hardware specs are [http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx]("http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx")

Still i will try.. can anyone please give me a link that guides how to install ubuntu on a separate partition?? Sorry i am going off topic!!

---

### Post by sudodus on 2012-02-09
Have a look at the following thread, where it is explained step by step.

[[COLOR="RoyalBlue"][COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1914298_[/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1914298")

---

### Post by neo1691 on 2012-02-09
> **sudodus said:**
> Have a look at the following thread, where it is explained step by step.

[[COLOR="RoyalBlue"][COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1914298_[/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1914298")
Awesome!! thanks a lot!! Hope so i make it through!!

---

### Post by neo1691 on 2012-02-19
Okay fine!! 
@everyone i have finally installed ubuntu 11.10... (yippie) but the fan is always making noise.. Its very hard to work that way. Also the heating is too much..

Apart from that, i think ubuntu is taking too time to load, its laggy.. Thats what i feel..

Whenever i press the windows key to get that search function, the typing in the search box is also laggy!!

I have done the following configuration while installing ubuntu.

1)I shrank 15gb of my disk in windows so that i can get 15gb of free space.
2) I choose to manually select drives for ubuntu.
3) I made 4 partitions.
    a)500 mb primary ext4 partition for /boot
    b)3gb swap area
    c)5gb ext4 partition for /
    d)finally the remaining around 8 gb for /home
4) For the bootloader i choose the sda3 ie the 500 mb /boot ext4 partiton.

I installed ubuntu and then restarted, it booted into windows 7 and from there i used easyBCD software to add a linux bootloader entry to it.
Then i again restarted and booted into ubuntu!
(i wanted windows bootloader to control the boot, in case i want to remove linux in future)

Thats all.. I guess maybe i did something wrong!! 
Please guide.
Thanks!

---

### Post by sudodus on 2012-02-19
I read in your link describing your hardware that you have ATI Radeon HD 3200 Graphics.

My experience is that it can be tricky to get the graphics to work efficiently (to make linux and ATI graphics to co-operate). Have you installed proprietary drivers? There is a new driver for ATI graphics, but I don't know if it works with HD 3200.

---

### Post by quickk on 2012-02-19
Hi neo1691, 

     To reduce the fan speed, and make your laptop run cooler overall, you can try intalling the jupiter applet.  See here: [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html").   

Once you have this installed, there will be a little lightening bolt in your system tray (I think on the top right for ubuntu 11.10, I use kubuntu so I don't know exactly where for ubunutu).   You will have the choice between three modes.   If you select the green lightening bolt, this should keep your fan under control.   It worked perfectly for my laptop!

Short install instructions: open up the terminal (seach for terminal) and type the following (you'll have to type your password after the first step).

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```

---

### Post by neo1691 on 2012-02-19
> **quickk said:**
> Hi neo1691, 

     To reduce the fan speed, and make your laptop run cooler overall, you can try intalling the jupiter applet.  See here: [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html").   

Once you have this installed, there will be a little lightening bolt in your system tray (I think on the top right for ubuntu 11.10, I use kubuntu so I don't know exactly where for ubunutu).   You will have the choice between three modes.   If you select the green lightening bolt, this should keep your fan under control.   It worked perfectly for my laptop!

Short install instructions: open up the terminal (seach for terminal) and type the following (you'll have to type your password after the first step).

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```
yup. I will try that and report for sure.. I dont know what is causing the lags though!! By the way.. is the configuration i gave about the hard drives is alright or not?

---

### Post by wildmanne39 on 2012-02-19
Hi, this should help with the laggy problem but do not uncheck the uniity plugin.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thanks

---

### Post by neo1691 on 2012-02-19
> **wildmanne39 said:**
> Hi, this should help with the laggy problem but do not uncheck the uniity plugin.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thanks
Again i will try that and report it. I guess my configuration is right though!! It was the first time i (uber noob in linux) did the advanced partition for ubuntu!! 

I dont even know what / means... :D

---

### Post by quickk on 2012-02-19
> **neo1691 said:**
> I dont even know what / means... :D

In windows, your main hard drive is usually called c:.   You then have other folders like c:\program files, c:\windows, etc.   So in windows, folders are separated by the "\" backslash.  

In linux, folders are separated from each other with the forward slash "/" instead.   The root folder (in which all other files are stored) is just /, and all other files are stored in this directory, or sub folders beneath it.   For example, your home directory is /home/yourname, most applications that you can run from the command line are stored in /usr/bin.   For more information about the linux file system, you can check out (for example), this link: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")

---

### Post by neo1691 on 2012-02-19
> **quickk said:**
> In windows, your main hard drive is usually called c:.   You then have other folders like c:\program files, c:\windows, etc.   So in windows, folders are separated by the "\" backslash.  

In linux, folders are separated from each other with the forward slash "/" instead.   The root folder (in which all other files are stored) is just /, and all other files are stored in this directory, or sub folders beneath it.   For example, your home directory is /home/yourname, most applications that you can run from the command line are stored in /usr/bin.   For more information about the linux file system, you can check out (for example), this link: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")
concepts cleared!! :D
Thanks a lot...

---

### Post by wildmanne39 on 2012-02-19
Hi, let us know how are recommendations work out for you.
Thanks

---

### Post by neo1691 on 2012-02-19
> **wildmanne39 said:**
> Hi, let us know how are recommendations work out for you.
Thanks
Finished my coding work on windows and have just now switched to ubuntu!! trying them!! update coming soon!!

---

### Post by neo1691 on 2012-02-19
> **quickk said:**
> Hi neo1691, 

     To reduce the fan speed, and make your laptop run cooler overall, you can try intalling the jupiter applet.  See here: [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html").   

Once you have this installed, there will be a little lightening bolt in your system tray (I think on the top right for ubuntu 11.10, I use kubuntu so I don't know exactly where for ubunutu).   You will have the choice between three modes.   If you select the green lightening bolt, this should keep your fan under control.   It worked perfectly for my laptop!

Short install instructions: open up the terminal (seach for terminal) and type the following (you'll have to type your password after the first step).

```
sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter
```
Its already on the power saver mode.. and the fan is a little less noisy but yes the noise is there!! I mean when i open a tab on firefox, or if i do some other task!! Thats the first take on the tweak.. i will report more soon!! Thanks a lot!! :)

---

### Post by neo1691 on 2012-02-19
> **sudodus said:**
> I read in your link describing your hardware that you have ATI Radeon HD 3200 Graphics.

My experience is that it can be tricky to get the graphics to work efficiently (to make linux and ATI graphics to co-operate). Have you installed proprietary drivers? There is a new driver for ATI graphics, but I don't know if it works with HD 3200.
Should i go for the drivers?? 

I tried the compiz tweak and the system seems more smoother now!! Thanks!!

But the heat is on!! I mean the noise of the fan is too much! I had operated ubuntu 10.10 on the same machine and that time it was cool as a cucumber.. Now its noisy than Windows!!!

---

### Post by sudodus on 2012-02-19
> **neo1691 said:**
> Should i go for the drivers?? 

I tried the compiz tweak and the system seems more smoother now!! Thanks!!

But the heat is on!! I mean the noise of the fan is too much! I had operated ubuntu 10.10 on the same machine and that time it was cool as a cucumber.. Now its noisy than Windows!!!
Are you running the default driver or the built-in proprietary driver (that is offered by the system)? Run the following command and paste the output into your next post in this thread!
```
glxinfo | grep -i opengl
``` It should show information about your graphics driver.

---

### Post by wildmanne39 on 2012-02-19
Hi, Type top into the terminal and see what is using your resources if anything stands out but it is a graphics driver issue in many cases that cause these problems.

I still recommend going to xubuntu 10.04 that is supported until April 2013 and should get rid of your heating and fan issues.
Thanks

---

### Post by neo1691 on 2012-02-19
> **sudodus said:**
> Are you running the default driver or the built-in proprietary driver (that is offered by the system)? Run the following command and paste the output into your next post in this thread!
```
glxinfo | grep -i opengl
``` It should show information about your graphics driver.
This is what i got!!
> neo1691@neo1691-HP-Pavilion-dv6-Notebook-PC:~$ glxinfo | grep -i opengl
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils


In the meantime i also tried installing the ATI drivers.. This is what happened

[IMG]http://i.minus.com/iQGIGiLtE8gyd.png[/IMG]

---

### Post by sudodus on 2012-02-19
Good enough, now we know that you have no proprietary driver. I suggest that you
- either try to install some driver for the AII card or
- try some simpler desktop environment (Unity 2D, xubuntu-desktop (XFCE) or LXDE).

---

### Post by neo1691 on 2012-02-19
> **sudodus said:**
> Good enough, now we know that you have no proprietary driver. I suggest that you
- either try to install some driver for the AII card or
- try some simpler desktop environment (Unity 2D, xubuntu-desktop (XFCE) or LXDE).
Okay i will try that else i will switch to xubuntu 10.04 or ubuntu 10.10!!

---

### Post by neo1691 on 2012-02-23
Okay i have tried searching a lot for the ATI drivers for ubuntu but i am not able to get any success.

Right now, ubuntu is lagging like hell and my laptop is seeming to be incompatible to run ubuntu.

I am avoiding to install xubuntu or ubuntu 10.04 LTS as i have already downloaded some softwares in this version of ubuntu (11.10)

My laptop configuration is here.
[http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx]("http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx")

Somebody please help me improve my experience on linux!

---

### Post by wildmanne39 on 2012-02-23
Hi, you can try this it helps with Ati graphic cards in most cases.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

I have a laptop like yours and even in 10.04 if I run like videos in full screen mode my fans run hard because it increases the heat a lot.
Thanks

---

### Post by sudodus on 2012-02-23
> **neo1691 said:**
> Okay i have tried searching a lot for the ATI drivers for ubuntu but i am not able to get any success.

Right now, ubuntu is lagging like hell and my laptop is seeming to be incompatible to run ubuntu.

I am avoiding to install xubuntu or ubuntu 10.04 LTS as i have already downloaded some softwares in this version of ubuntu (11.10)

My laptop configuration is here.
[http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx](http://www.gadgetsguru.in/hp-pavilion-dv6-1111au-notebook-vb627pa-price-specification-buy-india-8169.aspx)

Somebody please help me improve my experience on linux!

This way you get the XFCE desktop (and can select between the desktop environments at the log-in screen)
```
sudo apt-get install xubuntu-desktop
``` and you can keep all that you have already installed.

---

### Post by neo1691 on 2012-02-24
> **wildmanne39 said:**
> Hi, you can try this it helps with Ati graphic cards in most cases.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

I have a laptop like yours and even in 10.04 if I run like videos in full screen mode my fans run hard because it increases the heat a lot.
Thanks
Hi i already did that!!

By the way can anyone tell me if my ubuntu partitions were right? I had posted them.

---

### Post by wildmanne39 on 2012-02-24
Hi, here is a link for resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

I give 10 gigs to / partition so I do not run out of space in the root partition which happens if you install a lot of packages.

3 gigs for swap is good.

Home as large as you want, I put it on a separate partition from root so if I need to reinstall I can keep my home folder intact.

You do not need a separate boot partition any more.

This command:
```
sudo parted -l
```
will show how your drive is partitioned.
Thanks

---

### Post by neo1691 on 2012-02-24
> **wildmanne39 said:**
> Hi, here is a link for resizing partitions.
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

I give 10 gigs to / partition so I do not run out of space in the root partition which happens if you install a lot of packages.

3 gigs for swap is good.

Home as large as you want, I put it on a separate partition from root so if I need to reinstall I can keep my home folder intact.

You do not need a separate boot partition any more.

This command:
```
sudo parted -l
```
will show how your drive is partitioned.
Thanks
Here it is 

[IMG]http://i.minus.com/id3ouYrU6YyxZ.png[/IMG]

Also the xubuntu desktop is over 341 mb and my bandwidth is very low now. I cannot download now

---

### Post by wildmanne39 on 2012-02-24
Hi, I believe you can just install xfce4 to use the very lightest version of xubuntu on ubuntu on 10.04 it is 91 mbs.

Your partitions are small, if your root gets to full it will not even boot and it could be making it run slow but that is not causing heating issues.
Thanks

---

### Post by neo1691 on 2012-02-24
> **wildmanne39 said:**
> Hi, I believe you can just install xfce4 to use the very lightest version of xubuntu on ubuntu on 10.04 it is 91 mbs.

Your partitions are small, if your root gets to full it will not even boot and it could be making it run slow but that is not causing heating issues.
Thanks
the downloading started and it was like 9 hours remaining to download. so i had to kill the process!

isnt there a way where we can download the package from the net and then install it?? 
Like we do in windows?

---

### Post by wildmanne39 on 2012-02-24
Hi, you can install from there site but it will be 700 mbs.
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
Thanks

---

### Post by neo1691 on 2012-02-24
> **wildmanne39 said:**
> Hi, you can install from there site but it will be 700 mbs.
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)
Thanks
This seems to be a complete fresh installation. I will have to remove ubuntu and install xubuntu!!!

---

### Post by wildmanne39 on 2012-02-24
Hi, the only other way that I know of is the way already mentioned and it will allow you to switch between desktops.

I am about to go to bed for tonight maybe someone else will have more idea's.
Thanks

---

### Post by neo1691 on 2012-02-24
> **wildmanne39 said:**
> Hi, the only other way that I know of is the way already mentioned and it will allow you to switch between desktops.

I am about to go to bed for tonight maybe someone else will have more idea's.
Thanks
Yup!! Thanks for the help!! I will try to get my hands on some better internet somewhere!

---

### Post by wildmanne39 on 2012-02-24
Hi, your welcome! You might try a hotspot.
Thanks

---

### Post by neo1691 on 2012-02-24
> **wildmanne39 said:**
> Hi, your welcome! You might try a hotspot.
Thanks
I am thinking of deleting this version of ubuntu and reinstalling ubuntu. But within windows this time, not in a separated partition

---

### Post by neo1691 on 2012-02-24
> **jaal4 said:**
> you should increase your ram so that you can use obuntu .
3 gb ram isnt enough to run ubuntu???? :-O

---

### Post by neo1691 on 2012-03-15
Hey!! Re-firing the thread!! 

I have installed ubuntu 10.0.4 LTS and must say its pretty much stable!!! 

Now i want to ask this!! Should i download this (attachment) driver or not?? I have heard it caused some problems!! 

I am able to run compiz (visual effects) on the desktop.. (wobble, cube etc)..

---

### Post by mörgæs on 2012-03-15
If your installation works well with open-source drivers, why do you want closed-source?

---

### Post by neo1691 on 2012-03-15
> **mörgæs said:**
> If your installation works well with open-source drivers, why do you want closed-source?

Yeah it works pretty well except for the heating issues. But then heating issues are very common with my laptop.. So i guess i will have to live with more heat

---

### Post by sudodus on 2012-03-16
> **mörgæs said:**
> If your installation works well with open-source drivers, why do you want closed-source?
You can test that proprietary drive running ***live*** booted from the CD or USB install drive, 'install' it to that ram drive and find out if it works without installing anything to your hard drive.

---

### Post by neo1691 on 2012-03-16
> **sudodus said:**
> You can test that proprietary drive running ***live*** booted from the CD or USB install drive, 'install' it to that ram drive and find out if it works without installing anything to your hard drive.

Ok thanks for the advice. But then wont the installation of the drivers ask for a reboot? I mean then if the drivers are installed in ram then the drivers will be lost on reboot.

---

### Post by sudodus on 2012-03-16
> **neo1691 said:**
> Ok thanks for the advice. But then wont the installation of the drivers ask for a reboot? I mean then if the drivers are installed in ram then the drivers will be lost on reboot.
Yes, the good thing is that
- if the situation get worse, you have destroyed nothing.
- if you notice an improvment, reboot from the internal drive and install the driver permanently.

---

### Post by neo1691 on 2012-03-16
> **sudodus said:**
> Yes, the good thing is that
- if the situation get worse, you have destroyed nothing.
- if you notice an improvment, reboot from the internal drive and install the driver permanently.
Okay i will give that a try

---

### Post by cottfcfan on 2012-03-16
I know i have jumped in late here, but I had a HD2400 graphics card & fans were very noisy on OSS drivers.
You can download the proprietary driver from here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
For me it quietened down & cooled down my system considerably, but mileage & workability varies.
Read the release notes carefully on the download page though.

---

### Post by neo1691 on 2012-03-16
> **cottfcfan said:**
> I know i have jumped in late here, but I had a HD2400 graphics card & fans were very noisy on OSS drivers.
You can download the proprietary driver from here:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
For me it quietened down & cooled down my system considerably, but mileage & workability varies.
Read the release notes carefully on the download page though.

Thanks. Will.i be able to uninstall the driver later?

---

### Post by cottfcfan on 2012-03-17
> Will.i be able to uninstall the driver later? 
Yes. But you will then need to reinstall the OSS Drivers.
The following info is useful:
[http://www2.ati.com/drivers/linux/linux_8.24.8.html](http://www2.ati.com/drivers/linux/linux_8.24.8.html)
[http://mintsational.com/ubuntu/install-ati-drivers-in-ubuntu-11-10-in-three-different-ways/](http://mintsational.com/ubuntu/install-ati-drivers-in-ubuntu-11-10-in-three-different-ways/)
[http://onubuntu.blogspot.co.uk/2011/10/manually-removing-fglrx-from-ubuntu.html](http://onubuntu.blogspot.co.uk/2011/10/manually-removing-fglrx-from-ubuntu.html)

---

