---
title: "32 bit Download?"
date: 2016-06-03
forum: New to Ubuntu
---

### Post by Portaldominates on 2016-06-03
I was wondering, is the Ubuntu download 32 bit or 64 bit? I have a Tecra M2 with a 32 bit processor, so I need a 32 bit download. Thanks!

---

### Post by maxl4 on 2016-06-03
Hi there,
I've got a similar question:  my hardware is 32-bit (a 2008 Compaq desktop), and I have downloaded this    ubuntu-16.04-desktop-i386.iso   image thinking it is a 32-bit version of Ubuntu.  But when I installed it, the "uname -a" shows it's running a 64-bit version of Linux.  How is that possible?
I am actually seeing a lot of instabilities (Unity desktop hanging often), and I am thinking it's because of this calamity:  a 64-bit OS running on 32-bit hardware...

I'd really appreciate any help with this.
Thanks,
Max

---

### Post by thatsallurspaceships on 2016-06-03
> **Portaldominates said:**
> I was wondering, is the Ubuntu download 32 bit or 64 bit? I have a Tecra M2 with a 32 bit processor, so I need a 32 bit download. Thanks!you don neet do habve to use 64bit install
if tthere is enough ram >2gb you **can** use 64 bit

---

### Post by grahammechanical on 2016-06-03
The default download from ubuntu.com is 64 bit (amd64). You want i386. For Ubuntu 16.04 you will find it here. Click on xenial-desktop-i386.iso

