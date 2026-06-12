---
title: "Grub Error"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by troubledBeginner on 2012-11-24
Hello Sir,
I was previously using Win 7 home basic. Then sometime back i installed ubuntu 12.04 in my system.
As a consequence,the windows loader was automatically replaced by GNU Grub loader. To get back the Windows Loader, i tried some random software(foolishly) and ended up corrupting the Partitoning table.
Still,i was able to boot up Ubuntu. So,using TestDisk i tried to correct my Partitioning table. In the final step,Where you have to set the types for the partitions, **I set the wndows partition as the primary bootable whereas previously in my system the primary bootable was the linux partition.**  **This was my mistake.** 
Due to this I ended up in a Grub error.
On startup the system now shows:

Error:Unknown filesystem
Grub rescue>

I have tried various methods (reading from the forums) including Supergrub but none of it actually Worked. 
[B]If anyone could provide me with the command  line instructions for restoring my Grub loader(or any other help) , i will be heartily very grateful to you.
Please help me, I am in a very troubled state right now. [/B]:(
Thank You.

---

### Post by Bashing-om on 2012-11-25
troubledBeginner; Hi ! Welcome to the forum.

Regret the delay in responding; I do not use windows and my help is limited to directing you to links that will provide the instructions needed.
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
[https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode](https://help.ubuntu.com/community/Grub2#Command_Line_and_Rescue_Mode)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

and great docs all about grub2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Have a read, if any questions, by all means-> ask.
[INDENT][INDENT]Just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by troubledBeginner on 2012-11-26
Thank you for the links Sir,will try out and update you.

---

### Post by oldfred on 2012-11-26
Bashing-om's links give a lot of good info on grub, but some just want a gui tool to fix things. 
Boot-Repair often works and if it does not work gives a detailed report and system configuration so we suggest other solutions.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by troubledBeginner on 2012-11-26
Sir, GUI methods are is not working since the system is not reading from the internal CD-ROM drive even when i change the boot order settings from the BIOS environmet.
Thats why i asked for some command line help because i am completely zero at command line instructions.

---

### Post by YannBuntu on 2012-11-27
hello

> **troubledBeginner said:**
> So,using TestDisk i tried to correct my Partitioning table. In the final step,Where you have to set the types for the partitions, **I set the wndows partition as the primary bootable whereas previously in my system the primary bootable was the linux partition.**  **This was my mistake.** 
Due to this I ended up in a Grub error.

if i were you, i would:
1) use TestDisk to try reverting this error
2) if still not good, use TestDisk to recover lost documents, then reinstall everything

---

### Post by troubledBeginner on 2012-11-27
Sir, even i thought of using the TestDisk method..but i am in real deep trouble because my system is simply not booting up. I have burnt various CDs but none of them worked because my system is not reading from the disks.
All i get is:

Error:unknown filesystem
grub rescue>
 
Moreso, I couldn't find the ISO file of Testdisk over the internet. 
So,i have been unable to try that method.

---

### Post by troubledBeginner on 2012-11-27
On running the **ls** command in the grub rescue terminal i got the response:
 
(hd0) (hd0,msdos5) (hd0,msdos4) (hd0,msdos3) (hd0,msdos1)  

On running the **set** command i got:

prefix=(hd0,1)/root/grub
root=hd0,msdos3

Then again i ran the **unset prefix** command,after which on running the **set** command i got the result:

root=hdo,msdos3

I think i have messed up with my linux partition and there is no way i can save my data from getting lost.
Can i get some help sir?

---

### Post by oldfred on 2012-11-27
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Do you have a separate /boot?

To now see which partition may have grub.
 Try this with each partition from your ls above to see which has grub.

 Adjust drive, partition to your install:
ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?

Then you can use this to boot if separate /boot :
       
 Separate /boot on sda1, / on sda2:
grub> set prefix=(hd0,1)/grub
grub> insmod linux
grub> set root=(hd0,2)
grub> linux (hd0,1)/vmlinuz-2.6.32-30-generic root=/dev/sda2 ro
grub> initrd (hd0,1)/initrd.img-2.6.32-30-generic
grub> boot

---

### Post by troubledBeginner on 2012-11-27
Sir,i didn't get you. What do you mean by 'Do you have a separate /boot? '
All the partitions are listed as ms-dos partitions,so would any of those commands work?

---

### Post by oldfred on 2012-11-27
msdos is the partitioning. But some install Ubuntu with a separate /boot partition as one of the partitions. Others install with one / (root) partition with /boot as a folder inside the / partition. 

If you do not have a separate /boot you can use same commands but only use the same number for every entry. And the number you use has to be the one the ls then shows as grub. 

If you need more info see links to drs305 instructions. I just tried to give a quick list.

---

### Post by troubledBeginner on 2012-11-27
> **troubledBeginner said:**
> Sir,i didn't get you. What do you mean by 'Do you have a separate /boot? '
All the partitions are listed as ms-dos partitions,so would any of those commands work?

On running the ls commands i get an unknown file system error.

---

### Post by troubledBeginner on 2012-11-27
> **oldfred said:**
> msdos is the partitioning. But some install Ubuntu with a separate /boot partition as one of the partitions. Others install with one / (root) partition with /boot as a folder inside the / partition. 

If you do not have a separate /boot you can use same commands but only use the same number for every entry. And the number you use has to be the one the ls then shows as grub. 

If you need more info see links to drs305 instructions. I just tried to give a quick list.

I had one root partition with boot as a folder inside the root.
The commands are not helping me,i think i will have to format my hard drive,thats all! :cry:

---

