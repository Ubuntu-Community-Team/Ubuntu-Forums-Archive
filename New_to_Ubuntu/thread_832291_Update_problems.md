---
title: "Update problems"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by paulrach on 2008-06-17
I recently let Ubuntu 8.04 do an autoupdate, up until this point I have had very few issues with this. However, this UpDate has given me numerous errors.

On the update button I now have a 'no entry' sign which gives me a message about

Error: BrokenCount > 0 

Links on this site suggest that I need to go to Synaptic. When I go to Synaptic I get the following message:

E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I have removed about 100Mb of files from the HDD yet it still says that there is 0B free space. Other things that have stopped working are the Back button in Firefox, Evolution downloads.

I'm stuck here so any help would be greatly appreciated.

Regards Paul

---

### Post by HermanAB on 2008-06-17
I know the mods are going to flame me but:
Don't fix it if it ain't broke.

Once you got Ubuntu installed and working, leave it alone.  Install the new version from scratch when it comes out in 6 months.  Don't do the gawddamm updates.  If your system is working, then an update cannot make it better, it can only make it worse.  Linux is inherently much better quality than MS Windows, so ordinary mortals don't need to do the updates.

Cheers,

Herman.

---

### Post by Duck2006 on 2008-06-17
Yes i find a clean install is better than doing an up data.

---

### Post by cariboo on 2008-06-17
Where and how did you remove the 100mb of files? To see how much space you have used on your hdd in a terminal type:

```
df -h
```

You should see something like this:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             6.5G  3.8G  2.5G  61% /
varrun                992M  108K  992M   1% /var/run
varlock               992M     0  992M   0% /var/lock
udev                  992M   96K  992M   1% /dev
devshm                992M   24K  992M   1% /dev/shm
lrm                   992M   43M  950M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7             141G   68G   72G  49% /home
gvfs-fuse-daemon      6.5G  3.8G  2.5G  61% /home/jimk/.gvfs
/dev/sde1             2.0G  429M  1.5G  22% /media/disk
```

This listing will give you a pretty good idea of how much free space you have .

In this case I have a seperate root and home partitions. As you can see /dev/sda5 is my root partition and I've got 2.5G of available space. /dev/sda7 is my home partition and I have 72G of free space.

Jim

---

