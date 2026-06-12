---
title: "Change the Name Of Hotplugged Drives (FAT32)"
date: 2005-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by joshmachine on 2005-10-01
**Note:** This is definitely applicable to gnome.  I am not sure about KDE

This started as a personal vendetta against my external usb drive that kept showing up as **DRV2_VOL1**.  I wanted it to have a more meaningful name.  

With things being so simple today "It all just works" It was surpisingly difficult to really find out how the hell to change this. 

In the course of my investigation I identified the following flow of communication.[LIST]
[*]vfat usb drive is plugged in
[*]udev creates all of the low level crap (dev nodes) etc
[*]hal populates a device entry for the drive and all of the volumes
[*]***gnome-volume-manager*** uses the **volume.label** key from the volume to create the drive name as it appears in nautilus.[/LIST]Since there doesn't appear to be any way of getting ***gnome-volume-manager*** to use a user-defined name (it seems as though this would be relatively easy) I ended up hacking the hal entry to specify a volume label of my choosing. This was actually pretty damn easy once I knew where to go.

There is a decent write up of hal you can check out at [http://www.redhat.com/magazine/003jan05/features/hal/]("http://www.redhat.com/magazine/003jan05/features/hal/")

Basically you are able to create your own entries that will be merged into and override the purely device generated ones.

To do this I did the following steps:[LIST=1]
[*]Run ***hal-device-manager***
[*]Locate the offending volume entry (its name will be the same as it appears on the desktop.) It will be pretty deep ( Mine was at Computer -> [ a couple of USB controllers ] -> USB Storage Adapter -> SCSI Host Adapter -> SCSI Device -> [drive model] -> DRV2_VOL1) Whew!
[*]Click on the device node itself then select the "Advanced Tab." This is where all the useful information is.  I used the **volume.uuid** entry as my main key of overriding some of the other entries.
[*]Create a custom information directory at the following location: **/usr/share/hal/information**. I named mine **90local**.
[*]in this directory add a file which will match the offending volume and override some of the entries.  I named mine **90-usbdrive.fdi**.[/LIST]FDI file contents.  

If you know xml, the syntax is very simple. first you match on the entries of the device you want to change. then you merge (override) those things you want to.

these are the contents of my **90-usbdrive.fdi** file.

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- --> 
<deviceinfo version="0.2">
  <device>
    <match key="info.category" string="volume">
      <match key="volume.uuid" string="3845-92E9">
          <merge key="volume.label" type="string">backup</merge>
          <merge key="info.product" type="string">WD1</merge>
          <merge key="volume.policy.desired_mount_point" type="string">backup</merge>
      </match>
    </match>
  </device>
</deviceinfo>
``` 
The entries have the following effect.[LIST=1]
[*]First check if the device is a volume.
[*]Then check if it is the one i want to change
[*]Then set it's **volume.label** to how I want it to appear in gnomeland.
[*]**info.product** controls how the device appears in ***hal-device-manager*** (it may have other effects, but my system hasn't exploded yet.)
[*]**volume.policy.desired_mount_point** is respected by ***gnome-volume-manager*** in creating the actual mount point.  It will end up being **/media/backup**.[/LIST]That's it.  Save your file, unplug you drive, plug it back in and voila.  I get 'backup' in nautilus, and it is mounted at **/media/backup**.

If this seems overly difficult. Maybe it is. I would expect it to be more easily configurable in the next few realeases of Gnome/HAL. 

Hope this was helpful to someone. 

Cheers

---

### Post by darkvad0r on 2006-10-15
After some research, I finally found out how to do this in Edgy (it should also be valid for dapper but I can't assure it).
All you have to do is to edit /etc/hal/fdi/policy/preferences.fdi to suit your needs (as instructed by the post above).
It works with kde and gnome desktop.
Oh, by the way, this works for all types of hotplugged drives, not only fat32 .

---

### Post by p_ano on 2007-07-09
editing "/etc/hal/fdi/policy/preferences.fdi" worked for me in feisty as well.   hurray!

---

### Post by Morimando on 2008-01-09
Thanks for the tutorial, got it to work after some fiddling around. It might be because i run Gentoo or it might be just because i run a newer version of hal, but there are some things different. Let me describe it and i'll be off ;) (if this doesn't apply in Ubuntu, well i wasted some time, if it will, maybe i can save you the time of trying yourself ;) )
a) the file format and content is correct, though i had to make the new directory /usr/share/hal/fdi/policy/90local
2) in this directory i put ONE rule (don't know why, but it won't use more than this one rule from this directory
3) in this file you can actually specify as many devices as you like :) I just put them together like in the example below.
4) As usual, unmount, unplug, replug, name should be changed
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device><!-- 4GB USB Stick -->
<match key="info.category" string="volume">
<match key="volume.uuid" string="1cb488fd-f3d3-4562-a2e5-0fb8234dd45d">
<merge key="volume.label" type="string">Scooter</merge>
<merge key="info.product" type="string">Scooter-Daten</merge>
<merge key="volume.policy.mount_point" type="string">scooter</merge>
</match>
</match>
</device>
<device><!-- cruzer micro 1GB -->
<match key="info.category" string="volume">
<match key="volume.uuid" string="fcbceacb-a600-4deb-b53e-879a2130ad45">
<merge key="volume.label" type="string">Peeves</merge>
<merge key="info.product" type="string">Peeves-Daten</merge>
<merge key="volume.policy.desired_mount_point" type="string">peeves</merge>
</match>
</match>
</device>
</deviceinfo> 

```
After that all should work fine :guitar:

---

### Post by sbassett on 2008-01-09
I might be missing the point entirely, but if this is a hot-plugged drive, especially vfat, why not just use mtools' mlabel.

The syntax is:

```
mlabel c:[new_name]
```

and you are done. 

On the default Ubuntu install C: is mapped to /dev/sda1and commented out. So, just to give it a go, I uncommented the line for C: and typed the above in, unmouted, unplugged then replugged the thumbdrive back in, and it popped back up as SEAGATE, the name I gave it (it being a seagate and all).

Oh yeah, to get the package

```
sudo apt-get install mtools
```

---

