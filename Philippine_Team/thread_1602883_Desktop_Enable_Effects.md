---
title: "Desktop Enable Effects"
date: 2010-10-22
forum: Philippine Team
---

### Post by JCyberinux on 2010-10-22
ako po may problem sa aking video card, gusto ko sana enable and desktop effects sa may appearance preferences. ok naman siya in terms of normal mode. kaya lang may mga applications ako gusto i-enable kaso need nya ng desktop effects enable. kapag ginagawa ko yung ayaw mg-enable. 

May mga katanungan ako:

May problem ba sa video card ko since Nvidia Geforce FX 5200 ito. at 128 MB lang?

Kung hindi naman, anu mga process dapat gawin? Nagawa ko na yung mga advices nung mga nasa thread dito sa ubuntu kaya lang hindi ma-resolve ang issue.

Kung meron kapareho nung sa akin na issue at na-resolve ito, ipagbigay po alam sa akin. 

P.S. sana yung instructions ay yung madaling intindihin for the sake of everyone.

Thank you!

---

### Post by Script Warlock on 2010-10-22
binisita mo na ba to? [http://ubuntuforums.org/showthread.php?t=1369236](http://ubuntuforums.org/showthread.php?t=1369236)

---

### Post by JCyberinux on 2010-10-23
> **Script Warlock said:**
> binisita mo na ba to? [http://ubuntuforums.org/showthread.php?t=1369236](http://ubuntuforums.org/showthread.php?t=1369236)

yup... but it ain't help... but i found a solution by removing all my drivers specially the default nvidia and custom drivers installed by the ubuntu.

here's the link. 
[http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html](http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html)
[http://forums.whirlpool.net.au/archive/533870](http://forums.whirlpool.net.au/archive/533870)

i'll will also add a screen shots and instructions for the sake of others!!! :)

---

### Post by JCyberinux on 2010-10-23
First of all i would like to thank and give credit for this [I]website:  ANYK and posted by: Mittwoch, 12. May 2010
website: [http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html](http://anykwhere.blogspot.com/2010/05/nvidia-1953624-auf-ubuntu-1004-lucid.html)[/I]

NOTE: (I didn't follow the whole instructions on the said website, because the situation is different than mine.But it helps me to solved my desktop enable effects and video card driver)

==============================================
**first thing to know about installing video card driver and enabling desktop effects**
==============================================
[B](FOR NVIDIA VIDEO CARD DRIVERS AND OPEN GLX ONLY)
 - because i don't know if this process works also in ATI.[/B]
==============================================

1.) Know your video card driver. If it's NVIDiA, then this intructions may help you a lot like me!If it's ATI, hmm... i'm not sure if this instructions may help you.

2.)If you already know your video card driver, go to Official NVIDIA Website. **[http://www.nvidia.com/page/home.html](http://www.nvidia.com/page/home.html)**
> select country > i select default  (US) and go to Download Drivers and choose your video card driver and select Linux 32 bit (if your OS is 32 bit) and Linux 64bit (if your OS is 64 bit). 
> **[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)** > Download Nvidia Drivers (US)

3.)Download it and put it on your desired folder.  

==============================================
**THE SECOND STEP (REMOVAL OF DEFAULT DRIVERS AND INSTALLATION OF NEW AND UPDATED DRIVER)**
==============================================
NOTE: when using sudo command, it will as for a password, so just type your password. (if any). Use cd<space>DIRECTORY for changing directory, ls for showing Directory contents.

1.) Uninstall Noveau > Go to Application > Accessories > Terminal > and type :

***sudo apt-get remove nvidia****
(afterwards)
***sudo apt-get remove xserver-xorg-video-nouveau***

NOTE: If nothing happens, just ignore it and continue to other instructions.
(If there's a removal or additional or even updates and asking for continue press (Y))

After all is done, don't closed yet your terminal nor restart.

2.)Install driver from Packet Source 
(Install nVidia driver from Ubuntu repository to later upgrade it to the latest Version.)

Again, on the Terminal, type: 

[B]*sudo apt-get install libvdpau-dev libvdpau1 nvidia-kernel-common nvidia-185-modaliases nvidia-glx-185 nvidia-settings*
[/B]
NOTE: If nothing happens, just ignore it and continue to other instructions.
(If there's a removal or additional or even updates and asking for continue press (Y))

After all is done, don't closed yet your terminal nor restart.

3.)Using File Browser, Go to desired folder where you Download the NVIDIA video card driver. 

filename: **NVIDIA-Linux-x86-173.14.28-pkg1.run** **(For NVIDIA GFX 5200)**
then i put it at default folder : Downloads (where all my downloaded files are there)

When you located the file, Right-click > Properties > Permissions Tab
You will see:  
Owner: (your name for example) Access: (Read and write) 
Group: (your name for example) Access: (Read only) > change this to (Read and write)
Others: (your name for example) Access: (Read only) > change this to (Read and write)
Execute : check the checkbox (Allow executing file as program)

And then Close.
------------------------------------------------------------------------------------------------------------------------------
4.) On the Terminal, go to your desired folder where you put the downloaded file.
(mine was like this, for example: *yourname@yournamedesktop:~/Downloads$*) 

I go to my folder Downloads, locate the file and from there, I type : 

***sudo chmod a+x NVIDIA-Linux-x86-173.14.28-pkg1.run ***
(afterwards)
***sudo ./NVIDIA-Linux-x86-173.14.28-pkg1.run  -x***

NOTE: If nothing happens, just ignore it and continue to other instructions.
(If there's a removal or additional or even updates and asking for continue press (Y))

After all is done, don't closed yet your terminal nor restart.


==============================================
**THE THIRD STEP (INSTALLATION OF KERNEL HEADERS)**
==============================================
NOTE: when using sudo command, it will as for a password, so just type  your password. (if any). Use cd<space>DIRECTORY for changing  directory, ls for showing Directory contents.

1.)Again, on the Terminal, type: 

***sudo apt-get install linux-headers-`uname -r`***
(afterwards)
***sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux***

NOTE: If nothing happens, just ignore it and continue to other instructions.
(If there's a removal or additional or even updates and asking for continue press (Y))

After all is done, close folders and terminal. but do not restart.

==============================================
**THE FOURTH STEP (INSTALLATION OF NVIDIA VIDEO CARD)**
==============================================
NOTE: when using sudo command, it will as for a password, so just type your password. (if any). Use cd<space>DIRECTORY for changing directory, ls for showing Directory contents.

1.)Press ***CTRL-ALT-F1***

2.)At Terminal, type your login name: (put your login name and press enter) 
     and then asking for a password(put your password and press enter)

