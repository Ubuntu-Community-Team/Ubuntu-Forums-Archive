---
title: "Error Installing -  [Errno 13] Permission denied: '/var/lib/partman/stopfifo'"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by aravind3 on 2014-09-10
Hi All,

I am trying to install UBUNTU 14.0.4.1 LTS along with windows 8 to dual boot.

Specs:
Thoshiba p75-A7100
8gb , Came installed with Windows 8.

I am tryin to install ubuntu from a live cd. The UEFI is enabled,Secure boot is disabled. The Installer gets stuck at "Prepare to Install phase" with below stack trace in debug

Stack trace
---------------

(process:4250): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4250): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4250): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4250): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused

(process:4263): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4263): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4263): dconf-CRITICAL **: unable to create file '/home/ubuntu/.cache/dconf/user': Permission denied.  dconf will not work properly.

(process:4263): dconf-WARNING **: failed to commit changes to dconf: Could not connect: Connection refused
update_release_notes_label()
update_release_notes_label()
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 512 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 578 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
Exception caught in process_line:
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 145, in process_line
    return self.dbfilter.process_line()
  File "/usr/lib/ubiquity/ubiquity/debconffilter.py", line 287, in process_line
    if not input_widgets[0].run(priority, question):
  File "/usr/lib/ubiquity/plugins/ubi-partman.py", line 2977, in run
    size = int(parted.partition_info(p_id)[2])
  File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 220, in partition_info
    self.open_dialog('PARTITION_INFO', partition)
  File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 141, in open_dialog
    self.error_handler()
  File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 112, in error_handler
    exception_type = self.read_line()[0]
  File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 74, in read_line
    line = self.outf.readline().rstrip('\n')
  File "/usr/lib/python3.4/codecs.py", line 313, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xd5 in position 66: invalid continuation byte
Exception ignored in: <bound method PartedServer.__del__ of <ubiquity.parted_server.PartedServer object at 0x7f86ed2fbf28>>
Traceback (most recent call last):
  File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 62, in __del__
    self.close_dialog()
  File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 148, in close_dialog
    self.sync_server()
  File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 132, in sync_server
    with open(stopfifo, 'w'):
PermissionError: [Errno 13] Permission denied: '/var/lib/partman/stopfifo'

Screenshot Of Partition
---------------------------------

Attached as i am not able to paste here.

Please give some guidance on how to solve this. i am stuck on this for like 2 days now.

---

### Post by uRock on 2014-09-11
Hello and welcome to the forums. 

You can only have 4 primary partitions. [https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

If you haven't done so, then you may want to make a full backup of everything on the drive before doing any partitioning.

---

### Post by aravind3 on 2014-09-11
@uRock thanks for the Reply. Ok this was partitions created when i received my laptop. So i see 5 partitions and say i trim out one or 2 in that will this work. i have attached a screenshot.
Also the other concern is if i tamper with the partitions i might wreck the working windows 8.

---

### Post by uRock on 2014-09-11
> **aravind3 said:**
> @uRock thanks for the Reply. Ok this was partitions created when i received my laptop. So i see 5 partitions and say i trim out one or 2 in that will this work. i have attached a screenshot.
Also the other concern is if i tamper with the partitions i might wreck the working windows 8.

There is always a chance of ruining the an install when editing partitions, which is why I recommend creating a backup.

Once you have a backup and the repair disk, if that is required for Windows 8, you can alter partitions.

---

### Post by aravind3 on 2014-09-12
Ok i want to post the solution here so some body else finds it useful..

The  issues were 

1. I cloned my orginal HDD to my new SSD for windows 8 and then tried to install UBUNTU on it. Not sure what happened but that triggered some permission issues that causes the Installer to crash. So dont create a clone of your windows 8 rather use a recovery or an orginal CD to create the partiotions and install windows.

2.once you are sure that windows boots up. Dont tamper with partitions you dont have to and also if using 14.0.4 LTS.. just disable fast boot. rest every other configurations on bios is fine.

3. follow this link

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

And you are set . Am able to dual boot Ubuntu and windows and both works like charm. 

Thanks for the help.

---

