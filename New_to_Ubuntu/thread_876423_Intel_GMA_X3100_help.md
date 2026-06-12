---
title: "Intel GMA X3100 help?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by xnerdx on 2008-07-31
Hey,
   here is my problem. I recently purchased a Toshiba A205-S5000 laptop, on sale at walmart. I am very new to the Linux based OS's but after maybe 2 hours I managed to get the wireless card to work. I have gotten that far, the problem now is my graphics card. The laptop came with Windows Vista Home pre-installed, I formatted the HDD and replaced it with a fresh Ubuntu 7.10 OS and upgraded to 8.04 and installed all the latest updates. I have done research on the GMA X3100 and it should have 300 something MB of GP memory. On ubuntu I can't even set my Appearance Preferences to Normal... I entered this code into the terminal
```
lspci | grep VGA
```
I got this return line
```
michael@michael-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

```
Do I have the correct drivers? Why can't I improve my Visual Effects? Please can someone help?

---

### Post by insane_alien on 2008-07-31
hmm the X3100 should work fine out of the box. mine does at anyrate. 

ubuntu definitely has the drivers for it so no worries there and that is the correct return code for lspci.

it is strange that you can't change your appearence settings(i have issues there as well, but its a different issue thats solved by setting them to normal)

---

### Post by daimaru on 2008-07-31
EDIT:total blackout...

---

### Post by phidia on 2008-07-31
There isn't a special install for that card. The driver is already in the kernel I believe. You can look at your /etc/X11/xor.conf but if "intel" is the listed driver that's the best you can do with that card right now in linux. 
If the driver is listed as vesa or fbdev then you should be able to get better performance by getting the intel driver installed. You can take a look at [this]("https://help.ubuntu.com/community/Video#Intel") or search the video & multimedia forum too.
BTW your output doesn't list the X3100 unless that's the actual name it has and X3100 is a marketing moniker.

---

### Post by xnerdx on 2008-07-31
I checked the xorg.conf file and it is listed as vesa! My code reads as follows
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection
```
So my question is, how do I install the intel driver??

---

### Post by xnerdx on 2008-08-03
Can someone please assist me in installing the intel drivers for my graphics card?

---

### Post by ET! on 2008-08-03
the driver should come with the os installation....i previously had a GMA3100 and it worked fine... no issues whatsoever....did you search the intel website for driver(i dont think there is one)...i changed my card to an nvidia and linux prompted me to change the driver..after changing it everything worked fine

---

### Post by CatKiller on 2008-08-03
> **xnerdx said:**
> I checked the xorg.conf file and it is listed as vesa! My code reads as follows
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection
```
So my question is, how do I install the intel driver??

You can edit that file with ```
gksudo gedit /etc/X11/xorg.conf
``` Where it currently says "vesa", put "intel" instead. You can restart X with Ctrl-Alt-Backspace.

If X doesn't start for some reason, you can press Ctrl-Alt-F1 to get to a virtual console and use ```
sudo nano /etc/X11/xorg.conf
``` to change it back.

---

### Post by xnerdx on 2008-08-03
Wow, I never would have guessed that after 5+ hours of research I would find my answer to be so simple as typing 5 letters! Thank you very much though, it was getting to be a very large hassle! Hopefully at this point I will not have many more problems... anyways I thank you all and I have on more question. My last question is how can I write and compile C# code without a windows virtual system or dual booting? I don't know how I would do this as of now due to the fact that I can't install .net framework... as far as I know. Any assistance would be very much appreciated!

Freedom is a way of saying there is no way out.

---

### Post by jonathanmotes on 2008-08-08
For C# development in Linux, you would have to use the Mono Project's tools. 

Have a look at these links:
[http://www.mono-project.com/](http://www.mono-project.com/)
[http://www.mono-project.com/CSharp_Compiler](http://www.mono-project.com/CSharp_Compiler)

---

### Post by xnerdx on 2008-08-09
Thank you very much!

---

