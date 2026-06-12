---
title: "[SOLVED] Oh, man! I think I blew it..."
date: 2008-07-29
forum: New to Ubuntu
---

### Post by ionizd on 2008-07-29
I run Xubuntu on my laptop and I was poking around in my settings to try to resolve some long-standing issues I haven't had time to address until today.  For some reason, a 20Gb partition that formerly housed my Windows XP OS and that had been reformatted as EXT3 was refusing to mount when I started Gparted.  As I was looking through the toolbar at the top of the window, I happened upon the "set label" tab and couldn't recall going through that process when I was reformatting that partition.  Well, long story short, I selected the partition, clicked on the tool, and was completely horrified to see the entire drive change from my nice separate partitions to one single unallocated space.  I looked for an "undo" function, but it was grayed out.  I could still get to my files on the hard drive, though, so I figured that whatever it was that Gparted was saying had been done was not done and required some further action (apparently a reboot, go figure) to actually apply itself.
 So, what does it mean when GRUB refuses to boot and says "error 22"??
 I have disaster recovery tools and an Ultimate Boot CD, but somehow I don't think they will help me get my hard drive back to the way it was before.  PLEASE tell me I'm wrong about that and it's all right, that with a few simple keystrokes I can make this unfortunate episode go away.

---

### Post by steveneddy on 2008-07-29
Uh, oh. Hope someone besides me sees this.

---

### Post by Sef on 2008-07-29
> I have disaster recovery tools and an Ultimate Boot CD, but somehow I don't think they will help me get my hard drive back to the way it was before. PLEASE tell me I'm wrong about that and it's all right, that with a few simple keystrokes I can make this unfortunate episode go away.

Get [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by ionizd on 2008-07-29
Man, am I glad I had an Ultimate Boot CD burned and ready to use.  Test Disk is one of the many useful programs included on it, and this is the first time I've had a reason to use that particular app.  It worked like a charm!

 Thanks for the help.

---

