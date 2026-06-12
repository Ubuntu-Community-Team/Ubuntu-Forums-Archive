---
title: "[SOLVED] after todays update, no desktop only a white screen after logging in"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by gerben1 on 2008-05-26
Ubuntu told me there were updates ready to install, there about 21, among which I saw gdm. Anyways I just click yes install them after that was done it required a restart. 

After the restart I get to the login screen, that looks totally normal. When I type in my username and password all seesm to be going allright, I first see the brownish colored screen (while it is loading the desktop, I guess), but after that I end up with a white screen with only a mouse pointer, no desktop...

Any ideas on how to get the desktop back?

---

### Post by philinux on 2008-05-26
When grub loads stage 1.5 press esc. Then pick the previous kernel see if that loads ok.

---

### Post by gerben1 on 2008-05-26
Yes, thanks that works.

So apparently the kernel was updated too with todays update then?
What would you recommend, just using the older kernel (2.6.24-16), or somehow trying to get the new one working (2.6.24-17)?

---

### Post by philinux on 2008-05-26
You could try a full shutdown then reboot with the new kernel. If that fails I'd use the previous one until another arrives. You are not losing out by using the older kernel.

---

### Post by gerben1 on 2008-05-26
I already did a full shutdown, rebooting then with 2.4.24-17 still did not work, I then booted 2.4.24-16 which is working fine. I will just edit the grub config file then to load that kernel by default.

Thanks

---

### Post by philinux on 2008-05-26
> **gerben1 said:**
> I already did a full shutdown, rebooting then with 2.4.24-17 still did not work, I then booted 2.4.24-16 which is working fine. I will just edit the grub config file then to load that kernel by default.

Thanks

I would report this together with your hardware specs at launchpad. Then the devs know about it and can hopefully fix it with an update. It must be the new gdm thats causing some people a problem.

---

### Post by unutbu on 2008-05-26
If you had a special video driver installed to load with your 2.4.24-16 kernel, perhaps the problem is that video driver is not being loaded when you boot the 2.4.24-17 kernel.

---

### Post by liathus on 2008-05-26
yeah, i had this problem too, in the white screen i simply hit ctrl + alt + f2 and logged in, then ran envyng -t and reinstalled my vid drivers, rebooted and all was well...

---

### Post by ginger_meggs on 2008-05-26
Thanks liathus. Had the same problem with my Dell Inspiron 9400. All it needed was to reinstall the ATI drivers with envyng via the terminal. Cheers!

---

### Post by philinux on 2008-05-26
Thats annoying an update borking vid drivers and wifi too.

---

### Post by gerben1 on 2008-05-27
> **liathus said:**
> yeah, i had this problem too, in the white screen i simply hit ctrl + alt + f2 and logged in, then ran envyng -t and reinstalled my vid drivers, rebooted and all was well...

I just tried that, but unfortunately it did not solve the problem, I still end up with the white screen. 

This is what I did:
- Boot up computer, choosing kernel 2.6.24-**17** in Grub boot menu
- When in the log in screen, typed in username and password which brings me to the white screen.
- hit ctrl-alt-f2, and logged in in tty2
- ran "sudo envyng -t"
- chose option 3 "install ATI driver"
- reboot, choosing kernel 2.6.24-**17** in Grub boot menu
---> Same result, white screen
- reboot, choosing kernel 2.6.24-**16** in Grub boot menu
---> seems to be working fine

---

### Post by philinux on 2008-05-27
You could do the devs a favour and report this at launchpad.

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by DestroyMicroshaft on 2008-05-27
Ok so I woke up to this issue as well. Ive tried about everything I can think of but I get nothing. So until there is some resolution to this im sticking with the old kernel. I was using the catalyst 8.4 driver when I got the update, and I then got the white screen upon reboot. I tried envy, and manually reinstalling several different fglrx versions, the only one I got to work was the new catalyst 8.5, but i was getting serious corruption in compiz-fusion and awn, so I tried 8.4 again and got the white screen.

Can anyone tell me if sticking with the old kernel will become a problem? Im expecting a fix for this, but until then I wont run into any compatibility issues will I?

---

### Post by philinux on 2008-05-27
There's is no problem sticking with the old kernel. Unless someone out there knows more.

I had this in gutsy and waited for the next kernel .

---

### Post by abn91c on 2008-05-27
> **gerben1 said:**
> Ubuntu told me there were updates ready to install, there about 21, among which I saw gdm. Anyways I just click yes install them after that was done it required a restart. 

After the restart I get to the login screen, that looks totally normal. When I type in my username and password all seesm to be going allright, I first see the brownish colored screen (while it is loading the desktop, I guess), but after that I end up with a white screen with only a mouse pointer, no desktop...

Any ideas on how to get the desktop back?

do you have compiz or beryl enabled, it will do the white screen if your video drivers are changed during the update and openGL 3D effects are no longer supported

---

### Post by DestroyMicroshaft on 2008-05-27
If I shut of compiz in 16 and then boot into 17, I log in no problem, but when I try to enable compiz from inside 17 I get a white screen while logged in.

---

### Post by gerben1 on 2008-05-28
> **philinux said:**
> You could do the devs a favour and report this at launchpad.

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

