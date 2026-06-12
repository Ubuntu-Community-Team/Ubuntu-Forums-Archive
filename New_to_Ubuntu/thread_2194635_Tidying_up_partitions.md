---
title: "Tidying up partitions"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by bedayaya on 2013-12-19
Hey there!

I've been using Ubuntu for roughly a year but I wouldn't call myself anything other than a beginner x)

In any case, the other day Ubuntu complained it was running out of memory! :o 
Which made little sense to me as I still had plenty of free space in disk. Then I remembered that when installing Ubuntu I had edited my partitions (a bit with help from an Inthernet guide) so I could dual boot Ubuntu and Windows 7.

Now I figure the work I first did might not have been the best and I could use with editing my partitions once more.

I went and grabbed Gparted only to realise I couldn't make much sense of what it was showing me:

[http://i.imgur.com/J3gZamV.jpg](http://i.imgur.com/J3gZamV.jpg)

From this mess I wanted to turn it into just three or so main partitions, one just for windows, one for ubuntu and one for files.

So can anyone help me with this ? :)

---

### Post by newb85 on 2013-12-19
1&2 are for Windows, you probably shouldn't mess with them.

3 looks like you may have created it to share data between the two systems.  (Or it was created by Windows for some reason.)

4 is basically a holder, and you need it to have more than 4 partitions.

8 is where your entire Ubuntu system (including your /home directory) is located.  It's probably where you need more space.

5 & 6 I don't know about.  They're ext4, which means you probably created them when you installed Ubuntu, but they don't have mount points, so I have no idea what they're for.  They're holding something.  I'm guessing they don't need to be that big, though.

---

### Post by grahammechanical on 2013-12-19
It is standard for Ubuntu to have at least a partition with a mount point of / and a swap partition. Please tell us what sda5 is being used for? That is the partition that is close to being full. Is it /boot? If so, then it might be better to make it at least 1GB and also to remove some of the old kernels that are taking up space. I am a bit surprised that sda5 is not being shown as a mount point of /boot.

Ubuntu seems to be on sda8 and with 15GB you should not be getting out of disk space messages. What is sda7 doing? Gparted does not recognise it. I would not alter your windows partitions. You might need that recovery partition one day.

Regards.

---

### Post by bedayaya on 2013-12-24
Thanks for the replies guys :)

Ok, so no touching the Windows partitions!

I went to browse a bit and this is the guide I used in making the partitions
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

