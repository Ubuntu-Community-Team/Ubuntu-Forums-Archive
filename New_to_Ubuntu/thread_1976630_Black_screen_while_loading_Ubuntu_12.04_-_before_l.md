---
title: "Black screen while loading Ubuntu 12.04 - before log-in screen"
date: 2012-05-09
forum: New to Ubuntu
---

### Post by juanmhunicken on 2012-05-09
I installed Ubuntu with Wubi yesterday and the first impression was great, no errors while installing the system nor the first time I logged in. The second time I turned the computer on after installation, Ubuntu seemed to be loading but it froze on a black screen before showing the log-in screen. I reseted the computer and this time the system worked just fine. 

This has been repeating randomly since then, I am now using Ubuntu but I needed to reset twice before I could get it working.

Maybe this has something to do with the problem:
lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

More info:
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-24-generic
Processor: Intel® Pentium(R) Dual CPU E2200 @ 2.20GHz × 2 

Please let me know if you need more information, I want to make Ubuntu work this time (I've had some not-so-good experiences with previous versions)

---

### Post by dzsobacsi on 2012-05-09
I have similar problem and I am trying to look for some kind of solution right now. 
Most probably there is some problem with lightdm.
This seems to be a nice page to start:
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by plant on 2012-05-09
I also have this issue.
But I don't belive it be something to be worried about.
It can be a simple bug.

When the computer boots, step by step it initializes things. Before that the screen is simply loaded with a wallpaper or a simple animation. ex, the ubuntu logo.

Here in ubuntu, any intermediate step must be clearing the video memory before loading completely(probably the step that initializes graphics driver).

---

### Post by ecolom1269 on 2012-05-19
[QUOTE=juanmhunicken;11919435]I installed Ubuntu with Wubi yesterday and the first impression was great, no errors while installing the system nor the first time I logged in. The second time I turned the computer on after installation, Ubuntu seemed to be loading but it froze on a black screen before showing the log-in screen. I reseted the computer and this time the system worked just fine. 

This has been repeating randomly since then, I am now using Ubuntu but I needed to reset twice before I could get it working.

Maybe this has something to do with the problem:
lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)

More info:
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-24-generic


i seen this before, its your video card..work around:

try adding the word 'nomodeset' (no quotes) replacing the 'quiet splash' phrase in grub.
its somewhere near the end on a long line of code
if this work i will show you how to save it permenately to your grub file.

you get to the grub menu by holding the shift key during boot up.

i am confident this will work for you.

Processor: Intel® Pentium(R) Dual CPU E2200 @ 2.20GHz × 2

---

### Post by dzsobacsi on 2012-05-29
Let me try to explain the behavior of my computer a bit more detailed. 

First, this kind of problem occurs only during the first start up of the day. 
Grub starts correctly, I choose Ubuntu. Ubuntu boots up, the violet screen with the Ubuntu sign and the 5 dots appear correctly.
Then I can hear the small "drum" signal indicating the start up of the greeter but at this time the screen is black.
I have realized, that if I wait _several_ minutes (I have never measured it but it is around between 5 and 10 minutes) then the greeter appears and everything works well.
The system itself is running. I can switch to tty1 for example which works fine.
I also realized that I can even log in. I simply enter my password on the black screen, and the user interface is loading up. I know it because there is some strange noise at the speakers as the desktop starts up. However, at this point the screen is still black. Again, if I wait 5 to 10 minutes, the screen appears again. 

I tried to replace unity-greeter to gtk-greeter. In this case, the greeter appears correctly but as I enter my password and the desktop should start up, then the screen is black again. 

If the screen has once appeared, then after reboot it works normally without any issues. But if I switch off the computer for a longer period eg. for the night, I have the same problem on the next day. 

It is very annoying and I really cannot understand what could cause a behavior like this.

---

### Post by nipunshakya on 2012-05-29
This may be something to do with issues related to your  Graphics card.... I had some minor issues like such too...but after installation of additional drivers made available to me, everything went fine....

---

