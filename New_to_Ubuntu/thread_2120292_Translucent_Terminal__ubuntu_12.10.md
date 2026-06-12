---
title: "Translucent Terminal  ubuntu 12.10"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by interfacer on 2013-02-26
Hi all):P. First post. I HAVE NEVER USED LINUX BEFORE, but I have started reading the help file. I downloaded ubuntu 12.10 iso, wrote to disk and installed successfully.  Now all the help I've tried to get is futile because my terminal is translucent. When I open the terminal, the terminal menu bar appears and when I move the mouse cursor over a section of the desktop the cursor changes to text, but no terminal window appears. I'm so frustrated because it seems I can't do anything without the terminal... Help Please...

---

### Post by Impavidus on 2013-02-26
A translucent terminal is actually a feature but it shouldn't be completely invisible. Can you find preferences in the menu bar and play a bit with the background and the text colour? Sometimes that helps.

You can do quite a lot without the terminal but the terminal is usually the most efficient way to get things done.

---

### Post by varunendra on 2013-02-26
First of all, a Warm Welcome to the forums interfacer! :)

About your problem-
> **interfacer said:**
> and when I move the mouse cursor over a section of the desktop the cursor changes to text, but no terminal window appears. 
When the pointer does change to text cursor, does any text appear there if you click and start typing ?

Also, when you click on the area where it changes to text cursor, and then hover the mouse pointer over the Unity panel (the top black bar), can you access the Terminal menu items ? (File, Edit, View,...etc.)

If you can, then the transparency settings are under -
**Edit > Profile Preferences > Background** tab

Let us know if you have problem accessing it.

---

### Post by interfacer on 2013-02-26
Thanks for the hospitality and prompt response guys... The terminal menu appears. Changing the window size seems to change this invisible area. I tried changing the desktop wallpaper too - no joy. No text appears when I type either. I'm gonna try playing with the background colour and other preferences of the terminal itself perhaps?... Will let you know... Unfortunately I have to reboot into ubuntu (using 1 pc dual-booting windows and linux) to try all this because I haven't been able to connect my mobile broadband connection in ubuntu (my next post soon as I fix this terminal issue) so I hope you can be patient.

---

### Post by coldraven on 2013-02-26
You could install Guake, it is in the Software Centre.
It is a handy drop-down terminal that appears when you press F12.
when first installed it is transparent, to change this do the following.
Press F12 to see Guake.
Right click in the window, select Preferences.
Go to the Appearance tab and move the Effects slider.

If you like Guake then add it to "Startup Applications" and it will always be available.
You can make it go fullscreen with F11 or just drag it to the size that you like.
It also has tabs. New tab is the yellow button on the bottom right.

---

### Post by interfacer on 2013-02-26
Will try gauke - sounds like a convenient tool. So I don't need an internet connection to install it via Software Centre?

Anyway I tried changing terminal background, text colour and all the like - no success, no error message, no change in appearance. Interestingly though, when I boot in recovery mode using an option called system summary it seems to work just fine showing 'username@computername...' prompt. When I change preferences in this mode changes are affected immediately (like most other settings in the OS). I was very pleased to see the command prompt but now I am even more paranoid about the integrity of my installation... so not resolved as yet... I know this might sound like a stupid question, but I'll risk it: If I affect changes to my system (like install software) in this newly found OS mode this could this suffice for me as a learning platform for now? I plan on installing the server OS once I'm comfortable with the interface.

---

### Post by varunendra on 2013-02-26
> **interfacer said:**
> I know this might sound like a stupid question..
No it doesn't :)

> when I boot in recovery mode using an option called **system summary**..
Are you sure it says **system summary**? I haven't heard of such option in recovery menu. Maybe someone else with a 12.10 installation can explain better, but 'assuming' that it is similar to 'failsafeX' mode in earlier versions, yes, it 'should' be no different to the normal mode other than having no hardware acceleration support for 3d graphics.

But for learning and testing purpose, VMs are usually the best and safest option.

---

### Post by interfacer on 2013-02-26
You mean like a live OS? Is this VMware suitable for c programming learning purposes (like programming the parallel port?)?

So can I conclude that my installation is corrupt? That is why my terminal is not working in normal mode and I cannot fix this problem? I've been occasionally getting "Software problem encountered" when trying some operations in the OS. I'm considering jumping  into 12.04. perhaps that version is more stable. Is it normal for the Graphics to be very slow?

---

### Post by windscape on 2013-02-26
Hi,

Ubuntu 12.10 and 12.04 require hardware OpenGL for the Unity interface to work properly. What model graphics card does your PC have? It is probably either too old to support Unity or you need to install proprietary drivers to get hardware OpenGL support.

---

### Post by interfacer on 2013-02-26
Hi windscape,

Thanks for your insight. So this graphics problem could explain why terminal is there but not showing properly in normal mode?

I'm using NVIDIA Quadro NVS PCI 64mb graphics adapter.

---

### Post by varunendra on 2013-02-26
> **interfacer said:**
> You mean like a live OS? Is this VMware suitable for c programming learning purposes (like programming the parallel port?)?
Not a live OS. A Virtual Machine is just that - a Virtual computer. The OS installs in it just like it would in a real computer. Only with lower performance due to hardware emulation overhead. By the way, your later post suggests that your hardware configuration 'may be' questionable.

> I'm considering jumping  into 12.04. perhaps that version is more stable.
Ubuntu 12.04 is an LTS ([Long Term Support]("https://wiki.ubuntu.com/Releases")) version and is highly recommended, 64 bit if your system supports that.
To ensure the integrity of the downloaded iso, I personally recommend to [download via torrent]("http://www.ubuntu.com/download/desktop/alternative-downloads"), since hash checking is part of torrent protocols.

> **interfacer said:**
> So this graphics problem could explain why terminal is there but not showing properly in normal mode?
Probably. And with 64MB graphics adapter, I doubt if your system is even capable of running a VM in it.

What is the overall hardware configuration of your computer? (CPU, RAM, Graphics)

To run default Ubuntu with Unity desktop environment, at least 1GB RAM is recommended. To run a virtual machine in it, you'll need extra amount of RAM (as much as the OS running in the VM would require + slightly more for emulation overhead).

If you have less than 1GB RAM, you should consider a lighter version of Ubuntu, like [Xubuntu]("http://xubuntu.org/") or [Lubuntu]("http://lubuntu.net/").

By the way, VirtualBox is much lighter than VMware and is available in default Ubuntu repositories.

---

