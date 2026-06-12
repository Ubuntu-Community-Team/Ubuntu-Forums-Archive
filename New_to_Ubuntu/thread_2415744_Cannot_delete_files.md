---
title: "Cannot delete files"
date: 2019-03-30
forum: New to Ubuntu
---

### Post by petruta.c on 2019-03-30
Hello, 

I am an absolute begginer to Lubuntu. 
today I tried to delete some files but I get an error message "Unable to find or create trash directory for /media/petruta/Partitie/Personal( this is the name of the folder)/De rezolvat.docx

I tried deleting several files and folders and I get the same error. I checked the permissions and they are all "Read & write" and "Modify the content of the folder".
I know this question has been posted before, but I still don't understand what I need to do to correct this. 

Thank you!

---

### Post by ajgreeny on 2019-03-30
They may be read/write but to whom do they belong?

Are these files on an external drive?  External drives are usually mounted in /media/username as shown by the pathway of your file, but depending on a few settings such as the mount options and also the filesystem to which the external drive is formatted, files on it may belong to root, hence your inability to delete them.

With the external drive attached (if I'm right about that) show us the output in terminal of ```
sudo blkid -c /dev/null
ls -l /media/petruta/Partitie/Personal
```
which may help figure out why you're seeing this problem.

---

### Post by oldos2er on 2019-03-31
It might be unable to deal with the space in the file name *De rezolvat.docx*, you may need to use a terminal and escape the full name "/media/petruta/Partitie/Personal/De rezolvat.docx" with quotation marks just as I've done here.

---

### Post by ajgreeny on 2019-03-31
Good catch oldos2er.

I assumed that being a new user this would have been tried using a file manager, not command line, but having re-read the post I think you're probably correct.

@petruta.c
It is worth getting into the habit of using - or _ in place of spaces in file names as it makes life a lot simpler in terminal commands, though autocomplete will help, ie start typing the filename and hit tab after a few letters to fill the rest automatically.  If nothing appears immediately hit tab again and a list of matching file names will appear.

---

### Post by petruta.c on 2019-03-31
Hi everyone, 
Thanks a lot for your time! 
The files are on the computer drive, not on an external one. I use the file manager, not the terminal. 
I checked the permissions in "Properties" and they appear as "Owner: root; Group: root". In the attachment you can see the result I got by entering the code lines you indicated. 
What should I be doing now? 

Also, thanks for the tips regarding file naming, I'll keep it in mind. 

@oldos2er: I don't understand what you mean by "escape the full name with quotation marks"







Thanks again for your time and patience!

---

### Post by yancek on 2019-03-31
The owner:group of all the files is root user so on Ubuntu, you need to use 'sudo' to prefix a command.  THe Ubuntu documentation on using sudo is at the link below.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to edit as admin, read the Ubuntu handbook link below which explains how to do that.

[http://ubuntuhandbook.org/index.php/2018/02/open-as-admin-nautilus-file-browser/](http://ubuntuhandbook.org/index.php/2018/02/open-as-admin-nautilus-file-browser/)

> I don't understand what you mean by "escape the full name with quotation marks"

A number of the files in your example have spaces in the name.  Should not be a problem in a file manager but if you try to do it in a terminal using 'rm' (remove command), it will fail unless you put it in quotes as below.  You will need to be in the directory in the terminal in which the files exists.  You can do it from anywhere in the filesystem only if you include the full path. 

> sudo rm "Astro calcul.doc"

---

### Post by Impavidus on 2019-04-01
> **petruta.c said:**
> 
today I tried to delete some files but I get an error message "Unable to find or create trash directory for /media/petruta/Partitie/Personal( this is the name of the folder)/De rezolvat.docx
Was that the full error message or did it also say something about "permission denied" or "read-only filesystem"?

I assume the files you cannot delete are on sda2. That's an ntfs partition. Ntfs is a Windows format, so don't expect it to work perfectly on Linux. It's fine for sharing files with Windows on dual-boot computers, but on Linux-only systems ntfs is best avoided. All files on sda2 are owned by root, but all users have full access, so that shouldn't be a problem.

Ntfs has two disadvantages on Linux. The first is that it doesn't support Linux-style permissions and ownership. Permissions and ownership are set by the mount options and are the same for all files and directories on the partition. If you mounted the partition using the file manager, ownership should be set to you, but I imagine this could go wrong if you used your file manager as root.

The second problem is that, although Linux can read and write ntfs, it cannot defragment it or fix it if damaged. If an ntfs partition gets damaged, you need Windows to fix it (or you can format it, but that destroys all files stored there).

Show this:```
findmnt /dev/sda2
ls -ld /media/petruta/Partitie
```
Instead of using a screenshot, you can copy and paste the text into your next post. It's easier.

---

### Post by petruta.c on 2019-04-11
Hey Impavidus, 
That was the full message that I got. 

Below you can see what I got when entering those commands.

petruta@petruta-pc:~$ findmnt /dev/sda2
TARGET                  SOURCE    FSTYPE  OPTIONS
/media/petruta/Partitie /dev/sda2 fuseblk rw,relatime,user_id=0,group_id=0,allow_other,blksize=4
petruta@petruta-pc:~$ ls - ld /media/petruta/Partitie
ls: cannot access '-': No such file or directory
ls: cannot access 'ld': No such file or directory
/media/petruta/Partitie:
'$RECYCLE.BIN'                        Huawei
'AIP Protocol'                        Kindle
 Audiobooks                           Kituri
'Ayurveda Yoga & Meditation'         'Managementul calitatii - text bits'
 buget-personal-Laurentiu-Mihai.xls  'Microsoft Excel 2010 Formulas.pdf'
 Carti                                Model-Buget-Eveniment-Proiect.xlsx
'CVuri actualizate'                  'Modele scrisoare de intentie.doc'
'Dezvoltare personala'                MSOCache
 Diferite                             MUZICA
 Diplome                             'Muzica Adi'
 Diplome+CV                           Personal
'Diplome .zip'                        Plan-Financiar-ONG-Laurentiu-Mihai.xls
 DSC_0026.JPG                         POZE
'Evolution - revolution'              Scoala
'excel_tutorial (1).pdf'             'System Volume Information'
 Filme                                tunsori
petruta@petruta-pc:~$ 

 Thanks for the help.

---

### Post by Impavidus on 2019-04-12
Read more carefully. There should be no space between the dash and ld:```
ls -ld /media/petruta/Partitie
```

---

### Post by petruta.c on 2019-04-12
Hi, 
Thanks for pointing this out. This is what i got now: 

petruta@petruta-pc:~$ findmnt /dev/sda2
TARGET                  SOURCE    FSTYPE  OPTIONS
/media/petruta/Partitie /dev/sda2 fuseblk rw,relatime,user_id=0,group_id=0,allow_other,blksize=4
petruta@petruta-pc:~$ ls -ld /media/petruta/Partitie
drwxrwxrwx 1 root root 32768 mar 30 23:50 /media/petruta/Partitie
petruta@petruta-pc:~$

---

### Post by Impavidus on 2019-04-13
The partition is mounted with rw (read-write) option and all users have rwx permissions on it. It's supposed to work. Does the problem persist?

But when normally mounting some ntfs partition using the file manager, it should be owned by your regular user and have no write permission for the group and others. How do you mount this partition? If using the file manager, do you use it as root (you shouldn't)? After unmounting it, do you still see the /media/petruta/Partitie directory? It should disappear if you used the file manager to mount.

BTW, I see no evidence of a Windows system on your computer. Avoid using ntfs partitions on an internal drive if there's no Windows installed on that computer.

---

### Post by petruta.c on 2019-04-14
Hi, 

The partition is always mounted when I turn on the computer, I think that the mounting is automatic. 
I had windows before and then had lubuntu installed because windows seemed to stop working ( the laptop would heat itself so much that it shut down). 

How can I test the unmounting / mounting of the partition? 
Also, can the partition be changed from ntfs to one compatible with lubuntu? 
Thanks!

---

### Post by The Cog on 2019-04-14
If the partition is mounting at boot, then I expect that it is listed in /etc/fstab. Please post the outpout from the command **cat /etc/fstab** and we can check that out.

You can't change an ntfs partition into a linux compatible one (ext4 is the current normal one) without reformatting. You would need to copy your data elsewhere, reformat, then copy your data back. Also edit /etc/fstab to get it to mount on boot.

---

### Post by petruta.c on 2019-04-14
Hi Cog, 
Thanks for the info. 

Could you give me the exact command I should be entering? Thanks! :)
I would not have a problem in reformatting. I meant to delete almost all the files on this computer ...

---

### Post by The Cog on 2019-04-14
> **petruta.c said:**
> Hi Cog, 
Could you give me the exact command I should be entering? Thanks! :)

Not without more info. Can you post the output of these two commands please:
```
cat /etc/fstab
lsblk -mf
```

---

### Post by petruta.c on 2019-04-14
petruta@petruta-pc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=dfdc8f90-5279-4ba7-b94a-2e758c1beb83 /              ext4    defaults   0 1

#part 300 GB ntfs
UUID="0A6E96B76E969B51" /media/petruta/Partitie ntfs-3g defaults 0 0
petruta@petruta-pc:~$ lsblk -mf
NAME     SIZE OWNER GROUP MODE       FSTYPE LABEL UUID                                 MOUNTPOINT
sda    465,8G root  disk  brw-rw----                                                   
&#9500;&#9472;sda1 107,7G root  disk  brw-rw---- ext4         dfdc8f90-5279-4ba7-b94a-2e758c1beb83 /
&#9492;&#9472;sda2 358,1G root  disk  brw-rw---- ntfs         0A6E96B76E969B51                     /media/petruta/Partitie
sr0     1024M root  cdrom brw-rw----

---

### Post by The Cog on 2019-04-14
OK, IO can see in fstab that UUID 0A6E96B76E969B51 is to be mounted at /media/petruta/Partitie. And from lsblk I can see that this is device /dev/sda2. 

To unmount this, reformat it to ext4, mount it in the same place and give ownership to user petruta, give these commands
The ownership setting is needed because by default, new partitions are owned only by root:
```
sudo umount /dev/sda2
sudo mkfs.ext4 /dev/sda2
sudo mount dev/sda2 /media/petruta/Partitie
sudo chown petruta:petruta /media/petruta/Partitie
```
You then need to make this new partition mount every time you reboot. 
First you need to know the new UUID for the freshly formatted partition sda2. Run this command to find out:
```
lsblk -mf
```
Then you need to edit /etc/fstab. You can do it with the editor **nano** like this:
```
sudo nano /etc/fstab
```
You can edit the last two lines so they look more like this, but use the new UUID that lsblk showed you for sda2 in place of the question marks:
```
#part 300 GB ext4
UUID="???" /media/petruta/Partitie ext4 defaults 0 2
```

---