### Post by Bashing-om on 2012-11-27
troubledBeginner;
We are here to help you. In order to help you you must heed instructions.
Have you read and comprehended drs305's guide, as oldfred directed ?
You will have to KNOW where grub is installed using that guide, we can not tell you.
Once you are able to advise us of your disk configuration then we can advise further.

Hope this helps you to help us <== BDQ

---

### Post by troubledBeginner on 2012-11-28
> **Bashing-om said:**
> troubledBeginner;
We are here to help you. In order to help you you must heed instructions.
Have you read and comprehended drs305's guide, as oldfred directed ?
You will have to KNOW where grub is installed using that guide, we can not tell you.
Once you are able to advise us of your disk configuration then we can advise further.

Hope this helps you to help us <== BDQ

Thanks for giving me hope,sir. Finally,i found my grub folder.
It is the (hd0,msdos4) partition that contains the boot folder inside which the grub folder is also present.
And i don't have separate boot and root folders,the boot folder is inside the root folder. 
I tried to restore my system using drs305's instructions but on executing the linux vmlinuz command i got the error invalid command.
What shall i do now?
Will uploading a snapshot of my screen help?

---

### Post by troubledBeginner on 2012-11-28
I am copying a part of drs305's page(the part where i failed...the system gave an invalid command message):

Load the Kernel & Initrd image.
linux /vmlinuz root=/dev/sdXY ro
Substitute the correct values for X,Y - Example: sda5
initrd /initrd.img
To load a specific kernel, especially an older kernel:
linux /boot/vmlinuz-<kernel version> root=/dev/sdXY ro
initrd /boot/initrd.img-<kernel version>
Example: linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5 ro
Example: initrd /boot/initrd-2.6.35-22-generic

I entered my kernel version number but didn't get any different results.

---

### Post by oldfred on 2012-11-28
Did you also change to sda4 which is your system partition as the example used sda5.

       Adjust drive, if sda4 is your partition:
ls (hd04)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,4)/boot # Do you see the kernel and initrd image files ?
ls (hd0,4)/boot/grub # Do you see lots of *.mod files and grub.cfg ?

 set prefix=(hd0,4)/boot/grub
set root=(hd0,4)
insmod normal
(If that fails try:  insmod (hd0,4)/boot/grub/normal.mod)
insmod (hd0,4)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda4 ro
initrd /initrd.img
boot
#after boot
sudo update-grub 

Above example does not use specific kernel but the links that Ubuntu has in root to the most current kernel. But if an update did not complete correctly the links may be broken. Then you have to use the specific kernel in /boot.

---

### Post by troubledBeginner on 2012-11-28
> **oldfred said:**
> Did you also change to sda4 which is your system partition as the example used sda5.

       Adjust drive, if sda4 is your partition:
ls (hd04)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,4)/boot # Do you see the kernel and initrd image files ?
ls (hd0,4)/boot/grub # Do you see lots of *.mod files and grub.cfg ?

 set prefix=(hd0,4)/boot/grub
set root=(hd0,4)
insmod normal
(If that fails try:  insmod (hd0,4)/boot/grub/normal.mod)
insmod (hd0,4)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda4 ro
initrd /initrd.img
boot
#after boot
sudo update-grub 

Above example does not use specific kernel but the links that Ubuntu has in root to the most current kernel. But if an update did not complete correctly the links may be broken. Then you have to use the specific kernel in /boot.

Yes i did change to sda**msdos4** which is my partition.
On executing this command:
**linux /vmlinuz root=/dev/sda[B]msdos4** ro[/B] i got the error
**unknown command 'linux/vmlinuz'**.

I did not go further after getting this error. What shall i do now?

---

### Post by oldfred on 2012-11-28
**linux /vmlinuz root=/dev/sda[B]msdos4** ro[/B] i got the error
**unknown command 'linux/vmlinuz'**.

the error message says you left off the space. And where did the msdos come in at. commands have to be exact.

linux /vmlinuz root=/dev/sda4 ro

---

### Post by troubledBeginner on 2012-11-28
sir my partition name is (hd0,msdos4) thats why i have to use that everywhere.

---

### Post by audiomick on 2012-11-28
> **troubledBeginner said:**
> sir my partition name is (hd0,msdos4) thats why i have to use that everywhere.

Try what Fred suggested. He is usually right.... ;)

---

### Post by oldfred on 2012-11-28
Grub optionally now uses either msdos or gpt (maybe others?) to specify the type of partitioning. But device settings do not use that, so it should be this.

/dev/sda4

In grub it can be 

(hd0,4)
or 
(hd0,mdos4)

---

### Post by troubledBeginner on 2012-11-28
Sir,my system booted up just now!!! I am really heartily very thankful to you people,atleast i can save my data now!
but when i restarted the system i got the same error, what do i need to do next??

---

### Post by critin on 2012-11-28
> **troubledBeginner said:**
> sir my partition name is (hd0,msdos4) thats why i have to use that everywhere.

Sir, as oldfred stated,>  commands have to be exact   Copy and paste the command for best results and to avoid typos.

Good luck!

Edited--too late for my bit of advice...lol

---

### Post by oldfred on 2012-11-28
You have to manually boot again.

But you need to reinstall grub to fix the issue.

Once booted run this:

       sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
That should work, but you may have to totally uninstall & reinstall grub2 if it does not.

---

### Post by troubledBeginner on 2012-11-28
Installed boot repair and then applied recommended repair. Got my system working after a whole week. I am teary eyed. May god bless all of you,abundantly. 
Thanks a lot people. 
Ubuntu got a new lifelong fan. Ubuntu Rocks!
Thanx again Sir(s),thanx a zillion.

---

### Post by oldfred on 2012-11-28
Glad you got it working.

Now is a good time to work on procedures to back up your data. Hard drives also fail and then there is no way to get data back.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

