---
title: "CPU overheats"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by BobosAbelMihai on 2013-04-11
Hello,

I am runing ubuntu 12.10 64 bits.
My cpu overheats a lot, sometimes in idle get's to 70 degrees. The laptop is 5 months old, so i don't think it has dust. If i run the other OS everything cools down to normal.
My laptop is a Toshiba Satellite L855-149 and the CPU is i7.

Please tell me what to do if there is something that can be done, otherwise i will buy an stand cooler.

Thank you.

---

### Post by QIII on 2013-04-11
What is the graphics hardware?

---

### Post by BobosAbelMihai on 2013-04-11
This is my laptop hardware configuration, most of it:

[LIST]
[*]3rd generation Intel® Core™ i7-3630QM Processor with Intel® Turbo Boost Technology 2.0
[*]Toshiba TruBrite® HD TFT High Brightness display with 16 : 9 aspect ratio and LED backlighting
[*]750 GB
[*]Ice Blue Brushed Aluminium Finish, black keyboard
[*]6,144 (4,096 + 2,048) MB
[*]DDR3 RAM (1,600 MHz)
[*]AMD Radeon™ HD 7670M Graphics (2GB dedicated memory)
[/LIST]

---

### Post by QIII on 2013-04-11
This is not a happy situation in the Linux world.  Your CPU has a built-in GPU, so you have what is known as ATI/Intel Hybrid Graphics.

Take a look [here](http://ubuntuforums.org/showthread.php?t=1930450) and read through to see what you are up against.  Neither Intel nor ATI has been kind to the Linux community in this situation.

That thread may or may not be helpful, and don't do anything until you read it thoroughly and ask questions.

The other options are to disable either the integrated or dedicated graphics in BIOS, or try to use Jupiter to control the power consumption (and thus heat) of the ATI GPU.

Best wishes!  Wish I had better news.


QIII

---

### Post by BobosAbelMihai on 2013-04-11
I understood, but my question now is this: Can this situation if i leave it this way do any damage to may laptop if i buy a good stand cooler? I am pretty new to linux, and i have read that post and it's pretty difficult to understand,and maybe i'm a little to tired now . But, if a stand cooler it's ok and can solve , let's say 50% of the current heating, it's perfect for me. 
  What do you say?

---

### Post by QIII on 2013-04-11
Unless you blow air that is chilled to less than ambient, you aren't likely to get that magnitude of cooling performance.  And 70 degrees at idle is a sure way to smoke your machine.

Use Windows if it suits your needs, by all means.  Use what works.

But if you'd like to try getting Ubuntu to work, you might look for an Xorg-Edgers PPA that has something to get that hybrid system to work.  That, or Jupiter may help.

---

### Post by BobosAbelMihai on 2013-04-11
Thank you very much, I will try to make ubuntu work, I will keep reading, put all my data on another device to not lose them and I will try, I don't have nothing to lose.
  I have Windows, but i use it twice a week when i want to play a game, and that's it.

Ok, thank you very much, if I have more troubles I'll be back:p.

Cheers.

---

### Post by BobosAbelMihai on 2013-04-11
I entered in aty catalyst, and i saw that everything was at maximum, the anti-aiasing, the 3d,and the antisopric filtering , i put them lowest, everything on performance not quality and now it's constant at 60 and i have several aplications opened.
  I installed Jupiter, but it doesn't show me the temperature.

---

### Post by gerowen on 2013-04-11
I've had horrible experience with my Toshiba laptop and Linux.  I've tried Ubuntu (4 or 5 different versions), Debian, Fedora, Mandrake, Linux Mint.  All of them fail to throttle the CPU fan properly, regardless of whether or not I have proprietary graphics drivers.  When you turn the computer on, and the BIOS kicks the fan speed up, whatever speed it gets set at, that's the speed it runs at for the entire session regardless of load.  I've tried all sorts of things from trying to manually change fan speed settings in various configuration files to installing firmware for other laptops hoping it was the same motherboard, none of them work.  My suggestion, in the future, don't buy Toshiba laptops.

---

### Post by Locus Kiesselbachi on 2013-04-11
Hardware and kernel does not mix in here! I've read somewhere (sry couldnt find it anymore - I tried) that newer Linux kernels are more power hungry. Where do all this power goes - heating.
On the other hand... using older kernel on newer hardware should not make sense.

...dont mind just passing through.

---

### Post by Mark Phelps on 2013-04-11
> **Locus Kiesselbachi said:**
> Hardware and kernel does not mix in here! I've read somewhere (sry couldnt find it anymore - I tried) that newer Linux kernels are more power hungry. Where do all this power goes - heating.
On the other hand... using older kernel on newer hardware should not make sense.

...dont mind just passing through.
It's more a matter of the newer kernels not handling idling the CPU as well as the MS Windows kernels do -- not surprising, since the laptops are supplied with drivers from the suppliers that handle that well. Since the CPU is generally running faster, it's also running hotter -- which serves to heat up the other components in the laptop, as well.

As said, hybrid (or switchable) graphics is not well implemented in Linux.

---

### Post by jimafternoon on 2013-04-11
I had this issue with the switchable graphics on my Lenovo Ideapad u400. 

I found a fix, maybe you can adapt it to fit your needs.

In terminal, enter this ```

sudo nano /etc/default/grub
```

When you see this line. change it to ```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash modeset=1"
```, adding "modeset=1" after the "quiet splash" 

Press ctrl+O to save, and then ctrl+X to close. 

Now, open your terminal and type: 

```
sudo su
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

This turns off the switchable graphics and just uses the intel graphics, and the fan turns off immediately for me. 

If this works, you can also copy and paste those three 'echo' lines into the file that opens when you type into the terminal ```
gksudo gedit /etc/rc.local
``` (paste them just above the 'Exit 0' line at the bottom), and then save.  This will run the commands automatically on startup. 

Good luck, maybe this can help you.

---

### Post by zrdc28 on 2013-04-11
To solve your problem go to the link below and install jupiter and your problems will be over. It will throttle your cpu when it is not needed. It will appear
in the top right as a icon.

[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)

---

### Post by BobosAbelMihai on 2013-04-12
[**[COLOR=#000000]@jimafternoon[/COLOR]**[COLOR=#000000],i tried to do those steps, but when i must copy the [/COLOR]]("http://ubuntuforums.org/member.php?u=1803084")3 echo comands say to me no such directory, but i managed to copy those in the file 

gksudo gedit /etc/rc.localI installed Jupiter, so far it look's good.
The thing is now when is idle is around 50-55....when i work with it it goes 60-65. It's a reason to be worried?

Thank you all very much.

---

