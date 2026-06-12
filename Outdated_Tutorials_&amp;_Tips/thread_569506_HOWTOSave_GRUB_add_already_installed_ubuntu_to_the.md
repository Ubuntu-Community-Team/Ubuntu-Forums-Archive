---
title: "HOWTO:Save GRUB add already installed ubuntu to the vista bootloader"
date: 2007-10-07
forum: Outdated Tutorials &amp; Tips
---

### Post by BigDaddy-CF- on 2007-10-07
I made this for someone else having trouble but hoping that it will help someone else from having to go through the trial and error I did I have added it here to make it more accessible.
Anyway here's how I got my Ubuntu installation to show up in Vista's New Boot Loader(why make it so much harder MS?)
first things first from within Ubuntu type the following into a console to see the available partitions, pay special attention to whether or not your boot device is listed as /dev/hda or /dev/sda's mine are SDA's
```
sudo fdisk -l
```
Ok now type the following to see your mount points```

sudo df
```
Type the following within Ubuntu console to back up your GRUB boot manager, you need to take note of which drive has your linux installation on it, it's usually going to be either HDA or SDA though so if yours is /dev/hda/ or /dev/sda you need to put what is appropriate for you in the code below and also substitute the path of a writable partition which is also accessible for Vista for /media/SHARE/ if you need to
```
sudo dd if=/dev/sda of=/media/SHARE/ubuntu.bin bs=512 count=1
```
check the backup  by typing the following in the console
```
hexdump -C /media/SHARE/ubuntu.bin
```
search for some GRUB&#8217;s references. If it is blank (zeros) or has NTFS strings in it, you probably should 
check the if&#8217;s hda/sda parameters.
Thank Ilya Hevnikov's [Triple Boot XP,Vista, Ubuntu guide]("http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/") for the above
Hope you saved that grub backup to somewhere that's accessible from vista!
Now you need to basically create an entry in Vista's boot loader program that points to your backup GRUB .bin file
Now editing the boot menu in vista is WAY more complicated than it used to be in XP
here's all the help you should need if my text below doesn't guide you enough [1]("http://technet2.microsoft.com/WindowsVista/en/library/85cd5efe-c349-427c-b035-c2719d4af7781033.mspx?mfr=true"), [2]("http://technet2.microsoft.com/WindowsVista/f/?en/library/08d64d13-4f45-4a05-bd86-c99211a93dd91033.mspx"), [3]("http://vistafaqs.com/viewfaq.aspx?faq=73"), and [4]("http://www.x64bit.net/site/board/lofiversion/index.php?t1209.html")

Now In vista create a shortcut to command prompt and set it to run as administrator by right clicking the shortcut->properties->shortcut tab->advanced button->tick the "run as administrator" tick box->hit ok button->hit apply button->hit ok button and run command prompt. Vista will ask if it's ok to continue or not tell it to continue, my command prompt starts off in C:\Windows\System32> I hope yours does too. If a program is exhibitiing weird behavior and or not working in Vista you can use this trick of substituting a shortcut to run it as an administrator. This has fixed a number of issues for me in Vista especially on programs that run as a startup. Now type bcdedit /? and it will show you a list of the command parameters you can use. I type bcdedit /enum to enumerate the current listings for the vista boot editor
At that point in time it only listed one boot manager and one boot loader, since I had moved my GRUB backup which I had named Ubuntu.bin to C:\windows\.
Its important to make a backup at this point so that if you screw up you can fix it.
```
bcdedit /export "D:\bcdbackup\BcdBackup"
```
will backup your boot config, this folder must be created if it doesn't already exist prior to the backup operation
```
bcdedit /import "D:\bcdbackup\BcdBackup"
```
will import that backup to fix whatever you did if you have problems

now keep in mind that I don't triple boot but just dual boot Vista/Gutsy because windows is required for some of my school work. As such just point to my Linux grub backup ubuntu.bin as the legacy os entry. I will redo my entry to not only reflect my newer version of Ubuntu(feisty to gutsy) but also so that I can guide you through the process. So you'll be able to skip this first portion about deleting an entry but hop back in when I get to creating your new entry
so I type bcdedit /enum to get a listing of what's in my boot manager store and I get something like this
```
Windows Boot Manager
----------------------------
identifier                             {bootmgr}
device                                 partition=C:
description                            Windows Boot Manager
locale                                 en-US
inherit                                {globalsettings}
default                                {current}
resumeobject                           {3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}
displayorder                           {current}
                                       {ntldr}
toolisdisplayorder                     {memdiag}
timeout                                {30}

Windows Boot Loader
--------------------------
identifier                             {current}
device                                 partition=C:
path                                   \Windows\system32\winload.exe
description                            Microsoft Windows Vista
locale                                 en-US
inherit                                {bootloadersettings}
osdevice                               partition=C:
systemroot                             \Windows
resumeobject                           {3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}
nx                                     OptIn

Windows Legacy OS Loader
---------------------------------
identifier                             {ntldr}
device                                 partion=C:
path                                   \Windows\ubuntu.bin
description                            Ubuntu 7.04 [Feisty Fawn]
```

now to delete my now incorrect boot listing I type the following because my linux entry is listed as my legacy OS loader
```
bcdedit -delete {legacy} -f
```
I could have also typed
```
bcdedit -delete {ntldr} -f
```
now when I type bdedit /enum the legacy OS loader entry is gone so time to put a new one in it's place, I've already backed up a new gutsy GRUB backup and copied it over my Feisty GRUB backup so here goes nothing
```
bcdedit /create {legacy} /d "Ubuntu 7.10 [Gutsy Gibbon]"
```
or you could type
```
bcdedit /create {ntldr} /d "Ubuntu 7.10 [Gutsy Gibbon]"
```
Both ways show up as Windows Legacy OS Loaders, the drawback being you can only have one legacy entry.
```
bcdedit /enum all
```
shows my new entry, now time to enter some configuration for my new entry
```
bcdedit /set {legacy} device partition=C:
bcdedit /set {legacy} path \Windows\ubuntu.bin
bcdedit /displayorder {legacy} {current}
```
That last line adds your entry to the actual boot sequence with Ubuntu first and vista second you can reverse that if you would like. On a side note grub makes this whole boot selection process a lot easier to if you installed Linux after vista this process becomes a lot easier, since you don't have to mess with Vista's new boot loader at all if you don't want to. The only way I know of currently to create a new GUID so that you can create what amounts to multiple legacy entries is to do the following.
```
bcdedit /copy {current} /d "copyofcurrent"
```
This will make a new entry with all the settings of the current entry(Vista) but with a new GUID, so you can now start to set its parameters to what you would want just like above only using this method you aren't limited to making 1 new entry.
```
bcdedit /set {NewlyCreatedGUIDhere} path \Windows\ubuntu.bin
bcdedit /set {NewlyCreatedGUIDhere} DESCRIPTION "Ubuntu 7.10 [Gutsy Gibbon]"
```
Notice that there's a reason I typed the last line of code the way I did

---

### Post by chick on 2008-10-16
> **BigDaddy-CF- said:**
> 
```
bcdedit /set {legacy} device partion=C:
```

That should be "partition" instead of "partion". Peace!

---

