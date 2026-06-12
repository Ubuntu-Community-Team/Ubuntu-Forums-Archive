---
title: "Sold old Hard Drive as New. software check"
date: 2020-01-06
forum: New to Ubuntu
---

### Post by dave6 on 2020-01-06
Hi all... I was sold 2 hard drives 2TB each i size as "Opened, New, Unused"  I need these for my DAS win system, BUT when I went to format them, none of my OS drives systems could see them, it was only when I used them as a boot disk did I discover them to old, used drives from a sever network.

I remember some type of software here on Ubuntu that showed the disk size, health, etc. BUT also showed the logged hrs / days / years on the drive.

Does any one know what that program is called ?  till I see just how old they are.

Dave

---

### Post by jeremy31 on 2020-01-06
SMART data from disks program may show power on hours and power cycle count

---

### Post by dave6 on 2020-01-06
Hi Jeremy.. I brought the drive to a mate of mine, who has a larger Linux unit with more disc tools, same thing.  Blank, at a guess, there is no SMART on it, but we did decode the dates, one drive is dated as April 2014, second drive as Jan 2011 
I have zero confidence in these drives, so they will be shipped back to the suppler

---

### Post by TheFu on 2020-01-06
Every drive that has ever been sold by a vender that sells to the USGovt has smart data, period.  Effectively, that means any drive maker in the world.

smartutils is the package. there might be a dash in the name, IDK.

smartctl is the tool.
Step 1: run a test. wait the amount of time, short is usually 3 min.  long is usually 3+ hrs.
Step 2: run a report.  See the time-on hours and spinup/spindown cycles.

Not being able to see partitions doesn't mean anything.  That could just mean the prior owner wiped all data and partitions before selling it.

I've posted in these forums way too much about using smartctl.  Search and you can find those posts.

---

### Post by Impavidus on 2020-01-07
It is possible that you cannot read the smart data over usb (using a sata-to-usb adapter), but only when using the internal connector of your computer.

---

### Post by TheFu on 2020-01-07
> **Impavidus said:**
> It is possible that you cannot read the smart data over usb (using a sata-to-usb adapter), but only when using the internal connector of your computer.

Some USB adaptors won't do SMART, but many do.  I've had to pick a different device on smartctl command options to access some drives. For example:
```
$ sudo smartctl -d sat -a /dev/sdz
```
The device is required for every smartctl command.  The manpage has a list of possible devices, so be certain to check that.  Supported devices change with each smartctl release, so the manpage on your system is the best source for the specific devices supported.
```
       -d TYPE, --device=TYPE
              Specifies  the  type of the device.  The valid arguments to this
              option are:
```
There is an "auto" type, but it hasn't worked for my USB connected devices.
Also, sometimes external USB devices are slow and the drive may have spun down, so smart will fail until it spins up. The error messages are cryptic and change as the device comes alive.

There are other tools available like badblocks, but it is for a different purpose and takes much longer.

---

