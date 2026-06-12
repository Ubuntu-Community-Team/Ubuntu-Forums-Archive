---
title: "password will not work after install of windows ubuntu installer (wubi)"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by dan103 on 2014-05-08
Hello to all Ubuntu users! I'm brand new, here, and have never used any Unix/Linux based product, although, technically, Mac OS is suppossedly Linux based. :p

At any rate, I just installed the 32 bit version of Ubuntu (13.02 I believe) on an old Dell GX270 PC running dual boot XP and Win7; 2.9 GHz P4 HypterThreading and 2GB RAM (the most it can take).

During the install, the first box requests a username and password. The ID "user" was already in the "username" box as that is how I was logged onto XP (from where I did the install; not from the Win7 side). So, I entered  a password twice, as indicated, and let the install complete.

Once the install was finished, and the PC booted into Ubuntu, I entered the username ("user" which appeared on the initial install screen prompt) and the password I entered at that time; received an "invalid password" message. What gives?? :-s

At this point, I can only loggon as "guest" which allows me to do absolutely nothing! Help!! ](*,)

Did I do something wrong on the install, or is there a certain password I should be using? As I said, I am brand new at this and could use whatever help you folks in this community can offer Thanks!

---

### Post by coffeecat on 2014-05-08
The password the you need to put in is the password you entered (twice) in the installer. So if you are getting an invalid password error message, the password you are entering now does not match the one you chose during installation. Apart from a simple typo now, two possibilities:

You have inadvertently put caps-lock on now. Check that it's off.

You inadvertently had caps lock on when you chose the password during installation. In which case what you think is lower case will be upper case and vice versa.

If that doesn't help, post back and I or someone will show you how to reset the password.

One comment. You say "13.02". If you mean 13.04, that is past end-of-life and is unsupported - no security updates. If you have installed 13.04 you really need to re-install with a supported version. I would go for the recently released 14.04 which is long-term support (LTS).

Second comment. Wubi is useful for a tryout but runs slower than a conventional install. If you do use it, it's best to consider it as a temporary option. Since you have enough tehcnical knowledge to set up a Windows XP/7 dual-boot, I'm sure you'll find setting up a triple-boot with Ubuntu on a native Linux partition straightforward. :)

---

### Post by Impavidus on 2014-05-08
Mac indeed belongs to the same family as Ubuntu. Not really close family, but you can see the similarities.

There is no Ubuntu 13.02. It's always x.04 or x.10, with the exception of the long obsolete 6.06. The latest release and at the same time latest LTS (=Long Term Support) release is 14.04, so anyone installing now should use 14.04 unless you have very good reasons to use a different release.

Wubi is no longer supported. It may still work and on most older systems it indeed does work, but it's better to install Ubuntu as a real dual boot. Given your hardware, you may be better off using Xubuntu, which is a lighter flavour of Ubuntu. Download the .iso, create a live disk and try it.

There is a way to reset lost passwords ([http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)), but I'm not sure whether that works the same way in wubi.

---

### Post by dan103 on 2014-05-08
Coffee Cat/Impavidus; 

Thank you both for your prompt replies. I did check and, no, I did not have cap locks on and the password I typed in is the same one I've been using on this PC for serveral weeks. And, yes, the version is 13.10, not 13.02; I may be confusing it with version of the installer. 

I did attempt the password reset Impavidus recommended, but the method shown does not work with WUBI.

So, if you could help on resetting or finding out what password it needs, that would be awesome!

Thanks!

---

### Post by coffeecat on 2014-05-08
> **dan103 said:**
> 
I did attempt the password reset Impavidus recommended, but the method shown does not work with WUBI.


It does, but there's an extra trick you have to use.

Boot up and the first boot menu you see is white on black with the choice between Windows and Ubuntu, somewhat like this:

[img]https://help.ubuntu.com/community/Wubi?action=AttachFile&do=get&target=Wubi1.png[/img]

