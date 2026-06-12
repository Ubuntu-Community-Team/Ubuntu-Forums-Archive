---
title: "customize a certain liveCD manually"
date: 2008-07-08
forum: Other OS Talk
---

### Post by basenvironment on 2008-07-08
This method:
uses 'su' root account access not sudo.
requires a large amount of free disk space
has been used to create custom feisty-based ISOs
has been used to create custom heron-based ISOs
has been used to create custom debian sid based ISOS (change /casper/ to /live/ )


#create a directory to work in
[COLOR="Green"]mkdir work[/COLOR]

#change to work directory
[COLOR="Green"]cd work[/COLOR]

#change to root since some of the commands require root privys
[COLOR="Green"]su[/COLOR]

#unpack the ISO
[COLOR="Green"]mkdir iso
mkdir temp
mount iso_to_modify.iso -o loop temp/
cp -a temp/* iso/
umount temp/[/COLOR]

#Unpack the squash file system. This is the actual filesystem that is run when you use the livecd.
[COLOR="Green"]mount -t squashfs -o loop iso/casper/filesystem.squashfs temp/
mkdir fs
cp -a temp/* fs/
umount temp/
rm -rf temp/[/COLOR]

#remove the old squash from the iso since we will build a new one with our changes
[COLOR="Green"]rm iso/casper/filesystem.squashfs[/COLOR]

#copy a couple files related to network/internet access - skip this step if it is not needed
[COLOR="Green"]cp /etc/hosts fs/etc/
cp /etc/resolv.conf fs/etc/[/COLOR]

#mount dev, proc, etc
[COLOR="Green"]mount -t tmpfs --bind /dev/ fs/dev/
mount -t sysfs --bind /sys/ fs/sys/
mount -t proc --bind /proc/ fs/proc/
mount -t devpts --bind /dev/pts/ fs/dev/pts[/COLOR]

#change root to the extracted filesystem so we can work in it
[COLOR="Green"]chroot fs[/COLOR]

#export our locale thingy so we dont get irritating messages when we install software
[COLOR="Green"]export LC_ALL=C[/COLOR]

## add/remove software, edit files, etc...
[COLOR="Green"]aptitude install ....
nano file[/COLOR]

#exit the chroot back to our system
[COLOR="Green"]exit[/COLOR]

#unmount dev, proc, etc
[COLOR="Green"]umount fs/proc
umount fs/sys
umount fs/dev/pts
umount fs/dev[/COLOR]

#delete any temp files
[COLOR="Green"]rm -rf fs/tmp/*[/COLOR]

#remove those files from earlier, if needed - make some new empty ones, if needed
[COLOR="Green"]rm fs/etc/resolv.conf
rm fs/etc/hosts
touch fs/etc/resolv.conf
touch fs/etc/hosts[/COLOR]


#make the new squash filesystem from the folder we have been making changes to
[COLOR="Green"]mksquashfs fs/ iso/casper/filesystem.squashfs[/COLOR]

#make the new ISO
[COLOR="Green"]mkisofs -r -V "cd" -cache-inodes -J -l -o newcd.iso \
-b isolinux/isolinux.bin -c isolinux/boot.cat \
-no-emul-boot -boot-load-size 4 -boot-info-table iso/[/COLOR]

#newcd.iso should be in your working directory, it is owned by root so we need to chown/chgrp it
[COLOR="Green"]chown YourUserName:YourUserGroup newcd.iso[/COLOR]

If you aren't happy with the newcd (forgot to include something or forgot to tweak something) delete newcd.iso and you can keep the work you have done so far by starting back at rm iso/casper/filesystem.squashfs

#if done, remove the following folders
[COLOR="Green"]rm -rf fs/
rm -rf iso/[/COLOR]

All done!

---

### Post by basenvironment on 2008-07-08
**EXTRA INFO:**

**## add/remove software, edit files, etc..** - some helpful commands
show a list of all installed packages with package info
[COLOR="Green"]dpkg -l[/COLOR]
create a text file of all installed packages with package info
[COLOR="Green"]dpkg -l >> packagesinfo.txt[/COLOR]
show a list of all installed packages
[COLOR="Green"]dpkg-query -W --showformat=' ${Package}'[/COLOR]
create a text file of all installed packages
[COLOR="Green"]dpkg-query -W --showformat=' ${Package}' >> packages.txt[/COLOR]
show all installed packages sorted by size
[COLOR="Green"]dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -n [/COLOR]
create a text file of all installed packages sorted by size
[COLOR="Green"]dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -n >> packagesbysize.txt[/COLOR]


update your software package lists
[COLOR="Green"]aptitude update[/COLOR]
install software
[COLOR="Green"]aptitude install package[/COLOR]
clean up your download packages
[COLOR="Green"]aptitude clean[/COLOR]



**ALTERNATE STEPS** 

**#mount dev, proc, etc**
[COLOR="Green"]
chroot fs mount -t proc none /proc
chroot fs mount -t sysfs none /sys
chroot fs mount -t tmpfs none /dev
chroot fs mount -t devpts none /dev/pts
[/COLOR]
**#unmount dev, proc, etc**
[COLOR="Green"]chroot fs umount /proc
chroot fs umount /sys
chroot fs umount /dev/pts
chroot fs umount /dev[/COLOR]

---

### Post by LaRoza on 2008-07-08
I can't try this yet, but if anyone can confirm it works well, I'll add it to the sticky.

---

### Post by basenvironment on 2008-07-08
*reserved for more rambling info*

---

### Post by basenvironment on 2008-07-08
> **LaRoza said:**
> I can't try this yet, but if anyone can confirm it works well, I'll add it to the sticky.
I can confirm it... :lolflag:

---

### Post by adarkmethod on 2008-07-17
=======                                                   ]  13044/106171  12%Failed to read file /home/darkmethod/livecd/custom/proc/key-users, creating empty file



mine freezes there every time after I enter "sudo mksquashfs ~/livecd/custom ~/livecd/cd/casper/filesystem.squashfs"

---

### Post by wolfen69 on 2008-07-17
i'm not sure i get the point of this. how is this different than remastersys?

---

### Post by basenvironment on 2008-07-18
> **wolfen69 said:**
> i'm not sure i get the point of this. how is this different than remastersys?

the point would be to customize a livecd...

remastersys afaik rebuilds you system into a livecd and is fairly automagic in its actions...

---

### Post by basenvironment on 2008-07-18
> **adarkmethod said:**
> =======                                                   ]  13044/106171  12%Failed to read file /home/darkmethod/livecd/custom/proc/key-users, creating empty file

mine freezes there every time after I enter "sudo mksquashfs ~/livecd/custom ~/livecd/cd/casper/filesystem.squashfs"
it appears you aren't following the instructions since the instructions say nothing about using sudo or anything about ~/livecd/cd

---

### Post by Rui Pais on 2008-07-18
> **LaRoza said:**
> I can't try this yet, but if anyone can confirm it works well, I'll add it to the sticky.

Yes it should works.

This is essentially the
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
without sudo references (*a la* Debian) :)

---

### Post by basenvironment on 2008-07-18
> **Rui Pais said:**
> Yes it should works.

straight from the man that bans.... :lolflag:

Yes it is very similar to that page, a bit more simplified though.

---

### Post by basenvironment on 2008-07-18
Here is a video of me running thru the commands. It  is very boring, and long, and pointless. But if someone wanted to see the process and the output from the commands....

[VIDEO]("http://nrvwebsolutions.com/junk/customize_hardy_out.ogv")



ps - I actually created this thread because someone asked me for some help with a similar process I posted at another forum and I am banned at that forum. So I just posted so I could help someone with it. Hope that is okay.

---

