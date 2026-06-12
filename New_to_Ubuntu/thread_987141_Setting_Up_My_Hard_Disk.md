---
title: "Setting Up My Hard Disk"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Roger Allott on 2008-11-19
My HDD is currently partitioned into three drives, or four if you include the Linux swap thingy-wotsit. It used to be the internal HDD for a machine that went tits up a few months ago, so now it's in its own caddy and I'm using it as an external HDD connected through USB.

A long long time ago it had Windows Home on one drive, Windows Pro on another drive, and the third drive was set aside for data/document storage.

Windows Pro decided to stop working one day, so I took the opportunity to install openSUSE on the second drive (now ext3 format). It installed itself fine and I got a nice green screen on start-up that offered me the option of booting Windows Home, openSUSE or openSUSE in safe mode.

But then the machine it was installed on blew up, so the HDD is now, as I said above, in a caddy as an external HDD.

I've formatted (NTFS) the first drive that used to contain Windows Home, but of course Windows Vista (my current O/S on my new machine) can't see the drive that has openSUSE on it, so I can't format it. I suppose I could do from Ubuntu Live CD, but I haven't yet.

When my external HDD is connected to my machine when it boots up, rather than going into Vista as it usually does, I get the green screen offering me Windows Home, openSUSE or openSUSE (safe mode). Obviously, if I choose Windows Home, it just grinds to a halt immediately because there's nothing there.

If I choose either of the openSUSE options, it goes through its boot up routine but comes a cropper, bizarrely, when it tries to find the driver for the hard disk that it's running! I could understand if it fell over on a bit of hardware that was new to it, but surely it should know what it's sitting on as that hasn't changed. Odd.

Anyway, what I now want is to have my system set up as follows:

I want there to be no noticeable changes to my internal HDD so that when it powers up without the USB HDD connected, I just go into Windows Vista as I do now. No flash screen asking me whether I want Vista or Ubuntu therefore.

However, if my external HDD is attached, I want Ubuntu to fire up. Again, I would prefer this to be automatic without any flash screen giving me options.

So, having explained my position, how do I get rid of the green initial screen that openSUSE installed that's now completely pointless?

And secondly, what steps do I need to take to install Ubuntu on my external HDD such that it automatically boots up if connected without flashing up an initial option screen?

Any help would be much appreciated.

---

### Post by Het Irv on 2008-11-19
> **Roger Allott said:**
> 
Anyway, what I now want is to have my system set up as follows:

I want there to be no noticeable changes to my internal HDD so that when it powers up without the USB HDD connected, I just go into Windows Vista as I do now. No flash screen asking me whether I want Vista or Ubuntu therefore.

However, if my external HDD is attached, I want Ubuntu to fire up. Again, I would prefer this to be automatic without any flash screen giving me options.


Okay for this part, it shouldn't be to hard, just set your BIOS Boot order as follows : CD/DVD, USB, HD.... and so on.

If your Internal Hard Drive has GRUB or the Open Suse boot-loader on it you can erase them by Booting into a Windows Recovery Console and typing ```
fixmbr
``` I am not as familiar with Vista's boot disc, but I know there is one on the XP disc.

You can Hide GRUB on the external drive but changing the timeout to a low number, or uncommenting the "hiddenmenu" line in the menu.lst file ```
gksu gedit /boot/grub/menu.lst
```

---

### Post by Roger Allott on 2008-11-19
Here's my idea. Does this sound sensible as regards whether it will leave me with the set-up I'm looking for?

[LIST=1][*]Remove the internal HDD from my PC.

[*]Boot PC with the Ubuntu Live CD.

[*]Insert external HDD through USB connection.

[*]Format the second drive on the external HDD (the one that currently has an unplayable install of openSUSE). I'm hoping that doing that will get rid of the menu.lst file that's currently flashing me the green screen when I boot from the external HDD.

[*]Unmount the first and second drives on the external HDD.

[*]Run the Install script from System > Administration > Install. When it gets to step 4, I'll install Ubuntu to the second drive.[/LIST]

