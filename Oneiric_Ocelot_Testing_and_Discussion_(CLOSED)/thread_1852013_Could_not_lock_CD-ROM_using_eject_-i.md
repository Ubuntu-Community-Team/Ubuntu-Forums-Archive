---
title: "Could not lock CD-ROM using eject -i"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by haen on 2011-09-29
In 11.04 I was able to lock a CD-ROM drive using
```
eject -i 1 /dev/cdrom1
```

Under 11.10 it does not work anymore, although 'CD-Drive may NOT be ejected with device button' message is displayed on the console. Any thoughts?

---

### Post by cariboo on 2011-09-29
The first thing to do is to determine is actually a device called cdrom1 in /dev:

```
ls -l /dev/cdrom*
```

THis is the result I get when running the above command:

```
cariboo@alexis:~$ ls -l /dev/cdrom*
lrwxrwxrwx 1 root root 3 2011-09-29 09:52 /dev/cdrom -> sr0
```

now that we've determined if the device exists, use the following command:

```
sudo eject /dev/cdrom1
```.

Another thing is where are you getting the parameters from, when running:

```
eject --h
```

I don't see a -i option

---

### Post by haen on 2011-09-29
So
```
eject -h
```
is incomplete. Do
```
man eject
```
and you will see
```
-i on|1|off|0
            This option controls locking of the hardware  eject  button.  When
            enabled, the drive will not be ejected when the button is pressed.
            This is useful when you are carrying a laptop in a bag or case and
            don't want it to eject if the button is inadvertently pressed.
```

/dev/cdrom1 is present and (no sudo needed)
```
eject /dev/cdrom1
```
ejects drive as advertised. It is just the '-i' option refuses to work under 11.10.

---

### Post by thatguruguy on 2011-09-29
Here's a bug report about the issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/854814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/854814)

However, it's apparently not just limited to Ubuntu; it's a change in the way that udev interprets and handles the pressing of the button on the cd drive.

---

### Post by haen on 2011-09-30
Many thx.

There is some additional info and references here: [https://bugs.archlinux.org/task/25838](https://bugs.archlinux.org/task/25838). I will keep monitoring this issue. Since my firstborn discovered joys of pushing things my CD drive is in grave danger.

---

### Post by haen on 2011-09-30
For anyone interested:

[LIST=1]
[*]comment
```
ENV{DISK_EJECT_REQUEST}=="?*", RUN+="cdrom_id --eject-media $tempnode", GOTO="cdrom_end"
```
in /lib/udev/rules.d/60-cdrom_id.rules,
[*]restart udev
```
sudo /etc/init.d/udev restart
```
[*]now locking via eject -i 1 should work.
[/LIST]

---

### Post by thatguruguy on 2011-09-30
It looks like by commenting out that line, you're taking control of the cd button out of udev's hands.  Is that correct?

---

