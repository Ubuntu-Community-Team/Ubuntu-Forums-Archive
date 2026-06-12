---
title: "Using nvidia drivers on a Lucid live CD"
date: 2010-12-14
forum: Outdated Tutorials &amp; Tips
---

### Post by amsterdamharu on 2010-12-14
[SIZE=3][COLOR=Red]You need:[/COLOR][/SIZE]

[LIST=1]
[*]About 1G usb stick
[*]A computer that can boot off that stick
[*]I got the mint iso "linuxmint-9-gnome-cd-i386.iso" but the i386 Lucid iso would work just the same I assume
[*]About 4G of free space
[*]A working Linux (I used mint 8) kernel is importaint for re  creating the squasfs but not sure what version is needed but 9.04 or  9.10 Ubuntu would work just as well.
[*]A computer with an nvidia graphics card that has working drivers for it.
[*]I assume all the commands are executed when logged in as a normal user that can execute sudo.
[/LIST]
 
[SIZE=3][COLOR=Red]Install the programs we need:[/COLOR][/SIZE]
```
sudo apt-get install unetbootin squashfs-tools
```[SIZE=3][COLOR=Red]Make bootable iso with Lucid[/COLOR][/SIZE]
Now we get the iso file on your usb, 
Plug in a fat32 formatted usb drive (todo: maybe give the commands to do so here)
press alt + F2 and type unetbootin
After filling out your password it should show the unetbootin window
Check "Diskimage" ->  the ... button next to "diskimage" all the way  on the right -> browse to where the iso is and select it -> in the  bottom middle you should see your usb drive (mine is called /dev/sdb1)  -> click OK.
After it is done extracting the iso files to usb and making it bootable it will ask you to restart, you can do so.

[SIZE=3][COLOR=Red]Booting up the usb Lucid (first time)[/COLOR][/SIZE]
I assume it will boot up as the live CD, if it doesn't you might check  your bios settings for usb boot settings. Most laptops have F1 or F9 to  go to a boot menu, my desktop has escape to go to boot menu. Some  computers have no boot menu and you have to check bios settings for boot  order.
When it is done booting it might give you an error that low graphics  mode is selected, click ok and choose "restart x" (not sure if this is a  Mint thing or Ubuntu)
Now that you see your desktop you can wait a while and a message will  pop up saying that you can install drivers for your videocard, do this  but when it's done **don't reboot**.

[SIZE=3][COLOR=Red]Copy the nvidia deb driver packages to your local system[/COLOR][/SIZE]
After it's installed copy the deb files to your local system.
For smarties you have to copy the deb files in /var/cache/apt/archive to  (your local system)/home/your_user/temp/nvidia (all lower case)
More help: open nautilus (the file browser) and mount the home folder of  your installed system (the old mint 8 or Ubuntu 9.04 9.10 on your  harddisk). To do this you can click on the monitor icon on the top of  the nautilus screen. Here are listings like "160 20GB Hard Disk 87GB  filesystem" this happens to be my home so I double click on it which  mounts it.
Press alt + F2 and type 
```
gksu nautilus
```Now you have nautilus as root, on the left  side is the mounted local filesystem (now called a very long number  which is the guid). Click on it and browse to the home of your locally  installed system (the home of the user you usually log in with). Create a  folder in your home called temp (lover case) -> in this folder  create a folder named nvidia open this folder.
On the left side of the window is a clickable item named "File system"  right click and choose "open in new tab" now browse to  /var/cache/apt/archive and select all the files ending with .deb ->  press control + c to copy -> go to the other tab having your local  file systems home/youruser/temp/nvidia dir and paste the debs in there.
(Todo: use "sudo nvidia-xconfig" to create an /etc/X11/xorg.conf and put  that in the chrooted squashfs under /etc/X11/xorg.conf )

