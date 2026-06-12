---
title: "Gutsy Framebuffer HOWTO"
date: 2007-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by ckth on 2007-12-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
*EDIT: User [jonppe]("http://ubuntuforums.org/showpost.php?p=5534454&postcount=4") confirms that this HOWTO works on Ubuntu Hardy as well.*
				**_DISCLAIMER_**

The following guide is intended to help set up a framebuffer device on Ubuntu 7.10. It involves grappling with kernel modules and Grub settings, and while it is elementary, please attempt it only if you have a fair idea of what you're doing. 
I cannot guarantee that everything will work out fine on your hardware. (Although virtually all graphics hardware support framebuffers, there are exceptions to the applicability of the framebuffer drivers.)
The Gutsy framebuffer issue is still being tackled as a bug (See Additional Information at the end), and I take no responsibility for support: follow the instructions at your own risk.

If you find any glaring flaws (or dangerous typos), please let me know so I can fix them before they cause any damage. To the best of my knowledge, these tweaks work (for me, and for several people at launchpad.)

**_HOWTO: set up the framebuffer in Gutsy Gibbon._**

0. What is the framebuffer, and why do you need it?
It is a method of rendering the screen that bypasses the standard graphics card -> API -> Application Software route. The details are fuzzy[1], it would be great if someone could explain briefly.
More relevantly, framebuffer rendering can be carried out without an X session in the way, meaning that graphical applications can be run off the virtual consoles! Now, it's not that flashy, but it is functional- and you can play movies, images and slideshows, view PDFs, browse the net (with full graphical functionality, not just in text mode), and (obviously) listen to music, meaning that you can do most of the tasks usually consigned to X on the ttys. This is great for old machines, and for the times when your Xserver is down. 
(In addition, you can mix music, download torrents, chat and [do a lot more from the CLI]("http://ubuntuforums.org/showthread.php?t=260946")-  the framebuffer is like the icing on the cake.) 

1. Gutsy does not have the kernel framebuffer module(s) enabled by default. This is not a bug: The reason for this is given in /etc/modprobe.d/blacklist-framebuffer:
> # Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem.  For this reason we
# never load them automatically.  

Check to see if it's already enabled in your machine. Oddly enough, some fresh Gutsy installs seem to have the framebuffers enabled by default, even though all fb drivers are blacklisted (disabled), while *all* upgrades from Feisty appear to have this problem. If the output of 
```
fbset -i
``` 
is "/dev/fb0 not found" or some variant of this, your machine's framebuffer modules are not loaded.

If you get a description headed "Frame buffer device information", you can skip to 4.

