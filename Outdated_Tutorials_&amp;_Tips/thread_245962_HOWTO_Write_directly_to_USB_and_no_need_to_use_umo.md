---
title: "HOWTO: Write directly to USB and no need to use umount"
date: 2006-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by yopnono on 2006-08-28
In the MS windows world you can copy/move files to a USB unit and then just unplug it. 

But in the Linux world you need to use unmount device (umount), to make sure that your files are transferred to the unit.

If you are using this code, you can use the USB unit in a windows way = copy/move your files and unplug it.

Just copy the code in to a new file called... "usb.fdi" 
and put it in the "/etc/hal/fdi/policy" Or use the attached .DEB file

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <!-- Default policies merged onto computer root object  -->
  <device>
    <match key="info.udi" string="/org/freedesktop/Hal/devices/computer">
      <merge key="storage.policy.default.mount_root" type="string">/mnt</merge>
      <merge key="storage.policy.default.use_managed_keyword" type="bool">true</merge>
      <merge key="storage.policy.default.managed_keyword.primary" type="string">managed</merge>
      <merge key="storage.policy.default.managed_keyword.secondary" type="string">kudzu</merge>
      <merge key="storage.policy.default.mount_option.noauto" type="bool">true</merge>
      <merge key="storage.policy.default.mount_option.pamconsole" type="bool">true</merge>
      <merge key="storage.policy.default.mount_option.exec" type="bool">true</merge>
    </match>
  </device>

  <device>
    <!-- Whitelist bus types of storage devices we care about  -->
    <match key="info.category" string="storage">
      <match key="storage.bus" string="usb">
	<merge key="storage.policy.should_mount" type="bool">true</merge>      
      </match>
      <match key="storage.bus" string="ide">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
      <match key="storage.bus" string="ieee1394">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
      <match key="storage.bus" string="sata">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
      <match key="storage.bus" string="platform">
	<merge key="storage.policy.should_mount" type="bool">true</merge>
      </match>
    </match>

    <!-- Normal volumes; use volume label, uuid or drive_type -->
    <match key="block.is_volume" bool="true">
      <match key="volume.fsusage" string="filesystem">
	<!-- skip for drives with the no partitions hint (they are handled above) -->
	<match key="@block.storage_device:storage.no_partitions_hint" bool="false">

	  <merge key="volume.policy.should_mount" type="bool">true</merge>
	  <merge key="volume.policy.mount_filesystem" type="copy_property">volume.fstype</merge>
	  
	  <!-- Fallback is '<storage.bus>', appended with 'disk', e.g. usbdisk,
		  idedisk, scsidisk etc. -->
	<!--
	  <merge key="volume.policy.desired_mount_point" type="copy_property">@block.storage_device:storage.bus</merge>
	  <append key="volume.policy.desired_mount_point" type="string">disk</append>
	  -->
	  <merge key="volume.policy.desired_mount_point" type="string">removable</merge>

  
          <!-- Best: If available use filesystem label -->
          <match key="volume.label" empty="false">
            <!-- unless it's a path (e.g. /boot, /, /home etc) -->
            <match key="volume.label" is_absolute_path="false">
	      <!-- and only if the label is ascii -->
              <match key="volume.label" is_ascii="true">
		<merge key="volume.policy.desired_mount_point" type="copy_property">volume.label</merge>
              </match>
            </match>
          </match>
	  

	  <!-- Use noatime and sync options for all hotpluggable or removable
	       volumes smaller than 2GB -->
	  <match key="volume.size" compare_lt="2147483648">
	    <match key="@block.storage_device:storage.hotpluggable" bool="true">
	      <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
	      <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
	    </match>
	    <match key="@block.storage_device:storage.removable" bool="true">
	      <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
	      <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
	    </match>
	  </match>

	  <!-- Use UTF-8 charset for vfat -->
	  <!--
	  <match key="volume.fstype" string="vfat">
	    <merge key="volume.policy.mount_option.iocharset=utf8" type="bool">true</merge>
    </match>-->
	  
	  </match>	  
	</match>
      </match>
    </device>

