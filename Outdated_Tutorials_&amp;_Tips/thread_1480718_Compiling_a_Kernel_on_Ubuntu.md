---
title: "Compiling a Kernel on Ubuntu"
date: 2010-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by zkriesse on 2010-05-11
[SIZE="2"][COLOR="Blue"]**=== Compile A Kernel ===**
[/COLOR][/SIZE]

The first thing to understand is that each and every OS distribution has a set of very specific tools that can be used to build a custom kernel from the sources available. This article is about compiling a kernel on the Ubuntu System(s). What the author shall attempt to describe for you is information on how to build a custom kernel using the latest unmodified kernel sources from [[COLOR="Blue"][SIZE="2"]**Kernel.org**[/SIZE][/COLOR]]("http://www.kernel.org") and [[COLOR="Blue"][SIZE="2"]**Vanilla Kernel**[/SIZE][/COLOR]]("http://en.wikipedia.org/wiki/Vanilla_kernel#Versions"). This way you are completely independent from the kernels already supplied by your specific distribution. It will also show you how to patch the kernel sources if you have need of certain features that are not currently there. This has been tested on the Ubuntu 6.06 Desktop Edition and the Ubuntu 6.10 Server Edition. Now this is not the one and only way to set up a system such as this. There are multiple ways of achieving such a goal but this one of those ways we have chosen to document. [B][COLOR="Red"]
WARNING: There is no solid guarantee that this process will work for you.[/COLOR][/B]
 
[SIZE="2"][COLOR="Blue"]**=== Preliminary Note ===**
[/COLOR][/SIZE]> Although it's never a good idea to operate the Ubuntu System as the Root or SuperUser, the steps listed here can be accomplished via a root user which if you haven't yet created, you can do it via the following commands in your terminal. Alright. The first command if you wish to run the system as root is as follows.

```

$ sudo passwd root

```

After you have run that command, you can login as the root user via this command.

```

$ su root

```

If you prefer to run the system as the normal user (Which is preferred by us that you do so!)instead of running it as root, remember to put [SIZE="2"][COLOR="Red"]**"sudo"**[/COLOR][/SIZE] in front of any commands shown here in this how-to. For example, when you run,

```

$ apt-get update

``` 
You should instead run this,
 
```

sudo apt-get update

```

[SIZE="2"][COLOR="blue"]**=== /bin/sh on Ubuntu 6.10 Server Edition ===**
[/COLOR][/SIZE]
On Ubuntu 6.10 Server Edition, **/bin/sh** is a symlink to **/bin/dash** by default. **/bin/dash** seems to cause problems when you attempt to compile software from the sources. At least, that was the impression given at the time, which is why **/bin/sh** is a symlink to **/bin/dash** instead. If you are currently using Ubuntu 6.10 Server Edition, please enter the following command before proceeding further.

```

$ rm -f /bin/sh
$ ln -s /bin/bash /bin/sh

```

[SIZE="2"][COLOR="Blue"][B]=== Installation of Required Packages for Kernel Compilation ===
[/B][/COLOR][/SIZE]The first step is to update the database containing the current packages.

```

$ sudo apt-get update

```

And then,

```

$ apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

```

[SIZE="2"][COLOR="blue"][B]=== Downloading Kernel Sources ===
[/B][/COLOR][/SIZE]Now to download the desired kernel to **/usr/src**. Also, go to [[SIZE="2"][COLOR="blue"]**Kernel.Org**[/COLOR][/SIZE]]("http://www.kernel.org") to select the kernel that you wish to install, for example, **linux-2.6.18.1.tar.bz2** (all 2.6 kernel versions can be found here at: [[SIZE="2"][COLOR="blue"]**Kernel.org/Kernel Versions**[/COLOR][/SIZE]]("http://www.kernel.org/pub/linux/kernel/v2.6/")) After you have selected the kernel of your choice you can download it to **/usr/src** with the following command.

```

$ cd /usr/src

``` 

Then,

```

$ wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.1.tar.bz2

```

After you have done that, you can unpack the kernel's source(s) and create a symlink to the kernel's source(s) directory with this command.