2. Append fbcon[2] & vesafb[3][4] to the flie /etc/initramfs-tools/modules. (-if you're using Intel architecture. If you have a different graphics card, especially Nvidia, check [4]. ATI users might want to try appending radeonfb instead of vesafb, although the latter is supposed to work with *all* graphics cards.)

This tells the kernel to load these modules into memory (after updating the kernel, see below).

If you wish to automate the process, use the code here (It's safer to do it manually):
```
echo "fbcon" | sudo tee -a /etc/initramfs-tools/modules
echo "vesafb" | sudo tee -a /etc/initramfs-tools/modules
```

"Un-blacklist" the vesafb module. You need to comment out the "vesafb" entry in the file /etc/modprobe.d/blacklist-framebuffer. 
To automate the process (Again, it's safer to do it manually):
```
sudo sed "s/vesafb/#&/" -i /etc/modprobe.d/blacklist-framebuffer
```

3. Update the kernel(s) on your machine:
```
sudo update-initramfs -u -k all
```

4. Assuming you've not set a vga mode in your Grub boot options yet, you need to include vga=xxx, (where xxx is a number corresponding to your framebuffer resolution and colour depth) in your Grub menu.lst.

To see what resolutions and colour depths are supported by your graphics card / monitor combination, type in
```
sudo hwinfo --framebuffer
```
and choose from the resulting list. (You may need to install the package 'hwinfo' with aptitude/apt-get first.)
Pick a resolution, and look [here]("http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html#ss5.3") to find the corresponding hex code. It is essential that the code be entered in hexadecimal and not decimal, as Gutsy seems finicky about decimal declarations[5].
 
5. Find the defoptions line in /boot/grub/menu.lst, and append vga=0x317 (with your code replacing 0x317) to the end of the line. 
In my case, the line reads
# defoptions=splash vga=0x317

The following line automates the process, use it only if you understand what it does:
```
sudo sed "s/^# *defoptions.*$/& vga=0x317/" -i /boot/grub/menu.lst
```
(Otherwise open up a text editor and do it manually)

Alternatively, the vga option can be specified at the Grub menu during boot. Press e, then add vga=0x317 at the end of all other boot options and press enter. This is safer for diagnostics, as it is one time only.

6. Finally, update Grub, and you're all set. 
```
sudo update-grub
```

7. Reboot the pc, Turn off the resource hungry X, switch to the virtual consoles and revel in the high res glory. 


_**References & Caveats **_
[1] A better definition of a **framebuffer device** is here: [http://tldp.org/HOWTO/Framebuffer-HOWTO-3.html](http://tldp.org/HOWTO/Framebuffer-HOWTO-3.html)

[2] **"fbcon"** stands for FrameBuffer CONsole; meaning that a high res fully featured terminal is rendered by the framebuffer device. If your framebuffer is working, the "virtual console" you see as tty1 is a framebuffer console. 
More information here:  
[http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt](http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt) 
(Advanced) [http://racl.oltrelinux.com/tutorial/fbcon.html](http://racl.oltrelinux.com/tutorial/fbcon.html)

[3] **"vesafb"** is a generic framebuffer driver for Intel architecture, but works on several graphics chipsets. (Much like Xvesa works on several graphics chipsets.) It is what can be called "A Safe Bet".
[http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html)

[4] While there is an entry in /etc/modprobe.d/blacklist-framebuffer named nvidiafb, reports suggest that it is *not* required; vesafb suffices for *most* cards. In the event that vesafb does not work for you, you can add in nvidiafb in the modules file and comment it in the blacklist-framebuffer, and carry out the same sequence of operations as for vesafb.
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/comments/108](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/comments/108)

[5] Finicky decimal declarations: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/comments/161](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910/comments/161)


**_Additional Information:_**
If you are familiar with the "modprobe" command, you could load the modules yourself from the console, along the likes of "sudo modprobe vesafb". I'm not (familiar), so hopefully someone else will elaborate on this.

The framebuffer (or the lack, thereof) issue is being considered as a critical bug in Gutsy Gibbon. ([https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910))

This issue has been discussed before in the forums here:
[http://ubuntuforums.org/showthread.php?t=454392&page=3](http://ubuntuforums.org/showthread.php?t=454392&page=3), which is where part of the solution was gleaned from.

If you wish to know how framebuffer apps may be used to see videos or view images (among other things), check out: [http://ubuntuforums.org/showthread.php?t=260946](http://ubuntuforums.org/showthread.php?t=260946)

There is some general information on framebuffers to be found in the context of Gutsy Gibbon [here]("http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/").

Lastly, To undo the changes made, you could either backup all text files you edit, or since they're just one line (one word?) edits, you could revert to the older versions easily. Just remember to sudo update-initramfs and sudo update-grub after restoring the originals.

Happy framebuffering!

---

### Post by silentb on 2008-04-19
Thanks for this HOWTO!!!

I have a Geforce4 and I am not able to use nvidiafb und Nvidia's official xorg driver together (in Hardy - I don't know about Gutsy). While nvidiafb works without problems, Nvidia's driver simply stops working So I went back to vesafb. It's less speedy, but it's ok.

Another issue: My console apps are unable to use my mouse. Though, that's another topic probably.

---

### Post by rayburn on 2008-06-03
Thank you so much for this howto, I have searched in vain via Google for just this information! I used it in a server installation of Debian, and it worked perfectly, thanks again.

---

### Post by jonppe on 2008-08-06
Thanks a lot. It took me ~4 hours of despair to find this page.

I can confirm these instructions work also on Hardy.
I had to do some minor differences:

1. vesafb didn't work on my ati mobility radeon HD2400; radeonfb works fine.
2. command: 'sudo hwinfo --framebuffer' actually shows also hex values for  video modes and their different from those of the vesafb modes.

---

### Post by ckth on 2008-08-11
@silentb, rayburn: You're welcome!
You'll need to install gpm (a console mouse server) to enable mouse support. (A simple apt-get install gpm will do.)

@jonppe: Thanks for testing it on Hardy, I'm updating the HOWTO to include support for Hardy.

---

### Post by sirlatrom on 2008-09-22
> **rayburn said:**
> Thank you so much for this howto, I have searched in vain via Google for just this information! I used it in a server installation of Debian, and it worked perfectly, thanks again.

You'd want to install the gpm package then, that's a console mouse.

---

### Post by Mr.max on 2008-12-15
Tks for this howto. It helps to run SDL application using framebuffer.

---

### Post by krzysz00 on 2009-01-04
How do I increase the font size?

---

### Post by rvdavid on 2009-09-24
> **krzysz00 said:**
> How do I increase the font size?

I know that this is an old post, but I thought I'd add to this since I've been looking into enabling the framebuffer for my install: 

I'm currently using Ubuntu Karmic A6. 

Anyway, to change the font size, To select my own font size I simply run a dpkg-reconfigure - this fires the consle-setup configuration prompts and I can select the font and font-sizes I want to use. 

```

$sudo dpkg-reconfigure console-log


```

HTH.

---

### Post by mo0nykit on 2009-10-10
Hi! May I suggest we update the title, because it also works for me in Jaunty. This is what I did:

[LIST]
[*]I installed my own custom kernel **(This is not required)**. But the fact that installing a new kernel (and its corresponding initrd) might cause the framebuffer console **fbcon** and **vesafb** to be NOT loaded during boot, after the Nvidia proprietary drivers have been installed.
[*]While running under my new kernel, I installed the Nvidia proprietary drivers using the script I downloaded from their official site:
[/LIST]
[INDENT]```
# <switch and login to a virtual console with Ctrl-Alt-F1>

# Stop the X server
sudo /etc/init.d/gdm stop

# Install the Nvidia proprietary drivers (the filename is just an example)
sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg1.run

# Inside the installation program, it will ask if it should
# download a precompiled kernel interface. Say NO.
# Let it compile a new one. This will be successful if you have
# installed the corresponding linux-headers for the kernel that you
# are running.

# Also allow the program to automatically update the xorg.conf file
# so that you can use the Nvidia proprietary drivers in the X Server

# Start the X server
sudo /etc/init.d/gdm start
```[/INDENT]
[LIST]
[*]My problem started at this point. If I go back to the virtual console, everything is garbled.
[*]Go back to the X Server (Ctrl-Alt-F7) and do the following
[/LIST]
[INDENT]```
# Edit the /etc/initramfs-tools/modules file and add the following 
# lines in any order
vesafb
fbcon

# Edit /etc/usplash so that your splash screen will look good. This
# should correspond to the vga setting you will set in menu.lst
xres=1024
yres=768

# The two modifications above will only take effect upon updating
# the current initrd
sudo update-initramfs -u

# Edit /boot/grub/menu.lst and add the following boot option to the
# kernel you are using. This code is the decimal form for 1024x768.
vga=792

# In order to know all the other framebuffer modes that your video
# card supports (they are presented in hexadecimal)
sudo hwinfo --framebuffer
```[/INDENT]
[LIST]
[*]That's it. You should now be able to use your virtual console on the next reboot.
[/LIST]

---

### Post by markuman on 2009-11-12
I'm on Ubuntu 9.04 with an AMD Geode Chip and got still the same errors with /dev/fb0: No such file or directory.
The modules are still loaded, any suggestions?

---

### Post by kio_http on 2009-11-12
Gusty is very old now time to close this thread!

---

### Post by markuman on 2009-11-13
> **kio_http said:**
> Gusty is very old now time to close this thread!

=D>
But problems still existing!
Even in new Releases....

---

