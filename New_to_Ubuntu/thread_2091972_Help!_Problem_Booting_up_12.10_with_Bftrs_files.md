---
title: "Help! Problem Booting up 12.10 with Bftrs files"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by karpizl on 2012-12-06
Hello guys, I am really new to ubuntu 12.10 and this is my first post. I have a problem whenever i start up my computer. I upgraded to 12.1 recently and this problem has started happening ever since my first unexpected shutdown. When i start up it takes a little longer than usual and then goes to a black screen with the words in the top left, "searching for Bftrs files". Before the problem, every once and awhile my computer would boot right to the command line. I never knew how to get back to the gui from there so i would just restart, but now it does it all the time. I keep having to restart over and over until i get lucky and sign in. Then i keep the computer on for extended periods of time. Could you guys help with the bftrs files problem and tell me how to get from signing in in the command line back to the gui. Thanks and sorry for not using the right terminology or if this is a very basic problem.

---

### Post by karpizl on 2012-12-06
Also in case anyone needs it, my system information is as follows;

#29-Ubuntu SMP Fri Oct 19 10:26 :51 UTC 2012  all x86_64 GNU/Linux

 memory 7.7gb, Intel core i7-3720QM@2.60GHz x 8 Intel ivybridge mobile. 

I don't know if this information provides any help.

---

### Post by levlaz on 2012-12-06
Since you said you upgraded to 12.10 I am assuming that you used 12.04 before and it worked fine. If this is the case, perhaps it would be easiest to simply reinstall 12.10 from scratch. 

I am not sure what the btfr files are, but typically when it dumps you into the command line instead of the login screen there is some sort of problem with the video settings. 

A command that usually works when I am dumped into the command line interface is 

```
startx
```

This command starts the x-server which is the process that controls the GUI. Try running that command when you are dumped into the command line and see what happens. 

If there is some long error or your computer starts acting weird then I think the easiest way to fix all of this is to simply reinstall 12.10 from scratch.

---

### Post by oldfred on 2012-12-06
Was there some specific reason to use Btrfs?

       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

    Best not to shutdown without trying to close things normally. Remember the elephants.
       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

It used to be startx and that may work, but now it depends on what you use.
       startx
or 
now preferred
sudo service gdm start
sudo /etc/init.d/lightdm restart
sudo start gdm
or: gdm, lightdm, xdm, etc 

With ext4 you often need to run fsck after abnormal shutdowns. With btrfs I think you have to download another package to include those utilites. The system may be trying to run the file checks and without the btrfs utitily having issues. 

From synaptic:
btrfs-tools

> This package contains utilities (mkfs, fsck, btrfsctl) used to work with btrfs
and an utility (btrfs-convert) to make a btrfs filesystem from an ext3.

WARNING: Btrfs is under heavy development, and is not suitable for any uses
other than benchmarking and review.

    

---

### Post by HeroOfCanton on 2012-12-06
Second on "Why btrfs?"

Regardless, you may find information about the cause by running "dmesg" from the command line or viewing the contents of /var/log/boot.log.

Also, have you tried Alt-F7 when it boots you to a command line? If the GUI is active it should show up there. If not try oldfred's recommendations to start it manually and see what happens.

---

### Post by karpizl on 2012-12-16
Thank You guys for the help, the R S E I U B really helped and now it tends not to have the error any more. I don't really know why the problem was caused but it seems to be working fine now. Thank you so much for the help.

---

