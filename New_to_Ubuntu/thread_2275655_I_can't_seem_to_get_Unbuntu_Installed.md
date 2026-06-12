---
title: "I can't seem to get Unbuntu Installed"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by k9saint on 2015-04-27
Some im running windows 8.1 64bit and im wanting to try Ubuntu. I made a cd and a usb drive. Iv tried using both and nither will work like I want it too. I want it installed on my 120gb Samsung 840evo ssd that I also have my windows 8.1 on. I also have a 1tb wd hdd that I use for all my steam games//pics/movies ect. When I go to install it, it tells me there is no os found or it will only let me select the 1tb hdd and not to ssd. Here are my computer specs

Motherboard: Asus m5a97 R2.0
CPU: 6300 FX 3.5GHz/4.1GHz turbo
RAM: 8GB Corsair Vengeance 1600MHz
EVGA GeForce GTX 960 FTW Edition
EVGA 600w 600B Bronze PSU
Samsung 840 evo 120GB SSD
1TB WD HDD
Logitech g15 Keyboard with Logitech MX518 Mouse

---

### Post by yancek on 2015-04-27
A CD won't work because the iso is too large to fit on one.  Are you actually burning it to a DVD?  What software did you use to put the bootable image on the flash drive?  When you boot the Ubuntu installation medium to you see installation options such as install alongside and something else?  The something else option is basically a manual option and will give you control over what happens.  Have you ever installed Linux or any operating system before?  If you can boot the Ubuntu medium open a terminal and type the following command and post the output:  sudo fdisk -l(Lower case Letter L in the command) and post it here as a starting point.

Have you done any reading on UEFI/GPT which is what is used with windows 8?

---

### Post by k9saint on 2015-04-27
Yes I burnt it to a dvd-r Verbatim media. Universal pen drive was the program recommended by Ubuntu. The options seem to change each time I boot to install. Sometimes it will say along side windows but another time it will say no os installed. Or say boot along side windows but will only let me select the 1tb hdd. yes I get the option something else. yes I have installed may different Linux operating systems but none have ever caused a issues like this. yes I have read about UEFI/GPT. Not 100% sure on the UEFi/GPT. My bios show the same usb device twice. example: UEFI_usb_1992mb and usb_1992mb. Something along thos lines. When I select UEFI I get a black background screen with gurb at the top. If I select the other option it shows the white Ubuntu symbol in the background with options to select.

---

### Post by ajgreeny on 2015-04-27
Have a good read through all the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which may help you to figure out the UEFI/BIOS uncertainty you have at the moment, though I am prepared to bet that the machine uses UEFI.
If your Win8 is installed in UEFI mode, which is the default on just about all new machines, you must also install Ubuntu 64bit in UEFI mode as well. There is no way that I'm aware of that you can change the installed version of Win8 from UEFI to MBR/legacy BIOS

