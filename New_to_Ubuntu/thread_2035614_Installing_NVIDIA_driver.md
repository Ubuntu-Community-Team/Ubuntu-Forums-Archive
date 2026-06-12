---
title: "Installing NVIDIA driver"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by BlueAZ on 2012-07-31
Hi,         I've downloaded the most current driver for my Nvidia graphics card, which I just installed.  Ubuntu driver runs it, but gives this big flicker every minute, & it's driving me crazy!   The download is a .run file, & I've read Nvidia's instructions on how to install, as well as several posts in the forums.

I almost got it to work once!  But it wouldn't complete, saying I had to exit the X window.  I've tried >sudo gdm-stop< but Terminal says it doesn't recognize the command.  How do I shut off the X window?

I'm running Oneiric Ocelot, Unity 2D, 64-bit AMD quad-core CPU.

Thanks!

---

### Post by anewguy on 2012-07-31
Before trying what you did, did you try just going through additional drivers and see if it finds and downloads a driver for you to use?  I use nVidia and the driver ubuntu to was using "out of the box" had the flicker you mention.  When everything was installed okay, the first thing I did was go to additional drivers and it found and downloaded the correct driver and no more flicker.

---

### Post by deadflowr on 2012-07-31
To kill X run

```
sudo service lightdm stop
```

To follow anewguy, was there any reason to download the drivers from nvidia instead grabbing them through the additional drivers?

---

### Post by audiomick on 2012-07-31
> **deadflowr said:**
> To kill X run

```
sudo service lightdm stop
```


If that doesn't seem to work (which it should), just log off and back on again. Not a re-start, just log the user off and log back in. That will re-start the X-server.

I also would like to know why you feel you need to get the drivers from nVidia instead of using the Ubuntu Hardware drivers utility. I haven't experienced the flicker problem you describe, but I have been using the hardware driver utility for my various nVidia graphic cards for some years with never a problem.

---

### Post by NikTh on 2012-07-31
Hi , 

I agree with @anewguy and others . Do not struggle with .run file . 
Just open a terminal and do 
```
sudo apt-get update 
sudo apt-get install nvidia-current
sudo nvidia-xconfig 
sudo reboot
```Drivers provided as additional drivers , are technically tested by Ubuntu Developers. 
I don't say that drivers on Nivida's site aren't good , but I prefer first to install what Ubuntu includes. 

Thanks

---

### Post by BlueAZ on 2012-07-31
Sorry, I should have mentioned that I did use Additional Drivers in Ubuntu.  It loaded a driver that was older, so I couldn't access the Nvidia settings with it.  Also, the only screen res it offered was something like 400 x 600 -- everything was too huge to see.  So I had to purge that!

Thanks for instructions on how to stop X Service.  I'll try the .run install again & report back.

Meanwhile, I've developed a problem with an x-swat source, per separate post :confused:

---

### Post by BlueAZ on 2012-07-31
I did the command >sudo service lightdm stop<  and it put me in a text-only screen that kept adding entries on its own.  I couldn't input anything.  When it was apparently done, it restarted the computer, back in X Service.

I tried logging out, but when I logged back in, X Service is running.

Tried installing .run file again, & couldn't.  Var logfile says this:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Jul 31 11:32:39 2012
installer version: 295.59

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '2704' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

How do I operate the text-only black screen?

---

### Post by ubudog on 2012-07-31
> **BlueAZ said:**
> 
How do I operate the text-only black screen?

Press CTL+ALT+F1.

Enter your username and password to login to the shell.

From there you should be able to stop the X server:
```
sudo service lightdm stop
```

