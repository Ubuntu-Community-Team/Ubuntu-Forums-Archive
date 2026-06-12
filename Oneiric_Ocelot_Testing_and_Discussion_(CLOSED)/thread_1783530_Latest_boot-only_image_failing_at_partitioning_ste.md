---
title: "Latest boot-only image failing at partitioning step"
date: 2011-06-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2011-06-15
Downloaded **mini.iso** from:

```
http://archive.ubuntu.com/ubuntu/dists/oneiric/main/installer-i386/current/images/netboot/
```

and tried to install in vbirtualbox 4.0.8 (OO host).

Guided and manual partitioning both fail at "write changes to disk" stage.

A strange "????" pop-up window appears and the VM hangs if I try to go back to the previous screen or if I just try to continue and ignore the apparent error.

Anyone else had this?

Both of my OO hosts were upgraded from minimal natty installs by the way - just the way I prefer to set things up.

I *could* obviously use a natty **mini.iso** again and upgrade from there. In fact if I still had the last working **mini.iso** I used I could test that under the same conditions. Oh well. It's not a massive deal. Just wanted to experiment with slimming things down even more before I next do a *real* reinstall.

Btw, I just reused an existing natty VM instead of creating a new one from scratch. Didn't bother trying to create a new one from scratch to see if that would work. Seems unlikely though.

Another small thought - the natty VM I reused was actually created in a previous version of virtualbox (4.0.6 I think) so that's another variable in the equation, but it's late and I'm knackered so I'll leave it at that for tonight.

---

### Post by Starks on 2011-06-16
this bug: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/797054](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/797054)

---

### Post by paul_in_london on 2011-06-16
> **Starks said:**
> this bug: [https://bugs.launchpad.net/ubuntu/+source/parted/+bug/797054](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/797054)

Thanks **Starks**. Ah ok. From the upstream discussion, it's apparently down to the change in the format of the kernel version string so maybe I'll test that when I get home by booting 2.6.39.

Scratch that last part. Don't think I've quite woken up yet! The latest daily build would be booting from 3.0.0 in the VM so I'll just have to wait for the fix.

---

### Post by paul_in_london on 2011-06-16
This could be the fix:

```
paul@oneiric:~$ sudo aptitude safe-upgrade
Resolving dependencies...                
The following packages will be upgraded:
  libparted0debian1 parted 
2 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 278 kB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?] Y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ oneiric/main libparted0debian1 i386 2.3-6ubuntu1 [224 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ oneiric/main parted i386 2.3-6ubuntu1 [54.6 kB]
Fetched 278 kB in 0s (1177 kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LC_MESSAGES = "en_GB.UTF-8",
	LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 228881 files and directories currently installed.)
Preparing to replace libparted0debian1 2.3-5ubuntu6 (using .../libparted0debian1_2.3-6ubuntu1_i386.deb) ...
Unpacking replacement libparted0debian1 ...
Preparing to replace parted 2.3-5ubuntu6 (using .../parted_2.3-6ubuntu1_i386.deb) ...
Unpacking replacement parted ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up libparted0debian1 (2.3-6ubuntu1) ...
Setting up parted (2.3-6ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
                                         
Current status: 2 updates [-2].
paul@oneiric:~$
```

---

### Post by lucazade on 2011-06-16
latest cd iso image from today doesn't have this issue anymore.. installed properly in a vm.

---

