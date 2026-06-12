---
title: "HOWTO: Read and write Linux-like partitions (ext, xfs, jfs ...) under Windows XP"
date: 2007-09-03
forum: Outdated Tutorials &amp; Tips
---

### Post by C64MAN on 2007-09-03
Hi All Ubuntu Fan!

Thats my first post here, what is more my English isn't very good yet, so please be patient and supportive. Thanks.

I have a solution for the problem of filesystems-opsystems dilemma. I have never read any solution like that yet, that I decided to share with the Community.
Maybe that solution a bit complex and resource waster, but it works. 

First, I consider my idea for Masters, who can work without the full guide.

**The idea:** Under Windows XP install a VMware workstation, make a new Ubuntu virtual machine with NAT networking, install Ubuntu onto the virtual machine, stop it, go to the virtual machine's settings, connect your HDDs which contains Linux-like partitions and You want to use them to Your virtual machine. Then boot it up, locate the drives, than put them into the fstab. After that setup a SAMBA server, and share your drives. Now you can discover your drives via windows networks.

**Now in details**:

_Shopping list_:
- Microsoft Windows XP SP2
- [VMware Workstation]("http://www.vmware.com/vmwarestore/newstore/wkst6_eval_login.jsp") (You can download and use it for 30 days for free. When You finetuned your virtual machine You can change workstation to player which is full free.)
- Ubuntu 7.04
- Linux like partitions connected
- Time

_Tested with_:
- Windows XP Professional SP2 (With fresh drivers.)
- Ubuntu Feisty Fawn 7.04 Desktop
- VMware workstation 6
- My config is: AMD Athlon 64 X2 5200+, 1GB RAM, WD Caviar SATAII HDDs, XFS partitions

I used guides from ubuntuguide.org to write that HOWTO. Ubuntuguide.org is a very usefull site. 

**Let's start**:
1. Boot up Your Windows. Be sure, your Linux HDDs are connected. Check it in Device Manager. The HDDs must appear there. (Not the partitions.)

2. Download VMware workstation, get a registration key, and install it.

3. Create a new virtual machine for Ubuntu or 2.6 Linux OS. I recommend 6-8GB virtual drive, half of your system RAM, and NAT networking.

4. Insert Your Ubuntu CD, and start the virtual machine. Install a normal Ubuntu system. 

5. Shutdown Your installed virtual machine, open its settings, add your HDDs to the virtual machine. Then start it again.

**Be careful! After the previous step your partitions are online, and accessible, writeable etc... So look after your important files!**

6. Locate the names of your partitions device name. (Tip: You can find it at System->Settings->Hardwareinformation find your HDDs with them volumes, than click on Advanced. There you can see the device name.)

7. Insert your partitions into fstab:
You must know the filesystem's name. (You can get this information from Hardwareinformation too.)
Open a new folder in /media as a mounting point for the partition and set its permissions.
Open a terminal:
```
su
mkdir /media/*mountpoint
chmod 777 /media/*mountpoint

```
Replace *mountpoint with the directory name what you want. (But I recommend the device name. For example: hdb1, hdb2, hdc1 etc...)
Now open the fstab for editing.
```
gedit /etc/fstab
```
Open a new line, and insert your partitions data like that:
```
*devicename *mountingpoint  *filesystem  defaults 0 0
```
(* You must replace with the correct data.)
For example:
```
/dev/hdb1 /media/hdb1 xfs defaults 0 0
```
Save it, than reboot, and check how is it works.

8. [Install]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service"), and [configure]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_network_users") Samba. When you finished installion, and added yourself to the server, open System->Administration->Shared folders Set the workgroup, and check in "The computer is a WINS server." 

9. Now You can share your partitions. You can permit write permissions if you want.

10. Minimize the virtual machine's resurces. Decrase the shared RAM. Exactly I didn't finish that point. You can dull the system. I think you can stop gdm and other unnecessary services.

11. I recommend a windows reboot, than start the linux virtual machine. 

Now you can discover your partitions in the windows networks.

Good luck!
C64MAN

---

