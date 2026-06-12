---
title: "[SOLVED] Unidentified Video Mode on Start-up!"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Redptc on 2008-07-02
I don't know how to fix this. Everything else seems to be going well with my new Hardy install. This problem crops up when booting and slows everything down.

I have Gutsy on a different partition and so, on exactly the same machine and configuration, this difficulty doesn't appear. On Hardy it shows up even though everything is precisely the same....

When booting, we get the advice: [I]Starting up...
                                    Unidentified Video Mode[/I] 

I am then given 30 seconds to select a mode or scan for a mode amongst a selection that doesn't appear the same as what I have. Despite what I select, or don't select, the system continues and boots everything correctly. The screen resolution is ideal but I shouldn't have this interruption in the boot process!

What can I do to correct this problem????

---

### Post by Redptc on 2008-07-03
Doesn't anybody Know how to sort this?

---

### Post by sayakb on 2008-07-03
At a terminal:
```
sudo apt-get install startupmanager
```
Then run it from System->Administration->Startup-manager and set the correct resolution there.

---

### Post by Redptc on 2008-07-03
Thanks *Linuxis* but I have done that only to find the resolution is correct in "Startup Manager'. Once booted, Hardy runs as it should and my resolution is 'spot-on'. The login screen is also the correct resolution.

My problem crops up immediatly after the Grub menu, when we normally get the warning *Staring Up....* The normal desktop then loads to the login screen and we get business as usual.

In my case, the advise about "Incorrect Video Mode" inserts itself immediately after and we have at least 30 to 40 seconds to wait for things to proceed.

I would like to eliminate this intermediate step!

---

### Post by shad0w_walker on 2008-07-03
It sounds like for whatever reason, grub is giving a dodgy resolution to the splash screen, which it wants you to correct before carrying on.

To fix this will take a little bit of tinkering with the grub menu file.

First off, open up the grub menu file by pressing Alt+F2 then running this command:

```
gksu gedit /boot/grub/menu.lst
```

That should prompt you for your password (To confirm you have the rights to perform the action) and then open up a text editor with the grub menu file.

In this file, look for the line that begins like this:

```
# kopt=root=
```

This line will have somemore stuff after that part, don't touch that, just leave a space and add this:

```
vga=<value>
```

<value> should be replaced by the code for the resolution you want to use. This link shows the various codes that are available, just find the one you want and put it in place of <value>

