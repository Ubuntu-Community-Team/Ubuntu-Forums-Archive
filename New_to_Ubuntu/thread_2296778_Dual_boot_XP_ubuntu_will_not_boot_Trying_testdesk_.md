---
title: "Dual boot XP ubuntu will not boot Trying testdesk and boot-repair"
date: 2015-09-28
forum: New to Ubuntu
---

### Post by Yankee26 on 2015-09-28
Hi:

Boot-repair report: [http://paste2.org/dyB9FGHB](http://paste2.org/dyB9FGHB)

I ruined my dual boot when trying to upgrade to Python3. I am using asus AMD 64 bit computer. I used testdisk to try repairing partitions and computer did not boot up.  I then tried boot-repair and made the pastebin report for asking for help.

Thanks for your help, Bob.

---

### Post by oldfred on 2015-09-28
I do not know RAID and it looks like sda & sdb are some SIL RAID?
But sdc is not RAID?

But both Windows & Ubuntu show sdc as first drive, or that it should be seen as sda?
Since Ubuntu uses UUID it still should boot, but drive is now sdc in BIOS.

Do not use any auto fix in Boot-Repair.
But use advanced mode and choose Ubuntu install and re-install grub to drive that is shown as sdc.

---

### Post by Yankee26 on 2015-09-29
Hi Oldfred:

I tried your suggestions advanced mode Boot-Repair-Disk and it got hung up.  It had a sudo apt-get install statement.  I ran the sudo statement in a Terminal and it almost completely ran.  It wants "libuniversal-require-perl" installed.  The synaptic package manager did not have it and I downloaded the "libuniversal-require-perl" but could not install it or get synaptic to see it.  I searched the Internet but no help!  I tried to put the down loaded "libuniversal-require-perl" in a /usr/bin folder but the boot repair disk locks users out.

I will keep looking and thanks again for your help,
Bob

---

### Post by oldfred on 2015-09-29
I show that library in my synaptic with 14.04, but not installed.
I have run Bpoot-Repair but not advanced install options. But it should install any needed files/libraries when loaded?

---

### Post by Yankee26 on 2015-09-30
Hi:

I tried Oldfred's suggestion but it produces an error.  I attached a file of my disk-repair options I ran and the results.  It has the same error I had earlier about libuniversal-require-perl is missing and I can not load it.  Since I received a pastebin report last week I wonder if I selected too many options this time.  Also I tried to install GRUB in sdc.  I did not try to install MBR.  Should I try to install MBR and if that works install boot in Ubuntu partitions?

I also put the Boot-Repair-Options.txt file in dropbox.org.

Thanks again for your help,
Bob

---

### Post by oldfred on 2015-09-30
You cannot run synaptic from installer, you would have to chroot into your install.

       Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
      
 o chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

    
You have to mount your root & several folders inside it. Then CHange ROOT to be in your install but using kernel from live installer.
[https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD

---

### Post by Yankee26 on 2015-10-02
Hi Oldfred:

I read and reread your instructions.  I remembered your previous suggestion about installing Ubuntu.  I was in Live Ubuntu 14.04.3 and after starting it it had installed Ubuntu 14.04.3.  I ran it and it erased Ubuntu and swab partitions and installed 14.04.3 including Grub2.  Grub has Ubuntu, recovery, mem+ and XP.  It boots into Ubuntu OK and I can access Ubuntu Advance.  I briefly tried XP but it had a black screen for 5-10 minutes so I rebooted into Ubuntu.

I have some minor problems with Ubuntu.  It over wrote by device name so it now has bob@bob-System-Product-Name:/, even though it showed my system name when installing Ubuntu.  It also arbitrarily changed my password to an unknown one for me so now I can not use sudo.  I now will work on these problems and will open a new thread if I need help.

This thread can now be closed but I do see how to close this thread.

Thanks very much for your patience and help.  I very much appreciate it.

Bob

---

### Post by oldfred on 2015-10-02
If you did a full reinstall of Ubuntu, It asks for both the user name, system name and you have to type in password twice.

You can close thread using thread tools above first post.

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

