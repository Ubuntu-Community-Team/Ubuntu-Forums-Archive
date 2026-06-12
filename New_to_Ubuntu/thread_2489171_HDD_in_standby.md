---
title: "HDD in standby"
date: 2023-07-20
forum: New to Ubuntu
---

### Post by wackanoodle on 2023-07-20
I recently built a home media server that I also want to use as a nas. However my 4tb hdd is in standby and I'm not sure how to turn off standby. I tried the "wake-up from standby" button in the disk utility, but that did not work. I'm very new to linux so I'm not sure if there is an update or something that I have to install for it to work but I am very confused.

---

### Post by MAFoElffen on 2023-07-20
Hmmm. Thinking about this... Any read should wake it up.

If you do something like this
```

sudo dd if=[COLOR=#ff0000]/dev/sdx1[/COLOR] bs=1k count=1 of=/dev/zero

```
Substituting the red for how to ID your device...

That would try to read a byte from the pointed to partition. A "read" is non-destructive and safe. Just doing that should wake it up.

For mine, since mine is a Server, is set not to go to sleep, nor to suspend.

---

### Post by TheFu on 2023-07-21
I'd provide this warning.  A 4TB HDD as the place with the OS will add wear and tear to the disk.  I learned this the hard way with 3 4TB disks failing when they were used for the OS in my media center PC.  The failed disks were different models from different vendors.  In the end, I deployed an SSD for the OS and kept the media on other HDD storage.

Not all disks allow turning off standby, but **hdparm** is the tool for that. Run the command with the required options for your disk at every boot.  There are multiple ways to accomplish this. I'd just use @REBOOT in the system crontab myself, but you could do something with systemd unit files, if you prefer that.  The manpage for hdparm explains the different options.

---

### Post by wackanoodle on 2023-07-21
Thank you for the warning. I actually have an 250gb ssd running the OS,  and I wanted to hdd to have the contents of the NAS and the media  server. I tried running hdparm, but I'm not sure that I did it right. To  be perfectly honest, I'm not even sure I installed it correctly

---

### Post by wackanoodle on 2023-07-21
> **MAFoElffen said:**
> Hmmm. Thinking about this... Any read should wake it up.

If you do something like this
```

sudo dd if=[COLOR=#ff0000]/dev/sdx1[/COLOR] bs=1k count=1 of=/dev/zero

```
Substituting the red for how to ID your device...

That would try to read a byte from the pointed to partition. A "read" is non-destructive and safe. Just doing that should wake it up.

For mine, since mine is a Server, is set not to go to sleep, nor to suspend.


Thank you for your help. I tried running the code, but it didn't seem to work. I got the failure message, "dd: failed to open '/dev/sdx1': No such file or directory" 
Perhaps it has something to do with the fact that I have an ssd running the OS, and the hdd is sort of just sitting there lol

---

### Post by TheFu on 2023-07-21
> **wackanoodle said:**
> Thank you for the warning. I actually have an 250gb ssd running the OS,  and I wanted to hdd to have the contents of the NAS and the media  server. I tried running hdparm, but I'm not sure that I did it right. To  be perfectly honest, I'm not even sure I installed it correctly

What do you think someone else might need to know to help answer your questions?  Post that information. That would be where I started.

---

### Post by wackanoodle on 2023-07-21
> **TheFu said:**
> What do you think someone else might need to know to help answer your questions?  Post that information. That would be where I started.

Well, I'm not super sure what information would be helpful. I guess to start, it's comprised of a few older pc parts. I have a Ryzen 5 4600G, 1060 6gb, A520 mobo, 16g ddr4 3200 mhz ram, a 250gb ssd, and a 4 tb hdd. I haven't done a lot on the server just yet, but I started a modded minecraft server although it has been offline for a few weeks now. I also started using jellyfin. I really want to attach jellyfin to the hdd but I have no idea how to do that. I also tried to format the hdd, but it didn't really seem to do anything as I am still unable to wake the drive up

---

### Post by TheFu on 2023-07-21
For starters, you said you didn't know if you installed it correctly.  Maybe post the exact command used to install it along with any output?

Next you said you didn't know if you ran it correctly.  Maybe post the exact command used to run it along with any output?

If the command is supposed to act on the disk or a partition, we'd need to see a list of disks and/or partitions inside the system.

If the HDD isn't partitioned and doesn't have a file system and that file system isn't mounted, you aren't anywhere near ready to worry about trying to keep the drive from sleeping.  That's about step 20 in the list.  There are lots of different tools that can be used to do the stuff in this paragraph.  I'd use **gparted** myself for the first 3. 

Mounting a file system is handled through the /etc/fstab file.  You can google for 10,000 how-tos on that.  They are dependent on many things that are specific to your system.  YOU are expected to know which things are system-specific.  For example, /dev/sdx1 needs to be corrected to match what your system actually uses.  

MAFoElffen posted with a fictitious value so we'd see errors and know you didn't understand that aspect.  If it was another version of that or other commands, it could have been a really, really, bad day.  Unix systems expect the admin to know certain things.  Blindly copy/pasting commands is a good way to harm the system, if not the hardware.  Always - ALWAYS - read up on each command, each option BEFORE you run them.  Over time, you'll learn more and more, so you won't need to look up everything each time, but for now, consider this an opportunity to learn something useful for running your system.

It is ok to ask for help too. I'd like to see a genuine attempt at solving the problem yourself. Nothing teaches better/faster than struggle and correction.  So, when asking for help, I want to see the exact commands and **relevant** output.  If there are 5 lines of output, great, show it all.  If there are 50 lines, we don't need to see all of them, just the relevant lines which are usually the first few and some around the error.

Almost all command line (aka shell or CLI) programs require options to work.

---

### Post by MAFoElffen on 2023-07-22
I said to "substitute} what your parked disk is for that parameter... "[COLOR=#ff0000]/dev/sdX1[/COLOR]" was just a example of what *might* be.

Please post the output of this within CODE Tags
```

lsblk -e7 -o name,label,size,fstype,mountpoint

```
The indicate which is your target drive.

---

### Post by #&amp;thj^% on 2023-07-22
> **MAFoElffen said:**
> I said to "substitute} what your parked disk is for that parameter... "[COLOR=#ff0000]/dev/sdX1[/COLOR]" was just a example of what *might* be.

Please post the output of this within CODE Tags
```

lsblk -e7 -o name, label, size,fstype,mountpoint

```
The indicate which is your target drive.

```
lsblk -e7 -o name, label, size,fstype,mountpoint
lsblk: unknown column: name,

```
Or this?
```
lsblk -e7 -o name,label,size,fstype,mountpoint

```

---

### Post by MAFoElffen on 2023-07-22
LOL. The later. (Edited) Just woke up. Got your PM. Thanks.

---

