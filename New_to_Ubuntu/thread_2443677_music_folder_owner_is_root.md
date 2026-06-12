---
title: "music folder owner is root"
date: 2020-05-18
forum: New to Ubuntu
---

### Post by jostman on 2020-05-18
Hi,  I am (very) new to Ubuntu.  My pc (windows 7) has three HDD.  Windows and Ubuntu are On the same drive. on one of the other drives is a folder called Music. You can tell what it contains. This is backed up to the third disk.  I have mounted the disk with the music folder on. Logitech Media server can see it as can My media for Alexa and Rhytmbox.  When in Windows I use Media Monkey to organise my music, (check tags, add artwork, that sort of thing).  I don't think Rhytmbox is up to this.  I thought Clemantine would be better but can not put my music into it.  I think it wants me to make a new folder and copy my music to this new folder.  There would be no point to this as any edits I make would only be to a copy and I would have three music folders.  I think my problem may be to do with ownership of the music folder.  While I own it in Windows in Ubuntu Root owns it. The disks mount option is set to auto.  Do I need to turn off nosid?  I copied one album to a USB hdd and in Ubuntu I was the owner, I put thie into a new folder on the hdd it came from and the owner reverted to root?  Sorry, long question.  Thank you for reading.
:confused:

---

### Post by daniewicz on 2020-05-18
install the package nautilus-admin. This will give you the right click open as administrator (root) option when using the file manager to view you music folder. Under properties you can change the permissions of the music folder. This changing of permissions can also be done from the command line but I thought this approach would be easier for you.

---

### Post by TheFu on 2020-05-18
Clementine can use files from anywhere last time i checked, provided the userid has access to those files based on the permissions.

What file system is the music on?  if it isn't a native linux file system, performance will usually suffer.
**df -Th** will show the file system for all mounted storage.
**lsblk** is handy for a big picture overview.

if specific mount options are needed, the normal way to control that is in the /etc/fstab mount for that storage.

For non-linux file systems, changing permissions cannot happen after it is mounted.  Permissions are controlled by mount options. That would apply to NTFS, FAT32, exFAT file systems.  Native file systems would include ext2, ext3, ext4, xfs, jfs, zfs, btrfs, f2fs, and probably 10 more.

---

### Post by jostman on 2020-05-19
Thanks daniewicz, I've installed nautilus-admin.
Also thank you TheFu. It may be my inexperience but I point Rhythembox to file:///mnt/EE4482AB4482765D/Music but Clementine only seams to see mnt.  With regard to file systems I think Ubuntu prefers Ext4? The music folder built when running Windows 7 will be NTFS.  When I ask df -Th it comes up as fuseblk? I also see I have used 172G out of 932G.  Should I make a ext4 partition and move the music folder to that? Not sure what lsblk is telling me? It says sdc1 8:33  0  931.5G  0  part /mnt/EE4482AB4482765D   Thanks again

---

### Post by dino99 on 2020-05-19
As 'music' is a windows folder, follow [https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/) to easily deal with these

---

### Post by jostman on 2020-05-19
> **dino99 said:**
> As 'music' is a windows folder, follow [https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/) to easily deal with these

Thank you dino99. i tried to follow this how to, but got a bit confused.  I am not sure that this would work anyway as Windows and Ubuntu are on the same pc.

---

### Post by jostman on 2020-05-19
if my windows pc is named differently to my Ubuntu pc would changing one of the names to match the other solve this? Or would different user names cause a problem?

---

### Post by Morbius1 on 2020-05-19
Please post the output of the following command:
```
cat /etc/fstab
```

---

