---
title: "How to unpick (and restore) parallel installations [solved]"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by DoctorDunc on 2014-07-09
I installed xubuntu then lubuntu in parallel but I've decided to stick with xubuntu (easier to configure how I like it) so how do I get rid of the boot menu?  I've been into etc/grub.d but the scripts are so full of variables I can't make head or tail of them (I'm used to scripts, I used to do Unix but it's a long time ago).  I'd like to understand this but it's making my head hurt and in the end I just want to get on with using the machine.

So, how do I obliterate the lubuntu installation?

Cheers,
DD

[edit] Restoring starts on page 2

---

### Post by Impavidus on 2014-07-09
Make sure grub is controlled by Xubuntu (if necessary reinstall grub from Xubuntu), remove Lubuntu and update grub. Renaming the Lubuntu /boot directory should be enough to remove Lubuntu and is reversible. If everything is OK, you could completely remove it and reuse its partition for something else.

---

### Post by DoctorDunc on 2014-07-10
I'm sorry, I don't understand what you mean and there are several versions of grub.  I spent ages setting up xubuntu so I don't want to reinstall but I'm very disappointed that the authors of grub didn't think to incorporate a means of rolling back.

I presume lubuntu controls this because it was the last one installed and is the default.

---

### Post by Bucky Ball on 2014-07-10
Okay, boot into Xubuntu and do this to make sure it is controlling grub:

```
sudo install-grub /dev/sda
```

... presuming sda is the name of the drive you are using (if you have one drive it would be but check in Gparted).

Boot from a LiveDVD/USB, 'Try Ubuntu', once at the desktop launch Gparted, delete the Lubuntu partition. 

You're done. Reboot. Once you're back in Xubuntu, run:

```
sudo update-grub
```

PS: Don't edit the grub .cfg file directly (in almost every case). You should always edit '/etc/default/grub' then run:

```
sudo update-grub
```

That will write the changes to the .cfg file. ;)

---

### Post by DoctorDunc on 2014-07-10
Thanks, I think I see the way but now I come back to another gripe that made me try lubuntu in the first place.  I have gparted installed (ticked in Ubuntu Software Centre) but I can't find it in the menu, either by search or in the System category (hardly anything there curiously).  Trying "Run gparted" tells me I need to be root but I never needed to be on other flavours.  If I su in terminal and use my password it rejects this but again, this has worked on other installs. 

So what gives here?  

[edit: gparted is in All Settings]

---

### Post by Bucky Ball on 2014-07-11
Open a terminal:

gparted

That's all you need to type.

---

### Post by DoctorDunc on 2014-07-11
"sudo gparted" as it turns out but why can't I just run it from the menu?  What's with this distro?  It wasn't like this with SolydX.

Thanks fro your help btw :) - I don't want to sound ungrateful - I'm not.  It's just that I'm just getting a little frustrated with all thsi faffing about but I suppose that's part of the joy of open-source...

I'll post back once I've had a bash at your previous post

Thanks, DD

---

### Post by DoctorDunc on 2014-07-11
> **Bucky Ball said:**
> Okay, boot into Xubuntu and do this to make sure it is controlling grub:

```
sudo install-grub /dev/sda
```
Copied that in, ran it and got:

sudo: install-grub: command not found

---

### Post by Impavidus on 2014-07-11
That must be grub-install, not install-grub.

---

### Post by DoctorDunc on 2014-07-11
Hooray!  Thanks :)

[edit] so for anyone coming across this with the same problem, the required command is (from xubuntu): 

**sudo grub-install /dev/sda** [FONT=arial](assuming this is your device)[/FONT]

Now when I boot up there is no longer a boot menu and I go straight to xubuntu.  The lubuntu partition still exists but is now unmounted.  Rather than delete it I've decided to use it as my new home partition (there may be a new thread about this shortly!).

As for the gparted confusion, it appears in the All Settings menu and runs fine from there.

---

### Post by DoctorDunc on 2014-07-11
In the interests of understanding this better...

What if I now change my mind and want to reinstate the dual-boot?  The xubuntu partition has always been the bootable one, hasn't it, so there must have been "instructions" on it somewhere to transfer control to the lubuntu partition, which have now been overwritten.  The menu must have been on the lubuntu partition, no?, and is still there, although unmounted.

