---
title: "[SOLVED] Changing Drive letters"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Harpz on 2008-08-05
Hi
I totally new to Linux and 4 days ago i installed Ubuntu and thus far Im enjoying it, but i got a problem.

After installing what i wanted i came across Corky and the relevant modules that allow you to display system temps and what not.

I use the following to display my Hard Disk temps:
```
${color #ffffff}SDA-MAXTOR 250Gb:${alignr}${execi 300 nc localhost 7634 | cut -c31-32;}°C
${color #ffffff}SDB-SAMSUNG 250Gb:${alignr}${execi 300 nc localhost 7634 | cut -c62-63;}°C
${color #ffffff}SDC-MAXTOR 120Gb:${alignr}${execi 300 nc localhost 7634 | cut -c92-93;}°C
${color #ffffff}SDD-MAXTOR 200Gb:${alignr}${execi 300 nc localhost 7634 | cut -c122-123;}°C
```
This is based on:
```
mike@Ubuntu:~$ nc localhost 7634
```
which gives (edited to simulate problem):

```
|/dev/sda|Maxtor 6Y120L0|26|C||/dev/sdb|Maxtor 6Y200P0|30|C||/dev/sdc|MAXTOR STM3250820AS|34|C||/dev/sdd|SAMSUNG SP2504C|27|C|
```

My problem is that lately my drive letters (not sure thats even right term) seem to change after a boot/reboot and if i now run:
```
mike@Ubuntu:~$ nc localhost 7634
```
I get:
```
|/dev/sda|Maxtor 6Y120L0|26|C||/dev/sdb|Maxtor 6Y200P0|30|C||/dev/sdd|MAXTOR STM3250820AS|34|C||/dev/sde|SAMSUNG SP2504C|27|C|mike@Ubuntu:~$ 
```

As you can see there is no sdc and when I:

```
 hddtemp /dev/sdc
```
it tells me:
```
/dev/sdc: IOMEGA  ZIP 250       ATAPI             : S.M.A.R.T. not available
```

sda-d used to be my hard disks and thats what the "cut -c92-93" locations in my conkymain file are based on, now that the Zip Drive keeps showing up in the line up from time to time and taking sbc the "cuts" keep getting messed up.

Now the questions:

1. Is there a way to tell the Zip drive to use a different sb? letter?

2. Why do the letters (if thats the right term) keep changing? When i used to use windows once i set a drives letter it stayed the same until i changed it (i used to keep dvd-rom and zip drive on Y: and Z:).

and finally
3. Is there a way with Conky to get to read the temp from a given drive using the unique id of the drive? (UUID came across this term somewhere not 100% on what it does)

Hope some one can help
Mike

---

### Post by northern lights on 2008-08-05
Running ```
cat /etc/fstab
```will tell you the UUIDs of your devices. Unfortunately, if device names are bound to change once in a while.

---

### Post by Harpz on 2008-08-05
:( can UUIDs be used in Conky? so that i don't have to keep changing my "cut" positions

Mike

---

### Post by Harpz on 2008-08-19
> **northern lights said:**
> Running ```
cat /etc/fstab
```will tell you the UUIDs of your devices. Unfortunately, if device names are bound to change once in a while.

So is theres no way to set then so they stay the same?

---

### Post by ace007 on 2008-08-19
Which device it is depends on what order it is "plugged in".  If you boot up your computer with a USB drive plugged in, it might use the next available alphabet letter, or it may use the first and move all your devices down a letter.  That is my experience anyway.  If you dont plug it in until after ubuntu is loaded, it'll use the next available letter.

Windows behaves the same.  If your usb drive is always F:/ and then you install a new hard drive, it'll be called F:/ and your USB drive will be called E:/ every time you plug it in.

Anyways, UUID dont change with devices? but I dont know much about those.

To make the letter stay the same always, just always boot with the same hardware configuration.

Sorry that probably informative, but doesn't do anything for you.  It's late.

---

### Post by Vivaldi Gloria on 2008-08-19
> **Icerat said:**
> So is theres no way to set then so they stay the same?

You can with udev. Well, if you have time then you can learn udev.

[http://www.archive.org/details/HampshireLinuxUserGroup_udev](http://www.archive.org/details/HampshireLinuxUserGroup_udev)
[http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)

See the links at the end of the wikipedia article.

---

### Post by Harpz on 2008-09-11
Guess ill have to put up with it.
Marking solved
Mike

---