### Post by jostman on 2020-05-19
> **Morbius1 said:**
> Please post the output of the following command:
```
cat /etc/fstab
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=efccb7e4-f816-41cc-95bf-a70ac8af92e0 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda5 during installation
UUID=3AF7-77D0  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-uuid/EE4482AB4482765D /mnt/EE4482AB4482765D auto nosuid,nodev,nofail,x-gvfs-show 0 0

---

### Post by Morbius1 on 2020-05-19
[1] Find your uid number by running this command:
```
id
```
[2] Unmount the partition:
```
sudo umount /mnt/EE4482AB4482765D
```
[3] Change this:
> /dev/disk/by-uuid/EE4482AB4482765D /mnt/EE4482AB4482765D auto nosuid,nodev,nofail,x-gvfs-show 0 0         
To this:
> /dev/disk/by-uuid/EE4482AB4482765D /mnt/EE4482AB4482765D auto nosuid,nodev,nofail,x-gvfs-show[COLOR=#ff0000]**,uid=1000**[/COLOR] 0 0         
[COLOR=#ff0000][I]change "1000" to the uid number you found in step [1]

[/I][/COLOR][4] Remount with this command:
```
sudo mount -a
```
This will change ownership from root to you.

If you need to change the group you can add the "gid" option. For example:
> /dev/disk/by-uuid/EE4482AB4482765D /mnt/EE4482AB4482765D auto nosuid,nodev,nofail,x-gvfs-show[COLOR=#ff0000]**,uid=1000,gid=1000**[/COLOR] 0 0         

---

### Post by ActionParsnip on 2020-05-19
Check your mount options to make it user accessible. If its a Windows file system then this will need to happen

---

### Post by jostman on 2020-05-19
Sorry, bit dim. How do I do 3?

---

### Post by Morbius1 on 2020-05-19
If you are using Ubuntu:
```
sudo -H gedit /etc/fstab
```
If you are using some other desktop replace gedit with your text editor.

---

### Post by jostman on 2020-05-19
Thank you Morbius1 I am now the owner and have changed the folder to Share, it has a green blob on it.  I did get this message...(gedit:5631): Tepl-WARNING **: 14:24:33.596: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.
Any cause for concern?

---

### Post by TheFu on 2020-05-19
```
/dev/disk/by-uuid/EE4482AB4482765D /mnt/EE4482AB4482765D auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
is the mount. It appears to be an NTFS based on the UUID "style."

If the system is dual boot and the other OS is some sort of MS-Windows, then I'd leave this as NTFS and just solve the permissions and performance problems using mount options.

There might be new methods with 20.04 to automatically mount it with the current userid.  I don't know how to do that. Perhaps Morbius1 does?

The first userid created during the install of all Ubuntu systems has a uid=1000 and gid=1000. Use the 'id' command to check that. Assuming that is true for your userid, use **sudoedit /etc/fstab** to modify the 1 line at the bottom to be like this:
```
/dev/disk/by-uuid/EE4482AB4482765D /mnt/[COLOR="#0000FF"]Music[/COLOR] auto [COLOR="#0000FF"]uid=1000,gid=1000,big_writes,[/COLOR]nosuid,nodev,nofail,x-gvfs-show 0 0
```
All of that needs to be on 1 line. Don't let it wrap.  Comment out the original line.

Next, run **sudo mkdir /mnt/Music** followed by
**sudo systemctl daemon-reload**
and lastly run **sudo mount -a**

Now you should have /mnt/Music available under Linux for your userid to modify and with pretty ok performance.  If that fails to mount it, check for any errors - hopefully, you copied/pasted the line above - then reboot.  

Please, let us know.  I've been playing with the systemd.mount stuff the last few months and it usually works fine. Sometimes it seems to hiccup on local mount stuff, which may need the reboot to systemd.mount to re-re-read the fstab. Hopefully, the daemon-reload handles it.

Hope you don't mind the change from EE4482AB4482765D to "Music".  ;)

---

### Post by Morbius1 on 2020-05-19
> **jostman said:**
> Thank you Morbius1 I am now the owner and have changed the folder to Share, it has a green blob on it.  I did get this message...(gedit:5631): Tepl-WARNING **: 14:24:33.596: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.
Any cause for concern?
I don't know what you mean by "changed the folder to Share". Are you talking about Local Network Share? That is for sharing a folder between different physical machines not different operating systems on the same machine.

---

### Post by jostman on 2020-05-19
Thanks again, I did the stuff TheFu suggested.  I am not used to Clementine. If I open Music folder and right click on a track I can open with Rhythmbox. If I try to open with Clementine I get this....  Error loading file:///mnt/Music/Music/80s' - Retro Disco Coctail-[Tifon]/Disco Bouzouki Band - Disco Bouzouki.mp3

---

### Post by TheFu on 2020-05-19
**Clementine** has to read the files and create a library, doesn't it?  That's usually the first step.  

I use **cmus** which also needs to scan directories and build a library, but I'm a minimalist and don't want a GUI just to play music in the background. The program is a little odd for people used to mousing and buttons.

If you want a player that just plays media files, use something like mpv or vlc. Those can be connected to the file manager you use, if you like. Also, they support m3u playlists, which are trivial to create using 'find'.

