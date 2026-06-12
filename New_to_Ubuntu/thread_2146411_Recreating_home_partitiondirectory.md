---
title: "Recreating home partition/directory"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by chinna saaeb on 2013-05-18
I am using ubuntu 12.04 on thinkpad t43 .
I had installed ubuntu replacing the original xp.
I needed to reinstall windows xpsp3 and i did that and in the processes deleted the home partition.
I have made the system dual using grub4dos.
Logging as root into ubuntu I modified the /etc/fstab making appropriate modifications.
I created a home directory (it is blank- unfortunately ubuntu /etc/skel directory does not contain the ome direectory contents)
Now my problem is that I cannot login into the graphical mode (level 5)
I created a new user but nothing happened the user also cannot login into the graphical mode
Any solutions?
(Note my pc ram cannot go beyond 2GB and it is a p4 . So i dont wont to use virtual box for ubuntu. Similarly I am not for Xp into virtual box because I would need a new license then)

---

### Post by oldfred on 2013-05-18
Lets see details. Normally I thought if /home did not mount, it just created a new default. 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Update If you want to move data to /home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by chinna saaeb on 2013-05-18
Thanks.
The partition is gone and over written.
I have made changes to /etc/fstab and able to safely boot to level 3 but not to level 5 graphical mode
Now I have created the users home directory using mkdir -p /home/username
But the contents / configurations inside this are needed
Standard is that one should copy from /etc/skel. But in that there is nothing.
Now the users cannot boot to graphical mode.
Somefiles such as .dkim etc are needed.
creating user with useradd did not help
My specific requirement is to be ale to boot to level 5 graphical boot. I need to do everything for that
Kindly advise

---

### Post by oldfred on 2013-05-18
I do not know where default /home settings come from. 
My /etc/skel only has one Desktop entry and that is examples. And that is the same in several older versions also.

Does not rebooting create settings?

---

### Post by chinna saaeb on 2013-05-18
No, rebooting does not create it.

---

### Post by oldfred on 2013-05-18
Are you booting as a user not root?  So UID is 1000 which should be the first user.

[https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder)

---

### Post by chinna saaeb on 2013-05-18
Thanks
Logging in as a user not as a root.
The given link has only general notes.
Knowing what happens when a user is created - what ubuntu does at the underlying layer will provide me a solution
In Redhat / fedora the contents of /ect/skel are copied into the newly created users home. But here what happens we don't know

---

### Post by sisco311 on 2013-05-18
> **chinna saaeb said:**
> Thanks
Logging in as a user not as a root.
The given link has only general notes.
Knowing what happens when a user is created - what ubuntu does at the underlying layer will provide me a solution
In Redhat / fedora the contents of /ect/skel are copied into the newly created users home. But here what happens we don't know

The same happens in Ubuntu too. In my skel directory there are 3 hidden (dot) files: .bash_logout .bashrc and .profile. Non of this files are needed for a GUI login.


Did you chown the home directory of the user?

useradd is low level utility for adding users. Try to create the user with the adduser command which, by default, will create the home directory with skeletal configurations. 

And what do you mean by you cannot login into the GUI. Does the display manager start? Do you get any error messages during the boot?

---