[http://manac.wordpress.com/2006/02/19/how-to-change-grub-menu-resolution/](http://manac.wordpress.com/2006/02/19/how-to-change-grub-menu-resolution/)

Once you have finished with this, hit save and close the text editor. Now reboot and see if it's fixed the problem. 

Good luck.

---

### Post by bab1 on 2008-07-03
see below

BAB1

There you go shad0w_walker beat me to it.  :p

---

### Post by bab1 on 2008-07-03
I believe there is a video section in grub's boot.1st file.  You should be able to set the video for the time grub is in charge.  For details try:> you@there$ man grub

BAB1

---

### Post by dodle on 2008-07-03
Check your /etc/X11/xorg.conf file and see if there are any resolutions under the "Screen" section that should not be there.

---

### Post by Redptc on 2008-07-03
Thanks Shadow, I did as you suggested and made the following changes;

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=60e2cb04-dd57-4cb3-ab0a-6eeaef0f5318 ro vga=795

I added 'vga=795' as you can see. Is this where it should be placed? It has not changed things.

I checked your link on resolutions and I think I picked the correct code for a Dell SE198WF, DefaultDepth 24, 1280x1024

---

### Post by Redptc on 2008-07-03
> **dodle said:**
> Check your /etc/X11/xorg.conf file and see if there are any resolutions under the "Screen" section that should not be there.

Thanks Dodle, that seems to be OK, there is a list but the one I want and the one in use is the first in the list; 1280x1024

---

### Post by Redptc on 2008-07-04
[COLOR="RoyalBlue"][/COLOR]> **Redptc said:**
> Thanks Shadow, I did as you suggested and made the following changes;

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=60e2cb04-dd57-4cb3-ab0a-6eeaef0f5318 ro vga=795

I added 'vga=795' as you can see. Is this where it should be placed? It has not changed things.

I checked your link on resolutions and I think I picked the correct code for a Dell SE198WF, DefaultDepth 24, 1280x1024

*I tried it with some other choices with no luck. I also tried to insert the vga=795 before the 'ro', no change!*

Its only 30 seconds but on boot-up, thats a lifetime!

---

### Post by shad0w_walker on 2008-07-04
Edit: I just realised why that might not have worked. Grub probably didn't update the actual entries with the new defaults. So give this a try and see if it works:

Open a terminal (Applications > Accessories > Terminal) and run this:

```
sudo update-grub
```

That will make grub regenerate the file to add the vga option to the actual entries read at boot time.


If that doesn't work, try this out
Run:

```
gksu gedit /etc/usplash.conf
```

See what the resolution is in there, if it's something odd, try changing it to 640x480, 800x600 or 1024x768 depending on your preference. If that doesn't work, I'm afraid I'm all out of ideas.

---

### Post by Redptc on 2008-07-04
Thanks Mate, no good. The resolution seems to be correct all round but I still get the 'problem' and I do appreciate your time.

Crazy idea, but I am going to physically change screens (monitors) and, probably back again, to see what happens. Nothing to lose!

Everything else is perfect, so this little flaw is a real pain.

---

### Post by shad0w_walker on 2008-07-04
That's really weird. Have you checked to see if it happens with any other boot options, like recovery mode or such? Let us know how you do, I'm always interested in what a mystery problem really is.

---

### Post by plucky on 2008-07-04
@Redptc


What is your video card?

Can you post output of ```
cat /etc/usplash.conf
cat /boot/grub/menu.lst
```

Do you know which menu.lst is the default?  i.e where does the MBR look for its menu.lst file.

---

### Post by Redptc on 2008-07-04
Hello Plucky, The warning reads...Unidentified Video Mode 31b. I 'triple' boot Win98,Gutsy & Hardy. If I select Gutsy no problem but if I choose Hardy it crops up. Same monitor device etc.

Video card/Device "Intel Corp 82810E DC-133 CGC [Chipset Graphics Controller]

Requested Output #1;
 
# Usplash configuration file
xres=1280
yres=1024

Requested Output #2; I posted the parts I thought were needed?

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.



## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=60e2cb04-dd57-4cb3-ab0a-6eeaef0f5318 ro

Does it provide any clues???

---

### Post by Redptc on 2008-07-04
WTF SMILIES???? replace with an 8  :confused:

---

### Post by Redptc on 2008-07-04
> **shad0w_walker said:**
> That's really weird. Have you checked to see if it happens with any other boot options, like recovery mode or such? Let us know how you do, I'm always interested in what a mystery problem really is.

No hesitation in recovery mode! Just loads up with script on the screen.

---

### Post by shad0w_walker on 2008-07-04
That's damn odd. I'd suggest you have a look at the grub menu file again and see if there are any obvious differences between the two boot entries (At the bottom of the file) ignore the 'single' option as that is what specifies recovery mode. Other than that, I'm out of ideas.

---

### Post by plucky on 2008-07-04
I was looking for the boot lines in the file,the ones that look like 
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro splash vga=791
initrd		/boot/initrd.img-2.6.24-19-generic
quiet


I have a pentium III with the Intel i810 vga chipset which was giving the same error,and what fixed it was removing the vga=791 from the kernel line.

Also it is worth updating the initramfs  with the command ```
sudo update-initramfs -u
``` after you have made the changes.


Good Luck

---

### Post by Redptc on 2008-07-05
That did it Plucky, I removed the reference to *vga=795* and it now bypasses the warning. 

You don't know (maybe you do) how irritating that was! 

Many thanks for your advise Plucky and I appreciate you responding to my call for help and providing the answer. 

Shadow, I think you were one step away from leading me to the solution. I guess the next move would have been to remove the same phrase in order to duplicate the line in the 'recovery' mode. Thanks for your help!

---

### Post by dryan775 on 2008-10-12
I had the SAME problem (both after the grub menu and after shut down splash screens.  

This 
[ gksu gedit /etc/usplash.conf ]  corrected the resoltion and fixed the second (after the shutdown), but not the first (after grub).


> **plucky said:**
> 

Also it is worth updating the initramfs  with the command ```
sudo update-initramfs -u
``` after you have made the changes.

Good Luck


This fixed the after grub problem with the vga=791

Thanks!!
dryan775
[email]daron@darasdesigns.com[/email]

---

