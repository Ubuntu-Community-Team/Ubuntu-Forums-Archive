---
title: "HOWTO: Install Promise sata controllers using source"
date: 2006-02-05
forum: Outdated Tutorials &amp; Tips
---

### Post by keebler411 on 2006-02-05
Disclaimer: This has only been tested using the Promise Sata 300 TX4, kernel 2.6.12.x, and Ubuntu 5.10 using an initramfs image, but I don't see why it wouldn't work for other Promise sata controllers that have GPLd driver code.

Background: The Promise Sata 300 TX4 is a PCI 4-port sata controller (no hardware RAID).  According to [http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html") this controller is supported in sata_promise as of 2005-04-15. Which kernel version this date corresponds to exactly I'm not sure. However, I did try using the latest kernel and was never able to get it working reliably. So I opted to use the available source code.

Step 1: Install the necessary build tools and kernel source for your kernel *VERSION*.

```
apt-get install kernel-source-*VERSION*
apt-get install build-essential
apt-get install kernel-package
apt-get install gcc
apt-get install gcc-3.4
apt-get install libncurses5
apt-get install libncurses5-dev
apt-get install libqt3-mt-dev
cd /usr/src
tar --bzip2 -xvf linux-source-*VERSION*.tar.bz2
mv linux-source-*VERSION *linux-source-*VERSION*-sata
ln -s linux-source-*VERSION*-sata linux
``` 

Step 2: Download the appropriate source code file from Promise for your controller to /usr/src and unpack it. You should end up with a directory called ut_mod.

```
cd /usr/src
tar -xvf *SATADRIVERSOURCEFILE*.tar.gz
``` 

Step 3: Configure and compile the kernel. You don't need to run make menuconfig unless you want to change something because we've copied over an exisiting config file. However, its a good idea to set local version information to say -sata. You will find it under General setup ---> Local version - append to kernel release. 

```
cd /usr/src/linux
make clean
cp /boot/config.*VERSION *.config
make menuconfig (if desired)
make bzImage
make install
make modules
make modules_Install
``` 

Step 4: Compile and install the sata driver.

```
cd /usr/src/ut_mod
make clean
make
mkdir /lib/modules/*VERSION*-sata/scsi
cp ulsata2.ko /lib/modules/*VERSION*-sata/scsi
``` 

Step 5: Generate an initramfs image. PLEASE NOTE: If you don't edit /etc/mkinitramfs/modules and add ulsata2 the driver will still load (assuming automatic kernel module loading is enabled, which it is by default) but later in the boot process rather than sooner. The consequence of this is that you can't use fstab to mount filesystems on any attached sata disks. However you can mount them manually after logging in as root. Also, if you have any external drives that are recognized they may show up before the internal sata attached drives. This is reversed if ulsata2 gets loaded earlier in the boot process (a good thing).

```
cd /etc/mkinitramfs/modules
pico modules

add the following line:
ulsata2

cd /boot
mkinitramfs -o initrd.img-*VERSION*-sata* VERSION-*sata
``` 

Step 6: Configure grub to point to the new kernel.

```
cd /boot/grub
pico menu.lst

add the following lines:
title        Ubuntu, kernel *VERSION*-sata (sata test kernel)
root        (hd0,0)
kernel     /boot/vmlinuz-V*ERSION*-sata root=/dev/hda1 ro quiet splash
initrd       /boot/initrd.img-*VERSION-*sata
boot

``` 

Step 7: Create mount points for your disks. Then add entries to fstab that correspond to your attached sata disks. For example, to mount the first extended ext3 partition on the first attached sata disk:

```
mkdir /mnt/sata1
cd /etc
pico fstab

add the following line(s) customized to your situation:
/dev/sda5    /mnt/sata1   ext3   defaults   0   2
``` 

Step 8: Reboot and enjoy.

keeb

---

### Post by phreaky- on 2006-02-14
I'm trying your tutorial and I'm running into a problem :(

When I try to compile the SATA2 driver I get the following error:

root@pX:/usr/src/ut_mod# make clean

```

cat: /lib/modules/2.6.12-10-386/build//include/linux/version.h: No such file or directory
Makefile:103: ***
Makefile:104: *** Warning: kernel source version (2.6.12-sata)
Makefile:105: *** does not match running kernel  (2.6.12-10-386)
Makefile:106: *** Continuing with build,
Makefile:107: *** resulting driver may not be what you want
Makefile:108: ***
cd cam; make clean
make[1]: Entering directory `/usr/src/ut_mod/cam'
rm -f cam_mod.o cam.o cam_ata.o cam_isr.o cam_swap.o cam_var.o cam_fm.o
make[1]: Leaving directory `/usr/src/ut_mod/cam'
rm -rf ulsata2.o pdc-ulsata2.o include
```

Then I try make and I get:

```
 
whole list of errors...

make: *** [pdc-ulsata2.o] Error 1 
```

What did I do wrong? I'm running  2.6.12-10-386

---

### Post by bonez_15 on 2006-02-17
I'm having the exact same problem as phreaky

```
root@b-served:/usr/src/ut_mod# make
cat: /lib/modules/2.6.12-10-386/build//include/linux/version.h: No such file or directory
Makefile:103: ***
Makefile:104: *** Warning: kernel source version (2.6.12-sata)
Makefile:105: *** does not match running kernel  (2.6.12-10-386)
Makefile:106: *** Continuing with build,
Makefile:107: *** resulting driver may not be what you want
Makefile:108: ***
cd cam; make
make[1]: Entering directory `/usr/src/ut_mod/cam'
gcc -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -O2 -fo mit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-bound ary=2 -march=i386   -c -o cam.o cam.c
gcc -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -O2 -fo mit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-bound ary=2 -march=i386   -c -o cam_ata.o cam_ata.c
gcc -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -O2 -fo mit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-bound ary=2 -march=i386   -c -o cam_isr.o cam_isr.c
gcc -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -O2 -fo mit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-bound ary=2 -march=i386   -c -o cam_swap.o cam_swap.c
gcc -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -O2 -fo mit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-bound ary=2 -march=i386   -c -o cam_var.o cam_var.c
gcc -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -O2 -fo mit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-bound ary=2 -march=i386   -c -o cam_fm.o cam_fm.c
ld -r -o cam_mod.o cam.o cam_ata.o cam_isr.o cam_swap.o cam_var.o cam_fm.o
make[1]: Leaving directory `/usr/src/ut_mod/cam'
gcc -D__KERNEL__ -DMODULE -D__LINUX__ -DEXPORT_SYMTAB -DMODVERSIONS -D_MMIO_ -DS SBOX -DTCQ -DNCQ -I/usr/src/linux/include -I/usr/src/linux -Icam -I/usr/src/linu x/arch/i386/mach-generic -include /usr/src/linux/include/linux/modversions.h -Wa ll -Wstrict-prototypes -O2 -fomit-frame-pointer -fno-strict-aliasing -pipe -mpre ferred-stack-boundary=2 -fno-common -march=i586 -c pdc-ulsata2.c
cc1: error: /usr/src/linux/include/linux/modversions.h: No such file or director y
In file included from pdc-ulsata2.c:32:
/usr/src/linux/include/asm/irq.h:16:25: error: irq_vectors.h: No such file or di rectory
In file included from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/pagemap.h:10,
                 from /usr/src/linux/include/linux/blkdev.h:10,
                 from pdc-ulsata2.c:45:
/usr/src/linux/include/linux/irq.h:72: error: &#8216;NR_IRQS&#8217; undeclared here (not in a function)
In file included from /usr/src/linux/include/linux/irq.h:74,
                 from /usr/src/linux/include/asm/hardirq.h:6,
                 from /usr/src/linux/include/linux/hardirq.h:6,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/asm/highmem.h:24,
                 from /usr/src/linux/include/linux/highmem.h:12,
                 from /usr/src/linux/include/linux/pagemap.h:10,
                 from /usr/src/linux/include/linux/blkdev.h:10,
                 from pdc-ulsata2.c:45:
/usr/src/linux/include/asm/hw_irq.h:28: error: &#8216;NR_IRQ_VECTORS&#8217; undeclared here (not in a function)
pdc-ulsata2.c:46:18: error: scsi.h: No such file or directory
pdc-ulsata2.c:88: error: syntax error before &#8216;*&#8217; token
pdc-ulsata2.c:88: warning: function declaration isn&#8217;t a prototype
pdc-ulsata2.c:238: error: syntax error before &#8216;Scsi_Cmnd&#8217;
pdc-ulsata2.c:239: warning: function declaration isn&#8217;t a prototype
pdc-ulsata2.c: In function &#8216;__unmap_scsi_data&#8217;:

**** lots more *****

pdc-ulsata2.c:3302: warning: data definition has no type or storage class
In file included from pdc-ulsata2.c:3316:
/usr/src/linux/drivers/scsi/scsi_module.c: In function &#8216;init_this_scsi_driver&#8217;:
/usr/src/linux/drivers/scsi/scsi_module.c:19: warning: initialization from incom patible pointer type
/usr/src/linux/drivers/scsi/scsi_module.c: In function &#8216;exit_this_scsi_driver&#8217;:
/usr/src/linux/drivers/scsi/scsi_module.c:54: warning: initialization from incom patible pointer type
{standard input}: Assembler messages:
{standard input}:93: Error: symbol `buff' is already defined
{standard input}:99: Error: symbol `buff' is already defined
{standard input}:105: Error: symbol `buff' is already defined
{standard input}:111: Error: symbol `buff' is already defined
{standard input}:117: Error: symbol `buff' is already defined
{standard input}:123: Error: symbol `buff' is already defined
{standard input}:129: Error: symbol `buff' is already defined
{standard input}:135: Error: symbol `buff' is already defined
{standard input}:141: Error: symbol `buff' is already defined
{standard input}:147: Error: symbol `buff' is already defined
{standard input}:153: Error: symbol `buff' is already defined
{standard input}:159: Error: symbol `buff' is already defined
{standard input}:165: Error: symbol `buff' is already defined
{standard input}:171: Error: symbol `buff' is already defined
{standard input}:177: Error: symbol `buff' is already defined
{standard input}:183: Error: symbol `buff' is already defined
{standard input}:189: Error: symbol `buff' is already defined
{standard input}:195: Error: symbol `buff' is already defined
{standard input}:254: Error: symbol `drv' is already defined
{standard input}:260: Error: symbol `buff' is already defined
make: *** [pdc-ulsata2.o] Error 1


```

It seems that the modversions.h and vectors.h libraries arent available in the compiled kernelsource (linux-source2.6.12 (w. ubuntu patches.. from the src repo) )

I did a search for modversions.h on my system and cant find it anyware .. 

vectors.h is found in 3 directories namely 

/usr/include/asm-i386/mach-default/irq_vectors.h
/usr/include/asm-i386/mach-voyager/irq_vectors.h
/usr/include/asm-i386/mach-visws/irq_vectors.h

i tried copying the library to the /usr/src/linux/include/asm folder (where it couldnt find it in the first place). 
After running the make again the irq_vectors.h library was found but then i got the follow not found error

/usr/src/linux/include/asm/irq_vectors.h:87:32: error: irq_vectors_limits.h: No such file or directory

I also did a search for this file on my system but dint come up with anything.


----------------------------

Any idea why these libraries arent found and what we should do to ge these ?

---

### Post by jimmer on 2006-02-19
Thank you for the HowTo keebler. I am also receiving the same error messages as phreaky and bonez. Any ideas? I saw a post back in December by schedfan who successful compiled the kernel. Any help to get this mass storage controller working would be greatly appreciated. If I can't get this to work, are their any SATA controllers that work without compiling the kernel. I have 4 400GB Seagate SATA 300Gb/s drives. I am building a simple file server to host my family movies, DVDs and Mp3. Thank you

I found this post:
Sunday, 20 November 2005
Promise SATA300 TX4 on Linux (2.6.x)
If you are having problems with Promise SATA300 TX4 on Linux (2.6.x) and don't want to rebuild kernel, get Linux kernel 2.6.14 or later, where Promise SATA300 TX4 is supported out of the box. 

I confirmed by checking the changelog in kernel 2.6.14:

commit 08b791c02b86e25f456cba64f5f1a1f90326db1d
Author: Otto Meier <gf435@gmx.net>
Date:   Mon Aug 22 14:58:57 2005 +0100

    [PATCH] sata_promise: Add PDC40718 id
    
    Otto Meier recently submitted a patch to support the PDC40718 chip (marketed
    as SATA300 TX4, a 4-port SATA controller).
    
    Signed-off-by: Otto Meier <gf435@gmx.net>
    Signed-off-by: Daniel Drake <dsd@gentoo.org>
    Signed-off-by: Jeff Garzik <jgarzik@pobox.com>

Is this an option with Ubuntu? If it is how should I proceed?

---

### Post by jimmer on 2006-02-19
How to Get the Promise SATA300 TX4 to work with Breezy:
To answer my own question. I would need to compile a vanilla kernel. I saw the post by RubenGonc Howto 2.6.14 Vanilla Kernel with ck Patchset. I was really looking for a kernel image already compiled. I am a true linux newbie only at it for the past month or so. Any help would be appreciated. I am going to download and try Dapper Drake Alpha 4. I hear it contains the 2.6.15 kernel which will support my promise card out of the box.

---

### Post by bonez_15 on 2006-02-19
Hey Jimmer. Just the other day i compiled the vanilla kernel and guess what, the card works  :D .

I followed these two howto's

[ 1# kernel compilation for newbs]("http://www.ubuntuforums.org/showthread.php?t=85064")

[2# How to 2.6.14 with ck patchset]("http://www.ubuntuforums.org/showthread.php?t=84174")

Ofcourse the current vanilla kernel is 2.6.15 so get that 

[here ]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.tar.bz2")

and the kolivas patches

[here]("http://members.optusnet.com.au/ckolivas/kernel/")

---------------

Just follow the how to's above  and be sure to do the following when your in the kernel menuconfig (step 4 in kernel compilation for newbs)

Go to scsi support ( i dont know if this is in a section of its own .. i dont remember it beeing so but it could be)
once in scsi support (enable the following - aka put a * in front of it)

scsi support 
scsi disksupport (dunno if this is absolutely neccesary but i did it non the less)
scsi generic support 

then go to scsi low-level drivers 

and search for the promise (TX) series and put a * infront of those

that should do the trick..

for the rest just follow the how-to's above 

-----------------

Hope everything works

Bonez

---

### Post by jimmer on 2006-02-19
Thanks bonez, I'll give it a try. I downloaded Dapper Drake alpha 4. It found the promise card and all my drives right off the bat. I'm going to try your method so I can keep stable Breezy. Thanks for your post.

---

### Post by videoapelsin on 2006-03-23
So, this card will work with Ubuntu? In that case, i'm getting one right away!
I first bought a HighPoint RocketRAID 1520, which obiously don't work at all with Ubuntu.

---

### Post by Winded on 2006-05-28
I found this excellent how to just a couple weeks ago and its been invaluable in getting my Promise SATA 300 TX4 card working with my AMD64 system.  I did a couple things differently that I'd like to document here for everyone else and in case I need to do them again in the future while everything is fresh in my head. :D 

First I went through like Keebler did and installed all the packages you need.  I also downloaded the 64 bit Promise driver for kernel 2.6 from Promise's web site and unpacked that.  All of that was the same.  When it came to compiling though, some things were different.

First, on the command line type in 
```
uname -r
```
and note what it says here.  Then, I went to /usr/src/linux-source-2.6.12-sata and edited the Makefile.  There's a line that looks like 
```
EXTRAVERSION =
```
at the top.  You need to add in all the stuff after '2.6.12' when you executed the command 'uname -r'.  So when I did 'uname -r' I got back '2.6.12-10-amd64-k8-smp'.  So my line looks like:

```
EXTRAVERSION = -10-amd64-k8-smp
```

Yours will probably be different.  Now you can save and exit.  Next, I made the kernel with the commands 
```

make
make modules

```
I don't think 'make bzImage' or 'make modules_install' is necessary.  At least, I didn't do either of these, however, you may need them if you do Step 5 in Keebler's how to.

Now its time to make the actual driver.  This is the fun part.  First, go to /usr/src/ut_mod which is where you should have the driver from Promise's web site.  Edit the Makefile in this directory.  Find the line that says 
```

GENERIC = $(CFLAGS) -fno-common -march=i586

```
and change it to 
```

GENERIC = $(CFLAGS) -fno-common -march=athlon64

```

Now, above this line will be one that looks like
```

CFLAGS += $(MFLAGS) -Wall -Wstrict-prototypes -02 -fomit-frame-pointer \
      -fno-strict-aliasing -pipe -mpreferred-stack-boundary=2

``` 
The -mpreferred-stack-boundary option needs to be set to 4.  Disclaimer: I don't know what mpreferred-stack-boundary does.  I only made a cursory glance on the internet at finding out.  All I know is the compiler complained when it was set to 2 and said it needed to be between 4 and 12.  

So now we have
```

CFLAGS += $(MFLAGS) -Wall -Wstrict-prototypes -02 -fomit-frame-pointer \
      -fno-strict-aliasing -pipe -mpreferred-stack-boundary=4

```

Ah, but we're not done.  Now 'cd cam' and edit the Makefile there.  You're looking for the line that looks like:
```

CFLAGS =  -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -02 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-boundary=2 -march=i386

```
This line needs to be changed to 
```

CFLAGS =  -D__LINUX__ -D_MMIO_ -D_ATAPI_ -DTCQ -DNCQ -Wall -Wstrict-prototypes -02 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -mpreferred-stack-boundary=4 -march=athlon64

```

Now you should be able to cd back one directory and type 'make'.  When I did this, I initially got an error.  The compiler said it was unable to find modversions.h.  A little searching and I found that that file is in the kernel headers.  I did 
```

apt-get install kernel-headers-2.6.12-10

```
and copied that file over to the proper place (where the make file was looking for it) and everything went fine after that.  I did 'rmmod sata_promise' and then 'insmod ulsata2.ko' like the README says and it looks like its working great.  Hope this helps someone.

---

### Post by thor918 on 2006-11-12
hi there.
I got draper 2.6.15-23-server, and the card is working out of the box, as someone stated here.
one problem:
I don't like that the card gets priority over the onboard ports.
My motherboard's two sata ports are connected to hd's detected as sda and sdb.

when port1 on the promise card is used, it will be detected as sda.
is there something one could do to provoke what hd's are detected as?(not by changing cable order)
like this:
onboard sata:
 sda
 sdb
promise sata:
 sdc
 sdd
 sd...

by the way don't linux support hotswap?
My chieftec sata hotswap box works by restarting pc, but won't autodetect while pc is running...

---

### Post by thor918 on 2007-01-29
got to add 
I switched to using UUID in fstab insted of /dev/sd*
the mountpoints will be good even if a new drive pops up...

but still. how is the hotswap support going.
even being able to run a command to detect changes would be greate. 
but that probably exists allready.

---

### Post by thor918 on 2007-01-30
> **bonez_15 said:**
> Hey Jimmer. Just the other day i compiled the vanilla kernel and guess what, the card works  :D .

I followed these two howto's

[ 1# kernel compilation for newbs]("http://www.ubuntuforums.org/showthread.php?t=85064")

[2# How to 2.6.14 with ck patchset]("http://www.ubuntuforums.org/showthread.php?t=84174")

Ofcourse the current vanilla kernel is 2.6.15 so get that 

[here ]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.tar.bz2")

and the kolivas patches

[here]("http://members.optusnet.com.au/ckolivas/kernel/")

---------------

Just follow the how to's above  and be sure to do the following when your in the kernel menuconfig (step 4 in kernel compilation for newbs)

Go to scsi support ( i dont know if this is in a section of its own .. i dont remember it beeing so but it could be)
once in scsi support (enable the following - aka put a * in front of it)

scsi support 
scsi disksupport (dunno if this is absolutely neccesary but i did it non the less)
scsi generic support 

then go to scsi low-level drivers 

and search for the promise (TX) series and put a * infront of those

that should do the trick..

for the rest just follow the how-to's above 

-----------------

Hope everything works

Bonez


I did a compile from 2.6.18.1, and that do not have the promise in the scsi low-level driver list. is it included in the kolivas patches?


edit.
aha. theres a new category called  sata(production) and paralell ata (experimental) drivers
promise driver is listed there now

---

### Post by empirico on 2008-11-25
Hi: 
I do what you did but I have a problem. I´m using Ubuntu 8.10 server with kernel 2.6.27-7-server and when I try to do the make of the promise sata drivers I get the next error: 
root@server:/usr/src/pdc-ulsata2# make
Makefile:57: *** Linux kernel source not configured - missing config.h.  Stop.

¿Can anyone help me please?

Sorry for my bad english but I´m from Spain and I don´t practice much the english. 

Thank you very much

---

### Post by supersobbie on 2009-02-17
empirico, Same Problem Here!!!  From my understanding this card was suppose to be supported outta the box but it wasnt for me.  So I tried to install from source and have run into the same problem.  Everything else seemed to work fine but compiling the promise drives fails with same exact error.

Any help would be GREAT.

Thanks,
SoBBie

---