That is from the Windows bootloader. If you select Ubuntu, the Windows bootloader hands over control to GRUB, the Ubuntu bootloader, which has a purple menu like the one in the link Impavidus posted. The problem is that the grub menu does not display unless there is more than one operating system to control (or older kernels installed). As you'll see from that link, the way to get the purple grub menu to display so that you can select recovery mode is to press shift. The tricky part is getting the timing right. It's easy enough with a conventional Ubuntu installation when grub is invoked directly from the BIOS, but the Windows bootloader might complicate things. I've never had to do this with a wubi install but try one of these:

Highlight Ubuntu in the white on black menu and then hold down shift while pressing enter.

As above but press enter and then immediately hold down shift.

As above but press enter and then tap shift repeatedly.

Hopefully, one of those will work.

If you do manage to get into recovery mode, you need to get the syntax of the mount command right:

```
mount -o rw,remount /
```

Some people misread that, put a space between the comma and remount and, of course, that doesn't work.

Last thing - Ubuntu 13.10 reaches end of life in July this year. If you get this sorted you'll need to upgrade to 14.04 before then.

---

### Post by dan103 on 2014-05-08
Coffecat, thanks for that excellent info. I will give it a try tomorrow and see how it works. Additionally, after wubi installed, the system booted and I was presented with a triple choice menu; Windows XP Pro, Windows 7 and Ubuntu. If i chose Ubuntu, I received an error message  that I needed to run the install again. When I chose the XP menu item, I was taken to another sub-menu that displayed XP and Ubuntu only. Choosing Ubuntu there booted me into the OS no problem; interesting.

I'll keep you posted as to the results. Thanks!

---

### Post by 3rdalbum on 2014-05-09
Don't use Wubi.

I am wondering if the username you selected, 'user', is a reserved word in Linux.

When you reinstall, set the username as your actual name or internet handle. Not any technical words like user, admin, root, etc.

---

### Post by coffeecat on 2014-05-09
> **dan103 said:**
> Additionally, after wubi installed, the system booted and I was presented with a triple choice menu; Windows XP Pro, Windows 7 and Ubuntu. If i chose Ubuntu, I received an error message  that I needed to run the install again. When I chose the XP menu item, I was taken to another sub-menu that displayed XP and Ubuntu only. Choosing Ubuntu there booted me into the OS no problem; interesting.


I'm really rusty on the details, but I guess that would be something to do with the fact that there are significant differences between the XP and W7 bootloaders. You appear to be booting first into the W7 bootloader and then chainloading to the XP one - thence to grub if you choose Ubuntu. It could be that the wubi installer is confused by the two versions of Windows and didn't set up the Ubuntu choice in the Windows 7 boot menu properly - hence the error message. I doubt whether the wubi developers really considered the possibility of a Windows dual-boot - wubi is only intended for complete beginners, and if you can set up a Windows dual-boot, you are not a complete beginner, even if you don't have Linux experience. :)

I wouldn't go as far as 3rdalbum and say bluntly, "don't use wubi". Rather, if you can manage to reset your password, login and get a feel for Ubuntu in the knowledge that wubi is sluggish and second-best. Then have a think about installing Ubuntu conventionally. If you can't manage to reset your password, post a screenshot of the disk manager window from Windows so that we can see your partition layout, and then we can make suggestions for redoing the partitions in preparation for setting up a XP/W7/Ubuntu triple boot.

---

### Post by dan103 on 2014-05-09
Coffecat/3rdalbum;

Again, thanks to you both of taking the time to respond. Regarding Windows, no; Ubuntu, yes. I am a complete beginner in that regard with Ubuntu, so I chose this message board.

Coffecat, I attempted the boot into the recovery mode, but none of the options you listed worked. So, I uninstalled and am attempting a re-install using the advice 3rdalbum mentioned; instead of "user" I'm using my own name and password; see how that works. Failing any of that, I'm going to throw in the towel, create another partition and install Ubuntu to the local drive.

Now, should I install the 13.10 version or do the 14.xx version you suggested? If so, then what flavor: 32- or 64-bit? It's an older pc with 2GB of memory and a P4 2.9GHz socket 458 processor.