Is this as quick a fix as unpicking was?

---

### Post by Bucky Ball on 2014-07-11
You just did exactly this with the other install. 

There are no instructions. It depends on which OSs grub is installed in the MBR, that all.

Boot into the OS you want to control grub and run the command that was rightfully corrected earlier (thanks, and apologies for my mistake, it was very late here and I should have been in bed!).

sudo grub-install /dev/sda

Just remember, if you give Lubuntu control of the grub and you boot into Xubuntu, do an upgrade and it is a new kernel, that will update its grub during the process, *but you'll need to boot into Lubuntu and do 'sudo update-grub' for the new Xubuntu kernel to be shown on the menu list at boot*, if you follow, as Lubuntu runs the grub at boot, NOT Xubuntu. Hope that makes sense.

---

### Post by DoctorDunc on 2014-07-12
Ok, I get that but what I don't get is how to boot into an OS that is no longer mounted.  I'm now booting straight into sda1, there is no menu to select anything else, and lubuntu is on sda6.  I'm aware (I think!) that I have xubuntu's grub in the MBR (and installed in /boot/grub and /etc/grub.d) but I've got no idea where to go from here.  I obviously need to do some serious reading up (seeing as part of the reason for going linux was to learn) but my head fills up quick these days so any pointers would be gratefully received.

*(For the record: sda1 is / (flagged "boot"), sda2 is extended containing sda5 (swap) and sda6 (lubuntu, unmounted).  And it was the installers wot done it.)*

Cheers, DD

---

### Post by Bucky Ball on 2014-07-12
When you boot, hold shift key after the BIOS screen. That should bring up a grub menu with a list of kernels and OSs installed on system to choose from.

---

### Post by DoctorDunc on 2014-07-13
There are only two options in the menu: nomal and with options (plus a couple of memtest).  It's not picking up the lubuntu partition (sda6) so I suppose I have to mount it but GParted won't let me (the option is there but is greyed out).  I've had a look at fstab but that looks like dangerous territory so I'm not inclined to tamper.

---

### Post by Bucky Ball on 2014-07-14
But tamper you must if you want if you want it mounted at boot! It's simple and to avoid any mishaps, save a copy of the original first:

```
sudo cp /etc/fstab/ /etc/fstab.backup
```

Make a mount point for the Lubuntu partition:

```
sudo mkdir /media/Lubuntu
```

Then open the original:

```
sudo nano /etc/fstab
```

Now, open another terminal and:

```
sudo blkid
```

In that list, you will see your Lubuntu partition with a UUID number. That is what you want. Back in the other terminal, add these two lines:

```
#Entry for /dev/sda* [your Lubuntu partition and this line can read as you want] :
UUID=[UUID from 'sudo blkid' here]      /media/Lubuntu   ext4    errors=remount-ro       0       1
```

So, for instance, if the UUID you found for the Lubuntu partition with 'sudo blkid' is '865e6caa-b7bf-49b5-8d41-bf7e8d03be32', then the boot line would look like this:

```
#Entry for /dev/sda* [your Lubuntu partition and this line can read as you want] :
UUID=865e6caa-b7bf-49b5-8d41-bf7e8d03be32      /media/Lubuntu   ext4    errors=remount-ro       0       1
```

Once the changes are made, ctl+x, 'y', then reboot to see if the changes are correct and the Lubuntu partition mounts at boot. ;)

If all else fails and you need the original fstab back, simply:

```
sudo mv /etc/fstab.backup /etc/fstab
```

Done. Good luck.

PS: Do you want this mounting at boot? Does it show up in a file manager now? When you right click it (in a file manager, NOT Gparted) is the 'mount' option available? If so, when you click it what is the exact error message? Permissions error?

---

### Post by DoctorDunc on 2014-07-14
Ok, so I've edited fstab, which now has the extra line:
```

# /dev/sda6
UUID=bbc7dd70-36cc-4fa5-a82c-b64e5947c068 /media/Lubuntu  ext4    errors=remount-ro 0       1
```

and it works, sda6 is (still) showing as a removeable drive on the desktop and file manager but this time is mounted.  Definitely.  All the menus say so.  But I'm still not seeing Lubuntu on a shift-reboot.  What I get is:

Main menu:
```
*Ubuntu
 Advanced options for Ubuntu
 Memory test (memtest86+)
 Memory test (memtest86+, serial console 115200)
```

