---
title: "Screen won't wake up during gparted resize"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by junk_mail77 on 2014-04-22
I've done a lot of searching and reading and am pretty sure I might be hosed but I wanted to ask for some input before making a bad situation worse. This is my first attempt at installing Linux.

I am trying to get Ubuntu 14.04 installed and dual-booting on my old XP box with 2GB of RAM and a 150GB primary hard drive. My main problem is that my screen went to sleep shortly after I kicked off the Gparted resize of the windows partition and I can't wake it up. Based on my research, I'm guessing I have an Nvidia graphics card, as there seems to be some issues with those drivers (I've seen references to the "nomodeset" fix). Unfortunately the box is about 10 years old and I can't remember the detailed specs, such as what graphics card I have.  Here's what I've done:

1. Followed all the steps to cleanup my windows partition (cleanup files, CHKDSK, Defrag)
2. Booted into 14.04 via a Live USB stick
3. Set Gparted to resize my 150GB windows partition to 115GB
4. After about 5 minutes the screen went to sleep and I have been unable to wake it up
   - I tried different mouses, typing on the keyboard, un/re-plugging the monitor power, tried both DVI and VGA cables

As of right now the resize has been running for about 16 hours. The hard drive light has been on and solid green every time I check it, so either the resize is still happening or something is stuck/frozen. I've read that the resize can take a while, but 16 hours seems to be quite long. I'm planning to leave it for 48 hours just to be 110% sure it's a lost cause.

If the hard drive light is still going in 48 hours then my plan is to kill the box and try booting and see what happens. My guess is that I'll have to get out my Windows recovery discs and spend some fun time trying to get the box booting to windows again. All my files are backed up offsite (Crashplan), but it will take a long time to re-download everything so I'm at least hoping I can salvage things and get it booting into windows again without having to reinstall.

If anyone has any additional suggestions to try besides forcing a reboot on the box I'd love to hear them.

---

### Post by junk_mail77 on 2014-04-23
No thoughts or confirmations?  Oh well.

---

### Post by gedakc on 2014-04-23
You might consider trying to remotely connect to your PC over the network.  For example if your PC or Live CD is running an sshd daemon, then you could try connecting to the PC using **ssh**.  Once connected you could check out the machine status using commands like **iostat**, **ps**, and **dmesg**.

If your Windows partition has had only the end (right edge) moved left, then the operation should complete relatively quickly.  However, if the start (left edge) of the partition was moved then the entire partition will be moved and this can take a very long time, especially for large drives on older computers.  Also if the partition has been moved, then you might need to restore the ability to boot as you mentioned in your earlier messages.

---

### Post by junk_mail77 on 2014-04-23
Thanks, gedakc. I ended up rebooting. Windows booted fine and the partition was not resized, so it seems to have failed for some reason. I'll attempt it again, but not before setting the screen to never turn off!

---

