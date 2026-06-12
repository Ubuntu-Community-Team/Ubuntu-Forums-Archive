---
title: "Drive Wipe"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by 2-e on 2012-04-03
I am looking for a drive wipe tool on a live cd that won't take days on a 600gb drive. Boot and nuke won't boot on my hp pavilion g7. "Wipe" is taking forever. I am trying to ensure that a rootkit on now deleted Windows is completely gone. I am currently only using Lubuntu but will soon have to reinstall the Windows partition. Is a complete wipe even necessary? Any help would be much appreciated.

---

### Post by Carl7145 on 2012-04-04
I'm gonna say that if your re installing windows then yes you need to wipe that partition. If your in Ubuntu then just use disk utility. Its much easier than a other software. If you want use this [http://www.killdisk.com/](http://www.killdisk.com/)

That should help

If you have any furthur questions email me at 

[email]Carl.supportfortech@live.com[/email]

Seya 

{Carl}

---

### Post by sudodus on 2012-04-04
You can use ***dd***. Warning! This operation cannot be reversed, so check carefully that you are wiping the drive you want to wipe and nothing else! dd will write zeros onto the whole drive, so you have to make a new partition table before installing anything.

Boot a live session from your Lubuntu CD or USB drive and from there start two terminal windows. This is how you wipe the whole first drive (sd[COLOR=Red]a[/COLOR]) from the first window
```
sudo dd if=/dev/zero of=/dev/sd[COLOR=Red]a[/COLOR] bs=4096
```It works silently. This is how you can check the progress from the second window
```
ps -A | grep " dd$"
``` gives you the process id of dd. Example:
```
  [COLOR=Red]829[/COLOR] ?        00:00:00 dd
```Then you can make it write a 3-line status report with the process id you found.
```
kill -USR1 [COLOR=Red]829[/COLOR]
```Read ```
man dd
``` for more details

---

### Post by Alphamonkey on 2012-04-04
Another option which I have used before is the shred command. [http://linux.die.net/man/1/shred](http://linux.die.net/man/1/shred) just type sudo shred {options} {file} (in your case drive /dev/sda<drive-number>). You might have to download a LiveCD in order to do this if you want to do it on the drive you are currently using. As far as liveCDs go my preference for this sort of thing is knoppix, but I am pretty sure most will work.

---

### Post by oklokl on 2012-04-04
[http://www.jetico.com/wiping-bcwipe/](http://www.jetico.com/wiping-bcwipe/)


./configure
make
sudo make install


sudo bcwipe -F -mz -v /

---

### Post by Mark Phelps on 2012-04-04
There are several MS Windows partitioning tools that are available for free -- but I don't know if the free versions will do partition "wiping":
1) EASEUS Partition Master
2) Partition Wizard
3) Minitool Disk Wizard

---

### Post by Cheesemill on 2012-04-04
+1 for using dd.

Just boot from a Ubuntu Live CD, open a terminal and do:
```
sudo dd bs=1MB if=/dev/zero of=/dev/sda
```Making sure that you replace /dev/sda with the correct drive.
If you are unsure which drive you need to wipe then:
```
sudo fdisk -l
```will usually give you the information that you need.

[SIZE=2][COLOR=Red]***WARNING***[/COLOR][/SIZE] - The above command will completely delete all data on the specified drive. Use at your own risk !!!

It will be impossible to recover any data from the drive once that this command has completed, it will be factory fresh :)

---

### Post by 2-e on 2012-04-04
Thanks everyone for your suggestions. I am trying shred right now but it sounds like dd may be more thorough. What does the " bs=" refer to?

---

### Post by RJARRRPCGP on 2012-04-05
> **2-e said:**
> Thanks everyone for your suggestions. I am trying shred right now but it sounds like dd may be more thorough. What does the " bs=" refer to?

I believe that's the block size. bs=4096 I believe wipes in 4 KB chunks.

---

### Post by sudodus on 2012-04-05
> **2-e said:**
> Thanks everyone for your suggestions. I am trying shred right now but it sounds like dd may be more thorough. What does the " bs=" refer to?
***dd*** 'only' overwrites once. ***shred*** can overwrite several times depending on the setting. Both commands can overwrite devices (drives and partitions). The most thorough overwrite is that of the whole drive. If you want more details, read ```
man dd
``` and ```
info shred
```
RJARRRPCGP already answered the question about ***bs***.

---

### Post by Cheesemill on 2012-04-05
> **sudodus said:**
> ***dd*** 'only' overwrites once. ***shred*** can overwrite several times depending on the setting.
Overwriting data more than once is pointless, a simple one pass overwrite with 0's is all you need to ensure that your data cannot be recovered.

---

### Post by Paqman on 2012-04-05
> **2-e said:**
> I am trying to ensure that a rootkit on now deleted Windows is completely gone.
<snip>
Is a complete wipe even necessary?

No. Simply reformatting the partition when you reinstall the OS will do. However, I understand why you might want to err on the side of caution when dealing with a rootkit.

As mentioned above, a single pass of zeros is the fastest option and will completely destroy all data on the partition. You can use one of the tools in the package [secure-delete]("apt:secure-delete"), called sfill. It fills all free space, so make sure you delete all the data first:
```
sudo sfill -l -l -v -z /mount/point
```

(The switches there just specify a single pass with zeros)

Dd is ok for doing this too, just make very sure you pick the right target, as it will destroy data if pointed at the wrong partition. I've recommended sfill purely because it avoids this risk, both tools will do the same job at the same speed.

---

### Post by 2-e on 2012-04-06
Thank you all for your help. I wound up using shred for the windows partition and dd for the entire drive.

---

### Post by Dreamer Fithp Apprentice on 2012-04-06
Overwriting more that once is totally pointless overkill for your application. Data that can't be read by the hard drive itself can't possibly affect your system no matter how clever the malware writer.

For applications of the "we must keep the nuclear ICBM targeting and launch authorization codes out of the hands of Prof. Moriarty" sort no software based wiping tools are reliable on drives using either SMART remapping or load leveling which probably includes most drives currently being manufactured. These hardware "features" also make applications that depend on knowledge of the physical location of data, such as defragmenters and applications that try to put files more frequently used on a faster part of the disk and files frequently used in sequence in locations that facilitate faster reading of them in sequence, etc. less effective or totally ineffective.  Drive manufacturers have in some cases and to some extent compensated for this by providing utilities specific for their own hardware but they do not duplicate the range of functions and flexibility that are available from purely software based utilities working with traditional hard drives that do not hide information from the operating system. Which is part of why I think SMART is rather dumb.

---

