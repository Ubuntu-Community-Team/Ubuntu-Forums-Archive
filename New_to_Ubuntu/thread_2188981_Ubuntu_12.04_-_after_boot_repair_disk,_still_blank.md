---
title: "Ubuntu 12.04 - after boot repair disk, still blank screen"
date: 2013-11-20
forum: New to Ubuntu
---

### Post by leow99 on 2013-11-20
After failure to boot, used boot repair disk:

Report: [http://paste.ubuntu.com/6447248](http://paste.ubuntu.com/6447248)

but even "ubuntu 12.04" does not flash up.

The above report is one of many attempts.  I suspect the kernel is damaged and used another thread's instructions to reinstall kernel: [http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

but the install failed at the last step.

Suggestions, please.  Next step is to re-install 12.04 or higher in separate partition.

---

### Post by phaenze on 2013-11-20
Please try the following and let me know if one or more worked:
[LIST=1]
[*]You didn't say whether you had or not, but try  booting an earlier kernel in grub. If grub doesn't show up, hold down the left shift key right after the BIOS screen.
[*]Try booting into the recovery console.
[*]Follow the directions from this [post]("http://ubuntuforums.org/showthread.php?t=1613132") and see if you have a graphics card problem. Follow the section titled: **How to temporarily set kernel boot options on an installed OS**.
[/LIST]

Peace,
Paul :cool:

---

### Post by leow99 on 2013-11-20
I had tried an earlier kernel, but it gave the same result - which leads me to believe that they are purged.  I have also booted in recovery. I do get indications of sector errors.  Do not think there are any graphics card problems.  When I Try Ubuntu from the CD, I have full access to the Internet in correct resolution.  When, I do a normal boot, nothing seems to happen for a long time, but when I Cntrl-alt-F1 into a terminal, I see that the system is still trying and hitting sector errors.

---

### Post by oldfred on 2013-11-20
Boot script looks normal.

But if you only have one system installed, grub menu will not show normally. It assumes you want to directly boot the one installed system. You should be able to hold shift key from BIOS until menu appears.

If you are getting sector errors that is a hard drive issue?
Does live installer boot ok? You may need to run fsck.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

Or it could just be a video issue. What video card/chip do you have?

---