Ubuntu 32 bit will not work, or is very difficult to get to work, in UEFI as far as I'm aware, so why bother trying.

    GPT Advantages (older but still valid) see post#2 by srs5694:
    [http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
    [https://wiki.archlinux.org/index.php...antages_of_GPT](https://wiki.archlinux.org/index.php...antages_of_GPT)
    UEFI Advantages
    [http://askubuntu.com/questions/44696...y-vs-uefi-help](http://askubuntu.com/questions/44696...y-vs-uefi-help)


    Microsoft suggested partitions including reserved partition for gpt & UEFI:
    [http://technet.microsoft.com/en-us/l...8WS.10%29.aspx](http://technet.microsoft.com/en-us/l...8WS.10%29.aspx)
    Order on drive is important: msftres
    [http://en.wikipedia.org/wiki/Microso...rved_Partition](http://en.wikipedia.org/wiki/Microso...rved_Partition)


    Convert Windows BIOS to UEFI - Also command line install of files to efi partition uses rufus
    [http://www.eightforums.com/tutorials...e-windows.html](http://www.eightforums.com/tutorials...e-windows.html)
    [http://social.technet.microsoft.com/...n-to-uefi.aspx](http://social.technet.microsoft.com/...n-to-uefi.aspx) 

    For info on UEFI boot install & repair - Updated Mar 2015:
    [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

    Lots of detail, screenshots and essential info.14.04 Something Else example
    [http://www.dedoimedo.com/computers/u...all-guide.html](http://www.dedoimedo.com/computers/u...all-guide.html)
    [http://askubuntu.com/questions/34326...g-installation](http://askubuntu.com/questions/34326...g-installation)
    [http://askubuntu.com/questions/16396...-windows-using](http://askubuntu.com/questions/16396...-windows-using)


HP and some others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds.
Thanks to oldfred for this info.

UEFI still lets you boot devices and the /efi/Boot folder has bootx64.efi which is the hard drive boot entry. If you rename that and make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.

script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix).

---

### Post by k9saint on 2015-04-27
Yeah I downloaded the 32bit that I installed on my laptop. And I downloaded the 64bit for my desktop. Installed no problems on my tosiba laptop. Tho I deleted windows before I installed it so its alone. But my mobo is a windows 8.1 ready mobo with UEFI bios. Looks like more of a hassle to get it installed then anything. Total bummer

---

### Post by Mike_Walsh on 2015-04-27
Hi, k9saint.

This is perhaps a dozy suggestion, as I don't have a lot of experience in this field, but:

Have you researched (via Google, or whatever your preference is) to see whether there are any non UEFI BIOS's available for your mobo? Of course, that would limit you to only using Ubuntu, as there isn't (as far as I'm aware) any method for getting Windows 8.1 to boot from an MBR-type BIOS...

I could of course be completely wrong in this assumption. Just an idea.


Regards,

Mike.

---

### Post by k9saint on 2015-04-27
So i got it installed and running. Im acually using it as im typing this. I only have one problem and thats my screen resolution. It running in 1024x768 but my moniters native resolution is 1280x1024. I have a gtx 960 ftw edition. How do i fix this?

Edit: So i heard that if your using ssd to not creat a swap? Is this true? cuz i did. and if so can i delete it?
Edit: What about trim?

---

### Post by yancek on 2015-04-27
Have you tried going into System Settings and selecting the Display option?

Whether you need or use swap depends upon how much RAM you have.  I have 4GB and don't remember every using swap, it depends also on what you use the computer to do.

---

### Post by k9saint on 2015-04-27
Yup tried system settings. 

I have 8gb of ram. Using Ubuntu just for browsing. If I game I'll boot into widows 8.1

---

### Post by sandyd on 2015-04-27
There are now generally three reasons you want to use swap

[LIST]
[*]Hibernation (Swap partition must be same size as RAM)
[*]Low RAM on computer in the first place (I would say below 4G, depending on what your running)
[*]Don't want computer to crash when your RAM usage reaches 100% due to memory leaks/etc. This will give you time to shut down your computer or stop the process
[/LIST]

Side note: Using a swap partition, or paging file on a SSD is known to reduce SSD life

Edit #1:
8GB RAM is enough, unless you have one of the issues above.

---

### Post by k9saint on 2015-04-27
I don't use hibernation. So how do I delete the swap?

---

### Post by Geoffrey_Arndt on 2015-04-28
Re swap, you can use the program 'gparted' to see all your drives and their partitions including swap.   Once the partition is unmounted, you can edit it and remove, move, add partitions and other disk properties (like labels, etc.).

The custom install protocol is the one needed for install to SSD or other specific device & place on drives (aka "something else" option).

Re your monitor resolution - - did you (after install completed) - - install any proprietary video drivers (so you can get more than 1024 x 768)?

.......................................................................................................

---

### Post by sudodus on 2015-04-28
You should also remove a line or 'make it a comment' (put a # character in the beginning) in the file **/etc/fstab**, which tells the system to turn on swap and which swap partition (or file) to use.

Example: I have the following line ([COLOR=#ff0000]red[/COLOR]), and I show it commented away afterwards [COLOR=#0000ff](blue[/COLOR]).

```
# /dev/sda5 swap
[COLOR=#ff0000]UUID=03bed9e9-e39b-4107-8cd6-c2612af9a6aa none            swap    sw              0       0[/COLOR]

```
```
# /dev/sda5 swap
[COLOR=#0000ff]#UUID=03bed9e9-e39b-4107-8cd6-c2612af9a6aa none            swap    sw              0       0[/COLOR]
```

Start a terminal window. Edit the file** /etc/fstab** with superuser privileges for example with the editor ***nano*** with the command

```
sudo nano /etc/fstab
```

---

### Post by k9saint on 2015-04-28
So when I installed Ubuntu I selected something else. I used freespace from the ssd that I parted with windows 8.1 disk management. I did / for the root, swap(going to remove), and I did /home. did I have to do /home cuz Im seeing videos where they don't?

---

### Post by k9saint on 2015-04-28
And now that I installed the latest Nvidia drivers for my gtx960 I still can't select 1280x1024 resolution

---

### Post by sudodus on 2015-04-28
> **k9saint said:**
> So when I installed Ubuntu I selected something else. I used freespace from the ssd that I parted with windows 8.1 disk management. I did / for the root, swap(going to remove), and I did /home. did I have to do /home cuz Im seeing videos where they don't?

Some people prefer a separate /home partition, but the standard installation is to have /home as a directory in the root partition (/). I have a separate ***data*** partition instead of a separate /home partition, and I backup the data partition separately (without compression, because most big files are compressed already, picture files, multimedia files, iso files with squashfs and other compressed image files).

---

### Post by sudodus on 2015-04-28
> **k9saint said:**
> And now that I installed the latest Nvidia drivers for my gtx960 I still can't select 1280x1024 resolution

Maybe you have better luck with another nvidia driver.

---

### Post by dino99 on 2015-04-28
> **k9saint said:**
> And now that I installed the latest Nvidia drivers for my gtx960 I still can't select 1280x1024 resolution

install at least 346, but better to set 349 from xorg-edgers ppa
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

howto:
- after the ppa activation, update the repositories
- > sudo apt-get purge nvidia*
- install the 349 driver only  (either from synaptic or into a terminal > sudo apt-get install nvidia-349
- then deactivate that ppa and update the repo again (dont mess with other ppa package)

---

### Post by k9saint on 2015-04-28
I already installed 346

---

### Post by Geoffrey_Arndt on 2015-04-28
How about the nVidia console?   I have intentially avoided having nVidia or ATI graphics based systems for several years, but, as I recall, there should be video config options in the nVidia console dialog app (assuming it's still available . . )

---

### Post by k9saint on 2015-04-29
A non Nvidia/amd rig sounds bad to me. Can't run 4k res in a Intel chip that's for sure lol. My high dollar gpus are a must for gaming. Getting ready to ditch this Linux stuff all together. Now I remember why I quit messing around with it in the first place. Just getting a driver to work properly is like pulling teeth. I'll just wait for windows 10. Thanks for the help everyone but iv deleted the Linux partition. I work to much to mess around with it all day. Thanks

---

### Post by Geoffrey_Arndt on 2015-04-29
> **k9saint said:**
> A non Nvidia/amd rig sounds bad to me. Can't run 4k res in a Intel chip that's for sure lol. My high dollar gpus are a must for gaming. Getting ready to ditch this Linux stuff all together. Now I remember why I quit messing around with it in the first place. Just getting a driver to work properly is like pulling teeth. I'll just wait for windows 10. Thanks for the help everyone but iv deleted the Linux partition. I work to much to mess around with it all day. Thanks

Well OK . . . . different strokes for different folks.    If I ever get the urge to watch 4k video, do high-end gaming, I'll just just get this - _***Liquid cooled***_ gaming device:

[https://system76.com/desktops/leopard](https://system76.com/desktops/leopard)

And upgrade it with:

>  64 GB quad channel 2133MHz, GTX 980 w/2048 Cuda Cores (or maybe Titan Z), RAID w/T TB SSD Main & 512 GB PCI SSd (reads @ 1170Mbs/sec., write 930 Mbs/second)

:lolflag:

---

