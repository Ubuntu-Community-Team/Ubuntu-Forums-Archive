---
title: "[SOLVED] Dell Inspiron 1521 and Ubuntu 8.04.1 (Hardy Heron)"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Crayboff on 2008-09-09
I recently made an [COLOR="Red"]Ubuntu 8.04.1-desktop-i386[/COLOR] Live CD and decided to test it out by partitioning Gateway PC (Intel Pentium 4, sorry I don't know more detail about my computers) and it worked perfectly. However, what I really want to do is install Hardy Heron on my Dell [COLOR="Red"]Inspiron 1521[/COLOR] (some AMD 2x processor, the sticker thing wore off). Despite how annoyed with Vista I am, I do not want to delete it, I just want to partition my hard drive.

I first defragged my hard drive, to the suggestion of a friend of mine who is a Ubuntu veteran and pretty smart with computers in general. Then I booted from the Live CD and tried installing it. An error message (a black screen with white writing) came up saying that I was missing some drivers, I didn't have enough time to write down what these drivers were before the screen switched to the regular install screen. I got to the part with options for partitioning, however it did not give me the all three choices I had when I did this with my Gateway computer. The only options I had was "Guided - use entire disk" and "Manual" both are things I do not want to do. :(

What do I do to be able to run both Vista and Hardy Heron on my Inspiron 1521? Is it even possible to do this with my laptop? Please tell me how before I screw something up.](*,)

---

### Post by mevets on 2008-09-09
you might just want to install ubuntu thru wubi. All it requires is that that you stick the cd in when Windows is running. It goes ahead and install ubuntu inside of windows. If you want to do a dual boot setup the conventional way, read [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by LeoSolaris on 2008-09-09
Wubi is an excellent suggestion, another option would be to use Vista's built in partitioning software to shrink it down before installing.

(just a hint: before clicking hte install button, it is useful to use GParted from the System->Administration menu. If it isn't under Admin, it's in Preferences.) It is generally easier to work with when editing partitions.)

Another good idea is to see if the disc burned properly. There should be a "check disc" sort of option on the boot up menu when you boot from the CD. Click that and it will scan the disc to make sure it is right.

Wubi is still a good option though, and may solve your issues for now till you're ready to actually wipe Windows off of your machine.

---

### Post by mikewhatever on 2008-09-09
I don't understand the problem. You want Ubuntu installed, but don't want to use the available partitioning options? Why?
I suggest going back a step and find out your computer specs. Testing the hardware with the live cd is also extremely worthwhile.

---

### Post by Crayboff on 2008-09-09
> **mikewhatever said:**
> I don't understand the problem. You want Ubuntu installed, but don't want to use the available partitioning options? Why?
I suggest going back a step and find out your computer specs. Testing the hardware with the live cd is also extremely worthwhile.

I do want to use it's partitioning options but it didn't give me the option that allowed me to partition my hard drive. I'm trying to install it from the Live CD I created (I checked the disk integrity and it was fine)and none of the options I was given for partitioning actually would partition my hard drive for me (one would delete Vista completely and the other was Manual, which I don't know enough about to even attempt it.

Oh, I have a question to anyone, will using Wubi make Vista even slower? The main reason I'm looking at Linux is to have a faster OS, but I don't want to make Vista slower than the slug it already is. As I understand it, Wubi will make a folder in Windows, which I could only imagine would get quite large and probably slow windows to a crawl. I'll look more into it though

As for my specs:

**Manufacturer:** Dell
**Model:** Inspiron 1521
**Processor:** AMD Turion 64 X2 Mobile Technology TL-58 1.90GHz
**Memory (RAM):** 1918MB
**System Type:** 32-bit Operating System

and not sure if you need this for any reason:

**Current Operating System:** Windows Vista Home Premium

---

### Post by mevets on 2008-09-09
Wubi really wont slow vista down any. When you install ubuntu through wubi you specify how large you want the installation to be, so it isnt going to grow and grow. You allocate all the space you need from the beginning.

---

### Post by Crayboff on 2008-09-10
Alright, thanks everyone. Wubi worked like a charm. thanks:-D

---