The system will, I hope, look to Ubuntu like its being installed on a completely clean machine that currently has no O/S of any kind on it, so it will not create a menu.lst file with a flash screen on booting with the USB HDD connected. Also, because the internal HDD has been unaffected by the procedure, when I boot without the USB HDD connected, it just boots as now straight into Vista.

Anyone foresee any problems with this cunning plan?

---

### Post by Keen101 on 2008-11-19
Here is how i would do it:

1. erase all partitions on the external HDD (after backing up data) with gparted live-cd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

2. Unplug internal windows drive. (while installing ubuntu)

2.5. (optional) set up any fat32 and/or NTFS partitions with gparted live-cd on the back half of the external HDD.

3. Install ubuntu onto external HDD (on first half or the whole drive if step 2.5 is not what you need)


Following the above steps should set up a system which is exactly what you want. It's how i set up my system. If i wantxp i boot with external drive not plugged in. If i want ubuntu to boot, i plug it in, and then turn it on.

---

### Post by Roger Allott on 2008-11-19
Keen101, you're absolutely spot on that that's what I want and I'm delighted to see that I'm not completely bonkers for wanting it that way. Or may be it's just reassurance that there's someone else out there who's just as bonkers as me!

I've just got to weigh up in my head whether there's some benefit in keeping my partitions as they are, then I'm going in for the big plunge.

---

### Post by Keen101 on 2008-11-19
glad to have helped. I added the bit about step 2.5 because sometimes it's nice to have a spot that can be read by windows AND ubuntu AND OSX. I have the back half of my external drive partitioned as FAT32.

The reason i set it up that way was because when i first set it up, i had the idea that i would be using it on school computers mostly, and it's just nicer anyway. No having to wait at the GRUB prompt.

---

### Post by Roger Allott on 2008-11-20
Someone in Linux really **really** doesn't like me. AAARRRGGGHHHHH!!!

I decided to set up my drives in almost an identical manner to the way you have yours, Keen101. The only difference I made was in having my back end partition NTFS instead of FAT32.

I did this using the gparted utility which I downloaded and burned to CD.

The front end (30Gb) I left unallocated, in the belief that Ubuntu would arrange that during the install in the best way it thought to do so.

So then I booted Ubuntu Live CD. Under Partition Manager (also called gparted??) I took a screenshot of this:
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot--dev-sda-GParted.png[/IMG]

Then I started the install process and encountered problems yet again at step 4. The Prepare Partitions screen showed up blank:
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-Install.png[/IMG]

And then when I tried to go forward, it gave me the following error message:
[IMG]http://i476.photobucket.com/albums/rr122/Latrax/error1.png[/IMG]

I've then tried changing stuff in Partition Manager to make it get through this stage, but nothing I try has worked. In particular, there seems to be nothing in the various options that mentions 'root' or anything similar, such as '/'.

Anyone out there with a flash of inspiration for me??

---

### Post by Keen101 on 2008-11-21
umm..... weird. that shouldn't happen.  Are you using a 8.10 live-cd? if yes, i think there might be a bug in the partitioner software which incidentally is gparted, but not really as good as the gparted live version.

if you were doing this with a 8.10 cd, then i guess try a 8.04 cd. You could also try the alternate install disk of either 8.04 or 8.10. good luck. Don't give up yet!

---

### Post by Roger Allott on 2008-11-22
> **Keen101 said:**
> umm..... weird. that shouldn't happen.  Are you using a 8.10 live-cd? if yes, i think there might be a bug in the partitioner software which incidentally is gparted, but not really as good as the gparted live version.

To do all the partitioning stuff, I'm using the full gparted Live CD, not the one that's part of the Ubuntu Live CD.

---

### Post by Keen101 on 2008-11-22
ok, i think you need to format the drive, and then partition it.
 
In my case the hard drive i bought was already formatted, but not partitioned. I think you can use fdisk or dd, but i've never actually formatted a drive in linux.

try doing "man fdisk" in a terminal, or "fdisk --help" in a terminal to find out more. There is also google and these forums that you can search too.

---

### Post by roninbv on 2008-11-22
I would advise using cfdisk, since it provides a more friendly interface than fdisk. You will want to format that unallocated space to ext2 or 3 and set it's mount point to "/".

---