```

$ tar xjf linux-2.6.18.1.tar.bz2

```

Then,

```

$ ln -s linux-2.6.18.1 linux

```

And finally,

```

$ cd /usr/src/linux 

```

[COLOR="Blue"][SIZE="2"][B]=== Applying Patches to the Kernel Source(s) (Optional) ===
[/B][/SIZE][/COLOR]Well, as you may have guessed, sometimes you may have need of certain drivers for hardware which isn't supported by the current kernel, and you may need support virtualization techniques, or some other cutting edge technology that has not yet made it to the current kernel version. In all these different scenarios you have to patch the kernel's source(s) providing that there is a current patch already made available. 

Now, we're going to assume that you have already downloaded the needed patch (In this example the **patch** will be called **patch.bz2**) to **/usr/src**. The following code will show you how to apply it to your kernel's source(s). **NOTE: Keep in mind you must be in the [COLOR="Red"]/usr/src/linux[/COLOR] directory for this step.**

```

$ bzip2 -dc /usr/src/patch.bz2 | patch -p1 --dry-run
$ bzip2 -dc /usr/src/patch.bz2 | patch -p1

```

Now, the first command was simply just a test, it does nothing to your sources file. If it doesn't come back and report any errors, you can then run the second command which will in fact apply the downloaded patch. [COLOR="Red"]**WARNING: Do not run the second command if the previous command reported errors!**[/COLOR] Now, you also have the ability to apply kernel prepatches to your kernel's source(s). For example, if you have need of a certain feature that is available only for kernel version 2.6.18.1 or 2.6.18.2, and etc. An explanation of this can be found at [B][SIZE="2"][COLOR="Blue"][Kernel.org/Patchtypes]("http://kernel.org/patchtypes/pre.htm")
[/COLOR][/SIZE][/B]

[SIZE="2"][COLOR="blue"][B]=== Prepatch Explanation ===
[/B][/COLOR][/SIZE]**[SIZE="2"][COLOR="blue"]TIP: Prepatches are the equivalent to an alpha release of Linux, as they reside in the testing directories which are in the archives. The patches should be applied using the patch(1) utility available to the source code of the previous full release which has a 3-stage or 3-part version number. An example of this is the 2.6.12-rc4 prepatch that should be applied to the 2.6.11 kernel source(s), not 2.6.11.10.[/COLOR][/SIZE]** So, if you want to compile a 2.6.19-rc4 kernel, first you must download the 2.6.18 kernel source(s) from [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.18.tar.bz2) in step 3 instead of kernel version 2.6.18.1!

[B][SIZE="2"][COLOR="blue"]=== Applying the kernel Patch ===
[/COLOR][/SIZE][/B]To apply the 2.6.19-rc4 kernel patch to kernel 2.6.18, you will need to do the following.

```

$ cd /usr/src
$ wget http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.19-rc4.bz2
$ cd /usr/src/linux
$ bzip2 -dc /usr/src/patch-2.6.19-rc4.bz2 | patch -p1 --dry-run
$ bzip2 -dc /usr/src/patch-2.6.19-rc4.bz2 | patch -p1 

```

[SIZE="2"]**[COLOR="Blue"]=== Configuring The Kernel ===[/COLOR]**
[/SIZE]**TIP: Now it's usually a good idea to use the configuration of your current kernel as the base for your new kernel configuration. To do this we shall copy the existing configuration to [SIZE="2"]/usr/src/linux:[/SIZE] with the following commands.**

```

$ cp /boot/config-`uname -r` ./.config 

```

Then you should run this.

```

$ make menuconfig

```

The above code will bring up the kernel configuration menu. Scroll down with the arrow key until you hit **Load an Alternate Configuration File** and choose 
**.config** (.config will contain the current configuration of your current kernel) as the configuration file.