[SIZE=3][COLOR=Red]Re configure the squashfs[/COLOR][/SIZE]
Now you can reboot your system and boot in your mint 8/ubuntu 9.04/9.10. 
First we get the filesystem.squashfs, it is on your usb driver under the  casper directory, copy that to your home under temp/sqfs (create sqfs  directory under temp).
Open up a terminal and type the following command (this will take some time to complete):
```
sudo cd ~/temp/sqfs
sudo unsquashfs filesystem.squashfs

```After that's done you can type something like sudo ls, it's just to let  it ask for your password so the following commands can complete without  asking. Soon after that copy and paste the following commands (you can  copy all the lines at once not line for line) in the terminal you just  unsquased the squashfs and typed a sudo command in:
```
sudo cp ../nvidia/*.deb /var/cache/apt/archives/
sudo cp /etc/resolv.conf squashfs-root/etc/
sudo cp /etc/hosts squashfs-root/etc/
sudo mount --bind /dev/ squashfs-root/dev
sudo chroot squashfs-root # squashfs-root is the name of the extracted squashfs root dir
mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts
export HOME=/root
export LC_ALL=C
dbus-uuidgen > /var/lib/dbus/machine-id
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get install nvidia-current nvidia-settings

```That installed the nvidia drivers (chroot means the terminal is running  the squashfs Lucid/mint 9 system not the locally installed system).
If you wish you could install some other things with apt-get like  "apt-get install ffmpeg" but this is optional and the more you install  the more space you'll need on the usb.
Time to clean up and re-create the squashfs file; copy and paste the following commands:
```
aptitude clean
rm -rf /tmp/* ~/.bash_history
rm /etc/resolv.conf
rm /etc/hosts
rm /var/lib/dbus/machine-id
rm /sbin/initctl
dpkg-divert --rename --remove /sbin/initctl
umount /proc # if this doesn't work try umount -lf /proc
umount /sys
umount /dev/pts
exit[code]
And at last one more command:
[code]sudo umount squashfs-root/dev
```Now re create the squashfs, do replace myuser with your user (this will take a while):
```
sudo mksquashfs squashfs-root new_filesystem.squashfs 
sudo chown myuser:myuser new_filesystem.squashfs 
```[SIZE=3][COLOR=Red]Create a cd directory to be used for the iso later[/COLOR][/SIZE]
Copy all the files from the Lucid or Mint iso file (I use linuxmint-9-gnome-cd-i386.iso) to ~/cd (including the hidden ones). 
To do this you can open a file browser and browse to the iso file, right  click it and open with archive mounter -> in the left the iso is  mounted as a cd click on it and you'll see the contents -> press  control + h (there are hidden files on the cd that will show now) ->  press control + c -> go to your home folder and create a folder named  cd (lower case) -> go in this folder and press control + v

[SIZE=3][COLOR=Red]Edit the start menu of the CD so nouveau drivers aren't loaded (they block nvidia)[/COLOR][/SIZE]
 Go to the cd directory in your home folder and locate the file called  isolinux.cfg (it is in your home/cd/isolinux directory). Open this up in  a text editor. For Mint 9 you will see the following line:
```
  append  file= .....
```Replace this line with:
```
  append  file=/cdrom/preseed/mint.seed boot=casper  initrd=/casper/initrd.lz nouveau.modeset=0 rdblacklist=nouveau  blacklist=vga16fb nouveau.noaccel=1 --
```Save the file.

[SIZE=3][COLOR=Red]Create a bootable iso[/COLOR][/SIZE]
Open a terminal and copy and paste the following commands:
```
cd ~
rm cd/casper/filesystem.squashfs
cp temp/sqfs/new_filesystem.squashfs cd/casper/filesystem.squashfs
mkisofs -pad -l -r -J -v -V "Ubuntu nvidia" -no-emul-boot  -boot-load-size 4 -boot-info-table -b isolinux/isolinux.bin  -hide-rr-moved -o boot.iso cd
```
[SIZE=3][COLOR=Red]Create bootable usb with changed squashfs and boot menu.[/COLOR][/SIZE]
Now we get the iso file on your usb, 
 Plug in a fat32 formatted usb drive (todo: maybe give the commands to do so here)
 press alt + F2 and type unetbootin
 After filling out your password it should show the unetbootin window
 Check "Diskimage" ->  the ... button next to "diskimage" all the way  on the right -> **[COLOR=Red]browse to your home folder and select boot.iso[/COLOR]** -> in the  bottom middle you should see your usb drive (mine is called /dev/sdb1)  -> click OK.
**[SIZE=1][COLOR=Red]It will ask you to overwrite select all[/COLOR][/SIZE]**. After it is done extracting the iso files to usb and making it bootable it will ask you to restart, you can do so.


If you don't get a desktop at first press control + alt + F1 and type the following commands:
```
sudo nvidia-xconfig
sudo service gdm stop
 sudo service gdm start
```This is because I haven't got time yet to update this manual and put the  xorg.conf in the chrooted system before re creating the squashfs.


If you have any questions please don't hesitate to ask them, the only stupid question is a question unasked.

---

