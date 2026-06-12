---
title: "Another 11.04 to 11.10 question"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by vasa1 on 2011-10-09
There's an image posted over here ([http://ubuntuforums.org/showpost.php?p=11323908&postcount=2](http://ubuntuforums.org/showpost.php?p=11323908&postcount=2)).

Can someone explain what that image would look like if the computer already has two operating systems, Windows 7 and 11.04?

Assuming there are no space constraints in the extended partition that holds 11.04, would it be possible to have Win 7, 11.04 and 11.10 without any advanced knowledge? This will be my first time so please be gentle!

I plan to download the 11.10 .iso via torrent after it's been released and put it on a "live USB" using UnetBootin. (I know how to do that.)

(Also take for granted that I'll back up my data.)

---

### Post by garvinrick4 on 2011-10-09
You can have as many logical partitions as you want inside the extended partition.
Double or triple or quad keep going, all you need to think of is which install is in 
control of grub, they each have their own grub config and use theirs when installed
in mbr (master boot record)(which is simple to do). Partitioning  and grub2 (grub-pc) are two subjects worth
studying.
I am going to just give you some links to bookmark and keep around to study.
Some are written by a user drs305 in his signature are a good handfull of turorials
he took the time to write for us, bookmark them and read also when time permits.
I have found the tutorials written by certain Ubuntu users will be the quickest and 
fastest way to get where you want to go in Ubuntu linux along with these Forums.
[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 
[HowToPartition - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowtoPartition")
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
[Upgrade | Ubuntu]("http://www.ubuntu.com/download/ubuntu/upgrade")
[HOWTO: Grub Customizer - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")
[About Ubuntu | Ubuntu]("http://www.ubuntu.com/project/about-ubuntu")
### When you feel a bit lost or need any info just ask in these Forums.
Read the partitioning link so you understand the 3 parititons types, Primary, Extended and Logical. Then get back here
with requests on partitioning schemes to discuss.

---

### Post by raja.genupula on 2011-10-09
If you choose the first option then both Ubuntu 11.10 & 11.04 both are going to installed in a same partition.

If choose last option then you gonna have some possibility for selecting manual partition.

so these two are going to be best to do what you want(11.10,11.04.Windows 7).

First option not going to do any loss to your windows.


All the best

---

