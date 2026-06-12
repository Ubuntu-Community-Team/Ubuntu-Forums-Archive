---
title: "How To create a Diskless Swap System."
date: 2008-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Kernel_Krunch on 2008-10-12
[FONT="Microsoft Sans Serif"][SIZE="4"]This is a guide for setting up your computer with a fast swap system using usb memory sticks.  A detailed study of the theories behind this setup can be found [[COLOR="blue"]_here_[/COLOR]]("http://cs.kaist.ac.kr/research/technical/Archive/CS-TR-2006-250.pdf").  While this How-To does not include the CFLRU replacement algorithm, it does show the performance benefits of using NAND flash memory and will hopefully increase interest and speed development. [/SIZE]

It is assumed you have completed [[COLOR="blue"]_part 1_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=882215").

1.) Create a persistent device node for each swap device using udev.  This will allow the devices to move around but won't effect your swap system.  ```
sudo gedit /etc/udev/rules.d/15-swap.rules
``` 
Then add the following lines but using your serial numbers:
```
SUBSYSTEM=="block", ATTRS{serial}=="46d2cef7d5a461", NAME="%k", SYMLINK+="SwpNodA"
SUBSYSTEM=="block", ATTRS{serial}=="SNDKA96735075A203908", NAME="%k", SYMLINK+="SwpNodB"
SUBSYSTEM=="block", ATTRS{serial}=="SNDKA940252CCCC05806", NAME="%k", SYMLINK+="SwpNodC"
SUBSYSTEM=="block", ATTRS{serial}=="SNDKA96735037AA03903", NAME="%k", SYMLINK+="SwpNodD"
```

2.) Update fstab:
```
sudo gedit /etc/fstab
```
You should see a line something like this:
> UUID=921f422a-5816-4040-97df-850e569c4687 none swap sw 0 0
it is your current swap drive, comment it out with a '#' at the front.  Underneath place the following lines:
> /dev/SwpNodA      none            swap    sw,pri=0              0       0
/dev/SwpNodB      none            swap    sw,pri=0              0       0
/dev/SwpNodC      none            swap    sw,pri=0              0       0
/dev/SwpNodD      none            swap    sw,pri=0              0       0

3.) Edit sysfs:
```
sudo gedit /etc/init.d/bootmisc.sh
```
find the lines that read:
> 	# Remove bootclean's flag files.
	# Don't run bootclean again after this!
and add these lines
```
[COLOR="DarkRed"]for[/COLOR] [COLOR="DeepSkyBlue"]x[/COLOR] [COLOR="DarkRed"]in[/COLOR] A B C D
[COLOR="DarkRed"]do[/COLOR]
[COLOR="DeepSkyBlue"]Node[/COLOR]=[COLOR="DarkOrchid"]`udevinfo --query=name --name=SwpNod[COLOR="DeepSkyBlue"]$x[/COLOR] | cut -c -3`[/COLOR]
[COLOR="DarkRed"]echo[/COLOR] -n 1024 [COLOR="Red"]|[/COLOR][COLOR="DarkRed"] dd[/COLOR] ibs=4096 conv=fdatasync,sync of=[COLOR="Red"]/[/COLOR]sys[COLOR="Red"]/[/COLOR]block[COLOR="Red"]/[/COLOR][COLOR="DeepSkyBlue"]$Node[/COLOR][COLOR="Red"]/[/COLOR]device[COLOR="Red"]/[/COLOR]max_sectors 2>[COLOR="Red"]/[/COLOR]dev[COLOR="Red"]/[/COLOR]null
blockdev --setra 0 [COLOR="Red"]/[/COLOR]dev[COLOR="Red"]/[/COLOR][COLOR="DeepSkyBlue"]$Node[/COLOR]
[COLOR="DarkRed"]echo[/COLOR] deadline > [COLOR="Red"]/[/COLOR]sys[COLOR="Red"]/[/COLOR]block[COLOR="Red"]/[/COLOR][COLOR="DeepSkyBlue"]$Node[/COLOR][COLOR="Red"]/[/COLOR]queue[COLOR="Red"]/[/COLOR]scheduler
[COLOR="DarkRed"]done[/COLOR]
```

4.) As of kernel ~2.6.20 the Virtual Memory settings might need to be modified.  Check your values with ```
sudo sysctl -A | grep vm
``` Add the following to /etc/sysctl.conf if the values don't match these
> vm.dirty_writeback_centisecs=1000
vm.dirty_background_ratio=3
vm.dirty_ratio=40


5.) Reboot and check your swap system with ```
swapon -s
``` > Filename          Type               Size          Used          Priority
/dev/sde1          partition 503400 69252     0
/dev/sdf1          partition 976884 69024     0
/dev/sdb1          partition 497972 69140     0
/dev/sdd1          partition 497972 69008     0


[CENTER][COLOR="Blue"]**Comments:**[/COLOR]

**Udev**[/CENTER]
When the kernel starts it talks to all the devices and gathers information to build sysfs with.  Udev is a front end for us to use as a way of managing this information, without needing to know a lot about the kernel.  Here we identify our device by serial number and make a pseudo device node with a name "SwpNod".  The pseudo node is just a system link pointing to the kernel device, %k.

[CENTER]**fstab**[/CENTER]
Here our node is referenced for mounting purposes, it has the options of being a swap partition and has equal priority with the other nodes.  When the priorities are equal, the kernel will use them in sequence, first to last then back to the first and so on until all the data written.  In this situation, the work is spread across the devices evenly which multiplies read/write speeds of page clusters by the number of devices (i.e. x4).

[CENTER]**Boot Script**[/CENTER]
This function sets 3 kernel values for each device.  The first tells the kernel to transfer data to the device in bulk packages of up to 1024 sectors(usually 512b).  The second turns off device read ahead, which is a technique used by disk devices to help eliminate data access lag but is useless for swap devices in the long run due to the natural tendency of swap data to become fragmented over time (See the study for more info).  The third value tells the kernel to make read operations more important then write operations.  This is very true for a swap system since data being written is "dormant" and data being read is "critical".

[CENTER]**Sysctl**[/CENTER]
The default writeback time was 500 centisecs but is increased to 1000 to cut down on cpu operations and make better use of the max_sector value.  The other options should never have changed.  While "tweaking" these values may increase performance for one application in the short run, it will effect other applications including the desktop application in the long run.  Basically, the linux swap system is a simple system that "just works" and while the developers allow for configuration changes, it would be better to add to the code. 

[CENTER][COLOR="Blue"]**End Notes:**[/COLOR][/CENTER]

a) Blocks will "burn out" based on use over time, a check can be made and a resize of the partition can be done.  In most cases, an idle desktop with no background processes will not require a swap file and the `swapoff` command can safely be used.  `mkswap -c /dev/xxx1` will remake the swap file and check for errors.  For an exhaustive check, format the drive to ext2 and check with `mke2fs -c -c /dev/xxx1`.  I thought that over years of heavy use, the resulting sector loss was ~15MB of drive space off each device but this may be partition mechanics, device and partition reserve space since the reported size has not changed...  Keep an eye on the value and knock 100MB off the partition if paranoid.

b) This setup has been stress tested with large flash video files, World of Warcraft, Firefox with large cache, Mplayer playing DVD, all running simultaneously. It was also used during development of [[COLOR="blue"]_this_[/COLOR]]("http://www.linuxforums.org/forum/linux-programming-scripting/116810-automated-lfs-bash.html") script.  It should be noted that a number of bugs appeared during early development of that script which produced some extremely abnormal operating environments and I smoked a drive... the final version ran without issue.  The script is not intended for use, it is ***_linked only to document testing conditions_***. 

c) There is talk about turning swapping off since the cost of system RAM has decreased dramatically.  Wrong.  Swapping not only frees up system RAM, it splits the page lookup table into a table of "active" pages and a table of "non-active" pages.  This helps reduce the workload on a cpu by eliminating look-ups on dormant pages.  The idea ***should*** be taken further with a small area of system RAM (possibly the write cache) as a 'Level 1' swap area, NAND memory as 'Level 2' and finally a disk as 'Level 3'.  Here pages we normally would write to disk are kept in RAM(Level 1) "just in case", then expire to Level 2 and finally Level 3.  Things like access frequency, read or write access and possible access would determine what level(and table) the pages should reside. The idea is to have important pages circle in RAM, fall to a fast access Level 2 when deemed non-important and then finally hit a disk that is organised for fast read.  Memory Management kernel functions should be a candidate for [[COLOR="blue"]_co-processing_[/COLOR]]("http://en.wikipedia.org/wiki/Coprocessor").

[CENTER][COLOR="Blue"]**Further Reading:**[/COLOR][/CENTER]

```
man fstab; man udev; man swapon
```
[[COLOR="blue"][CENTER]_Sysctl VM_[/COLOR]]("http://kernel.org/doc/Documentation/sysctl/vm.txt")[/CENTER]

[/FONT]

---

