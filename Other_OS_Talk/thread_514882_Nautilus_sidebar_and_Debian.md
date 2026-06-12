---
title: "Nautilus sidebar and Debian"
date: 2007-08-01
forum: Other OS Talk
---

### Post by Steve1961 on 2007-08-01
I've been running Ubuntu (Feisty) and Debian (Lenny) now for a couple of years and I have a question that I'm hoping someone might be able to help me with.  In Ubuntu I can mount any of my partitions by double-clicking the icon in the nautilus sidebar and entering my password.  In Debian, however, the partitions are shown but if I try to mount one from the sidebar I just get an error message:

Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy

I can mount any partition in the usual way, but I've found that if there's an fstab entry for it the partition shows up twice in the sidebar, and yet no fstab entries seem to be necessary in feisty.

Does anyone know how I can add the ability to mount partitions from the sidebar to debian?

---

### Post by kerry_s on 2007-08-01
well from what i see in /etc/hal/fdi/policy/preferences.fdi  ,it's not setup by default, everything is commented out. so i'm guessing you would have to set it up. try checking what fiesty has in there. sorry can't be of more help, i use debian+icewm+rox and ivman for mounting.

---

### Post by Steve1961 on 2007-08-01
Both xml files are identical to each other so I'm guessing it's not that?

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->


<!-- 
  The following shows how to put sync and noatime on for devices smaller then
  1Gb and off for device larger then that. Note that the sync option can wear
  out device faster then you'd like too. See
  http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html for
  more info.
--> 
<!--
  <device> 
    <match key="block.is_volume" bool="true">
      <match key="volume.size" compare_lt="1000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">true</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">true</merge>
        </match>
      </match>
      <match key="volume.size" compare_ge="1000000000">
        <match key="@block.storage_device:storage.hotpluggable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
        </match>
        <match key="@block.storage_device:storage.removable" bool="true">
          <merge key="volume.policy.mount_option.sync" type="bool">false</merge>
          <merge key="volume.policy.mount_option.noatime" type="bool">false</merge>
        </match>
      </match>
    </match>
  </device>
--> 
</deviceinfo>
```

---

### Post by kerry_s on 2007-08-01
let me see if i got this right, you have other partions, but there not listed in fstab and there not mounted at startup?

do you have gnome-volume-manager installed?
i also see gnome-mount in synaptic, do you have that?

do you want them automounted?
if yes, have you tried putting> mount -a & < in /etc/rc.local?

i'm thinking it's a permission thing, have you checked if your in the disk group?

---

### Post by Steve1961 on 2007-08-01
> let me see if i got this right, you have other partions, but there not listed in fstab and there not mounted at startup?

I have numerous partitions, some of which I automount through fstab at startup, and others I manually mount if I need to access them.  However, all of my partitions also show up in the nautilus sidebar.  In Fesity I can just double-click them and mount or unmount them at will without any fstab entries.  This is really convenient and I wondered if it was also possible in Debian.

> do you have gnome-volume-manager installed?
i also see gnome-mount in synaptic, do you have that?

I have both installed.

> do you want them automounted?
if yes, have you tried putting> mount -a & < in /etc/rc.local?

No, I want to mount them as and when necessary

> i'm thinking it's a permission thing, have you checked if your in the disk group?

Ah, I'm not.  I'll give that a try and get back to you.

---

### Post by Steve1961 on 2007-08-01
Adding myself to the disk group made no difference.  I think it is a permissions problem, problem is I don't know what Feisty uses to grant rights to mount disks to users from within nautilus - or even from the desktop computer icon.

---

### Post by alexludwigklein on 2007-09-28
Hi everybody!

I tried to achieve the following thing: Mounting an encrypted partition from the places folder in gnome (with gnome-mount). This is easy, if this partition is on a removable media. It shows up and when you mount it you are asked for your password. Afterwards a mapper device is created. That device contains an ext3 filesystem, which is then again mounted. (tested with USB-Stick).

But in my setup the partition is on my internal harddisk. It did not show up in the places folder (computer:/// in Nautilus). My System is Debian Etch 4.0r1. In my opinion this might be related to Steve1961's problem.

I did the following steps:

1.) Make the partition to show up in Nautilus: 
in /usr/share/hal/fdi/policy/10osvendor/debian-storage-policy-ignore-fixed-crypto-drives.fdi
changed true to false. That way HAL does not ignore the partition (in my case /dev/sda3). That is the new file:
```
user@debian# cat debian-storage-policy-ignore-fixed-crypto-drives.fdi
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="volume.fsusage" string="crypto">
      <match key="@block.storage_device:storage.hotpluggable" bool="false">
        <match key="@block.storage_device:storage.removable" bool="false">
          <merge key="volume.ignore" type="bool">false</merge>
        </match>
      </match>
    </match>
  </device>
