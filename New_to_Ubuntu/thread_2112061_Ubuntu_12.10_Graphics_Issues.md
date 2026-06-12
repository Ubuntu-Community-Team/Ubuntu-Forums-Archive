---
title: "Ubuntu 12.10 Graphics Issues"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by pdb61 on 2013-02-03
Hi

**_Machine Details_**

I have installed Ubuntu 12.10 on a Dell Dimension 2400 which has 2Gb of RAM, 2.2Ghz CPU , 2 hard drives (80Gb + 30Gb) and a Nvidia GeForce 6200 PCI graphics card. This may/may not be relevant but the Dell Dimension 2400 also has an Intel on board graphics card (82845G/GL[Brookdale-G]/GE). I appreciate that the machine is not state of the art but I am not trying to do anything graphical intensive with it. Previously, it had Windows XP running on it without any complaints.

**_Issue_**

My problem is that after installing the Nvidia drivers for my graphics card, my display is unusable when I log into Ubuntu/ Unity. However, the display is functioning in Gnome. 

I would be happy to live in this state but I am unable to use any of TTY consoles (Cntl-Alt-F1 thru F6). The console has hung and displays an i915: render error detect, EIR: 0x00000010. I see this whether I fire up Unity or Gnome.

**_Question_**

What is the issue with Nvidia/ Unity? What is the error I am seeing in the console window? 

Any thoughts on how to resolve this would be gratefully received. Googling has left me with bleeding fingers.

---

### Post by stinkeye on 2013-02-04
Not sure why gnome works but unity doesn't.
Don't have Gnome installed to test.
Firstly I would check the nividia driver is actually being used...
```
lspci -nnk | grep -iA2 vga
```


After installing the nvidia driver in Unity 12.10 I had to purge the driver,
install linux-headers and reinstall the driver before it would work. See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12338523&postcount=2").

P.S. Since then I have uninstalled the nvidia driver as the nouveau driver
works just as well for normal desktop use with my GeForce GTX 550 Ti card.

---

### Post by carl4926 on 2013-02-04
Hybrid graphics can be problematic

---

### Post by Mark Phelps on 2013-02-04
The main problem is the hybrid graphics -- it's not a simple matter of just installing video drivers.  See below:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by 3rdalbum on 2013-02-04
It's not hybrid graphics. It's a computer that came with Intel graphics, but the person added a discrete graphics card. Hybrid graphics is where the computer can switch between the two depending on performance, with the output coming from a single VGA or DVI port no matter what GPU is in operation. This person's computer predates the introduction of hybrid graphics, and to my knowledge there's never been an Intel/Nvidia combination (only Nvidia/Nvidia or ATI/ATI).

@pdb61: Make sure the monitor is plugged into the Nvidia graphics card, and use your computer's BIOS to turn off the integrated graphics entirely.

---

### Post by pdb61 on 2013-02-04
Firstly, thanks for the input. 

3rdalbum is correct in that the PC came with an on-board Intel graphics card and that I have added a PCI card. I am not at my home PC but I believe that the Nvidia card is being used for 2 reasons. First, the monitor is plugged in to Nvidia card not the original on-board card and second, lspci | grep VGA shows the Nvidia card (but not the on-board card)

@3rdalbum: I can confirm that the monitor is plugged into the Nvidia graphics card. Unfortunately, my BIOS settings don't allow for me to turn off the integrated graphics card - the settings show ON-BOARD/AUTO only - I have selected AUTO.

I have flashed the PC with the latest (albeit old) BIOS.

The solution in Windows appears to be to use the Device Manager to deactivate the on-board card.([http://en.community.dell.com/support-forums/desktop/f/3515/t/8244525.aspx](http://en.community.dell.com/support-forums/desktop/f/3515/t/8244525.aspx) .. see the final post). Not sure if there is an equivalent approach in Ubuntu.

Thanks again for any input.

---

### Post by carl4926 on 2013-02-04
On all my machines with onboard and then a added PCI graphics, the adding of the PCI device automatically disabled the onboard.
I know there are BIOS toggle switches to do the said same, but I never needed to use them.

I'm moving graphics cards around all the time (nvidia is all I use) and it's water off a ducks back...

---

### Post by pdb61 on 2013-02-04
Would really appreciate any other thoughts on this.

Specifically, what is the issue with Nvidia/Unity and what is the "i915:: render error detect, EIR: 0x00000010" error I am seeing in the console window? 

Thanks

---

### Post by carl4926 on 2013-02-04
Have you tried blacklisting 'i915' ?

---

