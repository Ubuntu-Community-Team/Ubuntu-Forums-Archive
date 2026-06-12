---
title: "Files copied from a Mac seem to be empty ..."
date: 2013-01-02
forum: New to Ubuntu
---

### Post by Richard0102 on 2013-01-02
Hello,

I'm very new to Linux having installed Ubuntu 12.04 today.  I also have machines running Windows and an iMac (Mountain Lion) on my home network.

I can see my iMac from my laptop running Ubuntu, and can copy files from the Mac onto, for example, the Ubuntu desktop OK.  However, if I try to open those files I get an error message suggesting the file can't be read.  For example if I double click a .jpg file image viewer reports 'Could not load image <filename>.  Error reporting JPEG image file (improper call to JPEG library in state 200).  Similarly, if I double click a .pdf file copied from the mac I get 'Unable to open document.  File type plain text document (text/plain) is not supported.   

The curious bit is if I copy the exact same files onto a USB stick on the Mac, transfer the stick to the Ubuntu laptop, then they open just fine - either from the sick or if copied from the stick to the Ubuntu desktop.  

Investigating further, I found that if I copy (say) the .jpg back to the Mac then it won't open there either. The Mac reports 'The file <name> cannot be opened because it is empty'.  This caused me to look harder at the files as saved onto the Ubuntu laptop, and I notice that they are all 0 bytes in size!  It seems therefore as if the process of copying across the network copies an empty file shell, but not the file itself?

(Also, if I open up the Mac folder in Ubuntu's file manager and double click to open it, I get the same errors although, thankfully, back on the Mac, the file is unharmed.  I guess the attempt to open the file first means opening a copy on the Ubuntu machine?
 
Can anyone suggest what might be going on please?

(PS I;m running 64 bit Ubuntu if that makes any difference?)

Many thanks 

Richard - a confused newbie!

---

### Post by Terl on 2013-01-02
I imagine it has to do with Ubuntu accessing the HFS+ filesystem on the iMac.  Check [this Ubuntu doc]("https://help.ubuntu.com/community/hfsplus") and maybe [this will help.]("http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write")  I do not have a Mac any more so I cannot test these.  Oh, and more [here in forums]("http://ubuntuforums.org/showthread.php?t=953569").  It all seems centered on HFS+ file system issues but seems correctable.

---

### Post by BBQdave on 2013-01-02
> **Richard0102 said:**
> Can anyone suggest what might be going on please?

Hi Richard,

I have a legacy eMac with 10.4 that I use as a file server. First I enabled the ftp server on 10.4. And on my Ubuntu 12.04 notebook I use [Filezilla]("http://filezilla-project.org/") as a client application to access my eMac.

I am able to save and retrieve data with this set up. If you choose to try this method of data storage and transfer - when accessing your iMac as a ftp file server with Filezilla, you will be asked for the iMac's address, user name, port - usually 21, and user account password.

You may want to consider security steps with a ftp server. A strong password on both systems is a good idea of course. And I do this data transfer on my secure home network which is behind a couple of fire walls :)

---

### Post by Richard0102 on 2013-01-05
Thanks for the suggestions both.  I've read up on the Mac file system and am not keen on disabling journalling etc (I don't fully understand the implications, so best not to meddle I think). 

I've tried filezilla but with no luck - 'connection refused' messages.  

I don't have need to copy many files very often, so a USB stick solution is OK for now, but if anyone has any more suggestions, I would be grateful.

Thanks again.

---

### Post by r-senior on 2013-01-05
I share out directories from Ubuntu using NFS and connect to them with an iMac. That works well for me.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

If it's just occassional transfer, there's always Dropbox.

---