I did:
[https://bugs.launchpad.net/ubuntu/+bug/235039](https://bugs.launchpad.net/ubuntu/+bug/235039)

---

### Post by philinux on 2008-05-28
I would add a comment to your bug that reistalling drivers in your case did not solve the problem. Some other have left comments that suggest rinstalling grpahics drivers fixes the bug. Which for you, clearly it does not.

---

### Post by Delever on 2008-05-28
> **philinux said:**
> I would add a comment to your bug that reistalling drivers in your case did not solve the problem. Some other have left comments that suggest rinstalling grpahics drivers fixes the bug. Which for you, clearly it does not.

You need to reinstall drivers using -17 kernel (so they are compiled against it).

---

### Post by philinux on 2008-05-28
I assume you mean from recovery mode? Or do you mean login with a different option?

---

### Post by Delever on 2008-05-28
> **philinux said:**
> I assume you mean from recovery mode? Or do you mean login with a different option?

Ussually that means booting in newest kernel and installing from Failsafe session.

---

### Post by gerben1 on 2008-05-28
> **philinux said:**
> I would add a comment to your bug that reistalling drivers in your case did not solve the problem. Some other have left comments that suggest rinstalling grpahics drivers fixes the bug. Which for you, clearly it does not.

Yes good plan, I have added it.

> **Delever said:**
> You need to reinstall drivers using -17 kernel (so they are compiled against it).

Well, I booted kernel 2.6.24-17, and then when I got to the white screen, I hit ctrl-alt-f2, logged in and ran sudo envyNG -t etc. 
as I explained in post #11:
> **gerben1 said:**
> I just tried that, but unfortunately it did not solve the problem, I still end up with the white screen. 

This is what I did:
- Boot up computer, choosing kernel 2.6.24-**[SIZE="4"]17[/SIZE]** in Grub boot menu
- When in the log in screen, typed in username and password which brings me to the white screen.
- hit ctrl-alt-f2, and logged in in tty2
- ran "sudo envyng -t"
- chose option 3 "install ATI driver"
- reboot, choosing kernel 2.6.24-**17** in Grub boot menu
---> Same result, white screen
- reboot, choosing kernel 2.6.24-**16** in Grub boot menu
---> seems to be working fine

so, I assume I did what you are suggesting, or did you mean something else?

---

### Post by Delever on 2008-05-28
> **gerben1 said:**
> 
so, I assume I did what you are suggesting, or did you mean something else?

I am very sorry, I haven't read all your posts properly. I assume this is a real bug then :(

---

### Post by gerben1 on 2008-05-28
I just found out what the reason for my problem was. It was just that linux-restricted-modules-2.6.24-17 was not installed.

I installed it via Synaptic, and now 2.6.24-17 works fine.

This thread gave me the idea to check for the restricted modules package:
[http://ubuntuforums.org/showthread.php?t=809973](http://ubuntuforums.org/showthread.php?t=809973)

---

### Post by DestroyMicroshaft on 2008-05-29
This did not solve the problem for me, restricted modules 17 was already installed on my machine, so I reinstalled them, and same thing, white screen on login. Any other ideas?

---

### Post by unutbu on 2008-05-29
DestroyMicroshaft, please post the output of:

```
cat /etc/X11/xorg.conf | perl -ne "print unless (m/^#/)"
sudo lshw -C video

```

---

### Post by jag_rulz on 2008-05-30
Well, after I upgraded to 2.6.24-17, I was having the same problems that were described in the above posts. I was able to see the login scren and login, but then just white. So went to tty2 (Ctrl+F2), did this: (explanation below)
```

sudo apt-get update
sudo apt-get upgrade
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run

sudo sh ./ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/8.04
sudo dpkg -i xorg-driver-fglrx_8.493.1-0ubuntu1_i386.deb fglrx-kernel-source_8.493.1-0ubuntu1_i386.deb fglrx-amdcccle_8.493.1-0ubuntu1_i386.deb
sudo reboot

```
What this does is (in order): Update apt-get, updates all programs to the newest version, retrives the new ATI driver, builds packages for ubuntu 8.04 (you can enter your own version there), and then installs the packages and reboots the system.

Of course, this will only work if you are running the ATI propriatary fglrx driver. I have a 3870, and are running 8.04

Good luck!

---

### Post by pablomme on 2008-05-31
I've run into this problem a number of times. The thing to do is to force a re-install of linux-restricted-modules-2.6.xx-xx-generic. If you get access to X via the "Failsafe Terminal", the most comfortable way to do this is:

```

metacity --replace &
sudo synaptic

```

Right-click on linux-restricted-modules-2.6.xx-xx-generic and select "reinstall". Make sure you remove other driver packages you may have installed (look in Sections > Installed (local or obsolete) and Sections > Installed (auto removable)). Then close Synaptic and open the restricted drivers manager:

```

sudo jockey-gtk

```

and tick the ATI driver. Then "sudo reboot".

NOTE 1: If linux-restricted-modules-2.6.xx-xx-generic was not installed initially, install (or force a reinstall) of linux-restricted-modules, which will include the former and will also make sure that kernel upgrades go smoothly.

NOTE 2: 2.6.xx-xx is the version of the kernel. If in doubt, type "uname -r" on the command line.

---