And run the installer:
```
sudo ./nvidia-installer
```
(I believe that it needs to be run as root, someone please correct me if I'm wrong)

When it's done, you can restart X by either:
1. Rebooting:
```
sudo reboot
```

2. Starting up LightDM:
```
sudo service lightdm start
```

Hope that helps!

---

### Post by Bobhuber on 2012-07-31
> **ubudog said:**
> Press CTL+ALT+F1.

Enter your username and password to login to the shell.

From there you should be able to stop the X server:
```
sudo service lightdm stop
```And run the installer:
```
sudo ./nvidia-installer
```(I believe that it needs to be run as root, someone please correct me if I'm wrong)

When it's done, you can restart X by either:
1. Rebooting:
```
sudo reboot
```2. Starting up LightDM:
```
sudo service lightdm start
```Hope that helps!
Good instructions.
Reboot is a must to make sure the drivers have installed correctly.
Additional - Make sure the installer file NVIDIA -##-295.59.run  is marked as executable before doing anything. .
As to why the OP would want to install the latest stable drivers . I'm running the latest 304.30  (Beta) drivers and the video speeds have increased dramatically over the system drivers.
Also  the newest Nvidia driver now supports DKMS so you no longer have to reinstall with Kernel upgrades which used to be a hassle for us lazy folks.

---

### Post by BlueAZ on 2012-07-31
Thanks UbuDog & Bobhuber, but when I try it all hell breaks loose!  So the black screen with white lettering is called the 'shell'?  First it entered my username for me & asked for my password.  I entered it, the same & only one I'm aware of.  But it rejects my password & won't let me log in.  I tried every way I could think of.  Meanwhile, it keeps rattling off lines about 'forcing panel scaling' and 'nouveau' over & over.  It just keeps adding its own lines & rejecting anything I type in.  Had to do a hard shutoff to escape.  

I previously blacklisted 'nouveau' per someone else's directions.  Is that a problem now?  I fear I'll never get the hang of this!  :confused:

---

### Post by ubudog on 2012-07-31
> **BlueAZ said:**
> Thanks UbuDog & Bobhuber, but when I try it all hell breaks loose!  So the black screen with white lettering is called the 'shell'?  First it entered my username for me & asked for my password.  I entered it, the same & only one I'm aware of.  But it rejects my password & won't let me log in.  I tried every way I could think of.  Meanwhile, it keeps rattling off lines about 'forcing panel scaling' and 'nouveau' over & over.  It just keeps adding its own lines & rejecting anything I type in.  Had to do a hard shutoff to escape.

Try CTL+ALT+F2 (it goes up until F6).

---

### Post by Bobhuber on 2012-07-31
> **BlueAZ said:**
> Thanks UbuDog & Bobhuber, but when I try it all hell breaks loose!  So the black screen with white lettering is called the 'shell'?  First it entered my username for me & asked for my password.  I entered it, the same & only one I'm aware of.  But it rejects my password & won't let me log in.  I tried every way I could think of.  Meanwhile, it keeps rattling off lines about 'forcing panel scaling' and 'nouveau' over & over.  It just keeps adding its own lines & rejecting anything I type in.  Had to do a hard shutoff to escape.  

I previously blacklisted 'nouveau' per someone else's directions.  Is that a problem now?  I fear I'll never get the hang of this!  :confused:

Its not entering your username automatically.
When you get to the login screen enter your username first then the password. What you are seeing is just a prompt that has your name in it . Blacklisting nouveau is fine and until you get the driver installed it will not be happy.  What I would do now is boot into the recovery mode from the grub menu. Select resume normal boot from the menu that will come up and you will be put back into the  terminal "black screen with white lettering" where you should be able to enter your username and password without the system fighting you. You will not need to disable the xserver at this point (service lightdm stop) since it has not been loaded yet. Just follow the rest of the instructions to load the driver. The only way you learn to use the terminal is to actually use it. If you still have problems don't be afraid to ask.

---

### Post by BlueAZ on 2012-07-31
It just keeps doing the same thing:  rejecting my log in, & printing stuff about forcing panel scaling & nouveau.  It says 'No native mode' too.  I finally discovered that CTL+ALT+F7 gets me out of there.  That's a big help!

---

### Post by BlueAZ on 2012-07-31
OK, sorry...  how do I boot into recovery mode?  How would I get to the grub menu?  Please give basic step-by-step's, as I am a newbie!

---

### Post by Bobhuber on 2012-07-31
> **BlueAZ said:**
> OK, sorry...  how do I boot into recovery mode?  How would I get to the grub menu?  Please give basic step-by-step's, as I am a newbie!
Hold the shift key down while you booting the computer. It should bring up a menu that will allow you to boot into the recovery mode. No mouse just use the arrow keys to make a selection.

---

### Post by NikTh on 2012-08-01
Hi , 

can you please post the output of below command 
```
lspci -nnk | grep -iA2 vga
``` 

Thanks

---

### Post by BlueAZ on 2012-08-01
This is what that brings up:

01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GT] [10de:0402] (rev a1)
    Subsystem: Device [196e:0439]
    Kernel driver in use: nouveau

At this point, I'd settle for ANY graphics driver that would give me decent screen resolution and no flickering.  I'm not up to all this complicated stuff! ;-}

---

### Post by NikTh on 2012-08-01
Hi , 

did you try to install newest nvidia driver , with X-Swat PPA ? 

give the result of these commands 

