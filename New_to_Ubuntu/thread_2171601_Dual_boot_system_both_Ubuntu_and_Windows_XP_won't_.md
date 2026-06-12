---
title: "Dual boot system: both Ubuntu and Windows XP won't boot"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by pauldc2 on 2013-08-31
Needless to say, I'm an absolute beginner as far as Linux is concerned. I've got a dual boot laptop (nothing fancy, a lowly compaq presario with a 300gb HD). When I bought it, I asked the guy in the shop to install XP instead of Vista and leave a 200gb partition free so that I could install Linux at a later stage. I ran Win for some time and then eventually decided to install Ubuntu 10.04 from a CD I burned a while back. Installation went without a glitch and I was very pleased with the new Os' performance compared to Win, which I had decided to keep anyway as there are a few apps I need to run which are Win-only. I then started to have issues with XP which would only boot after a couple of attempts: I'd choose the Win partition on grub and then the XP logo would appear for a while before the whole system rebooted all of a sudden, restarting from the pre-Bios screen. When it finally loaded up, it would then run just fine and sometimes it would boot up without any hiccups whatsoever so I just left it as it was also because Ubuntu worked brilliantly everytime. Everything seemed sort of fine up until a few days ago when neither of the systems would boot. Windows is locked on to that grub-logo-back to bios loop indefinitely while Ubuntu will display the following message: 1.340258 Kernel Panic not syncing; vfs: unable to mount roots fs on unkwnown block (0,0) ("Oh no, not that again!" I'm sure some of you'll say!) Anyway, I've scoured the net for info and as you all probably know already, it's one of most common error messages relating to kernel problems. I could have followed some of the advice already posted but because I've got a dual system running slightly older OSes, I just thought I might have to go about it in a different way. I'd appreciate any help you could give me. Many thanks in advance!

---

### Post by oldfred on 2013-08-31
Welcome to the forums.

Still 10.04? Desktop is not supported anymore.

Error could be hard drive? Windows issues could have been a warning. But often with Windows a chkdsk fixes issues. If you had from Ubuntu copied files or done something to XP that often causes issues. Or system crash. But chkdsk usually fixes those. You have to run chkdsk from your XP disk in the repair consolue.

Same with Linux. It may not correctly read data if drive is failing or it just may need fsck.

Best to use a newer Linux repairCD or live installer flash drive or DVD. New versions will not install to CD.

From liveCD you can use Disks or Disk utility (depends on version) and click on drive. It should show Smart Status. It can run lots of tests but all I know is passed is good and anything else is time to backup and get a new drive as it may not be reliable, if working.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your ext family partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

This requires Internet and the install has to have available repositories which now you do not. 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by pauldc2 on 2013-09-01
Thanks so much for your reply Oldfred. I'll try and do as you've suggested and get back to you with the results! Cheers.

---

