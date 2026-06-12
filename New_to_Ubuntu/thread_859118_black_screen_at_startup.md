---
title: "black screen at startup"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by ET! on 2008-07-14
i have been using linux for a while...i have this strange problem(which occurs in an arbitrary way).every time i boot linux i get a black screen after the loading bar completes...it takes the login screen for a while to appear...but i can still type the username and password(while the screen is still blank)and the desktop appears after some time(and with some flickering)...why could this be

---

### Post by jbrown96 on 2008-07-14
It could be the X server starting. You could try to edit your grub entries (/boot/grub.menu.lst) and change "splash" to "nosplash" and see if that helps at all. 
Are you using proprietary graphics? The Nvidia splash screen may also cause some problems.

---

### Post by ET! on 2008-07-14
nope iam using intel onboard graphics...but the option is already no splash...so what do i do now

---

### Post by jbrown96 on 2008-07-14
Try to change your login manager. I don't remember how to do it in Gnome (either in preferences or system). xlogin or the most generic one you can find

---

### Post by Pastortom on 2008-07-14
> **ET! said:**
> i have been using linux for a while...i have this strange problem(which occurs in an arbitrary way).every time i boot linux i get a black screen after the loading bar completes...it takes the login screen for a while to appear...but i can still type the username and password(while the screen is still blank)and the desktop appears after some time(and with some flickering)...why could this be



Mate, while trying to find a solution for the same problem on my own computer I found the same solution for your problem.

When you boot your computer and Grub shows up, manually edit the Ubuntu normal choice and add the following tags at the end of the kernel line:
acpi=off vga=773

you might also wanna remove the 'splash' completely.. 

. I had the 100% exact same issues as you with all kinds of Ubuntus trying to load GUI (after seeing the loading bar fill up and you see the screen flicker).. but when I added ACPI=off at the end it fixed my problem..

At the moment I also remove the tag "splash" and add the tag "vga=773" to make sure the video resolution isnt the problem during bootup..  

Good luck mate, and I hope this saves you 12 hours of hard work which Ive been through to accidently find this out..

---

### Post by beeman1266 on 2008-07-22
> **Pastortom said:**
> Mate, while trying to find a solution for the same problem on my own computer I found the same solution for your problem.

When you boot your computer and Grub shows up, manually edit the Ubuntu normal choice and add the following tags at the end of the kernel line:
acpi=off vga=773

you might also wanna remove the 'splash' completely.. 

. I had the 100% exact same issues as you with all kinds of Ubuntus trying to load GUI (after seeing the loading bar fill up and you see the screen flicker).. but when I added ACPI=off at the end it fixed my problem..

At the moment I also remove the tag "splash" and add the tag "vga=773" to make sure the video resolution isnt the problem during bootup..  

Good luck mate, and I hope this saves you 12 hours of hard work which Ive been through to accidently find this out..

could you please explain a little bit how a newb can go about editing Grub and add those tags you mentioned. Thanks for your help. This blank screen is not much fun.

---

### Post by lossfound on 2008-07-24
Beeman, I was having a similar problem on my Thinkpad R61 and was able to solve it just by disabling the splash screen (changing "splash" to "nosplash"). This simultaneously solved a problem I was having with wireless configuration. 

You can try adding options at boot time by pressing "e" to edit the startup parameters for your normal kernel etc. boot option, then pressing "e" again to add parameters to the end of the "kernel" line. Press Enter to save the temporary changes you made, and "b" to boot. 

If you find the magic combination that solves your issue, do an Alt-F2 and run this:
gksudo gedit /boot/grub/menu.lst

Locate the area of the file that contains your normal GRUB boot commands - they should look familiar from your prior experiments - and add the magic words as needed, then save.

---

### Post by beeman1266 on 2008-07-25
Thanks for the tip lostfound. I've tried taking away 'splash', adding 'nosplash', adding those settings mentioned above and nothing works. In the end, I followed another post which suggested experimenting with the grub bootup settings, by editing grub at startup with 'vga =ask' at the end of the kernel, and then trying out different video monitor settings. i've settled on vga=1, which seems to work 9/10 times but still isn't perfect... i should mention this is for a dell inspiron 1100, ubuntu 8.04. still, i'm looking to go 10/10 if anyone has any other tips.

---

### Post by beeman1266 on 2008-07-25
sorry for messing up your name lossfound

---

### Post by lossfound on 2008-07-26
Beeman, no worries about my dumb login :) Good luck finding the magic VGA setting, I really hate trial-and-error things especially when they get so crazily intermittent like that. Maybe try another live-CD distro in the drive, like Knoppix or so, and see if it has success with a particular mode?

---

### Post by tyreafus on 2009-03-22
I'm having a similar issue, except that when I don't get the black screen, after login the desktop begins to load, but doesn't finish.  I have a mouse cursor, which I can move, and the normal mauve-ish background(no desktop image), but nothing more loads.  I've tried letting it sit like this for extended periods of time but it never progresses.

I've tried booting into recovery mode and running xfix to no avail.

The Ubuntu version is 8.10.  What is most frustrating is that I had a working install of the exact same version, installed from a CD made with the same ISO file, only days ago.  I did a reinstall due to VNC server issues and now I can't get the thing to fully start.  I didn't have to do anything special before, and I've done the CD error check and it comes up fine.

I will try vga=1 but I don't know if it will help given that my issue isn't so much the black screen as it is the fact that the desktop(gnome? xserver?  I'm a newb so I'm not sure what does what) never fully loads.

If anyone has experience troubleshooting this, please let me know.

---

### Post by tyreafus on 2009-03-22
I should mention that I'm also doing this on a Dell Inspiron 1100 laptop.  I have tried installing with auto-login and without.  No luck.

---

### Post by ugm6hr on 2009-03-22
This sounds like a RAM or graphics card issue.

How much RAM?

Have you installed Intrepid on the same computer before?

Can you boot into the Recovery Terminal?

If yes - try removing Compiz from there:

```
apt-get remove compiz-core
```

---

### Post by tyreafus on 2009-03-22
Update:

I updated the motherboard to the latest BIOS(see [here]("http://www.geocities.com/randomnumbergenerator2001/").)

Also, I realized that the first time I installed Intrepid, I had to do a dpkg before it would display properly.  I tried this and realized that it wasn't seeing the servers.  Checked my /etc/network/interfaces', realized that it didn't have a configuration for my NIC card.  I must have left the network cable out when I did the install.  I added the following to this file using nano /etc/network/interfaces at the root terminal(started in recovery mode)
```

auto eth0
iface eth0 inet dhcp
```

I then re-ran dpkg from the recovery menu.  It's downloading now, will update when it finishes.  Hopefully I'll have a working system then...

---

### Post by tyreafus on 2009-03-22
And we are a GO!

After the updates finished, did a reboot, didn't have to do anything with the boot command, it brought up the full GNOME.

Apparently the 8.10 base install doesn't work with my laptop, but the updates fix that.

Would highly reccomend running all updates if you're still having display issues.

---