```
apt-cache policy nvidia-current 
ls /etc/apt/sources.list.d/
``` 

Thanks

---

### Post by BlueAZ on 2012-08-01
> **NikTh said:**
> Hi , 

did you try to install newest nvidia driver , with X-Swat PPA ? 

give the result of these commands 

```
apt-cache policy nvidia-current 
ls /etc/apt/sources.list.d/
``` 

Thanks
I did try that, but the x-swat ppa wreaked havoc with my system.  Couldn't run Update Manager or Synaptic.  Went through a long process (in another post) to just get it off my computer.  I'm not about to do that again!  Any other ideas?  :~}

---

### Post by NikTh on 2012-08-01
> **BlueAZ said:**
> I did try that, but the x-swat ppa wreaked havoc with my system.  Couldn't run Update Manager or Synaptic.  Went through a long process (in another post) to just get it off my computer.  I'm not about to do that again!  Any other ideas?  :~}

Hi , 
I understand your fear with X-Swat ppa, but commands I gave you have nothing to do with this. 
Give the results if you want. 

Thanks

---

### Post by BlueAZ on 2012-08-01
> **BlueAZ said:**
> I did try that, but the x-swat ppa wreaked havoc with my system.  Couldn't run Update Manager or Synaptic.  Went through a long process (in another post) to just get it off my computer.  I'm not about to do that again!  Any other ideas?  :~}
OK, thanks for your patience!  The first line got this:

nvidia-current:
  Installed: (none)
  Candidate: 280.13-0ubuntu6.1
  Version table:
     280.13-0ubuntu6.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/restricted amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/restricted amd64 Packages
     280.13-0ubuntu6 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/restricted amd64 Packages

The 2nd line got this:

banshee-team-ppa-oneiric.list
banshee-team-ppa-oneiric.list.save
diesch-testing-oneiric.list
diesch-testing-oneiric.list.save
dropbox.list
dropbox.list.save
freefilesync-ffs-oneiric.list
freefilesync-ffs-oneiric.list.save
gnome3-team-gnome3-oneiric.list
gnome3-team-gnome3-oneiric.list.save
google-earth.list.save
medibuntu.list
medibuntu.list~
medibuntu.list.save
medibuntu-ppa-oneiric.list
medibuntu-ppa-oneiric.list.save
nilarimogard-webupd8-oneiric.list
nilarimogard-webupd8-oneiric.list.save
otto-kesselgulasch-gimp-oneiric.list
otto-kesselgulasch-gimp-oneiric.list.save
pidgin-developers-ppa-oneiric.list
pidgin-developers-ppa-oneiric.list.save
rye-ubuntuone-extras-oneiric.list
rye-ubuntuone-extras-oneiric.list.save
sevenmachines-flash-oneiric.list
sevenmachines-flash-oneiric.list.save
skype-wrapper-ppa-oneiric.list
skype-wrapper-ppa-oneiric.list.save
transmissionbt-ppa-oneiric.list
transmissionbt-ppa-oneiric.list.save
tualatrix-ppa-oneiric.list
tualatrix-ppa-oneiric.list.save
ubuntu-mozilla-security-ppa-oneiric.list
ubuntu-mozilla-security-ppa-oneiric.list.save
ubuntu-wine-ppa-oneiric.list
ubuntu-wine-ppa-oneiric.list.save
ubuntu-x-swat-x-updates-oneiric.list.save
weather-indicator-team-ppa-oneiric.list
weather-indicator-team-ppa-oneiric.list.save
webkit-team-ppa-oneiric.list
webkit-team-ppa-oneiric.list.save

In my other post about troublesome sources, I mentioned that I can't seem to delete or change things in the /etc folder.   That's why it was so hard to fix the problems caused by the x-swat ppa.  There must be a way to work with these files...??        Thanks again!

---

### Post by NikTh on 2012-08-01
Hi , 
yes , I can see a bunch of staff there. Too many PPA's . Are you really want all these ? 

Gnome3 - PPA , upgrades lot of things , almost all your packages. 
x-swat yes its still there. 

Why you cannot manage things inside /etc ? Do you have problem with permissions ? sudo maybe ? what is the problem ? 
My thoughts is that X-Swat ppa conflicts with gnome3 ppa (some packages maybe). 
I use X-swat ppa long time and I can confirm that is very stable. 
The Unstable PPA its X-edgers , contains lot of unstable packages. 

I think we must try to fix other problems first , and then we can proceed with nvidia-driver.

A , last question : 
Why you are in 11.10 , when 12.04 is here ? 