Advanced options:
```
3.13.0-30-generic
3.13.0-30-generic (recovery mode)
3.13.0-24-generic
3.13.0-24-generic (recovery mode)
```

Both boot to Xubuntu.  30 is what I was running before I started this mod (I just so happened to have made a note).  So I have now commented out the new line in fstab, rebooted and got exactly the same menu and options.  It's the correct edit because sda6 is no longer mounted.

sda6 contains a file system.  cat *-release in the local etc folder shows the same generic stuff I get from /etc.  There's nothing in local proc folder and I don't know where else to look to be certain of what I'm dealing with.

Gonna have to sack this for the night, I'm afraid.  Neck and shed both gone but progress I feel and it's all gonna be useful, so your efforts are very much appreciated.  Thanks.

---

### Post by Bucky Ball on 2014-07-15
When booted to the Xubuntu install:

```
sudo update-grub
```

Reboot. Anything?

Yes, you are making progress. Good work! ;)

---

### Post by DoctorDunc on 2014-07-15
Yep, I get:
```
Found linux image: /boot/vmlinuz-3.13.0-30-generic
Found initrd image: /boot/initrd.img-3.13.0-30-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04 LTS (14.04) on **/dev/sda6**
done
```
Which, as soon as you see **this**, is obviously going to work...and does!  

So to get rid of it again now I reboot into Xubuntu, unmount sda6, rerun "sudo update-grub" and it picks up the file system on sda6 even though it's unmounted(!) so I comment it out of fstab, reboot (and I'm getting yellow text - very pretty), rerun "sudo update-grub" and it *still* picks up the file system on sda6 (*@%!).  Don't tell me I'm gonna have to reinstall it again...so I have, rerun "sudo update-grub" and guess what it's still there so I'm going to the shops now.

Back.  Tried various combinations of install/boot/update, no joy, it's Groundhog Day.  All I did first time was install grub from xubuntu and then update.  I'm missing something...

---

### Post by Bucky Ball on 2014-07-16
Best way to check is to open a terminal and:

```
sudo blkid
```

Open another terminal and:

```
sudo nano /etc/fstab
```

Now, check the UUIDs on the uncommented lines in fstab against the UUIDs shown by 'sudo blkid'. Specifically, see if the UUID 'sudo blkid' gives for /sda6 against the UUID numbers that are on uncommented lines in the fstab. sda6 could be mounting under a heading for another partition, partition numbers may have been changed around during your 'procedures'. Open Gparted and double check sda6 is indeed still sda6.

Incidentally, good idea to backup fstab before breaking it! 

```
sudo cp /etc/fstab /etc/fstab.backup
```

If things go pear-shaped and you need the old one back:

```
sudo cp /etc/fstab.backup /etc/fstab
```

---

