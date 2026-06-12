---
title: "How to re-install a drive"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by chris-burmajster on 2015-11-07
Can somebody please tell me how to re-install a drive? It was OK the last time I used it and now it's not showing.

Chris

---

### Post by sudodus on 2015-11-07
Please tell us more about the drive!

- Hardware
- Software (what data is there in the drive?)

How have you been connecting and using it?

Can you try in another computer?

---

### Post by chris-burmajster on 2015-11-07
Hardware is Western Digital, and software is full of pictures. I have been connecting and using it until now and I can try it with another computer and it doesn't work. Connection is via a second hard drive.

---

### Post by yancek on 2015-11-07
Are you posting here because you have an Ubuntu operating system?
You indicate the drive is "not showing", where is it not showing?  Does this mean it no longer shows under the media directory?
If you have attached this drive on two computers and it "doesn't show", it is probably dead.
Can you give a little more detail on what "doesn't work" means?

---

### Post by sudodus on 2015-11-07
+1 to yancek's questions

I understand that it is an internal drive, connected via SATA or IDE (not a USB drive). Is this correct?

Does it sound like a working hard disk drive? Is there any sound from it at all?

Furthermore, if you are running linux, please post the output of the following commands, when the drive is connected,

```
sudo parted -ls
sudo lsblk -fm
sudo lshw -class disk
```

---

### Post by chris-burmajster on 2015-11-08
Yes, I'm using the Ubuntu operating system. The drive is not showing any more under the system icons. No, there is no sound from it at all. I cannot connect the drive (that's the problem) to see anything. It's dead. That's why I want to know how to re-install it.

---

### Post by sudodus on 2015-11-08
Please post the output of the following commands, when the drive is connected,

```
sudo parted -ls
sudo lsblk -fm
sudo lshw -class disk
```

I think the output of these commands can help us help you :-)

***Edit:*** I'm afraid that the hardware is damaged.

---

### Post by oldos2er on 2015-11-08
What type of system are you using, desktop or laptop? Have you checked the drive's physical connections, if possible? SATA? Have you tried running *smartctl* on the drive (install the package smartmontools if not)?

If it is truly dead, there's no reinstalling; it's time for a new disk.

---