</deviceinfo>
```

2.) TRY to make the device mountable by user:
I created a new policy in /usr/share/hal/fdi/policy/10osvendor/
```
user@debian# cat new_policy.fdi
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
	<device>
		<match key="volume.linux.is_device_mapper" bool="true">
			<match key="volume.uuid" string="a472a5dd-ae7f-453b-b04c-fdeb73fb22e2">
				<merge key="volume.ignore" type="bool">false</merge>
				<append key="volume.mount.valid_options" type="strlist">uid=</append>
			</match>
		</match>
	</device>
	<device>
    		<match key="volume.fsusage" string="crypto">
      			<match key="@block.storage_device:storage.hotpluggable" bool="false">
       				 <match key="@block.storage_device:storage.removable" bool="false">
          				<merge key="volume.ignore" type="bool">false</merge>
					<append key="volume.mount.valid_options" type="strlist">uid=</append>
        			</match>
      			</match>
    		</match>
  	</device>
</deviceinfo>
```

With this setup my encrypted partition (/dev/sda3) is mounted as clear text device /dev/dm-0 by gnome-mount. BUT then I am not allowd to mount the ext3 mapper device: /dev/dm-0 (its uuid is a472a5dd-ae7f-453b-b04c-fdeb73fb22e2 as typed above). gnome-mount gives:

```
user@debian# gnome-mount -vbd /dev/sda3
gnome-mount 0.5
libhal-storage.c 1401 : INFO: called LIBHAL_FREE_DBUS_ERROR but dbusError was not set.
** (gnome-mount:4479): DEBUG: Crypto volume - UDI '/org/freedesktop/Hal/devices/volume_uuid_ea9f10d3_7fda_42c3_928c_2d75270de2e8'
** (gnome-mount:4479): DEBUG: Setting up /org/freedesktop/Hal/devices/volume_uuid_ea9f10d3_7fda_42c3_928c_2d75270de2e8 for crypto
Setup clear-text device for /dev/sda3.
** (gnome-mount:4479): DEBUG: Waiting for cleartext volume backed by /org/freedesktop/Hal/devices/volume_uuid_ea9f10d3_7fda_42c3_928c_2d75270de2e8..
** (gnome-mount:4479): DEBUG: In crypto_setup_device_added for /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2
** (gnome-mount:4479): DEBUG: In crypto_setup_device_removed for /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2
** (gnome-mount:4479): DEBUG: In crypto_setup_device_added for /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2
** (gnome-mount:4479): DEBUG: In crypto_setup_device_removed for /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2
** (gnome-mount:4479): DEBUG: In crypto_setup_device_added for /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2
** (gnome-mount:4479): DEBUG: /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2 is backed by /org/freedesktop/Hal/devices/volume_uuid_ea9f10d3_7fda_42c3_928c_2d75270de2e8 - will mount
Clear text device is /dev/dm-0. Mounting.
** (gnome-mount:4479): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2
** (gnome-mount:4479): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2 with mount_point='dm-0', fstype='', num_options=0

** (gnome-mount:4479): WARNING **: Mount failed for /org/freedesktop/Hal/devices/volume_uuid_a472a5dd_ae7f_453b_b04c_fdeb73fb22e2
org.freedesktop.Hal.Device.PermissionDeniedByPolicy : hal-storage-fixed-mount refused uid 1000
```

It always ends with: hal-storage-fixed-mount refused uid 1000
If I check the device with hal-device-manager, the uid= is set. I also appended other strings to "volume.mount.valid_options", like users. But it did not change anything. 

Trying to mount this device should be the same case as the following setup: An ext3 partition, which should be mountable by a normal user. The user is a member of the disk group.

I would be deligthed if somebody could help me, since it would be comfortable to mount a partition from within Nautilus whenever the user wants it. 

BTW: pmount is able to mount /dev/sda3 with the following settings:

```
user@debian# cat /etc/pmount.allow
# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.
/dev/sda3
```

Another approach: It is possible to include the mapper device in my fstab:
```
UUID=a472a5dd-ae7f-453b-b04c-fdeb73fb22e2 /media/crypt   ext3 defaults,user,exec,noauto   0   0
```

HAL is then able to mount the device-mapper, because it uses the fstab properties for the device. BUT: If I use this, the mapper device is always listed in Nautilus, even if not present.

Thank you very much in advance for your help.

Kind regards

Alexander Klein.

---

