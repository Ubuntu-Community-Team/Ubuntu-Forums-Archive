---
title: "Multiboot questions"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by SpaceCeph on 2012-05-13
Moin! 
I installed Ubuntu two weeks ago. I had some problems after the installation with my nvidia card but now everything works well. Now I wanna try kubuntu and perhaps 12.10. I wanna make a 'standard' installation with swap, root and home. 
Now my questions... Is it better to make a separate boot partition? And what's the easiests way to share my documents and media files in the three versions? I know I need three root partitions, three home partitions and one swap. But I don't know what's best with the boot partition. 
I don't wanna install windows, so my hd is open for everything. 
Cheers and thanks!! 

PS. Excuse me for my English...

---

### Post by wilee-nilee on 2012-05-13
> **SpaceCeph said:**
> Moin! 
I installed Ubuntu two weeks ago. I had some problems after the installation with my nvidia card but now everything works well. Now I wanna try kubuntu and perhaps 12.10. I wanna make a 'standard' installation with swap, root and home. 
Now my questions... Is it better to make a separate boot partition? And what's the easiests way to share my documents and media files in the three versions? I know I need three root partitions, three home partitions and one swap. But I don't know what's best with the boot partition. 
I don't wanna install windows, so my hd is open for everything. 
Cheers and thanks!! 

PS. Excuse me for my English...

You can just install the kubuntu-desktop on the ubuntu, and have a choice of either at login.

You only need one swap for multiple OS's

---

### Post by rai4shu2 on 2012-05-13
> **SpaceCeph said:**
> Moin! 
Now my questions... Is it better to make a separate boot partition? And what's the easiests way to share my documents and media files in the three versions? I know I need three root partitions, three home partitions and one swap. But I don't know what's best with the boot partition.

Boot partition is pretty optional nowadays. I wouldn't bother.

For sharing, I find that using an external drive or external computer on a LAN works out best (in case things go horribly wrong). I use proftpd for that, but YMMV.

If you want to boot into three systems, you only need three roots, one swap, and one home partition (assuming you login with different user names for each system).

---

### Post by oldfred on 2012-05-13
I like to keep /home separate or inside / with multiple installs and have data in a shared partition. All data does not change system configuration and is more easily shared. 

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by grahammechanical on 2012-05-13
I think that it makes sense to dual/triple boot into different Ubuntu flavours rather than just installing the desktop. Have a working Ubuntu that is a standby OS for when another OS that you are experimenting with goes belly up.

You might want to consider testing the ISO images of the next release of Ubuntu in all its flavours as it is developed.

[https://wiki.ubuntu.com/Testing/ISO]("https://wiki.ubuntu.com/Testing/ISO")

You most certainly should install on your main Ubuntu Grub Customizer

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

It will let you keep the Grub menu in some sort of order.

Some of us found this tutorial helpful when we shared in ISO testing 12.04 recently.

[https://wiki.ubuntu.com/U+1/iso-testing-qa]("https://wiki.ubuntu.com/U+1/iso-testing-qa")

And do not forget the Ubuntu+1 section of this forum if you do try out 12.10

Regards.

---