### Post by r_avital on 2012-05-29
I had the same problem, until I realized something:  When you get the login page, in the box with your user-name, right next to the user-name, there is an ubutu logo button.  I clicked it, and selected gnome-2 and was able to start right after entering my password.

If there are issues between the newfangled oh-so-wonderful grub3/unity/whatever it's called this week and your graphics card, you'll need to fall back on gnome-2.

Here's a link to some instructions for that:
[http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-desktop-essentials/](http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-desktop-essentials/)

When on that page, search for "fallback" to get there.

If this is not relevant to your issue, my apologies.

---

### Post by dzsobacsi on 2012-05-30
> **r_avital said:**
> If there are issues between the newfangled oh-so-wonderful grub3/unity/whatever it's called this week and your graphics card, you'll need to fall back on gnome-2. 

I tried to load the Gnome-Classic UI with the same result. Does it mean that Gnome-Classic is also based on Gnome 3?

I skipped 11.11 never used it. With 11.04 I had not any kind of problem with Unity. But if I remember well Unity that time was implemented on the basis of Gnome 2. 

Hmmm, that can be possibly the point....

I think, I will update my graphics driver. If it will not work then I'll create a backup of my system and try to fallback to Gnome 2 or who knows maybe I'll try Kubuntu. I have never used any distro with KDE, maybe this is the right time to check it out.

---

### Post by Ditchdoc7893 on 2012-05-30
Not sure if this would be of any help or not, but have you tried the "nomodeset" option when Ubuntu is first starting up? This was what I had to do before I installed the appropriate NVIDIA drivers for my video card. I'm running a EVGA 01G-P3-1557-KR GeForce GTX 550 Ti.

---

### Post by dzsobacsi on 2012-06-04
> **Ditchdoc7893 said:**
> Not sure if this would be of any help or not, but have you tried the "nomodeset" option when Ubuntu is first starting up? 

Thanks, I've tried already nomodest. It did not help.

Let me tell you about my results from the weekend. 
I decided to struggle a bit more with Gnome 3 and not to switch to KDE. I installed a clear copy of Mint 13, Cinnamon edition. (Cinnamon is based on Gnome 3 as well)

After the install and some tuning, everything went fine. When I checked other available drivers there were 2 possibilities, both provided by Nvidia. I decided to install the first one which was recommended by the system. After the installation I had **absolutely the same behavior then with Precise before. **
I uninstalled the Nvidia driver, and the system started normally again. 
However, later on the day, Cinnamon has crashed, it seems that it has fallen back to Gnome 2 automatically. This is not only what I have tried to avoid but the system became a complete disarray and right now it is practically unusable.

My plans for today evening:
dpkg-reconfigure of mdm and cinnamon. 
If it will not work, I am going to install [Bumblebee]("https://wiki.ubuntu.com/Bumblebee").

The B-plan is to restore the backup that I have created from my previous system, and try to remove Nvidia drivers there. After all,  I had no stability issues with Gnome 3 after it started at last.

===============================================================
Update: 

None of the above brought me success.
Even my B-plan. I had difficulties to restore my backup (created with Clonezilla)  probably because the name of the partition has changed. 
I was tired to google and follow workarounds, so I decided to install Ubuntu 12.04 from the live CD. The graphics were a complete mess ](*,)
On the next day I have reinstalled Mint 13 (Cinnamon edition), which is still running and working flawlessly on my computer. 

I hope, I will not banned out of this forum because of that :p

One last thought:
As I have /home on a different partition installing a new distro was unimaginably painless. The icons on my desktop remained at the same place, all my firefox extensions, all my settings remained the same. I just installed the pieces of software that I needed and I did not have to configure nearly anything. That was an amazing experience and that is a major argument right now, why I love Linux even more.

I will take care not to change anything in my graphics configuration for a while. And I really hope that there will be no install CD in my hands before 2017.
 ):P

---

### Post by ecolom1269 on 2012-09-13
Does anyone know if this graphics problem was solved in ubunto 12.04.1?
my wife is nervous about me fudging with an upgrade.:lolflag::shock:

---

