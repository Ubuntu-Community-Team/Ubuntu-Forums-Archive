---
title: "HOWTO: Kernel Compilation for Newbies"
date: 2005-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-11-01
[COLOR="Red"]**[SIZE="3"]DAPPER USERS, please follow this guide:[/SIZE]**[/COLOR]
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)


[COLOR="Red"]**[B]THIS GUIDE IS FOR BREEZY**[/B][/COLOR]

This guide is aimed at the newbies who are willing to learn something about kernel compilation or just who need a new kernel for incompatibility issues (e.g. DMA issues). This is a STEP-BY-STEP guide, so don't be afraid of compiling your first kernel, it's a piece of cake. Moreover if you need to [COLOR="Blue"]compile any kernel module[/COLOR] (nvidia modules, ndiswrapper, etc.) I will also explain how to do it.

It takes a while (even an hour) to complete the process described below, so make sure you have enough time to spend.

Make sure you have all the repositories enabled

[COLOR="Magenta"]BEFORE YOU START[/COLOR]

If you have an Nvidia or ATI graphic card and you are using a proprietary driver (i.e. if you have installed the graphic driver before) please do this, otherwise get straight to step 1:

Open Terminal or Konsole and type these commands:

(if you are using GNOME, the graphic interface that comes with Ubuntu)
sudo gedit /etc/X11/xorg.conf

Otherwise

(if you are using KDE, the graphic interface that comes with Kubuntu)
sudo kate /etc/X11/xorg.conf

Scroll down the text until you find this section (this is my configuration):

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
Driver "[COLOR="Red"]ati[/COLOR]"
BusID "PCI:1:5:0"

Substitute the word in red with “vesa” or “nv” (NVIDIA's opensource driver) or “ati” (ATI's opensource driver), make it look like this:
Section "Device"
Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
Driver "[COLOR="Blue"]vesa[/COLOR]"
BusID "PCI:1:5:0"

Save and exit. Restart the computer and go to the next step. 

When you have the new kernel working you might want to reinstall the proprietary drivers for your graphic card. Have a look at my guide for the NVIDIA drivers: use method 2 if you want to install them manually OR compile the module with your kernel (as described below) and follow method 1 in my guide.

1) Open Terminal or Konsole and type these commands

uname -r (so as to see what kernel you are using)

[COLOR="Red"]NOTE: if you want to compile a vanilla kernel from kernel.org have a look at the end of the guide.Otherwise proceed with step 2.
[/COLOR]
2) 
[COLOR="Red"]IF YOU USE UBUNTU BREEZY or HOARY[/COLOR]:
sudo apt-get install linux-tree (this will download Ubuntu kernel sources and patches for kernel 2.6.12)
[COLOR="Red"]
IF YOU USE DAPPER[/COLOR]:

sudo apt-get install linux-tree

3) Open Terminal or Konsole (if it's not open yet) and type these commands:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc [COLOR="#ff0000"](this will install gcc-4.0 for kernel 2.6.13 or superior)[/COLOR]
sudo apt-get install gcc-3.4
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev
sudo apt-get install bin86
sudo passwd root
(and set the root password which you will need later)

cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cd /usr/src/linux

[COLOR="#ff0000"]NOTE: if the computer says "file exists" when you try type this command "sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux", you have to type "sudo rm /usr/src/linux" (this will remove the old link). Now you wont' have this error and the command "sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux" will work.[/COLOR]


sudo make oldconfig (so as not to compile the entire kernel from scratch)

If it makes you any questions just press Enter (so as to select the recommended answer)

sudo make menuconfig

4) Now you have to use the keyboard to move the cursor over the function or submenu you want and press Enter to select it.

Select the 4th option: Processor type and features

If you have a multiprocessor system you might want to enable "Symmetric multi-processing support" (SMP): select it with your keyboard and press the spacebar to enable it (a "*" will appear beside it). If you don't have it don't enable it.

Select Processor Family and choose the right one (i386 in my case) depending on the output of the command “uname -r” you have used before

Press the right arrow and select exit

If you have more than 900MB RAM then you'll definitely need this, otherwise (or if you are using Ubuntu 64 bit) skip this step: 
Scroll down the text until you find “High Memory Support”.
Select it.
You'll have three possible choices:
Off
4GB (if you have no more than 4GB RAM)
64GB (if you have more than 4GB RAM)
Select one of these functions and press enter.
Press the right arrow and select exit

The following operation is required if you want to enable DMA directly in your kernel. You might want to try this if none of the methods found in this forum works for you, Otherwise skip it and go to Step 5.
NOTE: if you have old hardware which doesn't support DMA you won't be able to access this hardware with your new kernel. If this happens go straight to Step 8. 

Select Device drivers

then

Select ATA/ATAPI/MFM/RLL support

Scroll down the text until you find (and highlight with the keyboard) “Enable DMA only for disks” and disable it by pressing N (now the “*” beside it should disappear, this means it is not selected any more)

Press the right arrow and select exit

5) Keep on selecting Exit until it asks you whether you want to save your new configuration or not. Answer yes.

Now you are back to the command line, type:

6) su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC


7)[COLOR="#ff0000"] DO THIS ONLY IF YOU NEED SOME RESTRICTED MODULE otherwise go to Point 8[/COLOR]

There will be no restricted modules for the kernel you are going to compile. However if you need them you can pick the modules you need and compile them together with your kernel.

Get the source package/s (from Ubuntu's repositories or from the web) and extract it under /usr/src

For example if you need ndiswrapper and or the nvidia drivers:

sudo apt-get install ndiswrapper-utils

sudo apt-get install ndiswrapper-source

sudo apt-get install nvidia-kernel-source
OR
sudo apt-get install nvidia-legacy-kernel-source [COLOR="#ff0000"](if you have a  old card which belongs to the list in the “Nvidia Legacy Cards” section at the end of the guide)[/COLOR]

[If you have got the package from the web (and not from the repositories) extract the file wherever you want and then type: sudo mv /path_to_the_folder_of_the_extracted_file /usr/src ]


cd /usr/src/

sudo tar --bzip2 -xvf ndiswrapper-source.tar.bz2

sudo tar -xvf nvidia-kernel-source.tar.gz
[COLOR="#ff0000"]OR[/COLOR]
sudo tar -xvf nvidia-legacy-kernel-source.tar.gz(if you have a  old card which belongs to the list in the “Notes section” at the end of the guide)

Repeat the commands you've just typed for any other module you want to add (you can add as many modules as you need) 

When you have finished to extract any other additional module you have to type the following command in order to compile your kernel image, headers and modules.

cd /usr/src/linux

sudo make-kpkg clean

sudo make-kpkg --initrd --append-to-version=-[COLOR="Red"]custom[/COLOR] kernel_image kernel_headers modules_image

[COLOR="#ff0000"]NOTE: you can put whatever you want instead of “custom”[/COLOR]

8 )[COLOR="#ff0000"] If you have followed point 7, skip this step and proceed to step 9[/COLOR]
cd /usr/src/linux

sudo make-kpkg clean

sudo make-kpkg --initrd --append-to-version=-[COLOR="#ff0000"]custom[/COLOR] kernel_image kernel_headers

[COLOR="#ff0000"]NOTE: you can put whatever you want instead of “custom”[/COLOR]

[COLOR="#ff0000"]e.g. sudo make-kpkg --initrd –-append-to-version=-alberto kernel_image kernel_headers[/COLOR]


The system will ask you this question:

“By default, I assume you know what you are doing, and I
apologize for being so annoying. Should I abort[Ny]?”

Answer no by either typing N and then pressing Enter, or just by pressing Enter (as N is the recommended answer)

Well now you'll have to wait at least 45min. The process will use 100% of your CPU so try to leave your computer alone, go have a tea or something else just to keep you away from your computer for a while.

9) After the (long) process type this in the command line (Terminal or Konsole)

cd /usr/src

ls

You'll see a list of the names of the files in the folder as well as the names of your new kernel image , kernel headers (and modules if you have followed Point 7); they should look (approximately)like these ones:

kernel-image-2.6.12-custom_10.00.Custom_i386.deb
kernel-headers-2.6.12-custom_10.00.Custom_i386.deb

(you will also see the modules like the ones below if you have followed Point 7)
ndiswrapper-modules-2.6.12-custom_1.1-4ubuntu2+10.00.Custom_i386.deb
nvidia-kernel-2.6.12-custom_1.0.7667-0ubuntu3+10.00.Custom_i386.deb

Now install them by typing these commands (change the name of the files according to the ones you have seen after the output of the command “ls”):

sudo dpkg -i kernel-image-2.6.12-custom_10.00.Custom_i386.deb

sudo dpkg -i kernel-headers-2.6.12-custom_10.00.Custom_i386.deb

sudo dpkg -i name_of_the_module [COLOR="#ff0000"](only if you have followed point 7)[/COLOR] [COLOR="#ff0000"](there might be several modules so you have to use this command for every module you have compiled)[/COLOR]
e.g. 
sudo dpkg -i ndiswrapper-modules-2.6.12-custom_1.1-4ubuntu2+10.00.Custom_i386.deb
sudo dpkg -i nvidia-kernel-2.6.12-custom_1.0.7667-0ubuntu3+10.00.Custom_i386.deb

[COLOR="#ff0000"]REMEMBER NOT TO UNINSTALL your previous kernel (just in case anything goes wrong)[/COLOR] [COLOR="#ff0000"](i.e. don't do anything else apart from following the instructions)[/COLOR]

10) Ok, now it's time to see if they work.

Restart your computer.

Then if you want to see if DMA is active (if you have enabled it in the kernel as described before) type (in Terminal or Konsole):

sudo hdparm -d /dev/hda (to check if your harddisk has DMA enabled)
sudo hdparm -d /dev/cdrom (to check if your cd-reader has DMA enabled)

Don't you worry if it gives you an error as output but the performance of your harddisk and cdreader have improved (try to transfer a file from a CD to your harddisk and see if it the system slows down).

If everything is ok, then Congratulations you have compiled your first kernel successfully!

11 ) If anything went wrong (I don't know a reason for which it would) you could switch back to your previous kernel: while your computer is booting press "ESC" repeatedly while your computer is booting until GRUB menu appears and you can choose kernel 2.6.12 again (using your keyboard arrows). Once you enter Ubuntu type these commands in order to uninstall the new kernel (remember to put the name of the kernel you have created)

follow this example and put the name of the kernel you have created instead of “custom”

sudo dpkg -r kernel-image-2.6.12-custom

sudo dpkg -r kernel-headers-2.6.12-custom

(in my case, sudo dpkg -r kernel-image-2.6.12-alberto)

NOTE you DON'T have to type the full name of the file .deb which you created

e.g. put “kernel-image-2.6.12-custom” instead of “kernel-image-2.6.12-custom_10.00.Custom_i386.deb”

And restart your computer.

Enjoy!

Alberto

--------------------------------------------------------------------------

[COLOR="Magenta"]NOTE: HOWTO compile from a vanilla kernel from kernel.org
[/COLOR]
If you want to compile from a vanilla kernel from kernel.org something need to be changed in my guide:

Skip [COLOR="Lime"]Point 2[/COLOR]
You have to download it from [www.kernel.org](www.kernel.org) (try the latest stable kernel source)

When you get to [COLOR="#00ff00"]Point 3[/COLOR] of the guide and you get to the following lines you have to modify them in this way:

cd /home/your_username_folder/directory_where_you_put_the_downloaded_kernel (instead of cd /usr/src) (e.g. "cd /home/alberto/download" in my case)
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2 /usr/src (use the name of the file you downloaded)
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux (use the name of the file you downloaded)
cd /usr/src/linux

OPTIONAL PATCH (if you don't need it you can continue with the instructions of Point 3)

At this point if you want to patch your vanilla kernel you have to:

1)Download the patch (I recommend you Kolivas' patches: go to [http://ck.kolivas.org/patches/2.6/]("http://ck.kolivas.org/patches/2.6/")  and choose the folder with the name which matches your kernel version (e.g. if you are going to compile "kernel 2.6.14" get to [http://ck.kolivas.org/patches/2.6/2.6.14/](http://ck.kolivas.org/patches/2.6/2.6.14/)). You will see other folders with different versions of the patch: I suggest you to select the latest version (2.6.14-ck3 in this case). Then you have to choose the file "patch-2.6.14-ck3.bz2" if you have a desktop computer (or laptop) or "patch-2.6.14-ck[COLOR="Red"]s[/COLOR]3.bz2" if you have a server.

NOTE about KOLIVAS patch: if you want to use Kolivas patches you have to download the 1st stable version of a series of kernels and apply the latest patch to it. I'd better explain it with an example: if you are interested in 2.6.14.x series you have to download the source of 2.6.14 (NOT of 2.6.14.4 or 2.6.14.3, etc.) and to apply the latest Kolivas patch (as it will include the patches which make the difference between e.g. version 2.6.14 and 2.6.14.4)

2)cd /usr/src/linux

3)sudo bzcat /home/your_user_name/folder_in_which_you_downloaded_the_file/patch-2.6.14-ck3.bz2 | patch -p1
(put the name of the file you have downloaded instead of the word I have put in red)

And in [COLOR="#00ff00"]Point 4[/COLOR] [COLOR="Red"](this is the 1st thing to do at the beginning of point 4)[/COLOR]:

Get to "File Systems".

Select your filesystem (ext3, reiserfs, etc.) with the cursor.( ext3 is the filesystem used by Ubuntu by default, so if you chose automatic partitioning when you installed Ubuntu Hoary then "ext3" is definitely your filesystem)

Then press the spacebar on the desired filesystem (a "*" will appear beside it). (Make sure there's a "*" beside it instead of a "M". In this way the support for you filesystem will be built directly in the kernel instead of being built as a module and you will not get a "kernel panic")

For example:
select "ext3 journalling filesystem support" and press the spacebar (a "*" will appear beside it).

Press the right arrow and select exit.

Then you can go on with the instructions of Point 4.

If you want to compile a kernel 2.6.13 or higher you have to skip Point 6.

The rest of the HOWTO is ok.

--------------------------------------------------------------------------

[COLOR="Magenta"]NVIDIA LEGACY CARDS[/COLOR]

Below are the legacy GPUs that are no longer supported in the unified driver.
These GPUs will continue to be maintained through the special legacy NVIDIA
GPU driver releases.

NVIDIA chip name Device PCI ID
------------------------------- -------------------------------
RIVA TNT 0x0020
RIVA TNT2/TNT2 Pro 0x0028
RIVA TNT2 Ultra 0x0029
Vanta/Vanta LT 0x002C
RIVA TNT2 Model 64/Model 64 Pro 0x002D
Aladdin TNT2 0x00A0
GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153

---

### Post by IronWolve on 2005-11-04
I tell you, this is horrible. It either locks the system, or says "no screen"...

Why is it so damn hard to get a nvidia 7800 to work in ubuntu... (Dell 9100, dual core 2.8ghz, 1920x1200 native lcd resolution)... I dont even need acceleration, just native resolution, but vesa wont support that. 

(nv driver locks system too)

Any ideas? :confused:

---

### Post by tseliot on 2005-11-04
[QUOTE=IronWolve]I tell you, this is horrible. It either locks the system, or says "no screen"...

Why is it so damn hard to get a nvidia 7800 to work in ubuntu... (Dell 9100, dual core 2.8ghz, 1920x1200 native lcd resolution)... I dont even need acceleration, just native resolution, but vesa wont support that. 

(nv driver locks system too)

Any ideas? :confused:[/QUOTE]
You should use nvidia driver 7676, I think the problem is the "nv" (the open source driver) in xorg, which perhaps doesn't support your graphic card yet. The nv driver was buggy for one of my cards (GeForce 6200 TC PCI-E).

If you have compiled the modules using this guide you are trying to use driver 7667. It probably won't work for you.

1) Set the driver to vesa (it doesn't matter if it doesn't support the resolution you need, it's only a way to use the graphical interface)

2) Try my guide (HOWTO: Latest NVIDIA drivers) (use method2) and use drivers 7676 (FOLLOW EVERY STEP)

3) Post any kind of problems you have in this other thread of mine: [http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

---

### Post by phanboy_iv on 2005-11-07
Um...I'm trying to install a 2.6.14 from kernel.org.
Everything works until I get to step #7. When I type "sudo make-kpkg clean",

I get

> sudo: make-kpkg: command not found

This is probably a simple problem:That's why it's so annoying that I don't know how to fix it. 
I installed all the packages that this guide listed, and followed it closely. 
I probably shouldn't even be doing kernel compilation if I can't solve this problem myself.

Oh, well, I don't care. This is interesting. I'm gonna do it. Asking people for help and experimenting is the 
only way to learn.

Help would be appreciated.

---

### Post by slimb on 2005-11-07
[QUOTE=phanboy_iv]Um...I'm trying to install a 2.6.14 from kernel.org.
Everything works until I get to step #7. When I type "sudo make-kpkg clean",
[/quote]

make kpkg is part of "kernel-package" installed in the early steps.  you may want to make sure you have that installed properly (do another apt-get install kernel-package) and you should be set.

---

### Post by phanboy_iv on 2005-11-07
[QUOTE=slimb]make kpkg is part of "kernel-package" installed in the early steps.  you may want to make sure you have that installed properly (do another apt-get install kernel-package) and you should be set.[/QUOTE]

I KNEW it was something simple I shoulda known.
Thanks much.
Now, let's try this again......

---

### Post by eraclito on 2005-11-07
[QUOTE=tseliot]
Now you are back to the command line, type:

6) su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
[/QUOTE]

what is this?
i never did it, and i wonder what it does...

and what about Kolivas' patches? on the url you gave there no info...

eraclito

---

### Post by tseliot on 2005-11-07
[QUOTE=eraclito]what is this?
i never did it, and i wonder what it does...

and what about Kolivas' patches? on the url you gave there no info...

eraclito[/QUOTE]
Sometimes exporting the compiler you want to use (gcc-3.4 or 4.0) doesn't work if you do it with the "sudo" command. For this reasons you will use "su" according to the steps described above (it won't damage or modify your system in any way).

About Kolivas' patches: get to the folder with a name which matches your kernel version (e.g. if you are going to compile "kernel 2.6.14" get to [http://ck.kolivas.org/patches/2.6/2.6.14/](http://ck.kolivas.org/patches/2.6/2.6.14/)). You will see other folders with different versions of the patch: I suggest you to select the latest version (2.6.14-ck3 in this case). Then you have to choose the file "patch-2.6.14-ck3.bz2" if you have a desktop computer (or laptop) or "patch-2.6.14-ck[COLOR="Red"]s[/COLOR]3.bz2" if you have a server.

Ok, I will add this to the guide, thanks for the feedback.

---

### Post by eraclito on 2005-11-07
[QUOTE=tseliot]
About Kolivas' patches: get to the folder with a name which matches your kernel version (e.g. if you are going to compile "kernel 2.6.14" get to [http://ck.kolivas.org/patches/2.6/2.6.14/](http://ck.kolivas.org/patches/2.6/2.6.14/)). You will see other folders with different versions of the patch: I suggest you to select the latest version (2.6.14-ck3 in this case). Then you have to choose the file "patch-2.6.14-ck3.bz2" if you have a desktop computer (or laptop) or "patch-2.6.14-ck[COLOR="Red"]s[/COLOR]3.bz2" if you have a server.
[/QUOTE]

thanks, but i was asking what the patches can do, why i have to use them (sorry but i want undertend what i do, to improve my linux knowledge...)

 eraclito

---

### Post by Drifter on 2005-11-08
tseliot, when I get to step 8 and type: sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
I get these errors:kernel/sched.c:1231: error: redefinition of ‘cache_delay’
kernel/sched.c:1211: error: previous definition of ‘cache_delay’ was here
kernel/sched.c:1238: error: redefinition of ‘preempt’
kernel/sched.c:1218: error: previous definition of ‘preempt’ was here
{standard input}: Assembler messages:
{standard input}:524: Error: symbol `cache_delay' is already defined
make[2]: *** [kernel/sched.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2

what am I doing wrong I can never get past this step.

---

### Post by tseliot on 2005-11-08
[QUOTE=eraclito]thanks, but i was asking what the patches can do, why i have to use them (sorry but i want undertend what i do, to improve my linux knowledge...)

 eraclito[/QUOTE]
You can have a look at Kolivas' webpage: [http://members.optusnet.com.au/ckolivas/kernel/]("http://members.optusnet.com.au/ckolivas/kernel/")

---

### Post by tseliot on 2005-11-08
> **Drifter]tseliot, when I get to step 8 and type: sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
I get these errors:kernel/sched.c:1231: error: redefinition of &#8216 said:**
> : *** [kernel/sched.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
make: *** [stamp-build] Error 2

what am I doing wrong I can never get past this step.

I haven't tried all the patches Kolivas has made (and I'm terribly busy right now) but I ask you to delete the directory (type sudo rm /usr/src/linux-2.6.14cK1) and try another patch (ck3) because it might work better. I will test it myself as soon as I have some free time (I have complete my thesis during this week)

---

### Post by Drifter on 2005-11-08
[QUOTE=tseliot]I haven't tried all the patches Kolivas has made (and I'm terribly busy right now) but I ask you to delete the directory (type sudo rm /usr/src/linux-2.6.14cK1) and try another patch (ck3) because it might work better. I will test it myself as soon as I have some free time (I have complete my thesis during this week)[/QUOTE]

It tells me no such file or directory when I type sudo rm /usr/src/linux-2.6.14ck1
sorry to bother u just let me know when u have time and thanks.

---

### Post by tseliot on 2005-11-08
[QUOTE=Drifter]It tells me no such file or directory when I type sudo rm /usr/src/linux-2.6.14ck1
sorry to bother u just let me know when u have time and thanks.[/QUOTE]

Forgive me, my mind is a mess in these days. The right command is:

sudo rm [COLOR="Red"]-r[/COLOR] /usr/src/linux-2.6.14ck1

---

### Post by Drifter on 2005-11-08
[QUOTE=tseliot]Forgive me, my mind is a mess in these days. The right command is:

sudo rm [COLOR="Red"]-r[/COLOR] /usr/src/linux-2.6.14ck1[/QUOTE]

It now says this:  

rm: cannot remove `/usr/src/linux-2.6.14ck1': No such file or directory

---

### Post by i3dmaster on 2005-11-08
Great Howto, thanks very much!

---

### Post by joysarba on 2005-11-09
Hi tseliot,

I tried the steps but something seems to have gone awry
> uname -r
    2.6.12-9-386
> sudo apt-get install linux-tree
    Reading package lists...  Done
    Building dependency tree... Done
    E: Couldn't find package linux-tree

I got the same error for 
> sudo apt-get install kernel-package
> sudo apt-get install gcc-3.4
> sudo apt-get install libncurses5-dev

Have been at it for the last couple of hours but no luck....

---

### Post by tseliot on 2005-11-09
[QUOTE=joysarba]Hi tseliot,

I tried the steps but something seems to have gone awry
> uname -r
    2.6.12-9-386
> sudo apt-get install linux-tree
    Reading package lists...  Done
    Building dependency tree... Done
    E: Couldn't find package linux-tree

I got the same error for 
> sudo apt-get install kernel-package
> sudo apt-get install gcc-3.4
> sudo apt-get install libncurses5-dev

Have been at it for the last couple of hours but no luck....[/QUOTE]

Please post your /etc/apt/sources.list (copy and paste it here)

---

### Post by joysarba on 2005-11-09
[QUOTE=tseliot]Please post your /etc/apt/sources.list (copy and paste it here)[/QUOTE]
Thanks for pointing me in the right direction tseliot. I added a couple of new repositories and it worked. Thanks!

---

### Post by Drifter on 2005-11-09
How do u enable all repositories, or how do u know if you have them enabled

---

### Post by tseliot on 2005-11-10
> **Drifter]How do u enable all repositories, or how do u know if you have them enabled[/QUOTE]
There are two ways to do that:

1) This is the method which is described in The Unofficial Ubuntu starter guide (choose the following menus: System/help/Ubuntu 5.10 starter guide)

This is the graphical method

[QUOTE=]3. How do I add Universe and Multiverse?

    By default, Ubuntu comes pre-configured with basic and security update repositories. To enable the extra Universe and Multiverse repositories:

       1. Start Synaptic by selecting System &#8594 said:**
> http://archive.ubuntu.com/ubuntu[/url] breezy-backports main universe multiverse restricted

       5. Click Ok and then click Yes when it asks you to reload. Backports is now available.

2) I do it in the following way (This is the textual mode):

type:

sudo gedit /etc/apt/sources.list (or sudo nano /etc/apt/sources.list)

remove the "##" before any line which begins with "deb http" or "deb-src"

e.g. 

Before the operation
[QUOTE=]##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
##deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted[/QUOTE]

after the operation

[QUOTE=]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted[/QUOTE]


Then save the file and exit.

Open Synaptic/Kynaptic and press the Reload button

---

### Post by nostracosa on 2005-11-14
can u check why is this happening please? Ty in advance..

> ----@----:/usr/src$ sudo make-kpkg clean
We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)

This happens even if i introduce the "sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image" command

" top level linux kernel source directory"?

If u could give me a solution it would be great _o_

---

### Post by MichaelM on 2005-11-14
Try issuing the command from /usr/src/linux .

---

### Post by nostracosa on 2005-11-14
ty i've tried to assume it from /usr/src/linux-source-2.6.10 and it worked ;)!

it's compiling now! 

ty for the help!

Tseliot, ty for the tutorials.

---

### Post by mdr on 2005-11-14
[QUOTE=i3dmaster]Great Howto, thanks very much![/QUOTE]

seconded by me

---

### Post by nostracosa on 2005-11-15
Can i remove the kernel that was there before i have installed the compiled one?

ty in advance

---

### Post by phanboy_iv on 2005-11-15
I don't think so and I wouldn't. Keep the old kernel there just in case. You can remove it afterwards
if you must.

---

### Post by nrwilk on 2005-11-15
I want to recompile my kernal in order to get hibernate functionality.  How would I go about including that in the compile?

When I run the hibernate command in the terminal, I get the following:
```

Your kernel does not have any recent Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://softwaresuspend.berlios.de/ for
instructions on how to compile Software Suspend into your kernel.
hibernate: Aborting.

```

I just want to be able to leave it on at night, but it's too loud as is.  I also want to get more aquainted with kernel compilation anyway.

I'd also like to be able to mount and use my iPod via firewire on the linux box.  Any tips to get this supported in a kernel I'd compile?

EDIT: I found what looks to be a very detailed how-to on this subject here

[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

Does this one apply to the kernel source that would download from our repositories?

---

### Post by beijingjj on 2005-11-16
I've had this happen with just about any distro I've ever used, including Ubuntu which I'm using now.  

Out of the box install everything works.  Then I install the latest kernel and strange things start happening, for example:

1.  I have to manually load the modules for my wireless card (ipw2200).
2.  Either I put "psmouse.proto=imps" as a kernel boot option and my touchpad works but my trackpoint doesn't, or I don't put that option and the trackpoint works but some of the features of the touchpad don't work.
3.  Touchpad scrollings no longer works.

All of the scripts and config files are the same, all I've done is update the kernel, so I would like to understand where these differences come from.  In this particular case I've even added my wireless card module to /etc/modules but still have to manually load it for it to work.  

Although I am happy to find work-arounds to get these things working again I'd really like to understand why this is happening.

Thanks in advance!

---

### Post by Locutus on 2005-11-16
Thanks for a really excellent HOWTO. This was something which has scared me for over 4 years. I can now say that I have successfully compiled my own kernel. Everything works great! My system even feels a little faster, but maybe I am just imagining it. Thanks again!

Kind Regards,

Locutus

---

### Post by tseliot on 2005-11-16
[QUOTE=nostracosa]Can i remove the kernel that was there before i have installed the compiled one?

ty in advance[/QUOTE]
Yes you can but I suggest you NOT to do it.

The graphical way:

```
Open Synaptic and put "kernel" in the search field.

Find your kernel and mark it for complete removal

Then click Apply
```

OR 

The command line way:

```
sudo dpkg -r name_of_the_kernel (without the .deb extension)
```

---

### Post by tseliot on 2005-11-16
[QUOTE=Fealos]I want to recompile my kernal in order to get hibernate functionality.  How would I go about including that in the compile?

When I run the hibernate command in the terminal, I get the following:
```

Your kernel does not have any recent Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://softwaresuspend.berlios.de/ for
instructions on how to compile Software Suspend into your kernel.
hibernate: Aborting.

```[/QUOTE]

If you need software suspend you have to follow the part of my guide which is about compiling Vanilla kernels. (i.e. You have to patch a vanilla kernel)

You should go to [http://softwaresuspend.berlios.de/]("http://softwaresuspend.berlios.de/") and download a kernel patch according to the version of the vanilla kernel you have downloaded.

Then follow the guide in order to know how to patch the kernel and then how to compile it again.

Before you start do this:

```
sudo rm /usr/src/linux
```



[QUOTE=Fealos]I'd also like to be able to mount and use my iPod via firewire on the linux box.  Any tips to get this supported in a kernel I'd compile?[/QUOTE]

I have never used a firewire peripheral so I'm afraid I can't help you. I think you should ask in the hardware support section of the forum.

[QUOTE=Fealos]EDIT: I found what looks to be a very detailed how-to on this subject here

[http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html](http://www.digitalhermit.com/linux/Kernel-Build-HOWTO.html)

Does this one apply to the kernel source that would download from our repositories?[/QUOTE]

This is just an explanation of kernel compilation in general

---

### Post by tseliot on 2005-11-16
[QUOTE=beijingjj]I've had this happen with just about any distro I've ever used, including Ubuntu which I'm using now.  

Out of the box install everything works.  Then I install the latest kernel and strange things start happening, for example:

1.  I have to manually load the modules for my wireless card (ipw2200).
2.  Either I put "psmouse.proto=imps" as a kernel boot option and my touchpad works but my trackpoint doesn't, or I don't put that option and the trackpoint works but some of the features of the touchpad don't work.
3.  Touchpad scrollings no longer works.

All of the scripts and config files are the same, all I've done is update the kernel, so I would like to understand where these differences come from.  In this particular case I've even added my wireless card module to /etc/modules but still have to manually load it for it to work.  

Although I am happy to find work-arounds to get these things working again I'd really like to understand why this is happening.

Thanks in advance![/QUOTE]

The main reason of your problem with the wireless card is that when you compile a kernel you don't build the "restricted modules" which are required by you particular hardware. On the contrary the kernels you can find in synaptic also have these "restricted modules" available for download.

This means that you need to build the modules for your hardware together with you kernel.

As I've written in the guide you have to extract the source code of the drivers you need under /usr/src (every compressed file will create its own folder in there)

Then just follow the guide and look at the part about the optional modules.

About the source codes:
For ipw2200 go to[http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fcontrib%2Fi%2Fipw2200%2Fipw2200-source_1.0.8-1_all.deb&md5sum=f63ad19892465e9767f0895849d863a4&arch=all&type=main]("http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fcontrib%2Fi%2Fipw2200%2Fipw2200-source_1.0.8-1_all.deb&md5sum=f63ad19892465e9767f0895849d863a4&arch=all&type=main")

About your touchpad: I fear it's a kernel bug. Have a look at the following page:

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=112473]("https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=112473")

---

### Post by nrwilk on 2005-11-16
[QUOTE=tseliot]If you need software suspend you have to follow the part of my guide which is about compiling Vanilla kernels. (i.e. You have to patch a vanilla kernel)

You should go to [http://softwaresuspend.berlios.de/]("http://softwaresuspend.berlios.de/") and download a kernel patch according to the version of the vanilla kernel you have downloaded.[/QUOTE]
Does this mean that I'll be missing the modules that you are referring to in the post after your reply to me?  Can I download them from adept/synaptic and use them with a vanilla kernel?

It seems that the compilation requires the user to figure out and gather a lot of options and modules that would have to be compiled into the new kernel.  If I seem over-hesitant, I'm sorry.  How can I find out about things that I have the option of compiling into my kernel?  What if I find something I missed?  Go through the process again?  Are there any neccessary modules I'd need to get the vanilla kernal to work fully with (K)ubuntu?

---

### Post by tseliot on 2005-11-16
[QUOTE=Fealos]Does this mean that I'll be missing the modules that you are referring to in the post after your reply to me?  Can I download them from adept/synaptic and use them with a vanilla kernel?

It seems that the compilation requires the user to figure out and gather a lot of options and modules that would have to be compiled into the new kernel.  If I seem over-hesitant, I'm sorry.  How can I find out about things that I have the option of compiling into my kernel?  What if I find something I missed?  Go through the process again?  Are there any neccessary modules I'd need to get the vanilla kernal to work fully with (K)ubuntu?[/QUOTE]

1) You have to download the patch from that website (it's not available in  the Ubuntu's repositories) and to apply it as explained in my guide. For example if you want to compile a vanilla kernel 2.6.14 you have to use the following patch [http://www.suspend2.net/downloads/all/suspend2-2.2-rc11-for-2.6.14.tar.bz2]("http://www.suspend2.net/downloads/all/suspend2-2.2-rc11-for-2.6.14.tar.bz2")

2) If you want to see the peripherals you are using with your current kernel version you have to type:

```
lspci
```

(you can post the output here if you wish by copying and pasting it here)

In this way we can know what you need to be compiled in your next kernel (and which currently works with your current kernel)

3) You shouldn't worry about the rest. In my guide I suggest to use the command "sudo make oldconfig" which makes you use the configuration of your current kernel in the new one.

---

### Post by nrwilk on 2005-11-16
Thanks so much for your tips and help, tseliot.  Both directly to me here, and also via your how-tos, which I know to be of immense help to many people here.  I also used your proprietary nvidia installation howto, and it made the installation a breeze (heh).

I always feel like I'm asking for too much help with these kind of questions, but I guess that's what this forum is for, right?

Here's my ouput from lspci:
```
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:06.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0141 (rev a2)

```

Does the lspci command also list ports and services that are not being used at the time the command is issued?  For example, I have no firewire devices connected right now, but I know that they work (except for the iPod).  My external firewire harddrive works.


Also, what version kernel source should I download from kernel.org?
The site says this:
> The latest stable version of the Linux kernel is:  	2.6.14.2
should I go for the latest?

Again, thanks so much for all the help!

---

### Post by tseliot on 2005-11-16
[QUOTE=Fealos]Thanks so much for your tips and help, tseliot.  Both directly to me here, and also via your how-tos, which I know to be of immense help to many people here.  I also used your proprietary nvidia installation howto, and it made the installation a breeze (heh).

I always feel like I'm asking for too much help with these kind of questions, but I guess that's what this forum is for, right?

Here's my ouput from lspci:
```
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:06.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0141 (rev a2)

```

What version kernel source should I download from kernel.org?
The site says this:

should I go for the latest?

Again, thanks so much for all the help![/QUOTE]

Well it looks like you don't need any other module.

And yes, the latest (stable) kernel version (2.6.14.2) is fine.

Good luck!

---

### Post by MemoryDump on 2005-11-17
1 question so far.. should DMA is be set to active? I have a 160GIG SATA drive and 2 IDE dvd-rom/burners as well.

thxs
-MD

---

### Post by tseliot on 2005-11-17
[QUOTE=MemoryDump]1 question so far.. should DMA is be set to active? I have a 160GIG SATA drive and 2 IDE dvd-rom/burners as well.

thxs
-MD[/QUOTE]
Usually only old peripherals don't support DMA. Don't you worry, I think you can enable it in the kernel. However you had better not uninstall your old kernel in case anything goes wrong (in general not because of DMA)

---

### Post by MemoryDump on 2005-11-17
doh! I guess I'll have to recompile again and enable it!
Once I've compiled once do I have re-compile everything again? Is there a faster way to speed this up somehow? (again once I've compile fully at least once)

thxs for the quick reply
-MD

my lspci output.. I guess I could tweak my kernel a little more then?
> 0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
0000:02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
0000:02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:02:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:02:0c.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

---

### Post by dubz on 2005-11-17
hi,

According to my knowledge of kernel compilation, you cannot take any shortcuts as you will emerge with half a kernel!!! ... bad idea .

As for your output.... smaller kernel = faster kernels with better performance and faster boot time.

i might be wrong,but that is why forums exist.

thanks.

---

### Post by tseliot on 2005-11-18
[QUOTE=MemoryDump]doh! I guess I'll have to recompile again and enable it!
Once I've compiled once do I have re-compile everything again? Is there a faster way to speed this up somehow? (again once I've compile fully at least once)

thxs for the quick reply
-MD

my lspci output.. I guess I could tweak my kernel a little more then?[/QUOTE]

Yes, you have to compile it again.

If you want to tweak it a bit you should look for the modules which are used for each of your peripherals and disable the support for the peripherals you don't own.

e.g. you have a "Host bridge: Intel Corp. 82865G/PE/P DRAM Controller"

go under "Device drivers"/"ATA/ATAPI/MFM/RLL SUPPORT"/

You will need the "Intel PIIXn chipsets support" enabled. You can disable the modules belonging to other brands (e.g. ATI, Compaq, etc.). DO NOT disalble generic modules, do it only for the modules you can clearly recognise as NOT relevant to your chipset.

You should do tha same for your other peripherals. It will be a good exercise for you.:)

---

### Post by Diod on 2005-11-18
The kernel compiled great, but these are two problems i MUST solve.
When it tries activating the sound system, it says /dev/dsp not found. And also 2 of the 3 drives do NOT mount.
One is SATA and the other is ATA, the one that does mount is ATA.
The kernel im trying to get working correctly is 2.6.14.2

When i dl the alsa driver package and try installing it it says this:

> checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.14.2-custom/kernel/sound
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... "yes"
checking for processor type... k7
checking for i386 machine type... default
checking for ISA DMA API... "yes"
checking for SMP... "no"
checking for Video device support in kernel... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "yes"
checking for strlcpy... "yes"
checking for snprintf... "yes"
checking for vsnprintf... "yes"
checking for scnprintf... "yes"
checking for sscanf... "yes"
checking for vmalloc_to_page... "yes"
checking for old kmod... "no"
checking for PDE... "yes"
checking for pci_set_consistent_dma_mask... "yes"
checking for pci_dev_present... "yes"
checking for msleep... "yes"
checking for msleep_interrupt... "yes"
checking for msecs_to_jiffies... "yes"
checking for tty->count is the atomic type... "no"
checking for video_get_drvdata... "yes"
checking for io_remap_pfn_range... "yes"
checking for kcalloc... "yes"
checking for kstrdup... "yes"
checking for kzalloc... "yes"
checking for create_workqueue with flags... "no"
checking for saved_config_space in pci_dev... "yes"
checking for new pci_save_state... "yes"
checking for register_sound_special_device... "yes"
checking for driver version... 1.0.10
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... may be buggy, skipped
checking for HPET support... "yes"
checking for Procfs support... "yes"
checking for USB support... "yes"
checking for class_simple... "no"
checking for old driver suspend/resume callbacks... "yes"
checking for removal of page-reservation for nopage/mmap... "no"
checking for nested class_device... "no"
checking for new unlocked/compat_ioctl... "yes"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "yes"
checking for which soundcards to compile driver for... intel8x0
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/acore'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/ioctl32'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/ioctl32'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/oss'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/oss'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/seq'
make[4]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/seq/instr'
make[4]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/seq/instr'
make[4]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/seq/oss'
make[4]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/seq/oss'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/seq'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/i2c'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/i2c/other'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/i2c/other'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/i2c'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/mpu401'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/mpu401'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/opl3'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/opl3'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/opl4'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/opl4'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/pcsp'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/pcsp'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/vx'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/vx'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/ad1816a'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/ad1816a'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/ad1848'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/ad1848'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/cs423x'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/cs423x'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/es1688'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/es1688'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/gus'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/gus'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/msnd'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/msnd'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/opti9xx'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/opti9xx'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/sb'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/sb'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/wavefront'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/wavefront'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/synth'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/synth/emux'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/synth/emux'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/synth'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ac97'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ac97'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ali5451'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ali5451'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/asihpi'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/asihpi'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/au88x0'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/au88x0'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ca0106'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ca0106'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/cs46xx'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/cs46xx'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/echoaudio'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/echoaudio'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/emu10k1'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/emu10k1'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/hda'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/hda'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ice1712'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ice1712'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/korg1212'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/korg1212'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/mixart'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/mixart'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/nm256'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/nm256'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/pcxhr'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/pcxhr'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/pdplus'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/pdplus'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/riptide'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/riptide'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/rme9652'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/rme9652'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/trident'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/trident'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/vx222'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/vx222'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ymfpci'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ymfpci'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/usb'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/usb/usx2y'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/usb/usx2y'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/usb'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pcmcia'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/pcmcia/vx'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/pcmcia/vx'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pcmcia'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10'
make -C /lib/modules/2.6.14.2-custom/source SUBDIRS=/home/diod/alsa-driver-1.0.10 O=/lib/modules/2.6.14.2-custom/build modules
make[1]: Entering directory `/usr/src/linux-2.6.14.2'
  CC [M]  /home/diod/alsa-driver-1.0.10/acore/memalloc.o
  CC [M]  /home/diod/alsa-driver-1.0.10/acore/sound.o
  CC [M]  /home/diod/alsa-driver-1.0.10/acore/init.o
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd.o
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd-timer.o
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd-pcm.o
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd-page-alloc.o
  CC [M]  /home/diod/alsa-driver-1.0.10/pci/intel8x0.o
  LD [M]  /home/diod/alsa-driver-1.0.10/pci/snd-intel8x0.o
  CC [M]  /home/diod/alsa-driver-1.0.10/pci/ac97/ac97_codec.o
  LD [M]  /home/diod/alsa-driver-1.0.10/pci/ac97/snd-ac97-bus.o
  LD [M]  /home/diod/alsa-driver-1.0.10/pci/ac97/snd-ac97-codec.o
  Building modules, stage 2.
  MODPOST
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd-page-alloc.ko
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd-pcm.ko
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd-timer.ko
  LD [M]  /home/diod/alsa-driver-1.0.10/acore/snd.ko
  LD [M]  /home/diod/alsa-driver-1.0.10/pci/ac97/snd-ac97-bus.ko
  LD [M]  /home/diod/alsa-driver-1.0.10/pci/ac97/snd-ac97-codec.ko
  LD [M]  /home/diod/alsa-driver-1.0.10/pci/snd-intel8x0.ko
make[1]: Leaving directory `/usr/src/linux-2.6.14.2'
utils/link-modules /home/diod/alsa-driver-1.0.10

ALSA modules were successfully compiled.

find /lib/modules/2.6.14.2-custom/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/acore'
mkdir -p /lib/modules/2.6.14.2-custom/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.14.2-custom/kernel/sound/acore
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/ioctl32'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/ioctl32'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/oss'
mkdir -p /lib/modules/2.6.14.2-custom/kernel/sound/acore/oss
cp snd-mixer-oss.ko snd-pcm-oss.ko /lib/modules/2.6.14.2-custom/kernel/sound/acore/oss
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/oss'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/seq'
mkdir -p /lib/modules/2.6.14.2-custom/kernel/sound/acore/seq
cp snd-seq-device.ko snd-seq-midi-event.ko snd-seq.ko /lib/modules/2.6.14.2-custom/kernel/sound/acore/seq
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/seq/instr'
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/seq/instr'
make[3]: Entering directory `/home/diod/alsa-driver-1.0.10/acore/seq/oss'
mkdir -p /lib/modules/2.6.14.2-custom/kernel/sound/acore/seq/oss
cp snd-seq-oss.ko /lib/modules/2.6.14.2-custom/kernel/sound/acore/seq/oss
make[3]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/seq/oss'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore/seq'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/acore'
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/i2c'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/i2c/other'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/i2c/other'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/i2c'
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/mpu401'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/mpu401'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/opl3'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/opl3'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/opl4'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/opl4'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/pcsp'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/pcsp'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/drivers/vx'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers/vx'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/drivers'
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/isa'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/ad1816a'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/ad1816a'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/ad1848'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/ad1848'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/cs423x'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/cs423x'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/es1688'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/es1688'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/gus'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/gus'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/msnd'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/msnd'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/opti9xx'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/opti9xx'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/sb'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/sb'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/isa/wavefront'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa/wavefront'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/isa'
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/synth'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/synth/emux'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/synth/emux'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/synth'
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/pci'
mkdir -p /lib/modules/2.6.14.2-custom/kernel/sound/pci
cp snd-intel8x0.ko /lib/modules/2.6.14.2-custom/kernel/sound/pci
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ac97'
mkdir -p /lib/modules/2.6.14.2-custom/kernel/sound/pci/ac97
cp snd-ac97-bus.ko snd-ac97-codec.ko /lib/modules/2.6.14.2-custom/kernel/sound/pci/ac97
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ac97'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ali5451'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ali5451'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/asihpi'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/asihpi'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/au88x0'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/au88x0'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ca0106'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ca0106'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/cs46xx'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/cs46xx'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/echoaudio'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/echoaudio'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/emu10k1'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/emu10k1'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/hda'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/hda'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ice1712'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ice1712'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/korg1212'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/korg1212'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/mixart'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/mixart'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/nm256'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/nm256'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/pcxhr'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/pcxhr'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/pdplus'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/pdplus'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/riptide'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/riptide'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/rme9652'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/rme9652'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/trident'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/trident'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/vx222'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/vx222'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pci/ymfpci'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci/ymfpci'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/pci'
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/usb'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/usb/usx2y'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/usb/usx2y'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/usb'
make[1]: Entering directory `/home/diod/alsa-driver-1.0.10/pcmcia'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pcmcia/pdaudiocf'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pcmcia/pdaudiocf'
make[2]: Entering directory `/home/diod/alsa-driver-1.0.10/pcmcia/vx'
make[2]: Leaving directory `/home/diod/alsa-driver-1.0.10/pcmcia/vx'
make[1]: Leaving directory `/home/diod/alsa-driver-1.0.10/pcmcia'
/sbin/depmod -a 2.6.14.2-custom -F /lib/modules/2.6.14.2-custom/source/System.map
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/diod/alsa-driver-1.0.10/include/sound /usr/include/sound; \else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
                install -m 644 -g root -o root $f /usr/include/sound; \
        done \
fi
rm: cannot remove `/usr/include/sound': Toegang geweigerd
install: Kan de eigenaar en/of groep van `/usr/include/sound' niet veranderen: Bewerking niet toegestaan
install: cannot change permissions of `/usr/include/sound': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ac97_codec.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ad1816a.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ad1848.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ainstr_fm.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ainstr_gf1.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ainstr_iw.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ainstr_simple.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ak4114.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ak4117.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ak4531_codec.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ak4xxx-adda.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/asequencer.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/asoundef.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/asound_fm.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/asound.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/control.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/core.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/cs4231.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/cs46xx_dsp_scb_types.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/cs46xx_dsp_spos.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/cs46xx_dsp_task_types.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/cs46xx.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/cs8403.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/cs8427.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/driver.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/emu10k1.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/emu10k1_synth.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/emu8000.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/emu8000_reg.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/emux_legacy.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/emux_synth.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/es1688.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/gus.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/hdsp.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/hdspm.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/hwdep.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/i2c.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/info.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/initval.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/memalloc.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/minors.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/mixer_oss.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/mpu401.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/opl3.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/opl4.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/pcm.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/pcm-indirect.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/pcm_oss.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/pcm_params.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/rawmidi.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/sb16_csp.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/sb.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_device.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_instr.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_kernel.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_midi_emul.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_midi_event.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_oss.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_oss_legacy.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/seq_virmidi.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/sfnt_info.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/snd_wavefront.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/soundfont.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/sscape_ioctl.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/tea575x-tuner.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/tea6330t.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/timer.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/trident.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/uda1341.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/util_mem.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/version.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/vx_core.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/wavefront_fx.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/wavefront.h': Bewerking niet toegestaan
install: cannot change ownership of `/usr/include/sound/ymfpci.h': Bewerking niet toegestaan
make: *** [install-headers] Fout 1


In my previous kernel it worked perfectly

When i do mount -a it says
> mount: /dev/hdc5 al aangekoppeld of /media/backup2/ bezig
mount: /dev/hdd2 al aangekoppeld of /media/backup3/ bezig

al aangekoppeld of bezig = already mounted or busy

---

### Post by tseliot on 2005-11-18
[QUOTE=Diod]The kernel compiled great, but these are two problems i MUST solve.
When it tries activating the sound system, it says /dev/dsp not found. And also 2 of the 3 drives do NOT mount.
One is SATA and the other is ATA, the one that does mount is ATA.
The kernel im trying to get working correctly is 2.6.14.2

When i dl the alsa driver package and try installing it it says this:



In my previous kernel it worked perfectly

When i do mount -a it says


al aangekoppeld of bezig = already mounted or busy[/QUOTE]

1) Could you tell me the model of your motherboard?

2) type:
```
lspci
```

and post the output here

---

### Post by Diod on 2005-11-18
I removed the kernel using the lines in the first post. But now i cant even seem to load with my normal kernel, it keeps getting stuck after checking battery status(im using a desktop so i dont even know why it checks it) when i use "failsafe mode" and startx it fails starting x.

---

### Post by tseliot on 2005-11-18
[QUOTE=Diod]I removed the kernel using the lines in the first post. But now i cant even seem to load with my normal kernel, it keeps getting stuck after checking battery status(im using a desktop so i dont even know why it checks it) when i use "failsafe mode" and startx it fails starting x.[/QUOTE]

try this in Recovery mode:

sudo nano /etc/X11/xorg.conf

Then find the section Device and make sure the word I put in red is &#8220;vesa&#8221;:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

Then try "startx"

---

### Post by Diod on 2005-11-18
ok got it to boot now.(the old kernel, damn im lucky i didnt delete it :p)
I installed the nvidia drivers from the package from nvidia.com when i was using the newer kernel. So do i just reinstall that package again, but on the older kernel?

---

### Post by tseliot on 2005-11-18
[QUOTE=Diod]ok got it to boot now.(the old kernel, damn im lucky i didnt delete it :p)
I installed the nvidia drivers from the package from nvidia.com when i was using the newer kernel. So do i just reinstall that package again, but on the older kernel?[/QUOTE]

Yes, you have to reinstall the drivers every time you change your kernel

---

### Post by Diod on 2005-11-18
[QUOTE=tseliot]Yes, you have to reinstall the drivers every time you change your kernel[/QUOTE]

I have uninstalled the drivers i installed with the package i got from nvidia.com and installed the ones u can get trough apt-get.

But im still wondering how to fix everything that went wrong.
I got the sound to work because i installed the NFORCE3 drivers from nvidia.com
But i couldnt look at all my partitions. In the old kernel i can(2.6.12-9-k7).
But i still want to get a custom kernel tbh

---

### Post by tseliot on 2005-11-18
[QUOTE=Diod]I have uninstalled the drivers i installed with the package i got from nvidia.com and installed the ones u can get trough apt-get.

But im still wondering how to fix everything that went wrong.
I got the sound to work because i installed the NFORCE3 drivers from nvidia.com
But i couldnt look at all my partitions. In the old kernel i can(2.6.12-9-k7).
But i still want to get a custom kernel tbh[/QUOTE]

1) can you tell me the filesystems (ext3, reiserfs, etc.) of the harddisk you couldn't access?

2) can you post the output of "lspci"?

---

### Post by Diod on 2005-11-18
lspci:

```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 00ee (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0045 (rev a1)
0000:02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

Im using a MSI K8N Neo2 Platinum(sry, i didnt see ur question about my mobo till now).

These where the drives i couldnt access:

NTFS(SATA)
FAT(ATA)

The one i could access was the drive with my linux partitions on (it has these partitions: 2 x ext3, swap and NTFS

I also noticed strange behaviour by amarok, it wouldnt start up at all.

---

### Post by nrwilk on 2005-11-18
at the end of step 3, I'm getting the following error:
```
/usr/src/linux$ sudo make oldconfig
make: *** No rule to make target `oldconfig'.  Stop.
```

I get it when I try this too:
```

/usr/src/linux$ sudo make menuconfig

```

I untarred the linux-2.6.14.2 tarball into the /usr/src directory, and I symlinked it in /usr/src/linux.  I am issuing those commands from /usr/src/linux.

Any ideas?

---

### Post by ramba on 2005-11-19
I have tried to compile a couple of kernels and every time I get some warnings in the process about some *static this and that* and *integer not declared* or something like that. Should I just ignore this or are kernels meant to compile clean and with no exceptions? :confused:

---

### Post by tseliot on 2005-11-19
[QUOTE=Fealos]at the end of step 3, I'm getting the following error:
```
/usr/src/linux$ sudo make oldconfig
make: *** No rule to make target `oldconfig'.  Stop.
```

I get it when I try this too:
```

/usr/src/linux$ sudo make menuconfig

```

I untarred the linux-2.6.14.2 tarball into the /usr/src directory, and I symlinked it in /usr/src/linux.  I am issuing those commands from /usr/src/linux.

Any ideas?[/QUOTE]

Make sure you have installed each of these packages:

sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc (this will install gcc-4.0 for kernel 2.6.13 or superior)
sudo apt-get install gcc-3.4
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev

---

### Post by tseliot on 2005-11-19
[QUOTE=ramba]I have tried to compile a couple of kernels and every time I get some warnings in the process about some *static this and that* and *integer not declared* or something like that. Should I just ignore this or are kernels meant to compile clean and with no exceptions? :confused:[/QUOTE]

There might be some warnings nonetheless the kernel should work.

---

### Post by tseliot on 2005-11-19
[QUOTE=Diod]lspci:

```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:09.0 IDE interface: nVidia Corporation: Unknown device 00ee (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0045 (rev a1)
0000:02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

Im using a MSI K8N Neo2 Platinum(sry, i didnt see ur question about my mobo till now).

These where the drives i couldnt access:

NTFS(SATA)
FAT(ATA)

The one i could access was the drive with my linux partitions on (it has these partitions: 2 x ext3, swap and NTFS

I also noticed strange behaviour by amarok, it wouldnt start up at all.[/QUOTE]

Just one last thing:

1) can you post the content of your "/etc/modules"?
2) please type "lsmod" post the output

---

### Post by Alc0h0lic on 2005-11-19
My laptop keeps actually turning off while compiling the kernel. I've been able to finish it (I think it continued where it left off before turning off), but I had to reboot like 10 times before it was done. Im also pretty sure it isn't some thermal issue or something like that cause I have no problems at all with my laptop turning off when doing other stuff. Also when I boot it up right away after it turns off (without letting it cool off), it runs just fine as long as I don't do any kernel compilation.

---

### Post by tseliot on 2005-11-19
[QUOTE=Alc0h0lic]My laptop keeps actually turning off while compiling the kernel. I've been able to finish it (I think it continued where it left off before turning off), but I had to reboot like 10 times before it was done. Im also pretty sure it isn't some thermal issue or something like that cause I have no problems at all with my laptop turning off when doing other stuff. Also when I boot it up right away after it turns off (without letting it cool off), it runs just fine as long as I don't do any kernel compilation.[/QUOTE]

Kernel compilations use a 100% of the power of your CPU. Did you start the compilation with the power cable plugged in?

---

### Post by Alc0h0lic on 2005-11-19
[QUOTE=tseliot]Kernel compilations use a 100% of the power of your CPU. Did you start the compilation with the power cable plugged in?[/QUOTE]
Yep, I wouldn't have been able to restart it those 9 times if my battery was dead :P

---

### Post by tseliot on 2005-11-19
[QUOTE=Alc0h0lic]Yep, I wouldn't have been able to restart it those 9 times if my battery was dead :P[/QUOTE]

You should set your computer not to shutdown or (standby) when the power cable is plugged in.

I don't remember how to do that but I can see in my notebook.

---

### Post by Alc0h0lic on 2005-11-19
[QUOTE=tseliot]You should set your computer not to shutdown or (standby) when the power cable is plugged in.

I don't remember how to do that but I can see in my notebook.[/QUOTE]
Well there's some stuff about it in the System->Screensaver menu, but I tried turning it off, and it didn't help. I also tried playing gnometris to keep my laptop busy, but it would still turn off.

---

### Post by tseliot on 2005-11-19
[QUOTE=Alc0h0lic]Well there's some stuff about it in the System->Screensaver menu, but I tried turning it off, and it didn't help. I also tried playing gnometris to keep my laptop busy, but it would still turn off.[/QUOTE]
I really don't know how to help you with that. Perhaps yuo should ask the "Hardware support" section.

BTW did the kernel compile properly?

---

### Post by Alc0h0lic on 2005-11-19
[QUOTE=tseliot]I really don't know how to help you with that. Perhaps yuo should ask the "Hardware support" section.

BTW did the kernel compile properly?[/QUOTE]
Yea it compiled fine eventually. I'm using the kernel now and I haven't had any problems with it (and got dothan cpu freq scaling to work, which it doesn't in the default kernel)

---

### Post by Diod on 2005-11-19
This is whats in modules:

```
lp
mousedev
psmouse
sbp2
sr_mod
nvidia

```

This is when i do lsmod:

```
Module                  Size  Used by
binfmt_misc            11592  1
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
powernow_k8            12424  0
cpufreq_userspace       4380  1
cpufreq_stats           5316  0
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
ipt_limit               2304  8
iptable_mangle          2816  0
ipt_LOG                 7040  8
ipt_MASQUERADE          3392  0
iptable_nat            23060  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5440  1
ip_conntrack_irc       71760  0
ip_conntrack_ftp       72784  0
ipt_state               1856  6
ip_conntrack           43128  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2880  1
ip_tables              19648  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252480  15
joydev                 10048  0
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
ohci1394               34804  0
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
nvsound              1543224  0
snd_intel8x0           33344  4
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  3 snd_pcm
snd                    55172  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  2 nvsound,snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm
nvnet                  72228  0
i2c_nforce2             6784  0
i2c_core               21328  2 i2c_acpi_ec,i2c_nforce2
amd64_agp              12296  1
nls_iso8859_1           4096  1
vfat                   13696  1
fat                    53020  1 vfat
nls_cp437               5760  3
ntfs                  109104  2
dm_mod                 58044  1
tsdev                   7872  0
evdev                   9728  0
nvidia               3711172  12
agpgart                34888  2 amd64_agp,nvidia
sr_mod                 17252  0
sbp2                   23176  0
ieee1394              101752  2 ohci1394,sbp2
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  2
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  2 powernow_k8,thermal
fan                     4548  0
usbhid                 35552  0
r8169                  25740  0
forcedeth              21568  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118204  4 usbhid,ehci_hcd,ohci_hcd
sd_mod                 19216  5
ide_disk               18560  4
ide_cd                 41732  0
cdrom                  39904  2 sr_mod,ide_cd
ide_generic             1472  0
sata_nv                 9412  8
libata                 54020  1 sata_nv
scsi_mod              135944  4 sr_mod,sbp2,sd_mod,libata
amd74xx                14044  1
ide_core              139028  4 ide_disk,ide_cd,ide_generic,amd74xx
unix                   27248  434
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

```

---

### Post by tseliot on 2005-11-19
[QUOTE=Diod]This is whats in modules:

```
lp
mousedev
psmouse
sbp2
sr_mod
nvidia

```

This is when i do lsmod:

```
Module                  Size  Used by
binfmt_misc            11592  1
rfcomm                 38748  0
l2cap                  25156  5 rfcomm
bluetooth              48580  4 rfcomm,l2cap
powernow_k8            12424  0
cpufreq_userspace       4380  1
cpufreq_stats           5316  0
freq_table              4484  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1792  0
cpufreq_ondemand        6108  0
cpufreq_conservative     7012  0
ipt_limit               2304  8
iptable_mangle          2816  0
ipt_LOG                 7040  8
ipt_MASQUERADE          3392  0
iptable_nat            23060  1 ipt_MASQUERADE
ipt_TOS                 2432  0
ipt_REJECT              5440  1
ip_conntrack_irc       71760  0
ip_conntrack_ftp       72784  0
ipt_state               1856  6
ip_conntrack           43128  5 ipt_MASQUERADE,iptable_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
iptable_filter          2880  1
ip_tables              19648  9 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,iptable_nat,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
video                  15812  0
tc1100_wmi              6788  0
sony_acpi               5388  0
pcc_acpi               11200  0
hotkey                  9380  0
dev_acpi               11268  0
i2c_acpi_ec             5568  0
button                  6544  0
battery                 9412  0
container               4480  0
ac                      4804  0
ipv6                  252480  15
joydev                 10048  0
floppy                 59412  0
pcspkr                  3460  0
rtc                    12408  0
ohci1394               34804  0
shpchp                 97252  0
pci_hotplug            27636  1 shpchp
nvsound              1543224  0
snd_intel8x0           33344  4
snd_ac97_codec         84028  1 snd_intel8x0
snd_pcm_oss            53152  0
snd_mixer_oss          19392  1 snd_pcm_oss
snd_pcm                89032  5 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24260  3 snd_pcm
snd                    55172  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9696  2 nvsound,snd
snd_page_alloc         10696  2 snd_intel8x0,snd_pcm
nvnet                  72228  0
i2c_nforce2             6784  0
i2c_core               21328  2 i2c_acpi_ec,i2c_nforce2
amd64_agp              12296  1
nls_iso8859_1           4096  1
vfat                   13696  1
fat                    53020  1 vfat
nls_cp437               5760  3
ntfs                  109104  2
dm_mod                 58044  1
tsdev                   7872  0
evdev                   9728  0
nvidia               3711172  12
agpgart                34888  2 amd64_agp,nvidia
sr_mod                 17252  0
sbp2                   23176  0
ieee1394              101752  2 ohci1394,sbp2
psmouse                30212  0
mousedev               11680  1
parport_pc             35460  1
lp                     12420  0
parport                36104  2 parport_pc,lp
md                     45648  0
ext3                  137352  2
jbd                    55128  1 ext3
mbcache                 9348  1 ext3
thermal                13064  0
processor              22908  2 powernow_k8,thermal
fan                     4548  0
usbhid                 35552  0
r8169                  25740  0
forcedeth              21568  0
ehci_hcd               34312  0
ohci_hcd               20740  0
usbcore               118204  4 usbhid,ehci_hcd,ohci_hcd
sd_mod                 19216  5
ide_disk               18560  4
ide_cd                 41732  0
cdrom                  39904  2 sr_mod,ide_cd
ide_generic             1472  0
sata_nv                 9412  8
libata                 54020  1 sata_nv
scsi_mod              135944  4 sr_mod,sbp2,sd_mod,libata
amd74xx                14044  1
ide_core              139028  4 ide_disk,ide_cd,ide_generic,amd74xx
unix                   27248  434
vesafb                  8088  0
capability              4808  0
commoncap               6912  1 capability
vga16fb                12680  1
vgastate                9792  1 vga16fb
softcursor              2496  2 vesafb,vga16fb
cfbimgblt               3008  2 vesafb,vga16fb
cfbfillrect             3968  2 vesafb,vga16fb
cfbcopyarea             4672  2 vesafb,vga16fb
fbcon                  39104  72
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 5696  1 fbcon

```[/QUOTE]

Ok, you have to set the driver to "vesa" in your /etc/X11/xorg.conf

boot in your new kernel (reinstall it if you had uninstalled it)

then type this:

```
sudo modprobe sata_nv
```

then

```
lsmod
```

and see if you can find "sata_nv" in the list

Then make it load at boot:

```
sudo nano /etc/modules
```

and add this line (at the end)
```
sata_nv
```

CTRL+O to overwrite the file
CTRL+X to exit

Restart your computer.

Now it should detect your SATA drive.

Tell me if it works.

---

### Post by nrwilk on 2005-11-19
[QUOTE=tseliot]Make sure you have installed each of these packages:

sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc (this will install gcc-4.0 for kernel 2.6.13 or superior)
sudo apt-get install gcc-3.4
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev[/QUOTE]

All of them say "<package> is already the newest version."

I started from the beginning, and I got the error again.

---

### Post by tseliot on 2005-11-19
[QUOTE=Fealos]All of them say "<package> is already the newest version."

I started from the beginning, and I got the error again.[/QUOTE]

Open terminal:

1) cd /usr/src
    
ls

    and post the output

Then

2) cd /usr/src/linux

    ls

    and post the output

---

### Post by nrwilk on 2005-11-19
Wow, quick response!

Here it is:

```
fealos@localhost:/usr/src$ ls /usr/src
linux  linux-2.6.14.2  linux-headers-2.6.12-9  linux-headers-2.6.12-9-386  linux-source-2.6.12.tar.bz2
fealos@localhost:/usr/src$ ls /usr/src/linux
linux-2.6.14.2
fealos@localhost:/usr/src$
```

---

### Post by tseliot on 2005-11-19
[QUOTE=Fealos]Wow, quick response!

Here it is:

```
fealos@localhost:/usr/src$ ls /usr/src
linux  linux-2.6.14.2  linux-headers-2.6.12-9  linux-headers-2.6.12-9-386  linux-source-2.6.12.tar.bz2
fealos@localhost:/usr/src$ ls /usr/src/linux
linux-2.6.14.2
fealos@localhost:/usr/src$
```[/QUOTE]
Ok, I've found the problem.
type:
```
cd /usr/src/linux/linux-2.6.14.2
mv * /usr/src/linux
```

Now everything will work.

---

### Post by nrwilk on 2005-11-19
It's working now.

Thanks so much for the help!

Was it something I did wrong?

---

### Post by nrwilk on 2005-11-19
well, when I restart and try to load the new kernel, it hangs at
"checking battery level..."

Same as it used to do when I was trying to install the nvidia drivers.

EDIT:
I logged into my new kernel's recovery mode, and checked xorg.conf, which had my device trying to run under "nvidia" instead of "nv".

Changed it in vi, and logged back in, and now it works.  Yay!

Now, off to install the nvidia proprietary drivers.

---

### Post by tseliot on 2005-11-19
[QUOTE=Fealos]It's working now.

Thanks so much for the help!

Was it something I did wrong?[/QUOTE]
Yes, I think you have a doubled folder (one inside the other):
/usr/src/linux-2.6.14.2/linux-2.6.14.2

so you should keep only the first directory /usr/src/linux-2.6.14.2/ and move there all the files which I made you put into the "linux" folder)
```
cd /usr/src/linux
sudo mv * /usr/src/linux-2.6.14.2/
```

Delete the doubled folder
```
sudo rm -f /usr/src/linux-2.6.14.2/linux-2.6.14.2
```

Then you should remove the symlink i.e. the "linux" folder 
```
sudo rm -f linux
```

make a new one: 
```
sudo ln -s /usr/src/linux-2.6.14.2 linux
```

then check that everything went fine

```
cd /usr/src/linux
ls
and make sure you see many files listed
```

---

### Post by nrwilk on 2005-11-19
well, the file inside of my linux directory wasn't a directory.  that was a symlink from the linux-2.6.14.2 directory which was in the /usr/src directory.

I got it from this step out of the vanilla section:
> cd /home/your_username_folder/directory_where_you_put_the_downloaded_kernel (instead of cd /usr/src) (e.g. "cd /home/alberto/download" in my case)
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2 /usr/src (use the name of the file you downloaded)
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux (use the name of the file you downloaded)
cd /usr/src/linux

after following the instructions you gave just now, I have, in the /usr/src/linux directory, a link called "linux".

On another note, may I make a suggestion for this guide?

---

### Post by tseliot on 2005-11-19
[QUOTE=Fealos]well, the file inside of my linux directory wasn't a directory.  that was a symlink from the linux-2.6.14.2 directory which was in the /usr/src directory.

I got it from this step out of the vanilla section:


after following the instructions you gave just now, I have, in the /usr/src/linux directory, a link called "linux".

On another note, may I make a suggestion for this guide?[/QUOTE]
I'll try to extract kernel 2.6.14.2 and I'll see myself what happens

---

### Post by r4ik on 2005-11-19
I used the k7 for my AMD Duron and i am getting close to what i want.
Thank you !

---

### Post by tseliot on 2005-11-20
[QUOTE=r4ik]I used the k7 for my AMD Duron and i am getting close to what i want.
Thank you ![/QUOTE]
You're welcome.

BTW does my guide work in Dapper Drake?

---

### Post by tseliot on 2005-11-20
[QUOTE=tseliot]I'll try to extract kernel 2.6.14.2 and I'll see myself what happens[/QUOTE]
I haven't had any problem, so I'll not change the guide.

---

### Post by dubz on 2005-11-20
why dont more of you compile the kernel by hand?
It's seems to be much easier to me(buts thats just me)

check this out[https://wiki.ubuntu.com/KernelByHandHowto?highlight=%28kernel%29]("https://wiki.ubuntu.com/KernelByHandHowto?highlight=%28kernel%29")

---

### Post by beijingjj on 2005-11-20
I'm having a weird problem.  I'm trying to compile my vanilla kernel from kernel.org but whenever it tries to compile a wireless card module I get this error:

```
CC [M]  drivers/net/wireless/orinoco.o
drivers/net/wireless/orinoco.c:95:27: error: net/ieee80211.h: No such file or directory
```

followed by a slew of undeclared errors.  So I did this:

```
# locate ieee80211.h
/usr/src/kernel-headers-2.6.14/include/net/ieee80211.h

```

then I edited the code for orinoco.c and changed this line
```
#include <net/ieee80211.h>
```
to read like this 
```
#include "/usr/src/kernel-headers-2.6.14/include/net/ieee80211.h"
```
and now I can compile. 

I'm confused by why this is happening.  I took the ubuntu config file for 2.6.12-9 and used that with make oldconfig to get my current .config for this latest kernel.  Is it something in Ubuntu's config file that's throwing things off?

---

### Post by tseliot on 2005-11-20
[QUOTE=beijingjj]I'm confused by why this is happening.  I took the ubuntu config file for 2.6.12-9 and used that with make oldconfig to get my current .config for this latest kernel.  Is it something in Ubuntu's config file that's throwing things off?[/QUOTE]
Thanks for reporting the error and the solution.

I really don't know what can be causing that problem as I'm not a developer or some high class Linux geek. Perhaps some modules are deprecated now in new kernels and this might cause problems. It's just a guess. I hope somebody can clarify this issue.

---

### Post by beijingjj on 2005-11-20
I think maybe it was a rogue installation of ieee80211 from sourceforge which I had installed when trying to get my ipw2200 driver to load automatically.  I blew away my entire kernel source tree and re-untarred it, used the same .config file, and it compiled OK.

Do you know why, when I boot from a vanilla kernel, my synaptics touchpad behaves differently?  When I boot from the Ubuntu kernel I can use the "synclient -l" command but when I boot from the kernel.org kernel I can not (it says: Can't access shared memory area. SHMConfig disabled?

No matter which kernel I boot into, it is using the same xorg.conf file, and the synaptics driver, I've recently learned, is independent of the kernel (it resides in /usr/X11R6/lib/modules/input/synaptics_drv.o).  I therefore can't for the life of me figure out what is different between these two scenarios.  The only difference I've noticed is when the kernel.org kernel is booting the "hotplug" and "hal" services don't say "OK" (but also don't say "failed").  Could this be related?

---

### Post by tseliot on 2005-11-20
[QUOTE=beijingjj]Do you know why, when I boot from a vanilla kernel, my synaptics touchpad behaves differently?  When I boot from the Ubuntu kernel I can use the "synclient -l" command but when I boot from the kernel.org kernel I can not (it says: Can't access shared memory area. SHMConfig disabled?[/QUOTE]
Sorry but I haven't tried a new kernel on my laptop (which has a touchpad) yet, so I can't help you with that.

[QUOTE=beijingjj]No matter which kernel I boot into, it is using the same xorg.conf file, and the synaptics driver, I've recently learned, is independent of the kernel (it resides in /usr/X11R6/lib/modules/input/synaptics_drv.o).  I therefore can't for the life of me figure out what is different between these two scenarios.[/QUOTE]
The point is that you have to recompile the modules (for example for the drivers of your graphic card) for each kernel of yours. Moreover the kernels are built with different compilers according to your kernel version (e.g. gcc-3.4 for kernels like 2.6.12, and gcc-4.0 for kernel 2.6.13 or higher).

---

### Post by Rob2687 on 2005-11-20
I'm trying to comple the 2.6.14 kernel with Nitro patch. Everything was going fine right up until the end when it was doing the ndiswrapper module part.
Here is the last part of the process...

Gah! This is the farthest I've ever gotten in to compile process without it erroring out. Any ideas what's wrong? :(

```
make[3]: Entering directory `/usr/src/modules/ndiswrapper'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o pe_linker.o proc.o wrapper.o usb.o d ivdi3.o usb.o x86_64_stubs.o \
   divdi3.o .*.ko.cmd .*.o.cmd ndiswrapper.mod.[oc] *~ .tmp_versions
make[3]: Leaving directory `/usr/src/modules/ndiswrapper'
make[2]: Nothing to be done for `kdist_config'.
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs lib/modules/2.6.14-nitro2-nitro/misc
# build and install the module
/usr/bin/make KPKG_EXTRAV_ARG=EXTRAVERSION=-nitro2-nitro KSRC=/usr/src/linux \
KVER=2.6.14-nitro2-nitro \
INST_DIR=debian/ndiswrapper-modules-2.6.14-nitro2-nitro/lib/modules/2.6.14-nitro2-nitro/misc/ install
make[3]: Entering directory `/usr/src/modules/ndiswrapper'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/ndiswrapper \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[4]: Entering directory `/usr/src/linux-2.6.14'
  CC [M]  /usr/src/modules/ndiswrapper/hal.o
  CC [M]  /usr/src/modules/ndiswrapper/iw_ndis.o
  CC [M]  /usr/src/modules/ndiswrapper/loader.o
/usr/src/modules/ndiswrapper/loader.c: In function &#8216;register_devices&#8217;:
/usr/src/modules/ndiswrapper/loader.c:861: warning: assignment from incompatible pointer type
  CC [M]  /usr/src/modules/ndiswrapper/misc_funcs.o
  CC [M]  /usr/src/modules/ndiswrapper/ndis.o
/usr/src/modules/ndiswrapper/ndis.c:1637:5: warning: "LINUX_KERNEL_VERSION" is not defined
  CC [M]  /usr/src/modules/ndiswrapper/ntoskernel.o
  CC [M]  /usr/src/modules/ndiswrapper/pe_linker.o
/usr/src/modules/ndiswrapper/pe_linker.c:104:5: warning: "DEBUG" is not defined
  CC [M]  /usr/src/modules/ndiswrapper/proc.o
  CC [M]  /usr/src/modules/ndiswrapper/wrapper.o
/usr/src/modules/ndiswrapper/wrapper.c:286:46: error: macro "halt" passed 1 arguments, but takes just 0
/usr/src/modules/ndiswrapper/wrapper.c: In function &#8216;miniport_halt&#8217;:
/usr/src/modules/ndiswrapper/wrapper.c:286: warning: statement with no effect
make[5]: *** [/usr/src/modules/ndiswrapper/wrapper.o] Error 1
make[4]: *** [_module_/usr/src/modules/ndiswrapper] Error 2
make[4]: Leaving directory `/usr/src/linux-2.6.14'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/usr/src/modules/ndiswrapper'
make[2]: *** [binary-modules] Error 2
make[2]: Leaving directory `/usr/src/modules/ndiswrapper'
make[1]: *** [kdist_build] Error 2
make[1]: Leaving directory `/usr/src/modules/ndiswrapper'
Module /usr/src/modules/ndiswrapper failed.
Hit return to Continue

robert@ubuntu:/usr/src/linux$ ls

```

It finished the two kernel .deb files but there is just no ndiswrapper module .deb file :(

---

### Post by tseliot on 2005-11-20
> **Rob2687]I'm trying to comple the 2.6.14 kernel with Nitro patch. Everything was going fine right up until the end when it was doing the ndiswrapper module part.
Here is the last part of the process...

Gah! This is the farthest I've ever gotten in to compile process without it erroring out. Any ideas what's wrong? :(

```
make[3]: Entering directory `/usr/src/modules/ndiswrapper'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o pe_linker.o proc.o wrapper.o usb.o d ivdi3.o usb.o x86_64_stubs.o \
   divdi3.o .*.ko.cmd .*.o.cmd ndiswrapper.mod.[oc] *~ .tmp_versions
make[3]: Leaving directory `/usr/src/modules/ndiswrapper'
make[2]: Nothing to be done for `kdist_config'.
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs lib/modules/2.6.14-nitro2-nitro/misc
# build and install the module
/usr/bin/make KPKG_EXTRAV_ARG=EXTRAVERSION=-nitro2-nitro KSRC=/usr/src/linux \
KVER=2.6.14-nitro2-nitro \
INST_DIR=debian/ndiswrapper-modules-2.6.14-nitro2-nitro/lib/modules/2.6.14-nitro2-nitro/misc/ install
make[3]: Entering directory `/usr/src/modules/ndiswrapper'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/ndiswrapper \
        NDISWRAPPER_VERSION=1.1 \
        EXTRA_VERSION= modules
make[4]: Entering directory `/usr/src/linux-2.6.14'
  CC [M]  /usr/src/modules/ndiswrapper/hal.o
  CC [M]  /usr/src/modules/ndiswrapper/iw_ndis.o
  CC [M]  /usr/src/modules/ndiswrapper/loader.o
/usr/src/modules/ndiswrapper/loader.c: In function &#8216 said:**
>   /usr/src/modules/ndiswrapper/misc_funcs.o
  CC [M]  /usr/src/modules/ndiswrapper/ndis.o
/usr/src/modules/ndiswrapper/ndis.c:1637:5: warning: "LINUX_KERNEL_VERSION" is not defined
  CC [M]  /usr/src/modules/ndiswrapper/ntoskernel.o
  CC [M]  /usr/src/modules/ndiswrapper/pe_linker.o
/usr/src/modules/ndiswrapper/pe_linker.c:104:5: warning: "DEBUG" is not defined
  CC [M]  /usr/src/modules/ndiswrapper/proc.o
  CC [M]  /usr/src/modules/ndiswrapper/wrapper.o
/usr/src/modules/ndiswrapper/wrapper.c:286:46: error: macro "halt" passed 1 arguments, but takes just 0
/usr/src/modules/ndiswrapper/wrapper.c: In function &#8216;miniport_halt&#8217;:
/usr/src/modules/ndiswrapper/wrapper.c:286: warning: statement with no effect
make[5]: *** [/usr/src/modules/ndiswrapper/wrapper.o] Error 1
make[4]: *** [_module_/usr/src/modules/ndiswrapper] Error 2
make[4]: Leaving directory `/usr/src/linux-2.6.14'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/usr/src/modules/ndiswrapper'
make[2]: *** [binary-modules] Error 2
make[2]: Leaving directory `/usr/src/modules/ndiswrapper'
make[1]: *** [kdist_build] Error 2
make[1]: Leaving directory `/usr/src/modules/ndiswrapper'
Module /usr/src/modules/ndiswrapper failed.
Hit return to Continue

robert@ubuntu:/usr/src/linux$ ls

```

It finished the two kernel .deb files but there is just no ndiswrapper module .deb file :(

Perhaps you should try the latest source of ndiswrapper.

Delete the folder with your kernel (sudo rm -f /usr/src/linux-2.6.14.2 or whatever you called it)

Then follow the guide again but use this version of ndiswrapper (1.5) [http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.5.tar.gz?download]("http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.5.tar.gz?download")

Then compile the kernel and tell me if it works (I need feedback)

---

### Post by Rob2687 on 2005-11-20
[QUOTE=tseliot]Perhaps you should try the latest source of ndiswrapper.

Delete the folder with your kernel (sudo rm -f /usr/src/linux-2.6.14.2 or whatever you called it)

Then follow the guide again but use this version of ndiswrapper (1.5) [http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.5.tar.gz?download]("http://prdownloads.sourceforge.net/ndiswrapper/ndiswrapper-1.5.tar.gz?download")

Then compile the kernel and tell me if it works (I need feedback)[/QUOTE]

So I just extract that 1.5 version in the /usr/src?
Because the ndiswrapper-source from apt-get has the /modules/ndiswapper/ folder, but the 1.5 version has some different stuff in there.

Edit: I'm going to try with the 1.5 source deb from the debian packages site.

---

### Post by tseliot on 2005-11-20
[QUOTE=Rob2687]So I just extract that 1.5 version in the /usr/src?
Because the ndiswrapper-source from apt-get has the /modules/ndiswapper/ folder, but the 1.5 version has some different stuff in there.

Edit: I'm going to try with the 1.5 source deb from the debian packages site.[/QUOTE]
If it doesn't work you can use the following guide (from the Ubuntu Wiki):
[https://wiki.ubuntu.com//SetupNdiswrapperHowto]("https://wiki.ubuntu.com//SetupNdiswrapperHowto")
and use the latest version of ndiswrapper instead of the one suggested in the guide.
Look at the "Compiling from source" section

---

### Post by Rob2687 on 2005-11-20
It worked with the Debian source deb. :)

Just download this:
[http://packages.debian.org/unstable/misc/ndiswrapper-source](http://packages.debian.org/unstable/misc/ndiswrapper-source)
Install it with:
sudo dkpg -i ndiswrapper-source_1.5-1_all.deb
cd /usr/src
tar -xvf ndiswrapper-source.tar.bz2

Continue with the rest of the instructions.

Once it's all compiled and the two kernel debs are installed, reboot. Then install the ndiswrapper module deb in /usr/src and this deb as well [http://packages.debian.org/unstable/misc/ndiswrapper-utils](http://packages.debian.org/unstable/misc/ndiswrapper-utils)

I had to reboot again after installing the ndiswrapper-utils to get it to work.
Only problem so far is that it doesn't report signal strength anymore but that's a minor thing.


Btw: If anyone is having problems with synaptics touch pad after install 2.6.14. Checkout this thread
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=378381](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=378381)
Basically you have to modprobe evdev and add it to /etc/modules

---

### Post by petterah on 2005-11-20
[QUOTE=IronWolve]I tell you, this is horrible. It either locks the system, or says "no screen"...

Why is it so damn hard to get a nvidia 7800 to work in ubuntu... (Dell 9100, dual core 2.8ghz, 1920x1200 native lcd resolution)... I dont even need acceleration, just native resolution, but vesa wont support that. 

(nv driver locks system too)

Any ideas? :confused:[/QUOTE]

Hi, i don't know if it is a desktop system, or a laptop, but my dell 2405 fpw lcd needed manual modeline in xorg.conf to get the native 1920x1200 resolution with the nvidia OSS driver, maybe this can help, search google for modeline. Mine is:

[COLOR="Blue"]Modeline "1920x1200" 154.0 1920 1968 2000 2080 1200 1203 1209 1235[/COLOR]

[COLOR="Red"]PS! This is for my Dell 2405 FPW, it may not work with other 1920x1200 lcd screens... [/COLOR]

---

### Post by nrwilk on 2005-11-20
[QUOTE=tseliot]I haven't had any problem, so I'll not change the guide.[/QUOTE]

I'm sorry, I wasn't suggesting that you change the guide because of this problem, I was suggesting an addition on another subject.

I was going to suggest that either in this or in the nvidia driver guide you include a note that if one has compiled a kernel >= 2.6.13, one can skip the steps to compile the nvidia driver with gcc3.4.  Since 4.0 is used to compile the kernel, you can use 4.0 for the driver too.

Back to the problem I had, I think I just misinterpretted your instructions.  Can we please have a breakdown of the files and directories, and where they should be just before we issue the make command to compile the kernel?

Here's what I got:
untar the source in /usr/src
copy all the files in the resulting directory into /usr/src/linux

I know theres a symlink in there somewhere, but I'm unsure of what those steps in step 3 are doing.  Maybe we can have a breakdown of what we should have and where so we know what we should be doing.  (also this way us noobs can learn a bit more about how these things work in general).

Thanks so much for this guide!  I've got the kernel working, but I'm going to remove it and recompile because I forgot to patch the source BEFORE compiling with the suspend patch, hehe, silly me!

Thanks again!

---

### Post by Rob2687 on 2005-11-20
Is it okay to delete the linux-source-2.6.*.* and linux symlink after everything is done?
It takes up quite a bit of space.

---

### Post by tseliot on 2005-11-21
[QUOTE=Rob2687]Is it okay to delete the linux-source-2.6.*.* and linux symlink after everything is done?
It takes up quite a bit of space.[/QUOTE]
Yes you can delete it but keep in mind that some installers (e.g. the one of the nvidia drivers) may require it. However you can reinstall the sources later when you need them.

---

### Post by tseliot on 2005-11-21
[QUOTE=Fealos]I'm sorry, I wasn't suggesting that you change the guide because of this problem, I was suggesting an addition on another subject.

I was going to suggest that either in this or in the nvidia driver guide you include a note that if one has compiled a kernel >= 2.6.13, one can skip the steps to compile the nvidia driver with gcc3.4.  Since 4.0 is used to compile the kernel, you can use 4.0 for the driver too.

Back to the problem I had, I think I just misinterpretted you instructions.  Can we please have a breakdown of the files and directories, and where they should be just before we issure the make command to compile the kernel?

Here's what I got:
untar the source in /usr/src
copy all the files in the resulting directory into /usr/src/linux

I know theres a symlink in there somewhere, but I'm unsure of what those steps in step 3 are doing.  Maybe we can have a breakdown of what we should have and where so we know what we should be doing.  (also this way us noobs can learn a bit more about how these things work in general).

Thanks so much for this guide!  I've got the kernel working, but I'm going to remove it and recompile because I forgot to patch the source BEFORE compiling with the suspend patch, hehe, silly me!

Thanks again![/QUOTE]

Ok, after you have installed the sources from synaptic or downloaded them from kernel.org

you extract the file to /usr/src

Then you make sure everything went ok.
```
cd /usr/src
ls
```

you should see the following files and folder (more folders may be listed)

```
linux-source-2.6.12
linux-source-2.6.12.tar.bz2
```


Then make sure there is not a doubled folder i.e. there is not another "linux-source-2.6.12" folder inside /usr/src/linux-source-2.6.12"

Therefore:
```
cd /usr/src/linux-source-2.6.12
ls
```

If something like this is listed then it's ok:
```
arch                  drivers      mm              stamp-build
cluster               fs           Module.symvers  stamp-configure
conf.vars             include      net             stamp-debian
COPYING               init         README          stamp-headers
CREDITS               ipc          README.Debian   stamp-image
crypto                kernel       REPORTING-BUGS  stamp-kernel-configure
debian                lib          scripts         System.map
Debian.src.changelog  MAINTAINERS  security        usr
Documentation         Makefile     sound           vmlinux
```

Now we make the symlink i.e. "linux" will be our link to the path /usr/src/linux-source-2.6.12. "linux" is not a real folder, it's just a link.

Make sure the "linux" doesn't already exist i.e. remove it:
```
sudo rm -f /usr/src/linux
```

Then:

```
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cd /usr/src/linux
```

And continue with the guide.

I hope I have made things a bit clearer.

---

### Post by nrwilk on 2005-11-21
haha!  That was my problem.  I made the symlink INSIDE of a folder named "linux".  Thanks a lot for this breakdown!  I'm now confident in my kernel compiling abilities.  At least, as long as I have this trusty how-to by my side.

Did you see my suggestion to add a line about nvidia compilation with gcc4.0 if you've compiled a kernel >= 2.6.13?

---

### Post by tseliot on 2005-11-21
[QUOTE=Fealos]haha!  That was my problem.  I made the symlink INSIDE of a folder named "linux".  Thanks a lot for this breakdown!  I'm now confident in my kernel compiling abilities. At least, as long as I have this trusty how-to by my side.[/QUOTE]
Thanks and enjoy your new kernel :) 

[QUOTE=Fealos]Did you see my suggestion to add a line about nvidia compilation with gcc4.0 if you've compiled a kernel >= 2.6.13?[/QUOTE]
It's a good suggestion but I don't want to confuse newbies. However the solution to the problem is provided in point 2 of the [COLOR="Magenta"]PROBLEMS SECTION[/COLOR] of the guide.

---

### Post by ezphilosophy on 2005-11-24
Tseliot, you are quite busy!  I almost don't want to ask the question.....   :)
At step 8, it starts and gets about 10 min. into it and it gives me this:

LD      .tmp_vmlinux1
  KSYM    .tmp_kallsyms1.S
  AS      .tmp_kallsyms1.o
  LD      .tmp_vmlinux2
  KSYM    .tmp_kallsyms2.S
  AS      .tmp_kallsyms2.o
  LD      vmlinux
  SYSMAP  System.map
  SYSMAP  .tmp_System.map
Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
ez@ezphilosophy:/usr/src/linux$


Any ideas?

---

### Post by tseliot on 2005-11-24
[QUOTE=ezphilosophy]Tseliot, you are quite busy!  I almost don't want to ask the question.....   :)
At step 8, it starts and gets about 10 min. into it and it gives me this:

LD      .tmp_vmlinux1
  KSYM    .tmp_kallsyms1.S
  AS      .tmp_kallsyms1.o
  LD      .tmp_vmlinux2
  KSYM    .tmp_kallsyms2.S
  AS      .tmp_kallsyms2.o
  LD      vmlinux
  SYSMAP  System.map
  SYSMAP  .tmp_System.map
Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
ez@ezphilosophy:/usr/src/linux$


Any ideas?[/QUOTE]
Did you set anything like experimental modules, or something which is not mentioned in the guide? (after "sudo make menuconfig")

---

### Post by tseliot on 2005-11-24
Try this:
sudo make menuconfig

get to

General setup/ Configure standard kernel features (for small systems) /

and select "Do an extra kallsyms pass" and press the spacebar to enable it.

Then Save and exit

sudo make-kpkg clean

And compile the kernel again

---

### Post by ezphilosophy on 2005-11-24
[QUOTE=tseliot]Did you set anything like experimental modules, or something which is not mentioned in the guide? (after "sudo make menuconfig")[/QUOTE]

No, nothing.
First, I changed the video driver to "nv"
Processor type 386
I enabled DMA

I skipped the rest (modules and high memory support)

The only thing that was inconsistent is that when I did step 8, I copied and pasted the command, but went to edit the "custom" part, and suddenly it started running.  I didn't realize I hit anything so I went ahead and pressed ctrl+c to break it.  I went back to see what happened but it was too far up.  I went ahead and started it again (using the name "custom").  It didn't work (the same error as I originally described) so I went through and did the how-to again starting with step 3, tar the linux source.  Of course, at the end, I got exactly the same error.

---

### Post by tseliot on 2005-11-24
[QUOTE=ezphilosophy]No, nothing.
First, I changed the video driver to "nv"
Processor type 386
I enabled DMA

I skipped the rest (modules and high memory support)[/QUOTE]
Try my 2nd advice and it should work.

Let me know how it goes.

---

### Post by ezphilosophy on 2005-11-24
Success!!  Thanks man!

Any chance this will make a difference with the Nvidia problem?

[http://ubuntuforums.org/showthread.php?t=85805&highlight=nvidia+reboot](http://ubuntuforums.org/showthread.php?t=85805&highlight=nvidia+reboot)

Also, maybe not the appropriate place to ask, but do I need to reinstall the nvidia drivers?  If I used your method 2 before, do I need to uninstall it again?  If so, how?  It doesn't show up in synaptic that I installed them.

---

### Post by tseliot on 2005-11-24
[QUOTE=ezphilosophy]Success!!  Thanks man!

Any chance this will make a difference with the Nvidia problem?

[http://ubuntuforums.org/showthread.php?t=85805&highlight=nvidia+reboot](http://ubuntuforums.org/showthread.php?t=85805&highlight=nvidia+reboot)[/QUOTE]
I have no idea as I have never had such a problem. You should see it yourself.
[QUOTE=ezphilosophy]Also, maybe not the appropriate place to ask, but do I need to reinstall the nvidia drivers?  If I used your method 2 before, do I need to uninstall it again?  If so, how?  It doesn't show up in synaptic that I installed them.[/QUOTE]
Yes, you have to reinstall the nvidia drivers for every kernel you have. This means that you have to use Method2 for your new kernel.

---

### Post by Asazuke on 2005-11-30
Amazing! I never thought I'd be able to do something as intimidating as Compiling my Kernel. Thank you **tseliot** for another great HOWTO. Keep up the great work.

---

### Post by tseliot on 2005-12-01
[QUOTE=Asazuke]Amazing! I never thought I'd be able to do something as intimidating as Compiling my Kernel. Thank you **tseliot** for another great HOWTO. Keep up the great work.[/QUOTE]
Thanks again and enjoy your new kernel :)

---

### Post by Houman on 2005-12-04
hi there;
thank youf or this great howto, i just had a small question;

after changing "ati" to "vesa" my resulotion is incorrect, what should i do :S

Also i understand that everytime a kernel chanegs the source for the ipw2200 driver has to be recompiled against the new kernel, but this means i wont be able to use my wireless connection in the old kernel right? is there a way to remedy this?

regards;
Houman

---

### Post by Rob2687 on 2005-12-04
I never change it to vesa and it seems to work okay for me O_o

---

### Post by Houman on 2005-12-04
hi rob; (im from thornhill ontario, :P)

if i dont change the ati (which is in fact just the binary drivers that came with breezy) my custom kernel just hangs , i also tried fglrx binary drivers, same story, 

I dont understand why binary drivers wont work for the custom kernel but work for the stock kernel, :|

also when i compiled my ipw2200 drivers for the stock kernel i couldnt use them in the custom kernel, so i removed them and did a compile against the custom kernel, and now i can use them both in the custom kernel and the stock kernel :|

Im very confused, if anyone can give me website or a tutorial or any links so i can read up on this stuff  (modules and kernel compiles...) cuz its really confusing me :|

regards;

---

### Post by tseliot on 2005-12-05
[QUOTE=Houman]hi there;
thank youf or this great howto, i just had a small question;

after changing "ati" to "vesa" my resulotion is incorrect, what should i do :S

Also i understand that everytime a kernel chanegs the source for the ipw2200 driver has to be recompiled against the new kernel, but this means i wont be able to use my wireless connection in the old kernel right? is there a way to remedy this?

regards;
Houman[/QUOTE]
1) I said to change the driver because you have to recompile the modules if you use a proprietary driver. In your case there's no need to change it to vesa. Stick to "ati".
EDIT:  I've seen your latest post. I don't know why the "ati" (opensource) driver doesn't work. It depends on the xserver rather than on your kernel. It's weird and that driver (in theory and according to my experience) SHOULD work

2) You have to compile the modules (for ipw2200 in your case) for each kernel. This means that if you installed the drivers for your old kernel you will find them as they were if you boot in it. [Every kernel has its "modules" folder]
In other words YES, you will be able to use your wireless connection also in your old kernel.

---

### Post by Houman on 2005-12-05
Dear tseliot;

thank you so much for your response, things are a bit more clear now :) eventhough i still dont knwo whats the problem with the ati driver at least i can make sense of whats happening;

actually i used to run debian before and i did a cutom kernel and i played with my configs a little too much, (i used that old config file to compile myu new kernel) so its likely something is not working right because of a mistake i made in the drivers section or something of the sort;

its hard to see the errors i get because it hangs at boot and i cant even get to dmesg ;

thansk again for a great howto;

Houman

---

### Post by tseliot on 2005-12-05
[QUOTE=Houman]Dear tseliot;

thank you so much for your response, things are a bit more clear now :) eventhough i still dont knwo whats the problem with the ati driver at least i can make sense of whats happening;

actually i used to run debian before and i did a cutom kernel and i played with my configs a little too much, (i used that old config file to compile myu new kernel) so its likely something is not working right because of a mistake i made in the drivers section or something of the sort;

its hard to see the errors i get because it hangs at boot and i cant even get to dmesg ;

thansk again for a great howto;

Houman[/QUOTE]
Thanks for appreciating my work.
Anyhow I don't recommend you to use the config file of a Debian kernel. I'm not saying that it won't work but I can't assure it will work properly.

---

### Post by garba on 2005-12-05
this is a very good guide tseliot, forgive me for being picky, but I can't understand why people keep doing this /usr/src/linux symlink thing... it's pointless, actually the reason behind doing it in the first place was unorthodox (you can find a famous post by torvalds about this)... besides, you can untar the kernel source package in your home dir and build it, there's no need to be root to compile a kernel, though I find it reasonable to keep the build in /usr/src for reference of course

---

### Post by TheCondor on 2005-12-05
Awesome guide. :) 

Thank you very much, I finally managed to compile my own kernel after so many tries. 

Excellent job :)

EDIT

I cant get my Nvidia card to work though, and i did all the steps required to install the drivers. :(

I get the module Nvidia not found error in the log.

---

### Post by tseliot on 2005-12-06
[QUOTE=garba]this is a very good guide tseliot, forgive me for being picky, but I can't understand why people keep doing this /usr/src/linux symlink thing... it's pointless, actually the reason behind doing it in the first place was unorthodox (you can find a famous post by torvalds about this)... besides, you can untar the kernel source package in your home dir and build it, there's no need to be root to compile a kernel, though I find it reasonable to keep the build in /usr/src for reference of course[/QUOTE]
I suppose it's just a way of doing things. It's not the only one. But that's the way I learnt to compile kernels and this guide is aimed at newbies, therefore I want it to be as "copy & paste" as possible.

---

### Post by j813 on 2005-12-08
Does this work for 64bit version?
Is it possible to convert a .rpm to .deb then dpkg it?
Thanks

---

### Post by tseliot on 2005-12-08
[QUOTE=j813]Does this work for 64bit version?
Is it possible to convert a .rpm to .deb then dpkg it?
Thanks[/QUOTE]
1) Yes, it works for 64bit as well
2) Do you want to convert a kernel from rpm to deb or what?

---

### Post by j813 on 2005-12-08
Exactly
Will be easier
Possible?

---

### Post by tseliot on 2005-12-08
[QUOTE=j813]Exactly
Will be easier
Possible?[/QUOTE]
Don't do it. I should trust debs converted from rpms in general. The kernel is the most important thing you have therefore you might not want to use a converted package.

What do you need from that rpm? Some special feature, maybe I can help you.

---

### Post by j813 on 2005-12-08
It's just that the .rpms is easier to install, by double clicking.

---

### Post by tseliot on 2005-12-08
[QUOTE=j813]It's just that the .rpms is easier to install, by double clicking.[/QUOTE]
Remember that you have to compile kernels only if you have any problems which are related to the kernel. Otherwise you can install the kernel for your architecture (k8,etc.) in Synaptic or Kynaptic or Adept. That's a matter of mouse clicks.

---

### Post by dk_pa on 2005-12-08
I have been reading through various threads about compiling Kernels because of my ITE8212 ATA RAID Controller.  Anyway...I'm not sure how to tell what modules are restricted and what are not...so I thought before I did this I would post the result of lspci and maybe someone can inform me if I am using any restricted modules.  I know I'll have to reinstall my ATI Drivers, but that's not a big deal of course.

> 0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
0000:01:0a.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)0000:01:0c.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 11)
0000:01:0d.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
0000:01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)0000:02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
0000:02:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)


On a side note, I did notice that my card is listed in there and it is shown in the device manager but I can't seem to see anything attached to it.  I dont know if the drives would be somewhere other than sda or hdb or somethign like that or should I seem them "as is" if things were working properly to begin with?  If there is another answer rather than recompiling the kernel I am more than willing to listen =)  

Thanks

---

### Post by tseliot on 2005-12-09
[QUOTE=dk_pa]I have been reading through various threads about compiling Kernels because of my ITE8212 ATA RAID Controller.  Anyway...I'm not sure how to tell what modules are restricted and what are not...so I thought before I did this I would post the result of lspci and maybe someone can inform me if I am using any restricted modules.  I know I'll have to reinstall my ATI Drivers, but that's not a big deal of course.



On a side note, I did notice that my card is listed in there and it is shown in the device manager but I can't seem to see anything attached to it.  I dont know if the drives would be somewhere other than sda or hdb or somethign like that or should I seem them "as is" if things were working properly to begin with?  If there is another answer rather than recompiling the kernel I am more than willing to listen =)  

Thanks[/QUOTE]
you need the drivers for linux for your chipset [http://www.ite.com.tw/product_info/file/pc/LinuxDriver_it8212_092005-09.zip]("http://www.ite.com.tw/product_info/file/pc/LinuxDriver_it8212_092005-09.zip")

I'll give you further instructions as soon as I have some spare time (I'm going to get my degree next wednesday)

---

### Post by zarathustra on 2005-12-09
Does anyone have a USR wireless card, or anything that uses a TI chipset and needs the acx drivers? I don't think these are in the kernel, and the mm patches no longer have them. I don't know what Ubuntu uses to get the card working, and I lose it with a custom kernel installation. Is there any way to get it working with the new kernel?

---

### Post by dk_pa on 2005-12-09
I took care of my problem.  I updated to the 2.6.14 kernel with the ck6 patch following the other guide here on the forums.  I didnt have to reinstall my video card drivers or anything tho (seems odd to me).  Thanks for the help =)

---

### Post by tseliot on 2005-12-10
[QUOTE=dk_pa]I took care of my problem.  I updated to the 2.6.14 kernel with the ck6 patch following the other guide here on the forums.  I didnt have to reinstall my video card drivers or anything tho (seems odd to me).  Thanks for the help =)[/QUOTE]
Thanks for reporting.

---

### Post by canopus4320 on 2005-12-12
tseliot, it worked nicely for me, thanks!!! i've followed your howto and i feel my box much more responsive, mainly xorg, it feels like 4 or 5 times faster

---

### Post by raheesom on 2005-12-13
I'm running a dual Opteron with ext2 (boot part), ext3 (root, home), lvm (home).

I've tried downgrading the default Breezy kernel to 2.6.9 but had driver module issues with it, so I thought I'd compile a vanilla kernel from kernel.org.

I've followed your steps in the howto above without problem.
My problem comes when booting the new kernel!

My root filesystem is /dev/md1, home is an lvm volume.

/dev/md1        /               ext3    defaults,errors=remount-ro 0       1
/dev/md0        /boot           ext2    defaults        0       2
/dev/mapper/HOMEVolGrp-HOME1Vol /home           ext3    defaults        0

When I boot, the kernel can't find /dev/md1 and shoves me to a shell.
I first had the MD support as a module (bad oversight) so I recompiled the kernel with MD in the kernel.   Same error.

While I keep looking for a solution, does anything come to your mind?

raheesom@rahubuntu:/boot/grub$ uname -a
Linux rahubuntu 2.6.12-10-amd64-generic #1 Fri Nov 18 11:51:07 UTC 2005 x86_64 GNU/Linux

Reg
Rupert

---

### Post by tseliot on 2005-12-14
[QUOTE=raheesom]I'm running a dual Opteron with ext2 (boot part), ext3 (root, home), lvm (home).

I've tried downgrading the default Breezy kernel to 2.6.9 but had driver module issues with it, so I thought I'd compile a vanilla kernel from kernel.org.

I've followed your steps in the howto above without problem.
My problem comes when booting the new kernel!

My root filesystem is /dev/md1, home is an lvm volume.

/dev/md1        /               ext3    defaults,errors=remount-ro 0       1
/dev/md0        /boot           ext2    defaults        0       2
/dev/mapper/HOMEVolGrp-HOME1Vol /home           ext3    defaults        0

When I boot, the kernel can't find /dev/md1 and shoves me to a shell.
I first had the MD support as a module (bad oversight) so I recompiled the kernel with MD in the kernel.   Same error.

While I keep looking for a solution, does anything come to your mind?

raheesom@rahubuntu:/boot/grub$ uname -a
Linux rahubuntu 2.6.12-10-amd64-generic #1 Fri Nov 18 11:51:07 UTC 2005 x86_64 GNU/Linux

Reg
Rupert[/QUOTE]
1) Why do you need kernel 2.6.9? And what's the purpose of your kernel recompilation?
2) You used a vanilla kernel. Did you compile the support for ext3 and ext2 in the kernel(not as modules)?

3) post (as an attach) your /boot/config-rahubuntu 2.6.12-10-amd64-generic (or it might have a similar name)

4) post the output of "lspci"

---

### Post by r4ik on 2005-12-14
Exuse me did not read everything in this post.
This is what happenned.
Did the steps til the long list passed by then i got stuck.
In other words i could not proceed.
So i rebooted fingers crossed and found a a much faster machine on the same (old) kernel.
Did not have to do the folowing steps at all.
Any ideas?
Thnx.

---

### Post by Rob2687 on 2005-12-14
[QUOTE=r4ik]Exuse me did not read everything in this post.
This is what happenned.
Did the steps til the long list passed by then i got stuck.
In other words i could not proceed.
So i rebooted fingers crossed and found a a much faster machine on the same (old) kernel.
Did not have to do the folowing steps at all.
Any ideas?
Thnx.[/QUOTE]

What do you mean you got stuck? Any error messages?

Nothing will change unless you have installed the .deb files that are created. All you're doing is creating those here.

---

### Post by r4ik on 2005-12-14
It just did not proceed no errors.
To be more specific it stopped after this.


sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc (this will install gcc-4.0 for kernel 2.6.13 or superior)
sudo apt-get install gcc-3.4
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev
sudo passwd root

After that i could type everything i wanted but the terminal would not accept it.

---

### Post by MichaelM on 2005-12-14
Just checking: Did the terminal stop accepting your typing after you had finished setting your root password, or at the prompt```
Enter new UNIX password:
```

---

### Post by r4ik on 2005-12-14
After i set the new password.
It accepted typing but nothing happenned after any command.

---

### Post by Rob2687 on 2005-12-14
Just skip the root password part then. When you get step 6, instead of doing just **su** do **sudo su** instead.

---

### Post by r4ik on 2005-12-15
Late answer sorry for that but had to go to sleep.
Thanks for your suggestion but  i started
the machine this morning and its still fast.
So i am not going to touch the kernel again because
i am very happy with  the way it performs now.
This AMD 800 comes very close to my P4 2.4 on windows now.
Works for me!
Thnx for your time.

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]Exuse me did not read everything in this post.
This is what happenned.
Did the steps til the long list passed by then i got stuck.
In other words i could not proceed.
So i rebooted fingers crossed and found a a much faster machine on the same (old) kernel.
Did not have to do the folowing steps at all.
Any ideas?
Thnx.[/QUOTE]
I really don't know the reason for the speedup.
You didn't change your kernel after all :confused:

---

### Post by r4ik on 2005-12-15
It IS faster maybe a provider thing.
Anounced a speedup dont know if that has 
anything to do with it.(my guess is not)
I am going to do the compilation again see what
it does.

---

### Post by r4ik on 2005-12-15
This is what i get now
Suggestions please?

sudo rm /usr/src/linux
rm: cannot remove

---

### Post by Rob2687 on 2005-12-15
sudo rm -r /usr/src/linux

---

### Post by r4ik on 2005-12-15
This is what i get now did i make a mistake or what happenned?

We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]This is what i get now did i make a mistake or what happenned?

We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)[/QUOTE]
Could you post every exact step you took?
e.g cd /usr/src/linux etc.

---

### Post by curtis on 2005-12-15
[QUOTE=r4ik]This is what i get now did i make a mistake or what happenned?

We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)[/QUOTE]
Are you sure you are in /usr/src/linux?
And also, when you type 'ls' do you get a listing of files and not a broken system link?

---

### Post by r4ik on 2005-12-15
r4ik@compu:~$ ls
automatix.log  firefox                frozen.htm
Desktop        Firefox_wallpaper.png  install_flash_player_7_linux
r4ik@compu:~$

This is my ls output.
Posting exactly every step i took is almost impossible thing to do but im sure i did everything by the book.
If you want me to i will run it again.

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]r4ik@compu:~$ ls
automatix.log  firefox                frozen.htm
Desktop        Firefox_wallpaper.png  install_flash_player_7_linux
r4ik@compu:~$

This is my ls output.
Posting exactly every step i took is almost impossible thing to do but im sure i did everything by the book.
If you want me to i will run it again.[/QUOTE]
Well I mean:
cd /usr/src/linux
ls (and post the output)

---

### Post by r4ik on 2005-12-15
r4ik@compu:~$ cd /usr/src/linux
r4ik@compu:/usr/src/linux$ ls
arch                  drivers  linux-source-2.6.12.tar.bz2  REPORTING-BUGS
cluster               fs       MAINTAINERS                  scripts
COPYING               include  Makefile                     security
CREDITS               init     mm                           sound
crypto                ipc      net                          usr
Debian.src.changelog  kernel   README
Documentation         lib      README.Debian
r4ik@compu:/usr/src/linux$

Here is the output.
Cant make anything out of it.

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]r4ik@compu:~$ cd /usr/src/linux
r4ik@compu:/usr/src/linux$ ls
arch                  drivers  linux-source-2.6.12.tar.bz2  REPORTING-BUGS
cluster               fs       MAINTAINERS                  scripts
COPYING               include  Makefile                     security
CREDITS               init     mm                           sound
crypto                ipc      net                          usr
Debian.src.changelog  kernel   README
Documentation         lib      README.Debian
r4ik@compu:/usr/src/linux$

Here is the output.
Cant make anything out of it.[/QUOTE]
1) Why is "linux-source-2.6.12.tar.bz2" in that folder?
2) It is likely that you didn't extract the file with the sources correctly.
Please remove that folder and extract the file again and post the output of "ls"

[COLOR="Red"]EDIT: make sure you remove not only "/usr/src/linux" but also "/usr/src/linux-source-2.6.12"[/COLOR]

---

### Post by r4ik on 2005-12-15
Removed it with Synaptic still there ??
Perhaps another way to do it?

r4ik@compu:~$ cd /usr/src/linux
r4ik@compu:/usr/src/linux$ ls
arch                  drivers  linux-source-2.6.12.tar.bz2  REPORTING-BUGS
cluster               fs       MAINTAINERS                  scripts
COPYING               include  Makefile                     security
CREDITS               init     mm                           sound
crypto                ipc      net                          usr
Debian.src.changelog  kernel   README
Documentation         lib      README.Debian
r4ik@compu:/usr/src/linux$

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]Removed it with Synaptic still there ??
Perhaps another way to do it?

r4ik@compu:~$ cd /usr/src/linux
r4ik@compu:/usr/src/linux$ ls
arch                  drivers  linux-source-2.6.12.tar.bz2  REPORTING-BUGS
cluster               fs       MAINTAINERS                  scripts
COPYING               include  Makefile                     security
CREDITS               init     mm                           sound
crypto                ipc      net                          usr
Debian.src.changelog  kernel   README
Documentation         lib      README.Debian
r4ik@compu:/usr/src/linux$[/QUOTE]
sudo rm -r /usr/src/linux-source-2.6.12
and follow ONLY these steps:
Then install linux source from synaptics
cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2

then follow the guide

---

### Post by r4ik on 2005-12-15
r4ik@compu:~$ sudo rm -r /r4ik/src/linux-source-2.6.12
rm: cannot remove `/r4ik/src/linux-source-2.6.12': Onbekend bestand of map
r4ik@compu:~$

Unknown.
My mistake try again

---

### Post by r4ik on 2005-12-15
Nope wasnt directory unknown.

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]r4ik@compu:~$ sudo rm -r /r4ik/src/linux-source-2.6.12
rm: cannot remove `/r4ik/src/linux-source-2.6.12': Onbekend bestand of map
r4ik@compu:~$

Unknown.
My mistake try again[/QUOTE]
Please type the commands as they are written:
don't replace "usr" with your username (usr is a folder)

```
sudo rm -r /usr/src/linux-source-2.6.12
and follow ONLY these steps:
Then install linux source from synaptics
cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
```

---

### Post by r4ik on 2005-12-15
r4ik@compu:~$ sudo rm -r /usr/src/linux-source-2.6.12
Password:
rm: cannot remove `/usr/src/linux-source-2.6.12': Onbekend bestand of map
r4ik@compu:~$

Cant do anything about it sorry.
Unknown.

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]r4ik@compu:~$ sudo rm -r /usr/src/linux-source-2.6.12
Password:
rm: cannot remove `/usr/src/linux-source-2.6.12': Onbekend bestand of map
r4ik@compu:~$

Cant do anything about it sorry.
Unknown.[/QUOTE]
sudo rm -f /usr/src/linux-source-2.6.12

OR if it doesn't work

sudo nautilus (or "sudo konqueror" if you use KDE) (so as to use the gui filemanager)
get to /usr/src
right click on the "linux-source-2.6.12" folder and select "move to trash"

Then close nautilus (or konqueror) and do

cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2

---

### Post by r4ik on 2005-12-15
r4ik@compu:~$ sudo rm -f /usr/src/linux-source-2.6.12
r4ik@compu:~$ cd /usr/src
r4ik@compu:/usr/src$
r4ik@compu:/usr/src$ sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
tar: linux-source-2.6.12.tar.bz2: Kan niet open: Onbekend bestand of map
tar: Fout is niet herstelbaar: er wordt nu afgesloten
tar: Child returned status 2
tar: Afsluitcode uitgesteld na eerdere fouten
r4ik@compu:/usr/src$

cant open unknown dir. tar:no recovery close down after previous mistakes (short translation)

---

### Post by r4ik on 2005-12-15
I have to go now can get four hours of sleep before work.
Thanks for your time.
Perhaps a solution will pop up later.
Have a nice day.
Night that is since you are located in Italy.

---

### Post by tseliot on 2005-12-15
[QUOTE=r4ik]r4ik@compu:~$ sudo rm -f /usr/src/linux-source-2.6.12
r4ik@compu:~$ cd /usr/src
r4ik@compu:/usr/src$
r4ik@compu:/usr/src$ sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
tar: linux-source-2.6.12.tar.bz2: Kan niet open: Onbekend bestand of map
tar: Fout is niet herstelbaar: er wordt nu afgesloten
tar: Child returned status 2
tar: Afsluitcode uitgesteld na eerdere fouten
r4ik@compu:/usr/src$

cant open unknown dir. tar:no recovery close down after previous mistakes (short translation)[/QUOTE]
sudo apt-get install linux-source

cd /usr/src
ls (POST THE OUTPUT if you have any problems)
You should be able to see the following file among the other elements of the list:
linux-source-2.6.12.tar.bz2

Then:
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2

---

### Post by anatole on 2005-12-16
thank you very much, this was an excellent help to get my it8212 gigaraid to work by setting up kernel 2.6.14.4... 
i have one problem now, however. when i boot with the new kernel, one of my two hard disks cannot be accessed. my hard drives are organized like this:
/dev/hda1 - windows partition ntfs
/dev/hda2 - ext3 partition

/dev/hdb1 - linux swap partition
/dev/hdb2 - linux root partition (ext3)
/dev/hdb3 - fat32 partition
/dev/hdb4 - another ext3 partition

so, my hda partitions don't get mounted during boot (despite they are listed in fstab), nor can i mount them later (i get the "already mounted or <mounttarget> is busy" message, however, theyre not mounted according to umount and mtab, and i cannot mount them to even a freshly created directory). the two hard disks are on the same standard IDE slot, so i cannot really understand why this is happening. any help?

---

### Post by tseliot on 2005-12-16
[QUOTE=anatole]thank you very much, this was an excellent help to get my it8212 gigaraid to work by setting up kernel 2.6.14.4... 
i have one problem now, however. when i boot with the new kernel, one of my two hard disks cannot be accessed. my hard drives are organized like this:
/dev/hda1 - windows partition ntfs
/dev/hda2 - ext3 partition

/dev/hdb1 - linux swap partition
/dev/hdb2 - linux root partition (ext3)
/dev/hdb3 - fat32 partition
/dev/hdb4 - another ext3 partition

so, my hda partitions don't get mounted during boot (despite they are listed in fstab), nor can i mount them later (i get the "already mounted or <mounttarget> is busy" message, however, theyre not mounted according to umount and mtab, and i cannot mount them to even a freshly created directory). the two hard disks are on the same standard IDE slot, so i cannot really understand why this is happening. any help?[/QUOTE]
1) If you use GNOME please select the following things from the menu:
System/Administration/Disks

Select the harddisk you can't access
click on the partition tab and tell me what it's written there.

2) I haven't tried 2.6.14.4 yet but did you try with another (older) version of the kernel?

---

### Post by anatole on 2005-12-16
> **tseliot]1) If you use GNOME please select the following things from the menu:
System/Administration/Disks

Select the harddisk you can't access
click on the partition tab and tell me what it's written there.[/QUOTE]

they differ from the working ones at the line "Status:" - it says inaccessible with hda1 and hda2 said:**
> 
2) I haven't tried 2.6.14.4 yet but did you try with another (older) version of the kernel?

i didn't. i will try with 2.6.13, however, if i'll have the time (there would be no point for me in using kernel 2.6.12, as it does not support my raid), and if what i posted above doesn't help.

---

### Post by tseliot on 2005-12-16
[QUOTE=anatole]they differ from the working ones at the line "Status:" - it says inaccessible with hda1 and hda2; when i click one "enable" , nothing happens.



i didn't. i will try with 2.6.13, however, if i'll have the time (there would be no point for me in using kernel 2.6.12, as it does not support my raid), and if what i posted above doesn't help.[/QUOTE]
I have never used two harddisks using raid. Sorry for my ignorance in that field :( 

For this reason I recommend you to start a new thread in the "Hardware Help" section

---

### Post by r4ik on 2005-12-16
For tseliot.
I havent been able to install the kernel.
System just will not install it.(noob thing has nothing to do with the howto)
I managed to install the k7 (synaptic) and i will keep it for a while.
Thanks again for your time and maybe i will return to the
subject when i am more able to compile kernels.
r4ik.

---

### Post by anatole on 2005-12-16
you misunderstood me, the hard drives are on one completely standard ide slot.
the raid support is needed for the cdrom drivers (there are only place on my motherboard there for them) and with the new kernel they work perfectly.

so, the funny thing is, the two hard drives are on the same slot, not raid but ide, and one works, another doesn't...

---

### Post by tseliot on 2005-12-16
[QUOTE=r4ik]For tseliot.
I havent been able to install the kernel.
System just will not install it.(noob thing has nothing to do with the howto)
I managed to install the k7 (synaptic) and i will keep it for a while.
Thanks again for your time and maybe i will return to the
subject when i am more able to compile kernels.
r4ik.[/QUOTE]
Ok. I'm sure you will be able to do it in a near future.

Anyhow if you want to post the output of the error when you try to install the kernel I can try to help you.

---

### Post by tseliot on 2005-12-16
[QUOTE=anatole]you misunderstood me, the hard drives are on one completely standard ide slot.
the raid support is needed for the cdrom drivers (there are only place on my motherboard there for them) and with the new kernel they work perfectly.

so, the funny thing is, the two hard drives are on the same slot, not raid but ide, and one works, another doesn't...[/QUOTE]
Perhaps now that your Cd readers are enabled the system changed the "label" of the other harddisk so that your fstab can be reporting the wrong name of your harddisk.

Please post the output of the following command:
```
dmesg
```

---

### Post by anatole on 2005-12-16
[QUOTE=tseliot]Perhaps now that your Cd readers are enabled the system changed the "label" of the other harddisk so that your fstab can be reporting the wrong name of your harddisk.

Please post the output of the following command:
```
dmesg
```[/QUOTE]

here it is:
```
attila@nanaki:~$ dmesg
ocate resource for EISA slot 8
[17179571.840000] EISA: Detected 0 cards.
[17179571.840000] NET: Registered protocol family 2
[17179572.488000] input: AT Translated Set 2 keyboard on isa0060/serio0
[17179572.500000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.500000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179572.500000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.500000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.500000] TCP reno registered
[17179572.500000] TCP bic registered
[17179572.500000] NET: Registered protocol family 8
[17179572.500000] NET: Registered protocol family 20
[17179572.500000] Using IPI Shortcut mode
[17179572.500000] ACPI wakeup devices: 
[17179572.500000] PCI0 PEX0 PEX1 PEX2 PEX3 PEX4 PEX5 HUB0 USB0 USB1 USB2 USB3 USBE AC97 MC97 AZAL 
[17179572.500000] ACPI: (supports S0 S1 S4 S5)
[17179572.500000] Freeing unused kernel memory: 220k freed
[17179572.512000] vga16fb: initializing
[17179572.512000] vga16fb: mapped to 0xc00a0000
[17179572.728000] Console: switching to colour frame buffer device 80x30
[17179572.728000] fb0: VGA16 VGA frame buffer device
[17179573.892000] NET: Registered protocol family 1
[17179573.904000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.904000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.904000] ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179573.904000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
[17179573.904000] ICH7: chipset revision 1
[17179573.904000] ICH7: not 100% native mode: will probe irqs later
[17179573.904000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
[17179573.904000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[17179573.904000] Probing IDE interface ide0...
[17179574.196000] hda: ST380021A, ATA DISK drive
[17179574.476000] hdb: SAMSUNG SP1604N, ATA DISK drive
[17179574.532000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.532000] Probing IDE interface ide1...
[17179575.108000] SCSI subsystem initialized
[17179575.108000] libata version 1.12 loaded.
[17179575.108000] ata_piix version 1.04
[17179575.108000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[17179575.108000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179575.108000] ata1: SATA max UDMA/133 cmd 0xD000 ctl 0xD402 bmdma 0xE000 irq 18
[17179575.108000] ata2: SATA max UDMA/133 cmd 0xD800 ctl 0xDC02 bmdma 0xE008 irq 18
[17179575.272000] ATA: abnormal status 0x7F on port 0xD007
[17179575.272000] ata1: disabling port
[17179575.272000] scsi0 : ata_piix
[17179575.436000] ATA: abnormal status 0x7F on port 0xD807
[17179575.436000] ata2: disabling port
[17179575.436000] scsi1 : ata_piix
[17179575.440000] Probing IDE interface ide1...
[17179576.008000] hda: max request size: 128KiB
[17179576.008000] hda: Host Protected Area detected.
[17179576.008000]       current capacity is 156299375 sectors (80025 MB)
[17179576.008000]       native  capacity is 156301488 sectors (80026 MB)
[17179576.008000] hda: Host Protected Area disabled.
[17179576.008000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.008000] hda: cache flushes not supported
[17179576.008000]  hda: hda1 hda2
[17179576.028000] hdb: max request size: 1024KiB
[17179576.036000] hdb: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[17179576.036000] hdb: cache flushes supported
[17179576.036000]  hdb: hdb1 hdb2 hdb3 hdb4
[17179576.200000] Attempting manual resume
[17179576.232000] usbcore: registered new driver usbfs
[17179576.232000] usbcore: registered new driver hub
[17179576.232000] USB Universal Host Controller Interface driver v2.3
[17179576.232000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[17179576.232000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.232000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.232000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.232000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bc00
[17179576.236000] hub 1-0:1.0: USB hub found
[17179576.236000] hub 1-0:1.0: 2 ports detected
[17179576.340000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[17179576.340000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.340000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.340000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.340000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000b000
[17179576.340000] hub 2-0:1.0: USB hub found
[17179576.340000] hub 2-0:1.0: 2 ports detected
[17179576.444000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[17179576.444000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.444000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.444000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.444000] uhci_hcd 0000:00:1d.2: irq 17, io base 0x0000b400
[17179576.444000] hub 3-0:1.0: USB hub found
[17179576.444000] hub 3-0:1.0: 2 ports detected
[17179576.548000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[17179576.548000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179576.548000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179576.548000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179576.548000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[17179576.548000] hub 4-0:1.0: USB hub found
[17179576.548000] hub 4-0:1.0: 2 ports detected
[17179576.672000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[17179576.672000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.672000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.672000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179576.672000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe1104000
[17179576.676000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179576.676000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[17179576.676000] hub 5-0:1.0: USB hub found
[17179576.676000] hub 5-0:1.0: 8 ports detected
[17179576.684000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179576.820000] tg3.c:v3.42 (Oct 3, 2005)
[17179576.820000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
[17179576.820000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179576.844000] eth0: Tigon3 [partno(BCM95789) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:14:85:8a:42:9d
[17179576.844000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179576.844000] eth0: dma_rwctrl[76180000]
[17179577.244000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[17179577.984000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[17179578.380000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[17179578.880000] usbcore: registered new driver hiddev
[17179578.896000] input: USB HID v1.10 Keyboard [1267:0103] on usb-0000:00:1d.3-1
[17179578.916000] input: USB HID v1.10 Device [1267:0103] on usb-0000:00:1d.3-1
[17179578.956000] input: USB HID v1.00 Mouse [1241:1166] on usb-0000:00:1d.3-2
[17179578.956000] usbcore: registered new driver usbhid
[17179578.956000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179578.980000] Initializing USB Mass Storage driver...
[17179578.980000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179578.980000] usb-storage: device found at 2
[17179578.980000] usb-storage: waiting for device to settle before scanning
[17179578.980000] usbcore: registered new driver usb-storage
[17179578.980000] USB Mass Storage support registered.
[17179579.288000] ACPI: CPU0 (power states: C1[C1])
[17179579.288000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179579.564000] Attempting manual resume
[17179579.580000] kjournald starting.  Commit interval 5 seconds
[17179579.580000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.548000] md: md driver 0.90.2 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179580.548000] md: bitmap version 3.39
[17179583.188000] Adding 248968k swap on /dev/hdb1.  Priority:-1 extents:1 across:248968k
[17179583.428000] EXT3 FS on hdb2, internal journal
[17179584.024000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17179584.024000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179584.052000] usb-storage: device scan complete
[17179585.540000] parport: PnPBIOS parport detected.
[17179585.540000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179585.640000] lp0: using parport0 (interrupt-driven).
[17179585.668000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17179585.672000] sda: Write Protect is off
[17179585.672000] sda: Mode Sense: 64 00 00 08
[17179585.672000] sda: assuming drive cache: write through
[17179585.680000] mice: PS/2 mouse device common for all mice
[17179585.688000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17179585.704000] sda: Write Protect is off
[17179585.704000] sda: Mode Sense: 64 00 00 08
[17179585.704000] sda: assuming drive cache: write through
[17179585.704000]  sda: sda1 sda2
[17179586.680000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[17179589.816000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179591.968000] device-mapper: dm-linear: Device lookup failed
[17179591.968000] device-mapper: error adding target to table
[17179591.976000] device-mapper: dm-linear: Device lookup failed
[17179591.976000] device-mapper: error adding target to table
[17179591.980000] device-mapper: dm-linear: Device lookup failed
[17179591.980000] device-mapper: error adding target to table
[17179591.988000] device-mapper: dm-linear: Device lookup failed
[17179591.988000] device-mapper: error adding target to table
[17179591.996000] device-mapper: dm-linear: Device lookup failed
[17179591.996000] device-mapper: error adding target to table
[17179591.996000] device-mapper: dm-linear: Device lookup failed
[17179591.996000] device-mapper: error adding target to table
[17179592.000000] device-mapper: dm-linear: Device lookup failed
[17179592.000000] device-mapper: error adding target to table
[17179592.000000] device-mapper: dm-linear: Device lookup failed
[17179592.000000] device-mapper: error adding target to table
[17179592.000000] device-mapper: dm-linear: Device lookup failed
[17179592.000000] device-mapper: error adding target to table
[17179592.004000] device-mapper: dm-linear: Device lookup failed
[17179592.004000] device-mapper: error adding target to table
[17179592.004000] device-mapper: dm-linear: Device lookup failed
[17179592.004000] device-mapper: error adding target to table
[17179592.004000] device-mapper: dm-linear: Device lookup failed
[17179592.004000] device-mapper: error adding target to table
[17179592.008000] device-mapper: dm-linear: Device lookup failed
[17179592.008000] device-mapper: error adding target to table
[17179592.008000] device-mapper: dm-linear: Device lookup failed
[17179592.008000] device-mapper: error adding target to table
[17179592.008000] device-mapper: dm-linear: Device lookup failed
[17179592.008000] device-mapper: error adding target to table
[17179592.012000] device-mapper: dm-linear: Device lookup failed
[17179592.012000] device-mapper: error adding target to table
[17179612.536000] NTFS driver 2.1.24 [Flags: R/O MODULE].
[17179612.552000] kjournald starting.  Commit interval 5 seconds
[17179612.552000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17179612.556000] EXT3 FS on hdb4, internal journal
[17179612.556000] EXT3-fs: mounted filesystem with ordered data mode.
[17179613.952000] Linux agpgart interface v0.101 (c) Dave Jones
[17179614.132000] agpgart: Detected an Intel 945G Chipset.
[17179614.148000] agpgart: AGP aperture is 256M @ 0x0
[17179614.392000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179614.640000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179615.384000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[17179615.384000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179616.100000] hw_random hardware driver 1.0.0 loaded
[17179616.508000] IT8212: IDE controller at PCI slot 0000:04:06.0
[17179616.508000] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 22 (level, low) -> IRQ 20
[17179616.508000] IT8212: chipset revision 19
[17179616.508000] it821x: controller in pass through mode.
[17179616.508000] IT8212: 100% native mode on irq 20
[17179616.508000]     ide2: BM-DMA at 0xa000-0xa007, BIOS settings: hde:pio, hdf:pio
[17179616.508000]     ide3: BM-DMA at 0xa008-0xa00f, BIOS settings: hdg:pio, hdh:pio
[17179616.508000] Probing IDE interface ide2...
[17179617.244000] hde: HL-DT-STDVD-ROM GDR8163B, ATAPI CD/DVD-ROM drive
[17179618.028000] hdf: HL-DT-ST DVDRAM GSA-4160B, ATAPI CD/DVD-ROM drive
[17179618.084000] ide2 at 0x9010-0x9017,0x9402 on irq 20
[17179618.096000] Probing IDE interface ide3...
[17179620.244000] Real Time Clock Driver v1.12
[17179620.284000] input: PC Speaker
[17179620.524000] hde: ATAPI 52X DVD-ROM drive, 256kB Cache
[17179620.524000] Uniform CD-ROM driver Revision: 3.20
[17179620.604000] hdf: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[17179621.044000] ts: Compaq touchscreen protocol output
[17179623.164000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179623.164000] tg3: eth0: Flow control is on for TX and on for RX.
[17179623.928000] NET: Registered protocol family 10
[17179623.928000] Disabled Privacy Extensions on device c02cd820(lo)
[17179623.928000] IPv6 over IPv4 tunneling driver
[17179624.772000] ACPI: Power Button (FF) [PWRF]
[17179624.772000] ACPI: Power Button (CM) [PWRB]
[17179624.788000] Using specific hotkey driver
[17179624.824000] ibm_acpi: ec object not found
[17179624.848000] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[17179632.392000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179632.392000] apm: overridden by ACPI.
[17179633.792000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179633.940000] eth0: no IPv6 routers present
[17179635.120000] Bluetooth: Core ver 2.7
[17179635.120000] NET: Registered protocol family 31
[17179635.120000] Bluetooth: HCI device and connection manager initialized
[17179635.120000] Bluetooth: HCI socket layer initialized
[17179635.152000] Bluetooth: L2CAP ver 2.7
[17179635.152000] Bluetooth: L2CAP socket layer initialized
[17179635.176000] Bluetooth: RFCOMM ver 1.5
[17179635.176000] Bluetooth: RFCOMM socket layer initialized
[17179635.176000] Bluetooth: RFCOMM TTY layer initialized
[17179651.356000] UDF-fs: No VRS found
[17179651.652000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179651.864000] ISOFS: changing to secondary root
[17179697.824000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17179824.124000] cdrom: This disc doesn't have any tracks I recognize!
[17184892.468000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17184892.468000] SGI XFS Quota Management subsystem
[17184892.488000] JFS: nTxBlock = 8099, nTxLock = 64796
[17185112.792000] UDF-fs: No VRS found
[17185112.816000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17185113.044000] ISOFS: changing to secondary root

```

---

### Post by tseliot on 2005-12-16
> **anatole]here it is:
```
attila@nanaki:~$ dmesg
ocate resource for EISA slot 8
[17179571.840000] EISA: Detected 0 cards.
[17179571.840000] NET: Registered protocol family 2
[17179572.488000] input: AT Translated Set 2 keyboard on isa0060/serio0
[17179572.500000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.500000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179572.500000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.500000] TCP: Hash tables configured (established 262144 bind 65536)
[17179572.500000] TCP reno registered
[17179572.500000] TCP bic registered
[17179572.500000] NET: Registered protocol family 8
[17179572.500000] NET: Registered protocol family 20
[17179572.500000] Using IPI Shortcut mode
[17179572.500000] ACPI wakeup devices: 
[17179572.500000] PCI0 PEX0 PEX1 PEX2 PEX3 PEX4 PEX5 HUB0 USB0 USB1 USB2 USB3 USBE AC97 MC97 AZAL 
[17179572.500000] ACPI: (supports S0 S1 S4 S5)
[17179572.500000] Freeing unused kernel memory: 220k freed
[17179572.512000] vga16fb: initializing
[17179572.512000] vga16fb: mapped to 0xc00a0000
[17179572.728000] Console: switching to colour frame buffer device 80x30
[17179572.728000] fb0: VGA16 VGA frame buffer device
[17179573.892000] NET: Registered protocol family 1
[17179573.904000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.904000] ide: Assuming 33MHz system bus speed for PIO modes said:**
>  ICH7: IDE controller at PCI slot 0000:00:1f.1
[17179573.904000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
[17179573.904000] ICH7: chipset revision 1
[17179573.904000] ICH7: not 100% native mode: will probe irqs later
[17179573.904000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
[17179573.904000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[17179573.904000] Probing IDE interface ide0...
[17179574.196000] hda: ST380021A, ATA DISK drive
[17179574.476000] hdb: SAMSUNG SP1604N, ATA DISK drive
[17179574.532000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.532000] Probing IDE interface ide1...
[17179575.108000] SCSI subsystem initialized
[17179575.108000] libata version 1.12 loaded.
[17179575.108000] ata_piix version 1.04
[17179575.108000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 18
[17179575.108000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179575.108000] ata1: SATA max UDMA/133 cmd 0xD000 ctl 0xD402 bmdma 0xE000 irq 18
[17179575.108000] ata2: SATA max UDMA/133 cmd 0xD800 ctl 0xDC02 bmdma 0xE008 irq 18
[17179575.272000] ATA: abnormal status 0x7F on port 0xD007
[17179575.272000] ata1: disabling port
[17179575.272000] scsi0 : ata_piix
[17179575.436000] ATA: abnormal status 0x7F on port 0xD807
[17179575.436000] ata2: disabling port
[17179575.436000] scsi1 : ata_piix
[17179575.440000] Probing IDE interface ide1...
[17179576.008000] hda: max request size: 128KiB
[17179576.008000] hda: Host Protected Area detected.
[17179576.008000]       current capacity is 156299375 sectors (80025 MB)
[17179576.008000]       native  capacity is 156301488 sectors (80026 MB)
[17179576.008000] hda: Host Protected Area disabled.
[17179576.008000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.008000] hda: cache flushes not supported
[17179576.008000]  hda: hda1 hda2
[17179576.028000] hdb: max request size: 1024KiB
[17179576.036000] hdb: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[17179576.036000] hdb: cache flushes supported
[17179576.036000]  hdb: hdb1 hdb2 hdb3 hdb4
[17179576.200000] Attempting manual resume
[17179576.232000] usbcore: registered new driver usbfs
[17179576.232000] usbcore: registered new driver hub
[17179576.232000] USB Universal Host Controller Interface driver v2.3
[17179576.232000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[17179576.232000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.232000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.232000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.232000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000bc00
[17179576.236000] hub 1-0:1.0: USB hub found
[17179576.236000] hub 1-0:1.0: 2 ports detected
[17179576.340000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[17179576.340000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.340000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.340000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.340000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000b000
[17179576.340000] hub 2-0:1.0: USB hub found
[17179576.340000] hub 2-0:1.0: 2 ports detected
[17179576.444000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[17179576.444000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.444000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.444000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.444000] uhci_hcd 0000:00:1d.2: irq 17, io base 0x0000b400
[17179576.444000] hub 3-0:1.0: USB hub found
[17179576.444000] hub 3-0:1.0: 2 ports detected
[17179576.548000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[17179576.548000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179576.548000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179576.548000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179576.548000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[17179576.548000] hub 4-0:1.0: USB hub found
[17179576.548000] hub 4-0:1.0: 2 ports detected
[17179576.672000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[17179576.672000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.672000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.672000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179576.672000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe1104000
[17179576.676000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179576.676000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[17179576.676000] hub 5-0:1.0: USB hub found
[17179576.676000] hub 5-0:1.0: 8 ports detected
[17179576.684000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[17179576.820000] tg3.c:v3.42 (Oct 3, 2005)
[17179576.820000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
[17179576.820000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179576.844000] eth0: Tigon3 [partno(BCM95789) rev 4101 PHY(5750)] (PCI Express) 10/100/1000BaseT Ethernet 00:14:85:8a:42:9d
[17179576.844000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[17179576.844000] eth0: dma_rwctrl[76180000]
[17179577.244000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[17179577.984000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[17179578.380000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[17179578.880000] usbcore: registered new driver hiddev
[17179578.896000] input: USB HID v1.10 Keyboard [1267:0103] on usb-0000:00:1d.3-1
[17179578.916000] input: USB HID v1.10 Device [1267:0103] on usb-0000:00:1d.3-1
[17179578.956000] input: USB HID v1.00 Mouse [1241:1166] on usb-0000:00:1d.3-2
[17179578.956000] usbcore: registered new driver usbhid
[17179578.956000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179578.980000] Initializing USB Mass Storage driver...
[17179578.980000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179578.980000] usb-storage: device found at 2
[17179578.980000] usb-storage: waiting for device to settle before scanning
[17179578.980000] usbcore: registered new driver usb-storage
[17179578.980000] USB Mass Storage support registered.
[17179579.288000] ACPI: CPU0 (power states: C1[C1])
[17179579.288000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179579.564000] Attempting manual resume
[17179579.580000] kjournald starting.  Commit interval 5 seconds
[17179579.580000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.548000] md: md driver 0.90.2 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179580.548000] md: bitmap version 3.39
[17179583.188000] Adding 248968k swap on /dev/hdb1.  Priority:-1 extents:1 across:248968k
[17179583.428000] EXT3 FS on hdb2, internal journal
[17179584.024000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17179584.024000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179584.052000] usb-storage: device scan complete
[17179585.540000] parport: PnPBIOS parport detected.
[17179585.540000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179585.640000] lp0: using parport0 (interrupt-driven).
[17179585.668000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17179585.672000] sda: Write Protect is off
[17179585.672000] sda: Mode Sense: 64 00 00 08
[17179585.672000] sda: assuming drive cache: write through
[17179585.680000] mice: PS/2 mouse device common for all mice
[17179585.688000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[17179585.704000] sda: Write Protect is off
[17179585.704000] sda: Mode Sense: 64 00 00 08
[17179585.704000] sda: assuming drive cache: write through
[17179585.704000]  sda: sda1 sda2
[17179586.680000] Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
[17179589.816000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179591.968000] device-mapper: dm-linear: Device lookup failed
[17179591.968000] device-mapper: error adding target to table
[17179591.976000] device-mapper: dm-linear: Device lookup failed
[17179591.976000] device-mapper: error adding target to table
[17179591.980000] device-mapper: dm-linear: Device lookup failed
[17179591.980000] device-mapper: error adding target to table
[17179591.988000] device-mapper: dm-linear: Device lookup failed
[17179591.988000] device-mapper: error adding target to table
[17179591.996000] device-mapper: dm-linear: Device lookup failed
[17179591.996000] device-mapper: error adding target to table
[17179591.996000] device-mapper: dm-linear: Device lookup failed
[17179591.996000] device-mapper: error adding target to table
[17179592.000000] device-mapper: dm-linear: Device lookup failed
[17179592.000000] device-mapper: error adding target to table
[17179592.000000] device-mapper: dm-linear: Device lookup failed
[17179592.000000] device-mapper: error adding target to table
[17179592.000000] device-mapper: dm-linear: Device lookup failed
[17179592.000000] device-mapper: error adding target to table
[17179592.004000] device-mapper: dm-linear: Device lookup failed
[17179592.004000] device-mapper: error adding target to table
[17179592.004000] device-mapper: dm-linear: Device lookup failed
[17179592.004000] device-mapper: error adding target to table
[17179592.004000] device-mapper: dm-linear: Device lookup failed
[17179592.004000] device-mapper: error adding target to table
[17179592.008000] device-mapper: dm-linear: Device lookup failed
[17179592.008000] device-mapper: error adding target to table
[17179592.008000] device-mapper: dm-linear: Device lookup failed
[17179592.008000] device-mapper: error adding target to table
[17179592.008000] device-mapper: dm-linear: Device lookup failed
[17179592.008000] device-mapper: error adding target to table
[17179592.012000] device-mapper: dm-linear: Device lookup failed
[17179592.012000] device-mapper: error adding target to table
[17179612.536000] NTFS driver 2.1.24 [Flags: R/O MODULE].
[17179612.552000] kjournald starting.  Commit interval 5 seconds
[17179612.552000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17179612.556000] EXT3 FS on hdb4, internal journal
[17179612.556000] EXT3-fs: mounted filesystem with ordered data mode.
[17179613.952000] Linux agpgart interface v0.101 (c) Dave Jones
[17179614.132000] agpgart: Detected an Intel 945G Chipset.
[17179614.148000] agpgart: AGP aperture is 256M @ 0x0
[17179614.392000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179614.640000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179615.384000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[17179615.384000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179616.100000] hw_random hardware driver 1.0.0 loaded
[17179616.508000] IT8212: IDE controller at PCI slot 0000:04:06.0
[17179616.508000] ACPI: PCI Interrupt 0000:04:06.0[A] -> GSI 22 (level, low) -> IRQ 20
[17179616.508000] IT8212: chipset revision 19
[17179616.508000] it821x: controller in pass through mode.
[17179616.508000] IT8212: 100% native mode on irq 20
[17179616.508000]     ide2: BM-DMA at 0xa000-0xa007, BIOS settings: hde:pio, hdf:pio
[17179616.508000]     ide3: BM-DMA at 0xa008-0xa00f, BIOS settings: hdg:pio, hdh:pio
[17179616.508000] Probing IDE interface ide2...
[17179617.244000] hde: HL-DT-STDVD-ROM GDR8163B, ATAPI CD/DVD-ROM drive
[17179618.028000] hdf: HL-DT-ST DVDRAM GSA-4160B, ATAPI CD/DVD-ROM drive
[17179618.084000] ide2 at 0x9010-0x9017,0x9402 on irq 20
[17179618.096000] Probing IDE interface ide3...
[17179620.244000] Real Time Clock Driver v1.12
[17179620.284000] input: PC Speaker
[17179620.524000] hde: ATAPI 52X DVD-ROM drive, 256kB Cache
[17179620.524000] Uniform CD-ROM driver Revision: 3.20
[17179620.604000] hdf: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[17179621.044000] ts: Compaq touchscreen protocol output
[17179623.164000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179623.164000] tg3: eth0: Flow control is on for TX and on for RX.
[17179623.928000] NET: Registered protocol family 10
[17179623.928000] Disabled Privacy Extensions on device c02cd820(lo)
[17179623.928000] IPv6 over IPv4 tunneling driver
[17179624.772000] ACPI: Power Button (FF) [PWRF]
[17179624.772000] ACPI: Power Button (CM) [PWRB]
[17179624.788000] Using specific hotkey driver
[17179624.824000] ibm_acpi: ec object not found
[17179624.848000] toshiba_acpi: Unknown parameter `hotkeys_over_acpi'
[17179632.392000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179632.392000] apm: overridden by ACPI.
[17179633.792000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179633.940000] eth0: no IPv6 routers present
[17179635.120000] Bluetooth: Core ver 2.7
[17179635.120000] NET: Registered protocol family 31
[17179635.120000] Bluetooth: HCI device and connection manager initialized
[17179635.120000] Bluetooth: HCI socket layer initialized
[17179635.152000] Bluetooth: L2CAP ver 2.7
[17179635.152000] Bluetooth: L2CAP socket layer initialized
[17179635.176000] Bluetooth: RFCOMM ver 1.5
[17179635.176000] Bluetooth: RFCOMM socket layer initialized
[17179635.176000] Bluetooth: RFCOMM TTY layer initialized
[17179651.356000] UDF-fs: No VRS found
[17179651.652000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179651.864000] ISOFS: changing to secondary root
[17179697.824000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17179824.124000] cdrom: This disc doesn't have any tracks I recognize!
[17184892.468000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17184892.468000] SGI XFS Quota Management subsystem
[17184892.488000] JFS: nTxBlock = 8099, nTxLock = 64796
[17185112.792000] UDF-fs: No VRS found
[17185112.816000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17185113.044000] ISOFS: changing to secondary root

```
Another question:
Did you patch the kernel (if yes, specify which)?

---

### Post by anatole on 2005-12-16
[QUOTE=tseliot]Another question:
Did you patch the kernel (if yes, specify which)?[/QUOTE]

no. to be honest i didn't quite understand why would i want to patch the newest stable kernel :) this was my first kernel compilation afterall.

---

### Post by tseliot on 2005-12-16
[QUOTE=anatole]no. to be honest i didn't quite understand why would i want to patch the newest stable kernel :) this was my first kernel compilation afterall.[/QUOTE]
Kolivas patches contain improvements. Please try the patch (yes, delete the folder with the kernel source you used and recompile your kernel from scratch, follow the guide), it might solve your problem

---

### Post by anatole on 2005-12-16
[QUOTE=tseliot]Kolivas patches contain improvements. Please try the patch (yes, delete the folder with the kernel source you used and recompile your kernel from scratch, follow the guide), it might solve your problem[/QUOTE]
tried it. the patching (both with ck3 and ck7, i tried those) makes errors, then so the kernel complilng... :/

---

### Post by tseliot on 2005-12-16
[QUOTE=anatole]tried it. the patching (both with ck3 and ck7, i tried those) makes errors, then so the kernel complilng... :/[/QUOTE]
I know, I apologise for not mentioning a little detail:
If you need to use Kolivas Patch you have to apply it to kernel 2.6.14 (not on 2.6.14.4) because the patch already contains the improvements of the latest version.

In other words:
1) Download the following patch [http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck7/patch-2.6.14-ck7.bz2]("http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck7/patch-2.6.14-ck7.bz2")

2) Download the kernel source: [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2")


and try again

---

### Post by anatole on 2005-12-16
[QUOTE=tseliot]I know, I apologise for not mentioning a little detail:
If you need to use Kolivas Patch you have to apply it to kernel 2.6.14 (not on 2.6.14.4) because the patch already contains the improvements of the latest version.

In other words:
1) Download the following patch [http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck7/patch-2.6.14-ck7.bz2]("http://ck.kolivas.org/patches/2.6/2.6.14/2.6.14-ck7/patch-2.6.14-ck7.bz2")

2) Download the kernel source: [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2]("http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.14.tar.bz2")


and try again[/QUOTE]


it fails with:
```
kernel/resource.c:480: warning: '__check_region' is deprecated (declared at kernel/resource.c:468)
  CC      kernel/sysctl.o
kernel/sysctl.c: In function 'register_proc_table':
kernel/sysctl.c:1413: error: 'struct proc_dir_entry' has no member named 'set'
kernel/sysctl.c: In function 'do_rw_proc':
kernel/sysctl.c:1471: error: 'struct proc_dir_entry' has no member named 'set'
kernel/sysctl.c:1493: error: 'struct proc_dir_entry' has no member named 'set'
make[2]: *** [kernel/sysctl.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14'
make: *** [stamp-build] Error 2

```

---

### Post by tseliot on 2005-12-16
[QUOTE=anatole]it fails with:
```
kernel/resource.c:480: warning: '__check_region' is deprecated (declared at kernel/resource.c:468)
  CC      kernel/sysctl.o
kernel/sysctl.c: In function 'register_proc_table':
kernel/sysctl.c:1413: error: 'struct proc_dir_entry' has no member named 'set'
kernel/sysctl.c: In function 'do_rw_proc':
kernel/sysctl.c:1471: error: 'struct proc_dir_entry' has no member named 'set'
kernel/sysctl.c:1493: error: 'struct proc_dir_entry' has no member named 'set'
make[2]: *** [kernel/sysctl.o] Error 1
make[1]: *** [kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.14'
make: *** [stamp-build] Error 2

```[/QUOTE]
Weird...
Can you post the output of "lspci" and "lsmod"?

---

### Post by anatole on 2005-12-16
[QUOTE=tseliot]Weird...
Can you post the output of "lspci" and "lsmod"?[/QUOTE]
lspci:
```
0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770 (rev 81)
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771 (rev 81)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corp.: Unknown device 27d4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 014f (rev a2)
0000:03:00.0 Ethernet controller: Broadcom Corporation: Unknown device 169d (rev 11)
0000:04:06.0 Unknown mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 13) 
```

lsmod:
```
bluetooth              41988  4 rfcomm,l2cap
acpi_cpufreq            6664  1 
cpufreq_userspace       4444  1 
cpufreq_stats           5124  0 
freq_table              4484  2 acpi_cpufreq,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6172  0 
cpufreq_conservative     6948  0 
video                  16260  0 
button                  6672  0 
battery                 9732  0 
container               4608  0 
ac                      4996  0 
ipv6                  220032  14 
tsdev                   7232  0 
ide_cd                 36996  1 
cdrom                  33568  1 ide_cd
pcspkr                  3680  0 
rtc                    11704  1 snd_rtctimer
it821x                  8068  0 [permanent]
tpm_atmel               5760  0 
tpm_nsc                 6528  0 
tpm                     9632  2 tpm_atmel,tpm_nsc
hw_random               5268  0 
snd_hda_intel          16640  4 
snd_hda_codec          77056  1 snd_hda_intel
snd_pcm_oss            45856  0 
snd_mixer_oss          16000  2 snd_pcm_oss
snd_pcm                77832  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_page_alloc         10248  2 snd_hda_intel,snd_pcm
shpchp                 80740  0 
pci_hotplug            24756  1 shpchp
intel_agp              21148  1 
agpgart                31688  1 intel_agp
ntfs                   86896  0 
nls_iso8859_1           4224  1 
nls_cp437               5888  2 
vfat                   11904  1 
fat                    46364  1 vfat
dm_mod                 49980  1 
snd_seq_dummy           3844  0 
snd_seq_oss            29056  0 
snd_seq_midi            8608  0 
snd_rawmidi            22432  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44304  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21636  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    47460  15 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  2 snd
psmouse                33156  0 
mousedev               10528  1 
sd_mod                 16784  1 
parport_pc             32324  1 
lp                     10820  0 
parport                31944  2 parport_pc,lp
md_mod                 56656  0 
thermal                13576  0 
processor              23100  2 acpi_cpufreq,thermal
fan                     4868  0 
usb_storage            64704  2 
usbhid                 31968  0 
tg3                    88580  0 
ehci_hcd               29832  0 
uhci_hcd               28304  0 
usbcore               105600  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_disk               16256  6 
ide_generic             1408  0 [permanent]
ata_piix                9092  0 
libata                 43784  1 ata_piix
scsi_mod              126312  3 sd_mod,usb_storage,libata
piix                    9220  0 [permanent]
generic                 4612  0 [permanent]
ide_core              112480  7 ide_cd,it821x,usb_storage,ide_disk,ide_generic,piix,generic
unix                   24496  314 
vga16fb                11848  1 
vgastate                8320  1 vga16fb
softcursor              2304  1 vga16fb
cfbimgblt               3072  1 vga16fb
cfbfillrect             3840  1 vga16fb
cfbcopyarea             3584  1 vga16fb
fbcon                  35712  72 
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 4992  1 fbcon
```

thanks for all the effort by the way :)

---

### Post by tseliot on 2005-12-17
[QUOTE=anatole]lspci:
```
0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770 (rev 81)
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771 (rev 81)
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corp.: Unknown device 27d4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b8 (rev 01)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 01)
0000:00:1f.2 IDE interface: Intel Corp.: Unknown device 27c0 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 014f (rev a2)
0000:03:00.0 Ethernet controller: Broadcom Corporation: Unknown device 169d (rev 11)
0000:04:06.0 Unknown mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (PCI version seems to be IT8212, embedded seems (rev 13) 
```

lsmod:
```
bluetooth              41988  4 rfcomm,l2cap
acpi_cpufreq            6664  1 
cpufreq_userspace       4444  1 
cpufreq_stats           5124  0 
freq_table              4484  2 acpi_cpufreq,cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        6172  0 
cpufreq_conservative     6948  0 
video                  16260  0 
button                  6672  0 
battery                 9732  0 
container               4608  0 
ac                      4996  0 
ipv6                  220032  14 
tsdev                   7232  0 
ide_cd                 36996  1 
cdrom                  33568  1 ide_cd
pcspkr                  3680  0 
rtc                    11704  1 snd_rtctimer
it821x                  8068  0 [permanent]
tpm_atmel               5760  0 
tpm_nsc                 6528  0 
tpm                     9632  2 tpm_atmel,tpm_nsc
hw_random               5268  0 
snd_hda_intel          16640  4 
snd_hda_codec          77056  1 snd_hda_intel
snd_pcm_oss            45856  0 
snd_mixer_oss          16000  2 snd_pcm_oss
snd_pcm                77832  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_page_alloc         10248  2 snd_hda_intel,snd_pcm
shpchp                 80740  0 
pci_hotplug            24756  1 shpchp
intel_agp              21148  1 
agpgart                31688  1 intel_agp
ntfs                   86896  0 
nls_iso8859_1           4224  1 
nls_cp437               5888  2 
vfat                   11904  1 
fat                    46364  1 vfat
dm_mod                 49980  1 
snd_seq_dummy           3844  0 
snd_seq_oss            29056  0 
snd_seq_midi            8608  0 
snd_rawmidi            22432  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44304  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21636  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    47460  15 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  2 snd
psmouse                33156  0 
mousedev               10528  1 
sd_mod                 16784  1 
parport_pc             32324  1 
lp                     10820  0 
parport                31944  2 parport_pc,lp
md_mod                 56656  0 
thermal                13576  0 
processor              23100  2 acpi_cpufreq,thermal
fan                     4868  0 
usb_storage            64704  2 
usbhid                 31968  0 
tg3                    88580  0 
ehci_hcd               29832  0 
uhci_hcd               28304  0 
usbcore               105600  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_disk               16256  6 
ide_generic             1408  0 [permanent]
ata_piix                9092  0 
libata                 43784  1 ata_piix
scsi_mod              126312  3 sd_mod,usb_storage,libata
piix                    9220  0 [permanent]
generic                 4612  0 [permanent]
ide_core              112480  7 ide_cd,it821x,usb_storage,ide_disk,ide_generic,piix,generic
unix                   24496  314 
vga16fb                11848  1 
vgastate                8320  1 vga16fb
softcursor              2304  1 vga16fb
cfbimgblt               3072  1 vga16fb
cfbfillrect             3840  1 vga16fb
cfbcopyarea             3584  1 vga16fb
fbcon                  35712  72 
tileblit                2432  1 fbcon
font                    8320  1 fbcon
bitblit                 4992  1 fbcon
```

thanks for all the effort by the way :)[/QUOTE]
Unless I'm missing something I guess everything's ok.
I can only ask you 2 things:
1) Have a look at your bios and see if all the devices are detected (but I think they are)
2) Start a new thread in the "Hardware help" section because I have never experienced your problem therefore I can't think of a solution.

---

### Post by Rob2687 on 2005-12-17
[QUOTE=tseliot]
If you need to use Kolivas Patch you have to apply it to kernel 2.6.14 (not on 2.6.14.4) because the patch already contains the improvements of the latest version.[/QUOTE]

You should mention that specifically in the guide. I remember the first few times I tried to compile with those patches I had that problem until I read it on another forum.

---

### Post by tseliot on 2005-12-17
[QUOTE=Rob2687]You should mention that specifically in the guide. I remember the first few times I tried to compile with those patches I had that problem until I read it on another forum.[/QUOTE]
I know, I did that yesterday

---

### Post by MichaelM on 2005-12-17
Question:
Is there any advantage (speed or otherwise) to compiling things (like drivers which aren't needed in the bootstrap process) directly into the kernel instead of as modules?

---

### Post by tseliot on 2005-12-17
[QUOTE=MichaelM]Question:
Is there any advantage (speed or otherwise) to compiling things (like drivers which aren't needed in the bootstrap process) directly into the kernel instead of as modules?[/QUOTE]
Perhaps it can increase the speed of the kernel compilation. If you want a real speed boost (shorter boot times) you can disable the support for all the drivers which are not relevant to your configuration (e.g. disable the support for chipsets of other motherboards, etc.)

---

### Post by ubuntu4everyone on 2005-12-18
Ok, i followed this tutorial and its great, so i made a script to do it all for us, just set the execute permission and in terminal when you are in the directory of the script type ./tweak. This is designed tu be run as a su'ed root, for exalmple

user@ubuntu$su
root@ubuntu$./tweak

by the way whay when you download this rename it from .txt to .sh

hope this helps.

:) :cool:

---

### Post by tseliot on 2005-12-18
[QUOTE=ubuntu4everyone]Ok, i followed this tutorial and its great, so i made a script to do it all for us, just set the execute permission and in terminal when you are in the directory of the script type ./tweak. This is designed tu be run as a su'ed root, for exalmple

user@ubuntu$su
root@ubuntu$./tweak

by the way whay when you download this rename it from .txt to .sh

hope this helps.

:) :cool:[/QUOTE]
Ok, that's a nice script but ,you know, I have two suggestions:
1) This line... :
```
sudo make-kpkg --initrd --append-to-version=-tweaked_image kernel_headers modules_image
```

...shouldn't be like the following?
```
sudo make-kpkg --initrd --append-to-version=-tweaked kernel_image kernel_headers modules_image
```

I don't know if it's the same (but maybe I'm wrong).

2) This suggestion is thought just to bother you ;) :
Could you add the possibility to download the nvidia kernel source (make the users choose between "nvidia" and "nvidia-legacy") and to extract it.
The "modules_image" in the command in point 1 will do the rest.

3) I can't program (never tried but I can learn) therefore I have to ask you the following things (I have some projects on my mind):
a) How did you do the script?
b) Which programming language should I learn in order to do scripts like yours (yes I am that ignorant :p )?
c) Could you address me to a good guide?

---

### Post by ubuntu4everyone on 2005-12-18
[QUOTE=tseliot]Ok, that's a nice script but ,you know, I have two suggestions:
1) This line... :
```
sudo make-kpkg --initrd --append-to-version=-tweaked_image kernel_headers modules_image
```

...shouldn't be like the following?
```
sudo make-kpkg --initrd --append-to-version=-tweaked kernel_image kernel_headers modules_image
```

I don't know if it's the same (but maybe I'm wrong).

2) This suggestion is thought just to bother you ;) :
Could you add the possibility to download the nvidia kernel source (make the users choose between "nvidia" and "nvidia-legacy") and to extract it.
The "modules_image" in the command in point 1 will do the rest.

3) I can't program (never tried but I can learn) therefore I have to ask you the following things (I have some projects on my mind):
a) How did you do the script?
b) Which programming language should I learn in order to do scripts like yours (yes I am that ignorant :p )?
c) Could you address me to a good guide?[/QUOTE]

Hi,
I checked the program, and the current  code is fine, also in regards to the nvida idea i will try, but i am still learning shell script. so i will learn more and then add it

the language i am using is called shell scripting, this is a good tut : [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

hope this helps

---

### Post by tseliot on 2005-12-18
thanks :)

---

### Post by Cuppa-Chino on 2005-12-18
hi, just short question:

```
@ubuntu:~$ sudo apt-get install libncurses5
Reading package lists... Done
Building dependency tree... Done
libncurses5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
johnny@ubuntu:~$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libncurses5-dev: Depends: libncurses5 (= 5.4-9ubuntu4) but 5.5-1ubuntu2 is to be installed
E: Broken packages

```

shall I force the installation despite not having a match between the two versions?
thx

---

### Post by tseliot on 2005-12-18
[QUOTE=Cuppa-Chino]hi, just short question:

```
@ubuntu:~$ sudo apt-get install libncurses5
Reading package lists... Done
Building dependency tree... Done
libncurses5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
johnny@ubuntu:~$ sudo apt-get install libncurses5-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libncurses5-dev: Depends: libncurses5 (= 5.4-9ubuntu4) but 5.5-1ubuntu2 is to be installed
E: Broken packages

```

shall I force the installation despite not having a match between the two versions?
thx[/QUOTE]
please post your /etc/apt/sources.list

---

### Post by Cuppa-Chino on 2005-12-18
[QUOTE=tseliot]please post your /etc/apt/sources.list[/QUOTE]

here goes:
```
#deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20051214)]/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
## created by arniebackports

```

tried creating with the wrong version but that did not work:
```
johnny@ubuntu:/usr/src/linux$ sudo make menuconfig   HOSTLD  scripts/kconfig/mconf
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

make[2]: *** [scripts/lxdialog/ncurses] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2

```

---

### Post by tseliot on 2005-12-18
[QUOTE=Cuppa-Chino]here goes:
```
#deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20051214)]/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
## created by arniebackports

```

tried creating with the wrong version but that did not work:
```
johnny@ubuntu:/usr/src/linux$ sudo make menuconfig   HOSTLD  scripts/kconfig/mconf
/usr/bin/ld: cannot find -lncurses
collect2: ld returned 1 exit status

>> Unable to find the Ncurses libraries.
>>
>> You must install ncurses-devel in order
>> to use 'make menuconfig'

make[2]: *** [scripts/lxdialog/ncurses] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2

```[/QUOTE]
1)You should not keep the backports enabled all the time. Comment out the backports and anything which is other than the official repositories.

2)Anyhow, why do you have this line? 
#deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20051214)]/ dapper main rest

---

### Post by Cuppa-Chino on 2005-12-18
[QUOTE=tseliot]1)You should not keep the backports enabled all the time. Comment out the backports and anything which is other than the official repositories.

2)Anyhow, why do you have this line? 
#deb cdrom:[Ubuntu 6.04 _Dapper Drake_ - Alpha i386 (20051214)]/ dapper main rest[/QUOTE]

1) did that does not change anything still have libncurses 5.5.1 & still get: 
libncurses5-dev:
  Depends: libncurses5 (=5.4-9ubuntu4) but 5.5-1ubuntu2 is to be installed

2) had a dapper CD in the drive and that is how that got there

please help me

---

### Post by tseliot on 2005-12-18
[QUOTE=Cuppa-Chino]1) did that does not change anything still have libncurses 5.5.1 & still get: 
libncurses5-dev:
  Depends: libncurses5 (=5.4-9ubuntu4) but 5.5-1ubuntu2 is to be installed

2) had a dapper CD in the drive and that is how that got there

please help me[/QUOTE]
Ok, make your sources.list look EXACTLY like mine:
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
```

Then uninstall libncurses5-dev (i.e. "Mark it for Complete Removal in Synaptics") if you already have it

And force the installation of the libncurses you need
sudo apt-get install --force-overwrite libncurses5 libncurses5-dev

---

### Post by Cuppa-Chino on 2005-12-18
sorry to be a pain but:

```
@ubuntu:~$ sudo apt-get install -force-overwrite libncurses5 libncurses5-dev
E: Option -force-overwrite: Configuration item specification must have an =<val>.

```

is what is happening for me

---

### Post by tseliot on 2005-12-18
[QUOTE=Cuppa-Chino]sorry to be a pain but:

```
@ubuntu:~$ sudo apt-get install -force-overwrite libncurses5
E: Option -force-overwrite: Configuration item specification must have an =<val>.

```

is what is happening for me[/QUOTE]
EDIT:Ok, try this
 
[COLOR="Red"]sudo apt-get install -force-downgrade libncurses5 [5.4-9][/COLOR]

---

### Post by Cuppa-Chino on 2005-12-18
still no luck...

```
@ubuntu:~$ sudo apt-get install -force-overwrite libncurses5
E: Option -force-overwrite: Configuration item specification must have an =<val>.
@ubuntu:~$
@ubuntu:~$ sudo apt-get install -force-downgrade libncurses5 [5.4-9]
E: Option -force-downgrade: Configuration item specification must have an =<val>.

```

---

### Post by tseliot on 2005-12-18
[QUOTE=Cuppa-Chino]still no luck...

```
@ubuntu:~$ sudo apt-get install -force-overwrite libncurses5
E: Option -force-overwrite: Configuration item specification must have an =<val>.
@ubuntu:~$
@ubuntu:~$ sudo apt-get install -force-downgrade libncurses5 [5.4-9]
E: Option -force-downgrade: Configuration item specification must have an =<val>.

```[/QUOTE]
Ok, I've never done that. I'll look for a solution using google.
I'll let you know

---

### Post by tseliot on 2005-12-18
Try this:

sudo apt-get install -force-overwrite libncurses5=5.4-9ubuntu4

[COLOR="Red"]EDIT: if it doesn't work you have to open Synaptic select "Edit" and then "Fix Broken Packages" then click on the "Apply button"[/COLOR]

---

### Post by Cuppa-Chino on 2005-12-18
found a copy of both libncurses5-dev_5.5-1ubuntu2_i386.deb and ibncurses5_5.4-9ubuntu4_i386.deb
[stanford mirror]("http://mirror.stanford.edu/yum/pub/ubuntu/pool/main/n/ncurses/?C=M;O=D")

have installed libncurses5-dev_5.5-1ubuntu2_i386.deb and will see if it works

_**I get the menu!**_

I spent lots of time in the menu but could not really get anywhere from there....

took the modules I wanted:

7) DO THIS ONLY IF YOU NEED SOME RESTRICTED MODULE otherwise go to Point 8
_ndiswrapper & wpa_supplicant _ - extracted them in usr/src and then tried to sudo make-kpkg clean there but kernel complained 
could find an answer so I tried doing it in usr/src/linux

```
/usr/bin/make -f /usr/share/kernel-package/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686-smp'
test ! -f .config || cp -pf .config config.precious
test -f Makefile && \
            /usr/bin/make    ARCH=i386 distclean
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686-smp'
fs/hostfs/Makefile:11: arch/um/scripts/Makefile.rules: No such file or directorymake[4]: *** No rule to make target `arch/um/scripts/Makefile.rules'.  Stop.
make[3]: *** [fs/hostfs] Error 2
make[2]: *** [_clean_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686-smp'
make[1]: [real_stamp_clean] Error 2 (ignored)
test ! -f config.precious || mv -f config.precious .config
test ! -f stamp-patch || /usr/bin/make -f /usr/share/kernel-package/rules unpatch_now
test -f stamp-building || test -f debian/official || rm -rf debian
# work around idiocy in recent kernel versions
test ! -e scripts/package/builddeb.dist || \
            mv -f scripts/package/builddeb.dist scripts/package/builddeb
test ! -e scripts/package/Makefile.dist || \
            mv -f scripts/package/Makefile.dist scripts/package/Makefile
rm -f modules/modversions.h modules/ksyms.ver debian/files conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches debian/buildinfo stamp-build stamp-configure stamp-source stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-buildpackage stamp-libc-kheaders stamp-debian stamp-patch stamp-kernel-configure
rm -rf debian/tmp-source debian/tmp-headers debian/tmp-image debian/tmp-doc
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686-smp'

```

then just as I have been trying all evening tried to get the kernel running:
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image

```
make[2]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make[1]: *** [init] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686-smp'
make: *** [stamp-build] Error 2

```
is what came from my sudo make-kpkg --initrd –append-to-version=-alberto kernel_image kernel_headers command...

it looks like I will have to try this another day - seems that I end up in my installed 686smp kernel there somewhere, did I maybe not link the directories right? I did not have an error message though....

---

### Post by tseliot on 2005-12-19
> **Cuppa-Chino]found a copy of both libncurses5-dev_5.5-1ubuntu2_i386.deb and ibncurses5_5.4-9ubuntu4_i386.deb
[URL="http://mirror.stanford.edu/yum/pub/ubuntu/pool/main/n/ncurses/?C=M said:**
> stanford mirror[/URL]

have installed libncurses5-dev_5.5-1ubuntu2_i386.deb and will see if it works

_**I get the menu!**_

I spent lots of time in the menu but could not really get anywhere from there....
1) Which menu? The one which appears when you do sudo make menuconfig?
took the modules I wanted:
2) which modules did you enable and why?

3) About ndiswrapper: it should work with kernel 2.6.12. Therefore do this:
cd /usr/src
ls  (and post the output)

---

### Post by ShirishAg75 on 2005-12-20
Hi all,
        I had done a compilation of the kernel long time ago. Was using Mandrake then at that time. No forums or stuff so it was difficult. Had to use help of friends. Anyway nice thread & happy to see the content of the thread. Read through the whole of 20 pages & have few questions. My questions are in parts:-
 First of, my output from lspci & lsmod :-
lspci
```
0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controll er/Host-Hub Interface (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Ch ipset Integrated Graphics Device (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 0 2)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 I DE Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 02)
0000:03:01.0 Modem: PCTel Inc: Unknown device 2189 (rev 04)
0000:03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)

```
lsmod :-
```
Module                  Size  Used by
isofs                  32824  1
udf                    75524  0
ipv6                  217408  6
i915                   17920  1
drm                    58004  2 i915
tc1100_wmi              6916  0
video                  16004  0
battery                 9604  0
container               4608  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
pcc_acpi               11392  0
sony_acpi               5516  0
ac                      4996  0
dev_acpi               11396  0
hotkey                  9508  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_intel8x0           30144  2
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  1
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_nsc                 6528  0
tpm_atmel               5504  0
tpm                     9504  2 tpm_nsc,tpm_atmel
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
nls_iso8859_1           4224  8
nls_cp437               5888  9
vfat                   12288  8
fat                    46492  1 vfat
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
reiserfs              217200  2
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
8139cp                 18432  0
8139too                23552  0
mii                     5248  2 8139cp,8139too
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  3 ehci_hcd,uhci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  12
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  605
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

Also something from /boot/grub :- There is no compilation as of yet just whatever installation happened through apt-get

```
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,11)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda12 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,11)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda12 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

#title          Ubuntu, kernel 2.6.12-9-386
#root           (hd0,11)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hda12 ro quiet splash
#initrd         /boot/initrd.img-2.6.12-9-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.12-9-386 (recovery mode)
#root           (hd0,11)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hda12 ro single
#initrd         /boot/initrd.img-2.6.12-9-386
#boot

title           Ubuntu, memtest86+
root            (hd0,11)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by ShirishAg75 on 2005-12-20
Now question time 
1. I've a p4 1.8 ghz I remember using i686 while compiling on mandrake. Why is this not used ? The processor family is i386 but would like to use the best that can be done.
Would like to use ubuntu kernel rather than anything from kernel.org or kovlias patches simply for the fact that it's my first kernel compilation on ubuntu/debian. 
2.  uname -r gives 2.6.12-10-386 so how do I uninstall the kernel 2.6.12-9-38 as well as the recovery mode. 
3. What is this ndiswrapper module, something to do with wireless or what? I saw this being mentioned again & again.
4. My usage would be just a good desktop, gaming, internet, multimedia & some graphics. Memory is 128 MB DDR but would be upgrading to 1 GB but in few months not now, hence what steps should I take in memory high support?
                   Thnx in advance. Hope to get some answers haven't started any compilations as yet, would do the same after some advice/suggestions from u. Would like to disable stuff which I don't use like digital cameras, no firewire support would like to have USB support as think to have a USB thumbdrive in couple of months.

---

### Post by tseliot on 2005-12-20
[QUOTE=shirishag75]Now question time 
1. I've a p4 1.8 ghz I remember using i686 while compiling on mandrake. Why is this not used ? The processor family is i386 but would like to use the best that can be done.[/QUOTE]
Why don't you install kernel for 686 processors in Synaptic/Kynaptic? Have a look at this guide [Picking the Kernel thats Right for You (Possible Speed Increase)]("http://ubuntuforums.org/showthread.php?t=85917")

[QUOTE=shirishag75]Would like to use ubuntu kernel rather than anything from kernel.org or kovlias patches simply for the fact that it's my first kernel compilation on ubuntu/debian.[/QUOTE]
I agree with you because this is what I usually do.

[QUOTE=shirishag75]2.  uname -r gives 2.6.12-10-386 so how do I uninstall the kernel 2.6.12-9-38 as well as the recovery mode.[/QUOTE]
About your old kernel (2.6.12-9-386): the easiest way to remove it is to:
open Synaptic/Kynaptic
type "linux" in the search field and press search
you will get a list, look for "linux-image-2.6.12-9-386" and mark it for complete removal

OR

a fastest way to do that is:
```
sudo dpkg -r linux-image-2.6.12-9-386
```

[QUOTE=shirishag75]3. What is this ndiswrapper module, something to do with wireless or what? I saw this being mentioned again & again.[/QUOTE]
If you have a wireless modem which needs Windows drivers to work you need ndiswrapper. (I've never used it)

[QUOTE=shirishag75]4. My usage would be just a good desktop, gaming, internet, multimedia & some graphics. Memory is 128 MB DDR but would be upgrading to 1 GB but in few months not now, hence what steps should I take in memory high support?[/QUOTE]
4GB of RAM is the maximum supported by default by Ubuntu Breezy's kernels and I suggest you to leave it as it is.

[QUOTE=shirishag75]Thnx in advance. Hope to get some answers haven't started any compilations as yet, would do the same after some advice/suggestions from u. Would like to disable stuff which I don't use like digital cameras, no firewire support would like to have USB support as think to have a USB thumbdrive in couple of months.[/QUOTE]
You can disable the support for firewire but it don't think it will make any difference. USB support is enabled by default.
Do not disable the support for the modules you are not sure to be useless for your computer.

---

### Post by ShirishAg75 on 2005-12-20
First of all thnx for taking the time to answer the questions above. Made me edit & give an Avatar & give some more info. about myself. 
            Simply installing the new 686 kernel should've some improvements but can that also be compiled to have some more better performance? If so how to go about doing that, using the same guide or something different? Would of course let u know if there are any improvements after installing the newer kernel. thnx in advance.

---

### Post by tseliot on 2005-12-20
[QUOTE=shirishag75]First of all thnx for taking the time to answer the questions above. Made me edit & give an Avatar & give some more info. about myself. 
            Simply installing the new 686 kernel should've some improvements but can that also be compiled to have some more better performance. If so how to go about doing that. Would of course let u know after installing the newer kernel  . thnx in advance.[/QUOTE]
If you want to compile a faster kernel you have to disable all the modules which are not useful to your hardware. In other words look at lspci and look for the Linux modules which are required by each device of yours. Then disable the modules (after you do the "sudo make menuconfig" thing in the guide) which you are sure to be related to devices (chipsets, etc.) other than yours.
This can be a good chance to learn something about Linux kernels.

Anyhow I wouldn't be able to help you now as I'm too stressed. I need some rest.

---

### Post by Bloot on 2005-12-20
Anybody found a solution to make automount devices work when compiling 2.6.14 + kernels?.

---

### Post by ShirishAg75 on 2005-12-20
Hi all,
        First of all did download the new image, it was 2 files & approximately took 25 MB space compressed space & 75 temporary space. Using the new kernel, it seems little bit more faster but still not good enough. Although couple of things need to be disabled through BUM but still don't think will have much effect. 
         Another question that came to me. Whenever one asks for :-
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
```
    1. Does the system know what kernel I'm using 2.6.12-10-686 kernel right now, how does it know that it shouldn't download let's say 2.6.12-10-386  or any other kernel? It would be interesting to understand that.
    2.  Just to understand all the entries in the lspci output are modules that are required or is there a difference when some of them show 0 in the used by column. A part of me says yes & a part says no hence the question :)
            Thnx again

---

### Post by tseliot on 2005-12-21
[QUOTE=Bloot]Anybody found a solution to make automount devices work when compiling 2.6.14 + kernels?.[/QUOTE]
I haven't tested kernel 2.6.14 too much. Anyhow if I find a solution I'll post it.

---

### Post by tseliot on 2005-12-21
[QUOTE=shirishag75]Hi all,
        First of all did download the new image, it was 2 files & approximately took 25 MB space compressed space & 75 temporary space. Using the new kernel, it seems little bit more faster but still not good enough. Although couple of things need to be disabled through BUM but still don't think will have much effect. 
         Another question that came to me. Whenever one asks for :-
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
```
    1. Does the system know what kernel I'm using 2.6.12-10-686 kernel right now, how does it know that it shouldn't download let's say 2.6.12-10-386  or any other kernel? It would be interesting to understand that.[/QUOTE]
Those packages are the same for every architecture (i386, 686, etc.)
    
[QUOTE=shirishag75]2.  Just to understand all the entries in the lspci output are modules that are required or is there a difference when some of them show 0 in the used by column. A part of me says yes & a part says no hence the question :)
            Thnx again[/QUOTE]
Ok have a look at your lspci. Put the name of each device (one per time) in Google's search engine together with the word "linux" (or "module").
In this way you will know the modules which each piece of your hardware needs.

The next step is to do the "sudo make menuconfig" thing and explore it. Each module you can enable (or disable) has a description of its function. if you select a module and press the "?" symbol on your keyboard you can have a detailed description. Then if you are sure you don't need the module (for example for a 3dfx card or an nforce controller) you can disable it.
In other words you have to learn what your computer really needs.

---

### Post by Bloot on 2005-12-21
[QUOTE=tseliot]I haven't tested kernel 2.6.14 too much. Anyhow if I find a solution I'll post it.[/QUOTE]

Thanks, it's annoying to build a new kernel and then be unable to mount any devices but the floppy.

---

### Post by ShirishAg75 on 2005-12-21
[QUOTE=tseliot]
/snip
About your old kernel (2.6.12-9-386): the easiest way to remove it is to:
open Synaptic/Kynaptic
type "linux" in the search field and press search
you will get a list, look for "linux-image-2.6.12-9-386" and mark it for complete removal

OR

a fastest way to do that is:
```
sudo dpkg -r linux-image-2.6.12-9-386
```
/snip
[/QUOTE]
Hi there,
             Thanx for pointing stuff out. Will look at the same. the dpkg -r didn't do it for me. What helped was doing the same in synaptic. Tried the same way today morning when I wanted to remove the 2.16.12.10-386 kernel but that didn't help. I marked it for total removal but still the entry was there in grub. Which atleast to me feels like the whole thing hasn't been removed. After quite a bit searching came to the apt manual which gives this command :-
```
apt-get --purge remove linux-image-2.6.12.10-386
``` I think this is the command which gets invoked when we do the same in Synaptic. I did the job wonderfully & was able to take the entries out of grub also. Also did an 
```
apt-get autoclean
``` It's been fascinating to see how things work in this universe :)

---

### Post by ShirishAg75 on 2005-12-21
Hi there,
            This is the last time I ask u before setting down to the actual dirty work.  In lspci the output usually comes such as :-
0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)

Now this tells me this is the RAM controller & uses Intel 82845 chipset who is responsible for it. Now what is the rev 03. I tried putting  many times the query such as :-
Q1. intel 82845G/GL DRAM Controller linux & there are many results but don't know how to narrow it down to know what module it is. For e.g. [http://lists.debian.org/debian-boot/2005/10/msg00841.html](http://lists.debian.org/debian-boot/2005/10/msg00841.html) he has a machine much closer to me atleast with the lspci output & he was able to do it in a 2.4 kernel so know that the modules are there.

 Q2.  What is the difference between a driver & a module? I also have made a complete note of the modprobe as well as lspci on a page so when doing this it should be helpful. Would like to understand what I'm searching for. 

 Another thing in u'r guide u have given 
                 ```
sudo make oldconfig
```
Q3.Should I be using this step also or not & what does this step do?
            As always thanx in advance.

---

### Post by tseliot on 2005-12-21
[QUOTE=shirishag75]Hi there,
            This is the last time I ask u before setting down to the actual dirty work.  In lspci the output usually comes such as :-
0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)

Now this tells me this is the RAM controller & uses Intel 82845 chipset who is responsible for it. Now what is the rev 03. I tried putting  many times the query such as :-
Q1. intel 82845G/GL DRAM Controller linux & there are many results but don't know how to narrow it down to know what module it is. For e.g. [http://lists.debian.org/debian-boot/2005/10/msg00841.html](http://lists.debian.org/debian-boot/2005/10/msg00841.html) he has a machine much closer to me atleast with the lspci output & he was able to do it in a 2.4 kernel so know that the modules are there.[/QUOTE]
I guess there's no need to do anything because kernel 2.6.12 supports your chipset.

[QUOTE=shirishag75]Q2.  What is the difference between a driver & a module? I also have made a complete note of the modprobe as well as lspci on a page so when doing this it should be helpful. Would like to understand what I'm searching for.[/QUOTE]
You can compile the support for a device (the driver) in the kernel or as a module (which you can disable and enable whenever you like)

[QUOTE=shirishag75] Another thing in u'r guide u have given 
                 ```
sudo make oldconfig
```
Q3.Should I be using this step also or not & what does this step do?
            As always thanx in advance.[/QUOTE]
oldconfig let you use the settings of your current kernel for the kernel you are going to compile.

---

### Post by ShirishAg75 on 2005-12-21
[QUOTE=tseliot]oldconfig let you use the settings of your current kernel for the kernel you are going to compile.[/QUOTE]
       Now don't know whether that's good or not. 
Further it seems the Realtek ethernet chipset 8139C+ fast ethernet is also supported generically. I say this as I didn't have to install a single driver till date. Things just had to be configured. 
         Just downloading the 1st part. downloading linux-tree. It's a 44.3 MB of download with the linux-source itself being a 40 mb download. That's quite a bit.      Also would be downloading the suggested packages libncurses-dev, kernel-package, libqt3-dev tonight as well as the recommended package gcc-3.4. Atleast complete all the downloads business tonight itself & then start trying to play around tomorrow.

---

### Post by ShirishAg75 on 2005-12-22
success, using my kernel surfing & doing stuff. It really has changed the countours of how the system was responding before. Pretty cool. Another thing it's always nice to see one's name in the kernel :) instead of alberto made shirish here. 
         One thing though. Made couple of bloopers. 1st had started the whole thing as sudo su hence while at the export step missed the CC=gcc3.4 & it had compiled with gcc=4.0 I guess then gave the command again & ran the whole group of commands as u had given. 

1.Further had saved the config file also. I gave it a name shirish.config how should I find it or where would it be?

2. It did give some errors while booting up. Although all the functions are happening properly. So what/where things are wrong or could've gone wrong? Any ideas? I'm sure there is some log which keeps the tab of the booting process. If possible wanna look at the log.

---

### Post by tseliot on 2005-12-22
[QUOTE=shirishag75]success, using my kernel surfing & doing stuff. It really has changed the countours of how the system was responding before. Pretty cool. Another thing it's always nice to see one's name in the kernel :) instead of alberto made shirish here. 
         One thing though. Made couple of bloopers. 1st had started the whole thing as sudo su hence while at the export step missed the CC=gcc3.4 & it had compiled with gcc=4.0 I guess then gave the command again & ran the whole group of commands as u had given. 

1.Further had saved the config file also. I gave it a name shirish.config how should I find it or where would it be?[/QUOTE]
If you have installed the new kernel you have to get to /boot and copy the file "config-name_of_your_kernel" to the folder you wish.
[QUOTE=shirishag75]2. It did give some errors while booting up. Although all the functions are happening properly. So what/where things are wrong or could've gone wrong? Any ideas? I'm sure there is some log which keeps the tab of the booting process. If possible wanna look at the log.[/QUOTE]
Have a look at /var/log/syslog.0

---

### Post by ShirishAg75 on 2005-12-23
(/snip)
```
 sudo passwd root
(and set the root password which you will need later) 
``` why do I need this? I want to keep my system simple. Just one password for user as well as root. So is it o.k. if I do su or sudo su here?
 ```

cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux  
``` I always remove the symbolic link in case present before. Nice & easy till here.
 ```

cd /usr/src/linux
make menuconfig 

``` changed it as I'm su here. Saved the file & everything's A o.k. till here.

(/snip)
```

Now you are back to the command line, type:
6) su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
 
```       This is the step where I get confused as to where I'm. Now here I don't need to be su as I'm the super user here.The moment I exit I become the normal user  let's say shirishag75 so it would be:-
```

root@ubuntu:/usr/src/linux# CC=gcc-3.4 
root@ubuntu:/usr/src/linux# export CC
root@ubuntu:/usr/src/linux# exit
exit
shirishag75@ubuntu:~$ CC=gcc-3.4
shirishag75@ubuntu:~$ export CC
shirishag75@ubuntu:~$ sudo make-kpkpg clean
Password:
sudo: make-kpkpg: command not found

shirishag75@ubuntu:~$ sudo cd/usr/src/linux
sudo: cd/usr/src/linux: command not found

``` 
        Now this last procedure is the most frustating of all.  See if this can be simplified more without putting the sudo passwd root routine as well as this changing back & forth or the reasons why we're doing it. Otherwise atleast I didn't understand is the user making the export & if ues why isn't the command after that of 
sudo make-kpkg clean being processed. 
              Sorry for being a pain in the a** but this either needs to be cleaned up or provided with some info. as what's happening. 
                   Thanx in advance.

---

### Post by tseliot on 2005-12-23
[QUOTE=shirishag75](/snip)
```
 sudo passwd root
(and set the root password which you will need later) 
``` why do I need this? I want to keep my system simple. Just one password for user as well as root. So is it o.k. if I do su or sudo su here?
 ```

cd /usr/src
sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux  
``` I always remove the symbolic link in case present before. Nice & easy till here.
 ```

cd /usr/src/linux
make menuconfig 

``` changed it as I'm su here. Saved the file & everything's A o.k. till here.

(/snip)
```

Now you are back to the command line, type:
6) su
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
 
```       This is the step where I get confused as to where I'm. Now here I don't need to be su as I'm the super user here.The moment I exit I become the normal user  let's say shirishag75 so it would be:-
```

root@ubuntu:/usr/src/linux# CC=gcc-3.4 
root@ubuntu:/usr/src/linux# export CC
root@ubuntu:/usr/src/linux# exit
exit
shirishag75@ubuntu:~$ CC=gcc-3.4
shirishag75@ubuntu:~$ export CC
shirishag75@ubuntu:~$ sudo make-kpkpg clean
Password:
sudo: make-kpkpg: command not found

shirishag75@ubuntu:~$ sudo cd/usr/src/linux
sudo: cd/usr/src/linux: command not found

``` 
        Now this last procedure is the most frustating of all.  See if this can be simplified more without putting the sudo passwd root routine as well as this changing back & forth or the reasons why we're doing it. Otherwise atleast I didn't understand is the user making the export & if ues why isn't the command after that of 
sudo make-kpkg clean being processed. 
              Sorry for being a pain in the a** but this either needs to be cleaned up or provided with some info. as what's happening. 
                   Thanx in advance.[/QUOTE]
If you want you can use the same password of your username for your root account (It's not recommended for security reasons).

You made a mistake (a typo)
You wrote:
```
sudo make-[COLOR="Red"]kpkpg[/COLOR] clean
```

But the correct command is:
```
sudo make-[COLOR="Red"]kpkg[/COLOR] clean
```

---

### Post by ShirishAg75 on 2005-12-23
[quote=tseliot]If you have installed the new kernel you have to get to /boot and copy the file "config-name_of_your_kernel" to the folder you wish.

Have a look at /var/log/syslog.0[/quote] 
 1. Strange looked at /var/log/syslog.0 & the last entry was of 
Dec 22 02:25:30 localhost exiting on signal 15 after that there's no entry. 

 2.Further more Nautilus seems to be behaving strangely. Now it's not able to go   to directories  other than mine even as root. It crashes sometimes randomly sometimes one after other. 

 3.  The horizontal bar which tells that Ubuntu is loading up & hides the textual loading up is gone. Now the text messages are seen.
      this is the line from /boot/grub/menu.lst . Is this just a simple thing of just deleting the quiet in between splash or something which 
     maybe I deselected in the menuconfig. 
```
/boot/vmlinuz-2.6.12-shirish root=/dev/hda12 ro quiet splash
```

        Lastly, now with the new kernel If I try again to build a kernel it should take quite a less time shouldn't it. As now it would try to use the p4 power+ RAM.  Whenever I do I would be skipping the make oldconfig step as I would want things to be efficient as well as stable also. Would be looking for u'r comments to what to watch out for while trying this next time :) Thanx all the same.

---

### Post by ShirishAg75 on 2005-12-24
Did try once before u answer but wasn't able to be successful. Another thing how much time/frequency does the kernel change. I've looked at some of the posts where u've been talking of the vanilla kernel & that is 2.6.14 so how much time lag is there between the kernels coming up at [www.kernel.org]("http://www.kernel.org") & they being posted in the repositeries.
             [FONT=System][SIZE=1]
[/SIZE][/FONT]

---

### Post by tseliot on 2005-12-24
[QUOTE=shirishag75]1. Strange looked at /var/log/syslog.0 & the last entry was of 
Dec 22 02:25:30 localhost exiting on signal 15 after that there's no entry. 

 2.Further more Nautilus seems to be behaving strangely. Now it's not able to go   to directories  other than mine even as root. It crashes sometimes randomly sometimes one after other. 

 3.  The horizontal bar which tells that Ubuntu is loading up & hides the textual loading up is gone. Now the text messages are seen.
      this is the line from /boot/grub/menu.lst . Is this just a simple thing of just deleting the quiet in between splash or something which 
     maybe I deselected in the menuconfig. 
```
/boot/vmlinuz-2.6.12-shirish root=/dev/hda12 ro quiet splash
```

        Lastly, now with the new kernel If I try again to build a kernel it should take quite a less time shouldn't it. As now it would try to use the p4 power+ RAM.  Whenever I do I would be skipping the make oldconfig step as I would want things to be efficient as well as stable also. Would be looking for u'r comments to what to watch out for while trying this next time :) Thanx all the same.[/QUOTE]
Weird... why don't you stick with the kernel which comes with Ubuntu by default?

---

### Post by ShirishAg75 on 2005-12-24
because it's damn slow. Compared with how it's working now with the new one, it used to take ages for the thing to start compared to this one.  Just if I got some more control over what's happening & what to look out for.

---

### Post by tseliot on 2005-12-24
[QUOTE=shirishag75]because it's damn slow. Compared with how it's working now with the new one, it takes ages for the thing to start compared to this one. Just if I got some more control over what's happening & what to look out for.[/QUOTE]
I don't know what you changed in the new kernel (with respect to Ubuntu's default kernel) so unless you tell me I can't help you.

---

### Post by ShirishAg75 on 2005-12-24
Sorry, English is not my first language & it was written on the spur of the moment. Anyway have changed/edited the post now.  What I meant was the one which is working now is faster than the 2.6.10-686 which was there in the default kernel.  The issue is I don't understand much of the make menuconfig thing as well as the exporting compiler issue. For e.g. why does the user also have to give the CC=export gcc-3.4 & the whole thing. 
           Another thing which I didn't tell u is that I was also using id3master's 
 How to speed up ubuntu process & inadverantly messed up the one of the syslogd entries. so would start play around a little, shut down the machine & then again the whole process couple of times & then see if I can find something in /var/log/whatever comes next. 
      Another thing which I wanted to ask u was which is superior in ALSA & OSS. Would u recommend both/ or one of the two more than the other & the reasons for the same. Feeling sleepy now going to sleep :)

---

### Post by ShirishAg75 on 2005-12-24
double posting bloopers.

---

### Post by Rob2687 on 2005-12-24
With the 2.6.14 kernel, it seems to be mounting stuff but not really mounting them. If I put in a CD or USB thumbdrive, they are accessable through /media/cdrom0 and /media/USB DRIVE but it isn't accessable through Computer or anything.

---

### Post by tseliot on 2005-12-25
[QUOTE=Rob2687]With the 2.6.14 kernel, it seems to be mounting stuff but not really mounting them. If I put in a CD or USB thumbdrive, they are accessable through /media/cdrom0 and /media/USB DRIVE but it isn't accessable through Computer or anything.[/QUOTE]
I don't use kernel 2.6.14 but I have heard other people complaining about mounting issues. I hope they can be solved in 2.6.15

---

### Post by tseliot on 2005-12-25
[QUOTE=shirishag75]Sorry, English is not my first language & it was written on the spur of the moment. Anyway have changed/edited the post now.  What I meant was the one which is working now is faster than the 2.6.10-686 which was there in the default kernel.[/QUOTE]
Do you use Ubuntu Hoary or Breezy? Or did you upgraded Hoary to Breezy? (kernel 2.6.10 came by default with Hoary)  
[QUOTE=shirishag75]The issue is I don't understand much of the make menuconfig thing as well as the exporting compiler issue. For e.g. why does the user also have to give the CC=export gcc-3.4 & the whole thing.[/QUOTE]
CC=export gcc-3.4 means that you tell your computer to use gcc-3.4 instead of the one which comes by default with Ubuntu Breezy (gcc-4.0).
Every kernel needs its particular version of gcc (the compiler) e.g. kernels 2.6.12-x need gcc-3.4 while kernels 2.6.14-x need gcc-4.0
In my guide I suggest to export CC 2 times (both as root and as common user) because sometimes it won't accept the command if prompted only by a common user (it happened to me 2 days ago).
[QUOTE=shirishag75]Another thing which I didn't tell u is that I was also using id3master's How to speed up ubuntu process & inadverantly messed up the one of the syslogd entries. so would start play around a little, shut down the machine & then again the whole process couple of times & then see if I can find something in /var/log/whatever comes next. [/QUOTE]
Sorry but I can't help you with that.
[QUOTE=shirishag75]Another thing which I wanted to ask u was which is superior in ALSA & OSS. Would u recommend both/ or one of the two more than the other & the reasons for the same. Feeling sleepy now going to sleep :)[/QUOTE]
I think ALSA is superior but OSS is required for a few things (games,etc.)
You can install alsa-oss from synaptic (so as to emulate OSS by using ALSA for compatibility reasons)

---

### Post by ShirishAg75 on 2005-12-25
[quote=tseliot]Do you use Ubuntu Hoary or Breezy? Or did you upgraded Hoary to Breezy? (kernel 2.6.10 came by default with Hoary)  

[COLOR=Lime]Ubuntu 5.10 no upgradations using the official shipit install CD & by default it installed the 2.6.10 kernel. Should it have installed one of the 2.6.14 by default?[/COLOR]

CC=export gcc-3.4 means that you tell your computer to use gcc-3.4 instead of the one which comes by default with Ubuntu Breezy (gcc-4.0).
Every kernel needs its particular version of gcc (the compiler) e.g. kernels 2.6.12-x need gcc-3.4 while kernels 2.6.14-x need gcc-4.0
In my guide I suggest to export CC 2 times (both as root and as common user) because sometimes it won't accept the command if prompted only by a common user (it happened to me 2 days ago).

[COLOR=Lime][COLOR=Lime]When one is giving this export command as su as well as common user remains in the RAM or not? Because as common user the moment I say exit it throws me out to my home directory & then unable to get to /usr/src/linux from where the command has to be given. Is there somehow that the moment su exists it doesn't throw me to my home directory so I can execute the export command in the /usr/src/linux directory itself. [/COLOR]
[/COLOR] 
Sorry but I can't help you with that.

I think ALSA is superior but OSS is required for a few things (games,etc.)
You can install alsa-oss from synaptic (so as to emulate OSS by using ALSA for compatibility reasons)[/quote]

     [COLOR=Lime]Thanx, will try that.[/COLOR]

---

### Post by tseliot on 2005-12-25
[QUOTE=shirishag75][COLOR=Lime]Ubuntu 5.10 no upgradations using the official shipit install CD & by default it installed the 2.6.10 kernel. Should it have installed one of the 2.6.14 by default?[/COLOR][/QUOTE]
Ubuntu Breezy 5.10 comes with kernel 2.6.12 by default. Ubuntu Hoary 5.04 with kernel 2.6.10. Ubuntu Dapper 6.04 will come with 2.6.15.

If you have a Breezy installation you should have kernel 2.6.12. Otherwise there's something wrong (unless you upgraded Hoary to Breezy)

[QUOTE=shirishag75][COLOR=Lime]When one is giving this export command as su as well as common user remains in the RAM or not? Because as common user the moment I say exit it throws me out to my home directory & then unable to get to /usr/src/linux from where the command has to be given. Is there somehow that the moment su exists it doesn't throw me to my home directory so I can execute the export command in the /usr/src/linux directory itself.[/COLOR][/QUOTE]
It's not important in which directory you are when you type the export command. If you follow EVERY step my guide (copy and paste the commands I suggest) everything will work.

---

### Post by ShirishAg75 on 2005-12-25
you were right it's 2.6.12-10 the default kernel which comes with the Ubuntu. Any info. on getting some more understanding of the make menuconfig thing. Some link which tells some of the options which are there.

---

### Post by tseliot on 2005-12-25
[QUOTE=shirishag75]you were right it's 2.6.12-10 the default kernel which comes with the Ubuntu. Any info. on getting some more understanding of the make menuconfig thing. Some link which tells some of the options which are there.[/QUOTE]
Try this website:
[http://www.kernelnewbies.org/]("http://www.kernelnewbies.org/")

Anyhow I don't know all the functions of a kernel and perhaps only a kernel hacker can fully understande them.

---

### Post by ephman on 2005-12-29
hi,

i'm having a bit of a problem with a restricted module i need to intall, madwifi.  i follow the instructions.  i download the source (since i used subversion i didn't have to decompress), and moved the directory to /usr/src/, then i:

sudo make-kpkg clean, and then
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image

see the .deb's for image and the headers, but not the .deb for madwifi?  am i missing something?

thanks for the bandwidth,
ephman

---

### Post by Rob2687 on 2005-12-29
You can just make and make install madwifi separately

---

### Post by ephman on 2005-12-29
hi,

i'm just curios why it didn't create the .deb for madwifi when it should have?  am i making a mistake anywhere?

thanks,
ephman

---

### Post by Rob2687 on 2005-12-29
The madwifi source should be in /usr/src/modules
I'm not sure that just using svn to get the source will give you the proper stuff to make a madwifi module.

You can try installing the debian madwifi source package from the Debian repos and extract it then make the modules.

---

### Post by ephman on 2005-12-29
cool thanks that makes sense.

go leafs go...


ephman

---

### Post by lynwis on 2006-01-10
hi, i compiled the kernel yesterday, and everything seems to be alright, but i don't really understand this thing about compiling restricted-modules.

I wanted to install the ati drivers; with the binary kernel i just got them via apt-get, running:
>apt-get install xorg-driver-fglrx

but now i understand this won't work with my custom kernel, so i tried to download the source for that driver, with:
> apt-get source xorg-driver-fglrx

but i get an archive named "linux-restriced-modules", containing more folders.
I tried to put the entire folder in /usr/src/ , to compile it as a module with the kernel, as you said in the how-to, but it didn't work.
There's also a subfolder named "ati" in the archive, with files that i think are needed for compiling fglrx and the other stuff, but i don't know what to do, since there seems to be no makefile or anything... (and i don't have much experience with compiling packages...)

well, in the end i just wanted to know what should i do to install the ati drivers (for radeon 9700) for the new compiled kernel

ps: thanks for the how-to, i hope my english is understandable

---

### Post by tseliot on 2006-01-10
[QUOTE=lynwis]hi, i compiled the kernel yesterday, and everything seems to be alright, but i don't really understand this thing about compiling restricted-modules.

I wanted to install the ati drivers; with the binary kernel i just got them via apt-get, running:
>apt-get install xorg-driver-fglrx

but now i understand this won't work with my custom kernel, so i tried to download the source for that driver, with:
> apt-get source xorg-driver-fglrx

but i get an archive named "linux-restriced-modules", containing more folders.
I tried to put the entire folder in /usr/src/ , to compile it as a module with the kernel, as you said in the how-to, but it didn't work.
There's also a subfolder named "ati" in the archive, with files that i think are needed for compiling fglrx and the other stuff, but i don't know what to do, since there seems to be no makefile or anything... (and i don't have much experience with compiling packages...)

well, in the end i just wanted to know what should i do to install the ati drivers (for radeon 9700) for the new compiled kernel

ps: thanks for the how-to, i hope my english is understandable[/QUOTE]
Those weren't ati proprietary drivers therefore you have to remove them from /usr/src (or wherever you put them).

The right drivers are the following:
```
sudo apt-get install fglrx-kernel-source
```

A new file will appear in  /usr/src

Extract it in the following way:
```
cd /usr/src
sudo tar -xzvf fglrx-kernel-source.tar.gz
```

Then compile the kernel (a new kernel) following the rest of the guide.

If you don't want to compile a new kernel then you might want to try the following guide: [HOW-TO: ATI fglrx driver 8.16.20]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ATI+drivers")

OR this one for the latest version of the driver [HOW-TO: ATI fglrx driver latest version]("http://ubuntuforums.org/showpost.php?p=423584")

---

### Post by Titan1958 on 2006-01-14
Thanks a lot!

It works straight forward for me. Short 'n Sweet!

I have compiled my 1st kernel woo woo :)

---

### Post by Azion on 2006-01-14
Is there a performance increase for compiling the kernel?

---

### Post by ashrack on 2006-01-15
[QUOTE=Azion]Is there a performance increase for compiling the kernel?[/QUOTE]
On my notebook I get noticable faster startup and some increase in overall performance. I believe its because of the slow HDD that notebooks have :(
But on my main desktop machine, I only noticed about 2sec faster bootup time.

Bottom line, if U have a good machine(check my sig) than theres no need for compiling it. I personally compile 4 fun. SInce I like to know whats happening under the hud.

---

### Post by greyhound4334 on 2006-01-20
Hi,

I've gotten myself somewhat messed up.  

I wanted to install a 2.6.15 series kernel.  I've always run stock ubuntu kernels before, and I'm not 100% sure what "extra" stuff ubuntu patches into the vanilla kernel.org kernels, so I had what I thought was a great brainstorm: let's see if there's a 2.6.15 kernel source package in dapper with all the ubuntu stuff.

Lo and behold, change my sources.list to dapper, apt-get update, and there's a lovely 2.6.15 kernel source with ubuntu patches for the taking.

So I downloaded the source and pretty much followed this installation guide (nice job, thank you for putting it up!).

But now I'm having some oddball module loading problems with ivtv (tv capture card driver for MythTV) that I'm wondering about.  Might there have been some subtle problems with building 2.6.15 that lead to this problem?

I'm pursuing this with the ivtv folks, but in the mean time, I wanted to backtrack a bit and ask these questions:

1. Is my approach valid (i.e., does it make sense to download the dapper kernel source and build it in a breezy installation)?
2. If not (or if the answer is unknown), how about a different approach: if I download a vanilla kernel from kernel.org, is there any "easy" way to apply the ubuntu patches to it?  
3. On a related note, found the CK patchset (I think you referenced it here), but I was wondering how that relates to any Ubuntu patches, if anyone knows.  More concretely, can I apply both the CK patchset AND the ubuntu patchset?

Thanks in advance for any help on this.

Cheers,
john

---

### Post by tseliot on 2006-01-20
[QUOTE=greyhound4334]1. Is my approach valid (i.e., does it make sense to download the dapper kernel source and build it in a breezy installation)?[/QUOTE]
In theory you shouldn't do it. However I did it several times (when I used Hoary) and nothing bad happened.

[QUOTE=greyhound4334]2. If not (or if the answer is unknown), how about a different approach: if I download a vanilla kernel from kernel.org, is there any "easy" way to apply the ubuntu patches to it?[/QUOTE]
I really don't know how to do that

[QUOTE=greyhound4334]3. On a related note, found the CK patchset (I think you referenced it here), but I was wondering how that relates to any Ubuntu patches, if anyone knows.  More concretely, can I apply both the CK patchset AND the ubuntu patchset?[/QUOTE]
I think they are different patches and you should use either one or the other.

BTW did you try to download the sources of the driver of your card. You might need to use the **latest** version and compile it together with the kernel as a kernel module (as I explain in the guide).

---

### Post by greyhound4334 on 2006-01-20
[QUOTE=tseliot]In theory you shouldn't do it. However I did it several times (when I used Hoary) and nothing bad happened.[/QUOTE]
Yeah, everything else seems fine.  And I'm only mildly suspicious of the kernel build process as a factor in my ivtv problem.  But thought I'd verify my assumptions.  All things being equal, I agree - I think I'd rather not try to mix-and-match the sources this way.

> 
I really don't know how to do that

OK.  But do you know anything about the "ubuntu patches"?  Right now they're a total mystery to me, and I'm a little leery of running without them.  I suppose I could try it and see what happens, but I'm afraid of running into a problem downstream when something that used to work suddenly doesn't.

> 
I think they are different patches and you should use either one or the other.

Makes sense to me.

> 
BTW did you try to download the sources of the driver of your card. You might need to use the **latest** version and compile it together with the kernel as a kernel module (as I explain in the guide).
Yes.  Err... maybe.  I'm not sure.  :)   I followed the method of your guide that explained how to download the installer and run it, which seemed to download source and compile and link it.  I used the latest version.  Whatever I did, the nVidia drivers seemed to work fine at the end.

Thanks for your guide(s) and for the help.  I'd really feel more comfortable if I could learn more about the ubuntu patches!

Cheers,
john

---

### Post by tseliot on 2006-01-20
[QUOTE=greyhound4334]Yes.  Err... maybe.  I'm not sure.  :)   I followed the method of your guide that explained how to download the installer and run it, which seemed to download source and compile and link it.  I used the latest version.  Whatever I did, the nVidia drivers seemed to work fine at the end.

If you follow this part of the guide "[COLOR="Red"]7) DO THIS ONLY IF YOU NEED SOME RESTRICTED MODULE[/COLOR]" and use it to install the latest version (which you have to get from a website and not from the repositories) of the ivtv driver (you don't need to compile also the nvidia drivers together with the kernel). You have to download the latest ivtv source code and put it in the modules folder in your /usr/src and follow the guide.


[QUOTE=greyhound4334]I'd really feel more comfortable if I could learn more about the ubuntu patches![/QUOTE]
Me too.

---

### Post by greyhound4334 on 2006-01-20
[QUOTE=tseliot]
If you follow this part of the guide "[COLOR="Red"]7) DO THIS ONLY IF YOU NEED SOME RESTRICTED MODULE[/COLOR]" and use it to install the latest version (which you have to get from a website and not from the repositories) of the ivtv driver (you don't need to compile also the nvidia drivers together with the kernel). You have to download the latest ivtv source code and put it in the modules folder in your /usr/src and follow the guide.
[/QUOTE]
Very interesting.  Let me make sure I understand you correctly.  I'm fairly novice at kernel building and all, so I'm groping a bit.

I think you're saying that I should treat the ivtv modules as a "restricted module" in your terms, much the same way you describe how to treat the nvidia proprietary driver in this way, right?

I *do* build the ivtv stuff from source, and I *think* it links in to the kernel headers for my kernel, but maybe that's not the same?  I'm a bit confused on this part, so I want to make sure I'm understanding you correctly.

Note that I built a 2.12 series kernel from source before, and followed the standard ivtv installation process (as I just described, NOT as you describe it -- the essential difference, I think, being that you want me to put it in the /usr/src/modules directory and have it built as part of make-kpkg) and it worked fine.

Maybe you could comment on what I just wrote so I can be sure I understand your suggestion.

Thanks for taking the time with this problem!  I'm very grateful.

Cheers,
john

---

### Post by tseliot on 2006-01-20
[QUOTE=greyhound4334]Very interesting.  Let me make sure I understand you correctly.  I'm fairly novice at kernel building and all, so I'm groping a bit.

I think you're saying that I should treat the ivtv modules as a "restricted module" in your terms, much the same way you describe how to treat the nvidia proprietary driver in this way, right?[/QUOTE]
You're right but the method I have suggested is useless unless you find a version of the source of the driver which compiles fine with kernel 2.6.15.

Once find the right source of the driver you should follow the standard ivtv installation process(which is faster and easier than mine). Therefore I retire my suggestion. You know, I'm studying for my 1st exam of the 2nd level degree and my brain is frying (literally) :p

---

### Post by greyhound4334 on 2006-01-20
Thanks.  And good luck with the exams!

---

### Post by HenryTheGreat on 2006-01-26
I must thank you tseliot; I followed your instructions and I compiled my first kernel (2.6.15)!! :D :D \\:D/

---

### Post by chinaski on 2006-01-29
hi,

is this How-To suitable also for Kubuntu BB AMD64-Bit?

---

### Post by tseliot on 2006-01-29
[QUOTE=chinaski]hi,

is this How-To suitable also for Kubuntu BB AMD64-Bit?[/QUOTE]
Yes, sure. You can use it for both Ubuntu 32bit and 64bit.

---

### Post by chinaski on 2006-01-29
good :)

thank you tseliot, grazie ;)

---

### Post by dolson on 2006-01-31
Updating /boot/grub/menu.lst ... done

Setting up kernel-image-2.6.12-dolson (1.0) ...
FATAL: Module dm_mod not found.


What is that about??

---

### Post by tseliot on 2006-01-31
[QUOTE=dolson]Updating /boot/grub/menu.lst ... done

Setting up kernel-image-2.6.12-dolson (1.0) ...
FATAL: Module dm_mod not found.


What is that about??[/QUOTE]
It's device-mapper. Does the kernel work properly?

---

### Post by dolson on 2006-01-31
Well, I think that I figured out why I get that. Or not why, but how/when.

At the time I was running the install command, I was running a vanilla kernel that I compiled with very very customized options (I disable everything that doesn't apply to my system pretty much), and was trying to use the Breezy source to make a slight customized version of the official kernel.

I think that when running the vanilla kernel, I get that message for some reason. I think this because I made a sandbox and tested the same procedure while running the default 386 kernel, and that message did not appear.

Yes, the kernel works fine. So I think it's something weird that happens when running the vanilla kernels.

I just thought I'd ask in your thread because I used a very similar method to yours (near identical, really), and thought perhaps it was something that happened every time.

---

### Post by tseliot on 2006-02-01
[QUOTE=dolson]Yes, the kernel works fine. So I think it's something weird that happens when running the vanilla kernels.

I just thought I'd ask in your thread because I used a very similar method to yours (near identical, really), and thought perhaps it was something that happened every time.[/QUOTE]
It never happened to me. Anyhow you have to be sure that all you disable in the kernel isn't related to your hardware. For example the 1st time I installed Gentoo I disabled the support for my network card:p the kernel was fast though..

---

### Post by whisperer on 2006-02-01
I'm trying to compile the 686 kernel on my Centrino laptop. In the config menu I select my processor type as Pentium M. I undestand that Pentium M is closer to 686 than 386, however the resulting .deb files are for 386. What gives ?

---

### Post by tseliot on 2006-02-01
[QUOTE=whisperer]I'm trying to compile the 686 kernel on my Centrino laptop. In the config menu I select my processor type as Pentium M. I undestand that Pentium M is closer to 686 than 386, however the resulting .deb files are for 386. What gives ?[/QUOTE]
That only means that the package is for a 32bit OS. In other words it's absolutely normal.

---

### Post by greywullf on 2006-02-02
Let me start by expressing my thanks for the detailed information provided.  I have been using Linux (redhat) since 1997 and recently decided to try ubuntu, so this is my first experience compiling a kernel with ubuntu.

I am trying to compile a version 2.6.12 kernel.

I followed the instructions and everything went well until I executed the command:
make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

The command executes and then exits with the following:
 LD      lib/zlib_deflate/built-in.o
  LD      lib/zlib_inflate/built-in.o
  LD      arch/i386/lib/built-in.o
  CC      arch/i386/lib/bitops.o
  AS      arch/i386/lib/checksum.o
  CC      arch/i386/lib/delay.o
  AS      arch/i386/lib/getuser.o
  CC      arch/i386/lib/memcpy.o
  CC      arch/i386/lib/mmx.o
  AS      arch/i386/lib/putuser.o
  CC      arch/i386/lib/strstr.o
  CC      arch/i386/lib/usercopy.o
  AR      arch/i386/lib/lib.a
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
drivers/built-in.o: In function `uncompress':
cloop.c:(.text+0x79f07): undefined reference to `zlib_inflateReset'
cloop.c:(.text+0x79f1b): undefined reference to `zlib_inflate'
cloop.c:(.text+0x79f5e): undefined reference to `zlib_inflateEnd'
cloop.c:(.text+0x79f76): undefined reference to `zlib_inflateInit_'
drivers/built-in.o: In function `clo_set_file':
cloop.c:(.text+0x7a90f): undefined reference to `zlib_inflate_workspacesize'
cloop.c:(.text+0x7a943): undefined reference to `zlib_inflateInit_'
cloop.c:(.text+0x7abdf): undefined reference to `zlib_inflate_workspacesize'
drivers/built-in.o: In function `cloop_exit':
cloop.c:(.exit.text+0x39e): undefined reference to `zlib_inflateEnd'
cloop.c:(.exit.text+0x44a): undefined reference to `zlib_inflateEnd'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory /usr/src/linux-source-2.6.12

Can someone provide some suggestions as to what needs to be fixed?

Thanks

---

### Post by tseliot on 2006-02-02
[QUOTE=greywullf]cloop.c:(.exit.text+0x44a): undefined reference to `zlib_inflateEnd'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory /usr/src/linux-source-2.6.12

Can someone provide some suggestions as to what needs to be fixed?

Thanks[/QUOTE]
Did you do "sudo make oldconfig" before doing "sudo make menuconfig" ?
I'm asking you because it might solve the problem (according to what other users have reported).

---

### Post by nehalem on 2006-02-02
Ok, I am trying to compile my kernel since I am making a small adjustment since my laptop has a high pitched noise.

**When I get to step 8 I get this on the clean statement:**
> cendrizzi@cte-laptop:/usr/src/linux$ sudo make-kpkg clean
/usr/bin/make -f /usr/share/kernel-package/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
test ! -f .config || cp -pf .config config.precious
test -f Makefile && \
            /usr/bin/make    ARCH=i386 distclean
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
fs/hostfs/Makefile:11: arch/um/scripts/Makefile.rules: No such file or directory
make[4]: *** No rule to make target `arch/um/scripts/Makefile.rules'.  Stop.
make[3]: *** [fs/hostfs] Error 2
make[2]: *** [_clean_fs] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: [real_stamp_clean] Error 2 (ignored)
test ! -f config.precious || mv -f config.precious .config
test ! -f stamp-patch || /usr/bin/make -f /usr/share/kernel-package/rules unpatch_now
test -f stamp-building || test -f debian/official || rm -rf debian
# work around idiocy in recent kernel versions
test ! -e scripts/package/builddeb.dist || \
            mv -f scripts/package/builddeb.dist scripts/package/builddeb
test ! -e scripts/package/Makefile.dist || \
            mv -f scripts/package/Makefile.dist scripts/package/Makefile
rm -f modules/modversions.h modules/ksyms.ver debian/files conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches debian/buildinfo stamp-build stamp-configure stamp-source stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-buildpackage stamp-libc-kheaders stamp-debian stamp-patch stamp-kernel-configure
rm -rf debian/tmp-source debian/tmp-headers debian/tmp-image debian/tmp-doc
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'


I have done this twice and know I have all the packages installed.  Can anyone help me understand what I've done wrong?

**Here is an ls -l of my my /usr/src/linux directory**
> lrwxrwxrwx  1 root root     31 2006-02-02 01:44 arch -> ../linux-headers-2.6.12-10/arch
lrwxrwxrwx  1 root root     34 2006-02-02 01:44 cluster -> ../linux-headers-2.6.12-10/cluster
lrwxrwxrwx  1 root root     33 2006-02-02 01:44 crypto -> ../linux-headers-2.6.12-10/crypto
lrwxrwxrwx  1 root root     34 2006-02-02 01:44 drivers -> ../linux-headers-2.6.12-10/drivers
lrwxrwxrwx  1 root root     29 2006-02-02 01:44 fs -> ../linux-headers-2.6.12-10/fs
drwxr-xr-x  4 root root   4096 2006-02-02 01:44 include
lrwxrwxrwx  1 root root     31 2006-02-02 01:44 init -> ../linux-headers-2.6.12-10/init
lrwxrwxrwx  1 root root     30 2006-02-02 01:44 ipc -> ../linux-headers-2.6.12-10/ipc
lrwxrwxrwx  1 root root     33 2006-02-02 01:44 kernel -> ../linux-headers-2.6.12-10/kernel
lrwxrwxrwx  1 root root     30 2006-02-02 01:44 lib -> ../linux-headers-2.6.12-10/lib
lrwxrwxrwx  1 root root     28 2006-02-02 18:45 linux-source-2.6.12 -> /usr/src/linux-source-2.6.12
lrwxrwxrwx  1 root root     35 2006-02-02 01:44 Makefile -> ../linux-headers-2.6.12-10/Makefile
lrwxrwxrwx  1 root root     29 2006-02-02 01:44 mm -> ../linux-headers-2.6.12-10/mm
-rw-r--r--  1 root root 238057 2006-01-16 11:30 Module.symvers
lrwxrwxrwx  1 root root     30 2006-02-02 01:44 net -> ../linux-headers-2.6.12-10/net
drwxr-xr-x  9 root root   4096 2006-02-02 01:44 scripts
lrwxrwxrwx  1 root root     35 2006-02-02 01:44 security -> ../linux-headers-2.6.12-10/security
lrwxrwxrwx  1 root root     32 2006-02-02 01:44 sound -> ../linux-headers-2.6.12-10/sound
lrwxrwxrwx  1 root root     30 2006-02-02 01:44 usr -> ../linux-headers-2.6.12-10/usr


Does it have to do with how my system is setup?

I have the 686 kernel installed and have the ati proprietary driver installed (I'm currently using the vesa kernel as told.

**The only thing I did different was this:**
> Change the "HZ" kernel constants to alter the frequency of timer interrupts. Discussion:

* Andreas Karnahl: i've read in several forums it has something to do with the "idle"-state (or "C3") of the processor. There is a frequency called "timer interrupt" (or so mething like that). Since kernel 2.6x it is set to 1000 Hz by default (compared to 100 Hz in Kernel 2.4x). The exact reason i don't know, but it is safe to change this frequency to 100 Hz in kernel 2.6x (by the way, windows up to XP uses 100 Hz by default).
Just do the following:

In [path to kernel-sources]/include/asm-i386/param.h find the line

#define HZ 1000

and change the value of HZ to 100:

#define HZ 100

Then recompile the kernel.
After i changed it on my ThinkPad A30 (under SuSE 9.2 and 9.3) and recompiling the kernel the high pitch noise is gone away.

This is supposed to fix the high pitched noise my laptop will produce.  

Thanks very much in advance!

---

### Post by tseliot on 2006-02-03
[QUOTE=nehalem]Ok, I am trying to compile my kernel since I am making a small adjustment since my laptop has a high pitched noise.

**When I get to step 8 I get this on the clean statement:**


I have done this twice and know I have all the packages installed.  Can anyone help me understand what I've done wrong?

**Here is an ls -l of my my /usr/src/linux directory**


Does it have to do with how my system is setup?

I have the 686 kernel installed and have the ati proprietary driver installed (I'm currently using the vesa kernel as told.

**The only thing I did different was this:**


This is supposed to fix the high pitched noise my laptop will produce.  

Thanks very much in advance![/QUOTE]
You don't need to do that thing. You can compile a vanilla kernel 2.6.14 or 2.6.15 in this way you can set the Frequency without the need of any trick.
Follow this guide (it also explains how to set the frequency):
[How-To: 2.6.14 Vanilla Kernel (latest) + ck Patchset (Enhanced Performance kernel)]("http://www.ubuntuforums.org/showthread.php?t=84174")

---

### Post by greywullf on 2006-02-03
tseliot

Thank you for yout assistance.  Yes it appears I missed that one command, on my second attempt I successfully compiled, installed and booted a new kernel.

Now on to getting the sound to work!

Once again, thanks

---

### Post by chugru on 2006-02-04
Thanks for a very useful and informative thread!

I have been struggling for 2 days, trying to recompile a 2.6.12 kernel for my Breezy box. I believe I followed the "Compilation for Newbies" instructions completely, and each step seemed to proceed according to plan.

Not so with my effort to restart. After many recompilation attempts, each time I  restart, I experience kernel panic:[HTML]Uncompressing Linix... Ok, booting the kernel.
[4294667.930000] Kernel panic - not synching: VFS: Unable to mount root fs 
on unknown-block(0,0)[/HTML]

I'm not sure what information can be derived from that error message. I also have run out of ideas as to what next to try... :???: 

Any help will be very much appreciated!

---

### Post by tseliot on 2006-02-04
[QUOTE=chugru]Thanks for a very useful and informative thread!

I have been struggling for 2 days, trying to recompile a 2.6.12 kernel for my Breezy box. I believe I followed the "Compilation for Newbies" instructions completely, and each step seemed to proceed according to plan.

Not so with my effort to restart. After many recompilation attempts, each time I  restart, I experience kernel panic:[HTML]Uncompressing Linix... Ok, booting the kernel.
[4294667.930000] Kernel panic - not synching: VFS: Unable to mount root fs 
on unknown-block(0,0)[/HTML]

I'm not sure what information can be derived from that error message. I also have run out of ideas as to what next to try... :???: 

Any help will be very much appreciated![/QUOTE]
1) Are you trying to compile the kernel from Ubuntu's sources (from the repos) or a vanilla kernel (from kernel.org)?

2) Did you do this before doing "sudo make menuconfig"? :
sudo make oldconfig

---

### Post by chugru on 2006-02-04
[QUOTE=tseliot]1) Are you trying to compile the kernel from Ubuntu's sources (from the repos) or a vanilla kernel (from kernel.org)?

2) Did you do this before doing "sudo make menuconfig"? :
sudo make oldconfig[/QUOTE]
Yes, I'm using Ubuntu's sources from the repositories, not a vanilla kernel. 

I did use **sudo make oldconfig** before doing **sudo make menuconfig**. I proceeded in this manner: ```
# cd /usr/src/linux
# cp /boot/config-2.6.12-9-386 /.config
# make oldconfig
```

Thank you for the quick response!

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]Yes, I'm using Ubuntu's sources from the repositories, not a vanilla kernel. 

I did use **sudo make oldconfig** before doing **sudo make menuconfig**. I proceeded in this manner: ```
# cd /usr/src/linux
# cp /boot/config-2.6.12-9-386 /.config
# make oldconfig
```

Thank you for the quick response![/QUOTE]
Post the content of your: 
1) /etc/fstab
2) /boot/grub/menu.lst

---

### Post by chugru on 2006-02-05
[QUOTE=tseliot]Post the content of your: 
1) /etc/fstab
2) /boot/grub/menu.lst[/QUOTE]
My /etc/fstab: ```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

... and my (now very long) menu.lst:```
title           Ubuntu, kernel 2.6.12 Default
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/hda1 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.12 Default (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/hda1 ro single
boot

title           Ubuntu, kernel 2.6.12.old Previous
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/hda1 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.12.old Previous (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/hda1 ro single
boot

title           Ubuntu, kernel 2.6.12.old
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12.old root=/dev/hda1 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.12.old (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12.old root=/dev/hda1 ro single
boot

title           Ubuntu, kernel 2.6.12-chugru
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-chugru root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-chugru
savedefault
boot

title           Ubuntu, kernel 2.6.12-chugru (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-chugru root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-chugru
boot

title           Ubuntu, kernel 2.6.12-chagru
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-chagru root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-chagru
savedefault
boot

title           Ubuntu, kernel 2.6.12-chagru (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-chagru root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-chagru
boot

title           Ubuntu, kernel 2.6.12-9-386.stable
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386.stable root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386.stable
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386.stable (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386.stable root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386.stable
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, kernel 2.6.12
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12 root=/dev/hda1 ro quiet splash
savedefault
boot

title           Ubuntu, kernel 2.6.12 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12 root=/dev/hda1 ro single
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

```

The "Stable" selection (/boot/vmlinuz-2.6.12-9-386.stable root=/dev/hda1 ro quiet splash) is the option from my original Kubuntu disk instillation---it still works.

Thanks, again, for looking at this!

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]My /etc/fstab: ```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```
The "Stable" selection (/boot/vmlinuz-2.6.12-9-386.stable root=/dev/hda1 ro quiet splash) is the option from my original Kubuntu disk instillation---it still works.

Thanks, again, for looking at this![/QUOTE]
Type this:
cat /boot/config-[COLOR="Red"]name_of_the_kernel_you_compiled[/COLOR] | grep REISER

and post the output

---

### Post by chugru on 2006-02-05
Gladly...

[CODE] cat config-2.6.12-chugru | grep REISER
CONFIG_REISERFS_FS=y
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y


Thanks...

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]Gladly...

```
cat config-2.6.12-chagru | grep REISER
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y

```

Thanks...[/QUOTE]
Usually if you compile a kernel from Ubuntu sources you don't need to compile the support for your filesystem in the kernel (you can compile it as a module).

Perhaps in your case is different. Therefore you could try to recompile the kernel and build the support for REISERFS in the kernel (a "y" will appear instead of a "m")

---

### Post by chugru on 2006-02-05
I just edited my last post to show the REISER content of **cat config-2.6.12-chagru** That was compiled with REISERFS kernel support. That recompiled version likewise fails with the same kernel panic message...

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]I just edited my last post to show the REISER content of **cat config-2.6.12-chagru** That was compiled with REISERFS kernel support. That recompiled version likewise fails with the same kernel panic message...[/QUOTE]
I think the user Rjwood had the same problem.
What does this command say?

cat config-2.6.12-chugru | grep initrd

---

### Post by chugru on 2006-02-05
That comand "cat config-2.6.12-chugru | grep initrd" returns nothing...

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]That comand "cat config-2.6.12-chugru | grep initrd" returns nothing...[/QUOTE]
My bad
cat /boot/config-2.6.12-10-k7 | grep INITRD

---

### Post by chugru on 2006-02-05
NP... Did you want: ```
cat **config-2.6.12-9-386** | grep INITRD
CONFIG_ACPI_INITRD=y
CONFIG_BLK_DEV_INITRD=y

```

---

### Post by chugru on 2006-02-05
Or did you want: ```
cat **config-2.6.12-chugru **| grep INITRD
CONFIG_ACPI_INITRD=y
CONFIG_BLK_DEV_INITRD=y

```

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]NP... Did you want: ```
cat **config-2.6.12-9-386** | grep INITRD
CONFIG_ACPI_INITRD=y
CONFIG_BLK_DEV_INITRD=y

```[/QUOTE]
Ok, another thing:
cd /boot
ls

---

### Post by chugru on 2006-02-05
[QUOTE=tseliot]Ok, another thing:
cd /boot
ls[/QUOTE]
My /boot directory: ```
$ ls -l
total 32400
-rw-r--r--  1 root root  239770 2005-10-10 08:16 abi-2.6.12-9-386
lrwxrwxrwx  1 root root      13 2006-02-03 19:09 config -> config-2.6.12
-rw-r--r--  1 root root   64118 2006-02-03 19:09 config-2.6.12
-rw-r--r--  1 root root   64135 2005-10-10 07:12 config-2.6.12-9-386
-rw-r--r--  1 root root   64125 2006-02-04 14:06 config-2.6.12-chagru
-rw-r--r--  1 root root   64137 2006-02-04 15:52 config-2.6.12-chugru
-rw-r--r--  1 root root   64141 2006-02-03 15:58 config-2.6.12.old
lrwxrwxrwx  1 root root      17 2006-02-03 19:09 config.old -> config-2.6.12.old
drwxr-xr-x  2 root root     416 2006-02-04 17:02 grub
-rw-r--r--  1 root root 4946814 2006-01-27 19:07 initrd.img-2.6.12-9-386
-rw-r--r--  1 root root 4946814 2006-02-03 13:53 initrd.img-2.6.12-9-386.stable
-rw-r--r--  1 root root 5195333 2006-02-04 15:20 initrd.img-2.6.12-chagru
-rw-r--r--  1 root root 4490229 2006-02-04 17:02 initrd.img-2.6.12-chugru
-rw-r--r--  1 root root   94664 2005-06-30 10:49 memtest86+.bin
lrwxrwxrwx  1 root root      17 2006-02-03 19:09 System.map -> System.map-2.6.12
-rw-r--r--  1 root root  897419 2006-02-03 19:09 System.map-2.6.12
-rw-r--r--  1 root root  897159 2005-10-10 08:16 System.map-2.6.12-9-386
-rw-r--r--  1 root root  918977 2006-02-04 15:11 System.map-2.6.12-chagru
-rw-r--r--  1 root root 1164042 2006-02-04 16:57 System.map-2.6.12-chugru
-rw-r--r--  1 root root  897600 2006-02-03 15:58 System.map-2.6.12.old
lrwxrwxrwx  1 root root      21 2006-02-03 19:09 System.map.old -> System.map-2.6.12.old
lrwxrwxrwx  1 root root      14 2006-02-03 19:09 vmlinuz -> vmlinuz-2.6.12
-rw-r--r--  1 root root 1197735 2006-02-03 19:09 vmlinuz-2.6.12
-rw-r--r--  1 root root 1206555 2005-10-10 08:16 vmlinuz-2.6.12-9-386
-rw-r--r--  1 root root 1206555 2006-02-03 13:54 vmlinuz-2.6.12-9-386.stable
-rw-r--r--  1 root root 1256857 2006-02-04 15:11 vmlinuz-2.6.12-chagru
-rw-r--r--  1 root root 2009341 2006-02-04 16:57 vmlinuz-2.6.12-chugru
-rw-r--r--  1 root root 1216391 2006-02-03 15:58 vmlinuz-2.6.12.old
lrwxrwxrwx  1 root root      18 2006-02-03 19:09 vmlinuz.old -> vmlinuz-2.6.12.old

```

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]My /boot directory: [CODE]$ ls -l
total 32400...[/QUOTE]
I don't understand... everything seems ok.

What's the model of your motherboard?

I'm asking you because I had a similar problem and I solved it by upgrading the BIOS.

---

### Post by chugru on 2006-02-05
[QUOTE=tseliot]I don't understand... everything seems ok.

What's the model of your motherboard?

I'm asking you because I had a similar problem and I solved it by upgrading the BIOS.[/QUOTE]
My motherboard: ```
 description: Desktop Computer
    product: P4S5A/DX
    vendor: ECS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: P4S5A/DX
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01                        )
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy28
80 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification

```

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]My motherboard: ```
 description: Desktop Computer
    product: P4S5A/DX
    vendor: ECS
    version: 1.0
    serial: 00000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: P4S5A/DX
       vendor: ECS
       physical id: 0
       version: 1.0
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 07.00T (04/02/01                        )
          size: 64KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy28
80 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification

```[/QUOTE]
My motherboard is Asus A8V.
I can't think of any solution.
You could start a thread on Linuxquestions.org

---

### Post by chugru on 2006-02-05
[QUOTE=tseliot]My motherboard is Asus A8V.
I can't think of any solution.
You could start a thread on Linuxquestions.org[/QUOTE]
Thank you for all your support...

I'm inclined to abort all these reconfig efforts and start from scratch.

2 questions: 

1) How to best remove all the reconfig efforts I've tried thus far
2) Any need for bin86 (which I saw but didn't install)

Thanks, sincerely...

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]Thank you for all your support...

I'm inclined to abort all these reconfig efforts and start from scratch.

2 questions: 

1) How to best remove all the reconfig efforts I've tried thus far
2) Any need for bin86 (which I saw but didn't install)

Thanks, sincerely...[/QUOTE]
1) I suggest you to remove the entire folder with your sources i.e. :
cd /usr/src/
sudo rmdir name_of_the_folder_with_you_sources

2) It won't hurt you ;)

---

### Post by chugru on 2006-02-05
[QUOTE=tseliot]1) I suggest you to remove the entire folder with your sources i.e. :
cd /usr/src/
sudo rmdir name_of_the_folder_with_you_sources

2) It won't hurt you ;)[/QUOTE]
Finally... A functioning recompiled kernel! I followed all the steps of the Howto and encountered only one glitch while the kernel image was compiling:```
Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
``` 

Revisiting **make menuconfig** and fixing the **KALLSYMS_EXTRA-PASS** allowed the compilation then to proceed without error.

Many thanks to **tseliot** for helping me through this! :D

---

### Post by tseliot on 2006-02-05
[QUOTE=chugru]Finally... A functioning recompiled kernel! I followed all the steps of the Howto and encountered only one glitch while the kernel image was compiling:```
Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
``` 

Revisiting **make menuconfig** and fixing the **KALLSYMS_EXTRA-PASS** allowed the compilation then to proceed without error.

Many thanks to **tseliot** for helping me through this! :D[/QUOTE]
I'm glad it worked in the end :)

---

### Post by codejunkie on 2006-02-05
i got a quick question i compiled my kernel following this howto and everything seems to be working fine except i have two breezy installs on this computer and when i try installing the new kernel on the other install it works fine but i can't compile the nvidia driver. it just dies and says check /var/log/nvidia-installer.log but it doesn't give any info on the cause im guessing the kernel-headers package i made doesn't contain the kernel modules the nvidia installer needs any help would be appreicated.
here's some more info that may help
kernel im trying to compile 2.6.15.2
options i used when building the new kernel
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
nvidia driver im trying to install
NVIDIA-Linux-x86-1.0-8178-pkg1.run
gcc version 4.0

---

### Post by mohapi on 2006-02-06
Thanks very much for this howto. It might solve a lot of the problems I have been experiencing lately. 

I just want to check something, before I take the time to try it myself. 

Could I build a custom kernel on one machine, with the intent of installing it on another? For example, I'd like to build the kernel on a fast machine, then copy it over to a slower one. I *think* that should work, but I suppose there is the chance I would be missing some files. 

Thanks in advance, and thanks again for the howto. :-D

---

### Post by tseliot on 2006-02-06
[QUOTE=codejunkie]i got a quick question i compiled my kernel following this howto and everything seems to be working fine except i have two breezy installs on this computer and when i try installing the new kernel on the other install it works fine but i can't compile the nvidia driver. it just dies and says check /var/log/nvidia-installer.log but it doesn't give any info on the cause im guessing the kernel-headers package i made doesn't contain the kernel modules the nvidia installer needs any help would be appreicated.
here's some more info that may help
kernel im trying to compile 2.6.15.2
options i used when building the new kernel
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
nvidia driver im trying to install
NVIDIA-Linux-x86-1.0-8178-pkg1.run
gcc version 4.0[/QUOTE]
If you want to install the latest Nvidia driver with kernel 2.6.15.x you need to patch the Nvidia installer first.
Here is a link to the patch and the instructions:
[http://www.nvnews.net/vbulletin/showthread.php?t=62021]("http://www.nvnews.net/vbulletin/showthread.php?t=62021")

---

### Post by tseliot on 2006-02-06
[QUOTE=mohapi]Thanks very much for this howto. It might solve a lot of the problems I have been experiencing lately. 

I just want to check something, before I take the time to try it myself. 

Could I build a custom kernel on one machine, with the intent of installing it on another? For example, I'd like to build the kernel on a fast machine, then copy it over to a slower one. I *think* that should work, but I suppose there is the chance I would be missing some files. 

Thanks in advance, and thanks again for the howto. :-D[/QUOTE]
The kernel you compile on a machine can be installed on any other machine. Of course a kernel compiled for a 32bit OS won't work on a 64bit OS and vice versa.

---

### Post by mohapi on 2006-02-07
Hi, just for future reference, I was able to compile a very light kernel for a 120Mh Pentium laptop, then move it (via CD) to the target machine and *sudo dpkg -i* it. 

It took a _very_ long time to install, and I got two warnings about a missing symbolic link (the /usr/src/linux), but in the end it worked perfectly and my poor old Compaq seems to boot a little faster. ...

Thanks again! :mrgreen:

---

### Post by gezzabob on 2006-02-11
For those of you like me who need IT8212 support (gagaRAID ATA IT8212) my problem and specs are on here
 [http://ubuntuforums.org/showthread.php?t=125524](http://ubuntuforums.org/showthread.php?t=125524) I fount this thread [http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12](http://ubuntuforums.org/showthread.php?t=106285&highlight=patch+kernel+2.6.12)

I am trying it now so far so good fingers crossed.

---

### Post by ubuntuross on 2006-02-11
I followed all of the steps in this guide, but when I restart my computer it get the following message:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like ot view the X server output to diagnose the problem?

When I say yes it tell me that I'm using X Window System Version 6.8.2.

Any ideas?

---

### Post by tseliot on 2006-02-11
[QUOTE=ubuntuross]I followed all of the steps in this guide, but when I restart my computer it get the following message:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like ot view the X server output to diagnose the problem?

When I say yes it tell me that I'm using X Window System Version 6.8.2.

Any ideas?[/QUOTE]
Do you use a proprietary graphic driver (such as "nvidia" or "fglrx")?

In that case you should type:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia" OR "ati" instead of "fglrx"
CTRL+O to save
CTRL+X to exit

```
sudo /etc/init.d/gdm stop (if you use GDM, otherwise "kdm stop")
```

Then
```
sudo /etc/init.d/gdm start (if you use GDM, otherwise "kdm start")
```

Then the xserver should work and you might want to reinstall the graphic drivers. Remember that every time you change or upgrade your kernel you will have to reinstall the drivers (only for the new kernel)

---

### Post by ubuntuross on 2006-02-11
Thank you so much!!! I never installed the proprietary driver so I just assumed that I was using nv...bad assumption.  That fixed me right up.  Many many thanks for writing this guide and for responding so quickly to my inquiry (and knowing how to fix my problem)!

---

### Post by tseliot on 2006-02-11
[QUOTE=ubuntuross]Thank you so much!!! I never installed the proprietary driver so I just assumed that I was using nv...bad assumption.  That fixed me right up.  Many many thanks for writing this guide and for responding so quickly to my inquiry (and knowing how to fix my problem)![/QUOTE]
I'm glad to help :) . Enjoy your Ubuntu experience.

---

### Post by nrwilk on 2006-02-17
Heya, tseliot!

I used the guide again to compile 2.6.15.4 vanilla.

First, a simple question:

Is it normal that my firewire devices are recognized and automounted MUCH, MUCH better with the new kernel than with the kernel which is installed with breezy by default?

Secondly, I have a problem since I've been using the new kernel.  When the computer starts up, it'll come to the grub menu, and after selecting 2.6.15.4-custom, Nothing is displayed on the screen until the xserver is started.  In other words, the entire start-up process goes by without being displayed on my monitor.  I wouldn't care so much, except that if something were to go wrong there, I'd want to know what happened.  Do you know of any way this could have been affected by the new kernel?  What can I do?

thanks!

---

### Post by tseliot on 2006-02-18
> **nrwilk]Is it normal that my firewire devices are recognized and automounted MUCH, MUCH better with the new kernel than with the kernel which is installed with breezy by default?[/QUOTE]
You should thank Linus Torvalds and his collaborators for that  said:**
> Secondly, I have a problem since I've been using the new kernel.  When the computer starts up, it'll come to the grub menu, and after selecting 2.6.15.4-custom, Nothing is displayed on the screen until the xserver is started.  In other words, the entire start-up process goes by without being displayed on my monitor.  I wouldn't care so much, except that if something were to go wrong there, I'd want to know what happened.  Do you know of any way this could have been affected by the new kernel?  What can I do?
It's a common problem. It seems that these kernels do not support the bootsplash. I haven't found a solution to the problem yet.

I've found a patch for kernel 2.6.15 but I haven't tried it myself yet:
[http://www.bootsplash.org/]("http://www.bootsplash.org/")

---

### Post by nrwilk on 2006-02-18
I looked over the instructions for applying the patch, but I don't think I understand the instructions well enough to try it. :-k 

Oh well.  You gain a little footing, you lose a little.  :)

---

### Post by nmsmith on 2006-02-18
This is rather an early step in the process, but when I do ```
apt-get install kernel-package
``` I get messages like:

```
W: Couldn't stat source package list ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```

What should I do? Do I need to set my repositories up differently?

---

### Post by Rizado on 2006-02-19
[QUOTE=tseliot]It's a common problem. It seems that these kernels do not support the bootsplash. I haven't found a solution to the problem yet.

I've found a patch for kernel 2.6.15 but I haven't tried it myself yet:
[http://www.bootsplash.org/]("http://www.bootsplash.org/")[/QUOTE]That shouldn't be necessary. Normal vga console should show up anyway. Try to remove "Splash" from grub.

Also I recommend [Arch CK's kernel patches.](http://iphitus.loudas.com/archck.php) It's the regular CK patches but with some other nice features, Suspend2, vesafb-tng, fbsplash and alot more.

---

### Post by tseliot on 2006-02-19
[QUOTE=nrwilk]Heya, tseliot!

I used the guide again to compile 2.6.15.4 vanilla.

First, a simple question:

Is it normal that my firewire devices are recognized and automounted MUCH, MUCH better with the new kernel than with the kernel which is installed with breezy by default?

Secondly, I have a problem since I've been using the new kernel.  When the computer starts up, it'll come to the grub menu, and after selecting 2.6.15.4-custom, Nothing is displayed on the screen until the xserver is started.  In other words, the entire start-up process goes by without being displayed on my monitor.  I wouldn't care so much, except that if something were to go wrong there, I'd want to know what happened.  Do you know of any way this could have been affected by the new kernel?  What can I do?

thanks![/QUOTE]
Rizado is right but before doing that perhaps you might want to try this:

Boot in your new kernel and regenerate  the initramfs (just copy and paste this command:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

Reboot and tell me if you can see your bootsplash

If that doesn't solve the problem then you might follow Rizado's suggestion.

---

### Post by tseliot on 2006-02-19
[QUOTE=nmsmith]This is rather an early step in the process, but when I do ```
apt-get install kernel-package
``` I get messages like:

```
W: Couldn't stat source package list ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```

What should I do? Do I need to set my repositories up differently?[/QUOTE]
Try this:
sudo nano /etc/apt/sources.list

scroll down the file and make comment out the lines which begin with "ftp://ftp.free" (i.e. put a "##" before them, e.g. ##[ftp://ftp.free](ftp://ftp.free))

CTRL+O to save
CTRL+X to exit

Then type:
sudo apt-get update

and try to install that package again.

---

### Post by nrwilk on 2006-02-19
[QUOTE=tseliot]Boot in your new kernel and regenerate  the initramfs (just copy and paste this command:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

Reboot and tell me if you can see your bootsplash[/QUOTE]

After issuing that command, it gives me this output:
```
Package `linux-image-2.6.15.4-custom' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.15.4-custom is not installed

```

I was in the new kernel, and I have not deleted any of the files which were made when compiling it.

---

### Post by PsychoTrauma on 2006-02-19
These are the steps I used to compile the newest vanilla kernal and get nvidia installed as well. I know they are a bit vague but tseliot already has a very good guide it just needs some organization.

```
Downloaded latest stable kernel.org kernel to my home directory.
sudo apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev
sudo passwd root (didn't need to use this not sure why it was added)
cd ~
tar --bzip2 -xvf linux-2.6.15.4.tar.bz2
sudo mv linux-2.6.15.4 /usr/src/linux-2.6.15.4
sudo ln -s /usr/src/linux-2.6.15.4 /usr/src/linux
cd /usr/src/linux
sudo make oldconfig (held enter untill they were all answered)
sudo make menuconfig (followed instructions along with the extra kernal.org instructions)
sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
cd ..
ls
dpkg -i "the deb files you saw with ls"
reboot to see if the kernel works
Since the kernel source was there I just needed to download the latest nvidia installer
Logout of kde (or gnome)
ctrl-alt-f1
login to your account
sudo /etc/init.d/kdm stop (replace kdm with gdm if you use gnome)
cd ~
sudo sh *.run
I let the installer setup my xorg.conf file (by default it's set on no so make sure to switch to yes)
The kernel has splash set which doesn't work so to disable that I did
sudo nano /boot/grub/menu.lst
use the arrow keys to go to the line that says "kernel          /boot/vmlinuz-2.6.15.4-custom root=/dev/hda2 ro quiet splash" and remove the splash from the end.
ctrl+0
ctrl+x
sudo reboot
now it should show info when you boot with the kernel and it wont have that plain black screen.
```

---

### Post by PsychoTrauma on 2006-02-19
[QUOTE=nrwilk]After issuing that command, it gives me this output:
```
Package `linux-image-2.6.15.4-custom' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.15.4-custom is not installed

```

I was in the new kernel, and I have not deleted any of the files which were made when compiling it.[/QUOTE]

I get the same exact thing using the same vanilla kernel but I fixed the bootsplash problem with the post above.

---

### Post by nrwilk on 2006-02-19
[QUOTE=Rizado]That shouldn't be necessary. Normal vga console should show up anyway.[/QUOTE]
I thought that it should.  It does display during shutdown.

[QUOTE=Rizado]Try to remove "Splash" from grub.[/QUOTE]
I looked for any entry of "Splash" in menu.lst, but I couldn't find one.  Should I be looking somewhere else?

---

### Post by PsychoTrauma on 2006-02-19
sudo kwrite /boot/grub/menu.lst
you'll need to scroll down almost to the bottom to see the line. (the drive it's pointing to will be different but that should be it)
"kernel          /boot/vmlinuz-2.6.15.4-custom root=/dev/hda2 ro quiet splash" and remove the splash from the end.

If you have that line without splash you might try removing the package usplash with apt-get.

Just removed usplash with "sudo apt-get --purge remove usplash" and nothing bad happened when I rebooted so it might be a option. I can't say for sure though since splash was already disabled for me.

---

### Post by nrwilk on 2006-02-19
Nice!  it worked.

I had wanted to get rid of that graphical "Kubuntu" splash for a while anyway.

Thanks, everyone!

---

### Post by Eazy© on 2006-02-21
Hi all!
I just thought I would link a question I have posted here:
[http://www.ubuntuforums.org/showthread.php?t=84174&page=31](http://www.ubuntuforums.org/showthread.php?t=84174&page=31)

Sorry about that, but I rellay really want this fixed, and maybe this would get tseliots attention at the same time ;)

---

### Post by tseliot on 2006-02-21
[QUOTE=Eazy©]Hi all!
I just thought I would link a question I have posted here:
[http://www.ubuntuforums.org/showthread.php?t=84174&page=31](http://www.ubuntuforums.org/showthread.php?t=84174&page=31)

Sorry about that, but I rellay really want this fixed, and maybe this would get tseliots attention at the same time ;)[/QUOTE]
Sorry but I don't play games in Linux and I've never had a soundblaster live.

Perhaps in the Ubuntu Gaming section you will find some help

---

### Post by Rizado on 2006-02-21
[QUOTE=Eazy©]Hi all!
I just thought I would link a question I have posted here:
[http://www.ubuntuforums.org/showthread.php?t=84174&page=31](http://www.ubuntuforums.org/showthread.php?t=84174&page=31)

Sorry about that, but I rellay really want this fixed, and maybe this would get tseliots attention at the same time ;)[/QUOTE]I have noticed that arts often conflict with games of different kinds. Try disabling it. Arts is for kde though, gnome uses something else, esd och jack i think.

---

### Post by dbw on 2006-03-01
tseliot- thanks for the guide.  I did some fairly heavy editing of the kernel options, which I think was in general quite beneficial.  Now I am able to touch my ntfs partition.  Additionally, my memory usage has dropped by 10% across every set of processes that I had benchmarked!!!  It seems, however, that cpu usage has increased - though I have not benchmarked this as rigourously.  Does anyone know of any special features that are installed in the standard Ubuntu x686 kernel that are not flagged by default in the source tree which might effect cpu efficiency?
  -y'all rock

---

### Post by tseliot on 2006-03-02
[QUOTE=dbw]tseliot- thanks for the guide.  I did some fairly heavy editing of the kernel options, which I think was in general quite beneficial.  Now I am able to touch my ntfs partition.  Additionally, my memory usage has dropped by 10% across every set of processes that I had benchmarked!!!  It seems, however, that cpu usage has increased - though I have not benchmarked this as rigourously.  Does anyone know of any special features that are installed in the standard Ubuntu x686 kernel that are not flagged by default in the source tree which might effect cpu efficiency?
  -y'all rock[/QUOTE]
I hope someone can help you because I'm not an expert in this field.

---

### Post by bluevoodoo1 on 2006-03-03
This is a great HOW-TO. It is very clearly written and anyone wanting to configure their own kernel should follow this thread. 
I wanted to do this because of DMA problems, so I did it... but DMA still is an issue. Here are a few threads of mine... [here]("http://ubuntuforums.org/showthread.php?t=138924") and [here]("http://ubuntuforums.org/showthread.php?t=117772")... Can I possibly reconfigure the kernel again to add any other DMA related support besides "“Enable DMA only for disks” and disable it " which I did. Are there any modules that I can choose to me loaded at bootup as the [DMA wiki]("https://wiki.ubuntu.com/DMA") suggests? (I do not have any piix, ide-core or ide-cd modules listed on my /etc/modules)

If not, will...

sudo dpkg -r kernel-image-2.6.12-custom

sudo dpkg -r kernel-headers-2.6.12-custom

remove all traces of the kernal and the source? I noticed it took up a lot of space on my / partition and there isn't much space left. Then I can just go back to using the normal 2.6.12 kernel. Thank you!

---

### Post by tseliot on 2006-03-03
> **bluevoodoo1]This is a great HOW-TO. It is very clearly written and anyone wanting to configure their own kernel should follow this thread. 
I wanted to do this because of DMA problems, so I did it... but DMA still is an issue. Here are a few threads of mine... [here]("http://ubuntuforums.org/showthread.php?t=138924") and [here]("http://ubuntuforums.org/showthread.php?t=117772")... Can I possibly reconfigure the kernel again to add any other DMA related support besides "&#8220 said:**
> DMA wiki[/URL] suggests? (I do not have any piix, ide-core or ide-cd modules listed on my /etc/modules)

If not, will...

sudo dpkg -r kernel-image-2.6.12-custom

sudo dpkg -r kernel-headers-2.6.12-custom

remove all traces of the kernal and the source? I noticed it took up a lot of space on my / partition and there isn't much space left. Then I can just go back to using the normal 2.6.12 kernel. Thank you!
1) what's the model of your motherboard?
2) If you want to remove the kernel make sure you don't boot in that kernel before trying to remove it (i.e. boot in your older kernel).
And to remove it completely:
sudo dpkg --purge remove kernel-image-2.6.12-custom kernel-headers-2.6.12-custom

---

### Post by bluevoodoo1 on 2006-03-03
[QUOTE=tseliot]1) what's the model of your motherboard?[/QUOTE]
From [this site]("http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAsusP4R8L") it says it's an ASUS P4R8L motherboard.

---

### Post by tseliot on 2006-03-03
[QUOTE=bluevoodoo1]From [this site]("http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAsusP4R8L") it says it's an ASUS P4R8L motherboard.[/QUOTE]
Perhaps your controller is doesn't work at its best with kernel 2.6.12.
Can you try to compile a vanilla kernel 2.6.15.x?

---

### Post by bluevoodoo1 on 2006-03-03
[QUOTE=tseliot]Perhaps your controller is doesn't work at its best with kernel 2.6.12.
Can you try to compile a vanilla kernel 2.6.15.x?[/QUOTE]

I'll give it a shot as soon as I can and I will let you know the outcome!!! Are there any other DMA related things to be aware of when compiling besides disabling the "Enable DMA only for disks&#8221; feature??

EDIT: Just want to make sure...

[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.5.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.5.tar.bz2)
is that is the correct link for the 2.6.15.5 source?

---

### Post by tseliot on 2006-03-03
> **bluevoodoo1]I'll give it a shot as soon as I can and I will let you know the outcome!!! Are there any other DMA related things to be aware of when compiling besides disabling the "Enable DMA only for disks&#8221 said:**
> 
Make sure Atiixp is enabled (but I think it's enabled by default)

[QUOTE=bluevoodoo1][http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.5.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.15.5.tar.bz2)
is that is the correct link for the 2.6.15.5 source?
Yes, it's that

---

### Post by zi99y on 2006-03-03
Hi, Thanks for the guide tseliot, and the support you are providing here, I wonder if I can get some help with a small problem. I need to use the xorg fglrx driver for my laptop - have tried the latest version howto and for various reasons I can't use it.

So I have tried to compile in the restricted module by doing the following at Step #7:

```
sudo apt-get install fglrx-kernel-source
```

followed by

```
cd /usr/src
tar xvzf fglrx-kernel-source.tar.gz
```

then I commence with the steps in the howto:

```
cd /usr/src/linux
sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-fglrx kernel_image kernel_headers modules_image
```

And here is when I run into bother after the lengthy compile:

```
dpkg-deb: building package `kernel-headers-2.6.12-fglrx' in `../kernel-headers-2.6.12-fglrx_10.00.Custom_i386.deb'.
rm -rf debian/tmp-headers
echo done >  stamp-headers
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
for module in /usr/src/modules/fglrx-kernel ; do                       \
          if test -d  $module; then                                \
    (cd $module;                                          \
              if ./debian/rules KVERS="2.6.12-fglrx" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG="EXTRAVERSION=-fglrx"        \
                             ARCH="i386"                  \
                             KDREV="10.00.Custom" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \                      echo "in fact being built as root, please file a bug ";  \                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
  fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
./debian/rules:77: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue


```

So I guess it is compiling the kernel ok but failing to make the fglrx deb - so I am wondering if there is anything I can do about this or if there is a ready made package I can use somewhere.

I hope there is a fix for this as my new laptop is running the old 386 kernel and the speed is noticably slow in places. :neutral: 

thanks

---

### Post by bluevoodoo1 on 2006-03-03
Two times in a row I've gotten this error... any ideas?

```

fs/nfs/direct.c: In function 'nfs_get_user_pages':
fs/nfs/direct.c:110: warning: implicit declaration of function 'nfs_free_user_pages'
fs/nfs/direct.c: At top level:
fs/nfs/direct.c:127: warning: conflicting types for 'nfs_free_user_pages'
fs/nfs/direct.c:127: error: static declaration of 'nfs_free_user_pages' follows non-static declaration
fs/nfs/direct.c:110: error: previous implicit declaration of 'nfs_free_user_pages' was here
make[3]: *** [fs/nfs/direct.o] Error 1
make[2]: *** [fs/nfs] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.5'
make: *** [stamp-build] Error 2

```

---

### Post by tseliot on 2006-03-04
[QUOTE=bluevoodoo1]Two times in a row I've gotten this error... any ideas?

```

fs/nfs/direct.c: In function 'nfs_get_user_pages':
fs/nfs/direct.c:110: warning: implicit declaration of function 'nfs_free_user_pages'
fs/nfs/direct.c: At top level:
fs/nfs/direct.c:127: warning: conflicting types for 'nfs_free_user_pages'
fs/nfs/direct.c:127: error: static declaration of 'nfs_free_user_pages' follows non-static declaration
fs/nfs/direct.c:110: error: previous implicit declaration of 'nfs_free_user_pages' was here
make[3]: *** [fs/nfs/direct.o] Error 1
make[2]: *** [fs/nfs] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.5'
make: *** [stamp-build] Error 2

```[/QUOTE]
Try to disable the support for NFS in your kernel

---

### Post by tseliot on 2006-03-04
> **zi99y]Hi, Thanks for the guide tseliot, and the support you are providing here, I wonder if I can get some help with a small problem. I need to use the xorg fglrx driver for my laptop - have tried the latest version howto and for various reasons I can't use it.

So I have tried to compile in the restricted module by doing the following at Step #7:

```
sudo apt-get install fglrx-kernel-source
```

followed by

```
cd /usr/src
tar xvzf fglrx-kernel-source.tar.gz
```

then I commence with the steps in the howto:

```
cd /usr/src/linux
sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-fglrx kernel_image kernel_headers modules_image
```

And here is when I run into bother after the lengthy compile:

```
dpkg-deb: building package `kernel-headers-2.6.12-fglrx' in `../kernel-headers-2.6.12-fglrx_10.00.Custom_i386.deb'.
rm -rf debian/tmp-headers
echo done >  stamp-headers
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
for module in /usr/src/modules/fglrx-kernel  said:**
> ; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \                      echo "in fact being built as root, please file a bug ";  \                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
         read ans;                                        \
              fi;                                                   \
     );                                                    \
  else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
  fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/fglrx-kernel'
./debian/rules:77: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'
Module /usr/src/modules/fglrx-kernel failed.
Hit return to Continue


```

So I guess it is compiling the kernel ok but failing to make the fglrx deb - so I am wondering if there is anything I can do about this or if there is a ready made package I can use somewhere.

I hope there is a fix for this as my new laptop is running the old 386 kernel and the speed is noticably slow in places. :neutral: 

thanks
I'm not an Ati user but I hope this works:

Compile the kernel without the "modules_image" thing.

Then type:

sudo module-assistant

You will see a menu: 
Select "SELECT". 
Select flglrx with your keyboard and press the spacebar on it in order to enable it.
Press "Enter"
Select BUILD (it will ask you if you want to download the source code but you can say no as you already seem to have the source code)

If the process goes fine you can install the new .deb package

---

### Post by zi99y on 2006-03-04
thanks for your reply.

I have the new kernel working already so I don't need to recompile - even though I got that error - it created the debs and I have them installed and working, without opengl ability on fglrx drivers.

"fglrx-kernel-source.tar.gz" is still in it's extracted location in /usr/src/modules so I have run "sudo module-assistant" but I am not seeing an fglrx module listed. Do I have to do something special to tell module assistant where to look for other modules?

ta

---

### Post by tseliot on 2006-03-04
[QUOTE=zi99y]Do I have to do something special to tell module assistant where to look for other modules?

ta[/QUOTE]
No, usually it shows you a list of the available modules.

Can you post that list?

---

### Post by zi99y on 2006-03-04
```
root@nausicaa:/usr/src# module-assistant list fglrx
fglrx-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): fglrx-kernel-2.6.12-10-386_8.20.8-1+2.6.12-10.24_i386.deb
root@nausicaa:/usr/src# apt-get install fglrx-kernel-source
Reading package lists... Done
Building dependency tree... Done
fglrx-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

The deb that it mentions is one that was created when using the latest fglrx driver howto (which worked but had problems which there isn't a fix for)

I can't give you the list from the module-assistant interface becuase it only shows 1 page at a time, unless you know a way to do it, but here's what I get from doing "module-assistant list"

```
root@nausicaa:/usr/src# module-assistant list
acx100-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
affix-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
alsa-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
arla-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
at76c503a-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
bcm4400-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
bcm5700-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cdfs-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cipe-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cloop-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
comedi-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cpad-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cryptoapi-core-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cryptoloop-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
dazuko-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ddrmat-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
device3dfx-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
drbd-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
drbd0.7-module-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
dvb-driver-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
e100-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
eagle-usb-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
em8300-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
freeswan-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ftape-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ftpfs-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
fuse-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
gpib-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
hostap-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
hubcot-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
i2c-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ipw2100-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ipw2200-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
linux-wlan-ng (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
lirc-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
lm-sensors-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
loop-aes-ciphers-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
loop-aes-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
lufs-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
mga-vid-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
misdn-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ndiswrapper-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
nvidia-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
openafs-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
openswan-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ov511-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
pcmcia-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
plex86-kernel-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ppscsi-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
qc-usb-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
qla2x00-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
rtai-source (source package not installed):
sh: /usr/share/modass/packages/rtai-source: Permission denied
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
shfs-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
sl-modem-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
thinkpad-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
tidev-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
translucency-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
tun-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
unicorn-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
unionfs-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
userlink-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
vaiostat-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
video4linux-nw802-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
wacom-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
xdslusb-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
xlibmesa-drm-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
zaptel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
Some packages could not be found. The "search" command can search in the
package pool for precompiled packages.

```

I do get a big list of modules - including the nvidia module - just no fglrx, should this appear as standard?

---

### Post by tseliot on 2006-03-04
[QUOTE=zi99y]```
root@nausicaa:/usr/src# module-assistant list fglrx
fglrx-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): fglrx-kernel-2.6.12-10-386_8.20.8-1+2.6.12-10.24_i386.deb
root@nausicaa:/usr/src# apt-get install fglrx-kernel-source
Reading package lists... Done
Building dependency tree... Done
fglrx-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

The deb that it mentions is one that was created when using the latest fglrx driver howto (which worked but had problems which there isn't a fix for)

I can't give you the list from the module-assistant interface becuase it only shows 1 page at a time, unless you know a way to do it, but here's what I get from doing "module-assistant list"

```
root@nausicaa:/usr/src# module-assistant list
acx100-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
affix-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
alsa-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
arla-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
at76c503a-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
bcm4400-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
bcm5700-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cdfs-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cipe-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cloop-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
comedi-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cpad-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cryptoapi-core-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
cryptoloop-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
dazuko-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ddrmat-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
device3dfx-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
drbd-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
drbd0.7-module-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
dvb-driver-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
e100-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
eagle-usb-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
em8300-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
freeswan-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ftape-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ftpfs-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
fuse-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
gpib-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
hostap-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
hubcot-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
i2c-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ipw2100-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ipw2200-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
linux-wlan-ng (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
lirc-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
lm-sensors-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
loop-aes-ciphers-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
loop-aes-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
lufs-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
mga-vid-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
misdn-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ndiswrapper-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
nvidia-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
openafs-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
openswan-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ov511-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
pcmcia-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
plex86-kernel-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
ppscsi-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
qc-usb-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
qla2x00-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
rtai-source (source package not installed):
sh: /usr/share/modass/packages/rtai-source: Permission denied
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
shfs-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
sl-modem-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
thinkpad-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
tidev-modules-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
translucency-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
tun-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
unicorn-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
unionfs-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
userlink-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
vaiostat-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
video4linux-nw802-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
wacom-kernel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
xdslusb-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
xlibmesa-drm-src (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
zaptel-source (source package not installed):
  -- Binary package(s) for kernel(s):
   + (2.6.12-10-386): not found
Some packages could not be found. The "search" command can search in the
package pool for precompiled packages.

```

I do get a big list of modules - including the nvidia module - just no fglrx, should this appear as standard?[/QUOTE]
Try this:
sudo module-assistant auto-install fglrx

---

### Post by zi99y on 2006-03-04
looks like the original problem here:
```
       &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; module-assistant, interactive mode &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
       &#9474; Build of the package fglrx-kernel-source failed! How do you   &#9474;
       &#9474; wish to proceed?                                              &#9474;
       &#9474;                                                               &#9474;
       &#9474;       VIEW     Examine the build log file                     &#9474;
       &#9474;       CONTINUE Skip and continue with the next operation      &#9474;
       &#9474;       STOP     Stop processing the build commands             &#9474;

```
if I view:
```
 &#9474; debian/rules:77: *** missing separator (did you mean TAB instead of 8
 &#9474; spaces?).  Stop.                                                           &#9618;

```
I found [this post]("http://ubuntuforums.org/showthread.php?t=11806") that looks like the same thing, and no one has got it to work so I guess I'm at a brick wall...

Is there any alternative to get the fglrx xorg driver working (with opengl) other than the latest driver version? Or it looks like I'm stuck with a 386 kernel

---

### Post by tseliot on 2006-03-04
> **zi99y]looks like the original problem here:
```
       &#9484 said:**
> this post[/URL] that looks like the same thing, and no one has got it to work so I guess I'm at a brick wall...

Is there any alternative to get the fglrx xorg driver working (with opengl) other than the latest driver version? Or it looks like I'm stuck with a 386 kernel
Sorry pal but I use Nvidia cards. Did you post in the thread of a guide about Ati drivers (e.g. [http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378) )?

---

### Post by bluevoodoo1 on 2006-03-04
[QUOTE=tseliot]Try to disable the support for NFS in your kernel[/QUOTE]

I disabled it and it compiled! Thank you! But, DMA *still* does not work. finished all steps, rebooted, redid sudo dpkg-reconfigure xserver-xorg...  checked sudo hdparm -d /dev/cdrom ... DMA is on, OK great. Inserted a DVD began to play it.... still choppy video.... checked sudo hdparm -d /dev/cdrom DMA now off... (this has been the problem to date)

Also... there is no screen after GRUB, just black screen until gdm and i2c support seems to have disappeared. But getting DMA to work is the major issue....

---

### Post by tseliot on 2006-03-04
[QUOTE=bluevoodoo1]I disabled it and it compiled! Thank you! But, DMA *still* does not work. finished all steps, rebooted, redid sudo dpkg-reconfigure xserver-xorg...  checked sudo hdparm -d /dev/cdrom ... DMA is on, OK great. Inserted a DVD began to play it.... still choppy video.... checked sudo hdparm -d /dev/cdrom DMA now off... (this has been the problem to date)[/QUOTE]
Can you try to swap the dvdreader with another one (or with a cd-reader) so as to see if the dvd-reader is the problem?

Or change the cable.

If it were a kernel issue you wouldn't see DMA enabled by default.

[QUOTE=bluevoodoo1]Also... there is no screen after GRUB, just black screen until gdm and i2c support seems to have disappeared. But getting DMA to work is the major issue....[/QUOTE]
sudo nano /boot/grub/menu.lst

look for the line with your kernel and remove the word I put in red:

```
title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet [COLOR="Red"]splash[/COLOR]
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot
```

CTRL+O to save
CTRL+X to exit

And reboot (the bootsplash won't work but you won't see a black screen either; there will be only writings)

---

### Post by bluevoodoo1 on 2006-03-04
[QUOTE=tseliot]Can you try to swap the dvdreader with another one (or with a cd-reader) so as to see if the dvd-reader is the problem?

Or change the cable.

If it were a kernel issue you wouldn't see DMA enabled by default.[/QUOTE]

I have a separate CD burner and a separate DVD drive on an old compter (both work with Ubuntu and have DMA working). This computer unfortunately only has one drive and it's a pain to get the drive out. I will first try a new cable, and if that doens't work then swap out for one of the other drives as you suggested. It probably is just the drive. I need to find some DVD burners that are compatible with linux...  I've had a bad experience with NEC... maybe a Lite-on?

but other than I fixed the boot up with what you said and it worked. The boot time is probably 50% of the 2.6.12 kernel. There were a few errors, one with a PCI something the other with the LVM (?). Is there a log file that I can view to see the exact problems?

Thank you very much for all your help tseliot.

---

### Post by tseliot on 2006-03-05
[QUOTE=bluevoodoo1]I have a separate CD burner and a separate DVD drive on an old compter (both work with Ubuntu and have DMA working). This computer unfortunately only has one drive and it's a pain to get the drive out. I will first try a new cable, and if that doens't work then swap out for one of the other drives as you suggested. It probably is just the drive. I need to find some DVD burners that are compatible with linux...  I've had a bad experience with NEC... maybe a Lite-on?[/QUOTE]
I have a TX and an LG (Dvd burners) and both of them work fine. Steer clear of Pioneer burners

[QUOTE=bluevoodoo1]but other than I fixed the boot up with what you said and it worked. The boot time is probably 50% of the 2.6.12 kernel. There were a few errors, one with a PCI something the other with the LVM (?). Is there a log file that I can view to see the exact problems?

Thank you very much for all your help tseliot.[/QUOTE]
type this:
dmesg | less

In this way you will see the entire log file. Use your keyboard arrows to move up or down in the text. Press Q to exit

---

### Post by bluevoodoo1 on 2006-03-05
[QUOTE=tseliot]Steer clear of Pioneer burners[/QUOTE]

HA! Well, I've read that my ASUS burner is merely a rebranded Pioneer. Perhaps that's my problem?!

---

### Post by tseliot on 2006-03-05
[QUOTE=bluevoodoo1]HA! Well, I've read that my ASUS burner is merely a rebranded Pioneer. Perhaps that's my problem?![/QUOTE]
Have a look a this thread (look for Kassetra's post):
[http://www.ubuntuforums.org/showthread.php?t=61969&highlight=pioneer]("http://www.ubuntuforums.org/showthread.php?t=61969&highlight=pioneer")

---

### Post by zi99y on 2006-03-06
Yeah I did, but thanks for the help here. There's always something else to try!! I'm going for another bash with the latest drivers.

ta again

---

### Post by nrwilk on 2006-03-06
can anyone explain to me what kind of speed one is supposed to gain by using Kolivas' patches? I tried 2.6.15 with his ck4 patch (he suggests that you use 2.6.15.0 because his patch contains the changes up to 2.6.15.4), and I have an issue, which I assume is the patch. When I had tried 2.6.15.4 with no patch, I previously mentioned that kernel's enhanced ability to detect and automount firewire devices. With the patch, though, I don't really see any speed increase, and the automounting still works as before, except Nothing which is mounted in /media gets an Icon on the desktop as before. It will show the unmounted device, but if I double click it, it says it is not mounted. For example, If I plug in my firewire harddrive, it is /dev/sda2, but it is mounted at /media/fwdrive. When I double-click it's icon on the desktop, it tells me "/dev/sda2 is not mounted," but if I navigate Konqueror to /media/fwdrive, it is mounted there. Should I just recompile 2.6.15.4 instead of using the patch? I think so, because any speed increases are unnoticable to me.

Thoughts?  Maybe a way to fix this before I spend 25 minutes compiling another kernel?

Thanks!

---

### Post by tseliot on 2006-03-07
[QUOTE=nrwilk]can anyone explain to me what kind of speed one is supposed to gain by using Kolivas' patches? I tried 2.6.15 with his ck4 patch (he suggests that you use 2.6.15.0 because his patch contains the changes up to 2.6.15.4), and I have an issue, which I assume is the patch. When I had tried 2.6.15.4 with no patch, I previously mentioned that kernel's enhanced ability to detect and automount firewire devices. With the patch, though, I don't really see any speed increase, and the automounting still works as before, except Nothing which is mounted in /media gets an Icon on the desktop as before. It will show the unmounted device, but if I double click it, it says it is not mounted. For example, If I plug in my firewire harddrive, it is /dev/sda2, but it is mounted at /media/fwdrive. When I double-click it's icon on the desktop, it tells me "/dev/sda2 is not mounted," but if I navigate Konqueror to /media/fwdrive, it is mounted there. Should I just recompile 2.6.15.4 instead of using the patch? I think so, because any speed increases are unnoticable to me.

Thoughts?  Maybe a way to fix this before I spend 25 minutes compiling another kernel?

Thanks![/QUOTE]
The speed boost would be noticeable only as far as boot time is concerned. And no, compiling another kernel won't help.

About mounting issues: Kubuntu has bug which has been fixed in Dapper. I guess you'll have to wait until Dapper's stable or Use GNOME (which works fine)

---

### Post by Dragineez on 2006-03-07
WTF?
```
make[1]: Entering directory `/usr/src/linux-source-2.6.12'
  CHK     include/linux/version.h
make[2]: `arch/i386/kernel/asm-offsets.s' is up to date.
  CHK     include/linux/compile.h
  CHK     usr/initramfs_list
  KSYM    .tmp_kallsyms1.S
  AS      .tmp_kallsyms1.o
  LD      .tmp_vmlinux2
  KSYM    .tmp_kallsyms2.S
  AS      .tmp_kallsyms2.o
  LD      vmlinux
  SYSMAP  System.map
  SYSMAP  .tmp_System.map
Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
```What is a "KALLSYMS" and why do I care?

---

### Post by ashrack on 2006-03-08
[QUOTE=tseliot]About mounting issues: Kubuntu has bug which has been fixed in Dapper. I guess you'll have to wait until Dapper's stable or Use GNOME (which works fine)[/QUOTE]
I can verify this error. Although sometimes it does work for me.

---

### Post by Rizado on 2006-03-08
[QUOTE=Dragineez]WTF?
```
make[1]: Entering directory `/usr/src/linux-source-2.6.12'
  CHK     include/linux/version.h
make[2]: `arch/i386/kernel/asm-offsets.s' is up to date.
  CHK     include/linux/compile.h
  CHK     usr/initramfs_list
  KSYM    .tmp_kallsyms1.S
  AS      .tmp_kallsyms1.o
  LD      .tmp_vmlinux2
  KSYM    .tmp_kallsyms2.S
  AS      .tmp_kallsyms2.o
  LD      vmlinux
  SYSMAP  System.map
  SYSMAP  .tmp_System.map
Inconsistent kallsyms data
Try setting CONFIG_KALLSYMS_EXTRA_PASS
make[1]: *** [vmlinux] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
```What is a "KALLSYMS" and why do I care?[/QUOTE]Start xconfig and navigate to "General Setup > Configure standard kernel features (for small systems)" Tick "Do an extra kallsyms pass" and try again.

---

### Post by bluevoodoo1 on 2006-03-08
[QUOTE=tseliot]Have a look a this thread (look for Kassetra's post):
[http://www.ubuntuforums.org/showthread.php?t=61969&highlight=pioneer]("http://www.ubuntuforums.org/showthread.php?t=61969&highlight=pioneer")[/QUOTE]


Well I got my LG burner today... and well... no dice. Same problems as the ASUS burner. I'm going to contact ASUS and see if they have any ideas. I have some software for the motherboard and BIOS but wine can't read it due to some missing DLLs... I tried hooking up my other computer's HDD (with windows) to this machine and THAT didn't work either! (got some blue screen of death!)

P.S. I also bought an evga fx5500 and your guide was great in getting it working! (fps went from 300 fps (ati 9100 igp) to 910!!! But the 2.6.15.5 kernel doesn't seem to like it, so I'm back with the 2.6.12.10, no worries though.

---

### Post by Dragineez on 2006-03-08
Thanx Rizado, that took care of it.

---

### Post by bluevoodoo1 on 2006-03-08
[QUOTE=bluevoodoo1]Well I got my LG burner today... and well... no dice. Same problems as the ASUS burner. I'm going to contact ASUS and see if they have any ideas. I have some software for the motherboard and BIOS but wine can't read it due to some missing DLLs... I tried hooking up my other computer's HDD (with windows) to this machine and THAT didn't work either! (got some blue screen of death!)

P.S. I also bought an evga fx5500 and your guide was great in getting it working! (fps went from 300 fps (ati 9100 igp) to 910!!! But the 2.6.15.5 kernel doesn't seem to like it, so I'm back with the 2.6.12.10, no worries though.[/QUOTE]


I GOT IT TO WORK!! I took out the ASUS drive and tested it in my other computer, worked in Breezy and Windows, so I figured it had to be some hardware related here. So I found a few sites that really saved me. Turns out it's a known problem, DMA and the ASUS Pudit-r... I had to do the following... plug IDE cable into "other" input, switch drive to slave and change drive from hda to hdb in /etc/fstab. I don't know if all of those are actually necessary... but DMA WORKS NOW! 3 months of torture now resolved!!! Thank you for all of your ideas and help regarding everything! Time for a DVD!!!

---

### Post by tseliot on 2006-03-09
[QUOTE=bluevoodoo1]I GOT IT TO WORK!! I took out the ASUS drive and tested it in my other computer, worked in Breezy and Windows, so I figured it had to be some hardware related here. So I found a few sites that really saved me. Turns out it's a known problem, DMA and the ASUS Pudit-r... I had to do the following... plug IDE cable into "other" input, switch drive to slave and change drive from hda to hdb in /etc/fstab. I don't know if all of those are actually necessary... but DMA WORKS NOW! 3 months of torture now resolved!!! Thank you for all of your ideas and help regarding everything! Time for a DVD!!![/QUOTE]
I'm glad you solved the problem in the end

---

### Post by escape on 2006-03-13
Regarding the High Memory Support bit, do the kernels from synaptic have this by default? Without it, does it only utilize <=900MB RAM (even if swap space was partitioned to 2 GB?) If not, what does it do? How big a difference can it make? I have 2GB or RAM, just wondering if I'm getting the most out of my kernel.

---

### Post by tseliot on 2006-03-14
[QUOTE=escape]Regarding the High Memory Support bit, do the kernels from synaptic have this by default? Without it, does it only utilize <=900MB RAM (even if swap space was partitioned to 2 GB?) If not, what does it do? How big a difference can it make? I have 2GB or RAM, just wondering if I'm getting the most out of my kernel.[/QUOTE]
The High Memory Support is enabled by default since Ubuntu Breezy 5.10.

Ubuntu Hoary 5.04 was not enabled by default.

I have 2GB of RAM as well and I don't have to recompile anything to make Ubuntu detect it.

BTW if you want to check the amount of RAM which is being detected you can:
1) use Gnome system monitor
OR
2) use KSysguard
OR
3) Open Terminal and type:
```
free
```

and you will get something like this:
```
             [COLOR="Red"]total [/COLOR]      used       free     shared    buffers     cached
Mem:       [COLOR="Red"]2073248[/COLOR]    1113164     960084          0      15644     872300
-/+ buffers/cache:     225220    1848028
Swap:      2097136          0    2097136
```

---

### Post by dag on 2006-03-17
Tried to make a new kernel and it stops at point 8. The commands don't work on my ubuntu.. I'm a newbie so I need a little help here :-) Did do all the other steps from point 1 - 6, skip 7 and go to point 8. 
Im using ubuntu 5.10 with kernel 2.6.12-10-386 and I tried this: sudo make -kpkg --initrd --2.6.12-10-386=-custom kernel_image kernel_headers

[COLOR="Red"]make: invalid option -- g
make: unrecognized option `--initrd'
make: unrecognized option `--2.6.12-10-386=-custom'[/COLOR]
__________________________________________________________________________________________________
Did go as su and I think I did that part now.. Here comes an another:
 sudo make-kpkg --initrd &#8211;append-to-version=-dag kernel_image kernel_headers
Error: Unknown target &#8211;append-to-version=-dag
use --targets to display help on valid targets.



Thanks for your help

Dag

---

### Post by garba on 2006-03-17
[QUOTE=dag]Tried to make a new kernel and it stops at point 8. The commands don't work on my ubuntu.. I'm a newbie so I need a little help here :-) Did do all the other steps from point 1 - 6, skip 7 and go to point 8. 
Im using ubuntu 5.10 with kernel 2.6.12-10-386 and I tried this: sudo make -kpkg --initrd --2.6.12-10-386=-custom kernel_image kernel_headers

[COLOR="Red"]make: invalid option -- g
make: unrecognized option `--initrd'
make: unrecognized option `--2.6.12-10-386=-custom'[/COLOR]
__________________________________________________________________________________________________
Did go as su and I think I did that part now.. Here comes an another:
 sudo make-kpkg --initrd &#8211;append-to-version=-dag kernel_image kernel_headers
Error: Unknown target &#8211;append-to-version=-dag
use --targets to display help on valid targets.



Thanks for your help

Dag[/QUOTE]


Don't worry Dag, it's just a typo, it's "make-kpkg" and not "make -kpkg" (remove the space in between, it's not the "make" command with a -kpkg option you are issuing here). And the --append-to-version option takes no "=".

---

### Post by tseliot on 2006-03-17
[QUOTE=dag]Tried to make a new kernel and it stops at point 8. The commands don't work on my ubuntu.. I'm a newbie so I need a little help here :-) Did do all the other steps from point 1 - 6, skip 7 and go to point 8. 
Im using ubuntu 5.10 with kernel 2.6.12-10-386 and I tried this: sudo make -kpkg --initrd --2.6.12-10-386=-custom kernel_image kernel_headers

[COLOR="Red"]make: invalid option -- g
make: unrecognized option `--initrd'
make: unrecognized option `--2.6.12-10-386=-custom'[/COLOR]
__________________________________________________________________________________________________
Did go as su and I think I did that part now.. Here comes an another:
 sudo make-kpkg --initrd &#8211;append-to-version=-dag kernel_image kernel_headers
Error: Unknown target &#8211;append-to-version=-dag
use --targets to display help on valid targets.



Thanks for your help

Dag[/QUOTE]
The exact command is this (copy and paste it):
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

make sure you use all the hyphens needed: it's "--append-to-version" and not "-append-to-version"

---

### Post by Bazon on 2006-03-19
three questions about this:
1.* sudo make oldconfig*
what config refers this old config to? I got at least severall configs in /boot.

2. In other Kernel How-tos there is something about *make modules_install*, but I can't find that here, what's about that?

3. With my custom kernel I got a problem with Usplash, what could I have done wrong?

Thanks,
Bazon

---

### Post by nrwilk on 2006-03-19
[QUOTE=Bazon]3. With my custom kernel I got a problem with Usplash, what could I have done wrong?[/QUOTE]

You've done nothing wrong, Bazon.  It's an issue with kernel 2.6.15.  We are all experiencing it.  If you go back several pages in this thread, there is som discussion about it.  You can disable the graphical splash, so that you see the basic console start-up process.  Other than that, I haven't seen someone yet say that they've found a way to fix the graphical splash.

I do know that dapper uses 2.6.15, and the graphical splash is working there, so there is some way to pull it off.

tseliot, will we have this problem when compiling kernels for Dapper in the future?  Or, will the "make oldconfig" transfer the ubuntu dev's illmatic kernel splash skills to the new kernels we compile?

---

### Post by Bazon on 2006-03-19
[QUOTE=nrwilk]You've done nothing wrong, Bazon.  It's an issue with kernel 2.6.15.  We are all experiencing it.[/QUOTE]
But I'm using 2.6.12.3 according to [this HowTo](https://wiki.ubuntu.com/ViaEpiaDriHowto) + [linked patch](http://www.epialinux.org/files/patch-2.6.12.3-epia.bz2).
And with 2.6.12-10 (recent Kernel for Ubuntu 5.0), USplash works.
Is maybe something wrong with [my config](http://home.arcor.de/bazonbloch/files/logs/Epia2.6.12.config)?
I searched for the string "splash" but couldn't find anything...

---

### Post by tseliot on 2006-03-19
[QUOTE=Bazon]three questions about this:
1.* sudo make oldconfig*
what config refers this old config to? I got at least severall configs in /boot.[/QUOTE]
Copy the config file you wish to use to your /usr/src/linux folder and rename it as ".config". The type sudo make oldconfig.

[QUOTE=Bazon]2. In other Kernel How-tos there is something about *make modules_install*, but I can't find that here, what's about that?[/QUOTE]
Ubuntu has its own way to compile kernels. Please see the section of my guide about compiling modules.

[QUOTE=Bazon]3. With my custom kernel I got a problem with Usplash, what could I have done wrong?[/QUOTE]
type:
nano /boot/grub/menu.lst

look for the lines about your kernel:
```
title		Ubuntu, kernel 2.6.15-18-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-18-k7 root=/dev/hdb1 ro quiet [COLOR="Blue"]splash[/COLOR]
initrd		/boot/initrd.img-2.6.15-18-k7
savedefault
```

and remove the word I put in blue.

Then restart your computer. You won't see the bootsplash but you won't see a black screen either.

---

### Post by tseliot on 2006-03-19
[QUOTE=nrwilk]tseliot, will we have this problem when compiling kernels for Dapper in the future?  Or, will the "make oldconfig" transfer the ubuntu dev's illmatic kernel splash skills to the new kernels we compile?[/QUOTE]
I haven't checked this out yet. I'll do it as soon as I have some spare time

---

### Post by Bazon on 2006-03-19
thanks for you tips!

About USplash:
[QUOTE=tseliot]
type:
nano /boot/grub/menu.lst

look for the lines about your kernel:
```
...kernel		/boot/vmlinuz-2.6.15-18-k7 root=/dev/hdb1 ro quiet [COLOR="Blue"]splash[/COLOR]

```
and remove the word I put in blue.

Then restart your computer. You won't see the bootsplash but you won't see a black screen either.[/QUOTE]Oh, that reproduced the behaviour I had before. (Maybe I should have explained more precisely, I didn't know that there could be black screens, too...)

But now I switched to [Splashy](http://wiki.ubuntuusers.de/Bootsplash?highlight=%28splashy%29) and at least that works... :)

---

### Post by mattlach on 2006-04-30
Do the binary Ubuntu kernels include non-kernel modules?

I ask because my network seems to depend on a module named "forcedeth" which I can't seem to find anywhere in menuconfig...  

Anyone know where I can find this module?


Also, what are the benefits of using kernel-package to create a .deb and installing it, instead of just doing:

# make && make modules modules_install

copying the image to /boot and editing grub.conf?

---

### Post by lyleogle on 2006-04-30
I downloaded some files to make a driver for Buslink L30 USB hard drive.  Make would not run, do I need to unpack something?  I have no clue but willing to try and learn.

Regards,

---

### Post by tseliot on 2006-05-01
[QUOTE=mattlach]Do the binary Ubuntu kernels include non-kernel modules?

I ask because my network seems to depend on a module named "forcedeth" which I can't seem to find anywhere in menuconfig...  

Anyone know where I can find this module?[/QUOTE]
I have that kernel module on Ubuntu Dapper

```
:~$ locate forcedeth
/lib/modules/2.6.15-19-386/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-20-386/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-20-k7/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-21-386/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-21-k7/kernel/drivers/net/forcedeth.ko
/usr/src/linux-headers-2.6.15-20-k7/include/config/forcedeth
/usr/src/linux-headers-2.6.15-20-k7/include/config/forcedeth/module.h
/usr/src/linux-headers-2.6.15-20/include/config/forcedeth.h
/usr/src/linux-headers-2.6.15-21-k7/include/config/forcedeth
/usr/src/linux-headers-2.6.15-21-k7/include/config/forcedeth/module.h
/usr/src/linux-headers-2.6.15-21/include/config/forcedeth.h
/usr/src/linux-source-2.6.15/drivers/net/forcedeth.c
```

[QUOTE=mattlach]Also, what are the benefits of using kernel-package to create a .deb and installing it, instead of just doing:

# make && make modules modules_install

copying the image to /boot and editing grub.conf?[/QUOTE]
If you make a deb package, grub is updated automatically and the kernel image is automatically copied to /boot.
And uninstalling a kernel is easier (as it's a package).

And, last but not least, that's the way we do it in Ubuntu ;)

---

### Post by tseliot on 2006-05-01
[QUOTE=lyleogle]I downloaded some files to make a driver for Buslink L30 USB hard drive.  Make would not run, do I need to unpack something?  I have no clue but willing to try and learn.

Regards,[/QUOTE]
I have never tried those drivers. What the output of the error?

---

### Post by mattlach on 2006-05-01
[QUOTE=tseliot]I have that kernel module on Ubuntu Dapper

```
:~$ locate forcedeth
/lib/modules/2.6.15-19-386/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-20-386/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-20-k7/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-21-386/kernel/drivers/net/forcedeth.ko
/lib/modules/2.6.15-21-k7/kernel/drivers/net/forcedeth.ko
/usr/src/linux-headers-2.6.15-20-k7/include/config/forcedeth
/usr/src/linux-headers-2.6.15-20-k7/include/config/forcedeth/module.h
/usr/src/linux-headers-2.6.15-20/include/config/forcedeth.h
/usr/src/linux-headers-2.6.15-21-k7/include/config/forcedeth
/usr/src/linux-headers-2.6.15-21-k7/include/config/forcedeth/module.h
/usr/src/linux-headers-2.6.15-21/include/config/forcedeth.h
/usr/src/linux-source-2.6.15/drivers/net/forcedeth.c
```
[/QUOTE]

Hmm.  I am clearly going to have to look through the kernel again.  In desperation I thought I had opted to compile ALL the network drivers as modules, just so I could find it, but it still wasnt compiled with the kernel.   Maybe I just missed it.  I'll have to take another look.

[QUOTE=tseliot]
If you make a deb package, grub is updated automatically and the kernel image is automatically copied to /boot.
And uninstalling a kernel is easier (as it's a package).

And, last but not least, that's the way we do it in Ubuntu ;)[/QUOTE]

ok then :)  Is there any way to alter how the automatic grub.conf updater generated the grub.conf (or menu.lst in this case) cause it's getting crowded in there. 

I've been using Gentoo since the early betas, so I am having to unlearn a lot of stuff I have learned :p

---

### Post by lyleogle on 2006-05-01
I tried to make it but it would not run.  I believe it copuld not find "make",I only tried once, I  will give it a go again.

---

### Post by zerocapacity on 2006-05-01
hey guys I new to ubuntu and am having fun with this. I have figured my way through it thus far with the help of many great posters and responders in this communtiy.

I have run into one problem though this line here

sudo apt-get install libqt3-headers libqt3-mt-dev

returns the error = libqt3-mt-dev: Depends: xlibs-static-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
Depends: libmng-dev (>= 1.0.3) but it is not going to be installed
Depends: libpng12-0-dev
Depends: zlib1g-dev but it is not going to be installed
Depends: libfreetype6-dev but it is not going to be installed
Depends: libxft-dev but it is not going to be installed

now When I try to install these I get this error =@ubuntu:~$ sudo apt-get install libqt3-headers libqt3-mt-dev xlibs-static-dev libmng-dev libmng-dev libpng12-dev zlib1g-dev lib freetype6-dev libxft-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package lib


: Note I changed the libpng12-0-dev to libpng-dev because it told me to


I will appreciate any help in this matter and hope to help others as I get to know this wonderful OS.

Thanks

Z

P.S. I have enabled all the archives and still no joy.

---

### Post by garba on 2006-05-01
Why on earth do people insist on building kernels as root in /usr/src? It's terribly insecure, just imagine what a faulty makefile with some bogus rm might lead to.

There are just too many bake-your-own-linux-kernel howto's out there which promote this perverted practice, not to mention the dread "linux" symlink thingie... :mrgreen:

---

### Post by tseliot on 2006-05-02
[QUOTE=garba]Why on earth do people insist on building kernels as root in /usr/src? It's terribly insecure, just imagine what a faulty makefile with some bogus rm might lead to.

There are just too many bake-your-own-linux-kernel howto's out there which promote this perverted practice, not to mention the dread "linux" symlink thingie... :mrgreen:[/QUOTE]
If you're more experienced than me, you might suggest a better way to compile kernels. You might tell me how to improve my guide or write a new guide yourself. That's what I call "constructive criticism".

I'm sharing with our Community all the knowloedge I managed to gather in 1 year of experience with Linux. I encourage you to do the same.

---

### Post by tseliot on 2006-05-02
[QUOTE=zerocapacity]hey guys I new to ubuntu and am having fun with this. I have figured my way through it thus far with the help of many great posters and responders in this communtiy.

I have run into one problem though this line here

sudo apt-get install libqt3-headers libqt3-mt-dev

returns the error = libqt3-mt-dev: Depends: xlibs-static-dev (>= 4.3.0.dfsg.1-4) but it is not going to be installed
Depends: libmng-dev (>= 1.0.3) but it is not going to be installed
Depends: libpng12-0-dev
Depends: zlib1g-dev but it is not going to be installed
Depends: libfreetype6-dev but it is not going to be installed
Depends: libxft-dev but it is not going to be installed

now When I try to install these I get this error =@ubuntu:~$ sudo apt-get install libqt3-headers libqt3-mt-dev xlibs-static-dev libmng-dev libmng-dev libpng12-dev zlib1g-dev lib freetype6-dev libxft-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package lib


: Note I changed the libpng12-0-dev to libpng-dev because it told me to


I will appreciate any help in this matter and hope to help others as I get to know this wonderful OS.

Thanks

Z

P.S. I have enabled all the archives and still no joy.[/QUOTE]
I've never had a dependecy problem using only Ubuntu's repos, so the questions are:
1) are you using Ubuntu Dapper or Breezy (or did you mix their repos)?
2) Did you use other repos than Ubuntu's (e.g. Debian's)
3) Did you remember anything else which could be of help (some unsupported package you installed, etc.)?

---

### Post by zerocapacity on 2006-05-02
[QUOTE=tseliot]I've never had a dependecy problem using only Ubuntu's repos, so the questions are:
1) are you using Ubuntu Dapper or Breezy (or did you mix their repos)?
2) Did you use other repos than Ubuntu's (e.g. Debian's)
3) Did you remember anything else which could be of help (some unsupported package you installed, etc.)?[/QUOTE]


1) I was using breezy (upgraded to dapper today)
2) Nope was told never to do thatet a diffrent app)
3) thats all the error message was I will try later and see (cept I am getting it also with dapper now trying to get a diff app)


Z

---

### Post by garba on 2006-05-02
Sorry tseliot, you're damn right here, forgive me for my comment which might have sounded kind of blunt, it was just supposed to be ironic... anyway, no, it's unlikely I am more knowledgeble than you. Still I feel that building a custom kernel as root is very, very insecure and totally pointless, as I've already stated this is a common practice in the linux world, just like the "linux" symlink thing was a few years back. Moreover, it's against educational principles, because it makes the kernel look like some "special" thing which needs some extra "power" to be built, but this is not the case. Hence I do hereby invite you to amend your guide and make proper use of the "fakeroot" program, please help me with my crusade against building debs as root ;)

---

### Post by thasheep on 2006-05-03
Your guide is very detailed an nice, but I have to agree about the fakeroot option so I've edited your guide to save your system in case of a malicious/negligent Makefile. Please forgive my plaguarism.

Open Terminal or Konsole (if it's not open yet) and type these commands:

sudo apt-get update
sudo apt-get install build-essential [color="#ff0000"]fakeroot[/color]  # gcc is pulled in by build-essential these anyway
sudo apt-get install linux-source # if you want to use the official ubuntu source, otherwise get your source (and patches) from kernel.org or wherever else
sudo apt-get install libncurses5-dev # only needed if you're doing make menuconfig
sudo apt-get install libqt3-mt-dev # only needed if you're doing make xconfig

sudo apt-get install ndiswrapper-source nvidia-kernel-source # if needed

mkdir ~/build
cd ~/build
tar -jxvf /usr/src/linux-source-2.6.12.tar.bz2 # if using non-ubuntu source, give the path to where you saved it

cd linux-*

Check that any patch(es) you have will apply cleanly and then apply them, eg
bzcat /path/to/patch.bz2 | patch -p1 --dry-run
bzcat /path/to/patch.bz2 | patch -p1

if the patch suffix is .gz not .bz2, do
zcat /path/to/patch.gz | patch -p1 --dry-run
zcat /path/to/patch.gz | patch -p1

if the patch suffix is .patch
cat /path/to/patch.patch | patch -p1 --dry-run
cat /path/to/patch.patch | patch -p1

cp /boot/config-`uname -r` .config # get your current config
make oldconfig (so as not to compile the entire kernel from scratch)

tar -jxf /usr/src/ndiswrapper-source.tar.bz2  # only if needed
tar -zxf /usr/src/nvidia-kernel-source.tar.gz  # again only if needed, -zxf rather than -jxf tells tar to use gzip rather than bzip2

If it asks you any questions just press Enter (so as to select the recommended answer)

make menuconfig   # or make xconfig or make gconfig

[color="#ff0000"]If you know what your hardware is (lsmod and lspci are your friends) and what filesystems you use (mount will tell you this, but be sure to enable the iso stuff for cds/dvds and fat/vfat if you want to mount most removable drives, ntfs is used for windows 2000/xp), be ruthless here and leave out as much as you (know you) can. This way, you'll get the the compilation time down to 10-20 min on a recent computer. It'll also reduce boot time and make your system run faster[/color]

make-kpkg clean

[color="#ff0000"]fakeroot[/color] make-kpkg --initrd --append-to-version=-[COLOR="Red"]custom[/COLOR] [color="#ff0000"]--stem=linux[/color] \
kernel_image kernel_headers
[color="#ff0000"]if you're using restricted modules, add modules_image to the line above.
changing the stem to linux (instead of kernel) is ubuntu now the standard - the packages will be called linux-image-[kernelversion] instead of kernel-image-[kernelversion], etc[/color]

[COLOR="#ff0000"]NOTE: you can put whatever you want instead of &#8220;custom&#8221;[/COLOR]

cd ..

ls

You'll see a list of the names of the files in the folder as well as the names of your new kernel image , kernel headers (and modules if you have followed Point 7); they should look (approximately)like these ones:

linux-image-2.6.12-custom_10.00.Custom_i386.deb
linux-headers-2.6.12-custom_10.00.Custom_i386.deb
[your extra modules go here]

sudo dpkg -i kernel-image-2.6.12-custom_10.00.Custom_i386.deb
sudo dpkg -i kernel-headers-2.6.12-custom_10.00.Custom_i386.deb
sudo dkpkg -i [extra modules.deb]

[COLOR="#ff0000"]REMEMBER NOT TO UNINSTALL your previous kernel (just in case anything goes wrong)[/COLOR] [COLOR="#ff0000"](i.e. don't do anything else apart from following the instructions)[/COLOR]

Restart your computer.

---

### Post by tseliot on 2006-05-03
Ok guys, I'll update the guide when I have some time. I promise.

Now I'm really up to my eyes (I have deadlines :(  )

---

### Post by lyleogle on 2006-05-03
[QUOTE=tseliot]I have never tried those drivers. What the output of the error?[/QUOTE]
ts

I recompiled the kernel via your instruction on the forum flawlessly, on a PII-266.  I went to sleep and checked this AM and booted this pm after work.

On the subject of the Buslink L30last three lines: USB Drive compilation it did not complete:

_last three lines:_
make[1]: *** [usbide-core.o] Error 1
make[1]: Leaving directory `/home/lyle/usb_driver/usbide'
make: *** [all] Error 2last three lines:

Errors and warnings spewed all over,, looked lile something I would write, I'm a hardware guy by trade.

I might go through the output and see if I can whilltle away on the errors

Again, thank for the kernel building guide, works GREAT!

Regards,

Lyle

---

### Post by ashrack on 2006-05-07
I installed "fglrx-kernel-source" and did everything per your guide. And my kernel compiles fine, but heres the error when trying to compile module FGLRX:

I used this line to compile it:
```
root@tom:/usr/src/linux# make-kpkg clean && make-kpkg --append-to-version=-hiber-fglrx kernel_image kernel_headers modules_image

```
and I attach the error that I got when it started to compile FGLRX module:

[ATTACH]9189[/ATTACH]

---

### Post by tseliot on 2006-05-08
[QUOTE=ashrack]I installed "fglrx-kernel-source" and did everything per your guide. And my kernel compiles fine, but heres the error when trying to compile module FGLRX:

I used this line to compile it:
```
root@tom:/usr/src/linux# make-kpkg clean && make-kpkg --append-to-version=-hiber-fglrx kernel_image kernel_headers modules_image

```
and I attach the error that I got when it started to compile FGLRX module:

[ATTACH]9189[/ATTACH][/QUOTE]
I don't know what went wrong but you can try this:
Install the kernel you have compiled and restart your computer.
Install module-assistant:
```
sudo apt-get install module-assistant
```
then
```
sudo module-assistant 
```

And use module-assistant to Select the driver (i.e. the module) you need to compile) and then build it.

---

### Post by vjlinux on 2006-05-20
Hello Alberto,

Thanks for this HOW-TO! It worked just fine the very first time and I enjoyed my first Linux kernel building (2.6.12) experience! 
The only thing that did not work was that the wirless interface did not show up. It was showing up before. Any idea what I did wrong? After reverting to the old kernel (2.6.10) the wireless interface showed again.
But nontheless your document was simply great to experience the first kernel building! 
Thanks again.
Open source/Linux rocks!

- Vijay

---

### Post by tseliot on 2006-05-20
[QUOTE=vjlinux]Hello Alberto,

Thanks for this HOW-TO! It worked just fine the very first time and I enjoyed my first Linux kernel building (2.6.12) experience! 
The only thing that did not work was that the wirless interface did not show up. It was showing up before. Any idea what I did wrong? After reverting to the old kernel (2.6.10) the wireless interface showed again.
But nontheless your document was simply great to experience the first kernel building! 
Thanks again.
Open source/Linux rocks!

- Vijay[/QUOTE]
Your wireless card needs the restricted modules. You should see the part of my guide about compiling kernel modules.

---

### Post by ashrack on 2006-05-30
[QUOTE=tseliot]I don't know what went wrong but you can try this:
Install the kernel you have compiled and restart your computer.
Install module-assistant:
```
sudo apt-get install module-assistant
```
then
```
sudo module-assistant 
```

And use module-assistant to Select the driver (i.e. the module) you need to compile) and then build it.[/QUOTE]

I dont have ATI or FGLRX anywhere on the module list. But nvidia-kernel* I have.
What else to do?

this are the packages for FGLRX that I have installed:
```
fglrx-kernel-source is keeping the following 1 packages installed:
  dpatch
Keep fglrx-kernel-source? [Ynpsiuqx?], [H]elp: S
Keep module-assistant? [Ynpsiuqx?], [H]elp: S
Keep xorg-driver-fglrx-dev? [Ynpsiuqx?], [H]elp: S

```

---

### Post by tseliot on 2006-05-30
[QUOTE=ashrack]I dont have ATI or FGLRX anywhere on the module list. But nvidia-kernel* I have.
What else to do?

this are the packages for FGLRX that I have installed:
```
fglrx-kernel-source is keeping the following 1 packages installed:
  dpatch
Keep fglrx-kernel-source? [Ynpsiuqx?], [H]elp: S
Keep module-assistant? [Ynpsiuqx?], [H]elp: S
Keep xorg-driver-fglrx-dev? [Ynpsiuqx?], [H]elp: S

```[/QUOTE]
I think you should ask for help on the thread of the guide about ATI drivers. I use only Nvidia cards

---

### Post by ashrack on 2006-05-31
OK
tanx anyway

EDIT: Opened a new thread about my problem, located here:
[http://ubuntuforums.org/showthread.php?p=1071660#post1071660](http://ubuntuforums.org/showthread.php?p=1071660#post1071660)
So any talks of this issue should go into the afore mentioned guide.

---

### Post by RichC on 2006-06-01
Hi,
Just installed Breezy Badger for a first time try at Linux.
Having trouble at:
> sudo apt-get install linux-tree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-tree

The linux box is off-line since i'm trying to install the driver for the dialup modem so that I can get on-line.

Any ideas?
Thanks

---

### Post by tseliot on 2006-06-02
[QUOTE=RichC]Hi,
Just installed Breezy Badger for a first time try at Linux.
Having trouble at:
> sudo apt-get install linux-tree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-tree

The linux box is off-line since i'm trying to install the driver for the dialup modem so that I can get on-line.

Any ideas?
Thanks[/QUOTE]
Apt-get needs the Internet connection in order to work.

---

### Post by deadgoon on 2006-06-03
TS,

Will you be creating a HOWTO for Dapper, or is it safe to use this one?

---

### Post by xXx 0wn3d xXx on 2006-06-03
[QUOTE=deadgoon]TS,

Will you be creating a HOWTO for Dapper, or is it safe to use this one?[/QUOTE]
It should be safe to use on Dapper. I have used this guide to compile headers and modules for my custom kernel on Dapper and it worked.

---

### Post by tseliot on 2006-06-04
[QUOTE=MasterChief1234]It should be safe to use on Dapper. I have used this guide to compile headers and modules for my custom kernel on Dapper and it worked.[/QUOTE]
Thanks for reporting

I need to tweak it a bit though in order to solve a few issues

---

### Post by SoggyCornflake on 2006-06-05
I had compiled a custom kernel with the Breezy release that allowed my tv card to be seen and it used alsa sound modules.  I lost both when I upgraded, so back to compiling. . . 

I followed the newbie guide to compling a kernel and when I entered, **sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers **, I got the following error message: 

> # For LKCD enabled kernels
test ! -f Kerntypes ||  cp Kerntypes                                   \
                        debian/tmp-image/boot/Kerntypes-2.6.12-custom
test ! -f Kerntypes ||  chmod 644                                      \
                        debian/tmp-image/boot/Kerntypes-2.6.12-custom
rm -f debian/tmp-image/lib/modules/2.6.12-custom/build
dpkg-gencontrol -DArchitecture=i386 -isp                   \
                        -pkernel-image-2.6.12-custom -Pdebian/tmp-image/
dpkg-gencontrol: error: package kernel-image-2.6.12-custom not in control info
make[1]: *** [real_stamp_image] Error 255
make[1]: Leaving directory `/usr/src/linux-source-2.6.12-2.6.12'
make: *** [kernel-image-deb] Error 2



(Seemingly it compiled ok, it was just at the end of the process.)

Any hints as to what is gving me this error?  Thanks in advance.

---

### Post by tseliot on 2006-06-05
[QUOTE=SoggyCornflake]I had compiled a custom kernel with the Breezy release that allowed my tv card to be seen and it used alsa sound modules.  I lost both when I upgraded, so back to compiling. . . 

I followed the newbie guide to compling a kernel and when I entered, **sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers **, I got the following error message: 



(Seemingly it compiled ok, it was just at the end of the process.)

Any hints as to what is gving me this error?  Thanks in advance.[/QUOTE]
As I have already said I haven't tested this guide on Dapper.

Why don't you use Dapper's kernel sources (2.6.15) and just enable the support for your tv card ?
And remember not to do the "export CC" thing with that kernel (it needs Gcc-4.0)

---

### Post by DagMan on 2006-06-06
Thanks tselliot, for this and more so for the NVIDIA driver guide.

In Dapper the package appears to be linux-source or linux-source-2.5.15 (I think) and not linux-tree.  Perhaps I'm missing a repository though.  I used linux-source-2.5.15 instead of linux-tree using this guide:
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)
Hopefully this was the correct way to do it.  Can someone verify if this is correct or not please.

If it is correct, the only extra thing I needed to do, for my system, was to copy over a file called Makefile.cpu from the old headers to the new ones at /usr/src/kernel-headers*/arch/i36/ when using method 2 of the NVIDIA drivers guide for Dapper.  I edited the file to be sure that it would find my architecure properly and can't say if it would work fine or not on it's own and it very well may be good how it is... my editing was sloppy and perhaps not necisary.   Either way it looks like it's fine if the processor type isn't changed in menuconfig before compiling though.
Can someone please state whether or not this was a necicary step for them as well.

---

### Post by tseliot on 2006-06-06
[QUOTE=DagMan]Thanks tselliot, for this and more so for the NVIDIA driver guide.

In Dapper the package appears to be linux-source or linux-source-2.5.15 (I think) and not linux-tree.  Perhaps I'm missing a repository though.  I used linux-source-2.5.15 instead of linux-tree using this guide:
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)
Hopefully this was the correct way to do it.  Can someone verify if this is correct or not please.[/QUOTE]
That's right. Thanks for reporting

[QUOTE=DagMan]If it is correct, the only extra thing I needed to do, for my system, was to copy over a file called Makefile.cpu from the old headers to the new ones at /usr/src/kernel-headers*/arch/i36/ when using method 2 of the NVIDIA drivers guide for Dapper.  I edited the file to be sure that it would find my architecure properly and can't say if it would work fine or not on it's own and it very well may be good how it is... my editing was sloppy and perhaps not necisary.   Either way it looks like it's fine if the processor type isn't changed in menuconfig before compiling though.
Can someone please state whether or not this was a necicary step for them as well.[/QUOTE]
Why do you need to do that?

---

### Post by DagMan on 2006-06-06
Thanks.

Don't know really why on the other thing other than the NVIDIA install exited with an error and the log file stated that it couldn't find that file.  I had a Makefile but not a Makefile.cpu in the directory.  The old directory had both.

The file is apparently passing the CPU type to the install but whether that's to match what the kernel options say or just what the actual architecture is I don't know.

Edit:  If it isn't usually necissary to do that, and having a look at the updated guide, I should throw out for thought that synaptic reporting linux-source and linux-source-2.6.15 as having differant filesizes, it could have been a result of me using the latter.

---

### Post by tseliot on 2006-06-06
[QUOTE=DagMan]
Edit:  If it isn't usually necissary to do that, and having a look at the updated guide, I should throw out for thought that synaptic reporting linux-source and linux-source-2.6.15 as having differant filesizes, it could have been a result of me using the latter.[/QUOTE]
linux-source is a dummy file which installs the latest source available

---

### Post by shelbydz on 2006-06-06
I'm trying this on dapper so I can disable agpgart and use nvagp. I've followed the instructions up to 7, I run  
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
but when thats done, I cd /usr/src and, there's no new files in there:
ls
linux  linux-source-2.6.15  linux-source-2.6.15.tar.bz2  modules  nvidia-kernel-source.tar.gz

what am I missing? I'm not getting the .deb files
the last few lines of the command, output like this:

make[5]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[4]: *** [drivers/usb/net/zd1211] Error 2
make[3]: *** [drivers/usb/net] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [stamp-build] Error 2

Any ideas?

---

### Post by tseliot on 2006-06-06
[QUOTE=shelbydz]I'm trying this on dapper so I can disable agpgart and use nvagp. I've followed the instructions up to 7, I run  
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image
but when thats done, I cd /usr/src and, there's no new files in there:
ls
linux  linux-source-2.6.15  linux-source-2.6.15.tar.bz2  modules  nvidia-kernel-source.tar.gz

what am I missing? I'm not getting the .deb files
the last few lines of the command, output like this:

make[5]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[4]: *** [drivers/usb/net/zd1211] Error 2
make[3]: *** [drivers/usb/net] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make: *** [stamp-build] Error 2

Any ideas?[/QUOTE]
Did you have any USB devices connected to your computer when you tried to compile the kernel?

IF NOT, you might need to disable the driver which causes conflict:
sudo make menuconfig
and get to
/Device Drivers/USB support/USB Network adapters/USB ZD1211 based wireless device support

press the spacebar to disable it.

Then recompile the kernel

---

### Post by DagMan on 2006-06-06
[QUOTE=tseliot]linux-source is a dummy file which installs the latest source available[/QUOTE]
Hi tseliot,
The package I pulled in is the same as what the dummy package was giving apparently but I still wanted to make sure that I didn't miss something.

I uninstalled the kernel and manually removed everything left over, including the modules folder, then started from scratch.  I didn't use the oldconfig tool but told menuconfig to load the file that was in grub.  It re-produced the problem I had with the NVIDIA install method 2 and the same fix worked for me again.

I don't know if others have run into this as well but perhaps it's something to keep in mind.

The log file overwrote itself when I fixed it and made a successfull install but as I said, the error was that the file didn't exist.  This occured with both NVIDIA installers 8756 and 8762.  

Also, in all instances I was using the 686 config file or made the config while running the 686 kernel, from the repos, and not the 386 that's installed with the system.

As for the Makefile.cpu passing values over and whether it needs to be edited or not when the processor type is changed, I really doubt it, it looks like it was just to pass to the compiler so it shouldn't matter. You can look at it in the log file once the install runs correctly.  Sorry if that's bit obvious for you but it's something I wasn't clear about.

This is moving off topic quite a bit now but that covers everything, and also I forgot to mention that in my case I removed "splash" from menu.lst in grub because I was getting a blank screen on boot and shutdown.

---

### Post by Nibiruet on 2006-06-11
**[COLOR="Red"]PROBLEM SOLVED[/COLOR] - thanks for replies.**
Have kernel 2.6.16.20-686 up and running. All seem to work ok _except_ Firestarter and programs requiring Internet connectivity under Wine. 

Firefox, Thunderbird, Gaim etc. working just fine.

Firestarter gives following error message:
               ** Failed to start the firewall**
               **Your kernel does not support iptables**
                Please check your network device settings and make sure your internet              connection is active.

I recall seing an error message flash past during boot up regarding iptables.

Please help!
Thanks :(

---

### Post by DagMan on 2006-06-11
The kernel options for iptables are a little differant for 2.6.16

I got this from the gentoo wiki but I still wasn't able to do it and had to copy a peice of someone's config file.  After doing that I now think that perhaps it will work if it's selected as modules.

```
Networking  ---->
 Networking options  ---->
  Network Packet Filtering (replaces Ipchains)--->
   Core Netfilter Configuration ---->
    ["enable"] Netfilter Xtables support (required for ip_tables)
   Network Packet Filtering (replaces Ipchains)--->
    Netfilter Configuration --->
     ["enable"] IP tables support (required for filtering/masq/NAT)
```

You can try that, enabling them as modules, if you feel like putting the extra time into it... don't know if it will work or not.

Edit: Also it was necissary to autoload the module on boot.  I don't know how to do this in Ubuntu.
Found this just now too.  Seems like there's some success using something else.  Worth a search through maybe [http://ubuntuforums.org/showthread.php?t=157560&](http://ubuntuforums.org/showthread.php?t=157560&)

---

### Post by cfp999 on 2006-06-24
I have been following this guide step-by-step. After doing this:

sudo cp /boot/config-2.6.15-25-k7 .config
make xconfig

I get a lot of error-outputs in the terminal while editing/configuring the kernel:

```
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:54:warning: trying to assign nonexistent symbol CC_ALIGN_FUNCTIONS
.config:55:warning: trying to assign nonexistent symbol CC_ALIGN_LABELS
.config:56:warning: trying to assign nonexistent symbol CC_ALIGN_LOOPS
```

I found this in another thread:

[http://ubuntuforums.org/showthread.php?t=46752&highlight=assign+nonexistant+symbol]("http://ubuntuforums.org/showthread.php?t=46752&highlight=assign+nonexistant+symbol")

I gather it might have something to do with the .config file being from another (wrong) kernel version. I have previously updated the stock Ubuntu Dapper kernel to the k7-variant. Somewhere else I read that the errors are caused by me trying to built a new 2.6.17 kernel with a .config file from 2.6.15-25 and that many of the .config options went away between those two
versions. So according to this, those warnings are about options that have gone away. Should I just ignore them, or how can I fix this?

---

### Post by tseliot on 2006-06-24
[QUOTE=cfp999]I have been following this guide step-by-step. After doing this:

sudo cp /boot/config-2.6.15-25-k7 .config
make xconfig[/QUOTE]
Try this:
```
sudo cp /boot/config-2.6.15-25-k7 .config
sudo make oldconfig
sudo make menuconfig
```

---

### Post by ashrack on 2006-06-24
<So according to this, those warnings are about options that have gone away.>
correct!

<Should I just ignore them>
Yes

---

### Post by cfp999 on 2006-06-25
Thanks! I am pleased to say that everything worked out, and I am now running 2.6.17 (ck1).

---

### Post by carlton on 2006-07-04
Hi all i followed the instruction but when i got to the part of changing the Ati to vesa in the xorg.conf and i rebooted the pc the screen went all funny and i cant see anything. Any idea why was that. Thank you.

---

### Post by tseliot on 2006-07-04
[QUOTE=carlton]Hi all i followed the instruction but when i got to the part of changing the Ati to vesa in the xorg.conf and i rebooted the pc the screen went all funny and i cant see anything. Any idea why was that. Thank you.[/QUOTE]
Try this:
sudo dpkg-reconfigure xserver-xorg

and select the "ati" driver. Press ENTER if you don't know the answer to the other questions.

then restart the xserver:
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)

---

### Post by caesar424 on 2006-07-04
Thanks TS for the great walk-through. I'm actually trying to compile a custom kernel to support Belkin Wireless G USB Network adapter (ralink rt73 chipset), using the package found at the Ralink website.

On step 8, when compiling the kernel, i receive the following message (posted with context):
```

  CC      ipc/util.o
  CC      ipc/msgutil.o
  CC      ipc/msg.o
ipc/msg.c: In function &#8216;sys_msgctl&#8217;:
ipc/msg.c:333: warning: &#8216;setbuf.qbytes&#8217; may be used uninitialized in this function
ipc/msg.c:333: warning: &#8216;setbuf.uid&#8217; may be used uninitialized in this function
ipc/msg.c:333: warning: &#8216;setbuf.gid&#8217; may be used uninitialized in this function
ipc/msg.c:333: warning: &#8216;setbuf.mode&#8217; may be used uninitialized in this function
  CC      ipc/sem.o
ipc/sem.c: In function &#8216;semctl_down&#8217;:
ipc/sem.c:805: warning: &#8216;setbuf.uid&#8217; may be used uninitialized in this function
ipc/sem.c:805: warning: &#8216;setbuf.gid&#8217; may be used uninitialized in this function
ipc/sem.c:805: warning: &#8216;setbuf.mode&#8217; may be used uninitialized in this function
  CC      ipc/shm.o
  CC      ipc/mqueue.o
ipc/mqueue.c: In function &#8216;sys_mq_notify&#8217;:
ipc/mqueue.c:1020: error: too few arguments to function &#8216;netlink_attachskb&#8217;
make[2]: *** [ipc/mqueue.o] Error 1
make[1]: *** [ipc] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.2'
make: *** [stamp-build] Error 2

```

Things to note: I decided to download a vanilla kernel, version 2.6.15.2 and apply the patch chk7. This is the first error message I have received, other than having to move the kernel package to the /usr/src directory before unpacking.

Any insight you could provide would, of course, be greatly appreciated.

---

### Post by caesar424 on 2006-07-04
Upon trying again, I received the following:

```

jrhorn@kubuntumobile:/usr/src/linux$ sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
Please ignore the warning about overriding and ignoring targets above.
These are harmless. They are only invoked in a part of the process
that tries to snarf variable values for the conf.vars file.
echo done >  stamp-configure
test -f stamp-configure || /usr/bin/make -f /usr/share/kernel-package/rules configure
/usr/bin/make  EXTRAVERSION=.2-custom  ARCH=i386 \
                             bzImage
make[1]: Entering directory `/usr/src/linux-2.6.15.2'
  CHK     include/linux/version.h
  CHK     include/linux/compile.h
  CHK     usr/initramfs_list
  CC      ipc/mqueue.o
ipc/mqueue.c: In function &#8216;sys_mq_notify&#8217;:
ipc/mqueue.c:1020: error: too few arguments to function &#8216;netlink_attachskb&#8217;
make[2]: *** [ipc/mqueue.o] Error 1
make[1]: *** [ipc] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.2'
make: *** [stamp-build] Error 2

```

---

### Post by caesar424 on 2006-07-10
BTTT / Help please... n00b looking to learn.

---

### Post by tseliot on 2006-07-11
> **caesar424 said:**
> Upon trying again, I received the following:

```

jrhorn@kubuntumobile:/usr/src/linux$ sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
Please ignore the warning about overriding and ignoring targets above.
These are harmless. They are only invoked in a part of the process
that tries to snarf variable values for the conf.vars file.
echo done >  stamp-configure
test -f stamp-configure || /usr/bin/make -f /usr/share/kernel-package/rules configure
/usr/bin/make  EXTRAVERSION=.2-custom  ARCH=i386 \
                             bzImage
make[1]: Entering directory `/usr/src/linux-2.6.15.2'
  CHK     include/linux/version.h
  CHK     include/linux/compile.h
  CHK     usr/initramfs_list
  CC      ipc/mqueue.o
ipc/mqueue.c: In function ‘sys_mq_notify’:
ipc/mqueue.c:1020: error: too few arguments to function ‘netlink_attachskb’
make[2]: *** [ipc/mqueue.o] Error 1
make[1]: *** [ipc] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.2'
make: *** [stamp-build] Error 2

```

Did you enable something else other than what I suggested in the guide?

---

### Post by mlind on 2006-07-11
Nice guide tseliot. I think you should instuct adding current user to **src** group, so you wouldn't need root privileges for configuring the kernel source on /usr/src folder or making kernel images. I guess using --rootcmd fakeroot would be better.

---

### Post by tseliot on 2006-07-11
> **mlind said:**
> Nice guide tseliot. I think you should instuct adding current user to **src** group, so you wouldn't need root privileges for configuring the kernel source on /usr/src folder or making kernel images. I guess using --rootcmd fakeroot would be better.

You're right. Other users made me notice that before. The exams are killing me and I have so many things to do that I hope to have time to update this guide sooner or later

---

### Post by fiuman on 2006-07-11
Tseliot tnx for ur guide

i have some problem, i have a different error anytime i try to compile kernel (step 8 )
this is my lspci
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:00:0d.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

```
 and this is my cpuinfo
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 6
model name      : AMD Athlon(tm) XP 2000+
stepping        : 2
cpu MHz         : 1660.185
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 3327.20

```

and last, i want to try to compile driver nvidia while compile kernel but i dont know how to get nvidia-kernel-source. i have a gforce2 mx 32mb

tnx for help :)

---

### Post by caesar424 on 2006-07-11
> **tseliot said:**
> Did you enable something else other than what I suggested in the guide?

I followed the guide very closely. I only applied the patch you recommended, and received no errors in doing so, other than noted above. I performed this on a fresh install of kubuntu, and was attempting to compile a vanilla kernel.

I installed everything except linux-tree (no repository for that). After downloading the vanilla kernel, I unzipped it to the /usr/src directory (by moving the file first). Could either actions be the source of the problem? To my knowledge, I've stated everything I did that deviated from the guide.

Thanks again for your help, and good luck with your exams!

---

### Post by tseliot on 2006-07-12
> **caesar424 said:**
> I followed the guide very closely. I only applied the patch you recommended, and received no errors in doing so, other than noted above. I performed this on a fresh install of kubuntu, and was attempting to compile a vanilla kernel.

I installed everything except linux-tree (no repository for that). After downloading the vanilla kernel, I unzipped it to the /usr/src directory (by moving the file first). Could either actions be the source of the problem? To my knowledge, I've stated everything I did that deviated from the guide.

Thanks again for your help, and good luck with your exams!
Which vanilla kernel did you use? linux-2.6.15.2?

You know that you should apply patches to linux-2.6.15 (and not to linux-2.6.15-x), don't you?

---

### Post by tseliot on 2006-07-12
> **fiuman said:**
> Tseliot tnx for ur guide

i have some problem, i have a different error anytime i try to compile kernel (step 8 )
Can you post the error?


> **fiuman said:**
> and last, i want to try to compile driver nvidia while compile kernel but i dont know how to get nvidia-kernel-source. i have a gforce2 mx 32mb

tnx for help :)

Make sure you have all the repositories enabled in your /etc/apt/menu.lst


And BTW why don't you use my script for the Nvidia driver?

---

### Post by fiuman on 2006-07-12
i have compiled my kernel and when i restart running new kernel i got an error about hda unable to create /root or something like this.

my hdparm -i /dev/hda output
```
/dev/hda:

 Model=Maxtor 6Y120L0, FwRev=YAR41BW0, SerialNo=Y31QMRTE
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=240121728
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: (null):  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

```

---

### Post by michaelt on 2006-07-13
400 posts, over 8 months, in a How-To! That fact is not a recommendation: it just does not say "authoritative", "comprehensible", "trustworthy". Too bad.

---

### Post by fiuman on 2006-07-13
tseliot i have fixed my error, i have installed my personal kernel :D

but now i have another problem lol

when i try to install driver nvidia using ur script, i have error "nvidia module not found"

in .config i have enabled ```
CONFIG_FB_NVIDIA=y
CONFIG_FB_NVIDIA_I2C=y
``` before compile

where have i wrong???

and what differents about choice Y or M in config???
tnx so much

---

### Post by tseliot on 2006-07-13
> **michaelt said:**
> 400 posts, over 8 months, in a How-To! That fact is not a recommendation: it just does not say "authoritative", "comprehensible", "trustworthy". Too bad.

Would you mind explaining the meaning of your statement?

If you've got constructive criticism, please share it with us.

If it's not constructive criticism I think you should follow another guide or write your own

---

### Post by tseliot on 2006-07-13
> **fiuman said:**
> tseliot i have fixed my error, i have installed my personal kernel :D

but now i have another problem lol

when i try to install driver nvidia using ur script, i have error "nvidia module not found"

in .config i have enabled ```
CONFIG_FB_NVIDIA=y
CONFIG_FB_NVIDIA_I2C=y
``` before compile

where have i wrong???

and what differents about choice Y or M in config???
tnx so much

The following options are enabled in Ubuntu's default kernel:
```
CONFIG_AGP_NVIDIA=m
CONFIG_FB_NVIDIA=m
CONFIG_FB_NVIDIA_I2C=y

```

---

### Post by fiuman on 2006-07-13
kk tnx so much

---

### Post by fiuman on 2006-07-14
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Jul 14 11:44:16 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: true
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/lib/xorg/modules
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC test with CC="cc".
-> Using the kernel source path
   '/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman' as specified by the
   '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman'
-> Kernel output path: '/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/kernel-headers-2.6.
   15.7-ubuntu1-byfiuman SYSOUT=/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfium
   an'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/kernel-headers-2.6.15.7-ubuntu1-byf
   iuman SUBDIRS=/home/pierpaolo/NVIDIA-Linux-x86-1.0-8762-pkg1/usr/src/nv modu
   les
   /usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman/arch/i386/Makefile:38: /us
   r/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman/arch/i386/Makefile.cpu: No su
   ch file or directory
   make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.15.7-ubuntu
   1-byfiuman/arch/i386/Makefile.cpu'.  Stop.
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```
/us
   r/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman/arch/i386/Makefile.cpu: No su
   ch file or directory

tnx and sorry if i abuse of ur time

---

### Post by tseliot on 2006-07-14
> **fiuman said:**
> ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Jul 14 11:44:16 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: true
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/lib/xorg/modules
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC test with CC="cc".
-> Using the kernel source path
   '/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman' as specified by the
   '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman'
-> Kernel output path: '/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/kernel-headers-2.6.
   15.7-ubuntu1-byfiuman SYSOUT=/usr/src/kernel-headers-2.6.15.7-ubuntu1-byfium
   an'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/kernel-headers-2.6.15.7-ubuntu1-byf
   iuman SUBDIRS=/home/pierpaolo/NVIDIA-Linux-x86-1.0-8762-pkg1/usr/src/nv modu
   les
   /usr/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman/arch/i386/Makefile:38: /us
   r/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman/arch/i386/Makefile.cpu: No su
   ch file or directory
   make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.15.7-ubuntu
   1-byfiuman/arch/i386/Makefile.cpu'.  Stop.
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```
/us
   r/src/kernel-headers-2.6.15.7-ubuntu1-byfiuman/arch/i386/Makefile.cpu: No su
   ch file or directory

tnx and sorry if i abuse of ur time

Read point 8 b) (of Method 2) of my guide about the Nvidia driver or just use my Envy script.

---

### Post by fiuman on 2006-07-14
8 ) Install the driver: IF you are using the kernel that comes by default with Ubuntu (or if you don't know what a kernel is) then type

my kernel is compiled by myself

i try ur script and dont have found linux-headers-2.6.15.7-ubuntu1-byfiuman, infact i have only kernel-headers-2.6.15.7-ubuntu1-byfiuman

after have compiled kernel by my self, in my /usr/src/ directory there was only kernel-headers-2.6.15.7-ubuntu1-byfiuman_10.00.Custom_i386.deb
 and kernel-image-2.6.15.7-ubuntu1-byfiuman_10.00.Custom_i386.deb
, linux-headers-2.6.15.7-ubuntu1-byfiuman_10.00.Custom_i386.deb doesnt exist.

tnx

---

### Post by tseliot on 2006-07-14
> **fiuman said:**
> 8 ) Install the driver: IF you are using the kernel that comes by default with Ubuntu (or if you don't know what a kernel is) then type

my kernel is compiled by myself
That's why I told you to read point 8 **[COLOR="Red"]B[/COLOR]**:
> b) if you are using kernel 2.6.14 or higher you have to type:

> **fiuman said:**
> i try ur script and dont have found linux-headers-2.6.15.7-ubuntu1-byfiuman, infact i have only kernel-headers-2.6.15.7-ubuntu1-byfiuman
That's absolutely normal

---

### Post by fiuman on 2006-07-14
kk its work, but if i put driver "nvidia" in xorg in device section x server dont start, so i have to put "nv"...
what's wrong???

sorry and tnx so much for ur help

---

### Post by tseliot on 2006-07-14
> **fiuman said:**
> kk its work, but if i put driver "nvidia" in xorg in device section x server dont start, so i have to put "nv"...
what's wrong???

sorry and tnx so much for ur help

Let's talk about this problem in this other thread:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

There you should post:
1) the model of your graphic card
2) your /etc/X11/xorg.conf

---

### Post by fiuman on 2006-07-14
kk ty

---

### Post by caesar424 on 2006-07-14
> **tseliot said:**
> Which vanilla kernel did you use? linux-2.6.15.2?

You know that you should apply patches to linux-2.6.15 (and not to linux-2.6.15-x), don't you?

Since it has been about a week, I will start over and post my results. Using the sudo apt-get linux-tree command gives an error, but I've downloaded the kernel source package for my kernel and after installing custom kernel on another computer, the kernel will not boot (blank screen during boot up).

will troubleshoot and try again. Thanks for your help so far!

--Jeff

---

### Post by tseliot on 2006-07-15
> **caesar424 said:**
> Since it has been about a week, I will start over and post my results. Using the sudo apt-get linux-tree command gives an error, but I've downloaded the kernel source package for my kernel and after installing custom kernel on another computer, the kernel will not boot (blank screen during boot up).

will troubleshoot and try again. Thanks for your help so far!

--Jeff

I have updated the guide. If you need to install the kernel source:
```
sudo apt-get install linux-source-2.6.15
```

---

### Post by Toufik on 2006-07-15
Hi, I was a bit worry about compiling my first kernel, this howto seemed to be easy so I decide to try it, but ...

> DEVLIST drivers/usb/net/zd1211/zddevlist.h
make[5]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[4]: *** [drivers/usb/net/zd1211] Error 2
make[3]: *** [drivers/usb/net] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2


Any idea of the problem?  I'm a bit lost!

By the way, I spend one hour trying to install libqt3-mt-dev.  I met everytime unresolved dependencies. My mistake was that I've XGL/compiz, so I had to uncomment these repositories to solve the problem...  Maybe it is worth to tell it in your first post!

Toufik

Dapper on a Vaio Laptop (Pentium M), intel integrated graphic card

---

### Post by Old Jimma on 2006-07-15
Here are 2 questions:

1) Is this kernel compilation good for Dapper running on AMD64 machines?

2) When I typed "sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2" I got the error message: "tar: linux-source-2.6.12.tar.bz2: Cannot open: No such file or directory"

What does this mean?

Thanks,
Phil Smith
Duluth, GA

---

### Post by tseliot on 2006-07-15
> **Phil Smith said:**
> Here are 2 questions:

1) Is this kernel compilation good for Dapper running on AMD64 machines?
This one is better:
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

> **Phil Smith said:**
> 2) When I typed "sudo tar --bzip2 -xvf linux-source-2.6.12.tar.bz2" I got the error message: "tar: linux-source-2.6.12.tar.bz2: Cannot open: No such file or directory"
You'll see it in that guide

---

### Post by atenlaugh on 2006-07-15
If anybody else is having trouble with installing libqt3-mt-dev, it apparently has to do with mesa versions. I started using the last post here: 

[http://www.ubuntuforums.org/showthread.php?t=195943&highlight=libqt3-mt-dev](http://www.ubuntuforums.org/showthread.php?t=195943&highlight=libqt3-mt-dev)

But instead of a sudo apt-get dist-upgrade, I just did: 

> sudo apt-get -f install

Worked for me.

---

### Post by caesar424 on 2006-07-16
> **tseliot said:**
> I have updated the guide. If you need to install the kernel source:
```
sudo apt-get install linux-source-2.6.15
```

Thanks for updating your guide at [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper]("http://doc.gwos.org/index.php/Kernel_Compilation_Dapper").

I have followed the instructions to a T with an error occuring at step 8 as before, pasted below with context. I have attached as much as the shell had displayed up to this point.

This is a kernel compilation attempted on an HP pavilion ze4400 laptop (AMD Athlon XP processor). Standard hardware with the exception of a USB Wireless Adapter, which was not attached during this attempt. I'm running Kubuntu Dapper and have had mild success compiling a custom kernel on my other computer following this guide. Any other information you need I can provide. The error is below:

```
  CC      ipc/util.o
  CC      ipc/msgutil.o
  CC      ipc/msg.o
ipc/msg.c: In function &#8216;sys_msgctl&#8217;:
ipc/msg.c:333: warning: &#8216;setbuf.qbytes&#8217; may be used uninitialized in this function
ipc/msg.c:333: warning: &#8216;setbuf.uid&#8217; may be used uninitialized in this function
ipc/msg.c:333: warning: &#8216;setbuf.gid&#8217; may be used uninitialized in this function
ipc/msg.c:333: warning: &#8216;setbuf.mode&#8217; may be used uninitialized in this function
  CC      ipc/sem.o
ipc/sem.c: In function &#8216;semctl_down&#8217;:
ipc/sem.c:805: warning: &#8216;setbuf.uid&#8217; may be used uninitialized in this function
ipc/sem.c:805: warning: &#8216;setbuf.gid&#8217; may be used uninitialized in this function
ipc/sem.c:805: warning: &#8216;setbuf.mode&#8217; may be used uninitialized in this function
  CC      ipc/shm.o
  CC      ipc/mqueue.o
ipc/mqueue.c: In function &#8216;sys_mq_notify&#8217;:
ipc/mqueue.c:1020: error: too few arguments to function &#8216;netlink_attachskb&#8217;
make[2]: *** [ipc/mqueue.o] Error 1
make[1]: *** [ipc] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.2'
make: *** [stamp-build] Error 2

```

Thanks again for taking the time to look at this and I look forward to any feedback you may provide.

Regards,
Jeff

---

### Post by tseliot on 2006-07-17
> **caesar424 said:**
> Thanks for updating your guide at [http://doc.gwos.org/index.php/Kernel_Compilation_Dapper]("http://doc.gwos.org/index.php/Kernel_Compilation_Dapper").

I have followed the instructions to a T with an error occuring at step 8 as before, pasted below with context. I have attached as much as the shell had displayed up to this point.

This is a kernel compilation attempted on an HP pavilion ze4400 laptop (AMD Athlon XP processor). Standard hardware with the exception of a USB Wireless Adapter, which was not attached during this attempt. I'm running Kubuntu Dapper and have had mild success compiling a custom kernel on my other computer following this guide. Any other information you need I can provide. The error is below:

```
  CC      ipc/util.o
  CC      ipc/msgutil.o
  CC      ipc/msg.o
ipc/msg.c: In function ‘sys_msgctl’:
ipc/msg.c:333: warning: ‘setbuf.qbytes’ may be used uninitialized in this function
ipc/msg.c:333: warning: ‘setbuf.uid’ may be used uninitialized in this function
ipc/msg.c:333: warning: ‘setbuf.gid’ may be used uninitialized in this function
ipc/msg.c:333: warning: ‘setbuf.mode’ may be used uninitialized in this function
  CC      ipc/sem.o
ipc/sem.c: In function ‘semctl_down’:
ipc/sem.c:805: warning: ‘setbuf.uid’ may be used uninitialized in this function
ipc/sem.c:805: warning: ‘setbuf.gid’ may be used uninitialized in this function
ipc/sem.c:805: warning: ‘setbuf.mode’ may be used uninitialized in this function
  CC      ipc/shm.o
  CC      ipc/mqueue.o
ipc/mqueue.c: In function ‘sys_mq_notify’:
ipc/mqueue.c:1020: error: too few arguments to function ‘netlink_attachskb’
make[2]: *** [ipc/mqueue.o] Error 1
make[1]: *** [ipc] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.2'
make: *** [stamp-build] Error 2

```

Thanks again for taking the time to look at this and I look forward to any feedback you may provide.

Regards,
Jeff

Try removing the support for "netlink_attachskb" (you should find it in the network device section)

---

### Post by Toufik on 2006-07-17
```
DEVLIST drivers/usb/net/zd1211/zddevlist.h
make[5]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[4]: *** [drivers/usb/net/zd1211] Error 2
make[3]: *** [drivers/usb/net] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
```

I answer to myself.  Refeering to [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33085]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33085")
You just have to write
```
sudo apt-get install gawk linux-kernel-devel
```

By the way, there is no need to install *libqt3-mt-dev*, it is only usefull for "make xconfig" and this how-to uses "make menuconfig"

Thanks for this how-to, I've got my first personnal kernel :D

---

### Post by tseliot on 2006-07-17
> **Toufik said:**
> ```
DEVLIST drivers/usb/net/zd1211/zddevlist.h
make[5]: *** [drivers/usb/net/zd1211/zddevlist.h] Error 1
make[4]: *** [drivers/usb/net/zd1211] Error 2
make[3]: *** [drivers/usb/net] Error 2
make[2]: *** [drivers/usb] Error 2
make[1]: *** [drivers] Error 2
```

I answer to myself.  Refeering to [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33085]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/33085")
You just have to write
```
sudo apt-get install gawk linux-kernel-devel
```

By the way, there is no need to install *libqt3-mt-dev*, it is only usefull for "make xconfig" and this how-to uses "make menuconfig"

Thanks for this how-to, I've got my first personnal kernel :D
Thanks for reporting.

I'll add it to the guide

---

### Post by mlind on 2006-07-17
Has anyone been able to compile nvidia kernel module using module-assistant for newer kernels ?

---

### Post by tseliot on 2006-07-17
> **mlind said:**
> Has anyone been able to compile nvidia kernel module using module-assistant for newer kernels ?

A quotation from my guide:

> b) if you are using kernel 2.6.14 or higher you have to type:

```
sudo cp /usr/src/name_of_your_source/arch/i386/Makefile.cpu /usr/src/kernel-headers-`uname -r`/arch/i386/
```


NOTE: you have to replace "name_of_your_source" with the name of your source, such as linux-2.6.16, etc.)

```
cd /usr/src/kernel-headers-`uname -r`/
```




```
sudo make prepare
```



```
sudo make prepare scripts
```

Then try module-assistant

---

### Post by mlind on 2006-07-17
> **tseliot said:**
> A quotation from my guide:



Then try module-assistant

Okay, thanks for that.

If anyone else is getting these messages on bootup
```

device-mapper: dm-linear: Device lookup failed
device-mapper: error adding target to table

```

Check out [http://evms.sourceforge.net/install/kernel.html#bdclaim](http://evms.sourceforge.net/install/kernel.html#bdclaim)

---

### Post by reckless2k2 on 2006-07-22
I had a blackout last night during the final "sudo make-kpkg" step of a kernel compilation. Do I have to start over from the beginning again? ](*,)

---

### Post by nismohasan on 2006-07-22
i used to run IDE drives and today i finally went and got myself a sata2 drive, i used my old kernel config file and that didnt let me boot up the kernel, i'm assuming because i removed something needed for the sata2 drive?

kernel craps out and mentions stuff about sata drives.. 

here is my kernel.config what have i disabled that is needed to sucesfully boot my kernel? (2.6.17 + beyond2.1 patch)

[http://members.westnet.com.au/husky87/kernelconfig.txt](http://members.westnet.com.au/husky87/kernelconfig.txt)

---

### Post by tseliot on 2006-07-22
> **reckless2k2 said:**
> I had a blackout last night during the final "sudo make-kpkg" step of a kernel compilation. Do I have to start over from the beginning again? ](*,)

Do a:
```
sudo make-kpkg clean
```

and then type the final "sudo make-kpkg" step of the kernel compilation

---

### Post by tseliot on 2006-07-22
> **nismohasan said:**
> i used to run IDE drives and today i finally went and got myself a sata2 drive, i used my old kernel config file and that didnt let me boot up the kernel, i'm assuming because i removed something needed for the sata2 drive?

kernel craps out and mentions stuff about sata drives.. 

here is my kernel.config what have i disabled that is needed to sucesfully boot my kernel? (2.6.17 + beyond2.1 patch)

[http://members.westnet.com.au/husky87/kernelconfig.txt](http://members.westnet.com.au/husky87/kernelconfig.txt)

I need to know the model of your SATA controller.

Post the output of this command:
```
lspci
```

---

### Post by nismohasan on 2006-07-23
> 
hasan@nismo-oobuntoo:~$ sudo lspci
pcilib: Cannot open /sys/bus/pci/devices
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
**0000:00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)**
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)


[http://members.westnet.com.au/husky87/beyondkernel.config.txt](http://members.westnet.com.au/husky87/beyondkernel.config.txt)

how'd i do this time? i removed alot of crap that i don't need, made sure the chipset stuff i needed was there but kernel still won't boot; it gets up to something about sata 1.5gbps and stops

---

### Post by tseliot on 2006-07-23
> **nismohasan said:**
> [http://members.westnet.com.au/husky87/beyondkernel.config.txt](http://members.westnet.com.au/husky87/beyondkernel.config.txt)

how'd i do this time? i removed alot of crap that i don't need, made sure the chipset stuff i needed was there but kernel still won't boot; it gets up to something about sata 1.5gbps and stops

Try to build this in the kernel (not as a module):
CONFIG_SCSI_SATA_VIA=m

---

### Post by nismohasan on 2006-07-23
i edited the config file in gedit to say CONFIG_SCSI_SATA_VIA=y

loaded up the config file in xconfig went to double check that it was ticked (it wasnt, still a module) tried to put a tick there but its either a module or not included.

what to do? lol

---

### Post by tseliot on 2006-07-23
> **nismohasan said:**
> i edited the config file in gedit to say CONFIG_SCSI_SATA_VIA=y

loaded up the config file in xconfig went to double check that it was ticked (it wasnt, still a module) tried to put a tick there but its either a module or not included.

what to do? lol

Post the output of this command:
```
lsmod
```

---

### Post by nismohasan on 2006-07-23
here you go

> hasan@nismo-oobuntoo:~$ lsmod
Module                  Size  Used by
ipt_limit               2944  8
iptable_mangle          3328  0
ipt_LOG                 7616  8
ipt_MASQUERADE          4160  0
ip_nat                 20972  1 ipt_MASQUERADE
ipt_TOS                 2880  0
ipt_REJECT              6592  1
ip_conntrack_irc        7280  0
ip_conntrack_ftp        8560  0
ipt_state               2304  6
ip_conntrack           54488  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntr ack_ftp,ipt_state
nfnetlink               7192  2 ip_nat,ip_conntrack
iptable_filter          3392  1
ip_tables              24000  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE, ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
via                    50720  1
drm                    78292  2 via
cpufreq_userspace       6816  0
cpufreq_stats           6912  0
freq_table              5152  1 cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
video                  16644  0
tc1100_wmi              7172  0
sony_acpi               5900  0
pcc_acpi               12736  0
hotkey                 11812  0
dev_acpi               11652  0
container               4928  0
button                  6992  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
ipv6                  287456  22
nls_cp437               6208  1
isofs                  39232  1
udf                    95876  0
af_packet              25224  2
dm_mod                 63640  1
md_mod                 76244  0
fuse                   41616  6
lp                     12612  0
psmouse                40132  0
serio_raw               8132  0
i2c_viapro              9364  0
i2c_core               23168  2 i2c_acpi_ec,i2c_viapro
parport_pc             38340  1
parport                39560  2 lp,parport_pc
via_rhine              25988  0
mii                     6528  1 via_rhine
pcspkr                  2564  0
via_agp                10560  1
agpgart                37072  2 drm,via_agp
shpchp                 49312  0
pci_hotplug            30916  1 shpchp
sg                     40352  0
evdev                  10432  1
tsdev                   8320  0
ext3                  148296  1
jbd                    65684  1 ext3
usbhid                 42912  0
ide_generic             1792  0
uhci_hcd               35472  0
ehci_hcd               36104  0
usbcore               138948  4 usbhid,uhci_hcd,ehci_hcd
ide_cd                 36228  1
cdrom                  41504  1 ide_cd
via82cxxx               9988  0 [permanent]
sd_mod                 20864  6
generic                 5444  0
sata_via               10628  10
libata                 84176  1 sata_via
scsi_mod              145736  3 sg,sd_mod,libata
thermal                14088  0
processor              26696  1 thermal
fan                     5124  0
capability              5256  0
commoncap               7616  1 capability
vesafb                  8924  1
fbcon                  44640  71
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit


---

### Post by tseliot on 2006-07-23
> **nismohasan said:**
> here you go

Another question: did your SATA controller worked with Ubuntu's standard kernel?

---

### Post by nismohasan on 2006-07-24
yes it does work with the standard kernel so there has to be an option in the kernel that ive missed:confused:

---

### Post by caesar424 on 2006-07-24
> **tseliot said:**
> Try removing the support for "netlink_attachskb" (you should find it in the network device section)

After buying another adapter to receive the belkin CD, I've obtained the windows Ralink RT73 driver file I needed to use ndiswrapper and I am happily using wireless (though it took a few hours to get straightened out). Luckily, my unlce needed the adapter and bought it from me :D.

However, I'm still curious and I'd like to get my own custom kernel compiled correctly for installing software and codecs without debian packages.

In response to your suggestion above, I googled God's green earth and couldn't find much information on the component that is giving me trouble. I could not locate "netlinks_attachkb" in the menuconfig for the kernel, under any network-related menu.

From what I gather, there are some bugs regarding sockets in the kernel I'm attempting to compile but have not the expertise to analyze or even figure out what my next step should be.

I'll keep toying around until I get it working. Any suggestions to prod me along are, as before, immensely appreciated.

Best regards,
Jeff

---

### Post by mlind on 2006-07-24
> **caesar424 said:**
> 
However, I'm still curious and I'd like to get my own custom kernel compiled correctly for installing software and codecs without debian packages.


You don't need a custom kernel for installing software that's not debian packaged, but I guess you know that. You'll also lose all Ubuntu specific fixes and tweaks when you opt-in for using custom kernel. On the other hand, you get less fat and bloated kernel (and probably more responsive for desktop usage).

> **caesar424 said:**
> 
From what I gather, there are some bugs regarding sockets in the kernel I'm attempting to compile but have not the expertise to analyze or even figure out what my next step should be.


Are you compiling 2.6.16 or 2.6.17 kernel ? I think this issue is fixed on 2.6.17. You can try patching 2.6.15 using [http://www.linuxhq.com/kernel/v2.6/15.7/ipc/mqueue.c](http://www.linuxhq.com/kernel/v2.6/15.7/ipc/mqueue.c), but I suggest to use newest kernel possible if you're going to build a custom kernel anyway.

---

### Post by caesar424 on 2006-07-25
> **mlind said:**
> You don't need a custom kernel for installing software that's not debian packaged, but I guess you know that. You'll also lose all Ubuntu specific fixes and tweaks when you opt-in for using custom kernel. On the other hand, you get less fat and bloated kernel (and probably more responsive for desktop usage).

Each time I attempt to compile the RT73 driver (ralink), for instance, I receive path not found errors during the make process. I receive only two lines of output from the make command, the second of which is [Error:2] and something about paths not found.

I've received path errors when installing VMWare player as well, but I believe these specifically apply to the headers. I do not know what is so weird about my ubuntu installation that no compilation works, but it has remained consistent through reinstalls of ubuntu on this machine.

I would prefer to keep the stock kernel but have found no advice on how to compile these two specific programs with the specific errors I received. I do not have those logs. Perhaps, if anyone wishes to send a PM to me we can discuss this one weekend where I have time to attempt these compilations again.

> 
Are you compiling 2.6.16 or 2.6.17 kernel ? I think this issue is fixed on 2.6.17. You can try patching 2.6.15 using [http://www.linuxhq.com/kernel/v2.6/15.7/ipc/mqueue.c](http://www.linuxhq.com/kernel/v2.6/15.7/ipc/mqueue.c), but I suggest to use newest kernel possible if you're going to build a custom kernel anyway.

I am attempting to compile 2.6.15 (from the sudo apt-get install linux-source command; currently running 2.6.15). I will attempt a patch  this weekend, if time permits. The whole compilation procedure (much less patching) has become overwhelming and a bit intimidating. We'll see! :-D

Thanks for your advice!!

---

### Post by mlind on 2006-07-25
> **caesar424 said:**
> Each time I attempt to compile the RT73 driver (ralink), for instance, I receive path not found errors during the make process. I receive only two lines of output from the make command, the second of which is [Error:2] and something about paths not found.

I've received path errors when installing VMWare player as well, but I believe these specifically apply to the headers. I do not know what is so weird about my ubuntu installation that no compilation works, but it has remained consistent through reinstalls of ubuntu on this machine.


Do you have a thread for this problem that I could view? It's usually (hopefully) just a missing build dependency. I don't think is the appropriate thread to post the full make ouput.

---

### Post by asfaltboy on 2006-07-26
Hmmph, I had the same "E: Couldn't find package linux-tree" all day now.

> **tseliot said:**
> Please post your /etc/apt/sources.list (copy and paste it here)

```
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb http://archive.ubuntu.com/ubuntu/ dapper-updates universe multiverse main restricted

deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free

```

Is there actually a linux-tree on dapper?

I've found some linux-source-2.6.15 while looking at things
related to source on synaptic package manager. As I'm a total noob
i'm probably doing something wrong but it looks big enough to
be good (100+ MB of download needed) :P .. i'll see how it works
out in a few minutes.

edit: no good. still no build directory where i want it... i'm actually doing this because i'm trying to build some OV51x drivers and to make i need a build directory.. any suggestions?

**edit#2:** Problem solved! it's 5:43am and i finally got it!
linux-tree really does not exist.. to get the build you must do
sudo apt-get install linux-headers-`uname -r`! It doesn't really relate to this thread but i hope some one finds it useful :)
[U]
thanks to [Beau Grantham](http://blog.thedarkmere.net/index.php?/archives/14-Ubuntu-ov51x-jpeg-guide.html)[/U]

---

### Post by tseliot on 2006-07-27
> **asfaltboy said:**
> **edit#2:** Problem solved! it's 5:43am and i finally got it!
linux-tree really does not exist.. to get the build you must do
sudo apt-get install linux-headers-`uname -r`! It doesn't really relate to this thread but i hope some one finds it useful :)

There's a reason if I wrote this at the beginning of the guide:
**[COLOR="Red"]DAPPER USERS, please follow this guide:[/COLOR]**
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

---

### Post by Darth Tux on 2006-07-27
Hi everyone,

Ok, i used the guide for dapper drake and compiled a new kernel just fine. I only have one problem. My graphics card is a Radeon 9200 that doesn't work with the newer drivers, so to install them i use this [guide]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26") and install the 8.24.8 drivers. (which give me acceleration) Usually that guide works perfectly but when I used it after I compiled my new driver I got this error : 


dh_testroot
rm -f configure-stamp     
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a                               rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions                                                       
rm -rf patch                                                               
dh_clean                                                                   
rm /usr/src/modules/fglrx/debian/control                                   
rm /usr/src/modules/fglrx/debian/dirs                                      
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \           
        cat /usr/src/modules/fglrx/debian/control.template >               
/usr/src/modules/fglrx/debian/control; \                                   
        i                                                                 
if [ -f /usr/src/modules/fglrx/debian/postinst ]; then \                   
         mv /usr/src/modules/fglrx/debian/postinst                          
/usr/src/modules/fglrx/debian/fglrx-kernel-2.6.17.7-bob.postinst; \        
        fi  
dh_testdir                                                                 
touch configure-stamp                                                      
dh_testdir                                                               /usr/bin/make -C /usr/src/kernel-headers-2.6.17.7-bob                      SUBDIRS=/usr/src/modules/fglrx modules                                     
make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.7-bob'         
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile:38:                
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile.cpu: No such       file or directory                                                          
make[1]: *** No rule to make target                                        
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile.cpu'.  Stop.      
make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.7-bob'          
make: *** [build] Error 2                                                  
^Y


Thanks for any help.
-darthtux

---

### Post by mlind on 2006-07-27
```

ake[1]: Entering directory `/usr/src/kernel-headers-2.6.17.7-bob'
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile:38:
**/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile.cpu**: No such file or directory
make[1]: *** No rule to make target
/usr/src/kernel-headers-2.6.17.7-bob/arch/i386/Makefile.cpu'. Stop.
make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.7-bob'
make: *** [build] Error 2 

```

You have copy Makefile.cpu from the actual kernel tree's arch/i386 directory to kernel-headers' arch/i386 directory. I dunno why it doesn't happen automatically.

---

### Post by Darth Tux on 2006-07-28
hey, thanks for the help. That worked and i had to copy over ssome more files too. but now i get this error:

 /usr/bin/make -C /usr/src/kernel-headers-2.6.17.7-bob                      
 SUBDIRS=/usr/src/modules/fglrx modules                                     
 make[1]: Entering directory `/usr/src/kernel-headers-2.6.17.7-bob'         
 gcc -m32 -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs                  
 -fno-strict-aliasing -fno-common -O2 -fomit-frame-pointer -pipe            
 -msoft-float -mpreferred-stack-boundary=2  -march=i686 -mtune=pentium4     
 -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default                 
 -Wdeclaration-after-statement -Wno-pointer-sign -D__KERNEL__ -Iinclude     
 -include include/linux/autoconf.h -m elf_i386  scripts/Makefile.lib.c      
 -o scripts/Makefile.lib                                                    
 cc1: error: missing argument to "-m"                                       
 make[2]: *** [scripts/Makefile.lib] Error 1                                
 make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      
 make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.7-bob'          
 make: *** [build] Error 2

From what i can tell it is a problem with the option "-m" in Makefile.lib. But How do I solve that? Sorry for so many questions a thanks for the help.
-darthtux

---

### Post by mlind on 2006-07-28
Nice error message.. I think you should clean the kernel tree and try repeating the step that caused that error. If you clean the whole kernel tree, no worries - you don't need to rebuild the kernel image, just some modules.


I'm not sure about what clean rule to invoke, maybe modules-clean.. or just simply; clean.

I had great success using module-assistant to compile kernel module for nvidia drivers, but don't know how it works for ati.

---

### Post by tinsami1 on 2006-07-28
> **tseliot said:**
> There's a reason if I wrote this at the beginning of the guide:
**[COLOR="Red"]DAPPER USERS, please follow this guide:[/COLOR]**
[http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)

Does linux-source contain the latest?  I tried the instructions, but it gave me a 2.6.15-7 source, whereas the kernel is already up to 2.6.15-26.  How do I get to the latest source?

---

### Post by tseliot on 2006-07-28
> **tinsami1 said:**
> Does linux-source contain the latest?  I tried the instructions, but it gave me a 2.6.15-7 source, whereas the kernel is already up to 2.6.15-26.  How do I get to the latest source?

```
sudo apt-get install linux-source-2.6.15
```

---

### Post by Darth Tux on 2006-07-28
i tried using module-assistant clean all. The command ran just fine but it didn't fix the problem. I still get the same error message. I appreciate the help, anymore ideas? Or does anyone know of any command I should be using?

---

### Post by Darth Tux on 2006-07-28
UPDATE: Tried using "sudo make-kpkg clean" in the kernel's directory and the kernel headers, but to no avail. It still failed.

---

### Post by tinsami1 on 2006-07-28
> **tseliot said:**
> ```
sudo apt-get install linux-source-2.6.15
```

Done that and I still get a kernel-image-2.6.15**[COLOR="Blue"].7[/COLOR]**-ubuntu1-custom_10.00.Custom_i386.deb package.

I did an ```
apt-get source linux-image-2.6.15-26-686
``` and got what appears to be an unpacked tarball under /var/cache/apt/archives.  Can I use this as is and just move it to /usr/src?

---

### Post by tinsami1 on 2006-07-29
> **tinsami1 said:**
> Done that and I still get a kernel-image-2.6.15**[COLOR="Blue"].7[/COLOR]**-ubuntu1-custom_10.00.Custom_i386.deb package.

I took a look at the Makefile and the EXTRAVERSION variable is set to [COLOR="DarkOrchid"]**.7-ubuntu1**[/COLOR].  So either the linux-source package is not yet updated or this is just an oversight on the part of the maintainer.  The version of linux-source-2.6.15 in Synaptic is the 2.6.15-26.45.

---

### Post by Darth Tux on 2006-07-30
```
 &#9474; In file included from include/linux/sched.h:20,                            &#9618;
 &#9474;                  from include/linux/module.h:10,                           &#9618;
 &#9474;                  from /usr/src/modules/fglrx/agp3.c:65:                    &#9618;
 &#9474; include/asm/semaphore.h: In function ‘down’:                               &#9618;
 &#9474; include/asm/semaphore.h:105: error: syntax error before ‘agp3’             &#9618;
 &#9474; include/asm/semaphore.h: In function ‘down_interruptible’:                 &#9618;
 &#9474; include/asm/semaphore.h:130: error: syntax error before ‘agp3’             &#9618;
 &#9474; include/asm/semaphore.h: In function ‘down_trylock’:                       &#9618;
 &#9474; include/asm/semaphore.h:155: error: syntax error before ‘agp3’             &#9618;
 &#9474; include/asm/semaphore.h: In function ‘up’:                                 &#9618;
 &#9474; include/asm/semaphore.h:179: error: syntax error before ‘agp3’             &#9618;
 &#9474; make[2]: *** [/usr/src/modules/fglrx/agp3.o] Error 1                       &#9618;
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      &#9618;
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.7-bob'          &#9618;
 &#9474; make: *** [build] Error 2
 &#9474;
```

Well, I got a little  farther  by experimenting, but now i hit this wonderful new error. I dont know C++ so how in the world am i going to fix a syntax error in this file. There has got to be an easier way than all this. I don't mind recompiling as long as anyone might know a way I can prevent all this stuff from happening next time around.   The howto i  used worked perfectly on kernel 2.6.15-23, so I am assuming that something was missing when I compiled 2.6.17.7. But  I have no idea what I could have left out that would cause all this.

---

### Post by mlind on 2006-07-30
> **Darth Tux said:**
> ```
 &#9474; In file included from include/linux/sched.h:20,                            
 &#9474;                  from include/linux/module.h:10,                           
 &#9474;                  from /usr/src/modules/fglrx/agp3.c:65:                    
 &#9474; include/asm/semaphore.h: In function ‘down’:                               
 &#9474; include/asm/semaphore.h:105: error: syntax error before ‘agp3’             
 &#9474; include/asm/semaphore.h: In function ‘down_interruptible’:                 
 &#9474; include/asm/semaphore.h:130: error: syntax error before ‘agp3’             
 &#9474; include/asm/semaphore.h: In function ‘down_trylock’:                       
 &#9474; include/asm/semaphore.h:155: error: syntax error before ‘agp3’             
 &#9474; include/asm/semaphore.h: In function ‘up’:                                 
 &#9474; include/asm/semaphore.h:179: error: syntax error before ‘agp3’             
 &#9474; make[2]: *** [/usr/src/modules/fglrx/agp3.o] Error 1                       
 &#9474; make[1]: *** [_module_/usr/src/modules/fglrx] Error 2                      
 &#9474; make[1]: Leaving directory `/usr/src/kernel-headers-2.6.17.7-bob'          
 &#9474; make: *** [build] Error 2
 &#9474;
```

Well, I got a little  farther  by experimenting, but now i hit this wonderful new error. I dont know C++ so how in the world am i going to fix a syntax error in this file. There has got to be an easier way than all this. I don't mind recompiling as long as anyone might know a way I can prevent all this stuff from happening next time around.   The howto i  used worked perfectly on kernel 2.6.15-23, so I am assuming that something was missing when I compiled 2.6.17.7. But  I have no idea what I could have left out that would cause all this.


Are you still using the guide which uses module assistant btw?
I think it's similar to nvidia driver install, create fglrx kernel module using module-assistant, then install drivers (userspace stuff) using .deb's (xorg-driver-fglrx_xx.xx and fglrx-control_xx.xx.deb).

Is that error happening when you're using module-assistant?

---

### Post by Darth Tux on 2006-07-30
> **mlind said:**
> Are you still using the guide which uses module assistant btw?
I think it's similar to nvidia driver install, create fglrx kernel module using module-assistant, then install drivers (userspace stuff) using .deb's (xorg-driver-fglrx_xx.xx and fglrx-control_xx.xx.deb).

Is that error happening when you're using module-assistant?

Yes, that is happenning while I am using module assistant to install and configure the fglrx kernel source.

---

### Post by mlind on 2006-07-31
> **Darth Tux said:**
> Yes, that is happenning while I am using module assistant to install and configure the fglrx kernel source.

Okay, here's the thing. I took a look at fglrx-kernel-source package contents and I doubt that this package could be ever built with module-assistant :(

Its contents are derieved from nvidia-kernel-source package, topmost changelog entry
```

 fglrx-kernel (3.14.6-0ubuntu1) hoary; urgency=low

  * First release; packaging derived from nvidia-kernel-source.

 -- Daniel Stone <daniel.stone@canonical.com>  Sat, 27 Nov 2004 12:52:32 +0000

```

Doesn't look too convincing. Then I found this
```

$ grep -R nvidia * | grep -v changelog:
copyright:Sat, 27 Nov 12:56:49 +0000.  It is heavily based on the nvidia-kernel packaging
dirs.template:lib/modules/#KVERS#/nvidia
make.sh:if [ -e nvidia-agp.o ]
make.sh:  rm -f nvidia-agp.o 2>&1 | tee -a $logfile
make.sh:SRC=${SOURCE_PREFIX}/nvidia-agp.c
make.sh:DST=nvidia-agp.o
make.sh:#ld="ld -r ${FGL_PUBLIC}_public.o agpgart_fe.o agpgart_be.o agp3.o i7505-agp.o nvidia-agp.o $core_lib -o ${MODULE}.o"
make.sh:ld="ld -r ${FGL_PUBLIC}_public.o agpgart_be.o agp3.o i7505-agp.o nvidia-agp.o $core_lib -o ${MODULE}${module_version}.o"
override.template:nvidia-kernel-#KVERS#: mknod-in-maintainer-script postinst:32
override.template:nvidia-kernel-#KVERS#: mknod-in-maintainer-script postinst:41
override.template:nvidia-kernel-#KVERS#: unstripped-binary-or-object ./lib/modules/#KVERS#/kernel/drivers/video/nvidia.o
postinst:# postinst script for nvidia-kernel
postinst:                       devfile="/dev/nvidia$i"
postinst:               devfile=/dev/nvidiactl

```

These look nvidia specific, not ati! What the f***? Looks like a major bug to me..

You should find another way to install ati drivers. I don't have ati gfx card myself, but I was able to build kernel module using debian's fglrx-kernel-src package - that's another story though (module built succesfully). If you want to continue about this subject, send me a private message, so this thread won't go more offtopic.

---

### Post by rold50 on 2006-08-09
I'm trying to install a driver for my pcmcia card.

in the readme it says to add a line in linux/drivers/media/video/Config.in

The Problem is I can't seem to find Config.in

I'm using Kubuntu. Is Config.in the same as KConfig?

Also, the readme says to add 

dep_tristate '  ImperX Video Capture Essentials PCMCIA support'
CONFIG_PCMCIA_IMPERX_VCE $CONFIG_VIDEO_DEV $CONFIG_PCMCIA

when I add these lines to KConfig and try to make it. I get errors saying it doesn't know what dep_tristate is.

---

### Post by tseliot on 2006-08-10
> **rold50 said:**
> I'm trying to install a driver for my pcmcia card.

in the readme it says to add a line in linux/drivers/media/video/Config.in

The Problem is I can't seem to find Config.in

I'm using Kubuntu. Is Config.in the same as KConfig?

Also, the readme says to add 

dep_tristate '  ImperX Video Capture Essentials PCMCIA support'
CONFIG_PCMCIA_IMPERX_VCE $CONFIG_VIDEO_DEV $CONFIG_PCMCIA

when I add these lines to KConfig and try to make it. I get errors saying it doesn't know what dep_tristate is.
Which kernel version does the readme refer to?

---

### Post by rold50 on 2006-08-10
It's refering to kernel version 2.4 something but I don't want to downgrade to 2.4..

actually I've realized that it's even impossible to downgrade the kernel to 2.4 with ubuntu (?) from reading the forums.

I have already fixed the Config.in to Kconfig conversion.

The Problem I have now is:

I have PCMCIA video grabber card.

The drivers written for it works for the 2.4 kernels.

I tried installing the drivers for the current kernel version but I get errors.

The problem lies in some of the function/member operator in the header files in 2.4 kernels is not in the latest kernel anymore.

For example in the pcmcia/ds.h There is a struct called dev_link_t, which had a member called release. In the current kernel, the release member has been omitted. 

Do you think it will work fine if I just grab the old ds.h from kernel 2.4 and then building the kernel from that?

---

### Post by gesho on 2006-08-14
I am using dapper and was thinking to try 2.6.17 for my laptops overheating, I get dismall C3/C4 state and mostly stay in C2.

two questions here:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557)
some reccomend here changing 
CONFIG_HZ_1000 TO 25O
where and how can this be done?

when I dpkg compiled binaries, will this update grub menue too? or menu.lst needs manual editing? 
will adept keep notifing and managing new updates as they are released? when booted from new kernel? when booted from old kernel?

---

### Post by ashrack on 2006-08-14
> **gesho said:**
> 
CONFIG_HZ_1000 TO 25O
where and how can this be done?
Unfortunetly am not in my LINUX box right now, but the setting is somewhere at the begining when U lunch 'make xconfig' or 'make menuconfig'
Will give U a more detailed advice once I get to my linux box.

> when I dpkg compiled binaries, will this update grub menue too? or menu.lst needs manual editing? 
It will auto update grub.
> will adept keep notifing and managing new updates as they are released? when booted from new kernel? when booted from old kernel?
I see your a KDE junkie;) 
Yes, adept will still be notifiying U about new updates.

---

### Post by gesho on 2006-08-14
**ashrack **
> Unfortunetly am not in my LINUX box right now, but the setting is somewhere at the begining when U lunch 'make xconfig' or 'make menuconfig'
Will give U a more detailed advice once I get to my linux box.
thank you, that would be helpful.

> It will auto update grub.
I see your a KDE junkie 
Yes, adept will still be notifiying U about new updates.

right, all clear.

---

### Post by tseliot on 2006-08-14
> **rold50 said:**
> It's refering to kernel version 2.4 something but I don't want to downgrade to 2.4..

actually I've realized that it's even impossible to downgrade the kernel to 2.4 with ubuntu (?) from reading the forums.

I have already fixed the Config.in to Kconfig conversion.

The Problem I have now is:

I have PCMCIA video grabber card.

The drivers written for it works for the 2.4 kernels.

I tried installing the drivers for the current kernel version but I get errors.

The problem lies in some of the function/member operator in the header files in 2.4 kernels is not in the latest kernel anymore.

For example in the pcmcia/ds.h There is a struct called dev_link_t, which had a member called release. In the current kernel, the release member has been omitted. 

Do you think it will work fine if I just grab the old ds.h from kernel 2.4 and then building the kernel from that?
AFAIK porting the drivers from a kernel version to another should be a big amount of work (which btw only kernel hackers could do).

I have no idea of how to help you. Maybe you could contact via email the author of the driver and ask him whether a he released a version of the driver which compiles on modern kernels.

---

### Post by tseliot on 2006-08-14
> **gesho said:**
> some reccomend here changing 
CONFIG_HZ_1000 TO 25O
where and how can this be done?

cd /usr/src/linux (or the path to your kernel source)

sudo make menuconfig

get to "Processor type and features"

and look for "Timer frequency"

There you can set it to 250

---

### Post by robins_web on 2006-08-14
Help! I've tried the instructions twice and get the same reults both times:

robin@deathstar-toshiba:~$ sudo apt-get install linux-tree
Reading package lists... Done
Building dependency tree... Done
**E: Couldn't find package linux-tree**
robin@deathstar-toshiba:~$  

Here's my sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository. ## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
#deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
#deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Also, there's nothing in /usr/src

---

### Post by gesho on 2006-08-14
**robins_web **
while I am no expert trying this 1st time now, looks like you're following old instructions. 
For Dapper there is new link in the very 1st post of the thread,
no more
sudo apt-get install linux-tree
there

---

### Post by gesho on 2006-08-14
> **tseliot said:**
> cd /usr/src/linux (or the path to your kernel source)

sudo make menuconfig

get to "Processor type and features"

and look for "Timer frequency"

There you can set it to 250

thanks, I'll try that

---

### Post by robins_web on 2006-08-14
*while I am no expert trying this 1st time now, looks like you're following old instructions.* 

Oh, duh!  Thanks.

---

### Post by gesho on 2006-08-14
I compiled 2.6.17.8 from kernel.org according to present instruction and all went smooth.

system booted without hassle (grub needed little editing).

I forgot to compile modules with kernel and added them separate later, ndiswrapper and fuse.

fuse was fine, but 
dpkg ndiswrapper*.deb
was giving me error: present ndiswrapper requieres 
ndiswrapper-utils >=1.8-1
while the one is repository was 1.8-0ubuntu2, older version apparently.

anyway, my high C-states were not resolved by this, so won't be using that kernel anyway.

but the guide by tseliot is good.

---

### Post by ravpaul on 2006-09-03
Hi guys,

Am trying to compile via the patch on kernel.org and when doing the following:

sudo tar --bzip2 -xvf patch-2.6.17.11.bz2 /usr/src

get the following error:

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

I have been trying to compile the kernel for approx 3months via the instructions posted here and on [http://www.ubuntuforums.org/showthread.php?t=157560&highlight=firewall](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=firewall)

but keep failing so I thought I would try the kernel patch from kernel.org instead but still failing!!! ](*,) 

Please help.

---

### Post by xXx 0wn3d xXx on 2006-09-03
> **ravpaul said:**
> Hi guys,

Am trying to compile via the patch on kernel.org and when doing the following:

**sudo tar -xvjf patch-2.6.17.11.bz2 /usr/src**

get the following error:

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

I have been trying to compile the kernel for approx 3months via the instructions posted here and on [http://www.ubuntuforums.org/showthread.php?t=157560&highlight=firewall](http://www.ubuntuforums.org/showthread.php?t=157560&highlight=firewall)

but keep failing so I thought I would try the kernel patch from kernel.org instead but still failing!!! ](*,) 

Please help.
That should work...

and if not...

sudo mv kernel.2.5.6.whatever /location/directory
cd /location/directory
sudo tar -xvjf patch-2.6.17.11.bz2

---

### Post by 5-HT on 2007-04-27
Edit: Please Ignore. I determined the problem was something caused by something else entirely and reposted in the appropriate forum.

---

