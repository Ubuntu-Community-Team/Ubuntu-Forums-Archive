---
title: "Ubuntu 15.04 Installation - Ubiquity Crash"
date: 2015-09-23
forum: New to Ubuntu
---

### Post by Dylan_Duryee on 2015-09-23
Hi, so I'm installing Ubuntu on my new SSD, because my old drive had a failure. When I reach this screen (partition) :

[IMG]http://i.imgur.com/ZgVLZx7.png[/IMG]

If I click +, -, or Change the whole installation freezes, then closes after about a minute or two. I get this error message: 

```
Ubiquity 2.21.25

(process:2637): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:2637): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:2667): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:2667): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:2711): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:2711): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:2724): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:2724): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:2734): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:2734): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
update_release_notes_label()
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied

(process:3767): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3767): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:3775): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3775): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:3783): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3783): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:3889): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3889): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:3897): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3897): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:3923): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3923): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
Exception caught in process_line:
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 145, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 430, in process_line
    data = self.db.command(command, *params)
  File "/usr/lib/python3/dist-packages/debconf.py", line 66, in command
    self.write.write("%s %s\n" % (command, ' '.join(map(str, params))))
ValueError: I/O operation on closed file.
Ubiquity 2.21.25

(process:3983): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3983): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:3995): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:3995): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4005): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4005): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4040): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4040): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4050): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4050): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
update_release_notes_label()
Exception caught in process_line:
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 145, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 287, in process_line
    if not input_widgets[0].run(priority, question):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 2715, in run
    "Deleting partition didn't rebuild cache?")
AssertionError: Deleting partition didn't rebuild cache?
dbfilter_handle_status stepPart
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1293, in on_partition_list_new_activate
    self.partman_dialog(devpart, partition)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 956, in partman_dialog
    if create and partition['parted']['type'] == 'pri/log':
TypeError: 'NoneType' object is not subscriptable

Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1293, in on_partition_list_new_activate
    self.partman_dialog(devpart, partition)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 956, in partman_dialog
    if create and partition['parted']['type'] == 'pri/log':
TypeError: 'NoneType' object is not subscriptable

(process:6014): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6014): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6022): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6022): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6031): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6031): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6076): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6076): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6084): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6084): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6092): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6092): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
Ubiquity 2.21.25

(process:6148): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6148): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6158): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6158): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6174): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6174): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6184): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6184): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:6194): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:6194): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
update_release_notes_label()
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1297, in on_partition_list_edit_activate
    self.partman_dialog(devpart, partition, create=False)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 978, in partman_dialog
    if ('can_resize' not in partition or not partition['can_resize'] or
TypeError: argument of type 'NoneType' is not iterable

Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1297, in on_partition_list_edit_activate
    self.partman_dialog(devpart, partition, create=False)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 978, in partman_dialog
    if ('can_resize' not in partition or not partition['can_resize'] or
TypeError: argument of type 'NoneType' is not iterable

(process:7831): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7831): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:7839): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7839): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:7847): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7847): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:7855): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7855): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:7865): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7865): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:7873): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7873): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
/usr/lib/ubiquity/ubiquity/gtkwidgets.py:13: Warning: g_object_set_data: assertion 'G_IS_OBJECT (object)' failed
  Gtk.main_iteration()
Ubiquity 2.21.25

(process:7972): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7972): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:7982): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:7982): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:8005): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:8005): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:8033): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:8033): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:8120): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:8120): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
update_release_notes_label()
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1293, in on_partition_list_new_activate
    self.partman_dialog(devpart, partition)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 956, in partman_dialog
    if create and partition['parted']['type'] == 'pri/log':
TypeError: 'NoneType' object is not subscriptable

Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1293, in on_partition_list_new_activate
    self.partman_dialog(devpart, partition)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 956, in partman_dialog
    if create and partition['parted']['type'] == 'pri/log':
TypeError: 'NoneType' object is not subscriptable

(process:9772): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9772): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9780): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9780): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9788): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9788): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9796): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9796): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9805): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9805): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9813): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9813): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
Ubiquity 2.21.25

(process:9874): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9874): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9884): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9884): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9894): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9894): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9904): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9904): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:9914): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:9914): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
update_release_notes_label()
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1297, in on_partition_list_edit_activate
    self.partman_dialog(devpart, partition, create=False)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 978, in partman_dialog
    if ('can_resize' not in partition or not partition['can_resize'] or
TypeError: argument of type 'NoneType' is not iterable

Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1297, in on_partition_list_edit_activate
    self.partman_dialog(devpart, partition, create=False)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 978, in partman_dialog
    if ('can_resize' not in partition or not partition['can_resize'] or
TypeError: argument of type 'NoneType' is not iterable

(process:11423): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11423): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11431): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11431): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11439): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11439): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11447): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11447): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11455): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11455): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11463): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11463): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
Ubiquity 2.21.25

(process:11622): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11622): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11632): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11632): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11646): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11646): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11656): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11656): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:11666): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:11666): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
update_release_notes_label()
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1293, in on_partition_list_new_activate
    self.partman_dialog(devpart, partition)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 956, in partman_dialog
    if create and partition['parted']['type'] == 'pri/log':
TypeError: 'NoneType' object is not subscriptable

Traceback (most recent call last):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 1293, in on_partition_list_new_activate
    self.partman_dialog(devpart, partition)
  File "/usr/lib/ubiquity/ubiquity/plugin.py", line 48, in wrapper
    return target(self, *args, **kwargs)
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 956, in partman_dialog
    if create and partition['parted']['type'] == 'pri/log':
TypeError: 'NoneType' object is not subscriptable

(process:13174): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:13174): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:13182): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:13182): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:13194): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:13194): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:13202): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:13202): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:13210): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:13210): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:13218): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.
```


