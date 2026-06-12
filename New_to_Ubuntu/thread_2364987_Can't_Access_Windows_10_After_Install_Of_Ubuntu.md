---
title: "Can't Access Windows 10 After Install Of Ubuntu"
date: 2017-06-30
forum: New to Ubuntu
---

### Post by newdorplane on 2017-06-30
Hello All...I am fairly new to Ubuntu, and not computer savvy in any sense, so please keep that in mind when prescribing solutions:

I had a dual boot machine, consisting of Windows 10 and Ubuntu.

I had a stupid idea of wanting to replace Ubuntu with Fedora, so I did the install, which went fine.  The thing is, Fedora's grub took over the entire drive, and I could no longer access Windows via GRUB.  I could access Windows by hitting F9 when the machine booted up, and going through that menu.

After using Fedora a short time, I realized that migrating from Ubuntu was a mistake, so I reinstalled Ubuntu.  That's when my problem began...

From this point forward, I cannot access Windows 10 - at all.  I have tried to uninstall and reinstall Grub, but Grub doesn't recognize my Windows partition.  If I hit F9, I cannot get to Windows; the menu only sees Ubuntu.

My HP laptop is out of warrantee; I cannot get a copy of Windows 10 software.

I did download Windows 10, and tried to repair the system as it booted up, but Windows said that I needed to use the software that came with my laptop (which I don't have).

I have looked online for solutions...I really don't know what to do.  I have tried mounting my Windows partition, and getting GRUB to recognize it, but both attempts have failed.

Thanks in advance for your time

---

### Post by oldfred on 2017-06-30
Have you run ?
sudo update-grub

You show an ESP - efi system partition, but was Windows originally BIOS boot from MBR partitioned drive? Windows only boots with UEFI from gpt and only with BIOS from MBR.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by newdorplane on 2017-06-30
> **oldfred said:**
> Have you run ?
sudo update-grub

You show an ESP - efi system partition, but was Windows originally BIOS boot from MBR partitioned drive? Windows only boots with UEFI from gpt and only with BIOS from MBR.

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Appreciate the reply.  Yes, I have run sudo update grub, updated and reinstalled grub, etc.

---

### Post by newdorplane on 2017-06-30
Sorry for the quality of the attached images...hope they are of some usefulness

---

### Post by oldfred on 2017-06-30
Normally Boot-Repair gives you a pastebin link, and you need to post that.
Report usually is too large to attach.

But from what I see is that you converted sda1 from the normal Windows boot partitionn in MBR partitioning with its boot files to a bios_grub partition which is only required or used with gpt partitioning.

Need to see full report to be sure of what fixes are needed, but you at minimum will need a Windows repair or installer with repair console to add the missing boot files. Windows normally has a separate boot partition but those files can be in the main install or c: drive, if boot flag is on c: drive. Boot-Repair or Linux tools cannot add the missing files, only Windows due to copyrights and legal stuff.

---

### Post by newdorplane on 2017-06-30
> **oldfred said:**
> Normally Boot-Repair gives you a pastebin link, and you need to post that.
Report usually is too large to attach.

But from what I see is that you converted sda1 from the normal Windows boot partitionn in MBR partitioning with its boot files to a bios_grub partition which is only required or used with gpt partitioning.

Need to see full report to be sure of what fixes are needed, but you at minimum will need a Windows repair or installer with repair console to add the missing boot files. Windows normally has a separate boot partition but those files can be in the main install or c: drive, if boot flag is on c: drive. Boot-Repair or Linux tools cannot add the missing files, only Windows due to copyrights and legal stuff.

Thanks for your time Fred.  Mine is a live and learn experience; since my hard drive has 20GB allocated towards windows repair/reinstall, it never occurred to me to make a backup Windows USB stick.

I'll try getting a handle on that, and pursue this through the Windows end...

Thanks again Fred, for trying to help.

---

### Post by oldfred on 2017-06-30
Hard drives do fail, so backups on hard drives are not really backups.

Some Windows links:
 How to: perform a repair upgrade using the Windows 10 ISO file
[http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085) 
   Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

 If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by Darth4212 on 2017-07-02
A long time ago when I first joined this forum or maybe some other can't remember (it was actually the reason why if I remember correctly) I had the same problem. My solution, as dumb as it is, was to download a program called Grub Customizer. Once I launched it it showed that the Windows 10 partition was hidden and I was able to unhide it with the program.
You can install the program by launching a terminal in Ubuntu and running the following commands:
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
```
Input your password, press **ENTER **and let it do its thing
Then run:
```
sudo apt-get update
```
And let it do its thing
Then finally run:
```
sudo apt-install grub-customizer
```
After it installs launch the program and go to View and after that click Hidden Entries
This should - hopefully - show your Windows partition and you can fix it!

---

### Post by johndough2 on 2017-07-02
Hi

I have a HP laptop that has a recovery partition, and HP sent me recovery DVD's and I recently used an .iso of Windows 10 I made myself and went to HP and updated drivers, SO you can install W10 independently.

I do not see the windows efi partition.  This is about 100 -250 MB in size and is usually the first partition, I think grub has overwritten it.  Perhaps you could try and create a small partition for grub by shrinking the swap file or something and giving the space back to W10.

---

### Post by oldfred on 2017-07-02
First post shows screen shot of partitions and sda5 is showing as an ESP - EFI System partition.
But that is unusual as johndough2 mentions as normal Windows installs ESP in first or second partition. some older HP systems have with BIOS/MBR a vendor recovery partition that was FAT32 and sometimes seen in partition lists as an ESP, but was not and should not be used as an ESP.

Please copy & paste terminal output, not post screen shots except from gui programs. You can just copy & paste, but if longer use Forum's Advanced Editor and use # to add code tags.

---

### Post by newdorplane on 2017-07-06
Okay...in case anyone runs into this problem, here's what I did:

Downloaded a copy of Windows 10 from Microsoft (this problem cannot be approached from the linux side, but from Windows OS).

Following commands:

Put bootable Windows USB into slot, and boot computer.  At the same time, shift + F10, which will bring up a terminal type window.

Next, enter the following commands:

# diskpart

(enter)

# list disk

(enter)

Discern which partition Windows is on, and in my case it was disk "0", so the following command was entered:  

# select disk 0

(enter)

# clean

(enter)

# convert GPT

And that's it!  Problem solved...

---

