---
title: "Mounting NAS following Hardy Heron upgrade"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Edk on 2008-05-02
Under Ubuntu 7.10 I used to be able to mount my NAS using this command:

> sudo mount -t smbfs //192.168.0.2/data /mnt/mini -o username=xxx,password=xxx,fmask=0777,dmask=0777 


Having upgraded to Hardy Heron, (No changes here just the bog-standard upgrade) the mount is OK, but I do not have permissions to create new files or folders using the GUI

Re-running the command in a terminal gives me this error:

> WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead. 

I tried:

> sudo mount -t smbfs //192.168.0.6/data /mnt/mini -o username=xxx,password=xxx,file_mode=0777,dir_mode=077 

but that did not work either

Can anyone come to my rescue please?!

Thank you very much

---

### Post by quirks on 2008-05-02
Have you tried this (**cifs **instead of **smbfs**):
```
sudo mount -t **cifs** //192.168.0.6/data /mnt/mini -o username=xxx,password=xxx,file_mode=0777,dir_mode=0777
```
Note: you also forgot a **7** at the end of dir_mode; could also be a copy and paste mistake, though.

---

### Post by drsox1899 on 2008-05-02
There are several posts with the same problem - me included !

I think they broke something in HH.

Unprotected shares on a NAS are OK, but passworded ones - not possible.

---

### Post by Paqman on 2008-05-02
If it's a NAS you probably want to mount it permanently at boot anyway. [This thread](http://ubuntuforums.org/showthread.php?t=288534) can help you set that up. Works perfectly for me in Hardy.

---

### Post by Edk on 2008-05-02
quirks - I tried that an exactly the same happened!

Paqman - My NAS has embedded Linux running FAT 32 - as far as I am aware.  It is a LACie.  The link you gave me does not seem to be relevant to me as it focusses on Windows shares, or have I missed somethign somewhere?

Thanks for help so far!  Much appreciated

---

### Post by fballem on 2008-05-11
> **Edk said:**
> quirks - I tried that an exactly the same happened!

Paqman - My NAS has embedded Linux running FAT 32 - as far as I am aware.  It is a LACie.  The link you gave me does not seem to be relevant to me as it focusses on Windows shares, or have I missed somethign somewhere?

Thanks for help so far!  Much appreciated

Don't know if this helps at all, but I am also running a LaCie NAS and definitely not having a problem: [http://ubuntuforums.org/showthread.php?p=4932265#post4932265](http://ubuntuforums.org/showthread.php?p=4932265#post4932265)

---

### Post by Edk on 2008-05-11
Sorry for the delay in getting back to you

Thanks but I remain confused.

My original command was:

[INDENT]sudo mount -t smbfs //servername/data /mnt/servername -o username=xxxx,password=xxxxx,fmask=0777,dmask=0777[/INDENT]

This worked fine in 7.nn

However I now get the error message:

[INDENT]WARNING: CIFS mount option 'fmask' is deprecated. Use 'file_mode' instead.
WARNING: CIFS mount option 'dmask' is deprecated. Use 'dir_mode' instead.
[/INDENT]

I have checked and smbfs IS installed, and from Synaptic it seems that  that allows CIFS as well?!

I have tried searching for information on CIFS and not get anywhere useful.

The issue seems to be one of permissions on the mount, as explained above.  It mounts, but only root can write!   

Reading the various linked and suggested forums posts, it seems that I need to use the fstab.  For a range of reasons I am not too keen to do that!  Surely it should work at the command line?

---

### Post by Edk on 2008-05-15
I have been able to solve this, with help from another forum, so am posting the reply in case anyone else is suffering as I did!!


[For the full posting see this link]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&p=58707")

For a quick answer this is it:

The code is:

[INDENT]sudo mount -t cifs //SERVER_IP/SERVERPATH /mnt/mini -o username=xxx,password=xxx,uid=MY-USERNAME-ON-UBUNTU,gid=users[/INDENT]

/mnt/mini is the local mount point and was previously created. 

I hope this helps someone else.

---

### Post by Paqman on 2008-05-15
> **Edk said:**
> 
Paqman - My NAS has embedded Linux running FAT 32 - as far as I am aware.  It is a LACie.  The link you gave me does not seem to be relevant to me as it focusses on Windows shares, or have I missed somethign somewhere?


Pretty much all NAS's run embedded Linux (mine included). However, since they're designed to share to a Windows network they tend to use Samba.

---