I've read around and haven't found anything useful for myself.

I've tried the Ubuntu 14.04.3 TLS, and it gives me the same error for some reason. If you need additional information please just tell me! Thanks!

---

### Post by VMC on 2015-09-23
Have you tried partitioning that drive first before installing? What type of BIOS do you have? I don't have an SSD hard drive, but does TRIM come into play on this?

---

### Post by Dylan_Duryee on 2015-09-23
I've tried to, but can't edit the drive in gPart or anything. Also, I have a MSI H81M-E33 Motherboard (ME FW-9.0.30.1482 BIOS).

---

### Post by Geoffrey_Arndt on 2015-09-23
Did you try unmounting it first?   gparted should give you an option to do that, and then the edit is available?

---

### Post by Dylan_Duryee on 2015-09-23
Yes I have, I get this error:

> 
umount: /cdrom: target is busy
        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)



---

### Post by oldfred on 2015-09-23
Please use code tags, # in advanced editor.
And please attach screen shots not post in line. Use paperclip icon in Forum's advanced editor.

---

### Post by Dylan_Duryee on 2015-09-23
Alright, thank you.

I've actually fixed it myself. I had to re-install the ISO to the drive, and create each partition before attempting to install. Thanks anyways.

---

### Post by IanUK on 2015-11-11
[FONT=arial]I had similar errors, with the installer crashing when it got to the "Creating User" stage.
I had setup my partitions before hand, and that did not help.
I was setting up the boot to use UEFI - I think this was the root of the problem.
I found this page - [http://www.scriptscoop.net/t/951358a27cfa/ubuntu-14-04-installer-stuck-while-already-on-liveusb.html](http://www.scriptscoop.net/t/951358a27cfa/ubuntu-14-04-installer-stuck-while-already-on-liveusb.html)
and ran this to check my disks - 
[/FONT][FONT=arial][FONT=courier new]sudo gdisk -l /dev/sda[/FONT]

sure enough, it reported that my disks had a mix of MBR and GPT.
I recreated the disks partition tables with gparted (see: [http://akabaila.pcug.org.au/gpt/gpt_gparted.html](http://akabaila.pcug.org.au/gpt/gpt_gparted.html)), and setup the partitions again.

The instal then ran ok.

Ian
.[/FONT]

---