It depends of you how you want to proceed . 

Thanks

---

### Post by BlueAZ on 2012-08-01
> **NikTh said:**
> Hi , 
yes , I can see a bunch of staff there. Too many PPA's . Are you really want all these ? 

Gnome3 - PPA , upgrades lot of things , almost all your packages. 
x-swat yes its still there. 

Why you cannot manage things inside /etc ? Do you have problem with permissions ? sudo maybe ? what is the problem ? 
My thoughts is that X-Swat ppa conflicts with gnome3 ppa (some packages maybe). 
I use X-swat ppa long time and I can confirm that is very stable. 
The Unstable PPA its X-edgers , contains lot of unstable packages. 

I think we must try to fix other problems first , and then we can proceed with nvidia-driver.

A , last question : 
Why you are in 11.10 , when 12.04 is here ? 

It depends of you how you want to proceed . 

Thanks
Thank you again for your patience!    I started with 11.04.  When I tried to upgrade to 11.10, I got a black screen & couldn't get into the OS at all.  I had to wipe the drive & do a fresh install of 11.10.  I've been afraid of that happening again.  But I think the earlier problem was my previous ATI Rage graphics card.  I thought this Nvidia card would take care of it all.

If you think it's safe, I'll try upgrading to 12.04.  Would that clean up the ppa's?  I've just added ones related to app's I use; the others have added themselves during updates.  I don't know what I need from what I don't.  From within the folder /etc, I have tried to delete things like the x-swat ppa, but it won't let me.  I can use the Terminal, but I only know a few commands.  Usually I find a procedure here or online, copy & paste it in the Terminal.  I don't understand the commands system very well.  Can I use Synaptic to do this?  If so, how?

---

### Post by simonmoon42 on 2012-08-01
At this point it might just be easier to wipe it out, re-install and start from scratch. It sounds like you've followed a lot of different suggestions and weren't able to back them out properly. I ran into the same thing when I first started out on Linux. Tried too many fixes and ended up making my system unusable. Re-installing a couple of times your first time out is expected. It's all a learning experience.

---

### Post by G4dget on 2012-08-01
Deja-vu. This definitely sounds like the troubles I encountered when trying to install nvidias drivers as well. I agree with simmon and that you may be to the point, unfortunately, of wiping and installing fresh since you have tried quite a few different suggestions. This is a pain but sometimes necessary when learning. 