Also, booting into the OS, a message was displayed: "mount: can't read 'proc/mount' no such file or directory"

Not sure what that means; if it's important or not.

---

### Post by coffeecat on 2014-05-09
> **dan103 said:**
> 
Also, booting into the OS, a message was displayed: "mount: can't read 'proc/mount' no such file or directory"

Not sure what that means; if it's important or not.

That throws up something interesting.

If you search through the paragraphless wall of text that is the OP in this thread:

[http://ubuntuforums.org/showthread.php?t=2100620](http://ubuntuforums.org/showthread.php?t=2100620)

You'll see that the OP and another poster get the same message as you and can only log in as guest. But the thread comes to no satisfactory conclusion. Also this one:

[http://ubuntuforums.org/showthread.php?t=2170023](http://ubuntuforums.org/showthread.php?t=2170023)

Same again if we read the OP's "root user" as the usual admin account rather than literally the root account. In that thread Old_Grey_Wolf, who gives good advice, states that this is a bug come feature of wubi post 12.04. That is new to me, although to be honest, I've only ever played with wubi to get a feel for it, and not for some time. I think the word "discontinued" for wubi post 12.04 is not quite right. It certainly is no longer being actively developed, but I notice that wubi.exe is still included with the 14.04 installation ISO.

13.10 or 14.04? I'd suggest going for 14.04 since 13.10 is so near to its use by date. But with increasing lack of enthusiasm seeing as wubi seems to be suffering from bit rot. I'm beginning to agree with what 3rdalbum said earlier, and suggest you might want to dump the idea of wubi and go for a proper install. The only thing to be said for wubi now is that it is easily uninstalled.

Some things to think about if you want to go for a proper Ubuntu install.

We need to know how many partitions you have already, and how big. Unlike Windows, Ubuntu can boot from a logical partition. And, unlike Windows, it uses a swap partition rather than a swap file by default. Which means with a pre-existing Windows 7/XP dual-boot, your best option would be to make enough space, create an extended partition and then logical partitions in the extended for Ubuntu. You can do all of that in the Gparted partitioning tool in a live session of Ubuntu booted from a DVD or USB, **except** shrink the Windows 7 partition.

Rule of thumb: OK to shrink a Windows XP C:/ partition or E:/F:/whatever data partition with Gparted; not OK to shrink a Windows 7 C:/ partition with Gparted. If you shrink a Windows 7 C:/ partition with Gparted it can make Windows unbootable - which makes for very unhappy bunnies posting here! You can use Windows 7 own disk management tool for this. 

One last point: installing Ubuntu to its own partition(s) as a multi-boot with Windows means that Ubuntu's grub bootloader installs its own stage 1 to the mbr, replacing the approx 440 bytes of Windows code there. Which is OK because you use grub to boot Windows. But you need to know in case you subsequently want to give up using Ubuntu. There are several ways to restore the Windows mbr, including use of an Ubuntu live session, but again this is the cause of yet more unhappy bunnies coming to this forum who have simply deleted their Ubuntu partition and can't boot into anything.

Food for thought! :)

Last thing: 32 or 64 bit? I only recently learnt that a few of the last P4's were 64-bit, but I don't know enough about CPUs to know whether that one is 64 bit or not.

---

### Post by dan103 on 2014-05-09
Yes, food for thought indeed!:o

That was a lot of info, Coffecat (BTW I like that ID, being a coffee lover myself :D). This is going to have to be read and re-read several times before I get it all.

The shrinking/enlarging of Win7 partitions (regardless of it's a C: or logical drive) is fraught with horrors. I attempted that with another dual boot pc, when the win7 partition was losing space, and, after enlarging it with Aeomi partition manager (a free-for-home-use PC disk partitioning tool), could not boot into the Win7 drive (the XP drive was fine); had to use the Win7 repair disk to correct.

But, your points are indeed well taken and also cause me some major concern. If need be, and I have to remove the Ubuntu installation, that could be a real problem. Many thanks for clueing me in that simply deleting the partition would not work; I may have well just done that! :eek:

After re-reading your post, I'll decide whether it's wise for me to proceed.

---

### Post by coffeecat on 2014-05-09
> **dan103 said:**
> I attempted that with another dual boot pc, when the win7 partition was losing space, and, after enlarging it with Aeomi partition manager (a free-for-home-use PC disk partitioning tool), could not boot into the Win7 drive (the XP drive was fine); had to use the Win7 repair disk to correct.

Indeed - that re-inforces the message. Interesting that a Windows based partitioner is as potentially unhealthy as a Linux partitioner when resizing a Windows 7 (and Vista and 8) C: partition. Don't blame the partitioners though. I'm hazy on the details, but it's something to do with the position of the partition boot sector or boot files having their absolute rather than relative position referred somewhere in the installation. But the Windows Disk Management tool is reliable - in my experience. I've resized several Windows 7 partitions with it, and each time fairly quickly and without problem.

> **dan103 said:**
> If need be, and I have to remove the Ubuntu installation, that could be a real problem.

No problem at all, in fact. You have a Windows 7 repair disk already. The fix is trivial. One for your bookmarks:

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

In most cases, fixboot from the Windows repair disk is not needed, only fixmbr. And that page give two alternatives for fixmbr from an Ubuntu live session. Fixboot would be needed after resizing a Windows 7 partition using Gparted or - ahem - Aeomi! :wink:

---

### Post by dan103 on 2014-05-09
Also, I've heard some disturbing news; is this forum going bye-bye on June 1st like the rest of Ubuntu.com?

---

### Post by sotiris2 on 2014-05-09
Ubuntu One , a cloud storage service (like dropbox), is going off the air in the 1st of June not Ubuntu.com or this forum.

---

### Post by matt_fussell2 on 2014-05-09
The GX270 is a 32 bit machine, so stick with the i386 distro version.

---

### Post by coffeecat on 2014-05-09
> **dan103 said:**
> Also, I've heard some disturbing news; is this forum going bye-bye on June 1st like the rest of Ubuntu.com?

Neither ubuntuforums nor ubuntu.com is going away. Ubuntu One cloud storage is being withdrawn, that is all. Ubuntu One SSO stays so you will still be able to log into the forum.

---

### Post by dan103 on 2014-05-12
Right now I have two partitions; one is the C: partition with XP (about 90gb); the other is the E: partition with Win7 (about 60gb).

---

### Post by dan103 on 2014-05-14
Okay, I decided to "bite-the-bullet" and go with the full install hoping that Ubuntu will know what to do re: the partition formating whether logical, extended, whatever as Wndows wasn't much help. All it created was a "basic volume" with a drive letter formated NTFS; that's it. 

So, I placed the 32-bit version in the DVD/CD drive, booted to it and..... nothing. All I saw was some funky figure of a "keyboard" like symbol followed by what looks like an "equals" sign followed by some guy-type figure standing in a circle. The screen then goes black and nothing further happens; no install screen or prompt of any kind. 

Any suggestions?

---

### Post by coffeecat on 2014-05-14
When the live DVD first boots, you should first see a purple screen with two icons at the bottom of the screen: a keyboard and a representation of a human figure. If you leave it, it should boot to a choice between going on to a live tryout session or to start the installer. If you tap any key when the two icons appear you should be taken to an old-style text menu. One of the choices is a disk check. See if you can get to the menu and do a disc check to make sure that the disc is OK. Whether or not it is OK, I suggest you start a new thread because the title with this one containing wubi won't attract those that can best help you. If the disc is OK, it may be that you need to add some kernel boot parameters at the text menu. For that we'll need some details of your graphics card.

Also - don't rely on the installer knowing what to do. You have an unusual partition layout with a dual-boot of two varieties of Windows. A partition layout to accommodate Ubuntu needs to be carefully thought out and created before you start the installer.

So - start a new thread with a relevant title. Include details of the problem with the live DVD, your graphics card, your current partition layout (a screenshot of the Windows Disk Management utility would be useful) and what you wish to achieve.

Good luck.

---

