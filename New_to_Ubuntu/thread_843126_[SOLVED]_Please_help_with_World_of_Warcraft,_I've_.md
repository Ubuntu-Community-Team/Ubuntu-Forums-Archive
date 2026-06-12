---
title: "[SOLVED] Please help with World of Warcraft, I've tried everything"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Paraphysicist on 2008-06-28
I'm trying to get this game to work, but haven't been able to install it.  I've searched the forums and google for help and I've been following several guides (as well as the 150+ main thread here) but I can't get past this step:

[PHP]cd /<path-to-directory>/
 wine Installer.exe[/PHP]

This is what I get after I run it:

[PHP]slippy@treefish:/cdrom$ wine Installer
wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
[/PHP]

I've tried copying the files from the dvd onto the desktop, it gives the same message.

[PHP]wine: could not load L"C:\\windows\\system32\\Installer.exe": Module not found
slippy@treefish:~/Desktop/wow_install$ 
[/PHP]

I have tried searching the dvd for a .exe file, but theres only an ununstaller.exe. There's a file called Installer Tome.mpq, but I get the same output from that command:

[PHP]slippy@treefish:~/Desktop/wow_install$ wine Installer_Tome.mpq
wine: could not load L"C:\\windows\\system32\\Installer_Tome.mpq": Module not found
[/PHP]

The guide says that in some dvds the installer is hidden, and that I should unmount the dvd, then re-mount it with this code:

[PHP]sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/[/PHP]

I have tried this code as is, after unmounting first, after forcibly unmounting, and I always get the same message:

[PHP]slippy@treefish:/cdrom$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
[sudo] password for slippy: 
mount: /dev/scd0 already mounted or /media/cdrom0/ busy
mount: according to mtab, /dev/scd0 is mounted on /media/cdrom0
[/PHP] ](*,)

I've also went in through the GUI and right-clicked Installer Tome.mpq, then clicked Open with "Wine Windows Emulator", but nothing happened. 

Wine is updated to 1.0.


I'm at a loss as of what to do, I've read a couple of similar issues with running wine Install , but haven't found any answers to it.  If anyone could help get this thing running, I will be eternally grateful. Thanks :KS

---

### Post by Paraphysicist on 2008-06-28
I got it working!  The dvd installer.exe was hidden, but the command in the guide didn't work.  I went to [http://linux.about.com/od/ubuntu_doc/a/ubudg19t19.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg19t19.htm) and found some commandds.  This command to mount worked well:

[PHP]sudo mount /media/cdrom0/ -o unhide[/PHP]

This command to unmount also worked: 

[PHP]sudo umount /media/cdrom0/[/PHP]

Now it's installing just fine.

---

### Post by Crafty Kisses on 2008-06-28
> **Paraphysicist said:**
> I got it working!  The dvd installer.exe was hidden, but the command in the guide didn't work.  I went to [http://linux.about.com/od/ubuntu_doc/a/ubudg19t19.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg19t19.htm) and found some commandds.  This command to mount worked well:

[PHP]sudo mount /media/cdrom0/ -o unhide[/PHP]

This command to unmount also worked: 

[PHP]sudo umount /media/cdrom0/[/PHP]

Now it's installing just fine.

Mark the thread solved.

---

### Post by Paraphysicist on 2008-06-28
> **Codename said:**
> Mark the thread solved.

:confused: I marked it solved right after the last post.

---

### Post by Tuxoid on 2008-08-02
Thank you very much.

I have been spending hours on this and finally, finally..., I find out it's a problem with my mount options.

---