On sda7, I'm not even sure if it's doing anything. I might have just made an empty partition that does nothing, I mean Gparted says [http://i.imgur.com/nAxdJM6.jpg](http://i.imgur.com/nAxdJM6.jpg)

I'm sorry if I'm not answering everything but I'm not even sure how I can check what each partition does :(

---

### Post by oldfred on 2013-12-24
May be best to see all the details. 
But gparted has message on your NTFS. Does it need chkdsk or is it hibernated. 
If you resolve that first, then we can see how much of that partition is used.

This is a bit of overkill as it shows everything. But easiest way to see what we need.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by cincibluer6 on 2013-12-24
Eh, my uninformed opinion says
5 should be left alone til you figure out what exactly it is. Is it mounted on startup? Mount it regardless and see what's residing in it (Ctrl +H in Files (nautilus) will show you the hidden files.)
Do you need that much swap? 1 or 2 gigs is usually way more than enough unless your rig only has like 1GB of RAM.
If not, shrink that down and extend it to one or another.

You can add the unallocated to whatever partition you want next to it (resize a partition that borders it.)
6 looks like your /home directory just judging by the space and amount used.
7 I would delete that (reformat) and add it to home. Just to clean it all up.

Hope that helps a little bit. If 5 is the one complaining for space, it's gonna be hard to help it as your root partition is next to it and trying to resize root to give more to 5 is just more than a little bit dangerous wrt your files.

---

### Post by bedayaya on 2013-12-29
I don't really know how much swap do I need, i just followed the guide that said 4 GB would be plenty.

The reports from the Boot-info

[http://paste.ubuntu.com/6657699/](http://paste.ubuntu.com/6657699/)

and Boot-repair

[http://paste.ubuntu.com/6657812](http://paste.ubuntu.com/6657812)


I tried adding the GParted from the sda2 but I couldn't.
Ok so 7 might be better to scrape and join with 6 and unallocated.
I tried changing a download directory to 6 actually since it's still got plenty of space but I couldn't. Could joining 8+6+unallocated+7 solve my problem?


Thanks again guys :)

---

### Post by oldfred on 2013-12-29
You show an old wubi install inside Windows. Are you using it? If not best to houseclean.
Speaking of housecleaning you have two installs and lots of kernels. Best to regularly houseclean old kernels.
One install in sda5, has grub installed to PBR or partition boot sector which you should not normally do. It does not show a fstab, does it boot?

And you have 13.04 in sda8.
It looks like each install had its own swap. You normally can share swaps unless you encrypt /home as then swap is also encrypted or want to hibernate. So you may be able to delete one swap. If you delete the one you use, then you have to change UUID in fstab to the one you keep.

       Check current kernel I also keep one older just in case:
            Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by bedayaya on 2013-12-30
The wubi should be from my first installs. I'm going to try and remove it then.
I had no idea I had "kernels" (or am really that enlightened by wikipedia on what a kernel is).
I understood nothing of your third sentence I'm sorry. I don't know what grub, PBR or fstab are. Ok from Google I get that grub has to do with the boot sequence window I get. I did set windows to let me choose which OS I boot, but I see 2 screens really. If I let it boot normally I see the OS options in the purple Ubuntu type screen (though I never told it to show me that it shows me that by default). SO I think my answer is a confused yes, I think it loads

I think Ubuntu on it's installation mentions something about encrypting and that might be what has them all split. I can see that sda9 and sda7 seem to be swap in the Boot-info Pastebin. sda7 was in an unknown status with Gparted.

uname -a gives:

Linux beda-K53U 3.8.0-34-generic #49-Ubuntu SMP Tue Nov 12 18:00:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

uname -r gives:

3.8.0-34-generic

But I'm getting more confused, this seems like needed maintenance  work but will this allow me to use the space in sda6 and stop with the no space problems?

I'm now going to try that kernel removing command you posted. Though why would I save 1 old one?

---

### Post by oldfred on 2013-12-30
Sometimes things break, so I like to have two kernels at all times, but then the much older one's are not required.
New versions of Ubuntu do not install synaptic, so if you want to use that, you will need to install it. You can do that with command line or Software Center. Ubuntu wants to replace synaptic with Software Center as then they can also sell things. Or command line.
sudo apt-get install synaptic

I do not always pay attention to the fact that posts are in Absolute Beginners as I usually look in new threads and do not notice.
Kernels are what operating system uses to boot. It is the fundamental part of Linux and is the operating system. 
Grub2 is the boot loader. Windows also has a boot loader but has no name. It is the code in the very first sector of a hard drive or MBR (if BIOS not new UEFI but that is another long discussion). BIOS loads from motherboard when you start system and it checks what hardware you have, then it passes to the MBR, but MBR is tiny, so that usually just finds more code somewhere on drive to continue boot process and load the operating system.

While discussion Vista and Windows, it shows the way systems work, grub is a bit different. You can just review pictures without reading all the detail if desired.
 Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

 More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)

---

### Post by bedayaya on 2014-01-31
Wow, I'm sorry I left this hanging so long ^ ^; 

Thanks for those links I'll look at them in a bit more detail later.

I'm not sure I was awfully clear with the grub thing so... when I turn on the computer it first goes to a purple screen where I can choose what to boot (if ubuntu if windows7 or some other options). If I choose Ubuntu, ubuntu loads, if I choose windows7 windows will take me to the black screen that shows me both options, that I turned on in the bios because I think for the first installation ubuntu wasn't the default, so to allow me access to the ubuntu OS in the first place.

Alright, I have cleaned up some kernels with Synaptic Package Manager  [http://imgur.com/a/8FYgd](http://imgur.com/a/8FYgd)

I kept one old kernel. And here are the BootRepair and BootInfo logs:

 [http://paste.ubuntu.com/6849039/](http://paste.ubuntu.com/6849039/)

[http://paste.ubuntu.com/6849042/](http://paste.ubuntu.com/6849042/)

 
But why do I still see all the not-installed and removed kernels?


And more important, now that I removed the kernels can I move on to rearranging the partitions?

Thanks again, you guys are awesome :D

---

### Post by oldfred on 2014-01-31
You still have wubi installed, so that is why Windows will boot and show another Ubuntu install. Wubi only works from inside Windows. If not using that version anymore you have to uninstall from inside Windows. The last supported version of wubi is 12.04 as it does not work with new UEFI systems.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)

You still show 7 3.5.xx versions of kernels.
And you have a lot of 3.2.xx versions. Those may not even show in synaptic if you upgraded in place. New install may not have old kernels still listed. Then you have to manually delete.

       Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example, change to your versions:
sudo apt-get purge linux-image-3.2.0-{41,43,44,45,48,49}-generic-pae

---

### Post by bedayaya on 2014-01-31
What is "ls vmlinuz*" for?

I can get the linux image versions to purge from the synaptic right?

Also, I couldn't do any purges i get

beda@beda-K53U:~$ cd /boot/
beda@beda-K53U:/boot$ ls vmlinuz*
vmlinuz-3.8.0-34-generic  vmlinuz-3.8.0-35-generic
beda@beda-K53U:/boot$ sudo apt-get purge linux-image-3.2.0-41-generic
[sudo] password for beda: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by oldfred on 2014-01-31
The ls command is just to list what files you may have, so you know what to delete or which one not to delete.

If you have a lock that is usually because you also have Software Center or synaptic still open. Or another terminal holding it open. Only one update process can run at a time.

Did you run this? These were your versions from BootInfo.
sudo apt-get purge linux-image-3.2.0-{41,43,44,45,48,49}-generic-pae

---

### Post by bedayaya on 2014-02-01
Ohhh yeah, I think I had synaptic still running on the side.


I'll try and remove those without synaptic on then

Also vmlinuz gives me 

beda@beda-K53U:/boot$ ls vmlinuz*
vmlinuz-3.8.0-34-generic  vmlinuz-3.8.0-35-generic

I'm imagining these ones are the files not to delete.
I'll try and remove the 3.2's without synaptic on then and see how it works :)

---

### Post by bedayaya on 2014-02-01
Ok, I tried purging without having synaptic on and I got this:

beda@beda-K53U:/boot$ sudo apt-get purge linux-image-3.2.0-43-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-3.2.0-43-generic-pae
E: Couldn't find any package by regex 'linux-image-3.2.0-43-generic-pae'

I'm not sure if that meant it was removed or that it tried and couldn't do it.

EDIT: I'm going to guess it didn't remove since this still shows the 3.2.0-43 [http://paste.ubuntu.com/6854866/](http://paste.ubuntu.com/6854866/)

---

### Post by oldfred on 2014-02-01
Then they were from previous install and not listed in current package manager.

You should then just delete. But you have to manually delete all the files with 3.2.0.43 which will be 4 or 5 files. And then each of all the other 3.2.xx files in same manner. Use up arrow key to get previous edit and change number.
You can use rm but be very careful with rm command as it can delete anything you tell it. 
May be easier to use , but again be very careful to only delete the files you want to delete.
gksudo nautilus

See details on deleting trash in users home that may be root & and root.
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by bedayaya on 2014-02-01
Wait, so the old kernels are no longer in boot but in trash? If so are they really still a problem?

---

### Post by oldfred on 2014-02-01
They are not in dpkg which manages current installed apps, so not listed as installed, but grub2's os-prober sees them in /boot so still adds them to grub menu.

---

### Post by bedayaya on 2014-02-01
Ok, since we're trying to delete stuff I used point 7.

I opened nautilus with 

gksudo dbus-launch nautilus ~/.local/share/Trash/

And I got this Trash window with nothing in it. When I tried to check properties, to see if something was hidden and it crashed saying it can't find the owner.

Back in Terminal I got:


beda@beda-K53U:/$ gksudo nautilus ~/.local/share/Trash
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

**
ERROR:nautilus-properties-window.c:1836:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))
beda@beda-K53U:/$ gksudo dbus-launch nautilus ~/.local/share/Trash/
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

**
ERROR:nautilus-properties-window.c:1836:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))