[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/1.png?direct[/IMG]

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/2.png?direct[/IMG]

After that, browse through the kernel configuration menu and make the choice(s) of your preference. 
When you finish, select **Exit** and answer the following question
**Do you wish to save your new kernel configuration?** with **Yes:**

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/3.png?direct[/IMG]

[B][SIZE="2"][COLOR="Blue"]=== Building the Kernel ===
[/COLOR][/SIZE][/B]To build the kernel, execute the following two commands.

```

$ make-kpkg clean
$ fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 

```

**IMPORTANT NOTE: After [SIZE="2"]--append-to-version=[/SIZE] you can write any string that will help you identify the kernel, but it [SIZE="2"][COLOR="red"]MUST[/COLOR][/SIZE] begin with a minus (-) sign and must [COLOR="Red"][SIZE="2"]NOT [/SIZE][/COLOR]contain any whitespace. Now, if you're getting frustrated, be patient. The kernel can take a long amount of time, so depending upon your kernel configuration and your processor speed it could either be a matter of a few minutes, or it could be hours.**

[B][SIZE="2"][COLOR="Blue"]====== Installation of the New Kernel ===
[/COLOR][/SIZE][/B]After the successful initial kernel build, you should find two .deb packages in the **/usr/src** directory using this command.

```

$ cd /usr/src
$ ls -l

``` 

On the test system the two .deb files were called **linux-image-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb** (The first .deb file contains the actual kernel.) and **linux-headers-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb** (This second .deb file contains certain files that are needed if you would like to compile additional kernel modules at a later date.) To install the two .deb files, use the following commands.

```

$ dpkg -i linux-image-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb
$ dpkg -i linux-headers-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb

```

**Little Tip: You can now transfer the two .deb files to other Ubuntu systems and install them there via the same methods described here in this documentation, which means that you won't have to compile the kernel on the new system.**

[B][SIZE="2"][COLOR="blue"]===== Checking the Kernel =====
[/COLOR][/SIZE][/B]Well, that's it! If you like, you can now check **/boot/grub/menu.lst** and there you should fine two stanzas for your new kernel in that directory via the terminal using this command.

```

$ vi /boot/grub/menu.lst

``` 

The stanzas that were added to the test system should look like these.

```

title           Ubuntu, kernel 2.6.18.1-custom
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.18.1-custom root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.18.1-custom
savedefault
boot

title           Ubuntu, kernel 2.6.18.1-custom (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.18.1-custom root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.18.1-custom
boot

```

Now you need to reboot your system by using the following command.

```

$ shutdown -r now

```

If everything went well, your system should restart with the new kernel. You can check if you're using your new kernel by running the following command.

```

$ uname -r

``` 

It should display something to the affect of, **2.6.18.1-custom** If the system doesn't start, restart it and when you see this,

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/4.png?direct[/IMG]

Press the **ESC** button to enter the **GRUB** menu:

[IMG]http://images.howtoforge.com/images/kernel_compilation_ubuntu/5.png?direct[/IMG]

Select your old kernel and start the system. If you do, you can now re-try compiling a working kernel. [COLOR="Red"]
**IMPORTANT: Don't forget to remove the stanzas of the kernel which doesn't work from the /boot/grub/menu.lst.**[/COLOR]

And that's it! I hope this works for you, and may you get a working kernel compiled.

Source Accreditation:
[HowtoForge-Kernel Compilation on Ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

---

### Post by godspeedmav on 2010-08-05
dude, it's me JoeMaverickSett, your mentee on Ubuntu-Youth. ):P
could you please fix the pictures? (or is it me who cannot see it?)

thanks!;)

---

### Post by zkriesse on 2010-08-06
> dude, it's me JoeMaverickSett, your mentee on Ubuntu-Youth. 
could you please fix the pictures? (or is it me who cannot see it?)

thanks!
What pictures? I didn't post any pics here

---

### Post by MichealH on 2010-08-06
Its me, I'm on Ubuntu Youth XD

I can see there are many pics supposed to be here. I can see there is a error finding pics.

Also, Thanks this will come in handy.

BOOKMARKED.

---

### Post by zkriesse on 2011-01-25
It'll display the pics if I try to edit the post but when I save it well, as you can "not" see, it won't display them....argh..any help admins?

---

