---
title: "seeming GUI not starting, hanging on boot"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by apprentice34 on 2012-03-23
Hi, first time poster here

I had Oneric 64 bit installed, and in the system settings I noticed under graphics it did not recognize my graphics card (Nvidia Geforce GT 425m - CUDA - 1GB). Under system info it lists graphics as unknown and experience as standard. I wanted to see if i could get it to reconize the card, so I started messing with some random drivers or something under default software application (i forget what its called). After installing and eventually rebooting, the boot hangs after displaying the purple background and sometimes briefly flashing the ubuntu start up screen. it then goes on to list some processes or something, and one of them fails, i can't tell which. 

it then hangs at *checking battery state.. , and usually goes on to display some other data if i leave it there for a while. 
[http://i.imgur.com/70ZEw.jpg](http://i.imgur.com/70ZEw.jpg)

I remember seeing some thread that said to run lsmod, and run some other command, changing i think a .conf file, and changing the word nvidia under drivers to nv. 
I was also told to try gksu jockey-gtk , I'm going to do this and report back. 

I'm currently on the same computer on a oneric live cd, and when I run lsmod it says it is running some nouveau drivers or something, where when run it on the actual computer it doesn't say nouveau or nvidia or nv. 

Thanks very much for any help!

---

### Post by wildmanne39 on 2012-03-23
Hi, try what is in this link it should allow you to boot so you can fix your driver problem.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by apprentice34 on 2012-03-23
Ill give it a shot, however I feel as if my problem is because of the graphics drivers being messed up, opposed to deeper problems as the link you posted seems.

---

### Post by wildmanne39 on 2012-03-23
That is what it is for the graphics driver and other things along that line.

---

### Post by apprentice34 on 2012-03-23
So i finally did the gksu jockey-gtk command i said I was going to do, by doing a standard boot and hitting ctrl alt f1 when it started hanging to bring up the terminal. after entering the command I got this warning:

(gksu:1640): Gtk-WARNING **: cannot open display:

I then tried the link you gave me, and started to try the 

[SIZE=4][B]How to permanently set kernel boot options on an installed OS
[/B][SIZE=1]
part of the tutorial. 

I entered 

[/SIZE][/SIZE]gksudo gedit /etc/default/grub

in the same area as before, and got this warning:

```
(gksudo:1698): Gtk-WARNING **: cannot open display:
```Thoughts?

---

### Post by wildmanne39 on 2012-03-23
Hi, first when you ran that command and got the error were you in the ubuntu desktop in the terminal? or was after you hit ctrl+alt+f1? it needs to be in the terminal.

You probably can remove the driver from additional drivers then reboot and you will not need to make it permanent.
Thanks

---

### Post by apprentice34 on 2012-03-23
I was logged in to my account, on the command line, but not on the live cd. Should i try it on the terminal on the live cd desktop?

to clarify, when the boot hangs when it says check battery state, i press ctrl alt f1, and it clears the screen and displays a login option, in the same style black and white text. I entered my info, and it brought up some kind of command line/terminal i think.

---

### Post by wildmanne39 on 2012-03-23
Hi, boot ubuntu then open a terminal like this ctrl+alt+t then enter the code to make it permanent but I would try to remove the driver from additional drivers first.
Thanks

---

### Post by apprentice34 on 2012-03-23
I'm assuming you mean my installation, not live cd.

How do i remove the driver from additional drivers?

---

### Post by wildmanne39 on 2012-03-23
Hi, open dash type add then click on additional drivers it will open and there should be a driver installed for your system because you said you installed one, then just click to deavtivate it then reboot.
Thanks

---

### Post by apprentice34 on 2012-03-23
Sorry but im not sure what your talking about. On the system settings under additional drivers it says there are no proprietary drivers used on the system. but that is under the live cd. If i open the terminal under the live cd, and type lsmod, it gives me a list of things that I think may be or are similar to drivers. nouveau is present. If i type lsmod under the installation, it doesn't list nouveau I believe. i don't know how to get to additional drivers under the installation, because there is no GUI

How do I find additional drivers under the installation?

Edit: i'm really new to ubuntu and linux so sorry if i don't understand at first

---

### Post by wildmanne39 on 2012-03-23
Hi, you need to boot ubuntu from your hard drive using the link I gave you, you will need to read that page carefully there are directions there for different scenarios.
Thanks

---

### Post by apprentice34 on 2012-03-23
I'm going to try to translate this in a form that I can understand, so please correct me when I get stuff wrong

The options presented in the link are:

**nomodeset **tells the kernel to not load drivers from the kernel immediatly and instead use the BIOS for the graphics, until X server starts/is loaded. The problem with this is that I think X server is a part of nvidia and as far as I can tell I do not have any functioning parts of nvidia left on my system. 

**acpi** options seem to function deeper, involving the kernel-BIOS more on a BIOS area. the **osi **option seems to deal with LCD backlights, and fans, and the like. I do not think this will affect my situation. the **off **option seems like it will disable crucial parts of my system and it doesn't look like it will do anything to help my system either.

[SIZE=2]**Noapic and nolapic **options seem to affect maybe even deeper BIOS problems, and I think my problem is on the kernel level.

[/SIZE]**[SIZE=2]vmalloc=xxxM [/SIZE]**[SIZE=2]seems to only affect 32 bit systems, and my installation is 64 bit on my 64 bit laptop. 

The next few options focus on the live cd and seem to make the assumption that the live cd itself won't start the GUI or something similar, which is not my problem considering the live cd works fine. 

The next option involves the installation and temporarily doing nomodest, which I haven't tried but I guess I will try now. 

The next option I tried and didn't work, I posted the errors I got. 


[/SIZE]

---

### Post by apprentice34 on 2012-03-23
So I just tried the temporary boot option. I went into the grub, and went to the linux /boot line. The end of the line was 

quiet splash vt. handoff=7

I added nomodeset to it, so it looked like 

quiet splash vt. handoff=7 nomodeset

I then pressed ctrl x to boot. It went to a purple screen and then went to a black screen, which i am currently looking at.

Should i try again? I'm not sure how excactly i was supposed to add nomodeset to that string of text, the tutorial is unclear on that.

Edit: if it helps, I think i just need to reset the part of the kernel that deals with graphics or something, to he state it originally comes with in the live cd for example.

---

### Post by wildmanne39 on 2012-03-24
Hi, try this it will make it simple if it works.

Go back into the grub menu then choose recovery, then I believe it will say root with networking choose that option then run these commands one at a time.
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
make sure you have internet access.
Thanks

---

### Post by apprentice34 on 2012-03-24
Awesome!

It's working now. 
I shift booted and went into recovery mode, chose the fsck option, then chose the root networking, and entered those two commands. Out of impulse i hit the grub reload/update option, i dont think that probably did anything though. 

Anyways, when the computer started up the graphics were at a very low resolution and it listed the graphics in the system info as VESA: Intel Ironlake Mobile Graphics. I then did an update (apt-get update && apt-get upgrade) and rebooted, and now the graphics are back to normal.

Thank you my good sir!

---

### Post by wildmanne39 on 2012-03-24
Hi, your welcome! I am glad I could help.

---

