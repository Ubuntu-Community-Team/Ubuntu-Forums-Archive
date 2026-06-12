---
title: "A few questions about Ubuntu"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by lolful64 on 2013-01-09
[I have ubuntu 12.10]

I have a few questions and I need simple to the point answers (ubuntu is already driving me mad and I've only started using it 7 minutes ago). Im a human being, not a NASA computer programmer. I need simple language because I know as much as ubuntu as a baby knows about computer codes.

By the way im pretty sure these are extremely common questions but the answers are written in the language of the computers, not English

How do I run .exe files (for both game related files and installer files)

How do I access my other *non external* partitioned hard drive? (ubuntu is on my D: drive and windows vista (which has failed me, again) is on C: drive. I want to copy the files off C: and put it into my ubuntu desktop)

How do I increase the size of my "ubuntu allocated memory"? I've just realised that I allocated too little space

----------------------------------------------------------------------------------------------------------------------------------
Windows vista "cannot repair this computer automatically, contact a system administrator" (which I am, unfortunately for me). Lucky I installed ubuntu some weeks ago :) <--(I think...). (although until now I haven't used it at all)
----------------------------------------------------------------------------------------------------------------------------------

---

### Post by Paqman on 2013-01-09
First of all: welcome to the forum! Now let's look at your problems:

> **lolful64 said:**
> 

How do I run .exe files (for both game related files and installer files)


You don't. 

Those .exe files are Windows software. You need to find a Linux alternative to your old Windows programs. Open up Ubuntu Software Centre and search for what you want, or check on [http://www.osalt.com/](http://www.osalt.com/) to get some ideas of Linux alternatives to Windows stuff.

There is a system called Wine that can allow some Windows software to sort of run on Linux, but a native Linux app will always be better than using Wine.

> 
How do I access my other *non external* partitioned hard drive? (ubuntu is on my D: drive and windows vista (which has failed me, again) is on C: drive. I want to copy the files off C: and put it into my ubuntu desktop)

Click on the folder icon in the launcher on the left and look in the left hand pane. Your old C drive should be listed in there, click on it to dig down into it.

> 
How do I increase the size of my "ubuntu allocated memory"? I've just realised that I allocated too little space


Did you install using Wubi (ie: you ran the installer while in Windows)? Or did you burn a CD, boot from it, and do a full install? The way to tackle the problem will depend on how your installed.

---

### Post by d.atanasov on 2013-01-09
Hi, and welcome to Ubuntu Forums.

Good for you to have Ubuntu installed, but you have to learn a bit to use any operating system. In Linux (this case Ubuntu) a files like .exe are not executable files. There is a whole story which you have to learn to execute files. But if you want to use exe files there are options in Ubuntu called "wine" or you just simple use "VirtualBox", where you put Windows :) I hope this can help you with the fist questions.

---

### Post by Impavidus on 2013-01-09
> **lolful64 said:**
> [I have ubuntu 12.10]

I have a few questions and I need simple to the point answers (ubuntu is already driving me mad and I've only started using it 7 minutes ago). Im a human being, not a NASA computer programmer. I need simple language because I know as much as ubuntu as a baby knows about computer codes.Well, 7 minutes is quite fast to turn mad.
> **lolful64 said:**
> 
How do I run .exe files (for both game related files and installer files)
In principle, you can't. .exe is the format for windows executables, which don't run on linux. However, there a workaround that may or may not work. You can install **wine**, which may be able to run your .exe files. But don't put your money on it...
> **lolful64 said:**
> 
How do I access my other *non external* partitioned hard drive? (ubuntu is on my D: drive and windows vista (which has failed me, again) is on C: drive. I want to copy the files off C: and put it into my ubuntu desktop)Ubuntu doesn't use those drive letters. Your other "drive" (windows calls both separate disks and partitions on disks drives, ubuntu uses separate terms) can probably be fould as an "x GB file system" in your file manager. You can click it to mount and then brows it. If this is a wubi install, you can find your windows files in /host.
> **lolful64 said:**
> 
How do I increase the size of my "ubuntu allocated memory"? I've just realised that I allocated too little spaceYou can use gparted from an Ubuntu Live dvd, at least, if this is a regular dual boot.
> **lolful64 said:**
> 
----------------------------------------------------------------------------------------------------------------------------------
Windows vista "cannot repair this computer automatically, contact a system administrator" (which I am, unfortunately for me). Lucky I installed ubuntu some weeks ago :) <--(I think...). (although until now I haven't used it at all)
----------------------------------------------------------------------------------------------------------------------------------
Sorry, I've never used windows vista. I guess installing Ubuntu somehow damaged the windows file system.

---

### Post by NikTh on 2013-01-09
If Windows Vista failed you **again** as you said , I suggest to throw out this OS and install Ubuntu to whole drive. 
Ubuntu is the easiest and most user friendly Linux system. (Linux mint too). 
If you have an external HDD , boot from an Ubuntu Live Media (such as CD/DVD/USB) copy all your important data to external HDD (photos , music , movies ... etc) and install Ubuntu to whole drive. 
Thousands of tutorials , how to .. etc exists in Web about Ubuntu. 
A good place to start is here : [https://help.ubuntu.com/community](https://help.ubuntu.com/community) and also this Forum. 
I usually suggest Ubuntu 12.04.1 LTS (because of Long Support and stability) which can be found here: [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) (32bit suggested for old computers - 5-6 years old and older , otherwise 64bit considered as faster). 

Thanks

---

### Post by lolful64 on 2013-01-09
> Originally Posted by **Impavidus**
Ubuntu doesn't use those drive letters. Your other "drive" (windows calls both separate disks and partitions on disks drives, ubuntu uses separate terms) can probably be fould as an "x GB file system" in your file manager. You can click it to mount and then brows it. If this is a wubi install, you can find your windows files in /host.

Took me A LONG WHILE of digging internally but I finally found what I was looking for. THANKS DUDE :) :) :) :) I didn't lose all that por.... never mind....

