---
title: "How to use Ubuntu 16.04 ?"
date: 2016-08-26
forum: New to Ubuntu
---

### Post by dkm171 on 2016-08-26
Dear admin & support team or friend !


I am new for Ubuntu 16.04 OS.

I need help,


1. No Refresh button on Ubuntu

2. how to change screen resolution to 1600x900,  not available 1600x900 Ubuntu 16.04 !

3. Ubuntu 16.04 Very slowly working on my computer (I have 8 GB ram, 2.8Ghz CPU, 160gb HDD)


how to use Ubuntu 16.04 soft and correctly ?

I don't know

i want to learn how to use Ubuntu Linux 16.04

---

### Post by yancek on 2016-08-26
Have you tried reading through the Ubuntu Desktop Guide at the link below for 16.04?


[https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)

---

### Post by grahammechanical on 2016-08-26
On the top panel at the right there is the power/cog icon. We use that to shut down Ubuntu. Click on the icon and from the drop down menu select Ubuntu Help. That will explain lots of things. Here is an online version of the Ubuntu Desktop Guild (Help)

[https://help.ubuntu.com/16.04/ubuntu-help/](https://help.ubuntu.com/16.04/ubuntu-help/)

What is a Refresh button? What is it supposed to do? Are you expecting Ubuntu to work the same way as a version Microsoft Windows? Ubuntu may be working slowly because of some conflict with the video driver. Go to the Power/Cog menu and select About this Computer. That will open System Settings at the Details page. What description does the Details page give for Graphics? If it says llvmpipe, then your system is using an open source video driver that is being used as a fall back video driver.

We get llvmpipe as a video driver if our graphic/video adapter cannot do the hardware accelerated 3D rendering that Ubuntu needs to run its Unity 3D user interface. We also get llvmpipe if there is a conflict with a proprietary video driver. What video adapter do you have? How much of its own memory does it have?

From the Details page go to All Settings and select Software & Updates>Additional Drivers tab and change the video driver. You need to be connected to the Internet and allow time for the utility to find appropriate video drivers for your graphic adapter.

Using a suitable video driver might make the video setting that you want available. What cable are you using to connect to the monitor. A VGA cable will limit the resolution available. At System Settings>Screen Displays there is a drop down menu that will list available screen displays. When Ubuntu loads it sets the screen resolution based on information stored in the circuitry of the digital monitor. Ubuntu will use the optimum resolution. It is best to stay with the optimum setting.

Regards

---

### Post by poorguy on 2016-08-26
Hey dkm171,

Ubuntu 16.04 user guide you can download.

[http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf](http://files.ubuntu-manual.org/manuals/getting-started-with-ubuntu/16.04/en_US/screen/Getting%20Started%20with%20Ubuntu%2016.04.pdf)

---

### Post by dkm171 on 2016-08-27
thanks friends for your replies

Dear friends

my mother board is Gigabyte H61M-S and [COLOR=#000000]I have 8 GB ram, 2.8Ghz CPU, 160gb HDD[/COLOR]

and 

i have seen on "About This Computer" :

Gallium 0.4 on llvmpipe (LLVM 3.8, 128 bits) 



i need change to correct display resolution 1600x900

(my dell led monitor and vga cable works on windows correctly for display 1600x900)





Best Regards!

---

### Post by zephar123 on 2016-08-28
Do you know what video card comes with that computer? AMD, intel , Nvidia?

---

### Post by Geoffrey_Arndt on 2016-08-28
There is a "standard" method to upgrade a newly intalled Ubuntu to it's proper video driver . . . do you know if you have tried that?

Just in case you have not done so . . . . the way it is done is:

Open the "System Settings" in the Launcher Bar.    Then open the "Software and Updates" program in System Settings.     Then click on the "additional drivers" tab within the Software and Updates window.    Then select the proper driver from the Additional Drivers window that corresponds to the video system you have on your PC.   This only applies to nVidida or AMD/ATI video - - not to Intel video.    After the driver is installed, close all programs, reboot the system, and you should now have normal speed of operations.

EDIT:   I just saw this is a repeat of what "Graham" in post #3 already said, but I still have not seen if you have tried to install the video driver.

---

### Post by dkm171 on 2016-08-29
Dear friend  [[COLOR=#000000]zephar123[/COLOR]]("https://ubuntuforums.org/member.php?u=1452155")

Intel video card !

Dear Geoffrey_Arndt

i will try this !

---

### Post by Geoffrey_Arndt on 2016-08-30
If standard driver install does not solve issue, the fix listed below is worth a try:

EDIT:   this post is from an older version of ubuntu/mint.   Suggest you backup your system first, or at least make a copy of existing xorg.conf if it already exists.

[lement Lefebvre (clementlefebvre)]("https://launchpad.net/%7Eclementlefebvre")             wrote             on 2012-11-25:                                                 [TABLE]
[TR]
[TD][/TD]
[TD="class: bug-comment-index"]           [ #18]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1074779/comments/18")[/TD]
[/TR]
[/TABLE]
                               Manual fix, create /etc/X11/xorg.conf and write the following into it:
 Section "Device"
        Identifier      "My device"
        Driver          "intel"
EndSection
 Press CTRL+ALT+BACKSPACE to restart your computer (or reboot if you're running Ubuntu).
 Check with inxi -G (or glxinfo if you're running Ubuntu) to make sure your renderer is now Intel and not Gallium LLVMPIPE.
 Please let us know if this works for you in Mint 14 or Ubuntu 12.10.

---

### Post by dkm171 on 2016-09-23
Dear friends and admins 


up to now i am facing display resolution in my pc, my pc display current setting 1024x768, but my led monitor supports 1600x900.

already i am using  1600x900 at windows, its working perfectly


please tell me,

---

### Post by oldos2er on 2016-09-23
I suggest you create a new thread for your display resolution problem, since the subject "How to use Ubuntu 16.04?" no longer seems to apply.

---

