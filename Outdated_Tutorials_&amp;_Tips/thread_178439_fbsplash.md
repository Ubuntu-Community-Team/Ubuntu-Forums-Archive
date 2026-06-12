---
title: "fbsplash"
date: 2006-05-17
forum: Outdated Tutorials &amp; Tips
---

### Post by knn on 2006-05-17
This howto was written for Breezy, when usplash could only support splash screens of 640x400 with 16 colors. Since Edgy, usplash supports higher resolutions and 256 colors, which is more than enough for a pretty splash screen (like the default splashes for Ubuntu and Kubuntu).
The work required to install fbsplash and the problems it causes (proprietary drivers, kernel updates etc.) is not worth the extra color depth (the default splash screens look good with only 256 colors) and the pretty terminal backgrounds (since you're not supposed to use the terminal in Ubuntu at all), therefore I recommend you **[COLOR="Red"]don't use it[/COLOR]**.

FBsplash howto v2.0

Here is what you will get once you finish this howto:
[[IMG]http://img427.imageshack.us/img427/2452/fbubuntu3qn.th.jpg[/IMG]](http://img427.imageshack.us/my.php?image=fbubuntu3qn.jpg)
[[IMG]http://img244.imageshack.us/img244/7441/ubuntu1024x768silent8gb.th.jpg[/IMG]](http://img244.imageshack.us/my.php?image=ubuntu1024x768silent8gb.jpg)

Thanks go to Jean-Damien Durand, who ported Gentoo's fbsplash to Debian, and then later made it compatible with Ubuntu. Most of the work was done by him.
Parts of this howto are based on his [howto for Debian]("http://jdurand.web.cern.ch/jdurand/fbsplash.html") and a few kernel compilation howtos from ubuntuforums.

Note: This will probably break firestarter. This thread [http://ubuntuforums.org/showthread.php?t=157560&highlight=firestarter+kernel]("http://ubuntuforums.org/showthread.php?t=157560&highlight=firestarter+kernel") has a solution, but since I didn't want to recompile the kernel again I dumped firestarter instead. (iptables works, so you'll be protected. You just won't have a nice graphical frontend to your firewall)

So, let's begin:

First we will need a patched kernel

**PART I - Compiling the shiny new kernel:**

**1.** If you are using a proprietary Nvidia or Ati driver, you will not be able to use it with your new kernel, and X will not start. You have to edit your xorg.conf file (sudo gedit /etc/X11/xorg.conf [replace gedit with kate for kde]). Find

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "[COLOR=Red]nvidia[/COLOR]"
EndSection

and replace nvidia with nv. If you have ati, replace it with vesa.

**2./a**Download the [2.6.16]("http://kernel.org/pub/linux/kernel/v2.6/patch-2.6.16.bz2") or [2.6.17]("http://kernel.org/pub/linux/kernel/v2.6/patch-2.6.16.bz2") kernel. 
Get the [emission patchset]("http://evolution-mission.org/viewforum.php?f=8&st=0&sk=t&sd=d&start=0&sid=691c1e9b35f054e81169e32d0f907ee0") (Recommended). Be sure to use the version for your kernel of choice.
You may also use the [beyond]("http://iphitus.loudas.com/beyond.html") patchset.
Download the attached evms patch (bd-claim.patch).
Note: Some people are having problems with 2.6.17-emission2. You may want to use the 2.6.16 kernel with emission4 or the 2.6.17 with the beyond patch until 2.6.17-emission3 comes out. Also, if you use emission and have problems, please post them [here]("http://www.evolution-mission.org/")

Or if you want the separate patches (you should use one of the patchsets, since they usually contain the latest patches):

**2./b** Go to [http://members.optusnet.com.au/ckolivas/kernel/]("http://members.optusnet.com.au/ckolivas/kernel/") and download the kernel and patch. In my case this was 2.6.16 and ck10 normal. Note that ck10 contains the fixes to 2.6.16 included in newer versions, so it cannot be applied to newer versions!
Go to [http://www.suspend2.net/]("http://www.suspend2.net/") and download the suspend 2 patch (latest stable for 2.6 kernels)
Go to [http://dev.gentoo.org/~spock/projects/gensplash/]("http://dev.gentoo.org/%7Espock/projects/gensplash/") and download the fbsplash patch. I also recommend you download the vesafb-tng patch ([http://dev.gentoo.org/~spock/projects/vesafb-tng/]("http://dev.gentoo.org/%7Espock/projects/vesafb-tng/")).
Download the attached evms patch (bd-claim.patch).

**3.** Create a folder in your home named kernel. Put all these files there. If you downloaded the separate patches, extract the suspend2 patch, you should get a subfolder.

**4.** Go to /usr/src. Remove the symbolic link linux if there is one. Extract the downloaded Linux kernel to /usr/src. You should get a subfolder named linux-2.6.16. Create a symbolic link to this folder named linux (sudo ln -s linux-2.6.16 linux). Enter the folder (cd linux)

**5.** Set a password for root if you don't already have one: sudo passwd root. Then, type su to switch to root.

**6./a** Apply the emission patch and the evms patch

bzcat /home/username/kernel/patch-2.6.16-emission4.bz2 | patch -p1
patch -p1 < home/username/kernel/bd-claim.patch

and skip to **step 10**

OR apply the separate patches:

**6./b** Apply the ck10 patch:

bzcat /home/username/kernel/patch-2.6.16-ck10.bz2 | patch -p1

**7.** Apply the suspend 2 patch. This is a little different:
> 
Usage:
   apply [path to patches]

   apply -R [path to patches]
    or
   unapply [path to patches]

The current directory _must_ be the kernel source tree you wish to patch.
The script must be able to find the path to the patches somehow. This can be
achieved by specifying the full path to apply, eg:

   /path/to/software-suspend-directory/apply

or, by specifying it as a parameter.

   apply /path/to/patches 
So type /home/username/kernel/suspend2-2.2.5-for-[2.6.16.9/apply]("http://2.6.16.9/apply") (use the tab key to autocomplete directory and file names)

**8.** Apply the fbsplash patch:

cat /home/username/kernel/fbsplash-0.9.2-rc5-2.6.16.patch | patch -p1

You will get an error message that one hunk in include/linux/sysctl.h failed. The failed hunk is a constant conflict with the ck10 patch and can be easily fixed. Open the files /usr/src/linux/include/linux/sysctl.h and /usr/src/linux/include/linux/sysctl.rej with gedit. Look at the bottom of the rej file. You should see: KERN_FBSPLASH=73,    /* string: path to fbsplash helper */ and a line number. It should be 148. Find line 148 in sysctl.h. As you can see there are a few new constants there, so we'll just copy the rejected line after them and change the number. Mine looks like this:
>     KERN_INTERACTIVE=73,    /* interactive tasks can have cpu bursts */
    KERN_COMPUTE=74,    /* adjust timeslices for a compute server */
    KERN_ISO_CPU=75,    /* percent cpu SCHED_ISO tasks run SCHED_RR */
    KERN_FBSPLASH=76,    /* string: path to fbsplash helper */ 
I've simply copied the line and changed 73 to 76.

**9.** Finally, apply the vesafb and evms patches:

cat /home/username/kernel/vesafb-tng-1.0-rc1-r3-2.6.16.patch | patch -p1
patch -p1 < home/username/kernel/bd-claim.patch

**10.** Now, import your configuration from your current kernel (in my case it's config-2.6.12-10-k7, type ls /boot/config* to see yours)

cp /boot/config-2.6.12-10-k7 .config

and configure it:

make xconfig

When I say check something, I mean put a checkmark into the square before it. [B]A small circle means building it as a module, which is not enough.
[/B]

Under Input device support, check Event interface (I believe this is needed to be able to use F2 to switch to verbose mode)
Graphics support:
Check support for frame buffer devices
Uncheck Tile blitting support! This is only needed for some Matrox cards, but is incompatible with fbsplash
Vesa VGA support: check it and select vesafb-tng if you patched the kernel with the vesafb-tng patch or emission, otherwise use vesafb (or a card-specific driver, e.g. nvidia, ati etc.).
In Graphics support/Console display driver support, check VGA text console and Video mode selection support. Check Framebuffer Console support (but not Rotation). 
Go back to Graphics support and check support for framebuffer splash (Scroll down, it should be the last one).

That should be it. Finally, some optimizations taken from another thread:
> 
In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family Choose the model of your processor.

Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz

Select a default IO scheduler in Device drivers/Block devices. I recommend the Anticipatory scheduler. If you leave the others checked too you can switch between them during boot (using a kernel parameter) or even while the system is running.

Here's some more info: [http://www.wlug.org.nz/LinuxIoScheduler]("http://www.wlug.org.nz/LinuxIoScheduler")
> Which one should I use?

I've not personally done any testing on this, so I can't speak from experience yet. The anticipatory scheduler will be the default one for a reason however - it is optimised for the common case. If you've only got single disk systems (ie, no RAID - hardware or software) then this scheduler is probably the right one for you. If it's a multiuser system, you will probably find cfq or deadline providing better performance, and the numbers seem to back deadline giving the best performance for database systems. 
In "Kernel hacking" uncheck "Kernel debugging".

Save the configuration.

**11.** compile the kernel:

make-kpkg clean
make-kpkg -initrd kernel_image kernel_headers modules_image

Go read a book :)
Hopefully, there will be no errors. Once it's ready, you'll have two new deb files in /usr/src. These will be kernel-image-*.deb and kernel-headers-*.deb. Install them using dpkg -i kernel*.deb
[B]
12.[/B] Reboot. Your new kernel will be the default one.

**PART II - Setting up fbsplash:**

**1.** Install the [Debian packages]("http://jdurand.web.cern.ch/jdurand/fbsplash.html") made by Jean-Damien Durand
You'll only need the three splashutils packages, don't install the other two. You can remove his repository so that the update manager doesn't bother you about the other two packages, but check back often for updates

**2.** configure the bootmanager
I will only give instructions for grub, since I don't know how to do it in lilo.
The current entry for your kernel should be something like this:

```
title        Ubuntu, kernel 2.6.16-emission4  
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.16-emission4  root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.16-emission4
savedefault
boot
``` 

remove the splash option
add these options:
```

video=vesafb:1024x768-32,ywrap splash=silent,theme:Ubuntu CONSOLE=/dev/tty1
``` 
(note: if you do not have vesafb-tng, do not use video=vesafb:1024x768-32,ywrap, use vga=791 instead. If you are using a different theme, change Ubuntu to the theme's name, e.g. theme:Linux)

It should look something like this:
```

title        Ubuntu, kernel 2.6.16-emission4
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.16-emission4  root=/dev/hda1 ro video=vesafb:1024x768-32,ywrap splash=silent,theme:Ubuntu quiet CONSOLE=/dev/tty1
initrd        /boot/initrd.img-2.6.16-emission4
savedefault
boot
``` 

NOTE: installing a new kernel package will regenerate menu.lst and revert these changes to the default options. The default options can also be set in menu.lst:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
[COLOR="Red"]# defoptions=quiet splash[/COLOR]

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single
```

Change this line to something like: 
defoptions=video=vesafb:1024x768-32,ywrap splash=silent,theme:Ubuntu quiet 
This way everytime something regenerates menu.lst, these options will be appended by default to every normal kernel entry (recovery entries have separate defaults)

**3.**
Download my Ubuntu theme or download one from [bootsplash.org]("http://www.bootsplash.org"). 
My theme has to be put under /etc/splash and does not have to be converted.
Bootsplash themes should be put under /etc/bootsplash/themes and have to be converted using bootsplash2fbsplash <themename>

**4.** Disable usplash:
Since splashutils provides usplash, you can uninstall usplash (*ubuntu-desktop will not be uninstalled). If you don't want to do that, disable it manually:

-instructions not available since the forum cut off this part of the howto and I can't remember them. Uninstall usplash instead.

**5.**
Regenerate the initrd image: If you uninstalled usplash you don't have to do this.
Whenever you install a new theme you'll have to regenerate the initrd image to be able to use it. Just run sudo update_initramfs. It will copy all themes in /etc/splash.

**6.**
To fix the flickering problem: (taken from JD's howto)
> At startup, screen will blink when the /etc/init.d/console-screen.sh will execute.

    * You can prevent that by commenting all lines starting with SCREEN_FONT in /etc/console-tools/config, they are not needed under fbsplash IMHO. 

---

### Post by Rizado on 2006-05-18
This is great, I'll try it on dapper as soon as I have time. I tried to get it working before but got stuck at the initscripts.

---

### Post by knn on 2006-05-18
From your forum style I suspect you are using kubuntu. I made a small fix for kdm, it's at the bottom of my first post. Also, could you please try installing the three splashutils packages without installing a newer version of sysv-rc, using --force-all instead of --force-overwrite? I don't have time to test this right now, but I'd really like to know if it works.

---

### Post by benplaut on 2006-05-19
anyone knwo if it works for dapper?

---

### Post by knn on 2006-05-19
It should work with Dapper too.

---

### Post by knn on 2006-05-19
I've made a little fix to the theme configuration file, so that now text is displayed (read the end of the first post). I also made a simple console background using the default ubuntu wallpaper:
[[IMG]http://img427.imageshack.us/img427/2452/fbubuntu3qn.th.jpg[/IMG]](http://img427.imageshack.us/my.php?image=fbubuntu3qn.jpg)
I'll put together a silent picture as well (the one that's displayed when booting) and post the new theme then.

Edit: Here it is, based on the GDM theme and LiveCD bootsplash:
[[IMG]http://img244.imageshack.us/img244/7441/ubuntu1024x768silent8gb.th.jpg[/IMG]](http://img244.imageshack.us/my.php?image=ubuntu1024x768silent8gb.jpg)

Extract the archive to /etc/splash (not bootsplash). There's no need to convert it. Don't forget to regenerate the initrd and set the kernel parameter.

Edit: moved to first post

---

### Post by Rizado on 2006-05-20
Ok now I have it working but there are some problems. When the kernel is initzialising I often only have parts of the theme. When It's done it looks fine but soon it starts to flicker and I can see the verbose screen and silent and some black bars. While using verbose screen it just flickers. I remember it did this on breezy as well when "setting up general console fonts" was shown.

I uploaded some pictures to show you what I mean. Also one funny thing is that when I reboot my system the splash says Booting blah blah blah but the progress bar starts at 100 and goes down. When it's almost at 0 the message changes to rebooting.

I tried to compile splashutils but it doesn't work. This is the whole compile message ```
make: Warning: File `Makefile' has modification time 1,2e+03 s in the future
CONF, libjpeg
MAKE, libjpeg
/bin/sh: -c: line 2: syntax error near unexpected token `;'
/bin/sh: -c: line 2: `   ; \'
make: *** [jpeglib] Fel 2
```miscsplash utils work fine though. sysv-rc isn't needed.

I tried to set vesafb-tng to ywrap ypan and nothing but there were only minor differences. ypan seems to work best but that might just be coincidence.

---

### Post by knn on 2006-05-20
You don't need to compile anything except the kernel. I couldn't compile the splashutils either, but I found those Debian pacakges. Just download all three and install them using dpkg -i --force-all.

It may be a video driver problem, but I doubt it because the shutdown screen works. Does the console background work fine after booting is finished (press Ctr-Alt-F1 to access the console and Ctr-Alt-F7 to return to the gui) or is it showing only parts too? It might also be that you did not install the packages correctly. If that is the case simply repeat part 2 of the howto. I've included the required packages as attachements and changed the second part of the howto, it should now be a bit simpler.
Don't forget to use --force-all instead of --force-overwrite if you didn't install the updated sysv-rc package

As for the flickering:
> At startup, screen will blink when the /etc/init.d/console-screen.sh will execute.

    * You can prevent that by commenting all lines starting with SCREEN_FONT in /etc/console-tools/config, they are not needed under fbsplash IMHO. 
This will not solve your problem though, only the flickering part.

The shutdown screen is supposed to go backwards, however it should show Shutting down the system and Rebooting the system. I'll check this immediately.
Edit: It works correctly for me.

---

### Post by Rizado on 2006-05-21
[QUOTE=knn]You don't need to compile anything except the kernel. I couldn't compile the splashutils either, but I found those Debian pacakges. Just download all three and install them using dpkg -i --force-all.

It may be a video driver problem, but I doubt it because the shutdown screen works. Does the console background work fine after booting is finished (press Ctr-Alt-F1 to access the console and Ctr-Alt-F7 to return to the gui) or is it showing only parts too? It might also be that you did not install the packages correctly. If that is the case simply repeat part 2 of the howto. I've included the required packages as attachements and changed the second part of the howto, it should now be a bit simpler.
Don't forget to use --force-all instead of --force-overwrite if you didn't install the updated sysv-rc package

As for the flickering:

This will not solve your problem though, only the flickering part.

The shutdown screen is supposed to go backwards, however it should show Shutting down the system and Rebooting the system. I'll check this immediately.
Edit: It works correctly for me.[/QUOTE]The problem with the packages is that they are for debian and relies on sysv-rc >= 2.86.ds1-12. Dapper uses 2.86.ds1-6ubuntu31 which probably is just the same so it's just a problem with dependencies. However if I install splashutils without debians sysv-rc I get a broken package that has to be fixed (removed) before any new apt changes. And of course lots of packages rely on 2.86.ds1-6ubuntu31 too so I  can't replace that either. This is why I want to compile. I'm thinking about repacking it too.

The flickering is the main problem, The half screen doesn't appear all the time and with ypan it almost never apear. Verbose screen works fine. I'll try playing with some settings.

---

### Post by knn on 2006-05-21
[QUOTE=Rizado]The problem with the packages is that they are for debian and relies on sysv-rc >= 2.86.ds1-12. Dapper uses 2.86.ds1-6ubuntu31 which probably is just the same so it's just a problem with dependencies. However if I install splashutils without debians sysv-rc I get a broken package that has to be fixed (removed) before any new apt changes. And of course lots of packages rely on 2.86.ds1-6ubuntu31 too so I  can't replace that either. This is why I want to compile. I'm thinking about repacking it too.

The flickering is the main problem, The half screen doesn't appear all the time and with ypan it almost never apear. Verbose screen works fine. I'll try playing with some settings.[/QUOTE]

You can install the Debian sysv-rc package, it works for me. Alternatively, open the .deb file in an archive manager, extract data.tar.gz. It contains all the files installed by the package with directories too, so you can do a manual install.

---

### Post by Rizado on 2006-05-21
I repacked it instead. Just unpack the debian package extract data.tar.gz and then control.tar.gz into a directory called DEBIAN. Edit control and reoack it with dpkg -b filesystem packagename.deb

Some hints on making a .deb [here](http://linuxdevices.com/articles/AT8047723203.html)
Changing the dependencies to sysv-rc (>= 2.86.ds1) will make it installable on both breezy and dapper and alot more.

EDIT: I can upload it if you want but I don't know where. I included the updated splash script and fbsplash_write but not rc. It should work with both dapper and breezy.

I noticed another problem now. This might only be on dapper but the bootscreen never finishes. It stops at 97% and this is really annoying because if I press F2 anywhere it kicks me to tty1.

---

### Post by SHAZcat07 on 2006-05-29
Thanks knn, after 2 days of recompiling kernels and testing, I have managed to make my masterpiece. I had used this guide for Debian and it worked great if you follow everything he tells you, but I had some exceptions. Instead of using vesafb-tng I had used vesafb because the the vesafb-tng was causing the screen to do some freaky stuff, and also if you are a person that has to use the initramfs when compiling (like me) use this little guide I had found off of the [Gentoo-Wiki]("http://gentoo-wiki.com/HOWTO_fbsplash#Loading_initramfs_at_boot_.28recommended.29").

> First, delete the present initramfs image: rm -iv /usr/src/linux/usr/initramfs_data.cpio.gz

Next, you'll have to create a new initramfs image containing the pictures, configs and the userspace helper (adjust resolution and theme - emergence in the example - to your needs).

```
Code:
splash_geninitramfs -g /usr/src/linux/usr/initramfs_data.cpio.gz -v -r 1024x768 emergence

```
You have to touch initramfs image to make sure it will be compiled into your new kernel: touch /usr/src/linux/usr/initramfs_data.cpio.gz. And then recompile your kernel

knn, you are welcome to add this little part in your tut, if you like.

---

### Post by knn on 2006-05-30
Compiling the initramfs into the kernel is not the best choice, because you will have to recompile the kernel (well, I guess not the whole thing if you don't make-kpkg clean, so it shouldn't be that terrible) if you want to install a new theme. That's why I didn't include it in the howto. I had no idea someone would have problems with initrd. Why can't you use it? Did you compile your kernel with initramfs support? The default Ubuntu config includes it.
I'll update the howto, and I'll add the new packages that do not depend on the newer sysv-rc.

---

### Post by SHAZcat07 on 2006-05-30
No, no, the initrd works fine. What I am saying is if you have to use the initrd to boot your system you can use those guide lines to append the splash to the initrd image. Everything works fine, just, I have to use the initrd to boot my system because if I don't the system can't find my hdd.

EDIT: AH, its alright, I timed my last compiling and it took about 30min, so I just pop in a movie or something and relax a bit.

---

### Post by knn on 2006-05-30
Oh, I understand. You don't have the filesystem or hard drive driver compiled into the kernel. There's an easier way to append the splash themes to an existing initrd file without recompiling the kernel, but I never tried it with fbsplash (I did with bootsplash and it didn't work), that's why I didn't include it in the howto and instead decided to compile in the hard disk and file system drivers and not compile an initrd kernel.
Since I've installed Dapper, I had to undo the changes, and I also uninstalled my custom kernel. I'll be posting an update with the fixed dependancies soon.

---

### Post by JMO707 on 2006-06-03
EDIT: Nothing to say. I should change my signature, I dont deserve it -_-

EDIT2: Well, now it's real. 

I followed the guide, but insted of the Debian splash, I used the [GNU one]("http://www.bootsplash.de/files/themes/Theme-GNU.tar.bz2") from [http://www.bootsplash.de]("http://www.bootsplash.de").

But..., I compiled the kernel using make-kpkg, not creating a bzImage (this 'cos I had to go through a hell when I did it)

So, the problem is that when the system is loading, it says all the time the next two lines. Loads fine, but:

[I]Can't open file (null)!
Failed to load image (null).[/I]

Not the big deal, but you know, its anti-aesthetic (wow, thats a new word to me. Really), and dont let me read fine the boot messages =p

Cheers.

---

### Post by knn on 2006-06-04
Did you change menu.lst to load the splash.img file or does it load the kernel image (linux-2.6.16-ck10.img if I remember correctly)? You can only have one initrd, if it's the kernel image, you have to append the splash themes to it, otherwise the kernel won't be able to find them. The splash_geninitramfs utility can do that, but you have to pass a different parameter (-a instead of -g I think, run splash_geninitramfs --help to check) and  the name of the ramdisk image you wan't to append the themes to. Then it should work.
Also, did you convert the theme, and did you change the kernel parameter theme:Debian to theme:<the name of the GNU theme's folder in /etc/splash>? (sorry, it seems that I forgot to mention this)

---

### Post by JMO707 on 2006-06-04
I changed the menu.lst entry to the splash.img, and it loads fine, everything. I dont know if this is supossed to happen =o
The theme GNU is well mentioned too ;)

If nothing works, I can always bury the error with a nice loading bar, no? =p

P.D: If you know any way to take a shell screenshot, I would show you. I tried *cat /dev/vcs1 > screenshot*, but the file is saved like a text.

---

### Post by knn on 2006-06-05
There's a program called fbgrab. Since you changed your menu.lst, it no longer loads the kernel initial ramdisk, but since you can load your system, everything is fine.
I fixed the howto after your post, so thanks for pointing this out.

---

### Post by JMO707 on 2006-06-05
Im glad that I could help =)
I let you the screenshot attached.

So your advice would be that I re-run the guide?
Anyway I dont like the name of my kernel: 2.6.16-ck11-ck11 :p

Hehe.

---

### Post by knn on 2006-06-05
your kernel name gets a -ck11 suffix automagically thanks to the patch, you can edit the makefile to remove it. The first ck11 should be because of the folder name.
You should try the Ubuntu theme, and see if you get the error messages. You don't have to rerun the entire guide, just install the theme

---

### Post by Noahod on 2006-06-07
Anyone working on a dpkg for dapper LTS?

---

### Post by knn on 2006-06-07
It should work on Dapper too, as soon as I have some free time, I'll test it. In the meantime, someone could make a nice animated Ubuntu theme, and then I'd have the motivation to test animations and implement them if necessary (probably)
Edit: Jean-Damien Durand changed his packages, so now installing only those *should* work, but I have not tested that yet

---

### Post by Krusty Ruffle on 2006-06-07
```
The following packages have unmet dependencies:
  splashutils: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
               Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2-turnerpatch0 is to be installed
E: Broken packages
```


The new .debs of his have busted dependencies in Ubuntu.... Ahh well, looks like it's time to start breaking my machine with Sid stuff, though I may try rebuilding them like someone did earlier in this thread.....

---

### Post by Noahod on 2006-06-08
yep, that's what I found. Let me know how you go... If you roll your own debs I'd be grateful if you upload them :)

---

### Post by scenestar on 2006-06-08
Knn I fsckin <3 you.

I really hated usplash, but i never got fbsplash to work ( I allways had issues with the initrd)

Once again, thank you for helping me get rid of that godawfull default artwork.

---

### Post by Krusty Ruffle on 2006-06-08
[QUOTE=Noahod]yep, that's what I found. Let me know how you go... If you roll your own debs I'd be grateful if you upload them :)[/QUOTE]

After many hours of playing around with this I am really confused, & tired to boot, but you can download the .debs from the site & install them by doing the following in a terminal: ```
cd /pathto/downloaddirectory && sudo dpkg -i --force-depends *.deb
```

It seems to be running okay, but I haven't really played with it a lot, except for the splash part, so don't blame me if it does break your box :-\" 

Anyway, I'll post some more thoughts and questions once I get some sleep and do a little more research. I get the feeling I'm going to have to learn bash scripting before I can get this to do what I want it to do...

[edit]If you do this splashutils does show up as a broken package in synaptic.... which means it will try to uninstall it everytime you try to install something else.... Dang...

Well, maybe I can compile it, but I have to do some more testing first.[/edit]

---

### Post by scenestar on 2006-06-09
I just extracted data.tgz from splashutils.deb straight into /  (root).

I know it's a fugley hack , but I'm too lazy to recompile the package.

---

### Post by Krusty Ruffle on 2006-06-09
[QUOTE=scenestar]I just extracted data.tgz from splashutils.deb straight into /  (root).

I know it's a fugley hack , but I'm too lazy to recompile the package.[/QUOTE]

Heh... Fugly's fine....

Okay, I'm fine with the verbose boot splash screens, so I haven't bothered hacking around on my rc files, but the thing that is annoying me is that I'm not getting themed consoles on vt2 - vt6. If I do "sudo /etc/init.d/splashutils start" then they will turn on, but even after setting the options in /etc/splash/splash.conf it just puts whatever theme is used during boot on all 6 vt's.

I know it reads the conf file because I tested it by changing the SPLASH_TTYS="1 2 3 4 5 6" setting, & it does change which consoles get themed, but the settings that allow you to apply diferent themes to different consoles do not seem to work.

I can, however, manually set the theme oon each to different themes, but that is a pain.

This is the main reason I ever started playing with gensplash on Ubuntu. I want pretty consoles, & it was really easy with Gentoo, but I'm starting to think it's not worth it here...

anyone have any ideas how to make this work in Ubuntu? I'm thinking a bootup script that runs absolutely last would do it, but I haven't figured out what to put in it yet as I'm not a scripter...](*,)

[edit]----------------------------------------------------------------------------------
Okay, after a lot of surfing around the net & hacking around on stuff here is what I have come up with:

I have found two ways to make this work on my laptop with Dapper.

This is the method I settled on:

I put the following code in a file & coppied it to /etc/init.d/splashconsoles```
#!/bin/sh
#
## Config file
#
if [ -r /etc/splash/splash.conf ]; then
    . /etc/splash/splash.conf
fi
for TTY in ${SPLASH_TTYS} ; do
	theme="${SPLASH_THEME}"

#	[[ ${TTY} == "1" && -z "$(/sbin/splash_util -c getstate --tty=${TTY}| grep 'off')" ]] && continue
	[[ ${TTY} == "0" ]] && continue

	if [[ -n "${SPLASH_TTY_MAP}" ]]; then
	    for i in ${SPLASH_TTY_MAP["${TTY}"-1]} ; do
		if [[ "${i%:*}" == "${TTY}" ]]; then
		    theme="${i:2}"

		fi
	    done
	fi
		
	if [[ -x /usr/bin/openvt ]]; then
	    /usr/bin/openvt -c ${TTY} echo -n "" 2>/dev/null
	fi
		
	/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setcfg 2>/dev/null 
	/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setpic 2>/dev/null
	/sbin/splash_util --tty="${TTY}" -c on 2>/dev/null
   done

/etc/init.d/splashutils stop

```Then I linked that to /etc/rcS.d/S99splashconsoles with```
sudo ln -s /etc/init.d/splashconsoles /etc/rcS.d/S99splashconsoles
```
[edit] This actually works much better if you link it in the runlevels that you want it to run in, (rc2.d etc... I'm actually not sure wich one Ubuntu uses for X?). Doing it this way avoids an issue with a flicker diuring boot, and allows you to switch the theme on console 1 without seeing it change in mid-boot.[/edit]

Now when I boot up I get nice pretty consoles wich I can set to display different themes with the options in /etc/splash/splash.conf & I am happy :D 

The other way I fount to do it was probably easier. I opened up the init file for splashutils with gedit```
sudo gedit /etc/init.d/splashutils
```I made three small changes to this script in it, (You may notice that the above script is mostly from this file, with just three small changes).

First I commented out this line:```
	[[ ${TTY} == "1" && -z "$(/sbin/splash_util -c getstate --tty=${TTY}| grep 'off')" ]] && continue
```This allows me to change the themes on the first console with the script.
Then I made the following block of code:```
	if [[ -n "${SPLASH_TTY_MAP}" ]]; then
	    for i in ${SPLASH_TTY_MAP} ; do
		if [[ "${i%:*}" == "${TTY}" ]]; then
		    theme="${i#:*}"

		fi
	    done
	fi

```
look like this:
```
	if [[ -n "${SPLASH_TTY_MAP}" ]]; then
	    for i in ${SPLASH_TTY_MAP["${TTY}"-1]} ; do
		if [[ "${i%:*}" == "${TTY}" ]]; then
		    theme="${i:2}"

		fi
	    done
	fi

```for some reason 	    for i in ${SPLASH_TTY_MAP} ; do
  wasn't looping right, and 		    theme="${i#:*}" wasn't splitting things the way it should have.
The last thing I did with this was to open up /etc/rc.local like this:```
sudo gedit /etc/rc.local
```And add:```
/etc/init.d/splashutils start
/etc/init.d/splashutils stop
```
after all the comments, & before the line with exit 0, then reboot....

Either way is probably pretty hackey, but either way works....

A couple of things worth mentioning:

1) the line in /etc/splash/splash.conf that tells it what consoles to theme looks like this: SPLASH_TTYS="1 2 3 4 5 6" & I'm guessing from the way I 'fixed' the issues I was having that if you theme more than 9 consoles with this it'll probably blow up....

2) the line in /etc/splash/splash.conf that tells it what themes to use on wich consoles looks like: SPLASH_TTY_MAP=(1:boot 2:vc2 3:vc3 4:vc4 5:vc5 6:vc6). it's bacically saying #ofthemed console:theme to use on console. I have found it best to leave console one with the same theme I use to boot, (explained below), & to make links from boot, vc2, vc3, etc... to the themes I want to use, that way I don't have to change the settings in several different files, only make new symlinks, & possably generale a new initrd file...

3)Although it is possabl to change the theme onn the first console with this I recomend sticking with using the boot theme here. for one thing, if you use the first method described above it will swith your theme before it finishes booting up, & with either method you'll end up with a different theme during shutdown than you do during boot up, (at least in verbose mode, though this may not be the case for those of you who have hacked aroung & gotten the silent mode working. I don't know:-k )

anyway, it may or may not work for you, but it worked for me, I'm sure it's ugly & hacked up like Mordors orcs, but I'm happy!!:D  Now I just need to go & make me up some themes, hopefullt I'll get 'em done & post them up somewhere in the next couple of days...

---

### Post by Krusty Ruffle on 2006-06-10
[Okay, here's my bootscreen/first console theme.]("http://ubuntuforums.org/gallery/showimage.php?i=2840&original=1&c=4") I like it, but the text area is a bit small for serious usage... Luckilly, I have five more to make, & I'm pretty sure I can make a couple of them better for real usage :)

---

### Post by Krusty Ruffle on 2006-06-12
Thanks to [Olterman's fbsplash/Debian Howto,]("http://olterman.homelinux.net/homelinux/2004/12/28/console-fluff-with-fbsplash/") I have updated my /etc/init.d/splashconsoles script to the following:
```

#!/bin/sh
#
## Config file
#
if [ -r /etc/splash/splash.conf ]; then
    . /etc/splash/splash.conf
fi

case $1 in
start)
for TTY in ${SPLASH_TTYS} ; do
	theme="${SPLASH_THEME}"

#	[[ ${TTY} == "1" && -z "$(/sbin/splash_util -c getstate --tty=${TTY}| grep 'off')" ]] && continue
	[[ ${TTY} == "0" ]] && continue

	if [[ -n "${SPLASH_TTY_MAP}" ]]; then
	    for i in ${SPLASH_TTY_MAP["${TTY}"-1]} ; do
		if [[ "${i%:*}" == "${TTY}" ]]; then
		    theme="${i:2}"

		fi
	    done
	fi
		
	if [[ -x /usr/bin/openvt ]]; then
	    /usr/bin/openvt -c ${TTY} echo -n "" 2>/dev/null
	fi
		
	/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setcfg 2>/dev/null 
	/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setpic 2>/dev/null
	/sbin/splash_util --tty="${TTY}" -c on 2>/dev/null
done
;;

stop)
for TTY in ${SPLASH_TTYS} ; do

	[[ ${TTY} == "0" ]] && continue

	for i in ${SPLASH_TTY_MAP["${TTY}"-1]} ; do
		if [[ "${i%:*}" == "${TTY}" ]]; then
		/sbin/splash_util --tty="${TTY}" --cmd=off 2>/dev/null 

		fi
	done
		
done
;;

boot)
KERNEL=`uname -r`
echo "creating initrd image for kernel $KERNEL"
su -c "rm -rf /boot/initrd.img-$KERNEL"
su -c "splash_geninitramfs -v -g /boot/initrd.img-$KERNEL -r 1024x768 boot"
;;

*)
echo "Dolp!! $1 not supported..."
echo "Usage = (start|stop|boot)"
;;
esac

```
so now I use sudo /etc/init.d/splashconsoles start to start the themes on the individule consoles, & sudo /etc/init.d/splashconsoles stop to clear all themes from the consoles, while still leaving the higher resolution, & sudo /etc/init.d/boot will make an initrd image with whatever theme the boot symlink points at.... (at 1024x768 resolution)...

Not to bad, but it's still probably pretty hackish :)

---

### Post by Krusty Ruffle on 2006-06-12
And here are shots of my newest console themes:
[Console #2]("http://ubuntuforums.org/gallery/showimage.php?i=2860&original=1&c=4")
[Console #3]("http://ubuntuforums.org/gallery/showimage.php?i=2861&original=1&c=4")
[And console #4]("http://ubuntuforums.org/gallery/showimage.php?i=2862&original=1&c=4")

I've still got to do 5 & 6, but I'm pretty happy with these so far.... :)

---

### Post by rogeriovinhal on 2006-06-19
I have just followed the HOWTO, but after the kernel compilation, the kernel image was also dependent of a initrd image that was already created to the previous kernel, and if I remove it from menu.lst, the kernel panics.

Is there a way to use 2 initrds? Or else, how can I make the new kernel image independent from the old initrd?

Is there any patches to fbsplash and vesafb-tng for the kernel 2.6.17?

---

### Post by Rui Pais on 2006-06-19
Hi,
this is a great HOWTO!
But it's, imho, at certain points (Part I) unnecessary complicated.

[QUOTE=rogeriovinhal]I have just followed the HOWTO, but after the kernel compilation, the kernel image was also dependent of a initrd image that was already created to the previous kernel, and if I remove it from menu.lst, the kernel panics.

Is there a way to use 2 initrds? Or else, how can I make the new kernel image independent from the old initrd?

Is there any patches to fbsplash and vesafb-tng for the kernel 2.6.17?[/QUOTE]

The vesafb-tng seems to give a lot of problems with 2.6.17 kernel.

But there are lot of choices of kernel patches with fbsplash and vesafb-tng, well tested, that don't produce rejected files and don't require manually intervention.

Like (in order of stable -> -stable/+speedy):
[beyound]("http://iphitus.loudas.com/beyond.php")
[emission]("http://evolution-mission.org/viewforum.php?f=8&st=0&sk=t&sd=d&start=0&sid=691c1e9b35f054e81169e32d0f907ee0")
[nosources ]("http://no.oldos.org/files/") (remember latest 2.6.17 dont have vesafb-tng patchs)

My favorites are the emission ones (very stables and very fast)

To use, just download the patchs, apply and compile (almost boring)

have fun

---

### Post by knn on 2006-06-19
Whoops, I forgot to login the last time I visited the site and didn't get any email notifications...
I managed to get console backgrounds for all consoles (though it was the same on all and it was on Breezy), but didn't test it with multiple consoles. Since I was busy studying for my final exams, which are now finally over, I didn't have time to play around with this. But now that I am free of school forever... (at least until september)
Instead of making a bzImage kernel, I'll try making an initrd image kernel and put the splashimages into the initrd image, so problems like rogeriovinhal's will be no more.

> I have just followed the HOWTO, but after the kernel compilation, the kernel image was also dependent of a initrd image that was already created to the previous kernel, and if I remove it from menu.lst, the kernel panics.

Is there a way to use 2 initrds? Or else, how can I make the new kernel image independent from the old initrd?

Is there any patches to fbsplash and vesafb-tng for the kernel 2.6.17?

That is actually a new initrd created for your new kernel (otherwise it shouldn't work), which should not exist if you used make-kpkg binary. If you get a kernel panic, it means that your kernel does not have some vital driver compiled in (most likely filesystem or hard drive driver). What does the panic say? Alternatively you can wait for me to test out the patch with an initrd kernel, that should make life simpler.

Unfortunately, you can't have two initrds.

> Hi,
this is a great HOWTO!
But it's, imho, at certain points (Part I) unnecessary complicated.

Quote:
Originally Posted by rogeriovinhal
I have just followed the HOWTO, but after the kernel compilation, the kernel image was also dependent of a initrd image that was already created to the previous kernel, and if I remove it from menu.lst, the kernel panics.

Is there a way to use 2 initrds? Or else, how can I make the new kernel image independent from the old initrd?

Is there any patches to fbsplash and vesafb-tng for the kernel 2.6.17?

The vesafb-tng seems to give a lot of problems with 2.6.17 kernel.

But there are lot of choices of kernel patches with fbsplash and vesafb-tng, well tested, that don't produce rejected files and don't require manually intervention.

Like (in order of stable -> -stable/+speedy):
beyound
emission
nosources (remember latest 2.6.17 dont have vesafb-tng patchs)

My favorites are the emission ones (very stables and very fast)

To use, just download the patchs, apply and compile (almost boring)

have fun

Thanks. I'll try the emissions patch. Thanks for the link. If it works nicely, it'll be in the howto replacing the current complicated patching.

Krusty I think you should release those backgrounds. They are really great. I especially like console 4

---

### Post by Rui Pais on 2006-06-19
hi,
here works nicely even with staircase patch.
I didn't do it with make-kpkg, but should work anyway creating a deb. 

Slighty OT, emission comes with suspend2 patches too. An excellent extra since, besides a better hibernation support (at least in my machine), it allows fbsplashs during sleep/hibernate, the sames that you choose for normal boot/shutdown, making the turn on/off look of the computer very consistent. :)

Another thing that i tried, in order to avoid at most the output from kernel before one gets the boot splash, was moving the start of udev to S01udev and compile any needed modules build in the kernell. That way i see only 4 lines on black screen, and the last, "Loading hardware drivers..." are very quick, putting fbsplash on much faster.

If anyone want to try :)

have fun.

---

### Post by knn on 2006-06-21
Just a quick note about nvidia drivers: running the installer script no longer installs the driver correctly on dapper like it did on breezy. Follow this guide instead: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Edit: It worked! Bootup splashscreen works only by installing jd's packages and running splash_geninitramfs. If you use the -a parameter and supply your existing initrd image, it will append the themes to the existing initrd and it will work. Run:
sudo cp /boot/initrd.img-<yourversion> /boot/initrd.img-<yourversion>.bak   (to backup)
sudo splash_geninitramfs -a /boot/initrd.img-<yourversion> --all
Edit2: see post 1 for updated instructions at the beginning of part 2


Problems:
-At the beginning of bootup usplash will display in the resolution you specified (in my case 1024x768 ), though it will only occupy 640x480 screen size. Since I don't want to remove it I'll have to figure out how to disable it. Edit: solved, see first post (beginning of part 2)
-Text is stuck at initializing kernel. This is a bug in my Ubuntu theme that I thought was a bug in the splash script. I've upload a new version (see post 6)
-No support for shutdown, since Debian's rc doesn't support this. I'll have to change the usplash_write script

---

### Post by Rizado on 2006-06-21
[QUOTE=Rizado]I noticed another problem now. This might only be on dapper but the bootscreen never finishes. It stops at 97% and this is really annoying because if I press F2 anywhere it kicks me to tty1.[/QUOTE]I still have this problem, it doesn't matter if I use the normal rc or the one for kdm. (I'm using kubuntu) This is a real problem now because I have to enter setup in vmware and that is button F2.

---

### Post by knn on 2006-06-21
The easiest solution would be to use the new scripts. To restore your system, reinstall sysv-rc, uninstall all three splashutils packages and then reinstall usplash. you might want to downgrade the packages you installed from debian too. Then install the three packages and follow the new instructions at the beginning of part 2. That should leave you with an almost clean system (except the two deleted usplash files). Plus it will work with an initrd kernel.

As for the different themes for each console, I'll investigate into that once I get shutdown splash to work.

Edit: I think I finally managed to get rid of usplash: making /sbin/usplash unexecutable should do the trick. added to howto
Edit2: I made some changes to the usplash_write script, so now it works with shutdown too.

---

### Post by ErikTheRed on 2006-06-21
You should consider adding the [beyond]("http://iphitus.loudas.com/beyond.html") patchset (formerly known as archCK) to your guide. It includes fbsplash and bunch of other cool things.

Great guide!

---

### Post by rogeriovinhal on 2006-06-21
I managed to make it work with the new howto.
But there are some issues that I wish to resolve...

First, I don't like 60Hz, but if I try to change the frequency to 1024x768@85 at menu.lst, the splash stop working. Why? Is there a way I can make it work with 85Hz?

The percentage stays in 0%, even with the progress bar moving...

I am having a lot of these errors at startup:
```

Jun 21 21:07:18 localhost kernel: [4294689.564000] device-mapper: dm-linear: Device lookup failed
Jun 21 21:07:18 localhost kernel: [4294689.568000] device-mapper: error adding target to table
Jun 21 21:07:18 localhost kernel: [4294689.573000] device-mapper: dm-linear: Device lookup failed
Jun 21 21:07:18 localhost kernel: [4294689.578000] device-mapper: error adding target to table
Jun 21 21:07:18 localhost kernel: [4294689.583000] device-mapper: dm-linear: Device lookup failed

```
I just pasted 3 times, but it appears about 10 times.

---

### Post by knn on 2006-06-22
The emission patchset contains [a lot of things]("http://evolution-mission.org/viewtopic.php?f=8&t=5&sid=c40fc96233cc17bb7469985e49245785") too.

> I managed to make it work with the new howto.
But there are some issues that I wish to resolve...

The percentage doesn't get updated because of a bug in my Ubuntu theme. Download the new one.

I don't know about the refresh rate, I'm just using 60Hz, but I'll try 85Hz.
Edit: it stayed at 60Hz, I'll try 80

I get those errors too. There are three [solutions]("http://evms.sourceforge.net/install/kernel.html#bdclaim").
The lazy way is patching the kernel to disable a feature that prevents evms from working, the other is to convert your root filesystem to evms (which is a little complicated), the third is to disable evms for partitions mounted by the kernel.
I think the Ubuntu kernel has the evms patch. I've disabled evms, and I'll reboot now to see what happens
Edit: system still works fine. I don't use Raid, so I don't think I need evms. However, I'm going to try the evms patch. 

This brings me to our next subject. Compiling a kernel takes a lot of time and is discouraging for many. It would be so much easier to use fbsplash if there were precompiled kernels available. Those of us who compile our kernels get two Debian packages that can be installed easily, but we most likely won't need them again. So why throw them away? We could upload them and make the kernel compilation step unnecessary. Of course those kernels would have to be compiled with the default Ubuntu kernel settings, except those needed by fbsplash and suspend2 and they would have to include the evms patch. We  should also use the same patches, IMO emission, but we could also provide beyond. After all, Linux is all about choices :)
I'm going to compile a new generic desktop kernel with emission and the evms patch for k7 processors. Then I'll make a new howto for building a generic kernel that can be used by others too. Using [this]("http://ubuntuforums.org/showthread.php?t=85064&highlight=custom+compile") howto I will also compile all restricted modules available for ubuntu. Once I'm finished, anyone who needs fbsplash on a k7 machine won't have to compile a kernel (hopefully).

---

### Post by domino on 2006-06-22
Finally, a way to make Ubuntu look professional. At first teh original usplash put me off comparing it with SuSE and Fedora. I hope the new patched kernel makes it in the repo some day. I  have one question though. Will this eventually work with proprietary nvidia and ATI drivers? I run Xgl/compiz on 9800 pro.

---

### Post by knn on 2006-06-22
I'm running a proprietary Nvidia driver, so yes, it will work. There's a link to a howto in part 3 that explains how to install the nvidia binary driver, and there's a binary driver for ati too. I'm going to compile the Ati modules too with the new kernel I'll upload, so if you have a k7 you can test it.

---

### Post by domino on 2006-06-22
Bahhh, I have a P4 so i'm sorry I can't help test. I will help test the first 686 kernel depending on which version. The newest kernel seem to have problems with compiz atm so i'm still on 2.6.15-23 until it's all sorted.

---

### Post by knn on 2006-06-22
Ok, I made a k7 kernel, however I only managed to compile ndiswrapper and nvidia modules, fglrx failed, and I don't know how to compile avm-fritz and madwifi, the directory structure is different.
Here's the fglrx compile output:
```
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc-4.0"  /usr/bin/make -C /usr/src/modules/fglrx-kerne l/fglrx/build_mod/2.6.x -f Makefile SYSSRC=/usr/src/linux  EXTRAVERSION=-emissio n4-k7-desktop KBUILD_PARAMS="-C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx-ke rnel/fglrx/build_mod/2.6.x"
make[3]: Entering directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x '
make[3]: Makefile: No such file or directory
make[3]: *** No rule to make target `Makefile'.  Stop.
make[3]: Leaving directory `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/fglrx-kernel'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue
```

These files are only 25 MB, which should not be a problem for anyone with broadband to upload. So if someone wants to help, give me a moment to write a short howto. In the meantime I'll upload the k7 kernel (SMP enabled, Suspend2 write to swap enabled, evms fixed, everything else Ubuntu default), and I'd appreaciate it if someone could test it, as I don't want to ruin my system (I have a custom compiled kernel without SMP and high memory support).

Links: 
You shouldn't use this as the nvidia driver won't work. You can install the kernel and the headers, but use the howto from Part 3 to install the Nvidia driver
[Headers]("http://files.filefront.com/kernel_headers_2616_e4/;5176295;;/fileinfo.html")
[Image]("http://files.filefront.com/kernel_image_2616_emission4/;5176364;;/fileinfo.html")
[Ndiswrapper]("http://files.filefront.com/ndiswrapper_modules_2616_e4/;5176371;;/fileinfo.html")
[Nvidia module]("http://files.filefront.com/nvidia_kernel_2616_emission4/;5176380;;/fileinfo.html")

---

### Post by rogeriovinhal on 2006-06-22
knn, I had the same problem compiling fglrx when I compiled the kernel, but I installed the official drivers from the 32 bit installer from ati.com, and it compiled pretty well...

If you are willing to install it just to compile fglrx module, it should give you no problems. And it also has a uninstaller so you can uninstall it safely after making the package.

---

### Post by knn on 2006-06-23
I'm going to use the source package for linux-restricted modules to compile the restricted modules. Binary drivers don't seem to produce the same files

---

### Post by rogeriovinhal on 2006-06-24
I compiled the 2.6.17 Kernel with the emission2 patch, and I am having these problems on startup:

```

CPU: Vendor Unknown, using generic init
CPU: Your system may be unstable
smapi::smapi_init, ERROR invalid usSmapiID
mwave: tp3780i::tp3780I_InitializeBoardData: Error: SMAPI is not available on this machine
mwave: mwavedd::mwave_init: Error: Failed to initialize board data
mwave: mwavedd::mwave_init: Error: Failed to initialize

```

I didn't have these on the plain 2.6.17 kernel, what is that supposed to mean?
I compiled with the Athlon64/K8 option in the kernel (even using the 32 bits system), now I tried the K7 option, and everything is the same.

---

### Post by Gandalf on 2006-06-24
Just in case no one knows, there's also a patchset called beyond, which is maintained by the old -nitro and -archck maintainers...
Home page -> [http://iphitus.loudas.com/beyond.html](http://iphitus.loudas.com/beyond.html)

---

### Post by knn on 2006-06-24
[QUOTE=rogeriovinhal]I compiled the 2.6.17 Kernel with the emission2 patch, and I am having these problems on startup:

```

CPU: Vendor Unknown, using generic init
CPU: Your system may be unstable
smapi::smapi_init, ERROR invalid usSmapiID
mwave: tp3780i::tp3780I_InitializeBoardData: Error: SMAPI is not available on this machine
mwave: mwavedd::mwave_init: Error: Failed to initialize board data
mwave: mwavedd::mwave_init: Error: Failed to initialize

```

I didn't have these on the plain 2.6.17 kernel, what is that supposed to mean?
I compiled with the Athlon64/K8 option in the kernel (even using the 32 bits system), now I tried the K7 option, and everything is the same.[/QUOTE]

Edit: Nothing, didn't notice they released a new version for 2.6.17
You could try the separate patches or beyond.

---

### Post by Rui Pais on 2006-06-24
[QUOTE=knn]Edit: Nothing, didn't notice they released a new version for 2.6.17[/QUOTE]
hi, there is indeed a new version (2 in fact) but they are a little experimental/testing yet.
Suspend2 is one case of things that don't work yet, neither on emission1 nor emission2 (for 2.6.17), a 3rd version is promissed for soon [here]("http://forums.gentoo.org/viewtopic.php?p=3402659").

---

### Post by rogeriovinhal on 2006-06-24
[QUOTE=knn]Edit: Nothing, didn't notice they released a new version for 2.6.17
You could try the separate patches or beyond.[/QUOTE]
Actually, Those problems I managed to solve, but I am also having a freeze in the boot proccess while "loading hardware drivers".
Right now I am compiling it again without the "Sparse Memory" option that I was instructed to use in another thread. Let's see if it works.

The reason why I am using emission and not the patches sepparately, is that I can't find any patches for the 2.6.17, neither fbsplash nor vesafb-tng, and the emission promises them for 2.6.17.

EDIT: After a LOT of tests, I am giving up using emission2 patch for 2.6.17. It locks boot up at "Loading Hardware Drivers", and the only way to unlock is to press "Ctrl+C", so it can fail. I have compiled the same kernel configs that I used to compile the 2.6.17-ck1, which I am using right now.

If anyone knows of a patch of fbsplash and vesafb-tng that works under 2.6.17, please post here.

---

### Post by scenestar on 2006-06-26
Heres a quick screenie from my framebuffer.

[http://www.ubuntuforums.org/gallery/showimage.php?i=2949&original=1&c=4](http://www.ubuntuforums.org/gallery/showimage.php?i=2949&original=1&c=4)

---

### Post by Rui Pais on 2006-06-26
[QUOTE=rogeriovinhal]...The reason why I am using emission and not the patches sepparately, is that I can't find any patches for the 2.6.17, neither fbsplash nor vesafb-tng, and the emission promises them for 2.6.17.[/QUOTE]
Hi, vesafb-tng and 2.6.17 seems to give a lot of problems when used in conjugation. 
There are a lot of work beeing done on it, mean while, why not go with 2.6.16-emission4 or beyound sources? they are both fast and stable kernel patchs...

> EDIT: After a LOT of tests, I am giving up using emission2 patch for 2.6.17. It locks boot up at "Loading Hardware Drivers", and the only way to unlock is to press "Ctrl+C", so it can fail. I have compiled the same kernel configs that I used to compile the 2.6.17-ck1, which I am using right now.

If anyone knows of a patch of fbsplash and vesafb-tng that works under 2.6.17, please post here.

If you are really desperate for 2.6.17 you could use the isolated patchs of 2.6.16-emission2. Download the [broken-out]("http://distfiles.evolution-mission.org/emission-sources/2.6.17/emission2/linux-2.6.17-emission2-broken-out.tar.bz2"), extract the patch:
**002-genpatches_rollup-2.6.17-gentoo-r1.patch**
and apply to the vanilla 2.6.17. that will give you, among others:
> 4200_fbsplash-0.9.2-r5.patch
4205_vesafb-tng-1.0-rc1-r3.patch
that will not diverge much from vanilla so you can check if your problem is really emission sources or some incompatible/not-supported-yet hardware problem on the 2.6.17 emission kernels.

---

### Post by rogeriovinhal on 2006-06-26
Actually, I have both 2.6.16-ck12 with fbsplash and vesafb-tng manually compiled and 2.6.17-ck1 working here right now, but I don't know, probably it is just an impression, but I feel 2.6.17 slightly more stable and fast than 2.6.16.
Because of that feeling I want to keep 2.6.17.

I will try that broken-out patch and post here my progress justa after...
Gladly, under these experiences I have shortened my lernel config so that my last kernel-image.deb is only 5.9MB, so it takes about 10 minutes to compile. :)

EDIT:
It worked. It seems that one of the others patches of beyond is causing that problem with Loading Hardware Drivers, because now it is working flawlessly, and the kernel image has now 5.4MB :)

What is the average size of your compiled custom kernels?

---

### Post by jasutton on 2006-06-27
I'd just like to say that these screenies look awesome.  I'd love to get fbsplash working on my Thinkpad running Dapper, but I really don't have time to re-compile my kernel (summerschool :D).

Also, is there some reason that no one has suggested (to whomever makes the decision) that fbsplash replace usplash in Ubuntu itself?

---

### Post by bittdude on 2006-06-27
A great howto, Everything worked on the first go for me!  I've envied this feature from Gentoo, especially the themed TTY's so thanks for helping me achieve this in Ubuntu :D

---

### Post by scenestar on 2006-06-27
to all you idiots who can't get it to work.

Just use a goddamn vanilla 2.6.16 with the beyond patches.

It is really that damn easy.

Now quit bitching about patch or kernel errors and keep on topic.


*(sorry about this rant but some people are driving this thread offtopic)*

---

### Post by knn on 2006-06-27
[QUOTE=scenestar]to all you idiots who can't get it to work.

Just use a goddamn vanilla 2.6.16 with the beyond patches.

It is really that damn easy.

Now quit bitching about patch or kernel errors and keep on topic.


*(sorry about this rant but some people are driving this thread offtopic)*[/QUOTE]

[We might all experience some frustration now and then, but we cannot allow that frustration to turn into a personal attack. It's important to remember that a community where people feel uncomfortable or threatened is not a productive one.]("http://www.ubuntu.com/community/conduct")

---

### Post by thephilv on 2006-06-27
Hello all,

first off I want to give my thanks for this guide.  I have followed it step by step.  I am using kernel-2.6.16 with the emission4 patch and bd-claim.patch.  I am running Ubuntu 6.06.

The problem I am having is that no matter what I do after uncompressing the kernel it always looks for 640x480.cfg instead of 1024x768.cfg

i have done:
```

sudo update-initramfs
and
sudo splash_geninitramfs -a /boot/initrd.img-2.6.16-emission4 --all
(I get a warning that says that Ubuntu config file for 800x600 does not exist.)

```

my menu.lst:
```

title		Ubuntu 2.6.16-emission4
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.16-emission4 root=/dev/hda6 ro video=vesafb:1024x768-32,ywrap splash=silent,theme:Ubuntu quiet CONSOLE=/dev/tty1
initrd		/boot/initrd.img-2.6.16-emission4
boot

```

EDIT:
If i try to preview the theme it outputs that there is no 640x480.cfg for the Ubuntu theme
It also screws up my screen. All the colors go wacky (i am thinking it changes the color depth but i could be way off)

I have been working on this since yesterday and it is frustrating me.  If anyone can help I would be most greatful.

Thanks everyone,

Phil V

---

### Post by Brando569 on 2006-06-27
everything went fine except im confused as to where the new initrd image comes from?

you have this listed in the howto but never explain where it is or how to make it:

add this line after the kernel line:
Code:

initrd /boot/fbsplash.img

---

### Post by knn on 2006-06-28
[QUOTE=Brando569]everything went fine except im confused as to where the new initrd image comes from?

you have this listed in the howto but never explain where it is or how to make it:

add this line after the kernel line:
Code:

initrd /boot/fbsplash.img[/QUOTE]

Whooops, that's from the old version of the howto, will fix it immediately.
The real initrd is installed by the package and is already there in grub. don't change it
Edit: fixed. Thanks for spotting this. I hope you didn't add the initrd /boot/fbsplash.img line. If you did, remove it.

@Phil V

The theme doesn't support 640x480. It's 1024x768 only. It seems your system can't do 1024x768-32 for some reason. Try 1024x768-16 instead

Edit: or uninstalling usplash ran a script that regenerates menu.lst with the default options. This means the required parameters are missing. Check your menu.lst, and redo step2 if that's the case
Edit2: I checked, uninstalling usplash doesn't do that, but you should check menu.lst anyway. I've added instructions about this to the howto, including how to set these options as default so you don't have to fix menu.lst when some package breaks it.

---

### Post by conexion200 on 2006-06-28
I have some problems with dapper. All the time fbsplash show message: initializing the kernel and progressbar doesn't move. Splash sometimes flickers. Please help.

---

### Post by scenestar on 2006-06-28
[QUOTE=conexion200]I have some problems with dapper. All the time fbsplash show message: initializing the kernel and progressbar doesn't move. Splash sometimes flickers. Please help.[/QUOTE]

**Is it really that hard to read through a thread before posting in it.**

[http://www.ubuntuforums.org/showpost.php?p=1116677&postcount=29](http://www.ubuntuforums.org/showpost.php?p=1116677&postcount=29)

quit wasting other peoples times with frivolous help requests. You need to do your [Homework]("http://www.catb.org/esr/faqs/smart-questions.html#id265155")

---

### Post by knn on 2006-06-28
[QUOTE=conexion200]I have some problems with dapper. All the time fbsplash show message: initializing the kernel and progressbar doesn't move. Splash sometimes flickers. Please help.[/QUOTE]

Flickering: check step 6 of part 2 (I just added it).
Progressbar problem: that's a bug in my ubuntu theme. Download it again, and don't forget to regenerate the initrd image (part 2/step 5).

---

### Post by thephilv on 2006-06-28
knn,
thanks I got it working.  I did not check allowance for splash screens for some reason on my kernel config.  It is working now except the progress bar doesn't move...gonna re-download the theme and try again.  thanks again for the tutorial and your help knn.
-Phil V

---

### Post by scenestar on 2006-06-29
I like to cut and paste:

su to root
> 
apt-get remove usplash

apt-get install linux-source

-=optional=-
apt-get install ndiswrapper-source
apt-get install nvidia-kernel-source 
-=-

apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev bin86

cd /usr/src

tar --bzip2 -xvf linux-source-2.6.16.tar.bz2

-=If you wan't to compile the sources mentioned before=-

tar --bzip2 -xvf ndiswrapper-source.tar.bz2
tar -xvf nvidia-kernel-source.tar.gz

ln -sf /usr/src/linux-source-2.6.16 /usr/src/linux

wget [http://iphitus.loudas.com/beyond/2.6.16/patch-2.6.16-beyond4.1.bz2](http://iphitus.loudas.com/beyond/2.6.16/patch-2.6.16-beyond4.1.bz2)

cd /usr/src/linux

bzcat /usr/src/patch-2.6.16-beyond4.1.bz2 | patch -p1

make oldconfig

make xconfig

-=- AS mentioned before-=-

When I say check something, I mean put a checkmark into the square before it. A small circle means building it as a module, which is not enough.


Under Input device support, check Event interface (I believe this is needed to be able to use F2 to switch to verbose mode)
Graphics support:
Check support for frame buffer devices
Uncheck Tile blitting support! This is only needed for some Matrox cards, but is incompatible with fbsplash
Vesa VGA support: check it and select vesafb-tng if you patched the kernel with the vesafb-tng patch or emission, otherwise use vesafb (or a card-specific driver, e.g. nvidia, ati etc.).
In Graphics support/Console display driver support, check VGA text console and Video mode selection support. Check Framebuffer Console support (but not Rotation).
Go back to Graphics support and check support for framebuffer splash (Scroll down, it should be the last one).

-=-

-=- take advantage of the patch enhancements -=-


In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family Choose the model of your processor.

Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz 

-=-

save the .config and 

> cd /usr/src/linux
make clean

make-kpkg --initrd kernel_image kernel_headers modules_image

when gcc is done crunching

> cd /user/src
dpkg -i *.deb


now reboot and make sure you boot up the new kernel.

-=- after reboot -=-

Open a new terminal and become root:

> su

mkdir fbsplash

cd fbsplash

wget [http://jdurand.web.cern.ch/jdurand/splashutils/binary/miscsplashutils_0.1.3-1_i386.deb](http://jdurand.web.cern.ch/jdurand/splashutils/binary/miscsplashutils_0.1.3-1_i386.deb)

wget [http://jdurand.web.cern.ch/jdurand/splashutils/binary/splashutils-initramfs_1.1.9.10-23_all.deb](http://jdurand.web.cern.ch/jdurand/splashutils/binary/splashutils-initramfs_1.1.9.10-23_all.deb)

wget [http://jdurand.web.cern.ch/jdurand/splashutils/binary/splashutils_1.1.9.10-23_i386.deb](http://jdurand.web.cern.ch/jdurand/splashutils/binary/splashutils_1.1.9.10-23_i386.deb)

dpkg -i *.deb

mkdir /etc/bootsplash/
mkdir /etc/bootsplash/themes

wget [http://www.bootsplash.de/files/themes/Theme-Ubuntu.tar.bz2](http://www.bootsplash.de/files/themes/Theme-Ubuntu.tar.bz2)

tar --bzip2 -xvf Theme-Ubuntu.tar.bz2 /etc/bootsplash/themes

bootsplash2fbsplash Ubuntu

-=-it should be installed.-=-

-=-last step before it actually works-=-

cp /boot/grub/menu.lst /boot/grub/menu.old

gedit /boot/grub/menu.lst

find the line "/boot/vmlinuz-2.6.16-beyond4.1 root=/dev/hda1 ro"
and add "splash=silent,fadein,theme:Ubuntu quiet CONSOLE=/dev/tty1" at the end of it


now reboot and enjoy.

---

### Post by scenestar on 2006-06-29
and to add a graphical cherry on top

[Here's a matching grubsplash for the verbose background in my howto]("http://www.gnome-look.org/content/show.php?content=41701")

---

### Post by knn on 2006-06-30
[QUOTE=scenestar]I like to cut and paste:

su to root


-=- AS mentioned before-=-

When I say check something, I mean put a checkmark into the square before it. A small circle means building it as a module, which is not enough.


Under Input device support, check Event interface (I believe this is needed to be able to use F2 to switch to verbose mode)
Graphics support:
Check support for frame buffer devices
Uncheck Tile blitting support! This is only needed for some Matrox cards, but is incompatible with fbsplash
Vesa VGA support: check it and select vesafb-tng if you patched the kernel with the vesafb-tng patch or emission, otherwise use vesafb (or a card-specific driver, e.g. nvidia, ati etc.).
In Graphics support/Console display driver support, check VGA text console and Video mode selection support. Check Framebuffer Console support (but not Rotation).
Go back to Graphics support and check support for framebuffer splash (Scroll down, it should be the last one).

-=-

-=- take advantage of the patch enhancements -=-


In "General Setup" activate:

-Support for paging of anonymous memory (swap)
--Support for prefetching swapped memory

In "Processor type and features":

-Processor family Choose the model of your processor.

Activate:

-Preemption Model
--Voluntary Kernel Preemption (Desktop)

-High Memory Support
--off -if you have less than 1 GB of RAM
--1GB Low Memory Support -if you have 1GB of RAM
--4GB -if you have more than 1GB of RAM

-Timer frequency
--1000 Hz 

-=-

save the .config and 



when gcc is done crunching


now reboot and make sure you boot up the new kernel.

-=- after reboot -=-

Open a new terminal and become root:


-=-it should be installed.-=-

-=-last step before it actually works-=-

cp /boot/grub/menu.lst /boot/grub/menu.old

gedit /boot/grub/menu.lst

find the line "/boot/vmlinuz-2.6.16-beyond4.1 root=/dev/hda1 ro"
and add "splash=silent,fadein,theme:Ubuntu quiet CONSOLE=/dev/tty1" at the end of it


now reboot and enjoy.[/QUOTE]

All fbsplash themes (like my Ubuntu theme) have to be installed to /etc/splash. Bootsplash themes are installed to /etc/bootsplash, and then they have to be converted.  I don't use fadein because it causes flicker with progressbars.

---

### Post by scenestar on 2006-06-30
[QUOTE=knn]All fbsplash themes (like my Ubuntu theme) have to be installed to /etc/splash. Bootsplash themes are installed to /etc/bootsplash, and then they have to be converted.  I don't use fadein because it causes flicker with progressbars.[/QUOTE]


bootsplash2fbsplash Ubuntu installs the theme straight into the right folder.

---

### Post by knn on 2006-06-30
[QUOTE=scenestar]bootsplash2fbsplash Ubuntu installs the theme straight into the right folder.[/QUOTE]

Ah, sorry, I didn't notice you were using a different theme

---

### Post by knn on 2006-07-01
That's it I give up. I tried to compile the linux restricted modules package, but it just didn't work. I compiled all three (386,686,k7) subarch kernels with beyond1, but the packages made by make-kpkg are missing some files (Makefile.cpu for example), so linux restricted modules won't compile.
If someone knows how to make a complete drop in replacement kernel that fits in perfectly, I might try this again sometime. I think downloading the ubuntu linux-source package and building it (after updating the kernel) might work, but right now I'm quite pissed at the Debian package system and the lack of documentation that I'm not going to start experimenting.

---

### Post by scenestar on 2006-07-01
[QUOTE=knn]a complete drop in replacement kernel that fits in perfectly[/QUOTE]


And why don't you ask for full win32 compatibility while you are at it.

Customising a kernel is one of those trivial things that should have a mandatory "Your Milage May Vary " warning label.

---

### Post by nesl247 on 2006-07-04
Hello there. I'm nesl247 from the Evolution Mission Kernel Patchset. I've read that there are some problems here in regards to fbsplash/splashutils (and a few other problems). I'm sorry to take this off topic, but can anyone with problems post on our site (site in my signature) so that we may get these bugs fixed. 

Again, I'm sorry to interrupt this thread, but since the howto recommends our kernel I felt obligated to get all bug reports so that they may be fixed.

And for those of you who are having problems in the meantime, I do suggest using the beyond kernel patchset. It is a very stable kernel, and maintained by two great people.

P.S. Moderators, if this was spam, I'm sorry. I'm just trying to collect bugs so that people can use the 2.6.17 kernel as the patchset is the recommended one in the first post.

---

### Post by knn on 2006-07-04
[QUOTE=nesl247]Hello there. I'm nesl247 from the Evolution Mission Kernel Patchset. I've read that there are some problems here in regards to fbsplash/splashutils (and a few other problems). I'm sorry to take this off topic, but can someone please post on our site (preferable in our [bugzilla]("http://bugzilla.evolution-mission.org"), main site in my signature) so that we may get these bugs fixed. 

Again, I'm sorry to interrupt this thread, but since the howto recommends our kernel I felt obligated to get all bug reports so that they may be fixed.

And for those of you who are having problems in the meantime, I do suggest using the beyond kernel patchset. It is a very stable kernel, and maintained by two great people.

P.S. Moderators, if this was spam, I'm sorry. I'm just trying to collect bugs so that people can use the 2.6.17 kernel as the patchset is the recommended one in the first post.[/QUOTE]

You don't have to apologize, in fact, thanks for posting, I've updated the howto and included the link to your bugzilla.
I hope you can sort out those problems soon and people can use this great patchset.

---

### Post by nesl247 on 2006-07-04
You are going to have to change the bugzilla link to our main page. I don't know why, but bugzilla never seems to work properly. (I'm starting to hate suExec) Anyways, I do hope to have any issues resolved. Vipernicus, the developer of the patchset is hard at work. 

If we can get a list of all the problems, we can surely fix them, or provide an explanation if they cannot be fixed.

I do like your howto though. It's very nicely done. 

For those of you who are looking into what kernel to use, don't choose an -mm based one. Those are the most problematic as it's an experimental kernel patchset. Not that I'm trying to demote them in any way, but -mm is known to break many patches which are not made specifically for it. (For instance the fbsplash and vesa-tng patch.)

---

### Post by awry on 2006-07-17
Hi everyone,

Thanks, knn, for this useful tutorial.  I've finally gotten fbsplash to work on dapper, with no small bit of effort.

However, I find that the progress bars do not work on any theme that I have tried.  According to [http://olterman.homelinux.net/homelinux/2004/12/28/console-fluff-with-fbsplash/](http://olterman.homelinux.net/homelinux/2004/12/28/console-fluff-with-fbsplash/) this requires some hacks to the init scripts; however, his rc and rcS look nothing like mine, and I'm not sure where to put the hacks in the dapper init system.  

I'm not that well-versed in ubuntu's init system.  Anyone already solve this?

---

### Post by knn on 2006-07-17
Please test my theme first. Progress bars should work, it may just be that the theme is incorrect.

---

### Post by awry on 2006-07-17
Sorry, I should have mentioned -- your theme is the first one I tried.  No love with the progress bar.  How does your theme know when/how to increment the bar?  Is this known to work in dapper?

Is there an updated download link, or is it still the attach at the bottom of the tutorial (page 1)?

Thanks for your help!

---

### Post by awry on 2006-07-17
Also, the text doesn't change throughout the boot process... just "Initializing the kernel..." the whole way through.

---

### Post by bryonhowley on 2006-07-23
> **rogeriovinhal said:**
> 
First, I don't like 60Hz, but if I try to change the frequency to 1024x768@85 at menu.lst, the splash stop working. Why? Is there a way I can make it work with 85Hz?


The only way I could get higher than 60Hz was to compile the kernel with support for it >
Device Drivers > Graphics Support
<*>    VESA VGA graphics support
         VESA driver type (vesafb-tng)  --->
(1024x768-24@85) VESA default mode
This works on my server box with a i810 chipset
It does not work on my desktop with BFG 7800GS(NVIDIA)
With this option on I get 87Hz according to the monitor controls. Much easyer on the eyes in console mode(witch the server runs most of the time).
Hope that helps. On my system anyway the compileing the option in the kernel is the only way to get it to work it simply will not over ride it by putting the option on the kernel line in the menu.lst file.

---

### Post by knn on 2006-07-23
> **awry said:**
> Also, the text doesn't change throughout the boot process... just "Initializing the kernel..." the whole way through.

The init scripts in Ubuntu already have support for usplash. Those fbsplash packages replace some usplash executables which update the progress bar of usplash with scripts that update the progress bar and text of fbsplash. Check if /sbin/usplash_write exists and open it with a text editor. It should be a text file. If it's an executable, then that means the packages were not installed correctly.
Also, try the following:
Ctrl-Alt-F1 to go to Console 1 (You can get back to the desktop by pressing Ctrl-Alt-F7)
log in
sudo su to become root
cd /sbin
./usplash_write PROGRESS 10
the splash screen should appear and the progress bar should be set at 10% (Text should also be there)
F2 to kill the screen
./usplash_write PROGRESS 100 to kill fbsplash.
exit to log out as root and exit again to log out

If it doesn't work and usplash_write is the fbsplash script, then there's some problem.

---

### Post by awry on 2006-07-26
Thanks for explaining how the fbsplash deb's replace the usplash scripts that are already called from init.  That's the extra bit of info I needed.

I had originally installed splashutils from source, without the miscsplashutils package, so I was missing the additional init scripts altogether (oops).

I ended up repackaging the debs to work on dapper, and all is well now.

Incidentally, `usplash_write PROGRESS 10` is not a command that works for me from a tty.  It always returns "PROGRESS: integer expression expected" - so it seems there may be something wrong with the testing methodology you recommended.

Anyway, everything works like a charm now - thanks for the assist!

---

### Post by knn on 2006-07-26
Well, I wrote that from memory on Windows looking at the source of the script. :) And I don't have fbsplash installed anyway.
Anyway, the packages provided by JD should work on Dapper, at least they worked for me the last time I checked, but that was a few versions ago.

Edit: Try ./usplash_write "PROGRESS 10". That should work

---

### Post by scenestar on 2006-07-27
We should turn this into a .deb package.

Knn, feel free to email me so that we can set up a more graphical and more intuitive setup.

---

### Post by knn on 2006-07-27
It already IS a deb package, three to be exact.

---

### Post by conexion200 on 2006-08-04
Hi!
I have problem with the newest versions of packages. During boot, I can see in the console:
```
rm: cannot remove '/lib/splash/cache/survey': Read-only filesystem
```

It appears many times. How can I solve that?

---

### Post by pravuil on 2006-08-24
Got ati fglrx to work with full acceleration with vesafb-tng with Kernel 2.6.16.27. Used all the patches but the suspend2. Probably would've worked with or without it just forgot to patch the kernel source with it. Also compiled kernel 2.6.17.10 with those patches and kept running into the same problem with the fglrx problem, this solution should work with that version too:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Problems_with_module-assistant")
Forgot to touch makefile.cpu in both the header and linux source folders. Thanks man, the howto worked perfectly for me. Now I just need to finish configuring fluxbox and xdm and I got my finished custom ubuntu box.

---

### Post by dolny on 2006-08-31
Hmm the link to evolution-mission.org is dead :( Any workarounds? I want to install the patches and stuff correctly.

---

### Post by Rui Pais on 2006-08-31
> **dolny said:**
> Hmm the link to evolution-mission.org is dead :( Any workarounds? I want to install the patches and stuff correctly.

They have problems with they servers. 
Maybe trying tomorrow or send a PM to [nesl247 (the maintainer of Evolution-Emission)]("http://ubuntuforums.org/member.php?u=132575") informing/asking for details....

---

### Post by storytobi on 2006-09-21
does anybody know, how I can use fbsplash without sacrificing my xgl-compiz setup which needs nvidia instead of nv ?

what I want is a completely graphical boot process from BIOS to GDM.

- usplash is the standard, it starts very early in the boot process, but it only detects a very low screen and color resolution
- splashy is a bit better because it detects a higher resolution but it can neither handle widescreen (1280x800) nor 32bit color mode, and it pops in too late after some lines of text are already on the screen and it flickers during startup.
- fbsplash was my choice back in my gentoo days, because it worked perfect with directfb, my screen and color resolution and covers the whole boot process from GRUB to GDM.

BUT: According to the tutorial on this page I have to change the device entry in the /etc/X11/xorg.conf file from "nvidia" back to "nv" which throws me back from Xgl to Xorg, which is a great loss for me.

AFAIK, Xgl and the COMPIZ eye-candy absolutely needs "nvidia" in the driver section.

Has anybody other suggestions, how to fix this issue?

---

### Post by knn on 2006-09-21
> **storytobi said:**
> does anybody know, how I can use fbsplash without sacrificing my xgl-compiz setup which needs nvidia instead of nv ?

what I want is a completely graphical boot process from BIOS to GDM.

- usplash is the standard, it starts very early in the boot process, but it only detects a very low screen and color resolution
- splashy is a bit better because it detects a higher resolution but it can neither handle widescreen (1280x800) nor 32bit color mode, and it pops in too late after some lines of text are already on the screen and it flickers during startup.
- fbsplash was my choice back in my gentoo days, because it worked perfect with directfb, my screen and color resolution and covers the whole boot process from GRUB to GDM.

BUT: According to the tutorial on this page I have to change the device entry in the /etc/X11/xorg.conf file from "nvidia" back to "nv" which throws me back from Xgl to Xorg, which is a great loss for me.

AFAIK, Xgl and the COMPIZ eye-candy absolutely needs "nvidia" in the driver section.

Has anybody other suggestions, how to fix this issue?


You can reinstall the nvidia driver after installing your custom kernel, but you'll have to use the nvidia installer which compiles the kernel module for your kernel. On Dapper, just running the installer downloaded from nvidia.com WILL NOT WORK. You need this howto: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
I never could get Xgl to work with my custom kernel, that's why I stopped using fbsplash

---

### Post by storytobi on 2006-09-21
> **knn said:**
> You can reinstall the nvidia driver after installing your custom kernel, but you'll have to use the nvidia installer which compiles the kernel module for your kernel. On Dapper, just running the installer downloaded from nvidia.com WILL NOT WORK. You need this howto: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
I never could get Xgl to work with my custom kernel, that's why I stopped using fbsplash
thanks for that link. I'll try it on the weekend.
Is there another splash I am not yet aware of?
gensplash(fbsplash), bootsplash(splashy), usplash, ...?

I also read in another post, there is an option for gensplash to load it in userspace not kernel. Does it probably work with original kernel, too?

---

### Post by knn on 2006-09-21
> **storytobi said:**
> thanks for that link. I'll try it on the weekend.
Is there another splash I am not yet aware of?
gensplash(fbsplash), bootsplash(splashy), usplash, ...?

I also read in another post, there is an option for gensplash to load it in userspace not kernel. Does it probably work with original kernel, too?

> This means that if you don't care about having an image in the background of your system consoles and all you really want is a progress bar and a nice picture while (re-)booting the system, you can just use splashutils and skip everything related to fbsplash, thus making gensplash a 100% userspace solution. No kernel patches are required in this case.


There is, but you don't get the console backgrounds and I don't know how early fbsplash will start (however since usplash can start early enough, fbsplash should be able to do that too, if set up correctly)

---

### Post by Magneto on 2006-09-28
great howto

I originally included all of the noted kernel items in addition to the ones required by my system but got that modules.dep error before even installing splashutils. Saw a few other errors with filesystem drivers that hate being builtin , especially UFS. It disappeared when I just stuck to copying the ubuntu config and only removing certain items and keeping necessary drivers as modules. Thought that was weird. I used the latest 2.6.17 Emission8 patches + idehotfix + other patches listed here. 
In case that helps anyone.

Also had to copy a new ipw2200 firmware version 2.4 to /lib/firmware/2.6.17 to get it working again. Copy it over to the name of the file that gives you the error.  If I came across those 2 bits I would have saved myself alot of reading and time.

Even with the modifications people listed to stop the flicker* it didnt work for me. I have to run my bootsplash in verbose mode to avoid that issue.

Im using radeonfb @1400x1050-32@60 my laptop's default resolution and a modified version of the original poster's Ubuntu theme with certain things changed to display in 1400x1050 mode.

convert some.png some.jpg  is a great way to modify a desktop wallpaper to plug into verbose or silent pics. jpg wouldnt work for me in gentoo but png did and in ubuntu its reversed png would only shoot error 22's

ill try fb grab in a minute and see if I can up a screenshot

---

### Post by knn on 2006-09-29
About that flicker: Did you add fade to the splash parameters? It caused flickering on my computer, that's why I removed it from the howto

---

### Post by Magneto on 2006-09-29
> **knn said:**
> About that flicker: Did you add fade to the splash parameters? It caused flickering on my computer, that's why I removed it from the howto
no I think I looked for it the other day as a possible cause for the flickering.
I have a more pressing problem - fbsplash turning consoles off and on at boot repeatedly 

[4294801.253000] fbsplash: console 0 using theme 'whateverIsetthistoo'

[4294801.123000] fbsplash: switched splash state to 'off' on console 1


and that repeats for every console and then tries again  so I get hundreds of pretty fbsplash lines :D - whether I set the theme in grub or not - the themes set but that goes nonstop during boot until login prompt on console1
 ever see that? i just started researching it and so far have only seen suspend issues and other stuff that doesnt really talk about what it is. Im guessing its the fbsplash daemon or whatever it is that runs from init.d maybe with debugging on

---

### Post by alexisdm on 2006-10-08
> **Magneto said:**
> 
and that repeats for every console and then tries again  so I get hundreds of pretty fbsplash lines :D

In splash=verbose mode, usplash_write checks if splashutils is running ("splashutils status") but it never is, so it starts it at each item in the progress list.

Try putting that line in /etc/init.d/splashutils
```

 [[ -z "$(/sbin/splash_util -c getstate --tty=${TTY} 2>/dev/null| grep 'off')" && -n "$(/sbin/splash_util -c getcfg --tty=${TTY} 2>/dev/null| grep ^theme:[[:space:]]*${theme}$)" ]] && continue
```

just before the block
```

/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setcfg 2>/dev/null
/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setpic 2>/dev/null
/sbin/splash_util --tty="${TTY}" -c on 2>/dev/null
```

And in /sbin/splash replace:
```

if [[ ${SPLASH_MODE_REQ} == "verbose" ]]; then
${SPLUTIL} -c on 2>/dev/null
exit 0

```

by

```

if [[ ${SPLASH_MODE_REQ} == "verbose" ]]; then
if [[ -z "$(${SPLUTIL} -c getstate 2>/dev/null| grep 'off')" ]]; then
${SPLUTIL} -c on 2>/dev/null
fi
exit 0

```

This will prevent the binaries splash_util and splash_util.static to be run more than once if the theme is already set and the splash/background already active.

---

### Post by Magneto on 2006-10-25
> **alexisdm said:**
> In splash=verbose mode, usplash_write checks if splashutils is running ("splashutils status") but it never is, so it starts it at each item in the progress list.

Try putting that line in /etc/init.d/splashutils
```

 [[ -z "$(/sbin/splash_util -c getstate --tty=${TTY} 2>/dev/null| grep 'off')" && -n "$(/sbin/splash_util -c getcfg --tty=${TTY} 2>/dev/null| grep ^theme:[[:space:]]*${theme}$)" ]] && continue
```

just before the block
```

/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setcfg 2>/dev/null
/sbin/splash_util --tty="${TTY}" -m v -t "${theme}" -c setpic 2>/dev/null
/sbin/splash_util --tty="${TTY}" -c on 2>/dev/null
```

And in /sbin/splash replace:
```

if [[ ${SPLASH_MODE_REQ} == "verbose" ]]; then
${SPLUTIL} -c on 2>/dev/null
exit 0

```

by

```

if [[ ${SPLASH_MODE_REQ} == "verbose" ]]; then
if [[ -z "$(${SPLUTIL} -c getstate 2>/dev/null| grep 'off')" ]]; then
${SPLUTIL} -c on 2>/dev/null
fi
exit 0

```

This will prevent the binaries splash_util and splash_util.static to be run more than once if the theme is already set and the splash/background already active.
alex you are the man/woman

gonna try that tonight, I will post back with the results

---

### Post by T-One on 2006-11-03
I need help. I'm trying to build this against 2.6.18 (emission1) on Edgy. I can get the kernel compiled, splashutils installed, etc...but I'm having problems:

If I use splash_geninitramfs, the splash will show at 1024x768, but any kernel messages over-write the splash. Also, no progress bar movement and text is always "loading kernel image". TTY1 does have the splash, however.

If I use the generic initrd file (backed up from kernel install), I get no splash at all. No mention of fbsplash in dmesg. (Vesafb is there, though the screen res during startup is only 640x480)

Am I missing something here? I've had the exact same problem using 2.6.17 and 2.6.18 kernels, all with various flavors of emission, beyond, hand-patching, etc. I've even tried a bootsplash splash (converted) and got the same exact problems.

Only thing I haven't tried yet is building splashutils from source. I'm also thinking there's either a problem with /etc/init.d/splashutils script or the fact that I'm missing any splash scripts in /etc/rc2.d (save for usplash's K10usplash script for shutdown)

---

### Post by knn on 2006-11-04
If you use Ubuntu's generic initrd file, you're using Ubuntu's kernel, that's why you don't get the splash (the initrd is a ramdisk image that contains the kernel and all the modules). You also only get the old vesafb, not vesafb-tng, which uses a different syntax, that's why it's only 640x480
I think it might be a problem with the scripts. Unfortunately I'm no longer using fbsplash (new usplash is fine), but I'll try to help. You don't need splash_geninitramfs, instead:

4. Disable usplash:
Since splashutils provides usplash, you can uninstall usplash (*ubuntu-desktop will not be uninstalled). If you don't want to do that, disable it manually:

-instructions not available since the forum cut off this part of the howto and I can't remember them. Uninstall usplash instead.

5.
Regenerate the initrd image: If you uninstalled usplash you don't have to do this.
Whenever you install a new theme you'll have to regenerate the initrd image to be able to use it. Just run sudo update_initramfs. It will copy all themes in /etc/splash.

The fbsplash packages add a script that automatically adds the themes to the initrd when you run update_initramfs, so there's no need to run splash_geninitramfs. You do have to uninstall usplash, since it will also copy itself to the initrd when you run update_initramfs. Uninstalling usplash will also run update_initramfs (to remove usplash from the initrd).
I doubt this will solve your problem tough, as it seems that the fbsplash daemon is killed too early, and that is probably caused by a script bug. Unfortunately I can't help you with that. You may want to contact the author of the scripts and the Debian howto (the link is in the first post)

---

### Post by T-One on 2006-11-05
I tried using both the generic initrd and the new one. The generic gave no theme at all, though the one I generated did give the splash, there were the problems I mentioned.

The reason I want to use fbsplash was for compatibility with suspend2, capability to switch to verbose mode, along with themed ttys. 


I'll try to contact the author, as it seems to me that the scripts are what's missing.

---

### Post by Rui Pais on 2006-11-06
> **knn said:**
> ...
4. Disable usplash:
Since splashutils provides usplash, you can uninstall usplash (*ubuntu-desktop will not be uninstalled). If you don't want to do that, disable it manually:

-instructions not available since the forum cut off this part of the howto and I can't remember them. Uninstall usplash instead. 

simply backup /sbin/usplash_write and replace it for:
> #!/bin/sh
#
## Wrapper usplash - fbsplash
#
## Make sure we process only PROGRESS command
## (until /etc/init.d/rc supports more)
#
exit 0


> **knn said:**
> ...
I doubt this will solve your problem tough, as it seems that the fbsplash daemon is killed too early, and that is probably caused by a script bug... 

in my case the script was killed by a long list of "[[: wrong substitution" or something like...

I replace the first line of /etc/init.d/splashutils from #!/bin/sh to:
```
#!/bin/bash
```
and it worked again. I'm using smae splashutils package then in dapper, not much updated, but since they work.

My only problem now is that boot messages appeared over the themed image...

---

### Post by knn on 2006-11-07
> **Rui Pais said:**
> simply backup /sbin/usplash_write and replace it for:




in my case the script was killed by a long list of "[[: wrong substitution" or something like...

I replace the first line of /etc/init.d/splashutils from #!/bin/sh to:
```
#!/bin/bash
```
and it worked again. I'm using smae splashutils package then in dapper, not much updated, but since they work.


If you're using Edgy, sh is symlinked to Dash, not Bash like in Dapper. Dash is a smaller, faster shell interpreter, but can cause problems like that

---

### Post by Rui Pais on 2006-11-07
> **knn said:**
> If you're using Edgy, sh is symlinked to Dash, not Bash like in Dapper. Dash is a smaller, faster shell interpreter, but can cause problems like that

yes, i figured it was something like that... 
those kind of things don't bring any special kind of speed or improvement, and creates a lot of problems with scripts not originally from Ubuntu, reducing compatibility with non-supported software :(  
Thanks for the info.

---

### Post by ~Gh05t~ on 2006-11-10
HI all, 
i just built a new kernel (2.6.18-emission1) for fbsplash, too, and i have the same problem like T-One.

System boots, fbsplash starts (resolution is correct), but i do not have any Silent-Mode. When fbsplash gets started my startup-screen just has another background, but the silent-image is never shown.

Another thing is, my System takes arround 50% of boottime on the Kernel (dirty black on white, just like before), 30% on init-scripts with non-silent-fbsplash and 20% on loading Xorg/kdm. 
Is it possible to start fbsplash directly with the kernel instead of the init-script? Because at the moment i do not have any splash on 70% of my bootprocess...

btw: how do i create a initrd-file with fbsplash-stuff ONLY? Everything my system needs is hardcoded in my kernel...

---

### Post by knn on 2006-11-10
Generate the initrd with splash_geninitramfs. run zcat yourinitrd_file | cpio --list to see what the initrd contains

---

### Post by ~Gh05t~ on 2006-11-11
ok, had a nearly empty initrd :-\"  
Built a new one, now splash starts very early. 

Found another thing:
When i started the slashutils-initsctipt after booting i got that:
```

mount: mount point /lib/splash/tmp does not exist
/etc/init.d/splashutils: line 143: eerror: command not found
/sbin/splash: line 172: splash_get_mode: command not found
/etc/init.d/splashutils: line 145: return: can only `return' from a function or sourced script
mount: special device /lib/splash/tmp does not exist
mount: mount point /lib/splash/tmp does not exist
umount: /lib/splash/tmp: not found

The filesystem mounted on / doesn't contain the /dev/tty1 device
which is required for the silent splash to function properly.
Silent splash will not be enabled. Please create the appropriate
device file to avoid this message.
```
So i added a directory /lib/splash/tmp and on next reboot my silent splash-process-bar startet moving (and stays silent). :) 

The only Problem i have now is that boot-messages of some init-scripts get printed over the silent-splash :-?  
That doesnt look very nice, any idea? The messages do not appear on verbose-fb-console when switching back to tty1 (from my X-Terminal), i do not even find them in any logfiles, too.

BTW: I use kUbuntu 6.10... anybody here without problems on ubuntu edgy with fbsplash/splashutils?

---

### Post by knn on 2006-11-11
Ubuntu's init outputs to tty8, not tty1. Check if the messages are there

---

### Post by Rui Pais on 2006-11-11
> **~Gh05t~ said:**
> ...

BTW: I use kUbuntu 6.10... anybody here without problems on ubuntu edgy with fbsplash/splashutils?

Yes, i have the same problem on Ubuntu 6.10. 
Everything works well, but boot messages appears over the splash image that looks pretty awful because my theme background is almost white and the messages are white letters on lines with black foreground that go all over the screen (not only the first line that sometimes happen on dapper...)
:(

---

### Post by ~Gh05t~ on 2006-11-11
> **knn said:**
> Ubuntu's init outputs to tty8, not tty1. Check if the messages are there
no, tty1-tty6 is console login, 7 is X, rest is blank... 

The messages are just the basic output of initscripts. That should be displayed on verbose-fb-splash-console, but there is nothing. The output there ends with kernel-init.

There was another problem with the usplash_write scipt, it used #!/bin/sh...  think i need to get rid of /bin/dash!
But that didnt solve my problem.

---

### Post by Rui Pais on 2006-11-11
> **~Gh05t~ said:**
> ...
There was another problem with the usplash_write scipt, it used #!/bin/sh...  think i need to get rid of /bin/dash!
But that didnt solve my problem.

see one of my posts above... just replace 
```
#!/bin/sh
``` with ```
#!/bin/bash
```

---

### Post by ~Gh05t~ on 2006-11-11
yeah, i know that problem... hoped that works, but it doesnt. 
Damn, would be such a nice system with fbsplash in combination with suspend2 hibernate... :sad: 

Question: What stands the boot-parameter CONSOLE=/dev/tty1 for? Where is defined where the init-output goes to?

---

### Post by Rui Pais on 2006-11-11
> **~Gh05t~ said:**
> Question: What stands the boot-parameter CONSOLE=/dev/tty1 for? Where is defined where the init-output goes to?

Here are the link for the official wiki for [fbsplash/gensplash]("http://gentoo-wiki.com/HOWTO_fbsplash"), check specially the part about the [kernel options]("http://gentoo-wiki.com/HOWTO_gensplash#Kernel_Options"). 
According to the wiki passing that option to the kernel with the "quiet" word on the kernel line should suppress kernel messages to support silent boots. 
I presume that its fail on something exclusively of edgy, since the same kernel/boot options work on dapper.

---

### Post by knn on 2006-11-11
> **~Gh05t~ said:**
> no, tty1-tty6 is console login, 7 is X, rest is blank... 


I know that, but when I switch to tty8 I see some init messages like activating swap and checking root file system.

---

### Post by Rui Pais on 2006-11-11
> **knn said:**
> I know that, but when I switch to tty8 I see some init messages like activating swap and checking root file system.

well, thats the problem. Apparently at edgy those messages are produced at tty1 (why?) and ***over*** the splash image...

---

### Post by knn on 2006-11-11
> **Rui Pais said:**
> well, thats the problem. Apparently at edgy those messages are produced (why?) at tty1 and **over** the splash image...

That's strange. I use Xgame to run games on a separate X server and I remember switching to tty8 on Dapper. When I upgraded to Edgy, the boot messages started showing up on tty8 and Xgame now uses tty9

> Here are the link for the official wiki for fbsplash/gensplash, check specially the part about the kernel options.
According to the wiki passing that option to the kernel with the "quiet" word on the kernel line should suppress kernel messages to support silent boots.
I presume that its fail on something exclusively of edgy, since the same kernel/boot options work on dapper.

quiet only suppresses kernel messages, not init messages. I suspect upstart is the culprit, but as I've said, Edgy's high res usplash is good enough for me, and I'd recommend you stay with it, and use fbsplash for the console backgrounds.

---

### Post by Rui Pais on 2006-11-11
> **knn said:**
> That's strange. I use Xgame to run games on a separate X server and I remember switching to tty8 on Dapper. When I upgraded to Edgy, the boot messages started showing up on tty8 and Xgame now uses tty9
Thats the most annoying part too me, cause i swear that at beginning edgy did put messages on tty8 and at certain point started to use tty1, even when i'm not using any splashutils or the default kernel :-k 
> 
quiet only suppresses kernel messages, not init messages. I suspect upstart is the culprit, but as I've said, Edgy's high res usplash is good enough for me, and I'd recommend you stay with it, and use fbsplash for the console backgrounds.
Well i start to agree with you on that... Usplash can be tweaked for something good looking enough... just trying to use fbsplash to keep suspend2 userui using a nice, integrated, suspend image... 

Anyway i managed to bork my edgy beyond recuperation (there was a freeze that force me to do a bad reset and since then is completely dead :() My last backup are from my pre-days of trying to make suspend2/fbsplash work so i think i will use that copy and try to use it with usplash and text mode suspend (faster anyway).

---

### Post by knn on 2006-11-11
Boot the live-cd and run fsck.ext3 on the root partition. It saved my disk after a hard reboot.

---

### Post by Rui Pais on 2006-11-11
> **knn said:**
> Boot the live-cd and run fsck.ext3 on the root partition. It saved my disk after a hard reboot.

I tried, that and
```
e2fsck -f /dev/hdb3
```
no errors report... 
kernel keeps panic or freeze after the 1st or 2nd message...

No problem, i'll use my backup, an aptitude upgrade and a kernel build and things should going back to track again... maybe the boring messages on tty1 even go away for good. 

Thanks for your suggestion, anyway.


*Edit:* btw, just for curiosity, with my old backup boot messages are going to tty8 again. Something had gone bad in my working version, probably somewhere while i was trying to get splashutils work.

---

### Post by ~Gh05t~ on 2006-11-12
> **knn said:**
> ... I suspect upstart is the culprit, but as I've said, Edgy's high res usplash is good enough for me, and I'd recommend you stay with it, and use fbsplash for the console backgrounds.

On [that page](http://upstart.ubuntu.com/doc/getting-started.html) i found some hints to change message output-direction (section 'console').   With that i got rc2.d's output to verbose-fbsplash on tty1 (just add/change 'console <outputtype>' to configs in /etc/event.d).

But maybe not upstart is the problem, but the new version of [lsb](http://packages.ubuntulinux.org/edgy/misc/lsb-base). It provides a shell-script collection that handles init-scripts and their outputs. Some right placed comments and you have a clear silent-fbsplash, but you do not have any output at all 8) 
 
Baybe some of you will take a look at /etc/lsb-base-logging.sh or /lib/lsb/init-functions . That files provide the functions called in init scripts to print console output. Unfortunately i do not understand it because i dont know the values of vars on boottime or even what they could be :-k .


@usplash: The new feature with high-res makes it halfway useable, but i will NOT use both of them! I prever fbsplash because of usability for suspend2, so ill use fbsplash or nothing.

> **knn said:**
> I know that, but when I switch to tty8 I see some init messages like activating swap and checking root file system.
Could you find out where that is configured? Is it just syslog or somethin else? Do you have output on tty1, too?

---

### Post by knn on 2006-11-13
The only output to tty1 is grub's output. Because of upstart, init messages don't output anymore, the only things on tty8 are swap and disk check messages

---

### Post by ~Gh05t~ on 2006-11-13
> **knn said:**
> The only output to tty1 is grub's output. Because of upstart, init messages don't output anymore, the only things on tty8 are swap and disk check messages
Hmmm... you use default Edgy, too? Does silent-fbsplash work for you without problems?

---

### Post by knn on 2006-11-13
I don't have fbsplash.

---

### Post by ~Gh05t~ on 2006-11-13
> **knn said:**
> I don't have fbsplash.You said that before, but does it work? Or didnt you even test it?

---

### Post by knn on 2006-11-13
It worked on Dapper, with an older version of fbsplash. I did not test it on Edgy

---

### Post by Rui Pais on 2006-11-13
> **knn said:**
> The only output to tty1 is grub's output. Because of upstart, init messages don't output anymore, the only things on tty8 are swap and disk check messages

the problem seems to be that as long as one removes uspalsh or deactivates its starts those messages, about swap and so on, are send to tty1...

---

### Post by black_rob on 2006-11-15
Hi.  I read this whole thread, and it was a big help in in getting fbsplash to work the way it used to when I used Gentoo, so I thought I'd share my twist on how to get a nice console background.

I have no use for any splash screen on startup, I like the kernel messages,  so I removed the whole "splash..." part out of menu.lst.

I like to have own custom splash appear after I've logged in, separate from any other users or the default console background, so I put the following in my .bashrc:

VCN=${VCON:8}
export VCN
if [ $TERM = "linux" ]
        then /usr/bin/splash_manager --tty=$VCN -m  s -t robert -c set
        consolechars -f Lat15-Terminus16
fi

and I put a similar line into .bash_logout to reset the splash background (and console font) back to the default after I've logged out.

To get this to work I had to edit /etc/udev/rules.d/40-permissions.rules and add the following line:

KERNEL=="fb*"   GROUP="video", MODE="0660"

I don't know if editing the device permissions was a good idea, but I'm pretty happy with how my console looks now.

---

### Post by T-One on 2006-11-29
Apparently the problem I was having before was due to the startup scripts in the [SplashUtils]("http://home.tele2.fr/jdurand/fbsplash/fbsplash.html") package, which has been updated since.

Now works like a charm.

Next up: Getting Suspend2 to work (and the Gnome Suspend/Hibernate functions to use the scripts...) Any help here will be appreciated.

---

### Post by Azrael Nightwalker on 2007-01-16
> **knn said:**
> **5.** Set a password for root if you don't already have one: sudo passwd root. Then, type su to switch to root.
That is not necessary. "sudo bash" will do just fine.

BTW: anyone tried to talk to Ubuntu devs about including fbsplash?

---

### Post by knn on 2007-01-16
> **Azrael Nightwalker said:**
> That is not necessary. "sudo bash" will do just fine.

BTW: anyone tried to talk to Ubuntu devs about including fbsplash?

I don't think that will happen. Usplash is pretty enough with Edgy's updates. And they're going to implement things like a second progress bar for fsck for usplash, so fbsplash would be a step backwards.

---

### Post by Azrael Nightwalker on 2007-01-16
Ok.
All I actually would like to see is a nice console, like in Suse, Mandriva or Gentoo - a console with an image behind it. Is fbsplash the only way to achieve it?

---

### Post by knn on 2007-01-17
> **Azrael Nightwalker said:**
> Ok.
All I actually would like to see is a nice console, like in Suse, Mandriva or Gentoo - a console with an image behind it. Is fbsplash the only way to achieve it?

Yes, but it's easier to set up than the splash screen. You do have to patch the kernel however.

---

### Post by billydv on 2007-03-28
Okay,  Just  to  be  clear,  has  anyone  actually  gotten  the  silent  fbsplash  to  work  properly  on  edgy  using  the  2.6.20  kernel  and  if  so  what  EXACTLY  did  you  do?
Ive  tried  the  changes  in  the  usplash_write  and  etc/init.d/splash  and  nothing  worked.

---

### Post by cumanzor on 2007-05-09
How do you make this work on Feisty?

---

### Post by biasquez on 2007-05-11
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
/etc/initramfs-tools/hooks/splashutils: fbsplash initramfs setup is starting
/etc/initramfs-tools/hooks/splashutils: Copying /usr/bin/chvt
/etc/initramfs-tools/hooks/splashutils: Copying /sbin/splash_helper
/etc/initramfs-tools/hooks/splashutils: Copying /etc/splash/luxisri.ttf
/etc/initramfs-tools/hooks/splashutils: Copying theme '/etc/splash/Ubuntu'
/etc/initramfs-tools/hooks/splashutils: Creating /dev/fbsplash device
/etc/initramfs-tools/hooks/splashutils: fbsplash initramfs setup is finished


  
---> not worked my splash like described in this howto. exactly when my pc start, i see black screen with text like normal boot less "quiet". nothing progress bar, nothing image.my distro is feisty.

---

### Post by echo6 on 2010-06-27
I'm not really interested in using boot splash, I'm quite happy with Plymouth on Ubuntu 10.04.  However I do want consoledecor.

I've patched 2.6.25-rc3 kernel and got /dev/fbcondecor, not I want to compile the fbcondecor utils to be able to setup background images on my virtual terminals.

I've added in the repositories as per [http://jeandamiendurand.free.fr/debian/splashutils/](http://jeandamiendurand.free.fr/debian/splashutils/)

However when trying to add splashutils I get scared off by the number of items that need to removed to accommodated.  So I decided to try and build from source.

When building from source I get an error for which I have not been able to resolve.

```
make[3]: O2: Command not found
ar: jcapimin.o: No such file or directory
make[3]: *** [libjpeg.a] Error 1
make[2]: *** [libjpeg.a] Error 2
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
```

---

