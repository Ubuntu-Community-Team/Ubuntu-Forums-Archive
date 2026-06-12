---
title: "Help settin up &quot;home&quot; to shared partition"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by saffagirl on 2008-09-21
Hi guys,

I'm fairly new at the whole Linux thing, but am loving it. i've used part magic to create a shared ntfs data partition with the intention of using this for music, docs, videos etc. 
Basically have partition a) Vista 35gb
b)Shared partition 170GB
c)Ubuntu 25gb

so what I'm wanting to do is get all music , video, openoffice , pictures to automatically save in default folders ie like //data/music ; //data/videos ; //data/docs on this partition for shared access . what's the best way to do this?

Thanks in advance:)

---

### Post by lswb on 2008-09-21
It appears you already have the /data directory mounted and accessible from ubuntu, is that right? If so, create the directories on the ntfs /data drive. You can use the usual commands from either linux or windows, cd /data/music, cd /data/videos, etc. or use a gui file browser to create them. I'm not sure how ntfs permissions work or how they translate to Linux & ext3, but for read/write access by all users, set them accordingly. If you need help with the ntfs permissions maybe someone else can help with that part, or check the man pages for mount and fstab.

Say you've made /data/music and /data/videos. In you users home directory make symlinks to these directories like this:

```

ln -s /data/music music
ln -s /data/videos videos

```

You could make these links on the Desktop if you prefer or any other convenient place. In the programs you use to download or create these files, set preferences to use the appropriate directory as the default.

---

### Post by AndyCooll on 2008-09-21
> **saffagirl said:**
> Hi guys,

I'm fairly new at the whole Linux thing, but am loving it. i've used part magic to create a shared ntfs data partition with the intention of using this for music, docs, videos etc. 
Basically have partition a) Vista 35gb
b)Shared partition 170GB
c)Ubuntu 25gb

so what I'm wanting to do is get all music , video, openoffice , pictures to automatically save in default folders ie like //data/music ; //data/videos ; //data/docs on this partition for shared access . what's the best way to do this?

Thanks in advance:)
Firstly you are going to need to ensure that this drive is automatically mounted on bootup. You can do this by adding a line to your /etc/fstab. You can find help on how to do this [here]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot")

Then it's the same process as with applications in Windows. You setup each application so it default saves to a particular folder (e.g. in Firefox the settings are in Edit > Preferences > Main Tab)

:cool:

---

### Post by saffagirl on 2008-09-22
Hi guys,

thanks for the responses,

Basically I'm able to see it, but I don't think it's automatically mounted I have to double click it from places in order to go into it then i see it on my workspace.

So I'm thinking automount and then try and point directories if it would let me ...symlink looks cool but would that automatically save it in the right folder?

---

### Post by biji on 2008-09-23
you can also set default permission for ntfs... fyi im using vfat for sharing...

---

### Post by saffagirl on 2008-09-23
Thanks for help, I'm trying to mount it and have finally figured out the syntax in fstab   , but I think I've done something silly. I can't manually mount my partition anymore  because I changed the mountpoint ...how do I change this I can't open it to adjust. 

I made a new directory /media/DATA but there had been one created already, so then it pointed to /media/DATA_ so i tried to point it to/DATA in options

I now get the following error:
cannot mount volume
Unable to mount the volume 'DATA'
mount_point cannot contain the following
characters: newline, G_DIR_SEPERATOR (usually /)

Thanks in advance.

---

### Post by AndyCooll on 2008-09-23
AFAIA the usual protocol for creating fixed mountpoints is to use the /mnt folder, /media is usually used by the OS for variable media types (e.g. usb devices etc).

In which case you'd create the mountpoint as follows:
```
sudo mkdir /mnt/DATA
```
And of course you'd modify /etc/fstab accordingly.

:cool:

---

### Post by saffagirl on 2008-09-23
Problem solved :0

Am now working from a boot mounted partition, now just to investigate programme defaults ;)

Thanks for the help:)

---