### Post by DoctorDunc on 2014-07-16
Bloody computers! This morning it booted straight into Xubuntu so to make sure I uderstand this properly I went through the whole process again.  Got boot menu with optional Lubuntu back (easy) but having the same trouble getting rid of it again as I had last night, even with a proper shutdown.  Partition names and UUIDs haven't changed and I've restored the original fstab.  Surely it must be possible without having to make Lubuntu the default (which I'm not even sure did the trick last time) but I've re-installed it for Xubuntu again anyway. I'll keep at it and post back...

---

### Post by Bucky Ball on 2014-07-16
> **DoctorDunc said:**
> Bloody computers! This morning it booted straight into Xubuntu so to make sure I uderstand this properly I went through the whole process again.  Got boot menu with optional Lubuntu back (easy) but having the same trouble getting rid of it again as I had last night, even with a proper shutdown.  Partition names and UUIDs haven't changed and I've restored the original fstab.  Surely it must be possible without having to make Lubuntu the default (which I'm not even sure did the trick last time) but I've re-installed it for Xubuntu again anyway. I'll keep at it and post back...

Now you've got grub with Xubuntu, boot into Xubuntu, open a terminal and:

```
sudo nano /etc/grub/default
```

... then check this:

[http://ubuntuforums.org/showthread.php?t=2232813&p=13065351&viewfull=1#post13065351](http://ubuntuforums.org/showthread.php?t=2232813&p=13065351&viewfull=1#post13065351)

Basically, you change the line that looks like this:

```
GRUB_DEFAULT=0
```

... to the appropriate number, save and close the file, then:

```
sudo update-grub
```

... then reboot and see how you go.

---

### Post by DoctorDunc on 2014-07-16
GRUB_DEFAULT=0 is already correct,isn't it, as it points to Xubuntu which I want. I didn't have to do this last time...

---

### Post by Bucky Ball on 2014-07-17
If 0 is Xubuntu, then yes, all good. Don't know why it's defaulting to the other. You might want to try installing Grub Customizer and forcing the issue. You'll find it with a quick search (don't think it's in the repos at this point, but check first). I think Ubuntu Tweak can do a similar thing, but not sure, never used.

---

### Post by DoctorDunc on 2014-07-17
It isn't defaulting to Lubuntu, it goes into Xubuntu by default.  But what I'm trying to do is to prevent Lubuntu appearing as an option at all and I don't understand why it is.  Seeing as its partition isn't even mounted (and I've reinstalled grub under Xubuntu for good measure) how does update-grub even find it?

Back when we first tackled this, booting into Xubuntu (which at the time was only an option to a default Lubuntu), installing grub and updating was enough to revert back to how things were before I installed Lubuntu in parallel to Xubuntu to try it out - no boot menu and straight to Xubuntu.  Now for reasons that I can't fathom, the same process isn't working.  I've even gone so far as to reinstate Lubuntu as the default and then try to revert from there.  Something's got written that wasn't before.  Or I'm missing a step, or doing things in a different order...

---

### Post by Impavidus on 2014-07-17
I couldn't completely follow what you were actually (trying to) do(ing) in recent days, but maybe I can clear up some confusion.

Whenever you run update-grub, update-grub will run the OS prober. The OS prober searches for certain boot files in all partitions of the system and puts an entry for the OSs it finds in the grub menu. It doesn't matter whether the partitions are mounted. If they are not, they will be mounted temporarily just to check for the presence of an OS. So if you want to remove Lubuntu from the grub menu, you have to either disable the OS prober or remove those boot files from sda6. If the OS prober can't find them, no entry will be created.

In post #10 you wrote you wanted to reuse sda6 as your /home partition. So I assume you want to completely remove the Lubuntu system. You can do this by first mounting it in your Xubuntu system. sda6 contains the entire Lubuntu OS, although you noticed (in post #17) that /proc was empty. That is because another (pseudo) file system is mounted there only when the system is running. Next you can delete the files on sda6. With the boot files (like the kernel image) gone, the OS prober will no longer detect it and will no longer put an entry for Lubuntu on sda6 in the grub menu.

Just double-check that Xubuntu is in control of the boot process or removing the grub files on sda6 will make your computer unbootable. After deleting those files, run sudo update-grub. Your Lubuntu system will now be permanently gone.

As to why the entry for Lubuntu disappeared (post #15) and later came back (post #19), I think that the file system on sda6 was somehow damaged, as a result of which the OS prober couldn't detect Lubuntu. That would also explain why gparted couldn't mount it (post #15). Putting it in fstab caused the sda6 file system to be mounted at boot (post #17), which caused a file system check, repairing the file system so that the OS prober again detected Lubuntu the next time you ran update-grub and put it back in the grub menu. Except for this coincidence, it didn't matter whether your sda6 partition was mounted or not.

To reuse sda6 as your /home partition, this may be good reading: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by DoctorDunc on 2014-07-17
That explains it! Now, just to clear things up...if I can...(sorry about getting a bit too stream-of-conciousness back there)

Once I got things back to how they were before I installed Lubuntu (i.e. booting straight to Xubuntu with no menu) I decided to use what was now a spare fs to practise getting to know grub a bit better.  Bringing Lubuntu back was easy enough (with your help, thank you!), as was making it default, as was reverting Xubuntu to default, but stopping Lubuntu appearing in the boot menu... well now I know why my efforts were in vain.  But never mind, I've learnt loads.  Thank you.  You are very patient.

So...

I think that's enough of that so I'm now going to have a read of that article (thank you) and get stuck into that.

Cheers,
DD

---

### Post by Bucky Ball on 2014-07-17
All good. Please mark the thread as solved to help others and post a new one with any further support or other issues/questions. Good luck and enjoy the learning curve. ;)

---