3.)Type: 
  *  **sudo /etc/init.d/gdm stop*** (press enter)

    (why? i will answer this later on the note after the instructions)

4.) Go to your desired folder where you put the downloaded file.
(mine was like this for example: *yourname@yournamedesktop:~/Downloads$*) 

I go to my folder Downloads, locate the file and from there, I type : 

***sudo ./NVIDIA-Linux-x86-173.14.28-pkg1.run ***
*(this time without -x)

5.) It will ask you the Accept Terms (press enter) and going between options using arrow keys,Afterwards, it will ask you to keep the previous xconfigure (options will be yes and no)but i choose NO. 

NOTE:  
        I let you type : *sudo /etc/init.d/gdm stop*
        because of the following error messages will arise.
       
[I]You cannot install the nvidia drivers while X is running.

ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page  at [www.nvidia.com](www.nvidia.com).[/I]
      
    
After all is done, type: ***sudo /etc/init.d/gdm start ***(press enter)
to start X. and login to your desktop :)
Enjoy your reborn video card driver and desktop enable effects!!! VIOLA!!! 
           
Thanks to the website, and may this instructions help others...

---

### Post by topet2k12001 on 2010-10-23
Hi Friend,

Actually there's an online repository/PPA that you can simply add so that you can save yourself time.:) After adding the online repository/PPA, whenever you use System->Administration->Hardware Drivers, Ubuntu will make use of the drivers from the online repository. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

Of course if you have tried to install the drivers previously, you will also have to remove/purge all of them first. ;) Never forget to restart the computer after for the changes to take effect (actually it will prompt you to restart your computer).

---

### Post by JCyberinux on 2010-10-26
> **topet2k12001 said:**
> Hi Friend,

Actually there's an online repository/PPA that you can simply add so that you can save yourself time.:) After adding the online repository/PPA, whenever you use System->Administration->Hardware Drivers, Ubuntu will make use of the drivers from the online repository. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

Of course if you have tried to install the drivers previously, you will also have to remove/purge all of them first. ;) Never forget to restart the computer after for the changes to take effect (actually it will prompt you to restart your computer).

yup, that's sometimes true but i think it depends on the case to case basis. Like mine, works that way, i don't know as you said adding a online repository/PPA may save time, but in my case it doesn't it also complicates my setup... After reading and also asking a lot of advices in ubuntu threads/forums and discussions on other community, this one works for me perfectly without a glitch. So making a thread may serve its purpose thru others. And thank you for sharing your thoughts with us. Cheers!:guitar:

---

