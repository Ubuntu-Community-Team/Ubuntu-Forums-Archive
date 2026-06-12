---
title: "Notifying a C#.Mono program when a flash drive is inserted"
date: 2008-05-29
forum: Programming Talk
---

### Post by Jordanwb on 2008-05-29
For Window's OSes I found this: [http://www.codeproject.com/KB/system/DriveDetector.aspx](http://www.codeproject.com/KB/system/DriveDetector.aspx) but it doesn't work in Mono. So I was wondering if anyone knew how I could get Ubuntu (or Mono) to tell my program that a flash drive was inserted. I want to make a program that keeps track of all my music (in the way that I want).

Thanks.

---

### Post by Lau_of_DK on 2008-05-29
> **Jordanwb said:**
> For Window's OSes I found this: [http://www.codeproject.com/KB/system/DriveDetector.aspx](http://www.codeproject.com/KB/system/DriveDetector.aspx) but it doesn't work in Mono. So I was wondering if anyone knew how I could get Ubuntu (or Mono) to tell my program that a flash drive was inserted. I want to make a program that keeps track of all my music (in the way that I want).

Thanks.

Yes, its possible. Although not as simple as in Windows :)

Read this guide: [Link]("http://www.gradstein.info/hardware/how-to-automatically-run-a-script-after-inserting-a-usb-device-on-ubuntu/")

And you should be all set,
/Lau

---

### Post by Jordanwb on 2008-05-29
Wow that is seriously confusing/complicated. [Brain Wave]

Stating the obvious: when a device is plugged in, it's mounted to the /media folder. For my flash drive it's /media/disk.

Idea: In the System.IO namespace there's a class that let's me monitor folders for new events, IE: a folder being created (hopefully), and in turn a new device. Now all I have to do is remember what the class is called.

[Edit] It's FileSystemWatcher

[Edit #2] That doesn't work.

---

