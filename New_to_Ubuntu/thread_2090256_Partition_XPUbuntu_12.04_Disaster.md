---
title: "Partition XP/Ubuntu 12.04 Disaster"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by Gonda on 2012-12-01
Hi,

while copying info from one external hard drive to another some files were accidentally deleted from xp. Now xp gives this error: <windows root>\system32\hal.dll and won't start.

Before I attempt to start any recovery in xp from the cd I just want to know what I need to be careful of and what could affect my Ubuntu system. I did google this and there are so many different options that I am not sure what to do. 

The thing that seems to be the most prominent is the loss of grub. Is this correct? 

Does anyone have a workable solution that I can follow to avoid messing up my Ubuntu partition? 

I know this is not really an Ubuntu issue, just hoping someone may know how I can repair XP without messing up Ubuntu - arrgghhh! nightmare. I am desperately hoping to find a fix without reinstalling or redoing my entire hard drive - so much info on both partitions. Help!! :confused:

I am also not sure how many other xp files may have been deleted in the process. 

I am not very good with this type of stuff and am trembling in my boots.

---

### Post by Bartender on 2012-12-01
If you have a genuine XP install CD, you could try to [Repair the Installation]("http://michaelstevenstech.com/XPrepairinstall.htm").  I'm not totally familiar with that process, but it is possible.

The Repair process should ignore the Linux-formatted partitions (if we're talking about a traditional dual-boot, not wubi).  If you can get XP to repair itself, then you should be good to go.

If you have to reinstall XP via a genuine XP disc or a recovery disc, then yes, GRUB will be broken because the Windows disc will re-write the Windows MBR at the very front of the HDD.  Part of GRUB will still be there in the Ubuntu partition, but the part of GRUB that sends the computer to the second part of GRUB will be gone from the MBR.  

Again, the Linux partitions *should* be ignored by either a genuine XP disc or a recovery disc, so the Linux partitions *should* remain untouched.  

So, after reinstalling XP, the Linux partitions won't appear as a choice at boot-up even if they're still there.

This is not a big deal if you prepare by making a [BootRepair bootable CD.]("https://help.ubuntu.com/community/Boot-Repair")  The Boot-Repair disc should fix GRUB so that it worked like before.  I've only used a Boot-Repair CD once or twice but it worked for me with zero hassles.

---

### Post by oldfred on 2012-12-01
Usually the hal.dll missing error is not a missing file but a boot.ini that is not configured correctly. If you attempted to move Windows from one partition to another you have to update boot.ini as that is hard coded to a partition. But the PBR - partition boot sector also has to be repaired with fixBoot as that has the start & size of the NTFS partition in it.

       Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

---

### Post by Gonda on 2012-12-02
Hi,

Thanks for the info, please can I have a little more advise about making a reboot cd?

I looked at the link [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Which option do i use? 1 or 2?

I also found this link [http://news.softpedia.com/news/Download-Ubuntu-Secure-Remix-12-04-272858.shtml](http://news.softpedia.com/news/Download-Ubuntu-Secure-Remix-12-04-272858.shtml)     - is it the same thing? 

The reason for asking about the link above is because it has a special note that it is for dual boot systems. If this is not going to work for me which of the two options from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) this link should I use? 

I am not very good with this - so just need to make sure I'm getting the correct one.  I don't really know what I'm doing - but i'm ok with following instructions :{

My pc:

 Nvidia Ge Force 7300GT
32 Bit res
Intel (R) Core TM 2 cpu
6300@1.86GHz
1.86 GHz, 2.00 GB RAM

---

### Post by Gonda on 2012-12-02
Hi,

I have found my deleted files (in trash) - should have looked there first :{ sorry. My xp works fine again. 

Before I close this thread - Is it a good idea to make a boot up cd anyway? Which download is the best one for me? 

Thank you for your help.

---

### Post by Bartender on 2012-12-02
Hey, no sweat, just glad to hear you fixed it on your own!  That was some original thinking, to go hunting in the dumpster, then get the file back in the right folder.

I'm not absolutely sure about which Boot-Repair you should download and convert to bootable disc.

If in doubt, the UbuntuSecureRemix disc seems like the one to try, doesn't it?  It'll be a much bigger d/l than just Boot-Repair.  

It probably doesn't matter, but I'd probably d/l it from [Sourceforge]("http://sourceforge.net/projects/ubuntu-secured/files/") rather than Softpedia.

---

### Post by YannBuntu on 2012-12-02
Hello

At the moment, Boot-Repair-Disk is based on Debian stable (quite old) so better using Ubuntu-Secure-Remix. See [http://sourceforge.net/p/boot-repair](http://sourceforge.net/p/boot-repair) for more details.

I checked the Softpedia links: they redirect to Sourceforge, so no problem.

---