Here is a [[COLOR="Navy"]link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2034982") to the posts I made documenting my trials and tribulations with the nvidia install. I am running 10.04 but I am pretty sure the steps will be the same for 11.04 - 12.04 , someone correct me if I am wrong.

Good luck

---

### Post by blade4 on 2012-08-01
I might be wrong here and this might have been mentioned here before ( I'm too lazy to check ), but if its gotten to the point where system reinstall is being talked about , why not remove everything nvidia related from synaptic and then reinstall from wherever one deems safe ?

---

### Post by NikTh on 2012-08-02
Hi , 
my first suggestion (as always) its to backup all your personal data (pictures - videos - documents - music) to external driver or Usb (if fit there) and do a** fresh install** of Ubuntu 12.04 32 or 64bits (depends on your processor architecture). 

If you want to upgrade instead of fresh install , you must delete all these PPA's . Especially Gnome 3 -PPA. I will quote here a Warning directly from [Gnome 3 - PPA.](https://launchpad.net/~gnome3-team/+archive/gnome3) 
> Before upgrading your system to a new Ubuntu release (i.e. from Ubuntu  11.10 to 12.04), you should probably run ppa-purge ppa:gnome3-team/gnome3 first. 

So, if you decide to upgrade , first go to Update manager > Settings > Other Software and Delete (not only Untick, but **delete completely**) all the ppa's you have. Then go to terminal and do ```
sudo apt-get update 

sudo apt-get dist-upgrade
``` , then you can proceed with Ubuntu release upgrade. 

Ask anything you want before proceed upgrade to 12.04 

I insist that a fresh install might be better. 

Thanks.

---

### Post by BlueAZ on 2012-08-02
OK, I guess I'll have to do a fresh install.  I'm backing up my stuff now.  If it's on Ubuntu One, I can just reinstall it to the new OS, right?  One more question:  The first time I installed Ubuntu (11.04),  I deselected some of the offered Updates that didn't sound right or what I was interested in.  But I got a buggy system.  The 2nd time I fresh-installed Ubuntu (11.10), I just accepted all offered updates in Update Manager, accepting that I know nothing.  Now I've got too much stuff.  What's the right way?  How do I know what's appropriate for my system and what's not?  Like Gnome -- I'm using Unity desktop, but I don't know if it's dependent on Gnome still or not.  If I'm going to do a fresh install, is there any way to save all the applications I've added?  It seems silly to download & install them all again, not to mention time-consuming.  Is there a guide to maintaining an Ubuntu system?  Thanks!

---

### Post by NikTh on 2012-08-02
> **BlueAZ said:**
> OK, I guess I'll have to do a fresh install.  I'm backing up my stuff now.  If it's on Ubuntu One, I can just reinstall it to the new OS, right?  One more question:  The first time I installed Ubuntu (11.04),  I deselected some of the offered Updates that didn't sound right or what I was interested in.  But I got a buggy system.  The 2nd time I fresh-installed Ubuntu (11.10), I just accepted all offered updates in Update Manager, accepting that I know nothing.  Now I've got too much stuff.  What's the right way?  How do I know what's appropriate for my system and what's not?  Like Gnome -- I'm using Unity desktop, but I don't know if it's dependent on Gnome still or not.  If I'm going to do a fresh install, is there any way to save all the applications I've added?  It seems silly to download & install them all again, not to mention time-consuming.  Is there a guide to maintaining an Ubuntu system?  Thanks!

Hi , 
OK , so many questions I see. 

I will answer as shortly and comprehensive I can. 
All below mentioned  are _**My Opinion and nothing else**_. Not Ubuntu's documentation or something like that.

1) For Updates , you accept them all. Updates usually are security updates and bug fixes for packages.

2) Do not add external PPA's if its not necessary. External PPA's offer Untrusted packages , that Ubuntu not accept them (yet) to Official repositories.** I do not  blame **PPAs , they offer much and notable packages  , but to many ppas can mess up things.

3) Gnome is a Desktop Environment , Unity is just a Plugin to this Environment. So if you take a look at the System Monitor you will see Gnome's release number. 

4) Applications from old install to new... No , this is not a good idea. Ubuntu 12.04 has its own packages , newer packages  than 11.10.  More stable, more bug fixed. You need to install packages from the beginning. 

5)  Guide for maintain ? hmm I don't know If I can give any link to that. I learned in time that Ubuntu (linux generally) doesn’t want so much maintain (as windows do). 
No registry cleaners , no disk or registry de-fragments . 
Many tools are on Software Center or Internet available (generically) , for cleaning up Ubuntu , but I.M.O none required. 
Clean up Ubuntu for me are simple commands in terminal . 
```
sudo apt-get autoremove
``` will remove all unwanted packages. 
```
sudo apt-get clean all
``` will clean up apt's cache . 
```
sudo rm -rf /var/lib/apt/lists/*
``` will clean up all your sources.list . 
You must re-create them with ```
sudo apt-get update
``````
sudo apt-get purge $(dpkg -l | awk '/^rc/ { print $2 }') 
``` this command will remove all packages that you have already removed but their settings  are still in /etc, and the not-fully installed packages.

Thanks

---

### Post by BlueAZ on 2012-08-02
Thank you so much NikTh!!   I will try these commands in the Terminal.  I know it's just your opinion, but if it works, I'd recommend posting this as a How-To.  If the Forum allows that.

---

### Post by simonmoon42 on 2012-08-02
> **BlueAZ said:**
> Thank you so much NikTh!!   I will try these commands in the Terminal.  I know it's just your opinion, but if it works, I'd recommend posting this as a How-To.  If the Forum allows that.

Just as an addendum to what NikTh said... look at ubuntu tweak. It includes a "janitor" tool that will help you clean off unwanted kernels, packages, etc... to install just follow the directions  [here.]("http://ubuntu-tweak.com/downloads/")

---

### Post by BlueAZ on 2012-08-03
Figured it out!!  After all the advice, I just kept trying different things.  I asked the Software Center for 'NVidia' -- it showed me an option, but wouldn't let me install it.  Tried many times to install the proprietary driver, v. 295.59 -- no joy.  Remember, I had originally opened Additional Drivers, & it installed an old driver that was awful (v. 173).  

Finally today, I opened Synaptic & searched for NVidia.  What a shock!!  Synaptic showed me several versions, including an actual current one, v. 295.2.  I checked it, it told me what else needed to be gotten, it downloaded & installed the driver, I restarted, & voila!!    Perfect graphics, access to Nvidia Settings, the works!

I hope this helps someone else not spend the hours I've spent solving this!

---

