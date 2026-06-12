---
title: "Edgy Howto drive sharing Kubuntu and Windows"
date: 2007-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2007-02-17
This will most probably work on other versions, but I only tested it on Kubuntu Edgy.

                                                     [COLOR=#000000][SIZE=3]_Edgy Howto share folders and drives between Windows and linux PC's on Kubuntu_[/SIZE][/COLOR]
 

 If you want to share a drive or a folder between Windows and Kubuntu on a dual boot PC (easiest) or separate Kubuntu and/or Windows PC some tricky setup has to be done. It is really not too complex, and this is just a basic guide so that you understand what you need to do and what you are doing in the next steps. It is not intended to be complete for every possible combination or situation. The security issues on linux is another encyclopedia on its own, so I have only dealt with a non secure situation which is most probably only useful for a home networking setup. Meaning that you will not be asked for passwords and verifications or be restricted on use of this shared folder. Once you have this working, you can consider a more secure environment for your files and change some configurations to prohibit or set certain access or permissions.


 Why would you want to share drives, folders or files? Lets assume you have two dual boot PC's connected to each other via a LAN cable and you would like to share the same Firefox and Thunderbird email and Internet profiles and you would like to have a common folder for all your data (documents, music, pictures, accounting data, etc.) and access this from any PC, then this is for you. It is quite possible to do this and the only  deciding factor is that one of your PC's must become the &#8220;server&#8221; and then contain this data and make it available to the other PC's connected to it. This PC must then always be on if you are working from any of the other ones, other than on a dual boot.  
 In this howto it is assumed that your gateway PC , the one that connects to the Internet will act as your server. On this server/gateway PC it will be necessary to create a FAT32 partition which is the most stable if used by both Windows and Linux. You will then move all your data that you would like to share in to this partition and enable sharing of this drive. From Windows on the same dual boot PC you will just see the extra drive and be able to use it, but to use it from Linux of the dual boot PC, the drive will need to be mounted first and certain permissions have to be looked at to allow reading and writing without asking for passwords and things. In addition for separate client PC's you also need to mount the server shared drive (on the server PC) on each separate client Linux PC  that needs to access these files. On separate Windows PC's you can just map the remote server drive to an unused local drive number on that PC.
 

 In Kubuntu you have an icon in the kicker bar that is called System Menu, from there you can go to Remote Places and Samba. This is a very good tool to use and check that your connected PC's can see any Samba shared files. For dual boot PC's the FAT32 partition should be visible in Storage Devices if sharing is enabled. When you intend sharing files it is going to save you a lot of running in circles if you can first get the file sharing working properly via Samba. Samba is actually used for Linux to Windows sharing, but also can share between Linux machines albeit not as fast as NFS. Once you have Samba running and sharing properly you can switch the Linux to Linux to use NFS which is much faster.
 

 Here goes:[LIST=1]
[*]Use     Synaptic/Adept and make sure that on the linux server PC you have     nfs-kernel-server, nfs-common and portmap installed for Linux to     allow sharing with other linux PC's using NFS.
[*]On     the linux client PC's make sure that portmap and nfs-common is     installed.
[*]To     enable sharing with Windows client PC's you need to also have samba,     samba-common, smbfs and smbclient installed on the linux server PC.
[*]Now     create your FAT32 partition on the server PC hdd. Here it is best to     use a good partition tool and there are many that can do this.     Acronis disk director is excellent and creates a bootable disk can     help you reduce your existing partitions to give you space for your     new FAT32 partition. There are excellent linux tools available as     well, but usually the best is to use a bootdisk when resizing     partitions. We will assume for explanatory purposes that the new     partition is /dev/hdb5 from here on.
[*]On     your server PC  create a folder called  /media/hdb5 which will     become your mountpoint.
[*]Now     mount the drive /dev/hdb5 to the mountpoint  in the server PC by     editing the /etc/fstab file and adding the 2 lines
# adding     mountpoint for hdb5 new FAT32 partition
/dev/hdb5  /media/hdb5      vfat  umask=000  0  1
[*]Now     reboot the server PC and check that the mounting takes place at boot     and that you can see the contents of the /media/hdb5 folder, which     should be the files that you what you want to share  in your hdb5     drive. You may only be able see any contents once the sharing has     been enabled in the next steps.
Enable Share with NFS
Under NFS Options enable Public and Writable
Under More NFS Options enable Public access and Writable
Then enable Share with Samba
Enter a sharename i.e. Serverhdb5   (or a name of your choice)
Enable Public and Writable
More Samba options, Name = Serverhdb5, enable Public, Browseable and Available.
Under users All Unspecified users = Allow
Remove any entries under Specified users (there is a root entry by default, remove this)
Force user and group &#8211; enter your userid in both
Security &#8211; Guest Access = nobody and leave Only allow Guest connections as NOT enabled.[/LIST][LIST=1]
[*]Now you should have a green check next to the sharing of the /dev/hdb5 drive for NFS and for Samba. Now reboot the server PC and thereafter the client PC's so that they can get to know each other better after the new settings.
[*]Now     open System menu,  and go to Storage media if you are on a dual boot     PC or remote Places if you are on a separate PC. On the Remote     Places you should open Samba shares, then Workgroup (or the actual     name of your workgroup). You should now see the name of the PC you     are using as server and the names of the other PC's that are     connected to it and on which sharing has been enabled. Here you     should now be able to see the mounted drive Serverhdb5 showing as     name of first PC  (i.e. kubuntu1).
Just a note here: If     you did any changes and did not reboot properly, first the server     and then the clients or if sharing is not properly set up then you     will not be able to see  every PC, usually not even your own. This     really only shows properly if the PC's are communicating over a     properly setup LAN and this is then only the Samba sharing part. If     this does not work properly go back, check and fix as you will just     get stuck if you carry on.
[*]Assuming     that you can now see the server PC called kubuntu1 as well as the     client PC called kubuntu2  on both the client and server PC's and     you can see the shared drive called Serverhdb5 on the the server PC     kubuntu1 then you can carry on. If not reboot again.
[*]Now     you need to create a mount point on each client PC and mount the     server shared drive to it. Create a folder /mnt/serverhdb5 on the     client PC.  (i.e. or any name of your choice)
[*] Now     manually mount the drive for testing purposes by typing 
sudo     mount 192.168.0.1:/media/hdb5 /mnt/serverhdb5     (the ip is your     server ip)
[*] You should now be able to see the contents of the     server shared drive in /mnt/serverhdb5.
[*]If     successful you can create a link (Icon) to your Desktop by dragging     and dropping it and selecting link when asked. This is optional and     only if you want to see the server shared drive as an icon on your     Desktop.
[*] You     will also find that you will now be able to access the drive from     OpenOffice etc. Before mounting it, this was not possible, even if     you could see it under Remote Places.
[*]Now     you need to edit the file /etc/fstab on the client PC to ensure that     the drive is mounted on each reboot. Add the following 2 lines:
#     Mounting serverhdb5 drive
192.168.0.1:/media/hdb5       /mnt/serverhdb5   nfs  rw  0  0
[*]Test     this by rebooting the client PC again.
[*]If     you have a firewall such as Firestarter you may have to deactivate     while doing this setup and reconfigure after all is working.[/LIST]This is only a very basic guide as there are thousands of howtos from every possible angle available that can take many hours to wade through before you start understanding what has to be done. I am not a linux fundi and will not be able to provide any answers as this is basically all I know and it may also not be the politically correct way of doing it. You are welcome to add anything in the forum thread that may help others or refer to other parts that have not been covered.

---