> Originally posted by **Paqman**
Did you install using Wubi (ie: you ran the installer while in Windows)? Or did you burn a CD, boot from it, and do a full install? The way to tackle the problem will depend on how your installed.

I did it from windows (Wubi installer is what I was told to download, so I did and ran the installer), now what?

---

### Post by Paqman on 2013-01-09
> **lolful64 said:**
> 
I did it from windows (Wubi installer is what I was told to download, so I did and ran the installer), now what?

One of the limitations of Wubi is that the maximum install size is only 30GB. So if you reinstalled you could choose up to that much. If you want more you would have to download the ISO, burn it to a disk or USB stick and boot up, doing a full install this time instead of using Wubi.

There are some techy ways to transfer an existing Wubi install to a normal partition, but I've not used any of them, they're complicated and since you've only just installed and haven't done too much to your system yet it would be far easier to just reinstall.

---

### Post by lolful64 on 2013-01-09
> **Paqman said:**
> One of the limitations of Wubi is that the maximum install size is only 30GB. So if you reinstalled you could choose up to that much. If you want more you would have to download the ISO, burn it to a disk or USB stick and boot up, doing a full install this time instead of using Wubi.

OK, I'll try

---

### Post by superDave972 on 2013-01-09
Just a quick tidbit that I wish I knew earlier on in my Ubuntu adventure:

When installing stuff, the Ubuntu equivalent of a .msi file is a .deb

But I prefer to use the Software Center or the terminal to install my packages.

---

### Post by Transhumanist on 2013-01-09
> **lolful64 said:**
> OK, I'll try

So the way to install Ubuntu normally is:

1) Download .ISO file on the website: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

2) Burn .ISO file to a USB stick (or DVD if you really must):
In Windows: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
In Wubi/Ubuntu: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

3) At BIOS, select "boot from USB": Usually by pressing one of the function keys as soon as the computer boots. E.g. F2, F8, F12, just observe what key is mentioned for BIOS as the computer is booting, or try keys and keep restarting to BIOS till some key works. 'Esc' key might even work.

4) Follow the simple GUI of the Live CD installer: the installer is pretty well-designed - the only confusing part might be the bit about choosing a partition to install to. I recommend reading the Wikipedia entry on partitions: [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

I would recommend saving your important stuff in Wubi, then uninstalling Wubi BEFORE you follow steps 3) and 4) of this procedure. That way when you re-size your Windows disk to make room for Wubi, you've got more space to work with. Otherwise if you're sick of Windows (like me), you can just completely format your Windows hard-drive with Ubuntu instead and not worry too much about partitions and dual-boot.

It seems daunting at first, but there's not too much to it you soon realise.

EDIT: After all that has happened, in your new Ubuntu install, you can go to the Software Centre and type in the search box 'Virtual Box'. Install this app. Now run it (go to the Unity launcher and start typing its name, then click on the icon when it shows up). Then add a new virtual machine, which basically involves installing Windows to a virtual disk (a file) on your hard drive. Windows will run this way as any other app would in Ubunuty - e.g. like your web browser Firefox. You can now run Windows apps flawlessly under Ubuntu (as long as they don't require any significant level of 3D acceleration - virtual Windows should be for mainly 2D stuff like running Maple symbolic algebra software). The cool thing about this is you can start and stop the virtual machine whenever, and when you do so you can either 'shutdown' the virtual machine as you would a normal Windows box, or simply save the machine state, which means clicking 'X', and then Virtual Box spends a few seconds saving the Windows OS to disk, so that when you start it again, you immediately start from where you left off - e.g. in Maple doing some matrix manipulations.

Note this requires a Windows install CD or a Windows .ISO (from where I will leave up to you to figure out).

---

### Post by mlentink on 2013-01-09
> **superDave972 said:**
> The Ubuntu equivalent of a .exe file is a .deb

No it isn't.
There simply is no exact equivalent to a '.exe' in ubuntu. Any file with its executable-bit set to yes is, in principle, executable. You can set text files to eecutable if you want, and if they contain valid commands, they will run too. 
A '.deb' is an installer, comparable to a windows .msi (or 'mis'? Can't remember exactly, haven't installed windows stuff in quite some time), and therefore a very special form of executable.

---

### Post by superDave972 on 2013-01-09
> **mlentink said:**
> No it isn't.
There simply is no exact equivalent to a '.exe' in ubuntu. Any file with its executable-bit set to yes is, in principle, executable. You can set text files to eecutable if you want, and if they contain valid commands, they will run too. 
A '.deb' is an installer, comparable to a windows .msi (or 'mis'? Can't remember exactly, haven't installed windows stuff in quite some time), and therefore a very special form of executable.

My bad. Duh. I had a brainfart. Not enough coffee I guess. Thanks!

---

### Post by blackbird34 on 2013-01-09
This site: [http://alternativeto.net/](http://alternativeto.net/) will explain what Linux alternatives exist for any windows programs you wanted.

---

### Post by AM Ramakrishnan on 2013-01-23
> **Paqman said:**
> 
There is a system called Wine that can allow some Windows software to sort of run on Linux, but a native Linux app will always be better than using Wine.

I would like to respectfull disagree. WINE directly translates windows commands into linux commands, so the delay is significantly less than an emulator. I have found that some third-party software like steam can cause issues when running other programs, but hey, nothings perfect.;)

---