</deviceinfo>
```

---

### Post by farky on 2006-08-29
Great! Thanks for this!

---

### Post by hoerig on 2006-09-13
Nice Script, but very slow.... :/

---

### Post by yopnono on 2006-09-13
> **hoerig said:**
> Nice Script, but very slow.... :/

Yep I know this is because it not using the cache, it's writing directly.
And this is why you can unplug it without umont.

If someone know how to speed it up, please tell.

---

### Post by ramcosca on 2006-09-13
I needed this a few days ago, haha. I moved something to the pen drive and simply unplugged... later realized I had to eject/unmount it so it would move the files.

Thanks.

---

### Post by grizzly on 2006-09-14
Great ! I was looking for something like this!

---

### Post by ijanos on 2006-09-14
Guys be careful with this!
This will reduce the lifetime of the USB storage because this gadgets designed to write and read big packets of data but with this setting the computer will write out every single bit instantly. 
Its better if you use sync command before unplug (create a panel button for eg.) and when the led stop flashing you can safely unplug.

---

### Post by bodhi.zazen on 2006-09-16
Nice script, but why not just use sync in fstb;

```
/dev/sda1 /media/usb vfat user,sync 0 0
```

The sync option should do the same thing.

---

### Post by tvor on 2006-10-08
Hi, just briefly, could you please point me to the right dirrection how to "sync command before unplug (create a panel button for eg.)" how do you create a panel button - to write a command seems to me a rather lengty procedure. Thanks

---

### Post by ijanos on 2006-10-08
> **tvor said:**
> Hi, just briefly, could you please point me to the right dirrection how to "sync command before unplug (create a panel button for eg.)" how do you create a panel button - to write a command seems to me a rather lengty procedure. Thanks

Just start a terminal, type *sync* and press enter.

---

### Post by 3rdalbum on 2006-10-09
Don't do this. One Linux distribution decided to make "sync" the default behaviour, and it ended off destroying people's flash drives in a matter of weeks.

Besides, you should never unplug any read/write device without unmounting it, not even on Windows. It might work 99/100, but you'd feel pretty silly when your data got corrupted. Come on, it only takes 2 seconds to unmount. If something's still copying, you can tell Gnome to unmount it and it will be unmounted when the copying finishes.

---

### Post by ashrack on 2006-10-09
But isn't "sync" the default option set in Windows?
So if Windows doesnt destroy FLASH DRIVEs and don't see why Linux should when "sync" is set?
And also why is copying so slow with SYNC option turned on? 

With SYNC I must wait an hour for a 70MB file to get coppied.

---

### Post by yopnono on 2006-10-09
You are talking about this right?
  [http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)

---

### Post by yopnono on 2006-10-09
Well it should be nice if it could use sync directly after the file / folder transfer. Like this:
```
cp file /media/usbdisk && sync
```

---

### Post by king20878 on 2006-10-09
Actually I nearly lost a vacations worth of photos when I unplugged a flash drive from a windows machine without choosing to eject it first.  Fortunately linux and fsck saved me.  ;)

---

### Post by ashrack on 2006-10-09
> **yopnono said:**
> You are talking about this right?
  [http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)
Correct! And after reading it am still curious why it isnt implemented the Windows way which is kinda better.

> **yopnono said:**
> Well it should be nice if it could use sync directly after the file / folder transfer. Like this:
```
cp file /media/usbdisk && sync
```
I believe Windows uses this kind of approach! I really wonder if it is possible to set GNOME to this behaviour somehow when transfering files to flash drive.

> **king20878 said:**
> Actually I nearly lost a vacations worth of photos when I unplugged a flash drive from a windows machine without choosing to eject it first.  Fortunately linux and fsck saved me.  ;)
Glad to hear U didn't lost data.

---

