---
title: "I need some help with directory ownership"
date: 2023-11-12
forum: New to Ubuntu
---

### Post by ironhand42 on 2023-11-12
I'm running Ubuntu 22.04.3 LTS on a home-built AMD Ryzen 7 3700 chip w/Gigabyte X570 mobo & Samsung 980 Pro 2 TB SSD. I've set up virtual  Windows 7 with KVM and QEMU. It runs flawlessly. But when I move a file, even a simple text file from Windows 7 to my host Public folder (inside my Ubuntu Home folder) Ubuntu tells me I don't have permissions to open the file (or any other for that matter) and this has driven me crazy. Yes, I've googled how to do this and have read 25 to 50 articles all directing me to the command line and chmod and chown commands but these are no help because they almost include something about the "path" to the folder. Well, I cut my teeth on CP/M and know how to cd around in Windows, but not Ubuntu. This has been going on for years.  Someone show me how to take COMPLETE read write ownership of my Ubuntu Downloads and Home folders. I'll need baby steps.

Cheers,

Richard Smiley


BTW I think someone could make some money by programming a simple Gui method for doing this.

---

### Post by MAFoElffen on 2023-11-12
Spinning up a Win7 Pro VM to take screen shots... BRB...

EDIT:
I can start writing that up... In your KVM setup, I assume you have Virtual Manager installed right?

---

### Post by MAFoElffen on 2023-11-12
<<EDITED>>Nothing special needed in the config.

I was going to do a passed through filesystem with virtiofs, but... The virtio drivers for that didn't support Win7. It started with Windows 8.0...

So what I did was to use Samba on my host > Created SMB Network shares of the folders I wanted to shared, created Samba Users, and let Sabmba through the UFW firewall. Then on the Win7 side, created inbound and outbound rules through the Firewall for SMB, setup the advanced sharing options, created a mapped network drive... Which then they showed up as Folders in the File Explorer. Then created shortcuts for them on the Desktop.

Would learning how to do it something like that work for you?

---

### Post by yancek on 2023-11-13
Your situation isn't a matter of owner:group or permissions but the fact that you are using a host and guest system (guest being the virtual software) to copy to/from.  You need to set up shared folders on the guest machine.  Have you done that?  Just do an online search for it with KVM/QEMU in the search.  To give you an idea of what to look for, I am posting a link to a site below that describes the process on KVM.  I would suggest reading through it before starting to make changes, maybe find a couple of other sites so you get an understanding of it.  