So I'm not sure Nautilus is working, should I just go the Terminal route?


EDIT: I tried the Terminal route and I get this when trying to deal with delete root's Trash contents in root's Trash bin

beda@beda-K53U:/$ sudo chown -R beda /root/.local/share/Trash/
chown: cannot access &#8216;/root/.local/share/Trash/&#8217;: No such file or directory

---

### Post by oldfred on 2014-02-01
You seem to be mixing commands.  Please review link in #17

You would just launch nautilus with this but nothing else on the line
gksudo nautilus

But if manually using terminal to rm files, not sure where kernels would go to when deleted, .local or root?
**[COLOR=DarkRed]sudo rm -rf ~/.local/share/Trash/*[/COLOR]**

Until you delete the kernels, the trash may be empty.

---

### Post by bedayaya on 2014-02-01
Ok, nautilus is just a file browser so no different  than the usual files window. And I can't really see anything in trash with it, it just crashes.

Terminal wise, I don't get it. I'm supposed to purge the older kernels and then remove them with the rm commands? Or am I just supposed to use rm?

These rm commands seem to be only to empty the trash but why would these old kernels be in the trash?

I mean have I actually deleted the kernels to begin with? I mean when I tried the purge I couldn't tell that they actually getting removed. If so isn't there just a command for "empty trash"?

---

### Post by bedayaya on 2014-02-01
Mmh I browsed a little bit and found this post on removing old kernels 

[http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu](http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu)

I'm going to reboot just to see if I see that "previous linux versions" option.

EDIT: no such luck :/ no previous versions option.

EDIT: but there seem to be other commands to do it here [http://askubuntu.com/questions/244732/is-this-command-to-remove-old-kernels-safe-to-use#244739](http://askubuntu.com/questions/244732/is-this-command-to-remove-old-kernels-safe-to-use#244739) I just don't know if they'll work for me :(

---

### Post by oldfred on 2014-02-01
I thought we already found that dpkg did not show the old kernels. Do those instructions on using dpkg will not work.

With Ubuntu most deletion is a two step process. You have to delete a file and then empty trash. Normally you just do that as  a user and it is not complicated. But when dealing with system files you have to do it with sudo or as the administrator.

So delete old kernels with either rm command or nautilus and then see if in trash. If in trash delete. I have had issues deleting from trash as it just puts it back in. So that may be why the link posted before has you chown  the root trash so then you can delete it.

---

### Post by bedayaya on 2014-02-01
beda@beda-K53U:~$ sudo apt-get purge linux-image-3.2.0-41-generic linux-image-3.2.0-41-generic
[sudo] password for beda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-3.2.0-41-generic
E: Couldn't find any package by regex 'linux-image-3.2.0-41-generic'
E: Unable to locate package linux-image-3.2.0-41-generic
E: Couldn't find any package by regex 'linux-image-3.2.0-41-generic'

beda@beda-K53U:~$ sudo apt-get purge linux-image-3.2.0-41-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-3.2.0-41-generic
E: Couldn't find any package by regex 'linux-image-3.2.0-41-generic'

beda@beda-K53U:~$ sudo apt-get purge linux-image-3.2.0-41-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-3.2.0-41-generic-pae
E: Couldn't find any package by regex 'linux-image-3.2.0-41-generic-pae'

Ok I get these for 3.2.0-41, but they still show up here [http://paste.ubuntu.com/6856631/](http://paste.ubuntu.com/6856631/) so am I even sending anything to trash at all?

---

### Post by oldfred on 2014-02-01
That is still using the dpkg list of installed apps. It is not seeing kernels you installed with the old version as current version does not have those old kernels.

You have to manually delete as I posted before. See post #17.

---

### Post by bedayaya on 2014-02-03
Ok, I still don't understand how can manually delete them.

The purge command doesn't work for the kernels because they were from old installs. I get that, but then where do I find them to remove them?

Post #17 makes reference to nautilus and to the problem of which trash the kernels might end up in, but I still don't know how I can delete the kernels or where they are.

---

### Post by westie457 on 2014-02-03
Does ```
sudo apt-get -s autoclean
``` show anything?

---

### Post by bedayaya on 2014-02-03
> 
beda@beda-K53U:~$ sudo apt-get -s autoclean
[sudo] password for beda: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del mendeleydesktop 1.10.2-stable [32,9 MB]
beda@beda-K53U:~$


It gives this. Doesn't look related to my problem...

---

### Post by westie457 on 2014-02-03
Look in ```
cd /usr/src

ls
``` are any of the older kernels in there?

---

### Post by bedayaya on 2014-02-03
```
beda@beda-K53U:~$ cd /usr/src/
beda@beda-K53U:/usr/src$ ls
linux-headers-3.8.0-19          linux-headers-3.8.0-32-generic
linux-headers-3.8.0-19-generic  linux-headers-3.8.0-33
linux-headers-3.8.0-30          linux-headers-3.8.0-33-generic
linux-headers-3.8.0-30-generic  linux-headers-3.8.0-34
linux-headers-3.8.0-31          linux-headers-3.8.0-34-generic
linux-headers-3.8.0-31-generic  linux-headers-3.8.0-35
linux-headers-3.8.0-32          linux-headers-3.8.0-35-generic

```

Ok, this shows me some old 3.8.0 kernels :)

Shouldn't these be removable by synaptic or something?
The bigger issue is the 3.5 and 3.2 kernels though :/

EDIT: slight off topic, why do people seem to like ls more than ll? ll seems so much more neat and organized ^.^

---

### Post by bedayaya on 2014-02-03
On wubi, 

EasyBCD route: removed the entry and the black screen with the ubuntu and windows options I got after choosing to load windows disapeared.

Uninstall route: I don't have the option to remove it in the uninstall programs or with CCleaner.

bcdedit route:

```

C:\Windows\system32>bcdedit

Gestor de Arranque do Windows
-----------------------------
identificador           {bootmgr}
device                  partition=C:
description             Windows Boot Manager
locale                  pt-PT
inherit                 {globalsettings}
resumeobject            {8cb2d9b0-7c05-11de-842e-b4611d44fefa}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 2
displaybootmenu         No

Carregador de Arranque do Windows
---------------------------------
identificador           {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  pt-PT
inherit                 {bootloadersettings}
recoverysequence        {8cb2d9b4-7c05-11de-842e-b4611d44fefa}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {8cb2d9b0-7c05-11de-842e-b4611d44fefa}
nx                      OptIn

C:\Windows\system32>

```

So no sign of it here anymore.

On the regedit route: 

Trying to find HKLM\Software\Microsoft\Windows\[CurrentVersion]("https://wiki.ubuntu.com/CurrentVersion")\Uninstall\Wubi led me to find no Wubi there.

Using search I do find something that goes by F:wubi.exe,0 on HKEY_USERS\S-1-5-21-(lots more numbers I won't type here unless you figure they're needed)\Software\Microsoft\Windows\CurrentVersion\Explorer\MountPoints2\{(more numbers)}\ _Autorun\DefaultIcon and still I see wubi on the bootrepair reports [http://paste.ubuntu.com/6869616/](http://paste.ubuntu.com/6869616/)

---

### Post by westie457 on 2014-02-03
I cannot work out where those kernels are hiding.
When you did the wubi install which version of Ubuntu went in?
At the moment that is the only place I  think they can be. I may well be wrong though.

As for getting rid of the wubi install, in Windows explorer is there a folder called 'Ubuntu'?

---

### Post by oldfred on 2014-02-03
The source files in /usr/src are not what is appearing in grub menu, but is taking up space and can also be housecleaned.

[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this)

But if old kernels that existed before an upgrade will not be listed anywhere. And those then have to be manually housecleaned. One more advantage of clean installs.

Edit I just ran this. This is my history with my typos and a few other commands edited out.

 1253  dpkg -S /usr/src/*
 1254  uname --kernel-release
 1255  sudo apt-get update
 1256  sudo apt-get upgrade
 1257  sudo apt-get -s autoclean
 1258  sudo apt-get autoclean
 1259  sudo apt-get -s autoremove
 1260  sudo apt-get  autoremove
 1261  df -h
with gksudo nautilus I deleted the old kernels in /usr/src
 1268  sudo chown -R fred /root/.local/share/Trash/
 1274  sudo rm -rf /root/.local/share/Trash/
 1275  df -h
 1276  history

Some of the commands I edited out were duplicates & several nautilus so I could delete files and then look into root's trash to see them, and then confirm they were gone. Found at end better just to open nautilus in another terminal. I did it in several steps so I could confirm what was happening. 
gksudo nautilus

---

### Post by bedayaya on 2014-02-04
**@westie457**

Searching on C: there is a folder called ubuntu with a last modified date of 13-05-2013

```

C:\ubuntu>dir /s /b /o:gn
C:\ubuntu\disks
C:\ubuntu\install
C:\ubuntu\winboot
C:\ubuntu\disks\boot
C:\ubuntu\disks\boot\grub
C:\ubuntu\install\boot
C:\ubuntu\install\custom-installation
C:\ubuntu\install\installation.iso
C:\ubuntu\install\MD5SUMS-metalink
C:\ubuntu\install\MD5SUMS-metalink.gpg
C:\ubuntu\install\ubuntu-12.04.2-desktop-i386.metalink
C:\ubuntu\install\boot\grub
C:\ubuntu\install\boot\initrd.lz
C:\ubuntu\install\boot\md5sum.txt
C:\ubuntu\install\boot\vmlinuz
C:\ubuntu\install\custom-installation\hooks
C:\ubuntu\install\custom-installation\packages
C:\ubuntu\install\custom-installation\hooks\casper-premount.sh
C:\ubuntu\install\custom-installation\hooks\early-command.sh
C:\ubuntu\install\custom-installation\hooks\failure-command.sh
C:\ubuntu\install\custom-installation\hooks\success-command.sh
C:\ubuntu\winboot\wubildr
C:\ubuntu\winboot\wubildr.mbr
C:\ubuntu\winboot\wubildr.tar

C:\ubuntu>

```

**@oldfred**

```
beda@beda-K53U:~$ dpkg -S /usr/src/*
linux-headers-3.8.0-19: /usr/src/linux-headers-3.8.0-19
linux-headers-3.8.0-19-generic: /usr/src/linux-headers-3.8.0-19-generic
linux-headers-3.8.0-30: /usr/src/linux-headers-3.8.0-30
linux-headers-3.8.0-30-generic: /usr/src/linux-headers-3.8.0-30-generic
linux-headers-3.8.0-31: /usr/src/linux-headers-3.8.0-31
linux-headers-3.8.0-31-generic: /usr/src/linux-headers-3.8.0-31-generic
linux-headers-3.8.0-32: /usr/src/linux-headers-3.8.0-32
linux-headers-3.8.0-32-generic: /usr/src/linux-headers-3.8.0-32-generic
linux-headers-3.8.0-33: /usr/src/linux-headers-3.8.0-33
linux-headers-3.8.0-33-generic: /usr/src/linux-headers-3.8.0-33-generic
linux-headers-3.8.0-34: /usr/src/linux-headers-3.8.0-34
linux-headers-3.8.0-34-generic: /usr/src/linux-headers-3.8.0-34-generic
linux-headers-3.8.0-35: /usr/src/linux-headers-3.8.0-35
linux-headers-3.8.0-35-generic: /usr/src/linux-headers-3.8.0-35-generic
beda@beda-K53U:~$ uname --kernel-release
3.8.0-35-generic
beda@beda-K53U:~$ sudo apt-get -s autoclean
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Del mendeleydesktop 1.10.2-stable [32,9 MB]
beda@beda-K53U:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Del mendeleydesktop 1.10.2-stable [32,9 MB]
beda@beda-K53U:~$ sudo apt-get -s autoremove
Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
beda@beda-K53U:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
beda@beda-K53U:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda8        15G  8,4G  5,6G  60% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            1,8G  4,0K  1,8G   1% /dev
tmpfs           356M  928K  355M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,8G  156K  1,8G   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda2       129G   70G   59G  55% /media/beda/OS


```


Alrighty, this  is what I get using the commands oldfred posted.
Then I go on gksudo nautilus and go to /usr/src to find [http://imgur.com/fEQ8wqS](http://imgur.com/fEQ8wqS)
None of the older kernels just the more recent 3.8 kernels (I can clean some up if you think it's worth it)

Btw, what is a "clean install". I installed 13.04 by getting a cd with the 13.04 iso image burned and running it on the 12.04 I was running then. I figured this would "format" the ubuntu like it does with windows OS's.

Why again is this all needed to fix my partitions?

---

### Post by westie457 on 2014-02-04
Still trying to find those lost kernels.
The following command should produce a lot of output if they are found.
The directory they are in will be at the start of each line.```
locate linux-headers-3.2
```
If this does not find them then I think they are in the wubi installation.

If you cannot uninstall wubi then am not sure how to remove them.

---

### Post by bedayaya on 2014-02-04
[B]@[COLOR=#000000]westie457[/COLOR]
[/B]
```

beda@beda-K53U:/$ locate linux-headers-3.2
beda@beda-K53U:/$

```

So, it produces nothing, guess they might be in the Windows folder?
Is there any way to check in windows if they're there?

---

### Post by oldfred on 2014-02-04
We are mixing up at least three different house cleaning issues.
Back in an early post was the suggestion to totally remove wubi from Windows.
That is a Windows issue, as the normal way to uninstall is to remove it just like any other Windows software. Only if that does not work then you have to manually delete files & folders that are wubi based. Instructions for uninstalling here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Then we had old & extra kernels in grub and in /boot that needed to be deleted.
And we had the old & extra kernels in the download source directory.
You have to first delete old files and then separately delete from trash.
And if done as a user it is in user trash, but many of the files required administrator acces so then once deleted they are in root's trash.

I think all of this is because when you reinstalled you did not tick the format box. You did what is called a "dirty" install as it does not reformat and installs all the new software, but then does not remove any of the previous version. New install then does not know about previous versions of kernels and many other applications, but they still are in the default file locations. If reinstalling the same version because of issues a dirty install may make sense.

---