Does clementine not play any files under the /mnt/Music or just the file with odd characters?  That difference would be important.  I just moved desktops a few weeks ago and decided against bringing clementine to the new system.

BTW, if you like, the fstab line can be shorter by changing:
```
/dev/disk/by-uuid/EE4482AB4482765D 
```
into 
```
UUID=EE4482AB4482765D
```
The /dev/disk/.... method is new to 20.04 as far as I know. The UUID= method has been used about 15 yrs, perhaps longer.  No need to change it unless the line wrap bothers you and the slightly shorter method makes enough difference.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) has more info if you _want_ to know a little more. Might want to setup fmask and dmask options.  Up to you.

I did some reading today about ways to avoid having to enter the uid/gid parameters and didn't see a way that would automatically mount the partition at boot. There is a way to mount using the mount command, however.  This would probably work via GUI mounts too.  I don't know how this works if you ever boot the machine with the NTFS partition disconnected/missing.  Perhaps the no-fail option would be useful?

Many file systems support tuning parameters in the mount options too. The big_writes option is for NTFS only.  For something that seems so simple, it does get complex pretty quick.

---

### Post by jostman on 2020-05-19
Re Music players in Windows (and on my Mac) I used itunes. You could edit the files in itunes, but it kept needing updates and is quit large and resorce heavy. So I switched to Media Monkey. I don't use it to play music much but use it to keep the music folder organised.  I reboot into Windows to do this with Media Monkey but would like to stop using Windows.  Sadly no Media Monkey for Linux.  I think my problem is I don't know how to get Clementine to see my music.  I mostly listen to my music files on Squeeze boxes or Alexa devices.

---

### Post by Morbius1 on 2020-05-19
You seem to be doing whatever the last person who responds suggests. Since I will never know what state you are in in any given moment I suspect the root cause of this problem: 
> If I open Music folder and right click on a track I can open with  Rhythmbox. If I try to open with  I get this....  Error 

Is because Rhythmbox comes from the normal Ubuntu repositories whereas Clementine is downloaded as a snap.

Google is your friend here. Good Luck.

---

### Post by TheFu on 2020-05-19
For music organization, I use **easytag** and follow the genre/artist/album/NN-Title.xxx method.  Easytag can take the directory structure and create id3 tags or it can take the id3 tags and create the directory structure.

If clementine is a snap, you can check that using **snap list**.  I'm not a fan of snaps that limit any media access for programs that routinely access videos, audio files, images.  Hopefully the clementine snap creator allows access to other areas. There is a command, something like:
```
snap connect clementine:removable-media
```
Hopefully, that will work.  If the package allows the removable-media connection, then any storage under /mnt/ or /media/ should be accessible.

It is worth reading whatever Morbius1 writes.  I didn't see his post when I wrote my how-to-mount post.

---

### Post by jostman on 2020-05-19
> **Morbius1 said:**
> You seem to be doing whatever the last person who responds suggests. Since I will never know what state you are in in any given moment I suspect the root cause of this problem: 

Is because Rhythmbox comes from the normal Ubuntu repositories whereas Clementine is downloaded as a snap.

Google is your friend here. Good Luck.

Sorry Morbius, I did not intend to upset you,  just willing to accept help from people who know more than me.

---

### Post by jostman on 2020-05-19
> **TheFu said:**
> For music organization, I use **easytag** and follow the genre/artist/album/NN-Title.xxx method.  Easytag can take the directory structure and create id3 tags or it can take the id3 tags and create the directory structure.

If clementine is a snap, you can check that using **snap list**.  I'm not a fan of snaps that limit any media access for programs that routinely access videos, audio files, images.  Hopefully the clementine snap creator allows access to other areas. There is a command, something like:
```
snap connect clementine:removable-media
```
Hopefully, that will work.  If the package allows the removable-media connection, then any storage under /mnt/ or /media/ should be accessible.

It is worth reading whatever Morbius1 writes.  I didn't see his post when I wrote my how-to-mount post.

I have been reading everything Morbius1 writes, he seams to be in a grump because I did what you suggested.  I can see his point, though it is not as if I don't believe him.

---

### Post by jostman on 2020-05-22
Many thanks to everyone who offered help, esp. Morbius and the Fu.  The last suggestion "
snap connect clementine:removable-media" allowed clementine to populate the library.  Problem sorted, thank you folks

---

### Post by TheFu on 2020-05-22
IF solved, please use the THREAD TOOLS button above the first post to help the community. Stops people from wasting their time.

---