[https://alexandrerosseto.medium.com/vmware-linux-how-to-share-folder-between-host-and-vm-62e63419ecbb](https://alexandrerosseto.medium.com/vmware-linux-how-to-share-folder-between-host-and-vm-62e63419ecbb)

Are you copying files from the windows 7 guest OS while logged in to Ubuntu, to copy to an Ubuntu directory or are you copying from windows 7 to the host Ubuntu?  Part of the problem may be that windows 7 is outdated, unsupported but that's just a guess.

---

### Post by TheFu on 2023-11-13
```
sudo chown -R $USER:$USER  $HOME
```
exactly as typed.  That should be 100% safe.

Then you can run 
```
sudo chmod  -R u+rw  $HOME
```

This may not be a good idea, but I can't think of any terrible repercussions that should happen after doing that.  I suppose some snaps might break, but they shouldn't.  Canonical and I have a differences of opinion for how snap constrains should work, however.  I can't think of any standard Linux/Unix thing that would break running those 2 commands.

I have made reasonable assumptions for what values are in the $USER and $HOME environment variables.  On every Ubuntu release I've seen over the last 15+ yrs, this has worked.

Of course, whether samba works or not is a different question.  Perhaps it would be better to "pull" the data from Win7 using the Linux computer rather than "push" the data from Win7 into Ubuntu?  Just a thought.

---

### Post by MAFoElffen on 2023-11-13
I was thinking that maybe if in the Public folder, if you created a folder with permissions of KVM itself...
```

sudo chown virtlib-qemu:kvm /home/UserName/Public/WIN7

```
Then it wouldn't complain about a VM writing to it. Because it shares the group permissions...

But a lot of things changed between KVM versions 5 and 6, on pass-through filesystems, with 5 having different options altogether than 6. They renanmed some of the drivers... And Windows 7 only supports a few things as an OS, so I tricked both...

I abandoned using filesystem pass-through from within livirtd and went outside the box... The trick is, think "Block Devices" and volume managers. LMFAO!!!

@TheFu -- You are both going to love and hate this at the same time... But it is very simple.

I created a nested KVM VM as my 20.04 Host, so I could test this on both 20.04 and 22.04... That is not important at all. It doesn't matter that it's nested. It is just a test case that I could destroy later. So I will just refer to the nested Host as "the host".

On the KVM Host, I created an LVM VG Storage pool, Named vg-data. I added that volume to a KVM Storage pool of type lvm2, Named "LVM_Pool".

Within that KVM storage pool, I created a 20G LV, named "lv_share2".

In add hardware for that Win7 guest, I added a storage disk.

I started up that Win7 VM Guest and started up Storage Management. It recognized the new disk, and asked if I wanted to initialize it (add a partition table). I said yes, and added a GPT partition table. I formatted it (NTFS).

I added some sample files to it...

Then I went back to the host and opened a terminal. I became root and looked for the LV's
```

sudo su -

lvscan
#  ACTIVE            '/dev/vgubuntu/root' [118.53 GiB] inherit
#  ACTIVE            '/dev/vgubuntu/swap_1' [976.00 MiB] inherit
#  ACTIVE            '/dev/vg-data/lv_share2' [20.00 GiB] inherit

ls /dev/mapper
#control  vg--data-lv_share2  vgubuntu-root  vgubuntu-swap_1
lsblk -e7 -f
#NAME FSTYPE LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINT
#sda                                                                    
#&#9492;&#9472;sda1
#     LVM2_m       EaE9Ne-sobe-kKyy-iY63-7zPx-IPRu-s5X2Bc                
#  &#9500;&#9472;vg--data-LV_Share
#  &#9474;                                                                    
#  &#9492;&#9472;vg--data-lv_share2
#sdb                                                                    
#&#9500;&#9472;sdb1
#&#9474;    vfat         08D5-5234                               504.9M     1% /boot/efi
#&#9492;&#9472;sdb2
#     LVM2_m       d5y4Q3-wfTa-YlBG-DAnp-krvy-L8qV-lTzO1P                
#  &#9500;&#9472;vgubuntu-root
#  &#9474;  ext4         9cf940b1-9a7d-4649-88a4-123b7863a077     83.3G    23% /
#  &#9492;&#9472;vgubuntu-swap_1
#     swap         3a2b7e3a-2aab-49e4-9bef-445b1791870f                  [SWAP]
#sr0  iso966 Ubuntu 20.04.6 LTS amd64
#                  2023-03-16-15-57-27-00                       0   100% /media/maf

```
Then I premounted the lv image with 'kpartx'. That is a utility to mount image devices as a block device. You might have to install that (not a default).
```

kpartx -av /dev/vg-data/lv_share2
#add map vg--data-lv_share2p2 (253:5): 0 41676800 linear 253:3 264192

lsblk -e7 -f
#NAME FSTYPE LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINT
#sda                                                                     
#&#9492;&#9472;sda1
#     LVM2_m       EaE9Ne-sobe-kKyy-iY63-7zPx-IPRu-s5X2Bc                
#  &#9500;&#9472;vg--data-LV_Share
#  &#9474;                                                                     
#  &#9492;&#9472;vg--data-lv_share2
#                                                                       
#    &#9492;&#9472;vg--data-lv_share2p2
#       ntfs   New Volume
#                    84A830DEA830D082                                      
#sdb                                                                     
#&#9500;&#9472;sdb1
#&#9474;    vfat         08D5-5234                               504.9M     1% /boot/efi
#&#9492;&#9472;sdb2
#     LVM2_m       d5y4Q3-wfTa-YlBG-DAnp-krvy-L8qV-lTzO1P                
#  &#9500;&#9472;vgubuntu-root
#  &#9474;  ext4         9cf940b1-9a7d-4649-88a4-123b7863a077     83.3G    23% /
#  &#9492;&#9472;vgubuntu-swap_1
#     swap         3a2b7e3a-2aab-49e4-9bef-445b1791870f                  [SWAP]
#sr0  iso966 Ubuntu 20.04.6 LTS amd64
#                  2023-03-16-15-57-27-00                       0   100% /media/maf

```
Then I mounted the UUID of the filesystem within the partition of the image
```

mount -t -o defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw UUID=84A830DEA830D082 /mnt
ls /home/mafoelffen/Public/WIN7
#SampleFile1.txt.txt  SampleFile2.txt.txt  SampleFile3.txt.txt

```
Then I checked in nautilis of the host and everything was there in that folder. I was able to open and save files, etc...

I created this script, saved it to my ~/Scripts folder as MountWin7 and made it executable
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,20231113
#  |  Mount KVM LVM VM Storage device in Host...
#  |  Called by /lib/systemd/system/pre-graphical.service

sudo kpartx -av /dev/vg-data/lv_share2
sudo mount -t ntfs -o defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw UUID=84A830DEA830D082 /home/mafoelffen/Public/WIN7

```
Made it exectuable via
```

chmod +x .~/Scripts/MountWIN7
That script alone, will mount the vm shared resource if you run it via sudo. I wanted to autmount it on the start of the host, by a service... So I created pre-graphical.target, but, it didn't work. It would mount it, then unmount it right after that... Smae haapened ifI added it to the ~/.bashrc...

But it does mount fine it ran manuall after you login in to your account. 

To unmount it, I created this script, named "UnmountWIN7".
[code]
#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,20231113
# Unmount KVM LVM VM Storage device from Host...

sudo umount /home/mafoelffen/Public/WIN7
sudo kpartx -dv /dev/vg-data/lv_share2
[code]
Mmade it executable
[code]
chmod +x ~/Scripts/UnmountWIN7

```
I add my Scripts folder to my path lke this at the end of $HOME/.profile
```

# set PATH so it includes user's private Script if it exists
if [ -d "$HOME/Scripts" ] ; then
    PATH="$HOME/Scripts:$PATH"
fi

```
I tried it with KVM ZFS dataset storage Volumes, works with that to, but mount it to the Host as an import/export in the script. Updated it to 22.04... works great there also.  

So no buggy modules to worry about. No tricky filesystem passthrough options, just treating thinks as a Block Device.

Have fun!

---

### Post by MAFoElffen on 2023-11-13
I was thinking that maybe if in the Public folder, if you created a folder with permissions of KVM itself...
```

sudo chown virtlib-qemu:kvm /home/UserName/Public/WIN7

```
Then it wouldn't complain about a VM writing to it. Because it shares the group permissions...

But a lot of things changed between KVM versions 5 and 6, on pass-through filesystems, with 5 having different options altogether than 6. They renanmed some of the drivers... And Windows 7 only supports a few things as an OS, so I tricked both...

I abandoned using filesystem pass-through from within livirtd and went outside the box... The trick is, think "Block Devices" and volume managers. LMFAO!!!

@TheFu -- You are both going to love and hate this at the same time... But it is very simple.

I created a nested KVM VM as my 20.04 Host, so I could test this on both 20.04 and 22.04... That is not important at all. It doesn't matter that it's nested. It is just a test case that I could destroy later. So I will just refer to the nested Host as "the host".

On the KVM Host, I created an LVM VG Storage pool, Named vg-data. I added that volume to a KVM Storage pool of type lvm2, Named "LVM_Pool".

Within that KVM storage pool, I created a 20G LV, named "lv_share2".

In add hardware for that Win7 guest, I added a storage disk.

I started up that Win7 VM Guest and started up Storage Management. It recognized the new disk, and asked if I wanted to initialize it (add a partition table). I said yes, and added a GPT partition table. I formatted it (NTFS).

I added some sample files to it...

Then I went back to the host and opened a terminal. I became root and looked for the LV's
```

sudo su -

lvscan
#  ACTIVE            '/dev/vgubuntu/root' [118.53 GiB] inherit
#  ACTIVE            '/dev/vgubuntu/swap_1' [976.00 MiB] inherit
#  ACTIVE            '/dev/vg-data/lv_share2' [20.00 GiB] inherit

ls /dev/mapper
#control  vg--data-lv_share2  vgubuntu-root  vgubuntu-swap_1
lsblk -e7 -f
#NAME FSTYPE LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINT
#sda                                                                    
#&#9492;&#9472;sda1
#     LVM2_m       EaE9Ne-sobe-kKyy-iY63-7zPx-IPRu-s5X2Bc                
#  &#9500;&#9472;vg--data-LV_Share
#  &#9474;                                                                    
#  &#9492;&#9472;vg--data-lv_share2
#sdb                                                                    
#&#9500;&#9472;sdb1
#&#9474;    vfat         08D5-5234                               504.9M     1% /boot/efi
#&#9492;&#9472;sdb2
#     LVM2_m       d5y4Q3-wfTa-YlBG-DAnp-krvy-L8qV-lTzO1P                
#  &#9500;&#9472;vgubuntu-root
#  &#9474;  ext4         9cf940b1-9a7d-4649-88a4-123b7863a077     83.3G    23% /
#  &#9492;&#9472;vgubuntu-swap_1
#     swap         3a2b7e3a-2aab-49e4-9bef-445b1791870f                  [SWAP]
#sr0  iso966 Ubuntu 20.04.6 LTS amd64
#                  2023-03-16-15-57-27-00                       0   100% /media/maf

```
Then I premounted the lv image with 'kpartx'. That is a utility to mount image devices as a block device. You might have to install that (not a default).
```

kpartx -av /dev/vg-data/lv_share2
#add map vg--data-lv_share2p2 (253:5): 0 41676800 linear 253:3 264192

lsblk -e7 -f
#NAME FSTYPE LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINT
#sda                                                                     
#&#9492;&#9472;sda1
#     LVM2_m       EaE9Ne-sobe-kKyy-iY63-7zPx-IPRu-s5X2Bc                
#  &#9500;&#9472;vg--data-LV_Share
#  &#9474;                                                                     
#  &#9492;&#9472;vg--data-lv_share2
#                                                                       
#    &#9492;&#9472;vg--data-lv_share2p2
#       ntfs   New Volume
#                    84A830DEA830D082                                      
#sdb                                                                     
#&#9500;&#9472;sdb1
#&#9474;    vfat         08D5-5234                               504.9M     1% /boot/efi
#&#9492;&#9472;sdb2
#     LVM2_m       d5y4Q3-wfTa-YlBG-DAnp-krvy-L8qV-lTzO1P                
#  &#9500;&#9472;vgubuntu-root
#  &#9474;  ext4         9cf940b1-9a7d-4649-88a4-123b7863a077     83.3G    23% /
#  &#9492;&#9472;vgubuntu-swap_1
#     swap         3a2b7e3a-2aab-49e4-9bef-445b1791870f                  [SWAP]
#sr0  iso966 Ubuntu 20.04.6 LTS amd64
#                  2023-03-16-15-57-27-00                       0   100% /media/maf

```
Then I mounted the UUID of the filesystem within the partition of the image
```

mount -t -o defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw UUID=84A830DEA830D082 /mnt
ls /home/mafoelffen/Public/WIN7
#SampleFile1.txt.txt  SampleFile2.txt.txt  SampleFile3.txt.txt

```
Then I checked in nautilis of the host and everything was there in that folder. I was able to open and save files, etc...

I created this script, saved it to my ~/Scripts folder as MountWin7 and made it executable
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,20231113
#  |  Mount KVM LVM VM Storage device in Host...
#  |  Called by /lib/systemd/system/pre-graphical.service

sudo kpartx -av /dev/vg-data/lv_share2
sudo mount -t ntfs -o defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw UUID=84A830DEA830D082 /home/mafoelffen/Public/WIN7

```
Made it exectuable via
```

chmod +x .~/Scripts/MountWIN7

```
That script alone, will mount the vm shared resource if you run it. I wanted to autmount it on the start of the host, by a service... So I created pre-graphical.target, but, it didn't work. It would mount it, then unmount it right after that... Smae haapened ifI added it to the ~/.bashrc...

But it does mount fine it ran manuall after you login in to your account. 

To unmount it, I created this script, named "UnmountWIN7".
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,20231113
# Unmount KVM LVM VM Storage device from Host...

sudo umount /home/mafoelffen/Public/WIN7
sudo kpartx -dv /dev/vg-data/lv_share2

```
Made it executable
```

chmod +x ~/Scripts/UnmountWIN7

```
I add from my Scripts folder to my path like this at the end of $HOME/.profile
```

# set PATH so it includes user's private Script if it exists
if [ -d "$HOME/Scripts" ] ; then
    PATH="$HOME/Scripts:$PATH"
fi

```
I tried it with KVM ZFS Dataset Storage Volumes, works with that to, but mount it to the Host as an import/export in the script. Updated it to 22.04... works great there also. Also worked for raw and qcow2 volume, with just other mount options...  

You do not need to create a special disk just for sharing. You could set up the whole VM image that it is installed on as shared, it you wanted, but I thought that would be messy to weed through... Rather, i created a shard space common to both, as if they were separate computers.

So no buggy modules to worry about. No tricky filesystem pass-through options, just treating things as a Block Device.

Have fun!

---

### Post by ironhand42 on 2023-11-18
Yes, I did set up a Samba server. It works fine except I followed some bad advice and used "nobody" as the owner. So my files from Windows (guest) when they get to my "Public" folder in Ubuntu (host) are owned by "nobody". But chown and chmod give me back ownership of the transferred files, just that I have to keep repeating the commands because new files transferred from Win7 to Ubuntu still end up owned by "nobody." I think I'll create a new folder to do transfers between client and host and just delete "Public." To soon we get old, too late we get smart!

---

### Post by ironhand42 on 2023-11-18
I did set up a shared folder with Samba. But I took some bad advice and files I create in Win7 and then drop into a shared folder "Public" end up owned by "nobody" in Ubuntu. I'm going to create another shared folder and delete "Public", my current shared folder. One step forward, two steps backwards.

---

### Post by ironhand42 on 2023-11-18
MAFoElffen--When I was first trying to set up a shared folder rant a few trials and created one shared folder with owner libvert-qemu-Libvert Qemu and group "richard" I think I'll tinker with that shared folder to see if I can make it work. As for Block Device I have no clue what that is and would have to spend another week figuring it out. As you can tell, I'm not an IT person. I did research before retiring and can do many things on a computer, but networking is mostly Greek to me.

---

### Post by ironhand42 on 2023-11-18
Thanks The Fu. Your two commands worked for me. I didn't know that putting a $ sign before a folder was an instruction to Ubuntu to "don't bother me with cd..ing around to find a particular folder; you find it and implement the previous command." Handy shortcut!

---

### Post by MAFoElffen on 2023-11-18
> **ironhand42 said:**
> MAFoElffen--When I was first trying to set up a shared folder rant a few trials and created one shared folder with owner libvert-qemu-Libvert Qemu and group "richard" I think I'll tinker with that shared folder to see if I can make it work. As for Block Device I have no clue what that is and would have to spend another week figuring it out. As you can tell, I'm not an IT person. I did research before retiring and can do many things on a computer, but networking is mostly Greek to me.
Treating it as a block device... Treating a file, volume manager volume or partition as the same thing. Block devices write to hardware in blocks of data. That "hardware" can be thought of in an abstract, loose kind of manner. the advantage of treating all devices like files in Linux? There is this advantage of Linux treating all devices like files in Unix in that it provides a uniform interface for I/O on Unix systems. Programs written to manage files will also work to manage devices, and vice versa.

If you can mount any storage device as a disk to KVM, whether it is a partition (raw), a file (raw or qcow2), a storage container of a volume manager (ZFS dataset, LVM LV), etc... You can use a utility call 'kpartx' to read the partition table that resides in it, and use that information to mount of to a Linux filesystem.

My example was with an LVM LV. But that could have been any type of storage container mounted to a VM as a mounted disk, whether that VM disk was the only disk (that the VM Guess is installed on), or a disk mounted to that VM as a go-between.

You can add a physical disk or partition to a KVM VM Guest as a storage device. You do Add Hardware > Add Storage Pool > Give it a name, type physical disk, and use the /dev/disk/by-id/<disk_name> in the path field. That will pass-through the whole disk as a virtual block device. Then you need nothing special on the host side of that, by it is truly a physical disk.

---

### Post by TheFu on 2023-11-18
> **ironhand42 said:**
> Thanks The Fu. Your two commands worked for me. I didn't know that putting a $ sign before a folder was an instruction to Ubuntu to "don't bother me with cd..ing around to find a particular folder; you find it and implement the previous command." Handy shortcut!

**_That isn't what a $ does.  _**

You should forget what you wrote above and learn about environment variables. That's what is happening.  BTW, MS-Windows works similarly with environment variables, but uses the %var instead.  All Unix-like OSes use $var and some scripting languages do as well for their variables.

---

### Post by ironhand42 on 2023-12-03
Ok. I'll forget that tip The Fu but that brings me back to square one. Ubuntu still tells me I don't have permission to open files  I create in Win 7 and move to my Ubuntu desktop via a shared folder. I'm going to post another question on this forum but this time I'll back up all the way to "how to create a shared folder between Unbuntu (host) and win7 (client) and retain **complete ownership** of said files." But thanks to all of you for trying to help me.

---

### Post by MAFoElffen on 2023-12-04
Be sure to include that the Win7 you are referring to is a VM. If you were using Win8 or newer VM Guest, you would have more options open to you. But you are not.

For more exposure for that new thread, I would recommend that you post it in the Virtualization Section. Both TheFu and I watch that section closely, along with others there who specialize and have a passion for Virtualization subjects and issues.

---

### Post by Morbius1 on 2023-12-04
> **ironhand42 said:**
> Ubuntu still tells me I don't have permission to open files  I create in Win 7 and move to my Ubuntu desktop via a shared folder. I'm going to post another question on this forum but this time I'll back up all the way to "how to create a shared folder between Unbuntu (host) and win7 (client) and retain **complete ownership** of said files." But thanks to all of you for trying to help me.
> I did set up a shared folder with Samba. But I took some bad advice and files I create in Win7 and then drop into a shared folder "Public" end up owned by "nobody" in Ubuntu. I'm going to create another shared folder and delete "Public", my current shared folder. One step forward, two steps backwards. 

So as not to interfere with any other shared folders you may have set I propose setting up a new folder to share and share that one.

Create a new "Public2" folder:
```
sudo mkdir -p /srv/Public2
```
Change ownership to you:
```
sudo chown morbius /srv/Public2
```
Edit /etc/samba/smb.conf and at the bottom of the file add a new share definition that looks like this:
```
[Public2]
path = /srv/Public2
read only = no
force user = morbius
guest ok = yes

```
Restart smbd:
```
sudo service smbd restart
```

**[COLOR="#0000FF"]Change morbius above to your Ubuntu login user name.[/COLOR]**

*[COLOR="#FF0000"]We can make this far more complicated if you wish and depending on your total use case for this share we may have to but for now see if the above does all that you want.[/COLOR]*

*[COLOR="#FF0000"]One more note[/COLOR]*: Most of the Howto's on the internet regarding Samba are wrong. The official HowTo in the Ubuntu documentation is wrong. So depending on what advice you followed if you have more difficulties I suggest you tell us how you are set up. 

You can do that by posting the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