[http://cdimage.ubuntu.com/xenial/daily-live/current/](http://cdimage.ubuntu.com/xenial/daily-live/current/)
[URL="http://cdimage.ubuntu.com/xubuntu/releases/xenial/release/"]
[/URL]Ubuntu may not be the best flavour to install on a computer with a 32 bit CPU. Other factors to consider are the amount of RAM and the capabilities of the video adapter. Ubuntu needs a video adapter that can do hardware accelerated 3D rendering.

You might need to consider Xubuntu

[http://cdimage.ubuntu.com/xubuntu/releases/xenial/release/](http://cdimage.ubuntu.com/xubuntu/releases/xenial/release/)

Lubuntu

[http://cdimage.ubuntu.com/lubuntu/releases/xenial/release/](http://cdimage.ubuntu.com/lubuntu/releases/xenial/release/)

Ubuntu Mate

[http://cdimage.ubuntu.com/ubuntu-mate/releases/xenial/release/](http://cdimage.ubuntu.com/ubuntu-mate/releases/xenial/release/)

Each of these flavours have their own web site. This chart may help choose the most appropriate flavour for you computer.

[URL="https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared"]https://bryanquigley.com/memory-usage/ubuntu-16-04-livecd-memory-usage-compared

[/URL]Each of these flavours has their own web site. Oh, by the way, A 64 bit ISO image will not run on a 32 bit CPU. Even if we managed to install a 64 bit OS on a computer with a 32 bit CPU it would not load. This is scientific fact. Whereas, a 32 bit OS will run on a 64 bit CPU.

Regards.

EDIT: To avoid arguments or difference of opinion, I have just shutdown my 64 bit install of Ubuntu and loaded a 32 bit install of Ubuntu. This is the printout from uname -a

> graham@sdb1-yakkety:~$ uname -a
Linux sdb1-yakkety 4.4.0-23-generic #41-Ubuntu SMP Mon May 16 23:03:32 UTC 2016 i686 i686 i686 GNU/Linux


Notice, the i686. That indicates the 32 bit kernel version. System Settings>Details will also show the OS type. It says 32 bit.

---

### Post by oldfred on 2016-06-03
My 10 year old Toshiba was 64 bit. I used 32 bit Ubuntu for a few years then converted to 64 bit.
Before Unity it worked well.
But issue with newer versions of Ubuntu was Unity. Full Ubuntu with Unity would not run or barely ran. I installed fallback which was the old gnome2 style and was much more lightweight gui and worked reasonably well.

Most, if system is older need Lubuntu or Xubuntu as graphics horsepower is the issue, not CPU or Ubuntu.

---

### Post by Portaldominates on 2016-06-03
Thanks guys! I will try Xenial first, then Lubuntu if that doesn't work.

---

### Post by maxl4 on 2016-06-03
Thanks for the tips about other flavors.  The reason I was confused about the bitt-ness of my Linux is because the "uname -a" command reports it as 64-bit, and my attempt to install a 32-bit NVIDIA video driver failed with the error message:  "you are running a 64-bit system".  
Wonder if someone else installed a 32-bit Ubuntu and could check and see what the 'uname -a' command writes out?..

---

### Post by howefield on 2016-06-03
> **maxl4 said:**
> ..Wonder if someone else installed a 32-bit Ubuntu and could check and see what the 'uname -a' command writes out?..

What exactly is the output of uname -a for you ?

If you used a 32 bit iso then it is a 32 bit install.

---

### Post by mastablasta on 2016-06-03
> **maxl4 said:**
> Hi there,
  ubuntu-16.04-desktop-i386.iso   image thinking it is a 32-bit version of Ubuntu. 


it is a 32 bit.

> But when I installed it, the "uname -a" shows it's running a 64-bit version of Linux.  How is that possible? 

it's not.

also 64bit won't run on 32 bit (by won't run i mean it won't even boot)

---

### Post by ajgreeny on 2016-06-03
This is what my virtual install of 32bit Xubuntu-core 16.04 shows me
```
Linux Xubuntu-Core-16 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:15 UTC 2016 i686 i686 i686 GNU/Linux
```
A 64bit system will show similar 
```
Linux XubuntuTrusty 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:32:09 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux 
```
Note, however, the different ending references of **i686** for 32bit and **x86_64** for 64bit.

---

### Post by maxl4 on 2016-06-03
> **mastablasta said:**
> it is a 32 bit.



it's not.

also 64bit won't run on 32 bit (by won't run i mean it won't even boot)


Here is what my uname -a command spits out.  I know, it's supposed to be a 32-bit system but it has "_64" in it.  

[INDENT][I]Linux max-KJ383AA-ABA-SR5450F 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux 
[/I][/INDENT]

I have just re-installed clean Ubuntu from the same  ubuntu-16.04-desktop-i386.iso   image, and noticed in the details window  some components labelled AMD64 (even though I have an Intel processor  in my box) - I guess those components were being installed...

---

### Post by maxl4 on 2016-06-03
Ran another command:    lshw

it showed me that my processor is, indeed, 64-bit  (but for some reason the box originally came with a 32-bit Windows Vista Home Premium)...   I guess I am doomed at this point.  The root cause of my problems is Compaq/HP who assembled my system back in 2008.  :/

Thanks guys!
Sorry I spooked everyone off.  
Will take one last whack at it:  try installing a 64-bit Ubuntu, and if that fails, I will need to change my hardware.

Thanks!
Max

---

### Post by howefield on 2016-06-03
> **maxl4 said:**
> I have just re-installed clean Ubuntu from the same  ubuntu-16.04-desktop-i386.iso   image, and noticed in the details window  some components labelled AMD64 (even though I have an Intel processor  in my box) - I guess those components were being installed...

AMD64 is just a historical reference to the fact that AMD were first with the instruction set. Don't worry about that on an Intel based system, it is only a naming convention.

On your live Ubuntu media you will find a README.diskdefines file on the root of the disk, that will tell you whether you have downloaded the 32 bit or the 64 bit version. It isn't possible to get a 64 bit kernel from a 32 bit installation.

---

### Post by maxl4 on 2016-06-05
Well, finally.  I tried both:  32-bit and 64-bit Ubuntu on my Presario 5450 hardware, and both of them exhibited desktop freeze.  Maybe due to the fact mentioned above that Ubuntu wants graphics hardware acceleration.  Maybe the video driver is not quite compatible with my NVIDIA graphics card...  Following Graham's suggestion, I moved on to Linux Mint, and so far haven't seen any freezes.  Thanks to everyone for contributing to this thread!

---

### Post by X-RED_Tech on 2016-06-05
You could have just installed the proprietary drivers and solved it in Ubuntu. It's very easy.
Linux Mint already packs and installs - illegally - the nvidia drivers, that's why it works fine immediatelly. But if you're happy with it, enjoy.

---

### Post by howefield on 2016-06-05
> **X-RED_Tech said:**
> ...Linux Mint already packs and installs - illegally - the nvidia drivers, that's why it works fine immediatelly....

Illegal to preinstall a graphics driver - in what way ?

---

### Post by X-RED_Tech on 2016-06-05
In their [license]("http://www.geforce.com/Drivers/License") way and the same for many closed-source firmware, although there's a Linux/FreeBSD exception I haven't noticed before:

> [COLOR=#000000]**2.1.2**[FONT=Trebuchet MS] Linux/FreeBSD Exception. Notwithstanding the foregoing terms of Section 2.1.1, SOFTWARE designed exclusively for use on the Linux or FreeBSD operating systems, or other operating systems derived from the source code to these operating systems, may be copied and redistributed, provided that the binary files thereof are not modified in any way (except for unzipping of compressed files).[/FONT]
[/COLOR]


Arguably this makes it legal, I have to concede that. However, the License still requires acceptance by any intermediate or end-users. So, when downloading the nvidia installer from nvidia users agree to those terms before downloading and again when installing. That's fine and exactly the same as in Windows.
Where many Linux distros fail, Ubuntu included, is in not presenting the same license but at least Ubuntu isn't redistributing the blob thingy in its official installation media.

---

